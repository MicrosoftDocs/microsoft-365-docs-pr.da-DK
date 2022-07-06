---
title: Konfigurer kryptering i Office 365 Enterprise
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: Med Office 365 er nogle krypteringsfunktioner som standard slået til. Andre funktioner kan konfigureres til at opfylde visse krav til overholdelse af angivne standarder eller juridiske krav.
ms.openlocfilehash: 86e39603025c29d47a2e1b2b5b946bfe2549245d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622101"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Konfigurer kryptering i Office 365 Enterprise

Kryptering kan beskytte dit indhold mod at blive læst af uautoriserede brugere. Da [kryptering i Office 365](encryption.md) kan udføres ved hjælp af forskellige teknologier og metoder, er der ikke ét sted, hvor du aktiverer eller konfigurerer kryptering. Denne artikel indeholder oplysninger om forskellige måder, du kan konfigurere kryptering på som en del af din strategi til beskyttelse af oplysninger.

> [!TIP]
> Hvis du leder efter flere tekniske oplysninger om kryptering, kan du se [Oplysninger om kryptering i teknisk reference om kryptering i Office 365](technical-reference-details-about-encryption.md).

Med Office 365 er flere krypteringsfunktioner tilgængelige som standard. Yderligere krypteringsfunktioner kan konfigureres til at opfylde visse krav til overholdelse af angivne standarder eller juridiske krav. I følgende tabel beskrives flere krypteringsmetoder til forskellige scenarier.

<br>

****

|Scenario|Krypteringsmetoder|
|---|---|
|Filer gemmes på Windows-computere|Kryptering på computerniveau kan udføres ved hjælp af BitLocker på Windows-enheder. Som virksomhedsadministrator eller IT Pro kan du konfigurere dette ved hjælp af Microsoft Deployment Toolkit (MDT). Se [Konfigurer MDT til BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Filer gemmes på mobilenheder|Nogle typer mobilenheder krypterer filer, der som standard er gemt på disse enheder. Med [funktioner i indbyggede Mobilenhedshåndtering til Office 365](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) kan du angive politikker, der bestemmer, om mobilenheder skal have adgang til data i Office 365. Du kan f.eks. angive en politik, der kun tillader enheder, der krypterer indhold, at få adgang til Office 365 data. Se [Opret og installer politikker for enhedssikkerhed](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Hvis du vil have yderligere kontrol over, hvordan mobilenheder interagerer med Office 365, kan du overveje at tilføje [Microsoft Intune](/mem/intune/fundamentals/setup-steps).|
|Du skal have kontrol over de krypteringsnøgler, der bruges til at kryptere dine data i Microsofts datacentre|Som Office 365 administrator kan du styre din organisations krypteringsnøgler og derefter konfigurere Office 365 til at bruge dem til at kryptere inaktive data i Microsofts datacentre. <p> [Tjenestekryptering med Microsoft Purview-kundenøgle](customer-key-overview.md)|
|Folk kommunikerer via mail (Exchange Online)|Som Exchange Online administrator har du flere muligheder for at konfigurere mailkryptering. Disse omfatter: <ul><li>Brug [Office 365 meddelelseskryptering (OME)](set-up-new-message-encryption-capabilities.md) med Azure Rights Management (Azure RMS) for at gøre det muligt for personer at sende krypterede meddelelser i eller uden for din organisation</li><li>Brug [af S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo) til at kryptere og signere mails digitalt</li><li>Brug af TLS til at [konfigurere forbindelser til et sikkert mailflow med en anden organisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)</li></ul> <p> Se [Kryptering af mail i Office 365](./email-encryption.md).|
|Filer tilgås fra teamwebsteder eller dokumentbiblioteker (OneDrive for Business eller SharePoint Online)|Når personer arbejder med filer, der er gemt i OneDrive for Business eller SharePoint Online, bruges der TLS-forbindelser. Dette er indbygget i Office 365 automatisk. Se [Datakryptering i OneDrive for Business og SharePoint Online](./data-encryption-in-odb-and-spo.md).|
|Filer deles i onlinemøder og chatsamtaler (Skype for Business Online)|Når personer arbejder med filer ved hjælp af Skype for Business Online, bruges TLS til forbindelsen. Dette er indbygget i Office 365 automatisk. Se [Sikkerhed og arkivering (Skype for Business Online)](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).|
|Filer deles i onlinemøder og chatsamtaler (Microsoft Teams)|Når personer arbejder med filer ved hjælp af Microsoft Teams, bruges TLS til forbindelsen. Dette er indbygget i Office 365 automatisk. Microsoft Teams understøtter i øjeblikket ikke indbygget gengivelse af krypteret mail. Hvis du vil forhindre, at krypteret mail lander som krypteret i Microsoft Teams, skal [du se Ofte stillede spørgsmål om meddelelseskryptering](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Flere oplysninger:

Hvis du vil vide mere om løsninger til filbeskyttelse, der omfatter krypteringsindstillinger, skal du se [Filerbeskyttelsesløsninger i Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
