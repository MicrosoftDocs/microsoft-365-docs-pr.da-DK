---
title: Sådan fungerer moderne godkendelse til Office 2013- Office 2016-klientprogrammer
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Lær, Microsoft 365 moderne godkendelsesfunktioner fungerer anderledes i forbindelse med Office 2013- og 2016-klientprogrammer.
ms.openlocfilehash: c3586029a3c1ea73dae30696c74011e3dd22400d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591000"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Sådan fungerer moderne godkendelse til Office 2013, Office 2016 og Office 2019-klientapps

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Læs denne artikel for at få mere at vide om, hvordan Office 2013-, Office 2016- og Office 2019-klientprogrammer bruger moderne godkendelsesfunktioner, der er baseret på godkendelseskonfigurationen på Microsoft 365-lejeren til Exchange Online, SharePoint Online og Skype for Business Online.

> [!NOTE]
> Ældre klientapps, f.eks. Office 2010 og Office til Mac 2011, understøtter ikke moderne godkendelse og kan kun bruges med grundlæggende godkendelse.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Tilgængeligheden af moderne godkendelse til Microsoft 365 tjenester

For Microsoft 365 er standardtilstanden for moderne godkendelse:

- Slået **til** for Exchange Online som standard. Se [Aktivér eller deaktiver moderne godkendelse Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) at slå den fra eller til.

- Slået **til** for SharePoint Online som standard.

- Slået **til** for Skype for Business Online som standard. Se [Aktivér Skype for Business Online til moderne godkendelsefor](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) at slå den fra eller til.

> [!NOTE]
> For lejere oprettet  før d. 1. august 2017 er moderne godkendelse som standard  slået fra for lejere Exchange Online og Skype for Business Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Logon-funktionsmåden i Office klientapps

Office 2013-klientapps understøtter ældre godkendelse som standard. "Ældre" betyder, at de understøtter enten Microsoft Online-logonassistent eller basisgodkendelse. For at disse klienter kan bruge moderne godkendelsesfunktioner, skal Windows have indstillet registreringsdatabasenøgler. Du kan finde en [vejledning i Aktivér moderne godkendelse Office 2013 på Windows enheder](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Hvis du vil aktivere moderne godkendelse for enheder, der kører Windows (f.eks. på bærbare computere og tablets), og som har Microsoft Office 2013 installeret, skal du angive følgende registreringsdatabasenøgler. Tasterne skal angives på hver enhed, du vil aktivere til moderne godkendelse:

|**Registreringsdatabasenøgle**|**Type**|**Værdi** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Læs [Sådan bruger du moderne godkendelse (ADAL) med Skype for Business at](./hybrid-modern-auth-overview.md) få mere at vide om, hvordan det fungerer med Skype for Business.

Office 2016- og Office 2019-klienter understøtter moderne godkendelse som standard, og klienten skal ikke gøre noget for at bruge disse nye flow. Dog er yderligere tiltag nødvendige for at bruge ældre godkendelse.

Klik på linkene nedenfor for at se, hvordan klientgodkendelse Office 2013, Office 2016 og Office 2019 fungerer sammen med Microsoft 365-tjenesterne, afhængigt af om moderne godkendelse er slået til eller fra.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

I følgende tabel beskrives godkendelsesfunktionsmåden for Office 2013, Office 2016 og Office 2019-klientprogrammer, når de opretter forbindelse til Exchange Online med eller uden moderne godkendelse.

|Office klientappversion****|Registreringsdatabasenøgle findes?****|Moderne godkendelse er aktiveret?****|Godkendelsesfunktionsmåde med moderne godkendelse er aktiveret for lejeren (standard)****|Godkendelsesfunktionsmåde med moderne godkendelse er deaktiveret for lejeren****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nej <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Ja  <br/> |Tvinger moderne godkendelse til Outlook 2013, 2016 eller 2019. <br/> [Flere oplysninger](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Tvinger moderne godkendelse i Outlook klient.<br/> |
|Office 2019  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL=0  <br/> |Nej  <br/> |Grundlæggende godkendelse  <br/> |Grundlæggende godkendelse  <br/> |
|Office 2016  <br/> |Nej <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Ja  <br/> |Tvinger moderne godkendelse til 2013, 2016 eller 2019. <br/> [Flere oplysninger](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Tvinger moderne godkendelse i Outlook klient.<br/> |
|Office 2016  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL=0  <br/> |Nej  <br/> |Grundlæggende godkendelse  <br/> |Grundlæggende godkendelse  <br/> |
|Office 2013  <br/> |Nej  <br/> |Nej  <br/> |Grundlæggende godkendelse  <br/> |Grundlæggende godkendelse  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges basisgodkendelse. Serveren afviser moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

I følgende tabel beskrives godkendelsesfunktionsmåden for Office 2013-, Office 2016- og Office 2019-klientprogrammer, når de opretter forbindelse til SharePoint Online med eller uden moderne godkendelse.

|Office klientappversion****|Registreringsdatabasenøgle findes?****|Moderne godkendelse er aktiveret?****|Godkendelsesfunktionsmåde med moderne godkendelse er aktiveret for lejeren (standard)****|Godkendelsesfunktionsmåde med moderne godkendelse er deaktiveret for lejeren****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Kunne ikke oprette forbindelse.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Kunne ikke oprette forbindelse.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online-logonassistent.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |
|Office 2016  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Kunne ikke oprette forbindelse.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Kunne ikke oprette forbindelse.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online-logonassistent.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |
|Office 2013  <br/> |Nej  <br/> |Nej  <br/> |Kun Microsoft Online-logonassistent.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Kunne ikke oprette forbindelse.  <br/> |

### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

I følgende tabel beskrives godkendelsesfunktionsmåden for Office 2013-, Office 2016- og Office 2019-klientprogrammer, når de opretter forbindelse til Skype for Business Online med eller uden moderne godkendelse.

|Office klientappversion****|Registreringsdatabasenøgle findes?****|Moderne godkendelse er aktiveret?****|Godkendelsesfunktionsmåde med moderne godkendelse er aktiveret for lejeren****|Godkendelsesfunktionsmåde med moderne godkendelse er deaktiveret for lejeren (standard)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online-logonassistent.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |
|Office 2016  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online-logonassistent.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |
|Office 2013  <br/> |Nej  <br/> |Nej  <br/> |Kun Microsoft Online-logonassistent.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren afviser en forbindelse med moderne godkendelse, bruges Microsoft Online-logonassistenten. Serveren afviser moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Kun Microsoft Online-logonassistent.  <br/> |

## <a name="see-also"></a>Se også

[Aktivér moderne godkendelse Office 2013 på Windows enheder](../admin/security-and-compliance/enable-modern-authentication.md)

[Multifaktorgodkendelse til Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Log på Microsoft 365 med multifaktorgodkendelse](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Enterprise oversigt](microsoft-365-overview.md)