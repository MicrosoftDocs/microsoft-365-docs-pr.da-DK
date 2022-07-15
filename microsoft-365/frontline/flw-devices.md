---
title: Administrer mobilenheder for frontlinjearbejdere
author: lanachin
ms.author: v-lanachin
ms.reviewer: mabolan
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
ms.localizationpriority: high
search.appverid: MET150
description: Få en oversigt over administration af mobilenheder for frontlinjearbejdere i din organisation.
ms.collection: m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: e0da7bf29865520507d9355fe25115700c3d8e28
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823889"
---
# <a name="manage-mobile-devices-for-frontline-workers"></a>Administrer mobilenheder for frontlinjearbejdere

## <a name="overview"></a>Oversigt

På tværs af alle brancher udgør frontlinjearbejdere et stort segment af arbejdsstyrken. Frontlinemedarbejderroller omfatter detailmedarbejdere, fabriksmedarbejdere, teknikere i marken og service, sundhedspersonale og mange flere.

Da arbejdsstyrken i høj grad er mobil og ofte skiftebaseret, er administration af de enheder, som frontlinjemedarbejdere bruger, en afgørende forudsætning. Nogle spørgsmål, du skal overveje:

- Bruger arbejdere enheder, der ejes af virksomheden, eller deres egne personlige enheder?
- Deles enheder, der ejes af virksomheden, mellem arbejdstagere eller tildeles til en person?
- Tager arbejdstagere enheder med hjem eller forlader dem på arbejdspladsen?

Det er vigtigt at angive en sikker grundlinje, der overholder angivne standarder, for at administrere enheder for din arbejdsstyrke, uanset om det er delte enheder eller arbejderes egne enheder. I denne artikel får du et overblik over almindelige scenarier med frontlinemedarbejdere og administrationsfunktioner, der hjælper dig med at styrke din arbejdsstyrke, samtidig med at du sikrer virksomhedens data.

## <a name="my-staff"></a>Mit personale

Med funktionen [Mit personale](/azure/active-directory/roles/my-staff-configure) i Azure Active Directory (Azure AD) kan du delegere almindelige brugeradministrationsopgaver til frontlinjeadministratorer via portalen Mit personale. Frontlineadministratorer kan udføre nulstilling af adgangskode eller administrere telefonnumre for frontlinjemedarbejdere direkte fra butikken eller fabriksgulvet uden at skulle distribuere anmodningerne om helpdesk, drift eller it.

Mit personale giver også frontlineledere mulighed for at registrere deres teammedlemmers telefonnumre til sms-logon. Hvis [SMS-baseret godkendelse](/azure/active-directory/authentication/howto-authentication-sms-signin) er aktiveret i din organisation, kan frontlinemedarbejdere logge på Teams og andre apps ved kun at bruge deres telefonnumre og en engangsadgangskode, der sendes via SMS. Det gør det nemt, sikkert og hurtigt at logge på frontlinjearbejdere.

## <a name="shared-devices"></a>Delte enheder

Mange frontlinjemedarbejdere bruger delte mobilenheder til at udføre arbejde. Delte enheder er enheder, der ejes af virksomheden, og som deles mellem medarbejdere på tværs af opgaver, skift eller placeringer.

Her er et eksempel på et typisk scenarie. En organisation har en pulje af enheder i opladningsholdere, der skal deles på tværs af alle medarbejdere. I starten af et skiftehold henter en medarbejder en enhed fra puljen og logger på Teams og andre virksomhedsapps, der er vigtige for deres rolle. I slutningen af deres vagt logger de af og returnerer enheden til puljen. Selv inden for samme skift returnerer en arbejder muligvis en enhed, når vedkommende afslutter en opgave eller stempler ud til frokost og derefter henter en anden, når vedkommende stempler ind igen.

Delte enheder udgør unikke sikkerhedsudfordringer. Medarbejdere kan f.eks. have adgang til firma- eller kundedata, der ikke bør være tilgængelige for andre på den samme enhed.

Dette afsnit indeholder en oversigt over de funktioner, der er tilgængelige til at administrere delte enheder for frontlinjearbejdere.

### <a name="shared-device-mode"></a>Tilstand for delt enhed

[Delt enhedstilstand](/azure/active-directory/develop/msal-shared-devices) er en funktion i Azure AD, der gør det muligt for dig at konfigurere enheder, der skal deles af medarbejdere. Denne funktion muliggør enkeltlogon (SSO) og enhedslogon til Microsoft Teams og alle andre apps, der understøtter delt enhedstilstand. Du kan integrere denne funktion i dine line of business-apps (LOB) ved hjælp af Microsoft Authentication Library (MSAL).

Her kan du se, hvordan delt enhedstilstand fungerer, f.eks. ved hjælp af Teams. Når en medarbejder logger på Teams i starten af deres vagt, er vedkommende automatisk logget på alle andre apps, der understøtter delt enhedstilstand på enheden. Når de logger af Teams, er de logget af globalt fra alle andre apps, der understøtter delt enhedstilstand, når de logger af Teams. Efter logon kan medarbejderens data og firmadata i Teams (herunder apps, der hostes i dem) og i alle andre apps, der understøtter delt enhedstilstand, ikke længere tilgås. Enheden er klar til den næste medarbejder og kan afleveres sikkert.

Du bruger en MDM-løsning (Mobile Device Management), f.eks. Microsoft Intune i Microsoft Endpoint Manager, til at forberede en enhed, der skal deles, ved at installere [Microsoft Authenticator-appen](https://support.microsoft.com/account-billing/how-to-use-the-microsoft-authenticator-app-9783c865-0308-42fb-a519-8cf666fe0acc) og aktivere delt tilstand. Teams og alle andre apps, der understøtter delt enhedstilstand, bruger indstillingen delt tilstand til at administrere brugere på enheden. Den MDM-løsning, du bruger, skal også udføre en enhedsoprydning, når der logges af.

Delt enhedstilstand understøttes i øjeblikket på Android-enheder. Her er nogle ressourcer, der kan hjælpe dig med at komme i gang.

#### <a name="enroll-android-devices-into-shared-device-mode"></a>Tilmeld Android-enheder til delt enhedstilstand

Hvis du vil administrere og tilmelde Android-enheder i delt enhedstilstand ved hjælp af Intune, skal enheder køre Android OS version 8.0 eller nyere og have forbindelse til Google Mobile Services (GMS). Du kan få mere at vide under:

- [Konfigurer Intune tilmelding til dedikerede Android Enterprise-enheder](/mem/intune/enrollment/android-kiosk-enroll)
- [Tilmeld Android Enterprise-dedikerede enheder til Azure AD delt enhedstilstand](https://techcommunity.microsoft.com/t5/intune-customer-success/enroll-android-enterprise-dedicated-devices-into-azure-ad-shared/ba-p/1820093)

Du kan også vælge at installere Microsoft Managed Home Screen-appen for at skræddersy oplevelsen til brugere på deres Intune tilmeldte Android-dedikerede enheder. Administreret startskærm fungerer som en startstarter, så andre godkendte apps kan køre oven på den, og giver dig mulighed for at tilpasse enheder og begrænse, hvad medarbejdere har adgang til. Du kan f.eks. definere, hvordan apps vises på startskærmen, tilføje dit firmalogo, angive brugerdefinerede baggrunde og give medarbejderne tilladelse til at angive en pinkode til sessionen. Du kan endda konfigurere, at logon sker automatisk efter en angivet periode med inaktivitet.  Du kan få mere at vide under:

- [Konfigurer Microsoft Managed Home Screen-appen til Android Enterprise](/mem/intune/apps/app-configuration-managed-home-screen-app)
- [Sådan konfigurerer du Microsoft Managed Home Screen på dedikerede enheder i kiosktilstand med flere apps](https://techcommunity.microsoft.com/t5/intune-customer-success/how-to-setup-microsoft-managed-home-screen-on-dedicated-devices/ba-p/1388060)

#### <a name="for-developers-creating-apps-for-shared-device-mode"></a>For udviklere, der opretter apps til delt enhedstilstand

Hvis du er udvikler, kan du se følgende ressourcer for at få flere oplysninger om, hvordan du integrerer din app med delt enhedstilstand:

- [Delt enhedstilstand for Android-enheder](/azure/active-directory/develop/msal-android-shared-devices)
- [Delt enhedstilstand for iOS-enheder](/azure/active-directory/develop/msal-ios-shared-devices)

## <a name="personal-devices-byod"></a>Personlige enheder (BYOD)

Nogle organisationer bruger en BYOD-model (bring-your-own-device), hvor frontlinjemedarbejdere bruger deres egne mobilenheder til at få adgang til Teams og andre virksomhedsapps. Her er en oversigt over nogle måder at administrere adgang og overholdelse af angivne standarder på personlige enheder på.

### <a name="enroll-android-and-ios-personal-devices"></a>Tilmeld personlige enheder til Android og iOS

Ud over dine enheder, der ejes af virksomheden, kan du [tilmelde](/mem/intune/enrollment/device-enrollment) brugernes personligt ejede enheder til administration i Intune. I forbindelse med BYOD-tilmelding kan du tilføje enhedsbrugere i Microsoft Endpoint Manager Administration, konfigurere deres tilmeldingsoplevelse og konfigurere Intune politikker. Brugerne selv fuldfører tilmeldingen i den Intune-firmaportal app, der er installeret på deres enhed.

I nogle tilfælde kan brugerne være tilbageholdende med at tilmelde deres personlige enheder til administration. Hvis tilmelding af enheder ikke er en mulighed, kan du vælge en MAM-tilgang (Mobile Application Management) og bruge [politikker for appbeskyttelse](/mem/intune/apps/app-protection-policies) til at administrere apps, der indeholder virksomhedsdata. Du kan f.eks. anvende politikker for appbeskyttelse i Teams og Office-mobilapps for at forhindre, at virksomhedsdata kopieres til personlige apps på enheden.

Du kan få mere at vide under ["Personlige enheder vs. enheder, der ejes af organisationen" i Intune planlægningsvejledning](/mem/intune/fundamentals/intune-planning-guide#personal-devices-vs-organization-owned-devices) og [installationsvejledning: Tilmeld enheder i Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment).

### <a name="off-shift-access-controls-in-teams"></a>Adgangskontrolelementer uden for vagt i Teams

Adgangskontrolelementer uden for vagten hjælper dig med at begrænse adgangen til Teams, når medarbejdere ikke er på vagt. Med denne funktion kan du angive Teams til at vise en meddelelse, når medarbejderne får adgang til appen uden for arbejdstiden. De skal acceptere meddelelsen, før de kan bruge Teams.

Standardmeddelelsen giver medarbejderen besked om, at vedkommende ikke bliver betalt for den tid, der er brugt på Teams uden for arbejdstiden. Du kan bruge standardmeddelelsen, vælge en foruddefineret meddelelse eller få vist din egen. Denne funktion hjælper med at sikre, at medarbejderne ikke ufrivilligt arbejder, når de ikke er på skift, og hjælper med at overholde arbejdsregler.

Du kan få mere at vide under [Fra shift-adgang til Teams](manage-shift-based-access-flw.md#off-shift-access-to-teams).

## <a name="related-articles"></a>Relaterede artikler

- [Styring af frontlinjemedarbejdere](/azure/active-directory/fundamentals/frontline-worker-management)
