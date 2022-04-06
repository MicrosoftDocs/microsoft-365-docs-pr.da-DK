---
title: Opret en brugerdefineret gradvis udrulningsproces for Microsoft Defender-opdateringer
description: Lær at bruge understøttede værktøjer til at oprette en brugerdefineret gradvis udrulningsproces for opdateringer
keywords: opdateringsværktøjer, gpo, intune, mdm, microsoft endpoint manager, politik, powershell
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
ms.openlocfilehash: 4261e32721da86233a0a929a435c318904d6ac12
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606578"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Opret en brugerdefineret gradvis udrulningsproces for Microsoft Defender-opdateringer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Denne funktionalitet kræver Microsoft Defender Antivirus version 4.18.2106.X eller nyere.

Hvis du vil oprette din egen brugerdefinerede gradvise implementeringsproces til Defender-opdateringer, kan du bruge Gruppepolitik, Microsoft Endpoint Manager og PowerShell.

I følgende tabel vises de tilgængelige gruppepolitikindstillinger til konfiguration af opdateringskanaler:

<br>

****

|Indstilling af titel|Beskrivelse|Placering|
|---|---|---|
|Vælg gradvis udrulningskanal for månedlige Microsoft Defender-platforme|Aktivér denne politik for at angive, hvornår enheder modtager Microsoft Defender-platformopdateringer under den månedlige gradvise udrulning. <p> Betakanal: Enheder, der er indstillet til denne kanal, er de første til at modtage nye opdateringer. Vælg Beta-kanal for at deltage i identificering og rapportering af problemer med Microsoft. Enheder i Windows Insider Program abonneres på denne kanal som standard. Kun til brug i (manuelle) testmiljøer og et begrænset antal enheder. <p> Aktuel kanal (forhåndsvisning): Enheder, der er indstillet til denne kanal, vil blive tilbudt opdateringer tidligst i løbet af den månedlige gradvise udgivelsescyklus. Foreslået til præ-produktions-/valideringsmiljøer. <p> Aktuel kanal (faseret): Enheder tilbydes opdateringer efter den månedlige gradvise udgivelsescyklus. Foreslået til at gælde for en lille, repræsentativ del af produktions populationen (~10 %). <p> Aktuel kanal (bred): Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået til at gælde for et bredt sæt enheder i produktionsbestanden (~10-100 %). <p> Kritisk– Tidsforsinkelse: Enheder tilbydes opdateringer med en 48-timers forsinkelse. Kun foreslået til kritiske miljøer. <p>Hvis du deaktiverer eller ikke konfigurerer denne politik, holder enheden sig automatisk opdateret i løbet af den gradvise udgivelsescyklus. Passer til de fleste enheder.|Windows Components\Microsoft Defender Antivirus|
|Vælg gradvis udrulningskanal for månedlige Microsoft Defender-programmer|Aktivér denne politik for at angive, hvornår enheder modtager Microsoft Defender Engine-opdateringer under den månedlige gradvise udrulning. <p> Betakanal: Enheder, der er indstillet til denne kanal, er de første til at modtage nye opdateringer. Vælg Beta-kanal for at deltage i identificering og rapportering af problemer med Microsoft. Enheder i Windows Insider Program abonneres på denne kanal som standard. Kun til brug i (manuelle) testmiljøer og et begrænset antal enheder. <p> Aktuel kanal (forhåndsvisning): Enheder, der er indstillet til denne kanal, vil blive tilbudt opdateringer tidligst i løbet af den månedlige gradvise udgivelsescyklus. Foreslået til præ-produktions-/valideringsmiljøer. <p> Aktuel kanal (faseret): Enheder tilbydes opdateringer efter den månedlige gradvise udgivelsescyklus. Foreslået til at gælde for en lille, repræsentativ del af produktions populationen (~10 %). <p> Aktuel kanal (bred): Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået til at gælde for et bredt sæt enheder i produktionsbestanden (~10-100 %). <p> Kritisk– Tidsforsinkelse: Enheder tilbydes opdateringer med en 48-timers forsinkelse. Kun foreslået til kritiske miljøer.<p> Hvis du deaktiverer eller ikke konfigurerer denne politik, holder enheden sig automatisk opdateret i løbet af den gradvise udgivelsescyklus. Passer til de fleste enheder.|Windows Components\Microsoft Defender Antivirus|
|Vælg en gradvis udrulningskanal for daglige sikkerhedsopdateringer til Microsoft Defender|Aktivér denne politik for at angive, hvornår enheder modtager Microsoft Defender security intelligence-opdateringer under den daglige gradvise udrulning. <p> Aktuel kanal (faseret): Enheder tilbydes opdateringer efter udgivelsescyklussen. Foreslået til at gælde for en lille, repræsentativ del af produktions populationen (~10 %). <p> Aktuel kanal (bred): Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået til at gælde for et bredt sæt enheder i produktionsbestanden (~10-100 %). <p>  Hvis du deaktiverer eller ikke konfigurerer denne politik, holder enheden automatisk opdateret i løbet af den daglige udgivelsescyklus. Passer til de fleste enheder.|Windows Components\Microsoft Defender Antivirus|
|Deaktiver gradvis udrulning af Microsoft Defender-opdateringer|Aktivér denne politik for at deaktivere gradvis udrulning af Defender-opdateringer. <p> Aktuel kanal (bred): Enheder, der er indstillet til denne kanal, tilbydes opdateringer sidste gang i den gradvise udgivelsescyklus. Bedst til datacenter maskiner, der kun modtager begrænsede opdateringer. <p> Bemærk! Denne indstilling gælder både månedligt og dagligt Defender-opdateringer og tilsidesætter tidligere konfigurerede kanalvalg for platform- og programopdateringer. <p> Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden i Aktuel kanal (standard), medmindre det er angivet på andre måder i bestemte kanaler til platform- og programopdateringer. Hold dig opdateret automatisk under den gradvise udgivelsescyklus. Passer til de fleste enheder.|Windows Components\Microsoft Defender Antivirus|
|

## <a name="group-policy"></a>Gruppepolitik

> [!NOTE]
> En opdateret Defender ADMX-skabelon udgives sammen med 21H2-udgivelsen af Windows 10. En ikke-lokaliseret version kan downloades på https://github.com/microsoft/defender-updatecontrols.

Du kan bruge [Gruppepolitik](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) til at konfigurere og Microsoft Defender Antivirus på dine slutpunkter.

Generelt kan du bruge følgende fremgangsmåde til at konfigurere eller ændre Microsoft Defender Antivirus gruppepolitikindstillinger:

1. Åbn Gruppepolitik Management **Console på** Gruppepolitik Administrationsmaskine, højreklik på det **Gruppepolitik-objekt** , du vil konfigurere, og klik på **Rediger**.

2. Når du bruger Gruppepolitik, skal du gå til **Computerkonfiguration**.

3. Klik **på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter > Microsoft Defender Antivirus**.

5. Udvid den sektion (kaldet Placering  i tabellen i dette emne), der indeholder den indstilling, du vil konfigurere, dobbeltklikke på indstillingen for at åbne den og foretage konfigurationsændringer.

6. [Installér det opdaterede gruppepolitikobjekt, som du normalt gør](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Følg vejledningen i nedenstående link for at oprette en brugerdefineret politik i Intune:

[Tilføj brugerdefinerede indstillinger for Windows 10-enheder Microsoft Intune – Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

Du kan finde flere oplysninger om den Defender CSP, der bruges til den gradvise udrulningsproces, [under Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

`Set-MpPreference` Brug cmdlet'en til at konfigurere udrulning af de gradvise opdateringer.

Brug følgende parametre:

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Eksempel:

Bruges `Set-MpPreference -PlatformUpdatesChannel Beta` til at konfigurere platformsopdateringer til at modtage fra Beta-kanalen.

Du kan finde flere oplysninger om parametrene, og hvordan du konfigurerer dem, [under Set-MpPreference (Microsoft Defender Antivirus)| Microsoft Docs](/powershell/module/defender/set-mppreference).
