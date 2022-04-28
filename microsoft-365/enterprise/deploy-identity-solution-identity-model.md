---
title: Trin 1. Bestem din cloudidentitetsmodel
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.date: 09/30/2020
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Trin 1. Fastlæg din Microsoft-cloudidentitetsmodel
ms.openlocfilehash: 41604ebb08104f802e33023763e9771d2b6acfda
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101265"
---
# <a name="step-1-determine-your-cloud-identity-model"></a>Trin 1. Bestem din cloudidentitetsmodel

Microsoft 365 bruger Azure Active Directory (Azure AD), en cloudbaseret brugeridentitets- og godkendelsestjeneste, der følger med dit Microsoft 365 abonnement, til at administrere identiteter og godkendelse for Microsoft 365. Det er vigtigt at få konfigureret din identitetsinfrastruktur korrekt for at administrere Microsoft 365 brugeradgang og tilladelser for din organisation.

Før du begynder, kan du se denne video for at få en oversigt over identitetsmodeller og godkendelse for Microsoft 365.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Dit første planlægningsvalg er din cloudidentitetsmodel.

## <a name="microsoft-cloud-identity-models"></a>Microsofts cloudidentitetsmodeller

Hvis du vil planlægge brugerkonti, skal du først forstå de to identitetsmodeller i Microsoft 365. Du kan kun vedligeholde din organisations identiteter i cloudmiljøet, eller du kan vedligeholde dine AD DS-identiteter (Active Directory i det lokale miljø Domain Services) og bruge dem til godkendelse, når brugerne får adgang til Microsoft 365 cloudtjenester.

Her er de to typer af identitet og deres bedste pasform og fordele.

| Attribut | Kun cloud-id | Hybrididentitet |
|:-------|:-----|:-----|
| **Definition** | Brugerkontoen findes kun i Azure AD-lejeren for dit Microsoft 365 abonnement. | Brugerkontoen findes i AD DS, og der findes også en kopi i Azure AD-lejeren for dit Microsoft 365 abonnement. Brugerkontoen i Azure AD kan også indeholde en hashkodet version af adgangskoden til AD DS-brugerkontoen, der allerede er hashkodet. |
| **Sådan godkender Microsoft 365 brugerlegitimationsoplysninger** | Azure AD-lejeren for dit Microsoft 365-abonnement udfører godkendelsen med cloudidentitetskontoen. | Azure AD-lejeren for dit Microsoft 365-abonnement håndterer enten godkendelsesprocessen eller omdirigerer brugeren til en anden identitetsudbyder. |
| **Bedst til** | Organisationer, der ikke har eller har brug for ad DS i det lokale miljø. | Organisationer, der bruger AD DS eller en anden identitetsudbyder. |
| **Største fordel** | Nem at bruge. Der kræves ingen ekstra katalogværktøjer eller -servere. | Brugerne kan bruge de samme legitimationsoplysninger, når de får adgang til lokale eller skybaserede ressourcer. |
||||

## <a name="cloud-only-identity"></a>Kun cloud-id

En skybaseret identitet bruger brugerkonti, der kun findes i Azure AD. Identitet, der kun findes i skyen, bruges typisk af små organisationer, der ikke har lokale servere eller ikke bruger AD DS til at administrere lokale identiteter.

Her er de grundlæggende komponenter i identitet, der kun findes i cloudmiljøet.

![Grundlæggende komponenter i identitet, der kun er i cloudmiljøet.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Både lokale og eksterne (online) brugere bruger deres Azure AD-brugerkonti og -adgangskoder til at få adgang til Microsoft 365 cloudtjenester. Azure AD godkender brugerlegitimationsoplysninger baseret på de gemte brugerkonti og adgangskoder.

### <a name="administration"></a>Administration
Da brugerkonti kun gemmes i Azure AD, kan du administrere cloudidentiteter med værktøjer som [Microsoft 365 Administration](/admin) og [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md).

## <a name="hybrid-identity"></a>Hybrididentitet

Hybrididentitet bruger konti, der stammer fra en AD DS i det lokale miljø og har en kopi i Azure AD-lejeren for et Microsoft 365-abonnement. De fleste ændringer, med undtagelse af [specifikke kontoattributter](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), flower kun én måde. De ændringer, du foretager af AD DS-brugerkonti, synkroniseres med deres kopi i Azure AD.

Azure AD Forbind leverer den løbende kontosynkronisering. Den kører på en server i det lokale miljø, kontrollerer, om der er ændringer i AD DS, og videresender disse ændringer til Azure AD. Azure AD Forbind gør det muligt at filtrere, hvilke konti der synkroniseres, og om der skal synkroniseres en hashkodet version af brugeradgangskoder, også kaldet synkronisering af adgangskodehash (PHS).

Når du implementerer hybrididentitet, er AD DS i det lokale miljø den autoritative kilde til kontooplysninger. Det betyder, at du primært udfører administrationsopgaver i det lokale miljø, som derefter synkroniseres til Azure AD.

Her er komponenterne i hybrididentitet.

![Komponenter i hybrididentitet.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD-lejeren har en kopi af AD DS-kontiene. I denne konfiguration godkendes både lokale og eksterne brugere, der får adgang til Microsoft 365 cloudtjenester, i Azure AD.

> [!NOTE]
> Du skal altid bruge Azure AD-Forbind til at synkronisere brugerkonti for hybrididentitet. Du skal bruge de synkroniserede brugerkonti i Azure AD for at kunne udføre licenstildeling og gruppeadministration, konfigurere tilladelser og andre administrative opgaver, der omfatter brugerkonti.

### <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a>Synkronisering af hybrididentitet og mappe for Microsoft 365

Afhængigt af dine forretningsbehov og tekniske krav er hybrididentitetsmodellen og katalogsynkroniseringen det mest almindelige valg for virksomhedskunder, der anvender Microsoft 365. Katalogsynkronisering giver dig mulighed for at administrere identiteter i dit ad-DS (Active Directory-domæneservices), og alle opdateringer af brugerkonti, grupper og kontakter synkroniseres med Azure AD-lejeren (Azure Active Directory) for dit Microsoft 365-abonnement.

>[!Note]
>Når AD DS-brugerkonti synkroniseres første gang, tildeles de ikke automatisk en Microsoft 365-licens og kan ikke få adgang til Microsoft 365 tjenester, f.eks. mail. Du skal først tildele dem en forbrugsplacering. Derefter skal du tildele en licens til disse brugerkonti enten individuelt eller dynamisk via gruppemedlemskab.
>

#### <a name="authentication-for-hybrid-identity"></a>Godkendelse af hybrididentitet

Der er to godkendelsestyper, når du bruger hybrididentitetsmodellen:

- Administreret godkendelse

  Azure AD håndterer godkendelsesprocessen ved hjælp af en hashkodet version af adgangskoden, der er gemt lokalt, eller sender legitimationsoplysningerne til en lokal softwareagent, der skal godkendes af AD DS i det lokale miljø.

- Federated Authentication

  Azure AD omdirigerer den klientcomputer, der anmoder om godkendelse, til en anden identitetsudbyder.

#### <a name="managed-authentication"></a>Administreret godkendelse

Der er to typer administreret godkendelse:

- Synkronisering af adgangskodehash (PHS)

  Azure AD udfører selve godkendelsen.

- Pass-through-godkendelse (PTA)

  Azure AD har AD DS til at udføre godkendelsen.


##### <a name="password-hash-synchronization-phs"></a>Synkronisering af adgangskodehash (PHS)

Med PHS synkroniserer du dine AD DS-brugerkonti med Microsoft 365 og administrerer dine brugere i det lokale miljø. Hashværdier for brugeradgangskoder synkroniseres fra dit AD DS til Azure AD, så brugerne har den samme adgangskode i det lokale miljø og i cloudmiljøet. Dette er den nemmeste måde at aktivere godkendelse for AD DS-identiteter på i Azure AD. 

![Synkronisering af adgangskodehash (PHS).](../media/plan-for-directory-synchronization/phs-authentication.png)

Når adgangskoder ændres eller nulstilles i det lokale miljø, synkroniseres de nye adgangskodehashs til Azure AD, så dine brugere altid kan bruge den samme adgangskode til cloudressourcer og ressourcer i det lokale miljø. Brugeradgangskoder sendes aldrig til Azure AD eller gemmes i Azure AD som klartekst. Nogle premiumfunktioner i Azure AD, f.eks Identity Protection, kræver PHS, uanset hvilken godkendelsesmetode der vælges.
  
Se [Valg af den rigtige godkendelsesmetode](/azure/active-directory/hybrid/choose-ad-authn) for at få mere at vide.
  
##### <a name="pass-through-authentication-pta"></a>Pass-through-godkendelse (PTA)

PTA leverer en simpel adgangskodevalidering for Azure AD-godkendelsestjenester ved hjælp af en softwareagent, der kører på en eller flere lokale servere, for at validere brugerne direkte med din AD DS. Med PTA synkroniserer du AD DS-brugerkonti med Microsoft 365 og administrerer dine brugere i det lokale miljø. 

![Pass-through-godkendelse (PTA).](../media/plan-for-directory-synchronization/pta-authentication.png)

PTA giver brugerne mulighed for at logge på både det lokale miljø og Microsoft 365 ressourcer og programmer ved hjælp af deres lokale konto og adgangskode. Denne konfiguration validerer brugernes adgangskoder direkte mod din AD DS i det lokale miljø uden at gemme adgangskodehash i Azure AD. 

PTA er også til organisationer med et sikkerhedskrav om straks at gennemtvinge tilstande for brugerkonti i det lokale miljø, adgangskodepolitikker og logontimer. 
  
Se [Valg af den rigtige godkendelsesmetode](/azure/active-directory/hybrid/choose-ad-authn) for at få mere at vide.
  
##### <a name="federated-authentication"></a>Federated Authentication

Organisationsnetværksgodkendelse er primært til store virksomhedsorganisationer med mere komplekse godkendelseskrav. AD DS-identiteter synkroniseres med Microsoft 365 og brugerkonti administreres i det lokale miljø. Med godkendelse i organisationsnetværket har brugerne den samme adgangskode i det lokale miljø og i cloudmiljøet, og de behøver ikke at logge på igen for at bruge Microsoft 365. 

Sammenkædet godkendelse kan understøtte yderligere godkendelseskrav, f.eks. chipkortbaseret godkendelse eller en flerfaktorgodkendelse fra tredjepart, og det er typisk påkrævet, når organisationer har et godkendelseskrav, der ikke understøttes oprindeligt af Azure AD.
 
Se [Valg af den rigtige godkendelsesmetode](/azure/active-directory/hybrid/choose-ad-authn) for at få mere at vide.
  
For tredjepartsgodkendelses- og identitetsprovidere kan katalogobjekter i det lokale miljø synkroniseres til Microsoft 365 og adgang til cloudressourcer, der primært administreres af en idP (third-party identity provider). Hvis din organisation bruger en tredjepartsorganisationsløsning, kan du konfigurere logon med denne løsning til Microsoft 365, forudsat at tredjeparts federationløsningen er kompatibel med Azure AD.
  
Se [kompatibilitetslisten for Azure AD Federation](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) for at få mere at vide.
  
### <a name="administration"></a>Administration

Da de oprindelige og autoritative brugerkonti er gemt i AD DS i det lokale miljø, kan du administrere dine identiteter med de samme værktøjer, som du administrerer AD DS.

Du bruger ikke Microsoft 365 Administration eller PowerShell til Microsoft 365 til at administrere synkroniserede brugerkonti i Azure AD.

## <a name="next-step"></a>Næste trin

[![Beskyt dine Microsoft 365 privilegerede konti](../media/deploy-identity-solution-overview/protect-your-global-administrator-accounts.png)](protect-your-global-administrator-accounts.md)

Fortsæt med [trin 2](protect-your-global-administrator-accounts.md) for at sikre dine globale administratorkonti.
