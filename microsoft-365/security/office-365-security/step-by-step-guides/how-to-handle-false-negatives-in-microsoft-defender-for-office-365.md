---
title: (Falske negativer) Sådan håndteres skadelige mails, der leveres til modtagere ved hjælp af Microsoft Defender for Office 365
description: Trinnene til håndtering af ondsindede mails, der sendes til slutbrugere og indbakker (som falske negativer) med Microsoft Defender for Office 365 for at forhindre tab af forretning.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: jarogers
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: decbece049ea4f91deb529d2fd640816bf3f1d0c
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042149"
---
# <a name="how-to-handle-malicious-emails-that-are-delivered-to-recipients-false-negatives-using-microsoft-defender-for-office-365"></a>Sådan håndterer du skadelige mails, der leveres til modtagere (falske negativer) ved hjælp af Microsoft Defender for Office 365

Microsoft Defender for Office 365 hjælper med at håndtere skadelige mails (Falsk negativ), der leveres til modtagere, og som sætter din organisations produktivitet i fare.
Defender for Office 365 kan hjælpe dig med at forstå, hvorfor mails leveres, hvordan du løser situationen hurtigt, og hvordan du forhindrer lignende situationer i at ske i fremtiden.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 1 og 2 (inkluderet som en del af E5). Exchange Online kunder kan også udnytte dette.
- Tilstrækkelige tilladelser (rollen Sikkerhedsadministrator).
- 5-10 minutter for at udføre trinnene nedenfor.

## <a name="handling-malicious-emails-in-the-inbox-folder-of-end-users"></a>Håndtering af skadelige mails i mappen Indbakke for slutbrugere

1. Bed slutbrugerne om at rapportere mailen som **phishing** eller **uønsket** mail ved hjælp af tilføjelsesprogrammet Microsoft Meddelelse eller Tilføjelsesprogrammet Microsoft Phish eller knapperne Outlook.
2. Slutbrugere kan også føje afsenderen til [listen over blokerede afsendere](https://support.microsoft.com/en-us/office/block-a-mail-sender-b29fd867-cac9-40d8-aed1-659e06a706e4#:~:text=1%20On%20the%20Home%20tab%2C%20in%20the%20Delete,4%20Click%20OK%20in%20both%20open%20dialog%20boxes..) i Outlook for at forhindre, at mails fra denne afsender leveres til deres indbakke.
3. Administratorer kan sortere de brugerrapporterede meddelelser fra [brugerrapporterede indholdsportaler](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
4. Fra disse rapporterede meddelelser kan administratorer **sende til** [Microsoft til analyse for](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) at få mere at vide om, hvorfor denne mail i første omgang blev tilladt.
5. Hvis det er nødvendigt, kan administratorer, mens de sender til Microsoft til analyse, oprette en [blok for afsenderen for](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) at afhjælpe problemet.
6. Når resultaterne for indsendelser er tilgængelige, kan du læse dommen for at forstå, hvorfor mails var tilladt, og hvordan din lejerkonfiguration kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.

## <a name="handling-malicious-emails-in-junk-folder-of-end-users"></a>Håndtering af skadelige mails i mappen uønsket mail for slutbrugere

1. Bed slutbrugerne om at rapportere mailen som **phishing** ved hjælp af Microsoft Message Add-in eller Microsoft Phish-tilføjelsesprogrammet eller knapperne Outlook.
2. Administratorer kan sortere de brugerrapporterede meddelelser fra den [brugerrapporterede indholdsportal](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
3. Fra disse rapporterede meddelelser kan administratorer **sende til** [Microsoft til analyse](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) og lære, hvorfor denne mail var tilladt i første omgang.
4. Hvis det er nødvendigt, kan administratorer, mens de sender til Microsoft til analyse, oprette en [blok for afsenderen for](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) at afhjælpe problemet.
5. Når resultaterne for indsendelser er tilgængelige, kan du læse dommen for at forstå, hvorfor mails var tilladt, og hvordan din lejerkonfiguration kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-end-users"></a>Håndtering af ondsindede mails, der lander i slutbrugernes karantænemappe

1. Slutbrugere modtager en [oversigt over](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) meddelelser i karantæne i henhold til de indstillinger, der er aktiveret af administratorer.
2. Slutbrugerne kan få vist meddelelserne i karantæne, blokere afsenderen og sende disse meddelelser til Microsoft til analyse.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-admins"></a>Håndtering af ondsindede mails, der lander i karantænemappen for administratorer

1. Administratorer kan få vist de karantænerede mails (herunder dem, der beder om tilladelse til at anmode om udgivelse) fra [gennemgangssiden](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true).
2. Administratorer kan sende eventuelle skadelige eller mistænkelige meddelelser til Microsoft til analyse og oprette en blok for at afhjælpe situationen, mens de venter på dom.
3. Når resultaterne for indsendelser er tilgængelige, kan du læse dommen for at få mere at vide om, hvorfor mails blev tilladt, og hvordan din lejerkonfiguration kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.
