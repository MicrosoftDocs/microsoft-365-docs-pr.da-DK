---
title: Rediger skemaet for nøjagtigt datamatch, så der bruges konfigurerbart match
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
description: Få mere at vide om, hvordan du ændrer et edm-skema, så det bruger konfigurerbart match.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a90f81136bf6aa78aa11d732deca19ecd1d59b9c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622057"
---
# <a name="modify-exact-data-match-schema-to-use-configurable-match"></a>Rediger skemaet for nøjagtigt datamatch, så der bruges konfigurerbart match

EDM-baseret klassificering (Exact Data Match) giver dig mulighed for at oprette brugerdefinerede typer følsomme oplysninger, der refererer til nøjagtige værdier i en database med følsomme oplysninger. Når du har brug for at tillade varianter af en nøjagtig streng, kan du bruge *konfigurerbart match* til at bede Microsoft Purview om at ignorere store og små bogstaver og nogle afgrænsere.

> [!IMPORTANT]
> Brug denne procedure til at redigere et eksisterende EDM-skema og en eksisterende datafil.

1. Fjern **EdmUploadAgent.exe** fra den computer, du bruger til at oprette forbindelse til Microsoft 365 til EDM-skema og overførsel af datafiler.

2. Download den relevante **EdmUploadAgent.exe** fil til dit abonnement ved hjælp af nedenstående links:
    - [Commercial + GCC](https://go.microsoft.com/fwlink/?linkid=2088639) – de fleste kommercielle kunder skal bruge dette
    - [GCC-High](https://go.microsoft.com/fwlink/?linkid=2137521) – Dette er specielt beregnet til cloudabonnenter med høj sikkerhed for offentlige myndigheder
    - [DoD](https://go.microsoft.com/fwlink/?linkid=2137807) – dette er specifikt til USA cloudkunder i forsvarsministeriet

3. Godkend EDM-uploadagenten, åbn et kommandopromptvindue (som administrator), og kør følgende kommando:

   ```dos
   EdmUploadAgent.exe /Authorize
   ```

4. Hvis du ikke har en aktuel kopi af det eksisterende skema, skal du downloade en kopi af det eksisterende skema, skal du køre denne kommando:

   ```dos
   EdmUploadAgent.exe /SaveSchema /DataStoreName <dataStoreName> [/OutputDir [Output dir location]]
   ```

5. Tilpas skemaet, så hver kolonne anvender "forskel på store og små bogstaver" og/eller "ignoredDelimiters".  Standardværdien for "caseInsensitive" er "false", og for "ignoredDelimiters" er det en tom streng.

    > [!NOTE]
    > Den underliggende brugerdefinerede følsomme informationstype eller den indbyggede følsomme informationstype, der bruges til at registrere det generelle regex-mønster, skal understøtte registrering af variationsinput, der er angivet med ignoredDelimiters. Den indbyggede SSN-type (social security number) kan f.eks. registrere variationer i dataene, der omfatter tankestreger, mellemrum eller manglende mellemrum mellem de grupperede tal, der udgør SSN. Det betyder, at de eneste afgrænsere, der er relevante at medtage i EDM's ignoredDelimiters for SSN-data, er: tankestreg og mellemrum.

    Her er et eksempel på et skema, der simulerer forskel på store og små bogstaver ved at oprette de ekstra kolonner, der er nødvendige for at genkende forskel på store og små bogstaver i de følsomme data.

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

    I ovenstående eksempel er variationerne af den oprindelige `PolicyNumber` kolonne ikke længere nødvendige, hvis både `caseInsensitive` og `ignoredDelimiters` tilføjes.

    Hvis du vil opdatere dette skema, så EDM bruger konfigurerbare match, skal du bruge flagene `caseInsensitive` og `ignoredDelimiters` .  Sådan ser det ud:

    ```xml
    <EdmSchema xmlns="http://schemas.microsoft.com/office/2018/edm">
      <DataStore name="PatientRecords" description="Schema for patient records policy" version="1">
             <Field name="PolicyNumber" searchable="true" caseInsensitive="true" ignoredDelimiters="-,/,*,#,^" />
      </DataStore>
    </EdmSchema>
    ```

    Flaget `ignoredDelimiters` understøtter alle tegn, der ikke er alfanumeriske. Her er nogle eksempler:
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
    - A-Å
    - a-z
    - \"
    - \,

6. [Opret forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell).

    > [!NOTE]
    > Hvis din organisation har konfigureret [kundenøgle til Microsoft 365 på lejerniveau (offentlig prøveversion),](customer-key-tenant-level.md#overview-of-customer-key-for-microsoft-365-at-the-tenant-level-public-preview) gør nøjagtigt datamatch automatisk brug af krypteringsfunktionen. Dette er kun tilgængeligt for E5-licenserede lejere i Commercial-cloudmiljøet.

7. Opdater skemaet ved at køre følgende kommando:

   ```powershell
   Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
   ```

8. Opdater om nødvendigt datafilen, så den svarer til den nye skemaversion.

    > [!TIP]
    > Du kan eventuelt køre en validering mod din csv-fil, før du overfører den, ved at køre:
    >
    > `EdmUploadAgent.exe /ValidateData /DataFile [data file] [schema file]`
    >
    > Du kan få flere oplysninger om alle de EdmUploadAgent.exe understøttede parametre ved at køre
    >
    > `EdmUploadAgent.exe /?`

9. Åbn kommandopromptvinduet (som administrator), og kør følgende kommando for at hashene og overføre dine følsomme data:

   ```dos
   EdmUploadAgent.exe /UploadData /DataStoreName [DS Name] /DataFile [data file] /HashLocation [hash file location] /Salt [custom salt] /Schema [Schema file]
   ```

## <a name="related-articles"></a>Relaterede artikler

- [Få mere at vide om nøjagtigt datamatch baseret på typer af følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [Definitioner af følsomme oplysningers typeenhed](sensitive-information-type-entity-definitions.md)
- [Brugerdefinerede typer følsomme oplysninger](./sensitive-information-type-learn-about.md)
- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Microsoft Defender for Cloud Apps](/cloud-app-security)
- [Ny-DlpEdmSchema](/powershell/module/exchange/new-dlpedmschema)
