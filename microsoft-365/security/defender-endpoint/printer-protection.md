---
title: Microsoft Defender for Endpoint printerbeskyttelse til enhedsstyring
description: Microsoft Defender for Endpoint Device Control Printer Protection forhindrer brugere i at udskrive via ikke-virksomhedsprintere eller ikke-godkendte USB-printere.
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.author: dansimp
author: lovina-saldanha
ms.reviewer: dansimp
manager: dansimp
audience: ITPro
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 9a700cd57b7843625f40289b43acd0e7a7eda45a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466669"
---
# <a name="device-control-printer-protection"></a>Printerbeskyttelse til enhedsstyring

**Gælder for**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint Device Control Printer Protection forhindrer brugere i at udskrive via ikke-virksomhedsprintere eller ikke-godkendte USB-printere.

## <a name="licensing"></a>Licensering

Før du går i gang med Printerbeskyttelse, skal du [bekræfte dit Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1). For at få adgang til og bruge Printerbeskyttelse skal du have følgende:

- Microsoft 365 E3 til installation af funktionalitet/politik
- Microsoft 365 E5 til rapportering

## <a name="permission"></a>Tilladelse

For udrulning af politik i Intune skal kontoen have tilladelse til at oprette, redigere, opdatere eller slette enhedskonfigurationsprofiler for at kunne installere politik via OMA-URI. Du kan oprette brugerdefinerede roller eller bruge en af de indbyggede roller med disse tilladelser:

- Politik og profiladministratorrolle.
- Eller brugerdefineret rolle med tilladelsen Opret/Rediger/Opdater/Læs/Slet/Vis rapporter aktiveret for Enhedskonfigurationsprofiler
- Eller Global administrator

Hvis du vil have vist rapporter om enhedskonfiguration, skal kontoen have visningsrapporter. Du kan oprette brugerdefinerede roller eller bruge de indbyggede roller med disse tilladelser:

- Global sikkerhedsadministrator
- Sikkerhedsadministrator
- Sikkerhedslæser

## <a name="prepare-your-endpoints"></a>Forbered dine slutpunkter

Sørg for, at Windows 10 eller Windows 11, du planlægger at udrulle Printerbeskyttelse, så de opfylder disse krav.

1. Følgende Windows installeres.
    - For Windows 1809: installér Windows Update [KB5003217](https://support.microsoft.com/topic/may-20-2021-kb5003217-os-build-17763-1971-preview-08687c95-0740-421b-a205-54aa2c716b46)
    - For Windows 1909: installér Windows Update [KB5003212](https://support.microsoft.com/topic/may-20-2021-kb5003212-os-build-18363-1593-preview-05381524-8380-4b30-b783-e330cad3d4a1)
    - I Windows 2004 eller nyere

2. Hvis du planlægger at implementere politik via Gruppepolitik, skal enheden være onboardet til Microsoft Defender for Endpoint. Hvis du planlægger at implementere politik via Microsoft Endpoint Manager, skal enheden være forbundet ved hjælp af Microsoft Intune.

## <a name="deploy-device-control-printer-protection-policy"></a>Implementer politik for printerbeskyttelse af enhedskontrol

Du kan implementere politikken via Gruppepolitik eller Intune.

<br>

****

|Titel|Beskrivelse|CSP-support | Understøttelse af gruppepolitikobjekt | Brugerbaseret support | Computerbaseret support |
|---|---|:---:|:---:|:---:|:---:|
|**Aktivér begrænsninger for udskrivning af enhedskontrol**|Bloker personer fra at udskrive via ikke-virksomhedsprinter|Ja|Ja|Ja|Ja|
|**Liste over godkendte USB-tilsluttede udskrivningsenheder**\*|Tillad en bestemt USB-printer|Ja|Ja|Ja|Ja|
|

\* Denne politik skal bruges sammen med begrænsninger for **udskrivning af Aktivér enhedsstyring**.

## <a name="deploy-policy-via-intune"></a>Installér politik via Intune

For Intune understøtter Enhedsstyring Printerbeskyttelse kun OMA-URI.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-intune"></a>Scenarie 1: Bloker personer fra at udskrive via en hvilken som helst printer uden for firmaet Intune

- Anvend politik over en computer:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControl`

- Anvend politik over bruger:

  `./Vendor/MSFT/Policy/Config/Printers/EnableDeviceControlUser`

CSP-supportstrengen med `<enabled/>`:

:::image type="content" source="../../media/customeditrow.png" alt-text="Siden Brugerdefineret" lightbox="../../media/customeditrow.png":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-intune"></a>Scenarie 2: Tillad bestemte godkendte USB-printere at bruge Intune

- Anvend politik over en computer:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevices`

- Anvend politik over bruger:

  `./Vendor/MSFT/Policy/Config/Printers/ApprovedUsbPrintDevicesUser`

CSP-supportstrengen med godkendte USB-printere via egenskaben "ApprovedUsbPrintDevices", eksempel `<enabled><data id="ApprovedUsbPrintDevices_List" value="03F0/0853,0351/0872"/>`:

:::image type="content" source="../../media/editrow.png" alt-text="Ruden Rediger række" lightbox="../../media/editrow.png":::

## <a name="deploy-policy-via-group-policy"></a>Implementer politik via Gruppepolitik

Hvis enheden ikke er Intune, kan du også installere politikken via Gruppepolitik.

### <a name="scenario-1-block-people-from-printing-via-any-non-corporate-printer-using-group-policy"></a>Scenarie 1: Bloker personer fra at udskrive via en hvilken som helst ikke-virksomhedsprinter, der bruger Gruppepolitik

- Anvend politik over en computer:

  Printer til administrative \> skabeloner til \> computerkonfiguration: Aktivér begrænsninger for udskrivning af enheder

- Anvend politik over bruger:

  Administrative skabeloner til \> brugerkonfiguration \> Kontrolpanel printere\>: Aktivér begrænsninger for udskrivning af enheder

:::image type="content" source="../../media/enable-device-ctrl-printing-restrictions.png" alt-text="Ruden Aktivér begrænsninger for udskrivning af enhedsstyring" lightbox="../../media/enable-device-ctrl-printing-restrictions.png":::

### <a name="scenario-2-allow-specific-approved-usb-printers-using-group-policy"></a>Scenarie 2: Tillad, at bestemte godkendte USB-printere Gruppepolitik

- Anvend politik over en computer:

  Printer til administrative \> skabeloner til \> computerkonfiguration: Liste over godkendte USB-tilsluttede udskrivningsenheder

- Anvend politik over bruger:

  Administrative skabeloner til \> brugerkonfiguration \> Kontrolpanel printere\>: Liste over godkendte USB-tilsluttede udskrivningsenheder

:::image type="content" source="../../media/list-of-approved-connected-print-devices.png" alt-text="Listen over godkendte USB-tilsluttede udskrivningsenheder" lightbox="../../media/list-of-approved-connected-print-devices.png":::

## <a name="view-device-control-printer-protection-data-in-microsoft-defender-for-endpoint-portal"></a>Få vist printerbeskyttelsesdata for enhedskontrol i Microsoft Defender for Endpoint portal

Portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender viser udskrivning</a>, der er blokeret af politikken til enhedskontrolprinterbeskyttelse ovenfor.

```kusto
DeviceEvents
| where ActionType == 'PrintJobBlocked'
| extend parsed=parse_json(AdditionalFields)
| extend PrintedFile=tostring(parsed.JobOrDocumentName)
| extend PrintPortName=tostring(parsed.PortName)
| extend PrinterName=tostring(parsed.PrinterName)
| extend Policy=tostring(parsed.RestrictionReason) 
| project Timestamp, DeviceId, DeviceName, ActionType, InitiatingProcessAccountName, Policy, PrintedFile, PrinterName, PrintPortName, AdditionalFields
| order by Timestamp desc
```

 :::image type="content" source="../../media/device-control-advanced-hunting.png" alt-text="avanceret jagt" lightbox="../../media/device-control-advanced-hunting.png":::

 Du kan bruge PnP-begivenheden til at finde den USB-printer, der bruges i organisationen:

```kusto
//find the USB Printer VID/PID
DeviceEvents
| where ActionType == "PnpDeviceConnected"
| extend parsed=parse_json(AdditionalFields)
| extend DeviceDescription = tostring(parsed.DeviceDescription) 
| extend PrinterDeviceId = tostring(parsed.DeviceId) 
| extend VID_PID_Array = split(split(PrinterDeviceId, "\\")[1], "&")
| extend VID_PID = replace_string(strcat(VID_PID_Array[0], '/', VID_PID_Array[1]), 'VID_', '')
| extend VID_PID = replace_string(VID_PID, 'PID_', '')
| extend ClassId = tostring(parsed.ClassId) 
| extend VendorIds = tostring(parsed.VendorIds) 
| where DeviceDescription == 'USB Printing Support'
| project Timestamp , DeviceId, DeviceName, ActionType, DeviceDescription, VID_PID, ClassId, PrinterDeviceId, VendorIds, parsed
| order by Timestamp desc
```

 :::image type="content" source="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png" alt-text="Siden Avanceret jagt" lightbox="https://user-images.githubusercontent.com/81826151/128954383-71df3009-77ef-40db-b575-79c73fda332b.png":::
