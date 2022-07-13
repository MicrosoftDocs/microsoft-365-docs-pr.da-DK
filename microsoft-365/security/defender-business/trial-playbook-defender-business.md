---
title: Microsoft Defender til virksomheder prøvelegebog
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.prod: m365-security
ms.technology: mdb
search.appverid:
- MOE150
- MET150
description: Få mest ud af din Defender for Business-prøveversion med denne playbook. Kom hurtigt i gang med at konfigurere, og kom i gang med at bruge dine nye sikkerhedsfunktioner.
ms.custom: trial-playbook
ms.openlocfilehash: 16843ef3dcb2efe36f9102001fe5579e920287b4
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772776"
---
# <a name="trial-playbook-microsoft-defender-for-business"></a>Playbook til prøveversion: Microsoft Defender til virksomheder

**Velkommen til Defender for Business-prøveversionens playbook!**

Denne playbook er en enkel vejledning, der hjælper dig med at få mest ud af din 30-dages gratis prøveversion. Brug anbefalingerne i denne artikel fra Microsoft Defender-teamet til at få mere at vide om, hvordan Defender for Business kan hjælpe med at højne din sikkerhed fra traditionel antivirusbeskyttelse til næste generations beskyttelse, registrering af slutpunkter og svar samt Håndtering af trusler og sikkerhedsrisici.

## <a name="what-is-defender-for-business"></a>Hvad er Defender for Business?

Defender for Business er en ny sikkerhedsløsning til slutpunkter, der er udviklet specielt til små og mellemstore virksomheder med op til 300 medarbejdere. Med denne sikkerhedsløsning til slutpunktet er din organisations enheder godt beskyttet mod ransomware, malware, phishing og andre trusler.

:::image type="content" source="media/mdb-offering-overview.png" alt-text="Defender for Business-funktioner og -funktioner.":::

**Lad os komme i gang!**

## <a name="set-up-your-trial"></a>Konfigurer din prøveversion

Sådan konfigurerer du dit prøveabonnement:

1. [Tilføj brugere, og tildel licenser](#step-1-add-users-and-assign-licenses).
2. [Besøg Microsoft 365 Defender-portalen](#step-2-visit-the-microsoft-365-defender-portal).
3. [Brug installationsguiden](#step-3-use-the-setup-wizard-in-defender-for-business-recommended).
4. [Konfigurer Defender for Business](#step-4-set-up-and-configure-defender-for-business).

### <a name="step-1-add-users-and-assign-licenses"></a>Trin 1: Tilføj brugere, og tildel licenser

Når du har tilmeldt dig Defender for Business, er det første trin at **[tilføje brugere og tildele licenser](mdb-add-users.md)**.

> [!NOTE]
> Du skal være global administrator for at kunne udføre denne opgave. Den person, der har tilmeldt din virksomhed til Microsoft 365 eller Defender for Business, er som standard den globale administrator. [Få mere at vide om roller og tilladelser](mdb-roles-permissions.md).

### <a name="step-2-visit-the-microsoft-365-defender-portal"></a>Trin 2: Besøg Microsoft 365 Defender-portalen
 
Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) er den one-stop-shop, hvor du bruger og administrerer Defender for Business. Den indeholder billedforklatter, der hjælper dig med at komme i gang, kort, der viser relevante oplysninger, og en navigationslinje, der giver nem adgang til de forskellige funktioner og funktioner.

- **[Besøg Microsoft 365 Defender-portalen](mdb-get-started.md)**.
- **[Udforsk navigationslinjen](mdb-get-started.md#the-navigation-bar)** i venstre side af skærmen for at få adgang til dine hændelser, få vist rapporter og administrere dine sikkerhedspolitikker og -indstillinger.

### <a name="step-3-use-the-setup-wizard-in-defender-for-business-recommended"></a>Trin 3: Brug installationsguiden i Defender for Business (anbefales)

Defender for Business er udviklet til at spare tid og kræfter på små og mellemstore virksomheder. Du kan udføre den indledende konfiguration ved hjælp af en installationsguide. Installationsguiden hjælper dig med at give adgang til dit sikkerhedsteam, konfigurere mailmeddelelser til dit sikkerhedsteam og onboarde din virksomheds Windows-enheder. **[Brug installationsguiden](mdb-use-wizard.md)**.

> [!NOTE]
> Du kan kun bruge installationsguiden én gang.

#### <a name="setup-wizard-flow-what-to-expect"></a>Konfigurationsguideflow: Hvad kan du forvente?

> [!TIP]
> **Det er valgfrit at bruge installationsguiden.** (Se [Hvad sker der, hvis jeg ikke bruger guiden?](mdb-use-wizard.md#what-happens-if-i-dont-use-the-wizard)) Hvis du vælger ikke at bruge guiden, eller hvis guiden lukkes, før installationsprocessen er fuldført, kan du selv fuldføre konfigurationsprocessen. Se [trin 4](#step-4-set-up-and-configure-defender-for-business). 

1. **[Tildel brugertilladelser](mdb-roles-permissions.md#view-or-edit-role-assignments)**. Giv sikkerhedsteamet adgang til Microsoft 365 Defender-portalen.

2. **[Konfigurer mailmeddelelser](mdb-email-notifications.md#view-and-edit-email-notifications)** til dit sikkerhedsteam.

3. **[Onboarde og konfigurer Windows-enheder](mdb-onboard-devices.md)**. Onboarding af enheder med det samme hjælper med at beskytte disse enheder fra dag 1.

   > [!NOTE]
   > Når du bruger installationsguiden, registrerer systemet, om du har Windows-enheder, der allerede er tilmeldt Intune. Du bliver spurgt, om du vil bruge automatisk onboarding for alle eller nogle af disse enheder. Du kan onboarde alle Windows-enheder på én gang eller først vælge bestemte enheder og derefter tilføje flere enheder senere. [Få mere at vide om automatisk onboarding](mdb-use-wizard.md#what-is-automatic-onboarding).
   
   Hvis du vil onboarde andre enheder, skal du se [trin 4](#step-4-set-up-and-configure-defender-for-business).

4.  **[Få vist og rediger dine sikkerhedspolitikker](mdb-configure-security-settings.md)**. Defender for Business indeholder standardsikkerhedspolitikker for næste generations beskyttelse og firewallbeskyttelse, der kan anvendes på virksomhedens enheder. Disse forudkonfigurerede sikkerhedspolitikker bruger anbefalede indstillinger, så du er beskyttet, så snart dine enheder er onboardet til Defender for Business. Og du kan redigere politikkerne eller oprette nye.

### <a name="step-4-set-up-and-configure-defender-for-business"></a>Trin 4: Konfigurer Defender for Business

Hvis du vælger ikke at bruge installationsguiden, kan du se følgende diagram, der viser den [overordnede konfigurationsproces](mdb-setup-configuration.md#the-setup-and-configuration-process) for Defender for Business.

[:::image type="content" source="media/mdb-setup-process-2.png" alt-text="Konfigurationsprocessen for Defender for Business.":::](mdb-setup-configuration.md)

Hvis du har brugt installationsguiden, men du har brug for at onboarde flere enheder, f.eks. ikke-Windows-enheder, skal du gå direkte til trin 4 i følgende procedure:

1. **[Gennemse kravene](mdb-requirements.md)** til at konfigurere og bruge Defender for Business. 

2. **[Tildel roller og tilladelser](mdb-roles-permissions.md)** på Microsoft 365 Defender-portalen.

   - [Få mere at vide om roller i Defender for Business](mdb-roles-permissions.md#roles-in-defender-for-business). 
   - [Få vist eller rediger rolletildelinger for dit sikkerhedsteam](mdb-roles-permissions.md#view-or-edit-role-assignments).

3. **[Konfigurer mailmeddelelser](mdb-email-notifications.md)** til dit sikkerhedsteam.

   - [Få mere at vide om typer af mailmeddelelser](mdb-email-notifications.md#types-of-email-notifications).
   - [Få vist og rediger indstillinger for mailbeskeder](mdb-email-notifications.md#view-and-edit-email-notifications).

4. **[Onboarde enheder](mdb-onboard-devices.md)**. Med Defender for Business har du flere muligheder at vælge imellem til onboarding af din virksomheds enheder. Først skal du vælge det operativsystem, du vil onboarde.

   | Enhedstype | Onboardingmetoder |
   |:---|:---|
   | [Windows-klienter](mdb-onboard-devices.md) | Vælg en af følgende indstillinger for at føje Windows-klientenheder til Defender for Business:<ul><li>Lokalt script (til onboarding af enheder manuelt på Microsoft 365 Defender-portalen)</li><li>Gruppepolitik (hvis du allerede bruger Gruppepolitik og foretrækker denne metode)</li><li>Microsoft Intune (*anbefales*; inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md))</li></ul> |
   | [Mac](mdb-onboard-devices.md) | Vælg en af følgende muligheder for at onboarde Mac:<ul><li>Lokalt script til Mac (*anbefales*)</li><li>Microsoft Intune til Mac (Intune er inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md))</li></ul><p>Vi anbefaler, at du bruger et lokalt script til at onboarde Mac. Selvom du kan [konfigurere tilmelding til Mac-enheder i Intune](/mem/intune/enrollment/macos-enroll), er det lokale script den nemmeste metode til onboarding af Mac til Defender for Business. |
   | Windows Server- og Linux-servere | *Muligheden for at onboarde en forekomst af Windows Server eller Linux Server er i øjeblikket en prøveversion og kræver en ekstra licens*. Se følgende artikler for at få mere at vide: <ul><li>[Defender for Business-krav](mdb-requirements.md)</li><li>[Onboarde enheder til Defender for Business](mdb-onboard-devices.md)</li></ul> |
   | [Mobilenheder](mdb-onboard-devices.md) | Du skal Microsoft Intune til at onboarde mobilenheder, f.eks. Android- og iOS-/iPadOS-enheder. Hvis du har [Microsoft 365 Business Premium](../../business-premium/index.md), er Intune en del af dit abonnement. Intune kan også købes separat. Se følgende ressourcer for at få hjælp til at tilmelde disse enheder til Intune:<ul><li>[Tilmeld Android-enheder](/mem/intune/enrollment/android-enroll)</li><li>[Tilmeld iOS- eller iPadOS-enheder](/mem/intune/enrollment/ios-enroll)</li></ul> |

5. **[Få vist og konfigurer dine sikkerhedspolitikker](mdb-configure-security-settings.md)**. Når du har onboardet din virksomheds enheder til Defender for Business, er det næste trin at få vist og redigere dine sikkerhedspolitikker og -indstillinger. Defender for Business indeholder forudkonfigurerede sikkerhedspolitikker, der bruger anbefalede indstillinger. Men du kan redigere indstillingerne, så de passer til dine forretningsbehov.

   | Handling | Beskrivelse |
   |:---|:---|
   | [Vælg, hvor du vil administrere dine sikkerhedspolitikker og -enheder](mdb-configure-security-settings.md#choose-where-to-manage-security-policies-and-devices). | Hvis du vælger den [forenklede konfigurationsproces](mdb-simplified-configuration.md), kan du få vist og administrere dine sikkerhedspolitikker på portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Men du er ikke begrænset til denne indstilling. Hvis du har brugt [Intune](/mem/intune/protect/), kan du blive ved med at bruge Microsoft Endpoint Manager Administration til at administrere dine sikkerhedspolitikker og -enheder. |
   | [Få vist eller rediger dine beskyttelsespolitikker i næste generation](mdb-configure-security-settings.md#view-or-edit-your-next-generation-protection-policies). | Næste generations beskyttelsesindstillinger omfatter beskyttelse i realtid, blokering ved første øjekast, netværksbeskyttelse, handlinger, der skal udføres på potentielt uønskede apps, og antivirus planlagte scanninger.  |
   | [Få vist eller rediger firewallpolitikkerne](mdb-configure-security-settings.md#view-or-edit-your-firewall-policies-and-custom-rules). | Firewallbeskyttelse bestemmer, hvilken netværkstrafik der må overføres til og fra virksomhedens enheder. [Brugerdefinerede regler](mdb-custom-rules-firewall.md) kan bruges til at definere undtagelser fra firewallpolitikkerne. |
   | [Konfigurer filtrering af webindhold](mdb-configure-security-settings.md#set-up-web-content-filtering). | Filtrering af webindhold gør det muligt for dit sikkerhedsteam at spore og regulere adgangen til websteder baseret på deres indholdskategorier, f.eks. indhold beregnet til voksne, høj båndbredde, juridisk ansvar, fritid eller ikke-kategoriseret. |
   | [Gennemse indstillingerne for avancerede funktioner](mdb-configure-security-settings.md#review-settings-for-advanced-features). | I Defender for Business er sikkerhedsfunktioner forudkonfigureret til anbefalede indstillinger. Du kan gennemse og redigere indstillingerne, så de passer til dine forretningsbehov. <br/><br/>Hvis du vil have adgang til indstillinger for avancerede funktioner, skal du gå til **Indstillinger** > **Slutpunkter** > **Generelle** > **avancerede funktioner** på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). |
   | [Få vist og rediger andre indstillinger](mdb-configure-security-settings.md#access-your-settings-in-the-microsoft-365-defender-portal) på Microsoft 365 Defender-portalen. | Ud over sikkerhedspolitikker, der anvendes på enheder, er der andre indstillinger, som du kan få vist og redigere i Defender for Business. Du kan f.eks. angive den tidszone, der skal bruges, og du kan onboarde (eller offboard) enheder. |

## <a name="start-using-defender-for-business"></a>Begynd at bruge Defender for Business

I de næste 30 dage anbefaler vi, at du afprøver dine nye sikkerhedsfunktioner, som beskrevet i følgende afsnit:

- [Brug dashboardet Administration af sårbarheder & Threat &](#use-the-threat--vulnerability-management-dashboard) 
- [Få vist og reager på registrerede trusler](#view-and-respond-to-detected-threats)
- [Gennemse sikkerhedspolitikker](#review-security-policies)
- [Forbered dig på løbende sikkerhedsstyring](#prepare-for-ongoing-security-management)

### <a name="use-the-threat--vulnerability-management-dashboard"></a>Brug dashboardet Administration af sårbarheder & Threat &

Defender for Business indeholder et dashboard til administration af sårbarheder & threat &, der er designet til at spare tid og kræfter på dit sikkerhedsteam. [Brug dashboardet Administration af sårbarheder & Threat &](mdb-view-tvm-dashboard.md).

- Få vist din eksponeringsscore, der er knyttet til enheder i din organisation.
- Få vist dine vigtigste sikkerhedsanbefalinger, f.eks. adressering af nedsat kommunikation med enheder, aktivér firewallbeskyttelse, eller opdater Microsoft Defender Antivirus-definitioner.
- Få vist afhjælpningsaktiviteter, f.eks. filer, der er sendt til karantæne, eller sikkerhedsrisici, der findes på enheder.

### <a name="view-and-respond-to-detected-threats"></a>Få vist og reager på registrerede trusler

Når der registreres trusler, og beskeder udløses, oprettes der hændelser. Organisationens sikkerhedsteam kan få vist og administrere hændelser på Microsoft 365 Defender portalen. [Få vist og reager på registrerede trusler](mdb-view-manage-incidents.md). 

- [Få vist og administrer hændelser](mdb-view-manage-incidents.md).
- [Reager på og afhjælp trusler](mdb-respond-mitigate-threats.md).
- [Gennemse mæglingshandlinger i Løsningscenter](mdb-review-remediation-actions.md).
- [Få vist og brug rapporter](mdb-reports.md).

### <a name="review-security-policies"></a>Gennemse sikkerhedspolitikker

I Defender for Business konfigureres sikkerhedsindstillinger via politikker, der anvendes på enheder. Defender for Business indeholder forudkonfigurerede politikker, der hjælper med at beskytte din virksomheds enheder, så snart de er onboardet, og beskytter din organisation mod identitet, enhed, program og dokumentering af sikkerhedstrusler. [Gennemse sikkerhedspolitikker](mdb-view-edit-create-policies.md).

- [Få mere at vide om dine standardpolitikker](mdb-view-edit-create-policies.md#default-policies-in-defender-for-business).
- [Få vist dine eksisterende politikker](mdb-view-edit-create-policies.md#view-your-existing-policies).
- [Forstå politikrækkefølgen](mdb-policy-order.md). 
- [Forstå konfigurationsindstillingerne for næste generation](mdb-next-gen-configuration-settings.md).
- [Gennemse dine standardindstillinger for firewall](mdb-firewall.md#default-firewall-settings-in-defender-for-business).
- [Forstå firewallindstillinger, du kan konfigurere](mdb-firewall.md#firewall-settings-you-can-configure-in-defender-for-business).
- [Konfigurer filtrering af webindhold](mdb-configure-security-settings.md#set-up-web-content-filtering). Filtrering af webindhold gør det muligt for dit sikkerhedsteam at spore og regulere adgangen til websteder baseret på deres indholdskategorier. Den er ikke slået til som standard, så du skal konfigurere den, hvis du vil have denne funktion for din organisation.
  
### <a name="prepare-for-ongoing-security-management"></a>Forbered dig på løbende sikkerhedsstyring

Nye sikkerhedshændelser, f.eks. trusselsregistrering på en enhed, tilføjelse af nye enheder og medarbejdere, der tilmelder sig eller forlader organisationen, kræver, at du administrerer sikkerheden. I Defender for Business er der mange måder, du kan administrere enhedssikkerhed på.

- [Få vist en liste over onboardede enheder](mdb-manage-devices.md#view-the-list-of-onboarded-devices) for at se deres risikoniveau, eksponeringsniveau og tilstand.
- [Udfør handlinger på en enhed](mdb-manage-devices.md#take-action-on-a-device-that-has-threat-detections) , der har trusselsregistreringer.
- [Om bord på en enhed til Defender for Business](mdb-manage-devices.md#onboard-a-device).
- [Om bord på en enhed fra Defender for Business](mdb-manage-devices.md#offboard-a-device).

## <a name="additional-resources"></a>Yderligere ressourcer

- [Oversigt over Defender for Business](mdb-overview.md)
- [Selvstudier og simuleringer i Defender for Business](mdb-tutorials.md)
- [Video: Enterprise-Grade Beskyttelse af små & mellemstore virksomheder](https://youtu.be/umhUNzMqZto)
- [Hent Defender for Business](get-defender-business.md)
