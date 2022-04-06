---
title: Arbejde med enhedsgrupper i Microsoft 365 Business Premium
description: Få mere at vide om enhedsgrupper Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 2cc874580dad24e1b3d5349d6075956a9e518704
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634641"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Enhedsgrupper i Microsoft 365 Business Premium

Microsoft 365 Business Premium omfatter slutpunktsbeskyttelse via Microsoft Defender til virksomheder. Politikker for enhedsbeskyttelse anvendes på enheder via visse samlinger, der kaldes enhedsgrupper. 

**I denne artikel beskrives følgende**:  

- [Hvilke enhedsgrupper er](#whats-a-device-group)
- [Sådan opretter du en ny enhedsgruppe](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Hvad er en enhedsgruppe?

En enhedsgruppe er en samling af enheder, der er grupperet sammen på grund af bestemte kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du udelader dem. 

Med dit abonnement har du standardenhedsgrupper, som du kan bruge. Standardenhedsgrupperne omfatter alle de enheder, der er onboardet til Defender for Business. Du kan dog også oprette nye enhedsgrupper for at tildele politikker for enhedsbeskyttelse med bestemte indstillinger til bestemte enheder. 

Alle enhedsgrupper, herunder dine standardenhedsgrupper og eventuelle brugerdefinerede enhedsgrupper, som du definerer, gemmes [i Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>Hvordan gør jeg du oprette en ny enhedsgruppe?

Du kan oprette en ny enhedsgruppe, mens du er i gang med at oprette eller redigere en politik for enhedsbeskyttelse. 

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg Enhedskonfiguration i **navigationsruden**. 

3. Gør et af følgende:

    1. Vælg en eksisterende politik, og vælg derefter **Rediger**.
    
    2. Vælg **+ Tilføj for** at oprette en ny politik.

    > [!TIP]
    > Hvis du vil have hjælp til at oprette eller redigere en politik, [skal du se Få vist eller rediger politikker Microsoft Defender til virksomheder](m365bp-view-edit-create-mdb-policies.md).

4. Gennemgå oplysningerne **i trinnet** Generelle oplysninger, rediger om nødvendigt, og vælg derefter **Næste**.

5. Vælg **+ Opret ny gruppe**. 

6. Angiv et navn og en beskrivelse af enhedsgruppen, og vælg derefter **Næste**.

7. Vælg de enheder, der skal medtages i gruppen, og vælg derefter **Opret gruppe**.

8. Gennemgå listen **over enhedsgrupper** for politikken på trinnet Enhedsgrupper. Hvis det er nødvendigt, kan du fjerne en gruppe fra listen. Vælg derefter **Næste**.

9. På siden **Konfigurationsindstillinger** skal du gennemse og redigere indstillingerne efter behov og derefter vælge **Næste**. Du kan finde flere oplysninger om disse indstillinger [under Forstå næste generations konfigurationsindstillinger Microsoft Defender til virksomheder](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. På **trinnet Gennemse din** politik skal du gennemse alle indstillingerne, foretage de nødvendige ændringer og derefter vælge **Opret politik** eller **Opdater politik**.


