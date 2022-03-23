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
description: Du kan oprette og bruge en skabelon til at spare tid og standardisere indstillingerne, når du tilføjer flere brugere.
ms.openlocfilehash: cacb3fc6ef2a145cbfe4c4131b2e5e38eca2c257
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589289"
---
# <a name="create-and-use-a-template-to-add-users"></a>Opret og brug en skabelon til at tilføje brugere

Du kan oprette og bruge en skabelon til at spare tid og standardisere indstillingerne, når du tilføjer flere brugere. Skabeloner er især nyttige, hvis du har brugere, der har mange fælles egenskaber, f.eks. dem, der har den samme rolle og arbejder på samme placering, og dem, der kræver den samme software. Du kan f.eks. have et team af supportteknikere, der arbejder på det samme kontor.  

## <a name="create-a-template"></a>Opret en skabelon

&mdash;Skabeloner er nemme at opretteDu >  >  kan vælge skabeloner til brugereaktive brugereBrugerskabeloner og  derefter vælge Tilføj en skabelon på rullelisten, eller du kan tilføje en ny bruger, og når du er færdig, har du mulighed for at gemme posten som en skabelon.

Når du opretter en skabelon efter at have tilføjet en bruger, gemmes de værdier, du vælger til følgende indstillinger, i skabelonen:

- Domænenavn
- Valg af adgangskodeindstillinger: Du kan vælge at oprette adgangskoder eller få dem til at genereres automatisk
- Valg af engangsadgangskode: Du kan kræve, at brugeren opretter en ny adgangskode efter første logon
- Licensplacering
- Licensvalg
- Programvalg
- Rolle
- De fleste profiloplysninger, **f.eks.** **Jobprofil**, **Afdeling, Office****, Office telefon** og **Adresse** 

Følgende oplysninger er brugerspecifikke og gemmes ikke i skabelonen:

- For- og efternavn
- Vist navn
- Brugernavn
- Valg om at sende adgangskoden i en mail, og hvem adgangskoden sendes til
- Mobiltelefonnummer

Hvis du vælger ikke at angive oplysninger for en indstilling i en sektion, vil denne værdi være tom, og denne indstilling vises ikke i skabelonen. Hvis du f.eks. lader **Stilling** være tom, når du gennemser skabelonen, og når du bruger **skabelonen, vises** Stilling slet ikke. Hvis du lader alle indstillingerne **for sektionen** Profil være tomme, **vises** Ingen angivet **i** den endelige skabelon i sektionen Profil.

Når du opretter en skabelon ved at vælge indstillingen **Tilføj en skabelon** , kan du vælge, hvilke værdier der skal fuldføres. Alt, hvad der er tomt, vises som **Ingen angivet** i skabelonen.

## <a name="use-a-template-to-add-a-user"></a>Brug en skabelon til at tilføje en bruger

Sådan bruger du en eksisterende skabelon til at tilføje en bruger:

1. Vælg BrugereAktivér brugere **i** >  **Administration**.

2. Vælg **Brugerskabeloner**, og vælg derefter en skabelon på rullelisten. Listen indeholder kun de skabeloner, du har oprettet, ikke dem, der er oprettet af andre administratorer.

   > [!NOTE]
   > Du kan også bruge en skabelon  >  til at tilføje en bruger ved at vælge Brugerskabeloner, vælge en skabelon og derefter vælge **Brug skabelon**.

3. Følg trinnene for at oprette en bruger ud fra den valgte skabelon.

   > [!NOTE]
   > Hvis du ikke har tilstrækkelige licenser til rådighed for en bruger, du tilføjer, og dine betalingsoplysninger er tilgængelige, forsøger vi at købe en anden licens ved hjælp af dine eksisterende betalingsoplysninger. Hvis dine betalingsoplysninger ikke er tilgængelige, oprettes brugeren som en bruger uden licens.

## <a name="manage-templates"></a>Administrer skabeloner

Du kan kun slette skabeloner, du ikke længere har brug for, og tilføje nye. Sådan sletter du en skabelon:

1. Vælg BrugereAktivér brugere **i** >  **Administration**.

2. Vælg **Skabeloner**, og **vælg derefter Administrer** skabeloner på rullelisten.

3. Der vises en liste over skabeloner. Du kan slette en skabelon ved at gøre et af følgende:
    - Vælg en eller flere skabeloner, og vælg derefter **Slet**. 
    - Markér de tre prik til højre for skabelonnavnet, og vælg derefter **Slet**.
    - Vælg skabelonnavnet. Når skabelondetaljerne vises i højre side af skærmen, skal du vælge **Slet skabelon**.

## <a name="related-articles"></a>Relaterede artikler

[Tilføje brugere og tildele licenser på samme tid](add-users.md)

[Fjern en tidligere medarbejder fra Microsoft 365](remove-former-employee.md)
  
