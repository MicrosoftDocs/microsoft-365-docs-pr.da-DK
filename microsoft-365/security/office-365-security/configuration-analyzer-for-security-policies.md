---
title: Konfigurationsanalyse til sikkerhedspolitikker
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan få mere at vide om, hvordan de bruger konfigurationsanalysen til at finde og rette sikkerhedspolitikker, der er under indstillingerne i Standardbeskyttelse og Begrænset beskyttelse i foruddefinerede sikkerhedspolitikker.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0acdf6d300984c00bb1b1b060d3e36562983ebca
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63590917"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>Konfigurationsanalyse til beskyttelsespolitikker i EOP og Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Konfigurationsanalyse i Microsoft 365 Defender-portalen udgør et centralt sted til at finde og rette sikkerhedspolitikker, hvor indstillingerne er under standardbeskyttelses- og strengbeskyttelsesprofilindstillingerne i foruddefinerede [sikkerhedspolitikker](preset-security-policies.md).

Følgende typer politikker analyseres af konfigurationsanalysen:

- **Exchange Online Protection (EOP)**-politikker: Dette omfatter Microsoft 365 organisationer med Exchange Online-postkasser og enkeltstående EOP-organisationer uden Exchange Online postkasser:
  - [Antispam-politikker](configure-your-spam-filter-policies.md).
  - [Antimalwarepolitikker](configure-anti-malware-policies.md).
  - [EOP-antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

- **Microsoft Defender til Office 365 politikker**: Dette omfatter organisationer med Microsoft 365 E5 eller Defender Office 365-tilføjelsesabonnementer:
  - Antiphishing-politikker i Microsoft Defender til Office 365, som omfatter:
    - De samme [spoof-indstillinger,](set-up-anti-phishing-policies.md#spoof-settings) der er tilgængelige i EOP-antiphishing-politikkerne.
    - [Indstillinger for repræsentation](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Avancerede grænseværdier for phishing](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Pengeskab links-politikker](set-up-safe-links-policies.md).
  - [Pengeskab politikker for vedhæftede filer](set-up-safe-attachments-policies.md).

De standard- og restriktive politikindstillingsværdier, der bruges som grundlinjer, er beskrevet i Anbefalede indstillinger [for EOP og Microsoft Defender Office 365 sikkerhed](recommended-settings-for-eop-and-office365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Configuration analyzer skal** du bruge <https://security.microsoft.com/configurationAnalyzer>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser i Microsoft 365 Defender, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil bruge **konfigurationsanalysen** og foretage opdateringer til sikkerhedspolitikker, skal du være medlem af **rollegrupperne** Organisationsadministration **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til konfigurationsanalyse skal du være medlem af **rollegrupperne Global læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - Når brugere føjes til den Azure Active Directory rolle, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  > - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

## <a name="use-the-configuration-analyzer-in-the-microsoft-365-defender-portal"></a>Brug konfigurationsanalyse i Microsoft 365 Defender portal

I  portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til Mail **& samarbejdspolitikker** \> **& Regler** \> \> for trusselspolitikker **Konfigurationsanalyse** i **sektionen Skabelonerede** politikker. For at gå direkte til **siden Configuration analyzer skal** du bruge <https://security.microsoft.com/configurationAnalyzer>.

Siden **Konfigurationsanalyse** har tre hovedfaner:

- **Standardanbefalinger**: Sammenlign dine eksisterende sikkerhedspolitikker med Standardanbefalinger. Du kan justere dine indstillinger for at få dem op på samme niveau som Standard.
- **Strenge anbefalinger**: Sammenlign dine eksisterende sikkerhedspolitikker med anbefalingerne fra Strict. Du kan justere dine indstillingsværdier, så de kommer op på det samme niveau som Streng.
- **Analyse og historik for konfigurationsændringer**: Overvågning og registrer ændringer af politikker over tid.

### <a name="standard-recommendations-and-strict-recommendations-tabs-in-the-configuration-analyzer"></a>Standardanbefalinger og fanerne Strenge anbefalinger i konfigurationsanalyse

Som standard åbnes konfigurationsanalysen under **fanen Standardanbefalinger** . Du kan skifte til **fanen Restriktive** anbefalinger. Indstillingerne, layoutet og handlingerne er de samme på begge faner.

![Indstillinger og anbefalinger i Konfigurationsanalyse.](../../media/configuration-analyzer-settings-and-recommendations-view.png)

Den første del af fanen viser antallet af indstillinger i hver type politik, der skal forbedres i forhold til Standard eller Streng beskyttelse. Typerne af politikker er:

- **Antispam**
- **Antiphishing**
- **Antimalware**
- **Pengeskab vedhæftede filer** (hvis dit abonnement omfatter Microsoft Defender til Office 365)
- **Pengeskab Links** (hvis dit abonnement omfatter Microsoft Defender til Office 365)

Hvis en politiktype og et tal ikke vises, opfylder alle dine politikker af den pågældende type de anbefalede indstillinger for Standard eller Restriktiv beskyttelse.

Resten af fanen er tabellen over indstillinger, der skal være op til niveauet Standard eller Streng beskyttelse. Tabellen indeholder følgende kolonner:

- **Anbefalinger**: Værdien af indstillingen i standard- eller strengbeskyttelsesprofilen.
- **Politik**: Navnet på den berørte politik, der indeholder indstillingen.
- **Gruppe-/indstillingsnavn**: Navnet på den indstilling, der kræver din opmærksomhed.
- **Politiktype**: Antispam, antiphishing, antimalware, Pengeskab links eller Pengeskab vedhæftede filer.
- **Aktuel konfiguration**: Den aktuelle værdi af indstillingen.
- **Senest ændret**: Den dato, hvor politikken sidst blev ændret.
- **Status**: Typisk er denne værdi **Ikke startet**.

### <a name="change-a-policy-setting-to-the-recommended-value"></a>Ændre en politikindstilling til den anbefalede værdi

På fanen **Standardbeskyttelse** **eller Streng beskyttelse** i konfigurationsanalysen skal du markere rækken i tabellen. Følgende knapper vises:

- **Anvend anbefaling**
- **Vis politik**
- **Opdater**:

Hvis du markerer en række og **klikker på Anvend anbefaling**, vises en bekræftelsesdialogboks (med mulighed for ikke at vise dialogboksen igen). Hvis du klikker **på OK**, sker følgende:

- Indstillingen opdateres til den anbefalede værdi.
- Politikken **Anvend og** Vis **forsvinder** (kun knappen **Opdater** forbliver).
- **Statusværdien** for rækken ændres til **Fuldført**.

Hvis du vælger en række og klikker  på Vis politik, kommer du til pop op-dialogboksen med oplysninger om den pågældende politik i Microsoft 365 Defender-portalen, hvor du kan opdatere indstillingen manuelt.

Når du opdaterer indstillingen automatisk eller manuelt, skal du  klikke på Opdater for at se det reducerede antal anbefalinger og fjerne den opdaterede række fra resultaterne.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Analyse af konfigurationsstabulering og fanen Historik i konfigurationsanalyse

Denne fane giver dig mulighed for at registrere de ændringer, der er foretaget i dine sikkerhedspolitikker, og hvordan disse ændringer sammenlignes med Standard- eller Restriktive indstillinger. Følgende oplysninger vises som standard:

- **Senest ændret**
- **Ændret af**
- **Indstillingsnavn**
- **Politik**: Navnet på den pågældende politik.
- **Type**: Antispam, antiphishing, antimalware, Pengeskab links eller Pengeskab vedhæftede filer.
- **Konfigurationsændring**: Den gamle værdi og den nye værdi for indstillingen
- **Konfigurationssletning**: **Den værdi Forøg** eller Formindsk, der angiver, at indstillingen øger eller formindsker sikkerhed sammenlignet med den anbefalede Standard- eller Streng-indstilling.

Hvis du vil filtrere resultaterne, skal du klikke **på Filtrer**. I pop **op-dialogboksen** Filtre, der vises, kan du vælge mellem følgende filtre:

- **Start-** og **sluttidspunktet** (dato): Du kan gå tilbage så langt som 90 dage fra i dag.
- **Standardbeskyttelse** eller **restriktiv beskyttelse**

Klik på Anvend, når du er **færdig**.

Hvis du vil eksportere resultaterne til en .csv, skal du klikke på **Eksportér**.

Hvis du vil filtrere resultaterne efter en bestemt **værdi af Ændret** af, **Indstillingsnavn** **eller Type** , skal du bruge **feltet** Søg.

![Analyse af konfigurationssyde og oversigtsvisning i Konfigurationsanalyse.](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
