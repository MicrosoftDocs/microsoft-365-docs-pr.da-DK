---
title: Sådan fungerer moderne godkendelse for Office 2013- og Office 2016-klientapps
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Få mere at vide om, hvordan Microsoft 365 moderne godkendelsesfunktioner fungerer anderledes for Office 2013- og 2016-klientapps.
ms.openlocfilehash: 9c4cdc384ceded4ce3bb78ae4e67e0f4c5a503de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093366"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Sådan fungerer moderne godkendelse for Office 2013, Office 2016 og Office 2019-klientapps

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Læs denne artikel for at få mere at vide om, hvordan Office 2013, Office 2016 og Office 2019-klientapps bruger moderne godkendelsesfunktioner, der er baseret på godkendelseskonfigurationen på Microsoft 365 lejeren til Exchange Online, SharePoint Online og Skype for Business Online.

> [!NOTE]
> Ældre klientapps, f.eks. Office 2010 og Office til Mac 2011, understøtter ikke moderne godkendelse og kan kun bruges sammen med grundlæggende godkendelse.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Tilgængelighed af moderne godkendelse for Microsoft 365 tjenester

For de Microsoft 365 tjenester er standardtilstanden for moderne godkendelse:

- **Aktiveret** for Exchange Online som standard. Se [Aktivér eller deaktiver moderne godkendelse i Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) for at slå den fra eller til.

- **Aktiveret** for SharePoint Online som standard.

- **Aktiveret** for Skype for Business Online som standard. Se [Aktivér Skype for Business Online for moderne godkendelsefor](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) at slå den fra eller til.

> [!NOTE]
> For lejere, der er oprettet **før** den 1. august 2017, er moderne godkendelse som standard **slået fra** for Exchange Online og Skype for Business Online.

## <a name="sign-in-behavior-of-office-client-apps"></a>Logonfunktion for Office klientapps

Office 2013-klientapps understøtter som standard ældre godkendelse. Legacy betyder, at de understøtter enten Microsoft Online Sign-in Assistant eller basisgodkendelse. Hvis disse klienter skal bruge moderne godkendelsesfunktioner, skal der være angivet registreringsdatabasenøgler for den Windows klient. Du kan finde instruktioner under [Aktivér moderne godkendelse for Office 2013 på Windows enheder](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Hvis du vil aktivere moderne godkendelse for alle enheder, der kører Windows (f.eks. på bærbare computere og tablets), der har Microsoft Office 2013 installeret, skal du angive følgende registreringsdatabasenøgler. Nøglerne skal angives på hver enhed, du vil aktivere til moderne godkendelse:

|**Registreringsdatabasenøgle**|**Type**|**Værdi** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Læs [Sådan bruger du ADAL (Modern Authentication) sammen med Skype for Business](./hybrid-modern-auth-overview.md) for at få mere at vide om, hvordan det fungerer med Skype for Business.

Office 2016- og Office 2019-klienter understøtter som standard moderne godkendelse, og der kræves ingen handling, for at klienten kan bruge disse nye flow. Eksplicit handling er dog nødvendig for at bruge ældre godkendelse.

Klik på linkene nedenfor for at se, hvordan Office 2013, Office 2016 og Office 2019-klientgodkendelse fungerer sammen med de Microsoft 365 tjenester, afhængigt af om moderne godkendelse er slået til eller ej.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype for Business Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

I følgende tabel beskrives godkendelsesfunktionsmåden for Office 2013, Office 2016 og Office 2019-klientapps, når de opretter forbindelse til Exchange Online med eller uden moderne godkendelse.

|Office klientappversion****|Registreringsdatabasenøglen findes?****|Moderne godkendelse er slået til?****|Godkendelsesfunktionsmåde med moderne godkendelse slået til for lejeren (standard)****|Godkendelsesfunktionsmåde med moderne godkendelse slået fra for lejeren****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nej <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Ja  <br/> |Gennemtvinger moderne godkendelse på Outlook 2013, 2016 eller 2019. <br/> [Flere oplysninger](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Gennemtvinger moderne godkendelse i Outlook-klienten.<br/> |
|Office 2019  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL=0  <br/> |Nej  <br/> |Basisgodkendelse  <br/> |Basisgodkendelse  <br/> |
|Office 2016  <br/> |Nej <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Ja  <br/> |Gennemtvinger moderne godkendelse i 2013, 2016 eller 2019. <br/> [Flere oplysninger](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Gennemtvinger moderne godkendelse i Outlook-klienten.<br/> |
|Office 2016  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL=0  <br/> |Nej  <br/> |Basisgodkendelse  <br/> |Basisgodkendelse  <br/> |
|Office 2013  <br/> |Nej  <br/> |Nej  <br/> |Basisgodkendelse  <br/> |Basisgodkendelse  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges basisgodkendelse. Serveren nægter moderne godkendelse, når lejeren ikke er aktiveret.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

I følgende tabel beskrives godkendelsesfunktionsmåden for Office 2013, Office 2016 og Office 2019-klientapps, når de opretter forbindelse til SharePoint Online med eller uden moderne godkendelse.

|Office klientappversion****|Registreringsdatabasenøglen findes?****|Moderne godkendelse er slået til?****|Godkendelsesfunktionsmåde med moderne godkendelse slået til for lejeren (standard)****|Godkendelsesfunktionsmåde med moderne godkendelse slået fra for lejeren****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Det lykkedes ikke at oprette forbindelse.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Det lykkedes ikke at oprette forbindelse.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |
|Office 2016  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Det lykkedes ikke at oprette forbindelse.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Det lykkedes ikke at oprette forbindelse.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |
|Office 2013  <br/> |Nej  <br/> |Nej  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Kun moderne godkendelse.  <br/> |Det lykkedes ikke at oprette forbindelse.  <br/> |

### <a name="skype-for-business-online"></a>Skype for Business Online
<a name="BK_SFBO"> </a>

I følgende tabel beskrives godkendelsesfunktionsmåden for Office 2013, Office 2016 og Office 2019-klientapps, når de opretter forbindelse til Skype for Business Online med eller uden moderne godkendelse.

|Office klientappversion****|Registreringsdatabasenøglen findes?****|Moderne godkendelse er slået til?****|Godkendelsesfunktionsmåde med moderne godkendelse slået til for lejeren****|Godkendelsesfunktionsmåde med moderne godkendelse slået fra for lejeren (standard)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2019  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |
|Office 2016  <br/> |Nej, eller EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |
|Office 2016  <br/> |Ja, EnableADAL = 0  <br/> |Nej  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |
|Office 2013  <br/> |Nej  <br/> |Nej  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |
|Office 2013  <br/> |Ja, EnableADAL = 1  <br/> |Ja  <br/> |Moderne godkendelse forsøges først. Hvis serveren nægter en moderne godkendelsesforbindelse, bruges Microsoft Online Sign-in Assistant. Serveren nægter moderne godkendelse, når Skype for Business Online-lejere ikke er aktiveret.  <br/> |Kun Microsoft Online Sign-in Assistant.  <br/> |

## <a name="see-also"></a>Se også

[Aktivér moderne godkendelse for Office 2013 på Windows enheder](../admin/security-and-compliance/enable-modern-authentication.md)

[Multifaktorgodkendelse til Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Log på Microsoft 365 med multifaktorgodkendelse](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[oversigt over Microsoft 365 Enterprise](microsoft-365-overview.md)