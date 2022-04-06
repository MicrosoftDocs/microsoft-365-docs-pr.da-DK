---
title: Konfigurer Microsoft Defender for Endpoint installation
description: Få mere at vide om, hvordan du konfigurerer installationen Microsoft Defender for Endpoint
keywords: Installér, konfiguration, licensvalidering, lejerkonfiguration, netværkskonfiguration
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
ms.openlocfilehash: e1fbfdaa71cc57a7797a2b95c96a56abba4fcc40
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64506983"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Konfigurer Microsoft Defender for Endpoint installation

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Implementering af Defender til slutpunkt er en trefaset proces:

|[![implementeringsfase – klargøring.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Fase 1: Forbered](prepare-deployment.md) | ![Installationsfase – konfiguration](images/phase-diagrams/setup.png#lightbox)<br>Fase 2: Konfiguration | [![Implementeringsfase – onboard](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Fase 3: Onboard](onboarding.md)|
|---|---|---|
||*Du er her!*||

Du er i øjeblikket i opsætningsfasen.

I dette installationsscenarie bliver du vejledt gennem trinnene til:

- Licenseringsvalidering
- Lejerkonfiguration
- Netværkskonfiguration

> [!NOTE]
> For at kunne guide dig gennem en typisk installation vil dette scenarie kun omfatte brugen af Microsoft Endpoint Configuration Manager. Defender til Slutpunkt understøtter brug af andre onboardingværktøjer, men den dækker ikke disse scenarier i installationsvejledningen. Få mere at vide under [Onboard-enheder for at Microsoft Defender for Endpoint](onboard-configure.md).

## <a name="check-license-state"></a>Kontrollér licenstilstanden

Kontrol af licenstilstanden, og om den er blevet korrekt klargjort, kan udføres via Administration eller **via Microsoft Azure portal**.

1. For at få vist dine licenser skal du **gå Microsoft Azure portal** og gå til [afsnittet Microsoft Azure portallicens](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Siden Azure-licensering" lightbox="images/atp-licensing-azure-portal.png":::

1. Alternativt kan du i Administration gå til **Faktureringsabonnementer**\>.

    På skærmen får du vist alle de klargjorte licenser og deres aktuelle **Status**.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Siden med faktureringslicenser" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Validering fra udbyder af skytjeneste

Hvis du vil have adgang til hvilke licenser, der er klargjort til din virksomhed, og du vil kontrollere licensens tilstand, skal du gå til Administration.

1. Fra **Partnerportalen skal** du **vælge Administrer > Office 365**.

2. Når du klikker **på linket Partnerportal** , åbnes **indstillingen Administrator på** vegne af, og du får adgang til kundeadministrationscentret.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Den Office 365 administrationsportal" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Lejerkonfiguration

Onboarding til Microsoft Defender for Endpoint er nemt. I navigationsmenuen skal du vælge et hvilket som helst element under sektionen Slutpunkter eller en hvilken som helst Microsoft 365 Defender-funktion, som f.eks Hændelser, Jagt, Handlingscenter eller Trusselsanalyse for at starte onboardingprocessen.

Fra en webbrowser skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

## <a name="data-center-location"></a>Datacenterplacering
Microsoft Defender for Endpoint lagrer og behandler data på den [samme placering, som de bruges af Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Hvis Microsoft 365 Defender ikke er blevet slået til endnu, vil onboarding til Microsoft Defender for Endpoint også slå Microsoft 365 Defender til, og en ny datacenterplacering vælges automatisk baseret på placeringen af aktive Microsoft 365  sikkerhedstjenester. Den valgte datacenterplacering vises på skærmen.

## <a name="network-configuration"></a>Netværkskonfiguration

Hvis organisationen ikke kræver, at slutpunkterne bruger en proxy for at få adgang til internettet, skal du springe dette afsnit over.

Sensoren Microsoft Defender for Endpoint Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Microsoft Defender for Endpoint-tjenesten. Den integrerede Microsoft Defender for Endpoint kører i systemkonteksten ved hjælp af LocalSystem-kontoen. Sensoren bruger Microsoft Windows HTTP-tjenester (WinHTTP) til at aktivere kommunikation med Microsoft Defender for Endpoint-skytjenesten. Indstillingen WinHTTP-konfiguration er uafhængig af Windows-internetbrowsingproxyindstillingerne (WinINet), og den kan kun opdage en proxyserver ved hjælp af følgende registreringsmetoder:

- **Autodiscovery-metoder**:
  - Gennemsigtig proxy
  - WPAD (Web Proxy Autodiscovery Protocol)

  Hvis en gennemsigtig proxy eller WPAD er blevet implementeret i netværktopologien, er der ikke behov for særlige konfigurationsindstillinger. Du kan finde flere oplysninger om Microsoft Defender for Endpoint URL-undtagelser i proxyen i afsnittet URL-adresser for [proxytjenester](production-deployment.md#proxy-service-urls) i dette dokument for listen over tilladte URL-adresser eller konfigurere enhedsproxy og indstillinger for [internetforbindelse](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **Manuel statisk proxykonfiguration**:
  - Registreringsdatabasebaseret konfiguration
  - WinHTTP konfigureret ved hjælp af netsh-kommando

    Kun egnet til skriveborde i en stabil topologi (f.eks.: en stationær computer i et firmanetværk bag den samme proxy).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Konfigurer proxyserveren manuelt ved hjælp af en statisk proxy i registreringsdatabasen

Konfigurer en registreringsbaseret statisk proxy for kun at tillade Microsoft Defender for Endpoint-sensor at rapportere diagnostiske data og kommunikere med Microsoft Defender for Endpoint-tjenester, hvis en computer ikke har tilladelse til at oprette forbindelse til internettet. Den statiske proxy kan konfigureres via Gruppepolitik (GP). Gruppepolitikken findes under:

- Administrative skabeloner \> Windows komponenter \> Dataindsamling og eksempel builds \> konfigureret godkendt proxybrug for den forbundne brugeroplevelse og telemetritjeneste
- Angiv den til **Aktiveret,** og **vælg Deaktiver godkendt proxybrug**

1. Åbn Gruppepolitik Administrationskonsol.
2. Opret en politik, eller rediger en eksisterende politik baseret på organisatoriske fremgangsmåder.
3. Rediger indholdstyperne Gruppepolitik og naviger til **Administrative \> skabeloner Windows Components \> Data Collection and Preview Builds \> Configured Proxy usage for the Connected User Experience and Telemetry Service**.

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="De indstillinger, der er relateret til konfiguration af politikken for brug" lightbox="images/atp-gpo-proxy1.png":::

4. Vælg **Aktiveret**.
5. Vælg **Deaktiver godkendt proxybrug**.
6. Naviger **til Administrative skabeloner \> Windows dataindsamling \> og eksempel builds Forbundne \> brugeroplevelser og telemetri**.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="De indstillinger, der er relateret til konfiguration af den forbundne brugeroplevelse og telemetri" lightbox="images/atp-gpo-proxy2.png":::

7. Vælg **Aktiveret**.
8. Angiv navnet **på proxyserveren**.

Politikken angiver to registreringsdatabaseværdier som `TelemetryProxyServer` REG_SZ som `DisableEnterpriseAuthProxy` REG_DWORD under registreringsdatabasenøglen `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

Registreringsdatabaseværdien `TelemetryProxyServer` har følgende strengformat:

```text
<server name or ip>:<port>
```

Eksempel: 10.0.0.6:8080

Registreringsdatabaseværdien `DisableEnterpriseAuthProxy` skal være indstillet til 1.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Konfigurere proxyserveren manuelt ved hjælp af kommandoen Netsh

Brug netsh til at konfigurere en statisk proxy for hele systemet.

> [!NOTE]
>
> - Dette påvirker alle programmer, herunder Windows, der bruger WinHTTP med standardproxy.
> - Bærbare computere, der ændrer topologien (f.eks.: fra office til privat brug), fungerer ikke korrekt med netsh. Brug den registreringsdatabasebaserede statiske proxykonfiguration.

1. Åbn en administrator-kommandolinje:
    1. Gå til **Start,** og skriv **cmd**.
    1. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   For eksempel: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Proxykonfiguration for enheder med down-level

Down-Level-enheder omfatter Windows 7 SP1- og Windows 8.1-arbejdsstationer samt Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 og versioner af Windows Server 2016 før Windows Server CB 1803. Disse operativsystemer har konfigureret proxyen som en del af Microsoft-administrationsagenten til at håndtere kommunikation fra slutpunktet til Azure. Se Installationsvejledning til Microsoft Management Agent Fast Deployment for at få oplysninger om, hvordan en proxy er konfigureret på disse enheder.

### <a name="proxy-service-urls"></a>URL-adresser for proxytjenesten

URL-adresser, der indeholder v20 i dem, er kun nødvendige, hvis du har Windows 10, version 1803 eller Windows 11 enheder. Det er f.eks. kun nødvendigt, `us-v20.events.data.microsoft.com` hvis enheden er på Windows 10, version 1803 eller Windows 11.

Hvis en proxy eller firewall blokerer anonym trafik, mens Microsoft Defender for Endpoint sensor opretter forbindelse fra systemkontekst, skal du sørge for, at anonym trafik er tilladt i de angivne URL-adresser.

Følgende regneark, der kan downloades, viser de tjenester og deres tilknyttede URL-adresser, som dit netværk skal kunne oprette forbindelse til. Sørg for, at der ikke er nogen firewall- eller netværksfiltreringsregler, der vil nægte adgang til disse URL-adresser, eller  du skal muligvis oprette en tilladelsesregel specifikt for dem.

<br>

****


|Listen Regneark over domæner| Beskrivelse|
|---|---|
|Microsoft Defender for Endpoint URL-adresse for kommercielle kunder| Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og operativsystem for kommercielle kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Microsoft Defender for Endpoint URL-adresseliste for Gov/GCC/DoD | Regneark med specifikke DNS-poster for tjenesteplaceringer, geografiske placeringer og OS for Gov/GCC/DoD-kunder. <p> [Download regnearket her.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Næste trin

[![**Fase 3: Onboard**.](images/onboard.png#lightbox)] <br> [Fase 3: Onboard](onboarding.md): Onboard-enheder til tjenesten, så Microsoft Defender for Endpoint kan hente sensordata fra dem.
