---
title: Få mere at vide om Administration af Microsoft Purview-poster
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
description: Få mere at vide om, hvordan Microsoft Purview-datastyring understøtter elementer af høj værdi til forretningsrelaterede, juridiske eller lovmæssige krav til registrering.
ms.openlocfilehash: b14c622d1468cdb91ad1ac8e58c184e650ebbe6c
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65284858"
---
# <a name="learn-about-records-management"></a>Få mere at vide om datastyring

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!TIP]
> *Vidste du, at du kan prøve premiumversionerne af alle ni Microsoft Purview-løsninger gratis?* Brug den 90-dages prøveversion af Purview-løsninger til at udforske, hvordan robuste Purview-funktioner kan hjælpe din organisation med at opfylde sine behov for overholdelse af angivne standarder. Microsoft 365 E3 og Office 365 E3 kunder kan starte nu ved [prøveversionshubben til Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Få mere at vide om [, hvem der kan tilmelde sig og prøvevilkår](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Organisationer af alle typer kræver en løsning til datastyring for at administrere lovmæssige, juridiske og forretningskritiske poster på tværs af deres virksomhedsdata. Datastyring for Microsoft Purview hjælper en organisation med at administrere deres juridiske forpligtelser, giver mulighed for at demonstrere overholdelse af regler og øger effektiviteten med regelmæssig fordeling af elementer, der ikke længere skal bevares, ikke længere er af værdi eller ikke længere kræves til forretningsmæssige formål.

Brug følgende funktioner til at understøtte din løsning til datastyring for Microsoft 365 tjenester og apps:

- **Mærk indhold som en post**. Opret og konfigurer opbevaringsmærkater for at markere indhold som en [post](#records) , der derefter kan anvendes af brugere eller automatisk anvendes ved at identificere følsomme oplysninger, nøgleord eller indholdstyper.

- **Overfør og administrer dine opbevaringskrav med filplanen**. Ved hjælp af en [filplan](file-plan-manager.md) kan du hente en eksisterende opbevaringsplan for at Microsoft 365 eller oprette en ny til forbedrede administrationsfunktioner.

- **Konfigurer indstillinger for opbevaring og sletning med opbevaringsmærkater**. Konfigurer [opbevaringsmærkater](retention.md#retention-labels) med opbevaringsperioder og handlinger baseret på forskellige faktorer, der omfatter den dato, hvor den senest blev ændret eller oprettet.

- **Start forskellige opbevaringsperioder, når der opstår en hændelse** med [hændelsesbaseret opbevaring](event-driven-retention.md).

- **Gennemse og valider disposition** med [dispositionsgennemgange](disposition.md#disposition-reviews) og bevis for [sletning af poster](disposition.md#disposition-of-records).

- **Eksportér oplysninger om alle fjernede elementer** med [eksportindstillingen](disposition.md#filter-and-export-the-views).

- **Angiv specifikke tilladelser** for datastyringsfunktioner i din organisation for at [have den rette adgang](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Ved hjælp af disse funktioner kan du inkorporere organisationens opbevaringsplaner og -krav i en løsning til datastyring, der administrerer opbevaring, erklæring af poster og fordeling for at understøtte hele livscyklussen for dit indhold.

Ud over onlinedokumentationen kan det være nyttigt at downloade et [sæt ofte stillede spørgsmål](https://aka.ms/MIPC/Blog-RecordsManagementWebinar) fra et webinar til datastyring. Optagelsen af det faktiske webinar er ikke længere tilgængelig.

## <a name="records"></a>Poster

Når indhold erklæres som en post:

- Der er begrænsninger for elementerne med hensyn til, hvilke [handlinger der er tilladt eller blokeret](#compare-restrictions-for-what-actions-are-allowed-or-blocked).

- Yderligere aktiviteter om elementet logføres.

- Du har bevis for fordeling, når elementerne slettes ved afslutningen af deres opbevaringsperiode.

Du kan bruge [opbevaringsmærkater](retention.md#retention-labels) til at markere indhold som en **post** eller en **lovmæssig post**. Forskellen mellem disse to er forklaret i næste afsnit. Du kan enten publicere disse mærkater, så brugere og administratorer kan anvende dem manuelt på indhold, eller automatisk anvende disse mærkater på indhold, som du vil markere som en post eller en lovmæssig post.

Når du bruger opbevaringsmærkater til at deklarere poster, kan du implementere en enkelt og ensartet strategi for administration af poster på tværs af dit Microsoft 365 miljø.

### <a name="compare-restrictions-for-what-actions-are-allowed-or-blocked"></a>Sammenlign begrænsninger for, hvilke handlinger der er tilladt eller blokeret

Brug følgende tabel til at identificere, hvilke begrænsninger der er lagt på indhold som følge af anvendelse af en standardopbevaringsmærkat og opbevaringsmærkater, der markerer indhold som en post eller lovmæssig post.

En standardopbevaringsmærkat har opbevaringsindstillinger og handlinger, men markerer ikke indhold som en post eller en lovmæssig post.

> [!NOTE]
> Af hensyn til fuldførelse indeholder tabellen kolonner for en låst og ulåst post, som gælder for SharePoint og OneDrive, men ikke Exchange. Muligheden for at låse og låse en post op bruger [postversioner](record-versioning.md), der ikke understøttes for Exchange elementer. Så for alle Exchange elementer, der er markeret som en post, knyttes funktionsmåden til kolonnen **Post – låst** og **Kolonnen Post – ulåst** er ikke relevant.


|Handling| Opbevaringsmærkat |Post - låst| Post – ulåst| Myndighedspost |
|:-----|:-----|:-----|:-----|:-----|:-----|
|Rediger indhold|Tilladt | **Blokeret** | Tilladt | **Blokeret**|
|Rediger egenskaber, herunder omdøbning|Tilladt |Tilladt <sup>1</sup> | Tilladt | **Blokeret**|
|Slette|Tilladt <sup>2</sup> |**Blokeret** |**Blokeret**| **Blokeret**|
|Kopiere|Tilladt |Tilladt | Tilladt| Tilladt|
|Flyt inden for objektbeholder <sup>3</sup>|Tilladt |Tilladt | Tilladt| Tilladt|
|Flyt på tværs af objektbeholdere <sup>3</sup>|Tilladt |Tilladt, hvis den aldrig blev låst op | **Blokeret** | **Blokeret**|
|Åbn/læs|Tilladt |Tilladt | Tilladt| Tilladt|
|Skift navn|Tilladt |Tilladt – kun objektbeholderadministrator | **Blokeret**| **Blokeret**
|Fjern navn|Tilladt |Tilladt – kun objektbeholderadministrator | **Blokeret**| **Blokeret**

Fodnoter:

<sup>1</sup> Redigeringsegenskaber for en låst post er tilladt som standard, men kan blokeres af en lejerindstilling i [Microsoft Purview-overholdelsesportalPostadministrationIndstillinger](https://compliance.microsoft.com/) >  for **administration** >  Af **posterAdministrationsmærkaterTillad** >  >  **redigering af postegenskaber**.

<sup>2</sup> Sletning af navngivne elementer i SharePoint og OneDrive kan blokeres som en lejerindstilling i [Microsoft Purview-overholdelsesportalPostadministrationIndstillinger](https://compliance.microsoft.com/) >  for >  administration  > **afpostadministrationSletning** >  **af elementer**.

Når du anvender en opbevaringsmærkat på et listeelement, der har en vedhæftet fil, arver dokumentet ikke opbevaringsindstillingerne og kan slettes fra listeelementet. Hvis listeelementet til sammenligning blev erklæret som en post med en opbevaringsmærkat, ville den vedhæftede fil nedarve opbevaringsindstillingerne og kunne ikke slettes.

<sup>3</sup> Objektbeholdere omfatter SharePoint dokumentbiblioteker, OneDrive konti og Exchange postkasser.

> [!IMPORTANT]
> Den vigtigste forskel for en lovmæssig post er, at når den er anvendt på indhold, kan ingen, ikke engang en global administrator, fjerne mærkaten.
>
> Opbevaringsmærkater, der er konfigureret for lovmæssige poster, har også følgende administratorbegrænsninger:
>
> - Opbevaringsperioden kan ikke gøres kortere, når mærkaten er gemt, men kun udvidet.
> - Disse mærkater understøttes ikke af politikker for automatisk mærkning og skal anvendes ved hjælp af [politikker for opbevaringsmærkater](create-apply-retention-labels.md).
>
> Desuden kan der ikke anvendes en lovmæssig mærkat på et dokument, der er tjekket ud i SharePoint.
>
> På grund af begrænsningerne og uigenkaldelige handlinger skal du sørge for at bruge lovmæssige poster, før du vælger denne indstilling for dine opbevaringsmærkater. For at forhindre utilsigtet konfiguration er denne indstilling ikke tilgængelig som standard, men skal først aktiveres ved hjælp af PowerShell. Instruktioner medtages i [Deklarer poster ved hjælp af opbevaringsmærkater](declare-records.md).

## <a name="configuration-guidance"></a>Konfigurationsvejledning

Se [Kom i gang med datastyring](get-started-with-records-management.md). Denne artikel indeholder oplysninger om abonnementer, tilladelser og links til end-to-end-konfigurationsvejledning til scenarier til datastyring.
