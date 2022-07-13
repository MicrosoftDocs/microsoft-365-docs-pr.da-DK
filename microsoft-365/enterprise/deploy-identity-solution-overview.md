---
title: Udrul din identitetsinfrastruktur til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-overview
- zerotrust-solution
ms.custom:
- intro-overview
description: Udrul din identitetsinfrastruktur til Microsoft 365.
ms.openlocfilehash: 7140fc9a34855c39487474f160856bf671666f24
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748423"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>Udrul din identitetsinfrastruktur til Microsoft 365

I Microsoft 365 for enterprise baner en veltilrettelagt og udført identitetsinfrastruktur vejen for stærkere sikkerhed, herunder begrænsning af adgang til dine produktivitetsarbejdsbelastninger og deres data til kun godkendte brugere og enheder. Sikkerhed for identiteter er et nøgleelement i en Nul tillid udrulning, hvor alle forsøg på at få adgang til ressourcer både i det lokale miljø og i cloudmiljøet godkendes og godkendes.

Du kan få oplysninger om identitetsfunktionerne for hver Microsoft 365 for enterprise, rollen som Azure Active Directory (Azure AD), komponenter i det lokale miljø og cloudbaserede komponenter og de mest almindelige godkendelseskonfigurationer på [plakaten Identitetsinfrastruktur](../downloads/m365e-identity-infra.pdf).

[![Plakaten Identitetsinfrastruktur.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Gennemse denne plakat med to sider for hurtigt at få oplysninger om identitetsbegreber og -konfigurationer til Microsoft 365 for enterprise.

Du kan [downloade denne plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) og kan udskrive den i brev-, juridiske eller tabloid-format (11 x 17).

Denne løsning er det første trin til at bygge Udrulningsstakken til Microsoft 365 Nul tillid.

![Microsoft 365 Nul tillid udrulningsstak](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

Du kan få flere oplysninger i [Udrulningsplanen for Microsoft 365 Nul tillid](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>Hvad er der i denne løsning

Denne løsning hjælper dig gennem udrulningen af en identitetsinfrastruktur for din Microsoft 365-lejer for at give dine medarbejdere adgang og beskyttelse mod identitetsbaserede angreb.

![Udrul din identitetsinfrastruktur til Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

Trinnene i denne løsning er:

1. [Bestem din identitetsmodel.](deploy-identity-solution-identity-model.md)
2. [Beskyt dine privilegerede Microsoft 365-konti.](protect-your-global-administrator-accounts.md)
3. [Beskyt dine Microsoft 365-brugerkonti.](microsoft-365-secure-sign-in.md)
4. [Udrul din identitetsmodel.](cloud-only-identities.md)

Denne løsning understøtter nøgleprincipperne i [Nul tillid](https://www.microsoft.com/security/business/zero-trust/):

- **Bekræft eksplicit:** Godkend og godkend altid baseret på alle tilgængelige datapunkter.
- **Brug adgang med færrest rettigheder:** Begræns brugeradgang med Just-In-Time og Just-Enough-Access (JIT/JEA), risikobaserede tilpassede politikker og databeskyttelse.
- **Antag brud:** Minimer eksplosionsradius og segmentadgang. Bekræft kryptering fra slutpunkt til slutpunkt, og brug analyser til at få synlighed, skabe trusselsregistrering og forbedre forsvaret.

I modsætning til almindelig intranetadgang, der har tillid til alt bag en organisations firewall, behandler Nul tillid hvert enkelt logon og adgang, som om det stammer fra et ikke-kontrolleret netværk, uanset om det er bag organisationens firewall eller på internettet. Nul tillid kræver beskyttelse af netværket, infrastrukturen, identiteter, slutpunkter, apps og data.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365-funktioner og -funktioner

Azure AD indeholder en komplet pakke med identitetsstyring og sikkerhedsfunktioner til din Microsoft 365-lejer.

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|[Multifaktorgodkendelse (MFA)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA kræver, at brugerne angiver to former for bekræftelse, f.eks. en brugeradgangskode plus en meddelelse fra Appen Microsoft Authenticator eller et telefonopkald. MFA reducerer i høj grad risikoen for, at stjålne legitimationsoplysninger kan bruges til at få adgang til dit miljø. Microsoft 365 bruger tjenesten Azure AD multifaktorgodkendelse til MFA-baserede logons.|Microsoft 365 E3 eller E5|
|[Betinget adgang](/azure/active-directory/conditional-access/overview)|Azure AD evaluerer betingelserne for brugerens logon og bruger politikker for betinget adgang til at bestemme den tilladte adgang. I denne vejledning viser vi f.eks., hvordan du opretter en politik for betinget adgang for at kræve overholdelse af angivne standarder for enheden for at få adgang til følsomme data. Dette reducerer i høj grad risikoen for, at en hacker med deres egen enhed og stjålne legitimationsoplysninger kan få adgang til dine følsomme data. Den beskytter også følsomme data på enhederne, fordi enhederne skal opfylde specifikke krav til tilstand og sikkerhed.|Microsoft 365 E3 eller E5|
|[Azure AD grupper](/azure/active-directory/fundamentals/active-directory-manage-groups)|Politikker for betinget adgang, enhedshåndtering med Intune og endda tilladelser til filer og websteder i din organisation er afhængige af tildelingen til brugerkonti eller Azure AD grupper. Vi anbefaler, at du opretter Azure AD grupper, der svarer til de beskyttelsesniveauer, du implementerer. For eksempel er dine chefmedarbejdere sandsynligvis højere værdimål for hackere. Det giver derfor mening at føje disse medarbejderes brugerkonti til en Azure AD gruppe og tildele denne gruppe til politikker for betinget adgang og andre politikker, der gennemtvinger et højere beskyttelsesniveau for adgang.|Microsoft 365 E3 eller E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Giver dig mulighed for at registrere potentielle sikkerhedsrisici, der påvirker din organisations identiteter, og konfigurere politikken for automatisk afhjælpning til lav, mellem og høj logonrisiko og brugerrisiko. Denne vejledning er afhængig af denne risikoevaluering for at anvende politikker for betinget adgang til multifaktorgodkendelse. Denne vejledning indeholder også en politik for betinget adgang, der kræver, at brugerne ændrer deres adgangskode, hvis der registreres højrisikoaktivitet for deres konto.|Microsoft 365 E5, Microsoft 365 E3 med tilføjelsesprogrammet E5 Security, EMS E5 eller Azure AD Premium P2-licenser|
|[Selvbetjeningstjenesten til nulstilling af adgangskode (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Tillad, at brugerne nulstiller deres adgangskoder sikkert og uden indgriben fra helpdesk ved at kontrollere flere godkendelsesmetoder, som administratoren kan kontrollere.|Microsoft 365 E3 eller E5|
|[Azure AD adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad)|Registrer og bloker kendte svage adgangskoder og deres varianter og yderligere svage ord, der er specifikke for din organisation. Standardlister over globale forbudte adgangskoder anvendes automatisk på alle brugere i en Azure AD lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugerne ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at gennemtvinge brugen af stærke adgangskoder.|Microsoft 365 E3 eller E5|
|

## <a name="next-steps"></a>Næste trin

Brug disse trin til at installere en identitetsmodel og en godkendelsesinfrastruktur for din Microsoft 365-lejer:

1. [Bestem din cloudidentitetsmodel.](deploy-identity-solution-identity-model.md)
2. [Beskyt dine privilegerede Microsoft 365-konti.](protect-your-global-administrator-accounts.md)
3. [Beskyt dine Microsoft 365-brugerkonti.](microsoft-365-secure-sign-in.md)
4. Udrul din cloudidentitetsmodel: [kun cloud](cloud-only-identities.md) eller [hybrid](prepare-for-directory-synchronization.md).

[![Bestem den identitetsmodel, der skal bruges til din Microsoft 365-lejer](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Yderligere ressourcer til Microsofts cloudidentitet

### <a name="manage"></a>Administrer

Hvis du vil administrere installationen af din Microsoft-cloudidentitet, skal du se:

- [Brugerkonti](manage-microsoft-365-accounts.md)
- [Licenser](assign-licenses-to-user-accounts.md)
- [Adgangskoder](manage-microsoft-365-passwords.md)
- [Grupper](manage-microsoft-365-groups.md)
- [Styring](manage-microsoft-365-identity-governance.md)
- [Katalogsynkronisering](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Sådan gør Microsoft identitet for Microsoft 365

Få mere at vide om, hvordan it-eksperter hos Microsoft [administrerer identiteter og sikker adgang](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>Denne IT Showcase-ressource er kun tilgængelig på engelsk.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Sådan klarede Contoso identitet for Microsoft 365

Du kan se et eksempel på, hvordan en fiktiv, men repræsentativ multinational organisation har udrullet en hybrid identitetsinfrastruktur til Microsoft 365-cloudtjenester, under [Identitet for Contoso Corporation](contoso-identity.md).

<!--

## Plan

To plan for your identity implementation:

- [Understand the different identity models](about-microsoft-365-identity.md)
- [Plan for hybrid identity and directory synchronization](plan-for-directory-synchronization.md)

## Deploy

To deploy your identity implementation:

- [Protect your global administrator accounts](protect-your-global-administrator-accounts.md)
- [Configure and use cloud-only identities](cloud-only-identities.md)
- [Configure and use hybrid identities](prepare-for-directory-synchronization.md)
- [Set up directory synchronization](set-up-directory-synchronization.md)
- If needed, deploy [hybrid identity scenarios](hybrid-solutions.md)

### Identity and device access recommendations

To help ensure a secure and productive workforce, Microsoft provides a set of recommendations for [identity and device access](../security/office-365-security/microsoft-365-policies-configurations.md). For identity, use the recommendations and settings in these articles:

- [Prerequisites](../security/office-365-security/identity-access-prerequisites.md)
- [Common identity and device access policies](../security/office-365-security/identity-access-policies.md)

--> 
