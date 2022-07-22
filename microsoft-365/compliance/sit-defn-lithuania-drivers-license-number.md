---
title: Definition af enhed for litauiske driveres licensnummer
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
search.appverid: MET150
ms.topic: reference
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContainsSensitiveInformation
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
hideEdit: true
feedback_system: None
recommendations: false
description: Objektdefinitionen for den følsomme oplysningstype for den litauiske drivers licensnummer.
ms.openlocfilehash: 3fcca58b1148dd3d21143c12af21bcbe28d8e90d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945401"
---
# <a name="lithuania-drivers-license-number"></a>Licensnummer for litauiske drivere

## <a name="format"></a>Format

otte cifre uden mellemrum og afgrænsere

## <a name="pattern"></a>Mønster

otte cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_lithuania_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_lithuania_eu_driver's_license_number` findes.

```xml
      <!-- Lithuania Driver's License Number -->
      <Entity id="86f7628b-e0f4-4dc3-9fbc-e4300e4c7d78" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_lithuania_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_lithuania_eu_driver's_license_number" />
          </Any>
        </Pattern>
      </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_eu_drivers_license_number"></a>Keywords_eu_driver er s_license_number

- driverlic
- driverlics
- driverlicense
- driverlicenses
- driverlicence
- driverlicences
- driver lic
- driver-lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverslic
- drivere
- driverslicence
- driverslicences
- driverslicense
- driverslicenses
- drivere lic
- drivere lics
- licens til drivere
- driverlicenser
- kørekort
- kørekort
- driver'lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driver' lic
- driver'lics
- driverlicens
- driverlicenser
- kørekort
- kørekort
- driverens slic
- driver'slics
- kørekort
- kørekort
- driver'slicence
- driver'slicences
- førerens lic
- driverens lics
- kørekort
- driverlicenser
- kørekort
- kørekort
- Dl #
- Dls #
- driverlic #
- driverlics #
- driverlicense #
- driverlicenses #
- driverlicence #
- driverlicences #
- driver lic #
- driver-lics #
- driverlicens #
- driverlicenser #
- kørekort #
- driverslic #
- drivere #
- driverslicense #
- driverslicenses #
- driverslicence #
- driverslicences #
- drivere lic #
- drivere lics #
- licens til drivere #
- driverlicenser #
- kørekort #
- kørekort #
- driver'lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driver' lic #
- driver'lics #
- driverlicens #
- driverlicenser #
- kørekort #
- kørekort #
- driverens slic #
- driver'slics #
- kørekort #
- kørekort #
- driver'slicence #
- driver'slicences #
- førerens lic #
- driverens lics #
- kørekort #
- driverlicenser #
- kørekort #
- kørekort #
- Kørekort
- kørekort
- dlno #
- driv lic
- driv licen
- driv license
- driv-licenser
- driv licence
- driv licences
- driver licen
- drivere licen
- driverens licen
- kørsel af lic
- kørsel af licen
- kørekort
- Kørekort
- Kørekort
- kørekort
- dl nej
- dlno
- dl-nummer

### <a name="keywords_lithuania_eu_drivers_license_number"></a>Keywords_lithuania_eu_driver er s_license_number

- vairuotojo pažymėjimas
- vairuotojo pažymėjimo numeris
- vairuotojo pažymėjimo numeriai