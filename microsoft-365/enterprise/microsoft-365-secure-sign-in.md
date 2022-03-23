---
title: 'Trin 3: Beskyt dine Microsoft 365-brugerkonti'
f1.keywords:
- NOCSH
author: kelleyvice-msft
ms.author: kvice
manager: laurawi
ms.date: 09/30/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365initiative-coredeploy
ms.custom: ''
description: Kræv, at dine brugere logger på sikkert med multifaktorgodkendelse (MFA) og andre funktioner.
ms.openlocfilehash: c144b374ecc49128e11635c034f3b4b76020eafd
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63590425"
---
# <a name="step-3-protect-your-microsoft-365-user-accounts"></a>Trin 3: Beskyt dine Microsoft 365-brugerkonti

Sådan øger du sikkerheden for bruger logins:

- Brug Windows Hello for Business
- Brug Azure Active Directory (Azure AD) Password Protection
- Brug multifaktorgodkendelse (MFA)
- Installere identitets- og enhedsadgangskonfigurationer
- Beskyt dig mod kompromis med legitimationsoplysninger med Azure AD Identity Protection

## <a name="windows-hello-for-business"></a>Windows Hello for Business

Windows Hello for Business i Windows 10 Enterprise erstatter adgangskoder med stærk tofaktorgodkendelse, når du logger på en Windows enhed. De to faktorer er en ny type brugerlegitimationsoplysninger, der er bundet til en enhed og en biometrisk eller pinkode.

Du kan finde flere oplysninger [i Windows Hello for Business Overview](/windows/security/identity-protection/hello-for-business/hello-overview).


## <a name="azure-ad-password-protection"></a>Azure AD Password Protection

Azure AD-adgangskodebeskyttelse registrerer og blokerer kendte svage adgangskoder og deres varianter og kan også blokere yderligere svage ord, der er specifikke for din organisation. Standard globale lister over forbudte adgangskoder anvendes automatisk for alle brugere i en Azure AD-lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugere ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at håndhæve brugen af stærke adgangskoder.

Du kan få mere at vide under [Konfigurer beskyttelse med adgangskode til Azure AD](/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>MFA

MFA kræver, at brugeradgangskonti er underlagt en yderligere bekræftelse ud over adgangskoden til brugerkontoen. Selvom en ondsindet bruger fastlægger en adgangskode til brugerkontoen, skal brugeren også kunne svare på en yderligere bekræftelse, f.eks. en sms, der sendes til en smartphone, før der gives adgang.

![Den korrekte adgangskode plus en yderligere bekræftelse resulterer i et vellykket logon.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

Dit første trin til at bruge MFA er at [kræve det for alle administratorkonti](protect-your-global-administrator-accounts.md), også kaldet privilegerede konti. Ud over dette første trin anbefaler Microsoft MFA Til alle brugere.

Der er tre måder, hvorpå du kan kræve, at dine brugere bruger MFA baseret på Microsoft 365 plan.

| Plan | Anbefaling |
|---------|---------|
|Alle Microsoft 365 (uden Azure AD Premium P1- eller P2-licenser)     |[Aktivér sikkerhedsstandardindstillinger i Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Sikkerhedsstandarden i Azure AD omfatter MFA for brugere og administratorer.   |
|Microsoft 365 E3 (omfatter Azure AD Premium P1-licenser)     | Brug de [almindelige politikker for Betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker: <br>- [Kræv MFA til administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (omfatter Azure AD Premium P2-licenser)     | Udnyt Azure AD Identity Protection, og begynd at implementere Microsofts anbefalede sæt af Betinget adgang og relaterede politikker ved at oprette disse to politikker:<br> - [Kræv MFA, når logonrisici er mellem eller høj](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) <br>- [Brugere med høj risiko skal ændre adgangskode](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)       |
| | |

### <a name="security-defaults"></a>Sikkerhedsstandardindstillinger

Sikkerhedsstandard er en ny funktion til abonnementer Microsoft 365 og Office 365 eller prøveabonnementer, der er oprettet efter d. 21. oktober 2019. Disse abonnementer har sikkerhedsstandard slået til, hvilket kræver, at alle dine brugere bruger ***MFA sammen med Microsoft Authenticator appen***.
 
Brugere har 14 dage til at tilmelde sig MFA med Microsoft Authenticator-appen fra deres smartphones, som begynder fra den første gang, de logger på, efter sikkerhedsstandarden er blevet aktiveret. Efter 14 dage kan brugeren ikke logge på, før MFA-registrering er fuldført.

Sikkerhedsstandarden sikrer, at alle organisationer har et grundlæggende sikkerhedsniveau for bruger login, der er aktiveret som standard. Du kan deaktivere sikkerhedsstandardindstillinger i stedet for MFA med politikker for Betinget adgang eller for individuelle konti.

Du kan finde flere oplysninger i [oversigten over sikkerhedsstandardindstillinger](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Politikker for betinget adgang er et sæt regler, der angiver de betingelser, som logon evalueres under, og hvor der tildeles adgang. Du kan f.eks. oprette en politik for Betinget adgang, der hedder:

- Hvis brugerkontonavnet er medlem af en gruppe for brugere, der er tildelt Exchange-, bruger-, adgangskode-, sikkerheds-, SharePoint-, **Exchange-administrator**-, **SharePoint-administrator**- eller **global administratorroller**, skal du kræve MFA, før du tillader adgang.

Denne politik gør det muligt at kræve MFA baseret på gruppemedlemskab i stedet for at forsøge at konfigurere individuelle brugerkonti til MFA, når de tildeles eller ikke er tildelt disse administratorroller.

Du kan også bruge politikker for betinget adgang for at få mere avancerede funktioner, f.eks. kræve at logon udføres fra en kompatibel enhed, f.eks. din bærbare computer, der kører Windows 10.

Betinget adgang kræver Azure AD Premium P1-licenser, som er inkluderet i Microsoft 365 E3 og E5.

Du kan finde flere oplysninger i [oversigten over Betinget adgang](/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>Brug af disse metoder sammen

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

## <a name="zero-trust-identity-and-device-access-configurations"></a>Konfigurationer for nultillidsidentitet og enhedsadgang

Indstillinger for nultillids- og enhedsadgang samt politikker anbefales for nødvendige funktioner og deres indstillinger kombineret med politikkerne Betinget adgang, Intune og Azure AD Identity Protection, der bestemmer, om en given anmodning om adgang skal tildeles og under hvilke betingelser. Denne bestemmelse er baseret på brugerkontoen for logon, den enhed, der bruges, den app, brugeren bruger til adgang, placeringen, hvor anmodningen om adgang er foretaget, og en vurdering af risikoen ved anmodningen. Denne funktion hjælper med at sikre, at kun godkendte brugere og enheder kan få adgang til dine vigtige ressourcer.

>[!Note]
>Azure AD Identity Protection kræver Azure AD Premium P2-licenser, som er inkluderet i Microsoft 365 E5.
>

Politikker for identitets- og enhedsadgang er defineret til at blive brugt på tre niveauer: 

- Beskyttelse af grundlinje er et minimumsniveau af sikkerhed for dine identiteter og enheder, der får adgang til dine apps og data.
- Følsom beskyttelse giver ekstra sikkerhed til bestemte data. Identiteter og enheder er underlagt højere niveauer af sikkerhed og krav til enhedstilstand.
- Beskyttelse af miljøer med meget regulerede eller klassificerede data er typisk små mængder data, der er meget klassificeret, indeholder forretningshemmeligheder eller er underlagt databestemmelser. Identiteter og enheder er underlagt meget højere niveauer af sikkerhed og krav til enhedstilstand. 

Disse niveauer og deres tilsvarende konfigurationer giver ensartede niveauer af beskyttelse på tværs af dine data, identiteter og enheder.

Microsoft anbefaler kraftigt, at du konfigurerer og udruller politikker for identitet og enhedsadgang i organisationen, herunder specifikke indstillinger for Microsoft Teams, Exchange Online og SharePoint. Du kan få mere at vide under [Konfigurationer for nultillidsidentitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

I dette afsnit kan du se, hvordan du konfigurerer politikker, der beskytter mod kompromis med legitimationsoplysninger, hvor en hacker bestemmer en brugers kontonavn og adgangskode for at få adgang til en organisations skytjenester og data. Azure AD Identity Protection indeholder en række måder, hvorpå du kan forhindre en hacker i at gå på kompromis med en brugerkontos legitimationsoplysninger.

Med Azure AD Identity Protection kan du:

|Funktion|Beskrivelse|
|:---------|:---------|
| Fastlægge og adressere potentielle sårbarheder i organisationens identiteter | Azure AD bruger maskinlæring til at registrere anomalies og mistænkelig aktivitet, f.eks. logon og aktiviteter efter logon. Ved hjælp af disse data genererer Azure AD Identity Protection rapporter og beskeder, der hjælper dig med at evaluere problemerne og gøre noget.|
|Finde mistænkelige handlinger, der er relateret til din organisations identiteter og reagere på dem automatisk|Du kan konfigurere risikobaserede politikker, der automatisk reagerer på registrerede problemer, når et angivet risikoniveau er nået. Disse politikker kan, ud over andre betingede adgangskontrolelementer, der leveres af Azure AD og Microsoft Intune, enten blokere adgangen automatisk eller foretage afhjælpende handlinger, herunder nulstilling af adgangskoder og krav om Azure AD Multi-Factor Authentication til efterfølgende logon. |
| Undersøg mistænkelige hændelser, og løs dem med administrative handlinger | Du kan undersøge risikohændelser ved hjælp af oplysninger om sikkerhedshændelsen. Grundlæggende arbejdsprocesser er tilgængelige til at spore undersøgelser og starte afhjælpningshandlinger, f.eks nulstilling af adgangskode. |
|||

Se [flere oplysninger om Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

Se trinnene [til at aktivere Azure AD Identity Protection](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies).

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>Administrator tekniske ressourcer til MFA og sikre logons

- [MFA for Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [Installér identitet for Microsoft 365](deploy-identity-solution-overview.md)
- [Kursusvideoer om Azure Academy Azure AD](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Konfigurere registreringspolitikken for Multi-Factor Authentication Azure AD](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Konfigurationer for identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="next-step"></a>Næste trin

![Installér din identitetsmodel](../media/deploy-identity-solution-overview/deploy-identity-solution-identity-infrastructure.png)

Fortsæt med trin 4 for at installere identitetsinfrastrukturen baseret på din valgte identitetsmodel:

- [Kun skyidentitet](cloud-only-identities.md)
- [Hybrididentitet](prepare-for-directory-synchronization.md)
