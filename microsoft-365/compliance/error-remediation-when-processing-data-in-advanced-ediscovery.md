---
title: Fejlafhjælpning under behandling af data
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
description: Få mere at vide om, hvordan du bruger fejlafhjælpning til at rette dataproblemer i eDiscovery (Premium), der kan forhindre korrekt behandling af indhold.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: e119458281a81ab41f8034ce76e65a5946536204
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093103"
---
# <a name="error-remediation-when-processing-data"></a>Fejlafhjælpning under behandling af data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Fejlafhjælpning giver eDiscovery-administratorer mulighed for at rette dataproblemer, der forhindrer Microsoft Purview eDiscovery (Premium) i at behandle indholdet korrekt. Filer, der er beskyttet med adgangskode, kan f.eks. ikke behandles, da filerne er låst eller krypteret. Ved hjælp af fejlafhjælpning kan eDiscovery-administratorer downloade filer med sådanne fejl, fjerne adgangskodebeskyttelsen og derefter uploade de afhjælpede filer.

Brug følgende arbejdsproces til at afhjælpe filer med fejl i eDiscovery-sager (Premium).

## <a name="create-an-error-remediation-session-to-remediate-files-with-processing-errors"></a>Opret en fejlafhjælpningssession for at afhjælpe filer med behandlingsfejl

> [!NOTE]
> Hvis guiden til fejlafhjælpning lukkes når som helst under følgende procedure, kan du vende tilbage til fejlafhjælpningssessionen under fanen **Behandling** ved at vælge **Afhjælpninger** i rullemenuen **Vis** .

1. Under fanen **Behandling** i eDiscovery-sagen (Premium) skal du vælge **Fejl** i rullemenuen **Vis** og derefter vælge et korrektursæt eller hele sagen i rullemenuen **Område**. I dette afsnit vises alle fejl fra sagen eller fejlen fra et bestemt korrektursæt.

   ![Fejlafhjælpning.](../media/8c2faf1a-834b-44fc-b418-6a18aed8b81a.png)

2. Vælg de fejl, du vil afhjælpe, ved at klikke på alternativknappen ud for enten fejltypen eller filtypen.  I følgende eksempel afhjælper vi en adgangskodebeskyttet fil.

3. Klik på **Ny fejlafhjælpning**.

    Arbejdsprocessen for fejlafhjælpning starter med en forberedelsesfase, hvor filerne med fejl kopieres til en Azure Storage placering, der er leveret af Microsoft, så du kan downloade dem til din lokale computer for at afhjælpe problemet.

    ![Forbereder fejlafhjælpning.](../media/390572ec-7012-47c4-a6b6-4cbb5649e8a8.png)

4. Når forberedelsen er fuldført, skal du klikke på **Næste: Download filer** for at fortsætte med overførslen.

    ![Download filer.](../media/6ac04b09-8e13-414a-9e24-7c75ba586363.png)

5. Hvis du vil downloade filer, skal du angive **destinationsstien til download**. Dette er en sti til den overordnede mappe på din lokale computer, hvor filen skal downloades.  Standardstien %USERPROFILE%\Downloads\errors peger på den mappe, som den bruger, der er logget på, henter. Du kan ændre denne sti, hvis det er nødvendigt. Hvis du ændrer den, anbefaler vi, at du bruger en lokal filsti for at opnå den bedste ydeevne. Brug ikke en sti til fjernnetværket. Du kan f.eks. bruge stien **C:\Remediation**.

   Stien til den overordnede mappe føjes automatisk til kommandoen AzCopy (som værdien for parameteren **/Dest** ).

6. Kopiér den foruddefinerede kommando ved at klikke på **Kopiér til Udklipsholder**. Åbn en Windows kommandoprompt, indsæt kommandoen AzCopy, og tryk derefter på **Enter**.

    ![Forbered fejlafhjælpning.](../media/f364ab4d-31c5-4375-b69f-650f694a2f69.png)

    > [!NOTE]
    > Du skal bruge AzCopy v8.1 for at kunne bruge den kommando, der er angivet på siden **Download filer** . Du skal også bruge AzCopy v8.1 til at overføre filerne i trin 10. Hvis du vil installere denne version af AzCopy, skal du se [Overfør data med AzCopy v8.1 på Windows](/previous-versions/azure/storage/storage-use-azcopy). Hvis den angivne AzCopy-kommando mislykkes, skal du se [Foretag fejlfinding af AzCopy i eDiscovery (Premium)](troubleshooting-azcopy.md).

    De filer, du har valgt, downloades til den placering, du angav i trin 5. I den overordnede mappe (f.eks. **C:\Remediation**) oprettes følgende undermappestruktur automatisk:

    `<Parent folder>\Subfolder 1\Subfolder 2\<file>`

    - *Undermappen 1* er navngivet med id'et for sagen eller gennemsynssættet, afhængigt af det område du valgte i trin 1.

    - *Undermappen 2* er navngivet med fil-id'et for den downloadede fil

    - Den downloadede fil er placeret i *undermappen 2* og er også navngivet med fil-id'et.

    Her er et eksempel på mappestien og det fejlfilnavn, der oprettes, når elementer downloades til den overordnede **mappe C:\Remediation** :

    `C:\Remediation\232f8b7e-089c-4781-88c6-210da0615d32\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938\d1459499146268a096ea20202cd029857d64087706e6d6ca2a224970ae3b8938.docx`

    Hvis der downloades flere filer, downloades hver enkelt til en undermappe med navnet med fil-id'et.

    > [!IMPORTANT]
    > Når du uploader filer i trin 9 og trin 10, skal de afhjælpede filer have det samme filnavn og være placeret i den samme undermappestruktur. Undermappen og filnavnene bruges til at knytte den afhjælpede fil til den oprindelige fejlfil. Hvis mappestrukturen eller filnavnene ændres, får du vist følgende fejl: `Cannot apply Error Remediation to the current Workingset`. For at forhindre problemer anbefales det, at de afhjælpede filer opbevares i den samme overordnede mappe og undermappestruktur.

7. Når du har downloadet filerne, kan du afhjælpe dem med et passende værktøj. For adgangskodebeskyttede filer er der flere værktøjer til at knække adgangskoder, du kan bruge. Hvis du kender adgangskoderne til filerne, kan du åbne dem og fjerne adgangskodebeskyttelsen.

8. Vend tilbage til eDiscovery (Premium) og guiden til fejlafhjælpning, og klik derefter på **Næste: Upload filer**.  Dette flyttes til næste side, hvor du nu kan uploade filerne.

    ![Upload Filer.](../media/af3d8617-1bab-4ecd-8de0-22e53acba240.png)

9. Angiv den overordnede mappe, hvor de afhjælpede filer er placeret i tekstfeltet **Sti til placering af filer** . Den overordnede mappe skal igen have den samme undermappestruktur, som blev oprettet, da du downloadede filerne.

    Stien til den overordnede mappe føjes automatisk til kommandoen AzCopy (som værdien for parameteren **/Source** ).

10. Kopiér den foruddefinerede kommando ved at klikke på **Kopiér til Udklipsholder**. Åbn en Windows kommandoprompt, indsæt kommandoen AzCopy, og tryk derefter på **Enter**. uploade filerne.

    ![Resultater af vellykket upload af afhjælpede filer i Azcopy.](../media/ff2ff691-629f-4065-9b37-5333f937daf6.png)

11. Når du har kørt kommandoen AzCopy, skal du klikke på **Næste: Behandl filer**.

    Når behandlingen er fuldført, kan du gå til gennemse sæt og få vist de afhjælpede filer.

## <a name="remediating-errors-in-container-files"></a>Afhjælpning af fejl i objektbeholderfiler

I situationer, hvor indholdet af en objektbeholderfil (f.eks. en .zip fil) ikke kan pakkes ud af eDiscovery (Premium), kan objektbeholderne hentes, og indholdet udvides til den samme mappe, som den oprindelige objektbeholder er placeret i. De udvidede filer tilskrives den overordnede objektbeholder, som om den oprindeligt blev udvidet med eDiscovery (Premium). Processen fungerer som beskrevet ovenfor med undtagelse af overførsel af en enkelt fil som erstatningsfil.  Når du uploader afhjælpede filer, skal du ikke inkludere den oprindelige objektbeholderfil.

## <a name="remediating-errors-by-uploading-the-extracted-text"></a>Afhjælpning af fejl ved at overføre den udtrukne tekst

Nogle gange er det ikke muligt at afhjælpe en fil til et oprindeligt format, som eDiscovery (Premium) kan fortolke. Men du kan erstatte den oprindelige fil med en tekstfil, der indeholder den oprindelige tekst i den oprindelige fil (i en proces, der kaldes *tekstoverlejring*). Det gør du ved at følge de trin, der er beskrevet i denne artikel, men i stedet for at afhjælpe den oprindelige fil i det oprindelige format skal du oprette en tekstfil, der indeholder den udtrukne tekst fra den oprindelige fil, og derefter uploade tekstfilen ved hjælp af det oprindelige filnavn, der er vedhæftet et .txt suffiks. Du downloader f.eks. en fil under fejlafhjælpning med filnavnet 335850cc-6602-4af0-acfa-1d14d9128ca2.abc. Du åbner filen i det oprindelige program, kopierer teksten og indsætter den derefter i en ny fil med navnet 335850cc-6602-4af0-acfa-1d14d9128ca2.abc.txt. Når du gør dette, skal du sørge for at fjerne den oprindelige fil i det oprindelige format fra den afhjælpede filplacering på din lokale computer, før du overfører den afhjælpede tekstfil til eDiscovery (Premium).

## <a name="what-happens-when-files-are-remediated"></a>Hvad sker der, når filer afhjælpes?

Når de afhjælpede filer uploades, bevares de oprindelige metadata med undtagelse af følgende felter:

- Udpakket tekststørrelse
- Har tekst
- IsErrorRemediate
- LoadId
- Behandlererrormeddelelse
- Status for behandling
- Tekst
- WordCount
- Arbejdssæt-id

Du kan finde en definition af alle metadatafelter i eDiscovery (Premium) under [Dokumentmetadatafelter](document-metadata-fields-in-advanced-ediscovery.md).