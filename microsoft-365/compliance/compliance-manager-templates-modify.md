---
title: Rediger bedømmelsesskabeloner i Microsoft Compliance Manager
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
description: Få mere at vide om, hvordan du redigerer bedømmelsesskabeloner i Microsoft Compliance Manager.
ms.openlocfilehash: d409c21d31c909e7e6a59c308c7087e26ec78e24
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593588"
---
# <a name="modify-assessment-templates-in-microsoft-compliance-manager"></a>Rediger bedømmelsesskabeloner i Microsoft Compliance Manager

Når du arbejder med bedømmelser i Overholdelsesstyring, kan det være en ide at ændre en bedømmelsesskabelon, du har oprettet. Processen svarer til processen til oprettelse [af](compliance-manager-templates-create.md) skabeloner, hvor du overfører en formateret Excel fil med skabelondataene.

Der er dog oplysninger, du skal være opmærksom på, når du formaterer filen med ændringer i eksisterende skabelondata. **Vi anbefaler, at du nøje gennemgår disse instruktioner for at sikre, at du ikke overskriver nogen eksisterende data, du vil bevare.**

Hvis du vil have mere at vide om formatet af dette regneark, skal [du se Formatér dine skabelondata Excel](compliance-manager-templates-format-excel.md).

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Formatér din Excel for at redigere en eksisterende skabelon

Vælg den  **skabelon, du vil redigere** , på siden med skabeloner, du vil redigere, for at få vist siden med oplysninger. Vælg  **derefterPorter for at Excel**. En Excel fil med alle dine skabelondata downloades. Gem filen på din lokale computer.

Hvis du vil arbejde med denne fil, kan du springe til et afsnit nedenfor for hurtigt at finde de instruktioner, du skal bruge:

- [Redigere attributterne for hovedskabelonen](#edit-the-main-template-attributes)
- [Tilføje en forbedringshandling](#add-an-improvement-action)
- [Redigere oplysningerne om en forbedringshandling](#edit-an-improvement-actions-information)
- [Ændre navnet på en forbedringshandling](#change-an-improvement-actions-name)
- [Fjerne en forbedringshandling](#remove-an-improvement-action)
- [Fjerne et kontrolelement](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Redigere attributterne for hovedskabelonen

På fanen **Skabeloner** kan du redigere alt i titelkolonnen, kolonnen **inScopeServices** og i enhver anden kolonne, du har tilføjet. Du kan dog ikke redigere noget i produkt- eller **certificeringskolonnerne**.

### <a name="add-an-improvement-action"></a>Tilføje en forbedringshandling

1. Gå til **fanen** Handlinger. Tilføj dine oplysninger i de påkrævede felter i den første tomme række under dine eksisterende handlinger.
2. Gå til fanen **ControlFamily** . Find rækken, der indeholder det kontrolelement, din forbedringshandling er knyttet til. Føj din nye handling til kolonnen **controlActionTitle** i den pågældende række (husk at adskille flere handlinger i dette felt med to semikolon, ingen mellemrum imellem).
3. Gem dit regneark.

### <a name="edit-an-improvement-actions-information"></a>Redigere oplysningerne om en forbedringshandling

Du kan ændre oplysningerne om enhver forbedring med *undtagelse af titlen*. Du kan redigere en hvilken som helst celle fra kolonne B og frem, og når du importerer filen tilbage til skabelonen, indeholder forbedringshandlingerne i skabelonen nu de opdaterede data.

Du kan ikke redigere **handlingenItle** (kolonne A), fordi Overholdelsesstyring mener, at dette er en ny forbedringshandling, hvis du gør det. Hvis du vil ændre navnet på en forbedringshandling, skal du se instruktionerne lige nedenfor.

### <a name="change-an-improvement-actions-name"></a>Ændre navnet på en forbedringshandling

Hvis du vil ændre navnet på en forbedringshandling, skal du angive udtrykkeligt i regnearket, at du vil erstatte et eksisterende navn med et nyt navn. Følg disse trin:

1. På fanen **Handlinger** i regnearket skal du føje en ny kolonne til regnearket efter kolonne A.
2. I denne nye kolonne, som nu er kolonne B, skal du placere den som sin overskrift i række 1: **oldActionTitle**.
3. Kopiér indholdet i kolonne A, og indsæt dem i kolonne B. Dette placerer dine eksisterende titler for forbedringshandling, som er det, du vil ændre, i kolonne B.
4. I kolonne A skal **du handlingSitle** slette det gamle navn og erstatte det med det nye navn til forbedringshandlingen.

Bemærk, at handlingstitler, både til dine forbedringshandlinger og Microsoft-handlinger, skal være skrevet på engelsk for at kunne genkendes, når der refereres til dem i kontrolelementer.

### <a name="remove-an-improvement-action"></a>Fjerne en forbedringshandling

Hvis du vil fjerne en forbedringshandling fra en skabelon, skal du fjerne den fra hvert kontrolelement, der refererer til den. Følg trinnene nedenfor for at redigere dit regneark:

1. På fanen **ControlFamily skal** du søge efter titlen på den forbedringshandling, du vil fjerne.
2. Slet titlen på forbedringshandlingen i de celler, hvor den vises. Hvis forbedringshandlingen er den eneste handling på den pågældende række, skal du slette hele rækken (hvilket fjerner kontrolelementet).
3. På fanen **Handlinger** skal du slette rækken, der indeholder den forbedringshandling, du sletter.
4. Gem dit regneark.

Når du importerer dit regneark til skabelonen igen, fjernes din forbedringshandling fra skabelonen.

Hvis du fjerner en forbedringshandling fra en skabelon, fjerner det ikke helt forbedringshandlingen fra Overholdelsesstyring. Denne handling kan stadig refereres til af en anden skabelon.

### <a name="remove-a-control"></a>Fjerne et kontrolelement

Hvis du vil fjerne et kontrolelement, skal du redigere dit regneark ved at følge nedenstående trin og derefter importere dit regneark igen:

1. På fanen **ControlFamily skal** du finde det kontrolelement, du vil fjerne, i **kolonnen ControlName** .
2. Slet rækken for det pågældende kontrolelement.
    - Hvis dette slettede kontrolelement indeholder forbedringshandlinger, der ikke refereres til af noget andet kontrolelement, skal du fjerne disse forbedringshandlinger fra **fanen** Handlinger. Ellers får du en valideringsfejl.

3. Gem dit regneark.

Når du importerer dit regneark til skabelonen igen, fjernes dit kontrolelement fra skabelonen.

## <a name="modify-template-info-in-compliance-manager"></a>Rediger skabelonoplysninger i Overholdelsesstyring

Når filen Excel og gemmes, skal du følge disse trin.

1. Åbn siden med bedømmelsesskabelonen igen, og vælg din skabelon. På detaljesiden for din skabelon skal du vælge **Rediger skabelon for** at starte guiden til ændring.
2. På **skærmbilledet Upload fil** skal du **vælge Gennemse** for at finde og uploade Excel fil.
3. Hvis der ikke er problemer med filen, vises navnet på den overførte fil på det næste skærmbillede. Vælg **Næste** for at fortsætte. Hvis du vil ændre filen, skal du **Upload en anden fil**.
    - Hvis der er et problem med filen, forklarer en fejlmeddelelse øverst, hvad der er galt. Du skal rette din fil og overføre den igen. Der opstår fejl, hvis dit regneark er formateret forkert, eller hvis der er ugyldige oplysninger i visse felter.

4. **Skærmbilledet Gennemse og** afslut viser antallet af forbedringshandlinger og kontrolelementer samt det maksimale antal point for skabelonen. Når du er klar til at godkende, skal du **vælge Næste**.
5. Det sidste skærmbillede bekræfter, at skabelonen er blevet ændret. Vælg **Udført** for at afslutte guiden.

Skabelonen indeholder nu de ændringer, du har foretaget. Alle bedømmelser, der bruger denne ændrede skabelon, viser nu ventende opdateringer, og du skal acceptere opdateringerne af bedømmelsesvurderingerne for at afspejle de ændringer, der er foretaget i skabelonen. Få mere at [vide om opdateringer til bedømmelser](compliance-manager-assessments.md#accept-updates-to-assessments).

> [!NOTE]
> Hvis du bruger Overholdelsesstyring på et andet sprog end engelsk, vil du bemærke, at noget tekst vises på engelsk, når du eksporterer en skabelon til Excel. Titlerne på handlinger (både dine forbedringshandlinger og, hvor det er relevant, Microsoft-handlinger) skal være på engelsk for at kunne genkendes af kontrolelementer. Hvis du foretager ændringer i en handlingtitel, skal du sørge for at skrive den på engelsk, så filen importerer korrekt.
