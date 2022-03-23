---
title: Eksempler på politikker for enhedsstyring for Intune
description: Lær at bruge politikker for enhedsstyring ved hjælp af eksempler, der kan bruges med Intune.
keywords: microsoft, defender, Microsoft Defender til Slutpunkt, mac, enhed, kontrol, usb, flytbart, medie, intune
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
ms.openlocfilehash: e9edec2b4e0b08cf6506f6234fbfb1f2c3c03914
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63593502"
---
# <a name="examples-of-device-control-policies-for-intune"></a>Eksempler på politikker for enhedsstyring for Intune

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Dette dokument indeholder eksempler på politikker for enhedsstyring, som du kan tilpasse til din egen organisation. Disse eksempler er gældende, hvis du bruger Intune til at administrere enheder i virksomheden.

## <a name="restrict-access-to-all-removable-media"></a>Begræns adgangen til alle flytbare medier

Følgende eksempel begrænser adgangen til alle flytbare medier. Bemærk den `none` tilladelse, der er anvendt på det øverste niveau i politikken, hvilket betyder, at alle filhandlinger ikke kan bruges.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>deviceControl</key>
                <dict>
                    <key>removableMediaPolicy</key>
                    <dict>
                        <key>enforcementLevel</key>
                        <string>block</string>
                        <key>permission</key>
                        <array>
                            <string>none</string>
                        </array>
                    </dict>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="set-all-removable-media-to-be-read-only"></a>Angiv, at alle flytbare medier skal være skrivebeskyttede

I følgende eksempel konfigureres alle flytbare medier til at være skrivebeskyttede. Bemærk den `read` tilladelse, der er anvendt på det øverste niveau i politikken, hvilket betyder, at alle skrive- og eksekveringshandlinger ikke kan bruges.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>deviceControl</key>
                <dict>
                    <key>removableMediaPolicy</key>
                    <dict>
                        <key>enforcementLevel</key>
                        <string>block</string>
                        <key>permission</key>
                        <array>
                            <string>read</string>
                        </array>
                    </dict>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="disallow-program-execution-from-removable-media"></a>Forbyde programudførelse fra flytbare medier

Følgende eksempel viser, hvordan programudførelse fra flytbare medier kan frameldes. Bemærk de `read` og `write` tilladelser, der anvendes på det øverste niveau i politikken.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>deviceControl</key>
                <dict>
                    <key>removableMediaPolicy</key>
                    <dict>
                        <key>enforcementLevel</key>
                        <string>block</string>
                        <key>permission</key>
                        <array>
                            <string>read</string>
                            <string>write</string>
                        </array>
                    </dict>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="restrict-all-devices-from-specific-vendors"></a>Begrænse alle enheder fra bestemte leverandører

I følgende eksempel begrænses alle enheder fra bestemte leverandører (i dette tilfælde identificeret af `fff0` og `4525`). Alle andre enheder vil være ubegrænset, da den tilladelse, der er defineret på det øverste niveau i politikken, viser alle mulige tilladelser (læse, skrive og udføre).

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>deviceControl</key>
                <dict>
                    <key>removableMediaPolicy</key>
                    <dict>
                        <key>enforcementLevel</key>
                        <string>block</string>
                        <key>permission</key>
                        <array>
                            <string>read</string>
                            <string>write</string>
                            <string>execute</string>
                        </array>
                        <key>vendors</key>
                        <dict>
                            <key>fff0</key>
                            <dict>
                                <key>permission</key>
                                <array>
                                    <string>none</string>
                                </array>
                            </dict>
                            <key>4525</key>
                            <dict>
                                <key>permission</key>
                                <array>
                                    <string>none</string>
                                </array>
                            </dict>
                        </dict>
                    </dict>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="restrict-specific-devices-identified-by-vendor-id-product-id-and-serial-number"></a>Begrænse bestemte enheder, der er identificeret af leverandør-id, produkt-id og serienummer

I følgende eksempel begrænses to bestemte enheder, der identificeres af leverandør-id `fff0`, produkt-id `1000`og serienumre `04ZSSMHI2O7WBVOA` og `04ZSSMHI2O7WBVOB`. På alle andre niveauer af politikken inkluderer tilladelserne alle mulige værdier (læse, skrive og udføre), hvilket betyder, at alle andre enheder vil være ubegrænset.

```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>deviceControl</key>
                <dict>
                    <key>removableMediaPolicy</key>
                    <dict>
                        <key>enforcementLevel</key>
                        <string>block</string>
                        <key>permission</key>
                        <array>
                            <string>read</string>
                            <string>write</string>
                            <string>execute</string>
                        </array>
                        <key>vendors</key>
                        <dict>
                            <key>fff0</key>
                            <dict>
                                <key>permission</key>
                                <array>
                                    <string>read</string>
                                    <string>write</string>
                                    <string>execute</string>
                                </array>
                                <key>products</key>
                                <dict>
                                    <key>1000</key>
                                    <dict>
                                        <key>permission</key>
                                        <array>
                                            <string>read</string>
                                            <string>write</string>
                                            <string>execute</string>
                                        </array>
                                        <key>serialNumbers</key>
                                        <dict>
                                            <key>04ZSSMHI2O7WBVOA</key>
                                            <array>
                                            <string>none</string>
                                            </array>
                                            <key>04ZSSMHI2O7WBVOB</key>
                                            <array>
                                            <string>none</string>
                                            </array>
                                        </dict>
                                    </dict>
                                </dict>
                            </dict>
                        </dict>
                    </dict>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over enhedsstyring til macOS](mac-device-control-overview.md)
