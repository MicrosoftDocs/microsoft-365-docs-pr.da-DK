---
title: Kom i gang med at indføre Microsoft SharePoint Syntex
description: Få mere at vide om, hvordan du bruger og implementerer SharePoint Syntex i din organisation for at hjælpe dig med at strømline dine forretningsprocesser.
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
ms.openlocfilehash: 9b11c5077551aad666d565b0f3c077b3e43dc78e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937823"
---
# <a name="get-started-driving-adoption-of-microsoft-sharepoint-syntex"></a>Kom i gang med at indføre Microsoft SharePoint Syntex

Tænk på, at de intelligente indholdstjenester, der er tilgængelige i SharePoint Syntex, har tre dele:

- **Indholdsforståelse:** Opret AI-modeller uden kode for at klassificere og udtrække oplysninger fra indhold for automatisk at anvende metadata til registrering og genbrug af viden. Få mere at vide om [forståelse af indhold](document-understanding-overview.md).
- **Indholdsbehandling:** Automatiser hentning, indtagelse og kategorisering af indhold, og strømline indholdscentrerede processer ved hjælp af Power Automate. Få mere at vide om [behandling af indhold](form-processing-overview.md).
- **Indholdsoverholdelse:** Styr og administrer indhold for at forbedre sikkerheden og styringen med integration til Microsoft Purview Information Protection.

Med nye AI-tjenester og -funktioner kan du bygge indholdsforståelses- og klassificeringsapps direkte i flowet til administration af indhold ved hjælp af SharePoint Syntex. Der er to forskellige måder at forstå dit indhold på. Den modeltype, du bruger, er baseret på filformat og use case.

| Formularbehandling | Dokumentforståelse |
|:-------|:-------|
| Oprettet ud fra dokumentbiblioteket. | Oprettet i indholdscenteret, en del af SharePoint Syntex. |
| Model oprettet i AI Builder. | Model oprettet i den oprindelige grænseflade. |
| Bruges til semi-strukturerede filformater. | Bruges til ustrukturerede filformater. |
| Angivbar klassificering. | Klassificering, der kan oplæres, med valgfrie udtrækningsmaskiner. |
| Begrænset til et enkelt bibliotek. | Kan anvendes på flere biblioteker. |
| Oplær på PDF, JPG, PNG-format, i alt 50 MB/500 pp. | Oplær på 5-10 PDF-, Office- eller mailfiler, herunder negative eksempler. |

Hvis du vil have en mere komplet sammenligning af egenskaberne, skal du se [Forskel mellem modeller til dokumentforståelse og formularbehandling](difference-between-document-understanding-and-form-processing-model.md).

## <a name="identify-pilot-business-scenarios-to-optimize"></a>Identificer forretningsscenarier i pilotprojektet for at optimere

Hvis du vil forberede dig på at bruge SharePoint Syntex i din organisation, skal du først forstå de scenarier, hvor det vil være nyttigt. "Hvorfor" hjælper med at bestemme, hvilken model der skal bruges, og hvordan du strukturerer din organisation baseret på, hvor modellen skal anvendes. Her er et par scenarier, hvor dokumentforståelse kan hjælpe din organisation:

- **Indholdsbehandling:** Behandl kontrakter, arbejdsopgørelser og andre formularlignende dokumenter. Indtag formularerne, oplær modellen til at forstå og tilknytte felterne, og kør derefter formularerne igennem for automatisk at indsamle dataene. Du kan få flere oplysninger under [Oversigt over formularbehandling](form-processing-overview.md).
- **Fakturaanalyse:** Træk de relevante oplysninger ud fra dine fakturaer, og sørg for, at de overholder politikken eller behandles korrekt.

Overvej, hvordan SharePoint Syntex kan hjælpe din organisation:

- Automatiser forretningsprocesser
- Gør søgningsnøjagtigheden bedre
- Administrer overholdelsesrisiko

Når du overvejer, hvilke forretningsscenarier du skal overveje, kan du stille dig selv følgende spørgsmål:

- Er det løse et reelt problem?
- Vil det blive anvendt i vid udstrækning eller have bred indvirkning?
- Kan den hentes?
- Kan du måle succes?

Prioriter scenarier baseret på indvirkning og nem implementering. Gør dit indledende fokusområde til scenarier med større indvirkning, der også nemt kan implementeres. Prioriter scenarier med lavere indvirkning, der er svære at implementere.

Brug [eksempelscenarierne og use cases](adoption-scenarios.md) til at spørge, hvordan du kan bruge SharePoint Syntex i din organisation.

## <a name="identify-roles--responsibilities"></a>Identificer roller & ansvarsområder

Find ud af, hvem i din organisation der skal oprette og administrere modellerne. Følgende roller kan være involveret.

| SharePoint/Vidensadministrator | Administrator af Power Platform | Videnchef | Modelejer |
|:-------|:-------|:-------|:-------|
| AAD rolle| AAD rolle | AAD rolle | Champions |
| Konfigurer formularbehandling | Konfigurer Dataverse-miljøet til formularbehandling | Indsaml use cases | Indsaml use cases for virksomheder |
| Administrer indholdscentre og tilladelser| Køb og tildel AIB-kreditter | Fastlæg bedste praksis, og gennemse modelanalyser | Opret og anvend modeller |

Videnchef, Ejer af forretningsproces og Ejer af indholdsmodel opretter eksempelmodeller og mestrer indførelse i organisationen.
Andre, der kan være involveret: Overholdelsesadministrator, Taksonomiadministratorer.

Hvor bygger og anvender de modellerne? Er der eksisterende processer eller lagre, der kan forbedres?

- Formularbehandling: Beslut, hvilke websteder der skal have en formularbehandlingshandling.
- Dokumentforståelse: Du kan oprette flere indholdscentre til forskellige forretningsområder.

## <a name="strategic-positioning"></a>Strategisk positionering

Arbejd sammen med interessenter for at sikre, at de er justeret i forhold til strategien for brug af SharePoint Syntex. Søg efter og angiv følgende ressourcer som en hjælp til denne placering:

- Forretningsresultater:
  - Potentielle økonomiske resultater
  - Potentielle fleksibilitetsresultater
  - Skabelon for forretningsresultat
- Interessenter/Exec sponsor buy-in/justering
  - Business case decks
  - Økonomiske modeller
  - Virksomhedens parathed - kultur

## <a name="identify-stakeholders"></a>Identificer interessenter

Identificer interessenterne for projektet.

|Rolle |Ansvar |Institut |
|:-------|:-------|:--------|
| Executive sponsor(r)   | Kommunikerer visioner og værdier på højt niveau til virksomheden   |  Ledelse   |
| Project kundeemner | Overse hele startudførelses- og udrulningsprocessen | administration af Project |
| Vidensadministratorer| Opret og administrer indholdscentrene | It- eller anden afdeling|
| Indholdsadministratorer og modelejere| Indsaml use cases, og opret og anvend modeller | En hvilken som helst afdeling|
| Champions | Hjælp med at evangelisere og administrere håndtering af indsigelser | Alle afdelinger (personale) |
| Lejeradministrator | Konfigurer indstillinger på lejerniveau | It-afdeling|
| Power Platform-administrator| Konfigurer Dataverse-miljø | It-afdeling|

> [!NOTE]
> Selvom vi anbefaler, at hver af disse roller opfyldes i hele udrulningen, kan du opleve, at du ikke kræver, at de alle kommer i gang med din identificerede løsning.

## <a name="readiness-checklist"></a>Parathedstjekliste

Hvis du vil være klar til at implementere SharePoint Syntex, skal du gøre følgende:

![Parathed til indholdsforståelse.](../media/content-understanding/cu-adoption-readinesschecklist.png)

1. Planlæg sluttilstanden
    - Modeller til dokumentforståelse er midlerne og ikke slutningen.
    - Plan for udnyttelse af værdien af udtrukne metadata med:
      - Søg
      - Filtrering og visningsformatering
      - Overholdelse af angivne standarder
      - Automatisering
2. Identificere
    - Forstå brugen af eksisterende informationsarkitektur og indholdsstyringsfunktion.
    - Er eksisterende indholdstyper velegnede til modeller?
    - Hvilke eksisterende processer vil blive forbedret ved hjælp af metadata?
3. Design
    - Design din tilgang til informationsarkitektur, administrerede metadata og indholdstyper.
    - Design processen til definition, oprettelse og administration.

## <a name="engage-your-organization"></a>Engager din organisation

1. Identificer interessenter, bekræft scenarier, og udvikl projektplan.
1. Konfigurer indstillinger, og anvend licenser.
1. Begynd opmærksomhed og træning – rekrutér mestre.
1. Udrul i faser.  
1. Indsaml feedback, og gentage.
1. I takt med at forbruget vokser i planen for alle AI Builder-kreditter efter behov.

## <a name="see-also"></a>Se også

[Scenarier og use cases for SharePoint Syntex](adoption-scenarios.md)

[Administrer kontrakter ved hjælp af en Microsoft 365 løsning](solution-manage-contracts-in-microsoft-365.md)
