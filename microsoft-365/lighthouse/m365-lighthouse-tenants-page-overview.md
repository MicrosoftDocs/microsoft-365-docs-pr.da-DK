---
title: Oversigt over siden Lejere i Microsoft 365 Fyrtårn
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
description: Få mere at vide om siden Lejere for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: 7b8e26ddbe68059a9c5ecf4d5e396fd11c49be71
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023277"
---
# <a name="overview-of-the-tenants-page-in-microsoft-365-lighthouse"></a>Oversigt over siden Lejere i Microsoft 365 Fyrtårn

Microsoft 365 Fyrtårn kan du administrere lejerkonti ved at vælge **Lejere** i venstre navigationsrude for at åbne siden Lejere. Siden Lejere indeholder en liste over alle dine lejere. Du kan vælge en lejer for at få vist detaljerede oplysninger, herunder kontaktoplysninger og installationsstatus.

Siden Lejere indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere lejerdata til en Excel fil med kommaseparerede værdier (.csv).
- **Administrer mærker:** Vælg at tilføje, redigere eller slette et mærke.
- **Tildel mærker:** Vælg at tildele et mærke til en lejer.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt lejer på listen.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-page-overview.png" alt-text="Skærmbillede af lejersiden.":::

## <a name="tenant-list"></a>Lejerliste

Lejerlisten giver indsigt i de forskellige lejere, du har en kontrakt med, herunder deres lejers onboardingstatus for Lighthouse. På lejerlisten kan du også mærke lejere for at levere forskellige filtre i hele Lighthouse og foretage detailudledning for at få mere at vide om en given lejer og status for dens udrulningsplan.

Når dine lejere opfylder [kravene til onboarding af Lighthouse](m365-lighthouse-requirements.md), vises dens status som **Aktiv** på lejerlisten.

På lejerlisten kan du:

- Sortér automatisk lejere efter aktive, inaktive og ikke-kvalificerede.
- Eksportér lejerlisten.
- Tildel og administrer mærker.
- Søg efter lejere efter navn.
- Filtrer lejere efter status, delegerede administrative rettigheder (DAP) og mærker.

Hvis du vil deaktivere lejeren eller få vist og administrere mærker, skal du vælge de tre prikker (flere handlinger) ud for lejernavnet. Du kan få vist individuelle lejere ved enten at vælge lejernavnet eller ved at vælge et af de mærker, der er tildelt lejeren.

## <a name="tenant-status"></a>Lejerstatus

I følgende tabel vises de forskellige statusser og deres betydning.<br><br>

| Status                                   | Beskrivelse                                                                                             |
|------------------------------------------|---------------------------------------------------------------------------------------------------------|
| Aktive                                   | Onboarding af lejer og dataflow er startet.                                                           |
| Inaktive                                 | Lejeren blev offboardet på anmodning af MSP'en og administreres ikke længere i Lighthouse.           |
| I gang                               | Lejeren blev fundet, men ikke fuldt onboardet.                                                              |
| Ikke berettiget – DAP eller GDAP er ikke konfigureret    | Partneren skal have delegeret (DAP) eller GDAP-administratorrettigheder (granular delegated) konfigureret med lejeren. |
| Ikke berettiget – Påkrævet licens mangler | Lejeren har ikke den påkrævede licens.                                                               |
| Ikke kvalificeret - Antallet af brugere er overskredet         | Lejeren har flere brugere end tilladt.                                                                     |
| Ikke berettiget - Geo-kontrol mislykkedes            | Partner og kunde skal være placeret på den samme geografiske placering.                                       |

Når du har deaktiveret en lejer, kan du ikke udføre handlinger på lejeren, før aktiveringsprocessen er fuldført. Det kan tage op til 48 timer, før inaktiveringen er fuldført. Hvis du beslutter at genaktivere en lejer, kan det tage op til 48 timer, før dataene vises igen.

## <a name="tenant-tags"></a>Lejertags

Hvis du vil organisere dine lejere og nemt filtrere eksisterende visninger, kan du oprette og tildele mærker til dine lejere. Du kan få mere at vide under [Administrer din lejerliste i Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md).

> [!NOTE]
> Du kan oprette op til 30 mærker på tværs af alle lejere.

## <a name="tenant-details-page"></a>Side med lejeroplysninger

Hvis du vil have vist detaljerede lejeroplysninger, skal du vælge en lejer på lejerlisten. Siden med lejeroplysninger indeholder kontaktoplysninger og status for installationsplanen.

:::image type="content" source="../media/m365-lighthouse-tenants-page-overview/tenant-details-page.png" alt-text="Skærmbillede af siden med lejeroplysninger.":::

### <a name="overview-tab"></a>Fanen Oversigt

Under fanen Oversigt kan du få vist lejeroversigt, kontaktoplysninger og Microsoft 365 serviceforbrug.

#### <a name="tenant-overview-card"></a>Oversigtskort for lejer

Oversigtskortet Lejer indeholder oplysninger om lejeren fra dens Microsoft 365 konto.<br><br>

| Lejeroplysninger    | Beskrivelse|
|-----------------------|------------------|
| Headquarters    | Hvor lejeren er placeret.|
| Industri    |Organisationens branche.|
| Hjemmeside    |Organisationens websted. Du kan redigere dette felt, hvis der ikke er angivet nogen data.|
| Kundedomæne    |Organisationens domæne.|
| Brugere i alt    |Antallet af brugere, der er tildelt i lejeren. Du kan vælge dette tal for at åbne siden Brugere for den pågældende lejer.|
| Enheder i alt|Antallet af enheder, der er tilmeldt lejeren. Du kan vælge dette tal for at åbne siden Enheder for den pågældende lejer.|

#### <a name="contacts-card"></a>Visitkort

Med kortet Kontakter kan du angive oplysninger om vigtige kontakter i de lejere, du administrerer, f.eks.:

- Navn
- Titel
- Telefon
- E-mail
- Bemærkninger

Afsnittet Noter er et tekstfelt, som du kan bruge til at registrere nøgleoplysninger for lejeren, f.eks. aftaleindstillinger, placering, tidszone og oplysninger om deres rolle i organisationen.

Hvis du vil redigere detaljer eller slette en eksisterende kontakt, skal du vælge kontaktens navn på listen. Rediger eller slet kontakten i ruden **Rediger kontakt** . Hvis du vil tilføje en anden kontakt, skal du vælge **+Tilføj kontakt**.

#### <a name="microsoft-365-usage-card"></a>Microsoft 365 forbrugskort

Lighthouse giver indsigt i Microsoft 365 brug af tjenester, herunder hvor mange brugere i en lejer der har licens og aktivt bruger hver tjeneste. Active angiver antallet af brugere eller enheder, der har logget på tjenesten mindst én gang i løbet af de seneste 28 dage. Ændring angiver ændring i aktive brugere og enheder siden sidste måned.

Kortet Microsoft 365 forbrug indeholder to afsnit:

- **Microsoft 365 Lighthouse-aktiverede tjenester:** Tjenester, der kan administreres på Lighthouse-portalen.
- **Yderligere Microsoft 365 tjenester:** Tjenester, der er inkluderet i Microsoft 365-pakken, men som ikke kan administreres i Microsoft 365 Lighthouse-portalen på nuværende tidspunkt.

### <a name="deployment-plans-tab"></a>Fanen Udrulningsplaner

Fanen Udrulningsplaner indeholder status for en lejers udrulningsplan. Udrulningstrinnene på listen er baseret på den oprindelige plan, der er anvendt på lejeren. Hvis du vil se detaljer om installationstrinnet, skal du vælge et installationstrin på listen.

Fanen Udrulningsplaner indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere data fra installationstrin til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste data for udrulningstrinnet.
- **Søg:** Angiv nøgleord for hurtigt at finde et bestemt installationstrin på listen.

## <a name="related-content"></a>Relateret indhold

[Krav til Microsoft 365 Fyrtårn](m365-lighthouse-requirements.md) (artikel)\
[Microsoft 365 Ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Administrer din lejerliste i Microsoft 365 Lighthouse](m365-lighthouse-manage-tenant-list.md) (artikel)\
[Oversigt over brug af Microsoft 365 baselines for fyrtårne til installation af standardlejerkonfigurationer](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (artikel)\
[Udrul Microsoft 365 lighthouse baselines](m365-lighthouse-deploy-baselines.md) (artikel)
