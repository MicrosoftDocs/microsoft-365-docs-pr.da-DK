---
title: Begræns gæstedeling for bestemte organisationer
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du begrænser gæstedeling til bestemte Azure AD eller Microsoft 365-organisationer.
ms.openlocfilehash: 75cfe739e1cdde2e0bd959382b2444487ea726be
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "66858314"
---
# <a name="limit-guest-sharing-to-specific-organizations"></a>Begræns gæstedeling for bestemte organisationer

Brugerne kan som standard invitere personer uden for organisationen som gæster. Dette omfatter at invitere dem til teams i Microsoft Team, SharePoint-websteder og dele individuelle filer og mapper med dem.

Hvis du kun vil have, at dine brugere skal invitere gæster fra bestemte organisationer, kan du angive disse organisationer i indstillingerne for adgang til [B2B-samarbejde](/azure/active-directory/external-identities/what-is-b2b) på tværs af lejere i Azure Active Directory.

## <a name="configure-cross-tenant-access-settings"></a>Konfigurer adgangsindstillinger på tværs af lejere

Det første trin i begrænsningen af gæstedeling er at ændre standardindstillingerne i Azure AD adgangsindstillinger på tværs af lejere for som standard at blokere invitation af gæster. Derefter kan du tillade gæsteinvitationer for bestemte organisationer.

> [!NOTE]
> Det kan tage to timer, før ændringer af adgangsindstillinger på tværs af lejere træder i kraft.

### <a name="set-the-default-b2b-collaboration-settings-to-block-inviting-guests"></a>Angiv standardindstillingerne for B2B-samarbejde for at blokere invitation af gæster

Da invitation af gæster er aktiveret som standard, kræver begrænsning af gæsteinvitationer til visse organisationer som standard blokering af indgående B2B-samarbejde.

Sådan blokerer du som standard indgående B2B-samarbejde
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. Vælg **Eksterne identiteter**, og vælg derefter **Indstillinger for adgang på tværs af lejere (prøveversion)**.
1. Vælg fanen **Standardindstillinger** .
1. Under **Indstillinger for indgående adgang** skal du vælge **Rediger indgående standarder**.
1. Vælg fanen **B2B-samarbejde** og fanen **Brugere og grupper** .
1. Under **Adgangsstatus** skal du vælge **Bloker adgang**.
1. Vælg fanen **Ekstern adgang** .
1. Under **Adgangsstatus** skal du vælge **Bloker adgang**.
1. Vælg **Gem**.
1. Luk bladet **Standardindstillinger** .

### <a name="add-the-organization-where-you-want-to-allow-guest-invitations"></a>Tilføj den organisation, hvor du vil tillade gæsteinvitationer

Tilføj derefter de organisationer, hvor du vil give dine brugere tilladelse til at invitere gæster til Azure AD adgangsliste på tværs af lejere.

Sådan tilføjer du en organisation
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere (prøveversion)**.
1. Vælg **Indstillinger for organisation**.
1. Vælg **Tilføj organisation**.
1. Skriv det fulde domænenavn (eller lejer-id) for organisationen i ruden **Tilføj organisation** .
1. Vælg organisationen i søgeresultaterne, og vælg derefter **Tilføj**.
1. Organisationen vises på listen **Organisationsindstillinger** .

På dette tidspunkt nedarves alle adgangsindstillinger for denne organisation fra dine standardindstillinger.

### <a name="configure-inbound-settings-for-the-organization-to-allow-all-users"></a>Konfigurer indgående indstillinger for organisationen for at tillade alle brugere

Når du har tilføjet organisationen, skal du opdatere organisationens indgående indstillinger, så B2B-samarbejdsbrugere kan inviteres som gæster. Gør dette for hver organisation, hvor du vil tillade, at dine brugere kan invitere gæster.

1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere (prøveversion)**.
1. Vælg linket til indgående adgang for den organisation, du vil ændre.
1. På fanen **B2B-samarbejde** skal du vælge **Tilpas indstillinger**.
1. Under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Under **Mål** skal du vælge at tillade alle brugere.
1. Vælg **Gem** , og luk bladet **Indstillinger for udgående adgang** .

## <a name="turn-off-one-time-passcode-authentication"></a>Slå engangsgodkendelse af adgangskode fra

Selvom du har begrænset B2B-samarbejde til visse organisationer, kan andre stadig dele filer og mapper med personer i andre organisationer – de får bare ikke en gæstekonto i din mappe.

Hvis du vil forhindre, at delingen udelukkende sker med andre organisationer, skal du deaktivere funktionen til engangs-adgangskode i Azure AD. Dette forhindrer personer uden for din organisation i at blive sendt en engangs-adgangskode til godkendelse til delte filer eller mapper.

Sådan deaktiverer du funktionen til engangspaskode for mail
1. Log på [Azure Portal](https://portal.azure.com/) som Azure AD global administrator.
1. Vælg **Azure Active Directory** i navigationsruden.
1. Vælg **Eksterne identiteter****Alle identitetsudbydere** > .
1. Vælg **Mail engangs-adgangskode**, og vælg derefter **Deaktiver engangspaskode for gæster** under **Send engangskode til gæster** (eller **Nej**, hvis funktionen tidligere er aktiveret, deaktiveret eller tilmeldt under prøveversion).
1. Vælg **Gem**.

## <a name="related-topics"></a>Relaterede emner

[Oversigt over B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Konfigurer adgangsindstillinger på tværs af lejere for direkte B2B-forbindelse](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Begræns, hvem der kan inviteres af en organisation](limit-invitations-from-specific-organization.md)

[Begræns organisationer, hvor brugerne kan have gæstekonti](limit-organizations-where-users-have-guest-accounts.md)