---
title: Administrere adgangskoder Microsoft 365 til brugerkonti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du Microsoft 365 adgangskoder til brugerkonti.
ms.openlocfilehash: 6a0d4298f3d6c46ab067795bccf01123605ce1aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594343"
---
# <a name="manage-microsoft-365-user-account-passwords"></a>Administrere adgangskoder Microsoft 365 til brugerkonti

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Du kan administrere adgangskoder Microsoft 365 din brugerkonto på flere forskellige måder, afhængigt af din identitetskonfiguration. Du kan administrere brugerkonti [i Microsoft 365 Administration](/admin), Active Directory-domæneservices (AD DS) eller i Azure Active Directory (Azure AD).

## <a name="plan-for-where-and-how-you-will-manage-your-user-account-passwords"></a>Planlæg, hvor og hvordan du vil administrere adgangskoder til din brugerkonto

Hvor og hvordan du kan administrere dine brugerkonti afhænger af den identitetsmodel, du vil bruge til din Microsoft 365. De to modeller er kun i skyen og hybrid.
  
### <a name="cloud-only"></a>Kun i skyen

Du administrerer adgangskoder til brugerkonti i:

- [Den Microsoft 365 Administration](/admin)
- Azure AD Administration
    
### <a name="hybrid"></a>Hybrid

Med hybrididentitet gemmes adgangskoder i AD DS så du skal bruge lokale AD DS til at administrere adgangskoder til brugerkonti. Selv når du bruger synkronisering af adgangskodehash ( PHS), hvor Azure AD gemmer en forsænket version af den allerede gemte version i AD DS, skal du og brugerne administrere deres adgangskoder i AD DS.

Med [tilbageførsel af](#pw_writeback) adgangskode kan brugerne ændre deres adgangskoder AD DS via Azure AD.

## <a name="prevent-bad-passwords"></a>Undgå ugyldige adgangskoder

Alle dine brugere skal bruge [Microsofts adgangskodevejledning til](https://www.microsoft.com/research/publication/password-guidance) at oprette deres adgangskoder til brugerkonti.

For at forhindre brugere i at oprette en let bestemt adgangskode skal du bruge Azure AD-adgangskodebeskyttelse, som både bruger en global liste over forbudte adgangskoder og en valgfri brugerdefineret liste over forbudte adgangskoder, som du angiver. Du kan f.eks. angive ord, der er specifikke for din organisation, f.eks.:

- Brandnavne
- Produktnavne
- Placeringer (f.eks. virksomhedens hovedkontor)
- Virksomhedsspecifikke interne begreber
- Forkortelser, der har en bestemt betydning for virksomheden

Du kan udelukke [ugyldige adgangskoder i](/azure/active-directory/authentication/concept-password-ban-bad) skyen og for [din lokale AD DS](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).

## <a name="simplify-user-sign-in"></a>Gør bruger login mere enkelt

Azure AD Seamless Single Sign-On (Azure AD Seamless SSO) fungerer sammen med PHS og Pass-Through Authentication (PTA) for at give brugerne mulighed for at logge på tjenester, der bruger Azure AD-brugerkonti uden at skulle skrive deres adgangskoder og i mange tilfælde deres brugernavne. Dette giver dine brugere nemmere adgang til skybaserede programmer, f.eks. Office 365, uden brug af yderligere lokale komponenter som f.eks. identitetssammenslutningsservere.

Du konfigurerer Azure AD Seamless SSO med Azure AD Forbind værktøjet. Se vejledningen [til konfiguration af Azure AD Seamless SSO](/azure/active-directory/connect/active-directory-aadconnect-sso-quick-start).

<a name="pw_writeback"></a>
## <a name="simplify-password-updates-to-ad-ds"></a>Gør adgangskodeopdateringer mere simple for AD DS

Med tilbageførsel af adgangskode kan du tillade brugere at nulstille deres adgangskoder via Azure AD, som derefter replikeres til AD DS. Brugere behøver ikke at få adgang til deres lokale netværk eller AD DS at opdatere deres adgangskoder. Dette har stor værdi for brugere af roaming eller eksterne brugere, der ikke har en fjernadgangsforbindelse til det lokale netværk.

Tilbageførsel af adgangskode er påkrævet for fuldt ud at bruge Azure AD Identity Protection-funktionerne, f.eks. krav om, at brugerne skal ændre deres lokale adgangskoder, når der er registreret en høj risiko for, at kontoen kompromitteres.

Du kan finde flere oplysninger og konfigurationsinstruktioner [i Azure AD SSPR med tilbageførsel af adgangskode](/azure/active-directory/active-directory-passwords-writeback).

>[!Note]
>Opgrader til den nyeste version af Azure AD Forbind for at sikre den bedst mulige oplevelse og nye funktioner, efterhånden som de frigives. Få mere at vide under [Brugerdefineret installation af Azure AD Forbind](/azure/active-directory/connect/active-directory-aadconnect-get-started-custom).
>

## <a name="simplify-password-resets"></a>Gør nulstilling af adgangskode mere enkelt

Selvbetjening for nulstilling af adgangskode (SSPR) giver brugerne mulighed for at nulstille eller låse op for deres adgangskoder eller konti. For at advare dig om misbrug eller misbrug kan du bruge den detaljerede rapportering, der registrerer, hvornår brugere får adgang til systemet, sammen med meddelelser. Du skal aktivere [tilbageførsel af adgangskode,](#pw_writeback) før du kan installere nulstilling af adgangskode.

Se vejledningen [for at udrulle nulstilling af adgangskode](/azure/active-directory/authentication/howto-sspr-deployment).