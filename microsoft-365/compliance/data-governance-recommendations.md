---
title: Sådan identificeres indhold med anbefalinger vedrørende datastyring
f1.keywords:
- NOCSH
ms.author: brendonb
author: cabailey
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.custom: admindeeplinkDEFENDER
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Portalen Microsoft 365 Defender-portalen og Microsoft 365 Overholdelsescenter anbefalinger til datastyring baseret på din organisations aktuelle konfiguration og gør det muligt at konfigurere ting med nogle få klik. Nogle af disse anbefalinger registrerer specifikt indhold i organisationen og giver derefter anbefalede trin til at administrere indholdet. Eksempelvis kan en anbefaling registrere elementer, der indeholder forretningskritisk indhold (f.eks. advokat-klientrettigheder eller NDA-oplysninger), og derefter lade dig automatisk anvende en opbevaringsmærkat på disse elementer for at sikre, at de er klassificeret og bevaret efter behov. I dette emne vises de anbefalinger til datastyring, du kan få vist, og det beskrives, hvilket indhold der registreres for at udløse hver enkelt.
ms.openlocfilehash: cddd73fdd0c21605549450968db182883ab7e6ad
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63587689"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>Sådan identificeres indhold med anbefalinger vedrørende datastyring

Portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">og Microsoft 365 Overholdelsescenter</a> anbefalinger til datastyring baseret på din organisations aktuelle konfiguration og lader dig konfigurere ting med et par klik. Nogle af disse anbefalinger registrerer specifikt indhold i organisationen og giver derefter anbefalede trin til at administrere indholdet. Eksempelvis kan en anbefaling registrere elementer, der indeholder forretningskritisk indhold (f.eks. advokat-klientrettigheder eller NDA-oplysninger), og derefter lade dig automatisk anvende en opbevaringsmærkat på disse elementer for at sikre, at de er klassificeret og bevaret efter behov.

I dette emne vises de anbefalinger til datastyring, du kan få vist, og det beskrives, hvilket indhold der registreres for at udløse hver enkelt.

## <a name="clean-up-voicemail"></a>Ryd op i telefonsvareren

Denne anbefaling vises, når mails, der identificeres som meddelelsestypen "voicemail", registreres i brugernes postkasser. Få mere at vide [om meddelelsesegenskaber Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>Label attorney-client privilege content

Denne anbefaling vises, når et af følgende kriterier er opfyldt.

- En vilkårlig kombination af disse nøgleord registreres i brødteksten i en mail:
  - LYDMØDER
  - Attorney Client Privilege
  - Attorney-Client rettighed
  - Attorney-Client privilegeret

- Enhver kombination af disse nøgleord registreres i SharePoint eller OneDrive filer:
  - LYDMØDER
  - Attorney Client Privilege*
  - AC-rettigheder

## <a name="retain-audio-files"></a>Behold lydfiler

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- .MP3
- . WMA
- . WAV
- . RA
- . RAM
- .RM
- . MID
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . AOPERALYS

## <a name="retain-cad-files"></a>Behold CAD-filer

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- .3DXML
- . ACIS
- . ARC
- . ASM
- .CAT*
- . CGR
- . DW*
- . DX*
- . EDRW
- . IAM
- . IGES
- . IGS
- . IPT
- . JT
- . MF1
- . NEU
- . PAR
- . PKG
- . Kina
- . PRT
- . PSM
- . PWD
- . SLD*
- . TRIN
- . STL
- . STP
- . U3D
- . UNV
- . VRML
- . WRL
- . X_*
- . XAS
- . XMT*
- . XPR

## <a name="retain-image-files"></a>Behold billedfiler

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . RAW
- .PSD
- . PSP
- .JPG
- . EXIF
- . PPM
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>Behold NDA-indhold

Denne anbefaling vises, når et af følgende kriterier er opfyldt.

- En vilkårlig kombination af disse nøgleord registreres i brødteksten i en mail:
  - NDA
  - "Fortrolighedsaftale"
  - "Fortrolighedsaftale"

- Enhver kombination af disse nøgleord registreres i .PDF eller .DOC i SharePoint eller OneDrive:
  - NDA
  - Fortrolighedsaftale

## <a name="retain-software-development-files"></a>Behold softwareudviklingsfiler

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- .CS
- . CSS
- . 1.
- .HTM*
- . INC
- . JAD
- . JAVA
- .JS*
- . LIB
- . O
- . PHP
- . RC
- . RESX
- . RPT
- . RSS
- . SCPT
- . SRC
- . VB*
- . WSF
- . XCODEPROJ
- .XML
- . XSD
- . XSL*

## <a name="retain-video-files"></a>Behold videofiler

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- . AVCHD
- .AVI
- . FLV
- . MOV
- . MP2V
- .MP4
- . MP4V
- . MPE
- .MPEG
- . MPEG1
- . MPEG2
- . MPEG4
- .MPG
- . MPG2
- . MPG4
- . WMV
- . XMV
