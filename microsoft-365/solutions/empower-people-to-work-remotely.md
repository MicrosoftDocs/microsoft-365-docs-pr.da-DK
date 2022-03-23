---
title: Konfigurer din infrastruktur til hybridarbejde med Microsoft 365
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-overview
- M365initiative-coredeploy
ms.custom: seo-marvel-jun2020
keywords: arbejde hjemmefra, arbejde fra hjemmet, hybrid, fjernarbejder, hybridarbejde, fjernmedarbejdere, hybridforbindelse, fjernadgang, fjernadgang, telearbejde, telearbejde, mobilarbejde, fjernjob, arbejde hvor som helst, fleksibel arbejdsplads
description: Gennemgå lagene af infrastruktur, så dine hybridmedarbejdere kan få sikker adgang til lokale og Microsoft 365 ressourcer.
ms.openlocfilehash: 87d72307f3e6a2b254bdbde21d07fc146806b89d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590065"
---
# <a name="set-up-your-infrastructure-for-hybrid-work-with-microsoft-365"></a>Konfigurer din infrastruktur til hybridarbejde med Microsoft 365

For at sikre og optimere din medarbejders produktivitet og samarbejde skal du give medarbejdere på stedet og eksterne medarbejdere adgang til din organisations lokale og skybaserede oplysninger, værktøjer og ressourcer nemt og sikkert. Denne løsning gennemgår udrulningen af vigtige infrastrukturlag, der giver dine medarbejdere mulighed for at udføre deres bedste arbejde, uanset hvor de befinder sig.

Hybridmedarbejdere kan arbejde på stedet eller eksternt på en kombination af placeringer. Det er vigtigt for mange organisationer at give medarbejderne tilladelse til at arbejde væk fra et traditionelt kontor:

- Ansætte og bevare medarbejdere, der ikke er i stand til at flytte eller kræve et fleksibelt arbejdsmiljø.
- Reducer antallet af medarbejdere, der skal arbejde, så medarbejdere har mere tid til at være produktive og til at reducere stressende aktiviteter uden for arbejdet.
- Spar kontorplads.

Microsoft 365 har de funktioner, der gør det muligt for dine hybridmedarbejdere at arbejde enten på stedet eller eksternt.

![Giv dine hybridmedarbejdere nye Microsoft 365.](../media/empower-people-to-work-remotely/2-m365-remoteworker-solution-businessoverview.png)

> [!NOTE]
> Hvis du er ny bruger af Microsoft 365, skal du [se disse ressourcer](https://www.microsoft.com/microsoft-365).

Se denne video for at få et overblik over installationsprocessen.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F1af]

For it-fagfolk, der administrerer onsite og skybaseret infrastruktur for at aktivere hybridmedarbejderes produktivitet, indeholder denne løsning disse vigtige funktioner:

- Tilsluttet

  Dine medarbejdere kan til enhver tid og fra hvor som helst i verden få adgang til:

  - Skybaserede tjenester og data i dit Microsoft 365 abonnement.

  - Organisationsressourcer, f.eks. dem, der tilbydes af lokale programdatacentre.

- Sikker

  Logons beskyttes med multifaktorgodkendelse (MFA) og indbyggede sikkerhedsfunktioner i Microsoft 365 og Windows 11 eller 10 for malware, ondsindede angreb og datatab.

- Administreret

  Din hybridmedarbejders enheder kan administreres fra skyen med sikkerhedsindstillinger, tilladte apps og kræve overholdelse af systemets tilstand.

- Samarbejdsorienteret og produktivt

  Dine hybridmedarbejdere kan være lige så produktive som lokale på en måde, der i høj grad samarbejder med:

  - Onlinemøder og chatsessioner med Teams.

  - Delte arbejdsområder til skybaseret fillagring med global tilgængelighed og samarbejde i realtid med SharePoint og OneDrive.

  - Delte opgaver og arbejdsprocesser for at opdele arbejdet og få tingene gjort.

For at få en problemfri logonoplevelse skal dine lokale Active Directory-domæneservices (AD DS)-brugerkonti synkroniseres med Azure Active Directory (Azure AD). For at beskytte Windows 11 eller 10 enheder skal de være tilmeldt Intune. Her er en oversigt over infrastrukturen på højt niveau.

![Den grundlæggende infrastruktur for hybridmedarbejdere med Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-basic-infrastructure.png)

For at aktivere funktionerne i Microsoft 365 for dine hybridmedarbejdere skal du bruge disse Microsoft 365 funktioner.

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|MFA gennemtvunget med sikkerhedsstandard|Beskyt dig mod kompromitterede identiteter og enheder ved at kræve en anden form for godkendelse til logon. Sikkerhedsstandarden kræver MFA for alle brugerkonti.|Microsoft 365 E3 eller E5|
|MFA gennemtvunget med Betinget adgang|Kræv MFA baseret på egenskaberne for logon med politikker for betinget adgang.|Microsoft 365 E3 eller E5|
|MFA gennemtvunget med risikobaseret betinget adgang|Kræv MFA baseret på risikoen ved at logge på med Azure AD Identity Protection.|Microsoft 365 E5 eller E3 med Azure AD Premium P2-licenser|
|Self-Service til nulstilling af adgangskode (SSPR)|Giv dine brugere mulighed for at nulstille eller låse deres adgangskoder eller konti op.|Microsoft 365 E3 eller E5|
|Azure AD-programproxy|Giv sikker fjernadgang til webbaserede programmer, der hostes på intranetservere.|Kræver separat betalt Azure-abonnement|
|Azure Point-to-Site VPN|Opret en sikker forbindelse fra en fjernmedarbejders enhed til intranettet via et virtuelt Azure-netværk.|Kræver separat betalt Azure-abonnement|
|Windows 365|Understøtte eksterne medarbejdere, der kun kan bruge deres personlige og ikke-administrerede enheder med Windows 365 Cloud-pc'er.|Kræver separat betalt Azure-abonnement|
|Fjernskrivebord |Giv medarbejdere mulighed for at oprette Windows-baserede computere på intranettet.|Microsoft 365 E3 eller E5|
|Gateway til Fjernskrivebord-tjenester|Kryptér kommunikation, og forbyd, at RDS-værter bliver direkte eksponeret for internettet.|Kræver separate Windows Serverlicenser|
|Microsoft Intune|Administrer enheder og programmer.|Microsoft 365 E3 eller E5|
|Konfigurationsstyring|Administrer softwareinstallationer, opdateringer og indstillinger på dine enheder|Kræver separate Konfigurationsstyring licenser|
|Endpoint Analytics|Afgør, om dine Windows er parate til opdateringer.|Kræver separate Konfigurationsstyring licenser|
|Windows Autopilot|Konfigurer og forudkonfigurer nye Windows 11 eller 10 enheder til produktiv brug.|Microsoft 365 E3 eller E5|
|Microsoft Teams, Exchange Online, SharePoint Online og OneDrive, Microsoft 365 Apps, Microsoft Power Platform Yammer|Opret, kommuniker og samarbejd.|Microsoft 365 E3 eller E5|
||||

Du kan finde flere kriterier til sikkerhed og overholdelse [af regler og standarder under Installere sikkerhed og overholdelse for eksterne medarbejdere](empower-people-to-work-remotely-security-compliance.md).

<a name="poster"></a> Du kan finde en tosidet oversigt over denne løsning på plakaten [Giv hybridmedarbejdere nye rettigheder](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf).

[![Gør plakaten for hybridmedarbejdere bedre.](../media/empower-people-to-work-remotely/empower-remote-workers-poster.png)](https://download.microsoft.com/download/9/b/b/9bb5fa79-74e9-497b-87c5-4021e53d9fc2/hybrid-worker-infrastructure.pdf)

## <a name="provide-hybrid-working-for-all-of-your-workers"></a>Give hybridarbejde for alle dine medarbejdere

Du kan gøre alle dine medarbejdere i stand til at være produktive overalt med disse enheder:

- En moderne enhed, f.eks. en bærbar Surface-computer og Windows 11 eller 10, som har funktioner, sikkerhed og ydeevne til at få adgang til Microsoft 365-skyapps og -tjenester direkte via internettet.

- Alle enheder, herunder ældre bærbare computere eller stationære computere, der bruges hjemmefra, og som har adgang til Microsoft 365-apps og tjenester indirekte via en [Windows 365 Cloud-pc](empower-people-to-work-remotely-remote-access.md#deploy-windows-365-to-provide-remote-access-for-remote-workers-using-personal-devices). Denne indstilling giver høj ydeevne, stærk sikkerhed og forenklet it-administration.

## <a name="next-steps"></a>Næste trin

Brug disse trin til at sikre og optimere adgang til organisationens servere og skytjenester og maksimere din hybridmedarbejders produktivitet.

1. [Forøg sikkerheden for logon med MFA](empower-people-to-work-remotely-secure-sign-in.md)
2. [Give fjernadgang til apps og tjenester i det lokale miljø](empower-people-to-work-remotely-remote-access.md)
3. [Installér sikkerheds- og overholdelsestjenester](empower-people-to-work-remotely-security-compliance.md)
4. [Installér slutpunktsstyring til dine enheder, pc'er og andre slutpunkter](empower-people-to-work-remotely-manage-endpoints.md)
5. [Installér produktivitetsapps og -tjenester for hybridmedarbejdere](empower-people-to-work-remotely-teams-productivity-apps.md)
6. [Oplære dine medarbejdere og adressere feedback om brug](empower-people-to-work-remotely-train-monitor-usage.md)

[![Trinnene til at konfigurere din infrastruktur til hybridarbejde med Microsoft 365.](../media/empower-people-to-work-remotely/remote-workers-step-grid.png)](empower-people-to-work-remotely-secure-sign-in.md)

Hvis du vil se, hvordan en fiktiv, men repræsentativ, multi national organisation konfigurerer sin infrastruktur til hybridarbejde, skal du se [Contosos COVID-19-svar og infrastruktur til hybridarbejde](contoso-remote-onsite-work.md).
