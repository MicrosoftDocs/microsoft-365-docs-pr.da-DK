---
title: Beskyt dine administratorkonti i Microsoft 365 Business Premium
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
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
description: Få mere at vide om, hvordan du konfigurerer og beskytter dine administratorkonti Microsoft 365 Business Premium.
ms.openlocfilehash: ad8ef2dfe1cbffe6e22e320a47d0907d4f1182e7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704765"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Beskyt dine administratorkonti i Microsoft 365 Business Premium

Da administratorkonti har administratorrettigheder, er de værdifulde mål for hackere og cyberkriminelle. I denne artikel beskrives følgende:

- Sådan oprettes en ekstra administratorkonto til nødstilfælde.
- Sådan beskyttes disse konti.

Når du tilmelder dig Microsoft 365 og angiver dine oplysninger, bliver du automatisk global administrator. En global administrator har ultimativ kontrol over brugerkonti og alle de andre indstillinger i Microsoft Administration, men der er mange forskellige typer administratorkonti med forskellige adgangsgrader. Se [om administratorroller](/office365/admin/add-users/about-admin-roles) for at få oplysninger om de forskellige adgangsniveauer for hver type administratorrolle.

## <a name="create-additional-admin-accounts"></a>Opret flere administratorkonti

Brug kun administratorkonti til administration. Administratorer skal have en separat brugerkonto til almindelig brug af Office-apps og kun bruge deres administrative konto, når det er nødvendigt for at administrere konti og enheder, og mens de arbejder med andre administratorfunktioner. Det er også en god ide at fjerne licensen Microsoft 365 administratorkontiene, så du ikke behøver at betale for dem.

Du skal konfigurere mindst én ekstra global administratorkonto for at give administratoradgang til en anden medarbejder, der er tillid til. Du kan også oprette separate administratorkonti til brugerstyring (denne rolle kaldes **Brugeradministrator**). Du kan få mere at vide [under Om administratorroller](/office365/admin/add-users/about-admin-roles).

Sådan opretter du flere administratorkonti:

 1. Gå til Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">, og</a> vælg derefter **Aktive brugere** \> **i** venstre navigationslinje.

    ![Vælg Brugere og derefter Aktive brugere i venstre navigationslinje.](../media/Activeusers.png)

 2. På siden **Aktive brugere** **skal du vælge** Tilføj en bruger øverst på siden, og i **panelet Ny** bruger skal du angive navn og andre oplysninger.
 3. Udvid **sektionen Roller** , og vælg **Global administrator for** at give denne bruger global administratoradgang. Du kan også vælge **Tilpasset administrator og** vælge en af de roller, der vises.

    Angiv en alternativ mail i **tekstfeltet Alternativ** mailadresse. Du kan bruge denne adresse til at gendanne dine adgangskodeoplysninger, hvis du bliver låst ude. For globale administratorer sendes der også en faktureringsopgørelse til denne adresse.

    ![Vælg administratorrollen.](../media/adminroles.png)

 4. I sektionen **Produktlicenser** skal du flytte vælgeren for **Microsoft 365 Business** **til Fra** og **Opret bruger uden produktlicens** til **Til**.

    ![Vælg produktlicensen.](../media/productlicense.png)

## <a name="create-an-emergency-admin-account"></a>Oprette en administratorkonto til nødstilfælde

Du bør også oprette en sikkerhedskopikonto, der ikke er konfigureret med multifaktorgodkendelse (MFA), så du ikke ved et uheld låser dig selv ude (f.eks. hvis du mister din telefon, som du bruger som en anden form for godkendelse). Sørg for, at adgangskoden til denne konto er en sætning eller mindst 16 tegn lang. Dette kaldes ofte en "pauseglaskonto".

## <a name="create-a-user-account-for-yourself"></a>Opret en brugerkonto til dig selv

Brug din brugerkonto til at deltage i samarbejde med din organisation, herunder til at tjekke mails. Det betyder, at dine administratorlegitimationsoplysninger muligvis svarer til *Att.Chavez <span></span>@Contoso.org*, og at din almindelige brugerkonto muligvis svarer til *1999-Contoso.com <span></span>*.

Sådan opretter du en ny brugerkonto:

1. Gå til Administration <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">, og</a> vælg derefter **Aktive brugere** \> **i** venstre navigationslinje.
2. På siden **Aktive brugere** **skal du vælge** Tilføj en bruger øverst på siden, og i **panelet Ny** bruger skal du angive navn og andre oplysninger.
3. Udvid **sektionen** Roller, og vælg **Bruger (ingen administrativ adgang)**.
4. I sektionen **Produktlicenser** skal du flytte vælgeren for **Microsoft 365 Business** til **Til**.

## <a name="turn-on-security-defaults"></a>Aktivere sikkerhedsstandardindstillinger

Sikkerhedsstandardindstillingerne hjælper med at beskytte din organisation mod identitetsrelaterede angreb ved at give forudkonfigurerede sikkerhedsindstillinger, som Microsoft administrerer på vegne af din organisation. Disse indstillinger omfatter aktivering af Multi-Factor Authentication (MFA) for alle administratorer og brugerkonti. Du kan finde flere oplysninger om sikkerhedsstandardindstillinger, og du kan få mere at vide om, hvordan du aktiverer dem, [under Aktivere sikkerhedsstandardindstillinger](m365bp-conditional-access.md).

## <a name="additional-recommendations"></a>Yderligere anbefalinger

- Før du bruger administratorkonti, skal du lukke alle browsersessioner og apps, der ikke er relateret til hinanden, herunder personlige mailkonti. Du kan også bruge i private browservinduer eller incognitovinduer.
- Når du har fuldført administratoropgaverne, skal du sørge for at logge af browsersessionen.
