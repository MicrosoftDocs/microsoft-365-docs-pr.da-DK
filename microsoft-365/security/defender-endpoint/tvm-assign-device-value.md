---
title: Tildel enhedsværdi – Håndtering af trusler og sikkerhedsrisici
description: Få mere at vide om, hvordan du tildeler en enhed en lav, normal eller høj værdi for at hjælpe dig med at skelne mellem aktivprioriteter.
keywords: Microsoft Defender for Endpoint enhedsværdi, Håndtering af trusler og sikkerhedsrisici enhedsværdi, enheder med høj værdi, eksponeringsscore for enhedsværdi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: ff6d61e02ff923cc9406412c81e9a67799e6880a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477209"
---
# <a name="assign-device-value---threat-and-vulnerability-management"></a>Tildel enhedsværdi – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Definition af en enheds værdi hjælper dig med at skelne mellem aktivprioriteter. Enhedsværdien bruges til at inkorporere risikoen fra et individuelt aktiv i Håndtering af trusler og sikkerhedsrisici beregning af eksponeringspoint. Enheder, der er tildelt som "høj værdi", får mere vægt.

Du kan også bruge [api'en set device value.](set-device-value.md)

Indstillinger for enhedsværdi:

- Lav
- Normal (standard)
- Høj

Eksempler på enheder, der skal tildeles en høj værdi:

- Domænecontrollere, Active Directory
- Enheder, der er vendt mod internettet
- VIP-enheder
- Enheder, der hoster interne/eksterne produktionstjenester

## <a name="choose-device-value"></a>Vælg enhedsværdi

1. Gå til en hvilken som helst enhed side, den nemmeste sted er fra enhedens lager.

2. Vælg **Enhedsværdi** fra tre prik ud for handlingslinjen øverst på siden.

   :::image type="content" source="images/tvm-device-value-dropdown.png" alt-text="Værdiindstillingen Enhed" lightbox="images/tvm-device-value-dropdown.png":::

3. Der vises en pop op-pop op-pop-op med den aktuelle enhedsværdi, og hvad det betyder. Gennemse værdien af enheden, og vælg den, der passer bedst til din enhed.

:::image type="content" source="images/tvm-device-value-flyout.png" alt-text="Siden Enhedsværdi" lightbox="images/tvm-device-value-flyout.png":::

## <a name="how-device-value-impacts-your-exposure-score"></a>Sådan påvirker enhedsværdien din eksponeringsscore

Eksponeringsresultatet er et vægtet gennemsnit på tværs af alle enheder. Hvis du har enhedsgrupper, kan du også filtrere scoren efter enhedsgruppe.

- Normale enheder har en tykkelse på 1
- Lavværdienheder har en tykkelse på 0,75
- Enheder med høj værdi har en tykkelse på NumberOfAssets/ 10.
    - Hvis du har 100 enheder, har hver enhed med høj værdi en tykkelse på 10 (100/10)

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [API'er](next-gen-threat-and-vuln-mgt.md#apis)