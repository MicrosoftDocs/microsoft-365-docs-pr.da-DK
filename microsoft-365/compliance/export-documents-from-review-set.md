---
title: Eksportere dokumenter fra et korrektursæt
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
description: Få mere at vide om, hvordan du vælger og eksporterer indhold Advanced eDiscovery et korrektursæt til præsentationer eller eksterne anmeldelser.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 61de8fed9c5bcb00daf3a8273f3ebfc86fe75a35
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63587293"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Eksportere dokumenter fra et korrektursæt i Advanced eDiscovery

Eksport giver brugerne mulighed for at tilpasse det indhold, der medtages i downloadpakken, når du eksporterer dokument fra et korrektursæt i Advanced eDiscovery.

Sådan eksporterer du dokumenter fra et korrektursæt:

1. I Microsoft 365 Overholdelsescenter skal du åbne Advanced eDiscovery store og små bogstaver, vælge fanen Gennemse sæt og  derefter vælge det korrektursæt, du vil eksportere.

2. I korrektursættet skal du klikke **på** **ActionExport** > .

   Værktøjet Eksportér viser pop op-siden med indstillingerne til konfiguration af eksporten. Nogle indstillinger er valgt som standard, men du kan ændre dem. Se følgende afsnit for at få beskrivelser af de eksportindstillinger, du kan konfigurere.

   ![Konfigurationsindstillinger for eksport af elementer fra et gennemsynssæt.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Når du har konfigureret eksporten, skal du **klikke på** Eksportér for at starte eksporten. Afhængigt af den indstilling, du har valgt i sektionen **Outputindstillinger**, kan du få adgang til eksportfilerne ved direkte download eller i organisationens Azure Storage konto.

> [!NOTE]
> Eksportjob bevares i hele sagens levetid. Du skal dog hente indholdet fra et eksportjob inden for 30 dage, efter eksportjobbet er fuldført.

## <a name="export-options"></a>Eksportindstillinger

Brug følgende indstillinger til at konfigurere eksporten. Det er ikke tilladt at bruge alle indstillinger for nogle outputindstillinger, den vigtigste er, at eksport af tekstfiler og redigerede PDF-filer ikke er tilladt, når du eksporterer til PST-formatet.

- **Eksportnavn**: Navnet på eksportjobbet. Dette bruges til at navngive de ZIP-filer, der skal downloades.

- **Beskrivelse**: Fri tekstfelt, hvor du kan tilføje en beskrivelse.

- **Eksportér disse dokumenter**

  - Kun valgte dokumenter: Denne indstilling eksporterer kun de dokumenter, der aktuelt er markeret. Denne indstilling er kun tilgængelig, når elementer er markeret i et gennemsynssæt.
  
  - Alle filtrerede dokumenter: Denne indstilling eksporterer dokumenterne i et aktivt filter. Denne indstilling er kun tilgængelig, når der anvendes et filter på korrektursættet.
  
  - Alle dokumenter i korrektursættet: Denne indstilling eksporterer alle dokumenter i korrektursættet.

- **Outputindstillinger**: Eksporteret indhold kan enten downloades direkte via en webbrowser eller kan sendes til en Azure Storage konto. De første to indstillinger aktiverer direkte download.
  
  - Kun rapporter: Der oprettes kun oversigts- og indlæsningsfil.
  
  - Løse filer og PST'er (mail føjes til PST'er, når det er muligt): Filer eksporteres i et format, der ligner den oprindelige mappestruktur, som brugerne i deres oprindelige programmer kan se.  Du kan finde flere oplysninger i [afsnittet Løse filer og PST-eksportstruktur](#loose-files-and-pst-export-structure) .
  
  - Komprimeret mappestruktur: Filer eksporteres og medtages i downloaden.
  
  - Komprimeret mappestruktur eksporteret til din Azure Storage-konto: Filer eksporteres til din organisations Azure Storage konto. For at gøre dette skal du angive URL-adressen på beholderen på din Azure Storage, som filerne skal eksporteres til. Du skal også angive SAS-token (Shared Access Signature) for din Azure Storage konto. Få mere at vide under [Eksportér dokumenter i et korrektursæt til en Azure Storage konto](download-export-jobs.md).

- **Medtag**
  
  - Mærker: Når denne indstilling er markeret, medtages oplysninger om mærkning i indlæsningsfilen.
  
  - Tekstfiler: Denne indstilling omfatter de udpakkede tekstversioner af oprindelige filer i eksporten.
  
  - Erstat oprindelige filer med konverterede PDF-filer: Hvis redigerede PDF-filer genereres under gennemsyn, kan disse filer eksporteres. Du kan vælge kun at eksportere de oprindelige filer, der blev redigeret (ved ikke at vælge denne indstilling), eller du kan vælge denne indstilling for at eksportere de PDF-filer, der indeholder de faktiske redactions.

  - PDF-filer til samtaler i stedet for individuelle chatmeddelelser: Markér dette afkrydsningsfelt for at eksportere chatsamtaler i en PDF-fil. Alle chatmeddelelser fra den samme samtale eksporteres i den samme PDF-fil. Hvis dette afkrydsningsfelt ikke er markeret, eksporteres hver enkelt meddelelse i en chatsamtale som et enkeltstående element. Filen eksporteres i samme format, som den blev gemt i postkassen. Hvis du har en bestemt samtale, modtager du flere .msg-filer.

I de følgende afsnit beskrives mappestrukturen for løse filer og indstillingerne for komprimeret mappestruktur. Eksporter opdeles i ZIP-filer med en maksimal størrelse på ukomprimeret indhold på 75 GB. Hvis eksportstørrelsen er mindre end 75 GB, består eksporten af en oversigtsfil og en enkelt ZIP-fil. Ved eksporter, der er større end 75 GB ukomprimerede data, oprettes der flere ZIP-filer. Når ZIP-filerne er hentet, kan de udkomprimeres til en enkelt placering for at genskabe den fulde eksport.

### <a name="loose-files-and-pst-export-structure"></a>Løse filer og PST-eksportstruktur

Hvis du vælger denne eksportindstilling, organiseres det eksporterede indhold i følgende struktur:

- Summary.csv: Indeholder en oversigt over det indhold, der eksporteres fra korrektursættet

- Rodmappe: Denne mappe med navnet [Eksportnavn] x z.zip og gentages for hver ZIP-filpartition. Rodmappen indeholder følgende:
  
  - Export_load_file_x af z.csv: metadatafilen.
  
  - Advarsler og fejl x af z.csv: Denne fil indeholder oplysninger om fejl, der opstod under forsøg på at eksportere fra korrektursættet.
  
  - Exchange: Denne mappe indeholder alt indhold fra Exchange der er gemt i PST-filer. PDF-filer, der er redigeret med rødt, kan ikke inkluderes i denne indstilling. Hvis en vedhæftet fil er markeret i korrektursættet, eksporteres den overordnede mail med den vedhæftede fil.
  
    Mappen Exchange også indeholde en undermappe med navnet mailboxname_loosefiles.zip, som indeholder følgende elementer:

    - IRM (Information Rights Management) beskyttede meddelelser, der er blevet afkodet.
    - Meddelelser, der er afhjulpet af fejl.
    - Moderne vedhæftede filer eller links, der refereres til i meddelelser.
    - Krypterede elementer (som ikke er inkluderet i PST-filerne i Exchange mappen).
  
  - SharePoint: Denne mappe indeholder alt lokalt indhold SharePoint oprindelige filformat. PDF-filer, der er redigeret med rødt, kan ikke inkluderes i denne indstilling.

### <a name="condensed-directory-structure"></a>Komprimeret mappestruktur

- Summary.csv: Indeholder en oversigt over det indhold, der eksporteres fra korrektursættet

- Rodmappe: Denne mappe med navnet [Eksportnavn] x z.zip og gentages for hver ZIP-filpartition.
  
  - Export_load_file_x på z.csv: Metadatafilen samt placeringen af hver fil, der er gemt i ZIP-filen.
  
  - Advarsler og fejl x af z.csv: Denne fil indeholder oplysninger om fejl, der opstod under forsøg på at eksportere fra korrektursættet.

  - NativeFiles: Denne mappe indeholder alle de oprindelige filer, der blev eksporteret. Oprindelige filer erstattes med redigerede PDF-filer, hvis du har valgt indstillingen Erstat oprindelige oprindelige filer med *konverterede PDF-filer* .
  
  - Error_files: Denne mappe indeholder filer, der havde enten udtræk eller anden behandlingsfejl. Filerne placeres i separate mapper, enten UdtrækFejl eller BehandlerFejl. Disse filer er angivet i indlæsningsfilen.

  - Extracted_text_files: Denne mappe indeholder alle de udpakkede tekstfiler, der blev genereret under behandling.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Komprimeret mappestruktur eksporteret til din Azure Storage-konto

Denne indstilling anvender den samme generelle struktur som mappestrukturen Komprimeret *, men* indholdet komprimeres ikke, og dataene gemmes i din Azure Storage konto. Denne indstilling bruges normalt, når du arbejder med en tredjeparts eDiscovery-udbyder. Hvis du vil have mere at vide om, hvordan du bruger denne indstilling, [skal du se Eksportere dokumenter i et korrektursæt til Azure Storage konto](download-export-jobs.md).
