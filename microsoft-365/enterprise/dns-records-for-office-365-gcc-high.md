---
title: DNS-poster for Office 365 GCC High
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Oversigt: DNS-poster for Office 365 GCC High'
hideEdit: true
ms.openlocfilehash: 80c1a5d4473af0877e67b6bc9e14a9ffd890e3ba
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63590962"
---
# <a name="dns-records-for-office-365-gcc-high"></a>DNS-poster for Office 365 GCC High

*Denne artikel gælder for Office 365 GCC High og Microsoft 365 GCC High*

Som en del af onboarding til Office 365 GCC High skal du føje dine SMTP- og SIP-domæner til din onlinetjenestelejer.  Du skal gøre dette ved hjælp af New-MsolDomain-cmdlet'en i Azure AD PowerShell eller bruge [Azure Government-portalen](https://portal.azure.us) til at starte processen med at tilføje domænet og bevise ejerskabet.

Når du har føjet dine domæner til din lejer og valideret, skal du bruge følgende vejledning til at tilføje de relevante DNS-poster for tjenesterne nedenfor.  Det kan være nødvendigt at redigere tabellen nedenfor, så den passer til organisationens behov i forhold til den eller de indgående MX-poster og eventuelle eksisterende Exchange Autodiscover-poster, du har på plads.  Vi anbefaler kraftigt, at du koordinerer disse DNS-poster med dit beskedteam for at undgå eventuelle strømsvigt eller forkert levering af mail.

## <a name="exchange-online"></a>Exchange Online

| Type | Prioritet | Værtsnavn | Peger på adresse eller værdi | TTL |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (se nedenfor for at få mere at vide) | En time |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | En time |
| CNAME | - | autodiscover | autodiscover.office365.us | En time |

### <a name="exchange-autodiscover-record"></a>Exchange Autodiscover-post

Hvis du har Exchange Server lokalt, anbefaler vi, at du lader din eksisterende post være på plads, mens du overfører til Exchange Online, og opdaterer denne post, når du har fuldført overførslen. 

### <a name="exchange-online-mx-record"></a>Exchange Online MX-post

MX-postværdien for dine accepterede domæner følger et standardformat som nævnt ovenfor: *tenant.mail.protection.office365.us*, der erstatter lejer med  den første del af dit standardlejernavn.

Hvis f.eks. dit lejernavn contoso.onmicrosoft.us, skal **du contoso.mail.protection.office365.us** som værdien for din MX-post.

## <a name="skype-for-business-online"></a>Skype for Business Online

### <a name="cname-records"></a>CNAME-poster

| Type | Værtsnavn | Peger på adresse eller værdi | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | En time |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | En time |

### <a name="srv-records"></a>SRV-poster

| Type | Tjeneste | Protokol | Port | Vægt | Prioritet | Navn | Destination | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.gov.skypeforbusiness.us | En time |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.gov.skypeforbusiness.us | En time |

## <a name="other-dns-records"></a>Andre DNS-poster

> [!IMPORTANT]
> Hvis du har en eksisterende *msoid* CNAME-post i din DNS-zone, skal **du** fjerne posten fra DNS på nuværende tidspunkt.  Msoid-posten er ikke kompatibel Microsoft 365 Enterprise apps *(tidligere Office 365 ProPlus),* og den vil forhindre, at aktiveringen lykkes.
