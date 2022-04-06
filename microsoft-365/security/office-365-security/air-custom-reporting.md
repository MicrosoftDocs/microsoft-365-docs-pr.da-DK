---
title: Brugerdefinerede rapporteringsløsninger med automatisk undersøgelse og svar
keywords: SIEM, API, AIR, autoIR, Microsoft Defender til slutpunkt, automatisk undersøgelse, integration, brugerdefineret rapport
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
ms.openlocfilehash: 3ff4317fc195a175a2b622c13ea4683a5e010b1c
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680703"
---
# <a name="custom-or-third-party-reporting-solutions-for-microsoft-defender-for-office-365"></a>Brugerdefinerede løsninger eller tredjepartsrapporteringsløsninger til Microsoft Defender Office 365

Med [Microsoft Defender til Office 365](defender-for-office-365.md) får du [detaljerede oplysninger om automatiserede undersøgelser](air-view-investigation-results.md). Nogle organisationer bruger dog også en brugerdefineret rapporteringsløsning eller en rapporteringsløsning fra tredjepart. Hvis din organisation vil integrere oplysninger om automatiserede undersøgelser med en sådan løsning, kan du bruge Office 365 Management Activity API.[](office-365-air.md)

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Med [Microsoft Defender til Office 365](defender-for-office-365.md) får du [detaljerede oplysninger om automatiserede undersøgelser](air-view-investigation-results.md). Nogle organisationer bruger dog også en brugerdefineret rapporteringsløsning eller en rapporteringsløsning fra tredjepart. Hvis din organisation vil integrere oplysninger om automatiserede undersøgelser med en sådan løsning, kan du bruge Office 365 Management Activity API.

|Ressource|Beskrivelse|
|:---|:---|
|[Office 365 oversigt over administrations-API'er](/office/office-365-management-api/office-365-management-apis-overview)|Administrationsaktivitets-API Office 365 indeholder oplysninger om forskellige bruger-, administrator-, system- og politikhandlinger og hændelser fra Microsoft 365 og Azure Active Directory aktivitetslogfiler.|
|[Introduktion til Office 365-API'er til administration](/office/office-365-management-api/get-started-with-office-365-management-apis)|Administrations-Office 365 anvender Azure AD til at levere godkendelsestjenester til dit program for at få adgang Microsoft 365 data. Følg trinnene i denne artikel for at konfigurere dette.|
|[Office 365 administrationsaktivitets-API-reference](/office/office-365-management-api/office-365-management-activity-api-reference)|Du kan bruge Office 365 Management Activity API til at hente oplysninger om bruger-, administrator-, system- og politikhandlinger og hændelser i Microsoft 365-aktivitetslogfiler og Azure AD-aktivitetslogfiler. Læs denne artikel for at få mere at vide om, hvordan det fungerer.|
|[Office 365 Management Activity API-skema](/office/office-365-management-api/office-365-management-activity-api-schema)|Få et overblik over skemaet [Common](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) og [Defender for Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) samt trusselsundersøgelse og svarskema for at få mere at vide om bestemte typer data, der er tilgængelige via Office 365 Management Activity API.|

## <a name="see-also"></a>Se også

- [Microsoft Defender til Office 365](defender-for-office-365.md)
- [Automatiseret undersøgelse og svar i Microsoft 365 Defender](/microsoft-365/security/defender/m365d-autoir)
