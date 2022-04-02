---
title: Vælg Microsoft Information Protection (MIP) indbygget mærkning af Office apps over Azure Information Protection-tilføjelsesprogrammet (AIP)
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
description: Når du bruger den samlede AIP-klient (Azure Information Protection), skal du forstå fordelene ved at bruge indbygget mærkning til Office-apps i stedet for AIP-tilføjelsesprogrammet.
ms.openlocfilehash: 38aee57720f38793f4f61cc871a9bee556e28690
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498599"
---
# <a name="why-choose-mip-built-in-labeling-over-the-aip-add-in-for-office-apps"></a>Hvorfor vælge Indbygget MIP-mærkning over AIP-tilføjelsesprogrammet til Office apps

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Når du bruger [](sensitivity-labels.md) følsomhedsmærkater i Microsoft 365 Apps på Windows-computere, har du mulighed for at bruge mærkning, der er indbygget i Office-apps, eller et tilføjelsesprogrammet fra [Den samlede AIP-klient (Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2)). 

Den indbyggede mærkning udgør hjørnestenene i en [Microsoft Information Protection-installation (MIP](information-protection-solution.md)), fordi denne mærkningsteknologi strækker sig over platforme (Windows, macOS, iOS, Android og internettet) samt på tværs af Microsoft-apps og -tjenester og længere væk. Den indbyggede mærkning er også udviklet til at fungere sammen med andre MIP-funktioner, f.eks. dataklassificering og forebyggelse af datatab (DLP).

Da indbyggede etiketter ikke bruger et tilføjelse Office, drager de fordel af mere stabilitet og bedre ydeevne. De understøtter også de nyeste MIP-funktioner, f.eks. avancerede klassificeringer.

Som standard er indbygget mærkning slået fra i Office for Windows apps, når AIP-klienten er installeret. Du kan ændre denne standardfunktionsmåde ved at følge vejledningen i følgende afsnit Sådan deaktiverer du [tilføjelsesprogrammet AIP for at bruge indbygget mærkning til Office apps](#how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps).

Når du beholder AIP-klienten installeret, men deaktiveret i Office apps, forbliver de andre funktioner i AIP-klienten understøttet:

- Højrekliksindstillinger i dialogboksen Stifinder brugerne mulighed for at anvende navne på alle filtyper.

- En fremviser til at vise krypterede filer for tekst, billeder eller PDF-dokumenter.

- Et PowerShell-modul til at opdage følsomme oplysninger i filer i det lokale miljø og anvende eller fjerne navne og kryptering fra disse filer.

- En scanner til at finde følsomme oplysninger, der er gemt i lokale datalagre, og derefter vælge at navnmærke indholdet.

Du kan finde flere oplysninger om disse funktioner, der udvider mærkning ud over Office-apps, i [Azure Information Protection Unified Labeling Client Administrator guide](/azure/information-protection/rms-client/clientv2-admin-guide) fra AIP-dokumentationen.

Uafhængigt af mærkningen kan du fortsætte med at bruge [AIPService](/powershell/module/aipservice) PowerShell-modulet til administration af krypteringstjenesten på lejerniveau. Konfigurer f.eks. superbrugeradgang, når du har brug for at fjerne kryptering til gendannelse af data, spor og tilbagekald dokumenter, der er blevet åbnet af AIP-klienten, og konfigurer anvendelseslicensens gyldighedsperiode for offlineadgang. Få mere at vide under [Administration af beskyttelse mod Azure Information Protection ved hjælp af PowerShell](/azure/information-protection/administer-powershell).

## <a name="decide-whether-to-use-built-in-labeling-for-office-apps-or-the-aip-add-in"></a>Beslut, om du vil bruge indbygget mærkning Office apps eller AIP-tilføjelsesprogrammet

Nu, hvor AIP-klienten er i vedligeholdelsestilstand[, anbefaler](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613) vi, at du ikke bruger tilføjelsesprogrammet AIP til Office-apps af følgende årsager:

- Ingen nye etiketfunktioner understøttes.
- Tilføjelsesprogrammer er mindre stabile, fordi de kan skabe konflikter med andre tilføjelsesprogrammer, der kan medføre, Office apps hænger, går ned eller automatisk deaktiverer tilføjelsesprogrammet.
- Som tilføjelsesprogrammet kører det langsommere og kan deaktiveres af brugere for at tilsidesætte krav til mærkning.
- Fejlrettelser kræver geninstallation af Azure Information Protection-klienten.
- Etiketoplevelsen for brugerne er en smule anderledes end indbyggede etiketter, som brugerne har på deres andre enheder (macOS, iOS, Android), og når de bruger Office på internettet. Denne forskel kan øge omkostningerne til uddannelse og support.
- Der er allerede nye Office udgivet mærkningsfunktioner, der kun understøttes af [indbygget](#features-supported-only-by-built-in-labeling-for-office-apps) mærkning, og listen vokser hele tiden.

Brug kun AIP-tilføjelsesprogrammet til dine Windows Office-apps, hvis du allerede har installeret det til brugerne, og du har brug for tid til at overføre dem til indbygget mærkning. Eller brugere har brug for en funktion, der ikke understøttes af indbygget mærkning. Brug oplysningerne [om paritet for funktioner på](#feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps) denne side som en hjælp til at identificere disse funktioner.

## <a name="features-supported-only-by-built-in-labeling-for-office-apps"></a>Funktioner, der kun understøttes af indbygget mærkning til Office apps

> [!NOTE]
> Mange nye mærkatfunktioner er under planlægning eller udvikling, så forvent, at listen i dette afsnit vokser med tiden.

Nogle funktioner understøttes kun af indbygget mærkning af Office-apps og understøttes ikke af AIP-tilføjelsesprogrammet. Disse omfatter:

- Til automatisk og anbefalet mærkat:
    - Adgang til intelligente klassificeringstjenester, [der](classifier-learn-about.md) omfatter trænbare klassificeringer, nøjagtigt [datamatch (EDM)](sit-learn-about-exact-data-match-based-sits.md) og [navngivne enheder](named-entities-learn.md)
    - Registrering af følsomme oplysninger, mens brugere skriver
    - I Word kan brugerne gennemse og fjerne det identificerede følsomme indhold
- For etiketter, som brugerne kan tildele tilladelser, kan forskellige tilladelser (Læs eller Rediger) tildeles til brugere eller grupper
- Encrypt-Only til mails
- Synlighed af navne på statuslinjen
- Support til skift af konto
- Brugere kan ikke deaktivere mærkning

Eksempel, der viser, hvordan brugere kan gennemse og eventuelt fjerne identificeret følsomt indhold i Word:

![Kreditkortnumre, der er identificeret for brugere som følsomhedsindhold med mulighed for at fjerne.](../media/detect-sensitive-content.png)

Hvis du vil holde dig informeret, når nye mærkningsfunktioner bliver tilgængelige til indbygget mærkning, skal du se Nyheder i [Microsoft 365-overholdelse](whats-new.md) og **følsomhedsetiketter** afsnittene.

## <a name="how-to-disable-the-aip-add-in-to-use-built-in-labeling-for-office-apps"></a>Sådan deaktiverer du tilføjelsesprogrammet AIP for at bruge indbygget mærkning til Office apps

Når du har installeret AIP-klienten til at udvide mærkning ud over Office-apps, men vil forhindre, at **klientens tilføjelsesprogrammer indlæses i Office-apps**, skal du bruge indstillingen Gruppepolitik-indstilling Liste over administrerede tilføjelsesprogrammer som dokumenteret i Indlæste tilføjelsesprogrammer uden tilføjelsesprogrammer på grund af gruppepolitikindstillinger [for Office 2013- og Office 2016-programmer](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

Til dine Windows Office-apps, der understøtter indbygget mærkning, skal du bruge konfigurationen til Microsoft Word 2016, Excel 2016, PowerPoint 2016 og Outlook 2016 ved at angive følgende programidentifikatorer (ProgID) for AIP-klienten og **angive indstillingen til 0: Tilføjelsesprogrammet er altid deaktiveret (blokeret)**

|Program  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

Installér denne indstilling ved Gruppepolitik eller ved hjælp af Office [skypolitiktjeneste](/DeployOffice/overview-office-cloud-policy-service).

> [!IMPORTANT]
> Hvis du bruger Gruppepolitik-indstillingen Brug funktionen Følsomhed i **Office** til at anvende og få vist følsomhedsmærkater og angive denne til **1**, er der visse situationer, hvor tilføjelsesprogrammet AIP stadig kan indlæses i Office-apps. Blokering af tilføjelsesprogrammet i at blive indlæst i hver app forhindrer dette.

Alternativt kan du deaktivere eller fjerne **tilføjelsesprogrammet Microsoft Azure Information Protection** Office interaktivt fra Word, Excel, PowerPoint og Outlook. Denne metode egner sig til en enkelt computer og ad hoc-test. Du kan finde en [vejledning i Få vist, administrer og installer tilføjelsesprogrammer i Office programmer](https://support.office.com/article/16278816-1948-4028-91e5-76dca5380f8d).

Uanset hvilken metode du vælger, træder ændringerne i kraft, når Office apps genstarter.

> [!NOTE]
> Indbyggede navne kræver en abonnementsversion af Office apps. Hvis du har enkeltstående udgaver af Office, som nogle gange kaldes "Office Tidsubelig", anbefaler vi, at du opgraderer til Microsoft 365 Apps, så Enterprise kan drage fordel af de nyeste egenskaber ved [navne.](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)

Husk, at når du bruger denne metode til at deaktivere AIP-tilføjelsesprogrammet, kan du stadig bruge AIP-klienten til at udvide mærkning ud over Office apps.

## <a name="feature-parity-for-built-in-labeling-and-the-aip-add-in-for-office-apps"></a>Funktionsparitet for indbygget mærkning og AIP-tilføjelsesprogrammet til Office apps

Mange af de etiketfunktioner, der understøttes af AIP-tilføjelsesprogrammet, understøttes nu af indbygget mærkning. Hvis du vil have en mere detaljeret liste over funktioner, minimumversioner, der kan være behov for, og konfigurationsoplysninger, skal du se Administrer følsomhedsmærkater [Office apps](sensitivity-labels-office-apps.md).

Der er planlagt og under udvikling af flere funktioner. Hvis der er en bestemt funktion, du er interesseret i, skal du se oversigten [over Microsoft 365](https://aka.ms/MIPC/Roadmap) og overveje at deltage i [Microsoft Information Protection i Office privat eksempelvisning](https://aka.ms/MIP/PreviewRing).

Brug følgende oplysninger som hjælp til at identificere, om du bruger en funktion fra AIP-tilføjelsesprogrammet, der endnu ikke understøttes af indbygget mærkning:

|Funktion eller funktion til AIP-tilføjelsesprogrammet|Indbygget mærkning |
|:-------------------------------|:----------------:|
|**Kategori: Generelt** ||
|Central rapportering og overvågning|![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#auditing-labeling-activities) |
|Government Cloud|![Understøttet.](../media/yes-icon.png)|
|Administratoren kan deaktivere mærkning <br> - Alle apps|  ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#office-built-in-labeling-client-and-other-labeling-solutions)|
|Administratoren kan deaktivere mærkning <br> - Pr. app|  Under planlægning eller udvikling|
|**Kategori: Brugeroplevelse** ||
|Knappen Mærkning på båndet|![Understøttet.](../media/yes-icon.png)|
|Understøttelse af flere sprog for navne og værktøjstip| ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) |
|Navnefarver| Under planlægning eller udvikling |
|Synlighed af navne på værktøjslinjen| Under planlægning eller udvikling |
|**Kategori: Navnehandlinger** ||
|Manuel mærkning |  ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) |
|Obligatorisk mærkning | ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do)|
|Standardmærkning <br> - Nye og eksisterende elementer <br> - Separate indstillinger for mail|  ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do) |
|Anbefalet eller automatisk |![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps) |
|Nedgrader begrundelse |  ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do)|
| **Kategori: Visuelle markeringer** | |
|Sidehoveder, sidefødder, vandmærke| ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels.md#what-label-policies-can-do)|
|Dynamiske markeringer| ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#dynamic-markings-with-variables)|
|Visuel mærkning pr. app| ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-office-apps.md#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook)|
| **Kategori: Kryptering** | |
|Administratordefinerede tilladelser | ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](encryption-sensitivity-labels.md#assign-permissions-now) |
|Brugerdefinerede tilladelser <br> - Videresendes ikke for Outlook <br> - Bruger- og gruppetilpassede tilladelser for Word, Excel, PowerPoint| ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](encryption-sensitivity-labels.md#let-users-assign-permissions)|
|Brugerdefinerede tilladelser <br> - Brugerdefinerede tilladelser for hele organisationen ved at angive domæner for Word, Excel, PowerPoint | Under planlægning eller udvikling |
|Samtidig redigering og automatisk lagring | ![Understøttet.](../media/yes-icon.png) <br>[Få mere at vide](sensitivity-labels-coauthoring.md) |
|Kryptering med dobbelt nøgle | Under planlægning eller udvikling |
|Tilbagekaldelse af dokumenter for brugere | Under gennemgang |
| | |

### <a name="support-for-powershell-advanced-settings"></a>Support til avancerede indstillinger i PowerShell

AIP-klienten understøtter mange tilpasninger ved hjælp af avancerede [indstillinger i PowerShell](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configuring-advanced-settings-for-the-client-via-powershell). Nogle af disse avancerede indstillinger understøttes nu af indbygget mærkning, som det er dokumenteret i [New-Label](/powershell/module/exchange/new-label) eller [Set-Label](/powershell/module/exchange/set-label) og [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy) eller [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy).

Du finder dog muligvis ud af, at du ikke behøver at bruge PowerShell til at konfigurere de understøttede indstillinger, fordi de er inkluderet i standardkonfigurationen fra Microsoft 365 Overholdelsescenter. Eksempelvis muligheden for at deaktivere obligatorisk mærkat for Outlook angive en anden standardetiket.

Følgende konfigurationer fra AIP-tilføjelsesprogrammet understøttes endnu ikke af indbygget mærkning:

- [Nedarvning af navne fra vedhæftede filer i mails](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
- [S/MIME til Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#configure-a-label-to-apply-smime-protection-in-outlook)
- [Overdeling af pop op-meddelelser for Outlook](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)
- [Standardundernavn for et overordnet navn](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#specify-a-default-sublabel-for-a-parent-label)
- [Fjerne eksterne indholdsmærkninger](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solution )

## <a name="features-not-planned-to-be-supported-by-built-in-labeling-for-office-apps"></a>Funktioner, der ikke er planlagt til at blive understøttet af indbygget mærkning af Office apps

Selvom der hele tiden tilføjes nye funktioner til indbygget mærkning, understøtter tilføjelsesprogrammet AIP Office følgende funktioner, der ikke er planlagt til at blive tilgængelige i fremtidige versioner til indbygget mærkning:

- Anvendelse af navne på Microsoft Office 97-2003-formater, f.eks. .doc filer
- Computere, der er afbrudt permanent
- Enkeltstående udgaver af Office (nogle gange kaldet "tidsubetiske Office") i stedet for abonnementsbaserede

## <a name="next-steps"></a>Næste trin

Du kan finde en vejledning til at oprette og konfigurere disse egenskaber for mærkning i [Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md).

> [!TIP]
> Hvis du allerede har følsomhedsmærkater i Microsoft 365 Overholdelsescenter, er du ikke berettiget til automatisk oprettelse af standardetiketter. Du kan dog stadig finde det nyttigt at henvise til deres konfiguration: [Standard følsomhedsmærkater](mip-easy-trials.md#default-sensitivity-labels). 
