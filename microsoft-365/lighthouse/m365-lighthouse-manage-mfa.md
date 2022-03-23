---
title: Administrer multifaktorgodkendelse
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
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du administrerer multifaktorgodkendelse.
ms.openlocfilehash: 5ab430e464fb2d20f9a911818f9fd6cb077d849e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592987"
---
# <a name="manage-multifactor-authentication"></a>Administrer multifaktorgodkendelse

Azure Active Directory (Azure AD) Multi-Factor Authentication (MFA) hjælper med at beskytte adgangen til data og programmer, hvilket giver et andet lag af sikkerhed ved hjælp af en anden form for godkendelse. Fanen Multifaktorgodkendelse indeholder detaljerede oplysninger om status for multifaktorgodkendelsesaktivering på tværs af dine lejere. Vælg en hvilken som helst lejer på listen for at få vist flere oplysninger om den pågældende lejer, herunder hvilke betingede adgangspolitikker, der kræver MFA, der allerede er konfigureret, og hvilke brugere der endnu ikke har tilmeldt sig MFA.

Til små og mellemstore virksomheder (SMB)-kunder anbefaler Microsoft [, at man](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) som minimum aktiverer sikkerhedsstandardindstillinger. Til mere komplekse scenarier kan du bruge Betinget [adgang til](/azure/active-directory/conditional-access/overview) at konfigurere bestemte politikker.

## <a name="before-you-begin"></a>Før du begynder

Følgende betingelser skal være opfyldt, før en lejer vises på listen:

- Kundelejeren skal have en Azure AD Premium licens for hver bruger. Du kan finde flere oplysninger om, hvilke licenser der understøtter [multifaktorgodkendelse, under Funktioner og licenser til Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-licensing).

- Kundelejeren skal være aktiv i Microsoft 365 Fyrtårn. Du kan få mere at vide om, hvordan du finder ud af, om en lejer [er aktiv, Microsoft 365 oversigt over lejerlisten i Lighthouse](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Aktivér MFA for en lejer

1. Vælg Brugere i venstre navigationsrude i **Fyrtårn**.

2. Vælg fanen **Multifaktorgodkendelse** .

3. Vælg en lejer på lejerlisten for at åbne detaljeruden.

4. På fanen **MFA-aktivering under** **MFA med sikkerhedsstandard skal** du vælge **Aktivér sikkerhedsstandard**.

5. Vælg **Gem ændringer**.

Hvis du vil aktivere MFA via Betinget adgang, skal du [se Selvstudium: Sikre brugerhændelser med Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>Giv besked til brugere, der ikke er registreret til MFA

1. Vælg Brugere i venstre navigationsrude i **Fyrtårn**.

2. Vælg fanen **Multifaktorgodkendelse** .

3. Vælg en lejer på lejerlisten for at åbne detaljeruden.

4. På fanen **Bruger, der ikke er registreret til MFA** skal du vælge de brugere, du vil underrette.

5. Vælg **Opret mail**.

Fyrtårn åbner din standardmailklient og udfylder mailen med instruktioner til at tilmelde dig MFA. Alle de valgte brugere medtages på linjen BCC. Hvis du foretrækker at sende en mail til brugerne enkeltvis, kan du vælge mailikonet ud for brugernavnet.

Hvis du vil bruge en anden mailkonto, kan du eksportere listen over brugere til en fil. Du kan også hente mailskabeloner, som du kan tilpasse med virksomhedens branding.

## <a name="next-steps"></a>Næste trin

Når MFA er aktiveret, kan du Azure Active Directory selvbetjeningstjenesten (Azure AD) til nulstilling af adgangskode. Denne funktion giver brugerne mulighed for at ændre eller nulstille deres adgangskode uden administrator- eller helpdeskdeltagelse. Du kan finde flere oplysninger under [Administrere nulstilling af adgangskode via selvbetjening](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>Relateret indhold

[Planlæg en Azure Active Directory installation af Multi-Factor Authentication](/azure/active-directory/authentication/howto-mfa-getstarted) (artikel)\
[Hvad er sikkerhedsstandard?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (artikel)\
[Hvad er Betinget adgang?](/azure/active-directory/conditional-access/overview) (artikel)\
[Få mere at vide om, hvordan du konverterer brugere fra MFA pr. bruger til Betinget adgang](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (artikel)
