---
title: Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder
description: Når der registreres trusler, kan du udføre handlinger for at reagere på og afhjælpe disse trusler.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b6d85d5032b9eb5837482649d4164e68b7c08275
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098774"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

På Microsoft 365 Defender-portalen kan dit sikkerhedsteam reagere på og afhjælpe registrerede trusler. I denne artikel gennemgås et eksempel på, hvordan du kan bruge Defender for Business.

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="view-detected-threats"></a>Vis registrerede trusler

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Læg mærke til kort på startsiden. Kort fortæller dig hurtigt, hvor mange trusler der blev registreret, samt hvor mange brugerkonti, slutpunkter (enheder) og andre aktiver der blev påvirket. Følgende billede er et eksempel på de kort, du kan se:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Skærmbillede af kort på Microsoft 365 Defender-portalen":::

3. Vælg en knap eller et link på kortet for at få vist flere oplysninger og udføre handlinger. Vores kort **Enheder med risiko omfatter** f.eks. knappen **Vis detaljer** . Hvis du vælger denne knap, kommer vi til siden **Enhedslager** , som vist på følgende billede:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Skærmbillede af enhedslager":::

   På siden **Enhedsoversigt** vises virksomhedens enheder sammen med deres risikoniveau og eksponeringsniveau.

4. Vælg et element, f.eks. en enhed. Der åbnes en pop op-rude, og der vises flere oplysninger om beskeder og hændelser, der genereres for det pågældende element, som vist på følgende billede:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Skærmbillede af pop op-ruden for en valgt enhed":::

5. Få vist de oplysninger, der vises, i pop op-vinduet. Vælg ellipsen (...) for at åbne en menu, der viser en liste over tilgængelige handlinger, som vist på følgende billede: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Skærmbillede af tilgængelige handlinger for en valgt enhed":::

6. Vælg en tilgængelig handling. Du kan f.eks. vælge **Kør antivirusscanning**, hvilket medfører, at Microsoft Defender Antivirus starter en hurtig scanning på enheden. Du kan også vælge **Start automatiseret undersøgelse** for at udløse en automatiseret undersøgelse på enheden.

## <a name="next-steps"></a>Næste trin

- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)
- [Administrer enheder i Microsoft Defender til virksomheder](mdb-manage-devices.md)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
