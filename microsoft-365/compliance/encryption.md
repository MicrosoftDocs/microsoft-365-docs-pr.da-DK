---
title: Kryptering i Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 0a322724-08ca-43db-b69a-afbfa20484cd
ms.collection:
- M365-security-compliance
- Strat_O365_IP
- m365solution-mip
- m365initiative-compliance
description: Med Office 365 krypteres dit indhold som inaktivt og under overførsel med den stærkeste kryptering, de protokoller og teknologier, der er tilgængelige. Få et overblik over kryptering i Office 365.
ms.openlocfilehash: 5b7b0f9fecbcbb6150eb56e19757c954aeb3e812
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637467"
---
# <a name="encryption"></a>Kryptering

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kryptering er en vigtig del af din strategi til beskyttelse af filer og beskyttelse af oplysninger. Denne artikel indeholder en oversigt over kryptering af Office 365. Få hjælp til krypteringsopgaver, f.eks. hvordan du konfigurerer kryptering for din organisation, og hvordan du beskytter Office dokumenter med adgangskode.
  
- Du kan finde oplysninger om certifikater og teknologier som TLS [under Tekniske referenceoplysninger om kryptering i Office 365](technical-reference-details-about-encryption.md).

- Du kan få oplysninger om, hvordan du konfigurerer eller konfigurerer kryptering for din organisation, [under Konfigurer kryptering i Office 365 Enterprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Hvad er kryptering, og hvordan fungerer den i Office 365?

Krypteringsprocessen koder dine data (kaldet almindelig tekst) til kryptering. I modsætning til almindelig tekst kan kryptering ikke bruges af personer eller computere, medmindre og før krypteringen af krypteringen. Dekryptering kræver en krypteringsnøgle, som kun godkendte brugere har. Kryptering hjælper med at sikre, at kun godkendte modtagere kan dekryptere dit indhold. Indhold omfatter filer, mails, kalenderposter osv.
  
Kryptering af sig selv forhindrer ikke indholdsfangning. Kryptering er en del af en større strategi for beskyttelse af oplysninger for din organisation. Ved hjælp af kryptering hjælper du med at sikre, at det kun er autoriserede parter, der kan bruge de krypterede data.
  
Du kan have flere krypteringslag på plads på samme tid. Du kan f.eks. kryptere mails og de kommunikationskanaler, som dine mailflows bruger. Med Office 365 krypteres dine data inaktive og under overførsel ved hjælp af flere stærke krypteringsprotokoller og teknologier, der omfatter TLS/SSL (Transport Layer Security/Secure Sockets Layer), IPSec (Internet Protocol Security) og Advanced Encryption Standard (AES).
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Kryptering af inaktive data og data under overførsel

 **Eksempler på inaktive data** omfatter filer, som du har uploadet til et SharePoint bibliotek, Project Online data, dokumenter, du har uploadet i et Skype for Business møde, mails og vedhæftede filer, som du har gemt i mapper i din postkasse, og filer, du har uploadet til OneDrive for Business.
  
 **Eksempler på data under overførsel** omfatter mails, der er ved at blive leveret, eller samtaler, der finder sted i et onlinemøde. I Office 365 overføres data, når en brugers enhed kommunikerer med en Microsoft-server, eller når en Microsoft-server kommunikerer med en anden server.
  
Med Office 365 arbejder flere lag og typer kryptering sammen for at sikre dine data. Følgende tabel indeholder nogle eksempler med links til yderligere oplysninger.
  
|**Typer af indhold**|**Krypteringsteknologier**|**Ressourcer til at få mere at vide**|
|:-----|:-----|:-----|
|Filer på en enhed. Disse filer kan omfatte mails, der er gemt i en mappe, Office dokumenter, der er gemt på en computer, tablet eller telefon, eller data, der er gemt i Microsoft-cloudmiljøet.  <br/> |BitLocker i Microsoft-datacentre. BitLocker kan også bruges på klientcomputere, f.eks. Windows computere og tablets  <br/> Distributed Key Manager (DKM) i Microsoft-datacentre  <br/> Kundenøgle til Microsoft 365  <br/> |[Windows IT Center: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Microsoft Center for sikkerhed og rettighedsadministration: Kryptering](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Serie af cloudsikkerhedskontroller: Kryptering af restdata](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Sådan beskytter Exchange Online dine mailhemmeligheder](exchange-online-secures-email-secrets.md) <br/> [Tjenestekryptering med kundenøgle](customer-key-overview.md) <br/> |
|Filer, der er under overførsel mellem brugere. Disse filer kan omfatte Office dokumenter eller SharePoint listeelementer, der deles mellem brugere.  <br/> |TLS for filer under overførsel  <br/> |[Datakryptering i OneDrive for Business og SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype for Business Online: Sikkerhed og arkivering](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Mail under overførsel mellem modtagere. Denne mail indeholder mail, der hostes af Exchange Online.  <br/> |Microsoft Purview-meddelelseskryptering med Azure Rights Management, S/MIME og TLS til overførsel af mail  <br/> |[Meddelelsekryptering](ome.md) <br/> [Mailkryptering i Office 365](email-encryption.md) <br/> [Sådan anvender Exchange Online-brugere TLS til at sikre deres mailforbindelser i Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Chats, meddelelser og filer under overførsel mellem modtagere ved hjælp af Microsoft Teams. <br/> |Teams bruger TLS og MTLS til at kryptere chatbeskeder. Medietrafik krypteres ved hjælp af Secure RTP (SRTP). Teams bruger FIPS-kompatible algoritmer (Federal Information Processing Standard) til krypteringsnøgleudveksling. <br/> |[Kryptering af Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Hvad gør jeg, hvis jeg har brug for mere kontrol over kryptering for at opfylde kravene til sikkerhed og overholdelse af angivne standarder?

Microsoft 365 leverer Microsoft-administrerede løsninger til kryptering af diskenhed, filkryptering og postkassekryptering i Office 365. Derudover leverer Microsoft krypteringsløsninger, som du kan administrere og styre. Disse krypteringsløsninger er bygget på Azure.
  
Du kan få mere at vide i følgende ressourcer:
  
- [Hvad er Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)

- [Aktivér Rights Management i Administration](../enterprise/activate-rms-in-microsoft-365.md)

- [Konfigurer IRM (Information Rights Management) i SharePoint Administration](set-up-irm-in-sp-admin-center.md)

- [Tjenestekryptering med Microsoft Purview-kundenøgle](customer-key-overview.md)

- [Kryptering med dobbelt nøgle](double-key-encryption.md)

## <a name="how-do-i"></a>Hvordan ... jeg

|**Sådan gør du denne opgave**|**Se disse ressourcer**|
|:-----|:-----|
|Konfigurer kryptering for min organisation|[Konfigurer kryptering i Office 365 Enterprise](set-up-encryption.md)|
|Få vist oplysninger om certifikater, teknologier og TLS-krypteringspakker|[Tekniske oplysninger om kryptering](technical-reference-details-about-encryption.md)|
|Arbejd med krypterede meddelelser på en mobilenhed|[Få vist krypterede meddelelser på din Android-enhedFå](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) [vist krypterede meddelelser på din iPhone eller iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Kryptér et dokument ved hjælp af adgangskodebeskyttelse. (Adgangskodebeskyttelse understøttes ikke i en browser. Brug skrivebordsversioner af Word, Excel og PowerPoint til adgangskodebeskyttelse. |[Tilføj eller fjern beskyttelse i dit dokument, din projektmappe eller præsentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Vælg afsnittet **Tilføj beskyttelse** , og se derefter **Kryptér med adgangskode**.|
|Fjern kryptering fra et dokument|[Tilføj eller fjern beskyttelse i dit dokument, din projektmappe eller præsentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Vælg afsnittet **Fjern beskyttelse** , og se derefter **Fjern adgangskodekryptering**.  |

## <a name="related-topics"></a>Relaterede emner

[Planlæg Microsoft 365 funktioner til beskyttelse af sikkerhed og oplysninger](plan-for-security-and-compliance.md)

[Bedste praksis for sikring af Microsoft 365 til forretningsplaner](/office365/admin/security-and-compliance/secure-your-business-data)

[Microsoft Stream kryptering og afspilningsflow på videoniveau](/stream/network-overview#video-level-encryption-and-playback-flow)
