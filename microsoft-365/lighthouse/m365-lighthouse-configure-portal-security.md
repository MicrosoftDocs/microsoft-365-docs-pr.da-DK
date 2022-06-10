---
title: Konfigurer sikkerhed i Microsoft 365 Lighthouse Portal
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: vivkuma
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
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du konfigurerer portalsikkerhed.
ms.openlocfilehash: 5033787f314036f345a00b7f9632851317ed05f0
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66013568"
---
# <a name="configure-microsoft-365-lighthouse-portal-security"></a>Konfigurer sikkerhed i Microsoft 365 Lighthouse Portal

Beskyttelse af adgang til kundedata, når en MSP (Managed Service Provider) har uddelegeret adgangstilladelser til sine lejere, er en prioritet for cybersikkerhed. Microsoft 365 Fyrtårn leveres med både påkrævede og valgfrie funktioner, der kan hjælpe dig med at konfigurere sikkerhed i Lighthouse-portalen. Du skal konfigurere specifikke roller, hvor multifaktorgodkendelse (MFA) er aktiveret, før du kan få adgang til Lighthouse. Du kan eventuelt konfigurere Azure AD Privileged Identity Management (PIM) og betinget adgang.

## <a name="set-up-multifactor-authentication-mfa"></a>Konfigurer multifaktorgodkendelse (MFA)

Som nævnt i blogindlægget [Din Pa $ $word betyder ikke noget](https://techcommunity.microsoft.com/t5/azure-active-directory-identity/your-pa-word-doesn-t-matter/ba-p/731984):

> "Din adgangskode er lige meget, men det gør MFA. På baggrund af vores undersøgelser er din konto mere end 99,9 % mindre tilbøjelige til at blive kompromitteret, hvis du bruger MFA."

Når brugerne får adgang til Lighthouse for første gang, bliver de bedt om at konfigurere MFA, hvis deres Microsoft 365 konto ikke allerede har den konfigureret. Brugerne kan ikke få adgang til Lighthouse, før det påkrævede trin til konfiguration af MFA er fuldført. Hvis du vil vide mere om godkendelsesmetoder, skal du se [Konfigurer dit Microsoft 365 logon til multifaktorgodkendelse](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

## <a name="set-up-role-based-access-control"></a>Konfigurer rollebaseret adgangskontrol

Rollebaseret adgangskontrol giver adgang til ressourcer eller oplysninger baseret på brugerroller. Adgang til kundelejerdata og -indstillinger i Lighthouse er begrænset til specifikke roller fra programmet Cloud Solution Provider (CSP). Hvis du vil konfigurere RBAC-roller i Lighthouse, anbefaler vi, at du bruger GDAP (Granular Delegated Admin Privileges) til at implementere detaljerede tildelinger for brugere. Der kræves stadig delegerede administratorrettigheder (DAP), for at lejeren kan onboarde korrekt, men kun GDAP-kunder vil snart kunne onboarde uden at være afhængige af DAP. GDAP-tilladelser har forrang, når DAP og GDAP eksisterer sammen for en kunde.

Hvis du vil konfigurere en GDAP-relation, skal du se [Få detaljerede administratortilladelser til at administrere en kundes tjeneste](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Du kan få flere oplysninger om, hvilke roller vi anbefaler at bruge Lighthouse i [Oversigt over tilladelser i Microsoft 365 Fyrtårn](m365-lighthouse-overview-of-permissions.md).

MSP-teknikere kan også få adgang til Lighthouse ved hjælp af rollerne Administratoragent eller Helpdesk Agent via delegerede administratorrettigheder (DAP).

For lejerrelaterede handlinger, der ikke er kunde, i Lighthouse (f.eks. onboarding, kunde deaktivering/genaktivering, administration af mærker, gennemsyn af logge), skal MSP-teknikere have en tildelt rolle i partnerlejer. Se [Oversigt over tilladelser i Microsoft 365 Fyrtårn](m365-lighthouse-overview-of-permissions.md) for at få flere oplysninger om partnerlejerroller.

## <a name="set-up-azure-ad-privileged-identity-management-pim"></a>Konfigurer Azure AD Privileged Identity Management (PIM)

MSP'er kan minimere antallet af personer, der har rolleadgang til sikre oplysninger eller ressourcer med høj rettighed ved hjælp af PIM. PIM reducerer risikoen for, at en ondsindet person får adgang til ressourcer eller godkendte brugere utilsigtet påvirker en følsom ressource. MSP'er kan også give brugere lige i tiden roller med høje rettigheder til at få adgang til ressourcer, foretage brede ændringer og overvåge, hvad de udpegede brugere gør med deres privilegerede adgang.

> [!NOTE]
> Brug af Azure AD PIM kræver en Azure AD Premium P2-licens i partnerlejer.

Følgende trin hæver brugere af partnerlejere til tidsbaserede roller med højere rettigheder ved hjælp af PIM:

1. Opret en gruppe, der kan tildeles roller, som beskrevet i artiklen [Opret en gruppe til tildeling af roller i Azure Active Directory](/azure/active-directory/roles/groups-create-eligible).

2. Gå til [Azure AD – alle grupper](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/AllGroups), og tilføj den nye gruppe som medlem af en sikkerhedsgruppe for roller med rettigheder på højt niveau (f.eks. sikkerhedsgruppen Administratoragenter for DAP eller en tilsvarende respektive sikkerhedsgruppe for GDAP-roller).

3. Konfigurer privilegeret adgang til den nye gruppe som beskrevet i artiklen [Tildel berettigede ejere og medlemmer til privilegerede adgangsgrupper](/azure/active-directory/privileged-identity-management/groups-assign-member-owner).

Du kan få mere at vide om PIM under [Hvad er Privileged Identity Management?](/azure/active-directory/privileged-identity-management/pim-configure)

## <a name="set-up-risk-based-azure-ad-conditional-access"></a>Konfigurer risikobaseret Azure AD betinget adgang

MSP'er kan bruge risikobaseret betinget adgang til at sikre, at deres medarbejdere beviser deres identitet ved hjælp af MFA og ved at ændre deres adgangskode, når de registreres som en risikobetonet bruger (med lækkede legitimationsoplysninger eller pr. Azure AD trusselsintelligens). Brugerne skal også logge på fra en velkendt placering eller en registreret enhed, når de registreres som et risikabelt logon. Andre risikable funktionsmåder omfatter at logge på fra en skadelig eller anonym IP-adresse eller fra en atypisk eller umulig rejseplacering, ved hjælp af et unormalt token, ved hjælp af en adgangskode fra en adgangskodespray eller udviser andre usædvanlige logonadfærd. Afhængigt af en brugers risikoniveau kan MSP'er også vælge at blokere adgang ved logon. Du kan få mere at vide om risici under [Hvad er risiko?](/azure/active-directory/identity-protection/concept-identity-protection-risks)

> [!NOTE]
> Betinget adgang kræver en Azure AD Premium P2-licens i partnerlejer. Hvis du vil konfigurere betinget adgang, skal du se [Konfiguration af Azure Active Directory Betinget adgang](/appcenter/general/configuring-aad-conditional-access).

## <a name="related-content"></a>Relateret indhold

[Tilladelser til nulstilling af adgangskode](/azure/active-directory/roles/permissions-reference#password-reset-permissions) (artikel)\
[Oversigt over tilladelser i Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md) (artikel)\
[Få vist dine Azure Active Directory roller i Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (artikel)\
[Krav til Microsoft 365 Fyrtårn](m365-lighthouse-requirements.md) (artikel)\
[Oversigt over Microsoft 365 Fyrtårn](m365-lighthouse-overview.md) (artikel)\
[Tilmeld dig Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (artikel)\
[ofte stillede spørgsmål om Microsoft 365 fyrtårn](m365-lighthouse-faq.yml) (artikel)