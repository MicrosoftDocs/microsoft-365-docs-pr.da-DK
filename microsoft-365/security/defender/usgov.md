---
title: Microsoft 365 Defender for US Government-kunder
description: Få mere at vide om de Microsoft 365 Defender til US Government-kunders krav og funktioner, der er tilgængelige
keywords: government, gcc, high, requirements,capabilities, defender, Microsoft 365 Defender, xdr, dod
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 53fc78159580a27a8af04009f4e5ecd5b18bc4e8
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057577"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft 365 Defender for US Government-kunder

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender til US Government-kunder, der er bygget i Azure US Government-miljøet, bruger de samme underliggende teknologier som Microsoft 365 Defender i Azure Commercial.

Dette tilbud er tilgængeligt for kunder med GCC, GCC High og DoD og er baseret på den samme forebyggelse, registrering, undersøgelse og afhjælpning som den kommercielle version. Der er dog nogle forskelle i tilgængeligheden af egenskaber for dette tilbud.

> [!NOTE]
> Hvis du er GCC kunde, der bruger Defender for Cloud Apps, Defender for Endpoint eller Defender for Identity in Commercial, skal du overføre disse tjenester til deres GCC versioner for at være berettiget til Microsoft 365 Defender GCC.

## <a name="licensing-requirements"></a>Licenskrav

Microsoft 365 Defender til US Government-kunder kræver et af følgende Microsoft-volumenlicenstilbud:

### <a name="desktop-licensing"></a>Skrivebordslicenser

<br />

****

|GCC|GCC Høj|Dod|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 for GCC High|Microsoft 365 G5 for DOD|
|GCC Microsoft 365 G5 Security|Microsoft 365 G5 Security for GCC High|Microsoft 365 G5 Sikkerhed for DOD|
|Enterprise Mobility + Security G5 GCC|Enterprise Mobility + Security E5 for GCC High|Enterprise Mobility + Security E5 for DOD|
|Office 365 G5 GCC|Office 365 E5 for GCC High|Office 365 E5 for DOD|
|Microsoft Defender for Cloud Apps GCC|Microsoft Defender for Cloud Apps for GCC High|Microsoft Defender for Cloud Apps for DOD|
|Microsoft Defender for Endpoint - GCC|Microsoft Defender for Endpoint for GCC High|Microsoft Defender for Endpoint for DOD|
|Microsoft Defender for Identity - GCC|Microsoft Defender for Identity for GCC Høj|Microsoft Defender for Identity for DOD|
|Microsoft Defender for Office 365 (Plan 2) GCC|Microsoft Defender for Office 365 (Plan 2) for GCC High|Microsoft Defender for Office 365 (Plan 2) for DOD|
|Windows 10 Enterprise E5 GCC|Windows 10 Enterprise E5 for GCC High|Windows 10 Enterprise E5 for DOD|
|

### <a name="server-licensing"></a>Serverlicensering

<br />

****

|GCC|GCC Høj|Dod|
|---|---|---|
|GCC Microsoft Defender for Endpoint Server|Microsoft Defender for Endpoint Server til høj GCC|Microsoft Defender for Endpoint Server til DOD|
|Microsoft Defender til servere|Microsoft Defender for servers – Government|Microsoft Defender for servers – Government|
|

## <a name="portal-urls"></a>PORTAL-URL-adresser

Følgende er URL-adresserne til Microsoft 365 Defender-portalen for US Government-kunder:

<br />

****

|Kundetype|URL-adresse til portal|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC Høj|Udrulning|
|Dod|Udrulning|
|
> [!NOTE]
> Hvis du er GCC kunde og er ved at flytte fra Microsoft Defender for Endpoint kommerciel til GCC, kan du bruge https://transition.security.microsoft.com til at få adgang til dine Microsoft Defender for Endpoint kommercielle data.

## <a name="api"></a>API

I stedet for de offentlige URI'er, der er angivet i vores [API-dokumentation](api-overview.md), skal du bruge følgende URI'er:

<br />

****

|Slutpunktstype|GCC|GCC-dod med høj &|
|---|---|---|
|Login|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|API til Microsoft 365 Defender|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Funktionsparitet med kommerciel

Microsoft 365 Defender for US Government-kunder har ikke fuldstændig paritet med det kommercielle tilbud. Selvom vores mål er at levere alle kommercielle funktioner og funktionalitet til vores us government-kunder, er der nogle funktioner, som vi endnu ikke vil fremhæve.

Dette er de kendte huller:

<br />

****

|Funktionsnavn|GCC|GCC Høj|Dod|
|---|:---:|:---:|:---:|
|Integrationer: Microsoft Sentinel (Hændelser & Rådata)|![Ja](../defender-endpoint/images/svg/check-yes.svg) I offentlig prøveversion|![Ja](../defender-endpoint/images/svg/check-yes.svg) I offentlig prøveversion|![Ja](../defender-endpoint/images/svg/check-yes.svg) I offentlig prøveversion|
|Microsoft Threat Experts|![Nej](../defender-endpoint/images/svg/check-no.svg) Om teknisk efterslæb|![Nej](../defender-endpoint/images/svg/check-no.svg) Om teknisk efterslæb|![Nej](../defender-endpoint/images/svg/check-no.svg) Om teknisk efterslæb|

Du kan finde en detaljeret liste over api-tabeller til hændelsesstreaming under [Microsoft 365 Defender streaminghændelsestyper, der understøttes i Api til hændelsesstreaming](supported-event-types.md).

## <a name="more-details"></a>Flere oplysninger

Du kan få flere oplysninger på de individuelle arbejdsbelastninger på US Gov-sider:

- [Microsoft Defender for Cloud Apps](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Microsoft Defender for Identity](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/gov).
