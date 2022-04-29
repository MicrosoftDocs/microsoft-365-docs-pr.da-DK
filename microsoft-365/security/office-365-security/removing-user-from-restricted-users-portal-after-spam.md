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
description: Administratorer kan få mere at vide om, hvordan de fjerner brugere fra siden Brugere med begrænset adgang på portalen Microsoft 365 Defender. Brugere føjes til portalen Brugere med begrænset adgang for at sende udgående spam, typisk som følge af konto kompromitteret.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 229dfbb7a0441f4a6cb6632432c0032f4ce4308e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130730"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>Fjern blokerede brugere fra portalen Brugere med begrænset adgang i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis en bruger overskrider en af de grænser for udgående afsendelse, som angivet i [tjenestegrænserne](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) eller i [politikker for udgående spam](configure-the-outbound-spam-policy.md), er brugeren begrænset til at sende mail, men vedkommende kan stadig modtage mail.

Brugeren føjes til siden **Begrænsede brugere** på portalen Microsoft 365 Defender. Når de forsøger at sende en mail, returneres meddelelsen i en rapport om manglende levering (også kendt som en NDR- eller bounce-meddelelse) med fejlkoden [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) og følgende tekst:

> "Meddelelsen kunne ikke leveres, fordi du ikke blev genkendt som en gyldig afsender. Den mest almindelige årsag til dette er, at din mailadresse er mistænkt for at sende spam, og det er ikke længere tilladt at sende e-mail.  Kontakt din mailadministrator for at få hjælp. Fjernserveren returnerede '550 5.1.8 Adgang nægtet, ugyldig udgående afsender."

Administratorer kan fjerne brugere fra siden **Begrænsede brugere** i Microsoft 365 Defender eller i Exchange Online PowerShell.

## <a name="learn-more-on-restricted-entities"></a>Få mere at vide om begrænsede enheder

En begrænset enhed er et objekt, der er blevet blokeret fra at sende mail, fordi det enten er blevet potentielt kompromitteret, eller fordi afsendelsesgrænsen er overskredet.

Der er to typer begrænsede enheder: 

- **Begrænset bruger**: Få mere at vide om, hvorfor en bruger kan begrænses, og hvordan man håndterer begrænsede brugere (denne artikel).  

- **Begrænset connector**: Du kan få flere oplysninger om, hvorfor en connector kan begrænses, og hvordan du håndterer begrænsede connectors, under [Fjern blokerede connectors fra portalen Begrænsede enheder](remove-blocked-connectors.md). 

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Begrænsede brugere** , skal du bruge <https://security.microsoft.com/restrictedusers>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil fjerne brugere fra portalen Begrænsede brugere, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til portalen Begrænsede brugere, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- En afsender, der overskrider grænserne for udgående mail, er en indikator for en kompromitteret konto. Før du fjerner brugeren fra portalen Begrænsede brugere, skal du sørge for at følge de påkrævede trin for at få kontrol over kontoen igen. Du kan få flere oplysninger under [Besvarelse af en kompromitteret mailkonto i Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Brug Microsoft 365 Defender-portalen til at fjerne en bruger fra listen Brugere med begrænset adgang

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejde** \> **Gennemse** **Brugere med begrænset adgang**\>. Hvis du vil gå direkte til siden **Begrænsede brugere** , skal du bruge <https://security.microsoft.com/restrictedusers>.

2. På siden **Begrænsede brugere** skal du finde og vælge den bruger, du vil fjerne blokeringen af, ved at klikke på brugeren.

3. Klik på handlingen **Fjern blokering** , der vises.

4. I pop op-vinduet **Fjern blokering af bruger** , der vises, skal du læse oplysningerne om den begrænsede konto. Du skal gennemgå anbefalingerne for at sikre, at du foretager de korrekte handlinger, hvis kontoen kompromitteres.

   Klik på **Næste**, når du er færdig.

5. Det næste skærmbillede indeholder anbefalinger, der hjælper med at forhindre fremtidig kompromis. Aktivering af multifaktorgodkendelse (MFA) og nulstilling af adgangskoden er et godt forsvar.

   Klik på **Send**, når du er færdig.

6. Klik på **Ja** for at bekræfte ændringen.

   > [!NOTE]
   > Det kan tage op til 1 time, før alle begrænsninger fjernes fra brugeren.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Kontrollér beskedindstillingerne for begrænsede brugere

Standardbeskedpolitikken med navnet Bruger, der er **begrænset til at sende mail** , giver automatisk administratorer besked, når brugere blokeres fra at sende udgående mail. Du kan bekræfte disse indstillinger og tilføje flere brugere for at give besked. Du kan få flere oplysninger om politikker for beskeder [under Beskedpolitikker i Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Hvis beskeder skal fungere, skal søgning i overvågningslog være aktiveret. Du kan finde flere oplysninger under [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & politikker for samarbejde** \> **& regler** \> **Beskedpolitik**. Hvis du vil gå direkte til siden **Beskedpolitik** , skal du bruge <https://security.microsoft.com/alertpolicies>.

2. På siden **Beskedpolitik** skal du finde og vælge den besked med navnet Bruger, der **ikke kan sende mail**. Du kan sortere politikkerne efter navn eller bruge **søgefeltet** til at finde politikken.

3. I pop op-vinduet Bruger, der **er begrænset til at sende mails** , som vises, skal du bekræfte eller konfigurere følgende indstillinger:
   - **Status**: Kontrollér, at beskeden er slået Til ![/fra.](../../media/scc-toggle-on.png).
   - **Mailmodtagere**: Klik på **Rediger** , og bekræft eller konfigurer følgende indstillinger i pop op-vinduet **Rediger modtagere** , der vises:
     - **Send mailmeddelelser**: Kontrollér, at dette er valgt (**Slået til**).
     - **Mailmodtagere**: Standardværdien er **TenantAdmins** (dvs. **globale administratormedlemmer** ). Hvis du vil tilføje flere modtagere, skal du klikke i et tomt område i feltet. Der vises en liste over modtagere, og du kan begynde at skrive et navn for at filtrere og vælge en modtager. Du kan fjerne en eksisterende modtager fra feltet ved at klikke på ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for deres navn.
     - **Grænse for daglig meddelelse**: Standardværdien er **Ingen grænse** , men du kan vælge en grænse for det maksimale antal meddelelser pr. dag.

     Klik på **Gem**, når du er færdig.

4. Tilbage på pop op-vinduet Bruger, der **er begrænset til at sende mail** , skal du klikke på **Luk**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Brug Exchange Online PowerShell til at få vist og fjerne brugere fra listen Brugere med begrænset adgang

Hvis du vil have vist denne liste over brugere, der ikke kan sende mails, skal du køre følgende kommando:

```powershell
Get-BlockedSenderAddress
```

Hvis du vil have vist detaljer om en bestemt bruger, skal du erstatte \<emailaddress\> med vedkommendes mailadresse og køre følgende kommando:

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Hvis du vil fjerne en bruger fra listen Begrænsede brugere, skal du erstatte \<emailaddress\> med vedkommendes mailadresse og køre følgende kommando:

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
