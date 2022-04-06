---
title: Onboarde Windows-enheder ved hjælp af et lokalt script
description: Brug et lokalt script til at installere konfigurationspakken på enheder for at aktivere onboarding af enhederne til tjenesten.
keywords: konfigurer enheder ved hjælp af et lokalt script, enhedshåndtering, konfigurer Microsoft Defender for Endpoint enheder
search.appverid: met150
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
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 1ea1661a89585d46aa5fc234f6f88be66512c1be
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468693"
---
# <a name="onboard-windows-devices-using-a-local-script"></a>Onboarde Windows-enheder ved hjælp af et lokalt script

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Du kan også manuelt onboarde individuelle enheder til Defender til Slutpunkt. Det kan være en god ide at gøre dette først, når du tester tjenesten, før du forpligter dig til at onboarde alle enheder i dit netværk.

> [!IMPORTANT]
> Dette script er blevet optimeret til brug på op til ti enheder.
> Lokal scripting er en særlig onboardingmetode til evaluering af Microsoft Defender for Endpoint.
> Hyppigheden af datarapportering er indstillet højere end med andre onboardingmetoder, når du onboarder ved hjælp af et lokalt script.
> Denne indstilling er til evalueringsformål og bruges ikke normalt i produktionsinstallationer. Der er derfor grund til bekymring over påvirkningen af miljøet, så vi anbefaler, at antallet af installationer med lokale scripts begrænses til ti.
> Hvis du installerer i et produktionsmiljø som beskrevet tidligere, skal du bruge [](configure-endpoints.md) andre installationsindstillinger som f.Gruppepolitik eller Microsoft Endpoint Configuration Manager.

Se [PDF-filen](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.pdf) eller [Visio](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/security/defender-endpoint/downloads/mdatp-deployment-strategy.vsdx) for at se de forskellige stier i udrulning af Defender til Slutpunkt. 

## <a name="onboard-devices"></a>Onboard-enheder 

1.  Åbn GP-konfigurationspakken .zip fil (*WindowsDefenderATPOnboardingPackage.zip*), du hentede fra guiden til onboarding af tjenesten. Du kan også hente pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>:

    1. I **navigationsruden** skal du **vælge Indstillinger** >  **EndpointsDevice** >  **managementOnboarding** > .


Se [PDF-filen](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) eller [Visio](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) for at se de forskellige stier i udrulning af Defender til Slutpunkt.

1. Åbn GP-konfigurationspakken .zip fil (*WindowsDefenderATPOnboardingPackage.zip*), du hentede fra guiden til onboarding af tjenesten. Du kan også hente pakken fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>:
    1. I **navigationsruden** skal du **vælge Indstillinger** \> Slutpunkter **Onboarding** \> til \> **enhedshåndtering**.
    2. Vælg Windows 10 eller Windows 11 som operativsystem.
    3. I feltet **Installationsmetode** skal du vælge **Lokalt script**.
    4. Klik **på Download** pakke, og gem .zip fil.

2. Udtræk indholdet af konfigurationspakken til en placering på den enhed, du vil onboarde (f.eks. Skrivebordet). Du skal have en fil med *navnet WindowsDefenderATPLocalOnboardingScript.cmd*.

3. Åbn en kommandoprompt med administrator på enheden, og kør scriptet:
   1. Gå til **Start,** og skriv **cmd**.
   2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

    :::image type="content" source="images/run-as-admin.png" alt-text="Vinduets menuen Start peger på Kør som administrator" lightbox="images/run-as-admin.png":::

4.  Skriv placeringen af scriptfilen. Hvis du har kopieret filen til skrivebordet, skal du skrive: *%userprofile%\Desktop\WindowsDefenderATPLocalOnboardingScript.cmd*

5.  Tryk på **Enter,** eller klik på **OK**.

Du kan finde oplysninger om, hvordan du manuelt kan validere, om enheden er kompatibel og korrekt rapporterer sensordata, under [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md).

> [!TIP]
> Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på et nyligt onboardet Microsoft Defender for Endpoint slutpunkt](run-detection-test.md).

## <a name="configure-sample-collection-settings"></a>Konfigurere indstillinger for eksempelsamling

For hver enhed kan du angive en konfigurationsværdi, der angiver, om der kan indsamles eksempler fra enheden, når der foretages en anmodning via Microsoft 365 Defender om at sende en fil til dybdegående analyse.

Du kan manuelt konfigurere eksempelindstillingen for deling på enheden ved hjælp af *regedit* eller ved at oprette og køre en *.reg-fil* .

Konfigurationen angives via følgende registreringsdatabasenøglepost:

```console
Path: "HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection"
Name: "AllowSampleCollection"
Value: 0 or 1
```

Where Name type is a D-WORD. De mulige værdier er:

- 0 – tillader ikke eksempeldeling fra denne enhed
- 1 – tillader deling af alle filtyper fra denne enhed

Standardværdien i tilfælde af, at registreringsdatabasenøglen ikke findes, er 1.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Kør en registreringstest for at bekræfte onboarding

Når du har onboardet enheden, kan du vælge at køre en registreringstest for at bekræfte, at enheden er korrekt onboardet til tjenesten. Få mere at vide under [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md).

## <a name="offboard-devices-using-a-local-script"></a>Offboard-enheder, der bruger et lokalt script

Af sikkerhedsmæssige årsager udløber den pakke, der blev brugt til Offboard-enheder, 30 dage efter den dato, den blev downloadet. Udløbne offboarding-pakker, der sendes til en enhed, afvises. Når du henter en offboarding-pakke, får du besked om udløbsdatoen for pakkerne, og den vil også være inkluderet i pakkenavnet.

> [!NOTE]
> Onboarding- og offboarding-politikker må ikke installeres på den samme enhed på samme tid, da dette ellers vil medføre uforudsete fejl.

1. Hent offboarding-pakken <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>:
    1. I navigationsruden skal du **vælge Indstillinger** \> **Endpoints** \> **Device management** \> **Offboarding**.
    2. Vælg Windows 10 eller Windows 11 som operativsystem.
    3. I feltet **Installationsmetode** skal du vælge **Lokalt script**.
    4. Klik **på Download** pakke, og gem .zip fil.

2. Udtræk indholdet af .zip til en delt, skrivebeskyttet placering, der kan åbnes af enhederne. Du skal have en fil med *WindowsDefenderATPOffboardingScript_valid_until_YYYY-DD.cmd-mm*.

3. Åbn en kommandoprompt med administrator på enheden, og kør scriptet:
   1. Gå til **Start,** og skriv **cmd**.
   2. Højreklik på **Kommandoprompt,** og **vælg Kør som administrator**.

      :::image type="content" source="images/run-as-admin.png" alt-text="Den Windows menuen Start peger på indstillingen Kør som administrator" lightbox="images/run-as-admin.png":::

4. Skriv placeringen af scriptfilen. Hvis du har kopieret filen til skrivebordet, skal du skrive: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-DD.cmd*

5. Tryk på **Enter,** eller klik på **OK**.

> [!IMPORTANT]
> Offboarding får enheden til at holde op med at sende sensordata til portalen, men data fra enheden, herunder reference til eventuelle beskeder, enheden har haft, bevares i op til seks måneder.

## <a name="monitor-device-configuration"></a>Overvåg enhedskonfiguration

Du kan følge de forskellige bekræftelsestrin i Fejlfinding [af onboardingproblemer](troubleshoot-onboarding.md) for at bekræfte, at scriptet blev fuldført, og at agenten kører.

Overvågning kan også udføres direkte på portalen eller ved hjælp af de forskellige installationsværktøjer.

### <a name="monitor-devices-using-the-portal"></a>Overvåg enheder ved hjælp af portalen

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.
2. Klik **på Lager enheder**.
3. Kontrollér, at enheder vises.

## <a name="related-topics"></a>Relaterede emner
- [Onboard Windows enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
- [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Configuration Manager](configure-endpoints-sccm.md)
- [Onboard Windows-enheder ved hjælp af mobile Enhedshåndtering værktøjer](configure-endpoints-mdm.md)
- [Onboard ikke-permanente VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
- [Kør en registreringstest på en nyligt onboardet Microsoft Defender for Endpoint enhed](run-detection-test.md)
- [Fejlfinding Microsoft Defender for Endpoint onboardingproblemer](troubleshoot-onboarding.md)
