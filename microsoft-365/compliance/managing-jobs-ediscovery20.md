---
title: Administrer job i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Advanced eDiscovery-job kan hjælpe dig med at holde styr på status for langsigtede processer, der er relateret til at udføre Advanced eDiscovery opgaver.
ms.openlocfilehash: 484f492ea56f6e75d3f5144dd41128c2cedfc914
ms.sourcegitcommit: 57211e8082a3429017ad33fe0e6bd9af203bb7ab
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/09/2022
ms.locfileid: "63588717"
---
# <a name="manage-jobs-in-advanced-ediscovery"></a>Administrer job i Advanced eDiscovery

Her er en liste over de job (som typisk er lange processer), der registreres på fanen Jobs for en sag  i Advanced eDiscovery. Disse job udløses af brugerhandlinger, når du bruger og administrerer sager.

| Jobtype           | Beskrivelse     |
| :----------------- | :----------     |
|Føje data til et korrektursæt | En bruger føjer en samling til et gennemsynssæt. Dette job består af to underjob: </br>• **Eksportér** – Der genereres en liste over elementer i samlingen. </br>• **Ingestion & Indeksering** – Elementerne i samlingen, der svarer til søgeforespørgslen, kopieres til en Azure Storage-placering (i en proces kaldet *ingestion*), og derefter bliver elementerne i Azure Storage-placeringen indekseret igen. Dette nye indeks bruges til at forespørge og analysere elementer i datasættet. </br></br>Få mere at vide under [Føj søgeresultater til et korrektursæt](add-data-to-review-set.md). |
|Føje data til et andet korrektursæt | En bruger tilføjer dokumenter fra ét korrektursæt til et andet korrektursæt i samme tilfælde. Få mere at vide under [Føj data til et korrektursæt fra et andet korrektursæt](add-data-to-review-set-from-another-review-set.md).|
|Tilføjelse af Microsoft 365 data i et korrektursæt | En bruger overfører ikke-Microsoft 365 til et korrektursæt. Dataene indekseres også under denne proces. Eksempelvis uploades filer fra en lokal filserver eller en klientcomputer til et korrektursæt. Få mere at vide under [Indlæs ikke-Microsoft 365 data i et korrektursæt](load-non-office-365-data-into-a-review-set.md).| 
|Tilføjelse af afhjælpede data i et korrektursæt | Data med behandlingsfejl afhjælpes og indlæses tilbage i et gennemsynssæt. Du kan finde flere oplysninger under:</br>• [Fejlafhjulning under behandling af data](error-remediation-when-processing-data-in-advanced-ediscovery.md)</br>• [Afhjælpning af fejl ved et enkelt element](single-item-error-remediation.md)| 
|Sammenligning af indlæsningssæt | En bruger ser på forskellene mellem forskellige indlæsningssæt i et korrektursæt. Et indlæsningssæt er en forekomst af at føje data til et korrektursæt. Hvis du f.eks. føjer resultaterne af to forskellige søgninger til det samme korrektursæt, repræsenterer hver især et indlæsningssæt. |
|Samtalebetrædende|Når en bruger føjer resultaterne af en søgning til et *samtalegennemsynssæt, genoprettes* chatsamtaler (også kaldet samtaler med tråde) i tjenester som Microsoft Teams i en PDF-fil. Dette job udløses også, når en bruger klikker på Handlingsruden **> Opret** PDF-filer til samtale i et gennemsynssæt. Du kan finde flere [oplysninger i Gennemse samtaler i Advanced eDiscovery](conversation-review-sets.md).
|Konvertere dokumenter, der er redigeret igen, til PDF|Når en bruger anmærker et dokument i et korrektursæt og redigerer en del af det, kan brugeren vælge at konvertere det redigerede dokument til en PDF-fil. Dette sikrer, at den redigerede del ikke er synlig, hvis dokumentet eksporteres til præsentation. Få mere at vide under [Få vist dokumenter i et gennemsynssæt](view-documents-in-review-set.md). |
|Anslå søgeresultater | Når en bruger opretter og kører eller kører en kladdesamling igen, søger søgeværktøjet efter elementer, der svarer til søgeforespørgslen, og forbereder et estimat, der omfatter antallet og den samlede størrelse af alle elementer via søgningen, og antallet af datakilder, der søges efter.  Få mere at vide under [Indsaml data for en sag](collecting-data-for-ediscovery.md). | 
|Forberedelse af data til eksport | En bruger eksporterer dokumenter fra et gennemsynssæt. Når eksporten er fuldført, kan de hente de eksporterede data til en lokal computer. Få mere at vide under [Eksportér sagsdata](exporting-data-ediscover20.md). | 
|Forberedelse til fejlløsning |Når en bruger vælger en fil og opretter en ny fejlløsning i visningen Fejl under fanen Behandler for en  sag, er det første trin i processen at overføre den fil, der indeholder behandlingsfejlen, til en Azure Storage-placering i Microsoft-skyen. Dette job registrerer status for overførselsprocessen. Du kan finde flere oplysninger om arbejdsprocessen til afhjælpning af fejl under [Afhjælpning af fejl under behandling af data](error-remediation-when-processing-data-in-advanced-ediscovery.md). | 
|Forberede forhåndsvisning af søgning | Når en bruger opretter og kører en ny kladdesamling (eller kører en eksisterende kladdesamling igen), forbereder søgeværktøjet et eksempel på et undersæt af elementer (der svarer til søgeforespørgslen), som kan vises som eksempel. Visning af søgeresultater hjælper dig med at bestemme effektiviteten af søgningen.  Få mere at vide under [Indsaml data for en sag](collecting-data-for-ediscovery.md#view-search-results-and-statistics). | 
|Indeksering af data for oversigter igen | Når du føjer en leder til en sag, bliver alle delvist indekserede elementer i den valgte datakilder igen omgivet af en proces, der kaldes Avanceret *indeksering*. Dette job udløses også, når du klikker  på Opdater indeks på  fanen Behandler for en sag, og når du opdaterer indekset for en bestemt seer på pop op-siden med egenskaber for afholdsegenskaber. Du kan få mere at vide [under Avanceret indeksering af data, der er til hjælp for brugere, der er under indsamling](indexing-custodian-data.md).
|Kørende analyser | En bruger analyserer data i et gennemsynssæt ved at køre Advanced eDiscovery analyseværktøjer såsom nær registrering af dubletter, mailtrådeanalyse og temaanalyse. Få mere at vide under [Analysér data i et gennemsynssæt](analyzing-data-in-review-set.md). | 
|Mærkning af dokumenter | Dette job udløses, når en bruger klikker på **Start mærkning af job** i panelet  Mærkning, når du gennemser dokumenter i et korrektursæt. En bruger kan starte dette job efter mærkning af dokumenter i et korrektursæt og derefter markere dem flere i panelet vis dokument. Få mere at vide under [Tag dokumenter i et korrektursæt](tagging-documents.md). | 
|||

## <a name="job-status"></a>Jobstatus

I følgende tabel beskrives de forskellige statustilstande for job.

| Status           | Beskrivelse     |
| :----------------- | :----------     |
| Indsendt | Der blev oprettet et nyt job.  Den dato og det klokkeslæt, hvor jobbet blev sendt, vises i **kolonnen** Oprettet under **fanen** Job. |
| Indsendelse mislykkedes | Jobafsendelsen mislykkedes.  Du skal forsøge at køre den handling, der udløste jobbet, igen. |
| I gang | Jobbet er i gang, og du kan overvåge jobbets status under **fanen** Job. |
| Vellykket | Jobbet blev fuldført. Den dato og det klokkeslæt, hvor jobbet blev afsluttet, vises **i kolonnen** Fuldført **på fanen Job** . |
| Delvist vellykket | Jobbet blev gennemført. Denne status returneres typisk, når jobbet ikke fandt nogen delvist indekserede data (også kaldet *ikke-indekserede data*) i nogle af de datakilder, der er ved at blive vist.  |
| Mislykkedes | Jobbet mislykkedes.  Du skal forsøge at køre den handling, der udløste jobbet, igen. Hvis jobbet mislykkes endnu en gang, anbefaler vi, at du kontakter Microsoft Support og leverer supportoplysninger fra jobbet. |
|||
