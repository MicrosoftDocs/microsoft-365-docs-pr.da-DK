---
title: Multifaktorgodkendelse for Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 043807b2-21db-4d5c-b430-c8a6dee0e6ba
ROBOTS: NOINDEX, NOFOLLOW
description: Multifaktorgodkendelse (MFA) bruger både en adgangskode, som skal være stærk, og en yderligere kontrolmetode.
ms.openlocfilehash: f939b187fc81381dae4959fdf14280bc839dadb0
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739865"
---
# <a name="multifactor-authentication-for-microsoft-365"></a>Multifaktorgodkendelse for Microsoft 365

Adgangskoder er den mest almindelige metode til godkendelse af et logon til en computer eller onlinetjeneste, men de er også de mest sårbare. Folk kan vælge nemme adgangskoder og bruge de samme adgangskoder til flere logons på forskellige computere og tjenester.

Hvis du vil give et ekstra sikkerhedsniveau for logon, skal du bruge multifaktorgodkendelse (MFA), som bruger både en adgangskode, som skal være stærk, og en yderligere kontrolmetode, der er baseret på:

- Noget, du har med dig, der ikke let duplikeres, f.eks. en smartphone.
- Noget, du unikt og biologisk har, f.eks. dine fingeraftryk, dit ansigt eller andre biometriske egenskaber.

Den ekstra bekræftelsesmetode anvendes først, når brugerens adgangskode er blevet bekræftet. Med MFA har hackeren ikke din smartphone eller dit fingeraftryk til at fuldføre logon, selvom en stærk brugeradgangskode kompromitteres.

## <a name="mfa-support-in-microsoft-365"></a>MFA-understøttelse i Microsoft 365

Som standard understøtter både Microsoft 365 og Office 365 MFA for brugerkonti ved hjælp af:

- En sms, der sendes til en telefon, som kræver, at brugeren skriver en bekræftelseskode.
- Et telefonopkald.
- Den Microsoft Authenticator smartphone-app.

I begge tilfælde bruger MFA-logon metoden "noget, du har med dig, der ikke let duplikeres" til den ekstra bekræftelse. Du kan aktivere MFA på flere måder for Microsoft 365 og Office 365:

- Med sikkerhedsstandarder
- Med politikker for betinget adgang
- For hver enkelt brugerkonto (anbefales ikke)

Disse måder er baseret på din Microsoft 365 plan.

|Plan|Anbefaling|Kundetype|
|---|---|---|
|Alle Microsoft 365 planer|Brug sikkerhedsstandarder, som kræver MFA for alle brugerkonti. <p> Du kan også konfigurere MFA pr. bruger for individuelle brugerkonti, men det anbefales ikke.|Mindre virksomheder|
|Microsoft 365 Business Premium <p> Microsoft 365 E3 <p> Azure Active Directory (Azure AD) Premium P1-licenser|Brug [sikkerhedsstandarder eller politikker for betinget adgang](/microsoft-365/business-premium/m365bp-conditional-access) til at kræve MFA for brugerkonti, der er baseret på gruppemedlemskab, apps eller andre kriterier.|Små virksomheder til virksomheder|
|Microsoft 365 E5 <p> Azure AD Premium P2-licenser|Brug Azure AD Identity Protection til at kræve MFA baseret på kriterier for logonrisiko.|Enterprise|
||||

### <a name="security-defaults"></a>Sikkerhedsstandarder

Sikkerhedsstandarder er en ny funktion til Microsoft 365 og Office 365 betalte abonnementer eller prøveabonnementer, der er oprettet efter den 21. oktober 2019. Disse abonnementer har sikkerhedsstandarder slået til, som:

- Kræver, at alle dine brugere bruger MFA sammen med Microsoft Authenticator-appen.
- Blokerer ældre godkendelse.

Brugerne har 14 dage til at tilmelde sig MFA med Microsoft Authenticator-appen fra deres smartphones, hvilket starter fra første gang, de logger på, efter at sikkerhedsstandarder er blevet aktiveret. Efter 14 dage er gået, kan brugeren ikke logge på, før MFA-registreringen er fuldført.

Sikkerhedsstandarder sikrer, at alle organisationer har et grundlæggende sikkerhedsniveau for brugerlogon, der er aktiveret som standard. Du kan deaktivere sikkerhedsstandarder til fordel for MFA med politikker for betinget adgang.

Du aktiverer eller deaktiverer sikkerhedsstandarder i ruden **Egenskaber** for Azure AD i Azure Portal.

![Billede af siden Med mappeegenskaber.](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Du kan bruge sikkerhedsstandarder sammen med en hvilken som helst Microsoft 365 plan.

Du kan få flere oplysninger i denne [oversigt over sikkerhedsstandarder](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Politikker for betinget adgang er et sæt regler, der angiver de betingelser, under hvilke logon evalueres og tillades. Du kan f.eks. oprette en politik for betinget adgang, der angiver:

- Hvis brugerkontonavnet er medlem af en gruppe for brugere, der har fået tildelt rollerne Exchange, bruger, adgangskode, sikkerhed, SharePoint eller global administrator, skal du bruge MFA, før du tillader adgang.

Denne politik giver dig mulighed for at kræve MFA baseret på gruppemedlemskab i stedet for at forsøge at konfigurere individuelle brugerkonti til MFA, når de er tildelt eller ikke er tildelt fra disse administratorroller.

Du kan også bruge politikker for betinget adgang til mere avancerede funktioner, f.eks. kræve MFA for bestemte apps, eller at logon udføres fra en kompatibel enhed, f.eks. din bærbare computer, der kører Windows 10.

Du kan konfigurere politikker for betinget adgang fra ruden **Sikkerhed** for Azure AD i Azure Portal.

![Billede af menuindstillingen Betinget adgang.](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Du kan bruge politikker for betinget adgang med:

- Microsoft 365 Business Premium
- Microsoft 365 E3 og E5
- Azure AD Premium P1- og Azure AD Premium P2-licenser

For små virksomheder med Microsoft 365 Business Premium kan du nemt bruge politikker for betinget adgang ved hjælp af følgende trin:

1. Opret en gruppe, der indeholder de brugerkonti, der kræver MFA.
2. Aktivér politikken **Kræv MFA for globale administratorer** .
3. Opret en gruppebaseret politik for betinget adgang med disse indstillinger:
    - Tildelinger > brugere og grupper: Navnet på din gruppe fra trin 1 ovenfor.
    - Tildelinger > Cloud-apps eller -handlinger: Alle cloudapps.
    - Adgangskontrolelementer > Giv > Tildel adgang > Kræver multifaktorgodkendelse.
4. Aktivér politikken.
5. Føj en brugerkonto til den gruppe, der er oprettet i trin 1 ovenfor, og test.
6. Hvis du vil kræve MFA for yderligere brugerkonti, skal du føje dem til den gruppe, der blev oprettet i trin 1.

Denne politik for betinget adgang giver dig mulighed for at udrulle MFA-kravet til dine brugere i dit eget tempo.

Virksomheder skal bruge [almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker:

- [Kræv MFA for administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Du kan få flere oplysninger i denne [oversigt over betinget adgang](/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

Med Azure AD identitetsbeskyttelse kan du oprette en yderligere politik for betinget adgang for at [kræve MFA, når logonrisikoen er mellem eller høj](../../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk).

Du kan bruge Azure AD identitetsbeskyttelse og risikobaserede politikker for betinget adgang med:

- Microsoft 365 E5
- Azure AD Premium P2-licenser

Du kan få flere oplysninger i denne [oversigt over Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

### <a name="legacy-per-user-mfa-not-recommended"></a>Ældre MFA pr. bruger (anbefales ikke)

Du skal bruge enten sikkerhedsstandarder eller politikker for betinget adgang for at kræve MFA for logon til din brugerkonto. Men hvis en af disse ikke kan bruges, anbefaler Microsoft på det kraftigste MFA for brugerkonti, der har administratorroller, især den globale administratorrolle, for alle størrelsesabonnementer.

Du aktiverer MFA for individuelle brugerkonti fra ruden <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Aktive brugere**</a> i Microsoft 365 Administration.

![Billede af indstillingen Multifaktorgodkendelse på siden Aktive brugere.](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Når brugeren er blevet aktiveret, bliver vedkommende bedt om at tilmelde sig MFA, næste gang vedkommende logger på, og om at vælge og teste den ekstra bekræftelsesmetode.

### <a name="using-these-methods-together"></a>Brug af disse metoder sammen

I denne tabel vises resultaterne af aktivering af MFA med sikkerhedsstandarder, politikker for betinget adgang og kontoindstillinger pr. brugerkonto.

|*Element*|Aktiveret|Deaktiveret|Sekundær godkendelsesmetode|
|---|---|---|---|
|**Sikkerhedsstandarder**|Politikker for betinget adgang kan ikke bruges|Kan bruge politikker for betinget adgang|Microsoft Authenticator app|
|**Politikker for betinget adgang**|Hvis nogen er aktiveret, kan du ikke aktivere sikkerhedsstandarder|Hvis alle er deaktiveret, kan du aktivere sikkerhedsstandarder|Brugerdefineret under MFA-registrering|
|**Ældre MFA pr. bruger (anbefales ikke)**|Tilsidesætter sikkerhedsstandarder og politikker for betinget adgang, der kræver MFA ved hvert logon|Tilsidesat af sikkerhedsstandarder og politikker for betinget adgang|Brugerdefineret under MFA-registrering|
||||

Hvis sikkerhedsstandarder er aktiveret, bliver alle nye brugere bedt om at angive MFA-registrering og brugen af Microsoft Authenticator-appen ved næste logon.

## <a name="ways-to-manage-mfa-settings"></a>Måder at administrere MFA-indstillinger på

Der er to måder at administrere MFA-indstillinger på.

I Azure Portal kan du:

- Aktivér og deaktiver sikkerhedsstandarder
- Konfigurer politikker for betinget adgang

I Microsoft 365 Administration kan du konfigurere <a href="https://go.microsoft.com/fwlink/p/?linkid=2169174" target="_blank">MFA-indstillinger</a> pr. bruger og tjeneste.

## <a name="next-steps"></a>Næste trin

[Konfigurer MFA for Microsoft 365](set-up-multi-factor-authentication.md)

## <a name="related-content"></a>Relateret indhold

[Aktivér multifaktorgodkendelse](set-up-multi-factor-authentication.md) (video)\
[Slå multifaktorgodkendelse til for din telefon](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (video)