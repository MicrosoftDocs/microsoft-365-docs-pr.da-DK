---
title: Angiv skybeskyttelsesniveauet for Microsoft Defender Antivirus
description: Angiv dit niveau af skybeskyttelse for Microsoft Defender Antivirus.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, cloud, aggressivitet, beskyttelsesniveau
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.date: 08/26/2021
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 1f71e5cc2a944ce409a19b6493bda1b40747a066
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417474"
---
# <a name="specify-the-cloud-protection-level"></a>Angive skybeskyttelsesniveauet

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Cloudbeskyttelse arbejder sammen med Microsoft Defender Antivirus om at levere beskyttelse til dine slutpunkter meget hurtigere end via traditionelle sikkerhedsintelligensopdateringer. Du kan konfigurere dit niveau af skybeskyttelse ved hjælp af Microsoft Endpoint Manager (anbefales) eller Gruppepolitik.

> [!NOTE]
> Hvis du vælger **Høj**, **Høj +** eller **Nul-tolerance** , kan det medføre, at nogle legitime filer registreres. Hvis det sker, kan du fjerne blokeringen af den registrerede fil eller bestride registreringen på Microsoft 365 Defender-portalen.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Brug Microsoft Endpoint Manager til at angive niveauet af skybeskyttelse

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint security** \> **Antivirus**.

3. Vælg en antivirusprofil. (Hvis du endnu ikke har en profil, eller hvis du vil oprette en ny profil, skal du se [Konfigurer indstillinger for enhedsbegrænsning i Microsoft Intune](/intune/device-restrictions-configure).

4. Vælg **Egenskaber**. Vælg derefter **Rediger** ud for **Konfigurationsindstillinger**.

5. Udvid **Cloud-beskyttelse**, og vælg derefter en af følgende på listen **Cloud-leveret beskyttelsesniveau** :

    - **Ikke konfigureret**: Standardtilstand.
    - **Høj**: Anvender et stærkt registreringsniveau.
    - **High plus**: Bruger det **høje** niveau og anvender ekstra beskyttelsesforanstaltninger (kan påvirke klientens ydeevne).
    - **Nultolerance**: Blokerer alle ukendte eksekverbare filer.

6. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

> [!TIP]
> Har du brug for hjælp? Se følgende ressourcer:
>
> - [Konfigurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Tilføj beskyttelsesindstillinger for slutpunkter i Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Brug Gruppepolitik til at angive niveauet af skybeskyttelse

1. Åbn [administrationskonsollen Gruppepolitik Gruppepolitik](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** \> **Administrative skabeloner**.

4. Udvid træet for at **Windows Komponenter** \> **Microsoft Defender Antivirus** \> **MpEngine**.

5. Dobbeltklik på indstillingen **Vælg skybeskyttelsesniveau** , og angiv den til **Aktiveret**. Vælg beskyttelsesniveauet:

    - **Ikke konfigureret**: Standardtilstand.
    - **Standardblokeringsniveauet** giver stærk registrering uden at øge risikoen for registrering af legitime filer.
    - **Moderat blokeringsniveau** giver kun moderat for registreringer med høj genkendelsessikkerhed
    - **Et højt blokeringsniveau** anvender et stærkt registreringsniveau, samtidig med at klientens ydeevne optimeres (men det kan også give dig større chance for falske positiver).
    - **Højt + blokerende niveau** anvender ekstra beskyttelsesforanstaltninger (kan påvirke klientens ydeevne og øge din chance for falske positiver).
    - **Nultolerance blokerer niveau** blokerer alle ukendte eksekverbare filer.

6. Vælg **OK**.

7. Installer det opdaterede Gruppepolitik objekt. Se [administrationskonsollen Gruppepolitik](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Bruger du Gruppepolitik objekter i det lokale miljø? Se, hvordan de oversættes i cloudmiljøet. [Analysér dine gruppepolitikobjekter i det lokale miljø ved hjælp af Gruppepolitik analyser i Microsoft Endpoint Manager – prøveversion](/mem/intune/configuration/group-policy-analytics).

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

[Hvorfor skal cloudbeskyttelse aktiveres for Microsoft Defender Antivirus](why-cloud-protection-should-be-on-mdav.md)
