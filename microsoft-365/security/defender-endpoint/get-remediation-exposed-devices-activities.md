---
title: Vis blotsatte enheder for én afhjælpningsaktivitet
description: Returnerer oplysninger om eksponerede enheder for den angivne afhjælpningsopgave.
keywords: apis, afhjælpning, afhjælpnings-API, hent, afhjælpningsopgaver, afhjælpningsudsatte enheder
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 1a7dffa064b68b2c1ce0296b66eef663eb471496
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63593240"
---
# <a name="list-exposed-devices-of-one-remediation-activity"></a>Vis blotsatte enheder for én afhjælpningsaktivitet

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Returnerer oplysninger om eksponerede enheder for den angivne afhjælpningsopgave.

[Få mere at vide om afhjælpningsaktiviteter](tvm-remediation.md).

## <a name="list-exposed-devices-associated-with-a-remediation-task-id"></a>Vis eksponerede enheder, der er knyttet til en afhjælpningsopgave (id)

**URL-adresse:** GET: /api/remediationTasks/\{id\}/machineReferences

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|RemediationTasks.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|RemediationTask.Read.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

## <a name="properties-details"></a>Oplysninger om egenskaber

Egenskab (id)|Datatype|Beskrivelse|Eksempel
:---|:---|:---|:---
id|String|Enheds-id|w2957837fwda8w9ae7f023dba081059dw8d94503
computerDnsName|String|Enhedsnavn|PC-SRV2012R2Foo.UserNameVldNet.local
osPlatform|String|Enhedsoperativsystemer|WindowsServer2012R2
rbacGroupName|String|Navnet på den enhedsgruppe, som denne enhed er knyttet til|Servere

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/03942ef5-aecb-4c6e-b555-d6a97013844c/machinereferences
```

### <a name="response-example"></a>Eksempel på svar

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "3cb5df6bb3640a2d37ad09fcd357b182d684fafc",
            "computerDnsName": "ComputerPII_2ea21b2d97c9df23c143ad9e3e454cb674232529.DomainPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3d9b1ca53e8f077199c7dcbfc9dbfa78f9bf1918",
            "computerDnsName": "ComputerPII_001d606fc149567c192747f48fae304b43c0ddba.DomainxPII_21eed80b086e79bdfa178eabfa25e8be9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3db8b27e6172951d7ea2e2d75945abec56feaf82",
            "computerDnsName": "ComputerPII_ce60cfbjj4b82a091deb5eae560332bba99a9bd7.DomainPII_0bc1aee0fa396d175e514bd61a9e7a5b2b07ee8e.corp.contoso.com",
            "osPlatform": "WindowsServer2016",
            "rbacGroupName": "UnassignedGroup",

        },
        {
            "id": "3bad326dcda5b53fab47408cd4a7080f3f3cc8ab",
            "computerDnsName": "ComputerPII_b6b35960dd6539d1d1cef5ada02e235e7b357408.DomainPII_21eed80b089e76bdfa178eadfa25e8de9acfa346.corp.contoso.com",
            "osPlatform": "WindowsServer2012R2",
            "rbacGroupName": "UnassignedGroup",

        }
]
}
```

## <a name="see-also"></a>Se også

- [Afhjælpningsmetoder og egenskaber](get-remediation-methods-properties.md)
- [Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)
- [Vis alle afhjælpningsaktiviteter](get-remediation-all-activities.md)
- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sårbarheder i din organisation](tvm-weaknesses.md)
