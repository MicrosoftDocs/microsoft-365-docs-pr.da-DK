---
title: Onboarding ved hjælp Microsoft Endpoint Configuration Manager
description: Få mere at vide om, hvordan du kommer i gang med Microsoft Defender til slutpunkt ved hjælp Microsoft Endpoint Configuration Manager
keywords: onboarding, konfiguration, installation, installation, slutpunktskonfigurationsstyring, Microsoft Defender til slutpunkt, oprettelse af samling, svar på registrering af slutpunkt, næste generations beskyttelse, reduktion af angrebsoverfladen, konfigurationsstyring til Microsoft-slutpunkt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a4668969982563bdc050a8e71b00980d52a7e6ff
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63603010"
---
# <a name="onboarding-using-microsoft-endpoint-configuration-manager"></a>Onboarding ved hjælp Microsoft Endpoint Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Denne artikel er en del af Installationsvejledningen og fungerer som et eksempel på onboardingmetoden.

I emnet [Planlægning](deployment-strategy.md) var der flere forskellige metoder for onboardingenheder til tjenesten. Dette emne omhandler arkitekturen for samtidig administration.

![Billede af skybaseret arkitektur.](images/co-management-architecture.png)
 *Diagram over miljøarkitekturer*

Mens Defender til Slutpunkt understøtter onboarding af forskellige slutpunkter og værktøjer, dækker denne artikel dem ikke. Du kan finde oplysninger om generel onboarding ved hjælp af andre understøttede installationsværktøjer og metoder under [Oversigt over onboarding](onboarding.md).

Dette emne hjælper brugerne i:

- Trin 1: Onboarding Windows enheder til tjenesten
- Trin 2: Konfiguration af Defender til slutpunkt-funktioner

Denne onboardingvejledning vejleder dig gennem de følgende grundlæggende trin, du skal tage, når du bruger Microsoft Endpoint Configuration Manager:

- **Oprettelse af en samling i Microsoft Endpoint Configuration Manager**
- **Konfiguration af Microsoft Defender til slutpunktsfunktioner ved hjælp af Microsoft Endpoint Configuration Manager**

> [!NOTE]
> Kun Windows enheder er dækket i denne eksempelinstallation.

## <a name="step-1-onboard-windows-devices-using-microsoft-endpoint-configuration-manager"></a>Trin 1: Onboard Windows enheder ved hjælp af Microsoft Endpoint Configuration Manager

### <a name="collection-creation"></a>Oprettelse af samlinger

For at Windows enheder med Microsoft Endpoint Configuration Manager kan installationen målrette mod en eksisterende samling, eller der kan oprettes en ny samling til test.

Onboarding ved hjælp af værktøjer som f.eks Gruppepolitik eller manuel metode installerer ikke nogen agent på systemet.

I Microsoft Endpoint Configuration Manager konfigureres onboardingprocessen som en del af indstillingerne for overholdelse i konsollen.

Ethvert system, der modtager denne påkrævede konfiguration, bevarer konfigurationen, så længe Konfigurationsstyring-klienten fortsat modtager denne politik fra administrationspunktet.

Følg trinnene nedenfor for at onboarde slutpunkter ved hjælp Microsoft Endpoint Configuration Manager.

1. I Microsoft Endpoint Configuration Manager skal du gå til Oversigt **over aktiver og overholdelse \> af enhedssamlinger\>**.

    ![Billede af Microsoft Endpoint Configuration Manager guide1.](images/configmgr-device-collections.png)

2. Højreklik på **Samling af enheder,** og vælg **Opret samling af enheder**.

    ![Billede af Microsoft Endpoint Configuration Manager guide2.](images/configmgr-create-device-collection.png)

3. Angiv et **navn og** **bebegrænsning af samling**, og vælg **derefter Næste**.

    ![Billede af Microsoft Endpoint Configuration Manager guide3.](images/configmgr-limiting-collection.png)

4. Vælg **Tilføj regel,** og vælg **Forespørgselsregel**.

    ![Billede af Microsoft Endpoint Configuration Manager guide4.](images/configmgr-query-rule.png)

5. Klik **på Næste** i guiden **Direkte medlemskab, og** klik på **Rediger forespørgselssætningen**.

     ![Billede af Microsoft Endpoint Configuration Manager guide5.](images/configmgr-direct-membership.png)

6. Vælg **Kriterier** , og vælg derefter stjerneikonet.

     ![Billede af Microsoft Endpoint Configuration Manager guide6.](images/configmgr-criteria.png)

7. Bevar kriterietype som **simpel** værdi, vælg hvor som Operativsystem **– buildnummer, operator** som  er større end eller lig med og værdi **14393**, og klik på **OK**.

    ![Billede af Microsoft Endpoint Configuration Manager guide7.](images/configmgr-simple-value.png)

8. Vælg **Næste** og **Luk**.

    ![Billede af Microsoft Endpoint Configuration Manager guide8.](images/configmgr-membership-rules.png)

9. Vælg **Næste**.

    ![Billede af Microsoft Endpoint Configuration Manager guide9.](images/configmgr-confirm.png)

Når du har fuldført denne opgave, har du nu en samling af enheder Windows alle slutpunkter i miljøet.

## <a name="step-2-configure-microsoft-defender-for-endpoint-capabilities"></a>Trin 2: Konfigurer Microsoft Defender til slutpunktsfunktioner

Dette afsnit vejleder dig i konfigurationen af følgende funktioner ved hjælp af Microsoft Endpoint Configuration Manager på Windows enheder:

- [**Registrering af slutpunkt og svar**](#endpoint-detection-and-response)
- [**Næste generations beskyttelse**](#next-generation-protection)
- [**Reduktion af angrebsoverfladen**](#attack-surface-reduction)

### <a name="endpoint-detection-and-response"></a>Registrering af slutpunkt og svar

#### <a name="windows-10-and-windows-11"></a>Windows 10 og Windows 11

`.onboarding` Fra Microsoft 365 Defender-portalen er det muligt at hente den politik, der kan bruges til at oprette politikken i System Center Configuration Manager og installere denne politik på Windows 10 og Windows 11 enheder.

1. Fra en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> skal du [vælge Indstillinger og derefter Onboarding](https://security.microsoft.com/preferences2/onboarding).

2. Vælg den understøttede version af Microsoft Endpoint Configuration Manager **under Installationsmetode**.

    ![Billede af guiden Microsoft Defender til onboarding af slutpunkt10.](images/mdatp-onboarding-wizard.png)

3. Vælg **Download pakke**.

    ![Billede af guiden Microsoft Defender til onboarding af slutpunkt11.](images/mdatp-download-package.png)

4. Gem pakken på en handicapvenlig placering.
5. I Microsoft Endpoint Configuration Manager skal du gå til: **Aktiver og overholdelse > Oversigt > Endpoint Protection > Microsoft Defender ATP-politikker**.

6. Højreklik på **Microsoft Defender ATP-politikker,** og vælg **Opret Microsoft Defender ATP-politik**.

    ![Billede af Microsoft Endpoint Configuration Manager guide12.](images/configmgr-create-policy.png)

7. Angiv navn og beskrivelse, kontrollér, **at Onboarding** er markeret, og vælg derefter **Næste**.

    ![Billede af Microsoft Endpoint Configuration Manager guide13.](images/configmgr-policy-name.png)

8. Klik **på Gennemse**.

9. Gå til den downloadede fils placering fra trin 4 ovenfor.

10. Klik på **Næste**.
11. Konfigurer Agenten med de relevante eksempler (**Ingen** **eller Alle filtyper**).

    ![Billede af konfigurationsindstillinger1.](images/configmgr-config-settings.png)

12. Vælg den relevante telemetri (**Normal** eller **Fremskyndet), og** klik derefter på **Næste**.

    ![Billede af konfigurationsindstillinger2.](images/configmgr-telemetry.png)

13. Bekræft konfigurationen, og klik derefter på **Næste**.

     ![Billede af konfigurationsindstillinger3.](images/configmgr-verify-configuration.png)

14. Klik **på** Luk, når guiden er fuldført.

15. I konsollen Microsoft Endpoint Configuration Manager skal du højreklikke på den Defender for Endpoint-politik, du lige har oprettet, og vælge **Deploy**.

     ![Billede af konfigurationsindstillinger4.](images/configmgr-deploy.png)

16. Vælg den tidligere oprettede samling i højre panel, og klik på **OK**.

    ![Billede af konfigurationsindstillinger5.](images/configmgr-select-collection.png)

#### <a name="previous-versions-of-windows-client-windows-7-and-windows-81"></a>Tidligere versioner af Windows klient (Windows 7 og Windows 8.1)

Følg trinnene nedenfor for at identificere Defender for Endpoint Workspace-id'et og Workspace-nøglen, som skal bruges til onboarding af tidligere versioner Windows.

1. Fra en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> skal du **vælge Indstillinger** \> **Slutpunkter** \> **Onboarding** (under **Enhedshåndtering**).

2. Under operativsystem skal du **Windows 7 SP1 og 8.1**.

3. Kopiér **arbejdsområde-id'et** **og arbejdsområdenøglen,** og gem dem. De vil blive brugt senere i processen.

    ![Billede af onboarding.](images/91b738e4b97c4272fd6d438d8c2d5269.png)

4. Installér Microsoft Monitoring Agent (AGENT).

   ÆLDRE understøttes i øjeblikket (pr. januar 2019 på følgende Windows operativsystemer:

   - ServerSKU'er: Windows Server 2008 SP1 eller nyere
   - Klient-SKU'er: Windows 7 SP1 og nyere

   ÆLDRE-agenten skal installeres på Windows enheder. For at installere agenten skal nogle systemer downloade Opdatering til kundeoplevelse og diagnostisk [telemetri for](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry) at indsamle data med DIOG. Disse systemversioner omfatter, men er muligvis ikke begrænset til:

   - Windows 8.1
   - Windows 7
   - Windows Server 2016
   - Windows Server 2012 R2
   - Windows Server 2008 R2

   Især til Windows 7 SP1 skal følgende rettelser installeres:

   - [Installér KB4074598](https://support.microsoft.com/help/4074598/windows-7-update-kb4074598)
   - Installér [.NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653) (eller nyere) **eller** [KB3154518](https://support.microsoft.com/help/3154518/support-for-tls-system-default-versions-included-in-the-net-framework). Installér ikke begge dele på det samme system.

5. Hvis du bruger en proxy til at oprette forbindelse til internettet, skal du se afsnittet Konfigurer proxyindstillinger.

Når du er færdig, bør du kunne se onboardede slutpunkter i portalen inden for en time.

### <a name="next-generation-protection"></a>Næste generations beskyttelse

Microsoft Defender Antivirus er en indbygget antimalwareløsning, der giver næste generations beskyttelse til computere, bærbare computere og servere.

1. I konsollen Microsoft Endpoint Configuration Manager skal **\> \> du gå til Oversigt over aktiver og overholdelse Endpoint Protection \> Antimalware-politikker** og **vælge Opret antimalwarepolitik**.

    ![Billede af antimalwarepolitik.](images/9736e0358e86bc778ce1bd4c516adb8b.png)

2. Vælg **Planlagte scanninger, Scanningsindstillinger****,** Standardhandlinger, Beskyttelse i **realtid,** Udeladelsesindstillinger **,** Avanceret, Trusselssidesættelser, **Cloud Protection Service** og **Sikkerhedsintelligens-opdateringer**, og vælg **OK**. 

    ![Billede af næste generations beskyttelsesrude1.](images/1566ad81bae3d714cc9e0d47575a8cbd.png)

    I visse brancher eller nogle udvalgte virksomhedskunder kan have specifikke behov for, hvordan antivirus er konfigureret.

    [Hurtig scanning kontra fuld scanning og brugerdefineret scanning](/windows/security/threat-protection/microsoft-defender-antivirus/scheduled-catch-up-scans-microsoft-defender-antivirus#quick-scan-versus-full-scan-and-custom-scan)

    Du kan finde flere oplysninger [Windows Sikkerhed konfigurationsstruktur](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-configuration-framework).
  
    ![Billede af næste generations beskyttelsesrude2.](images/cd7daeb392ad5a36f2d3a15d650f1e96.png)

    ![Billede af næste generations beskyttelsesrude3.](images/36c7c2ed737f2f4b54918a4f20791d4b.png)

    ![Billede af næste generations beskyttelsesrude4.](images/a28afc02c1940d5220b233640364970c.png)

    ![Billede af næste generations beskyttelsesrude5.](images/5420a8790c550f39f189830775a6d4c9.png)

    ![Billede af næste generations beskyttelsesrude6.](images/33f08a38f2f4dd12a364f8eac95e8c6b.png)

    ![Billede af næste generations beskyttelsesrude7.](images/41b9a023bc96364062c2041a8f5c344e.png)

    ![Billede af næste generations beskyttelsesrude8.](images/945c9c5d66797037c3caeaa5c19f135c.png)

    ![Billede af næste generations beskyttelsesrude9.](images/3876ca687391bfc0ce215d221c683970.png)

3. Højreklik på den nyligt oprettede antimalwarepolitik, og vælg **Installér**.

    ![Billede af næste generations beskyttelsesrude10.](images/f5508317cd8c7870627cb4726acd5f3d.png)

4. Målret den nye antimalwarepolitik mod din Windows, og klik på **OK**.

     ![Billede af næste generations beskyttelsesrude11.](images/configmgr-select-collection.png)

Når du har fuldført denne opgave, har du nu konfigureret Windows Defender Antivirus.

### <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

Angrebsoverfladens reduktionssøjle i Defender til slutpunkt indeholder det funktionssæt, der er tilgængeligt under Exploit Guard. Reduktion af angrebsoverfladen (ASR)-regler, Styret mappeadgang, Netværksbeskyttelse og Exploit Protection.

Alle disse funktioner giver en overvågningstilstand og en bloktilstand. I overvågningstilstand har det ingen indvirkning på slutbrugeren. Det eneste, programmet gør, er at indsamle yderligere telemetri og gøre det tilgængeligt Microsoft 365 Defender portalen. Målet med en installation er at flytte sikkerhedskontrolelementerne trinvist til bloktilstand.

Sådan angives ASR-regler i overvågningstilstand:

1. I konsollen Microsoft Endpoint Configuration Manager skal du gå til **Oversigt \> \> over aktiver og overholdelse Endpoint Protection \> Windows Defender Exploit Guard** og vælge **Create Exploit Guard-politik**.

   ![Billede af Microsoft Endpoint Configuration Manager konsol0.](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Vælg **Reduktion af angrebsoverfladen**.

3. Angiv regler til Overvågning **,** og klik på **Næste**.

    ![Billede af Microsoft Endpoint Configuration Manager konsol1.](images/d18e40c9e60aecf1f9a93065cb7567bd.png)

4. Bekræft den nye Exploit Guard-politik ved at klikke på **Næste**.

    ![Billede af Microsoft Endpoint Configuration Manager konsol2.](images/0a6536f2c4024c08709cac8fcf800060.png)

5. Klik på Luk, når politikken er **oprettet**.

    ![Billede af Microsoft Endpoint Configuration Manager konsol3.](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Højreklik på den nyoprettede politik, og vælg **Installér**.

    ![Billede af Microsoft Endpoint Configuration Manager konsol4.](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7. Målret politikken til den nyoprettede samling Windows, og klik på **OK**.

    ![Billede af Microsoft Endpoint Configuration Manager konsol5.](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Når du har fuldført denne opgave, har du nu konfigureret ASR-regler i overvågningstilstand.

Nedenfor finder du yderligere trin til at kontrollere, om ASR-regler anvendes korrekt på slutpunkter. (Dette kan tage nogle minutter)

1. Gå til Microsoft 365 Defender fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">en webbrowser</a>.

2. Vælg **Konfigurationsstyring** fra menuen til venstre.

3. Klik **på Gå til administration af angrebsoverfladen** i panelet til administration af angrebsoverfladen.

    ![Billede af administration af angrebsoverfladen.](images/security-center-attack-surface-mgnt-tile.png)

4. Klik **på fanen** Konfiguration i rapporter om reduktionsregler for angrebsoverfladen. Den viser oversigt over konfiguration af ASR-regler og ASR-regelstatus på hver enhed.

    ![Et skærmbillede af rapporter om reduktion af angrebsoverfladen1.](images/f91f406e6e0aae197a947d3b0e8b2d0d.png)

5. Klik på hver enhed, der viser konfigurationsoplysninger for ASR-regler.

    ![Et skærmbillede af rapporter om reduktion af angrebsoverfladen2.](images/24bfb16ed561cbb468bd8ce51130ca9d.png)

Se [Optimer installation og registrering af ASR-regler](/microsoft-365/security/defender-endpoint/configure-machines-asr) for at få mere at vide.

#### <a name="set-network-protection-rules-in-audit-mode"></a>Angiv regler for netværksbeskyttelse i overvågningstilstand

1. I konsollen Microsoft Endpoint Configuration Manager skal du gå til **Oversigt \> \> over aktiver og overholdelse Endpoint Protection \> Windows Defender Exploit Guard** og vælge **Create Exploit Guard-politik**.

    ![Et skærmbillede af System Center Configuration Manager1.](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Vælg **Netværksbeskyttelse**.

3. Angiv indstillingen til Overvågning **, og** klik på **Næste**.

    ![Et skærmbillede af System Center Configuration Manager2.](images/c039b2e05dba1ade6fb4512456380c9f.png)

4. Bekræft den nye Exploit Guard-politik ved at klikke på **Næste**.

    ![Et skærmbillede af Exploit Guard-politik1.](images/0a6536f2c4024c08709cac8fcf800060.png)

5. Når politikken er oprettet, skal du klikke på **Luk**.

    ![Et skærmbillede af Exploit Guard-politik2.](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Højreklik på den nyoprettede politik, og vælg **Installér**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager1.](images/8999dd697e3b495c04eb911f8b68a1ef.png)

7. Vælg politikken til den nyoprettede samling Windows, og vælg **OK**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager2.](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Når du har fuldført denne opgave, har du nu konfigureret Netværksbeskyttelse i overvågningstilstand.

#### <a name="to-set-controlled-folder-access-rules-in-audit-mode"></a>Sådan angives regler for styret mappeadgang i overvågningstilstand

1. I konsollen Microsoft Endpoint Configuration Manager skal du gå til **Assets and** **ComplianceOverview** >  >  **Endpoint Protection** >  **Windows Defender Exploit Guard** og derefter **vælge Create Exploit Guard-politik**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager3.](images/728c10ef26042bbdbcd270b6343f1a8a.png)

2. Vælg **Styret mappeadgang**.

3. Angiv konfigurationen til Overvågning **, og** klik på **Næste**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager4.](images/a8b934dab2dbba289cf64fe30e0e8aa4.png)

4. Bekræft den nye Exploit Guard-politik ved at klikke på **Næste**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager5.](images/0a6536f2c4024c08709cac8fcf800060.png)

5. Når politikken er oprettet, skal du klikke på **Luk**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager6.](images/95d23a07c2c8bc79176788f28cef7557.png)

6. Højreklik på den nyoprettede politik, og vælg **Installér**.

    ![Et skærmbillede af Microsoft Endpoint Configuration Manager7.](images/8999dd697e3b495c04eb911f8b68a1ef.png)


7. Målret politikken til den nyoprettede samling Windows, og klik på **OK**.


    ![Et skærmbillede af Microsoft Endpoint Configuration Manager8.](images/0ccfe3e803be4b56c668b220b51da7f7.png)

Du har nu konfigureret Styret mappeadgang i overvågningstilstand.

## <a name="related-topic"></a>Relateret emne

- [Onboarding ved hjælp Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
