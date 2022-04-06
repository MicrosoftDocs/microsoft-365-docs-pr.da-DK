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
description: Få mere at vide om færdigbuilte modeller i Microsoft SharePoint Syntex.
ms.openlocfilehash: 1146e4947392ce0e0848632e55f22e5b8b8d2d91
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569042"
---
# <a name="prebuilt-models-overview-in-microsoft-sharepoint-syntex"></a>Oversigt over færdigbyggede modeller i Microsoft SharePoint Syntex

Ud over [dokumentforståelse af](document-understanding-overview.md) [modeller og](form-processing-overview.md) modeller til formularbehandling indeholder SharePoint Syntex indbyggede modeller til at automatisere udtrækningen af oplysninger.

Indbyggede modeller er indbyggede til at genkende dokumenter og de strukturerede oplysninger i dokumenterne. I stedet for at skulle oprette en ny brugerdefineret model fra bunden kan du bruge en eksisterende foruddefineret model til at tilføje bestemte felter, der passer til organisationens behov. 

Foruddefinerede modeller bruger optisk tegngenkendelse (OCR) kombineret med dybtgående læringsmodeller til at identificere og udtrække foruddefinerede tekst- og datafelter, der er fælles for bestemte dokumenttyper. Du starter med at analysere en af dine filer i forhold til den indbyggede model. Derefter vælger du de registrerede felter, der giver mening for dit formål. Hvis modellen ikke registrerer de felter, du skal bruge, kan du analysere igen ved hjælp af en anden fil.

Ligesom dokumentforståelsesmodeller oprettes og administreres indbyggede modeller i [indholdscenter](create-a-content-center.md). Når den anvendes på SharePoint dokumentbibliotek, er modellen knyttet til en indholdstype og indeholder kolonner til at gemme de oplysninger, der udtrækkes. 

Efter publicering af modellen skal du bruge indholdscenteret til at anvende det på SharePoint dokumentbibliotek, du har adgang til.  

## <a name="requirements"></a>Krav

- Understøttede filformater: JPEG, PNG, BMP, TIFF og PDF (tekst integreret eller scannet).

- Understøttede sprog: Kun fakturaer på engelsk fra USA understøttes i øjeblikket. Engelske kvitteringer fra Australien, Canada, USA, Storbritannien og Indien understøttes.

- Tekst integrerede PDF-filer er bedst til at fjerne muligheden for fejl i tegnudtrækning og placering.

- For PDF og TIFF kan der behandles op til 2.000 sider.

- Filstørrelsen skal være mindre end 50 MB.

- Billeddimensionerne skal være mellem 50 x 50 pixel og 10.000 x 10.000 pixel.

- PDF-dimensioner er op til 17 x 17 tommer, svarende til juridisk eller A3 papirstørrelse eller mindre.

- Den samlede størrelse af kursusdataene er 500 sider eller mindre.

### <a name="file-limitations"></a>Filbegrænsninger

Bemærk følgende forskelle om Microsoft Office tekstbaserede filer og OCR-scannede filer (PDF, billede eller TIFF):

- Office filer: Afkortet med 64.000 tegn (når de køres mod filer i et dokumentbibliotek).

- OCR-scannede filer: Der er en grænse på 20 sider.  

## <a name="model-considerations"></a>Modelovervejelser

- Hvis to eller flere færdigbyggende modeller anvendes på det samme bibliotek, klassificeres filen ved hjælp af den model, der har det højeste tillidsresultat for gennemsnittet. De udtrukne enheder vil kun være fra den anvendte model.

- Hvis der anvendes en færdigbyggende model på et bibliotek, der har en dokumentforståelsesmodel, klassificeres filen ved hjælp af dokumentforståelsesmodellen og eventuelle uddannede udtræk for den pågældende model. Hvis der er tomme kolonner, der svarer til den indbyggede model, udfyldes kolonnerne ved hjælp af de udtrukne værdier.

- Hvis der anvendes en færdigbyggede model på et bibliotek, der har en brugerdefineret formularbehandlingsmodel, klassificeres filen ved hjælp af den indbyggede model og eventuelle registrerede udtræk for den pågældende model. Hvis der er tomme kolonner, der svarer til formularbehandlingsmodellen, udfyldes kolonnerne ved hjælp af de udtrukne værdier.

- Anvendelse af mere end én brugerdefineret formularbehandlingsmodel til et bibliotek understøttes ikke.


## <a name="see-also"></a>Se også

[Brug en indbygget model til at udtrække oplysninger fra fakturaer eller kvitteringer](prebuilt-overview.md)
 

