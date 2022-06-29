---
title: Konfigurer globale indstillinger for indstillinger for Sikre links i Defender for Office 365
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
description: Administratorer kan få mere at vide om, hvordan de kan få vist og konfigurere globale indstillinger (listen "Bloker følgende URL-adresser" og beskyttelse af Office 365 apps) for Sikre links i Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c8b40109f20215b86a2264ed1a9f69c8db43bda
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487559"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Konfigurer globale indstillinger for Sikre links i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til erhvervskunder, der har [Microsoft Defender for Office 365](defender-for-office-365.md). Hvis du er hjemmebruger og leder efter oplysninger om Safelinks i Outlook, skal du se [Avanceret Outlook.com sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Sikre links er en funktion i [Microsoft Defender for Office 365](defender-for-office-365.md), der leverer URL-scanning af indgående mails i et mailflow og tidspunktet for klikbekræftelse af URL-adresser og links i mails og andre steder. Du kan få flere oplysninger [under Sikre links i Microsoft Defender for Office 365](safe-links.md).

Du konfigurerer de fleste indstillinger for Sikre links i politikker for sikre links. Du kan finde instruktioner [under Konfigurer politikker for sikre links i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

Men Safe Links bruger også følgende globale indstillinger, som du konfigurerer uden for selve politikkerne for Sikre links:

- Listen **Bloker følgende URL-adresser** . Denne indstilling gælder for alle brugere, der er inkluderet i alle aktive politikker for sikre links. Du kan få flere oplysninger på [listen "Bloker følgende URL-adresser" for Sikre links](safe-links.md#block-the-following-urls-list-for-safe-links)

- Beskyttelse af sikre links for Office 365 apps. Disse indstillinger gælder for alle brugere i organisationen, der er licenseret til Defender for Office 365, uanset om brugerne er inkluderet i aktive politikker for sikre links eller ej. Du kan få flere oplysninger under [Indstillinger for sikre links for Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).

Du kan konfigurere de globale indstillinger for Sikre links på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til berettigede Microsoft 365-organisationer med postkasser i Exchange Online; separat EOP PowerShell til organisationer uden Exchange Online postkasser, men med Microsoft Defender for Office 365 abonnementer på tilføjelsesprogrammer).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Selvom der ikke er nogen standardpolitik for Sikre links, giver den forudindstillede sikkerhedspolitik for **indbygget beskyttelse** beskyttelse af sikre links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede politikker for sikre links). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md). Du kan også oprette politikker for sikre links, der gælder for bestemte brugere, grupper eller domæner. Du kan finde instruktioner [under Konfigurer politikker for sikre links i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, skal du se [Opret forbindelse til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil konfigurere de globale indstillinger for Sikre links, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til de globale indstillinger for Sikre links, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Du kan se vores anbefalede værdier for de globale indstillinger for Sikre links under [Indstillinger for sikre links](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Der kan gå op til 30 minutter, før en ny eller opdateret politik anvendes.

- [Nye funktioner føjes løbende til Microsoft Defender for Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Efterhånden som der tilføjes nye funktioner, skal du muligvis foretage justeringer af dine eksisterende politikker for sikre links.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Konfigurer listen "Bloker følgende URL-adresser" på Microsoft 365 Defender-portalen

> [!NOTE]
> Du kan nu administrere blokerings-URL-adresser på [listen over tilladte/blokerede lejere](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list). Listen "Bloker følgende URL-adresser" frarådes. Vi forsøger at overføre eksisterende poster fra listen "Bloker følgende URL-adresser" for at blokere URL-adresser på listen over tilladte/blokerede lejere. Meddelelser, der indeholder den blokerede URL-adresse, sættes i karantæne.

Listen **Bloker følgende URL-adresser** identificerer de links, der altid skal blokeres af scanning af sikre links i understøttede apps. Du kan få flere oplysninger på [listen "Bloker følgende URL-adresser" for Sikre links](safe-links.md#block-the-following-urls-list-for-safe-links).

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

2. Klik på **Globale indstillinger** på siden **Sikre links**. I den viste **politik for sikre links for din organisation** skal du gå til feltet **Bloker følgende URL-adresser** .

3. Konfigurer en eller flere poster som beskrevet i [Postsyntaks for listen "Bloker følgende URL-adresser"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

   Klik på **Gem**, når du er færdig.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>Konfigurer listen "Bloker følgende URL-adresser" i PowerShell

Du kan finde flere oplysninger om syntaksen for [indtastningen i Postsyntaks for listen "Bloker følgende URL-adresser"](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

Du kan bruge **Get-AtpPolicyForO365-cmdlet'en** til at få vist eksisterende poster i egenskaben _BlockURLs_ .

- Hvis du vil tilføje værdier, der erstatter eksisterende poster, skal du bruge følgende syntaks i Exchange Online PowerShell eller Exchange Online Protection PowerShell:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  I dette eksempel føjes følgende poster til listen:

  - Bloker domænet, underdomænerne og stierne til fabrikam.com.
  - Bloker opslag i underdomænet, men ikke det overordnede domæne eller andre underdomæner i tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Hvis du vil tilføje eller fjerne værdier, uden at det påvirker andre eksisterende poster, skal du bruge følgende syntaks:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  Dette eksempel tilføjer en ny post for adatum.com og fjerner posten for fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>Konfigurer beskyttelse af sikre links for Office 365 apps på Microsoft 365 Defender-portalen

Beskyttelse af sikre links til Office 365 apps gælder for dokumenter i understøttede Office-skrivebords-, mobil- og webapps. Du kan få flere oplysninger under [Indstillinger for sikre links for Office 365 apps](safe-links.md#safe-links-settings-for-office-365-apps).

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Sikre links** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Sikre links** , skal du bruge <https://security.microsoft.com/safelinksv2>.

2. Klik på **Globale indstillinger** på siden **Sikre links**. I den **viste politik for sikre links for din organisation** skal du konfigurere følgende indstillinger i afsnittet **Indstillinger, der gælder for indhold i understøttede Office 365 apps**:

   - **Brug Sikre links i Office 365 apps**: Kontrollér, at til/fra-knappen er til højre for at aktivere Sikre links for understøttede Office 365 apps: ![Slå til.](../../media/scc-toggle-on.png).

   - **Spor ikke, når brugere klikker på beskyttede links i Office 365 apps**: Flyt til/fra-knappen til venstre for at spore bruger klik, der er relateret til blokerede URL-adresser i understøttede Office 365 apps: ![Slå til/fra.](../../media/scc-toggle-off.png).

   - **Lad ikke brugere klikke sig igennem til den oprindelige URL-adresse i Office 365 apps**: Kontrollér, at til/fra-knappen er til højre for at forhindre brugere i at klikke sig igennem til den oprindelige blokerede URL-adresse i understøttede Office 365 apps: ![Slå til.](../../media/scc-toggle-on.png).

   Klik på **Gem**, når du er færdig.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>Konfigurer sikker links-beskyttelse for Office 365 apps i PowerShell

Hvis du hellere vil bruge PowerShell til at konfigurere Safe Links-beskyttelse for Office 365 apps, skal du bruge følgende syntaks i Exchange Online PowerShell eller Exchange Online Protection PowerShell:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

I dette eksempel konfigureres følgende indstillinger for beskyttelse af sikre links i Office 365 apps:

- Sikre links for Office 365 apps er slået til (vi bruger ikke parameteren _EnableSafeLinksForO365Clients_, og standardværdien er $true).
- Bruger klik relateret til blokerede URL-adresser i understøttede Office 365 apps spores.
- Brugerne har ikke tilladelse til at klikke sig igennem til den oprindelige blokerede URL-adresse i understøttede Office 365 apps (vi bruger ikke parameteren _AllowClickThrough_, og standardværdien er $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Du kan finde detaljerede oplysninger om syntaks og parametre [under Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har konfigureret de globale indstillinger for Sikre links (listen **Bloker følgende URL-adresser** og indstillingerne for Office 365 appbeskyttelse):

- Klik på **Globale indstillinger** på siden **Sikre links** på Microsoft 365 Defender-portalen på <https://security.microsoft.com/safelinksv2>, og kontrollér indstillingerne i det viste fly.

- I Exchange Online PowerShell eller Exchange Online Protection PowerShell skal du køre følgende kommando og kontrollere indstillingerne:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Du kan finde detaljerede oplysninger om syntaks og parametre [under Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
