---
title: Objektdefinition for indiens driveres licensnummer
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
description: Objektdefinitionen for den følsomme oplysningstype for den indiske driverlicensnummer.
ms.openlocfilehash: 444ef2aaff2ea48fec54b57026a437f1e7289580
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66945416"
---
# <a name="india-drivers-license-number"></a>Licensnummer for indiens drivere

## <a name="format"></a>Format

Alfanumerisk mønster på 15 tegn

## <a name="pattern"></a>Mønster

15 bogstaver eller cifre:

- to bogstaver, der angiver statskode
- valgfri mellemrum eller tankestreg
- to cifre, der angiver bykode
- valgfri mellemrum eller tankestreg
- fire cifre, der angiver udstedelsesår
- valgfri mellemrum eller tankestreg
- syv cifre

## <a name="checksum"></a>Checksum

Nej

## <a name="definition"></a>Definition

En DLP-politik har stor tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger i nærheden af 300 tegn:

- Det regulære udtryk `Regex_india_driving_license` finder indhold, der svarer til mønsteret.
- Der blev fundet et nøgleord fra `Keywords_eu_driver's_license_number_common` .

En DLP-politik har mellem tillid til, at den har registreret denne type følsomme oplysninger, hvis den ligger inden for en nærhed af 300 tegn:

- Det regulære udtryk `Regex_india_driving_license` finder indhold, der svarer til mønsteret.

```xml
      <!-- India Driver's License Number -->
        <Entity id="680788a3-53b6-455a-b891-c38cd76dc917" patternsProximity="300" recommendedConfidence="85" relaxProximity="true">
          <Pattern confidenceLevel="85">
            <IdMatch idRef="Regex_india_driving_license" />
            <Match idRef="Keywords_eu_driver's_license_number_common" />
          </Pattern>
          <Pattern confidenceLevel="75">
            <IdMatch idRef="Regex_india_driving_license" />
            </Pattern>
        </Entity>
```

## <a name="keywords"></a>Søgeord

### <a name="keywords_eu_drivers_license_number_common"></a>Keywords_eu_driver s_license_number_common

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