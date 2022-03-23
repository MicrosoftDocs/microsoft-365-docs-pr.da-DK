---
title: Forstå vurdering i relevans i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1d33d4fb-91ed-41c0-b72e-5a26eca3a2a7
description: Få et overblik over fasen Bedømmelse og dens rolle i vurderingen af den omfattende betydning for relevanskurser i Microsoft 365 Advanced eDiscovery.
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 80ec4f0c362ff403f45123bf837e82c5d2f6ed7e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589518"
---
# <a name="assessment-in-the-relevance-module-in-advanced-ediscovery"></a>Vurdering i relevansmodulet i Advanced eDiscovery
  
Advanced eDiscovery det muligt at foretage en tidlig vurdering, f.eks. for de definerede problemer og de importerede data for en sag. Advanced eDiscovery kan gøre det muligt for eksperten at træffe beslutninger om en indført tilgang og anvende disse beslutninger i dokumentgennemsynsprojektet.
  
## <a name="understanding-assessment"></a>Forstå bedømmelse

Eksperten gennemgår et vilkårligt sæt af mindst 500 filer, som bruges til at afgøre, hvor omfattende problemerne er, og til at udarbejde statistik, der afspejler uddannelsesresultaterne. Vurdering er vellykket, når der er fundet tilstrækkeligt med relevante filer til at nå et statistisk niveau, som kan hjælpe Advanced eDiscovery relevans med at levere nøjagtig statistik og for effektivt at bestemme stabiliseringspunktet i uddannelsesprocessen. 
  
Jo højere antallet af relevante filer i bedømmelsessættet er, desto mere nøjagtig bliver statistikken og effektiviteten af stabilitetsalgoritmen. Antallet af relevante filer i bedømmelsesfilerne afhænger af problemets omfattende indhold. Richness is the estimated percent of relevant files in the set relevant to an issue. Problemer med større richness vil nå et højere antal relevante filer hurtigere end problemer med lavere richness. Problemer med meget lav richness (f.eks. 2 % eller mindre) kræver et meget stort antal bedømmelsessæt for at nå et betydeligt antal relevante filer.
  
Den statistik, der præsenteres i fanerne Spor og Beslut under uddannelse og efter batchberegningen, omfatter estimering af tilbagekaldelse for forskellige korrektursæt. I statistik omfatter estimeringerne, der er baseret på et stikprøvesæt (i dette tilfælde vurderingsfilerne), fejlmargenen og tillidsniveauet for den pågældende fejlmargen. Anslået tilbagekaldelse af 80 % kan f.eks. have en fejlmargen på plus eller minus 5 % med et tillidsniveau på 95 %. Det betyder, at den anslåede tilbagekaldelse faktisk er 75 %-85 %, og dette estimering har 95 % tillid. Jo større bedømmelsessættet er, jo mindre bliver fejlmargenen, og statistikken er mere nøjagtig. 
  
Når eksperten har gennemset et indledende bedømmelsessæt med 500 filer, kan Relevans afgøre den aktuelle fejlmargen for tilbagekaldelsesværdierne. Relevansen vil også anbefale en standardmargen for fejl, der kan nås, for at optimere bedømmelsessættet. Her er nogle eksempler:
  
- Hvis bedømmelsessættet allerede gav en fejlmargen på plus eller minus 10 %, anbefaler Relevans, at du går videre til uddannelse (ingen yderligere vurdering er nødvendig). 

- Hvis bedømmelsessættet gav en fejlmargen på plus eller minus 13 %, kan Relevans anbefale gennemgangen af et andet sæt bedømmelsesfiler for at nå en mindre margen. 

- Hvis den omfattende mængde er meget lav, kan relevans anbefale at stoppe vurderingen, selvom fejlmargenen er stor (hvilket gør statistik upraktisk), fordi det skøn, der kræves for at nå en nyttig fejlmargen, er for stor.

Hvert problem har sit eget indhold, den aktuelle fejlmargen og det anslåede antal yderligere vurderingsfiler. Det næste bedømmelsessæt oprettes ud fra det maksimale antal filer (op til 1.000 i et enkelt sæt).
  
Du kan acceptere anbefalingerne for relevans eller justere den aktuelle fejlmargen efter dine behov. Standardmargenen for den aktuelle fejl bestemmes for tilbagekaldelse ved ens eller over 75 %.
  
> [!NOTE]
> Fasen Bedømmelse kan **\>** tilsidesættes på fanen Relevansspor i den udvidede visning for et problem ved at fjerne markeringen i afkrydsningsfeltet Vurdering pr. problem og derefter for "alle problemer". Der vil derfor ikke være nogen statistik for dette problem. Rydning **af afkrydsningsfeltet** Bedømmelse kan kun udføres, før der udføres en vurdering. Hvis der findes flere problemer i en sag, tilsidesættes vurderingen kun, hvis afkrydsningsfeltet ikke er markeret for hvert problem.
