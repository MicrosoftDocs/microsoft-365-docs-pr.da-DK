---
title: Føje søgeresultater til et korrektursæt
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
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du føjer søgeresultater eller eksempler på disse søgeresultater Advanced eDiscovery en gennemgangssæt til en sag.
ms.openlocfilehash: bce0301e7045eeb0dd5c42f8a119d56649120a11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588703"
---
# <a name="add-search-results-to-a-review-set"></a>Føje søgeresultater til et korrektursæt

Når du er tilfreds med resultaterne af en søgning, og du er klar til at gennemse og analysere disse søgeresultater, kan du føje dem til et gennemsynssæt i sagen. Kopiering af de oprindelige data til korrektursættet letter også gennemsyns- og analyseprocessen ved at give dig avancerede analyseværktøjer som f.eks registrering af temaer, registrering af næsten dubletter og identifikation af mailtråde. Du kan også føje data fra ikke-Microsoft 365-datakilder til et korrektursæt, så du kan gennemse disse data ud over de data, du indsamler fra Microsoft 365.

Når du føjer resultaterne af en søgning til et korrektursæt (korrektursæt i en sag vises på fanen Gennemse **sæt** ), sker følgende:

- Søgningen køres igen. Det betyder, at de faktiske søgeresultater, der kopieres til korrektursættet, kan være anderledes end de anslåede resultater, der blev returneret, da søgningen sidst blev kørt.

- Alle elementer i søgeresultaterne kopieres fra den oprindelige datakilde i livetjenesterne og kopieres til en sikker placering Azure Storage Microsoft-skyen.

- Alle elementer (herunder indhold og metadata) bliver indekseret igen, så alle data i korrektursættet er fuldt søgbare under gennemgangen af sagsdataene. Når du søger efter data i gennemsynssættet under caseundersøgelse, kan det give nye dataresultater en grundig og hurtig søgning.

- En fil, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) og er vedhæftet en mail, der returneres i søgeresultaterne, dekrypteres, når mailen og den vedhæftede fil føjes til gennemsynssættet. Du kan gennemse og forespørge på den dekrypterede fil i korrektursættet. Du skal have tildelt rollen RMS Dekrypter for at tilføje dekrypterede vedhæftede filer i mails til et gennemsynssæt. Få mere at vide under [Dekryptering i Microsoft 365 eDiscovery-værktøjer](ediscovery-decryption.md).

Hvis du vil føje data til et korrektursæt, skal du  klikke på en søgning på fanen Søgninger  og derefter klikke på Tilføj resultater for at gennemse sættet på pop op-siden.

Du kan føje til et eksisterende korrektursæt eller oprette et nyt korrektursæt.  Hvis du føjer til et nyt korrektursæt, skal du angive navnet og derefter klikke på **Tilføj for** at få vist pop op-siden.

![Vælg et korrektursæt, og konfigurer samlingsindstillinger.](../media/AeD_AddToReviewSet.png)

Det er lang tid at føje data til et korrektursæt. Denne proces omfatter indsamling af elementer fra de oprindelige datakilder i Microsoft 365 (f.eks. fra postkasser og websteder), kopiering af dem til Azure Storage-placeringen (denne kopieringsproces kaldes også *ingestion*) og derefter genindførte elementerne. Du kan spore status på fanen **Jobs** eller på fanen Søgninger ved  at overvåge status i kolonnen Tilføjede **data til gennemsynssæt**. Når behandlingen af korrektursættet er fuldført, skal  du klikke på fanen Gennemse sæt i sagen og derefter klikke på korrektursættet for at starte filtreringsprocessen, gennemgangen, mærkningen og eksporten af data i korrektursættet.

## <a name="define-options-to-scope-your-collection-for-review"></a>Definer indstillinger for at begrænse din samling til gennemsyn

Når du føjer indholdet af en søgning til et eksisterende eller nyt korrektursæt, har du følgende muligheder for at indsamle indholdet til gennemsyn:

- **Medtag versioner fra SharePoint (beta)**: Brug denne indstilling til at aktivere indsamling af alle versioner af et SharePoint-dokument pr. versionsgrænserne og søgeparametre i samlingen. Hvis du vælger denne indstilling, øges størrelsen på elementer, der føjes til korrektursættet betydeligt.

- **Indstillinger for hentning af** samtaler: Elementer, der er føjet til korrektursættet, er aktiveret til samtaler med tråde for at hjælpe med at gennemse indhold i konteksten for frem og tilbage-samtalen. Du kan finde flere [oplysninger i Gennemse samtaler i Advanced eDiscovery](conversation-review-sets.md).

- **Aktivér hentning af moderne vedhæftede** filer: Brug denne indstilling til at medtage moderne vedhæftede filer eller sammenkædede filer i samlingen til yderligere gennemgang. Du kan finde flere oplysninger om de søgbare egenskaber, der er relateret til moderne vedhæftede filer, under Felter [til dokumentmetadata Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

## <a name="add-a-sample-to-a-review-set"></a>Føj en prøve til et korrektursæt

Hvis du vil validere resultaterne af en søgning grundigre, før du føjer dem alle til et korrektursæt, kan du føje en stikprøve af søgeresultaterne til et korrektursæt i stedet for at tilføje alt.

Hvis du vil føje en prøve til et korrektursæt, skal du  klikke på en søgning på fanen Søgninger og **klikke på Eksempel** på pop op-siden. På siden **Stikprøveparametre** skal du vælge en af følgende indstillinger:

- **Tillidsniveau %** og **Tillidsinterval %** – De elementer, der føjes til korrektursættet, bestemmes af de statistiske parametre, du angiver. Hvis du typisk bruger et tillidsniveau og interval, når der anvendes stikprøveresultater, skal du angive dem i rullelisten. Ellers skal du bruge standardindstillingerne.

- **Tilfældigt eksempel %** – De elementer, der føjes til korrektursættet, er baseret på et tilfældigt udvalg af den angivne procentdel af det samlede antal elementer, der returneres af søgningen.

Når du har valgt og konfigureret en af de forrige indstillinger, skal du vælge et korrektursæt, som eksemplet skal føjes til, og derefter klikke på **Send**. Igen kan du spore status på fanen **Jobs** eller på fanen Søgninger ved at  overvåge status i kolonnen Tilføjede data, der **skal gennemses**.

## <a name="optical-character-recognition"></a>Optisk tegngenkendelse

Når du føjer søgeresultater til et korrektursæt, udtrækker optisk tegngenkendelse (OCR)-funktionalitet i Advanced eDiscovery automatisk tekst fra billeder og inkluderer billedteksten med de data, der er føjet til et korrektursæt. Du kan få vist den udpakkede tekst i Tekstvisning for den valgte billedfil i korrektursættet. Dette giver dig mulighed for yderligere gennemgang og analyse af tekst i billeder. OCR understøttes til løse filer, vedhæftede filer i mails og integrerede billeder. Du kan finde en liste over billedfilformater, der understøttes af OCR, under [Understøttede filtyper Advanced eDiscovery](supported-filetypes-ediscovery20.md#image).

Du skal aktivere OCR-funktionalitet for hvert tilfælde, som du opretter i Advanced eDiscovery. Få mere at vide under [Konfigurer indstillinger for søgning og analyse](configure-search-and-analytics-settings-in-advanced-ediscovery.md#optical-character-recognition-ocr).
