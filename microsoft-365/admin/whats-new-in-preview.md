---
title: Nyheder i Microsoft 365 Administration
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- MET150
- MOE150
- FRP150
ms.custom:
- MACDashWhatsNew
- AdminSurgePortfolio
- admindeeplinkMAC
description: Microsoft 365 Administration – få mere at vide om de funktioner, der blev tilføjet i denne måned.
ms.openlocfilehash: 42c2d1dcf6b778504f1d4786c6fbcc2ce38f9724
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099507"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Nyheder i Microsoft 365 Administration

::: moniker range="o365-21vianet"

> [!NOTE]
> Nogle af oplysningerne i denne artikel gælder muligvis ikke for Office 365, der drives af 21Vianet.

::: moniker-end

Vi føjer løbende nye funktioner til [Microsoft 365 Administration](Oversigt over Microsoft 365 Administration](admin-overview/admin-center-overview.md), løse problemer, vi lærer om, og foretage ændringer baseret på din feedback. Se nedenfor for at se, hvad der er tilgængeligt for dig i dag. Nogle funktioner udrulles med forskellige hastigheder til vores kunder. Hvis du endnu ikke kan se en funktion, [kan du prøve at føje dig selv til målrettet udgivelse](manage/release-options-in-office-365.md).

Og hvis du gerne vil vide, hvad der er nyt med andre Microsoft-cloudtjenester:

- [Nyheder i Azure Active Directory](/azure/active-directory/fundamentals/whats-new)
- [Nyheder i Exchange Administration](/Exchange/whats-new)
- [Nyheder i Microsoft Intune](/mem/intune/fundamentals/whats-new)
- [Nyheder på Microsoft Purview-overholdelsesportalen](/Office365/SecurityCompliance/whats-new)
- [Nyheder i Microsoft 365 Defender](../security/mtp/whats-new.md)
- [Nyheder i SharePoint Administration](/sharepoint/what-s-new-in-admin-center)
- [Office opdateringer](/OfficeUpdates/)
- [Sådan kontrollerer du Windows udgivelsestilstand](/windows/deployment/update/check-release-health)

## <a name="april-2022"></a>April 2022

### <a name="nps-sentiment-insights"></a>NPS-tillid Insights

NPS-undersøgelsesindsigt er et AI-drevet dashboard, der er tilgængeligt i Microsoft 365 Administration.

I Administration skal du gå til **HealthProduct** >  **feedbackNPS** >  **survey insights**.

Denne funktion hjælper administratorer som dig med at få handlingsvenlig indsigt, der er afledt af Microsoft NPS-undersøgelser, som dine brugere har svaret på. Få mere at vide på [Microsofts NPS-produktfeedback og indsigt for din organisation](manage/manage-feedback-product-insights.md).

Baseret på din feedback introducerer vi en ny funktion, der identificerer synspunkterne for hver nps ordret feedback, så du kan lære, hvad dine brugere har med Microsoft 365 produkter. Synspunktsmærkater, f.eks **. Positiv**, **Negativ** og **Andet** , tildeles nps ordret feedback.

:::image type="content" source="../media/product-feedback-nps-verbatims.png" alt-text="Skærmbillede: Dashboard til produktfeedback på fanen Indsigt i NPS-undersøgelser":::

Med synspunktsfunktionen på dashboardet indsigt i NPS-undersøgelsen kan du:

- Visualiser synspunktstendensen for de sidste 12 måneder baseret på nps ordret feedback.

- Identificer synspunktet pr. app og platform.

Der er tre tilgængelige synspunkter:

:::image type="content" source="../media/sentiment-examples.png" alt-text="Skærmbillede: Eksempler på synspunkter og beskrivelser":::

Hvis du vil give dig en bedre oplevelse ved hjælp af dashboardet med indsigt i NPS-undersøgelsen, anbefaler vi, at du kontrollerer følgende elementer:

- Tilskynd dine brugere til at indsende feedback.

- Bekræft, at [politikker for undersøgelse i produktet](https://config.office.com) er aktiveret.

- Gør diagnosticering bedre ved at aktivere [Windows Fejlrapportering](/windows/win32/wer/windows-error-reporting).

> [!NOTE]
> Hvis du er virksomhedskunde, og du er interesseret i at deltage i vores designsessioner, kan du sende os en mail på: prosight@microsoft.com

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 Administration søgning

Du kan nu få vist alle søgeresultater på en separat browserside ved at søge i global søgning og vælge **Enter**.

Med vores nye separate side med søgeresultater kan du udforske en mere omfattende liste over resultater og nemt vende tilbage til browsersiden for at få en mere effektiv søgeoplevelse.

:::image type="content" source="../media/whats-new-search-page.png" alt-text="Skærmbillede: Ny Microsoft 365 Administration browsersøgeside":::

### <a name="search-in-distribution-lists-to-add-priority-accounts"></a>Søg på distributionslister for at tilføje prioritetskonti

Tidligere kunne du kun mærke prioritetskonti ved at søge efter dem ved hjælp af personens navn, mailadresse eller stillingsbetegnelse. Med denne opdatering kan du nu søge efter personer, der skal føjes til prioritetskonti på en distributionsliste. Dette giver dig mulighed for at massetilføj personer på en effektiv måde og reducerer den tid, det tager at mærke individuelle personer i din organisation.

:::image type="content" source="../media/search-by-distribution-list-priority-accounts.png" alt-text="Skærmbillede: Søg efter prioritetskonti, der skal tilføjes ved hjælp af en distributionsliste":::

- Du kan mærke op til 50 brugere fra en distributionsliste som prioritetskonti i en enkelt handling.

- Yderligere oplysninger om brugeren, f.eks. afdeling og stillingsbetegnelse, er blevet introduceret på siden Prioritetskonti.

- Du kan kun mærke brugerkonti på distributionslister og ikke selve listen. Brugere, der allerede er mærket, vises ikke i søgningen på distributionslisten.

## <a name="march-2022"></a>Marts 2022

### <a name="microsoft-365-lighthouse-ga"></a>Microsoft 365 Fyrtårn GA

Små og mellemstore virksomheder er ofte afhængige af pålidelige it-partnere til at administrere deres it-miljøer. Vi gør det nemmere for partnere at sikre kunder i stor skala med den generelle tilgængelighed af [Microsoft 365 Lighthouse](https://aka.ms/March1SMBPartnerBlog), en administrationsportal med flere lejere til MSP'er (Managed Service Providers). Microsoft 365 Lighthouse giver kunderne en komplet oplevelse ved at sætte deres partnere i stand til hurtigt at identificere og reagere på trusler, unormale logons og beskeder om enhedens overholdelse af angivne standarder for at holde dem sikre.

:::image type="content" source="../media/lighthouse.png" alt-text="Skærmbillede: dashboardet Microsoft 365 Lighthouse":::

Microsoft 365 Lighthouse er kun en it-partnertjeneste, og den er kun tilgængelig for partnere, der er tilmeldt programmet Cloud Solution Provider (CSP), og som administrerer kunder, der har op til 1.000 brugere med licens til Microsoft 365 Business Premium, Microsoft 365 E3 , eller Microsoft Defender til virksomheder (i prøveversion) abonnementer. Hvis du er Microsoft CSP-tilmeldt it-partner, er Microsoft 365 Lighthouse gratis for din organisation og er designet til at hjælpe din virksomhed med at skalere og vokse. Se [hjælpbiblioteket Microsoft 365 Lighthouse](../lighthouse/m365-lighthouse-overview.md) for at få flere oplysninger.

Hvis du vil i gang med at bruge Microsoft 365 Fyrtårn, skal [du se Tilmeld dig Microsoft 365 Fyrtårn](../lighthouse/m365-lighthouse-sign-up.md). Hvis du vil vide mere om Microsoft 365 Lighthouse, Defender for Business og Microsoft 365 Business Premium, [kan du deltage i vores partnerwebinarserie](https://aka.ms/M365MDBSeries).

## <a name="february-2022"></a>Februar 2022

### <a name="net-promoter-score-nps-survey-insights"></a>Indsigt i NPS-undersøgelser (Net promoter score)

Du kan nu få vist NPS-undersøgelsesdata og indsigt fra dine brugere i Microsoft 365 Administration. Med denne nye funktion kan du få handlingsrettet indsigt fra NPS-undersøgelsessvar fra dine slutbrugere og opnå glæde hos slutbrugere i højere grad ved at løse eventuelle problemer og problemer.

I Administration skal du gå til **HealthProduct** >  **feedbackNPS** >  **survey insights**.

:::image type="content" source="../media/feedback-whatsnew.png" alt-text="Skærmbillede: Visning af siden Feedback i Microsoft 365 Administration":::

Vi har identificeret de fælles temaer fra brugerfeedback. Derefter brugte vi teknikker til maskinel indlæring til at oplære datasættene og automatisk organisere feedbacken i De vigtigste emner.

Der er ni emner tilgængelige. Se efter flere emner i fremtidige opdateringer.

:::image type="content" source="../media/feedback-nine-topics.png" alt-text="Skærmbillede: Viser de ni nye feedbackemner":::

Dashboardet med indsigt i NPS-undersøgelsen indeholder også disse tre nye rapporter og pivots:

- Nps månedlige NPS tendensvolumen for de sidste 12 måneder
- I stand til at identificere passiver, promotorer og detraktorer
- NPS-volumen pr. platform og app

For at give dig en bedre oplevelse ved hjælp af dashboardet nps-undersøgelses indsigt:

- Tilskynd dine slutbrugere til at indsende feedback
- Bekræft, at politikker for undersøgelser i produktet er aktiveret
- Gør diagnosen bedre ved at aktivere Windows Fejlrapportering

Få mere at vide på [Microsofts NPS-produktfeedback og indsigt for din organisation](manage/manage-feedback-product-insights.md).  

> [!NOTE]
> Hvis du er interesseret i at deltage i vores designsessioner, kan du sende os en mail på: prosight@microsoft.com

### <a name="microsoft-365-admin-center-video-training"></a>Microsoft 365 Administration videotræning

Vi har opdateret vores Microsoft 365 Administration videotræning. Gå til siden [Med administratoruddannelsesvideobibliotek](admin-video-library.yml) for at få mere at vide om, hvordan du konfigurerer og administrerer Microsoft 365 for din virksomhed.

:::image type="content" source="../media/admin-library-vid-training.png" alt-text="Skærmbillede: Viser biblioteket til videotræning i Administration":::

## <a name="july-2021"></a>Juli 2021

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 Administration søgning

Du kan nu søge efter hændelses-id'er i <a href="https://go.microsoft.com/fwlink/p/?linkid=2091030" target="_blank">Microsoft 365 Administration</a>. Du kan få mere at vide om aktuelle hændelser via sociale medier, branchepublikationer eller fra andre administratorer. Du kan nu gå til Administration for at se flere oplysninger om hændelsen og for at forstå indvirkningen på din organisation. Du skal blot søge efter hændelses-id'et i Administration.

:::image type="content" source="../media/incident-id.png" alt-text="Skærmbillede: Søger efter hændelses-id i Administration":::

### <a name="support-ticket-insight-for-premier-organizations"></a>Supportanmodningsindsigt for Premier-organisationer

Vi har tilføjet to grafer kaldet **Volumentendens** og **Volumentendens efter produkt** for at give dig visuel indsigt i din supportvolumen.

Kurvediagrammet under fanen **Volumentendens** fremhæver tendensen, hvis supportsagerne er stigende eller faldende for din organisation måned for måned. Du kan holde markøren over grafen for at kontrollere antallet af supportsager, der er oprettet i hver måned.

:::image type="content" source="../media/SuppInsight-voltrnd.PNG" alt-text="Skærmbillede: Graph, der fremhæver tendensen, hvis supportsager er stigende eller faldende for din organisation måned for måned":::

**Grafen Mængdetendens efter produkt** viser de øverste 3 produkter i hver måned med de højeste supportsager. Vi har aktiveret filtrering i tabellen, og du kan nu filtrere resultaterne efter **Produkt**, **Alvorsgrad** og **Dato**.

:::image type="content" source="../media/SuppInsight-voltrndproduct.PNG" alt-text="Skærmbillede: Graph viser de øverste 3 produkter i hver måned med de højeste supportsager":::

Vi har også tilføjet to nye felter, **Alvorsgrad** og **Lukket dato** i tabellen **Vis serviceanmodning** for at give dig mere indsigt i dine billetter.

:::image type="content" source="../media/SuppInsight-date-sev.PNG" alt-text="Skærmbillede: Tabel, der viser sortering af supportanmodninger efter alvorsgrad og dato.":::

Hvis du vil se disse opdateringer i <a href="https://go.microsoft.com/fwlink/p/?linkid=2166757" target="_blank">Microsoft 365 Administration</a>, skal du gå til **SupportView** >  **Service-anmodninger** i venstre navigationsrude.

## <a name="june-2021"></a>Juni 2021

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 Administration søgning

Vi har føjet et par nye kategorier til søgefunktionen.

- Du kan nu søge efter Microsoft 365 administratorroller i global søgning og hurtigt få vist og administrere rolletildelinger fra en hvilken som helst side. Søg f.eks. efter **Intune administrator**.

- Du kan nu finde forenklede konfigurationsoplevelser via global søgning. Dette kan hjælpe dig og dit team med hurtigt at komme i gang med, hvordan du bruger nye funktioner. Søg f.eks. efter **angiv adgangskode til aldrig at udløbe**.

Hvis du vil vide mere om søgning i Administration, skal du se [Søg i Microsoft 365 Administration](manage/search-in-the-mac.md).

## <a name="may-2021"></a>Maj 2021

### <a name="admin-mobile-app"></a>Mobilappen Administration

### <a name="keep-track-of-support-ticket-updates-using-the-admin-mobile-app"></a>Hold styr på opdateringer af supportanmodninger ved hjælp af mobilappen Administrator

For alle de serviceanmodninger, der er oprettet i din lejer, kan du nu holde styr på billetstatussen, få vist oplysninger om billetten og angive/anmode om yderligere oplysninger ved at tilføje noter & vedhæftede filer.

:::image type="content" source="../media/Keep-track-support-ticket-updates2.PNG" alt-text="Skærmbillede: Spor opdateringer af supportanmodninger":::

### <a name="stay-on-top-of-all-the-major-updates-to-the-app-and-your-microsoft-365-subscription"></a>Hold dig opdateret om alle de store opdateringer til appen og dit Microsoft 365 abonnement

- Hold dig opdateret om alle de store opdateringer til dit Microsoft 365 abonnement via Pushmeddelelser i Meddelelsescenter (nu aktiveret som standard).

- Hold styr på de nyeste funktioner, der er tilgængelige i appen, ved hjælp af afsnittet **Nyheder** . Gå til **Indstillinger** >  **Hvad er nyt?**

:::image type="content" source="../media/Stay-on-top-of-updates.PNG" alt-text="Skærmbillede: Spor større opdateringer og funktioner":::

## <a name="april-2021"></a>I april 2021

### <a name="admin-mobile-app"></a>Mobilappen Administration

### <a name="manage-licenses-and-bills-from-the-admin-mobile-app"></a>Administrer licenser og regninger fra mobilappen Administrator

- Du kan nu få vist alle tilgængelige og tildelte licenser til dine abonnementer. Du kan også tildele eller fjerne licenser til brugere og tilføje eller fjerne licenser.
- Du kan nu få vist detaljerede fakturaer i appen.
- Disse opdateringer er tilgængelige på både [Android-](https://go.microsoft.com/fwlink/p/?linkid=2159786) og [iOS-enheder](https://go.microsoft.com/fwlink/p/?linkid=2159787) .

:::image type="content" source="../media/assign-license-mobile-app2.png" alt-text="Skærmbillede: Siden Tildel licens til administratormobilapp":::
:::image type="content" source="../media/license-screen-mobile-app2.png" alt-text="Skærmbillede: Skærmen Administrator af mobilapp med brugere og deres licenser":::
:::image type="content" source="../media/invoice-summary-mobile-app.png" alt-text="Skærmbillede: Siden Med oversigt over faktura i mobilappen til administration":::

### <a name="updated-message-center-feed-in-the-admin-mobile-app"></a>Opdateret feed til Meddelelsescenter i administrationsmobilappen

- Du har nu en mere fleksibel læseoplevelse i Meddelelsescenter-feedet. Du har nu mulighed for at filtrere meddelelser baseret på tjenesten eller mærker og markere meddelelser som favoritter. Der er også tilføjet massehandlinger til markering af meddelelser som læst, ulæst eller arkiveret.
- Disse opdateringer er tilgængelige på både [Android-](https://go.microsoft.com/fwlink/p/?linkid=2159786) og [iOS-enheder](https://go.microsoft.com/fwlink/p/?linkid=2159787) .

:::image type="content" source="../media/mc-feed-mobile-app.png" alt-text="Skærmbillede: Siden Meddelelsescenter for administration af mobilapps":::

## <a name="ignite-2021-march"></a>Ignite 2021 (marts)

Velkommen til Microsoft Ignite. Vi håber, at du kunne deltage i nogle af vores sessioner: [Microsoft Ignite 2021](https://myignite.microsoft.com/sessions). Her er nogle af de ting, vi talte om på Ignite.
> [!NOTE]
> Ikke alle funktioner vil være tilgængelige for alle med det samme. Hvis du ikke kan se de nye funktioner, [kan du tilmelde dig Målrettet udgivelse](manage/release-options-in-office-365.md).

### <a name="message-center"></a>Meddelelsescenter

Vi har moderniseret Meddelelsescenter for at hjælpe dig med at finde relevante meddelelser og tilføjet en mere fleksibel læseoplevelse. Vi har tilføjet en ny **kolonne af typen Tjeneste** for at hjælpe dig med at scanne, hvilken tjeneste en meddelelse gælder for, og filtrere meddelelser efter tjeneste og andre metadata. Du kan markere en meddelelse som favorit til opfølgning, vælge, hvilke kolonner der skal vises på meddelelseslisten, og navigere mellem meddelelser med knapperne Tilbage og Næste. Vi har også forbedret processen for at gøre det nemmere at give feedback på meddelelser i Meddelelsescenter.

:::image type="content" source="../media/message-center.png" alt-text="Skærmbillede: Startsiden for Meddelelsescenter, der viser indbakke og meddelelser":::

Du kan få mere at vide om de nye funktioner i [Meddelelsescenter](manage/message-center.md).

### <a name="whats-new-features"></a>Nyheder

Vi har foretaget forbedringer af, hvordan du får vist funktionerne "Nyheder" for brugerne i Office apps. Du kan nu se det omfattende indhold i ruden Nyheder, som dine brugere kan se. Du kan også få mere at vide om funktionen, før du beslutter dig for at fortælle dine brugere om funktionen. Du kan finde flere oplysninger i [Administrer, hvilke Office funktioner der vises i Nyheder](manage/show-hide-new-features.md).

:::image type="content" source="../media/power-bi-whats-new2.png" alt-text="Skærmbillede: Office apps siden Nyheder, der viser forbedringer af Power BI":::
