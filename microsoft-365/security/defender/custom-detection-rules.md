---
title: Opret og administrer regler for brugerdefineret registrering i Microsoft 365 Defender
description: Få mere at vide om, hvordan du opretter og administrerer regler for brugerdefinerede registreringer baseret på avancerede forespørgselsforespørgsler
keywords: avanceret jagt, trusselssporing, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, regler, skema, kusto, RBAC, tilladelser, Microsoft Defender til slutpunkt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dac2a68249d90b212e6bbcaacdec84918560deb5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755804"
---
# <a name="create-and-manage-custom-detections-rules"></a>Oprette og administrere regler for brugerdefinerede registreringer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

Brugerdefinerede registreringsregler er regler, du kan designe og justere ved hjælp [af avancerede](advanced-hunting-overview.md) forespørgselsforespørgsler. Disse regler gør det muligt proaktivt at overvåge forskellige hændelser og system tilstande, herunder mistænkelig aktivitet for brud og forkert konfigurerede slutpunkter. Du kan indstille dem til at køre med jævne mellemrum, generere beskeder og tage svarhandlinger, når der er resultater.

## <a name="required-permissions-for-managing-custom-detections"></a>Påkrævede tilladelser til administration af brugerdefinerede registreringer

Hvis du vil administrere brugerdefinerede registreringer, skal du have tildelt en af disse roller:

- **Sikkerhedsadministrator** – Brugere med [denne Azure Active Directory rolle kan](/azure/active-directory/roles/permissions-reference#security-administrator) administrere sikkerhedsindstillinger i Microsoft 365 Defender-portalen og andre portaler og tjenester.

- **Sikkerhedsoperatør** – Brugere med denne [Azure Active Directory-rolle](/azure/active-directory/roles/permissions-reference#security-operator) kan administrere beskeder og få global skrivebeskyttet adgang til sikkerhedsrelaterede funktioner, herunder alle oplysninger på Microsoft 365 Defender-portalen. Denne rolle er kun tilstrækkelig til at administrere brugerdefinerede registreringer, hvis rollebaseret adgangskontrol (RBAC) er slået fra i Microsoft Defender til slutpunkt. Hvis du har konfigureret RBAC, skal du også have **tilladelsen Administrer sikkerhedsindstillinger** for Defender til Slutpunkt.

Du kan også administrere brugerdefinerede registreringer, der gælder for data fra bestemte Microsoft 365 Defender, hvis du har tilladelser til dem. Hvis du kun har tilladelse til at administrere Microsoft 365 Defender for Office, `Email` kan du f.eks. oprette brugerdefinerede registreringer ved hjælp af tabeller, men ikke `Identity` tabeller.  

En global administrator kan gøre følgende for **at administrere påkrævede** tilladelser:

- Tildel **sikkerhedsadministratoren eller** **sikkerhedsoperatorrollen** [i Microsoft 365 Administration](https://admin.microsoft.com/) under **RolesSecurity-administrator** > .
- Kontrollér RBAC-indstillingerne for Microsoft Defender for slutpunkt [Microsoft 365 Defender](https://security.microsoft.com/) under **Indstillinger** >  **PermissionsRoles** > . Vælg den tilsvarende rolle for at tildele **tilladelsen Administrer sikkerhedsindstillinger** .

> [!NOTE]
> Sikkerhedsoperatorer skal have **tilladelsen** Administrer sikkerhedsindstillinger i  Microsoft Defender til slutpunkt for at administrere brugerdefinerede registreringer, hvis RBAC er slået til.

## <a name="create-a-custom-detection-rule"></a>Oprette en brugerdefineret registreringsregel
### <a name="1-prepare-the-query"></a>1. Forbered forespørgslen.

I portalen Microsoft 365 Defender skal du gå til **Avanceret på jagt** og vælge en eksisterende forespørgsel eller oprette en ny forespørgsel. Når du bruger en ny forespørgsel, skal du køre forespørgslen for at identificere fejl og forstå mulige resultater.

>[!IMPORTANT]
>Hvis du vil forhindre tjenesten i at returnere for mange beskeder, er hver regel begrænset til kun at generere 100 beskeder, når den kører. Før du opretter en regel, skal du justere din forespørgsel for at undgå at blive advaret om normal, daglig aktivitet.


#### <a name="required-columns-in-the-query-results"></a>Påkrævede kolonner i forespørgselsresultaterne
Hvis du vil oprette en brugerdefineret registreringsregel, skal forespørgslen returnere følgende kolonner:

- `Timestamp`– bruges til at angive tidsstemplet for oprettede beskeder
- `ReportId`– aktiverer opslag for de oprindelige poster
- En af følgende kolonner, der identificerer bestemte enheder, brugere eller postkasser:
    - `DeviceId`
    - `DeviceName`
    - `RemoteDeviceName`
    - `RecipientEmailAddress`
    - `SenderFromAddress` (konvolutafsender eller Return-Path adresse)
    - `SenderMailFromAddress` (Afsenderadresse vist af mailklient)
    - `RecipientObjectId`
    - `AccountObjectId`
    - `AccountSid`
    - `AccountUpn`
    - `InitiatingProcessAccountSid`
    - `InitiatingProcessAccountUpn`
    - `InitiatingProcessAccountObjectId`

>[!NOTE]
>Understøttelse af yderligere enheder tilføjes, når nye tabeller føjes til det avancerede [jagtskema](advanced-hunting-schema-tables.md).

Simple forespørgsler, f.eks. dem `project` `summarize` , der ikke bruger operatoren eller til at tilpasse eller aggregere resultater, returnerer typisk disse fælles kolonner.

Der er forskellige måder at sikre, at mere komplekse forespørgsler returnerer disse kolonner. Hvis du f.eks. foretrækker at sammenlægge og tælle efter enhed under `DeviceId`en kolonne som f.eks. , `ReportId` `Timestamp` kan du stadig returnere og ved at hente det fra den seneste hændelse, der involverer hver entydig.`DeviceId`


> [!IMPORTANT]
> Undgå at filtrere brugerdefinerede registreringer ved hjælp af `Timestamp` kolonnen. De data, der bruges til brugerdefinerede registreringer, filtreres på forhånd baseret på registreringsfrekvensen.


Nedenstående eksempelforespørgsel tæller antallet af unikke enheder (`DeviceId`) med antivirusregistreringer og bruger dette antal til kun at finde enheder med mere end fem registreringer. Hvis det nyeste og det `Timestamp` tilsvarende skal `ReportId`returneres, bruges `summarize` operatoren med `arg_max` funktionen.

```kusto
DeviceEvents
| where ingestion_time() > ago(1d)
| where ActionType == "AntivirusDetection"
| summarize (Timestamp, ReportId)=arg_max(Timestamp, ReportId), count() by DeviceId
| where count_ > 5
```

> [!TIP]
> Du kan forbedre forespørgslens ydeevne ved at angive et tidsfilter, der svarer til den tilsigtede kørselsfrekvens for reglen. Da den mest hyppige kørsel er _hver 24 timer_, vil filtreringen for den seneste dag omfatte alle nye data.

### <a name="2-create-new-rule-and-provide-alert-details"></a>2. Opret ny regel, og angiv beskedoplysninger.

Med forespørgslen i forespørgselseditoren skal du **vælge Opret registreringsregel** og angive følgende beskeddetaljer:

- **Registreringsnavn** – navnet på registreringsreglen. skal være entydig
- **Hyppighed** – interval for at køre forespørgslen og gøre noget. [Se yderligere vejledning nedenfor](#rule-frequency)
- **Titel for** besked – titel vist med beskeder udløst af reglen; skal være entydig
- **Alvorsgrad** – den potentielle risiko ved komponenten eller aktiviteten identificeret af reglen
- **Kategori** – trusselskomponent eller aktivitet identificeret af reglen
- **MITRE ATT&CK-teknikker** – en eller flere angrebsteknikker, der er identificeret af reglen som dokumenteret i [MITRE ATT&CK-frameworket](https://attack.mitre.org/). Dette afsnit er skjult for visse kategorier af beskeder, herunder malware, ransomware, mistænkelig aktivitet og uønsket software
- **Beskrivelse** – flere oplysninger om den komponent eller aktivitet, der er identificeret af reglen 
- **Anbefalede handlinger** – yderligere handlinger, svarere kan udføre som svar på en besked

#### <a name="rule-frequency"></a>Regelfrekvens
Når du gemmer en ny regel, køres den, og der kontrolleres for match fra de seneste 30 dages data. Reglen kører derefter igen med faste intervaller og anvender en tilbagekaldsvarighed baseret på den hyppighed, du vælger:

- **Hver 24. time** – kører hver 24. time og kontrollerer data fra de seneste 30 dage
- **Hver 12. time** – kører hver 12. time og kontrollerer data fra de seneste 24 timer
- **Hver 3. time** – kører hver 3. time og kontrollerer data fra de seneste 6 timer
- **Hver time** – kører hver time og kontrollerer data fra de seneste 2 timer

Når du redigerer en regel, køres den med de anvendte ændringer i den næste kørselstid planlagt i overensstemmelse med den hyppighed, du angiver.



>[!TIP]
> Match tidsfiltrene i forespørgslen med opslagsvarigheden. Resultater uden for opslagsvarigheden ignoreres.  

Vælg den hyppighed, der passer til, hvor tæt du vil overvåge registreringer. Overvej din organisations kapacitet til at besvare beskederne.

### <a name="3-choose-the-impacted-entities"></a>3. Vælg de på påvirkede enheder.
Identificer de kolonner i forespørgselsresultaterne, hvor du forventer at finde den primære påvirkede eller påvirkede enhed. En forespørgsel kan f.eks. returnere afsender- (`SenderFromAddress` eller `SenderMailFromAddress`) og modtageradresser (`RecipientEmailAddress`). Når du identificerer, hvilke af disse kolonner der repræsenterer den primære påvirkningte enhed, hjælper det tjenesten med at samle relevante beskeder, korrelere hændelser og målrette svarhandlinger.

Du kan kun vælge én kolonne for hver enhedstype (postkasse, bruger eller enhed). Kolonner, der ikke returneres af forespørgslen, kan ikke markeres.

### <a name="4-specify-actions"></a>4. Angiv handlinger.
Din brugerdefinerede registreringsregel kan automatisk udføre handlinger på enheder, filer eller brugere, der returneres af forespørgslen.

#### <a name="actions-on-devices"></a>Handlinger på enheder
Disse handlinger anvendes på enheder i kolonnen `DeviceId` med forespørgselsresultater:
- **Isoler enhed** – bruger Microsoft Defender til slutpunkt til at anvende fuld netværksisolation, hvilket forhindrer enheden i at oprette forbindelse til et hvilket som helst program eller nogen tjeneste. [Få mere at vide om Microsoft Defender for endpoint-maskinisolation](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#isolate-devices-from-the-network)
- **Indsamler undersøgelsespakke** – indsamler enhedsoplysninger i en ZIP-fil. [Få mere at vide om undersøgelsespakken til Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts#collect-investigation-package-from-devices)
- **Kør en antivirusscanning** – udfører en Windows Defender Antivirus scanning på enheden
- **Initier** undersøgelse – [igangsætter en automatisk](m365d-autoir.md) undersøgelse på enheden
- **Begræns** udførelse af apps – angiver begrænsninger på enheden for kun at tillade kørsel af filer, der er signeret med et Microsoft-udstedt certifikat. [Få mere at vide om appbegrænsninger med Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/respond-machine-alerts#restrict-app-execution)

#### <a name="actions-on-files"></a>Handlinger på filer
Når denne indstilling er markeret, kan du vælge at anvende **filhandlingen** Karantæne på filer i `SHA1`, `InitiatingProcessSHA1``SHA256``InitiatingProcessSHA256` eller kolonnen i forespørgselsresultaterne. Denne handling sletter filen fra den aktuelle placering og placerer en kopi i karantæne.

#### <a name="actions-on-users"></a>Handlinger for brugere
Når denne indstilling er **markeret, sker handlingen** Markér bruger som kompromitteret for brugerne i `AccountObjectId`, `InitiatingProcessAccountObjectId`eller kolonnen `RecipientObjectId` i forespørgselsresultaterne. Denne handling indstiller brugernes risikoniveau til "højt" i Azure Active Directory, hvilket udløser tilsvarende politikker [for identitetsbeskyttelse](/azure/active-directory/identity-protection/overview-identity-protection).

> [!NOTE]
> Handlingen Tillad eller bloker for brugerdefinerede registreringsregler understøttes i øjeblikket ikke på Microsoft 365 Defender.

### <a name="5-set-the-rule-scope"></a>5. Angiv reglens omfang.
Angiv omfanget for at angive, hvilke enheder der er omfattet af reglen. Omfanget påvirker regler, der kontrollerer enheder og ikke påvirker regler, der kun kontrollerer postkasser og brugerkonti eller identiteter.

Når du angiver omfanget, kan du vælge:

- Alle enheder
- Bestemte enhedsgrupper

Der vil kun blive forespørget på data fra enheder, som er omfattet af området. Der vil også kun blive foretaget handlinger på disse enheder.

### <a name="6-review-and-turn-on-the-rule"></a>6. Gennemse og aktiver reglen.
Når du har gennemset reglen, skal du vælge **Opret** for at gemme den. Den brugerdefinerede registreringsregel kører straks. Den kører igen baseret på konfigureret hyppighed for at kontrollere match, generere beskeder og udføre svarhandlinger.


>[!Important] 
>Brugerdefinerede registreringer bør regelmæssigt revideres med henblik på effektivitet og effektivitet. For at sikre, at du opretter registreringer, der udløser sande beskeder, kan du bruge tid på at gennemgå dine eksisterende brugerdefinerede registreringer ved at følge trinnene i Administrer [eksisterende brugerdefinerede registreringsregler](#manage-existing-custom-detection-rules). <br>  
Du har stadig kontrol over kompleksiteten eller specificiteten af dine brugerdefinerede registreringer, så falske beskeder, der genereres af brugerdefinerede registreringer, kan angive, at det er nødvendigt at ændre visse parametre i reglerne.


## <a name="manage-existing-custom-detection-rules"></a>Administrere eksisterende regler for brugerdefineret registrering
Du kan få vist listen over eksisterende brugerdefinerede registreringsregler, kontrollere deres tidligere  kørt, og gennemse de beskeder, de har udløst. Du kan også køre en regel efter behov og ændre den.

>[!TIP]
> Beskeder, der er hævet ved brugerdefinerede registreringer, er tilgængelige via påmindelser og hændelses-API'er. Du kan finde flere oplysninger under [Understøttede Microsoft 365 Defender API'er](api-supported.md).

### <a name="view-existing-rules"></a>Få vist eksisterende regler

Hvis du vil have vist alle eksisterende brugerdefinerede registreringsregler, skal du **gå til** **registreringsreglerne for HuntingCustom** > . Siden viser alle regler med følgende kørselsoplysninger:

- **Sidste kørsel** – når der sidst blev kørt en regel for at søge efter forespørgsels match og oprette beskeder
- **Status for Seneste kørsel** – om en regel kørte korrekt
- **Næste kørsel** – næste planlagte kørsel
- **Status** – om en regel er blevet slået til eller fra

### <a name="view-rule-details-modify-rule-and-run-rule"></a>Få vist oplysninger om reglen, redigere reglen og køre reglen

For at få vist omfattende oplysninger om en brugerdefineret registreringsregel skal du gå til **HuntingCustom-registreringsregler**  >  og derefter vælge navnet på reglen. Du kan derefter få vist generelle oplysninger om reglen, herunder oplysninger om dens kørselsstatus og omfang. Siden indeholder også en liste over udløste beskeder og handlinger.

:::image type="content" source="../../media/custom-detect-rules-view.png" alt-text="Detaljesiden for brugerdefineret registreringsregel i Microsoft 365 Defender portal" lightbox="../../media/custom-detect-rules-view.png":::<br>
*Oplysninger om brugerdefineret registreringsregel*

Du kan også udføre følgende handlinger på reglen fra denne side:

- **Kør** – kør reglen med det samme. Dette nulstiller også intervallet for den næste kørsel.
- **Rediger** – rediger reglen uden at ændre forespørgslen
- **Rediger forespørgsel** – rediger forespørgslen i avanceret forespørgsel
- **Slå til** /  **Deaktivere reglen** eller forhindre den i at køre
- **Slet** – de deaktivere reglen og fjerne den

### <a name="view-and-manage-triggered-alerts"></a>Få vist og administrere udløste beskeder

I skærmbilledet med regeloplysninger (**HuntingCustom-registreringer** > [Regelnavn **]**) skal du gå til Udløste beskeder, der viser de beskeder, der **genereres** >  af svarer til reglen. Vælg en besked for at få vist detaljerede oplysninger om den og udføre følgende handlinger:

- Administrer beskeden ved at angive dens status og klassificering (sand eller falsk besked)
- Sammenkæde beskeden med en hændelse
- Kør den forespørgsel, der udløste beskeden om avanceret jagt

### <a name="review-actions"></a>Gennemse handlinger
I skærmbilledet med regeloplysninger (**Søgningskunder** > [ > Regelnavn **]**) skal du gå til Udløste **handlinger, der** viser de handlinger, der er foretaget baseret på match til reglen.

>[!TIP]
>Hvis du hurtigt vil have vist oplysninger og reagere på et element i en tabel, skal du bruge markeringskolonnen [&#10003;] til venstre i tabellen.

>[!NOTE]
>Nogle af kolonnerne i denne artikel er muligvis ikke tilgængelige i Microsoft Defender til slutpunkt. [Slå en Microsoft 365 Defender til](m365d-enable.md) for at lede efter trusler ved hjælp af flere datakilder. Du kan flytte dine avancerede arbejdsprocesser på jagt fra Microsoft Defender for Endpoint til Microsoft 365 Defender ved at følge trinnene i Overfør avancerede [forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md).

## <a name="see-also"></a>Se også
- [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md)
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær det avancerede forespørgselssprog](advanced-hunting-query-language.md)
- [Overfør avancerede forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md)
