---
title: Microsoft 365 Defender for kunder inden for det amerikanske offentlige
description: Få mere at vide Microsoft 365 Defender af kundekrav og funktioner, der er tilgængelige for kunder i det amerikanske Microsoft 365 Defender det amerikanske miljø
keywords: government, gcc, high, requirements, capabilities, defender, Microsoft 365 Defender, xdr, dod
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
ms.openlocfilehash: 3e8f6e523a5483de99beb0af7d01ab96951b7a3e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63596967"
---
# <a name="microsoft-365-defender-for-us-government-customers"></a>Microsoft 365 Defender for kunder inden for det amerikanske offentlige

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender amerikanske kunder, der er bygget i Azure US Government-miljøet, bruger de samme underliggende teknologier som Microsoft 365 Defender i Azure Commercial.

Dette tilbud er tilgængeligt for GCC-, GCC High- og DoD-kunder og er baseret på den samme forebyggelse, registrering, undersøgelse og afhjælpning som den kommercielle version. Der er dog nogle forskelle i tilgængeligheden af funktioner for dette tilbud.

> [!NOTE]
> Hvis du er GCC-kunde, der bruger Defender til skyapps, Defender til slutpunkt eller Defender for Identity i kommercielt, skal du overgå disse tjenester til deres GCC-versioner for at være berettiget til Microsoft 365 Defender GCC.

## <a name="licensing-requirements"></a>Licenskrav

Microsoft 365 Defender kunder i det amerikanske offentlige myndigheder kræver et af følgende Microsoft-volumenlicenstilbud:

### <a name="desktop-licensing"></a>Skrivebordslicenser

<br />

****

|GCC|GCC høj|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 til GCC Høj|Microsoft 365 G5 til DOD|
|Microsoft 365 G5-sikkerheds GCC|Microsoft 365 G5-sikkerhed til GCC High|Microsoft 365 G5-sikkerhed til DOD|
|Enterprise Mobility + Security G5-GCC|Enterprise Mobility + Security E5 til GCC Høj|Enterprise Mobility + Security E5 til DOD|
|Office 365 G5-GCC|Office 365 E5 til GCC Høj|Office 365 E5 for DOD|
|Microsoft Defender til skyapps GCC|Microsoft Defender til skyapps til GCC High|Microsoft Defender til skyapps til DOD|
|Microsoft Defender til slutpunkt – GCC|Microsoft Defender til slutpunkt for GCC High|Microsoft Defender til slutpunkt for DOD|
|Microsoft Defender for Identity – GCC|Microsoft Defender for Identity for GCC High|Microsoft Defender for Identity for DOD|
|Microsoft Defender for Office 365 (Plan 2) GCC|Microsoft Defender til Office 365 (Plan 2) for GCC High|Microsoft Defender for Office 365 (Plan 2) for DOD|
|Windows 10 Enterprise E5-GCC|Windows 10 Enterprise E5 til GCC Høj|Windows 10 Enterprise E5 til DOD|
|

### <a name="server-licensing"></a>Serverlicensering

<br />

****

|GCC|GCC høj|DoD|
|---|---|---|
|Microsoft Defender for Endpoint Server GCC|Microsoft Defender for Endpoint Server til GCC High|Microsoft Defender for Endpoint Server for DOD|
|Microsoft Defender til servere|Microsoft Defender til servere – Government|Microsoft Defender til servere – Government|
|

## <a name="portal-urls"></a>Url-adresser for portaler

Følgende er URL-adresser Microsoft 365 Defender portalen for kunder i det amerikanske offentlige:

<br />

****

|Kundetype|URL-adresse til portal|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC høj|Udrulning|
|DoD|Udrulning|
|
> [!NOTE]
> Hvis du er GCC-kunde og er i gang med at flytte fra microsoft Defender til slutpunkt kommerciel til GCC, https://transition.security.microsoft.com kan du bruge til at få adgang til dine kommercielle Microsoft Defender for Endpoint-data.

## <a name="api"></a>API

I stedet for de offentlige URI'er, der [er angivet i vores API-dokumentation](api-overview.md), skal du bruge følgende URI'er:

<br />

****

|Slutpunktstype|GCC|GCC High & DoD|
|---|---|---|
|Logon|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Microsoft 365 Defender API|`https://api-gcc.security.microsoft.us`|`https://api-gov.security.microsoft.us`|
|

## <a name="feature-parity-with-commercial"></a>Funktionsparitet med kommerciel

Microsoft 365 Defender for kunder i det amerikanske offentlige myndigheder har ikke fuldstændig paritet med det kommercielle tilbud. Vores mål er at levere alle kommercielle funktioner og funktionalitet til vores kunder i det amerikanske offentlige, men der er visse funktioner, som endnu ikke er tilgængelige, som vi gerne vil fremhæve.

Disse er de kendte mellemrum:

<br />

****

|Funktionsnavn|GCC|GCC høj|DoD|
|---|:---:|:---:|:---:|
|Integrationer: Microsoft Sentinel (hændelser & Raw-data)|![Ja](../defender-endpoint/images/svg/check-yes.svg)|![Ja](../defender-endpoint/images/svg/check-yes.svg) I privat eksempelvisning|![Ja](../defender-endpoint/images/svg/check-yes.svg) I privat eksempelvisning|
|Microsoft-trusselseksperter|![Nej](../defender-endpoint/images/svg/check-no.svg) På teknisk backlog|![Nej](../defender-endpoint/images/svg/check-no.svg) På teknisk backlog|![Nej](../defender-endpoint/images/svg/check-no.svg) På teknisk backlog|

## <a name="more-details"></a>Flere oplysninger

Du kan få mere at vide under de enkelte sider med arbejdsbelastninger fra USA:
- [Microsoft Defender til skyapps](/enterprise-mobility-security/solutions/ems-cloud-app-security-govt-service-description).
- [Microsoft Defender for Identity](/enterprise-mobility-security/solutions/ems-mdi-govt-service-description).
- [Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/gov).
