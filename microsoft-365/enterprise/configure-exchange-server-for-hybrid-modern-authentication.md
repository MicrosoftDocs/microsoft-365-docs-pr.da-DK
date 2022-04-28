---
title: Sådan konfigurerer du Exchange Server i det lokale miljø til at bruge hybrid moderne godkendelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/27/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Få mere at vide om, hvordan du konfigurerer et Exchange Server i det lokale miljø til at bruge Hybrid Modern Authentication (HMA), som giver dig mere sikker brugergodkendelse og -godkendelse.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2ee190a541fdf3e4e77a251e040f2cb69416088c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095746"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Sådan konfigurerer du Exchange Server i det lokale miljø til at bruge hybrid moderne godkendelse

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Hybrid Modern Authentication (HMA) er en metode til identitetsstyring, der tilbyder mere sikker brugergodkendelse og -godkendelse og er tilgængelig for Exchange hybridinstallationer på serveren i det lokale miljø.

## <a name="definitions"></a>Definitioner

Før vi begynder, skal du være fortrolig med nogle definitioner:

- Hybrid Modern Authentication \> HMA

- Exchange i det lokale miljø \> EXCH

- \> Exchange Online EXO

Hvis *et grafikelement i denne artikel har et objekt, der er "nedtonet" eller "nedtonet", betyder det desuden, at det element, der vises med gråt, ikke er inkluderet i HMA-specifik konfiguration*.

## <a name="enabling-hybrid-modern-authentication"></a>Aktivering af hybrid moderne godkendelse

Aktivering af HMA betyder:

1. At være sikker på at du opfylder de prereqs før du begynder.

1. Da mange **forudsætninger** er fælles for både Skype for Business og Exchange, [oversigt over hybrid moderne godkendelse og forudsætninger for at bruge den med Skype for Business og Exchange servere i det lokale miljø](hybrid-modern-auth-overview.md). Gør dette, før du begynder på nogen af trinnene i denne artikel.
Krav til sammenkædede postkasser, der skal indsættes.

1. Tilføjelse af URL-adresser til webtjenesten i det lokale miljø som **TJENESTEprincipalnavne (SPN'er)** i Azure AD. Hvis EXCH er i hybrid med **flere lejere**, skal disse URL-adresser til webtjenesten i det lokale miljø tilføjes som SPN'er i Azure AD for alle de lejere, der er hybride med EXCH.

1. Sikrer, at alle virtuelle mapper er aktiveret for HMA

1. Søger efter Objektet EvoSTS Auth Server

1. Aktivering af HMA i EXCH.

> [!NOTE]
> Understøtter din version af Office MA? Se [Sådan fungerer moderne godkendelse for Office 2013 og Office 2016-klientapps](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Sørg for, at du opfylder alle forudsætningerne

Da mange forudsætninger er almindelige for både Skype for Business og Exchange, skal du gennemse [oversigt over hybridmoderne godkendelse og forudsætninger for at bruge den med Skype for Business og Exchange servere i det lokale miljø](hybrid-modern-auth-overview.md). Gør dette  *, før*  du begynder på nogen af trinnene i denne artikel.

> [!NOTE]
> Outlook Web App og Exchange Kontrolpanel fungerer ikke med hybrid moderne godkendelse.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Tilføj URL-adresser til webtjenesten i det lokale miljø som SPN'er i Azure AD

Kør de kommandoer, der tildeler URL-adresser til webtjenesten i det lokale miljø som Azure AD-SPN'er. SPN'er bruges af klientcomputere og enheder under godkendelse og godkendelse. Alle de URL-adresser, der kan bruges til at oprette forbindelse fra det lokale miljø til Azure Active Directory (Azure AD), skal være registreret i Azure AD (dette omfatter både interne og eksterne navneområder).

Først skal du samle alle de URL-adresser, du skal tilføje i AAD. Kør disse kommandoer i det lokale miljø:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

Sørg for, at URL-adresserne, som klienter kan oprette forbindelse til, er angivet som HTTPS-tjenesteprincipalnavne i AAD. Hvis EXCH er i hybrid med **flere lejere**, skal disse HTTPS-SPN'er tilføjes i AAD for alle lejere i hybrid med EXCH.

1. Først skal du oprette forbindelse til AAD med [disse instruktioner](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > Du skal bruge indstillingen _Forbind-MsolService_ fra denne side for at kunne bruge kommandoen nedenfor.

2. Skriv følgende kommando for dine Exchange-relaterede URL-adresser:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Notér (og skærmbillede til senere sammenligning) outputtet af denne kommando, som skal indeholde en `https://*autodiscover.yourdomain.com*` og `https://*mail.yourdomain.com*` URL-adresse, men hovedsageligt består af SPN'er, der starter med `00000002-0000-0ff1-ce00-000000000000/`. Hvis der mangler `https://` URL-adresser fra dit lokale miljø, skal disse specifikke poster føjes til listen.

3. Hvis du ikke kan se dine interne og eksterne MAPI/HTTP-, EWS-, ActiveSync-, OAB- og Autodiscover-poster på denne liste, skal du tilføje dem ved hjælp af kommandoen nedenfor (url-adresserne i eksemplet er `mail.corp.contoso.com` og `owa.contoso.com`, men du vil **erstatte eksempel-URL-adresserne med dine egne**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. Kontrollér, at de nye poster blev tilføjet ved at køre `Get-MsolServicePrincipal` kommandoen fra trin 2 igen og gennemse outputtet. Sammenlign listen/skærmbilledet fra før med den nye liste over SPN'er. Du kan også tage et skærmbillede af den nye liste for dine poster. Hvis du lykkedes, kan du se de to nye URL-adresser på listen. I eksemplet indeholder listen over SPN'er nu de specifikke URL-adresser `https://mail.corp.contoso.com` og `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>Kontrollér, at virtuelle mapper er konfigureret korrekt

Kontrollér nu, at OAuth er korrekt aktiveret i Exchange på alle de virtuelle mapper, Outlook kan bruge, ved at køre følgende kommandoer:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Kontrollér outputtet for at sikre, at **OAuth** er aktiveret for hver af disse VDirs. Det ser nogenlunde sådan ud (og det vigtigste at se på er 'OAuth'):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Hvis OAuth mangler fra en server og en af de fire virtuelle mapper, skal du tilføje den ved hjælp af de relevante kommandoer, før du fortsætter ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) og [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Bekræft, at EvoSTS-godkendelsesserverobjektet er til stede

Vend tilbage til den lokale Exchange Management Shell for den sidste kommando. Nu kan du validere, at dit lokale miljø har en post for evoSTS-godkendelsesprovideren:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

Dit output skal vise en AuthServer med navnet EvoSts med et GUID, og tilstanden 'Aktiveret' skal være Sand. Hvis du ikke kan se dette, skal du hente og køre den nyeste version af guiden Hybridkonfiguration.

> [!NOTE]
> Hvis EXCH er i hybrid med **flere lejere**, skal outputtet vise én AuthServer for hver `EvoSts - {GUID}` lejer i hybrid med EXCH, og tilstanden **Aktiveret** skal være Sand for alle disse AuthServer-objekter.

> [!IMPORTANT]
> Hvis du kører Exchange 2010 i dit miljø, oprettes EvoSTS-godkendelsesprovideren ikke.

## <a name="enable-hma"></a>Aktivér HMA

Kør følgende kommando i Exchange Management Shell i det lokale miljø, hvor kommandolinjen erstattes \<GUID\> med strengen i dit miljø:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> I ældre versioner af guiden Hybridkonfiguration blev EvoSts AuthServer blot navngivet EvoSTS uden et tilknyttet GUID. Der er ingen handling, du skal udføre. Du skal blot ændre kommandolinjen ovenfor for at afspejle dette ved at fjerne GUID-delen af kommandoen:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

Hvis EXCH-versionen er Exchange 2016 (CU18 eller nyere) eller Exchange 2019 (CU7 eller nyere), og hybrid blev konfigureret med HCW downloadet efter september 2020, skal du køre følgende kommando i Exchange Management Shell i det lokale miljø:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> Hvis EXCH er i hybrid med **flere lejere**, er der flere AuthServer-objekter i EXCH med domæner, der svarer til hver lejer.  Flaget **IsDefaultAuthorizationEndpoint** skal angives til sand (ved hjælp af **IsDefaultAuthorizationEndpoint-cmdlet'en** ) for et af disse AuthServer-objekter. Dette flag kan ikke angives til sand for alle Authserver-objekter, og HMA vil være aktiveret, selvom et af disse AuthServer-objekters **IsDefaultAuthorizationEndpoint-flag** er angivet til sand.
> 
> Til parameteren **DomainName** skal du bruge værdien for lejerdomænet, som normalt er i formatet `contoso.onmicrosoft.com`.

## <a name="verify"></a>Kontrollere

Når du aktiverer HMA, bruger en klients næste logon det nye godkendelsesflow. Bemærk, at hvis du bare aktiverer HMA, udløses der ikke en godkendelse for en hvilken som helst klient, og det kan tage et stykke tid for Exchange at hente de nye indstillinger.

Du skal også holde CTRL-tasten nede, samtidig med at du højreklikker på ikonet for Outlook-klienten (også på Windows meddelelsesbakken) og klikke på "Forbindelsesstatus". Søg efter klientens SMTP-adresse i forhold til **typen Authn** , `Bearer\*`som repræsenterer det ihændehavertoken, der bruges i OAuth.

> [!NOTE]
> Har du brug for at konfigurere Skype for Business med HMA? Du skal bruge to artikler: Én, der viser [understøttede topologier](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), og en, der viser dig [, hvordan du udfører konfigurationen](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Brug af hybrid moderne godkendelse med Outlook til iOS og Android

Hvis du er kunde i det lokale miljø ved hjælp af Exchange server på TCP 443, skal du tillade netværkstrafik fra følgende IP-områder:

```console
52.125.128.0/20
52.127.96.0/23
```

Disse IP-adresseområder er også dokumenteret i [Yderligere slutpunkter, der ikke er inkluderet i Office 365 IP-adresse og URL-webtjeneste](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>Relaterede emner

[Krav til moderne godkendelseskonfiguration for overgang fra Office 365 dedikeret/ITAR til vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
