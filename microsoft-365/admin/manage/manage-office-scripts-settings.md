---
title: Administrer indstillinger for Office-scripts
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
description: Få mere at vide om, hvordan du administrerer indstillinger for Office scripts for brugerne i din organisation.
ms.openlocfilehash: fdc9c947ee7f12e284fd215f05f8b5c3dcb127eb
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941143"
---
# <a name="manage-office-scripts-settings"></a>Administrer indstillinger for Office-scripts

[Office scripts](/office/dev/scripts) gør det muligt for brugerne at automatisere opgaver ved at optage, redigere og køre scripts i Excel på internettet. Office scripts fungerer sammen med Power Automate, og brugerne kører scripts på projektmapper ved hjælp af connectoren Excel Online (Business). Microsoft 365 administratorer kan administrere indstillingerne for Office scripts fra Microsoft 365 Administration.

## <a name="before-you-begin"></a>Før du begynder

- Hvis du vil administrere indstillingerne for Office scripts, skal du være global administrator. Du kan få flere oplysninger under [Om administratorroller](../add-users/about-admin-roles.md).

- Sørg for, at brugerne i organisationen har en gyldig licens til en Microsoft 365- eller Office 365 kommerciel plan eller EDU-plan, der omfatter adgang til Office desktopapps, f.eks. en af følgende planer:

- Microsoft 365 Business Standard
- Microsoft 365 Apps for business
- Microsoft 365 Apps for enterprise
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Administrer tilgængeligheden af Office scripts og deling af scripts

1. I Microsoft 365 Administration skal du gå til fanen **Indstillinger** \> **Organisationsindstillinger** \> **[Tjenester](https://go.microsoft.com/fwlink/p/?linkid=2053743)**.

2. Vælg **Office scripts**.

3. Office Scripts er som standard slået til, og alle i organisationen kan få adgang til og bruge funktionen og dele scripts. Hvis du vil deaktivere Office scripts for din organisation, skal du fjerne markeringen i afkrydsningsfeltet **Lad brugerne automatisere deres opgaver i Excel på internettet**.

4. Hvis du tidligere har deaktiveret Office scripts for din organisation, og du vil slå den til igen, skal du vælge **Lad brugerne automatisere deres opgaver i Excel på internettet** og derefter angive, hvem der har adgang til og kan bruge funktionen:

    - Hvis du vil give alle brugere i din organisation adgang til og bruge Office Scripts, skal du lade **Alle** (standarden) være markeret.

    - Hvis du kun vil give medlemmer af en bestemt gruppe adgang til og bruge Office scripts, skal du vælge **Specifik gruppe** og derefter angive navnet eller mailaliasset for gruppen for at føje den til listen over tilladte. Du må kun føje én gruppe til listen over tilladte, og den skal være en af følgende typer:
        - Microsoft 365 gruppe
        - Distributionsgruppe
        - Sikkerhedsgruppe
        - Mailaktiveret sikkerhedsgruppe

        Du kan få mere at vide om de forskellige typer af grupper under [Sammenlign grupper](../create-groups/compare-groups.md).

5. Hvis du vil give brugere med adgang til Office scripts til at dele deres scripts med andre i din organisation, skal du vælge **Lad brugere med adgang til Office scripts dele deres scripts med andre i organisationen**. Deling af scripts uden for en organisation er ikke tilladt.

    > [!NOTE]
    > Hvis du senere slår scriptdeling fra for din organisation, kan brugerne stadig køre tidligere delte scripts.

6. Angiv, hvilke brugere med adgang til Office scripts der kan dele deres scripts:

    - Hvis du vil give alle brugere med adgang til Office scripts tilladelse til at dele deres scripts, skal du lade **Alle** (standarden) være markeret.

    - Hvis du kun vil give medlemmer af en bestemt gruppe adgang til Office scripts til at dele deres scripts, skal du vælge **Specifik gruppe** og derefter angive navnet eller mailaliasset for gruppen for at føje det til listen over tilladte. Du må kun føje én gruppe til listen over tilladte, og den skal være en af følgende typer:
        - Microsoft 365 gruppe
        - Distributionsgruppe
        - Sikkerhedsgruppe
        - Mailaktiveret sikkerhedsgruppe

        Du kan få mere at vide om de forskellige typer af grupper under [Sammenlign grupper](../create-groups/compare-groups.md).

7. Hvis du vil tillade brugere at køre deres Office scripts i Power Automate flow, skal du vælge **Lad brugere med adgang til Office Scripts køre deres scripts med Power Automate**. Dette giver brugerne mulighed for at tilføje flowtrin med scriptet **Kør** [Excel Online (Business) Connector](/connectors/excelonlinebusiness).

    - Hvis du vil give alle brugere med adgang til Office scripts mulighed for at bruge deres scripts i flow, skal du lade **Alle** (standarden) være markeret.

    - Hvis du kun vil give medlemmer af en bestemt gruppe adgang til Office scripts til at bruge deres scripts i flow, skal du vælge **Specifik gruppe** og derefter angive navnet eller mailaliasset for gruppen for at føje den til listen over tilladte. Du må kun føje én gruppe til listen over tilladte, og den skal være en af følgende typer:
        - Microsoft 365 gruppe
        - Distributionsgruppe
        - Sikkerhedsgruppe
        - Mailaktiveret sikkerhedsgruppe

        Du kan få mere at vide om de forskellige typer af grupper under [Sammenlign grupper](../create-groups/compare-groups.md).

    - Hvis du vil vide mere om brug af Office scripts med Power Automate, skal du se [Kør Office scripts med Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. Vælg **Gem**.

    Det kan tage op til 48 timer, før ændringerne af indstillingerne for Office-scripts træder i kraft.

## <a name="next-steps"></a>Næste trin

Da Office scripts fungerer sammen med Power Automate, anbefaler vi, at du gennemser dine eksisterende politikker til forebyggelse af datatab i Microsoft Purview for at sikre, at organisationens data forbliver beskyttede, mens brugerne bruger Office scripts. Du kan få flere oplysninger under [Politikker om forebyggelse af datatab (DLP)](/power-automate/prevent-data-loss).

## <a name="related-content"></a>Relateret indhold

[Office Scripts teknisk dokumentation](/office/dev/scripts/) (linkside)\
[Introduktion til Office scripts i Excel](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) (artikel)\
[Deling Office scripts i Excel til internettet](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (artikel)\
[Optag, rediger og opret Office scripts i Excel på internettet](/office/dev/scripts/tutorials/excel-tutorial) (artikel)
