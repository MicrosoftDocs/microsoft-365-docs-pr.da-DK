---
title: Løs problemer, der er fundet af værktøjet til vurdering af parathed
description: Detaljerede handlinger, der skal tages for hvert problem, som værktøjet finder
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: badf2d65f2b29e265a1312cb1d5f4802a44f3cb3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63594354"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Løs problemer, der er fundet af værktøjet til vurdering af parathed

For hver kontrol rapporterer værktøjet et af fire mulige resultater:

| Resultat  | Betydning |
| ----- | ----- |
| Klar | Der kræves ingen handling, før tilmeldingen fuldføres. |
| Vejledning | Følg trinnene i værktøjet eller denne artikel for at få den bedste oplevelse med registrering og for brugere. <br><br> Du *kan* fuldføre tilmeldingen, men du skal løse disse problemer, før du installerer din første enhed. |
| Ikke klar | **Din tilmelding mislykkes, hvis du ikke løser disse problemer.** <br><br> Følg trinnene i værktøjet eller denne artikel for at løse dem. |
| Error | Den Azure Active Directory (AD) rolle, du bruger, har ikke tilstrækkelige tilladelser til at køre denne kontrol. |

> [!NOTE]
> De resultater, der rapporteres af dette værktøj, afspejler kun status for dine indstillinger på det tidspunkt, hvor du kørte det. Hvis du senere foretager ændringer i politikker i Microsoft Intune, Azure Active Directory eller Microsoft 365, kan elementer, der var "klar", blive "Ikke klar". Hvis du vil undgå problemer med microsoft-administrerede skrivebordshandlinger, skal du kontrollere de specifikke indstillinger, der er beskrevet i denne artikel, før du ændrer eventuelle politikker.

## <a name="microsoft-intune-settings"></a>Microsoft Intune indstillinger

Du kan få adgang til indstillinger i Intune Microsoft Endpoint Manager [Administration](https://endpoint.microsoft.com).

### <a name="autopilot-deployment-profile"></a>Autopilot-udrulningsprofil

Du bør ikke have nogen eksisterende Autopilot-profiler, som er tildelt til eller dynamiske grupper med Microsoft Managed Desktop-enheder. Microsoft Managed Desktop bruger Autopilot til at konfigurere nye enheder. Hvis du har en eksisterende Autopilot-installationsprofil, skal indstillingen Konvertér alle målrettede enheder til **Autopilot** være indstillet til **Nej, for** at parathedstesten for Microsoft Managed Desktop Autopilot kan lykkes.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har en Autopilot-profil, der er tildelt til alle enheder. <br><br> Få mere at vide under [Tilmeld Windows enheder i Intune ved hjælp af Windows Autopilot](/mem/autopilot/enrollment-autopilot). Når Microsoft Managed Desktop er tilmeldt, skal du indstille din Autopilot-politik til at udelukke **enheder med moderne arbejdsplads – alle** Azure AD-grupper.
| Vejledning | Sørg for, at dine Autopilot-profiler målretter en tildelt eller dynamisk Azure AD-gruppe, der ikke omfatter Microsoft-administrerede skrivebordsenheder. <br><br> Få mere at vide under [Tilmeld Windows enheder i Intune ved hjælp af Windows Autopilot](/mem/autopilot/enrollment-autopilot). Når Microsoft Managed Desktop er tilmeldt, skal du indstille dine Autopilot-profiler til at udelukke **enheder med moderne arbejdsplads – alle** Azure AD-grupper. |

### <a name="certificate-connectors"></a>Certifikatforbindelser

Hvis du har nogen certifikatforbindelser, der skal bruges af de enheder, du vil tilmelde i Microsoft Managed Desktop, bør forbindelser ikke have nogen fejl. Kun én af følgende råd gælder for din situation, så kontrollér dem omhyggeligt.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Der er ingen certifikatforbindelser. Det er muligt, at du ikke har brug for forbindelser, men du bør evaluere, om du skal bruge nogle til netværksforbindelsen på dine Microsoft-administrerede skrivebordsenheder. <br><br> Få mere at vide under [Forbered certifikater og netværksprofiler til Microsoft Managed Desktop](certs-wifi-lan.md). |
| Vejledning | Mindst én certifikatforbindelse har en fejl. Hvis du har brug for denne forbindelse til at levere certifikater til Enheder med Microsoft-administreret skrivebord, skal du rette fejlen. <br><br> Få mere at vide under [Forbered certifikater og netværksprofiler til Microsoft Managed Desktop](certs-wifi-lan.md). |
| Vejledning | Du har mindst én certifikatforbindelse, og der rapporteres ingen fejl. Men før installationen kan være nødvendigt at oprette en profil for at genbruge forbindelsen til Microsoft-administrerede enheder på computeren. <br><br> Få mere at vide under [Forbered certifikater og netværksprofiler til Microsoft Managed Desktop](certs-wifi-lan.md). |

### <a name="company-portal"></a>Firmaportal

Microsoft Managed Desktop kræver, at it-administratorer installerer Intune-firmaportal til deres brugere med Microsoft-administrerede desktopenheder.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har ikke installeret Firmaportal for dine brugere. Køb Firmaportal og gennemtving en synkronisering mellem Intune og Microsoft Store til Virksomheder. <br><br> Du kan finde flere oplysninger [i Intune-firmaportal på enheder](../get-started/company-portal.md).

### <a name="conditional-access-policies"></a>Politikker for betinget adgang

Politikker for betinget adgang kan ikke forhindre Microsoft Managed Desktop i at administrere din Azure AD-organisation (lejer) i Intune og Azure AD.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har mindst én politik for betinget adgang, der er målrettet alle brugere. <br><br> Under tilmelding udelader vi Microsoft Managed Desktop-tjenestekonti fra relevante politikker for betinget adgang og anvender nye politikker for betinget adgang for at begrænse adgangen til disse konti. <br><br> Efter tilmelding kan du gennemse politikken for betinget adgang til Microsoft Managed Desktop Microsoft Endpoint Manager. Du kan finde flere oplysninger om disse tjenestekonti under [Standardoperativsystemer](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Vejledning | Du har politikker for betinget adgang, der kan forhindre Microsoft Managed Desktop i at administrere Microsoft Managed Desktop-tjenesten. <br><br> Under tilmelding udelader vi Microsoft Managed Desktop-tjenestekonti fra relevante politikker for betinget adgang og anvender nye politikker for betinget adgang for at begrænse adgangen til disse konti. <br><br> Du kan finde flere oplysninger om disse tjenestekonti under [Standardoperativsystemer](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Error | Intune-administratorrollen har ikke tilstrækkelige tilladelser til denne kontrol. Du skal også have tildelt disse Azure AD-roller for at køre denne kontrol: <ul><li>Sikkerhedslæser</li><li>Sikkerhedsadministrator</li><li>Administrator for betinget adgang</li><li>Global læser</li><li>Enheders administrator</li></ul>
### <a name="device-compliance-policies"></a>Politikker for enhedsoverholdelse

Politikker for overholdelse af intune-enheder i din Azure AD-organisation kan påvirke Microsoft-administrerede stationære computere.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Du har mindst én politik for overholdelse af regler og standarder, der gælder for alle brugere. Microsoft Managed Desktop indeholder også politikker for overholdelse, der gælder for dine Microsoft-administrerede stationære computere. Gennemse alle de politikker for overholdelse, der er oprettet af din organisation, som gælder for Microsoft-administrerede stationære computere for at sikre, at der ikke er nogen konflikter. <br><br> Få mere at vide under [Opret en politik for overholdelse af regler og Microsoft Intune](/mem/intune/protect/create-compliance-policy). |

### <a name="device-configuration-profiles"></a>Enhedskonfigurationsprofiler

Intune-enhedskonfigurationsprofiler i din Azure AD-organisation kan ikke målrette nogen Microsoft Manage Desktop-enheder eller -brugere.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har mindst én konfigurationsprofil, der gælder for alle brugere, alle enheder eller begge dele. Nulstil profilen, så den gælder for en bestemt Azure AD-gruppe, der ikke omfatter nogen Microsoft-administrerede skrivebordsenheder. <br><br> Få mere at vide under [Opret en profil med brugerdefinerede indstillinger i Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |
| Vejledning | Sørg for, at alle konfigurationspolitikker, du har, ikke omfatter nogen Microsoft-administrerede stationære computere eller brugere. <br><br> Få mere at vide under [Opret en profil med brugerdefinerede indstillinger i Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |

### <a name="device-type-restrictions"></a>Begrænsninger for enhedstype

Microsoft-administrerede skrivebordsenheder skal have tilladelse til at tilmelde sig Intune.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har i øjeblikket mindst én politik for registreringsbegrænsning konfigureret til at forhindre Windows enheder i at tilmelde sig i Intune. <br><br> Følg trinnene [i Angiv](/mem/intune/enrollment/enrollment-restrictions-set) registreringsbegrænsninger for hver registreringsbegrænsningspolitik, der er målrettet brugere af Microsoft-administrerede computere, og rediger **indstillingen Windows (MDM)** til **Tillad**. Du kan dog indstille alle personligt **ejet Windows** **(MDM)-enheder** til at **blokere**. |

### <a name="enrollment-status-page"></a>Statusside for registrering

Du har i øjeblikket aktiveret Statussiden for tilmelding. Hvis du vil deltage i den offentlige forhåndsvisning af denne funktion fra Microsoft Managed Desktop, kan du ignorere dette element. Få mere at vide under [Første kørselsoplevelse med Autopilot og Statussiden For tilmelding](../get-started/esp-first-run.md).

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har ESP-standardprofilen angivet til **Vis status for app- og profilkonfiguration**. <br><br> Deaktiver denne indstilling, eller sørg for, at tildelinger til en Azure AD-gruppe ikke omfatter Microsoft Managed Desktop-enheder ved at følge trinnene i Konfigurer [statussiden for tilmelding](/mem/intune/enrollment/windows-enrollment-status). |
| Vejledning | Sørg for, at alle profiler, der har statusindstillingen Vis **app** og profilkonfiguration, ikke tildeles til nogen Azure AD-gruppe, der omfatter Microsoft Managed Desktop-enheder. <br><br> Du kan finde flere [oplysninger under Konfigurere statussiden for tilmelding](/mem/intune/enrollment/windows-enrollment-status). |

### <a name="microsoft-store-for-business"></a>Microsoft Store til Virksomheder

Vi bruger Microsoft Store til Virksomheder og installerer Firmaportal-appen på Microsoft Managed Desktop. Denne metode giver brugerne mulighed for eventuelt at installere visse apps, f.eks. Microsoft Project og Microsoft Visio (hvis det er tilladt).

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Microsoft Store til Virksomheder enten ikke er aktiveret eller ikke er synkroniseret med Intune. <br><br> Du kan finde flere oplysninger under Sådan administreres volumenkøbte [apps fra Microsoft Store til Virksomheder med Microsoft Intune](/mem/intune/apps/windows-store-for-business) og [Intune-firmaportal på enheder](../get-started/company-portal.md). |

### <a name="multi-factor-authentication"></a>Multifaktorgodkendelse

Multifaktorgodkendelse kan ikke forhindre Microsoft Managed Desktop i at administrere din Azure AD-organisation (lejer) i Intune og Azure AD.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har angivet nogle politikker for multifaktorgodkendelse, som **er påkrævet** for politikker for betinget adgang, der tildeles til alle brugere. <br><br> Under tilmelding udelader vi Microsoft Managed Desktop-tjenestekonti fra relevante politikker for betinget adgang og anvender nye politikker for betinget adgang for at begrænse adgangen til disse konti. <br><br> Du kan finde flere oplysninger om disse tjenestekonti under [Standardoperativsystemer](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Vejledning | Du har multifaktorgodkendelse påkrævet på betingede adgangspolitikker, der kan forhindre Microsoft Managed Desktop i at administrere Microsoft Managed Desktop-tjenesten. <br><br> Under tilmeldingen kan du udelade Microsoft Managed Desktop-tjenestekonti fra relevante politikker for betinget adgang og anvende nye politikker for betinget adgang for at begrænse adgangen til disse konti. Du kan finde flere oplysninger om disse tjenestekonti under [Standardoperativsystemer](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Error | Intune-administratorrollen har ikke tilstrækkelige tilladelser til denne kontrol. Du skal også have tildelt disse Azure AD-roller for at køre denne kontrol: <ul><li>Sikkerhedslæser</li><li>Sikkerhedsadministrator</li><li>Administrator for betinget adgang</li><li>Global læser</li><li>Enheders administrator</li></ul>

### <a name="powershell-scripts"></a>PowerShell-scripts

Windows PowerShell scripts kan ikke tildeles på en måde, der målrettes mod Microsoft-administrerede desktopenheder.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Sørg for, Windows PowerShell scripts i Azure AD-organisationen ikke målrettes nogen Microsoft Administrer stationære enheder eller brugere. Tildel ikke et PowerShell-script til at målrette mod alle brugere, alle enheder eller begge dele. Skift politikken til at bruge en opgave, der er målrettet en bestemt Azure AD-gruppe, som ikke omfatter nogen Microsoft-administreret skrivebordsenheder eller brugere. <br><br> Få mere at vide under [Brug PowerShell-scripts på Windows 10 enheder i Intune](/mem/intune/apps/intune-management-extension). |

### <a name="region"></a>Område

Dit område skal være understøttet af Microsoft Managed Desktop.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Dit Azure AD-organisationsområde understøttes i øjeblikket ikke af Microsoft Managed Desktop. <br><br> Få mere at vide under [Understøttede områder og sprog for Microsoft Managed Desktop](../service-description/regions-languages.md). |
| Vejledning | Et eller flere af de lande, hvor din Azure AD-organisation er placeret, understøttes ikke af Microsoft Managed Desktop. <br><br> Få mere at vide under [Understøttede områder og sprog for Microsoft Managed Desktop](../service-description/regions-languages.md). |

### <a name="security-baselines"></a>Grundlinjer for sikkerhed

Politikker for grundlinjer for sikkerhed bør ikke målrettes på nogen Microsoft-administreret skrivebord-enhed.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har en grundlinjeprofil for sikkerhed, der er målrettet alle brugere, alle enheder eller begge dele. Rediger politikken til at bruge en opgave, der er målrettet en bestemt Azure AD-gruppe, som ikke omfatter nogen Microsoft-administrerede skrivebordsenheder. <br><br> Få mere at vide under [Brug sikkerheds oprindelige planer til at konfigurere Windows 10 enheder i Intune](/mem/intune/protect/security-baselines). Under tilmeldingen anvender vi en ny sikkerheds baseline på alle Microsoft Managed Desktop-enheder. Efter tilmeldingen kan du gennemse microsoft Managed Desktop security baseline policy i politikområdet Konfiguration i  Microsoft Endpoint Manager. |
| Vejledning | Sørg for, at alle politikker for grundlinjer for sikkerhed, som du har udelader Microsoft-administrerede skrivebordsenheder. Få mere at vide under [Brug sikkerheds oprindelige planer til at konfigurere Windows 10 enheder i Intune](/mem/intune/protect/security-baselines). <br><br> Under tilmeldingen anvender vi en ny sikkerheds baseline på alle Microsoft Managed Desktop-enheder. Enheder **på den moderne arbejdsplads – Alle** Azure AD-grupper er en dynamisk gruppe, som vi opretter, når du tilmelder dig Microsoft Managed Desktop. Du er nødt til at vende tilbage for at udelukke denne gruppe efter tilmeldingen. |

### <a name="unlicensed-admins"></a>Administratorer uden licens

Denne indstilling skal være aktiveret for at undgå fejlen "manglende tilladelser", når vi interagerer med din Azure AD-organisation.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | **Tillad adgang til administratorer uden licens skal** være aktiveret. Du kan finde flere oplysninger [under Forudsætninger for gæstekonti](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="windows-apps"></a>Windows apps

Gennemgå de apps, som dine Microsoft-administrerede brugere af stationære computere skal have.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Du skal forberede en oversigt over de apps, som dine Microsoft-administrerede brugere af stationære computere skal have. Da disse apps skal installeres af Intune, skal du evaluere genbrug af eksisterende Intune-apps. Overvej at Firmaportal (se [Installér Intune-firmaportal](../get-started/company-portal.md) på enheder og Statusside for registrering ) til at distribuere apps til dine brugere. <br><br> Få mere at vide under [Apps i Microsoft Managed Desktop](apps.md) og [Første kørsel med Autopilot og Statussiden For tilmelding](../get-started/esp-first-run.md). <br><br> Du kan bede din Microsoft-kontorepræsentant om en forespørgsel i Microsoft Endpoint Configuration Manager at identificere de apps, der er klar til at blive overført til Intune, eller som skal justeres. |

### <a name="windows-hello-for-business"></a>Windows Hello for Business

Microsoft Managed Desktop kræver, Windows Hello for Business er aktiveret.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Windows Hello for Business er enten deaktiveret eller ikke konfigureret. Aktivér det ved at følge trinnene [i Oprette Windows Hello for Business-politik](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy). |

### <a name="windows-10-update-rings"></a>Windows 10 opdateringsringe

Politikken "Windows 10 opdateringsring" i Intune må ikke målrettes mod nogen Microsoft-administreret skrivebordsenheder.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har en politik for "opdateringsring", der er målrettet alle enheder, alle brugere eller begge dele. Skift politikken til at bruge en opgave, der er målrettet en bestemt Azure AD-gruppe, som ikke omfatter nogen Microsoft-administrerede skrivebordsenheder. <br><br> Få mere at vide under [Administrer Windows 10 softwareopdateringer i Intune](/mem/intune/protect/windows-update-for-business-configure). |
| Vejledning | Sørg for, at alle politikker for opdateringsring, som du har, **udelader enheder med den moderne arbejdsplads – alle** Azure AD-grupper. Hvis du har tildelt Azure AD-brugergrupper til disse politikker, skal du sørge for, at alle politikker for opdateringsring, som du også har udelukket den moderne arbejdsplads **–** alle Azure AD-grupper, som du føjer dine Microsoft-administrerede brugere til (eller en tilsvarende gruppe). <br><br> Få mere at vide under [Administrer Windows 10 softwareopdateringer i Intune](/mem/intune/protect/windows-update-for-business-configure). Både enheder **til den moderne arbejdsplads – alle** og den moderne arbejdsplads **–** Alle Azure AD-grupper er grupper, som vi opretter, når du tilmelder dig Microsoft Managed Desktop. Du er nødt til at vende tilbage for at udelukke denne gruppe efter tilmeldingen. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory indstillinger

Du kan få Azure Active Directory indstillingerne i [Azure-portalen](https://portal.azure.com).

### <a name="intune-enrollment"></a>Tilmelding i Intune

Windows 10 enheder i din Azure AD-organisation skal kunne tilmeldes Intune automatisk.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Sørg for, at **MDM-brugerområdet** er angivet **til Nogle** eller **Alle**, ikke **Ingen**. <br><br> Hvis **du vælger Nogle**, skal du vende tilbage efter tilmeldingen og vælge gruppen Moderne arbejdsplads **–** alle Azure **AD for grupper** eller en tilsvarende gruppe, der er målrettet alle dine Brugere af Microsoft-administreret skrivebord. <br><br> Du kan finde flere [oplysninger i Konfigurere registrering for Windows ved hjælp af Microsoft Intune](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment). |

### <a name="ad-hoc-subscriptions"></a>Ad hoc-abonnementer

Anbefaler, hvordan du kontrollerer en indstilling, der, hvis den er indstillet til "falsk", kan forhindre Enterprise State Roaming i at fungere korrekt.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Sørg for **, at AllowAdHocSubscriptions** er angivet til **Sand**. Ellers fungerer Enterprise State Roaming muligvis ikke. <br><br> Du kan finde flere oplysninger [under Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings). |

### <a name="enterprise-state-roaming"></a>Enterprise State Roaming

Enterprise State Roaming skal være aktiveret.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Sørg for, at Enterprise State Roaming er aktiveret for **Alle** eller for **Valgte** grupper. <br><br> Du kan finde flere oplysninger [i Aktivere Enterprise State Roaming i Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable). |

### <a name="guest-invitation-settings"></a>Indstillinger for gæsteinvitationer

Microsoft Managed Desktop anbefaler at justere indstillingerne for gæsteinvitationer, da standardindstillingen tillader alle brugere og gæster i biblioteket at invitere gæster.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | **Medlemsbrugere og brugere, der er tildelt bestemte administratorroller, kan invitere gæster, herunder gæster med medlemstilladelser** , bør være aktiveret. <br><br> Du kan finde flere oplysninger [under Forudsætninger for gæstekonti](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="guest-user-access"></a>Gæstebrugeradgang

Microsoft Managed Desktop anbefaler at justere gæsteadgang, da standardindstillingen tillader alle gæster i biblioteket at få samme adgang som medlemmer.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | **Gæstebrugere har begrænset adgang til egenskaber, og medlemskaber af katalogobjekter bør** være aktiveret. <br><br> Du kan finde flere oplysninger [under Forudsætninger for gæstekonti](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="licenses"></a>Licenser

Der kræves mange licenser for at bruge Microsoft Managed Desktop.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har ikke alle de licenser, du skal bruge for at kunne bruge Microsoft Managed Desktop. <br><br> Du kan finde flere oplysninger i [Microsoft Managed Desktop-teknologier](../intro/technologies.md) [og Mere om licenser](prerequisites.md#more-about-licenses). |

### <a name="microsoft-managed-desktop-service-accounts"></a>Microsoft Managed Desktop-tjenestekonti

Visse kontonavne kan konflikte med kontonavne, der er oprettet af Microsoft Managed Desktop, for at administrere tjenesten Microsoft Managed Desktop.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Du har mindst ét kontonavn, der er i konflikt med kontonavne, der er oprettet af Microsoft Managed Desktop. Arbejd sammen med din Microsoft-kontorepræsentant om at udelade disse kontonavne. Vi oplister ikke kontonavnene offentligt for at minimere sikkerhedsrisikoen.

### <a name="security-administrator-roles"></a>Sikkerhedsadministratorroller

Brugere med visse sikkerhedsroller skal have tildelt disse roller i Microsoft Defender til slutpunkt.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Hvis du har brugere, der er tildelt en af disse roller i Din Azure AD-organisation, skal du sikre dig, at de også har fået tildelt disse roller i Microsoft Defender til slutpunkt. Ellers kan administratorer med disse roller ikke få adgang til administrationsportalen. <ul><li>Sikkerhedsoperator</li><li>Global læser</li></ul> <br> Få mere at vide under [Opret og administrer roller for rollebaseret adgangskontrol](/windows/security/threat-protection/microsoft-defender-atp/user-roles).

### <a name="security-default"></a>Sikkerhedsstandard

Sikkerhedsstandardindstillinger i Azure Active Directory forhindrer Microsoft Managed Desktop i at administrere dine enheder.

| Resultat  | Betydning |
| ----- | ----- |
| Ikke klar | Sikkerhedsstandard er slået til. Deaktivere standardindstillinger for sikkerhed og konfigurere politikker for betinget adgang. <br><br> Få mere at vide under [Almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common). |

### <a name="self-service-password-reset"></a>Nulstilling af adgangskode via selvbetjening

Selvbetjening for nulstilling af adgangskode (SSPR) kan aktiveres for alle brugere af Microsoft Managed Desktop, undtagen konti til Microsoft Managed Desktop-tjenester. <br><br> Du kan finde flere oplysninger i Selvstudium: Give brugerne mulighed for at låse deres konto op eller nulstille adgangskoder Azure Active Directory at nulstille [adgangskode via selvbetjeningstjenesten](/azure/active-directory/authentication/tutorial-enable-sspr).

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Sørg for, at den **SSPR-valgte** indstilling omfatter brugere af Microsoft Managed Desktop, men ikke konti til Microsoft Managed Desktop-tjenesten. Microsoft Managed Desktop-tjenestekonti kan ikke fungere som forventet, når SSPR er aktiveret. |

### <a name="standard-user-role"></a>Standardbrugerrolle

Ud over de brugere, der er tildelt global administrator og enhedsadministrator Azure Active Directory administratorroller, vil Microsoft Managed Desktop-brugere være almindelige brugere uden lokale administratorrettigheder. Alle andre brugere får tildelt en standardbrugerrolle, når de starter deres Microsoft-administrerede skrivebordsenhed.

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Brugere af Microsoft-administrerede computere har ikke lokale administratorrettigheder på deres Microsoft-administrerede stationære computere efter tilmeldingen. |

## <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

### <a name="onedrive"></a>OneDrive

Indstillingen **Tillad synkronisering kun på pc'er, der er forbundet til bestemte** domæner vil være i konflikt med Microsoft Managed Desktop. Du kan OneDrive adgang til OneDrive [Administration](https://admin.onedrive.com).

| Resultat  | Betydning |
| ----- | ----- |
| Vejledning | Du bruger indstillingen Tillad kun **synkronisering på pc'er, der er forbundet med bestemte domæner** . Denne indstilling virker ikke med Microsoft Managed Desktop. Deaktiver denne indstilling. I stedet skal du konfigurere OneDrive at bruge en politik for betinget adgang. <br><br> Du kan få mere at vide [under Planlægge en installation med Betinget adgang](/azure/active-directory/conditional-access/plan-conditional-access) for at få hjælp. |
