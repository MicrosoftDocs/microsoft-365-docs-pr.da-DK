---
title: Få vist og administrer risikabelt bruger
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365, kan du få mere at vide om, hvordan du får vist og administrerer risikabele brugere.
ms.openlocfilehash: 708fc0576c85d9b8511ac6b31ed0398fae1b20d3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704915"
---
# <a name="view-and-manage-risky-users"></a>Få vist og administrer risikabelt bruger

Microsoft indsamler og analyserer hver dag trillioner af bruger login-signaler. Disse signaler bruges til at opbygge gode adfærdsmønstre for logon og identificere potentielle risiko for forsøg på at logge på. Azure Active Directory (Azure AD) Identity Protection bruger disse signaler til at gennemse brugeres logonforsøg og handle, hvis der er mistænkelig aktivitet.

Microsoft 365 Lighthouse hjælper med at administrere risici, der registreres af Azure AD Identity Protection, ved at give en enkelt visning af risikabelde brugere på tværs af alle dine administrerede lejere. Du kan hurtigt sikre risikabelt brugere ved enten at nulstille deres adgangskode eller blokere dem fra at logge på deres Microsoft 365 konto. Du kan også få vist indsigter for bedre at forstå en brugers risiko og fastlægge de næste trin.

Azure AD Identity Protection identificerer risici af mange typer, herunder:

- Lækerede legitimationsoplysninger
- Anonym brug af IP
- Atypisk rejse
- Logge på fra enheder, der er inficeret
- Logge på fra IP-adresser med mistænkelig aktivitet
- Logge på fra ukendte placeringer

## <a name="before-you-begin"></a>Før du begynder

Følgende betingelser skal være opfyldt, før brugere kan vises på listen over risikabele brugere:

- Kundelejeren skal have en Azure AD Premium licens for hver bruger. Du kan finde flere oplysninger om, hvilke licenser der understøtter Azure AD Identity Protection, [under Hvad er identitetsbeskyttelse?](/azure/active-directory/identity-protection/overview-identity-protection)

- Kundelejeren skal være aktiv i Microsoft 365 Fyrtårn. Du kan finde ud af, om en lejer er aktiv[, Microsoft 365 oversigten over lejere i Lighthouse](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Gennemse registrerede risici og reaktion

I Azure AD Identity Protection omfatter risikoregistreringer alle identificerede mistænkelige handlinger relateret til brugerkonti i Azure AD.

1. Vælg Brugere i venstre navigationsrude i **Fyrtårn**.

2. Vælg **fanen Risikabelt bruger** .

3. Gennemse brugerne på listen med risikotilstanden **I risiko**.

4. Vælg **Vis risikoregistreringer for** at få detaljerede oplysninger om de registrerede risici for hver bruger. Du kan finde flere oplysninger om risikotyper og [registrering under Hvad er risiko?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

5. For hver bruger skal du vurdere risikoregistreringerne og vælge en af følgende handlinger efter behov:

    - Nulstil adgangskode – rediger eller nulstil brugerens adgangskode.

    - Bloker logon – undgå, at nogen logger på som denne bruger.

    - Bekræft, at brugeren er kompromitteret – sæt risikotilstanden til bekræftet kompromitteret.

    - Afvis brugerrisici – sæt risikotilstanden til afvist.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Gør noget på flere brugerkonti på én gang

Sådan kan du gøre noget for flere påvirkede brugere på én gang:

1. Vælg **det sæt af** brugere, du vil handle på, under fanen Risikabelt bruger.

2. Vælg en af følgende handlinger, du vil udføre:

    - Nulstil adgangskode

    - Bloker logon

    - Bekræft, at brugeren er kompromitteret

    - Afvis brugerrisici

> [!NOTE]
> Hvis den organisation, du administrerer, har en Azure AD Premium P2-licens, anbefales det, at du aktiverer risikobaserede politikker for betinget adgang for brugerne. Få mere at vide under [Betinget adgang: Bruger risikobaseret betinget adgang](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Relateret indhold
[Selvstudium: Brug risikoregistreringer til brugeradgang til at udløse Azure AD-multifaktorgodkendelse](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) eller ændringer af adgangskode (artikel)\
[Hvad er risiko?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (artikel) \
[Afhjælpe risici og fjerne blokeringen af brugere](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (artikel)
