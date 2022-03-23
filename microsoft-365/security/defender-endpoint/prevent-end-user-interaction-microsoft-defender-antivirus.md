---
title: Skjule Microsoft Defender Antivirus brugergrænsefladen
description: Du kan skjule feltet virus- og trusselsbeskyttelse i Windows Sikkerhed app.
keywords: låsning af brugergrænseflade, hovedløs tilstand, skjul app, skjul indstillinger, skjul grænseflade
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: d54d8ecf2d0c365168ae636cbe85ef1da9cfb6b1
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63593829"
---
# <a name="prevent-users-from-seeing-or-interacting-with-the-microsoft-defender-antivirus-user-interface"></a>Forhindre brugere i at se eller arbejde med Microsoft Defender Antivirus brugergrænsefladen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Du kan bruge Gruppepolitik at forhindre brugere på slutpunkter i at se den Microsoft Defender Antivirus grænseflade. Du kan også forhindre dem i at sætte scanninger på pause.

## <a name="hide-the-microsoft-defender-antivirus-interface"></a>Skjule Microsoft Defender Antivirus brugergrænsefladen

I Windows 10 version 1703 skjuler du grænsefladen Microsoft Defender Antivirus-meddelelser og forhindrer flisen Virus &-trusselsbeskyttelse i at blive vist i Windows Sikkerhed-appen.

Med indstillingen angivet til **Aktiveret**:

:::image type="content" source="../../media/wdav-headless-mode-off-1703.png" alt-text="Skærmbillede af Windows Sikkerhed uden skjoldikonet og sektionerne for virus- og trusselsbeskyttelse.":::

Med indstillingen indstillet til **Deaktiveret** eller ikke konfigureret:

:::image type="content" source="../../media/wdav-headless-mode-1703.png" alt-text="Skærmbillede af Windows Sikkerhed med skjoldikon og trusselsbeskyttelsessnit.":::

> [!NOTE]
> Hvis du skjuler grænsefladen, forhindres Microsoft Defender Antivirus meddelelser i at blive vist på slutpunktet. Microsoft Defender for Endpoint-meddelelser vises stadig. Du kan også konfigurere de [meddelelser, der vises på slutpunkter, individuelt](configure-notifications-microsoft-defender-antivirus.md)

I tidligere versioner Windows 10 skjules klientgrænseflade Windows Defender n under indstillingen. Hvis brugeren forsøger at åbne den, modtager brugeren en advarsel, hvor der står "Din systemadministrator har begrænset adgang til denne app".

:::image type="content" source="../../media/wdav-headless-mode-1607.png" alt-text="Advarselsmeddelelse, når tilstanden for forhovedet er aktiveret i Windows 10 versioner, der er tidligere end 1703":::

## <a name="use-group-policy-to-hide-the-microsoft-defender-av-interface-from-users"></a>Brug Gruppepolitik til at skjule Microsoft Defender AV-grænsefladen for brugerne

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. Når du bruger **Gruppepolitik, skal du** gå til **Computerkonfiguration**.

3. Klik **på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter > Microsoft Defender Antivirus > klientgrænseflade**.

5. Dobbeltklik på indstillingen **Aktivér tilstand for brugergrænseflade uden sidehoved** , og angiv indstillingen til **Aktiveret**. Klik på **OK**.

Se [Forhindre brugere i at redigere politikindstillinger](configure-local-policy-overrides-microsoft-defender-antivirus.md) lokalt for at få flere indstillinger til at forhindre brugere i at redigere beskyttelse på deres pc'er.

## <a name="prevent-users-from-pausing-a-scan"></a>Forhindre brugere i at sætte en scanning på pause

Du kan forhindre brugere i at afbryde scanninger, hvilket kan være nyttigt for at sikre, at planlagte scanninger eller scanninger efter behov ikke afbrydes af brugerne.

> [!NOTE]
> Denne indstilling understøttes ikke på Windows 10.

### <a name="use-group-policy-to-prevent-users-from-pausing-a-scan"></a>Brug Gruppepolitik at forhindre brugere i at sætte en scanning på pause

1. På din Gruppepolitik administrationsmaskine skal du åbne [Gruppepolitik Administrationskonsol](/previous-versions/windows/desktop/gpmc/group-policy-management-console-portal), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og klikke på **Rediger**.

2. Når du bruger **Gruppepolitik, skal du** gå til **Computerkonfiguration**.

3. Klik **på Administrative skabeloner**.

4. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Scanning**.

5. Dobbeltklik på indstillingen Tillad **brugere at afbryde scanningen** midlertidigt, og angiv indstillingen til **Deaktiveret**. Klik på **OK**.

## <a name="related-articles"></a>Relaterede artikler

- [Konfigurere de meddelelser, der vises på slutpunkter](configure-notifications-microsoft-defender-antivirus.md)
- [Konfigurere slutbrugerinteraktion med Microsoft Defender Antivirus](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
