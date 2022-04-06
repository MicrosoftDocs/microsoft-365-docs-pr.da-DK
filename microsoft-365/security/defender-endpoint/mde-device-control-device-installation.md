---
title: Microsoft Defender for Endpoint installation af enhed til enhedsstyring
description: Dette emne indeholder en gennemgang af Microsoft Defender for Endpoint installation af enhed til enhedsstyring
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
ms.openlocfilehash: ccef3ec748983db89b6ceca9b8092eafbef0d899
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472611"
---
# <a name="microsoft-defender-for-endpoint-device-control-device-installation"></a>Microsoft Defender for Endpoint installation af enhed til enhedsstyring

**Gælder for**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint installation af Enhedskontrolenhed kan du udføre følgende opgave:

- Undgå, at brugere installerer bestemte enheder.
- Tillad brugere at installere bestemte enheder, men forhindre andre enheder.

> [!NOTE]
> Du kan finde forskellen mellem Enhedsinstallation og kontrol af flytbar lageradgang under [Microsoft Defender for Endpoint Enhedshåndtering Flytbar Storage Beskyttelse](/microsoft-365/security/defender-endpoint/device-control-removable-storage-protection?view=o365-worldwide&preserve-view=true).

|Rettighed|Tilladelse|
|---|---|
|Access|Installation af enhed |
|Handlingstilstand|Tillad, Forebyd |
|CSP-support|Ja|
|Understøttelse af gruppepolitikobjekt|Ja|
|Brugerbaseret support|Nej|
|Computerbaseret support|Ja|

## <a name="prepare-your-endpoints"></a>Forbered dine slutpunkter

Installer installation af enhed på Windows 10, Windows 11 enheder og Windows Server 2022.

## <a name="device-properties"></a>Enhedsegenskaber

Følgende enhedsegenskaber understøttes af enhedsinstallationssupport:

- Enheds-id
- Hardware-id
- Kompatibelt id
- Enhedsklasse
- Type af 'Flytbar enhed': Visse enheder kan klassificeres som Flytbare enheder. En enhed betragtes som flytbar, når driveren til den enhed, den er tilsluttet, angiver, at enheden er flytbar. En USB-enhed rapporteres f.eks. at være flytbar af driverne til den USB-hub, som enheden er tilsluttet.
Du kan finde flere oplysninger [under Installation af enhed i Windows](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="policies"></a>Politikker

### <a name="allow-installation-of-devices-that-match-any-of-these-device-ids"></a>Tillad installation af enheder, der svarer til et af disse enheds-cd'er

Denne politikindstilling giver dig mulighed for at angive en liste over Plug and Play hardware-Plug and Play og kompatible- og Windows til enheder, som Windows har tilladelse til at installere. Denne politikindstilling er beregnet til kun at blive brugt, når politikindstillingen Anvend lagdelt evalueringsrækkefølge for Tillad og Forbyd installation af enheder på tværs af alle politikker **for** overensstemmelse med enheder er aktiveret.

Når denne politikindstilling er aktiveret sammen med anvend lagvis evalueringsrækkefølge for Tillad og Undgå installation af enhed på tværs af alle politikindstillinger **for** enhedsmatchingkriterier, har Windows tilladelse til at installere eller opdatere enhver enhed, hvis Plug and Play-hardware-id eller kompatible id vises på den liste, du opretter, medmindre en anden politikindstilling på samme eller højere lag i hierarkiet specifikt forhindrer  installation, f.eks. følgende politikindstillinger:

- Undgå installation af enheder, der svarer til disse enheds-cd'er.
- Undgå installation af enheder, der svarer til et af disse enheds-forekomst-cd'er.

Hvis **politikindstillingen** Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd installation af enheder på tværs af alle politikker for enhedsmatchning ikke er aktiveret med denne politikindstilling, så har andre politikindstillinger, der specifikt forhindrer installation, forrang.

> [!NOTE]
> Indstillingen Forebyd **installation** af enheder, der ikke er beskrevet af andre politikindstillinger, er blevet erstattet af politikindstillingen Anvend lagdelt evalueringsrækkefølge **for** Tillad og Forbyd installation af enheder på tværs af alle politikindstillinger for enhedsmatchingkriterier for understøttede Windows 10-versioner og -Windows 11. Det anbefales, at du bruger indstillingen Anvend lagvis evalueringsrækkefølge for Tillad og Forbyd installation af enheder på tværs af alle politikker **for** enhedsmatchingkriterier, når det er muligt.

### <a name="allow-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Tillad installation af enheder, der svarer til et af disse enhedsforekomst-cd'er

Denne politikindstilling giver dig mulighed for at angive en liste over Plug and Play forekomster af enheder for enheder, Windows har tilladelse til at installere. Denne politikindstilling er beregnet til kun at blive brugt, når politikindstillingen Anvend lagdelt evalueringsrækkefølge for Tillad og Forbyd installation af enheder på tværs af alle politikker **for** overensstemmelse med enheder er aktiveret.

Når denne politikindstilling er aktiveret sammen med anvend lagvis evalueringsrækkefølge for Tillad og Undgå installation af enhed på tværs af alle politikker **for** enhedsmatching med kriterier, har Windows tilladelse til at installere eller opdatere enhver enhed, hvis Plug and Play enhedsforekomst-id vises på den liste, du opretter, medmindre en anden politikindstilling på samme eller højere lag i hierarkiet specifikt forhindrer det  installation, f.eks. følgende politikindstillinger:

- Undgå installation af enheder, der svarer til et af disse enheds-forekomst-cd'er

Hvis **politikindstillingen** Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd installation af enheder på tværs af alle politikker for enhedsmatchning ikke er aktiveret med denne politikindstilling, så har andre politikindstillinger, der specifikt forhindrer installation, forrang.

### <a name="allow-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Tillad installation af enheder med drivere, der svarer til disse enhedskonfigurationsklasser

Denne politikindstilling giver dig mulighed for at angive en liste over enhedskonfigurationsklasse GUID'er (Globally Unique Identifiers) for driverpakker, Windows har tilladelse til at installere. Denne politikindstilling er beregnet til kun at blive brugt, når politikindstillingen Anvend lagdelt evalueringsrækkefølge for Tillad og Forbyd installation af enheder på tværs af alle politikker **for** overensstemmelse med enheder er aktiveret.

Når denne politikindstilling er aktiveret sammen med indstillingen Anvend lagvis evalueringsrækkefølge for Tillad og Undgå installation af enhed på tværs af alle politikindstillinger **for** enhedsmatchingkriterier, har Windows tilladelse til at installere eller opdatere driverpakker, hvis enhedskonfigurationsklasse-GUID'er vises på den liste, du opretter, medmindre en anden politikindstilling på samme eller højere lag i hierarkiet specifikt forhindrer den pågældende installation.  f.eks. følgende politikindstillinger:

- Forebyd installation af enheder for disse enhedsklasser
- Undgå installation af enheder, der svarer til disse enheds-cd'er
- Undgå installation af enheder, der svarer til et af disse enheds-forekomst-cd'er

Hvis **politikindstillingen** Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd installation af enheder på tværs af alle politikker for enhedsmatchning ikke er aktiveret med denne politikindstilling, så har andre politikindstillinger, der specifikt forhindrer installation, forrang.

### <a name="apply-layered-order-of-evaluation-for-allow-and-prevent-device-installation-policies-across-all-device-match-criteria"></a>Anvend lagdelt evalueringsrækkefølge for Tillad og Forebyd installationspolitikker for enheder på tværs af alle kriterier for enhedsmatching

Denne politikindstilling ændrer evalueringsrækkefølgen, hvori indstillingerne Tillad og Forbyd anvendes, når der anvendes mere end én indstilling for installationspolitik for en given enhed. Aktivér denne politikindstilling for at sikre, at der anvendes overlappende enheds matchkriterier baseret på et etableret hierarki, hvor mere specifikke matchkriterier erstatter mindre specifikke matchkriterier. Den hierarkiske rækkefølge af evaluering for politikindstillinger, der angiver kriterier for enhedsmatchning, er som følger:

**Enhedsforekomst-iD'er** \> **Enheds-sdr.** \> **Klasse til konfiguration af enhed** \> **Flytbare enheder**

#### <a name="device-instance-ids"></a>Enhedsforekomst-iD'er

1. Undgå installation af enheder med drivere, der svarer til disse enheds-forekomst-cd'er.
2. Tillad installation af enheder med drivere, der svarer til disse enheds-forekomst-cd'er.

#### <a name="device-ids"></a>Enheds-sdr.

1. Undgå installation af enheder med drivere, der svarer til disse enheds-cd'er.
2. Tillad installation af enheder med drivere, der svarer til disse enheds-cd'er.

#### <a name="device-setup-class"></a>Klasse til konfiguration af enhed

1. Undgå installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration.
2. Tillad installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration.

#### <a name="removable-devices"></a>Flytbare enheder

Undgå installation af flytbare enheder

> [!NOTE]
> Denne politikindstilling giver mere detaljeret kontrol end indstillingen **Forebyd installation af enheder, der ikke er beskrevet i andre politikindstillinger** . Hvis disse indstillinger for modstridende politikker er aktiveret på samme tid, aktiveres politikindstillingen Anvend lagdelt evalueringsrækkefølge for Tillad og Forbyd installation af enheder på tværs af alle politikindstillinger **for** enhedsmatchingkriterier, og de andre politikindstillinger ignoreres.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-ids"></a>Undgå installation af enheder, der svarer til et af disse enheds-cd'er

Denne politikindstilling giver dig mulighed for at angive en liste over Plug and Play hardware-Plug and Play og kompatible- og Windows for enheder, som Windows ikke kan installere. Denne politikindstilling tilsidesætter som standard alle andre politikindstillinger, der gør det muligt Windows installere en enhed.

> [!NOTE]
> Hvis du vil aktivere politikindstillingen Tillad installation af enheder, der svarer til et af disse enhedsforekomst-cd'er for at erstatte denne politikindstilling for relevante enheder, skal du aktivere indstillingen Anvend lagdelt rækkefølge af evaluering for Tillad og Forbyd installation af enhed på tværs af alle politikindstillinger **for** enhedsmatchingkriterier.

Hvis du aktiverer denne politikindstilling, er Windows forhindret i at installere en enhed med hardware-id eller kompatibelt id på den liste, du opretter. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af de angivne enheder fra en klient til fjernskrivebord til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan enheder installeres og opdateres som tilladte eller forhindret af andre politikindstillinger.

### <a name="prevent-installation-of-devices-that-match-any-of-these-device-instance-ids"></a>Undgå installation af enheder, der svarer til et af disse enheds-forekomst-cd'er

Denne politikindstilling gør det muligt at angive en liste Plug and Play forekomst-Plug and Play på enheder, som Windows er forhindret i at installere. Denne politikindstilling tilsidesætter alle andre politikindstillinger, der gør det Windows at installere en enhed.

Hvis du aktiverer denne politikindstilling, er Windows forhindret i at installere en enhed, hvis enhedsforekomst-id vises på den liste, du opretter. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af de angivne enheder fra en klient til fjernskrivebord til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan enheder installeres og opdateres som tilladte eller forhindret af andre politikindstillinger.

### <a name="prevent-installation-of-devices-using-drivers-that-match-these-device-setup-classes"></a>Undgå installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration

Denne politikindstilling giver dig mulighed for at angive en liste over enhedskonfigurationsklasse GUID'er (Globally Unique Identifiers) for driverpakker, som Windows er forhindret i at installere. Denne politikindstilling tilsidesætter som standard alle andre politikindstillinger, der gør det muligt Windows installere en enhed.

> [!NOTE]
> Hvis du vil aktivere politikindstillingerne Tillad **installation** af enheder, der svarer til et af disse enheds-cd'er og Tillad **installation** af enheder, der svarer til nogen af disse enhedsforekomster-politikindstillinger for at erstatte denne politikindstilling **for** relevante enheder, skal du aktivere anvend lagdelt evalueringsrækkefølge for Tillad og Undgå installationspolitikker for enheder på tværs af alle politikker for enhedsmatchingkriterier.

Hvis du aktiverer denne politikindstilling, er Windows forhindret i at installere eller opdatere driverpakker, hvis enhedskonfigurationsklasse-GUID'er vises på den liste, du opretter. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af de angivne enheder fra en klient til fjernskrivebord til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, Windows installere og opdatere enheder som tilladte eller forhindret af andre politikindstillinger.

### <a name="prevent-installation-of-removable-devices"></a>Undgå installation af flytbare enheder

Denne politikindstilling gør det muligt at forhindre Windows at installere flytbare enheder. En enhed betragtes som flytbar, når driveren til den enhed, den er tilsluttet, angiver, at enheden er flytbar. En USB-enhed (Universal Serial Bus) er f.eks. rapporteret at være flytbar af driverne til den USB-hub, som enheden er tilsluttet. Denne politikindstilling tilsidesætter som standard alle andre politikindstillinger, der gør det muligt Windows installere en enhed.

> [!NOTE]
> For at aktivere klasserne Tillad **installation** af enheder med drivere, der svarer til disse **enhedskonfigurationsklasser** skal du Tillade installation af enheder, der passer til et af disse enheds-cd'er og Tillad **installation** af enheder, der svarer til nogen af disse enhedsforekomst-politikindstillinger for at erstatte denne politikindstilling for relevante enheder, aktivere indstillingen Anvend lagdelt rækkefølge for evaluering for Tillad og Forbyd installationspolitikker for enheder på tværs af alle politikindstillinger **for** enhedsmatchingkriterier.

Hvis du aktiverer denne politikindstilling, er Windows forhindret i at installere flytbare enheder, og eksisterende flytbare enheder kan ikke få deres drivere opdateret. Hvis du aktiverer denne politikindstilling på en fjernskrivebordsserver, påvirker politikindstillingen omdirigering af flytbare enheder fra en klient til fjernskrivebord til fjernskrivebordsserveren.

Hvis du deaktiverer eller ikke konfigurerer denne politikindstilling, kan Windows installere og opdatere driverpakker til flytbare enheder som tilladte eller forhindret af andre politikindstillinger.

## <a name="common-removable-storage-access-control-scenarios"></a>Almindelige flytbare Storage Access Control scenarier

For at gøre dig bekendt med Microsoft Defender for Endpoint Flytbare Storage Access Control har vi samlet nogle almindelige scenarier, som du kan følge.

### <a name="scenario-1-prevent-installation-of-all-usb-devices-while-allowing-an-installation-of-only-an-authorized-usb-thumb-drive"></a>Scenarie 1: Undgå installation af alle USB-enheder, mens du kun tillader en installation af et autoriseret USB-usb-drev

I dette scenarie bruges følgende politikker:

- Undgå installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration.
- Anvend lagdelt evalueringsrækkefølge for Tillad og Forbyd installationspolitikker for enheder på tværs af alle kriterier for enhedsmatching.
- Tillad installation af enheder, der svarer til et af disse enheds-forekomst-cd'er eller Tillad installation af enheder, der matcher et af disse enheds-cd'er.

#### <a name="deploying-and-managing-policy-via-intune"></a>Implementering og administration af politik via Intune

Med funktionen Til installation af enhed kan du anvende politikken via Intune på enhed.

#### <a name="licensing"></a>Licensering

Før du går i gang med installationen af enheden, skal du bekræfte dit [Microsoft 365 abonnement](https://www.microsoft.com/en-in/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=2). For at få adgang til og bruge enhedsinstallation skal du have Microsoft 365 E3.

#### <a name="permission"></a>Tilladelse

I forbindelse med udrulning af Intune skal kontoen have tilladelse til at oprette, redigere, opdatere eller slette enhedskonfigurationsprofiler. Du kan oprette brugerdefinerede roller eller bruge en af de indbyggede roller med disse tilladelser:

- Politik og profilstyringsrolle
- Eller brugerdefineret rolle med tilladelsen Opret/Rediger/Opdater/Læs/Slet/Vis rapporter aktiveret for Enhedskonfigurationsprofiler
- Eller Global administrator

#### <a name="deploying-policy"></a>Implementeringspolitik

I Microsoft Endpoint Manager [https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)

1. Konfigurer **Forebyd installation af enheder med drivere, der svarer til disse klasser til enhedskonfiguration**.

    - Åbn Endpoint-> reduktion af angrebsoverfladen > Opret politik > platform: Windows 10 (og nyere) & Profil: Enhedsstyring.
    
      :::image type="content" source="../../media/devicepolicy-editprofile.png" alt-text="Siden Rediger profil" lightbox="../../media/devicepolicy-editprofile.png":::
    
2. Tilslut en USB-enhed, så får du vist følgende fejlmeddelelse:

      :::image type="content" source="../../media/devicepolicy-errormsg.png" alt-text="Fejlmeddelelsen" lightbox="../../media/devicepolicy-errormsg.png":::

3. **Aktivér Anvend lagdelt evalueringsrækkefølge for Tillad og Forbyd installationspolitikker for enheder på tværs af alle kriterier for enhedsmatching**.

    - **understøtter kun OMA-URI i** øjeblikket: Enheder >-konfigurationsprofiler > Opret profil > platform: Windows 10 (og nyere) & Profil: Brugerdefineret
    
      :::image type="content" source="../../media/devicepolicy-editrow.png" alt-text="Siden Rediger række" lightbox="../../media/devicepolicy-editrow.png":::

4. Aktivér og tilføj tilladt USB-forekomst-id **– Tillad installation af enheder, der matcher et af disse enheds-id'er**.

    - Opdater trin 1 Enhedsstyringsprofil
    
      :::image type="content" source="../../media/devicepolicy-devicecontrol.png" alt-text="Et id på siden Enhedshåndtering" lightbox="../../media/devicepolicy-devicecontrol.png":::
       
    Tilføjelse af AFR LØBENDE\CC_0C03; 1. CC_0C0330. INDERT\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB oven for skærmbilledet er, fordi det ikke er nok kun at aktivere et enkelt hardware-id for at aktivere et enkelt USB-usb-drev. Du skal sikre dig, at alle de USB-enheder, der er forud for destinationen, heller ikke er blokeret (tilladt). Du kan åbne Enhedshåndtering og ændre visningen til "Enheder efter forbindelser" for at se, hvordan enheder er installeret i PnP-træet. I Vores tilfælde skal følgende enheder være tilladt, så USB-usb-drevet også kan tillades: 

    Tilføjelse af AFR LØBENDE\CC_0C03; 1. CC_0C0330. INDERT\VEN_8086; PNP0CA1; PNP0CA1&HOST; USB\ROOT_HUB30; USB\ROOT_HUB20; USB\USB20_HUB oven for skærmbilledet er, fordi det ikke er nok kun at aktivere et enkelt hardware-id for at aktivere et enkelt USB-usb-drev. Du skal sikre dig, at alle de USB-enheder, der er forud for destinationen, heller ikke er blokeret (tilladt). Du kan åbne Enhedshåndtering og ændre visningen til "Enheder efter forbindelser" for at se, hvordan enheder er installeret i PnP-træet. I Vores tilfælde skal følgende enheder være tilladt, så USB-usb-drevet også kan tillades:

    - "Intel(R) USB 3.0 eXtensible Host Controller – 1.0 (Microsoft)" -> ETHERNET\CC_0C03
    - "USB-rodhub (USB 3.0)" -> USB\ROOT_HUB30
    - "Generic USB Hub" -> USB\USB20_HUB

    :::image type="content" source="../../media/devicepolicy-devicemgr.png" alt-text="Menupunktet Vis på Enhedshåndtering side" lightbox="../../media/devicepolicy-devicemgr.png":::

    > [!NOTE]
    > Nogle enheder i systemet har flere lag forbindelse til at definere deres installation i systemet. USB-usb-drev er sådanne enheder. Når du ønsker at blokere eller tillade dem på et system, er det derfor vigtigt at forstå stien til forbindelsen for hver enhed. Der er flere generiske enheds-it'er, der ofte bruges i systemer, og som kan give en god start på at oprette en "tilladelsesliste" i sådanne tilfælde. Følgende er et eksempel (det er ikke altid det samme for alle USB'er; du skal forstå PNP-træet for den enhed, du vil administrere via Enhedshåndtering):
    >
    > 1. CC_0C03. 1. CC_0C0330. INDERT\VEN_8086; PNP0CA1; PNP0CA1&HOST (til værtscontrollere)/ USB\ROOT_HUB30; USB\ROOT_HUB20 (til USB-rodhubs)/ USB\USB20_HUB (til generiske USB-hubs)/
    >
    > Specifikt til stationære computere er det vigtigt at nævne alle de USB-enheder, som dine tastaturer og mus er tilsluttet via på ovenstående liste. Hvis du ikke gør dette, kan det blokere en bruger i at få adgang til sin computer via HID-enheder.
    >
    > Forskellige pc-producenter har nogle gange forskellige måder at indlejre USB-enheder i PnP-træet på, men generelt er det sådan, det gøres.

5. Tilslut det tilladte USB igen. Du kan se, at det nu er tilladt og tilgængeligt.

    :::image type="content" source="../../media/devicepolicy-removedrive.png" alt-text="Siden Fjern drevdetaljer" lightbox="../../media/devicepolicy-removedrive.png":::

#### <a name="deploying-and-managing-policy-via-group-policy"></a>Implementering og administration af politik via Gruppepolitik

Med funktionen Til installation af enhed kan du anvende politikken via Gruppepolitik.

#### <a name="licensing"></a>Licensering

For at få adgang til og bruge enhedsinstallation skal du have Windows E3.

#### <a name="deploying-policy"></a>Implementeringspolitik

Du kan finde installationsdetaljene her: Administrer installation [af enhed med Gruppepolitik (Windows 10) - Windows klient](/windows/client-management/manage-device-installation-with-group-policy).

## <a name="view-device-control-removable-storage-access-control-data-in-microsoft-defender-for-endpoint"></a>Vis flytbare enhedsstyringsdata Storage Access Control i Microsoft Defender for Endpoint

[Sikkerhedsportalen Microsoft 365](https://sip.security.microsoft.com/homepage) flytbart lager, der er blokeret af installationen af enhedens kontrolenhed. For at få Microsoft 365 adgang til sikkerhed skal du have følgende abonnement:

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

### <a name="how-can-i-know-whether-the-target-machine-gets-the-deployed-policy"></a>Hvordan ved jeg, om destinationscomputeren får den installerede politik?

Du kan bruge følgende forespørgsel til at få antimalwareklientversion på Microsoft 365-sikkerhedsportalen:

```kusto
//check whether the Device installation policy has been deployed to the target machine, event only when modification happens
DeviceRegistryEvents
| where RegistryKey contains "HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows\\DeviceInstall\\"
| order by Timestamp desc
```

## <a name="why-the-allow-policy-doesnt-work"></a>Hvorfor virker politikken Tillad ikke?

Det er ikke nok kun at aktivere et enkelt hardware-id for at aktivere et enkelt USB-usb-drev. Sørg for, at alle USB-enheder, der står foran destinationen, heller ikke blokeres (tilladt).

:::image type="content" source="../../media/devicemgrscrnshot.png" alt-text="Ofte stillede spørgsmål om installation af enhed" lightbox="../../media/devicemgrscrnshot.png":::

