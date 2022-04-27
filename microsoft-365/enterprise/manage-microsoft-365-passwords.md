---
title: Administrer adgangskoder for Microsoft 365 brugerkonto
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Få mere at vide om, hvordan du administrerer Microsoft 365 adgangskoder til brugerkonti.
ms.openlocfilehash: 689f88c2380f0655af70cea08404ed7163fa1239
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094388"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>Administrer adgangskoder for Microsoft 365 brugerkonto

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan administrere Microsoft 365 adgangskoder til brugerkonti på flere forskellige måder, afhængigt af din identitetskonfiguration. Du kan administrere brugerkonti i [Microsoft 365 Administration](/admin), i Active Directory-domæneservices (AD DS) eller i Azure Active Directory (Azure AD) Administration.

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>Planlæg, hvor og hvordan du vil administrere adgangskoder for din brugerkonto

Hvor og hvordan du kan administrere dine brugerkonti, afhænger af den identitetsmodel, du vil bruge til dine Microsoft 365. De to modeller er kun cloudbaserede og hybride.
  
### <a name="cloud-only"></a>Kun i skyen

Du administrerer adgangskoder for brugerkonti i:

- [Microsoft 365 Administration](/admin)
- Azure AD Administration
    
### <a name="hybrid"></a>Hybrid

Med hybrididentitet gemmes adgangskoder i AD DS, så du skal bruge AD DS-værktøjer i det lokale miljø til at administrere adgangskoder til brugerkonti. Selv når du bruger PHS (Password Hash Synchronization), hvor Azure AD gemmer en hashkodet version af den allerede hashkodede version i AD DS, skal du og brugerne administrere deres adgangskoder i AD DS.

Med [tilbageførsel af adgangskode](#pw_writeback) kan brugerne ændre deres AD DS-adgangskoder via Azure AD.

## <a name="prevent-bad-passwords"></a>Undgå forkerte adgangskoder

Alle dine brugere skal bruge [Microsofts adgangskodevejledning](https://www.microsoft.com/research/publication/password-guidance) til at oprette deres adgangskoder til brugerkontoen.

Hvis du vil forhindre brugerne i at oprette en adgangskode, der er let at bestemme, skal du bruge Azure AD-adgangskodebeskyttelse, som bruger både en global liste over forbudte adgangskoder og en valgfri brugerdefineret liste over forbudte adgangskoder, som du angiver. Du kan f.eks. angive ord, der er specifikke for din organisation, f.eks.:

- Mærker
- Produktnavne
- Placeringer (f.eks. virksomhedens hovedkontor)
- Virksomhedsspecifikke interne vilkår
- Forkortelser, der har en bestemt betydning for virksomheden

Du kan forbyde forkerte adgangskoder [i skyen](/azure/active-directory/authentication/concept-password-ban-bad) og til [AD DS i det lokale miljø](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

## <a name="simplify-user-sign-in"></a>Gør brugerlogon mere enkel

Azure AD Seamless Single Sign-On (Azure AD Seamless SSO) fungerer sammen med PHS og Pass-Through Authentication (PTA) for at give dine brugere mulighed for at logge på tjenester, der bruger Azure AD-brugerkonti uden at skulle indtaste deres adgangskoder og i mange tilfælde deres brugernavne. Det giver brugerne lettere adgang til cloudbaserede programmer, f.eks. Office 365, uden at de har brug for yderligere komponenter i det lokale miljø, f.eks. identitetsforbundne servere.

Du kan konfigurere Azure AD Seamless SSO med Azure AD Forbind-værktøjet. Se [vejledningen til konfiguration af Azure AD Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>Gør det nemmere at opdatere adgangskoder til AD DS

Med tilbageførsel af adgangskode kan du give brugerne mulighed for at nulstille deres adgangskoder via Azure AD, som derefter replikeres til AD DS. Brugerne behøver ikke at få adgang til deres AD DS i det lokale miljø for at opdatere deres adgangskoder. Dette er værdifuldt for roaming- eller fjernbrugere, der ikke har en fjernadgangsforbindelse til netværket i det lokale miljø.

Tilbageførsel af adgangskode er påkrævet for fuldt ud at udnytte azure AD Identity Protection-funktioner, f.eks. kræve, at brugerne ændrer deres adgangskoder i det lokale miljø, når der er registreret en høj risiko for, at kontoen kompromitteres.

Du kan finde flere oplysninger og konfigurationsvejledninger under [Azure AD SSPR med tilbageførsel af adgangskode](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Opgrader til den nyeste version af Azure AD Forbind for at sikre den bedst mulige oplevelse og nye funktioner, efterhånden som de udgives. Du kan få flere oplysninger under [Brugerdefineret installation af Azure AD-Forbind](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>Gør nulstilling af adgangskode enklere

Selvbetjent nulstilling af adgangskode (SSPR) giver brugerne mulighed for at nulstille eller låse deres adgangskoder eller konti op. Hvis du vil advare dig om misbrug, kan du bruge den detaljerede rapportering, der sporer, når brugerne tilgår systemet, sammen med meddelelser. Du skal aktivere [tilbageførsel af adgangskode](#pw_writeback) , før du kan installere nulstilling af adgangskode.

Se [vejledningen til udrulning af nulstilling af adgangskode](/azure/active-directory/authentication/howto-sspr-deployment).