---
title: Virtuelle aftaler med Teams – integration i Epic EHR
author: LanaChin
ms.author: v-lanachin
manager: samanro
audience: ITPro
ms.topic: conceptual
ms.service: microsoft-365-frontline
search.appverid: MET150
searchScope:
- Microsoft Teams
- Microsoft Cloud for Healthcare
f1.keywords:
- NOCSH
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- Teams_ITAdmin_Healthcare
- microsoftcloud-healthcare
- m365solution-healthcare
- m365solution-scenario
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.reviewer: ansantam
description: Få mere at vide om, hvordan du integrerer Teams EHR-connectoren for at gøre det muligt for sundhedsudbydere i din organisation at foretage virtuelle aftaler med patienter eller andre udbydere i Teams direkte fra Epic EHR-systemet.
ms.openlocfilehash: 0d3a4818b327171a03506425d1fbd849eeafdd88
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66824062"
---
# <a name="virtual-appointments-with-teams---integration-into-epic-ehr"></a>Virtuelle aftaler med Teams – integration i Epic EHR

Microsoft Teams EHR-connectoren (Electronic Health Record) gør det nemt for klinikere at starte en virtuel patientaftale eller rådspørge en anden udbyder i Microsoft Teams direkte fra Epic EHR-systemet. Teams, der er bygget på Microsoft 365-cloudmiljøet, muliggør simpelt, sikkert samarbejde og kommunikation med chat-, video-, stemme- og sundhedsværktøjer i en enkelt hub, der understøtter overholdelse af HIPAA, HITECH-certificering og meget mere.

Teams' kommunikations- og samarbejdsplatform gør det nemt for klinikere at skære igennem rodet i fragmenterede systemer, så de kan fokusere på at yde den bedst mulige pleje. Med Teams EHR-connectoren kan du:

- Start virtuelle Teams-aftaler fra dit Epic EHR-system med en integreret klinisk arbejdsproces.
- Gør det muligt for patienterne at deltage i virtuelle Teams-aftaler fra patientportalen eller via sms.
- Understøtte andre scenarier, herunder flere deltagere, gruppebesøg og tolketjenester.
- Skriv metadata tilbage til EHR-systemet om virtuelle Teams-aftaler, der skal registreres, når deltagerne opretter forbindelse, afbryder forbindelsen og aktiverer automatisk overvågning og registrering.
- Få vist rapporter over forbrugsdata og oplysninger om opkaldskvalitet, der kan tilpasses, for aftaler, der er forbundet med EHR.

I denne artikel beskrives det, hvordan du konfigurerer Teams EHR-connectoren til at integrere med Epic-platformen i din sundhedsorganisation. Den giver dig også et overblik over den virtuelle Teams-aftaleoplevelse fra Epic EHR-systemet.

## <a name="before-you-begin"></a>Før du begynder

Før du går i gang, er der et par ting, du skal gøre for at forberede integrationen.

### <a name="get-familiar-with-the-integration-process"></a>Bliv fortrolig med integrationsprocessen

Gennemse følgende oplysninger for at få en forståelse af den overordnede integrationsproces.

:::image type="content" source="media/ehr-connector-epic-flow.png" alt-text="Billede, der opsummerer trinnene i den overordnede integrationsproces.":::

| &nbsp; |Anmod om appadgang|Appaktivering|Konfiguration af connector|Episk konfiguration|Test|
|--------|---------|---------|---------|---------|---------|
| **Varighed** | Ca. 12-24 timer| Ca. 24 timer | Ca. 1-3 dage | Ca. 1-3 dage | &nbsp; |
| **Handling**| Du [anmoder om adgang til Teams-appen](#request-access-to-the-teams-app).  | Vi opretter et offentligt og privat nøglecertifikat og uploader dem til Epic. | Du fuldfører konfigurationstrinnene i EHR-connectorkonfigurationsportalen.  | Du arbejder sammen med din Epic-tekniske specialist for at konfigurere FDI-poster i Epic.| Du fuldfører testen i dit testmiljø. |
| **Resultatet**| Vi godkender din organisation til test. | Epic synkroniserer certifikatet for den offentlige nøgle. | Du modtager FDI-poster for Epic-konfigurationen. | Konfigurationen er fuldført. Klar til at teste. | Fuld validering af flow og beslutning om at flytte til produktion. |


### <a name="request-access-to-the-teams-app"></a>Anmod om adgang til Teams-appen

Du skal anmode om adgang til Teams-appen.

1. Anmodning om at downloade Teams-appen på [markedspladsen Epic App Orchard](https://apporchard.epic.com/Gallery?id=16793). Hvis du gør dette, udløses en anmodning fra Epic til Microsoft EHR-connectorteamet.
1. Når du har sendt din anmodning, kan du sende en mail til [TeamsForHealthcare@service.microsoft.com](mailto:teamsforhealthcare@service.microsoft.com) med organisationens navn, lejer-id og mailadressen på din Tekniske Kontakt i Epic.
1. Microsoft EHR-connectorteamet besvarer din mail med bekræftelse af aktivering.

### <a name="review-the-epic-microsoft-teams-telehealth-integration-guide"></a>Gennemse vejledningen til Epic-Microsoft Teams Telehealth Integration

Gennemse [Epic-Microsoft Teams Telehealth Integration Guide](https://galaxy.epic.com/Search/GetFile?Url=1!68!100!100100357) med din Epic tekniske specialist. Sørg for, at alle forudsætninger er opfyldt.

## <a name="prerequisites"></a>Forudsætninger

- Et aktivt abonnement på Microsoft Cloud for Healthcare eller et abonnement på separat tilbud på Microsoft Teams EHR-connector (gennemtvinges kun ved test i et EHR-produktionsmiljø).
- Epic version november 2018 eller nyere.
- Brugerne har en passende Licens til Microsoft 365 eller Office 365, der omfatter Teams-møder.
- Teams bruges i din sundhedsorganisation.
- Dine systemer opfylder alle [software- og browserkrav](/microsoftteams/hardware-requirements-for-the-teams-app) til Teams.

> [!IMPORTANT]
> Sørg for at fuldføre trinnene før integration, og at alle forudsætninger er opfyldt, før du går videre med integrationen.

Integrationstrinnene udføres af følgende personer i din organisation:

- **Global administrator af Microsoft 365**: Den primære person, der er ansvarlig for integrationen. Administratoren konfigurerer connectoren, aktiverer SMS (hvis det er nødvendigt) og tilføjer Epic-kundeanalytikeren, der godkender konfigurationen.
- **Epic-kundeanalytiker**: En person i din organisation, der har legitimationsoplysninger til Epic. De godkender de konfigurationsindstillinger, der er angivet af administratoren, og leverer konfigurationsposterne til Epic.

Microsoft 365-administratoren og Epic-kundeanalytikeren kan være den samme person.

## <a name="set-up-the-teams-ehr-connector"></a>Konfigurer Teams EHR-connectoren

Opsætningen af connectoren kræver, at du:

- [Start konfigurationsportalen for EHR-connectoren](#launch-the-ehr-connector-configuration-portal)
- [Angiv konfigurationsoplysninger](#enter-configuration-information)
- [Aktivér sms-meddelelser (valgfrit)](#enable-sms-notifications-optional)
- [Godkend eller få vist konfigurationen](#approve-or-view-the-configuration)
- [Gennemse og afslut konfigurationen](#review-and-finish-the-configuration)

### <a name="launch-the-ehr-connector-configuration-portal"></a>Start konfigurationsportalen for EHR-connectoren

For at komme i gang starter din Microsoft 365-administrator [ehr-connectorkonfigurationsportalen](https://ehrconnector.teams.microsoft.com) og logger på med deres Legitimationsoplysninger til Microsoft 365.

Din Microsoft 365-administrator kan konfigurere en enkelt organisation eller flere organisationer for at teste integrationen. Konfigurer URL-adressen til test og produktion på konfigurationsportalen. Sørg for at teste integrationen fra Epic-testmiljøet, før du går over til produktion.

> [!NOTE]
> Din Microsoft 365-administrator og Epic-kundeanalytiker skal fuldføre integrationstrinnene på konfigurationsportalen. Hvis du vil konfigurere Epic-konfigurationstrin, skal du kontakte den tekniske specialist i Epic, der er tildelt din organisation.

### <a name="enter-configuration-information"></a>Angiv konfigurationsoplysninger

Derefter gør din Microsoft 365-administrator følgende for at konfigurere integrationen:

1. Tilføjer FHIR-basis-URL-adressen (Fast Health Interoperability Resources) fra din Epic-tekniske specialist og angiver miljøet. Konfigurer så mange FHIR-grundlæggende URL-adresser efter behov, afhængigt af organisationens behov og de miljøer, du vil teste.

    - FHIR-basis-URL-adressen er en statisk adresse, der svarer til serverens FHIR API-slutpunkt. Et eksempel på EN URL-adresse er `https://lamnahealthcare.com/fhir/auth/connect-ocurprd-oauth/api/FHDST`.

    - Du kan konfigurere integrationen for test- og produktionsmiljøer. I forbindelse med den indledende konfiguration opfordrer vi dig til at konfigurere connectoren fra et testmiljø, før du går over til produktion.

1. Tilføjer brugernavnet for Epic-kundeanalytikeren, der godkender konfigurationen i et senere trin.

    :::image type="content" source="media/ehr-connector-epic-configure.png" alt-text="Skærmbillede af siden Konfiguration, der viser den godkender, der tilføjes." lightbox="media/ehr-connector-epic-configure.png":::

### <a name="enable-sms-notifications-optional"></a>Aktivér sms-meddelelser (valgfrit)

> [!NOTE]
> Sms-meddelelser er i øjeblikket kun tilgængelige i USA. Vi arbejder på at gøre denne funktion tilgængelig i andre områder i fremtidige versioner af Teams og opdaterer denne artikel, når den er tilgængelig.

Fuldfør dette trin, hvis din organisation ønsker, at Microsoft skal administrere sms-meddelelser for dine patienter. Når du aktiverer sms-beskeder, modtager dine patienter bekræftelses- og påmindelsesmeddelelser for planlagte aftaler.

Hvis du vil aktivere sms-meddelelser, gør din Microsoft 365-administrator følgende:

1. På siden med sms-meddelelser skal du markere begge afkrydsningsfelter for samtykke for at:

    - Tillad, at Microsoft sender sms-meddelelser til patienter på vegne af din organisation.
    - Bekræft, at du sikrer, at deltagerne har givet samtykke til at sende og modtage sms-beskeder.
    
    :::image type="content" source="media/ehr-connector-epic-sms-notifications.png" alt-text="Skærmbillede af siden med sms-beskeder, der viser afkrydsningsfelterne for samtykke og muligheden for at oprette et telefonnummer." lightbox="media/ehr-connector-epic-sms-notifications.png":::

1. Under **Dine telefonnumre** skal du vælge **Generér et nyt telefonnummer** for at generere et telefonnummer for din organisation. Når du gør dette, startes processen med at anmode om og generere et nyt telefonnummer. Det kan tage op til to minutter at fuldføre denne proces.

    Når telefonnummeret er genereret, vises det på skærmen. Dette nummer vil blive brugt til at sende sms-bekræftelser og påmindelser til dine patienter. Nummeret er klargjort, men er ikke knyttet til FHIR-basis-URL-adressen endnu. Det gør du i næste trin.

    :::image type="content" source="media/ehr-connector-epic-phone-number.png" alt-text="Skærmbillede, der viser et eksempel på det telefonnummer, der er genereret." lightbox="media/ehr-connector-epic-phone-number.png":::

    Vælg **Udført**, og vælg derefter **Næste**.

1. Hvis du vil knytte telefonnummeret til en FHIR-basis-URL-adresse, skal du vælge nummeret under **Telefonnummer** i afsnittet **SMS-konfiguration** . Gør dette for hver FHIR-basis-URL-adresse, som du vil aktivere sms-meddelelser for.

    :::image type="content" source="media/ehr-connector-epic-link-phone-number.png" alt-text="Skærmbillede, der viser, hvordan du linker et telefonnummer til en FHIR-basis-URL-adresse." lightbox="media/ehr-connector-epic-link-phone-number.png":::

    Hvis det er første gang, du konfigurerer connectoren, kan du se den FHIR-basis-URL-adresse, der blev angivet i det tidligere trin. Det samme telefonnummer kan knyttes til flere FHIR-base-URL-adresser, hvilket betyder, at patienterne vil modtage sms-beskeder fra det samme telefonnummer for forskellige organisationer og/eller afdelinger.

1. Vælg **SMS-konfiguration** ud for hver FHIR-basis-URL-adresse for at konfigurere de typer sms-meddelelser, der skal sendes til dine patienter.

    :::image type="content" source="media/ehr-connector-epic-sms-setup.png" alt-text="Skærmbillede, der viser indstillinger for sms-konfiguration." lightbox="media/ehr-connector-epic-sms-setup.png":::

    - **Bekræftelses-SMS**: Beskeder sendes til patienter, når en aftale er planlagt, opdateret eller annulleret i EHR-systemet.
    - **Påmindelses-SMS**: Meddelelser sendes til patienterne i henhold til det tidsinterval, du angiver, og det planlagte tidspunkt for aftalen.

    Vælg **Gem**.

1. Vælg **Overfør certifikat** for at overføre et certifikat med en offentlig nøgle. Du skal uploade et Base64-kodet .cer-certifikat (kun offentlig nøgle) for hvert miljø.

    Der kræves et certifikat med en offentlig nøgle for at modtage aftaleoplysninger til afsendelse af sms-meddelelser. Certifikatet skal bruges til at bekræfte, at de indgående oplysninger kommer fra en gyldig kilde.

    Når connectoren bruges til at sende sms-påmindelser, sendes patientens telefonnummer af Epic i en HL7v2-nyttedata, når der oprettes aftaler i Epic. Disse tal gemmes for hver aftale i organisationens geografi og bevares, indtil aftalen finder sted. Hvis du vil vide mere om, hvordan du konfigurerer HL7v2-meddelelser, skal du se [Epic-Microsoft Teams Telehealth Integration Guide](https://galaxy.epic.com/Search/GetFile?Url=1!68!100!100100357).

    Vælg **Næste**.

> [!NOTE]
> Din Microsoft 365-administrator kan når som helst opdatere alle SMS-indstillingerne. Vær opmærksom på, at ændring af indstillinger kan resultere i en afbrydelse af SMS-tjenesten. Du kan få flere oplysninger om, hvordan du får vist SMS-rapporter, under [Teams EHR-connector Virtuelle Aftaler rapport](ehr-connector-report.md).

### <a name="approve-or-view-the-configuration"></a>Godkend eller få vist konfigurationen

Epic-kundeanalytikeren i din organisation, der blev tilføjet som godkender, starter [EHR-connectorkonfigurationsportalen](https://ehrconnector.teams.microsoft.com) og logger på med deres legitimationsoplysninger til Microsoft 365. Når valideringen er fuldført, bliver godkenderen bedt om at logge på med sine Epic-legitimationsoplysninger for at validere Epic-organisationen.

> [!Note]
> Hvis Microsoft 365-administratoren og Epic-kundeanalytikeren er den samme person, skal du stadig logge på Epic for at validere din adgang. Epic-logon bruges kun til at validere din FHIR-basis-URL-adresse. Microsoft gemmer ikke legitimationsoplysninger eller får ikke adgang til EHR-data med dette logon.

:::image type="content" source="media/ehr-connector-epic-login-approve.png" alt-text="Skærmbillede af siden Godkend eller Vis konfiguration, der viser indstillingen Log på og godkend." lightbox="media/ehr-connector-epic-login-approve.png":::

Efter vellykket logon til Epic **skal** Epic-kundeanalytikeren godkende konfigurationen. Hvis konfigurationen ikke er korrekt, kan din Microsoft 365-administrator logge på konfigurationsportalen og ændre indstillingerne.

:::image type="content" source="media/ehr-connector-epic-approve.png" alt-text="Skærmbillede af siden Godkend eller Vis konfiguration, der viser indstillingen Godkend." lightbox="media/ehr-connector-epic-approve.png":::

### <a name="review-and-finish-the-configuration"></a>Gennemse og afslut konfigurationen

Når konfigurationsoplysningerne godkendes af Epic-administratoren, får du vist integrationsposter for patient- og udbyderstart. Integrationsposterne omfatter:

- Patient- og udbyderposter
- Direkte SMS-post
- Sms-konfigurationspost
- Konfigurationspost for enhedstest

Konteksttokenet til enhedstest findes i patientintegrationsposten. Epic-kundeanalytikeren skal levere disse poster til Epic for at fuldføre konfigurationen af virtuelle aftaler i Epic. Du kan få flere oplysninger i [Epic-Microsoft Teams Telehealth Integration Guide](https://galaxy.epic.com/Search/GetFile?Url=1!68!100!100100357).

> [!Note]  
> Microsoft 365- eller Epic-kundeanalytikeren kan når som helst logge på konfigurationsportalen for at få vist integrationsposter og ændre organisationens konfiguration efter behov.

:::image type="content" source="media/ehr-connector-epic-finish.png" alt-text="Skærmbillede af siden Gennemse og Afslut, der viser integrationsoplysninger." lightbox="media/ehr-connector-epic-finish.png":::

> [!Note]
> Epic-kundeanalytikeren skal fuldføre godkendelsesprocessen for hver FHIR-basis-URL-adresse, der er konfigureret af Microsoft 365-administratoren.

## <a name="launch-teams-virtual-appointments"></a>Start virtuelle Teams-aftaler

Når ehr-connectortrinnene og Epic-konfigurationen er fuldført, er din organisation klar til at understøtte videoaftaler med Teams.

### <a name="virtual-appointments-prerequisites"></a>Forudsætninger for virtuelle aftaler

- Dine systemer skal opfylde alle [software- og browserkrav](/microsoftteams/hardware-requirements-for-the-teams-app) til Teams.

- Du har fuldført integrationskonfigurationen mellem Epic-organisationen og din Microsoft 365-organisation.

### <a name="provider-experience"></a>Udbyderoplevelse

Sundhedsudbydere fra din organisation kan deltage i aftaler ved hjælp af Teams fra deres Epic-udbyderapps (Hyperspace, Haiku, Canto). Knappen **Start virtuelt besøg** er integreret i udbyderflowet.

  ![Udbyderens oplevelse af en virtuel aftale med patienten.](media/ehc-provider-experience-6.png)

Nøglefunktioner i udbyderoplevelsen:

- Providere kan tilmelde sig aftaler ved hjælp af understøttede browsere eller Teams-appen.

- Providere skal logge på én gang med deres Microsoft 365-konto, første gang de tilmelder sig en aftale.

- Efter engangslogon sendes udbyderen direkte til den virtuelle aftale i Teams. (Udbyderen skal være logget på Teams).

- Udbydere kan se opdateringer i realtid af deltagere, der opretter forbindelse og afbryder forbindelsen for en given aftale. Udbyderne kan se, hvornår patienten har forbindelse til en aftale.

> [!NOTE]
> Alle oplysninger, der er angivet i mødechatten, og som er nødvendige af hensyn til kontinuitet eller opbevaring af journaler, skal downloades, kopieres og noteres af sundhedsudbyderen. Chatten udgør ikke en juridisk journal eller et angivet registreringssæt. Meddelelser fra chatten gemmes på baggrund af indstillinger, der er oprettet af Microsoft Teams-administratoren.

### <a name="patient-experience"></a>Patientoplevelse

Connectoren understøtter patienter, der deltager i aftaler via et link i sms-sms'en, MyChart-web og mobil. På tidspunktet for aftalen kan patienterne starte aftalen fra MyChart ved hjælp af knappen **Start virtuelt besøg** eller ved at trykke på linket i SMS-sms'en.

  ![Patientoplevelse i forbindelse med en virtuel aftale.](media/ehc-virtual-visit-5.png)

Vigtige funktioner i patientoplevelsen:

- Patienter kan tilmelde sig aftaler fra [moderne webbrowsere på stationære og mobile computere og mobilenheder uden at skulle installere Teams-appen](browser-join.md).
- Patienterne kan teste deres enhedshardware og -forbindelse, før de deltager i en aftale.

    :::image type="content" source="media/ehr-admin-epic-device-test.png" alt-text="Billeder af en mobilenhed, der viser enhedens testfunktioner." lightbox="media/ehr-admin-epic-device-test.png":::
  
    Funktioner til enhedstest:

  - Patienterne kan teste deres højttaler, mikrofon, kamera og forbindelse.
  - Patienterne kan fuldføre et testkald for fuldt ud at validere deres konfiguration.
  - Resultaterne af enhedstesten kan sendes tilbage til EHR-systemet.

- Patienter kan deltage i aftaler med et enkelt klik, og ingen anden konto eller logon er påkrævet.

- Patienterne behøver ikke at oprette en Microsoft-konto eller logge på for at starte en aftale.

- Patienterne placeres i en lobby, indtil udbyderen tilmelder sig og giver dem adgang.

- Patienterne kan teste deres video og mikrofon i lobbyen, før de deltager i aftalen.

> [!Note]
> Epic, MyChart, Haiku og Canto er varemærker tilhørende Epic Systems Corporation.

## <a name="get-insight-into-virtual-appointments-usage"></a>Få indsigt i brug af virtuelle aftaler

[Brugsrapporten for virtuelle besøg](virtual-visits-usage-report.md) i Microsoft Teams Administration giver administratorer et overblik over aktiviteter med virtuelle Teams-aftaler i din organisation. Rapporten viser detaljerede analyser for virtuelle aftaler, herunder Teams EHR-integrerede møder, der udføres fra dit EHR-system.

Du kan få vist vigtige målepunkter, f.eks. lobbyventetid og aftalevarighed. Brug disse oplysninger til at få indsigt i brugstendenser for at hjælpe dig med at optimere virtuelle aftaler for at levere bedre forretningsresultater.

### <a name="privacy-and-location-of-data"></a>Beskyttelse af personlige oplysninger og placering af data

Teams-integration i EHR-systemer optimerer mængden af data, der bruges og gemmes under integration og virtuelle aftaleflows. Løsningen følger de overordnede teams principper og retningslinjer for beskyttelse af personlige oplysninger og dataadministration, der er beskrevet i Teams Privacy.

Teams EHR-connectoren gemmer eller overfører ikke identificerbare personlige data eller sundhedsjournaler for patienter eller sundhedssektoren fra EHR-systemet. De eneste data, der gemmes af EHR-connectoren, er EHR-brugerens entydige id, som bruges under konfiguration af Teams-møder.

EHR-brugerens entydige id gemmes i et af de tre geografiske områder, der er beskrevet i [Hvor dine Microsoft 365-kundedata er gemt](/microsoft-365/enterprise/o365-data-locations). Al chat, optagelser og andre data, der deles i Teams af mødedeltagere, gemmes i henhold til eksisterende lagerpolitikker. Hvis du vil vide mere om placeringen af data i Teams, skal du se [Placering af data i Teams](/microsoftteams/location-of-data-in-teams).

## <a name="related-articles"></a>Relaterede artikler

- [Brugsrapport for virtuelle teams-besøg](virtual-visits-usage-report.md)
- [Teams EHR-connector Virtuelle Aftaler rapport](ehr-connector-report.md)
- [Kom i gang med Teams til sundhedssektoren](teams-in-hc.md)
