---
title: Oversigt over tilladelser i Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: magarlan, chrigreen
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: I forbindelse med MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om tilladelseskrav til fyrtårne.
ms.openlocfilehash: 0ccc47fd151fa681b0231b2f776de3d2c46c5784
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66858703"
---
# <a name="overview-of-permissions-in-microsoft-365-lighthouse"></a>Oversigt over tilladelser i Microsoft 365 Lighthouse

Uddelegeret adgang til kundelejere er påkrævet, for at udbydere af administrerede tjenester kan bruge Microsoft 365 Lighthouse. GdAP (Granular Delegated Administration Privileges) giver MSP'er en høj grad af kontrol og fleksibilitet ved at give kunderne adgang via [indbyggede roller i Azure Active Directory (Azure AD).](/azure/active-directory/roles/permissions-reference) Tildeling af de mindst privilegerede roller efter opgave via GDAP til MSP-teknikere reducerer sikkerhedsrisikoen for både MSP'er og kunder. Du kan få flere oplysninger om de mindst privilegerede roller efter opgave under [Roller med færrest rettigheder – Partnercenter](/partner-center/gdap-least-privileged-roles-by-task) og [Mindst privilegerede roller efter opgave i Azure Active Directory](/azure/active-directory/roles/delegate-by-task). Du kan finde flere oplysninger om, hvordan du konfigurerer en GDAP-relation til en kundelejer, under [Få detaljerede administratortilladelser til at administrere en kundes tjeneste – Partnercenter.](/partner-center/gdap-obtain-admin-permissions-to-manage-customer)

Vi anbefaler, at du tildeler roller til grupper af MSP-teknikere baseret på de opgaver, hver gruppe skal udføre på vegne af kunden. Service Desk-teknikere skal muligvis blot læse kundelejerdata eller nulstille brugeradgangskoder. I modsætning hertil kan det være nødvendigt for eskaleringsteknikere at udføre flere afhjælpende handlinger for at opdatere sikkerhedsindstillingerne for kundens lejer. Det er bedste praksis at tildele den mindst tilladte rolle, der kræves for at udføre en opgave, så kunde- og partnerdata bevares sikre. Vi anbefaler, at du bruger Privileged Identity Management (PIM) til at aktivere tidsbaseret adgang til rollen Global administrator, hvis det er nødvendigt. Det er en sikkerhedsrisiko at give for mange brugere global adgang, og vi anbefaler, at du begrænser det så meget som muligt. Du kan få flere oplysninger om, hvordan du aktiverer PIM, under [Konfigurer Azure AD PIM.](m365-lighthouse-configure-portal-security.md#set-up-azure-ad-privileged-identity-management-pim)

Tabellerne i næste afsnit beskriver, hvilke GDAP-roller der giver tilladelse til at læse kundedata og udføre handlinger på kundelejere i Lighthouse. Se [Tilladelser i partnerlejer](#permissions-in-the-partner-tenant) i denne artikel for at få yderligere roller, der kræves for at administrere fyrtårnsobjekter (f.eks. tags og anmodninger om fyrtårnstjeneste).

## <a name="example-msp-service-tiers-recommended-gdap-roles-and-permissions"></a>Eksempel på MSP-tjenesteniveauer, anbefalede GDAP-roller og tilladelser

I følgende tabel vises de anbefalede GDAP-roller for nogle eksempler på MSP-tjenesteniveauer. 

|| Kontoadministratorer| Service Desk-teknikere | Systemadministratorer | Eskaleringsteknikere|
|---|---|---|---|---|
| **Anbefalede GDAP-roller** |<ul><li>Helpdesk-administrator</li></ul> |<ul><li>Sikkerhedslæser<br>+</li><li>Helpdesk-administrator</li></ul> |<ul><li>Global læser<br>+</li><li>Brugeradministrator<br>+</li><li>Godkendelsesadministrator</li></ul> |<ul><li>Global læser<br>+</li><li>Brugeradministrator<br>+</li><li>Intune administrator<br>+</li><li>Sikkerhedsadministrator</li></ul>|

I følgende tabel vises de handlinger, som MSP-tjenesteniveauerne i eksemplet kan udføre på de forskellige fyrtårnssider i forhold til deres tildelte GDAP-roller (som er angivet i den forrige tabel).

| Fyrtårnsside | Account Managers tilladte handlinger| Service Desk-teknikere tilladte handlinger |Systemadministratorer tillader handlinger | Tilladte handlinger for eskaleringsteknikere|
|---|---|---|---|---|
| Home  | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | 
| Lejere     | <ul><li>Vis liste over lejere</li><li>Opdater kundekontakter og websted</li><li>Vis udrulningsplaner</li></ul>  | <ul><li>Vis liste over lejere</li><li>Opdater kundekontakter og websted</li><li>Vis udrulningsplaner</li></ul>   |  <ul><li>Vis liste over lejere</li><li>Opdater kundekontakter og websted</li><li>Vis udrulningsplaner</li><li>Vis brug af Microsoft 365-tjenester</li></ul> | <ul><li>Vis liste over lejere</li><li>Opdater kundekontakter og websted</li><li>Vis udrulningsplaner</li><li>Vis brug af Microsoft 365-tjenester</li></ul>  |
| Brugere   | <ul><li>Vis lejerniveau (ikke-brugerspecifikke) data</li><li>Søg i brugerkonti på tværs af lejere</li><li>Nulstil adgangskode for ikke-administratorer*</li></ul>  | <ul><li>Få vist alle brugerspecifikke data</li><li>Søg i brugerkonti på tværs af lejere</li><li>Nulstil adgangskode for ikke-administratorer*</li></ul>|  <ul><li>Få vist alle brugerspecifikke data</li><li>Søg i brugerkonti på tværs af lejere</li><li>Nulstil adgangskode for ikke-administratorer*</i><li>Bloker logon</li></ul>  | <ul><li>Få vist alle brugerspecifikke data</li><li>Søg i brugerkonti på tværs af lejere</li><li>Nulstil adgangskode for ikke-administratorer*</li><li>Bloker logon</li><li>Bekræft kompromitterede brugere</li><li>Afvis risikoen for brugere</li></ul> |
| Enheder    | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li><li>Synkroniser enhed</li><li>Genstart enhed</li><li>Indsaml diagnosticering</li></ul>|
| Trusselsstyring  | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li><li>Kør fuld scanning</li><li>Kør hurtig scanning</li><li>Opdater antivirusbeskyttelse</li><li>Genstart enhed</li></ul>|
| Grundlinjer    | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul>  | <ul><li>Vis alle data</li></ul> |
| Windows 365 | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> | <ul><li>Vis alle data</li></ul> |
| Tjenestetilstand**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN |
| Overvågningslogge**| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;NIELSEN |

*Se [Tilladelser til nulstilling af adgangskode](/azure/active-directory/roles/permissions-reference#password-reset-permissions) for en tabel, der viser, hvilke roller der kræves for at nulstille adgangskoder for kundelejere.

**Der kræves forskellige roller og tilladelser for at få vist Tjenestetilstand- og overvågningslogge. Du kan få flere oplysninger under [Tilladelser i partnerlejer](#permissions-in-the-partner-tenant).

> [!NOTE]
> Hvis du får vist en meddelelse i Lighthouse om, at du ikke har tilladelse til at få vist eller redigere oplysninger, får du tildelt en rolle, der ikke har de nødvendige tilladelser til at udføre handlingen. Du skal kontakte en administrator i din partnerlejer, som kan tildele dig den relevante rolle for den handling, du forsøger at udføre.

## <a name="delegated-admin-privileges-dap-in-lighthouse"></a>Delegerede Administration rettigheder (DAP) i Lighthouse

GDAP erstatter til sidst DAP som den primære metode til konfiguration af uddelegeret adgang for kundelejere. Men hvis GDAP ikke er blevet konfigureret, kan MSP-teknikere stadig få adgang til Lighthouse ved hjælp af rollerne Helpdesk Agent eller Administration Agent, der er tildelt via DAP. For kunder, hvor GDAP og DAP eksisterer sammen, har roller, der tildeles MSP-teknikere via GDAP, forrang. Du kan få flere oplysninger om GDAP- eller DAP-udfasning i [ofte stillede spørgsmål om GDAP](/partner-center/gdap-faq) eller [i Partnercenter-meddelelser](/partner-center/announcements/2022-march#15) om datoer og tidslinjer.

For kunder med DAP og ingen GDAP giver rollen Administration Agent tilladelse til at få vist alle lejerdata og udføre handlinger i Lighthouse (se nedenfor for andre handlinger, der også kræver en rolle i partnerlejeren).

Rollen Helpdesk Agent giver tilladelser til at få vist alle lejerdata og udføre begrænsede handlinger i Lighthouse, f.eks. nulstille brugeradgangskoder, blokere brugerlogon og opdatere kundekontaktoplysninger og websteder.

I betragtning af de brede tilladelser, der er tildelt partnerbrugere med DAP-roller, anbefaler vi, at gdap vedtages hurtigst muligt. 

## <a name="permissions-in-the-partner-tenant"></a>Tilladelser i partnerlejer

For visse handlinger i Lighthouse kræves der rolletildelinger i partnerlejer. I følgende tabel vises partnerlejerroller og deres tilknyttede tilladelser.

| Partnerlejerroller | Tilladelser |
|--|--|
| Global administrator af partnerlejer | <ul><li>Tilmeld dig Lighthouse i Microsoft 365 Administration.</li><li>Acceptér ændringer af partnerkontrakten under førstegangsoplevelsen.</li><li>Aktivér og inaktiver en lejer.</li><li>Opret, opdater og slet mærker.</li><li>Tildel og fjern mærker fra en kundelejer.</li><li>Gennemse overvågningslogfiler</li></ul> |
| Partnerlejermedlem med mindst én Azure AD rolle, der er tildelt følgende egenskabssæt:<br>**microsoft.office365.supportTickets/allEntities/allTasks**<br>Du kan se en komplet liste over Azure AD roller [under Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference). | Opret anmodninger om fyrtårnsservice. |
| Partnerlejermedlem, der opfylder *begge* følgende krav: <ul><li>Har mindst én Azure AD rolle tildelt følgende egenskabssæt:<br>**microsoft.office365.serviceHealth/allEntities/allTasks**<br>Du kan se en komplet liste over Azure AD roller [under Azure AD indbyggede roller](/azure/active-directory/roles/permissions-reference).</li><li>Har mindst én DAP-uddelegeret rolle tildelt (Administration Agent eller Helpdesk Agent)</li></ul> | Vis oplysninger om tjenestetilstand. |

## <a name="related-content"></a>Relateret indhold

[Krav til Microsoft 365 Lighthouse](m365-lighthouse-requirements.md) (artikel)  
[Ofte stillede spørgsmål om delegerede administrationsrettigheder (DAP)](/partner-center/dap-faq) (artikel)  
[Få vist dine Azure Active Directory-roller i Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (artikel)  
[Tildel roller og tilladelser til brugere](/partner-center/permissions-overview) (artikel)  
[Oversigt over Microsoft 365 Lighthouse](m365-lighthouse-overview.md) (artikel)  
[Tilmeld dig Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md) (artikel)  
[Ofte stillede spørgsmål om Microsoft 365 Lighthouse](m365-lighthouse-faq.yml) (artikel)
