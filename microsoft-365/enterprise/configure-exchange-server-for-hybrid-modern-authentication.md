---
title: Sådan konfigureres Exchange Server lokalt miljø til at bruge hybrid, moderne godkendelse
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Lær, hvordan du konfigurerer Exchange Server lokalt miljø til at bruge hybrid moderne godkendelse (HMA), hvilket giver dig mere sikker brugergodkendelse og autorisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0889008595717308695c1ad9c5d2a9f1766d1ea
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591551"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Sådan konfigureres Exchange Server lokalt miljø til at bruge hybrid, moderne godkendelse

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Hybrid moderne godkendelse (HMA) er en identitetsadministrationsmetode, der tilbyder mere sikker brugergodkendelse og -godkendelse, og som er tilgængelig for Exchange-serverhybridinstallationer i det lokale miljø.

## <a name="definitions"></a>Definitioner

Før vi begynder, bør du være fortrolig med nogle definitioner:

- Hybrid moderne godkendelse \> HMA

- Exchange lokale miljø \> EXCH

- \> Exchange Online EXO

Hvis grafikken i denne artikel desuden har et objekt, der er "nedtonet" eller "nedtonet", betyder det, at det element, der vises i grå, ikke er medtaget i *HMA-specifik konfiguration*.

## <a name="enabling-hybrid-modern-authentication"></a>Aktivering af hybrid moderne godkendelse

Aktivering af HMA betyder:

1. At være sikker på, at du opfylder kravene, før du går i gang.

1. Da mange **forudsætninger** er fælles for både Skype for Business og Exchange, oversigt over hybrid moderne godkendelse og forudsætninger for brug af det med lokale [Skype for Business og Exchange servere](hybrid-modern-auth-overview.md). Gør dette, før du starter nogle af trinnene i denne artikel.
Krav til sammenkædede postkasser, der skal indsættes.

1. Tilføjelse af lokale webtjeneste-URL-adresser som **Service Principal Names (SPN'er)** i Azure AD. I tilfælde af at EXCH er i hybrid med flere lejere, skal disse URL-adresser for den lokale webtjeneste **tilføjes** som SPN'er i Azure AD for alle lejere, der er hybride med EXCH.

1. Sørg for, at alle virtuelle kataloger er aktiveret til HMA

1. Søger efter objektet for den godkendelsesserver, der er kontrolleret

1. Aktivering af HMA i EXCH.

> [!NOTE]
> Understøtter din version Office MA? Se [Sådan fungerer moderne godkendelse til Office 2013 og Office 2016-klientprogrammer](modern-auth-for-office-2013-and-2016.md).

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Sørg for, at du opfylder alle forudsætningerne

Da mange forudsætninger er fælles for både Skype for Business og Exchange, skal du gennemse Oversigt over hybrid moderne godkendelse og forudsætninger for at bruge den med lokale [Skype for Business og Exchange-servere](hybrid-modern-auth-overview.md). Gør dette  *,*  før du starter nogle af trinnene i denne artikel.

> [!NOTE]
> Outlook Web App og Exchange fungerer ikke med moderne hybridgodkendelse.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Tilføj url-adresser for lokale webtjeneste som SPN'er i Azure AD

Kør de kommandoer, der tildeler dine lokale webtjeneste URL-adresser som Azure AD SPN'er. SPN'er bruges af klientcomputere og enheder under godkendelse og godkendelse. Alle DE URL-adresser, der kan bruges til at oprette forbindelse fra lokalt til Azure Active Directory (Azure AD), skal registreres i Azure AD (dette omfatter både interne og eksterne navneområder).

Først skal du samle alle de URL-adresser, du skal tilføje i AAD. Kør disse kommandoer lokalt:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

Kontrollér, at URL-adresserne, som klienterne kan oprette forbindelse til, er angivet som HTTPS-tjenestens hovednavne AAD. I tilfælde af at EXCH er hybrid med flere lejere, skal disse HTTPS-SPN'er **tilføjes** i AAD af alle lejere i hybrid med EXCH.

1. Du skal først oprette AAD med [denne vejledning](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > Du skal bruge indstillingen _Forbind-MsolService_ fra denne side for at kunne bruge kommandoen nedenfor.

2. For dine Exchange-relaterede URL-adresser skal du skrive følgende kommando:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Vær opmærksom på (og skærmbillede til senere sammenligning) outputtet af denne kommando, `https://*autodiscover.yourdomain.com*` `https://*mail.yourdomain.com*` som skal indeholde en og URL-adresse, men som primært består af SPN'er, der starter med `00000002-0000-0ff1-ce00-000000000000/`. Hvis der er `https://` URL-adresser fra dit lokale miljø, der mangler, skal disse specifikke poster føjes til denne liste.

3. Hvis du ikke kan se dine interne og eksterne MAPI-/HTTP-, EWS-, ActiveSync-, OAB- og Autodiscover-poster på denne liste, skal du tilføje dem ved hjælp af kommandoen nedenfor (`mail.corp.contoso.com``owa.contoso.com`eksemplet med URL-adresser er, og , men du vil erstatte disse URL-adresser **med dine egne**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. Bekræft, at dine nye poster blev tilføjet ved `Get-MsolServicePrincipal` at køre kommandoen fra trin 2 igen og gennemgå outputtet. Sammenlign listen/skærmbilledet fra før med den nye liste over SPN'er. Du kan også tage et skærmbillede af den nye liste til dine poster. Hvis det lykkedes for dig, kan du se de to nye URL-adresser på listen. I vores eksempel vil listen over SPN'er nu indeholde de specifikke URL-adresser `https://mail.corp.contoso.com` og `https://owa.contoso.com`.

## <a name="verify-virtual-directories-are-properly-configured"></a>Bekræft, at Virtuelle kataloger er konfigureret korrekt

Kontrollér nu, at OAuth er aktiveret korrekt i Exchange på alle virtuelle kataloger, Outlook bruger, ved at køre følgende kommandoer:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Kontrollér outputtet for at sikre, at **OAuth** er aktiveret på hver af disse VDirs, det vil se ud som dette (og det vigtigste at se på er 'OAuth'):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Hvis OAuth mangler på en server og en af de fire virtuelle mapper, skal du tilføje den ved hjælp af de relevante kommandoer, før du fortsætter ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) og [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>Bekræft, at objektet godkendelsesserver er til stede

Gå tilbage til den lokale Exchange Management Shell for denne sidste kommando. Nu kan du validere, om din lokale bruger har en post for udbyderen af godkendelse via softwareSTS-godkendelse:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

Dine output bør vise en godkendelsesserver for navneservere med et GUID, og den "aktiverede" tilstand skal være Sand. Hvis du ikke kan se dette, skal du downloade og køre den nyeste version af guiden Hybridkonfiguration.

> [!NOTE]
> I tilfælde af at EXCH er i hybrid med flere lejere **, bør** dit output vise én AuthServer af `EvoSts - {GUID}` navnet for hver lejer i hybrid med EXCH,  og den aktiverede tilstand skal være Sand for alle disse AuthServer-objekter.

> [!IMPORTANT]
> Hvis du kører Exchange 2010 i dit miljø, oprettes godkendelsesudbyderen ikke.

## <a name="enable-hma"></a>Aktivér HMA

Kør følgende kommando i Exchange Management Shell, lokal, \<GUID\> der erstatter i kommandolinjen med strengen i dit miljø:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> I ældre versioner af guiden Hybridkonfiguration blev hybrid-godkendelsesserveren ganske enkelt navngivet hybridSTS uden en tilknyttet GUID. Der er ingen handling, du skal udføre, du skal blot redigere kommandolinjen ovenfor for at afspejle dette ved at fjerne GUID-delen af kommandoen:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

Hvis EXCH-versionen er Exchange 2016 (CU18 eller nyere) eller Exchange 2019 (CU7 eller nyere), og hybrid blev konfigureret med HCW downloadet efter september 2020, skal du køre følgende kommando i den lokale Exchange Management Shell:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> I tilfælde af at EXCH er i hybrid med flere lejere **, er** der flere AuthServer-objekter i EXCH med domæner, der svarer til hver lejer.  **Flaget IsDefaultAuthorizationEndpoint** skal være angivet til sand (ved hjælp af **IsDefaultAuthorizationEndpoint-cmdlet'et**) for et af disse AuthServer-objekter. Dette flag kan ikke indstilles til sand for alle Authserver-objekterne, og HMA vil være aktiveret, selvom et af disse AuthServer-objekters **IsDefaultAuthorizationEndpoint-flag** er angivet til sand.
> 
> For **DomainName-parameteren** skal du bruge værdien for lejerdomænet, som normalt er i formularen `contoso.onmicrosoft.com`.

## <a name="verify"></a>Bekræft

Når du aktiverer HMA, bruger en klients næste logon det nye godkendelsesflow. Bemærk, at kun aktivering af HMA ikke udløser en genautentiering for nogen klient, og det kan tage et stykke tid, Exchange vælger de nye indstillinger.

Du skal også holde CTRL-tasten nede, samtidig med at du højreklikker på ikonet for Outlook-klienten (også i proceslinjen Windows-meddelelser), og klikke på "Forbindelsesstatus". Se efter klientens SMTP-adresse mod en **Authn-type** `Bearer\*`, som repræsenterer den iOAuth-token, der bruges i OAuth.

> [!NOTE]
> Har du brug for at Skype for Business med HMA? Du skal bruge to artikler: en, der viser [understøttede topologier](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported), og en, der viser [dig, hvordan du laver konfigurationen](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>Brug af hybrid moderne godkendelse Outlook til iOS og Android

Hvis du er lokal kunde, der bruger Exchange-server på TCP 443, skal du tillade netværkstrafik fra følgende IP-områder:

```console
52.125.128.0/20
52.127.96.0/23
```

Disse IP-adresseintervaller er også dokumenteret i Yderligere slutpunkter, der ikke er inkluderet [i Office 365 IP-adresse og URL-webadresse](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>Relaterede emner

[Konfigurationskrav til moderne godkendelse til overgang fra Office 365 dedikeret/ITAR til vNext](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
