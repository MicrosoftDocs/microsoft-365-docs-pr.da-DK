---
title: Opgrader Office 2010 til Microsoft 365 – Microsoft 365 administrator
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.custom:
- fwlink 824861; CampaignID
- O365_Comm_SR_UpgradeOffice
- seo-marvel-may2020
- fwlink 824861; CampaignID O365_Comm_SR_UpgradeOffice
- AdminSurgePortfolio
ms.assetid: f6b00895-b5fd-4af6-a656-b7788ea20cbb
description: Få mere at vide om, hvordan Microsoft Office til den nyeste Office klient for brugere i organisationen.
ms.topic: article
ms.openlocfilehash: 7994fb10d00484f2c211f4443d2030fa71003d5f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589376"
---
# <a name="upgrade-your-microsoft-365-for-business-users-to-the-latest-office-client"></a>Opgrader Microsoft 365 til virksomhedsbrugere til den nyeste Office klient

## <a name="office-2010-reaches-end-of-support"></a>Office 2010 når ophør af support

Office 2010 havde slutdato for supporten d. 13. oktober 2020. Microsoft vil ikke længere levere følgende:

- Teknisk support til problemer

- Fejlrettelser til problemer, der opdages

- Sikkerhedsopdateringer til sårbarheder, der opdages

Se [oversigten Office slutdato for support for 2010](/deployoffice/endofsupport/office-2010-end-support-roadmap) for at få flere oplysninger.

 **Er dette det rigtige emne for dig?**
  
 Hvis du er den administrator, der er ansvarlig for Microsoft 365 for Business-abonnementet i din organisation, er du det rigtige sted. Administratorer er typisk ansvarlige for opgaver som administration af brugere, nulstilling af adgangskoder, administration Office installationer og tilføjelse eller fjernelse af licenser.

 Hvis du ikke er administrator, og du har et [Microsoft 365 Family-produkt](https://support.microsoft.com/office/28cbc8cf-1332-4f04-9123-9b660abb629e#BKMK_OfficePlans), skal du se Hvordan opgraderer jeg [Office](https://support.microsoft.com/office/ee68f6cf-422f-464a-82ec-385f65391350) for at få oplysninger om opgradering af din ældre, private brugsversion af Office.

## <a name="get-ready-to-upgrade-to-microsoft-365"></a>Bliv klar til at opgradere til Microsoft 365

Som administrator styrer du, hvilken version af Office personer i organisationen kan installere. Vi anbefaler stærkt, at du hjælper brugerne i organisationen med at køre ældre versioner af Office, f.eks. Office 2010, Office 2013 eller Office 2016, med at opgradere til den nyeste version for at udnytte forbedringerne inden for sikkerhed og produktivitet.

## <a name="upgrade-steps"></a>Opgraderingstrin

Nedenstående trin fører dig gennem processen med at opgradere dine brugere til den nyeste Office desktopklient. Vi anbefaler, at du læser disse trin, før du påbegynder opgraderingsprocessen.
  
## <a name="step-1---check-system-requirements"></a>Trin 1– Kontrollér systemkrav

[Kontrollér systemkravene for din](https://www.microsoft.com/microsoft-365/microsoft-365-and-office-resources) Office for at sikre, at dine enheder er kompatible med den nyeste version af Office. Nyere versioner af Office kan f.eks. ikke installeres på computere, der kører Windows XP eller Windows Vista.
  
> [!TIP]
> Hvis du har brugere i organisationen, der kører ældre versioner af Windows på deres pc eller bærbare computere, anbefaler vi, at du opgraderer til Windows 10. Windows support er slut på 7. Læs [Support til Windows 7 slutter i januar 2020](https://www.microsoft.com/microsoft-365/windows/end-of-windows-7-support?rtc=1) for at få flere oplysninger.

Se systemkravene [Windows 10 se,](https://www.microsoft.com/windows/windows-10-specifications) om du kan opgradere deres operativsystemer.

### <a name="check-application-compatibility"></a>Kontrollér programkompatibilitet

For at sikre en vellykket opgradering anbefaler vi, at du identificerer dine Office-programmer – herunder VBA-scripts, makroer, tilføjelsesprogrammer fra tredjeparter og komplekse dokumenter og regneark – og vurderer deres kompatibilitet med den nyeste version af Office.
  
Hvis du f.eks. bruger tilføjelser fra en tredjepart med din aktuelle Office-installation, skal du kontakte fremstillet for at sikre dig, at de er kompatible med den nyeste version af Office.
  
## <a name="step-2---check-your-existing-subscription-plan"></a>Trin 2: Kontrollér din eksisterende abonnementsplan

Nogle Microsoft 365 omfatter ikke de komplette desktopversioner af Office, og trinnene til at opgradere er anderledes, hvis din plan ikke omfatter Office.
  
Er du ikke sikker på, hvilket abonnement du har? Se [Hvilket Microsoft 365 til virksomheder har jeg?](../admin-overview/what-subscription-do-i-have.md)
  
Hvis din eksisterende plan Office, skal du gå videre [til Trin 3 - fjern Office](#step-3---uninstall-office).
  
Hvis din eksisterende plan ikke Office, skal du vælge mellem indstillingerne nedenfor:
  
### <a name="upgrade-options-for-plans-that-dont-include-office"></a>Opgraderingsmuligheder for planer, der ikke omfatter Office

 **Mulighed 1: Skift Office-abonnementer**

Skift til et abonnement, der Office. Se [Skift til en anden Microsoft 365 for business-plan](../../commerce/subscriptions/switch-to-a-different-plan.md).

**Mulighed 2: Køb individuelle engangskøb af Office, eller Office gennem en volumenlicens**

 - Køb et individuelt engangskøb af Office. Se [Office Home &amp; Business](https://www.microsoft.com/microsoft-365/buy/compare-all-microsoft-365-products-b) eller [Office Professional](https://www.microsoft.com/microsoft-365/p/office-professional-2019/CFQ7TTC0K7C5/)

     ELLER

 - Køb flere kopier af Office gennem en volumenlicens. Se Sammenlign [de pakker, der er tilgængelige via volumenlicens](https://products.office.com/business/microsoft-office-volume-licensing-suites-comparison).

## <a name="step-3---uninstall-office"></a>Trin 3: Fjern Office

Før du installerer den nyeste version af Office, anbefaler vi, at du fjerner alle ældre versioner af Office. Men hvis du skifter mening om opgradering af Office, skal du være opmærksom på følgende tilfælde, hvor du ikke kan geninstallere Office efter at have fjernet den.
  
Hvis du har tilføjelsesprogrammet fra tredjepart, anbefaler vi, at du kontakter producenten for at se, om der er en opdatering, der fungerer med den nyeste version af Office.

> [!TIP]
> Hvis du løber ind i problemer, mens du fjerner Office, kan du bruge Microsoft Support- og genoprettelsesassistent-værktøjet til at hjælpe dig med at fjerne Office: Download og kør [Microsoft Support- og genoprettelsesassistent](https://go.microsoft.com/fwlink/?LinkID=2155008).

### <a name="select-the-version-of-office-you-want-to-uninstall"></a>Vælg den version af Office du vil fjerne

- [Fra en pc](https://support.microsoft.com/office/9dd49b83-264a-477a-8fcc-2fdf5dbf61d8)

- [Fra en Mac](https://support.microsoft.com/office/eefa1199-5b58-43af-8a3d-b73dc1a8cae3)
  
### <a name="known-issues-trying-to-reinstall-older-versions-of-office-after-an-uninstall"></a>Kendte problemer ved forsøg på at geninstallere ældre versioner Office efter fjernelse

 **Office en volumenlicens** Hvis du ikke længere har adgang til kildefilerne til disse volumenlicensversioner af Office, kan du ikke geninstallere den.

 **Office forudinstalleret** på computeren Hvis du ikke længere har en disk eller produktnøgle (hvis Office fulgte med en), kan du ikke geninstallere den.

 **Ikke-understøttede abonnementer** Hvis din kopi af Office blev hentet via udgåede abonnementer, f.eks. Office 365 Small Business Premium eller Office 365 Mid-size Business, kan du ikke installere en ældre version af Office, medmindre du har den produktnøgle, der fulgte med dit abonnement.

Hvis du hellere vil installere din ældre version af Office side om side med den nyeste version, kan du se en liste over versioner, hvor dette understøttes i Installér og brug forskellige versioner af [Office](https://support.microsoft.com/office/6ebb44ce-18a3-43f9-a187-b78c513788bf) på den samme pc. En side om side-installation kan være det rigtige valg for dig, hvis du f.eks. har installeret tilføjelsesprogrammet fra en tredjepart, du bruger til din ældre version af Office, og du endnu ikke er sikker på, at de er kompatible med den nyeste version.

## <a name="step-4---assign-office-licenses-to-users"></a>Trin 4: Tildel Office licenser til brugere

Hvis du ikke allerede har gjort det, skal du tildele licenser til alle brugere i organisationen, der skal installere Office, se Tildel licenser til brugere [i Microsoft 365 til virksomheder](../manage/assign-licenses-to-users.md).
  
## <a name="step-5---install-office"></a>Trin 5: Office

Når du har bekræftet, at de brugere, du vil opgradere, alle har licenser, er det sidste trin at få dem til at installere Office, se [Download og installér](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) eller geninstaller Office på din pc eller Mac.
  
> [!TIP]
> Hvis du ikke ønsker, at brugerne selv installerer Office, kan du se Administrer indstillinger [for download af software i Office 365](/DeployOffice/manage-software-download-settings-office-365). Du kan bruge Office-udrulningsværktøjet til at downloade Office-softwaren til dit lokale netværk og derefter installere Office ved hjælp af den softwareinstallationsmetode, du normalt bruger.[](/DeployOffice/overview-office-deployment-tool)