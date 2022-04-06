---
title: Microsoft Defender for Endpoint enhedshåndtering enhedsinstallation
description: I dette emne gennemgås Microsoft Defender for Endpoint enhedsinstallation
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: dc05633d1badfc29b2179915ac6d318dd9523834
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666388"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Microsoft Defender for Endpoint enhedshåndtering enhedsinstallation

**Gælder for**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint Enhedshåndtering Enhedsinstallation gør det muligt for dig at udføre følgende opgave:

- Undgå, at personer installerer bestemte enheder.
- Tillad personer at installere bestemte enheder, men undgå andre enheder.

> [!NOTE]
> Hvis du vil finde forskellen mellem Enhedsinstallation og Flytbare lageradgangskontrol, [skal du se Microsoft Defender for Endpoint Device Control Flytbare Storage Protection](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true).

|Privilegium|Tilladelse|
|---|---|
|Access|Enhedsinstallation |
|Handlingstilstand|Tillad, Forbyd |
|Understøttelse af CSP|Ja|
|Understøttelse af gruppepolitikobjekt|Ja|
|Brugerbaseret support|Nej|
|Computerbaseret support|Ja|

## <a name="prepare-your-endpoints"></a>Forbered dine slutpunkter

Installer enhedsinstallation på Windows 10, Windows 11 enheder Windows Server 2022.

## <a name="device-properties"></a>Enhedsegenskaber

Følgende enhedsegenskaber understøttes af understøttelse af enhedsinstallation:

- Enheds-id
- Hardware-id
- Kompatibelt id
- Enhedsklasse
- 'Flytbar enhed' Enhedstype: Nogle enheder kan klassificeres som flytbare enheder. En enhed anses for at være flytbar, når driveren til den enhed, den er tilsluttet, angiver, at enheden er flytbar. En USB-enhed rapporteres f.eks. at være flytbar af drivere til den USB-hub, som enheden er tilsluttet.
Du kan få flere oplysninger [under Enhedsinstallation i Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>Politikker

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Tillad installation af enheder, der svarer til nogen af disse enheds-id'er

Med denne politikindstilling kan du angive en liste over Plug and Play hardware-id'er og kompatible id'er for de enheder, Windows har tilladelse til at installere. Denne politikindstilling er kun beregnet til at blive brugt, når politikindstillingen **Anvend lagdelt rækkefølge for evaluering for Tillad og Forbyd enhedsinstallationspolitikker på tværs af alle politikindstillinger for enhedsmatchkriterier** er aktiveret.

Når denne politikindstilling er aktiveret sammen med **evalueringsrækkefølgen Anvend lagdelt rækkefølge for tillad og undgå enhedsinstallation på tværs af alle politikindstillinger for enhedsmatch**, har Windows tilladelse til at installere eller opdatere en hvilken som helst enhed, hvis Plug and Play hardware-id eller kompatible id vises på den liste, du opretter, medmindre en anden politikindstilling på samme eller højere lag i hierarkiet specifikt forhindrer  installation, f.eks. følgende politikindstillinger:

- Undgå installation af enheder, der svarer til disse enheds-id'er.
- Undgå installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er.

Hvis politikindstillingen **Anvend lagdelt rækkefølge for evaluering af Tillad og Forbyd enhedsinstallation på tværs af alle enhed match kriterier** ikke er aktiveret med denne politikindstilling, vil alle andre politikindstillinger, der specifikt forhindrer installation, have forrang.

> [!NOTE]
> Politikindstillingen **Forbyd installation af enheder, der ikke er beskrevet af andre politikindstillinger**, er blevet **erstattet af politikindstillingen Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd enhedsinstallationspolitikker på tværs af alle politikindstillinger for enhedsmatch** for understøttede mål Windows 10 versioner og Windows 11. Det anbefales, at du bruger politikindstillingen **Anvend lagdelt rækkefølge af evaluering for Tillad og Undgå enhedsinstallation på tværs af alle politikindstillinger for enhedsmatch** , når det er muligt.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Tillad installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er

Med denne politikindstilling kan du angive en liste over Plug and Play enhedsforekomst-id'er for de enheder, Windows har tilladelse til at installere. Denne politikindstilling er kun beregnet til at blive brugt, når politikindstillingen **Anvend lagdelt rækkefølge for evaluering for Tillad og Forbyd enhedsinstallationspolitikker på tværs af alle politikindstillinger for enhedsmatchkriterier** er aktiveret.

Når denne politikindstilling er aktiveret sammen med **evalueringsrækkefølgen Anvend lagdelt rækkefølge for tillad og forbyd enhedsinstallation på tværs af alle enhed matcher kriterier** for politikindstilling, har Windows tilladelse til at installere eller opdatere en hvilken som helst enhed, hvis Plug and Play enhedsforekomst-id vises på den liste, du opretter, medmindre en anden politikindstilling på samme eller højere lag i hierarkiet specifikt forhindrer, at  installation, f.eks. følgende politikindstillinger:

- Undgå installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er

Hvis politikindstillingen **Anvend lagdelt rækkefølge for evaluering af Tillad og Forbyd enhedsinstallation på tværs af alle enhed match kriterier** ikke er aktiveret med denne politikindstilling, vil alle andre politikindstillinger, der specifikt forhindrer installation, have forrang.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Tillad installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser

Med denne politikindstilling kan du angive en liste over enhedskonfigurationsklassen GUID'er (Globally Unique Identifiers) for driverpakker, som Windows har tilladelse til at installere. Denne politikindstilling er kun beregnet til at blive brugt, når politikindstillingen **Anvend lagdelt rækkefølge for evaluering for Tillad og Forbyd enhedsinstallationspolitikker på tværs af alle politikindstillinger for enhedsmatchkriterier** er aktiveret.

Når denne politikindstilling er aktiveret sammen med **evalueringsrækkefølgen Anvend lagdelt rækkefølge for tillad og undgå enhedsinstallation på tværs af alle politikindstillinger for enhedsmatch**, har Windows tilladelse til at installere eller opdatere driverpakker, hvis enhedskonfigurationsklasse-GUID'er vises på den liste, du opretter, medmindre en anden politikindstilling på samme eller højere lag i hierarkiet specifikt forhindrer denne installation,  f.eks. følgende politikindstillinger:

- Undgå installation af enheder til disse enhedsklasser
- Undgå installation af enheder, der svarer til disse enheds-id'er
- Undgå installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er

Hvis politikindstillingen **Anvend lagdelt rækkefølge for evaluering af Tillad og Forbyd enhedsinstallation på tværs af alle enhed match kriterier** ikke er aktiveret med denne politikindstilling, vil alle andre politikindstillinger, der specifikt forhindrer installation, have forrang.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Anvend den lagdelte evalueringsrækkefølge for Politikker for Tillad og Forbyd enhedsinstallation på tværs af alle kriterier for enhedsmatch

Denne politikindstilling ændrer den evalueringsrækkefølge, hvor politikindstillingerne Tillad og Forbyd anvendes, når mere end én politikindstilling for installation gælder for en given enhed. Aktivér denne politikindstilling for at sikre, at der anvendes overlappende kriterier for enhedsmatch baseret på et etableret hierarki, hvor mere specifikke matchkriterier tilsidesætter mindre specifikke matchkriterier. Den hierarkiske evalueringsrækkefølge for politikindstillinger, der angiver kriterier for enhedsmatch, er som følger:

**Id'er** \> for enhedsforekomst **Enheds-id'er** \> **Klasse for enhedskonfiguration** \> **Flytbare enheder**

#### <a name="device-instance-ids"></a>Id'er for enhedsforekomst

1. Undgå installation af enheder ved hjælp af drivere, der svarer til disse enhedsforekomst-id'er.
2. Tillad installation af enheder ved hjælp af drivere, der svarer til disse enhedsforekomst-id'er.

#### <a name="device-ids"></a>Enheds-id'er

1. Undgå installation af enheder ved hjælp af drivere, der svarer til disse enheds-id'er.
2. Tillad installation af enheder ved hjælp af drivere, der svarer til disse enheds-id'er.

#### <a name="device-setup-class"></a>Klasse for enhedskonfiguration

1. Undgå installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser.
2. Tillad installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser.

#### <a name="removable-devices"></a>Flytbare enheder

Undgå installation af flytbare enheder

> [!NOTE]
> Denne politikindstilling giver mere detaljeret kontrol end politikindstillingen **Forbyd installation af enheder, der ikke er beskrevet af andre politikindstillinger** . Hvis disse modstridende politikindstillinger aktiveres på samme tid, **aktiveres politikindstillingen Anvend lagdelt rækkefølge for evaluering for Tillad og Undgå enhedsinstallation på tværs af alle politikindstillinger for enhedsmatch** , og den anden politikindstilling ignoreres.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Undgå installation af enheder, der svarer til nogen af disse enheds-id'er

Med denne politikindstilling kan du angive en liste over Plug and Play hardware-id'er og kompatible id'er for de enheder, Windows forhindres i at installere. Denne politikindstilling tilsidesætter som standard alle andre politikindstillinger, der gør det muligt for Windows at installere en enhed.

> [!NOTE]
> Hvis du vil aktivere politikindstillingen **Tillad installation af enheder, der svarer til en af disse enhedsforekomst-id'er** , for at tilsidesætte denne politikindstilling for relevante enheder, skal du aktivere politikindstillingen **Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd enhedsinstallationspolitikker på tværs af alle enhed match kriterier** .

Hvis du aktiverer denne politikindstilling, forhindres Windows i at installere en enhed, hvis hardware-id eller kompatible id vises på den liste, du opretter. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af de angivne enheder fra en fjernskrivebordsklient til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan enheder installeres og opdateres som tilladt eller forhindres af andre politikindstillinger.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Undgå installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er

Denne politikindstilling giver dig mulighed for at angive en liste over Plug and Play enhedsforekomst-id'er for enheder, der Windows forhindres i at installere. Denne politikindstilling har forrang frem for alle andre politikindstillinger, der gør det muligt for Windows at installere en enhed.

Hvis du aktiverer denne politikindstilling, forhindres Windows i at installere en enhed, hvis enhedsforekomst-id vises på den liste, du opretter. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af de angivne enheder fra en fjernskrivebordsklient til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan enheder installeres og opdateres som tilladt eller forhindres af andre politikindstillinger.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Undgå installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser

Med denne politikindstilling kan du angive en liste over enhedsopsætningsklassen GUID'er (Globally Unique Identifiers) for driverpakker, der Windows forhindres i at installere. Denne politikindstilling tilsidesætter som standard alle andre politikindstillinger, der gør det muligt for Windows at installere en enhed.

> [!NOTE]
> Hvis du vil aktivere politikindstillingerne **Tillad installation af enheder, der svarer til et af disse enheds-id'er** og **Tillad installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er** , at tilsidesætte denne politikindstilling for relevante enheder, skal du aktivere politikindstillingen **Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd enhedsinstallationspolitikker på tværs af alle enhed match kriterier** .

Hvis du aktiverer denne politikindstilling, forhindres Windows i at installere eller opdatere driverpakker, hvis enhedskonfigurationsklasse-GUID'er vises på den liste, du opretter. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af de angivne enheder fra en fjernskrivebordsklient til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan Windows installere og opdatere enheder som tilladt eller forhindret af andre politikindstillinger.

### <a name="prevent-installation-of-removable-devices"></a>Undgå installation af flytbare enheder

Med denne politikindstilling kan du forhindre Windows i at installere flytbare enheder. En enhed anses for at være flytbar, når driveren til den enhed, den er tilsluttet, angiver, at enheden er flytbar. En USB-enhed (Universal Serial Bus) rapporteres f.eks. at være flytbar af driverne til den USB-hub, som enheden er tilsluttet. Denne politikindstilling tilsidesætter som standard alle andre politikindstillinger, der gør det muligt for Windows at installere en enhed.

> [!NOTE]
> Hvis du vil aktivere **indstillingen Tillad installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser**, **Tillad installation af enheder, der svarer til nogen af disse enheds-id'er**, og **Tillad installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er** , for at tilsidesætte denne politikindstilling for relevante enheder, skal du aktivere politikindstillingen **Anvend lagdelt rækkefølge af evaluering for Tillad og forbyd enhedsinstallationspolitikker på tværs af alle enhedsmatchkriterier** .

Hvis du aktiverer denne politikindstilling, forhindres Windows i at installere flytbare enheder, og eksisterende flytbare enheder kan ikke opdatere deres drivere. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af flytbare enheder fra en fjernskrivebordsklient til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan Windows installere og opdatere driverpakker til flytbare enheder som tilladt eller forhindret af andre politikindstillinger.

## <a name="common-removable-storage-access-control-scenarios"></a>Almindelige flytbare Storage Access Control scenarier

For at gøre dig fortrolig med Microsoft Defender for Endpoint Flytbare Storage Access Control har vi sammensat nogle almindelige scenarier, som du kan følge.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Scenarie 1: Undgå installation af alle USB-enheder, mens det kun er tilladt at installere et autoriseret USB-tommelfingerdrev

I dette scenarie bruges følgende politikker:

- Undgå installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser.
- Anvend den lagdelte evalueringsrækkefølge for Politikker for Tillad og Forbyd enhedsinstallation på tværs af alle kriterier for enhedsmatch.
- Tillad installation af enheder, der svarer til nogen af disse enhedsforekomst-id'er eller Tillad installation af enheder, der svarer til et af disse enheds-id'er.

#### <a name="deploying-and-managing-policy-via-intune"></a>Udrulning og administration af politik via Intune

Med enhedsinstallationsfunktionen kan du anvende politikken via Intune på enheden.

#### <a name="licensing"></a>Licensering

Før du går i gang med enhedsinstallationen, skal du bekræfte dit [Microsoft 365 abonnement](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). Hvis du vil have adgang til og bruge enhedsinstallationen, skal du have Microsoft 365 E3.

#### <a name="permission"></a>Tilladelse

I forbindelse med udrulning af politik i Intune skal kontoen have tilladelser til at oprette, redigere, opdatere eller slette enhedskonfigurationsprofiler. Du kan oprette brugerdefinerede roller eller bruge en af de indbyggede roller med disse tilladelser:

- Rolle som politik- og profiladministrator
- Eller brugerdefineret rolle med tilladelserne Opret/Rediger/Opdater/Læs/Slet/Vis rapporter aktiveret for profiler til enhedskonfiguration
- Eller global administrator

#### <a name="deploying-policy"></a>Installerer politik

I Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. Konfigurer **Forbyd installation af enheder ved hjælp af drivere, der svarer til disse enhedskonfigurationsklasser**.

    - Open Endpoint security > Reduktion af angrebsoverfladen > Opret politik > Platform: Windows 10 (og nyere) & profil: Enhedskontrol.

      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="Siden Rediger profil" lightbox="../../media/devicepolicy-editprofile.png":::

2. Tilslut en USB-enhed, så får du vist følgende fejlmeddelelse:

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="Fejlmeddelelsen" lightbox="../../media/devicepolicy-errormsg.png":::

3. Aktivér **Anvend lagdelt evalueringsrækkefølge for Politikker for Tillad og Forbyd enhedsinstallation på tværs af alle kriterier for enhedsmatch**.

    - **Understøtter kun OMA-URI på nuværende tidspunkt**: Enheder > konfigurationsprofiler > Opret profil > platform: Windows 10 (og nyere) & profil: Brugerdefineret

      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="Siden Rediger række" lightbox="../../media/devicepolicy-editrow.png":::

4. Aktivér og tilføj tilladt USB-forekomst-id – **Tillad installation af enheder, der svarer til nogen af disse enheds-id'er**.

    - Opdater trin 1 Profil for enhedskontrol

      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="Et id på siden Enhedskontrol" lightbox="../../media/devicepolicy-devicecontrol.png":::

    Tilføjer PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB på ovenstående skærmbillede skyldes, at det ikke er nok kun at aktivere et enkelt hardware-id for at aktivere et enkelt USB-tommelfingerdrev. Du skal sikre, at alle de USB-enheder, der går forud for målenhederne, ikke også er blokeret (tilladt). Du kan åbne Enhedshåndtering og ændre visningen til "Enheder efter forbindelser" for at se, hvordan enheder installeres i PnP-træet. I vores tilfælde skal følgende enheder være tilladt, så USB-destinationstommeldrevet også kan tillades:

    Tilføjer PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB på ovenstående skærmbillede skyldes, at det ikke er nok kun at aktivere et enkelt hardware-id for at aktivere et enkelt USB-tommelfingerdrev. Du skal sikre, at alle de USB-enheder, der går forud for målenhederne, ikke også er blokeret (tilladt). Du kan åbne Enhedshåndtering og ændre visningen til "Enheder efter forbindelser" for at se, hvordan enheder installeres i PnP-træet. I vores tilfælde skal følgende enheder være tilladt, så USB-destinationstommeldrevet også kan tillades:

    - "Intel(R) USB 3.0 eXtensible Host Controller – 1.0 (Microsoft)" -> PCI\CC_0C03
    - "USB-rodhub (USB 3.0)" -> USB\ROOT_HUB30
    - "Generic USB Hub" -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="Menupunktet Vis på siden Enhedshåndtering" lightbox="../../media/devicepolicy-devicemgr.png":::

    > [!NOTE]
    > Nogle enheder i systemet har flere netværkslag til at definere deres installation på systemet. USB-tommelfingerdrev er sådanne enheder. Når du enten vil blokere eller tillade dem på et system, er det derfor vigtigt at forstå forbindelsesstien for hver enhed. Der er flere generiske enheds-id'er, der ofte bruges i systemer, og som kan give en god start på at oprette en "liste over tilladte" i sådanne tilfælde. Følgende er et eksempel (det er ikke altid det samme for alle USB'er. Du skal forstå PnP-træet på den enhed, du vil administrere via Enhedshåndtering):
    >
    > PCI\CC_0C03; PCI\CC_0C0330; PCI\VEN_8086; PNP0CA1; PNP0CA1&HOST (til værtscontrollere)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (til USB-rodhubber)/USB\USB20_HUB (til generiske USB-hubs)/
    >
    > Specielt til stationære computere er det vigtigt at angive alle de USB-enheder, som dine tastaturer og mus er forbundet via, på ovenstående liste. Hvis du ikke gør det, kan det blokere en bruger fra at få adgang til computeren via HID-enheder.
    >
    > Forskellige pc-producenter har nogle gange forskellige måder at indlejre USB-enheder i PnP-træet på, men generelt er det sådan, det gøres.

5. Tilslut den tilladte USB igen. Du kan se, at den nu er tilladt og tilgængelig.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="Siden Fjern drevoplysninger" lightbox="../../media/devicepolicy-removedrive.png":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Udrulning og administration af politik via Gruppepolitik

Med enhedsinstallationsfunktionen kan du anvende politikken via Gruppepolitik.

#### <a name="licensing"></a>Licensering

Hvis du vil have adgang til og bruge enhedsinstallationen, skal du have Windows E3.

#### <a name="deploying-policy"></a>Installerer politik

Du kan finde installationsdetaljerne her: [Administrer enhedsinstallation med Gruppepolitik (Windows 10) – Windows klient](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Få vist flytbare Storage Access Control data for enhedsstyring i Microsoft Defender for Endpoint

På [Microsoft 365 sikkerhedsportal](https://sip.security.microsoft.com/homepage) vises et flytbart lager, der er blokeret af enhedsinstallationen for enhedskontrol. Hvis du vil have adgang til Microsoft 365 sikkerhed, skal du have følgende abonnement:

- Microsoft 365 til E5-rapportering

```kusto
//events triggered by Device Installation policies
DeviceEvents
| where ActionType == "PnpDeviceBlocked" or ActionType == "PnpDeviceAllowed"
| extend parsed=parse_json(AdditionalFields)
| extend MediaClassGuid = tostring(parsed.ClassGuid)
| extend MediaInstanceId = tostring(parsed.DeviceInstanceId)
| extend MediaDeviceId = tostring(parsed.MatchingDeviceId)
| project Timestamp , DeviceId, DeviceName, ActionType, MediaClassGuid, MediaDeviceId, MediaInstanceId, AdditionalFields
| order by Timestamp desc
```

:::image type="content" source="../../media/block-removable-storage2.png" alt-text="Bloklageret" lightbox="../../media/block-removable-storage2.png":::

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Hvordan kan jeg vide, om destinationscomputeren får den udrullede politik?

Du kan bruge følgende forespørgsel til at hente en antimalwareklientversion på Microsoft 365 sikkerhedsportalen:

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>Hvorfor virker politikken Tillad ikke?

Det er ikke nok kun at aktivere et enkelt hardware-id for at aktivere et enkelt USB-tommelfingerdrev. Sørg for, at alle de USB-enheder, der kommer før destinationen, ikke også er blokeret (tilladt).

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Ofte stillede spørgsmål om enhedsinstallation" lightbox="../../media/devicemgrscrnshot.png":::
