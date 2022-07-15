---
title: Få vist og administrer risikable brugere i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: ragovind
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
description: For udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du får vist og administrerer risikable brugere.
ms.openlocfilehash: b4f34ccfafa1a002a9c798924641eaeeebdb04fe
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823413"
---
# <a name="view-and-manage-risky-users-in-microsoft-365-lighthouse"></a>Få vist og administrer risikable brugere i Microsoft 365 Lighthouse

Microsoft indsamler og analyserer billioner af brugerlogonsignaler hver dag. Disse signaler bruges til at hjælpe med at skabe gode funktionsmådemønstre for brugerlogon og identificere potentielle risikable logonforsøg. Identitetsbeskyttelse i Azure Active Directory (Azure AD) bruger disse signaler til at gennemse brugerlogonforsøg og udføre handlinger, hvis der er mistænkelig aktivitet.

Microsoft 365 Lighthouse hjælper med at administrere risici, der registreres af Azure AD Identity Protection, ved at give en enkelt visning af risikable brugere på tværs af alle dine administrerede lejere. Du kan hurtigt sikre risikable brugere ved enten at nulstille deres adgangskode eller blokere dem fra at logge på deres Microsoft 365-konto. Du kan også få vist indsigt for bedre at forstå en brugers risiko og fastlægge de næste trin.

Azure AD Identitetsbeskyttelse identificerer risici af mange typer, herunder:

- Lækkede legitimationsoplysninger
- Anonym brug af IP
- Atypiske rejser
- Logger på fra inficerede enheder
- Logon fra IP-adresser med mistænkelig aktivitet
- Logon fra ukendte placeringer

## <a name="before-you-begin"></a>Før du begynder

Følgende betingelser skal være opfyldt, før brugerne kan blive vist på listen over risikable brugere:

- Kundelejer skal have en Azure AD Premium-licens for hver bruger. Du kan få flere oplysninger om, hvilke licenser der understøtter Azure AD Identity Protection, under [Hvad er identitetsbeskyttelse?](/azure/active-directory/identity-protection/overview-identity-protection)

- Kundelejer skal være aktiv i Microsoft 365 Lighthouse. Hvis du vil finde ud af, om en lejer er aktiv, skal du se [Oversigt over siden Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse](m365-lighthouse-tenant-list-overview.md).

## <a name="review-detected-risks-and-take-action"></a>Gennemse registrerede risici, og udfør handlinger

I Azure AD Identity Protection omfatter risikoregistreringer eventuelle identificerede mistænkelige handlinger, der er relateret til brugerkonti i Azure AD.

1. I venstre navigationsrude i Lighthouse skal du vælge **Brugere** > **, der er risiko for brugere**.

2. Gennemse brugerne på listen under fanen **Risikable brugere** med **risikotilstand**.

3. Vælg **Vis risikoregistreringer** for at få detaljerede oplysninger om de registrerede risici for hver bruger. Du kan få flere oplysninger om risikotyper og registrering under [Hvad er risikoen?](/azure/active-directory/identity-protection/concept-identity-protection-risks).

4. For hver bruger skal du vurdere risikoregistreringerne og vælge en af følgende handlinger efter behov:

    - Nulstil adgangskode – skift eller nulstil brugeradgangskoden.

    - Bloker logon – undgå, at nogen logger på som denne bruger.

    - Bekræft, at brugeren er kompromitteret – angiv risikotilstanden til bekræftet kompromitteret.

    - Afvis brugerrisiko – angiv risikotilstanden til afvist.

## <a name="take-action-on-multiple-user-accounts-at-once"></a>Udfør handlinger på flere brugerkonti på én gang

Sådan reagerer du på flere berørte brugere på én gang:

1. I venstre navigationsrude i Lighthouse skal du vælge **Brugere** > **, der er risiko for brugere**.

2. På fanen **Risikable brugere** skal du vælge det sæt brugere, du vil udføre en handling på.

3. Vælg en af følgende handlinger, der skal udføres:

    - Nulstil adgangskode

    - Bloker logon

    - Bekræft, at brugeren er kompromitteret

    - Afvis brugerrisiko

> [!NOTE]
> Hvis den organisation, du administrerer, har en Azure AD Premium P2-licens, anbefales det, at du aktiverer politikker for betinget adgang baseret på brugerrisiko. Du kan få flere oplysninger under [Betinget adgang: Brugerrisikobaseret betinget adgang](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user).

## <a name="related-content"></a>Relateret indhold
[Selvstudium: Brug risikoregistreringer til brugerlogon til at udløse Azure AD ændringer af multifaktorgodkendelse eller adgangskode](/azure/active-directory/authentication/tutorial-risk-based-sspr-mfa) (artikel)\
[Hvad er risiko?](/azure/active-directory/identity-protection/concept-identity-protection-risks) (artikel) \
[Afhjælpning af risici og fjernelse af blokering af brugere](/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock) (artikel)
