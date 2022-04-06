---
title: Oversigt over dokumentforståelse i Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.customer: intro-overview
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om dokumentforståelse i Microsoft SharePoint Syntex.
ms.openlocfilehash: c7488fcb44116f030d538b416af1f04b33382519
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507317"
---
# <a name="document-understanding-overview-in-microsoft-sharepoint-syntex"></a>Oversigt over dokumentforståelse i Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7] 

</br>

Dokumentforståelse bruger kunstig intelligens til at automatisere klassificeringen af filer og udtræk af oplysninger. Det fungerer bedst med ustrukturerede dokumenter, f.eks. breve eller kontrakter. Disse dokumenter skal have tekst, der kan identificeres ud fra udtryk eller mønstre. Den identificerede tekst angiver både den filtype, den er (klassificering), og hvad du gerne vil udtrække (dens udtræk).

> [!NOTE]
> Se SharePoint Syntex [introduktion: Introduktion for at få mere at](./adoption-getstarted.md) vide om eksempler på dokumentforståelsesscenarier.

Dokumentforståelsesmodeller oprettes og administreres i en type SharePoint, der kaldes et *indholdscenter*. Når den anvendes på SharePoint, er modellen knyttet til en indholdstype kolonner til at gemme de oplysninger, der udtrækkes. Den indholdstype, du opretter, gemmes i SharePoint indholdstype. Du kan også vælge at bruge eksisterende indholdstyper til at bruge deres skema.

> [!NOTE]
> Skrivebeskyttede eller lukkede indholdstyper kan ikke opdateres, så de kan ikke bruges i en model.

Tilføj *klassificeringer og udtræk* *til dit* dokuments forståelse af modeller for at udføre følgende handlinger: 

- Klassificeringer bruges til at identificere og klassificere dokumenter, der overføres til dokumentbiblioteket. En klassificering kan f.eks. "trænes" til at identificere alle dokumenter til *kontraktfornyelse* , der overføres til biblioteket. Indholdstypen for kontraktfornyelse defineres af dig, når du opretter din klassificering.

- Udtrækkere henter oplysninger fra disse dokumenter. For hvert dokument til fornyelse af kontrakt, der er identificeret i dit dokumentbibliotek, vises kolonnerne, der viser *tjenestens* startdato *og klient* for hvert dokument. 

Du kan bruge eksempelfiler til at træne og teste dine klassificeringer og udtræk i modellen. Eksempelfiler indeholder modelekseler på, hvad du skal lede efter, når du forsøger at identificere og udtrække data fra filer. Du ville f.eks. træne dine klassificeringer og uddrag af din kontraktfornyelse med eksempler på dokumenter til fornyelse af kontrakt, som din virksomhed arbejder sammen med. Du kan også bruge eksempelfiler til at teste effektiviteten af modellen.

Efter publicering af modellen skal du bruge indholdscenteret til at anvende det på SharePoint dokumentbibliotek, du har adgang til.  

## <a name="file-limitations"></a>Filbegrænsninger

Dokumentforståelsesmodeller bruger Optical Character Recognition-teknologi (OCR) til at scanne PDF-filer, billeder og TIFF-filer. Filer scannes, når du oplærer en model med eksempelfiler, og når du kører modellen i forhold til filer i et dokumentbibliotek.

Bemærk følgende forskelle om Microsoft Office tekstbaserede filer og OCR-scannede filer (PDF, billede eller TIFF):

- Office filer: Afkortet med 64.000 tegn (i kursus, og når der er filer i et dokumentbibliotek).

- OCR-scannede filer: Der er en grænse på 20 sider.  

### <a name="requirements"></a>Krav

OCR-behandling fungerer bedst på dokumenter, der opfylder følgende krav:

- JPG-, PNG- eller PDF-format (tekst eller scannet). Tekst integrerede PDF-filer er bedre, fordi der ikke vil være nogen fejl i tegnudtrækning og placering.

- Hvis dine PDF-filer er låst med adgangskode, skal du fjerne låsen, før du sender dem.

- Den kombinerede filstørrelse på de dokumenter, der bruges til uddannelse pr. samling, må ikke overstige 50 MB, og PDF-dokumenter må ikke have mere end 500 sider.

- For billeder skal dimensionerne være mellem 50 × 50 og 10.000 × 10.000 pixel.
   > [!NOTE]
   > Billeder, der er meget brede eller har underlige dimensioner (f.eks. plantegninger), kan blive afkortet i OCR-processen og miste nøjagtigheden.
 
- For PDF-filer skal størrelsen være højst 17 x 17 tommer, svarende til juridiske eller A3 papirstørrelser og mindre.

- Hvis det scannes fra papirdokumenter, skal scanninger være billeder i høj kvalitet.

- Skal bruge det latinske alfabet (engelske tegn).

> [!NOTE]
> AI Builder understøtter i øjeblikket ikke følgende typer inputdata for formularbehandling:<br>- Afkrydsningsfelter eller alternativknapper<br>- Signaturer<br>- Udfyldbare PDF-filer

### <a name="supported-file-types"></a>Understøttede filtyper

Dokumentforståelsesmodeller understøtter følgende filtyper:

- dokument
- docx
- eml
- heic
- heif
- htm
- html
- jpeg
- jpg
- markdown
- md
- msg
- pdf
- png
- ppt
- pptx
- rtf
- tif
- tiff
- txt
- xls
- xlsx

### <a name="supported-languages"></a>Understøttede sprog

Dokumentforståelsesmodeller understøtter alle de latinske sprog, herunder:

- English
- French
- German
- Italian
- Spanish


## <a name="see-also"></a>Se også
[Opret en klassificering](create-a-classifier.md)

[Opret en extractor](create-an-extractor.md)

[Opret et indholdscenter](create-a-content-center.md)

[Oprette en formularbehandlingsmodel](create-a-form-processing-model.md)

[Anvend en model](apply-a-model.md)   

[Forskellen mellem et dokuments forståelse og en formularbehandlingsmodel](difference-between-document-understanding-and-form-processing-model.md)
  
[Oversigt over behandling af formular](form-processing-overview.md)

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)
