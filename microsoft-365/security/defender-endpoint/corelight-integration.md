---
title: Aktivér Corelight-integration i Microsoft Defender for Endpoint
description: Aktivér Corelight-integration for at få synlighed, der fokuserer på IoT-/OT-enheder i områder af netværket, hvor MDE ikke er udrullet
keywords: aktivér siem-connector, siem, connector, sikkerhedsoplysninger og -hændelser
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 629d475c160d5836d155ca0374630ad64b0928b4
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372015"
---
# <a name="enable-corelight-data-integration"></a>Aktiver Integration af Corelight-data

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft har indgået partnerskab med [Corelight](https://corelight.com/integrations/iot-security), der er udbyder af branchens førende NDR-platform (Open Network Detection and Response), for at hjælpe dig med at finde IoT-/OT-enheder på tværs af din organisation. Ved hjælp af data, der sendes fra Corelight-netværksapparater, får Microsoft 365 Defender øget synlighed i ikke-administrerede enheders netværksaktiviteter, herunder kommunikation med andre ikke-administrerede enheder eller eksterne netværk.

Når denne datakilde er aktiveret, sendes alle hændelser fra Corelight-netværksapparater til Microsoft 365 Defender. Du kan få vist disse aktiviteter på tidslinjen for ikke-administrerede enheder, som er tilgængelig i oversigten over Microsoft Defender for Endpoint enheder. Du kan finde flere oplysninger under [Enhedsregistrering](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Aktivering af Corelight-integration

Hvis du vil aktivere Corelight-integrationen, skal du udføre følgende trin:

[Trin 1: Slå Corelight til som datakilde](#step-1-turn-on-corelight-as-a-data-source)<br>
[Trin 2: Giv Corelight tilladelse til at sende hændelser til Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Trin 3: Konfigurer corelight-enheden til at sende data til Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Trin 1: Slå Corelight til som datakilde

1. I navigationsruden på portalen [https://security.microsoft.com](https://security.microsoft.com/) skal du vælge **Indstillinger** \> **Datakilder til** **enhedsregistrering**\>.

   :::image type="content" source="images/enable-corelight.png" alt-text="Siden med datakilder på Microsoft 365 Defender-portalen" lightbox="images/enable-corelight.png":::

2. Vælg **Send Corelight-data til M365D,** og vælg **Gem**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Trin 2: Giv Corelight tilladelse til at sende hændelser til Microsoft 365 Defender

> [!NOTE]
> Du skal være global administrator for at give Corelight tilladelse til at få adgang til ressourcer i din organisation.

1. Som global lejeradministrator skal du gå til dette [link](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) for at give tilladelse.
2. Gå til [https://security.microsoft.com](https://security.microsoft.com/) portalen, vælg **Indstillinger** \> **Microsoft 365 Defender**, og notér **lejer-id'et**. Du skal bruge disse oplysninger, når du konfigurerer din Corelight-apparat.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Trin 3: Konfigurer corelight-enheden til at sende data til Microsoft 365 Defender

> [!NOTE]
> Integrationen er tilgængelig i Corelight Sensor software v25 og nyere.
> 
> Du skal bruge internetforbindelse, for at din sensor kan nå både Defender- og Corelight-cloudtjenesterne, for at løsningen kan fungere.

#### <a name="enable-the-integration-in-the-corelight-web-interface"></a>Aktivér integration i Corelight-webgrænsefladen

1. I corelight-webgrænsefladen skal du navigere til **Sensoreksport**\>.

   :::image type="content" source="images/exporttodefender.png" alt-text="Kafka-eksporten" lightbox="images/exporttodefender.png":::

2. Aktivér **Eksportér til Microsoft Defender**.
3. Angiv dit Lejer-id til Microsoft 356 Defender.
4. Du kan eventuelt:
    - angiv **Zeek Logs til Exclude**. Det minimale sæt logge, du skal inkludere, er: dns, conn, files, http, ssl, ssh, x509, snmp, smtp, ftp, sip, dhcp og notice.
    - vælg at oprette et **Microsoft Defender-logfilter**.
5. Vælg **Anvend ændringer**.

#### <a name="enable-the-integration-in-the-corelight-client"></a>Aktivér integrationen i corelight-client

1. Aktivér **Eksportér til Microsoft Defender** ved hjælp af følgende kommando i corelight-client:

    ``` command
    corelight-client configuration update \
    --bro.export.defender.enable True
    ```

2. Angiv dit lejer-id

3. Du kan eventuelt bruge følgende kommando til at udelade bestemte logge eller til at oprette et Microsoft Defender-logfilter. Det minimale sæt logge, du skal inkludere, er: dns, conn, files, http, ssl, ssh, x509, snmp, smtp, ftp, sip, dhcp og notice.

   ``` command
     corelight-client configuration update \
    --bro.export.defender.exclude=<logs_to_exclude> \
    --bro.export.defender.filter=<logs_to_filter>
   ```

## <a name="see-also"></a>Se også

- [Ofte stillede spørgsmål om enhedssøgning](device-discovery-faq.md)
