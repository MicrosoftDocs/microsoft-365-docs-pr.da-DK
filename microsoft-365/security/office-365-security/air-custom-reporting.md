---
title: Brugerdefinerede rapporteringsløsninger med automatiseret undersøgelse og svar
keywords: SIEM, API, AIR, autoIR, Microsoft Defender for Endpoint, automatiseret undersøgelse, integration, brugerdefineret rapport
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Få mere at vide om, hvordan du integrerer automatiseret undersøgelse og svar med en brugerdefineret rapporteringsløsning eller en rapporteringsløsning fra tredjepart.
ms.date: 01/29/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f21ed51cc9e89c2d60c924df377f109c6e29eec6
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647881"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Brugerdefinerede rapporteringsløsninger eller tredjepartsrapporteringsløsninger til Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Med [Microsoft Defender for Office 365](defender-for-office-365.md) får du [detaljerede oplysninger om automatiserede undersøgelser](air-view-investigation-results.md). Nogle organisationer bruger dog også en brugerdefineret rapporteringsløsning eller en rapporteringsløsning fra tredjepart. Hvis din organisation vil integrere oplysninger om [automatiserede undersøgelser](office-365-air.md) med en sådan løsning, kan du bruge API'en Office 365 managementaktivitet.

Med [Microsoft Defender for Office 365](defender-for-office-365.md) får du [detaljerede oplysninger om automatiserede undersøgelser](air-view-investigation-results.md). Nogle organisationer bruger dog også en brugerdefineret rapporteringsløsning eller en rapporteringsløsning fra tredjepart. Hvis din organisation vil integrere oplysninger om automatiserede undersøgelser med en sådan løsning, kan du bruge API'en Office 365 managementaktivitet.

|Ressource|Beskrivelse|
|:---|:---|
|[Oversigt over API'er til administration af Office 365](/office/office-365-management-api/office-365-management-apis-overview)|API'en til administration af Office 365 indeholder oplysninger om forskellige bruger-, administrator-, system- og politikhandlinger og -hændelser fra Microsoft 365 og Azure Active Directory aktivitetslogge.|
|[Kom i gang med API'er til administration af Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis)|API'en til administration af Office 365 bruger Azure AD til at levere godkendelsestjenester, så dit program kan få adgang til Microsoft 365 data. Følg trinnene i denne artikel for at konfigurere dette.|
|[Reference til Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference)|Du kan bruge API'en til administration af Office 365 til at hente oplysninger om bruger-, administrator-, system- og politikhandlinger og -hændelser fra Microsoft 365 og Azure AD aktivitetslogge. Læs denne artikel for at få mere at vide om, hvordan det fungerer.|
|[Skema til Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-schema)|Få et overblik over det [fælles skema](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) og [skemaet for Defender for Office 365 og trusselsundersøgelser og svar](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) for at få mere at vide om bestemte typer data, der er tilgængelige via API'en til administration af Office 365.|

## <a name="see-also"></a>Se også

- [Microsoft Defender for Office 365](defender-for-office-365.md)
- [Automatiseret undersøgelse og svar i Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
