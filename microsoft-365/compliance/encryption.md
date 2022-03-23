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
description: Med Office 365 er dit indhold krypteret under transport og under overførsel med den stærkeste kryptering, protokoller og de teknologier, der er tilgængelige. Få et overblik over kryptering i Office 365.
ms.openlocfilehash: a1ee73d7ded7a02cd7851081412d2403e0ca8f1d
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/26/2021
ms.locfileid: "63589524"
---
# <a name="encryption"></a>Kryptering

Kryptering er en vigtig del af din strategi for filbeskyttelse og informationsbeskyttelse. I denne artikel får du en oversigt over kryptering til Office 365. Få hjælp til krypteringsopgaver, f.eks. hvordan du konfigurerer kryptering for din organisation, og hvordan du beskytter dine Office dokumenter.
  
- Du kan finde oplysninger om certifikater og teknologier som f.eks. TLS under [Tekniske referenceoplysninger om kryptering Office 365](technical-reference-details-about-encryption.md).

- Hvis du vil have mere at vide om, hvordan du konfigurerer eller konfigurerer kryptering for organisationen, skal du [se Konfigurer kryptering Office 365 Enterprise](set-up-encryption.md).

## <a name="what-is-encryption-and-how-does-it-work-in-office-365"></a>Hvad er kryptering, og hvordan fungerer det i Office 365?

Krypteringsprocessen koder dine data (kaldet almindelig tekst) til kryptering af tekst. Til forskel fra almindelig tekst kan ciphertext ikke bruges af personer eller computere, medmindre det er muligt at dekryptere ciphertext. Dekryptering kræver en krypteringsnøgle, som kun autoriserede brugere har. Kryptering sikrer, at kun autoriserede modtagere kan dekryptere dit indhold. Indhold omfatter filer, mails, kalenderposter osv.
  
Kryptering forhindrer ikke i sig selv skæring af indhold. Kryptering er en del af en større strategi for beskyttelse af oplysninger for organisationen. Ved hjælp af kryptering hjælper du med at sikre, at kun autoriserede parter kan bruge de krypterede data.
  
Du kan have flere lag kryptering på plads på samme tid. Du kan f.eks. kryptere mails og også de kommunikationskanaler, som dine mails flyder gennem. Med Office 365 krypteres dine data ved rest- og overførsel ved hjælp af flere stærke krypteringsprotokoller og teknologier, der omfatter Transport Layer Security/Secure Sockets Layer (TLS/SSL), IPSec (Internet Protocol Security) og AES (Advanced Encryption Standard) AES (Internet Protocol Security) og AES.
  
## <a name="encryption-for-data-at-rest-and-data-in-transit"></a>Kryptering af in rest-data og data under overførsel

 Eksempler på **indgående data** omfatter filer, du har uploadet til et SharePoint-bibliotek, Project Online-data, dokumenter, du har uploadet til et Skype for Business-møde, mails og vedhæftede filer, du har gemt i mapper i din postkasse, og filer, du har uploadet til OneDrive for Business.
  
 **Eksempler på data under overførsel** omfatter mails, der er i gang med at blive leveret, eller samtaler, der finder sted i et onlinemøde. In Office 365, data er under overførsel, når en brugers enhed kommunikerer med en Microsoft-server, eller når en Microsoft-server kommunikerer med en anden server.
  
Med Office 365 arbejder flere lag og typer kryptering sammen for at sikre dine data. Følgende tabel indeholder nogle eksempler med links til yderligere oplysninger.
  
|**Typer af indhold**|**Encryption Technologies**|**Ressourcer til at få mere at vide**|
|:-----|:-----|:-----|
|Filer på en enhed. Disse filer kan omfatte mails, der er gemt i en mappe, Office dokumenter, der er gemt på en computer, tablet eller telefon, eller data, der er gemt i Microsoft-skyen.  <br/> |BitLocker i Microsoft-datacentre. BitLocker kan også bruges på klientcomputere, f.eks. Windows computere og tablets  <br/> Distributed Key Manager (DKM) i Microsoft-datacentre  <br/> Kundenøgle til Microsoft 365  <br/> |[Windows IT-center: BitLocker](/windows/device-security/bitlocker/bitlocker-overview) <br/> [Microsoft Center for sikkerhed og sikkerhed: Kryptering](https://www.microsoft.com/TrustCenter/Security/Encryption) <br/> [Serien Skysikkerhedskontrolelementer: Kryptering af data i rest](https://blogs.microsoft.com/microsoftsecure/2015/09/10/cloud-security-controls-series-encrypting-data-at-rest) <br/> [Sådan Exchange Online dine mailhemmeligheder](exchange-online-secures-email-secrets.md) <br/> [Tjenestekryptering med kundenøgle](customer-key-overview.md) <br/> |
|Filer i transit mellem brugere. Disse filer kan omfatte Office dokumenter eller SharePoint listeelementer, der deles mellem brugere.  <br/> |TLS for filer under overførsel  <br/> |[Datakryptering i OneDrive for Business og SharePoint Online](data-encryption-in-odb-and-spo.md) <br/> [Skype for Business Online: Sikkerhed og arkivering](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features) <br/> |
|Mail under overførsel mellem modtagere. Denne mail indeholder mails, der hostes af Exchange Online.  <br/> |Office 365-meddelelseskryptering med Azure Rights Management, S/MIME og TLS til mail under overførsel  <br/> |[Office 365-meddelelseskryptering (OME)](ome.md) <br/> [Mailkryptering i Office 365](email-encryption.md) <br/> [Sådan Exchange Online TLS til at sikre mailforbindelser i Office 365](exchange-online-uses-tls-to-secure-email-connections.md) <br/> |
|Chats, meddelelser og filer under overførsel mellem modtagere ved hjælp Microsoft Teams. <br/> |Teams bruger TLS og MTLS til at kryptere chatbeskeder. Medietrafik krypteres ved hjælp af Secure RTP (SRTP). Teams anvender FIPS-kompatible algoritmer (Federal Information Processing Standard) til kryptering af nøgleudvekslinger. <br/> |[Kryptering til Teams](/microsoftteams/teams-security-guide#encryption-for-teams) <br/> |

## <a name="what-if-i-need-more-control-over-encryption-to-meet-security-and-compliance-requirements"></a>Hvad gør jeg, hvis jeg har brug for mere kontrol over kryptering for at opfylde krav til sikkerhed og overholdelse af regler og standarder?

Microsoft 365 leverer Microsoft-administrerede løsninger til volumenkryptering, filkryptering og postkassekryptering Office 365. Desuden leverer Microsoft krypteringsløsninger, som du kan administrere og kontrollere. Disse krypteringsløsninger er bygget på Azure.
  
Du kan få mere at vide i følgende ressourcer:
  
- [Hvad er Azure Rights Management?](/information-protection/understand-explore/what-is-azure-rms)

- [Aktivere Rights Management i Administration](../enterprise/activate-rms-in-microsoft-365.md)

- [Konfigurere IRM (Information Rights Management) SharePoint Administration](set-up-irm-in-sp-admin-center.md)

- [Tjenestekryptering med kundenøgle i Office 365](customer-key-overview.md)

- [Kryptering med dobbelt nøgle til Microsoft 365](double-key-encryption.md)

## <a name="how-do-i"></a>Hvordan kan jeg...

|**Hvis du vil**|**Se disse ressourcer**|
|:-----|:-----|
|Konfigurer kryptering for min organisation|[Konfigurer kryptering i Office 365 Enterprise](set-up-encryption.md)|
|Få vist detaljer om certifikater, teknologier og TLS-krypteringspakker|[Tekniske detaljer om kryptering](technical-reference-details-about-encryption.md)|
|Arbejde med krypterede meddelelser på en mobilenhed|[Se krypterede meddelelser på din Android-enhedFå](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb) [vist krypterede meddelelser på iPhone eller iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|
|Kryptér et dokument ved hjælp af adgangskodebeskyttelse. Beskyttelse med adgangskode understøttes ikke i en browser. Brug skrivebordsversioner af Word, Excel og PowerPoint til adgangskodebeskyttelse). |[Tilføj eller fjern beskyttelsen i dit dokument, din projektmappe eller præsentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Vælg en **Tilføj beskyttelse-sektion** , og se derefter **Kryptér med adgangskode**.|
|Fjern kryptering fra et dokument|[Tilføj eller fjern beskyttelsen i dit dokument, din projektmappe eller præsentation](https://support.office.com/article/05084cc3-300d-4c1a-8416-38d3e37d6826). Vælg sektionen **Fjern beskyttelse** , og se derefter **Fjern adgangskodekryptering**.  |

## <a name="related-topics"></a>Relaterede emner

[Planlæg funktioner Microsoft 365 sikkerhed og informationsbeskyttelse](plan-for-security-and-compliance.md)

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](/office365/admin/security-and-compliance/secure-your-business-data)

[Kryptering og afspilningsflow på Microsoft Stream-videoniveau](/stream/network-overview#video-level-encryption-and-playback-flow)