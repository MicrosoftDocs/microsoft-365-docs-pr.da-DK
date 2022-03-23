---
title: Angiv beskyttelsesniveauet for skyen for Microsoft Defender Antivirus
description: Angiv dit niveau af skybeskyttelse til Microsoft Defender Antivirus.
keywords: Microsoft Defender Antivirus, antimalware, sikkerhed, defender, sky, aggressiveness, beskyttelsesniveau
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
ms.openlocfilehash: 4723b84e285e508e33ca4b54a1897bbed036a897
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/03/2021
ms.locfileid: "63592168"
---
# <a name="specify-the-cloud-protection-level"></a>Angive skybeskyttelsesniveauet

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Antivirus

Skybeskyttelse arbejder sammen med Microsoft Defender Antivirus at levere beskyttelse til dine slutpunkter meget hurtigere end via traditionelle sikkerhedsintelligensopdateringer. Du kan konfigurere dit niveau af skybeskyttelse ved hjælp af Microsoft Endpoint Manager (anbefales) eller Gruppepolitik.

> [!NOTE]
> Hvis du **vælger Høj**, **Høj +** eller **Nultolerance** , kan det medføre, at nogle legitime filer bliver registreret. Hvis det sker, kan du fjerne blokeringen af den registrerede fil eller tvist, som registreringen Microsoft 365 Defender-portalen.

## <a name="use-microsoft-endpoint-manager-to-specify-the-level-of-cloud-protection"></a>Brug Microsoft Endpoint Manager til at angive niveauet for skybeskyttelse

1. Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), og log på.

2. Vælg **Endpoint security** \> **Antivirus**.

3. Vælg en antivirusprofil. Hvis du endnu ikke har en profil, eller hvis du vil oprette en ny profil, skal du se Konfigurer indstillinger for enhedsbegrænsning [i Microsoft Intune](/intune/device-restrictions-configure).

4. Vælg **Egenskaber**. Derefter skal du ud **for Konfigurationsindstillinger** vælge **Rediger**.

5. **Udvid Skybeskyttelse**, og vælg **derefter et af følgende** på listen Cloud-leveret beskyttelsesniveau:

    - **Ikke konfigureret**: Standardtilstand.
    - **Høj**: Anvender et stærkt registreringsniveau.
    - **Høj plus**: Bruger det **høje niveau** og anvender ekstra beskyttelse (kan påvirke klientens ydeevne).
    - **Nultolerance**: Blokerer alle ukendte eksekverbare værdier.

6. Vælg **Gennemse + gem**, og vælg derefter **Gem**.

> [!TIP]
> Har du brug for hjælp? Se følgende ressourcer:
>
> - [Konfigurer Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-configure)
> - [Tilføj indstillinger for slutpunktsbeskyttelse i Intune](/mem/intune/protect/endpoint-protection-configure)

## <a name="use-group-policy-to-specify-the-level-of-cloud-protection"></a>Brug Gruppepolitik til at angive niveauet for skybeskyttelse

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik administrationskonsollen](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg derefter **Rediger**.

3. I Gruppepolitik **skal du gå** til **Administrative skabeloner til computerkonfiguration**\>.

4. Udvid træet til **Windows Components** \> **Microsoft Defender Antivirus** \> **MpEngine**.

5. Dobbeltklik på indstillingen Vælg **skybeskyttelsesniveau, og** angiv den til **Aktiveret**. Vælg beskyttelsesniveauet:

    - **Ikke konfigureret**: Standardtilstand.
    - **Standardblokeringsniveauet** giver registrering af stærke filer uden at øge risikoen for at registrere legitime filer.
    - **Moderat blokeringsniveau giver** kun moderat ved registreringer med høj sikkerhed
    - **Højt blokeringsniveau** anvender et højt registreringsniveau under optimering af klientens ydeevne (men kan også give dig større risiko for falske positive).
    - **Højt niveau af blokering anvender** ekstra beskyttelse målinger (kan påvirke klientens ydeevne og øge risikoen for falske positive).
    - **Blokeringsniveauet Nultolerance** blokerer alle ukendte eksekverbare værdier.

6. Vælg **OK**.

7. Installér den opdaterede Gruppepolitik-objekt. Se [Gruppepolitik administrationskonsol](/windows/win32/srvnodes/group-policy)

> [!TIP]
> Bruger du Gruppepolitik lokale objekter? Se, hvordan de oversættes i skyen. [Analysér dine lokale gruppepolitikobjekter ved hjælp Gruppepolitik analyser i Microsoft Endpoint Manager – forhåndsvisning](/mem/intune/configuration/group-policy-analytics).
  
## <a name="see-also"></a>Se også

[Derfor skal skybeskyttelse være aktiveret for Microsoft Defender Antivirus](why-cloud-protection-should-be-on-mdav.md)
