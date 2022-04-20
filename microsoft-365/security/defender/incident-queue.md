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
ms.openlocfilehash: 285da473c8e8035a28ee6e64c4950e2b8fe373f5
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944409"
---
# <a name="prioritize-incidents-in-microsoft-365-defender"></a>Prioriter hændelser i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender anvender korrelationsanalyser og aggregerer relaterede beskeder og automatiserede undersøgelser fra forskellige produkter i en hændelse. Microsoft 365 Defender udløser også entydige beskeder om aktiviteter, der kun kan identificeres som skadelige på grund af synligheden fra ende til anden i Microsoft 365 Defender har på tværs af hele produktpakken. Denne visning giver dine sikkerhedsanalytikere den bredere angrebshistorie, som hjælper dem med bedre at forstå og håndtere komplekse trusler på tværs af din organisation.

**Hændelseskøen** viser en samling af hændelser, der blev oprettet på tværs af enheder, brugere og postkasser. Det hjælper dig med at sortere gennem hændelser for at prioritere og oprette en informeret beslutning om cybersikkerhedsrespons, en proces, der er kendt som hændelsestriage.

Du kommer til hændelseskøen fra **Hændelser & beskeder > Hændelser** på hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Afsnittet Hændelse, der viser hændelseskøen på portalen Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Afsnittet **Seneste hændelser og beskeder** viser en graf over antallet af modtagne beskeder og hændelser, der er oprettet inden for de seneste 24 timer.

Som standard viser hændelseskøen på Microsoft 365 Defender-portalen hændelser, der er set i de sidste seks måneder. Den seneste hændelse er øverst på listen, så du kan se den først.

Hændelseskøen har kolonner, der kan tilpasses (vælg **Vælg kolonner**), som giver dig indblik i forskellige egenskaber for hændelsen eller de påvirkede enheder. Dette hjælper dig med at træffe en informeret beslutning om prioriteringen af hændelser til analyse.

Automatisk navngivning af hændelser genererer hændelsesnavne baseret på beskedattributter, f.eks. antallet af berørte slutpunkter, berørte brugere, registreringskilder eller kategorier, for at opnå yderligere synlighed ved hjælp af automatisk navngivning af hændelser. Dette giver dig mulighed for hurtigt at forstå omfanget af hændelsen.

Eksempel: *Hændelse med flere faser på flere slutpunkter rapporteret af flere kilder.*

> [!NOTE]
> Hændelser, der fandtes før udrulningen af automatisk navngivning af hændelser, får ikke deres navn ændret.

Hændelseskøen indeholder også flere filtreringsindstillinger, der, når de anvendes, giver dig mulighed for at udføre en bred gennemgang af alle eksisterende hændelser i dit miljø eller beslutte at fokusere på et bestemt scenarie eller en bestemt trussel. Anvendelse af filtre på hændelseskøen kan hjælpe med at afgøre, hvilken hændelse der kræver øjeblikkelig opmærksomhed. 

Listen **Filtre** over listen over hændelser viser de aktuelt anvendte filtre.

## <a name="available-filters"></a>Tilgængelige filtre

Fra standardhændelseskøen kan du vælge **Filter** for at få vist ruden **Filter** , hvorfra du angiver et filtreret sæt hændelser. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Ruden Filtre for hændelseskøen på portalen Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Du kan også se ruden **Filter** ved at vælge et af filtrene på listen **Filtre** over listen over hændelser.

I denne tabel vises de filternavne, der er tilgængelige.

| Filternavn | Beskrivelse |
|:-------|:-----|
| Status | Vælg **Ny**, **Igangværende** eller **Løst**. |
| Sværhedsgraden | Alvorsgraden af en hændelse er tegn på den indvirkning, den kan have på dine aktiver. Jo højere alvorsgrad, jo større virkning og kræver typisk den mest øjeblikkelige opmærksomhed. Vælg **Høj**, **Mellem**, **Lav** eller **Oplysende**. |
| Hændelsestildeling | Vælg den eller de tildelte brugere. |
| Flere tjenestekilder  | Angiv, om filteret skal bruges til mere end én tjenestekilde. |
| Tjenestekilder  | Angiv hændelser, der indeholder beskeder fra: Appstyring, Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Cloud Apps. |
| Tags | Vælg et eller flere mærkatnavne på listen. |
| Flere kategorier  | Angiv, om filteret skal indeholde mere end én kategori. |
| Kategorier | Vælg kategorier for at fokusere på specifikke taktikker, teknikker eller angrebskomponenter, der ses. |
| Enheder | Angiv navnet på et aktiv, f.eks. en bruger, en enhed, en postkasse eller et programnavn. |
| Datafølsomhed | Nogle angreb fokuserer på målretning for at exfiltrere følsomme eller værdifulde data. Ved at anvende et filter for bestemte følsomhedsmærkater kan du hurtigt afgøre, om følsomme oplysninger potentielt er blevet kompromitteret, og prioritere håndteringen af disse hændelser. <br><br> Dette filter viser kun oplysninger, når du har anvendt [følsomhedsmærkater fra Microsoft Purview Information Protection](../../compliance/sensitivity-labels.md). |
| Enhedsgrupper | Angiv navnet på en [enhedsgruppe](/windows/security/threat-protection/microsoft-defender-atp/machine-groups) . |
| OS-platform | Angiv enhedsoperativsystemer. |
| Klassificering | Angiv sættet af klassificeringer for de relaterede beskeder. |
| Automatiseret undersøgelsestilstand | Angiv status for automatiseret undersøgelse.  |
| Tilknyttet trussel | Angiv en navngiven trussel.  |
| Aktører | Angiv en navngivet trusselsaktør.  |
|||

Standardfilteret er at vise alle beskeder og hændelser med statussen **Ny** og **I gang** og med alvorsgraden **Lav**, **Mellem** eller **Høj**.

Du kan hurtigt fjerne et filter ved at vælge **X** i navnet på et filter på listen **Filtre** . 

## <a name="save-custom-filters-as-urls"></a>Gem brugerdefinerede filtre som URL-adresser

Når du har konfigureret et nyttigt filter i hændelseskøen, kan du angive et bogmærke for URL-adressen til browserfanen eller på anden måde gemme den som et link på en webside, et Word-dokument eller et sted efter eget valg. Dette giver dig adgang med et enkelt klik til nøglevisninger af hændelseskøen, f.eks.:

- Nye hændelser
- Hændelser med høj alvorsgrad
- Ikke-tildelte hændelser
- Hændelser med høj alvorsgrad, ikke-tildelte hændelser
- Hændelser, der er tildelt mig
- Hændelser, der er tildelt mig og for Microsoft Defender for Endpoint
- Hændelser med et bestemt mærke eller mærker
- Hændelser med en bestemt trusselskategori
- Hændelser med en bestemt tilknyttet trussel
- Hændelser med en bestemt agent

Når du har kompileret og gemt din liste over nyttige filtervisninger som URL-adresser, kan du bruge den til hurtigt at behandle og prioritere hændelserne i din kø og [administrere](manage-incidents.md) dem til efterfølgende tildeling og analyse.

## <a name="search-for-incidents"></a>Søg efter hændelser

I feltet **Søg efter navn eller id** over listen over hændelser kan du skrive hændelses-id'et eller hændelsesnavnet. Når du vælger en hændelse på listen over søgeresultater, åbner Microsoft 365 Defender-portalen en ny fane med egenskaberne for hændelsen, hvorfra du kan starte din [undersøgelse](investigate-incidents.md).

## <a name="search-for-impacted-assets"></a>Søg efter påvirkede aktiver

Du kan navngive et aktiv&mdash;, f.eks. en bruger, en enhed, en postkasse eller et programnavn&mdash;, og finde alle relaterede hændelser. 

## <a name="specify-a-time-range"></a>Angiv et tidsinterval

Standardlisten over hændelser er for dem, der er opstået i de sidste seks måneder. Du kan angive et nyt tidsinterval på rullelisten ud for kalenderikonet ved at vælge:

 - 1 dag
 - 3 dage
 - 1 uge
 - 30 dage
 - 30 dage
 - 6 måneder
 - Et brugerdefineret område, hvor du kan angive både datoer og klokkeslæt

## <a name="next-steps"></a>Næste trin

Når du har bestemt, hvilken hændelse der kræver den højeste prioritet, skal du vælge den og:

- [Administrer](manage-incidents.md) egenskaberne for hændelsen for koder, tildeling, øjeblikkelig løsning for falske positive hændelser og kommentarer.
- Begynd [efterforskningen](investigate-incidents.md).

## <a name="see-also"></a>Se også
- [Oversigt over hændelser](incidents-overview.md)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)
