---
title: Brug kommunikation med SIEM-løsninger
description: Få mere at vide om integration af overholdelse af kommunikation med SIEM-løsninger.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
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
ms.openlocfilehash: 247999954e6ff69fdfbd2ff681bb79c0bf22c8bc
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66686113"
---
# <a name="use-communication-compliance-with-siem-solutions"></a>Brug kommunikation med SIEM-løsninger

[Overholdelse af angivne standarder for kommunikation](/microsoft-365/compliance/communication-compliance) er en insiderrisikoløsning i Microsoft Purview, der hjælper dig med at minimere kommunikationsrisici ved at hjælpe dig med at registrere, registrere og reagere på upassende meddelelser i din organisation. SIEM-løsninger (Security Information and Event Management), f.eks [. Microsoft Sentinel](https://azure.microsoft.com/services/azure-sentinel) eller [Splunk](https://www.splunk.com/) , bruges ofte til at aggregere og spore trusler i en organisation.

Et almindeligt behov for organisationer er at integrere beskeder om overholdelse af angivne standarder for kommunikation og disse SIEM-løsninger. Med denne integration kan organisationer få vist beskeder om overholdelse af angivne standarder i deres SIEM-løsning og derefter afhjælpe beskeder i arbejdsprocessen for overholdelse af kommunikation og brugeroplevelsen. En medarbejder sender f.eks. en stødende meddelelse til en anden medarbejder, og denne meddelelse registreres af en overvågning af politikken for overholdelse af kommunikation for upassende indhold. Disse hændelser spores i Microsoft 365 Audit (også kendt som "unified audit log") af løsningen til kommunikationsoverholdelse og importeres til SIEM-løsningen. Der udløses derefter en besked i SIEM-løsningen for organisationen fra hændelser, der overvåges i Microsoft 365 Audit, som er knyttet til beskeder om kommunikation med overholdelse af angivne standarder. Efterforskere får besked om advarslen i SIEM-løsningerne, og de undersøger og afhjælper derefter advarslen i løsningen til kommunikationsoverholdelse.

## <a name="communication-compliance-alerts-in-microsoft-365-audit"></a>Beskeder om kommunikation med overholdelse af angivne standarder i Microsoft 365 Audit

Alle overholdelsespolitikkampe for kommunikation registreres i Microsoft 365 Audit. Følgende eksempler viser de oplysninger, der er tilgængelige for de valgte aktiviteter for politikken for overholdelse af angivne standarder for kommunikation:

**Eksempel på en post i overvågningsloggen for et forkert indholdspolitikskabelonmatch:**

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

**Eksempel på en Post i Microsoft 365-overvågningslog for en politik med et brugerdefineret nøgleordsmatch (brugerdefineret type følsomme oplysninger):**

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
> Der kan i øjeblikket være op til en 24-timers forsinkelse mellem det tidspunkt, hvor et politikmatch registreres i Microsoft 365 Audit, og det tidspunkt, hvor du kan undersøge politikforekomster i kommunikation med overholdelse af angivne standarder.

## <a name="configure-communication-compliance-and-microsoft-sentinel-integration"></a>Konfigurer overholdelse af kommunikation og Microsoft Sentinel-integration

Når du bruger Microsoft Sentinel til at aggregere overholdelsespolitik for kommunikation, bruger Sentinel Microsoft 365 Audit som datakilde. Hvis du vil integrere beskeder om kommunikation med overholdelse af angivne standarder med Sentinel, skal du fuldføre følgende trin:

1. [Onboard til Microsoft Sentinel](/azure/sentinel/quickstart-onboard). Som en del af onboardingprocessen skal du konfigurere dine datakilder.
2. Konfigurer Microsoft Sentinel [Microsoft Office 365 dataconnector](/azure/sentinel/data-connectors-reference#microsoft-office-365), og vælg *Exchange* under connectorkonfiguration.
3. Konfigurer søgeforespørgslen for at hente beskeder om kommunikation med overholdelse af angivne standarder. Eksempel:

    *| OfficeActivity | hvor OfficeWorkload == "Exchange" og Operation == "SupervisionRuleMatch" | sortér efter TimeGenerated*

    Hvis du vil filtrere efter en bestemt bruger, skal du bruge følgende forespørgselsformat:

    *| OfficeActivity | where OfficeWorkload == "Exchange" and Operation == "SupervisionRuleMatch" and UserId == "User1@Contoso.com" | sortér efter TimeGenerated*

Du kan finde flere oplysninger om Microsoft 365-overvågningslogge for Office 365, der indsamles af Microsoft Sentinel, under [Reference til Azure Monitor Logs](/azure/azure-monitor/reference/tables/OfficeActivity).

## <a name="configure-communication-compliance-and-splunk-integration"></a>Konfigurer kommunikation med overholdelse af angivne standarder og Splunk-integration

Hvis du vil integrere beskeder om kommunikation med overholdelse af angivne standarder med Splunk, skal du udføre følgende trin:

1. Installér [tilføjelsesprogrammet Splunk til Microsoft Office 365](https://docs.splunk.com/Documentation/AddOns/released/MSO365/ConfigureinputsmanagementAPI)
2. Konfigurer et integrationsprogram i Azure AD for tilføjelsesprogrammet Splunk for Microsoft Office 365
3. Konfigurer søgeforespørgsler i din Splunk-løsning. Brug følgende søgeeksempel til at identificere alle beskeder om kommunikation med overholdelse af angivne standarder:

    *index=\* sourcetype="o365:management:activity" Workload=Exchange Operation=SupervisionRuleMatch*

Hvis du vil filtrere resultaterne for en bestemt politik for overholdelse af kommunikation, kan du bruge parameteren *SRPolicyMatchDetails.SRPolicyName* .

Følgende søgeeksempel returnerer f.eks. beskeder om matches til en politik for kommunikation med overholdelse af angivne standarder med navnet *Upassende indhold*:

  *index=\* sourcetype='o365:management:activity' Workload=Exchange Operation=SupervisionRuleMatch SRPolicyMatchDetails.SRPolicyName=\<Inappropriate content\>*

I følgende tabel vises eksempelsøgeresultater for forskellige politiktyper:

| Politiktyper | Eksempel på søgeresultater |
| :------------------ | :--------------------------------------- |
| Politik til registrering af en nøgleordsliste med brugerdefinerede følsomme oplysninger | { <br> CreationTime: 09-17T16:29:57 <br> ID: 4b9ce23d-ee60-4f66-f38d-08d979f8631f <br> IsPolicyHit: true <br> Objectid: <CY1PR05MB27158B96AF7F3AFE62E1F762CFDD9@CY1PR05MB2715.namprd05.prod.outlook.com> <br> Handling: SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM. Note","CcsiResults":"leak"} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.OnMicrosoft.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> Version: 1 <br> Arbejdsbelastning: Exchange <br> } |
| Politik til registrering af upassende sprog | { <br> CreationTime: 09-17T23:44:35 <br> ID: e0ef6f54-9a52-4e4c-9584-08d97a351ad0 <br> IsPolicyHit: true <br> Objectid: <BN6PR05MB3571AD9FBB85C4E12C1F66B4CCDD9@BN6PR05MB3571.namprd05.prod.outlook.com> <br> Handling: SupervisionRuleMatch <br> OrganizationId: d6a06676-95e8-4632-b949-44bc00f0793f <br> RecordType: 68 <br> ResultStatus: {"ItemClass":"IPM. Yammer.Message","CcsiResults":""} <br> SRPolicyMatchDetails: { [+] } <br> UserId: user1@contoso.com <br> UserKey: SupervisionStoreDeliveryAgent <br> UserType: 0 <br> Version: 1 <br> }  |

## <a name="configure-communication-compliance-with-other-siem-solutions"></a>Konfigurer overholdelse af kommunikation med andre SIEM-løsninger

Hvis du vil hente overholdelsespolitik for kommunikation fra Microsoft 365 Audit, kan du enten bruge PowerShell eller [API'en til administration af Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

Når du bruger PowerShell, kan du bruge en af disse parametre med **search-UnifiedAuditLog-cmdlet'en** til at filtrere hændelser i overvågningsloggen for aktiviteter for kommunikation med overholdelse af angivne standarder.

| Parameter for overvågningslog | Parameterværdi for kommunikation med overholdelse af angivne standarder |
| :------------------ | :--------------------------------------- |
| Operationer          | TilsynSregelmatch                     |
| Posttype          | ComplianceSupervisionExchange            |

Følgende er f.eks. en eksempelsøgning ved hjælp af parameteren **Operations** og værdien *SupervisionRuleMatch* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionRuleMatch | ft CreationDate,UserIds,AuditData
```
Følgende er et eksempel på en søgning ved hjælp af parameteren **RecordsType** og værdien *ComplianceSupervisionExchange* :

```powershell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType ComplianceSuperVisionExchange | ft CreationDate,UserIds,AuditData
```
## <a name="resources"></a>Ressourcer

- [Overvågning af kommunikation med overholdelse af angivne standarder](/microsoft-365/compliance/communication-compliance-reports-audits#audit)
- [Microsoft Purview-gennemgang (Premium)](/microsoft-365/compliance/advanced-audit)
- [Reference til Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference)
