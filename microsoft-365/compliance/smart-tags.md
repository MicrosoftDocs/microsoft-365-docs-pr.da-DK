---
title: Konfigurer i-mærker i eDiscovery (Premium)
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
description: Med i-mærker kan du anvende funktionerne til maskinel indlæring, når du gennemser indhold i en eDiscovery-sag (Premium). Brug grupper med i-mærker til at få vist resultaterne af modeller til registrering af maskinel indlæring, f.eks. rettighedsmodellen for advokat/klient.
ms.openlocfilehash: 9fd4a53df00bcb096a885ed311e4fb4ed365725e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934615"
---
# <a name="set-up-smart-tags-in-ediscovery-premium"></a>Konfigurer i-mærker i eDiscovery (Premium)

Funktioner til maskinel indlæring i Microsoft Purview eDiscovery (Premium) kan hjælpe dig med at gøre beslutningsprocessen mere effektiv, når du gennemser sagsdokumenter i et korrektursæt. I-mærker er en metode til at overføre ML-funktionerne til de steder, hvor beslutningerne registreres: når du mærker dokumenter under gennemgangen. Når du opretter en gruppe med i-mærker, vises de beslutninger, der er resultatet af den ML-model, du har knyttet til i-mærke-gruppen, på linje med mærkerne i mærkegruppen. Dette hjælper med at se oplysningerne om ML-resultaterne på linje, når du gennemser bestemte dokumenter.

## <a name="how-to-set-up-a-smart-tag-group"></a>Sådan konfigurerer du en gruppe med i-mærker

1. I et korrektursæt skal du klikke på **Administrer korrektursæt** og derefter klikke på **Administrer mærker**.

2. Klik på **Tilføj mærkegruppe** , og vælg derefter **Tilføj i-mærke-gruppe**.

3. Vælg den ML-model, du vil knytte til kodegruppen.
    
   Dette opretter en kodegruppe og *N-underordnede* mærker, hvor *N* er antallet af mulige output fra modellen. [Modellen til registrering af rettigheder for advokatklienter](attorney-privilege-detection.md) har f.eks. to mulige output: 

   - **Positiv** – bruges til at mærke dokumenter, der indeholder privilegeret indhold fra en advokat/klient.
   
   - **Negativ** – bruges til at mærke dokumenter, der ikke indeholder privilegeret indhold fra en advokat/klient.
    
    Hvis du vælger denne model, oprettes der en kodegruppe med to underordnede mærker (én underordnet kode med navnet **Positiv** og den anden med navnet **Negativ**) for korrektursættet. I dette eksempel svarer hvert underordnet mærke til et af de mulige output fra modellen til registrering af rettighedsregistrering for advokat/klient.

4. Du kan også omdøbe kodegruppen og de underordnede mærker. Du kan f.eks. omdøbe koden **Positiv** til **Privilegeret** og **Negativ** til **Ikke privilegeret**.

## <a name="how-to-use-smart-tags"></a>Sådan bruger du i-mærker

Når du gennemser et dokument, vises modellens resultater ud for den relevante underordnede kode. Hvis du f.eks. har en i-mærkegruppe til registrering af rettighedsregistrering for advokater og klienter, og du gennemser et dokument, der muligvis er privilegeret, vises årsagen til denne konklusion ud for det relevante tag. Det er vigtigt at bemærke, at koden ikke anvendes automatisk på dokumentet. Korrekturlæseren træffer beslutning om, hvordan dokumentet skal mærkes.
