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
description: Med Office 365 er nogle krypteringsfunktioner som standard slået til. Andre funktioner kan konfigureres til at opfylde bestemte krav til overholdelse af regler og standarder eller juridiske krav.
ms.openlocfilehash: 84ba80c38d6167fbd9d32fdac0288fa1ef4ac3db
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680404"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Konfigurer kryptering i Office 365 Enterprise

Kryptering kan beskytte dit indhold mod at blive læst af uautoriserede brugere. Da [kryptering i Office 365](encryption.md) kan udføres ved hjælp af forskellige teknologier og metoder, er der ikke ét sted, hvor du aktiverer eller konfigurerer kryptering. Denne artikel indeholder oplysninger om forskellige måder, hvorpå du kan konfigurere kryptering som en del af din strategi til beskyttelse af oplysninger.

> [!TIP]
> Hvis du leder efter flere tekniske detaljer om kryptering, skal du [se Tekniske referenceoplysninger om kryptering Office 365](technical-reference-details-about-encryption.md).

Med Office 365 er flere krypteringsfunktioner tilgængelige som standard. Yderligere krypteringsfunktioner kan konfigureres til at opfylde bestemte krav til overholdelse af regler og standarder eller juridiske krav. I følgende tabel beskrives flere krypteringsmetoder til forskellige scenarier.

<br>

****

|Scenarie|Krypteringsmetoder|
|---|---|
|Filer gemmes på Windows computere|Kryptering på computerniveau kan udføres ved hjælp af BitLocker på Windows enheder. Som virksomhedsadministrator eller it-Pro kan du konfigurere dette ved hjælp af Microsoft Deployment Toolkit (MDT). Se [Konfigurer MDT til BitLocker](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Filer gemmes på mobilenheder|Visse typer mobilenheder krypterer filer, der gemmes på disse enheder som standard. Med [funktioner indbygget funktionalitet i Mobilenhedshåndtering til Office 365](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) kan du angive politikker, der bestemmer, om du vil tillade mobilenheder at få adgang til data Office 365. Du kan f.eks. angive en politik, der kun tillader enheder, der krypterer indhold, at få adgang Office 365 data. Se [Opret og installer sikkerhedspolitikker for enheder](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Hvis du vil have yderligere kontrol over, hvordan mobilenheder interagerer Office 365, kan du overveje at [Microsoft Intune](/mem/intune/fundamentals/setup-steps).|
|Du skal have kontrol over de krypteringsnøgler, der bruges til at kryptere dine data i Microsofts datacentre|Som administrator Office 365 administrator kan du kontrollere organisationens krypteringsnøgler og derefter konfigurere Office 365 til at bruge dem til at kryptere dine data i hvile i Microsofts datacentre. <p> [Tjenestekryptering med kundenøgle i Office 365](customer-key-overview.md)|
|Personer kommunikerer via mail (Exchange Online)|Som administrator Exchange Online du flere forskellige muligheder for at konfigurere mailkryptering. Disse omfatter: <ul><li>Brug [Office 365 kryptering af meddelelser (OME)](set-up-new-message-encryption-capabilities.md) med Azure Rights Management (Azure RMS) for at give folk mulighed for at sende krypterede meddelelser i eller uden for organisationen</li><li>Brug [af S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo) til at kryptere og signere mails digitalt</li><li>Brug af TLS [til at konfigurere forbindelser for et sikkert mailflow med en anden organisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)</li></ul> <p> Se [Mailkryptering i Office 365](./email-encryption.md).|
|Filer tilgås fra teamwebsteder eller dokumentbiblioteker (OneDrive for Business eller SharePoint Online)|Når folk arbejder med filer, der er OneDrive for Business eller SharePoint Online, bruges TLS-forbindelser. Dette er indbygget Office 365 automatisk. Se [Datakryptering i OneDrive for Business og SharePoint Online](./data-encryption-in-odb-and-spo.md).|
|Filer deles i onlinemøder og chatsamtaler (Skype for Business Online)|Når personer arbejder med filer, der Skype for Business Online, bruges TLS til forbindelsen. Dette er indbygget Office 365 automatisk. Se [Sikkerhed og arkivering (Skype for Business Online)](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).|
|Filer deles i onlinemøder og chatsamtaler (Microsoft Teams)|Når personer arbejder med filer, der Microsoft Teams, bruges TLS til forbindelsen. Dette er indbygget Office 365 automatisk. Microsoft Teams understøtter i øjeblikket ikke indbygget gengivelse af krypteret mail. Hvis du vil forhindre krypterede mails i at lande Microsoft Teams krypteret, skal du se Ofte [stillede spørgsmål om meddelelseskryptering](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Flere oplysninger:

Du kan få mere at vide om filbeskyttelsesløsninger, der omfatter krypteringsindstillinger, [under Filbeskyttelsesløsninger Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
