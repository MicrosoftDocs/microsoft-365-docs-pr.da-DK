---
title: Beskyt dine administratorkonti i Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: Få mere at vide om, hvordan du konfigurerer og beskytter dine administratorkonti i Microsoft 365 Business Premium.
ms.openlocfilehash: e20fa8f408668287065f6aa1e30490fd8e3c2fec
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489919"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Beskyt dine administratorkonti i Microsoft 365 Business Premium

Fordi administratorkonti har administratorrettigheder, er de værdifulde mål for hackere og cyberkriminelle. I denne artikel beskrives:

- Sådan konfigurerer du en ekstra administratorkonto til nødsituationer.
- Sådan beskytter du disse konti.

Når du tilmelder dig Microsoft 365 og angiver dine oplysninger, bliver du automatisk global administrator (også kaldet global administrator). En global administrator har den ultimative kontrol over brugerkonti og alle andre indstillinger i Microsoft Administration ([https://admin.microsoft.com](https://admin.microsoft.com)), men der er mange forskellige typer administratorkonti med varierende adgangsgrader. Se [om administratorroller](/office365/admin/add-users/about-admin-roles) for at få oplysninger om de forskellige adgangsniveauer for hver type administratorrolle.

## <a name="create-additional-admin-accounts"></a>Opret flere administratorkonti

Brug kun administratorkonti til administration. Administratorer skal have en separat brugerkonto til regelmæssig brug af Office-apps og kun bruge deres administrative konto, når det er nødvendigt for at administrere konti og enheder, og mens de arbejder med andre administratorfunktioner. Det er også en god idé at fjerne Microsoft 365-licensen fra administratorkontiene, så du ikke behøver at betale for dem.

Du skal konfigurere mindst én ekstra global administratorkonto for at give administratoren adgang til en anden medarbejder, der er tillid til. Du kan også oprette separate administratorkonti til brugeradministration (denne rolle kaldes **Administrator af brugeradministration**). Du kan få flere oplysninger under [Administratorroller](/office365/admin/add-users/about-admin-roles).

Sådan opretter du flere administratorkonti:

 1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 Administration</a>, og vælg derefter **Aktive** \> **brugere** i venstre navigationsrude.

    ![Vælg Brugere og derefter Aktive brugere i venstre navigationsrude.](../media/Activeusers.png)

 1. På siden **Aktive brugere** skal du vælge **Tilføj en bruger** øverst på siden. 

 1. I panelet **Tilføj en bruger** skal du angive grundlæggende oplysninger, f.eks. oplysninger om navn og brugernavn.

 1. Angiv og konfigurer oplysninger om **produktlicenser** .

 1. Under **Valgfrie indstillinger** skal du definere brugerens rolle, herunder tilføje Administration centeradgang, hvis det er relevant.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Definer nye brugerroller.":::

 1. Udfør og gennemse dine indstillinger, og vælg **Afslut tilføjelse** for at bekræfte detaljerne.

## <a name="create-an-emergency-admin-account"></a>Opret en nødadministratorkonto

Du skal også oprette en sikkerhedskopikonto, der ikke er konfigureret med multifaktorgodkendelse , så du ikke ved et uheld låser dig ud (f.eks. hvis du mister din telefon, som du bruger som en anden form for bekræftelse). Sørg for, at adgangskoden til denne konto er et udtryk eller mindst 16 tegn langt. Dette kaldes ofte en "break-glass-konto".

## <a name="create-a-user-account-for-yourself"></a>Opret en brugerkonto til dig selv

Brug din brugerkonto til at deltage i samarbejde med din organisation, herunder tjek af mail. Det betyder, at dine administratorlegitimationsoplysninger  *f.eks. svarer til Alice.Chavez <span></span>@Contoso.org*, og at din almindelige brugerkonto ligner *Alice <span></span>@Contoso.com*.

Sådan opretter du en ny brugerkonto:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 Administration</a>, og vælg derefter **Aktive** \> **brugere** i venstre navigationsrude.

1. På siden **Aktive brugere** skal du vælge **Tilføj en bruger** øverst på siden og angive navnet og andre oplysninger i panelet **Tilføj en bruger** .

1. I afsnittet **Produktlicenser** skal du markere afkrydsningsfeltet for **Microsoft 365 Business Premium (ingen administrativ adgang)**.

1. I afsnittet **Valgfrie indstillinger** skal du lade standard alternativknappen være valgt for **Bruger (ingen adgang til Administration).**

1. Udfør og gennemse dine indstillinger, og vælg **Afslut tilføjelse** for at bekræfte detaljerne.

## <a name="additional-recommendations"></a>Yderligere anbefalinger

- Før du bruger administratorkonti, skal du lukke alle ikke-relaterede browsersessioner og -apps, herunder personlige mailkonti. Du kan også bruge i private eller inkognito browservinduer.

- Når du har fuldført administratoropgaver, skal du sørge for at logge af browsersessionen.

## <a name="next-objective"></a>Næste mål

Udfør trinnene for at [aktivere sikkerhedsstandarder](m365bp-conditional-access.md).

