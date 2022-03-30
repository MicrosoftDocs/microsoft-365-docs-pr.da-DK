---
title: Microsoft 365 oversigt over lejere i Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Få mere at vide om siden Lejere for administrerede tjenesteudbydere, der Microsoft 365 Lighthouse.
ms.openlocfilehash: 23f151664455c35bb2fcc191d774ead00927e830
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598552"
---
# <a name="microsoft-365-lighthouse-tenants-page-overview"></a>Microsoft 365 oversigt over lejere i Lighthouse

Microsoft 365 Lighthouse kan du administrere lejerkonti ved at vælge **Lejere i venstre navigationsrude** for at åbne siden Lejere. Siden Lejere indeholder en liste over alle dine lejere. Du kan vælge en lejer for at få vist detaljerede oplysninger, herunder kontaktoplysninger og installationsstatus.

Siden Lejere indeholder også følgende indstillinger:

- **Eksportér:** Vælg for at eksportere lejerdata Excel en fil med kommaseparerede værdier (.csv).
- **Administrer mærker:** Vælg for at tilføje, redigere eller slette et mærke.
- **Tildel mærker:** Vælg for at tildele et mærke til en lejer.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt lejer på listen.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Skærmbillede af lejersiden.":::

## <a name="tenant-list"></a>Lejerliste

Lejerlisten giver indsigt i de forskellige lejere, du har en kontrakt med, herunder deres lejers lighthouse-onboardingstatus. Lejerlisten giver dig også mulighed for at mærke lejere, så de kan levere forskellige filtre i hele Fyrtårn og analysere ned for at få mere at vide om en given lejer og status for dens installationsplan.

Når dine lejere opfylder [onboardingkravene til Fyrtårn](m365-lighthouse-requirements.md), vises dens status **som Aktiv** på lejerlisten.

Lejerlisten gør det muligt at:

- Sortér automatisk lejere efter aktive, inaktive og ikke-berettigede.
- Eksportér lejerlisten.
- Tildel og administrer mærker.
- Søg efter lejere efter navn.
- Filtrer lejere efter status, delegerede administrative rettigheder (DAP) og mærker.

Hvis du vil deaktivere lejeren eller få vist og administrere mærker, skal du vælge de tre prik (flere handlinger) ud for lejernavnet. Du kan få vist individuelle lejere ved enten at vælge lejernavnet eller ved at vælge et af mærkerne, der er tildelt til lejeren.

## <a name="tenant-status"></a>Lejerstatus

Følgende tabel viser de forskellige statusser og deres betydning.<br><br>

| Status                                   | Beskrivelse                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Aktiv                                   | Lejer-onboarding og dataflow er startet.                                                           |
| Inaktiv                                 | Lejer blev offboardet på anmodning af MSP'en og administreres ikke længere i Fyrtårn.           |
| I gang                               | Lejeren blev fundet, men ikke fuldt onboardet.                                                              |
| Ikke berettiget – DAP eller GDAP er ikke konfigureret    | Partner skal have delegerede (DAP) eller detaljeret delegerede administratorrettigheder (GDAP) konfigureret med lejeren. |
| Ikke berettiget – Påkrævet licens mangler | Lejer har ikke den nødvendige licens.                                                               |
| Ikke berettiget – Antal brugere er overskredet         | Lejer har flere brugere end tilladt.                                                                     |
| Ikke berettiget – Geo-kontrol mislykkedes            | Partner og kunde skal være placeret det samme geografiske sted.                                       |

Når du deaktiverer en lejer, kan du ikke udføre en handling på lejeren, før deaktiveringsprocessen er fuldført. Det kan tage op til 48 timer, før inaktiveringen er fuldført. Hvis du beslutter dig for at genaktivere en lejer, kan det tage op til 48 timer, før dataene vises igen.

## <a name="tenant-tags"></a>Lejermærker

For at organisere dine lejere og nemt filtrere de eksisterende visninger kan du oprette og tildele mærker til dine lejere. Du kan få mere at vide under [Administrer din lejerliste](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Du kan oprette op til 30 mærker på tværs af alle lejere.

## <a name="tenant-details-page"></a>Siden Lejeroplysninger

Hvis du vil have vist detaljerede lejeroplysninger, skal du vælge en lejer på lejerlisten. Siden med lejeroplysninger indeholder kontaktoplysninger og status for installationsplan.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Skærmbillede af siden Lejeroplysninger.":::

### <a name="overview-tab"></a>Fanen Oversigt

På fanen Oversigt kan du få vist lejeroversigt, kontaktoplysninger og Microsoft 365 brug af tjenester.

#### <a name="tenant-overview-card"></a>Oversigtskort for lejer

Oversigtskortet lejer indeholder oplysninger om lejeren fra dens Microsoft 365 konto.<br><br>

| Lejeroplysninger    | Beskrivelse|
|-----------------------|------------------|
| Headquarters    | Hvor lejeren er placeret.|
| Branche    |Organisationens branche.|
| Websted    |Organisationens websted. Du kan redigere dette felt, hvis der ikke er angivet nogen data.|
| Kundedomæne    |Organisationens domæne.|
| Brugere i alt    |Antallet af brugere, der er tildelt i lejeren. Du kan vælge dette nummer for at åbne siden Brugere for den pågældende lejer.|
| Enheder i alt|Antallet af enheder, der er tilmeldt lejeren. Du kan vælge dette nummer for at åbne siden Enheder for den pågældende lejer.|

#### <a name="contacts-card"></a>Visitkort

Med visitkortet kan du angive oplysninger om de vigtigste kontakter i de lejere, du administrerer, f.eks.:

- Navn
- Titel
- Telefon
- Mail
- Bemærkninger

Afsnittet Noter er et tekstfelt, som du kan bruge til at registrere vigtige oplysninger for lejeren, f.eks. aftaleindstillinger, placering, tidszone og oplysninger om deres rolle i organisationen.

Hvis du vil redigere detaljer eller slette en eksisterende kontakt, skal du vælge navnet på kontakten på listen. I **ruden Rediger** kontakt skal du redigere eller slette kontakten. Hvis du vil tilføje en anden kontakt, skal **du vælge +Tilføj kontakt**.

#### <a name="microsoft-365-usage-card"></a>Microsoft 365 dit brugerkort

Lighthouse giver indsigt i Microsoft 365 brug af tjenester, herunder hvor mange brugere i en lejer der har licens og aktivt bruger hver enkelt tjeneste. Aktiv angiver antallet af brugere eller enheder, der har logget på tjenesten mindst én gang inden for de seneste 28 dage. En ændring angiver ændringer for aktive brugere og enheder siden sidste måned.

Kortet Microsoft 365 brug indeholder to sektioner:

- **Microsoft 365 på Lighthouse-aktiverede tjenester:** tjenester, der kan administreres på fyrtårnsportalen.
- **Yderligere Microsoft 365-tjenester:** Tjenester, der er inkluderet i Microsoft 365-pakken, men som på nuværende tidspunkt ikke kan administreres på Microsoft 365 Lighthouse-portalen.

### <a name="deployment-plans-tab"></a>Fanen Installationsplaner

Fanen Installationsplaner giver status for en lejers installationsplan. Installationstrinnene på listen er baseret på den oprindelige plan anvendt på lejeren. Hvis du vil se detaljer om installationstrin, skal du vælge et installationstrin på listen.

Fanen Installationsplaner indeholder også følgende indstillinger:

- **Eksportér:** Vælg for at eksportere installationstrindata Excel en fil med kommaseparerede værdier (.csv).
- **Opdater:** Vælg for at hente de mest aktuelle installationstrindata.
- **Søg:** Angiv nøgleord for hurtigt at finde et bestemt installationstrin på listen.

## <a name="related-content"></a>Relateret indhold

[Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Administrer din lejerliste](m365-lighthouse-manage-tenant-list.md) (artikel)\
[Oversigt over brug af oprindelige planer til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artikel)\
[Installér Microsoft 365 grundlinjer med fyrtårne](m365-lighthouse-deploy-baselines.md) (artikel)
