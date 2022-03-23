---
title: Re besvare og afhjælpe trusler i Microsoft Defender for Business
description: I tilfælde af at der registreres trusler, kan du reagere på og afhjælpe disse trusler.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f57774f993c0044878655713202d6835a2a69173
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593039"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>Re besvare og afhjælpe trusler i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Portalen Microsoft 365 Defender gør det muligt for dit sikkerhedsteam at reagere på og afhjælpe registrerede trusler. I denne artikel får du vist et eksempel på, hvordan du kan bruge Defender for Business.

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="view-detected-threats"></a>Få vist registrerede trusler

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Meddelelseskort på startsiden. Kort giver dig et hurtigt overblik over, hvor mange trusler der blev registreret, samt hvor mange brugerkonti, slutpunkter (enheder) og andre aktiver, der blev påvirket. Følgende billede er et eksempel på kort, du kan få vist:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Skærmbillede af kort i Microsoft 365 Defender portal":::

3. Vælg en knap eller et link på kortet for at få vist flere oplysninger og gøre noget. Som et eksempel omfatter vores **enheder med risikokort** knappen **Vis** detaljer. Hvis du vælger denne knap, kommer vi til **lagersiden** for enheder, sådan som det er vist på følgende billede:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Skærmbillede af lager over enheder":::

   På **lagersiden** for enheder vises virksomhedens enheder sammen med deres risikoniveau og eksponeringsniveau.

4. Vælg et element, f.eks. en enhed. En pop op-rude åbnes og viser flere oplysninger om beskeder og hændelser, der genereres for det pågældende element, som vist på følgende billede:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Skærmbillede af pop op-ruden for en valgt enhed":::

5. Få vist de viste oplysninger i pop op-pop-op-pop-op-pop-meddelelse. Vælg ellipsen (...) for at åbne en menu, der viser tilgængelige handlinger, som vist på følgende billede: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Skærmbillede af tilgængelige handlinger for en valgt enhed":::

6. Vælg en tilgængelig handling. Du kan f.eks. **vælge Kør antivirus-scanning**, som Microsoft Defender Antivirus til at starte en hurtig scanning på enheden. Eller du kan vælge **Initier automatiseret undersøgelse** for at udløse en automatisk undersøgelse på enheden.

## <a name="next-steps"></a>Næste trin

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)

- [Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)