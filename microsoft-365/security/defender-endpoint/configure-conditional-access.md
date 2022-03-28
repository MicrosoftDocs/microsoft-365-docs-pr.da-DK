---
title: Konfigurer Betinget adgang i Microsoft Defender til slutpunkt
description: Få mere at vide om de trin, du skal udføre i Intune, Microsoft 365 Defender og Azure for at implementere Betinget adgang
keywords: betinget adgang, betinget, adgang, enhedsrisici, risikoniveau, integration, intune-integration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8706f756b4e8d0ba87a747396e8f7ef71d66460c
ms.sourcegitcommit: c11d4a2b9cb891ba22e16a96cb9d6389f6482459
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63597568"
---
# <a name="configure-conditional-access-in-microsoft-defender-for-endpoint"></a>Konfigurer Betinget adgang i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Dette afsnit fører dig gennem alle de trin, du skal udføre for at implementere Betinget adgang korrekt.

## <a name="before-you-begin"></a>Før du begynder

> [!WARNING]
> Det er vigtigt at bemærke, at registrerede Azure AD-enheder ikke understøttes i dette scenarie.</br>
> Kun tilmeldte Intune-enheder understøttes.

Du skal sikre dig, at alle dine enheder er tilmeldt Intune. Du kan bruge en af følgende indstillinger til at tilmelde enheder i Intune:

- IT-administrator: Du kan finde flere oplysninger om, hvordan du aktiverer [automatisk registrering, Windows Registrering](/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- Slutbruger: Du kan finde flere oplysninger om, hvordan du tilmelder din Windows 10 og Windows 11-enhed i Intune, under Tilmeld din [Windows 10 enhed i Intune](/intune/quickstart-enroll-windows-device)
- Alternativ til slutbruger: Du kan finde flere oplysninger om deltagelse i et Azure AD-domæne under [Sådan: Planlæg din implementering af Azure AD-deltagelse](/azure/active-directory/devices/azureadjoin-plan).

Der er trin, du skal følge i Microsoft 365 Defender, Intune-portalen og Azure AD-portalen.

Det er vigtigt at bemærke de nødvendige roller for at få adgang til disse portaler og implementere Betinget adgang:

- **Microsoft 365 Defender** – Du skal logge på portalen med en global administratorrolle for at aktivere integrationen.
- **Intune** – Du skal logge på portalen med sikkerhedsadministratorrettigheder med administrationstilladelser.
- **Azure AD-portalen** – Du skal logge på som global administrator, sikkerhedsadministrator eller betinget adgangsadministrator.

> [!NOTE]
> Du skal bruge et Microsoft Intune miljø med Intune-administreret og Azure AD-Windows 10 og Windows 11-enheder.

Gør følgende for at aktivere Betinget adgang:

- Trin 1: Slå den Microsoft Intune forbindelse fra Microsoft 365 Defender
- Trin 2: Slå Defender for Endpoint-integration til i Intune
- Trin 3: Opret overholdelsespolitikken i Intune
- Trin 4: Tildel politikken 
- Trin 5: Opret en politik for betinget adgang i Azure AD

### <a name="step-1-turn-on-the-microsoft-intune-connection"></a>Trin 1: Slå den Microsoft Intune forbindelse til

1. I navigationsruden skal du **vælge Indstillinger** \> **Generelt avancerede slutpunkter-funktioner** \>  \>  \> **Microsoft Intune forbindelse**.
2. Slå indstillingen Microsoft Intune til **Til**.
3. Klik **på Gem indstillinger**.

### <a name="step-2-turn-on-the-defender-for-endpoint-integration-in-intune"></a>Trin 2: Slå Defender for Endpoint-integration til i Intune

1. Log på portalen[Azure](https://portal.azure.com).
2. Vælg **Enhedsoverholdelse** \> **Microsoft Defender ATP**.
3. Sæt **Forbind Windows 10.0.15063+ enheder til Microsoft Defender Advanced Threat Protection** **Til**.
4. Klik på **Gem**.

### <a name="step-3-create-the-compliance-policy-in-intune"></a>Trin 3: Opret overholdelsespolitikken i Intune

1. I [Azure-portalen](https://portal.azure.com) skal du **vælge Alle tjenester**, filtrere **på Intune** og vælge **Microsoft Intune**.
2. Vælg **Politikker for enhedsoverholdelse** \> **Opret** \> **politik**.
3. Angiv et **Navn** og **en Beskrivelse**.
4. I **Platform** skal du **Windows 10 og nyere**.
5. I indstillingerne **for Enhedstilstand** skal du **angive Kræv, at enheden er på eller under Enhedstrusselsniveauet** til dit foretrukne niveau:

   - **Sikret**: Dette niveau er det mest sikre. Enheden kan ikke have eksisterende trusler og har stadig adgang til virksomhedens ressourcer. Hvis der bliver fundet nogen trusler, evalueres enheden som ikke-kompatierende.
   - **Lav**: Enheden er kompatibel, hvis der kun findes trusler med lav niveau. Enheder med mellemstor eller høj trusselsniveau er ikke kompatible.
   - **Mellem**: Enheden er kompatibel, hvis de trusler, der findes på enheden, er lave eller mellemstore. Hvis der registreres trusler på højt niveau, bestemmes enheden som ikke-kompatierende.
   - **Høj**: Dette niveau er det mindst sikre og tillader alle trusselsniveauer. Så enheder med høje, mellem eller lave trusler betragtes som kompatible.

6. Vælg **OK** og **Opret for** at gemme ændringerne (og oprette politikken).

### <a name="step-4-assign-the-policy"></a>Trin 4: Tildel politikken

1. I [Azure-portalen](https://portal.azure.com) skal du **vælge Alle tjenester**, filtrere **på Intune** og vælge **Microsoft Intune**.
2. Vælg **Politikker for overholdelse af** \> **enhed** ,> vælg din Politik for overholdelse af regler og standarder for Microsoft Defender til Slutpunkt.
3. Vælg **Opgaver**.
4. Medtag eller udelad dine Azure AD-grupper for at tildele dem politikken.
5. Hvis du vil installere politikken for grupperne, skal du vælge **Gem**. De brugerenheder, som politikken målretter, evalueres for overholdelse af regler og standarder.

### <a name="step-5-create-an-azure-ad-conditional-access-policy"></a>Trin 5: Opret en politik for betinget adgang i Azure AD

1. I [Azure-portalen skal](https://portal.azure.com) du **åbne Azure Active Directory** \> **ny politik for** \> **betinget adgang**.
2. Angiv en politik **Navn**, og vælg **Brugere og grupper**. Brug indstillingerne Medtag eller Udelad for at tilføje dine grupper for politikken, og vælg **Udført**.
3. Vælg **Skyapps**, og vælg, hvilke apps der skal beskyttes. Vælg f.eks **. Vælg apps**, og **vælg Office 365 SharePoint Online** **og Office 365 Exchange Online**. Vælg **Udført** for at gemme ændringerne.

4. Vælg **Betingelser** \> **Klientapps** for at anvende politikken på apps og browsere. Vælg f.eks. **Ja**, og aktivér derefter **browser-** og **mobilapps og skrivebordsklienter**. Vælg **Udført** for at gemme ændringerne.

5. Vælg **Giv for** at anvende Betinget adgang baseret på enhedsoverholdelse. Vælg f.eks. **Giv adgang Kræv** \> **, at en enhed markeres som kompatibel**. Vælg **Vælg** for at gemme ændringerne.

6. Vælg **Aktivér politik** og derefter **Opret for** at gemme ændringerne.

Få mere at vide under [Gennemtving overholdelse af regler for Microsoft Defender til slutpunkt med Betinget adgang i Intune](/intune/advanced-threat-protection).

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-belowfoldlink)
