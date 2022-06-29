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
description: Angiv, hvor lang tid brugerens session skal vare i Microsoft 365, før brugeren får timeout.
ms.openlocfilehash: 611541ebc16c3ee8c187b8fc1a5b33661b221897
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487471"
---
# <a name="idle-session-timeout-for-microsoft-365"></a>Timeout for inaktiv session for Microsoft 365

<!-- Add metadata: localization, AdminSurgePortfolio, admindeeplinkMAC. remove robots nofollow -->

Brug timeout for inaktiv session til at konfigurere en politik for, hvor længe brugere er inaktive i din organisation, før de er logget af Microsoft 365-webapps. Dette hjælper med at beskytte følsomme virksomhedsdata og tilføjer endnu et lag af sikkerhed for slutbrugere, der arbejder på ikke-virksomhedsenheder eller delte enheder.

Når en bruger når den inaktive timeoutsession, du har angivet, får vedkommende en meddelelse om, at vedkommende er ved at blive logget af. De skal vælge at forblive logget på, ellers bliver de automatisk logget af alle Microsoft 365-webapps.

> [!IMPORTANT]
> Timeout for inaktiv session påvirker ikke dine Microsoft 365-skrivebords- og mobilapps.

## <a name="turn-on-idle-session-timeout"></a>Slå timeout for inaktiv session til

Hvis du ikke er Microsoft 365 eller Office 365 global administrator, kan du ikke se fanen **Sikkerhed & beskyttelse af personlige oplysninger**.

1. I Microsoft 365 Administration skal du vælge **Organisationsindstillinger** **->**[Sikkerhed & fanen beskyttelse af personlige oplysninger](https://go.microsoft.com/fwlink/p/?linkid=2072756) og vælge **Timeout for inaktiv session**.  

2. På **timeout for inaktiv session** skal du vælge til/fra-knappen for at aktivere den. Du kan vælge en standardindstilling eller vælge dit eget brugerdefinerede klokkeslæt. Det tager et par minutter, før inaktiv session er slået til i din organisation.

> [!NOTE]
> Hvis du har konfigureret timeoutpolitikker for inaktive sessioner for [Outlook-webapp](https://support.microsoft.com/topic/description-of-the-activity-based-authentication-timeout-for-owa-in-office-365-0c101e1b-020e-69c1-a0b0-26532d60c0a4) og [SharePoint Online](/sharepoint/sign-out-inactive-users), tilsidesætter aktivering af timeout for inaktive sessioner i Microsoft 365 Administration Outlook-webappen og SharePoint-indstillingerne.

Timeout for inaktiv session er en af de mange sikkerhedsforanstaltninger i Microsoft 365. Hvis du vil vide mere om andre sikkerhedsopgaver i Microsoft 365, skal du se [De vigtigste sikkerhedsopgaver i Microsoft 365](../../security/top-security-tasks-for-remote-work.md).  

## <a name="what-users-will-see"></a>Det får brugerne vist

Når en bruger har været inaktiv i Microsoft 365-webapps i den valgte tidsperiode, får vedkommende vist følgende prompt. De skal vælge **Forbliv logget på** , ellers bliver de logget af.

:::image type="content" source="../../media/idle-session-timeout.png" alt-text="Skærmbillede: Spørg, om din session er ved at udløbe. Vælg Forbliv logget på, så du ikke bliver logget af Microsoft 365-webapps":::

## <a name="details-about-idle-session-timeout"></a>Oplysninger om timeout for inaktiv session

- Følgende Microsoft 365-webapps understøttes. Der vil snart blive tilføjet flere webapps.

    - Outlook Web App

    - OneDrive for Business

    - SharePoint Online (SPO)

    - Office.com og andre startsider

    - Office (Word, Excel, PowerPoint) på internettet

    - Microsoft 365 Administration Centreret

- Aktivitet refererer til enhver brugerinteraktion på klientsiden, der finder sted i webappens kontekst. Det kan f.eks. være museklik og tastaturtryk.  

- Timeout for inaktiv session fungerer pr. browsersession. En brugers aktivitet på Microsoft Edge behandles anderledes end deres aktivitet i andre browsere, f.eks. Google Chrome. Brugerne bliver logget af fra alle faner, der svarer til deres konto i den pågældende browsersession.

- Når du har slået timeout for inaktiv session til, gælder den for hele organisationen og kan ikke begrænses til bestemte brugere, organisationsenheder eller grupper. Brug Azure AD politikker for [betinget adgang](/azure/active-directory/conditional-access/) for forskellige brugere og grupper til at få adgang til SharePoint og Exchange Online.

- Brugerne skal være inaktive på alle faner i Microsoft 365-webappen i den konfigurerede varighed. Hvis brugeren er aktiv på én fane (f.eks. OWA), mens vedkommende er inaktiv på en anden fane (f.eks. SPO), betragtes vedkommende som aktiv og bliver ikke logget af.  

- Brugerne bliver ikke logget af i disse tilfælde.
    - Hvis de får enkeltlogon (SSO) til webappen fra den enhedstilsluttede konto eller vælger **Forbliv logget** på, når de logger på. Du kan finde flere oplysninger om, hvordan du skjuler denne indstilling for din organisation, under [Føj branding til organisationens logonside](/azure/active-directory/fundamentals/customize-branding).
    - Hvis de er på en administreret enhed (en, der overholder eller er tilsluttet et domæne) og bruger en understøttet browser, f.eks. Microsoft Edge eller Google Chrome (med [udvidelsen Windows-konti](https://chrome.google.com/webstore/detail/windows-accounts/ppnbnpeolgkicgegkbkbjmhlideopiji)). Hvis denne funktion ikke skal udløses på en administreret enhed, kræves der et berettiget Azure AD Premium P1- eller P2-abonnement og en specifik politik for betinget adgang. Se nedenfor for at få flere oplysninger.

> [!IMPORTANT]
> Timeout for inaktiv session er ikke tilgængelig for Microsoft 365, der drives af 21Vianet eller Microsoft 365 Germany.

## <a name="idle-session-timeout-on-unmanaged-devices"></a>Timeout for inaktiv session på ikke-administrerede enheder  

Hvis timeout for inaktiv session skal udløses på ikke-administrerede enheder, skal du tilføje en politik for betinget adgang i Azure AD Administration.

1. I **| Betinget adgang Siden Politikker** i Azure AD Administration, vælg **Ny politik**, og angiv et navn til politikken.

2. Vælg **Brugere eller arbejdsbelastningsidentiteter**, og vælg derefter **Alle brugere**.

3. Vælg **Cloudapps eller -handlinger**, **Vælg apps**, og søg efter **Office 365**. Vælg **Office 365**, og vælg derefter **Vælg**.  

4. Vælg **Betingelser**, **Klientapps**, **Konfigurer til Ja**, **Browser**, og vælg derefter **Udført**.

5. Vælg **Session**, **Brug tvungne begrænsninger for appen**, og **vælg derefter.**

6. Aktivér politikken, og vælg **Opret**.

## <a name="frequently-asked-questions"></a>Ofte stillede spørgsmål

### <a name="are-there-any-browsers-or-browser-scenarios-in-which-idle-session-timeout-feature-doesnt-work"></a>Er der nogen browsere eller browserscenarier, hvor timeoutfunktionen for inaktive sessioner ikke virker?  

Timeout for inaktiv session understøttes ikke, når cookies fra tredjepart er deaktiveret i browseren. Brugerne kan ikke se nogen logonprompts. Vi anbefaler, at du bevarer indstillingen til forebyggelse af sporing til [Balanceret (standard)](/microsoft-edge/web-platform/tracking-prevention) for Microsoft Edge og cookies fra tredjepart aktiveret i dine andre browsere. Microsoft 365-apps og -tjenester har holdt op med at understøtte Internet Explorer 11 siden den 17. august 2021.

### <a name="how-should-i-prepare-if-my-organization-is-already-using-existing-outlook-web-app-and-sharepoint-online-idle-timeout-policies"></a>Hvordan skal jeg forberede mig, hvis min organisation allerede bruger eksisterende Timeoutpolitikker for inaktive Outlook-webapps og SharePoint Online?  

Hvis du allerede bruger eksisterende Outlook-webapps og timeoutpolitikker for inaktivitet i SharePoint Online, kan du stadig aktivere timeoutfunktionen for inaktive sessioner. Når du slår timeoutpolitikken for inaktivitet til, tilsidesættes den eksisterende Outlook-webapp og SharePoint Online-politikker. Vi planlægger at fraråde de eksisterende Outlook-webapps og SharePoint Online-politikker i nær fremtid. Hvis du vil forberede din organisation bedre, anbefaler vi, at du slår timeout for inaktiv session til.

### <a name="what-happens-if-i-am-inactive-on-an-included-microsoft-365-web-app-but-active-on-a-microsoft-web-app-or-saas-web-app-that-doesnt-have-idle-session-timeout-turned-on"></a>Hvad sker der, hvis jeg er inaktiv i en inkluderet Microsoft 365-webapp, men er aktiv i en Microsoft-webapp eller SaaS-webapp, hvor timeout for inaktiv session ikke er slået til?  

Følgende Microsoft 365-webapps understøttes.

- Outlook Web App

- OneDrive for Business

- SharePoint Online (SPO)

- Office.com og andre startsider

- Office (Word, Excel, PowerPoint) på internettet

- Microsoft 365 Administration Centreret

Hvis du arbejder på en anden webapp med den samme konto, anvendes aktiviteten i den pågældende webapp ikke på timeout for inaktive sessioner.

### <a name="i-want-to-make-changes-to-the-idle-session-timeout-policy-or-delete-it-how-can-i-do-that"></a>Jeg vil foretage ændringer i timeoutpolitikken for inaktive sessioner eller slette den. Hvordan kan jeg gøre det?

Opdater politikken:

1. I Microsoft 365 Administration skal du vælge **Organisationsindstillinger**, gå til fanen **Sikkerhed & Beskyttelse af personlige oplysninger** og vælge **Timeout for inaktiv session**.

2. Vælg en anden timeoutværdi i rullemenuen, og vælg derefter **Gem**.  

Slet politikken:

1. I Microsoft 365 Administration skal du vælge **Organisationsindstillinger**, gå til fanen **Sikkerhed & Beskyttelse af personlige oplysninger** og vælge **Timeout for inaktiv session**.

2. Fjern markeringen i **Afkrydsningsfeltet Slå til for at angive inaktivitetsperioden for brugere, der skal være logget af Office-webapps** , og vælg **Gem**.
