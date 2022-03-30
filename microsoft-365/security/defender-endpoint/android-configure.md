---
title: Konfigurer Microsoft Defender til slutpunkt på Android-funktioner
description: Beskrivelse af, hvordan du konfigurerer Microsoft Defender til slutpunkt på Android
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, konfiguration
ms.prod: m365-security
ms.mktglfcycl: deploy
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
ms.openlocfilehash: 22e0eed3becebdcb3dee4c31ddc7659651bac71f
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/03/2022
ms.locfileid: "63599295"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Konfigurer Defender til slutpunkt på Android-funktioner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Betinget adgang med Defender til slutpunkt på Android

Microsoft Defender til slutpunkt på Android sammen med Microsoft Intune og Azure Active Directory gør det muligt at gennemtvinge politikker for enhedsoverholdelse og Betinget adgang baseret på risikoniveauer for enheder. Defender til Slutpunkt er en MTD-løsning (Mobile Threat Defense), som du kan implementere for at anvende denne funktion via Intune.

Du kan finde flere oplysninger om, hvordan du konfigurerer Defender til Slutpunkt på Android og Betinget adgang, under [Defender til Slutpunkt og Intune](/mem/intune/protect/advanced-threat-protection).

## <a name="configure-custom-indicators"></a>Konfigurere brugerdefinerede indikatorer

> [!NOTE]
> Defender til Slutpunkt på Android understøtter kun oprettelse af brugerdefinerede indikatorer for IP-adresser og URL-adresser/domæner.

Defender til Slutpunkt på Android giver administratorer mulighed for at konfigurere brugerdefinerede indikatorer til også at understøtte Android-enheder. Du kan finde flere oplysninger om, hvordan du konfigurerer brugerdefinerede indikatorer, [under Administrere indikatorer](manage-indicators.md).

## <a name="configure-web-protection"></a>Konfigurere webbeskyttelse
Defender til Slutpunkt på Android giver it-administratorer mulighed for at konfigurere funktionen til webbeskyttelse. Denne funktion er tilgængelig i Microsoft Endpoint Manager Administration.

> [!NOTE]
> Defender til Slutpunkt på Android ville bruge et VPN for at levere funktionen Web Protection. Dette er ikke et almindeligt VPN og er et lokalt/selvløkkende VPN, der ikke tager trafik uden for enheden.
> Få mere at vide under [Konfigurer webbeskyttelse på enheder, der kører Android](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="privacy-controls"></a>Kontrolelementer til beskyttelse af personlige oplysninger

> [!IMPORTANT]
> Kontrolelementer til beskyttelse af personlige oplysninger for Microsoft Defender til Slutpunkt på Android er i forhåndsvisning. Følgende oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Følgende kontrolelementer til beskyttelse af personlige oplysninger er tilgængelige til konfiguration af de data, der sendes af Defender til Slutpunkt fra Android-enheder:

|Trusselsrapport     |Detaljer      |
|--------------------|-------------|
|Malwarerapport |Administratorer kan konfigurere kontrol af beskyttelse af personlige oplysninger for malwarerapport – Hvis beskyttelse af personlige oplysninger er aktiveret, vil Defender til Endpoint ikke sende navnet på malware-appen og andre appoplysninger som en del af rapporten om malwarebeskeder |
|Rapporten Phish |Administratorer kan konfigurere beskyttelse af personlige oplysninger for phish-rapport – Hvis beskyttelse af personlige oplysninger er aktiveret, sender Defender til Endpoint ikke domænenavnet og oplysningerne på det usikre websted som en del af rapporten om phish-besked |
|Vurdering af sikkerhedsrisiko i apps (kun Android) |Som standard er det kun oplysninger om apps, der er installeret i arbejdsprofilen, der sendes til vurdering af sikkerhedsrisiko. Administratorer kan deaktivere beskyttelse af personlige oplysninger, så de inkluderer personlige apps|

## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>Konfigurer vurdering af sikkerhedsrisiko for apps til BYOD-enheder

Fra version 1.0.3425.0303 af Microsoft Defender til slutpunkt på Android vil du kunne køre sikkerhedsrisikovurderinger af OS og apps, der er installeret på onboardede mobilenheder.

> [!NOTE]
> Vurdering af sikkerhedsrisiko er en [del af administrationen af trussel og](next-gen-threat-and-vuln-mgt.md) sikkerhedsrisiko i Microsoft Defender til slutpunkt. 

**Noter om beskyttelse af personlige oplysninger i forbindelse med apps fra personlige enheder (BYOD):**

- I Android Enterprise med en arbejdsprofil er det kun apps, der er installeret på arbejdsprofilen, der understøttes.
- For andre BYOD-tilstande er sikkerhedsrisikovurdering af apps som standard **ikke aktiveret** . Men når enheden er i administratortilstand, kan administratorer eksplicit aktivere denne funktion via Microsoft Endpoint Manager at få listen over apps installeret på enheden. Du kan få mere at vide under detaljer nedenfor.

### <a name="configure-privacy-for-device-administrator-mode"></a>Konfigurere beskyttelse af personlige oplysninger for enhedens administratortilstand

Brug følgende trin til at **aktivere sikkerhedsrisikovurdering af apps fra enheder** i **enhedstilstand** for målrettede brugere. 

> [!NOTE]
> Dette er som standard slået fra for enheder, der er tilmeldt enhed administratortilstand.

1. I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **EnhederKonfigurationsprofilerOprette** >  >  **profil** og angive følgende indstillinger:

   - **Platform**: Vælg administrator for Android-enheder
   - **Profil**: Vælg "Brugerdefineret", og klik på Opret

2. Angiv **et navn og** en beskrivelse af profilen i sektionen Grundlæggende.

3. Vælg Tilføj **OMA-URI-indstilling under Konfigurationsindstillinger**:

   - **Navn**: Angiv et entydigt navn og en beskrivelse af denne OMA-URI-indstilling, så du nemt kan finde den senere.
   - OMA-URI: **./vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Datatype: Vælg Heltal på rullelisten.
   - Værdi: Angiv 0 for at deaktivere indstillingen for beskyttelse af personlige oplysninger (værdien er som standard 1)

4. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Konfigurere beskyttelse af personlige oplysninger for Android Enterprise-arbejdsprofil

Defender til Slutpunkt understøtter vurdering af sikkerhedsrisiko i apps på arbejdsprofilen. Men hvis du vil deaktivere denne funktion for målrettede brugere, kan du bruge følgende trin:

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå **til Konfigurationspolitikker** **for** AppsAppAddManaged-enheder > . >  > 
2. Giv politikken et navn; **Platform > Android Enterprise**; skal du vælge profiltypen.
3. Vælg **Microsoft Defender til slutpunkt** som destinationsappen.
4. På Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderTVMPrivacyMode** som tasten og værditypen **som Heltal**
   - For at deaktivere sikkerhedsrisikoen for apps i arbejdsprofilen skal du angive værdi som `1` og tildele denne politik til brugerne. Denne værdi er som standard angivet til `0`.
   - For brugere med nøgle angivet som `0`, sender Defender til Endpoint listen over apps fra arbejdsprofilen til backendtjenesten af sikkerhedsvurdering.
5. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du slår ovenstående kontrolelementer til beskyttelse af personlige oplysninger til eller fra, påvirker det ikke kontrol af enhedsoverholdelse eller betinget adgang.

## <a name="configure-privacy-for-phishing-alert-report"></a>Konfigurere beskyttelse af personlige oplysninger for phishingbeskeder

Beskyttelse af personlige oplysninger for rapporten Phish kan bruges til at deaktivere samlingen af domænenavne eller webstedsoplysninger i rapporten om phish-trusler. Dette giver organisationer fleksibilitet til at vælge, om de vil indsamle domænenavnet, når et skadeligt eller phish-websted registreres og blokeres af Defender til Slutpunkt.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Konfigurer beskyttelse af personlige oplysninger for phishingbeskedrapport på enheder, der er tilmeldt Android-enheder:

Brug følgende trin til at aktivere det for målrettede brugere:

1. I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **EnhederKonfigurationsprofilerOprette** >  >  **profil** og angive følgende indstillinger:

   - **Platform**: Vælg Administrator for Android-enheder.
   - **Profil**: Vælg "Brugerdefineret", og klik på **Opret**.

2. Angiv **et navn og** en beskrivelse af profilen i sektionen Grundlæggende.

3. Vælg Tilføj **OMA-URI-indstilling under Konfigurationsindstillinger**:

   - **Navn**: Angiv et entydigt navn og en beskrivelse af denne OMA-URI-indstilling, så du nemt kan finde den senere.
   - OMA-URI: **./vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Datatype: Vælg Heltal på rullelisten.
   - Værdi: Angiv 1 for at aktivere indstillingen for beskyttelse af personlige oplysninger. Standardværdien er 0.

4. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du bruger dette kontrolelement til beskyttelse af personlige oplysninger, påvirker det ikke enhedsoverholdelseskontrollen eller den betingede adgang.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Konfigurere beskyttelse af personlige oplysninger for rapporten om phishingbesked på Android Enterprise-arbejdsprofilen

Brug følgende trin til at aktivere beskyttelse af personlige oplysninger for målrettede brugere i arbejdsprofilen:

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå **til Konfigurationspolitikker** **for** AppsAppAddManaged-enheder > . >  > 
2. Giv politikken et navn, **Platform > Android Enterprise**, vælg profiltypen.
3. Vælg **Microsoft Defender til slutpunkt** som destinationsappen.
4. På Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderExcludeURLInReport** som nøgle- og værditype **som Heltal**.
   - Angiv **1 for at aktivere beskyttelse af personlige oplysninger**. Standardværdien er 0.
5. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du slår ovenstående kontrolelementer til beskyttelse af personlige oplysninger til eller fra, påvirker det ikke kontrol af enhedsoverholdelse eller betinget adgang.

## <a name="configure-privacy-for-malware-threat-report"></a>Konfigurere beskyttelse af personlige oplysninger for malwaretrusler

Kontrol af beskyttelse af personlige oplysninger for malwaretrusler kan bruges til at deaktivere samlingen af appoplysninger (navn og pakkeoplysninger) fra rapporten over malwaretrusler. Dette giver organisationer fleksibilitet til at vælge, om de vil indsamle appnavnet, når der registreres en skadelig app.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Konfigurer rapport om beskyttelse af personlige oplysninger for malware på enheder, der er tilmeldt Android-enheder:

Brug følgende trin til at aktivere det for målrettede brugere:

1. I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **EnhederKonfigurationsprofilerOprette** >  >  **profil** og angive følgende indstillinger:

   - **Platform**: Vælg Administrator for Android-enheder.
   - **Profil**: Vælg "Brugerdefineret", og klik på **Opret**.

2. Angiv **et navn og** en beskrivelse af profilen i sektionen Grundlæggende.

3. Vælg Tilføj **OMA-URI-indstilling under Konfigurationsindstillinger**:

   - **Navn**: Angiv et entydigt navn og en beskrivelse af denne OMA-URI-indstilling, så du nemt kan finde den senere.
   - OMA-URI: **./vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Datatype: Vælg Heltal på rullelisten.
   - Værdi: Angiv 1 for at aktivere indstillingen for beskyttelse af personlige oplysninger. Standardværdien er 0.

4. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du bruger dette kontrolelement til beskyttelse af personlige oplysninger, påvirker det ikke enhedsoverholdelseskontrollen eller den betingede adgang. Enheder med en skadelig app vil f.eks. altid have et risikoniveau på "Mellem".

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Konfigurere rapport om beskyttelse af personlige oplysninger for malware på Android Enterprise-arbejdsprofil

Brug følgende trin til at aktivere beskyttelse af personlige oplysninger for målrettede brugere i arbejdsprofilen:

1. I [Microsoft Endpoint Manager Administration skal du](https://go.microsoft.com/fwlink/?linkid=2109431) gå **til Konfigurationspolitikker** **for** AppsAppAddManaged-enheder > . >  > 
2. Giv politikken et navn, **Platform > Android Enterprise**, vælg profiltypen.
3. Vælg **Microsoft Defender til slutpunkt** som destinationsappen.
4. På Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderExcludeAppInReport** som nøgle- og værditype **som Heltal**
   - Angiv **1 for at aktivere beskyttelse af personlige oplysninger**. Standardværdien er 0.
5. Klik **på Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du bruger dette kontrolelement til beskyttelse af personlige oplysninger, påvirker det ikke enhedsoverholdelseskontrollen eller den betingede adgang. Enheder med en skadelig app vil f.eks. altid have et risikoniveau på "Mellem".

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender til slutpunkt på Android](microsoft-defender-endpoint-android.md)
- [Installér Microsoft Defender til slutpunkt på Android med Microsoft Intune](android-intune.md)
