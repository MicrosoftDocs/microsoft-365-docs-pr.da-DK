---
title: Politikker for styring af insiderrisiko
description: Få mere at vide om politikker for styring af insiderrisiko i Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 22682a801123d4f8c24cbc11e2d0e35d42228bba
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627277"
---
# <a name="insider-risk-management-policies"></a>Politikker for styring af insiderrisiko

Politikker for styring af insiderrisiko bestemmer, hvilke brugere der er inden for området, og hvilke typer risikoindikatorer der er konfigureret til beskeder. Du kan hurtigt oprette en politik, der gælder for alle brugere i organisationen, eller du kan definere individuelle brugere eller grupper til administration i en politik. Politikker understøtter indholdsprioriteter for at fokusere politikbetingelser på flere eller specifikke Microsoft Teams, SharePoint-websteder, datafølsomhedstyper og datamærkater. Ved hjælp af skabeloner kan du vælge specifikke risikoindikatorer og tilpasse hændelsestærskler for politikindikatorer, tilpasse risikoscores effektivt og niveauet og hyppigheden af beskeder. Derudover hjælper boostere af risikoscore og registreringer af uregelmæssigheder med at identificere brugeraktivitet, der er af højere vigtighed eller mere usædvanlig. Politikvinduer giver dig mulighed for at definere den tidsramme, hvor politikken skal anvendes på beskedaktiviteter, og bruges til at bestemme varigheden af politikken, når den er aktiveret.

Se [videoen Konfiguration af politikker for styring af insiderrisiko](https://www.youtube.com/watch?v=kudK5ajZTUo) for at få en oversigt over, hvordan politikker, der oprettes med indbyggede politikskabeloner, kan hjælpe dig med hurtigt at reagere på potentielle risici.

## <a name="policy-dashboard"></a>Politikdashboard

På **politikdashboardet** kan du hurtigt se politikkerne i din organisation, politikkens tilstand, manuelt føje brugere til politikker og få vist status for beskeder, der er knyttet til hver politik.

- **Politiknavn**: Det navn, der er tildelt politikken i politikguiden.
- **Status**: Tilstandsstatus for hver politik. Viser antallet af politikadvarsler og -anbefalinger eller statussen *I orden* for politikker uden problemer.  Du kan vælge politikken for at få vist oplysninger om tilstandsstatus for eventuelle advarsler eller anbefalinger.
- **Aktive beskeder**: Antallet af aktive beskeder for hver politik.
- **Bekræftede beskeder**: Det samlede antal beskeder, der resulterede i sager fra politikken inden for de sidste 365 dage.
- **Handlinger, der er udført på beskeder**: Det samlede antal beskeder, der er blevet bekræftet eller afvist i de sidste 365 dage.
- **Effektivitet af politikbeskeder**: Den procentdel, der bestemmes af det samlede antal bekræftede beskeder divideret med det samlede antal handlinger, der er udført på beskeder (hvilket er summen af beskeder, der er blevet bekræftet eller afvist i løbet af det seneste år).

![Dashboard med politik for styring af insiderrisiko.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics"></a>Politikanbefalinger fra analyse

Insiderrisikoanalyse giver dig mulighed for at evaluere potentielle insiderrisici i din organisation uden at konfigurere nogen politikker for insiderrisiko. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisiko og hjælpe med at bestemme typen og omfanget af politikker for styring af insiderrisiko, som du kan overveje at konfigurere.

Hvis du vil vide mere om insiderrisikoanalyse og politikanbefalinger, skal du se [Indstillinger for styring af insiderrisiko: Analytics](insider-risk-management-settings.md#analytics).

## <a name="policy-templates"></a>Politikskabeloner

Skabeloner til styring af insiderrisiko er foruddefinerede politikbetingelser, der definerer de typer risikoindikatorer og modellen for risikoscore, der bruges af politikken. Hver politik skal have en skabelon tildelt i guiden til oprettelse af politikker, før politikken oprettes. Styring af insiderrisiko understøtter op til fem politikker for hver politikskabelon. Når du opretter en ny insiderrisikopolitik med guiden Politik, skal du vælge mellem en af følgende politikskabeloner:

### <a name="data-theft-by-departing-users"></a>Datatyveri foretaget af afrejsende brugere

Når brugere forlader din organisation, er der specifikke risikoindikatorer, der typisk er knyttet til datatyveri af afrejsende brugere. Denne politikskabelon bruger exfiltrationsindikatorer til risikoscore og fokuserer på registrering og beskeder i dette risikoområde. Datatyveri til afrejsende brugere kan omfatte download af filer fra SharePoint Online, udskrivning af filer og kopiering af data til personlige cloudbeskeder og lagertjenester i nærheden af deres opsigelser og slutdatoer for beskæftigelse. Ved hjælp af enten Microsoft 365 HR-connectoren eller muligheden for automatisk at registrere sletning af brugerkonto i Azure Active Directory for din organisation starter denne skabelon scoring for risikoindikatorer, der relaterer til disse aktiviteter, og hvordan de korrelerer med brugerbeskæftigelsesstatus.

> [!IMPORTANT]
> Når du bruger denne skabelon, kan du konfigurere en Microsoft 365 HR-connector til periodisk at importere oplysninger om fratræden og slutdato for brugere i din organisation. Se artiklen [Importér data med HR-connectoren](import-hr-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation. Hvis du vælger ikke at bruge HR-connectoren, skal du vælge indstillingen Brugerkonto slettet fra Azure AD, når du konfigurerer udløserhændelser i politikguiden.

### <a name="general-data-leaks"></a>Generelle datalækager

Beskyttelse af data og forebyggelse af datalækager er en konstant udfordring for de fleste organisationer, især med den hurtige vækst i nye data, der er oprettet af brugere, enheder og tjenester. Brugerne er bemyndiget til at oprette, gemme og dele oplysninger på tværs af tjenester og enheder, der gør administration af datalækager mere og mere kompleks og vanskelig. Datalækager kan omfatte utilsigtet overdeling af oplysninger uden for din organisation eller datatyveri med ondsindede hensigter. Med en tildelt DLP-politik (Microsoft Purview Forebyggelse af datatab), indbyggede eller tilpassede udløserhændelser starter denne skabelon scoring af registreringer i realtid af mistænkelige SharePoint Online-dataoverførsler, fil- og mappedeling, udskrivning af filer og kopiering af data til personlige cloudmeddelelses- og lagertjenester.

Når du bruger en skabelon for *datalækager* , kan du tildele en DLP-politik til at udløse indikatorer i insiderrisikopolitikken for beskeder med høj alvorsgrad i din organisation. Når en besked med høj alvorsgrad genereres af en DLP-politikregel føjes til Office 365 overvågningslog, undersøger insiderrisikopolitikker, der oprettes med denne skabelon, automatisk DLP-beskeden med høj alvorsgrad. Hvis beskeden indeholder en bruger i området, der er defineret i insiderrisikopolitikken, behandles beskeden af insiderrisikopolitikken som en ny besked og tildeles en insiderrisiko alvorsgrad og risikoscore. Du kan også vælge at tildele valgte indikatorer som udløsende hændelser for en politik. Denne fleksibilitet og tilpasning hjælper med kun at tilpasse politikken til de aktiviteter, der er omfattet af indikatorerne. Denne politik giver dig mulighed for at evaluere denne besked i kontekst med andre aktiviteter, der er inkluderet i sagen.

#### <a name="data-leaks-policy-guidelines"></a>Retningslinjer for datalækagepolitik

Når du opretter eller ændrer DLP-politikker til brug med politikker for styring af insiderrisiko, skal du overveje følgende retningslinjer:

- Prioriter dataudfiltreringshændelser, og vær selektiv, når du tildeler indstillinger for **hændelsesrapporter** til *Høj* , når du konfigurerer regler i dine DLP-politikker. Mailing af følsomme dokumenter til en kendt konkurrent bør f.eks. være en eksfiltrationshændelse på *højt* beskedniveau. Overtildeling af niveauet *Højt* i indstillingerne for **hændelsesrapporter** i andre DLP-politikregler kan øge støjen i arbejdsprocessen for beskeder om insiderrisikostyring og gøre det vanskeligere for dine dataforskere og analytikere at evaluere disse beskeder korrekt. Hvis du f.eks. tildeler *høje* beskedniveauer til adgangsafvisende aktiviteter i DLP-politikker, bliver det mere udfordrende at evaluere en virkelig risikabel brugeradfærd og -aktiviteter.
- Når du bruger en DLP-politik som udløserhændelse, skal du sørge for, at du forstår og konfigurerer brugerne i både DLP- og insiderrisikostyringspolitikker korrekt. Det er kun brugere, der er defineret som indbyggede politikker for styring af insiderrisiko ved hjælp af skabelonen **Datalækager** , der behandler DLP-politikbeskeder med høj alvorsgrad. Derudover er det kun brugere, der er defineret som omfattet af en regel for en DLP-besked med høj alvorsgrad, der undersøges af politikken for styring af insiderrisiko. Det er vigtigt, at du ikke ubevidst konfigurerer brugere i omfang i både dine DLP- og insiderrisikopolitikker på en modstridende måde.

     Hvis dine DLP-politikregler f.eks. kun er beregnet til brugere i salgsteamet, og den insiderrisikopolitik, der er oprettet ud fra skabelonen **Datalækager** , har defineret alle brugere som i området, behandles DLP-beskeder med høj alvorsgrad kun for brugerne i salgsteamet. Politikken for insiderrisiko modtager ikke DLP-beskeder med høj prioritet, som brugerne skal behandle, og som ikke er defineret i DLP-reglerne i dette eksempel. Omvendt, hvis din politik for styring af insiderrisiko, der er oprettet ud fra **datalækageskabeloner** , er begrænset til kun at omfatte brugere i salgsteamet, og den tildelte DLP-politik er begrænset til alle brugere, vil insiderrisikopolitikken kun behandle DLP-beskeder med høj alvorsgrad for medlemmer af salgsteamet. Politikken for styring af insiderrisiko ignorerer DLP-beskeder med høj alvorsgrad for alle brugere, der ikke er i salgsteamet.

- Sørg for, at regelindstillingen **Hændelsesrapporter** i den DLP-politik, der bruges til denne skabelon til styring af insiderrisiko, er konfigureret til beskeder på *højt* alvorsgradsniveau. Niveauet *Høj* alvorsgrad er de udløsende hændelser, og beskeder om styring af insiderrisiko genereres ikke ud fra regler i DLP-politikker, hvor feltet **Hændelsesrapporter** er angivet til *Lav* eller *Mellem*.

    ![DLP-politikbeskedindstilling.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Når du opretter en ny DLP-politik ved hjælp af de indbyggede skabeloner, skal du vælge indstillingen **Opret eller tilpas avancerede DLP-regler** for at konfigurere indstillingen **Hændelsesrapporter** for niveauet *Høj* alvorsgrad.

Hver politik for styring af insiderrisiko, der er oprettet ud fra skabelonen **Datalækager** , kan kun tildeles én DLP-politik, når du bruger denne indstilling for udløserhændelse. Overvej at oprette en dedikeret DLP-politik, der kombinerer de forskellige aktiviteter, du vil registrere og fungere som udløsende hændelser for insiderrisikopolitikker, der bruger skabelonen **Datalækager** .

Se artiklen [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md) for at få en trinvis vejledning til, hvordan du konfigurerer DLP-politikker for din organisation.

### <a name="data-leaks-by-priority-users-preview"></a>Datalækager fra prioriterede brugere (prøveversion)

Beskyttelse af data og forebyggelse af datalækager for brugere i din organisation kan afhænge af deres placering, adgangsniveau til følsomme oplysninger eller risikohistorik. Datalækager kan omfatte utilsigtet overdeling af meget følsomme oplysninger uden for din organisation eller datatyveri med ondsindede hensigter. Med en tildelt DLP-politik (forebyggelse af datatab) som en udløserhændelsesmulighed begynder denne skabelon at score registreringer i realtid af mistænkelig aktivitet og resultere i en øget sandsynlighed for insiderrisikobeskeder og beskeder med højere alvorsgradsniveauer. Prioritetsbrugere defineres i [prioriterede brugergrupper](insider-risk-management-settings.md#priority-user-groups-preview) , der er konfigureret i området indstillinger for styring af insiderrisiko.

Som med **skabelonen Generelle datalækager** kan du vælge en DLP-politik til at udløse indikatorer i insiderrisikopolitikken for beskeder med høj alvorsgrad i din organisation. Følg retningslinjerne for datalækagepolitik for DLP-politikker, når du opretter en politik med indstillingen DLP, når du bruger denne skabelon. Du kan også vælge at tildele valgte indikatorer som udløsende hændelser for en politik. Denne fleksibilitet og tilpasning hjælper med at tilpasse politikken til de aktiviteter, der er omfattet af indikatorerne. Derudover skal du tildele prioritetsbrugergrupper, der er oprettet i **Indstillinger for** >  **styring af insiderrisiko,** > **Prioritet af brugergrupper** til politikken.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Datalækager fra utilfredse brugere (prøveversion)

Når brugerne oplever stressfaktorer for beskæftigelse, kan de blive utilfredse, hvilket kan øge chancerne for insiderrisikoaktivitet. Denne skabelon starter brugeraktivitet med point, når der identificeres en indikator, der er knyttet til disgruntlement. Eksempler omfatter meddelelser om forbedring af ydeevnen, anmeldelser af dårlig ydeevne eller ændringer af status på jobniveau. Datalækager til utilfredse brugere kan omfatte download af filer fra SharePoint Online og kopiering af data til personlige cloudbeskeder og lagertjenester i nærheden af stressorhændelser i forbindelse med beskæftigelse.

Når du bruger denne skabelon, skal du også konfigurere en Microsoft 365 HR-connector for jævnligt at importere meddelelser om forbedring af ydeevnen, status for gennemgang af dårlig ydeevne eller ændringsoplysninger på jobniveau for brugere i din organisation. Se artiklen [Importér data med HR-connectoren](import-hr-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation.

### <a name="general-security-policy-violations-preview"></a>Generelle sikkerhedspolitiske overtrædelser (prøveversion)

I mange organisationer har brugerne tilladelse til at installere software på deres enheder eller til at ændre enhedsindstillinger for at hjælpe med deres opgaver. Brugere kan enten utilsigtet eller med ondsindede hensigter installere malware eller deaktivere vigtige sikkerhedsfunktioner, der hjælper med at beskytte oplysninger på deres enhed eller på dine netværksressourcer. Denne politikskabelon bruger sikkerhedsbeskeder fra Microsoft Defender for Endpoint til at begynde at score disse aktiviteter og fokusere registrering og beskeder til dette risikoområde. Brug denne skabelon til at give indsigt i sikkerhedspolitikovertrædelser i scenarier, hvor brugerne kan have en historik over sikkerhedspolitiske overtrædelser, der kan være en indikator for insiderrisiko.

Du skal have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan finde flere oplysninger om konfiguration af Defender for Endpoint til integration af styring af insiderrisiko under [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="general-patient-data-misuse-preview"></a>Generel misbrug af patientdata (prøveversion)

Beskyttelse af data i sundhedssektoren og forebyggelse af misbrug af patientoplysninger er et vigtigt problem for organisationer i sundhedssektoren. Dette misbrug kan omfatte fortrolige datalækager til uautoriserede personer, svigagtig ændring af patientjournaler eller tyveri af patientjournaler. Forebyggelse af dette misbrug af patientdata, enten på grund af manglende opmærksomhed, uagtsomhed eller svig fra brugernes side, er også en vigtig komponent i at opfylde de lovmæssige krav i hipaa-loven (Health Insurance Portability and Accountability Act) og hitech-loven (Health Information Technology for Economic and Clinical Health). Begge disse handlinger fastlægger kravene til sikring af patientbeskyttede sundhedsoplysninger (PHI).

Denne politikskabelon muliggør risikoscore for interne brugere, der registrerer mistænkelige aktiviteter, der er knyttet til poster, der hostes på eksisterende EMR-systemer (Electronic Medical Record). Registrering fokuserer på uautoriseret adgang, visning, ændring og eksport af patientdata. Du skal konfigurere en connector [til Microsoft Healthcare-connectoren](import-healthcare-data.md) eller [Epic-connectoren](import-epic-data.md) for at understøtte registrering af adgangs-, eksfiltrations- eller sløringsaktiviteter i dit EMR-system.

Når du bruger denne skabelon, skal du også konfigurere en Microsoft 365 HR-connector for jævnligt at importere organisationsprofildata for brugere i din organisation. Se artiklen [Konfigurer en connector til import af HR-data](/microsoft-365/compliance/import-hr-data) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation.

### <a name="security-policy-violations-by-departing-users-preview"></a>Sikkerhedspolitikovertrædelser af afgåede brugere (prøveversion)

Afrejsende brugere kan, uanset om de forlader dem på positive eller negative vilkår, være større risici for sikkerhedspolitiske overtrædelser. Denne politikskabelon bruger Defender for Endpoint-beskeder til at give indsigt i sikkerhedsrelaterede aktiviteter for at hjælpe med at beskytte mod utilsigtede eller skadelige sikkerhedsovertrædelser for afgåede brugere. Disse aktiviteter omfatter den bruger, der installerer malware eller andre potentielt skadelige programmer og deaktiverer sikkerhedsfunktioner på deres enheder. Ved hjælp af enten [Microsoft 365 HR-connectoren](import-hr-data.md) eller muligheden for automatisk at registrere sletning af brugerkonto i Azure Active Directory for din organisation starter denne skabelon scoring for risikoindikatorer, der relaterer til disse sikkerhedsaktiviteter, og hvordan de korrelerer med brugerbeskæftigelsesstatus.

Du skal have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan finde flere oplysninger om konfiguration af Defender for Endpoint til integration af styring af insiderrisiko under [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Sikkerhedspolitikovertrædelser for prioriterede brugere (prøveversion)

Beskyttelse mod sikkerhedsovertrædelser for brugere i din organisation kan afhænge af deres position, adgangsniveau til følsomme oplysninger eller risikohistorik. Da sikkerhedsovertrædelser fra prioriterede brugere kan have en betydelig indvirkning på organisationens kritiske områder, starter denne politikskabelon score på disse indikatorer og bruger Microsoft Defender for Endpoint beskeder til at give indsigt i sikkerhedsrelaterede aktiviteter for disse brugere. Disse aktiviteter kan omfatte de prioriterede brugere, der installerer malware eller andre potentielt skadelige programmer, og deaktivering af sikkerhedsfunktioner på deres enheder. Prioritetsbrugere defineres i prioriterede brugergrupper, der er konfigureret i området indstillinger for styring af insiderrisiko.

Du skal have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan finde flere oplysninger om konfiguration af Defender for Endpoint til integration af styring af insiderrisiko under [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). Derudover skal du tildele prioritetsbrugergrupper, der er oprettet i **Indstillinger for** >  **styring af insiderrisiko,** > **Prioritet af brugergrupper** til politikken.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Sikkerhedspolitikovertrædelser af utilfredse brugere (prøveversion)

Brugere, der oplever stressfaktorer for beskæftigelse, kan have en højere risiko for utilsigtede eller skadelige sikkerhedspolitiske overtrædelser. Disse stressfaktorer kan omfatte, at brugeren placeres på en plan til forbedring af ydeevnen, status for gennemgang af dårlig ydeevne eller sænkes fra deres nuværende position. Denne politikskabelon starter risikoscore baseret på disse indikatorer og aktiviteter, der er knyttet til disse hændelser for disse brugere.

Når du bruger denne skabelon, skal du også konfigurere en Microsoft 365 HR-connector for jævnligt at importere meddelelser om forbedring af ydeevnen, status for gennemgang af dårlig ydeevne eller ændringsoplysninger på jobniveau for brugere i din organisation. Se artiklen [Importér data med HR-connectoren](import-hr-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation.

Du skal også have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan finde flere oplysninger om konfiguration af Defender for Endpoint til integration af styring af insiderrisiko under [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>Forudsætninger for politikskabelon og udløsende hændelser

Afhængigt af den skabelon, du vælger til en politik for styring af insiderrisiko, varierer de udløsende hændelser og politikforudsætningerne. Udløsende hændelser er forudsætninger, der bestemmer, om en bruger er aktiv for en politik for styring af insiderrisiko. Hvis en bruger føjes til en politik for styring af insiderrisiko, men ikke har en udløsende hændelse, evalueres brugeraktiviteten ikke af politikken, medmindre brugeren tilføjes manuelt i dashboardet Brugere. Politikforudsætninger er påkrævede elementer, så politikken modtager de signaler eller aktiviteter, der er nødvendige for at evaluere risikoen.

I følgende tabel vises de udløsende hændelser og forudsætninger for politikker, der er oprettet ud fra hver politikskabelon for styring af insiderrisiko:

| **Politikskabelon** | **Udløsende hændelser for politikker** | **Forudsætninger** |
| :------------------ | :--------------------------------- | :---------------- |
| **Datatyveri foretaget af afrejsende brugere** | Indikator for fratrædelsesdato eller slutdato fra sletning af HR-connector eller Azure Active Directory-konto | (valgfrit) Microsoft 365 HR-connector, der er konfigureret til indikatorer for afslutning og fratrædelsesdato |
| **Generelle datalækager** | Politikaktivitet for datalækage, der opretter en besked med *høj alvorsgrad* eller indbyggede eksfiltrationshændelsesudløsere | DLP-politik, der er konfigureret til beskeder *med høj alvorsgrad* <br><br> ELLER <br><br> Brugerdefinerede udløserindikatorer |
| **Datalækager fra prioriterede brugere** | Politikaktivitet for datalækage, der opretter en besked med *høj alvorsgrad* eller indbyggede eksfiltrationshændelsesudløsere | DLP-politik, der er konfigureret til beskeder *med høj alvorsgrad* <br><br> ELLER <br><br> Brugerdefinerede udløserindikatorer <br><br> Prioriterede brugergrupper, der er konfigureret i indstillinger for insiderrisiko |
| **Datalækager fra utilfredse brugere** | Indikatorer for forbedring af ydeevnen, dårlig ydeevne eller ændring af jobniveau fra HR-connector | Microsoft 365 HR-connector, der er konfigureret til disgruntlementindikatorer |
| **Overtrædelser af den generelle sikkerhedspolitik** | Forsvarsunddragelse af sikkerhedskontroller eller uønsket software, der opdages af Microsoft Defender for Endpoint | Abonnement på aktive Microsoft Defender for Endpoint <br><br> Microsoft Defender for Endpoint integration med Microsoft Purview-compliance-portal konfigureret |
| **Generel misbrug af patientdata** | Forsvarsunddragelse af sikkerhedskontroller fra EMR-systemer <br><br> Matchende indikatorer for bruger- og patientadresse fra HR-systemer | Adgangsindikatorer for sundhedssektoren, der er valgt i politik eller indstillinger for insiderrisiko <br><br> Microsoft 365 HR-connector, der er konfigureret til adressematchning <br><br> Konfigureret Microsoft Healthcare- eller Epic-connector |
| **Sikkerhedspolitikovertrædelser af afrejsende brugere** | Indikatorer for fratrædelses- eller slutdato fra sletning af HR-connector eller Azure Active Directory-konto | (valgfrit) Microsoft 365 HR-connector, der er konfigureret til indikatorer for afslutning og fratrædelsesdato <br><br> Abonnement på aktive Microsoft Defender for Endpoint <br><br> Microsoft Defender for Endpoint integration med Microsoft Purview-compliance-portal konfigureret |
| **Sikkerhedspolitiske overtrædelser af prioriterede brugere** | Forsvarsunddragelse af sikkerhedskontroller eller uønsket software, der opdages af Microsoft Defender for Endpoint | Abonnement på aktive Microsoft Defender for Endpoint <br><br> Microsoft Defender for Endpoint integration med Microsoft Purview-compliance-portal konfigureret <br><br> Prioriterede brugergrupper, der er konfigureret i indstillinger for insiderrisiko |
| **Sikkerhedspolitikovertrædelser af utilfreds bruger** | Indikatorer for forbedring af ydeevnen, dårlig ydeevne eller ændring af jobniveau fra HR-connector | Microsoft 365 HR-connector, der er konfigureret til disgruntlementindikatorer <br><br> Abonnement på aktive Microsoft Defender for Endpoint <br><br> Microsoft Defender for Endpoint integration med Microsoft Purview-compliance-portal konfigureret |

## <a name="prioritize-content-in-policies"></a>Prioriter indhold i politikker

Politikker for styring af insiderrisiko understøtter angivelse af en højere prioritet for indhold, afhængigt af hvor det er gemt, typen af indhold, eller hvordan det klassificeres. Hvis indhold angives som en prioritet, øges risikoscoren for alle tilknyttede aktiviteter, hvilket igen øger risikoen for at generere en besked med høj alvorsgrad. Nogle aktiviteter genererer dog slet ikke en besked, medmindre det relaterede indhold indeholder indbyggede eller brugerdefinerede følsomme infotyper eller er angivet som en prioritet i politikken.

Din organisation har f.eks. et dedikeret SharePoint-websted til et meget fortroligt projekt. Datalækager til information på dette SharePoint-websted kan kompromittere projektet og have en betydelig indvirkning på dets succes. Ved at prioritere dette SharePoint-websted i en politik for datalækager øges risikoscores for kvalificerede aktiviteter automatisk. Denne prioritering øger sandsynligheden for, at disse aktiviteter genererer en insiderrisikobesked og øger alvorsgraden for beskeden.

Når du opretter en politik for styring af insiderrisiko i guiden Politik, kan du vælge mellem følgende prioriteter:

- **SharePoint-websteder**: Alle aktiviteter, der er knyttet til alle filtyper på definerede SharePoint-websteder, tildeles en højere risikoscore. Brugere, der konfigurerer politikken og vælger prioriterede Share Point-websteder, kan vælge SharePoint-websteder, som de har tilladelse til at få adgang til. Hvis den aktuelle bruger ikke kan vælge SharePoint-websteder i politikken, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de påkrævede websteder.
- **Følsomme oplysningstyper**: Alle aktiviteter, der er knyttet til indhold, som indeholder [følsomme oplysningstyper](sensitive-information-type-entity-definitions.md) , tildeles en højere risikoscore.
- **Følsomhedsmærkater**: Alle aktiviteter, der er knyttet til indhold, som har specifikke [følsomhedsmærkater](sensitivity-labels.md) , tildeles en højere risikoscore.
- **Filtypenavne**: Alle aktiviteter, der er knyttet til indhold, som har bestemte filtypenavne. Brugere, der konfigurerer en politik for datatyveri/lækage, som vælger **Filtypenavne, der skal prioriteres** i politikguiden, kan definere op til 50 filtypenavne, der skal prioriteres i politikken. De angivne udvidelser kan indeholde eller udelade et '.' som det første tegn i den prioriterede udvidelse.

## <a name="sequence-detection"></a>Sekvensregistrering

Risikable aktiviteter kan ikke forekomme som isolerede hændelser. Disse risici er ofte en del af en større sekvens af hændelser. En sekvens er en gruppe af to eller flere brugeraktiviteter, der udføres den ene efter den anden, som kan tyde på en øget risiko. At identificere disse relaterede aktiviteter er en vigtig del af evalueringen af den overordnede risiko. Når sekvensregistrering er aktiveret for politikker for datatyveri eller datalækager, vises indsigt fra aktiviteter med sekvensoplysninger under fanen **Brugeraktivitet** i en sag om styring af insiderrisiko. Følgende politikskabeloner understøtter registrering af sekvenser:

- Datatyveri foretaget af afrejsende brugere
- Generelle datalækager
- Datalækager fra prioriterede brugere
- Datalækager fra utilfredse brugere

Disse politikker for styring af insiderrisiko kan bruge specifikke indikatorer og den rækkefølge, de opstår, til at registrere hvert trin i en sekvens af risiko. Filnavne bruges ved tilknytning af aktiviteter på tværs af en sekvens. Disse risici er organiseret i fire hovedkategorier af aktiviteter:

- **Samling**: Disse kategorisignaler fokuserer på downloadaktiviteter for brugere af politikker i området. Nogle eksempler på aktiviteter i denne kategori er hentning af filer fra SharePoint-websteder eller flytning af filer til en komprimeret mappe.
- **Eksfiltration**: Disse kategorisignaler fokuserer på deling eller udtrækningsaktiviteter til interne og eksterne kilder af brugere af politikker i området. En eksempelaktivitet i denne kategori er at sende mails med vedhæftede filer fra din organisation til eksterne modtagere.
- **Tilsløring**: Disse kategorisignaler fokuserer på maskering af risikable aktiviteter, der udføres af brugere af politikker i området. Nogle eksempelaktiviteter i denne kategori kan være omdøbning af filer på en enhed eller fjernelse eller nedgradering af følsomhedsmærkater i SharePoint-filer.
- **Oprydning**: Disse kategorisignaler fokuserer på sletningsaktiviteter for brugere af politikker i området. Et eksempel på en aktivitet i denne kategori er sletning af filer fra en enhed.

> [!NOTE]
> Sekvensregistrering bruger indikatorer, der er aktiveret i de globale indstillinger for styring af insiderrisiko og indikatorer, der er valgt i en politik. Hvis der ikke er valgt relevante indikatorer, fungerer registrering af sekvenser ikke.

Du kan tilpasse individuelle indstillinger for tærskelværdi for hver type sekvensregistrering, når den er konfigureret i politikken. Disse indstillinger for tærskel justerer beskeder baseret på mængden af filer, der er knyttet til sekvensen.

Hvis du vil vide mere om administration af sekvensregistrering i **visningen Brugeraktivitet** , skal du se [Sager om styring af insiderrisiko: Brugeraktivitet](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Akkumuleret eksfiltrationsregistrering (prøveversion)

Insiderrisikoindikatorer hjælper med at identificere usædvanlige niveauer af risikoaktiviteter, når de evalueres dagligt for brugere, der er omfattet af politikker for insiderrisiko. Akkumuleret eksfiltrationsregistrering bruger modeller til maskinel indlæring til at hjælpe dig med at identificere, hvornår exfiltrationsaktiviteter, som en bruger udfører over en bestemt tid, overstiger den normale mængde, der er udført af brugere i din organisation i de seneste 30 dage over flere eksfiltrationsaktivitetstyper. Hvis en bruger f.eks. delte flere filer end de fleste brugere i løbet af den seneste måned, ville denne aktivitet blive registreret og klassificeret som en kumulativ eksfiltrationsaktivitet.

Analytikere og efterforskere af styring af insiderrisiko kan bruge akkumuleret indsigt i eksfiltrationsregistrering til at identificere eksfiltrationsaktiviteter, der typisk ikke genererer beskeder, men er over det, der er typisk for deres organisation. Nogle eksempler kan være, at brugere, der forlader virksomheden langsomt, exfiltrerer data på tværs af en række dage, eller når brugerne gentagne gange deler data på tværs af flere kanaler mere end normalt for datadeling for din organisation.  Højere risikoscores tildeles til akkumulerede eksfiltrationsaktiviteter for SharePoint-websteder, følsomme oplysningstyper og indhold med [følsomhedsmærkater](/microsoft-365/compliance/sensitivity-labels#label-priority-order-matters), der er konfigureret som prioriteret indhold i en politik, eller til aktiviteter, der involverer mærkater, der er konfigureret som høj prioritet i Microsoft Purview Information Protection.

Akkumuleret eksfiltrationsregistrering er som standard aktiveret, når følgende politikskabeloner bruges:

- Datatyveri foretaget af afrejsende brugere
- Generelle datalækager
- Datalækager fra prioriterede brugere
- Datalækager fra utilfredse brugere

> [!NOTE]
> Akkumuleret eksfiltrationsregistrering bruger exfiltrationsindikatorer, der er aktiveret i de globale indstillinger for insiderrisikostyring og exfiltrationsindikatorer, der er valgt i en politik. Derfor evalueres kumulativ eksfiltrationsregistrering kun for de nødvendige eksfiltrationsindikatorer, der er valgt. Akkumulerede exfiltrationsaktiviteter for [følsomhedsmærkater](sensitivity-labels.md) , der er konfigureret i prioriteret indhold, genererer højere risikoscores.

Når akkumuleret eksfiltrationsregistrering er aktiveret for politikker for datatyveri eller datalækage, vises indsigt fra akkumulerede exfiltrationsaktiviteter under fanen **Brugeraktivitet** i en insiderrisikoadministrationssag.

Hvis du vil vide mere om administration af brugeraktivitet, skal du se [Sager om styring af insiderrisiko: Brugeraktiviteter](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>Politiktilstand

Politikkens tilstandsstatus giver dig indsigt i potentielle problemer med dine politikker for styring af insiderrisiko. Kolonnen **Status** under fanen **Politikker** kan give dig besked om problemer med politikker, der kan forhindre, at brugeraktivitet rapporteres, eller hvorfor antallet af aktivitetsbeskeder er usædvanligt. Politikkens tilstandsstatus kan også bekræfte, at politikken er sund og ikke har brug for opmærksomhed eller konfigurationsændringer.

Hvis der er problemer med en politik, viser politiktilstandsstatus meddelelsesadvarsler og -anbefalinger for at hjælpe dig med at løse politikproblemer. Disse meddelelser kan hjælpe dig med at løse følgende problemer:

- **Politikker med ufuldstændig konfiguration**. Disse problemer kan omfatte manglende brugere eller grupper i politikken eller andre ufuldstændige konfigurationstrin for politikker.
- **Politikker med problemer med indikatorkonfiguration**. Indikatorer er en vigtig del af hver politik. Hvis indikatorer ikke er konfigureret, eller hvis der er valgt for få indikatorer, evaluerer politikken muligvis ikke risikable aktiviteter som forventet.
- **Politikudløsere fungerer ikke, eller kravene til politikudløsere er ikke konfigureret korrekt**. Politikfunktionalitet kan afhænge af andre tjenester eller konfigurationskrav for effektivt at registrere udløsende hændelser for at aktivere tildeling af risikoscore til brugere i politikken. Disse afhængigheder kan omfatte problemer med connectorkonfiguration, Microsoft Defender for Endpoint beskeddeling eller konfigurationsindstillinger for politikker til forebyggelse af datatab.
- **Lydstyrkegrænserne nærmer sig eller overskrider grænserne**. Politikker for styring af insiderrisiko bruger mange Microsoft 365-tjenester og -slutpunkter til at aggregere signaler om risikoaktivitet. Afhængigt af antallet af brugere i dine politikker kan mængdegrænser forsinke identifikation og rapportering af risikoaktiviteter. Få mere at vide om disse grænser i afsnittet Politikskabelongrænser i denne artikel.

Hvis du hurtigt vil have vist en politiks tilstandsstatus, skal du gå til fanen **Politik** og kolonnen **Status** . Her kan du se følgende indstillinger for politiktilstandsstatus for hver politik:

- *Sund*: Der er ikke identificeret nogen problemer med politikken.
- *Anbefalinger*: Der er nogle problemer med politikken, der kan forhindre, at politikken fungerer som forventet.
- *Advarsler*: Der er problemer med politikken, der forhindrer den i at identificere risikable aktiviteter.

Du kan få flere oplysninger om eventuelle anbefalinger eller advarsler ved at vælge en politik under fanen **Politik** for at åbne kortet med oplysninger om politik. Du kan finde flere oplysninger om anbefalinger og advarsler, herunder vejledning i, hvordan du løser disse problemer, i afsnittet **Meddelelser** på detaljekortet.

![Politik for styring af insiderrisiko.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Meddelelser

Brug følgende tabel til at få mere at vide om anbefalinger og advarsler og handlinger, der skal udføres for at løse potentielle problemer.

|Meddelelser|Politikskabeloner|Årsager/Prøv denne handling for at løse problemet|
|---|---|---|
|Politikken tildeler ikke risikoscores til aktivitet|Alle politikskabeloner|Det kan være en god idé at gennemse politikomfanget og udløse hændelseskonfigurationen, så politikken kan tildele risikoscores til aktiviteter <br><br> 1. Gennemse de brugere, der er valgt for politikken. Hvis du har valgt få brugere, kan det være en god idé at vælge flere brugere. <br> 2. Hvis du bruger en HR-connector, skal du kontrollere, at din HR-connector sender de korrekte data. <br> 3. Hvis du bruger en DLP-politik som udløserhændelse, skal du kontrollere konfigurationen af din DLP-politik for at sikre, at den er konfigureret til at blive brugt i denne politik. <br> 4. I forbindelse med politikker for sikkerhedsovertrædelse skal du gennemse status for Microsoft Defender for Endpoint vigtig besked, der er valgt i indstillingerne for Insider-risiko > Intelligente registreringer. Bekræft, at beskedfilteret ikke er for smalt.|
|Politikken har ikke genereret nogen beskeder|Alle politikskabeloner|Det kan være en god idé at gennemse din politikkonfiguration, så du analyserer scoringen af den aktivitet, du interesserer dig for. <br><br> 1. Bekræft, at du har valgt indikatorer, som du vil score. Jo flere indikatorer der vælges, jo flere aktiviteter tildeles risikoscores. <br> 2. Gennemse tilpasning af tærskel for politik. Hvis de valgte tærskler ikke stemmer overens med din organisations risikotolerance, skal du justere valgene, så der oprettes beskeder baseret på dine foretrukne tærskler. <br> 3. Gennemse de brugere og grupper, der er valgt for politikken. Bekræft, at du har valgt alle de relevante brugere og grupper. <br> 4. I forbindelse med politikker for sikkerhedsovertrædelse skal du bekræfte, at du har valgt den vigtige status for vigtige beskeder, som du vil score for Microsoft Defender for Endpoint beskeder i Intelligente registreringer i indstillinger.|
|Ingen brugere eller grupper er inkluderet i denne politik|Alle politikskabeloner|Brugere eller grupper er ikke tildelt politikken. <br><br> Rediger din politik, og vælg brugere eller grupper til politikken.|
|Der er ikke valgt nogen indikatorer for denne politik|Alle politikskabeloner|Der er ikke valgt indikatorer for politikken <br><br> Rediger politikken, og vælg de relevante politikindikatorer for politikken.|
|Der er ikke medtaget nogen prioritetsbrugergrupper i denne politik|- Datalækager fra prioriterede brugere <br> - Prioriterede brugeres overtrædelser af sikkerhedspolitik|Prioritetsbrugergrupper tildeles ikke til politikken. <br><br> Konfigurer prioritetsbrugergrupper i Indstillinger for styring af insiderrisiko, og tildel prioritetsbrugergrupper til politikken.|
|Der er ikke valgt nogen udløsende hændelse for denne politik|Alle politikskabeloner|Der er ikke konfigureret en udløserhændelse for politikken <br><br> Scorer for risici tildeles ikke til brugeraktiviteter, før du redigerer politikken og vælger en udløsende hændelse.|
|HR-connectoren er ikke konfigureret eller fungerer som forventet|- Datatyveri ved afrejsende bruger <br> - Sikkerhedspolitikovertrædelser ved afrejsebruger <br> - Datalækager fra utilfredse brugere <br> – Sikkerhedspolitiske overtrædelser af utilfredse brugere|Der er et problem med HR-connectoren. <br><br> 1. Hvis du bruger en HR-connector, skal du kontrollere, at din HR-connector sender korrekte data <br><br> ELLER <br><br> 2. Vælg den slettede udløserhændelse for Azure AD konto.|
|Der er ikke onboardet nogen enheder|- Datatyveri ved afrejsende brugere <br> – Generelle datalækager <br> - Datalækager fra utilfredse brugere <br> - Datalækager fra prioriterede brugere|Enhedsindikatorer er valgt, men der er ikke nogen enheder, der er onboardet i Microsoft 365 <br><br> Kontrollér, om enheder er onboardet og opfylder kravene.|
|HR-connectoren har ikke uploadet data for nylig|- Datatyveri ved afrejsende bruger <br> - Sikkerhedspolitikovertrædelser ved afrejsebruger <br> - Datalækager fra utilfredse brugere <br> – Sikkerhedspolitiske overtrædelser af utilfredse brugere|HR-connectoren har ikke importeret data i mere end syv dage. <br><br> Kontrollér, at HR-connectoren er konfigureret korrekt og sender data.|
|Vi kan ikke kontrollere status for hr-connectoren lige nu. Kontrollér igen senere|- Datatyveri ved afrejsende bruger <br> - Sikkerhedspolitikovertrædelser ved afrejsebruger <br> - Datalækager fra utilfredse brugere <br> – Sikkerhedspolitiske overtrædelser af utilfredse brugere|Løsningen til styring af insiderrisiko kan ikke kontrollere status for hr-connectoren. <br><br> Kontrollér, at hr-connectoren er konfigureret korrekt og sender data, eller vend tilbage og kontrollér politikstatussen.|
|DLP-politikken er ikke valgt som udløserhændelsen|- Generelle datalækager <br> - Datalækager fra prioriterede brugere|En DLP-politik er ikke blevet valgt som en udløsende hændelse, eller den valgte DLP-politik er blevet slettet. <br><br> Rediger politikken, og vælg enten en aktiv DLP-politik eller "Bruger udfører en eksfiltrationsaktivitet" som udløserhændelse i politikkonfigurationen.|
|DLP-politik, der bruges i denne politik, er deaktiveret|- Generelle datalækager <br> - Datalækager fra prioriterede brugere|DLP-politik, der bruges i denne politik, er deaktiveret. <br><br> 1. Slå den DLP-politik, der er tildelt denne politik, til. <br><br> ELLER <br><br> 2. Rediger denne politik, og vælg enten en ny DLP-politik eller "Bruger udfører en eksfiltrationsaktivitet" som udløserhændelse i politikkonfigurationen.|
|DLP-politikken opfylder ikke kravene|- Generelle datalækager <br> - Datalækager fra prioriterede brugere|DLP-politikker, der bruges som udløserhændelser, skal konfigureres til at generere vigtige beskeder med høj alvorsgrad. <br><br>  1. Rediger din DLP-politik for at tildele relevante beskeder som *Høj alvorsgrad*. <br><br> ELLER <br><br> 2. Rediger denne politik, og vælg *Bruger udfører en eksfiltrationsaktivitet* som udløserhændelse.|
|Organisationen har ikke et Microsoft Defender for Endpoint abonnement|- Overtrædelser af den generelle sikkerhedspolitik <br> - Sikkerhedspolitiske overtrædelser af afrejsende brugere <br> – Sikkerhedspolitiske overtrædelser af utilfredse brugere <br> - Prioriterede brugeres overtrædelser af sikkerhedspolitik|Der blev ikke registreret et aktivt Microsoft Defender for Endpoint-abonnement for din organisation. <br><br> Før der tilføjes et Microsoft Defender for Endpoint abonnement, tildeler disse politikker ikke risikoscores til brugeraktivitet.|
|Microsoft Defender for Endpoint beskeder deles ikke med overholdelsesportalen|- Overtrædelser af den generelle sikkerhedspolitik <br> - Sikkerhedspolitiske overtrædelser af afrejsende brugere <br> – Sikkerhedspolitiske overtrædelser af utilfredse brugere <br> - Prioriterede brugeres overtrædelser af sikkerhedspolitik|Microsoft Defender for Endpoint beskeder deles ikke med overholdelsesportalen. <br><br> Konfigurer deling af Microsoft Defender for Endpoint beskeder.|
|Du nærmer dig den maksimale grænse for brugere, der aktivt scores for denne politikskabelon.|Alle politikskabeloner|Hver politikskabelon har et maksimalt antal brugere i området. Se detaljer om skabelongrænsen. <br><br> Gennemse brugerne under fanen Brugere, og fjern alle brugere, der ikke længere skal have score.|
|Udløsende hændelse forekommer gentagne gange for over 15 % af brugerne i denne politik.|Alle politikskabeloner|Juster udløserhændelsen for at hjælpe med at reducere, hvor ofte brugere føres ind i politikområdet.|

## <a name="policy-template-limits"></a>Grænser for politikskabeloner

Skabeloner til insiderrisikostyringspolitik bruger grænser til at administrere mængden og behandlingshastigheden for brugerrisikoaktiviteter i det omfang, og hvordan denne proces er integreret med understøttende Microsoft 365-tjenester. Hver politikskabelon har et maksimalt antal brugere, der aktivt kan tildeles risikoscores for den politik, som den kan understøtte og effektivt behandle og rapportere risikoaktiviteter. Brugere i området er brugere, der udløser hændelser for politikken.

Grænsen for hver politik beregnes på baggrund af det samlede antal entydige brugere, der modtager risikoscores pr. politikskabelontype. Hvis antallet af brugere for en politikskabelontype er nær eller overskrider brugergrænsen, reduceres politikkens ydeevne. Hvis du vil have vist det aktuelle antal brugere for en politik, skal du gå til fanen Politik og kolonnen Brugere i område. Du kan have op til fem politikker for en hvilken som helst politikskabelon. Disse maksimale grænser gælder for brugere på tværs af alle politikker ved hjælp af en given politikskabelon.

Brug følgende tabel til at bestemme det maksimale antal brugere i området, der understøttes for hver politikskabelon:

|Politikskabelon|Aktuelt maksimum for bruger i område|
|---|---|
|Generel datalækage|15,000|
|Datalækage fra utilfredse brugere|7,500|
|Datalækage fra prioriterede brugere|1,000|
|Datatyveri foretaget af afrejsende brugere|20,000|
|Overtrædelser af den generelle sikkerhedspolitik|1,000|
|Generel misbrug af patientdata|5,000|
|Sikkerhedspolitikovertrædelse af prioriterede brugere|1,000|
|Sikkerhedspolitikovertrædelser af afrejsende brugere|15,000|
|Sikkerhedspolitiske overtrædelser af utilfredse brugere|7,500|

## <a name="create-a-new-policy"></a>Opret en ny politik

Hvis du vil oprette en ny politik for styring af insiderrisiko, skal du bruge guiden Politik i **Insider Risk Management-løsningen** i Microsoft Purview-compliance-portal.

Udfør følgende trin for at oprette en ny politik:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Politikker**.
2. Vælg **Opret politik** for at åbne politikguiden.
3. Vælg en politikkategori på siden **Politikskabelon** , og vælg derefter skabelonen til den nye politik. Disse skabeloner består af betingelser og indikatorer, der definerer de risikoaktiviteter, du vil registrere og undersøge. Gennemse skabelonforudsætningerne, udløsende hændelser og registrerede aktiviteter for at bekræfte, at denne politikskabelon passer til dine behov.

    > [!IMPORTANT]
    > Nogle politikskabeloner har forudsætninger, der skal konfigureres, for at politikken kan generere relevante beskeder. Hvis du ikke har konfigureret de relevante politikforudsætningerne, skal du se **trin 4** ovenfor.

4. Vælg **Næste** for at fortsætte.
5. Udfyld følgende felter på siden **Navn og beskrivelse** :
    - **Navn (obligatorisk)**: Angiv et brugervenligt navn til politikken. Dette navn kan ikke ændres, når politikken er oprettet.
    - **Beskrivelse (valgfrit)**: Angiv en beskrivelse af politikken.

6. Vælg **Næste** for at fortsætte.
7. På siden **Brugere og grupper** skal du vælge **Medtag alle brugere og grupper** eller **Medtag bestemte brugere og grupper** for at definere, hvilke brugere eller grupper der er inkluderet i politikken, eller hvis du har valgt en prioriteret brugerbaseret skabelon. vælg **Tilføj eller rediger prioritetsbrugergrupper**. Hvis du vælger **Medtag alle brugere og grupper** , vil du søge efter udløsende hændelser for alle brugere og grupper i din organisation for at begynde at tildele risikoscores til politikken. Hvis du vælger **Medtag bestemte brugere og grupper** , kan du definere, hvilke brugere og grupper der skal tildeles politikken. Gæstebrugerkonti understøttes ikke.
8. Vælg **Næste** for at fortsætte.
9. På siden Indhold, der **skal prioriteres** kan du tildele (hvis det er nødvendigt) de kilder, der skal prioriteres, hvilket øger chancen for at generere en besked med høj alvorsgrad for disse kilder. Vælg et af følgende muligheder:

    - **Jeg vil angive SharePoint-websteder, følsomhedsmærkater og/eller følsomme oplysningstyper som prioriteret indhold**. Hvis du vælger denne indstilling, kan detaljesider i guiden konfigurere disse kanaler.
    - **Jeg vil ikke angive prioritetsindhold lige nu (det kan du gøre, når politikken er oprettet).** Hvis du vælger denne indstilling, springes kanaldetaljesiderne i guiden over.

10. Vælg **Næste** for at fortsætte.

11. Hvis du har valgt **Jeg vil angive SharePoint-websteder, følsomhedsmærkater, typer af følsomme oplysninger og/eller filtypenavne som prioriteret indhold** i det forrige trin, får du vist detaljesiderne for *SharePoint-websteder*, *følsomme oplysningstyper*, *følsomhedsmærkater* og *filtypenavne*. Brug disse detaljesider til at definere SharePoint, følsomme infotyper og følsomhedsmærkater, der skal prioriteres i politikken.

    - **SharePoint-websteder**: Vælg **Tilføj SharePoint-websted** , og vælg de SharePoint-websteder, du har adgang til, og som du vil prioritere. For eksempel *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Type af følsomme oplysninger**: Vælg **Tilføj type følsomme oplysninger** , og vælg de følsomhedstyper, du vil prioritere. Det kan f.eks *. være "Bankkontonummer for USA"* og *"Kreditkortnummer"*.
    - **Følsomhedsmærkater**: Vælg **Tilføj følsomhedsmærkat** , og vælg de mærkater, du vil prioritere. Det kan f.eks. være *"Fortroligt"* og *"Hemmelig"*.
    - **Filtypenavne**: Tilføj op til 50 filtypenavne. Du kan medtage eller udelade '.' med filtypenavnet. *.py* eller *py* vil f.eks. prioritere Python-filer.

    >[!NOTE]
    >Brugere, der konfigurerer politikken og vælger prioriterede Share Point-websteder, kan vælge SharePoint-websteder, som de har tilladelse til at få adgang til. Hvis den aktuelle bruger ikke kan vælge SharePoint-websteder i politikken, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de påkrævede websteder.

12. Vælg **Næste** for at fortsætte.
13. Hvis du har valgt skabelonerne *Generelle datalækager* eller *Datalækager fra prioriterede brugere* , kan du se indstillinger på siden **Udløsere** for denne politikside for brugerdefinerede udløsende hændelser og politikindikatorer. Du har mulighed for at vælge en DLP-politik eller indikatorer til udløsning af hændelser, der giver brugere, der er tildelt politikken, adgang til aktivitetsscore. Hvis du vælger indstillingen **Bruger matcher en politik til forebyggelse af datatab (DLP),** skal du vælge en DLP-politik på rullelisten DLP-politik for at aktivere udløserindikatorer for DLP-politikken for denne politik for styring af insiderrisiko. Hvis du vælger indstillingen **Bruger, der udløser en eksfiltrationsaktivitet** , skal du vælge en eller flere af de viste indikatorer for hændelsen, der udløser politikken.
    >[!IMPORTANT]
    >Hvis du ikke kan vælge en angivet indikator, skyldes det, at de ikke er aktiveret for din organisation. Hvis du vil gøre dem tilgængelige for at vælge og tildele til politikken, skal du aktivere indikatorerne i **Indstillinger for styring** **af insiderrisikostyring** >  > **Politikindikatorer**.

    Hvis du har valgt andre politikskabeloner, understøttes brugerdefinerede udløserhændelser ikke. De indbyggede hændelser for politikudløsende handlinger gælder, og du fortsætter til trin 23 uden at definere politikattributter.

14. Vælg **Næste** for at fortsætte.
15. Hvis du har valgt skabelonerne *Generelle datalækager* eller *Datalækager af prioriterede brugere* og har valgt **, at Brugeren udfører en eksfiltrationsaktivitet og tilknyttede indikatorer**, kan du vælge brugerdefinerede tærskler eller standardgrænser for de indikatorudløsende hændelser, du har valgt. Vælg enten **Brug standardtærskler (anbefales)** eller **Brug brugerdefinerede tærskler for udløserhændelser**.
16. Vælg **Næste** for at fortsætte.
17. Hvis du har valgt **Brug brugerdefinerede tærskler for udløserhændelser**, skal du for hver indikator for udløsende hændelser, som du valgte i trin 13, vælge det relevante niveau for at generere det ønskede niveau af aktivitetsbeskeder.
18. Vælg **Næste** for at fortsætte.
19. På siden **Politikindikatorer** kan du se de [indikatorer](insider-risk-management-settings.md#indicators), du har defineret som tilgængelige på siden **Indikatorer** **for insiderrisikoindstillinger** > . Vælg de indikatorer, du vil anvende på politikken.

    > [!IMPORTANT]
    > Hvis indikatorer på denne side ikke kan vælges, skal du vælge de indikatorer, du vil aktivere for alle politikker. Du kan bruge knappen **Slå indikatorer** til i guiden eller vælge indikatorer på siden **Indstillinger for politikindikatorer** >  **for styring af insiderrisikostyring** > .

    Hvis du har valgt mindst én *Office* - eller *enhedsindikator* , skal du vælge **boosterne for risikoscore** efter behov. Boostere til risikoscore gælder kun for udvalgte indikatorer.
    Hvis du har valgt en politikskabelon *for datatyveri* eller *datalækager* , skal du vælge en eller flere metoder til **registrering af sekvenser** og en kumulativ metode til **registrering af eksfiltration** , der skal anvendes på politikken.

20. Vælg **Næste** for at fortsætte.
21. På siden **Beslut, om du vil bruge standardtærskelværdier eller brugerdefinerede indikatortærskler** , skal du vælge brugerdefinerede eller standardgrænser for de politikindikatorer, du har valgt. Vælg enten **Brug standardgrænser for alle indikatorer** eller **Angiv brugerdefinerede tærskler** for de valgte politikindikatorer. Hvis du har valgt Angiv brugerdefinerede tærskler, skal du vælge det relevante niveau for at generere det ønskede niveau af aktivitetsbeskeder for hver politikindikator.
22. Vælg **Næste** for at fortsætte.
23. Gennemse de indstillinger, du har valgt for politikken, og eventuelle forslag eller advarsler til dine valg på siden **Gennemse** . Vælg **Rediger** for at ændre en af politikværdierne, eller vælg **Send** for at oprette og aktivere politikken.

## <a name="update-a-policy"></a>Opdater en politik

Hvis du vil opdatere en eksisterende politik for styring af insiderrisiko, skal du bruge guiden Politik i **Insider Risk Management-løsningen** i Microsoft Purview-compliance-portal.

Fuldfør følgende trin for at administrere en eksisterende politik:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Politikker**.
2. Vælg den politik, du vil administrere, på politikdashboardet.
3. På siden med politikoplysninger skal du vælge **Rediger politik**
4. I politikguiden kan du ikke redigere følgende:
    - **Politikskabelon**: Den skabelon, der bruges til at definere de typer risikoindikatorer, der overvåges af politikken.
    - **Navn**: Politikkens fulde navn
5. Opdater beskrivelsen af politikken i feltet **Beskrivelse** på siden **Navn og beskrivelse**.
6. Vælg **Næste** for at fortsætte.
7. På siden **Brugere og grupper** skal du vælge **Medtag alle brugere og grupper** eller **Medtag bestemte brugere og grupper** for at definere, hvilke brugere eller grupper der er inkluderet i politikken, eller hvis du har valgt en prioriteret brugerbaseret skabelon. vælg **Tilføj eller rediger prioritetsbrugergrupper**. Hvis du vælger **Medtag alle brugere og grupper** , vil du søge efter udløsende hændelser for alle brugere og grupper i din organisation for at begynde at tildele risikoscores til politikken. Hvis du vælger **Medtag bestemte brugere og grupper** , kan du definere, hvilke brugere og grupper der skal tildeles politikken. Gæstebrugerkonti understøttes ikke.
8. Vælg **Næste** for at fortsætte.
9. På siden Indhold, der **skal prioriteres** kan du tildele (hvis det er nødvendigt) de kilder, der skal prioriteres, hvilket øger chancen for at generere en besked med høj alvorsgrad for disse kilder. Vælg et af følgende muligheder:

    - **Jeg vil angive SharePoint-websteder, følsomhedsmærkater, typer af følsomme oplysninger og/eller filtypenavne som prioriteret indhold**. Hvis du vælger denne indstilling, kan detaljesider i guiden konfigurere disse kanaler.
    - **Jeg vil ikke angive prioritetsindhold lige nu (det kan du gøre, når politikken er oprettet).** Hvis du vælger denne indstilling, springes kanaldetaljesiderne i guiden over.

10. Vælg **Næste** for at fortsætte.

11. Hvis du har valgt **Jeg vil angive SharePoint-websteder, følsomhedsmærkater og/eller følsomme oplysningstyper som prioriteret indhold** i det forrige trin, får du vist detaljesiderne for *SharePoint-websteder*, *følsomme oplysningstyper* og *følsomhedsmærkater*. Brug disse detaljesider til at definere SharePoint, følsomme infotyper og følsomhedsmærkater, der skal prioriteres i politikken.

    - **SharePoint-websteder**: Vælg **Tilføj SharePoint-websted** , og vælg de SharePoint-websteder, du har adgang til, og som du vil prioritere. For eksempel *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Type af følsomme oplysninger**: Vælg **Tilføj type følsomme oplysninger** , og vælg de følsomhedstyper, du vil prioritere. Det kan f.eks *. være "Bankkontonummer for USA"* og *"Kreditkortnummer"*.
    - **Følsomhedsmærkater**: Vælg **Tilføj følsomhedsmærkat** , og vælg de mærkater, du vil prioritere. Det kan f.eks. være *"Fortroligt"* og *"Hemmelig"*.
    - **Filtypenavne**: Tilføj op til 50 filtypenavne. Du kan medtage eller udelade '.' med filtypenavnet. *.py* eller *py* vil f.eks. prioritere Python-filer.

    >[!NOTE]
    >Brugere, der konfigurerer politikken og vælger prioriterede Share Point-websteder, kan vælge SharePoint-websteder, som de har tilladelse til at få adgang til. Hvis den aktuelle bruger ikke kan vælge SharePoint-websteder i politikken, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de påkrævede websteder.

12. Vælg **Næste** for at fortsætte.
13. Hvis du har valgt skabelonerne *Generelle datalækager* eller *Datalækager fra prioriterede brugere* , kan du se indstillinger på siden **Udløsere** for denne politikside for brugerdefinerede udløsende hændelser og politikindikatorer. Du har mulighed for at vælge en DLP-politik eller indikatorer til udløsning af hændelser, der giver brugere, der er tildelt politikken, adgang til aktivitetsscore. Hvis du vælger indstillingen **Bruger matcher en politik til forebyggelse af datatab (DLP),** skal du vælge en DLP-politik på rullelisten DLP-politik for at aktivere udløserindikatorer for DLP-politikken for denne politik for styring af insiderrisiko. Hvis du vælger indstillingen **Bruger, der udløser en eksfiltrationsaktivitet** , skal du vælge en eller flere af de viste indikatorer for hændelsen, der udløser politikken.
    >[!IMPORTANT]
    >Hvis du ikke kan vælge en angivet indikator, skyldes det, at de ikke er aktiveret for din organisation. Hvis du vil gøre dem tilgængelige for at vælge og tildele til politikken, skal du aktivere indikatorerne i **Indstillinger for styring** **af insiderrisikostyring** >  > **Politikindikatorer**.

    Hvis du har valgt andre politikskabeloner, understøttes brugerdefinerede udløserhændelser ikke. De indbyggede hændelser for politikudløsende handlinger gælder, og du fortsætter til trin 23 uden at definere politikattributter.

14. Vælg **Næste** for at fortsætte.
15. Hvis du har valgt skabelonerne *Generelle datalækager* eller *Datalækager af prioriterede brugere* og har valgt **, at Brugeren udfører en eksfiltrationsaktivitet og tilknyttede indikatorer**, kan du vælge brugerdefinerede tærskler eller standardgrænser for de indikatorudløsende hændelser, du har valgt. Vælg enten **Brug standardtærskler (anbefales)** eller **Brug brugerdefinerede tærskler for udløserhændelser**.
16. Vælg **Næste** for at fortsætte.
17. Hvis du har valgt **Brug brugerdefinerede tærskler for udløserhændelser**, skal du for hver indikator for udløsende hændelser, som du valgte i trin 13, vælge det relevante niveau for at generere det ønskede niveau af aktivitetsbeskeder.
18. Vælg **Næste** for at fortsætte.
19. På siden **Politikindikatorer** kan du se de [indikatorer](insider-risk-management-settings.md#indicators), du har defineret som tilgængelige på siden **Indikatorer** **for insiderrisikoindstillinger** > . Vælg de indikatorer, du vil anvende på politikken.

    > [!IMPORTANT]
    > Hvis indikatorer på denne side ikke kan vælges, skal du vælge de indikatorer, du vil aktivere for alle politikker. Du kan bruge knappen **Slå indikatorer** til i guiden eller vælge indikatorer på siden **Indstillinger for politikindikatorer** >  **for styring af insiderrisikostyring** > .

    Hvis du har valgt mindst én *Office* - eller *enhedsindikator* , skal du vælge **boosterne for risikoscore** efter behov. Boostere til risikoscore gælder kun for udvalgte indikatorer.
    Hvis du har valgt en politikskabelon *for datatyveri* eller *datalækager* , skal du vælge en eller flere metoder til **registrering af sekvenser** og en kumulativ metode til **registrering af eksfiltration** , der skal anvendes på politikken.

20. Vælg **Næste** for at fortsætte.
21. På siden **Beslut, om du vil bruge standardtærskelværdier eller brugerdefinerede indikatortærskler** , skal du vælge brugerdefinerede eller standardgrænser for de politikindikatorer, du har valgt. Vælg enten **Brug standardgrænser for alle indikatorer** eller **Angiv brugerdefinerede tærskler** for de valgte politikindikatorer. Hvis du har valgt Angiv brugerdefinerede tærskler, skal du vælge det relevante niveau for at generere det ønskede niveau af aktivitetsbeskeder for hver politikindikator.
22. Vælg **Næste** for at fortsætte.
23. Gennemse de indstillinger, du har valgt for politikken, og eventuelle forslag eller advarsler til dine valg på siden **Gennemse** . Vælg **Rediger** for at ændre en af politikværdierne, eller vælg **Send** for at oprette og aktivere politikken.

## <a name="copy-a-policy"></a>Kopiér en politik

Du skal muligvis oprette en ny politik, der svarer til en eksisterende politik, men som kun har brug for nogle få konfigurationsændringer. I stedet for at oprette en ny politik fra bunden kan du kopiere en eksisterende politik og derefter redigere de områder, der skal opdateres i den nye politik.

Fuldfør følgende trin for at kopiere en eksisterende politik:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Politikker**.
2. Vælg den politik, du vil kopiere, på politikdashboardet.
3. Vælg Kopiér på siden med politikoplysninger.
4. I politikguiden skal du navngive den nye politik og opdatere politikkonfigurationen efter behov.

## <a name="immediately-start-scoring-user-activity"></a>Start straks brugeraktivitet med point

Der kan være scenarier, hvor du skal begynde at tildele risikoscores til brugere med insiderrisikopolitikker uden for arbejdsprocessen for insiderrisikostyring, der udløser hændelse. Brug **Start resultataktivitet for brugere** under fanen **Politikker** til manuelt at føje en bruger (eller brugere) til en eller flere insiderrisikopolitikker i et bestemt tidsrum, til straks at begynde at tildele risikoscores til deres aktivitet og til at tilsidesætte kravet om, at en bruger har en udløserindikator (f.eks. et DLP-politikmatch). Du kan også føje en årsag til, at brugeren føjes til politikken, som vises på brugernes aktivitetstidslinje. Brugere, der manuelt er føjet til politikker, vises i dashboardet **Brugere** , og der oprettes beskeder, hvis aktiviteten opfylder tærsklerne for politikbeskeder.

Nogle scenarier, hvor det kan være en god ide at starte med at score brugeraktiviteter med det samme:

- Når brugere identificeres med risikobekymringer, og du straks vil begynde at tildele risikoscores til deres aktivitet for en eller flere af dine politikker
- Når der er en hændelse, der kan kræve, at du straks begynder at tildele risikoscores til de involverede brugeres aktivitet for en eller flere af dine politikker
- Når du ikke har konfigureret din HR-connector endnu, men du vil begynde at tildele risikoscores til brugeraktiviteter for HR-hændelser ved at uploade en .csv fil for brugerne

> [!NOTE]
> Det kan tage flere timer, før nye manuelt tilføjede brugere vises i dashboardet **Brugere** . Det kan tage op til 24 timer at vise aktiviteter for de foregående 90 dage for disse brugere. Hvis du vil have vist aktiviteter for manuelt tilføjede brugere, skal du gå til fanen **Brugere** og vælge brugeren på dashboardet **Brugere** og åbne fanen **Brugeraktivitet** i detaljeruden.

Hvis du vil starte scoringsaktiviteten manuelt for brugere i en eller flere politikker for styring af insiderrisiko, skal du fuldføre følgende trin:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Politikker**.
2. Vælg den eller de politikker, du vil føje brugere til, på politikdashboardet.
3. Vælg **Start resultataktivitet for brugere**.
4. I **feltet Årsag** i ruden **Føj brugere til flere politikker** skal du tilføje en årsag til at tilføje brugerne.
5. I feltet **Dette skal vare i (vælg mellem 5 og 30 dage)** skal du definere det antal dage, hvor brugerens aktivitet skal bedømmes for den politik, brugeren føjes til
6. Hvis du vil søge i Active Directory efter brugere, skal du bruge feltet **Søg bruger til at føje til politikker** . Skriv navnet på den bruger, du vil føje til politikkerne. Vælg brugernavnet, og gentag for at tildele flere brugere til politikkerne. Listen over de brugere, du har valgt, vises i sektionen Brugere i ruden Føj brugere til flere politikker.
7. Hvis du vil importere en liste over brugere, der skal føjes til politikkerne, skal du vælge **Importér** for at importere en .csv fil (kommaseparerede værdier). Filen skal være i følgende format, og du skal angive brugerens hovednavne i filen:

    ```csv
    user principal name
    user1@domain.com
    user2@domain.com
    ```

8. Vælg Føj brugere til politikker for at acceptere ændringerne og føje brugere til politikkerne, eller vælg Annuller for at slette ændringerne og lukke dialogboksen.

## <a name="stop-scoring-users-in-a-policy"></a>Stop brugere med point i en politik

Hvis du vil stoppe scoringsbrugerne i en politik, skal du se artiklen [Brugere af styring af insiderrisiko: Fjern brugere fra tildeling i omfang til politikker](insider-risk-management-users.md#remove-users-from-in-scope-assignment-to-policies) .

## <a name="delete-a-policy"></a>Slet en politik

> [!NOTE]
> Hvis du sletter en politik, slettes aktive eller arkiverede beskeder, der genereres fra politikken, ikke.

Hvis du vil slette en eksisterende politik for styring af insiderrisiko, skal du udføre følgende trin:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Politikker**.
2. Vælg den politik, du vil slette, på politikdashboardet.
3. Vælg **Slet** på dashboardværktøjslinjen.
4. Vælg **Ja** i dialogboksen **Slet** for at slette politikken, eller vælg **Annuller** for at lukke dialogboksen.
