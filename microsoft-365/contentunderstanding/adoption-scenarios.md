---
title: Scenarier og use cases til Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
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
description: Find forretningsscenarier om, hvordan du bruger SharePoint Syntex i organisationen.
ms.openlocfilehash: c5af826396d4b53dd84c36f8af599344fd5fb2ba
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475625"
---
# <a name="scenarios-and-use-cases-for-microsoft-sharepoint-syntex"></a>Scenarier og use cases til Microsoft SharePoint Syntex

Brug følgende eksempelscenarier til at spørge om, hvordan du kan bruge SharePoint Syntex i organisationen.

- [Scenarie: Spore data fra fakturaer med formularbehandling](adoption-scenarios.md#scenario-track-data-from-invoices-with-form-processing)
- [Scenarie: Spore oplysninger fra kontrakter med dokumentforståelse](adoption-scenarios.md#scenario-track-information-from-contracts-with-document-understanding)
- [Scenarie: Undgå risici med datastyring, dokumentstyring og overholdelsesprocesser baseret på SharePoint Syntex](adoption-scenarios.md#scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex)
- [Scenarie: Registrere oplysninger fra tidligere utilgængelige dokumenter](adoption-scenarios.md#scenario-capture-information-from-previously-inaccessible-documents)
- [Scenarie: Forbedr databehandling for at give indsigt og analyser](adoption-scenarios.md#scenario-improve-data-processing-to-provide-insights-and-analytics)
- [Scenarie: Automatiser ordrebehandling](adoption-scenarios.md#scenario-automate-order-processing)
- [Scenarie: Forenkle processen til fornyelse af Visa](adoption-scenarios.md#scenario-simplify-visa-renewal-process)

## <a name="scenario-track-data-from-invoices-with-form-processing"></a>Scenarie: Spore data fra fakturaer med formularbehandling

Du kan f.eks. konfigurere en proces ved hjælp SharePoint Syntex og Power Automate til at spore og overvåge fakturaer.

1. Konfigurer et bibliotek til at gemme fakturadokumenterne.
1. Træn modellen til at genkende felter i dokumenterne.
1. Udtræk de felter, du vil spore, til en liste.
1. Konfigurer et flow, der giver dig besked om bestemte begivenheder, f.eks.:
    - Der tilføjes en ny faktura.
    - En faktura har forfaldsdato.
    - En faktura er for et beløb, der er større end det automatiske godkendelsesbeløb.

![Spor og overvåg fakturaer med SharePoint Syntex og Power Automate.](../media/content-understanding/process-invoices-flow.png)

Når du automatiserer dette scenarie, kan du:

- Spar tid og penge ved automatisk at udtrække data fra fakturaerne i stedet for at gøre det manuelt.
- Reducer potentielle fejl, og sørg for bedre overholdelse ved at bruge arbejdsprocesser til at kontrollere fakturaer og give dig besked om eventuelle problemer.

## <a name="scenario-track-information-from-contracts-with-document-understanding"></a>Scenarie: Spore oplysninger fra kontrakter med dokumentforståelse

Som et andet eksempel kan du konfigurere en proces til at identificere kontrakter, som din virksomhed har med andre virksomheder eller enkeltpersoner. Opret en model til at udtrække vigtige oplysninger fra disse kontrakter, f.eks. kundenavn, gebyrer, datoer eller andre vigtige oplysninger, og tilføj oplysningerne til biblioteket som felter, du hurtigt kan få vist. Anvend en opbevaringsmærkat på dokumentbiblioteket for at sikre, at kontrakter ikke kan slettes før et bestemt tidsrum for at overholde dine virksomhedsforordninger.

1. Start i indholdscentret, og opret en ny dokumentforståelsesmodel for kontrakter.
1. Upload eksempeldokumenter for positive og negative eksempler, og kør derefter kurset for at identificere kontraktdokumenter og gennemse resultaterne.
1. Træn extractoren til at identificere felter i kontrakterne, f.eks. klientens navn, gebyr og dato, og test derefter extractoren.
1. Når modellen er færdig, skal du anvende modellen på et bibliotek, hvor du kan overføre kontrakter.
1. Anvend et opbevaringsnavn på datofeltet, så kontrakter bevares i biblioteket i den påkrævede periode.

![Spor og overvåg kontrakter med SharePoint Syntex og opbevaringsetiketter.](../media/content-understanding/process-contracts-flow.png)

Når du automatiserer dette scenarie, kan du:

- Spar tid og penge ved automatisk at udtrække data fra kontrakter i stedet for at gøre det manuelt.
- Sørg for bedre overholdelse af regler og standarder ved at bruge opbevaringsetiketter for at sikre, at kontrakterne bevares korrekt.

## <a name="scenario-avoid-risk-with-records-management-document-governance-and-compliance-processes-based-on-sharepoint-syntex"></a>Scenarie: Undgå risici med datastyring, dokumentstyring og overholdelsesprocesser baseret på SharePoint Syntex

Det er almindeligt for de fleste virksomheder at reducere risici. Du skal muligvis bruge:

- En bedre måde at levere/gennemtvinge informationsstyring på tværs af din lejer.
- For at forbedre systemet til klassificering af dokumenter, mails og andre former for kommunikation betragtes som "poster" for projekter.
- Sådan overvåges kvitteringer, kontrakter osv. for at sikre overholdelse af firmaets politikker.
- Sådan sikrer du, at projekter har al den dokumentation, der kræves for overholdelse af regler og standarder.

Konfigurer nogle processer til overholdelse af regler og SharePoint Syntex til at registrere og korrekt klassificere, overvåge og markere dokumenter og formularer, der har brug for bedre styring. Du kan være afhængig af SharePoint Syntex du automatisk klassificerer indhold i stedet for at være afhængig af slutbrugere til manuelt at mærke, eller overholdelsesteamet til manuelt at anvende styringsregler og arkivering. Og du kan aktivere en forenklet søgeoplevelse, administrere datamængde, anvende datastyring og opbevaringspolitikker, sikre overholdelse af regler og standarder samt arkiverings- og slettepraksis for bedste praksis.

Når du automatiserer dette scenarie, kan du være sikker på, at:

- Overholdelse begrænses, og risikoen reduceres.
- Taksonomi og datastyring anvendes konsekvent og præcist.
- Indholdsmængde styres.
- Medarbejderne kan nemt finde de rigtige oplysninger i den rigtige kontekst.

## <a name="scenario-capture-information-from-previously-inaccessible-documents"></a>Scenarie: Registrere oplysninger fra tidligere utilgængelige dokumenter

De fleste organisationer har store lagre af juridiske dokumenter, politikker, kontrakter, HR-dokumenter og retningslinjer for styring. Mine disse datalagre for at udtrække værdifulde oplysninger, som f.eks.: projekter, aktiviteter, temaer, personer, geografiske områder osv.

Eksempelvis skal en HR-direktør have hurtig adgang til alle HR-dokumenter – herunder CV'er, HR-politikker og andre formularer. Og de ønsker hurtigt at identificere nødvendige oplysninger fra CV'er og andre HR-relaterede dokumenter uden at skulle skulle igennem dokumenterne manuelt. De leder efter en løsning, der gør det muligt for dem hurtigt at finde de oplysninger, de skal bruge, uden at skulle gennemgå tusindvis af CV'er, HR-politikker og anden dokumentation, der kan være spredt ud over flere websteder.

Når du automatiserer dette scenarie, kan du:

- Frigør viden fra digitalt indhold.
- Klassificere HR-politikker, CV'er, salgsdokumenter, tekniske grundpapirer, kontoplaner og udtrække oplysninger.
- Find hurtigt de rigtige oplysninger eller det dokument, du leder efter.
- Få øjeblikkelig adgang til de seneste oplysninger.
- Reducer søgetider.

## <a name="scenario-improve-data-processing-to-provide-insights-and-analytics"></a>Scenarie: Forbedr databehandling for at give indsigt og analyser

For example, a pharmaceutical company could use SharePoint Syntex to extract information from FDA documents to answer questions that their leaders have. Det kan reducere den tid, det er nødvendigt at oprette disse svar på, og øge tilgængeligheden af data for at skabe mere nøjagtige svar på ledelsesspørgsmål.

Eksempelvis skal en projektleder hurtigt komme med svar på produktrelaterede spørgsmål fra mit ledelsesteam. De skal finde oplysninger og målepunkter, der er relateret til forespørgsler, i ét konsolideret dashboard. De leder efter en løsning, der udtrækker de oplysninger, de skal bruge, fra produktetiketter, produkt pjecener og andre materialer og genererer en konsolideret rapport, som de kan bruge, når de rapporterer tilbage til deres lederteam.

Når du automatiserer dette scenarie, kan du:

- Reducer tiden til at producere svar.
- Øg tilgængeligheden af data.
- Giv mere nøjagtige svar.

## <a name="scenario-automate-order-processing"></a>Scenarie: Automatiser ordrebehandling

Med SharePoint Syntex kan du reducere tiden for manuel behandling af kundeordrer. Du kan f.eks. uploade ordrer fra fax, mail eller papir til SharePoint ved hjælp af OCR-behandling og derefter udtrække metadataene fra disse ordrer, så du kan udføre dem ved hjælp af automatiserede processer.

En forsyningskædeleder ønsker f.eks. at reducere fejl forårsaget af manuel dataindtastning. De ønsker at undgå manuel gennemgang og dataindtastning af indgående kundeordrer (papir, fax eller mail) for at reducere fejl i deres virksomhedssystemer. De ønsker en løsning, der anvender AI- og maskinlæringsteknikker til at validere oplysninger om indgående ordre, udtrække kernedata og automatisk skubbe dem ind i deres ERP-system til indfrielse og afstemning.

Når du automatiserer dette scenarie, kan du sikre, at:

- Ordre- og forsendelsesnøjagtigheden øges.
- Gebyrer eller hvor der er knyttet til ordre- eller forsendelsesfejl, reduceres.
- Forsinkelser i invoicing eller fald i betalinger.
- Personaleomkostningerne reduceres.

## <a name="scenario-simplify-visa-renewal-process"></a>Scenarie: Forenkle processen til fornyelse af Visa

SharePoint Syntex kan hjælpe dig med at automatisere påmindelser og fornyelser for vigtige kontraktoplysninger. Eksempelvis skal en HR-direktør sikre, at medarbejdernes visa er opdateret og/eller fornyet til tiden. They want to give people a simple and intuitive process for updating their Visas. De har brug for en løsning, der udtrækker fornyelsesdatoer fra kontrakter og automatisk sender medarbejderne påmindelser, når deres fornyelsesdatoer nærmer sig.

Når du automatiserer dette scenarie, kan du sikre, at:

- Graderne af manglende overholdelse reduceres.
- Antallet af manuelle påmindelser reduceres.
- Antallet af fines for manglende overholdelse reduceres.

## <a name="see-also"></a>Se også

[Kom i gang med at få indføringen af SharePoint Syntex](adoption-getstarted.md)