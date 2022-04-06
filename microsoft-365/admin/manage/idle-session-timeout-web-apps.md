---
title: Timeout for inaktiv session for Microsoft 365
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Adm_TOC
description: Angiv, hvor længe brugerens session varer, Microsoft 365 før de får time time out.
ms.openlocfilehash: 215b900315b2d98b01a8cf87b14a6fa65289e121
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63705365"
---
# <a name="idle-session-timeout-for-microsoft-365-public-preview"></a>Timeout for inaktiv session til Microsoft 365 (offentlig prøveversion)

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Brug timeout for inaktiv session til at konfigurere en politik for, hvor længe brugere er inaktive i organisationen, før de logges af Microsoft 365 webapps. Dette er med til at beskytte følsomme virksomhedsdata og føjer et ekstra lag af sikkerhed til slutbrugere, der arbejder på enheder, der ikke er virksomheder eller er delte.

Når en bruger når den inaktive timeoutsession, du har angivet, får de besked om, at de er ved at blive logget af. De skal vælge for at forblive logget på, ellers logges de automatisk af alle Microsoft 365 webapps.

> [!IMPORTANT]
> Timeout for inaktive sessioner påvirker ikke dine Microsoft 365-skrivebords- og mobilapps.

## <a name="turn-on-idle-session-timeout"></a>Slå timeout for Inaktiv session til

Hvis du ikke er Microsoft 365 global Office 365 administrator, kan du ikke se fanen **Sikkerhed og & beskyttelse af** personlige oplysninger.

1. I gruppen Microsoft 365 Administration du vælge **Indstillinger sikkerhedsoplysninger** **->**[& og](https://go.microsoft.com/fwlink/p/?linkid=2072756) vælge **Timeout for Inaktiv session**.  

2. I **Timeout for Ledig session skal** du vælge til/fra-knappen for at aktivere den. Du kan vælge en standardindstilling eller vælge dit eget brugerdefinerede tidspunkt. Det tager et par minutter, før den inaktive session er aktiveret i din organisation.

> [!NOTE]
> Hvis du har konfigureret timeoutpolitikker for inaktiv session [for Outlook-webapp](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) og [SharePoint Online](/sharepoint/sign-out-inactive-users), tilsidesætter aktivering af timeout for inaktiv session i Microsoft 365 Administration Outlook-webappen og SharePoint-indstillingerne.

Timeout for inaktive sessioner er en af de mange sikkerhedsforanstaltninger i Microsoft 365. Du kan få mere at vide om andre Microsoft 365 i [Øverste sikkerhedsopgaver i Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Hvad brugerne får vist

Når en bruger har været inaktiv Microsoft 365 webapps i den tidsperiode, du vælger, får brugeren vist følgende meddelelse. De skal vælge Hold **dig logget på** , ellers logges de af.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Skærmbillede: Spørg, om din session er ved at udløbe. Vælg Hold dig logget på, så du ikke logges af Microsoft 365 webapps":::

## <a name="details-about-idle-session-timeout"></a>Oplysninger om timeout for inaktiv session

- Følgende Microsoft 365 webapps understøttes. Der tilføjes snart flere webapps.

    - Outlook Web App

    - OneDrive for Business

    - SharePoint Online (SPO)

    - Office.com og andre startsider

    - Office (Word, Excel, PowerPoint) på internettet

    - Microsoft 365 Administration Center

- Aktivitet refererer til brugerinteraktion på klientsiden, der finder sted i forbindelse med webappen. Museklik og tryk på tastatur.  

- Timeout for inaktive sessioner fungerer pr. browser-session. En brugers aktivitet på en Microsoft Edge behandles anderledes end aktivitet i andre browsere, f.eks. Google Chrome. Brugere logges af alle faner, der svarer til deres konto i den pågældende browsersession.

- Når du har aktiveret timeout for inaktiv session, gælder det for hele organisationen og kan ikke begrænses til bestemte brugere, organisationsenheder eller grupper. Brug [betinget adgang i Azure AD](/azure/active-directory/conditional-access/) til politikker for forskellige brugere og grupper.

- Brugere skal være inaktive på Microsoft 365-webappfaner i den konfigurerede varighed. Hvis brugeren er aktiv på én fane (f.eks. OWA), mens han eller hun er inaktiv på en anden fane (f.eks. SPO), betragtes brugeren som aktiv og logges ikke af.  

- Brugerne bliver ikke logget af i disse tilfælde.
    - Hvis de får single sign-on (SSO) i webappen fra den enhed, der er forbundet  med kontoen, eller de har valgt Hold dig logget på, da de loggede på. Hvis du vil have mere at vide om at skjule denne indstilling for din organisation, [skal du se Føje branding til din organisations logonside](/azure/active-directory/fundamentals/customize-branding).
    - Hvis de er på en administreret enhed (en, der er kompatibel eller forbundet til et domæne) og bruger en understøttet browser som f.eks. Microsoft Edge eller Google Chrome (med [Windows-kontoudvidelsen](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Hvis denne funktion ikke skal udløses på en administreret enhed, kræves et kvalificerede Azure AD Premium P1- eller P2-abonnement og en bestemt politik for betinget adgang. Du kan få mere at vide nedenfor.

> [!IMPORTANT]
> Timeout for inaktive sessioner er ikke tilgængelig for Microsoft 365 drevet af 21Vianet eller Microsoft 365 Germany.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Timeout for inaktiv session på enheder, der ikke er administrerede  

For at timeout for inaktiv session bliver udløst på enheder, der ikke er administrerede, skal du tilføje en politik for betinget adgang i Azure AD Administration.

1. På **siden Betinget adgang | Siden** Politikker i Azure AD Administration skal du vælge **Ny politik** og angive et navn til politikken.

2. Vælg **Brugere eller identiteter for arbejdsbelastning**, og vælg derefter **Alle brugere**.

3. Vælg **Skyapps eller handlinger**, **Vælg apps**, og søg **efter Office 365**. Vælg **Office 365**, og vælg **derefter Vælg**.  

4. Vælg **Betingelser**, **Klientapps**, **Konfigurer til Ja**, **Browser**, og vælg derefter **Udført**.

5. Vælg **Session**, **Brug tvungne appbegrænsninger**, og vælg **derefter.**

6. Aktiver politikken, og vælg **Opret**.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Er der nogen browsere eller browserscenarier, hvor timeoutfunktionen for inaktive sessioner ikke virker?  

Timeout for inaktive sessioner understøttes ikke, når tredjepartscookies deaktiveres i browseren. Brugerne får ikke vist nogen prompter om at logge af. Vi anbefaler at holde indstillingen for forebyggelse af sporing [balanceret (standard)](/microsoft-edge/web-platform/tracking-prevention) for Microsoft Edge og cookies fra tredjeparter aktiveret i dine andre browsere. Microsoft 365 apps og tjenester har siden 17. august 2021 stoppet understøttelsen af Internet Explorer 11.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Hvordan skal jeg forberede mig, hvis min organisation allerede bruger eksisterende Outlook webapp og SharePoint onlinetidspolitikker for inaktive timeouts?  

Hvis du allerede bruger eksisterende Outlook webapp og SharePoint politikker for inaktiv onlinetid, kan du stadig aktivere timeoutfunktion for inaktiv session. Når du slår politikken for inaktiv timeout til, tilsidesætter den den eksisterende Outlook-webapp og SharePoint Online-politikker. Vi planlægger at fraråde den eksisterende Outlook-webapp og SharePoint Online-politikker i den nærmeste fremtid. For bedre at forberede din organisation anbefaler vi, at du slår timeout for inaktiv session til.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Hvad sker der, hvis jeg er inaktiv på en inkluderet Microsoft 365-webapp, men aktiv på en Microsoft-webapp eller SaaS-webapp, der ikke har inaktiv sessionstimeout slået til?  

Følgende Microsoft 365 webapps understøttes.

- Outlook Web App

- OneDrive for Business

- SharePoint Online (SPO)

- Office.com og andre startsider

- Office (Word, Excel, PowerPoint) på internettet

- Microsoft 365 Administration Center

Hvis du arbejder på en anden webapp med den samme konto, anvendes aktiviteten i den pågældende webapp ikke på timeout for den inaktive session.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Jeg vil foretage ændringer i timeoutpolitikken for inaktive sessioner eller slette den. Hvordan gør jeg det?

Opdater politikken:

1. I gruppen Microsoft 365 Administration du vælge **Org-indstillinger**, gå til fanen Sikkerhed og **&** vælge **Timeout for Inaktiv session**.

2. Vælg en anden timeoutværdi i rullemenuen, og vælg derefter **Gem**.  

Slet politikken:

1. I gruppen Microsoft 365 Administration du vælge **Org-indstillinger**, gå til fanen Sikkerhed og **&** vælge **Timeout for Inaktiv session**.

2. Fjern markeringen **i afkrydsningsfeltet Slå til for at angive inaktivitetsperioden for** brugere, der skal være logget af Office-webapps, og vælg **Gem**.
