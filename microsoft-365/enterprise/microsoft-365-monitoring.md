---
title: Microsoft 365 overvågning
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: mediumn
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: Brug Microsoft 365 overvågning for at få oplysninger om hændelser eller gode råd i Microsoft 365.
ms.openlocfilehash: 47f54859d7dd0973814a0ad9229a902bddcb8587
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824841"
---
# <a name="learn-about-microsoft-365-monitoring"></a>Få mere at vide om overvågning af Microsoft 365

Du kan bruge dashboards i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) til at overvåge tilstanden for forskellige Microsoft-tjenester for din organisations Microsoft 365 abonnement. Denne funktion blev oprindeligt startet med Exchange Online og blev nu udvidet til andre Microsoft-tjenester, f.eks. Microsoft Teams, Microsoft 365 Apps og mere tjeneste i fremtiden. Overvågning giver dig oplysninger om hændelser og gode råd, der indsamles i disse kategorier:

- **Infrastruktur**. Der registreres et problem i den Microsoft 365 infrastruktur, som Microsoft ejer for at levere regelmæssige opdateringer og løse problemet. Brugerne kan f.eks. ikke få adgang til Exchange Online på grund af problemer med Exchange eller andre Microsoft 365 cloudinfrastruktur.

- **Tredjepartsinfrastruktur**. Der registreres et problem i tredjepartsinfrastrukturen, som din organisation har taget en afhængighed af, og som kræver handling fra din organisation for at løse problemet. Brugergodkendelsestransaktioner begrænses f.eks. af en TREDJEPARTSUDBYDER af sikkerhedstokentjenester, der forhindrer brugerne i at oprette forbindelse til Exchange Online.

- **Kundeinfrastruktur**. Problemet er registreret i organisationens infrastruktur og kræver handling fra din organisation for at løse problemet. Brugerne kan f.eks. ikke få adgang til Exchange Online, fordi de ikke kan hente et godkendelsestoken fra STS-udbyderen, der hostes af din organisation, på grund af et udløbet certifikat.

Her er et eksempel på siden **Tjenestetilstand** i Microsoft 365 Administration, som er tilgængelig på **Tilstand** >  **Tjenestetilstand** for scenarier med organisationsscenarier og [prioritetskonto](../admin/setup/priority-accounts.md).

![Siden Tjenestetilstand i Microsoft 365 Administration.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Problemer i din organisation** identificeres og bruges af overvågning på organisationsniveau og prioriteret kontoovervågning.

Værdien af kolonnen **Sundhed** under **Problemer i din organisation** angiver, om organisationens infrastruktur eller tredjepartssoftware påvirker tjenestetilstandsoplevelsen for organisationens brugere og/eller prioritetskonti i Exchange Online. Rådgivere eller hændelser kræver, at dine handlinger løses.

Værdien af kolonnen **Tilstand** under **Microsofts tjenestetilstand** angiver, at tjenesten er sund, eller at den indeholder rådgivere eller hændelser, der er baseret på de cloudtjenester, som Microsoft vedligeholder.

Her er et eksempel på den Exchange Online overvågningsside i Microsoft 365 Administration, der viser tilstanden af scenarier på organisationsniveau og prioritetskonti, som er tilgængelige fra **Tilstand** >  **Tjenestetilstand** >  **Exchange Online**.

![Scenarier på organisationsniveau til Exchange Online overvågning.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

På scenarielistesiden kan du se, om Microsoft-tjenesten er sund eller ej, og om der er nogen tilknyttede hændelser eller rådgivere. Med Exchange Online overvågning kan du f.eks. se på tjenestetilstanden for bestemte mailscenarier og få vist signaler i næsten realtid for at bestemme virkningen efter scenariet på organisationsniveau. Du kan også se tilstanden for prioriterede kontoscenarier, hvis de er tilgængelige.

## <a name="requirements-for-monitoring"></a>Krav til overvågning

Denne prøveversion er aktiveret for kunder, der opfylder følgende krav:

- Din organisation skal have et licensantal på mindst 5.000 fra et eller en kombination af disse produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5 eller Microsoft 365 E5.

   Din organisation kan f.eks. have 3.000 Office 365 E3 licenser og 2.500 Microsoft 365 E5 i alt 5.500 licenser fra de kvalificerende produkter.

- Din organisation skal have mindst 50 aktive brugere om måneden for en eller flere centrale Microsoft 365-tjenester, herunder Microsoft Teams, OneDrive for Business, SharePoint Online, Exchange Online og Office Apps.

- Alle roller med tilladelser til dashboardniveau for tjenestetilstand kan få adgang Exchange Online overvågning. Hvis du vil have flere oplysninger, skal du se [Sådan kontrollerer du tjenestetilstanden for Microsoft 365](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>Yderligere overvågning af Microsoft-tjenester

Tjenestespecifik overvågning er også aktiveret for følgende Microsoft-tjenester. Vælg det tilsvarende link for at få mere at vide om overvågning for den pågældende tjeneste.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [Microsoft 365 Apps](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>Send os feedback

Du kan give feedback på to måder:

- Brug indstillingen **Giv feedback** tilgængelig på alle sider i Microsoft 365 Administration.

- Send feedback ved hjælp af **Er dette indlæg nyttigt? et link til en bestemt hændelse eller rådgivning.

  !["Er dette indlæg nyttigt?" et link til en bestemt hændelse eller rådgivning.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. Hvorfor kan jeg ikke se linket "vis" under kolonnen Organisationsovervågning i Microsoft 365 Administration i Service Health?

Først skal du sørge for, at du har aktiveret det nye Administration **på startsiden** for [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Sørg derefter for, at du opfylder begge følgende krav:

- Din organisation skal have et licensantal på mindst 5.000 fra et eller en kombination af disse produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5 eller Microsoft 365 E5.

- Din organisation skal have mindst 50 aktive brugere om måneden for en eller flere centrale Microsoft 365-tjenester, herunder Microsoft Teams, OneDrive for Business, SharePoint Online, Exchange Online og Office Apps.

Hvis licensantallet for din organisation falder til under 5.000 brugere, og de månedlige aktive brugere falder under 50 brugere i kernetjenesterne, aktiveres Exchange Online overvågning ikke, før disse krav er opfyldt.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. Vil der i fremtiden være andre overvågningsscenarier for andre tjenester?

Ja. Vi har et par flere tjenester i offentlig prøveversion nu. Vi vil fortsætte med at arbejde på at udvide fodaftrykket til andre tjenester.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. Hvad er planen for offentlig tilgængelighed af denne oplevelse?

Microsofts plan er at indsamle din feedback om prøveversionsoplevelsen og derefter definere vores plan for generel tilgængelighed.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. Er dette en gratis (inkluderet) eller betalt (ekstra) funktion?

Dette er en gratis funktion, der er tilgængelig som prøveversion og kun tilgængelig for kunder, der opfylder kravene i spørgsmål 1. Der er ikke en betalt mulighed for at modtage dette indhold.

### <a name="5-how-do-i-provide-feedback"></a>5. Hvordan gør jeg give feedback?

Hvis du vil have generel feedback, skal du bruge ikonet **Giv feedback** nederst til højre på overvågningssiden.

Hvis du vil have feedback om hændelser eller gode råd, skal du bruge **Er dette indlæg nyttigt? Link.

### <a name="6-are-there-any-privacy-concerns"></a>6. Er der nogen bekymringer om beskyttelse af personlige oplysninger?

Overvågning fokuserer på tjenestemetadata, og brugerindhold overvåges ikke.
