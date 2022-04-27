---
title: Mærknings- og relevanstræning i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 8576cc86-d51b-4285-b54b-67184714cc62
ROBOTS: NOINDEX, NOFOLLOW
description: Få mere at vide om, hvordan du tagger og derefter arbejder med et træningseksempel på 40 filer i fasen Relevanstræning i eDiscovery (Premium).
ms.openlocfilehash: 3e2deb66658aacc8fdd50f2dea5ba082afb8a5e6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090379"
---
# <a name="tagging-and-relevance-training-in-ediscovery-premium"></a>Mærknings- og relevanstræning i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
I denne artikel beskrives proceduren for at arbejde med modulet Relevanstræning i Microsoft Purview eDiscovery (Premium).
  
Når vurderingen er fuldført i eDiscovery (Premium), og du går ind i fasen Relevanstræning, føres der et træningseksempel på 40 filer ind under fanen Mærkat til mærkning.
  
## <a name="performing-relevance-training"></a>Udfører relevanstræning

1. Under fanen **Relevansmærke \>** vises ruden Mærkning som standard i venstre rude, og eksempelfilerne vises én ad gangen til mærkning.

    ![Panelet Relevansmærke.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    Under fanen **Mærke** vises filens viste navn. Det kan være stien, mailemnet, titlen eller det brugerdefinerede navn. Id'et, filstien eller tekststien kan kopieres ved at højreklikke på filens sti.

    Statistik for tagging under fanen **Mærkat** viser fileksemplets nummer (øverst i venstre rude), antallet af aktuelt viste filer ud af det samlede antal filer i eksemplet (nederst til højre) og det aktuelle samlede antal mærkede filer i eksemplet (nederst i venstre rude), som ændres, efterhånden som du mærker filer. Dette gælder for eventuel udført relevansmarkering, uanset om det er i vurdering, træning, opfangning eller test.

    Ikoner, der angiver, at der findes kommentarer, mærker og familiefiler, vises i filvisningen på en linje over filen.

2. Bestem filens relevans for sagsproblemet, og tagge filen ved hjælp af enten knapperne for markeringsindstillingerne eller tastaturgenveje som vist i følgende tabel:

   |**Indstilling for mærkning**|**Beskrivelse**|**Tastaturgenvej**|**Massemarkering af tastaturgenvej (for flere problemer)**|
   |-----|-----|-----|-----|
   |R  <br/> |Relevante  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |Ikke relevant  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Springe  <br/> |Springe  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Når der er flere problemer med en fil, efter at du har mærket et problem, flyttes markeringen til det næste problem (hvis der er nogen).  

   - Nøgleord, der blev defineret af administratoren eller sagsstyringen ved fremhævning af nøgleord (nøgleord for relevansopsætning \> fremhævede nøgleord), vises (i angivne farver) for at hjælpe med at identificere relevante filer under mærkning. Hvis et nøgleord har en dobbelt understregning, kan du klikke på det for at få vist et værktøjstip med beskrivelsen af nøgleordet.

     Du kan også vælge at klikke på **Mærkatindstillinger** under fanen **Mærkat** for at angive følgende indstillinger:

      ![Indstillinger for relevansmærke.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Massekode**: Brug denne indstilling til at tildele flere problemer til en fil ved at vælge **Alle** for at angive koden for den valgte fil for alle problemer (tilsidesætter allerede mærkede problemer) eller ved at vælge **Resten** for at anvende koden på de resterende umarkerede problemer. Den valgte indstilling forbliver i kraft for alle denne brugers sager, indtil den pågældende bruger har ændret den (indstillingen er pr. bruger for alle brugerens sager).

   - **Automatisk kode**: Markér dette afkrydsningsfelt for at angive andre problemer for en fil som Ikke relevant efter en enkelt relevant mærkning.

   - **Automatisk fremrykning**: Markér dette afkrydsningsfelt for at flytte den viste filmarkering til den næste fil, når du markerer det sidste eller eneste umarkerede problem.

    Filer, der springes over, tages ikke i betragtning i forbindelse med relevanstræning og relevansscore.

3. Fritekstkommentarer, der er knyttet til en fil, kan vises og redigeres via indstillingen **Kommentar** på rullelisten i venstre rude. (valgfrit)

4. Du kan få vist retningslinjer for mærkning ved at vælge indstillingen **Retningslinjer for mærkning** på rullelisten i venstre rude.

5. Når du er færdig med at mærke alle filer på listen og er klar til at beregne resultaterne, skal du klikke på **Beregn**. Fanen **Spor** vises.  

## <a name="working-with-the-sample-files-list"></a>Arbejde med listen over eksempelfiler

Listen med eksempelfiler giver dig mulighed for at få vist en liste over filerne i et oplæringseksempel og udføre forskellige handlinger på en eller flere filer. I ruden **Eksempelfiler** til venstre under fanen **Relevanskode** \> vises der en liste over eksempelfiler til behandling med processer af typen Vurdering, Oplæring, Opfang og Uoverensstemmelser.
  
1. Under fanen **Relevansmærke \>** skal du vælge eksempelfilerne på rullelisten i venstre rude. Eksempelfilerne vises i venstre rude.

    ![Liste over eksempelfiler til relevansmærke.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. Vælg et bestemt eksempel- eller filnummer ved at angive eller vælge dets nummer i felterne **Eksempel** eller **Fil** .

   - Der vises et filsekvensnummer i venstre kolonne på den viste filliste under fanen **Mærke** . Når du klikker på overskriften, vender den oprindelige viste rækkefølge af filerne tilbage til den oprindelige rækkefølge.

   - Når du klikker på en filrække, vises indholdet i højre rude.

   - Naviger mellem filer i det aktuelle eksempel ved hjælp af de nederste menulinjeindstillinger. Desuden er navigationstastaturgenveje tilgængelige:
  
     - Sådan går du til den første fil i eksemplet: `Shift + Ctrl + <`

     - Sådan går du til den forrige fil i eksemplet: `Shift + <`

     - Sådan går du til den næste fil i eksemplet: `Shift + >`

     - Sådan går du til den sidste fil i eksemplet: `Shift + Ctrl + >`
