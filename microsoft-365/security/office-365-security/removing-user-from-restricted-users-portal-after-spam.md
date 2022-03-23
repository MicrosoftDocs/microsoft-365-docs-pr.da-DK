---
title: Fjern blokerede brugere fra portalen Begrænsede brugere
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.exch.eac.ActionCenter.Restricted.Users.RestrictedUsers
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: Administratorer kan lære, hvordan du fjerner brugere fra siden Begrænsede brugere på Microsoft 365 Defender portal. Brugere føjes til portalen Begrænsede brugere for at sende udgående spam, typisk som et resultat af, at kontoen er blevet kompromitteret.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 66b810f7bb6381d405ee7ffc0d6b1cf7a10f2bf2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589157"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>Fjern blokerede brugere fra portalen Begrænsede brugere i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis en bruger overskrider en af begrænsningerne for udgående afsendelse som angivet i tjenestegrænserne eller politikkerne for udgående [spam](configure-the-outbound-spam-policy.md), er brugeren begrænset i at kunne sende mail, men brugeren kan stadig modtage mail.[](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options)

Brugeren føjes til siden **Begrænsede brugere** i Microsoft 365 Defender portal. Når de forsøger at sende mail, returneres meddelelsen i en rapport om manglende levering (også kaldet en NDR eller meddelelser om ikke-leveret post) med fejlkoden [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) og følgende tekst:

> "Meddelelsen kunne ikke leveres, fordi du ikke blev genkendt som en gyldig afsender. Den mest almindelige årsag til dette er, at der er mistanke om, at din mailadresse sender spam, og at den ikke længere har tilladelse til at sende mails.  Kontakt mailadministratoren for at få hjælp. Fjernserver returnerede '550 5.1.8 Access denied, bad udgående afsender."

Administratorer kan fjerne brugere fra siden Begrænsede brugere i Microsoft 365 Defender eller i Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Begrænsede brugere** skal du bruge <https://security.microsoft.com/restrictedusers>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil fjerne brugere fra portalen Begrænsede brugere, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til portalen Brugere med begrænset adgang skal du være medlem af **rollegrupperne Global læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- En afsender, der overskrider grænsen for udgående mail, er en indikator for en kompromitteret konto. Før du fjerner brugeren fra portalen Begrænsede brugere, skal du sørge for at følge de nødvendige trin for at få kontrollen over deres konto tilbage. Du kan få mere at vide [under Svar på en kompromitteret mailkonto i Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Brug portalen Microsoft 365 Defender til at fjerne en bruger fra listen Begrænsede brugere

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail og & Gennemse** \> brugere **med** \> **begrænset adgang**. For at gå direkte til **siden Begrænsede brugere** skal du bruge <https://security.microsoft.com/restrictedusers>.

2. På siden **Begrænsede brugere** skal du finde og vælge den bruger, du vil fjerne blokeringen af, ved at klikke på brugeren.

3. Klik på handlingen **Fjern blokering** , der vises.

4. I pop **op-pop op-pop** op-vindue med brugere, der vises, skal du læse oplysningerne om den begrænsede konto. Du bør gennemgå anbefalingerne for at sikre, at du tager de rigtige handlinger i tilfælde af, at kontoen bliver kompromitteret.

   Klik på Næste, når du er **færdig**.

5. Den næste skærm indeholder anbefalinger til at forhindre fremtidigt kompromis. Aktivering af multifaktorgodkendelse (MFA) og nulstilling af adgangskoden er et godt forsvar.

   Klik på Send, når du er **færdig**.

6. Klik **på Ja** for at bekræfte ændringen.

   > [!NOTE]
   > Det kan tage op til 1 time, før alle begrænsninger fjernes fra brugeren.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Bekræft beskedindstillingerne for begrænsede brugere

Standardpolitikken for påmindelse, der hedder **Bruger, der ikke kan sende** mails, giver automatisk administratorer besked, når brugere er blokeret fra at sende udgående mail. Du kan bekræfte disse indstillinger og tilføje flere brugere, der skal underrettes. Du kan finde flere oplysninger om beskedpolitikker [under Påmindelsespolitikker i Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> For at beskeder kan fungere, skal søgning i overvågningsloggen være aktiveret. Du kan finde flere oplysninger [i Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

1. I portalen Microsoft 365 Defender skal du gå til **& politikker for** \> **samarbejde &** **reglerBeskedpolitik**\>.

2. På siden **Beskedpolitik skal** du finde og vælge beskeden Bruger begrænset fra **at sende mail**. Du kan sortere politikkerne efter navn eller bruge **feltet Søg til** at finde politikken.

3. I pop **op-menuen Bruger begrænset i at sende** mails, der vises, skal du bekræfte eller konfigurere følgende indstillinger:
   - **Status**: Bekræft, at beskeden er slået ![til.](../../media/scc-toggle-on.png).
   - **Mailmodtagere**: Klik **på Rediger** og bekræft eller konfigurer følgende indstillinger i pop **op-menuen Rediger** modtagere, der vises:
     - **Send mailbeskeder**: Kontrollér, at dette er valgt (**Til**).
     - **Mailmodtagere**: Standardværdien er **TenantAdmins** (dvs. **globale administratormedlemmer** ). Hvis du vil tilføje flere modtagere, skal du klikke i et tomt område i feltet. Der vises en liste over modtagere, og du kan begynde at skrive et navn for at filtrere og vælge en modtager. Du kan fjerne en eksisterende modtager fra feltet ved at klikke på ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for navnet.
     - **Daglig beskedgrænse**: Standardværdien er **Ingen grænse,** men du kan vælge en grænse for det maksimale antal meddelelser pr. dag.

     Klik på **Gem**, når du er færdig.

4. Tilbage på pop **op-menuen Bruger begrænset fra at sende** mail skal du klikke **på Luk**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Brug Exchange Online PowerShell til at få vist og fjerne brugere fra listen Begrænsede brugere

For at få vist denne liste over brugere, der er begrænset i at sende mail, skal du køre følgende kommando:

```powershell
Get-BlockedSenderAddress
```

Hvis du vil have vist oplysninger om en bestemt bruger, \<emailaddress\> skal du erstatte med dennes mailadresse og køre følgende kommando:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Hvis du vil fjerne en bruger fra listen Begrænsede brugere, skal du \<emailaddress\> erstatte med deres mailadresse og køre følgende kommando:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
