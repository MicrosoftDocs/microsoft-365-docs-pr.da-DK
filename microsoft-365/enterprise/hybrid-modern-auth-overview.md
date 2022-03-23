---
title: Oversigt over hybrid moderne godkendelse og forudsætninger for brug med lokale Skype for Business og Exchange servere
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel kan du få mere at vide om moderne hybridgodkendelse og forudsætningerne for brug med lokale Skype for Business og Exchange servere.
ms.openlocfilehash: efce3b5a04f2e9500330cab87d7ba8e62ca49db0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591347"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Hybrid, moderne godkendelsesoversigt og forudsætninger for brug af det med lokale Skype for Business og Exchange servere

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

_Moderne godkendelse_ er en identitetsadministrationsmetode, der giver mere sikker brugergodkendelse og autorisation. Den er tilgængelig for Office 365-hybridinstallationer af Skype for Business-server i det lokale miljø og Exchange-server i det lokale miljø og Skype for Business-hybridinstallationer. Denne artikel indeholder links til relaterede dokumenter om forudsætninger, konfiguration/deaktivering af moderne godkendelse og til nogle af de relaterede klienter (f.eks. Outlook og Skype klienter).

- [Hvad er moderne godkendelse?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Hvilke ændringer, når jeg bruger moderne godkendelse?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Kontrollér den moderne godkendelsesstatus for dit lokale miljø](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Opfylder du moderne godkendelsesfor forudsætninger?](#do-you-meet-modern-authentication-prerequisites)
- [Hvad mere har jeg brug for at vide, før jeg begynder?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Hvad er moderne godkendelse?
<a name="BKMK_WhatisModAuth"> </a>

Moderne godkendelse er et overlysbillede for en kombination af godkendelses- og godkendelsesmetoder mellem en klient (f.eks. din bærbare computer eller din telefon) og en server samt nogle sikkerhedsforanstaltninger, der afhænger af adgangspolitikker, som du måske allerede kender. Den indeholder:

- **Godkendelsesmetoder**: Multifaktorgodkendelse (MFA); godkendelse af chipkort. klientcertifikatbaseret godkendelse
- **Godkendelsesmetoder**: Microsofts implementering af Open Authorization (OAuth)
- **Politikker for betinget adgang**: Administration af mobilapps (MAM) og Azure Active Directory (Azure AD) betinget adgang

Administration af brugeridentiteter med moderne godkendelse giver administratorer mange forskellige værktøjer at bruge, når det drejer sig om at sikre ressourcer og tilbyder mere sikre metoder til identitetsadministration for både lokale scenarier (Exchange og Skype for Business), Exchange hybrid og Skype for Business hybrid-/split-domain-scenarier.

Da Skype for Business tæt sammen med Exchange, påvirkes logonfunktionsmåden for Skype for Business-klientbrugere af den moderne godkendelsesstatus for Exchange. Det er også relevant, hvis du har en Skype for Business _delt domæne-hybridarkitektur_, hvor du har både Skype for Business Online og Skype for Business lokalt, hvor brugerne er hjemme på begge placeringer.

Du kan finde flere oplysninger om moderne godkendelse Office 365 i [Office 365-klientappsupport – Multifaktorgodkendelse](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Pr. august 2017 vil alle nye lejere i Office 365, der omfatter Skype for Business online og Exchange online, som standard have moderne godkendelse aktiveret. Eksisterende lejere har ikke en ændring i deres MA-standardtilstand, men alle nye lejere understøtter automatisk det udvidede sæt af identitetsfunktioner, som du kan se ovenfor. Hvis du vil kontrollere din MA-status, [skal du se afsnittet Kontrollér den moderne godkendelsesstatus for dit lokale](hybrid-modern-auth-overview.md#BKMK_CheckStatus) miljø.

## <a name="what-changes-when-i-use-modern-authentication"></a>Hvilke ændringer, når jeg bruger moderne godkendelse?
<a name="BKMK_WhatChanges"> </a>

Når du bruger moderne godkendelse med en lokal Skype for Business- eller Exchange-server, godkender du stadig brugere lokalt, men historien  om at autorisere deres adgang til ressourcer (f.eks. filer eller mails) ændres. Selvom moderne godkendelse handler om klient- og serverkommunikation, betyder det, at de trin, der er taget under konfigurationen af MA, medfører, at AzureSTS (en sikkerhedstokentjeneste, der bruges af Azure AD), angives som Auth-server til Skype for Business- og Exchange-server i det lokale miljø.

Ændringen af størrelseSTS gør det muligt for dine lokale servere at udnytte OAuth (tokenudstedelse) til at autorisere dine kunder, og lader også dine lokale bruge sikkerhedsmetoder, der er almindelige i skyen (f.eks. Multi-Factor Authentication). Desuden udsteder forespørgselstokens, der giver brugerne mulighed for at anmode om adgang til ressourcer uden at angive deres adgangskode som en del af anmodningen. Uanset hvor dine brugere er hjemme (online eller i det lokale miljø), og uanset hvilken placering der hoster den nødvendige ressource, bliver serviceressourcer kernen i tilladelsesstyring af brugere og klienter, når moderne godkendelse er konfigureret.

Hvis en Skype for Business-klient f.eks. skal have adgang til Exchange-serveren for at få kalenderoplysninger på vegne af en bruger, bruges Microsofts godkendelsesbibliotek (MSAL) til at gøre dette. MSAL er et kodebibliotek, der er udviklet til at gøre sikre ressourcer i dit bibliotek tilgængelige for klientprogrammer ved hjælp af OAuth-sikkerhedstokens. MSAL arbejder sammen med OAuth om at bekræfte krav og udveksle tokens (i stedet for adgangskoder) for at give en bruger adgang til en ressource. Tidligere har den myndighed, der har bestået en transaktion som denne - en server, der ved, hvordan man validerer brugerkrav og udsteder de nødvendige tokens – måske have været en lokal sikkerhedstokentjeneste eller endda Active Directory Federation Services. Moderne godkendelse centraliserer imidlertid den pågældende myndighed ved hjælp af Azure AD.

Det betyder også, at selvom dine Exchange-server- og Skype for Business-miljøer kan være helt lokale, vil den tilladelsesbaserede server være online, og dit lokale miljø skal have mulighed for at oprette og opretholde en forbindelse til dit Office 365-abonnement i skyen (og den Azure AD-forekomst, som dit abonnement bruger som sin mappe).

Hvad ændres ikke? Uanset om du er i en hybrid med opdelte domæner eller bruger Skype for Business Exchange-server i det lokale miljø, skal alle brugere først godkende *lokalt*. I en hybrid implementering af moderne godkendelse peger _Lyncdiscovery_ og _Autodiscovery_ begge på din lokale server.

> [!IMPORTANT]
> Hvis du har brug for at kende de Skype for Business topologier, der understøttes med MA, [er det dokumenteret lige her](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Kontrollér den moderne godkendelsesstatus for dit lokale miljø
<a name="BKMK_CheckStatus"> </a>

Da moderne godkendelse ændrer godkendelsesserveren, der bruges, når tjenester anvender OAuth/S2S, skal du vide, om moderne godkendelse er aktiveret eller deaktiveret for dine lokale Skype for Business- og Exchange-miljøer. Du kan kontrollere status på dine Exchange servere ved at køre følgende PowerShell-kommando:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Hvis værdien af egenskaben _OAuth2ClientProfileEnabled_ er **Falsk**, deaktiveres moderne godkendelse.

Du kan finde flere oplysninger Get-OrganizationConfig cmdlet'en [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

Du kan kontrollere dine Skype for Business servere ved at køre følgende PowerShell-kommando:

```powershell
Get-CSOAuthConfiguration
```

Hvis kommandoen returnerer en tom _OAuthServers-egenskab_ , eller hvis værdien af egenskaben _ClientADALAuthOverride_ ikke er **Tilladt,** deaktiveres moderne godkendelse.

Du kan finde flere oplysninger Get-CsOAuthConfiguration cmdlet i [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Opfylder du moderne godkendelsesfor forudsætninger?

Bekræft og markér disse elementer på listen, inden du fortsætter:

- **Skype for Business specifikke**
  - Alle servere skal have akkumuleret opdatering fra maj 2017 (CU5) Skype for Business Server 2015 eller nyere
    - **Undtagelse** – SBA (Versionen af forgreningsafdelingen) kan være på den aktuelle version (baseret på Lync 2013)
  - Dit SIP-domæne tilføjes som et organisationsnetværksdomæne i Office 365
  - Alle SFB-frontender skal have forbindelser udgående til internettet, til Office 365-godkendelseswebadresser (TCP 443) og velkendte certifikatroden for liste over tilbagekaldte certifikater (TCP 80), der er angivet i række 56 og 125 i afsnittet Microsoft 365 Common and Office' [i Office 365](urls-and-ip-address-ranges.md) URL-adresser og IP-adresseintervaller.

- **Skype for Business det lokale miljø i et Office 365 miljø**
  - En Skype for Business Server 2019-installation med alle servere, der Skype for Business Server 2019.
  - En Skype for Business Server 2015-installation med alle servere, der Skype for Business Server 2015.
  - En installation med maksimalt to forskellige serverversioner som angivet nedenfor:
    - Skype for Business Server 2015
    - Skype for Business Server 2019
  - Alle Skype for Business-servere skal have de nyeste akkumulerede opdateringer installeret. Se Skype for Business Server [opdateringer](/skypeforbusiness/sfb-server-updates) for at finde og administrere alle tilgængelige opdateringer.
  - Der er ingen Lync Server 2010 eller 2013 i hybridmiljøet.

>[!NOTE]
>Hvis dine Skype for Business front end-servere bruger en proxyserver til internetadgang, skal ip-adressen og portnummeret for proxyserveren angives i konfigurationssektionen af web.config-filen for hver front end.

- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

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
> Sørg for at abonnere på RSS-feedet for [Office 365 URL-adresser](urls-and-ip-address-ranges.md) og IP-adresseintervaller for at holde dig opdateret med de seneste lister over påkrævede URL-adresser.

- **Exchange Server specifikke**
  - Du bruger enten Exchange server 2013 CU19 og op, Exchange server 2016 CU8 og op, eller Exchange Server 2019 CU1 og op.
  - Der er ingen Exchange server 2010 i miljøet.
  - SSL-aflæsning er ikke konfigureret. SSL-afslutning og genkryptering understøttes.
  - Hvis dit miljø benytter en proxyserverinfrastruktur til at tillade servere at oprette forbindelse til internettet, skal du sørge for, at alle Exchange-servere har den proxyserver, der er defineret i [egenskaben InternetWebProxy](/powershell/module/exchange/set-exchangeserver).

- **Exchange Server det lokale miljø i et Office 365 miljø**

  - Hvis du bruger en Exchange Server 2013, skal mindst én server have postkasse- og klientadgangsserverrollerne installeret. Selvom det er muligt at installere rollerne Postkasse og Klientadgang på separate servere, anbefaler vi kraftigt, at du installerer begge roller på den samme server for at give større pålidelighed og forbedret ydeevne.
  - Hvis du bruger en Exchange server 2016 eller nyere version, skal mindst én server have postkasseserverrollen installeret.
  - Der er ingen Exchange server 2007 eller 2010 i hybridmiljøet.
  - Alle Exchange-servere skal have de seneste akkumulerede opdateringer installeret. Se Opgrader [Exchange](/exchange/plan-and-deploy/install-cumulative-updates) til de seneste akkumulerede opdateringer for at finde og administrere alle tilgængelige opdateringer.

- **Exchange klient- og protokolkrav**

    Tilgængeligheden af moderne godkendelse bestemmes af kombinationen af klienten, protokollen og konfigurationen. Hvis moderne godkendelse ikke understøttes af klienten, protokollen og/eller konfigurationen, fortsætter klienten med at bruge ældre godkendelse.
  
    Følgende klienter og protokoller understøtter moderne godkendelse med lokal godkendelse, Exchange moderne godkendelse er aktiveret i miljøet:

  |**Klienter**|**Primary Protocol**|**Bemærkninger**|
  |:-----|:-----|:-----|
  |Outlook 2013 og nyere  <br/> |MAPI over HTTP  <br/> |MAPI over HTTP skal være aktiveret i Exchange for at kunne bruge moderne godkendelse med disse klienter (aktiveret eller Sand for nye installationer af Exchange 2013 Service Pack 1 og nyere). Få mere at vide under Sådan fungerer moderne godkendelse [til Office 2013- og Office 2016-klientapps](modern-auth-for-office-2013-and-2016.md).  <br/> Sørg for, at du kører det mindst nødvendige build af Outlook. Se Seneste opdateringer til versioner af Outlook, der [bruger Windows Installer (MSI)](/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 til Mac og nyere  <br/> |Exchange webtjenester  <br/> |  <br/> |
  |Outlook til iOS og Android  <br/> | Microsoft-synkroniseringsteknologi <br/> |Se [Brug af hybrid moderne godkendelse med Outlook til iOS og Android for at](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) få flere oplysninger.  <br/> |
  |Exchange ActiveSync klienter (f.eks. iOS11 Mail)  <br/> |Exchange ActiveSync  <br/> |For Exchange ActiveSync, der understøtter moderne godkendelse, skal du genoprette profilen for at skifte fra grundlæggende godkendelse til moderne godkendelse.  <br/> |

    Klienter og/eller protokoller, der ikke er angivet (f.eks. POP3), understøtter ikke moderne godkendelse med lokale Exchange og fortsætter med at bruge ældre godkendelsesmekanismer, selv efter moderne godkendelse er aktiveret i miljøet.

- **Generelle forudsætninger**
  - Scenarier for ressourceskove kræver en tovejs tillid til kontoskoven for at sikre, at der udføres korrekte SID-opslag under moderne hybridanmodninger om godkendelse. 
  - Hvis du bruger AD FS, skal du have Windows 2012 R2 AD FS 3.0 og derover til sammenslutning.
  - Dine identitetskonfigurationer er alle de typer, der understøttes af Azure AD Forbind, f.eks. synkronisering af adgangskodehash, pass-through-godkendelse og lokal STS, der understøttes af Office 365.
  - Du har Azure AD Forbind konfigureret og fungerer for brugerreplikering og synkronisering.
  - Du har bekræftet, at hybrid er konfigureret ved Exchange den klassiske hybridtopologitilstand mellem dit lokale miljø Office 365 miljøet. Official support statement for Exchange hybrid says you must have either current CU or current CU - 1.
    > [!NOTE]
    > Hybrid moderne godkendelse understøttes ikke med [hybridagenten](/exchange/hybrid-deployment/hybrid-agent).

  - Sørg for, at både en lokal testbruger og en hybridtestbruger, der er hjemme i Office 365, kan logge på Skype for Business-klienten på computeren (hvis du vil bruge moderne godkendelse med Skype) og Microsoft Outlook (hvis du vil bruge moderne godkendelse med Exchange).
  - Sørg for, at indstillingen SignInOptions i Microsoft Office ikke er konfigureret efter dens mest restriktive indstilling. Du kan finde flere oplysninger [under Sådan tillader Office at oprette forbindelse til internettet](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Hvad mere har jeg brug for at vide, før jeg begynder?
<a name="BKMK_Whatelse"> </a>

- Alle scenarier for lokale servere involverer konfiguration af moderne godkendelse i det lokale miljø (faktisk er der for Skype for Business en liste over understøttede topologier), så serveren, der er ansvarlig for godkendelse og godkendelse, er i Microsoft Cloud (Azure AD's sikkerhedstokentjeneste, kaldet "installationsSTS") og opdaterer Azure AD om URL-adresser eller navneområder, der bruges af din lokale installation af begge Skype for Business eller Exchange. Derfor tager lokale servere en Microsoft Cloud-afhængighed. Denne handling kan betragtes som konfiguration af "hybrid godkendelse".
- Denne artikel linker til andre, der kan hjælpe dig med at vælge understøttede topologier for moderne godkendelse (kun til Skype for Business) og vejledningsartikler, der beskriver konfigurationstrinnene eller trin til at deaktivere moderne godkendelse i Exchange lokalt og Skype for Business lokalt miljø. Gør denne side til favorit i din browser, hvis du skal bruge en hjemmebase til brug af moderne godkendelse i dit servermiljø.

## <a name="related-topics"></a>Relaterede emner
<a name="BKMK_URLListforMA"> </a>

- [Sådan konfigureres Exchange Server lokalt miljø til at bruge moderne godkendelse](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype for Business topologier, der understøttes med moderne godkendelse](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Sådan konfigureres Skype for Business lokale miljø til at bruge moderne godkendelse](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Fjerne eller deaktivere hybrid moderne godkendelse fra Skype for Business og Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
