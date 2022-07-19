---
title: Begræns, hvem der kan inviteres af en organisation
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
description: Få mere at vide om, hvordan du begrænser, hvilke af dine brugere der kan inviteres som gæst eller deltager i en delt kanal til en bestemt organisation.
ms.openlocfilehash: 599f83a4464498f7a964f02a955f802cb8545432
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "66858311"
---
# <a name="limit-who-can-be-invited-by-an-organization"></a>Begræns, hvem der kan inviteres af en organisation

Hvis du samarbejder med en anden organisation og vil begrænse, hvem der kan inviteres til denne organisation som gæst eller medlem af en delt kanal i Teams, kan du angive, hvem der kan inviteres i indstillingerne for adgang på tværs af lejere i Azure Active Directory.

> [!NOTE]
> Det kan tage to timer, før ændringer af adgangsindstillinger på tværs af lejere træder i kraft.

## <a name="create-a-security-group"></a>Opret en sikkerhedsgruppe

Den nemmeste måde at angive, hvem der kan inviteres til en anden organisation, er at bruge en sikkerhedsgruppe. Du kan bruge en sikkerhedsgruppe med et defineret medlemskab eller en dynamisk sikkerhedsgruppe. Du kan bruge en eksisterende sikkerhedsgruppe eller oprette en ny til dette formål.

Sådan opretter du en sikkerhedsgruppe
1. Log på [Azure Active Directory](https://aad.portal.azure.com) ved hjælp af en Global administrator- eller sikkerhedsadministratorkonto.
1. På siden **Active Directory** skal du vælge **Grupper** og derefter vælge **Ny gruppe**.
1. Vælg **Sikkerhed** for **gruppetypen**.
1. Skriv et **gruppenavn.** 
1. Du kan også tilføje en beskrivelse af gruppen.
1. For **Azure AD roller kan tildeles til gruppen**, skal du vælge **Nej**.
1. Vælg en foruddefineret **medlemskabstype (påkrævet).**.
1. Tilføj gruppeejere og -medlemmer eller en [dynamisk forespørgsel](/azure/active-directory/enterprise-users/groups-dynamic-membership) , hvis du bruger dynamisk brugermedlemskab.
1. Vælg **Opret**. Din gruppe er oprettet og klar til, at du kan tilføje medlemmer.

## <a name="add-an-organization"></a>Tilføj en organisation

Hvis du vil definere samarbejdsregler med en anden organisation, skal du føje organisationen til Azure AD adgangsindstillinger på tværs af lejere. Hvis du ikke allerede har tilføjet organisationen, skal du følge denne fremgangsmåde for at tilføje den.

Sådan tilføjer du en organisation
1. I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Indstillinger for adgang på tværs af lejere (prøveversion)**.1. Vælg **Indstillinger for organisation**.
1. Vælg **Tilføj organisation**.
1. Skriv det fulde domænenavn (eller lejer-id) for organisationen i ruden **Tilføj organisation** .
1. Vælg organisationen i søgeresultaterne, og vælg derefter **Tilføj**.
1. Organisationen vises på listen **Organisationsindstillinger** . På dette tidspunkt nedarves alle adgangsindstillinger for denne organisation fra dine standardindstillinger.

## <a name="choose-who-can-be-invited-by-an-organization"></a>Vælg, hvem der kan inviteres af en organisation

Der er to muligheder for at begrænse, hvem der kan inviteres til en organisation:

- Begræns, hvem der kan inviteres som gæst. Dette forhindrer, at brugerne føjes til den anden organisations Azure AD som gæst. Det forhindrer deling af filer, mapper, websteder, teams og Microsoft 365-grupper med personer, der ikke er i sikkerhedsgruppen.
- Begræns, hvem der kan føjes til en ekstern delt kanal. Dette forhindrer, at personer, der ikke er i sikkerhedsgruppen, føjes til delte kanaler i den anden organisation.

I [Azure Active Directory](https://aad.portal.azure.com) skal du vælge **Eksterne identiteter** og derefter vælge **Adgangsindstillinger på tværs af lejere (prøveversion)**.

Sådan begrænser du, hvem der kan inviteres som gæst
1. Vælg linket til udgående adgang for den organisation, du vil ændre.
1. På fanen **B2B-samarbejde** skal du vælge **Tilpas indstillinger**.
1. Under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Under **Mål** skal du vælge **Vælg eksterne brugere og grupper**.
1. Vælg linket for at tilføje brugere og grupper.
1. Søg efter og vælg den sikkerhedsgruppe, du vil bruge.
1. Vælg **Vælg**.
1. Vælg **Gem** , og luk bladet **Indstillinger for udgående adgang** .


Sådan begrænser du, hvem der kan inviteres som deltager i en delt kanal
1. Vælg linket til udgående adgang for den organisation, du vil ændre.
1. På fanen **B2B Direct Connect** skal du vælge **Tilpas indstillinger**.
1. Under **Adgangsstatus** skal du vælge **Tillad adgang**.
1. Under **Mål** skal du vælge **Vælg eksterne brugere og grupper**.
1. Vælg linket for at tilføje brugere og grupper.
1. Søg efter og vælg den sikkerhedsgruppe, du vil bruge.
1. Vælg **Vælg**.
1. Vælg **Gem** , og luk bladet **Indstillinger for udgående adgang** .

## <a name="related-topics"></a>Relaterede emner

[Oversigt over B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview)

[Konfigurer adgangsindstillinger på tværs af lejere for direkte B2B-forbindelse](/azure/active-directory/external-identities/cross-tenant-access-settings-b2b-direct-connect)

[Begræns organisationer, hvor brugerne kan have gæstekonti](limit-organizations-where-users-have-guest-accounts.md)

[Begræns gæstedeling for bestemte organisationer](limit-guest-sharing-to-specific-organization.md)