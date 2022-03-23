---
title: Test af relevansanalyse i Advanced eDiscovery
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
ms.assetid: 1b092f7c-ea55-44f5-b419-63f3458fd7e0
ROBOTS: NOINDEX, NOFOLLOW
description: Lær at bruge fanen Test efter batchberegning i Advanced eDiscovery til at teste, sammenligne og validere den overordnede kvalitet af behandlingen.
ms.openlocfilehash: 0ea34ce101f6891670a0b646380c965a4391ea32
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589536"
---
# <a name="test-relevance-analysis-in-advanced-ediscovery"></a>Test af relevansanalyse i Advanced eDiscovery
  
Fanen Test i Advanced eDiscovery gør det muligt at teste, sammenligne og validere den overordnede kvalitet af behandlingen. Disse test udføres efter batchberegningen. Ved at tagge filerne i samlingen foretager en ekspert den endelige vurdering af, om hver taggede fil er relevant for sagen.
  
I enkeltstående scenarier og scenarier med flere problemer udføres der typisk test pr. problem. Resultaterne kan vises efter hver test, og testresultater kan omarbejdes med angivne prøvetestfiler.
  
## <a name="testing-the-rest"></a>Tester resten

Testen "Test resten" bruges til at validere nedslagte beslutninger, f.eks. til kun at gennemgå filer, der er over et bestemt skæringsresultat for relevans, baseret på de endelige Advanced eDiscovery resultater. Eksperten gennemser et udsnit af filer under et valgt skæringsresultat for at evaluere antallet af relevante filer i det pågældende sæt.
  
Denne test indeholder statistik og en sammenligning mellem Gennemse-sættet og Test resten af populationen. Resultaterne af korrektursættet er dem, der er beregnet efter Relevans under kurser. Resultaterne omfatter beregninger baseret på indstillinger og inputparametre, f.eks.:
  
- Test stikprøvestatistik over antallet af filer i en stikprøve og identificerede relevante filer.

- Tabelsammenligning af parametrene populationer for Review-sættet og Resten, f.eks. antallet af filer, anslået antal relevante filer, anslået indhold og de gennemsnitlige omkostninger til at finde en anden relevant fil. Indstillinger for omkostningsparametre kan angives af administratoren.

Sådan køres testen "Test resten":

1. Åbne fanen **Relevanstest\>**.

2. Klik på **Ny** test under **fanen Test**. Dialogboksen **Opret test** vises som vist i følgende eksempel.

    ![Relevanstest restresultaterne.](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. Skriv **navn** og **beskrivelse i** Testnavn og Beskrivelse.

4. På listen **Testtype** skal du vælge **Test resten**

5. Vælg **navnet på problemet** på listen Problem/kategori.

6. Vælg **indlæsningen** på listen Indlæs. 

7. I **Læs % skal** du acceptere standardværdien eller vælge en værdi for skæringslevansscoreen. 

8. I **Angiv størrelse**, eller acceptér standardværdien. Gendannelsesikonerne gendanner standardværdierne.

9. Klik **på Start mærkning**. Der genereres en testeksempel.

10. Gennemse og mærk hver enkelt af filerne under fanen **Relevansmærke, \> og** klik på Beregn, når du **er færdig**.

11. På fanen Test kan du klikke på Vis **resultater for** at få vist testresultaterne. Der vises et eksempel på følgende skærmbillede.

    ![Test resten af resultaterne.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
I det forrige skærmbillede indeholder  sektionen Eksempelparametre i tabellen oplysninger om antallet af filer i det eksempel, der er tagget af eksperten, og antallet af relevante filer, der findes i det pågældende eksempel.
  
Sektionen **med populationsparametre** i tabellen indeholder testresultaterne, herunder populationen af filer med et resultat under den valgte skæring og "Resten"-populationen af filer med et resultat over den valgte skæring. For hver population vises følgende resultater:
  
- Omfatter filer med læst % – angivet skæring

- Det samlede antal filer

- Det anslåede antal relevante filer

- Den anslåede værdi

- De gennemsnitlige omkostninger til gennemsyn for at finde en anden relevant fil

## <a name="testing-the-slice"></a>Test af udsnittet

Testen "Test udsnittet" udfører en test, der svarer til "Test resten"-testen, men med et segment af filen, der er angivet af Relevans læs %.

Sådan køres testen "Test udsnittet":
  
1. Åbne fanen **Relevanstest\>**.

2. Klik på **Ny** test under **fanen Test**. Dialogboksen **Opret** test vises.

3. Skriv **oplysningerne i** **Testnavn** og Beskrivelse.

4. Vælg **Test udsnittet** på **listen Testtype**.

5. Vælg **navnet på** problemet på listen Problem.

6. Vælg **indlæsningen** på listen Indlæs.

7. I **Læs % mellem skal** du acceptere standardværdierne for lave og høje områder eller vælge værdier til skæringsrelevansresultater.

8. Vælg **en værdi** i Angiv størrelse, eller acceptér standardværdien.

    Gendannelsesikonerne gendanner standardværdien.

9. Klik **på Start mærkning**. Der genereres en testeksempel.

10. Gennemse og mærk hver enkelt af filerne under fanen **Relevansmærke, \> og** klik på Beregn, når du **er færdig**.

11. På fanen Test kan du klikke på Vis **resultater for** at få vist testresultaterne.
