---
title: Aktivér delte kanaler med alle eksterne organisationer
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
description: Få mere at vide om, hvordan du aktiverer delte kanaler med alle andre Microsoft 365- og Azure Active Directory-organisationer.
ms.openlocfilehash: 601bfaa825afdaf9ec5addb4b7c7e21804b07cb7
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "66858306"
---
# <a name="enable-shared-channels-with-all-external-organizations"></a>Aktivér delte kanaler med alle eksterne organisationer

Selvom deling af delte kanaler eksternt er aktiveret som standard i Teams, skal azure Active Directory-adgangsindstillinger på tværs af lejere for [direkte B2B-forbindelse](/azure/active-directory/external-identities/b2b-direct-connect-overview) også konfigureres til at dele en kanal eksternt. Disse indstillinger er som standard angivet til at blokere alle organisationer.

Du kan ændre standardindstillingerne for direkte forbindelse mellem B2B for at tillade alle organisationer. Dette giver brugerne mulighed for at samarbejde i delte kanaler, uden at din organisation skal oprette en separat konfiguration for hver organisation, som du vil samarbejde med. Bemærk, at de organisationer, du samarbejder med, også skal konfigurere deres B2B-indstillinger for direkte forbindelse.

Hvis din organisation ikke har et krav om at begrænse samarbejdet med andre organisationer, kan aktivering af alle organisationer som standard spare dig tid og kompleksitet ved at administrere hver organisation separat.

> [!NOTE]
> Det kan tage to timer, før ændringer af adgangsindstillinger på tværs af lejere træder i kraft.

## <a name="allow-users-to-invite-people-in-other-organizations-to-participate-in-shared-channels"></a>Tillad brugere at invitere personer i andre organisationer til at deltage i delte kanaler

Du kan som standard give dine brugere tilladelse til at invitere personer fra andre organisationer til at bruge delte ressourcer, f.eks. delte kanaler i Teams.

Sådan gør du det muligt for brugerne at invitere deltagere med direkte forbindelse til B2B som standard
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. Vælg **Eksterne identiteter**, og vælg derefter **Indstillinger for adgang på tværs af lejere (prøveversion)**.
1. Under fanen **Standardindstillinger** under **Indstillinger for indgående adgang** skal du vælge **Rediger indgående standarder**.
1. Vælg fanen **B2B Direct Connect** .
1. Under fanen **Brugere og grupper** under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Under fanen **Eksterne programmer** under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Vælg **Gem**.
1. Vælg fanen **Indstillinger for tillid** .
1. Vælg, om du vil have tillid til multifaktorgodkendelse, kompatible enheder eller hybride Azure AD tilsluttede enheder fra andre organisationer.
1. Vælg **Gem**.
1. Luk bladet **Standardindstillinger** .

## <a name="allow-users-to-participate-in-shared-channels-in-other-organizations"></a>Tillad brugere at deltage i delte kanaler i andre organisationer

Du kan give dine brugere adgang til ressourcer, der hostes af en ekstern organisation – f.eks. delte kanaler i Teams – som standard.

Sådan giver du brugerne adgang til ressourcer fra andre organisationer som standard
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere (prøveversion)**.
1. Under fanen **Standardindstillinger** under **Indstillinger for udgående adgang** skal du vælge **Rediger udgående standarder**.
1. Vælg fanen **B2B Direct Connect** .
1. Under fanen **Brugere og grupper** under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Under fanen **Eksterne programmer** under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Vælg **Gem**.
1. Luk bladet **Standardindstillinger** .

## <a name="related-topics"></a>Relaterede emner

[Oversigt over B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Konfigurer adgangsindstillinger på tværs af lejere for direkte B2B-forbindelse](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

