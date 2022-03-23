---
title: Administrer nulstilling af adgangskode via selvbetjening
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
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du administrerer nulstilling af adgangskode via selvbetjening.
ms.openlocfilehash: f9f8ef9a3c81281629c378fb4b55cd4c9a839c1d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594038"
---
# <a name="manage-self-service-password-reset"></a>Administrer nulstilling af adgangskode via selvbetjening

Microsoft 365 Lighthouse giver partnere mulighed for Azure Active Directory selvbetjening (Azure AD) for nulstilling af adgangskode (SSPR). SSPR giver brugerne mulighed for at ændre eller nulstille deres adgangskode uden administrator- eller helpdeskdeltagelse. Hvis en brugers konto er låst, eller brugeren glemmer sin adgangskode, kan brugeren følge instruktionerne for at fjerne blokeringen af sig selv og gå tilbage til arbejdet. Denne mulighed reducerer helpdeskopkald og produktivitetstab, når en bruger ikke kan logge på sin enhed eller et program.

## <a name="before-you-begin"></a>Før du begynder

Følgende betingelser skal være opfyldt, før en lejer vises på listen:

- Kundelejeren skal have en Azure AD Premium licens for hver bruger. Du kan finde flere oplysninger om, hvilke licenser der understøtter SSPR, under [Licenskrav til Azure Active Directory nulstilling af adgangskode via selvbetjening](/azure/active-directory/authentication/concept-sspr-licensing).

- Kundelejeren skal være aktiv i Lighthouse. Du kan få mere at vide om, hvordan du finder ud af, om en [lejer er aktiv, Microsoft 365 oversigten over alle fyrlejere](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>Vis SSPR-lejerstatus

1. I venstre navigationsrude i Lighthouse skal du vælge **Brugere**.

2. Vælg fanen **Nulstil** adgangskode.

Fanen Nulstilling af adgangskode indeholder en oversigt over de lejere, der har aktiveret SSPR via de anbefalede indstillinger, antallet af brugere, der ikke er registreret for SSPR, og en detaljeret opdeling efter lejer af SSPR-installationen på tværs af de organisationer, du administrerer.

## <a name="enable-sspr-for-a-tenant"></a>Aktivere SSPR for en lejer

1. Vælg Brugere i venstre navigationsrude i **Fyrtårn**.

2. Vælg fanen **Nulstil** adgangskode.

3. Vælg en lejer på listen over lejere for at åbne detaljeruden.

4. Vælg **Rediger SSPR-indstillinger i Azure Active Directory** for at gå til Azure Active Directory (Azure AD).

5. I Azure AD skal du aktivere SSPR for alle eller udvalgte brugere. Du kan få mere at vide [under Selvstudium:](/azure/active-directory/authentication/tutorial-enable-sspr) Gør det muligt for brugerne at låse deres konto op eller nulstille adgangskoder Azure Active Directory at nulstille adgangskode via selvbetjening.

## <a name="notify-users-to-register-for-sspr"></a>Giv brugerne besked om at tilmelde sig SSPR

1. Vælg Brugere i venstre navigationsrude i **Fyrtårn**.

2. Vælg fanen **Nulstil** adgangskode.

3. Vælg en lejer på listen over lejere for at åbne detaljeruden.

4. Vælg de brugere, du vil give besked.

5. Vælg **Opret mail**.

Fyrtårn åbner din standardmailklient og udfylder på forhånd mailen med instruktioner i at tilmelde dig SSPR. Alle de valgte brugere medtages på linjen BCC. Hvis du foretrækker at sende en mail til brugerne enkeltvis, kan du vælge mailikonet ud for brugernavnet.

Hvis du vil bruge en anden mailkonto, kan du eksportere listen over brugere til en fil. Du kan også hente mailskabeloner, som du kan tilpasse med virksomhedens branding.

## <a name="related-content"></a>Relateret indhold

[Planlæg en Azure Active Directory installation af selvbetjening til nulstilling af adgangskode](/azure/active-directory/authentication/howto-sspr-deployment) (artikel)\
[Selvstudium: Gør det muligt for brugerne at låse deres konto op eller nulstille adgangskoder Azure Active Directory](/azure/active-directory/authentication/tutorial-enable-sspr) brug af selvbetjening til nulstilling af adgangskode (artikel)\
[Sådan aktiveres og konfigureres SSPR i Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (video)\
[Administrer multifaktorgodkendelse](m365-lighthouse-manage-mfa.md) (artikel)
