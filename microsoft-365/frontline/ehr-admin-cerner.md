---
title: Virtuelle aftaler med Teams – integration i Cerner EHR
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
description: Få mere at vide om, hvordan du integrerer Teams EHR-connectoren for at gøre det muligt for sundhedsudbydere i din organisation at foretage virtuelle aftaler med patienter eller andre udbydere i Teams direkte fra Cerner EHR-systemet.
ms.openlocfilehash: eeb851e0f040d714dd55c5d1b262507a6b5eaf83
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859042"
---
# <a name="virtual-appointments-with-teams---integration-into-cerner-ehr"></a>Virtuelle aftaler med Teams – integration i Cerner EHR

Med Microsoft Teams EHR-connectoren (Electronic Health Record) er det nemt for klinikere at aftale en virtuel patient eller kontakte en anden udbyder i Microsoft Teams direkte fra Cerner EHR-systemet. Teams, der er bygget på Microsoft 365-cloudmiljøet, muliggør simpelt, sikkert samarbejde og kommunikation med chat-, video-, stemme- og sundhedsværktøjer i en enkelt hub, der understøtter overholdelse af HIPAA, HITECH-certificering og meget mere.

Teams' kommunikations- og samarbejdsplatform gør det nemt for klinikere at skære igennem rodet i fragmenterede systemer, så de kan fokusere på at yde den bedst mulige pleje. Med Teams EHR-connectoren kan du:

- Udfør virtuelle Teams-aftaler fra dit Cerner EHR-system med en integreret klinisk arbejdsproces.
- Gør det muligt for patienterne at deltage i virtuelle Teams-aftaler fra mail- eller sms-meddelelser.
- Få vist rapporter over forbrugsdata og oplysninger om opkaldskvalitet, der kan tilpasses, for aftaler, der er forbundet med EHR.

I denne artikel beskrives det, hvordan du konfigurerer Teams EHR-connectoren til at integrere med Cerner-platformen. Den giver dig også et overblik over den virtuelle Teams-aftaleoplevelse fra Cerner EHR-systemet.

## <a name="before-you-begin"></a>Før du begynder

> [!NOTE]
> Sørg for at tale med din Cerner-repræsentant, og gennemse din Cerner-integrationsvejledning, før du aktiverer integrationen.

### <a name="prerequisites"></a>Forudsætninger

Før du integrerer Teams EHR-connectoren i din sundhedsorganisation, skal du have følgende:

- Et aktivt abonnement på Microsoft Cloud for Healthcare eller et abonnement på separat tilbud på Microsoft Teams EHR-connector.
- Brugerne har en passende Licens til Microsoft 365 eller Office 365, der omfatter Teams-møder.
- Teams bruges i din sundhedsorganisation.
- Dine systemer opfylder alle [software- og browserkrav](/microsoftteams/hardware-requirements-for-the-teams-app) til Teams.
- Cerner version november 2018 eller nyere

## <a name="set-up-the-teams-ehr-connector"></a>Konfigurer Teams EHR-connectoren

Opsætningen af connectoren kræver, at du:

- [Start konfigurationsportalen for EHR-connectoren](#launch-the-ehr-connector-configuration-portal)
- [Angiv konfigurationsoplysninger](#enter-configuration-information)
- [Aktivér sms-meddelelser (valgfrit)](#enable-sms-notifications-optional)
- [Gennemse og afslut konfigurationen](ehr-admin-cerner.md#review-and-finish-the-configuration)

> [!IMPORTANT]
> Disse trin skal fuldføres af den globale administrator af Microsoft 365 i din organisation.  

### <a name="launch-the-ehr-connector-configuration-portal"></a>Start konfigurationsportalen for EHR-connectoren

For at komme i gang starter din Microsoft 365-administrator [EHR-connectorkonfigurationsportalen](https://ehrconnector.teams.microsoft.com) og logger på med deres Microsoft-legitimationsoplysninger.

Din Microsoft 365-administrator kan konfigurere en enkelt afdeling eller flere afdelinger for at teste integrationen. Konfigurer URL-adressen til test og produktion på konfigurationsportalen. Sørg for at teste integrationen fra Cerner-testmiljøet, før du går over til produktion.

### <a name="enter-configuration-information"></a>Angiv konfigurationsoplysninger

For at konfigurere integrationen tilføjer Microsoft 365-administratoren en FHIR-basis-URL-adresse (Fast Health Interoperability Resources) fra Cerner og angiver miljøet. Konfigurer så mange FHIR-grundlæggende URL-adresser efter behov, afhængigt af organisationens behov og de miljøer, du vil teste.

:::image type="content" source="media/ehr-admin-cerner-configuration.png" alt-text="Skærmbillede af siden Konfigurationsoplysninger på Teams EHR-connectorkonfigurationsportalen." lightbox="media/ehr-admin-cerner-configuration.png":::

- FHIR-basis-URL-adressen er en statisk adresse, der svarer til serverens FHIR API-slutpunkt. Et eksempel på EN URL-adresse er `https://lamnahealthcare.com/fhir/auth/connect-ocurprd-oauth/api/FHDST`.

- Du kan konfigurere integrationen for test- og produktionsmiljøer. I forbindelse med den indledende konfiguration opfordrer vi dig til at konfigurere connectoren fra et testmiljø, før du går over til produktion.

Når FHIR-basis-URL-adressen er valideret, og miljøet er valgt, skal du vælge **Udført**. Tilføj derefter flere FHIR-grundlæggende URL-adresser til andre miljøer efter behov.

Vælg **Næste** for at gå til næste trin.

### <a name="enable-sms-notifications-optional"></a>Aktivér sms-meddelelser (valgfrit)

Fuldfør dette trin, hvis din organisation ønsker, at Microsoft skal administrere sms-meddelelser for dine patienter. Når du aktiverer sms-beskeder, modtager dine patienter bekræftelses- og påmindelsesmeddelelser for planlagte aftaler.

Hvis du vil aktivere sms-meddelelser, gør din Microsoft 365-administrator følgende:

1. På siden med sms-meddelelser skal du markere begge afkrydsningsfelter for samtykke for at:

    - Tillad, at Microsoft sender sms-meddelelser til patienter på vegne af din organisation.
    - Bekræft, at du sikrer, at deltagerne har givet samtykke til at sende og modtage sms-beskeder.

    :::image type="content" source="media/ehr-admin-cerner-sms-notifications.png" alt-text="Skærmbillede af siden med sms-beskeder, der viser afkrydsningsfelterne for samtykke og muligheden for at oprette et telefonnummer." lightbox="media/ehr-admin-cerner-sms-notifications.png":::

1. Under **Dine telefonnumre** skal du vælge **Generér et nyt telefonnummer** for at generere et telefonnummer for din organisation. Når du gør dette, startes processen med at anmode om og generere et nyt telefonnummer. Det kan tage op til to minutter at fuldføre denne proces.

    Når telefonnummeret er genereret, vises det på skærmen. Dette nummer vil blive brugt til at sende sms-bekræftelser og påmindelser til dine patienter. Nummeret er klargjort, men er ikke knyttet til FHIR-basis-URL-adressen endnu. Det gør du i næste trin.

    :::image type="content" source="media/ehr-admin-cerner-phone-number.png" alt-text="Skærmbillede, der viser et eksempel på det telefonnummer, der er genereret." lightbox="media/ehr-admin-cerner-phone-number.png":::

    Vælg **Udført**, og vælg derefter **Næste**.

1. Hvis du vil knytte telefonnummeret til en FHIR-basis-URL-adresse, skal du vælge nummeret under **Telefonnummer** i afsnittet **SMS-konfiguration** . Gør dette for hver FHIR-basis-URL-adresse, som du vil aktivere sms-meddelelser for.

    :::image type="content" source="media/ehr-admin-cerner-link-phone-number.png" alt-text="Skærmbillede, der viser, hvordan du linker et telefonnummer til en FHIR-basis-URL-adresse." lightbox="media/ehr-admin-cerner-link-phone-number.png":::

    Hvis det er første gang, du konfigurerer connectoren, kan du se den FHIR-basis-URL-adresse, der blev angivet i det tidligere trin. Det samme telefonnummer kan knyttes til flere FHIR-base-URL-adresser, hvilket betyder, at patienterne vil modtage sms-beskeder fra det samme telefonnummer for forskellige organisationer og/eller afdelinger.

     Vælg **Næste**.

### <a name="review-and-finish-the-configuration"></a>Gennemse og afslut konfigurationen

Du får vist integrationsposter til start af patient og udbyder. Disse poster er nødvendige for at fuldføre konfigurationen af virtuelle aftaler i Cerner. Du kan få flere oplysninger i vejledningen til Cerner-Microsoft Teams Telehealth Integration.

> [!NOTE]
> Din Microsoft 365-administrator kan når som helst logge på konfigurationsportalen for at få vist integrationsposter og ændre konfigurationsindstillingerne, hvis det er nødvendigt.

## <a name="launch-teams-virtual-appointments"></a>Start virtuelle Teams-aftaler

Når du har fuldført trinnene i EHR-connectoren og Cerner-konfigurationstrinnene, er din organisation klar til at understøtte videoaftaler med Teams.

### <a name="virtual-appointments-prerequisites"></a>Forudsætninger for virtuelle aftaler

- Dine systemer skal opfylde alle [software- og browserkrav](/microsoftteams/hardware-requirements-for-the-teams-app) til Teams.
- Du har fuldført integrationskonfigurationen mellem Cerner-organisationen og din Microsoft 365-organisation.

### <a name="provider-experience"></a>Udbyderoplevelse

Sundhedssektoren i din organisation kan deltage i aftaler ved hjælp af Teams fra PowerChart-portalen. Udbyderen skal navigere til patientkortet, hvor Teams-indstillingen er tilgængelig.

Herfra kan udbyderen få vist aftaleoplysninger, deltage i aftaler og sende mødelinket. Efter engangslogon sendes udbyderen direkte til den virtuelle aftale i Teams.

Nøglefunktioner i udbyderoplevelsen:

- Providere kan tilmelde sig aftaler ved hjælp af understøttede browsere eller Teams-appen.
- Udbydere kan bruge alle understøttede Teams-mødefunktioner, herunder skærmdeling, brugerdefineret baggrund og optagelse.
- Udbydere kan se opdateringer i realtid af patienter, der opretter forbindelse til en aftale for en given aftale i PowerChart.
- Udbyderoplysninger er ikke synlige for patienter under aftalen.

> [!NOTE]
> Alle oplysninger, der er angivet i mødechatten, og som er nødvendige af hensyn til kontinuitet eller opbevaring af journaler, skal downloades, kopieres og noteres af sundhedsudbyderen. Chatten udgør ikke en juridisk journal eller et angivet registreringssæt. Meddelelser fra chatten gemmes på baggrund af indstillinger, der er oprettet af Microsoft Teams-administratoren.

### <a name="patient-experience"></a>Patientoplevelse

Connectoren understøtter patienter, der deltager i aftaler via et link i SMS-sms'en. På tidspunktet for aftalen kan patienterne starte en aftale ved at trykke på linket i sms-meddelelsen.

Vigtige funktioner i patientoplevelsen

- Patienter kan tilmelde sig aftaler fra [moderne webbrowsere på stationære og mobile computere og mobilenheder uden at skulle installere Teams-appen](browser-join.md).
- Patienter kan deltage i aftaler med et enkelt klik, og ingen anden konto eller logon er påkrævet.
- Patienterne behøver ikke at oprette en Microsoft-konto eller logge på for at starte et besøg.
- Patienterne placeres i en lobby, indtil udbyderen tilmelder sig og giver dem adgang.
- Patienterne kan teste deres video og mikrofon i lobbyen, før de deltager i aftalen.

## <a name="get-insight-into-virtual-appointments-usage"></a>Få indsigt i brug af virtuelle aftaler

[Brugsrapporten for virtuelle besøg](virtual-visits-usage-report.md) i Microsoft Teams Administration giver administratorer et overblik over aktiviteter med virtuelle Teams-aftaler i din organisation. Rapporten viser detaljerede analyser for virtuelle aftaler, herunder Teams EHR-integrerede møder, der udføres fra dit EHR-system.

Du kan få vist vigtige målepunkter, f.eks. lobbyventetid og aftalevarighed. Brug disse oplysninger til at få indsigt i brugstendenser for at hjælpe dig med at optimere virtuelle aftaler for at levere bedre forretningsresultater.

## <a name="privacy-and-location-of-data"></a>Beskyttelse af personlige oplysninger og placering af data

Teams-integration i EHR-systemer optimerer mængden af data, der bruges og gemmes under integration og virtuelle aftaleflows. Løsningen følger de overordnede teams principper og retningslinjer for beskyttelse af personlige oplysninger og dataadministration, der er beskrevet i Teams Privacy.

Teams EHR-connectoren gemmer eller overfører ikke identificerbare personlige data eller sundhedsjournaler for patienter eller sundhedssektoren fra EHR-systemet. De eneste data, som EHR-connectoren gemmer, er EHR-brugerens entydige id, som bruges under konfiguration af Teams-møder.

EHR-brugerens entydige id gemmes i et af de tre geografiske områder, der er beskrevet i [Hvor dine Microsoft 365-kundedata er gemt](/microsoft-365/enterprise/o365-data-locations). Alle chats, optagelser og andre data, der deles i Teams af mødedeltagere, gemmes i henhold til eksisterende lagerpolitikker. Hvis du vil vide mere om placeringen af data i Teams, skal du se [Placering af data i Teams](/microsoftteams/location-of-data-in-teams).

## <a name="related-articles"></a>Relaterede artikler

- [Brugsrapport for virtuelle teams-besøg](virtual-visits-usage-report.md)
- [Teams EHR-connector Virtuelle Aftaler rapport](ehr-connector-report.md)
- [Kom i gang med Teams til sundhedssektoren](teams-in-hc.md)
