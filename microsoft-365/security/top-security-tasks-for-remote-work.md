---
title: De 12 vigtigste opgaver for sikkerhedsteams til at understøtte hjemmearbejde
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
description: Beskyt din virksomheds mail og data mod cybertrusler, herunder ransomware, phishing og skadelige vedhæftede filer.
ms.openlocfilehash: 584da4e192ddbd8ac5b223e0d292a71f0c35c305
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63588617"
---
# <a name="top-12-tasks-for-security-teams-to-support-working-from-home"></a>De 12 vigtigste opgaver for sikkerhedsteams til at understøtte hjemmearbejde

Hvis du er som [Microsoft](https://www.microsoft.com/microsoft-365/blog/2020/03/10/staying-productive-while-working-remotely-with-microsoft-teams/) og pludselig understøtter en primært hjemmebaseret arbejdsstyrke, vil vi gerne hjælpe dig med at sikre, at din organisation arbejder så sikkert som muligt. Denne artikel prioriterer opgaver for at hjælpe sikkerhedsteams med at implementere de vigtigste sikkerhedsfunktioner så hurtigt som muligt.

![Udfør disse vigtigste opgaver for at understøtte hjemmearbejde.](../media/security/security-support-remote-work.png)

Hvis du er en lille eller mellemstor organisation, der bruger en af Microsofts virksomhedsplaner, kan du i stedet se disse ressourcer:

- [De 10 vigtigste måder at sikre, Office 365 og Microsoft 365 planer til virksomheder](../admin/security-and-compliance/secure-your-business-data.md)
- [Microsoft 365 til kampagner](../business-premium/index.md) (indeholder en anbefalet sikkerhedskonfiguration til Microsoft 365 Business)

For kunder, der bruger vores virksomhedsplaner, anbefaler Microsoft, at du udfører de opgaver, der er angivet i følgende tabel, som gælder for din serviceplan. Hvis du, i stedet for Microsoft 365 en virksomhedsplan, kombinerer abonnementer, skal du bemærke følgende:

- Microsoft 365 E3 omfatter Enterprise Mobility + Security (EMS) E3 og Azure AD P1
- Microsoft 365 E5 omfatter EMS E5 og Azure AD P2

****

|Trin|Opgave|Alle Office 365 Enterprise-planer|Microsoft 365 E3|Microsoft 365 E5|
|---|---|---|---|---|
|1|[Aktivér Azure AD MFA (Multi-Factor Authentication)](#1-enable-azure-ad-multi-factor-authentication-mfa)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|2|[Beskyt dig mod trusler](#2-protect-against-threats)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|3|[Konfigurer Microsoft Defender til Office 365](#3-configure-microsoft-defender-for-office-365)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|4|[Konfigurer Microsoft Defender for Identity](#4-configure-microsoft-defender-for-identity)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|5|[Slå Microsoft 365 Defender](#5-turn-on-microsoft-365-defender)|||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|6|[Konfigurere Intune-mobilappbeskyttelse til telefoner og tablets](#6-configure-intune-mobile-app-protection-for-phones-and-tablets)||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|7|[Konfigurer MFA og betinget adgang for gæster, herunder Intune-appbeskyttelse](#7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection)||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|8|[Tilmeld pc'er til enhedsadministration og kræv kompatible pc'er](#8-enroll-pcs-into-device-management-and-require-compliant-pcs)||![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|9|[Optimere dit netværk til skyforbindelse](#9-optimize-your-network-for-cloud-connectivity)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|10|[Oplære brugere](#10-train-users)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|11|[Kom i gang med Microsoft Defender til skyapps](#11-get-started-with-microsoft-defender-for-cloud-apps)|||![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|12|[Hold øje med trusler, og gør noget](#12-monitor-for-threats-and-take-action)|![Inkluderet.](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|![Inkluderet](../media/d238e041-6854-4a78-9141-049224df0795.png)|
|

Før du begynder, skal [du Microsoft 365 sikker score](./defender/microsoft-secure-score.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">på Microsoft 365 Defender portal</a>. Fra et centraliseret dashboard kan du overvåge og forbedre sikkerheden for dine Microsoft 365 identiteter, data, apps, enheder og infrastruktur. Du får point for konfiguration af anbefalede sikkerhedsfunktioner, udførelse af sikkerhedsrelaterede opgaver (f.eks. visning af rapporter) eller adressering til anbefalinger med et program eller software fra en tredjepart. De anbefalede opgaver i denne artikel hæver din score.

![Skærmbillede af Microsoft Secure Score.](../media/secure-score.png)

## <a name="1-enable-azure-ad-multi-factor-authentication-mfa"></a>1: Aktivér Azure AD Multi-Factor Authentication (MFA)

Det bedste, du kan gøre for at forbedre sikkerheden for medarbejdere, der arbejder hjemmefra, er at aktivere MFA. Hvis du ikke allerede har processer på plads, skal du behandle dette som et nødsforsøg og sørge for, at du har supportmedarbejdere klar til at hjælpe medarbejdere, der sidder fast. Da du sandsynligvis ikke kan distribuere hardwaresikkerhedsenheder, kan du bruge Windows Hello biometriske apps og apps til smartphonegodkendelse som Microsoft Authenticator.

Normalt anbefaler Microsoft, at du giver brugerne 14 dage til at registrere deres enhed til multifaktorgodkendelse, før du kræver multifaktorgodkendelse. Men hvis dine medarbejdere pludselig arbejder hjemmefra, kan du kræve MFA som sikkerhedsprioritet og være forberedt på at hjælpe brugere, der har brug for det.

Det kan kun tage et par minutter at anvende disse politikker, men du vil være klar til at understøtte dine brugere i løbet af de næste par dage.

****

|Plan|Anbefaling|
|---|---|
|Microsoft 365 (uden Azure AD P1 eller P2)|[Aktivér standardindstillinger for sikkerhed i Azure AD](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Sikkerhedsstandarden i Azure AD omfatter MFA for brugere og administratorer.|
|Microsoft 365 E3 (med Azure AD P1)|Brug [almindelige politikker for betinget adgang](/azure/active-directory/conditional-access/concept-conditional-access-policy-common) til at konfigurere følgende politikker: <br/>- [Kræv MFA til administratorer](/azure/active-directory/conditional-access/howto-conditional-access-policy-admin-mfa) <br/>- [Kræv MFA for alle brugere](/azure/active-directory/conditional-access/howto-conditional-access-policy-all-users-mfa) <br/> - [Bloker ældre godkendelse](/azure/active-directory/conditional-access/howto-conditional-access-policy-block-legacy)|
|Microsoft 365 E5 (med Azure AD P2)|Udnyt Azure AD Identity Protection, og begynd at implementere Microsofts anbefalede sæt [af betinget adgang og relaterede politikker](./office-365-security/identity-access-policies.md) ved at oprette disse politikker:<br/> - [Kræv MFA, når logonrisici er mellem eller høj](./office-365-security/identity-access-policies.md#require-mfa-based-on-sign-in-risk) <br/>- [Blokere klienter, der ikke understøtter moderne godkendelse](./office-365-security/identity-access-policies.md#block-clients-that-dont-support-multi-factor)<br/>- [Brugere med høj risiko skal ændre adgangskode](./office-365-security/identity-access-policies.md#high-risk-users-must-change-password)|
|

## <a name="2-protect-against-threats"></a>2: Beskyt dig mod trusler

Alle Microsoft 365 omfatter en række funktioner til trusselsbeskyttelse. Det tager kun nogle få minutter at skubbe beskyttelsen for disse funktioner.

- Beskyttelse mod malware
- Beskyttelse mod skadelige URL-adresser og filer
- Beskyttelse mod phishing
- Beskyttelse mod uønsket post

Se [Beskyt mod trusler i Office 365](office-365-security/protect-against-threats.md) for at få en vejledning, du kan bruge som udgangspunkt.

## <a name="3-configure-microsoft-defender-for-office-365"></a>3: Konfigurer Microsoft Defender til Office 365

Microsoft Defender til Office 365, som følger med Microsoft 365 E5 og Office 365 E5, beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Det kan tage flere timer at konfigurere.

Microsoft Defender til Office 365:

- Beskytter din organisation mod ukendte mailtrusler i realtid ved hjælp af intelligente systemer, der undersøger vedhæftede filer og links for skadeligt indhold. Disse automatiserede systemer omfatter en robust detonationsplatform, heuristics og maskinlæringsmodeller.
- Beskytter din organisation, når brugere samarbejder og deler filer, ved at identificere og blokere skadelige filer på teamwebsteder og dokumentbiblioteker.
- Anvender maskinlæringsmodeller og avancerede algoritmer til registrering af efterligninger for at forhindre phishing-angreb.

Du kan få et overblik, herunder en oversigt over planer, [under Defender for Office 365](./office-365-security/defender-for-office-365.md).

Den globale administrator kan konfigurere disse beskyttelser:

- [Konfigurere Pengeskab links](office-365-security/set-up-safe-links-policies.md)
- [Konfigurere globale indstillinger for Pengeskab links](office-365-security/configure-global-settings-for-safe-links.md)
- [Konfigurere politikker Pengeskab vedhæftede filer](office-365-security/set-up-safe-attachments-policies.md)

Du skal arbejde sammen med din Exchange Online administrator og SharePoint Online-administrator for at konfigurere Defender til Office 365 for disse arbejdsbelastninger:

- [Microsoft Defender til slutpunkt for SharePoint, OneDrive og Microsoft Teams](office-365-security/mdo-for-spo-odb-and-teams.md)

## <a name="4-configure-microsoft-defender-for-identity"></a>4: Konfigurer Microsoft Defender for Identity

[Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp) er en skybaseret sikkerhedsløsning, der udnytter dine lokale Active Directory-signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige Insider-handlinger rettet mod din organisation. Fokuser på dette næste, fordi den beskytter din on-prem og din skyinfrastruktur, ikke har afhængigheder eller forudsætninger, og kan give øjeblikkelig fordel.

- Se [Hurtigstarter til Microsoft Defender for Identity for](/azure-advanced-threat-protection/install-atp-step1) at få hurtig konfiguration
- Se [video: Introduktion til Microsoft Defender for Identity](https://www.youtube.com/watch?reload=9&v=EGY2m8yU_KE)
- Gennemgå de [tre faser af Microsoft Defender for Identity-installation](/azure-advanced-threat-protection/what-is-atp#whats-next)

## <a name="5-turn-on-microsoft-365-defender"></a>5: Slå Microsoft 365 Defender

Nu hvor du har konfigureret Microsoft Defender Office 365 Og Microsoft Defender til identitet, kan du se de kombinerede signaler fra disse egenskaber i ét dashboard. [Microsoft 365 Defender](./defender/microsoft-365-defender.md) samler beskeder, hændelser, automatisk undersøgelse og svar og avanceret jagt på tværs af arbejdsbelastninger (Microsoft Defender for Identity, Defender til Office 365, Microsoft Defender til slutpunkt og Microsoft Defender til skyapps) i en enkelt <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">rude i Microsoft 365 Defender .</a>

![MTP-dashboardillustration.](../media/top-ten-security-remote-work-mtp-dashboard.png)

Når du har konfigureret en eller flere af dine Defender til Office 365, skal du aktivere MTP. Nye funktioner føjes kontinuerligt til MTP; overvej at tilmelde dig for at modtage funktioner til eksempelvisning.

- [Få mere at vide om MTP](./defender/microsoft-365-defender.md)
- [Slå MTP til](./defender/m365d-enable.md)
- [Tilmeld dig visningsfunktioner](./defender/preview.md)

## <a name="6-configure-intune-mobile-app-protection-for-phones-and-tablets"></a>6: Konfigurer Beskyttelse af mobilapps i Intune til telefoner og tablets

Microsoft Intune mam (Mobile Application Management) kan du administrere og beskytte din organisations data på telefoner og tablets uden at administrere disse enheder. Sådan fungerer det:

- Du opretter en appbeskyttelsespolitik, der bestemmer, hvilke apps på en enhed der administreres, og hvilke funktionsmåder der er tilladte (f.eks. forhindre data fra en administreret app i at blive kopieret til en ikke-administreret app). Du opretter én politik for hver platform (iOS, Android).
- Når du har oprettet politikker for appbeskyttelse, kan du gennemtvinge disse ved at oprette en regel for betinget adgang i Azure AD, så der kræves godkendt apps og app-databeskyttelse.

Politikker for appbeskyttelse omfatter mange indstillinger. Heldigvis behøver du ikke at få mere at vide om alle indstillinger og vurdere indstillingerne. Microsoft gør det nemt at anvende en konfiguration af indstillinger ved at anbefale startpunkter. Rammen [for databeskyttelse ved hjælp af politikker til beskyttelse af](/mem/intune/apps/app-protection-framework) apps indeholder tre niveauer, du kan vælge mellem.

Endnu bedre koordinerer Microsoft denne ramme for appbeskyttelse med et sæt betinget adgang og relaterede politikker, som vi anbefaler, at alle organisationer bruger som udgangspunkt. Hvis du har implementeret MFA ved hjælp af vejledningen i denne artikel, er du halvvejs!

For at konfigurere beskyttelse af mobilapps skal du bruge vejledningen i [Fælles identitets- og enhedsadgangspolitikker](./office-365-security/identity-access-policies.md):

 1. Brug vejledningen [Anvend politikker til beskyttelse af app-data](./office-365-security/identity-access-policies.md#apply-app-data-protection-policies) til at oprette politikker til iOS og Android. Niveau 2 (udvidet databeskyttelse) anbefales til beskyttelse af grundlinjer.
 2. Opret en regel for betinget adgang til [Kræv godkendt apps og APP-beskyttelse](./office-365-security/identity-access-policies.md#require-approved-apps-and-app-protection).

## <a name="7-configure-mfa-and-conditional-access-for-guests-including-intune-mobile-app-protection"></a>7: Konfigurer MFA og betinget adgang for gæster, herunder beskyttelse af Intune-mobilapp

Lad os derefter sikre, at du kan fortsætte med at samarbejde og arbejde med gæster. Hvis du bruger den nye Microsoft 365 E3, og du har implementeret MFA for alle brugere, er du klar.

Hvis du bruger Microsoft 365 E5-planen, og du udnytter Azure Identity Protection til risikobaseret MFA, skal du foretage et par justeringer (da beskyttelse af Azure AD-identitet ikke udvides til gæster):

- Opret en ny regel for betinget adgang til at kræve MFA altid for gæster og eksterne brugere.
- Opdater den risikobaserede regel for betinget adgang for MFA for at udelukke gæster og eksterne brugere.

Brug vejledningen i Opdatering [af de](./office-365-security/identity-access-policies-guest-access.md) fælles politikker for at tillade og beskytte gæsteadgang og ekstern adgang for at forstå, hvordan gæsteadgang fungerer sammen med Azure AD, og for at opdatere de berørte politikker.

De politikker for beskyttelse af intune-mobilapps, du har oprettet, gælder sammen med reglen for betinget adgang til at kræve godkendt apps og APP-beskyttelse for gæster-konti, og de er med til at beskytte din organisations data.

> [!NOTE]
> Hvis du allerede har tilmeldt pc'er til enhedsstyring for at kræve kompatible pc'er, skal du også udelade gæstekonti fra reglen om betinget adgang, der gennemtvinger enhedsoverholdelse.

## <a name="8-enroll-pcs-into-device-management-and-require-compliant-pcs"></a>8: Tilmeld pc'er til enhedshåndtering og kræv kompatible pc'er

Der er flere forskellige metoder til at tilmelde dine medarbejderes enheder. Hver metode afhænger af enhedens ejerskab (personlig eller virksomhed), enhedstype (iOS, Windows, Android) og administrationskrav (nulstillinger, affinitet, låsning). Det kan tage lidt tid at finde ud af det. Se: [Tilmeld enheder i Microsoft Intune](/mem/intune/enrollment/).

Den hurtigste måde at komme i gang på [er at Konfigurere automatisk registrering for Windows 10 enheder](/mem/intune/enrollment/quickstart-setup-auto-enrollment).

Du kan også drage fordel af disse selvstudier:

- [Brug Autopilot til at tilmelde Windows enheder i Intune](/mem/intune/enrollment/tutorial-use-autopilot-enroll-devices)
- [Brug Apples registreringsfunktioner i Apple Business Manager (ABM) til at tilmelde iOS-/iPadOS-enheder i Intune](/mem/intune/enrollment/tutorial-use-device-enrollment-program-enroll-ios)

Når du har tilmeldt enheder, kan du bruge vejledningen i Almindelige [identitets- og enhedsadgangspolitikker](./office-365-security/identity-access-policies.md) til at oprette disse politikker:

- [Definer politikker for enhedsoverholdelse](./office-365-security/identity-access-policies.md#define-device-compliance-policies) – De anbefalede indstillinger for Windows 10 omfatter krav om antivirusbeskyttelse. Hvis du har Microsoft 365 E5, kan du bruge Microsoft Defender til Slutpunkt til at overvåge medarbejdernes tilstand. Sørg for, at politikker for overholdelse af regler og standarder for andre operativsystemer omfatter antivirusbeskyttelses- og slutpunktsbeskyttelsessoftware.
- [Kræv kompatible pc'er](./office-365-security/identity-access-policies.md#require-compliant-pcs-and-mobile-devices) – Dette er reglen for betinget adgang i Azure AD, der gennemtvinger politikker for enhedsoverholdelse.

Kun én organisation kan administrere en enhed, så sørg for at udelade gæstekonti fra reglen om betinget adgang i Azure AD. Hvis du ikke udelukker gæster og eksterne brugere fra politikker, der kræver overholdelse af enhed, vil disse politikker blokere disse brugere. Få mere at vide under [Opdatering af de fælles politikker for at tillade og beskytte gæsteadgang og ekstern adgang](./office-365-security/identity-access-policies-guest-access.md).

## <a name="9-optimize-your-network-for-cloud-connectivity"></a>9: Optimere dit netværk til skyforbindelse

Hvis du hurtigt aktiverer mange af dine medarbejdere til at arbejde hjemmefra, kan denne pludselige skift af forbindelsesmønstre have stor indflydelse på virksomhedens netværksinfrastruktur. Mange netværk blev skaleret og udviklet, før skytjenester blev indført. I mange tilfælde er netværk over for fjernmedarbejdere, men de er ikke designet til at blive brugt eksternt af alle brugere på samme tid.

Netværkselementer som f.eks. VPN-enheder, central netværk udgangsudstyr (f.eks. proxyer og enheder til forebyggelse af datatab), central internetbåndbredde, BACKhaul MPLS-kredsløb, NAT-funktionalitet osv. belastes pludseligt af den store belastning af hele virksomheden, der bruger dem. Slutresultatet er dårlig ydeevne og produktivitet kombineret med en dårlig brugeroplevelse for brugere, der tilpasser sig til at arbejde hjemmefra.

Nogle af de beskyttelsesprogrammer, der traditionelt er blevet leveret ved at dirigere trafik tilbage gennem et virksomhedsnetværk, leveres af de skyapps, dine brugere har adgang til. Hvis du har nået dette trin i denne artikel, har du implementeret et sæt avancerede sikkerhedskontrolelementer i skyen til Microsoft 365 tjenester og data. Når disse kontrolelementer er på plads, er du muligvis klar til at dirigere fjernbrugeres trafik direkte Office 365. Hvis du stadig kræver et VPN-link for at få adgang til andre programmer, kan du i høj grad forbedre din ydeevne og brugeroplevelse ved at implementere opdelt inddelning. Når du opnår enighed i organisationen, kan dette opnås inden for en dag af et velkoordineret netværksteam.

Se disse ressourcer på Docs for at få flere oplysninger:

- [Oversigt: Optimer forbindelse for eksterne brugere ved hjælp af VPN-opdeling](/Office365/Enterprise/office-365-vpn-split-tunnel)
- [Implementering af VPN-opdeling af Office 365](/Office365/Enterprise/office-365-vpn-implement-split-tunnel)

Seneste blogartikler om dette emne:

- [Sådan optimerer du hurtigt trafik til eksternt & reducere belastningen på din infrastruktur](https://techcommunity.microsoft.com/t5/office-365-blog/how-to-quickly-optimize-office-365-traffic-for-remote-staff-amp/ba-p/1214571#)
- [Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i moderne, unikke scenarier med fjernarbejde](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

## <a name="10-train-users"></a>10: Oplære brugere

Kursusbrugere kan gemme dine brugere og sikkerhedsteamet en masse tid og frustration. Erfarne brugere er mindre tilbøjelige til at åbne vedhæftede filer eller klikke på links i tvivlsomme mails, og de er mere tilbøjelige til at undgå mistænkelige websteder.

The Harvard The School [Cybersecurity Campaign Handbook giver](https://go.microsoft.com/fwlink/?linkid=2015598&amp;clcid=0x409) fremragende vejledning til oprettelse af en stærk kultur for sikkerhedskultur i din organisation, herunder uddannelse af brugere til at identificere phishing-angreb.

Microsoft 365 indeholder følgende ressourcer, som kan hjælpe med at informere brugerne i organisationen:

****

|Koncept|Ressourcer|
|---|---|
|Microsoft 365|[Brugerdefinerbare læringsstier](/office365/customlearning/) <p>Disse ressourcer kan hjælpe dig med at sammensætte kurser til slutbrugere i organisationen|
|Microsoft 365 sikkerhed|[Learning modul: Beskyt din organisation med indbygget, intelligent sikkerhed Microsoft 365](/learn/modules/security-with-microsoft-365) <p>Dette modul gør det muligt for dig at beskrive, Microsoft 365 sikkerhedsfunktioner fungerer sammen, og til at fordele ved disse sikkerhedsfunktioner.|
|Multifaktorgodkendelse|[Totrinsbekræftelse: Hvad er den ekstra bekræftelsesside?](/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time) <p>Denne artikel hjælper slutbrugere med at forstå, hvad multifaktorgodkendelse er, og hvorfor den bruges i din organisation.|
|

Ud over denne vejledning anbefaler Microsoft, at brugerne tager de handlinger, der er beskrevet i denne artikel: [Beskyt din konto og dine enheder mod hackere og malware](https://support.office.com/article/066d6216-a56b-4f90-9af3-b3a1e9a327d6.aspx). Disse handlinger omfatter:

- Brug af stærke adgangskoder
- Beskyttelse af enheder
- Aktivering af sikkerhedsfunktioner på Windows 10 og Mac-pc'er (for enheder, der ikke er administrerede)

Microsoft anbefaler også, at brugerne beskytter deres personlige mailkonti ved at udføre de handlinger, der anbefales i følgende artikler:

- [Hjælp med at beskytte din Outlook.com-mailkonto](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Beskyt din Gmail-konto med totrinsbekræftelse](https://go.microsoft.com/fwlink/p/?linkid=2015688)

## <a name="11-get-started-with-microsoft-defender-for-cloud-apps"></a>11: Kom i gang med Microsoft Defender til skyapps

[Microsoft Defender til skyapps](/cloud-app-security) giver stor synlighed, kontrol over datarejse og avancerede analyser til at identificere og bekæmpe cybertrusler på tværs af alle dine skytjenester. Når du kommer i gang med Defender til skyapps, aktiveres automatisk registreringspolitikker, men Defender til skyapps har en indledende læringsperiode på syv dage, hvor ikke alle beskeder om unormal registrering er hævet.

Kom i gang med Defender til skyapps nu. Senere kan du konfigurere mere avanceret overvågning og kontrolelementer.

- [Hurtig start: Kom i gang med Defender til skyapps](/cloud-app-security/getting-started-with-cloud-app-security)
- [Få øjeblikkelig adfærdsanalyse og registrering af unormalt](/cloud-app-security/anomaly-detection-policy)
- [Få mere at vide om Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security)
- [Gennemse nye funktioner og egenskaber](/cloud-app-security/release-notes)
- [Se grundlæggende konfigurationsvejledninger](/cloud-app-security/general-setup)

## <a name="12-monitor-for-threats-and-take-action"></a>12: Hold øje med trusler, og gør noget

Microsoft 365 indeholder flere måder til at overvåge status og udføre relevante handlinger. Dit bedste udgangspunkt er <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalen Microsoft 365 Defender</a>, hvor du kan se din organisations [Microsoft Secure Score](./defender/microsoft-secure-score.md) samt eventuelle beskeder eller enheder, der kræver din opmærksomhed.

- [Introduktion til Microsoft 365 Defender portalen](./defender/microsoft-365-defender.md#the-microsoft-365-defender-portal)
- [Se sikkerhedsportalerne i Microsoft 365](./defender/portals.md)

## <a name="next-steps"></a>Næste trin

Tillykke! Du har hurtigt implementeret nogle af de vigtigste sikkerhedsbeskyttelse, og din organisation er meget mere sikker. Nu er du klar til at gå skridtet videre med funktioner til trusselsbeskyttelse (herunder Microsoft Defender til slutpunkt), dataklassificering og beskyttelsesfunktioner og sikring af administrative konti. Du kan finde et mere dybt, metodisk sæt sikkerhedsanbefalinger for Microsoft 365 i [Microsoft 365 Security for Business Decision Makers (BDMs) (Business Decision Makers).](Microsoft-365-security-for-bdm.md)

Besøg også Microsofts nye Defender for Cloud på [docs.microsoft.com/security](/security).
