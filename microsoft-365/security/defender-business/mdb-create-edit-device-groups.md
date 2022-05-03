---
title: Enhedsgrupper i Microsoft Defender til virksomheder
description: Sikkerhedspolitikker anvendes på enheder via enhedsgrupper i Defender for Business.
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
ms.openlocfilehash: abb1c694f98ace7595f1389e3270ca3479d0c745
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172219"
---
# <a name="device-groups-in-microsoft-defender-for-business"></a>Enhedsgrupper i Microsoft Defender til virksomheder

I Microsoft Defender til virksomheder anvendes politikker på enheder via visse samlinger, der kaldes enhedsgrupper. 

**I denne artikel beskrives**:  

- [Hvilke enhedsgrupper er](#what-is-a-device-group)   
- [Sådan opretter du enhedsgrupper i Defender for Business](#create-a-new-device-group)
- [Sådan får du vist en eksisterende enhedsgruppe](#view-an-existing-device-group)
- [Hvad gør indstillingen Tilføj alle enheder?](#what-does-the-add-all-devices-option-do)

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="what-is-a-device-group"></a>Hvad er en enhedsgruppe?

En enhedsgruppe er en samling af enheder, der er grupperet på grund af visse angivne kriterier, f.eks. operativsystemversionen. Enheder, der opfylder kriterierne, er inkluderet i den pågældende enhedsgruppe, medmindre du ekskluderer dem. I Microsoft Defender til virksomheder anvendes politikker på enheder ved hjælp af enhedsgrupper.

Defender for Business indeholder standardenhedsgrupper, som du kan bruge. Standardenhedsgrupperne omfatter alle de enheder, der er onboardet til Defender for Business. Der er f.eks. en standardenhedsgruppe for Windows enheder. Når du onboarder Windows enheder, føjes de automatisk til standardenhedsgruppen.

Du kan også oprette nye enhedsgrupper for at tildele politikker med bestemte indstillinger til bestemte enheder. Du kan f.eks. have tildelt en firewallpolitik til ét sæt Windows enheder og en anden firewallpolitik, der er tildelt et andet sæt Windows enheder. Du kan definere specifikke enhedsgrupper, der skal bruges sammen med dine politikker.

> [!NOTE]
> Når du opretter politikker i Defender for Business, tildeles en prioritetsrækkefølge. Hvis du anvender flere politikker på et bestemt sæt enheder, modtager disse enheder kun den første anvendte politik. Du kan få flere oplysninger [under Forstå politikrækkefølgen i Microsoft Defender til virksomheder](mdb-policy-order.md).

Alle enhedsgrupper, herunder dine standardenhedsgrupper og brugerdefinerede enhedsgrupper, som du definerer, gemmes i [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis) (Azure AD).

## <a name="create-a-new-device-group"></a>Opret en ny enhedsgruppe

I Øjeblikket kan du i Defender for Business oprette en ny enhedsgruppe, mens du er i gang med at oprette eller redigere en politik, som beskrevet i følgende procedure: 

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Enhedskonfiguration** i navigationsruden. 

3. Udfør en af følgende handlinger:

    1. Vælg en eksisterende politik, og vælg derefter **Rediger**.
    2. Vælg **+ Tilføj** for at oprette en ny politik.

    > [!TIP]
    > Hvis du vil have hjælp til at oprette eller redigere en politik, skal du se [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md).

4. Gennemse oplysningerne i trinnet **Generelle oplysninger** , rediger dem, hvis det er nødvendigt, og vælg derefter **Næste**.

5. Vælg **+ Opret ny gruppe**. 

6. Angiv et navn og en beskrivelse til enhedsgruppen, og vælg derefter **Næste**.

7. Vælg de enheder, der skal medtages i gruppen, og vælg derefter **Opret gruppe**.

8. Gennemse listen over enhedsgrupper for politikken på trinnet **Enhedsgrupper** . Hvis det er nødvendigt, skal du fjerne en gruppe fra listen. Vælg derefter **Næste**.

9. Gennemse og rediger indstillingerne efter behov på siden **Konfigurationsindstillinger** , og vælg derefter **Næste**. Du kan få flere oplysninger om disse indstillinger under [Konfigurationsindstillinger](mdb-next-gen-configuration-settings.md).

10. Gennemse alle indstillingerne i trinnet **Gennemse din politik** , foretag de nødvendige ændringer, og vælg derefter **Opret politik** eller **Opdater politik**.

## <a name="view-an-existing-device-group"></a>Få vist en eksisterende enhedsgruppe

I Defender for Business kan du i øjeblikket få vist dine eksisterende enhedsgrupper, mens du er i gang med at oprette eller redigere en politik, som beskrevet i følgende procedure: 

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Enhedskonfiguration** i navigationsruden. 

3. Udfør en af følgende handlinger:

    1. Vælg en eksisterende politik, og vælg derefter **Rediger**.
    2. Vælg **+ Tilføj** for at oprette en ny politik.

    > [!TIP]
    > Hvis du vil have hjælp til at oprette eller redigere en politik, skal du se [Få vist eller rediger politikker i Microsoft Defender til virksomheder](mdb-view-edit-policies.md).

4. Gennemse oplysningerne i trinnet **Generelle oplysninger** , rediger dem, hvis det er nødvendigt, og vælg derefter **Næste**.

5. Vælg **Brug eksisterende gruppe**. Et pop op-vindue åbnes og viser enhedsgrupper. Hvis du endnu ikke har nogen enhedsgrupper, bliver du bedt om at oprette en ny enhedsgruppe.

## <a name="what-does-the-add-all-devices-option-do"></a>Hvad gør indstillingen Tilføj alle enheder?

Når du opretter eller redigerer en politik, kan du muligvis se indstillingen **Tilføj alle enheder** .

:::image type="content" source="media/add-all-devices-option.png" alt-text="Skærmbillede af indstillingen Tilføj alle enheder.":::

Hvis du vælger denne indstilling, modtager alle de enheder, der er tilmeldt Microsoft Intune som standard den politik, du opretter eller redigerer. 

## <a name="next-steps"></a>Næste trin

Vælg en eller flere af følgende opgaver:

- [Få vist eller rediger politikker](mdb-view-edit-policies.md)
- [Opret en ny politik](mdb-create-new-policy.md)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)