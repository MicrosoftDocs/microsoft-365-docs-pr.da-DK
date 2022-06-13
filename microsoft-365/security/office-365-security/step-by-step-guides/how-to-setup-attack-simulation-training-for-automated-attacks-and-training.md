---
title: Sådan konfigurerer du automatiserede angreb og træning i angrebssimuleringskurser
description: Trinnene til at automatisere oplæring af angrebssimulering og sende en nyttedata til målbrugere. Ved at følge denne vejledning lærer du at oprette automatiserede angrebsflow med specifikke teknikker og nyttedata.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: ccf4222878777789fb7f89b6382c858eaad9f0c2
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042139"
---
# <a name="how-to-setup-automated-attacks-and-training-within-attack-simulation-training"></a>Sådan konfigurerer du automatiserede angreb og træning i angrebssimuleringskurser

Oplæring af angrebssimulering giver dig mulighed for at køre godartede angrebssimuleringer i din organisation for at vurdere din phishing-risiko og lære dine brugere, hvordan de bedre kan undgå phishangreb. Ved at følge denne vejledning kan du konfigurere automatiserede flow med bestemte teknikker og nyttedata, der kører, når de angivne betingelser er opfyldt, og starte simuleringer mod din organisation.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 2 (inkluderet som en del af E5).
- Tilstrækkelige tilladelser (rollen Sikkerhedsadministrator).
- 5-10 minutter for at udføre trinnene nedenfor.

## <a name="send-a-payload-to-target-users"></a>Send en nyttedata til målbrugere

1. Naviger til [træning i simulering af angreb](https://security.microsoft.com/attacksimulator).
1. Vælg **Simuleringsautomatiseringer** på den øverste navigationslinje.
1. Tryk på **Opret automatisering**.
1. Navngiv simuleringsautomatisering med noget relevant og mindeværdigt. *Næste*.
1. Vælg de teknikker, du vil bruge, i pop op-vinduet. *Næste*.
1. Vælg manuelt op til 20 nyttedata, du vil bruge til denne automatisering, eller vælg randomiser. *Næste*.
1. Hvis du har valgt OAuth som nyttedata, skal du angive det navn, det logo og det omfang (tilladelser), som appen skal have, når den bruges i en simulering. *Næste*.
1. Vælg, hvem der skal målrettes med nyttedataene, hvis alternativknappen fremhæves, hvis du vælger hele organisationen. *Næste*.
1. Ellers skal du vælge **Tilføj brugere** og derefter søge efter eller filtrere brugerne med guiden og trykke på Tilføj bruger(r). *Næste*.
1. Tilpas træningen, hvis det er relevant. Ellers skal du lade Tildel oplæring for mig (anbefales) være valgt. *Næste*.
1. Tilpas den landingsside, der vises, når en bruger er phished, hvis det er relevant. Ellers skal du forlade som Microsoft Standard. *Næste*.
1. Vælg, om du vil have slutbrugermeddelelser, hvis det er tilfældet, skal du vælge leveringsindstillingerne og tilpasse, hvor det er relevant. *Næste*.
1. Som simuleringsplan kan du enten vælge **Randomiseret** eller **Fast**. Den anbefalede indstilling er Randomiseret, når den er valgt, skal du vælge *Næste*.
1. Afhængigt af dit valg af Randomiseret eller Fast kan oplysningerne om tidsplanen variere, men du kan vælge indstillinger for valget, herunder start- og slutdatoerne for automatiseringen. *Næste*.
1. Under **Startoplysninger** skal du vælge de endelige indstillinger, du vil have, f.eks. bruge entydige nyttedata eller målrette gentagne lovovertrædere og derefter vælge *Næste*.
1. **Indsend** , og automatiseringen af simulering er konfigureret.

## <a name="learn-more"></a>Få mere at vide

Du kan finde fuld vejledning i [simuleringsautomatiseringer til oplæring i simulering af angreb – Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training-simulation-automations.md).
