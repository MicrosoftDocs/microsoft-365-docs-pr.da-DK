---
title: Slå skybeskyttelse til i Microsoft Defender Antivirus
description: Slå skybeskyttelse til for at drage fordel af hurtige og avancerede beskyttelsesfunktioner.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, cloud, blok ved første øjekast
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.date: 02/03/2022
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 38bd804d40c3d5f84e80585f86d906c6a645a668
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416688"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Slå skybeskyttelse til i Microsoft Defender Antivirus

**Gælder for:**

- Microsoft Defender Antivirus
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

**Platforme**
- Windows

[Cloudbeskyttelse i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md) leverer nøjagtig beskyttelse i realtid og intelligent beskyttelse. Cloudbeskyttelse skal som standard være aktiveret. Du kan dog konfigurere cloudbeskyttelse, så den passer til organisationens behov.

## <a name="methods-to-configure-cloud-protection"></a>Metoder til konfiguration af skybeskyttelse

Du kan slå Microsoft Defender Antivirus cloudbeskyttelse til eller fra ved hjælp af en af flere metoder:

- Microsoft Endpoint Manager, som omfatter Microsoft Intune og Configuration Manager
- Gruppepolitik
- PowerShell-cmdlet'er

Du kan også slå skybeskyttelse til eller fra på individuelle slutpunkter ved hjælp af appen Windows Sikkerhed. 

Du kan finde flere oplysninger om de specifikke krav til netværksforbindelsen for at sikre, at dine slutpunkter kan oprette forbindelse til cloudbeskyttelsestjenesten, under [Konfigurer og valider netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> I Windows 10 og Windows 11 er der ingen forskel mellem de **grundlæggende** og **avancerede** rapporteringsindstillinger, der er beskrevet i denne artikel. Dette er en ældre skelnen, og hvis du vælger en af disse indstillinger, resulterer det i det samme niveau af skybeskyttelse. Der er ingen forskel i typen eller mængden af oplysninger, der deles. Du kan finde flere oplysninger om, hvad vi indsamler, i [Microsofts erklæring om beskyttelse af personlige oplysninger](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Brug Intune til at aktivere skybeskyttelse

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Enhedskonfiguration > Profiler** i ruden **Hjem**.

3. Vælg den profiltype **for enhedsbegrænsninger** , du vil konfigurere. Hvis du har brug for at oprette en ny profiltype **for enhedsbegrænsninger**, skal du se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure).

4. Vælg **Konfigurationsindstillinger for egenskaber** \> **: Rediger** \> **Microsoft Defender Antivirus**.

5. Vælg **Aktivér** på parameteren **Skybaseret beskyttelse**.

6. På rullelisten **Spørg brugere før eksempelafsendelse** skal du vælge **Send alle data automatisk**.

Du kan få flere oplysninger om Intune enhedsprofiler, herunder hvordan du opretter og konfigurerer deres indstillinger, under [Hvad er Microsoft Intune enhedsprofiler?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Brug Microsoft Endpoint Manager til at aktivere skybeskyttelse

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint security** \> **Antivirus**.

3. Vælg en antivirusprofil. (Hvis du endnu ikke har en profil, eller hvis du vil oprette en ny profil, skal du se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure).

4. Vælg **Egenskaber**. Vælg derefter **Rediger** ud for **Konfigurationsindstillinger**.

5. Udvid **Cloud-beskyttelse**, og vælg derefter en af følgende på listen **Cloud-leveret beskyttelsesniveau** :
   - **Høj**: Anvender et stærkt registreringsniveau.
   - **High plus**: Bruger det **høje** niveau og anvender flere beskyttelsesforanstaltninger (kan påvirke klientens ydeevne).
   - **Nultolerance**: Blokerer alle ukendte eksekverbare filer.

6. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

Du kan få flere oplysninger om konfiguration af Microsoft Endpoint Configuration Manager under [Sådan opretter og installerer du antimalwarepolitikker: Cloud-protection Service](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Brug Gruppepolitik til at aktivere cloudbeskyttelse

1. Åbn [administrationskonsollen for Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) på din Gruppepolitik-administrationsenhed, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **Gruppepolitik Management Editor** skal du gå til **Computerkonfiguration**.

3. Vælg **Administrative skabeloner**.

4. Udvid træet for at **Windows komponenter** >  **Microsoft Defender Antivirus > KORT**

    > [!NOTE]
    > KORTindstillinger svarer til skybaseret beskyttelse.

5. Dobbeltklik på **Deltag i Microsoft MAPS**. Sørg for, at indstillingen er slået til, og angiv den til **Grundlæggende KORT** eller **Avancerede KORT**. Vælg **OK**.

    Du kan vælge at sende grundlæggende eller yderligere oplysninger om registreret software:

    - Grundlæggende KORT: Grundlæggende medlemskab sender grundlæggende oplysninger til Microsoft om malware og potentielt uønsket software, der er registreret på din enhed. Oplysningerne omfatter, hvor softwaren kom fra (f.eks. URL-adresser og delvise stier), de handlinger, der blev udført for at løse truslen, og om handlingerne lykkedes.

    - Avancerede KORT: Ud over grundlæggende oplysninger sender avanceret medlemskab detaljerede oplysninger om malware og potentielt uønsket software, herunder den fulde sti til softwaren, og detaljerede oplysninger om, hvordan softwaren har påvirket din enhed.

6. Dobbeltklik på **Send fileksempler, når der kræves yderligere analyse**. Sørg for, at den første indstilling er angivet til **Aktiveret** , og at de andre indstillinger er angivet til enten:

   - **Send sikre eksempler** (1)
   - **Send alle eksempler** (3)

   >[!NOTE]
   > Indstillingen **Send sikre eksempler** (1) betyder, at de fleste eksempler sendes automatisk. Filer, der sandsynligvis indeholder personlige oplysninger, bliver stadig bedt om og kræver yderligere bekræftelse.
   > Hvis du angiver indstillingen til **Spørg altid** (0), sænkes beskyttelsestilstanden for enheden. Hvis du angiver den til **Send aldrig** (2), betyder det, at funktionen [Blok ved første øjekast](configure-block-at-first-sight-microsoft-defender-antivirus.md) i Microsoft Defender for Endpoint ikke virker.

7. Vælg **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Brug PowerShell-cmdlet'er til at aktivere cloudbeskyttelse

Følgende cmdlet'er kan aktivere skybeskyttelse:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Du kan få flere oplysninger om, hvordan du bruger PowerShell sammen med Microsoft Defender Antivirus i [Brug PowerShell-cmdlet'er til at konfigurere og køre Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md) og [Microsoft Defender Antivirus cmdlet'er](/powershell/module/defender/). [Politik-CSP – Defender](/windows/client-management/mdm/policy-csp-defender) indeholder også flere oplysninger specifikt om [-SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Du kan angive **-SubmitSamplesConsent** til `SendSafeSamples` (standardindstillingen, den anbefalede indstilling), `NeverSend`eller `AlwaysPrompt`. Indstillingen `SendSafeSamples` betyder, at de fleste eksempler sendes automatisk. Filer, der sandsynligvis indeholder personlige oplysninger, vil resultere i en prompt om at fortsætte og kræver bekræftelse.
> Indstillingerne `NeverSend` og `AlwaysPrompt` sænker enhedens beskyttelsesniveau. Desuden betyder indstillingen`NeverSend`, at funktionen [Blok ved første øjekast](configure-block-at-first-sight-microsoft-defender-antivirus.md) i Microsoft Defender for Endpoint ikke virker.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Brug WMI (Windows Management Instruction) til at aktivere cloudbeskyttelse

Brug [metoden **Set** for klassen **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) til følgende egenskaber:

```WMI
MAPSReporting
SubmitSamplesConsent
```

Du kan få flere oplysninger om tilladte parametre [under Windows Defender WMIv2 API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Slå cloudbeskyttelse til for individuelle klienter med Windows Sikkerhed-appen

> [!NOTE]
> Hvis indstillingen **Konfigurer lokal indstilling tilsidesætter rapportering af Microsoft MAPS** Gruppepolitik er angivet til **Deaktiveret**, er den **skybaserede beskyttelsesindstilling** i Windows Indstillinger nedtonet og utilgængelig. Ændringer, der foretages via et Gruppepolitik objekt, skal først installeres på individuelle slutpunkter, før indstillingen opdateres i Windows Indstillinger.

1. Åbn appen Windows Sikkerhed ved at vælge skjoldikonet på proceslinjen eller ved at søge i menuen Start efter **Windows Sikkerhed**.

2. Vælg feltet **Virus & trusselsbeskyttelse** (eller skjoldikonet på menulinjen til venstre), og vælg derefter **Indstillinger for virus & trusselsbeskyttelse** under **Administrer indstillinger**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Indstillingerne for beskyttelse mod virus & trusler" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Bekræft, at **cloudbaseret beskyttelse** og **automatisk indsendelse af eksempel** er **slået til.**

   > [!NOTE]
   > Hvis den automatiske indsendelse af eksempler er konfigureret med Gruppepolitik er indstillingen nedtonet og utilgængelig.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

- [Brug Microsoft Cloud Protection i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)

- [Sådan opretter og installerer du antimalwarepolitikker: Cloud-beskyttelsestjeneste](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Brug PowerShell-cmdlet'er til at administrere Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)
