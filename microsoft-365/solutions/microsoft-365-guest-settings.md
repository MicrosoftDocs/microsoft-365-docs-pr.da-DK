---
title: Reference for Microsoft 365-gæstedelingsindstillinger
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
f1.keywords: NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
recommendations: false
description: Få mere at vide om de indstillinger for gæstedeling, der er tilgængelige i Microsoft 365, og som kan påvirke deling med personer uden for din organisation.
ms.openlocfilehash: 574e2ab6b3ca01de31d4489b80c5b6aefddd6a9f
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949453"
---
# <a name="microsoft-365-guest-sharing-settings-reference"></a>Reference for Microsoft 365-gæstedelingsindstillinger

Denne artikel indeholder en reference til de forskellige indstillinger, der kan påvirke deling med personer uden for din organisation for Microsoft 365-arbejdsbelastninger: Teams, Microsoft 365-grupper, SharePoint og OneDrive. Disse indstillinger findes i Azure Active Directory, Microsoft 365, Teams og SharePoint Administration.

## <a name="azure-active-directory"></a>Azure Active Directory

**Administration rolle:** Global administrator

Azure Active Directory er den katalogtjeneste, der bruges af Microsoft 365. Indstillingerne for Azure Active Directory Organisationsrelationer påvirker direkte deling i Teams, Microsoft 365-grupper, SharePoint og OneDrive.

> [!NOTE]
> Disse indstillinger påvirker kun SharePoint, når [SharePoint- og OneDrive-integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) er konfigureret. I nedenstående tabel antages det, at dette er konfigureret.

### <a name="external-collaboration-settings"></a>Indstillinger for eksternt samarbejde

**Navigation:** [Azure Active Directory Administration](https://aad.portal.azure.com) > Azure Active Directory > eksterne identiteter > indstillinger for eksternt samarbejde

![Skærmbillede af siden Indstillinger for organisationsrelationer i Azure Active Directory.](../media/azure-ad-organizational-relationships-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Adgang for gæstebruger|Gæstebrugere har begrænset adgang til egenskaber og medlemskaber af katalogobjekter|Bestemmer de [tilladelser, som gæster har i Azure Active Directory](/azure/active-directory/fundamentals/users-default-permissions).|
|Indstillinger for gæsteinvitation|Alle i organisationen kan invitere gæstebrugere, herunder gæster og ikke-administratorer|Bestemmer, om gæster, medlemmer og administratorer kan invitere gæster til organisationen. <p> Denne indstilling påvirker Microsoft 365-delingsoplevelser, f.eks. Teams og SharePoint.|
|Aktivér tilmelding via selvbetjening via brugerflow|Nej|Bestemmer, om du kan oprette brugerflows, der giver andre mulighed for at tilmelde sig en app, som du har oprettet, og oprette en ny gæstekonto.|
|Begrænsninger for samarbejde|Tillad, at invitationer sendes til et hvilket som helst domæne|Denne indstilling giver dig mulighed for at angive en liste over tilladte eller blokerede domæner til deling. Når der er angivet tilladte domæner, kan invitationer til deling kun sendes til disse domæner. Når der er angivet domæner, der afvises, kan invitationer til deling ikke sendes til disse domæner. <p> Denne indstilling påvirker Microsoft 365-delingsoplevelser, f.eks. Teams og SharePoint. Du kan tillade eller blokere domæner på et mere detaljeret niveau ved hjælp af domænefiltrering i SharePoint eller Teams.|

Disse indstillinger påvirker, hvordan brugerne inviteres til mappen. De påvirker ikke deling med gæster, der allerede er i mappen.

### <a name="cross-tenant-access-settings"></a>Indstillinger for adgang på tværs af lejere

**Navigation:** [Azure Active Directory Administration](https://aad.portal.azure.com) > Azure Active Directory > eksterne identiteter > Adgangsindstillinger på tværs af lejere > fanen Standardindstillinger

Standardindstillingerne gælder for alle eksterne Azure AD organisationer undtagen organisationer med organisationsspecifikke indstillinger. Indstillinger for en bestemt organisation kan konfigureres under fanen **Organisationsindstillinger**. Der er separate indstillinger for gæster (B2B-samarbejde) og [Azure AD B2B-brugere med direkte forbindelse](/azure/active-directory/external-identities/b2b-direct-connect-overview).

![Skærmbillede af siden med indstillinger for azure Active Directory-adgang på tværs af lejere.](../media/azure-ad-cross-tenant-default-settings.png)

**Indstillinger for indgående adgang**

Indstillinger for indgående adgang styrer, om brugere fra eksterne Azure AD organisationer har adgang til ressourcer i din organisation.

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|B2B-samarbejde – eksterne brugere og grupper|Alle tilladt|Bestemmer, hvilke personer i andre Azure AD organisationer der kan få adgang til ressourcer i din organisation som gæster.|
|B2B-samarbejde – programmer|Alle tilladt|Bestemmer, hvilke apps i organisationen gæster kan få adgang til.|
|B2B Direct Connect – eksterne brugere og grupper|Alle blokerede|Bestemmer, om personer i andre Azure AD organisationer kan få adgang til ressourcer i din organisation via B2B Direct Connect.|
|B2B Direct Connect – programmer|Alle blokerede|Bestemmer, hvilke apps i din organisation B2B-brugere med direkte forbindelse, der kan tildeles adgang til.|
|Indstillinger for tillid|Deaktiveret|Bestemmer, om dine politikker for betinget adgang accepterer krav fra andre Azure AD organisationer, når personer fra disse organisationer får adgang til dine ressourcer.|

**Indstillinger for udgående adgang**

Indstillinger for udgående adgang styrer, om dine brugere kan få adgang til ressourcer i en ekstern organisation.

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|B2B-samarbejde – eksterne brugere og grupper|Alle tilladt|Bestemmer, hvilke brugere i organisationen der kan få adgang til ressourcer i andre Azure AD organisationer som gæster.|
|B2B-samarbejde – programmer|Alle tilladt|Bestemmer, hvilke apps i andre Azure AD organisationer dine brugere kan få adgang til som gæster.|
|B2B Direct Connect – eksterne brugere og grupper|Alle blokerede|Bestemmer, hvilke brugere i organisationen der kan få adgang til ressourcer i andre Azure AD organisationer via B2B Direct Connect.|
|B2B Direct Connect – programmer|Alle blokerede|Bestemmer, hvilke apps i andre Azure AD organisationer dine brugere kan få adgang til via B2B Direct Connect.|

## <a name="microsoft-365"></a>Microsoft 365

**Administration rolle:** Global administrator

Microsoft 365 Administration har indstillinger på organisationsniveau til deling og til Microsoft 365-grupper.

### <a name="sharing"></a>Deling

**Navigation:** [Microsoft 365 Administration](https://admin.microsoft.com) >  **Indstillinger** > **For organisationen** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**Sikkerhed &** fanen</a> > **Beskyttelse af** personlige oplysninger Deling.

![Skærmbillede af indstillingen for gæstedeling for sikkerhed og beskyttelse af personlige oplysninger i Microsoft 365 Administration.](../media/sharepoint-security-privacy-sharing-setting.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Lad brugerne føje nye gæster til organisationen|På|Når indstillingen er angivet til **Ja**, kan Azure AD medlemmer invitere gæster via Azure AD. Når indstillingen er angivet til **Nej**, kan de ikke. Når indstillingen er angivet til **Ja**, kan Microsoft 365-gruppemedlemmer invitere gæster med ejergodkendelse. Når indstillingen er angivet til **Nej**, kan Microsoft 365-gruppemedlemmer invitere gæster med ejergodkendelse, men ejere skal være globale administratorer for at godkende. <p> Bemærk, at **medlemmer kan invitere** henviser til medlemmer i Azure AD (i modsætning til gæster) og ikke til websteds- eller gruppemedlemmer i Microsoft 365. <p> Dette er identisk med indstillingen **Medlemmer kan invitere** i indstillinger for Organisationsrelationer i Azure Active Directory.|

### <a name="microsoft-365-groups"></a>Microsoft 365-grupper

**Navigation:** [Microsoft 365 Administration](https://admin.microsoft.com) >  **Indstillinger** > **for organisationen** > Microsoft 365-grupper

![Skærmbillede af Microsoft 365-grupper gæsteindstillinger i Microsoft 365 Administration.](../media/office-365-groups-guest-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Giv gruppemedlemmer uden for organisationen adgang til gruppeindhold|På|Når indstillingen er slået til **Til**, kan gæster få adgang til gruppers indhold. Når de er slået **fra**, kan de ikke. Denne indstilling skal være **Slået** til for alle scenarier, hvor gæster interagerer med Microsoft 365-grupper eller Teams.|
|Lad gruppeejere føje personer uden for din organisation til grupper|På|Når **Slået** til, kan ejere af Microsoft 365-grupper eller Teams invitere nye gæster til gruppen. Når **de er væk**, kan de ikke. Denne indstilling skal være **Slået** til for et hvilket som helst scenarie, hvor gæster skal føjes til grupper.|

Disse indstillinger findes på organisationsniveau. Se [Opret indstillinger for en bestemt gruppe for](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#create-settings-for-a-specific-group) at få oplysninger om, hvordan du ændrer disse indstillinger på gruppeniveau ved hjælp af PowerShell.

## <a name="teams"></a>Teams

Teams-gæsteadgangskontakten **Tillad gæsteadgang i Teams** skal være **Slået** til, for at de andre gæsteindstillinger er tilgængelige.

**Administration rolle:** Teams-tjenesteadministrator

### <a name="guest-access"></a>Gæsteadgang

**Navigation:** [Teams Administration](https://admin.teams.microsoft.com) > **Indstillinger for** >  hele organisationen <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**Gæsteadgang**</a>

![Skærmbillede af Teams-gæsteadgang til/fra.](../media/teams-guest-access-toggle.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Tillad gæsteadgang i Teams|På|Slår gæsteadgang til eller fra for Teams generelt. Det kan tage 24 timer, før denne indstilling træder i kraft, når den er ændret.|

### <a name="guest-calling"></a>Gæsteopkald

**Navigation:** [Teams Administration](https://admin.teams.microsoft.com) > **Indstillinger for** >  hele organisationen <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**Gæsteadgang**</a>

![Skærmbillede af indstillinger for Gæsteopkald i Teams.](../media/teams-guest-calling-setting.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Foretag private opkald|På|Når **Slået** til, kan gæster foretage peer-to-peer-opkald i Teams. Når **De er slået fra**, kan de ikke.|

### <a name="guest-meeting"></a>Gæstemøde

**Navigation:** [Teams Administration](https://admin.teams.microsoft.com) > **Indstillinger for** >  hele organisationen <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**Gæsteadgang**</a>

![Skærmbillede af indstillinger for Teams-gæstemøde.](../media/teams-guest-meeting-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Tillad IP-video|På|Når **Den er slået til**, kan gæster bruge video i deres opkald og møder. Når **De er slået fra**, kan de ikke.|
|Skærmdelingstilstand|Hele skærmen|Når **deaktiveret**, kan gæster ikke dele deres skærme i Teams. Når indstillingen er angivet til **Enkelt program**, kan gæster kun dele et enkelt program på deres skærm. Når indstillingen er angivet til **Hele skærmen**, kan gæster vælge at dele et program eller hele deres skærm.|
|Tillad møde nu|På|Når **Den er slået** til, kan gæster bruge funktionen Møde nu i Teams. Når **De er slået fra**, kan de ikke.|

### <a name="guest-messaging"></a>Gæstebeskeder

**Navigation:** [Teams Administration](https://admin.teams.microsoft.com) > **Indstillinger for** >  hele organisationen <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**Gæsteadgang**</a>

![Skærmbillede af indstillinger for Teams-gæstebeskeder.](../media/teams-guest-messaging-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Rediger sendte meddelelser|På|Når **Slået til**, kan gæster redigere meddelelser, de tidligere har sendt. Når **De er slået fra**, kan de ikke.|
|Slet sendte meddelelser|På|Når **Slået til**, kan gæster slette meddelelser, de tidligere har sendt. Når **De er slået fra**, kan de ikke.|
|Chat|På|Når **Slået til**, kan gæster bruge chat i Teams. Når **De er slået fra**, kan de ikke.|
|Brug Giphys i samtaler|På|Når **Den er Slået** til, kan gæsterne bruge Giphys i samtaler. Når **De er slået fra**, kan de ikke.|
|Giphy-indholdsklassifikation|Moderat|Når indstillingen er angivet til **Tillad alt indhold**, kan gæster indsætte alle Giphys i chats, uanset indholdsklassifikationen. Når den er indstillet til **Moderate** gæster kan indsætte Giphys i chats, men vil være moderat begrænset fra indhold for voksne. Når indstillingen er angivet til **Strict** , kan gæster indsætte Giphys i chats, men de kan ikke indsætte indhold fra voksne.|
|Brug Memes i samtaler|På|Når **Du er Slået til**, kan gæster bruge memes i samtaler. Når **De er slået fra**, kan de ikke.|
|Brugerklistermærker i samtaler|På|Når **Den er slået til**, kan gæsterne bruge klistermærker i samtaler; Når **De er slået fra**, kan de ikke.|
|Tillad moderne læser til visning af meddelelser|På|Når **Slået til**, kan gæster få vist meddelelser i Forenklet læser. Når de er **slået fra**, kan de ikke.|

## <a name="sharepoint-and-onedrive-organization-level"></a>SharePoint og OneDrive (på organisationsniveau)

**Administration rolle:** SharePoint-administrator

Disse indstillinger påvirker alle websteder i organisationen. De påvirker ikke Microsoft 365-grupper eller Teams direkte, men vi anbefaler, at du tilpasser disse indstillinger til indstillingerne for Microsoft 365-grupper og Teams for at undgå problemer med brugeroplevelsen. Hvis gæstedeling f.eks. er tilladt i Teams, men ikke SharePoint, har gæster i Teams ikke adgang til fanen Filer, fordi Teams-filer er gemt i SharePoint.

### <a name="sharepoint-and-onedrive-sharing-settings"></a>Delingsindstillinger for SharePoint og OneDrive

Da OneDrive er et hierarki af websteder i SharePoint, påvirker delingsindstillingerne på organisationsniveau OneDrive direkte på samme måde som andre SharePoint-websteder.

**Navigation:** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a> af **> politikker** >  i SharePoint Administration

![Skærmbillede af SharePoint-indstillinger for deling på organisationsniveau.](../media/sharepoint-organization-external-sharing-controls.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|SharePoint|Nogen|Angiver de mest tilladte delingstilladelser for SharePoint-websteder.|
|OneDrive|Nogen|Angiver de mest tilladte delingstilladelser for OneDrive-websteder. Denne indstilling kan ikke være mere eftergivende end SharePoint-indstillingen.|

### <a name="sharepoint-and-onedrive-advanced-sharing-settings"></a>Avancerede delingsindstillinger for SharePoint og OneDrive

**Navigation:** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a> af **> politikker** >  i SharePoint Administration

![Skærmbillede af yderligere delingsindstillinger på organisationsniveau i SharePoint.](../media/external-sharing.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Begræns ekstern deling efter domæne|Ud|Denne indstilling giver dig mulighed for at angive en liste over tilladte eller blokerede domæner til deling. Når der er angivet tilladte domæner, kan invitationer til deling kun sendes til disse domæner. Når der er angivet domæner, der afvises, kan invitationer til deling ikke sendes til disse domæner. <p> Denne indstilling påvirker alle SharePoint- og OneDrive-websteder i organisationen.|
|Tillad kun, at brugere i bestemte sikkerhedsgrupper deler eksternt|Ud|Hvis du vil begrænse, hvem der kan dele med gæster i SharePoint og OneDrive, kan du gøre det ved at begrænse deling til personer i angivne sikkerhedsgrupper. Disse indstillinger påvirker ikke deling via Microsoft 365-grupper eller Teams. Gæster, der inviteres via en gruppe eller et team, vil også have adgang til det tilknyttede websted, selvom dokument- og mappedeling kun kan udføres af personer i de angivne sikkerhedsgrupper. <p> For hver angivet gruppe kan du vælge, hvilken af disse brugere der kan dele med alle-links.|
|Gæster skal logge på med den samme konto, som invitationer til deling sendes til|Ud|Forhindrer gæster i at indløse invitationer til deling af websteder ved hjælp af en anden mailadresse, end invitationen blev sendt til. <p> [SharePoint- og OneDrive-integration med Azure AD B2B (prøveversion)](/sharepoint/sharepoint-azureb2b-integration-preview) bruger ikke denne indstilling, fordi alle gæster føjes til mappen baseret på den mailadresse, som invitationen blev sendt til. Alternative mailadresser kan ikke bruges til at få adgang til webstedet.|
|Giv gæster tilladelse til at dele elementer, de ikke ejer|På|Når **Slået til**, kan gæster dele elementer, som de ikke ejer, med andre brugere eller gæster. når **Off** de ikke kan. Gæster kan altid dele elementer, som de har fuld kontrol over.|
|Personer, der bruger en bekræftelseskode, skal godkende igen efter dette antal dage|Ud|Denne indstilling giver dig mulighed for at kræve, at brugere, der godkender med en engangskode, skal godkende igen efter et bestemt antal dage.|
|Gæsteadgang til et websted eller OneDrive udløber automatisk efter dette antal dage|På|Hvis administratoren har angivet en udløbstid for gæsteadgang, får hver gæst, du inviterer til webstedet, eller som du deler individuelle filer og mapper med, adgang i et bestemt antal dage. Du kan finde flere oplysninger under [Administrer gæsteudløb for et websted](https://support.microsoft.com/en-us/office/manage-guest-expiration-for-a-site-25bee24f-42ad-4ee8-8402-4186eed74dea)

### <a name="sharepoint-and-onedrive-file-and-folder-link-settings"></a>Indstillinger for fil- og mappelink til SharePoint og OneDrive

Når filer og mapper deles i SharePoint og OneDrive, sendes der et link med tilladelser til filen eller mappen til delingsmodtagere i stedet for at få direkte adgang til selve filen eller mappen. Der er flere typer links tilgængelige, og du kan vælge den standardlinktype, der vises for brugerne, når de deler en fil eller mappe. Du kan også angive tilladelser og udløbsindstillinger for *alle* links.

**Navigation:** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a> af **> politikker** >  i SharePoint Administration

![Skærmbillede af SharePoint-indstillinger for deling af filer og mapper på organisationsniveau.](../media/sharepoint-organization-files-folders-sharing-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Fil- og mappelinks|Alle med linket|Angiver, hvilket delingslink der vises som standard, når en bruger deler en fil eller mappe. Brugerne kan ændre indstillingen, før de deler, hvis de vil. Hvis standardindstillingen er angivet til **Alle med linket** , og *Deling af alle* ikke er tilladt for et bestemt websted, er det **kun personer i organisationen** , der vises som standard for det pågældende websted.|
|Disse links skal udløbe inden for dette antal dage|Fra (ingen udløb)|Angiver antallet af dage, efter at der er oprettet et link af typen *Alle* , som det udløber. Udløbne links kan ikke fornys. Opret et nyt link, hvis du har brug for at fortsætte delingen efter udløbet.|
|Filtilladelser|Få vist og rediger|Angiver de filtilladelsesniveauer, der er tilgængelige for brugerne, når de opretter et link af *typen Alle* . Hvis **Vis** er valgt, kan brugerne kun oprette *links til alle* filer med visningstilladelser. Hvis **Vis og rediger** er valgt, kan brugerne vælge mellem visnings- og visnings- og redigeringstilladelser, når de opretter linket.|
|Mappetilladelser|Få vist, rediger og upload|Angiver de mappetilladelsesniveauer, der er tilgængelige for brugerne, når de opretter et link til *alle* . Hvis **Vis** er valgt, kan brugerne kun oprette links til *mappen Alle* med visningstilladelser. Hvis **Vis, rediger og upload** er valgt, kan brugerne vælge mellem visnings- og visnings-, redigerings- og uploadtilladelser, når de opretter linket.|

## <a name="sharepoint-site-level"></a>SharePoint (webstedsniveau)

**Administration rolle:** SharePoint-administrator

Da disse indstillinger er underlagt indstillingerne for hele organisationen for SharePoint, kan den effektive indstilling for deling for webstedet blive ændret, hvis indstillingen på organisationsniveau ændres. Hvis du vælger en indstilling her, og organisationsniveauet senere er angivet til en mere restriktiv værdi, fungerer dette websted på den mere restriktive værdi. Hvis du f.eks. vælger **Nogen** , og indstillingen på organisationsniveau senere er angivet til **Nye og eksisterende gæster**, tillader dette websted kun nye og eksisterende gæster. Hvis indstillingen på organisationsniveau derefter er indstillet til **Alle**, tillader dette websted igen *alle* links.

### <a name="site-sharing"></a>Deling af websted

Du kan angive tilladelser til gæstedeling for hvert websted i SharePoint. Denne indstilling gælder for både webstedsdeling og fil- og mappedeling. (*Alle, der* deler, er ikke tilgængelige for deling af websteder. Hvis du vælger **Nogen**, kan brugerne dele filer og mapper ved hjælp af Links til *alle* og selve webstedet med nye og eksisterende gæster.

Hvis der er anvendt en følsomhedsmærkat på webstedet, kan denne mærkat styre indstillingerne for ekstern deling. Du kan finde flere oplysninger under [Brug følsomhedsmærkater til at beskytte indhold i Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Delingsindstillinger for kanalwebsteder kan kun ændres ved hjælp af [PowerShell-cmdlet'en Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) .

**Navigation:** SharePoint Administration > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> > vælge fanen **> Politikker** > **Rediger ekstern deling**

![Skærmbillede af indstillinger for ekstern deling på SharePoint-webstedet.](../media/sharepoint-site-external-sharing-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Webstedsindhold kan deles med|Varierer efter webstedstype (se tabellen nedenfor)|Angiver den type ekstern deling, der er tilladt for dette websted. De indstillinger, der er tilgængelige her, er underlagt indstillingerne for deling på organisationsniveau for SharePoint.|

### <a name="site-file-and-folder-link-settings"></a>Indstillinger for webstedsfil og mappelink

Du kan angive standarder for linktype og -tilladelser samt udløbsindstillinger for *alle* links for hvert websted. Når disse indstillinger er angivet på webstedsniveau, tilsidesætter de indstillingerne på organisationsniveau. Bemærk, at hvis *Nogen* links er deaktiveret på organisationsniveau, vil *Alle* ikke være en tilgængelig linktype på webstedsniveau.

**Navigation:** SharePoint Administration > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> > vælge fanen **> Politikker** > **Rediger ekstern deling**

![Skærmbillede af indstillinger for deling af links på SharePoint-webstedsniveau.](../media/sharepoint-site-link-sharing-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Begræns deling efter domæne|Ud|Denne indstilling giver dig mulighed for at angive en liste over tilladte eller blokerede domæner til deling. Når der er angivet tilladte domæner, kan invitationer til deling kun sendes til disse domæner. Når der er angivet domæner, der afvises, kan invitationer til deling ikke sendes til disse domæner. <p> Denne indstilling kan ikke bruges til at tilsidesætte domænebegrænsninger, der er angivet på organisationsniveau eller Azure AD niveau.|
|Standardtype for delingslink|Samme som indstilling på organisationsniveau|Denne indstilling giver dig mulighed for at angive det standardlink til deling, der vises for brugerne på dette websted. Indstillingen *Samme som indstilling på organisationsniveau* er defineret af en kombination af indstillinger for organisations- og webstedsdeling.|
|Avancerede indstillinger for links til alle|Samme som indstilling på organisationsniveau|Angiver antallet af dage, efter at der er oprettet et link af typen *Alle* for en fil på dette websted, som det udløber. Udløbne links kan ikke fornys. Opret et nyt link, hvis du har brug for at fortsætte delingen efter udløbet.|
|Standardlinktilladelse|Samme som indstilling på organisationsniveau|Denne indstilling giver dig mulighed for at angive standardtilladelsen (Vis eller Rediger) til deling af links, der er oprettet til filer på dette websted.|

### <a name="default-site-sharing-settings"></a>Standardindstillinger for webstedsdeling

I nedenstående tabel vises standardindstillingen for deling for hver webstedstype.

| Webstedstype | Standardindstilling for deling |
|:-----|:-----|
|Classic|**Kun personer i din organisation**|
|OneDrive|**Nogen**|
|Gruppeforbundne websteder (herunder Teams)|**Nye og eksisterende gæster**, hvis indstillingen Microsoft 365-grupper **Lad gruppeejere føje personer uden for organisationen til grupper** er **Slået** til. Ellers er **kun eksisterende gæster**|
|Kommunikation|**Kun personer i din organisation**|
|Moderne websteder uden gruppe (#STS3 TeamSite)|**Kun personer i din organisation**|

> [!NOTE]
> Rodkommunikationswebstedet (tenant-name.sharepoint.com) har standardindstillingen for deling for **Alle**.

## <a name="see-also"></a>Se også

[Oversigt over ekstern deling af SharePoint og OneDrive](/sharepoint/external-sharing-overview)

[Gæsteadgang i Microsoft Teams](/MicrosoftTeams/guest-access)

[Tilføjelse af gæster til Microsoft 365-grupper](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)
