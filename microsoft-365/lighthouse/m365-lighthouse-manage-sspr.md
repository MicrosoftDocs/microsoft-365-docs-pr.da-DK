---
title: Administrer selvbetjent nulstilling af adgangskode i Microsoft 365 Fyrtårn
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
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du administrerer selvbetjent nulstilling af adgangskode.
ms.openlocfilehash: 0af624e93ae9321834e147f829a87f09c36dedf7
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017670"
---
# <a name="manage-self-service-password-reset-in-microsoft-365-lighthouse"></a>Administrer selvbetjent nulstilling af adgangskode i Microsoft 365 Fyrtårn

Microsoft 365 Lighthouse gør det muligt for partnere at administrere Azure Active Directory (Azure AD) selvbetjent nulstilling af adgangskode (SSPR). SSPR giver brugerne mulighed for at ændre eller nulstille deres adgangskode uden at være involveret som administrator eller helpdesk. Hvis en brugers konto er låst, eller vedkommende glemmer sin adgangskode, kan vedkommende følge prompterne for at fjerne blokeringen af sig selv og komme tilbage på arbejde. Denne mulighed reducerer helpdeskopkald og tab af produktivitet, når en bruger ikke kan logge på sin enhed eller et program.

## <a name="before-you-begin"></a>Før du begynder

Følgende betingelser skal være opfyldt, før en lejer vises på listen:

- Kundelejer skal have en Azure AD Premium licens for hver bruger. Du kan finde flere oplysninger om, hvilke licenser der understøtter SSPR, under [Licenskrav til Azure Active Directory selvbetjent nulstilling af adgangskode](/azure/active-directory/authentication/concept-sspr-licensing).

- Kundelejer skal være aktiv i Lighthouse. Du kan få mere at vide om, hvordan du finder ud af, om en lejer er aktiv, på [siden Oversigt over Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse](m365-lighthouse-tenants-page-overview.md).

## <a name="view-sspr-tenant-status"></a>Vis status for SSPR-lejer

1. Vælg **Brugere** i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Nulstil adgangskode** .

Fanen Nulstilling af adgangskode indeholder en oversigt over de lejere, der har aktiveret SSPR via de anbefalede indstillinger, antallet af brugere, der ikke har registreret sig til SSPR, og en detaljeret opdeling efter lejer af status for SSPR-udrulningen på tværs af de organisationer, du administrerer.

## <a name="enable-sspr-for-a-tenant"></a>Aktivér SSPR for en lejer

1. Vælg **Brugere** i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Nulstil adgangskode** .

3. Vælg en lejer på listen over lejere for at åbne detaljeruden.

4. Vælg **Rediger SSPR-indstillinger i Azure Active Directory** for at gå til Azure Active Directory (Azure AD).

5. I Azure AD skal du aktivere SSPR for alle eller valgte brugere. Du kan få mere at vide under [Selvstudium: Giv brugerne mulighed for at låse deres konto op eller nulstille adgangskoder ved hjælp af Azure Active Directory selvbetjent nulstilling af adgangskode](/azure/active-directory/authentication/tutorial-enable-sspr).

## <a name="notify-users-to-register-for-sspr"></a>Giv brugerne besked om at tilmelde sig SSPR

1. Vælg **Brugere** i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Nulstil adgangskode** .

3. Vælg en lejer på listen over lejere for at åbne detaljeruden.

4. Vælg de brugere, du vil give besked om.

5. Vælg **Opret mail**.

Lighthouse åbner din standardmailklient og udfylder mailmeddelelsen med instruktioner i, hvordan du tilmelder dig SSPR. Alle de valgte brugere medtages på BCC-linjen. Hvis du foretrækker at sende mails individuelt til brugere, kan du vælge mailikonet ud for brugernavnet.

Hvis du vil bruge en anden mailkonto, kan du eksportere listen over brugere til en fil. Du kan også downloade eksempelmailskabeloner, som du kan tilpasse med din virksomhedsbranding.

## <a name="related-content"></a>Relateret indhold

[Planlæg en Azure Active Directory selvbetjent udrulning af adgangskodenulstilling](/azure/active-directory/authentication/howto-sspr-deployment) (artikel)\
[Selvstudium: Giv brugerne mulighed for at låse deres konto op eller nulstille adgangskoder ved hjælp af Azure Active Directory selvbetjent nulstilling af adgangskode](/azure/active-directory/authentication/tutorial-enable-sspr) (artikel)\
[Sådan aktiverer og konfigurerer du SSPR i Azure AD](https://www.youtube.com/watch?v=rA8TvhNcCvQ) (video)\
[Administrer multifaktorgodkendelse i Microsoft 365 Lighthouse](m365-lighthouse-manage-mfa.md) (artikel)
