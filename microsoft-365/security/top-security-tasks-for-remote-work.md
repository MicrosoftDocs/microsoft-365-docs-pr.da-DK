---
title: Top 12-opgaver til sikkerhedsteams, der understøtter at arbejde hjemmefra
f1.keywords:
- CSH
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- remotework
ms.custom: admindeeplinkDEFENDER
description: Beskyt din virksomheds mail og dine data mod cybertrusler, herunder ransomware, phishing og ondsindede vedhæftede filer.
ms.openlocfilehash: bc1dd84e83e5c5f1828e65203585d38acc28de5e
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617254"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>Top 12-opgaver til sikkerhedsteams, der understøtter at arbejde hjemmefra

Hvis du er som [Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) og pludselig finder dig selv i at støtte en primært hjemmebaseret arbejdsstyrke, vil vi gerne hjælpe dig med at sikre, at din organisation arbejder så sikkert som muligt. I denne artikel prioriteres opgaver for at hjælpe sikkerhedsteams med at implementere de vigtigste sikkerhedsfunktioner så hurtigt som muligt.

:::image type="content" source="../media/security/security-support-remote-work.png" alt-text="De vigtigste opgaver, der skal udføres for at understøtte at arbejde hjemmefra" lightbox="../media/security/security-support-remote-work.png":::


Hvis du er en lille eller mellemstor organisation, der bruger en af Microsofts forretningsplaner, kan du i stedet se disse ressourcer:

- [Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 til kampagner](../business-premium/index.md) (indeholder en anbefalet sikkerhedskonfiguration til Microsoft 365 Business)

For kunder, der bruger vores virksomhedsplaner, anbefaler Microsoft, at du udfører de opgaver, der er angivet i følgende tabel, som gælder for din serviceplan. Hvis du i stedet for at købe en Microsoft 365 Enterprise-plan kombinerer abonnementer, skal du bemærke følgende:

- Microsoft 365 E3 omfatter Enterprise Mobility + Security (EMS) E3 og Azure AD P1
- Microsoft 365 E5 omfatter EMS E5 og Azure AD P2

****

|Trin|Opgave|Alle Office 365 Enterprise planer|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Aktivér MFA (Multi-Factor Authentication) for Azure AD](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Beskyt mod trusler](#2-protect-against-threats)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Konfigurer Microsoft Defender for Office 365](#3-configure-microsoft-defender-for-office-365)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Konfigurer Microsoft Defender for Identity](#4-configure-microsoft-defender-for-identity)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[Slå Microsoft 365 Defender til](#5-turn-on-microsoft-365-defender)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Konfigurer Intune beskyttelse af mobilapps til telefoner og tablets](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[Konfigurer MFA og betinget adgang for gæster, herunder Intune appbeskyttelse](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[Tilmeld pc'er til enhedshåndtering, og kræv kompatible pc'er](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[Optimer dit netværk til cloudforbindelse](#9-optimize-your-network-for-cloud-connectivity)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Oplær brugere](#10-train-users)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Kom i gang med Microsoft Defender for Cloudapps](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[Overvåg for trusler, og udfør handlinger](#12-monitor-for-threats-and-take-action)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|

Før du begynder, skal du kontrollere din [Microsoft 365 Secure Score](./defender/microsoft-secure-score.md) på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. Fra et centraliseret dashboard kan du overvåge og forbedre sikkerheden for dine Microsoft 365-identiteter, data, apps, enheder og infrastruktur. Du får point for konfiguration af anbefalede sikkerhedsfunktioner, udførelse af sikkerhedsrelaterede opgaver (f.eks. visning af rapporter) eller løsning af anbefalinger med et tredjepartsprogram eller -software. De anbefalede opgaver i denne artikel øger din score.

:::image type="content" source="../media/secure-score.png" alt-text="Skærmen Microsoft Secure Score på Microsoft 365 Defender-portalen" lightbox="../media/secure-score.png":::

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: Aktivér Azure AD multifaktorgodkendelse (MFA)

Det bedste, du kan gøre for at forbedre sikkerheden for medarbejdere, der arbejder hjemmefra, er at aktivere MFA. Hvis du ikke allerede har processer på plads, skal du behandle dette som en nødpilot og sørge for, at du har support folk klar til at hjælpe medarbejdere, der sidder fast. Da du sandsynligvis ikke kan distribuere hardwaresikkerhedsenheder, skal du bruge Windows Hello biometriske data og apps til smartphonegodkendelse, f.eks. Microsoft Authenticator.

Normalt anbefaler Microsoft, at du giver brugerne 14 dage til at registrere deres enhed til multifaktorgodkendelse, før de kræver MFA. Men hvis din arbejdsstyrke pludselig arbejder hjemmefra, skal du gå videre og kræve MFA som en sikkerhedsprioritet og være forberedt på at hjælpe brugere, der har brug for det.

Det tager kun nogle få minutter at anvende disse politikker, men vær forberedt på at understøtte dine brugere i løbet af de næste par dage.

****

|Plan|Anbefaling|
|---|---|
|Microsoft 365-planer (uden Azure AD P1 eller P2)|[Aktivér sikkerhedsstandarder i Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Sikkerhedsstandarder i Azure AD omfatter MFA for brugere og administratorer.|
|Microsoft 365 E3 (med Azure AD P1)|Brug [almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker: <br/>- [Kræv MFA for administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (med Azure AD P2)|Ved at udnytte Azure AD identitetsbeskyttelse kan du begynde at implementere Microsofts [anbefalede sæt betinget adgang og relaterede politikker](./office-365-security/identity-access-policies.md) ved at oprette disse politikker:<br/> - [Kræv MFA, når logonrisikoen er mellem eller høj](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Bloker klienter, der ikke understøtter moderne godkendelse](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Brugere med høj risiko skal ændre adgangskode](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|

## <a name="2-protect-against-threats"></a>2: Beskyt mod trusler

Alle Microsoft 365-planer indeholder en række funktioner til trusselsbeskyttelse. Det tager kun et par minutter, før beskyttelsen af disse funktioner støder op.

- Beskyttelse mod malware
- Beskyttelse mod skadelige URL-adresser og filer
- Beskyttelse mod phishing
- Beskyttelse mod spam

Se [Beskyt mod trusler i Office 365](office-365-security/protect-against-threats.md) for at få vejledning, du kan bruge som udgangspunkt.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: Konfigurer Microsoft Defender for Office 365

Microsoft Defender for Office 365, der følger med Microsoft 365 E5 og Office 365 E5, beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Det kan tage flere timer at konfigurere.

Microsoft Defender for Office 365:

- Beskytter din organisation mod ukendte mailtrusler i realtid ved hjælp af intelligente systemer, der undersøger vedhæftede filer og links for skadeligt indhold. Disse automatiserede systemer omfatter en robust detonationsplatform, heuristik og modeller til maskinel indlæring.
- Beskytter din organisation, når brugerne samarbejder og deler filer, ved at identificere og blokere skadelige filer på teamwebsteder og i dokumentbiblioteker.
- Anvender modeller til maskinel indlæring og avancerede algoritmer til registrering af repræsentation på afværge phishing-angreb.

Du kan få en oversigt, herunder en oversigt over planer, [under Defender for Office 365](./office-365-security/defender-for-office-365.md).

Den globale administrator kan konfigurere disse beskyttelser:

- [Konfigurer politikker for sikre links](office-365-security/set-up-safe-links-policies.md)
- [Konfigurer globale indstillinger for Sikre links](office-365-security/configure-global-settings-for-safe-links.md)
- [Konfigurer politikker for vedhæftede filer, der er tillid til](office-365-security/set-up-safe-attachments-policies.md)

Du skal samarbejde med Exchange Online-administratoren og SharePoint Online-administratoren om at konfigurere Defender for Office 365 for disse arbejdsbelastninger:

- [Microsoft Defender for Endpoint til SharePoint, OneDrive og Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: Konfigurer Microsoft Defender for Identity

[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) er en cloudbaseret sikkerhedsløsning, der udnytter dine Active Directory i det lokale miljø signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation. Fokuser derefter på dette, da det beskytter dit lokale miljø og din cloudinfrastruktur, ikke har nogen afhængigheder eller forudsætninger og kan give øjeblikkelige fordele.

- Se [Microsoft Defender for Identity Hurtig start](/azure-advanced-threat-protection/install-atp-step1) for at få hurtig konfiguration
- Se [video: Introduktion til Microsoft Defender for Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- Gennemse de [tre faser i Microsoft Defender for Identity udrulningen](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5: Slå Microsoft 365 Defender til

Nu, hvor du har konfigureret Microsoft Defender for Office 365 og Microsoft Defender for Identity, kan du få vist de kombinerede signaler fra disse funktioner i ét dashboard. [Microsoft 365 Defender](./defender/microsoft-365-defender.md) samler beskeder, hændelser, automatiseret undersøgelse og svar og avanceret jagt på tværs af arbejdsbelastninger (Microsoft Defender for Identity, Defender for Office 365, Microsoft Defender for Endpoint og Microsoft Defender for Cloud Apps) til en enkelt rude på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalen Microsoft 365 Defender</a>.

:::image type="content" source="../media/top-ten-security-remote-work-mtp-dashboard.png" alt-text="Det Microsoft 365 Defender dashboard" lightbox="../media/top-ten-security-remote-work-mtp-dashboard.png":::

Når du har konfigureret en eller flere af dine Defender for Office 365 tjenester, skal du aktivere MTP. Nye funktioner føjes løbende til MTP. overveje at tilvalge for at modtage prøveversionsfunktioner.

- [Få mere at vide om MTP](./defender/microsoft-365-defender.md)
- [Slå MTP til](./defender/m365d-enable.md)
- [Tilmeld dig prøveversionsfunktioner](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: Konfigurer beskyttelse af Intune mobilapps til telefoner og tablets

Microsoft Intune MAM (Mobile Application Management) giver dig mulighed for at administrere og beskytte organisationens data på telefoner og tablets uden at administrere disse enheder. Sådan fungerer det:

- Du opretter en App Protection Policy (APP), der bestemmer, hvilke apps på en enhed der administreres, og hvilke funktionsmåder der er tilladt (f.eks. forhindre, at data fra en administreret app kopieres til en ikke-administreret app). Du opretter én politik for hver platform (iOS, Android).
- Når du har oprettet politikker for appbeskyttelse, gennemtvinger du disse ved at oprette en regel for betinget adgang i Azure AD for at kræve godkendte apps og beskyttelse af appdata.

Politikker for appbeskyttelse omfatter mange indstillinger. Heldigvis behøver du ikke at lære om alle indstillinger og veje mulighederne. Microsoft gør det nemt at anvende en konfiguration af indstillinger ved at anbefale startpunkter. [Databeskyttelsesstrukturen, der bruger politikker for appbeskyttelse](/mem/intune/apps/app-protection-framework), indeholder tre niveauer, du kan vælge imellem.

Endnu bedre koordinerer Microsoft denne appbeskyttelsesramme med et sæt betinget adgang og relaterede politikker, som vi anbefaler, at alle organisationer bruger som udgangspunkt. Hvis du har implementeret MFA ved hjælp af vejledningen i denne artikel, er du halvvejs der!

Hvis du vil konfigurere beskyttelse af mobilapps, skal du bruge vejledningen i [Almindelige politikker for identitets- og enhedsadgang](./office-365-security/identity-access-policies.md):

 1. Brug vejledningen [Anvend politikker for databeskyttelse for app](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) til at oprette politikker til iOS og Android. Niveau 2 (forbedret databeskyttelse) anbefales til grundlæggende beskyttelse.
 2. Opret en regel for betinget adgang for at [kræve godkendt appbeskyttelse og appbeskyttelse](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: Konfigurer MFA og betinget adgang for gæster, herunder beskyttelse af Intune mobilapps

Lad os nu sikre, at du kan fortsætte med at samarbejde og arbejde med gæster. Hvis du bruger Microsoft 365 E3-planen, og du har implementeret MFA for alle brugere, er du indstillet.

Hvis du bruger Microsoft 365 E5-planen, og du udnytter Azure Identity Protection til risikobaseret MFA, skal du foretage et par justeringer (fordi Azure AD identitetsbeskyttelse ikke omfatter gæster):

- Opret en ny regel for betinget adgang for altid at kræve MFA for gæster og eksterne brugere.
- Opdater den risikobaserede MFA-regel for betinget adgang for at udelukke gæster og eksterne brugere.

Brug vejledningen i [Opdatering af de fælles politikker for at tillade og beskytte gæsteadgang og ekstern adgang](./office-365-security/identity-access-policies-guest-access.md) for at forstå, hvordan gæsteadgang fungerer sammen med Azure AD og for at opdatere de berørte politikker.

De Intune politikker for beskyttelse af mobilapps, du har oprettet, samt reglen for betinget adgang, der kræver godkendte apps og appbeskyttelse, gælder for gæstekonti og hjælper med at beskytte dine organisationsdata.

> [!NOTE]
> Hvis du allerede har tilmeldt pc'er til enhedsadministration for at kræve kompatible pc'er, skal du også udelade gæstekonti fra reglen for betinget adgang, der gennemtvinger enhedsoverholdelse.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: Tilmeld pc'er til enhedshåndtering og kræv kompatible pc'er

Der er flere metoder til at tilmelde din arbejdsstyrkes enheder. Hver metode afhænger af enhedens ejerskab (personlig eller firma), enhedstype (iOS, Windows, Android) og administrationskrav (nulstilling, tilhørsforhold, låsning). Det kan tage lidt tid at sortere ud. Se: [Tilmeld enheder i Microsoft Intune](/mem/intune/enrollment/).

Den hurtigste måde at komme i gang på er at [konfigurere automatisk tilmelding til Windows 10 enheder](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Du kan også drage fordel af disse selvstudier:

- [Brug Autopilot til at tilmelde Windows-enheder i Intune](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [Brug Apples funktioner til tilmelding af virksomhedsenheder i Apple Business Manager (ABM) til at tilmelde iOS-/iPadOS-enheder i Intune](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Når du har tilmeldt enheder, kan du bruge vejledningen i [Almindelige politikker for identitets- og enhedsadgang](./office-365-security/identity-access-policies.md) til at oprette disse politikker:

- [Definer politikker for enhedsoverholdelse](./office-365-security/identity-access-policies.md#define-device-compliance-policies) – De anbefalede indstillinger for Windows 10 omfatter krav om antivirusbeskyttelse. Hvis du har Microsoft 365 E5, kan du bruge Microsoft Defender for Endpoint til at overvåge medarbejdernes enheders tilstand. Sørg for, at overholdelsespolitikker for andre operativsystemer omfatter antivirusbeskyttelse og slutpunktbeskyttelsessoftware.
- [Kræv kompatible pc'er](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) – dette er reglen for betinget adgang i Azure AD, der gennemtvinger politikkerne for enhedsoverholdelse.

Kun én organisation kan administrere en enhed, så sørg for at udelade gæstekonti fra reglen for betinget adgang i Azure AD. Hvis du ikke udelukker gæstebrugere og eksterne brugere fra politikker, der kræver enhedsoverholdelse, blokerer disse politikker disse brugere. Du kan få flere oplysninger under [Opdatering af de fælles politikker for at tillade og beskytte gæsteadgang og ekstern adgang](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: Optimer dit netværk til cloudforbindelse

Hvis du hurtigt gør det muligt for størstedelen af dine medarbejdere at arbejde hjemmefra, kan denne pludselige skift af forbindelsesmønstre have en betydelig indvirkning på virksomhedens netværksinfrastruktur. Mange netværk blev skaleret og designet, før cloudtjenesterne blev indført. I mange tilfælde er netværk tolerante over for fjernarbejdere, men de er ikke designet til at blive brugt eksternt af alle brugere samtidig.

Netværkselementer som VPN-koncentratorer, udgående udstyr til centrale netværk (f.eks. proxyer og enheder til forebyggelse af datatab), central internetbåndbredde, backhaul MPLS-kredsløb, NAT-funktionalitet osv. bliver pludselig belastet enormt på grund af belastningen af hele virksomheden, der bruger dem. Slutresultatet er dårlig ydeevne og produktivitet kombineret med en dårlig brugeroplevelse for brugere, der tilpasser sig hjemmefra.

Nogle af de beskyttelser, der traditionelt er blevet leveret ved at dirigere trafik tilbage gennem virksomhedens netværk, leveres af de cloudapps, som brugerne får adgang til. Hvis du har nået dette trin i denne artikel, har du implementeret et sæt avancerede cloudsikkerhedskontroller til Microsoft 365-tjenester og -data. Når disse kontrolelementer er på plads, er du muligvis klar til at dirigere fjernbrugeres trafik direkte til Office 365. Hvis du stadig har brug for et VPN-link for at få adgang til andre programmer, kan du forbedre din ydeevne og brugeroplevelse markant ved at implementere opdelt tunnelføring. Når du når til enighed i din organisation, kan dette opnås inden for en dag af et velkoordnet netværksteam.

Se disse ressourcer på Docs for at få flere oplysninger:

- [Oversigt: Optimer forbindelse for fjernbrugere ved hjælp af opdelt VPN-tunnelføring](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Implementering af VPN-opdelt tunnelføring for Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Seneste blogartikler om dette emne:

- [Sådan optimerer du hurtigt trafik til fjernpersonalet & reducere belastningen på din infrastruktur](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Alternative måder for sikkerhedsteknikere og it-medarbejdere at opnå moderne sikkerhedskontroller på i dagens unikke fjernarbejdsscenarier](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: Oplær brugere

Oplæring af brugere kan spare dine brugere og sikkerhedsteamet meget tid og frustration. Kyndige brugere er mindre tilbøjelige til at åbne vedhæftede filer eller klikke på links i tvivlsomme mails, og de er mere tilbøjelige til at undgå mistænkelige websteder.

Harvard Kennedy School [Cybersecurity Campaign Handbook](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) giver fremragende vejledning i at etablere en stærk kultur af sikkerhedsbevidsthed i din organisation, herunder uddannelse af brugere til at identificere phishing-angreb.

Microsoft 365 indeholder følgende ressourcer, der kan hjælpe med at informere brugerne i din organisation:

****

|Koncept|Ressourcer|
|---|---|
|Microsoft 365|[Læringsforløb, der kan tilpasses](/office365/customlearning/) <p>Disse ressourcer kan hjælpe dig med at sammensætte træning for slutbrugere i din organisation|
|Microsoft 365-sikkerhed|[Læringsmodul: Beskyt din organisation med indbygget, intelligent sikkerhed fra Microsoft 365](/learn/modules/security-with-microsoft-365) <p>I dette modul kan du beskrive, hvordan Microsoft 365-sikkerhedsfunktioner arbejder sammen, og hvordan du kan formulere fordelene ved disse sikkerhedsfunktioner.|
|Multifaktorgodkendelse|[Totrinsbekræftelse: Hvad er den ekstra bekræftelsesside?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Denne artikel hjælper slutbrugerne med at forstå, hvad multifaktorgodkendelse er, og hvorfor den bruges i din organisation.|

Ud over denne vejledning anbefaler Microsoft, at dine brugere foretager de handlinger, der er beskrevet i denne artikel: [Beskyt din konto og dine enheder mod hackere og malware](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Disse handlinger omfatter:

- Brug af stærke adgangskoder
- Beskyttelse af enheder
- Aktivering af sikkerhedsfunktioner på Windows 10- og Mac-pc'er (til ikke-administrerede enheder)

Microsoft anbefaler også, at brugerne beskytter deres personlige mailkonti ved at gøre de handlinger, der anbefales i følgende artikler:

- [Hjælp med at beskytte din Outlook.com mailkonto](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Beskyt din Gmail-konto med totrinsbekræftelse](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: Kom i gang med Microsoft Defender for Cloud Apps

[Microsoft Defender for Cloud Apps](/cloud-app-security) giver omfattende synlighed, kontrol over datarejser og avancerede analyser til at identificere og bekæmpe cybertrusler på tværs af alle dine cloudtjenester. Når du kommer i gang med Defender for Cloud Apps, aktiveres politikker for registrering af uregelmæssigheder automatisk, men Defender for Cloud Apps har en indledende læringsperiode på syv dage, hvor ikke alle beskeder om registrering af uregelmæssigheder udløses.

Kom i gang med Defender for Cloud Apps nu. Senere kan du konfigurere mere avancerede overvågning og kontrolelementer.

- [Hurtig start: Kom i gang med Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Hent øjeblikkelig adfærdsanalyse og registrering af uregelmæssigheder](/cloud-app-security/anomaly-detection-policy)
- [Få mere at vide om Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [Gennemse nye funktioner og funktioner](/cloud-app-security/release-notes)
- [Se grundlæggende konfigurationsvejledninger](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: Overvåg for trusler, og udfør handlinger

Microsoft 365 indeholder flere måder at overvåge status og udføre relevante handlinger på. Dit bedste udgangspunkt er <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, hvor du kan se din organisations [Microsoft Secure Score](./defender/microsoft-secure-score.md) og eventuelle beskeder eller enheder, der kræver din opmærksomhed.

- [Kom i gang med Microsoft 365 Defender-portalen](./defender/microsoft-365-defender-portal.md)
- [Se sikkerhedsportalerne i Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>Næste trin

Tillykke! Du har hurtigt implementeret nogle af de vigtigste sikkerhedsforanstaltninger, og din organisation er meget mere sikker. Nu er du klar til at gå endnu længere med trusselsbeskyttelsesfunktioner (herunder Microsoft Defender for Endpoint), dataklassificering og beskyttelsesfunktioner samt sikring af administrative konti. Du kan finde et dybere, metodisk sæt sikkerhedsanbefalinger til Microsoft 365 under [Microsoft 365 BDMs (Security for Business Decision Makers).](Microsoft-365-security-for-bdm.md)

Besøg også Microsofts nye Defender for Cloud på [docs.microsoft.com/security](/security).
