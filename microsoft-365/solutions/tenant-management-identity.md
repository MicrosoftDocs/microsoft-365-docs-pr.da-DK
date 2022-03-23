---
title: Trin 3. Identitet for din Microsoft 365 for virksomhedslejere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Installér den korrekte identitetsmodel for Microsoft 365 lejere, og gennemtving stærke bruger logins.
ms.openlocfilehash: cb57b62f18afcd669b3dd84c25096e5dd72b25d0
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63591940"
---
# <a name="step-3-identity-for-your-microsoft-365-for-enterprise-tenants"></a>Trin 3. Identitet for din Microsoft 365 for virksomhedslejere

Din Microsoft 365 lejer omfatter Azure Active Directory (Azure AD) lejer til at administrere identiteter og godkendelse for logons. Det er vigtigt at få konfigureret din identitetsinfrastruktur korrekt Microsoft 365 administration af brugeradgang og tilladelser for organisationen.

## <a name="cloud-only-vs-hybrid"></a>Kun i skyen kontra hybrid

Her er de to typer identitetsmodeller og deres bedste tilpasning og fordele.


| Model | Beskrivelse | Sådan Microsoft 365 brugerlegitimationsoplysninger | Bedst til | Største fordel |
|:-------|:-----|:-----|:-----|:-----|
| Kun i skyen | Brugerkonto findes kun i Azure AD-lejeren for din Microsoft 365 lejer. | Azure AD-lejeren for din Microsoft 365 udfører godkendelsen med skyidentitetskontoen. | Organisationer, der ikke har eller har brug for et lokalt Active Directory. | Nem at bruge. Der kræves ingen ekstra katalogværktøjer eller servere. |
| Hybrid |  Brugerkonto findes i din lokale Active Directory-domæneservices (AD DS), og der er også en kopi i Azure AD-lejeren for din Microsoft 365 lejer. Azure AD Forbind på en lokal server for at synkronisere AD DS med din Azure AD-lejer. Brugerkontoen i Azure AD kan også indeholde en ændret version af den allerede AD DS adgangskoden til brugerkontoen. | Azure AD-lejeren for din Microsoft 365 håndterer godkendelsesprocessen eller omdirigerer brugeren til en anden identitetsudbyder. | Organisationer, der AD DS en anden identitetsudbyder. | Brugere kan bruge de samme legitimationsoplysninger, når de får adgang til lokale eller skybaserede ressourcer. |
||||||

Her er de grundlæggende komponenter i en identitet, der kun findes i skyen.

![Grundlæggende komponenter i kun skyidentitet.](../media/about-microsoft-365-identity/cloud-only-identity.png)

I denne illustration logger lokale og eksterne brugere på med konti i Azure AD-lejeren for deres Microsoft 365 lejer.

Her er de grundlæggende komponenter i hybrididentitet.

![Grundlæggende komponenter i hybrididentitet.](../media/about-microsoft-365-identity/hybrid-identity.png)

I denne illustration logger lokale og eksterne brugere på deres Microsoft 365-lejer med konti i Azure AD-lejeren, der er blevet kopieret fra deres lokale AD DS.

## <a name="synchronizing-your-on-premises-ad-ds"></a>Synkronisering af din lokale AD DS

Afhængigt af virksomhedens behov og tekniske krav er hybrididentitetsmodellen og katalogsynkronisering det mest almindelige valg for virksomhedskunder, der Microsoft 365. Katalogsynkronisering gør det muligt at administrere identiteter i din AD DS, og alle opdateringer af brugerkonti, grupper og kontakter synkroniseres med Azure AD-lejeren for din Microsoft 365-lejer.

> [!NOTE]
> Når AD DS brugerkonti synkroniseres for første gang, tildeles de ikke automatisk en Microsoft 365-licens og kan ikke få adgang til Microsoft 365-tjenester, f.eks. mail. Du skal først tildele dem en brugsplacering. Tildel derefter en licens til disse brugerkonti enten enkeltvis eller dynamisk via gruppemedlemskab.

Her er de to typer godkendelse, når du bruger hybrididentitetsmodellen.

| Godkendelsestype | Beskrivelse |
|:-------|:-----|
| Administreret godkendelse | Azure AD håndterer godkendelsesprocessen ved hjælp af en lokalt gemt hashedsversion af adgangskoden eller sender legitimationsoplysningerne til en lokal softwareagent, der skal godkendes af den lokale AD DS. <br> <br>  Der findes to typer administreret godkendelse: Synkronisering af adgangskodehash (PHS) og pass-through-godkendelse (PTA). Med PHS udfører Azure AD selve godkendelsen. Med PTA har Azure AD AD DS at udføre godkendelsen. |
| Federated Authentication | Azure AD omdirigerer klientcomputeren, der anmoder om godkendelse, til en anden identitetsudbyder. |
|  |  |

Se [vælge den rigtige godkendelsesmetode for at](/azure/active-directory/hybrid/choose-ad-authn) få mere at vide.

## <a name="enforcing-strong-sign-ins"></a>Gennemtvinge stærke logons

For at øge sikkerheden for bruger-logons skal du bruge funktionerne og egenskaberne i følgende tabel.

| Funktion | Beskrivelse | Flere oplysninger | Licenskrav |
|:-------|:-----|:-----|:-----|:-----|
| Windows Hello for Business | Erstatter adgangskoder med stærk to faktor-godkendelse, når du logger på en Windows enhed. De to faktorer er en ny type brugerlegitimationsoplysninger, der er bundet til en enhed og en biometrisk eller pinkode. | [Windows Hello for Business – oversigt](/windows/security/identity-protection/hello-for-business/hello-overview) | Microsoft 365 E3 eller E5 |
| Azure AD Password Protection | Registrerer og blokerer kendte svage adgangskoder og deres varianter og kan også blokere yderligere svage ord, der er specifikke for din organisation. | [Konfigurere Azure AD-adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad) | Microsoft 365 E3 eller E5 |
| Brug multifaktorgodkendelse (MFA) | MFA kræver, at brugernes logons bliver underlagt en anden bekræftelse ud over adgangskoden til brugerkontoen, f.eks. bekræftelse med en smartphoneapp eller en sms-besked, der sendes til en smartphone. Se [denne video](https://support.microsoft.com/office/set-up-multi-factor-authentication-in-microsoft-365-business-a32541df-079c-420d-9395-9d59354f7225) for at få vejledning i, hvordan brugerne konfigurerer MFA. | [MFA til Microsoft 365 til virksomheder](../enterprise/microsoft-365-secure-sign-in.md#mfa) | Microsoft 365 E3 eller E5 |
| Konfigurationer for identitets- og enhedsadgang | Indstillinger og politikker, der består af anbefalede nødvendige funktioner og deres indstillinger kombineret med politikkerne Betinget adgang, Intune og Azure AD Identity Protection, der bestemmer, om en given anmodning om adgang skal tildeles og under hvilke betingelser.  | [Konfigurationer for identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) | Microsoft 365 E3 eller E5 |
| Azure AD Identity Protection | Beskyt dig mod kompromis med legitimationsoplysninger, hvor en hacker bestemmer en brugers kontonavn og adgangskode for at få adgang til en organisations skytjenester og data. | [Azure AD Identity Protection](/azure/active-directory/active-directory-identityprotection) | Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet Identity & Threat Protection |
|  |  |  |



## <a name="results-of-step-3"></a>Resultater af trin 3

For identiteten af Microsoft 365 lejer har du fastlagt:

- Hvilken identitetsmodel, der skal bruges.
- Sådan gennemtvinger du stærk bruger- og enhedsadgang.

Her er et eksempel på en lejer med de nye hybrididentitetselementer fremhævet.

![Eksempel på hybrididentitet for en lejer.](../media/tenant-management-overview/tenant-management-tenant-build-step3.png)

I denne illustration har lejeren:

- Et AD DS, der synkroniseres med Azure AD-lejeren ved hjælp af en katalogsynkroniseringsserver og Azure AD Forbind.
- En kopi af AD DS-brugerkonti og andre objekter fra AD DS skov.
- Et sæt af betingede adgangspolitikker til at gennemtvinge sikre brugeradgang, der er baseret på brugerkontoen.

## <a name="ongoing-maintenance-for-identity"></a>Løbende vedligeholdelse af identitet

Du kan løbende få brug for at:

- Tilføj eller rediger brugerkonti og grupper. Kun i skyen bevarer du dine skybaserede brugere og grupper med Azure AD-værktøjer som f.eks. Microsoft 365 Administration eller PowerShell. For hybrididentitet vedligeholder du dine lokale brugere og grupper med AD DS værktøjer.
- Tilføj eller rediger konfigurationen af din identitet og enhedsadgang for at gennemtvinge sikkerhedskrav til logon.

## <a name="next-step"></a>Næste trin

[![Trin 4. Overfør dine lokale Office servere og data.](../media/tenant-management-overview/tenant-management-step-grid-migration.png)](tenant-management-migration.md)

Fortsæt med [overførslen](tenant-management-migration.md) for at overføre dine lokale servere Office deres data for at Microsoft 365.