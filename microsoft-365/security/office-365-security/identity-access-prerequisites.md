---
title: Nødvendige arbejde til implementering af politikker for identitet og enhedsadgang – Microsoft 365 til | Microsoft Docs
description: I denne artikel beskrives de forudsætninger, du skal opfylde for at bruge nultillidsidentitet og politikker og konfigurationer for enhedsadgang.
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
ms.openlocfilehash: 1dbcfbff2a45cd3dfbc453f84eaa73e178174aee
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590442"
---
# <a name="prerequisite-work-for-implementing-zero-trust-identity-and-device-access-policies"></a>Påkrævet arbejde til implementering af nultillidsidentitet og politikker for enhedsadgang

I denne artikel beskrives de forudsætninger, som administratorer skal opfylde for at kunne bruge anbefalede politikker for nultillidsidentitet og enhedsadgang og for at bruge Betinget adgang. Den gennemgår også de anbefalede standarder til konfiguration af klientplatforme for at få den bedste single sign-on-oplevelse (SSO).

## <a name="prerequisites"></a>Forudsætninger

Før du bruger politikkerne Nul tillid til identitet og enhedsadgang, der anbefales, skal din organisation opfylde forudsætningerne. Kravene er forskellige for de forskellige identitets- og godkendelsesmodeller, der er angivet:

- Kun i skyen
- Hybrid med godkendelse af adgangskodehashsynkronisering (PHS)
- Hybrid med pass-through-godkendelse (PTA)
- Medlem af organisationsnetværk

Følgende tabel indeholder oplysninger om de nødvendige funktioner og deres konfiguration, der gælder for alle identitetsmodeller, undtagen hvor dette er angivet.

|Konfiguration|Undtagelser|Licensering|
|---|:---:|---|
|[Konfigurer PHS](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).  Dette skal være aktiveret for at registrere lækerede legitimationsoplysninger og handle på dem for risikobaseret betinget adgang. **Bemærk!** Dette er påkrævet, uanset om din organisation bruger organisationsnetværksgodkendelse.|Kun i skyen|Microsoft 365 E3 eller E5|
|[Aktivér problemfri enkelt logon for automatisk](/azure/active-directory/connect/active-directory-aadconnect-sso) at logge brugere på, når de er på deres organisationsenheder, der har forbindelse til organisationens netværk.|Kun i skyen og i organisationsnetværk|Microsoft 365 E3 eller E5|
|[Konfigurere navngivne placeringer](/azure/active-directory/reports-monitoring/quickstart-configure-named-locations). Azure AD Identity Protection indsamler og analyserer alle tilgængelige sessionsdata for at generere et risikoresultat. Vi anbefaler, at du angiver organisationens offentlige IP-områder for dit netværk i konfigurationen af navngivne Azure AD-placeringer. Trafik, der kommer fra disse områder, får en reduceret risiko, og trafik uden for organisationen får en højere risikoscore.||Microsoft 365 E3 eller E5|
|[Registrer alle brugere til selvbetjenings-nulstilling af adgangskode (SSPR) og multifaktorgodkendelse (MFA)](/azure/active-directory/authentication/concept-registration-mfa-sspr-converged). Vi anbefaler, at du registrerer brugere til Azure AD-multifaktorgodkendelse i forvejen. Azure AD Identity Protection bruger Multifaktorgodkendelse i Azure AD til at udføre yderligere sikkerhedskontrol. For at få den bedste logonoplevelse anbefaler vi desuden, at brugerne [installerer Microsoft Authenticator-appen](/azure/active-directory/user-help/microsoft-authenticator-app-how-to) og Microsoft Firmaportal-appen på deres enheder. Disse kan installeres fra App Store for hver platform.||Microsoft 365 E3 eller E5|
|[Aktivér automatisk enhedsregistrering af domænetilføjede Windows computere](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup). Betinget adgang sikrer, at enheder, der opretter forbindelse til apps, er domæneforbindet eller kompatible. For at understøtte dette Windows computere skal enheden være registreret med Azure AD.  I denne artikel beskrives det, hvordan du konfigurerer automatisk enhedsregistrering.|Kun i skyen|Microsoft 365 E3 eller E5|
|**Forbered dit supportteam**. Have en plan på plads for brugere, der ikke kan fuldføre MFA. Dette kan være at føje dem til en udeladelsesgruppe for politikker eller registrere nye oplysninger om MFA for dem. Før du foretager en af disse sikkerhedsfølsomme ændringer, skal du sikre dig, at den faktiske bruger foretager anmodningen. At kræve, at brugernes ledere skal hjælpe med godkendelsen, er et effektivt trin.||Microsoft 365 E3 eller E5|
|[Konfigurer tilbageførsel af adgangskode til lokal AD](/azure/active-directory/active-directory-passwords-getting-started). Tilbageførsel af adgangskode gør det muligt for Azure AD at kræve, at brugere ændrer deres lokale adgangskoder, når der registreres et kompromis med en konto med høj risiko. Du kan aktivere denne funktion ved hjælp af Azure AD Forbind på en af to måder: du kan enten  aktivere Tilbageførsel af adgangskode i skærmbilledet med valgfrie funktioner i Konfiguration af Azure AD Forbind eller aktivere det via Windows PowerShell.|Kun i skyen|Microsoft 365 E3 eller E5|
|[Konfigurer Azure AD-adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad). Azure AD-adgangskodebeskyttelse registrerer og blokerer kendte svage adgangskoder og deres varianter og kan også blokere yderligere svage ord, der er specifikke for din organisation. Standard globale lister over forbudte adgangskoder anvendes automatisk for alle brugere i en Azure AD-lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugere ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at håndhæve brugen af stærke adgangskoder.||Microsoft 365 E3 eller E5|
|[Aktivér Azure Active Directory-identitetsbeskyttelse](/azure/active-directory/identity-protection/overview-identity-protection). Azure AD Identity Protection gør det muligt at registrere potentielle sårbarheder, der påvirker organisationens identiteter, og konfigurere en automatisk afhjælpningspolitik til lav, mellem og høj logon-risiko og brugerrisici.||Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Sikkerhed|
|**Aktivér moderne** godkendelse [for Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online) og for [Skype for Business Online](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx). Moderne godkendelse er en forudsætning for brug af MFA. Moderne godkendelse er som standard aktiveret for Office 2016- og 2019-klienter, -SharePoint og OneDrive for Business.||Microsoft 365 E3 eller E5|
|[Aktivér kontinuerlig adgangsevaluering](microsoft-365-continuous-access-evaluation.md) for Azure AD. Løbende evaluering af adgang afslutter proaktivt aktive brugersessioner og gennemtvinger ændringer i lejerpolitikken næsten i realtid.||Microsoft 365 E3 eller E5|
|

## <a name="recommended-client-configurations"></a>Anbefalede klientkonfigurationer

I dette afsnit beskrives standardkonfigurationerne for platformsklienten, som vi anbefaler, at de giver brugerne den bedste SSO-oplevelse samt de tekniske forudsætninger for betinget adgang.

### <a name="windows-devices"></a>Windows enheder

Vi anbefaler Windows 11 eller Windows 10 (version 2004 eller nyere), da Azure er designet til at give den bedst mulige SSO-oplevelse for både det lokale miljø og Azure AD. Enheder, der er udstedt til arbejde eller skole, skal konfigureres til at deltage direkte i Azure AD, eller hvis organisationen bruger en lokal AD-domæneforbindelse, skal disse enheder konfigureres til automatisk og automatisk at registrere sig i [Azure AD](/azure/active-directory/active-directory-conditional-access-automatic-device-registration-setup).

Brugere kan Windows Tilføje arbejds- eller skolekonto til **BYOD-enheder**. Bemærk, at brugere af Google Chrome-browseren på Windows 11- eller Windows 10-enheder skal installere en udvidelse for at [](https://chrome.google.com/webstore/detail/windows-10-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji?utm_source=chrome-app-launcher-info-dialog) få den samme jævne logonoplevelse som Microsoft Edge brugere. Hvis din organisation har domæne-tilmeldte Windows 8- eller 8.1-enheder, kan du også installere Microsoft Workplace Join til ikke-Windows 10 computere. [Download pakken for at registrere](https://www.microsoft.com/download/details.aspx?id=53554) enhederne med Azure AD.

### <a name="ios-devices"></a>iOS-enheder

Vi anbefaler, at du installerer [Microsoft Authenticator-appen](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) på brugerenheder, før du installerer politikker for Betinget adgang eller MFA. Appen bør som minimum installeres, når brugere bliver bedt om at registrere deres enhed med Azure AD ved at tilføje en arbejds- eller skolekonto, eller når de installerer Intune-firmaportalappen for at tilmelde deres enhed til administration. Dette afhænger af den konfigurerede politik for betinget adgang.

### <a name="android-devices"></a>Android-enheder

Vi anbefaler, at brugerne [installerer Intune-firmaportal-appen](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal&hl=en) [og Microsoft Authenticator,](/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to) før politikker for Betinget adgang installeres, eller når det kræves under visse godkendelsesforsøg. Efter appinstallationen kan brugerne blive bedt om at registrere sig i Azure AD eller tilmelde deres enhed med Intune. Dette afhænger af den konfigurerede politik for betinget adgang.

Vi anbefaler også, at enheder, der ejes af organisationer, standardiseres på OEMs og versioner, der understøtter Android til arbejde eller Samsung Knox for at tillade mailkonti, administreres og beskyttes af Intune MDM-politik.

### <a name="recommended-email-clients"></a>Anbefalede mailklienter

Følgende mailklienter understøtter moderne godkendelse og Betinget adgang.

|Platform|Klient|Version/Noter|
|---|---|---|
|**Windows**|Outlook|2019, 2016, 2013 <p> [Aktivér moderne godkendelse](../../admin/security-and-compliance/enable-modern-authentication.md) <p> [Påkrævede opdateringer](https://support.office.com/article/Outlook-Updates-472c2322-23a4-4014-8f02-bbc09ad62213)|
|**iOS**|Outlook til iOS|[Seneste](https://itunes.apple.com/us/app/microsoft-outlook-email-and-calendar/id951937596?mt=8)|
|**Android**|Outlook til Android|[Seneste](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook&hl=en)|
|**macOS**|Outlook|2019 og 2016|
|**Linux**|Understøttes ikke||
|

### <a name="recommended-client-platforms-when-securing-documents"></a>Anbefalede klientplatforme ved sikring af dokumenter

Følgende klienter anbefales, når der er anvendt en politik for sikre dokumenter.

|Platform|Word/Excel/PowerPoint|OneNote|OneDrive app|SharePoint-app|[OneDrive-synkronisering klient](/onedrive/enable-conditional-access)|
|---|---|---|---|---|---|
|Windows 11 eller Windows 10|Understøttet|Understøttet|I/T|I/T|Understøttet|
|Windows 8.1|Understøttet|Understøttet|I/T|I/T|Understøttet|
|Android|Understøttet|Understøttet|Understøttet|Understøttet|I/T|
|iOS|Understøttet|Understøttet|Understøttet|Understøttet|I/T|
|macOS|Understøttet|Understøttet|I/T|I/T|Understøttes ikke|
|Linux|Understøttes ikke|Understøttes ikke|Understøttes ikke|Understøttes ikke|Understøttes ikke|
|

### <a name="microsoft-365-client-support"></a>Microsoft 365 klientsupport

Du kan finde flere oplysninger om klientsupport Microsoft 365 i følgende artikler:

- [Microsoft 365 klientapp-support – betinget adgang](../../enterprise/microsoft-365-client-support-conditional-access.md)
- [Microsoft 365-klientappsupport – Multifaktorgodkendelse](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md)

## <a name="protecting-administrator-accounts"></a>Beskyttelse af administratorkonti

For Microsoft 365 E3 eller E5 eller med separate Azure AD Premium P1- eller P2-licenser kan du kræve MFA til administratorkonti med en manuelt oprettet politik for betinget adgang. Se [Betinget adgang: Kræv MFA for administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) for at få flere oplysninger.

For versioner af Microsoft 365 eller Office 365 der ikke understøtter Betinget adgang, kan du aktivere sikkerhedsstandardindstillinger til at kræve MFA for alle konti.[](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Her er nogle flere anbefalinger:

- Brug [Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-getting-started) til at reducere antallet af faste administrative konti.
- [Brug adgangsstyring med](../../compliance/privileged-access-management-overview.md) rettigheder til at beskytte din organisation mod brud, der kan bruge eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger.
- Opret og brug separate konti, der er [tildelt Microsoft 365 administratorroller,](../../admin/add-users/about-admin-roles.md) *kun til administration*. Administratorer skal have deres egen brugerkonto til almindelig ikke-administrativ brug og kun bruge en administrativ konto, når det er nødvendigt for at udføre en opgave, der er knyttet til deres rolle eller jobfunktion.
- Følg [bedste fremgangsmåder](/azure/active-directory/admin-roles-best-practices) for sikring af privilegerede konti i Azure AD.

## <a name="next-step"></a>Næste trin

[![Trin 2: Konfigurer de fælles nultillidsidentitet og få adgang til betingede adgangspolitikker.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-2.png)](identity-access-policies.md)

[Konfigurere de fælles politikker for nultillidsidentitet og enhedsadgang](identity-access-policies.md)