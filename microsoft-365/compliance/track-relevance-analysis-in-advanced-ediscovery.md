---
title: Spor relevansanalyse i eDiscovery (Premium)
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
ms.assetid: 3ab1e2c3-28cf-4bf5-b0a8-c0222f32bdf5
ROBOTS: NOINDEX, NOFOLLOW
description: Få mere at vide om, hvordan du får vist og fortolker status for relevanstræning og resultater for sagsproblemer i eDiscovery (Premium).
ms.openlocfilehash: dd2eecbcd347125b1728851d873068b37f82aced
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093981"
---
# <a name="track-relevance-analysis-in-ediscovery-premium"></a>Spor relevansanalyse i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
I Microsoft Purview eDiscovery (Premium) viser fanen Relevanssporing den beregnede gyldighed af den relevanstræning, der udføres under fanen Mærke, og angiver det næste trin, der skal udføres i den iterative oplæringsproces i Relevans. 
  
## <a name="tracking-relevance-training-status"></a>Sporer status for relevanstræning

1. Få vist følgende oplysninger i Relevanssporing for sagsproblemer, som vist i følgende eksempel på dialogboksen **Problemnavn** nedenfor.

   - **Vurdering**: Denne statusindikator viser, i hvilken grad den relevanstræning, der er udført til dette punkt, har nået vurderingsmålet med hensyn til fejlmargen. Rigdommen i resultaterne af relevanstræning vises også.

   - **Oplæring**: Denne farvekodede statusindikator og værktøjstip angiver stabiliteten af relevanstræningsresultater og en numerisk skala, der viser antallet af relevanstræningseksempler, der er mærket for hvert problem. Eksperten overvåger status for den iterative relevanstræningsproces. 
  
   - **Batchberegning**: Denne statusindikator indeholder oplysninger om fuldførelsen af batchberegningen.
  
   - **Næste trin**: Viser anbefalingen for det næste trin, der skal udføres. 
  
    I eksemplet vises en vellykket gennemført vurdering af et problem, der er angivet med indikatoren for fuldført farvestatus og fluebenet. Mærkning er i gang, men sagen betragtes stadig som ustabil (stabilitetsstatus vises også i et værktøjstip). Anbefalingen for næste trin er "Træning". 
  
    ![Relevanssporingstræning trin 1.](../media/a00fe607-680a-48eb-9d61-4565319f7ab6.png)
  
    Den udvidede visning viser yderligere oplysninger og indstillinger. Den viste aktuelle fejlmargen er fejlmargenen for tilbagekaldelsen i den aktuelle vurderingstilstand på grund af de eksisterende (allerede mærkede) vurderingsfiler.
  
    > [!NOTE]
    >  Vurderingsfasen kan tilsidesættes ved at fjerne markeringen i afkrydsningsfeltet **Vurdering** for hvert problem og derefter for "alle problemer". Som et resultat heraf vil der dog ikke være nogen statistikker for dette problem. > markeringen i afkrydsningsfeltet **Vurdering** kan kun udføres, før vurderingen udføres. Hvis der er flere problemer i en sag, tilsidesættes vurderingen kun, hvis afkrydsningsfeltet er fjernet for hvert problem 
  
    Når vurderingen ikke er fuldført med det første eksempelsæt af filer, kan vurdering være det næste trin til mærkning af flere filer.
  
    I **Relevanssporing** \> angiver statusindikatoren for oplæringen og værktøjstippet det anslåede antal yderligere eksempler, der er nødvendige for at opnå stabilitet. Dette estimat indeholder en retningslinje for den yderligere træning, der er nødvendig.
  
    ![Træning af relevanssporing.](../media/98dbc3f5-5238-4d73-9f88-1aa4d77ea729.png)
  
2. Når du er færdig med at tagge, og hvis du har brug for at fortsætte oplæringen, skal du klikke på **Oplæring**. Der genereres et andet eksempelsæt af filer ud fra det indlæste filsæt til yderligere oplæring. Du vender derefter tilbage til fanen Mærkat for at mærke og oplære flere filer.

### <a name="reaching-stable-training-levels"></a>At nå stabile træningsniveauer

Når vurderingsfilerne har opnået et stabilt oplæringsniveau, er eDiscovery (Premium) klar til batchberegning.
  
> [!NOTE]
> Efter tre stabile træningseksempler er det næste trin normalt "Batchberegning". Der kan f.eks. være undtagelser, når der var ændringer i mærkningen af filer fra tidligere eksempler, eller når der blev tilføjet seed-filer. 
  
### <a name="performing-batch-calculation"></a>Udfører batchberegning

Batchberegning udføres som næste trin, når oplæringen er fuldført (når status for oplæringen vises i statuslinjen, en markering og stabil status i værktøjstip. Batchberegning anvender den viden, der er erhvervet under relevanstræningen, på hele filpopulationen for at vurdere filernes relevans og for at tildele relevansscores.
  
Når der er mere end ét problem, udføres batchberegningen pr. problem. Under batchberegningen overvåges status under behandling af alle filerne. 
  
Her anbefales det næste trin "Ingen", hvilket angiver, at der ikke kræves yderligere iterativ relevanstræning på nuværende tidspunkt. Den næste fase er fanen **Relevans decider\>**. 
  
Hvis du vil importere nye filer efter batchberegningen, kan administratoren føje de importerede filer til en ny indlæsning.
  
> [!NOTE]
> Hvis du klikker på **Annuller** under batchberegningen, gemmes det, der allerede er udført. Hvis du kører Batchberegning igen, fortsætter processen fra det sidst udførte punkt. 
  
### <a name="assessing-tagging-consistency"></a>Vurdering af konsistens ved mærkning

Hvis der er uoverensstemmelser i filmarkering, kan det påvirke analysen. Processen med eDiscovery-mærkning (Premium) kan bruges, når resultaterne ikke er optimale, eller der er tvivl om konsistensen. Der returneres en liste over mulige uoverensstemmende kodede filer, og de kan gennemses og mærkes igen efter behov.
  
> [!NOTE]
> Efter syv eller flere træningsrunder efter vurdering kan konsistensen ved mærkning ses i **Relevansspor** \>  \> **Problem** \> **Detaljerede resultater** \> **Oplæringsstatus**. Denne anmeldelse udføres for ét problem ad gangen.
  
1. Udvid rækken for et problem i **Relevanssporing\>**.
  
2. Klik på **Rediger** til højre for **Næste trin**.
  
3. Vælg **Markér uoverensstemmelser** som indstillingen **Næste trin** efter syv oplæringseksempler, og klik på **OK**.
  
4. Vælg **Mærk uoverensstemmelser**. Fanen **Mærkat** åbnes og viser en liste over de uoverensstemmelser, der skal genmærkes efter behov.
  
5. Klik på **Beregn** for at sende ændringerne. Det næste trin efter mærkning af uoverensstemmelser er "Oplæring". 
  
## <a name="viewing-and-using-relevance-results"></a>Visning og brug af relevansresultater

Udvid rækken for et problem under fanen **Relevanssporing\>**, og klik på **Vis** ud for **Detaljerede resultater**. De detaljerede resultatruder vises, som vist og beskrevet nedenfor.
  
![Detaljerede resultater af relevanstræning.](../media/495c04a9-ed1e-4355-8cab-c14270ca2bbb.png)
  
### <a name="tagging-summary"></a>Oversigt over mærkning

 I eksemplet nedenfor viser **oversigt over mærkning** totaler for hver vurderings-, oplærings- og opfangningsproces.
  
![Oversigt over markering af relevanssporing.](../media/0ec906fc-bc84-4245-a964-fb3ca37891db.png)
  
### <a name="keywords"></a>Søgeord

Et nøgleord er en entydig streng, et ord, et udtryk eller en sekvens af ord i en fil, der er identificeret af eDiscovery (Premium) som en vigtig indikator for, om en fil er relevant. Nøgleord og vægtninger for "Medtag" kolonner vises i filer, der er mærket som relevante, og kolonnerne "Udelad" viser nøgleord og vægtninger i filer, der er mærket som Ikke relevante.
  
eDiscovery (Premium) tildeler negative eller positive nøgleordsvægtværdier. Jo højere vægt, jo højere er sandsynligheden for, at en fil, hvor nøgleordet vises, tildeles en højere relevansscore under batchberegningen.
  
EDiscovery-listen (Premium) med nøgleord kan bruges til at supplere en liste, der er oprettet af en ekspert, eller som en indirekte tilregnelighedskontrol på et hvilket som helst tidspunkt i filgennemsynsprocessen.
  
### <a name="training-progress"></a>Status for oplæring

Ruden **Oplæringsstatus** indeholder en visning af statusgrafen for oplæring og en kvalitetsindikator som vist i eksemplet nedenfor.
  
![Relevanssporing af status for oplæring.](../media/8a5089f5-a162-4246-ae09-bc1921859860.png)
  
**Indikator for oplæringskvalitet**: Viser bedømmelsen af konsistensen af mærkningen på følgende måde:
  
- **Godt**: Filer mærkes konsekvent. (Grønt lys vises)
  
- **Medium**: Nogle filer kan være mærket uoverensstemmende. (Gult lys vises)

- **Advarsel**! Mange filer kan blive mærket uoverensstemmende. (Rødt lys vises)

**Graf over oplæringsstatus**: Viser graden af stabilitet af relevanstræning efter mange cyklusser for relevanstræning sammenlignet med F-målingsværdien. Når vi flytter fra venstre mod højre på tværs af grafen, indsnævres konfidensintervallet, og det bruges sammen med F-målingen af eDiscovery (Premium) Relevans til at bestemme stabiliteten, når resultaterne af relevanstræningen optimeres.
  
> [!NOTE]
> Relevans bruger F2, som er en metrikværdi for F-måling, hvor Recall modtager dobbelt så meget vægt som Præcision. I tilfælde med høj rigdom (over 25 %), relevansen bruger F1 (1:1-forhold). F-målingsforholdet kan konfigureres i **Relevanskonfiguration** \> **Avancerede indstillinger**.
  
### <a name="batch-calculation-results"></a>Batchberegningsresultater

Ruden **Batchberegningsresultater** indeholder antallet af filer, der blev scoret for relevans på følgende måde: 
  
- **Succes**
  
- **Tom**: Indeholder ingen tekst, f.eks. kun mellemrum/tabulatorer
  
- **Mislykket**: På grund af for stor størrelse eller kunne ikke læses
  
- **Ignoreret**: På grund af for stor størrelse
  
- **Tåget**: Indeholder meningsløs tekst eller ingen funktioner, der er relevante for problemet
  
> [!NOTE]
> Tom, Mislykket, Ignoreret eller Tåget modtager en relevansscore på -1.
  
### <a name="training-statistics"></a>Træningsstatistik

Ruden **Oplæringsstatistik** viser statistikker og grafer baseret på resultater fra eDiscovery (Premium) Relevanstræning. 
  
![Relevanssporingsstatistik for oplæring.](../media/9a07740e-20d3-49fb-b9b9-84265e0a1836.png)
  
I denne visning vises følgende:
  
- **Forhold mellem anmeldelse og genkaldelse**: Sammenligning af resultater i henhold til relevansscores i en hypotetisk lineær gennemgang. Tilbagekaldelse anslås på grund af den angivne størrelse for gennemgangen.
  
- **Parametre**: Akkumulerede beregnede statistikker vedrørende gennemsynssættet i forhold til filpopulationen for hele sagen.
  
- **Anmeldelse**: Procentdel af filer, der skal gennemses baseret på denne skæring.
  
- **Husk**: Procentdel af relevante filer i korrektursættet. 
  
- **Distribution efter relevansscore**: Filer i den mørke grå skærm til venstre er under skæringsscoren. Et værktøjstip viser relevansscoren og den relaterede procentdel af filer i korrekturfilen, der er angivet i forhold til det samlede antal filer.
