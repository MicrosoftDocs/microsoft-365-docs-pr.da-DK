---
title: Installér din identitetsinfrastruktur til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
- m365initiative-coredeploy
- m365solution-m365-identity
- m365solution-scenario
- m365solution-overview
ms.custom:
- intro-overview
description: Installér din identitetsinfrastruktur til Microsoft 365.
ms.openlocfilehash: 77dbb7c5c38e2ecd8d8ef5ae71044565c2ae6b20
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63597005"
---
# <a name="deploy-your-identity-infrastructure-for-microsoft-365"></a>Installér din identitetsinfrastruktur til Microsoft 365

I Microsoft 365 for enterprise forberedes en velorganeret og eksekveret identitetsinfrastruktur af en stærkere sikkerhed, herunder begrænsning af adgangen til dine produktivitetsmængder og deres data til kun godkendte brugere og enheder. Sikkerhed for identiteter er et vigtigt element i en Zero Trust-installation, hvor alle forsøg på at få adgang til ressourcer både lokalt og i skyen godkendes og godkendes.

Du kan finde oplysninger om identitetsfunktionerne for hver Microsoft 365 til virksomheder, rollen som Azure Active Directory (Azure AD), lokale og skybaserede komponenter og de mest almindelige godkendelseskonfigurationer på plakaten for identitetsinfrastruktur[.](../downloads/m365e-identity-infra.pdf)

[![Plakaten Identitetsinfrastruktur.](../downloads/m365e-identity-infra.png)](../downloads/m365e-identity-infra.pdf)

Gennemse denne tosidede plakat for hurtigt at sætte gang i identitetskoncepter og -konfigurationer til Microsoft 365 til virksomheder.

Du kan [downloade denne plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/m365e-identity-infra.pdf) og udskrive den i letter-, legal- eller tabloid-format (11 x 17).

Denne løsning er det første trin til at udbygge installationsstakken Microsoft 365 Zero Trust.

![Installationsstakken Microsoft 365 Zero Trust](../media/deploy-identity-solution-overview/zero-trust-deployment-stack.png)

Du kan finde flere oplysninger [i Microsoft 365 Zero Trust-installationsplanen](/microsoft-365/security/microsoft-365-zero-trust).

## <a name="whats-in-this-solution"></a>Hvad er der i denne løsning

Denne løsning giver dig adgang til installationen af en identitetsinfrastruktur til din Microsoft 365-lejer, så du giver dine medarbejdere adgang og beskyttelse mod identitetsbaserede angreb.

![Installér din identitetsinfrastruktur til Microsoft 365](../media/deploy-identity-solution-overview/deploy-identity-solution-overview.png)

Trinnene i denne løsning er:

1. [Bestem din identitetsmodel.](deploy-identity-solution-identity-model.md)
2. [Beskyt dine Microsoft 365-konti.](protect-your-global-administrator-accounts.md)
3. [Beskyt dine Microsoft 365-brugerkonti.](microsoft-365-secure-sign-in.md)
4. [Installér din identitetsmodel.](cloud-only-identities.md)

Denne løsning understøtter de centrale principper for [Zero Trust](https://www.microsoft.com/security/business/zero-trust/):

- **Bekræft udtrykkeligt:** Godkend og godkend altid baseret på alle tilgængelige datapunkter.
- **Brug adgang med mindst rettigheder:** Begræns brugeradgang med Just-In-Time og Just-Enough-Access (JIT/JEA), risikobaserede adaptive politikker og databeskyttelse.
- **Antag misligholdelse:** Minimer mængden af radius og segmentadgang. Bekræft kryptering fra ende til anden, og brug analyse til at få synlighed, køre trusselsregistrering og forbedre forsvar.

I modsætning til traditionel intranetadgang, som har tillid til alt bag en organisations firewall, behandler Zero Trust hvert logon og adgang, som om det stammer fra et netværk, der er til at få adgang til, uanset om det er bag organisationens firewall eller på internettet. Nultillid kræver beskyttelse af netværket, infrastrukturen, identiteter, slutpunkter, apps og data.

## <a name="microsoft-365-capabilities-and-features"></a>Microsoft 365 funktioner

Azure AD indeholder en komplet pakke med identitetsadministration og sikkerhedsfunktioner til din Microsoft 365 lejer.

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|[MFA (Multi-Factor Authentication)](/azure/active-directory/authentication/concept-mfa-howitworks)|MFA kræver, at brugerne angiver to former for bekræftelse, f.eks. en brugeradgangskode plus en meddelelse fra Microsoft Authenticator-appen eller et telefonopkald. MFA reducerer kraftigt risikoen for, at stjålet legitimationsoplysninger kan bruges til at få adgang til dit miljø. Microsoft 365 bruger Azure AD Multi-Factor Authentication-tjenesten til MFA-baserede logons.|Microsoft 365 E3 eller E5|
|[Betinget adgang](/azure/active-directory/conditional-access/overview)|Azure AD evaluerer betingelserne for brugerens logon og bruger politikker for betinget adgang til at bestemme den tilladte adgang. I denne vejledning viser vi dig f.eks., hvordan du opretter en Betinget adgang-politik for at kræve enhedsoverholdelse for at få adgang til følsomme data. Dette reducerer risikoen for, at en hacker med sin egen enhed og stjålne legitimationsoplysninger kan få adgang til dine følsomme data. Den beskytter også følsomme data på enhederne, fordi enhederne skal opfylde specifikke krav til tilstand og sikkerhed.|Microsoft 365 E3 eller E5|
|[Azure AD-grupper](/azure/active-directory/fundamentals/active-directory-manage-groups)|Politikker for betinget adgang, enhedshåndtering med Intune og endda tilladelser til filer og websteder i organisationen afhænger af tildeling til brugerkonti eller Azure AD-grupper. Vi anbefaler, at du opretter Azure AD-grupper, der svarer til de niveauer af beskyttelse, du implementerer. Eksempelvis er dine ledere sandsynligvis bedre mål for hackere. Derfor giver det mening at føje brugerkontiene for disse medarbejdere til en Azure AD-gruppe og tildele denne gruppe til politikker for betinget adgang og andre politikker, der gennemtvinger et højere niveau af beskyttelse af adgang.|Microsoft 365 E3 eller E5|
|[Azure AD Identity Protection](/azure/active-directory/identity-protection/overview)|Gør det muligt at registrere potentielle sårbarheder, der påvirker organisationens identiteter, og konfigurere automatiseret afhjælpningspolitik til lav, mellem og høj logon-risiko og brugerrisici. Denne vejledning afhænger af denne risikoevaluering for at anvende betingede Access-politikker til multifaktorgodkendelse. Denne vejledning indeholder også en politik for betinget adgang, der kræver, at brugerne ændrer deres adgangskode, hvis der registreres aktivitet med høj risiko for deres konto.|Microsoft 365 E5, Microsoft 365 E3 med E5 Security-tilføjelsesprogrammet, EMS E5 eller Azure AD Premium P2-licenser|
|[Selvbetjeningstjenesten til nulstilling af adgangskode (SSPR)](/azure/active-directory/authentication/concept-sspr-howitworks)|Giv dine brugere mulighed for at nulstille deres adgangskoder sikkert og uden helpdesk-handling ved at levere bekræftelse af flere godkendelsesmetoder, som administratoren kan styre.|Microsoft 365 E3 eller E5|
|[Azure AD-adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad)|Find og bloker kendte svage adgangskoder og deres varianter og yderligere svage ord, der er specifikke for din organisation. Standard globale lister over forbudte adgangskoder anvendes automatisk for alle brugere i en Azure AD-lejer. Du kan definere yderligere poster på en brugerdefineret liste over forbudte adgangskoder. Når brugere ændrer eller nulstiller deres adgangskoder, kontrolleres disse lister over forbudte adgangskoder for at håndhæve brugen af stærke adgangskoder.|Microsoft 365 E3 eller E5|
|

## <a name="next-steps"></a>Næste trin

Brug disse trin til at installere en identitetsmodel og godkendelsesinfrastruktur for din Microsoft 365 lejer:

1. [Bestem din skyidentitetsmodel.](deploy-identity-solution-identity-model.md)
2. [Beskyt dine Microsoft 365-konti.](protect-your-global-administrator-accounts.md)
3. [Beskyt dine Microsoft 365-brugerkonti.](microsoft-365-secure-sign-in.md)
4. Installér din skyidentitetsmodel: [kun i skyen](cloud-only-identities.md) eller [hybrid](prepare-for-directory-synchronization.md).

[![Find frem til den identitetsmodel, der skal bruges til din Microsoft 365 lejer](../media/deploy-identity-solution-overview/identity-solution-identity-model.png)](deploy-identity-solution-identity-model.md)
  
## <a name="additional-microsoft-cloud-identity-resources"></a>Flere Microsoft-skyidentitetsressourcer

### <a name="manage"></a>Administrer

Hvis du vil administrere din Microsoft-skyidentitetsinstallation, skal du se:

- [Brugerkonti](manage-microsoft-365-accounts.md)
- [Licenser](assign-licenses-to-user-accounts.md)
- [Adgangskoder](manage-microsoft-365-passwords.md)
- [Grupper](manage-microsoft-365-groups.md)
- [Styring](manage-microsoft-365-identity-governance.md)
- [Katalogsynkronisering](view-directory-synchronization-status.md)

### <a name="how-microsoft-does-identity-for-microsoft-365"></a>Sådan gør Microsoft identitet for Microsoft 365

Få mere at vide om, hvordan [it-eksperter hos Microsoft administrerer identiteter og sikker adgang](https://www.microsoft.com/en-us/itshowcase/managing-user-identities-and-secure-access-at-microsoft).

>[!Note]
>Denne IT Showcase-ressource er kun tilgængelig på engelsk.
>

### <a name="how-contoso-did-identity-for-microsoft-365"></a>Sådan gjorde Contoso identitet for Microsoft 365

Hvis du vil se et eksempel på, hvordan en fiktiv men repræsentativ multinational organisation har udviklet en hybrid identitetsinfrastruktur til Microsoft 365-skytjenester, skal du se [Identity for Contoso Corporation](contoso-identity.md).

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
