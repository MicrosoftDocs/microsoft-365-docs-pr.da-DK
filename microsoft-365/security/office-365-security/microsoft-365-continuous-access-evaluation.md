---
title: Løbende evaluering af adgang til Microsoft 365 – Microsoft 365 til virksomheder
description: Beskriver, hvordan betinget adgangsevaluering for Microsoft 365 og Azure AD proaktivt afslutter aktive brugersessioner og gennemtvinger ændringer i lejerpolitikken i nær realtid.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 255618508559e989a356ab404429bc4d87bfe2c6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594053"
---
# <a name="continuous-access-evaluation-for-microsoft-365"></a>Løbende evaluering af adgang til Microsoft 365

Moderne skytjenester, der bruger OAuth 2.0 til godkendelse, er traditionelt afhængig af udløb af adgangstoken for at tilbagekalde en brugerkontos adgang. I praksis betyder det, at selvom en administrator tilbagekalder en brugerkontos adgang, vil brugeren stadig have adgang, indtil adgangstokenet udløber, hvilket for Microsoft 365 som standard plejede at være op til en time efter, at den første tilbagekaldelseshændelse fandt sted.

Evaluering af betinget adgang for Microsoft 365 og Azure Active Directory (Azure AD) afslutter proaktivt aktive brugersessioner og gennemtvinger ændringer i lejerpolitikken næsten i realtid i stedet for at være afhængig af udløb af adgangstoken. Azure AD giver besked om evalueringsaktiveret for kontinuerlig adgang til Microsoft 365-tjenester (f.eks. SharePoint, Teams og Exchange), når brugerkontoen eller lejeren er blevet ændret på en måde, der kræver, at brugerkontoens godkendelsestilstand ændres.

Når en klient med kontinuerlig adgang, som f.eks. Outlook forsøger at få adgang til Exchange med en eksisterende adgangstoken, afvises tokenet af tjenesten, hvilket beder om en ny Azure AD-godkendelse. Resultatet er næsten håndhævelsen af brugerkontoen og politikken i realtid.

Her er nogle flere fordele:

- For en ondsindet insider, der kopierer og eksporterer et gyldigt adgangstoken uden for organisationen, forhindrer kontinuerlig adgangsevaluering brugen af dette token via politikken for placering af Azure AD IP-adresser. Med løbende evaluering af adgang synkroniserer Azure AD politikker ned til understøttede Microsoft 365-tjenester, så når et adgangstoken forsøger at få adgang til tjenesten fra et sted uden for IP-adresseområdet i politikken, afviser tjenesten tokenet.

- Kontinuert adgangsevaluering forbedrer fleksibiliteten ved at kræve færre tokenopdateringer. Da understøttende tjenester modtager proaktive meddelelser om krav om genautentiering, kan Azure AD udstede længerevarende tokens, f.eks. mere end en time. Med længerevarende tokens behøver klienter ikke at anmode om en tokenopdatering fra Azure AD så ofte, så brugeroplevelsen er mere robust.

Her er nogle eksempler på situationer, hvor kontinuerlig adgangsevaluering forbedrer sikkerheden for kontrol af brugeradgang:

- En brugerkontos adgangskode er blevet kompromitteret, så en administrator gør alle eksisterende sessioner ugyldige og nulstiller adgangskoden Microsoft 365 Administration. I næsten realtid bliver alle eksisterende brugersessioner med Microsoft 365 tjenester ugyldige.

- En bruger, der arbejder på et dokument i Word, tager sin tablet til en offentlig café, der ikke er i et administrator defineret og godkendt IP-adresseområde. På caféen blokeres brugerens adgang til dokumentet med det samme.

For Microsoft 365 er kontinuert adgangsevaluering i øjeblikket understøttet af:

- Exchange, SharePoint og Teams tjenester.
- Outlook, Teams, Office og OneDrive i en webbrowser og for Win32-, iOS-, Android- og Mac-klienterne.

Microsoft arbejder på yderligere Microsoft 365-tjenester og -klienter for at understøtte kontinuerlig adgangsevaluering.

Kontinuerlig adgangsevaluering medtages i alle versioner af Office 365 og Microsoft 365. Konfiguration af Betingede adgangspolitikker kræver Azure AD Premium P1, som er inkluderet i alle Microsoft 365 versioner.

> [!NOTE]
> Se [denne artikel](/azure/active-directory/conditional-access/concept-continuous-access-evaluation#limitations) for begrænsningerne ved kontinuerlig adgangsevaluering.

## <a name="scenarios-supported-by-microsoft-365"></a>Scenarier, der understøttes af Microsoft 365

Kontinuerlig adgangsevaluering understøtter to typer hændelser:

- Vigtige hændelser er dem, hvor en bruger skal miste adgang.
- Evaluering af betinget adgang til politik sker, når en bruger skulle miste adgangen til en ressource baseret på en administratordefineret politik.

Kritiske hændelser omfatter:

- Brugerkonto er deaktiveret
- Adgangskoden er ændret
- Brugersessioner tilbagekaldes
- Multifaktorgodkendelse er aktiveret for brugeren
- Kontorisici øges på baggrund af evalueringen af adgangen fra [Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)

Evaluering af betinget adgang-politik sker, når brugerkontoen ikke længere opretter forbindelse fra et netværk, der er tillid til.

Følgende tjenester Microsoft 365 i øjeblikket evaluering af kontinuerlig adgang ved at lytte til begivenheder fra Azure AD.

<br>

****

|Håndhævelsestype|Exchange|SharePoint|Teams|
|---|---|---|---|
|**Kritiske hændelser:**||||
|Brugerens tilbagekaldelse|Understøttet|Understøttet|Understøttet|
|Bruger risiko|Understøttet|Understøttes ikke|Understøttes ikke|
|**Evaluering af betinget adgang-politik:**||||
|Politik for placering af IP-adresse|Understøttet|Understøttet\*|Understøttet|
|

\*SharePoint Office webbrowser understøtter øjeblikkelig håndhævelse af IP-politikken ved at aktivere streng tilstand. Uden streng tilstand er adgangstokenslevetid én time.

Du kan finde flere oplysninger om, hvordan du konfigurerer en politik for Betinget adgang, [i denne artikel](/azure/active-directory/conditional-access/overview).

## <a name="microsoft-365-clients-supporting-continuous-access-evaluation"></a>Microsoft 365 klienter, der understøtter kontinuerlig adgangsevaluering

Kunder med mulighed for kontinuerlig adgang til evaluering for Microsoft 365 understøtter en kravudfordring, som er en omdirigering af en brugersession til Azure AD til genautentiering, når en cachelagret brugertoken afvises af en kontinuerlig adgangsevalueringsaktiveret Microsoft 365-tjeneste.

Følgende klienter understøtter løbende evaluering af adgang på internettet, Win32, iOS, Android og Mac:

- Outlook
- Teams
- Office\*
- SharePoint
- OneDrive

\*Kravudfordring understøttes ikke Office til internettet.

For kunder, der ikke understøtter kontinuerlig adgangsevaluering, forbliver adgangstokenslevetid for brugere Microsoft 365 som standard en time.

## <a name="see-also"></a>Se også

- [Kontinuerlig adgangsevaluering](/azure/active-directory/conditional-access/concept-continuous-access-evaluation)
- [Dokumentation om betinget adgang](/azure/active-directory/conditional-access/overview)
- [Dokumentation til Azure AD Identity Protection](/azure/active-directory/identity-protection/overview-identity-protection)
