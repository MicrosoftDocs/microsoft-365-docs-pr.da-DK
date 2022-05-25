---
title: Konfigurer Microsoft Defender for Endpoint risikosignaler ved hjælp af MAM (App Protection Policies)
description: Beskriver, hvordan du konfigurerer Microsoft Defender for Endpoint risikosignaler ved hjælp af politikker for appbeskyttelse
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, konfiguration, MAM, App Protectection Policies, Managed app
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
ms.openlocfilehash: 48a128e32e949ecad6c34c4dfc96f6246780d0db
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/25/2022
ms.locfileid: "65670174"
---
# <a name="configure-microsoft-defender-for-endpoint-risk-signals-using-app-protection-policies-mam"></a>Konfigurer Microsoft Defender for Endpoint risikosignaler ved hjælp af MAM (App Protection Policies)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



Microsoft Defender for Endpoint på Android, som allerede beskytter virksomhedsbrugere på MOBILE Enhedshåndtering(MDM)-scenarier, udvider nu support til MAM (Mobile App Management) for enheder, der ikke er tilmeldt ved hjælp af Intune administration af mobilenheder (MDM). Denne support udvides også til kunder, der bruger andre løsninger til administration af virksomhedsmobilitet, mens de stadig bruger Intune til administration af mobilapps (MAM). Denne funktion giver dig mulighed for at administrere og beskytte din organisations data i et program.

Microsoft Defender for Endpoint på Android-trusselsoplysninger anvendes af Intune politikker for appbeskyttelse for at beskytte disse apps. Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller findes i en administreret app. Et administreret program har anvendt politikker for appbeskyttelse og kan administreres af Intune.  

Microsoft Defender for Endpoint på Android understøtter begge konfigurationer af MAM
- **Intune MDM + MAM**: It-administratorer kan kun administrere apps ved hjælp af politikker for appbeskyttelse på enheder, der er tilmeldt Intune administration af mobilenheder (MDM).
- **MAM uden enhedsregistrering**: MAM uden enhedsregistrering eller MAM-WE gør det muligt for it-administratorer at administrere apps ved hjælp af [politikker for appbeskyttelse](/mem/intune/apps/app-protection-policy) på enheder, der ikke er tilmeldt Intune MDM. Denne klargøring betyder, at apps kan administreres af Intune på enheder, der er tilmeldt EMM-tredjepartsudbydere. For at administrere apps i begge disse konfigurationer skal kunderne bruge Intune i [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

Hvis du vil aktivere denne funktion, skal en administrator konfigurere forbindelsen mellem Microsoft Defender for Endpoint og Intune, oprette beskyttelsespolitikken for apps og anvende politikken på målrettede enheder og programmer. 
 
Slutbrugerne skal også tage skridt til at installere Microsoft Defender for Endpoint på deres enhed og aktivere onboardingflowet.


## <a name="admin-prerequisites"></a>Administration forudsætninger

- **Valider, at Microsoft Defender for Endpoint-Intune-connector er aktiveret**

  a. Gå til security.microsoft.com. 

  b. Vælg **Indstillinger > Slutpunkter> Avancerede funktioner> Microsoft Intune Forbindelse** er slået til.

  c. Hvis forbindelsen ikke er slået til, skal du vælge til/fra-knappen for at aktivere den og derefter vælge **Gem indstillinger**.

  :::image type="content" source="images/enable-intune-connection.png" alt-text="Afsnittet Avancerede funktioner på Microsoft 365 Defender-portalen" lightbox="images/enable-intune-connection.png":::

  d. Gå til **Microsoft Endpoint Manager (Intune),** og valider, om Microsoft Defender for Endpoint-Intune-connector er aktiveret.

  :::image type="content" source="images/validate-intune-connector.png" alt-text="Statusruden for intune-connectoren på Microsoft 365 Defender-portalen" lightbox="images/validate-intune-connector.png":::

- **Aktivér Microsoft Defender for Endpoint på Android Connector til App Protection Policy (APP)**
  
  Konfigurer connectoren på Intune Microsoft Endpoint Manager for Appbeskyttelse politikker:

  a. Gå til **Lejeradministration > forbindelser og tokens > Microsoft Defender for Endpoint**.

  b. Slå til/fra-knappen for beskyttelsespolitikken for apps til Android (som vist på følgende skærmbillede).

  c. Vælg **Gem**.

  :::image type="content" source="images/app-settings.png" alt-text="Ruden programindstillinger på Microsoft 365 Defender-portalen" lightbox="images/app-settings.png":::

- **Opret en beskyttelsespolitik for apps** 
 
Bloker adgang til eller slet data for en administreret app baseret på Microsoft Defender for Endpoint risikosignaler ved at oprette en beskyttelsespolitik for apps.
Microsoft Defender for Endpoint kan konfigureres til at sende trusselssignaler, der skal bruges i politikker for appbeskyttelse (APP, også kendt som MAM). Med denne funktion kan du bruge Microsoft Defender for Endpoint til at beskytte administrerede apps.

1. Opret en politik <br>
Appbeskyttelse politikker (APP) er regler, der sikrer, at en organisations data forbliver sikre eller findes i en administreret app. En politik kan være en regel, der gennemtvinges, når brugeren forsøger at få adgang til eller flytte "virksomhedsdata" eller et sæt handlinger, der ikke er tilladt eller overvåges, når brugeren befinder sig i appen. 

:::image type="content" source="images/create-policy.png" alt-text="Fanen Opret politik på siden Appbeskyttelse politikker på portalen Microsoft 365 Defender" lightbox="images/create-policy.png":::

2. Tilføj apps <br>
    a. Vælg, hvordan du vil anvende denne politik på apps på forskellige enheder. Tilføj derefter mindst én app. <br>
    Brug denne indstilling til at angive, om denne politik skal gælde for ikke-administrerede enheder. I Android kan du angive politikken for Android Enterprise, Device Administration eller Unmanaged devices. Du kan også vælge at målrette din politik til apps på enheder i en hvilken som helst administrationstilstand.
Da administration af mobilapps ikke kræver enhedsadministration, kan du beskytte virksomhedsdata på både administrerede og ikke-administrerede enheder. Administrationen er centreret om brugeridentiteten, hvilket fjerner kravet om enhedshåndtering. Virksomheder kan bruge politikker for appbeskyttelse med eller uden MDM på samme tid. Overvej f.eks. en medarbejder, der bruger både en telefon, der er udstedt af virksomheden, og deres egen personlige tablet. Firmatelefonen er tilmeldt MDM og beskyttet af politikker for appbeskyttelse, mens den personlige enhed kun er beskyttet af politikker for appbeskyttelse.

    b. Vælg apps<br>
    En administreret app er en app, hvor der er anvendt politikker for appbeskyttelse, og som kan administreres af Intune. Alle apps, der er integreret med [Intune SDK eller](/mem/intune/developer/app-sdk) ombrudt af [Intune App Wrapping Tool](/mem/intune/developer/apps-prepare-mobile-application-management), kan administreres ved hjælp af Intune politikker for appbeskyttelse. Se den officielle liste over [Microsoft Intune beskyttede apps](/mem/intune/apps/apps-supported-intune-apps), der er bygget ved hjælp af disse værktøjer og er tilgængelige til offentlig brug.

    *Eksempel: Outlook som en administreret app*

  :::image type="content" source="images/managed-app.png" alt-text="Ruden Offentlige apps på Microsoft 365 Defender-portalen" lightbox="images/managed-app.png":::


 3. Angiv sikkerhedskrav til logon for din beskyttelsespolitik. <br>
Vælg **Indstilling > Maks. tilladt niveau for enhedstrussel** under **Enhedsbetingelser** , og angiv en værdi. Vælg derefter  **Handling: "Bloker adgang"**. Microsoft Defender for Endpoint på Android deler dette Device Threat Level.

  :::image type="content" source="images/conditional-launch.png" alt-text="Ruden Enhedsbetingelser på portalen Microsoft 365 Defender" lightbox="images/conditional-launch.png":::
  
- **Tildel brugergrupper, som politikken skal anvendes på.**<br>
  Vælg **Inkluderede grupper**. Tilføj derefter de relevante grupper. 

    :::image type="content" source="images/assignment.png" alt-text="Ruden Inkluderede grupper på portalen Microsoft 365 Defender" lightbox="images/assignment.png":::


## <a name="end-user-prerequisites"></a>Slutbrugerforudsætninger
- Mæglerappen skal installeres
    - Intune-firmaportal
    
- Brugerne har de nødvendige licenser til den administrerede app og har installeret appen

### <a name="end-user-onboarding"></a>Onboarding af slutbrugere 

1. Log på et administreret program, f.eks. Outlook. Enheden er registreret, og beskyttelsespolitikken for programmet synkroniseres med enheden. Beskyttelsespolitikken for programmet genkender enhedens tilstandstilstand.  

2. Vælg **Fortsæt**. Der vises en skærm, som anbefaler download og konfiguration af Microsoft Defender for Endpoint på Android-appen.

3. Vælg **Download**. Du omdirigeres til appbutikken (Google Play). 

4.  Installér appen Microsoft Defender for Endpoint (mobil), og start onboardingskærmen administreret app igen.

  :::image type="content" source="images/download-mde.png" alt-text="De illustrerende sider, der indeholder proceduren for download af MDE og start af appens onboarding-skærm igen" lightbox="images/download-mde.png":::
  

5.  Klik på **Fortsæt > Start**. Flowet Microsoft Defender for Endpoint app onboarding/activation startes. Følg trinnene for at fuldføre onboarding. Du omdirigeres automatisk tilbage til onboardingskærmen for administrerede apps, hvilket nu indikerer, at enheden fungerer korrekt.

6. Vælg **Fortsæt** for at logge på det administrerede program. 



## <a name="related-topics"></a>Relaterede emner

- [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
- [Installér Microsoft Defender for Endpoint på Android med Microsoft Intune](android-intune.md)
