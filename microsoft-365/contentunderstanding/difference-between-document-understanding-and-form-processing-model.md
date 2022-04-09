---
title: Forskelle mellem modeller til dokumentforståelse og formularbehandling
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om vigtige forskelle mellem en model til dokumentforståelse og en formularbehandlingsmodel.
ms.openlocfilehash: a3f36adbf261ef290aada8efe1c0643ee1ce570f
ms.sourcegitcommit: 46e796c6b76a01516c48977335bbf5076ca74a06
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738410"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Forskelle mellem modeller til dokumentforståelse og formularbehandling 

Indholdsforståelse i Microsoft SharePoint Syntex giver dig mulighed for at identificere og klassificere dokumenter, der uploades til SharePoint dokumentbiblioteker, og derefter udtrække relevante oplysninger fra hver fil. Da filer f.eks. uploades til et SharePoint dokumentbibliotek, klassificeres alle filer, der er identificeret som *indkøbsordrer*, som sådanne og vises derefter i en brugerdefineret dokumentbiblioteksvisning. Derudover kan du hente bestemte oplysninger fra hver fil (f.eks *. po-nummer* og *total*) og få dem vist som en kolonne i dokumentbibliotekets visning. 

Med indholdsforståelse kan du oprette *modeller* for at identificere og udtrække de oplysninger, du har brug for. Modeller har værdi i at hjælpe med at løse forretningsproblemer i forbindelse med søgning, forretningsprocesser, overholdelse af angivne standarder og mange andre.

Du kan bruge to brugerdefinerede modeltyper:

- [Dokumentforståelsesmodeller](document-understanding-overview.md)
- [Formularbehandlingsmodeller](form-processing-overview.md)

Selvom begge modeller generelt bruges til samme formål, påvirker de nøgleforskelle, der er angivet nedenfor, hvilke du kan bruge.

> [!NOTE]
> Se [SharePoint Syntex: Introduktionsvejledning](./adoption-getstarted.md) for at få flere oplysninger om formularbehandling og eksempler på scenarieforståelse.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Struktureret i forhold til ustruktureret og semi-struktureret indhold

Brug modeller til dokumentforståelse til at identificere og udtrække data fra ustrukturerede dokumenter, f.eks. breve eller kontrakter, hvor de tekstenheder, du vil udtrække, findes i sætninger eller bestemte områder i dokumentet. Et ustruktureret dokument kan f.eks. være et kontraktfornyelsesbrev, der kan skrives på forskellige måder. Oplysningerne findes dog konsekvent i brødteksten i hvert kontraktfornyelsesdokument, f.eks. tekststrengens *startdato for Tjenesten efterfulgt af* en faktisk dato.

Brug modeller til formularbehandling til at identificere filer og udtrække data fra strukturerede eller semi-strukturerede dokumenter, f.eks. formularer eller fakturaer. Modeller til formularbehandling oplæres til at forstå layoutet af din formular fra eksempeldokumenter og lære at søge efter de data, du skal bruge til at udtrække fra lignende placeringer. Formularer har normalt et mere struktureret layout, hvor enheder befinder sig samme sted (f.eks. et cpr-nummer i en skatteformular).

> [!NOTE]
> Du skal have adgang til et indholdscenterwebsted for at kunne oprette en model til dokumentforståelse eller anvende en på et SharePoint dokumentbibliotek. 

## <a name="where-models-are-created"></a>Hvor modeller oprettes

Modeller til dokumentforståelse oprettes og administreres på et SharePoint indholdscenterwebsted. 

> [!NOTE]
> Du kan få flere oplysninger om inputdokumenter under [Krav og begrænsninger for formularbehandlingsmodel](/ai-builder/form-processing-model-requirements). 

Formularbehandlingsmodeller oprettes i Power Apps [AI Builder](/ai-builder/overview), men oprettelsen starter direkte fra et SharePoint dokumentbibliotek. Oprettelse af en formularbehandlingsmodel skal være aktiveret for et dokumentbibliotek, før en bruger kan oprette en formularbehandlingsmodel til det. Administratorer kan aktivere oprettelse af en formularbehandlingsmodel i det indhold, der forstår administratorindstillingerne. Formularbehandlingsmodeller bruger Power Automate flow til at behandle filer, når de uploades til dokumentbiblioteket.

Når du opretter en model til dokumentforståelse, opretter du en ny [SharePoint indholdstype](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), der gemmes i galleriet med SharePoint indholdstyper. Du kan også bruge eksisterende indholdstyper til at definere din model, hvis det er nødvendigt.

Når en indholdstype er oprettet og knyttet til en model, kan du også referere til denne model fra **egenskabspanelet Webstedsindholdstype** .

![Skærmbillede af panelet Webstedsindholdstype, der viser modellen til dokumentforståelse fremhævet.](../media/content-understanding/site-content-type-panel.png)

Formularbehandlingsmodeller opretter også nye [SharePoint indholdstyper](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) og gemmes også i galleriet med SharePoint indholdstyper.

## <a name="where-they-can-be-applied"></a>Hvor de kan anvendes

Du kan anvende modeller til dokumentforståelse til SharePoint dokumentbiblioteker, du har adgang til. Brug indholdscenteret til at oprette en model til dokumentforståelse og anvende den på forskellige dokumentbiblioteker. Indholdscenteret giver dig et mere centralt kontrolelement til, hvordan modeller til dokumentforståelse bruges, og hvor de anvendes. Bemærk, at disse oplysninger også skal rulles op til et indholdscenter.

Formularbehandlingsmodeller kan i øjeblikket kun anvendes på det SharePoint dokumentbibliotek, du har oprettet dem ud fra. Dette giver brugere med licens adgang til webstedet mulighed for at oprette en formularbehandlingsmodel. Bemærk, at en administrator skal aktivere formularbehandling på et SharePoint dokumentbibliotek, for at det er tilgængeligt for brugere med licens.

## <a name="comparison-of-forms-processing-and-document-understanding"></a>Sammenligning af formularbehandling og dokumentforståelse

Brug følgende tabel til at forstå, hvornår du skal bruge formularbehandling, og hvornår du skal bruge dokumentforståelse.

| Funktion | Formularbehandling | Dokumentforståelse |
| ------- | ------- | ------- |
| Modeltype – hvornår skal hver enkelt bruges? | Bruges til semi-strukturerede filformater, f.eks. PDF-filer til formularindhold, f.eks. fakturaer eller indkøbsordrer, hvor layoutet og formateringen er den samme.  | Bruges til semi-strukturerede filformater – f.eks. Office dokumenter, hvor der er forskelle i layoutet, men stadig lignende oplysninger, der skal udtrækkes. |
| Oprettelse af model | Model, der er oprettet i AI Builder med problemfri adgang fra SharePoint dokumentbibliotek.| Model, der er oprettet i SharePoint på et nyt websted, indholdscenteret. |
| Klassificeringstype| Settable classifier bruges til at give et fingerpeg til systemet om, hvilke data der skal udtrækkes.| Klassificering, der kan oplæres, med valgfrie udtrækninger ved hjælp af maskinundervisning til at tildele dokumentplacering for, hvilke data der skal udtrækkes.|
| Steder | Oplært i et enkelt dokumentbibliotek.| Kan anvendes på flere biblioteker.|
| Understøttede filtyper| Oplær på PDF-, JPG-, PNG-format, i alt 50 MB og 500 sider.| Oplær på 5-10 PDF-, Office- eller mailfiler, herunder negative eksempler.<br>Office filer afkortes med 64.000 tegn. OCR-scannede filer er begrænset til 20 sider.|
| Integrer med administrerede metadata | Nej | Ja, ved at udtrække enheder, der refererer til et konfigureret felt for administrerede metadata.|
| Integration af overholdelsesfunktion, når Microsoft Information Protection er aktiveret | Angiv publicerede opbevaringsmærkater.<br>Angiv følsomhedsmærkater kommer. | Angiv publicerede opbevaringsmærkater.<br>Angiv publicerede følsomhedsmærkater. |
| Understøttede områder| Formularbehandling er afhængig af Power Platform. Du kan få oplysninger om global tilgængelighed for Power Platform og AI Builder under [Tilgængelighed af Power Platform](https://dynamics.microsoft.com/geographic-availability/). | Tilgængelig i alle områder.|
| Transaktionsomkostninger | Bruger AI Builder-kreditter.<br>Kreditter kan købes i batches på 1 mio.<br>Kreditter på 1 mio. er inkluderet, når der købes mere end 300 SharePoint Syntex licenser.<br>Kreditter på 1 mio. tillader behandling af 2.000 filsider.<br>| NIELSEN |
| Kapacitet | Bruger Power Platform-standardmiljøet (brugerdefinerede miljøer med understøttet Dataverse-database). | Har ikke kapacitetsbegrænsninger.|
| Understøttede sprog| Understøttelse af sprog for mere [end 73 sprog](/power-platform-release-plan/2021wave2/ai-builder/form-processing-new-language-support). | Modeller fungerer på alle latinske alfabetsprog. Ud over engelsk: tysk, svensk, fransk, spansk, italiensk og portugisisk.|


## <a name="see-also"></a>Se også

[Oplæring: Øg virksomhedens ydeevne med AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Oversigt over formularbehandling](form-processing-overview.md)

[Introduktion til SharePoint Syntex](index.md)
