---
title: Dokument fingeraftryk
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: ITPro
ms.topic: article
search.appverid: MET150
ms.service: exchange-online
ms.collection: M365-security-compliance
ms.localizationpriority: medium
description: Informationsmedarbejdere i din organisation håndterer mange typer af følsomme oplysninger på en typisk dag. Dokument fingeraftryk gør det nemmere for dig at beskytte disse oplysninger ved at identificere standardformularer, der bruges i hele organisationen. I dette emne beskrives begreberne bag Dokument fingeraftryk, og hvordan du opretter et ved hjælp af PowerShell.
ms.openlocfilehash: cd75fe8ec8f4c727f86689cd3a46f331e71afdad
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63587684"
---
# <a name="document-fingerprinting"></a>Dokument fingeraftryk

Informationsmedarbejdere i din organisation håndterer mange typer af følsomme oplysninger på en typisk dag. I Security &amp; Compliance Center gør Dokument fingeraftryk det nemmere for dig at beskytte disse oplysninger ved at identificere standardformularer, der bruges i hele organisationen. I dette emne beskrives begreberne bag Dokument fingeraftryk, og hvordan du opretter et ved hjælp af PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>Grundlæggende scenarie for dokument fingeraftryk

Dokument fingeraftryk er en funktion til forebyggelse af datatab (DLP), der konverterer en standardformular til en følsom oplysningstype, som du kan bruge i reglerne for dine DLP-politikker. For example, you can create a document fingerprint based on a blank patent template and then create a DLP policy that detects and blocks all outgoing patent templates with sensitive content filled in. Du kan også konfigurere politiktip til [](use-notifications-and-policy-tips.md) at underrette afsendere om, at de muligvis sender følsomme oplysninger, og afsenderen skal bekræfte, at modtagerne er kvalificeret til at modtage patenterne. Denne proces fungerer sammen med alle tekstbaserede formularer, der bruges i organisationen. Andre eksempler på formularer, du kan overføre, omfatter:

- Offentlige formularer
- Formularer til overholdelse af HIPAA (Health Insurance Portability and Accountability Act)
- Formularer til medarbejderoplysninger for HR-afdelinger
- Brugerdefinerede formularer, der er oprettet specifikt til din organisation

Ideelt set har din organisation allerede en etableret forretningspraksis ved brug af visse formularer til at overføre følsomme oplysninger. Når du overfører en tom formular, der skal konverteres til et dokuments fingeraftryk og konfigurerer en tilsvarende politik, registrerer DLP alle dokumenter i udgående mail, der svarer til det pågældende fingeraftryk.

## <a name="how-document-fingerprinting-works"></a>Sådan fungerer dokument fingeraftryk

Du har sikkert allerede gættet, at dokumenter ikke har faktiske fingeraftryk, men navnet hjælper med at forklare funktionen. På samme måde som en persons fingeraftryk har unikke mønstre, har dokumenter entydige ordmønstre. Når du overfører en fil, identificerer DLP det entydige ordmønster i dokumentet, opretter et dokuments fingeraftryk baseret på det pågældende mønster og bruger det pågældende dokuments fingeraftryk til at registrere udgående dokumenter, der indeholder det samme mønster. Derfor opretter overførsel af en formular eller skabelon den mest effektive type dokument fingeraftryk. Alle, der udfylder en formular, bruger det samme oprindelige sæt ord og føjer derefter sine egne ord til dokumentet. Så længe det udgående dokument ikke er beskyttet med adgangskode og indeholder al tekst fra den oprindelige formular, kan DLP afgøre, om dokumentet svarer til dokumentets fingeraftryk.

> [!IMPORTANT]
> I øjeblikket kan DLP bruge dokument fingeraftryk som en registreringsmetode i Exchange online.

Følgende eksempel viser, hvad der sker, hvis du opretter et dokuments fingeraftryk, der er baseret på en patentskabelon, men du kan bruge en hvilken som helst formular som grundlag for at oprette et dokuments fingeraftryk.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Eksempel på et patentdokument, der matcher et dokuments fingeraftryk af en patentskabelon

![Diagram over dokument fingeraftryk.](../media/Document-Fingerprinting-diagram.png)

The patent template contains the blank fields "Patent title," "Inventors," and "Description" and descriptions for each of those fields — that's the word pattern. Når du uploader den oprindelige patentskabelon, findes den i en af de understøttede filtyper og i almindelig tekst. DLP konverterer dette ordmønster til et dokuments fingeraftryk, som er en lille Unicode XML-fil, der indeholder en entydig hash-værdi, der repræsenterer den oprindelige tekst, og fingeraftryket gemmes som en dataklassificering i Active Directory. (Af sikkerhedsmæssigehensende gemmes selve dokumentet ikke på tjenesten, kun hash-værdien gemmes, og det oprindelige dokument kan ikke genoprettes fra hash-værdien). Patent-fingeraftryk bliver så til en følsom oplysningstype, som du kan knytte til en DLP-politik. Når du knytter fingeraftryk til en DLP-politik, registrerer DLP alle udgående mails, der indeholder dokumenter, der matcher patent-fingeraftryk og handler med dem i henhold til din organisations politik.

For example, you might want to set up a DLP policy that prevents regular employees from sending outgoing messages containing patents. DLP bruger patent-fingeraftryk til at registrere patenter og blokere disse mails. Alternativt kan det være en god ide at lade din juridiske afdeling kunne sende patenter til andre organisationer, fordi den har forretningsmæssige behov for at gøre det. Du kan tillade, at bestemte afdelinger sender følsomme oplysninger ved at oprette undtagelser for disse afdelinger i din DLP-politik, eller du kan give dem tilladelse til at tilsidesætte et politiktip med en forretningsberettigelse.

### <a name="supported-file-types"></a>Understøttede filtyper

Dokument fingeraftryk understøtter de samme filtyper, der understøttes i regler for mailflow (også kaldet transportregler). Du kan finde en liste over understøttede filtyper under [Understøttede filtyper til inspektion af indhold af mailflowregel](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). En hurtig note om filtyper: Hverken regler for mailflow eller dokument fingeraftryk understøtter filtypen .dotx, hvilket kan være forvirrende, fordi det er en skabelonfil i Word. Når du ser ordet "skabelon" i dette og andre dokument fingeraftryksemner, refererer det til et dokument, som du har oprettet som en standardformular, ikke skabelonfiltypen.

#### <a name="limitations-of-document-fingerprinting"></a>Begrænsninger for dokument fingeraftryk

Dokument fingeraftryk registrerer ikke følsomme oplysninger i følgende tilfælde:

- Adgangskodebeskyttede filer
- Filer, der kun indeholder billeder
- Dokumenter, der ikke indeholder al tekst fra den oprindelige formular, der bruges til at oprette dokumentets fingeraftryk
- Filer, der er større end 10 MB

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Brug PowerShell til at oprette en klassificeringsregelpakke baseret på dokument fingeraftryk

Du kan i øjeblikket kun oprette et dokuments fingeraftryk [i Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

DLP bruger klassificeringsregelpakker til at registrere følsomt indhold. Hvis du vil oprette en klassificeringsregelpakke, der er baseret på et dokuments fingeraftryk, skal du bruge **New-DlpFingerprint** og **New-DlpSensitiveInformationType-cmdlet'er** . Da resultaterne af **New-DlpFingerprint** ikke gemmes uden for dataklassificeringsreglen, kører du altid **New-DlpFingerprint** og **New-DlpSensitiveInformationType** eller **Set-DlpSensitiveInformationType** i den samme PowerShell-session. I følgende eksempel oprettes der et nyt dokument fingeraftryk, der er baseret på filen C:\Dokumenter\Contoso-medarbejder Template.docx. Du gemmer det nye fingeraftryk som en variabel, så du kan bruge den med **New-DlpSensitiveInformationType-cmdlet'en** i den samme PowerShell-session.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Lad os nu oprette en ny dataklassificeringsregel med navnet "Fortroligt med Contoso-medarbejder", der bruger dokumentets fingeraftryk fra filen C:\Dokumenter\Contoso-kundeoplysninger Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Du kan nu bruge **Get-DlpSensitiveInformationType-cmdlet'en** til at finde alle pakker til DLP-dataklassificeringsregel, og i dette eksempel er "Contoso Kundefortrolige" en del af listen med pakker til dataklassificeringsregel.

Til sidst skal du føje dataklassificeringspakken "Fortroligt for Contoso"-data til en DLP-politik i Security &amp; Compliance Center. I dette eksempel føjes en regel til en eksisterende DLP-politik med navnet "FortroligtPolicy".

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Du kan også bruge dataklassificeringsregelpakken i regler for mailflow i Exchange Online som vist i følgende eksempel. For at køre denne kommando skal du først Forbind [at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Bemærk også, at det tager tid for regelpakken at synkronisere fra Security &amp; Compliance Center til Exchange Administration.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

DLP registrerer nu dokumenter, der svarer til Contoso-Form.docx dokument fingeraftryk.

Du kan finde oplysninger om syntaks og parameter i:

- [New-DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
