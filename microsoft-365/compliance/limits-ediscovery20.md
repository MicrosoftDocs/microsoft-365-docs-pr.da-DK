---
title: Advanced eDiscovery grænser
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide om de case limits, indexing limits, and search limits in effect for the Advanced eDiscovery solution in Microsoft 365.
ms.openlocfilehash: 04b0f98286693ef14019b30ab9c8d3a592484d92
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712789"
---
# <a name="limits-in-advanced-ediscovery"></a>Begrænsninger i Advanced eDiscovery

I denne artikel beskrives grænserne i Advanced eDiscovery i Microsoft 365.

## <a name="case-and-review-set-limits"></a>Grænser for sags- og gennemgang

I følgende tabel vises begrænsningerne for tilfælde og kontrolsæt i Advanced eDiscovery.

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Samlet antal dokumenter, der kan føjes til en sag (for alle korrektursæt i en sag).  <br/> |3 millioner <br/> |
|Samlet filstørrelse pr. indlæsningssæt. Dette omfatter indlæsning af Office 365 i et korrektursæt.  <br/> |300 GB <br/> |
|Samlet mængde data indlæst i alle korrektursæt i organisationen pr. dag.<br/> |2 TB <br/> |
|Maksimale antal indlæsningssæt pr. sag.  <br/> |200 <br/> |
|Maksimale antal korrektursæt pr. sag.  <br/> |20 <br/> |
|Maksimale antal kodegrupper pr. sag.  <br/> |1,000 |
|Maksimale antal entydige mærker pr. sag. <br/> |1.0001<sup></sup> |
|Maksimum af samtidige job i organisationen for at føje indhold til et korrektursæt. Disse job har navnet **Føje data til et gennemsynssæt** og vises på **fanen Jobs** i en sag.| <sup>102</sup> |
|Maksimalt antal samtidige job for at føje indhold til et gennemsynssæt pr. bruger. Disse job har navnet **Føje data til et gennemsynssæt** og vises på **fanen Jobs** i en sag. | 3 |

## <a name="hold-limits"></a>Begrænsninger for venteposition

I følgende tabel vises begrænsningerne for ventelister, der er knyttet Advanced eDiscovery sag.

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Maksimalt antal politikker for venteposition for en organisation. Denne grænse omfatter det samlede antal ventepositionspolitikker i Core eDiscovery og Advanced eDiscovery-sager. <br/> |10.0003<sup></sup>  <br/> |
|Maksimale antal postkasser i et enkelt sags hold. Denne grænse omfatter det samlede antal brugerpostkasser og de postkasser, der er knyttet til Microsoft 365 Grupper, Microsoft Teams og Yammer Grupper. <br/> |1,000  <br/> |
|Maksimale antal websteder i én enkelt venteposition. Denne grænse omfatter det samlede antal OneDrive for Business websteder, SharePoint-websteder og de websteder, der er knyttet til Microsoft 365 Grupper, Microsoft Teams og Yammer Grupper.  <br/> |100  <br/> |

## <a name="indexing-limits"></a>Indekseringsgrænser

I følgende tabel vises indekseringsgrænserne i Advanced eDiscovery.

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Maksimale antal tegn, der er hentet fra en enkelt fil.  <br/> |10 <sup>millioner4</sup> <br/> |
|Maksimumstørrelse på en enkelt fil.   <br/> |150 <sup>MB4</sup> <br/> |
|Maksimal dybde for integrerede elementer i et dokument.  <br/> |<sup>254</sup> <br/> |
|Maksimumstørrelse på filer, der behandles af Optical Character Recognition (OCR).  <br/> |24 <sup>MB4</sup> <br/>  

## <a name="search-limits"></a>Søgebegrænsninger

De grænser, der er beskrevet i dette afsnit, er relateret til brug af **søgeværktøjet** på fanen Søgninger til at indsamle data om en sag. Få mere at vide under [Indsaml data for en sag Advanced eDiscovery](collecting-data-for-ediscovery.md).

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Maksimale antal postkasser eller websteder, der kan søges i i en enkelt søgning. |Ingen grænse|
|Maksimale antal søgninger, der kan køre på samme tid. |Ingen grænse |
|Maksimale antal søgninger, som en enkelt bruger kan starte på samme tid. |10 | 
|Maksimale antal tegn for en søgeforespørgsel (herunder operatorer og betingelser). |10.0005<sup></sup>|
|Maksimale antal tegn for en søgeforespørgsel til SharePoint og OneDrive for Business (herunder operatorer og betingelser). |10,000<br>4.000 med <sup>jokertegn5</sup>|
|Minimumantal af alfategn for præfiks jokertegn; f.eks. **et\**_ eller _* set\***.|3 |  
|Maksimale varianter, der returneres, når du bruger jokertegnet Præfiks til at søge efter et bestemt udtryk, eller når du bruger et præfiks med jokertegn og **NEAR** Boolean-operatoren. |10.0006<sup></sup>|
|Maksimale antal elementer pr. brugerpostkasse, der vises på eksempelsiden for søgninger. De nyeste elementer vises. |100|
|Maksimale antal elementer fra alle postkasser, der vises på eksempelsiden for søgninger.|1,000|
|Maksimale antal postkasser, der kan vises eksempler for søgeresultater.  Hvis der er mere end 1.000 postkasser, der indeholder elementer, der svarer til søgeforespørgslen, er det kun de øverste 1.000 postkasser med de fleste resultater, der kan vises.|1,000|
|Maksimale antal elementer fra SharePoint OneDrive for Business websteder, der vises på eksempelsiden for søgninger. De nyeste elementer vises. |200|
|Maksimale antal websteder SharePoint og OneDrive for Business, der kan vises i forhåndsvisning for søgeresultater. Hvis der er mere end 200 websteder, der indeholder elementer, der svarer til søgeforespørgslen, er det kun de øverste 200 websteder med de bedste resultater, der er tilgængelige for forhåndsvisning.|200|
|Maksimale antal elementer pr. postkasse i offentlig mappe, der vises på forhåndsvisningssiden for søgninger. |100|
|Maksimale antal elementer, der findes i alle elementer i postkassen i den offentlige mappe, som vises på eksempelsiden til søgninger. |200|
|Maksimale antal postkasser i offentlige mapper, der kan vises i søgeresultaterne. Hvis der er mere end 500 postkasser i offentlige mapper, der indeholder elementer, der svarer til søgeforespørgslen, er det kun de øverste 500 postkasser med de bedste resultater, der er tilgængelige til forhåndsvisning.|500|
|Den maksimale størrelse på et element, der kan vises på eksempelsiden i en kladdesamling.|10.000.000 byte (ca. 9,5 MB)|

## <a name="search-times"></a>Søgetider

Microsoft indsamler oplysninger om ydeevnen for søgninger, der køres af alle organisationer. Selvom kompleksiteten af søgeforespørgslen kan påvirke søgetider, er den største faktor, der påvirker, hvor lang tid søgninger tager, antallet af postkasser, der søges i. Selvom Microsoft ikke leverer en serviceaftale for søgetider, viser følgende tabel gennemsnitlige søgetider for søgning i samlinger baseret på antallet af postkasser, der er inkluderet i søgningen.
  
| Antal postkasser | Gennemsnitlig søgetid |
|:-----|:-----|
|100  <br/> |30 sekunder  <br/> |
|1,000  <br/> |45 sekunder  <br/> |
|10,000  <br/> |4 minutter  <br/> |
|25,000  <br/> |10 minutter  <br/> |
|50,000  <br/> |20 minutter  <br/> |
|100,000  <br/> |25 minutter  <br/> |

## <a name="viewer-limits"></a>Begrænsninger for fremvisere

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Maksimumstørrelse på Excel fil, der kan vises i den oprindelige fremviser.  <br/> |4 MB  <br/> |

## <a name="export-limits---final-export-out-of-review-set"></a>Eksportgrænser – Endelig eksport ud af Korrektursæt

De grænser, der er beskrevet i dette afsnit, er relateret til eksport af dokumenter fra et korrektursæt.

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Maksimumstørrelse for en enkelt eksport.|5 millioner dokumenter eller 500 GB, alt efter hvad der er mindre|
|Det maksimale antal samtidige eksporter pr. gennemsynssæt. | 1 |

## <a name="review-set-download-limits"></a>Gennemgå de indstillede grænser for download

| Beskrivelse af grænse | Grænse |
|:-----|:-----|
|Samlet filstørrelse eller maksimalt antal dokumenter, der er hentet fra et korrektursæt.  <br/> |3 MB eller 50 <sup>dokumenter7</sup>|

## <a name="notes"></a>Bemærkninger

> [!NOTE]
> <sup>1</sup> Dette er det maksimale antal mærker, du kan oprette i en sag. Denne grænse er ikke relateret til antallet af dokumenter, der kan mærkes.
>
> <sup>2</sup> Denne grænse deles med eksport af indhold i andre eDiscovery-værktøjer. Det betyder, at samtidige eksporter i Indholdssøgning og Core eDiscovery (og tilføjelse af indhold til gennemgang af sæt i Advanced eDiscovery) alle anvendes i forhold til denne grænse.
>
> <sup>3</sup> Når du sætter mere end 1.000 postkasser eller 100 websteder i venteposition i en enkelt politik for venteposition, skalerer systemet automatisk ventepositionen efter behov. Det betyder, at systemet automatisk føjer dataplaceringer til flere politikker for venteposition i stedet for at føje dem til en enkelt politik for venteposition. Men grænsen på 10.000 politikker for venteposition for hver organisation gælder stadig.
>
> <sup>4</sup> Et element, der overskrider grænsen for en enkelt fil, vises som en behandlingsfejl.
>
> <sup>5</sup> Når du søger SharePoint og OneDrive for Business, tæller tegnene i URL-adresserne for de websteder, der søges efter, med denne grænse. Det samlede antal tegn består af:<br>
> - Alle tegn i både felterne Brugere og Filtre.
> - Alle søgetilladelsesfiltre, der gælder for brugeren.
> - Tegnene fra alle placeringsegenskaber i søgningen. dette omfatter ExchangeLocation,PublicFolderLocation,SharPointLocation,ExchangeLocationExclusion,PublicFolderLocationExclusion,SharePointLocationExclusion, OneDriveLocationExclusion.
>   For eksempel vil alle SharePoint-websteder og OneDrive-konti i søgningen tælle som seks tegn, da ordet "ALL" vises for både feltet SharePointLocation og OneDriveLocation.
>
> <sup>6</sup> Til forespørgsler, der ikke er udtryk (en nøgleordsværdi, der ikke bruger dobbelte anførselstegn), bruger vi et særligt præfiksindeks. Dette fortæller os, at et ord forekommer i et dokument, men ikke der, hvor det forekommer i dokumentet. For at udføre en sætningsforespørgsel (en nøgleordsværdi med dobbelte anførselstegn) skal vi sammenligne placeringen i dokumentet med ordene i udtrykket. Det betyder, at vi ikke kan bruge præfiksindekset for udtryksforespørgsler. I dette tilfælde udvider vi forespørgslen internt med alle mulige ord, som præfikset udvides til; F.eks  **. kan tid\**_ udvides til _*"tid ELLER timer ELLER klokkeslæt ELLER timex ELLER timeboxED OR ..."**. Grænsen på 10.000 er det maksimale antal varianter, som ordet kan udvides til, ikke antallet af dokumenter, der matcher forespørgslen. Der er ingen øvre grænse for udtryk, der ikke er udtryk.
>
> <sup>7</sup> Denne grænse gælder for at hente udvalgte dokumenter fra et korrektursæt. Den gælder ikke for eksport af dokumenter fra et korrektursæt. Du kan finde flere oplysninger om at hente og eksportere dokumenter [under Eksportere sagsdata Advanced eDiscovery](exporting-data-ediscover20.md).
