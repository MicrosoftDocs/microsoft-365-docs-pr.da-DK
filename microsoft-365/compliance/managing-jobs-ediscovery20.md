---
title: Administrer job i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: eDiscovery-job (Premium) hjælper dig med at spore status for langvarige processer, der er relateret til udførelse af forskellige eDiscovery-opgaver (Premium).
ms.openlocfilehash: 9be48325e3103e8f4e349c32cc559db36e42a05e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639726"
---
# <a name="manage-jobs-in-ediscovery-premium"></a>Administrer job i eDiscovery (Premium)

Her er en liste over de job (som typisk er langvarige processer), der spores under fanen **Job** i en sag i Microsoft Purview eDiscovery (Premium). Disse job udløses af brugerhandlinger, når du bruger og administrerer sager.

|Jobtype|Beskrivelse|
|---|---|
|Tilføjelse af data til et korrektursæt|En bruger føjer en samling til et korrektursæt. Dette job består af to underjob: <ul><li>**Export** – Der genereres en liste over elementer i samlingen.</li><li>**Indtagelse & indeksering** – De elementer i samlingen, der svarer til søgeforespørgslen, kopieres til en Azure Storage-placering (i en proces, der kaldes *indtagelse*), og derefter genindekseres disse elementer på Azure Storage-placeringen. Dette nye indeks bruges til at forespørge på og analysere elementer i datasættet.</li><ul> <p> Du kan finde flere oplysninger under [Føj søgeresultater til et korrektursæt](add-data-to-review-set.md).|
|Tilføjelse af data til et andet korrektursæt|En bruger føjer dokumenter fra ét korrektursæt til et andet korrektursæt i samme tilfælde. Du kan få flere oplysninger under [Føj data til et korrektursæt fra et andet korrektursæt](add-data-to-review-set-from-another-review-set.md).|
|Tilføjelse af data, der ikke er Microsoft 365, til et anmeldelsessæt|En bruger uploader data, der ikke er Microsoft 365, til et anmeldelsessæt. Dataene indekseres også under denne proces. Filer fra en filserver i det lokale miljø eller en klientcomputer uploades f.eks. til et korrektursæt. Du kan få flere oplysninger under [Indlæs ikke-Microsoft 365-data i et korrektursæt](load-non-office-365-data-into-a-review-set.md).|
|Tilføjelse af afhjælpede data til et korrektursæt|Data med behandlingsfejl afhjælpes og indlæses i et korrektursæt igen. Du kan finde flere oplysninger under: <ul><li>[Fejlafhjælpning under behandling af data](error-remediation-when-processing-data-in-advanced-ediscovery.md)</li><li>[Afhjælpning af fejl med et enkelt element](single-item-error-remediation.md)</li></ul>|
|Sammenligning af indlæsningssæt|En bruger kigger på forskellene mellem forskellige indlæsningssæt i et korrektursæt. Et indlæsningssæt er en forekomst af tilføjelse af data til et korrektursæt. Hvis du f.eks. føjer resultaterne af to forskellige søgninger til det samme korrektursæt, repræsenterer hver enkelt et indlæsningssæt.|
|Genopbygning af samtale|Når en bruger føjer resultaterne af en søgning til et samtalegennemsynssæt, genskabes chatsamtaler (også kaldet *trådede samtaler*) i tjenester som Microsoft Teams i en PDF-fil. Dette job udløses også, når en bruger klikker på **Handling > Opret samtale-PDF'er** i et korrektursæt. Du kan finde flere oplysninger [under Gennemse samtaler i eDiscovery (Premium)](conversation-review-sets.md).
|Konverterer redigerede dokumenter til PDF|Når en bruger har anmærket et dokument i et korrektursæt og redigerer en del af det, kan vedkommende vælge at konvertere det redigerede dokument til en PDF-fil. Dette sikrer, at den redigerede del ikke er synlig, hvis dokumentet eksporteres til præsentation. Du kan få flere oplysninger under [Få vist dokumenter i et gennemsynssæt](view-documents-in-review-set.md).|
|Vurdering af søgeresultater|Når en bruger opretter og kører eller kører en kladdesamling igen, søger søgeværktøjet i indekset efter elementer, der stemmer overens med søgeforespørgslen, og forbereder et estimat, der indeholder antallet og den samlede størrelse af alle elementer i søgningen og det antal datakilder, der søges efter.  Du kan finde flere oplysninger under [Indsaml data for en sag](collecting-data-for-ediscovery.md).|
|Forbereder data til eksport|En bruger eksporterer dokumenter fra et korrektursæt. Når eksporten er fuldført, kan de downloade de eksporterede data til en lokal computer. Du kan finde flere oplysninger under [Eksportér sagsdata](exporting-data-ediscover20.md).|
|Forbereder fejlløsning|Når en bruger vælger en fil og opretter en ny fejlafhjælpning i visningen Fejl under fanen **Behandling** i en sag, er det første trin i processen at uploade den fil, der indeholder behandlingsfejlen, til en Azure Storage-placering i Microsoft-cloudmiljøet. Dette job sporer statussen for overførselsprocessen. Du kan få flere oplysninger om arbejdsprocessen for fejlafhjælpning under [Fejlafhjælpning under behandling af data](error-remediation-when-processing-data-in-advanced-ediscovery.md).|
|Forbereder eksempelvisning af søgning|Når en bruger opretter og kører en ny kladdesamling (eller kører en eksisterende kladdesamling igen), forbereder søgeværktøjet et eksempel på en delmængde af elementer (der svarer til søgeforespørgslen), som kan vises som eksempel. Hvis du får vist søgeresultaterne, kan du se, hvor effektiv søgningen er.  Du kan finde flere oplysninger under [Indsaml data for en sag](collecting-data-for-ediscovery.md#view-search-results-and-statistics).|
|Genindekserer data fra tilsynsførende|Når du føjer en tilsynsførende til en sag, genindekseres alle delvist indekserede elementer i den tilsynsførendes valgte datakilder af en proces, der kaldes *Avanceret indeksering*. Dette job udløses også, når du klikker på **Opdater indeks** under fanen **Behandling** i en sag, og når du opdaterer indekset for en bestemt tilsynsførende på pop op-siden med egenskaber for tilsynsførende. Du kan få flere oplysninger under [Avanceret indeksering af data fra tilsynsførende](indexing-custodian-data.md).
|Kører analyse|En bruger analyserer data i et korrektursæt ved at køre eDiscovery-analyseværktøjer (Premium), f.eks. næsten registrering af dubletter, analyse af mailtråde og temaanalyse. Du kan få flere oplysninger under [Analysér data i et anmeldelsessæt](analyzing-data-in-review-set.md).|
|Mærkning af dokumenter|Dette job udløses, når en bruger klikker på **Start mærkningsjob** i **panelet Mærkning** , når dokumenter gennemses i et korrektursæt. En bruger kan starte dette job efter at have mærket dokumenter i et korrektursæt og derefter massemarkering af dem i visningsdokumentpanelet. Du kan få flere oplysninger under [Mærk dokumenter i et gennemsynssæt](tagging-documents.md).|

## <a name="job-status"></a>Jobstatus

I følgende tabel beskrives de forskellige statustilstande for job.

|Status|Beskrivelse|
|---|---|
|Forelagt|Der blev oprettet et nyt job.  Den dato og det klokkeslæt, hvor jobbet blev sendt, vises i kolonnen **Oprettet** under fanen **Job** .|
|Afsendelse mislykkedes|Jobafsendelsen mislykkedes.  Du bør forsøge at køre den handling, der udløste jobbet, igen.|
|Igangværende|Jobbet er i gang. Du kan overvåge status for jobbet under fanen **Job** .|
|Vellykket|Jobbet blev fuldført. Den dato og det klokkeslæt, hvor jobbet blev fuldført, vises i kolonnen **Fuldført** under fanen **Job** .|
|Delvist fuldført|Jobbet lykkedes. Denne status returneres typisk, når jobbet ikke fandt nogen delvist indekserede data (også kaldet *ikke-indekserede data*) i nogle af de tilsynsførende datakilder.|
|Mislykkedes|Jobbet mislykkedes.  Du bør forsøge at køre den handling, der udløste jobbet, igen. Hvis jobbet mislykkes igen, anbefaler vi, at du kontakter Microsoft Support og angiver supportoplysningerne fra jobbet.|
