---
title: Oversigt – Avanceret jagt
description: Få mere at vide om avancerede forespørgselsforespørgsler i Microsoft 365, og hvordan du kan bruge dem til proaktivt at finde trusler og trusler i dit netværk
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 03f99f6b883a46e0a7c87d6cbdb2abb8f5552a31
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63591294"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Proaktivt på jagt efter trusler med avanceret jagt på Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

Avanceret jagt er et forespørgselsbaseret trusselsbaseret jagtværktøj, der giver dig mulighed for at udforske op til 30 dages rå data. Du kan proaktivt undersøge hændelser i dit netværk for at finde trusselsindikatorer og -enheder. Fleksibel adgang til data gør det muligt at gå på jagt efter både kendte og potentielle trusler.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Du kan bruge de samme trusselsforespørgsler til at opbygge brugerdefinerede registreringsregler. Disse regler køres automatisk for at søge efter og derefter reagere på mistænkelige sikkerhedsbrud, forkert konfigurerede computere og andre resultater.

Denne funktion svarer til avanceret [jagt i Microsoft Defender til slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) og understøtter forespørgsler, der kontrollerer et bredere datasæt fra:

- Microsoft Defender til Slutpunkt
- Microsoft Defender til Office 365
- Microsoft Defender til skyapps
- Microsoft Defender for Identity

Hvis du vil bruge avanceret [jagt, skal du Microsoft 365 Defender](m365d-enable.md).

Du kan finde flere oplysninger om avanceret jagt på Microsoft Defender til skyapps-data i [videoen](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>Kom i gang med avanceret jagt

Vi anbefaler, at du gennemgår flere trin for hurtigt at komme i gang med avanceret jagt.

| Learning mål | Beskrivelse | Ressource |
|--|--|--|
| **Lær sproget** | Avanceret jagt er baseret på [Kusto-forespørgselssprog](/azure/kusto/query/) og understøtter samme syntaks og operatorer. Begynd at lære forespørgselssproget ved at køre din første forespørgsel. | [Oversigt over forespørgselssprog](advanced-hunting-query-language.md) |
| **Få mere at vide om, hvordan du bruger forespørgselsresultaterne** | Få mere at vide om diagrammer og forskellige måder, du kan få vist eller eksportere dine resultater på. Udforsk, hvordan du hurtigt kan justere forespørgsler, analysere ned for at få mere detaljerede oplysninger og udføre svarhandlinger. | - [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)<br /> - [Handle på forespørgselsresultater](advanced-hunting-take-action.md) |
| **Forstå skemaet** | Få en god, høj grad af forståelse af tabellerne i skemaet og deres kolonner. Få mere at vide om, hvor du skal søge efter data, når du konstruerer dine forespørgsler. | - [Skemareference](advanced-hunting-schema-tables.md) <br />- [Overgang fra Microsoft Defender til slutpunkt](advanced-hunting-migrate-from-mde.md) |
| **Få eksperttip og eksempler** | Træn gratis med vejledninger fra Microsoft-eksperter. Udforsk samlinger af foruddefinerede forespørgsler, der dækker forskellige scenarier med trusselssøgning. | - [Få ekspertkurser](advanced-hunting-expert-training.md) <br />- [Brug delte forespørgsler](advanced-hunting-shared-queries.md) <br />- [Gå på jagt](advanced-hunting-go-hunt.md) <br />- [Lede efter trusler på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md) |
| **Optimere forespørgsler og håndtere fejl** | Forstå, hvordan du opretter effektive og fejlfri forespørgsler. | - [Bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)<br />- [Håndtere fejl](advanced-hunting-errors.md) |
| **Oprette brugerdefinerede registreringsregler** | Få mere at vide om, hvordan du kan bruge avancerede forespørgselsforespørgsler til at udløse beskeder og udføre svarhandlinger automatisk. | - [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md) <br />- [Brugerdefinerede registreringsregler](custom-detection-rules.md) |

## <a name="get-access"></a>Få adgang
Hvis du vil bruge avanceret [jagt eller Microsoft 365 Defender](microsoft-365-defender.md) funktioner, har du brug for en passende rolle Azure Active Directory. [Læs om nødvendige roller og tilladelser til avanceret jagt](custom-roles.md).

Desuden bestemmes din adgang til slutpunktsdata af rollebaseret adgangskontrolindstillinger (RBAC) i Microsoft Defender til slutpunkt. [Læs om administration af adgang til Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Datas tæthed og opdateringsfrekvens
Avancerede jagtdata kan kategoriseres i to forskellige typer, som hver konsolideres forskelligt.

- **Begivenheds- eller** aktivitetsdata udfylder tabeller om beskeder, sikkerhedshændelser, systemhændelser og rutineopgaver. Avanceret jagt modtager disse data næsten umiddelbart efter de sensorer, der indsamler dem, og overfører dem til de tilsvarende skytjenester. Du kan f.eks. forespørge efter begivenhedsdata fra sunde sensorer på arbejdsstationer eller domænecontrollere, næsten umiddelbart efter at de er tilgængelige på Microsoft Defender til Slutpunkt og Microsoft Defender for Identity.
- **Enhedsdata** – udfylder tabeller med oplysninger om brugere og enheder. Disse data kommer fra både relativt statiske datakilder og dynamiske kilder, f.eks. Active Directory-poster og hændelseslogfiler. For at levere nye data opdateres tabeller med nye oplysninger hvert 15. minut og tilføjer rækker, der muligvis ikke er helt udfyldt. En gang i døgnet konsolideres data for at indsætte en post, der indeholder det nyeste og mest omfattende datasæt om hver enhed.

## <a name="time-zone"></a>Tidszone
Klokkeslætsoplysninger i avanceret jagt findes i UTC-tidszonen.

## <a name="related-topics"></a>Relaterede emner
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Få ekspertkurser](advanced-hunting-expert-training.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md)
