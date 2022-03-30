---
title: Udvid bedømmelsesskabeloner i Microsoft Compliance Manager
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
description: Få mere at vide om, hvordan du udvider bedømmelsesskabeloner i Microsoft Compliance Manager for at tilføje og ændre kontrolelementer.
ms.openlocfilehash: 4c9e4543a046e09733711500ae6162a547e3602b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598503"
---
# <a name="extend-assessment-templates-in-microsoft-compliance-manager"></a>Udvid bedømmelsesskabeloner i Microsoft Compliance Manager

Overholdelsesstyring giver mulighed for at tilføje dine egne kontrolelementer og forbedringshandlinger til en eksisterende skabelon. Denne proces kaldes at udvide en skabelon.

Hvis du vil udvide en skabelon, skal du bruge særlige instruktioner til at redigere skabelondata, afhængigt af om du udvider Microsoft-bedømmelsesskabeloner eller universelle bedømmelsesskabeloner.

## <a name="extend-microsoft-assessment-templates"></a>Udvid Microsoft-bedømmelsesskabeloner

Når du udvider en Microsoft-skabelon, f.eks. en, der er oprettet til Microsoft 365, kan den stadig modtage opdateringer, der er udgivet af Microsoft. Opdateringer kan ske, når der er ændringer i den pågældende forordning eller produkt (se [Acceptér opdateringer til bedømmelser](compliance-manager-assessments.md#accept-updates-to-assessments)).

### <a name="prepare-template-data-and-create-extension"></a>Forberede skabelondata og oprette filtypenavn

For at forberede dig skal du samle et specialformateret regneark Excel at importere de nødvendige skabelondata. Filerne Excel det samme format, der er beskrevet i [Formatér vurderingsskabelondata med Excel](compliance-manager-templates-format-excel.md), men der er særlige krav til udvidelser. Se disse yderligere punkter for at forhindre fejl:

- Dit regneark må kun indeholde de handlinger og kontrolelementer, du vil føje til bedømmelsesvurderingen.
- Regnearket må ikke indeholde nogen af de kontrolelementer eller handlinger, der allerede findes i den bedømmelsesvurdering, du vil redigere.
- Overvej at medtage "udvidelse" i skabelonens titel, f.eks. "GDPR – [dit firmanavn]-udvidelse." Det gør det nemmere at identificere dig på listen på  siden med bedømmelsesskabeloner, så de adskiller sig fra den standardskabelon, som Microsoft har leveret, eller en brugerdefineret skabelon med et lignende navn.

Når du har formateret dit regneark, skal du følge trinnene nedenfor.

1. Gå til siden med **bedømmelsesskabeloner** , og **vælg Opret ny skabelon**. En guide til oprettelse af skabeloner åbnes.

2. Vælg den type skabelon, du vil oprette. I dette tilfælde skal du vælge **Udvid en Microsoft-skabelon** og derefter **Vælg Microsoft-skabelon**.

3. Der vises en pop op-rude med valg af skabelon i højre side af skærmen med en liste over alle skabeloner og deres status for aktiv eller inaktiv. **Tælleren for aktiverede** skabeloner viser, hvor mange skabeloner der aktuelt er i brug, ud af det samlede antal, der kan bruges. Hvis du er over grænsen, vises der en meddelelse på en meddelelseslinje.

4. Der vises en pop op-rude til valg af skabelon i højre side af skærmen. Brug **Søg** til at anvende filtre til at finde den ønskede skabelon

5. Når du har fundet skabelonen, skal du vælge alternativknappen til venstre for dens navn og derefter vælge **Gem**.

6. Det næste skærmbillede viser den valgte skabelon. Hvis det er korrekt, skal du **vælge Næste**. (Hvis det ikke er korrekt, skal **du vælge Vælg en anden skabelon** for at vælge igen.)

7. På **skærmbilledet Upload fil** skal du vælge Gennemse for  at finde og uploade din formaterede Excel fil, der indeholder alle de påkrævede skabelondata.

8. Hvis der ikke er problemer med filen, vises navnet på den overførte fil på det næste skærmbillede. Vælg **Næste** for at fortsætte. Hvis du vil ændre filen, skal du **Upload en anden fil**.

    - Hvis der er et problem med filen, forklarer en fejlmeddelelse øverst, hvad der er galt. Du skal løse problemet og overføre filen igen. Der opstår fejl, hvis dit regneark er formateret forkert, eller hvis der er ugyldige oplysninger i visse felter.

9. **Skærmbilledet Gennemse og** afslut viser antallet af forbedringshandlinger og kontrolelementer samt det maksimale antal point for skabelonen. Når du er klar til at godkende, skal du **vælge Næste**. Hvis du vil foretage ændringer, skal du vælge **Upload en anden fil**.

10. Det sidste skærmbillede bekræfter, at der er oprettet en ny skabelon. Vælg **Udført** for at afslutte guiden.

11. Du kommer til detaljesiden for din nye skabelon. Herfra kan du oprette din bedømmelsesvurdering ved at vælge **Opret bedømmelsesvurdering**. Du kan finde en vejledning [under Opbygge og administrere bedømmelser](compliance-manager-assessments.md#create-assessments).

## <a name="extend-universal-assessment-templates"></a>Udvid universelle bedømmelsesskabeloner

Universelle versioner af skabeloner kan også udvides til at tilpasse dine produktspecifikke vurderinger. Du får en særlig udvidelsesskabelon, når du opretter en bedømmelsesskabelon ved hjælp af en universel skabelon, og bedømmelsesfilen har en unik kombination af produkt og certificering. Denne fil kan ændres, så den opfylder dine behov. Du kan finde en vejledning til, hvordan du redigerer skabelonen, i vejledningen [til redigering af en skabelon](compliance-manager-templates-modify.md).

Når du redigerer en universel skabelon, kan alt indhold i skabelonen ændres, men hvis du gør det, brydes nedarvningen med den overordnede skabelon. Det betyder, at microsoft ikke længere automatisk modtager opdateringer fra Microsoft, hvis den overordnede skabelon opdateres.
