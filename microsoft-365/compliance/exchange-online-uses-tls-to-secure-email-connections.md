---
title: Sådan Exchange Online du bruger TLS (Transport Layer Security) til at sikre mailforbindelser
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/08/2021
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4cde0cda-3430-4dc0-b489-f2c0736c929f
ms.collection:
- M365-security-compliance
- Strat_O365_IP
description: Lær, Exchange Online og Microsoft 365 bruger TLS (Transport Layer Security) og fremadrettet social sikring til sikker mailkommunikation. Få også oplysninger om det certifikat, der er udstedt af Microsoft til Exchange Online.
ms.openlocfilehash: 1caf4a8425f4a8e7c340e8a52d785027e99a1618
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588928"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Sådan Exchange Online du bruger TLS til at sikre mailforbindelser

Lær, Exchange Online og Microsoft 365 bruger TLS (Transport Layer Security) og fremadrettet social sikring til sikker mailkommunikation. Indeholder også oplysninger om det certifikat, der er udstedt af Microsoft til Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Grundlæggende om TLS til Microsoft 365 og Exchange Online

Transport Layer Security (TLS) og SSL, der kom før TLS, er krypterede protokoller, som sikrer kommunikationen via et netværk ved hjælp af sikkerhedscertifikater til at kryptere en forbindelse mellem computere. TLS erstatter Secure Sockets Layer (SSL) og kaldes ofte SSL 3.1. Exchange Online bruger TLS til at kryptere forbindelserne mellem Exchange-servere og forbindelserne mellem Exchange-servere og andre servere, f.eks. dine lokale Exchange-servere eller modtagernes mailservere. Når forbindelsen er krypteret, sendes alle data, der sendes via den pågældende forbindelse, via den krypterede kanal. Men hvis du videresender en meddelelse, der blev sendt via en TLS-krypteret forbindelse, er den pågældende meddelelse ikke nødvendigvis krypteret. TLS krypterer ikke meddelelsen, kun forbindelsen.
  
Hvis du vil kryptere meddelelsen, skal du bruge en krypteringsteknologi, der krypterer meddelelsens indhold. Du kan f.eks. bruge Office eller S/MIME. Se [Mailkryptering i Office 365](email-encryption.md) [og Office 365-meddelelseskryptering (OME),](ome.md) hvis du vil have mere at vide om meddelelseskryptering Office 365.
  
Brug TLS i situationer, hvor du vil oprette en sikker kanal for korrespondance mellem Microsoft og din lokale organisation eller en anden organisation, f.eks. en partner. Exchange Online altid forsøger at bruge TLS først for at sikre din mail, men kan ikke, hvis den anden part ikke tilbyder TLS-sikkerhed. Læs videre for at finde ud af, hvordan du kan sikre alle mails til dine lokale servere eller vigtige partnere ved hjælp *af forbindelser*.

For at levere den bedste i klassen-kryptering til vores kunder har Microsoft forældet TLS-versionerne (Transport Layer Security) 1.0 og 1.1 [i Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) [og Office 365 GCC](tls-1-2-in-office-365-gcc.md). Du kan dog fortsætte med at bruge en ikke-krypteret SMTP-forbindelse uden nogen TLS. Vi anbefaler ikke mailoverførsel uden kryptering.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Sådan Exchange Online TLS mellem Exchange Online kunder

Exchange Online-servere krypterer altid forbindelser til Exchange Online servere i vores datacentre med TLS 1.2. Når du sender en meddelelse til en modtager, der er inden for din organisation, Exchange Online automatisk meddelelsen via en krypteret forbindelse ved hjælp af TLS. Exchange Online sender også mails, som du sender til andre kunder via krypterede forbindelser ved hjælp af TLS, der er sikret ved hjælp af videresendte mails.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Sådan Microsoft 365 TLS mellem Microsoft 365 og eksterne partnere, der er tillid til

Som standard Exchange Online altid *opportunistisk TLS*. Opportunistisk TLS betyder, at Exchange Online altid forsøger at kryptere forbindelser med den mest sikre version af TLS først og derefter arbejder sig nedad på listen over TLS-krypteringer, indtil den finder en, som begge parter kan acceptere. Medmindre du har konfigureret Exchange Online til at sikre, at meddelelser til den pågældende modtager skal bruge sikre forbindelser, sendes meddelelsen som standard uden kryptering, hvis modtagerens organisation ikke understøtter TLS-kryptering. Opportunistic TLS er tilstrækkelig for de fleste virksomheder. Men for virksomheder, der har overholdelseskrav, som f.eks. læge-, bank- eller offentlige organisationer, kan du konfigurere Exchange Online til at kræve eller gennemtvinge TLS. Du kan finde en vejledning [i Konfigurere mailflow ved hjælp af forbindelser Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Hvis du beslutter dig for at konfigurere TLS mellem din organisation og en pålidelig partnerorganisation, kan Exchange Online bruge gennemtvungne *TLS* til at oprette kommunikationskanaler, der er tillid til. Tvungne TLS kræver, at din partnerorganisation godkender Exchange Online med et sikkerhedscertifikat for at sende mails til dig. Din partner skal administrere deres egne certifikater. Exchange Online bruger forbindelser til at beskytte meddelelser, du sender fra uautoriseret adgang, før de ankommer til modtagerens mailudbyder. Du kan finde oplysninger om brug af forbindelser til at konfigurere mailflow i [Konfigurer mailflow ved hjælp af forbindelser Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>TLS- og Exchange Server installationer

Hvis du administrerer en hybrid Exchange-installation, skal din lokale Exchange-server godkende til Microsoft 365 ved hjælp af et sikkerhedscertifikat til at sende mails til de modtagere, hvis postkasser kun er i Office 365. Derfor skal du administrere dine egne sikkerhedscertifikater til dine lokale Exchange servere. Du skal også sikkert gemme og vedligeholde disse servercertifikater. Du kan finde flere oplysninger om administration af certifikater i hybridinstallationer [under Certifikatkrav til hybridinstallationer](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Sådan konfigurerer du gennemtvungne TLS til Exchange Online i Office 365

For Exchange Online brugere skal du konfigurere mere end én forbindelse, der kræver TLS, for at tvungne TLS kan arbejde for at sikre alle dine sendte og modtagne mails. Du skal bruge én forbindelse til meddelelser, der sendes til brugerpostkasser, og en anden forbindelse til meddelelser, der sendes fra brugerpostkasser. Opret disse forbindelser i Exchange Administration i Office 365. Du kan finde en vejledning [i Konfigurere mailflow ved hjælp af forbindelser Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>Oplysninger om TLS-certifikat til Exchange Online

De certifikatoplysninger, der anvendes Exchange Online, er beskrevet i følgende tabel. Hvis din forretningspartner konfigurerer tvungne TLS på deres mailserver, skal du give disse oplysninger til dem. Af sikkerhedsmæssige årsager ændres vores certifikater fra tid til anden. Det aktuelle certifikat er gyldigt fra d. 24. september 2020.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>Aktuelle certifikatoplysninger gyldige fra 24. september 2020
  
| Attribut | Værdi |
|:-----|:-----|
|Rodudstedende nøglecenter|DigiCert CA – 1|
|Certifikatnavn|mail.protection.outlook.com|
|Organisation|Microsoft Corporation|
|Organisationsenhed|www.digicert.com|
|Nøglestyrke for certifikat|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>Få mere at vide om TLS, certifikater og Microsoft 365 og download certifikater

[Microsoft 365 krypteringskæder og downloads af certifikater](encryption-office-365-certificate-chains.md)

[Microsoft 365 krypteringskæder og downloads af certifikater - DOD og GCC High](encryption-office-365-certificate-chains-itar.md)

Du kan finde en liste over understøttede krypteringspakker under [Oplysninger om teknisk reference om kryptering](technical-reference-details-about-encryption.md).
  
[Konfigurer forbindelser til sikker mailflow med en partnerorganisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Forbindelser med forbedret mailsikkerhed](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Kryptering i Microsoft 365](encryption.md)
