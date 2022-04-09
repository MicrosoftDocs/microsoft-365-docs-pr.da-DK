---
title: Oversigt - Avanceret jagt
description: Få mere at vide om avancerede jagtforespørgsler i Microsoft 365, og hvordan du bruger dem til proaktivt at finde trusler og svagheder i dit netværk
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede opdagelser, skema, kusto
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
ms.openlocfilehash: 1ee8d8fbd3b1a56f83106ffaf6be937fa984c272
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731433"
---
# <a name="proactively-hunt-for-threats-with-advanced-hunting-in-microsoft-365-defender"></a>Proaktivt jagt efter trusler med avanceret jagt i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Avanceret jagt er et forespørgselsbaseret trusselsjagtværktøj, der giver dig mulighed for at udforske op til 30 dages rådata. Du kan proaktivt inspicere hændelser i dit netværk for at finde trusselsindikatorer og -enheder. Den fleksible adgang til data gør det muligt at jagte både kendte og potentielle trusler uden begrænsninger.
<br><br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4G6DO]

Du kan bruge de samme trusselsjagtforespørgsler til at oprette brugerdefinerede registreringsregler. Disse regler kører automatisk for at kontrollere for og derefter reagere på mistanke om brudaktivitet, forkert konfigurerede maskiner og andre resultater.

Denne funktion svarer til [avanceret jagt i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview) og understøtter forespørgsler, der kontrollerer et bredere datasæt fra:

- Microsoft Defender for Endpoint
- Microsoft Defender for Office 365
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Identity

Hvis du vil bruge avanceret jagt, [skal du aktivere Microsoft 365 Defender](m365d-enable.md).

Du kan finde flere oplysninger om avanceret jagt i Microsoft Defender for Cloud Apps data i [videoen](https://www.microsoft.com/en-us/videoplayer/embed/RWFISa). 

## <a name="get-started-with-advanced-hunting"></a>Kom i gang med avanceret jagt

Vi anbefaler, at du gennemgår flere trin for hurtigt at komme i gang med avanceret jagt.

| Learning mål | Beskrivelse | Ressource |
|--|--|--|
| **Lær sproget** | Avanceret jagt er baseret på [Kusto-forespørgselssprog](/azure/kusto/query/), der understøtter den samme syntaks og operatorer. Begynd at lære forespørgselssproget ved at køre din første forespørgsel. | [Oversigt over forespørgselssprog](advanced-hunting-query-language.md) |
| **Få mere at vide om, hvordan du bruger forespørgselsresultaterne** | Få mere at vide om diagrammer og forskellige måder, du kan få vist eller eksportere dine resultater på. Udforsk, hvordan du hurtigt kan finjustere forespørgsler, foretage detailudledning for at få mere detaljerede oplysninger og udføre svarhandlinger. | - [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)<br /> - [Udfør en handling på forespørgselsresultater](advanced-hunting-take-action.md) |
| **Forstå skemaet** | Få en god forståelse af tabellerne i skemaet og deres kolonner på højt niveau. Få mere at vide om, hvor du kan søge efter data, når du konstruerer dine forespørgsler. | - [Skemareference](advanced-hunting-schema-tables.md) <br />- [Overgang fra Microsoft Defender for Endpoint](advanced-hunting-migrate-from-mde.md) |
| **Få eksperttips og eksempler** | Oplær gratis med guider fra Microsoft-eksperter. Udforsk samlinger af foruddefinerede forespørgsler, der dækker forskellige trusselsjagtscenarier. | - [Få ekspertuddannelse](advanced-hunting-expert-training.md) <br />- [Brug delte forespørgsler](advanced-hunting-shared-queries.md) <br />- [Gå på jagt](advanced-hunting-go-hunt.md) <br />- [Jagt efter trusler på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md) |
| **Optimer forespørgsler, og håndter fejl** | Forstå, hvordan du opretter effektive og fejlfrie forespørgsler. | - [Forespørg om bedste praksis](advanced-hunting-best-practices.md)<br />- [Håndter fejl](advanced-hunting-errors.md) |
| **Opret regler for brugerdefineret registrering** | Forstå, hvordan du kan bruge avancerede jagtforespørgsler til at udløse beskeder og udføre svarhandlinger automatisk. | - [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md) <br />- [Regler for brugerdefineret registrering](custom-detection-rules.md) |

## <a name="get-access"></a>Få adgang
Hvis du vil bruge avanceret jagt eller andre [Microsoft 365 Defender](microsoft-365-defender.md) egenskaber, skal du have en passende rolle i Azure Active Directory. [Læs om påkrævede roller og tilladelser til avanceret jagt](custom-roles.md).

Din adgang til slutpunktsdata bestemmes også af RBAC-indstillinger (role-based access control) i Microsoft Defender for Endpoint. [Læs om administration af adgang til Microsoft 365 Defender](m365d-permissions.md).


## <a name="data-freshness-and-update-frequency"></a>Opdateringshyppighed og opdateringshyppighed for data
Avancerede jagtdata kan kategoriseres i to forskellige typer, der hver især konsolideres forskelligt.

- **Hændelses- eller aktivitetsdata** – udfylder tabeller om beskeder, sikkerhedshændelser, systemhændelser og rutinevurderinger. Avanceret jagt modtager disse data næsten umiddelbart efter sensorerne, der indsamler dem, overfører dem til de tilsvarende cloudtjenester. Du kan f.eks. forespørge om hændelsesdata fra sunde sensorer på arbejdsstationer eller domænecontrollere næsten umiddelbart efter, at de er tilgængelige på Microsoft Defender for Endpoint og Microsoft Defender for Identity.
- **Objektdata** – udfylder tabeller med oplysninger om brugere og enheder. Disse data kommer fra både relativt statiske datakilder og dynamiske kilder, f.eks. Active Directory-poster og hændelseslogge. For at levere nye data opdateres tabeller med nye oplysninger hvert 15. minut og tilføjer rækker, der muligvis ikke er udfyldt fuldt ud. Hver 24. time konsolideres data for at indsætte en post, der indeholder det nyeste og mest omfattende datasæt om hvert objekt.

## <a name="time-zone"></a>Tidszone
Tidsoplysningerne i avanceret jagt er i UTC-tidszonen.

## <a name="related-topics"></a>Relaterede emner
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Få ekspertkurser](advanced-hunting-expert-training.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over brugerdefinerede registreringer](custom-detections-overview.md)
