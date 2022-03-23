---
title: Installer Microsoft Defender til Slutpunkt på iOS-funktioner
description: Beskrivelse af, hvordan du installerer Microsoft Defender til Slutpunkt på ikke-tilmeldte iOS-enheder.
keywords: microsoft, defender, Microsoft Defender til Endpoint, ios, configure, features, ios
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
ms.openlocfilehash: 082e03100c366294a193d5fc7eb3cf0dd868caa6
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63593355"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Installer Microsoft Defender til Slutpunkt på ikke-tilmeldte iOS-enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender til Slutpunkt på iOS bruger et VPN for at levere webbeskyttelsesfunktionen. Dette er ikke et almindeligt VPN og er et lokalt/selvløkkende VPN, der ikke tager trafik uden for enheden.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Konfigurer risikosignaler for Microsoft Defender til slutpunkt i appbeskyttelsespolitik (MAM)

Microsoft Defender til slutpunkt på iOS, som allerede beskytter virksomhedsbrugere på scenarier med administration af mobilenheder (MDM), understøtter nu administration af mobilapps (MAM – Mobile App Management) for enheder, der ikke er tilmeldt Ved hjælp af Administration af intune-mobilenheder (MDM). Det udvider også denne support til kunder, der bruger andre enterprise mobility management-løsninger, mens de stadig bruger Intune til administration af mobilapps (MAM). Denne funktion giver dig mulighed for at administrere og beskytte din organisations data i et program.

Microsoft Defender til Slutpunkt på iOS-trusselsoplysninger udnyttes af Intune-politikker for appbeskyttelse for at beskytte disse apps. Appbeskyttelsespolitikker er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. Et administreret program har anvendte politikker for appbeskyttelse og kan administreres af Intune.  

Microsoft Defender til slutpunkt på iOS understøtter begge konfigurationer af MAM
- **Intune MDM + MAM**: It-administratorer kan kun administrere apps ved hjælp af politikker for appbeskyttelse på enheder, der er tilmeldt Intune administration af mobilenheder (MDM).
- **MAM uden tilmelding til** enhed: MAM uden enhedsregistrering eller MAM-WE giver it-administratorer mulighed for at administrere apps ved hjælp af [politikker for appbeskyttelse](/mem/intune/app/app-protection-policy) på enheder, der ikke er tilmeldt Intune MDM. Det betyder, at apps kan administreres af Intune på enheder, der er tilmeldt tredjeparts EMM-udbydere. Kunder, der administrerer apps, der bruger begge ovenstående konfigurationer, skal bruge Intune [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431)

For at aktivere denne funktion skal en administrator konfigurere forbindelsen mellem Microsoft Defender til slutpunkt og Intune, oprette beskyttelsespolitikken for apps og anvende politikken på målrettede enheder og programmer. 
 
Slutbrugere skal også tage skridt til at installere Microsoft Defender for Endpoint på deres enhed og aktivere onboardingflowet.

### <a name="pre-requisites"></a>Forudsætninger

1. **Kontrollér, at forbindelsen er aktiveret**. <br> På den [samlede sikkerhedskonsol skal](https://security.microsoft.com) du gå **til Indstillinger** >  **Endpoints** >  **Avancerede** funktioner og sikre, **at Microsoft Intune er** aktiveret.

  ![Billede af Defender til forbindelsespunktet Endpoint -Intune](images/enable-intune-connection.png)
  
2. **Kontrollér, at forbindelsen er aktiveret på Intune-portalen**. <br> I [Microsoft Endpoint Manager Administration skal](https://go.microsoft.com/fwlink/?linkid=2109431) du gå til **Endpoint SecurityMicrosoft** >  **Defender til slutpunkt og** sikre, at Forbindelsesstatus er aktiveret.

  ![Appindstillinger](images/app-settings.png)

### <a name="create-an-app-protection-policy"></a>Opret en politik for appbeskyttelse
 
Bloker adgang til eller sletning af data i en administreret app, der er baseret på risikosignaler for Microsoft Defender til Slutpunkt, ved at oprette en politik for appbeskyttelse.
Microsoft Defender til slutpunkt kan konfigureres til at sende trusselssignaler, der skal bruges i politikker for appbeskyttelse (APP, også kaldet MAM). Med denne funktion kan du bruge Microsoft Defender til Slutpunkt til at beskytte administrerede apps.

1. Opret en politik <br>
Appbeskyttelsespolitikker er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. En politik kan være en regel, der håndhæves, når brugeren forsøger at få adgang til eller flytte "virksomhedsdata" eller et sæt handlinger, der er forbudt eller overvåget, når brugeren er inde i appen. 

![Billede af oprettelse af politik](images/create-policy.png)

2. Tilføj apps <br>
    a. Vælg, hvordan du vil anvende denne politik på apps på forskellige enheder. Tilføj derefter mindst én app. <br>
    Brug denne indstilling til at angive, om denne politik gælder for enheder, der ikke er administrerede. Du kan også vælge at målrette din politik mod apps på enheder af en hvilken som helst administrationstilstand.
Da administration af mobilapps ikke kræver enhedshåndtering, kan du beskytte virksomhedsdata på både administrerede og ikke-administrerede enheder. Administrationen er centreret om brugeridentiteten, hvilket fjerner kravet til enhedshåndtering. Virksomheder kan bruge politikker for appbeskyttelse med eller uden MDM på samme tid. Tænk f.eks. på en medarbejder, der både bruger en telefon udstedt af virksomheden og deres egen personlige tablet. Virksomhedens telefon er tilmeldt MDM og beskyttet af politikker for appbeskyttelse, mens den personlige enhed kun er beskyttet af politikker for appbeskyttelse.

    b. Vælg Apps<br>
    En administreret app er en app, der har politikker for beskyttelse af apps anvendt på den og kan administreres af Intune. Alle apps, der er integreret med [Intune SDK](/mem/intune/developer/app-sdk) eller ombrudt af [Intune-App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management), kan administreres ved hjælp af Intune-appbeskyttelsespolitikker. Se den officielle liste over [Microsoft Intune beskyttede apps,](/mem/intune/apps/apps-supported-intune-apps) der er udviklet ved hjælp af disse værktøjer, og som er tilgængelige til offentlig brug.

    *Eksempel: Outlook som en administreret app*

    ![Billede Outlook som administreret app](images/managed-app.png)

 3. Angiv sikkerhedskrav til logon for din beskyttelsespolitik. <br>
Vælg **Indstilling > maks. tilladte trusselsniveau for** enheder **under Enhedsbetingelser** , og angiv en værdi. Vælg derefter  **Handling: "Bloker adgang"**. Microsoft Defender til slutpunkt på iOS deler dette Device Threat-niveau.

    ![Billede af betinget start](images/conditional-launch.png)

4. Tildel brugergrupper, som politikken skal anvendes på.<br>
  Vælg **Inkluderede grupper**. Tilføj derefter de relevante grupper. 


Du kan finde flere oplysninger om MAM eller beskyttelsespolitik for apps under [Indstillinger for politik for beskyttelse af iOS-apps](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Installér Microsoft Defender til Slutpunkt for MAM eller på enheder, der ikke er tilmeldt

Microsoft Defender til Slutpunkt på iOS aktiverer scenariet for beskyttelsespolitik for apps og er tilgængelig i Apple App Store.

Når politikker for appbeskyttelse er konfigureret til apps til at medtage risikosignaler fra Microsoft Defender til slutpunkt, bliver brugerne omdirigeret til at installere Microsoft Defender til slutpunkt, når de bruger disse apps. Alternativt kan brugerne også installere den nyeste version af appen direkte fra Apple App Store.
