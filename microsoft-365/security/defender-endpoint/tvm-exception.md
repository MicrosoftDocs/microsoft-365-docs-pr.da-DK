---
title: Opret og få vist undtagelser for sikkerhedsanbefalinger – Håndtering af trusler og sikkerhedsrisici
description: Opret og overvåg undtagelser for sikkerhedsanbefalinger i Håndtering af trusler og sikkerhedsrisici.
keywords: Microsoft Defender for Endpoint afhjælpning af tvm, Microsoft Defender for Endpoint tvm, Håndtering af trusler og sikkerhedsrisici, trussel & håndtering af sikkerhedsrisici , & håndtering af sikkerhedsrisici afhjælpning, tvm remediation intune, tvm remediation sccm
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 00d7afd9daec71a14d4b789d1d6dcfe5eaf07d83
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64477187"
---
# <a name="create-and-view-exceptions-for-security-recommendations---threat-and-vulnerability-management"></a>Opret og få vist undtagelser for sikkerhedsanbefalinger – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Som et alternativ til en afhjælpningsanmodning, når en anbefaling ikke er relevant i øjeblikket, kan du oprette undtagelser for anbefalinger. Hvis din organisation har enhedsgrupper, kan du begrænse undtagelsen til bestemte enhedsgrupper. Der kan enten oprettes undtagelser for udvalgte enhedsgrupper eller for alle enhedsgrupper, der er tidligere og nuværende.

Når der oprettes en undtagelse for en anbefaling, er anbefalingen ikke aktiv før slutningen af varigheden af undtagelsen. Tilstanden Anbefaling ændres til **Fuld undtagelse** eller **Delvis undtagelse** (efter enhedsgruppe).

## <a name="permissions"></a>Tilladelser

Kun brugere med tilladelser til "håndtering af undtagelser" kan administrere undtagelser (herunder oprettelse eller annullering). [Få mere at vide om RBAC-roller](user-roles.md).

:::image type="content" source="images/tvm-exception-permissions.png" alt-text="Tilladelse til håndtering af undtagelser" lightbox="images/tvm-exception-permissions.png":::

## <a name="create-an-exception"></a>Oprette en undtagelse

Vælg en sikkerhedsanbefaling, du vil oprette en undtagelse for, og vælg **derefter Undtagelsesindstillinger** , og udfyld formularen.

:::image type="content" source="images/tvm-exception-options.png" alt-text="Placeringen af knappen med undtagelsesindstillinger i pop op-menuen med en sikkerhedsanbefaling" lightbox="images/tvm-exception-options.png":::

### <a name="exception-by-device-group"></a>Undtagelse efter enhedsgruppe

Anvend undtagelsen på alle aktuelle enhedsgrupper, eller vælg bestemte enhedsgrupper. Fremtidige enhedsgrupper medtages ikke i undtagelsen. Enhedsgrupper, der allerede har en undtagelse, vises ikke på listen. Hvis du kun vælger visse enhedsgrupper, ændres anbefalingstilstanden fra "aktiv" til "delvis undtagelse". Tilstanden ændres til "fuld undtagelse", hvis du vælger alle enhedsgrupper.

:::image type="content" source="images/tvm-exception-device-group-500.png" alt-text="Rullemenuen Enhedsgruppe" lightbox="images/tvm-exception-device-group-500.png":::

#### <a name="filtered-views"></a>Filtrerede visninger

Hvis du har filtreret efter enhedsgruppe på en af Håndtering af trusler og sikkerhedsrisici sider, er det kun dine filtrerede enhedsgrupper, der vises som indstillinger.

Dette er knappen til at filtrere efter enhedsgruppe på alle Håndtering af trusler og sikkerhedsrisici sider:

:::image type="content" source="images/tvm-selected-device-groups.png" alt-text="Filteret for de valgte enhedsgrupper" lightbox="images/tvm-selected-device-groups.png":::

Undtagelsesvisning med filtrerede enhedsgrupper:

:::image type="content" source="images/tvm-exception-device-filter500.png" alt-text="Rullelisten for den filtrerede enhedsgruppe" lightbox="images/tvm-exception-device-filter500.png":::

#### <a name="large-number-of-device-groups"></a>Stort antal enhedsgrupper

Hvis din organisation har mere end 20 enhedsgrupper, skal du **vælge Rediger** ud for den filtrerede gruppe af enheder.

:::image type="content" source="images/tvm-exception-edit-groups.png" alt-text="Fremgangsmåden til redigering af et stort antal grupper" lightbox="images/tvm-exception-edit-groups.png":::

Der vises en pop op-pop op-pop-op-uddeling, hvor du kan søge efter og vælge de enhedsgrupper, du vil inkludere. Vælg markeringsikonet under Søg for at markere/fjerne markeringen i alle.

:::image type="content" source="images/tvm-exception-device-group-flyout-400.png" alt-text="Pop op-pop op-pop op-pop-op-gruppe med store enheder" lightbox="images/tvm-exception-device-group-flyout-400.png":::

### <a name="global-exceptions"></a>Globale undtagelser

Hvis du har globale administratortilladelser, kan du oprette og annullere en global undtagelse. Det påvirker alle **nuværende** og fremtidige enhedsgrupper i organisationen, og kun en bruger med lignende tilladelser vil kunne ændre den. Tilstanden Anbefaling ændres fra "aktiv" til "fuld undtagelse".

:::image type="content" source="images/tvm-exception-global.png" alt-text="Indstillingen global undtagelse" lightbox="images/tvm-exception-global.png":::

Nogle ting, du skal huske:

- Hvis en anbefaling er under global undtagelse, suspenderes nyligt oprettede undtagelser for enhedsgrupper, indtil den globale undtagelse er udløbet eller blevet annulleret. Derefter træder de nye undtagelser for enhedsgrupper i kraft, indtil de udløber.
- Hvis en anbefaling allerede har undtagelser for bestemte enhedsgrupper, og der oprettes en global undtagelse, suspenderes enhedsgruppens undtagelse, indtil den udløber, eller den globale undtagelse annulleres, før den udløber.

### <a name="justification"></a>Justering

Vælg din begrundelse for den undtagelse, du skal arkivere i stedet for at løse den pågældende sikkerhedsanbefaling. Udfyld justeringskonteksten, og angiv derefter varigheden af undtagelsen.

Følgende liste indeholder oplysninger om begrundelserne bag indstillingerne for undtagelser:

- **Tredjepartskontrol –** Et tredjepartsprodukt eller -software adresserer allerede denne anbefaling – Hvis du vælger denne begrundelsestype, reduceres din eksponeringsscore og din sikre score, fordi risikoen reduceres
- **Alternativ afhjælpning** – Et internt værktøj adresserer allerede denne anbefaling – Hvis du vælger denne begrundelsestype, sænkes din eksponeringsscore, og din sikre score øges, fordi risikoen reduceres
- **Risk accepted** - Poses low risk and/or implementing the recommendation is too expensive
- **Planlagt afhjælpning (udvidet periode)** – Allerede planlagt, men afventer udførelse eller godkendelse

## <a name="view-all-exceptions"></a>Få vist alle undtagelser

Gå til **fanen** Undtagelser på **siden** Afhjælpning. Du kan filtrere efter justering, type og status.

 Vælg en undtagelse for at åbne en pop op-mail med flere oplysninger. Undtagelser pr. enhedsgruppe har en liste over hver enhedsgruppe, som undtagelsen dækker, og som du kan eksportere. Du kan også få vist den relaterede anbefaling eller annullere undtagelsen.

:::image type="content" source="images/tvm-exception-view.png" alt-text="Fanen Undtagelser på siden Afhjælpning" lightbox="images/tvm-exception-view.png":::

## <a name="how-to-cancel-an-exception"></a>Sådan annullerer du en undtagelse

Hvis du vil annullere en undtagelse, skal du **gå** til fanen Undtagelser på **siden** Afhjælpning. Vælg undtagelsen.

Hvis du vil annullere undtagelsen for alle enhedsgrupper eller for en global undtagelse, skal du vælge **knappen Annuller undtagelse for alle enhedsgrupper** . Du vil kun kunne annullere undtagelser for enhedsgrupper, du har tilladelser til.

:::image type="content" source="images/tvm-exception-cancel.png" alt-text="Knappen Annuller" lightbox="images/tvm-exception-cancel.png":::

### <a name="cancel-the-exception-for-a-specific-device-group"></a>Annullere undtagelsen for en bestemt enhedsgruppe

Vælg den specifikke enhedsgruppe for at annullere undtagelsen for den. Der vises en pop op-pop op-pop-op-indstilling for enhedsgruppen, og du kan vælge **Annuller undtagelse**.

:::image type="content" source="images/tvm-exception-device-group-hover.png" alt-text="Fremgangsmåden til at vælge en bestemt enhedsgruppe" lightbox="images/tvm-exception-device-group-hover.png":::

## <a name="view-impact-after-exceptions-are-applied"></a>Få vist virkning, når undtagelserne er anvendt

På siden Sikkerhed Anbefalinger du vælge Tilpas kolonner og markere  afkrydsningsfelterne for Kun eksponerede enheder **(** efter undtagelser) og **Virkning (efter undtagelser)**.

:::image type="content" source="images/tvm-after-exceptions.png" alt-text="Indstillingerne for Tilpas kolonner" lightbox="images/tvm-after-exceptions.png":::

Kolonnen over enheder, der vises (efter undtagelser), viser de resterende enheder, der stadig er eksponeret for sårbarheder, efter undtagelserne er anvendt. Begrundelser for undtagelser, der påvirker eksponeringen omfatter "tredjepartskontrol" og "alternativ afhjælpning". Andre begrundelser reducerer ikke eksponeringen af en enhed, og de betragtes stadig som eksponerede.

Virkningen (efter undtagelser) viser den resterende effekt på eksponeringsscore eller sikre scorer, når undtagelserne er anvendt. Undtagelsesberettigelse, der påvirker resultaterne, omfatter "tredjepartskontrol" og "alternativ afhjælpning". Andre begrundelser reducerer ikke eksponeringen af en enhed, og eksponeringsscore og sikre score ændres derfor ikke.

:::image type="content" source="images/tvm-after-exceptions-table.png" alt-text="Kolonnerne i tabellen" lightbox="images/tvm-after-exceptions-table.png":::

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Afhjælpe sårbarheder](tvm-remediation.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)
