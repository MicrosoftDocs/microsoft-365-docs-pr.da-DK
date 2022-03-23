---
title: Få vist og administrer hændelser i Microsoft Defender for Business
description: Få mere at vide om, & du kan administrere beskeder, reagere på trusler, administrere enheder og gennemse afhjælpningshandlinger
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
ms.openlocfilehash: a814aa4ad002672fa3451ef1bcc524d9b03d4eb5
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593670"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>Få vist og administrer hændelser i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

I tilfælde af at der registreres trusler, og der udløses beskeder, oprettes der hændelser. Din virksomheds sikkerhedsteam kan få vist og administrere hændelser i Microsoft 365 Defender-portalen.

**Denne artikel indeholder**:

- [Sådan overvåger du dine hændelser og beskeder](#monitor-your-incidents--alerts)

- [Besked om alvorsgrad](#alert-severity)

- [Næste trin](#next-steps)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="monitor-your-incidents--alerts"></a>Overvåg dine & beskeder

1. Vælg Hændelser Microsoft 365 Defender [https://security.microsoft.com](https://security.microsoft.com) navigationsruden i **navigationsruden**. Alle hændelser, der er blevet oprettet, vises på siden.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Skærmbillede af listen over hændelser":::

2. Vælg en besked for at åbne pop op-ruden med pop op-vinduet, hvor du kan få mere at vide om beskeden. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Skærmbillede af hændelse markeret med pop op-knappen åben":::

3. I pop op-ruden kan du se beskedens titel, få vist en liste over aktiver (f.eks. slutpunkter eller brugerkonti), der er blevet påvirket, udføre tilgængelige handlinger og bruge links til at få vist flere oplysninger og endda åbne detaljesiden for den valgte besked. 

> [!TIP]
> Microsoft Defender for Business er udviklet til at hjælpe dig med at håndtere registrerede trusler ved at tilbyde anbefalede handlinger. Når du får vist en besked, skal du se efter de anbefalede handlinger, du kan udføre. Du skal også være opmærksom på alvorsniveauet for din besked, som ikke blot bestemmes ud fra alvorsniveauet for truslerne, men også på risikoniveau for din virksomhed. 

## <a name="alert-severity"></a>Besked om alvorsgrad

Når Microsoft Defender Antivirus tildeler en besked alvorsgrad baseret på den absolutte alvor af en registreret trussel (malware) og den potentielle risiko for et enkelt slutpunkt (hvis inficeret).
Microsoft Defender for Business tildeler en alarm alvorlighed baseret på alvorligheden af den registrerede funktionsmåde, den faktiske risiko for et slutpunkt (enhed) og ikke mere vigtigt, den potentielle risiko for din virksomhed. I følgende tabel vises nogle få eksempler: <br/><br/>

| Scenarie | Besked om alvorsgrad | Årsag |
|:---|:---|:---|
| Microsoft Defender Antivirus registrerer og stopper en trussel, før den gør nogen skade. | Information | Truslerne blev stoppet, før skaden blev udført. |
| Microsoft Defender Antivirus registrerer malware, der er blevet udført i din virksomhed. Malwaren stoppes og afhjælpes. | Lav | Selvom der kan være gjort noget skade på et enkelt slutpunkt, udgør malwaren nu ingen trussel mod din virksomhed. |
| Malware, der udføres, registreres af Microsoft Defender for Business. Malwaren blokeres næsten øjeblikkeligt. | Mellem eller Høj | Malwaren udgør en trussel mod individuelle slutpunkter og din virksomhed. |
| Mistænkelig adfærd registreres, men der er endnu ikke foretaget nogen afhjælpningshandlinger. | Lav, Mellem eller Høj | Alvorsgraden afhænger af, i hvilken grad funktionsmåden udgør en trussel mod din virksomhed. |

## <a name="next-steps"></a>Næste trin

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)

- [Få vist eller rediger enhedspolitikker i Microsoft Defender for Business](mdb-view-edit-policies.md)