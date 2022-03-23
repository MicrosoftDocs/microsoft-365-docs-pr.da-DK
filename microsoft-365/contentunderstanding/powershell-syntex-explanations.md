---
title: Arbejd med dokumentforståelse for modelforklaringer i PowerShell
ms.author: jaeccles
author: jameseccles
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
search.appverid: MET150
ms.localizationpriority: medium
description: Få mere at vide om at SharePoint Syntex dokumentforståelse for modelforklaringer i PowerShell.
ms.openlocfilehash: 12bdb4c7019b34ee7d2c1f4315673d78cbfb7ba1
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594128"
---
# <a name="work-with-document-understanding-model-explanations-in-powershell"></a>Arbejd med dokumentforståelse for modelforklaringer i PowerShell

> [!IMPORTANT]
> The SharePoint Syntex PowerShell cmdlets and all other PnP components are open source tools backed by an active community providing support for them. Der er ingen SLA for understøttelse af open source-værktøjer fra officielle Microsoft-supportkanaler.

Brugerdefinerede forklaringsskabeloner gemmes på en liste i et indholdscenter. Da disse forklaringer gemmes som listeelementer, kan PowerShell bruges til at interagere med dem.

## <a name="list-saved-explanations"></a>Liste over gemte forklaringer

I dette eksempel vises det, hvordan du får vist alle de brugerdefinerede forklaringsskabeloner, der er gemt i et bestemt indholdscenter.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list and items
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"
$explanations = Get-PnPListItem -List $explanationTemplatesList -Fields "Id", "Title", "ExplanationName", "ExplanationType", "ExplanationDescription","ExplanationContent"

# Extract explanation components
$explanationValues = $explanations.fieldvalues 
$explanationOutput = @()

foreach ($explanation in $explanationValues) {
    $content = $explanation.ExplanationContent
    $content = $content.replace('false','"false"')
    $content = $content.replace('true','"true"')
    $contentArray = $content | ConvertFrom-Json

    $output = New-Object -TypeName PSObject
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Explanation Name" -Value $explanation.ExplanationName
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Explanation Description" -Value $explanation.ExplanationDescription
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Explanation Type" -Value $contentArray.kind
    Add-Member -InputObject $output -MemberType NoteProperty -Name "RegEx Pattern" -Value $contentArray.pattern
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Phrase List" -Value $contentArray.ngrams
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Case Sensitive" -Value $contentArray.caseSensitive
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Ignore Digit Identity" -Value $contentArray.ignoreDigitIdentity
    Add-Member -InputObject $output -MemberType NoteProperty -Name "Ignore Letter Identity" -Value $contentArray.ignoreLetterIdentity

    $explanationOutput += $output
}

$explanationOutput
```

## <a name="create-a-phrase-list-explanation"></a>Opret en forklaring til en sætningsliste

Dette eksempel viser, hvordan du opretter en forklaringsskabelon til en brugerdefineret sætningsliste.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"
$explanationName = "Phrase Explanation A"
$explanationDescription = "This is my explanation"
$phrases = "Phrase 1", "Phrase 2"
$caseSensitive = $false
$ignoreDigitIdentity= $false
$ignoreLetterIdentity = $false

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"

#Generate GUID for explanation
$guid = New-Guid

#Format phrase list
$phrases = $phrases -join "`",`""

#Convert booleans to lower case strings
$caseSensitive = ($caseSensitive.ToString()).ToLower()
$ignoreDigitIdentity= ($ignoreDigitIdentity.ToString()).ToLower()
$ignoreLetterIdentity = ($ignoreLetterIdentity.ToString()).ToLower()

# Build explanation content
$explanationContent = "{`"id`":`"$guid`",`"kind`":`"dictionaryFeature`",`"name`":`"$explanationName`",`"active`":true,`"nGrams`":[`"$phrases`"],`"caseSensitive`":$caseSensitive,`"ignoreDigitIdentity`":$ignoreDigitIdentity,`"ignoreLetterIdentity`":$ignoreLetterIdentity}"

# Create item in explanation list
Add-PnPListItem -List $explanationTemplatesList -Values @{"Title"= $explanationName; "ExplanationName" = $explanationName; "ExplanationDescription" = $explanationDescription; "ExplanationContent" = $explanationContent}
```

## <a name="create-a-regular-expression-explanation"></a>Oprette en forklaring til et regulært udtryk

Dette eksempel viser, hvordan du opretter en brugerdefineret forklaringsskabelon til regulære udtryk.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"
$explanationName = "RegEx Explanation A"
$explanationDescription = "This is my explanation"
$pattern = "\b(https?):\/\/\S+"

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"

#Generate GUID for explanation
$guid = New-Guid

# Build explanation content
$pattern = $pattern.Replace('\','\\')
$explanationContent = "{`"id`":`"$guid`",`"kind`":`"regexFeature`",`"name`":`"$explanationName`",`"active`":true,`"pattern`":`"$pattern`"}"

# Create item in explanation list
Add-PnPListItem -List $explanationTemplatesList -Values @{"Title"= $explanationName; "ExplanationName" = $explanationName; "ExplanationDescription" = $explanationDescription; "ExplanationContent" = $explanationContent}
```

## <a name="create-a-phrase-list-explanation-based-on-a-term-set"></a>Opret en forklaring til en sætningsliste baseret på et ordsæt

Dette eksempel viser, hvordan du opretter en forklaringsskabelon til en brugerdefineret sætningsliste ved at tage værdierne fra et ordsæt. Dette omfatter de foretrukne ordnavne og eventuelle synonymer.

```PowerShell
$contentCenterURL = "https://contoso.sharepoint.com/sites/yourContentCenter"
$termSetName = "Terms"
$termGroupName = "GroupA"
$explanationName = "MMS Explanation A"
$explanationDescription = "This is my explanation"
$caseSensitive = $false
$ignoreDigitIdentity= $false
$ignoreLetterIdentity = $false

# Connect to content center
Connect-PnPOnline -url $contentCenterURL

# Load explanation templates list
$explanationTemplatesList = Get-PnPList -Identity "/Explanations"

#Generate GUID for explanation
$guid = New-Guid

#Get term set, including preferred labels and synonyms
$terms = Get-PnPTerm -TermGroup $termGroupName -TermSet $termSetName -Includes Labels
$phrases = $terms.labels.value

#Format phrase list
$phrases = $phrases -join "`",`""

#Convert booleans to lower case strings
$caseSensitive = ($caseSensitive.ToString()).ToLower()
$ignoreDigitIdentity= ($ignoreDigitIdentity.ToString()).ToLower()
$ignoreLetterIdentity = ($ignoreLetterIdentity.ToString()).ToLower()

# Build explanation content
$explanationContent = "{`"id`":`"$guid`",`"kind`":`"dictionaryFeature`",`"name`":`"$explanationName`",`"active`":true,`"nGrams`":[`"$phrases`"],`"caseSensitive`":$caseSensitive,`"ignoreDigitIdentity`":$ignoreDigitIdentity,`"ignoreLetterIdentity`":$ignoreLetterIdentity}"

# Create item in explanation list
Add-PnPListItem -List $explanationTemplatesList -Values @{"Title"= $explanationName; "ExplanationName" = $explanationName; "ExplanationDescription" = $explanationDescription; "ExplanationContent" = $explanationContent}
```
