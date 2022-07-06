---
title: Formatér vurderingsskabelondata i Excel til Microsoft Purview Compliance Manager
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
description: Forstå, hvordan du arbejder med Excel-data til vurderingsskabeloner i Microsoft Purview Compliance Manager.
ms.openlocfilehash: 6c94d79fec8ff59419854c34755a7402f841cfe8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631221"
---
# <a name="format-assessment-template-data-in-excel-for-microsoft-purview-compliance-manager"></a>Formatér vurderingsskabelondata i Excel til Microsoft Purview Compliance Manager

Når [du opretter](compliance-manager-templates-create.md), [ændrer](compliance-manager-templates-modify.md) eller [udvider](compliance-manager-templates-extend.md) vurderingsskabeloner i Overholdelsesstyring, skal du arbejde med Excel-regneark, der bruger et bestemt format og skema. Disse specifikationer skal følges, for at filerne kan importeres korrekt.

## <a name="download-example-spreadsheet"></a>Download eksempelregneark

Download [en eksempelfil](https://go.microsoft.com/fwlink/?linkid=2124865) for at få vist et eksempelregneark. Du kan bruge dette som reference til at oprette din egen fil.

Hvis du planlægger at redigere en eksisterende skabelon, skal du starte med at få vist skabelonens oplysninger i Overholdelsesstyring og downloade dens Excel-fil.

## <a name="spreadsheet-format"></a>Regnearksformat

Excel-regnearket indeholder fire faner, hvoraf tre er påkrævet:

1. [Skabelon](#template-tab) (påkrævet)
2. [ControlFamily](#controlfamily-tab) (påkrævet)
3. [Handlinger](#actions-tab) (påkrævet)
4. [Dimensioner](#dimensions-tab) (valgfrit)

Når du udfylder regnearket med skabelondata, skal regnearket **indeholde fanerne i den rækkefølge, der er angivet ovenfor**, ellers importeres dataene ikke til en skabelon.

### <a name="template-tab"></a>Fanen Skabelon

Fanen **Skabelon** er påkrævet. Oplysningerne under denne fane indeholder metadata om skabelonen. Der er fire påkrævede kolonner. Kolonnerne skal bevare rækkefølgen i Excel-arket som vist nedenfor. Du kan tilføje din egen kolonne **efter** de fire kolonner for at angive dine egne dimensioner. Hvis du gør dette, skal du sørge for at føje dem til fanen **Dimensioner** .

- **titel**: Dette er titlen på skabelonen, som skal være entydig. Den kan ikke dele et navn med en anden skabelon, du har i Overholdelsesstyring, herunder dine egne skabeloner eller en Skabelon for Overholdelsesstyring.

- **produkt**: Dette er en påkrævet dimension. Angiv det produkt, der er knyttet til skabelonen.

- **certificering**: Dette er den forordning, du bruger til skabelonen.

- **inScopeServices**: Dette er tjenesterne i produktet, som denne vurdering omhandler (hvis du f.eks. har angivet Office 365 som produktet, kan Microsoft Teams være en tjeneste i området). Du kan få vist flere tjenester adskilt af to semikolon.

> [!NOTE]
> De data, du indsætter i **produktet** og **certificeringscellerne** , kan ikke redigeres, når du har importeret regnearket for at oprette eller tilpasse en skabelon. En gruppe kan heller ikke indeholde to vurderinger, der har samme **kombination af produkt/certificering** . Du kan have flere skabeloner med den samme kombination af produkt/certificering.

### <a name="controlfamily-tab"></a>Fanen ControlFamily

Fanen **ControlFamily** er påkrævet.  De påkrævede kolonner under denne fane, som skal følge den rækkefølge, der er angivet i eksempelregnearket, er:

- **controlName**: Dette er navnet på kontrolelementet fra certificeringen, standarden eller forordningen, som typisk er en type id. Navne på kontrolelementer skal være entydige i en skabelon. Du kan ikke have flere kontrolelementer med det samme navn i regnearket.

- **controlFamily**: Angiv et ord eller udtryk for objektetFamily, som identificerer en bred gruppering af kontrolelementer. En controlFamily behøver ikke at være entydig. Den kan angives mere end én gang i et regneark. Det samme kontrolelementFamily kan også vises i flere skabeloner, selvom de ikke har nogen relation til hinanden. Alle controlFamily skal knyttes til mindst ét kontrolelement.

- **controlTitle**: Angiv en titel til kontrolelementet. Mens controlName er en referencekode, er titlen et RTF-format, der typisk ses i forordningerne.

- **controlDescription**: Angiv en beskrivelse af kontrolelementet.

- **controlActionTitle**: Dette felt relaterer kontrolelementet til en eller flere handlinger, der er angivet af deres actionTitle. Du kan tilføje flere handlinger ved at adskille dem med to semikolon uden mellemrum mellem dem. Hvert kontrolelement, du har angivet, skal indeholde mindst én eksisterende handling, og handlingen kan være defineret under fanen **Handlinger** i det samme regneark, være i en anden skabelon eller oprettes af Microsoft. Forskellige kontrolelementer kan referere til den samme handling.

### <a name="actions-tab"></a>Fanen Handlinger

Fanen **Handlinger** er påkrævet.  Den angiver forbedringshandlinger, der administreres af din organisation og ikke af Microsoft, som allerede findes i Overholdelsesstyring. De påkrævede kolonner til denne fane, som skal følge den rækkefølge, der er angivet i eksempelregnearket, er:

- **actionTitle**: Dette er titlen på din handling og er et obligatorisk felt. Den titel, du angiver, skal være entydig. **Vigtigt!** Hvis du refererer til en handling, du ejer, som allerede findes (f.eks. i en anden skabelon), og du ændrer nogen af dens elementer i de efterfølgende kolonner, overføres disse ændringer til den samme handling i andre skabeloner.

- **implementationType**: I dette påkrævede felt skal du angive en af følgende tre implementeringstyper: 
  1) **Operationel** – handlinger, der implementeres af personer og processer for at beskytte fortroligheden, integriteten og tilgængeligheden af organisatoriske systemer, aktiver, data og personale (f.eks. sikkerhedsbevidsthed og uddannelse).      
  2) **Teknisk** – handlinger, der udføres ved hjælp af teknologi og mekanismer, der er indeholdt i hardware-, software- eller firmwarekomponenterne i informationssystemet for at beskytte fortroligheden, integriteten og tilgængeligheden af organisatoriske systemer og data (f.eks. multifaktorgodkendelse).
  3) **Dokumentation** – handlinger, der implementeres via dokumenterede politikker og procedurer, der etablerer og definerer de kontroller, der kræves for at beskytte fortroligheden, integriteten og tilgængeligheden af organisatoriske systemer, aktiver, data og personale (f.eks. en informationssikkerhedspolitik).

- **actionScore**: I dette påkrævede felt skal du angive en numerisk scoreværdi for din handling. Værdien skal være et heltal fra 1 til 99. Den må ikke være 0, null eller tom. Jo højere tallet er, jo større er dets værdi i forhold til at forbedre din overholdelse af angivne standarder. Billedet nedenfor viser, hvordan Overholdelsesstyrings scorer styrer:

  ![Overholdelsesstyring styrer punktværdier.](../media/compliance-score-action-scoring.png "Overholdelsesstyring styrer punktværdier")

- **actionDescriptionTitle**: Dette er titlen på beskrivelsen og er påkrævet. Denne beskrivelsestitel giver dig mulighed for at have den samme handling i flere skabeloner og angive en anden beskrivelse i hver skabelon.  Dette felt hjælper dig med at præcisere, hvilken skabelon beskrivelsen refererer til. I de fleste tilfælde kan du placere navnet på den skabelon, du opretter, i dette felt.

- **actionDescription**: Angiv en beskrivelse af handlingen. Du kan anvende formatering, f.eks. fed tekst og links. Dette er et obligatorisk felt.

- **dimension-Action Formål**: Dette er et valgfrit felt. Hvis du inkluderer den, skal overskriften indeholde præfikset "dimension-". Alle dimensioner, du inkluderer her, bruges som filtre i Overholdelsesstyring og vises på siden med oplysninger om forbedringshandlinger i Overholdelsesstyring.

### <a name="dimensions-tab"></a>Fanen Dimensioner

Fanen **Dimensioner** er valgfri. Men hvis du refererer til en dimension et andet sted, skal du angive den her, hvis den ikke findes i en skabelon, du allerede har oprettet, eller i en Microsoft-skabelon. Kolonnerne til denne fane er angivet nedenfor:

- **dimensionKey**: liste som "produkt", "certificeringer", "handlingsformål"
- **dimensionValue**: eksempler: Office 365, HIPPA, Forebyggende, Detektiv

Når du eksporterer en eksisterende skabelon, har det eksporterede regneark fanen **Dimensioner** , som viser alle de dimensioner, der bruges i skabelonen.
