---
title: Datastyring i Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- admindeeplinkCOMPLIANCE
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Med datastyring i Microsoft 365 kan du anvende dine opbevaringsplaner i en filplan, der administrerer opbevaring, dataerklæring og disposition.
ms.openlocfilehash: ce00fdfc6db90b9c65051a31e8768d6cd661072d
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755683"
---
# <a name="learn-about-records-management-in-microsoft-365"></a>Få mere at vide om datastyring i Microsoft 365

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Organisationer af alle typer kræver en løsning til datastyring for at administrere lovgivningsmæssige, juridiske og forretningsmæssige data på tværs af deres virksomhedsdata. Datastyring i Microsoft 365 hjælper en organisation med at administrere deres juridiske forpligtelser, giver mulighed for at demonstrere overholdelse af bestemmelser og øger effektiviteten med almindelig disposition af elementer, der ikke længere kræves for at blive bevaret, ikke længere af værdi eller ikke længere er nødvendige til forretningsmæssige formål.

Brug følgende funktioner til at understøtte din løsning til datastyring i Microsoft 365:

- **Navn giv indhold som en post**. Opret og konfigurer opbevaringsnavne for at markere indhold [](#records) som en post, som derefter kan anvendes af brugere eller automatisk anvendes ved at identificere følsomme oplysninger, nøgleord eller indholdstyper.

- **Overfør og administrer dine opbevaringskrav med filplan**. Ved hjælp af [en filplan](file-plan-manager.md) kan du hente en eksisterende opbevaringsplan for at Microsoft 365, eller du kan oprette en ny for at få forbedrede administrationsfunktioner.

- **Konfigurer indstillinger for opbevaring og sletning med opbevaringsnavne**. Konfigurer [opbevaringsnavne](retention.md#retention-labels) med opbevaringsperioderne og handlinger baseret på forskellige faktorer, der omfatter datoen, hvor seneste ændring eller oprettelse er.

- **Start forskellige opbevaringsperioder, når en hændelse forekommer** med [hændelsesbaseret opbevaring](event-driven-retention.md).

- **Gennemse og valider disposition med** [dispositionsgennemgange](disposition.md#disposition-reviews) og dokumentation for [sletning af poster](disposition.md#disposition-of-records).

- **Eksportér oplysninger om alle afhændede** elementer med [eksportindstillingen](disposition.md#filter-and-export-the-views).

- **Angiv specifikke tilladelser for** datastyringsfunktioner i organisationen for at [få den rette adgang](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Ved hjælp af disse funktioner kan du inkorporere organisationens opbevaringsplaner og krav til en løsning til datastyring, der administrerer opbevaring, dataerklæring og disposition, så dit indholds fulde livscyklus understøttes.

Ud over onlinedokumentationen kan det være nyttigt at downloade en præsentation med ofte stillede spørgsmål [fra](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) et webinar om datastyring. Optagelsen af det faktiske webinar er ikke længere tilgængelig.

## <a name="records"></a>Poster

Når indhold erklæres som en post:

- Der sættes begrænsninger på elementerne med hensyn til, hvilke handlinger [der er tilladte eller blokerede](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Yderligere aktiviteter om elementet logføres.

- Du har bevis for dispositionen, når elementerne slettes i slutningen af deres opbevaringsperiode.

Du kan [bruge opbevaringsnavne](retention.md#retention-labels) til at markere indhold **som en** post eller en **lovgivningspost**. Forskellen mellem disse to er forklaret i næste afsnit. Du kan enten publicere disse etiketter, så brugere og administratorer manuelt kan anvende dem på indhold, eller automatisk anvende disse etiketter på indhold, du vil markere som en post eller en lovpost.

Ved at bruge opbevaringsetiketter til at erklære poster kan du implementere en enkelt og ensartet strategi til administration af data på tværs Microsoft 365 miljø.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Sammenlign begrænsninger for, hvilke handlinger der er tilladte eller blokerede

Brug følgende tabel til at identificere, hvilke begrænsninger der er på indholdet som et resultat af at anvende en standardopbevaringsetiket og opbevaringsetiketter, der markerer indhold som en post eller en lovgivningsmæssig post.

En standardopbevaringsetiket har opbevaringsindstillinger og -handlinger, men markerer ikke indhold som en post eller en lovgivningsmæssig post.

> [!NOTE]
> For at sikre fuldstændigheden indeholder tabellen kolonner til en låst og ulåst post, som gælder for SharePoint og OneDrive, men ikke Exchange. Muligheden for at låse og låse op for en post [anvender postversionering](record-versioning.md), der ikke understøttes Exchange elementer. Så for alle Exchange, der er markeret som en post, er funktionsmåden kort til kolonnen **Post –** låst, og kolonnen Post **–** ulåst er ikke relevant.


|Handling| Opbevaringsmærkat |Post – låst| Optag – låst op| Lovgivningspost |
|:-----|:-----|:-----|:-----|:-----|:-----|
|Rediger indhold|Tilladt | **Blokeret** | Tilladt | **Blokeret**|
|Rediger egenskaber, herunder omdøb|Tilladt |Tilladt <sup>1</sup> | Tilladt | **Blokeret**|
|Slet|Tilladt <sup>2</sup> |**Blokeret** |**Blokeret**| **Blokeret**|
|Kopiér|Tilladt |Tilladt | Tilladt| Tilladt|
|Flytte inden for objektbeholder <sup>3</sup>|Tilladt |Tilladt | Tilladt| Tilladt|
|Flyt på tværs af <sup>objektbeholdere 3</sup>|Tilladt |Tilladt, hvis den aldrig er låst op | **Blokeret** | **Blokeret**|
|Åbn/læs|Tilladt |Tilladt | Tilladt| Tilladt|
|Skift etiket|Tilladt |Tilladt – kun containeradministrator | **Blokeret**| **Blokeret**
|Fjern etiket|Tilladt |Tilladt – kun containeradministrator | **Blokeret**| **Blokeret**

Fodnoter:

<sup>1</sup> **Redigeringsegenskaber** for en låst post er tilladt som standard, men kan **blokeres** >  >  af en lejerindstilling i [administrationsindstillingerne for Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/) >  PostværdierIndstillinger for **administrationRetention-etiketterStil** >  tilladelse til redigering af postegenskaber **.**

<sup>2</sup> Sletning af navneelementer i SharePoint og OneDrive kan **blokeres** >  >  som en lejerindstilling i [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com/) >  **StyringPosterIndstillinger** for **administrationRetention-navneSlettelse** >  af **elementer.**

Når du anvender et opbevaringsnavn på et listeelement, der har en vedhæftet fil, arver dokumentet ikke opbevaringsindstillingerne og kan slettes fra listeelementet. Til sammenligning ville det vedhæftede dokument nedarve opbevaringsindstillingerne og kunne ikke slettes, hvis det pågældende listeelement blev erklæret som en post med en opbevaringsetiket.

<sup>3</sup> Beholdere omfatter SharePoint dokumentbiblioteker, OneDrive konti og Exchange postkasser.

> [!IMPORTANT]
> Den vigtigste forskel for en lovgivningspost er, at når den anvendes på indhold, kan ingen, ikke engang en global administrator, fjerne navnet.
>
> Opbevaringsnavne, der er konfigureret til lovgivningsmæssige poster, har også følgende administratorbegrænsninger:
>
> - Opbevaringsperioden kan ikke gøres kortere, efter etiketten er gemt, kun udvidet.
> - Disse etiketter understøttes ikke af politikker for automatisk mærkatering, og de skal anvendes ved hjælp af politikker for [opbevaringsetiketter](create-apply-retention-labels.md).
>
> Desuden kan der ikke anvendes en lovgivningsmæssig etiket på et dokument, der er tjekket ud i SharePoint.
>
> På grund af restriktionerne og handlinger, der ikke kan fortrydes, skal du sikre dig, at du er nødt til at bruge lovmæssige poster, før du vælger denne indstilling til dine opbevaringsnavne. For at forhindre utilsigtet konfiguration er denne indstilling ikke tilgængelig som standard, men skal først aktiveres ved hjælp af PowerShell. Der findes instruktioner i [Declare-poster ved hjælp af opbevaringsetiketter](declare-records.md).

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Se [Introduktion til datastyring](get-started-with-records-management.md). Denne artikel indeholder oplysninger om abonnementer, tilladelser og links til en ende-til-en-konfigurationsvejledning til datastyringsscenarier.