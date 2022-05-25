---
title: Integration af SIEM-server med Microsoft 365 tjenester og programmer
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 11/18/2019
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom:
- Ent_Solutions
- SIEM
- seo-marvel-apr2020
description: Få et overblik over SIEM-serverintegration (Security Information and Event Management) med dine Microsoft 365 cloudtjenester og -programmer
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ffb457a378539691627eff3ad24b24ef782705c1
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670196"
---
# <a name="security-information-and-event-management-siem-server-integration-with-microsoft-365-services-and-applications"></a>Integration af SIEM-server (Security Information and Event Management) med Microsoft 365 tjenester og programmer

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="summary"></a>Oversigt

Bruger eller planlægger din organisation at få en SIEM-server (Security Information and Event Management)? Du undrer dig måske over, hvordan den kan integreres med Microsoft 365 eller Office 365. Denne artikel indeholder en liste over ressourcer, du kan bruge til at integrere din SIEM-server med Microsoft 365 tjenester og programmer.

> [!TIP]
> Hvis du endnu ikke har en SIEM-server og udforsker dine muligheder, kan du overveje **[Microsoft Sentinel](/azure/sentinel/overview)**.

## <a name="do-i-need-a-siem-server"></a>Har jeg brug for en SIEM-server?

Om du har brug for en SIEM-server, afhænger af mange faktorer, f.eks. din organisations sikkerhedskrav, og hvor dine data er placeret. Microsoft 365 indeholder en lang række sikkerhedsfunktioner, der opfylder mange organisationers sikkerhedsbehov uden yderligere servere, f.eks. en SIEM-server. Nogle organisationer har særlige omstændigheder, der kræver brug af en SIEM-server. Her er nogle eksempler:

- *Fabrikam* har noget indhold og programmer i det lokale miljø, og nogle i cloudmiljøet (de har en hybrid cloududrulning). Fabrikam har implementeret en SIEM-server for at få sikkerhedsrapporter på tværs af alt deres indhold og programmer.
- *Contoso* er en organisation for finansielle tjenesteydelser, der har særligt strenge sikkerhedskrav. De har føjet en SIEM-server til deres miljø for at drage fordel af den ekstra sikkerhedsbeskyttelse, de har brug for.

## <a name="siem-server-integration-with-microsoft-365"></a>SIEM-serverintegration med Microsoft 365

En SIEM-server kan modtage data fra en lang række Microsoft 365 tjenester og programmer. I følgende tabel vises flere Microsoft 365 tjenester og programmer sammen med SIEM-serverinput og -ressourcer for at få mere at vide.

<br/><br/>

|Microsoft 365 tjeneste eller program|SIEM-serverinput/-metoder|Ressourcer til at få mere at vide|
|---|---|---|
|[Microsoft Defender for Office 365](defender-for-office-365.md)|Overvågningslogge|[SIEM-integration med Microsoft Defender for Office 365](siem-integration-with-office-365-ti.md)|
|[Microsoft Defender for Endpoint](/windows/security/threat-protection/)|HTTPS-slutpunkt, der hostes i Azure <p> REST API|[Pullbeskeder til dine SIEM-værktøjer](../defender-endpoint/configure-siem.md)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)|Logintegration|[SIEM-integration med Microsoft Defender for Cloud Apps](/cloud-app-security/siem)|

> [!TIP]
> Se [nærmere på Microsoft Sentinel](/azure/sentinel/overview). Microsoft Sentinel leveres med connectors til Microsoft-løsninger. Disse connectors er tilgængelige "klar til brug" og sikrer integration i realtid. Du kan bruge Microsoft Sentinel sammen med dine Microsoft 365 Defender løsninger og Microsoft 365 tjenester, herunder Office 365, Azure AD, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps og meget mere.

### <a name="audit-logging-must-be-turned-on"></a>Overvågningslogføring skal være slået til

Sørg for, at overvågningslogføring er slået til, før du konfigurerer SIEM-serverintegration.

- Du kan se SharePoint Online, OneDrive for Business og Azure Active Directory under [Slå overvågning til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).
- Du kan få Exchange Online under [Administrer overvågning af postkasser](../../compliance/enable-mailbox-auditing.md).

## <a name="integration-steps-if-your-siem-is-microsoft-sentinel"></a>Integrationstrin, hvis din SIEM er Microsoft Sentinel

Sørg for, at din aktuelle plan tillader Microsoft Sentinel-integration (du har f.eks. Microsoft Defender for Office 365 Plan 2 eller nyere), og at din konto i Microsoft Defender for Office 365 eller Microsoft 365 Defender er en *Sikkerhedskonto Administrator*. Til sidst skal du sørge for, at du har *skriverettigheder i Microsoft Sentinel*.

1. Gå til Microsoft Sentinel.
1. I navigationen til venstre for **skærmens Configuration** > **Data-connectors**.
1. **Søg efter** Microsoft 365 Defender, og vælg **connectoren Microsoft 365 Defender (prøveversion).**
1. Vælg **Åbn forbindelsesside** til højre på skærmen.
1. Vælg **Forbind hændelser & beskeder** under **Konfiguration** >
    1. Deaktiver alle Microsoft-regler for oprettelse af hændelser for de produkter, der er valgt i øjeblikket.
1. Rul til **Microsoft Defender for Office 365** i sektionen **Forbind hændelser** på siden.

Bemærk, at du kan vælge tabeller fra *et hvilket som helst andet Microsoft Defender-produkt* , som du finder nyttigt og relevant, når du fuldfører det sidste trin (nedenfor).

7. Vælg **EmailEvents**, **EmailUrlInfo**, **EmailAttachmentInfo** og **EmailPostDeliveryEvents** > og **Anvend ændringer**.

## <a name="more-resources"></a>Flere ressourcer

[Integrer sikkerhedsløsninger i Microsoft Defender for Cloud](/azure/security-center/security-center-partner-integration#exporting-data-to-a-siem)

[Integrer Microsoft Graph sikkerhed-API-beskeder med en SIEM](/graph/security-integration)
