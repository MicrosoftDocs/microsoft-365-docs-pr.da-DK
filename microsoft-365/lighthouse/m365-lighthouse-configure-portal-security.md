---
title: Konfigurere Microsoft 365 Lighthouse-portalens sikkerhed
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du konfigurerer portalsikkerhed.
ms.openlocfilehash: 532ce9d6e90ea4d502c6898a105702d525f05a1b
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64632683"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Konfigurere Microsoft 365 Lighthouse-portalens sikkerhed

Beskyttelse af adgang til kundedata, når en administreret tjenesteudbyder har uddelegeret adgangstilladelser til lejerne, er en cybersikkerhedsprioritet. Microsoft 365 Lighthouse leveres med både nødvendige og valgfrie funktioner, der kan hjælpe dig med at konfigurere sikkerhed på Lighthouse-portalen. Du skal konfigurere bestemte roller med multifaktorgodkendelse aktiveret, før du kan få adgang til Lighthouse. Du kan også konfigurere Azure AD Privileged Identity Management (PIM) og Betinget adgang.

## <a name="set-up-multifactor-authentication-mfa"></a>Konfigurer multifaktorgodkendelse (MFA)

Som nævnt i [blogindlægget Din Pa$$word er ligegyldig](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Din adgangskode er ligegyldig, men det gør MFA. Baseret på vores undersøgelser er din konto mere end 99,9 % mindre tilbøjelig til at blive kompromitteret, hvis du bruger MFA."

Når brugere første gang får adgang til Lighthouse, bliver de bedt om at konfigurere MFA, hvis deres Microsoft 365-konto ikke allerede har konfigureret den. Brugerne kan ikke få adgang til Lighthouse, før det nødvendige trin til konfiguration af MFA er fuldført. Hvis du vil have mere at vide om godkendelsesmetoder, [skal Microsoft 365 konfigurere dit logon til multifaktorgodkendelse](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Konfigurere rollebaseret adgangskontrol

Rollebaseret adgangskontrol giver adgang til ressourcer eller oplysninger baseret på brugerroller. Adgang til kundelejerdata og indstillinger i Lighthouse er begrænset til bestemte roller fra Cloud Solution Provider (CSP)-programmet. Hvis du vil konfigurere RBAC-roller i Lighthouse, anbefaler vi, at du bruger GDAP (Granular Delegated Admin Privileges) til at implementere granulartildelinger for brugere. Delegerede administratorrettigheder (DAP) er stadig påkrævet, for at lejeren kan komme i gang, men kun GDAP-kunder vil snart kunne onboarde uden at være afhængige af DAP. GDAP-tilladelser har forrang, når DAP og GDAP anvendes for en kunde. 

Hvis du vil konfigurere en GDAP-relation, [skal du se Få detaljerede administratortilladelser til at administrere en kundes tjeneste](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Hvis du vil have mere at vide om, hvilke roller vi anbefaler, skal [du se Oversigt over tilladelser i Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).

MSP-teknikere kan også få adgang til Lighthouse ved hjælp af administratoragent- eller Helpdesk-agentroller via Delegerede administratorrettigheder (DAP).

For ikke-kundelejerrelaterede handlinger i Lighthouse (f.eks. onboarding, deaktivering/genaktivering af kunden, administration af mærker, gennemgang af logfiler) skal MSP-teknikere have en tildelt rolle i partnerlejeren. Se [Oversigt over tilladelser i Microsoft 365 Lighthouse, hvis](m365-lighthouse-overview-of-permissions.md) du vil have mere at vide om partnerlejerroller.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Konfigurer Azure AD Privileged Identity Management (PIM)

MSP'er kan minimere antallet af personer, der har adgang til rolle med høj rettighed, for at sikre oplysninger eller ressourcer ved hjælp af PIM. PIM reducerer risikoen for, at en ondsindet person får adgang til ressourcer eller autoriserede brugere ved et tilfælde påvirker en følsom ressource. MSP'er kan også give brugere just-in-time høj rettighedsroller adgang til ressourcer, foretage brede ændringer og overvåge, hvad de angivne brugere gør med deres adgangsprivilegerede adgang. 

> [!NOTE]
> Brug af Azure AD PIM kræver en Azure AD Premium P2-licens i partnerlejeren.

Følgende trin giver partnerlejerbrugere timebaserede højere rettighedsroller ved hjælp af PIM:

1. Opret en gruppe, der kan tildeles rollen, som beskrevet i artiklen [Opret en gruppe til tildeling af roller i Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. Gå til [Azure AD –](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups) Alle grupper, og tilføj den nye gruppe som medlem af en sikkerhedsgruppe for at få roller med høj rettighed (f.eks. sikkerhedsgruppen Administratoragenter for DAP eller en tilsvarende tilsvarende sikkerhedsgruppe for GDAP-roller).

3. Konfigurer privilegeret adgang til den nye gruppe som beskrevet i artiklen Tildel berettigede [ejere og medlemmer for grupper med adgangspriviligerede rettigheder](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Du kan få mere at vide om PIM [under Hvad er Privileged Identity Management?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Konfigurer risikobaseret betinget adgang til Azure AD

MSP'er kan bruge risikobaseret betinget adgang for at sikre, at deres medarbejdere bekræfter deres identitet ved hjælp af MFA og ved at ændre deres adgangskode, når de registreres som en risikabel bruger (med lækerede legitimationsoplysninger eller pr. Azure AD-trusselsintelligens). Brugere skal også logge på fra en velkendt placering eller registreret enhed, når de registreres som et risikabelt logon. Andre risikabel adfærd omfatter at logge på fra en ondsindet eller anonym IP-adresse eller fra en atypisk eller umulig rejseplacering, ved hjælp af et unormalt token, ved hjælp af en adgangskode fra en adgangskodeplacering eller ved at udvise anden usædvanlig logonfunktion. Afhængigt af en brugers risikoniveau kan MSP'er også vælge at blokere adgang ved logon. Du kan få mere at vide om risici [under Hvad er risiko?](/azure/active-directory/identity-protection/concept-identity-protection-risks) 

> [!NOTE]
> Betinget adgang kræver en Azure AD Premium P2-licens i partnerlejeren. Hvis du vil konfigurere Betinget adgang, skal [du se Konfigurer Azure Active Directory Betinget adgang](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>Relateret indhold

[Tilladelser til nulstilling af adgangskode](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (artikel)\
[Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artikel)\
[Oversigt over Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (artikel)\
[Tilmeld dig Microsoft 365 Fyrtårn](m365-lighthouse-sign-up.md) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)