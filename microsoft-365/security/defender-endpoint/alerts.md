---
title: Få vigtige API'er
description: Få mere at vide om metoderne og egenskaberne for ressourcetypen Påmindelse i Microsoft Defender til slutpunkt.
keywords: apis, graph api, understøttede API'er, hent, beskeder, seneste
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 3344bb13d785739f7957c3b0d000b04ae7fea95b
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63591272"
---
# <a name="alert-resource-type"></a>Ressourcetypen Besked

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="methods"></a>Metoder

<br>

****

|Metode|Returtype|Beskrivelse|
|---|---|---|
|[Få besked](get-alert-info-by-id.md)|[Besked](alerts.md)|Få et enkelt [advarselsobjekt](alerts.md) .|
|[Vis beskeder](get-alerts.md)|[Samling af](alerts.md) beskeder|Samling [af listebeskeder](alerts.md) .|
|[Opdateringsbesked](update-alert.md)|[Besked](alerts.md)|Opdater specifik [besked](alerts.md).|
|[Beskeder om batchopdatering](batch-update-alerts.md)||Opdater en batch af [beskeder](alerts.md).|
|[Opret besked](create-alert-by-reference.md)|[Besked](alerts.md)|Opret en besked baseret på hændelsesdata, der er hentet [fra Avanceret jagt](run-advanced-query-api.md).|
|[Vis relaterede domæner](get-alert-related-domain-info.md)|Domænesamling|Vis URL-adresser, der er knyttet til beskeden.|
|[Vis relaterede filer](get-alert-related-files-info.md)|[Filsamling](files.md)|Vis en [liste over](files.md) de filobjekter, der er knyttet til [beskeden](alerts.md).|
|[Listerelaterede IP'er](get-alert-related-ip-info.md)|IP-samling|Liste-IP'er, der er knyttet til beskeden.|
|[Hent relaterede computere](get-alert-related-machine-info.md)|[Computer](machine.md)|Den [computer](machine.md) , der er knyttet til [beskeden](alerts.md).|
|[Hent relaterede brugere](get-alert-related-user-info.md)|[Bruger](user.md)|Den [bruger](user.md) , der er knyttet til [beskeden](alerts.md).|
|

## <a name="properties"></a>Egenskaber

<br>

****

|Egenskab|Type|Beskrivelse|
|---|---|---|
|id|String|Besked-id.|
|titel|String|Titel for besked.|
|beskrivelse|String|Beskrivelse af besked.|
|alertCreationTime|Nullable DateTimeOffset|Den dato og det klokkeslæt (i UTC) beskeden blev oprettet.|
|lastEventTime|Nullable DateTimeOffset|Den sidste forekomst af den hændelse, der udløste beskeden på den samme enhed.|
|firstEventTime|Nullable DateTimeOffset|Den første forekomst af den hændelse, der udløste beskeden på den pågældende enhed.|
|lastUpdateTime|Nullable DateTimeOffset|Den dato og det klokkeslæt (i UTC) beskeden blev sidst opdateret.|
|resolvedTime|Nullable DateTimeOffset|Den dato og det klokkeslæt, hvor beskedens status blev ændret til "Løst".|
|incidentId|Null-værdi for lang|[Hændelses-id'et](view-incidents-queue.md) for beskeden.|
|investigationId|Null-værdi for lang|[Undersøgelses-id'et](automated-investigations.md) knyttet til beskeden.|
|undersøgelseTilstande|Null-værdi Enum|Undersøgelsens aktuelle [status](automated-investigations.md). Mulige værdier er: 'Ukendt', 'Afsluttet', 'Behæftet', 'Benign', 'Failed', 'PartiallyRemedated', 'Running', 'PendingApproval', 'PendingResource', 'PartiallyInvestigated', 'TerminatedByUser', 'TerminatedBySystem', 'Queued', 'InnerFailure', 'PreexistingAlert', 'UnsupportedOs', 'UnsupportedAlertType', 'suppressedAlert'.|
|assignedTo|String|Ejeren af beskeden.|
|rbacGroupName|String|Navn på RBAC-enhedsgruppe.|
|mitreTechniques|String|Mitre Enterprise-teknik-id.|
|relatedUser|String|Oplysninger om bruger, der er relateret til en bestemt besked.|
|alvorsgrad|Enum|Beskedens alvorsgrad. Mulige værdier er: 'Uspecificeret', 'Informational', 'Lav', 'Mellem' og 'Høj'.|
|status|Enum|Angiver beskedens aktuelle status. Mulige værdier er: "Ukendt", "Ny", "InProgress" og "Løst".|
|klassificering|Null-værdi Enum|Specifikation af beskeden. Mulige værdier er: 'Ukendt', 'FalskPositiv', 'TruePositive'.|
|determination|Null-værdi Enum|Angiver bestemmelse af beskeden. De mulige værdier er: "NotAvailable", "Apt", "Malware", "SecurityPersonnel", "SecurityTesting", "UnwantedSoftware", "Other".|
|kategori|String|Kategori for beskeden.|
|detectionSource|String|Registreringskilde.|
|threatFamilyName|String|Trusselsfamilie.|
|threatName|String|Navn på trussel.|
|machineId|String|Id for en [computerenhed](machine.md) , der er knyttet til beskeden.|
|computerDnsName|String|[fuldt](machine.md) kvalificeret navn.|
|aadTenantId|String|Id Azure Active Directory.|
|id|String|Id'et for den besked, der udløste beskeden.|
|kommentarer|Liste over vigtige kommentarer|Kommentarobjektet til påmindelse indeholder: kommentarstreng, oprettetBy-streng og createTime-datotid.|
|Beviser|Liste over bevis på besked|Beviser knyttet til beskeden. Se eksemplet nedenfor.|
|

### <a name="response-example-for-getting-single-alert"></a>Eksempel på svar for at få en enkelt besked:

```http
GET https://api.securitycenter.microsoft.com/api/alerts/da637472900382838869_1364969609
```

```json
{
    "id": "da637472900382838869_1364969609",
    "incidentId": 1126093,
    "investigationId": null,
    "assignedTo": null,
    "severity": "Low",
    "status": "New",
    "classification": null,
    "determination": null,
    "investigationState": "Queued",
    "detectionSource": "WindowsDefenderAtp",
    "detectorId": "17e10bbc-3a68-474a-8aad-faef14d43952",
    "category": "Execution",
    "threatFamilyName": null,
    "title": "Low-reputation arbitrary code executed by signed executable",
    "description": "Binaries signed by Microsoft can be used to run low-reputation arbitrary code. This technique hides the execution of malicious code within a trusted process. As a result, the trusted process might exhibit suspicious behaviors, such as opening a listening port or connecting to a command-and-control (C&C) server.",
    "alertCreationTime": "2021-01-26T20:33:57.7220239Z",
    "firstEventTime": "2021-01-26T20:31:32.9562661Z",
    "lastEventTime": "2021-01-26T20:31:33.0577322Z",
    "lastUpdateTime": "2021-01-26T20:33:59.2Z",
    "resolvedTime": null,
    "machineId": "111e6dd8c833c8a052ea231ec1b19adaf497b625",
    "computerDnsName": "temp123.middleeast.corp.microsoft.com",
    "rbacGroupName": "A",
    "aadTenantId": "a839b112-1253-6432-9bf6-94542403f21c",
    "threatName": null,
    "mitreTechniques": [
        "T1064",
        "T1085",
        "T1220"
    ],
    "relatedUser": {
        "userName": "temp123",
        "domainName": "DOMAIN"
    },
    "comments": [
        {
            "comment": "test comment for docs",
            "createdBy": "secop123@contoso.com",
            "createdTime": "2021-01-26T01:00:37.8404534Z"
        }
    ],
    "evidence": [
        {
            "entityType": "User",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": null,
            "sha256": null,
            "fileName": null,
            "filePath": null,
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": "name",
            "domainName": "DOMAIN",
            "userSid": "S-1-5-21-11111607-1111760036-109187956-75141",
            "aadUserId": "11118379-2a59-1111-ac3c-a51eb4a3c627",
            "userPrincipalName": "temp123@microsoft.com",
            "detectionStatus": null
        },
        {
            "entityType": "Process",
            "evidenceCreationTime": "2021-01-26T20:33:58.6133333Z",
            "sha1": "ff836cfb1af40252bd2a2ea843032e99a5b262ed",
            "sha256": "a4752c71d81afd3d5865d24ddb11a6b0c615062fcc448d24050c2172d2cbccd6",
            "fileName": "rundll32.exe",
            "filePath": "C:\\Windows\\SysWOW64",
            "processId": 3276,
            "processCommandLine": "rundll32.exe  c:\\temp\\suspicious.dll,RepeatAfterMe",
            "processCreationTime": "2021-01-26T20:31:32.9581596Z",
            "parentProcessId": 8420,
            "parentProcessCreationTime": "2021-01-26T20:31:32.9004163Z",
            "parentProcessFileName": "rundll32.exe",
            "parentProcessFilePath": "C:\\Windows\\System32",
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        },
        {
            "entityType": "File",
            "evidenceCreationTime": "2021-01-26T20:33:58.42Z",
            "sha1": "8563f95b2f8a284fc99da44500cd51a77c1ff36c",
            "sha256": "dc0ade0c95d6db98882bc8fa6707e64353cd6f7767ff48d6a81a6c2aef21c608",
            "fileName": "suspicious.dll",
            "filePath": "c:\\temp",
            "processId": null,
            "processCommandLine": null,
            "processCreationTime": null,
            "parentProcessId": null,
            "parentProcessCreationTime": null,
            "parentProcessFileName": null,
            "parentProcessFilePath": null,
            "ipAddress": null,
            "url": null,
            "registryKey": null,
            "registryHive": null,
            "registryValueType": null,
            "registryValue": null,
            "accountName": null,
            "domainName": null,
            "userSid": null,
            "aadUserId": null,
            "userPrincipalName": null,
            "detectionStatus": "Detected"
        }
    ]
}
```
