---
title: Konfigurer Microsoft Defender for Endpoint installation
description: Få mere at vide om, hvordan du konfigurerer installationen for Microsoft Defender for Endpoint
keywords: installation, konfiguration, licensvalidering, lejerkonfiguration, netværkskonfiguration
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
ms.openlocfilehash: bae66223494d8de98737516cef1a2c407d7d1a6a
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783516"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Konfigurer Microsoft Defender for Endpoint installation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Udrulning af Defender for Endpoint er en trefaset proces:

|[![udrulningsfasen – forbered.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Fase 1: Forbered](prepare-deployment.md) | ![udrulningsfase – installation](images/phase-diagrams/setup.png#lightbox)<br>Fase 2: Installation | [![udrulningsfase – onboard](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Fase 3: Onboard](onboarding.md)|
|---|---|---|
||*Du er her!*||

Du er i øjeblikket i konfigurationsfasen.

I dette installationsscenarie får du vejledning i trinnene på:

- Licensvalidering
- Lejerkonfiguration
- Netværkskonfiguration

> [!NOTE]
> Med henblik på at guide dig gennem en typisk udrulning dækker dette scenarie kun brugen af Microsoft Endpoint Configuration Manager. Defender for Endpoint understøtter brugen af andre onboardingværktøjer, men dækker ikke disse scenarier i installationsvejledningen. Du kan få flere oplysninger under [Onboard enheder til Microsoft Defender for Endpoint](onboard-configure.md).

## <a name="check-license-state"></a>Kontrollér licenstilstand

Kontrol af licenstilstanden, og om den blev korrekt klargjort, kan udføres via Administration eller via **Microsoft Azure-portalen**.

1. Hvis du vil have vist dine licenser, skal du gå til **Microsoft Azure-portalen** og navigere til [afsnittet Microsoft Azure portallicens](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Siden Azure-licenser" lightbox="images/atp-licensing-azure-portal.png":::

1. Alternativt kan du i Administration navigere til **Faktureringsabonnementer**\>.

    På skærmen kan du se alle de klargjorte licenser og deres aktuelle **status**.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Siden Faktureringslicenser" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Validering af cloudtjenesteudbyder

Hvis du vil have adgang til, hvilke licenser der klargøres til din virksomhed, og for at kontrollere licensernes tilstand, skal du gå til Administration.

1. Vælg **Administrer tjenester > Office 365** på **partnerportalen**.

2. Hvis du klikker på linket **Partnerportal** , åbnes indstillingen **Administrator på vegne** af , og du får adgang til kundeadministrationen.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Administrationsportalen Office 365" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Lejerkonfiguration

Det er nemt at onboarde til Microsoft Defender for Endpoint. I navigationsmenuen skal du vælge et hvilket som helst element under afsnittet Slutpunkter eller en hvilken som helst Microsoft 365 Defender funktion, f.eks. Hændelser, Jagt, Handlingscenter eller Trusselsanalyse for at starte onboardingprocessen.

Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> fra en webbrowser.

## <a name="data-center-location"></a>Placering af datacenter
Microsoft Defender for Endpoint gemmer og behandler data på [samme placering, som bruges af Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Hvis Microsoft 365 Defender endnu ikke er slået til, vil onboarding til Microsoft Defender for Endpoint også aktivere Microsoft 365 Defender, og der vælges automatisk en ny placering af datacenteret baseret på placeringen af aktive Microsoft 365  sikkerhedstjenester. Den valgte datacenterplacering vises på skærmen.

## <a name="network-configuration"></a>Netværkskonfiguration

Hvis organisationen ikke kræver, at slutpunkterne bruger en proxy til at få adgang til internettet, skal du springe dette afsnit over.

Den Microsoft Defender for Endpoint sensor kræver, at Microsoft Windows HTTP (WinHTTP) rapporterer sensordata og kommunikerer med Microsoft Defender for Endpoint-tjenesten. Den integrerede Microsoft Defender for Endpoint-sensor kører i systemkonteksten ved hjælp af LocalSystem-kontoen. Sensoren bruger Microsoft Windows HTTP Services (WinHTTP) til at aktivere kommunikation med Microsoft Defender for Endpoint cloudtjenesten. Konfigurationsindstillingen WinHTTP er uafhængig af indstillingerne for wininet-proxyindstillingerne (Windows Internet) og kan kun finde en proxyserver ved hjælp af følgende registreringsmetoder:

- **Metoder til automatisk søgning**:
  - Gennemsigtig proxy
  - Web Proxy Autodiscovery Protocol (WPAD)

  Hvis der er implementeret en gennemsigtig proxy eller WPAD i netværkstopologien, er der ikke behov for særlige konfigurationsindstillinger. Du kan få flere oplysninger om Microsoft Defender for Endpoint URL-adresseudeladelser i proxytjenestens [URL-adresser](production-deployment.md#proxy-service-urls) i dette dokument for at få oplysninger om listen over tilladte URL-adresser eller om [Konfigurer indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **Manuel statisk proxykonfiguration**:
  - Registreringsdatabasebaseret konfiguration
  - WinHTTP konfigureret ved hjælp af kommandoen netsh

    Egner sig kun til stationære computere i en stabil topologi (f.eks. et skrivebord i et virksomhedsnetværk bag den samme proxy).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Konfigurer proxyserveren manuelt ved hjælp af en registreringsdatabasebaseret statisk proxy

Konfigurer en registreringsdatabasebaseret statisk proxy for kun at tillade, at Microsoft Defender for Endpoint sensor rapporterer diagnosticeringsdata og kommunikerer med Microsoft Defender for Endpoint tjenester, hvis en computer ikke har tilladelse til at oprette forbindelse til internettet. Den statiske proxy kan konfigureres via Gruppepolitik (GP). Du kan finde gruppepolitikken under:

- Administrative skabeloner \> Windows komponenter \> Dataindsamling og eksempelbuilds \> Konfigurer godkendt proxyanvendelse for tjenesten Tilsluttet brugeroplevelse og telemetri
- Angiv den til **Aktiveret,** og vælg **Deaktiver godkendt proxyanvendelse**

1. Åbn administrationskonsollen Gruppepolitik.
2. Opret en politik, eller rediger en eksisterende politik baseret på organisationens praksisser.
3. Rediger Gruppepolitik, og naviger til **Administrative skabeloner \> Windows Komponenter \> Dataindsamling og Eksempelbuilds \> Konfigurer godkendt proxyanvendelse for tjenesten Tilsluttet brugeroplevelse og telemetri**.

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="De indstillinger, der er relateret til konfiguration af brugspolitikken" lightbox="images/atp-gpo-proxy1.png":::

4. Vælg **Aktiveret**.
5. Vælg **Deaktiver godkendt proxyanvendelse**.
6. Gå til **Administrative skabeloner \> Windows Komponenter \> Dataindsamling og Eksempelbuilds \> Konfigurer forbundne brugeroplevelser og telemetri**.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="De indstillinger, der er relateret til konfiguration af den forbundne brugeroplevelse og telemetri" lightbox="images/atp-gpo-proxy2.png":::

7. Vælg **Aktiveret**.
8. Angiv **navnet på proxyserveren**.

Politikken angiver to registreringsdatabaseværdier `TelemetryProxyServer` som REG_SZ og `DisableEnterpriseAuthProxy` som REG_DWORD under registreringsdatabasenøglen `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

Registreringsdatabaseværdien `TelemetryProxyServer` har følgende strengformat:

```text
<server name or ip>:<port>
```

Eksempel: 10.0.0.6:8080

Registreringsdatabaseværdien `DisableEnterpriseAuthProxy` skal angives til 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Konfigurer proxyserveren manuelt ved hjælp af kommandoen netsh

Brug netsh til at konfigurere en statisk proxy for hele systemet.

> [!NOTE]
>
> - Dette påvirker alle programmer, herunder Windows tjenester, der bruger WinHTTP med standardproxy.
> - Bærbare computere, der skifter topologi (f.eks. fra kontor til hjem) fungerer ikke korrekt med netsh. Brug den registreringsdatabasebaserede statiske proxykonfiguration.

1. Åbn en kommandolinje med administratorrettigheder:
    1. Gå til **Start,** og skriv **cmd**.
    1. Højreklik på **Kommandoprompt,** og vælg **Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Eksempel: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Proxykonfiguration for enheder på et niveau ned

Down-Level enheder omfatter Windows 7 SP1- og Windows 8.1-arbejdsstationer samt Windows Server 2008 R2 og andre serveroperativsystemer, der tidligere er onboardet ved hjælp af Microsoft-overvågningsagenten. Disse operativsystemer har proxyen konfigureret som en del af Microsoft Management Agent til at håndtere kommunikation fra slutpunktet til Azure. Se Microsoft Management Agent Fast Deployment Guide for at få oplysninger om, hvordan en proxy er konfigureret på disse enheder.

### <a name="proxy-service-urls"></a>URL-adresser til proxytjeneste

URL-adresser, der indeholder v20 i dem, er kun nødvendige, hvis du har Windows 10, version 1803 eller Windows 11 enheder. Er f.eks. kun nødvendig, `us-v20.events.data.microsoft.com` hvis enheden er på Windows 10, version 1803 eller Windows 11.

Hvis en proxy eller firewall blokerer anonym trafik, når Microsoft Defender for Endpoint sensor opretter forbindelse fra systemkonteksten, skal du sørge for, at anonym trafik er tilladt i de angivne URL-adresser.

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Sørg for, at der ikke er nogen regler for firewall- eller netværksfiltrering, der vil nægte adgang til disse URL-adresser, eller du skal muligvis oprette en *regel for tilladelse* specifikt for dem.

<br>

****


|Regneark med domæneliste| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresseliste til kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OPERATIVSYSTEM til kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Næste trin

[![**Fase 3: Onboard**.](images/onboard.png#lightbox)] <br> [Fase 3: Onboard enheder](onboarding.md) til tjenesten, så den Microsoft Defender for Endpoint tjeneste kan få sensordata fra dem.
