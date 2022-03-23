---
title: Eksportér dokumenter til din organisations Azure Storage konto
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
ms.custom: seo-marvel-mar2020
description: Eksportér dokumenter i et korrektursæt til en Azure Storage-konto, og brug Azure Storage Stifinder til at hente dem til en lokal computer.
ms.openlocfilehash: 8f3110ef386fd5c5d8adc641aa223435caf0da67
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589508"
---
# <a name="export-documents-in-a-review-set-to-an-azure-storage-account"></a>Eksportere dokumenter i et korrektursæt til en Azure Storage konto

Når du eksporterer dokumenter fra et korrektursæt i en Advanced eDiscovery-sag, har du mulighed for at eksportere dem til en Azure Storage-konto, der administreres af din organisation. Hvis du bruger denne indstilling, uploades dokumenterne til din Azure Storage placering. Når de er eksporteret, kan du få adgang til dokumenterne (og hente dem til en lokal computer eller et andet sted) ved hjælp af Azure Storage Stifinder. Denne artikel indeholder instruktioner om, hvordan du eksporterer dokumenter til din Azure Storage-konto, og hvordan du bruger Azure Storage Stifinder til at oprette forbindelse til en Azure Storage-placering for at hente de eksporterede dokumenter. Du kan finde flere oplysninger Azure Storage Stifinder i [Brug Azure Storage Stifinder](/azure/storage/blobs/storage-quickstart-blobs-storage-explorer).

## <a name="before-you-export-documents-from-a-review-set"></a>Før du eksporterer dokumenter fra et korrektursæt

- Du skal angive et SAS-token (Shared Access Signature) for din Azure Storage-konto og URL-adressen til en bestemt beholder på lagerkontoen for at eksportere dokumenter fra et korrektursæt. Sørg for at have disse lige ved hånden (f.eks. kopieret til en tekstfil), når du udfører trin 2

  - **SAS-token**: Sørg for, at SAS-token er til din Azure Storage -konto (og ikke for beholderen). Du kan generere et SAS-token for din konto Azure Storage. For at gøre dette skal du gå til Azure Storage-kontoen og vælge **Del adgangssignatur** **under** Indstillinger i lagerkontoens blade. Brug standardindstillingerne, og tillad alle ressourcetyper, når du genererer SAS-tokenet.

  - **URL-adresse** for objektbeholder: Du skal oprette en beholder til at overføre dokumentet i korrektursættet til og derefter få en kopi af URL-adressen for beholderen. f.eks. `https://ediscoverydata.blob.core.windows.net/exportdata`. For at få URL-adressen skal du gå til beholderen i Azure Storage og vælge **Egenskaber** **Indstillinger sektionen** i objektbeholderens blade.

- Download og installér Azure Storage Stifinder. Du kan finde en vejledning [Azure Storage Stifinder-værktøjet](https://go.microsoft.com/fwlink/p/?LinkId=544842). Du bruger dette værktøj til at oprette forbindelse til beholderen i din Azure Storage-konto og hente de dokumenter, du eksporterede i trin 1.

## <a name="step-1-export-the-documents-from-a-review-set"></a>Trin 1: Eksportér dokumenterne fra et korrektursæt

Det første trin er at oprette et eksportjob for at eksportere dokumenter ud af et korrektursæt. Hvis du vil have mere at vide om alle eksportindstillingerne, skal [du se Eksportere dokumenter fra et korrektursæt](export-documents-from-review-set.md). Følgende procedure fremhæver indstillingerne for at eksportere dokumenter til din organisations Azure Storage konto.

1. I Microsoft 365 Overholdelsescenter skal du åbne Advanced eDiscovery store og små bogstaver, vælge fanen Gennemse sæt og  derefter vælge det korrektursæt, du vil eksportere.

2. I korrektursættet skal du klikke **på** **ActionExport** > .

3. På pop **op-siden** Eksportindstillinger skal du skrive et navn (påkrævet) og en beskrivelse (valgfrit) til eksporten.

4. Konfigurer indstillingerne i sektionerne dokumenter, metadata, indhold og indstillinger. Du kan finde flere oplysninger om disse indstillinger i [Eksportere dokumenter fra et korrektursæt](export-documents-from-review-set.md).

5. I sektionen **Outputindstillinger** skal du vælge indstillingen **Komprimeret mappestruktur eksporteret til din Azure Storage-konto**.

6. Indsæt objektbeholderens URL-adresse og SAS-token for din lagerkonto i de tilsvarende felter.

   ![Indsæt forbindelsens URL-adresse og SAS-token i de tilsvarende felter.](../media/AzureStorageOutputOptions.png)

7. Klik **på Eksportér** for at oprette eksportjobbet.

## <a name="step-2-obtain-the-sas-url-from-the-export-job"></a>Trin 2: Hent SAS URL-adressen fra eksportjobbet

Næste trin er at få SAS URL-adressen, der genereres, efter at du har oprettet eksportjobbet i trin 1. Du kan bruge SAS URL-adressen til at oprette forbindelse til beholderen på din Azure Storage, som du eksporterede dokumenterne til gennemsynssættet til.

1. På siden **Advanced eDiscovery** skal du gå til sagen og derefter klikke på **fanen Eksporter**.

2. Klik på **det** eksportjob, du vil downloade, under fanen Eksporter. Dette er det eksportjob, du oprettede i trin 1.

3. Kopiér SAS URL-adressen, **der vises**, under Placeringer på pop op-siden. Hvis det er nødvendigt, kan du gemme den i en tekstfil, så du kan få adgang til den i trin 3.

   ![Kopiér SAS URL-adressen, der vises under Placeringer.](../media/eDiscoExportJob.png)

   > [!TIP]
   > SAS-URL-adressen, der vises i eksportjobbet, er en sammenk følge af CONTAINER URL-adressen og SAS-tokenet for din Azure Storage konto. Du kan kopiere den fra eksportjobbet eller oprette den selv ved at kombinere URL-adressen og SAS-tokenet.

## <a name="step-3-connect-to-the-azure-storage-container"></a>Trin 3: Forbind til Azure Storage objektbeholder

Det sidste trin er at bruge Azure Storage Explorer og SAS URL til at oprette forbindelse til beholderen i din Azure Storage-konto og hente de eksporterede dokumenter til en lokal computer.

1. Start den Azure Storage, du har downloadet og installeret.

2. Klik på **Forbind Åbn dialogboks**.

   ![Klik på ikonet Tilføj konto.](../media/AzureStorageConnect.png)

3. På siden **Forbind for Azure Storage** skal du klikke på **Blob-objektbeholder**.

4. På siden **Vælg godkendelsesmetode skal** du vælge indstillingen **SAS -signatur (Shared Access Signature),** og derefter skal du klikke på **Næste**.

5. På siden **Angiv forbindelsesoplysninger** skal du indsætte SAS URL-adressen (som du fik i eksportjobbet i trin 2) i **feltet BLob Container SAS URL-adresse** .

    ![Indsæt SAS URL-adressen i URI-feltet.](../media/AzureStorageConnect3.png)

    Bemærk, at objektbeholderens navn vises i **feltet Vist** navn. Du kan redigere dette navn.

6. Klik **på Næste** for at få **vist oversigtssiden**, og klik **derefter Forbind**.

    **Noden Blob-objektbeholdere** (**under Storage Accounts** > **(Attached Containers)** \> åbnes.

    ![Eksportér jobs i noden Blobs-objektbeholdere.](../media/AzureStorageConnect5.png)

    Den indeholder en objektbeholder navngivet med visningsnavnet fra trin 5. Denne beholder indeholder en mappe for hvert eksportjob, du har downloadet til beholderen på din Azure Storage konto. Disse mapper navngives med et id, der svarer til id'et for eksportjobbet. Du kan finde disse eksport-lD'er (og navnet på eksporten) under **Supportoplysninger** på pop op-siden for hvert  forberedelsesdata til eksportjob, der er  angivet på fanen Jobs i Advanced eDiscovery-tilfældet.

7. Dobbeltklik på eksportjobmappen for at åbne den.

   Der vises en liste over mapper og eksportrapporter.

    ![Eksportmappen indeholder eksporterede filer og eksportrapporter.](../media/AzureStorageConnect6.png)

8. Hvis du vil eksportere alt indhold fra eksportjobbet,  skal du klikke på pil op for at gå tilbage til eksportjobmappen og derefter klikke på **Hent**.

9. Angiv den placering, hvor du vil hente de eksporterede filer, og klik derefter på Vælg mappe.

    Den Azure Storage Stifinder starter downloadprocessen. Status for hentning af de eksporterede elementer vises i **ruden** Aktiviteter. Der vises en meddelelse, når overførslen er fuldført.

> [!NOTE]
> I stedet for at downloade hele eksportjobbet Azure Storage Stifinder, kan du vælge specifikke elementer, der skal downloades og vises.

## <a name="more-information"></a>Flere oplysninger

- Eksportjobmappen indeholder følgende elementer. De faktiske elementer i eksportmappen bestemmes af de eksportindstillinger, der blev konfigureret, da eksportjobbet blev oprettet. Få mere at vide om disse indstillinger under [Eksportér dokumenter fra et korrektursæt](export-documents-from-review-set.md).

  - Export_load_file.csv: Denne CSV-fil er en detaljeret eksportrapport, der indeholder oplysninger om hvert eksporterede dokument. Filen består af en kolonne for hver metadataegenskab til et dokument. Du kan finde en liste og beskrivelse af de metadata, der er inkluderet i denne rapport, i kolonnen Eksporteret feltnavn i tabellen i [Dokumentmetadatafelter i Advanced eDiscovery](document-metadata-fields-in-advanced-ediscovery.md).

  - Summary.txt: En tekstfil, der indeholder en oversigt over eksporten, herunder eksportstatistik.

  - Extracted_text_files: Denne mappe indeholder en tekstfilversion af hvert eksporterede dokument.

  - NativeFiles: Denne mappe indeholder en oprindelig filversion af hvert eksporterede dokument.

  - Error_files: Denne mappe indeholder følgende elementer, når eksportjobbet indeholder fejlfiler:

    - ExtractionError.csv: Denne CSV-fil indeholder de tilgængelige metadata for filer, der ikke blev hentet korrekt fra deres overordnede element.

    - Behandlerfejl: Denne mappe indeholder dokumenter med behandlingsfejl. Dette indhold er på et elementniveau, hvilket betyder, at hvis en vedhæftet fil havde en behandlingsfejl, medtages det dokument, der indeholder den vedhæftede fil, også i denne mappe.
