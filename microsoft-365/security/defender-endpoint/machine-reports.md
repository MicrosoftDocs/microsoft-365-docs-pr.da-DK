---
title: Tilstands- og overholdelsesrapport for enheder i Microsoft Defender for Endpoint
description: Registrer registreringer af enhedens tilstand, antivirusstatus, OPERATIVSYSTEM-platform Windows 10 versioner ved hjælp af tilstands- og overholdelsesrapporten for enheder
keywords: tilstand, antivirus, styresystemplatform, windows 10-version, version, tilstand, overholdelse, tilstand
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bf89c0e57cbe14980b15ecf6f5a88f6db2b83e84
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474019"
---
# <a name="device-health-and-compliance-report-in-microsoft-defender-for-endpoint"></a>Tilstands- og overholdelsesrapport for enheder i Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Enhedsstatusrapporten indeholder detaljerede oplysninger om enhederne i organisationen. Rapporten indeholder de mest populære oplysninger, der viser sensorens tilstand, antivirusstatus, OS-platforme Windows 10 (og Windows 11) versioner.

Dashboardet er struktureret i to sektioner:

:::image type="content" source="images/device-reports.png" alt-text="Enhedsrapporten" lightbox="images/device-reports.png":::


<br>

****

|Sektion|Beskrivelse|
|---|---|
|1|Enhedstendenser|
|2|Enhedsoversigt (dags dato)|
|||

## <a name="device-trends"></a>Enhedstendenser

Som standard viser enhedstendenserne enhedsoplysninger fra den 30-dages periode, der slutter med den seneste hele dag. Hvis du vil have et bedre perspektiv på tendenser i organisationen, kan du finjustere rapporteringsperioden ved at justere den viste tidsperiode. Hvis du vil justere tidsperioden, skal du vælge et tidsinterval fra rulleindstillingerne:

- 30 dage
- Tre måneder
- Seks måneder
- Brugerdefineret

> [!NOTE]
> Disse filtre anvendes kun på sektionen Enhedstendenser. Det påvirker ikke sektionen Enhedsoversigt.

## <a name="device-summary"></a>Enhedsoversigt

Mens tendenserne for enheder viser de mest populære enhedsoplysninger, viser enhedsoversigten enhedsoplysningerne, der er omfattet af den aktuelle dag.

> [!NOTE]
> Dataene, der afspejles i oversigtssektionen, er begrænset til 180 dage før den aktuelle dato. Hvis dags dato f.eks. er 27. marts 2019, vil dataene i oversigtssektionen afspejle tal fra d. 28. september 2018 til 27. marts 2019.
>
> Det filter, der anvendes på tendenssektionen, anvendes ikke i oversigtssektionen.

I sektionen Enhedstendenser kan du analysere ned til listen over enheder med det tilsvarende filter anvendt på den. Hvis du f.eks. klikker på den inaktive linje på kortet med sensorens tilstand, får du vist listen over enheder med resultater, der kun viser de enheder, hvis sensorstatus er inaktiv.

## <a name="device-attributes"></a>Enhedsattributter

Rapporten består af kort, der viser følgende enhedsattributter:

- **Tilstandstilstand**: viser oplysninger om sensortilstanden på enheder, hvilket giver en samlet visning af aktive enheder, der oplever forringet kommunikation, inaktiv, eller hvor der ikke kan ses nogen sensordata.
- **Antivirusstatus for aktive Windows 10 enheder**: viser antallet af enheder og status for Microsoft Defender Antivirus.
- **OS-platforme**: viser fordelingen af OS-platforme, der findes i din organisation.
- **Windows 10 versioner**: viser fordelingen af Windows 10 og deres versioner i organisationen.

## <a name="filter-data"></a>Filtrere data

Brug de angivne filtre til at medtage eller udelade enheder med bestemte attributter.

Du kan vælge flere filtre, der skal anvendes fra enhedsattributterne.

> [!NOTE]
> Disse filtre gælder **for** alle kort i rapporten.

Hvis du f.eks. vil vise data om Windows 10 enheder med tilstanden Aktiv sensor:

1. Under **Filtre > sensorens tilstand > Aktiv**.
2. Vælg derefter **OS-platforme > Windows 10**.
3. Vælg **Anvend**.

## <a name="related-topic"></a>Relateret emne

- [Rapport om trusselsbeskyttelse](threat-protection-reports.md)
