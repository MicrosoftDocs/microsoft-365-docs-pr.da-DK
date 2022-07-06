---
title: Sådan bruger Exchange Online TLS til at sikre mailforbindelser
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
description: Få mere at vide om, hvordan Exchange Online og Microsoft 365 bruger TLS (Transport Layer Security) og FS (Forward Secrecy) til at sikre mailkommunikation. Få også oplysninger om det certifikat, der er udstedt af Microsoft til Exchange Online.
ms.openlocfilehash: 93f71e38e3063aeec0c423dbfea25ac463a3e46f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641554"
---
# <a name="how-exchange-online-uses-tls-to-secure-email-connections"></a>Sådan bruger Exchange Online TLS til at sikre mailforbindelser

Få mere at vide om, hvordan Exchange Online og Microsoft 365 bruger TLS (Transport Layer Security) og FS (Forward Secrecy) til at sikre mailkommunikation. Indeholder også oplysninger om det certifikat, der er udstedt af Microsoft til Exchange Online.
  
## <a name="tls-basics-for-microsoft-365-and-exchange-online"></a>Grundlæggende om TLS til Microsoft 365 og Exchange Online

TLS (Transport Layer Security) og SSL, der kom før TLS, er kryptografiske protokoller, der sikrer kommunikation via et netværk ved hjælp af sikkerhedscertifikater til at kryptere en forbindelse mellem computere. TLS tilsidesætter SSL (Secure Sockets Layer) og kaldes ofte SSL 3.1. Exchange Online bruger TLS til at kryptere forbindelserne mellem Exchange-servere og forbindelserne mellem Exchange-servere og andre servere, f.eks. dine Exchange-servere i det lokale miljø eller modtagernes mailservere. Når forbindelsen er krypteret, sendes alle data, der sendes via den pågældende forbindelse, via den krypterede kanal. Men hvis du videresender en meddelelse, der blev sendt via en TLS-krypteret forbindelse, krypteres meddelelsen ikke nødvendigvis. TLS krypterer ikke meddelelsen, kun forbindelsen.
  
Hvis du vil kryptere meddelelsen, skal du bruge en krypteringsteknologi, der krypterer meddelelsens indhold. Du kan f.eks. bruge Microsoft Purview-meddelelseskryptering eller S/MIME. Se [Mailkryptering i Office 365](email-encryption.md) og [Meddelelsekryptering](ome.md) for at få oplysninger om meddelelsekryptering i Office 365.
  
Brug TLS i situationer, hvor du vil konfigurere en sikker kanal til korrespondance mellem Microsoft og din lokale organisation eller en anden organisation, f.eks. en partner. Exchange Online forsøger altid at bruge TLS først til at sikre din mail, men kan ikke, hvis den anden part ikke tilbyder TLS-sikkerhed. Fortsæt med at læse for at finde ud af, hvordan du kan sikre alle mails til dine lokale servere eller vigtige partnere ved hjælp af *connectors*.

Microsoft har frarådet TLS-version 1.0 og 1.1 i [Office 365](tls-1.0-and-1.1-deprecation-for-office-365.md) og [Office 365 GCC](tls-1-2-in-office-365-gcc.md) for at levere den bedste kryptering til vores kunder. Du kan dog fortsætte med at bruge en ukrypteret SMTP-forbindelse uden nogen TLS. Vi anbefaler ikke overførsel af mail uden kryptering.  
  
## <a name="how-exchange-online-uses-tls-between-exchange-online-customers"></a>Sådan bruger Exchange Online TLS mellem Exchange Online kunder

Exchange Online servere krypterer altid forbindelser til andre Exchange Online servere i vores datacentre med TLS 1.2. Når du sender en meddelelse til en modtager i din organisation, sender Exchange Online automatisk meddelelsen via en krypteret forbindelse ved hjælp af TLS. Exchange Online sender også mail, som du sender til andre kunder, via krypterede forbindelser ved hjælp af TLS, der er sikret ved hjælp af Videresendelseshemmelighed.
  
## <a name="how-microsoft-365-uses-tls-between-microsoft-365-and-external-trusted-partners"></a>Sådan bruger Microsoft 365 TLS mellem Microsoft 365 og eksterne partnere, der er tillid til

Som standard bruger Exchange Online altid *opportunistisk TLS*. Opportunistisk TLS betyder, at Exchange Online altid forsøger at kryptere forbindelser med den mest sikre version af TLS først og derefter arbejder sig ned ad listen over TLS-ciffer, indtil den finder en, som begge parter kan blive enige om. Medmindre du har konfigureret Exchange Online til at sikre, at meddelelser til den pågældende modtager skal bruge sikre forbindelser, sendes meddelelsen som standard uden kryptering, hvis modtagerorganisationen ikke understøtter TLS-kryptering. Opportunistisk TLS er tilstrækkeligt for de fleste virksomheder. Men for virksomheder, der har overholdelseskrav, f.eks. medicinske, bankmæssige eller offentlige organisationer, kan du konfigurere Exchange Online til at kræve eller gennemtvinge TLS. Du kan finde en vejledning [under Konfigurer mailflow ved hjælp af connectors i Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
Hvis du beslutter at konfigurere TLS mellem din organisation og en partnerorganisation, der er tillid til, kan Exchange Online bruge *tvungen TLS* til at oprette kommunikationskanaler, der er tillid til. Tvungen TLS kræver, at din partnerorganisation godkender for at Exchange Online med et sikkerhedscertifikat for at sende mail til dig. Din partner skal administrere sine egne certifikater. Exchange Online bruger forbindelser til at beskytte meddelelser, som du sender fra uautoriseret adgang, før de ankommer til modtagerens mailudbyder. Du kan få oplysninger om, hvordan du bruger forbindelser til at konfigurere mailflow, under [Konfigurer mailflow ved hjælp af forbindelser i Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).
  
## <a name="tls-and-hybrid-exchange-server-deployments"></a>TLS- og hybridinstallationer Exchange Server

Hvis du administrerer en hybrid Exchange-installation, skal exchange-serveren i det lokale miljø godkende Microsoft 365 ved hjælp af et sikkerhedscertifikat for at sende mail til modtagere, hvis postkasser kun er i Office 365. Derfor skal du administrere dine egne sikkerhedscertifikater for dine Exchange-servere i det lokale miljø. Du skal også gemme og vedligeholde disse servercertifikater på en sikker måde. Du kan få flere oplysninger om administration af certifikater i hybridinstallationer under [Certifikatkrav til hybridinstallationer](/exchange/certificate-requirements).
  
## <a name="how-to-set-up-forced-tls-for-exchange-online-in-office-365"></a>Sådan konfigurerer du tvungen TLS for Exchange Online i Office 365

For Exchange Online kunder skal du konfigurere mere end én connector, der kræver TLS, for at tvinge TLS til at arbejde for at sikre alle dine sendte og modtagne mails. Du skal bruge én connector til meddelelser, der er sendt til brugerpostkasser, og en anden connector til meddelelser, der er sendt fra brugerpostkasser. Opret disse connectorer i Exchange Administration i Office 365. Du kan finde en vejledning [under Konfigurer mailflow ved hjælp af connectors i Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

## <a name="tls-certificate-information-for-exchange-online"></a>TLS-certifikatoplysninger for Exchange Online

De certifikatoplysninger, der bruges af Exchange Online, er beskrevet i følgende tabel. Hvis din forretningspartner konfigurerer tvungne TLS på deres mailserver, skal du give dem disse oplysninger. Af sikkerhedsmæssige årsager ændres vores certifikater fra tid til anden. Det aktuelle certifikat er gyldigt fra den 24. september 2020.

### <a name="current-certificate-information-valid-from-september-24-2020"></a>Aktuelle certifikatoplysninger, der er gyldige fra den 24. september 2020
  
| Attribut | Værdi |
|:-----|:-----|
|Rodudsteder for nøglecenter|DigiCert CA – 1|
|Certifikatnavn|mail.protection.outlook.com|
|Organisation|Microsoft Corporation|
|Organisationsenhed|www.digicert.com|
|Certifikatnøglestyrke|2048|

## <a name="get-more-information-about-tls-certificates-and-microsoft-365-and-download-certificates"></a>Få flere oplysninger om TLS, certifikater og Microsoft 365, og download certifikater

[Microsoft 365-krypteringskæder og certifikatoverførsler](encryption-office-365-certificate-chains.md)

[Microsoft 365-krypteringskæder og certifikatoverførsler – DOD og GCC High](encryption-office-365-certificate-chains-itar.md)

Du kan finde en liste over understøttede krypteringspakker under [Oplysninger om kryptering i teknisk reference](technical-reference-details-about-encryption.md).
  
[Konfigurer forbindelser til et sikkert mailflow med en partnerorganisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)
  
[Forbindelser med forbedret mailsikkerhed](/previous-versions/exchange-server/exchange-150/dn942516(v=exchg.150))
  
[Kryptering i Microsoft 365](encryption.md)
