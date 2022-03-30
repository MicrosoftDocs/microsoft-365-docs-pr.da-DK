---
title: Trin 1. Bestem din skyidentitetsmodel
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Trin 1. Bestem din Microsoft-skyidentitetsmodel
ms.openlocfilehash: 2f9527b05a688b27304529634a75db4ef8a1b07d
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63598599"
---
# <a name="step-1-determine-your-cloud-identity-model"></a>Trin 1. Bestem din skyidentitetsmodel

Microsoft 365 bruger Azure Active Directory (Azure AD), en skybaseret brugeridentitet og autentifikationsservice, der er inkluderet i dit Microsoft 365-abonnement, til at administrere identiteter og godkendelse for Microsoft 365. Det er vigtigt at få konfigureret din identitetsinfrastruktur korrekt Microsoft 365 administration af brugeradgang og tilladelser for organisationen.

Før du begynder, kan du se denne video for at få et overblik over identitetsmodeller og godkendelse til Microsoft 365.

<p> </p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE2Pjwu]

Dit første planlægningsvalg er din skyidentitetsmodel.

## <a name="microsoft-cloud-identity-models"></a>Microsoft-skyidentitetsmodeller

Hvis du vil planlægge brugerkonti, skal du først forstå de to identitetsmodeller i Microsoft 365. Du kan kun bevare organisationens identiteter i skyen, eller du kan bevare dine lokale Active Directory-domæneservices-identiteter (AD DS) og bruge dem til godkendelse, når brugere får adgang til Microsoft 365-skytjenester.

Her er de to typer identiteter og deres bedste tilpasning og fordele.

| Attribut | Kun skyidentitet | Hybrididentitet |
|:-------|:-----|:-----|
| **Definition** | Brugerkonto findes kun i Azure AD-lejeren for dit Microsoft 365 abonnement. | Brugerkonto findes i et AD DS og der findes også en kopi i Azure AD-lejeren for Microsoft 365 abonnement. Brugerkontoen i Azure AD kan også indeholde en ændret version af den allerede AD DS adgangskoden til brugerkontoen. |
| **Sådan Microsoft 365 brugerlegitimationsoplysninger** | Azure AD-lejeren for dit Microsoft 365-abonnement udfører godkendelsen med skyidentitetskontoen. | Azure AD-lejeren for dit Microsoft 365 håndterer godkendelsesprocessen eller omdirigerer brugeren til en anden identitetsudbyder. |
| **Bedst til** | Organisationer, der ikke har eller har brug for en lokal AD DS. | Organisationer, der AD DS en anden identitetsudbyder. |
| **Største fordel** | Nem at bruge. Der kræves ingen ekstra katalogværktøjer eller servere. | Brugere kan bruge de samme legitimationsoplysninger, når de får adgang til lokale eller skybaserede ressourcer. |
||||

## <a name="cloud-only-identity"></a>Kun skyidentitet

En identitet, der kun findes i skyen, bruger brugerkonti, der kun findes i Azure AD. Identitet, der kun findes i skyen, bruges typisk af små organisationer, der ikke har lokale servere eller ikke bruger AD DS til at administrere lokale identiteter.

Her er de grundlæggende komponenter i en identitet, der kun findes i skyen.

![Grundlæggende komponenter i kun skyidentitet.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Både lokale og eksterne (online) brugere bruger deres Azure AD-brugerkonti og adgangskoder til at få adgang Microsoft 365 skytjenester. Azure AD godkender brugerlegitimationsoplysninger baseret på de gemte brugerkonti og adgangskoder.

### <a name="administration"></a>Administration
Da brugerkonti kun gemmes i Azure AD, administrerer du skyidentiteter med værktøjer som [Microsoft 365 Administration og](/admin) [Windows PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md).

## <a name="hybrid-identity"></a>Hybrididentitet

Hybrididentitet bruger konti, der stammer fra en lokal AD DS og har en kopi i Azure AD-lejeren for et Microsoft 365 abonnement. De fleste ændringer, med undtagelse af [bestemte kontoattributter](/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized), flyder kun én måde. De ændringer, du foretager AD DS brugerkonti, synkroniseres med deres kopi i Azure AD.

Azure AD Forbind den løbende synkronisering af konti. Den kører på en lokal server, kontrollerer, om der er ændringer i AD DS og videresender disse ændringer til Azure AD. Azure AD Forbind giver mulighed for at filtrere, hvilke konti der synkroniseres, og om du vil synkronisere en hash-version af brugeradgangskoder, også kaldet synkronisering af adgangskodehash ( PHS).

Når du implementerer hybrididentitet, er din lokale AD DS den autoritative kilde til kontooplysninger. Det betyder, at du hovedsageligt udfører administrationsopgaver i det lokale miljø, som derefter synkroniseres med Azure AD.

Her er komponenterne for hybrididentitet.

![Komponenter i hybrididentitet.](../media/about-microsoft-365-identity/hybrid-identity.png)

Azure AD-lejeren har en kopi af de AD DS konti. I denne konfiguration godkendes både lokale brugere og eksterne brugere, der Microsoft 365 skytjenester, i Azure AD.

> [!NOTE]
> Du skal altid bruge Azure AD-Forbind at synkronisere brugerkonti til hybrididentitet. Du skal bruge de synkroniserede brugerkonti i Azure AD for at kunne udføre licenstildeling og gruppeadministration, konfigurere tilladelser og andre administrative opgaver, der involverer brugerkonti.

### <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a>Hybrid identitet og katalogsynkronisering til Microsoft 365

Afhængigt af virksomhedens behov og tekniske krav er hybrididentitetsmodellen og katalogsynkronisering det mest almindelige valg for virksomhedskunder, der Microsoft 365. Katalogsynkronisering gør det muligt at administrere identiteter i din Active Directory-domæneservices (AD DS), og alle opdateringer af brugerkonti, grupper og kontakter synkroniseres med Azure Active Directory-lejeren (Azure AD) i dit Microsoft 365-abonnement.

>[!Note]
>Når AD DS brugerkonti synkroniseres for første gang, tildeles de ikke automatisk en Microsoft 365-licens og kan ikke få adgang til Microsoft 365-tjenester, f.eks. mail. Du skal først tildele dem en brugsplacering. Tildel derefter en licens til disse brugerkonti enten enkeltvis eller dynamisk via gruppemedlemskab.
>

#### <a name="authentication-for-hybrid-identity"></a>Godkendelse til hybrididentitet

Der findes to typer godkendelse, når du bruger hybrididentitetsmodellen:

- Administreret godkendelse

  Azure AD håndterer godkendelsesprocessen ved hjælp af en lokalt gemt hashedsversion af adgangskoden eller sender legitimationsoplysningerne til en lokal softwareagent for at blive godkendt af den lokale AD DS.

- Federated Authentication

  Azure AD omdirigerer klientcomputeren, der anmoder om godkendelse, til en anden identitetsudbyder.

#### <a name="managed-authentication"></a>Administreret godkendelse

Der findes to typer administreret godkendelse:

- Synkronisering af adgangskodehash (PHS)

  Azure AD udfører selve godkendelsen.

- Pass-through-godkendelse (PTA)

  Azure AD AD DS udføre godkendelsen.


##### <a name="password-hash-synchronization-phs"></a>Synkronisering af adgangskodehash (PHS)

Med PHS synkroniserer du dine AD DS-brugerkonti Microsoft 365 og administrerer dine brugere lokalt. Hashes af brugeradgangskoder synkroniseres fra din AD DS til Azure AD, så brugerne har den samme adgangskode lokalt og i skyen. Dette er den nemmeste måde at aktivere godkendelse AD DS identiteter i Azure AD. 

![Synkronisering af adgangskodehash (PHS).](../media/plan-for-directory-synchronization/phs-authentication.png)

Når adgangskoder ændres eller nulstilles lokalt, synkroniseres de nye adgangskodehashes med Azure AD, så brugerne altid kan bruge den samme adgangskode til skyressourcer og lokale ressourcer. Brugeradgangskoder sendes aldrig til Azure AD eller gemmes i Azure AD i klar tekst. Nogle førsteklassesfunktioner i Azure AD, f.eks Identity Protection, kræver PHS, uanset hvilken godkendelsesmetode der vælges.
  
Se [vælge den rigtige godkendelsesmetode for at](/azure/active-directory/hybrid/choose-ad-authn) få mere at vide.
  
##### <a name="pass-through-authentication-pta"></a>Pass-through-godkendelse (PTA)

PTA giver en enkel adgangskodevalidering for Azure AD-godkendelsestjenester, der bruger en softwareagent, der kører på en eller flere lokale servere, til at validere brugerne direkte med din AD DS. Med PTA synkroniserer du AD DS-brugerkonti med Microsoft 365 og administrerer dine brugere lokalt. 

![Pass-through-godkendelse (PTA).](../media/plan-for-directory-synchronization/pta-authentication.png)

PTA gør det muligt for brugerne at logge på både lokale og lokale Microsoft 365 og programmer ved hjælp af deres lokale konto og adgangskode. Denne konfiguration validerer brugernes adgangskoder direkte i forhold til din lokale AD DS uden at gemme adgangskodehashes i Azure AD. 

PTA er også for organisationer med et sikkerhedskrav om øjeblikkeligt at gennemtvinge tilstande for lokale brugerkontoer, adgangskodepolitikker og logontimer. 
  
Se [vælge den rigtige godkendelsesmetode for at](/azure/active-directory/hybrid/choose-ad-authn) få mere at vide.
  
##### <a name="federated-authentication"></a>Federated Authentication

Federated Authentication er primært for store virksomhedsorganisationer med mere komplekse godkendelseskrav. AD DS identiteter synkroniseres med Microsoft 365 og brugerkonti administreres lokalt. Med federated authentication har brugerne den samme adgangskode lokalt og i skyen, og de behøver ikke at logge på igen for at bruge Microsoft 365. 

Federated Authentication kan understøtte yderligere godkendelseskrav, f.eks chipkort-baseret godkendelse eller en tredjeparts multifaktorgodkendelse og er typisk påkrævet, når organisationer har et godkendelseskrav, der ikke oprindeligt understøttes af Azure AD.
 
Se [vælge den rigtige godkendelsesmetode for at](/azure/active-directory/hybrid/choose-ad-authn) få mere at vide.
  
For tredjepartsudbydere af godkendelse og identitet kan katalogobjekter i det lokale miljø synkroniseres med Microsoft 365 og ressourceadgang i skyen, som primært administreres af en tredjepartsidentitetsudbyder. Hvis din organisation bruger en tredjepartssammenslutningsløsning, kan du konfigurere logon med den løsning til Microsoft 365 forudsat, at tredjepartssammenslutningsløsningen er kompatibel med Azure AD.
  
Se Azure [AD-sammenslutningens kompatibilitetsliste for](/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) at få mere at vide.
  
### <a name="administration"></a>Administration

Da de oprindelige og autoritative brugerkonti er gemt i den lokale AD DS, administrerer du dine identiteter med de samme værktøjer, som du administrerer dine AD DS.

Du bruger ikke bruger-Microsoft 365 Administration eller PowerShell til Microsoft 365 administrere synkroniserede brugerkonti i Azure AD.

## <a name="next-step"></a>Næste trin

[![Beskyt dine Microsoft 365-konti](../media/deploy-identity-solution-overview/protect-your-global-administrator-accounts.png)](protect-your-global-administrator-accounts.md)

Fortsæt med [trin 2](protect-your-global-administrator-accounts.md) for at sikre dine globale administratorkonti.
