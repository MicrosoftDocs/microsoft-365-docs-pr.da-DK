---
title: Onboarding ved hjælp Microsoft Endpoint Configuration Manager
description: Få mere at vide om, hvordan du kommer i gang Microsoft Defender for Endpoint at bruge Microsoft Endpoint Configuration Manager
keywords: onboarding, konfiguration, installation, installation, slutpunktskonfigurationsstyring, Microsoft Defender for Endpoint, oprettelse af samling, svar på registrering af slutpunkter, næste generations beskyttelse, reduktion af angrebsoverfladen, konfigurationsstyring til Microsoft-slutpunkt
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
ms.openlocfilehash: b8847fb9132ee037a3103bf86aabd14d21fb482f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469421"
---
# <a name="onboarding-using-microsoft-endpoint-configuration-manager"></a>Onboarding ved hjælp Microsoft Endpoint Configuration Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Denne artikel er en del af Installationsvejledningen og fungerer som et eksempel på onboardingmetoden.

I emnet [Planlægning](deployment-strategy.md) var der flere forskellige metoder for onboardingenheder til tjenesten. Dette emne omhandler arkitekturen for samtidig administration.

:::image type="content" source="images/co-management-architecture.png" alt-text="Den skybaserede arkitektur" lightbox="images/co-management-architecture.png":::
*Diagram over miljøarkitekturer*

Mens Defender til Slutpunkt understøtter onboarding af forskellige slutpunkter og værktøjer, dækker denne artikel dem ikke. Du kan finde oplysninger om generel onboarding ved hjælp af andre understøttede installationsværktøjer og metoder under [Oversigt over onboarding](onboarding.md).

Dette emne hjælper brugerne i:

- Trin 1: Onboarding Windows enheder til tjenesten
- Trin 2: Konfiguration af Defender til slutpunkt-funktioner

Denne onboardingvejledning vejleder dig gennem de følgende grundlæggende trin, du skal tage, når du bruger Microsoft Endpoint Configuration Manager:

- **Oprettelse af en samling i Microsoft Endpoint Configuration Manager**
- **Konfiguration Microsoft Defender for Endpoint funktioner ved hjælp af Microsoft Endpoint Configuration Manager**

> [!NOTE]
> Kun Windows enheder er dækket i denne eksempelinstallation.

## <a name="step-1-onboard-windows-devices-using-microsoft-endpoint-configuration-manager"></a>Trin 1: Onboard Windows enheder ved hjælp af Microsoft Endpoint Configuration Manager

### <a name="collection-creation"></a>Oprettelse af samlinger

For at Windows enheder med Microsoft Endpoint Configuration Manager kan installationen målrette mod en eksisterende samling, eller der kan oprettes en ny samling til test.

Onboarding ved hjælp af værktøjer som f.eks Gruppepolitik eller manuel metode installerer ikke nogen agent på systemet.

I Microsoft Endpoint Configuration Manager konfigureres onboardingprocessen som en del af indstillingerne for overholdelse i konsollen.

Ethvert system, der modtager denne påkrævede konfiguration, bevarer konfigurationen, så længe Configuration Manager-klienten fortsat modtager denne politik fra administrationspunktet.

Følg trinnene nedenfor for at onboarde slutpunkter ved hjælp Microsoft Endpoint Configuration Manager.

1. I Microsoft Endpoint Configuration Manager skal du gå til Oversigt **over aktiver og overholdelse \> af enhedssamlinger\>**.

    :::image type="content" source="images/configmgr-device-collections.png" alt-text="Den Microsoft Endpoint Configuration Manager guide1" lightbox="images/configmgr-device-collections.png":::

2. Højreklik på **Samling af enheder,** og vælg **Opret samling af enheder**.

    :::image type="content" source="images/configmgr-create-device-collection.png" alt-text="Den Microsoft Endpoint Configuration Manager guide2" lightbox="images/configmgr-create-device-collection.png":::

3. Angiv et **navn og** **bebegrænsning af samling**, og vælg **derefter Næste**.

    :::image type="content" source="images/configmgr-limiting-collection.png" alt-text="Den Microsoft Endpoint Configuration Manager guide3" lightbox="images/configmgr-limiting-collection.png":::

4. Vælg **Tilføj regel,** og vælg **Forespørgselsregel**.

    :::image type="content" source="images/configmgr-query-rule.png" alt-text="Den Microsoft Endpoint Configuration Manager guide4" lightbox="images/configmgr-query-rule.png":::

5. Klik **på Næste** i guiden **Direkte medlemskab, og** klik på **Rediger forespørgselssætningen**.

    :::image type="content" source="images/configmgr-direct-membership.png" alt-text="Den Microsoft Endpoint Configuration Manager guide5" lightbox="images/configmgr-direct-membership.png":::

6. Vælg **Kriterier** , og vælg derefter stjerneikonet.

    :::image type="content" source="images/configmgr-criteria.png" alt-text="Den Microsoft Endpoint Configuration Manager guide6" lightbox="images/configmgr-criteria.png":::

7. Bevar kriterietype som **simpel** værdi, vælg hvor som Operativsystem **– buildnummer, operator** som  er større end eller lig med og værdi **14393**, og klik på **OK**.

    :::image type="content" source="images/configmgr-simple-value.png" alt-text="Den Microsoft Endpoint Configuration Manager guide7" lightbox="images/configmgr-simple-value.png":::

8. Vælg **Næste** og **Luk**.

    :::image type="content" source="images/configmgr-membership-rules.png" alt-text="Den Microsoft Endpoint Configuration Manager guide8" lightbox="images/configmgr-membership-rules.png":::

9. Vælg **Næste**.

    :::image type="content" source="images/configmgr-confirm.png" alt-text="Den Microsoft Endpoint Configuration Manager guide9" lightbox="images/configmgr-confirm.png":::

Når du har fuldført denne opgave, har du nu en samling af enheder Windows alle slutpunkter i miljøet.

## <a name="step-2-configure-microsoft-defender-for-endpoint-capabilities"></a>Trin 2: Microsoft Defender for Endpoint egenskaber

Dette afsnit vejleder dig i konfigurationen af følgende funktioner ved hjælp af Microsoft Endpoint Configuration Manager på Windows enheder:

- [**Registrering af slutpunkt og svar**](#endpoint-detection-and-response)
- [**Næste generations beskyttelse**](#next-generation-protection)
- [**Reduktion af angrebsoverfladen**](#attack-surface-reduction)

### <a name="endpoint-detection-and-response"></a>Registrering af slutpunkt og svar

#### <a name="windows-10-and-windows-11"></a>Windows 10 og Windows 11

Fra Microsoft 365 Defender-portalen `.onboarding` er det muligt at hente den politik, der kan bruges til at oprette politikken i System Center Configuration Manager og installere denne politik på Windows 10 og Windows 11 enheder.

1. Fra en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> skal du [vælge Indstillinger og derefter Onboarding](https://security.microsoft.com/preferences2/onboarding).

2. Vælg den understøttede version af Microsoft Endpoint Configuration Manager **under Installationsmetode**.

    :::image type="content" source="images/mdatp-onboarding-wizard.png" alt-text="Guiden Microsoft Endpoint Configuration Manager 10" lightbox="images/mdatp-onboarding-wizard.png":::

3. Vælg **Download pakke**.

   :::image type="content" source="images/mdatp-download-package.png" alt-text="Guiden Microsoft Endpoint Configuration Manager 11" lightbox="images/mdatp-download-package.png":::

4. Gem pakken på en handicapvenlig placering.
5. I Microsoft Endpoint Configuration Manager skal du gå til: **Aktiver og overholdelse > Oversigt > Endpoint Protection > Microsoft Defender ATP-politikker**.

6. Højreklik på **Microsoft Defender ATP-politikker,** og vælg **Opret Microsoft Defender ATP-politik**.

    :::image type="content" source="images/configmgr-create-policy.png" alt-text="Guiden Microsoft Endpoint Configuration Manager 12" lightbox="images/configmgr-create-policy.png":::

7. Angiv navn og beskrivelse, kontrollér, **at Onboarding** er markeret, og vælg derefter **Næste**.

    :::image type="content" source="images/configmgr-policy-name.png" alt-text="Guiden Microsoft Endpoint Configuration Manager 13" lightbox="images/configmgr-policy-name.png":::

8. Klik **på Gennemse**.

9. Gå til den downloadede fils placering fra trin 4 ovenfor.

10. Klik på **Næste**.
11. Konfigurer Agenten med de relevante eksempler (**Ingen** **eller Alle filtyper**).

    :::image type="content" source="images/configmgr-config-settings.png" alt-text="Konfigurationsindstillinger1" lightbox="images/configmgr-config-settings.png":::

12. Vælg den relevante telemetri (**Normal** eller **Fremskyndet), og** klik derefter på **Næste**.

    :::image type="content" source="images/configmgr-telemetry.png" alt-text="Konfigurationsindstillingerne2" lightbox="images/configmgr-telemetry.png":::

13. Bekræft konfigurationen, og klik derefter på **Næste**.

    :::image type="content" source="images/configmgr-verify-configuration.png" alt-text="Konfigurationsindstillingerne3" lightbox="images/configmgr-verify-configuration.png":::

14. Klik **på** Luk, når guiden er fuldført.

15. I konsollen Microsoft Endpoint Configuration Manager skal du højreklikke på den Defender for Endpoint-politik, du lige har oprettet, og vælge **Deploy**.

    :::image type="content" source="images/configmgr-deploy.png" alt-text="Konfigurationsindstillingerne4" lightbox="images/configmgr-deploy.png":::

16. Vælg den tidligere oprettede samling i højre panel, og klik på **OK**.

    :::image type="content" source="images/configmgr-select-collection.png" alt-text="Konfigurationsindstillingerne5" lightbox="images/configmgr-select-collection.png":::

#### <a name="previous-versions-of-windows-client-windows-7-and-windows-81"></a>Tidligere versioner af Windows klient (Windows 7 og Windows 8.1)

Følg trinnene nedenfor for at identificere Defender for Endpoint Workspace-id'et og Workspace-nøglen, som skal bruges til onboarding af tidligere versioner Windows.

1. Fra en <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> skal du **vælge Indstillinger** \> **Slutpunkter** \> **Onboarding** (under **Enhedshåndtering**).

2. Under operativsystem skal du **Windows 7 SP1 og 8.1**.

3. Kopiér **arbejdsområde-id'et** **og arbejdsområdenøglen,** og gem dem. De vil blive brugt senere i processen.

   :::image type="content" source="images/91b738e4b97c4272fd6d438d8c2d5269.png" alt-text="Onboardingprocessen" lightbox="images/91b738e4b97c4272fd6d438d8c2d5269.png":::

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

   :::image type="content" source="images/9736e0358e86bc778ce1bd4c516adb8b.png" alt-text="Antimalwarepolitikken" lightbox="images/9736e0358e86bc778ce1bd4c516adb8b.png":::

2. Vælg **Planlagte scanninger, Scanningsindstillinger****,** Standardhandlinger, Beskyttelse i **realtid,** Udeladelsesindstillinger **,** Avanceret, Trusselssidesættelser, **Cloud Protection Service** og **Sikkerhedsintelligens-opdateringer**, og vælg **OK**. 

   :::image type="content" source="images/1566ad81bae3d714cc9e0d47575a8cbd.png" alt-text="Næste generations beskyttelsesrude1" lightbox="images/1566ad81bae3d714cc9e0d47575a8cbd.png":::

    I visse brancher eller nogle udvalgte virksomhedskunder kan have specifikke behov for, hvordan antivirus er konfigureret.

    [Hurtig scanning kontra fuld scanning og brugerdefineret scanning](/windows/security/threat-protection/microsoft-defender-antivirus/scheduled-catch-up-scans-microsoft-defender-antivirus#quick-scan-versus-full-scan-and-custom-scan)

    Du kan finde flere oplysninger [Windows Sikkerhed konfigurationsstruktur](/windows/security/threat-protection/windows-security-configuration-framework/windows-security-configuration-framework).
  
    :::image type="content" source="images/cd7daeb392ad5a36f2d3a15d650f1e96.png" alt-text="Næste generations beskyttelsesrude2" lightbox="images/cd7daeb392ad5a36f2d3a15d650f1e96.png":::

    :::image type="content" source="images/36c7c2ed737f2f4b54918a4f20791d4b.png" alt-text="Næste generations beskyttelsesrude3" lightbox="images/36c7c2ed737f2f4b54918a4f20791d4b.png":::

    :::image type="content" source="images/a28afc02c1940d5220b233640364970c.png" alt-text="Næste generations beskyttelsesrude4" lightbox="images/a28afc02c1940d5220b233640364970c.png":::

    :::image type="content" source="images/5420a8790c550f39f189830775a6d4c9.png" alt-text="Næste generations beskyttelsesrude5" lightbox="images/5420a8790c550f39f189830775a6d4c9.png":::

    :::image type="content" source="images/33f08a38f2f4dd12a364f8eac95e8c6b.png" alt-text="Næste generations beskyttelsesrude6" lightbox="images/33f08a38f2f4dd12a364f8eac95e8c6b.png":::

    :::image type="content" source="images/41b9a023bc96364062c2041a8f5c344e.png" alt-text="Næste generations beskyttelsesrude7" lightbox="images/41b9a023bc96364062c2041a8f5c344e.png":::

    :::image type="content" source="images/945c9c5d66797037c3caeaa5c19f135c.png" alt-text="Næste generations beskyttelsesrude8" lightbox="images/945c9c5d66797037c3caeaa5c19f135c.png":::

    :::image type="content" source="images/3876ca687391bfc0ce215d221c683970.png" alt-text="Næste generations beskyttelsesrude9" lightbox="images/3876ca687391bfc0ce215d221c683970.png":::

3. Højreklik på den nyligt oprettede antimalwarepolitik, og vælg **Installér**.

    :::image type="content" source="images/f5508317cd8c7870627cb4726acd5f3d.png" alt-text="Næste generations beskyttelsesrude10" lightbox="images/f5508317cd8c7870627cb4726acd5f3d.png":::

4. Målret den nye antimalwarepolitik mod din Windows, og klik på **OK**.

    :::image type="content" source="images/configmgr-select-collection.png" alt-text="Næste generations beskyttelsesrude11" lightbox="images/configmgr-select-collection.png":::

Når du har fuldført denne opgave, har du nu konfigureret Windows Defender Antivirus.

### <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

Angrebsoverfladens reduktionssøjle i Defender til slutpunkt indeholder det funktionssæt, der er tilgængeligt under Exploit Guard. Reduktion af angrebsoverfladen (ASR)-regler, Styret mappeadgang, Netværksbeskyttelse og Exploit Protection.

Alle disse funktioner giver en overvågningstilstand og en bloktilstand. I overvågningstilstand har det ingen indvirkning på slutbrugeren. Det eneste, programmet gør, er at indsamle yderligere telemetri og gøre det tilgængeligt Microsoft 365 Defender portalen. Målet med en installation er at flytte sikkerhedskontrolelementerne trinvist til bloktilstand.

Sådan angives ASR-regler i overvågningstilstand:

1. I konsollen Microsoft Endpoint Configuration Manager skal du gå til **Oversigt \> \> over aktiver og overholdelse Endpoint Protection \> Windows Defender Exploit Guard** og vælge **Create Exploit Guard-politik**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="Den Microsoft Endpoint Configuration Manager konsol0" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. Vælg **Reduktion af angrebsoverfladen**.

3. Angiv regler til Overvågning **,** og klik på **Næste**.

   :::image type="content" source="images/d18e40c9e60aecf1f9a93065cb7567bd.png" alt-text="Den Microsoft Endpoint Configuration Manager konsol1" lightbox="images/d18e40c9e60aecf1f9a93065cb7567bd.png":::

4. Bekræft den nye Exploit Guard-politik ved at klikke på **Næste**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="Den Microsoft Endpoint Configuration Manager konsol2" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. Klik på Luk, når politikken er **oprettet**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="Den Microsoft Endpoint Configuration Manager konsol3" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. Højreklik på den nyoprettede politik, og vælg **Installér**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Den Microsoft Endpoint Configuration Manager konsol4" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. Målret politikken til den nyoprettede samling Windows, og klik på **OK**.

   :::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Den Microsoft Endpoint Configuration Manager konsol5" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

Når du har fuldført denne opgave, har du nu konfigureret ASR-regler i overvågningstilstand.

Nedenfor finder du yderligere trin til at kontrollere, om ASR-regler anvendes korrekt på slutpunkter. (Dette kan tage nogle minutter)

1. Gå til Microsoft 365 Defender fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">en webbrowser</a>.

2. Vælg **Konfigurationsstyring** fra menuen til venstre.

3. Klik **på Gå til administration af angrebsoverfladen** i panelet til administration af angrebsoverfladen.

   :::image type="content" source="images/security-center-attack-surface-mgnt-tile.png" alt-text="Administration af angrebsoverfladen" lightbox="images/security-center-attack-surface-mgnt-tile.png":::

4. Klik **på fanen** Konfiguration i rapporter om reduktionsregler for angrebsoverfladen. Den viser oversigt over konfiguration af ASR-regler og ASR-regelstatus på hver enhed.

   :::image type="content" source="images/f91f406e6e0aae197a947d3b0e8b2d0d.png" alt-text="Rapporter om reduktion af angrebsoverfladen1" lightbox="images/f91f406e6e0aae197a947d3b0e8b2d0d.png":::

5. Klik på hver enhed, der viser konfigurationsoplysninger for ASR-regler.

   :::image type="content" source="images/24bfb16ed561cbb468bd8ce51130ca9d.png" alt-text="Rapporter om reduktion af angrebsoverfladen2" lightbox="images/24bfb16ed561cbb468bd8ce51130ca9d.png":::

Se [Optimer installation og registrering af ASR-regler](/microsoft-365/security/defender-endpoint/configure-machines-asr) for at få mere at vide.

#### <a name="set-network-protection-rules-in-audit-mode"></a>Angiv regler for netværksbeskyttelse i overvågningstilstand

1. I konsollen Microsoft Endpoint Configuration Manager skal du gå til **Oversigt \> \> over aktiver og overholdelse Endpoint Protection \> Windows Defender Exploit Guard** og vælge **Create Exploit Guard-politik**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="The System Center Configuration Manager1" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. Vælg **Netværksbeskyttelse**.

3. Angiv indstillingen til Overvågning **, og** klik på **Næste**.

   :::image type="content" source="images/c039b2e05dba1ade6fb4512456380c9f.png" alt-text="The System Center Configuration Manager2" lightbox="images/c039b2e05dba1ade6fb4512456380c9f.png":::

4. Bekræft den nye Exploit Guard-politik ved at klikke på **Næste**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="Exploit Guard-politikken1" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. Når politikken er oprettet, skal du klikke på **Luk**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="Exploit Guard-politikken2" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. Højreklik på den nyoprettede politik, og vælg **Installér**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Den Microsoft Endpoint Configuration Manager-1" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::

7. Vælg politikken til den nyoprettede samling Windows, og vælg **OK**.

   :::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Den Microsoft Endpoint Configuration Manager-2" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

Når du har fuldført denne opgave, har du nu konfigureret Netværksbeskyttelse i overvågningstilstand.

#### <a name="to-set-controlled-folder-access-rules-in-audit-mode"></a>Sådan angives regler for styret mappeadgang i overvågningstilstand

1. I konsollen Microsoft Endpoint Configuration Manager skal du gå til **Assets and** **ComplianceOverview** >  >  **Endpoint Protection** >  **Windows Defender Exploit Guard** og derefter **vælge Create Exploit Guard-politik**.

   :::image type="content" source="images/728c10ef26042bbdbcd270b6343f1a8a.png" alt-text="Den Microsoft Endpoint Configuration Manager-3" lightbox="images/728c10ef26042bbdbcd270b6343f1a8a.png":::

2. Vælg **Styret mappeadgang**.

3. Angiv konfigurationen til Overvågning **, og** klik på **Næste**.

   :::image type="content" source="images/a8b934dab2dbba289cf64fe30e0e8aa4.png" alt-text="The Microsoft Endpoint Configuration Manager-4" lightbox="images/a8b934dab2dbba289cf64fe30e0e8aa4.png":::

4. Bekræft den nye Exploit Guard-politik ved at klikke på **Næste**.

   :::image type="content" source="images/0a6536f2c4024c08709cac8fcf800060.png" alt-text="Den Microsoft Endpoint Configuration Manager-5" lightbox="images/0a6536f2c4024c08709cac8fcf800060.png":::

5. Når politikken er oprettet, skal du klikke på **Luk**.

   :::image type="content" source="images/95d23a07c2c8bc79176788f28cef7557.png" alt-text="Den Microsoft Endpoint Configuration Manager-6" lightbox="images/95d23a07c2c8bc79176788f28cef7557.png":::

6. Højreklik på den nyoprettede politik, og vælg **Installér**.

   :::image type="content" source="images/8999dd697e3b495c04eb911f8b68a1ef.png" alt-text="Den Microsoft Endpoint Configuration Manager-7" lightbox="images/8999dd697e3b495c04eb911f8b68a1ef.png":::


7. Målret politikken til den nyoprettede samling Windows, og klik på **OK**.


:::image type="content" source="images/0ccfe3e803be4b56c668b220b51da7f7.png" alt-text="Den Microsoft Endpoint Configuration Manager-8" lightbox="images/0ccfe3e803be4b56c668b220b51da7f7.png":::

Du har nu konfigureret Styret mappeadgang i overvågningstilstand.

## <a name="related-topic"></a>Relateret emne

- [Onboarding ved hjælp Microsoft Endpoint Manager](onboarding-endpoint-manager.md)
