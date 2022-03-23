---
title: Opret en ordbog til nøgleord
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
description: Lær de grundlæggende trin til at oprette en ordbog til nøgleord i Office 365 Security & Compliance Center.
ms.openlocfilehash: ca88c57739c8734f9fcdb5d3356a44dc6a72faa5
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63588912"
---
# <a name="create-a-keyword-dictionary"></a>Opret en ordbog til nøgleord

Forebyggelse af datatab (DLP) kan identificere, overvåge og beskytte dine følsomme elementer. Identificering af følsomme elementer kræver nogle gange, at du leder efter nøgleord, især når du identificerer generisk indhold (f.eks. sundhedsrelateret kommunikation) eller upassende eller eksplicit sprog. Selvom du kan oprette nøgleordslister i typer med følsomme oplysninger, er nøgleordslister begrænset i størrelse og kræver ændring af XML for at oprette eller redigere dem. Nøgleordsordbøger giver enklere administration af nøgleord og på meget større skala, hvilket understøtter op til 1 MB ord (efter komprimering) i ordbogen og understøtter alle sprog. Lejergrænsen er også 1 MB efter komprimeringen. 1 MB komprimeringsgrænse betyder, at alle ordbøger kombineret på tværs af en lejer kan have tæt på 1 million tegn.

## <a name="keyword-dictionary-limits"></a>Begrænsninger for ordbog til nøgleord

Der er en grænse på 50 ordbøger baseret på følsomme oplysninger, der kan oprettes pr. lejer. For at finde ud af hvor mange ordbøger til nøgleord, du har i din lejer, skal du oprette forbindelse ved hjælp af procedurerne i [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) for at oprette forbindelse til din lejer og køre dette PowerShell-script.

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

## <a name="basic-steps-to-creating-a-keyword-dictionary"></a>Grundlæggende trin til at oprette en ordbog til nøgleord

Nøgleordene til din ordbog kan komme fra forskellige kilder, oftest fra en fil (f.eks. en .csv- eller .txt-liste), der er importeret i tjenesten eller af PowerShell-cmdlet'en, fra en liste, du angiver direkte i PowerShell-cmdlet'en eller fra en eksisterende ordbog. Når du opretter en ordbog til nøgleord, skal du følge de samme grundlæggende trin:

1. Brug *<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter eller</a> opret forbindelse til **Security &amp; Compliance Center PowerShell**.

2. **Definere eller indlæse dine nøgleord fra den tilsigtede kilde**. Både guiden og cmdlet'en accepterer en kommasepareret liste over nøgleord for at oprette en ordbog med brugerdefinerede nøgleord, så dette trin varierer en smule, afhængigt af hvor dine nøgleord kommer fra. Når de er indlæst, kodes og konverteres de til en bytematrix, før de importeres.

3. **Opret din ordbog**. Vælg et navn og en beskrivelse, og opret din ordbog.

## <a name="create-a-keyword-dictionary-using-the-security--compliance-center"></a>Opret en ordbog til nøgleord ved hjælp af Sikkerheds- & Compliance Center

Brug følgende trin til at oprette og importere nøgleord til en brugerordbog:

1. Forbind til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>.

2. Gå til **Klassificeringer > typer af følsomme oplysninger**.

3. Vælg **Opret** , og angiv **et Navn** **og en Beskrivelse** til din type af følsomme oplysninger, og vælg derefter **Næste**

4. Vælg **Tilføj et element**, og vælg **derefter Ordbog (Store nøgleord)** på **rullelisten Find indhold** , der indeholder.

5. Vælg **Tilføj en ordbog**

6. Under søgekontrolelementet skal du vælge **Du kan oprette nye ordbøger til nøgleord her**.

7. Angiv et **Navn** til din brugerordbog.

8. Vælg **Importér**, og vælg enten **Fra tekst** eller **Fra CSV afhængigt** af nøgleordsfiltypen.

9. I dialogboksen Fil skal du vælge nøgleordsfilen fra din lokale pc eller filshare i netværket og derefter vælge **Åbn**.

10. Vælg **Gem**, og vælg derefter din brugerordbog på **listen Nøgleordsordbøger** .

11. Vælg **Tilføj**, og vælg derefter **Næste**.

12. Gennemse og færdiggør dine valg af type af følsomme oplysninger, og vælg derefter **Udfør**.

## <a name="create-a-keyword-dictionary-from-a-file-using-powershell"></a>Opret en ordbog til nøgleord fra en fil ved hjælp af PowerShell

Når du ofte har brug for at oprette en stor ordbog, er det at bruge nøgleord fra en fil eller en liste, der er eksporteret fra en anden kilde. I dette tilfælde skal du oprette en ordbog med nøgleord, der indeholder en liste over upassende sprog til at screene i eksterne mails. Du skal først [Forbind Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

1. Kopiér nøgleordene til en tekstfil, og sørg for, at hvert nøgleord er på en separat linje.

2. Gem tekstfilen med Unicode-kodning. Klik Notesblok \> **under Gem** \> **som kodning af** \> **Unicode**.

3. Læs filen i en variabel ved at køre denne cmdlet:

    ```powershell
    $fileData = [System.IO.File]::ReadAllBytes('<filename>')
    ```

4. Opret ordbogen ved at køre denne cmdlet:

    ```powershell
    New-DlpKeywordDictionary -Name <name> -Description <description> -FileData $fileData
    ```

## <a name="using-keyword-dictionaries-in-custom-sensitive-information-types-and-dlp-policies"></a>Brug af ordbøger til nøgleord i brugerdefinerede typer af følsomme oplysninger og DLP-politikker

Nøgleordsordbøger kan bruges som en del af matchkravene til en brugerdefineret type af følsomme oplysninger eller som en type af følsomme oplysninger. Begge kræver, at du opretter en [brugerdefineret type af følsomme oplysninger](create-a-custom-sensitive-information-type-in-scc-powershell.md). Følg vejledningen i den sammenkædede artikel for at oprette en type af følsomme oplysninger. Når du har XML, skal du bruge GUID-identifikatoren til ordbogen for at bruge den.

```xml
<Entity id="9e5382d0-1b6a-42fd-820e-44e0d3b15b6e" patternsProximity="300" recommendedConfidence="75">
    <Pattern confidenceLevel="75">
        <IdMatch idRef=". . ."/>
    </Pattern>
</Entity>
```

For at få identiteten af din ordbog skal du køre denne kommando og kopiere **værdien for egenskaben** Identitet:

```powershell
Get-DlpKeywordDictionary -Name "Diseases"
```

Outputtet for kommandoen ser sådan ud:

`RunspaceId        : 138e55e7-ea1e-4f7a-b824-79f2c4252255`
`Identity          : 8d2d44b0-91f4-41f2-94e0-21c1c5b5fc9f`
`Name              : Diseases`
`Description       : Names of diseases and injuries from ICD-10-CM lexicon`
`KeywordDictionary : aarskog's syndrome, abandonment, abasia, abderhalden-kaufmann-lignac, abdominalgia, abduction contracture, abetalipo` `proteinemia, abiotrophy, ablatio, ablation, ablepharia, abocclusion, abolition, aborter, abortion, abortus, aboulomania,`
                    `abrami's disease, abramo`
`IsValid           : True`
`ObjectState       : Unchanged`

Indsæt identiteten i XML'en med en brugerdefineret type af følsomme oplysninger, og overfør den. Nu vises din ordbog på listen over typer af følsomme oplysninger, og du kan bruge den direkte i din politik, hvor du angiver, hvor mange nøgleord der kræves for at matche.

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
> Microsoft 365 Information Protection understøtter dobbelt-byte tegnsætsprog til:
>
> - Kinesisk (forenklet)
> - Kinesisk (traditionelt)
> - Korean
> - Japanese
>
> Denne support er tilgængelig for typer af følsomme oplysninger. Se Understøttelse af [beskyttelse af oplysninger for dobbelt byte-tegnsæt produktbemærkninger (forhåndsvisning)](mip-dbcs-relnotes.md) for at få flere oplysninger.

> [!TIP]
> Hvis du vil registrere mønstre, der indeholder kinesiske/japanske tegn og enkelte bytetegn eller til at registrere mønstre, der indeholder kinesisk/japansk og engelsk, skal du definere to varianter af nøgleordet eller regex.
>
> - Hvis du f.eks. vil registrere et nøgleord som "机密的dokument", skal du bruge to varianter af nøgleordet; et med et mellemrum mellem den japanske og engelske tekst og et andet uden mellemrum mellem den japanske og engelske tekst. Så de nøgleord, der skal tilføjes i SIT, bør være "机密的 dokument" og "机密的dokument". På samme måde skal der bruges to varianter til 東京オリ "東京オリンピック2020". "東京オリンピック 2020" og "東京オリンピック2020".
>
> Sammen med kinesisk/japansk/dobbelt byte tegn, hvis listen over nøgleord/sætninger også indeholder ikke-kinesiske/japanske ord (som kun engelsk), anbefales det at oprette to ordbøger/nøgleordslister. En til nøgleord, der indeholder kinesiske/japanske/dobbelte bytetegn og et andet til kun engelsk.
>
> - Hvis du f.eks. vil oprette en ordbog/liste med nøgleord med tre udtryk "Meget fortroligt", "機密性が高い" og "机密的dokument", skal du oprette to lister med nøgleord.
>     1. Meget fortrolig
>     2. 機密性が高い, 机密的dokument og 机密的 dokument
>
> Mens du opretter en regex ved hjælp af en dobbelt byte bindestreg eller et dobbelt byte punktum, skal du sørge for at undgå begge tegn, som om den ene ville escape en bindestreg eller punktum i en regex. Her er en eksempelre regex til reference:
>
> - `(?<!\d)([４][０-９]{3}[\-?\－\t]*[０-９]{4}`
>
> Vi anbefaler, at du bruger et strengmatch i stedet for et ordmatch i en nøgleordsliste.
