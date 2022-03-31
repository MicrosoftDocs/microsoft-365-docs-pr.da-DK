---
title: Trin 2. Beskyt dine Microsoft 365-konti
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
ms.openlocfilehash: ff20b8dcaf203771b0c3a935b67e83eb291ec75e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63601634"
---
# <a name="step-2-protect-your-microsoft-365-privileged-accounts"></a>Trin 2. Beskyt dine Microsoft 365-konti

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Sikkerhedsbdrag af en Microsoft 365-lejer, herunder indsamling af oplysninger og phishing-angreb, udføres typisk ved at der gås på kompromis med legitimationsoplysninger for en Microsoft 365 privilegeret konto. Sikkerhed i skyen er et partnerskab mellem dig og Microsoft:
  
- Microsofts skytjenester er bygget på et grundlag af tillid og sikkerhed. Microsoft leverer sikkerhedskontrolelementer og -funktioner, der kan hjælpe dig med at beskytte dine data og programmer.
    
- Du ejer dine data og identiteter og har ansvaret for at beskytte dem, sikkerheden for dine lokale ressourcer og sikkerheden for de skykomponenter, du styrer.
    
Microsoft leverer funktioner, der beskytter din organisation, men de er kun effektive, hvis du bruger dem. Hvis du ikke bruger dem, kan du være sårbar over for angreb. For at beskytte dine privilegerede konti er Microsoft her for at hjælpe dig med detaljerede instruktioner til at:
  
1. Opret dedikerede, privilegerede, skybaserede konti, og brug dem kun, når det er nødvendigt.
    
2. Konfigurer multifaktorgodkendelse (MFA) for dine dedikerede Microsoft 365-konti, og brug den stærkeste form for sekundær godkendelse.

3. Beskyt privilegerede konti med anbefalinger om nultillidsidentitet og enhedsadgang.

## <a name="1-create-dedicated-privileged-cloud-based-user-accounts-and-use-them-only-when-necessary"></a>1. Opret dedikerede, privilegerede, skybaserede brugerkonti, og brug dem kun, når det er nødvendigt

I stedet for at bruge almindelige brugerkonti, der har fået tildelt administratorroller, kan du oprette dedikerede brugerkonti, der har administratorrollerne i Azure AD. 

Fra nu af logger du kun på med de dedikerede konti for at udføre opgaver, der kræver administratorrettigheder. Alle andre Microsoft 365 administration skal udføres ved at tildele andre administrationsroller til brugerkonti.
  
> [!NOTE]
> Dette kræver yderligere trin for at logge af din almindelige brugerkonto og logge på med en dedikeret administratorkonto. Men dette skal kun udføres lejlighedsvist i forbindelse med administratorhandlinger. Overvej, at genoprettelse af Microsoft 365 efter brud på administratorkontoens sikkerhed kræver mange flere trin.

Du skal også oprette [adgangskonti til nødstilfælde](/azure/active-directory/roles/security-emergency-access) for at forhindre, at de ved en fejl bliver låst ude fra Azure AD.

Du kan yderligere beskytte dine privilegerede konti med Azure AD Privileged Identity Management (PIM) til on-demand, just-in-time tildeling af administratorroller. 
 
## <a name="2-configure-multi-factor-authentication-for-your-dedicated-microsoft-365-privileged-accounts"></a>2. Konfigurer multifaktorgodkendelse for dine dedikerede Microsoft 365 privilegerede konti

Multifaktorgodkendelse (MFA) kræver yderligere oplysninger ud over kontonavn og adgangskode. Microsoft 365 understøtter disse yderligere bekræftelsesmetoder:
  
- Den Microsoft Authenticator app
- Et telefonopkald
- En tilfældigt genereret bekræftelseskode sendt via en SMS-besked
- Et chipkort (virtuelt eller fysisk) (kræver federated authentication)
- En biometrisk enhed
- Oauth-token
- 
    
>[!Note]
>For organisationer, der skal overholde NIST-standarder (National Institute of Standards and Technology), begrænses brugen af telefonopkald eller sms-baserede yderligere bekræftelsesmetoder. Klik [her](https://pages.nist.gov/800-63-FAQ/#q-b01) for at få flere oplysninger.
>

Hvis du er en lille virksomhed, der bruger brugerkonti, der kun er gemt i skyen (kun i skyen for identitetsmodellen), skal du konfigurere MFA til at konfigurere [MFA](/office365/admin/security-and-compliance/set-up-multi-factor-authentication) ved hjælp af et telefonopkald eller en SMS-bekræftelseskode sendt til en smartphone for hver dedikeret privilegeret konto.
    
Hvis du er en større organisation, der bruger en Microsoft 365 hybrididentitetsmodel, har du flere bekræftelsesmuligheder. Hvis du allerede har sikkerhedsinfrastrukturen på plads til en stærkere sekundær godkendelsesmetode, skal du konfigurere [MFA](../admin/security-and-compliance/set-up-multi-factor-authentication.md) og konfigurere hver dedikeret privilegeret konto for den relevante bekræftelsesmetode.
  
Hvis sikkerhedsinfrastrukturen til den ønskede stærkere godkendelsesmetode ikke er på plads og fungerer for Microsoft 365 MFA, anbefaler vi kraftigt, at du konfigurerer dedikerede privilegerede konti med MFA ved hjælp af Microsoft Authenticator-appen, et telefonopkald eller en SMS-bekræftelseskode sendt til en smartphone for dine privilegerede konti som en midlertidig sikkerhedsforanstaltning. Lad ikke dine dedikerede privilegerede konti være uden yderligere beskyttelse leveret af MFA.
  
Du kan finde flere oplysninger [under MFA for Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md).
  
## <a name="3-protect-administrator-accounts-with-zero-trust-identity-and-device-access-recommendations"></a>3. Beskyt administratorkonti med nultillidsidentitet og anbefalinger for enhedsadgang

For at sikre en sikker og produktiv arbejdsstyrke leverer Microsoft en række anbefalinger til [identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md). For identitet skal du bruge anbefalingerne og indstillingerne i disse artikler:

- [Forudsætninger](../security/office-365-security/identity-access-prerequisites.md)
- [Fælles identitets- og enhedsadgangspolitikker](../security/office-365-security/identity-access-policies.md)

## <a name="additional-protections-for-enterprise-organizations"></a>Flere beskyttelser til virksomhedsorganisationer

Brug disse yderligere metoder til at sikre, at din privilegerede konto, og den konfiguration, du udfører ved hjælp af den, er så sikker som muligt.
  
### <a name="privileged-access-workstation"></a>Arbejdsstation med særlige rettigheder

For at sikre at udførelse af opgaver med de højt privilegerede opgaver er så sikker som muligt, skal du bruge en privilegeret adgangsstation (AFSER). En AFSE er en dedikeret computer, der kun bruges til følsomme konfigurationsopgaver, f.eks. Microsoft 365 konfiguration, der kræver en konto med rettigheder. Da denne computer ikke bruges dagligt til internetbrowsing eller mail, er den bedre beskyttet mod internetangreb og trusler.
  
Du kan finde en vejledning i, hvordan du konfigurerer en AFSÆT, under [https://aka.ms/cyberpaw](/security/compass/privileged-access-devices).

Hvis du vil aktivere Azure PIM for din Azure AD-lejer og administratorkonti, skal du [se trinnene til konfiguration af PIM](/azure/active-directory/active-directory-privileged-identity-management-configure).

Hvis du vil udarbejde en omfattende oversigt over beskyttelse af privilegeret adgang mod cyberangreb, skal du se Sikring af privilegeret adgang [til hybrid- og skyinstallationer i Azure AD](/azure/active-directory/admin-roles-best-practices).

### <a name="azure-ad-privileged-identity-management"></a>Azure AD-Privileged Identity Management

I stedet for at dine privilegerede konti skal tildeles en administratorrolle permanent, kan du bruge Azure AD PIM til at aktivere tidsbaseret tildeling af administratorrollen efter behov, når der er behov for det.
  
Dine administratorkonti går fra at være permanente administratorer til berettigede administratorer. Administratorrollen er inaktiv, indtil nogen har brug for den. Du skal derefter gennemføre en aktiveringsproces for at føje administratorrollen til den privilegerede konto i et foruddefineret tidsrum. Når tiden udløber, fjerner PIM administratorrollen fra den privilegerede konto.
  
Når du bruger PIM og denne proces, reduceres den mængde tid, dine privilegerede konti er sårbar over for angreb og brug af ondsindede brugere.

PIM fås med Azure Active Directory Premium P2, som er inkluderet i Microsoft 365 E5. Alternativt kan du købe individuelle Azure Active Directory Premium P2-licenser til dine administratorkonti.
  
Du kan finde flere oplysninger under:

- [Azure AD Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).
- [Sikring af privilegeret adgang til hybrid- og skyinstallationer i Azure AD](/azure/active-directory/roles/security-planning)
  

### <a name="privileged-access-management"></a>Adgangsstyring med rettigheder

Administration af adgang med rettigheder aktiveres ved at konfigurere politikker, der angiver tidsbaseret adgang for opgavebaserede aktiviteter i din lejer. Det kan hjælpe med at beskytte din organisation mod brud, der kan bruge eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger. Du kan f.eks. konfigurere en politik for adgangsstyring med rettigheder, der kræver udtrykkelig godkendelse for at få adgang til og ændre indstillingerne for organisationens postkasse i din lejer.

I dette trin skal du aktivere administration af adgang med rettigheder i din lejer og konfigurere politikker for privilegeret adgang, som giver ekstra sikkerhed for opgavebaseret adgang til data og konfigurationsindstillinger for organisationen. Der er tre grundlæggende trin til at komme i gang med privilegeret adgang i din organisation:

- Oprette en godkenders gruppe
- Aktivering af privilegeret adgang
- Oprettelse af godkendelsespolitikker

Med rettighedsadministration af adgang kan din organisation anvende stående rettigheder uden stående rettigheder og levere et lag af forsvar mod sårbarheder, der opstår på grund af en sådan stående administrativ adgang. Privilegeret adgang kræver godkendelser for at udføre en opgave, der har defineret en tilknyttet godkendelsespolitik. Brugere, der skal udføre opgaver, der er inkluderet i godkendelsespolitikken, skal anmode om og få tildelt adgangsgodkendelse.

Hvis du vil aktivere adgangsstyring med adgangsrettigheder, skal [du se Konfigurer adgangsstyring med rettigheder](/office365/securitycompliance/privileged-access-management-configuration).

Du kan finde flere oplysninger under [Administration af adgangsrettigheder](/office365/securitycompliance/privileged-access-management-overview).

### <a name="security-information-and-event-management-siem-software-for-microsoft-365-logging"></a>Sikkerhedsoplysninger og begivenhedsstyringssoftware (SIEM) til Microsoft 365 logføring

SIEM-software, der køres på en server, udfører realtidsanalyse af sikkerhedsadvarsler og hændelser, der er oprettet af programmer og netværkshardware. Hvis du vil gøre det muligt for din SIEM-server at Microsoft 365 sikkerhedsadvarsler og hændelser i dens analyse- og rapporteringsfunktioner, skal du integrere Azure AD i seim. Se [Introduktion til integration af Azure-log](/azure/security/security-azure-log-integration-overview).

## <a name="next-step"></a>Næste trin

[![Beskyt dine Microsoft 365-brugerkonti](../media/deploy-identity-solution-overview/microsoft-365-secure-sign-in.png)](microsoft-365-secure-sign-in.md)

Fortsæt med [trin 3 for](microsoft-365-secure-sign-in.md) at sikre dine brugerkonti.
