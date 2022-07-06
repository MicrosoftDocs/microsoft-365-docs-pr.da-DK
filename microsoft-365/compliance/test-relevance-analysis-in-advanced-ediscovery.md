---
title: Test relevansanalyse i eDiscovery (Premium)
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
ms.assetid: 1b092f7c-ea55-44f5-b419-63f3458fd7e0
ROBOTS: NOINDEX, NOFOLLOW
description: Få mere at vide om, hvordan du bruger fanen Test efter batchberegning i eDiscovery (Premium) til at teste, sammenligne og validere den overordnede kvalitet af behandlingen.
ms.openlocfilehash: 5c1fabf677dd305fb91d77e94af0e18304280d45
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637037"
---
# <a name="test-relevance-analysis-in-ediscovery-premium"></a>Test relevansanalyse i eDiscovery (Premium)
  
Fanen Test i Microsoft Purview eDiscovery (Premium) giver dig mulighed for at teste, sammenligne og validere den overordnede kvalitet af behandlingen. Disse test udføres efter batchberegningen. Ved at tagge filerne i samlingen træffer en ekspert den endelige vurdering af, om hver mærkede fil er relevant for sagen.
  
I scenarier med enkelt- og flere problemer udføres der typisk test pr. problem. Resultaterne kan vises efter hver test, og testresultaterne kan omarbejdes med de angivne eksempeltestfiler.
  
## <a name="testing-the-rest"></a>Test af resten

Test resttesten bruges til at validere beslutninger om aflivning, f.eks. til kun at gennemse filer over en bestemt score for relevansafskæring baseret på de endelige resultater for eDiscovery (Premium). Eksperten gennemgår en stikprøve af filer under en valgt skæringsscore for at evaluere antallet af relevante filer i det pågældende sæt.
  
Denne test indeholder statistikker og en sammenligning mellem reviewsættet og restpopulationen Test. Resultaterne af korrektursættet er dem, der beregnes af Relevans under oplæringen. Resultaterne omfatter beregninger baseret på indstillinger og inputparametre, f.eks.:
  
- Test eksempelstatistik for antallet af filer i et eksempel og identificerede relevante filer.

- Tabelsammenligning af Population-parametrene for reviewsættet og resten, f.eks. antallet af filer, det anslåede antal relevante filer, den anslåede rigdom og den gennemsnitlige omkostning ved at finde en anden relevant fil. Indstillinger for omkostningsparametre kan angives af administratoren.

Sådan kører du testen "Test resten":

1. Åbn fanen **Relevanstest\>**.

2. Klik på **Ny test** under fanen **Test**. Dialogboksen **Opret test** vises som vist i følgende eksempel.

    ![Relevanstest restresultaterne.](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. I **Testnavn** og **Beskrivelse** skal du skrive navnet og beskrivelsen.

4. På listen **Testtype** skal du vælge **Test resten**

5. Vælg problemnavnet på listen **Problem/kategori** .

6. Vælg indlæsningen på listen **Indlæs** . 

7. Acceptér standardværdien i **Læs %**, eller vælg en værdi for skæringsresultatet Relevans. 

8. I **Angiv størrelse**, eller acceptér standardværdien. Gendannelsesikonerne gendanner standardværdierne.

9. Klik på **Start mærkning**. Der genereres et testeksempel.

10. Gennemse og mærk hver af filerne under fanen **Relevansmærke\>**, og klik på **Beregn**, når du er færdig.

11. Under fanen Test kan du klikke på **Vis resultater** for at se testresultaterne. Der vises et eksempel på følgende skærmbillede.

    ![Test resten af resultaterne.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
På det forrige skærmbillede indeholder afsnittet **Eksempelparametre** i tabellen oplysninger om antallet af filer i eksemplet, der er mærket af eksperten, og antallet af relevante filer, der blev fundet i eksemplet.
  
Delen af **Population-parametrene** i tabellen indeholder testresultaterne, herunder populationen af filer med et gennemsynssæt med en score under den valgte skæringsfunktion og "Resten"-populationen af filer med en score over den valgte skæring. For hver population vises følgende resultater:
  
- Medtager filer med læse -% - Angivet skæring

- Det samlede antal filer

- Det anslåede antal relevante filer

- Den anslåede rigdom

- Den gennemsnitlige omkostninger ved at finde en anden relevant fil

## <a name="testing-the-slice"></a>Test af udsnittet

Testen "Test udsnittet" udfører test, der svarer til "Test resten"-testen, men til et segment af filen, der er angivet af Relevanslæsning %.

Sådan kører du testen "Test udsnittet":
  
1. Åbn fanen **Relevanstest\>**.

2. Klik på **Ny test** under fanen **Test**. Dialogboksen **Opret test** vises.

3. Skriv oplysningerne i **Testnavn** og **Beskrivelse**.

4. Vælg **Test udsnittet på** listen **Testtype**.

5. Vælg problemnavnet på listen **Problem** .

6. Vælg indlæsningen på listen **Indlæs** .

7. I **Læs % mellem** skal du acceptere standardværdierne for lavt og højt interval eller vælge værdier for skæringsresultatet Relevans.

8. I **Angiv størrelse** skal du vælge en værdi eller acceptere standardværdien.

    Gendannelsesikonerne gendanner standardværdien.

9. Klik på **Start mærkning**. Der genereres et testeksempel.

10. Gennemse og mærk hver af filerne under fanen **Relevansmærke\>**, og klik på **Beregn**, når du er færdig.

11. Under fanen Test kan du klikke på **Vis resultater** for at se testresultaterne.
