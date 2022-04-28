---
title: Trin 2. Beskyt dine Microsoft 365 privilegerede konti
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 09/30/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365initiative-coredeploy
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 6b4ded77-ac8d-42ed-8606-c014fd947560
description: Denne artikel indeholder oplysninger om beskyttelse af privilegeret adgang til din Microsoft 365 lejer.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 34e4665067640ec625501b15c12c1c2e80d5ffb4
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095592"
---
# <a name="step-2-protect-your-microsoft-365-privileged-accounts"></a>Trin 2. Beskyt dine Microsoft 365 privilegerede konti

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Sikkerhedsbrud på en Microsoft 365 lejer, herunder indsamling af oplysninger og phishing-angreb, udføres typisk ved at kompromittere legitimationsoplysningerne for en Microsoft 365 privilegeret konto. Sikkerhed i cloudmiljøet er et partnerskab mellem dig og Microsoft:
  
- Microsofts cloudtjenester er bygget på et fundament af tillid og sikkerhed. Microsoft giver dig sikkerhedskontroller og -funktioner, der kan hjælpe dig med at beskytte dine data og programmer.
    
- Du ejer dine data og identiteter og ansvaret for at beskytte dem, sikkerheden for dine ressourcer i det lokale miljø og sikkerheden for cloudkomponenter, som du styrer.
    
Microsoft leverer funktioner, der kan hjælpe med at beskytte din organisation, men de er kun effektive, hvis du bruger dem. Hvis du ikke bruger dem, kan du være sårbar over for angreb. For at beskytte dine privilegerede konti er Microsoft her for at hjælpe dig med detaljerede instruktioner til:
  
1. Opret dedikerede, privilegerede, cloudbaserede konti, og brug dem kun, når det er nødvendigt.
    
2. Konfigurer multifaktorgodkendelse (MFA) for dine dedikerede Microsoft 365 privilegerede konti, og brug den stærkeste form for sekundær godkendelse.

3. Beskyt privilegerede konti med anbefalinger til Nul tillid identitet og enhedsadgang.

## <a name="1-create-dedicated-privileged-cloud-based-user-accounts-and-use-them-only-when-necessary"></a>1. Opret dedikerede, privilegerede, skybaserede brugerkonti, og brug dem kun, når det er nødvendigt

I stedet for at bruge daglige brugerkonti, der er blevet tildelt administratorroller, skal du oprette dedikerede brugerkonti, der har administratorrollerne i Azure AD. 

Fra nu af logger du kun på med de dedikerede privilegerede konti for opgaver, der kræver administratorrettigheder. Alle andre Microsoft 365 administration skal udføres ved at tildele andre administrationsroller til brugerkonti.
  
> [!NOTE]
> Dette kræver yderligere trin for at logge af som din daglige brugerkonto og logge på med en dedikeret administratorkonto. Men det skal kun gøres lejlighedsvis i forbindelse med administratorhandlinger. Overvej at gendanne dit Microsoft 365 abonnement efter brud på en administratorkonto kræver mange flere trin.

Du skal også oprette [akutadgangskonti](/azure/active-directory/roles/security-emergency-access) for at forhindre, at azure AD låses utilsigtet.

Du kan beskytte dine privilegerede konti yderligere med Azure AD Privileged Identity Management (PIM) til tildeling efter behov af administratorroller efter behov. 
 
## <a name="2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-privileged-accounts"></a>2. Konfigurer multifaktorgodkendelse for dine dedikerede Microsoft 365 privilegerede konti

Multifaktorgodkendelse kræver yderligere oplysninger ud over kontonavnet og adgangskoden. Microsoft 365 understøtter disse yderligere kontrolmetoder:
  
- Appen Microsoft Authenticator
- Et telefonopkald
- En tilfældigt genereret bekræftelseskode, der sendes via en sms
- Et chipkort (virtuelt eller fysisk) (kræver godkendelse i organisationsnetværket)
- En biometrisk enhed
- Oauth-token
- 
    
>[!Note]
>For organisationer, der skal overholde NIST-standarder (National Institute of Standards and Technology), begrænses brugen af et telefonopkald eller sms-baserede yderligere kontrolmetoder. Klik [her](https://pages.nist.gov/800-63-FAQ/#q-b01) for at få flere oplysninger.
>

Hvis du er en lille virksomhed, der kun bruger brugerkonti, der kun er gemt i cloudmiljøet (identitetsmodellen kun i cloudmiljøet), skal du [konfigurere MFA](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) til at konfigurere MFA ved hjælp af et telefonopkald eller en bekræftelseskode for en sms, der er sendt til en smartphone for hver dedikeret privilegeret konto.
    
Hvis du er en større organisation, der bruger en Microsoft 365 hybrididentitetsmodel, har du flere kontrolmuligheder. Hvis du allerede har sikkerhedsinfrastrukturen til en stærkere sekundær godkendelsesmetode, skal du [konfigurere MFA](../admin/security-and-compliance/set-up-multi-factor-authentication.md) og konfigurere hver dedikeret privilegeret konto for den relevante kontrolmetode.
  
Hvis sikkerhedsinfrastrukturen for den ønskede stærkere kontrolmetode ikke er på plads og fungerer for Microsoft 365 MFA, anbefaler vi på det kraftigste, at du konfigurerer dedikerede privilegerede konti med MFA ved hjælp af Microsoft Authenticator-appen, et telefonopkald eller en bekræftelseskode til en sms, der sendes til en smart telefon for dine privilegerede konti som en midlertidig sikkerhedsforanstaltning. Lad ikke dine dedikerede privilegerede konti være uden den ekstra beskyttelse, der leveres af MFA.
  
Du kan få flere oplysninger under [MFA for Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md).
  
## <a name="3-protect-administrator-accounts-with-zero-trust-identity-and-device-access-recommendations"></a>3. Beskyt administratorkonti med Nul tillid anbefalinger til identitet og enhedsadgang

For at hjælpe med at sikre en sikker og produktiv arbejdsstyrke giver Microsoft en række anbefalinger til [identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). I forbindelse med identitet skal du bruge anbefalingerne og indstillingerne i disse artikler:

- [Forudsætninger](../security/office-365-security/identity-access-prerequisites.md)
- [Fælles politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md)

## <a name="additional-protections-for-enterprise-organizations"></a>Yderligere beskyttelse af virksomhedsorganisationer

Brug disse yderligere metoder til at sikre, at din privilegerede konto og den konfiguration, du udfører ved hjælp af den, er så sikker som muligt.
  
### <a name="privileged-access-workstation"></a>Arbejdsstation med privilegeret adgang

Hvis du vil sikre, at udførelsen af yderst privilegerede opgaver er så sikker som muligt, skal du bruge en arbejdsstation med privilegeret adgang (PAW). En PAW er en dedikeret computer, der kun bruges til følsomme konfigurationsopgaver, f.eks. Microsoft 365 konfiguration, der kræver en privilegeret konto. Da denne computer ikke bruges dagligt til internetbrowsing eller mail, er den bedre beskyttet mod internetangreb og trusler.
  
Du kan finde oplysninger om, hvordan du konfigurerer en PAW, under [https://aka.ms/cyberpaw](/security/compass/privileged-access-devices).

Hvis du vil aktivere Azure PIM for dine Azure AD-lejer- og administratorkonti, skal du se [trinnene til konfiguration af PIM](/azure/active-directory/active-directory-privileged-identity-management-configure).

Hvis du vil udvikle en omfattende køreplan for at sikre privilegeret adgang mod cyberangreb, skal du se [Sikring af privilegeret adgang til hybrid- og cloudinstallationer i Azure AD](/azure/active-directory/admin-roles-best-practices).

### <a name="azure-ad-privileged-identity-management"></a>Azure AD-Privileged Identity Management

I stedet for at få tildelt en administratorrolle permanent til dine privilegerede konti kan du bruge Azure AD PIM til at aktivere tildeling efter behov af administratorrollen efter behov.
  
Dine administratorkonti går fra at være permanente administratorer til berettigede administratorer. Administratorrollen er inaktiv, indtil nogen har brug for den. Du fuldfører derefter en aktiveringsproces for at føje administratorrollen til den privilegerede konto i et forudbestemt tidsrum. Når tiden udløber, fjerner PIM administratorrollen fra den privilegerede konto.
  
Brug af PIM og denne proces reducerer betydeligt den tid, dine privilegerede konti er sårbare over for angreb og brug af ondsindede brugere.

PIM fås med Azure Active Directory Premium P2, som følger med Microsoft 365 E5. Du kan også købe individuelle Azure Active Directory Premium P2-licenser til dine administratorkonti.
  
Du kan finde flere oplysninger under:

- [Azure AD-Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
- [Sikring af privilegeret adgang til hybrid- og cloudinstallationer i Azure AD](/azure/active-directory/roles/security-planning)
  

### <a name="privileged-access-management"></a>Privileged Access Management

Privilegeret adgangsstyring aktiveres ved at konfigurere politikker, der angiver just-in-time-adgang for opgavebaserede aktiviteter i din lejer. Det kan hjælpe med at beskytte din organisation mod brud, der kan bruge eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger. Du kan f.eks. konfigurere en politik for privilegeret adgangsstyring, der kræver eksplicit godkendelse for at få adgang til og ændre indstillingerne for organisationspostkasser i din lejer.

I dette trin skal du aktivere privilegeret adgangsstyring i din lejer og konfigurere privilegerede adgangspolitikker, der giver yderligere sikkerhed for opgavebaseret adgang til data og konfigurationsindstillinger for din organisation. Der er tre grundlæggende trin til at komme i gang med privilegeret adgang i din organisation:

- Oprettelse af en godkenders gruppe
- Aktivering af privilegeret adgang
- Oprettelse af godkendelsespolitikker

Privilegeret adgangsstyring gør det muligt for din organisation at arbejde med nul stående rettigheder og levere et forsvarslag mod sikkerhedsrisici, der opstår på grund af sådan stående administrativ adgang. Privilegeret adgang kræver godkendelser til udførelse af en opgave, der har en tilknyttet godkendelsespolitik defineret. Brugere, der skal udføre opgaver, der er inkluderet i godkendelsespolitikken, skal anmode om og tildeles adgangsgodkendelse.

Hvis du vil aktivere privilegeret adgangsstyring, skal du se [Konfigurer privilegeret adgangsstyring](/office365/securitycompliance/privileged-access-management-configuration).

Du kan få flere oplysninger under [Privilegeret adgangsstyring](/office365/securitycompliance/privileged-access-management-overview).

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>SIEM-software (Security Information and Event Management) til Microsoft 365 logføring

SIEM-software, der kører på en server, udfører analyse i realtid af sikkerhedsbeskeder og hændelser, der er oprettet af programmer og netværkshardware. Hvis du vil tillade, at din SIEM-server inkluderer Microsoft 365 sikkerhedsbeskeder og -hændelser i dens analyse- og rapporteringsfunktioner, skal du integrere Azure AD i dit SEIM. Se [Introduktion til Azure Log Integration](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Næste trin

[![Beskyt dine Microsoft 365 brugerkonti](../media/deploy-identity-solution-overview/microsoft-365-secure-sign-in.png)](microsoft-365-secure-sign-in.md)

Fortsæt med [trin 3](microsoft-365-secure-sign-in.md) for at sikre dine brugerkonti.
