---
title: Konfigurer Microsoft 365 til frontlinjemedarbejdere
author: samanro
ms.author: samanro
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du konfigurerer Microsoft 365 med de tjenester og funktioner, du har brug for til dine frontlinjearbejdere.
ms.localizationpriority: high
ms.collection:
- m365-frontline
- m365solution-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 25f33208cd52520d810efbb9d48643595c955f3e
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823905"
---
# <a name="set-up-microsoft-365-for-frontline-workers"></a>Konfigurer Microsoft 365 til frontlinjemedarbejdere

Hvis du vil konfigurere Microsoft 365 til frontlinjearbejdere, skal du følge denne overordnede proces:

1. **[Identificer dine scenarier](#step-1-identify-your-scenarios)**: Hvilke scenarier vil du implementere for frontlinjemedarbejderne? Når du har bestemt, hvilke scenarier du ønsker, kan du bruge tabellen nedenfor til at identificere de påkrævede apps og tjenester for hvert scenarie, du vil implementere.
1. **[Konfigurer dit miljø og kernen i Microsoft 365](#step-2-set-up-your-environment-and-core-microsoft-365)**: Følg installationsvejledningerne i Microsoft 365 Administration for at konfigurere Microsoft 365. Læs videre for at få mere at vide om, hvordan du får adgang til disse vejledninger.
1. **[Konfigurer Microsoft Teams](#step-3-set-up-microsoft-teams)**: Brug enten onboardingguiden eller Installation af teams i stor skala til at konfigurere tjenesten og oprette dine teams.
1. **[Konfigurer alle andre tjenester, der skal bruges til dit scenarie](#step-4-set-up-other-services)**: Følg instruktionerne i afsnittene nedenfor for at konfigurere disse tjenester.
1. **[Konfigurer apps](#step-5-configure-apps-for-your-scenario)**: Når alt er konfigureret og konfigureret i Administration, kan du følge vejledningen til dine scenarier for yderligere at konfigurere de apps, du skal bruge til hvert scenarie.
1. **[Enheder](#step-6-set-up-devices)**: Konfigurer delte og personlige enheder, så de fungerer sammen med Microsoft 365 og Microsoft Teams, og gør det muligt for dine frontlinjemedarbejdere at kommunikere mere sikkert i din organisation.

:::image type="content" source="media/m365-frontline-setup-steps.png" alt-text="Trin til konfiguration af Microsoft 365 til frontlinjemedarbejdere." lightbox="media/m365-frontline-setup-steps.png":::

## <a name="step-1-identify-your-scenarios"></a>Trin 1: Identificer dine scenarier

I følgende tabel vises scenarierne for frontlinjemedarbejderne. Du kan læse en oversigt over hvert scenarie i [vælge dine scenarier](flw-choose-scenarios.md) og finde ud af præcis, hvad du skal konfigurere, ved at følge linkene til hvert scenarie og til hver enkelt app eller tjeneste, der er påkrævet.

| Scenario | Påkrævede tjenester |
|  ------- | -------  |
| [Teamkommunikation og samarbejde](flw-team-collaboration.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Mail med Exchange Online](#set-up-email-with-exchange-online) |
| [Virksomhedskommunikation](flw-corp-comms.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Viva Connections](#set-up-viva-connections) <br>[Yammer](#set-up-your-organizations-social-network-with-yammer) |
| [Virtuelle aftaler](virtual-appointments.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) |
| [Engagere dine medarbejdere og fokusere på medarbejdernes trivsel](flw-wellbeing-engagement.md)| [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Viva Connections](#set-up-viva-connections) <br>[Yammer](#set-up-your-organizations-social-network-with-yammer) |
| [Planlæg dit team med vagter](shifts-for-teams-landing-page.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) |
| [Onboarder nye medarbejdere](/sharepoint/onboard-employees)| [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[SharePoint](#set-up-sites-with-sharepoint-in-microsoft-365) <br>[Viva Connections](#set-up-viva-connections) <br>[Viva Learning](#set-up-viva-learning)|
| [Løbende træning](flw-onboarding-training.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Viva Learning](#set-up-viva-learning) |
| [Gør forretningsprocesserne mere forenklede](simplify-business-processes.md) | [Microsoft Teams](#step-3-set-up-microsoft-teams) <br>[Power Apps, Power Automate og Power BI](#set-up-power-apps-power-automate-and-power-bi) |

Nogle tjenester er kun inkluderet i F3-licenser, f.eks. mail og Power Platform. Se [Forstå brugertyper og licenser for frontlinemedarbejdere](flw-licensing-options.md) for at finde ud af, hvilken type licenser du skal bruge til dine brugere.

## <a name="step-2-set-up-your-environment-and-core-microsoft-365"></a>Trin 2: Konfigurer dit miljø og microsoft 365-kernemiljøet

Microsoft 365 Administration har en række [konfigurationsvejledninger](/microsoft-365/enterprise/setup-guides-for-microsoft-365), der fører dig gennem trinnene til konfiguration af produkter, sikkerhedsfunktioner og samarbejdsværktøjer i Microsoft 365. Du kan få adgang til installationsvejledningerne på [siden Med vejledning til konfiguration](https://aka.ms/setupguidance) i Microsoft 365 Administration.

1. Brug vejledningen [Forbered dit miljø](https://aka.ms/prepareyourenvironment) til at forberede organisationens miljø til Microsoft 365- og Office 365-tjenester.
1. Brug [installationsvejledningen til Microsoft 365](https://aka.ms/microsoft365setupguide) til at konfigurere produktivitetsværktøjer, sikkerhedspolitikker og funktioner til enhedshåndtering. Du kan også bruge denne rådgiver til at konfigurere organisationens enheder.

## <a name="step-3-set-up-microsoft-teams"></a>Trin 3: Konfigurer Microsoft Teams

I forbindelse med et pilotprojekt kan du bruge guiden Frontline worker onboarding til at oprette et enkelt team, der er konfigureret til frontlinjearbejdere. Hvis du vil have en trinvis vejledning, skal du se [Brug onboardingguiden Frontline Worker til at få din frontlinjearbejdsstyrke op at køre](flw-onboarding-wizard.md).

I forbindelse med komplette udrulninger skal du følge vejledningen i [Installér teams i stor skala for frontlinjemedarbejdere](deploy-teams-at-scale.md).

## <a name="step-4-set-up-other-services"></a>Trin 4: Konfigurer andre tjenester

### <a name="set-up-email-with-exchange-online"></a>Konfigurer mail med Exchange Online

Hvis du ønsker, at dine frontlinjeledere og -medarbejdere skal have adgang til mail, skal du konfigurere mail i Microsoft 365. Brugerne skal have en F3-licens for at få adgang til mail. Følg [konfigurationsvejledningen til mail](https://aka.ms/office365setup) for at konfigurere den.

Bemærk, at dine brugere også kan installere Outlook-appen, så de kan bruge den til deres mail, så du skal sørge for at dele, hvor du kan downloade Outlook-appen med dem.

### <a name="set-up-sites-with-sharepoint-in-microsoft-365"></a>Konfigurer websteder med SharePoint i Microsoft 365

[Med SharePoint](/sharepoint/sharepoint-online) kan du dele dokumenter og oprette websteder. Brug [installationsvejledningen til SharePoint](https://aka.ms/spoguidance) i Microsoft 365 Administration til at konfigurere den.

### <a name="set-up-employee-experiences-with-viva-modules"></a>Konfigurer medarbejderoplevelser med Viva-moduler

[Microsoft Viva](/viva/microsoft-viva-overview) hjælper medarbejderne med at få en integreret medarbejderoplevelse, der samler kommunikation, viden, læring, ressourcer og indsigt i arbejdsflowet. Microsoft Viva har flere moduler, der kan bruges sammen med Microsoft Teams til at skabe medarbejderoplevelser.

#### <a name="set-up-viva-connections"></a>Konfigurer Viva Connections

Brug [Viva Connections](/viva/connections/viva-connections-overview) til at oprette et dashboard, der hjælper med at engagere og informere frontlinjemedarbejderne. Viva Connections er en app, der kan tilpasses i Microsoft Teams, og som giver alle en tilpasset destination til at finde relevante nyheder, samtaler og de værktøjer, de har brug for for at få succes. 

Følg [konfigurationsvejledningen Byg din medarbejderoplevelse](https://aka.ms/EmployeeExperienceDashboard) for at konfigurere den. Få mere at vide om [konfiguration af Viva Connections](/viva/connections/guide-to-setting-up-viva-connections).

#### <a name="set-up-viva-learning"></a>Konfigurer Viva Learning

[Viva Learning](/viva/learning/) er en app i Microsoft Teams, der giver medarbejderne mulighed for at gøre læring til en naturlig del af dagen ved at få læring ind i arbejdsflowet inden for de værktøjer og platforme, de allerede bruger. Se [Konfigurer Microsoft Viva Learning i Teams Administration](/viva/learning/set-up-viva-learning) for at få mere at vide om, hvordan du konfigurerer Viva Learning.

### <a name="set-up-your-organizations-social-network-with-yammer"></a>Konfigurer din organisations sociale netværk med Yammer

[Yammer](/yammer) hjælper med at forbinde din arbejdsstyrke på tværs af din virksomhed. Brug [Yammer-udrulningsrådgiveren](https://aka.ms/yammerdeploymentguide) til at konfigurere den.

### <a name="set-up-power-apps-power-automate-and-power-bi"></a>Konfigurer Power Apps, Power Automate og Power BI

Du kan bruge alle disse apps i Microsoft Teams. Du kan få flere oplysninger om, hvordan du konfigurerer dem, under:

- [Integration af Power Apps og Microsoft Teams](/powerapps/teams/overview)
- [Power Automate – brug flow i Microsoft Teams](/power-automate/teams/overview)
- [Samarbejd i Microsoft Teams med Power BI](/power-bi/collaborate-share/service-collaborate-microsoft-teams)
- [Power Virtual Agents-app i Microsoft Teams](/power-virtual-agents/teams/fundamentals-what-is-power-virtual-agents-teams)
- [Power Apps](/microsoftteams/manage-power-platform-apps)

## <a name="step-5-configure-apps-for-your-scenario"></a>Trin 5: Konfigurer apps til dit scenarie

Når alt er konfigureret og konfigureret i Administration, kan du følge vejledningen til dine scenarier for yderligere at konfigurere de apps, du skal bruge til hvert scenarie.

Scenarier og apps

| Scenario | Godkendelser | Bookinger | Lister | Ros | Skift | Opgaver | Opdateringer |
| :---- | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| [Teamkommunikation og samarbejde](flw-team-collaboration.md) | &#x2705; | &nbsp; | &#x2705; | &#x2705; | &nbsp; | &#x2705; | &#x2705; |
| [Virksomhedskommunikation](flw-corp-comms.md) |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |  &nbsp; |
| [Virtuelle aftaler med Microsoft Teams og Bookings-appen](bookings-virtual-visits.md) |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp;|  &nbsp; |
| Trivsel & engagement |  &nbsp; |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; |
| [Planlæg dit team med vagter](shifts-for-teams-landing-page.md) |  &nbsp; | &nbsp; | &#x2705; |  &nbsp; | &#x2705; | &#x2705; | &#x2705; |
| [Oplæring: Onboarder nye medarbejdere](/sharepoint/onboard-employees) |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| Løbende træning |  &nbsp; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| [Gør forretningsprocesserne mere forenklede](simplify-business-processes.md) | &#x2705; |  &nbsp; | &#x2705; |  &nbsp; |  &nbsp; | &#x2705; | &#x2705; |
| Administrer websteder, butikker og projekter | &#x2705; |  &nbsp; | &#x2705; |  &nbsp; | &nbsp; | &#x2705; | &#x2705; |

## <a name="step-6-set-up-devices"></a>Trin 6: Konfigurer enheder

Hvis du vil konfigurere delte og personlige enheder til at arbejde med Microsoft 365 og Microsoft Teams og gøre det muligt for frontlinjemedarbejderne at kommunikere mere sikkert i din organisation, skal du se [Administrer mobilenheder for frontlinjearbejdere](flw-devices.md).
