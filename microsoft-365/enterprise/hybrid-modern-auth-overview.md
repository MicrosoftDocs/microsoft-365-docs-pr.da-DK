---
title: Oversigt over hybrid moderne godkendelse og forudsætninger for brug med Skype for Business- og Exchange servere i det lokale miljø
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: I denne artikel får du mere at vide om hybrid moderne godkendelse og forudsætningerne for brug sammen med Skype for Business og Exchange servere i det lokale miljø.
ms.openlocfilehash: c161f205aba1222f39811155bef5c6be6da613d0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093388"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Hybrid moderne godkendelsesoversigt og forudsætninger for at bruge den med Skype for Business- og Exchange servere i det lokale miljø

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

_Moderne godkendelse_ er en metode til identitetsstyring, der tilbyder mere sikker brugergodkendelse og -godkendelse. Den er tilgængelig til Office 365 hybridinstallationer af Skype for Business server i det lokale miljø og Exchange server i det lokale miljø og Skype for Business hybrider med delt domæne. Denne artikel indeholder links til relaterede dokumenter om forudsætninger, konfiguration/deaktivering af moderne godkendelse og til nogle af de relaterede klienter (f.eks. Outlook og Skype klienter) oplysninger.

- [Hvad er moderne godkendelse?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Hvilke ændringer ændres, når jeg bruger moderne godkendelse?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Kontrollér den moderne godkendelsesstatus for dit lokale miljø](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Opfylder du moderne godkendelsesbetingelser?](#do-you-meet-modern-authentication-prerequisites)
- [Hvad skal jeg ellers vide, før jeg begynder?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Hvad er moderne godkendelse?
<a name="BKMK_WhatisModAuth"> </a>

Moderne godkendelse er et paraplyord for en kombination af godkendelses- og godkendelsesmetoder mellem en klient (f.eks. din bærbare computer eller din telefon) og en server samt nogle sikkerhedsforanstaltninger, der er afhængige af adgangspolitikker, som du måske allerede kender. Den indeholder:

- **Godkendelsesmetoder**: Multifactor-godkendelse (MFA); chipkortgodkendelse; klientcertifikatbaseret godkendelse
- **Autorisationsmetoder**: Microsofts implementering af Open Authorization (OAuth)
- **Politikker for betinget adgang**: Administration af mobilapps (MAM) og Azure Active Directory (Azure AD) Betinget adgang

Administration af brugeridentiteter med moderne godkendelse giver administratorer mange forskellige værktøjer til at beskytte ressourcer og tilbyder mere sikre metoder til identitetsstyring i både det lokale miljø (Exchange og Skype for Business), Exchange hybrid- og Skype for Business hybrid-/split-domænescenarier.

Da Skype for Business arbejder tæt sammen med Exchange, påvirkes logonfunktionsmåden Skype for Business klientbrugere af den moderne godkendelsesstatus for Exchange. Det gælder også, hvis du har en Skype for Business hybridarkitektur med _opdelt domæne_, hvor du både har Skype for Business Online og Skype for Business i det lokale miljø, hvor brugerne er placeret begge steder.

Du kan få flere oplysninger om moderne godkendelse i Office 365 under [understøttelse af Office 365 klientapp – multifaktorgodkendelse](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Fra august 2017 vil alle nye Office 365 lejere, der omfatter Skype for Business online og Exchange online, som standard have moderne godkendelse aktiveret. Eksisterende lejere vil ikke have en ændring i deres standard-MA-tilstand, men alle nye lejere understøtter automatisk det udvidede sæt identitetsfunktioner, som du kan se ovenfor. Hvis du vil kontrollere din godkendelsesstatus, skal du se afsnittet [Kontrollér den moderne godkendelsesstatus for dit lokale miljø](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .

## <a name="what-changes-when-i-use-modern-authentication"></a>Hvilke ændringer ændres, når jeg bruger moderne godkendelse?
<a name="BKMK_WhatChanges"> </a>

Når du bruger moderne godkendelse med Skype for Business eller Exchange server i det lokale miljø, *godkender* du stadig brugere i det lokale miljø, men historien om *godkendelse* af deres adgang til ressourcer (f.eks. filer eller mails) ændres. Det er grunden til, at selvom moderne godkendelse handler om klient- og serverkommunikation, vil de trin, der udføres under konfigurationen af MA, resultere i, at en sikkerhedstokentjeneste, der bruges af Azure AD, angives som Auth Server for Skype for Business og Exchange server i det lokale miljø.

Ændringen til evoSTS gør det muligt for dine lokale servere at drage fordel af OAuth (tokenudgivelse) til godkendelse af dine klienter, og gør det også muligt for dine lokale myndigheder at bruge sikkerhedsmetoder, der er fælles i cloudmiljøet (f.eks. multifaktorgodkendelse). Derudover fremkalder de tokens til problemer, der giver brugerne mulighed for at anmode om adgang til ressourcer uden at angive deres adgangskode som en del af anmodningen. Uanset hvor dine brugere er placeret (af online eller i det lokale miljø), og uanset hvilken placering der er vært for den nødvendige ressource, bliver EvoSTS kernen i godkendelse af brugere og klienter, når moderne godkendelse er konfigureret.

Hvis en Skype for Business klient f.eks. skal have adgang til Exchange server for at hente kalenderoplysninger på vegne af en bruger, bruger den Microsoft Authentication Library (MSAL) til at gøre det. MSAL er et kodebibliotek, der er designet til at gøre sikre ressourcer i din mappe tilgængelige for klientprogrammer ved hjælp af OAuth-sikkerhedstokens. MSAL arbejder sammen med OAuth om at bekræfte krav og om at udveksle tokens (i stedet for adgangskoder) for at give en bruger adgang til en ressource. Tidligere har autoriteten i en transaktion som denne – den server, der ved, hvordan brugerkrav skal valideres og udsteder de nødvendige tokens – måske været en sikkerhedstokentjeneste i det lokale miljø eller endda Active Directory Federation Services. Moderne godkendelse centraliserer dog denne myndighed ved hjælp af Azure AD.

Det betyder også, at selvom dine Exchange-server- og Skype for Business-miljøer kan være helt i det lokale miljø, vil den godkendende server være online, og dit lokale miljø skal have mulighed for at oprette og vedligeholde en forbindelse til dit Office 365 abonnement i cloudmiljøet (og den Azure AD-forekomst, som dit abonnement bruger som sin mappe).

Hvad ændres ikke? Uanset om du er i en hybrid med opdelt domæne eller bruger Skype for Business og Exchange server i det lokale miljø, skal alle brugere først godkende *i det lokale miljø*. I en hybrid implementering af moderne godkendelse peger _Lyncdiscovery_ og _Autodiscovery_ begge på din lokale server.

> [!IMPORTANT]
> Hvis du har brug for at kende de specifikke Skype for Business topologier, der understøttes med ma, [er det dokumenteret lige her](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Kontrollér den moderne godkendelsesstatus for dit lokale miljø
<a name="BKMK_CheckStatus"> </a>

Da moderne godkendelse ændrer den godkendelsesserver, der bruges, når tjenester anvender OAuth/S2S, skal du vide, om moderne godkendelse er aktiveret eller deaktiveret for dine lokale Skype for Business og Exchange miljøer. Du kan kontrollere status på dine Exchange servere ved at køre følgende PowerShell-kommando:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Hvis værdien af egenskaben _OAuth2ClientProfileEnabled_ er **False**, er moderne godkendelse deaktiveret.

Du kan få flere oplysninger om cmdlet'en Get-OrganizationConfig under [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

Du kan kontrollere dine Skype for Business-servere ved at køre følgende PowerShell-kommando:

```powershell
Get-CSOAuthConfiguration
```

Hvis kommandoen returnerer en tom _OAuthServers-egenskab_ , eller hvis værdien af egenskaben _ClientADALAuthOverride_ ikke er **tilladt**, er moderne godkendelse deaktiveret.

Du kan få flere oplysninger om cmdlet'en Get-CsOAuthConfiguration under [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Opfylder du moderne godkendelsesbetingelser?

Kontrollér og markér disse elementer fra listen, før du fortsætter:

- **Skype for Business specifik**
  - Alle servere skal have en kumulativ opdatering fra maj 2017 (CU5) for Skype for Business Server 2015 eller nyere
    - **Undtagelse** – SBA (Survivability Branch Appliance) kan være på den aktuelle version (baseret på Lync 2013)
  - Dit SIP-domæne tilføjes som et domæne i organisationsnetværket i Office 365
  - Alle SFB-frontends skal have forbindelser, der er udgående til internettet, for at Office 365 URL-adresser til godkendelse (TCP 443) og velkendte certifikatrod-CRLs (TCP 80), der er angivet i række 56 og 125 i afsnittet "Microsoft 365 Fælles og Office" [i Office 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md).

- **Skype for Business i det lokale miljø i et hybridt Office 365 miljø**
  - En Skype for Business Server 2019-installation med alle servere, der kører Skype for Business Server 2019.
  - En Skype for Business Server 2015-installation med alle servere, der kører Skype for Business Server 2015.
  - En installation med maksimalt to forskellige serverversioner som angivet nedenfor:
    - Skype for Business Server 2015
    - Skype for Business Server 2019
  - Alle Skype for Business servere skal have de nyeste kumulative opdateringer installeret. Se [Skype for Business Server opdateringer](/skypeforbusiness/sfb-server-updates) for at finde og administrere alle tilgængelige opdateringer.
  - Der er ingen Lync Server 2010 eller 2013 i hybridmiljøet.

>[!NOTE]
>Hvis dine Skype for Business frontendservere bruger en proxyserver til internetadgang, skal den anvendte proxyservers IP- og portnummer angives i konfigurationsafsnittet i web.config-filen for hver frontend.

- C:\Programmer\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Programmer\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> Sørg for at abonnere på RSS-feedet for [Office 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md) for at holde dig opdateret med de seneste lister over påkrævede URL-adresser.

- **Exchange Server specifik**
  - Du bruger enten Exchange server 2013 CU19 og op, Exchange server 2016 CU8 og op eller Exchange Server 2019 CU1 og op.
  - Der er ingen Exchange server 2010 i miljøet.
  - SSL-aflastning er ikke konfigureret. SSL-afslutning og kryptering igen understøttes.
  - Hvis dit miljø anvender en proxyserverinfrastruktur til at tillade, at servere opretter forbindelse til internettet, skal du sørge for, at alle Exchange servere har den proxyserver, der er defineret i egenskaben [InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server i det lokale miljø i et hybridt Office 365 miljø**

  - Hvis du bruger Exchange Server 2013, skal rollerne Postkasse og Klientadgang være installeret på mindst én server. Selvom det er muligt at installere rollerne Postkasse og Klientadgang på separate servere, anbefaler vi på det kraftigste, at du installerer begge roller på den samme server for at give større pålidelighed og forbedret ydeevne.
  - Hvis du bruger Exchange server 2016 eller nyere version, skal mindst én server have serverrollen Postkasse installeret.
  - Der er ingen Exchange server 2007 eller 2010 i hybridmiljøet.
  - Alle Exchange servere skal have de nyeste kumulative opdateringer installeret. Se [Opgrader Exchange til de seneste kumulative opdateringer](/exchange/plan-and-deploy/install-cumulative-updates) for at finde og administrere alle tilgængelige opdateringer.

- **krav til Exchange klient og protokol**

    Tilgængeligheden af moderne godkendelse bestemmes af kombinationen af klienten, protokollen og konfigurationen. Hvis moderne godkendelse ikke understøttes af klienten, protokollen og/eller konfigurationen, vil klienten fortsat bruge ældre godkendelse.
  
    Følgende klienter og protokoller understøtter moderne godkendelse med Exchange i det lokale miljø, når moderne godkendelse er aktiveret i miljøet:

  |**Klienter**|**Primær protokol**|**Bemærkninger**|
  |:-----|:-----|:-----|
  |Outlook 2013 og nyere  <br/> |MAPI via HTTP  <br/> |MAPI via HTTP skal være aktiveret i Exchange for at kunne bruge moderne godkendelse med disse klienter (aktiveret eller Sand for nye installationer af Exchange 2013 Service Pack 1 eller nyere). Du kan få flere oplysninger under [Sådan fungerer moderne godkendelse for Office 2013- og Office 2016-klientapps](modern-auth-for-office-2013-and-2016.md).  <br/> Sørg for, at du kører det påkrævede build af Outlook. Se [Seneste opdateringer til versioner af Outlook, der bruger Windows Installer (MSI)](/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 til Mac og nyere  <br/> |Exchange webtjenester  <br/> |  <br/> |
  |Outlook til iOS og Android  <br/> | Microsoft-synkroniseringsteknologi <br/> |Se [Brug af hybrid moderne godkendelse med Outlook til iOS og Android for](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) at få flere oplysninger.  <br/> |
  |Exchange ActiveSync klienter (f.eks. iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |For Exchange ActiveSync klienter, der understøtter moderne godkendelse, skal du genoprette profilen for at skifte fra grundlæggende godkendelse til moderne godkendelse.  <br/> |

    Klienter og/eller protokoller, der ikke er angivet (f.eks. POP3), understøtter ikke moderne godkendelse med Exchange i det lokale miljø og fortsætter med at bruge ældre godkendelsesmetoder, selv efter at moderne godkendelse er aktiveret i miljøet.

- **Generelle forudsætninger**
  - Scenarier med ressourceområder kræver tovejs tillid til kontoområdet for at sikre, at der udføres korrekte SID-opslag under hybride moderne godkendelsesanmodninger. 
  - Hvis du bruger AD FS, skal du have Windows 2012 R2 AD FS 3.0 og nyere for sammenslutning.
  - Dine identitetskonfigurationer er en af de typer, der understøttes af Azure AD Forbind, f.eks. synkronisering af adgangskodehash, pass-through-godkendelse og STS i det lokale miljø, der understøttes af Office 365.
  - Du har Azure AD-Forbind konfigureret og fungerer til brugerreplikering og -synkronisering.
  - Du har kontrolleret, at hybrid er konfigureret ved hjælp af Exchange klassisk hybridtopologitilstand mellem dit lokale miljø og Office 365 miljø. Officiel supporterklæring for Exchange hybrid siger, at du skal have enten nuværende CU eller nuværende CU - 1.
    > [!NOTE]
    > Hybrid moderne godkendelse understøttes ikke med [Hybrid Agent](/exchange/hybrid-deployment/hybrid-agent).

  - Sørg for, at både en testbruger i det lokale miljø samt en hybridtestbruger, der er placeret i Office 365, kan logge på den Skype for Business desktopklient (hvis du vil bruge moderne godkendelse sammen med Skype) og Microsoft Outlook (hvis du vil bruge moderne godkendelse med Exchange).
  - Sørg for, at indstillingen SignInOptions i Microsoft Office ikke er konfigureret til den mest restriktive indstilling. Du kan få flere oplysninger under [Sådan tillader du, at Office opretter forbindelse til internettet](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Hvad skal jeg ellers vide, før jeg begynder?
<a name="BKMK_Whatelse"> </a>

- Alle scenarierne for lokale servere omfatter konfiguration af moderne godkendelse i det lokale miljø (faktisk for Skype for Business der er en liste over understøttede topologier), så den server, der er ansvarlig for godkendelse og godkendelse, befinder sig i Microsoft Cloud (Azure AD's sikkerhedstokentjeneste, kaldet 'evoSTS'), og opdatering af Azure AD om de URL-adresser eller navneområder, der bruges af din installation i det lokale miljø af enten Skype for Business eller Exchange. Derfor påtager lokale servere sig en Microsoft Cloud-afhængighed. Hvis du udfører denne handling, kan det overvejes at konfigurere "hybridgodkendelse".
- Denne artikel indeholder links til andre, der kan hjælpe dig med at vælge understøttede moderne godkendelsestopologier (kun nødvendige for Skype for Business) og vejledningsartikler, der beskriver konfigurationstrinnene eller trin til deaktivering af moderne godkendelse for Exchange i det lokale miljø og Skype for Business i det lokale miljø. Gør denne side til favorit i din browser, hvis du har brug for en hjemmebase til brug af moderne godkendelse i dit servermiljø.

## <a name="related-topics"></a>Relaterede emner
<a name="BKMK_URLListforMA"> </a>

- [Sådan konfigurerer du Exchange Server i det lokale miljø til at bruge moderne godkendelse](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype for Business topologier, der understøttes med moderne godkendelse](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Sådan konfigurerer du Skype for Business i det lokale miljø til at bruge moderne godkendelse](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Fjernelse eller deaktivering af hybrid moderne godkendelse fra Skype for Business og Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
