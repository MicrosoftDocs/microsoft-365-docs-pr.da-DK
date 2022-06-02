---
title: (Falske negativer) Sådan håndterer du skadelige mails, der leveres til modtagere ved hjælp af Microsoft Defender for Office 365
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
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: d9827af44cb7ea6f573f453fd1db6ac1c2de79d6
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842400"
---
# <a name="how-to-handle-malicious-emails-that-are-delivered-to-recipients-false-negatives-using-microsoft-defender-for-office-365"></a>Sådan håndterer du skadelige mails, der leveres til modtagere (falske negativer) ved hjælp af Microsoft Defender for Office 365

Microsoft Defender for Office 365 hjælper med at håndtere skadelige mails (Falsk negativ), der leveres til modtagere, og som sætter din organisations produktivitet i fare.
Defender for Office 365 kan hjælpe dig med at forstå, hvorfor mails leveres, hvordan du løser situationen hurtigt, og hvordan du forhindrer lignende situationer i at ske i fremtiden.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 1 og 2 (inkluderet som en del af E3, E5). EOP-kunder kan også udnytte dette.
- Tilstrækkelige tilladelser (rollen Sikkerhedsadministrator).
- 5-10 minutter for at udføre trinnene nedenfor.

## <a name="handling-malicious-emails-in-the-inbox-folder-of-end-users"></a>Håndtering af skadelige mails i mappen Indbakke for slutbrugere
1. Bed slutbrugerne om at rapportere mailen som **phishing** eller **uønsket** mail ved hjælp af tilføjelsesprogrammet Microsoft Meddelelse eller Tilføjelsesprogrammet Microsoft Phish eller knapperne Outlook.
2. Slutbrugere kan også føje afsenderen til [listen over blokerede afsendere](https://support.microsoft.com/en-us/office/block-a-mail-sender-b29fd867-cac9-40d8-aed1-659e06a706e4#:~:text=1%20On%20the%20Home%20tab%2C%20in%20the%20Delete,4%20Click%20OK%20in%20both%20open%20dialog%20boxes..) i Outlook for at forhindre, at mails fra denne afsenders mail ankommer til indbakker.
3. Administratorer kan sortere de brugerrapporterede meddelelser fra [brugerrapporterede indholdsportaler](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft) .
4. Fra disse rapporterede meddelelser kan administratorer **sende til** [Microsoft til analyse for](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal) at få mere at vide om, hvorfor denne mail i første omgang blev tilladt.
5. Hvis det er nødvendigt, kan administratorer, mens de sender til Microsoft til analyse, oprette en [blok for afsenderen for](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide) at afhjælpe problemet.
6. Når resultaterne for indsendelser er tilgængelige, kan du læse dommen for at forstå, hvorfor mails var tilladt, og hvordan din lejerkonfiguration kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.

## <a name="handling-malicious-emails-in-junk-folder-of-end-users"></a>Håndtering af skadelige mails i mappen uønsket mail for slutbrugere

1. Bed slutbrugerne om at rapportere mailen som **phishing** ved hjælp af Microsoft Message Add-in eller Microsoft Phish-tilføjelsesprogrammet eller knapperne Outlook.
2. Administratorer kan sortere de brugerrapporterede meddelelser fra den [brugerrapporterede indholdsportal](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft) .
3. Fra disse rapporterede meddelelser kan administratorer **sende til** [Microsoft til analyse](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal) og lære, hvorfor denne mail var tilladt i første omgang.
4. Hvis det er nødvendigt, kan administratorer, mens de sender til Microsoft til analyse, oprette en [blok for afsenderen for](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide) at afhjælpe problemet.
5. Når resultaterne for indsendelser er tilgængelige, kan du læse dommen for at forstå, hvorfor mails var tilladt, og hvordan din lejerkonfiguration kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-end-users"></a>Håndtering af ondsindede mails, der lander i slutbrugernes karantænemappe

1. Slutbrugere modtager en [oversigt over](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide) meddelelser i karantæne i henhold til de indstillinger, der er aktiveret af administratorer.
2. Slutbrugerne kan få vist meddelelserne i karantæne, blokere afsenderen og sende disse meddelelser til Microsoft til analyse.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-admins"></a>Håndtering af ondsindede mails, der lander i karantænemappen for administratorer
1. Administratorer kan få vist de karantænerede mails (herunder dem, der beder om tilladelse til at anmode om udgivelse) fra [gennemgangssiden](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide).
2. Administratorer kan sende eventuelle skadelige eller mistænkelige meddelelser til Microsoft til analyse og oprette en blok for at afhjælpe situationen, mens de venter på dom.
3. Når resultaterne for indsendelser er tilgængelige, kan du læse dommen for at få mere at vide om, hvorfor mails blev tilladt, og hvordan din lejerkonfiguration kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.
