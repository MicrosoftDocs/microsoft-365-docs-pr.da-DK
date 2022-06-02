---
title: (Falske positiver) Sådan håndterer du legitime mails, der bliver blokeret fra levering ved hjælp af Microsoft Defender for Office 365
description: Trinnene til håndtering af legitime mails, der blokeres (falsk positiv) af Microsoft Defender for Office 365 for at forhindre tab af forretning.
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
ms.openlocfilehash: 4a82bc32d1c41a3ee6e200e886cea4c325fadb02
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842397"
---
# <a name="how-to-handle-legitimate-emails-getting-blocked-false-positive-using-microsoft-defender-for-office-365"></a>Sådan håndterer du legitime mails, der blokeres (falsk positiv) ved hjælp af Microsoft Defender for Office 365

Microsoft Defender for Office 365 hjælper med at håndtere vigtige legitime forretningsmails, der ved en fejltagelse blokeres som trusler (falske positiver). Defender for Office 365 kan hjælpe administratorer med at forstå *, hvorfor* legitime mails blokeres, hvordan situationen løses hurtigt, og forhindre, at lignende situationer opstår i fremtiden.

## <a name="what-youll-need"></a>Det skal du bruge

- Microsoft Defender for Office 365 Plan 1 eller 2 (inkluderet som en del af E3, E5). EOP-kunder kan også udnytte denne funktion.
- Tilstrækkelige tilladelser (rollen Sikkerhedsadministrator).
- 5-10 minutter for at udføre trinnene nedenfor.

## <a name="handling-legitimate-emails-in-to-junk-folder-of-end-users"></a>Håndtering af legitime mails i mappen Uønsket mail for slutbrugere

1. Bed slutbrugerne om at rapportere mailen som **ikke uønsket mail** ved hjælp af Microsoft-tilføjelsesprogrammet Meddelelse eller knapperne Outlook.
2. Slutbrugere kan også føje afsenderen til [**listen over sikre afsendere**](https://support.microsoft.com/en-us/office/safe-senders-in-outlook-com-470d4ee6-e3b6-402b-8cd9-a6f00eda7339) i Outlook for at forhindre, at mailen fra disse afsendere lander i mappen Uønsket mail.
3. Administratorer kan sortere de brugerrapporterede meddelelser fra [brugerrapporteret indholdsportal](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft) .
4. Fra disse rapporterede meddelelser kan administratorer sende til [**Microsoft til analyse**](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal) og forstå, hvorfor mailen i første omgang blev blokeret.
5. Hvis det er nødvendigt, kan administratorer, mens de indsender til Microsoft til analyse, med omovervejelse oprette [en **mulighed** for, at en afsender](/microsoft-365/security/office-365-security/manage-tenant-allows?view=o365-worldwide#add-sender-allows-using-the-submissions-portal) kan afhjælpe problemet.
6. Når resultaterne fra indsendelsen af administratoren er tilgængelige, kan du læse den for at forstå, hvorfor mails blev blokeret, og hvordan din lejerkonfiguration kan forbedres for at *forhindre* , at lignende situationer opstår i fremtiden.

## <a name="handling-legitimate-emails-that-are-in-quarantine-folder-of-end-users"></a>Håndtering af legitime mails, der er i slutbrugerens karantænemappe

1. En slutbruger modtager en [mailoversigt](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide) over karantænemeddelelser i henhold til de indstillinger, der er aktiveret af sikkerhedsadministratorer.
2. Slutbrugere kan få forhåndsvist meddelelserne i karantæne, blokere afsenderen, frigive meddelelserne, sende disse meddelelser til Microsoft til analyse og anmode om udgivelse af disse mails fra administratorer.

## <a name="handling-legitimate-emails-emails-in-quarantine-folder-of-an-admin"></a>Håndtering af legitime mails i en administrators karantænemappe

1. Administratorer kan få vist de karantænerede mails (herunder dem, der beder om tilladelse til at anmode om udgivelse) fra [gennemgangssiden](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide).
2. Administratorer kan frigive meddelelsen fra karantæne, mens de sender den til Microsoft til analyse, og oprette en tilladelse til at afhjælpe situationen.
3. Når resultaterne for indsendelser er tilgængelige, skal administratorer læse dommen for at forstå, hvorfor mails blev blokeret, og hvordan lejerkonfigurationen kan forbedres for at forhindre, at lignende situationer opstår i fremtiden.