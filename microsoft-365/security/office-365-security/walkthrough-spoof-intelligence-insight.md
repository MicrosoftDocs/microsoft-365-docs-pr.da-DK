---
title: Administrer spoofed afsendere ved hjælp af spoof intelligence-politikken og indsigt i spoof intelligence
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om, hvordan de bruger spoof intelligence-politikken og indsigt i spoof intelligence til at tillade eller blokere registrerede spoofed-afsendere.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 66253ed6deab0f41cac3a4ff732201e20d100e98
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65771991"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Administrer spoofed afsendere ved hjælp af spoof intelligence-politikken og indsigt i spoof intelligence i EOP

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Administration af spoofed-afsender på Microsoft 365 Defender-portalen er nu kun tilgængelig på fanen **Spoofing** på listen over tilladte/blokerede lejere. Du kan se aktuelle procedurer på Microsoft 365 Defender-portalen [under Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md).
>
> Administration af spoofed-afsender i Exchange Online PowerShell eller enkeltstående EOP PowerShell er ved at blive overført udelukkende til de relaterede **\*-TenantAllowBlockListSpoofItems**, **Get-SpoofIntelligenceInsight** og **Get-SpoofMailReport-cmdlet'er**. Du kan se procedurer for brug af disse cmdlet'er i følgende artikler:
>
> - [Vis spoofed afsenderposter ved hjælp af PowerShell](tenant-allow-block-list.md#view-spoofed-sender-entries)
> - [Tilføj tilladte poster for spoofed afsender ved hjælp af PowerShell](manage-tenant-allows.md#add-spoofed-sender-allow-entries-using-powershell)
> - [Tilføj spoofed afsenderblokposter ved hjælp af PowerShell](manage-tenant-blocks.md#add-spoofed-sender-block-entries)
> - [Rediger spoofed afsenderposter ved hjælp af PowerShell](modify-remove-entries-tenant-allow-block.md#modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
> - [Fjern spoofed afsenderposter ved hjælp af PowerShell](modify-remove-entries-tenant-allow-block.md#remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
>
> Den ældre spoofed afsenderadministrationsoplevelse ved hjælp af **Get-PhishFilterPolicy** - og **Set-PhishFilterPolicy-cmdlet'erne** frarådes, men præsenteres stadig i denne artikel for fuldførelse, indtil cmdlet'erne fjernes overalt.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre spoof intelligence-politikken eller aktivere eller deaktivere spoof intelligence, skal du være medlem af:
    - **Organisationsadministration**
    - **Konfiguration af sikkerhedsadministrator** <u>og</u> kun **visning** eller **kun visning af organisationsadministration**.
  - Hvis du vil have skrivebeskyttet adgang til spoof intelligence-politikken, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Indstillingerne for spoof intelligence er beskrevet i [Spoof-indstillinger i anti-phishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

- Du kan aktivere, deaktivere og konfigurere spoof intelligence-indstillingerne i politikker til bekæmpelse af phishing. Du kan finde instruktioner baseret på dit abonnement i et af følgende emner:

  - [Konfigurer politikker til bekæmpelse af phishing i EOP](configure-anti-phishing-policies-eop.md).
  - [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

- Du kan se vores anbefalede indstillinger for spoof intelligence under [EOP-politikindstillinger for anti-phishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="use-powershell-to-manage-spoofed-senders"></a>Brug PowerShell til at administrere forfalskede afsendere

Hvis du vil have vist tilladte og blokerede afsendere i spoof intelligence, skal du bruge følgende syntaks:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

I dette eksempel returneres detaljerede oplysninger om alle afsendere, der har tilladelse til at spoof-brugere i dine domæner.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Hvis du vil konfigurere tilladte og blokerede afsendere i spoof intelligence, skal du følge disse trin:

1. Hent den aktuelle liste over registrerede spoofede afsendere ved at skrive outputtet fra **Get-PhishFilterPolicy-cmdlet'en** til en CSV-fil ved at køre følgende kommando:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Rediger CSV-filen for at tilføje eller ændre følgende værdier:
   - **Afsender** (domæne i kildeserverens PTR-post, IP/24-adresse eller bekræftet DKIM-domæne)
   - **SpoofedUser**: En af følgende værdier:
     - Den interne brugers mailadresse.
     - Den eksterne brugers maildomæne.
     - En tom værdi, der angiver, at du vil blokere eller tillade alle spoofede meddelelser fra den angivne **afsender**, uanset den spoofede mailadresse.
   - **AllowedToSpoof** (Ja eller Nej)
   - **SpoofType** (intern eller ekstern)

   Gem filen, læs filen, og gem indholdet som en variabel med navnet `$UpdateSpoofedSenders` ved at køre følgende kommando:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Brug variablen `$UpdateSpoofedSenders` til at konfigurere spoof intelligence-politikken ved at køre følgende kommando:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Hvis du vil bekræfte, at du har konfigureret spoof intelligence med afsendere, der har tilladelse og ikke har tilladelse til at spoof, skal du køre følgende kommandoer i PowerShell for at få vist de afsendere, der har tilladelse til at spoof:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- I PowerShell skal du køre følgende kommando for at eksportere listen over alle misvisende afsendere til en CSV-fil:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
