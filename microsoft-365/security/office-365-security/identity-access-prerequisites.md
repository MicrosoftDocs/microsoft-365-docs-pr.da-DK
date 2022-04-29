---
title: Forudsætningsarbejde for implementering af politikker for identitets- og enhedsadgang – Microsoft 365 for virksomheds-| Microsoft Docs
description: I denne artikel beskrives de forudsætninger, du skal opfylde for at bruge Nul tillid politikker og konfigurationer for identitets- og enhedsadgang.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 2c2902e7e61428d9c60423f83ed637d6d22a0570
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131234"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>Forudsætning for arbejde med implementering af Nul tillid politikker for identitets- og enhedsadgang

I denne artikel beskrives de forudsætninger, administratorer skal opfylde for at bruge anbefalede Nul tillid politikker for identitets- og enhedsadgang og for at bruge Betinget adgang. Den beskriver også de anbefalede standarder for konfiguration af klientplatforme til den bedste SSO-oplevelse (Single Sign-on).

## <a name="prerequisites"></a>Forudsætninger

Før du bruger de politikker for Nul tillid identitet og enhedsadgang, der anbefales, skal din organisation opfylde forudsætningerne. Kravene er forskellige for de forskellige identitets- og godkendelsesmodeller, der er angivet:

- Kun i skyen
- Hybrid med PHS-godkendelse (Password Hash Sync)
- Hybrid med pass-through-godkendelse (PTA)
- Sammenkædet

Følgende tabel indeholder oplysninger om de nødvendige funktioner og deres konfiguration, der gælder for alle identitetsmodeller, undtagen de angivne.

|Konfiguration|Undtagelser|Licensering|
|---|:---:|---|
|[Konfigurer PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Dette skal være aktiveret til at registrere lækkede legitimationsoplysninger og reagere på dem for risikobaseret betinget adgang. **Bemærk:** Dette er påkrævet, uanset om din organisation bruger godkendelse i organisationsnetværket.|Kun i skyen|Microsoft 365 E3 eller E5|
|[Aktivér problemfri enkeltlogon](/azure/active-directory/connect/active-directory-aadconnect-sso) for automatisk at logge brugere på, når de er på deres organisationsenheder, der har forbindelse til organisationens netværk.|Kun cloudmiljøet og organisationsnetværket|Microsoft 365 E3 eller E5|
|[Konfigurer navngivne placeringer](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Identity Protection indsamler og analyserer alle tilgængelige sessionsdata for at generere en risikoscore. Vi anbefaler, at du angiver organisationens offentlige IP-intervaller for dit netværk i Azure AD navngivne placeringskonfiguration. Trafik, der kommer fra disse områder, får en reduceret risikoscore, og trafik uden for organisationsmiljøet får en højere risikoscore.||Microsoft 365 E3 eller E5|
|[Registrer alle brugere til selvbetjent nulstilling af adgangskode (SSPR) og multifactor-godkendelse (MFA).](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged) Vi anbefaler, at du registrerer brugere til Azure AD multifaktorgodkendelse på forhånd. Azure AD Identity Protection bruger Azure AD Multifactor Authentication til at udføre yderligere sikkerhedsgodkendelse. Derudover anbefaler vi, at brugerne installerer [appen Microsoft Authenticator](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) og Microsoft Firmaportal-appen på deres enheder for at få den bedste logonoplevelse. Disse kan installeres fra appbutikken for hver platform.||Microsoft 365 E3 eller E5|
|[Aktivér automatisk enhedsregistrering af domænetilsluttede Windows computere](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). Betinget adgang sikrer, at enheder, der opretter forbindelse til apps, er domænetilsluttede eller kompatible. Hvis du vil understøtte dette på Windows computere, skal enheden være registreret i Azure AD.  I denne artikel beskrives det, hvordan du konfigurerer automatisk enhedsregistrering.|Kun i skyen|Microsoft 365 E3 eller E5|
|**Forbered dit supportteam**. Have en plan på plads for brugere, der ikke kan fuldføre MFA. Dette kan være at føje dem til en politikudeladelsesgruppe eller registrere nye MFA-oplysninger for dem. Før du foretager en af disse sikkerhedsfølsomme ændringer, skal du sikre dig, at den faktiske bruger foretager anmodningen. Det er et effektivt trin at kræve, at brugernes ledere hjælper med godkendelsen.||Microsoft 365 E3 eller E5|
|[Konfigurer tilbageførsel af adgangskode til AD i det lokale miljø](/azure/active-directory/active-directory-passwords-getting-started). Tilbageførsel af adgangskode gør det muligt for Azure AD at kræve, at brugerne ændrer deres adgangskoder i det lokale miljø, når der registreres en kompromitteret konto med høj risiko. Du kan aktivere denne funktion ved hjælp af Azure AD Forbind på to måder: Du kan enten aktivere **Tilbageskrivning af adgangskode** på skærmbilledet med valgfrie funktioner i Azure AD Forbind installation eller aktivere den via Windows PowerShell.|Kun i skyen|Microsoft 365 E3 eller E5|
|[Konfigurer Azure AD adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad). Azure AD Adgangskodebeskyttelse registrerer og blokerer kendte svage adgangskoder og deres varianter og kan også blokere yderligere svage ord, der er specifikke for din organisation. Standardlister over globale forbudte adgangskoder anvendes automatisk på alle brugere i en Azure AD lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugerne ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at gennemtvinge brugen af stærke adgangskoder.||Microsoft 365 E3 eller E5|
|[Aktivér Azure Active Directory identitetsbeskyttelse](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Identitetsbeskyttelse giver dig mulighed for at registrere potentielle sikkerhedsrisici, der påvirker din organisations identiteter, og konfigurere en automatiseret afhjælpningspolitik til lav, mellem og høj logonrisiko og brugerrisiko.||Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Security|
|**Aktivér moderne godkendelse** for [Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) og for [Skype for Business Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). Moderne godkendelse er en forudsætning for at bruge MFA. Moderne godkendelse er som standard aktiveret for klienter Office 2016 og 2019, SharePoint og OneDrive for Business.||Microsoft 365 E3 eller E5|
|[Aktivér løbende evaluering af adgang](microsoft-365-continuous-access-evaluation.md) for Azure AD. Kontinuerlig adgangsevaluering afslutter proaktivt aktive brugersessioner og gennemtvinger ændringer af lejerpolitik i næsten realtid.||Microsoft 365 E3 eller E5|

## <a name="recommended-client-configurations"></a>Anbefalede klientkonfigurationer

I dette afsnit beskrives de standardkonfigurationer for platformklienter, som vi anbefaler, for at give dine brugere den bedste SSO-oplevelse samt de tekniske forudsætninger for betinget adgang.

### <a name="windows-devices"></a>Windows enheder

Vi anbefaler Windows 11 eller Windows 10 (version 2004 eller nyere), da Azure er designet til at give den mest problemfri SSO-oplevelse i både det lokale miljø og Azure AD. Arbejds- eller skoleudstedte enheder skal konfigureres til at tilmelde sig Azure AD direkte, eller hvis organisationen bruger AD-domænejoin i det lokale miljø, skal disse enheder [konfigureres til automatisk og uovervåget at registrere med Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

For BYOD-Windows enheder kan brugerne bruge **Tilføj arbejds- eller skolekonto**. Bemærk, at brugere af Google Chrome-browseren på Windows 11 eller Windows 10 enheder skal [installere en udvidelse](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) for at få den samme problemfri logonoplevelse som Microsoft Edge brugere. Hvis din organisation har domænetilsluttede Windows 8 eller 8.1-enheder, kan du også installere Microsoft Workplace Join til computere, der ikke er Windows 10. [Download pakken for at registrere](https://www.microsoft.com/download/details.aspx?id=53554) enhederne med Azure AD.

### <a name="ios-devices"></a>iOS-enheder

Vi anbefaler, at [du installerer appen Microsoft Authenticator](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) på brugerenheder, før du installerer betinget adgang eller MFA-politikker. Appen skal som minimum installeres, når brugerne bliver bedt om at registrere deres enhed med Azure AD ved at tilføje en arbejds- eller skolekonto, eller når de installerer appen Intune firmaportal for at tilmelde deres enhed til administration. Dette afhænger af den konfigurerede politik for betinget adgang.

### <a name="android-devices"></a>Android-enheder

Vi anbefaler, at brugerne installerer [appen Intune-firmaportal](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) og [Microsoft Authenticator,](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) før politikker for betinget adgang installeres, eller når det kræves under visse godkendelsesforsøg. Efter appinstallationen bliver brugerne muligvis bedt om at tilmelde sig Azure AD eller tilmelde deres enhed med Intune. Dette afhænger af den konfigurerede politik for betinget adgang.

Vi anbefaler også, at organisationsejede enheder standardiseres på OEM'er og versioner, der understøtter Android til arbejde eller Samsung Knox for at tillade mailkonti, administreres og beskyttes af Intune MDM-politik.

### <a name="recommended-email-clients"></a>Anbefalede mailklienter

Følgende mailklienter understøtter moderne godkendelse og betinget adgang.

|Platform|Klient|Version/noter|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Aktivér moderne godkendelse](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Påkrævede opdateringer](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**Ios**|Outlook til iOS|[Seneste](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook til Android|[Seneste](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**Macos**|Outlook|2019 og 2016|
|**Linux**|Understøttes ikke||

### <a name="recommended-client-platforms-when-securing-documents"></a>Anbefalede klientplatforme ved sikring af dokumenter

Følgende klienter anbefales, når der er anvendt en politik for sikre dokumenter.

|Platform|Word/Excel/PowerPoint|OneNote|OneDrive app|SharePoint app|[OneDrive-synkronisering klient](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 eller Windows 10|Understøttes|Understøttes|NIELSEN|NIELSEN|Understøttes|
|Windows 8.1|Understøttes|Understøttes|NIELSEN|NIELSEN|Understøttes|
|Android|Understøttes|Understøttes|Understøttes|Understøttes|NIELSEN|
|Ios|Understøttes|Understøttes|Understøttes|Understøttes|NIELSEN|
|Macos|Understøttes|Understøttes|NIELSEN|NIELSEN|Understøttes ikke|
|Linux|Understøttes ikke|Understøttes ikke|Understøttes ikke|Understøttes ikke|Understøttes ikke|

### <a name="microsoft-365-client-support"></a>Microsoft 365 klientsupport

Du kan få flere oplysninger om klientsupport i Microsoft 365 i følgende artikler:

- [understøttelse af Microsoft 365 klientapp – betinget adgang](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [understøttelse af Microsoft 365 klientapp – multifaktorgodkendelse](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Beskyttelse af administratorkonti

For Microsoft 365 E3 eller E5 eller med separate Azure AD Premium P1- eller P2-licenser kan du kræve MFA for administratorkonti med en manuelt oprettet politik for betinget adgang. Se [Betinget adgang: Kræv MFA for administratorer for](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) at få flere oplysninger.

I forbindelse med versioner af Microsoft 365 eller Office 365, der ikke understøtter betinget adgang, kan du aktivere [sikkerhedsstandarder](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) for at kræve MFA for alle konti.

Her er nogle yderligere anbefalinger:

- Brug [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) til at reducere antallet af vedvarende administrative konti.
- [Brug privilegeret adgangsstyring](../../compliance/privileged-access-management-overview.md) til at beskytte din organisation mod brud, der kan bruge eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger.
- Opret og brug separate konti, der kun er tildelt [Microsoft 365 administratorroller](../../admin/add-users/about-admin-roles.md) *til administration*. Administratorer skal have deres egen brugerkonto til regelmæssig ikke-administrativ brug og kun bruge en administrativ konto, når det er nødvendigt, for at fuldføre en opgave, der er knyttet til deres rolle eller jobfunktion.
- Følg [bedste praksis](/azure/active-directory/admin-roles-best-practices) for sikring af privilegerede konti i Azure AD.

## <a name="next-step"></a>Næste trin

[![Trin 2: Konfigurer de almindelige politikker for Nul tillid identitet og adgang betinget adgang.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png#lightbox)](identity-access-policies.md)

[Konfigurer de fælles politikker for Nul tillid identitet og enhedsadgang](identity-access-policies.md)
