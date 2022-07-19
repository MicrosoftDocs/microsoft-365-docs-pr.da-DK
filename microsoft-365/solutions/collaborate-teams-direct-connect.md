---
title: Samarbejd med eksterne deltagere i en delt kanal
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom: ''
localization_priority: Priority
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du aktiverer delte kanaler i Microsoft Teams til samarbejde med personer uden for din organisation.
ms.openlocfilehash: ae076b5bfb653fd1a90d9260d699d454246200a0
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66858959"
---
# <a name="collaborate-with-external-participants-in-a-shared-channel"></a>Samarbejd med eksterne deltagere i en delt kanal

Hvis du vil give dine brugere mulighed for at samarbejde med personer uden for din organisation i [delte kanaler](/MicrosoftTeams/shared-channels), skal du konfigurere B2B Direkte forbindelse for hver organisation, du vil samarbejde med. Du kan også [aktivere delte kanaler med alle eksterne organisationer](/microsoft-365/solutions/allow-direct-connect-with-all-organizations).

Når du aktiverer delte kanaler i Teams med en anden organisation:

- Teamejere i din organisation kan invitere personer fra andre organisationer til at deltage i delte kanaler.
- Organisationens brugerdefinerede apps (brancheapps) vil være tilgængelige i delte kanaler, og eksterne deltagere vil kunne få adgang til dem.
- Organisationens appliste vil være tilgængelig i delte kanaler, og eksterne deltagere vil kunne få adgang til dem.

## <a name="video-demonstration"></a>Videodemonstration

I denne video vises de konfigurationstrin, der er beskrevet i dette dokument.
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4WRMx?autoplay=false]

## <a name="enable-shared-channels-in-teams"></a>Aktivér delte kanaler i Teams

Delte kanaler er som standard aktiveret i Teams. Følg denne procedure for at bekræfte indstillingerne.

Sådan konfigurerer du delte kanaler
1. Udvid **Teams** i [Teams Administration](https://admin.teams.microsoft.com/), og vælg derefter **Teams-politikker**.
1. Vælg den politik, du vil aktivere delte kanaler for, og vælg derefter **Rediger**.
1. Vælg de indstillinger, du vil aktivere:
    - Hvis du vil tillade teamejere at oprette delte kanaler, skal du slå **Opret delte kanaler** til.
    - Hvis du vil tillade teamejere at dele delte kanaler med personer uden for organisationen, skal du slå **Inviter eksterne brugere til delte kanaler** til.
    - Hvis du vil tillade, at brugere inviteres til delte kanaler i andre organisationer, skal du slå **Deltag i eksterne delte kanaler** til.
1. Vælg **Anvend**.

Hvis eksterne kanaldeltagere skal kunne deltage i møder, skal ekstern adgang være aktiveret. Dette er også påkrævet for at kunne se eksterne deltageres tilstedeværelse i kanalen.

Sådan aktiverer du ekstern adgang
1. I [Teams Administration](https://admin.teams.microsoft.com/) skal du udvide **Brugere** og derefter vælge **Ekstern adgang**.
1. Under **Teams og Skype for Business brugere i eksterne organisationer** skal du sikre, at de organisationer, du vil samarbejde med, ikke er blokeret.

## <a name="configure-cross-tenant-access-settings-in-azure-ad"></a>Konfigurer adgangsindstillinger på tværs af lejere i Azure AD

Azure AD direkte forbindelse til B2B er deaktiveret som standard. Hvis du vil aktivere samarbejde i delte kanaler med personer fra andre organisationer, skal du:

1. [Tilføj en organisation](#add-an-organization).
1. [Konfigurer indgående indstillinger](#configure-inbound-settings) for organisationen for at tillade, at brugere fra organisationen inviteres til dine delte kanaler.
1. [Konfigurer udgående indstillinger](#configure-outbound-settings) for organisationen, så dine brugere kan inviteres til den anden organisations delte kanaler.

Som en del af denne konfiguration aktiverer vi **Office 365-programmet**, som omfatter Teams- og Teams-integrerede tjenester, f.eks. SharePoint.

> [!NOTE]
> Det kan tage op til seks timer, før ændringer af adgangsindstillinger på tværs af lejere træder i kraft.

> [!NOTE]
> Delte kanaler mellem kommercielle og GCC-cloudmiljøer understøttes ikke.

### <a name="add-an-organization"></a>Tilføj en organisation

Tilføj hver organisation, som du vil deltage i delte kanaler med.

Sådan tilføjer du en organisation
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. Vælg **Eksterne identiteter**, og vælg derefter **Adgangsindstillinger på tværs af lejere**.
1. Vælg **Indstillinger for organisation**.
1. Vælg **Tilføj organisation**.
1. Skriv det fulde domænenavn (eller lejer-id) for organisationen i ruden **Tilføj organisation** , og tryk på Enter.
1. Vælg **Tilføj**.
1. Organisationen vises på listen over organisationer. På dette tidspunkt nedarves alle adgangsindstillinger for denne organisation fra dine standardindstillinger.

### <a name="configure-inbound-settings"></a>Konfigurer indgående indstillinger

Følg denne procedure for hver organisation, hvor du vil invitere eksterne deltagere.

Sådan konfigurerer du indgående indstillinger for en organisation
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere**.
1. Vælg linket til indgående adgang for den organisation, du vil ændre.
1. På fanen **B2B Direct Connect** skal du vælge **Tilpas indstillinger**.
1. På fanen **Eksterne brugere og grupper** skal du vælge **Tillad adgang** og **Alle eksterne brugere og grupper**. Du kan vælge **Vælg eksterne brugere og grupper** , hvis du vil begrænse adgangen til bestemte brugere og grupper, f.eks. dem, der har underskrevet en fortrolighedsaftale.
1. Under fanen **Programmer** skal du vælge **Tillad adgang** og **Vælg programmer**.
1. Vælg **Tilføj Microsoft-programmer**.
1. Vælg **programmet Office 365**, og vælg derefter **Vælg**.
1. Vælg **Gem** , og luk bladet **Indstillinger for indgående adgang** .

### <a name="configure-outbound-settings"></a>Konfigurer udgående indstillinger

Følg denne procedure for hver organisation, hvor brugerne skal kunne deltage i eksterne delte kanaler.

Sådan konfigurerer du udgående indstillinger for en organisation
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere**.
1. Vælg linket til udgående adgang for den organisation, du vil ændre.
1. På fanen **B2B Direct Connect** skal du vælge **Tilpas indstillinger**.
1. Under fanen **Eksterne brugere og grupper** skal du vælge **Tillad adgang** og angive **Gælder for** alle brugere.
1. Under fanen **Eksterne programmer** skal du vælge **Tillad adgang** og **Vælg eksterne programmer**.
1. Vælg **Tilføj Microsoft-programmer**.
1. Vælg **programmet Office 365**, og vælg derefter **Vælg**.
1. Vælg **Gem**, vælg **Ja** for at bekræfte, og luk bladet **Indstillinger for udgående adgang** .

## <a name="see-also"></a>Se også

[Oversigt over B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Konfigurer adgangsindstillinger på tværs af lejere for direkte B2B-forbindelse](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Begræns, hvem der kan inviteres af en organisation](limit-invitations-from-specific-organization.md)

[Grænser for delte kanaler](/MicrosoftTeams/shared-channels#shared-channel-limits)
