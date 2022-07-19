---
title: Konfigurer og gennemse prioritetskonti i Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 3/21/2022
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Få mere at vide om, hvordan du identificerer kritiske personer i en organisation og tilføjer prioritetskontomærket for at give dem ekstra beskyttelse.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 466061562ba0ccc1a33a9fe6ca58073196f4f7e0
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858851"
---
# <a name="configure-and-review-priority-accounts-in-microsoft-defender-for-office-365"></a>Konfigurer og gennemse prioritetskonti i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I alle organisationer er der personer, der er kritiske, f.eks. direktører, ledere, ledere eller andre brugere, der har adgang til følsomme, beskyttede oplysninger eller oplysninger med høj prioritet. Du kan mærke disse brugere i Microsoft Defender for Office 365 som prioriterede konti, så sikkerhedsteams kan prioritere deres fokus på disse kritiske personer. Med differentieret beskyttelse af prioritetskonti modtager brugere, der er mærket som prioriterede konti, et højere niveau af beskyttelse mod trusler.

Prioriterede konti målrettes oftere af hackere og angribes generelt med mere avancerede teknikker. Differentieret beskyttelse af prioriterede konti fokuserer på dette specifikke brugersæt og giver et højere niveau af beskyttelse ved hjælp af forbedrede modeller til maskinel indlæring. Denne differentiering i lærings- og meddelelseshåndtering giver den højeste beskyttelse af disse konti og hjælper med at opretholde en lav falsk positiv rate, da en høj forekomst af falske positiver også kan have en negativ indvirkning på disse brugere.

## <a name="configure-priority-account-protection"></a>Konfigurer beskyttelse af prioritetskonto

Prioritetskontobeskyttelse er som standard slået til for forhåndsidentificerede kritiske brugere. Sikkerhedsadministratoren i din organisation kan dog også aktivere prioritetsbeskyttelse af kontoen ved at følge disse trin:

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Indstillinger** \> **Mail & samarbejde** \> **Prioritet til kontobeskyttelse**. Hvis du vil gå direkte til siden **Prioritetskontobeskyttelse** , skal du bruge <https://security.microsoft.com/securitysettings/priorityAccountProtection>.

2. På siden **Prioritetskontobeskyttelse** skal du aktivere **Prioritetskontobeskyttelse** (:::image type="icon" source="../../media/scc-toggle-on.png" border="false":::).

    > [!div class="mx-imgBorder"]
    > ![Slå prioritetskontobeskyttelse til.](../../media/mdo-priority-account-protection.png)

> [!NOTE]
> Vi anbefaler ikke, at du deaktiverer eller deaktiverer prioritetskontobeskyttelse.

Hvis du vil bruge Exchange Online PowerShell til at aktivere prioritetskontobeskyttelse, skal du gøre følgende:

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), og kør følgende kommando:

   ```powershell
   Set-EmailTenantSettings -EnablePriorityAccountProtection $true
   ```

2. Hvis du vil kontrollere, at beskyttelse af prioritetskonti er slået til, skal du køre følgende kommando for at bekræfte egenskabsværdien EnablePriorityAccountProtection:

   ```powershell
   Get-EmailTenantSettings | Format-List Identity,EnablePriorityAccountProtection
   ```

   Værdien Sand betyder, at prioritetskontobeskyttelse er slået til. Værdien False betyder, at prioritetskontobeskyttelse er deaktiveret.

### <a name="assign-the-priority-account-tag-to-users"></a>Tildel kontomærket Prioritet til brugere

Microsoft Defender for Office 365 understøtter prioritetskonti som mærker, der kan bruges som filtre i beskeder, rapporter, hændelser og meget mere.

Du kan få flere oplysninger [under Brugerkoder i Microsoft Defender for Office 365](user-tags.md).

## <a name="review-differentiated-protection-from-priority-account-protection"></a>Gennemgå differentieret beskyttelse fra prioriteret kontobeskyttelse

Indvirkningen af prioritetskontobeskyttelse er synlige i følgende funktioner:

- [Beskeder](alerts.md)
- [Brugerdefinerede beskedpolitikker](../../compliance/alert-policies.md#viewing-alerts)
- [Trusselsoversigt og registreringer i realtid](threat-explorer.md)
- [Kompromitteret brugerrapport](view-email-security-reports.md#compromised-users-report)
- [Mailobjektside](mdo-email-entity-page.md#other-innovations)
- [Statusrapport om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
- [Rapport over de vigtigste afsendere og modtagere](view-email-security-reports.md#top-senders-and-recipients-report)
- [Simulering af angreb](attack-simulation-training.md#target-users)
- [Kampagnevisninger](campaigns.md)
- [Administration og brugerindsendelser](admin-submission.md)
- [Karantæne](quarantine.md)

### <a name="threat-protection-status-report"></a>Statusrapport om trusselsbeskyttelse

**Statusrapporten trusselsbeskyttelse** er en enkelt visning, der samler oplysninger om skadeligt indhold og skadelig mail, der er registreret og blokeret af Microsoft Defender for Office 365.

Benyt følgende fremgangsmåde for at få vist rapporten:

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail i rapporter** \> **& samarbejde** \> **Mail & samarbejdsrapporter** \> find **Status for trusselsbeskyttelse**, og klik derefter på **Vis detaljer**. Hvis du vil gå direkte til rapporten, skal du bruge <https://security.microsoft.com/reports/TPSAggregateReportATP>.

2. Standardvisningen er **Vis data efter Oversigt**. Klik på denne værdi for at ændre visningen ved at vælge en af følgende værdier:
   - **Få vist data via mail-phish \>**
   - **Få vist data via mailmalware \>**
   - **Få vist data via mailspam \>**

3. Klik på ![Filterikon.](../../media/m365-cc-sc-filter-icon.png) **Filter**.

4. I pop op-vinduet **Filtre**, der åbnes, skal du vælge **Ja**, **Nej** eller begge værdier i sektionen **Prioritetskonti**.

   ![Prioritetsfiltre til kontobeskyttelse i statusrapporten trusselsbeskyttelse.](../../media/priority-account-protection-tps-report.png)

### <a name="threat-explorer"></a>Trusselsoversigt

Kontekstfilter i Threat Explorer hjælper med at søge efter mails, hvor prioritetskontobeskyttelse var involveret i registrering af meddelelsen. Dette gør det muligt for sikkerhedsteams at se den værdi, der leveres af denne beskyttelse. Du kan stadig filtrere meddelelser efter prioritetskontomærke for at finde alle meddelelser for det specifikke sæt brugere.

Benyt følgende fremgangsmåde for at få vist den ekstra beskyttelse i Threat Explorer:

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail &** **Samarbejdsstifinder**\>. Hvis du vil gå direkte til siden **Threat Explorer** , skal du bruge <https://security.microsoft.com/threatexplorer>.

2. Vælg **Kontekst** på rullelisten, og markér derefter afkrydsningsfeltet ud for **Prioritetskontobeskyttelse**.

> [!div class="mx-imgBorder"]
> ![Kontekstfilter i Threat Explorer.](../../media/threat-explorer-context-filter.png)

### <a name="email-entity-page"></a>Mailobjektside

Mailobjektsiden er tilgængelig i **Threat Explorer**. Vælg emnet for en mail, du er ved at undersøge. Der vises en guldbjælke øverst i mail-pop op-vinduet for den mail. Vælg at få vist den nye side.

Fanerne øverst på objektsiden giver dig mulighed for at undersøge mail effektivt. Klik på fanen **Analyse** . Prioritetskontobeskyttelse er nu angivet under **Oplysninger om trusselsregistrering**.

## <a name="more-information"></a>Flere oplysninger

- [Brugerkoder i Microsoft Defender for Office 365](user-tags.md)
- [Administrer og overvåg prioritetskonti](../../admin/setup/priority-accounts.md)
