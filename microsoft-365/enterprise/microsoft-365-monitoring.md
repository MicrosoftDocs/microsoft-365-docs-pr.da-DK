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
description: Brug Microsoft 365 overvågning for oplysninger om hændelser eller rådgivning i Microsoft 365.
ms.openlocfilehash: 2d78bcae258730e1b48c7d6cc77fa5ae2b200b07
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520811"
---
# <a name="learn-about-microsoft-365-monitoring"></a>Få mere at vide Microsoft 365 overvågning

Du kan bruge dashboards [i Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339) til at overvåge forskellige Microsoft-tjenester for din organisations Microsoft 365 abonnement. Denne funktion blev oprindeligt startet med Exchange Online og udvides nu til andre Microsoft-tjenester f.eks. Microsoft Teams, Microsoft 365 Apps og mere tjeneste i fremtiden. Overvågning giver dig oplysninger om hændelser og råd, der indsamles i disse kategorier:

- **Infrastruktur**. Problemet registreres i den Microsoft 365, som Microsoft ejer til at levere regelmæssige opdateringer og løse problemet. Brugere kan f.eks. ikke få adgang Exchange Online på grund af problemer med Exchange eller anden Microsoft 365 skyinfrastruktur.

- **Tredjepartsinfrastruktur**. Problemet registreres i tredjepartsinfrastruktur, som organisationen har taget afhængighed af og kræver handling fra din organisation for at løse problemet. Eksempelvis bliver brugergodkendelsestransaktioner begrænser af en tredjeparts STS-udbyder (security token service), der forhindrer brugere i at oprette forbindelse til Exchange Online.

- **Kundeinfrastruktur**. Problemet registreres i organisationens infrastruktur og kræver handling fra din organisation for at løse problemet. Brugere kan f.eks. ikke få adgang til Exchange Online, fordi de ikke kan hente et godkendelsestoken fra STS-udbyderen, der er hostet af din organisation på grund af et udløbet certifikat.

Her er et eksempel på **siden Tjenestetilstand** i Microsoft 365 Administration,  >  der findes på Health **Tjenestetilstand** for organisationsscenarier og prioritetskontoscenarier.[](../admin/setup/priority-accounts.md)

![Siden Tjenestetilstand i Microsoft 365 Administration.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Problemer i din organisation kan** identificeres og bruges af overvågning og prioritet af kontoovervågning på organisationsniveau.

Værdien af kolonnen **Tilstand under Problemer** i organisationen angiver, om organisationens infrastruktur eller tredjepartssoftware påvirker tjenesteoplevelsen for organisationens brugere og/eller prioritetskonti i Exchange Online. Rådgivning eller hændelser kræver, at du løser dine handlinger.

Værdien af kolonnen **Tilstand** under **Microsofts tjeneste** sundhed angiver, at tjenesten er sund eller har gode råd eller hændelser baseret på de skytjenester, som Microsoft vedligeholder.

Her er et eksempel på siden Exchange Online-overvågning i Microsoft 365 Administration, der viser stilstanden for scenarier med organisations- og prioritetskonti > , der er tilgængelige **fra Tilstand Tjenestetilstand** >  **Exchange Online**.

![Scenarier på organisationsniveau for Exchange Online overvågnings.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-org-scenarios.png)

Med scenarielistesiden kan du se, om Microsoft-tjenesten er sund eller ej, og om der er tilknyttet hændelser eller gode råd. Med Exchange Online kan du f.eks. se på tjenestestilstanden for bestemte mailscenarier og få vist næsten realtidslydesignaler for at bestemme påvirkningen efter scenarie på organisationsniveau. Du kan også se scenarier for prioritetskontoens tilstand, hvis de er tilgængelige.

## <a name="requirements-for-monitoring"></a>Krav til overvågning

Eksempelvisningen er aktiveret for kunder, der opfylder følgende krav:

- Din organisation skal have en licenstælling på mindst 5.000 fra én eller en kombination af disse produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5 eller Microsoft 365 E5.

   Din organisation kan f.eks. have 3.000 Office 365 E3-licenser og 2.500 Microsoft 365 E5, i alt 5.500 licenser fra de kvalificerende produkter.

- Din organisation skal have mindst 50 månedlige aktive brugere for en eller flere centrale Microsoft 365-tjenester, som omfatter Microsoft Teams, OneDrive for Business, SharePoint Online, Exchange Online og Office apps.

- Alle roller med tilladelser på Dashboard for tjenestetilstand kan få adgang Exchange Online Overvågnings. Hvis du vil have flere oplysninger, skal du se [Sådan kontrollerer du tjenestetilstanden for Microsoft 365](view-service-health.md).

## <a name="additional-monitoring-for-microsoft-services"></a>Yderligere overvågning af Microsoft-tjenester

Tjenestespecifik overvågning er også aktiveret for følgende Microsoft-tjenester. Vælg det tilsvarende link for at få mere at vide om overvågning for den pågældende tjeneste.

- [Exchange Online](microsoft-365-exchange-monitoring.md)

- [Microsoft 365 Apps](microsoft-365-apps-monitoring.md)

- [Microsoft Teams](microsoft-365-teams-monitoring.md)

## <a name="send-us-feedback"></a>Send os feedback

Du kan give feedback på to måder:

- Brug indstillingen **Giv feedback**, der er tilgængelig på hver side Microsoft 365 Administration.

- Send feedback ved hjælp af **Er dette indlæg nyttigt? link til en bestemt hændelse eller vejledning.

  !["Er dette indlæg nyttigt?" link til en bestemt hændelse eller vejledning.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="1-why-dont-i-see-view-link-under-organizational-monitoring-column-in-the-microsoft-365-admin-center-inside-service-health"></a>1. Hvorfor kan jeg ikke se linket "vis" under kolonnen Organisatorisk overvågning på Microsoft 365 Administration i Tjeneste sundhed?

Først skal du kontrollere, at du har aktiveret den nye Administration på **siden** Startside for [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339).

Kontrollér derefter, at du opfylder begge følgende krav:

- Din organisation skal have en licenstælling på mindst 5.000 fra én eller en kombination af disse produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5 eller Microsoft 365 E5.

- Din organisation skal have mindst 50 månedlige aktive brugere for en eller flere centrale Microsoft 365-tjenester, som omfatter Microsoft Teams, OneDrive for Business, SharePoint Online, Exchange Online og Office apps.

Hvis antallet af licenser for din organisation falder til under 5.000 brugere, og de månedlige aktive brugere falder til under 50 brugere i kernetjenesterne, bliver Exchange Online-overvågning ikke aktiveret, før disse krav er opfyldt.

### <a name="2-will-there-be-other-monitoring-scenarios-for-other-services-in-future"></a>2. Vil der i fremtiden være andre overvågningsscenarier for andre tjenester?

Ja. Vi har et par flere tjenester i offentlig prøveversion nu. Vi fortsætter med at arbejde på at udvide aftrykket til andre tjenester.

### <a name="3-what-is-the-plan-for-general-availability-of-this-experience"></a>3. Hvad er planen for generel tilgængelighed af denne oplevelse?

Microsofts plan er at indsamle din feedback på forhåndsvisningsoplevelsen og derefter definere vores plan for generel tilgængelighed.

### <a name="4-is-this-a-free-included-or-paid-extra-feature"></a>4. Er dette en gratis (inkluderet) eller betalt (ekstra) funktion?

Dette er en gratis funktion, der er i preview og kun tilgængelig for kunder, der opfylder de krav, der er spørgsmål 1. Der er ikke en betalt mulighed for at modtage dette indhold.

### <a name="5-how-do-i-provide-feedback"></a>5. Hvordan gør jeg give feedback?

Du kan få generel feedback **ved at bruge** ikonet Giv feedback i nederste højre hjørne på overvågningssiden.

Hvis du vil have feedback på hændelser eller gode råd, kan du bruge **Er dette indlæg nyttigt? .

### <a name="6-are-there-any-privacy-concerns"></a>6. Er der nogen bekymringer vedrørende beskyttelse af personlige oplysninger?

Overvågning fokuserer på tjenestemetadata, og brugerindhold overvåges ikke.
