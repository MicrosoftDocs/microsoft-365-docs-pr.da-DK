---
title: Opret bedømmelsesskabeloner i Microsoft Compliance Manager
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
description: Forstå, hvordan du opretter skabeloner til bedømmelser i Microsoft Compliance Manager. Opret og rediger skabeloner ved hjælp af en formateret Excel fil.
ms.openlocfilehash: 1c7ccbe01d3411ace40cfe6ccdbe4fcb4d90480b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592981"
---
# <a name="create-an-assessment-template-in-microsoft-compliance-manager"></a>Opret en bedømmelsesskabelon i Microsoft Compliance Manager

Hvis du vil oprette din egen nye skabelon til brugerdefinerede bedømmelser i Overholdelsesstyring, skal du bruge et specialformateret Excel-regneark til at samle de nødvendige kontroldata. Når du er færdig med regnearket, skal du importere det i Overholdelsesstyring.

Du kan få mere at vide om formatering af dit [regneark i Formatér skabelondata til bedømmelsesvurdering med Excel](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>Påkrævede roller

Kun brugere med rollen Global administrator eller Overholdelsesstyring kan oprette og redigere skabeloner. Få mere at [vide om roller og tilladelser](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-new-template-in-compliance-manager"></a>Opret ny skabelon i Overholdelsesstyring

1. Gå til siden med **bedømmelsesskabeloner** i Overholdelsesstyring.
2. Vælg **Opret ny skabelon**. En guide til oprettelse af skabeloner åbnes.
3. Vælg den type skabelon, du vil oprette. I dette tilfælde skal du **vælge Opret en brugerdefineret skabelon** og derefter vælge **Næste**.
4. På **skærmbilledet Upload fil** skal du vælge Gennemse for  at finde og uploade din formaterede Excel fil, der indeholder alle de påkrævede skabelondata.
5. Hvis der ikke er problemer med filen, vises navnet på den overførte fil. Vælg **Næste for** at fortsætte. (Hvis du vil ændre filen, skal du vælge **Upload anden fil**).
    - Hvis der er en fejl i filen, forklarer en fejlmeddelelse øverst, hvad der er galt. Du skal rette din fil og overføre den igen. Der opstår fejl, hvis dit regneark er formateret forkert, eller hvis der er ugyldige oplysninger i visse felter.
6. **Skærmbilledet Gennemse og** afslut viser antallet af forbedringshandlinger og kontrolelementer samt det maksimale antal point for skabelonen. Når du er klar til at godkende, skal **du vælge Opret skabelon.** Hvis du vil foretage ændringer, skal du vælge **Tilbage**.
7. Det sidste skærmbillede bekræfter, at der er oprettet en ny skabelon. Vælg **Udført** for at afslutte guiden.
8. Du kommer til detaljesiden for din nye skabelon, hvor du kan [oprette din vurdering](compliance-manager-assessments.md#create-assessments).
