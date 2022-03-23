---
title: Forskelle mellem dokumentforståelse og modeller til formularbehandling
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
description: Få mere at vide om de vigtigste forskelle mellem en dokumentforståelsesmodel og en formularbehandlingsmodel.
ms.openlocfilehash: 0605beb2b034343cc53e32058905870f75f811a4
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63590096"
---
# <a name="differences-between-document-understanding-and-form-processing-models"></a>Forskelle mellem dokumentforståelse og modeller til formularbehandling 

Indholdsforståelse i Microsoft SharePoint Syntex giver dig mulighed for at identificere og klassificere dokumenter, der uploades til SharePoint-dokumentbiblioteker, og udtrække relevante oplysninger fra hver enkelt fil.  Når filer eksempelvis uploades til et SharePoint-dokumentbibliotek, klassificeres alle filer, der identificeres som  indkøbsordrer, som sådan, og de vises derefter i en brugerdefineret visning af dokumentbiblioteket. Desuden kan du trække bestemte oplysninger fra hver fil (f.eks. *IP-nummer* og *Total*) og få det vist som en kolonne i visningen af dokumentbiblioteket. 

Med indholdsforståelse kan *du oprette* modeller til at identificere og udtrække de oplysninger, du har brug for. Modeller har værdi i at hjælpe med at løse forretningsmæssige problemer i forbindelse med søgning, forretningsprocesser, overholdelse af regler og standarder og mange andre.

Der er to modeltyper, du kan bruge:

- [Dokumentforståelsesmodeller](document-understanding-overview.md)
- [Modeller til behandling af formular](form-processing-overview.md)

Mens begge modeller generelt bruges til det samme formål, påvirker de væsentligste forskelle nedenfor, hvilke af dem du kan bruge.

> [!NOTE]
> Se SharePoint Syntex[: Introduktion for at få mere at](./adoption-getstarted.md) vide om eksempler på formularbehandling og dokumentforståelsesscenarier.

## <a name="structured-versus-unstructured-and-semi-structured-content"></a>Struktureret kontra ustruktureret og semistruktureret indhold

Brug dokumentforståelsesmodeller til at identificere og udtrække data fra ustrukturerede dokumenter, f.eks. breve eller kontrakter, hvor de tekstenheder, du vil udtrække, findes i sætninger eller bestemte områder i dokumentet. Et ustruktureret dokument kan f.eks. være et brev til fornyelse af kontrakt, der kan skrives på forskellige måder. Der findes dog konsekvent oplysninger i brødteksten i hvert dokument til fornyelse af kontrakt, f.eks. startdatoen for tekststrengtjenesten *efterfulgt af* en faktisk dato.

Brug modeller til behandling af formularer til at identificere filer og udtrække data fra strukturerede eller semistrukturerede dokumenter, f.eks. formularer eller fakturaer. Modeller til behandling af formular er uddannet i at forstå layoutet i din formular fra eksempeldokumenter og lærer at søge efter de data, du skal bruge til at udtrække fra lignende placeringer. Formularer har som regel et mere struktureret layout, hvor enheder er på samme placering (f.eks. et CPR-nummer i en skatteformular).

> [!NOTE]
> Du skal have adgang til et indholdscenterwebsted for at oprette en dokumentforståelsesmodel eller for at anvende et SharePoint et dokumentbibliotek. 

## <a name="where-models-are-created"></a>Hvor modeller oprettes

Dokumentforståelsesmodeller oprettes og administreres på SharePoint indholdscenterwebsted. 

> [!NOTE]
> Du kan finde flere oplysninger om inputdokumenter under [Krav og begrænsninger for formularbehandlingsmodel](/ai-builder/form-processing-model-requirements). 

Modeller til formularbehandling oprettes Power Apps [AI Builder](/ai-builder/overview), men oprettelsen starter direkte fra et SharePoint dokumentbibliotek. Et dokumentbibliotek skal have oprettelse af en formularbehandlingsmodel aktiveret, før en bruger kan oprette en formularbehandlingsmodel for den. Administratorer kan aktivere oprettelse af formularbehandlingsmodel i indholdsforståelse af administratorindstillinger. Modeller til formularbehandling bruger PowerAutomateflows til at behandle filer, når de uploades til dokumentbiblioteket.

Når du opretter en dokumentforståelsesmodel, opretter du en [ny SharePoint indholdstype](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978), der gemmes i galleriet SharePoint indholdstyper. Eller du kan bruge eksisterende indholdstyper til at definere din model, hvis det er nødvendigt.

Når en indholdstype er oprettet og knyttet til en model, kan du også referere til den pågældende model fra **egenskabspanelet Webstedsindholdstype** .

![Skærmbillede af panelet Webstedsindholdstype, der viser, at Dokumentforståelsesmodellen er fremhævet.](../media/content-understanding/site-content-type-panel.png)

Modeller til formularbehandling opretter også [SharePoint indholdstyper](https://support.microsoft.com/office/use-content-types-to-manage-content-consistently-on-a-site-48512bcb-6527-480b-b096-c03b7ec1d978) og gemmes også i galleriet SharePoint indholdstyper.

## <a name="where-they-can-be-applied"></a>Hvor de kan anvendes

Du kan anvende dokumentforståelsesmodeller SharePoint dokumentbiblioteker, du har adgang til. Brug indholdscenter til at oprette en dokumentforståelsesmodel, og anvend den på forskellige dokumentbiblioteker. Indholdscenter giver dig en mere central kontrol over, hvordan dokumentforståelsesmodeller bruges, og hvor de anvendes. Bemærk, at disse oplysninger også skal vises i et indholdscenter.

Modeller til formularbehandling kan i øjeblikket kun anvendes på det SharePoint dokumentbibliotek, hvorfra du har oprettet dem. Dette giver licenserede brugere med adgang til webstedet mulighed for at oprette en formularbehandlingsmodel. Bemærk, at en administrator skal aktivere behandling af formular på SharePoint dokumentbibliotek, for at det er tilgængeligt for brugere med licens.

## <a name="comparison-of-forms-processing-and-document-understanding"></a>Sammenligning af formularbehandling og dokumentforståelse

Brug tabellen nedenfor til at forstå, hvornår du skal bruge behandling af formularer, og hvornår du skal bruge dokumentforståelse.

| Funktion | Behandling af formularer | Dokumentforståelse |
| ------- | ------- | ------- |
| Modeltype – hvornår du skal bruge hver | Bruges til semistrukturerede filformater, f.eks. PDF-filer til formularindhold som fakturaer eller indkøbsordrer, hvor layout og formatering er ens.  | Bruges til semistrukturerede filformater – f.eks. Office dokumenter, hvor der er forskelle i layoutet, men stadig lignende oplysninger, der skal udtrækkes. |
| Oprettelse af modeller | Model oprettet i AI Builder med problemfri adgang fra SharePoint dokumentbibliotek.| Model oprettet i SharePoint på et nyt websted, indholdscenter. |
| Klassificeringstype| Angiv en klassificering, der kan indstilles, bruges til at give tip til systemet om, hvilke data der skal udtrækkes.| Trænbar klassificering med valgfrie udtræksorer ved hjælp af maskinlæring til at tildele dokumentplacering for hvilke data, der skal udtrækkes.|
| Placeringer | Trænet i et enkelt dokumentbibliotek.| Kan anvendes på flere biblioteker.|
| Understøttede filtyper| Træn på PDF-, JPG-, PNG-format, i alt 50 MB og 500 sider.| Træn på 5-10 PDF-, Office- eller mailfiler, herunder negative eksempler.<br>Office filer afkortes med 64.000 tegn. OCR-scannede filer er begrænset til 20 sider.|
| Integrer med administrerede metadata | Nej | Ja, efter undervisningsenhedsudtrækning eller henvisning til et konfigureret felt med administrerede metadata.|
| Integration af overholdelsesfunktion, når Microsoft Information Protection er aktiveret | Angiv publicerede Opbevaringsnavne.<br>Angiv følsomhedsmærkater. | Angiv publicerede Opbevaringsnavne.<br>Angiv publicerede følsomhedsmærkater. |
| Understøttede områder| Formularbehandling afhænger af Power Platform. Du kan finde oplysninger om global tilgængelighed for Power Platform og AI Builder under [Tilgængelighed af Power Platform](https://dynamics.microsoft.com/geographic-availability/). | Tilgængelig i alle områder.|
| Transaktionsomkostninger | Bruger AI Builder-kredit.<br>Kreditter kan købes i batches af 1M.<br>1M-kredit er inkluderet, når der er købt over 300 SharePoint Syntex licenser.<br>1M-kredit tillader behandling af 2.000 filsider.<br>| I/T |
| Kapacitet | Bruger standardmiljøet for Power Platform (brugerdefinerede miljøer med dataversdatabase understøttet). | Har ikke kapacitetsbegrænsninger.|
| Understøttede sprog| English <br>Kommer senere i 2022: sprog med latinsk alfabet | Modeller fungerer på alle latinske alfabetsprog. Ud over engelsk: tysk, svensk, fransk, spansk, italiensk og portugisisk.|

## <a name="see-also"></a>Se også

[Kursus: Forbedr virksomhedens ydeevne med AI Builder](/learn/paths/improve-business-performance-ai-builder/?source=learn)

[Oversigt over dokumentforståelse](document-understanding-overview.md)

[Oversigt over behandling af formular](form-processing-overview.md)

[Introduktion til SharePoint Syntex](index.md)