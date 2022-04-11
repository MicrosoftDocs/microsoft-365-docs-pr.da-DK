---
title: Opret en politik for følsomme oplysninger ved hjælp af Office 365 meddelelseskryptering
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
description: Få mere at vide om, hvordan du opretter en politik for følsomme oplysninger for din organisation ved hjælp af Office 365 Meddelelseskryptering.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: a12c3c559fdd9dcc7bd142e5ee7d58d777211bc7
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64759407"
---
# <a name="create-a-sensitive-information-type-policy-for-your-organization-using-message-encryption"></a>Opret en politik for følsomme oplysninger for din organisation ved hjælp af meddelelseskryptering

Du kan bruge enten Exchange regler for mailflow eller DLP (Forebyggelse af datatab) til at oprette en politik for følsomme oplysninger med Office 365 meddelelseskryptering. Hvis du vil oprette en Exchange mailflowregel, kan du enten bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> eller PowerShell.

## <a name="to-create-the-policy-by-using-mail-flow-rules-in-the-eac"></a>Sådan opretter du politikken ved hjælp af regler for mailflow i EAC

Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>, og gå til **MailflowRules** > . På siden Regler skal du oprette en regel, der anvender Office 365 Meddelelseskryptering. Du kan oprette en regel baseret på betingelser, f.eks. tilstedeværelsen af bestemte nøgleord eller følsomme oplysningstyper i meddelelsen eller den vedhæftede fil.

### <a name="to-create-the-policy-by-using-mail-flow-rules-in-powershell"></a>Sådan opretter du politikken ved hjælp af regler for mailflow i PowerShell

Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, start en Windows PowerShell session, og opret forbindelse til Exchange Online. Du kan finde instruktioner [under Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Brug cmdlet'erne Set-IRMConfiguration og New-TransportRule til at oprette politikken.

## <a name="example-mail-flow-rule-created-with-powershell"></a>Eksempel på en regel for mailflow, der er oprettet med PowerShell

Kør følgende kommandoer i PowerShell for at oprette en regel for Exchange mailflow, der automatisk krypterer mails, der sendes uden for din organisation, med indstillingen Kun krypteret, hvis mails eller deres vedhæftede filer indeholder følgende typer følsomme oplysninger:

- ABA-routingnummer
- Kreditkortnummer
- Dea-nummer (Drug Enforcement Agency)
- Amerikansk/britisk pasnummer
- Amerikansk bankkontonummer
- Id-nummer for individuelle amerikanske skatteborgere (ITIN)
- SSN (US Social Security Number)

```powershell
Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
New-TransportRule -Name "Encrypt outbound sensitive emails (out of box rule)" -SentToScope  NotInOrganization  -ApplyRightsProtectionTemplate "Encrypt" -MessageContainsDataClassifications @(@{Name="ABA Routing Number"; minCount="1"},@{Name="Credit Card Number"; minCount="1"},@{Name="Drug Enforcement Agency (DEA) Number"; minCount="1"},@{Name="U.S. / U.K. Passport Number"; minCount="1"},@{Name="U.S. Bank Account Number"; minCount="1"},@{Name="U.S. Individual Taxpayer Identification Number (ITIN)"; minCount="1"},@{Name="U.S. Social Security Number (SSN)"; minCount="1"}) -SenderNotificationType "NotifyOnly"
```

Du kan få flere oplysninger under [Set-IRMConfiguration](/powershell/module/exchange/set-irmconfiguration) og [New-TransportRule](/powershell/module/exchange/new-transportrule).

## <a name="how-recipients-access-attachments"></a>Sådan får modtagerne adgang til vedhæftede filer

Når Microsoft har krypteret en meddelelse, har modtagerne ubegrænset adgang til vedhæftede filer, når de får adgang til og åbner deres krypterede mail.

## <a name="to-prepare-for-this-change"></a>Som forberedelse til denne ændring

Det kan være en god idé at opdatere relevant dokumentation og undervisningsmateriale til slutbrugere for at forberede personer i din organisation på denne ændring. Del disse Office 365 ressourcer til meddelelsekryptering med dine brugere efter behov:

- [Send, få vist og besvar krypterede meddelelser i Outlook til pc](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)
- [video om Microsoft 365 Essentials: Office meddelelsekryptering](https://youtu.be/CQR0cG_iEUc)

## <a name="view-these-changes-in-the-audit-log"></a>Vis disse ændringer i overvågningsloggen

Microsoft 365 overvåger denne aktivitet og gør den tilgængelig for administratorer. Handlingen er 'New-TransportRule', og et kodestykke for en eksempelrevisionspost fra søgningen i overvågningsloggen i Security & Compliance Center er nedenfor:

```text
*{"CreationTime":"2018-11-28T23:35:01","Id":"a1b2c3d4-daa0-4c4f-a019-03a1234a1b0c","Operation":"New-TransportRule","OrganizationId":"123456-221d-12345 ","RecordType":1,"ResultStatus":"True","UserKey":"Microsoft Operator","UserType":3,"Version":1,"Workload":"Exchange","ClientIP":"123.456.147.68:17584","ObjectId":"","UserId":"Microsoft Operator","ExternalAccess":true,"OrganizationName":"contoso.onmicrosoft.com","OriginatingServer":"CY4PR13MBXXXX (15.20.1382.008)","Parameters": {"Name":"Organization","Value":"123456-221d-12346"{"Name":"ApplyRightsProtectionTemplate","Value":"Encrypt"},{"Name":"Name","Value":"Encrypt outbound sensitive emails (out of box rule)"},{"Name":"MessageContainsDataClassifications"...etc.*
```

## <a name="to-disable-or-customize-the-sensitive-information-types-policy"></a>Sådan deaktiverer eller tilpasser du politikken for følsomme oplysningstyper

Når du har oprettet reglen for Exchange mailflow, kan du [deaktivere eller redigere reglen](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#enable-or-disable-a-mail-flow-rule) ved at gå til **MailflowRules** >  i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> og deaktivere reglen "*Kryptér udgående følsomme mails (standardregel)*".