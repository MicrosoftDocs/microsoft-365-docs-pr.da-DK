---
title: Enhedsgrupper i Microsoft Defender for Business
description: Få mere at vide om enhedsgrupper i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 340d696d2fbc6b698821c54962d04502d6781701
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594698"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>Enhedsgrupper i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

I Microsoft Defender for Business anvendes politikker for enheder via visse samlinger, der kaldes enhedsgrupper. 

**I denne artikel beskrives følgende**:  

- [Hvilke enhedsgrupper er](#what-is-a-device-group)   
- [Sådan opretter du enhedsgrupper i Defender for Business](#create-a-new-device-group)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="what-is-a-device-group"></a>Hvad er en enhedsgruppe?

En enhedsgruppe er en samling af enheder, der er grupperet sammen på grund af bestemte kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du udelader dem. I Microsoft Defender for Business anvendes politikker for enheder ved hjælp af enhedsgrupper. 

Defender for Business omfatter standardenhedsgrupper, som du kan bruge. Standardenhedsgrupperne omfatter alle de enheder, der er onboardet til Defender for Business. Du kan dog også oprette nye enhedsgrupper til at tildele politikker med bestemte indstillinger til bestemte enheder. 

Alle enhedsgrupper, herunder dine standardenhedsgrupper og eventuelle brugerdefinerede enhedsgrupper, som du definerer, gemmes [i Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>Opret en ny enhedsgruppe

I øjeblikket kan du i Defender for Business oprette en ny enhedsgruppe, mens du er i gang med at oprette eller redigere en politik, som beskrevet i følgende procedure: 

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg Enhedskonfiguration i **navigationsruden**. 

3. Gør et af følgende:

    1. Vælg en eksisterende politik, og vælg derefter **Rediger**.
    2. Vælg **+ Tilføj for** at oprette en ny politik.

    > [!TIP]
    > Hvis du vil have hjælp til at oprette eller redigere en politik, [skal du se Få vist eller rediger politikker i Microsoft Defender for Business](mdb-view-edit-policies.md).

4. Gennemgå oplysningerne **i trinnet** Generelle oplysninger, rediger om nødvendigt, og vælg derefter **Næste**.

5. Vælg **+ Opret ny gruppe**. 

6. Angiv et navn og en beskrivelse af enhedsgruppen, og vælg derefter **Næste**.

7. Vælg de enheder, der skal medtages i gruppen, og vælg derefter **Opret gruppe**.

8. Gennemgå listen **over enhedsgrupper** for politikken på trinnet Enhedsgrupper. Hvis det er nødvendigt, kan du fjerne en gruppe fra listen. Vælg derefter **Næste**.

9. På siden **Konfigurationsindstillinger** skal du gennemse og redigere indstillingerne efter behov og derefter vælge **Næste**. Du kan finde flere oplysninger om disse indstillinger under [Konfigurationsindstillinger](mdb-next-gen-configuration-settings.md).

10. På **trinnet Gennemse din** politik skal du gennemse alle indstillingerne, foretage de nødvendige ændringer og derefter vælge **Opret politik** eller **Opdater politik**.

## <a name="next-steps"></a>Næste trin

Vælg en eller flere af følgende opgaver:

- [Få vist eller rediger politikker](mdb-view-edit-policies.md)

- [Opret en ny politik](mdb-create-new-policy.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)