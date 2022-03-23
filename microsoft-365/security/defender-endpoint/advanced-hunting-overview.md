---
title: Oversigt over avanceret jagt i Microsoft Defender til slutpunkt
description: Brug muligheder for trusselssøgning i Microsoft Defender til slutpunkt til at oprette forespørgsler, der finder trusler og fanger i dit netværk
keywords: avanceret jagt, trusselssporing, cybertrusler på jagt, mdatp, microsoft defender atp, microsoft defender for slutpunkt, wdatp, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto, tidszone, UTC
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2e1b6a5bb77dc757861a5d7f56d8a4380c6fc6c1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63591287"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting"></a>Proaktivt lede efter trusler med avanceret jagt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhunting-abovefoldlink)

Avanceret jagt er et forespørgselsbaseret værktøj til trusselssøgning, som giver dig mulighed for at udforske op til 30 dages rå data. Du kan proaktivt undersøge hændelser i dit netværk for at finde trusselsindikatorer og -enheder. Fleksibel adgang til data gør det muligt at gå på jagt efter både kendte og potentielle trusler.

Watch this video for a quick overview of advanced hunting and a short tutorial that will get you started fast.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bGqo]

Du kan bruge de samme trusselsforespørgsler til at opbygge brugerdefinerede registreringsregler. Disse regler køres automatisk for at søge efter og derefter reagere på mistænkelige sikkerhedsbrud, forkert konfigurerede computere og andre resultater.

> [!TIP]
> Brug [avanceret jagt på Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview) til at lede efter trusler ved hjælp af data fra Defender til Slutpunkt, Microsoft Defender til Office 365, Microsoft Defender til skyapps og Microsoft Defender for Identity. [Slå Microsoft 365 Defender til](/microsoft-365/security/defender/m365d-enable).

Få mere at vide om, hvordan du flytter dine avancerede arbejdsprocesser på jagt fra Microsoft Defender til Microsoft 365 Defender i [Overfør avancerede forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="get-started-with-advanced-hunting"></a>Kom i gang med avanceret jagt

Gennemgå følgende trin for at få din avancerede viden til at lede på en ny måde.

Vi anbefaler, at du går gennem flere trin for hurtigt at komme i gang med avanceret jagt.

<br>

****

|Learning mål|Beskrivelse|Ressource|
|---|---|---|
|**Lær sproget**|Avanceret jagt er baseret på [Kusto-forespørgselssprog](/azure/kusto/query/) og understøtter samme syntaks og operatorer. Begynd at lære forespørgselssproget ved at køre din første forespørgsel.|[Oversigt over forespørgselssprog](advanced-hunting-query-language.md)|
|**Få mere at vide om, hvordan du bruger forespørgselsresultaterne**|Få mere at vide om diagrammer og forskellige måder, du kan få vist eller eksportere dine resultater på. Udforsk, hvordan du hurtigt kan justere forespørgsler og analysere ned for at få mere detaljerede oplysninger.|[Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)|
|**Forstå skemaet**|Få en god, høj grad af forståelse af tabellerne i skemaet og deres kolonner. Få mere at vide om, hvor du skal søge efter data, når du konstruerer dine forespørgsler.|[Skemareference](advanced-hunting-schema-reference.md)|
|**Bruge foruddefinerede forespørgsler**|Udforsk samlinger af foruddefinerede forespørgsler, der dækker forskellige scenarier med trusselssøgning.|[Delte forespørgsler](advanced-hunting-shared-queries.md)|
|**Optimere forespørgsler og håndtere fejl**|Forstå, hvordan du opretter effektive og fejlfri forespørgsler.|[Bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md) <p> [Håndtere fejl](advanced-hunting-errors.md)|
|**Få den mest komplette dækning**|Brug overvågningsindstillinger for at sikre bedre datadækning for din organisation.|[Udvid avanceret jagtdækning](advanced-hunting-extend-data.md)|
|**Kør en hurtig undersøgelse**|Kør hurtigt en avanceret forespørgsel for at undersøge mistænkelig aktivitet.|[Hurtig jagt på enheds- eller begivenhedsoplysninger med *gå på jagt*](advanced-hunting-go-hunt.md)|
|**Indeholder trusler og adressering af kompromiser**|Svar på angreb ved at modne filer, begrænse eksekvering af apps og andre handlinger|[Tag skridtet videre med avancerede resultater af en forespørgsel](advanced-hunting-take-action.md)|
|**Oprette brugerdefinerede registreringsregler**|Få mere at vide om, hvordan du kan bruge avancerede forespørgselsforespørgsler til at udløse beskeder og udføre svarhandlinger automatisk.|[Oversigt over brugerdefinerede registreringer](overview-custom-detections.md) <p> [Brugerdefinerede registreringsregler](custom-detection-rules.md)|
|

## <a name="data-freshness-and-update-frequency"></a>Datas tæthed og opdateringsfrekvens

Avancerede jagtdata kan kategoriseres i to forskellige typer, som hver konsolideres forskelligt.

- **Begivenheds- eller** aktivitetsdata: Udfylder tabeller om beskeder, sikkerhedshændelser, systemhændelser og rutineopgaver. Avanceret jagt modtager disse data næsten umiddelbart efter de sensorer, der indsamler dem, og overfører dem til Defender til slutpunktet.
- **Enhedsdata**: Udfylder tabeller med konsoliderede oplysninger om brugere og enheder. Disse data kommer fra både relativt statiske datakilder og dynamiske kilder, f.eks. Active Directory-poster og hændelseslogfiler. For at levere nye data opdateres tabeller med nye oplysninger hvert 15. minut og tilføjer rækker, der muligvis ikke er helt udfyldt. En gang i døgnet konsolideres data for at indsætte en post, der indeholder det nyeste og mest omfattende datasæt om hver enhed.

## <a name="time-zone"></a>Tidszone

Klokkeslætsoplysninger i avanceret jagt befinder sig i øjeblikket i UTC-tidszonen.

## <a name="related-topics"></a>Relaterede emner

- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Forstå skemaet](advanced-hunting-schema-reference.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over brugerdefinerede registreringer](overview-custom-detections.md)
- [Storage kontooversigt](/azure/storage/common/storage-account-overview)
- [Azure Event Hubs – En stor datastreamingplatform og begivenhedstjeneste til inngestion](/azure/event-hubs/event-hubs-about)
