---
title: Konfigurer katalogsynkronisering for Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Få mere at vide om, hvordan du konfigurerer katalogsynkronisering mellem Microsoft 365 og din Active Directory i det lokale miljø.
ms.openlocfilehash: 49240d056520a83c0828440e21c5cf26943bae8e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092883"
---
# <a name="set-up-directory-synchronization-for-microsoft-365"></a>Konfigurer katalogsynkronisering for Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Microsoft 365 bruger en Azure AD-lejer (Azure Active Directory) til at gemme og administrere identiteter til godkendelse og tilladelser til at få adgang til skybaserede ressourcer. 

Hvis du har et ad DS-domæne (Active Directory i det lokale miljø Domain Services), kan du synkronisere dine AD DS-brugerkonti, -grupper og -kontakter med Azure AD-lejeren for dit Microsoft 365-abonnement. Dette er en hybrididentitet for Microsoft 365. Her er komponenterne.

![Komponenter i katalogsynkronisering for Microsoft 365.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD Forbind kører på en lokal server og synkroniserer din AD DS med Azure AD-lejeren. Ud over katalogsynkronisering kan du også angive disse godkendelsesindstillinger:

- Synkronisering af adgangskodehash (PHS)

  Azure AD udfører selve godkendelsen.

- Pass-through-godkendelse (PTA)

  Azure AD har AD DS til at udføre godkendelsen.

- Federated Authentication

  Azure AD henviser den klientcomputer, der anmoder om godkendelse, til en anden identitetsudbyder.

Se [Hybrididentiteter](plan-for-directory-synchronization.md) for at få flere oplysninger.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Gennemse forudsætninger for Azure AD-Forbind

Du får et gratis Azure AD-abonnement med dit Microsoft 365-abonnement. Når du konfigurerer katalogsynkronisering, installerer du Azure AD-Forbind på en af dine lokale servere.
  
For Microsoft 365 skal du:
  
- Kontrollér dit lokale domæne. Guiden Azure AD Forbind hjælper dig gennem dette.
- Hent brugernavne og adgangskoder til administratorkontiene for din Microsoft 365 lejer og AD DS.

For den lokale server, hvor du installerer Azure AD Forbind, skal du bruge:
  
|**Serveroperativsystemer**|**Anden software**|
|:-----|:-----|
|Windows Server 2012 R2 og nyere | – PowerShell er installeret som standard. Der kræves ingen handling.  <br> - Net 4.5.1 og nyere udgivelser tilbydes via Windows Update. Sørg for, at du har installeret de nyeste opdateringer på Windows Server i Kontrolpanel. |
|Windows Server 2008 R2 med Service Pack 1 (SP1)** eller Windows Server 2012 | – Den nyeste version af PowerShell er tilgængelig i Windows Management Framework 4.0. Søg efter den på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .Net 4.5.1 og nyere versioner er tilgængelige på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | – Den nyeste understøttede version af PowerShell er tilgængelig i Windows Management Framework 3.0, som er tilgængelig på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> - .Net 4.5.1 og nyere versioner er tilgængelige på [Microsoft Download Center](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Se [Forudsætninger for Azure Active Directory Forbind for](/azure/active-directory/hybrid/how-to-connect-install-prerequisites) at få oplysninger om krav til hardware, software, konto og tilladelser, SSL-certifikatkrav og objektgrænser for Azure AD-Forbind.
  
Du kan også gennemse Azure AD Forbind [versionsudgivelseshistorikken](/azure/active-directory/hybrid/reference-connect-version-history) for at se, hvad der er inkluderet og løst i hver version.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. Installer Azure AD Forbind, og konfigurer katalogsynkronisering

Før du begynder, skal du sørge for, at du har:

- Brugernavnet og adgangskoden for en Microsoft 365 global administrator
- Brugernavnet og adgangskoden for en AD DS-domæneadministrator
- Hvilken godkendelsesmetode (PHS, PTA, sammenkædet)
- Uanset om du vil bruge [Azure AD Seamless Single Sign-on (SSO)](/azure/active-directory/hybrid/how-to-connect-sso)

Følg disse trin:

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ( ,https://admin.microsoft.com) og vælg **Aktive brugere** \> i venstre navigationsrude.
2. På siden **Aktive brugere** skal du vælge **Flere** (tre prikker) \> **Katalogsynkronisering**.
  
3. På siden **Azure Active Directory forberedelse** skal du vælge linket **Gå til Download Center for at få linket azure AD Forbind værktøj** for at komme i gang. 
4. Følg trinnene i [Køreplan for installation af Azure AD Forbind og Azure AD Forbind Health](/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. Afslut konfiguration af domæner

Følg trinnene i [Opret DNS-poster for Microsoft 365 når du administrerer dine DNS-poster](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) for at afslutte indstillingerne for dine domæner.

## <a name="next-step"></a>Næste trin

[Tildel licenser til brugerkonti](assign-licenses-to-user-accounts.md)