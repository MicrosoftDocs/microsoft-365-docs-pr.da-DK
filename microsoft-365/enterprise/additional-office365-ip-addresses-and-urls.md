---
title: Andre slutpunkter, der ikke er inkluderet i Office 365 IP-adresse og URL-webtjeneste
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 01/31/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: ''
description: 'Oversigt: Den nye slutpunktswebtjeneste indeholder ikke nogle få slutpunkter til bestemte scenarier.'
hideEdit: true
ms.openlocfilehash: 0453efbea7957c3cf859c59da7a2cff7db04b4f0
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/01/2022
ms.locfileid: "63601604"
---
# <a name="other-endpoints-not-included-in-the-office-365-ip-address-and-url-web-service"></a>Andre slutpunkter, der ikke er inkluderet i Office 365 IP-adresse og URL-webtjeneste

Nogle netværksslutpunkter er tidligere blevet publiceret og er ikke medtaget i [den Office 365 IP-adresse og URL-webtjeneste](microsoft-365-ip-web-service.md). Webtjenesten udgiver netværksslutpunkter, der er nødvendige for at kunne oprette Office 365 på tværs af et virksomhedsperimeternetværk. Dette omfang omfatter i øjeblikket ikke:

1. Netværksforbindelse, der kan være påkrævet fra et Microsoft-datacenter til et kundenetværk (indgående hybridservernetværkstrafik).
2. Netværksforbindelse fra servere på et kundenetværk på tværs af virksomhedens perimeter (udgående servernetværkstrafik).
3. Ualmindelige scenarier for krav til netværksforbindelser fra en bruger.
4. Krav til forbindelse til DNS-løsning (ikke angivet nedenfor).
5. Internet Explorer eller Microsoft Edge websteder, der er tillid til.

Bortset fra DNS er disse forekomster alle valgfri for de fleste kunder, medmindre du har brug for det specifikke scenarie, der er beskrevet.

<br>

****

|Række|Formål|Destination|Type|
|---|---|---|---|
|1|**[Importtjeneste](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) til PST- og filimport**|Se [importtjenesten for at](https://support.office.com/article/use-network-upload-to-import-your-organization-pst-files-to-office-365-103f940c-0468-4e1a-b527-cc8ad13a5ea6) få flere krav.|Ualmindeligt scenarie med udgående trafik|
|2|**[Microsoft Support- og genoprettelsesassistent til Office 365](https://diagnostics.office.com/#/)**|<https://autodiscover.outlook.com> <br> <https://officecdn.microsoft.com> <br> <https://api.diagnostics.office.com> <br> <https://apibasic.diagnostics.office.com> <br> <https://autodiscover-s.outlook.com> <br> <https://cloudcheckenabler.azurewebsites.net> <br> <https://login.live.com> <br> <https://login.microsoftonline.com> <br> <https://login.windows.net> <br> <https://o365diagtelemetry.trafficmanager.net> <br> <https://odc.officeapps.live.com> <br> <https://offcatedge.azureedge.net> <br> <https://officeapps.live.com> <br> <https://outlook.office365.com> <br> <https://outlookdiagnostics.azureedge.net>|Udgående servertrafik|
|3|**Azure AD Forbind (w/SSO-indstilling)** <p> WinRM & remote PowerShell|Kunde-STS-miljø (AD FS-server og AD FS-proxy) \| TCP-port 80 & 443|Indgående servertrafik|
|4|**STS** , f.eks. AD FS-proxyserver(e) (kun for kunder, der er medlem af et organisationsnetværk)|Kunde-STS-porte (f.eks. AD FS-proxy) \| TCP 443 eller TCP 49443 med klient-TLS|Indgående servertrafik|
|5|**[Exchange Online integration med Unified Messaging/SBC](/exchange/voice-mail-unified-messaging/telephone-system-integration-with-um/configuration-notes-for-session-border-controllers)**|Tovejs mellem den lokale sessionsgrænsecontroller og \*.um.outlook.com|Udelukkende udgående servertrafik|
|6|**Postkasseoverførsel**<p>Når postkasseoverflytningen startes fra den lokale [Exchange Hybrid](/exchange/exchange-deployment-assistant) til Office 365, opretter Office 365 forbindelse til din publicerede Exchange-webtjenesteserver (EWS)/Mailbox Replication Services (MRS). Hvis du skal bruge de NAT IP-adresser, der bruges af Exchange Online-servere til at begrænse indgående forbindelser fra bestemte kilde-IP-områder, er de angivet i [Office 365 URL & IP-områder](urls-and-ip-address-ranges.md) under tjenesteområdet "Exchange Online". <p> Vær forsigtig for at sikre, at adgang til publicerede EWS-slutpunkter som f.eks. OWA ikke påvirkes ved at sikre, at MRS-proxyen løses til en separat FQDN og offentlig IP-adresse, før TCP 443-forbindelser fra bestemte kilde-IP-områder begrænses.|Kundens lokale EWS/MRS-proxy <br> TCP-port 443|Indgående servertrafik|
|7|**[Exchange hybride](/exchange/exchange-deployment-assistant) sameksistensfunktioner som** f.eks. deling af ledig/optaget tid.|Lokal kundeserver Exchange|Indgående servertrafik|
|8|**[Exchange hybrid proxygodkendelse](/exchange/exchange-deployment-assistant)**|STS i kundens lokale miljø|Indgående servertrafik|
|9|Bruges til at [konfigurere Exchange hybrid](/exchange/exchange-deployment-assistant) ved hjælp Exchange **[guiden Hybridkonfiguration](/exchange/hybrid-configuration-wizard)** <p> Bemærk! Disse slutpunkter er kun nødvendige for at konfigurere Exchange hybrid|domains.live.com PÅ TCP-portene 80 & 443, kun påkrævet til Exchange 2010 SP3-hybridkonfiguration <p> GCC Høj IP-adresser for DoD: 40.118.209.192/32; 168.62.190.41/32 <p> Verdensomspændende kommercielle & GCC: \*.store.core.windows.net; asl.configure.office.com; tds.configure.office.com; mshybridservice.trafficmanager.net ; <br> aka.ms/hybridwizard; <br> \*shcwreleaseprod.blob.core.windows.net/shcw/;|Udelukkende udgående servertrafik|
|10|Tjenesten **Autodetect bruges** i Exchange [hybridscenarier](/exchange/exchange-deployment-assistant) med [hybrid moderne godkendelse Outlook til iOS og Android](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) <p> `*.acompli.net` <br> `*.outlookmobile.com` <br> `*.outlookmobile.us` <br> `52.125.128.0/20` <br> `52.127.96.0/23`|Lokal kundeserver Exchange TCP 443|Indgående servertrafik|
|11|**Exchange hybrid Azure AD-godkendelse**|*.msappproxy.net|UDELUKKENDE TCP-trafik til udgående server|
|12|Skype for Business i Office 2016 omfatter **videobaseret skærmdeling**, som bruger UDP-porte. Tidligere Skype for Business i Office 2013 og tidligere brugt RDP over TCP-port 443.|TCP-port 443 åbnes til 52.112.0.0/14|Skype for Business ældre klientversioner i Office 2013 og tidligere versioner|
|13|**Skype for Business en hybrid lokal serverforbindelse til** Skype for Business Online|13.107.64.0/18, 52.112.0.0/14 <br> UDP-porte 50.000-59.999 <br> TCP-porte 50.000-59.999; 5061|Skype for Business lokal server – udgående forbindelse|
|14|**Cloud PSTN** med lokal hybridforbindelse kræver netværksforbindelse, der er åben for lokale værter. Få mere at vide om Skype for Business Online-hybridkonfigurationer|Se [Planlæg hybridforbindelse mellem Skype for Business Server og Office 365](/skypeforbusiness/hybrid/plan-hybrid-connectivity)|Skype for Business lokal hybrid indgående|
|15|**Godkendelses- og identitets-FQDN'er** <p> FQDN'et `secure.aadcdn.microsoftonline-p.com` skal være i klientens Internet Explorer (IE) eller zonen Pålidelige websteder i Edge for at fungere.||Websteder, du har tillid til|
|16|**Microsoft Teams FQDN'er** <p> Hvis du bruger Internet Explorer eller Microsoft Edge, skal du aktivere førsteparts- og tredjepartscookies og føje FQDN'er for Teams til dine websteder, du har tillid til. Dette er i tillæg til de pakke brede FQDN'er, CDN'er og telemetrien, der er angivet i række 14. Se [Kendte problemer for Microsoft Teams](/microsoftteams/known-issues) for at få flere oplysninger.||Websteder, du har tillid til|
|17|**SharePoint Online og OneDrive for Business FQDN'er** <p> Alle ".sharepoint.com"-FQDN'er med "\<tenant\>" i FQDN'et skal være i zonen Pålidelige websteder i IE eller Edge for at fungere. Ud over de pakke brede FQDN'er, CDN'er og telemetrien, der er angivet i række 14, skal du også tilføje disse slutpunkter.||Websteder, du har tillid til|
|18|**Yammer**  <br> Yammer er kun tilgængeligt i browseren og kræver, at den godkendte bruger sendes gennem en proxy. Alle Yammer FQDN'er skal være i zonen Pålidelige websteder i kundens IE eller Edge for at fungere.||Websteder, du har tillid til|
|19|Brug **[Azure AD Forbind](/azure/active-directory/hybrid/)** til at synkronisere lokale brugerkonti med Azure AD.|Se [Påkrævede porte og protokoller for hybrididentitet](/azure/active-directory/hybrid/reference-connect-ports), [Fejlfinding af Azure AD-forbindelse](/azure/active-directory/hybrid/tshoot-connect-connectivity) [og installation Forbind Azure AD-agent](/azure/active-directory/hybrid/how-to-connect-health-agent-install#outbound-connectivity-to-the-azure-service-endpoints).|Udelukkende udgående servertrafik|
|20|**[Azure AD Forbind](/azure/active-directory/hybrid/)** 21 ViaNet i Kina for at synkronisere lokale brugerkonti til Azure AD.|\*.digicert.com:80 <BR> \*.entrust.net:80 <BR> \*.chinacloudapi.cn:443 <br> secure.aadcdn.partner.microsoftonline-p.cn:443 <br> \*.partner.microsoftonline.cn:443 <p> Se også [Fejlfinding i forbindelse med ingress med Azure AD-forbindelsesproblemer](https://docs.azure.cn/zh-cn/active-directory/hybrid/tshoot-connect-connectivity).|Udelukkende udgående servertrafik|
|21|**Microsoft Stream** (skal bruge Azure AD-brugertoken). <br> Office 365 Worldwide (herunder GCC)|\*.cloudapp.net <br> \*.api.microsoftstream.com <br> \*.notification.api.microsoftstream.com <br> amp.azure.net <br> api.microsoftstream.com <br> az416426.vo.msecnd.net <br> s0.assets-yammer.com <br> vortex.data.microsoft.com <br> web.microsoftstream.com <br> TCP-port 443|Indgående servertrafik|
|22|Brug **MFA-server** til anmodninger om multifaktorgodkendelse, både nye installationer af serveren og konfiguration Active Directory-domæneservices (AD DS).|Se [Introduktion til Azure AD Multi-Factor Authentication Server](/azure/active-directory/authentication/howto-mfaserver-deploy#plan-your-deployment).|Udelukkende udgående servertrafik|
|23|**Meddelelser om Graph microsoft-ændringer** <p> Udviklere kan bruge [meddelelser om ændringer](/graph/webhooks?context=graph%2fapi%2f1.0&view=graph-rest-1.0) til at abonnere på begivenheder i Microsoft Graph.|Public Cloud: 52.159.23.209, 52.159.17.84, 52.147.213.251, 52.147.213.181, 13.85.192.59, 13.85.192.123, 13.89.108.233, 13.89.104.147, 20.96.21.67, 20.69.245.215, 137.135.11.161, 137.135.11.116, 52.159.107.50, 52.159.107.4, 52.229.38.131, 52.183.67.212, 52.142.114.29, 52.142.115.31, 51.124.75.43, 51.124.73.177, 20.44.210.83, 20.44.210.146, 40.80.232.177, 40.80.232.118, 20.48.12.75, 20.48.11.201, 104.215.13.23, 104.215.6.169, 52.148.24.136, 52.148.27.39, 40.76.162.99, 40.76.162.42 , 40.74.203.28, 40.74.203.27, 13.86.37.15, 52.154.246.238, 20.96.21.98, 20.96.21.115, 137.135.11.222, 137.135.11.250, 52.159.109.205, 52.159.102.72, 52.151.30.78, 52.191.173.85, 51.104.159.213, 51.104.159.181, 51.138.90.7, 51.138.90.52, 52.148.115.48, 52.148.114.238, 40.80.233.14, 40.80.239.196, 20.48.14.35, 20.48.15.147, 104.215.18.55, 104.215.12.254, 20.199.102.157, 20.199.102.73, 13.87.81.123, 13.87.81.35, 20.111.9.46, 20.111.9.77, 13.87.81.133, 13.87.81.141 <p> Microsoft Cloud for US Government: 52.244.33.45, 52.244.35.174, 52.243.157.104, 52.243.157.105, 52.182.25.254, 52.182.25.110, 52.181.25.67, 52.181.25.66, 52.244.111.156, 52.244.111.170, 52.243.147.249, 52.243.148.1 9, 52.182.32.51, 52.182.32.143, 52.181.24.199, 52.181.24.220 <p> Microsoft Cloud China drevet af 21Vianet: 42.159.72.35, 42.159.72.47, 42.159.180.55, 42.159.180.56, 40.125.138.23, 40.125.136.69, 40.72.155.199, 40.72.155.216 <br> TCP-port 443 <p> Bemærk! Udviklere kan angive forskellige porte, når de opretter abonnementer.|Indgående servertrafik|
|24|**Statusindikator for netværksforbindelse**<p>Bruges af Windows 10 og 11 til at afgøre, om computeren har forbindelse til internettet (gælder ikke for ikke-Windows klienter). Når denne URL-adresse ikke kan nås, antager Windows, at den ikke har forbindelse til internettet, og M365 Apps for Enterprise vil ikke forsøge at bekræfte aktiveringsstatus, hvilket medfører, at forbindelser til Exchange og andre tjenester mislykkes.|www.mstfconnecttest.com <br> 13.107.4.52<p>Se også [Administrer forbindelsesslutpunkter for Windows 11 Enterprise](/windows/privacy/manage-windows-11-endpoints) og [Administrer forbindelsesslutpunkter for Windows 10 Enterprise, version 21H2](/windows/privacy/manage-windows-21h2-endpoints).|Udelukkende udgående servertrafik|
|

## <a name="related-topics"></a>Relaterede emner

[Administrere Office 365 slutpunkter](managing-office-365-endpoints.md)
  
[Overvåg Microsoft 365 forbindelse](./monitor-connectivity.md)
  
[Klientforbindelse](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Netværk, der kan levere indhold](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Azure IP-områder og tjenestemærker – Offentlig sky](https://www.microsoft.com/download/details.aspx?id=56519)

[Azure IP Ranges and Service Tags – US Government Cloud](https://www.microsoft.com/download/details.aspx?id=57063)

[Azure IP-områder og tjenestemærker – Germany Cloud](https://www.microsoft.com/download/details.aspx?id=57064)

[Azure IP Ranges and Service Tags – China Cloud](https://www.microsoft.com/download/details.aspx?id=57062)
  
[Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602)
