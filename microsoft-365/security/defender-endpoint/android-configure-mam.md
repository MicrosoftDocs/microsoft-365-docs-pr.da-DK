---
title: Konfigurer Risikosignaler for Microsoft Defender til slutpunkt ved hjælp af appbeskyttelsespolitikker (MAM)
description: Beskrivelse af, hvordan du konfigurerer risikosignaler for Microsoft Defender til Slutpunkt ved hjælp af appbeskyttelsespolitikker
keywords: microsoft, defender, Microsoft Defender til slutpunkt, mde, android, konfiguration, MAM, App Protectection Policies, Administreret app
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: shthota
author: shthota
manager: dansimp
ms.localizationpriority: medium
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 5c18d5e9fbf628f5d4e4373b866fa300c193ac30
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594031"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Konfigurer Risikosignaler for Microsoft Defender til slutpunkt ved hjælp af appbeskyttelsespolitikker (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Microsoft Defender til slutpunkt på Android, som allerede beskytter virksomhedsbrugere på MDM-scenarier (Mobile Device Management), understøtter nu administration af mobilapps (MAM – Mobile App Management) for enheder, der ikke er tilmeldt Ved hjælp af Administration af mobilenheder i Intune (MDM). Det udvider også denne support til kunder, der bruger andre enterprise mobility management-løsninger, mens de stadig bruger Intune til administration af mobilapps (MAM). Denne funktion giver dig mulighed for at administrere og beskytte din organisations data i et program.

Microsoft Defender til Slutpunkt på Android-trusselsoplysninger udnyttes af Intune-politikker for appbeskyttelse for at beskytte disse apps. Appbeskyttelsespolitikker er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. Et administreret program har anvendte politikker for appbeskyttelse og kan administreres af Intune.  

Microsoft Defender til slutpunkt på Android understøtter begge konfigurationer af MAM
- **Intune MDM + MAM**: It-administratorer kan kun administrere apps ved hjælp af politikker for appbeskyttelse på enheder, der er tilmeldt Intune administration af mobilenheder (MDM).
- **MAM uden tilmelding til** enhed: MAM uden enhedsregistrering eller MAM-WE giver it-administratorer mulighed for at administrere apps ved hjælp af [politikker for appbeskyttelse](/mem/intune/app/app-protection-policy) på enheder, der ikke er tilmeldt Intune MDM. Det betyder, at apps kan administreres af Intune på enheder, der er tilmeldt tredjeparts EMM-udbydere. Kunder, der administrerer apps, der bruger begge ovenstående konfigurationer, skal bruge Intune [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431)

For at aktivere denne funktion skal en administrator konfigurere forbindelsen mellem Microsoft Defender til slutpunkt og Intune, oprette beskyttelsespolitikken for apps og anvende politikken på målrettede enheder og programmer. 
 
Slutbrugere skal også tage skridt til at installere Microsoft Defender for Endpoint på deres enhed og aktivere onboardingflowet.


## <a name="admin-prerequisites"></a>Administratorfor forudsætninger

- **Valider, at Microsoft Defender for Endpoint-Intune forbindelse er aktiveret**

  a. Gå til security.microsoft.com. 

  b. Vælg **Indstillinger > slutpunkter> avancerede funktioner, > Microsoft Intune Forbindelse er** slået til.

  c. Hvis forbindelsen ikke er aktiveret, skal du vælge til/fra-knappen for at aktivere den og derefter vælge **Gem indstillinger**.

  ![Billede af Defender til forbindelsespunktet Endpoint -Intune](images/enable-intune-connection.png)

  d. Gå til **Microsoft Endpoint Manager (Intune),** og Valider, om Microsoft Defender til Endpoint-Intune forbindelse er aktiveret.

  ![Billede af Defender til Endpoint-Intune forbindelse i Intune](images/validate-intune-connector.png)

- **Aktivér Microsoft Defender til slutpunkt på Android Connector til appbeskyttelsespolitik (APP)**
  
  Konfigurer forbindelsen på Intune-Microsoft Endpoint Manager politikker for appbeskyttelse:

  a. Gå til **Lejeradministration > forbindelser og tokens > Microsoft Defender til slutpunkt**.

  b. Slå til/fra-knappen til for appbeskyttelsespolitikken for Android (som vist på følgende skærmbillede).

  c. Vælg **Gem**.

  ![Appindstillinger](images/app-settings.png)

- **Opret en politik for appbeskyttelse** 
 
Bloker adgang til eller sletning af data i en administreret app, der er baseret på risikosignaler for Microsoft Defender til Slutpunkt, ved at oprette en politik for appbeskyttelse.
Microsoft Defender til slutpunkt kan konfigureres til at sende trusselssignaler, der skal bruges i politikker for appbeskyttelse (APP, også kaldet MAM). Med denne funktion kan du bruge Microsoft Defender til Slutpunkt til at beskytte administrerede apps.

1. Opret en politik <br>
Appbeskyttelsespolitikker er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. En politik kan være en regel, der håndhæves, når brugeren forsøger at få adgang til eller flytte "virksomhedsdata" eller et sæt handlinger, der er forbudt eller overvåget, når brugeren er inde i appen. 

![Billede af oprettelse af politik](images/create-policy.png)

2. Tilføj apps <br>
    a. Vælg, hvordan du vil anvende denne politik på apps på forskellige enheder. Tilføj derefter mindst én app. <br>
    Brug denne indstilling til at angive, om denne politik gælder for enheder, der ikke er administrerede. I Android-enheder kan du angive, at politikken skal gælde for Android Enterprise, Enhedsadministrator eller Ikke-administrerede enheder. Du kan også vælge at målrette din politik mod apps på enheder af en hvilken som helst administrationstilstand.
Da administration af mobilapps ikke kræver enhedshåndtering, kan du beskytte virksomhedsdata på både administrerede og ikke-administrerede enheder. Administrationen er centreret om brugeridentiteten, hvilket fjerner kravet til enhedshåndtering. Virksomheder kan bruge politikker for appbeskyttelse med eller uden MDM på samme tid. Tænk f.eks. på en medarbejder, der både bruger en telefon udstedt af virksomheden og deres egen personlige tablet. Virksomhedens telefon er tilmeldt MDM og beskyttet af politikker for appbeskyttelse, mens den personlige enhed kun er beskyttet af politikker for appbeskyttelse.

    b. Vælg Apps<br>
    En administreret app er en app, der har politikker for beskyttelse af apps anvendt på den og kan administreres af Intune. Alle apps, der er integreret med [Intune SDK](/mem/intune/developer/app-sdk) eller ombrudt af [Intune-App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management), kan administreres ved hjælp af Intune-appbeskyttelsespolitikker. Se den officielle liste over [Microsoft Intune beskyttede apps,](/mem/intune/apps/apps-supported-intune-apps) der er udviklet ved hjælp af disse værktøjer, og som er tilgængelige til offentlig brug.

    *Eksempel: Outlook som en administreret app*

    ![Billede Outlook som administreret app](images/managed-app.png)

 3. Angiv sikkerhedskrav til logon for din beskyttelsespolitik. <br>
Vælg **Indstilling > maks. tilladte trusselsniveau for** enheder **under Enhedsbetingelser** , og angiv en værdi. Vælg derefter  **Handling: "Bloker adgang"**. Microsoft Defender til slutpunkt på Android deler dette trusselsniveau for enheden.

    ![Billede af betinget start](images/conditional-launch.png)


- **Tildel brugergrupper, som politikken skal anvendes på.**<br>
  Vælg **Inkluderede grupper**. Tilføj derefter de relevante grupper. 

    ![Billede af assigments](images/assignment.png)


## <a name="end-user-prerequisites"></a>Forudsætninger for slutbruger
- Formidlerappen skal installeres
    - Intune-firmaportal
    
- Brugere har de nødvendige licenser til den administrerede app og har appen installeret

### <a name="end-user-onboarding"></a>Onboarding af slutbrugere 

1. Log på et administreret program, f.eks. Outlook. Enheden er registreret, og programbeskyttelsespolitikken synkroniseres med enheden. Programbeskyttelsespolitikken genkender enhedens tilstand.  

2. Vælg **Fortsæt**. Der vises en skærm, som anbefaler at downloade og konfigurere Microsoft Defender til slutpunkt på Android-appen.

3. Vælg **Download**. Du bliver omdirigeret til App Store (Google Play). 

4.  Installér appen Microsoft Defender til Slutpunkt (mobil), og start onboardingskærmen for Administreret app igen.

  ![Installér MDE, og start back-administreret onboardingskærm for apps](images/download-mde.png)

5.  Klik **på > Start**. Onboarding-/aktiveringsflowet for Microsoft Defender til slutpunktsappen startes. Følg trinnene for at fuldføre onboarding. Du bliver automatisk omdirigeret tilbage til onboardingskærmen for administrerede apps, som nu angiver, at enheden er sund.

6. Vælg **Fortsæt** for at logge på det administrerede program. 



## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender til slutpunkt på Android](microsoft-defender-endpoint-android.md)
- [Installér Microsoft Defender til slutpunkt på Android med Microsoft Intune](android-intune.md)
