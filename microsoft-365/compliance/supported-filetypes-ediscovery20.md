---
title: Understøttede filtyper i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: En liste over understøttede filtyper i Microsoft 365 Advanced eDiscovery, herunder billedfiltyper, der understøttes af OCR-funktionen Advanced eDiscovery.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 96d469d861be3392108b53811478f94d0e59f40b
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63589537"
---
# <a name="supported-file-types-in-advanced-ediscovery"></a>Understøttede filtyper i Advanced eDiscovery

Advanced eDiscovery understøtter mange filtyper på mange forskellige niveauer. Supportfilerne er beskrevet i følgende tabeller i denne artikel. Denne liste er ikke afsluttet, og vi tilføjer nye filtyper, efterhånden som vi fortsætter vores valideringstest. Disse tabeller angiver, om en filtype understøttes til tekstudtrækning (og Optical Character Recognition eller OCR-tekstudtrækning til billedfiler), der kan vises i den oprindelige fremviser, og understøtter også Anmærkningsvisning i Advanced eDiscovery.

## <a name="archive--container"></a>Arkiv / Objektbeholder

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Beholderudtrækning|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|
|application/x-7z-compressed|Ja|Ja|Ja|.7z|
|application/x-dekomprimeret|Ja|Ja|Ja|.rar|
|application/x-tar|Ja|Ja|Ja|.tar|
|program/zip|Ja|Ja|Ja|.zip|
|

## <a name="audio--video"></a>Lyd/video

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/mp4|Ja|Ja|Nej|Ja|Nej|.f4v; .m4a; .m4v; .mp4. .mp4v; .mpeg. .mpeg4|
|lyd/mpeg|Ja|Ja|Nej|Ja|Nej|.mpeg|
|video/3gpp|Ja|Ja|Nej|Ja|Nej|.3gp|
|video/3gpp2|Ja|Ja|Nej|Ja|Nej|.3g2; .3gp2|
|video/quicktime|Ja|Ja|Nej|Ja|Nej|.moov; .mov; .qt|
|video/x-m4v|Ja|Ja|Nej|Ja|Nej|.m4v|
|

## <a name="database"></a>Database

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|Ja|Ja|Ja|Nej|Nej|.mdb|
|

## <a name="email"></a>Mail

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|Ja|Ja|Ja|Ja|Ja|.msg|
|meddelelse/rfc822|Ja|Ja|Ja|Ja|Ja|.eml|
|text/vcard-contact|Ja|Ja|Ja|Ja|Ja|.vcf|
|

## <a name="email-container"></a>Mailbeholder

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Beholderudtrækning|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|
|application/mbox|Ja|Ja|Ja|.mbox|
|application/vnd.ms-outlook-pst|Ja|Ja|Ja|.pst|
|

## <a name="html"></a>HTML

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|Ja|Ja|Ja|Ja|Ja|.xhtml|
|application/xml|Ja|Ja|Ja|Ja|Ja|.xml|
|tekst/html|Ja|Ja|Ja|Ja|Ja|.htm; .html; .shtml|
|

## <a name="image"></a>Billede

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|OCR-tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|billede/bmp|Ja|Ja|Ja|Ja|Ja|.bmp|
|image/emf|Ja|Ja|Ja|Ja|Ja|.emf|
|image/gif|Ja|Ja|Ja|Ja|Ja|.gif|
|image/jpeg|Ja|Ja|Ja|Ja|Ja|.jpeg; .jpg|
|image/png|Ja|Ja|Ja|Ja|Ja|.png|
|image/svg+xml|Ja|Ja|Ja|Ja|Nej|.svg|
|image/tiff|Ja|Ja|Ja|Ja|Ja|.tif|
|image/vnd.dwg|Ja|Ja|Ja|Ja|Ja|.dwg; .dxf|
|image/wmf|Ja|Ja|Ja|Ja|Ja|.wmf|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|Ja|Ja|Ja|Ja|Ja|.dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|Ja|Ja|Ja|Ja|Nej|.xlsb|
|application/vnd.ms-excel.sheet.macroenabled.12|Ja|Ja|Ja|Ja|Ja|.xlsm|
|application/vnd.ms-excel.template.macroenabled.12|Ja|Ja|Ja|Nej|Nej|.xltm|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|Ja|Ja|Ja|Ja|Ja|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|Ja|Ja|Ja|Ja|Ja|.xltx|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|program/onenote|Ja|Ja|Ja|Nej|Nej|.one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|Ja|Ja|Ja|Ja|Ja|.pot; .pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|Ja|Ja|Ja|Ja|Ja|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|Ja|Ja|Ja|Ja|Ja|.ppsx|
|application/vnd.openxmlformats-officedocument.presentationml.template|Ja|Ja|Ja|Ja|Ja|.potx|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|Ja|Ja|Ja|Nej|Ja|.mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|Ja|Ja|Ja|Ja|Ja|.pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|Ja|Ja|Ja|Ja|Nej||
|application/vnd.visio|Ja|Ja|Ja|Ja|Ja|.vsd|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|Ja|Ja|Ja|Ja|Ja|.dat; .doc|
|program/rtf|Ja|Ja|Ja|Ja|Ja|.doc; .rtf|
|application/vnd.ms-word.document.macroenabled.12|Ja|Ja|Ja|Ja|Ja|.docm|
|application/vnd.ms-word.template.macroenabled.12|Ja|Ja|Ja|Ja|Ja|.dotm|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|Ja|Ja|Ja|Ja|Ja|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|Ja|Ja|Ja|Ja|Ja|.dotx|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|Ja|Ja|Nej|Nej|Nej|.wps|
|application/vnd.ms-works-wp|Ja|Ja|Nej|Nej|Nej|.wps|
|

## <a name="open-document-format"></a>Åbn dokumentformat

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|Ja|Ja|Ja|Ja|Ja|.odt|
|

## <a name="other"></a>Andet

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|Ja|Ja|Ja|Ja|Ja|i/t|
|application/octet-stream|Ja|Nej|Nej|Nej|Nej|.fluid|
|application/vnd.ms-graph|Ja|Ja|Nej|Nej|Nej||
|application/winhlp|Ja|Ja|Nej|Nej|Nej|.hlp|
|application/x-tnef|Ja|Ja|Nej|Nej|Nej||
|

## <a name="plain-text"></a>Almindelig tekst

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|tekst/csv|Ja|Ja|Ja|Ja|Ja|.csv|
|tekst/almindelig|Ja|Ja|Ja|Ja|Ja|.con; .css; .csv; .dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Portable Document Format

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/pdf|Ja|Ja|Ja|Ja|Ja|.pdf|
|

## <a name="word-perfect"></a>Perfekt ord

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5,0|Ja|Ja|Ja|Nej|Nej|.wpd|
|application/vnd.wordperfect; version=5,1|Ja|Ja|Ja|Nej|Nej|.wpd|
|application/vnd.wordperfect; version=6.x|Ja|Ja|Ja|Nej|Nej|.wpd|
|

## <a name="word-pro"></a>Word Pro

<br>

****

|Mime-type|Filidentifikation|Metadataudtrækning|Tekstudtrækning|Indbygget fremviser|Anmærke fremviser|Mulige udvidelser|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|Ja|Ja|Nej|Nej|Nej|.lwp|
|
