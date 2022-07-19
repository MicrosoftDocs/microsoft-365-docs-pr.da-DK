---
title: Begræns organisationer, hvor brugerne kan have gæstekonti
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
description: Få mere at vide om, hvordan du angiver, hvilke organisationer dine brugere kan have gæstekonti i.
ms.openlocfilehash: 00db14560c491461435e41e30c106c2554d9ad61
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "66858303"
---
# <a name="limit-organizations-where-users-can-have-guest-accounts"></a>Begræns organisationer, hvor brugerne kan have gæstekonti

Andre Microsoft 365- og Azure Active Directory-organisationer kan som standard invitere dine brugere til at deltage i deres organisation som gæster. Dette omfatter at invitere dem til teams i Microsoft Team, SharePoint-websteder og dele individuelle filer og mapper med dem.

Hvis du kun vil have, at dine brugere skal deltage som gæster i bestemte organisationer, kan du angive disse organisationer i azure Active Directory-adgangsindstillingerne på tværs af lejere for [B2B-samarbejde](/azure/active-directory/external-identities/what-is-b2b).

> [!NOTE]
> Det kan tage to timer, før ændringer af adgangsindstillinger på tværs af lejere træder i kraft.

## <a name="set-the-default-b2b-collaboration-settings-to-block-users-from-being-guests"></a>Angiv standardindstillingerne for B2B-samarbejde for at forhindre brugere i at være gæster

Da deltagelse som gæster er aktiveret som standard, kræver begrænsning af gæstedeltagelse til visse organisationer, at udgående B2B-samarbejde som standard blokeres.

Sådan blokerer du udgående B2B-samarbejde som standard
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. Vælg **Eksterne identiteter**, og vælg derefter **Indstillinger for adgang på tværs af lejere (prøveversion)**.
1. Vælg fanen **Standardindstillinger** .
1. Under **Indstillinger for udgående adgang** skal du vælge **Rediger udgående standarder**.
1. Vælg fanen **B2B-samarbejde** og fanen **Brugere og grupper** .
1. Under **Adgangsstatus** skal du vælge **Bloker adgang**.
1. Vælg fanen **Ekstern adgang** .
1. Under **Adgangsstatus** skal du vælge **Bloker adgang**.
1. Vælg **Gem**.
1. Luk bladet **Standardindstillinger** .

## <a name="add-an-organization"></a>Tilføj en organisation

Derefter skal du tilføje de organisationer, hvor du vil tillade dine brugere at samarbejde som gæster, på Azure AD adgangsliste på tværs af lejere.

Sådan tilføjer du en organisation
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere (prøveversion)**.
1. Vælg **Indstillinger for organisation**.
1. Vælg **Tilføj organisation**.
1. Skriv det fulde domænenavn (eller lejer-id) for organisationen i ruden **Tilføj organisation** .
1. Vælg organisationen i søgeresultaterne, og vælg derefter **Tilføj**.
1. Organisationen vises på listen **Organisationsindstillinger** .

På dette tidspunkt nedarves alle adgangsindstillinger for denne organisation fra dine standardindstillinger.

## <a name="configure-the-organizations-outbound-setting-to-allow-all-users"></a>Konfigurer organisationens udgående indstilling for at tillade alle brugere

Når du har tilføjet organisationen, skal du opdatere organisationens udgående indstillinger, så B2B-samarbejdsbrugere kan tilføjes som gæster. Gør dette for hver organisation, hvor du vil tillade, at dine brugere tilføjes som gæster.

Sådan giver du brugere tilladelse til at samarbejde med B2B-gæster i en organisation
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere (prøveversion)**.
1. Vælg linket til udgående adgang for den organisation, du vil ændre.
1. På fanen **B2B-samarbejde** skal du vælge **Tilpas indstillinger**.
1. Under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Under **Mål** skal du vælge at tillade alle brugere.
1. Vælg **Gem** , og luk bladet **Indstillinger for udgående adgang** .

## <a name="related-topics"></a>Relaterede emner

[Oversigt over B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Konfigurer adgangsindstillinger på tværs af lejere for direkte B2B-forbindelse](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Begræns, hvem der kan inviteres af en organisation](limit-invitations-from-specific-organization.md)

[Begræns gæstedeling for bestemte organisationer](limit-guest-sharing-to-specific-organization.md)