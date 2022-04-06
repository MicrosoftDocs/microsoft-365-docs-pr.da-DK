---
title: Kør live svarkommandoer på en enhed
description: Få mere at vide om, hvordan du kører en sekvens af live svarkommandoer på en enhed.
keywords: API'er, graph api, understøttede API'er, upload til bibliotek
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
MS.technology: mde
ms.custom: api
ms.openlocfilehash: e81c235105a7c7479a917c7cb7cc404e2553f2f1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606584"
---
# <a name="run-live-response-commands-on-a-device"></a>Kør live svarkommandoer på en enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Kører en sekvens af live svarkommandoer på en enhed

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 10 opkald pr. minut (yderligere anmodninger besvares med HTTP 429).

2. 25 sessioner, der kører samtidigt (anmodninger, der overskrider begrænsningsgrænsen, får et "429 - for mange anmodninger"-svar).

3. Hvis computeren ikke er tilgængelig, sættes sessionen i kø i op til 3 dage.

4. RunScript-kommandotidsouts efter 10 minutter.

5. Kommandoer til direkte svar kan ikke sættes i kø og kan kun udføres én ad gangen.

6. Hvis den computer, du forsøger at køre dette API-opkald, er i en RBAC-enhedsgruppe, der ikke har fået tildelt et automatiseret afhjælpningsniveau, skal du som minimum aktivere det mindste afhjælpningsniveau for en given enhedsgruppe.

7. Flere live svarkommandoer kan køres på et enkelt API-opkald. Men når en direkte svarkommando mislykkes, udføres alle efterfølgende handlinger ikke.

## <a name="minimum-requirements"></a>Minimumskrav

Før du kan starte en session på en enhed, skal du opfylde følgende krav:

- **Kontrollér, at du kører en understøttet version af Windows**.

  Enheder skal køre en af følgende versioner af Windows

  - **Windows 11**
  
  - **Windows 10**
    - [Version 1909](/windows/whats-new/whats-new-windows-10-version-1909) eller nyere
    - [Version 1903](/windows/whats-new/whats-new-windows-10-version-1903) med [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)
    - [Version 1809 (RS 5)](/windows/whats-new/whats-new-windows-10-version-1809) [med KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)
    - [Version 1803 (RS 4)](/windows/whats-new/whats-new-windows-10-version-1803) med [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)
    - [Version 1709 (RS 3)](/windows/whats-new/whats-new-windows-10-version-1709) med [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)

  - **Windows Server 2019 – gælder kun for offentlig prøveversion**
    - Version 1903 eller (med [KB4515384](https://support.microsoft.com/help/4515384/windows-10-update-kb4515384)) senere
    - Version 1809 (med [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818))
    
  - **Windows Server 2022**

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, under [Introduktion](apis-intro.md).

|Tilladelsestype|Tilladelse|Visningsnavn for tilladelse|
|---|---|---|
|Program|Machine.LiveResponse|Kør live svar på en bestemt computer|
|Delegeret (arbejds- eller skolekonto)|Machine.LiveResponse|Kør live svar på en bestemt computer|

## <a name="http-request"></a>HTTP-anmodning

```HTTP
POST https://api.securitycenter.microsoft.com/API/machines/{machine_id}/runliveresponse
```

## <a name="request-headers"></a>Anmod om brevhoveder

|Navn|Type|Beskrivelse|
|---|---|---|
|Godkendelse|String|Bearer\<token>\. Påkrævet.|
|Indholdstype|streng|application/json. Påkrævet.|

## <a name="request-body"></a>Anmodningstekst

|Parameter|Type|Beskrivelse|
|---|---|---|
|Kommenter|String|Kommentar, der skal knyttes til handlingen.|
|Kommandoer|Matrix|Kommandoer, der skal køres. Tilladte værdier er PutFile, RunScript, GetFile.|

## <a name="commands"></a>Kommandoer

|Kommandotype|Parametre|Beskrivelse|
|---|---|---|
|PutFile|Nøgle: Filnavn <p> Værdi: \<file name\>|Placerer en fil fra biblioteket til enheden. Filer gemmes i en arbejdsmappe og slettes, når enheden genstarter som standard.
|RunScript|Nøgle: ScriptNavn <br> Værdi: \<Script from library\> <p> Nøgle: det hele <br> Værdi: \<Script arguments\>|Kører et script fra biblioteket på en enhed. <p>  Parameteren videregives til dit script. <p> Timeouts efter 10 minutter.|
|GetFile|Nøgle: Sti <br> Værdi: \<File path\>|Indsaml fil fra en enhed. BEMÆRK! Der skal bruges escape-skråstreger på stien.|

## <a name="response"></a>Svar

- Hvis det lykkes, returnerer denne metode 201 Oprettet.

  Handlingsenhed. Hvis en computer med det angivne id ikke blev fundet – 404 blev ikke fundet.

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```HTTP
POST https://api.securitycenter.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runliveresponse

```JSON
{
   "Commands":[
      {
         "type":"RunScript",
         "params":[
            {
               "key":"ScriptName",
               "value":"minidump.ps1"
            },
            {
               "key":"Args",
               "value":"OfficeClickToRun"
            }

         ]
      },
      {
         "type":"GetFile",
         "params":[
            {
               "key":"Path",
               "value":"C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
            }
         ]
      }
   ],
   "Comment":"Testing Live Response API"
}
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

```HTTP
HTTP/1.1 200 Ok
```

Indholdstype: program/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#MachineActions/$entity",
    "id": "{machine_action_id}",
    "type": "LiveResponse",
    "requestor": "analyst@microsoft.com",
    "requestorComment": "Testing Live Response API",
    "status": "Pending",
    "machineId": "{machine_id}",
    "computerDnsName": "hostname",
    "creationDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "lastUpdateDateTimeUtc": "2021-02-04T15:36:52.7788848Z",
    "errorHResult": 0,
    "commands": [
        {
            "index": 0,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "RunScript",
                "params": [
                    {
                        "key": "ScriptName",
                        "value": "minidump.ps1"
                    },{
                        "key": "Args",
                        "value": "OfficeClickToRun"
                    }
                ]
            }
        }, {
            "index": 1,
            "startTime": null,
            "endTime": null,
            "commandStatus": "Created",
            "errors": [],
            "command": {
                "type": "GetFile",
                "params": [{
                        "key": "Path", "value": "C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip"
                    }
                ]
            }
        }
    ]
}
```

## <a name="related-topics"></a>Relaterede emner

- [Hent computerhandlings-API](get-machineaction-object.md)
- [Få direkte svarresultat](get-live-response-result.md)
- [Annuller computerhandling](cancel-machine-action.md)
