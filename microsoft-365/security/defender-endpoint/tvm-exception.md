---
title: Opret og få vist undtagelser for sikkerhedsanbefalinger – Håndtering af trusler og sikkerhedsrisici
description: Opret og overvåg undtagelser for sikkerhedsanbefalinger i Håndtering af trusler og sikkerhedsrisici.
keywords: Microsoft Defender for Endpoint tvm remediation, Microsoft Defender for Endpoint tvm, Håndtering af trusler og sikkerhedsrisici, threat & håndtering af sikkerhedsrisici, threat & håndtering af sikkerhedsrisici  afhjælpning, tvm remediation intune, tvm remediation sccm
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
ms.openlocfilehash: a3986d44027824f2ba9ca508567d518cce270450
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63603075"
---
# <a name="create-and-view-exceptions-for-security-recommendations---threat-and-vulnerability-management"></a>Opret og få vist undtagelser for sikkerhedsanbefalinger – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

Som et alternativ til en afhjælpningsanmodning, når en anbefaling ikke er relevant i øjeblikket, kan du oprette undtagelser for anbefalinger. Hvis din organisation har enhedsgrupper, kan du begrænse undtagelsen til bestemte enhedsgrupper. Der kan enten oprettes undtagelser for udvalgte enhedsgrupper eller for alle enhedsgrupper, der er tidligere og nuværende.

Når der oprettes en undtagelse for en anbefaling, er anbefalingen ikke aktiv før slutningen af varigheden af undtagelsen. Tilstanden Anbefaling ændres til **Fuld undtagelse** eller **Delvis undtagelse** (efter enhedsgruppe).

## <a name="permissions"></a>Tilladelser

Kun brugere med tilladelser til "håndtering af undtagelser" kan administrere undtagelser (herunder oprettelse eller annullering). [Få mere at vide om RBAC-roller](user-roles.md).

![Visning af tilladelse til håndtering af undtagelser.](images/tvm-exception-permissions.png)

## <a name="create-an-exception"></a>Oprette en undtagelse

Vælg en sikkerhedsanbefaling, du vil oprette en undtagelse for, og vælg **derefter Undtagelsesindstillinger** , og udfyld formularen.

![Viser, hvor knappen for "undtagelsesindstillinger" er placeringen i et pop op-pop op-billede med en sikkerhedsanbefaling.](images/tvm-exception-options.png)

### <a name="exception-by-device-group"></a>Undtagelse efter enhedsgruppe

Anvend undtagelsen på alle aktuelle enhedsgrupper, eller vælg bestemte enhedsgrupper. Fremtidige enhedsgrupper medtages ikke i undtagelsen. Enhedsgrupper, der allerede har en undtagelse, vises ikke på listen. Hvis du kun vælger visse enhedsgrupper, ændres anbefalingstilstanden fra "aktiv" til "delvis undtagelse". Tilstanden ændres til "fuld undtagelse", hvis du vælger alle enhedsgrupper.

![Viser rullelisten Enhedsgruppe.](images/tvm-exception-device-group-500.png)

#### <a name="filtered-views"></a>Filtrerede visninger

Hvis du har filtreret efter enhedsgruppe på en af Håndtering af trusler og sikkerhedsrisici sider, er det kun dine filtrerede enhedsgrupper, der vises som indstillinger.

Dette er knappen til at filtrere efter enhedsgruppe på alle Håndtering af trusler og sikkerhedsrisici sider:

![Viser filteret for valgte enhedsgrupper.](images/tvm-selected-device-groups.png)

Undtagelsesvisning med filtrerede enhedsgrupper:

![Viser rullelisten filtreret enhedsgruppe.](images/tvm-exception-device-filter500.png)

#### <a name="large-number-of-device-groups"></a>Stort antal enhedsgrupper

Hvis din organisation har mere end 20 enhedsgrupper, skal du **vælge Rediger** ud for den filtrerede gruppe af enheder.

![Viser, hvordan du redigerer et stort antal grupper.](images/tvm-exception-edit-groups.png)

Der vises en pop op-pop op-pop-op-uddeling, hvor du kan søge efter og vælge de enhedsgrupper, du vil inkludere. Vælg markeringsikonet under Søg for at markere/fjerne markeringen i alle.

![Viser pop op-vinduer med store enheder.](images/tvm-exception-device-group-flyout-400.png)

### <a name="global-exceptions"></a>Globale undtagelser

Hvis du har globale administratortilladelser, kan du oprette og annullere en global undtagelse. Det påvirker alle **nuværende** og fremtidige enhedsgrupper i organisationen, og kun en bruger med lignende tilladelser vil kunne ændre den. Tilstanden Anbefaling ændres fra "aktiv" til "fuld undtagelse".

![Viser indstillingen for globale undtagelser.](images/tvm-exception-global.png)

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

![Viser fanen "Undtagelser" på siden Afhjælpning.](images/tvm-exception-view.png)

## <a name="how-to-cancel-an-exception"></a>Sådan annullerer du en undtagelse

Hvis du vil annullere en undtagelse, skal du **gå** til fanen Undtagelser på **siden** Afhjælpning. Vælg undtagelsen.

Hvis du vil annullere undtagelsen for alle enhedsgrupper eller for en global undtagelse, skal du vælge **knappen Annuller undtagelse for alle enhedsgrupper** . Du vil kun kunne annullere undtagelser for enhedsgrupper, du har tilladelser til.

![Knappen Annuller.](images/tvm-exception-cancel.png)

### <a name="cancel-the-exception-for-a-specific-device-group"></a>Annullere undtagelsen for en bestemt enhedsgruppe

Vælg den specifikke enhedsgruppe for at annullere undtagelsen for den. Der vises en pop op-pop op-pop-op-indstilling for enhedsgruppen, og du kan vælge **Annuller undtagelse**.

![Viser, hvordan du vælger en bestemt enhedsgruppe.](images/tvm-exception-device-group-hover.png)

## <a name="view-impact-after-exceptions-are-applied"></a>Få vist virkning, når undtagelserne er anvendt

På siden Sikkerhed Anbefalinger du vælge Tilpas kolonner og markere  afkrydsningsfelterne for Kun eksponerede enheder **(** efter undtagelser) og **Virkning (efter undtagelser)**.

![Viser indstillinger for tilpas kolonner.](images/tvm-after-exceptions.png)

Kolonnen over enheder, der vises (efter undtagelser), viser de resterende enheder, der stadig er eksponeret for sårbarheder, efter undtagelserne er anvendt. Begrundelser for undtagelser, der påvirker eksponeringen omfatter "tredjepartskontrol" og "alternativ afhjælpning". Andre begrundelser reducerer ikke eksponeringen af en enhed, og de betragtes stadig som eksponerede.

Virkningen (efter undtagelser) viser den resterende effekt på eksponeringsscore eller sikre scorer, når undtagelserne er anvendt. Undtagelsesberettigelse, der påvirker resultaterne, omfatter "tredjepartskontrol" og "alternativ afhjælpning". Andre begrundelser reducerer ikke eksponeringen af en enhed, og eksponeringsscore og sikre score ændres derfor ikke.

![Viser kolonnerne i tabellen.](images/tvm-after-exceptions-table.png)

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Afhjælpe sårbarheder](tvm-remediation.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Eksponeringsscore](tvm-exposure-score.md)
- [Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)
