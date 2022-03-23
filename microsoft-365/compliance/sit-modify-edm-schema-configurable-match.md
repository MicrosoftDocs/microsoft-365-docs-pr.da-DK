---
title: Rediger skemaet for nøjagtig datamatching for at bruge konfigurerbart match
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du redigerer etedm-skema for at bruge match, der kan konfigureres.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf11e60f3fce46926d297c97a44c7d494942d556
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63592557"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Rediger skemaet for nøjagtig datamatching for at bruge konfigurerbart match

Den nøjagtige EDM-baserede klassificering (Data Match) gør det muligt at oprette brugerdefinerede typer af følsomme oplysninger, der refererer til nøjagtige værdier i en database med følsomme oplysninger. Når du har brug for at tillade varianter af en præcis streng, kan du bruge  et match, der kan konfigureres, til at Microsoft 365 at ignorere store og små bogstaver og nogle afgrænsere.

> [!IMPORTANT]
> Brug denne fremgangsmåde til at redigere et eksisterende EDM-skema og en eksisterende datafil.

1. FjernEdmUploadAgent.exe **fra** den computer, du bruger til at oprette forbindelse Microsoft 365 til brug for overførsel af EDM-skema og datafil.

2. Download den relevante **EdmUploadAgent.exe** til dit abonnement ved hjælp af nedenstående links:
    - [Kommerciel + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) - de fleste kommercielle kunder skal bruge dette
    - [GCC-High –](https://go.microsoft.com/fwlink/?linkid=2137521) Dette er specifikt for skyabonn abonnenter på den offentlige højsikkerhed
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) – dette er specifikt for kunder fra det amerikanske forsvarsministerium i skyen

3. Godkend EDM Upload agent, åbn et kommandopromptvindue (som administrator), og kør følgende kommando:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. Hvis du ikke har en aktuel kopi af det eksisterende skema, skal du hente en kopi af det eksisterende skema ved at køre denne kommando:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. Tilpas skemaet, så hver kolonne benytter "caseInsensitive" og/ eller "ignoreredeAfgrænsere".  Standardværdien for "caseInsensitive" er "false", og for "ignoreredeafgrænsere" er det en tom streng.

    > [!NOTE]
    > Den underliggende brugerdefinerede følsomme oplysningstype eller den indbyggede type af følsomme oplysninger, der bruges til at registrere det generelle regex-mønster, skal understøtte registrering af de variationer, der er angivet med ignoreredeAfgrænsere. Den indbyggede amerikanske CPR-nummer (SSN) af følsomme oplysninger kan f.eks. registrere variationer i de data, der indeholder tankestreger, mellemrum eller manglende mellemrum mellem de grupperede tal, der udgør CPR-nummeret. Derfor er de eneste afgrænsere, der er relevante for at medtage i EDM's ignoreredeAfgrænsere for SSN-data: bindestreg og mellemrum.

    Her er et eksempelskema, der simulerer forskel på store og små bogstaver ved at oprette de ekstra kolonner, der skal bruges til at genkende forskel på store og små bogstaver i de følsomme data.

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
               <Field name="PolicyNumber" searchable="true" />
               <Field name="PolicyNumberLowerCase" searchable="true" />
               <Field name="PolicyNumberUpperCase" searchable="true" />
               <Field name="PolicyNumberCapitalLetters" searchable="true" />
      </DataStore>
    </EdmSchema>
    ```

    I eksemplet ovenfor vil variationer af den oprindelige kolonne `PolicyNumber` ikke længere være nødvendige, hvis begge er `caseInsensitive` tilføjet `ignoredDelimiters` .

    Hvis du vil opdatere dette skema, så EDM bruger konfigurerbar match, skal du `caseInsensitive` bruge `ignoredDelimiters` flag og .  Sådan ser det ud:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    Flaget `ignoredDelimiters` understøtter alle ikke-alfanumeriske tegn. Her er nogle eksempler:
    - \.
    - \-
    - \/
    - \_
    - \*
    - \^
    - \#
    - \!
    - \?
    - \[
    - \]
    - \{
    - \}
    - \\
    - \~
    - \;

    Flaget `ignoredDelimiters` understøtter ikke:
    - tegn 0-9
    - A-Z
    - a-z
    - \"
    - \,

6. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > Hvis din organisation har konfigureret kundenøgle [til Microsoft 365 på](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) lejerniveau (offentlig prøveversion) vil den nøjagtige dataoverensstemmelse automatisk gøre brug af dens krypteringsfunktionalitet. Dette er kun tilgængeligt for E5-licenserede lejere i den kommercielle sky.

7. Opdater dit skema ved at køre følgende kommando:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. Hvis det er nødvendigt, skal du opdatere datafilen, så den svarer til den nye skemaversion.

    > [!TIP]
    > Du kan også køre en validering af CSV-filen, før du uploader, ved at køre:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > Du kan finde flere oplysninger om alle EdmUploadAgent.exe understøttede parametre ved at køre
    >
    > `EdmUploadAgent.exe /?`

9. Åbn vinduet Kommandoprompt (som administrator), og kør følgende kommando for at hashtagle og overføre dine følsomme data:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>Relaterede artikler

- [Få mere at vide om nøjagtige dataoverensstemmelsesbaserede typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Definitioner af følsomme oplysningstypeenhed](sensitive-information-type-entity-definitions.md)
- [Brugerdefinerede typer af følsomme oplysninger](./sensitive-information-type-learn-about.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Microsoft Defender til skyapps](/cloud-app-security)
- [New-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
