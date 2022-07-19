---
title: Kræv betinget adgang for personer uden for din organisation
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
description: Få mere at vide om, hvordan du kræver, at personer uden for din organisation består kontrol af betinget adgang, f.eks. MFA og enheder, der overholder angivne standarder.
ms.openlocfilehash: a9a48bd891810530fba4f78824f675d2b0f0556e
ms.sourcegitcommit: c33af120921d3c4fb5c362dac3e74f0ab3d1e58d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/06/2022
ms.locfileid: "66858482"
---
# <a name="require-conditional-access-for-people-outside-your-organization"></a>Kræv betinget adgang for personer uden for din organisation

Du kan kræve en af følgende indstillinger for betinget adgang for personer uden for din organisation:

- Multifaktorgodkendelse
- Enheder, der overholder angivne standarder
- Hybride Azure AD tilsluttede enheder

Når du bruger Azure AD B2B-direkte forbindelse – f.eks. med delte kanaler i Teams – kan du vælge at have tillid til indstillingerne for betinget adgang fra andre organisationer for disse muligheder. Bemærk, at politikkerne for betinget adgang kun bruges til at få adgang til fanen Filer i den delte kanal og det tilknyttede SharePoint-websted.

## <a name="planning-considerations-for-conditional-access"></a>Overvejelser i forbindelse med planlægning af betinget adgang

Multifaktorgodkendelse kan bruges med enhver ekstern konto. Hvis din organisation ikke har tillid til multifaktorgodkendelse fra andre Azure AD organisationer, skal brugere fra disse organisationer udføre multifaktorgodkendelse, når de får adgang til ressourcer i din organisation. Personer med mailadresser fra tredjepart (ikke hostet af Microsoft) bliver altid bedt om multifaktorgodkendelse.

Indstillingerne **Kræv, at enheden er markeret som kompatibel** og **Kræv hybrid Azure AD tilsluttet enhed** kræver enheder, der administreres i Azure AD. Hvis du vælger at aktivere disse indstillinger, skal personer uden for organisationen bruge enheder, der administreres af din organisation eller af en organisation, du har tillid til. Personer uden administrerede enheder blokeres, herunder:

- Personer med mailadresser fra tredjepart eller forbrugere
- Personer fra Microsoft 365 eller Azure AD organisationer, der ikke administrerer enheder
- Personer fra Microsoft 365 eller Azure AD organisationer, der kræver administrerede enheder, hvor din organisation ikke har tillid til deres indstillinger for betinget adgang.

Vi anbefaler, at du er forsigtig, når du kræver overholdelse eller hybrid Azure AD tilsluttede enheder, da dette vil blokere mange eksterne samarbejdsscenarier. Sørg for, at alle dine partnerorganisationer administrerer deres enheder, og at din organisation har tillid til deres indstillinger.

## <a name="set-up-conditional-access-requirements-for-people-outside-your-organization"></a>Konfigurer krav til betinget adgang for personer uden for din organisation

Hvis du vil kræve betinget adgang for personer uden for din organisation, skal du gøre følgende:

1. [Vælg indstillinger for betinget adgang for at have tillid fra andre organisationer](#choose-conditional-access-settings-to-trust-from-other-organizations).
1. [Konfigurer betinget adgang for personer uden for din organisation](#set-up-conditional-access-for-people-outside-your-organization).

## <a name="choose-conditional-access-settings-to-trust-from-other-organizations"></a>Vælg indstillinger for betinget adgang, som andre organisationer skal have tillid til

Du kan vælge at have tillid til indstillinger for betinget adgang fra alle andre Microsoft 365- og Azure AD organisationer eller kun fra dem, du angiver.

> [!NOTE]
> Det kan tage to timer, før ændringer af adgangsindstillinger på tværs af lejere træder i kraft.

### <a name="trust-conditional-access-settings-from-all-azure-active-directory-organizations"></a>Hav tillid til indstillinger for betinget adgang fra alle Azure Active Directory-organisationer

Hvis du vil have tillid til indstillinger for betinget adgang fra alle organisationer, skal du følge denne procedure.

Sådan har du tillid til indstillinger for betinget adgang fra alle Azure Active Directory-organisationer
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. Vælg **Eksterne identiteter**, og vælg derefter **Indstillinger for adgang på tværs af lejere (prøveversion)**.
1. Vælg fanen **Standardindstillinger** .
1. Under **Indstillinger for indgående adgang** skal du vælge **Rediger indgående standarder**.
1. Vælg fanen **Indstillinger for tillid** .
1. Vælg, hvilke indstillinger politikker for betinget adgang skal acceptere fra andre organisationer.
1. Vælg **Gem** , og luk bladet **Standardindstillinger** .

### <a name="trust-conditional-access-settings-from-a-specific-organization"></a>Hav tillid til indstillinger for betinget adgang fra en bestemt organisation

Hvis du vil have tillid til indstillinger for betinget adgang fra en bestemt organisation, skal du følge denne procedure.

Sådan har du tillid til indstillinger for betinget adgang fra en bestemt organisation
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. Vælg **Eksterne identiteter**, og vælg derefter **Indstillinger for adgang på tværs af lejere (prøveversion)**.
1. Vælg indstillingerne for **indgående adgang** for den organisation, hvor du vil have tillid til indstillinger for betinget adgang.
1. Vælg fanen **Indstillinger for tillid** .
1. Vælg indstillingen **Tilpas indstillinger** .
1. Vælg, hvilke indstillinger politikker for betinget adgang skal acceptere fra andre organisationer.
1. Vælg **Gem** , og luk bladet **Standardindstillinger** .

## <a name="set-up-conditional-access-for-people-outside-your-organization"></a>Konfigurer betinget adgang for personer uden for din organisation

Konfiguration af en politik for betinget adgang for personer uden for organisationen påvirker følgende:

- Personer, der bruger gæstekonti (Azure AD B2B-samarbejdsbrugere)
- Eksterne deltagere i delte Teams-kanaler (Azure AD B2B-brugere med direkte forbindelse)

> [!IMPORTANT]
> Vælg kun **Kræv, at enheden er markeret som kompatibel** eller **Kræv hybrid Azure AD tilsluttet enhed**, hvis alle uden for organisationen bruger en enhed, der administreres af din organisation eller af en Microsoft 365- eller Azure AD-organisation, der er tillid til.

Sådan konfigurerer du betinget adgang for personer uden for din organisation
1. Gå til [Politikker for betinget adgang i Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
1. I **| Betinget adgang Bladet Politikker** , og klik på **Ny politik**.
1. Skriv et navn i feltet **Navn** .
1. Klik på **Brugere og grupper** under **Tildelinger**.
1. På bladet **Brugere og grupper** skal du vælge **Vælg brugere og grupper**, markere afkrydsningsfeltet **Alle gæster og eksterne brugere** .
1. Klik på **Cloudapps eller -handlinger** under **Tildelinger**.
1. På bladet **Cloud-apps eller -handlinger** skal du vælge **Alle cloudapps** under fanen **Medtag** .
1. Klik på **Grant (Tildel**) under **Access controls (Adgangskontrolelementer**).
1. På bladet **Tildel** skal du vælge de indstillinger, du vil kræve for personer uden for din organisation, og derefter klikke på **Vælg**.
1. Klik på **Til** under **Aktivér politik** på bladet **Ny**, og klik derefter på **Opret**.

## <a name="related-topics"></a>Relaterede emner

[Selvstudium: Gennemtving multifaktorgodkendelse for B2B-gæster](/azure/active-directory/external-identities/b2b-tutorial-require-mfa)
