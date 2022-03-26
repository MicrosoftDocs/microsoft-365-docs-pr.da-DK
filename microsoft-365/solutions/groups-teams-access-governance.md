---
title: Styre adgangen til Microsoft 365 grupper, Teams og SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du Microsoft 365 adgang i Teams, grupper og SharePoint.
ms.openlocfilehash: 3f4304a54cd1eae86c98d530e5a4ec4db5f6dc66
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63716162"
---
# <a name="governing-access-in-microsoft-365-groups-teams-and-sharepoint"></a>Styre adgangen til Microsoft 365 grupper, Teams og SharePoint

Der er mange kontrolelementer, der giver dig mulighed for at styre, hvordan personer får adgang til ressourcer i grupper, teams SharePoint. Gennemgå disse muligheder, og overvej, hvordan de kortlægger dine forretningsmæssige behov, følsomheden af dine data og omfanget af personer, som dine brugere skal samarbejde med.

Den følgende tabel giver en hurtig reference til de adgangskontrolelementer, der er tilgængelige Microsoft 365. Yderligere oplysninger findes i de følgende afsnit.

|Kategori|Beskrivelse|Reference|
|:-------|:----------|:--------|
|Medlemskab|||
||Opdagelse af private teams|[Administrer opdagelsen af private teams i Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)|
||Dynamisk gruppemedlemskab baseret på regler|[Opret eller opdater en dynamisk gruppe i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)|
||Be kontrol, hvem der kan dele filer, mapper og websteder.|[Konfigurere og administrere anmodninger om adgang](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)|
|Betinget adgang|||
||Multifaktorgodkendelse|[Azure AD multi-factor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)|
||Kontroller adgang til enheder baseret på gruppe-, team- eller webstedsfølsomhed.|[Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Begræns adgangen til webstedet for enheder, der ikke er administrerede.|[Styre SharePoint adgang fra enheder, der ikke er administrerede](/sharepoint/control-access-from-unmanaged-devices)|
||Kontrollere adgang til webstedet baseret på placering|[Kontrollere adgang til SharePoint og OneDrive baseret på netværksplacering](/sharepoint/control-access-based-on-network-location)|
|Gæsteadgang|||
||Tillad eller bloker SharePoint deling fra angivne domæner.|[Begræns deling SharePoint indhold OneDrive efter domæne](/sharepoint/restricted-domains-sharing)|
||Tillad eller bloker for team- eller gruppemedlemskab fra angivne domæner.|[Tillad eller bloker invitationer til B2B-brugere fra bestemte organisationer](/azure/active-directory/b2b/allow-deny-list)|
||Undgå anonym deling.|[Deaktivere alle links](./share-limit-accidental-exposure.md#turn-off-anyone-links)|
||Kontrollere tilladelserne for anonyme adgangslinks.|[Angive linktilladelser for alle links](./best-practices-anonymous-sharing.md#set-link-permissions)|
||Kontrollere udløb af anonyme delingslinks.|[Angiv en udløbsdato for alle links](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)|
||Styr den type delingslink, der vises for brugere som standard.|[Skift standardlinktypen for et websted](/sharepoint/change-default-sharing-link)|
||Begræns ekstern deling til bestemte personer.|[Begræns ekstern deling til angivne sikkerhedsgrupper](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)|
||Kontroller gæsteadgang til en gruppe, et team eller et websted baseret på oplysningernes følsomhed.|[Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Slå delingsindstillinger fra.|[Begræns deling i Microsoft 365](./microsoft-365-limit-sharing.md)|
|Brugeradministration|||
||Gennemgå team- og gruppemedlemskab med jævne mellemrum.|[Hvad er Azure AD-adgangsvurderinger?](/azure/active-directory/governance/access-reviews-overview)|
||Automatiser adgangsstyring for grupper og teams.|[Hvad er Azure AD rettighedsstyring?](/azure/active-directory/governance/entitlement-management-overview)|

## <a name="membership"></a>Medlemskab

Medlemskab af teams og grupper styres af ejere. Medlemmer kan invitere andre, men invitationerne sendes til ejere til godkendelse. Mens offentlige teams og grupper er tilgængelige for alle i organisationen, kan du styre, om private teams og grupper kan findes:

- [Administrer opdagelsen af private teams i Microsoft Teams](/microsoftteams/manage-discovery-of-private-teams)

Du kan administrere medlemskab af en gruppe eller et team dynamisk ud fra nogle kriterier, f.eks. afdeling. I dette tilfælde kan medlemmer og ejere ikke invitere personer til teamet. Dynamiske grupper bruger metadata, som du definerer i Azure Active Directory til at styre, hvem der er medlem af gruppen. Sørg for, at de metadata, du bruger, er fuldstændige og opdaterede som forkerte metadata, så brugere bliver væk fra grupper, eller at der tilføjes forkerte brugere.

- [Opret eller opdater en dynamisk gruppe i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

SharePoint giver mulighed for at tilføje ejere, medlemmer og besøgende, som ikke er medlem af grupper eller teams. Afhængigt af dine krav kan det være en ide at begrænse, hvem der kan invitere personer til webstedet. Afhængigt af følsomheden af oplysningerne på et givet websted kan du eventuelt begrænse, hvem der kan dele filer og mapper. Disse begrænsninger konfigureres af team-, gruppe- eller webstedsejeren:

- [Konfigurere og administrere anmodninger om adgang](https://support.microsoft.com/office/94b26e0b-2822-49d4-929a-8455698654b3)


## <a name="conditional-access"></a>Betinget adgang

Med Microsoft 365 kan du kræve multifaktorgodkendelse for både personer i og uden for organisationen. Der er mange muligheder for de omstændigheder, hvor folk bliver bedt om en anden godkendelsesmetode. Vi anbefaler på det kraftigste, at du installerer multifaktorgodkendelse for organisationen:

- [Azure AD Multi-Factor Authentication](/azure/active-directory/authentication/concept-mfa-howitworks)

Hvis du har følsomme oplysninger i nogle af dine grupper og teams, kan du håndhæve politikker for administration af enheder baseret på en gruppe eller et teams følsomhedsmærkat. Du kan blokere adgangen helt fra enheder, der ikke er administrerede, eller tillade begrænset adgang, kun via internettet:

- [Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)

I SharePoint kan du begrænse adgangen til websteder fra bestemte netværksplaceringer.

- [Kontrollere adgang til SharePoint og OneDrive baseret på netværksplacering](/sharepoint/control-access-based-on-network-location)


Flere ressourcer:

- [Planlægge en installation med betinget adgang](/azure/active-directory/conditional-access/plan-conditional-access)

- [Microsoft Intune oversigt](/mem/intune/fundamentals/what-is-intune)

- [Styre SharePoint adgang fra enheder, der ikke er administrerede](/sharepoint/control-access-from-unmanaged-devices)


## <a name="guest-access"></a>Gæsteadgang

Du kan begrænse gæster baseret på domænet for deres mailadresse. SharePoint tilbyder indstillinger for begrænsning af domæner for hele organisationen og for hele virksomheden. Grupper og Teams bruger domænets tilladelseslister eller blokeringslister i Azure AD. Sørg for at konfigurere begge indstillinger for at undgå uønsket deling og sikre en ensartet brugeroplevelse:

- [Begræns deling SharePoint indhold OneDrive efter domæne](/sharepoint/restricted-domains-sharing)

- [Tillad eller bloker invitationer til B2B-brugere fra bestemte organisationer](/azure/active-directory/b2b/allow-deny-list)

Microsoft 365 anonym deling af filer og mapper ved hjælp af *Alle, der* deler links. *Alle* links kan videresendes, og alle med linket kan få adgang til det delte element. Afhængigt af dine datas følsomhed kan du overveje at styre, hvordan *Alle links bruges* – herunder helt at deaktivere dem, begrænse linktilladelser til skrivebeskyttet eller angive et udløbstidspunkt for dem:

- [Deaktivere alle links](./share-limit-accidental-exposure.md#turn-off-anyone-links)

- [Angive linktilladelser for alle links](./best-practices-anonymous-sharing.md#set-link-permissions)

- [Angiv en udløbsdato for alle links](./best-practices-anonymous-sharing.md#set-an-expiration-date-for-anyone-links)

Når du deler filer eller mapper, har brugerne flere linktyper at vælge mellem. For at reducere risikoen for utilsigtet upassende deling kan du ændre den standardlinktype, der vises til brugere, når de deler. Hvis du f.eks. ændrer  standardlinks fra Alle - som tillader anonym adgang - til personer i *organisationens links*, kan det reducere risikoen for uønsket ekstern deling af følsomme oplysninger:

- [Skift standardlinktypen for et websted](/sharepoint/change-default-sharing-link)

Hvis din organisation har følsomme data, som du skal dele med gæster, men du er bekymret over upassende deling, kan du begrænse ekstern deling af filer og mapper til medlemmer af bestemte sikkerhedsgrupper. På denne måde kan du begrænse ekstern deling til en bestemt gruppe af personer eller kræve, at dine brugere tager kurser omkring relevant ekstern deling, før de føjes til sikkerhedsgruppen:

- [Begræns ekstern deling til angivne sikkerhedsgrupper](./share-limit-accidental-exposure.md#limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups)

Grupper og Teams har indstillinger på organisationsniveau, der tillader eller afviser gæsteadgang. Selvom du kan [begrænse gæsteadgang til bestemte teams](per-group-guest-access.md) eller grupper ved hjælp af Microsoft PowerShell, anbefaler vi, at du gør dette ved hjælp af et følsomhedsmærkat. Med følsomhedsmærkater kan du automatisk tillade eller afvise gæsteadgang baseret på den etiket, der er anvendt:

- [Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)

I et miljø, hvor du ofte inviterer gæster til grupper og teams, kan du overveje at konfigurere regelmæssigt planlagte anmeldelser af gæsteadgang. Ejere kan blive bedt om at gennemse gæster i deres grupper og teams og godkende eller afvise adgang.

- [Konfigurer anmeldelser af gæsteadgang](/microsoft-365/solutions/create-secure-guest-sharing-environment#set-up-guest-access-reviews)

Microsoft 365 tilbyder mange forskellige metoder til deling af oplysninger. Hvis du har følsomme oplysninger, og du vil begrænse, hvordan de deles, skal du gennemse mulighederne for at begrænse deling:

- [Begræns deling i Microsoft 365](./microsoft-365-limit-sharing.md)

Flere ressourcer:

- [Konfigurer sikkert samarbejde med Microsoft 365](./setup-secure-collaboration-with-teams.md)

- [Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](./best-practices-anonymous-sharing.md)

- [Begræns utilsigtet eksponering af filer ved deling med personer uden for organisationen](./share-limit-accidental-exposure.md)

- [Opret et sikkert miljø for gæstedeling](./create-secure-guest-sharing-environment.md)

- [Aktivér eksternt B2B-samarbejde, og administrer, hvem der kan invitere gæster](/azure/active-directory/b2b/delegate-invitations)

## <a name="user-management"></a>Brugeradministration

Når grupper og teams udvikler sig i organisationen, er det en god ide at gennemgå team- og gruppemedlemskab med jævne mellemrum. Dette kan især være nyttigt for teams og grupper med et skiftende medlemskab, dem, der indeholder følsomme oplysninger, eller dem, der omfatter gæster. Overvej at konfigurere adgangsvurderinger for disse teams og grupper:

- [Hvad er Azure AD-adgangsvurderinger?](/azure/active-directory/governance/access-reviews-overview)

Mange organisationer har forretningsområder med andre organisationer eller nøgleleverandører, som de samarbejder i dybden med. Det kan være en udfordring at administrere brugerstyring og adgang til ressourcer i disse scenarier. Overvej at automatisere nogle af brugeradministrationsopgaverne og endda overgå nogle af dem til din partnerorganisation:

- [Hvad er Azure AD rettighedsstyring?](/azure/active-directory/governance/entitlement-management-overview)

Private kanaler i Teams mulighed for samtaler og fildeling mellem et undersæt af teammedlemmer. Afhængigt af dine specifikke forretningsmæssige behov kan det være en ide at tillade eller blokere denne funktion.

- [Private kanaler i Microsoft Teams](/MicrosoftTeams/private-channels)

Delte kanaler giver dig mulighed for at invitere personer, der er uden for teamet eller uden for organisationen. Afhængigt af dine specifikke forretningsbehov og politikker for ekstern deling kan det være en ide at tillade eller blokere denne funktion.

- [Delte kanaler](/MicrosoftTeams/shared-channels)

Flere ressourcer:

- [Azure Active Directory identitetsstyring](/azure/active-directory/governance)

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Sikkerhed og overholdelse i Microsoft Teams](/microsoftteams/security-compliance-overview)

[Administrer indstillinger for deling i SharePoint](/sharepoint/turn-external-sharing-on-or-off)

[Oprette og administrere et eksternt netværk i Yammer](/yammer/work-with-external-users/create-and-manage-an-external-network)

[Konfigurere Teams med tre niveauer af beskyttelse](./configure-teams-three-tiers-protection.md)