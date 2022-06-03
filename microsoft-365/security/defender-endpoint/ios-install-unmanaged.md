---
title: Udrul Microsoft Defender for Endpoint på iOS-funktioner
description: Beskriver, hvordan du installerer Microsoft Defender for Endpoint på ikke-tilmeldte iOS-enheder.
keywords: microsoft, defender, Microsoft Defender for Endpoint, ios, konfigurer, funktioner, ios
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
ms.openlocfilehash: 1d05f515ef1f2badcb6ba0bde69daa3fa2677434
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873506"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-unenrolled-ios-devices"></a>Installér Microsoft Defender for Endpoint på ikke-tilmeldte iOS-enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> Defender for Endpoint på iOS bruger en VPN-forbindelse til at levere webbeskyttelsesfunktionen. Dette er ikke en almindelig VPN- og er en lokal/selv-løkke-VPN, der ikke tager trafik uden for enheden.

## <a name="configure-microsoft-defender-for-endpoint-risk-signals-in-app-protection-policy-mam"></a>Konfigurer Microsoft Defender for Endpoint risikosignaler i MAM (App Protection Policy)

Microsoft Defender for Endpoint på iOS, som allerede beskytter virksomhedsbrugere på MOBILE Enhedshåndtering(MDM)-scenarier, udvider nu support til MAM (Mobile App Management) for enheder, der ikke er tilmeldt ved hjælp af Intune administration af mobilenheder (MDM). Denne support udvides også til kunder, der bruger andre løsninger til administration af virksomhedsmobilitet, mens de stadig bruger Intune til administration af mobilapps (MAM). Denne funktion giver dig mulighed for at administrere og beskytte din organisations data i et program.

Microsoft Defender for Endpoint på iOS-trusselsoplysninger udnyttes af Intune politikker for appbeskyttelse for at beskytte disse apps. Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller findes i en administreret app. Et administreret program har anvendt politikker for appbeskyttelse og kan administreres af Intune.  

Microsoft Defender for Endpoint på iOS understøtter begge konfigurationer af MAM
- **Intune MDM + MAM**: It-administratorer kan kun administrere apps ved hjælp af politikker for appbeskyttelse på enheder, der er tilmeldt Intune administration af mobilenheder (MDM).
- **MAM uden enhedsregistrering**: MAM uden enhedsregistrering eller MAM-WE gør det muligt for it-administratorer at administrere apps ved hjælp af [politikker for appbeskyttelse](/mem/intune/apps/app-protection-policy) på enheder, der ikke er tilmeldt Intune MDM. Det betyder, at apps kan administreres af Intune på enheder, der er tilmeldt hos EMM-tredjepartsudbydere. For at administrere apps, der bruger i begge ovenstående konfigurationer, skal kunderne bruge Intune i [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431)

Hvis du vil aktivere denne funktion, skal en administrator konfigurere forbindelsen mellem Microsoft Defender for Endpoint og Intune, oprette beskyttelsespolitikken for apps og anvende politikken på målrettede enheder og programmer. 
 
Slutbrugerne skal også tage skridt til at installere Microsoft Defender for Endpoint på deres enhed og aktivere onboardingflowet.

### <a name="pre-requisites"></a>Forudsætninger

1. **Kontrollér, at connectoren er aktiveret**. <br> På [unified security console](https://security.microsoft.com) skal du gå til **Indstillinger** >  **Endpoints** > **Avancerede funktioner** og sikre, at **Microsoft Intune forbindelse** er aktiveret.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Defender for Endpoint – Intune connector" lightbox="images/enable-intune-connection.png":::

  
2. **Kontrollér, at connectoren er aktiveret på Intune-portalen**. <br> I [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431) skal du gå til **Endpoint Security** >  **Microsoft Defender for Endpoint** og kontrollere, at forbindelsesstatus er aktiveret.

  :::image type="content" source="images/app-settings.png" alt-text="Programindstillingerne" lightbox="images/app-settings.png":::

### <a name="create-an-app-protection-policy"></a>Opret en beskyttelsespolitik for apps
 
Bloker adgang til eller slet data for en administreret app baseret på Microsoft Defender for Endpoint risikosignaler ved at oprette en beskyttelsespolitik for apps.
Microsoft Defender for Endpoint kan konfigureres til at sende trusselssignaler, der skal bruges i politikker for appbeskyttelse (APP, også kendt som MAM). Med denne funktion kan du bruge Microsoft Defender for Endpoint til at beskytte administrerede apps.

1. Opret en politik <br>
Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller findes i en administreret app. En politik kan være en regel, der gennemtvinges, når brugeren forsøger at få adgang til eller flytte "virksomhedsdata" eller et sæt handlinger, der ikke er tilladt eller overvåges, når brugeren befinder sig i appen. 

:::image type="content" source="images/create-policy.png" alt-text="Fanen Opret politik i menupunktet Appbeskyttelse politikker" lightbox="images/create-policy.png":::

2. Tilføj apps <br>
    a. Vælg, hvordan du vil anvende denne politik på apps på forskellige enheder. Tilføj derefter mindst én app. <br>
    Brug denne indstilling til at angive, om denne politik skal gælde for ikke-administrerede enheder. Du kan også vælge at målrette din politik til apps på enheder i en hvilken som helst administrationstilstand.
Da administration af mobilapps ikke kræver enhedsadministration, kan du beskytte virksomhedsdata på både administrerede og ikke-administrerede enheder. Administrationen er centreret om brugeridentiteten, hvilket fjerner kravet om enhedshåndtering. Virksomheder kan bruge politikker for appbeskyttelse med eller uden MDM på samme tid. Overvej f.eks. en medarbejder, der bruger både en telefon, der er udstedt af virksomheden, og deres egen personlige tablet. Firmatelefonen er tilmeldt MDM og beskyttet af politikker for appbeskyttelse, mens den personlige enhed kun er beskyttet af politikker for appbeskyttelse.

    b. Vælg apps<br>
    En administreret app er en app, hvor der er anvendt politikker for appbeskyttelse, og som kan administreres af Intune. Alle apps, der er integreret med [Intune SDK eller](/mem/intune/developer/app-sdk) ombrudt af [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management), kan administreres ved hjælp af Intune politikker for appbeskyttelse. Se den officielle liste over [Microsoft Intune beskyttede apps](/mem/intune/apps/apps-supported-intune-apps), der er bygget ved hjælp af disse værktøjer og er tilgængelige til offentlig brug.

    *Eksempel: Outlook som en administreret app*

     :::image type="content" source="images/managed-app.png" alt-text="Menupunktet Microsoft Outlook i venstre navigationsrude" lightbox="images/managed-app.png":::
  

 3. Angiv sikkerhedskrav til logon for din beskyttelsespolitik. <br>
Vælg **Indstilling > Maks. tilladt niveau for enhedstrussel** under **Enhedsbetingelser** , og angiv en værdi. Vælg derefter  **Handling: "Bloker adgang"**. Microsoft Defender for Endpoint på iOS deler dette Device Threat Level.

    
   :::image type="content" source="images/conditional-launch.png" alt-text="Ruden Enhedsbetingelser" lightbox="images/conditional-launch.png":::

4. Tildel brugergrupper, som politikken skal anvendes på.<br>
  Vælg **Inkluderede grupper**. Tilføj derefter de relevante grupper. 


Du kan få flere oplysninger om MAM- eller appbeskyttelsespolitik under [Indstillinger for beskyttelsespolitik for iOS-apps](/mem/intune/apps/app-protection-policy-settings-ios).

## <a name="deploy-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>Udrul Microsoft Defender for Endpoint til MAM eller på ikke-tilmeldte enheder

Microsoft Defender for Endpoint på iOS aktiverer scenariet for beskyttelsespolitikken for apps og er tilgængelig i Apple App Store.

Når politikker for appbeskyttelse er konfigureret til apps til at omfatte enhedsrisikosignaler fra Microsoft Defender for Endpoint, omdirigeres brugerne til at installere Microsoft Defender for Endpoint, når de bruger sådanne apps. Alternativt kan brugerne også installere den nyeste version af appen direkte fra Apple App Store.
