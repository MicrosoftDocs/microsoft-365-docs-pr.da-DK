---
title: Konfigurer i-mærker i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ROBOTS: NOINDEX, NOFOLLOW
description: Med i-mærker kan du anvende maskinel indlæringsegenskaber, når du gennemser indhold i Advanced eDiscovery sag. Brug i-mærkegrupper til at vise resultaterne af modeller til registrering af maskinel indlæring, f.eks. attorney-client privilege model.
ms.openlocfilehash: 80c946da943e4880dbd82ea6b34d238b80030b4c
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63588724"
---
# <a name="set-up-smart-tags-in-advanced-ediscovery"></a>Konfigurer i-mærker i Advanced eDiscovery

Ml-funktioner (Machine Learning) i Advanced eDiscovery kan hjælpe dig med at gøre beslutningsprocessen mere effektiv, når du gennemser sagsdokumenter i et gennemsynssæt. I-mærker er en metode til at føre ML-funktionerne til de steder, hvor beslutninger registreres: ved mærkning af dokumenter under gennemsyn. Når du opretter en i-mærkegruppe, vises de beslutninger, der er resultatet af ML-modellen, du har knyttet til i-mærkegruppen, på linje med mærkerne i mærkegruppen. Dette er med til at få vist oplysningerne om ML-resultaterne direkte, når du gennemser bestemte dokumenter.

## <a name="how-to-set-up-a-smart-tag-group"></a>Sådan konfigureres en i-mærkegruppe

1. I et korrektursæt skal du klikke **på Administrer korrektursæt** og derefter klikke **på Administrer mærker**.

2. Klik **på Tilføj mærkegruppe,** og vælg **derefter Tilføj i-mærkegruppe**.

3. Vælg den ML-model, du vil knytte til mærkegruppen.
    
   Dette opretter en mærkegruppe *og underordnede N-mærker* , hvor *N* er antallet af mulige output fra modellen. For example, the [attorney-client privilege detection model](attorney-privilege-detection.md) has two possible outputs: 

   - **Positiv** – Bruges til at mærke dokumenter, der indeholder indhold med klienter med rettigheder.
   
   - **Negativ** – Bruges til at mærke dokumenter, der ikke indeholder indhold med klienter med rettigheder som advokat.
    
    Hvis du vælger denne model, oprettes der en mærkegruppe med to underordnede mærker (et underordnet mærke med navnet **Positiv** og den anden med navnet **Negativ**) for gennemsynssættet. I dette eksempel svarer hvert underordnet mærke til en af de mulige output fra attorney-client privilege detection model.

4. Du kan også omdøbe mærkegruppen og de underordnede mærker. Du kan f.eks. omdøbe mærket **Positiv** til **Privilegeret** og mærket **Negativ** til **Ikke privilegeret**.

## <a name="how-to-use-smart-tags"></a>Sådan bruges i-mærker

Når du gennemser et dokument, vises modellens resultater ud for det relevante underordnede mærke. Hvis du f.eks. har en i-mærkegruppe til registrering af advokat-klient-rettigheder, og du gennemser et dokument, der potentielt er privilegeret, vises årsagen til den pågældende konklusion ud for det relevante mærke. Det er vigtigt at bemærke, at mærket ikke automatisk anvendes på dokumentet. Korrekturlæseren beslutter, hvordan dokumentet skal mærkes.
