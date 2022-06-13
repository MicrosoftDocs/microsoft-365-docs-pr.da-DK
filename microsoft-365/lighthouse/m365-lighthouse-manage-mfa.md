---
title: Administrer multifaktorgodkendelse i Microsoft 365 Fyrtårn
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
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du administrerer multifaktorgodkendelse.
ms.openlocfilehash: 6db13adbce775ea276352b715cf25f0da7324b87
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017714"
---
# <a name="manage-multifactor-authentication-in-microsoft-365-lighthouse"></a>Administrer multifaktorgodkendelse i Microsoft 365 Fyrtårn

Azure Active Directory (Azure AD) MFA (Multi-Factor Authentication) hjælper med at beskytte adgangen til data og programmer og giver endnu et sikkerhedslag ved hjælp af en anden form for godkendelse. Fanen Multifactor Authentication indeholder detaljerede oplysninger om status for MFA-aktivering på tværs af dine lejere. Vælg en hvilken som helst lejer på listen for at få vist flere oplysninger om den pågældende lejer, herunder hvilke politikker for betinget adgang, der kræver MFA, der allerede er konfigureret, og hvilke brugere der endnu ikke har registreret sig til MFA.

For kunder med små og mellemstore virksomheder (SMB) anbefaler Microsoft, at du aktiverer [sikkerhedsstandarder](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) som minimum. I forbindelse med mere komplekse scenarier kan du bruge [Betinget adgang](/azure/active-directory/conditional-access/overview) til at konfigurere bestemte politikker.

## <a name="before-you-begin"></a>Før du begynder

Følgende betingelser skal være opfyldt, før en lejer vises på listen:

- Kundelejer skal have en Azure AD Premium licens for hver bruger. Du kan få flere oplysninger om, hvilke licenser der understøtter MFA, under [Funktioner og licenser til Azure AD multifaktorgodkendelse](/azure/active-directory/authentication/concept-mfa-licensing).

- Kundelejer skal være aktiv i Microsoft 365 Lighthouse. Hvis du vil vide mere om, hvordan du finder ud af, om en lejer er aktiv, [skal du se oversigt over Microsoft 365 Lighthouse-lejerliste](/microsoft-365/lighthouse/m365-lighthouse-tenant-list-overview).

## <a name="enable-mfa-for-a-tenant"></a>Aktivér MFA for en lejer

1. Vælg **Brugere** i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Multifactor Authentication (Godkendelse af multifaktor** ).

3. Vælg en lejer på lejerlisten for at åbne detaljeruden.

4. Under fanen **MFA-aktivering** under **MFA med sikkerhedsstandarder** skal du vælge **Aktivér sikkerhedsstandarder**.

5. Vælg **Gem ændringer**.

Hvis du vil aktivere MFA via betinget adgang, skal du se [Selvstudium: Sikre brugerlogonhændelser med Azure AD multifaktorgodkendelse](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

## <a name="notify-users-who-arent-registered-for-mfa"></a>Giv brugere, der ikke er registreret til MFA, besked

1. Vælg **Brugere** i navigationsruden til venstre i Lighthouse.

2. Vælg fanen **Multifactor Authentication (Godkendelse af multifaktor** ).

3. Vælg en lejer på lejerlisten for at åbne detaljeruden.

4. Vælg de brugere, du vil give besked, under fanen Bruger, der **ikke er registreret til MFA** .

5. Vælg **Opret mail**.

Lighthouse åbner din standardmailklient og udfylder mailmeddelelsen med instruktioner i, hvordan du tilmelder dig MFA. Alle de valgte brugere medtages på BCC-linjen. Hvis du foretrækker at sende mails individuelt til brugere, kan du vælge mailikonet ud for brugernavnet.

Hvis du vil bruge en anden mailkonto, kan du eksportere listen over brugere til en fil. Du kan også downloade eksempelmailskabeloner, som du kan tilpasse med din virksomhedsbranding.

## <a name="next-steps"></a>Næste trin

Når MFA er aktiveret, kan du aktivere selvbetjent nulstilling af Azure Active Directory (Azure AD). Denne funktion giver brugerne mulighed for at ændre eller nulstille deres adgangskode uden involvering af administrator eller helpdesk. Du kan få flere oplysninger under [Administrer selvbetjent nulstilling af adgangskode i Microsoft 365 Lighthouse](m365-lighthouse-manage-sspr.md).

## <a name="related-content"></a>Relateret indhold

[Planlæg en Azure Active Directory udrulning af multifaktorgodkendelse](/azure/active-directory/authentication/howto-mfa-getstarted) (artikel)\
[Hvad er sikkerhedsstandarder?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) (artikel)\
[Hvad er betinget adgang?](/azure/active-directory/conditional-access/overview) (artikel)\
[Få mere at vide om, hvordan du konverterer brugere fra MFA pr. bruger til betinget adgang](/azure/active-directory/authentication/howto-mfa-getstarted#convert-users-from-per-user-mfa-to-conditional-access-based-mfa) (artikel)
