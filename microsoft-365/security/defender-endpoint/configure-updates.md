---
title: Opret en brugerdefineret gradvis udrulningsproces for Microsoft Defender-opdateringer
description: Få mere at vide om, hvordan du bruger understøttede værktøjer til at oprette en brugerdefineret gradvis udrulningsproces for opdateringer
keywords: update tools, gpo, intune, mdm, microsoft endpoint manager, policy, powershell
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4a963172e69b61a7cb33486132630e0d56d0420b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788540"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Opret en brugerdefineret gradvis udrulningsproces for Microsoft Defender-opdateringer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> [!NOTE]
> Denne funktionalitet kræver Microsoft Defender Antivirus version 4.18.2106.X eller nyere.

Hvis du vil oprette din egen brugerdefinerede gradvise udrulningsproces for Defender-opdateringer, kan du bruge Gruppepolitik, Microsoft Endpoint Manager og PowerShell.

I følgende tabel vises de tilgængelige gruppepolitikindstillinger for konfiguration af opdateringskanaler:

<br>

****

|Indstilling af titel|Beskrivelse|Placering|
|---|---|---|
|Vælg gradvis udrulningskanal for månedlig opdatering af Microsoft Defender-platform|Aktivér denne politik for at angive, hvornår enheder modtager Opdateringer til Microsoft Defender-platformen under den månedlige gradvise udrulning. <p> Betakanal: Enheder, der er angivet til denne kanal, er de første til at modtage nye opdateringer. Vælg Beta Channel for at deltage i identificering og rapportering af problemer til Microsoft. Enheder i Windows Insider Program abonneres som standard på denne kanal. Kun til brug i (manuelle) testmiljøer og et begrænset antal enheder. <p> Aktuel kanal (prøveversion): Enheder, der er angivet til denne kanal, tilbydes opdateringer tidligst under den månedlige gradvise udgivelsescyklus. Foreslået til præproduktions-/valideringsmiljøer. <p> Aktuel kanal (faset): Enheder tilbydes opdateringer efter den månedlige gradvise udgivelsescyklus. Foreslået at gælde for en lille, repræsentativ del af din produktionspopulation (~10%). <p> Aktuel kanal (bred): Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået at anvende på et bredt sæt enheder i din produktionspopulation (~10-100%). <p> Kritisk – tidsforsinkelse: Enheder får tilbudt opdateringer med en forsinkelse på 48 timer. Kun foreslået til kritiske miljøer. <p>Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden automatisk opdateret under den gradvise udgivelsescyklus. Egnet til de fleste enheder.|Windows komponenter\Microsoft Defender Antivirus|
|Vælg gradvis udrulningskanal for Microsoft Defender-månedligt program|Aktivér denne politik for at angive, hvornår enheder modtager opdateringer fra Microsoft Defender-programmet under den månedlige gradvise udrulning. <p> Betakanal: Enheder, der er angivet til denne kanal, er de første til at modtage nye opdateringer. Vælg Beta Channel for at deltage i identificering og rapportering af problemer til Microsoft. Enheder i Windows Insider Program abonneres som standard på denne kanal. Kun til brug i (manuelle) testmiljøer og et begrænset antal enheder. <p> Aktuel kanal (prøveversion): Enheder, der er angivet til denne kanal, tilbydes opdateringer tidligst under den månedlige gradvise udgivelsescyklus. Foreslået til præproduktions-/valideringsmiljøer. <p> Aktuel kanal (faset): Enheder tilbydes opdateringer efter den månedlige gradvise udgivelsescyklus. Foreslået at gælde for en lille, repræsentativ del af din produktionspopulation (~10%). <p> Aktuel kanal (bred): Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået at anvende på et bredt sæt enheder i din produktionspopulation (~10-100%). <p> Kritisk – tidsforsinkelse: Enheder får tilbudt opdateringer med en forsinkelse på 48 timer. Kun foreslået til kritiske miljøer.<p> Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden automatisk opdateret under den gradvise udgivelsescyklus. Egnet til de fleste enheder.|Windows komponenter\Microsoft Defender Antivirus|
|Vælg gradvis udrulningskanal for opdateringer til sikkerhedsintelligens i Microsoft Defender|Aktivér denne politik for at angive, hvornår enheder modtager Microsoft Defender Security Intelligence-opdateringer under den daglige gradvise udrulning. <p> Aktuel kanal (i fase): Enheder tilbydes opdateringer efter udgivelsescyklussen. Foreslået at gælde for en lille, repræsentativ del af produktionspopulationen (~10%). <p> Aktuel kanal (bred): Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået at anvende på et bredt sæt enheder i din produktionspopulation (~10-100%). <p>  Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden automatisk opdateret under den daglige udgivelsescyklus. Egnet til de fleste enheder.|Windows komponenter\Microsoft Defender Antivirus|
|Deaktiver gradvis udrulning af Microsoft Defender-opdateringer|Aktivér denne politik for at deaktivere gradvis udrulning af Defender-opdateringer. <p> Aktuel kanal (bred): Enheder, der er angivet til denne kanal, vil blive tilbudt opdateringer sidst under den gradvise udgivelsescyklus. Bedst til datacentermaskiner, der kun modtager begrænsede opdateringer. <p> Bemærk! Denne indstilling gælder for både månedlige og daglige Defender-opdateringer og tilsidesætter alle tidligere konfigurerede kanalvalg for platform- og programopdateringer. <p> Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden i Aktuel kanal (standard), medmindre andet er angivet i specifikke kanaler for platform- og programopdateringer. Hold dig automatisk opdateret under den gradvise udgivelsescyklus. Egnet til de fleste enheder.|Windows komponenter\Microsoft Defender Antivirus|
|

## <a name="group-policy"></a>Gruppepolitik

> [!NOTE]
> Der udgives en opdateret Defender ADMX-skabelon sammen med 21H2-versionen af Windows 10. Du kan hente en ikke-lokaliseret version på https://github.com/microsoft/defender-updatecontrols.

Du kan bruge [Gruppepolitik](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) til at konfigurere og administrere Microsoft Defender Antivirus på dine slutpunkter.

Generelt kan du bruge følgende fremgangsmåde til at konfigurere eller ændre Microsoft Defender Antivirus gruppepolitikindstillinger:

1. Åbn **administrationskonsollen Gruppepolitik Gruppepolitik**, højreklik på det **Gruppepolitik objekt**, du vil konfigurere, og klik på **Rediger**.

2. Ved hjælp af administrationseditoren Gruppepolitik gå til **Computerkonfiguration**.

3. Klik på **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter > Microsoft Defender Antivirus**.

5. Udvid det afsnit (kaldet **Placering** i tabellen i dette emne), der indeholder den indstilling, du vil konfigurere, dobbeltklik på indstillingen for at åbne den, og foretag konfigurationsændringer.

6. [Udrul det opdaterede gruppepolitikobjekt, som du normalt gør](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Følg instruktionerne i nedenstående link for at oprette en brugerdefineret politik i Intune:

[Tilføj brugerdefinerede indstillinger for Windows 10 enheder i Microsoft Intune – Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

Du kan få flere oplysninger om defender-CSP'en, der bruges til gradvis udrulning, under [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

Brug cmdlet'en `Set-MpPreference` til at konfigurere udrulning af gradvise opdateringer.

Brug følgende parametre:

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Eksempel:

Bruges `Set-MpPreference -PlatformUpdatesChannel Beta` til at konfigurere platformopdateringer til at modtage fra betakanalen.

Du kan få flere oplysninger om parametrene, og hvordan du konfigurerer dem, under [Set-MpPreference (Microsoft Defender Antivirus)|Microsoft Docs](/powershell/module/defender/set-mppreference).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [macOS Antivirus politikindstillinger for Microsoft Defender Antivirus til Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)