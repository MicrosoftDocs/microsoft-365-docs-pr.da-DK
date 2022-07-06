---
title: Opret vurderingsskabeloner i Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Forstå, hvordan du opretter skabeloner til vurderinger i Microsoft Purview Compliance Manager. Opret og rediger skabeloner ved hjælp af en formateret Excel-fil.
ms.openlocfilehash: f7198d9b7bb9c30d388924d9c1b16a79e86bb8ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638648"
---
# <a name="create-an-assessment-template-in-microsoft-purview-compliance-manager"></a>Opret en vurderingsskabelon i Microsoft Purview Compliance Manager

Hvis du vil oprette din egen nye skabelon til brugerdefinerede vurderinger i Overholdelsesstyring, skal du bruge et særligt formateret Excel-regneark til at samle de nødvendige kontroldata. Når regnearket er fuldført, skal du importere det i Overholdelsesstyring.

Hvis du vil vide mere om formatering af dit regneark, skal du se [Formatér vurderingsskabelondata med Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>Påkrævede roller

Det er kun brugere, der har rollen Global administrator eller Overholdelsesstyring, der kan oprette og redigere skabeloner. Få mere at vide om [roller og tilladelser](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>Opret ny skabelon i Overholdelsesstyring

1. Gå til siden med **dine vurderingsskabeloner** i Overholdelsesstyring.
2. Vælg **Opret ny skabelon**. Der åbnes en skabelonoprettelsesguide.
3. Vælg den type skabelon, du vil oprette. I dette tilfælde skal du vælge **Opret en brugerdefineret skabelon** og derefter vælge **Næste**.
4. På skærmen **Upload fil** skal du vælge **Gennemse** for at finde og uploade den formaterede Excel-fil, der indeholder alle de påkrævede skabelondata.
5. Hvis der ikke er problemer med filen, vises navnet på den overførte fil. Vælg **Næste** for at fortsætte. (Hvis du har brug for at ændre filen, skal du vælge **Upload en anden fil**).
    - Hvis der er en fejl i filen, forklares det i en fejlmeddelelse øverst, hvad der er galt. Du skal rette filen og overføre den igen. Der opstår fejl, hvis regnearket er formateret forkert, eller hvis der er ugyldige oplysninger i visse felter.
6. Skærmbilledet **Gennemse og afslut** viser antallet af forbedringshandlinger og -kontrolelementer og den maksimale score for skabelonen. Når du er klar til at godkende, skal du vælge **Opret skabelon.** (Hvis du har brug for at foretage ændringer, skal du vælge **Tilbage**).
7. Det sidste skærmbillede bekræfter, at der er oprettet en ny skabelon. Vælg **Udført** for at afslutte guiden.
8. Du ankommer til den nye skabelons detaljeside, hvor du kan [oprette din vurdering](compliance-manager-assessments.md#create-assessments).
