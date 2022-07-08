---
title: Oversigt over færdigbyggede modeller i Microsoft SharePoint Syntex
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
description: Få mere at vide om færdigbyggede modeller i Microsoft SharePoint Syntex.
ms.openlocfilehash: 47579f640e02874545177946534d81f1350104cd
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687668"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Oversigt over færdigbyggede modeller i Microsoft SharePoint Syntex

Ud over at [dokumentere forståelse af modeller](document-understanding-overview.md) og [modeller til formularbehandling](form-processing-overview.md) indeholder SharePoint Syntex også færdigbyggede modeller, der kan automatisere udtrækningen af oplysninger.

Færdigbyggede modeller er forudlært til at genkende dokumenter og strukturerede oplysninger i dokumenterne. I stedet for at skulle oprette en ny brugerdefineret model fra bunden kan du gentage en eksisterende forududdannet model for at tilføje specifikke felter, der passer til organisationens behov. 

Færdigbyggede modeller bruger optisk tegngenkendelse (OCR) kombineret med deep learning-modeller til at identificere og udtrække foruddefinerede tekst- og datafelter, der er fælles for bestemte dokumenttyper. Du starter med at analysere en af dine filer i forhold til den færdigbyggede model. Du vælger derefter de registrerede felter, der giver mening for dit formål. Hvis modellen ikke registrerer de felter, du har brug for, kan du analysere igen ved hjælp af en anden fil.

På samme måde som modeller til dokumentforståelse oprettes og administreres færdigbyggede modeller i [indholdscenteret](create-a-content-center.md). Når modellen anvendes på et SharePoint-dokumentbibliotek, er den knyttet til en indholdstype og indeholder kolonner til lagring af de oplysninger, der udtrækkes. 

Når du har publicerer din model, skal du bruge indholdscenteret til at anvende det på et hvilket som helst SharePoint-dokumentbibliotek, som du har adgang til.  

## <a name="requirements"></a>Krav

- Understøttede filformater: JPEG, PNG, BMP, TIFF og PDF (tekst integreret eller scannet).

- Understøttede sprog: I øjeblikket understøttes kun fakturaer på engelsk fra USA. Engelske salgskvitteringer fra Australien, Canada, USA, Storbritannien og Indien understøttes.

- Tekstbaserede PDF-filer er bedst til at fjerne risikoen for fejl i tegnudtrækning og placering.

- For PDF og TIFF kan op til 2.000 sider behandles.

- Filstørrelsen skal være mindre end 50 MB.

- Billeddimensioner skal være mellem 50 x 50 pixel og 10.000 x 10.000 pixel.

- PDF-dimensioner er op til 17 x 17 tommer, svarende til juridisk eller A3-papirstørrelse eller mindre.

- Den samlede størrelse af træningsdataene er 500 sider eller mindre.

### <a name="file-limitations"></a>Filbegrænsninger

Bemærk følgende forskelle i forbindelse med tekstbaserede Microsoft Office-filer og OCR-scannede filer (PDF, billede eller TIFF):

- Office-filer: Afkortes med 64.000 tegn (når de køres mod filer i et dokumentbibliotek).

- OCR-scannede filer: Der er en grænse på 20 sider.  

## <a name="model-considerations"></a>Overvejelser i forbindelse med modellen

- Hvis to eller flere færdigbyggede modeller anvendes på det samme bibliotek, klassificeres filen ved hjælp af den model, der har den højeste gennemsnitlige konfidensscore. De udtrukne enheder kommer kun fra den anvendte model.

- Hvis der anvendes en færdigbygget model på et bibliotek, der har en brugerdefineret formularbehandlingsmodel, klassificeres filen ved hjælp af den færdigbyggede model og eventuelle registrerede udtrækninger for den pågældende model. Hvis der er tomme kolonner, der svarer til formularens behandlingsmodel, udfyldes kolonnerne med disse udtrukne værdier.

- Anvendelse af mere end én brugerdefineret formularbehandlingsmodel i et bibliotek understøttes ikke.

## <a name="see-also"></a>Se også

[Brug en færdigbygget model til at udtrække oplysninger fra fakturaer eller kvitteringer](prebuilt-overview.md)
 

