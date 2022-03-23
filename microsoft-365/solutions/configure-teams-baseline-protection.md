---
title: Konfigurer teams med beskyttelse mod grundlinjer
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkTEAMS
- admindeeplinkSPO
recommendations: false
description: Få mere at vide om, hvordan du installerer teams med et oprindeligt beskyttelsesniveau.
ms.openlocfilehash: 21fe46a9df9b67c41ff2c0a21fbbe175295e1fdf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590064"
---
# <a name="configure-teams-with-baseline-protection"></a>Konfigurer teams med beskyttelse mod grundlinjer

I denne artikel ser vi på, hvordan du installerer teams med et oprindeligt beskyttelsesniveau. Dette niveau giver brugerne en lang række muligheder for samarbejde, mens de forbedrer administrationen af tilladelser og giver grundlæggende beskyttelse mod overdeling. Anbefalede beskyttelser på dette niveau omfatter politikker for identitets- og enhedsadgang og beskyttelse mod malware. Desuden kan du anvende betingede adgangspolitikker og beskyttelse mod datatab efter behov.

## <a name="initial-protections"></a>Indledende beskyttelse

Som det første trin anbefaler vi, at du konfigurerer grundlæggende identitets- og enhedsadgangspolitikker. Se [Politikanbefalinger for sikring Teams chatsamtaler, grupper og filer for at](../security/office-365-security/teams-access-policies.md) få flere oplysninger.

Vi anbefaler også, at du slår grundlæggende Defender til Office 365 funktioner til for at beskytte mod malware i dokumenter, vedhæftede filer og links. Vi anbefaler, at du slår hver af indstillingerne i følgende tabel til.

|Indstilling|Oplysninger|
|:------|:-----------|
|Pengeskab vedhæftede filer til SPO, OneDrive og Teams|[Pengeskab vedhæftede filer](../security/office-365-security/safe-attachments.md) <p> [Defender til Office 365 – SharePoint, OneDrive og Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md)|
|Sikre dokumenter|[Pengeskab dokumenter i Microsoft Defender til Office 365](../security/office-365-security/safe-docs.md)|
|Pengeskab Links til Teams|[Office 365 Pengeskab Links i Teams](../security/office-365-security/safe-links.md) <p> [Sikre links](../security/office-365-security/safe-links.md)|

## <a name="teams-guest-sharing"></a>Teams gæstedeling

I hvert niveau har vi mulighed for at dele med personer uden for organisationen. For de følsomme og meget følsomme niveauer har vi mulighed for at slå gæstedeling fra på teamniveau ved hjælp af følsomhedsmærkater. Men indstillingen for gæstedeling på organisationsniveau skal være slået til, for at gæstedeling overhovedet kan fungere Teams.

![Skærmbillede af Teams til/fra-knap for gæsteadgang.](../media/teams-guest-access-toggle-on.png)

Sådan angives Teams indstillingerne for gæsteadgang

1. Log på Microsoft 365 Administration på [https://admin.microsoft.com](https://admin.microsoft.com).
2. I venstre navigationsrude skal du klikke **på Vis alle**.
3. Under **Administration skal** du klikke **på Teams**.
4. På siden Teams Administration skal du i venstre navigationsrude **udvide Indstillinger for** >  hele <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**organisationenGuest-adgang**</a>.
5. Sørg for **, at Tillad gæsteadgang Teams** er indstillet til **Til**.
6. Foretag de ønskede ændringer af de ekstra gæsteindstillinger, og klik derefter på **Gem**.

> [!NOTE]
> Det kan tage op til fireogtyve timer, før Teams bliver aktiv, efter du har aktiveret den.

Gæstedeling er som standard slået til for Office 365-grupper og SharePoint, men hvis du tidligere har ændret nogen af indstillingerne for gæstedeling for din organisation, anbefaler vi, at du gennemser Samarbejd med gæster i et [team](./collaborate-as-team.md) for at sikre, at gæstedeling er tilgængelig i Teams.

## <a name="site-and-file-sharing"></a>Websteds- og fildeling

For at reducere risikoen for utilsigtet deling af filer eller mapper med personer uden for organisationen anbefaler vi, at du ændrer standardlinket til deling for SharePoint til Kun personer *i organisationen*. Hvis brugerne skal dele eksternt, og du har aktiveret gæstedeling, kan de stadig ændre linktypen, når de deler.

Sådan ændrer du standardlinket til deling

1. Åbn SharePoint Administration, og **vælg Deling** under <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Politikker**</a>.
1. Under **Fil- og mappelinks** skal **du vælge Kun personer i organisationen**.
1. Vælg **Gem**.

For at få den bedste oplevelse med gæstedeling anbefaler vi også, at [du SharePoint OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview).

## <a name="create-a-team"></a>Opret et team

Yderligere konfiguration for det oprindelige beskyttelsesniveau foretages på det websted, SharePoint der er knyttet til et team. [Opret et offentligt eller privat team,](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) før du fortsætter til næste afsnit.

## <a name="site-sharing-settings"></a>Indstillinger for webstedsdeling

Som standard kan medlemmer af et SharePoint invitere andre til webstedet. Når et websted er en del af et team, er teammedlemmer inkluderet som webstedsmedlemmer. Men personer, der føjes direkte til webstedet, har ikke adgang til resten af teamet. Vi anbefaler derfor, at du kun administrerer tilladelser gennem teamet.

Som en hjælp til administration af tilladelser anbefaler vi, at du konfigurerer det tilknyttede websted til kun at tillade, at ejere deler webstedet alene. Dette forenkler administration af tilladelser og hjælper med at forhindre adgang for personer uden en teamejers viden. Gør dette for hvert team, der kræver beskyttelse af grundlinjer.

Sådan opdaterer du indstillingerne for deling af websteder
1. Klik på Filer på teamets **værktøjslinje**.
2. Klik **på Åbn SharePoint**.
3. Klik på ikonet indstillinger på SharePoint på webstedets værktøjslinje, og klik derefter på **Webstedstilladelser**.
4. I **ruden Webstedstilladelser** under Deling **af websted skal du** klikke **på Rediger, hvordan medlemmer kan dele**.
5. Under **Tilladelser til deling** skal du vælge Webstedsejere og -medlemmer, og personer med redigeringstilladelser kan dele filer og mapper, men kun **webstedsejere** kan dele webstedet, og klik derefter på **Gem**.

## <a name="additional-protections"></a>Yderligere beskyttelse

Microsoft 365 tilbyder yderligere metoder til sikring af dit indhold. Overvej, om følgende indstillinger kan være med til at forbedre sikkerheden for din organisation.

- Få gæster til at acceptere [vilkår for anvendelse](/azure/active-directory/conditional-access/terms-of-use).
- Konfigurer en [politik for timeout for en session](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) for gæster.
- Opret [typer af følsomme oplysninger,](../compliance/sensitive-information-type-learn-about.md) og brug [beskyttelse mod datatab til at](../compliance/dlp-learn-about-dlp.md) angive politikker vedrørende adgang til følsomme oplysninger.

## <a name="see-also"></a>Se også

[Administrer mødepolitikker i Teams](/microsoftteams/meeting-policies-in-teams)

[Kom i gang med insider-risikostyring](../compliance/insider-risk-management-configure.md)