---
title: Forstå vurdering i relevans i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få et overblik over vurderingsfasen og dens rolle i forbindelse med bestemmelse af de mange problemer under relevanstræning i Microsoft Purview eDiscovery (Premium).
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 19d518e116fbd86dc0f781443ba16c21890c4346
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625549"
---
# <a name="assessment-in-the-relevance-module-in-ediscovery-premium"></a>Vurdering i relevansmodulet i eDiscovery (Premium)
  
Microsoft Purview eDiscovery (Premium) muliggør tidlig vurdering, f.eks. for de definerede problemer og de data, der er importeret for en sag. Med eDiscovery (Premium) kan eksperten træffe beslutninger om en vedtaget tilgang og anvende disse beslutninger på projektet til dokumentgennemgang.
  
## <a name="understanding-assessment"></a>Om vurdering

I vurderingen gennemgår eksperten et tilfældigt sæt på mindst 500 filer, som bruges til at fastslå, hvor omfattende problemerne er, og til at udarbejde statistikker, der afspejler uddannelsesresultater. Vurderingen lykkes, når der findes nok relevante filer til at nå et statistisk niveau, der hjælper eDiscovery (Premium) Relevans til at levere nøjagtige statistikker og til effektivt at bestemme stabiliseringspunktet i uddannelsesprocessen. 
  
Jo højere antal relevante filer i vurderingssættet, jo mere nøjagtige statistikker og effektivitet af stabilitetsalgoritmen. Antallet af relevante filer i vurderingsfilerne afhænger af problemets rigdom. Richness er den anslåede procentdel af relevante filer i sættet, der er relevant for et problem. Problemer med større rigdom vil hurtigere nå et højere antal relevante filer end problemer med lavere rigdom. Problemer med meget lav rigdom (f.eks. 2 % eller mindre) kræver et meget stort vurderingssæt for at nå et betydeligt antal relevante filer.
  
De statistikker, der vises under fanerne Spor og Beslut under oplæring og efter batchberegning, omfatter estimering af genkaldelse for forskellige korrektursæt. I statistikker omfatter skøn, der er baseret på et eksempelsæt (i dette tilfælde vurderingsfilerne), fejlmargenen og tillidsniveauet for fejlmargenen. Anslået genkaldelse af 80 % kan f.eks. have en fejlmargen på plus eller minus 5 % med et konfidensniveau på 95 %. Det betyder, at den anslåede genkaldelse rent faktisk er 75 %-85 %, og at dette skøn har 95 % tillid. Jo større vurderingssættet er, bliver fejlmargenen mindre, og statistikkerne er mere nøjagtige. 
  
Når eksperten har gennemset et indledende vurderingssæt på 500 filer, kan Relevans bestemme den aktuelle fejlmargen for genkaldelsesværdierne. Relevans anbefaler også en standardmargen for fejl for at nå for at optimere vurderingssættet. Her er nogle eksempler:
  
- Hvis vurderingssættet allerede gav en fejlmargen på plus eller minus 10 %, anbefaler Relevans, at man går videre til uddannelse (der kræves ingen yderligere vurdering). 

- Hvis vurderingssættet gav en fejlmargen på plus eller minus 13 %, anbefaler Relevans muligvis gennemgangen af et andet sæt vurderingsfiler for at nå en mindre margen. 

- Hvis rigdommen er meget lav, anbefaler Relevans muligvis at stoppe vurderingen, selvom fejlmargenen er stor (hvilket gør det upraktisk at bruge statistikker), fordi den vurdering, der er nødvendig for at nå frem til en nyttig fejlmargen, er for stor.

Hvert problem har sin egen rigdom, aktuelle fejlmargen og som et resultat heraf det anslåede antal ekstra vurderingsfiler. Det næste vurderingssæt oprettes i henhold til det maksimale antal filer (op til 1.000 i et enkelt sæt).
  
Du kan acceptere relevansanbefalinger eller justere den aktuelle fejlmargen i henhold til dine behov. Standarden for den aktuelle fejlmargen bestemmes for tilbagekaldelse med ens eller over 75 %.
  
> [!NOTE]
> Vurderingsfasen kan tilsidesættes under fanen **Relevanssporing \>** i den udvidede visning for et problem ved at fjerne markeringen i afkrydsningsfeltet **Vurdering** for hvert problem og derefter for "alle problemer". Der vil derfor ikke være nogen statistikker for dette problem. Rydning af afkrydsningsfeltet **Vurdering** kan kun udføres, før vurderingen udføres. Hvis der findes flere problemer i en sag, tilsidesættes vurderingen kun, hvis afkrydsningsfeltet er ryddet for hvert problem.
