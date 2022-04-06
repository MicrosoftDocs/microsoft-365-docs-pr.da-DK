---
title: Slå skybeskyttelse til i Microsoft Defender Antivirus
description: Slå skybeskyttelse til for at drage fordel af hurtige og avancerede beskyttelsesfunktioner.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, sky, blok ved første synsviden
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
ms.openlocfilehash: 78f992e20ee0c0c2505777295ca3ba34a5c4ea66
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470631"
---
# <a name="turn-on-cloud-protection-in-microsoft-defender-antivirus"></a>Slå skybeskyttelse til i Microsoft Defender Antivirus

**Gælder for:**

- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

[Skybeskyttelse i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md) leverer nøjagtig, realtid og intelligent beskyttelse. Skybeskyttelse bør være aktiveret som standard. du kan dog konfigurere skybeskyttelse, så den passer til din organisations behov.

## <a name="methods-to-configure-cloud-protection"></a>Metoder til at konfigurere skybeskyttelse

Du kan slå Microsoft Defender Antivirus skybeskyttelse til eller fra ved hjælp af en af flere forskellige metoder:

- Microsoft Endpoint Manager, som omfatter Microsoft Intune og Configuration Manager
- Gruppepolitik
- PowerShell-cmdlet'er

Du kan også slå skybeskyttelse til eller fra for individuelle slutpunkter ved hjælp Windows Sikkerhed appen. 

Du kan finde flere oplysninger om de specifikke krav til netværksforbindelser for at sikre, at dine slutpunkter kan oprette forbindelse til [skybeskyttelsestjenesten under Konfigurere og validere netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md).

> [!NOTE]
> I Windows 10 og Windows 11 er der ingen forskel mellem de grundlæggende **og avancerede rapporteringsmuligheder**, der er  beskrevet i denne artikel. Dette kan skelne mellem ældre og valg af begge indstillinger medfører det samme niveau af skybeskyttelse. Der er ingen forskel på typen eller mængden af oplysninger, der deles. Du kan finde flere oplysninger om, hvad vi indsamler, i [Microsofts erklæring om beskyttelse af personlige oplysninger](https://go.microsoft.com/fwlink/?linkid=521839).

## <a name="use-intune-to-turn-on-cloud-protection"></a>Brug Intune til at aktivere skybeskyttelse

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. I **ruden Hjem** skal du **vælge Enhedskonfiguration > Profiler**.

3. Vælg den **profiltype for** Enhedsbegrænsninger, du vil konfigurere. Hvis du vil oprette en ny **profiltype for Enhedsbegrænsninger**, skal du [se Konfigurer indstillinger for enhedsbegrænsning Microsoft Intune](/intune/device-restrictions-configure).

4. Vælg **Egenskaber** \> **Konfigurationsindstillinger: Rediger** \> **Microsoft Defender Antivirus**.

5. Vælg **Aktivér på cloud-leveret** beskyttelse **.**

6. Vælg Send **alle data automatisk på rullelisten** Spørg brugere før **eksempelindsendelse**.

Du kan finde flere Intune om enhedsprofiler, herunder hvordan du opretter og konfigurerer deres indstillinger, [under Hvad Microsoft Intune på enhedsprofiler?](/intune/device-profiles)

## <a name="use-microsoft-endpoint-manager-to-turn-on-cloud-protection"></a>Brug Microsoft Endpoint Manager til at aktivere skybeskyttelse

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint security** \> **Antivirus**.

3. Vælg en antivirusprofil. Hvis du endnu ikke har en profil, eller hvis du vil oprette en ny profil, skal du se Konfigurer indstillinger for enhedsbegrænsning [i Microsoft Intune](/intune/device-restrictions-configure).

4. Vælg **Egenskaber**. Derefter skal du ud **for Konfigurationsindstillinger** vælge **Rediger**.

5. **Udvid Skybeskyttelse**, og vælg **derefter et af følgende** på listen Cloud-leveret beskyttelsesniveau:
   - **Høj**: Anvender et stærkt registreringsniveau.
   - **Høj plus**: Bruger det **høje niveau** og anvender flere beskyttelseforanstaltninger (kan påvirke klientens ydeevne).
   - **Nultolerance**: Blokerer alle ukendte eksekverbare værdier.

6. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

Du kan finde flere oplysninger om konfiguration Microsoft Endpoint Configuration Manager under Sådan oprettes og [installeres antimalwarepolitikker: Skybeskyttelsestjeneste](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service).

## <a name="use-group-policy-to-turn-on-cloud-protection"></a>Brug Gruppepolitik til at aktivere skybeskyttelse

1. På Gruppepolitik administrationsenhed skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration**.

3. Vælg **Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** >  **Microsoft Defender Antivirus > MAPS**

    > [!NOTE]
    > KORT-indstillinger er lig med skybaseret beskyttelse.

5. Dobbeltklik på Deltag **i Microsoft MAPS**. Sørg for, at indstillingen er aktiveret og indstillet **til Grundlæggende KORT** **eller Avancerede KORT**. Vælg **OK**.

    Du kan vælge at sende grundlæggende eller yderligere oplysninger om registreret software:

    - Grundlæggende KORT: Grundlæggende medlemskab sender grundlæggende oplysninger til Microsoft om malware og potentielt uønsket software, der er registreret på din enhed. Oplysningerne omfatter, hvor softwaren stammer fra (f.eks. URL-adresser og delvise stier), de handlinger, der er foretaget for at løse truslerne, og om handlingerne blev gennemført.

    - Avancerede KORT: Ud over grundlæggende oplysninger sender avanceret medlemskab detaljerede oplysninger om malware og potentielt uønsket software, herunder den fulde sti til softwaren samt detaljerede oplysninger om, hvordan softwaren har påvirket din enhed.

6. Dobbeltklik på Send **fileksempler, når yderligere analyse er påkrævet**. Sørg for, at den første indstilling er angivet til **Aktiveret** , og at de andre indstillinger er indstillet til enten:

   - **Send sikre eksempler** (1)
   - **Send alle eksempler** (3)

   >[!NOTE]
   > Indstillingen **Send sikre eksempler** (1) betyder, at de fleste eksempler sendes automatisk. Filer, der sandsynligvis indeholder personlige oplysninger, vil stadig blive bedt om det og kræver yderligere bekræftelse.
   > Hvis du vælger **Spørg altid** (0), sænkes enhedens beskyttelsestilstand. Hvis du angiver **den til Send** aldrig (2), betyder det, [at](configure-block-at-first-sight-microsoft-defender-antivirus.md) funktionen Bloker ved første syn Microsoft Defender for Endpoint ikke fungerer.

7. Vælg **OK**.

## <a name="use-powershell-cmdlets-to-turn-on-cloud-protection"></a>Brug PowerShell-cmdlet'er til at aktivere skybeskyttelse

Følgende cmdlet'er kan aktivere skybeskyttelse:

```PowerShell
Set-MpPreference -MAPSReporting Advanced
Set-MpPreference -SubmitSamplesConsent SendAllSamples
```

Du kan finde flere oplysninger om, hvordan du bruger PowerShell Microsoft Defender Antivirus i Brug [PowerShell-cmdlet'er](use-powershell-cmdlets-microsoft-defender-antivirus.md) til at konfigurere og køre Microsoft Defender Antivirus [og Microsoft Defender Antivirus-cmdlet'er](/powershell/module/defender/). [Politik-CSP – Defender](/windows/client-management/mdm/policy-csp-defender) har også flere oplysninger specifikt [om -SubmitSamplesConsent](/windows/client-management/mdm/policy-csp-defender#defender-submitsamplesconsent).

> [!IMPORTANT]
> Du kan angive **-SubmitSamplesConsent** til `SendSafeSamples` (standardindstillingen, den anbefalede indstilling) `NeverSend`eller `AlwaysPrompt`. Indstillingen `SendSafeSamples` betyder, at de fleste eksempler sendes automatisk. Filer, der sandsynligvis indeholder personlige oplysninger, medfører, at du bliver bedt om at fortsætte, og det kræver en bekræftelse.
> Og `NeverSend` indstillingerne `AlwaysPrompt` sænker beskyttelsesniveauet på enheden. Desuden betyder `NeverSend` indstillingen, [at funktionen Blok ved første](configure-block-at-first-sight-microsoft-defender-antivirus.md) syn Microsoft Defender for Endpoint ikke fungerer.

## <a name="use-windows-management-instruction-wmi-to-turn-on-cloud-protection"></a>Brug Windows -administrationsvejledning (WMI) til at aktivere skybeskyttelse

Brug [**metoden Angiv** for **MSFT_MpPreference**](/previous-versions/windows/desktop/defender/set-msft-mppreference) til følgende egenskaber:

```WMI
MAPSReporting
SubmitSamplesConsent
```

Du kan finde flere oplysninger om tilladte parametre [under Windows Defender WMIv2-API'er](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="turn-on-cloud-protection-on-individual-clients-with-the-windows-security-app"></a>Aktivere skybeskyttelse på individuelle klienter med Windows Sikkerhed appen

> [!NOTE]
> Hvis indstillingen Konfigurer lokal indstilling til rapportering **af Microsoft MAPS** Gruppepolitik er indstillet til Deaktiveret **, vil** indstillingen for skybaseret beskyttelse i Windows Indstillinger være nedtonet og ikke tilgængelig. Ændringer, der er foretaget via Gruppepolitik-objekt, skal først installeres til individuelle slutpunkter, før indstillingen opdateres Windows Indstillinger.

1. Åbn Windows Sikkerhed-appen ved at vælge skjoldikonet på proceslinjen eller ved at søge i menuen Start efter **Windows Sikkerhed**.

2. Vælg **flisen Virusbeskyttelse &** (eller skjoldikonet på venstre menulinje), og vælg derefter indstillinger for **& mod trusler under Administrer indstillinger**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Indstillingerne for & mod trusler" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. Bekræft **, at skybaseret beskyttelse** **og automatisk indsendelse af eksempler** er slået **Til**.

   > [!NOTE]
   > Hvis der er konfigureret automatisk indsendelse af eksempler Gruppepolitik er indstillingen nedtonet og ikke tilgængelig.

## <a name="see-also"></a>Se også

- [Brug Microsoft Cloud Protection i Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)

- [Sådan oprettes og installeres antimalwarepolitikker: Skybeskyttelsestjeneste](/configmgr/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)

- [Brug PowerShell-cmdlet'er til at administrere Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)
