---
title: Microsoft Defender for Identity sikkerhedsadvarsler i Microsoft 365 Defender
description: Få mere at vide om, hvordan du administrerer og gennemser sikkerhedsadvarsler, der er Microsoft Defender for Identity i Microsoft 365 Defender
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 3023dc05550aeee5a9d47bb7561eb221c6d1c588
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465811"
---
# <a name="defender-for-identity-security-alerts-in-microsoft-365-defender"></a>Defender til identitetssikkerhedsbeskeder i Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender
- Defender for Identity

I denne artikel forklares det grundlæggende om, hvordan [du Microsoft Defender for Identity med](/defender-for-identity) sikkerhedsadvarsler [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Defender til identitetsbeskeder er indbygget i Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">med</a> et dedikeret sideformat for identitetsbeskeder. Dette markerer det første trin på rejsen til [at introducere den fulde Microsoft Defender for Identity oplevelse Microsoft 365 Defender](/defender-for-identity/defender-for-identity-in-microsoft-365-defender).

Den nye side med identitetsbeskeder giver Microsoft Defender for Identity bedre signal mellem domæner og nye muligheder for automatiseret identitetssvar. Det sikrer, at du er sikker og hjælper med at forbedre effektiviteten af dine sikkerhedshandlinger.

En af fordelene ved at undersøge beskeder [via Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender) er, Microsoft Defender for Identity beskeder yderligere korreleres med oplysninger, der er indhentet fra hvert af de andre produkter i pakken. Disse forbedrede beskeder svarer til de andre Microsoft 365 Defender, der stammer fra [Microsoft Defender for Office 365](/microsoft-365/security/office-365-security) og [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint). Den nye side eliminerer effektivt behovet for at navigere til en anden produktportal for at undersøge beskeder, der er knyttet til identitet.

Beskeder, der kommer fra Defender for Identity, kan nu udløse Microsoft 365 Defender-funktioner til automatisk undersøgelse og svar [(AIR](/microsoft-365/security/defender/m365d-autoir)), herunder automatisk afhjælpning af beskeder og afhjælpning af værktøjer og processer, der kan bidrage til den mistænkelige aktivitet.

> [!IMPORTANT]
> Som en del af dine Microsoft 365 Defender har nogle indstillinger og detaljer ændret sig fra deres placering i Defender for Identity-portalen. Læs oplysningerne nedenfor for at finde ud af, hvor du kan finde både de velkendte og nye funktioner.

## <a name="review-security-alerts"></a>Gennemse sikkerhedsadvarsler

 Beskeder kan **tilgås** fra flere forskellige steder, herunder siden Vigtige beskeder, siden Hændelser, siderne for individuelle enheder og fra den **Avancerede jagtside**. I dette eksempel gennemgår vi **siden Vigtige beskeder**.

I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> skal du **gå til & og** derefter til **Beskeder**.

:::image type="content" source="../../media/defender-identity/incidents-alerts.png" alt-text="Menupunktet Vigtige beskeder" lightbox="../../media/defender-identity/incidents-alerts.png":::

For at få vist beskeder fra Defender for Identity skal du øverst til højre vælge **Filtrer** og derefter under **Tjenestekilder** vælge **Microsoft Defender for Identity** og vælge **Anvend**:

:::image type="content" source="../../media/defender-identity/filter-defender-for-identity.png" alt-text="Filteret for Defender for Identity-hændelserne" lightbox="../../media/defender-identity/filter-defender-for-identity.png":::

Beskederne vises med oplysninger i følgende **kolonner: Navn** på besked, **Mærker****,** Alvorsgrad **,** Undersøgelsestilstand, **Status****, Kategori****,** Registreringskilde **, På** påvirkede **aktiver, Første** aktivitet og **Seneste aktivitet**.

:::image type="content" source="../../media/defender-identity/filtered-alerts.png" alt-text="Defender for Identity-hændelserne" lightbox="../../media/defender-identity/filtered-alerts.png":::

## <a name="manage-alerts"></a>Administrer beskeder

Hvis du klikker **på beskedens** navn for en af beskederne, går du til siden med oplysninger om beskeden. I venstre rude får du vist en oversigt over, hvad **der skete**:

:::image type="content" source="../../media/defender-identity/what-happened.png" alt-text="Ruden Hvad skete der?" lightbox="../../media/defender-identity/what-happened.png":::

Over feltet **Hvad skete** der er knapperne for **Konti**, **Destinationsvært** **og Kildevært** for beskeden. Ved andre beskeder vises der muligvis knapper til at få mere at vide om yderligere værter, konti, IP-adresser, domæner og sikkerhedsgrupper. Vælg en af dem for at få flere oplysninger om de involverede enheder.

I højre rude får du vist detaljerne **om besked**. Her kan du se flere detaljer og udføre flere opgaver:

- **Klassificer** denne besked – Her kan du angive denne besked **som en sand eller** **falsk besked**

    :::image type="content" source="../../media/defender-identity/classify-alert.png" alt-text="Den side, hvor du kan klassificere en besked" lightbox="../../media/defender-identity/classify-alert.png":::

- **Beskedtilstand** – I **Angiv klassificering** kan du klassificere beskeden som **Sand** eller **Falsk**. I **Tildelt til** kan du tildele beskeden til dig selv eller fjerne den.

    :::image type="content" source="../../media/defender-identity/alert-state.png" alt-text="Ruden Beskedtilstand" lightbox="../../media/defender-identity/alert-state.png":::

- **Beskeddetaljer** **– Under Vigtige** oplysninger kan du finde flere oplysninger om den specifikke besked, følge et link til dokumentationen om typen af besked, se, hvilken hændelse beskeden er knyttet til, gennemse eventuelle automatiserede undersøgelser, der er knyttet til denne beskedtype, og se de påknyttede enheder og brugere.

   :::image type="content" source="../../media/defender-identity/alert-details.png" alt-text="Siden med beskedoplysninger" lightbox="../../media/defender-identity/alert-details.png":::

- **Kommentarer & oversigten** – Her kan du føje dine kommentarer til beskeden og se historikken for alle handlinger, der er knyttet til beskeden.

    :::image type="content" source="../../media/defender-identity/comments-history.png" alt-text="Siden & kommentarer" lightbox="../../media/defender-identity/comments-history.png":::

- **Administrer besked** – Hvis du vælger **Administrer besked**, kommer du til en rude, hvor du kan redigere:
  - **Status** – Du kan vælge **Ny**, **Løst** eller **I gang**.
  - **Klassificering** – Du kan vælge **Sand eller** **Falsk besked**.
  - **Kommentar** – Du kan tilføje en kommentar om beskeden.

    Hvis du vælger de tre prik ud for Administrer **besked, kan** du Kontakte en trusselsekspert **, Eksportere** beskeden til en Excel-fil eller  **Link til en anden hændelse**.

    :::image type="content" source="../../media/defender-identity/manage-alert.png" alt-text="Indstillingen Administrer besked" lightbox="../../media/defender-identity/manage-alert.png":::

    > [!NOTE]
    > I den Excel fil har du nu to tilgængelige links: **Vis i Microsoft Defender for Identity** **og Vis i Microsoft 365 Defender**. Hvert link bringer dig til den relevante portal og giver oplysninger om beskeden der.

## <a name="see-also"></a>Se også

- [Undersøg beskeder i Microsoft 365 Defender](../defender/investigate-alerts.md)
