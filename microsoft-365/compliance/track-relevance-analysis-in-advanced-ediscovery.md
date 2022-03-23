---
title: Spor relevansanalyse i Advanced eDiscovery
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
ms.assetid: 3ab1e2c3-28cf-4bf5-b0a8-c0222f32bdf5
ROBOTS: NOINDEX, NOFOLLOW
description: Få mere at vide om, hvordan du får vist og fortolker relevanstræningsstatus og resultater for sagsproblemer Advanced eDiscovery.
ms.openlocfilehash: 7a2786a727fd233b6617779bae95a26c1b62644e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589535"
---
# <a name="track-relevance-analysis-in-advanced-ediscovery"></a>Spor relevansanalyse i Advanced eDiscovery
  
I Advanced eDiscovery viser fanen Relevansspor den beregnede gyldighed af de relevanskurser, der udføres under fanen Mærker, og angiver det næste trin, du skal tage i den iterative kursusproces i Relevans. 
  
## <a name="tracking-relevance-training-status"></a>Kursusstatus for sporing af relevans

1. Få vist følgende oplysninger i Relevansspor for de forskellige sagsproblemer som vist i følgende eksempel på dialogboksen **Problemnavn** nedenfor.

   - **Vurdering**: Denne statusindikator viser, i hvilken grad relevanstræningen har nået vurderingsmålet med hensyn til fejlmargen. De mange resultater af relevanskurser vises også.

   - **Kursus**: Denne farvekodede statusindikator og værktøjstip angiver stabiliteten af træningsresultatet for relevans og en numerisk skala, der viser antallet af relevanstræningseksempler, der er mærket for hvert problem. Eksperten overvåger status for kursusprocessen for iterativ relevans. 
  
   - **Batchberegning**: Denne statusindikator indeholder oplysninger om fuldførelsen af batchberegningen.
  
   - **Næste trin**: Viser en anbefaling for det næste trin, der skal udføres. 
  
    I eksemplet vises en korrekt fuldført vurdering af et problem, angivet med den fuldførte farve statusindikator og afkrydsningsfeltet. Mærkning er i gang, men sagen betragtes stadig som ustabil (stabilitetsstatus vises også i et værktøjstip). Det næste trin er "Kursus". 
  
    ![Kurser i relevanssporet trin 1.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    Den udvidede visning viser yderligere oplysninger og indstillinger. Den viste aktuelle fejlmargen er fejlmargenen for tilbagekaldelsen i den aktuelle vurderingstilstand i betragtning af de eksisterende (allerede mærkede) bedømmelsesfiler.
  
    > [!NOTE]
    >  Fasen Bedømmelse kan tilsidesættes ved at fjerne markeringen **i** afkrydsningsfeltet Vurdering pr. problem og derefter for "alle problemer". Der vil dog som resultat være nogen statistik for dette problem. > markeringen i **afkrydsningsfeltet** Vurdering kan kun udføres, før der foretages en vurdering. Hvis der findes flere problemer i en sag, tilsidesættes vurderingen kun, hvis afkrydsningsfeltet ikke er markeret for hvert problem 
  
    Når vurderingen ikke er fuldført med det første eksempelsæt af filer, kan vurdering være det næste trin til mærkning af flere filer.
  
    I **Relevansspor** \> **angiver** indikatoren for oplæringsforløb og værktøjstip det anslåede antal yderligere stikprøver, der skal bruges for at opnå stabilitet. Dette skøn giver en retningslinje for den yderligere nødvendige uddannelse.
  
    ![Kurser i sporing af relevans.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Når du er færdig med mærkning, og hvis du har brug for at fortsætte kurser, skal du klikke på **Kursus**. Der genereres et andet eksempelsæt af filer fra det indlæste filsæt for at få yderligere kurser. Du kommer derefter tilbage til fanen Mærke for at mærke og træne flere filer.

### <a name="reaching-stable-training-levels"></a>Nå et stabilt kursusniveau

Når bedømmelsesfilerne har fået et stabilt uddannelsesniveau, er Advanced eDiscovery klar til beregning i batchen.
  
> [!NOTE]
> Efter tre stabile træningseksempler er næste trin normalt "Batchberegning". Der kan være undtagelser, f.eks. når der er blevet foretaget ændringer til mærkningen af filer fra tidligere eksempler, eller når basisfiler blev tilføjet. 
  
### <a name="performing-batch-calculation"></a>Udføre batchberegning

Batchberegningen udføres som det næste trin, når træningen er gennemført (når en stabil kursusstatus vises på statuslinjen, en markering og en stabil status i værktøjstip. Batchberegning anvender den viden, der er erhvervet under relevans-kurset på hele filens population, for at vurdere filernes relevans og for at tildele relevansresultater.
  
Når der er mere end ét problem, udføres batchberegning pr. problem. Under batchberegning overvåges fremdrift under behandlingen af alle filerne. 
  
Her er det anbefalede næste trin "Ingen", hvilket angiver, at der ikke kræves yderligere kursus om iterativ relevans på nuværende tidspunkt. Den næste fase er fanen **Relevans\>.** 
  
Hvis du vil importere nye filer efter batchberegningen, kan administratoren føje de importerede filer til en ny indlæsning.
  
> [!NOTE]
> Hvis du klikker på **Annuller** under batchberegning, gemmer processen det, der allerede er udført. Hvis du kører Batchberegning igen, fortsætter processen fra det sidste eksekverede punkt. 
  
### <a name="assessing-tagging-consistency"></a>Vurdering af mærkning af konsistens

Hvis der er uoverensstemmelser i filmærkning, kan det påvirke analysen. Den Advanced eDiscovery proces til mærkning af ensartethed kan bruges, når resultaterne ikke er optimale, eller der er tvivl om ensartetheden. Der returneres en liste over mulige uoverensstemmende kodede filer, og de kan gennemses og ommærkes efter behov.
  
> [!NOTE]
> Efter syv eller flere uddannelsesrunder efter vurdering kan mærkning  \>  \>  \> af konsistens vises i Detaljerede resultater af problem med relevansspor **Kursusforløb**\>. Denne gennemgang er udført for ét problem ad gangen.
  
1. **Udvid \> et** problems række i Relevansspor.
  
2. Klik på Rediger **til højre for** Næste **trin**.
  
3. Vælg **Markér uoverensstemmelser som indstillingen Næste** trin **efter syv** undervisningseksempler, og klik på **OK**.
  
4. Vælg **Uoverensstemmelser i mærker**. Fanen **Mærke** åbnes og viser en liste over de uoverensstemmelser, der skal vises for at ommærke efter behov.
  
5. Klik **på Beregn** for at indsende ændringerne. Det næste trin efter mærkning af uoverensstemmelser er "Kursus". 
  
## <a name="viewing-and-using-relevance-results"></a>Visning og brug af resultater af relevans

Udvid **rækken \> med** et problem under fanen Relevansspor, og klik på Vis ud **for** Detaljerede **resultater**. De detaljerede ruder med resultater vises som vist og beskrevet nedenfor.
  
![Detaljerede resultater fra relevanskurser.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Oversigt over mærkning

 I eksemplet, som er **vist nedenfor,** viser oversigten over mærkning totaler for hver af processerne Bedømmelse, Træning og Catch-up-filmærkning.
  
![Oversigt over mærkning med relevansspor.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Nøgleord

Et nøgleord er en entydig streng, et ord, et udtryk eller en sekvens af ord i en fil, der identificeres af Advanced eDiscovery som en vigtig indikator for, om en fil er relevant. Kolonnerne "Medtag" viser nøgleord og vægt i filer, der er mærket som relevante, og kolonnerne "Udelad" viser nøgleord og vægt i filer, der er mærket Som Ikke relevante.
  
Advanced eDiscovery tildeler negative eller positive værdier for nøgleordstykkelse. Jo højere vægt, desto større sandsynlighed er der for, at en fil, hvor nøgleordet vises, tildeles et højere relevansscore under batchberegningen.
  
Listen Advanced eDiscovery kan bruges til at supplere en liste, der er opbygget af en ekspert eller som en indirekte normalitetskontrol på et hvilket som helst tidspunkt i filgennemsynsprocessen.
  
### <a name="training-progress"></a>Kursusforløb

**Ruden Kursusforløb** indeholder en graf over kursusforløb og visning af kvalitetsindikator, som vist i eksemplet nedenfor.
  
![Status for sporing af kurser om relevans.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Indikator for kursuskvalitet**: Viser klassificeringen af mærkningens ensartethed på følgende måde:
  
- **God**: Filer mærkes konsekvent. (Grønt lys vises)
  
- **Mellem**: Nogle filer kan være kodet inkonsistent. (Gult lys vises)

- **Advarsel**! Mange filer kan være kodet inkonsistent. (Rødt lys vises)

**Graf over kursusforløb**: Viser graden af relevanskursusstabilitet efter mange relevanstræningscyklusser i sammenligning med F-målingsværdien. Efterhånden som vi bevæger os fra venstre mod højre på tværs af grafen, indsnævres tillidsintervallet og bruges sammen med F-målingen af Advanced eDiscovery Relevans til at bestemme stabiliteten, når resultaterne af relevanskurserne optimeres.
  
> [!NOTE]
> Relevans bruger F2, en F-målingsmetrik, hvor Recall får dobbelt så meget vægt som Præcision. I tilfælde med høj richness (over 25 %), bruger Relevans F1 (1:1-forhold). Forholdet mellem F-målingen kan konfigureres i **konfigurationen af Relevans Avancerede** \> **indstillinger**.
  
### <a name="batch-calculation-results"></a>Resultater af batchberegning

**Ruden med beregningsresultater** for batchen indeholder antallet af filer, der blev scoret for relevans, som følger: 
  
- **Succes**
  
- **Tom**: Indeholder ingen tekst, f.eks. kun mellemrum/tabulatorer
  
- **Mislykket**: På grund af unødvendig størrelse eller kan ikke læses
  
- **Ignoreret**: På grund af unødvendig størrelse
  
- **Nebulous**: Indeholder meningsløs tekst eller ingen funktioner, der er relevante for problemet
  
> [!NOTE]
> Empty, Failed, ignored, or Nebulous will receive a Relevance score of -1.
  
### <a name="training-statistics"></a>Uddannelsesstatistik

**Statistikruden Kursus** viser statistik og grafer baseret på resultater fra Advanced eDiscovery relevanskurser. 
  
![Statistik for sporing af relevans.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
Denne visning viser følgende:
  
- **Review-recall-forholdet**: Sammenligning af resultater efter relevansresultater i en manuelt lineær gennemgang. Tilbagekaldelse estimeres med det indstillede størrelsessæt for gennemsyn.
  
- **Parametre**: Kumulativ beregnet statistik, der vedrører gennemsynssættet i forhold til fil populationen for hele sagen.
  
- **Gennemse**: Procentdel af filer, der skal gennemses, baseret på denne skæring.
  
- **Tilbagekaldelse**: Procentdel af relevante filer i korrektursættet. 
  
- **Fordeling efter relevansscore**: Filer i den mørkegrå visning til venstre er under skæringsresultatet. Et værktøjstip viser relevansscoren og den relaterede procentdel af filer i gennemsynsfilen angivet i forhold til de samlede filer.
