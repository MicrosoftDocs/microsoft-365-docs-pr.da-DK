---
title: Pengeskab dokumenter i Microsoft Defender for Office 365
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Få mere at vide Pengeskab dokumenter i Microsoft 365 E5/A5 eller Microsoft 365 E5/A5 Security.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab5e35954cac20a18e34f418b5b9fcdc7f2fd007
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466339"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>Pengeskab dokumenter i Microsoft 365 E5/A5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pengeskab Dokumenter er en premium-funktion, der bruger cloud-back-enden [af Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) til at scanne åbnede Office-dokumenter i [Beskyttet](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) visning eller [Application Guard for at Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

Brugere behøver ikke Defender til Slutpunkt installeret på deres lokale enheder for at få Pengeskab Dokumenter beskyttelse. Brugerne får Pengeskab-dokumentbeskyttelse, hvis alle følgende krav er opfyldt:

- Pengeskab dokumenter er aktiveret i organisationen som beskrevet i denne artikel.
- Licenser fra en påkrævet licensplan tildeles til brugerne. Pengeskab dokumenter styres af **serviceplanen Office 365 SafeDocs** (eller **SAFEDOCS** eller **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (også kaldet en tjeneste). Denne serviceaftale er tilgængelig i følgende licensplaner (også kaldet licensplaner, Microsoft 365 abonnementer eller produkter):
  - Microsoft 365 A5 til fakultetsmedarbejdere
  - Microsoft 365 A5 for studerende
  - Microsoft 365 E5
  - Microsoft 365 E5 Sikkerhed

  Pengeskab dokumenter er ikke inkluderet i Microsoft Defender for Office 365 licensplaner.

  Du kan finde flere oplysninger under [Produktnavne og serviceplanidentifikatorer til licenser](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- De bruger en Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus) version 2004 eller nyere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du Pengeskab konfigurere indstillingerne for Dokumenter, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator**.
  - For at få skrivebeskyttet adgang til Pengeskab-dokumentindstillinger skal du være medlem af **rollegrupperne Global læser** **eller Sikkerhedslæser**.

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

### <a name="how-does-microsoft-handle-your-data"></a>Hvordan håndterer Microsoft dine data?

For at holde dig beskyttet skal Pengeskab dokumenter sende filer til skyen [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) til analyse. Oplysninger om, hvordan Microsoft Defender for Endpoint håndterer dine data, kan findes her: Microsoft Defender for Endpoint [datalagring og beskyttelse af personlige oplysninger](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Filer, der Pengeskab dokumenter, bevares ikke i Defender til slutpunkt ud over den tid, der er brug for analyse (typisk mindre end 24 timer).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Brug portalen Microsoft 365 Defender til at konfigurere Pengeskab dokumenter

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til & politikker  \> for samarbejde **&** **regler** \> \> **for trussel Pengeskab** Vedhæftede filer i **sektionen** Politikker. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. Klik på **Pengeskab globale indstillinger** på siden **Vedhæftede filer**.

3. I pop **op-menuen** Globale indstillinger, der vises, skal du konfigurere følgende indstillinger:
   - **Aktiver Pengeskab dokumenter for Office** klienter: Flyt til/fra-knappen til højre for at slå funktionen til: ![Til/fra.](../../media/scc-toggle-on.png).
   - **Tillad brugere** at klikke gennem Beskyttet visning, selvom Pengeskab Dokumenter identificeret filen som skadelig: Vi anbefaler, at du lader denne indstilling være deaktiveret (lad til/fra-knappen være til venstre: ![Slå fra.](../../media/scc-toggle-off.png)).

   Klik på **Gem**, når du er færdig.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Dialogboksen Pengeskab Dokumenter, når du har valgt Globale indstillinger på siden Pengeskab vedhæftede filer" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Brug Exchange Online PowerShell til at konfigurere Pengeskab dokumenter

Hvis du hellere vil bruge PowerShell til at konfigurere Pengeskab dokumenter, skal du bruge følgende syntaks i Exchange Online PowerShell:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- _Parameteren EnableSafeDocs_ aktiverer eller deaktiverer Pengeskab Dokumenter for hele organisationen.
- _Parameteren AllowSafeDocsOpen_ tillader eller forhindrer brugere i at forlade beskyttet visning (dvs. åbning af dokumentet), hvis dokumentet er identificeret som skadeligt.

Dette eksempel aktiverer Pengeskab dokumenter for hele organisationen og forhindrer brugere i at åbne dokumenter, der er identificeret som skadelige fra Beskyttet visning.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Konfigurere individuel adgang til Pengeskab dokumenter

Hvis du selektivt vil tillade eller blokere adgangen til Pengeskab dokumenter, skal du følge disse trin:

1. Aktiver Pengeskab Dokumenter i Microsoft 365 Defender eller PowerShell Exchange Online som beskrevet tidligere i denne artikel.
2. Brug Azure AD PowerShell til at deaktivere Pengeskab-dokumenter for bestemte brugere som beskrevet i [Deaktiver bestemte Microsoft 365-tjenester for bestemte brugere i en bestemt licensplan](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  Navnet på den serviceplan, der skal deaktiveres i PowerShell, **er SAFEDOCS**.

Du kan finde flere oplysninger i følgende emner:

- [Få Microsoft 365 licenser og tjenester med PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Vis Microsoft 365-kontolicens og serviceoplysninger med PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Produktnavne og serviceabonnement-id'er til licenser](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Onboard to the Microsoft Defender for Endpoint for at aktivere overvågningsfunktioner

Hvis du vil aktivere overvågningsfunktioner, skal den lokale enhed have Microsoft Defender for Endpoint installeret. For at Microsoft Defender for Endpoint installationen skal du gennemgå de forskellige implementeringsfaser. Efter onboarding kan du konfigurere overvågningsfunktioner i Microsoft 365 Defender portal.

Du kan få mere at [vide under Onboard to Microsoft Defender for Endpoint service](/microsoft-365/security/defender-endpoint/onboarding). Hvis du har brug for yderligere hjælp, kan du [se Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Hvordan gør jeg du, at det lykkedes?

For at bekræfte, at du har aktiveret og konfigureret Pengeskab dokumenter, skal du gøre et af følgende:

- I Microsoft 365 Defender-portalen  \> skal du gå til Politikker & samarbejde  via mail **&** \>  \> Regler om trusler **Pengeskab** \> Vedhæftede filer i sektionen Globale **indstillinger og kontrollere** Aktivere **Pengeskab-dokumenter for Office-klienter** **og Tillad brugere at klikke gennem Beskyttet visning, selvom Pengeskab dokumenter identificerer filen som skadelige** indstillinger.

- Kør følgende kommando i Exchange Online PowerShell, og bekræft egenskabsværdierne:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Følgende filer kan testes Pengeskab dokumentbeskyttelse. Disse filer ligner den EICAR.TXT til test af antimalware og antivirusløsninger. Filerne er ikke skadelige, men de udløser Pengeskab dokumentbeskyttelse.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
