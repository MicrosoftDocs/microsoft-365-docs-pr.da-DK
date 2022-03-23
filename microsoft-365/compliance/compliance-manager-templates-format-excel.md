---
title: Formatér vurderingsskabelondata Excel til Microsoft Compliance Manager
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
description: Få mere at vide om, hvordan du Excel med data til bedømmelsesskabeloner i Microsoft Compliance Manager.
ms.openlocfilehash: 755716e67589b2f002fcaec7458f502ff945c318
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594033"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-compliance-manager"></a>Formatér vurderingsskabelondata Excel til Microsoft Compliance Manager

Når [du](compliance-manager-templates-create.md) opretter, [redigerer](compliance-manager-templates-modify.md) eller [](compliance-manager-templates-extend.md) udvider bedømmelsesskabeloner i Overholdelsesstyring, arbejder du med Excel, der bruger et bestemt format og skema. Disse specifikationer skal følges, for at filerne kan importeres korrekt.

## <a name="download-example-spreadsheet"></a>Download eksempel på regneark

Hvis du vil have vist et eksempelark, [skal du hente en eksempelfil](https://go.microsoft.com/fwlink/?linkid=2124865). Du kan bruge denne som reference til at oprette din egen fil.

Hvis du planlægger at redigere en eksisterende skabelon, skal du starte med at få vist skabelonens oplysninger i Overholdelsesstyring og downloade dens Excel fil.

## <a name="spreadsheet-format"></a>Regnearksformat

Regnearket Excel fire faner, hvoraf tre er påkrævede:

1. [Skabelon](#template-tab) (påkrævet)
2. [ControlFamily](#controlfamily-tab) (påkrævet)
3. [Handlinger](#actions-tab) (påkrævet)
4. [Dimensioner](#dimensions-tab) (valgfrit)

Når du udfylder dit regneark med skabelondata, skal regnearket indeholde fanerne i den rækkefølge, der er angivet **ovenfor,** ellers bliver dine data ikke importeret til en skabelon.

### <a name="template-tab"></a>Fanen Skabelon

Fanen **Skabelon** er påkrævet. Oplysningerne på denne fane indeholder metadata om skabelonen. Der er fire obligatoriske kolonner. Kolonnerne skal bevare rækkefølgen på arket Excel som angivet nedenfor. Du kan tilføje din egen kolonne **efter de** fire kolonner for at angive dine egne dimensioner. Hvis du gør dette, skal du sørge for at føje dem til **fanen** Dimensioner.

- **titel**: Dette er titlen på skabelonen, som skal være entydig. Den kan ikke dele et navn med en anden skabelon, du har i Overholdelsesstyring, herunder dine egne skabeloner eller en Overholdelsesstyring-skabelon.

- **produkt**: Dette er en påkrævet dimension. Få vist det produkt, der er knyttet til skabelonen.

- **certificering**: Dette er den forordning, du bruger til skabelonen.

- **inScopeServices**: Disse er de tjenester i produktet, som denne vurdering adresserer (hvis du f.eks. har angivet Office 365 som produkt, kan Microsoft Teams være en tjeneste, der er in-scope). Du kan oprette en liste over flere tjenester adskilt af to semikolon.

> [!NOTE]
> De data, du indsætter i **produkt-** **og certificeringscellerne** , kan ikke redigeres, når du har importeret regnearket for at oprette eller tilpasse en skabelon. Desuden kan en gruppe ikke indeholde to bedømmelser, der har den samme kombination **af produkt/** certificering. Du kan have flere skabeloner med den samme kombination af produkt/certificering.

### <a name="controlfamily-tab"></a>Fanen ControlFamily

Fanen **ControlFamily** er påkrævet.  De påkrævede kolonner under denne fane, som skal følge den rækkefølge, der er angivet i eksempelarket, er:

- **controlName**: Dette er kontrolelementnavnet fra certificeringen, standarden eller kontrolelementet, hvilket typisk er en slags id. Kontrolelementnavne skal være entydige i en skabelon. Du kan ikke have flere kontrolelementer med det samme navn i regnearket.

- **controlFamily**: Angiv et ord eller udtryk til kontrolelementetFamily, som identificerer en bred gruppering af kontrolelementer. Et kontrolelementFamily behøver ikke at være entydigt. den kan angives mere end én gang i et regneark. Det samme kontrolelementFamily kan også vises i flere skabeloner, selvom de ikke har nogen relation til hinanden. Hvert kontrolelementFamily skal knyttes til mindst ét kontrolelement.

- **controlTitle**: Angiv en titel til kontrolelementet. Mens controlName er en referencekode, er titlen et RTF-format, der typisk ses i reglerne.

- **controlDescription**: Angiv en beskrivelse af kontrolelementet.

- **controlActionTitle**: Dette felt relaterer dit kontrolelement til en eller flere handlinger, der er angivet af deres actionTitle. Du kan tilføje flere handlinger ved at adskille dem med to semikolon uden mellemrum. Hvert kontrolelement, du har angivet, skal indeholde mindst én eksisterende handling, og handlingen kan være defineret under  fanen Handlinger i det samme regneark, være i en anden skabelon eller oprettes af Microsoft. Forskellige kontrolelementer kan referere til den samme handling.

### <a name="actions-tab"></a>Fanen Handlinger

Fanen **Handlinger** er påkrævet.  Den angiver forbedringshandlinger, der administreres af din organisation og ikke af Microsoft, som allerede findes i Overholdelsesstyring. De kolonner, der er nødvendige for denne fane, og som skal følge den rækkefølge, der er angivet i eksempelarket, er:

- **actionTitle**: Dette er titlen på din handling og er et obligatorisk felt. Den titel, du angiver, skal være entydig. **Vigtigt**! Hvis du refererer til en handling, du ejer, som allerede findes (f.eks. i en anden skabelon), og du redigerer et af elementerne i dens efterfølgende kolonner, bliver disse ændringer overført til den samme handling i andre skabeloner.

- **implementationType**: I dette obligatoriske felt skal du oprette en liste over en af følgende tre implementeringstyper: 
  1) **Drift** – handlinger, der implementeres af personer og processer for at beskytte fortrolighed, integritet og tilgængelighed af organisationssystemer, aktiver, data og medarbejdere (eksempel: sikkerhedsindsigt og uddannelse).      
  2) **Teknisk** – handlinger, der gennemføres ved hjælp af teknologi og mekanismer, der er indeholdt i hardware-, software- eller firmwarekomponenterne i informationssystemet for at beskytte fortrolighed, integritet og tilgængelighed af organisationssystemer og data (eksempel: multifaktorgodkendelse).
  3) **Dokumentation** – handlinger, der implementeres via dokumenterede politikker og procedurer, etablerer og definerer de kontrolelementer, der er nødvendige for at beskytte fortroligheden, integriteten og tilgængeligheden af organisationssystemer, aktiver, data og medarbejdere (f.eks.: en informationssikkerhedspolitik).

- **actionScore**: I dette obligatoriske felt skal du angive en numerisk scoreværdi for handlingen. Værdien skal være et helt tal mellem 1 og 99. Må den ikke være 0, null eller tom. Jo højere tallet er, desto større er dets værdi i forhold til at forbedre din overholdelsespost. Billedet nedenfor viser, hvordan Styring af overholdelse af standarder får kontrolelementer:

  ![Kontrolelementer til styring af overholdelse af regler og standarder kontrollerer punktværdier.](../media/compliance-score-action-scoring.png "Punktværdier for kontrolelementer i Overholdelsesstyring")

- **actionDescriptionTitle**: Dette er titlen på beskrivelsen og er påkrævet. Denne beskrivelse giver dig mulighed for at have den samme handling i flere skabeloner og give en anden beskrivelse i hver skabelon.  Dette felt hjælper dig med at tydeliggøre, hvilken skabelon beskrivelsen refererer til. I de fleste tilfælde kan du placere navnet på den skabelon, du opretter, i dette felt.

- **actionDescription**: Angiv en beskrivelse af handlingen. Du kan anvende formatering, f.eks. fed tekst og links. Feltet er obligatorisk.

- **dimension-Handling Formål**: Dette er et valgfrit felt. Hvis du medtager det, skal overskriften indeholde præfikset "dimension-". Alle dimensioner, du medtager her, vil blive brugt som filtre i Overholdelsesstyring og vises på siden med oplysninger om forbedringshandlinger i Overholdelsesstyring.

### <a name="dimensions-tab"></a>Fanen Dimensioner

Fanen **Dimensioner** er valgfri. Men hvis du refererer til en dimension et andet sted, skal du angive den her, hvis den ikke findes i en skabelon, du allerede har oprettet, eller i en Microsoft-skabelon. Kolonnerne for denne fane er angivet nedenfor:

- **dimensionKey**: liste som "produkt", "certificeringer", "handlingsformål"
- **dimensionValue**: eksempler: Office 365, HIPPA, Preventative, Gordon

Når du eksporterer en eksisterende skabelon, har det eksporterede regneark fanen  Dimensioner, som viser alle de dimensioner, der bruges i skabelonen.
