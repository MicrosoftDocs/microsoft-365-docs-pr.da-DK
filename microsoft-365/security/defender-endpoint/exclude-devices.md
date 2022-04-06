---
title: Udelad enheder i Microsoft Defender for Endpoint
description: Udelad enheder fra enhedens lagerliste
keywords: Udelukke
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: cbfc82f56cc1922a663c31defe30dc61c2d3dd9b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664144"
---
# <a name="exclude-devices"></a>Udelad enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-threat-and-vulnerability-management"></a>Udelad enheder fra Håndtering af trusler og sikkerhedsrisici

Hvis du udelader enheder, der er inaktive, duplikerede eller uden for omfanget, kan du fokusere på at finde og prioritere risiciene på dine aktive enheder. Denne handling kan også hjælpe med at afspejle en mere præcis Håndtering af trusler og sikkerhedsrisici eksponeringsscore, da de ekskluderede enheder ikke er synlige i dine Håndtering af trusler og sikkerhedsrisici rapporter.

Når enheder er udelukket, kan du ikke få vist opdaterede eller relevante oplysninger om sikkerhedsrisici og installeret software på disse enheder. Det påvirker alle Håndtering af trusler og sikkerhedsrisici sider, rapporter og relaterede tabeller i avanceret jagt.

Selvom funktionen til enhedsudeladelse fjerner enhedsdataene fra håndtering af sikkerhedsrisici sider og rapporter, forbliver enhederne tilsluttet netværket og kan stadig være en risiko for organisationen. Du kan når som helst annullere enhedsudeladelse.

## <a name="how-to-exclude-a-device"></a>Sådan ekskluderer du en enhed

Du kan vælge at udelade en enkelt enhed eller flere enheder på samme tid.

### <a name="exclude-a-single-device"></a>Udelad en enkelt enhed

1. Gå til siden **Enhedsoversigt** , og vælg den enhed, der skal udelades.
2. Vælg **Udelad** på handlingslinjen på enhedens lagerside eller i menuen Handlinger i enhedens pop op-vindue.

   ![Billede af menuindstillingen Ekskluder enhed.](images/exclude-devices-menu.png)

3. Vælg en begrundelse:

    - Inaktiv enhed
    - Dupliker enhed
    - Enheden findes ikke
    - Uden for området
    - Andet

4. Skriv en note, og vælg **Udelad enhed**.

![Billede af ekskluderingsenhed.](images/exclude-device.png)

Du kan også udelade en enhed fra dens enhedsside.

> [!NOTE]
> Det anbefales ikke at udelade aktive enheder, da det er særligt risikabelt ikke at have indblik i oplysningerne om deres sårbarhed. Hvis en enhed er aktiv, og du forsøger at ekskludere den, får du vist en advarsel og et pop op-pop op-meddelelse med bekræftelse, hvor du bliver spurgt, om du er sikker på, at du vil ekskludere en aktiv enhed.

Det kan tage op til 10 timer, før en enhed er helt udelukket fra håndtering af sikkerhedsrisici visninger og data.

Udeladte enheder er stadig synlige på enhedsoversigtslisten. Du kan administrere din visning af udeladte enheder ved at:

- Tilføjelse af kolonnen **Udeladelsestilstand** til enhedslagervisningen.
- Brug af filteret **Udeladelsestilstand** til at få vist den relevante liste over enheder.

![Billede af udeladelsestilstand.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Masseenhedsudeladelse

Du kan også vælge at udelade flere enheder på samme tid:

1. Gå til siden **Enhedsoversigt** , og vælg de enheder, der skal udelades.

2. Vælg **Udelad** på handlingslinjen.

3. Vælg en justering, og vælg **Udelad enhed**.

Hvis du vælger flere enheder på enhedslisten med forskellige udelukkelsesstatusser, giver pop op-vinduet Ekskluder valgte enheder dig oplysninger om, hvor mange af de valgte enheder der allerede er udelukket. Du kan udelade enhederne igen, men justeringen og noterne tilsidesættes.

![Billede af masse-udelad](images/exclude-device-bulk.png)

Når en enhed er udelukket, kan du ikke se data for registrerede sikkerhedsrisici, softwareoversigt eller sikkerhedsanbefalinger, hvis du går til enhedssiden for en ekskluderet enhed. Dataene vises heller ikke på håndtering af sikkerhedsrisici sider, relaterede avancerede jagttabeller og rapporten over sårbare enheder.

## <a name="stop-excluding-a-device"></a>Stop med at udelade en enhed

Du kan til enhver tid stoppe med at udelade en enhed. Når enheder ikke længere er udelukket, vil deres sårbarhedsdata være synlige på håndtering af sikkerhedsrisici sider, rapporter og i avanceret jagt. Det kan tage op til 8 timer, før ændringerne træder i kraft.

1. Gå til enhedsoversigten, vælg den ekskluderede enhed for at åbne pop op-vinduet, og vælg derefter **Udeladelsesoplysninger**
2. Vælg **Stop udeladelse**

![Billede af oplysninger om udeladelse](images/exclusion-details.png)

## <a name="see-also"></a>Se også

- [Enhedslager](machines-view-overview.md)
