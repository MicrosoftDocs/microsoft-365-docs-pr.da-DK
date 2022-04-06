---
title: Konfigurere Microsoft Defender for Endpoint risikosignaler ved hjælp af App Protection Policies (MAM)
description: Beskriver, hvordan du konfigurerer Microsoft Defender for Endpoint ved hjælp af politikker for appbeskyttelse
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, konfiguration, MAM, App Protectection Policies, Administreret app
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
ms.openlocfilehash: 5d74fd2af61ee4047dd2728c28e6093efbc58ce9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64471291"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Konfigurere Microsoft Defender for Endpoint risikosignaler ved hjælp af App Protection Policies (MAM)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Microsoft Defender for Endpoint på Android, som allerede beskytter virksomhedsbrugere på Mobile Enhedshåndtering-scenarier (MDM), understøtter nu administration af mobilapps (MAM – Mobile App Management) for enheder, der ikke er tilmeldt Intune administration af mobilenheder (MDM). Det udvider også denne support til kunder, der bruger andre enterprise mobility management-løsninger, mens de stadig bruger Intune til administration af mobilapps (MAM). Denne funktion giver dig mulighed for at administrere og beskytte din organisations data i et program.

Microsoft Defender for Endpoint oplysninger om Android-trusler anvendes af Intune politikker for appbeskyttelse for at beskytte disse apps. Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. Et administreret program har anvendt politikker for appbeskyttelse og kan administreres af Intune.  

Microsoft Defender for Endpoint på Android understøtter begge konfigurationer af MAM
- **Intune MDM + MAM**: It-administratorer kan kun administrere apps ved hjælp af politikker for appbeskyttelse på enheder, der er tilmeldt Intune administration af mobilenheder (MDM).
- **MAM uden enhedsregistrering**: MAM uden enhedsregistrering eller MAM-WE giver it-administratorer mulighed for at administrere apps ved hjælp af [politikker for appbeskyttelse](/mem/intune/app/app-protection-policy) på enheder, der ikke er tilmeldt Intune MDM. Denne klargøring betyder, at apps kan administreres Intune enheder, der er tilmeldt tredjeparts EMM-udbydere. For at administrere apps, der bruger begge ovenstående konfigurationer, skal Intune i [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431)

For at aktivere denne funktion skal en administrator konfigurere forbindelsen mellem Microsoft Defender for Endpoint og Intune, oprette beskyttelsespolitikken for apps og anvende politikken på målrettede enheder og programmer. 
 
Slutbrugere skal også tage skridt til at installere Microsoft Defender for Endpoint på deres enhed og aktivere onboardingflowet.


## <a name="admin-prerequisites"></a>Administratorfor forudsætninger

- **Valider, at Microsoft Defender for Endpoint-Intune forbindelse er aktiveret**

  a. Gå til security.microsoft.com. 

  b. Vælg **Indstillinger > slutpunkter> avancerede funktioner, > Microsoft Intune Forbindelse er** slået til.

  c. Hvis forbindelsen ikke er aktiveret, skal du vælge til/fra-knappen for at aktivere den og derefter vælge **Gem indstillinger**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Afsnittet Avancerede funktioner i Microsoft 365 Defender portalen" lightbox="images/enable-intune-connection.png":::

  d. Gå til **Microsoft Endpoint Manager (Intune)** og Valider, om Microsoft Defender til Endpoint-Intune forbindelse er aktiveret.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Statusruden intune-connector i Microsoft 365 Defender portal" lightbox="images/validate-intune-connector.png":::

- **Aktivér Microsoft Defender for Endpoint på Android Connector til appbeskyttelsespolitik (APP)**
  
  Konfigurer forbindelsen på en Intune Microsoft Endpoint Manager for Appbeskyttelse politikker:

  a. Gå til **Lejeradministration > forbindelsesforbindelser og tokens > Microsoft Defender for Endpoint**.

  b. Slå til/fra-knappen til for appbeskyttelsespolitikken for Android (som vist på følgende skærmbillede).

  c. Vælg **Gem**.

  :::image type="content" source="images/app-settings.png" alt-text="Ruden Programindstillinger i Microsoft 365 Defender portal" lightbox="images/app-settings.png":::

- **Opret en politik for appbeskyttelse** 
 
Bloker adgang til eller sletning af data i en administreret app baseret på Microsoft Defender for Endpoint risikosignaler ved at oprette en politik for appbeskyttelse.
Microsoft Defender for Endpoint kan konfigureres til at sende trusselslyde, der skal bruges i politikker for appbeskyttelse (APP, også kaldet MAM). Med denne funktion kan du bruge en Microsoft Defender for Endpoint til at beskytte administrerede apps.

1. Opret en politik <br>
Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller indeholdt i en administreret app. En politik kan være en regel, der håndhæves, når brugeren forsøger at få adgang til eller flytte "virksomhedsdata" eller et sæt handlinger, der er forbudt eller overvåget, når brugeren er inde i appen. 

:::image type="content" source="images/create-policy.png" alt-text="Fanen Opret politik på Appbeskyttelse politikker i Microsoft 365 Defender portal" lightbox="images/create-policy.png":::

2. Tilføj apps <br>
    a. Vælg, hvordan du vil anvende denne politik på apps på forskellige enheder. Tilføj derefter mindst én app. <br>
    Brug denne indstilling til at angive, om denne politik gælder for enheder, der ikke er administrerede. I Android kan du angive politikken for Android Enterprise, Enhedsadministrator eller Ikke-administrerede enheder. Du kan også vælge at målrette din politik mod apps på enheder af en hvilken som helst administrationstilstand.
Da administration af mobilapps ikke kræver enhedshåndtering, kan du beskytte virksomhedsdata på både administrerede og ikke-administrerede enheder. Administrationen er centreret om brugeridentiteten, hvilket fjerner kravet til enhedshåndtering. Virksomheder kan bruge politikker for appbeskyttelse med eller uden MDM på samme tid. Tænk f.eks. på en medarbejder, der både bruger en telefon udstedt af virksomheden og deres egen personlige tablet. Virksomhedens telefon er tilmeldt MDM og beskyttet af politikker for appbeskyttelse, mens den personlige enhed kun er beskyttet af politikker for appbeskyttelse.

    b. Vælg Apps<br>
    En administreret app er en app, der har politikker for appbeskyttelse anvendt på den, og den kan administreres Intune. Alle apps, der er integreret med [INTUNE SDK](/mem/intune/developer/app-sdk) eller ombrudt af Intune App Wrapping Tool, [](/mem/intune/developer/apps-prepare-mobile-application-management) kan administreres ved hjælp Intune politikker for appbeskyttelse. Se den officielle liste over [Microsoft Intune beskyttede apps,](/mem/intune/apps/apps-supported-intune-apps) der er udviklet ved hjælp af disse værktøjer, og som er tilgængelige til offentlig brug.

    *Eksempel: Outlook som en administreret app*

  :::image type="content" source="images/managed-app.png" alt-text="Ruden Offentlige apps i Microsoft 365 Defender portalen" lightbox="images/managed-app.png":::


 3. Angiv sikkerhedskrav til logon for din beskyttelsespolitik. <br>
Vælg **Indstilling > maks. tilladte trusselsniveau for** enheder **under Enhedsbetingelser** , og angiv en værdi. Vælg derefter  **Handling: "Bloker adgang"**. Microsoft Defender for Endpoint på Android deler dette trusselsniveau for enheden.

  :::image type="content" source="images/conditional-launch.png" alt-text="Ruden Enhedsbetingelser i Microsoft 365 Defender portal" lightbox="images/conditional-launch.png":::
  
- **Tildel brugergrupper, som politikken skal anvendes på.**<br>
  Vælg **Inkluderede grupper**. Tilføj derefter de relevante grupper. 

    :::image type="content" source="images/assignment.png" alt-text="Ruden Inkluderede grupper i Microsoft 365 Defender portal" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Forudsætninger for slutbruger
- Formidlerappen skal installeres
    - Intune-firmaportal
    
- Brugere har de nødvendige licenser til den administrerede app og har appen installeret

### <a name="end-user-onboarding"></a>Onboarding til slutbruger 

1. Log på et administreret program, f.eks. Outlook. Enheden er registreret, og programbeskyttelsespolitikken synkroniseres med enheden. Programbeskyttelsespolitikken genkender enhedens tilstand.  

2. Vælg **Fortsæt**. Der vises en skærm, som anbefaler at downloade og konfigurere Microsoft Defender for Endpoint i Android-appen.

3. Vælg **Download**. Du bliver omdirigeret til App Store (Google Play). 

4.  Installér Microsoft Defender for Endpoint (mobil) og start back Managed app onboarding screen.

  :::image type="content" source="images/download-mde.png" alt-text="De vejledende sider, der indeholder fremgangsmåden til at hente MDE og starte appen tilbage på onboardingskærmen" lightbox="images/download-mde.png":::
  

5.  Klik **på > Start**. Start Microsoft Defender for Endpoint-appens onboarding-/aktiveringsflow. Følg trinnene for at fuldføre onboarding. Du bliver automatisk omdirigeret tilbage til onboardingskærmen for administrerede apps, som nu angiver, at enheden er sund.

6. Vælg **Fortsæt** for at logge på det administrerede program. 



## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
- [Installer Microsoft Defender for Endpoint på Android med Microsoft Intune](android-intune.md)
