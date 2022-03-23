---
title: Trin 1. Øg sikkerheden for hybridmedarbejdere med MFA
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Kræv, at dine hybridmedarbejdere logger på med Multi-Factor Authentication (MFA).
ms.openlocfilehash: 3bccf8b3ab6bc57417c6b9beafa35c8c7230f20f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588647"
---
# <a name="step-1-increase-sign-in-security-for-hybrid-workers-with-mfa"></a>Trin 1. Øg sikkerheden for hybridmedarbejdere med MFA

Brug multifaktorgodkendelse (MFA) for at øge sikkerheden for dine hybridmedarbejdere. MFA kræver, at brugeradgangskonti er underlagt en yderligere bekræftelse ud over adgangskoden til brugerkontoen. Selvom en ondsindet bruger fastlægger en adgangskode til brugerkontoen, skal brugeren også kunne svare på en yderligere bekræftelse, f.eks. en sms, der sendes til en smartphone, før der gives adgang.

![Den korrekte adgangskode plus en yderligere bekræftelse resulterer i et vellykket logon.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

For alle brugere, herunder hybridmedarbejdere og især administratorer, anbefaler Microsoft kraftigt MFA.

Der er tre måder, hvorpå du kan kræve, at dine brugere bruger MFA baseret på Microsoft 365 plan.

|Plan  |Anbefaling  |
|---------|---------|
|Alle Microsoft 365 (uden Azure AD Premium P1- eller P2-licenser)     |[Aktivér standardindstillinger for sikkerhed i Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Sikkerhedsstandarden i Azure AD omfatter MFA for brugere og administratorer.   |
|Microsoft 365 E3 (omfatter Azure AD Premium P1-licenser)     | Brug [almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker: <br>- [Kræv MFA til administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (omfatter Azure AD Premium P2-licenser)     | Udnyt Azure AD Identity Protection, og begynd at implementere Microsofts anbefalede sæt [betinget adgang](../security/office-365-security/identity-access-policies.md) og relaterede politikker ved at oprette disse politikker:<br> - [Kræv MFA, når logonrisici er mellem eller høj](../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br>- [Blokere klienter, der ikke understøtter moderne godkendelse](../security/office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br>- [Brugere med høj risiko skal ændre adgangskode](../security/office-365-security/identity-access-policies.md#high-risk-users-must-change-password)       |
| | |

## <a name="security-defaults"></a>Sikkerhedsstandardindstillinger

Sikkerhedsstandard er en ny funktion til abonnementer Microsoft 365 og Office 365 eller prøveabonnementer, der er oprettet efter d. 21. oktober 2019. Disse abonnementer har sikkerhedsstandard slået til, hvilket kræver, at alle dine brugere bruger ***MFA sammen med Microsoft Authenticator appen***.
 
Brugere har 14 dage til at tilmelde sig MFA med Microsoft Authenticator-appen fra deres smartphones, som begynder fra den første gang, de logger på, efter sikkerhedsstandarden er blevet aktiveret. Efter 14 dage kan brugeren ikke logge på, før MFA-registrering er fuldført.

Sikkerhedsstandarden sikrer, at alle organisationer har et grundlæggende sikkerhedsniveau for bruger login, der er aktiveret som standard. Du kan deaktivere sikkerhedsstandardindstillinger i stedet for MFA med politikker for Betinget adgang eller for individuelle konti.

Du kan finde flere oplysninger i denne [oversigt over sikkerhedsstandardindstillinger](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

## <a name="conditional-access-policies"></a>Politikker for betinget adgang

Betingede access-politikker er et sæt regler, der angiver de betingelser, under hvilke logons evalueres og tillades. Du kan f.eks. oprette en politik for Betinget adgang, der hedder:

- Hvis brugerkontonavnet er medlem af en gruppe for brugere, der er tildelt Exchange, bruger-, adgangskode-, sikkerheds-, SharePoint- eller globale administratorroller, skal du kræve MFA, før du tillader adgang.

Denne politik gør det muligt at kræve MFA baseret på gruppemedlemskab i stedet for at forsøge at konfigurere individuelle brugerkonti til MFA, når de tildeles eller ikke er tildelt disse administratorroller.

Du kan også bruge politikker for betinget adgang for at få mere avancerede funktioner, f.eks. kræve at logon udføres fra en kompatibel enhed, f.eks. din bærbare computer, der kører Windows 11 eller 10.

Betinget adgang kræver Azure AD Premium P1-licenser, som er inkluderet i Microsoft 365 E3 og E5.

Få mere at vide under denne [oversigt over Betinget adgang](/azure/active-directory/conditional-access/overview).

## <a name="azure-ad-identity-protection-support"></a>Understøttelse af Azure AD Identity Protection

Med Azure AD Identity Protection kan du oprette en ekstra politik for betinget adgang, der hedder:

- Hvis risikoen ved at logge på er mellem eller høj, skal du kræve MFA.

Azure AD Identity Protection kræver Azure AD Premium P2-licenser, som er inkluderet i Microsoft 365 E5.

Du kan finde flere oplysninger [under Risikobaseret betinget adgang](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk#require-mfa-medium-or-high-sign-in-risk-users).

Med Azure AD Identity Protection kan du også oprette en politik, der kræver, at brugerne skal tilmelde sig MFA. Få mere at vide under [Konfigurer registreringspolitikken for Azure AD Multi-Factor Authentication](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)


## <a name="using-these-methods-together"></a>Brug af disse metoder sammen

Vær opmærksom på følgende:

- Du kan ikke aktivere sikkerhedsstandardindstillinger, hvis du har aktiveret Betingede adgangspolitikker.
- Du kan ikke aktivere Betingede adgangspolitikker, hvis du har aktiveret sikkerhedsstandardindstillinger.

Hvis sikkerhedsstandardindstillingerne er aktiveret, bliver alle nye brugere bedt om at registrere MFA og Microsoft Authenticator appen. 

Denne tabel viser resultaterne af aktivering af MFA med sikkerhedsstandard og politikker for betinget adgang.

| Metode | Aktiveret | Deaktiveret | Yderligere godkendelsesmetode |
|:-------|:-----|:-------|:-------|
| **Sikkerhedsstandardindstillinger**  | Betingede adgangspolitikker kan ikke bruges | Kan bruge politikker for betinget adgang | Microsoft Authenticator app |
| **Politikker for betinget adgang** | Hvis nogen er aktiveret, kan du ikke aktivere sikkerhedsstandardindstillinger | Hvis alle er deaktiveret, kan du aktivere sikkerhedsstandardindstillinger  | Brugeren angiver under MFA-registrering  |
||||

## <a name="let-your-users-reset-their-own-passwords"></a>Lad brugerne nulstille deres egne adgangskoder

Self-Service SSPR (Password Reset) giver brugerne mulighed for at nulstille deres egne adgangskoder uden at påvirke it-medarbejdere. Brugere kan hurtigt nulstille deres adgangskoder når som helst og fra et hvilket som helst sted. Du kan få mere at vide [under Planlæg en installation af selvbetjening for Azure AD til nulstilling af adgangskode](/azure/active-directory/authentication/howto-sspr-deployment).

## <a name="sign-in-to-saas-apps-with-azure-ad"></a>Log på SaaS-apps med Azure AD

Ud over at give skygodkendelse for brugere kan Azure AD også være din centrale måde at sikre alle dine apps, uanset om de er i det lokale miljø, i Microsofts sky eller i en anden sky. Ved [at integrere dine apps i Azure AD](/azure/active-directory/manage-apps/plan-an-application-integration) kan du gøre det nemt for hybridmedarbejdere at finde de programmer, de skal bruge, og logge på dem sikkert.

## <a name="admin-technical-resources-for-mfa-and-identity"></a>Tekniske ressourcer for MFA og identitet for administratorer

- [De fem mest populære måder, dit Azure AD kan hjælpe dig med at aktivere fjernarbejde på](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/top-5-ways-your-azure-ad-can-help-you-enable-remote-work/ba-p/1144691)
- [Identitetsinfrastruktur til Microsoft 365](../enterprise/deploy-identity-solution-overview.md)
- [Kursusvideoer om Azure Academy Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)

## <a name="results-of-step-1"></a>Resultater af trin 1

Efter udrulning af MFA gør dine brugere følgende:

- Er påkrævet for at bruge MFA til logon.
- Har fuldført MFA-registreringsprocessen og bruger MFA for alle logons.
- Kan bruge SSPR til at nulstille deres egne adgangskoder.

## <a name="next-step"></a>Næste trin

[![Trin 2: Giv fjernadgang til apps og tjenester i det lokale miljø.](../media/empower-people-to-work-remotely/remote-workers-step-grid-2.png)](empower-people-to-work-remotely-remote-access.md)

Fortsæt med [trin 2](empower-people-to-work-remotely-remote-access.md) for at give fjernadgang til apps og tjenester i det lokale miljø.