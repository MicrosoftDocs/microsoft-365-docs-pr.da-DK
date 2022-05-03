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
description: Få mere at vide om Pengeskab dokumenter i Microsoft 365 E5/A5 eller Microsoft 365 E5/A5 Security.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3fa1c7e07c1e1cd117ee20f4712dbbadad3c2b5c
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174137"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>Pengeskab dokumenter i Microsoft 365 E5/A5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Pengeskab Dokumenter er en Premium-funktion, der bruger cloudbackend af [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) til at scanne åbne Office dokumenter i [beskyttet visning](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) eller [Application Guard for Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

Brugerne behøver ikke at have Defender for Endpoint installeret på deres lokale enheder for at få beskyttelse Pengeskab dokumenter. Brugerne får Pengeskab dokumentbeskyttelse, hvis alle følgende krav er opfyldt:

- Pengeskab Dokumenter er aktiveret i organisationen som beskrevet i denne artikel.
- Licenser fra en påkrævet licensplan tildeles til brugerne. Pengeskab Dokumenter styres af **serviceplanen Office 365 SafeDocs** (eller **SAFEDOCS** eller **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (også kendt som en tjeneste). Denne serviceplan er tilgængelig i følgende licensplaner (også kendt som licensplaner, Microsoft 365 planer eller produkter):
  - Microsoft 365 A5 for fakultetsansatte
  - Microsoft 365 A5 til studerende
  - Microsoft 365 E5 Sikkerhed

  Pengeskab Dokumenter er ikke inkluderet i Microsoft Defender for Office 365 licensplaner.

  Du kan få flere oplysninger under [Produktnavne og tjenesteplan-id'er for licenser](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- De bruger Microsoft 365 Apps for enterprise (tidligere kaldet Office 365 ProPlus) version 2004 eller nyere.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Pengeskab Vedhæftede filer**, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil konfigurere Pengeskab dokumentindstillinger, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator**.
  - Hvis du vil have skrivebeskyttet adgang til Pengeskab dokumentindstillinger, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser**.

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  >
  > - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

### <a name="how-does-microsoft-handle-your-data"></a>Hvordan håndterer Microsoft dine data?

For at holde dig beskyttet sender Pengeskab dokumenter filer til [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) cloudmiljøet til analyse. Du kan finde oplysninger om, hvordan Microsoft Defender for Endpoint håndterer dine data, her: [Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Filer, der sendes af Pengeskab dokumenter, bevares ikke i Defender for Endpoint ud over den tid, der kræves til analysen (typisk mindre end 24 timer).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Brug Microsoft 365 Defender-portalen til at konfigurere Pengeskab dokumenter

1. På portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Pengeskab Vedhæftede filer** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Pengeskab Vedhæftede filer**, skal du bruge <https://security.microsoft.com/safeattachmentv2>.

2. Klik på **Globale indstillinger** på siden **Pengeskab Vedhæftede filer**.

3. Konfigurer følgende indstillinger i de **globale indstillinger** , der vises:
   - **Slå Pengeskab dokumenter til for Office klienter**: Flyt til/fra-knappen til højre for at aktivere funktionen: ![Slå til.](../../media/scc-toggle-on.png).
   - **Tillad, at andre klikker gennem beskyttet visning, selvom Pengeskab dokumenter har identificeret filen som skadelig**: Vi anbefaler, at du lader denne indstilling være slået fra (lad til/fra-knappen til venstre: ![Slå til/fra](../../media/scc-toggle-off.png)).

   Klik på **Gem**, når du er færdig.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Indstillingerne for Pengeskab dokumenter, når du har valgt Globale indstillinger på siden Pengeskab vedhæftede filer" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Brug Exchange Online PowerShell til at konfigurere dokumenter Pengeskab

Hvis du hellere vil bruge PowerShell til at konfigurere Pengeskab dokumenter, skal du bruge følgende syntaks i Exchange Online PowerShell:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Parameteren _EnableSafeDocs_ aktiverer eller deaktiverer Pengeskab dokumenter for hele organisationen.
- Parameteren _AllowSafeDocsOpen_ tillader eller forhindrer brugere i at forlade beskyttet visning (dvs. åbne dokumentet), hvis dokumentet er blevet identificeret som skadeligt.

Dette eksempel aktiverer Pengeskab dokumenter for hele organisationen og forhindrer brugerne i at åbne dokumenter, der er blevet identificeret som skadelige fra beskyttet visning.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Du kan finde detaljerede oplysninger om syntaks og parametre [under Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Konfigurer individuel adgang til Pengeskab dokumenter

Hvis du selektivt vil tillade eller blokere adgang til funktionen Pengeskab dokumenter, skal du følge disse trin:

1. Slå Pengeskab dokumenter til på Microsoft 365 Defender-portalen eller Exchange Online PowerShell som tidligere beskrevet i denne artikel.
2. Brug Azure AD PowerShell til at deaktivere Pengeskab dokumenter for bestemte brugere som beskrevet i [Deaktiver specifikke Microsoft 365-tjenester for bestemte brugere for en bestemt licensplan](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  Navnet på den tjenesteplan, der skal deaktiveres i PowerShell, er **SAFEDOCS**.

Du kan få flere oplysninger i følgende emner:

- [Få vist Microsoft 365 licenser og tjenester med PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Få vist oplysninger om Microsoft 365-kontolicens og -tjeneste med PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Produktnavne og tjenesteplan-id'er for licensering](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Onboard til Microsoft Defender for Endpoint-tjenesten for at aktivere overvågningsfunktioner

Hvis du vil aktivere overvågningsfunktioner, skal Microsoft Defender for Endpoint være installeret på den lokale enhed. Hvis du vil udrulle Microsoft Defender for Endpoint, skal du gennemgå de forskellige udrulningsfaser. Når du har onboardet, kan du konfigurere overvågningsfunktioner på portalen Microsoft 365 Defender.

Du kan få mere [at vide under Onboard to the Microsoft Defender for Endpoint service](/microsoft-365/security/defender-endpoint/onboarding). Hvis du har brug for yderligere hjælp, kan du se [Fejlfinding af Microsoft Defender for Endpoint problemer med onboarding](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Hvordan gør jeg ved, det virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har aktiveret og konfigureret Pengeskab dokumenter:

- På Microsoft 365 Defender-portalen skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Pengeskab Vedhæftede filer** i afsnittet \> **Politikker** **Globale indstillinger**, og kontrollere **Slå Pengeskab dokumenter til for Office klienter** og **Tillad, at personer klikker gennem beskyttet visning, selvom Pengeskab dokumenter identificerer filen som skadelige** indstillinger.

- Kør følgende kommando i Exchange Online PowerShell, og kontrollér egenskabsværdierne:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Følgende filer er tilgængelige til test Pengeskab dokumentbeskyttelse. Disse filer ligner EICAR.TXT-filen til test af antimalware- og antivirusløsninger. Filerne er ikke skadelige, men de udløser Pengeskab dokumentbeskyttelse.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
