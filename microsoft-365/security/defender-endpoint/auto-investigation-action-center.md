---
title: Gå til Handlingscenter for at se afhjælpningshandlinger
description: Brug handlingscenter til at få vist detaljer og resultater efter en automatisk undersøgelse
keywords: handling, center, autoir, automatiseret, undersøgelse, svar, afhjælpning
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: how-to
ms.reviewer: ramarom, evaldm, isco, mabraitm, chriggs
ms.date: 01/28/2021
ms.technology: mde
ms.openlocfilehash: 7c300a6d66ae67d481b61a0a35101a0472031266
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592130"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Gå til Handlingscenter for at se afhjælpningshandlinger

Under og efter en automatiseret undersøgelse identificeres afhjælpningshandlinger ved trusselsregistreringer. Afhængigt af den pågældende trussel, og hvordan [Microsoft Defender til Slutpunkt](/windows/security/threat-protection) er konfigureret for din organisation, vil nogle afhjælpningshandlinger blive taget automatisk, og andre kræver godkendelse. Hvis du er en del af organisationens sikkerhedsteam, kan du få vist afventende og afsluttede [afhjælpningshandlinger](manage-auto-investigation.md#remediation-actions) i **Handlingscenter**.


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="new-a-unified-action-center"></a>(NY!) Et samlet handlingscenter


Vi er glade for at kunne bekendtgøre et nyt, samlet handlingscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center))!

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Handlingscenter i Microsoft 365 Defender portalen.":::

Følgende tabel sammenligner det nye, samlede handlingscenter med det forrige Handlingscenter.

|Det nye, samlede handlingscenter  |Det forrige handlingscenter  |
|---------|---------|
|Viser ventende og fuldførte handlinger for enheder og mail på ét sted <br/>([Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md) plus [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp))|Viser ventende og fuldførte handlinger for enheder <br/> ([Kun Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md) )   |
|Findes på:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Findes på:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender i</a> portalen **Handlingscenter**. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Navigere til handlingscenter i Microsoft 365 Defender portal."::: | I Microsoft 365 Defender skal du vælge **Automated investigationsAction** >  **center**. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="Navigere til handlingscenter fra Microsoft 365 Defender-portalen.":::  |

Det samlede Handlingscenter samler afhjælpningshandlinger på tværs af Defender for Endpoint og Defender Office 365. Den definerer et fælles sprog for alle afhjælpningshandlinger og giver en samlet undersøgelsesoplevelse.

Du kan bruge det samlede handlingscenter, hvis du har de rette tilladelser og ét eller flere af følgende abonnementer:

- [Defender til Slutpunkt](microsoft-defender-endpoint.md)
- [Defender til Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)

> [!TIP]
> Du kan få mere at vide under [Krav](/microsoft-365/security/mtp/prerequisites).

## <a name="using-the-action-center"></a>Brug af Handlingscenter

Sådan finder du det samlede handlingscenter i den forbedrede Microsoft 365 Defender portal:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på.
2. Vælg Handlingscenter i **navigationsruden**.

Når du besøger Handlingscenter, vises der to faner: **Ventende handlinger** og **Oversigt**. Følgende tabel opsummerer, hvad du ser på hver fane:

|Tabulator|Beskrivelse|
|---|---|
|**Afventer**|Viser en liste over handlinger, der kræver opmærksomhed. Du kan godkende eller afvise handlinger én ad gangen eller vælge flere handlinger, hvis de har samme type handling (f.eks. **karantænefil**). <p> **Tip**: Sørg for at [gennemse](manage-auto-investigation.md) og godkende (eller afvise) afventende handlinger så hurtigt som muligt, så dine automatiserede undersøgelser kan fuldføres i tide.|
|**Historik**|Fungerer som en overvågningslog for handlinger, der er blevet foretaget, f.eks.: <ul><li>Afhjælpningshandlinger, der er taget som et resultat af automatiserede undersøgelser</li><li>Afhjælpningshandlinger, der er godkendt af sikkerhedsteamet</li><li>Kommandoer, der blev kørt, og afhjælpningshandlinger, der blev anvendt under Live Response-sessioner</li><li>Afhjælpningshandlinger, der er foretaget af trusselsbeskyttelsesfunktioner i Microsoft Defender Antivirus</li></ul> <p> Indeholder en metode til at fortryde bestemte handlinger (se [Fortryd fuldførte handlinger](manage-auto-investigation.md#undo-completed-actions)).|

Du kan tilpasse, sortere, filtrere og eksportere data i Handlingscenter.

:::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Kolonner og filtre i Handlingscenter.":::

- Vælg en kolonneoverskrift for at sortere elementerne i stigende eller faldende rækkefølge.
- Brug tidsfilteret til at få vist data for den seneste dag, uge, 30 dage eller 6 måneder.
- Vælg de kolonner, du vil have vist.
- Angiv, hvor mange elementer der skal medtages på hver side med data.
- Brug filtre til at få vist netop de elementer, du vil have vist.
- Vælg **Eksportér** for at eksportere resultaterne til .csv fil.

## <a name="next-steps"></a>Næste trin

- [Få vist og godkend afhjælpningshandlinger](manage-auto-investigation.md)
- [Se den interaktive vejledning: Undersøg og afhjulpet trusler med Microsoft Defender til Slutpunkt](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Se også

- [Adressere falske positive/negativer i Microsoft Defender til slutpunkt](defender-endpoint-false-positives-negatives.md)
