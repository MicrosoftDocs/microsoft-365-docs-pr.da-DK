---
title: Planlæg eksternt samarbejde med kanalsamtaler, filsamarbejde og delte apps
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
localization_priority: Normal
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om forskellen mellem gæstesamarbejde og delte kanaler i Teams, og hvordan du vælger, hvilken der skal bruges.
ms.openlocfilehash: 3a6bc5c7f0b07208e3543bfab9d1d5f0d51fc225
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "66858615"
---
# <a name="plan-external-collaboration-with-channel-conversations-file-collaboration-and-shared-apps"></a>Planlæg eksternt samarbejde med kanalsamtaler, filsamarbejde og delte apps

Microsoft 365 indeholder flere muligheder for at samarbejde med personer uden for din organisation:

- 1:1 og gruppechat i Teams med personer uden for din organisation
- Teams-møder med personer uden for din organisation
- Deling af individuelle filer eller mapper med personer uden for din organisation
- Samarbejde i et team med kanalsamtaler, filsamarbejde og delte apps

I denne artikel beskrives den fjerde indstilling, gruppesamarbejde med kanalsamtaler, filsamarbejde og delte apps. (Du kan få en oversigt over alle mulighederne under [Oversigt over indstillinger for eksternt samarbejde i Microsoft 365](/microsoft-365/enterprise/external-guest-access)).

## <a name="terms"></a>Vilkår

- **Azure AD B2B-samarbejde** – en funktion, der giver brugerne mulighed for at dele filer, mapper, websteder, grupper og teams med personer uden for din organisation. Disse personer får adgang til delte ressourcer ved hjælp af gæstekonti i din mappe.
- **Azure AD B2B Direct Connect** – en funktion, der giver brugerne mulighed for at dele ressourcer i din organisation med personer fra andre Azure AD organisationer. Disse personer får adgang til de delte ressourcer ved hjælp af deres egen arbejds- eller skolekonto. Der oprettes ingen gæstekonto i din organisation.
- **Ekstern deltager** – en person uden for din organisation, der deltager i en ressource – f.eks. en delt kanal – ved hjælp af sin egen identitet og ikke en gæstekonto i din mappe.
- **Ekstern organisation** – en anden organisation, som du deler ressourcer med.
- **Gæst** – en person uden for din organisation, der tilgår delte ressourcer ved at logge på en gæstekonto i din mappe.
- **Værtsorganisation** – den organisation, der hoster en delt ressource, f.eks. en delt kanal.
- **Delt kanal** – en Teams-kanal, der kan deles med personer uden for teamet. Disse personer kan være i din organisation eller fra andre Azure AD organisationer.
- **Deling af links** – links med tilladelser til en fil eller mappe, der bruges til at dele den pågældende fil eller mappe med andre. De personer, der deles med, kan være i eller uden for din organisation.

## <a name="options-for-collaboration-in-a-team"></a>Muligheder for samarbejde i et team

Når du samarbejder i et team med personer uden for din organisation, er der to muligheder for, hvordan disse personer får adgang til de ressourcer, du deler med dem.

### <a name="guest-sharing"></a>Gæstedeling

Gæstedeling bruger Azure AD B2B-samarbejde til at tillade deling og samarbejde med personer uden for din organisation ved at tilføje en gæstekonto i Azure AD for hver person. Gæstekonti kan bruges til følgende:

- Gæstemedlemskab i teams, SharePoint-websteder og Microsoft 365-grupper
- Individuel fil- og mappedeling

Gæster i et team har samme egenskaber som almindelige teammedlemmer.

### <a name="external-participants-in-shared-channels"></a>Eksterne deltagere i delte kanaler

Eksterne deltagere får adgang til delte ressourcer i din organisation ved hjælp af deres egne Azure AD eller En Microsoft 365-identitet. Dette aktiveres af Azure AD B2B direkte forbindelse via en organisationsrelation, der er konfigureret af begge organisationer. Gæstekonti bruges ikke i denne relation.

Den primære fordel ved eksterne deltagere i delte kanaler i forhold til gæstedeling er, at personer uden for din organisation kan samarbejde med dine brugere i Teams uden at skulle ændre deres brugerkontekst. Når brugerne bruger gæstekonti, skal de logge af Teams med deres arbejds- eller skolekonto og logge på igen ved hjælp af gæstekontoen. Alternativt kan de have en separat kopi af Teams kørende i en privat browsersession. Dette skift mellem organisationer tager tid og kan medføre, at brugerne går glip af vigtig kommunikation, mens de er logget af en bestemt organisation.

Med delte kanaler kan brugerne forblive logget på deres organisation og få adgang til kanaler, der deles med dem fra andre organisationer. Delte kanaler fra andre organisationer er tilgængelige i Teams sammen med teams og kanaler i din organisation. Det er ikke nødvendigt at skifte organisation.

## <a name="feature-comparison"></a>Sammenligning af funktioner

I følgende tabel beskrives de tilgængelige oplevelser, afhængigt af den anvendte kontotype.

|Funktion|Bruger (din organisation)|Gæst (Azure AD samarbejde)|Ekstern deltager (Azure AD direkte forbindelse)|
|:-----|:-----|:------|:-------|
|Teamadgang|Y|Y|N|
|Adgang til delt kanal|Y|N|Y|
|Tilladelser via links til fildeling|Y|Y|N|
|Brug delte kanaler|Y|N|Y|
|Brug private kanaler|Y|Y|N|
|Konto i din mappe|Y|Y|N|
|Få adgang til korrekturer|Y|Y|Y|

## <a name="planning-considerations"></a>Overvejelser i forbindelse med planlægning

De fleste organisationer bruger både gæstedelingskanaler og delte kanaler med eksterne deltagere.

Gæstedeling er som standard aktiveret i Azure AD og i Microsoft 365 (Teams, Microsoft 365-grupper og SharePoint). Dette giver brugerne mulighed for at invitere gæster til teams og websteder og dele filer med dem uden at skulle anmode om hjælp fra it-medarbejdere.

Du skal bruge gæstedeling, hvis:

- Du vil invitere personer uden for din organisation til teamet i stedet for individuelle kanaler
- Du vil dele filer eller mapper i en kanal med personer uden for din organisation, som ikke er i kanalen
- Du vil samarbejde med personer uden for din organisation, der ikke har en arbejds- eller skolekonto.

Selvom delte kanaler er slået til som standard i Teams, kræver eksternt samarbejde med delte kanaler, at en Azure AD administrator konfigurerer adgang på tværs af lejere mellem din organisation og hinandens organisation, som du vil dele med. Hver anden organisation skal også konfigurere adgang på tværs af lejere til deres ende.

Hvis du planlægger at bruge delte kanaler med andre organisationer, kan du vælge mellem en selvbetjeningsmodel og en model efter anmodning.

- Selvbetjening – Du kan konfigurere adgang på tværs af lejere for at tillade indgående og udgående adgang til alle andre Azure AD organisationer. Du kan også blokere en liste over organisationer, som dine brugere ikke skal dele med, så alle andre organisationer er tilgængelige. Dette giver brugerne mulighed for at invitere personer uden for organisationen til at deltage i delte kanaler uden at skulle kontakte din helpdesk eller it-afdeling.
- Efter anmodning – Du kan konfigurere adgang på tværs af lejere for hver enkelt organisation, som du vil tillade delte kanaler med. Når du vælger denne model, er det vigtigt at have en dokumenteret forretningsproces, som dine brugere kan følge for at anmode om adgang på tværs af lejere med en anden organisation.

## <a name="compliance-in-shared-channels"></a>Overholdelse i delte kanaler

Delte kanaler er integreret med Funktioner i Microsoft Purview.

### <a name="communications-compliance"></a>Overholdelse af kommunikation

Administratorer kan angive politikker for at overvåge indhold for alle brugere i kanalen. Alt meddelelsesindhold i kanaler, herunder delte kanaler, er dækket af [politikker for kommunikation med overholdelse af angivne standarder](/microsoft-365/compliance/communication-compliance). Delte kanaler nedarver politikken for værtsorganisationen.

### <a name="conditional-access"></a>Betinget adgang

Understøttede [politikker for betinget adgang](/azure/active-directory/conditional-access/overview) fra værtsorganisationen kan anvendes på B2B-brugere med direkte forbindelse. (Den eksterne organisations politikker bruges ikke). Følgende typer politikker for betinget adgang understøttes med delte kanaler:

- Politikker, der er begrænset til **alle gæstebrugere og eksterne brugere**, og **Office 365 SharePoint Online-cloudappen**.
- Tildel adgangskontrolelementer, der kræver MFA, en kompatibel enhed eller en hybrid Azure AD tilsluttet enhed.

IP-baserede politikker understøttes på SharePoint-filniveau. En ekstern deltager kan derfor få adgang til en delt kanal fra en begrænset placering, men blokeres, når der gøres forsøg på at åbne en fil.

Du kan få flere oplysninger om betinget adgang til eksterne identiteter under [Godkendelse og betinget adgang til eksterne identiteter](/azure/active-directory/external-identities/authentication-conditional-access).

### <a name="data-loss-prevention-dlp"></a>Forebyggelse af datatab (DLP)

Administratorer kan anvende [Microsoft Purview DLP-politikker](/microsoft-365/compliance/dlp-policy-design) på et team, hvor alle kanaler, herunder delte kanaler, nedarver politikken. Delte kanaler nedarver politikken for værtsorganisationen.

### <a name="retention-policy"></a>Opbevaringspolitik

Administratorer kan anvende en [opbevaringspolitik](/microsoft-365/compliance/retention) på et team, hvor alle kanaler, herunder delte kanaler, arver opbevaringspolitikken. Delte kanaler nedarver politikken for det overordnede team.

### <a name="sensitivity-labels"></a>Følsomhedsmærkater

[Følsomhedsmærkater](/microsoft-365/compliance/sensitivity-labels) , der er tilgængelige i værtsorganisationen, er de eneste mærkater, der kan anvendes på dokumenterne på et websted med en delt kanal. En fil, der er krypteret af en følsomhedsmærkat, kan ikke åbnes af eksterne deltagere, medmindre der gives tilladelser. Automatisk mærkning bruges ikke.

Delte kanaler og deres tilknyttede SharePoint-websteder nedarver etiketten fra det overordnede team.

### <a name="information-barriers"></a>Informationsbarrierer

Brugere, der ikke har tilladelse til at kommunikere pr. [politik for informationsbarrierer](/microsoftteams/information-barriers-in-teams) , kan ikke være en del af en delt kanal. Politikker for informationsbarrierer er kun effektive for brugere i værtsorganisationen. Hvis brugerne er eksterne deltagere i en anden organisations delte kanal, gælder politikker for informationsbarrierer ikke.

### <a name="ediscovery"></a>eDiscovery

Administratorer kan udføre søgninger for alle brugere i kanalen. Alle kanaler, herunder den delte kanal, kan findes. Alle meddelelsesdata i kanalen, uanset hvem der har tilføjet dataene, kan registreres af overholdelsesadministratoren.

### <a name="legal-hold"></a>Juridisk venteposition

Administratorer kan placere medlemmer, der kun har kanaler, fra værtsorganisationen, som ikke er en del af teamet i venteposition. De kan også [placere hele teamet i venteposition](/MicrosoftTeams/legal-hold). Administratorer kan ikke placere en ekstern deltager i venteposition.

### <a name="audit-logs"></a>Overvågningslogge

Alle de handlinger, der udføres for [eksisterende overvågningshændelser](/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log) , overvåges i delte kanaler.

## <a name="related-topics"></a>Relaterede emner

[Introduktion til filsamarbejde i Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planlæg filsamarbejde i SharePoint med Microsoft 365](/sharepoint/deploy-file-collaboration)
