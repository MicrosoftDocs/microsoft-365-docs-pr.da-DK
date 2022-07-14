---
title: Indstillinger for styring af insiderrisiko
description: Få mere at vide om indstillinger for styring af insiderrisiko i Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 5e9f9eb04d2fb239c69aacd8927cde7f295c7716
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787534"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Kom i gang med indstillinger for styring af insiderrisiko

Indstillinger for styring af insiderrisiko gælder for alle politikker for styring af insiderrisiko, uanset hvilken skabelon du vælger, når du opretter en politik. Indstillinger konfigureres ved hjælp af kontrolelementet **Insider-risikoindstillinger** , der er placeret øverst på alle sider til styring af insiderrisiko. Disse indstillinger styrer politikkomponenter for følgende områder:

- [Beskyttelse af personlige oplysninger](#privacy)
- [Indikatorer](#indicators)
- [Politiktidsrammer](#policy-timeframes)
- [Intelligente registreringer](#intelligent-detections)
- [Eksportér beskeder](#export-alerts)
- [Prioriterede brugergrupper (prøveversion)](#priority-user-groups-preview)
- [Prioriterede fysiske aktiver (prøveversion)](#priority-physical-assets-preview)
- [Power Automate-flow (prøveversion)](#power-automate-flows-preview)
- [Microsoft Teams (prøveversion)](#microsoft-teams-preview)
- [Analytics](#analytics)
- [Administration meddelelser](#admin-notifications)

Før du kommer i gang og opretter politikker for styring af insiderrisiko, er det vigtigt at forstå disse indstillinger og vælge de indstillingsniveauer, der passer bedst til organisationens behov for overholdelse af angivne standarder.

## <a name="privacy"></a>Beskyttelse af personlige oplysninger

Det er vigtigt at beskytte beskyttelsen af personlige oplysninger for brugere, der har politikforekomster, og det kan hjælpe med at fremme objektivitet i forbindelse med dataundersøgelser og analysegennemgange for insiderrisikobeskeder. For brugere med et match af en insiderrisikopolitik kan du vælge en af følgende indstillinger:

- **Vis anonymiserede versioner af brugernavne**: Navne på brugere anonymiseres for at forhindre administratorer, dataundersøgere og korrekturlæsere i at se, hvem der er knyttet til politikbeskeder. En bruger "Grace Taylor" vises f.eks. med et randomiseret pseudonym, f.eks. "AnonIS8-988" på alle områder af insiderrisikostyringsoplevelsen. Hvis du vælger denne indstilling, anonymiseres alle brugere med aktuelle og tidligere politikforekomster og gælder for alle politikker. Brugerprofiloplysninger i insiderrisikobeskeden og sagsoplysningerne vil ikke være tilgængelige, når denne indstilling vælges. Brugernavne vises dog, når du føjer nye brugere til eksisterende politikker, eller når du tildeler brugere til nye politikker. Hvis du vælger at deaktivere denne indstilling, vises brugernavne for alle brugere, der har aktuelle eller tidligere politikforekomster.

    >[!IMPORTANT]
    >Hvis du vil bevare referentiel integritet for brugere, der har insiderrisikobeskeder eller -sager i Microsoft 365 eller andre systemer, bevares anonymisering af brugernavne ikke for eksporterede beskeder. Eksporterede beskeder viser brugernavne for hver besked.

- **Vis ikke anonymiserede versioner af brugernavne**: Brugernavne vises for alle aktuelle og tidligere politikkampe for beskeder og sager. Brugerprofiloplysninger (navn, titel, alias og organisation eller afdeling) vises for brugeren for alle insiderrisikostyringsbeskeder og -sager.

![Indstillinger for beskyttelse af personlige oplysninger i forbindelse med styring af insiderrisiko.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Indikatorer

Skabeloner til insiderrisikopolitik definerer den type risikoaktiviteter, du vil registrere og undersøge. Hver politikskabelon er baseret på specifikke indikatorer, der svarer til specifikke udløsere og risikoaktiviteter. Alle indikatorer er som standard deaktiveret, og du skal vælge en eller flere politikindikatorer, før du konfigurerer en insiderrisikostyringspolitik.

Beskeder udløses af politikker, når brugerne udfører aktiviteter, der er relateret til politikindikatorer, der opfylder en påkrævet tærskel. Insiderrisikostyring bruger to typer indikatorer:

- **Udløsende hændelser**: Hændelser, der bestemmer, om en bruger er aktiv i en politik for styring af insiderrisiko. Hvis en bruger føjes til en politik for styring af insiderrisiko ikke har en udløsende hændelse, evalueres brugeraktiviteten ikke af politikken. Bruger A føjes f.eks. til en politik, der er oprettet *ud fra datatyveri ved hjælp af politikskabelonen for brugere, der forlader* virksomheden, og politikken og Microsoft 365 HR-connectoren er konfigureret korrekt. Indtil bruger A har en slutdato rapporteret af HR-connectoren, evalueres Bruger A-aktiviteter ikke af denne politik for styring af insiderrisiko for risici. Et andet eksempel på en udløsende hændelse er, hvis en bruger har en DLP-politikbesked med *høj* alvorsgrad, når der bruges politikker for *datalækager* .
- **Politikindikatorer**: Indikatorer, der er inkluderet i politikker for styring af insiderrisiko, som bruges til at fastslå en risikoscore for en bruger i området. Disse politikindikatorer aktiveres kun, når der opstår en udløsende hændelse for en bruger. Nogle eksempler på politikindikatorer er, når en bruger kopierer data til personlige cloudlagertjenester eller bærbare lagerenheder, hvis en brugerkonto fjernes fra Azure Active Directory, eller hvis en bruger deler interne filer og mapper med uautoriserede eksterne parter.

Visse politikindikatorer kan også bruges til at tilpasse udløsende hændelser for bestemte politikskabeloner. Når disse indikatorer er konfigureret i politikguiden for skabelonerne *Generelle datalækager* eller *Datalækager for prioriterede brugere* , giver disse indikatorer dig større fleksibilitet og tilpasning til dine politikker, og når brugerne er omfattet af en politik. Du kan også definere individuelle aktivitetstærskler for disse udløsende indikatorer for at få mere detaljeret kontrol i en politik.

Politikindikatorer er opdelt i følgende områder. Du kan vælge de indikatorer, der skal aktivere og tilpasse indikatorhændelsesgrænserne for hvert indikatorniveau, når du opretter en insiderrisikopolitik:

- **Office-indikatorer**: Disse omfatter politikindikatorer for SharePoint-websteder, Microsoft Teams og mailbeskeder.
- **Enhedsindikatorer**: Disse omfatter politikindikatorer for aktiviteter, f.eks. deling af filer via netværket eller med enheder. Indikatorer omfatter aktiviteter, der involverer alle filtyper, bortset fra eksekverbar filaktivitet (.exe) og .dll. Hvis du vælger *Enhedsindikatorer*, behandles aktiviteten for enheder med Windows 10 Build 1809 eller nyere og macOS-enheder (Catalina 10.15 eller nyere). For både Windows- og macOS-enheder skal du først onboarde enheder til overholdelsesportalen. Enhedsindikatorer omfatter også browsersignalregistrering, der hjælper din organisation med at registrere og reagere på exfiltrationssignaler for ikke-eksekverbare filer, der vises, kopieres, deles eller udskrives i Microsoft Edge og Google Chrome. Du kan få flere oplysninger om konfiguration af Windows-enheder til integration med insiderrisiko i afsnittet [Aktivér enhedsindikatorer og onboarding af Windows-enheder](insider-risk-management-settings.md#OnboardDevices) i denne artikel. Du kan få flere oplysninger om konfiguration af macOS-enheder til integration med insiderrisiko i afsnittet Aktivér enhedsindikatorer og onboarde macOS-enheder i denne artikel. Du kan finde flere oplysninger om browsersignalregistrering under [Få mere at vide om og konfigurer browsersignalregistrering for styring af insiderrisiko](insider-risk-management-browser-support.md).
- **Indikator for overtrædelse af sikkerhedspolitik (prøveversion)**: Disse omfatter indikatorer fra Microsoft Defender for Endpoint, der er relateret til installation af ikke-godkendt eller skadelig software eller omgåelse af sikkerhedskontroller. Hvis du vil modtage beskeder i styring af insiderrisiko, skal du have aktiveret en aktiv Defender for Endpoint-licens og integration af insiderrisiko. Du kan finde flere oplysninger om konfiguration af Defender for Endpoint til integration af styring af insiderrisiko under [Konfigurer avancerede funktioner i Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Adgangsindikatorer for patientjournaler (prøveversion)**: Disse omfatter politikindikatorer for adgang til patientjournaler. Forsøg på at få adgang til patientjournaler i dine EMR-systemlogge (Electronic Medical Records) kan f.eks. deles med politikker for styring af insiderrisiko. Hvis du vil modtage disse typer beskeder i styring af insiderrisiko, skal du have konfigureret en sundhedsspecifik dataconnector og HR-dataconnectoren.
- **Indikatorer for fysisk adgang (prøveversion)**: Disse omfatter politikindikatorer for fysisk adgang til følsomme aktiver. Forsøg på at få adgang til et begrænset område i dine fysiske systemlogge for dårligging kan f.eks. deles med politikker for styring af insiderrisiko. Hvis du vil modtage disse typer beskeder i styring af insiderrisiko, skal du have prioriteret fysiske aktiver aktiveret i styring af insiderrisiko og [den fysiske badging-dataconnector](import-physical-badging-data.md) konfigureret. Du kan få mere at vide om konfiguration af fysisk adgang i [afsnittet Prioritet for fysisk adgang](#priority-physical-assets-preview) i denne artikel.
- **Microsoft Defender for Cloud Apps indikatorer (prøveversion)**: Disse omfatter politikindikatorer fra delte beskeder fra Defender for Cloud Apps. Automatisk aktiveret registrering af uregelmæssigheder i Defender for Cloud Apps begynder straks at registrere og sortere resultater og målretter adskillige uregelmæssigheder i funktionsmåden på tværs af dine brugere og de maskiner og enheder, der er forbundet til dit netværk. Hvis du vil medtage disse aktiviteter i vigtige politikbeskeder for styring af insiderrisiko, skal du vælge en eller flere indikatorer i dette afsnit. Hvis du vil vide mere om Defender for Cloud Apps-analyser og registrering af uregelmæssigheder, skal du se [Hent adfærdsanalyser og registrering af uregelmæssigheder](/cloud-app-security/anomaly-detection-policy).
- **Boostere af risikoscore**: Disse omfatter at øge risikoscoren for aktiviteter, der er over brugerens normale aktivitet for en dag, eller for brugere med tidligere sager, der er løst som en politikovertrædelse. Aktivering af boostere af risikoscore øger risikoscores og sandsynligheden for beskeder for disse typer aktiviteter. For aktiviteter, der ligger over brugerens normale aktivitet for en dag, øges scorerne, hvis den registrerede aktivitet afviger fra brugerens typiske adfærd. For brugere med tidligere sager, der er løst som en politikovertrædelse, øges scorerne, hvis en bruger tidligere har fået løst mere end én sag som en bekræftet politikovertrædelse. Boostere til risikoscore kan kun vælges, hvis en eller flere indikatorer er valgt.

I nogle tilfælde kan det være en god idé at begrænse de indikatorer for insiderrisikopolitik, der anvendes på insiderrisikopolitikker i din organisation. Du kan slå politikindikatorer for bestemte områder fra ved at deaktivere dem fra alle politikker for insiderrisiko. Udløsende hændelser kan kun ændres for politikker, der er oprettet ud fra skabelonerne *Generelle datalækager* eller *Datalækager af prioriterede brugere* . Politikker, der er oprettet ud fra alle andre skabeloner, har ikke udløserindikatorer eller -hændelser, der kan tilpasses.

Hvis du vil definere indikatorer for insiderrisikopolitik, der er aktiveret i alle insiderrisikopolitikker, skal du gå til **Insiderrisikoindstillinger** > **Indikatorer** og vælge en eller flere politikindikatorer. De indikatorer, der er valgt på siden Med indstillinger for indikatorer, kan ikke konfigureres individuelt, når du opretter eller redigerer en insiderrisikopolitik i guiden Politik.

> [!NOTE]
> Det kan tage flere timer, før nye manuelt tilføjede brugere vises i **dashboardet Brugere**. Det kan tage op til 24 timer at vise aktiviteter for de foregående 90 dage for disse brugere. Hvis du vil have vist aktiviteter for manuelt tilføjede brugere, skal du vælge brugeren på **dashboardet Brugere** og åbne fanen **Brugeraktivitet** i detaljeruden.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Aktivér enhedsindikatorer og onboarde Windows-enheder
<a name="OnboardDevices"> </a>

Hvis du vil aktivere registrering af risikoaktiviteter på Windows-enheder og inkludere politikindikatorer for disse aktiviteter, skal dine Windows-enheder opfylde følgende krav, og du skal fuldføre følgende onboardingtrin.

#### <a name="step-1-prepare-your-endpoints"></a>Trin 1: Forbered dine slutpunkter

Sørg for, at de Windows 10 enheder, du planlægger at rapportere i insiderrisikostyring, opfylder disse krav.

1. Skal køre Windows 10 x64 build 1809 eller nyere og skal have installeret [opdateringen til Windows 10 (OS Build 17763.1075)](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) fra den 20. februar 2020.
2. Den brugerkonto, der bruges til at logge på Windows 10 enhed, skal være en aktiv AAD-konto (Azure Active Directory). Den Windows 10 enhed kan være [tilmeldt AAD](/azure/active-directory/devices/concept-azure-ad-join), hybrid AAD eller Active Directory eller AAD registreret.
3. Installér Microsoft Edge-browseren på slutpunktsenheden for at registrere handlinger for uploadaktiviteten i skyen. Se [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>Trin 2: Onboarding af enheder
<a name="OnboardStep2"> </a>

Du skal aktivere enhedsovervågning og onboarde dine slutpunkter, før du kan registrere insiderrisikostyringsaktiviteter på en enhed. Begge handlinger udføres i Microsoft Purview-compliance-portal.

Når du vil onboarde enheder, der endnu ikke er onboardet, skal du downloade det relevante script og installere som beskrevet i følgende trin.

Hvis du allerede har enheder onboardet i [Microsoft Defender for Endpoint](/windows/security/threat-protection/), vises de allerede på listen over administrerede enheder. Følg [trin 3: Hvis du har enheder onboardet i Microsoft Defender for Endpoint](insider-risk-management-settings.md#OnboardStep3) i næste afsnit.

I dette installationsscenarie skal du onboarde enheder, der endnu ikke er onboardet, og du vil blot registrere insiderrisikoaktiviteter på Windows 10 enheder.

1. Åbn [Microsoft Purview-compliance-portal](https://compliance.microsoft.com).
2. Åbn siden med indstillinger for overholdelsesportalen, og vælg **Ombordværende enheder**.

   > [!NOTE]
   > Selvom det normalt tager ca. 60 sekunder, før onboarding af enheder er aktiveret, skal du vente op til 30 minutter, før du engagerer dig i Microsoft-support.

3. Vælg **Enhedshåndtering** for at åbne listen **Enheder** . Listen er tom, indtil du onboarder enheder.
4. Vælg **Onboarding** for at starte onboardingprocessen.
5. Vælg, hvordan du vil installere på disse flere enheder, på listen **Installationsmetode** , og **download derefter pakken**.
6. Følg de relevante procedurer i [Onboarding værktøjer og metoder til Windows 10 maskiner](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Dette link fører dig til en landingsside, hvor du kan få adgang til Microsoft Defender for Endpoint procedurer, der svarer til den installationspakke, du valgte i trin 5:
    - Onboarde Windows 10 maskiner ved hjælp af Gruppepolitik
    - Onboarde Windows-maskiner ved hjælp af Microsoft Endpoint Configuration Manager
    - Onboarde Windows 10-maskiner ved hjælp af værktøjer til Enhedshåndtering til mobilenheder
    - Onboarde Windows 10-maskiner ved hjælp af et lokalt script
    - Onboarde VDI-maskiner (Virtual Desktop Infrastructure), der ikke er vedvarende.

Når du er færdig, og slutpunktet er onboardet, bør det være synligt på enhedslisten, og slutpunktet begynder at rapportere overvågningsaktivitetslogge til styring af insiderrisiko.

> [!NOTE]
> Denne oplevelse er under håndhævelse af licenser. Uden den påkrævede licens er data ikke synlige eller tilgængelige.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>Trin 3: Hvis du har enheder onboardet i Microsoft Defender for Endpoint
<a name="OnboardStep3"> </a>

Hvis Microsoft Defender for Endpoint allerede er installeret, og der er rapportering af slutpunkter i, vises alle disse slutpunkter på listen over administrerede enheder. Du kan fortsætte med at onboarde nye enheder i styring af insiderrisiko for at udvide dækningen ved hjælp af afsnittet [Trin 2: Onboarding-enheder](insider-risk-management-settings.md#OnboardStep2) .

1. Åbn [Microsoft Purview-compliance-portal](https://compliance.microsoft.com).
2. Åbn siden med indstillinger for overholdelsesportalen, og vælg **Aktivér enhedsovervågning**.
3. Vælg **Enhedshåndtering** for at åbne listen **Enheder** . Du bør kunne se listen over enheder, der allerede rapporterer til Microsoft Defender for Endpoint.
4. Vælg **Onboarding** , hvis du har brug for at onboarde flere enheder.
5. Vælg, hvordan du vil installere på disse flere enheder, på listen **Installationsmetode** og derefter **Download pakke**.
6. Følg de relevante procedurer i [Onboarding værktøjer og metoder til Windows 10 maskiner](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Dette link fører dig til en landingsside, hvor du kan få adgang til Microsoft Defender for Endpoint procedurer, der svarer til den installationspakke, du valgte i trin 5:
    - Onboarde Windows 10 maskiner ved hjælp af Gruppepolitik
    - Onboarde Windows-maskiner ved hjælp af Microsoft Endpoint Configuration Manager
    - Onboarde Windows 10-maskiner ved hjælp af værktøjer til Enhedshåndtering til mobilenheder
    - Onboarde Windows 10-maskiner ved hjælp af et lokalt script
    - Onboarde VDI-maskiner (Virtual Desktop Infrastructure), der ikke er vedvarende.

Når du er færdig, og slutpunktet er onboardet, bør det være synligt under tabellen **Enheder** , og slutpunktet begynder at rapportere overvågningsaktivitetslogge til styring af insiderrisiko.

> [!NOTE]
>Denne oplevelse er under håndhævelse af licenser. Uden den påkrævede licens er data ikke synlige eller tilgængelige.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Aktivér enhedsindikatorer og onboarde macOS-enheder

macOS-enheder (Catalina 10.15 eller nyere) kan onboardes i Microsoft 365 for at understøtte politikker for styring af insiderrisiko ved hjælp af enten Intune eller JAMF Pro. Du kan finde flere oplysninger og konfigurationsvejledning i [Oversigt over onboarding af macOS-enheder i Microsoft 365 (prøveversion).](device-onboarding-macos-overview.md)

### <a name="indicator-level-settings-preview"></a>Indstillinger for indikatorniveau (prøveversion)

Når du opretter en politik i politikguiden, kan du konfigurere, hvordan det daglige antal risikohændelser skal påvirke risikoscoren for insiderrisikobeskeder. Disse indikatorindstillinger hjælper dig med at styre, hvordan antallet af forekomster af risikohændelser i din organisation skal påvirke risikoscoren og dermed den tilknyttede alvorsgrad for disse hændelser. Hvis du foretrækker det, kan du også vælge at beholde de standardtærskelniveauer for hændelser, der anbefales af Microsoft, for alle aktiverede indikatorer.

Du beslutter f.eks. at aktivere SharePoint-indikatorer i indstillingerne for insiderrisikopolitik og **at angive brugerdefinerede tærskler** for SharePoint-hændelser, når du konfigurerer indikatorer for en ny politik for insiderrisikoDatalækager. I guiden til insiderrisikopolitik konfigurerer du tre forskellige daglige hændelsesniveauer for hver SharePoint-indikator for at påvirke risikoscoren for beskeder, der er knyttet til disse hændelser.

![Brugerdefinerede indikatorindstillinger for styring af insiderrisiko.](../media/insider-risk-custom-indicators.png)

For det første daglige hændelsesniveau angiver du tærsklen til *10 eller flere hændelser pr. dag* for en lavere indvirkning på risikoscoren for hændelserne, *20 eller flere hændelser pr. dag* for en mellemstor påvirkning af risikoscoren for hændelserne, og *30 eller flere hændelser pr. dag* en højere indvirkning på risikoscoren for hændelserne. Disse indstillinger betyder på effektiv vis:

- Hvis der er 1-9 SharePoint-hændelser, der finder sted efter udløsende hændelse, påvirkes risikoscore minimalt og vil have en tendens til ikke at generere en besked.
- Hvis der er 10-19 SharePoint-hændelser, der finder sted efter en udløsende hændelse, er risikoscoren i sagens natur lavere, og alvorlighedsniveauer for beskeder vil have en tendens til at være på et lavt niveau.
- Hvis der er 20-29 SharePoint-hændelser, der finder sted efter en udløsning, er risikoscoren i sagens natur højere, og alvorlighedsniveauer for beskeder vil have en tendens til at være på et mellemstort niveau.
- Hvis der er 30 eller flere SharePoint-hændelser, der finder sted efter en udløsning, er risikoscoren i sagens natur højere, og alvorsgradsniveauerne for beskeder vil have en tendens til at være på et højt niveau.

En anden mulighed for politiktærskler er at tildele den hændelse, der udløser politikken, til aktiviteter, der er over det normale antal daglige aktiviteter for brugere. I stedet for at være defineret af specifikke indstillinger for tærskelværdi, tilpasses hver tærskel dynamisk for uregelmæssige aktiviteter, der registreres for brugere af politikker i området. Hvis tærskelaktivitet for unormale aktiviteter understøttes for en individuel indikator, kan du vælge **Aktivitet er over brugerens normale aktivitet for dagen** i politikguiden for den pågældende indikator. Hvis denne indstilling ikke er angivet, er udløseren af unormal aktivitet ikke tilgængelig for indikatoren. Hvis **aktiviteten er over brugerens sædvanlige aktivitet for dagen** er angivet for en indikator, men ikke kan vælges, skal du aktivere denne indstilling i **Insider-risikoindstillinger** > **Politikindikatorer**.

## <a name="policy-timeframes"></a>Politiktidsrammer

Med politiktidsrammer kan du definere tidligere og fremtidige evalueringsperioder, der udløses efter politikkampe baseret på hændelser og aktiviteter for politikskabelonerne for styring af insiderrisiko. Afhængigt af den politikskabelon du vælger, er følgende politiktidsrammer tilgængelige:

- **Aktiveringsvindue**: Vinduet *Aktivering* er tilgængeligt for alle politikskabeloner og er det definerede antal dage, som vinduet aktiveres **efter** en udløsende hændelse. Vinduet aktiveres i 1 til 30 dage, efter at der opstår en udløsende hændelse for alle brugere, der er tildelt politikken. Du har f.eks. konfigureret en politik for styring af insiderrisiko og angivet *aktiveringsvinduet* til 30 dage. Der er gået flere måneder, siden du konfigurerede politikken, og der forekommer en udløsende hændelse for en af de brugere, der er inkluderet i politikken. Udløserhændelsen aktiverer *aktiveringsvinduet* , og politikken er aktiv for den pågældende bruger i 30 dage, efter at udløserhændelsen fandt sted.
- **Registrering af tidligere aktiviteter**: Tilgængelig for alle politikskabeloner. *Registrering af tidligere aktivitet* er det definerede antal dage, som vinduet aktiverer **før** en udløsende hændelse. Vinduet aktiveres i 0 til 90 dage, før der opstår en udløsende hændelse for en bruger, der er tildelt politikken. Du har f.eks. konfigureret en politik for styring af insiderrisiko og angivet *registrering af tidligere aktiviteter* til 90 dage. Der er gået flere måneder, siden du konfigurerede politikken, og der forekommer en udløsende hændelse for en af de brugere, der er inkluderet i politikken. Den udløsende hændelse aktiverer *registreringen af tidligere aktiviteter* , og politikken indsamler historiske aktiviteter for den pågældende bruger i 90 dage før udløserhændelsen.

![Indstillinger for styring af insiderrisiko.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Intelligente registreringer

Intelligente indstillinger for registrering hjælper med at tilpasse, hvordan registreringer af risikable aktiviteter behandles for beskeder. I visse tilfælde skal du muligvis definere filtyper, der skal ignoreres, eller du vil gennemtvinge et registreringsniveau for daglige hændelser for at øge risikoscores for brugerne. Brug disse indstillinger til at styre undtagelser for filtyper, øge risikoscore for usædvanlig aktivitet og grænser for filmængde.

### <a name="file-type-exclusions"></a>Undtagelser for filtype

Hvis du vil udelade bestemte filtyper fra alle matchning af politikker for styring af insiderrisiko, skal du angive filtypeudvidelser adskilt af kommaer. Hvis du f.eks. vil udelade visse typer musikfiler fra politikmatches, kan du angive *aac,mp3,wav,wma* i feltet **Filtypeudeladelser** . Filer med disse udvidelser ignoreres af alle politikker for styring af insiderrisiko.

### <a name="minimum-number-of-daily-events-to-boost-score-for-unusual-activity"></a>Minimum antal daglige hændelser for at øge scoren for usædvanlig aktivitet

Med denne indstilling kan du definere, hvor mange daglige hændelser der kræves for at øge risikoscoren for aktiviteter, der anses for at være usædvanlige for en bruger. Lad os f.eks. sige, at du angiver 25 for denne risikobooster. Hvis en bruger i gennemsnit har downloadet 10 filer i løbet af de seneste 30 dage, men en politik registrerer, at de har downloadet 20 filer på én dag, øges scoren for denne aktivitet ikke, selvom det er usædvanligt for den pågældende bruger, fordi antallet af filer, de downloadede den pågældende dag, var mindre end det antal, du har angivet for denne risikobooster.

### <a name="alert-volume"></a>Beskedmængde

Brugeraktiviteter, der registreres af insiderrisikopolitikker, tildeles en bestemt risikoscore, som igen bestemmer alvorsgraden af beskeden (lav, mellem, høj). Som standard genererer vi en vis mængde beskeder om lav, mellem og høj alvorsgrad, men du kan øge eller reducere mængden, så den passer til dine behov. Hvis du vil justere mængden af beskeder for alle politikker for styring af insiderrisiko, skal du vælge en af følgende indstillinger:

- **Færre beskeder**: Du kan se alle vigtige beskeder med høj alvorsgrad, færre beskeder med mellemhøj alvorsgrad og ingen beskeder med lav alvorsgrad. Dette indstillingsniveau betyder, at du kan gå glip af nogle sande positiver.
- **Standardmængde**: Du kan se alle vigtige beskeder med høj alvorsgrad og en afbalanceret mængde beskeder med mellemstor og lav alvorsgrad.
- **Flere beskeder**: Du kan se alle beskeder med mellemstor og høj alvorsgrad og beskeder med den laveste alvorsgrad. Dette indstillingsniveau kan resultere i flere falske positiver.

### <a name="microsoft-defender-for-endpoint-preview"></a>Microsoft Defender for Endpoint (prøveversion)

[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) er en sikkerhedsplatform til virksomhedsslutpunkter, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. Hvis du vil have bedre synlighed af sikkerhedsovertrædelser i din organisation, kan du importere og filtrere Defender for Endpoint-beskeder for aktiviteter, der bruges i politikker, der er oprettet ud fra skabeloner til sikkerhedsovertrædelse for insiderrisikostyring.

Afhængigt af de typer signaler, du er interesseret i, kan du vælge at importere beskeder til styring af insiderrisiko baseret på status for besked triage i Defender for Endpoint. Du kan definere en eller flere af følgende statusser for vigtige beskeder i de globale indstillinger, der skal importeres:

- Unknown
- Nye
- Igangværende
- Løst

Beskeder fra Defender for Endpoint importeres dagligt. Afhængigt af den triagestatus, du vælger, kan du se flere brugeraktiviteter for den samme besked, som triagestatussen ændres i Defender for Endpoint.

Hvis du f.eks. vælger *Ny*, *Igangværende* og *Løst* for denne indstilling, når der genereres en Microsoft Defender for Endpoint besked, og statussen er *Ny*, importeres en indledende beskedaktivitet for brugeren med insiderrisiko. Når status for Defender for Endpoint ændres til *Igangværende*, importeres der endnu en aktivitet for denne besked for den bruger, der er i insiderrisiko. Når den endelige defender for endpoint-triagestatus for *Løst* er angivet, importeres der en tredje aktivitet for denne besked for den bruger, der er i insiderrisiko. Denne funktionalitet gør det muligt for efterforskere at følge forløbet af Defender for Endpoint-beskederne og vælge det synlighedsniveau, som undersøgelsen kræver.

> [!IMPORTANT]
> Du skal have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan finde flere oplysninger om konfiguration af Defender for Endpoint til integration af styring af insiderrisiko under [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Domæner

Domæneindstillinger hjælper dig med at definere risikoniveauer for aktiviteter til bestemte domæner. Disse aktiviteter omfatter deling af filer, afsendelse af mails, download eller upload af indhold. Ved at angive domæner i disse indstillinger kan du øge eller reducere risikoscoren for aktiviteter, der finder sted med disse domæner.

Brug Tilføj domæne til at definere et domæne for hver af domæneindstillingerne. Du kan også bruge jokertegn til at matche variationer af roddomæner eller underdomæner. Hvis du f.eks. vil angive sales.wingtiptoys.com og support.wingtiptoys.com, skal du bruge jokertegnposten '*.wingtiptoys.com' til at matche disse underdomæner (og alle andre underdomæner på samme niveau). Hvis du vil angive underdomæner på flere niveauer for et roddomæne, skal du markere afkrydsningsfeltet **Medtag underdomæner med flere niveauer** .

For hver af følgende domæneindstillinger kan du angive op til 500 domæner:

- **Ikke-tilladte domæner:** Ved at angive ikke-tilladte domæner vil aktiviteter, der finder sted med disse domæner, have *højere* risikoscores. Nogle eksempler er aktiviteter, der involverer deling af indhold med en person (f.eks. afsendelse af mail til en person med en gmail.com adresse), og når brugerne downloader indhold til en enhed fra et af disse ikke-tilladte domæner.
- **Tilladte domæner:** Visse aktiviteter, der er relateret til tilladte domæner, ignoreres af dine politikker og genererer ikke beskeder. Disse aktiviteter omfatter:

    - Mail sendt til eksterne domæner
    - Filer, mapper, websteder, der deles med eksterne domæner
    - Filer, der er overført til eksterne domæner (ved hjælp af Microsoft Edge-browser)

    Ved at angive tilladte domæner i indstillinger behandles denne aktivitet med disse domæner på samme måde, som intern organisationsaktivitet behandles. Domæner, der føjes her kort til aktiviteter, kan f.eks. omfatte deling af indhold med nogen uden for din organisation (f.eks. afsendelse af mail til en person med en gmail.com adresse).

- **Tredjepartsdomæner:** Hvis din organisation bruger tredjepartsdomæner til forretningsmæssige formål (f.eks. cloudlager), skal du inkludere dem her, så du kan modtage beskeder om aktivitet, der er relateret til enhedsindikatoren *Brug en browser til at downloade indhold fra et tredjepartswebsted*.

## <a name="export-alerts"></a>Eksportér beskeder

Beskedoplysninger om styring af insiderrisiko kan eksporteres til SIEM-løsninger (Security Information Information and Event Management) og SOAR-løsninger (Security Orchestration Automated Response) ved hjælp af [API-skemaet for Office 365 Management Activity](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema). Du kan bruge API'erne til administration af Office 365 til at eksportere beskedoplysninger til andre programmer, som din organisation kan bruge til at administrere eller samle oplysninger om insiderrisiko. Beskedoplysninger eksporteres og er tilgængelige hvert 60. minut via API'erne til administration af Office 365.

Hvis din organisation bruger Microsoft Sentinel, kan du også bruge den indbyggede connector til styring af insiderrisikodata til at importere oplysninger om insiderrisikobeskeder til Sentinel. Du kan få flere oplysninger i [IRM (Insider Risk Management) (Preview)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) i artiklen Microsoft Sentinel.

>[!IMPORTANT]
>Hvis du vil bevare referentiel integritet for brugere, der har insiderrisikobeskeder eller -sager i Microsoft 365 eller andre systemer, bevares anonymisering af brugernavne ikke for eksporterede beskeder. Eksporterede beskeder viser brugernavne for hver besked.

Sådan bruger du API'erne til at gennemse oplysninger om insiderrisikobeskeder:

1. Aktivér understøttelse af API til administration af Office 365 i **Indstillinger for** >  **styring af** >  insiderrisiko **Eksportér beskeder**. Denne indstilling er som standard deaktiveret for din Microsoft 365-organisation.
2. Filtrer de almindelige Office 365 overvågningsaktiviteter efter *SecurityComplianceAlerts*.
3. Filtrer *SecurityComplianceAlerts* efter kategorien *InsiderRiskManagement* .

![Indstillinger for eksport af vigtige beskeder til styring af insiderrisiko.](../media/insider-risk-settings-export.png)

Beskedoplysninger indeholder oplysninger fra skemaet for sikkerheds- og overholdelsesbeskeder og det fælles skema Office 365 Management Activity API.

Følgende felter og værdier eksporteres til insiderrisikostyringsbeskeder for skemaet sikkerheds- & overholdelsesadvarsel:

| **Beskedparameter** | **Beskrivelse** |
|:------------------|:----------------|
| AlertType | Typen af beskeden er *brugerdefineret*.  |
| Besked-id | BESKEDENS GUID. Beskeder om styring af insiderrisiko kan slås fra. Når beskedstatus ændres, oprettes der en ny log med det samme AlertID. Dette AlertID kan bruges til at korrelere opdateringer for en besked. |
| Kategori | Kategorien for beskeden er *InsiderRiskManagement*. Denne kategori kan bruges til at skelne fra disse beskeder fra andre sikkerheds- & beskeder om overholdelse af angivne standarder. |
| Kommentarer | Standardkommentarer for beskeden. Værdier er *Ny besked* (logført, når der oprettes en besked) og *Besked opdateret* (logført, når der er en opdatering til en besked). Brug AlertID til at korrelere opdateringer for en besked. |
| Data | Dataene for beskeden indeholder det entydige bruger-id, brugerens hovednavn og dato og klokkeslæt (UTC), da brugeren blev udløst i en politik. |
| Navn | Politiknavn for politikken for styring af insiderrisiko, der genererede beskeden. |
| PolicyId | GUID'et for politikken for styring af insiderrisiko, der udløste beskeden. |
| Sværhedsgraden | Alvorsgraden af beskeden. Værdierne er *Høj*, *Mellem* eller *Lav*. |
| Kilde | Kilden til beskeden. Værdien er *Office 365 Security & Compliance*. |
| Status | Status for beskeden. Værdier er *aktive* (*kræver gennemgang* i insiderrisiko), *undersøgelse* (*bekræftet* i insiderrisiko), *Løst* (*løst* i insiderrisiko), *Afvist* (*afvist* i insiderrisiko). |
| Version | Versionen af skemaet for sikkerheds- og overholdelsesbeskeder. |

Følgende felter og værdier eksporteres til insiderrisikostyringsbeskeder for det [fælles skema Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema).

- Userid
- Id
- Posttype
- Oprettelsestid
- Drift
- Organisations-id
- UserType
- UserKey

## <a name="priority-user-groups-preview"></a>Prioriterede brugergrupper (prøveversion)

Brugere i din organisation kan have forskellige risikoniveauer, afhængigt af deres placering, adgangsniveau til følsomme oplysninger eller risikohistorik. Prioritering af undersøgelse og scoring af disse brugeres aktiviteter kan hjælpe dig med at advare dig om potentielle risici, der kan have højere konsekvenser for din organisation. Prioriterede brugergrupper i styring af insiderrisiko hjælper med at definere de brugere i organisationen, der har brug for mere kontrol og mere følsom risikoscore. Sammen med politikskabelonerne *for sikkerhedspolitikovertrædelser af prioriterede brugere* og *datalækager fra prioriterede brugere* har brugere, der føjes til en prioriteret brugergruppe, øget sandsynlighed for insiderrisikobeskeder og beskeder med højere alvorsgradsniveauer.

![Indstillinger for brugergruppeprioritet for styring af insiderrisiko.](../media/insider-risk-settings-priority-users.png)

I stedet for at være åbne for gennemgang af alle analytikere og efterforskere kan prioritetsbrugergrupper også være nødt til at begrænse korrekturaktiviteter til bestemte brugere eller insiderrisikorollegrupper. Du kan vælge at tildele individuelle brugere og rollegrupper til at gennemse brugere, beskeder, sager og rapporter for hver prioriteret brugergruppe. Prioritetsbrugergrupper kan have tilladelse til at gennemse de indbyggede rollegrupper *Insider Risk Management*, *Insider Risk Management Og* *Insider Risk Management Investigators* , en eller flere af disse rollegrupper eller til et brugerdefineret udvalg af brugere.

Du skal f.eks. beskytte mod datalækager for et meget fortroligt projekt, hvor brugerne har adgang til følsomme oplysninger. Du vælger at oprette en brugergruppe med *prioriteten Fortrolige projektbrugere*  for brugere i din organisation, der arbejder på dette projekt. Desuden bør denne prioriterede brugergruppe ikke have brugere, beskeder, sager og rapporter, der er knyttet til gruppen, synlige for alle standardadministratorer, analytikere og efterforskere af insiderrisikostyring. Under **Indstillinger** kan du oprette gruppen *Fortrolige projektbrugeres* prioritetsbrugere og tildele to brugere som korrekturlæser, der kan få vist data, der er relateret til grupperne. Ved hjælp af politikguiden og politikskabelonen *Datalækager efter prioriterede brugere* kan du oprette en ny politik og tildele gruppen *Fortrolige project-brugere* prioritetsbrugere til politikken. Aktiviteter, der undersøges af politikken for medlemmer af den prioriterede brugergruppe *Fortrolige projektbrugere* , er mere følsomme over for risici, og der vil være større sandsynlighed for, at disse brugere vil generere en besked og have beskeder med højere alvorsgradsniveauer.

### <a name="create-a-priority-user-group"></a>Opret en prioritetsbrugergruppe

Hvis du vil oprette en ny prioriteret brugergruppe, skal du bruge indstillingskontrolelementer i **insiderrisikoadministrationsløsningen** i Microsoft Purview-compliance-portal. Hvis du vil oprette en prioriteret brugergruppe, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*.

Fuldfør følgende trin for at oprette en prioriteret brugergruppe:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af Insider-risici** og vælge **Indstillinger for insiderrisiko**.
2. Vælg siden **Prioritetsbrugergrupper (prøveversion).**
3. På siden **Prioritetsbrugergrupper (prøveversion)** skal du vælge **Opret brugergruppe med prioritet** for at starte guiden til oprettelse af gruppen.
4. Udfyld følgende felter på siden **Navn og beskriv** :
    - **Navn (obligatorisk)**: Angiv et brugervenligt navn til den prioriterede brugergruppe. Du kan ikke ændre navnet på den prioriterede brugergruppe, når du har fuldført guiden.
    - **Beskrivelse (valgfrit)**: Angiv en beskrivelse af den prioriterede brugergruppe.
5. Vælg **Næste** for at fortsætte.
6. På siden **Vælg medlemmer** skal du vælge **Vælg medlemmer** , der skal søges efter, og vælge, hvilke mailaktiverede brugerkonti der skal medtages i gruppen, eller markér afkrydsningsfeltet **Markér alle** for at føje alle brugere i din organisation til gruppen. Vælg **Tilføj** for at fortsætte, eller vælg **Annuller** for at lukke uden at føje brugere til gruppen.
7. Vælg **Næste** for at fortsætte.
8. På siden **Vælg, hvem der kan få vist denne gruppe** skal du definere, hvem der kan gennemse brugere, beskeder, sager og rapporter for den prioriterede brugergruppe. Der skal tildeles mindst én rollegruppe for bruger- eller insiderrisikostyring. Vælg **Vælg brugere og rollegrupper** , og vælg de brugere eller rollegrupper for styring af insiderrisiko, du vil tildele til den prioriterede brugergruppe. Vælg **Tilføj** for at tildele de valgte brugere eller rollegrupper til gruppen.
9. Vælg Næste for at fortsætte.
10. Gennemse de indstillinger, du har valgt for den prioriterede brugergruppe, på siden **Gennemse** . Vælg **Rediger** links for at ændre en af gruppeværdierne, eller vælg **Send** for at oprette og aktivere den prioriterede brugergruppe.
11. Vælg **Udført** på bekræftelsessiden for at afslutte guiden.

### <a name="update-a-priority-user-group"></a>Opdater en prioritetsbrugergruppe

Hvis du vil opdatere en eksisterende prioriteret brugergruppe, skal du bruge indstillingskontrolelementer i **insiderrisikoadministrationsløsningen** i Microsoft Purview-compliance-portal. Hvis du vil opdatere en prioriteret brugergruppe, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*.

Fuldfør følgende trin for at redigere en prioriteret brugergruppe:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af Insider-risici** og vælge **Indstillinger for insiderrisiko**.
2. Vælg siden **Prioritetsbrugergrupper (prøveversion).**
3. Vælg den prioritetsbrugergruppe, du vil redigere, og vælg **Rediger gruppe**.
4. Opdater eventuelt feltet Beskrivelse på siden **Navn og beskriv** . Du kan ikke opdatere navnet på den prioriterede brugergruppe. Vælg **Næste** for at fortsætte.
5. På siden **Vælg medlemmer** skal du føje nye medlemmer til gruppen ved hjælp af kontrolelementet **Vælg medlemmer** . Hvis du vil fjerne en bruger fra gruppen, skal du vælge 'X' ud for den bruger, du vil fjerne. Vælg **Næste** for at fortsætte.
6. På siden **Vælg, hvem der kan få vist denne gruppe skal** du tilføje eller fjerne brugere eller rollegrupper, der kan gennemse brugere, beskeder, sager og rapporter for den prioriterede brugergruppe.
7. Vælg **Næste** for at fortsætte.
8. Gennemse de opdateringsindstillinger, du har valgt for den prioriterede brugergruppe, på siden **Gennemse** . Vælg **Rediger** links for at ændre en af gruppeværdierne, eller vælg **Send** for at opdatere den prioriterede brugergruppe.
9. Vælg **Udført** på bekræftelsessiden for at afslutte guiden.

### <a name="delete-a-priority-user-group"></a>Slet en prioritetsbrugergruppe

Hvis du vil slette en eksisterende prioriteret brugergruppe, skal du bruge indstillingskontrolelementer i løsningen **Insider Risk Management** i Microsoft Purview-compliance-portal. Hvis du vil slette en prioriteret brugergruppe, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*.

> [!IMPORTANT]
> Hvis du sletter en prioriteret brugergruppe, fjernes den fra alle aktive politikker, som den er tildelt. Hvis du sletter en prioriteret brugergruppe, der er tildelt til en aktiv politik, indeholder politikken ingen brugere i området og vil være inaktiv og vil ikke oprette beskeder.

Fuldfør følgende trin for at slette en prioriteret brugergruppe:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af Insider-risici** og vælge **Indstillinger for insiderrisiko**.
2. Vælg siden **Prioritetsbrugergrupper (prøveversion).**
3. Vælg den prioritetsbrugergruppe, du vil redigere, og vælg **Slet** i dashboardmenuen.
4. I dialogboksen **Slet** skal du vælge **Ja** for at slette den prioriterede brugergruppe eller vælge **Annuller** for at vende tilbage til dashboardet.

## <a name="priority-physical-assets-preview"></a>Prioriterede fysiske aktiver (prøveversion)

Identificering af adgang til prioriterede fysiske aktiver og korrelering af adgangsaktivitet til brugerhændelser er en vigtig komponent i din infrastruktur for overholdelse af angivne standarder. Disse fysiske aktiver repræsenterer prioriterede placeringer i din organisation, f.eks. virksomhedsbygninger, datacentre eller serverrum. Insiderrisikoaktiviteter kan være forbundet med brugere, der arbejder usædvanligt i timer, og forsøger at få adgang til disse uautoriserede følsomme eller sikre områder og anmodninger om adgang til områder på højt niveau uden legitime behov.

Når prioriteten af fysiske aktiver er aktiveret, og [dataconnectoren til fysisk badging](import-physical-badging-data.md) er konfigureret, integrerer styring af insiderrisiko signaler fra din fysiske kontrol og adgangssystemer med andre aktiviteter for brugerrisiko. Ved at undersøge adfærdsmønstre på tværs af fysiske adgangssystemer og korrelere disse aktiviteter med andre insiderrisikohændelser kan styring af insiderrisiko hjælpe med at fastslå overholdelse af angivne standarder og analytikere træffe mere informerede svarbeslutninger for beskeder. Adgang til prioriterede fysiske aktiver bedømmes og identificeres i indsigter på en anden måde end adgang til ikke-prioriterede aktiver.

Din organisation har f.eks. et badgingsystem for brugere, der styrer og godkender fysisk adgang til normale arbejds- og følsomme projektområder. Du har flere brugere, der arbejder på et følsomt projekt, og disse brugere vender tilbage til andre områder i organisationen, når projektet er fuldført. Da det følsomme projekt er ved at blive fuldført, skal du sikre dig, at projektarbejde forbliver fortroligt, og at adgangen til projektområderne styres nøje.

Du vælger at aktivere connectoren Fysisk badging-data i Microsoft 365 for at importere adgangsoplysninger fra dit fysiske badgingsystem og angive prioriterede fysiske aktiver i styring af insiderrisiko. Når du importerer oplysninger fra dit badgingsystem og korrelerer oplysninger om fysisk adgang med andre risikoaktiviteter, der er identificeret i insiderrisikostyring, bemærker du, at en af brugerne på projektet tilgår projektkontorerne efter normal arbejdstid og eksporterer også store mængder data til en personlig cloudlagertjeneste fra deres normale arbejdsområde. Denne fysiske adgangsaktivitet, der er knyttet til onlineaktiviteten, kan pege på mulige datatyveri og overholdelse af angivne standarder, som efterforskere og analytikere kan udføre relevante handlinger i henhold til omstændighederne for denne bruger.

![Insiderrisikostyring prioriterede fysiske aktiver.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Konfigurer prioriterede fysiske aktiver

Hvis du vil konfigurere prioriterede fysiske aktiver, skal du konfigurere connectoren Physical badging og bruge indstillingskontrolelementer i **Insider Risk Management-løsningen** i Microsoft Purview-compliance-portal. Hvis du vil konfigurere prioriterede fysiske aktiver, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*.

Udfør følgende trin for at konfigurere prioriterede fysiske aktiver:

1. Følg konfigurationstrinnene for styring af insiderrisiko i artiklen [Introduktion til styring af insiderrisiko](insider-risk-management-configure.md) . I trin 3 skal du sørge for at konfigurere connectoren Physical badging.

    > [!IMPORTANT]
    > Hvis politikker for styring af insiderrisiko skal bruge og korrelere signaldata, der er relateret til afrejsende og afbrudte brugere med hændelsesdata fra dine fysiske kontrol- og adgangsplatforme, skal du også konfigurere Microsoft 365 HR-connectoren. Hvis du aktiverer den fysiske badging-connector uden at aktivere Microsoft 365 HR-connectoren, behandler politikker for styring af insiderrisiko kun hændelser for fysiske adgangsaktiviteter for brugere i din organisation.

2. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af Insider-risici** og vælge **Indstillinger for** >  insiderrisiko **Prioritet af fysiske aktiver**.
3. På siden **Prioritet af fysiske aktiver** kan du enten manuelt tilføje de fysiske aktiv-id'er, du vil registrere aktivhændelser, der importeres af connectoren fysisk badging, eller importere en .csv fil med alle fysiske aktiv-id'er, der er importeret af connectoren Fysisk badging: a) Hvis du vil tilføje id'er for fysiske aktiver manuelt, skal du vælge **Tilføj prioriterede fysiske aktiver**, angive et id for et fysisk aktiv,  vælg derefter **Tilføj**. Angiv andre fysiske aktiv-id'er, og vælg derefter **Tilføj prioriterede fysiske aktiver** for at gemme alle de angivne aktiver.
    b) Hvis du vil tilføje en liste over id'er for fysiske aktiver fra en .csv-fil, skal du vælge **Importér prioriterede fysiske aktiver**. Vælg den .csv fil, du vil importere, i dialogboksen Stifinder, og vælg derefter **Åbn**. Id'erne for de fysiske aktiver fra de .csv filer føjes til listen.
4. Gå til siden **Politikindikatorer** i **Indstillinger**.
5. På siden **Politikindikatorer** skal du navigere til afsnittet **Fysiske adgangsindikatorer** og markere afkrydsningsfeltet for **Fysisk adgang efter afslutning eller mislykket adgang til følsomt aktiv**.
6. Vælg **Gem** for at konfigurere og afslutte.

### <a name="delete-a-priority-physical-asset"></a>Slet et prioriteret fysisk aktiv

Hvis du vil slette et eksisterende prioriteret fysisk aktiv, skal du bruge indstillingskontrolelementer i løsningen til styring af insiderrisiko i Microsoft Purview-compliance-portal. Hvis du vil slette et prioriteret fysisk aktiv, skal du være medlem af rollegruppen Insider Risk Management eller Insider Risk Management Administration.

> [!IMPORTANT]
> Hvis du sletter et prioriteret fysisk aktiv, fjernes det fra undersøgelse af en aktiv politik, som det tidligere blev inkluderet i. Beskeder, der genereres af aktiviteter, der er knyttet til det prioriterede fysiske aktiv, slettes ikke.

Fuldfør følgende trin for at slette et prioriteret fysisk aktiv:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af Insider-risici** og vælge **Indstillinger for** >  insiderrisiko **Prioritet af fysiske aktiver**.
2. Vælg det aktiv, du vil slette, på siden **Prioritet for fysiske aktiver** .
3. Vælg **Slet** i handlingsmenuen for at slette aktivet.

## <a name="power-automate-flows-preview"></a>Power Automate-flow (prøveversion)

[Microsoft Power Automate](/power-automate/getting-started) er en arbejdsprocestjeneste, der automatiserer handlinger på tværs af programmer og tjenester. Ved hjælp af flow fra skabeloner eller oprettet manuelt kan du automatisere almindelige opgaver, der er knyttet til disse programmer og tjenester. Når du aktiverer Power Automate-flow til styring af insiderrisiko, kan du automatisere vigtige opgaver for sager og brugere. Du kan konfigurere Power Automate-flow for at hente bruger-, besked- og sagsoplysninger og dele disse oplysninger med interessenter og andre programmer samt automatisere handlinger i styring af insiderrisiko, f.eks. at sende noter til sag. Power Automate-flow er gældende for sager og alle brugere, der er omfattet af en politik.

Kunder med Microsoft 365-abonnementer, der indeholder insiderrisikostyring, behøver ikke yderligere Power Automate-licenser for at bruge de anbefalede skabeloner til styring af insiderrisikostyring i Power Automate. Disse skabeloner kan tilpasses for at understøtte din organisation og dække kernescenarier for styring af insiderrisiko. Hvis du vælger at bruge Premium Power Automate-funktioner i disse skabeloner, oprette en brugerdefineret skabelon ved hjælp af Microsoft Purview-connectoren eller bruge Power Automate-skabeloner til andre overholdelsesområder i Microsoft 365, har du muligvis brug for flere Power Automate-licenser.

Følgende Power Automate-skabeloner leveres til kunder for at understøtte procesautomatisering for brugere og sager til styring af insiderrisiko:

- **Giv brugerne besked, når de føjes til en insiderrisikopolitik**: Denne skabelon er til organisationer, der har interne politikker, beskyttelse af personlige oplysninger eller lovmæssige krav, som brugerne skal have besked om, når de er underlagt politikker for styring af insiderrisiko. Når dette flow er konfigureret og valgt for en bruger på siden **Brugere** , sendes brugerne og deres ledere en mail, når brugeren føjes til en insiderrisikostyringspolitik. Denne skabelon understøtter også opdatering af en SharePoint-liste, der hostes på et SharePoint-websted, for at hjælpe med at spore meddelelsesoplysninger, f.eks. dato/klokkeslæt og meddelelsens modtager. Hvis du har valgt at anonymisere brugere under **Indstillinger for beskyttelse af personlige oplysninger**, fungerer de flow, der oprettes ud fra denne skabelon, ikke som tiltænkt, så brugernes beskyttelse af personlige oplysninger bevares. Power Automate-flow, der bruger denne skabelon, er tilgængelige på **dashboardet Brugere**.
- **Anmod HR eller virksomheden om en bruger i en insiderrisikosag**: Når der reageres på en sag, kan insiderrisikoanalytikere og efterforskere være nødt til at rådføre sig med HR eller andre interessenter for at forstå konteksten for sagsaktiviteterne. Når dette flow er konfigureret og valgt for en sag, sender analytikere og efterforskere en mail til HR- og forretningsinteressenter, der er konfigureret for dette flow. Hver modtager får tilsendt en meddelelse med forudkonfigurerede eller tilpassede svarindstillinger. Når modtagerne vælger en svarindstilling, registreres svaret som en sagsnote og indeholder oplysninger om modtager og dato/klokkeslæt. Hvis du har valgt at anonymisere brugere under **Indstillinger for beskyttelse af personlige oplysninger**, fungerer de flow, der oprettes ud fra denne skabelon, ikke som tiltænkt, så brugernes beskyttelse af personlige oplysninger bevares. Power Automate-flow, der bruger denne skabelon, er tilgængelige på **dashboardet Sager**.
- **Giv lederen besked, når en bruger har en insiderrisikobesked**: Nogle organisationer skal muligvis have en øjeblikkelig besked om administration, når en bruger har en insiderrisikostyringsadvarsel. Når dette flow er konfigureret og valgt, sendes der en mail til sagsbrugerens chef med følgende oplysninger om alle sagsbeskeder:
    - Gældende politik for beskeden
    - Dato/klokkeslæt for beskeden
    - Alvorsgrad for beskeden

    Flowet opdaterer automatisk sagen og bemærker, at meddelelsen blev sendt, og at flowet blev aktiveret. Hvis du har valgt at anonymisere brugere under **Indstillinger for beskyttelse af personlige oplysninger**, fungerer de flow, der oprettes ud fra denne skabelon, ikke som tiltænkt, så brugernes beskyttelse af personlige oplysninger bevares. Power Automate-flow, der bruger denne skabelon, er tilgængelige på **dashboardet Sager**.
- **Opret en post for insiderrisikocase i ServiceNow**: Denne skabelon er til organisationer, der vil bruge deres ServiceNow-løsning til at spore insiderrisikostyringssager.  Når insiderrisikoanalytikere og efterforskere i en sag kan oprette en post for sagen i ServiceNow. Du kan tilpasse denne skabelon for at udfylde de valgte felter i ServiceNow på baggrund af din organisations krav. Power Automate-flow, der bruger denne skabelon, er tilgængelige på **dashboardet Sager**. Du kan få flere oplysninger om tilgængelige ServiceNow-felter i [referenceartiklen ServiceNow Connector](/connectors/service-now/) .

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Opret et Power Automate-flow fra skabelonen styring af insiderrisiko

Hvis du vil oprette et Power Automate-flow fra en anbefalet skabelon til styring af insiderrisiko, skal du bruge indstillingskontrolelementerne i **insiderrisikoadministrationsløsningen** i Microsoft Purview-compliance-portal eller indstillingen **Administrer Power Automate-flow** fra kontrolelementet **Automate**, når du arbejder direkte i **dashboards** for **sager** eller brugere.

Hvis du vil oprette et Power Automate-flow i indstillingsområdet, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. Hvis du vil oprette et Power Automate-flow med indstillingen **Administrer Power Automate-flow** , skal du være medlem af mindst én rollegruppe for styring af insiderrisiko.

Fuldfør følgende trin for at oprette et Power Automate-flow fra en anbefalet skabelon til styring af insiderrisiko:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge **Indstillinger for** >  insiderrisiko **Power Automate-flow**. Du kan også få adgang fra **dashboardsiderne** **Sager** eller Brugere ved at vælge **Automatiser** > **Administrer Power Automate-flow**.
2. På siden **Power Automate-flow** skal du vælge en anbefalet skabelon i afsnittet **Insider Risk Management-skabeloner, som du kan synes godt om** på siden.
3. Flowet viser de integrerede forbindelser, der er nødvendige for flowet, og vil bemærke, om forbindelsesstatusserne er tilgængelige. Opdater eventuelle forbindelser, der ikke vises som tilgængelige, hvis det er nødvendigt. Vælg **Fortsæt**.
4. De anbefalede flow er som standard forudkonfigureret med den anbefalede styring af insiderrisiko og datafelter i Microsoft 365-tjenesten, der kræves for at fuldføre den tildelte opgave for flowet. Tilpas om nødvendigt flowkomponenterne ved hjælp af kontrolelementet **Vis avancerede indstillinger** og konfiguration af de tilgængelige egenskaber for flowkomponenten.
5. Hvis det er nødvendigt, kan du føje andre trin til flowet ved at vælge knappen **Nyt trin** . I de fleste tilfælde bør dette ikke være nødvendigt for de anbefalede standardskabeloner.
6. Vælg **Gem kladde** for at gemme flowet for yderligere konfiguration, eller vælg **Gem** for at fuldføre konfigurationen af flowet.
7. Vælg **Luk** for at vende tilbage til siden **Power Automate-flow** . Den nye skabelon vises som et flow under fanerne **Mine flow** og er automatisk tilgængelig via kontrolelementet **Automate** , når der arbejdes med insiderrisikostyringssager for den bruger, der opretter flowet.

> [!IMPORTANT]
> Hvis andre brugere i organisationen skal have adgang til flowet, skal flowet deles.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Opret et brugerdefineret Power Automate-flow til styring af insiderrisiko

Nogle processer og arbejdsprocesser for din organisation kan være uden for de anbefalede skabeloner til styring af insiderrisikostyring, og du har muligvis brug for at oprette brugerdefinerede Power Automate-flow til insiderrisikostyringsområder. Power Automate-flow er fleksible og understøtter omfattende tilpasning, men der er trin, der skal udføres for at integrere med insiderrisikostyringsfunktioner.

Udfør følgende trin for at oprette en brugerdefineret Power Automate-skabelon til styring af insiderrisiko:

1. **Kontrollér din Licens til Power Automate-flow**: Hvis du vil oprette tilpassede Power Automate-flow, der bruger insiderrisikostyringsudløsere, skal du have en Power Automate-licens. De anbefalede flowskabeloner til styring af insiderrisiko kræver ikke ekstra licenser og er inkluderet som en del af din insiderrisikostyringslicens.
2. **Opret et automatiseret flow**: Opret et flow, der udfører en eller flere opgaver, når det udløses af en insiderrisikostyringshændelse. Du kan finde oplysninger om, hvordan du opretter et automatiseret flow, [under Opret et flow i Power Automate](/power-automate/get-started-logic-flow).
3. **Vælg Microsoft Purview-connectoren**: Søg efter, og vælg Microsoft Purview-connectoren. Denne connector aktiverer udløsere og handlinger til styring af insiderrisiko. Du kan få flere oplysninger om connectors i artiklen [Oversigt over connectorreference](/connectors/connector-reference/) .
4. **Vælg insiderrisikostyringsudløsere til dit flow**: Insiderrisikostyring har to tilgængelige udløsere til brugerdefinerede Power Automate-flow:
    - **For en valgt sag om styring af insiderrisiko**: Flow med denne udløser kan vælges på dashboardsiden Sager om insiderrisikostyring.
    - **For en valgt bruger til styring af insiderrisiko**: Flow med denne udløser kan vælges på dashboardsiden Brugere af insiderrisikostyring.
5. Vælg insiderrisikostyringshandlinger for dit flow: Du kan vælge mellem flere handlinger til styring af insiderrisiko, der skal inkluderes i dit brugerdefinerede flow:
    - Få besked om styring af insiderrisiko
    - Få insiderrisikostyringscase
    - Få bruger til styring af insiderrisiko
    - Få insiderrisikostyringsbeskeder for en sag
    - Tilføj note om insiderrisikostyringssag

### <a name="share-a-power-automate-flow"></a>Del et Power Automate-flow

Power Automate-flow, der er oprettet af en bruger, er som standard kun tilgængelige for den pågældende bruger. Hvis andre brugere af styring af insiderrisiko skal have adgang til og bruge et flow, skal flowet deles af opretteren af flowet. Hvis du vil dele et flow, skal du bruge indstillingskontrolelementerne i **løsningen Styring af insiderrisiko** i Microsoft Purview-compliance-portal eller indstillingen **Administrer Power Automate-flow** fra kontrolelementet Automate, når du arbejder direkte på **dashboardsiderne** **Sager** eller Brugere. Når du har delt et flow, kan alle, som det er blevet delt med, få adgang til flowet på rullelisten **Automate-kontrolelementet** på **dashboardene** **Sag** og Bruger.

Hvis du vil dele et Power Automate-flow i indstillingsområdet, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. Hvis du vil dele et Power Automate-flow med indstillingen **Administrer Power Automate-flow** , skal du være medlem af mindst én rollegruppe for styring af insiderrisiko.

Fuldfør følgende trin for at dele et Power Automate-flow:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge **Indstillinger for** >  insiderrisiko **Power Automate-flow**. Du kan også få adgang fra **dashboardsiderne** **Sager** eller Brugere ved at vælge **Automatiser** > **Administrer Power Automate-flow**.
2. På siden **Power Automate-flow** skal du vælge fanen **Mine flow** eller **Teamflow** .
3. Vælg det flow, der skal deles, og vælg derefter **Del** i menuen med flowindstillinger.
4. Angiv navnet på den bruger eller gruppe, du vil tilføje som ejer af flowet, på siden til deling af flowet.
5. I dialogboksen **Forbindelse brugt** skal du vælge **OK** for at bekræfte, at den tilføjede bruger eller gruppe har fuld adgang til flowet.

### <a name="edit-a-power-automate-flow"></a>Rediger et Power Automate-flow

Hvis du vil redigere et flow, skal du bruge indstillingskontrolelementerne i løsningen **Styring af insiderrisiko** i Microsoft Purview-compliance-portal eller indstillingen **Administrer Power Automate-flow** fra kontrolelementet **Automate**, når du arbejder direkte i **dashboards** for **sager** eller brugere.

Hvis du vil redigere et Power Automate-flow i indstillingsområdet, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. Hvis du vil redigere et Power Automate-flow med indstillingen **Administrer Power Automate-flow** , skal du være medlem af mindst én rollegruppe for styring af insiderrisiko.

Fuldfør følgende trin for at redigere et Power Automate-flow:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge **Indstillinger for** >  insiderrisiko **Power Automate-flow**. Du kan også få adgang fra **dashboardsiderne** **Sager** eller Brugere ved at vælge **Automatiser** > **Administrer Power Automate-flow**.
2. På siden **Power Automate-flow** skal du vælge et flow, der skal redigeres, og vælge **Rediger** i menuen til flowstyring.
3. Vælg **ellipseindstillingerne** >  for at ændre indstillingen for en flowkomponent eller **ellipsen** > **Slet** for at slette en flowkomponent.
4. Vælg **Gem** og derefter **Luk** for at fuldføre redigeringen af flowet.

### <a name="delete-a-power-automate-flow"></a>Slet et Power Automate-flow

Hvis du vil slette et flow, skal du bruge indstillingskontrolelementerne i løsningen **Styring af insiderrisiko** i Microsoft Purview-compliance-portal eller indstillingen **Administrer Power Automate-flow** fra kontrolelementet **Automate**, når du arbejder direkte i **dashboards** for **sager** eller brugere. Når et flow slettes, fjernes det som en indstilling for alle brugere.

Hvis du vil slette et Power Automate-flow i indstillingsområdet, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. Hvis du vil slette et Power Automate-flow med indstillingen **Administrer Power Automate-flow** , skal du være medlem af mindst én rollegruppe for styring af insiderrisiko.

Fuldfør følgende trin for at slette et Power Automate-flow:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge **Indstillinger for** >  insiderrisiko **Power Automate-flow**. Du kan også få adgang fra **dashboardsiderne** **Sager** eller Brugere ved at vælge **Automatiser** > **Administrer Power Automate-flow**.
2. På siden **Power Automate-flow** skal du vælge et flow, der skal slettes, og vælge **Slet** i menuen til flowstyring.
3. Vælg **Slet** i bekræftelsesdialogboksen for sletning for at fjerne flowet, eller vælg **Annuller** for at afslutte sletningen.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (prøveversion)

Overholdelsesanalytikere og efterforskere kan nemt bruge Microsoft Teams til at samarbejde om insiderrisikostyringssager. De kan koordinere og kommunikere med andre interessenter i Microsoft Teams for at:

- Koordinere og gennemse svaraktiviteter for sager i private Teams-kanaler
- Sikker deling og lagring af filer og beviser i forbindelse med individuelle sager
- Spor og gennemse svaraktiviteter udført af analytikere og efterforskere

Når Microsoft Teams er aktiveret til styring af insiderrisiko, oprettes der et dedikeret Microsoft Teams-team, hver gang en besked bekræftes, og der oprettes en sag. Som standard inkluderer teamet automatisk alle medlemmer af rollegrupperne *Insider Risk Management*, *Insider Risk Management Analysts* og *Insider Risk Management Investigators* (op til 100 indledende brugere). Yderligere bidragydere til organisationen kan føjes til teamet, når de er oprettet og efter behov. I forbindelse med eksisterende sager, der er oprettet før aktivering af Microsoft Teams, kan analytikere og efterforskere vælge at oprette et nyt Microsoft Teams-team, når de arbejder i en sag, hvis det er nødvendigt.  Når du har løst den tilknyttede sag i styring af insiderrisiko, arkiveres teamet automatisk (flyttet til skjult og skrivebeskyttet).

Du kan få flere oplysninger om, hvordan du bruger teams og kanaler i Microsoft Teams, under [Oversigt over teams og kanaler i Microsoft Teams](/MicrosoftTeams/teams-channels-overview).

Det er hurtigt og nemt at konfigurere aktivering af Microsoft Teams-understøttelse af sager. Hvis du vil aktivere Microsoft Teams til styring af insiderrisiko, skal du udføre følgende trin:

1. I [Microsoft Purview-compliance-portal skal du](https://compliance.microsoft.com) gå til **Insider-risikostyring** > **Indstillinger for Insider-risiko**.
2. Vælg siden **Microsoft Teams** .
3. Aktivér Microsoft Teams-integration til styring af insiderrisiko.
4. Vælg **Gem** for at konfigurere og afslutte.

![Styring af insiderrisiko Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Opret et Microsoft Teams-team til eksisterende sager

Hvis du aktiverer Understøttelse af insiderrisikostyring i Microsoft Teams, når du har eksisterende sager, skal du manuelt oprette et team for hver sag efter behov. Når du har aktiveret Understøttelse af Microsoft Teams i indstillinger for styring af insiderrisiko, opretter nye sager automatisk et nyt Microsoft Teams-team.

Brugerne skal have tilladelse til at oprette Microsoft 365-grupper i din organisation for at oprette et Microsoft Teams-team ud fra en sag. Du kan få flere oplysninger om administration af tilladelser til Microsoft 365-grupper under Administrer, [hvem der kan oprette Microsoft 365-grupper](../solutions/manage-creation-of-groups.md).

Hvis du vil oprette et team til en sag, skal du bruge kontrolelementet Opret Microsoft Team, når du arbejder direkte i en eksisterende sag. Fuldfør følgende trin for at oprette et nyt team:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Sager** om styring af  > **insiderrisiko** og vælge en eksisterende sag.
2. I menuen sagshandling skal du vælge **Opret Microsoft Team**.
3. Angiv et navn til det nye Microsoft **Teams-team i feltet Teamnavn** .
4. Vælg **Opret Microsoft-team,** og vælg derefter **Luk**.

Afhængigt af antallet af brugere, der er tildelt rollegrupper for styring af insiderrisiko, kan det tage 15 minutter, før alle efterforskere og analytikere føjes til Microsoft Teams-teamet for en sag.

## <a name="analytics"></a>Analytics

Insiderrisikoanalyse giver dig mulighed for at evaluere potentielle insiderrisici i din organisation uden at konfigurere nogen politikker for insiderrisiko. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisiko og hjælpe med at bestemme typen og omfanget af politikker for styring af insiderrisiko, som du kan overveje at konfigurere. Analysescanninger giver følgende fordele for din organisation:

- Let at konfigurere: Hvis du vil i gang med analysescanninger, kan du vælge Kør scanning, når du bliver bedt om det af anbefalingerne til analyse, eller gå til **Insider-risikoindstillinger** > **Analytics** og aktivere analyse.
- Beskyttelse af personlige oplysninger efter design: Scanningsresultater og indsigt returneres som aggregeret og anonymiseret brugeraktivitet. Individuelle brugernavne kan ikke identificeres af korrekturlæsere.
- Forstå potentielle risici via konsolideret indsigt: Scanningsresultater kan hjælpe dig med hurtigt at identificere potentielle risikoområder for dine brugere, og hvilken politik der er bedst til at afhjælpe disse risici.

Se [videoen Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) for at få hjælp til at forstå, hvordan analyser kan fremskynde identificeringen af potentielle insiderrisici og hjælpe dig med hurtigt at handle.

Analysescanninger for risikoaktivitetshændelser fra flere kilder for at hjælpe med at identificere indsigt i potentielle risikoområder. Afhængigt af din aktuelle konfiguration søger analyse efter kvalificerede risikoaktiviteter på følgende områder:

- **Microsoft 365-overvågningslogge**: Dette er den primære kilde til at identificere de fleste af de potentielt risikable aktiviteter, der er inkluderet i alle scanninger.
- **Exchange Online**: Inkluderet i alle scanninger hjælper Exchange Online aktivitet med at identificere aktiviteter, hvor data i vedhæftede filer sendes via mail til eksterne kontakter eller tjenester.
- **Azure Active Directory**: Azure Active Directory-historikken er inkluderet i alle scanninger og hjælper med at identificere risikable aktiviteter, der er knyttet til brugere med slettede brugerkonti.
- **Microsoft 365 HR-dataconnector**: Hvis de er konfigureret, hjælper HR-connectorhændelser med at identificere risikable aktiviteter, der er knyttet til brugere, der har fratræden eller kommende slutdatoer.

Analyseindsigt fra scanninger er baseret på de samme risikoaktivitetssignaler, der bruges af politikker for styring af insiderrisiko, og rapportresultater baseret på både enkelt- og sekvensbrugeraktiviteter. Scoren for risiko for analyser er dog baseret på op til 10 dages aktivitet, mens insiderrisikopolitikker bruger daglig aktivitet til indsigt. Når du aktiverer og kører analyser i din organisation første gang, får du vist scanningsresultaterne for én dag. Hvis du lader analyse være aktiveret, kan du se resultaterne af hver daglig scanning, der føjes til indsigtsrapporterne, i et maksimalt interval på de forrige 10 dages aktivitet.

### <a name="enable-analytics-and-start-your-scan"></a>Aktivér analyser, og start scanningen

Hvis du vil aktivere insiderrisikoanalyse, skal du være medlem af rollegruppen *Insider Risk Management*, *Insider Risk Management Administration* eller *Microsoft 365 Global admin*.
Fuldfør følgende trin for at aktivere insiderrisikoanalyse:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Insider Risk Management**.
2. Vælg **Kør scanning** på fanen **Scan for insiderrisici på dit organisationskort** under fanen **Oversigt over** styring af insiderrisiko. Dette aktiverer analysescanning for din organisation. Du kan også aktivere scanning i din organisation ved at gå til **Insider-risikoindstillinger** > **Analytics** og aktivere **Scan din lejers brugeraktivitet for at identificere potentielle insiderrisici**.
3. I ruden **Analysedetaljer** skal du vælge **Kør scanning** for at starte scanningen for din organisation. Resultaterne af analysescanningen kan tage op til 48 timer, før indsigt er tilgængelig som rapporter til gennemsyn.

![Indstillinger for analyse af styring af insiderrisiko.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Visning af analyseindsigt og oprettelse af nye politikker

Når den første analysescanning er fuldført for din organisation, modtager medlemmer af rollegruppen *Insider Risk Management Administration* automatisk en mailmeddelelse og kan få vist den første indsigt og anbefalinger til potentielt risikable aktiviteter fra dine brugere. Daglige scanninger fortsætter, medmindre du deaktiverer analyser for din organisation. Der gives mailmeddelelser til administratorer for hver af de tre kategorier i området til analyse (datalækager, tyveri og exfiltration) efter den første forekomst af aktivitet i din organisation. Mailmeddelelser sendes ikke til administratorer til registrering af opfølgningsaktivitet som følge af de daglige scanninger.  Hvis analyser i **Indstillinger for** >  **styring af** >  insiderrisiko er deaktiveret og derefter aktiveres igen i din organisation, nulstilles automatiske mailmeddelelser, og der sendes mails til medlemmer af rollegruppen *Insider Risk Management Administration* for at få ny scanningsindsigt.

Hvis du vil have vist potentielle risici for din organisation, skal du gå til fanen **Oversigt** og vælge **Få vist resultater** på kortet **Insider Risk Analytics** . Hvis scanningen for din organisation ikke er fuldført, får du vist en meddelelse om, at scanningen stadig er aktiv.

![Rapportklart kort til analyse af insiderrisikostyring.](../media/insider-risk-analytics-ready-card.png)

I forbindelse med fuldførte scanninger kan du se de potentielle risici, der er registreret i din organisation, samt indsigt og anbefalinger til at håndtere disse risici. Identificerede risici og specifik indsigt er inkluderet i rapporter grupperet efter område, det samlede antal brugere med identificerede risici, procentdelen af disse brugere med potentielt risikable aktiviteter og en anbefalet insiderrisikopolitik for at hjælpe med at afhjælpe disse risici. Rapporterne omfatter:

- **Indsigt i datalækage**: Aktiviteter for alle brugere, der kan omfatte utilsigtet overdeling af oplysninger uden for din organisation eller datalækager fra brugere med ondsindede hensigter.
- **Indsigt i datatyveri**: Aktiviteter for afrejsende brugere eller brugere med slettede Azure Active Directory-konti, der kan omfatte risiko for deling af oplysninger uden for din organisation eller datatyveri foretaget af brugere med ondsindede hensigter.
- **Top indsigt i eksfiltration**: Aktiviteter for alle brugere, der kan omfatte deling af data uden for din organisation.

![Oversigtsrapport over analyse af styring af insiderrisiko.](../media/insider-risk-analytics-overview.png)

Hvis du vil have vist flere oplysninger om en indsigt, skal du vælge **Vis detaljer** for at få vist detaljeruden for indsigten. Detaljeruden indeholder de komplette indsigtsresultater, en anbefaling af insiderrisikopolitik og knappen **Opret politik** , så du hurtigt kan få hjælp til at oprette den anbefalede politik. Hvis du vælger Opret politik, føres du til politikguiden og vælger automatisk den anbefalede politikskabelon, der er relateret til indsigten. Hvis analyseindsigten f.eks. er til *datalækageaktivitet* , vælges politikskabelonen *Generelle datalækager* på forhånd i politikguiden for dig.

![Detaljeret rapport over analyse af insiderrisikostyring.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Deaktiver analyse

Hvis du vil slå insiderrisikoanalyse fra, skal du være medlem af rollegruppen *Insider Risk Management*, *Insider Risk Management Administration* eller Microsoft 365 *Global admin*. Når du deaktiverer analyse, forbliver indsigtsrapporter for analyse statiske og opdateres ikke for nye risici.

Udfør følgende trin for at slå insiderrisikoanalyse fra:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Insider Risk Management**.
2. Vælg **Indstillinger for** >  insiderrisiko **Analytics-side**.
3. På siden **Analytics** skal du slå **Scan din lejers brugeraktivitet fra for at identificere potentielle insiderrisici**.

## <a name="admin-notifications"></a>Administration meddelelser

Administration meddelelser sender automatisk en mailmeddelelse til valgbare rollegrupper for styring af insiderrisiko. Du kan aktivere meddelelser og tildele, hvilke rollegrupper der modtager meddelelserne for følgende scenarier:

- Send en mail med besked, når den første besked genereres for en ny politik. Politikker kontrolleres hver 24. time for førstegangsbeskeder, og meddelelser sendes ikke for efterfølgende beskeder for politikken.
- Send en daglig mail, når der genereres nye beskeder med høj alvorsgrad. Politikker kontrolleres hver 24. time for beskeder med høj alvorsgrad.
- Send en ugentlig mail med en opsummering af politikker, der har uløste advarsler

Hvis du har aktiveret insiderrisikostyringsanalyse for din organisation, modtager medlemmer af rollegruppen *Insider Risk Management Administration* automatisk en mailmeddelelse om indledende analyseindsigt for datalækager, tyveri og eksfiltrationsaktiviteter.

Hvis du foretrækker at deaktivere administrator- og analysemeddelelser, skal du fuldføre følgende trin:

1. I [Microsoft Purview-compliance-portal skal du](https://compliance.microsoft.com) gå til **Insider-risikostyring** > **Indstillinger for Insider-risiko**.
2. Vælg siden **Administration meddelelser**.
3. Fjern markeringen i afkrydsningsfeltet for at få vist følgende indstillinger efter indstillingerne:
    - **Send en mail med besked, når den første besked genereres for en ny politik**
    - **Send en mail, når der er en ny indsigt tilgængelig i Analytics**
    - **Send en mail, når Analytics er slået fra**

4. Vælg **Gem** for at konfigurere og afslutte.
