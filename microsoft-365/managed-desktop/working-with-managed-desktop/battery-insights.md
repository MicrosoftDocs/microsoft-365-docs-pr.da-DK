---
title: Batteriindsigt
description: En rapport, der viser data om forventet batterilevetid og bedste forbrugere
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
audience: Admin
ms.openlocfilehash: 32ab3a984d5ab46aac26989518cd3e570082d688
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2021
ms.locfileid: "63588986"
---
# <a name="battery-insights"></a>Batteriindsigt
Denne visning indeholder målepunkter for strøm, batteri og appanvendelse for dine Microsoft-administrerede stationære enheder. En app anses for at være "i brug", hvis den kører og er i fokus.

Hvis du vil have vist brugsdata, skal du **vælge fanen** Batteri.

![Ruden Batteri: Forudsagt batterilevetid pr. enhedsmodel øverst til venstre, de vigtigste energiforbrugere (efter app) øverst til højre, Insights-tabel over bunden. Linket Dokumentation øverst til højre](../../media/insights_battery.png)

## <a name="predicted-battery-life"></a>Forventet batterilevetid

I området **Forventet batterilevetid leverer** vi prognoser for den forventede batterilevetid for dine enheder, organiseret efter enhedsmodel.

> [!NOTE]
> Disse data er afledt af stikprøver af energiforbrug, brugstid og batterikapacitet fra et <em></em> tilfældigt udvalg af enhederne i din Microsoft Managed Desktop-installation, som også rapporterer data.

Tabellen leverer den forventede batterilevetid (i timer), gennemsnitlig batterilevetid for de samme modeller i andre Microsoft Managed Desktop-installationer samt antallet af enheder, der rapporterer disse data i dit miljø. Sortér dataene ved at vælge kolonneoverskrifterne.



## <a name="top-energy-consumers"></a>De bedste energiforbrugere

I området **Vigtigste energiforbrugere** finder du de apps i dit miljø, der bruger mest energi i milliWatt-timer (mWh). De viste apps er pr. bestemt enhed, som du vælger **i sektionen Forudsagt batterilevetid** til venstre. Hvis du f.eks. vil se forbrug pr. app for dine Microsoft Surface Book 2-enheder, skal du vælge den pågældende række i området for batterilevetid. Hvis du ikke vælger en model, er de viste appforbrugsdata for alle apps, som vi har data for samlet.

 For hver app viser farvede segmenter fordelingen af appens energianvendelse mellem disse kategorier:

- CPU
- Vis
- Netværk
- Andet

"Andre" kan omfatte energiforbrug fra forskellige kilder, f.eks. diskaktivitet, brug af mobilbredbånd og energi, der går tabt som følge af intern modhed. 

Du kan filtrere denne visning, så der kun vises forgrundsapps, baggrundsapps eller begge dele, ved hjælp af menuen øverst til højre. Forgrundsapps er dem, der har haft brugerinteraktion inden for de seneste 28 dage, f.eks. valg af noget med en mus.

## <a name="insights"></a>Insights

Området **Insights** de tre vigtigste energiforbrugere i kategorierne CPU og netværk. Disse elementer bruger energi, der er højere end gennemsnittet, sammenlignet med alle Microsoft Managed Desktop-installationer. Visningsressourcen vises ikke, da den i høj grad afhænger af indstillingerne for enhedens brugstid og lysstyrke. 

Vælg listerne i kolonnen **Detaljer for** at få flere oplysninger.

## <a name="battery-optimization"></a>Batterioptimering

Windows 10 tilbyder mange [enhedsindstillinger til](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips) at forbedre strømforbrug og øge batterilevetiden på dine Microsoft Managed Desktop-enheder. Nogle af disse indstillinger kan forringe Windows funktionalitet, så du også er nødt til at overveje andre faktorer, f.eks. enhedens rolle i organisationen. Windows understøtter en liste over disse tip [til at spare på batteriet](https://support.microsoft.com/help/20443/windows-10-battery-saving-tips).

Brugerne kan justere nogle indstillinger selv uden behov for administratorhøjde eller support. Andre indstillinger kræver support fra din organisations it-administrator.
