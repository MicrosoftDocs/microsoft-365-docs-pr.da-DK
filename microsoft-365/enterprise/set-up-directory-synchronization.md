---
title: Konfigurer katalogsynkronisering for Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Få mere at vide om, hvordan du konfigurerer katalogsynkronisering mellem Microsoft 365 og dit lokale Active Directory.
ms.openlocfilehash: 61b2dd822d0e65ebbf97ddcbfc3c8a03887c45a6
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63601565"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Konfigurer katalogsynkronisering for Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 bruger en Azure Active Directory (Azure AD) til at lagre og administrere identiteter til godkendelse og tilladelser til at få adgang til skybaserede ressourcer. 

Hvis du har et lokalt Active Directory-domæneservices (AD DS)-domæne eller -område, kan du synkronisere dine AD DS-brugerkonti, -grupper og -kontakter med Azure AD-lejeren i dit Microsoft 365-abonnement. Dette er en hybrididentitet for Microsoft 365. Her er dens komponenter.

![Komponenter i katalogsynkronisering til Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD Forbind kører på en lokal server og synkroniserer din AD DS med Azure AD-lejeren. Sammen med katalogsynkronisering kan du også angive disse godkendelsesindstillinger:

- Synkronisering af adgangskodehash (PHS)

  Azure AD udfører selve godkendelsen.

- Pass-through-godkendelse (PTA)

  Azure AD AD DS udføre godkendelsen.

- Federated Authentication

  Azure AD refererer klientcomputeren, der anmoder om godkendelse, til en anden identitetsudbyder.

Se [Hybrididentiteter](plan-for-directory-synchronization.md) for at få flere oplysninger.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Gennemgå forudsætninger for Azure AD-Forbind

Du får et gratis Azure AD-abonnement med dit Microsoft 365 abonnement. Når du konfigurerer katalogsynkronisering, skal du installere Azure AD Forbind på en af dine lokale servere.
  
Du Microsoft 365 vide, om du skal:
  
- Bekræfte dit lokale domæne. Guiden Azure AD Forbind vejleder dig gennem dette.
- Hent brugernavne og adgangskoder til administratorkonti på din Microsoft 365 lejer og AD DS.

For den lokale server, hvor du installerer Azure AD Forbind, skal du bruge:
  
|**Server OS**|**Anden software**|
|:-----|:-----|
|Windows Server 2012 R2 og nyere | - PowerShell er installeret som standard. Der kræves ingen handling.  <br> - Net 4.5.1 og nyere versioner tilbydes via Windows Update. Sørg for, at du har installeret de nyeste Windows server i Kontrolpanel. |
|Windows Server 2008 R2 med Service Pack 1 (SP1)** eller Windows Server 2012 | - Den nyeste version af PowerShell er tilgængelig i Windows Management Framework 4.0. Søg efter det på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .Net 4.5.1 og nyere versioner er tilgængelige på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | - Den nyeste understøttede version af PowerShell er tilgængelig i Windows Management Framework 3.0, som findes [på Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .Net 4.5.1 og nyere versioner er tilgængelige på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Se [Forudsætninger for Azure Active Directory Forbind](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) for at få mere at vide om krav til hardware, software, konto og tilladelser, SSL-certifikatkrav og objektbegrænsninger for Azure AD Forbind.
  
Du kan også gennemse Azure AD Forbind [versionsudgivelsesoversigten](/azure/active-directory/hybrid/reference-connect-version-history) for at se, hvad der er inkluderet og rettet i hver version.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Installér Azure AD Forbind og konfigurer katalogsynkronisering

Før du begynder, skal du kontrollere, at du har:

- Brugernavn og adgangskode for en Microsoft 365 global administrator
- Brugernavn og adgangskode for en AD DS domæneadministrator
- Hvilken godkendelsesmetode (PHS, PTA, organisationsnetværk)
- Uanset om du vil bruge [Azure AD Seamless Single Sign-on (SSO)](/azure/active-directory/hybrid/how-to-connect-sso)

Følg disse trin:

1. Log på siden [Microsoft 365 Administration](https://admin.microsoft.com) ( oghttps://admin.microsoft.com) vælg **Aktive brugere** \> **i** venstre navigationsrude.
2. På siden **Aktive brugere skal** du vælge **Flere** (tre d'er) **Katalogsynkronisering**\>.
  
3. På siden **Azure Active Directory forberedelse** skal du vælge linket Gå til **Download for at få linket Azure AD Forbind til** at komme i gang. 
4. Følg trinnene i [Azure AD Forbind roadmap til installation af Azure AD Forbind Azure AD.](/azure/active-directory/hybrid/how-to-connect-install-roadmap)

## <a name="3-finish-setting-up-domains"></a>3. Afslut konfigurationen af domæner

Følg trinnene i Oprette [DNS-poster for Microsoft 365 når](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) du administrerer dine DNS-poster for at afslutte konfigurationen af dine domæner.

## <a name="next-step"></a>Næste trin

[Tildel licenser til brugerkonti](assign-licenses-to-user-accounts.md)