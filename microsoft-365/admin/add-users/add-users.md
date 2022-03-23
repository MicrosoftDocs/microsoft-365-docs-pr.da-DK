---
title: Tilføj brugere, og tildel licenser
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- MET150
description: Hvert teammedlem skal have en brugerkonto, før de kan logge på og få adgang Microsoft 365 til virksomheder. Få mere at vide om, hvordan du tilføjer brugere og tildeler licenser.
ms.date: 07/01/2020
ms.openlocfilehash: 90ef6506d10c0f4c106dd18816ccd2f11803a079
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63588268"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Tilføje brugere og tildele licenser på samme tid

Alle i dit team skal have en brugerkonto, før de kan logge på og få adgang [Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/business). Den nemmeste måde at tilføje brugerkonti på er at tilføje dem én ad gangen i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Når du har gjort dette, har dine brugere Microsoft 365 licenser, logge på legitimationsoplysninger og Microsoft 365 postkasser.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global, licens- eller brugeradministrator for at tilføje brugere og tildele licenser. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>Se: Tilføj brugere i dashboardvisningen

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> De trin, der bruges i videoen, viser et andet udgangspunkt for tilføjelse af brugere, men de resterende trin er de samme som i følgende procedure.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Tilføje brugere én ad gangen i dashboardvisningen

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Skærmbillede: Dashboardvisning i Administration":::

::: moniker range="o365-worldwide"

1. Gå til Administration på <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Gå til **BrugereAktivér** >  brugere, og vælg **Tilføj en bruger**.
3. I **ruden Konfigurer de grundlæggende oplysninger** skal du udfylde de grundlæggende brugeroplysninger og derefter vælge **Næste**.
    - **Navn** Udfyld for- og efternavn, visningsnavn og brugernavn.
    - **Domæne** Vælg domænet for brugerens konto. Hvis brugerens brugernavn f.eks. er Jakob, og domænet er contoso.com, logger han eller hun på ved hjælp af jakob@contoso.com.
    - **Adgangskodeindstillinger** Vælg at bruge den autogenererede adgangskode eller at oprette din egen stærke adgangskode til brugeren.
    - Brugeren skal ændre adgangskoden efter 90 dage. Eller du kan vælge **Kræv, at denne bruger ændrer sin adgangskode, når de logger på første gang**.
    - Vælg, om du vil sende adgangskoden i en mail, når brugeren tilføjes.
4. I **ruden Tildel produktlicenser** skal du vælge placeringen og den relevante licens for brugeren. Hvis du ikke har nogen tilgængelige licenser, kan du stadig tilføje en bruger og købe flere licenser. **Udvid Apps**, og vælg eller fravælg apps for at begrænse de apps, som brugeren har en licens til. Vælg **Næste**.
5. I **ruden Valgfrie indstillinger** skal du **udvide Roller** for at gøre denne bruger til administrator. **Udvid profiloplysninger** for at tilføje yderligere oplysninger om brugeren.
6. Vælg **Næste**, gennemse din nye brugers indstillinger, foretag de ændringer, du ønsker, og vælg derefter **Afslut tilføjelse**, og derefter **Luk**.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Tilføj en bruger i den forenklede administratorvisning

Hvis du får vist denne side i Administration, er du i den forenklede **administratorvisning**. Følg trinnene nedenfor for at tilføje en bruger.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Skærmbillede: Forenklet administrationscentervisning":::

::: moniker range="o365-worldwide"

1. Gå til Administration på <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Vælg **Opret en konto til en anden person**.
3. På siden **Tilføj en brugerkonto** skal du udfylde det for- og efternavn, det viste navn og det brugernavn, de skal bruge til at logge på med.
4. Tilføj brugerens mailadresse i **tekstfeltet Op til 5** mailadresser.... Dette sikrer, at den nye bruger får de oplysninger, de skal bruge til at logge på Microsoft 365-tjenester.
5. Vælg **Tilføj bruger** **og Download logonoplysninger,** hvis du vil gemme disse oplysninger.

## <a name="add-multiple-users-at-the-same-time"></a>Tilføj flere brugere på samme tid

Du kan bruge en af følgende metoder til at tilføje flere brugere på samme tid:

- **Brug et regneark til at tilføje flere personer flere.** Se [Tilføj flere brugere på samme tid](../../enterprise/add-several-users-at-the-same-time.md).
- **Automatiser tilføjelse af konti og tildeling af licenser.** Se [Opret brugerkonti med Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Vælg denne metode, hvis du allerede er fortrolig med brugen Windows PowerShell cmdlet'er.
- **Bruger du ActiveDirectory?** [Konfigurer katalogsynkronisering for Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Brug værktøjet Azure AD Forbind til at kopiere Active Directory-brugerkonti (og andre Active Directory-objekter) i Microsoft 365. Synkroniseringen tilføjer kun brugerkontiene. Du skal tildele licenser til de synkroniserede brugere, før de kan bruge mail og Office apps.
- **Vil du overføre fra Exchange?** Se [Metoder til at overføre flere mailkonti for at Office 365](/Exchange/mailbox-migration/mailbox-migration). Når du overfører flere postkasser til Microsoft 365 ved hjælp af enten cutover, staged eller en hybrid Exchange-metode, tilføjer du automatisk brugere som en del af overførslen. Overførslen tilføjer kun brugerkontiene. Du skal tildele licenser til brugerne, før de kan bruge mail og andre Office apps. Hvis du ikke tildeler en licens til en bruger, deaktiveres brugerens postkasse efter 30 dage. Få mere at vide [om, hvordan du tildeler](../manage/assign-licenses-to-users.md) licenser til brugere Microsoft 365 Administration.

## <a name="next-steps"></a>Næste trin

Når du har tilføjet en bruger, får du en mail fra Microsoft. Mailen indeholder brugerens bruger-id og adgangskode, så vedkommende kan logge på Microsoft 365. Brug den normale proces til at kommunikere nye adgangskoder. Del [hurtig](../setup/employee-quick-setup.md) startvejledningen for medarbejdere med dine nye brugere for at konfigurere ting som f.eks. hvordan du downloader og installerer [Office-apps](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) på en pc eller Mac, og hvordan du konfigurerer [Office-apps](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f) og mail på en mobilenhed.

## <a name="related-content"></a>Relateret indhold

[Føj en ny medarbejder til Microsoft 365](add-new-employee.md) (artikel)\
[Føj flere brugere på samme tid til Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (artikel)\
[Gendan en bruger Microsoft 365](restore-user.md) (artikel)\
[Tildel licenser til brugere](../manage/assign-licenses-to-users.md) (artikel)\
[Slet en bruger fra din organisation](delete-a-user.md) (artikel)
