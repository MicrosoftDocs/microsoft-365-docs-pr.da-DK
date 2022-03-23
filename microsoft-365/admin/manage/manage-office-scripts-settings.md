---
title: Administrere Office scripts
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Lær at administrere Office scripts for brugere i organisationen.
ms.openlocfilehash: f03ee34e0ff41c3eb082beca79127cd609496564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591029"
---
# <a name="manage-office-scripts-settings"></a>Administrere Office scripts

[Office scripts](/office/dev/scripts) kan brugerne automatisere opgaver ved at optage, redigere og køre scripts i Excel på internettet. Office scripts fungerer sammen med Power Automate, og brugere kører scripts på projektmapper ved hjælp af forbindelsen Excel Online (Business). Microsoft 365 administratorer kan administrere Office scripts fra Microsoft 365 Administration.

## <a name="before-you-begin"></a>Før du begynder

- Du skal Office global administrator for at kunne administrere scripts. Du kan få mere at vide [under Om administratorroller](../add-users/about-admin-roles.md).

- Sørg for, at brugerne i organisationen har en gyldig licens til en kommerciel eller EDU-plan af Microsoft 365 eller Office 365, der omfatter adgang til Office-skrivebordsapps, f.eks. en af følgende planer:

- Microsoft 365 Business Standard
- Microsoft 365 Apps for business
- Microsoft 365 Apps for enterprise
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Administrere tilgængeligheden Office scripts og deling af scripts

1. I Microsoft 365 Administration skal du gå til **Indstillinger** \> **Org settings** \> **[Services](https://go.microsoft.com/fwlink/p/?linkid=2053743)**.

2. Vælg **Office scripts**.

3. Office scripts er slået til som standard, og alle i organisationen kan få adgang til og bruge funktionen og dele scripts. Hvis du vil deaktivere Office scripts for organisationen, skal du fjerne markeringen **i afkrydsningsfeltet Lad brugere automatisere deres Excel på internettet** efter behov.

4. Hvis du tidligere har deaktiveret Office Scripts for organisationen, og du vil slå det til igen, skal du vælge Lad brugerne automatisere deres opgaver i **Excel på internettet** og derefter angive, hvem der kan få adgang til og bruge funktionen:

    - Hvis du vil give alle brugere i organisationen adgang til og bruge Office scripts, skal **du lade** Alle (standard) være markeret.

    - Hvis du kun vil give medlemmer af en bestemt gruppe adgang til og bruge Office Scripts, skal du vælge Bestemt gruppe og derefter angive navnet eller mailaliasset på gruppen for at føje det til listen over tilladte. Du kan kun føje én gruppe til listen over tilladte, og det skal være en af følgende typer:
        - Microsoft 365 gruppe
        - Distributionsgruppe
        - Sikkerhedsgruppe
        - Mailaktiveret sikkerhedsgruppe

        Hvis du vil have mere at vide om de forskellige typer af grupper, skal du [se Sammenlign grupper](../create-groups/compare-groups.md).

5. Hvis du vil give brugere med adgang til Office Scripts mulighed for at dele deres scripts med andre i organisationen, skal du vælge Giv brugere med adgang til **Office-scripts** adgang til at dele deres scripts med andre i organisationen. Deling af scripts uden for en organisation er ikke tilladt.

    > [!NOTE]
    > Hvis du senere deaktiverer scriptdeling for organisationen, kan brugerne stadig køre tidligere delte scripts.

6. Angiv, hvilke brugere med adgang til Office scripts der kan dele deres scripts:

    - Hvis du vil give alle brugere med adgang Office scripts til at dele deres scripts, skal **du lade** Alle (standard) være markeret.

    - Hvis du kun vil tillade medlemmer af en bestemt gruppe med adgang til Office Scripts for at dele deres scripts, skal du vælge Bestemt gruppe og derefter angive gruppens navn eller mailalias for at føje det til listen over tilladte. Du kan kun føje én gruppe til listen over tilladte, og det skal være en af følgende typer:
        - Microsoft 365 gruppe
        - Distributionsgruppe
        - Sikkerhedsgruppe
        - Mailaktiveret sikkerhedsgruppe

        Hvis du vil have mere at vide om de forskellige typer af grupper, skal du [se Sammenlign grupper](../create-groups/compare-groups.md).

7. Hvis du vil tillade brugere at køre deres Office Scripts i Power Automate flows, skal du vælge Lad brugere med adgang til **Office Scripts køre deres scripts med Power Automate**. Dette giver brugerne mulighed for at tilføje flowtrin [med Excel Online (Business) Connectors](/connectors/excelonlinebusiness) **Kør-scriptindstilling**.

    - For at give alle brugere med adgang til Office scripts at bruge deres scripts i flow, skal **du lade** Alle (standard) være markeret.

    - Hvis du kun vil tillade medlemmer af en bestemt gruppe med adgang til Office Scripts at bruge deres scripts i flows, skal du vælge En bestemt gruppe og derefter angive gruppens navn eller mailalias for at føje det til listen over tilladte. Du kan kun føje én gruppe til listen over tilladte, og det skal være en af følgende typer:
        - Microsoft 365 gruppe
        - Distributionsgruppe
        - Sikkerhedsgruppe
        - Mailaktiveret sikkerhedsgruppe

        Hvis du vil have mere at vide om de forskellige typer af grupper, skal du [se Sammenlign grupper](../create-groups/compare-groups.md).

    - Du kan få mere at vide Office at bruge scripts Power Automate med Power Automate i [Kør Office med Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Vælg **Gem**.

    Det kan tage op til 48 timer, før ændringerne af indstillingerne for Office-scripts træder i kraft.

## <a name="next-steps"></a>Næste trin

Da Office Scripts fungerer sammen med Power Automate, anbefaler vi, at du gennemgår dine eksisterende politikker til forebyggelse af datatab (DLP) for at sikre, at din organisations data forbliver beskyttet, mens brugerne bruger Office scripts. Du kan få flere oplysninger under [Politikker om forebyggelse af datatab (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Relateret indhold

[Office scripts til teknisk dokumentation](/office/dev/scripts/) (linkside)\
[Introduktion til Office Scripts i Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (artikel)\
[Deling Office scripts Excel til internettet](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (artikel)\
[Optag, rediger og opret Office scripts i Excel på internettet](/office/dev/scripts/tutorials/excel-tutorial) (artikel)
