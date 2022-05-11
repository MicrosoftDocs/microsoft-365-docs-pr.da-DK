---
title: Arbejde med enhedsgrupper i Microsoft 365 Business Premium
description: Få mere at vide om enhedsgrupper i Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 03/16/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 2c218cd2b0f04201f46155a72a916cc7676aaddb
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "65320812"
---
# <a name="device-groups-in-microsoft-365-business-premium"></a>Enhedsgrupper i Microsoft 365 Business Premium

Microsoft 365 Business Premium omfatter beskyttelse af slutpunkter via Microsoft Defender til virksomheder. Politikker for enhedsbeskyttelse anvendes på enheder via visse samlinger, der kaldes enhedsgrupper. 

**I denne vejledning beskrives**:  

- [Hvilke enhedsgrupper er](#whats-a-device-group)
- [Sådan opretter du en ny enhedsgruppe](#how-do-i-create-a-new-device-group)

## <a name="whats-a-device-group"></a>Hvad er en enhedsgruppe?

En enhedsgruppe er en samling af enheder, der er grupperet på grund af visse angivne kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du ekskluderer dem. 

Med dit abonnement har du standardenhedsgrupper, som du kan bruge. Standardenhedsgrupperne omfatter alle de enheder, der er onboardet til Defender for Business. Du kan dog også oprette nye enhedsgrupper for at tildele politikker for enhedsbeskyttelse med bestemte indstillinger til bestemte enheder. 

Alle enhedsgrupper, herunder dine standardenhedsgrupper og brugerdefinerede enhedsgrupper, som du definerer, gemmes i [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="how-do-i-create-a-new-device-group"></a>Hvordan gør jeg oprette en ny enhedsgruppe?

Du kan oprette en ny enhedsgruppe, mens du er i gang med at oprette eller redigere en politik for enhedsbeskyttelse. 

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Enhedskonfiguration** i navigationsruden. 

3. Udfør en af følgende handlinger:

    1. Vælg en eksisterende politik, og vælg derefter **Rediger**.
    
    2. Vælg **+ Tilføj** for at oprette en ny politik.

    > [!TIP]
    > Hvis du vil have hjælp til at oprette eller redigere en politik, skal du se [Få vist eller rediger politikker i Microsoft Defender til virksomheder](m365bp-view-edit-create-mdb-policies.md).

4. Gennemse oplysningerne i trinnet **Generelle oplysninger** , rediger dem, hvis det er nødvendigt, og vælg derefter **Næste**.

5. Vælg **+ Opret ny gruppe**. 

6. Angiv et navn og en beskrivelse til enhedsgruppen, og vælg derefter **Næste**.

7. Vælg de enheder, der skal medtages i gruppen, og vælg derefter **Opret gruppe**.

8. Gennemse listen over enhedsgrupper for politikken på trinnet **Enhedsgrupper** . Hvis det er nødvendigt, skal du fjerne en gruppe fra listen. Vælg derefter **Næste**.

9. Gennemse og rediger indstillingerne efter behov på siden **Konfigurationsindstillinger** , og vælg derefter **Næste**. Du kan finde flere oplysninger om disse indstillinger [under Forstå næste generations konfigurationsindstillinger i Microsoft Defender til virksomheder](../security/defender-business/mdb-next-gen-configuration-settings.md).

10. Gennemse alle indstillingerne i trinnet **Gennemse din politik** , foretag de nødvendige ændringer, og vælg derefter **Opret politik** eller **Opdater politik**.

## <a name="next-steps"></a>Næste trin

Nu, hvor du har fuldført dine primære missioner, kan du konfigurere dine [svarteams](m365bp-security-incident-management.md) og [vedligeholde dit miljø](m365bp-maintain-environment.md).

