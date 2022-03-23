---
title: Enhedsstyring til macOS
description: Få mere at vide om, hvordan du konfigurerer Microsoft Defender til slutpunkt på Mac for at reducere trusler fra flytbare lager som f.eks. USB-enheder.
keywords: microsoft, defender, Microsoft Defender til Slutpunkt, mac, enhed, kontrol, usb, flytbart, medie
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5cb41b0bd3f185237055daa2d282f0a1d6975a49
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63592643"
---
# <a name="device-control-for-macos"></a>Enhedsstyring til macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="requirements"></a>Krav

Enhedsstyring til macOS har følgende forudsætninger:

> [!div class="checklist"]
>
> - Rettighed for Microsoft Defender til slutpunkt (kan være prøveversion)
> - Minimumversion af OS: macOS 11 eller nyere
> - Minimumsversion af produkt: 101.34.20

## <a name="device-control-policy"></a>Politik for enhedsstyring

Hvis du vil konfigurere enhedsstyring for macOS, skal du oprette en politik, der beskriver de begrænsninger, du vil have i organisationen.

Politikken for enhedsstyring er inkluderet i konfigurationsprofilen, der bruges til at konfigurere alle andre produktindstillinger. Du kan finde flere oplysninger [under Konfiguration af profilstruktur](mac-preferences.md#configuration-profile-structure).

I konfigurationsprofilen er politikken for enhedsstyring defineret i følgende afsnit:

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|deviceControl|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|

Politikken for enhedsstyring kan bruges til at:

- [Tilpas URL-destinationen for meddelelser, der er hævet af enhedskontrol](#customize-url-target-for-notifications-raised-by-device-control)
- [Tillad eller bloker flytbare enheder](#allow-or-block-removable-devices)

### <a name="customize-url-target-for-notifications-raised-by-device-control"></a>Tilpas URL-destinationen for meddelelser, der er hævet af enhedskontrol

Når den politik for enhedsstyring, du har indført, håndhæves på en enhed (f.eks. er adgang til et flytbart medie enhed begrænset), vises der en meddelelse til brugeren.

![Meddelelse om enhedsstyring.](images/mac-device-control-notification.png)

Når slutbrugere klikker på denne meddelelse, åbnes en webside i standardbrowseren. Du kan konfigurere den URL-adresse, der åbnes, når slutbrugere klikker på meddelelsen.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|navigationTarget|
|**Datatype**|String|
|**Kommentarer**|Hvis det ikke er defineret, anvender produktet en standard-URL-adresse, der peger på en generisk side, der forklarer den handling, der er foretaget af produktet.|
|

### <a name="allow-or-block-removable-devices"></a>Tillad eller bloker flytbare enheder

Sektionen med flytbare medier i politikken for enhedsstyring bruges til at begrænse adgangen til flytbare medier.

> [!NOTE]
> Følgende typer flytbare medier understøttes i øjeblikket og kan medtages i politikken: USB-lagerenheder.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|flytbareMediaPolicy|
|**Datatype**|Ordbog (indlejret indstilling)|
|**Kommentarer**|Se de følgende afsnit for at få en beskrivelse af indholdet i ordbogen.|
|

Denne del af politikken er hierarkisk, der giver maksimal fleksibilitet og dækker en lang række use cases. Leverandører identificeres ved hjælp af et leverandør-id på det øverste niveau. For hver leverandør er der produkter, der er identificeret ved hjælp af et produkt-id. Endelig er der for hvert produkt serienumre, der viser bestemte enheder.

```text
|-- policy top level
    |-- vendor 1
        |-- product 1
            |-- serial number 1
            ...
            |-- serial number N
        ...
        |-- product N
    ...
    |-- vendor N
```

Du kan finde oplysninger om, hvordan du finder enheds-id'erne, under [Slå enheds-id'er op](#look-up-device-identifiers).

Politikken evalueres fra den mest specifikke post til den mest generelle. Når en enhed er tilsluttet, forsøger produktet at finde det mest specifikke match i politikken for hver flytbare medieenhed og anvende tilladelserne på dette niveau. Hvis der ikke er noget match, anvendes det næste bedste match, helt til den tilladelse, der er angivet på det øverste niveau, som er standarden, når en enhed ikke svarer til nogen anden indtastning i politikken.

#### <a name="policy-enforcement-level"></a>Håndhævelsesniveau for politikker

Under sektionen flytbare medier er der mulighed for at angive håndhævelsesniveauet, hvilket kan tage en af følgende værdier:

- `audit` - Hvis adgangen til en enhed begrænses i dette håndhævelsesniveau, vises der en meddelelse til brugeren, men enheden kan stadig bruges. Dette håndhævelsesniveau kan være nyttigt for at evaluere effektiviteten af en politik.
- `block` - Under dette håndhævelsesniveau er de handlinger, brugeren kan udføre på enheden, begrænset til det, der er defineret i politikken. Desuden er der hævet en meddelelse til brugeren.

> [!NOTE]
> Som standard er håndhævelsesniveauet indstillet til `audit`.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|enforcementLevel|
|**Datatype**|String|
|**Mulige værdier**|overvågning (standard) <p> bloker|
|

#### <a name="default-permission-level"></a>Standardtilladelsesniveau

På det øverste niveau i sektionen med flytbare medier kan du konfigurere standardtilladelsesniveauet for enheder, der ikke svarer til andet i politikken.

Denne indstilling kan indstilles til:

- `none` - Der kan ikke udføres nogen handlinger på enheden
- En kombination af følgende værdier:
  - `read` - Læsehandlinger er tilladt på enheden
  - `write` - Skrivehandlinger er tilladt på enheden
  - `execute` - Udfør handlinger er tilladt på enheden

> [!NOTE]
> Hvis `none` den findes i tilladelsesniveauet, ignoreres andre tilladelser (`read`, `write``execute`eller ).
>
> Tilladelsen `execute` refererer kun til udførelse af Mach-O-binære. Det omfatter ikke udførelse af scripts eller andre typer nyttedata.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|tilladelse|
|**Datatype**|Matrix med strenge|
|**Mulige værdier**|ingen <p> læs <p> skriv <p> udfør|
|

#### <a name="restrict-removable-media-by-vendor-product-and-serial-number"></a>Begrænse flytbare medier efter leverandør, produkt og serienummer

Som beskrevet i [Tillad eller bloker](#allow-or-block-removable-devices) flytbare enheder kan flytbare medier, f.eks. USB-enheder, identificeres ved hjælp af leverandør-id, produkt-id og serienummer.

På det øverste niveau i politikken for flytbare medier kan du eventuelt definere mere detaljerede begrænsninger på leverandørniveau.

Ordbogen `vendors` indeholder en eller flere poster, hvor hver post identificeres af leverandør-id'et.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|leverandører|
|**Datatype**|Ordbog (indlejret indstilling)|
|

For hver leverandør kan du angive det ønskede tilladelsesniveau for enheder fra den pågældende leverandør.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|tilladelse|
|**Datatype**|Matrix med strenge|
|**Mulige værdier**|Samme som [standardtilladelsesniveau](#default-permission-level)|
|

Du kan også vælge at angive det sæt produkter, der tilhører den pågældende leverandør, og for hvilke der er defineret mere detaljerede tilladelser. Ordbogen `products` indeholder en eller flere poster, hvor hver post identificeres ved hjælp af produkt-id'et.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|produkter|
|**Datatype**|Ordbog (indlejret indstilling)|
|

For hvert produkt kan du angive det ønskede tilladelsesniveau for det pågældende produkt.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|tilladelse|
|**Datatype**|Matrix med strenge|
|**Mulige værdier**|Samme som [standardtilladelsesniveau](#default-permission-level)|
|

Du kan også angive et valgfrit sæt serienumre, for hvilke der er defineret mere detaljerede tilladelser.

Ordbogen `serialNumbers` indeholder en eller flere poster, hvor hvert element identificeres ved hjælp af serienummeret.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|serialNumbers|
|**Datatype**|Ordbog (indlejret indstilling)|
|

For hvert serienummer kan du angive det ønskede tilladelsesniveau.

<br>

****

|Sektion|Værdi|
|---|---|
|**Domæne**|`com.microsoft.wdav`|
|**Tast**|tilladelse|
|**Datatype**|Matrix med strenge|
|**Mulige værdier**|Samme som [standardtilladelsesniveau](#default-permission-level)|
|

#### <a name="example-device-control-policy"></a>Eksempel på politik for enhedsstyring

Følgende eksempel viser, hvordan alle ovenstående begreber kan kombineres til en politik for enhedsstyring. I følgende eksempel skal du være opmærksom på den hierarkiske type af politikken for flytbare medier.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>deviceControl</key>
    <dict>
        <key>navigationTarget</key>
        <string>[custom URL for notifications]</string>
        <key>removableMediaPolicy</key>
        <dict>
            <key>enforcementLevel</key>
            <string>[enforcement level]</string> <!-- audit / block -->
            <key>permission</key>
            <array>
                <string>[permission]</string> <!-- none / read / write / execute -->
                <!-- other permissions -->
            </array>
            <key>vendors</key>
            <dict>
                <key>[vendor id]</key>
                <dict>
                    <key>permission</key>
                    <array>
                        <string>[permission]</string> <!-- none / read / write / execute -->
                        <!-- other permissions -->
                    </array>
                    <key>products</key>
                    <dict>
                        <key>[product id]</key>
                        <dict>
                            <key>permission</key>
                            <array>
                                <string>[permission]</string> <!-- none / read / write / execute -->
                                <!-- other permissions -->
                            </array>
                            <key>serialNumbers</key>
                            <dict>
                                <key>[serial-number]</key>
                                <array>
                                    <string>[permission]</string> <!-- none / read / write / execute -->
                                    <!-- other permissions -->
                                </array>
                                <!-- other serial numbers -->
                            </dict>
                        </dict>
                        <!-- other products -->
                    </dict>
                </dict>
                <!-- other vendors -->
            </dict>
        </dict>
    </dict>
</dict>
</plist>
```

Vi har medtaget flere eksempler på politikker for enhedsstyring i følgende dokumenter:

- [Eksempler på politikker for enhedsstyring for Intune](mac-device-control-intune.md)
- [Eksempler på politikker for enhedsstyring for SYLF](mac-device-control-jamf.md)

#### <a name="look-up-device-identifiers"></a>Slå enheds-id'er op

Sådan finder du leverandør-id, produkt-id og serienummer på en USB-enhed:

1. Log på en Mac-enhed.
1. Tilslut den USB-enhed, du vil søge efter identifikatorerne for.
1. I menuen på macOS på øverste niveau skal du vælge **Om denne Mac**.

    ![Om denne Mac.](images/mac-device-control-lookup-1.png)

1. Vælg **Systemrapport**.

    ![Systemrapport.](images/mac-device-control-lookup-2.png)

1. Vælg USB i den venstre **kolonne**.

    ![Visning af alle USB-enheder.](images/mac-device-control-lookup-3.png)

1. Under **USB-enhedstræ** skal du gå til den USB-enhed, du har tilsluttet.

    ![Detaljer om en USB-enhed.](images/mac-device-control-lookup-4.png)

1. Leverandør-id, produkt-id og serienummer vises. Når du føjer leverandør-id og produkt-id til politikken for flytbare medier, skal du kun tilføje delen efter `0x`. I nedenstående billede er leverandør-id f.eks`1000`. og produkt-id .`090c`

#### <a name="discover-usb-devices-in-your-organization"></a>Opdag USB-enheder i din organisation

Du kan få vist mount- og unmount-hændelser og volumenændringshændelser, der stammer fra USB-enheder i Microsoft Defender til avanceret jagt på slutpunkter. Disse hændelser kan være nyttige til at identificere mistænkelig forbrugsaktivitet eller udføre interne undersøgelser.

```bash
DeviceEvents
    | where ActionType == "UsbDriveMounted" or ActionType == "UsbDriveUnmounted" or ActionType == "UsbDriveDriveLetterChanged"
    | where DeviceId == "<device ID>"
```

## <a name="device-control-policy-deployment"></a>Installation af politik for enhedsstyring

Politikken for enhedsstyring skal inkluderes ud for de andre produktindstillinger, som beskrevet i Angiv indstillinger [for Microsoft Defender til Slutpunkt på macOS](mac-preferences.md).

Denne profil kan installeres ved hjælp af de instruktioner, der er angivet i [Konfigurationsprofilinstallation](mac-preferences.md#configuration-profile-deployment).

## <a name="troubleshooting-tips"></a>Tip til fejlfinding

Når du har skubbet konfigurationsprofilen via Intune eller JAMF, kan du kontrollere, om den blev afhentet korrekt af produktet ved at køre følgende kommando fra Terminalen:

```bash
mdatp device-control removable-media policy list
```

Denne kommando udskriver den politik for enhedsstyring, der bruges som standard. `Policy is empty`Hvis dette udskrives, skal du sikre dig, at (a) konfigurationsprofilen rent faktisk er blevet rykket til din enhed fra administrationskonsollen, og (b) det er en gyldig politik for enhedsstyring, sådan som det er beskrevet i dette dokument.

På en enhed, hvor politikken er blevet leveret, og hvor der er tilsluttet en eller flere enheder, kan du køre følgende kommando for at få vist en liste over alle enheder og de effektive tilladelser, der er anvendt på dem.

```bash
mdatp device-control removable-media devices list
```

Eksempel på output:

```Output
.Device(s)
|-o Name: Untitled 1, Permission ["read", "execute"]
| |-o Vendor: General "fff0"
| |-o Product: USB Flash Disk "1000"
| |-o Serial number: "04ZSSMHI2O7WBVOA"
| |-o Mount point: "/Volumes/TESTUSB"
```

I eksemplet ovenfor er der kun én flytbar medieenhed tilsluttet, `read` `execute` og den har og tilladelser i henhold til politikken for enhedsstyring, der blev leveret til enheden.

## <a name="related-topics"></a>Relaterede emner

- [Eksempler på politikker for enhedsstyring for Intune](mac-device-control-intune.md)
- [Eksempler på politikker for enhedsstyring for SYLF](mac-device-control-jamf.md)
