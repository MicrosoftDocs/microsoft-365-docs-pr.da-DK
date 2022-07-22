---
title: Definition af enhed for bulgariens licensnummer for drivere
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
description: Enhedsdefinitionen af enheden for følsomme oplysninger for bulgariens licensnummer.
ms.openlocfilehash: ed43c47dde5d421c81778465d0025c363c65f8b8
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66944778"
---
# <a name="bulgaria-drivers-license-number"></a>Bulgariens kørekortsnummer

## <a name="format"></a>Format

ni cifre uden mellemrum og afgrænsere

## <a name="pattern"></a>Mønster

ni cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_bulgaria_eu_driver's_license_number` finder indhold, der svarer til mønsteret.
- Et nøgleord fra `Keywords_eu_driver's_license_number` eller `Keywords_bulgaria_eu_driver's_license_number` findes.

```xml
      <!-- Bulgaria Driver's License Number -->
      <Entity id="66d39258-94c2-43b2-804b-aa312258e54b" patternsProximity="300" recommendedConfidence="75">
        <Pattern confidenceLevel="75">
          <IdMatch idRef="Regex_bulgaria_eu_driver's_license_number" />
          <Any minMatches="1">
            <Match idRef="Keywords_eu_driver's_license_number" />
            <Match idRef="Keywords_bulgaria_eu_driver's_license_number" />
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

### <a name="keywords_bulgaria_eu_drivers_license_number"></a>Keywords_bulgaria_eu_driver er s_license_number

- свидетелство за управление на мпс
- свидетелство за управление на моторно превозно средство
- сумпс
- шофьорска книжка
- шофьорски книжки