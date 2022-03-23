---
title: Kursus om mærkning og relevans i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om, hvordan du mærker og derefter arbejder med et kursuseksempel på 40 filer under kurset Relevanskursus Advanced eDiscovery.
ms.openlocfilehash: c21ec89896dbd67bd348abd317d1389f8e105fda
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587306"
---
# <a name="tagging-and-relevance-training-in-advanced-ediscovery"></a>Kursus om mærkning og relevans i Advanced eDiscovery
  
I denne artikel beskrives fremgangsmåden for at arbejde med uddannelsesmodulet Relevans i Advanced eDiscovery.
  
Når Bedømmelse er fuldført Advanced eDiscovery, og du går ind i uddannelsesfasen Relevans, findes der et træningseksempel på 40 filer på fanen Mærker til mærkning.
  
## <a name="performing-relevance-training"></a>Udføre kurser om relevans

1. På fanen **Relevansmærke \>** vises ruden Mærkning som standard i venstre rude, og eksempelfilerne vises én ad gangen til mærkning.

    ![Panelet For relevansmærke.](../media/0cf19ab4-b427-4a7f-8749-0f4ed9afaf58.png)
  
    Under **fanen** Mærke vises filens viste navn. Dette kan være stien, mailens emne, titel eller brugerdefinerede navn. Id'et, filstien eller tekststien kan kopieres ved at højreklikke på filens sti.

    På fanen **Mærke** vises kodningsstatistikken for eksempelfilen (øverst i venstre rude), nummeret på den aktuelt viste fil ud af det samlede antal filer i eksemplet (nederst i højre rude) og det aktuelle samlede antal mærkede filer i eksemplet (nederst i venstre rude), som ændres, når du mærker filer. Dette gælder for alle relevansmærkninger, der udføres, uanset om det er i Bedømmelse, Kursus, Opfølgning eller Test.

    Ikoner, der angiver eksistensen af kommentarer, mærker og familiefiler, vises i filvisningen i en søjle over filen.

2. Bestem filens relevans for sagsproblemet, og mærk filen enten ved hjælp af alternativknapperne for mærkning eller tastaturgenveje, som vist i følgende tabel:

   |**Indstillingen Mærkning**|**Beskrivelse**|**Tastaturgenvej**|**Massemærkning af tastaturgenvej (ved flere problemer)**|
   |-----|-----|-----|-----|
   |R  <br/> |Relevante  <br/> |Z  <br/> |`Shift + Z`  <br/> |
   |NR  <br/> |Ikke relevant  <br/> |X  <br/> |`Shift + X`  <br/> |
   |Spring over  <br/> |Spring over  <br/> |C  <br/> |`Shift + A`  <br/> |
   |||||

   - Når der findes flere problemer for en fil, flyttes markeringen til det næste problem (hvis der er et) efter mærkning af et problem.  

   - Nøgleord, der blev defineret af administratoren eller Case Manager ved fremhævning af nøgleord ( \> Konfiguration af relevans fremhævede nøgleord), vises (i angivne farver) for at identificere relevante filer under mærkning. Hvis et nøgleord har en dobbelt understregning, kan der klikkes på det for at få vist et værktøjstip med nøgleordets beskrivelse.

     Du kan også klikke på **Mærkeindstillinger** under fanen **Mærker for** at angive følgende indstillinger:

      ![Indstillinger for relevansmærke.](../media/533e89fa-7eb4-409e-ab07-f5aab9296dd8.png)
  
   - **Massemærke**: Brug denne indstilling til at tildele flere problemer for en fil ved at  vælge Alle for at angive koden for den valgte fil for alle problemer (tilsidesætter allerede mærkede problemer) eller ved  at vælge Resten for at anvende mærket på de resterende umærkede problemer. Den valgte indstilling gælder for alle denne brugers sager, indtil den pågældende bruger har ændret sig (indstillingen er pr. bruger for alle brugerens tilfælde).

   - **Auto-mærke**: Markér dette afkrydsningsfelt for at angive andre problemer for en fil som Ikke relevant efter en enkelt relevant mærkning.

   - **Automatisk fornyelse**: Markér dette afkrydsningsfelt for at flytte den viste filmarkering til den næste fil, når du mærker det sidste eller eneste problem, der ikke er markeret.

    Ignorerede filer tages ikke i betragtning med henblik på relevanskurser og relevansscore.

3. Fritekstkommentarer, der er knyttet til en fil, kan ses og redigeres  via indstillingen Kommentar i rullelisten til venstre i ruden. (valgfrit)

4. Retningslinjer for mærkning kan ses ved at vælge **indstillingen Retningslinjer** for mærkning på rullelisten i venstre rude.

5. Når du er færdig med at mærke alle filer på listen og er klar til at beregne resultaterne, skal du klikke på **Beregn**. **Fanen Sporing** vises.  

## <a name="working-with-the-sample-files-list"></a>Arbejde med listen over eksempelfiler

Eksempelfilerne giver dig mulighed for at få vist en liste over filerne i et træningseksempel og udføre forskellige handlinger på en eller flere filer. I fanen **Relevansmærke** \> viser venstre rude  Eksempelfiler en liste over eksempelfiler til behandling med Assessment-, Training-, Catch-up- og Inconsistens-processer.
  
1. På fanen **Relevansmærke \>** skal du vælge rullelisten Eksempelfiler i venstre rude. Eksempelfilerne vises i venstre rude.

    ![Eksempelfiler med relevansmærkeliste.](../media/fd058bdd-645a-4af1-a1eb-bff08581cb18.png)
  
2. Vælg et bestemt eksempel eller filnummer ved at angive eller vælge dets nummer i **felterne Eksempel** **eller** Fil.

   - Der vises et filsekvensnummer i venstre kolonne i den viste filliste under **fanen** Mærke. Ved at klikke på sidehovedet returneres den oprindelige viste rækkefølge af filerne til den oprindelige rækkefølge.

   - Når du klikker på en filrække, vises dens indhold i højre rude.

   - Naviger mellem filer i det aktuelle eksempel ved hjælp af de nederste menulinjeindstillinger. Desuden findes der tastaturgenveje til navigation:
  
     - Sådan går du til den første fil i eksemplet: `Shift + Ctrl + <`

     - Sådan går du til den forrige fil i eksemplet: `Shift + <`

     - Sådan går du til den næste fil i eksemplet: `Shift + >`

     - Sådan går du til den sidste fil i eksemplet: `Shift + Ctrl + >`
