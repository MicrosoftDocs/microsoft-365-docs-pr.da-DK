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
ms.openlocfilehash: a4f6265fd47a449c4768e7aef82ad6fdc004011f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66631822"
---
# <a name="protect-your-administrator-accounts-in-microsoft-365-business-premium"></a>Beskyt dine administratorkonti i Microsoft 365 Business Premium

Fordi administratorkonti har administratorrettigheder, er de værdifulde mål for hackere og cyberkriminelle. I denne artikel beskrives:

- [Sådan opretter du en anden administratorkonto til nødsituationer](#create-other-admin-accounts).
- [Sådan opretter du en akutadministratorkonto](#create-an-emergency-admin-account).
- [Sådan opretter du en brugerkonto til dig selv](#create-a-user-account-for-yourself).
- [Sådan beskytter du administratorkonti](#protect-admin-accounts).
- [Yderligere anbefalinger](#additional-recommendations) og dit [næste mål](#next-objective).

Når du tilmelder dig Microsoft 365 og angiver dine oplysninger, bliver du automatisk global administrator (også kaldet global administrator). En global administrator har den ultimative kontrol over brugerkonti og alle andre indstillinger i Microsoft Administration ([https://admin.microsoft.com](https://admin.microsoft.com)), men der er mange forskellige typer administratorkonti med varierende adgangsgrader. Se [om administratorroller](/office365/admin/add-users/about-admin-roles) for at få oplysninger om de forskellige adgangsniveauer for hver type administratorrolle.

## <a name="create-other-admin-accounts"></a>Opret andre administratorkonti

Brug kun administratorkonti til Microsoft 365-administration. Administratorer skal have en separat brugerkonto til deres regelmæssige brug af Office-apps og kun bruge deres administrative konto, når det er nødvendigt for at administrere konti og enheder, og mens de arbejder med andre administratorfunktioner. Det er også en god idé at fjerne Microsoft 365-licensen fra dine administratorkonti, så du ikke behøver at betale for ekstra licenser.

Du skal konfigurere mindst én anden global administratorkonto for at give administratoren adgang til en anden medarbejder, der er tillid til. Du kan også oprette separate administratorkonti til brugeradministration (denne rolle kaldes **Administrator af brugeradministration**). Du kan få flere oplysninger under [Administratorroller](/office365/admin/add-users/about-admin-roles).

> [!IMPORTANT]
> Selvom vi anbefaler, at du konfigurerer et sæt administratorkonti, skal du begrænse antallet af globale administratorer for din organisation. Derudover anbefaler vi, at du overholder begrebet færrest mulige rettigheder, hvilket betyder, at du kun giver adgang til de data og handlinger, der er nødvendige for at udføre deres job. [Få mere at vide om princippet om færrest mulige rettigheder](/azure/active-directory/develop/secure-least-privileged-access). 

Sådan opretter du flere administratorkonti:

 1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 Administration</a>, og vælg derefter **Aktive** \> **brugere** i venstre navigationsrude.

    ![Vælg Brugere og derefter Aktive brugere i venstre navigationsrude.](../media/Activeusers.png)

 2. På siden **Aktive brugere** skal du vælge **Tilføj en bruger** øverst på siden. 

 3. I panelet **Tilføj en bruger** skal du angive grundlæggende oplysninger, f.eks. oplysninger om navn og brugernavn.

 4. Angiv og konfigurer oplysninger om **produktlicenser** .

 5. Under **Valgfrie indstillinger** skal du definere brugerens rolle, herunder tilføje Administration centeradgang, hvis det er relevant.

    :::image type="content" source="media/m365bp-global-admin.png" alt-text="Definer nye brugerroller.":::

 6. Udfør og gennemse dine indstillinger, og vælg **Afslut tilføjelse** for at bekræfte detaljerne.

## <a name="create-an-emergency-admin-account"></a>Opret en nødadministratorkonto

Du skal også oprette en sikkerhedskopikonto, der ikke er konfigureret med multifaktorgodkendelse , så du ikke ved et uheld låser dig ud (hvis du f.eks. mister din telefon, som du bruger som en anden form for bekræftelse). Sørg for, at adgangskoden til denne konto er et udtryk eller mindst 16 tegn langt. Denne akutadministratorkonto kaldes ofte en "break-glass-konto".

## <a name="create-a-user-account-for-yourself"></a>Opret en brugerkonto til dig selv

Hvis du er administrator, skal du bruge en brugerkonto til almindelige arbejdsopgaver, f.eks. kontrol af mail. Navngiv dine konti, så du ved, hvad der er hvad. Dine administratorlegitimationsoplysninger kan  *f.eks. svare til Alice.Chavez <span></span>@Contoso.org*, og din almindelige brugerkonto kan ligne *Alice <span></span>@Contoso.com*.

Sådan opretter du en ny brugerkonto:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">Microsoft 365 Administration</a>, og vælg derefter **Aktive** \> **brugere** i venstre navigationsrude.

2. På siden **Aktive brugere** skal du vælge **Tilføj en bruger** øverst på siden og angive navnet og andre oplysninger i panelet **Tilføj en bruger** .

3. I afsnittet **Produktlicenser** skal du markere afkrydsningsfeltet for **Microsoft 365 Business Premium (ingen administrativ adgang)**.

4. I afsnittet **Valgfrie indstillinger** skal du lade standard alternativknappen være valgt for **Bruger (ingen adgang til Administration).**

5. Udfør og gennemse dine indstillinger, og vælg **Afslut tilføjelse** for at bekræfte detaljerne.

## <a name="protect-admin-accounts"></a>Beskyt administratorkonti

Hvis du vil beskytte alle dine administratorkonti, skal du sørge for at følge disse anbefalinger:

- Kræv, at alle administratorkonti bruger godkendelse uden adgangskode (f.eks. Windows Hello eller en godkenderapp) eller MFA. Du kan få mere at vide om, hvorfor godkendelse uden adgangskode er vigtig, i [hvidbogen Microsoft Security: Beskyttelse uden adgangskode](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RE2KEup).

- Undgå at bruge brugerdefinerede tilladelser til administratorer. I stedet for at tildele tilladelser til bestemte brugere skal du tildele tilladelser via roller i Azure Active Directory (Azure AD). Og giv kun adgang til de data og handlinger, der er nødvendige for at udføre den pågældende opgave. [Få mere at vide om de mindst privilegerede roller i Azure AD](/azure/active-directory/roles/delegate-by-task).

- Brug indbyggede roller til at tildele tilladelser, hvor det er muligt. Rollebaseret adgangskontrol i Azure (RBAC) har flere indbyggede roller, som du kan bruge. [Få mere at vide om Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).

## <a name="additional-recommendations"></a>Yderligere anbefalinger

- Før du bruger administratorkonti, skal du lukke alle ikke-relaterede browsersessioner og -apps, herunder personlige mailkonti. Du kan også bruge i private eller inkognito browservinduer.

- Når du har fuldført administratoropgaver, skal du sørge for at logge af browsersessionen.

## <a name="next-objective"></a>Næste mål

Udfør trinnene for at [aktivere sikkerhedsstandarder](m365bp-conditional-access.md).

