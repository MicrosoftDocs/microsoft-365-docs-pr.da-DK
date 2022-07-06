---
title: Sådan identificeres indhold for anbefalinger til datastyring
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
description: Microsoft 365 Defender-portalen og Microsoft Purview-compliance-portal komme med anbefalinger til datastyring baseret på din organisations aktuelle konfiguration og giver dig mulighed for at konfigurere ting med nogle få klik. Nogle af disse anbefalinger registrerer specifikt indhold i din organisation og angiver derefter anbefalede trin til administration af dette indhold. En anbefaling kan f.eks. registrere elementer, der indeholder forretningskritisk indhold (f.eks. rettigheden advokat-klient eller NDA-oplysninger), og derefter lade dig automatisk anvende en opbevaringsmærkat på disse elementer for at sikre, at de klassificeres og opbevares efter behov. I dette emne beskrives de anbefalinger til datastyring, du kan få vist, og som beskriver, hvilket indhold der registreres for at udløse hver enkelt.
ms.openlocfilehash: 27fcc5dd07695be355fc15ba2145ffa5540673ca
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637301"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>Sådan identificeres indhold for anbefalinger til datastyring

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> og <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> komme med anbefalinger til datastyring baseret på din organisations aktuelle konfiguration og giver dig mulighed for at konfigurere ting med et par klik. Nogle af disse anbefalinger registrerer specifikt indhold i din organisation og angiver derefter anbefalede trin til administration af dette indhold. En anbefaling kan f.eks. registrere elementer, der indeholder forretningskritisk indhold (f.eks. rettigheden advokat-klient eller NDA-oplysninger), og derefter lade dig automatisk anvende en opbevaringsmærkat på disse elementer for at sikre, at de klassificeres og opbevares efter behov.

I dette emne beskrives de anbefalinger til datastyring, du kan få vist, og som beskriver, hvilket indhold der registreres for at udløse hver enkelt.

## <a name="clean-up-voicemail"></a>Ryd op i talebesked

Denne anbefaling vises, når mails, der er identificeret som meddelelsestypen 'voicemail', registreres i brugernes postkasser. Få mere at vide om [meddelelsesegenskaber i Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>Navn på rettighedsindhold for advokat/klient

Denne anbefaling vises, når et af følgende kriterier er opfyldt.

- En kombination af disse nøgleord registreres i brødteksten i en mail:
  - AVS
  - Rettighed som advokatklient
  - Attorney-Client rettighed
  - privilegeret Attorney-Client

- Alle kombinationer af disse nøgleord registreres i SharePoint- eller OneDrive-filer:
  - AVS
  - Advokatklientrettigheder*
  - Ac-rettigheder

## <a name="retain-audio-files"></a>Bevar lydfiler

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- .MP3
- . WMA
- . WAV
- . RA
- . RAM
- .RM
- . MIDTEN
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . ALAC

## <a name="retain-cad-files"></a>Bevar CAD-filer

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
- . KINA
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
- . Sikkerhed på rækkeniveau
- . X_*
- . XAS
- . XMT*
- . XPR

## <a name="retain-image-files"></a>Bevar billedfiler

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . RÅ
- .PSD
- . PSP
- .JPG
- . EXIF
- . PPM
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>Bevar NDA-indhold

Denne anbefaling vises, når et af følgende kriterier er opfyldt.

- En kombination af disse nøgleord registreres i brødteksten i en mail:
  - NDA
  - "Fortrolighedsaftale"
  - "Fortrolighedsaftale"

- Enhver kombination af disse nøgleord registreres i .PDF- eller .DOC-filer i SharePoint eller OneDrive:
  - NDA
  - Fortrolighedsaftale

## <a name="retain-software-development-files"></a>Bevar filer til softwareudvikling

Denne anbefaling vises, når en af følgende filtyper registreres i SharePoint eller OneDrive.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- .CS
- . CSS
- . DISCO
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

## <a name="retain-video-files"></a>Bevar videofiler

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
