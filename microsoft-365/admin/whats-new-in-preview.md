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
ms.openlocfilehash: 198832f09f6b219579f128b7104ecf3ae2fa3446
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65679346"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Nyheder i Microsoft 365 Administration

::: moniker range="o365-21vianet"

> [!NOTE]
> Nogle af oplysningerne i denne artikel gælder muligvis ikke for Office 365, der drives af 21Vianet.

::: moniker-end

Vi føjer løbende nye funktioner til [Microsoft 365 Administration](Oversigt over Microsoft 365 Administration](admin-overview/admin-center-overview.md), løse problemer, vi lærer om, og foretage ændringer baseret på din feedback. Nogle funktioner udrulles med forskellige hastigheder til vores kunder. Hvis du endnu ikke kan se en funktion, [kan du prøve at føje dig selv til målrettet udgivelse](manage/release-options-in-office-365.md).

Og hvis du gerne vil vide, hvad der er nyt med andre Microsoft-cloudtjenester:

- [Nyheder i Azure Active Directory](/azure/active-directory/fundamentals/whats-new)
- [Nyheder i Exchange Administration](/Exchange/whats-new)
- [Nyheder i Microsoft Intune](/mem/intune/fundamentals/whats-new)
- [Nyheder i Microsoft Purview-compliance-portal](/Office365/SecurityCompliance/whats-new)
- [Nyheder i Microsoft 365 Defender](../security/mtp/whats-new.md)
- [Nyheder i SharePoint Administration](/sharepoint/what-s-new-in-admin-center)
- [Office opdateringer](/OfficeUpdates/)
- [Sådan kontrollerer du Windows udgivelsestilstand](/windows/deployment/update/check-release-health)

## <a name="may-2022"></a>Maj 2022

### <a name="role-based-access-controls-rbac"></a>Rollebaseret adgangskontrol (RBAC)

Der er fire nye roller i Microsoft 365 Administration til administration af brugerdefinerede sikkerhedsattributter. Disse roller er tilgængelige, så alle kan bruge i Microsoft 365 Administration under **Roller**.

- **Administrator af attributtildeling**   Tildel brugerdefinerede sikkerhedsattributnøgler og -værdier til understøttede Azure AD objekter.

- **Attributtildelingslæser**   Læser brugerdefinerede sikkerhedsattributnøgler og -værdier for understøttede Azure AD objekter.

- **Attributdefinitionsadministrator**   Definer og administrer definitionen af brugerdefinerede sikkerhedsattributter.

- **Attributdefinitionslæser**   Læser definitionen af brugerdefinerede sikkerhedsattributter.

Der er også en ny rolle, der giver dig mulighed for kun at give administratorer den adgang, de har brug for til at administrere virtuelle besøg.

- **Administrator af virtuelle besøg**   Administrer og del oplysninger og målepunkter for virtuelle besøg fra administrationscentre eller appen Virtuelle besøg.

Du kan få flere oplysninger om disse roller [under Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).

### <a name="quick-assist"></a>Lynhjælp

Vi har flyttet Lynhjælp til Windows Store for at forbedre appens ydeevne og sikkerhed. Appen Windows Lynhjælp giver dig og dine slutbrugere mulighed for at modtage eller give pc-hjælp via en fjernforbindelse.

Med den nye Lynhjælp Store app kan du se en betydelig forbedring af tiderne for generering af adgangskode og en reduktion af programfejl.

Du kan finde flere oplysninger under [Løs pc-problemer via en fjernforbindelse](https://support.microsoft.com/windows/solve-pc-problems-over-a-remote-connection-b077e31a-16f4-2529-1a47-21f6a9040bf3), og [installér Lynhjælp](https://support.microsoft.com/windows/install-quick-assist-c17479b7-a49d-4d12-938c-dbfb97c88bca)

## <a name="april-2022"></a>April 2022

### <a name="nps-sentiment-insights"></a>NPS-tillid Insights

NPS-undersøgelsesindsigt er et AI-drevet dashboard, der er tilgængeligt i Microsoft 365 Administration.

I Administration skal du gå til Feedback **på tilstand Produktfeedback** >  >  **NPS-undersøgelsesindsigt**.

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

I Administration skal du gå til Feedback **på tilstand Produktfeedback** >  >  **NPS-undersøgelsesindsigt**.

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

Vi har opdateret vores Microsoft 365 Administration videotræning. Gå til siden [Administration videobibliotek for at](admin-video-library.yml) få mere at vide om, hvordan du konfigurerer og administrerer Microsoft 365 for din virksomhed.

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

Hvis du vil tjekke disse opdateringer ud i <a href="https://go.microsoft.com/fwlink/p/?linkid=2166757" target="_blank">Microsoft 365 Administration</a>, skal du gå til **Support** > **Vis tjenesteanmodninger** i venstre navigationsrude.

## <a name="june-2021"></a>Juni 2021

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 Administration søgning

Vi har føjet et par nye kategorier til søgefunktionen.

- Du kan nu søge efter Microsoft 365 administratorroller i global søgning og hurtigt få vist og administrere rolletildelinger fra en hvilken som helst side. Søg f.eks. efter **Intune administrator**.

- Du kan nu finde forenklede konfigurationsoplevelser via global søgning. Dette kan hjælpe dig og dit team med hurtigt at komme i gang med, hvordan du bruger nye funktioner. Søg f.eks. efter **angiv adgangskode til aldrig at udløbe**.

Hvis du vil vide mere om søgning i Administration, skal du se [Søg i Microsoft 365 Administration](manage/search-in-the-mac.md).
