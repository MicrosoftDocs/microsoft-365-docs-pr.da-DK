---
title: Prøv Microsoft 365 Defender funktioner til svar på hændelser i et pilotmiljø
description: Prøv funktioner til svar på hændelser i Microsoft 365 Defender for at prioritere og administrere hændelser, automatisere undersøgelser og bruge avanceret jagt i trusselsregistrering.
keywords: Microsoft 365 Defender prøveperiode, prøv Microsoft 365 Defender, evaluer Microsoft 365 Defender Microsoft 365 Defender evalueringslaboratorium Microsoft 365 Defender  pilot, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 01a263569da09807c96160c32fda719bd2575994
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748469"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>Prøv Microsoft 365 Defender funktioner til svar på hændelser i et pilotmiljø

**Gælder for:**
- Microsoft 365 Defender

Denne artikel er [trin 2 af 2](eval-defender-investigate-respond.md) i processen med at udføre en undersøgelse og svar på en hændelse i Microsoft 365 Defender ved hjælp af et pilotmiljø. Du kan få flere oplysninger om denne proces i [](eval-defender-investigate-respond.md) oversigtsartiklen.

Når du har udført et [hændelsessvar for et simuleret angreb](eval-defender-investigate-respond-simulate-attack.md), er her nogle Microsoft 365 Defender funktioner, du kan udforske:

|Kapacitet |Beskrivelse |
|:-------|:-----|
| [Prioritering af hændelser](#prioritize-incidents) | Brug filtrering og sortering af hændelseskøen til at bestemme, hvilke hændelser der skal håndteres næste. |
| [Administration af hændelser](#manage-incidents) | Rediger hændelsesegenskaber for at sikre korrekt tildeling, tilføje mærker og kommentarer og for at løse en hændelse. |
| [Automatiseret undersøgelse og svar](#examine-automated-investigation-and-response-with-the-action-center) | Brug air-funktioner (automated investigation and response) til at hjælpe dit sikkerhedsteam med at håndtere trusler mere effektivt og effektivt. Handlingscenter er en "enkelt rude af glas" til hændelses- og beskedopgaver, f.eks. godkendelse af ventende afhjælpningshandlinger. |
| [Avanceret jagt](#use-advanced-hunting) | Brug forespørgsler til proaktivt at inspicere hændelser i dit netværk og finde trusselsindikatorer og -enheder. Du bruger også avanceret jagt under undersøgelse og afhjælpning af en hændelse. |


## <a name="prioritize-incidents"></a>Prioriter hændelser

Du kommer til hændelseskøen fra **Hændelser & beskeder > Hændelser** på hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Afsnittet Hændelser & beskeder på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::


Afsnittet **Seneste hændelser og beskeder** viser en graf over antallet af modtagne beskeder og hændelser, der er oprettet inden for de seneste 24 timer.

Hvis du vil undersøge listen over hændelser og prioritere deres vigtighed for tildeling og undersøgelse, kan du: 

- Konfigurer kolonner, der kan tilpasses (vælg **Vælg kolonner**), for at give dig indblik i forskellige egenskaber for hændelsen eller de påvirkede objekter. Dette hjælper dig med at træffe en informeret beslutning om prioriteringen af hændelser til analyse.

- Brug filtrering til at fokusere på et bestemt scenarie eller en bestemt trussel. Anvendelse af filtre på hændelseskøen kan hjælpe med at afgøre, hvilke hændelser der kræver øjeblikkelig opmærksomhed. 

I standardhændelseskøen skal du vælge **Filtre** for at se ruden **Filtre** , hvorfra du kan angive et bestemt sæt hændelser. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Ruden Filtre i sektionen Hændelser & beskeder på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Du kan få mere at vide under [Prioriter hændelser](incident-queue.md).

## <a name="manage-incidents"></a>Administrer hændelser

Du kan administrere hændelser fra ruden **Administrer hændelse** for en hændelse. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Ruden Administrer hændelse i sektionen Hændelser & beskeder på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Du kan få vist denne rude via linket **Administrer hændelse** på:

- Ruden Egenskaber for en hændelse i hændelseskøen.
- **Oversigtsside** for en hændelse.

Her er de måder, du kan administrere dine hændelser på:

- Rediger hændelsesnavnet

  Skift det navn, der automatisk er tildelt, på baggrund af bedste praksis for dit sikkerhedsteam.
  
- Tilføj hændelseskoder

  Tilføj mærker, som dit sikkerhedsteam bruger til at klassificere hændelser, som senere kan filtreres.
  
- Tildel hændelsen

  Tildel det til et brugerkontonavn, som kan filtreres senere.
  
- Løs en hændelse

  Luk hændelsen, når den er blevet afhjælpet.
  
- Angiv klassificering og bestemmelse

  Klassificer og vælg trusselstypen, når du løser en hændelse.
  
- Tilføj kommentarer

  Brug kommentarer til status, noter eller andre oplysninger, der er baseret på bedste praksis for sikkerhedsteamet. Den komplette kommentarhistorik er tilgængelig fra indstillingen **Kommentarer og historik** på detaljesiden for en hændelse.

Du kan få flere oplysninger under [Administrer hændelser](manage-incidents.md).

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>Undersøg automatiseret undersøgelse og svar med Løsningscenter

Afhængigt af hvordan automatiserede undersøgelses- og svarfunktioner er konfigureret for din organisation, udføres afhjælpningshandlinger automatisk eller kun efter godkendelse af dit team for sikkerhedshandlinger. Alle handlinger, uanset om de er ventende eller fuldført, er angivet i [Løsningscenter](m365d-action-center.md), som viser ventende og fuldførte afhjælpningshandlinger for dine enheder, mail & samarbejdsindhold og identiteter på én placering.

Her er et eksempel.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Unified Action Center på Microsoft 365 Defender-portalen" lightbox="../../media/m3d-action-center-unified.png":::

I Løsningscenter kan du vælge ventende handlinger og derefter godkende eller afvise dem i pop op-ruden. Her er et eksempel.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Ruden, der viser indstillingerne for godkendelse eller afvisning af en handling på Microsoft 365 Defender-portalen" lightbox="../../media/air-actioncenter-itemselected.png":::


Godkend (eller afvis) ventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fortsætte og fuldføres rettidigt.

Du kan få flere oplysninger i [Automatiseret undersøgelse og svar](m365d-autoir.md) og [Løsningscenter](m365d-action-center.md).

## <a name="use-advanced-hunting"></a>Brug avanceret jagt

> [!NOTE]
> Før vi fører dig gennem den avancerede jagtsimulering, kan du se følgende video for at forstå avancerede jagtkoncepter, se, hvor du kan finde den på portalen, og vide, hvordan den kan hjælpe dig i dine sikkerhedsoperationer.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


Hvis den [valgfri filløse PowerShell-angrebssimulering](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) var et rigtigt angreb, der allerede havde nået adgangsfasen for legitimationsoplysninger, kan du bruge avanceret jagt på ethvert tidspunkt i undersøgelsen til proaktivt at søge gennem hændelser og poster i netværket ved hjælp af det, du allerede ved fra de genererede beskeder og berørte enheder. 

Baseret på oplysninger i [SMB-beskeden (User and IP address reconnaissance)](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity) kan du f.eks. bruge tabellen `IdentityDirectoryEvents` til at finde alle optællingshændelser for SMB-sessionen eller finde flere registreringsaktiviteter i forskellige andre protokoller i Microsoft Defender for Identity data ved hjælp af tabellen`IdentityQueryEvents`.


### <a name="hunting-environment-requirements"></a>Krav til jagtmiljøer

Der kræves en enkelt intern postkasse og enhed til denne simulering. Du skal også bruge en ekstern mailkonto for at sende testmeddelelsen.

1. Kontrollér, at din lejer har [aktiveret Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Identificer en destinationspostkasse, der skal bruges til at modtage mail.

   - Denne postkasse skal overvåges af Microsoft Defender for Office 365

   - Enheden fra krav 3 skal have adgang til denne postkasse

3. Konfigurer en testenhed:

    a. Kontrollér, at du bruger Windows 10 version 1903 eller nyere version.

    b. Slut testenheden til testdomænet.

    c. [Slå Windows Defender Antivirus](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) til. Hvis du har problemer med at aktivere Windows Defender Antivirus, kan du se [dette emne om fejlfinding](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

    d. [Ombord til Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>Kør simuleringen

1. Fra en ekstern mailkonto skal du sende en mail til den postkasse, der er identificeret i trin 2 i afsnittet krav til jagtmiljøer. Medtag en vedhæftet fil, der tillades via alle eksisterende politikker for mailfilter. Denne fil behøver ikke at være skadelig eller eksekverbar. Foreslåede filtyper er <i>.pdf</i>, <i>.exe</i> (hvis det er tilladt) eller en Office-dokumenttype, f.eks. en Word-fil.

2. Åbn den sendte mail fra den enhed, der er konfigureret som defineret i trin 3 i afsnittet krav til jagtmiljøer. Åbn den vedhæftede fil, eller gem filen på enheden.

#### <a name="go-hunting"></a>Gå på jagt

1. Åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

2. Vælg **Jagt > Avanceret jagt** i navigationsruden.

3. Opret en forespørgsel, der starter med at indsamle mailhændelser.

   1. Vælg **Forespørgsel > Ny**.

   1. I grupperne **Mail** under **Avanceret jagt** skal du dobbeltklikke på **EmailEvents**. Du bør kunne se dette i forespørgselsvinduet.

      ```console
      EmailEvents
      ```

   1. Ret tidsrammen for forespørgslen til de seneste 24 timer. Hvis vi antager, at den mail, du sendte, da du kørte simuleringen ovenfor, var inden for de seneste 24 timer, skal du ellers ændre tidsrammen efter behov.

   1. Vælg **Kør forespørgsel**. Du kan have forskellige resultater, afhængigt af dit pilotmiljø.

      > [!NOTE]
      > Se næste trin for at få oplysninger om filtreringsindstillinger for at begrænse dataretur.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-1.png" alt-text="Siden Avanceret jagt på portalen Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-1.png":::

        > [!NOTE]
        > Avanceret jagt viser forespørgselsresultater som tabeldata. Du kan også vælge at få vist dataene i andre formattyper, f.eks. diagrammer.

   1. Se på resultaterne, og se, om du kan identificere den mail, du har åbnet. Det kan tage op til to timer, før beskeden vises i avanceret jagt. Hvis du vil indsnævre resultaterne, kan du **føje** where-betingelsen til din forespørgsel for kun at søge efter mails, der har "yahoo.com" som deres SenderMailFromDomain. Her er et eksempel.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Klik på de resulterende rækker fra forespørgslen, så du kan undersøge posten.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-2.png" alt-text="Sektionen Undersøg post på siden Avanceret jagt på Microsoft 365 Defender-portalen" lightbox="../../media/advanced-hunting-incident-response-try-2.png":::

4. Nu, hvor du har bekræftet, at du kan se mailen, skal du tilføje et filter for de vedhæftede filer. Fokuser på alle mails med vedhæftede filer i miljøet. I forbindelse med denne simulering skal du fokusere på indgående mails, ikke dem, der sendes ud fra dit miljø. Fjern eventuelle filtre, du har tilføjet, for at finde meddelelsen, og tilføj "| hvor **AttachmentCount > 0** og **EmailDirection** == **"Indgående""**

   I følgende forespørgsel vises resultatet med en kortere liste end din første forespørgsel for alle mailhændelser:

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Derefter skal du inkludere oplysninger om den vedhæftede fil (f.eks. filnavn, hashes) i resultatsættet. Det gør du ved at joinforbinde tabellen **EmailAttachmentInfo** . De fælles felter, der skal bruges til at tilmelde sig, er i dette tilfælde **NetworkMessageId** og **RecipientObjectId**.

   Følgende forespørgsel indeholder også en ekstra linje "| **project-rename EmailTimestamp=Timestamp**", der hjælper med at identificere, hvilket tidsstempel der var relateret til mailen i forhold til tidsstempler relateret til filhandlinger, som du tilføjer i næste trin.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Derefter skal du bruge **SHA256-værdien** fra tabellen **EmailAttachmentInfo** til at finde **DeviceFileEvents** (filhandlinger, der skete på slutpunktet) for denne hash. Det fælles felt her er SHA256-hashen for den vedhæftede fil.

   Den resulterende tabel indeholder nu oplysninger fra slutpunktet (Microsoft Defender for Endpoint), f.eks. enhedsnavn, hvilken handling der blev udført (i dette tilfælde filtreret til kun at omfatte hændelser af typen FileCreated), og hvor filen blev gemt. Det kontonavn, der er knyttet til processen, medtages også.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Du har nu oprettet en forespørgsel, der identificerer alle indgående mails, hvor brugeren har åbnet eller gemt den vedhæftede fil. Du kan også afgrænse denne forespørgsel for at filtrere efter specifikke afsenderdomæner, filstørrelser, filtyper osv.

7. Funktioner er en særlig form for joinforbindelse, som giver dig mulighed for at hente flere TI-data om en fil, f.eks. dens prævalens, underskriver- og udstederoplysninger osv. Hvis du vil have flere oplysninger om filen, skal du bruge funktionsberigelsen **FileProfile(** ):

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Opret en registrering

Når du har oprettet en forespørgsel, der identificerer de oplysninger, du gerne vil **have besked** om, hvis de opstår fremover, kan du oprette en brugerdefineret registrering ud fra forespørgslen.

Brugerdefinerede registreringer kører forespørgslen i henhold til den angivne hyppighed, og resultaterne af forespørgslerne opretter sikkerhedsbeskeder baseret på de påvirkede aktiver, du vælger. Disse beskeder vil blive korreleret til hændelser og kan behandles som alle andre sikkerhedsbeskeder, der genereres af et af produkterne.

1. På forespørgselssiden skal du fjerne linje 7 og 8, der blev tilføjet i trin 7 i gå jagtinstruktionerne, og klikke på **Opret registreringsregel**.

   :::image type="content" source="../../media/advanced-hunting-incident-response-try-3.png" alt-text="Sektionen Forespørgselsredigering på siden Avanceret jagt på Microsoft 365 Defender-portalen" lightbox="../../media/advanced-hunting-incident-response-try-3.png":::

   > [!NOTE]
   > Hvis du klikker på **Opret registreringsregel** , og der er syntaksfejl i forespørgslen, gemmes registreringsreglen ikke. Dobbelttjek forespørgslen for at sikre, at der ikke er nogen fejl.

2. Udfyld de påkrævede felter med de oplysninger, der gør det muligt for sikkerhedsteamet at forstå beskeden, hvorfor den blev genereret, og hvilke handlinger du forventer, at de skal udføre.

   :::image type="content" source="../../media/mtp/fig23.png" alt-text="Siden Beskedoplysninger på portalen Microsoft 365 Defender" lightbox="../../media/mtp/fig23.png":::

   Sørg for, at du udfylder felterne med klarhed for at give den næste bruger en informeret beslutning om denne besked om registreringsregel

3. Vælg, hvilke enheder der påvirkes i denne besked. I dette tilfælde skal du vælge **Enhed** og **Postkasse**.

   :::image type="content" source="../../media/mtp/fig24.png" alt-text="Detaljesiden Påvirkede objekter på Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig24.png":::

4. Find ud af, hvilke handlinger der skal udføres, hvis beskeden udløses. I dette tilfælde skal du køre en antivirusscanning, selvom der kan udføres andre handlinger.

   :::image type="content" source="../../media/mtp/fig25.png" alt-text="Siden Handlinger på Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig25.png":::

5. Vælg området for påmindelsesreglen. Da denne forespørgsel omfatter enheder, er enhedsgrupperne relevante i denne brugerdefinerede registrering i henhold til Microsoft Defender for Endpoint kontekst. Når du opretter en brugerdefineret registrering, der ikke indeholder enheder som påvirkede enheder, gælder omfanget ikke.

   :::image type="content" source="../../media/mtp/fig26.png" alt-text="Områdesiden på Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig26.png":::


   I dette pilotprojekt kan det være en god idé at begrænse denne regel til et undersæt af testenheder i produktionsmiljøet.

6. Vælg **Opret**. Vælg derefter **Regler for brugerdefineret registrering** i navigationspanelet.

   :::image type="content" source="../../media/mtp/fig27a.png" alt-text="Indstillingen Regler for brugerdefineret registrering på Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig27a.png":::

   :::image type="content" source="../../media/mtp/fig27b.png" alt-text="Den side, der viser registreringsregler og udførelsesoplysninger på Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig27b.png":::

   På denne side kan du vælge registreringsreglen, som åbner en side med oplysninger.

   :::image type="content" source="../../media/mtp/fig28.png" alt-text="Den side, der viser detaljer om de udløste beskeder på Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig28.png":::


### <a name="expert-training-on-advanced-hunting"></a>Ekspertuddannelse i avanceret jagt

**Sporing af modstanderen** er en webcastserie for nye sikkerhedsanalytikere og erfarne trusselsjægere. Den guider dig gennem de grundlæggende funktioner inden for avanceret jagt, så du kan oprette dine egne avancerede forespørgsler. 

Se [Få ekspertuddannelse i avanceret jagt](advanced-hunting-expert-training.md) for at komme i gang.

### <a name="navigation-you-may-need"></a>Navigation, du muligvis har brug for

[Opret det Microsoft 365 Defender evalueringsmiljø](eval-create-eval-environment.md)
