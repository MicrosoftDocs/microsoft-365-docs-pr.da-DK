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
ms.openlocfilehash: 385d981f1f8db22ec7d18c79734bde5a8fc3739d
ms.sourcegitcommit: 23e186b46b27a6a4863f507a52a11105afae9726
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64882478"
---
# <a name="document-understanding-overview-in-microsoft-sharepoint-syntex"></a>Oversigt over dokumentforståelse i Microsoft SharePoint Syntex


</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4CSu7]

</br>

Dokumentforståelse bruger AI-modeller (artificial intelligence) til at automatisere klassificering af filer og udtrækning af oplysninger. Den fungerer bedst sammen med ustrukturerede dokumenter, f.eks. breve eller kontrakter. Disse dokumenter skal have tekst, der kan identificeres på baggrund af udtryk eller mønstre. Den identificerede tekst angiver både den filtype, den er (dens klassificering), og hvad du gerne vil udtrække (dens udtrækninger).

> [!NOTE]
> Se [SharePoint Syntex implementering: Introduktionsvejledning](./adoption-getstarted.md) for at få flere oplysninger om eksempler på scenarier, der kan bruges til dokumentforståelse.

Modeller til dokumentforståelse oprettes og administreres i en type SharePoint websted, der kaldes et *indholdscenter*. Når modellen anvendes på et SharePoint dokumentbibliotek, er den knyttet til en indholdstype, hvor der er kolonner til lagring af de oplysninger, der udtrækkes. Den indholdstype, du opretter, gemmes i galleriet med SharePoint indholdstyper. Du kan også vælge at bruge eksisterende indholdstyper til at bruge deres skema.

> [!NOTE]
> Skrivebeskyttede eller forseglede indholdstyper kan ikke opdateres, så de kan ikke bruges i en model.

Føj *klassificeringer* og *udtrækninger* til dit dokument og forstå modeller for at udføre følgende handlinger:

- Klassificeringer bruges til at identificere og klassificere dokumenter, der uploades til dokumentbiblioteket. En klassificering kan f.eks. "oplæres" til at identificere alle *kontraktfornyelsesdokumenter* , der uploades til biblioteket. Indholdstypen for kontraktfornyelse defineres af dig, når du opretter klassificeringen.

- Udtrækker oplysninger fra disse dokumenter. For hvert kontraktfornyelsesdokument, der er identificeret i dokumentbiblioteket, vises der f.eks. kolonner, der viser *tjenestens startdato* og *klient* for hvert dokument. 

Du kan bruge eksempelfiler til at oplære og teste dine klassificeringer og udtrækninger i din model. Eksempelfiler giver dine modeleksempler på, hvad du skal søge efter, når du forsøger at identificere og udtrække data fra filer. Du kan f.eks. oplære dine klassificeringer og udtræk af kontraktfornyelse med eksempler på kontraktfornyelsesdokumenter, som din virksomhed arbejder med. Du kan også bruge eksempelfiler til at teste modellens effektivitet.

Når du har publicerer din model, kan du bruge indholdscenteret til at anvende det på alle SharePoint dokumentbibliotek, du har adgang til.  

## <a name="file-limitations"></a>Filbegrænsninger

Modeller til dokumentforståelse bruger OCR-teknologien (Optical Character Recognition) til at scanne PDF-filer, billeder og TIFF-filer. Filer scannes, når du oplærer en model med eksempelfiler, og når du kører modellen mod filer i et dokumentbibliotek.

Bemærk følgende forskelle om Microsoft Office tekstbaserede filer og OCR-scannede filer (PDF, billede eller TIFF):

- Office filer: Afkortes med 64.000 tegn (under oplæring, og når de køres mod filer i et dokumentbibliotek).

- OCR-scannede filer: Der er en grænse på 20 sider.  

### <a name="requirements"></a>Krav

OCR-behandling fungerer bedst på dokumenter, der opfylder følgende krav:

- JPG-, PNG- eller PDF-format (tekst eller scannet). Tekst-integrerede PDF-filer er bedre, fordi der ikke vil være nogen fejl i tegnudtrækning og placering.

- Hvis dine PDF-filer er låst med adgangskode, skal du fjerne låsen, før du indsender dem.

- Den kombinerede filstørrelse for de dokumenter, der bruges til oplæring pr. samling, må ikke overstige 50 MB, og PDF-dokumenter må ikke have mere end 500 sider.

- For billeder skal dimensioner være mellem 50 x 50 og 10.000 x 10.000 pixel.
   > [!NOTE]
   > Billeder, der er meget brede eller har ulige dimensioner (f.eks. plantegninger), afkortes muligvis i OCR-processen og mister nøjagtigheden.

- For PDF-filer skal dimensionerne højst være 17 x 17 tommer, svarende til juridiske eller A3-papirstørrelser og mindre.

- Hvis der scannes fra papirdokumenter, bør scanninger være billeder i høj kvalitet.

- Skal bruge det latinske alfabet (engelske tegn).

> [!NOTE]
> AI Builder understøtter i øjeblikket ikke følgende typer inputdata til formularbehandling:
>
> - Afkrydsningsfelter eller alternativknapper
> - Signaturer
> - PDF-filer, der kan udfyldes

### <a name="supported-file-types"></a>Understøttede filtyper

Modeller til dokumentforståelse understøtter følgende filtyper:

- Doc
- Docx
- Eml
- heic
- heif
- Htm
- Html
- Jpeg
- Jpg
- markdown
- Md
- Msg
- Pdf
- Png
- Ppt
- Pptx
- rtf
- Tif
- Tiff
- Txt
- Xls
- Xlsx

### <a name="supported-languages"></a>Understøttede sprog

Modeller til dokumentforståelse understøtter *alle* de latinske sprog, herunder:

- English
- French
- German
- Italian
- Spanish

## <a name="see-also"></a>Se også

[Opret en klassificering](create-a-classifier.md)

[Opret en udtrækningsmaskine](create-an-extractor.md)

[Opret et indholdscenter](create-a-content-center.md)

[Opret en formularbehandlingsmodel](create-a-form-processing-model.md)

[Anvend en model](apply-a-model.md)

[Forskel mellem en dokumentforståelse og en formularbehandlingsmodel](difference-between-document-understanding-and-form-processing-model.md)
  
[Oversigt over formularbehandling](form-processing-overview.md)

[SharePoint Syntex hjælp til handicappede](accessibility-mode.md)
