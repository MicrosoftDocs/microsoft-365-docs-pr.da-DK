---
title: Angiv udløbspolitikken for adgangskoder for organisationen
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
description: Få mere at vide om, hvordan en administrator kan angive en udløbspolitik for adgangskoder for din virksomhed, skole eller nonprofitorganisation Microsoft 365 Administration.
ms.openlocfilehash: 9ba871a166169a0125b68808c124b10802424dfd
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63590153"
---
# <a name="set-the-password-expiration-policy-for-your-organization"></a>Angiv udløbspolitikken for adgangskoder for organisationen

## <a name="before-you-begin"></a>Før du begynder

Denne artikel er for personer, der angiver udløbspolitikken for adgangskoder for en virksomhed, skole eller non-profit organisation. For at fuldføre disse trin skal du logge på med Microsoft 365 administratorkonto. [Hvad er en administratorkonto?](/microsoft-365/admin/add-users/about-admin-roles).

Som administrator kan du indstille brugernes adgangskoder til at udløbe efter et bestemt antal dage eller til aldrig at udløbe. Som standard er adgangskoder indstillet til aldrig at udløbe for din organisation.

Aktuelle undersøgelser indikerer på det kraftigste, at ændringer af adgangskoder gør mere skade end gavn. De driver brugerne til at vælge svage adgangskoder, anvende adgangskoder igen eller opdatere gamle adgangskoder på måder, som hackere nemt kan gætte. Vi anbefaler, at [du aktiverer multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md). Du kan få mere at vide om adgangskodepolitik i Anbefalinger [til adgangskodepolitik](../misc/password-policy-recommendations.md).

Du skal være [global administrator for](../add-users/about-admin-roles.md) at udføre disse trin.

Hvis du er bruger, har du ikke tilladelse til at indstille din adgangskode til aldrig at udløbe. Bed teknisk support på din arbejdsplads eller skole om at udføre trinnene for dig.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="set-password-expiration-policy"></a>Angiv udløbspolitik for adgangskoder

Følg nedenstående trin, hvis du vil indstille brugeradgangskoder til at udløbe efter et bestemt tidsrum.

1. I gruppen Microsoft 365 Administration du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**fanen Sikkerhed og &**</a> under **Org Indstillinger**.

    Hvis du ikke er global administrator, kan du ikke se indstillingen Sikkerhed og beskyttelse af personlige oplysninger.
  
1. Vælg **Udløbspolitik for adgangskoder**.
  
1. Hvis du ikke ønsker, at brugerne skal ændre deres adgangskoder, skal du fjerne markeringen i afkrydsningsfeltet ud for Angiv brugeradgangskoder til at **udløbe efter et antal dage**.

1. Angiv, hvor ofte adgangskoder skal udløbe. Vælg et antal dage mellem 14 og 730.
  
1. Skriv, hvornår brugeren skal have besked om, at adgangskoden udløber i det andet felt, og vælg derefter **Gem**. Vælg et antal dage mellem 1 og 30.

> [!IMPORTANT]
> Meddelelser om udløb af adgangskoder understøttes ikke længere Office webapps [eller Administration](https://portal.office.com).
  
## <a name="important-things-you-need-to-know-about-the-password-expiration-feature"></a>Vigtige ting, du bør vide om funktionen udløb af adgangskoder
  
Personer, der kun Outlook-appen, tvinges ikke til at nulstille deres Microsoft 365 adgangskode, før den udløber i cachen. Dette kan være flere dage efter den faktiske udløbsdato. Der er ingen løsning til dette på administratorniveau.

## <a name="prevent-last-password-from-being-used-again"></a>Forhindre, at den sidste adgangskode bruges igen

Hvis du vil forhindre, at dine brugere genbruger gamle adgangskoder, kan du gøre det ved at gennemtvinge adgangskodehistorik i det lokale Active Directory (AD). Se [Opret en brugerdefineret adgangskodepolitik](/azure/active-directory-domain-services/password-policy#create-a-custom-password-policy).

I Azure AD kan den sidste adgangskode ikke bruges igen, når brugeren ændrer en adgangskode. Adgangskodepolitikken anvendes på alle brugerkonti, der oprettes og administreres direkte i Azure AD. Denne adgangskodepolitik kan ikke ændres. Se [Politikker for adgangskoder til Azure AD](/azure/active-directory/authentication/concept-sspr-policy#password-policies-that-only-apply-to-cloud-user-accounts).

## <a name="synchronize-user-passwords-hashes-from-an-on-premises-active-directory-to-azure-ad-microsoft-365"></a>Synkroniser brugeradgangskoderhashes fra et lokalt Active Directory til Azure AD (Microsoft 365)

Denne artikel handler om at indstille udløbspolitikken for brugere, der kun bruger skyen (Azure AD). Den gælder ikke for hybrididentitetsbrugere, der bruger synkronisering af adgangskodehash, pass-through-godkendelse eller lokal sammenslutning som f.eks. ADFS.
  
Du kan få mere at vide om, hvordan du synkroniserer brugeradgangskodehashes fra lokal AD til Azure AD under [Implementer synkronisering af adgangskodehash med Azure AD Forbind synkronisering](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization).

## <a name="password-policies-and-account-restrictions-in-azure-active-directory"></a>Adgangskodepolitikker og kontobegrænsninger i Azure Active Directory

Du kan angive flere adgangskodepolitikker og begrænsninger i Azure Active Directory. Se [Adgangskodepolitikker og kontobegrænsninger i Adgangskode Azure Active Directory](/azure/active-directory/authentication/concept-sspr-policy) for at få flere oplysninger.

## <a name="update-password-policy"></a>Opdater adgangskodepolitik

Den Set-MsolPasswordPolicy-cmdlet opdaterer adgangskodepolitikken for et bestemt domæne eller lejer og angiver det tidsrum, en adgangskode forbliver gyldig, før den skal ændres.

Du kan få mere at vide om, hvordan du opdaterer adgangskodepolitikken for et bestemt domæne eller en bestemt lejer, [under Set-MsolPasswordPolicy](/powershell/module/msonline/set-msolpasswordpolicy).

## <a name="related-content"></a>Relateret indhold

[Lad brugere nulstille deres egne adgangskoder](../add-users/let-users-reset-passwords.md) (artikel)/

[Nulstil adgangskoder](../add-users/reset-passwords.md) (artikel)
