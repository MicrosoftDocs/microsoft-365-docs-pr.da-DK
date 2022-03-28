---
title: Trin 3. Beskyt identiteter
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: ransomware, ransomware drevet af mennesker, ransomware drevet af mennesker, HumOR, extortionsangreb, ransomware-angreb, kryptering, cryptovirologi, nultillids
description: Brug sikre logons og betinget adgang til at beskytte dine Microsoft 365 mod ransomware-angreb.
ms.openlocfilehash: 548e0649d7180ef39f693049210a91c1e0dce312
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596889"
---
# <a name="step-3-protect-identities"></a>Trin 3. Beskyt identiteter

Brug følgende afsnit for at beskytte din organisation mod kompromis med legitimationsoplysninger, hvilket typisk er første trin i en større ransomware-angreb.

## <a name="increase-sign-in-security"></a>Øg sikkerheden for logon

Brug [godkendelse uden adgangskode](/azure/active-directory/authentication/howto-authentication-passwordless-deployment) til brugerkonti i Azure Active Directory (Azure AD).

Under overgangen til godkendelse uden adgangskode skal du bruge disse bedste fremgangsmåder for brugerkonti, der stadig autentifikation af adgangskode:

- Bloker kendte svage og brugerdefinerede adgangskoder [med Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad).
- Udvid blokering af kendte svage og brugerdefinerede adgangskoder til din lokale [Active Directory-domæneservices (AD DS) med Azure AD Password Protection](/azure/active-directory/authentication/concept-password-ban-bad-on-premises).
- Giv dine brugere mulighed for at ændre deres egne adgangskoder [med SSPR (Self-Service Password Reset).](/azure/active-directory/authentication/concept-sspr-howitworks)

Dernæst skal du implementere [politikkerne Fælles identitet og Enhedsadgang](/microsoft-365/security/office-365-security/identity-access-policies). Disse politikker giver højere sikkerhed for adgang til Microsoft 365 skytjenester. 

Disse politikker omfatter følgende for bruger logons:

- Krav om multifaktorgodkendelse (MFA) for [prioritetskonti](/microsoft-365/admin/setup/priority-accounts) (straks) og med tiden alle brugerkonti.
- Krav om logon med høj risiko for at bruge MFA.
- Kræver, at brugere med høj risiko-logons ændrer deres adgangskoder.

## <a name="prevent-privilege-escalation"></a>Undgå eskalering af rettigheder

Brug disse bedste fremgangsmåder:

- Implementer princippet om [mindste rettigheder](/windows-server/identity/ad-ds/plan/security-best-practices/implementing-least-privilege-administrative-models) og brug adgangskodebeskyttelse som beskrevet i Forøg [sikkerheden for de](#increase-sign-in-security) brugerkonti, der stadig bruger adgangskoder til deres logon. 
- Undgå at bruge tjenestekonti på administratorniveau på hele domænet. 
- Begræns lokale administrative rettigheder for at begrænse installation af rat'er (Remote Access trojanske) og andre uønskede programmer.
- Brug betinget adgang i Azure AD til eksplicit at validere tillid til brugere og arbejdsstationer, før du tillader adgang til administrative portaler. Se [dette eksempel](/azure/active-directory/conditional-access/howto-conditional-access-policy-azure-management) for Azure-portalen.
- Aktivér lokal administration af adgangskode til administratorer.
- Afgør, hvor konti med de højst privilegerede konti logger på og bruger legitimationsoplysninger. Konti med de meget privilegerede rettigheder bør ikke findes på arbejdsstationer.
- Deaktiver lokal lagring af adgangskoder og legitimationsoplysninger.

## <a name="impact-on-users-and-change-management"></a>Indvirkning på brugere og administration af ændringer

Du skal gøre brugerne i organisationen opmærksom på følgende:

- De nye krav til stærkere adgangskoder.
- Ændringerne i logonprocesser, f.eks. den nødvendige brug af MFA og registrering af den sekundære MFA-godkendelsesmetode.
- Brug af adgangskodevedligeholdelse med SSPR. Det kan f.eks. være, at der ikke længere skal ringes op til helpdesk om nulstilling af adgangskode.
- Når du bliver bedt om at kræve MFA eller en adgangskodeændring for logons, der vurderes at være risikabelt.

## <a name="resulting-configuration"></a>Resulterende konfiguration

Her er beskyttelse mod ransomware for din lejer for trin 1-3.

![Beskyttelse mod ransomware for din Microsoft 365 lejer efter trin 3](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step3.png)

## <a name="next-step"></a>Næste trin

[![Trin 4 for ransomware-beskyttelse med Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step4.png)](ransomware-protection-microsoft-365-devices.md)

Fortsæt med [trin 4](ransomware-protection-microsoft-365-devices.md) for at beskytte enheder (slutpunkter) i din Microsoft 365 lejer. 
