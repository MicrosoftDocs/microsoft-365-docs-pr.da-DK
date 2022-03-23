---
title: Rapport om trusselsbeskyttelse i Microsoft Defender til Slutpunkt
description: Registrere registreringer af beskeder, kategorier og alvorsgrad ved hjælp af rapporten om trusselsbeskyttelse
keywords: registrering af beskeder, kilde, besked efter kategori, alvorsgrad for besked, beskedklassifikation, bestemmelse
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
ms.openlocfilehash: 84893d7f015ec354bc27ac706c00e864705a42e5
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63592712"
---
# <a name="threat-protection-report-in-microsoft-defender-for-endpoint"></a>Rapport om trusselsbeskyttelse i Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Rapporten om trusselsbeskyttelse indeholder detaljerede oplysninger om vigtige beskeder, der genereres i organisationen. Rapporten indeholder de mest populære oplysninger, der viser registreringskilder, kategorier, alvorsgrader, statusser, klassificeringer og bestemmelse af beskeder på tværs af tid.

Dashboardet er struktureret i to sektioner:

![Billede af rapporten om trusselsbeskyttelse.](images/threat-protection-reports.png)

Sektion|Beskrivelse
---|---
1|Beskedtendenser
2|Beskedoversigt

## <a name="alert-trends"></a>Påmindelsestendenser
Som standard viser påmindelsestendenserne beskedoplysninger fra den 30-dages periode, der slutter med den sidste hele dag. Hvis du vil have et bedre perspektiv på tendenser i organisationen, kan du finjustere rapporteringsperioden ved at justere den viste tidsperiode. Hvis du vil justere tidsperioden, skal du vælge et tidsinterval fra rulleindstillingerne:

- 30 dage
- 3 måneder
- 6 måneder
- Brugerdefineret

> [!NOTE]
> Disse filtre anvendes kun på sektionen Påmindelsestendenser. Det påvirker ikke sektionen med beskedoversigten.

## <a name="alert-summary"></a>Beskedoversigt

Selvom tendenserne for påmindelsestendenser viser de mest populære oplysninger, viser oversigten over påmindelsen beskedoplysninger med oplysninger om den aktuelle dag.

 Beskedens oversigt giver dig mulighed for at analysere ned til en bestemt beskedkø med det tilsvarende filter anvendt på den. Hvis du f.eks. klikker på Slutpunktsregistrering og -svar-linjen på kortet Registreringskilder, får du beskedkøen med resultater, der kun viser beskeder, der er genereret Slutpunktsregistrering og -svar registreringer.

> [!NOTE]
> Dataene, der afspejles i oversigtssektionen, er begrænset til 180 dage før den aktuelle dato. Hvis dags dato f.eks. er 5. november 2019, vil dataene i oversigtssektionen afspejle tal begyndende fra 5. maj 2019 til 5. november 2019.
>
> Det filter, der anvendes på tendenssektionen, anvendes ikke i oversigtssektionen.

## <a name="alert-attributes"></a>Beskedattributter

Rapporten består af kort, der viser følgende beskedattributter:

- **Registreringskilder**: viser oplysninger om de sensor- og registreringsteknologier, der leverer de data, der bruges af Microsoft Defender til slutpunkt til at udløse beskeder.
- **Trusselskategorier**: Viser typerne af trussels- eller angrebsaktivitet, der udløste beskeder, hvilket angiver mulige fokusområder for dine sikkerhedshandlinger.
- **Alvorsgrad**: Viser alvorsniveauet for beskeder, der angiver den kollektive potentielle virkning af trusler i organisationen og det svarniveau, der skal bruges for at håndtere dem.
- **Status**: Viser opløsningsstatus for beskeder, der angiver effektiviteten af dine manuelle beskedsvar og automatiseret afhjælpning (hvis det er aktiveret).
- **Klassificering & bestemmelse**: viser, hvordan du har klassificeret vigtige beskeder efter opløsning, uanset om du har klassificeret dem som faktiske trusler (egentlige advarsler) eller som forkerte registreringer (falske beskeder). Disse kort viser også bestemmelse af løste beskeder, hvilket giver yderligere indsigt, f.eks. de typer faktiske trusler, der blev fundet, eller de legitime aktiviteter, der blev fundet forkert.

## <a name="filter-data"></a>Filtrere data

Brug de angivne filtre til at medtage eller udelade beskeder med bestemte attributter.

> [!NOTE]
> Disse filtre gælder **for** alle kort i rapporten.

Hvis du f.eks. kun vil have vist data om vigtige beskeder om høj alvorsgrad:

1. Under **Hændelser & beskeder om** \> **>** \> **skal** du vælge **Høj**.
2. Sørg for, at alle andre **indstillinger** under Alvorsgrad er fravalgt.
3. Vælg **Anvend**.

## <a name="related-topic"></a>Relateret emne

- [Tilstands- og overholdelsesrapport for enheder](machine-reports.md)
