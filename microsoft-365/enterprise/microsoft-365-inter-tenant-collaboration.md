---
title: Microsoft 365 samarbejde mellem lejere
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: Få mere at Microsoft 365 om, hvordan samarbejde fungerer på tværs af lejere og organisationer, så forskellige organisationer kan samarbejde sikkert.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9cb91b6bcaac212eeaf0ef4051f466751d8dbbd9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590352"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 samarbejde mellem lejere

Antag, at to organisationer, Fabrikam og Contoso, hver har en Microsoft 365 til virksomhedslejer, og de vil arbejde sammen på flere projekter, hvoraf nogle kører i en begrænset periode, og nogle af dem er i gang. Hvordan kan Fabrikam og Contoso gøre det muligt for deres personer og teams at samarbejde mere effektivt på tværs af deres Microsoft 365 lejere på en sikker måde? Microsoft 365 B2B-samarbejde (Azure AD) indeholder Azure Active Directory muligheder i forbindelse med samarbejde med Azure AD. I denne artikel beskrives flere vigtige scenarier, som Fabrikam og Contoso kan overveje.

Microsoft 365 muligheder for samarbejde mellem lejere omfatter brug af en central placering til filer og samtaler, deling af kalendere, chat, lyd-/videoopkald til kommunikation og sikring af adgang til ressourcer og programmer. Brug følgende tabeller til at vælge løsninger og få mere at vide.

## <a name="exchange-online-collaboration-options"></a>Exchange Online indstillinger for samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Dele kalendere med en anden Microsoft 365 organisation |Administratorer kan konfigurere forskellige niveauer af kalenderadgang i Exchange Online for at tillade virksomheder at samarbejde med andre virksomheder og lade brugere dele tidsplaner (oplysninger om ledig/optaget) med andre. | <ul><li>[Deling](/exchange/sharing/sharing) </li><li> [Organisationsrelationer](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Oprette en organisationsrelation](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Rediger en organisationsrelation](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Fjern en organisationsrelation](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Dele kalendere med eksterne brugere](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Kontrollere, hvordan brugere deler deres kalendere med personer uden for organisationen | Administratorer anvender delingspolitikker til brugernes postkasser for at styre, hvem den kan deles med, og hvilket adgangsniveau der kan tildeles |  <ul><li> [Delingspolitikker](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Opret en delingspolitik](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Anvend en delingspolitik på postkasser](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Rediger, deaktiver eller fjern en delingspolitik](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|Konfigurer sikre mailkanaler, og styr mailflow med partnerorganisationer | Administratorer opretter forbindelsesforbindelser, der skal sikre dine mailudvekslinger med en partnerorganisation eller serviceudbyder. Forbindelsesforbindelserne gennemtvinger kryptering via Transport Layer Security (TLS), og tillader begrænsninger på domænenavne eller IP-adresseintervaller, som dine partnere sender mail fra. |  <ul><li> [Sådan Exchange Online du bruger TLS til at sikre mailforbindelser](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Konfigurere mailflow ved hjælp af forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Fjerndomæner](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [Konfigurer forbindelse for sikker mailflow med en partnerorganisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Bedste fremgangsmåder for mailflow (oversigt)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint online og OneDrive for Business indstillinger for samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Dele websteder og dokumenter med eksterne brugere | Administratorer konfigurerer deling på lejeren eller på niveauet for grupper af websteder for godkendte Microsoft-konti, godkendte arbejds- eller skolekonti eller gæstekonti |  <ul><li> [Administrere ekstern deling for dit SharePoint Online-miljø](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Begræns deling SharePoint indhold OneDrive efter domæne](/sharepoint/restricted-domains-sharing) </li><li> [Brug SharePoint Online som en B2B-ekstranetløsning (business-to-business)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Sporing og kontrol af ekstern deling for slutbrugere | OneDrive for Business-filejere og SharePoint Online-slutbrugere konfigurerer deling af websteder og dokumenter og opretter meddelelser til at spore deling |  <ul><li> [Konfigurer meddelelser for ekstern deling for OneDrive for Business](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Del SharePoint filer eller mapper](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>Skype for Business indstillinger for samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Skype for Business Online – chat, opkald og tilstedeværelse med andre Skype for Business brugere | Administratorer kan gøre deres Skype for Business Online-brugere i stand til at chat, foretage lyd-/videoopkald og se tilstedeværelse hos brugere i Microsoft 365 lejer. | [Tillad brugere at kontakte eksterne Skype for Business brugere](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype for Business online – chat, opkald og tilstedeværelse med Skype brugere (forbrugere) | Administratorer kan gøre deres Skype for Business onlinebrugere i stand til at chat, foretage opkald og se tilstedeværelse hos Skype (forbrugere). | [Lad Skype for Business brugere tilføje Skype kontakter](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Indstillinger for Azure AD B2B-samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Azure AD B2B-samarbejde – Indholdsdeling ved at føje eksterne brugere til en gruppe i en organisations mappe | En **Azure AD DC-administrator****,** sikkerhedsadministrator **,** brugeradministrator **,** skyprogramadministrator eller global **administrator for en** Microsoft 365-lejer kan invitere personer i en anden Microsoft 365-lejer til at deltage i deres adresseliste, føje disse eksterne brugere til en gruppe og give adgang til indhold, f.eks. SharePoint-websteder og biblioteker for gruppen. |  <ul><li> [Hvad er Azure AD B2B-samarbejdseksempel?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B: Nye opdateringer gør det nemt at samarbejde på tværs af virksomheder](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Ekstern deling og Azure Active Directory B2B-samarbejde](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Azure Active Directory API og tilpasning af B2B-samarbejde](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD og Identity Show: Azure AD B2B-samarbejde (Business til Business)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 indstillinger for samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Microsoft 365 grupper – mail, kalender, OneNote og delte filer på et centralt sted | Grupper understøttes i Business Essentials-, Business Premium-, Education- og Enterprise E1-, E3- og E5-planerne. Personer i én Microsoft 365-lejer kan oprette en gruppe og invitere personer fra en Microsoft 365 lejer som gæstebrugere. Gælder også for Dynamics CRM. |  <ul><li> [Få mere at vide Microsoft 365 grupper](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Gæsteadgang i Microsoft 365 Grupper](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Installér Microsoft 365 grupper](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>Yammer indstillinger for samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Yammer – samarbejde via sociale medier for virksomheder | Medmindre muligheden for at oprette eksterne grupper er deaktiveret af en Yammer-administrator, kan brugerne oprette eksterne grupper til at samarbejde i Yammer via samtaler, muligheden for at synes godt om og følge indlæg, dele filer og chatte online. | [Opret og administrer eksterne grupper i Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Teams indstillinger for samarbejde

|Deling af mål|Administrativ handling|Sådan gør du|
|:-----|:-----|:-----|
|Samarbejd i Teams med brugere uden for organisationen | En **brugeradministrator** eller **global administrator for** invitationen til Microsoft 365 lejeren skal aktivere eksternt samarbejde i Teams. Globale administratorer og teamejere kan nu invitere alle med en mailadresse til at samarbejde i Teams.  <br/> Administratorer kan også administrere og redigere gæster, der allerede findes i deres lejer. |  <ul><li> [Godkend gæsteadgang](/microsoftteams/teams-dependencies) </li><li> [Slå gæsteadgang til eller fra i Teams](/microsoftteams/set-up-guests) </li><li> [Brug PowerShell til at styre gæsteadgang](/microsoftteams/guest-access-powershell) </li><li> [Tjekliste for gæsteadgang](/microsoftteams/guest-access-checklist) </li><li> [Vis gæstebrugere](/microsoftteams/view-guests) </li><li> [Rediger gæstebrugeroplysninger](/microsoftteams/edit-guests-information) </li></ul> |
|Teamejere kan invitere og administrere, hvordan gæster samarbejder inden for deres teams.  |Teamejere har yderligere kontrol over, hvad gæsterne kan gøre inden for deres teams. |  <ul><li> [Tilføj gæster](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Føj en gæst til et team](/microsoftteams/add-guests) </li><li> [Administrer gæsteadgang i Teams](/microsoftteams/manage-guests) </li><li> [Se, hvem der er på et team eller i en kanal](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Gæster fra andre lejere kan få vist indhold i Teams og samarbejde med andre medlemmer | Ingen. | [Oplevelsen af gæsteadgang](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>Power BI indstillinger for samarbejde

| Deling af mål | Administrativ handling | Sådan gør du |
|:-----|:-----|:-----|
|Power BI gør det muligt for eksterne gæstebrugere at bruge indhold, der deles med dem, via links. Dette giver brugerne i organisationen mulighed for at distribuere indhold på en sikker måde på tværs af organisationer.<br/> | Den Power BI administrator kan styre, om brugere kan invitere eksterne brugere til at få vist indhold i organisationen.| [Distribuer Power BI indhold til eksterne gæstebrugere med Azure AD B2B](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Oplysninger, du skal være opmærksom på Microsoft 365 samarbejde mellem lejere

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Deling af brugerkonti, licenser, abonnementer og lagerplads

Hver organisation vedligeholder sine egne brugerkonti, identiteter, sikkerhedsgrupper, abonnementer, licenser og lagerplads. Folk bruger samarbejdsfunktionerne i Microsoft 365 sammen med delingspolitikker og sikkerhedsindstillinger for at give adgang til nødvendige oplysninger og samtidig bevare kontrollen over virksomhedens aktiver.

- **Brugerkonti:** Konti kan ikke deles eller duplikeres mellem lejere eller partitioner i det lokale Active Directory-domæneservices.

- **Licensabonnementer&amp;:** I Microsoft 365 giver licenser fra licensplaner (også kaldet SKU'er eller Microsoft 365-planer) brugerne adgang til de Microsoft 365-tjenester, der er defineret for disse planer.

- **Storage:** I Microsoft 365 licensplaner administreres softwaregrænser og -begrænsninger for SharePoint Online separat fra postkassens lagergrænser. Lagergrænser for postkasser konfigureres og administreres ved hjælp af Exchange Online. I begge scenarier kan lagerpladsen ikke deles mellem lejere.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Kan vi dele domænenavneområder på tværs Microsoft 365 lejere?

Nej. Organisationens domænenavne, f.eks fabrikam.com eller tailspintoys.com, kan kun knyttes til og bruges med en enkelt Microsoft 365 lejer. Hver lejer skal have sit eget navneområde. UPN-, SMTP- og SIP-navneområder kan ikke deles mellem lejere.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Hvad med hybridkomponenter og Microsoft 365 samarbejde mellem lejere?

Lokale hybridkomponenter, f.eks. en Exchange og Azure AD Forbind, kan ikke opdeles på tværs af flere lejere.
