---
title: Vis alle afhjælpningsaktiviteter
description: Returnerer oplysninger om alle afhjælpningsaktiviteter.
keywords: API'er, afhjælpning, afhjælpnings-API, hent, afhjælpningsopgaver, al afhjælpning,
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
ms.openlocfilehash: 3e387c8fb6ca9f1aca756ef2ab0b4c0684033370
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63592184"
---
# <a name="list-all-remediation-activities"></a>Vis alle afhjælpningsaktiviteter

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!Include[Prerelease information](../../includes/prerelease.md)]

[!Include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!Include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Returnerer oplysninger om alle afhjælpningsaktiviteter.

[Få mere at vide om afhjælpningsaktiviteter](tvm-remediation.md).

**URL-adresse:** GET: /api/remediationTasks
<br>[Understøtter OData V4-forespørgsler](https://www.odata.org/documentation/).
<br>OData-understøttede operatorer:
<br>```$filter``` på:  ```createdon``` og ```status``` egenskaber.
<br>```$top``` med en maks. værdi på 10.000.
<br>```$skip```.
<br>Se eksempler på [OData-forespørgsler med Microsoft Defender til slutpunkt](exposed-apis-odata-samples.md).

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Brug Microsoft Defender til endpoint-API'er for at få flere oplysninger.](apis-intro.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
:---|:---|:---
Program|RemediationTasks.Read.All|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'
Delegeret (arbejds- eller skolekonto)|RemediationTask.Read|\'Læs oplysninger om sikkerhedsrisiko og sikkerhedsrisiko\'

## <a name="properties"></a>Egenskaber

Egenskab (id)|Datatype|Beskrivelse|Eksempel på en returneret værdi
:---|:---|:---|:---
Kategori|String|Kategori af afhjælpningsaktiviteten (Software/sikkerhedskonfiguration)|Software
completerEmail|String|Hvis afhjælpningsaktiviteten blev fuldført manuelt af en person, indeholder denne kolonne deres mail|Null
completerId|String|Hvis afhjælpningsaktiviteten blev fuldført manuelt af en person, indeholder denne kolonne deres objekt-id|Null
completionMethod|String|En afhjælpningsaktivitet kan udføres "automatisk" (hvis alle enhederne er rettet) eller "manuelt" af en person, der vælger "markér som fuldført".|Automatisk
createdOn|DateTime|Tidspunktet for denne afhjælpningsaktivitet blev oprettet|2021-01-12T18:54:11.5499478Z
Beskrivelse|String|Beskrivelse af denne afhjælpningsaktivitet|Opdater Microsoft Silverlight til en nyere version for at afhjælpe kendte sårbarheder, der påvirker dine enheder.
dueOn|DateTime|Forfaldsdato, som opretteren har angivet for denne afhjælpningsaktivitet|2021-01-13T00:00:00Z
fixedDevices|.|Antallet af enheder, der er blevet rettet|2
Id|String|Id for denne afhjælpningsaktivitet|097d9735-5479-4899-b1b7-77398899df92
nameId|String|Relateret produktnavn|Microsoft Silverlight
Prioritet|String|Prioritet, som forfatteren har angivet for denne afhjælpningsaktivitet (Høj\Mellem\Lav)|Høj
productId|String|Relateret produkt-id|microsoft-_-silverlight
productivityImpactRemediationType|String|Der kan kun anmodes om nogle få konfigurationsændringer for enheder, der ikke påvirker brugere. Denne værdi angiver valget mellem "alle eksponerede enheder" eller "kun enheder uden brugerpåvirkning".|AllExposedAssets
rbacGroupNames|String|Relaterede enhedsgruppenavne|[ "Windows Servers", "Windows 11", "Windows 10" ]
recommendedProgram|String|Anbefalet program at opgradere til|Null
anbefaletVenlighed|String|Anbefalet leverandør at opgradere til|Null
recommendedVersion|String|Anbefalet version at opdatere/opgradere til|Null
relatedComponent|String|Relateret komponent i denne afhjælpningsaktivitet (svarende til den relaterede komponent for en sikkerhedsanbefaling)|Microsoft Silverlight
requesterEmail|String|Opretter-mailadresse|globaladmin@UserName.contoso.com
requesterId|String|Creator-objekt-id|r647211f-2e16-43f2-a480-16ar3a2a796r
anmoderNoter|String|De noter (gratis tekst), som forfatteren har tilføjet til denne afhjælpningsaktivitet|Null
Scid|String|SCID for den relaterede sikkerhedsanbefaling|Null
Status|String|Aktivitetsstatus for afhjælpning (aktiv/fuldført)|Aktiv
statusLastModifiedOn|DateTime|Dato for opdatering af statusfeltet|2021-01-12T18:54:11.5499487Z
targetDevices|Lang|Antal blotlagte enheder, som denne afhjælpning gælder for|43
Titel|String|Titlen på denne afhjælpningsaktivitet|Opdater Microsoft Silverlight
Type|String|Afhjælpningstype|Opdater
vendorId|String|Relateret leverandørnavn|Microsoft

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

```http
GET https://api-luna.securitycenter.windows.com/api/remediationtasks/
```

### <a name="response-example"></a>Eksempel på svar

```json
{
    "@odata.context": "https://wpatdadi-luna-stg.cloudapp.net/api/$metadata#RemediationTasks",
    "value": [
        {
            "id": "03942ef5-aewb-4w6e-b555-d6a97013844w",
            "title": "Update Microsoft Silverlight",
            "createdOn": "2021-02-10T13:20:36.4718166Z",
            "requesterId": "65548a1d-ef00-4a7a-8d19-1b967b5c36f4",
            "requesterEmail": "user1@contoso.com",
            "status": "Active",
            "statusLastModifiedOn": "2021-02-10T13:20:36.4719698Z",
            "description": "Update Silverlight to a later version  to mitigate 55 known vulnerabilities affecting your devices. Doing so can help lessen the security risk to your organization due to versions which have reached their end-of-support.",
            "relatedComponent": "Microsoft Silverlight",
            "targetDevices": 18511,
            "rbacGroupNames": [
                "UnassignedGroup",
                "hhh"
            ],
            "fixedDevices": 2866,
            "requesterNotes": "test",
            "dueOn": "2021-02-11T00:00:00Z",
            "category": "Software",
            "productivityImpactRemediationType": null,
            "priority": "Medium",
            "completionMethod": null,
            "completerId": null,
            "completerEmail": null,
            "scid": null,
            "type": "Update",
            "productId": "microsoft-_-silverlight",
            "vendorId": "microsoft",
            "nameId": "silverlight",
            "recommendedVersion": null,
            "recommendedVendor": null,
            "recommendedProgram": null
        }
    ]
}
```

## <a name="see-also"></a>Se også

- [Afhjælpningsmetoder og egenskaber](get-remediation-methods-properties.md)
- [Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)
- [Vis blotsatte enheder for én afhjælpningsaktivitet](get-remediation-exposed-devices-activities.md)
- [Risikobaserede & håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Sårbarheder i din organisation](tvm-weaknesses.md)
