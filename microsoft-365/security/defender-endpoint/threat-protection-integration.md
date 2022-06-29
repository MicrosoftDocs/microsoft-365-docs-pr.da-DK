---
title: Integrer Microsoft Defender for Endpoint med andre Microsoft-løsninger
description: Få mere at vide om, hvordan Microsoft Defender for Endpoint integreres med andre Microsoft-løsninger, herunder Microsoft Defender for Identity og Microsoft Defender for Cloud.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, betinget adgang, office, Microsoft Defender for Endpoint, microsoft defender for identity, microsoft defender for office, Microsoft Defender for Cloud, microsoft cloud app security, azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 24244fa9b0cbb9ed452c8b09b6a108055ac6f770
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489398"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender for Endpoint og andre Microsoft-løsninger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Integrer med andre Microsoft-løsninger

Microsoft Defender for Endpoint integreres direkte med forskellige Microsoft-løsninger.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender for Cloud

Microsoft Defender for Endpoint indeholder en omfattende serverbeskyttelsesløsning, herunder EDR-funktioner (Endpoint Detection and Response) på Windows Servers.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

Med Microsoft Defender for Endpoint-connectoren kan du streame beskeder fra Microsoft Defender for Endpoint til Microsoft Sentinel. Dette giver dig mulighed for mere omfattende at analysere sikkerhedshændelser på tværs af din organisation og oprette strategibøger, så du kan reagere effektivt og øjeblikkeligt.

### <a name="azure-information-protection"></a>Azure Information Protection

Vi har for nylig frarådet azure Information Protection-integration, da vores DLP-slutpunktsfunktioner omfatter en forbedret registrerings- og beskyttelsesløsning for følsomme data, der er gemt på slutpunktsenheder, og som giver større synlighed og integration mellem løsninger. Dette blev annonceret i følgende [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555). Vi anbefaler, at kunderne flytter til ved hjælp af Slutpunkt DLP.

### <a name="conditional-access"></a>Betinget adgang

Microsoft Defender for Endpoint dynamiske enhedsrisikoscore er integreret i evalueringen af betinget adgang og sikrer, at det kun er sikre enheder, der har adgang til ressourcer.

### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender for Cloud Apps

Microsoft Defender for Cloud Apps udnytter Microsoft Defender for Endpoint signaler til at give direkte indsigt i brug af cloudprogrammer, herunder brugen af ikke-understøttede cloudtjenester (skygge-IT) fra alle Microsoft Defender for Endpoint overvågede enheder.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Mistænkelige aktiviteter er processer, der kører under en brugerkontekst. Integrationen mellem Microsoft Defender for Endpoint og Microsoft Defender for Identity giver fleksibiliteten til at udføre sikkerhedsundersøgelser på tværs af aktiviteter og identiteter.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender til Office

[Defender for Office 365](/office365/securitycompliance/office-365-atp) hjælper med at beskytte din organisation mod malware i mails eller filer via Sikre links, Sikre vedhæftede filer, avancerede funktioner til anti-phishing og spoof intelligence. Integrationen mellem Microsoft Defender for Office 365 og Microsoft Defender for Endpoint gør det muligt for sikkerhedsanalytikere at gå opstrøms for at undersøge indgangspunktet for et angreb. Via deling af trusselsintelligens kan angreb være indeholdt og blokeret.

> [!NOTE]
> Defender for Office 365 data vises for hændelser inden for de sidste 30 dage. I forbindelse med beskeder vises Defender for Office 365 data baseret på første aktivitetstid. Derefter er dataene ikke længere tilgængelige i Defender for Office 365.

### <a name="skype-for-business"></a>Skype for Business

Den Skype for Business integration gør det muligt for analytikere at kommunikere med en potentielt kompromitteret bruger eller enhedsejer via en simpel knap fra portalen.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

Med Microsoft 365 Defender, Microsoft Defender for Endpoint og forskellige Microsoft-sikkerhedsløsninger udgør en samlet virksomhedsforsvarspakke før og efter sikkerhedsbrud, der oprindeligt integreres på tværs af slutpunkter, identitet, mail og programmer for at registrere, forhindre, undersøge og automatisk reagere på avancerede angreb.

[Få mere at vide om Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>Relaterede emner

- [Konfigurer integration og andre avancerede funktioner](advanced-features.md)
- [Oversigt over Microsoft 365 Defender-portalen](/microsoft-365/security/defender/microsoft-365-defender)
- [Slå Microsoft 365 Defender til](/microsoft-365/security/defender/m365d-enable)
- [Beskyt brugere, data og enheder med betinget adgang](conditional-access.md)
