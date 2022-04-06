---
title: Installér Microsoft Defender for Endpoint i iOS-funktioner
description: Beskrivelse af, hvordan du Microsoft Defender for Endpoint på ikke-tilmeldte iOS-enheder.
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, configure, features, ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: sunasing
author: sunasing
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: b1945059147f87499d131d241c74aaca749fb6e7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474107"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Installér Microsoft Defender for Endpoint på ikke-tilmeldte iOS-enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender til Slutpunkt på iOS bruger et VPN for at levere webbeskyttelsesfunktionen. Dette er ikke et almindeligt VPN og er et lokalt/selvløkkende VPN, der ikke tager trafik uden for enheden.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Konfigurer Microsoft Defender for Endpoint risikosignaler i appbeskyttelsespolitik (MAM)

Microsoft Defender for Endpoint på iOS, som allerede beskytter virksomhedsbrugere på MdM-scenarier (Mobile Enhedshåndtering), understøtter nu administration af mobilapps (MAM – Mobile App Management) for enheder, der ikke er tilmeldt Intune administration af mobilenheder (MDM). Det udvider også denne support til kunder, der bruger andre enterprise mobility management-løsninger, mens de stadig bruger Intune til administration af mobilapps (MAM). Denne funktion giver dig mulighed for at administrere og beskytte din organisations data i et program.

Microsoft Defender for Endpoint oplysninger om iOS-trusler udnyttes af Intune politikker for appbeskyttelse for at beskytte disse apps. Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. Et administreret program har anvendt politikker for appbeskyttelse og kan administreres af Intune.  

Microsoft Defender for Endpoint på iOS understøtter begge konfigurationer af MAM
- **Intune MDM + MAM**: It-administratorer kan kun administrere apps ved hjælp af politikker for appbeskyttelse på enheder, der er tilmeldt Intune administration af mobilenheder (MDM).
- **MAM uden enhedsregistrering**: MAM uden enhedsregistrering eller MAM-WE giver it-administratorer mulighed for at administrere apps ved hjælp af [politikker for appbeskyttelse](/mem/intune/app/app-protection-policy) på enheder, der ikke er tilmeldt Intune MDM. Det betyder, at apps kan administreres Intune enheder, der er tilmeldt tredjeparts EMM-udbydere. For at administrere apps, der bruger begge ovenstående konfigurationer, skal Intune i [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431)

For at aktivere denne funktion skal en administrator konfigurere forbindelsen mellem Microsoft Defender for Endpoint og Intune, oprette beskyttelsespolitikken for apps og anvende politikken på målrettede enheder og programmer. 
 
Slutbrugere skal også tage skridt til at installere Microsoft Defender for Endpoint på deres enhed og aktivere onboardingflowet.

### <a name="pre-requisites"></a>Forudsætninger

1. **Kontrollér, at forbindelsen er aktiveret**. <br> På den [samlede sikkerhedskonsol skal](https://security.microsoft.com) du gå **til Indstillinger** >  **Endpoints** >  **Avancerede** funktioner og sikre, **at Microsoft Intune er** aktiveret.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Defender for Endpoint – Intune forbindelse" lightbox="images/enable-intune-connection.png":::

  
2. **Kontrollér, at forbindelsen er aktiveret på Intune portal**. <br> I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **Slutpunktssikkerhed** >  **Microsoft Defender for Endpoint** og sikre, at Forbindelsesstatus er aktiveret.

  :::image type="content" source="images/app-settings.png" alt-text="Programindstillingerne" lightbox="images/app-settings.png":::

### <a name="create-an-app-protection-policy"></a>Opret en politik for appbeskyttelse
 
Bloker adgang til eller sletning af data i en administreret app baseret på Microsoft Defender for Endpoint risikosignaler ved at oprette en politik for appbeskyttelse.
Microsoft Defender for Endpoint kan konfigureres til at sende trusselslyde, der skal bruges i politikker for appbeskyttelse (APP, også kaldet MAM). Med denne funktion kan du bruge en Microsoft Defender for Endpoint til at beskytte administrerede apps.

1. Opret en politik <br>
Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. En politik kan være en regel, der håndhæves, når brugeren forsøger at få adgang til eller flytte "virksomhedsdata" eller et sæt handlinger, der er forbudt eller overvåget, når brugeren er inde i appen. 

:::image type="content" source="images/create-policy.png" alt-text="Fanen Opret politik i menuelementet Appbeskyttelse Politikker" lightbox="images/create-policy.png":::

2. Tilføj apps <br>
    a. Vælg, hvordan du vil anvende denne politik på apps på forskellige enheder. Tilføj derefter mindst én app. <br>
    Brug denne indstilling til at angive, om denne politik gælder for enheder, der ikke er administrerede. Du kan også vælge at målrette din politik mod apps på enheder af en hvilken som helst administrationstilstand.
Da administration af mobilapps ikke kræver enhedshåndtering, kan du beskytte virksomhedsdata på både administrerede og ikke-administrerede enheder. Administrationen er centreret om brugeridentiteten, hvilket fjerner kravet til enhedshåndtering. Virksomheder kan bruge politikker for appbeskyttelse med eller uden MDM på samme tid. Tænk f.eks. på en medarbejder, der både bruger en telefon udstedt af virksomheden og deres egen personlige tablet. Virksomhedens telefon er tilmeldt MDM og beskyttet af politikker for appbeskyttelse, mens den personlige enhed kun er beskyttet af politikker for appbeskyttelse.

    b. Vælg Apps<br>
    En administreret app er en app, der har politikker for appbeskyttelse anvendt på den, og den kan administreres Intune. Alle apps, der er integreret med [INTUNE SDK](/mem/intune/developer/app-sdk) eller ombrudt af Intune App Wrapping Tool, [](/mem/intune/developer/apps-prepare-mobile-application-management) kan administreres ved hjælp Intune politikker for appbeskyttelse. Se den officielle liste over [Microsoft Intune beskyttede apps,](/mem/intune/apps/apps-supported-intune-apps) der er udviklet ved hjælp af disse værktøjer, og som er tilgængelige til offentlig brug.

    *Eksempel: Outlook som en administreret app*

     :::image type="content" source="images/managed-app.png" alt-text="Microsofts Outlook menupunkt i venstre navigationsrude" lightbox="images/managed-app.png":::
  

 3. Angiv sikkerhedskrav til logon for din beskyttelsespolitik. <br>
Vælg **Indstilling > maks. tilladte trusselsniveau for** enheder **under Enhedsbetingelser** , og angiv en værdi. Vælg derefter  **Handling: "Bloker adgang"**. Microsoft Defender for Endpoint på iOS deler dette Device Threat-niveau.

    
   :::image type="content" source="images/conditional-launch.png" alt-text="Ruden Enhedsbetingelser" lightbox="images/conditional-launch.png":::

4. Tildel brugergrupper, som politikken skal anvendes på.<br>
  Vælg **Inkluderede grupper**. Tilføj derefter de relevante grupper. 


Du kan finde flere oplysninger om MAM eller beskyttelsespolitik for apps under [Indstillinger for politik for beskyttelse af iOS-apps](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Installér Microsoft Defender for Endpoint til MAM eller på enheder, der ikke er tilmeldt

Microsoft Defender for Endpoint iOS aktiverer scenariet for beskyttelse af apps og er tilgængeligt i Apple App Store.

Når politikker for appbeskyttelse er konfigureret til apps til at medtage risikosignaler fra Microsoft Defender for Endpoint, bliver brugerne omdirigeret til at installere Microsoft Defender for Endpoint, når de bruger disse apps. Alternativt kan brugerne også installere den nyeste version af appen direkte fra Apple App Store.
