---
title: Konfigurer Microsoft Defender for Endpoint på Android-funktioner
description: Beskriver, hvordan du konfigurerer Microsoft Defender for Endpoint på Android
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
ms.openlocfilehash: 0e0a8a99444f09d58a43502edd1c94e4cce52301
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664672"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Konfigurer Defender for Endpoint på Android-funktioner

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Betinget adgang med Defender for Endpoint på Android

Microsoft Defender for Endpoint på Android sammen med Microsoft Intune og Azure Active Directory gør det muligt at gennemtvinge enhedsoverholdelse og politikker for betinget adgang baseret på enhedens risikoniveauer. Defender for Endpoint er en MTD-løsning (Mobile Threat Defense), som du kan udrulle for at udnytte denne funktionalitet via Intune.

Du kan finde flere oplysninger om, hvordan du konfigurerer Defender for Endpoint på Android og betinget adgang, under [Defender for Endpoint og Intune](/mem/intune/protect/advanced-threat-protection).

## <a name="configure-custom-indicators"></a>Konfigurer brugerdefinerede indikatorer

> [!NOTE]
> Defender for Endpoint på Android understøtter kun oprettelse af brugerdefinerede indikatorer for IP-adresser og URL-adresser/domæner.

Defender for Endpoint på Android gør det muligt for administratorer at konfigurere brugerdefinerede indikatorer, så de også understøtter Android-enheder. Du kan få mere at vide om, hvordan du konfigurerer brugerdefinerede indikatorer, under [Administrer indikatorer](manage-indicators.md).

## <a name="configure-web-protection"></a>Konfigurer webbeskyttelse
Defender for Endpoint på Android giver it-administratorer mulighed for at konfigurere webbeskyttelsesfunktionen. Denne funktion er tilgængelig i Microsoft Endpoint Manager Administration.

> [!NOTE]
> Defender for Endpoint på Android ville bruge en VPN-forbindelse for at levere webbeskyttelsesfunktionen. Dette er ikke en almindelig VPN- og er en lokal/selv-løkke-VPN, der ikke tager trafik uden for enheden.
> Du kan få flere oplysninger under [Konfigurer webbeskyttelse på enheder, der kører Android](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="privacy-controls"></a>Kontrolelementer til beskyttelse af personlige oplysninger

> [!IMPORTANT]
> Kontrolelementer til beskyttelse af personlige oplysninger for Microsoft Defender for Endpoint på Android fås som prøveversion. Følgende oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Følgende kontrolelementer til beskyttelse af personlige oplysninger er tilgængelige til konfiguration af de data, der sendes af Defender for Endpoint fra Android-enheder:

|Trusselsrapport     |Detaljer      |
|--------------------|-------------|
|Malwarerapport |Administratorer kan konfigurere kontrolelementet til beskyttelse af personlige oplysninger for malwarerapport – Hvis beskyttelse af personlige oplysninger er aktiveret, sender Defender for Endpoint ikke navnet på malwareappen og andre appoplysninger som en del af rapporten med malwarebeskeder |
|Phish-rapport |Administratorer kan konfigurere kontrolelementet til beskyttelse af personlige oplysninger for phishrapport – Hvis beskyttelse af personlige oplysninger er aktiveret, sender Defender for Endpoint ikke domænenavnet og oplysningerne om det usikre websted som en del af phish-beskedrapporten |
|Vurdering af sårbarheder for apps (kun Android) |Som standard sendes der kun oplysninger om de apps, der er installeret i arbejdsprofilen, til vurdering af sårbarheder. Administratorer kan deaktivere beskyttelse af personlige oplysninger for at inkludere personlige apps|

## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>Konfigurer vurdering af sårbarheder for apps til BYOD-enheder

Fra version 1.0.3425.0303 af Microsoft Defender for Endpoint på Android kan du køre sårbarhedsvurderinger af OS og apps, der er installeret på de onboardede mobilenheder.

> [!NOTE]
> Vurdering af sårbarheder er en del af [administration af trusler og sårbarheder](next-gen-threat-and-vuln-mgt.md) i Microsoft Defender for Endpoint. 

**Noter om beskyttelse af personlige oplysninger for apps fra personlige enheder (BYOD):**

- For Android Enterprise med en arbejdsprofil understøttes kun apps, der er installeret på arbejdsprofilen.
- I andre BYOD-tilstande aktiveres vurdering af sårbarheder som standard **ikke** for apps. Men når enheden er i administratortilstand, kan administratorer eksplicit aktivere denne funktion via Microsoft Endpoint Manager for at få vist listen over apps, der er installeret på enheden. Du kan finde flere oplysninger i detaljer nedenfor.

### <a name="configure-privacy-for-device-administrator-mode"></a>Konfigurer beskyttelse af personlige oplysninger for enhedens administratortilstand

Brug følgende trin til at **aktivere vurdering af sårbarheder for apps** fra enheder i **enhedsadministratortilstand** for målrettede brugere. 

> [!NOTE]
> Denne indstilling er som standard slået fra for de enheder, der er tilmeldt enhedens administratortilstand.

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **EnhederKonfigurationsprofilerOpret** >  >  **profil**, og angiv følgende indstillinger:

   - **Platform**: Vælg Android-enhedsadministrator
   - **Profil**: Vælg "Brugerdefineret", og klik på Opret

2. I afsnittet **Grundlæggende** skal du angive et navn og en beskrivelse af profilen.

3. Under **Konfigurationsindstillinger** skal du vælge Tilføj **OMA-URI-indstilling** :

   - **Navn**: Angiv et entydigt navn og en beskrivelse til denne OMA-URI-indstilling, så du nemt kan finde den senere.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Datatype: Vælg Heltal på rullelisten.
   - Værdi: Angiv 0 for at deaktivere indstillingen for beskyttelse af personlige oplysninger (værdien er som standard 1)

4. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Konfigurer beskyttelse af personlige oplysninger for Android Enterprise-arbejdsprofil

Defender for Endpoint understøtter vurdering af sårbarheder for apps i arbejdsprofilen. Hvis du vil slå denne funktion fra for målrettede brugere, kan du dog bruge følgende trin:

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **AppsAppkonfigurationspolitikkerAddAdministrerede** >  >  >  **enheder**.
2. Giv politikken et navn. **Platform > Android Enterprise**; vælg profiltypen.
3. Vælg **Microsoft Defender for Endpoint** som destinationsapp.
4. På siden Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderTVMPrivacyMode** som nøgle- og værditype som **Heltal**
   - Hvis du vil deaktivere sårbarheder for apps i arbejdsprofilen, skal du angive værdi som `1` og tildele denne politik til brugere. Denne værdi er som standard angivet til `0`.
   - For brugere med nøgle angivet som `0`sender Defender for Endpoint listen over apps fra arbejdsprofilen til backendtjenesten med henblik på vurdering af sårbarheder.
5. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du slår ovenstående kontrolelementer til beskyttelse af personlige oplysninger til eller fra, påvirker det ikke kontrollen af enhedens overholdelse eller betinget adgang.

## <a name="configure-privacy-for-phishing-alert-report"></a>Konfigurer rapporten om beskyttelse af personlige oplysninger for phishingbeskeder

Kontrolelementet til beskyttelse af personlige oplysninger for phish-rapporten kan bruges til at deaktivere samlingen af domænenavne eller webstedsoplysninger i phish threat-rapporten. Dette giver organisationer fleksibiliteten til at vælge, om de vil indsamle domænenavnet, når et skadeligt eller phish-websted registreres og blokeres af Defender for Endpoint.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Konfigurer rapporten om beskyttelse af personlige oplysninger for phishingbeskeder på enheder, der er tilmeldt af Android-enhedsadministratorer:

Brug følgende trin til at slå den til for målrettede brugere:

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **EnhederKonfigurationsprofilerOpret** >  >  **profil**, og angiv følgende indstillinger:

   - **Platform**: Vælg Android-enhedsadministrator.
   - **Profil**: Vælg "Brugerdefineret", og klik på **Opret**.

2. I afsnittet **Grundlæggende** skal du angive et navn og en beskrivelse af profilen.

3. Under **Konfigurationsindstillinger** skal du vælge Tilføj **OMA-URI-indstilling** :

   - **Navn**: Angiv et entydigt navn og en beskrivelse til denne OMA-URI-indstilling, så du nemt kan finde den senere.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Datatype: Vælg Heltal på rullelisten.
   - Værdi: Angiv 1 for at aktivere indstillingen for beskyttelse af personlige oplysninger. Standardværdien er 0.

4. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

Brug af dette kontrolelement til beskyttelse af personlige oplysninger påvirker ikke kontrollen af enhedens overholdelse af angivne standarder eller betinget adgang.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Konfigurer rapport om beskyttelse af personlige oplysninger for phishingbeskeder på Android Virksomhedsarbejdsprofil

Brug følgende trin til at aktivere beskyttelse af personlige oplysninger for målrettede brugere i arbejdsprofilen:

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **AppsAppkonfigurationspolitikkerAddAdministrerede** >  >  >  **enheder**.
2. Giv politikken et navn, **Platform > Android Enterprise**, vælg profiltypen.
3. Vælg **Microsoft Defender for Endpoint** som destinationsapp.
4. På Indstillinger side skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderExcludeURLInReport** som nøgle- og værditypen som **Heltal**.
   - Angiv **1 for at aktivere beskyttelse af personlige oplysninger**. Standardværdien er 0.
5. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

Hvis du slår ovenstående kontrolelementer til beskyttelse af personlige oplysninger til eller fra, påvirker det ikke kontrollen af enhedens overholdelse eller betinget adgang.

## <a name="configure-privacy-for-malware-threat-report"></a>Konfigurer beskyttelse af personlige oplysninger for malwaretrusselrapport

Kontrolelementet til beskyttelse af personlige oplysninger for malwaretrusselrapporter kan bruges til at deaktivere indsamlingen af appoplysninger (navn og pakkeoplysninger) fra malwaretrusselrapporten. Dette giver organisationer fleksibiliteten til at vælge, om de vil indsamle appnavnet, når der registreres en skadelig app.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Konfigurer rapporten over beskeder om beskyttelse af personlige oplysninger for malware på de enheder, der er tilmeldt af Android-enhedsadministratoren:

Brug følgende trin til at slå den til for målrettede brugere:

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **EnhederKonfigurationsprofilerOpret** >  >  **profil**, og angiv følgende indstillinger:

   - **Platform**: Vælg Android-enhedsadministrator.
   - **Profil**: Vælg "Brugerdefineret", og klik på **Opret**.

2. I afsnittet **Grundlæggende** skal du angive et navn og en beskrivelse af profilen.

3. Under **Konfigurationsindstillinger** skal du vælge Tilføj **OMA-URI-indstilling** :

   - **Navn**: Angiv et entydigt navn og en beskrivelse til denne OMA-URI-indstilling, så du nemt kan finde den senere.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Datatype: Vælg Heltal på rullelisten.
   - Værdi: Angiv 1 for at aktivere indstillingen for beskyttelse af personlige oplysninger. Standardværdien er 0.

4. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

Brug af dette kontrolelement til beskyttelse af personlige oplysninger påvirker ikke kontrollen af enhedens overholdelse af angivne standarder eller betinget adgang. Enheder med en skadelig app vil f.eks. altid have risikoniveauet "Mellem".

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Konfigurer rapport om beskyttelse af personlige oplysninger for malwarebeskeder på Android Enterprise-arbejdsprofil

Brug følgende trin til at aktivere beskyttelse af personlige oplysninger for målrettede brugere i arbejdsprofilen:

1. I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431), og gå til **AppsAppkonfigurationspolitikkerAddAdministrerede** >  >  >  **enheder**.
2. Giv politikken et navn, **Platform > Android Enterprise**, vælg profiltypen.
3. Vælg **Microsoft Defender for Endpoint** som destinationsapp.
4. På siden Indstillinger skal du vælge **Brug konfigurationsdesigner** og tilføje **DefenderExcludeAppInReport** som nøgle- og værditypen som **Heltal**
   - Angiv **1 for at aktivere beskyttelse af personlige oplysninger**. Standardværdien er 0.
5. Klik på **Næste** , og tildel denne profil til målrettede enheder/brugere.

Brug af dette kontrolelement til beskyttelse af personlige oplysninger påvirker ikke kontrollen af enhedens overholdelse af angivne standarder eller betinget adgang. Enheder med en skadelig app vil f.eks. altid have risikoniveauet "Mellem".

## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
- [Installér Microsoft Defender for Endpoint på Android med Microsoft Intune](android-intune.md)
