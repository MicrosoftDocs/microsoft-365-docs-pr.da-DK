---
title: Exchange Online overvågning af Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: admindeeplinkMAC
f1.keywords:
- NOCSH
description: Brug Exchange Online overvågning for oplysninger om mailhændelser eller rådgivning i Microsoft 365.
ms.openlocfilehash: 22985d1fd6e79693a526c8ec008e189593543ae6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591489"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Exchange Online overvågning af Microsoft 365

Du kan bruge Exchange Online i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> til at overvåge Exchange-tjenestens tilstand for din organisations Microsoft 365 abonnement. Exchange Online giver dig oplysninger om hændelser og rådgivning, der indsamles i disse kategorier:

- **Infrastruktur**: Problemet registreres i den Microsoft 365-infrastruktur, som Microsoft ejer til at levere regelmæssige opdateringer og løse problemet. Brugere kan f.eks. ikke Exchange Online på grund af problemer med Exchange eller anden Microsoft 365 skyinfrastruktur.
- **Tredjepartsinfrastruktur: Problemet** registreres i tredjepartsinfrastruktur, som organisationen er afhængig af og kræver handling fra din organisation for at løse problemet. Eksempelvis bliver brugergodkendelsestransaktioner begrænser af en tredjeparts STS-udbyder (security token service), der forhindrer brugere i at oprette forbindelse til Exchange Online.
- **Kundeinfrastruktur**: Problemet registreres i organisationens infrastruktur og kræver handling fra din organisation for at løse problemet. Brugere kan f.eks. ikke få adgang til Exchange Online, fordi de ikke kan hente et godkendelsestoken fra STS-udbyderen, der er hostet af din organisation på grund af et udløbet certifikat.

Her er et eksempel på siden **Tjeneste** sundhed i Microsoft 365 Administration, der er tilgængelig fra **Health > Service health** for organization and [priority account](../admin/setup/priority-accounts.md) scenarios.

![Siden Tjenestestilstand i Microsoft 365 Administration.](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

**Problemer i din organisation kan** identificeres og bruges af overvågning og prioritet af kontoovervågning på organisationsniveau.

Værdien af kolonnen **Tilstand under Problemer** i organisationen angiver, om organisationens infrastruktur eller tredjepartssoftware påvirker tjenesteoplevelsen for organisationens brugere og/eller prioritetskonti i Exchange Online. Rådgivning eller hændelser kræver, at *du løser* dine handlinger.

Værdien af kolonnen **Tilstand** under **Microsofts tjeneste** sundhed angiver, at tjenesten er sund eller har gode råd eller hændelser baseret på de skytjenester, som Microsoft vedligeholder.

Her er et eksempel på siden Exchange Online-overvågning i Microsoft 365 Administration, der viser stilstanden for scenarier med organisationsniveau og prioritetskonto, der er tilgængelige fra Tilstand **> > Exchange Online**.

![Den Exchange Online overvågningsside i Microsoft 365 Administration.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example.png)

Med **Exchange Online** overvågningssiden kan du se, om Exchange Online-tjenesten er sund eller ej, og om der er tilknyttet hændelser eller gode råd. Med Exchange Online overvågning kan du se på tjenestestilstanden for bestemte mailscenarier og få vist næsten realtidslys for at bestemme påvirkningen efter scenarie på organisationsniveau. Du kan også se tilstand for prioritetskontoscenarier.

## <a name="requirements"></a>Krav

Eksempelvisningen er aktiveret for kunder, der opfylder følgende krav:

- Din organisation skal have en licenstælling på mindst 5.000 fra én eller en kombination af disse produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5.

  Din organisation kan f.eks. have 3.000 Office 365 E3-licenser og 2.500 Microsoft 365 E5, i alt 5.500 licenser fra de kvalificerende produkter.

- Din organisation skal have mindst 50 månedlige aktive brugere for en eller flere centrale Microsoft 365-tjenester, som omfatter Microsoft Teams, OneDrive for Business, SharePoint Online, Exchange Online og Office apps.

- Alle roller med tilladelser på Dashboard for tjenestetilstand kan få adgang Exchange Online Overvågnings. Hvis du vil have flere oplysninger, skal du se [Sådan kontrollerer du tjenestetilstanden for Microsoft 365](view-service-health.md).

## <a name="organization-level-scenarios"></a>Scenarier på organisationsniveau

Med Exchange Online understøtter overvågning følgende scenarier:

- **Mailklienter**: Du kan få vist tilstand for følgende mailklienter baseret på læseaktivitet for mail:

  - Outlook skrivebord
  - Outlook på internettet
  - Indbyggede mailklienter til iOS og Android
  - Outlook mobilapp i iOS og Android
  - Outlook Mac-klient

   For disse klienter kan du se antallet af aktive brugere i de sidste 30 minutter baseret på brugere, der læser en mail, samt antallet af hændelser og rådgivning i dashboardet. Disse data sammenlignes med det samme interval for den forrige uge for at se, om der er et problem.

   >[!Note]
   > Antallet af aktive brugere måles efter en enkelt aktivitet, f.eks. når en bruger læser en mail. Den tager kun hensyn til de seneste 30 minutters aktivitet.

- **Appforbindelse**: Anslået forbindelse er baseret på procentdelen af vellykkede, forbedrede forbindelser mellem din organisations enheder og Exchange Online og kan omfatte problemer uden for Microsofts kontrol. Du kan få mere at vide [Microsoft 365 Connectivity Optics](microsoft-365-connectivity-optics.md).

- **Grundlæggende godkendelse og moderne godkendelse**: Antallet af brugere er blevet valideret i Exchange Online tjeneste.

- **Mailflow**: Antallet af meddelelser, der blev leveret til en postkasse uden forsinkelse, efter meddelelsen blev nået Microsoft 365 netværket.

  ![Et eksempel på overvågning af Exchange for levering af mail.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-scenario-example.png)

For disse scenarier er de vigtigste tal for de sidste 30 minutter på hoveddashboardet. Detaljerede visninger for hvert af disse scenarier viser næsten realtidstendensen for syv dage med 30-minutters aggregatet sammenlignet med den forrige uge.

## <a name="priority-accounts-monitoring-scenarios"></a>Overvågningsscenarier for prioritetskonti

Når Exchange Online prioritetskontoovervågning, kan du få vist tilstand for følgende scenarier efter konfiguration af [prioritetskonti](/microsoft-365/admin/setup/priority-accounts):

- Exchange licensering

- Postkasselager

- Meddelelsesgrænse

- Undermapper pr. mappe

- Mappehierarki

- Genoprettelige elementer

Scenariet Exchange licensering kontrollerer, om prioritetskontoen ikke kan logge på på grund af ugyldige licensproblemer, som kan løses af lejeradministratoren.

De resterende fem scenarier ovenfor kontrollerer, om din prioritetskontos postkasse er tæt på at nå eller har nået de grænser, der er [beskrevet i Exchange Online grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits).

For disse scenarier kan du se aktive og løste rådgivere og hændelser, der påvirker dine prioritetskonti. Identificerbare oplysninger om prioritetskonti vises i oplysningerne om rådgivning eller hændelser sammen med anbefalinger. Her er et eksempel fra siden **på > For tjeneste > Exchange Online**.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-priority-accounts-example.png" alt-text="Eksempel på aktive og løste gode råd og hændelser, der påvirker dine prioritetskonti":::

I ruden med den berørte **konto har kolonnen Status** disse værdier:

- Rettet: Problemet, der forårsager, at rådgivningen eller hændelsen er blevet løst for prioritetskontoen. Der er ikke længere et problem. 

- Aktiv: Problemet, der forårsager rådgivningen eller hændelsen, er fortsat for prioritetskontoen. Problemet er der stadig. 

- Forsinket: Problemet, der forårsager, at rådgivningen eller hændelsen ikke er blevet behandlet for prioritetskontoen inden for 96 timer, så det suspenderes. Problemet er der stadig. 

Her er et eksempel.

:::image type="content" source="../media/microsoft-365-exchange-monitoring/exchange-status-column-example.png" alt-text="Eksempel på statuskolonnen i den berørte kontorude":::

En vejledning eller hændelse vil blive løst, når ingen konti forbliver i **den aktive** tilstand. 

## <a name="send-us-feedback"></a>Send os feedback

Du kan give feedback på to måder:

- Brug indstillingen **Giv feedback**, der er tilgængelig på hver side Microsoft 365 Administration.

- Send feedback ved hjælp **af linket Er dette indlæg nyttigt?** for en bestemt hændelse eller vejledning.

  !["Er dette indlæg nyttigt?" link til en bestemt hændelse eller vejledning.](../media/microsoft-365-exchange-monitoring/exchange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

#### <a name="1-why-dont-i-see-exchange-online-monitoring-under-health-in-the-microsoft-365-admin-center"></a>1. Hvorfor kan jeg ikke se "overvågning Exchange Online" under Tilstand i Microsoft 365 Administration? 

Først skal du kontrollere, at du har aktiveret den nye Administration på **siden** Startside for <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

Kontrollér derefter, at du opfylder begge følgende krav:

- Din organisation skal have en licenstælling på mindst 5.000 fra én eller en kombination af disse produkter: Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5.

- Din organisation skal have mindst 50 månedlige aktive brugere for en eller flere centrale Microsoft 365-tjenester, som omfatter Microsoft Teams, OneDrive for Business, SharePoint Online, Exchange Online og Office apps.

Hvis antallet af licenser for din organisation falder til under 5.000 brugere, og de månedlige aktive brugere falder til under 50 brugere i kernetjenesterne, bliver Exchange Online-overvågning ikke aktiveret, før disse krav er opfyldt.

#### <a name="2-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>2. Antallet af aktive brugere i dashboardet for hver klient ser ud til at være lavt. Vi har mange aktive licenser tildelt til brugere. Hvad betyder det?

Det aktive brugerantal, der vises under overvågning, er baseret på et 30-minutters vindue, hvor brugerne har udført den aktivitet, der er vist i funktionen. Dette må ikke forveksles med brugsnumre. Hvis du vil have vist forbrugsnumre, skal du bruge aktivitetsrapporter Microsoft 365 Administration (<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">**ReportsUsage**</a> > ).

#### <a name="3-will-there-be-other-monitoring-scenarios-for-other-services-such-as-teams-and-sharepoint"></a>3. Vil der være andre overvågningsscenarier for andre tjenester som f.eks Teams og SharePoint?

Microsoft integrerer denne oplevelse direkte i dashboardet Tjenestetilstand i Microsoft 365 Administration. Dette giver Microsoft mulighed for at udvide overvågningsscenarier for andre tjenester, som annonceres, når der er nyheder, der skal deles.

#### <a name="4-what-is-the-plan-for-general-availability-of-this-experience"></a>4. Hvad er planen for generel tilgængelighed af denne oplevelse?

Microsoft har integreret Exchange Online direkte overvågning på <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**dashboardet Tjenestetilstand**</a> i Microsoft 365 Administration.

Med denne nye integrerede oplevelse er Microsofts plan at indsamle din feedback og derefter definere vores plan for generel tilgængelighed.

#### <a name="5-is-this-a-free-included-or-paid-extra-feature"></a>5. Er dette en gratis (inkluderet) eller betalt (ekstra) funktion? 

Dette er en gratis funktion, der er i preview og kun tilgængelig for kunder, der opfylder de krav, der er spørgsmål 1. Der er ikke en betalt mulighed for at modtage dette indhold.

#### <a name="6-how-do-i-provide-feedback"></a>6. Hvordan giver jeg feedback?

Du kan få generel feedback ved **at bruge** ikonet Giv feedback i nederste højre hjørne af **siden Exchange Online** overvågningssiden. 

Hvis du vil have feedback på hændelser eller gode råd, kan du **bruge linket Er dette indlæg nyttigt?**

#### <a name="7-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>7. Hvor er dataene, der anvendes til de scenarier, der viser aktivitetstendenser?

Dataene anvendes i Exchange Online tjeneste. Hvis der sker en fejl, før anmodningen når Exchange Online, eller der er en fejl i Exchange Online, kan du se en fald i aktivitetssignalet.

#### <a name="8-are-there-any-privacy-concerns"></a>8. Er der nogen problemer i forbindelse med beskyttelse af personlige oplysninger?

Overvågning fokuserer på tjenestemetadata, og brugerindhold overvåges ikke.

## <a name="see-also"></a>Se også

- [Sådan kontrolleres Microsoft 365 tjeneste sundhed](view-service-health.md) 

- [Exchange Online begrænsninger](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-storage-limits)

- [Administrere og overvåge prioritetskonti](/microsoft-365/admin/setup/priority-accounts)

- [Brug af prioritetskonti i Microsoft 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/using-priority-accounts-in-microsoft-365/ba-p/1873314)

- [Tjenestebeskeder om anvendelsen af postkasse i Exchange Online overvågning](microsoft-365-mailbox-utilization-service-alerts.md)

- [Tjenestebeskeder om mrs-kildeforsinkelse i Exchange Online overvågning](microsoft-365-mrs-source-delays-service-alerts.md)
