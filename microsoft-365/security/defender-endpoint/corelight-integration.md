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
ms.openlocfilehash: bf3095b9178b4ff2e71d4ee5f652d9316f233746
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664584"
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
>  Integrationen vil være offentlig i Corelight Sensor software v24 og nyere. 

Hvis du vil have vist et eksempel i v23 eller v22.1, skal du udføre `corelight-client configuration update --enable.adfiot 1` for at aktivere konfigurationsafsnittet i den grafiske brugergrænseflade.

Derudover kræver den grafiske brugergrænsefladevalidering, at der er konfigureret en mægler i konfigurationsafsnittet på alle v23-udgivelser.  Den mægler, du angiver, er påkrævet, men bruges faktisk ikke. Angiv `127.0.0.1:1234` i feltet _kafka broker_ for at sikre, at valideringen lykkes, før du følger nedenstående trin for at aktivere afsendelse af data til Microsoft 365 Defender.

> [!NOTE]
> Du skal bruge internetforbindelse, for at din sensor kan nå både Defender- og Corelight-cloudtjenesterne, for at løsningen kan fungere.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Aktivering i den grafiske brugergrænseflade for Corelight-sensoren

1. I konfigurationsafsnittet Corelight Sensor GUI skal du vælge **Sensoreksport**\>.
2. Gå til **EKSPORTÉR TIL KAFKA** på listen, og vælg skift for at slå den til.

   :::image type="content" source="images/exporttokafka.png" alt-text="Kafka-eksporten" lightbox="images/exporttokafka.png":::

3. Slå derefter **EKSPORTÉR TIL AZURE DEFENDER FOR IOT til** , og angiv dit lejer-id, som er angivet i trin 1, i feltet LEJER-id.

   :::image type="content" source="images/exporttodiot.png" alt-text="Den ikke-eksporterede" lightbox="images/exporttodiot.png":::

4. Vælg **Anvend ændringer**.

   :::image type="content" source="images/corelightapply.png" alt-text="Ikonet Anvend ændringer" lightbox="images/corelightapply.png":::

> [!NOTE]
> Konfigurationsindstillinger i Kafka (undtagen logudeladelse og filtre) bør ikke ændres. Eventuelle ændringer, der er foretaget, ignoreres.

#### <a name="enabling-in-the-corelight-client"></a>Aktivering i corelight-client

Du kan aktivere **EKSPORTÉR TIL KAFKA** og **EKSPORTÉR TIL AZURE DEFENDER FOR IOT** ved hjælp af følgende kommando i corelight-client:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Hvis du allerede bruger Kafka-eksport, skal du kontakte Corelight Support for at få en alternativ konfiguration.

Sådan konfigurerer du kun afsendelse af det minimale sæt logge:

1. I gui'en Corelight Sensor skal du gå til afsnittet Kafka
2. Gå til **Zeek-logfiler for at udelade**
3. Markér **alle**
4. Vælg derefter **x** ud for følgende logge for at sikre, at de fortsætter med at gå til Microsoft:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Vælg **Anvend ændringer**

Listen over logfiler, der overføres til Microsoft, udvides muligvis over tid.

## <a name="see-also"></a>Se også

- [Ofte stillede spørgsmål om enhedssøgning](device-discovery-faq.md)
