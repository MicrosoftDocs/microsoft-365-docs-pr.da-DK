---
title: Tilføj brugere, og tildel licenser i Microsoft 365
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
description: Få mere at vide om, hvordan du giver hvert teammedlem en brugerkonto, så de kan have Microsoft 365 licenser, logonlegitimationsoplysninger og Microsoft 365 postkasser.
ms.date: 07/01/2020
ms.openlocfilehash: 8ebc4b99840f9987d115539d0039efa1950499d3
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466806"
---
# <a name="add-users-and-assign-licenses-at-the-same-time"></a>Tilføj brugere, og tildel licenser på samme tid

Personerne i dit team skal hver især have en brugerkonto, før de kan logge på og få adgang [til Microsoft 365 til virksomheder](https://www.microsoft.com/microsoft-365/business). Den nemmeste måde at tilføje brugerkonti på er ved at tilføje dem én ad gangen i <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Når du har gjort dette trin, har dine brugere Microsoft 365 licenser, logger på legitimationsoplysninger og Microsoft 365 postkasser.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global, licens eller brugeradministrator for at tilføje brugere og tildele licenser. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="watch-add-users-in-the-dashboard-view"></a>Se: Tilføj brugere i dashboardvisningen

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfN?autoplay=false]

> [!NOTE]
> De trin, der bruges i videoen, viser et andet udgangspunkt for tilføjelse af brugere, men de resterende trin er de samme som følgende procedure.

## <a name="add-users-one-at-a-time-in-the-dashboard-view"></a>Tilføj brugere én ad gangen i dashboardvisningen

:::image type="content" source="../../media/classic-admin-center.png" alt-text="Skærmbillede: Dashboardvisning i Administration":::

::: moniker range="o365-worldwide"

1. Gå til Administration på <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Gå til **BrugereAktive** >  brugere, og vælg **Tilføj en bruger**.
3. I ruden **Konfigurer de grundlæggende** oplysninger skal du udfylde de grundlæggende brugeroplysninger og derefter vælge **Næste**.
    - **Navn** Udfyld for- og efternavn, vist navn og brugernavn.
    - **Domæne** Vælg domænet for brugerens konto. Hvis brugerens brugernavn f.eks. er Jakob, og domænet er contoso.com, logger vedkommende på ved hjælp af jakob@contoso.com.
    - **Indstillinger for adgangskode** Vælg at bruge den automatisk genererede adgangskode eller at oprette din egen stærke adgangskode til brugeren.
    - Brugeren skal ændre sin adgangskode efter 90 dage. Eller du kan vælge **Kræv, at denne bruger ændrer sin adgangskode, første gang vedkommende logger på**.
    - Vælg, om du vil sende adgangskoden i en mail, når brugeren tilføjes.
4. I ruden **Tildel produktlicenser** skal du vælge placeringen og den relevante licens for brugeren. Hvis du ikke har nogen tilgængelige licenser, kan du stadig tilføje en bruger og købe yderligere licenser. Udvid **Apps** , og vælg eller fjern markeringen af apps for at begrænse de apps, som brugeren har en licens til. Vælg **Næste**.
5. I ruden **Valgfrie indstillinger** skal du udvide **Roller** for at gøre denne bruger til administrator. Udvid **Profiloplysninger** for at tilføje flere oplysninger om brugeren.
6. Vælg **Næste**, gennemse den nye brugers indstillinger, foretag eventuelle ændringer, og vælg derefter **Afslut tilføjelse** og derefter **Luk**.

## <a name="add-a-user-in-the-admin-simplified-view"></a>Tilføj en bruger i den forenklede administratorvisning

Hvis du får vist denne side i Administration, er du i den **forenklede administratorvisning**. Følg nedenstående trin for at tilføje en bruger.

:::image type="content" source="../../media/vsb-add-user-view.png" alt-text="Skærmbillede: Forenklet visning af Administration":::

::: moniker range="o365-worldwide"

1. Gå til Administration på <https://admin.microsoft.com>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Vælg **Opret en konto til en anden person**.
3. På siden **Tilføj en brugerkonto** skal du udfylde det for- og efternavn, det viste navn og brugernavn, de skal bruge til at logge på.
4. Tilføj brugerens mailadresse i tekstfeltet **Op til fem mailadresser...** Dette sikrer, at den nye bruger får de oplysninger, vedkommende skal bruge for at logge på Microsoft 365-tjenester.
5. Vælg **Tilføj bruger** og **Hent logonoplysninger** , hvis du vil gemme disse oplysninger.

## <a name="add-multiple-users-at-the-same-time"></a>Tilføj flere brugere på samme tid

Du kan bruge en af følgende metoder til at tilføje flere brugere på samme tid:

- **Brug et regneark til at tilføje flere personer samlet.** Se [Tilføj flere brugere på samme tid](../../enterprise/add-several-users-at-the-same-time.md).
- **Automatiser tilføjelse af konti og tildeling af licenser.** Se [Opret brugerkonti med Microsoft 365 PowerShell](../../enterprise/create-user-accounts-with-microsoft-365-powershell.md). Vælg denne metode, hvis du allerede har kendskab til Windows PowerShell cmdlet'er.
- **Bruger du ActiveDirectory?** [Konfigurer katalogsynkronisering for Microsoft 365](../../enterprise/set-up-directory-synchronization.md). Brug værktøjet Azure AD Forbind til at replikere Active Directory-brugerkonti (og andre Active Directory-objekter) i Microsoft 365. Synkroniseringen tilføjer kun brugerkontiene. Du skal tildele licenser til de synkroniserede brugere, før de kan bruge mail og andre Office apps.
- **Migrerer du fra Exchange?** Se [Måder at overføre flere mailkonti til Office 365](/Exchange/mailbox-migration/mailbox-migration) på. Når du overfører flere postkasser til Microsoft 365 ved hjælp af enten cutover, staged eller en hybrid Exchange metode, tilføjer du automatisk brugere som en del af migreringen. Overførslen tilføjer kun brugerkontiene. Du skal tildele licenser til brugerne, før de kan bruge mail og andre Office apps. Hvis du ikke tildeler en licens til en bruger, deaktiveres brugerens postkasse efter en respitperiode på 30 dage. Få mere at vide om, hvordan [du tildeler licenser til brugere](../manage/assign-licenses-to-users.md) i Microsoft 365 Administration.

## <a name="next-steps"></a>Næste trin

Når du har tilføjet en bruger, får du en meddelelse via mail fra Microsoft. Mailen indeholder personens bruger-id og adgangskode, så vedkommende kan logge på Microsoft 365. Brug din normale proces til at kommunikere nye adgangskoder. Del [vejledningen til hurtig start af medarbejdere](../setup/employee-quick-setup.md) med dine nye brugere for at konfigurere ting, f.eks. hvordan [du downloader og installerer Office apps på en pc eller Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658), og hvordan [du konfigurerer Office apps og mail på en mobilenhed](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f).

## <a name="related-content"></a>Relateret indhold

[Føj en ny medarbejder til Microsoft 365](add-new-employee.md) (artikel)\
[Føj flere brugere på samme tid til Microsoft 365](../../enterprise/add-several-users-at-the-same-time.md) (artikel)\
[Gendan en bruger i Microsoft 365](restore-user.md) (artikel)\
[Tildel licenser til brugere](../manage/assign-licenses-to-users.md) (artikel)\
[Slet en bruger fra din organisation](delete-a-user.md) (artikel)
