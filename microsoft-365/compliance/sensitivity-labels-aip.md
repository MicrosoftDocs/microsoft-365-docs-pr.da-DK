---
title: Vælg Microsoft Purview Information Protection indbygget mærkat til Office apps via tilføjelsesprogrammet Azure Information Protection (AIP)
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Når du bruger Azure Information Protection (AIP) Unified Labeling-klienten, kan du forstå fordelene ved at bruge indbygget mærkat til Office apps i stedet for AIP-tilføjelsesprogrammet.
ms.openlocfilehash: c790ee691e6a72228c865b8cdf9911ee83f4dfd4
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66011564"
---
# <a name="why-choose-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>Hvorfor vælge indbygget mærkning via AIP-tilføjelsesprogrammet til Office apps

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du bruger [følsomhedsmærkater](sensitivity-labels.md) i Microsoft 365 Apps på Windows computere, kan du vælge at bruge mærkater, der er indbygget i Office apps, eller et tilføjelsesprogram fra [AIP-klienten (Azure Information Protection).](/azure/information-protection/rms-client/aip-clientv2) 

Indbygget mærkning udgør hjørnestenen i en [udrulning af Microsoft Purview Information Protection](information-protection-solution.md), fordi denne mærkningsteknologi strækker sig på tværs af platforme (Windows, macOS, iOS, Android og web) samt på tværs af Microsoft-apps og -tjenester og andre steder. Indbygget mærkning er også designet til at fungere sammen med andre Microsoft Purview-funktioner, f.eks. dataklassificering og Forebyggelse af datatab i Microsoft Purview (DLP).

Da indbyggede mærkater ikke bruger et Office-tilføjelsesprogram, kan de drage fordel af mere stabilitet og bedre ydeevne. De understøtter også de nyeste Funktioner i Microsoft Purview, f.eks. avancerede klassificeringer.

Indbygget mærkning er som standard slået fra i Office for Windows apps, når AIP-klienten er installeret. Du kan ændre denne standardfunktionsmåde ved hjælp af vejledningen i følgende afsnit, [Sådan deaktiverer du AIP-tilføjelsesprogrammet for at bruge indbygget mærkat til Office apps](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps).

Når du bevarer AIP-klienten installeret, men deaktiveret i Office apps, understøttes de andre funktioner i AIP-klienten fortsat:

- Højreklik på indstillinger i Stifinder, så brugerne kan anvende mærkater på alle filtyper.

- En fremviser til at vise krypterede filer for tekst, billeder eller PDF-dokumenter.

- Et PowerShell-modul til registrering af følsomme oplysninger i filer i det lokale miljø og til at anvende eller fjerne mærkater og kryptering fra disse filer.

- En scanner til at finde følsomme oplysninger, der er gemt i datalagre i det lokale miljø, og derefter eventuelt navngive indholdet.

Du kan få flere oplysninger om disse funktioner, der udvider mærkning ud over Office apps, i [Vejledningen til Azure Information Protection unified labeling-klientadministrator](/azure/information-protection/rms-client/clientv2-admin-guide) i AIP-dokumentationen.

Uafhængigt af mærkning kan du fortsætte med at bruge [AIPService](/powershell/module/aipservice) PowerShell-modulet til administration af krypteringstjenesten på lejerniveau. Du kan f.eks. konfigurere superbrugeradgang, når du har brug for at fjerne kryptering til datagendannelse, spore og tilbagekalde dokumenter, der er blevet åbnet af AIP-klienten, og konfigurere licensens gyldighedsperiode for offlineadgang. Du kan få flere oplysninger under [Administration af beskyttelse fra Azure Information Protection ved hjælp af PowerShell](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>Beslut, om du vil bruge indbygget mærkning til Office apps eller AIP-tilføjelsesprogrammet

Nu, hvor AIP-klienten er i [vedligeholdelsestilstand](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613), anbefaler vi ikke, at du bruger AIP-tilføjelsesprogrammet til Office apps af følgende årsager:

- Der understøttes ingen nye mærkatfunktioner.
- Tilføjelsesprogrammer er mindre stabile, fordi de kan være i konflikt med andre tilføjelsesprogrammer, der kan resultere i, at Office apps hænger, går ned eller automatisk deaktiverer tilføjelsesprogrammet.
- Som et tilføjelsesprogram kører det langsommere og kan deaktiveres af brugerne for at tilsidesætte krav til mærkater.
- Eventuelle fejlrettelser kræver geninstallation af Azure Information Protection-klienten.
- Mærkatoplevelsen for brugerne adskiller sig lidt fra indbyggede mærkater, som brugerne har på deres andre enheder (macOS, iOS, Android), og når de bruger Office på internettet. Denne forskel kan øge omkostningerne til uddannelse og support.
- Der er allerede udgivet nye Office mærkningsfunktioner, der [kun understøttes af indbygget mærkning](#features-supported-only-by-built-in-labeling-for-office-apps), og listen vokser hele tiden.

Brug kun AIP-tilføjelsesprogrammet til dine Windows Office apps, hvis du allerede har udrullet det til brugerne, og du har brug for tid til at overføre dem til indbygget mærkning. Eller brugerne har brug for en funktion, der ikke understøttes af indbygget mærkning. Brug [oplysningerne om funktionsparitet](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) på denne side som en hjælp til at identificere disse funktioner.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Funktioner, der kun understøttes af indbygget mærkning for Office apps

> [!NOTE]
> Mange nye mærkatfunktioner er i planlægning eller udvikling, så forvent, at listen i dette afsnit vokser over tid.

Nogle funktioner understøttes kun af indbygget mærkning for Office apps og understøttes ikke af AIP-tilføjelsesprogrammet. Disse omfatter:

- Til automatisk og anbefalet mærkning:
    - Adgang til intelligente klassificeringstjenester, der omfatter [klassificeringer, der kan oplæres](classifier-learn-about.md), [EDM (exact data match)](sit-learn-about-exact-data-match-based-sits.md) og [navngivne enheder](named-entities-learn.md)
    - Registrering af følsomme oplysninger som brugertype
    - I Word kan brugerne gennemse og fjerne det identificerede følsomme indhold
- [Understøttelse af PDF](sensitivity-labels-office-apps.md#pdf-support)
- For mærkater, der giver brugere mulighed for at tildele tilladelser, kan der tildeles forskellige tilladelser (Læs eller Rediger) til brugere eller grupper
- Encrypt-Only til mails
- Synlighed af mærkater på statuslinjen
- Understøttelse af kontoskift
- Brugerne kan ikke deaktivere mærkning

Eksempel, der viser, hvordan brugerne kan gennemse og eventuelt fjerne identificeret følsomt indhold i Word:

![Kreditkortnumre, der er identificeret til brugere som følsomhedsindhold med en mulighed for at fjerne.](../media/detect-sensitive-content.png)

Hvis du vil holde dig orienteret, når nye mærkatfunktioner bliver tilgængelige til indbygget mærkning, skal du se Nyheder [i Microsoft Purview](whats-new.md) og sektionerne **Med følsomhedsmærkater** .

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Sådan deaktiverer du AIP-tilføjelsesprogrammet for at bruge indbygget mærkning til Office apps

Når du har installeret AIP-klienten for at udvide mærkateringen ud over Office apps, men vil forhindre klientens tilføjelsesprogram i at blive indlæst i Office apps, skal du bruge Gruppepolitik indstilling **Liste over administrerede tilføjelsesprogrammer**, som dokumenteret i [Ingen tilføjelsesprogrammer indlæst på grund af gruppepolitikindstillinger for Office 2013 og Office 2016-programmer](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

I forbindelse med dine Windows Office apps, der understøtter indbygget mærkning, skal du bruge konfigurationen for Microsoft Word 2016, Excel 2016, PowerPoint 2016 og Outlook 2016, angive følgende program-id'er (ProgID) for AIP-klienten og angive indstillingen til **0: Tilføjelsesprogrammet er altid deaktiveret (blokeret)**

|Program  |Progid  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Udrul denne indstilling ved hjælp af Gruppepolitik eller ved hjælp af [tjenesten Office cloudpolitik](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> Hvis du bruger indstillingen Gruppepolitik **Brug funktionen Følsomhed i Office til at anvende og få vist følsomhedsmærkater** og angive dette til **1**, er der nogle situationer, hvor AIP-tilføjelsesprogrammet stadig kan indlæses i Office apps. Blokering af tilføjelsesprogrammet fra indlæsning i hver app forhindrer, at dette sker.

Du kan også deaktivere eller fjerne **tilføjelsesprogrammet Microsoft Azure Information Protection** Office interaktivt fra Word, Excel, PowerPoint og Outlook. Denne metode er velegnet til en enkelt computer og ad hoc-test. Du kan finde instruktioner under [Få vist, administrer og installér tilføjelsesprogrammer i Office programmer](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

Uanset hvilken metode du vælger, træder ændringerne i kraft, når Office apps genstartes.

> [!NOTE]
> Indbyggede mærkater kræver en abonnementsversion af Office apps. Hvis du har enkeltstående versioner af Office, der nogle gange kaldes "Office Perpetual", anbefaler vi, at du opgraderer til Microsoft 365 Apps, så Enterprise kan drage fordel [af de nyeste mærkatfunktioner](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Husk, at når du bruger denne metode til at deaktivere AIP-tilføjelsesprogrammet, kan du stadig bruge AIP-klienten til at udvide mærkateringen ud over Office apps.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Funktionsparitet for indbygget mærkning og AIP-tilføjelsesprogrammet til Office apps

Mange af de mærkatfunktioner, der understøttes af AIP-tilføjelsesprogrammet, understøttes nu af indbygget mærkning. Du kan finde en mere detaljeret liste over funktioner, minimumversioner, der kan være nødvendige, og konfigurationsoplysninger under [Administrer følsomhedsmærkater i Office apps](sensitivity-labels-office-apps.md).

Der er planlagt flere funktioner, og de er under udvikling. Hvis du er interesseret i en bestemt funktion, kan du se [køreplanen for Microsoft 365](https://aka.ms/MIPC/Roadmap) og overveje at deltage [i Microsoft Information Protection i Office Private Preview](https://aka.ms/MIP/PreviewRing).

Brug følgende oplysninger som en hjælp til at identificere, om du bruger en funktion fra AIP-tilføjelsesprogrammet, der endnu ikke understøttes af indbygget mærkning:

|AIP-tilføjelsesprogramfunktion eller -funktionalitet|Indbygget mærkning |
|:-------------------------------|:----------------:|
|**Kategori: Generelt** ||
|Central rapportering og overvågning|![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Government Cloud|![Understøttes.](../media/yes-icon.png)|
|Administratoren kan deaktivere mærkning <br> - Alle apps|  ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#if-you-need-to-turn-off-built-in-labeling-in-office-apps-on-windows)|
|Administratoren kan deaktivere mærkning <br> - Pr. app|  I planlægning eller udvikling|
|**Kategori: Brugeroplevelse** ||
|Knappen Navne på båndet|![Understøttes.](../media/yes-icon.png)|
|Understøttelse af flere sprog for navne og værktøjstip| ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Navnefarver| I planlægning eller udvikling |
|Synlighed af navne på værktøjslinjen| I planlægning eller udvikling |
|**Kategori: Navnehandlinger** ||
|Manuel mærkning |  ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Obligatorisk mærkning | ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do)|
|Standardnavne <br> - Nye og eksisterende elementer <br> - Separate indstillinger for mail|  ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do) |
|Anbefalet eller automatisk |![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Justering af nedgradering |  ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do)|
| **Kategori: Visuelle markeringer** | |
|Sidehoveder, sidefødder, vandmærke| ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do)|
|Dynamiske markeringer| ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Markering af visualiseringer pr. app| ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Kategori: Kryptering** | |
|Administratordefinerede tilladelser | ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](encryption-sensitivity-labels.md#assign-permissions-now) |
|Brugerdefinerede tilladelser <br> - Videresend ikke for Outlook <br> – Bruger- og gruppetilladelser til Word, Excel PowerPoint| ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Brugerdefinerede tilladelser <br> – Brugerdefinerede tilladelser for hele organisationen ved at angive domæner for Word, Excel PowerPoint | I planlægning eller udvikling |
|Samtidig redigering og automatisk lagring | ![Understøttes.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-coauthoring.md) |
|Kryptering med dobbelt nøgle | I planlægning eller udvikling |
|Tilbagekaldelse af dokument for brugere | Under gennemgang |
| | |

### <a name="support-for-powershell-advanced-settings"></a>Understøttelse af avancerede PowerShell-indstillinger

AIP-klienten understøtter mange tilpasninger ved hjælp af [avancerede powershell-indstillinger](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). Nogle af disse avancerede indstillinger understøttes nu af indbygget mærkning, som dokumenteret i [New-Label](/powershell/module/exchange/new-label) eller [Set-Label](/powershell/module/exchange/set-label) og [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) eller [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

Du kan dog opleve, at du ikke behøver at bruge PowerShell til at konfigurere de understøttede indstillinger, fordi de er inkluderet i standardkonfigurationen fra Microsoft Purview-overholdelsesportalen. Det kan f.eks. være muligheden for at slå obligatorisk mærkning fra for Outlook og angive et andet standardnavn.

Følgende konfigurationer fra AIP-tilføjelsesprogrammet understøttes endnu ikke af indbygget mærkat omfatter:

- [Mærk nedarvning fra vedhæftede filer i mails](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME til Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [Overdeling af pop op-meddelelser for Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Standardundermærkat for en overordnet etiket](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Fjern eksterne indholdsmarkeringer](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Funktioner, der ikke er planlagt til at blive understøttet af indbygget mærkning for Office apps

Selvom der hele tiden tilføjes nye funktioner til indbygget mærkning, understøtter AIP-Office-tilføjelsesprogrammet følgende funktioner, der ikke er planlagt til at være tilgængelige i fremtidige versioner til indbygget mærkning:

- Anvendelse af mærkater til Microsoft Office 97-2003-formater, f.eks. .doc filer
- Computere, der er afbrudt permanent
- Enkeltstående udgaver af Office (også kaldet "Office Permanent") i stedet for abonnementsbaserede

## <a name="next-steps"></a>Næste trin

Du kan finde oplysninger om, hvordan du opretter og konfigurerer disse mærkategenskaber, under [Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md).

> [!TIP]
> Hvis du allerede har følsomhedsmærkater på Microsoft Purview-overholdelsesportalen, er du ikke berettiget til automatisk oprettelse af standardmærkater. Du kan dog stadig finde det nyttigt at referere til deres konfiguration: [Standardfølsomhedsmærkater](mip-easy-trials.md#default-sensitivity-labels). 
