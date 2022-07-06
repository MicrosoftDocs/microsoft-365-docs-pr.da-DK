---
title: Udvid vurderingsskabeloner i Microsoft Purview Compliance Manager
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
description: Forstå, hvordan du udvider vurderingsskabeloner i Microsoft Purview Compliance Manager for at tilføje og redigere kontrolelementer.
ms.openlocfilehash: b4cf642e7b5a9dac47cd513251c05a802f16b77b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630449"
---
# <a name="extend-assessment-templates-in-microsoft-purview-compliance-manager"></a>Udvid vurderingsskabeloner i Microsoft Purview Compliance Manager

Overholdelsesstyring giver dig mulighed for at føje dine egne kontrolelementer og forbedringshandlinger til en eksisterende skabelon. Denne proces kaldes udvidelse af en skabelon.

Hvis du vil udvide en skabelon, skal du bruge særlige instruktioner til ændring af skabelondata, afhængigt af om du udvider Microsoft-vurderingsskabeloner eller universelle vurderingsskabeloner.

## <a name="extend-microsoft-assessment-templates"></a>Udvid Microsoft-vurderingsskabeloner

Når du udvider en Microsoft-skabelon, f.eks. en, der er oprettet til brug med Microsoft 365, kan den stadig modtage opdateringer, der er udgivet af Microsoft. Opdateringer kan ske, når der er ændringer i den relaterede regulering eller det relaterede produkt (se [Acceptér opdateringer til vurderinger](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Forbered skabelondata, og opret udvidelse

Som forberedelse skal du samle et særligt formateret Excel-regneark for at importere de nødvendige skabelondata. Excel-filerne følger det samme format, der er beskrevet i [skabelonen Formatvurdering med Excel](compliance-manager-templates-format-excel.md), men der er særlige krav til udvidelser. Se disse yderligere punkter for at hjælpe med at forhindre fejl:

- Regnearket skal kun indeholde de handlinger og kontrolelementer, du vil føje til vurderingen.
- Regnearket kan ikke indeholde nogen af de kontrolelementer eller handlinger, der allerede findes i den vurdering, du vil ændre.
- Overvej at medtage "udvidelse" i skabelonens titel, f.eks. udvidelsen "GDPR – [dit firmanavn]". Det gør det nemmere at identificere på listen på siden **med vurderingsskabeloner** i forhold til Microsoft-standardskabelonen eller en brugerdefineret skabelon med et lignende navn.

Når du har formateret regnearket, skal du følge nedenstående trin.

1. Gå til siden **Med vurderingsskabeloner** , og vælg **Opret ny skabelon**. Der åbnes en skabelonoprettelsesguide.

2. Vælg den type skabelon, du vil oprette. I dette tilfælde skal du vælge **Udvid en Microsoft-skabelon** og derefter **Vælge Microsoft-skabelon**.

3. Der vises en pop op-rude til valg af skabelon i højre side af skærmen, som viser en liste over alle skabeloner og deres status som aktiv eller inaktiv. Tælleren **med aktiverede skabeloner** viser, hvor mange skabeloner der i øjeblikket er i brug ud af det samlede antal, der er tilgængeligt. Hvis du har overskredet din grænse, vises der en meddelelse på en meddelelseslinje.

4. Der vises en pop op-rude til valg af skabelon i højre side af skærmen. Brug **Søg** til at anvende filtre til at finde den ønskede skabelon

5. Når du har fundet skabelonen, skal du vælge alternativknappen til venstre for dens navn og derefter vælge **Gem**.

6. På det næste skærmbillede vises den valgte skabelon. Hvis det er korrekt, skal du vælge **Næste**. (Hvis forkert, skal du vælge **Vælg en anden skabelon** for at vælge igen).

7. På skærmen **Upload fil** skal du vælge **Gennemse** for at finde og uploade den formaterede Excel-fil, der indeholder alle de påkrævede skabelondata.

8. Hvis der ikke er problemer med filen, vises navnet på den overførte fil på det næste skærmbillede. Vælg **Næste** for at fortsætte (hvis du har brug for at ændre filen, skal du vælge **Upload en anden fil**).

    - Hvis der er et problem med filen, forklares det i en fejlmeddelelse øverst, hvad der er galt. Du skal rette og uploade filen igen. Der opstår fejl, hvis regnearket er formateret forkert, eller hvis der er ugyldige oplysninger i visse felter.

9. Skærmbilledet **Gennemse og afslut** viser antallet af forbedringshandlinger og -kontrolelementer og den maksimale score for skabelonen. Når du er klar til at godkende, skal du vælge **Næste**. Hvis du har brug for at foretage ændringer, skal du vælge **Overfør en anden fil**.

10. Det sidste skærmbillede bekræfter, at der er oprettet en ny skabelon. Vælg **Udført** for at afslutte guiden.

11. Du ankommer til den nye skabelons detaljeside. Herfra kan du oprette din vurdering ved at vælge **Opret vurdering**. Du kan finde vejledning under [Opret og administrer vurderinger](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Udvid universelle vurderingsskabeloner

Universelle versioner af skabeloner kan også udvides til at tilpasse dine produktspecifikke vurderinger. Du modtager en særlig udvidelsesskabelon, når du opretter en vurdering ved hjælp af en universel skabelon, og vurderingen har en unik kombination af produkt og certificering. Filen kan ændres, så den opfylder dine behov. Du kan finde vejledning til, hvordan du redigerer skabelonen, i vejledningen til [ændring af en skabelon](compliance-manager-templates-modify.md).

Når du redigerer en universel skabelon, kan alt indhold i skabelonen ændres, men hvis du gør det, brydes nedarvning med den overordnede skabelon. Det betyder, at den ikke længere automatisk modtager opdateringer fra Microsoft, hvis den overordnede skabelon opdateres.
