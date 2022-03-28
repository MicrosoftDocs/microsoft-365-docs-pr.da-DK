---
title: Understøttede SVAR-API'er for Microsoft Defender til slutpunktssvar
description: Få mere at vide om de specifikke svarrelaterede Microsoft Defender for Endpoint API-opkald.
keywords: response apis, graph api, understøttede API'er, agent, beskeder, enhed, bruger, domæne, ip, fil
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
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
ms.openlocfilehash: dcf73669ab780ec23cbd5551039dc8c74f0502ef
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597508"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>Understøttede API'er for Microsoft Defender til slutpunktsforespørgsel

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!TIP]
> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-supported-response-apis-abovefoldlink)

Få mere at vide om de understøttede svarrelaterede API-opkald, du kan køre, og få mere at vide om de påkrævede anmodningsoverskrifter og forventet svar fra opkald.

## <a name="in-this-section"></a>I dette afsnit

<br>

****

|Emne|Beskrivelse|
|---|---|
|Pakke til samlet undersøgelse|Kør denne API for at indsamle en undersøgelsespakke fra en enhed.|
|Isoler enhed|Kør denne API for at isolere en enhed fra netværket.|
|Unisolate-enhed|Fjern en enhed fra isolation.|
|Begræns udførelse af kode|Kør denne API, der indeholder et angreb, ved at stoppe ondsindede processer. Du kan også låse en enhed og forhindre efterfølgende forsøg på potentielt skadelige programmer i at køre.|
|Ubegrænset udførelse af kode|Kør dette for at ophæve begrænsningen af programpolitikken, når du har bekræftet, at den kompromitterede enhed er blevet løst.|
|Kør antivirusscanning|Påbegynde en antivirus-scanning eksternt for at identificere og afhjælpe malware, der kan være på en kompromitteret enhed.|
|Stop og karantæne-fil|Kør dette opkald for at stoppe med at køre processer, sætte filer i karantæne og slette vedvarendehed som registreringsdatabasenøgler.|
|Anmodningseksempel|Kør dette opkald for at anmode om en eksempel på en fil fra en bestemt enhed. Filen indsamles fra enheden og uploades til et sikkert lager.|
|Bloker fil|Kør denne API for at forhindre yderligere overførsel af et angreb i din organisation ved at udelukke potentielt skadelige filer eller mistanke om malware.|
|Fjern blokering af fil|Tillad kørsel af en fil i organisationen ved hjælp Microsoft Defender Antivirus.|
|Hent SAS URI'en pakke|Kør denne API for at få en URI, der gør det muligt at hente en undersøgelsespakke.|
|Hent MachineAction-objekt|Kør denne API for at få MachineAction-objekt.|
|Hent MachineActions-samling|Kør dette for at få MachineAction-samling.|
|Hent samlingen FileActions|Kør denne API for at få FileActions-samling.|
|Hent FileMachineAction-objekt|Kør denne API for at få FileMachineAction-objekt.|
|Hent FileMachineActions-samling|Kør denne API for at få FileMachineAction-samling.|
|
