---
title: Grænser for eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om de sagsgrænser, indekseringsgrænser og søgegrænser, der gælder for eDiscovery-løsningen (Premium) i Microsoft 365.
ms.openlocfilehash: 5b83cd578b8975dd0185fb2902357c2f0c201043
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772677"
---
# <a name="limits-in-ediscovery-premium"></a>Grænser i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I denne artikel beskrives grænserne i Microsoft Purview eDiscovery-løsning (Premium) i Microsoft 365.

## <a name="case-and-review-set-limits"></a>Grænser for sags- og gennemgangssæt

I følgende tabel vises grænserne for sager og gennemsynssæt i eDiscovery (Premium).

|Beskrivelse af grænse|Grænse|
|---|---|
|Det samlede antal dokumenter, der kan føjes til en sag (for alle korrektursæt i en sag).|3 millioner|
|Samlet filstørrelse pr. indlæsningssæt. Dette omfatter indlæsning af ikke-Office 365 i et korrektursæt.|300 GB|
|Den samlede mængde data, der indlæses i alle korrektursæt i organisationen pr. dag.<br/>|2 TB|
|Maksimalt antal indlæsningssæt pr. case.|200|
|Maksimalt antal korrektursæt pr. sag.|20|
|Maksimalt antal mærkegrupper pr. sag.|1,000|
|Maksimalt antal entydige mærker pr. sag.|1.000<sup>1</sup>|
|Det maksimale antal samtidige job i din organisation, der kan føjes indhold til et korrektursæt. Disse job hedder **Føj data til et korrektursæt** og vises i en sag under fanen **Job** .|10<sup>2</sup>|
|Det maksimale antal samtidige job, der skal føjes indhold til et gennemsynssæt pr. bruger. Disse job hedder **Føj data til et korrektursæt** og vises i en sag under fanen **Job** .|3|

## <a name="hold-limits"></a>Grænser for venteposition

I følgende tabel vises grænserne for de ventepositioner, der er knyttet til en eDiscovery-sag (Premium).

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Det maksimale antal politikker for bevarelse af en organisation. Denne grænse omfatter det samlede antal ventepositionspolitikker i Microsoft Purview eDiscovery-sager (Standard) og Microsoft Purview eDiscovery-sager (Premium). <br/> |10.000<sup>3</sup>  <br/> |
|Det maksimale antal postkasser i en enkelt sag i venteposition. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer Grupper. <br/> |1,000  <br/> |
|Det maksimale antal websteder i en enkelt sag i venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint websteder og de websteder, der er knyttet til Microsoft 365-grupper, Microsoft Teams og Yammer grupper.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Indekseringsgrænser

I følgende tabel vises indekseringsgrænserne i eDiscovery (Premium).

|Beskrivelse af grænse|Grænse|
|---|---|
|Det maksimale antal tegn, der udtrækkes fra en enkelt fil.|10 millioner<sup>4</sup>|
|Maksimal størrelse på en enkelt fil.|150 MB<sup>4</sup>|
|Maksimal dybde for integrerede elementer i et dokument.|25<sup>4</sup>|
|Maksimal størrelse af filer, der behandles af optisk tegngenkendelse (OCR).|24 MB<sup>4</sup> <br/> |
|Maksimalt avanceret gennemløb for indeksering | 2 GB pr. time |

## <a name="search-limits"></a>Søgegrænser

De grænser, der er beskrevet i dette afsnit, er relateret til at bruge søgeværktøjet under fanen **Søgninger** til at indsamle data for en sag. Du kan finde flere oplysninger [under Indsaml data for en sag i eDiscovery (Premium)](collecting-data-for-ediscovery.md).

|Beskrivelse af grænse|Grænse|
|---|---|
|Det maksimale antal postkasser eller websteder, der kan søges i i en enkelt søgning.|Ingen grænse|
|Det maksimale antal søgninger, der kan køre på samme tid.|Ingen grænse|
|Det maksimale antal søgninger, som en enkelt bruger kan starte på samme tid.|10|
|Det maksimale antal tegn for en søgeforespørgsel (herunder operatorer og betingelser).|10.000<sup>5</sup>|
|Det maksimale antal tegn for en søgeforespørgsel for SharePoint og OneDrive for Business websteder (herunder operatorer og betingelser).|10,000<br>4.000 med jokertegn<sup>5</sup>|
|Det mindste antal alfategn for præfiks jokertegn. f.eks. **one\**_ eller _* set\***.|3|
|Det maksimale antal varianter, der returneres, når der bruges præfiks jokertegn til at søge efter et nøjagtigt udtryk, eller når der bruges et præfiks jokertegn og operatoren **NEAR** Boolesk.|10.000<sup>6</sup>|
|Det maksimale antal elementer pr. brugerpostkasse, der vises på eksempelsiden for søgninger. De nyeste elementer vises.|100|
|Det maksimale antal elementer fra alle postkasser, der vises på eksempelsiden for søgninger.|1,000|
|Det maksimale antal postkasser, der kan vises i søgeresultaterne.  Hvis der er mere end 1.000 postkasser, der indeholder elementer, der svarer til søgeforespørgslen, er det kun de øverste 1.000 postkasser med de fleste resultater, der er tilgængelige som prøveversion.|1,000|
|Det maksimale antal elementer fra SharePoint og OneDrive for Business websteder, der vises på eksempelsiden for søgninger. De nyeste elementer vises.|200|
|Det maksimale antal SharePoint og OneDrive for Business websteder, der kan gennemses for søgeresultater. Hvis der er mere end 200 websteder, der indeholder elementer, der svarer til søgeforespørgslen, er det kun de øverste 200 websteder med de fleste resultater, der er tilgængelige som prøveversion.|200|
|Det maksimale antal elementer pr. postkasse med offentlige mapper, der vises på eksempelsiden for søgninger.|100|
|Det maksimale antal elementer, der blev fundet i alle elementer i postkassen med offentlige mapper, som vises på eksempelsiden for søgninger.|200|
|Det maksimale antal offentlige mappepostkasser, der kan vises som eksempel for søgeresultater. Hvis der er mere end 500 offentlige mappepostkasser, der indeholder elementer, der svarer til søgeforespørgslen, er det kun de øverste 500 postkasser med de fleste resultater, der er tilgængelige som prøveversion.|500|
|Den maksimale størrelse af et element, der kan vises på eksempelsiden i en kladdesamling.|10.000.000 byte (ca. 9,5 MB)|

## <a name="search-times"></a>Søgetider

Microsoft indsamler oplysninger om ydeevnen for søgninger, der køres af alle organisationer. Selvom kompleksiteten af søgeforespørgslen kan påvirke søgetiderne, er den største faktor, der påvirker, hvor lang tid det tager at søge, antallet af postkasser, der søges i. Selvom Microsoft ikke leverer en serviceniveauaftale for søgetider, vises de gennemsnitlige søgetider for samlingssøgninger i følgende tabel baseret på antallet af postkasser, der er inkluderet i søgningen.
  
|Antal postkasser|Gennemsnitlig søgetid|
|---|---|
|100|30 sekunder|
|1,000|45 sekunder|
|10,000|4 minutter|
|25,000|10 minutter|
|50,000|20 minutter|
|100,000|25 minutter|

## <a name="viewer-limits"></a>Seergrænser

|Beskrivelse af grænse|Grænse|
|---|---|
|Den maksimale størrelse på Excel fil, der kan vises i den oprindelige fremviser.|4 MB|

## <a name="export-limits---final-export-out-of-review-set"></a>Eksportgrænser – Endelig eksport uden for gennemsynssættet

De grænser, der er beskrevet i dette afsnit, er relateret til eksport af dokumenter fra et gennemsynssæt.

|Beskrivelse af grænse|Grænse|
|---|---|
|Maksimal størrelse på en enkelt eksport.|5 millioner dokumenter eller 500 GB, alt efter hvad der er mindre|
|Det maksimale antal samtidige eksporter pr. korrektursæt.|1|

## <a name="review-set-download-limits"></a>Gennemse de grænser for download, der er angivet

|Beskrivelse af grænse|Grænse|
|---|---|
|Den samlede filstørrelse eller det maksimale antal dokumenter, der er hentet fra et korrektursæt.|3 MB eller 50 dokumenter<sup>7</sup>|


## <a name="reference-notes"></a>Referencenoter
<sup>1</sup> Dette er det maksimale antal mærker, du kan oprette i en sag. Denne grænse er ikke relateret til antallet af dokumenter, der kan mærkes.

<sup>2</sup> Denne grænse deles med eksport af indhold i andre eDiscovery-værktøjer. Det betyder, at samtidige eksporter i Indholdssøgning og eDiscovery (Standard) (og tilføjelse af indhold til korrektursæt i eDiscovery (Premium)) alle anvendes mod denne grænse.

<sup>3</sup> Når du placerer mere end 1.000 postkasser eller 100 websteder i venteposition i en enkelt ventepositionspolitik, skalerer systemet automatisk ventepositionen efter behov. Det betyder, at systemet automatisk føjer dataplaceringer til politikker for flere ventepositioner i stedet for at føje dem til en politik for enkelt venteposition. Grænsen på 10.000 politikker for sags bevarelse pr. organisation gælder dog stadig.

<sup>4</sup> Alle elementer, der overskrider en enkelt filgrænse, vises som en behandlingsfejl.

<sup>5</sup> Når der søges i SharePoint og OneDrive for Business placeringer, tælles tegnene i URL-adresserne på de websteder, der søges efter, med i forhold til denne grænse. Det samlede antal tegn består af:

  - Alle tegn i både felterne Brugere og Filtre.
  - Alle filtre for søgetilladelser, der gælder for brugeren.
  - Tegnene fra alle placeringsegenskaber i søgningen, herunder ExchangeLocation, PublicFolderLocation, SharPointLocation, ExchangeLocationExclusion, PublicFolderLocationExclusion, SharePointLocationExclusion og OneDriveLocationExclusion. Hvis du f.eks. medtager alle SharePoint websteder og OneDrive konti i søgningen, tælles det med seks tegn, da ordet "ALL" vises for både feltet SharePointLocation og OneDriveLocation.

<sup>6</sup> Til forespørgsler uden udtryk (en nøgleordsværdi, der ikke bruger dobbelte anførselstegn) bruger vi et særligt præfiksindeks. Dette fortæller os, at der forekommer et ord i et dokument, men ikke der, hvor det forekommer i dokumentet. Hvis du vil udføre en udtryksforespørgsel (en nøgleordsværdi med dobbelte anførselstegn), skal vi sammenligne placeringen i dokumentet med ordene i udtrykket. Det betyder, at vi ikke kan bruge præfiksindekset til udtryksforespørgsler. I dette tilfælde udvider vi forespørgslen internt med alle de mulige ord, som præfikset udvides til. time_ kan f.eks. ***udvides til _*"time OR timer OR times OR timex OR timeboxed OR ...".\*** Grænsen på 10.000 er det maksimale antal varianter, ordet kan udvides til, ikke antallet af dokumenter, der svarer til forespørgslen. Der er ingen øvre grænse for ord, der ikke er udtryk.

<sup>7</sup> Udældelsesperioden for de Azure Blobs, der gemmer eDiscovery-samlinger (Premium), er ét år. Alle samlinger, der er oprettet for et år siden, er muligvis ikke længere tilgængelige.
 
<sup>8</sup> Denne grænse gælder for hentning af valgte dokumenter fra et gennemsynssæt. Det gælder ikke for eksport af dokumenter fra et korrektursæt. Du kan finde flere oplysninger om hentning og eksport af dokumenter [under Eksportér sagsdata i eDiscovery (Premium)](exporting-data-ediscover20.md).
