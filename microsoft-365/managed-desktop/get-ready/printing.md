---
title: Forbered udskrivningsressourcer til Microsoft Managed Desktop
description: Vigtige trin for at sikre, at udskrivning fungerer problemfrit
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: a66075637a15eb39eda38e318070af2bcbdc8fe6
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/08/2022
ms.locfileid: "63590037"
---
# <a name="prepare-printing-resources-for-microsoft-managed-desktop"></a>Forbered udskrivningsressourcer til Microsoft Managed Desktop

Når du gør dig klar til at tilmelde dig Microsoft Managed Desktop, skal du evaluere dine udskrivningskrav og fastlægge den rette fremgangsmåde for dit miljø. Du har tre muligheder:

| Indstilling | Beskrivelse |
| ------ | ------ |
| Installér løsningen Microsoft Universal Print | Microsoft Universal Print-løsningen gør det nemt for Microsoft Managed Desktop-enheder at finde printere. Du kan få mere at vide [under Hvad er universel udskrift](/universal-print/fundamentals/universal-print-whatis). |
| Installér printere direkte ved hjælp af et brugerdefineret PowerShell-script | Følg trinnene i [afsnittet Konfigurere lokale](#set-up-local-printers) printere. |
| Brug en løsning til udskrivning i skyen, som ikke er Microsoft | Brug en udskrivningsløsning, der ikke er Microsoft-skybaseret, og som er kompatibel med Windows 10 enheder og er forbundet til Azure Active Directory domæne. Løsningen skal opfylde softwarekravene til Microsoft Managed Desktop. Du kan få mere at vide under [Krav til Microsoft-administreret skrivebordsapp](../service-description/mmd-app-requirements.md). |

Hvis printerdriverne ikke er tilgængelige fra Microsoft Update eller Microsoft Store i alle ovenstående indstillinger, skal du hente dem selv og få dem pakket til installation på dine Microsoft Managed Desktop-enheder med Microsoft Intune. Få mere at vide [under Enkeltstående Intune - Win32-appadministration](/mem/intune/apps/apps-win32-app-management)

## <a name="set-up-local-printers"></a>Konfigurere lokale printere

Følgende instruktioner forudsætter, at du har forberedt udskrivningsressourcerne og besluttet at installere printere ved hjælp af et brugerdefineret PowerShell-script.

**Sådan installerer du printere ved hjælp af et brugerdefineret PowerShell-script:**

1. Gå til Microsoft Managed Desktop-portalen.
1. Indsend en anmodning med *navnet Printer* i **sektionen Support > supportanmodninger** på administrationsportalen.
1. Angiv følgende oplysninger:
    - Alle UNC-stier til delte printerplaceringer, der skal installeres på Microsoft Managed Desktop-enheder.
    - Brugergrupper, der kræver adgang til disse delte printere.
1. Ved hjælp af administrationsportalen giver vi dig besked, når anmodningen er afsluttet. Til at begynde med installerer vi kun konfigurationen på enheder i gruppen Testinstallation.
1. Test og bekræft, om konfigurationen fungerer som forventet.
1. Svar ved hjælp af **fanen Diskussion** i supportanmodningen for at fortælle os, når du har fuldført testen.
1. Vi udruller derefter konfigurationen til de andre installationsgrupper.

## <a name="steps-to-get-ready"></a>Trin til at blive klar

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. [Forberede brugeradgang til data](authentication.md).
1. [Forbered apps](apps.md).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. Forberede udskriftsressourcer (denne artikel).
1. Navne [på adresseenhed](address-device-names.md).
