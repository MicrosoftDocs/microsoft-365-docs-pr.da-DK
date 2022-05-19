---
title: Besøg Handlingscenter for at se afhjælpningshandlinger
description: Brug Løsningscenter til at få vist detaljer og resultater efter en automatiseret undersøgelse
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
ms.technology: mde
ms.openlocfilehash: 6a2cc5d4315c5dd64a852c74176272061789b1ba
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535398"
---
# <a name="visit-the-action-center-to-see-remediation-actions"></a>Besøg Handlingscenter for at se afhjælpningshandlinger

Under og efter en automatiseret undersøgelse identificeres afhjælpningshandlinger for trusselsregistreringer. Afhængigt af den specifikke trussel, og hvordan [automatiserede undersøgelses- og afhjælpningsfunktioner er konfigureret](configure-automated-investigations-remediation.md) for din organisation, udføres nogle afhjælpningshandlinger automatisk, og andre kræver godkendelse. Hvis du er en del af organisationens team for sikkerhedshandlinger, kan du få vist ventende og fuldførte [afhjælpningshandlinger](manage-auto-investigation.md#remediation-actions) i **Løsningscenter**.

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

## <a name="the-unified-action-center"></a>Det samlede løsningscenter

For nylig blev Løsningscenter opdateret. Du har nu en unified Action Center-oplevelse. Hvis du vil have adgang til dit Løsningscenter, skal du gå til [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) og logge på.

:::image type="content" source="images/mde-action-center-unified.png" alt-text="Siden Løsningscenter på Microsoft 365 Defender-portalen" lightbox="images/mde-action-center-unified.png":::

### <a name="whats-changed"></a>Hvad er ændret?

I følgende tabel sammenlignes det nye samlede løsningscenter med det forrige Løsningscenter.

|Det nye unified Action Center  |Det forrige Handlingscenter  |
|---------|---------|
|Viser ventende og fuldførte handlinger for enheder og mail på én placering <br/>([Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) plus [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp))|Viser ventende og fuldførte handlinger for enheder <br/> (kun [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md))   |
|Er placeret på:<br/>[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)         |Er placeret på:<br/>[https://securitycenter.windows.com/action-center](https://securitycenter.windows.com/action-center)     |
| Vælg **Løsningscenter** <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">på Microsoft 365 Defender portal</a>. <p>:::image type="content" source="images/action-center-nav-new.png" alt-text="Navigationsruden til Løsningscenter på Microsoft 365 Defender-portalen" lightbox="images/action-center-nav-new.png"::: | På Microsoft 365 Defender-portalen skal du vælge **Automatiserede undersøgelserAction** >  **Center**. <p>:::image type="content" source="images/action-center-nav-old.png" alt-text="En ældre version af navigationsruden til Løsningscenter på Microsoft 365 Defender portalen" lightbox="images/action-center-nav-old.png":::  |

I Unified Action Center samles afhjælpningshandlinger på tværs af Defender for Endpoint og Defender for Office 365. Den definerer et fælles sprog for alle afhjælpningshandlinger og giver en samlet undersøgelsesoplevelse.

Du kan bruge Unified Action Center, hvis du har de nødvendige tilladelser og et eller flere af følgende abonnementer:

- [Microsoft 365 Defender](/microsoft-365/security/mtp/microsoft-threat-protection)
- [Defender for Endpoint](microsoft-defender-endpoint.md)
- [Defender for Office 365](/microsoft-365/security/office-365-security/office-365-atp)
- [Defender for Business](../defender-business/mdb-overview.md)

## <a name="using-the-action-center"></a>Brug af Løsningscenter

Sådan kommer du til unified Action Center på den forbedrede Microsoft 365 Defender-portal:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og log på.

2. Vælg **Løsningscenter** i navigationsruden.

3. Brug fanerne **Ventende handlinger** og **Oversigt** . I følgende tabel opsummeres det, du får vist under hver fane:

   |Tab|Beskrivelse|
   |---|---|
   |**Ventende**|Viser en liste over handlinger, der kræver opmærksomhed. Du kan godkende eller afvise handlinger én ad gangen eller vælge flere handlinger, hvis de har samme type handling (f.eks **. Karantænefil**). <p> **TIP**: Sørg for at [gennemse og godkende (eller afvise) ventende handlinger](manage-auto-investigation.md) så hurtigt som muligt, så dine automatiserede undersøgelser kan fuldføres rettidigt.|
   |**Historie**|Fungerer som en overvågningslog for handlinger, der blev udført, f.eks.: <ul><li>Afhjælpningshandlinger, der blev taget som følge af automatiserede undersøgelser</li><li>Afhjælpningshandlinger, der blev godkendt af dit team for sikkerhedshandlinger</li><li>Kommandoer, der blev kørt, og afhjælpningshandlinger, der blev anvendt under Live Response-sessioner</li><li>Afhjælpningshandlinger, der blev taget af funktioner til trusselsbeskyttelse i Microsoft Defender Antivirus</li></ul> <p> Giver dig mulighed for at fortryde visse handlinger (se [Fortryd fuldførte handlinger](manage-auto-investigation.md#undo-completed-actions)).|

4. Hvis du vil tilpasse, sortere, filtrere og eksportere data i Løsningscenter, skal du benytte en eller flere af følgende fremgangsmåder:

   :::image type="content" source="images/new-action-center-columnsfilters.png" alt-text="Løsningscenter med kolonner og filtre" lightbox="images/new-action-center-columnsfilters.png":::

   - Vælg en kolonneoverskrift for at sortere elementer i stigende eller faldende rækkefølge.
   - Brug tidsperiodefilteret til at få vist data for den seneste dag, uge, 30 dage eller 6 måneder.
   - Vælg de kolonner, du vil have vist.
   - Angiv, hvor mange elementer der skal medtages på hver side med data.
   - Brug filtre til kun at få vist de elementer, du vil have vist.
   - Vælg **Eksportér** for at eksportere resultater til en .csv fil.

## <a name="next-steps"></a>Næste trin

- [Få vist og godkend afhjælpningshandlinger](manage-auto-investigation.md)
- [Se den interaktive vejledning: Undersøg og afhjælp trusler med Microsoft Defender for Endpoint](https://aka.ms/MDATP-IR-Interactive-Guide)

## <a name="see-also"></a>Se også

- [Adresser falske positive/negativer i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)
- [Sammenlign sikkerhedsfunktioner i Microsoft 365 planer for små og mellemstore virksomheder](../defender-business/compare-mdb-m365-plans.md)
