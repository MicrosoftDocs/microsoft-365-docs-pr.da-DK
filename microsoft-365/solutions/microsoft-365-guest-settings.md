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
description: Få mere at vide om de indstillinger for gæstedeling, der er tilgængelige Microsoft 365, der kan påvirke deling med personer uden for organisationen.
ms.openlocfilehash: 9cb6eb52c523bba624af5f830c3c34c4edaf86b8
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594834"
---
# <a name="microsoft-365-guest-sharing-settings-reference"></a>Reference for Microsoft 365-gæstedelingsindstillinger

Denne artikel indeholder en reference til de forskellige indstillinger, der kan påvirke deling med personer uden for organisationen i forbindelse med Microsoft 365-arbejdsbelastninger: Teams, Microsoft 365-grupper, SharePoint og OneDrive. Disse indstillinger findes i Azure Active Directory, Microsoft 365, Teams og SharePoint Administration.

## <a name="azure-active-directory"></a>Azure Active Directory

**Administratorrolle:** Global administrator

Azure Active Directory er den katalogtjeneste, der bruges af Microsoft 365. Indstillingerne Azure Active Directory organisationsrelationer påvirker direkte deling i Teams, Microsoft 365-grupper, SharePoint og OneDrive.

> [!NOTE]
> Disse indstillinger påvirker kun SharePoint når [SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) er blevet konfigureret. Nedenstående tabel forudsætter, at dette er konfigureret.

### <a name="external-collaboration-settings"></a>Indstillinger for eksternt samarbejde

**Navigation:** [Azure Active Directory Administration > Azure Active Directory >](https://aad.portal.azure.com) eksterne identiteter > indstillinger for eksternt samarbejde

![Skærmbillede af Azure Active Directory siden Organisationsrelationer Indstillinger organisationsrelationer.](../media/azure-ad-organizational-relationships-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Gæstebrugeradgang|Gæstebrugere har begrænset adgang til egenskaber og medlemskaber af katalogobjekter|Bestemmer de [tilladelser, som gæster har i Azure Active Directory](/azure/active-directory/fundamentals/users-default-permissions).|
|Indstillinger for gæste inviterer|Alle i organisationen kan invitere gæstebrugere, herunder gæster og ikke-administratorer|Afgør, om gæster, medlemmer og administratorer kan invitere gæster til organisationen. <p> Denne indstilling påvirker Microsoft 365, f.eks. deling Teams og SharePoint.|
|Aktivér tilmelding via selvbetjening for gæster via brugerflows|Nej|Bestemmer, om du kan oprette brugerflows, der giver nogen mulighed for at tilmelde sig en app, som du har oprettet, og oprette en ny gæstekonto.|
|Begrænsninger for samarbejde|Tillad, at invitationer sendes til et domæne|Med denne indstilling kan du angive en liste over tilladte eller blokerede domæner til deling. Når tilladte domæner er angivet, kan delingsinvitationer kun sendes til disse domæner. Når nægtede domæner er angivet, kan invitationer til deling ikke sendes til disse domæner. <p> Denne indstilling påvirker Microsoft 365, f.eks. deling Teams og SharePoint. Du kan tillade eller blokere domæner på et mere detaljeret niveau ved hjælp af domænefiltrering i SharePoint eller Teams.|

Disse indstillinger påvirker, hvordan brugere inviteres til kataloget. De påvirker ikke deling med gæster, der allerede findes i kataloget.

## <a name="microsoft-365"></a>Microsoft 365

**Administratorrolle:** Global administrator

Den Microsoft 365 Administration har indstillinger på organisationsniveau for deling og for Microsoft 365-grupper.

### <a name="sharing"></a>Deling

**Navigation:** [Microsoft 365 Administration](https://admin.microsoft.com) >  **Indstillinger** >  **Org settingsSecurity** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2072756" target="_blank">**& fanen Beskyttelse af** personlige oplysningerDeling</a> > .

![Skærmbillede af indstillingen for gæstedeling for sikkerhed og beskyttelse af personlige oplysninger i Microsoft 365 Administration.](../media/sharepoint-security-privacy-sharing-setting.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Lad brugere føje nye gæster til organisationen|Til|Når den er **indstillet til** Ja, kan Azure AD-medlemmer invitere gæster via Azure AD. når den er **indstillet til Nej**, kan de ikke. Når den er indstillet til **Ja, kan** Microsoft 365-gruppemedlemmer invitere gæster med ejergodkendelse. Når den er indstillet til **Nej, kan** Microsoft 365-gruppemedlemmer invitere gæster med ejergodkendelse, men ejere skal være globale administratorer for at godkende. <p> Bemærk, **at medlemmer kan** invitere henviser til medlemmer i Azure AD (i modsætning til gæster) og ikke til websteds- eller gruppemedlemmer i Microsoft 365. <p> Dette er identisk med **indstillingen Medlemmer kan invitere** Azure Active Directory indstillingerne for organisationsrelationer.|

### <a name="microsoft-365-groups"></a>Microsoft 365-grupper

**Navigation:** [Microsoft 365 Administration](https://admin.microsoft.com) >  **Indstillinger** >  **Org-indstillinger** > Microsoft 365-grupper

![Skærmbillede Microsoft 365-grupper af indstillingerne for gæster i Microsoft 365 Administration.](../media/office-365-groups-guest-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Lad gruppemedlemmer uden for organisationen få adgang til gruppeindhold|Til|Når den er **indstillet til Til**, kan gæster få adgang til gruppeindhold; når indstillet **til Fra**, kan de ikke. Denne indstilling skal være **Til** i alle scenarier, hvor gæster interagerer med Microsoft 365-grupper eller Teams.|
|Lad gruppeejere føje personer uden for organisationen til grupper|Til|Når **den er** til, Microsoft 365-grupper eller Teams invitere nye gæster til gruppen. Når **de er** slået Fra, kan de ikke. Denne indstilling skal være **Til** i alle scenarier, hvor gæster skal føjes til grupper.|

Disse indstillinger er på organisationsniveau. Se [Opret indstillinger for en bestemt gruppe for at](/azure/active-directory/users-groups-roles/groups-settings-cmdlets#create-settings-for-a-specific-group) få oplysninger om, hvordan du ændrer disse indstillinger på gruppeniveau ved hjælp af PowerShell.

## <a name="teams"></a>Teams

Kontakten Teams for gæsteadgang, Tillad gæsteadgang **i Teams**, skal være **til, for** at de andre gæsteindstillinger er tilgængelige.

**Administratorrolle:** Teams tjenesteadministrator

### <a name="guest-access"></a>Gæsteadgang

**Navigation:** Teams **administrationOrg-indstillinger**[](https://admin.teams.microsoft.com) >  For hele <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**sidenGuest-adgang**</a> > 

![Skærmbillede af Teams til/fra-knap for gæsteadgang.](../media/teams-guest-access-toggle.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Tillad gæsteadgang i Teams|Fra|Slår gæsteadgang til eller fra for alle Teams gæster. Det kan tage 24 timer, før denne indstilling er blevet ændret.|

### <a name="guest-calling"></a>Gæsteopkald

**Navigation:** Teams **administrationOrg-indstillinger**[](https://admin.teams.microsoft.com) >  For hele <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**sidenGuest-adgang**</a> > 

![Skærmbillede af Teams indstillinger for gæsteopkald.](../media/teams-guest-calling-setting.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Foretag private opkald|Til|Når **den er** slået Til, kan gæster foretage peer-to-peer-opkald i Teams, men når **slået** Fra, kan de ikke.|

### <a name="guest-meeting"></a>Gæstemøde

**Navigation:** Teams **administrationOrg-indstillinger**[](https://admin.teams.microsoft.com) >  For hele <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**sidenGuest-adgang**</a> > 

![Skærmbillede Teams indstillingerne for gæstemøder.](../media/teams-guest-meeting-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Tillad IP-video|Til|Når **den er** til, kan gæster bruge video i deres opkald og møder; når **Deaktiveret**, kan de ikke.|
|Skærmdelingstilstand|Hele skærmen|Når **det er** deaktiveret, kan gæster ikke dele deres skærme Teams. Når den er **indstillet til** enkelt applikation, kan gæster kun dele et enkelt program på deres skærm. Når den er **indstillet til** Hele skærmen, kan gæster vælge at dele et program eller hele deres skærm.|
|Tillad Møde nu|Til|Når **den er** slået Til, kan gæster bruge funktionen Møde nu i Teams, men **når de er** slået Fra, kan de ikke.|

### <a name="guest-messaging"></a>Gæstebeskeder

**Navigation:** Teams **administrationOrg-indstillinger**[](https://admin.teams.microsoft.com) >  For hele <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**sidenGuest-adgang**</a> > 

![Skærmbillede Teams indstillingerne for gæstemeddelelser.](../media/teams-guest-messaging-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Rediger sendte meddelelser|Til|Når **den er** til, kan gæster redigere meddelelser, de tidligere har sendt. når **Deaktiveret**, kan de ikke.|
|Slet sendte meddelelser|Til|Når **den er** til, kan gæster slette meddelelser, de tidligere har sendt. når **Deaktiveret**, kan de ikke.|
|Chat|Til|Når **den er** slået Til, kan gæster bruge chat i Teams, når **de** er slået Fra, men det kan de ikke.|
|Brug Giphys i samtaler|Til|Når **den er** til, kan gæster bruge Giphys i samtaler; når **Deaktiveret**, kan de ikke.|
|Giphy-indholdsbedømmelse|Moderat|Når den er **indstillet til Tillad** alt indhold, kan gæster indsætte alle Giphys i chats, uanset indholdsbedømmelse. Når den er **indstillet** til Moderat, kan gæster indsætte Giphys i chats, men begrænses moderat fra indhold beregnet for voksne. Når den er **indstillet** til Streng, kan gæster indsætte Giphys i chats, men vil være begrænset fra at indsætte indhold beregnet for voksne.|
|Brug Memes i samtaler|Til|Når **den er** til, kan gæster bruge memes i samtaler; når **Deaktiveret**, kan de ikke.|
|Brugermærkater i samtaler|Til|Når **den er** til, kan gæster bruge klistermærker i samtaler; når **Deaktiveret**, kan de ikke.|
|Tillad Forenklet læser til visning af meddelelser|Til|Når **den er** slået Til, kan gæster se meddelelser Forenklet læser meddelelser, men **når de** er slået Fra, kan de ikke.|

## <a name="sharepoint-and-onedrive-organization-level"></a>SharePoint og OneDrive (organisationsniveau)

**Administratorrolle:** SharePoint administrator

Disse indstillinger påvirker alle websteder i organisationen. De påvirker ikke Microsoft 365-grupper eller Teams direkte, men vi anbefaler, at du justerer disse indstillinger efter indstillingerne for Microsoft 365-grupper og Teams for at undgå problemer med brugeroplevelsen. (Hvis gæstedeling f.eks. er tilladt i Teams men ikke i SharePoint, så har gæster i Teams ikke adgang til fanen Filer, fordi Teams-filer gemmes i SharePoint).

### <a name="sharepoint-and-onedrive-sharing-settings"></a>SharePoint og OneDrive indstillinger for deling

Da OneDrive er et hierarki af websteder i SharePoint, påvirker indstillingerne for deling på organisationsniveau direkte OneDrive samme måde, som de gør andre SharePoint websteder.

**Navigation:** SharePoint Administration > **Omdeling** >  <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**af politikker**</a>

![Skærmbillede af SharePoint af indstillinger for deling på organisationsniveau.](../media/external-sharing.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|SharePoint|Alle|Angiver de mest tilladelsesfulde delingstilladelser til SharePoint websteder.|
|OneDrive|Alle|Angiver de mest tilladelsesfulde delingstilladelser for OneDrive websteder. Denne indstilling kan ikke være mere tilladelig end SharePoint indstilling.|

### <a name="sharepoint-and-onedrive-advanced-sharing-settings"></a>SharePoint og OneDrive avancerede indstillinger for deling

**Navigation:** SharePoint Administration > **Omdeling** >  <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**af politikker**</a>

![Skærmbillede af SharePoint af flere delingsindstillinger på organisationsniveau.](../media/external-sharing.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Begræns ekstern deling efter domæne|Fra|Med denne indstilling kan du angive en liste over tilladte eller blokerede domæner til deling. Når tilladte domæner er angivet, kan delingsinvitationer kun sendes til disse domæner. Når nægtede domæner er angivet, kan invitationer til deling ikke sendes til disse domæner. <p> Denne indstilling påvirker alle SharePoint og OneDrive websteder i organisationen.|
|Tillad kun brugere i bestemte sikkerhedsgrupper at dele eksternt|Fra|Hvis du vil begrænse, hvem der kan dele med gæster i SharePoint og OneDrive, kan du gøre det ved at begrænse deling til personer i bestemte sikkerhedsgrupper. Disse indstillinger påvirker ikke deling via Microsoft 365-grupper eller Teams. Gæster, der inviteres via en gruppe eller et team, har også adgang til det tilknyttede websted, selvom dokument- og mappedeling kun kan udføres af personer i de angivne sikkerhedsgrupper. <p> For hver angivet gruppe kan du vælge, hvilke af disse brugere der kan dele med Alle-links.|
|Gæster skal logge på med den samme konto, som invitationer til deling sendes til|Fra|Forhindrer gæster i at indløse invitationer til webstedsdeling med en anden mailadresse end invitationen blev sendt til. <p> [SharePoint og OneDrive-integration med Azure AD B2B (Preview)](/sharepoint/sharepoint-azureb2b-integration-preview) bruger ikke denne indstilling, da alle gæster føjes til kataloget baseret på den mailadresse, invitationen blev sendt til. Alternative mailadresser kan ikke bruges til at få adgang til webstedet.|
|Tillad gæster at dele elementer, de ikke ejer|Til|Når **den er** på, kan gæster dele elementer, de ikke ejer, med andre brugere eller gæster. når **Fra kan** de ikke. Gæster kan altid dele elementer, de har fuld kontrol over.|
|Personer, der bruger en bekræftelseskode, skal genautate efter dette antal dage|Fra|Med denne indstilling kan du kræve, at brugere, der godkender med en engangs adgangskode, skal genautatere efter et bestemt antal dage.|
|Gæsteadgang til et websted eller OneDrive udløber automatisk efter dette antal dage|Til|Hvis administratoren har angivet et udløbstidspunkt for gæsteadgang, vil hver gæst, som du inviterer til webstedet, eller som du deler individuelle filer og mapper med, få adgang til dem i et bestemt antal dage. Hvis du vil have mere at vide, [skal du gå til Administrer gæsteudløb for et websted](https://support.microsoft.com/en-us/office/manage-guest-expiration-for-a-site-25bee24f-42ad-4ee8-8402-4186eed74dea)

### <a name="sharepoint-and-onedrive-file-and-folder-link-settings"></a>SharePoint og OneDrive fil- og mappelinkindstillinger

Når filer og mapper deles i SharePoint og OneDrive, sendes et link med tilladelser til filen eller mappen i stedet for at få direkte adgang til selve filen eller mappen. Der findes flere typer links, og du kan vælge den standardlinktype, der vises til brugerne, når de deler en fil eller mappe. Du kan også angive tilladelser og udløbsindstillinger for *alle links* .

**Navigation:** SharePoint Administration > **Omdeling** >  <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**af politikker**</a>

![Skærmbillede af SharePoint af filer og mapper på organisationsniveau.](../media/sharepoint-organization-files-folders-sharing-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Fil- og mappelinks|Alle med linket|Angiver, hvilket delingslink der vises som standard, når en bruger deler en fil eller mappe. Brugere kan ændre indstillingen før deling, hvis de ønsker det. Hvis standardindstillingen er angivet til Alle med **linket**,  og Alle, der deler ikke er tilladt for et bestemt  websted, vises Kun personer i organisationen som standard for webstedet.|
|Disse links skal udløbe inden for dette antal dage|Fra (ingen udløb)|Angiver antallet af dage, efter et *Alle-link* er oprettet, som det udløber. Udløbne links kan ikke fornyes. Opret et nyt link, hvis du har brug for at fortsætte med at dele efter udløb.|
|Filtilladelser|Få vist og rediger|Angiver de filtilladelsesniveauer, der er tilgængelige for brugerne, når de opretter et *Alle-link* . Hvis **Vis** er markeret, kan brugerne kun oprette *Alle fillinks* med visningstilladelser. Hvis **Vis og rediger er** markeret, kan brugerne vælge mellem visnings- og visnings- og redigeringstilladelser, når de opretter linket.|
|Mappetilladelser|Få vist, rediger og overfør|Angiver de mappetilladelsesniveauer, der er tilgængelige for brugere, når de opretter et *Alle-link* . Hvis **Vis** er markeret, kan brugerne kun oprette *Alle-mappelinks* med visningstilladelser. Hvis **Vis, rediger og upload** er markeret, kan brugerne vælge mellem visnings-, redigerings- og uploadtilladelser, når de oprette linket.|

## <a name="sharepoint-site-level"></a>SharePoint (webstedsniveau)

**Administratorrolle:** SharePoint administrator

Da disse indstillinger er underlagt indstillingerne for hele organisationen for SharePoint, kan den effektive indstilling for deling af webstedet blive ændret, hvis indstillingen på organisationsniveau ændres. Hvis du vælger en indstilling her, og organisationsniveau senere angives til en mere restriktiv værdi, vil webstedet fungere på denne mere restriktive værdi. Hvis du f.eks **. vælger** Alle, og indstillingen på organisationsniveau senere angives til Ny og eksisterende **gæster, så** vil dette websted kun tillade nye og eksisterende gæster. Hvis indstillingen på organisationsniveau derefter er indstillet tilbage til **Alle**, tillader dette websted igen *Alle* links.

### <a name="site-sharing"></a>Webstedsdeling

Du kan angive tilladelser for gæstedeling for hvert websted SharePoint. Denne indstilling gælder både deling af websteder og fil- og mappedeling. Alle *, der* deler, er ikke tilgængelige for deling af websteder. Hvis du vælger **Alle**, kan brugerne dele filer og mapper ved hjælp *af Alle-links* og selve webstedet med nye og eksisterende gæster.

Hvis der er anvendt et følsomhedsmærkat på webstedet, styrer etiketten muligvis indstillingerne for ekstern deling. Få mere at vide under [Brug følsomhedsmærkater til at beskytte indhold Microsoft Teams, Microsoft 365, grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Indstillinger for deling af kanalwebsteder kan kun ændres ved hjælp af [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) PowerShell-cmdlet'en.

**Navigation:** SharePoint Administration > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**aktive websteder**</a> > vælge fanen > **Politikker** > **Rediger ekstern deling**

![Skærmbillede af SharePoint indstillingerne for ekstern deling på webstedet.](../media/sharepoint-site-external-sharing-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Webstedsindhold kan deles med|Varierer efter webstedstype (se tabellen nedenfor)|Angiver typen af ekstern deling, der er tilladt for dette websted. De indstillinger, der er tilgængelige her, er underlagt indstillingerne for deling på organisationsniveau for SharePoint.|

### <a name="site-file-and-folder-link-settings"></a>Indstillinger for link til webstedsfil og mappe

Du kan angive standarder for linktype og -tilladelser samt udløbsindstillinger for *Alle-links* for hvert websted. Når de er indstillet på webstedsniveau, tilsidesætter disse indstillinger indstillingerne på organisationsniveau. Bemærk, at *hvis Alle* links er deaktiveret på *organisationsniveau,* vil Alle ikke være en tilgængelig linktype på webstedsniveau.

**Navigation:** SharePoint Administration > <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**aktive websteder**</a> > vælge fanen > **Politikker** > **Rediger ekstern deling**

![Skærmbillede af SharePoint af indstillinger for deling af links på webstedsniveau.](../media/sharepoint-site-link-sharing-settings.png)

| Indstilling | Standard | Beskrivelse |
|:-----|:-----|:-----|
|Begræns deling efter domæne|Fra|Med denne indstilling kan du angive en liste over tilladte eller blokerede domæner til deling. Når tilladte domæner er angivet, kan delingsinvitationer kun sendes til disse domæner. Når nægtede domæner er angivet, kan invitationer til deling ikke sendes til disse domæner. <p> Denne indstilling kan ikke bruges til at tilsidesætte domænebegrænsninger, der er angivet på organisationsniveau eller Azure AD-niveau.|
|Standardtype for delingslink|Samme som indstilling på organisationsniveau|Med denne indstilling kan du angive det standardlink til deling, som brugerne på dette websted får vist. Indstillingen *Samme som indstilling på organisationsniveau* defineres ved hjælp af en kombination af indstillinger for organisations- og webstedsdeling.|
|Avancerede indstillinger for alle links|Samme som indstilling på organisationsniveau|Angiver antallet af dage, efter der oprettes *et Alle-link* for en fil på dette websted, som det udløber. Udløbne links kan ikke fornyes. Opret et nyt link, hvis du har brug for at fortsætte med at dele efter udløb.|
|Standardtilladelse for link|Samme som indstilling på organisationsniveau|Med denne indstilling kan du angive standardtilladelsen (Vis eller Rediger) for deling af links, der er oprettet for filer på dette websted.|

### <a name="default-site-sharing-settings"></a>Standardindstillinger for webstedsdeling

Tabellen nedenfor viser standardindstillingen for deling for hver webstedstype.

| Webstedstype | Standardindstilling for deling |
|:-----|:-----|
|Classic|**Kun personer i din organisation**|
|OneDrive|**Alle**|
|Gruppeforbundne websteder (herunder Teams)|**Nye og eksisterende gæster**, hvis indstillingen Microsoft 365-grupper **Lad gruppeejere** føje personer uden for organisationen til grupper er **til,** ellers **er Kun eksisterende gæster**|
|Kommunikation|**Kun personer i din organisation**|
|Moderne websteder uden nogen gruppe (#STS3 TeamSite)|**Kun personer i din organisation**|

> [!NOTE]
> Rodwebstedet (tenant-name.sharepoint.com) har en standardindstilling for deling af **Alle**.

## <a name="see-also"></a>Se også

[SharePoint og OneDrive oversigt over ekstern deling](/sharepoint/external-sharing-overview)

[Gæsteadgang i Microsoft Teams](/MicrosoftTeams/guest-access)

[Tilføjelse af gæster til Microsoft 365-grupper](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)
