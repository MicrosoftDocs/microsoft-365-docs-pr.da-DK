---
title: Eksportér dokumenter til en Azure Storage-konto til en organisation
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
ms.custom: seo-marvel-mar2020
description: Eksportér dokumenter i et korrektursæt til en Azure Storage-konto, og brug derefter Azure Storage Explorer til at downloade dem til en lokal computer.
ms.openlocfilehash: 87e7f04f2e21becb5320c3bca999d7e0ff4900b2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626485"
---
# <a name="export-documents-in-a-review-set-to-an-azure-storage-account"></a>Eksportér dokumenter i et korrektursæt til en Azure Storage-konto

Når du eksporterer dokumenter fra et korrektursæt i en eDiscovery(Premium)-sag, har du mulighed for at eksportere dem til en Azure Storage-konto, der administreres af din organisation. Hvis du bruger denne indstilling, uploades dokumenterne til din Azure Storage-placering. Når de er eksporteret, kan du få adgang til dokumenterne (og downloade dem til en lokal computer eller en anden placering) ved hjælp af Azure Storage Explorer. Denne artikel indeholder instruktioner til, hvordan du eksporterer dokumenter til din Azure Storage-konto og bruger Azure Storage Explorer til at oprette forbindelse til en Azure Storage-placering for at downloade de eksporterede dokumenter. Du kan få flere oplysninger om Azure Storage Explorer under [Brug Azure Storage Explorer](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer).

## <a name="before-you-export-documents-from-a-review-set"></a>Før du eksporterer dokumenter fra et korrektursæt

- Du skal angive et SAS-token (shared access signature) for din Azure Storage-konto og URL-adressen for en bestemt objektbeholder på lagerkontoen for at eksportere dokumenter fra et gennemsynssæt. Sørg for at have disse ved hånden (f.eks. kopieret til en tekstfil), når du udfører trin 2

  - **SAS-token**: Sørg for at få SAS-tokenet er til din Azure Storage-konto (og ikke til objektbeholderen). Du kan generere et SAS-token for din konto i Azure Storage. Det gør du ved at gå til Azure Storage-kontoen og vælge **Del adgangssignatur** under indstillingerne under bladet **Indstillinger** på bladet Lagerkonto. Brug standardindstillingerne, og tillad alle ressourcetyper, når du genererer SAS-tokenet.

  - **URL-adresse til objektbeholder**: Du skal oprette en objektbeholder for at uploade de dokumenter, der er angivet til gennemsyn, og derefter hente en kopi af URL-adressen til objektbeholderen. f.eks. `https://ediscoverydata.blob.core.windows.net/exportdata`. Hvis du vil hente URL-adressen, skal du gå til objektbeholderen i Azure Storage og vælge **Egenskaber** under afsnittet **Indstillinger** på beholderbladet.

- Download og installér Azure Storage Explorer. Du kan finde instruktioner i [Værktøjet Azure Storage Explorer](https://go.microsoft.com/fwlink/p/?LinkId=544842). Du kan bruge dette værktøj til at oprette forbindelse til objektbeholderen på din Azure Storage-konto og downloade de dokumenter, du eksporterede i trin 1.

## <a name="step-1-export-the-documents-from-a-review-set"></a>Trin 1: Eksportér dokumenterne fra et gennemsynssæt

Det første trin er at oprette et eksportjob for at eksportere dokumenter ud af et gennemsynssæt. Du kan finde mere detaljerede instruktioner om alle eksportindstillingerne under [Eksportér dokumenter fra et gennemsynssæt](export-documents-from-review-set.md). I følgende procedure fremhæves indstillingerne for eksport af dokumenter til din organisations Azure Storage-konto.

1. I Microsoft Purview-compliance-portal skal du åbne sagen eDiscovery (Premium), vælge fanen **Gennemse sæt** og derefter vælge det korrektursæt, du vil eksportere.

2. Klik på **Handlingseksport** >  i korrektursættet.

3. Skriv et navn (obligatorisk) og en beskrivelse (valgfrit) for eksporten på siden **Eksportindstillinger** .

4. Konfigurer indstillingerne i sektionerne dokumenter, metadata, indhold og indstillinger. Du kan finde flere oplysninger om disse indstillinger under [Eksportér dokumenter fra et korrektursæt](export-documents-from-review-set.md).

5. I afsnittet **Outputindstillinger** skal du vælge indstillingen **Komprimeret mappestruktur, der eksporteres til din Azure Storage-konto** .

6. Indsæt objektbeholderens URL-adresse og SAS-tokenet for din lagerkonto i de tilsvarende felter.

   ![Indsæt URL-adressen til forbindelsen og SAS-tokenet i de tilsvarende felter.](../media/AzureStorageOutputOptions.png)

7. Klik på **Eksportér** for at oprette eksportjobbet.

## <a name="step-2-obtain-the-sas-url-from-the-export-job"></a>Trin 2: Hent SAS URL-adressen fra eksportjobbet

Det næste trin er at hente den SAS-URL-adresse, der genereres, når du har oprettet eksportjobbet i trin 1. Du kan bruge SAS URL-adressen til at oprette forbindelse til objektbeholderen på din Azure Storage-konto, som du eksporterede gennemsynssættet dokumenter til.

1. Gå til sagen på siden **eDiscovery (Premium),** og klik derefter på fanen **Eksporter** .

2. Klik på det eksportjob, du vil downloade, under fanen **Eksporter** . Dette er det eksportjob, du oprettede under trin 1.

3. Kopiér den SAS-URL-adresse, der vises, under **Placeringer** på pop op-siden. Hvis det er nødvendigt, kan du gemme den i en tekstfil, så du kan få adgang til den i trin 3.

   ![Kopiér den SAS-URL-adresse, der vises under Placeringer.](../media/eDiscoExportJob.png)

   > [!TIP]
   > DEN SAS-URL-adresse, der vises i eksportjobbet, er en sammenkædning af URL-adressen til objektbeholderen og SAS-tokenet for din Azure Storage-konto. Du kan kopiere det fra eksportjobbet eller selv oprette det ved at kombinere URL-adressen og SAS-tokenet.

## <a name="step-3-connect-to-the-azure-storage-container"></a>Trin 3: Opret forbindelse til Azure Storage-objektbeholderen

Det sidste trin er at bruge Azure Storage Explorer og SAS URL-adressen til at oprette forbindelse til objektbeholderen på din Azure Storage-konto og downloade de eksporterede dokumenter til en lokal computer.

1. Start Azure Storage Explorer, som du har downloadet og installeret.

2. Klik på ikonet **Åbn dialogboksen Opret forbindelse** .

   ![Klik på ikonet Tilføj konto.](../media/AzureStorageConnect.png)

3. Klik på **Blob-objektbeholder** på siden **Opret forbindelse til Azure Storage**.

4. På siden **Vælg godkendelsesmetode** skal du vælge indstillingen **Delt adgangssignatur (SAS)** og derefter klikke på **Næste**.

5. På siden **Angiv forbindelsesoplysninger** skal du indsætte SAS URL-adressen (som du fik i eksportjobbet i trin 2) i feltet **URL-adresse til Blob Container SAS** .

    ![Indsæt SAS URL-adressen i URI-feltet.](../media/AzureStorageConnect3.png)

    Bemærk, at objektbeholdernavnet vises i feltet **Vist navn** . Du kan redigere dette navn.

6. Klik på **Næste** for at få vist **oversigtssiden** , og klik derefter på **Opret forbindelse**.

    Noden **BLOB-objektbeholdere** (under **Lagerkonti** >  **(vedhæftede objektbeholdere)** \> åbnes.

    ![Eksportér job i noden Blobs-objektbeholdere.](../media/AzureStorageConnect5.png)

    Den indeholder en objektbeholder, der er navngivet med det viste navn fra trin 5. Denne objektbeholder indeholder en mappe til hvert eksportjob, du har downloadet til objektbeholderen på din Azure Storage-konto. Disse mapper er navngivet med et id, der svarer til id'et for eksportjobbet. Du kan finde disse eksport-id'er (og navnet på eksporten) under **Supportoplysninger** på pop op-siden for hver **Forbereder data til eksportjob** , der er angivet under fanen **Job** i eDiscovery (Premium).

7. Dobbeltklik på mappen med eksportjobbet for at åbne den.

   Der vises en liste over mapper og eksportrapporter.

    ![Eksportmappen indeholder eksporterede filer og eksportrapporter.](../media/AzureStorageConnect6.png)

8. Hvis du vil eksportere alt indhold fra eksportjobbet, skal du klikke på pil **op** for at gå tilbage til mappen med eksportjobbet og derefter klikke på **Download**.

9. Angiv den placering, hvor du vil hente de eksporterede filer, og klik derefter på Vælg mappe.

    Azure Storage Explorer starter downloadprocessen. Status for overførslen af de eksporterede elementer vises i ruden **Aktiviteter** . Der vises en meddelelse, når overførslen er fuldført.

> [!NOTE]
> I stedet for at downloade hele eksportjobbet i Azure Storage Explorer kan du vælge bestemte elementer, der skal downloades og vises.

## <a name="more-information"></a>Flere oplysninger

- Mappen til eksportjobbet indeholder følgende elementer. De faktiske elementer i eksportmappen bestemmes af de eksportindstillinger, der blev konfigureret, da eksportjobbet blev oprettet. Du kan finde flere oplysninger om disse indstillinger under [Eksportér dokumenter fra et korrektursæt](export-documents-from-review-set.md).

  - Export_load_file.csv: Denne CSV-fil er en detaljeret eksportrapport, der indeholder oplysninger om hvert eksporteret dokument. Filen består af en kolonne for hver metadataegenskab for et dokument. Du kan finde en liste over og en beskrivelse af de metadata, der er inkluderet i denne rapport, i kolonnen **Med det eksporterede feltnavn** i tabellen i [Felterne Dokumentmetadata i eDiscovery (Premium)](document-metadata-fields-in-advanced-ediscovery.md).

  - Summary.txt: En tekstfil, der indeholder en oversigt over eksporten, herunder eksportstatistik.

  - Extracted_text_files: Denne mappe indeholder en tekstfilversion af hvert eksporteret dokument.

  - NativeFiles: Denne mappe indeholder en oprindelig filversion af hvert eksporteret dokument.

  - Error_files: Denne mappe indeholder følgende elementer, når eksportjobbet indeholder fejlfiler:

    - ExtractionError.csv: Denne CSV-fil indeholder de tilgængelige metadata for filer, der ikke blev udtrukket korrekt fra deres overordnede element.

    - ProcessingError: Denne mappe indeholder dokumenter med behandlingsfejl. Dette indhold er på elementniveau, hvilket betyder, at hvis en vedhæftet fil havde en behandlingsfejl, medtages det dokument, der indeholder den vedhæftede fil, også i denne mappe.
