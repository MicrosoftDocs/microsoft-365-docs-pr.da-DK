---
title: Anbefalede Teams politikker – Microsoft 365 til | Microsoft Docs
description: Beskriver politikkerne for Microsoft-anbefalinger om, hvordan du sikrer Teams og adgang til filer.
author: MicrosoftHeidi
manager: serdars
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.author: heidip
ms.date: 09/30/2020
ms.reviewer: anmorgan
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: ec4aa28c25982ea81662ff26fa19f615d13cd314
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465393"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Politikanbefalinger til sikring Teams chats, grupper og filer

I denne artikel beskrives det, hvordan du implementerer de anbefalede politikker for Nul tillid identitet og enhedsadgang for at beskytte Microsoft Teams chatsamtaler, grupper og indhold som f.eks. filer og kalendere. Denne vejledning bygger på de [almindelige politikker for identitet og](identity-access-policies.md) enhedsadgang med yderligere oplysninger, der Teams specifikke. Da Teams med vores andre produkter, kan du også se Politikanbefalinger [til sikring af SharePoint-websteder](sharepoint-file-access-policies.md) og -filer og [Politikanbefalinger til sikring af mail](secure-email-recommended-policies.md).

Disse anbefalinger er baseret på tre forskellige niveauer af sikkerhed og beskyttelse til Teams, der kan anvendes baseret på granulariteten af dine behov: udgangspunkt, virksomhed og særlig sikkerhed. Du kan få mere at vide om disse sikkerhedsniveauer og de anbefalede politikker, der refereres til i disse anbefalinger i [Konfigurationer for identitets- og enhedsadgang](microsoft-365-policies-configurations.md).

Der findes flere anbefalinger, Teams om udrulning, i denne artikel for at dække specifikke godkendelsesforhold, herunder for brugere uden for organisationen. Du skal følge denne vejledning for at få en komplet sikkerhedsoplevelse.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Introduktion til Teams før andre afhængige tjenester

Du behøver ikke at aktivere afhængige tjenester for at komme i gang med Microsoft Teams. Disse tjenester fungerer alle "bare". Du skal dog være forberedt på at administrere følgende tjenesterelaterede elementer:

- Microsoft 365 grupper
- SharePoint teamwebsteder
- OneDrive for Business
- Exchange postkasser
- Stream videoer og Planner-planer (hvis disse tjenester er aktiveret)

## <a name="updating-common-policies-to-include-teams"></a>Opdatering af almindelige politikker, der skal Teams

For at beskytte chat, grupper og indhold i Teams viser nedenstående diagram, hvilke politikker der skal opdateres fra de fælles politikker for identitet og enhedsadgang. For at opdatere hver politik skal du sørge for, Teams og afhængige tjenester er inkluderet i tildelingen af skyapps.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="Oversigten over politikopdateringer til beskyttelse af adgang til Teams og dens afhængige tjenester" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Disse tjenester er de afhængige tjenester, der medtages i tildelingen af skyapps til Teams:

- Microsoft Teams
- SharePoint og OneDrive for Business
- Exchange Online
- Skype for Business Online
- Microsoft Stream (mødeoptagelser)
- Microsoft Planner (Planner-opgaver, og planlæg data)

I denne tabel vises de politikker, der skal revideres[, og](identity-access-policies.md) links til hver politik i de fælles politikker for identitet og adgang til enheder, som har den bredere politik angivet for alle Office programmer.

|Beskyttelsesniveau|Politikker|Yderligere oplysninger om Teams implementering|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisici er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Sørg for Teams og afhængige tjenester er inkluderet på listen over apps. Teams har regler for gæsteadgang og ekstern adgang, som du også skal overveje, kan du få mere at vide om disse regler senere i denne artikel.|
||[Blokere klienter, der ikke understøtter moderne godkendelse](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Medtag Teams og afhængige tjenester i tildelingen af skyapps.|
||[Brugere med høj risiko skal ændre adgangskode](identity-access-policies.md#high-risk-users-must-change-password)|Tvinger Teams brugere til at ændre deres adgangskode, når de logger på, hvis der registreres aktivitet med høj risiko for deres konto. Sørg for Teams og afhængige tjenester er inkluderet på listen over apps.|
||[Anvend politikker for beskyttelse af app-data](identity-access-policies.md#apply-app-data-protection-policies)|Sørg for Teams og afhængige tjenester er inkluderet på listen over apps. Opdater politikken for hver platform (iOS, Android, Windows).|
|**Enterprise**|[Kræv MFA, når risikoen for at logge *på er* *lav, mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams har regler for gæsteadgang og ekstern adgang, som du også skal overveje, kan du få mere at vide om disse regler senere i denne artikel. Medtag Teams og afhængige tjenester i denne politik.|
||[Definer politikker for enhedsoverholdelse](identity-access-policies.md#define-device-compliance-policies)|Medtag Teams og afhængige tjenester i denne politik.|
||[Kræv kompatible *pc'er* og mobilenheder](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Medtag Teams og afhængige tjenester i denne politik.|
|**Speciel sikkerhed**|[*Kræv* altid MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uanset brugeridentiteten vil MFA blive brugt af din organisation. Medtag Teams og afhængige tjenester i denne politik. |

## <a name="teams-dependent-services-architecture"></a>Teams afhængig tjenestearkitektur

Følgende diagram illustrerer de tjenester, som Teams afhænger af. Du kan finde flere oplysninger og illustrationer [Microsoft Teams produktivitetstjenester og relaterede produktivitetstjenester Microsoft 365 IT-arkitekter](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="Diagrammet viser Teams af SharePoint, OneDrive for Business og Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Gæsteadgang og ekstern adgang til Teams

Microsoft Teams definerer følgende adgangstyper:

- **Gæsteadgang** bruger en Azure AD B2B-konto til en gæst eller ekstern bruger, der kan tilføjes som medlem af et team og har alle tilladelse til at få adgang til teamets kommunikation og ressourcer.

- **Ekstern adgang** er for en ekstern bruger, der ikke har en Azure AD B2B-konto. Ekstern adgang kan omfatte invitationer og deltagelse i opkald, chats og møder, men omfatter ikke teammedlemskab og adgang til teamets ressourcer.

Politikker for betinget adgang gælder kun for gæsteadgang i Teams, fordi der er en tilsvarende Azure AD B2B-konto.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Hvis du vil have anbefalede politikker til at tillade adgang for gæster og eksterne brugere med en Azure AD B2B-konto, skal du se Politikker for at tillade gæsteadgang og ekstern [B2B-konto](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>Gæsteadgang i Teams

Ud over politikkerne for brugere, der er interne for din virksomhed eller organisation, kan administratorer aktivere gæsteadgang for at give personer, der er eksterne i forhold til din virksomhed eller organisation, mulighed for at få adgang til Teams ressourcer og interagere med interne personer i forbindelse med ting som gruppesamtaler, chat og møder.

Du kan finde flere oplysninger om gæsteadgang, og hvordan du [implementerer den, Teams gæsteadgang](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Ekstern adgang i Teams

Ekstern adgang forveksles nogle gange med gæsteadgang, så det er vigtigt at være klar over, at disse to ikke-interne adgangsmekanismer er forskellige typer adgang.

Ekstern adgang er en metode til Teams brugere fra et helt eksternt domæne til at finde, ringe, chatte og konfigurere møder med dine brugere i Teams. Teams administratorer konfigurerer ekstern adgang på organisationsniveau. Få mere at vide under [Administrer ekstern adgang i Microsoft Teams](/microsoftteams/manage-external-access).

Eksterne adgangsbrugere har mindre adgang og funktionalitet end en enkeltperson, der er blevet tilføjet via gæsteadgang. Eksterne adgangsbrugere kan f.eks. chatte med dine interne brugere med Teams men kan ikke få adgang til teamkanaler, filer eller andre ressourcer.

Ekstern adgang bruger ikke Azure AD B2B-brugerkonti og bruger derfor ikke politikker for betinget adgang.

## <a name="teams-policies"></a>Teams politikker

Uden for de fælles politikker, der er anført ovenfor, er Teams specifikke politikker, der kan og skal konfigureres til at administrere Teams funktioner.

### <a name="teams-and-channels-policies"></a>Teams og kanaler politikker

Teams og kanaler er to almindeligt brugte elementer i Microsoft Teams, og der er politikker, du kan sætte ind for at styre, hvad brugerne kan og ikke kan gøre, når de bruger teams og kanaler. Selvom du kan oprette et globalt team, vil du, hvis din organisation har 5000 brugere eller mindre, sandsynligvis finde det nyttigt at have mindre teams og kanaler til bestemte formål helt i overensstemmelse med dine organisationsbehov.

Det anbefales, at du ændrer standardpolitikken eller opretter brugerdefinerede politikker, og du kan få mere at vide om administration af dine politikker på dette link: Administrer [teams-politikker Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Meddelelsespolitikker

Beskeder eller chat kan også administreres via den globale standardpolitik eller via brugerdefinerede politikker, og det kan hjælpe brugerne med at kommunikere med hinanden på en måde, der passer til din organisation. Disse oplysninger kan gennemses under [Administration af meddelelsespolitikker i Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Mødepolitikker

Ingen diskussion af Teams være fuldstændig uden planlægning og implementering af politikker omkring Teams møder. Møder er en vigtig komponent i Teams, så folk formelt kan mødes og præsentere for mange brugere på én gang og dele indhold, der er relevant for mødet. Det er vigtigt at angive de rigtige politikker for organisationen omkring møder.

Du kan finde flere oplysninger [under Administrer mødepolitikker i Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Politikker for apptilladelser

Teams giver dig også mulighed for at bruge apps på forskellige steder, f.eks. kanaler eller personlige chats. At have politikker for, hvilke apps der kan tilføjes og bruges, og hvor det er afgørende for at opretholde et indholdsrigt miljø, der også er sikkert.

Hvis du vil have mere at vide om tilladelsespolitikker for apps, skal [du se Administrere tilladelsespolitikker for apps Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Næste trin

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Trin 4: Politikker for Microsoft 365 skyapps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Konfigurere Betingede adgangspolitikker for:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)