---
title: Om dokumentaftryk
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
description: Informationsmedarbejdere i din organisation håndterer mange slags følsomme oplysninger i løbet af en typisk dag. Dokumentaftryk gør det nemmere for dig at beskytte disse oplysninger ved at identificere standardformularer, der bruges i hele organisationen. I dette emne beskrives begreberne bag dokumentaftryk, og hvordan du opretter et ved hjælp af PowerShell.
ms.openlocfilehash: 3df4b7cf6f9fa09e81cf326cc58cc8114c025be9
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014470"
---
# <a name="document-fingerprinting"></a>Dokumentfingeraftryk

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Informationsmedarbejdere i din organisation håndterer mange slags følsomme oplysninger i løbet af en typisk dag. På Microsoft Purview-overholdelsesportalen gør dokumentaftryk det nemmere for dig at beskytte disse oplysninger ved at identificere de standardformularer, der bruges i hele organisationen. I dette emne beskrives begreberne bag dokumentaftryk, og hvordan du opretter et ved hjælp af PowerShell.

## <a name="basic-scenario-for-document-fingerprinting"></a>Grundlæggende scenarie for dokumentaftryk

Dokumentaftryk er en Microsoft Purview DLP-funktion (Forebyggelse af datatab), der konverterer en standardformular til en følsom oplysningstype, som du kan bruge i reglerne i dine DLP-politikker. Du kan f.eks. oprette et dokumentaftryk baseret på en tom patentskabelon og derefter oprette en DLP-politik, der registrerer og blokerer alle udgående patentskabeloner med følsomt indhold udfyldt. Du kan eventuelt konfigurere [politiktips](use-notifications-and-policy-tips.md) for at give afsendere besked om, at de muligvis sender følsomme oplysninger, og afsenderen skal bekræfte, at modtagerne er kvalificerede til at modtage patenterne. Denne proces fungerer sammen med alle tekstbaserede formularer, der bruges i din organisation. Yderligere eksempler på formularer, som du kan uploade, omfatter:

- Offentlige formularer
- HIPAA-formularer (Health Insurance Portability and Accountability Act)
- Formularer med medarbejderoplysninger til HR-afdelinger
- Brugerdefinerede formularer, der er oprettet specielt til din organisation

Ideelt set har din organisation allerede en etableret forretningspraksis med at bruge visse formularer til at overføre følsomme oplysninger. Når du har uploadet en tom formular, der skal konverteres til et dokumentaftryk og konfigureret en tilsvarende politik, registrerer DLP alle dokumenter i udgående mails, der svarer til det pågældende fingeraftryk.

## <a name="how-document-fingerprinting-works"></a>Sådan fungerer dokumentaftryk

Du har sikkert allerede gættet, at dokumenter ikke har faktiske fingeraftryk, men navnet hjælper med at forklare funktionen. På samme måde som en persons fingeraftryk har unikke mønstre, har dokumenter unikke ordmønstre. Når du uploader en fil, identificerer DLP det entydige ordmønster i dokumentet, opretter et dokumentaftryk baseret på dette mønster og bruger dette dokumentaftryk til at registrere udgående dokumenter, der indeholder det samme mønster. Det er derfor, at upload af en formularskabelon opretter den mest effektive type dokumentaftryk. Alle, der udfylder en formular, bruger det samme oprindelige sæt ord og derefter tilføjer sine egne ord i dokumentet. Så længe det udgående dokument ikke er beskyttet med adgangskode og indeholder al teksten fra den oprindelige formular, kan DLP afgøre, om dokumentet stemmer overens med dokumentets fingeraftryk.

> [!IMPORTANT]
> I øjeblikket kan DLP kun bruge dokumentaftryk som en registreringsmetode i Exchange online.

I følgende eksempel kan du se, hvad der sker, hvis du opretter et dokumentaftryk baseret på en patentskabelon, men du kan bruge en hvilken som helst formular som grundlag for at oprette et dokumentaftryk.

### <a name="example-of-a-patent-document-matching-a-document-fingerprint-of-a-patent-template"></a>Eksempel på et patentdokument, der matcher et dokuments fingeraftryk af en patentskabelon

![Diagram over dokumentaftryk.](../media/Document-Fingerprinting-diagram.png)

Patentskabelonen indeholder de tomme felter "Patenttitel", "Opfindere" og "Beskrivelse" og beskrivelser for hvert af disse felter – dvs. ordmønsteret. Når du uploader den oprindelige patentskabelon, er den i en af de understøttede filtyper og i almindelig tekst. DLP konverterer dette ordmønster til et dokumentaftryk, som er en lille Unicode XML-fil, der indeholder en entydig hashværdi, der repræsenterer den oprindelige tekst, og fingeraftrykket gemmes som en dataklassificering i Active Directory. (Som en sikkerhedsforanstaltning gemmes selve det oprindelige dokument ikke i tjenesten, kun hashværdien gemmes, og det oprindelige dokument kan ikke genskabes ud fra hashværdien). Patentets fingeraftryk bliver derefter en følsom informationstype, som du kan knytte til en DLP-politik. Når du har knyttet fingeraftrykket til en DLP-politik, registrerer DLP eventuelle udgående mails, der indeholder dokumenter, der stemmer overens med patentaftrykket, og behandler dem i henhold til din organisations politik.

Det kan f.eks. være, at du vil konfigurere en DLP-politik, der forhindrer almindelige medarbejdere i at sende udgående meddelelser, der indeholder patenter. DLP bruger patentaftrykket til at registrere patenter og blokere disse mails. Alternativt kan du lade din juridiske afdeling være i stand til at sende patenter til andre organisationer, fordi den har et forretningsmæssigt behov for at gøre det. Du kan tillade, at bestemte afdelinger sender følsomme oplysninger ved at oprette undtagelser for disse afdelinger i din DLP-politik, eller du kan tillade, at de tilsidesætter et politiktip med en forretningsberettigelse.

### <a name="supported-file-types"></a>Understøttede filtyper

Dokumentaftryk understøtter de samme filtyper, der understøttes i regler for mailflow (også kaldet transportregler). Du kan se en liste over understøttede filtyper under [Understøttede filtyper til indholdskontrol af mailflowregel](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection). En hurtig bemærkning om filtyper: Hverken regler for mailflow eller dokumentaftryk understøtter filtypen .dotx, hvilket kan være forvirrende, da det er en skabelonfil i Word. Når du ser ordet "skabelon" i denne og andre emner om dokumentaftryk, henviser det til et dokument, du har oprettet som en standardformular, og ikke skabelonfiltypen.

#### <a name="limitations-of-document-fingerprinting"></a>Begrænsninger ved dokumentaftryk

Dokumentaftryk registrerer ikke følsomme oplysninger i følgende tilfælde:

- Filer, der er beskyttet med adgangskode
- Filer, der kun indeholder billeder
- Dokumenter, der ikke indeholder al tekst fra den oprindelige formular, som blev brugt til at oprette dokumentets fingeraftryk
- Filer, der er større end 10 MB

## <a name="use-powershell-to-create-a-classification-rule-package-based-on-document-fingerprinting"></a>Brug PowerShell til at oprette en klassificeringsregelpakke, der er baseret på dokumentaftryk

I øjeblikket kan du kun oprette et dokumentaftryk i [PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

DLP bruger klassificeringsregelpakker til at registrere følsomt indhold. Hvis du vil oprette en klassificeringsregelpakke, der er baseret på et dokuments fingeraftryk, skal du bruge cmdlet'erne **New-DlpFingerprint** og **New-DlpSensitiveInformationType** . Da resultaterne af **New-DlpFingerprint** ikke gemmes uden for dataklassificeringsreglen, kører du altid **New-DlpFingerprint** og **New-DlpSensitiveInformationType** eller **Set-DlpSensitiveInformationType** i den samme PowerShell-session. I følgende eksempel oprettes et nyt dokumentaftryk baseret på filen C:\Mine dokumenter\Contoso Employee Template.docx. Du gemmer det nye fingeraftryk som en variabel, så du kan bruge den sammen med Cmdlet'en **New-DlpSensitiveInformationType** i den samme PowerShell-session.

```powershell
$Employee_Template = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Employee Template.docx'))
$Employee_Fingerprint = New-DlpFingerprint -FileData $Employee_Template -Description "Contoso Employee Template"
```

Lad os nu oprette en ny dataklassificeringsregel med navnet "Contoso Employee Confidential", der bruger dokumentaftrykket fra filen C:\Mine dokumenter\Contoso-kundeoplysninger Form.docx.

```powershell
$Customer_Form = ([System.IO.File]::ReadAllBytes('C:\My Documents\Contoso Customer Information Form.docx'))
$Customer_Fingerprint = New-DlpFingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
New-DlpSensitiveInformationType -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information."
```

Du kan nu bruge **cmdlet'en Get-DlpSensitiveInformationType** til at finde alle DLP-dataklassificeringsregelpakker, og i dette eksempel er "Contoso Customer Confidential" en del af listen over regelpakker til dataklassificering.

Til sidst skal du føje regelpakken "Contoso Customer Confidential" til en DLP-politik på Microsoft Purview-overholdelsesportalen. I dette eksempel føjes der en regel til en eksisterende DLP-politik med navnet "ConfidentialPolicy".

```powershell
New-DlpComplianceRule -Name "ContosoConfidentialRule" -Policy "ConfidentialPolicy" -ContentContainsSensitiveInformation @{Name="Contoso Customer Confidential"} -BlockAccess $True
```

Du kan også bruge dataklassificeringsregelpakken i regler for mailflow i Exchange Online, som vist i følgende eksempel. Hvis du vil køre denne kommando, skal du først [Forbind for at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Bemærk også, at det tager tid for regelpakken at synkronisere fra Microsoft Purview-overholdelsesportalen til Exchange Administration.

```powershell
New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}
```

DLP registrerer nu dokumenter, der svarer til Contoso-kundens Form.docx dokumentaftryk.

Du kan få oplysninger om syntaks og parametre under:

- [Nyt DlpFingerprint](/powershell/module/exchange/New-DlpFingerprint)
- [New-DlpSensitiveInformationType](/powershell/module/exchange/New-DlpSensitiveInformationType)
- [Remove-DlpSensitiveInformationType](/powershell/module/exchange/Remove-DlpSensitiveInformationType)
- [Set-DlpSensitiveInformationType](/powershell/module/exchange/Set-DlpSensitiveInformationType)
- [Get-DlpSensitiveInformationType](/powershell/module/exchange/Get-DlpSensitiveInformationType)
