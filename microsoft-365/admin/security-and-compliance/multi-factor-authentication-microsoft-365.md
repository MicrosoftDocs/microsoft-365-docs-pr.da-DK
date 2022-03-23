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
description: Multifaktorgodkendelse (MFA) bruger både en adgangskode, som skal være stærk, og en yderligere bekræftelsesmetode.
ms.openlocfilehash: 460de9426dfb249da17d5df79becaca725ee36ed
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63589457"
---
# <a name="multifactor-authentication-for-microsoft-365"></a>Multifaktorgodkendelse for Microsoft 365

Adgangskoder er den mest almindelige metode til godkendelse af et logon på en computer eller onlinetjeneste, men de er også de mest følsomme. Folk kan vælge nemme adgangskoder og bruge de samme adgangskoder til at logge på forskellige computere og tjenester med flere forskellige tjenester.

For at give et yderligere sikkerhedsniveau for logon skal du bruge multifaktorgodkendelse (MFA), som bruger både en adgangskode, der skal være stærk, og en yderligere bekræftelsesmetode, der er baseret på:

- Noget, du har med dig, som ikke nemt kan duplikere, f.eks. en smartphone.
- Noget, du entydigt og gradvist har, f.eks. dine fingeraftryk, ansigt eller anden biometrisk attribut.

Den ekstra bekræftelsesmetode anvendes ikke, før brugerens adgangskode er blevet bekræftet. Med MFA, selvom en stærk brugeradgangskode er kompromitteret, har hackeren ikke din smartphone eller dit fingeraftryk til at fuldføre logon'et.

## <a name="mfa-support-in-microsoft-365"></a>MFA-understøttelse i Microsoft 365

Som standard understøtter både Microsoft 365 og Office 365 MFA for brugerkonti, der bruger:

- En sms-besked, der sendes til en telefon, der kræver, at brugeren skriver en bekræftelseskode.
- Et telefonopkald.
- Appen Microsoft Authenticator smartphone.

I begge tilfælde bruger MFA-logonmetoden "noget, du har med dig, som ikke er nemt at duplikere"-metoden til den ekstra godkendelse. Der er flere måder, hvorpå du kan aktivere MFA for Microsoft 365 og Office 365:

- Med sikkerhedsstandardindstillinger
- Med politikker for betinget adgang
- For hver enkelt brugerkonto (anbefales ikke)

Disse måder er baseret på din Microsoft 365 plan.

|Plan|Anbefaling|Kundetype|
|---|---|---|
|Alle Microsoft 365-planer|Brug sikkerhedsstandardindstillinger, som kræver MFA for alle brugerkonti. <p> Du kan også konfigurere MFA pr. bruger på individuelle brugerkonti, men det anbefales ikke.|Små virksomheder|
|Microsoft 365 Business Premium <p> Microsoft 365 E3 <p> Azure Active Directory (Azure AD) Premium P1-licenser|Brug Betingede adgangspolitikker til at kræve MFA for brugerkonti, der er baseret på gruppemedlemskab, apps eller andre kriterier.|Små virksomheder til virksomheder|
|Microsoft 365 E5 <p> Azure AD Premium P2-licenser|Brug Azure AD Identity Protection til at kræve MFA baseret på kriterier for logonrisici.|Enterprise|
||||

### <a name="security-defaults"></a>Sikkerhedsstandardindstillinger

Sikkerhedsstandard er en ny funktion til abonnementer Microsoft 365 og Office 365 eller prøveabonnementer, der er oprettet efter d. 21. oktober 2019. Disse abonnementer har aktiveret sikkerhedsstandardindstillinger, som:

- Kræver, at alle dine brugere bruger MFA med Microsoft Authenticator app.
- Blokerer ældre godkendelse.

Brugere har 14 dage til at tilmelde sig MFA med Microsoft Authenticator-appen fra deres smartphones, som begynder fra den første gang, de logger på, efter sikkerhedsstandarden er blevet aktiveret. Efter 14 dage kan brugeren ikke logge på, før MFA-registrering er fuldført.

Sikkerhedsstandarden sikrer, at alle organisationer har et grundlæggende sikkerhedsniveau for bruger login, der er aktiveret som standard. Du kan deaktivere sikkerhedsstandardindstillinger i stedet for MFA med politikker for betinget adgang.

Du aktiverer eller deaktiverer sikkerhedsstandardindstillinger fra **ruden** Egenskaber for Azure AD i Azure-portalen.

![Billede af siden Egenskaber for mappe.](../../media/multi-factor-authentication-microsoft-365/security-defaults-mfa.png)

Du kan bruge sikkerhedsstandardindstillinger med enhver Microsoft 365 plan.

Du kan finde flere oplysninger i denne [oversigt over sikkerhedsstandardindstillinger](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults).

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Betingede access-politikker er et sæt regler, der angiver de betingelser, under hvilke logons evalueres og tillades. Du kan f.eks. oprette en politik for Betinget adgang, der hedder:

- Hvis brugerkontonavnet er medlem af en gruppe for brugere, der er tildelt Exchange, bruger-, adgangskode-, sikkerheds-, SharePoint- eller globale administratorroller, skal du kræve MFA, før du tillader adgang.

Denne politik gør det muligt at kræve MFA baseret på gruppemedlemskab i stedet for at forsøge at konfigurere individuelle brugerkonti til MFA, når de tildeles eller ikke er tildelt disse administratorroller.

Du kan også bruge politikker for betinget adgang for at få mere avancerede funktioner, f.eks. kræve MFA til bestemte apps, eller at logon udføres fra en kompatibel enhed, f.eks. din bærbare computer, der kører Windows 10.

Du kan konfigurere politikker for betinget adgang **fra** ruden Sikkerhed for Azure AD i Azure-portalen.

![Billede af menuindstillingen Betinget adgang.](../../media/multi-factor-authentication-microsoft-365/conditional-access-mfa.png)

Du kan bruge politikker for betinget adgang med:

- Microsoft 365 Business Premium
- Microsoft 365 E3 og E5
- Azure AD Premium P1- og Azure AD Premium P2-licenser

Til mindre virksomheder med Microsoft 365 Business Premium kan du nemt bruge Betinget adgang-politikker med følgende trin:

1. Opret en gruppe, der skal indeholde de brugerkonti, der kræver MFA.
2. Aktivér **politikken Kræv MFA for globale** administratorer.
3. Opret en gruppebaseret politik for Betinget adgang med disse indstillinger:
    - Opgaver > Brugere og grupper: Navnet på din gruppe fra trin 1 ovenfor.
    - Opgaver > skyapps eller -handlinger: Alle skyapps.
    - Adgangskontrolelementer > giv > adgang, > Kræv multifaktorgodkendelse.
4. Aktivér politikken.
5. Føj en brugerkonto til den gruppe, der blev oprettet i trin 1 ovenfor, og test.
6. Hvis du vil kræve MFA for yderligere brugerkonti, skal du føje dem til den gruppe, der blev oprettet i trin 1.

Denne Politik for betinget adgang gør det muligt at udrulle MFA-kravet til dine brugere i dit eget tempo.

Virksomheder skal bruge [fælles politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker:

- [Kræv MFA til administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa)
- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa)
- [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)

Få mere at vide under denne [oversigt over Betinget adgang](/azure/active-directory/conditional-access/overview).

### <a name="azure-ad-identity-protection"></a>Azure AD Identity Protection

Med Azure AD Identity Protection kan du oprette en ekstra politik for betinget adgang, der kræver MFA, når risikoen for logon [er mellem eller høj](../../security/office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk).

Du kan bruge Azure AD Identity Protection og risikobaserede politikker for betinget adgang med:

- Microsoft 365 E5
- Azure AD Premium P2-licenser

Få mere at vide under denne oversigt [over Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection).

### <a name="legacy-per-user-mfa-not-recommended"></a>Ældre MFA pr. bruger (anbefales ikke)

Du skal enten bruge sikkerhedsstandard eller Betinget adgang-politikker for at kræve MFA for logon til din brugerkonto. Men hvis et af disse ikke kan bruges, anbefaler Microsoft på det kraftigste MFA til brugerkonti, der har administratorroller, især den globale administratorrolle, til ethvert abonnement i hvilken som helst størrelse.

Du aktiverer MFA for individuelle brugerkonti fra <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**ruden Aktive**</a> brugere i Microsoft 365 Administration.

![Billede af indstillingen Multifaktorgodkendelse på siden Aktive brugere.](../../media/multi-factor-authentication-microsoft-365/per-user-mfa.png)

Næste gang brugeren logger på, bliver brugeren bedt om at tilmelde sig MFA og vælge og teste den ekstra bekræftelsesmetode, næste gang brugeren logger på.

### <a name="using-these-methods-together"></a>Brug af disse metoder sammen

Denne tabel viser resultaterne af aktivering af MFA med sikkerhedsstandard, politikker for betinget adgang og indstillinger for konti pr. brugerkonto.

|*Element*|Aktiveret|Deaktiveret|Sekundær godkendelsesmetode|
|---|---|---|---|
|**Sikkerhedsstandardindstillinger**|Betingede adgangspolitikker kan ikke bruges|Kan bruge politikker for betinget adgang|Microsoft Authenticator app|
|**Politikker for betinget adgang**|Hvis nogen er aktiveret, kan du ikke aktivere sikkerhedsstandardindstillinger|Hvis alle er deaktiveret, kan du aktivere sikkerhedsstandardindstillinger|Brugerdefineret under MFA-registrering|
|**Ældre MFA pr. bruger (anbefales ikke)**|Tilsidesætter sikkerhedsstandard og Betingede adgangspolitikker, der kræver MFA ved hvert log på|Tilsidesættes som standard af sikkerhedsindstillinger og politikker for betinget adgang|Brugerdefineret under MFA-registrering|
||||

Hvis sikkerhedsstandardindstillingerne er aktiveret, bliver alle nye brugere bedt om at registrere MFA og Microsoft Authenticator-appen ved næste logon.

## <a name="ways-to-manage-mfa-settings"></a>Måder at administrere MFA-indstillinger på

Der er to måder at administrere MFA-indstillinger på.

I Azure-portalen kan du:

- Aktivér og deaktiver sikkerhedsstandardindstillinger
- Konfigurere politikker for betinget adgang

I Microsoft 365 Administration kan du konfigurere <a href="https://go.microsoft.com/fwlink/p/?linkid=2169174" target="_blank">MFA-indstillinger</a> pr. bruger og tjeneste.

## <a name="next-steps"></a>Næste trin

[Konfigurer MFA for Microsoft 365](set-up-multi-factor-authentication.md)

## <a name="related-content"></a>Relateret indhold

[Slå multifaktorgodkendelse til](set-up-multi-factor-authentication.md) (video)\
[Slå multifaktorgodkendelse til for din telefon](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14) (video)