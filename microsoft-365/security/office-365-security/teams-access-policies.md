---
title: Anbefalede Teams politikker – Microsoft 365 for virksomheds | Microsoft Docs
description: Beskriver politikkerne for Microsofts anbefalinger til, hvordan du sikrer Teams kommunikation og filadgang.
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
ms.openlocfilehash: 25f70d3ccdf11daa6a52d16b66d612c04ab8876a
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131168"
---
# <a name="policy-recommendations-for-securing-teams-chats-groups-and-files"></a>Politikanbefalinger til sikring af Teams chats, grupper og filer

I denne artikel beskrives det, hvordan du implementerer de anbefalede Nul tillid identitets- og enhedsadgangspolitikker for at beskytte Microsoft Teams chats, grupper og indhold, f.eks. filer og kalendere. Denne vejledning bygger på de [fælles politikker for identitets- og enhedsadgang](identity-access-policies.md) med yderligere oplysninger, der er Teams specifikke. Da Teams integreres med vores andre produkter, kan du også se [Politikanbefalinger til sikring af SharePoint websteder og filer](sharepoint-file-access-policies.md) og [politikanbefalinger til sikring af mail](secure-email-recommended-policies.md).

Disse anbefalinger er baseret på tre forskellige niveauer af sikkerhed og beskyttelse af Teams, der kan anvendes baseret på granulariteten af dine behov: udgangspunkt, virksomhed og specialiseret sikkerhed. Du kan få mere at vide om disse sikkerhedsniveauer og de anbefalede politikker, der henvises til af disse anbefalinger, i [konfigurationerne Identitet og enhedsadgang](microsoft-365-policies-configurations.md).

Der er flere anbefalinger, der er specifikke for Teams udrulning, i denne artikel for at dække specifikke godkendelsesforhold, herunder for brugere uden for din organisation. Du skal følge denne vejledning for at få en komplet sikkerhedsoplevelse.

## <a name="getting-started-with-teams-before-other-dependent-services"></a>Introduktion til Teams før andre afhængige tjenester

Du behøver ikke at aktivere afhængige tjenester for at komme i gang med Microsoft Teams. Disse tjenester vil alle "bare fungere". Du skal dog være forberedt på at administrere følgende tjenesterelaterede elementer:

- Microsoft 365 grupper
- SharePoint teamwebsteder
- OneDrive for Business
- Exchange postkasser
- Stream-videoer og Planner-planer (hvis disse tjenester er aktiveret)

## <a name="updating-common-policies-to-include-teams"></a>Opdatering af almindelige politikker, så de omfatter Teams

For at beskytte chat, grupper og indhold i Teams viser følgende diagram, hvilke politikker der skal opdateres fra de fælles politikker for identitets- og enhedsadgang. For hver politik, der skal opdateres, skal du sørge for, at Teams og afhængige tjenester er inkluderet i tildelingen af cloudapps.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png" alt-text="Oversigten over politikopdateringer til beskyttelse af adgang til Teams og de afhængige tjenester" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-teams.png":::

Disse tjenester er de afhængige tjenester, der skal medtages i tildelingen af cloudapps til Teams:

- Microsoft Teams
- SharePoint og OneDrive for Business
- Exchange Online
- Skype for Business Online
- Microsoft Stream (mødeoptagelser)
- Microsoft Planner (planlægningsopgaver og plandata)

I denne tabel vises de politikker, der skal besøges igen, og links til hver politik i de [fælles politikker for identitets- og enhedsadgang](identity-access-policies.md), som har den bredere politik, der er angivet for alle Office programmer.

|Beskyttelsesniveau|Politikker|Yderligere oplysninger om Teams implementering|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisikoen er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Sørg for, at Teams og afhængige tjenester er inkluderet på listen over apps. Teams har regler for gæsteadgang og ekstern adgang, som du også skal overveje, får du mere at vide om disse regler senere i denne artikel.|
||[Bloker klienter, der ikke understøtter moderne godkendelse](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Medtag Teams og afhængige tjenester i tildelingen af cloudapps.|
||[Brugere med høj risiko skal ændre adgangskode](identity-access-policies.md#high-risk-users-must-change-password)|Tvinger Teams brugere til at ændre deres adgangskode, når de logger på, hvis der registreres højrisikoaktivitet for deres konto. Sørg for, at Teams og afhængige tjenester er inkluderet på listen over apps.|
||[Anvend politikker for databeskyttelse i APP](identity-access-policies.md#apply-app-data-protection-policies)|Sørg for, at Teams og afhængige tjenester er inkluderet på listen over apps. Opdater politikken for hver platform (iOS, Android, Windows).|
|**Enterprise**|[Kræv MFA, når logonrisikoen er *lav*, *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Teams har regler for gæsteadgang og ekstern adgang, som du også skal overveje, får du mere at vide om disse regler senere i denne artikel. Medtag Teams og afhængige tjenester i denne politik.|
||[Definer politikker for enhedsoverholdelse](identity-access-policies.md#define-device-compliance-policies)|Medtag Teams og afhængige tjenester i denne politik.|
||[Kræv kompatible pc'er *og* mobilenheder](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Medtag Teams og afhængige tjenester i denne politik.|
|**Specialiseret sikkerhed**|[*Kræv altid* MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Uanset brugeridentitet bruges MFA af din organisation. Medtag Teams og afhængige tjenester i denne politik. |

## <a name="teams-dependent-services-architecture"></a>arkitektur for Teams afhængige tjenester

Som reference illustrerer følgende diagram de tjenester, Teams er afhængig af. Du kan få flere oplysninger og illustrationer [under Microsoft Teams og relaterede produktivitetstjenester i Microsoft 365 til it-arkitekter](../../solutions/productivity-illustrations.md).

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png" alt-text="Diagrammet, der viser Teams afhængigheder af SharePoint, OneDrive for Business og Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-logical-architecture-teams.png":::

## <a name="guest-and-external-access-for-teams"></a>Gæsteadgang og ekstern adgang til Teams

Microsoft Teams definerer følgende adgangstyper:

- **Gæsteadgang** bruger en Azure AD B2B-konto for en gæst eller ekstern bruger, der kan tilføjes som medlem af et team og har alle tilladelser til at få adgang til kommunikation og ressourcer for teamet.

- **Ekstern adgang** er for en ekstern bruger, der ikke har en Azure AD B2B-konto. Ekstern adgang kan omfatte invitationer og deltagelse i opkald, chats og møder, men omfatter ikke teammedlemskab og adgang til teamets ressourcer.

Politikker for betinget adgang gælder kun for gæsteadgang i Teams, fordi der er en tilsvarende Azure AD B2B-konto.

<!--
In Azure AD, guest and external users are the same. The user type for both of these is Guest. Guest users are B2B users. Microsoft Teams differentiates between guest users and external users in the app. While it's important to understand how each of these are treated in Teams, both types of users are B2B users in Azure AD and the recommended policies for B2B users apply to both.

-->

Hvis du vil have anbefalet politikker, der giver adgang for gæstebrugere og eksterne brugere med en Azure AD B2B-konto, skal du se [Politikker for at give adgang til gæste- og eksterne B2B-konti](identity-access-policies-guest-access.md).

### <a name="guest-access-in-teams"></a>Gæsteadgang i Teams

Ud over politikkerne for brugere, der er interne i din virksomhed eller organisation, kan administratorer give gæsteadgang til at give brugere, der er eksterne for din virksomhed eller organisation, adgang til Teams ressourcer og interagere med interne personer for ting som gruppesamtaler, chat og møder.

Du kan få flere oplysninger om gæsteadgang, og hvordan du implementerer den, [under Teams gæsteadgang](/microsoftteams/guest-access).

### <a name="external-access-in-teams"></a>Ekstern adgang i Teams

Ekstern adgang forveksles nogle gange med gæsteadgang, så det er vigtigt at være klar over, at disse to ikke-interne adgangsmekanismer er forskellige typer adgang.

Ekstern adgang er en måde, hvorpå Teams brugere fra et helt eksternt domæne kan finde, ringe til, chatte og konfigurere møder med dine brugere i Teams. Teams administratorer konfigurere ekstern adgang på organisationsniveau. Du kan få flere oplysninger under [Administrer ekstern adgang i Microsoft Teams](/microsoftteams/manage-external-access).

Brugere med ekstern adgang har mindre adgang og funktionalitet end en person, der er blevet tilføjet via gæsteadgang. Brugere med ekstern adgang kan f.eks. chatte med dine interne brugere med Teams, men de kan ikke få adgang til teamkanaler, filer eller andre ressourcer.

Ekstern adgang bruger ikke Azure AD B2B-brugerkonti og bruger derfor ikke politikker for betinget adgang.

## <a name="teams-policies"></a>Teams politikker

Uden for de fælles politikker, der er angivet ovenfor, er der Teams specifikke politikker, der kan og bør konfigureres til at administrere forskellige Teams funktioner.

### <a name="teams-and-channels-policies"></a>politikker for Teams og kanaler

Teams og kanaler er to almindeligt anvendte elementer i Microsoft Teams, og der er politikker, du kan indføre for at styre, hvad brugerne kan og ikke kan gøre, når de bruger teams og kanaler. Selvom du kan oprette et globalt team, vil det sandsynligvis være nyttigt at have mindre teams og kanaler til bestemte formål i overensstemmelse med organisationens behov, hvis din organisation har 5000 brugere eller derunder.

Det anbefales at ændre standardpolitikken eller oprette brugerdefinerede politikker, og du kan få mere at vide om administration af dine politikker på dette link: [Administrer teams-politikker i Microsoft Teams](/microsoftteams/teams-policies).

### <a name="messaging-policies"></a>Meddelelsespolitikker

Beskeder eller chat kan også administreres via den globale standardpolitik eller via brugerdefinerede politikker, og det kan hjælpe dine brugere med at kommunikere med hinanden på en måde, der passer til din organisation. Disse oplysninger kan gennemses under [Administration af meddelelsespolitikker i Teams](/microsoftteams/messaging-policies-in-teams).

### <a name="meeting-policies"></a>Mødepolitikker

Ingen diskussion af Teams ville være fuldført uden planlægning og implementering af politikker omkring Teams møder. Møder er en vigtig del af Teams, så folk formelt kan mødes og præsentere for mange brugere på én gang og dele indhold, der er relevant for mødet. Det er vigtigt at angive de rette politikker for din organisation omkring møder.

Du kan få flere oplysninger ved at gennemse [Administrer mødepolitikker i Teams](/microsoftteams/meeting-policies-in-teams).

### <a name="app-permission-policies"></a>Politikker for apptilladelser

Teams giver dig også mulighed for at bruge apps forskellige steder, f.eks. kanaler eller personlige chats. Det er vigtigt at have politikker om, hvilke apps der kan tilføjes og bruges, og hvor det er vigtigt at bevare et indholdsrigt miljø, der også er sikkert.

Hvis du vil have mere at vide om politikker for apptilladelser, skal du se [Administrer app-tilladelsespolitikker i Microsoft Teams](/microsoftteams/teams-app-permission-policies).

## <a name="next-steps"></a>Næste trin

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Trin 4: Politikker for Microsoft 365 cloudapps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Konfigurer politikker for betinget adgang for:

- [Exchange Online](secure-email-recommended-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
