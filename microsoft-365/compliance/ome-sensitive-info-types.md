---
title: Opret en politik for følsomme oplysninger ved hjælp af Office 365-meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- Strat_O365_Enterprise
description: Lær, hvordan du opretter en politik for følsomme oplysninger i organisationen ved hjælp Office 365-meddelelseskryptering.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 8978b1f9faae2e96fa1940bf7663855ec3bb61da
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63587319"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>Opret en politik for typen af følsomme oplysninger for organisationen ved hjælp af meddelelseskryptering

Du kan bruge enten Exchange regler for mailflow eller forebyggelse af datatab (DLP) til at oprette en politik for følsomme oplysninger Office 365-meddelelseskryptering. Hvis du Exchange en regel for mailflow, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">kan du bruge enten Exchange Administration (EAC)</a> eller PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>Sådan oprettes politikken ved hjælp af regler for mailflow i EAC

Log på Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Administration, og</a> gå til **MailflowRules** > . På siden Regler skal du oprette en regel, der gælder Office 365-meddelelseskryptering. Du kan oprette en regel baseret på betingelser som f.eks. tilstedeværelsen af bestemte nøgleord eller typer af følsomme oplysninger i meddelelsen eller den vedhæftede fil.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>Sådan opretter du politikken ved hjælp af regler for mailflow i PowerShell

Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, start en session Windows PowerShell opret forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Brug Set-IRMConfiguration og New-TransportRule til at oprette politikken.

## <a name="example-mail-flow-rule-created-with-powershell"></a>Eksempel på en regel for mailflow, der er oprettet med PowerShell

Kør følgende kommandoer i PowerShell for at oprette en regel for mailflow i Exchange, der automatisk krypterer mails, der sendes uden for din organisation, med indstillingen kun kryptering, hvis mails eller deres vedhæftede filer indeholder følgende typer af følsomme oplysninger:

- ABA-registreringsnummer
- Kreditkortnummer
- Håndhævelsesorgan (DEA)
- USA/Storbritannien pasnummer
- AMERIKANSK bankkontonummer
- USA Id-nummer for individuelle skatteydere (ITIN)
- USA CPR-nummer (SSN)

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Du kan finde flere [oplysninger under Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) [og New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Sådan får modtagere adgang til vedhæftede filer

Når Microsoft har krypteret en meddelelse, har modtagerne ubegrænset adgang til vedhæftede filer, når de får adgang til og åbner deres krypterede mail.

## <a name="to-prepare-for-this-change"></a>Sådan forberedes denne ændring

Det kan være en ide at opdatere al relevant dokumentation for slutbrugeren og undervisningsmaterialer for at forberede personer i din organisation til denne ændring. Del disse Office 365-meddelelseskryptering med dine brugere efter behov:

- [Send, få vist og svar på krypterede meddelelser i Outlook til pc](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [Microsoft 365 Essentials Video: Office af meddelelseskryptering](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Få vist disse ændringer i overvågningsloggen

Microsoft 365 denne aktivitet og gør den tilgængelig for administratorer. Handlingen er "New-TransportRule", og et kodestykke fra overvågningsloggens søgning i overvågningsloggen i Security & Compliance Center er nedenfor:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"…etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Sådan deaktiverer eller tilpasser du politikken for typer af følsomme oplysninger

Når du har oprettet reglen Exchange-mailflow, kan du deaktivere eller redigere reglen [](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) ved at gå til **MailflowRules** >  i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> Administration og deaktivere reglen "Kryptere udgående følsomme mails *(out of box rule)*".