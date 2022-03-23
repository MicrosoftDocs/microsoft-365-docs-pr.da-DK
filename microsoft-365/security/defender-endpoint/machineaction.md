---
title: machineAction-ressourcetype
description: Få mere at vide om metoder og egenskaber for ressourcetypen MachineAction i Microsoft Defender til slutpunkt.
keywords: API'er, understøttede API'er, hent, machineaction, seneste
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
ms.technology: mde
ms.openlocfilehash: 625170f0e589ece6f6277dc8445f3af7bef11837
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63593798"
---
# <a name="machineaction-resource-type"></a>Ressourcetypen MachineAction

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)


[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


- Du kan få mere at vide under [Svarhandlinger](respond-machine-alerts.md).

|Metode|Returtype|Beskrivelse|
|---|---|---|
|[List MachineActions](get-machineactions-collection.md)|[Computerhandling](machineaction.md)|Enheder [for listemaskinehandling](machineaction.md) .|
|[Hent MachineAction](get-machineaction-object.md)|[Computerhandling](machineaction.md)|Få en enkelt [enhed med maskine-handling](machineaction.md) .|
|[Pakke til samlet undersøgelse](collect-investigation-package.md)|[Computerhandling](machineaction.md)|Indsamle undersøgelsespakke fra en [computer](machine.md).|
|[Hent undersøgelsespakken SAS URI](get-package-sas-uri.md)|[Computerhandling](machineaction.md)|Hent URI'en til at hente undersøgelsespakken.|
|[Isoler maskine](isolate-machine.md)|[Computerhandling](machineaction.md)|[Isoler maskine](machine.md) fra netværk.|
|[Frigiv computer fra isolation](unisolate-machine.md)|[Computerhandling](machineaction.md)|[Frigiv maskine](machine.md) fra Isolation.|
|[Begræns appudførelse](restrict-code-execution.md)|[Computerhandling](machineaction.md)|Begræns udførelsen af programmet.|
|[Fjern appbegrænsning](unrestrict-code-execution.md)|[Computerhandling](machineaction.md)|Fjern begrænsningen af programudførelsen.|
|[Kør antivirusscanning](run-av-scan.md)|[Computerhandling](machineaction.md)|Kør en AV-scanning ved hjælp Windows Defender (hvis relevant).|
|[Offboard machine](offboard-machine-api.md)|[Computerhandling](machineaction.md)|Offboard [machine](machine.md) fra Microsoft Defender for Endpoint.|
|[Stop og karantæne-fil](stop-and-quarantine-file.md)|[Computerhandling](machineaction.md)|Stop udførelse af en fil på en computer, og slet den.|
|[Kør live-svar](run-live-response.md)|[Computerhandling](machineaction.md)|Kører en sekvens af live svarkommandoer på en enhed|
|[Få direkte svarresultat](get-live-response-result.md)|URL-enhed|Henter et specifikt link til live response-kommandoresultatet ved hjælp af dets indeks.|
|[Annuller computerhandling](cancel-machine-action.md)|[Computerhandling](machineaction.md)|Annuller en aktiv computerhandling.|

<br>

## <a name="properties"></a>Egenskaber

|Egenskab|Type|Beskrivelse|
|---|---|---|
|Id|Guid|Identiteten på [enhedsenheden Computerhandling](machineaction.md) .|
|type|Enum|Typen af handlingen. Mulige værdier er: "RunAntiVirusScan", "Offboard", "Live Response", "CollectInvestigationPackage", "Isolate", "Unisolate", "StopAndQuarantineFile", "RestrictCodeExecution" og "UnrestrictCodeExecution".|
|område|streng|Handlingens omfang. "Fuld" eller "Selektiv" for isolation, "Hurtig" eller "fuld" for antivirusscanning.|
|anmoder|String|Identiteten på den person, der udførte handlingen.|
|externalID|String|Id, som kunden kan sende i anmodningen om brugerdefineret korrelation.|
|requestSource|streng|Navnet på den bruger/det program, der sendte handlingen.|
|kommandoer|matrix|Kommandoer, der skal køres. Tilladte værdier er PutFile, RunScript, GetFile.|
|cancellationRequestor|String|Identiteten på den person, der annullerede handlingen.|
|requestorComment|String|Kommentar, der blev skrevet under udstedelsen af handlingen.|
|annulleringComment|String|Kommentar, der blev skrevet, da handlingen blev annulleret.|
|status|Enum|Kommandoens aktuelle status. Mulige værdier er: "Afventer", "InProgress", "Udført", "Mislykkedes", "TimeOut" og "Annulleret".|
|machineId|String|Id for [den computer](machine.md) , hvor handlingen blev udført.|
|computerDnsName|String|Navnet på den [computer](machine.md) , hvor handlingen blev udført.|
|creationDateTimeUtc|DateTimeOffset|Dato og klokkeslæt for, hvornår handlingen blev oprettet.|
|cancellationDateTimeUtc|DateTimeOffset|Dato og klokkeslæt for, hvornår handlingen blev annulleret.|
|lastUpdateDateTimeUtc|DateTimeOffset|Den seneste dato og det sidste klokkeslæt, hvor handlingsstatussen blev opdateret.|
|titel|String|Titel på computerhandling.|
|relatedFileInfo|Klasse|Indeholder to egenskaber. streng `fileIdentifier`, Enum `fileIdentifierType` med de mulige værdier: "Sha1", "Sha256" og "Md5".|

## <a name="json-representation"></a>Json-repræsentation

```json
{
        "id": "5382f7ea-7557-4ab7-9782-d50480024a4e",
        "type": "Isolate",
        "scope": "Selective",
        "requestor": "Analyst@TestPrd.onmicrosoft.com",
        "requestorComment": "test for docs",
        "status": "Succeeded",
        "machineId": "7b1f4967d9728e5aa3c06a9e617a22a4a5a17378",
        "computerDnsName": "desktop-test",
        "creationDateTimeUtc": "2019-01-02T14:39:38.2262283Z",
        "lastUpdateDateTimeUtc": "2019-01-02T14:40:44.6596267Z",
        "relatedFileInfo": null
}
```
