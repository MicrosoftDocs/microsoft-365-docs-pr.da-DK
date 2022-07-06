---
title: Føj søgeresultater til et korrektursæt
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
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du føjer søgeresultater eller eksempler af disse søgeresultater til et eDiscovery(Premium)-sagsgennemgangssæt.
ms.openlocfilehash: 48371521edef225b63b6b06170dc422881122034
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640936"
---
# <a name="add-search-results-to-a-review-set"></a>Føj søgeresultater til et korrektursæt

Når du er tilfreds med resultaterne af en søgning, og du er klar til at gennemse og analysere disse søgeresultater, kan du føje dem til et korrektursæt i tilfælde af. Kopiering af de oprindelige data til korrektursættet faciliterer også gennemgangs- og analyseprocessen ved at give dig avancerede analyseværktøjer, f.eks. registrering af temaer, registrering af næsten dubletter og identifikation af mailtråde. Du kan også føje data fra ikke-Microsoft 365-datakilder til et korrektursæt, så du kan gennemse disse data ud over de data, du indsamler fra Microsoft 365.

Når du føjer resultaterne af en søgning til et korrektursæt (korrektursættene i en sag vises under fanen **Korrektursæt** ), sker følgende ting:

- Søgningen køres igen. Det betyder, at de faktiske søgeresultater, der kopieres til korrektursættet, kan være anderledes end de anslåede resultater, der blev returneret, da søgningen sidst blev kørt.

- Alle elementer i søgeresultaterne kopieres fra den oprindelige datakilde i livetjenesterne og kopieres til en sikker Azure Storage-placering i Microsoft-cloudmiljøet.

- Alle elementer (herunder indhold og metadata) omdexeres, så alle data i korrektursættet er fuldt søgbare under gennemgangen af sagsdataene. Genintegrering af dataene resulterer i grundige og hurtige søgninger, når du søger efter dataene i gennemgangssættet under sagsundersøgelsen.

- En fil, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) og er knyttet til en mail, der returneres i søgeresultaterne, dekrypteres, når mailen og den vedhæftede fil føjes til korrektursættet. Du kan gennemse og forespørge den dekrypterede fil i korrektursættet. Du skal tildeles rollen RMS Dekrypter for at føje dekrypterede vedhæftede filer i mails til et korrektursæt. Du kan få flere oplysninger [under Dekryptering i Microsoft Purview eDiscovery værktøjer](ediscovery-decryption.md).

Hvis du vil føje data til et korrektursæt, skal du klikke på en søgning under fanen **Søgninger** og derefter klikke på **Tilføj resultater for at gennemse sæt** på pop op-siden.

Du kan føje til et eksisterende korrektursæt eller oprette et nyt korrektursæt.  Hvis du føjer til et nyt korrektursæt, skal du angive navnet og derefter klikke på **Tilføj** for at få vist pop op-siden.

![Vælg et korrektursæt, og konfigurer indstillinger for samling.](../media/AeD_AddToReviewSet.png)

Tilføjelse af data til et korrektursæt er en langvarig proces. Denne proces omfatter indsamling af elementer fra de oprindelige datakilder i Microsoft 365 (f.eks. fra postkasser og websteder), kopiering af dem til Azure Storage-placeringen (denne kopieringsproces kaldes også *indtagelse*) og derefter omdexere elementerne. Du kan spore statussen under fanen **Job** eller under fanen **Søgninger** ved at overvåge statussen i kolonnen **Tilføjede data for at gennemse den sætkolonne** . Når behandlingen af gennemsynssættet er fuldført, skal du klikke på fanen **Gennemse sæt** i sagen og derefter klikke på korrektursættet for at starte processen med at filtrere, gennemse, mærke og eksportere data i korrektursættet.

## <a name="define-options-to-scope-your-collection-for-review"></a>Definer indstillinger til gennemsyn af din samling

Når du føjer indholdet af en søgning til et eksisterende eller nyt korrektursæt, har du følgende muligheder for at indsamle indholdet til gennemsyn:

- **Medtag versioner fra SharePoint (beta)**: Brug denne indstilling til at aktivere samlingen af alle versioner af et SharePoint-dokument i henhold til versionsgrænserne og søgeparametrene for samlingen. Hvis du vælger denne indstilling, øges størrelsen af elementer, der føjes til korrektursættet, markant.

- **Indstillinger for hentning af samtale**: Elementer, der er føjet til korrektursættet, er aktiveret for trådede samtaler for at hjælpe med at gennemse indhold i forbindelse med frem og tilbage-samtalen. Du kan finde flere oplysninger [under Gennemse samtaler i eDiscovery (Premium)](conversation-review-sets.md).

- **Aktivér hentning for moderne vedhæftede filer**: Brug denne indstilling til at inkludere moderne vedhæftede filer eller sammenkædede filer i samlingen til yderligere gennemsyn. Du kan finde flere oplysninger om søgbare egenskaber, der er relateret til moderne vedhæftede filer, [i Dokumentmetadatafelter i eDiscovery (Premium)](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Føj et eksempel til et korrektursæt

Hvis du vil validere resultaterne af en søgning mere grundigt, før du føjer dem alle til et korrektursæt, kan du føje et eksempel på søgeresultaterne til et korrektursæt i stedet for at tilføje alt.

Hvis du vil føje et eksempel til et korrektursæt, skal du klikke på en søgning under fanen **Søgninger** og klikke på **Eksempel** på pop op-siden. Vælg en af følgende indstillinger på siden **Parametre for stikprøvetagning** :

- **Konfidensniveau %** og **konfidensinterval %** – De elementer, der føjes til korrektursættet, bestemmes af de statistiske parametre, du har angivet. Hvis du typisk bruger et konfidensniveau og et interval, når du prøver resultater, skal du angive dem på rullelistene. Ellers skal du bruge standardindstillingerne.

- **Random sample %** – De elementer, der føjes til korrektursættet, er baseret på et tilfældigt valg af den angivne procentdel af det samlede antal elementer, der returneres af søgningen.

Når du har valgt og konfigureret en af de tidligere indstillinger, skal du vælge et korrektursæt for at føje eksemplet til og derefter klikke på **Send**. Igen kan du spore statussen under fanen **Job** eller under fanen **Søgninger** ved at overvåge status i kolonnen **Tilføjet data for at gennemse den angivne** kolonne.

## <a name="optical-character-recognition"></a>Optisk tegngenkendelse

Når du føjer søgeresultater til et korrektursæt, udtrækker optisk tegngenkendelse (OCR) i eDiscovery (Premium) automatisk tekst fra billeder og inkluderer billedteksten med de data, der er føjet til et korrektursæt. Du kan få vist den udtrukne tekst i Tekstfremviser for den valgte billedfil i korrektursættet. Dette giver dig mulighed for at foretage yderligere gennemgang og analyse af tekst i billeder. OCR understøttes til løse filer, vedhæftede filer i mails og integrerede billeder. Du kan finde en liste over billedfilformater, der understøttes for OCR, [under Understøttede filtyper i eDiscovery (Premium)](supported-filetypes-ediscovery20.md#image).

Du skal aktivere OCR-funktionalitet for hver enkelt sag, du opretter i eDiscovery (Premium). Du kan finde flere oplysninger under [Konfigurer søge- og analyseindstillinger](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
