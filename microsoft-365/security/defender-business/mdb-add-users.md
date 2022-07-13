---
title: Tilføj brugere, og tildel licenser i Microsoft Defender til virksomheder
description: Tilføj brugere, og tildel Defender for Business-licenser for at beskytte deres enheder
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.openlocfilehash: 7d1715352ab1a1392b06cae5bfc3ee81196bf3e2
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772722"
---
# <a name="add-users-and-assign-licenses-in-microsoft-defender-for-business"></a>Tilføj brugere, og tildel licenser i Microsoft Defender til virksomheder

Så snart du har tilmeldt dig Defender for Business, er dit første skridt at tilføje brugere og tildele licenser. I denne artikel beskrives det, hvordan du tilføjer brugere og inkluderer næste trin.

## <a name="add-users-and-assign-licenses"></a>Tilføj brugere, og tildel licenser

> [!IMPORTANT]
> Du skal være global administrator for at kunne udføre denne opgave.  Den person, der har tilmeldt sig din virksomhed til Microsoft 365 eller Defender for Business, er som standard global administrator.

1. Gå til Microsoft 365 Administration på , og log på[https://admin.microsoft.com](https://admin.microsoft.com).

2. Gå til **Brugere** > **Aktive brugere**, og vælg derefter **Tilføj en bruger**.

3. I ruden **Konfigurer de grundlæggende** oplysninger skal du udfylde de grundlæggende brugeroplysninger og derefter vælge **Næste**.

   - **Navn**: Udfyld for- og efternavn, vist navn og brugernavn.
   - **Domæne** Vælg domænet for brugerens konto. Hvis brugerens brugernavn f.eks. er `Pat`, og domænet er `contoso.com`, logger vedkommende på ved hjælp `pat@contoso.com`af .
   - **Adgangskodeindstillinger**: Vælg, om du vil bruge den automatisk genererede adgangskode, eller om du vil oprette din egen stærke adgangskode til brugeren. Brugeren skal ændre sin adgangskode efter 90 dage. Eller du kan vælge indstillingen **Kræv, at denne bruger ændrer sin adgangskode, første gang vedkommende logger på**. Du kan også vælge, om du vil sende brugerens adgangskode i en mail, når brugeren tilføjes.

4. På siden **Tildel produktlicenser** skal du vælge Defender for Business (eller Microsoft 365 Business Premium). Vælg derefter **Næste**. 

   Hvis du ikke har nogen tilgængelige licenser, kan du stadig tilføje en bruger og købe yderligere licenser. Du kan få flere oplysninger om tilføjelse af brugere under [Tilføj brugere og tildel licenser på samme tid](../../admin/add-users/add-users.md).

5. På siden **Valgfrie indstillinger** kan du udvide **Profiloplysninger** og udfylde detaljer, f.eks. brugerens titel, afdeling, placering osv. Vælg derefter **Næste**.

6. Gennemse detaljerne på siden **Gennemse og afslut** , og vælg derefter **Afslut tilføjelse** for at tilføje brugeren. Hvis du har brug for at foretage ændringer, skal du vælge **Tilbage** for at gå tilbage til en forrige side.

## <a name="next-steps"></a>Næste trin

- [Besøg Microsoft 365 Defender-portalen](mdb-get-started.md)
- [Brug installationsguiden i Defender for Business](mdb-use-wizard.md).