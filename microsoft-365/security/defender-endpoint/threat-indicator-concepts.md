---
title: Forstå koncepter for trusselsintelligens i Microsoft Defender til Slutpunkt
description: Opret brugerdefinerede advarsler om trusler for organisationen, og få mere at vide om begreberne omkring trusselsintelligens i Microsoft Defender til Slutpunkt
keywords: trusselsintelligens, beskeddefinitioner, indikatorer for kompromis, ioc
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
ms.technology: mde
ms.openlocfilehash: 440f788c4adb757013611bb05621b4eb4f4e9715
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592918"
---
# <a name="understand-threat-intelligence-concepts"></a>Forstå koncepter for trusselsintelligens

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

Avancerede cyberangreb består af flere komplekse ondsindede hændelser, attributter og kontekstafhængige oplysninger. Det kan være en udfordring at identificere og beslutte, hvilke af disse aktiviteter der kvalificeres som mistænkelige. Dit kendskab til kendte attributter og unormale aktiviteter, der er specifikke for din branche, er grundlæggende for at vide, hvornår du skal kalde en observeret funktionsmåde som mistænkelig.

Med Microsoft 365 Defender kan du oprette brugerdefinerede beskeder om trusler, som kan hjælpe dig med at holde styr på mulige angrebsaktiviteter i organisationen. Du kan markere mistænkelige begivenheder for at sammensætte ledetråde og muligvis stoppe en angrebskæde. Disse brugerdefinerede advarsler om trusler vises kun i din organisation og markerer hændelser, som du indstiller den til at spore.

Før du opretter brugerdefinerede advarsler om trusler, er det vigtigt at kende begreberne bag beskeddefinitioner og indikatorer for kompromis (IOCs) og relationen mellem dem.

## <a name="alert-definitions"></a>Beskeddefinitioner
Definitioner af beskeder er kontekstafhængige attributter, der kan bruges samlet til at identificere tidlige fingerpeg om et muligt cyberangreb. Disse indikatorer er typisk en kombination af aktiviteter, karakteristika og handlinger, som en hacker har foretaget for at opnå formålet med et angreb. Overvågning af disse kombinationer af attributter er afgørende for at få et udsigtspunkt mod angreb og muligvis forstyrre kæden af hændelser, før en hackers mål er nået.

## <a name="indicators-of-compromise-ioc"></a>Indikatorer for forlig (IOC)
IOC'er er individuelt kendte skadelige hændelser, der angiver, at der allerede er et netværk eller en enhed, der er blevet brudt. I modsætning til definitioner af beskeder betragtes disse indikatorer som bevis for brud. De ses ofte, når et angreb allerede er blevet udført, og målet er nået, f.eks. eks. eksfiltrering. Det er også vigtigt at holde styr på IOCs under undersøgelser af undersøgelse af oplysninger. Selvom den muligvis ikke kan gribe ind med en angrebskæde, kan det være nyttigt at indsamle disse indikatorer til at skabe bedre forsvar mod mulige fremtidige angreb.

## <a name="relationship-between-alert-definitions-and-iocs"></a>Relation mellem definitioner af beskeder og IOCs
I forbindelse med Microsoft 365 Defender og Microsoft Defender til slutpunkt er beskeddefinitioner beholdere for IOCs og definerer beskeden, herunder de metadata, der er hævet for et bestemt IOC-match. Der leveres forskellige metadata som en del af beskeddefinitionerne. Metadata såsom beskedens definitionsnavn for angreb, alvorsgrad og beskrivelse leveres sammen med andre indstillinger.

Hver IOC definerer de konkrete registreringslogik ud fra typen, værdien og handlingen, som bestemmer, hvordan den matches. Den er bundet til en bestemt beskeddefinition, der definerer, hvordan en registrering vises som en besked på Microsoft 365 Defender konsollen.

Her er et eksempel på en IOC:
- Type: Sha1
- Værdi: 92cfceb39d57d914ed8b14d0e37643de0797ae56
- Handling: Er lig med

IOCs har en mange til en-relation med beskeddefinitioner, så en beskeddefinition kan have mange IOCs, der svarer til den.


## <a name="related-topics"></a>Relaterede emner
- [Administrer indikatorer](manage-indicators.md)
