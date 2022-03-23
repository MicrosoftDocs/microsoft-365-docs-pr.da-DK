---
title: Indstillinger for Insider-risikostyring
description: Få mere at vide om indstillinger for insider-risikostyring i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
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
ms.openlocfilehash: f80ab9fcb0a3e057a20c22ff05c3a960cdf7eab4
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63590916"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Kom i gang med indstillingerne for insider-risikostyring

Insider-indstillinger for risikostyring gælder for alle insider-risikostyringspolitikker, uanset hvilken skabelon du vælger, når du opretter en politik. Indstillinger konfigureres ved hjælp af **kontrolelementet Insider-risikoindstillinger**, der er placeret øverst på alle sider med insider-risikostyring. Disse indstillinger styrer politikkomponenter for følgende områder:

- Beskyttelse af personlige oplysninger
- Indikatorer
- Tidslinjer for politikker
- Intelligente registreringer
- Eksportér beskeder
- Prioritet af brugergrupper (forhåndsvisning)
- Prioritet af fysiske aktiver (forhåndsvisning)
- Power Automate flows (forhåndsvisning)
- Microsoft Teams (eksempel)
- Analyse
- Administratormeddelelser

Før du går i gang og opretter insider-risikostyringspolitikker, er det vigtigt at forstå disse indstillinger og vælge de niveauer, der bedst opfylder organisationens behov for overholdelse.

## <a name="privacy"></a>Beskyttelse af personlige oplysninger

Beskyttelse af personlige oplysninger for brugere, der har opfylder politikkerne, er vigtigt og kan hjælpe med at fremme objektivitet i anmeldelser af data og analyse for insider-risikobeskeder. For brugere med et match til en Insider-risikopolitik kan du vælge en af følgende indstillinger:

- **Vis anonymiserede versioner af brugernavne**: Navne på brugere er anonymiserede for at forhindre administratorer, dataadministratorer og korrekturlæsere i at se, hvem der er knyttet til politikadvarsler. Eksempelvis blev en brugers 'Grace Taylor' vist med et randomiseret pseudonym, f.eks. 'AnonIS8-988' på alle områder af Insider-risikostyringsoplevelsen. Hvis du vælger denne indstilling, anonymiseres alle brugere med aktuelle og tidligere politikoverensstemmelser og gælder for alle politikker. Oplysninger om brugerprofiler i insider-risikobeskeden og sagsoplysninger vil ikke være tilgængelige, når denne indstilling vælges. Brugernavne vises dog, når du føjer nye brugere til eksisterende politikker, eller når du tildeler brugere nye politikker. Hvis du vælger at deaktivere denne indstilling, vises brugernavne for alle brugere, der har aktuelle eller tidligere politik match.

    >[!IMPORTANT]
    >For at bevare referentiel integritet for brugere, der har insider-risikoadvarsler eller -sager i Microsoft 365 eller andre systemer, bevares anonymisering af brugernavne ikke for eksporterede beskeder. Eksporterede beskeder viser brugernavne for hver besked.

- **Vis ikke anonymiserede versioner af brugernavne**: Brugernavne vises for alle aktuelle og tidligere politik match for beskeder og sager. Brugerprofiloplysninger (navn, titel, alias og organisation eller afdeling) vises for brugeren for alle Insider Risk Management-beskeder og -sager.

![Indstillinger for beskyttelse af personlige oplysninger for Insiders til risikostyring.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Indikatorer

Skabeloner for Insider-risikopolitik definerer typen af risikoaktiviteter, som du vil registrere og undersøge. Hver politikskabelon er baseret på specifikke indikatorer, der svarer til bestemte udløsere og risikoaktiviteter. Alle indikatorer er som standard deaktiveret, og du skal vælge en eller flere politikindikatorer, før du konfigurerer en insider-politik for risikostyring.

Beskeder udløses af politikker, når brugere udfører aktiviteter relateret til politikindikatorer, der opfylder en påkrævet grænse. Insider-risikostyring anvender to typer indikatorer:

- **Udløsende begivenheder**: Hændelser, der bestemmer, om en bruger er aktiv i en insider-politik for risikostyring. Hvis en bruger føjes til en insider-risikostyringspolitik, der ikke har en udløsende hændelse, evalueres brugerens aktivitet ikke af politikken. Eksempelvis føjes Bruger A til en politik, der er oprettet ud fra skabelonen *Datatyveri* ved at tage brugere ud af politikskabelonen, og politikken og Microsoft 365 HR-forbindelsen er korrekt konfigureret. Indtil bruger A har en slutdato, der rapporteres af HR-forbindelsen, evalueres User A-aktiviteter ikke af denne insider-risikostyringspolitik for risici. Et andet eksempel på en udløsende hændelse er, hvis en bruger  har en DLP-politikbesked med høj alvorlighed, når der bruges *politikker for datalækage*.
- **Politikindikatorer**: Indikatorer i politikker for insider-risikostyring, der bruges til at bestemme et risikoresultat for en in-scope-bruger. Disse politikindikatorer aktiveres kun, når en udløserhændelse forekommer for en bruger. Eksempler på politikindikatorer er, når en bruger kopierer data til personlige skylagertjenester eller bærbare lagringsenheder, hvis en brugerkonto fjernes fra Azure Active Directory, eller hvis en bruger deler interne filer og mapper med uautoriserede eksterne parter.

Visse politikindikatorer kan også bruges til at tilpasse udløserhændelser for bestemte politikskabeloner. Når de er konfigureret i politikguiden for generelle datalækager eller *datalækager* efter *prioritetsbrugerskabeloner* , giver disse indikatorer dig større fleksibilitet og tilpasningsmuligheder for dine politikker, og når brugerne er omfattet af en politik. Desuden kan du definere individuelle aktivitetstærskler for disse udløsende indikatorer for at få et mere gransket kontrolelement i en politik.

Politikindikatorer er opdelt i følgende områder. Du kan vælge symbolerne til at aktivere og tilpasse grænser for indikatorhændelser for hvert indikatorniveau, når du opretter en insider-risikopolitik:

- **Office indikatorer**: Disse omfatter politikindikatorer for SharePoint, Microsoft Teams og mails.
- **Enhedsindikatorer**: Disse omfatter politikindikatorer for aktivitet såsom deling af filer via netværket eller med enheder. Indikatorer omfatter aktiviteter, der involverer alle filtyper, undtagen eksekverbar (.exe) og dynamic link library-.dll)-filaktivitet. Hvis du vælger *Enhedsindikatorer*, behandles aktiviteten for enheder med Windows 10 build 1809 eller nyere og macOS-enheder (Catalina 10.15 eller nyere). For både Windows og macOS-enheder skal du først onboarde enheder til overholdelsescenter. Enhedsindikatorer omfatter også browsersignalregistrering, der kan hjælpe organisationen med at registrere og reagere på udfyldningssignaler til ikke-eksekverbare filer, der vises, kopieres, deles eller udskrives i Microsoft Edge og Google Chrome. Du kan finde flere oplysninger om konfiguration Windows enheder til integration med Insider-risici i det følgende afsnit [Aktivér enhedsindikatorer og onboard Windows-enheder](insider-risk-management-settings.md#OnboardDevices) i denne artikel. Du kan finde flere oplysninger om konfiguration af macOS-enheder til integration med Insider Risk i det følgende afsnit Aktivér enhedsindikatorer og onboard macOS-enheder i denne artikel. Du kan finde flere oplysninger om browsersignalregistrering under [Få mere at vide om og konfigurer insider-browsersignalregistrering for risikostyring](insider-risk-management-browser-support.md).
- **Indikator for overtrædelse af** sikkerhedspolitik (forhåndsvisning): Disse omfatter indikatorer fra Microsoft Defender til slutpunkt, der relaterer til installation af ikke-godkendt eller skadelig software eller tilsidesætter sikkerhedskontrolelementer. Hvis du vil modtage beskeder i Insider Risk Management, skal du have aktiveret en aktiv Defender for Endpoint-licens og insider-risikointegration. Du kan finde flere oplysninger om konfiguration af Defender til Endpoint for integration af insider-risikostyring i Konfigurer [avancerede funktioner i Microsoft Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Adgangsindikatorer for patientjournaler (forhåndsvisning)**: Disse omfatter politikindikatorer for adgang til patientjournaler. Eksempelvis kan forsøg på at få adgang til patientjournaler i dine elektroniske patientjournaler (EMR)-systemlogfiler deles med insider-politikker for risikostyring i sundhedssektoren. Hvis du vil modtage disse typer beskeder i Insider Risk Management, skal du have en sundhedsspecifik dataforbindelse og HR-dataforbindelse konfigureret.
- **Symboler for fysisk adgang (forhåndsvisning)**: Disse omfatter politikindikatorer for fysisk adgang til følsomme aktiver. Forsøg på at få adgang til et begrænset område i dine fysiske badging systemlogge kan f.eks. deles med insider-risikostyringspolitikker. Hvis du vil modtage disse typer beskeder i Insider Risk Management, skal du have aktiveret prioritets fysiske aktiver i Insider Risk Management og den fysiske [badging-dataforbindelse](import-physical-badging-data.md) konfigureret. Du kan få mere at vide om konfiguration af fysisk adgang i [afsnittet Prioritets fysisk adgang](#priority-physical-assets-preview) i denne artikel.
- **Indikatorer for Microsoft Defender til skyapps (forhåndsvisning)**: Disse omfatter politikindikatorer fra delte beskeder fra Defender til skyapps. Automatisk aktiveret registrering af anomali i Defender til skyapps starter straks med at registrere og sammenligne resultater, hvilket målretter mange funktionsmådeanomer på tværs af dine brugere og de computere og enheder, der er forbundet til dit netværk. Vælg en eller flere indikatorer i dette afsnit for at medtage disse aktiviteter i meddelelser om insider-risikostyringspolitik. Hvis du vil have mere at vide om Defender til cloudapps-analyser og registrering af unormalt indhold, skal du se Få [adfærdsanalyser og registrering af unormalt indhold](/cloud-app-security/anomaly-detection-policy).
- **Risikostyring:** Disse omfatter at hæve risikoscore for aktivitet, der er over brugerens sædvanlige aktivitet for en dag eller for brugere med tidligere sager løst som en overtrædelse af politikken. Hvis du aktiverer risikoscore, øges risikoresultaterne og risikoen for beskeder for disse typer aktiviteter. For aktivitet, der er over brugerens sædvanlige aktivitet for en dag, øges pointtal, hvis den registrerede aktivitet afviger fra brugerens typiske adfærd. For brugere, hvor tidligere sager er blevet løst som en overtrædelse af politikken, får de et større antal point, hvis mere end én sag tidligere er blevet løst som en bekræftet overtrædelse af politikken. Risikoscorepoint kan kun vælges, hvis der er valgt en eller flere indikatorer.

I nogle tilfælde kan det være en ide at begrænse de indikatorer for Insider-risikopolitikker, der anvendes på insider-risikopolitikker i organisationen. Du kan deaktivere politikindikatorerne for bestemte områder ved at deaktivere dem fra alle insider-risikopolitikker. Udløserhændelser kan kun *ændres* i forhold til politikker, der er skabt af de generelle datalækager eller *datalækager efter prioritetsbrugerskabeloner* . Politikker, der er oprettet ud fra alle andre skabeloner, kan ikke tilpasses og udløser indikatorer eller hændelser.

For at definere insider-risikopolitikindikatorerne, der er aktiveret i alle insider-risikopolitikker, skal du gå til Insider-risikoindstillingerIndikatorer  >  og vælge en eller flere politikindikatorer. De indikatorer, der er valgt på siden med indstillinger for indikatorer, kan ikke konfigureres individuelt, når du opretter eller redigerer en Insider-risikopolitik i guiden politik.

> [!NOTE]
> Det kan tage flere timer, før nye manuelt tilføjede brugere vises i **brugerdashboardet**. Det kan tage op til 24 timer at få vist aktiviteter for disse brugere i de foregående 90 dage. Hvis du vil have vist aktiviteter for manuelt tilføjede brugere, skal du vælge brugeren på **dashboardet** Brugere og åbne **fanen** Brugeraktivitet i detaljeruden.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Aktivér enhedsindikatorer og onboard-Windows enheder
<a name="OnboardDevices"> </a>

Hvis du vil aktivere overvågning af risikoaktiviteter på Windows-enheder og medtage politikindikatorer for disse aktiviteter, skal dine Windows-enheder opfylde følgende krav, og du skal udføre følgende onboardingtrin.

#### <a name="step-1-prepare-your-endpoints"></a>Trin 1: Forbered dine slutpunkter

Sørg for, at Windows 10 enheder, du planlægger at rapportere i Insider Risk Management, opfylder disse krav.

1. Skal køre Windows 10 x64 build 1809 eller nyere og skal have installeret [Windows 10-opdateringen (OS Build 17763.1075)](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) fra den 20. februar 2020.
2. Den brugerkonto, der bruges til at logge på Windows 10 enhed, skal være en aktiv Azure Active Directory (AAD)-konto. Den Windows 10 enhed kan være [AAD](/azure/active-directory/devices/concept-azure-ad-join), hybrid AAD eller Active Directory forbundet eller AAD registreret.
3. Installér Microsoft Edge på slutpunktsenheden for at overvåge handlinger for uploadaktiviteten i skyen. Se [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>Trin 2: Onboardingenheder
<a name="OnboardStep2"> </a>

Du skal aktivere overvågning af enheder og onboarde dine slutpunkter, før du kan overvåge insider-risikostyringsaktiviteter på en enhed. Begge handlinger er foretaget i Microsoft 365 Compliance Portal.

Når du vil onboarde enheder, der endnu ikke er blevet onboardet, skal du downloade det relevante script og installere som beskrevet i følgende trin.

Hvis du allerede har enheder onboardet i [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/), vises de allerede på listen over administrerede enheder. Følg [trin 3: Hvis du har enheder, der er onboardet på Microsoft Defender til slutpunkt](insider-risk-management-settings.md#OnboardStep3) i næste afsnit.

I dette installationsscenarie vil du onboarde enheder, der endnu ikke er blevet onboardet, og du ønsker blot at overvåge insider-risikoaktiviteter på Windows 10 enheder.

1. Åbn [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com).
2. Åbn siden med indstillinger for Overholdelsescenter, og vælg **Onboard-enheder**.

   > [!NOTE]
   > Det tager som regel ca. 60 sekunder, før onboarding af enheder er aktiveret, men det kan tage op til 30 minutter, før du går i gang med Microsoft Support.

3. Vælg **Enhedshåndtering** for at åbne **listen** Enheder. Listen vil være tom, indtil du onboarder enheder.
4. Vælg **Onboarding** for at starte onboardingprocessen.
5. Vælg den måde, du vil installere på disse flere enheder på listen **Installationsmetode** , og **download derefter pakke**.
6. Følg de relevante procedurer i [Onboarding-værktøjer og -metoder til Windows 10 computere](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Dette link fører dig til en landingsside, hvor du kan få adgang til Microsoft Defender for Endpoint-procedurer, der svarer til den installationspakke, du valgte i trin 5:
    - Onboard Windows 10 computere, der bruger Gruppepolitik
    - Onboard Windows computere, der bruger Microsoft Endpoint Configuration Manager
    - Onboard Windows 10 computere ved hjælp af værktøjer til administration af mobilenheder
    - Onboard Windows 10 computere, der bruger et lokalt script
    - Onboard ikke-permanente VDI-computere (Virtual Desktop Infrastructure).

Når det er gjort, og slutpunktet er onboardet, skal det være synligt på listen over enheder, og slutpunktet starter rapportering af overvågningsaktivitetslogs for insider-risikostyring.

> [!NOTE]
> Denne oplevelse håndhæves af licens. Uden den påkrævede licens vil data ikke være synlige eller tilgængelige.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>Trin 3: Hvis du har enheder, der er onboardet på Microsoft Defender til Slutpunkt
<a name="OnboardStep3"> </a>

Hvis Microsoft Defender til slutpunkt allerede er installeret, og der rapporteres slutpunkter, vises alle disse slutpunkter på listen over administrerede enheder. Du kan fortsætte med at onboarde nye enheder i insider-risikostyring for at udvide dækningen ved hjælp af [sektionen Trin 2: Onboardingenheder](insider-risk-management-settings.md#OnboardStep2) .

1. Åbn [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com).
2. Åbn siden med indstillinger for Overholdelsescenter, og vælg **Aktivér enhedsovervågning**.
3. Vælg **Enhedshåndtering** for at åbne **listen** Enheder. Du bør få vist listen over enheder, der allerede rapporterer til Microsoft Defender til slutpunkt.
4. Vælg **Onboarding,** hvis du har brug for at onboarde flere enheder.
5. Vælg den måde, du vil installere på disse flere enheder på listen **Installationsmetode** , og vælg derefter **Download pakke**.
6. Følg de relevante procedurer i [Onboarding-værktøjer og -metoder til Windows 10 computere](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Dette link fører dig til en landingsside, hvor du kan få adgang til Microsoft Defender for Endpoint-procedurer, der svarer til den installationspakke, du valgte i trin 5:
    - Onboard Windows 10 computere, der bruger Gruppepolitik
    - Onboard Windows computere, der bruger Microsoft Endpoint Configuration Manager
    - Onboard Windows 10 computere ved hjælp af værktøjer til administration af mobilenheder
    - Onboard Windows 10 computere, der bruger et lokalt script
    - Onboard ikke-permanente VDI-computere (Virtual Desktop Infrastructure).

Når det er gjort, og slutpunktet er onboardet, bør det være  synligt under tabellen Enheder, og slutpunktet starter rapportering af overvågningsaktivitetslogs for insider-risikostyring.

> [!NOTE]
>Denne oplevelse håndhæves af licens. Uden den påkrævede licens vil data ikke være synlige eller tilgængelige.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Aktivér enhedsindikatorer og onboard macOS-enheder

macOS-enheder (Catalina 10.15 eller nyere) kan onboardes i Microsoft 365 til at understøtte Insider-politikker for risikostyring ved hjælp af enten Intune eller SYLTEF Pro. Du kan finde flere oplysninger og konfigurationsvejledning [under Onboard macOS-enheder Microsoft 365 oversigt (forhåndsvisning)](device-onboarding-macos-overview.md).

### <a name="indicator-level-settings-preview"></a>Indstillinger for indikatorniveau (eksempel)

Når du opretter en politik i guiden til politikker, kan du konfigurere, hvordan det daglige antal risikohændelser skal påvirke risikoresultatet for Insider-risikobeskeder. Disse indikatorindstillinger hjælper dig med at styre, hvordan antallet af forekomster af risikohændelser i organisationen skal påvirke risikoscore og dermed den tilknyttede alvorsgrad for disse hændelser. Hvis du foretrækker det, kan du også vælge at beholde de standardniveauer for begivenhed, der anbefales af Microsoft til alle aktiverede indikatorer.

Du beslutter f.eks., at aktivere SharePoint-indikatorer i insider-risikopolitikindstillingerne og angive brugerdefinerede grænseværdier for SharePoint-hændelser, når du konfigurerer indikatorer for en ny politik  for insider-risikodatalækager. Mens du er i guiden insider-risikopolitik, skal du konfigurere tre forskellige daglige begivenhedsniveauer for hver SharePoint for at påvirke risikoscore for beskeder, der er knyttet til disse begivenheder.

![Indstillinger for brugerdefineret indikator for Insider-risikostyring.](../media/insider-risk-custom-indicators.png)

For det første daglige begivenhedsniveau angiver du grænsen til *10* eller flere begivenheder pr. dag for en lavere påvirkning af risikoscore for hændelserne, *20* eller flere begivenheder pr. dag for en mellemstor påvirkning af risikoresultatet for begivenhederne og *30* eller flere hændelser pr. dag en højere påvirkning af risikoresultatet for hændelserne. Disse indstillinger betyder i praksis:

- Hvis der er 1-9 SharePoint hændelser, der finder sted efter udløsning af hændelse, påvirkes risikoresultater minimalt og vil som regel ikke generere en besked.
- Hvis der sker 10-19 SharePoint hændelser efter en udløsende hændelse, er risikopointen forbundet med lavere, og alvorsgraderne for beskeder vil ofte være på et lavt niveau.
- Hvis der er 20-29 SharePoint hændelser, der finder sted efter en udløser, er risikopointen forbundet med højere, og alvorsgraderne for beskeder vil ofte være på et mellemlangt niveau.
- Hvis der er 30 eller flere SharePoint hændelser, der finder sted efter en udløser, er risikopointen forbundet med højere, og alvorsgraderne for beskeder vil ofte være på et højt niveau.

## <a name="policy-timeframes"></a>Politiktidsrammer

Med politiktidsrammer kan du definere tidligere og fremtidige korrekturperioder, der udløses efter politik matches, baseret på begivenheder og aktiviteter for politikskabelonerne for insider-risikostyring. Afhængigt af den politikskabelon, du vælger, er følgende politiktidsrammer tilgængelige:

- **Aktiveringsvindue**: Tilgængeligt for alle politikskabeloner, er aktiveringsvinduet det definerede antal dage, som vinduet aktiveres **efter** en udløsende hændelse. Vinduet aktiveres i 1 til 30 dage, efter en udløsende hændelse forekommer for alle brugere, der er tildelt politikken. Du har f.eks. konfigureret en politik for insider-risikostyring og *indstillet vinduet Aktivering* til 30 dage. Der er gået flere måneder, siden du konfigurerede politikken, og en udløsende hændelse forekommer for en af brugerne i politikken. Udløserhændelsen aktiverer aktiveringsvinduet, og politikken er aktiv for den pågældende bruger i 30 dage, efter den udløsende hændelse indtraf.
- **Registrering af tidligere aktivitet**: Tilgængelig for alle politikskabeloner, er registrering af tidligere aktivitet det definerede antal dage, vinduet aktiveres **før en** udløsende hændelse. Vinduet aktiveres i 0 til 90 dage, før en udløsende hændelse forekommer for alle brugere, der er tildelt politikken. Eksempelvis har du konfigureret en politik for insider-risikostyring og indstillet registrering *af tidligere aktivitet* til 90 dage. Der er gået flere måneder, siden du konfigurerede politikken, og en udløsende hændelse forekommer for en af brugerne i politikken. Udløserbegivenhed aktiverer registrering af tidligere aktivitet *,* og politikken samler historiske aktiviteter for den pågældende bruger i 90 dage før den udløsende begivenhed.

![Insider-tidsrammeindstillinger for risikostyring.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Intelligente registreringer

Intelligente registreringsindstillinger hjælper med at finjustere, hvordan registreringer af risikabelt aktivitet behandles for beskeder. I visse tilfælde kan det være nødvendigt at definere filtyper, der skal ignoreres, eller du ønsker at gennemtvinge et registreringsniveau for daglige begivenheder for at øge risikopoints for brugerne. Brug disse indstillinger til at styre udeladelse af filtyper, styrke risikoscore for usædvanlig aktivitet og filmængdebegrænsninger.

### <a name="file-type-exclusions"></a>Udeladelse af filtyper

Hvis du vil udelukke bestemte filtyper fra alle matchning af insider-risikostyringspolitik, skal du angive filtypenavne adskilt af kommaer. Hvis du f.eks. vil udelukke visse typer musikfiler fra politik matches, kan du indtaste *aac,mp3,wav,wma* i **feltet Filtype udeladelse** . Filer med disse udvidelser ignoreres af alle insider-politikker for risikostyring.

### <a name="minimum-number-of-daily-events-to-boost-score-for-unusual-activity"></a>Minimum antal daglige begivenheder for at øge scoren for usædvanlig aktivitet

Med denne indstilling angiver du, hvor mange daglige begivenheder, der kræves for at øge risikoscore for aktivitet, der betragtes som usædvanlig for en bruger. Lad os f.eks. sige, at du angiver 25 for denne risiko. Hvis en bruger beregner 10 filoverførsler i løbet af de seneste 30 dage, men en politik registrerer, at de har hentet 20 filer på én dag, bliver scoren for den pågældende aktivitet ikke boostet, selvom det er usædvanligt for den pågældende bruger, fordi antallet af filer, brugeren hentede den pågældende dag, var mindre end det antal, du angav for denne risikouddeling.

### <a name="alert-volume"></a>Besked om lydstyrke

Brugeraktiviteter, der registreres af insider-risikopolitikker, tildeles en specifik risikoscore, som igen bestemmer alvorsgrad for beskeden (lav, mellem, høj). Som standard genererer vi en bestemt mængde lav, mellem og høj alvorsgrad, men du kan øge eller mindske lydstyrken, så den passer til dine behov. Hvis du vil justere mængden af beskeder for alle politikker for insider-risikostyring, skal du vælge en af følgende indstillinger:

- **Færre beskeder**: Du får vist alle vigtige beskeder om høj alvorsgrad, færre beskeder om mellem alvorlighed og ingen lav alvorsgrad. Dette indstillingsniveau betyder, at du muligvis går glip af nogle reelle positive.
- **Standardmængde**: Du får vist alle vigtige beskeder om høj alvorsgrad og en balanceret mængde af mellem og lav alvorsgrad.
- **Flere beskeder**: Du får vist alle beskeder om mellemstor og høj alvorsgrad og de mest lav alvorsgrader. Dette indstillingsniveau kan resultere i flere falske positive.

### <a name="microsoft-defender-for-endpoint-preview"></a>Microsoft Defender til Slutpunkt (forhåndsvisning)

[Microsoft Defender til Slutpunkt er en](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) sikkerhedsplatform til virksomheder, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. For at få bedre overblik over sikkerhedsbrud i organisationen kan du importere og filtrere Defender for Endpoint-beskeder for aktiviteter, der bruges i politikker, der er oprettet ud fra politikskabeloner til insider-risikostyringssikkerhedsbrud.

Afhængigt af de typer signaler, du er interesseret i, kan du vælge at importere beskeder til Insider Risk Management baseret på triagestatussen for Defender for Endpoint-beskeder. Du kan angive en eller flere af følgende statusser for beskedstyring i de globale indstillinger for at importere:

- Unknown
- Ny
- I gang
- Løst

Beskeder fra Defender til slutpunkt importeres dagligt. Afhængigt af den valgte status for administration kan du se flere brugeraktiviteter for den samme besked, som statussen for triage ændres i Defender til slutpunkt.

Hvis du f.eks. vælger *Ny, I* gang og *Løst for denne* indstilling, når der genereres en Microsoft Defender for Endpoint-besked, og status er *Ny, importeres* der en indledende beskedaktivitet for brugeren i insider-risiko.  Når status for triage for Defender til slutpunkt ændres til I *gang,* importeres endnu en aktivitet for denne besked for brugeren i insider-risiko. Når den endelige status for triage for Defender til slutpunkt  for Løst er angivet, importeres en tredje aktivitet for denne besked for brugeren i insider-risiko. Denne funktionalitet gør det muligt for dig at følge forløbet for Defender for Endpoint-beskederne og vælge det synlighedsniveau, som undersøgelsen kræver.

> [!IMPORTANT]
> Du skal have Microsoft Defender til Slutpunkt konfigureret i din organisation og aktivere Defender for Endpoint for integration af Insider Risk Management i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde flere oplysninger om konfiguration af Defender til Endpoint for integration af insider-risikostyring i [Konfigurer avancerede funktioner i Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Domæner

Domæneindstillinger hjælper dig med at definere risikoniveauer for aktiviteter for bestemte domæner. Disse aktiviteter omfatter deling af filer, afsendelse af mails, hentning eller overførsel af indhold. Ved at angive domæner i disse indstillinger kan du øge eller mindske risikoscore for aktivitet, der finder sted med disse domæner.

Brug Tilføj domæne til at definere et domæne for hver af domæneindstillingerne. Du kan også bruge jokertegn til at matche variationer af roddomæner eller underdomæner. Hvis du f.eks. vil angive sales.wingtiptoys.com og support.wingtiptoys.com, skal du bruge jokertegnet '*.wingtiptoys.com' til at matche disse underdomæner (og andre underdomæner på samme niveau). Hvis du vil angive underdomæner på flere niveauer for et roddomæne, skal du markere afkrydsningsfeltet Medtag **underdomæner** på flere niveauer.

For hver af følgende domæneindstillinger kan du angive op til 500 domæner:

- **Ikke tilladte domæner:** Ved at angive ikke-tilladte domæner vil aktivitet, der finder sted med disse domæner, have *højere* risikoresultater. Nogle eksempler er aktiviteter, der involverer deling af indhold med nogen (f.eks. afsendelse af mail til en person med en gmail.com-adresse), og når brugere downloader indhold til en enhed fra et af disse ikke-tilladte domæner.
- **Tilladte domæner:** Visse aktiviteter, der er relateret til tilladte domæner, ignoreres af dine politikker og genererer ikke beskeder. Disse aktiviteter omfatter:

    - Mail, der sendes til eksterne domæner
    - Filer, mapper, websteder, der deles med eksterne domæner
    - Filer, der er overført til eksterne domæner (ved Microsoft Edge webbrowser)

    Ved at angive tilladte domæner i indstillinger behandles denne aktivitet med disse domæner på samme måde som intern organisationsaktivitet behandles. Domæner, der er føjet her, er f.eks. kort over til aktiviteter, der kan omfatte deling af indhold med en person uden for organisationen (f.eks. afsendelse af mails til en person med gmail.com adresse).

- **Tredjepartsdomæner:** Hvis din organisation bruger tredjepartsdomæner til forretningsformål (f.eks. skylager), skal du medtage dem her, så du kan modtage beskeder om aktivitet, der er relateret til enhedsindikatoren Brug en browser til at downloade indhold fra et *tredjepartswebsted*.

## <a name="export-alerts"></a>Eksportér beskeder

Insider-oplysninger om risikostyringsadvarsel kan eksporteres til sikkerhedsoplysninger og begivenhedsstyring (SIEM) og SOAR-løsninger (Security Automated Response) ved hjælp af [Office 365 Management Activity API-skemaet](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema). Du kan bruge de Office 365 Management Activity API'er til at eksportere beskedoplysninger til andre programmer, som din organisation kan bruge til at administrere eller aggregere insider-risikooplysninger. Beskedoplysninger eksporteres og er tilgængelige hvert 60. minut via Office 365-API'er for aktivitetsstyring.

Hvis din organisation bruger Microsoft Sentinel, kan du også bruge insider-dataforbindelse til insider-risikostyring til at importere Insider-oplysninger om risikobeskeder til Sentinel. Du kan finde flere [oplysninger Microsoft 365 Insider Risk Management (IRM) (Preview)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) i Microsoft Sentinel-artiklen.

>[!IMPORTANT]
>For at bevare referentiel integritet for brugere, der har insider-risikoadvarsler eller -sager i Microsoft 365 eller andre systemer, bevares anonymisering af brugernavne ikke for eksporterede beskeder. Eksporterede beskeder viser brugernavne for hver besked.

Sådan bruges API'er til at gennemse insider-risikoadvarsler:

1. Aktivér Office 365 Management Activity API-understøttelse **i Insider-Indstillinger** >  >  **Export-beskeder**. Denne indstilling er som standard deaktiveret for din Microsoft 365 organisation.
2. Filtrer de almindelige Office 365 af *SecurityComplianceAlerts*.
3. *Filtrer SecurityComplianceAlerts* af *kategorien InsiderRiskManagement*.

![Indstillinger for eksport af Insider-risikostyring.](../media/insider-risk-settings-export.png)

Beskedoplysninger indeholder oplysninger fra skemaet for sikkerheds- og overholdelsesadvarsler og Office 365 administrationsaktivitets-API'ens fælles skema.

Følgende felter og værdier eksporteres til insider-risikostyringsadvarsler for skemaet til & Security & Compliance Alert:

| **Beskedparameter** | **Beskrivelse** |
|:------------------|:----------------|
| AlertType | Beskedens type er *Brugerdefineret*.  |
| AlertId | GUID'et for beskeden. Insider-beskeder om risikostyring er mutable. Når statussen for beskeder ændres, genereres der en ny log med det samme AlertID. Dette AlertID kan bruges til at korrelere opdateringer for en besked. |
| Kategori | Kategorien for beskeden er *InsiderRiskManagement*. Denne kategori kan bruges til at skelne fra disse beskeder fra andre sikkerhedsadvarsler & overholdelse af regler og standarder. |
| Kommentarer | Standardkommentarer til beskeden. Værdier er Ny *besked (logført* , når der oprettes en besked) og Besked *opdateret (* logført, når der er en opdatering af en besked). Brug AlertID til at korrelere opdateringer for en besked. |
| Data | Dataene til beskeden omfatter det entydige bruger-id, brugerens hovednavn og dato og klokkeslæt (UTC), når brugeren blev udløst til en politik. |
| Navn | Politiknavn for insider-politik for risikostyring, der genererede beskeden. |
| PolicyId | GUID'et for den Insider Risk Management-politik, der udløste beskeden. |
| Alvorsgrad | Beskedens alvorlighed. Værdierne er *Høj*, *Mellem* eller *Lav*. |
| Kilde | Kilden til beskeden. Værdien er Office 365 *Security & Compliance*. |
| Status | Beskedens status. Værdier er *aktive* (*Needs Review* i insider-risiko), *Undersøgelse* *(* Bekræftet i insider-risiko *), Løst* *(Løst* i insider-risiko), *Afvist* (*Afvist* i insider-risiko). |
| Version | Versionen af skemaet for sikkerheds- og overholdelsesbeskeder. |

Følgende felter og værdier eksporteres til insider-risikostyringsadvarsler til det [fælles Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema).

- UserId
- Id
- RecordType
- CreationTime
- Handling
- OrganizationId
- UserType
- UserKey

## <a name="priority-user-groups-preview"></a>Prioritet af brugergrupper (forhåndsvisning)

Brugere i organisationen kan have forskellige risikoniveauer afhængigt af deres placering, adgangsniveau til følsomme oplysninger eller risikohistorik. Prioritering af undersøgelse og pointdeling af disse brugeres aktiviteter kan hjælpe med at advare dig om potentielle risici, der kan have større konsekvenser for organisationen. Prioritet af brugergrupper i Insider Risk Management hjælper med at definere de brugere i organisationen, der har brug for nærmere inspektion og mere følsom risikoscore. I kombination med  brud på sikkerhedspolitik efter prioritetsbrugere og datalækager efter *prioritetsskabeloner* for brugere har brugere føjet til en prioriteret brugergruppe en øget sandsynlighed for insider-risikoadvarsler og -beskeder med højere alvorsgrad.

![Insider-indstillinger for risikostyringsprioritet for brugergrupper.](../media/insider-risk-settings-priority-users.png)

I stedet for at være åben for gennemgang af alle analytikere og grupper af prioritetsbrugere kan det også være nødvendigt at begrænse gennemgangsaktiviteterne til bestemte brugere eller insider-risikorollegrupper. Du kan vælge at tildele individuelle brugere og rollegrupper til at gennemgå brugere, beskeder, sager og rapporter for hver prioriteret brugergruppe. Prioritetsbrugergrupper kan have gennemgårtilladelser, der er tildelt de indbyggede *rollegrupper Insider Risk Management*, *Insider Risk Management-analytikere* og rollegrupper for *Insider Risk Management* , en eller flere af disse rollegrupper eller til et brugerdefineret udvalg af brugere.

Du skal f.eks. beskytte dig mod datalækager i forbindelse med et meget fortroligt projekt, hvor brugerne har adgang til følsomme oplysninger. Du vælger at oprette *Fortroligt Project*  Brugerprioritetsbrugergruppe for brugere i organisationen, der arbejder på dette projekt. Desuden bør denne prioritetsbrugergruppe ikke have brugere, beskeder, sager og rapporter, der er knyttet til gruppen, synlige for alle standardadministratorer, analytikere og administratorer for insider-risikostyring. I **Indstillinger** skal du oprette gruppen Fortrolige *Project* Brugeres prioritet og tildele to brugere som korrekturlæser, der kan få vist data, der er relateret til grupperne. Ved hjælp af guiden Politik og Datalækager efter prioritetens politikskabelon for brugere, kan du oprette en ny politik og tildele gruppen Fortrolige *Project* *Brugeres* prioritet til politikken. Aktiviteter, der skyldes politikken for medlemmer af gruppen *Fortroligt Project* Brugeres prioritet er mere følsomme over for risici, og disse brugeres aktiviteter vil være mere tilbøjelige til at generere en besked og have højere alvorsgrader.

### <a name="create-a-priority-user-group"></a>Opret en prioritetsbrugergruppe

Hvis du vil oprette en ny prioritetsbrugergruppe, skal du bruge indstillingskontrolelementerne i insider-risikostyringsløsningen i Microsoft 365 Overholdelsescenter. Hvis du vil oprette en prioriteret brugergruppe, skal du være medlem af *rollegruppen Insider Risk Management* eller *Insider Risk Management Administration* .

Udfør følgende trin for at oprette en prioriteret brugergruppe:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger**.
2. Vælg siden **Prioritetsbrugergrupper (eksempel** ).
3. På siden **Prioritetsbrugergrupper (forhåndsvisning)** skal du **vælge Opret prioritetsbrugergruppe** for at starte guiden til oprettelse af gruppe.
4. På siden **Navn og beskriv** skal du udfylde følgende felter:
    - **Navn (påkrævet)**: Angiv et brugervenligt navn til prioritetsbrugergruppen. Når du har fuldført guiden, kan du ikke ændre navnet på brugergruppen, der er prioritet.
    - **Beskrivelse (valgfrit)**: Angiv en beskrivelse af brugergruppens prioritet.
5. Vælg **Næste for** at fortsætte.
6. På siden **Vælg** medlemmer skal du vælge  Vælg medlemmer for at søge og vælge, hvilke mailaktiverede brugerkonti, der medtages i gruppen,  eller markere afkrydsningsfeltet Markér alt for at føje alle brugere i organisationen til gruppen. Vælg **Tilføj for** at fortsætte eller **Annuller** for at lukke uden at føje brugere til gruppen.
7. Vælg **Næste for** at fortsætte.
8. På siden **Vælg, hvem der** kan få vist denne gruppe skal du definere, hvem der kan gennemse brugere, beskeder, sager og rapporter for brugergruppens prioritet. Der skal tildeles mindst én rollegruppe for bruger- eller insider-risikostyring. Vælg **Vælg brugere og rollegrupper,** og vælg de brugere eller Insider-rollegrupper for risikostyring, du vil tildele den prioriteret brugergruppe. Vælg **Tilføj** for at tildele de valgte brugere eller rollegrupper til gruppen.
9. Vælg Næste for at fortsætte.
10. På siden **Gennemse** skal du gennemgå de indstillinger, du har valgt for brugergruppens prioritet. Vælg Rediger **links** for at ændre nogen af gruppeværdierne, eller vælg **Send** for at oprette og aktivere prioritetsbrugergruppen.
11. På bekræftelsessiden skal du vælge **Udført** for at afslutte guiden.

### <a name="update-a-priority-user-group"></a>Opdatere en prioritetsbrugergruppe

Hvis du vil opdatere en eksisterende prioriteret brugergruppe, skal du bruge indstillingskontrolelementerne i **Insider-risikostyringsløsningen** i Microsoft 365 Overholdelsescenter. Hvis du vil opdatere en prioriteret brugergruppe, skal du være medlem af *rollegruppen Insider Risk Management* eller *Insider Risk Management Administration* .

Udfør følgende trin for at redigere en prioriteret brugergruppe:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger**.
2. Vælg siden **Prioritetsbrugergrupper (eksempel** ).
3. Vælg den prioritetsbrugergruppe, du vil redigere, og **vælg Rediger gruppe**.
4. På siden **Navn og beskriv** skal du opdatere feltet Beskrivelse, hvis det er nødvendigt. Du kan ikke opdatere navnet på prioritetsbrugergruppen. Vælg **Næste for** at fortsætte.
5. På siden **Vælg medlemmer** skal du føje nye medlemmer til gruppen ved hjælp af **kontrolelementet Vælg** medlemmer. Hvis du vil fjerne en bruger fra gruppen, skal du vælge X'et ud for den bruger, du vil fjerne. Vælg **Næste for** at fortsætte.
6. På siden **Vælg, hvem** der kan få vist denne gruppe skal du tilføje eller fjerne brugere eller rollegrupper, som kan gennemse brugere, beskeder, sager og rapporter for brugergruppens prioritet.
7. Vælg **Næste for** at fortsætte.
8. På siden **Gennemse** skal du gennemgå de opdateringsindstillinger, du har valgt til prioritetsbrugergruppen. Vælg Rediger **links** for at ændre nogen af gruppeværdierne, eller vælg Send **for** at opdatere prioritetsbrugergruppen.
9. På bekræftelsessiden skal du vælge **Udført** for at afslutte guiden.

### <a name="delete-a-priority-user-group"></a>Slet en prioritetsbrugergruppe

Hvis du vil slette en eksisterende prioritetsbrugergruppe, skal du bruge indstillingskontrolelementerne i **Insider-risikostyringsløsningen** i Microsoft 365 Overholdelsescenter. Hvis du vil slette en prioriteret brugergruppe, skal du være medlem af *rollegruppen Insider Risk Management* eller *Insider Risk Management Administration* .

> [!IMPORTANT]
> Hvis du sletter en prioritetsbrugergruppe, fjernes den fra enhver aktiv politik, den er tildelt til. Hvis du sletter en prioritetsbrugergruppe, der er tildelt en aktiv politik, indeholder politikken ikke nogen in-scope-brugere og vil i praksis være inaktiv og vil ikke oprette beskeder.

Udfør følgende trin for at slette en prioriteret brugergruppe:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger**.
2. Vælg siden **Prioritetsbrugergrupper (eksempel** ).
3. Vælg den prioritetsbrugergruppe, du vil redigere, **og vælg** Slet i dashboardmenuen.
4. I dialogboksen **Slet skal** du vælge Ja **for at slette** prioritetsbrugergruppen eller vælge **Annuller** for at vende tilbage til dashboardet.

## <a name="priority-physical-assets-preview"></a>Prioritet af fysiske aktiver (forhåndsvisning)

At identificere adgang til prioritet af fysiske aktiver og korrelering af adgangsaktivitet til brugerbegivenheder er en vigtig komponent i din overholdelsesinfrastruktur. Disse fysiske aktiver repræsenterer prioritetsplaceringer i organisationen, f.eks. virksomhedens bygninger, datacentre eller serverrum. Insider-risikoaktiviteter kan være knyttet til brugere, der arbejder usædvanligt mange timer, forsøger at få adgang til disse uautoriserede følsomme eller sikre områder og anmoder om adgang til områder på højt niveau uden legitime behov.

Når prioritet af fysiske aktiver er aktiveret, og forbindelseselementet Fysisk [badging af data](import-physical-badging-data.md) er konfigureret, integrerer Insider-risikostyring signaler fra din fysiske kontrol og adgangssystemer med andre brugerrisici. Ved at undersøge adfærdsmønstre på tværs af fysiske adgangssystemer og korrelere disse aktiviteter med andre insider-risikohændelser kan Insider Risk Management hjælpe brugere og analytikere med at træffe mere informerede svarbeslutninger vedrørende beskeder. Adgang til prioritet af fysiske aktiver får point og identificeres i indsigter, der er anderledes end adgang til ikke-prioritetsaktiver.

Organisationen har f.eks. et badging-system for brugere, der overvåger og godkender fysisk adgang til normalt arbejde og følsomme projektområder. Du har flere brugere, der arbejder på et følsomt projekt, og disse brugere vender tilbage til andre områder i organisationen, når projektet er fuldført. Efterhånden som det følsomme projekt nærmer sig sin afslutning, skal du sikre dig, at projektarbejdet forbliver fortroligt, og at adgangen til projektområderne er styret stramt.

Du vælger at aktivere dataforbindelse for Fysisk badging i Microsoft 365 for at importere adgangsoplysninger fra dit fysiske ugyldige system og angive prioritets fysiske aktiver i insider-risikostyring. Ved at importere oplysninger fra dit badgingsystem og korrelere fysiske adgangsoplysninger med andre risikoaktiviteter, der er identificeret i Insider Risk Management, bemærker du, at en af brugerne på projektet har adgang til projektkontorerne efter normal arbejdstid, og at den også eksporterer store mængder data til en personlig skylagringstjeneste fra deres normale arbejdsområde. Denne fysiske adgangsaktivitet, der er knyttet til onlineaktiviteten, kan pege på mulige datatyveri og overholdelse af regler og standarder, og analytikere kan udføre de relevante handlinger efter omstændighederne for denne bruger.

![Insider-prioritering af fysiske aktiver i risikostyring.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Konfigurere prioritet af fysiske aktiver

Hvis du vil konfigurere prioritet af fysiske aktiver, skal du konfigurere forbindelsen Fysisk badging og bruge indstillingskontrolelementerne i **Insider-risikostyringsløsningen** Microsoft 365 Overholdelsescenter. Hvis du vil konfigurere prioritet af fysiske aktiver, skal du være medlem af *rollegruppen Insider Risk Management* eller *Insider Risk Management Administration*.

Udfør følgende trin for at konfigurere prioritet af fysiske aktiver:

1. Følg konfigurationstrinnene for insider-risikostyring i [artiklen Introduktion til Insider Risk](insider-risk-management-configure.md) Management. I trin 3 skal du sørge for at konfigurere forbindelsen Fysisk badging.

    > [!IMPORTANT]
    > For at insider-risikostyringspolitikker kan bruge og korrelere signaldata, der er relateret til brugere, der forlader og afslutter, med begivenhedsdata fra din fysiske kontrol og adgangsplatforme, skal du også konfigurere Microsoft 365 HR-forbindelsen. Hvis du aktiverer forbindelsen Fysisk badging uden at aktivere Microsoft 365 HR-forbindelsen, behandler politikkerne for insider-risikostyring kun hændelser for fysiske adgangsaktiviteter for brugere i organisationen.

2. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillingerPrioritets** >  **fysiske aktiver**.
3. På siden  Prioritet for fysiske aktiver kan du enten manuelt tilføje de fysiske aktiv-iD'er, du vil holde øje med, for de aktivhændelser, der importeres af forbindelsen Fysisk badging, eller du kan importere en .csv-fil med alle fysiske aktiv-iD'er, der importeres af den fysiske ugyldige forbindelse: a) Hvis du manuelt vil tilføje fysiske aktivers ID'er, skal du vælge Tilføj prioritets fysiske **aktiver.**  Angiv et id for det fysiske aktiv, og vælg **derefter Tilføj**. Angiv andre fysiske aktiv-ID'er, og vælg derefter **Tilføj fysiske prioritetsaktiver for** at gemme alle de angivne aktiver.
    b) Hvis du vil tilføje en liste over fysiske aktiv-.csv, skal du vælge **Importér fysiske aktiver for prioritet**. I dialogboksen Stifinder skal du vælge den .csv fil, du vil importere, og derefter vælge **Åbn**. De fysiske aktiv-.csv på listen.
4. Gå til siden **Politikindikatorer** i **Indstillinger**.
5. På siden **Politikindikatorer skal** du gå til sektionen  Indikatorer for fysisk adgang og markere afkrydsningsfeltet for Fysisk adgang efter afslutning eller **mislykket adgang til følsomt aktiv**.
6. Vælg **Gem for** at konfigurere og afslutte.

### <a name="delete-a-priority-physical-asset"></a>Slette et fysisk prioritetsaktiv

Hvis du vil slette et eksisterende fysisk prioritetsaktiv, skal du bruge indstillingskontrolelementerne i insider-risikostyringsløsningen Microsoft 365 Overholdelsescenter. Hvis du vil slette et prioritets fysisk aktiv, skal du være medlem af rollegruppen Insider Risk Management eller Insider Risk Management Administration.

> [!IMPORTANT]
> Når du sletter et fysisk prioritetsaktiv, fjernes det fra undersøgelse med en aktiv politik, som det tidligere er medtaget i. Beskeder, der genereres af aktiviteter, der er knyttet til det fysiske prioritetsaktiv, slettes ikke.

Udfør følgende trin for at slette et prioritets fysisk aktiv:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillingerPrioritets** >  **fysiske aktiver**.
2. På siden **Prioritet for fysiske aktiver** skal du vælge det aktiv, du vil slette.
3. Vælg **Slet** i handlingsmenuen for at slette aktivet.

## <a name="power-automate-flows-preview"></a>Power Automate flows (forhåndsvisning)

[Microsoft Power Automate er](/power-automate/getting-started) en arbejdsprocestjeneste, der automatiserer handlinger på tværs af programmer og tjenester. Ved hjælp af flows fra skabeloner eller oprettet manuelt kan du automatisere almindelige opgaver, der er knyttet til disse programmer og tjenester. Når du aktiverer Power Automate for Insider Risk Management, kan du automatisere vigtige opgaver for sager og brugere. Du kan konfigurere Power Automate flows til at hente bruger-, besked- og sagsoplysninger og dele disse oplysninger med interessenter og andre programmer samt automatisere handlinger i insider-risikostyring, f.eks. at skrive til sagsnoter. Power Automate flows er gældende for tilfælde og alle brugere, som er omfattet af en politik.

Kunder med Microsoft 365, der omfatter insider-risikostyring, behøver ikke yderligere Power Automate-licenser for at bruge de anbefalede insider-risikostyringsskabeloner Power Automate skabeloner. Disse skabeloner kan tilpasses, så de understøtter din organisation og dækker centrale insider-scenarier for risikostyring. Hvis du vælger at bruge Premium Power Automate-funktioner i disse skabeloner, oprette en brugerdefineret skabelon ved hjælp af Microsoft 365-overholdelsesforbindelse eller bruge Power Automate-skabeloner til andre overholdelsesområder i Microsoft 365, har du muligvis brug for flere Power Automate-licenser.

De følgende Power Automate leveres til kunder til at understøtte proces automatisering for insider-brugere og -sager for risikostyring:

- Giv brugerne besked, når de føjes til en **Insider-risikopolitik**: Denne skabelon er til organisationer, der har interne politikker, beskyttelse af personlige oplysninger eller lovmæssige krav, som brugere skal have besked om, når de er underlagt insider-politikker for risikostyring. Når dette flow konfigureres og vælges for en bruger på siden Brugere, sendes brugere og deres ledere en mail, når brugeren føjes til en insider-politik for risikostyring. Denne skabelon understøtter også opdatering af en liste SharePoint, der er hostet på et SharePoint-websted, for at hjælpe med at spore meddelelse oplysninger som f.eks. dato/klokkeslæt og modtageren af meddelelsen. Hvis du har valgt at anonymisere brugere i indstillinger for beskyttelse af personlige **oplysninger, vil** flows, der er oprettet ud fra denne skabelon, ikke fungere efter hensigten, så brugernes beskyttelse af personlige oplysninger bevares. Power Automate flows ved hjælp af denne skabelon er tilgængelige på **dashboardet Brugere**.
- Anmod om oplysninger fra HR eller virksomheder om en bruger i en **insider-risikosag**: Når du handler på en sag, kan insider risk analysts og analytikere have brug for at rådføre sig med HR eller andre interessenter for at forstå konteksten for sagsaktiviteterne. Når dette flow er konfigureret og valgt for en sag, sender analytikere og virksomheder en mail til HR og virksomheds interessenter, der er konfigureret til dette flow. Hver modtager får tilsendt en meddelelse med forudkonfigurerede eller brugerdefinerede svarindstillinger. Når modtagerne vælger en svarindstilling, registreres svaret som en casenote og indeholder oplysninger om modtager og dato/klokkeslæt. Hvis du har valgt at anonymisere brugere i indstillinger for beskyttelse af personlige **oplysninger, vil** flows, der er oprettet ud fra denne skabelon, ikke fungere efter hensigten, så brugernes beskyttelse af personlige oplysninger bevares. Power Automate flows ved hjælp af denne skabelon er tilgængelige på **dashboardet Sager**.
- **Giv manager besked, når en bruger har en insider-risikobesked**: Nogle organisationer skal muligvis have øjeblikkelig besked om administration, når en bruger har en insider-besked om risikostyring. Når dette flow er konfigureret og valgt, sendes lederen for sagsbrugeren en mail med følgende oplysninger om alle vigtige beskeder om sager:
    - Gældende politik for beskeden
    - Dato/klokkeslæt for beskeden
    - Beskedens alvorsniveau

    Flowet opdaterer automatisk sagsnoterne, som meddelelsen blev sendt, og at flowet blev aktiveret. Hvis du har valgt at anonymisere brugere i indstillinger for beskyttelse af personlige **oplysninger, vil** flows, der er oprettet ud fra denne skabelon, ikke fungere efter hensigten, så brugernes beskyttelse af personlige oplysninger bevares. Power Automate flows ved hjælp af denne skabelon er tilgængelige på **dashboardet Sager**.
- **Opret en post for insider-risikosag i ServiceNow**: Denne skabelon er til organisationer, der vil bruge deres ServiceNow-løsning til at spore insider-sager i risikostyring.  Når det er tilfældet, kan Insider Risk-analytikere og -analysemedarbejdere oprette en post for sagen i ServiceNow. Du kan tilpasse denne skabelon til at udfylde valgte felter i ServiceNow baseret på organisationens krav. Power Automate flows ved hjælp af denne skabelon er tilgængelige på **dashboardet Sager**. Du kan finde flere oplysninger om tilgængelige ServiceNow-felter i [artiklen ServiceNow Connector-reference](/connectors/service-now/) .

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Opret et Power Automate fra skabelonen insider-risikostyring

Hvis du vil oprette et Power Automate-flow fra en anbefalet skabelon til insider-risikostyring, skal du bruge indstillingskontrolelementerne i  Insider-risikostyringsløsningen i Microsoft 365 Overholdelsescenter eller indstillingen **Administrer Power Automate** flow fra kontrolelementet **Automatiser**, når der arbejdes direkte i **Dashboardene Sager** **eller Brugere**.

For at oprette Power Automate administratorflow i indstillingsområdet skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. For at oprette Power Automate flow med indstillingen **Administrer Power Automate flows** skal du være medlem af mindst én insider-rollegruppe for risikostyring.

Udfør følgende trin for at oprette et Power Automate flow fra en anbefalet skabelon til insider-risikostyring:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger Power Automate** >  **flows**. Du kan også få adgang fra **siderne med Sager** **eller Brugere-dashboards** ved at vælge **AutomateManage** >  **Power Automate flows**.
2. På siden **Power Automate flow skal** du vælge en anbefalet skabelon fra **sektionen Insider-skabeloner** til risikostyring, som du kan lide på siden.
3. Flowet viser de integrerede forbindelser, der skal bruges til flowet, og bemærker, om forbindelsesstatusserne er tilgængelige. Hvis det er nødvendigt, skal du opdatere eventuelle forbindelser, der ikke vises som tilgængelige. Vælg **Fortsæt**.
4. Som standard er de anbefalede flows forudkonfigureret med de anbefalede insider-risikohåndterings- og Microsoft 365-tjenestedatafelter, der kræves for at fuldføre den tildelte opgave for flowet. Hvis det er nødvendigt, kan du tilpasse flowkomponenterne ved hjælp **af** kontrolelementet Vis avancerede indstillinger og konfigurere de tilgængelige egenskaber for flowkomponenten.
5. Hvis det er nødvendigt, kan du føje andre trin til flowet ved at **vælge knappen Nyt** trin. I de fleste tilfælde skal dette ikke bruges til de anbefalede standardskabeloner.
6. Vælg **Gem kladde** for at gemme flowet til yderligere konfiguration, eller vælg **Gem** for at fuldføre konfigurationen af flowet.
7. Vælg **Luk** for at vende tilbage **Power Automate flowsiden**. Den nye skabelon vises som et flow på fanerne Mine  flow og er automatisk tilgængelig fra rullekontrolelementet **Automate**, når der arbejdes med Insider-sager til risikostyring for brugeren, der opretter flowet.

> [!IMPORTANT]
> Hvis andre brugere i organisationen skal have adgang til flowet, skal flowet deles.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Opret et brugerdefineret Power Automate for Insider Risk Management

Nogle processer og arbejdsprocesser for din organisation kan være uden for de anbefalede insider-risikostyringsflowskabeloner, og du har muligvis behov for at oprette brugerdefinerede Power Automate-flow for insider-risikostyringsområder. Power Automate flows er fleksible og understøtter omfattende tilpasning, men der er trin, der skal tages for at integrere med insider-funktioner til risikostyring.

Udfør følgende trin for at oprette en Power Automate skabelon til insider-risikostyring:

1. **Tjek din Power Automate flowlicens**: Hvis du vil oprette tilpassede Power Automate flows, der bruger Insider Risk Management-udløsere, skal du have en Power Automate licens. De anbefalede skabeloner til insider-risikostyringsflow kræver ikke ekstra licenser og er inkluderet som en del af din insider risk management-licens.
2. **Opret et automatiseret flow**: Opret et flow, der udfører en eller flere opgaver, efter det er udløst af en Insider Risk Management-begivenhed. Hvis du vil have mere at vide om, hvordan du opretter et automatiseret flow, [skal du se Opret et flow Power Automate](/power-automate/get-started-logic-flow).
3. **Vælg Microsoft 365 overholdelsesforbindelse**: Søg efter, og vælg Microsoft 365 overholdelsesforbindelse. Denne forbindelse aktiverer insider-udløsere og handlinger til risikostyring. Du kan finde flere oplysninger om forbindelser i artiklen [Oversigt over forbindelser](/connectors/connector-reference/) .
4. **Vælg insider-udløsere til dit flow**: Insider-risikostyring har to udløsere tilgængelige for brugerdefinerede Power Automate flow:
    - **For en valgt insider-sag til risikostyring**: Flows med denne udløser kan vælges fra dashboardsiden Insider Risk Management Cases.
    - **For en valgt insider-bruger til risikostyring**: Flows med denne udløser kan vælges fra insider-administrationssiden brugeres dashboard.
5. Vælg Insider-handlinger til risikostyring for dit flow: Du kan vælge mellem flere handlinger, som Insider Risk Management kan medtage i dit brugerdefinerede flow:
    - Få besked om insider-risikostyring
    - Få insider-sag til risikostyring
    - Få insider-bruger til risikostyring
    - Få insider-beskeder om risikostyring for en sag
    - Tilføj insider-casenote til risikostyring

### <a name="share-a-power-automate-flow"></a>Del et Power Automate flow

Som standard er Power Automate, der er oprettet af en bruger, kun tilgængelige for den pågældende bruger. For at andre brugere af Insider Risk Management kan få adgang til og bruge et flow, skal flowet deles af flowudvikleren. Hvis du vil dele et flow, skal du bruge indstillingerne i   Insider-risikostyringsløsningen i Microsoft 365 Overholdelsescenter eller indstillingen **Administrer Power Automate flows** fra kontrolelementet Automatiser, når du arbejder direkte i dashboardsiderne Sager eller Brugere. Når du har delt et flow, kan alle, som det er blevet delt med, få adgang til flowet i rullelisten **Automate** control i **sags** - **og brugerdashboards**.

For at dele Power Automate flow i indstillingsområdet skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. For at dele Power Automate flow med indstillingen **Administrer Power Automate flows** skal du være medlem af mindst én insider-rollegruppe for risikostyring.

Udfør følgende trin for at dele et Power Automate flow:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger Power Automate** >  **flows**. Du kan også få adgang fra **siderne med Sager** **eller Brugere-dashboards** ved at vælge **AutomateManage** >  **Power Automate flows**.
2. På siden **Power Automate flows** skal du vælge **fanen Mine flow** **eller Teamflows**.
3. Vælg flowet, der skal deles, og vælg **derefter Del** i menuen med indstillinger for flow.
4. På siden flowdeling skal du skrive navnet på den bruger eller gruppe, du vil tilføje som ejer for flowet.
5. I dialogboksen **Forbindelse brugt** skal du vælge **OK for** at bekræfte, at den tilføjede bruger eller gruppe har fuld adgang til flowet.

### <a name="edit-a-power-automate-flow"></a>Rediger et Power Automate flow

Hvis du vil redigere et flow, skal du bruge indstillingerne i **Insider-risikostyringsløsningen** i Microsoft 365 Overholdelsescenter eller  indstillingen **Administrer Power Automate flow** **fra** kontrolelementet **Automatiser**, når du arbejder direkte i dashboardet Sager eller Brugere.

For at redigere Power Automate flow i indstillingsområdet skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. For at redigere Power Automate flow med indstillingen **Administrer Power Automate flows** skal du være medlem af mindst én insider-rollegruppe for risikostyring.

Udfør følgende trin for at redigere et Power Automate flow:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger Power Automate** >  **flows**. Du kan også få adgang fra **siderne med Sager** **eller Brugere-dashboards** ved at vælge **AutomateManage** >  **Power Automate flows**.
2. På siden **Power Automate flow skal** du vælge et flow, der skal redigeres, og **vælge** Rediger i flowkontrolmenuen.
3. Vælg **ellipsen for** >  **Indstillinger at** ændre en indstilling for flowkomponent eller **ellipseSlette**  >  for at slette en flowkomponent.
4. Vælg **Gem og** derefter **Luk for at** fuldføre redigeringen af flowet.

### <a name="delete-a-power-automate-flow"></a>Slet et Power Automate flow

Hvis du vil slette et flow, skal du bruge indstillingerne i  Insider-risikostyringsløsningen i Microsoft 365 Overholdelsescenter eller indstillingen **Administrer Power Automate flows** fra kontrolelementet **Automatiser**, når du arbejder direkte i **dashboardet** Sager eller Brugere. Når et flow slettes, fjernes det som en indstilling for alle brugere.

Hvis du vil Power Automate dataflow i indstillingsområdet, skal du være medlem af rollegruppen *Insider Risk Management* eller *Insider Risk Management Administration*. For at slette Power Automate flow med indstillingen **Administrer Power Automate flows** skal du være medlem af mindst én insider-rollegruppe for risikostyring.

Udfør følgende trin for at slette et Power Automate flow:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring og** vælge **Insider-risikoindstillinger Power Automate** >  **flows**. Du kan også få adgang fra **siderne med Sager** **eller Brugere-dashboards** ved at vælge **AutomateManage** >  **Power Automate flows**.
2. På siden **Power Automate flow skal** du vælge et flow, der skal slettes, **og vælge Slet** i flowkontrolmenuen.
3. I bekræftelsesdialogboksen for sletning skal du **vælge Slet** for at fjerne flowet eller vælge **Annuller** for at afslutte sletningshandlingen.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (eksempel)

Analytikere og analytikere for overholdelse af regler og standarder kan Microsoft Teams til samarbejde om insider-sager inden for risikostyring. De kan koordinere og kommunikere med andre interessenter i Microsoft Teams at:

- Koordinere og gennemse svaraktiviteter for sager i private Teams kanaler
- Del og gem filer og beviser i forbindelse med individuelle sager på sikker måde
- Spore og gennemgå svaraktiviteter for analytikere og analytikere

Når Microsoft Teams er aktiveret til insider-risikostyring, oprettes der et dedikeret Microsoft Teams team, hver gang en besked bekræftes, og der oprettes en sag. Som standard omfatter teamet automatisk alle medlemmer af *rollegrupperne Insider Risk Management*, *Insider Risk Management-analytikere* og *insider-risikoadministrationsgrupper* (op til 100 startbrugere). Yderligere organisationens bidragydere kan føjes til teamet, efter det er blevet oprettet og efter behov. For eksisterende sager, der er oprettet før aktivering af Microsoft Teams, kan analytikere og virksomheder vælge at oprette et nyt Microsoft Teams-team, når der arbejdes i en sag, hvis det er nødvendigt.  Når du løser den tilknyttede sag i Insider Risk Management, arkiveres teamet automatisk (flyttes til skjult og skrivebeskyttet).

Hvis du vil have mere at vide om, hvordan du bruger teams og kanaler Microsoft Teams, skal du se Oversigt over [teams og kanaler Microsoft Teams](/MicrosoftTeams/teams-channels-overview).

Det er Microsoft Teams hurtigt og nemt at konfigurere support til sager. Hvis du vil Microsoft Teams administration af Insider-risici, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter,](https://compliance.microsoft.com) skal du gå **til Insider Risk ManagementInsider** >  **risikoindstillinger**.
2. Vælg **Microsoft Teams** side.
3. Aktivér Microsoft Teams integration for Insider Risk Management.
4. Vælg **Gem for** at konfigurere og afslutte.

![Insider-Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Opret et Microsoft Teams team til eksisterende sager

Hvis du Microsoft Teams support til insider-risikostyring, når du har eksisterende sager, skal du manuelt oprette et team for hver sag efter behov. Når du Microsoft Teams support i indstillingerne for insider-risikostyring, vil nye sager automatisk oprette en ny Microsoft Teams team.

Brugere skal have tilladelse til at Microsoft 365 grupper i organisationen for at kunne oprette Microsoft Teams team fra en sag. Du kan finde flere oplysninger om administration af tilladelser Microsoft 365 grupper i Administrer, [hvem der kan Microsoft 365 grupper](../solutions/manage-creation-of-groups.md).

Hvis du vil oprette et team til en sag, skal du bruge kontrolelementet Opret Microsoft Team, når du arbejder direkte i en eksisterende sag. Udfør følgende trin for at oprette et nyt team:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider Risk** **ManagementCases** >  og vælge en eksisterende sag.
2. I menuen til sagshandling skal du vælge **Opret Microsoft Team**.
3. I feltet **Teamnavn** skal du skrive et navn til den nye Microsoft Teams team.
4. Vælg **Opret Microsoft-team** , og vælg derefter **Luk**.

Afhængigt af antallet af brugere, der er tildelt rollegrupper inden for insider-risikostyring, kan det tage 15 minutter, før alle analytikere og analytikere føjes til Microsoft Teams-teamet for en sag.

## <a name="analytics"></a>Analyse

Insider-risikoanalyse gør det muligt at gennemføre en evaluering af potentielle insider-risici i organisationen uden at konfigurere insider-risikopolitikker. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisici og hjælpe med at bestemme typen og omfanget af de insider-risikostyringspolitikker, du kan overveje at konfigurere. Analysescanninger har følgende fordele for din organisation:

- Nem at konfigurere: For at komme i gang med analysescanninger kan du vælge Kør scanning, når du bliver bedt om det af analyse anbefalingen, eller gå til Insider-risikoindstillingerAnalytics  >  og aktivere analyser.
- Beskyttelse af personlige oplysninger efter design: Scanningsresultater og indsigt returneres som aggregeret og anonymiseret brugeraktivitet, individuelle brugernavne kan ikke identificeres af korrekturlæsere.
- Forstå potentielle risici via konsolideret indsigt: Scanningsresultater kan hjælpe dig med hurtigt at identificere potentielle risikoområder for dine brugere, og hvilken politik der bedst kan hjælpe med at reducere disse risici.

Se videoen [Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) for at hjælpe med at forstå, hvordan analyser kan hjælpe med at fremskynde identifikationen af potentielle insider-risici og hjælpe dig med hurtigt at reagere.

Analysescanninger af risikoaktivitetshændelser fra flere kilder for at hjælpe med at identificere indsigt i potentielle risikoområder. Afhængigt af din aktuelle konfiguration søger analyser efter kvalificerende risikoaktiviteter på følgende områder:

- **Microsoft 365: Inkluderet** i alle scanninger er dette den primære kilde til at identificere de fleste af de potentielt risikabele aktiviteter.
- **Exchange Online**: Inkluderet i alle scanninger hjælper Exchange Online med at identificere aktiviteter, hvor data i vedhæftede filer sendes til eksterne kontakter eller tjenester.
- **Azure Active Directory**: Oversigten er inkluderet i alle Azure Active Directory scanninger og hjælper med at identificere risikabele aktiviteter, der er knyttet til brugere med slettede brugerkonti.
- **Microsoft 365 HR-dataforbindelse: Hvis** konfigureret, hjælper hændelser i HR-forbindelsen med at identificere risikabelt arbejde, der er knyttet til brugere, der har kommende eller kommende datoer for opsigelse.

Analyseindsigt fra scanninger er baseret på de samme risikoaktivitetssignaler, der bruges af insider-politikker til risikostyring, og rapporterer resultater baseret på både enkelt- og sekvensbaserede brugeraktiviteter. Men risikoscore for analyse er baseret på op til 10 dages aktivitet, mens politikker for insider-risiko bruger daglig aktivitet til indsigt. Når du aktiverer og kører analyser i din organisation første gang, får du vist scanningsresultaterne for én dag. Hvis du lader analyse være aktiveret, får du vist resultaterne af hver daglig scanning føjet til Insight-rapporterne for et interval for de seneste 10 dages aktivitet.

### <a name="enable-analytics-and-start-your-scan"></a>Aktivér analyse, og start din scanning

For at aktivere Insider Risk Analytics skal du være medlem af *Insider Risk Management*, *Insider Risk Management-administrator* *eller Microsoft 365 globale administratorrollegruppe*.
Udfør følgende trin for at aktivere Insider Risk Analytics:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring**.
2. Vælg **Kør scanning** på **scanningen for insider-risici i dit organisationskort** på fanen Oversigt over **insider-risikohåndtering** . Dette aktiverer analysescanning for din organisation. Du kan også aktivere scanning i din organisation ved at navigere til Insider-risikoindstillingerAnalytics  >  og aktivere Scan din lejers brugeraktivitet for at identificere **potentielle insiderrisici**.
3. På **detaljeruden Analyse skal** du vælge **Kør scanning for** at starte scanningen for din organisation. Analysescanningsresultater kan tage op til 48 timer, før indsigter er tilgængelige som rapporter til gennemsyn.

![Insider-indstillinger for risikostyringsanalyse.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Få vist analyseindsigt og oprette nye politikker

Når den første analysescanning er fuldført for din organisation, vil medlemmer af rollegruppen for *Insider Risk Management-administrator* automatisk modtage en mail og kan få vist den indledende indsigt og anbefalinger til potentielt risikabelt aktiviteter fra dine brugere. Daglige scanninger fortsætter, medmindre du deaktiverer analyser for organisationen. Mailbeskeder til administratorer leveres til hver af de tre kategorier for analyse (datalækager, tyveri og udfyldning) efter den første aktivitet i organisationen. Mailbeskeder sendes ikke til administratorer til registrering af opfølgningsaktivitet, som opstår som følge af de daglige scanninger. Hvis analyser i **Insider-risikostyring** >  **Indstillinger** >  **Analytics** deaktiveres og derefter genaktiveres i din organisation, nulstilles automatiske mailmeddelelser, og der sendes mails til medlemmer af rollegruppen *insider-administrator* for ny scanningsindsigt.

Hvis du vil have vist potentielle risici for din organisation **, skal du** gå til fanen Oversigt og vælge **Vis resultater på** **kortet Insider-risikoanalyse** . Hvis scanningen for din organisation ikke er fuldført, får du vist en meddelelse om, at scanningen stadig er aktiv.

![Insider-kortet til analyse af risikostyring.](../media/insider-risk-analytics-ready-card.png)

Ved fuldførte scanninger får du vist de potentielle risici, der opdages i din organisation, samt viden og anbefalinger til at tage hånd om disse risici. Identificerede risici og specifik viden er inkluderet i rapporter grupperet efter område, det samlede antal brugere med identificerede risici, procentdelen af disse brugere med potentielt risikabelt aktiviteter og en anbefalet insider-risikopolitik for at hjælpe med at reducere disse risici. Rapporterne omfatter:

- **Datalækageindsigt**: Aktiviteter for alle brugere, der kan omfatte utilsigtet overdeling af oplysninger uden for organisationen, eller datalækager fra brugere med ondsindede hensigter.
- **Datatyveriindsigt**: Aktiviteter til brugere, der forlader organisationen, eller brugere med slettede Azure Active Directory-konti, som kan omfatte risikabel deling af oplysninger uden for organisationen eller datatyveri fra brugere med ondsindede hensigter.
- **Mest populære indsigt i udfyldning**: Aktiviteter af alle brugere, som kan omfatte deling af data uden for organisationen.

![Oversigtsrapport for Insiders til risikostyringsanalyse.](../media/insider-risk-analytics-overview.png)

For at få vist flere oplysninger for at få et indblik skal **du vælge Vis detaljer** for at få vist detaljeruden for indsigten. Detaljeruden indeholder de komplette indsigtsresultater, en anbefaling for insider-risikopolitik og knappen  Opret politik, der hurtigt kan hjælpe dig med at oprette den anbefalede politik. Når du vælger Opret politik, kommer du til guiden politik og vælger automatisk den anbefalede politikskabelon, der er relateret til indsigten. Hvis analyseindsigtet f.eks.  er for datalækageaktivitet, vil skabelonen Generel politik for *datalækager* være valgt på forhånd i guiden til politik for dig.

![Detaljerapport for Insiders til risikostyringsanalyse.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Slå analyse fra

For at deaktivere Insider Risk Analytics skal du være medlem af *Insider Risk Management*, *Insider Risk Management-administrator* eller Microsoft 365 *globale administratorrollegruppe*. Når du deaktiverer analyser, forbliver analysers indsigtsrapporter statiske og opdateres ikke for nye risici.

Udfør følgende trin for at deaktivere Insider Risk Analytics:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring**.
2. Vælg **siden Insider risk** **settingsAnalytics** > .
3. På siden **Analytics** skal du slå Scan din **lejers brugeraktivitet fra for at identificere potentielle insiderrisici**.

## <a name="admin-notifications"></a>Administratormeddelelser

Administratormeddelelser sender automatisk en mail til brugere, der er inkluderet i *rollegrupperne Insider Risk Management*, *Insider Risk Management-analytikere* og *insider-risikoadministrationsgrupper* , når den første advarsel genereres for en ny politik. Dette er aktiveret som standard for alle organisationer, og politikker kontrolleres hver 24 timer for første gang. Meddelelser sendes ikke for beskeder, der forekommer i politikker efter den første besked.

Hvis du har aktiveret Insider Risk Management Analytics for din organisation, modtager medlemmer af rollegruppen for *Insider Risk Management-administrator* automatisk en mailmeddelelse for indledende analyseindsigt om datalækager, tyveri og udfyldningsaktiviteter.

Hvis du foretrækker at deaktivere administratormeddelelser, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter,](https://compliance.microsoft.com) skal du gå **til Insider Risk ManagementInsider** >  **risikoindstillinger**.
2. Vælg siden **Administratormeddelelser** .
3. Fjern markeringen i afkrydsningsfeltet for følgende indstillinger, alt efter hvad der er relevant:
    - **Send en mail, når den første besked genereres for en ny politik**
    - **Send en mail, når en ny indsigt er tilgængelig i Analytics**
    - **Send en mail, når Analytics er slået fra**

4. Vælg **Gem for** at konfigurere og afslutte.

![Indstillinger for insider-beskeder til administratorer af risikostyring.](../media/insider-risk-admin-notifications.png)
