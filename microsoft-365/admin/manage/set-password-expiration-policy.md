---
title: Angiv politikken for udløb af adgangskode for din organisation
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 0f54736f-eb22-414c-8273-498a0918678f
description: Få mere at vide om, hvordan en administrator kan angive en udløbspolitik for adgangskoder for din virksomhed, skole eller nonprofitorganisation i Microsoft 365 Administration.
ms.openlocfilehash: b7f7691d0c1c0e6177d5414bc7802b62bb07a3b3
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468772"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Angiv politikken for udløb af adgangskode for din organisation

## <a name="before-you-begin"></a>Før du begynder

Denne artikel er til personer, der angiver en politik for udløb af adgangskode for en virksomhed, skole eller nonprofitorganisation. Hvis du vil fuldføre disse trin, skal du logge på med din Microsoft 365 administratorkonto. [Hvad er en administratorkonto?](/microsoft-365/admin/add-users/about-admin-roles).

Som administrator kan du få brugeradgangskoder til at udløbe efter et bestemt antal dage eller indstille adgangskoder til aldrig at udløbe. Adgangskoder er som standard angivet til aldrig at udløbe for din organisation.

Aktuelle undersøgelser viser på det kraftigste, at mandatændringer af adgangskoder gør mere skade end gavn. De driver brugerne til at vælge svagere adgangskoder, genbruge adgangskoder eller opdatere gamle adgangskoder på måder, der let gættes af hackere. Vi anbefaler, at du aktiverer [multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md). Hvis du vil vide mere om adgangskodepolitik, skal du se [Anbefalinger til adgangskodepolitik](../misc/password-policy-recommendations.md).

Du skal være [global administrator](../add-users/about-admin-roles.md) for at kunne udføre disse trin.

Hvis du er bruger, har du ikke tilladelse til at angive din adgangskode til aldrig at udløbe. Bed din tekniske support til dit arbejde eller din skole om at udføre trinnene i denne artikel for dig.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="set-password-expiration-policy"></a>Angiv politik for udløb af adgangskode

Følg nedenstående trin, hvis du vil angive, at brugeradgangskoder skal udløbe efter et bestemt tidsrum.

1. I Microsoft 365 Administration skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">fanen **Sikkerhed & beskyttelse af personlige oplysninger**</a>.

    Hvis du ikke er global administrator eller sikkerhedsadministrator, kan du ikke se indstillingen Sikkerhed & beskyttelse af personlige oplysninger.
  
1. Vælg **Politik for udløb af adgangskode**.
  
1. Hvis du ikke ønsker, at brugerne skal ændre adgangskoder, skal du fjerne markeringen i afkrydsningsfeltet ud for **Angiv adgangskoder til aldrig at udløbe**.

1. Skriv, hvor ofte adgangskoder skal udløbe. Vælg et antal dage mellem 14 og 730.
 
> [!IMPORTANT]
> Meddelelser om udløb af adgangskode understøttes ikke længere i Office webapps eller [i Administration](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Vigtige ting, du skal vide om udløbsfunktionen for adgangskoden
  
Personer, der kun bruger Outlook-appen, bliver ikke tvunget til at nulstille deres Microsoft 365 adgangskode, før den udløber i cachen. Dette kan være flere dage efter den faktiske udløbsdato. Der er ingen løsning på dette på administratorniveau.

## <a name="prevent-last-password-from-being-used-again"></a>Undgå, at den seneste adgangskode bruges igen

Hvis du vil forhindre dine brugere i at genbruge gamle adgangskoder, kan du gøre det ved at gennemtvinge adgangskoder i Active Directory i det lokale miljø (AD). Se [Opret en brugerdefineret adgangskodepolitik](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

I Azure AD kan den sidste adgangskode ikke bruges igen, når brugeren ændrer en adgangskode. Adgangskodepolitikken anvendes på alle brugerkonti, der oprettes og administreres direkte i Azure AD. Denne adgangskodepolitik kan ikke ændres. Se [Azure AD adgangskodepolitikker](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synkroniser brugeradgangskoder fra en Active Directory i det lokale miljø til Azure AD (Microsoft 365)

Denne artikel omhandler angivelse af udløbspolitikken for brugere, der kun har skyen (Azure AD). Det gælder ikke for hybride identitetsbrugere, der bruger synkronisering af adgangskodehash, pass-through-godkendelse eller sammenslutning i det lokale miljø, f.eks. ADFS.
  
Hvis du vil vide mere om, hvordan du synkroniserer brugeradgangskodehash fra AD i det lokale miljø til Azure AD, skal du se [Implementer synkronisering af adgangskodehash med Azure AD Forbind synkronisering](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Adgangskodepolitikker og kontobegrænsninger i Azure Active Directory

Du kan angive flere politikker og begrænsninger for adgangskoder i Azure Active Directory. Se [adgangskodepolitikker og kontobegrænsninger i Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) for at få flere oplysninger.

## <a name="update-password-policy"></a>Opdater adgangskodepolitik

Den Set-MsolPasswordPolicy cmdlet opdaterer adgangskodepolitikken for et angivet domæne eller en bestemt lejer og angiver, hvor lang tid en adgangskode forbliver gyldig, før den skal ændres.

Hvis du vil vide mere om, hvordan du opdaterer adgangskodepolitikken for et bestemt domæne eller en bestemt lejer, skal [du se Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>Relateret indhold

[Lad brugerne nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)/

[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)
