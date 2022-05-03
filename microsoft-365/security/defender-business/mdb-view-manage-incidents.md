---
title: Få vist og administrer hændelser i Microsoft Defender til virksomheder
description: Få vist og administrer beskeder, reager på trusler, administrer enheder, og gennemse afhjælpningshandlinger på registrerede trusler i Defender for Business.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 04c8d32c6bb016d4640094013d1f71eb248a8d6c
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172718"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>Få vist og administrer hændelser i Microsoft Defender til virksomheder

Når der registreres trusler, og beskeder udløses, oprettes der hændelser. Virksomhedens sikkerhedsteam kan få vist og administrere hændelser på Microsoft 365 Defender portalen.

**Denne artikel indeholder**:

- [Sådan overvåger du dine hændelser og beskeder](#monitor-your-incidents--alerts)
- [Alvorsgrad af vigtig besked](#alert-severity)
- [Næste trin](#next-steps)

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="monitor-your-incidents--alerts"></a>Overvåg dine hændelser & beskeder

1. Vælg **Hændelser** i navigationsruden i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). Alle hændelser, der er oprettet, vises på siden.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Skærmbillede af listen Over hændelser":::

2. Vælg en besked for at åbne dens pop op-rude, hvor du kan få mere at vide om beskeden. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Skærmbillede af hændelse valgt med pop op-vinduet åbent":::

3. I pop op-ruden kan du se beskedens titel, få vist en liste over aktiver (f.eks. slutpunkter eller brugerkonti), der er berørt, udføre tilgængelige handlinger og bruge links til at få vist flere oplysninger og endda åbne detaljesiden for den valgte besked. 

> [!TIP]
> Microsoft Defender til virksomheder er designet til at hjælpe dig med at håndtere registrerede trusler ved at tilbyde anbefalede handlinger. Når du får vist en besked, skal du søge efter de anbefalede handlinger. Vær også opmærksom på den vigtige alvorsgrad, som ikke kun bestemmes på baggrund af truslens alvorsgrad, men også på risikoniveauet for din virksomhed. 

## <a name="alert-severity"></a>Alvorsgrad af vigtig besked

Når Microsoft Defender Antivirus tildeler en besked alvorsgrad baseret på den absolutte alvorsgrad af en registreret trussel (malware) og den potentielle risiko for et individuelt slutpunkt (hvis den er inficeret).
Microsoft Defender til virksomheder tildeler en besked alvorsgrad baseret på alvorsgraden af den registrerede funktionsmåde, den faktiske risiko for et slutpunkt (enhed) og endnu vigtigere den potentielle risiko for din virksomhed. I følgende tabel vises nogle eksempler:

| Scenario | Alvorsgrad af vigtig besked | Grund |
|:---|:---|:---|
| Microsoft Defender Antivirus registrerer og stopper en trussel, før den gør nogen skade. | Informative | Truslen blev stoppet, før nogen skade blev gjort. |
| Microsoft Defender Antivirus registrerer malware, der blev udført i din virksomhed. Malwaren stoppes og afhjælpes. | Lav | Selv om nogle skader kan have været gjort til et individuelt slutpunkt, malware nu udgør ingen trussel for din virksomhed. |
| Malware, der udføres, registreres af Microsoft Defender til virksomheder. Malwaren er blokeret næsten med det samme. | Mellem eller høj | Malwaren udgør en trussel mod individuelle slutpunkter og din virksomhed. |
| Mistænkelig funktionsmåde registreres, men der udføres endnu ingen afhjælpningshandlinger. | Lav, Mellem eller Høj | Alvorsgraden afhænger af, i hvor høj grad adfærden udgør en trussel for din virksomhed. |

## <a name="next-steps"></a>Næste trin

- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)
- [Få vist eller rediger enhedspolitikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md)