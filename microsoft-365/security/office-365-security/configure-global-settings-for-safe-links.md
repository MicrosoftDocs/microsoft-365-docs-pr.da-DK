---
title: Konfigurer globale indstillinger for Pengeskab Links i Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan lære, hvordan de får vist og konfigurerer globale indstillinger (listen "Bloker følgende URL-adresser" og beskyttelse af Office 365-apps) til Pengeskab Links i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 857519e93df9490ebeb178a23a44ddddbdfc83ef
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63601690"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Konfigurer globale indstillinger for Pengeskab Links i Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til virksomhedskunder, der [har Microsoft Defender Office 365](defender-for-office-365.md). Hvis du er privat bruger og leder efter oplysninger om Safelinks i Outlook, skal du [se Avanceret Outlook.com-sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Pengeskab Links er en funktion i [Microsoft Defender til Office 365](defender-for-office-365.md), der giver URL-scanning af indgående mails i mailflow, og tidspunktet for klikbekræftelse af URL-adresser og links i mails og på andre placeringer. Du kan finde flere oplysninger [Pengeskab Links i Microsoft Defender for Office 365](safe-links.md).

Du konfigurerer de Pengeskab indstillinger for links Pengeskab politikker for links. Du kan finde en [vejledning under Konfigurere Pengeskab Links-politikker i Microsoft Defender Office 365](set-up-safe-links-policies.md).

Men linkene Pengeskab også de følgende globale indstillinger, som du konfigurerer uden for selve politikkerne Pengeskab links:

- Listen **Bloker følgende URL-adresser** . Denne indstilling gælder for alle brugere, der er inkluderet i alle aktive Pengeskab politikker for links. Du kan finde flere oplysninger på [listen "Bloker følgende URL-adresser" for Pengeskab Links](safe-links.md#block-the-following-urls-list-for-safe-links)
- Pengeskab links til Office 365 apps. Disse indstillinger gælder for alle brugere i organisationen, der har licens til Defender til Office 365, uanset om brugerne er inkluderet i aktive Pengeskab Links-politikker eller ej. Du kan finde flere oplysninger [Pengeskab Indstillinger for links til Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).

Du kan konfigurere de globale Pengeskab Links-indstillinger på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell for berettigede Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser, men med Microsoft Defender Office 365-tilføjelsesabonnementer).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Selvom der ikke er nogen standardpolitik for Pengeskab Links, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab **Kæder-politikker**). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md). Du kan også oprette Pengeskab links-politikker, der gælder for bestemte brugere, grupper eller domæner. Du kan finde en [vejledning under Konfigurere Pengeskab Links-politikker i Microsoft Defender Office 365](set-up-safe-links-policies.md).

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil konfigurere de globale Pengeskab links, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator**.
  - For skrivebeskyttet adgang til de globale indstillinger for Pengeskab Links skal du være medlem af rollegrupperne **Global læser** **eller Sikkerhedslæser**.

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- For vores anbefalede værdier for de globale indstillinger for Pengeskab Links skal du [Pengeskab Indstillinger for links](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Der kan gå op til 30 minutter, før en ny eller opdateret politik anvendes.

- [Nye funktioner bliver løbende føjet til Microsoft Defender for Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Når der tilføjes nye funktioner, kan det være nødvendigt at foretage justeringer af dine eksisterende Pengeskab politikker for links.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Konfigurer listen "Bloker følgende URL-adresser" Microsoft 365 Defender portalen

Listen **Bloker følgende URL-adresser** identificerer de links, der altid bør blokeres ved at Pengeskab links i understøttede apps. Du kan finde flere oplysninger [på listen "Bloker følgende URL-adresser" for Pengeskab Links](safe-links.md#block-the-following-urls-list-for-safe-links).

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til & **politikker** \> for samarbejde **& Regler** \>  \> Pengeskab **Links** i **sektionen** Politikker. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links skal** du klikke på **Globale indstillinger**. I dialogboksen **Pengeskab for din organisation pop op-politik**, der vises, skal du gå til **feltet Bloker følgende URL-adresser**.

3. Konfigurer en eller flere poster som beskrevet i [Postsyntaksen for listen "Bloker følgende URL-adresser"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

   Klik på **Gem**, når du er færdig.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Konfigurer listen "Bloker følgende URL-adresser" i PowerShell

Hvis du vil have mere at vide om postsyntaksen, [skal du se Postsyntaksen for listen "Bloker følgende URL-adresser"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

Du kan bruge **Get-AtpPolicyForO365-cmdlet'en til at** få vist eksisterende poster i _egenskaben BlockURLs_ .

- Hvis du vil tilføje værdier, der erstatter eksisterende poster, skal du bruge følgende syntaks i Exchange Online PowerShell eller Exchange Online Protection PowerShell:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  I dette eksempel føjes følgende poster til listen:

  - Bloker domænet, underdomæner og stier til fabrikam.com.
  - Bloker underdomæneundersøgelse, men ikke det overordnede domæne eller andre underdomæner i tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Hvis du vil tilføje eller fjerne værdier uden at påvirke andre eksisterende poster, skal du bruge følgende syntaks:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  I dette eksempel tilføjes en ny adatum.com, og posten for fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>Konfigurere Pengeskab links til Office 365-apps i Microsoft 365 Defender portalen

Pengeskab links til Office 365-apps gælder for dokumenter i understøttede Office, mobilapps og webapps. Du kan finde flere oplysninger [Pengeskab Indstillinger for links til Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).

1. I Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til & **politikker** \> for samarbejde **& Regler** \>  \> Pengeskab **Links** i **sektionen** Politikker. For at gå direkte til **siden Pengeskab Links skal** du bruge <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links skal** du klikke på **Globale indstillinger**. I afsnittet **Pengeskab Links for** din organisation, der vises, skal du konfigurere følgende indstillinger i sektionen Indstillinger, der gælder for indhold i **understøttede Office 365-apps**:

   - **Brug Pengeskab links i Office 365-apps**: Bekræft, at til/fra-knappen er til højre for at aktivere Pengeskab Links for understøttede Office 365-apps: ![Slå til.](../../media/scc-toggle-on.png).

   - Registrer ikke, hvornår brugere klikker på beskyttede **links i Office 365-apps**: Flyt til/fra-knappen til venstre for at spore brugerklik, der er relateret til blokerede URL-adresser i understøttede Office 365-apps: ![Slå fra.](../../media/scc-toggle-off.png).

   - Lad ikke brugere klikke igennem til den oprindelige **URL-adresse i Office 365-apps**: Kontrollér, at til/fra-knappen er til højre for at forhindre brugere i at klikke igennem til den oprindelige blokerede URL-adresse i understøttede Office 365-apps: ![Til/fra.](../../media/scc-toggle-on.png).

   Klik på **Gem**, når du er færdig.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>Konfigurere Pengeskab Links-beskyttelse for Office 365-apps i PowerShell

Hvis du hellere vil bruge PowerShell til at konfigurere Pengeskab Links-beskyttelse for Office 365-apps, skal du bruge følgende syntaks i Exchange Online PowerShell eller Exchange Online Protection PowerShell:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

I dette eksempel konfigureres følgende indstillinger for Pengeskab links i Office 365 apps:

- Pengeskab Links til Office 365-apps er slået til (vi bruger ikke _parameteren EnableSafeLinksForO365Clients_, og standardværdien er $true).
- Brugerklik relateret til blokerede URL-adresser i understøttede Office 365 apps registreres.
- Brugerne har ikke tilladelse til at klikke igennem den oprindelige blokerede URL-adresse i understøttede Office 365-apps (vi bruger ikke _parameteren AllowClickThrough_, og standardværdien er $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

For at bekræfte, at du har konfigureret de globale indstillinger for Pengeskab Links (listen Bloker følgende  URL-adresser og Office 365-appbeskyttelsesindstillingerne), skal du gøre et af følgende:

- På siden **Pengeskab links i** Microsoft 365 Defender på <https://security.microsoft.com/safelinksv2>skal du klikke på **Globale** indstillinger og kontrollere indstillingerne i det pop op-vindue, der vises.

- I Exchange Online PowerShell eller Exchange Online Protection PowerShell skal du køre følgende kommando og bekræfte indstillingerne:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
