---
title: Integrer Microsoft Defender til slutpunkt med andre Microsoft-løsninger
description: Få mere at vide om, hvordan Microsoft Defender til Slutpunkt integreres med andre Microsoft-løsninger, herunder Microsoft Defender for Identity og Microsoft Defender for Cloud.
author: mjcaparas
ms.author: macapara
ms.prod: m365-security
keywords: microsoft 365 defender, conditional access, office, Microsoft Defender for Endpoint, microsoft defender for identity, microsoft defender for office, Azure Defender, microsoft cloud app security, azure sentinel
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 4f220b16b0402215aa1fad0681edf241b61062ed
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63606458"
---
# <a name="microsoft-defender-for-endpoint-and-other-microsoft-solutions"></a>Microsoft Defender til slutpunkt og andre Microsoft-løsninger

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="integrate-with-other-microsoft-solutions"></a>Integrer med andre Microsoft-løsninger

Microsoft Defender til Slutpunkt integreres direkte med forskellige Microsoft-løsninger.

### <a name="microsoft-defender-for-cloud"></a>Microsoft Defender til skyen

Microsoft Defender til Slutpunkt giver en omfattende serverbeskyttelsesløsning, herunder slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar) på Windows-servere.

### <a name="microsoft-sentinel"></a>Microsoft Sentinel

Med forbindelsespunktet Microsoft Defender for Endpoint kan du streame beskeder fra Microsoft Defender til Endpoint til Microsoft Sentinel. Dette gør det muligt for dig at analysere sikkerhedshændelser mere grundigt på tværs af din organisation og opbygge strategibøger, så du kan få et effektivt og øjeblikkeligt svar.

### <a name="azure-information-protection"></a>Azure Information Protection

Vi har for nylig forældet integration med Azure Information Protection, da vores Slutpunkt-DLP-funktioner omfatter en forbedret løsning til registrering og beskyttelse af følsomme data, der er gemt på slutpunktsenheder, hvilket muliggør større synlighed og integration mellem løsninger. Dette blev offentliggjort på følgende [blog](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/protecting-sensitive-information-on-devices/ba-p/2143555). Vi anbefaler, at kunderne flytter til at bruge Slutpunkt DLP.

### <a name="conditional-access"></a>Betinget adgang

Microsoft Defender til slutpunkts dynamiske risikoscore for enheder er integreret i evalueringen af Betinget adgang, hvilket sikrer, at kun sikre enheder har adgang til ressourcer.

### <a name="microsoft-defender-for-cloud-apps"></a>Microsoft Defender til skyapps

Microsoft Defender til skyapps udnytter Microsoft Defender til slutpunkt-signaler til at tillade direkte synlighed i brug af skyprogrammer, herunder brug af ikke-understøttede skytjenester (skygge IT) fra alle overvågede Microsoft Defender-enheder på slutpunktet.

### <a name="microsoft-defender-for-identity"></a>Microsoft Defender for Identity

Mistænkelige aktiviteter kører under en brugerkontekst. Integrationen mellem Microsoft Defender for Endpoint og Microsoft Defender for Identity giver fleksibilitet til at udføre cybersikkerhedsundersøgelse på tværs af aktiviteter og identiteter.

### <a name="microsoft-defender-for-office"></a>Microsoft Defender til Office

[Defender for Office 365](/office365/securitycompliance/office-365-atp) hjælper med at beskytte din organisation mod malware i mails eller filer via Pengeskab Links, Pengeskab Vedhæftede filer, avancerede antiphishing- og efterlignede intelligensfunktioner. Integrationen mellem Microsoft Defender for Office 365 og Microsoft Defender til Endpoint gør det muligt for sikkerhedsanalytikere at gå opstrøms for at undersøge indgangspunktet for et angreb. Via deling med trusselsintelligens kan angreb blive indeholdt og blokeret.

> [!NOTE]
> Defender for Office 365 vises for hændelser inden for de seneste 30 dage. Ved påmindelser vises Defender Office 365 data baseret på første aktivitetstid. Derefter er dataene ikke længere tilgængelige i Defender til Office 365.

### <a name="skype-for-business"></a>Skype for Business

Integration Skype for Business gør det muligt for analytikere at kommunikere med en potentielt kompromitteret bruger eller enhedsejer via en simpel knap fra portalen.

## <a name="microsoft-365-defender"></a>Microsoft 365 Defender

Med Microsoft 365 Defender udgør Microsoft Defender til slutpunkt og forskellige Microsoft-sikkerhedsløsninger en samlet virksomhedsforligspakke, der oprindeligt integreres på tværs af slutpunkt, identitet, mail og programmer for at registrere, forhindre, undersøge og automatisk reagere på avancerede angreb.

[Få mere at vide om Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

## <a name="related-topics"></a>Relaterede emner

- [Konfigurere integration og andre avancerede funktioner](advanced-features.md)
- [Microsoft 365 Defender oversigt](/microsoft-365/security/defender/microsoft-365-defender)
- [Slå Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable)
- [Beskyt brugere, data og enheder med Betinget adgang](conditional-access.md)
