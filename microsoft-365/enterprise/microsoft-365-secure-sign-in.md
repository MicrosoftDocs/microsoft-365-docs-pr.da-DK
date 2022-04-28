---
title: 'Trin 3: Beskyt dine Microsoft 365 brugerkonti'
f1.keywords:
- NOCSH
author: kelleyvice-msft
ms.author: kvice
manager: scotv
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
description: Kræv, at brugerne logger sikkert på med multifaktorgodkendelse (MFA) og andre funktioner.
ms.openlocfilehash: 4566b2c8c73ce258899e1de6ef621715092e50a5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090269"
---
# <a name="step-3-protect-your-microsoft-365-user-accounts"></a>Trin 3: Beskyt dine Microsoft 365 brugerkonti

Sådan øger du sikkerheden for brugerlogon:

- Brug Windows Hello til virksomheder
- Brug Azure Active Directory (Azure AD) Adgangskodebeskyttelse
- Brug multifaktorgodkendelse (MFA)
- Udrul konfigurationer for identitets- og enhedsadgang
- Beskyt mod kompromitterede legitimationsoplysninger med Azure AD Identity Protection

## <a name="windows-hello-for-business"></a>Windows Hello til virksomheder

Windows Hello til virksomheder i Windows 10 Enterprise erstatter adgangskoder med stærk tofaktorgodkendelse, når der logges på en Windows enhed. De to faktorer er en ny type brugerlegitimationsoplysninger, der er knyttet til en enhed og en biometrisk eller pinkode.

Du kan få flere oplysninger [under Windows Hello til virksomheder Oversigt](/windows/security/identity-protection/hello-for-business/hello-overview).


## <a name="azure-ad-password-protection"></a>Azure AD-adgangskodebeskyttelse

Azure AD Password Protection registrerer og blokerer kendte svage adgangskoder og deres varianter og kan også blokere yderligere svage ord, der er specifikke for din organisation. Standardlister over globale forbudte adgangskoder anvendes automatisk for alle brugere i en Azure AD-lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugerne ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at gennemtvinge brugen af stærke adgangskoder.

Du kan få flere oplysninger under [Konfigurer Adgangskodebeskyttelse i Azure AD](/azure/active-directory/authentication/concept-password-ban-bad).

## <a name="mfa"></a>MFA

MFA kræver, at brugerlogon er underlagt en yderligere bekræftelse ud over adgangskoden til brugerkontoen. Selvom en ondsindet bruger bestemmer en adgangskode til en brugerkonto, skal vedkommende også kunne besvare en yderligere bekræftelse, f.eks. en sms, der sendes til en smartphone, før der gives adgang.

![Den korrekte adgangskode plus en yderligere bekræftelse resulterer i et vellykket logon.](../media/empower-people-to-work-remotely/remote-workers-mfa.png)

Dit første trin i brugen af MFA er at [kræve det for alle administratorkonti](protect-your-global-administrator-accounts.md), der også kaldes privilegerede konti. Ud over dette første trin anbefaler Microsoft MFA for alle brugere.

Der er tre måder, du kan kræve, at dine brugere bruger MFA på baseret på din Microsoft 365 plan.

| Plan | Anbefaling |
|---------|---------|
|Alle Microsoft 365 planer (uden Azure AD Premium P1- eller P2-licenser)     |[Aktivér sikkerhedsstandarder i Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Sikkerhedsstandarder i Azure AD omfatter MFA for brugere og administratorer.   |
|Microsoft 365 E3 (omfatter Azure AD Premium P1-licenser)     | Brug de [almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker: <br>- [Kræv MFA for administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br>- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br> - [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)       |
|Microsoft 365 E5 (omfatter Azure AD Premium P2-licenser)     | Udnyt Azure AD Identity Protection ved at begynde at implementere Microsofts anbefalede sæt betinget adgang og relaterede politikker ved at oprette disse to politikker:<br> - [Kræv MFA, når logonrisikoen er mellem eller høj](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk) <br>- [Brugere med høj risiko skal ændre adgangskode](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk-user)       |
| | |

### <a name="security-defaults"></a>Sikkerhedsstandarder

Sikkerhedsstandarder er en ny funktion til Microsoft 365 og Office 365 betalte abonnementer eller prøveabonnementer, der er oprettet efter den 21. oktober 2019. Disse abonnementer har sikkerhedsstandarder slået til, hvilket ***kræver, at alle dine brugere bruger MFA sammen med Microsoft Authenticator-appen***.
 
Brugerne har 14 dage til at tilmelde sig MFA med Microsoft Authenticator-appen fra deres smartphones, hvilket starter fra første gang, de logger på, efter at sikkerhedsstandarder er blevet aktiveret. Efter 14 dage er gået, kan brugeren ikke logge på, før MFA-registreringen er fuldført.

Sikkerhedsstandarder sikrer, at alle organisationer har et grundlæggende sikkerhedsniveau for brugerlogon, der er aktiveret som standard. Du kan deaktivere sikkerhedsstandarder til fordel for MFA med politikker for betinget adgang eller for individuelle konti.

Du kan få flere oplysninger i [oversigten over sikkerhedsstandarder](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Politikker for betinget adgang er et sæt regler, der angiver de betingelser, som logon evalueres under, og adgang tildeles. Du kan f.eks. oprette en politik for betinget adgang, der angiver:

- Hvis brugerkontonavnet er medlem af en gruppe for brugere, der har fået tildelt rollerne Exchange, bruger, adgangskode, sikkerhed, SharePoint, **Exchange administrator**, **SharePoint administrator** eller **Global administrator**, skal du bruge MFA, før du tillader adgang.

Denne politik giver dig mulighed for at kræve MFA baseret på gruppemedlemskab i stedet for at forsøge at konfigurere individuelle brugerkonti til MFA, når de tildeles eller ikke tildeles fra disse administratorroller.

Du kan også bruge politikker for betinget adgang til mere avancerede funktioner, f.eks. kræve, at logon udføres fra en kompatibel enhed, f.eks. din bærbare computer, der kører Windows 10.

Betinget adgang kræver Azure AD Premium P1-licenser, som er inkluderet i Microsoft 365 E3 og E5.

Du kan få flere oplysninger i [oversigten over betinget adgang](/azure/active-directory/conditional-access/overview).

### <a name="using-these-methods-together"></a>Brug af disse metoder sammen

Vær opmærksom på følgende:

- Du kan ikke aktivere sikkerhedsstandarder, hvis du har aktiveret politikker for betinget adgang.
- Du kan ikke aktivere nogen politikker for betinget adgang, hvis du har aktiveret sikkerhedsstandarder.

Hvis sikkerhedsstandarder er aktiveret, bliver alle nye brugere bedt om at angive MFA-registrering og brugen af Microsoft Authenticator-appen. 

I denne tabel vises resultaterne af aktivering af MFA med sikkerhedsstandarder og politikker for betinget adgang.

| Metode | Aktiveret | Deaktiveret | Yderligere godkendelsesmetode |
|:-------|:-----|:-------|:-------|
| **Sikkerhedsstandarder**  | Politikker for betinget adgang kan ikke bruges | Kan bruge politikker for betinget adgang | Microsoft Authenticator app |
| **Politikker for betinget adgang** | Hvis nogen er aktiveret, kan du ikke aktivere sikkerhedsstandarder | Hvis alle er deaktiveret, kan du aktivere sikkerhedsstandarder  | Brugeren angiver under MFA-registrering  |
||||

## <a name="zero-trust-identity-and-device-access-configurations"></a>Konfigurationer af Nul tillid-identitet og enhedsadgang

Nul tillid indstillinger og politikker for identitets- og enhedsadgang anbefales, og deres indstillinger kombineres med politikker for betinget adgang, Intune og Azure AD Identity Protection, der bestemmer, om en given adgangsanmodning skal tildeles og under hvilke betingelser. Denne bestemmelse er baseret på brugerkontoen for logon, den enhed, der bruges, den app, som brugeren bruger til at få adgang, den placering, hvorfra adgangsanmodningen foretages, og en vurdering af risikoen for anmodningen. Denne funktion hjælper med at sikre, at kun godkendte brugere og enheder kan få adgang til dine vigtige ressourcer.

>[!Note]
>Azure AD Identity Protection kræver Azure AD Premium P2-licenser, som er inkluderet i Microsoft 365 E5.
>

Politikker for identitets- og enhedsadgang er defineret til at blive brugt på tre niveauer: 

- Grundlæggende beskyttelse er et minimumsniveau for sikkerhed for dine identiteter og enheder, der har adgang til dine apps og data.
- Følsom beskyttelse giver yderligere sikkerhed for bestemte data. Identiteter og enheder er underlagt højere niveauer af sikkerhed og enhedstilstandskrav.
- Beskyttelse af miljøer med højt regulerede eller klassificerede data er typisk til små mængder data, der er højt klassificeret, indeholder forretningshemmeligheder eller er underlagt dataregler. Identiteter og enheder er underlagt langt højere sikkerhedskrav og krav til enhedens tilstand. 

Disse niveauer og deres tilsvarende konfigurationer giver ensartede beskyttelsesniveauer på tværs af dine data, identiteter og enheder.

Microsoft anbefaler på det kraftigste, at du konfigurerer og udruller Nul tillid politikker for identitets- og enhedsadgang i din organisation, herunder specifikke indstillinger for Microsoft Teams, Exchange Online og SharePoint. Du kan få flere oplysninger [under konfigurationer af Nul tillid identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

## <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

I dette afsnit får du mere at vide om, hvordan du konfigurerer politikker, der beskytter mod kompromitterede legitimationsoplysninger, hvor en hacker bestemmer en brugers kontonavn og adgangskode for at få adgang til en organisations cloudtjenester og -data. Azure AD Identity Protection indeholder en række måder, du kan hjælpe med at forhindre, at en hacker kompromitterer en brugerkontos legitimationsoplysninger.

Med Azure AD Identity Protection kan du:

|Kapacitet|Beskrivelse|
|:---------|:---------|
| Fastlæg og løs potentielle sikkerhedsrisici i din organisations identiteter | Azure AD bruger maskinel indlæring til at registrere uregelmæssigheder og mistænkelig aktivitet, f.eks. logon og aktiviteter efter logon. Ved hjælp af disse data genererer Azure AD Identity Protection rapporter og beskeder, der hjælper dig med at evaluere problemerne og udføre handlinger.|
|Registrer mistænkelige handlinger, der er relateret til din organisations identiteter, og reager automatisk på dem|Du kan konfigurere risikobaserede politikker, der automatisk reagerer på registrerede problemer, når et angivet risikoniveau er nået. Disse politikker kan ud over andre kontrolelementer for betinget adgang, der leveres af Azure AD og Microsoft Intune, enten automatisk blokere adgang eller udføre korrigerende handlinger, herunder nulstilling af adgangskode og kræve Azure AD Multi-Factor Authentication for efterfølgende logon. |
| Undersøg mistænkelige hændelser, og løs dem med administrative handlinger | Du kan undersøge risikohændelser ved hjælp af oplysninger om sikkerhedshændelsen. Grundlæggende arbejdsprocesser er tilgængelige til at spore undersøgelser og starte afhjælpningshandlinger, f.eks. nulstilling af adgangskode. |
|||

Se [flere oplysninger om Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

Se [trinnene til aktivering af Azure AD Identity Protection](/azure/active-directory/identity-protection/howto-identity-protection-configure-risk-policies).

## <a name="admin-technical-resources-for-mfa-and-secure-sign-ins"></a>Administrator tekniske ressourcer til MFA og sikre logons

- [MFA for Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)
- [Udrul identitet for Microsoft 365](deploy-identity-solution-overview.md)
- [Azure Academy Azure AD-træningsvideoer](https://www.youtube.com/watch?v=pN8o0owHfI0&list=PL-V4YVm6AmwUFpC3rXr2i2piRQ708q_ia)
- [Konfigurer azure AD-politikken for registrering af multifaktorgodkendelse](/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy)
- [Konfigurationer af identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md)

## <a name="next-step"></a>Næste trin

![Udrul din identitetsmodel](../media/deploy-identity-solution-overview/deploy-identity-solution-identity-infrastructure.png)

Fortsæt med trin 4 for at udrulle identitetsinfrastrukturen baseret på din valgte identitetsmodel:

- [Kun cloud-id](cloud-only-identities.md)
- [Hybrididentitet](prepare-for-directory-synchronization.md)
