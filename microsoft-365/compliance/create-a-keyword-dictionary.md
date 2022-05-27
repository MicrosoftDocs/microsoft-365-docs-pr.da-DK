---
title: Opret en ordbog over nøgleord
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
description: Få mere at vide om de grundlæggende trin til oprettelse af en nøgleordsordbog i Office 365 Security & Compliance Center.
ms.openlocfilehash: ceb410d09d9869d87681128f2c6e7b45cd8363cb
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753666"
---
# <a name="create-a-keyword-dictionary"></a>Opret en ordbog over nøgleord

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Forebyggelse af datatab (DLP) kan identificere, overvåge og beskytte dine følsomme elementer. Identificering af følsomme elementer kræver nogle gange, at du søger efter nøgleord, især når du identificerer generisk indhold (f.eks. sundhedsrelateret kommunikation) eller upassende eller eksplicit sprog. Selvom du kan oprette nøgleordslister i følsomme oplysningstyper, er nøgleordslister begrænset og kræver ændring af XML for at oprette eller redigere dem. Søgeordsordbøger giver en enklere administration af nøgleord og i meget større skala, der understøtter op til 1 MB ord (efter komprimering) i ordbogen og understøtter ethvert sprog. Lejergrænsen er også 1 MB efter komprimering. 1 MB postkomprimeringsgrænse betyder, at alle ordbøger, der kombineres på tværs af en lejer, kan have næsten 1 million tegn.

## <a name="keyword-dictionary-limits"></a>Nøgleordsordbogsgrænser

Der er en grænse på 50 nøgleordsordbogsbaserede følsomme oplysningstyper, der kan oprettes pr. lejer. Hvis du vil finde ud af, hvor mange nøgleordsordbøger du har i din lejer, skal du oprette forbindelse ved hjælp af procedurerne i [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) for at oprette forbindelse til din lejer og køre dette PowerShell-script.

```powershell
$rawFile = $env:TEMP + "\rule.xml"

$kd = Get-DlpKeywordDictionary
$ruleCollections = Get-DlpSensitiveInformationTypeRulePackage
[System.IO.File]::WriteAllBytes((Resolve-Path $rawFile), $ruleCollections.SerializedClassificationRuleCollection)
$UnicodeEncoding = New-Object System.Text.UnicodeEncoding
$FileContent = [System.IO.File]::ReadAllText((Resolve-Path $rawFile), $unicodeEncoding)

if($kd.Count -gt 0)
{
$count = 0
$entities = $FileContent -split "Entity id"
for($j=1;$j -lt $entities.Count;$j++)
{
for($i=0;$i -lt $kd.Count;$i++)
{
$Matches = Select-String -InputObject $entities[$j] -Pattern $kd[$i].Identity -AllMatches
$count = $Matches.Matches.Count + $count
if($Matches.Matches.Count -gt 0) {break}
}
}

Write-Output "Total Keyword Dictionary SIT:"
$count
}
else
{
$Matches = Select-String -InputObject $FileContent -Pattern $kd.Identity -AllMatches
Write-Output "Total Keyword Dictionary SIT:"
$Matches.Matches.Count
}

Remove-Item $rawFile
```

## <a name="basic-steps-to-creating-a-keyword-dictionary"></a>Grundlæggende trin til oprettelse af en nøgleordsordbog

Nøgleordene til din ordbog kan stamme fra forskellige kilder, oftest fra en fil (f.eks. en .csv eller .txt liste), der er importeret i tjenesten eller af PowerShell-cmdlet'en, fra en liste, du angiver direkte i PowerShell-cmdlet'en eller fra en eksisterende ordbog. Når du opretter en nøgleordsordbog, skal du følge de samme kernetrin:

1. Brug *<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal,</a> eller opret forbindelse til **Microsoft Purview-compliance-portal PowerShell**.

2. **Definer eller indlæs dine nøgleord fra den ønskede kilde**. Guiden og cmdlet'en accepterer begge en kommasepareret liste over nøgleord for at oprette en brugerdefineret nøgleordsordbog, så dette trin varierer en smule, afhængigt af hvor dine nøgleord kommer fra. Når de er indlæst, kodes de og konverteres til en bytematrix, før de importeres.

3. **Opret din ordbog**. Vælg et navn og en beskrivelse, og opret din ordbog.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Opret en nøgleordsordbog ved hjælp af Security & Compliance Center

Brug følgende trin til at oprette og importere nøgleord for en brugerordbog:

1. Forbind til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>.

2. Naviger til **klassificeringer > typer følsomme oplysninger**.

3. Vælg **Opret** , og angiv et **navn** og en **beskrivelse** for din følsomme infotype, og vælg derefter **Næste**

4. Vælg **Tilføj et element**, og vælg derefter **Ordbog (store nøgleord)** på rullelisten **Registrer indhold, der indeholder** .

5. Vælg **Tilføj en ordbog**

6. Under kontrolelementet Søg skal du vælge **Du kan oprette nye nøgleordsordbøger her**.

7. Angiv et **navn** til brugerordbogen.

8. Vælg **Importér**, og vælg enten **Fra tekst** eller **Fra csv** , afhængigt af din nøgleordsfiltype.

9. I dialogboksen fil skal du vælge nøgleordsfilen fra din lokale pc eller dit netværksfilshare og derefter vælge **Åbn**.

10. Vælg **Gem**, og vælg derefter din brugerordbog på listen **Nøgleordsordbøger** .

11. Vælg **Tilføj**, og vælg derefter **Næste**.

12. Gennemse og færdiggør dine valg af følsomme oplysninger, og vælg derefter **Udfør**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>Opret en nøgleordsordbog fra en fil ved hjælp af PowerShell

Når du har brug for at oprette en stor ordbog, er det ofte at bruge nøgleord fra en fil eller en liste, der er eksporteret fra en anden kilde. I dette tilfælde skal du oprette en nøgleordsordbog, der indeholder en liste over upassende sprog til skærm i eksterne mails. Du skal først [Forbind til PowerShell & Security & Compliance Center](/powershell/exchange/connect-to-scc-powershell).

1. Kopiér nøgleordene til en tekstfil, og sørg for, at hvert nøgleord er på en separat linje.

2. Gem tekstfilen med Unicode-kodning. I Notesblok \> **Gem som** \> **kodning af** \> **Unicode**.

3. Læs filen i en variabel ved at køre denne cmdlet:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Opret ordbogen ved at køre denne cmdlet:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Brug af nøgleordsordbøger i brugerdefinerede følsomme oplysningstyper og DLP-politikker

Nøgleordsordbøger kan bruges som en del af matchkravene for en brugerdefineret følsom informationstype eller som en selvfølsom oplysningstype. Begge kræver, at du opretter en [brugerdefineret type følsomme oplysninger](create-a-custom-sensitive-information-type-in-scc-powershell.md). Følg instruktionerne i den sammenkædede artikel for at oprette en type følsomme oplysninger. Når du har XML-koden, skal du bruge GUID-identifikatoren, for at ordbogen kan bruge den.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

Hvis du vil hente identiteten af din ordbog, skal du køre denne kommando og kopiere egenskabsværdien **Identitet** :

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Outputtet af kommandoen ser ud som følger:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Indsæt identiteten i XML-koden for den brugerdefinerede følsomme oplysningstype, og upload den. Nu vises din ordbog på listen over følsomme informationstyper, og du kan bruge den direkte i din politik og angive, hvor mange nøgleord der kræves for at matche.

```xml
<Entity id="d333c6c2-5f4c-4131-9433-db3ef72a89e8" patternsProximity="300" recommendedConfidence="85">
      <Pattern confidenceLevel="85">
        <IdMatch idRef="8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f" />
      </Pattern>
    </Entity>
    <LocalizedStrings>
      <Resource idRef="d333c6c2-5f4c-4131-9433-db3ef72a89e8">
        <Name default="true" langcode="en-us">Diseases</Name>
        <Description default="true" langcode="en-us">Detects various diseases</Description>
      </Resource>
    </LocalizedStrings>
```

> [!NOTE]
> Microsoft 365 Information Protection understøtter sprog med dobbeltbytetegnsæt for:
>
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
> Denne understøttelse er tilgængelig for typer af følsomme oplysninger. Se [Produktbemærkninger til beskyttelse af oplysninger for dobbeltbytetegnsæt (prøveversion)](mip-dbcs-relnotes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du vil registrere mønstre, der indeholder kinesiske/japanske tegn og enkeltbytetegn, eller for at registrere mønstre, der indeholder kinesisk/japansk og engelsk, skal du definere to varianter af nøgleordet eller regex.
>
> - Hvis du f.eks. vil registrere et nøgleord som "机密的dokument", skal du bruge to varianter af nøgleordet. en med et mellemrum mellem japansk og engelsk tekst og en anden uden et mellemrum mellem japansk og engelsk tekst. De nøgleord, der skal tilføjes i SIT, skal derfor være "机密的 document" og "机密的document". På samme måde bør der bruges to varianter for at registrere udtrykket "東京オリンピック2020". "東京オリンピック 2020" og "東京オリンピック2020".
>
> Sammen med kinesisk/japansk/dobbeltbytetegn anbefales det at oprette to ordbøger/nøgleordslister, hvis listen over nøgleord/udtryk også indeholder ikke-kinesiske/japanske ord (f.eks. kun engelsk). Et til nøgleord, der indeholder kinesiske/japanske/dobbelte bytetegn, og et til kun engelsk.
>
> - Hvis du f.eks. vil oprette en nøgleordsordbog/liste med tre udtryk "Meget fortroligt", "機密性が高い" og "机密的dokument", skal du oprette to nøgleordslister.
>   1. Meget fortroligt
>   2. 機密性が高い, 机密的document og 机密的 dokument
>
> Mens du opretter en regex ved hjælp af en dobbelt byte bindestreg eller et dobbelt byte punktum, skal du sørge for at undslippe begge tegn, som man ville undslippe en bindestreg eller et punktum i en regex. Her er et eksempel på et regex som reference:
>
> - `(?<!\d)([4][0-9]{3}[\-?\-\t]*[0-9]{4}`
>
> Vi anbefaler, at du bruger et strengmatch i stedet for et ordmatch på en nøgleordsliste.
