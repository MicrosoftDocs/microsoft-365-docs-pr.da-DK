---
title: Udelad enheder i Microsoft Defender til slutpunkt
description: Udelad enheder fra lagerlisten over enheder
keywords: ekskluder
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
ms.openlocfilehash: c17bea7b6a3decdb1cf20f21067c316366c2afed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705065"
---
# <a name="exclude-devices"></a>Udelad enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-threat-and-vulnerability-management"></a>Udelad enheder fra Håndtering af trusler og sikkerhedsrisici

Hvis du udelader enheder, der er inaktive, duplikerede eller uden for omfanget, kan du fokusere på at opdage og prioritere risici på dine aktive enheder. Denne handling kan også hjælpe med at afspejle en mere nøjagtig Håndtering af trusler og sikkerhedsrisici eksponeringsscore, da de ekskluderede enheder ikke er synlige i dine Håndtering af trusler og sikkerhedsrisici rapporter.

Når enhederne er udelukket, kan du ikke få vist opdaterede eller relevante oplysninger om sårbarheder og installeret software på disse enheder. Det påvirker alle Håndtering af trusler og sikkerhedsrisici, rapporter og relaterede tabeller i avanceret jagt.

Selvom funktionen til udelukkelse af enheder fjerner enhedsdata fra håndtering af sikkerhedsrisici sider og rapporter, forbliver enhederne forbundet til netværket og kan stadig være en risiko for organisationen. Du kan til enhver tid annullere udelukkelsen af enheder.

## <a name="how-to-exclude-a-device"></a>Sådan udelader du en enhed

Du kan vælge at udelukke en enkelt enhed eller flere enheder på samme tid.

### <a name="exclude-a-single-device"></a>Udelad en enkelt enhed

1. Gå til lagersiden **for enheden** , og vælg den enhed, der ikke skal udelades.
2. Vælg **Udelad** på handlingslinjen på enhedens lagerside eller i menuen Handlinger i pop op-menuen for enheden.

![Billede af menuindstillingen Udelad enhed.](images/exclude-devices-menu.png)

 3. Vælg en justering:

    - Inaktiv enhed
    - Dupliker enhed
    - Enheden findes ikke
    - Uden for området  
    - Andet

4. Skriv en note, og vælg **Udelad enhed**.

![Billede af ekskluder enhed.](images/exclude-device.png)

Du kan også udelade en enhed fra enhedens side.

> [!NOTE]
> Det anbefales ikke at udelukke aktive enheder, da det er særligt risikabelt ikke at få indsigt i oplysninger om sikkerhedsrisikoen. Hvis en enhed er aktiv, og du forsøger at udelukke den, får du vist en advarselsmeddelelse og en bekræftelses pop op, hvor du bliver spurgt, om du er sikker på, at du vil udelukke en aktiv enhed.

Det kan tage op til 10 timer, før en enhed udelades fuldstændigt håndtering af sikkerhedsrisici visninger og data.

Udeladte enheder er stadig synlige på listen enhedslager. Du kan administrere din visning af ekskluderede enheder ved at:

- Tilføjelse af **kolonnen Udelukkelsestilstand** i lagervisningen for enheder.
- Brug  **statefilteretExclusion**  til at få vist den relevante liste over enheder.

![Billede af udeladelsestilstand.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Udeladelse af masseenhed

Du kan også vælge at udelukke flere enheder på samme tid:

1. Gå til lagersiden **for enheden** , og vælg de enheder, der skal udelades.

2. Vælg Udelad på **handlingslinjen**.

3. Vælg en justering, og vælg **Udelad enhed**.

Hvis du vælger flere enheder på listen over enheder med forskellige udelukkelsesstatusser, giver pop op-pop-op'en Ekskluder valgte enheder dig oplysninger om, hvor mange af de valgte enheder der allerede er udeladt. Du kan udelukke enhederne igen, men justeringen og noterne tilsidesættes.

![Billede af masseforlad](images/exclude-device-bulk.png)

Når en enhed er udeladt, kan du, hvis du går til enhedssiden for en udeladt enhed, ikke se data for opdagede sårbarheder, lagerbeholdning af software eller sikkerhedsanbefalinger. Dataene vises heller ikke på alle sider håndtering af sikkerhedsrisici, relaterede avancerede jagttabeller og rapporten over følsomme enheder.

## <a name="stop-excluding-a-device"></a>Stop med at udelukke en enhed

Du kan når som helst stoppe med at udelukke en enhed. Når enheder ikke længere er udelukket, vil deres sikkerhedsrisikodata kunne ses på håndtering af sikkerhedsrisici sider, rapporter og i avanceret jagt. Det kan tage op til 8 timer, før ændringerne træder i kraft.

1. Gå til lager for enhed, vælg den udeladte enhed for at åbne pop op-pop op-uddelingskopien, og vælg derefter **Udeladelsesoplysninger**
2. Vælg **Stop udeladelse**

![Billede af udeladelsesoplysninger](images/exclusion-details.png)

## <a name="see-also"></a>Se også

- [Lagerenhed](machines-view-overview.md)
