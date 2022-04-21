---
title: Indlæs data, der ikke er Microsoft 365, i et korrektursæt
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du importerer data, der ikke er Microsoft 365, til et korrektursæt til analyse i en eDiscovery-sag (Premium).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d7167f85760d0c1cc05e130413dbcdae9e0e3973
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996850"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Indlæs data, der ikke er Microsoft 365, i et korrektursæt

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Ikke alle dokumenter, du skal analysere i Microsoft Purview eDiscovery (Premium), er placeret i Microsoft 365. Med funktionen til import af data, der ikke er Microsoft 365 i eDiscovery (Premium), kan du overføre dokumenter, der ikke er placeret i Microsoft 365, til et korrektursæt. I denne artikel kan du se, hvordan du henter dine dokumenter, der ikke er Microsoft 365, ind i eDiscovery (Premium) til analyse.

## <a name="requirements-to-upload-non-office-365-content"></a>Krav til upload af indhold, der ikke er Office 365

Brug af funktionen upload, der ikke er Microsoft 365, som beskrevet i denne artikel, kræver, at du har følgende:

- Alle tilsynsførende, som du vil knytte ikke-Microsoft 365 indhold til, skal tildeles den relevante licens. Du kan finde flere oplysninger under [Kom i gang med eDiscovery (Premium)](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- En eksisterende eDiscovery(Premium)-sag.

- Tilsynsførende skal føjes til sagen, før du kan uploade og knytte de data, der ikke er Microsoft 365, til dem.

- Data, der ikke er Microsoft 365, skal være en filtype, der understøttes af eDiscovery (Premium). Du kan finde flere oplysninger [under Understøttede filtyper i eDiscovery (Premium)](supported-filetypes-ediscovery20.md).

- Alle filer, der uploades til et korrektursæt, skal være placeret i mapper, hvor hver mappe er knyttet til en bestemt tilsynsførende. Navnene på disse mapper skal bruge følgende navngivningsformat: *alias@domainname*. Alias@domainname skal være brugerens Microsoft 365 alias og domæne. Du kan indsamle alle de alias@domainname mapper i en rodmappe. Rodmappen kan kun indeholde de alias@domainname mapper. Løse filer i rodmappen understøttes ikke.

   Mappestrukturen for de data, der ikke er Microsoft 365, som du vil overføre, svarer til følgende eksempel:

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   Hvor abraham.mcmahon@contoso.com, jewell.gordon@contoso.com og staci.gonzalez@contoso.com er SMTP-adresserne på tilsynsførende i sagen.

   ![Mappestrukturen for dataoverførsel, der ikke er Microsoft 365.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- En konto, der er tildelt til rollegruppen eDiscovery Manager (og tilføjet som eDiscovery-administrator).

- Værktøjet AzCopy v8.1, der er installeret på en computer, som har adgang til indholdsmappens struktur, der ikke er Microsoft 365. Hvis du vil installere AzCopy, skal du se [Overfør data med AzCopy v8.1 på Windows](/previous-versions/azure/storage/storage-use-azcopy). Sørg for at installere AzCopy på standardplaceringen, som er **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy**. Du skal bruge AzCopy v8.1. Andre versioner af AzCopy fungerer muligvis ikke, når der indlæses ikke-Microsoft 365 data i eDiscovery (Premium).


## <a name="upload-non-microsoft-365-content-into-ediscovery-premium"></a>Overfør indhold, der ikke er Microsoft 365, til eDiscovery (Premium)

1. Som eDiscovery Manager eller eDiscovery-administrator skal du åbne eDiscovery (Premium) og gå til den sag, hvor de ikke-Microsoft 365 data uploades til.  

2. Klik på **Gennemse sæt**, og vælg derefter det korrektursæt, du vil overføre de data, der ikke Microsoft 365 til.  Hvis du ikke har et anmeldelsessæt, kan du oprette et. 
 
3. Åbn korrektursættet ved enten at klikke på det eller vælge det og klikke på **Åbn korrektursæt**.

4. Klik på **Administrer korrektursæt** (pil ned lige efter indstillingen **Handlinger**) i korrektursættet, og klik derefter på dataindstillingen **Ikke-Office 365**.

5. Klik på **Overfør filer** for at starte guiden til import af data.

   ![Overfør filer.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   Det første trin i guiden forbereder en sikker Microsoft-leveret Azure Storage placering, hvor filerne kan uploades til.  Når forberedelsen er fuldført, aktiveres knappen **Næste: Overfør filer** .

   ![Import, der ikke er Microsoft 365: Forbered.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. Klik på **Næste: Overfør filer**.

6. Gør følgende på siden **Overfør filer** :

   ![Import, der ikke er Microsoft 365: Overfør filer.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. I feltet **Sti til filplacering** skal du bekræfte eller skrive placeringen af den rodmappe, hvor du har gemt de data, der ikke er Microsoft 365, som du vil overføre. Hvis du f.eks. vil angive placeringen af de eksempelfiler, der vises i **afsnittet Før du begynder**, skal du skrive **%USERPROFILE\Downloads\nonO365**. Hvis du angiver den korrekte placering, sikrer du, at kommandoen AzCopy, der vises i feltet under stien, opdateres korrekt.

   b. Klik på **Kopiér til Udklipsholder** for at kopiere den kommando, der vises i feltet.

7. Start en Windows-kommandoprompt, indsæt den kommando, du kopierede i det forrige trin, og tryk derefter på **Enter** for at starte kommandoen AzCopy.  Når du har startet kommandoen, uploades de filer, der ikke er Microsoft 365, til den Azure Storage placering, der blev forberedt i trin 4.

   ![Ikke-Microsoft 365 import: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Som tidligere nævnt skal du bruge AzCopy v8.1 til at bruge den kommando, der er angivet på siden **Overfør filer** . Hvis den angivne AzCopy-kommando mislykkes, skal du se [Foretag fejlfinding af AzCopy i eDiscovery (Premium)](troubleshooting-azcopy.md).

8. Gå tilbage til Microsoft Purview-overholdelsesportalen, og klik på **Næste: Behandl filer** i guiden.  Dette starter behandling, tekstudtrækning og indeksering af de filer, der ikke er Microsoft 365, som blev uploadet til den Azure Storage placering.  

9. Spor status for behandling af filerne på siden **Behandl filer** eller under fanen **Job** ved at få vist et job med navnet **Føj ikke-Microsoft 365 data til et korrektursæt**.  Når jobbet er fuldført, vil de nye filer være tilgængelige i korrektursættet.

   ![Import, der ikke er Microsoft 365: Behandl filer.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. Når behandlingen er fuldført, kan du lukke guiden.
