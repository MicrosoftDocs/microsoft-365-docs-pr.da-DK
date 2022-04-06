---
title: Fejlfinding Microsoft Defender for Endpoint onboardingproblemer
description: Foretag fejlfinding af problemer, der kan opstå under onboarding af enheder eller Microsoft Defender for Endpoint-tjenesten.
keywords: fejlfinding af onboarding, onboardingproblemer, logføring, dataindsamling og eksempel builds, sensordata og diagnosticering
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 9813857bffe62ab26d377d49b2830f55d0f38f93
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473491"
---
# <a name="troubleshoot-microsoft-defender-for-endpoint-onboarding-issues"></a>Fejlfinding Microsoft Defender for Endpoint onboardingproblemer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Windows Server 2012 R2
- Windows Server 2016
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Du skal muligvis foretage fejlfinding af Microsoft Defender for Endpoint onboardingprocessen, hvis du støder på problemer.
Denne side indeholder detaljerede trin til fejlfinding af onboardingproblemer, der kan opstå, når du installerer med et af installationsværktøjerne, og almindelige fejl, der kan opstå på enhederne.

Før du går i gang med fejlfinding af problemer med onboardingværktøjer, er det vigtigt at kontrollere, om minimumskravene er opfyldt for onboardingenheder til tjenesterne. [Få mere at vide om krav til licenser, hardware og software for onboardingenheder til tjenesten](minimum-requirements.md).

## <a name="troubleshoot-issues-with-onboarding-tools"></a>Fejlfinding af problemer med onboardingværktøjer

Hvis du har fuldført onboardingprocessen og ikke kan se enheder på listen Enheder efter [](investigate-machines.md) en time, kan det angive et problem med onboarding eller forbindelse.

### <a name="troubleshoot-onboarding-when-deploying-with-group-policy"></a>Fejlfinding i forbindelse med onboarding, når du installerer med Gruppepolitik

Installation med Gruppepolitik udføres ved at køre onboarding-scriptet på enhederne. Den Gruppepolitik konsol angiver ikke, om installationen er fuldført eller ej.

Hvis du har fuldført onboardingprocessen og ikke kan se enheder på listen Enheder efter [](investigate-machines.md) en time, kan du kontrollere outputtet af scriptet på enhederne. Få mere at vide under [Fejlfinding i forbindelse med onboarding, når du installerer med et script](#troubleshoot-onboarding-when-deploying-with-a-script).

Hvis scriptet er fuldført korrekt, skal du [se Fejlfinding af onboardingproblemer på enhederne](#troubleshoot-onboarding-issues-on-the-device) for yderligere fejl, der kan opstå.

### <a name="troubleshoot-onboarding-issues-when-deploying-with-microsoft-endpoint-configuration-manager"></a>Fejlfinding af onboardingproblemer ved installation med Microsoft Endpoint Configuration Manager

Når du onboarder enheder ved hjælp af følgende versioner af Configuration Manager:

- Microsoft Endpoint Configuration Manager
- System Center 2012 Configuration Manager
- System Center 2012 R2 Configuration Manager

Installation med de ovennævnte versioner af Configuration Manager udføres ved at køre onboarding-scriptet på enhederne. Du kan spore installationen i Configuration Manager Konsol.

Hvis installationen mislykkes, kan du kontrollere outputtet fra scriptet på enhederne.

Hvis onboarding blev gennemført uden problemer, men enhederne ikke vises på listen  Enheder efter en time, skal du se Foretage fejlfinding af [onboardingproblemer](#troubleshoot-onboarding-issues-on-the-device) på enheden for yderligere fejl, der kan opstå.

### <a name="troubleshoot-onboarding-when-deploying-with-a-script"></a>Fejlfinding af onboarding ved implementering med et script

**Kontrollér resultatet af scriptet på enheden:**

1. Klik **på Start**, **skriv Logbog**, og tryk på **Enter**.

2. Gå **til Windows Logføring**\>.

3. Se efter en hændelse fra **WDATPOnboarding-hændelseskilden** .

Hvis scriptet mislykkes, og hændelsen er en fejl, kan du kontrollere hændelses-id'et i følgende tabel for at hjælpe dig med at foretage fejlfinding af problemet.

> [!NOTE]
> Følgende hændelses-id'er er kun specifikke for onboarding-scriptet.

<br>

****

|Hændelses-id|Fejltype|Trin til løsning|
|:---:|---|---|
|`5`|Offboarding-data blev fundet, men kunne ikke slettes|Kontrollér tilladelserne til registreringsdatabasen, især <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.|
|`10`|Onboardingdata kunne ikke skrives til registreringsdatabasen|Kontrollér tilladelserne til registreringsdatabasen, især <p> `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`. <p> Kontrollér, at scriptet er blevet kørt som administrator.|
|`15`|Sense-tjenesten kunne ikke startes|Kontrollér tjenestetjenestens tilstand (`sc query sense` kommando). Sørg for, at den ikke er i en mellemliggende tilstand (*'Pending_Stopped'*, *'Pending_Running'*), og prøv at køre scriptet igen (med administratorrettigheder). <p> Hvis enheden kører Windows 10, returnerer version 1607`sc query sense`, og kørsel af kommandoen returnerer `START_PENDING`, genstart enheden. Hvis genstart af enheden ikke afhjælper problemet, skal du opgradere til KB4015217 og prøve at starte igen.|
|`15`|Sense-tjenesten kunne ikke startes|Hvis fejlmeddelelsen om fejlen er: Systemfejl 577 eller fejl 1058 er opstået, skal du aktivere Microsoft Defender Antivirus ELAM-driveren, se Kontrollér, at [Microsoft Defender Antivirus](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) ikke er deaktiveret af en politik for at få vejledning.|
|`30`|Scriptet kunne ikke vente på, at tjenesten begynder at køre|Tjenesten kan have taget længere tid at starte, eller der opstod fejl under forsøget på at starte. Du kan finde flere oplysninger om hændelser og fejl, der er relateret til SENSE, [under Gennemse hændelser og fejl ved hjælp af Hændelsesvisning](event-error-codes.md).|
|`35`|Scriptet fandt ikke den nødvendige onboardingstatus i registreringsdatabaseværdien|Når SENSE-tjenesten starter for første gang, skrives onboardingstatus til placeringen i registreringsdatabasen <p> `HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection\Status`. <p> Scriptet kunne ikke finde det efter flere sekunder. Du kan teste den manuelt og kontrollere, om den er der. Du kan finde flere oplysninger om hændelser og fejl, der er relateret til SENSE, [under Gennemse hændelser og fejl ved hjælp af Hændelsesvisning](event-error-codes.md).|
|`40`|ONBOARDING-status for SENSE-tjenesten er ikke indstillet til **1**|SENSE-tjenesten kunne ikke onboarde korrekt. Du kan finde flere oplysninger om hændelser og fejl, der er relateret til SENSE, [under Gennemse hændelser og fejl ved hjælp af Hændelsesvisning](event-error-codes.md).|
|`65`|Utilstrækkelige rettigheder|Kør scriptet igen med administratorrettigheder.|
|

### <a name="troubleshoot-onboarding-issues-using-microsoft-intune"></a>Fejlfinding af onboardingproblemer ved hjælp af Microsoft Intune

Du kan bruge Microsoft Intune til at kontrollere fejlkoder og forsøge at foretage fejlfinding af årsagen til problemet.

Hvis du har konfigureret politikker i Intune, og de ikke overføres på enheder, skal du muligvis konfigurere automatisk MDM-registrering.

Brug følgende tabeller til at forstå de mulige årsager til problemer under onboarding:

- Microsoft Intune fejlkoder og OMA-URIs tabel
- Kendte problemer med ikke-overholdelsestabel
- Tabel med Enhedshåndtering for hændelseslogfiler (mobile Enhedshåndtering)

Hvis ingen af hændelseslogfilerne og fejlfindingstrinnene fungerer, skal du  downloade det lokale script fra sektionen Enhedshåndtering på portalen og køre det i en kommandoprompt med administrator administrator.

#### <a name="microsoft-intune-error-codes-and-oma-uris"></a>Microsoft Intune fejlkoder og OMA-URIs

<br>

****

|Fejlkode hex|Fejlkode dec|Fejlbeskrivelse|OMA-URI|Mulige trin til årsag og fejlfinding|
|:---:|---|---|---|---|
|0x87D1FDE8|-2016281112|Afhjælpning mislykkedes|Onboarding <p> Offboarding|**Mulig årsag:** Onboarding eller offboarding mislykkedes på en forkert blob: forkert signatur eller manglende PreviousOrgIds-felter. <p> **Fejlfindingstrin:** <p> Kontrollér hændelses-iD'erne i [sektionen Vis onboarding af agent i sektionen Enhedshændelseslog](#view-agent-onboarding-errors-in-the-device-event-log) . <p> Kontrollér MDM-hændelseslogfilerne i følgende tabel, eller følg vejledningen i [Diagnosticere MDM-fejl Windows](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).|
||||Onboarding <p> Offboarding <p> Eksempeldeling|**Mulig årsag:** Microsoft Defender for Endpoint en registreringsdatabasenøgle til politik findes ikke, eller OMA DM-klienten har ikke tilladelse til at skrive til den. <p> **Fejlfindingstrin:** Sørg for, at følgende registreringsdatabasenøgle findes: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection` <p> Hvis den ikke findes, skal du åbne en kommando med administrator og tilføje nøglen.|
||||SenseIsRunning <p> OnboardingState <p> OrgId|**Mulig årsag:** Et forsøg på at afhjælpe dette i skrivebeskyttet egenskab. Onboarding mislykkedes. <p> **Fejlfindingstrin:** Se fejlfindingstrinnene [i Fejlfinding af onboardingproblemer på enheden](#troubleshoot-onboarding-issues-on-the-device). <p> Kontrollér MDM-hændelseslogfilerne i følgende tabel, eller følg vejledningen i [Diagnosticere MDM-fejl Windows](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10).|
||||Alle|**Mulig årsag:** Forsøg at installere Microsoft Defender for Endpoint på ikke-understøttet SKU/platform, især Holographic SKU. <p> Aktuelt understøttede platforme: <p> Enterprise, Education og Professional.<p> Serveren understøttes ikke.|
|0x87D101A9|-2016345687|SyncML(425): Den anmodede kommando mislykkedes, fordi afsenderen ikke har tilstrækkelige adgangskontroltilladelser (ACL) på modtageren.|Alle|**Mulig årsag:** Forsøg at installere Microsoft Defender for Endpoint på ikke-understøttet SKU/platform, især Holographic SKU.<p> Aktuelt understøttede platforme: <p> Enterprise, Education og Professional.|
|

#### <a name="known-issues-with-non-compliance"></a>Kendte problemer med manglende overholdelse

Den følgende tabel indeholder oplysninger om problemer med manglende overholdelse, og hvordan du kan løse problemerne.

<br>

****

|Sag|Symptomer|Mulige trin til årsag og fejlfinding|
|:---:|---|---|
|`1`|Enheden er kompatibel med SenseIsRunning OMA-URI. Men er ikke-kompatibel af OrgId-, Onboarding- og OnboardingState OMA-URI'er.|**Mulig årsag:** Kontrollér, at brugeren har overført OOBE efter Windows installation eller opgradering. Under OOBE-onboarding kunne ikke fuldføres, men SENSE kører allerede. <p> **Fejlfindingstrin:** Vent på, at OOBE afsluttes.|
|`2`|Enheden er kompatibel med OrgId, Onboarding og OnboardingState OMA-URI'er, men er ikke kompatibel med SenseIsRunning OMA-URI.|**Mulig årsag:** Sense-tjenestens starttype er angivet som "Forsinket start". Dette får nogle gange Microsoft Intune-serveren til at rapportere enheden som ikke-kompatibel af SenseIsRunning, når DM-sessionen forekommer ved systemstart. <p> **Fejlfindingstrin:** Problemet bør automatisk blive rettet inden for 24 timer.|
|`3`|Enheden er ikke-kompatibel|**Fejlfindingstrin:** Sørg for, at politikker for onboarding og offboarding ikke installeres på den samme enhed på samme tid.|
|

#### <a name="mobile-device-management-mdm-event-logs"></a>Hændelseslogfiler Enhedshåndtering mobildata (MDM)

Få vist MDM-hændelseslogfilerne for at foretage fejlfinding af problemer, der kan opstå under onboarding:

Lognavn: Microsoft\Windows\DeviceManagement-EnterpriseDiagnostics-Provider

Kanalnavn: Administrator

<br>

****

|Id|Alvorsgrad|Beskrivelse af hændelse|Fejlfindingstrin|
|---|---|---|---|
|1819|Error|Microsoft Defender for Endpoint CSP: Nodes værdi blev ikke angivet. NodeId: (%1), TokenName: (%2), Result: (%3).|Download den [kumulative opdatering til Windows 10, 1607](https://go.microsoft.com/fwlink/?linkid=829760).|
|

## <a name="troubleshoot-onboarding-issues-on-the-device"></a>Fejlfinding af onboardingproblemer på enheden

Hvis de anvendte installationsværktøjer ikke angiver en fejl i onboardingprocessen, men enheder stadig ikke vises på listen over enheder i en time, skal du gå gennem følgende bekræftelsesemner for at kontrollere, om der er opstået en fejl med Microsoft Defender for Endpoint-agenten.

- [Få vist onboardingfejl for agent i enhedshændelsesloggen](#view-agent-onboarding-errors-in-the-device-event-log)
- [Sørg for, at den diagnostiske datatjeneste er aktiveret](#ensure-the-diagnostics-service-is-enabled)
- [Sørg for, at tjenesten er indstillet til at starte](#ensure-the-service-is-set-to-start)
- [Kontrollér, at enheden har forbindelse til internettet](#ensure-the-device-has-an-internet-connection)
- [Kontrollér, Microsoft Defender Antivirus er deaktiveret af en politik](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

### <a name="view-agent-onboarding-errors-in-the-device-event-log"></a>Få vist onboardingfejl for agent i enhedshændelsesloggen

1. Klik **på Start**, **skriv Logbog**, og tryk på **Enter**.

2. I **ruden Logbog (lokal) skal** du udvide **Program- og tjenestelogfiler** \> **Microsoft** \> **Windows** \> **SENSE**.

   > [!NOTE]
   > SENSE er det interne navn, der bruges til at referere til den funktionsmåde sensor, der har Microsoft Defender for Endpoint.

3. Vælg **Drift** for at indlæse logfilen.

4. Klik på **Filtrer** aktuel **log i handlingsruden**.

5. På fanen **Filter** under Hændelsesniveau **: vælg Kritisk**, Advarsel **og** **Fejl,** og klik på **OK**.

   :::image type="content" source="images/filter-log.png" alt-text="Det Logbog logfilter" lightbox="images/filter-log.png":::

6. Hændelser, der kan angive, at problemerne vises i **ruden** Drift. Du kan forsøge at foretage fejlfinding af dem baseret på løsningerne i følgende tabel:

   <br>

   ****

   |Hændelses-id|Meddelelse|Trin til løsning|
   |:---:|---|---|
   |`5`|Microsoft Defender for Endpoint tjeneste kunne ikke oprette forbindelse til serveren på _variabel_|[Kontrollér, at enheden har internetadgang](#ensure-the-device-has-an-internet-connection).|
   |`6`|Microsoft Defender for Endpoint ikke onboardingtjeneste, og der blev ikke fundet nogen onboardingparametre. Fejlkode: _variabel_|[Kør onboarding-scriptet igen](configure-endpoints-script.md).|
   |`7`|Microsoft Defender for Endpoint kunne ikke læse onboardingparametrene. Fejlkode: _variabel_|[Kontrollér, at enheden har internetadgang](#ensure-the-device-has-an-internet-connection), og kør derefter hele onboardingprocessen igen.|
   |`9`|Microsoft Defender for Endpoint kunne ikke ændre starttypen. Fejlkode: variabel|Hvis hændelsen skete under onboarding, skal du genstarte og forsøge at køre onboardingscriptet igen. Få mere at vide under [Kør onboarding-scriptet igen](configure-endpoints-script.md). <br><br>Hvis hændelsen skete under offboarding, skal du kontakte support.|
   |`10`|Microsoft Defender for Endpoint-tjenesten kunne ikke bevare onboardingoplysningerne. Fejlkode: variabel|Hvis hændelsen skete under onboarding, skal du forsøge at køre onboardingscriptet igen. Få mere at vide under [Kør onboarding-scriptet igen](configure-endpoints-script.md). <br><br>Hvis problemet fortsætter, skal du kontakte support.|
   |`15`|Microsoft Defender for Endpoint kan ikke starte kommandokanal med URL-adresse: _variabel_|[Kontrollér, at enheden har internetadgang](#ensure-the-device-has-an-internet-connection).|
   |`17`|Microsoft Defender for Endpoint tjeneste kunne ikke ændre placeringen af forbundne brugeroplevelser og telemetritjenesten. Fejlkode: variabel|[Kør onboarding-scriptet igen](configure-endpoints-script.md). Hvis problemet fortsætter, skal du kontakte support.|
   |`25`|Microsoft Defender for Endpoint kunne ikke nulstille tilstandsstatussen i registreringsdatabasen. Fejlkode: _variabel_|Kontakt support.|
   |`27`|Det lykkedes ikke at Microsoft Defender for Endpoint i Windows Defender. Onboardingprocessen mislykkedes. Fejlkode: variabel|Kontakt support.|
   |`29`|Kunne ikke læse offboarding-parametrene. Fejltype: %1, fejlkode: %2, Beskrivelse: %3|Kontrollér, at enheden har internetadgang, og kør derefter hele offboarding-processen igen.|
   |`30`|Det lykkedes ikke at deaktivere tilstanden $(build.sense.productDisplayName) Microsoft Defender for Endpoint. Fejlkode: %1|Kontakt support.|
   |`32`|Tjenesten $(build.sense.productDisplayName) kunne ikke anmode om at stoppe sig selv efter offboarding-processen. Fejlkode: %1|Kontrollér, at tjenestens starttype er manuel, og genstart enheden.|
   |`55`|Autologgeret Secure ETW kunne ikke oprettes. Fejlkode: %1|Genstart enheden.|
   |`63`|Opdaterer starttypen for den eksterne tjeneste. Navn: %1, faktisk starttype: %2, forventet starttype: %3, udgangskode: %4|Identificer, hvad der forårsager ændringer i starttypen for den nævnte tjeneste. Hvis udgangskoden ikke er 0, kan du indstille starttypen manuelt til den forventede starttype.|
   |`64`|Starter stoppet ekstern tjeneste. Navn: %1, udgangskode: %2|Kontakt support, hvis begivenheden bliver ved med at blive vist igen.|
   |`68`|Tjenestens starttype er uventet. Tjenestenavn: %1, faktisk starttype: %2, forventet starttype: %3|Identificer, hvad der forårsager ændringer i starttype. Ret den nævnte tjenestes starttype.|
   |`69`|Tjenesten er stoppet. Tjenestenavn: %1|Start den nævnte tjeneste. Kontakt support, hvis problemet fortsætter.|
   |

Der er flere komponenter på enheden, som den Microsoft Defender for Endpoint, afhænger af for at fungere korrekt. Hvis der ikke er nogen onboardingrelaterede fejl i Microsoft Defender for Endpoint-agenthændelsesloggen, skal du fortsætte med følgende trin for at sikre, at de ekstra komponenter er konfigureret korrekt.

<span id="ensure-the-diagnostics-service-is-enabled" />

### <a name="ensure-the-diagnostic-data-service-is-enabled"></a>Sørg for, at den diagnostiske datatjeneste er aktiveret

Hvis enhederne ikke rapporterer korrekt, skal du muligvis kontrollere, at den diagnostiske Windows er indstillet til at starte automatisk og kører på enheden. Tjenesten er muligvis deaktiveret af andre programmer eller ændringer i brugerkonfigurationen.

Først skal du kontrollere, at tjenesten er indstillet til at starte automatisk, når Windows starter, og derefter skal du kontrollere, at tjenesten kører i øjeblikket (og starte den, hvis den ikke er).

### <a name="ensure-the-service-is-set-to-start"></a>Sørg for, at tjenesten er indstillet til at starte

**Brug kommandolinjen til at kontrollere starttypen Windows diagnostiske datatjeneste**:

1. Åbn en kommandoprompt med administrator på enheden:

   a. Klik **på Start**, **skriv cmd**, og tryk på **Enter**.

   b. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```console
   sc qc diagtrack
   ```

   Hvis tjenesten er aktiveret, bør resultatet se ud som på følgende skærmbillede:

   :::image type="content" source="images/windefatp-sc-qc-diagtrack.png" alt-text="Resultatet af sc-forespørgselskommandoen for diagtrack" lightbox="images/windefatp-sc-qc-diagtrack.png":::

   Hvis den `START_TYPE` ikke er angivet til `AUTO_START`, skal du indstille tjenesten til at starte automatisk.

**Brug kommandolinjen til at indstille Windows til at starte automatisk:**

1. Åbn en kommandoprompt med administrator på enheden:

   a. Klik **på Start**, **skriv cmd**, og tryk på **Enter**.

   b. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

2. Angiv følgende kommando, og tryk på **Enter**:

   ```console
   sc config diagtrack start=auto
   ```

3. Der vises en vellykket meddelelse. Bekræft ændringen ved at angive følgende kommando, og tryk på **Enter**:

   ```console
   sc qc diagtrack
   ```

4. Start tjenesten. Skriv følgende kommando i kommandoprompten, og tryk på **Enter**:

   ```console
   sc start diagtrack
   ```

### <a name="ensure-the-device-has-an-internet-connection"></a>Kontrollér, at enheden har forbindelse til internettet

Sensoren Microsoft Defender for Endpoint Microsoft Windows HTTP (WinHTTP) for at rapportere sensordata og kommunikere med Microsoft Defender for Endpoint-tjenesten.

WinHTTP er uafhængig af internetbrowsing-proxyindstillingerne og andre brugerkontekstprogrammer og skal kunne registrere de proxyservere, der er tilgængelige i dit specifikke miljø.

Hvis du vil sikre dig, at sensoren har forbindelse til tjenesten, skal du følge trinnene, der er beskrevet i emnet Bekræft [klientforbindelsen Microsoft Defender for Endpoint url-adresser](configure-proxy-internet.md#verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls) for tjenesten.

Hvis bekræftelsen mislykkes, og dit miljø bruger en proxy til at oprette forbindelse til internettet, skal du følge trinnene beskrevet i emnet Konfigurer [indstillinger for proxy og internetforbindelse](configure-proxy-internet.md) .

### <a name="ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy"></a>Kontrollér, Microsoft Defender Antivirus er deaktiveret af en politik

> [!IMPORTANT]
> Følgende gælder kun for enheder, der endnu  ikke har modtaget opdateringen fra august 2020 (version 4.18.2007.8) til Microsoft Defender Antivirus.
>
> Opdateringen sikrer, at Microsoft Defender Antivirus ikke kan deaktiveres på klientenheder via systempolitik.

**Problem**: Tjenesten Microsoft Defender for Endpoint ikke efter onboarding.

**Symptom**: Onboarding fuldføres, men du får vist fejl 577 eller fejl 1058, når du forsøger at starte tjenesten.

**Løsning**: Hvis dine enheder kører en tredjeparts antimalwareklient, skal Microsoft Defender for Endpoint-agenten have aktiveret antimalwaredriveren (Early Launch Antimalware). Du skal sørge for, at den ikke deaktiveres af en systempolitik.

- Afhængigt af det værktøj, du bruger til at implementere politikker, skal du kontrollere, at følgende Windows Defender politikker er ryddet:

  - DisableAntiSpyware
  - DisableAntiVirus

  Eksempelvis bør der Gruppepolitik være nogen poster som f.eks. følgende værdier:

  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiSpyware"/></Key>`
  - `<Key Path="SOFTWARE\Policies\Microsoft\Windows Defender"><KeyValue Value="0" ValueKind="DWord" Name="DisableAntiVirus"/></Key>`

> [!IMPORTANT]
> Indstillingen `disableAntiSpyware` er udgået og ignoreres på alle Windows 10-enheder pr. august 2020 (version 4.18.2007.8) til Microsoft Defender Antivirus.

- Når du har ryddet politikken, skal du køre onboardingtrinnene igen.

- Du kan også kontrollere de tidligere registreringsdatabasenøgleværdier for at bekræfte, at politikken er deaktiveret ved at åbne registreringsdatabasenøglen `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender`.

  :::image type="content" source="images/atp-disableantispyware-regkey.png" alt-text="Registreringsdatabasenøglen til Microsoft Defender Antivirus" lightbox="images/atp-disableantispyware-regkey.png":::

   > [!NOTE]
   > Alle Windows Defender (wdboot, wdfilter, wdnisdrv, wdnissvc og windefend) bør være i standardtilstand. Ændring af start af disse tjenester understøttes ikke, og det kan tvinge dig til at genimage systemet.
   >
   > Eksempel på standardkonfigurationer for WdBoot og WdFilter:
   >
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdBoot"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`
   > - `<Key Path="SYSTEM\CurrentControlSet\Services\WdFilter"><KeyValue Value="0" ValueKind="DWord" Name="Start"/></Key>`

## <a name="troubleshoot-onboarding-issues"></a>Fejlfinding af onboardingproblemer 

> [!NOTE]
> Følgende fejlfindingsvejledning gælder kun for Windows Server 2016 og lavere.

Hvis du støder på problemer under onboarding af en server, skal du gennemgå følgende bekræftelsestrin for at løse eventuelle problemer.


- [Sørg for, at Microsofts overvågningsagent (ÆLDRE) er installeret og konfigureret til at rapportere sensordata til tjenesten](configure-server-endpoints.md)
- [Kontrollér, at serverproxy- og internetforbindelsesindstillingerne er konfigureret korrekt](configure-server-endpoints.md)

Du skal muligvis også kontrollere følgende:

- Kontrollér, at der kører Microsoft Defender for Endpoint tjeneste under **fanen** Processer **i Jobliste**. Eksempel:

  :::image type="content" source="images/atp-task-manager.png" alt-text="Procesvisningen med Microsoft Defender for Endpoint tjeneste, der kører" lightbox="images/atp-task-manager.png":::

- Kontrollér **Logbog** \> **Applications and Services Logs** \> **Operation Manager** for at se, om der er nogen fejl.

- Under **Tjenester** kan du kontrollere, **om Microsofts overvågningsagent** kører på serveren. For eksempel

  :::image type="content" source="images/atp-services.png" alt-text="Tjenesterne" lightbox="images/atp-services.png":::

- I **OMS (Microsoft Monitoring Agent** \> **Azure Log Analytics)** skal du kontrollere arbejdsområderne og kontrollere, at statussen kører.

  :::image type="content" source="images/atp-mma-properties.png" alt-text="Egenskaberne for Microsofts overvågningsagent" lightbox="images/atp-mma-properties.png":::

- Kontrollér, at enhederne afspejles **på listen Enheder** i portalen.

## <a name="confirming-onboarding-of-newly-built-devices"></a>Bekræftelse af onboarding af nybyggede enheder

Der kan være forekomster, når onboarding er installeret på en nyligt oprettet enhed, men ikke fuldført.

Nedenstående trin giver vejledning til følgende scenarie:

- Onboarding-pakken installeres på nybyggede enheder
- Sensoren starter ikke, fordi OOBE (Out of box Experience) eller første brugerlogon ikke er fuldført
- Enheden slukkes eller genstartes, før slutbrugeren udfører et første logon
- I dette scenarie starter SENSE-tjenesten ikke automatisk, selvom onboardingpakken blev installeret

> [!NOTE]
> Brugerlogon efter OOBE er ikke længere påkrævet, for at SENSE-tjenesten kan starte på følgende eller nyere Windows-versioner: Windows 10, version 1809- eller Windows Server 2019 eller Windows Server 2022 med opdateringsopdateringen [for 22. april 2021](https://support.microsoft.com/kb/5001384). Windows 10, version 1909 med [opdateringsopdateringsopdateringen for april 2021](https://support.microsoft.com/kb/5001396). Windows 10, version 2004/20H2 med [opdateringsopdateringsopdateringen for 28. april 2021](https://support.microsoft.com/kb/5001391). 


> [!NOTE]
> Følgende trin er kun relevante, når du bruger Microsoft Endpoint Configuration Manager. Du kan finde flere oplysninger om onboarding ved Microsoft Endpoint Configuration Manager under [Microsoft Defender for Endpoint](/mem/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection).

1. Opret et program Microsoft Endpoint Configuration Manager.

   :::image type="content" source="images/mecm-1.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-1" lightbox="images/mecm-1.png":::

2. Vælg **Angiv programoplysningerne manuelt**.

   :::image type="content" source="images/mecm-2.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-2" lightbox="images/mecm-2.png":::

3. Angiv oplysninger om programmet, og vælg derefter **Næste**.

   :::image type="content" source="images/mecm-3.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-3" lightbox="images/mecm-3.png":::

4. Angiv oplysninger om softwarecenteret, og vælg derefter **Næste**.

   :::image type="content" source="images/mecm-4.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-4" lightbox="images/mecm-4.png":::

5. Vælg **Tilføj i Installationstyper**.

   :::image type="content" source="images/mecm-5.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-5" lightbox="images/mecm-5.png":::

6. Vælg **Angiv oplysninger om installationstype manuelt**, og vælg derefter **Næste**.

   :::image type="content" source="images/mecm-6.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-6" lightbox="images/mecm-6.png":::

7. Angiv oplysninger om installationstypen, og vælg derefter **Næste**.

   :::image type="content" source="images/mecm-7.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-7" lightbox="images/mecm-7.png":::

8. I **Installationsprogram** \> **til indhold** skal du angive kommandoen: `net start sense`.

   :::image type="content" source="images/mecm-8.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-8" lightbox="images/mecm-8.png":::

9. I **Registreringsmetode skal** du vælge **Konfigurer regler for at registrere tilstedeværelsen af denne installationstype** og derefter vælge **Tilføj delsætning**.

   :::image type="content" source="images/mecm-9.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-9" lightbox="images/mecm-9.png":::

10. Angiv følgende oplysninger om registreringsreglen, og vælg derefter **OK**:

    :::image type="content" source="images/mecm-10.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-10" lightbox="images/mecm-10.png":::

11. Vælg **Næste under** **Registreringsmetode**.

    :::image type="content" source="images/mecm-11.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-11" lightbox="images/mecm-11.png":::

12. Angiv **følgende oplysninger** i Brugeroplevelse, og vælg derefter **Næste**:

    :::image type="content" source="images/mecm-12.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-12" lightbox="images/mecm-12.png":::

13. Vælg **Næste** under **Krav**.

    :::image type="content" source="images/mecm-13.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-13" lightbox="images/mecm-13.png":::

14. Vælg **Næste under** **Afhængigheder**.

    :::image type="content" source="images/mecm-14.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-14" lightbox="images/mecm-14.png":::

15. I **Oversigt skal** du vælge **Næste**.

    :::image type="content" source="images/mecm-15.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-15" lightbox="images/mecm-15.png":::

16. Vælg **Luk** under **Fuldførelse**.

    :::image type="content" source="images/mecm-16.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-16" lightbox="images/mecm-16.png":::

17. Vælg **Næste under** **Installationstyper**.

    :::image type="content" source="images/mecm-17.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-17" lightbox="images/mecm-17.png":::

18. I **Oversigt skal** du vælge **Næste**.

    :::image type="content" source="images/mecm-18.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-18" lightbox="images/mecm-18.png":::

    Status vises derefter: Den :::image type="content" source="images/mecm-19.png" alt-text="Microsoft Endpoint Configuration Manager configuration-19" lightbox="images/mecm-19.png":::

19. Vælg **Luk** under **Fuldførelse**.

    :::image type="content" source="images/mecm-20.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-20" lightbox="images/mecm-20.png":::

20. Du kan nu installere programmet ved at højreklikke på appen og vælge **Installér**.

    :::image type="content" source="images/mecm-21.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-21" lightbox="images/mecm-21.png":::

21. I **Generelt skal** du **vælge Fordel automatisk indhold for afhængigheder** og **Gennemse**.

    :::image type="content" source="images/mecm-22.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-22" lightbox="images/mecm-22.png":::

22. I **Indhold skal** du **vælge Næste**.

    :::image type="content" source="images/mecm-23.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-23" lightbox="images/mecm-23.png":::

23. I **Installationsindstillinger skal** du vælge **Næste**.

    :::image type="content" source="images/mecm-24.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-24" lightbox="images/mecm-24.png":::

24. I **Planlægning** skal **du vælge Så tidligt som muligt efter den tilgængelige tid** og derefter vælge **Næste**.

    :::image type="content" source="images/mecm-25.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-25" lightbox="images/mecm-25.png":::

25. I **Brugeroplevelse skal** du **vælge Be bekræftelse af ændringer ved deadline eller under et vedligeholdelsesvindue (kræver genstart)** og derefter vælge **Næste**.

    :::image type="content" source="images/mecm-26.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-26" lightbox="images/mecm-26.png":::

26. I **Beskeder skal** du vælge **Næste**.

    :::image type="content" source="images/mecm-27.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-27" lightbox="images/mecm-27.png":::

27. I **Oversigt skal** du vælge **Næste**.

    :::image type="content" source="images/mecm-28.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-28" lightbox="images/mecm-28.png":::
      

    Status vises derefter Den Microsoft Endpoint Configuration Manager :::image type="content" source="images/mecm-29.png" alt-text="konfiguration-29" lightbox="images/mecm-29.png":::

28. Vælg **Luk** under **Fuldførelse**.

    :::image type="content" source="images/mecm-30.png" alt-text="Den Microsoft Endpoint Configuration Manager configuration-30" lightbox="images/mecm-30.png":::

## <a name="related-topics"></a>Relaterede emner

- [Fejlfinding af Microsoft Defender for Endpoint](troubleshoot-mdatp.md)
- [Onboard-enheder](onboard-configure.md)
- [Konfigurere indstillinger for enhedsproxy og internetforbindelse](configure-proxy-internet.md)
