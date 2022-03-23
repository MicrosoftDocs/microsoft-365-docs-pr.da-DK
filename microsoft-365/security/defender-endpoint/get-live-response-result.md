---
title: Få resultater med livesvar
description: Få mere at vide om, hvordan du kan hente et bestemt live response-kommandoresultat ved hjælp af indekset.
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
ms.openlocfilehash: bd8b3c997a8efceb2791eca4de0b0e42d47513f8
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592239"
---
# <a name="get-live-response-results"></a>Få resultater med livesvar

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]

## <a name="api-description"></a>API-beskrivelse

Henter et bestemt live response-kommandoresultat ved hjælp af dens indeks.

## <a name="limitations"></a>Begrænsninger

1. Satsbegrænsninger for denne API er 100 opkald pr. minut og 1500 opkald pr. time.

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
Program|Machine.Read.All|''Læs alle maskinprofiler''
Program|"Machine.ReadWrite.All|"Læs og skriv alle computeroplysninger"
|Delegeret (arbejds- eller skolekonto)|Machine.LiveResponse|Kør live svar på en bestemt computer|

## <a name="http-request"></a>HTTP-anmodning

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/{machine action
id}/GetLiveResponseResultDownloadLink(index={command-index})
```

## <a name="request-headers"></a>Anmod om brevhoveder

|Navn|Type|Beskrivelse|
|---|---|---|
|Godkendelse|String|Bearer {token}. Påkrævet.|

## <a name="request-body"></a>Anmodningstekst

Tom

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode 200, OK-svarkode med objekt, der indeholder linket til kommandoresultatet i *værdiegenskaben* . Dette link er gyldigt i 30 minutter og bør straks bruges til at hente pakken til et lokalt lager. Et udløbet link kan oprettes igen af et andet opkald, og der er ingen grund til at køre livesvar igen.

*Egenskaber for runscript-afskrift:*

|Egenskab|Beskrivelse|
|---|---|
|script_name|Navn på udført script|
|exit_code|Eksekveret script-udgangskode|
|script_output|Udført scriptstandardoutput|
|script_errors|Fejloutput for eksekveret scriptstandard|

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

Her er et eksempel på anmodningen.

```HTTP
GET https://api.securitycenter.microsoft.com/api/machineactions/988cc94e-7a8f-4b28-ab65-54970c5d5018/GetLiveResponseResultDownloadLink(index=0)
```

### <a name="response-example"></a>Eksempel på svar

Her er et eksempel på svaret.

HTTP/1.1 200 Ok

Indholdstype: program/json

```JSON
{
    "@odata.context": "https://api.securitycenter.microsoft.com/api/$metadata#Edm.String",
    "value": "https://core.windows.net/investigation-actions-data/ID/CustomPlaybookCommandOutput/4ed5e7807ad1fe59b00b664fe06a0f07?se=2021-02-04T16%3A13%3A50Z&sp=r&sv=2019-07-07&sr=b&sig=1dYGe9rPvUlXBPvYSmr6/OLXPY98m8qWqfIQCBbyZTY%3D"
}
```

*Filindhold:*

```JSON
{
    "script_name": "minidump.ps1",
    "exit_code": 0,
    "script_output": "Transcript started, output file is C:\\ProgramData\\Microsoft\\Windows Defender Advanced Threat Protection\\Temp\\PSScriptOutputs\\PSScript_Transcript_{TRANSCRIPT_ID}.txt
C:\\windows\\TEMP\\OfficeClickToRun.dmp.zip\n51 MB\n\u0000\u0000\u0000",
    "script_errors":""
}
```

## <a name="related-topics"></a>Relaterede emner

- [Hent computerhandlings-API](get-machineaction-object.md)
- [Annuller computerhandling](cancel-machine-action.md)
- [Kør live-svar](run-live-response.md) 
