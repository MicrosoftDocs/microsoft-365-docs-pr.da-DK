---
title: Aktivér Corelight-integration i Microsoft Defender for Endpoint
description: Aktivér Corelight-integration for at opnå synlighed med fokus på IoT/OT-enheder i områder af netværket, hvor MDE ikke er installeret
keywords: aktivér siem-forbindelse, siem, forbindelse, sikkerhedsoplysninger og hændelser
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
ms.openlocfilehash: 3a7a4b7ab842baaadb276e60037451e8eb919bf9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465466"
---
# <a name="enable-corelight-data-integration"></a>Aktivere Integration af Corelight-data

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft har indgået partnerskab med [Corelight](https://corelight.com/integrations/iot-security), udbyder af branchens førende platform til åben netværksregistrering og -svar (NDR), som kan hjælpe dig med at opdage IoT-/OT-enheder på tværs af organisationen. Ved hjælp af data, der sendes fra Corelight-netværksenheder, øges Microsoft 365 Defender synligheden i netværksaktiviteterne for enheder, der ikke er administrerede, herunder kommunikation med andre enheder, der ikke er administrerede, eller eksterne netværk.

Når denne datakilde er aktiveret, sendes alle hændelser fra Corelight-netværkskabe til Microsoft 365 Defender. Du kan få vist disse aktiviteter på tidslinjen for ikke-administrerede enheder, der er tilgængelige Microsoft Defender for Endpoint lager over enheder. Du kan få mere at vide under [Enhedsregistrering](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Aktivering af Corelight-integration

Hvis du vil aktivere Corelight-integrationen, skal du gøre følgende:

[Trin 1: Slå Corelight til som datakilde](#step-1-turn-on-corelight-as-a-data-source)<br>
[Trin 2: Giv tilladelse til, at Corelight kan sende begivenheder til Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[Trin 3: Konfigurer Corelight-maskinen til at sende data Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>Trin 1: Slå Corelight til som datakilde

1. I navigationsruden på portalen skal [https://security.microsoft.com](https://security.microsoft.com/) du vælge Indstillinger **datakilder** \> **for enhedsregistrering**\>.

   :::image type="content" source="images/enable-corelight.png" alt-text="Siden datakilder i Microsoft 365 Defender portal" lightbox="images/enable-corelight.png":::

2. Vælg **Send Corelight-data til M365D,** og vælg **Gem**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>Trin 2: Giv tilladelse til, at Corelight kan sende begivenheder til Microsoft 365 Defender

> [!NOTE]
> Du skal være global administrator for at give Corelight-tilladelse til at få adgang til ressourcer i organisationen.

1. Som global lejeradministrator skal du gå til dette [link for](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) at give tilladelse.
2. Gå til [https://security.microsoft.com](https://security.microsoft.com/) portal, vælg **Indstillinger** \> **Microsoft 365 Defender**, og vær opmærksom på **lejer-id'et**. Du skal bruge disse oplysninger, når du konfigurerer dit Corelight-maskine.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>Trin 3: Konfigurer Corelight-maskinen til at sende data Microsoft 365 Defender

> [!NOTE]
>  Integrationen bliver offentlig i Corelight Sensor software v24 og nyere. 

Du skal udføre en prøveversion i v23 eller v22.1 `corelight-client configuration update --enable.adfiot 1` for at aktivere konfigurationssektionen i den grafiske brugergrænseflade.

Ud over dette kræver GUI-validering, at en formidler er konfigureret i konfigurationssektionen på alle v23-udgivelser.  Den formidler, du leverer, er påkrævet, men kan faktisk ikke bruges. Enter `127.0.0.1:1234` in the _kafka broker_ field to ensure successful validation before following the steps to enable sending data to Microsoft 365 Defender.

> [!NOTE]
> Du skal have forbindelse til internettet, for at din sensor kan nå både Defender- og Corelight-skytjenesterne, for at løsningen kan fungere.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Aktivering i Corelight Sensor GUI

1. I sektionen Konfiguration af Corelight-sensor-GUI skal du **vælge Sensor** \> **Export**.
2. Gå til EKSPORTÉR TIL **KAFKA på listen** , og vælg kontakten for at aktivere den.

   :::image type="content" source="images/exporttokafka.png" alt-text="Kafka-eksporten" lightbox="images/exporttokafka.png":::

3. Slå derefter EKSPORT TIL **AZURE DEFENDER FOR IOT** til, og angiv dit lejer-id, der er angivet i trin 1, i feltet LEJER-id.

   :::image type="content" source="images/exporttodiot.png" alt-text="Den iot-eksport" lightbox="images/exporttodiot.png":::

4. Vælg **Anvend ændringer**.

   :::image type="content" source="images/corelightapply.png" alt-text="Ikonet Anvend ændringer" lightbox="images/corelightapply.png":::

> [!NOTE]
> Konfigurationsindstillingerne i Kafka (undtagen Logudeudelse og Filtre) bør ikke ændres. De ændringer, der foretages, ignoreres.

#### <a name="enabling-in-the-corelight-client"></a>Aktivering i corelight-client

Du kan aktivere EKSPORT **TIL KAFKA** og **EKSPORTÉR TIL AZURE DEFENDER FOR IOT** ved hjælp af følgende kommando i corelight-client:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Hvis du allerede bruger Kafka-eksport, skal du kontakte Corelight Support for at få en alternativ konfiguration.

Sådan konfigureres det kun at sende et minimalt sæt logfiler:

1. I Corelight Sensor GUI skal du gå til afsnittet Kafka
2. Gå til **Zeek-logfiler for at udelukke**
3. Markér **alt**
4. Vælg derefter **x ud** for følgende logfiler for at sikre, at de fortsætter med at flyde til Microsoft:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Vælg **Anvend ændringer**

Listen over logfiler, der flyder til Microsoft, kan blive udvidet med tiden.

## <a name="see-also"></a>Se også

- [Ofte stillede spørgsmål om enhedsregistrering](device-discovery-faq.md)
