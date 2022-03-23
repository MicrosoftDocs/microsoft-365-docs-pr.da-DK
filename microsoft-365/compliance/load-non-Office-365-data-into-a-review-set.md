---
title: Indlæse ikke-Microsoft 365 i et korrektursæt
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
description: Få mere at vide om, hvordan du importerer Microsoft 365 data til et gennemsynssæt til analyse i Advanced eDiscovery tilfælde.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 39f91846e42bb2403c2b1faf7fd98ff3e7759182
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63588720"
---
# <a name="load-non-microsoft-365-data-into-a-review-set"></a>Indlæse ikke-Microsoft 365 i et korrektursæt

Det er ikke alle dokumenter, du skal analysere i Advanced eDiscovery, der befinder sig i Microsoft 365. Med funktionen Microsoft 365 til dataimport i Advanced eDiscovery kan du overføre dokumenter, der ikke er placeret i Microsoft 365, til et korrektursæt. I denne artikel kan du se, hvordan du kan hente dine Microsoft 365 dokumenter ind i Advanced eDiscovery til analyse.

## <a name="requirements-to-upload-non-office-365-content"></a>Krav til overførsel af ikke-Office 365 indhold

Hvis du bruger funktionen til ikke-Microsoft 365, der er beskrevet i denne artikel, skal du have følgende:

- Alle samarbejdspartnererne, som du vil knytte ikke-Microsoft 365 indhold til, skal være tildelt den korrekte licens. Du kan finde flere oplysninger [i Introduktion til Advanced eDiscovery](get-started-with-advanced-ediscovery.md#step-1-verify-and-assign-appropriate-licenses).

- En eksisterende Advanced eDiscovery sag.

- Assistenter skal føjes til sagen, før du kan uploade og knytte de ikke-Microsoft 365 til dem.

- Ikke-Microsoft 365 data skal være en filtype, der understøttes af Advanced eDiscovery. Du kan finde flere oplysninger [under Understøttede filtyper i Advanced eDiscovery](supported-filetypes-ediscovery20.md).

- Alle filer, der uploades til et gennemsynssæt, skal være placeret i mapper, hvor hver mappe er knyttet til en bestemt person, der skal gennemgå den. Navnene på disse mapper skal have følgende navngivningsformat: *alias@domainname*. Den alias@domainname skal være brugerens alias Microsoft 365 domæne. Du kan samle alle alias@domainname i en rodmappe. Rodmappen kan kun indeholde alias@domainname mapper. Løse filer i rodmappen understøttes ikke.

   Mappestrukturen for de ikke-Microsoft 365, du vil overføre, vil ligne følgende eksempel:

   - c:\nonO365\abraham.mcmahon@contoso.com
   - c:\nonO365\jewell.gordon@contoso.com
   - c:\nonO365\staci.gonzalez@contoso.com

   Hvor abraham.mcmahon@contoso.com, jewell.gordon@contoso.com og staci.gonzalez@contoso.com er SMTP-adresserne på de y-ligere, hvor det er tilfældet, skal du gøre følgende.

   ![Mappestrukturen Microsoft 365 ikke-overførte data.](../media/3f2dde84-294e-48ea-b44b-7437bd25284c.png)

- En konto, der er tildelt rollegruppen eDiscovery Manager (og tilføjet som eDiscovery-administrator).

- AzCopy v8.1-værktøjet er installeret på en computer, der har adgang til den ikke-Microsoft 365 indholdsmappestruktur. Hvis du vil installere AzCopy, [skal du se Overfør data med AzCopy v8.1 Windows](/previous-versions/azure/storage/storage-use-azcopy). Sørg for at installere AzCopy på standardplaceringen, som er **%ProgramFiles(x86)%\Microsoft SDKs\Azure\AzCopy**. Du skal bruge AzCopy v8.1. Andre versioner af AzCopy fungerer muligvis ikke ved indlæsning af ikke-Microsoft 365 data Advanced eDiscovery.


## <a name="upload-non-microsoft-365-content-into-advanced-ediscovery"></a>Upload ikke-Microsoft 365 indhold Advanced eDiscovery

1. Som eDiscovery-leder eller eDiscovery-administrator skal du åbne Advanced eDiscovery og gå til den sag, som ikke-Microsoft 365-data bliver uploadet til.  

2. Klik **på Gennemse sæt**, og vælg derefter sættet til gennemsyn for at overføre de Microsoft 365 til.  Hvis du ikke har et korrektursæt, kan du oprette et. 
 
3. Åbn korrektursættet ved enten at klikke på det eller markere det og klikke på **Åbn korrektursæt**.

4. I korrektursættet skal du klikke på Administrer korrektursæt **(pil** ned lige  efter indstillingen Handlinger), og derefter skal du klikke på **indstillingen Office 365 Data**.

5. Klik **Upload filer for** at starte guiden dataimport.

   ![Upload filer.](../media/574f4059-4146-4058-9df3-ec97cf28d7c7.png)

   Det første trin i guiden forbereder en sikker Microsoft-leveret placering Azure Storage at overføre filerne til.  Når klargøringen er fuldført, **bliver knappen Næste: Upload filer** aktive.

   ![Ikke-Microsoft 365 import: Forbered.](../media/0670a347-a578-454a-9b3d-e70ef47aec57.png)
 
5. Klik **på Næste: Upload filer**.

6. På siden **Upload filer** skal du gøre følgende:

   ![Ikke-Microsoft 365 Import: Upload filer.](../media/3ea53b5d-7f9b-4dfc-ba63-90a38c14d41a.png)

   a. I feltet **Sti til placering** af filer skal du bekræfte eller skrive placeringen af rodmappen, hvor du har gemt de ikke-Microsoft 365, du vil overføre. For placeringen af eksempelfilerne, der er vist i sektionen Før du **begynder, skal** du f.eks. skrive %BRUGERPROFIL **\\npåO365**. Når du giver den korrekte placering, sikrer du, at kommandoen AzCopy, der vises i feltet under stien, opdateres korrekt.

   b. Klik **på Kopiér til Udklipsholder** for at kopiere den kommando, der vises i feltet.

7. Start en Windows kommandoprompt, indsæt den kommando, du kopierede i forrige trin, og tryk derefter på **Enter** for at starte AzCopy-kommandoen.  Når du starter kommandoen, uploades de ikke-Microsoft 365 filer til den placering Azure Storage der blev forberedt i trin 4.

   ![Ikke-Microsoft 365 Import: AzCopy.](../media/504e2dbe-f36f-4f36-9b08-04aea85d8250.png)

   > [!NOTE]
   > Som tidligere nævnt skal du bruge AzCopy v8.1 for at kunne bruge den kommando, der er angivet på **siden Upload** filer. Hvis den medfølgende AzCopy-kommando mislykkes, skal [du se Fejlfinding af AzCopy Advanced eDiscovery](troubleshooting-azcopy.md).

8. Gå tilbage til Microsoft 365 Overholdelsescenter, og klik på **Næste: Bearbejde** filer i guiden.  Dette starter behandlingen, tekstudtrækning og indeksering af de ikke-Microsoft 365 filer, der blev overført til den Azure Storage placering.  

9. Spor status for behandling af filerne på siden Procesfiler eller på fanen **Job** ved at få vist et job med navnet Føj **ikke-Microsoft 365 data til et gennemsynssæt**.  Når jobbet er afsluttet, vil de nye filer være tilgængelige i gennemsynssættet.

   ![Ikke-Microsoft 365 Import: Procesfiler.](../media/218b1545-416a-4a9f-9b25-3b70e8508f67.png)

10. Når behandlingen er færdig, kan du lukke guiden.
