---
title: Kommunikationsoverholdelse med SIEM-løsninger
description: Få mere at vide om integration af kommunikationsoverholdelse med SIEM-løsninger.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: d957b5fec4341cd7335f5c5a49b6654ffaf51f68
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63594024"
---
# <a name="communication-compliance-with-siem-solutions"></a>Kommunikationsoverholdelse med SIEM-løsninger

[Kommunikationsoverholdelse](communication-compliance.md) er en insider-risikoløsning i Microsoft 365, der hjælper med at minimere kommunikationsrisici ved at hjælpe dig med at registrere, registrere og reagere på upassende meddelelser i din organisation. Sikkerhedsoplysninger og begivenhedsstyring (SIEM)-løsninger som [f.eks. Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel) eller [Splunk](https://www.splunk.com/) bruges ofte til at samle og spore trusler i en organisation.

Et almindeligt behov for organisationer er at integrere beskeder om kommunikationsoverholdelse og disse SIEM-løsninger. Med denne integration kan organisationer få vist beskeder om kommunikationsoverholdelse i deres SIEM-løsning og derefter afhjælpe beskeder i kommunikationsoverholdelsesarbejdsprocessen og brugeroplevelsen. En medarbejder sender f.eks. en stødende meddelelse til en anden medarbejder, og meddelelsen registreres af en overvågning af overholdelsespolitik for kommunikation for upassende indhold. Disse hændelser registreres i Microsoft 365 Audit (også kaldet "samlet overvågningslog") af løsningen til overholdelse af kommunikation og importeres til SIEM-løsningen. Der udløses derefter en besked i SIEM-løsningen for organisationen fra hændelser, der overvåges i Microsoft 365 Audit, som er knyttet til beskeder om kommunikationsoverholdelse. Ligene underrettes om advarslen i SIEM-løsningerne, og de undersøger og afhjælper derefter beskeden i løsningen til overholdelse af kommunikation.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>Beskeder om overholdelse af kommunikation i Microsoft 365 Audit

Alle match til overholdelse af kommunikationspolitik registreres Microsoft 365 Overvågning. Følgende eksempler viser de oplysninger, der er tilgængelige for de valgte matchaktiviteter for politikker for overholdelse af kommunikation:

**Eksempel på post i overvågningsloggen for en skabelon til upassende indholdspolitik, der matcher:**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/7/2021 5:30:11 AM
UserIds: user1@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-07T05:30:11","Id":"44e98a7e-57fd-4f89-79b8-08d941084a35","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<HE1P190MB04600526C0524C75E5750C5AC61A9@HE1P190MB0460.EURP190.PROD.OUTLOOK.COM\>","UserId":"user1@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"53be0bf4-75ee-4315-b65d-17d63bdd53ae","SRPolicyName":"Adult images","SRRuleMatchDetails":\[\]}}
ResultIndex: 24
ResultCount: 48
Identity: 44e98a7e-57fd-4f89-79b8-08d941084a35
IsValid: True
ObjectState: Unchanged
```

**Eksempel på en post Microsoft 365 overvågningslog for en politik med et brugerdefineret nøgleordsmatch (brugerdefineret type af følsomme oplysninger):**

```xml
RunspaceId: 5c7bc9b0-7672-4091-a112-0635bd5f7732
RecordType: ComplianceSupervisionExchange
CreationDate: 7/6/2021 9:50:12 PM
UserIds: user2@contoso.onmicrosoft.com
Operations: SupervisionRuleMatch
AuditData: {"CreationTime":"2021-07-06T21:50:12","Id":"5c61aae5-26fc-4c8e-0791-08d940c8086f","Operation":"SupervisionRuleMatch","OrganizationId":"338397e6\-697e-4dbe-a66b-2ea3497ef15c","RecordType":68,"ResultStatus":"{\\"ItemClass\\":\\"IPM.Note\\",\\"CcsiResults\\":\\"public\\"}","UserKey":"SupervisionStoreDeliveryAgent","UserType":0,"Version":1,"Workload":"Exchange","ObjectId":"\<20210706174831.24375086.807067@sailthru.com\>","UserId":"user2@contoso.onmicrosoft.com","IsPolicyHit":true,"SRPolicyMatchDetails":{"SRPolicyId":"a97cf128-c0fc-42a1-88e3-fd3b88af9941","SRPolicyName":"Insiders","SRRuleMatchDetails":\[{"SRCategoryName":"New insiders lexicon"}\]}}
ResultIndex: 46
ResultCount: 48
Identity: 5c61aae5-26fc-4c8e-0791-08d940c8086f
IsValid: True
ObjectState: Unchanged
```

> [!NOTE]
> Der kan i øjeblikket være op til en 24-timers forsinkelse mellem det tidspunkt, hvor et match til politikken registreres i Microsoft 365 Audit, og det tidspunkt, hvor du kan undersøge overensstemmelse mellem politikker i overensstemmelse med kommunikation.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>Konfigurer kommunikationsoverholdelse og integration af Microsoft Sentinel

Når du bruger Microsoft Sentinel til at aggregere overholdelsespolitikken for kommunikation, bruger Sentinel Microsoft 365 Audit som datakilde. Hvis du vil integrere beskeder om kommunikationsoverholdelse med Sentinel, skal du udføre følgende trin:

1. [Onboard til Microsoft Sentinel](/azure/sentinel/quickstart-onboard). Som en del af onboardingprocessen skal du konfigurere dine datakilder.
2. Konfigurer Microsoft Sentinel-Microsoft Office 365 [dataforbindelse, og](/azure/sentinel/data-connectors-reference#microsoft-office-365) under konfiguration af forbindelse skal *du Exchange*.
3. Konfigurer søgeforespørgsel for at hente beskeder om kommunikationsoverholdelse. Eksempel:

    *| OfficeActivity | hvor OfficeWorkload == "Exchange" og Operation == "SupervisionRuleMatch" | sortér efter TimeGenerated*

    Hvis du vil filtrere for en bestemt bruger, skal du bruge følgende forespørgselsformat:

    *| OfficeActivity | hvor OfficeWorkload == "Exchange" og Operation == "SupervisionRuleMatch" og UserId == "User1@Contoso.com" | sortér efter TimeGenerated*

Du kan finde flere oplysninger Microsoft 365 overvågningslogfiler til data Office 365 der er indsamlet af Microsoft Sentinel, under [Reference til Azure Monitor-logge](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>Konfigurer kommunikationsoverholdelse og integration af Splunk

Hvis du vil integrere beskeder om kommunikationsoverholdelse med Splunk, skal du udføre følgende trin:

1. Installér [Splunk-tilføjelsesprogrammet til Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. Konfigurer et integrationsprogram i Azure AD til Splunk-tilføjelsesprogrammet til Microsoft Office 365
3. Konfigurer søgeforespørgsler i din Splunk-løsning. Brug følgende søgeeksemsel til at identificere alle beskeder om kommunikationsoverholdelse:

    *index=\* sourcetype="o365:management:activity" workload=Exchange Operation=SupervisionRuleMatch*

Hvis du vil filtrere resultaterne for en bestemt politik for overholdelse af kommunikation, kan du bruge *parameteren SRPolicyMatchDetails.SRPolicyName* .

I følgende søgeeksemsel returneres der f.eks. beskeder om match til en politik for overholdelse af regler og standarder med navnet *Upassende indhold*:

  *index=\* sourcetype='o365:management:activity' workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

Følgende tabel viser eksempler på søgeresultater for forskellige politiktyper:

| Politiktyper | Eksempel på søgeresultater |
| :------------------ | :--------------------------------------- |
| Politik, der registrerer en brugerdefineret liste med nøgleord af typen følsomme oplysninger | { <br> CreationTime: 2021-09-17T16:29:57 <br> ID: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: true <br> ObjectId: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> Handling: OvervågningsregelMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM. Note","CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey: OvervågningStoreDeliveryAgent <br> UserType: 0 <br> Version: 1 <br> Arbejdsbelastning: Exchange <br> } |
| Politik, der registrerer upassende sprog | { <br> CreationTime: 2021-09-17T23:44:35 <br> ID: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: true <br> ObjectId: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> Handling: OvervågningsregelMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM.Yammer. Message","CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey: OvervågningStoreDeliveryAgent <br> UserType: 0 <br> Version: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Konfigurere kommunikationsoverholdelse med andre SIEM-løsninger

Hvis du vil hente matches af kommunikationsoverholdelsespolitik Microsoft 365 Audit, kan du enten bruge PowerShell eller [Office 365 Management API](/office/office-365-management-api/office-365-management-activity-api-reference).

Når du bruger PowerShell, kan du bruge en af disse parametre med **Search-UnifiedAuditLog-cmdlet'en** til at filtrere overvågningsloghændelser for kommunikationsoverholdelsesaktiviteter.

| Parameteren Overvågningslog | Parameterværdi for kommunikationsoverholdelse |
| :------------------ | :--------------------------------------- |
| Handlinger          | OvervågningsregelMatch                     |
| RecordType          | ComplianceSupervisionExchange            |

Følgende er f.eks. en eksempelsøgning ved hjælp af **parameteren Operations** og *SupervisionRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Følgende er en stikprøvesøgning, der bruger **RecordsType-parameteren** og *ComplianceSupervisionExchange-værdien* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Ressourcer

- [Overvågning af overholdelse af kommunikation](communication-compliance-reports-audits.md#audit)
- [Avanceret overvågning i Microsoft 365](advanced-audit.md)
- [Office 365 administrationsaktivitets-API-reference](/office/office-365-management-api/office-365-management-activity-api-reference)
