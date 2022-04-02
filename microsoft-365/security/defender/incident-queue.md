---
title: Prioriter hændelser i Microsoft 365 Defender
description: Få mere at vide om, hvordan du filtrerer hændelser fra hændelseskøen i Microsoft 365 Defender
keywords: hændelse, kø, oversigt, enheder, identiteter, brugere, postkasse, mail, hændelser, analysere, svar, triage
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 40178e42737bdfea756db55658aaeb988ad4f19f
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498731"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Prioriter hændelser i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender anvender korrelationsanalyser og aggregerer relaterede beskeder og automatiserede undersøgelser fra forskellige produkter i en hændelse. Microsoft 365 Defender udløser også entydige beskeder om aktiviteter, der kun kan identificeres som skadelig i forhold til den slutpunkt-til-slutpunkt-synlighed, som Microsoft 365 Defender har på tværs af hele produktpakken. Denne visning giver dine sikkerhedsanalytikere den bredere angrebshistorie, som hjælper dem med bedre at forstå og håndtere komplekse trusler på tværs af organisationen.

**Hændelseskøen** viser en samling af hændelser, der er oprettet på tværs af enheder, brugere og postkasser. Det hjælper dig med at sortere efter hændelser for at prioritere og skabe en informeret beslutning om cybersikkerhedsrespons, en proces kaldet hændelses triage.

Du kommer til hændelseskøen **fra Hændelser & hændelser > hændelser** i hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Afsnittet Hændelse, der viser hændelseskøen i Microsoft 365 Defender-portalen." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Afsnittet **Seneste hændelser og beskeder** viser en graf over antallet af modtagne beskeder og hændelser, der er oprettet inden for de seneste 24 timer.

Som standard viser hændelseskøen i Microsoft 365 Defender viser hændelser, der er set inden for de sidste seks måneder. Den seneste hændelse er øverst på listen, så du kan se den først.

Hændelseskøen har brugerdefinerbare kolonner (vælg Vælg **kolonner), der** giver dig overblik over forskellige karakteristika ved hændelsen eller de på påvirkede enheder. På den måde kan du tage en informeret beslutning om prioritering af hændelser til analyse.

For at få et hurtigt overblik over synligheden genererer automatisk navngivning af hændelser hændelsesnavne baseret på beskedattributter som f.eks. antallet af slutpunkter, der er påvirket, brugere, registreringskilder eller kategorier. Dette giver dig mulighed for hurtigt at forstå omfanget af hændelsen.

For eksempel: *Hændelser i flere faser på flere slutpunkter rapporteret af flere kilder.*

> [!NOTE]
> Hændelser, der fandtes før rullen af automatisk navngivning af hændelser, vil ikke få deres navn ændret.

Hændelseskøen indeholder også flere filtreringsindstillinger, som gør det muligt for dig at udføre en bred oprydning af alle eksisterende hændelser i dit miljø eller beslutte at fokusere på et bestemt scenarie eller en bestemt trussel. Anvendelse af filtre på hændelseskøen kan hjælpe med at afgøre, hvilken hændelse der kræver øjeblikkelig handling. 

Listen **Filtre** over listen over hændelser viser de aktuelt anvendte filtre.

## <a name="available-filters"></a>Tilgængelige filtre

Fra standardhændelseskøen kan du vælge **Filtrer** for at få vist en **Filter-rude** , hvorfra du angiver et filtreret sæt hændelser. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Ruden Filtre for hændelseskøen i Microsoft 365 Defender portalen." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Du kan også se ruden **Filter** ved at vælge et af filtrene på **listen** Filtre over listen over hændelser.

Denne tabel viser de filternavne, der er tilgængelige.

| Filternavn | Beskrivelse |
|:-------|:-----|
| Status | Vælg **Ny**, **I gang** eller **Løst**. |
| Alvorsgrad | Alvoren af en hændelse er omfanget af den indvirkning, det kan have på dine aktiver. Jo højere alvorsgrad, desto større virkning og kræver typisk den mest øjeblikkelige opmærksomhed. Vælg **Høj**, **Mellem**, **Lav** eller **Informations.** |
| Hændelsestildeling | Vælg den eller de tildelte brugere. |
| Flere tjenestekilder  | Angiv, om filteret er for mere end én tjenestekilde. |
| Tjenestekilder  | Angiv hændelser, der indeholder beskeder fra: Styring af apps, Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps. |
| Mærker | Markér et eller flere kodenavne på listen. |
| Flere kategorier  | Angiv, om filteret er til mere end én kategori. |
| Kategorier | Vælg kategorier for at fokusere på bestemte taktikker, teknikker eller angrebskomponenter, der kan ses. |
| Enheder | Angiv navnet på et aktiv, f.eks. en bruger, enhed, postkasse eller et programnavn. |
| Datafølsomhed | Nogle angreb fokuserer på målretning for at eksfiltrere følsomme eller værdifulde data. Ved at anvende et filter til bestemte følsomhedsmærkater kan du hurtigt afgøre, om følsomme oplysninger potentielt er blevet kompromitteret og prioritere adressering af disse hændelser. <br><br> Dette filter er kun tilgængeligt, Microsoft Information Protection er slået til. |
| Enhedsgrupper | Angiv navnet [på en enhedsgruppe](/windows/security/threat-protection/microsoft-defender-atp/machine-groups) . |
| STYRESYSTEM-platform | Angiv operativsystemer til enheder. |
| Klassificering | Angiv klassificeringssættet for de relaterede beskeder. |
| Automatiseret undersøgelsestilstand | Angiv status for automatisk undersøgelse.  |
| Tilknyttet trussel | Angiv en navngivet trussel.  |
| Aktører | Angiv en navngiven trussels agent.  |
|||

Standardfilteret er at vise alle beskeder og hændelser med statussen Ny og  I gang  og med en alvorlighed af **Lav****, Mellem** eller **Høj**.

Du kan hurtigt fjerne et filter ved at vælge **X** i navnet på et filter på **listen** Filtre. 

## <a name="save-custom-filters-as-urls"></a>Gemme brugerdefinerede filtre som URL-adresser

Når du har konfigureret et nyttigt filter i køen til hændelser, kan du oprette et bogmærke til webadressen for browserfanen eller på anden måde gemme den som et link på en webside, et Word-dokument eller et sted efter eget valg. Dette giver dig adgang med et enkelt klik til vigtige visninger af hændelseskøen, f.eks.:

- Nye hændelser
- Hændelser med høj alvorsgrad
- Ikke-tildelte hændelser
- Hændelser med høj alvorlighed og ikke-tildelte hændelser
- Hændelser, der er tildelt mig
- Hændelser, der er tildelt mig og for Microsoft Defender for Endpoint
- Hændelser med et bestemt mærke eller mærker
- Hændelser med en bestemt trusselskategori
- Hændelser med en bestemt relateret trussel
- Hændelser med en bestemt agent

Når du har samlet og gemt din liste over nyttige filtervisninger som URL-adresser, kan du bruge den til hurtigt at behandle og prioritere hændelserne i din kø og administrere dem [](manage-incidents.md) til efterfølgende tildeling og analyse.

## <a name="search-for-incidents"></a>Søg efter hændelser

I feltet **Søg efter navn eller id** over listen over hændelser kan du skrive hændelses-id'et eller navnet på hændelsen. Når du vælger en hændelse på listen over søgeresultater, åbner Microsoft 365 Defender-portalen en ny fane med egenskaberne for hændelsen, hvorfra du kan starte [din undersøgelse](investigate-incidents.md).

## <a name="search-for-impacted-assets"></a>Søge efter påvirkningte aktiver

Du kan navngive et aktiv&mdash; som f.eks. en bruger, enhed, postkasse eller programmets navnog&mdash; finde alle de relaterede hændelser. 

## <a name="specify-a-time-range"></a>Angive et tidsinterval

Standardlisten over hændelser er for dem, der er opstået inden for de sidste seks måneder. Du kan angive et nyt tidsinterval fra rullelisten ud for kalenderikonet ved at vælge:

 - 1 dag
 - 3 dage
 - 1 uge
 - 30 dage
 - 30 dage
 - 6 måneder
 - Et brugerdefineret område, hvor du kan angive både datoer og klokkeslæt

## <a name="next-steps"></a>Næste trin

Når du har besluttet, hvilken hændelse der kræver højeste prioritet, skal du markere den og:

- [Administrer](manage-incidents.md) egenskaberne for hændelsen for mærker, tildeling, øjeblikkelig løsning for falske positive hændelser og kommentarer.
- Start [dine undersøgelser](investigate-incidents.md).

## <a name="see-also"></a>Se også
- [Oversigt over hændelser](incidents-overview.md)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)
