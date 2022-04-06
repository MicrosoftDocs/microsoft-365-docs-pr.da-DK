---
title: Uønsket software
ms.reviewer: ''
description: Få mere at vide om, hvordan uønsket software ændrer dine standardindstillinger uden dit samtykke, og hvad du kan gøre for at beskytte dig selv.
keywords: sikkerhed, malware, beskyttelse, uønsket, software, ændre, inficere, uønsket software, software bundlers, browser modifikatorer, beskyttelse af personlige oplysninger, sikkerhed, beregningsoplevelse, forhindre infektion, løsning, WDSI, MMPC, Microsoft Malware Protection Center, virus forskning trusler, forskning malware, pc-beskyttelse, computer infektion, virus infektion, beskrivelser, afhjælpning, seneste trusler
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 654730571de934552d983e1135f24a3299567741
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666674"
---
# <a name="unwanted-software"></a>Uønsket software

Uønsket software er programmer, der ændrer den Windows oplevelse uden dit samtykke eller kontrol. Dette kan tage form af ændret browseroplevelse, manglende kontrol over downloads og installation, vildledende meddelelser eller uautoriserede ændringer af Windows indstillinger.

## <a name="how-unwanted-software-works"></a>Sådan fungerer uønsket software

Uønsket software kan introduceres, når en bruger søger efter og downloader programmer fra internettet. Nogle programmer er software bundlere, hvilket betyder, at de er pakket med andre programmer. Andre programmer kan derfor installeres utilsigtet, når det oprindelige program downloades.

Her er nogle indikationer på uønsket software:

- Der er programmer, som du ikke har installeret, og som kan være svære at fjerne

- Browserfunktioner eller -indstillinger er blevet ændret, og du kan ikke få vist eller ændre dem

- Der er for mange meddelelser om enhedens tilstand eller om filer og programmer

- Der er annoncer, der ikke nemt kan lukkes

Nogle indikatorer er sværere at genkende, fordi de er mindre forstyrrende, men stadig er uønskede. Uønsket software kan f.eks. ændre websider, så de viser bestemte annoncer, overvåger browsingaktiviteter eller fjerner kontrollen over browseren.

Microsoft bruger et omfattende [evalueringskriterier](criteria.md) til at identificere uønsket software.

## <a name="how-to-protect-against-unwanted-software"></a>Sådan beskytter du mod uønsket software

For at forhindre uønsket software infektion, download software kun fra officielle hjemmesider, eller fra Microsoft Store. Vær forsigtig med at downloade software fra tredjepartswebsteder.

Brug [Microsoft Edge](/microsoft-edge/deploy/index), når du søger på internettet. Microsoft Edge omfatter yderligere beskyttelse, der effektivt blokerer browsermodifikatorer, som kan ændre dine browserindstillinger. Microsoft Edge blokerer også kendte websteder, der hoster uønsket software, ved hjælp af [Windows Defender SmartScreen](/microsoft-edge/deploy/index) (bruges også af Internet Explorer).

Aktivér [Microsoft Defender Antivirus](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-in-windows-10) i Windows 10. Det giver beskyttelse i realtid mod trusler og registrerer og fjerner kendt uønsket software.

Download [Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201) til beskyttelse i realtid i Windows 7 eller Windows Vista.

Du kan få mere generelle tip under [Undgå malware-infektion](prevent-malware-infection.md).

### <a name="what-should-i-do-if-my-device-is-infected"></a>Hvad skal jeg gøre, hvis min enhed er inficeret? 

Hvis du har mistanke om, at du har uønsket software, kan du [indsende filer til analyse](https://www.microsoft.com/wdsi/filesubmission).

Noget uønsket software tilføjer fjernelsesposter, hvilket betyder, at du kan **fjerne dem ved hjælp af Indstillinger**.
1. Vælg knappen Start
2. Gå til **Indstillinger > apps > &-funktioner**.
3. Vælg den app, du vil fjerne, og klik derefter på **Fjern**.

Hvis du først for nylig har bemærket symptomer på uønsket software infektion, kan du overveje at sortere apps efter installationsdato og derefter fjerne de nyeste apps, som du ikke har installeret.

Du skal muligvis også **fjerne browsertilføjelsesprogramme** i dine browsere, f.eks. Internet Explorer, Firefox eller Chrome.

Hvis fjernelse af trusler mislykkes, kan du læse om [fejlfinding af problemer med registrering og fjernelse af malware](https://support.microsoft.com/help/4466982/windows-10-troubleshoot-problems-with-detecting-and-removing-malware).