---
title: Fejl der afhjælpes ved behandling af data
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
description: Få mere at vide om, hvordan du bruger fejl afhjælpning til at rette dataproblemer i Advanced eDiscovery der kan forhindre korrekt behandling af indhold.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: d0dabe5a16ff2b9b67b5f282401806daff8f82ea
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588933"
---
# <a name="error-remediation-when-processing-data"></a>Fejl der afhjælpes ved behandling af data

Fejl afhjælpning giver eDiscovery-administratorer mulighed for at udbedre dataproblemer, der Advanced eDiscovery i at blive behandlet indholdet korrekt. Filer, der er beskyttet med adgangskode, kan f.eks. ikke behandles, da filerne er låst eller krypteret. Ved hjælp af fejl afhjælpning kan eDiscovery-administratorer downloade filer med sådanne fejl, fjerne adgangskodebeskyttelsen og derefter uploade de afhjælpede filer.

Brug følgende arbejdsproces til at løse filer med fejl i Advanced eDiscovery tilfælde.

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>Opret en session til afhjælpning af fejl for at løse filer med behandlingsfejl

> [!NOTE]
> Hvis guiden til afhjælpning af fejl er lukket på et hvilket som helst tidspunkt i den følgende procedure, kan du vende tilbage til sessionen til afhjælpning  af fejl ved at vælge  Afhjælpninger i rullemenuen Vis.

1. På fanen **Behandler** i Advanced eDiscovery-sag skal du vælge Fejl i rullemenuen Vis og derefter  vælge et korrektursæt eller hele sagen i rullemenuen Omfang.  I dette afsnit vises alle fejl fra sagen eller fejlen fra et bestemt gennemsynssæt.

   ![Fejl afhjælpning.](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Vælg de fejl, du vil løse, ved at klikke på alternativknappen ud for enten fejltypen eller filtypen.  I følgende eksempel afhjælper vi en adgangskodebeskyttet fil.

3. Klik **på Ny fejl afhjælpning**.

    Arbejdsprocessen til afhjælpning af fejl starter med en forberedelsesfase, hvor filerne med fejl kopieres til en placering, som Microsoft har leveret Azure Storage, så du kan downloade dem til din lokale computer for at afhjælpe problemet.

    ![Forbereder fejl afhjælpning.](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Når klargøringen er fuldført, skal du klikke **på Næste: Hent filer** for at fortsætte med overførslen.

    ![Download filer.](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Hvis du vil downloade filer, skal du **angive destinationsstien til hentning**. Dette er en sti til den overordnede mappe på din lokale computer, hvor filen downloades.  Standardstien, %BRUGERPROFIL%\Downloads\fejl, peger på den loggede brugers downloadmappe. Du kan ændre denne sti efter behov. Hvis du ændrer det, anbefaler vi, at du bruger en lokal filsti for at opnå den bedste ydeevne. Brug ikke en ekstern netværkssti. Du kan f.eks. bruge stien **C:\Afhjælpning**.

   Stien til den overordnede mappe føjes automatisk til kommandoen AzCopy (som værdien af **parameteren /Dest** ).

6. Kopiér den foruddefinerede kommando ved at klikke på Kopiér **til Udklipsholder**. Åbn en Windows kommandoprompt, indsæt kommandoen AzCopy, og tryk derefter på **Enter**.

    ![Forberede afhjælpning af fejl.](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)

    > [!NOTE]
    > Du skal bruge AzCopy v8.1 for at kunne bruge den kommando, der findes på **siden Download** filer. Du skal også bruge AzCopy v8.1 til at overføre filerne i trin 10. Hvis du vil installere denne version af AzCopy, [skal du se Overfør data med AzCopy v8.1 Windows](/previous-versions/azure/storage/storage-use-azcopy). Hvis den medfølgende AzCopy-kommando mislykkes, skal [du se Fejlfinding af AzCopy Advanced eDiscovery](troubleshooting-azcopy.md).

    De markerede filer hentes til den placering, du angav i trin 5. I den overordnede mappe (f.eks. **C:\Afhjælpning**) oprettes følgende undermappestruktur automatisk:

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - *Undermappe 1 navngives* med id'et for sagen eller gennemsynssættet afhængigt af det omfang, du valgte i trin 1.

    - *Undermappe 2 navngives* med fil-id'et for den hentede fil

    - Den hentede fil er placeret *i Undermappe 2* og er også navngivet med fil-id'et.

    Her er et eksempel på mappestien og fejlfilnavnet, der oprettes, når elementer downloades til den overordnede **mappe C:\Afhjælpning** :

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Hvis der hentes flere filer, hentes hver af dem til en undermappe, der er navngivet med fil-id'et.

    > [!IMPORTANT]
    > Når du overfører filer i trin 9 og trin 10, skal de afhjælpede filer have det samme filnavn og være placeret i den samme undermappestruktur. Undermappen og filnavnene bruges til at knytte den afhjælpede fil til den oprindelige fejlfil. Hvis mappestrukturen eller filnavnene ændres, får du vist følgende fejlmeddelelse: `Cannot apply Error Remediation to the current Workingset`. Hvis du vil forhindre problemer, anbefaler vi, at de afhjælpede filer bevares i den samme overordnede mappe og undermappestruktur.

7. Når du har downloadet filerne, kan du afhjælpe dem med et passende værktøj. For filer, der er beskyttet med adgangskode, er der flere forskellige værktøjer, du kan bruge til at revne adgangskoder. Hvis du kender adgangskoderne til filerne, kan du åbne dem og fjerne adgangskodebeskyttelsen.

8. Gå tilbage Advanced eDiscovery og guiden til afhjælpning af fejl, og klik derefter **på Næste: Upload filer**.  Dette flytter til næste side, hvor du nu kan overføre filerne.

    ![Upload Filer.](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Angiv den overordnede mappe, hvor de afhjælpede filer er placeret i **tekstfeltet Sti til placering af** filer. Den overordnede mappe skal igen have den samme struktur i undermappen, som blev oprettet, da du hentede filerne.

    Stien til den overordnede mappe føjes automatisk til kommandoen AzCopy (som værdien af **parameteren /Source** ).

10. Kopiér den foruddefinerede kommando ved at klikke på Kopiér **til Udklipsholder**. Åbn en Windows kommandoprompt, indsæt kommandoen AzCopy, og tryk derefter på **Enter**. overføre filerne.

    ![Resultaterne af vellykket upload af afhjælpede filer i Azcopy.](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. Når du har kørt kommandoen AzCopy, skal du klikke **på Næste: Bearbejde filer**.

    Når behandlingen er fuldført, kan du gå til at gennemgå sættet og få vist de afhjælpede filer.

## <a name="remediating-errors-in-container-files"></a>Løse fejl i objektbeholderfiler

I situationer, hvor indholdet af en objektbeholderfil (f.eks. en .zip-fil) ikke kan udtrækkes af Advanced eDiscovery, kan objektbeholderne downloades, og indholdet udvides til den samme mappe, som den oprindelige beholder er placeret i. De udvidede filer vil blive tildelt den overordnede objektbeholder, som om den oprindeligt blev udvidet af Advanced eDiscovery. Processen fungerer som beskrevet ovenfor med undtagelse af overførsel af en enkelt fil som erstatningsfil.  Når du uploader afhjælpede filer, skal du ikke medtage den oprindelige objektbeholderfil.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Løse fejl ved at overføre den udpakkede tekst

Nogle gange er det ikke muligt at løse en fil til oprindelige formater, som Advanced eDiscovery kan fortolke. Men du kan erstatte den oprindelige fil med en tekstfil, der indeholder den oprindelige tekst fra den oprindelige fil (i en proces *kaldet tekstoverlejring*). Det gør du ved at følge de trin, der er beskrevet i denne artikel, men i stedet for at rette den oprindelige fil i det oprindelige format, skal du oprette en tekstfil, der indeholder den udpakkede tekst fra den oprindelige fil, og derefter overføre tekstfilen ved hjælp af det oprindelige filnavn, der er føjet til et .txt-suffiks. Du downloader f.eks. en fil under fejl afhjælpning med filnavnet 335850cc-6602-4af0-acfa-1d14d9128ca2.abc. Du åbner filen i det oprindelige program, kopierer teksten og indsætter den derefter i en ny fil med navnet 335850cc-6602-4af0-acfa-1d14d9128ca2.abc.txt. Når du gør dette, skal du sørge for at fjerne den oprindelige fil i det oprindelige format fra den afhjælpede filplacering på din lokale computer, før du overfører den afhjælpede tekstfil for at Advanced eDiscovery.

## <a name="what-happens-when-files-are-remediated"></a>Hvad sker der, når filer afhjælpes

Når afhjælpningsfiler overføres, bevares de oprindelige metadata med undtagelse af følgende felter:

- UdpakketTekstStørrelse
- HasText
- IsErrorRemediate
- LoadId
- ProcessingErrorMessage
- ProcessingStatus
- Tekst
- WordCount
- WorkingsetId

Du kan finde en definition af alle metadatafelter Advanced eDiscovery i Felterne [Dokumentmetadata](document-metadata-fields-in-advanced-ediscovery.md).