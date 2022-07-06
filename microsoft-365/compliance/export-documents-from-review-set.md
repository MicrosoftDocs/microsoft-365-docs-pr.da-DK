---
title: Eksportér dokumenter fra et valideringssæt
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
description: Få mere at vide om, hvordan du vælger og eksporterer indhold fra et eDiscovery(Premium)-korrektursæt til præsentationer eller eksterne korrekturer.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 249990915cb012ca71a40ef074d8a1f5044b8d6e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635343"
---
# <a name="export-documents-from-a-review-set-in-ediscovery-premium"></a>Eksportér dokumenter fra et korrektursæt i eDiscovery (Premium)

Eksport giver brugerne mulighed for at tilpasse det indhold, der er inkluderet i downloadpakken, når du eksporterer dokumentet fra et korrektursæt i eDiscovery (Premium).

Sådan eksporterer du dokumenter fra et gennemsynssæt:

1. I Microsoft Purview-compliance-portal skal du åbne sagen eDiscovery (Premium), vælge fanen **Gennemse sæt** og derefter vælge det korrektursæt, du vil eksportere.

2. Klik på **Handlingseksport** >  i korrektursættet.

   Værktøjet Eksportér viser pop op-siden med indstillingerne for at konfigurere eksporten. Nogle indstillinger er valgt som standard, men du kan ændre disse. Se følgende afsnit for at få beskrivelser af de eksportindstillinger, du kan konfigurere.

   ![Konfigurationsindstillinger til eksport af elementer fra et korrektursæt.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Når du har konfigureret eksporten, skal du klikke på **Eksportér** for at starte eksportprocessen. Afhængigt af den indstilling, du har valgt i afsnittet **Outputindstillinger** , kan du få adgang til eksportfilerne ved at downloade direkte eller på din organisations Azure Storage-konto.

> [!NOTE]
> Eksportjob bevares i hele sagen. Du skal dog hente indholdet fra et eksportjob inden for 30 dage, efter at eksportjobbet er fuldført.

## <a name="export-options"></a>Eksportindstillinger

Brug følgende indstillinger til at konfigurere eksporten. Ikke alle indstillinger er tilladt for nogle outputindstillinger, især eksport af tekstfiler og redigerede PDF-filer er ikke tilladt, når du eksporterer til PST-formatet.

- **Eksportnavn**: Navnet på eksportjobbet. Dette bruges til at navngive de ZIP-filer, der downloades.

- **Beskrivelse**: Fritekstfelt, hvor du kan tilføje en beskrivelse.

- **Eksportér disse dokumenter**

  - Kun valgte dokumenter: Denne indstilling eksporterer kun de dokumenter, der er valgt i øjeblikket. Denne indstilling er kun tilgængelig, når der er valgt elementer i et korrektursæt.
  
  - Alle filtrerede dokumenter: Denne indstilling eksporterer dokumenterne i et aktivt filter. Denne indstilling er kun tilgængelig, når der anvendes et filter på korrektursættet.
  
  - Alle dokumenter i korrektursættet: Denne indstilling eksporterer alle dokumenter i korrektursættet.

- **Outputindstillinger**: Eksporteret indhold kan enten downloades direkte via en webbrowser eller kan sendes til en Azure Storage-konto. De første to indstillinger muliggør direkte download.
  
  - Kun rapporter: Det er kun oversigts- og indlæsningsfilen, der oprettes.
  
  - Løse filer og PST'er (mail føjes til PST'er, når det er muligt): Filer eksporteres i et format, der ligner den oprindelige mappestruktur, som brugerne ser i deres oprindelige programmer.  Du kan finde flere oplysninger i afsnittet [Løse filer og PST-eksportstruktur](#loose-files-and-pst-export-structure) .
  
  - Komprimeret mappestruktur: Filer eksporteres og inkluderes i downloaden.
  
  - Komprimeret mappestruktur, der eksporteres til din Azure Storage-konto: Filer eksporteres til din organisations Azure Storage-konto. Til denne indstilling skal du angive URL-adressen for objektbeholderen på din Azure Storage-konto for at eksportere filerne til. Du skal også angive SAS-tokenet (Shared Access Signature) for din Azure Storage-konto. Du kan finde flere oplysninger [under Eksportér dokumenter i et gennemsynssæt til en Azure Storage-konto](download-export-jobs.md).

- **Omfatter**
  
  - Mærker: Når det er valgt, medtages mærkningsoplysninger i indlæsningsfilen.
  
  - Tekstfiler: Denne indstilling indeholder de udpakkede tekstversioner af oprindelige filer i eksporten.
  
  - Erstat redigerede oprindelige filer med konverterede PDF-filer: Hvis der genereres redigerede PDF-filer under gennemsyn, er disse filer tilgængelige til eksport. Du kan vælge kun at eksportere de oprindelige filer, der er redigeret (ved ikke at vælge denne indstilling), eller du kan vælge denne indstilling for at eksportere de PDF-filer, der indeholder de faktiske redigeringer.

  - Samtale-PDF-filer i stedet for individuelle chatmeddelelser: Markér dette afkrydsningsfelt for at eksportere chatsamtaler i en PDF-fil. Alle chatbeskeder fra den samme samtale eksporteres i den samme PDF-fil. Hvis du ikke markerer afkrydsningsfeltet, eksporteres hver entydige meddelelse i en chatsamtale som et separat element. Filen eksporteres i samme format, som den blev gemt i postkassen. I forbindelse med en bestemt samtale modtager du flere .msg-filer.

I følgende afsnit beskrives mappestrukturen for løse filer og indstillinger for smal mappestruktur. Eksporter partitioneres i ZIP-filer med en maksimal størrelse på dekomprimeret indhold på 75 GB. Hvis eksportstørrelsen er mindre end 75 GB, består eksporten af en oversigtsfil og en enkelt ZIP-fil. Ved eksporter, der er større end 75 GB ikke-komprimerede data, oprettes der flere ZIP-filer. Når zip-filerne er downloadet, kan de dekomprimeres til en enkelt placering for at genskabe den fulde eksport.

### <a name="loose-files-and-pst-export-structure"></a>Løse filer og PST-eksportstruktur

Hvis du vælger denne eksportindstilling, er det eksporterede indhold organiseret i følgende struktur:

- Summary.csv: Indeholder en oversigt over det indhold, der eksporteres fra korrektursættet

- Rodmappe: Denne mappe i med navnet [Eksportnavn] x af z.zip og gentages for hver ZIP-filpartition. Rodmappen indeholder følgende:
  
  - Export_load_file_x af z.csv: Metadatafilen.
  
  - Advarsler og fejl x for z.csv: Denne fil indeholder oplysninger om fejl, der opstod under forsøg på at eksportere fra korrektursættet.
  
  - Exchange: Denne mappe indeholder alt indhold fra Exchange, der er gemt i PST-filer. Redigerede PDF-filer kan ikke inkluderes i denne indstilling. Hvis der er valgt en vedhæftet fil i korrektursættet, eksporteres den overordnede mail med den vedhæftede fil.
  
    Exchange-mappen kan også indeholde en undermappe med navnet mailboxname_loosefiles.zip, som indeholder følgende elementer:

    - IRM-beskyttede meddelelser (Information Rights Management), der er afkodet.
    - Fejlmeddelelser.
    - Moderne vedhæftede filer eller links, der refereres til i meddelelser.
    - Krypterede elementer (som ikke er inkluderet i PST-filerne i Exchange-mappen).
  
  - SharePoint: Denne mappe indeholder alt oprindeligt indhold fra SharePoint i et oprindeligt filformat. Redigerede PDF-filer kan ikke inkluderes i denne indstilling.

### <a name="condensed-directory-structure"></a>Smal mappestruktur

- Summary.csv: Indeholder en oversigt over det indhold, der eksporteres fra korrektursættet

- Rodmappe: Denne mappe i med navnet [Eksportnavn] x af z.zip og gentages for hver ZIP-filpartition.
  
  - Export_load_file_x af z.csv: Metadatafilen og indeholder også placeringen af hver fil, der er gemt i ZIP-filen.
  
  - Advarsler og fejl x for z.csv: Denne fil indeholder oplysninger om fejl, der opstod under forsøg på at eksportere fra korrektursættet.

  - NativeFiles: Denne mappe indeholder alle de oprindelige filer, der blev eksporteret. Oprindelige filer erstattes med redigerede PDF-filer, hvis du har valgt indstillingen *Erstat redigerede oprindelige filer med konverterede PDF-filer* .
  
  - Error_files: Denne mappe indeholder filer, der enten havde en udpakningsfejl eller en anden behandlingsfejl. Filerne placeres i separate mapper, enten ExtractionError eller ProcessingError. Disse filer er angivet i indlæsningsfilen.

  - Extracted_text_files: Denne mappe indeholder alle de udtrukne tekstfiler, der blev genereret under behandlingen.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Komprimeret mappestruktur, der eksporteres til din Azure Storage-konto

Denne indstilling bruger den samme generelle struktur som *mappen Condensed*, men indholdet zippers ikke, og dataene gemmes på din Azure Storage-konto. Denne indstilling bruges generelt, når du arbejder med en tredjepartsudbyder af eDiscovery. Du kan finde oplysninger om, hvordan du bruger denne indstilling, [under Eksportér dokumenter i en anmeldelse, der er angivet til en Azure Storage-konto](download-export-jobs.md).
