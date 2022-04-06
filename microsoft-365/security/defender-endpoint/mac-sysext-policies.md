---
title: Nye konfigurationsprofiler til macOS Catalina og nyere versioner af macOS
description: I dette emne beskrives de ændringer, der skal foretages for at kunne drage fordel af systemudvidelserne, som er en erstatning for kerneudvidelser på macOS Catalina og nyere versioner af macOS.
keywords: microsoft, defender, Microsoft Defender for Endpoint, mac, kernel, system, udvidelser, catalina
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ROBOTS: noindex,nofollow
ms.technology: mde
ms.openlocfilehash: 53194aac16091b9afd9559b4f372c2d436c198bf
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474701"
---
# <a name="new-configuration-profiles-for-macos-catalina-and-newer-versions-of-macos"></a>Nye konfigurationsprofiler til macOS Catalina og nyere versioner af macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

I overensstemmelse med macOS's udvikling forbereder vi en Microsoft Defender for Endpoint på macOS-opdatering, der udnytter systemudvidelser i stedet for kerneudvidelser. Denne opdatering gælder kun for macOS Catalina (10.15.4) og nyere versioner af macOS.

Hvis du har installeret Microsoft Defender for Endpoint på macOS i et administreret miljø (via JAMF, Intune eller en anden MDM-løsning), skal du implementere nye konfigurationsprofiler. Hvis du ikke gør dette, medfører det, at brugerne får godkendelsesanmodninger om at køre disse nye komponenter.

## <a name="jamf"></a>JAMF

### <a name="jamf-system-extensions-policy"></a>Politik forPROPPsystemudvidelser

For at godkende systemudvidelserne skal du oprette følgende nyttedata:

1. I **Computere > konfigurationsprofiler skal** **du vælge > på Systemudvidelser**.
2. Vælg **Tilladte systemudvidelser** **på rullelisten** Systemudvidelsestyper.
3. Brug **UBF8T346G9 til** Team-id.
4. Føj følgende bundle-id'er til **listen tilladte systemudvidelser** :

    - **com.microsoft.wdav.epsext**
    - **com.microsoft.wdav.netext**

    :::image type="content" source="images/mac-approved-system-extensions.png" alt-text=" Siden godkendte systemudvidelser" lightbox="images/mac-approved-system-extensions.png":::

### <a name="privacy-preferences-policy-control"></a>Politikkontrolelement for indstillinger for beskyttelse af personlige oplysninger

Tilføj følgende SYLF-nyttedata for at give fuld diskadgang til Microsoft Defender for Endpoint endpoint-sikkerhedsudvidelsen. Denne politik er en forudsætning for at køre udvidelsen på din enhed.

1. Vælg Indstillinger **for Politikkontrolelement** \> **for indstillinger for beskyttelse af personlige oplysninger**.
2. Brug som `com.microsoft.wdav.epsext` **Identifikator** `Bundle ID` og **som Bundle-type**.
3. Indstil kodekrav til `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
4. Angiv **app eller tjeneste** til **SystemPolicyAllFiles** , og få adgang til **Tillad**.

   :::image type="content" source="images/mac-system-extension-privacy.png" alt-text=" Menupunktet Politikkontrolelementet Indstillinger for beskyttelse af personlige oplysninger" lightbox="images/mac-system-extension-privacy.png":::

### <a name="network-extension-policy"></a>Politik for netværksudvidelse

Som en del af egenskaberne slutpunktsregistrering og svar undersøger Microsoft Defender for Endpoint på macOS sockettrafik og rapporterer disse oplysninger til Microsoft 365 Defender portal. Følgende politik gør det muligt for netværksudvidelsen at udføre denne funktionalitet.

> [!NOTE]
> JAMF har ikke indbygget understøttelse af politikker for filtrering af indhold, hvilket er en forudsætning for at aktivere de netværksudvidelser, Microsoft Defender for Endpoint installerer på macOS på enheden. DESUDEN ændrer SYLEF nogle gange indholdet af de politikker, der installeres.
> Følgende trin er derfor en løsning, der involverer signering af konfigurationsprofilen.

1. Gem følgende indhold på din enhed ved hjælp af `com.microsoft.network-extension.mobileconfig` et tekstredigeringsprogram:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
    <plist version="1">
        <dict>
            <key>PayloadUUID</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadType</key>
            <string>Configuration</string>
            <key>PayloadOrganization</key>
            <string>Microsoft Corporation</string>
            <key>PayloadIdentifier</key>
            <string>DA2CC794-488B-4AFF-89F7-6686A7E7B8AB</string>
            <key>PayloadDisplayName</key>
            <string>Microsoft Defender Network Extension</string>
            <key>PayloadDescription</key>
            <string/>
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
                    <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                    <key>PayloadType</key>
                    <string>com.apple.webcontent-filter</string>
                    <key>PayloadOrganization</key>
                    <string>Microsoft Corporation</string>
                    <key>PayloadIdentifier</key>
                    <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                    <key>PayloadDisplayName</key>
                    <string>Approved Network Extension</string>
                    <key>PayloadDescription</key>
                    <string/>
                    <key>PayloadVersion</key>
                    <integer>1</integer>
                    <key>PayloadEnabled</key>
                    <true/>
                    <key>FilterType</key>
                    <string>Plugin</string>
                    <key>UserDefinedName</key>
                    <string>Microsoft Defender Network Extension</string>
                    <key>PluginBundleID</key>
                    <string>com.microsoft.wdav</string>
                    <key>FilterSockets</key>
                    <true/>
                    <key>FilterDataProviderBundleIdentifier</key>
                    <string>com.microsoft.wdav.netext</string>
                    <key>FilterDataProviderDesignatedRequirement</key>
                    <string>identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                </dict>
            </array>
        </dict>
    </plist>
    ```

2. Kontrollér, at filen ovenfor blev kopieret korrekt ved at køre `plutil` værktøjet i Terminalen:

    ```bash
    $ plutil -lint <PathToFile>/com.microsoft.network-extension.mobileconfig
    ```

    Hvis filen f.eks. blev gemt i Dokumenter:

    ```bash
    $ plutil -lint ~/Documents/com.microsoft.network-extension.mobileconfig
    ```

    Kontrollér, at kommandooutput .`OK`

    ```bash
    <PathToFile>/com.microsoft.network-extension.mobileconfig: OK
    ```

3. Følg vejledningen på denne [side for](https://www.jamf.com/jamf-nation/articles/649/creating-a-signing-certificate-using-jamf-pro-s-built-in-certificate-authority) at oprette et signeringscertifikat ved hjælp af SYLFFs indbyggede nøglecenter.

4. Når certifikatet er oprettet og installeret på din enhed, skal du køre følgende kommando fra Terminalen for at signere filen:

    ```bash
    $ security cms -S -N "<CertificateName>" -i <PathToFile>/com.microsoft.network-extension.mobileconfig -o <PathToSignedFile>/com.microsoft.network-extension.signed.mobileconfig
    ```

    Hvis certifikatnavnet f.eks. **er SigningCertificate** , og den signerede fil gemmes i Dokumenter:

    ```bash
    $ security cms -S -N "SigningCertificate" -i ~/Documents/com.microsoft.network-extension.mobileconfig -o ~/Documents/com.microsoft.network-extension.signed.mobileconfig
    ```

5. Fra SYLF-portalen skal du gå **til Konfigurationsprofiler** og klikke **på Upload**. Vælg, `com.microsoft.network-extension.signed.mobileconfig` når du bliver bedt om at angive filen.

## <a name="intune"></a>Intune

### <a name="intune-system-extensions-policy"></a>Intune politik for systemudvidelser

Sådan godkender du systemudvidelserne:

1. I Intune skal du åbne **Administrer** \> **enhedskonfiguration**. Vælg **Administrer** \> **profiler Opret** \> **profil**.
2. Vælg et navn til profilen. Skift **Platform=macOS** **til Profiltype=Udvidelser**. Vælg **Opret**.
3. Giv denne `Basics` nye profil et navn under fanen.
4. `Configuration settings` Tilføj følgende elementer i sektionen under fanen`Allowed system extensions`:

   <br>

   ****

   |Bundle-id|Team-id|
   |---|---|
   |com.microsoft.wdav.epsext|UBF8T346G9|
   |com.microsoft.wdav.netext|UBF8T346G9|
   |||

   :::image type="content" source="images/mac-system-extension-intune2.png" alt-text=" Siden Systemkonfigurationsprofiler" lightbox="images/mac-system-extension-intune2.png":::

5. På fanen `Assignments` skal du tildele denne profil til **Alle brugere & Alle enheder**.
6. Gennemse og opret denne konfigurationsprofil.

### <a name="create-and-deploy-the-custom-configuration-profile"></a>Oprette og installere den brugerdefinerede konfigurationsprofil

Følgende konfigurationsprofil aktiverer netværksudvidelsen og giver fuld diskadgang til slutpunktssikkerhedssystemudvidelsen.

Gem følgende indhold i en fil med **navnetsysext.xml**:

```xml
<?xml version="1.0" encoding="UTF-8"?><!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft Corporation</string>
        <key>PayloadIdentifier</key>
        <string>7E53AC50-B88D-4132-99B6-29F7974EAA3C</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender System Extensions</string>
        <key>PayloadDescription</key>
        <string/>
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
                <string>2BA070D9-2233-4827-AFC1-1F44C8C8E527</string>
                <key>PayloadType</key>
                <string>com.apple.webcontent-filter</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>CEBF7A71-D9A1-48BD-8CCF-BD9D18EC155A</string>
                <key>PayloadDisplayName</key>
                <string>Approved Network Extension</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>FilterType</key>
                <string>Plugin</string>
                <key>UserDefinedName</key>
                <string>Microsoft Defender Network Extension</string>
                <key>PluginBundleID</key>
                <string>com.microsoft.wdav</string>
                <key>FilterSockets</key>
                <true/>
                <key>FilterDataProviderBundleIdentifier</key>
                <string>com.microsoft.wdav.netext</string>
                <key>FilterDataProviderDesignatedRequirement</key>
                <string>identifier &quot;com.microsoft.wdav.netext&quot; and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
            </dict>
            <dict>
                <key>PayloadUUID</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadType</key>
                <string>com.apple.TCC.configuration-profile-policy</string>
                <key>PayloadOrganization</key>
                <string>Microsoft Corporation</string>
                <key>PayloadIdentifier</key>
                <string>56105E89-C7C8-4A95-AEE6-E11B8BEA0366</string>
                <key>PayloadDisplayName</key>
                <string>Privacy Preferences Policy Control</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>Services</key>
                <dict>
                    <key>SystemPolicyAllFiles</key>
                    <array>
                        <dict>
                            <key>Identifier</key>
                            <string>com.microsoft.wdav.epsext</string>
                            <key>CodeRequirement</key>
                            <string>identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9</string>
                            <key>IdentifierType</key>
                            <string>bundleID</string>
                            <key>StaticCode</key>
                            <integer>0</integer>
                            <key>Allowed</key>
                            <integer>1</integer>
                        </dict>
                    </array>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

Kontrollér, at den ovenstående fil blev kopieret korrekt. Fra Terminalen skal du køre følgende kommando og kontrollere, at dens output:`OK`

```bash
$ plutil -lint sysext.xml
sysext.xml: OK
```

Sådan installerer du denne brugerdefinerede konfigurationsprofil:

1. I Intune skal du åbne **Administrer** \> **enhedskonfiguration**. Vælg **Administrer** \> **profiler Opret** \> **profil**.
2. Vælg et navn til profilen. Skift **Platform=macOS** og **Profiltype=Brugerdefineret**. Vælg **Konfigurer**.
3. Åbn konfigurationsprofilen, og **overførsysext.xml**. Denne fil blev oprettet i det foregående trin.
4. Vælg **OK**.

   :::image type="content" source="images/mac-system-extension-intune.png" alt-text="Systemudvidelsen på Intune side" lightbox="images/mac-system-extension-intune.png":::

5. På fanen `Assignments` skal du tildele denne profil til **Alle brugere & Alle enheder**.
6. Gennemse og opret denne konfigurationsprofil.
