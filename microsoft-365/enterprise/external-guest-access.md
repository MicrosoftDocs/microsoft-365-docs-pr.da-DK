---
title: Oversigt over indstillinger for eksternt samarbejde i Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- SPO_Content
ms.localizationpriority: medium
description: Få mere at vide om, hvordan personer uden for din organisation kan få adgang til dit Microsoft 365-abonnement til møder, gæstedeling, chat og samarbejde.
ms.openlocfilehash: 988a1ecae8a060cae2334f97ef19bc90ba2be6bc
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "66858362"
---
# <a name="overview-of-external-collaboration-options-in-microsoft-365"></a>Oversigt over indstillinger for eksternt samarbejde i Microsoft 365

Med Microsoft 365 kan dine brugere samarbejde med personer uden for din organisation på flere forskellige måder. Brugerne kan dele filer, invitere gæster til teams, holde møder med eksterne deltagere og chatte med personer fra andre organisationer. I denne artikel beskrives de muligheder for eksternt samarbejde, der er tilgængelige, og links til det indhold, du skal bruge for at konfigurere hvert enkelt indhold.

I følgende tabel vises de primære måder, som personer uden for din organisation kan få adgang til dine Microsoft 365-ressourcer på:

|Aktivitet|Kontotype|Standardindstillingen|
|:-------|:-----------|:--------------|
|Godkendt fil- og mappedeling|Gæstekonto|Aktiveret|
|Deling af websted|Gæstekonto|Aktiveret|
|Teamdeling|Gæstekonto|Aktiveret|
|Delt kanal i Teams|Eksisterende ekstern Microsoft 365-konto|Deaktiveret|
|Ekstern chat og møder|Eksisterende ekstern Microsoft 365-konto|Aktiveret|
|Deltag i anonymt møde|Ingen|Aktiveret|
|Ikke-godkendt fil- og mappedeling|Ingen|Aktiveret|

Personer uden for din organisation har ikke adgang, medmindre en bruger i organisationen starter en af disse aktiviteter. Du kan deaktivere en af disse indstillinger, hvis du ikke vil tillade denne aktivitet i din organisation.

## <a name="document-site-and-team-sharing-with-guest-accounts"></a>Dokument-, websteds- og teamdeling med gæstekonti

Deling af dokumenter, websteder og teams med personer uden for din organisation bruger *gæstekonti*. Gæstekonti er en type konto i Azure Active Directory, der administreres via [Azure AD B2B-samarbejde](/azure/active-directory/external-identities/what-is-b2b). De kan bruges til at dele ressourcer i din organisation med alle, der har en mailadresse. Du kan administrere gæstekonti på samme måde, som du administrerer brugere i din organisation. Gæster behøver ikke at have licens til de fleste samarbejdsfunktioner. 

Gæster kan kun få adgang til ressourcer, som du specifikt deler med dem.

Hvis gæsten har en arbejds- eller skolekonto i en anden organisation eller en Microsoft-konto, kan vedkommende logge på med sit almindelige brugernavn og sin adgangskode. Hvis de har en anden type konto – f.eks. en Gmail-konto – kan de logge på ved hjælp af en engangs-adgangskode, der sendes til deres mailadresse.

Med gæster kan du:

- Inviter dem til Microsoft 365-grupper, -teams eller SharePoint-websteder, hvor de kan samarbejde med personer i din organisation.
- Del en enkelt fil eller mappe med dem, som de kan få vist eller redigere, afhængigt af de tilladelser, du giver dem.

Du kan få oplysninger om, hvordan du planlægger samarbejde med gæster i Microsoft 365, i følgende referencer:

- [Eksternt samarbejde](/microsoft-365/solutions/plan-external-collaboration)
- [Konfigurer sikker fildeling og samarbejde med Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams)

Du kan få oplysninger om, hvordan du konfigurerer Microsoft 365 til samarbejde med gæster, i følgende referencer:

- [Samarbejd med gæster om et dokument](/microsoft-365/solutions/collaborate-on-documents)
- [Samarbejd med gæster på et websted](/microsoft-365/solutions/collaborate-in-site)
- [Samarbejd med gæster i et team](/microsoft-365/solutions/collaborate-as-team)
 
## <a name="shared-channels"></a>Delte kanaler

Delte kanaler er en type Teams-kanal, der giver dig mulighed for at dele med personer uden for teamet, herunder personer i andre Microsoft 365-organisationer. Selvom delte kanaler er slået til som standard i Teams, er eksternt samarbejde med delte kanaler deaktiveret som standard. Eksternt samarbejde med delte kanaler bruger [Azure AD direkte B2B-forbindelse](/azure/active-directory/external-identities/b2b-direct-connect-overview), som giver dig mulighed for at føje personer fra andre Microsoft 365-organisationer til Teams-kanaler uden at skulle oprette en gæstekonto.

Delte kanaler har en særlig fordel i forhold til gæstekonti, da de ikke kræver, at eksterne deltagere skifter organisation i Teams-skrivebordsklienten eller logger på din organisation. De kan forblive logget på deres organisation og få direkte adgang til kanalen.

Deling af kanaler med personer uden for din organisation kræver, at din organisation og den eksterne organisation både konfigurerer en organisationsrelation i [Azure AD B2B Direct Connect](/azure/active-directory/external-identities/b2b-direct-connect-overview).

Du kan få oplysninger om, hvordan du konfigurerer Microsoft 365 til eksternt samarbejde med delte kanaler, i følgende referencer:

- [Eksternt samarbejde](/microsoft-365/solutions/plan-external-collaboration)
- [Delte kanaler i Microsoft Teams](/MicrosoftTeams/shared-channels)
- [Samarbejd med eksterne deltagere i en kanal](/microsoft-365/solutions/collaborate-teams-direct-connect)

## <a name="external-chat-and-meetings"></a>Ekstern chat og møder

Brugere i din organisation kan chatte, føje brugere til møder og bruge lyd- eller videomøder i Teams med brugere i eksterne Microsoft 365-organisationer. Brugere i din organisation kan som standard kommunikere på disse måder med alle andre Microsoft 365-domæner. Personer i andre organisationer kan kommunikere på disse måder med dine brugere, hvis de kender brugerens mailadresse. Du kan tillade eller blokere bestemte domæner eller blokere alle domæner, hvis du vil deaktivere funktionen.

Du kan også give brugere i din organisation tilladelse til at kommunikere med personer uden for din organisation, som bruger Teams-konti, der ikke administreres af en organisation, samt Skype for Business (online- og i det lokale miljø) og Skype-brugere.

Gæstekonti bruges ikke som en del af eksterne chat- og møder. Eksterne deltagere forbliver logget på deres organisation eller skype og kan kommunikere direkte med personer i din organisation. De har ikke adgang til dine teams eller kanaler.

Du kan få oplysninger om, hvordan du konfigurerer Microsoft 365 til eksterne chat og møder, i følgende referencer:

- [Brug gæsteadgang og ekstern adgang til at samarbejde med personer uden for din organisation](/microsoftteams/communicate-with-users-from-other-organizations)
- [Administrer ekstern adgang i Microsoft Teams](/microsoftteams/manage-external-access).

## <a name="anonymous-meeting-join"></a>Deltag i anonymt møde 

Personer uden for din organisation kan deltage i møder på følgende måder:

- Hvis de er logget på din organisation med en gæstekonto, deltager de i møder som gæst.
- Hvis de er logget på en anden organisation med en arbejds- eller skolekonto, og din organisation har aktiveret ekstern adgang, deltager de i møder som en ekstern deltager.
- Hvis de ikke er en gæst eller ekstern deltager, skal de deltage anonymt i møder.

Hvis indstillingen for anonym deltagelse er aktiveret for din organisation, kan anonyme brugere kun deltage i et møde ved hjælp af et mødelink, der er delt med dem (f.eks. et link i mødeinvitationen). De bliver bedt om at angive et vist navn efter eget valg, når de deltager i mødet anonymt. Afhængigt af lobbyindstillingerne kan den anonyme bruger automatisk få adgang til mødet eller føjes til en lobby, hvor mødearrangøren (eller mødedeltagere med præsentationsrollen) kan tillade eller nægte adgang til mødet. 

Det er ikke muligt at bekræfte identiteten af anonyme brugere før, under eller efter mødet. 

Du kan styre anonyme brugeres mulighed for at deltage i møder på organisationsniveau. Hvis den er aktiveret for organisationen, kan mødearrangører styre anonym deltagelse via indstillinger for mødepolitik.

Du kan få oplysninger om konfiguration af anonym deltagelse til møder [under Administrer mødeindstillinger i Microsoft Teams](/microsoftteams/meeting-settings-in-teams).

## <a name="unauthenticated-file-and-folder-access"></a>Ikke-godkendt fil- og mappeadgang

I Microsoft 365 kan filer og mapper i Teams, SharePoint og OneDrive deles ved hjælp af ikke-godkendte links – eller *alle* – links. Alle links giver adgang til det delte element til alle, der har linket. Alle links kan deles med andre, hvilket giver disse personer adgang til filen eller mappen.

Personer, der bruger et link af typen Enhver, behøver ikke at godkende, og deres adgang kan ikke overvåges. Fil- og mappeejere kan til enhver tid tilbagekalde adgangen ved at slette linket.

Alle links kan ikke bruges sammen med filer på et delt Teams-kanalwebsted.

Du kan få oplysninger om, hvordan du arbejder med anonym fil- og mappedeling, i følgende referencer:

- [Administrer delingsindstillinger](/sharepoint/turn-external-sharing-on-or-off)
- [Bedste praksis for deling af filer og mapper med ikke-godkendte brugere](/microsoft-365/solutions/best-practices-anonymous-sharing)

## <a name="related-topics"></a>Relaterede emner

[Introduktion til filsamarbejde i Microsoft 365, drevet af SharePoint](/sharepoint/intro-to-file-collaboration)

[Filsamarbejde i SharePoint med Microsoft 365](/sharepoint/deploy-file-collaboration)

[Brug gæsteadgang og ekstern adgang til at samarbejde med personer uden for din organisation](/microsoftteams/communicate-with-users-from-other-organizations)

[Begræns gæstedeling for bestemte organisationer](/microsoft-365/solutions/limit-guest-sharing-to-specific-organization)

[Begræns organisationer, hvor brugerne kan have gæstekonti](/microsoft-365/solutions/limit-organizations-where-users-have-guest-accounts)