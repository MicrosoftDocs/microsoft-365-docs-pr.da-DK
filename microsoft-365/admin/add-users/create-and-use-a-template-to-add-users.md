---
title: Opret og brug en skabelon til at tilføje brugere
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
description: Du kan oprette og bruge en skabelon til at spare tid og standardisere indstillinger, når du tilføjer flere brugere i Microsoft 365 Administration.
ms.openlocfilehash: 0f0d737bcf600acb4084c5e2b85e5595c6387fee
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436985"
---
# <a name="create-and-use-a-template-to-add-users"></a>Opret og brug en skabelon til at tilføje brugere

Du kan oprette og bruge en skabelon til at spare tid og standardisere indstillinger, når du tilføjer flere brugere. Skabeloner er især nyttige, hvis du har brugere, der deler mange almindelige egenskaber, f.eks. dem, der har samme rolle og arbejder på samme placering, og dem, der har brug for den samme software. Du kan f.eks. have et team af supportteknikere, der arbejder på det samme kontor.  

## <a name="create-a-template"></a>Opret en skabelon

Det er nemt at oprette&mdash; skabeloner. Du kan vælge **BrugereAktive** >  **brugereBrugerskabeloner** >  og derefter vælge **Tilføj en skabelon** på rullelisten, eller du kan tilføje en ny bruger, og når du er færdig, kan du gemme posten som en skabelon.

Når du opretter en skabelon, når du har tilføjet en bruger, gemmes de værdier, du vælger for følgende indstillinger, i skabelonen:

- Domænenavn
- Valg af adgangskodeindstillinger: Du kan vælge at oprette adgangskoder eller få dem oprettet automatisk
- Engangsvalg af adgangskode: Du kan kræve, at brugeren opretter en ny adgangskode, når du logger på første gang
- Licensplacering
- Licensvalg
- Programvalg
- Rolle
- De fleste profiloplysninger, f.eks **. Jobprofil**, **Afdeling**, **Office**, **Office telefon** og **Adresse** 

Følgende oplysninger er brugerspecifikke og gemmes ikke i skabelonen:

- For- og efternavn
- Vist navn
- Brugernavn
- Valg af at sende adgangskoden i en mail, og hvem adgangskodemailen sendes til
- Mobiltelefonnummer

Hvis du vælger ikke at angive oplysninger om en indstilling i en sektion, er denne værdi tom, og denne indstilling vises ikke i skabelonen. Hvis du f.eks. lader **Jobtitel** være tom, vises **Jobtitel** slet ikke, når du gennemser skabelonen, og når du bruger skabelonen. Hvis du lader alle indstillingerne for **profilsektionen** være tomme, vises **ingen** angivet i den endelige skabelon i sektionen **Profil**.

Når du opretter en skabelon ved at vælge indstillingen **Tilføj en skabelon** , kan du vælge, hvilke værdier der skal udfyldes. Alt, hvad der er tomt, vises som **Ingen angivet** i skabelonen.

## <a name="use-a-template-to-add-a-user"></a>Brug en skabelon til at tilføje en bruger

Sådan bruger du en eksisterende skabelon til at tilføje en bruger:

1. Vælg **BrugereAktive** >  brugere i Administration.

2. Vælg **Brugerskabeloner**, og vælg derefter en skabelon på rullelisten. (Listen indeholder kun de skabeloner, du har oprettet, ikke dem, der er oprettet af andre administratorer).

   > [!NOTE]
   > Du kan også bruge en skabelon til at tilføje en bruger ved at vælge **BrugerskabelonerAdministrer** >  **skabeloner**, vælge en skabelon og derefter vælge **Brug skabelon**.

3. Følg trinnene for at oprette en bruger ud fra den valgte skabelon.

   > [!NOTE]
   > Hvis du ikke har tilstrækkelige licenser tilgængelige for en bruger, som du tilføjer, og dine betalingsoplysninger er tilgængelige, forsøger vi at købe en anden licens ved hjælp af dine eksisterende betalingsoplysninger. Hvis dine betalingsoplysninger ikke er tilgængelige, oprettes brugeren som en bruger uden licens.

## <a name="manage-templates"></a>Administrer skabeloner

Du kan kun slette skabeloner, du ikke længere har brug for, og tilføje nye. Sådan sletter du en skabelon:

1. Vælg **BrugereAktive** >  brugere i Administration.

2. Vælg **Skabeloner**, og vælg derefter **Administrer skabeloner** på rullelisten.

3. Der vises en liste over skabeloner. Du kan slette en skabelon ved at gøre et af følgende:
    - Vælg en eller flere skabeloner, og vælg derefter **Slet**. 
    - Vælg de tre prikker til højre for skabelonnavnet, og vælg derefter **Slet**.
    - Vælg skabelonnavnet. Når oplysningerne om skabelonen vises i højre side af skærmen, skal du vælge **Slet skabelon**.

## <a name="related-articles"></a>Relaterede artikler

[Tilføj brugere, og tildel licenser på samme tid](add-users.md)

[Fjern en tidligere medarbejder fra Microsoft 365](remove-former-employee.md)
  
