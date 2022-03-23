---
title: Konfigurer multifaktorgodkendelse for brugere
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 8f0454b2-f51a-4d9c-bcde-2c48e41621c6
description: Få mere at vide om, hvordan du konfigurerer multifaktorgodkendelse for organisationen.
monikerRange: o365-worldwide
ms.openlocfilehash: 1279220ceb8de5c5fdb4361a258e2c2bfc1f7061
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63589380"
---
# <a name="set-up-multifactor-authentication"></a>Konfigurer multifaktorgodkendelse

Multifaktorgodkendelse betyder, at du og dine medarbejdere skal angive mere end én måde at logge på Microsoft 365 er en af de nemmeste måder at sikre din virksomhed på. Baseret på din forståelse af [multifaktorgodkendelse (MFA) og dens support i Microsoft 365](multi-factor-authentication-microsoft-365.md) er det tid til at konfigurere den og udrulle den til din organisation. 

> [!IMPORTANT]
> Hvis du har købt dit abonnement eller din prøveversion efter den 21. oktober 2019, og du bliver bedt om MFA [, når](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) du logger på, er sikkerhedsstandardindstillingerne automatisk aktiveret for dit abonnement.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="watch-turn-on-multifactor-authentication"></a>Se: Slå multifaktorgodkendelse til

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2MuO3?autoplay=false]

1. Gå til Microsoft 365 Administration på <a href="https://admin.microsoft.com/ " target="_blank">https://admin.microsoft.com</a>.
1. Vælg **Vis alle**, og vælg **Azure Active Directory Administration**.
1. Vælg **Azure Active Directory**, **Egenskaber** og **Administrer standardindstillinger for sikkerhed**.
1. Under **Aktivér standardindstillinger for sikkerhed** skal du **vælge Ja** og derefter **Gem**.

## <a name="before-you-begin"></a>Før du begynder

- Du skal være global administrator for at administrere MFA. Du kan få mere at vide [under Om administratorroller](../add-users/about-admin-roles.md).
- Hvis du har slået ældre MFA pr. bruger til, skal [du Slå ældre MFA fra pr. bruger](#turn-off-legacy-per-user-mfa).
- Hvis du har Office 2013-klienter på Windows-enheder, skal du aktivere moderne godkendelse [for Office 2013-klienter](./enable-modern-authentication.md).
- Avanceret: Hvis du har tredjepartskatalogtjenester med Active Directory Federation Services (AD FS), skal du konfigurere Azure MFA-serveren. Se [avancerede scenarier med Azure AD-multifaktorgodkendelse og VPN-tredjepartsløsninger for at](/azure/active-directory/authentication/howto-mfaserver-nps-vpn) få flere oplysninger.

### <a name="turn-off-legacy-per-user-mfa"></a>Slå ældre MFA'er pr. bruger fra

Hvis du tidligere har aktiveret MFA pr. bruger, skal du deaktivere den, før du aktiverer standardindstillinger for sikkerhed.

1. Vælg aktive Microsoft 365 Administration brugere i venstre **navigationslinje**\>.
1. På siden **Aktive brugere** skal du **vælge Multi-Factor Authentication**.
1. På siden multifaktorgodkendelse skal du vælge hver bruger og angive status for multifaktorgodkendelse til **Deaktiveret**.

## <a name="turn-security-defaults-on-or-off"></a>Slå standardindstillinger for sikkerhed til eller fra

For de fleste organisationer giver sikkerhedsstandards et godt niveau af ekstra logonsikkerhed. Du kan finde flere oplysninger [under Hvad er sikkerhedsstandard?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)

Hvis dit abonnement er nyt, er standardindstillingerne for sikkerhed måske allerede slået til for dig automatisk.

Du aktiverer eller deaktiverer **sikkerhedsstandardindstillinger fra** ruden Egenskaber for Azure Active Directory (Azure AD) i Azure-portalen.

1. Log [på Microsoft 365 Administration med](https://admin.microsoft.com) globale legitimationsoplysninger.
2. I venstre navigationslinje skal **du vælge Vis** **alle, og under** **Administration skal du Azure Active Directory**.
3. Vælg **Azure Active Directory Egenskaber** **i Azure Active Directory** \> **Administration**.
4. Nederst på siden skal du vælge **Administrer sikkerhedsstandardindstillinger**.
5. Vælg **Ja** for at aktivere sikkerhedsstandard eller **Nej for** at deaktivere sikkerhedsstandard, og vælg derefter **Gem**.

Hvis du har brugt betingede [adgangspolitikker for den](/azure/active-directory/conditional-access/concept-baseline-protection) oprindelige plan, bliver du bedt om at deaktivere dem, før du går til at bruge sikkerhedsstandardindstillinger.

1. Gå til siden [Betinget adgang – Politikker](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies).
2. Vælg hver politik for grundlinjer, der **er slået Til** , og angiv **Aktivér politik** **til Fra**.
3. Gå til [siden Azure Active Directory - egenskaber](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties).
4. Nederst på siden skal du vælge **Administrer sikkerhedsstandardindstillinger**.
5. Vælg **Ja** for at aktivere sikkerhedsstandard og **Nej for** at deaktivere sikkerhedsstandardindstillinger, og vælg derefter **Gem**.

## <a name="use-conditional-access-policies"></a>Brug Betingede adgangspolitikker

Hvis din organisation har mere detaljerede sikkerhedsbehov for logon, kan politikkerne for Betinget adgang give dig mere kontrol. Med Betinget adgang kan du oprette og definere politikker, der reagerer for at logge på-hændelser og anmode om yderligere handlinger, før en bruger får tildelt adgang til et program eller en tjeneste.

> [!IMPORTANT]
> Deaktiver både standardindstillinger for MFA pr. bruger og Sikkerhed, før du aktiverer politikker for Betinget adgang.

Betinget adgang er tilgængelig for kunder, der har købt Azure AD Premium P1, eller licenser, der omfatter dette, f.eks. Microsoft 365 Business Premium og Microsoft 365 E3. Få mere at vide under [Opret en politik for betinget adgang](/azure/active-directory/authentication/tutorial-enable-azure-mfa).

Risikobaseret betinget adgang er tilgængelig via Azure AD Premium P2-licens eller licenser, der omfatter dette, f.eks. Microsoft 365 E5. Du kan finde flere oplysninger [under risikobaseret betinget adgang](/azure/active-directory/conditional-access/howto-conditional-access-policy-risk).

Du kan finde flere oplysninger om Azure AD P1 og P2 [under Azure Active Directory priser](https://azure.microsoft.com/pricing/details/active-directory/).

### <a name="turn-on-modern-authentication-for-your-organization"></a>Slå moderne godkendelse til for din organisation

Moderne godkendelse er automatisk aktiveret for de fleste abonnementer, men hvis du har købt dit abonnement før august 2017, er det sandsynligt, at du skal aktivere moderne godkendelse for at få funktioner som multifaktorgodkendelse til at fungere i Windows-klienter som Outlook.


1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">indstillinger Microsoft 365 Administration</a> navigation i venstre **navigationslinje Indstillinger** \> **Org**.
2. Under fanen **Tjenester** skal du vælge **Moderne godkendelse**, og i ruden **Moderne** godkendelse skal du sørge for, **at Aktivér moderne godkendelse** er markeret. Vælg **Gem ændringer**.


## <a name="next-steps"></a>Næste trin

- [Sådan tilmelder du dig deres yderligere bekræftelsesmetode](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
- [Hvad er: Multifaktorgodkendelse](https://support.microsoft.com/help/4577374/what-is-multifactor-authentication)
- [Sådan logger du på efter registrering](https://support.microsoft.com/office/2b856342-170a-438e-9a4f-3c092394d3cb)
- [Sådan ændrer du deres yderligere bekræftelsesmetode](https://support.microsoft.com/office/956ec8d0-7081-4518-a701-f8414cc20831)

## <a name="related-content"></a>Relateret indhold

[Konfigurer multifaktorgodkendelse](set-up-multi-factor-authentication.md) (video)

[Slå multifaktorgodkendelse til for din telefon](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14)
