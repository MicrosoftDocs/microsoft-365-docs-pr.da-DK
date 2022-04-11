---
title: Rediger vurderingsskabeloner i Microsoft Compliance Manager
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
description: Forstå, hvordan du redigerer vurderingsskabeloner i Microsoft Compliance Manager.
ms.openlocfilehash: 589e13e766e35d38eed985a0e7bb9e21544c370d
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758525"
---
# <a name="modify-assessment-templates-in-microsoft-compliance-manager"></a>Rediger vurderingsskabeloner i Microsoft Compliance Manager

Når du arbejder med vurderinger i Overholdelsesstyring, kan det være en god idé at ændre en vurderingsskabelon, som du har oprettet. Processen ligner processen til [oprettelse af skabelonen](compliance-manager-templates-create.md), da du uploader en formateret Excel fil med dine skabelondata.

Der er dog oplysninger, du skal være opmærksom på, når du formaterer filen med ændringer af eksisterende skabelondata. **Vi anbefaler, at du gennemser disse instruktioner omhyggeligt for at sikre, at du ikke overskriver eksisterende data, som du vil bevare.**

Hvis du vil vide mere om formatet af dette regneark, skal du se [Formatér dine skabelondata med Excel](compliance-manager-templates-format-excel.md).

## <a name="format-your-excel-file-to-modify-an-existing-template"></a>Formatér din Excel fil for at redigere en eksisterende skabelon

Vælg den skabelon, du vil ændre, på siden med **vurderingsskabeloner** , som viser siden med oplysninger. Vælg derefter **Eksportér til Excel**. Der downloades en Excel fil med alle dine skabelondata. Gem filen på din lokale computer.

Hvis du vil arbejde med denne fil, skal du gå til et afsnit nedenfor for hurtigt at finde de instruktioner, du skal bruge:

- [Rediger hovedskabelonattributterne](#edit-the-main-template-attributes)
- [Tilføj en forbedringshandling](#add-an-improvement-action)
- [Rediger oplysninger om en forbedringshandling](#edit-an-improvement-actions-information)
- [Rediger navnet på en forbedringshandling](#change-an-improvement-actions-name)
- [Fjern en forbedringshandling](#remove-an-improvement-action)
- [Fjern et kontrolelement](#remove-a-control)

### <a name="edit-the-main-template-attributes"></a>Rediger hovedskabelonattributterne

Under fanen **Skabeloner** kan du redigere alt i **titelkolonnen** , kolonnen **inScopeServices** og i en hvilken som helst anden kolonne, du har tilføjet. Du kan dog ikke redigere noget i **produkt** - eller **certificeringskolonnerne** .

### <a name="add-an-improvement-action"></a>Tilføj en forbedringshandling

1. Gå til fanen **Handlinger** . Tilføj dine oplysninger i de påkrævede felter i den første tomme række under dine eksisterende handlinger.
2. Gå til fanen **ControlFamily** . Find den række, der indeholder det kontrolelement, som din forbedringshandling er knyttet til. Føj den nye handling til kolonnen **controlActionTitle** i den pågældende række (husk at adskille flere handlinger i dette felt med to semikolon, ingen mellemrum imellem).
3. Gem regnearket.

### <a name="edit-an-improvement-actions-information"></a>Rediger oplysninger om en forbedringshandling

Du kan ændre oplysningerne for en forbedringshandling *med undtagelse af dens titel*. Du kan redigere en hvilken som helst celle fra kolonner B videre, og når du importerer filen tilbage til skabelonen, indeholder forbedringshandlingerne i skabelonen nu de opdaterede data.

Du kan ikke redigere **actionTitle** (kolonne A), fordi Overholdelsesstyring anser dette for at være en ny forbedringshandling, hvis du gør det. Hvis du vil ændre navnet på en forbedringshandling, skal du se vejledningen umiddelbart nedenfor.

### <a name="change-an-improvement-actions-name"></a>Rediger navnet på en forbedringshandling

Hvis du vil ændre navnet på en forbedringshandling, skal du eksplicit angive i regnearket, at du erstatter et eksisterende navn med et nyt navn. Følg disse trin:

1. Føj en ny kolonne til regnearket efter kolonne A under fanen **Handlinger** i regnearket.
2. I denne nye kolonne, som nu er kolonne B, skal du placere den som overskrift i række 1: **oldActionTitle**.
3. Kopiér indholdet af kolonne A, og indsæt dem i kolonne B. Dette placerer dine eksisterende titler på forbedringshandlinger, som du vil ændre, i kolonne B.
4. I kolonne A **, actionTitle**, skal du slette det gamle navn og erstatte det med det nye navn til forbedringshandlingen.

Bemærk, at handlingstitler, både til dine forbedringshandlinger og til Microsoft-handlinger, skal skrives på engelsk for at kunne genkendes, når der refereres til dem i kontrolelementer.

### <a name="remove-an-improvement-action"></a>Fjern en forbedringshandling

Hvis du vil fjerne en forbedringshandling fra en skabelon, skal du fjerne den fra alle kontrolelementer, der refererer til den. Følg nedenstående trin for at redigere regnearket:

1. Søg efter titlen på den forbedringshandling, du vil fjerne, under fanen **ControlFamily** .
2. Slet forbedringshandlingens titel i de celler, hvor den vises. Hvis forbedringshandlingen er den eneste handling på den pågældende række, skal du slette hele rækken (hvilket fjerner kontrolelementet).
3. Slet den række, der indeholder den forbedringshandling, du sletter, under fanen **Handlinger** .
4. Gem regnearket.

Når du importerer regnearket tilbage til skabelonen, fjernes forbedringshandlingen fra skabelonen.

Hvis du fjerner en forbedringshandling fra en skabelon, fjernes forbedringshandlingen ikke fuldstændigt fra Overholdelsesstyring. En anden skabelon kan stadig referere til denne handling.

### <a name="remove-a-control"></a>Fjern et kontrolelement

Hvis du vil fjerne et kontrolelement, skal du ændre regnearket ved at følge nedenstående trin og derefter importere regnearket igen:

1. Find det kontrolelement, du vil fjerne, i kolonnen **controlName** under fanen **ControlFamily**.
2. Slet rækken for det pågældende kontrolelement.
    - Hvis dette slettede kontrolelement indeholder forbedringshandlinger, der ikke refereres til af andre kontrolelementer, skal du fjerne disse forbedringshandlinger fra fanen **Handlinger** . Ellers får du vist en valideringsfejl.

3. Gem regnearket.

Når du importerer regnearket tilbage til skabelonen, fjernes kontrolelementet fra skabelonen.

## <a name="modify-template-info-in-compliance-manager"></a>Rediger skabelonoplysninger i Overholdelsesstyring

Når din Excel fil er fuldført og gemt, skal du følge disse trin.

1. Åbn siden med vurderingsskabelonen igen, og vælg skabelonen. Vælg **Rediger skabelon** på siden med oplysninger om skabelonen for at starte ændringsguiden.
2. På skærmen **Upload fil** skal du vælge **Gennemse** for at finde og uploade din Excel fil.
3. Hvis der ikke er problemer med filen, vises navnet på den overførte fil på det næste skærmbillede. Vælg **Næste** for at fortsætte (hvis du har brug for at ændre filen, skal du vælge **Upload en anden fil**).
    - Hvis der er et problem med filen, forklares det i en fejlmeddelelse øverst, hvad der er galt. Du skal rette filen og overføre den igen. Der opstår fejl, hvis regnearket er formateret forkert, eller hvis der er ugyldige oplysninger i visse felter.

4. Skærmbilledet **Gennemse og afslut** viser antallet af forbedringshandlinger og -kontrolelementer og den maksimale score for skabelonen. Når du er klar til at godkende, skal du vælge **Næste**.
5. Det sidste skærmbillede bekræfter, at skabelonen er blevet ændret. Vælg **Udført** for at afslutte guiden.

Skabelonen indeholder nu de ændringer, du har foretaget. Alle vurderinger, der bruger denne ændrede skabelon, viser nu ventende opdateringer, og du skal acceptere opdateringerne af vurderingerne, så de afspejler de ændringer, der er foretaget i skabelonen. Få mere at vide om [opdateringer til vurderinger](compliance-manager-assessments.md#accept-updates-to-assessments).

> [!NOTE]
> Hvis du bruger Overholdelsesstyring på et andet sprog end engelsk, vil du bemærke, at der vises noget tekst på engelsk, når du eksporterer en skabelon til Excel. Titlerne på handlinger (både dine forbedringshandlinger og, hvor det er relevant, Microsoft-handlinger), skal være på engelsk for at kunne genkendes af kontrolelementer. Hvis du foretager ændringer i en handlingstitel, skal du skrive den på engelsk, så filen importeres korrekt.
