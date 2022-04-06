---
title: Kom i gang med at få indføringen af Microsoft SharePoint Syntex
description: Lær at bruge og implementere SharePoint Syntex din organisation til at hjælpe dig med at strømline dine forretningsprocesser.
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: Adopt
search.appverid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 40af6061029785705d262f3b8c5134531e76885f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467637"
---
# <a name="get-started-driving-adoption-of-microsoft-sharepoint-syntex"></a>Kom i gang med at få indføringen af Microsoft SharePoint Syntex

Tænk på, at de intelligente indholdstjenester i SharePoint Syntex har tre dele:

- **Indholdsforståelse:** Opret modeller uden brug af kode til at klassificere og udtrække oplysninger fra indhold for automatisk at anvende metadata til vidensregistrering og -genbrug. Få mere at vide om [indholdsforståelse](document-understanding-overview.md).
- **Indholdsbehandling:** Automatiser registrer, ingestion og kategorisering af indhold, og strømlin indholdscentriske processer ved hjælp Power Automate. Få mere at vide [om indholdsbehandling](form-processing-overview.md).
- **Overholdelse af indhold:** Styr og administrer indhold for at forbedre sikkerhed og styring med integration Microsoft Information Protection.

Med nye AI-tjenester og -egenskaber kan du opbygge indholdsforståelse og klassificering af apps direkte i flowet til indholdsstyring ved hjælp SharePoint Syntex. Der er to forskellige måder at forstå dit indhold på. Den modeltype, du bruger, er baseret på filformat og use case.

| Formularbehandling | Dokumentforståelse |
|:-------|:-------|
| Oprettet fra dokumentbibliotek. | Oprettet i indholdscenter er en del af SharePoint Syntex. |
| Model oprettet i AI Builder. | Model oprettet i indbygget grænseflade. |
| Bruges til semistrukturerede filformater. | Bruges til ustrukturerede filformater. |
| Angiv en klassificering, der kan indstilles. | Trænbar klassificering med valgfrie udtræksorer. |
| Begrænset til et enkelt bibliotek. | Kan anvendes på flere biblioteker. |
| Træn på PDF-, JPG-, PNG-format, i alt 50 MB/500 pp. | Træn på 5-10 PDF-, Office- eller mailfiler, herunder negative eksempler. |

Du kan finde en mere komplet sammenligning af egenskaberne i [Forskellen mellem dokumentforståelse og modeller til formularbehandling](difference-between-document-understanding-and-form-processing-model.md).

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identificer pilotscenarier for virksomheder, som kan optimeres

For at forberede dig SharePoint Syntex brug i din organisation, skal du først forstå de scenarier, hvor det vil være nyttigt. "Hvorfor" hjælper med at afgøre, hvilken model der er behov for, og hvordan din organisation struktureres ud fra, hvor modellen anvendes. Her er nogle få scenarier, hvor dokumentforståelse kan hjælpe din organisation:

- **Indholdsbehandling:** Bearbejde kontrakter, arbejdsopgørelser og andre formularlignende dokumenter. formularerne, træn modellen til at forstå og tilknytte felterne, og kør derefter formularerne igennem for at indsamle dataene automatisk. Få mere at vide under [Oversigt over formularbehandling](form-processing-overview.md).
- **Fakturaanalyse:** Udtræk de relevante oplysninger fra dine fakturaer, og sørg for, at de overholder politikken, eller at de behandles korrekt.

Tænk over, hvordan SharePoint Syntex kan hjælpe din organisation:

- Automatiser forretningsprocesser
- Forbedr søgenøjagtigheden
- Administrer overensstemmelsesrisici

Når du overvejer, hvilke forretningsscenarier du skal overveje, kan du stille dig selv følgende spørgsmål:

- Løser det et reelt problem?
- Vil den blive anvendt bredt eller have bred virkning?
- Kan det fås?
- Kan du måle succes?

Prioriter scenarier, der er baseret på effekt og nem implementering. Gør dit indledende fokusområde til højere virkningsscenarier, som også nemt kan implementeres. Af prioriter scenarier med lavere påvirkning, der er svære at implementere.

Brug [eksempelscenarierne, og brug tilfælde til](adoption-scenarios.md) at give dig ideer til, hvordan du kan SharePoint Syntex i organisationen.

## <a name="identify-roles--responsibilities"></a>Identificer roller & ansvarsområder

Find ud af, hvem i organisationen der skal bygge og administrere modellerne. Der kan være følgende roller involveret.

| SharePoint/Knowledge-administrator | Power Platform-administrator | Knowledge Manager | Modelejer |
|:-------|:-------|:-------|:-------|
| AAD rolle| AAD rolle | AAD rolle | Vindere |
| Konfigurere formularbehandling | Konfigurere dataverstmiljø til formularbehandling | Indsamle use cases | Indsamle forretningsbrugssager |
| Administrere indholdscentre og -tilladelser| Købe og tildele AIB-kredit | Opret bedste fremgangsmåder, og gennemse modelanalyse | Opret og anvend modeller |

Knowledge Manager, Ejer af forretningsproces og ejer af indholdsmodel opretter eksempelmodeller og vinder adoption i organisationen.
Andre, der kan være involveret: Overholdelsesadministrator, taksonomiadministratorer.

Hvor skal de oprettes og anvendes modellerne? Er der eksisterende processer eller lagre, der kan forbedres?

- Formularbehandling: Beslut, hvilke websteder der skal behandles af en formular.
- Dokumentforståelse: Du kan oprette flere indholdscentre for forskellige forretningsområder.

## <a name="strategic-positioning"></a>Strategisk placering

Arbejd med interessenter for at sikre, at de er afstemt med strategi for brug SharePoint Syntex. Research, og giv dig følgende ressourcer som hjælp til denne placering:

- Forretningsresultater:
  - Potentielle økonomiske resultater
  - Potentielle fleksibilitetsresultater
  - Skabelonen Forretningsresultat
- Interessenter/Exec-sponsorkøb/justering
  - Business case-sæt
  - Finansielle modeller
  - Virksomhedsparathed – kultur

## <a name="identify-stakeholders"></a>Identificere interessenter

Identificer interessenterne for projektet.

|Rolle |Ansvarsområder |Afdeling |
|:-------|:-------|:--------|
| Ledelsens sponsor(e)   | Kommuniker højt syn og værdier til virksomheden   |  Ledelsen   |
| Project eller kundeemne | Overse, at hele lanceringen og implementeringsprocessen overvåges | Project administration |
| Vidensadministratorer| Opret og administrer indholdscentrene | It-afdelingen eller en anden afdeling|
| Indholdsledere og modelejere| Saml use cases, og opret og anvend modeller | En hvilken som helst afdeling|
| Vindere | Hjælp med at omvende og administrere håndtering af indvendinger | Enhver afdeling (personale) |
| Lejeradministrator | Konfigurere indstillinger på lejerniveau | It-afdeling|
| Power Platform-administrator| Konfigurere Dataverse-miljø | It-afdeling|

> [!NOTE]
> Selvom vi anbefaler, at hver af disse roller skal fuldføres under udrulningen, vil du måske opdage, at du ikke behøver dem alle for at komme i gang med din identificerede løsning.

## <a name="readiness-checklist"></a>Tjekliste for parathed

For at gøre dig klar SharePoint Syntex implementering af SharePoint Syntex skal du:

![Parat til indholdsforståelse.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planlæg sluttilstanden
    - Dokumentforståelsesmodeller er middelne, ikke slutningen.
    - Planlæg at udnytte værdien af udtrukne metadata med:
      - Søg
      - Filtrering og visning af formatering
      - Overholdelse af regler og standarder
      - Automatisering
2. Identificer
    - Forstå eksisterende informationsarkitektur og brug af funktioner til indholdsstyring.
    - Er nogen eksisterende indholdstyper gode kandidater til modeller?
    - Hvilke eksisterende processer vil blive forbedret med metadata?
3. Design
    - Design din tilgang til informationsarkitektur, administrerede metadata og indholdstyper.
    - Design processen for definition, oprettelse, administration.

## <a name="engage-your-organization"></a>Engager din organisation

1. Identificer toholdere, bekræft scenarier og udvikd projektplan.
1. Konfigurer indstillinger, og anvend licenser.
1. Start opmærksomhed og kurser – Rekrutteringsmestre.
1. Rul ud i faser.  
1. Indsam brug feedback, og iterate.
1. I takt med at planen vokser for alle AI Builder-kreditter efter behov.

## <a name="see-also"></a>Se også

[Scenarier og use cases til SharePoint Syntex](adoption-scenarios.md)

[Administrer kontrakter ved hjælp af en Microsoft 365 løsning](solution-manage-contracts-in-microsoft-365.md)
