---
title: Detaljer og resultater af en automatiseret undersøgelse
description: Få vist resultaterne og de vigtigste resultater af den automatiserede undersøgelse i Microsoft 365 Defender
keywords: automatiseret, undersøgelse, resultater, analysere, detaljer, afhjælpning, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: cc53717feed347019540ffcb8c85687a6c28537f
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607471"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Detaljer og resultater af en automatiseret undersøgelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Med Microsoft 365 Defender er oplysninger om undersøgelsen tilgængelige både under og efter den automatiserede undersøgelsesproces, når en [automatiseret undersøgelse](m365d-autoir.md) kører. Hvis du har de [nødvendige tilladelser](m365d-action-center.md#required-permissions-for-action-center-tasks), kan du få vist disse oplysninger i en visning af undersøgelsesdetaljer, der giver dig opdateret status og mulighed for at godkende eventuelle ventende handlinger. 

## <a name="new-unified-investigation-page"></a>(NY) Unified Investigation-side

Undersøgelsessiden er for nylig blevet opdateret, så den indeholder oplysninger på tværs af dine enheder, mail og samarbejdsindhold. Den nye, samlede undersøgelsesside definerer et fælles sprog og giver en samlet oplevelse for automatiske undersøgelser på tværs af [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) og [Microsoft Defender for Office 365](../office-365-security/defender-for-office-365.md). Hvis du vil have adgang til siden med den samlede undersøgelse, skal du vælge linket i det gule banner, du får vist på:

- En hvilken som helst undersøgelsesside i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a>
- En hvilken som helst undersøgelsesside på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com))
- Enhver hændelses- eller Handlingscenter-oplevelse på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>

## <a name="open-the-investigation-details-view"></a>Åbn visningen med undersøgelsesoplysninger

Du kan åbne visningen med undersøgelsesdetaljer ved hjælp af en af følgende metoder:

- [Vælg et element i Løsningscenter](#select-an-item-in-the-action-center)
- [Vælg en undersøgelse fra en side med oplysninger om hændelser](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>Vælg et element i Løsningscenter

Det forbedrede [Handlingscenter](m365d-action-center.md) ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) samler [afhjælpningshandlinger](m365d-remediation-actions.md) på tværs af dine enheder, mail & samarbejdsindhold og identiteter. De viste handlinger omfatter afhjælpningshandlinger, der blev udført automatisk eller manuelt. I Løsningscenter kan du få vist handlinger, der afventer godkendelse, og handlinger, der allerede er godkendt eller fuldført. Du kan også navigere til flere detaljer, f.eks. en undersøgelsesside.

> [!TIP]
> Du skal have [visse tilladelser](m365d-action-center.md#required-permissions-for-action-center-tasks) til at godkende, afvise eller fortryde handlinger.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal,</a> og log på. 

2. Vælg **Løsningscenter** i navigationsruden. 

3. Vælg et element under fanen **Ventende** eller **Oversigt** . Dens pop op-rude åbnes.

4. Gennemse oplysningerne i pop op-ruden, og udfør derefter et af følgende trin:
   - Vælg **siden Åbn undersøgelse** for at få vist flere oplysninger om undersøgelsen.
   - Vælg **Godkend** for at starte en ventende handling.
   - Vælg **Afvis** for at forhindre, at der udføres en ventende handling.
   - Vælg **Gå på jagt** for at gå ind i [Avanceret jagt](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Åbn en undersøgelse fra en side med oplysninger om en hændelse

Brug en side med oplysninger om hændelser til at få vist detaljerede oplysninger om en hændelse, herunder beskeder, der blev udløst oplysninger om alle berørte enheder, brugerkonti eller postkasser.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal,</a> og log på. 

2. Vælg **Hændelser & beskeder** > **Hændelser** i navigationsruden. 

3. Vælg et element på listen, og vælg derefter **Åbn hændelsesside**.

4. Vælg fanen **Undersøgelser** , og vælg derefter en undersøgelse på listen. Dens pop op-rude åbnes.

5. Vælg **siden Åbn undersøgelse**. 

Her er et eksempel.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Undersøgelsessiden på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>Undersøgelsesoplysninger

Brug visningen med undersøgelsesoplysninger til at se tidligere, aktuelle og ventende aktiviteter, der vedrører en undersøgelse. Her er et eksempel.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Siden med undersøgelsesoplysninger på Microsoft 365 Defender-portalen" lightbox="../../media/mtp-air-investdetails.png":::

I visningen Undersøgelsesoplysninger kan du se oplysninger i **grafen Undersøgelse**, **Beskeder**, **Enheder**, **Identiteter**, **Nøgleresultater**, **Enheder**, **Log** og **Ventende handlinger** , som beskrevet i følgende tabel.

> [!NOTE]
> De specifikke faner, du kan se på en side med undersøgelsesoplysninger, afhænger af, hvad dit abonnement omfatter. Hvis dit abonnement f.eks. ikke indeholder Microsoft Defender for Office 365 Plan 2, kan du ikke se fanen **Postkasser**.

| Tab | Beskrivelse |
|:--------|:--------|
| **Undersøgelsesgraf** | Giver en visuel repræsentation af undersøgelsen. Viser enheder og viser de trusler, der blev fundet, sammen med beskeder, og om der er handlinger, der afventer godkendelse.<br/>Du kan vælge et element på grafen for at få vist flere oplysninger. Hvis du f.eks. vælger ikonet **Beviser** , kommer du til fanen **Beviser** , hvor du kan se registrerede enheder og deres domme. |
| **Beskeder** | Viser de beskeder, der er knyttet til undersøgelsen. Beskeder kan komme fra funktioner til trusselsbeskyttelse på en brugers enhed, i Office-apps, Microsoft Defender for Cloud Apps og andre Microsoft 365 Defender funktioner. <br> <br> Bemærk, at hvis du ser *beskedtypen Ikke-understøttet*, betyder det, at automatiserede undersøgelsesfunktioner ikke kan hente beskeden for at køre en automatisk undersøgelse. Du kan dog [undersøge disse beskeder manuelt](investigate-incidents.md#alerts).
| **Enheder** | Viser de enheder, der er inkluderet i undersøgelsen, sammen med afhjælpningsniveauet. (Afhjælpningsniveauer svarer til [automatiseringsniveauet for enhedsgrupper](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups)). |
| **Postkasser** |Viser postkasser, der påvirkes af registrerede trusler.  |
| **Brugere**  | Viser brugerkonti, der påvirkes af registrerede trusler. |
| **Beviser** | Viser bevismateriale, der er rejst i forbindelse med beskeder eller undersøgelser. Inkluderer domme (*Ondsindet*, *Mistænkelig*, *Ukendt* eller *Ingen trusler fundet*) og afhjælpningsstatus. |
| **Enheder** | Indeholder oplysninger om hvert analyseret objekt, herunder en dom for hver objekttype (*ondsindede*, *mistænkelige* eller *ingen trusler fundet*).|
|**Log** | Giver en kronologisk og detaljeret visning af alle de undersøgelseshandlinger, der udføres, efter at en besked blev udløst.|
| **Oversigt over ventende handlinger** | Viser elementer, der kræver godkendelse for at fortsætte. Gå til Løsningscenter ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) for at godkende ventende handlinger. |

## <a name="next-steps"></a>Næste trin

- [Få vist og administrer afhjælpningshandlinger](m365d-autoir-actions.md)
- [Få mere at vide om afhjælpningshandlinger](m365d-remediation-actions.md)
