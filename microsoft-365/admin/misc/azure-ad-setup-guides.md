---
title: Azure Active Directory konfigurationsvejledninger
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
description: Få mere at vide om konfigurationsvejledninger til Azure Active Directory.
ms.openlocfilehash: 58f7ed9a20580db742a773cb8a7874137f0cfc4c
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128406"
---
# <a name="azure-active-directory-setup-guides"></a>Azure Active Directory konfigurationsvejledninger

Azure Active Directory (Azure AD) hjælper dig med at administrere og beskytte din organisation. Disse konfigurationsvejledninger hjælper dig med at integrere disse funktioner på en enkel måde. I de følgende afsnit beskriver vi kort konfigurationsvejledningerne og deler links til vejledningerne.

## <a name="who-are-these-setup-guides-for"></a>Who er disse konfigurationsvejledninger til?

Disse konfigurationsvejledninger er udviklet til små og mellemstore organisationer, der typisk ikke har et dedikeret identitetsteam. Du behøver ikke at være identitetsekspert for at bruge dem.

## <a name="what-to-expect-and-what-youll-need"></a>Hvad du kan forvente, og hvad du har brug for

Konfigurationsvejledningerne hjælper dig med at konfigurere kernefunktionaliteten i Azure AD. Hvis du har brug for at konfigurere en mere avanceret konfiguration, peger installationsvejledningen dig på den relevante placering på Azure AD-portalen.

### <a name="required-permissions"></a>Påkrævede tilladelser

Du skal være medlem af følgende administrative roller:

- Global administrator: Giver dig mulighed for at bruge integrerede værktøjer i konfigurationsvejledningerne til at foretage ændringer i din Microsoft 365 organisation.

- Global læser: Giver dig mulighed for at få vist konfigurationsvejledningerne, men ikke foretage ændringer i din lejer.

## <a name="identity-security-for-teams"></a>Identitetssikkerhed for Teams

Azure Active Directory (Azure AD) er vores cloudbaserede tjeneste til identitets- og adgangsstyring, som hjælper dine medarbejdere med at logge på og få adgang til apps og tjenester.
Dette katalog indeholder nogle grundlæggende sikkerhedsfunktioner, som du kan bruge til at sikre, at dine brugere er sikre og har den mest produktive tid ved hjælp af Teams.

### <a name="licensing"></a>Licensering

Der kræves en Azure Active Directory P2-licens for at kunne anvende sikkerhedsfunktionerne i dette katalog.

[Åbn identitetssikkerheden for Teams katalog](https://aka.ms/teamsidentity)

## <a name="identity-governance"></a>Identitetsstyring

Dette guidekatalog er designet til at hjælpe kunder med Azure Active Directory P2-funktionalitet, herunder Access Reviews (AR), Privileged Identity Management (PIM) og berettigelsesstyring (ELM). Til PIM og ELM tilbyder vi en udvalgt liste over dokumenter og en pointer til Azure Active Directory Administration, hvor administratoren kan konfigurere denne funktionalitet. For AR tilbyder vi en fuldt automatiseret oplevelse, der giver administratorer mulighed for at vælge mellem to skabeloner. Disse skabeloner omfatter en, der gør det muligt for gruppeejere at godkende gæstebrug i alle Microsoft 365 grupper. Dette er en toppolitik, som kunderne bruger i dag.  

Derefter tilbyder vi en testskabelon, hvor administratoren er korrekturlæser af gæster for en bestemt gruppe, de vælger. Hvis lejeren allerede har en anmeldelse på plads, der dækker alle Microsoft 365 grupper af gæstebrugere, bliver administratoren henvist til Azure Active Directory Administration for at administrere den eksisterende anmeldelse, og der vil ikke være nogen automatiseret oplevelse.

[Åbn konfigurationsvejledningen til identitetsstyring](https://go.microsoft.com/fwlink/p/?linkid=386330)

> [!NOTE]
> Azure Active Directory P2-licens er påkrævet for at bruge sikkerhedsfunktionerne i dette katalog.

## <a name="azure-active-directory-deployment"></a>Azure Active Directory udrulning  

Konfigurationsvejledningen til Azure Active Directory hjælper dig med at konfigurere de mest almindelige Azure AD funktioner i en anbefalet rækkefølge. Installationsvejledningen er opdelt i tre afsnit: **Initial**, **Core** og **Advanced**. I hvert afsnit anbefales et sæt funktioner, som du skal aktivere.

Konfigurationsvejledningerne indeholder en tjekliste over de opgaver, du skal udføre, og du kan spore din status, efterhånden som du gennemgår vejledningerne. Hjælpelinjerne linker også til de andre opsætningsvejledninger, når det er nødvendigt.

[Åbn installationsvejledningen til Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=2183427).

## <a name="add-or-sync-users-to-your-microsoft-account"></a>Føj eller synkroniser brugere til din Microsoft-konto  

Denne vejledning hjælper dig med at konfigurere konfiguration af brugerkonti i Azure og Microsoft 365. Baseret på dit miljø og dine behov kan du vælge at tilføje brugere individuelt, overføre din lokale mappe med Azure AD cloudsynkronisering eller Azure AD Forbind eller foretage fejlfinding af eksisterende synkroniseringsproblemer.

### <a name="licensing"></a>Licensering

Brug af Azure Active Directory synkroniseringsværktøjer er gratis og inkluderet i alle Microsoft 365 abonnementer.

[Åbn konfigurationsvejledningen til Tilføj eller synkroniser brugere](https://go.microsoft.com/fwlink/?linkid=2183349).

## <a name="secure-your-cloud-apps-with-single-sign-on-sso"></a>Beskyt dine cloudapps med enkeltlogon (SSO)

Denne vejledning er designet til at hjælpe dig med at føje cloudapps til Microsoft 365. I vores vejledning kan du føje et program til din lejer, føje brugere til appen, tildele roller og meget mere.  Hvis appen understøtter Enkelt Sign-On (SSO), fører vi dig også gennem denne konfiguration.

### <a name="licensing"></a>Licensering

Alle betalte abonnementer på Microsoft 365 leveres med et gratis abonnement på Azure AD. Du kan bruge Azure AD til at administrere dine apps og oprette og administrere bruger- og gruppekonti.

[Åbn konfigurationsvejledningen Tilføj en cloudapp for at Microsoft 365](https://aka.ms/AzureAppSetup)

## <a name="azure-self-service-password-reset-sspr-guide"></a>Vejledning til nulstilling af Azure Self-Service-adgangskode (SSPR)

Denne installationsvejledning er designet til at hjælpe dig med at aktivere og konfigurere selvbetjent nulstilling af adgangskode. Konfigurationsvejledningen fører dig gennem anbefalede indstillinger, herunder meddelelser om tilbageskrivning af adgangskode og administratormeddelelser.

### <a name="licensing"></a>Licensering

SSPR kræver en af følgende licenser:

- Azure Active Directory P1 eller P2

- Microsoft 365 Business Premium

- Microsoft 365 Enterprise E3 eller E5  

- Enterprise Mobility and Security E3 eller E5

[Åbn konfigurationsvejledningen til selvbetjent nulstilling af adgangskode](https://go.microsoft.com/fwlink/p/?linkid=2183284).

## <a name="multi-factor-authentication-mfa"></a>Multifaktorgodkendelse (MFA)

Denne vejledning indeholder den aktuelle MFA-status og hjælper it-administratorer med at vælge den bedste MFA-indstilling, der opfylder deres organisations krav. Derefter hjælper vi med at konfigurere og gennemtvinge den valgte MFA-metode for organisationen.

### <a name="licensing"></a>Licensering

Betinget adgang kræver en Azure Active Directory P1- eller P2-licens, sikkerhedsstandarder og MFA pr. bruger er gratis og inkluderet i alle Microsoft 365 abonnementer.

[Åbn vejledningen til multifaktorgodkendelse](https://go.microsoft.com/fwlink/?linkid=2183506)

## <a name="the-passwordless-setup-guide"></a>Den konfigurationsvejledning, der ikke er adgangskodeløs

Den konfigurationsvejledning, der ikke er adgangskodeløs, er designet til at hjælpe dig med at finde den bedste metode uden adgangskode til dit miljø. Metoderne omfatter sikkerhedsnøgler, Windows Hello til virksomheder og appen Microsoft Authenticator. Hvis anbefalingen er Windows Hello til virksomheder, er der et afsnit, der guider dig gennem de forskellige muligheder. Vejledningen stiller dig spørgsmål for at hjælpe dig med at udforme en trinvis plan.

### <a name="licensing"></a>Licensering

Alle betalte abonnementer på Microsoft 365 leveres med et gratis abonnement på Azure AD. Du kan bruge Azure AD til at administrere dine apps og oprette og administrere bruger- og gruppekonti.

[Åbn konfigurationsvejledningen uden adgangskode](https://go.microsoft.com/fwlink/?linkid=2183427).
