---
title: Om Microsoft 365 forbrugsanalyse
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
ms.assetid: 77ff780d-ab19-4553-adea-09cb65ad0f1f
description: Få et overblik over, hvordan din organisation anvender Microsoft 365 tjenester til at kommunikere og samarbejde.
ms.openlocfilehash: 92a6b1437fa092b54df5e10a6593d130e0808164
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65467948"
---
# <a name="microsoft-365-usage-analytics"></a>Microsoft 365 forbrugsanalyse

Brug Microsoft 365 forbrugsanalyse i Power BI til at få indsigt i, hvordan din organisation bruger de forskellige tjenester i Microsoft 365. Du kan visualisere og analysere Microsoft 365 forbrugsdata, oprette brugerdefinerede rapporter og dele indsigten i din organisation. Du kan også få indsigt i, hvordan bestemte områder eller afdelinger bruger Microsoft 365.
  
Microsoft 365 brugsanalyse giver dig adgang til et færdigbygget dashboard, der giver en visning på tværs af produkter for de sidste 12 måneder og indeholder en række færdigbyggede rapporter. Hver rapport giver dig specifik indsigt i forbrug. Brugerspecifikke oplysninger er tilgængelige for den sidste hele kalendermåned.
  
Den [datamodel](usage-analytics-data-model.md) , der driver skabelonappen, indeholder brugerattributter fra Active Directory, hvilket gør det muligt at pivotere i visse rapporter. Følgende Active Directory-attributter er inkluderet: placering, afdeling og organisation. 
  
Se [Aktivér Microsoft 365 forbrugsanalyse](enable-usage-analytics.md) for at begynde at indsamle data. 
  
Microsoft 365 indeholder en række rapporter, der er beskrevet i følgende afsnit. 

Du kan få adgang til detaljerede rapporter for hvert område ved at vælge datatabellerne. Du kan få vist alle færdigbyggede rapporter ved at vælge fanerne nederst på webstedet. Hvis du vil have mere detaljerede instruktioner, skal du læse [Navigering og brug af rapporterne](navigate-and-utilize-reports.md) og [Tilpasning af rapporterne](customize-reports.md).

## <a name="executive-summary"></a>Resumé

Resumeet af hovedopgaven er et overblik over Microsoft 365 for virksomheder, anvendelse, mobilitet, kommunikation, samarbejde og lagerrapporter og er beregnet til beslutningstagere i virksomheden. Den giver et overblik over, hvordan nogle individuelle tjenester bruges, baseret på alle de brugere, der er blevet aktiveret, og dem, der er aktive. Alle værdier i måneden, der vises i rapporten, refererer til den seneste hele måned. 

I denne oversigt kan du hurtigt forstå brugsmønstre i Office, og hvordan og hvor dine medarbejdere samarbejder.

![Billede af oversigt over brug af Microsoft 365.](../../media/office365usage-exec-summary.png)

## <a name="overview"></a>Oversigt

Den Microsoft 365 oversigtsrapport indeholder følgende rapporter. Du kan få dem vist ved at vælge fanen øverst på rapportsiden. Alle værdier i måneden, der vises i det øverste afsnit i rapporten, refererer til den seneste hele måned.

- **Vedtagelse** &ndash; Giver en samlet oversigt over indføringstendenser. Brug rapporterne i dette afsnit til at få mere at vide om, hvordan dine brugere har vedtaget Microsoft 365, samt hvordan den samlede brug af de enkelte tjenester har ændret sig måned for måned. Du kan se, hvordan brugere er aktiveret, hvor mange personer i organisationen der aktivt bruger Microsoft 365, hvor mange der returnerer brugere, og hvor mange der bruger produktet for første gang.

- **Brug** &ndash; Giver en detaljeret visning af mængden af aktive brugere og nøgleaktiviteterne for hvert produkt for de sidste 12 måneder. Brug rapporterne i dette afsnit til at få mere at vide om, hvordan personer i din organisation bruger Microsoft 365.

- **Kommunikation** &ndash; Du kan hurtigt se, om personer i din organisation foretrækker at holde kontakten ved hjælp af Teams, Yammer, mail eller Skype opkald. Du kan se, om der er skift i mønstre i brugen af kommunikationsværktøjer blandt dine medarbejdere. 

- **Samarbejde** &ndash; Se, hvordan personer i din organisation bruger OneDrive og SharePoint til at gemme dokumenter og samarbejde med hinanden, og hvordan disse tendenser udvikler sig måned for måned. Du kan også se, hvor mange brugere der har delt dokumenter internt eller eksternt, og hvor mange brugere der har brugt SharePoint websteder eller OneDrive konti, opdelt af ejere og andre samarbejdspartnere.

-  &ndash; Storage Brug denne rapport til at spore cloudlager for postkasser, OneDrive og SharePoint websteder.

- **Mobilitet** &ndash; Spor, hvilke klienter og enheder folk bruger til at oprette forbindelse til mail, Teams, Skype eller Yammer.

## <a name="activation-and-licensing"></a>Aktivering og licensering

Aktiverings- og licenssiden indeholder rapporter om Microsoft 365 aktivering, dvs. hvor mange brugere der har downloadet og aktiveret Office apps, og hvor mange licenser din organisation har tildelt. Månedsværdien mod toppen refererer til den aktuelle måned, og målepunkterne afspejler værdier, der er samlet fra begyndelsen af måneden til dags dato.

- **Aktivering** &ndash; Spor serviceabonnementer (f.eks. Microsoft 365 Apps for enterprise, Project og Visio) aktiveringer i din organisation. Hver person med en Office licens kan installere produkter på op til fem enheder. Du kan også bruge rapporter i dette afsnit til at se de enheder, som brugerne har installeret Office apps på. Bemærk, at hvis du vil aktivere en plan, skal en bruger installere appen og logge på med sin konto.

- **Licenser** &ndash; Denne rapport indeholder en oversigt over licenstyper, antallet af brugere, der blev tildelt hver licenstype, og distributionen af licenstildelinger for hver måned. Månedsværdien mod toppen refererer til den aktuelle måned, og målepunkterne afspejler værdier, der er samlet fra begyndelsen af måneden til dags dato.

## <a name="product-usage"></a>Produktforbrug

Denne rapport indeholder en separat rapport for hver Microsoft 365 tjeneste, herunder Exchange, Microsoft 365 grupper, OneDrive, SharePoint, Skype, Teams og Yammer. Hver rapport indeholder det samlede antal aktiverede i forhold til samlede aktive brugerrapporter, antallet af enheder, f.eks. postkasser, websteder, grupper og konti samt rapporter af aktivitetstype, hvor det er relevant. Alle værdier i måneden, der vises i det øverste afsnit i rapporten, refererer til den seneste hele måned.

## <a name="user-activity"></a>Brugeraktivitet

Brugeraktivitetsrapporter er tilgængelige for visse individuelle tjenester. Disse rapporter indeholder brugsdata på brugerniveau, der er joinforbundet med Active Directory-attributter. Derudover giver rapporten Afdelingsindføring dig mulighed for at opdele efter Active Directory-attributter, så du kan se aktive brugere på tværs af alle individuelle tjenester. Alle målepunkter samles for den seneste hele måned. Hvis du vil have vist indholdsdatoen, skal du gå til tabelsiden og vælge UserActivity-tabel, hvor værdien under TimeFrame leverer rapporteringsperioden. 

> [!NOTE]
> Læseren af globale læser- og forbrugsoversigtsrapporter har ikke tilladelse til at få vist brugeraktivitetsrapporterne. 

## <a name="faq"></a>Ofte stillede spørgsmål

### <a name="is-this-template-app-going-to-be-available-through-purchase-or-will-it-be-free"></a>Er dette skabelonprogram tilgængeligt via køb, eller vil det være gratis?

Det er ikke gratis, du skal bruge en Power BI Pro licens. Du kan finde flere oplysninger under [Forudsætninger](/power-bi/service-template-apps-install-distribute#prerequisites) for installation, tilpasning og distribution af en skabelonapp.

Hvis du vil dele dashboards med andre, skal du se mere under [Del dashboards og rapporter](/power-bi/service-how-to-collaborate-distribute-dashboards-reports#share-dashboards-and-reports).

### <a name="who-can-connect-to-microsoft-365-usage-analytics"></a>Who kan oprette forbindelse til Microsoft 365 forbrugsanalyse?

Du skal enten være **global administrator**, **Exchange administrator**, **Skype for Business administrator**, **SharePoint administrator**, **Global læser**, **Rapportlæser**, **Læser af oversigt over forbrugsrapporter** for at oprette forbindelse til skabelonappen. Se [Om administratorroller](../add-users/about-admin-roles.md) for at få flere oplysninger. **Bemærk!** Læseren af **globale rapporter over læser****- og forbrugsoversigter** tillader kun adgang til aggregeringer på lejerniveau i Microsoft 365 forbrugsanalyser, og de har ikke tilladelse til at få vist brugeraktivitetsrapporterne. 

### <a name="who-can-customize-the-usage-analytics-reports"></a>Who kan tilpasse forbrugsanalyserapporterne?

Det er kun den bruger, der har oprettet den indledende forbindelse til skabelonappen, der kan tilpasse rapporterne eller oprette nye rapporter i Power BI webgrænseflade. Se [Tilpas rapporterne i Microsoft 365 brugsanalyse](customize-reports.md) for at få instruktioner.

### <a name="can-i-only-customize-the-reports-from-the-power-bi-web-interface"></a>Kan jeg kun tilpasse rapporterne fra Power BI webgrænsefladen?

Ud over at tilpasse rapporterne fra Power BI webgrænseflade kan brugerne også bruge Power BI Desktop til at oprette direkte forbindelse til Microsoft 365-rapporteringstjenesten for at oprette deres egne rapporter.

### <a name="how-can-i-get-the-pbit-file-that-this-dashboard-is-associated-with"></a>Hvordan får jeg den pbit-fil, som dette dashboard er knyttet til?

Du kan få adgang til pbit-filen fra [Microsoft Download Center](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). 

### <a name="who-can-view-the-dashboards-and-reports"></a>Who kan få vist dashboards og rapporter?

Hvis du har oprettet forbindelse til skabelonappen, kan du dele den med alle ved hjælp af [delingsfunktionen](/power-bi/collaborate-share/service-share-dashboards). Power BI licenser kræver, at både brugerdelingen og den bruger, som et dashboard deles med, har Power BI Pro eller Power BI Premium.

### <a name="can-anyone-share-the-dashboard-or-does-it-have-to-be-the-person-who-connected-to-the-dashboard"></a>Kan alle dele dashboardet, eller skal det være den person, der har oprettet forbindelse til dashboardet?

Når du deler dashboardet, kan du enten give brugerne tilladelse til at dele dashboardet igen med andre eller ej. Du kan angive denne indstilling på tidspunktet for deling.

### <a name="is-it-possible-to-work-on-and-customize-the-same-template-app-with-a-group-of-people"></a>Er det muligt at arbejde på og tilpasse det samme skabelonprogram med en gruppe personer?

Ja. Hvis du vil gøre det muligt for en gruppe administratorer at arbejde sammen om den samme skabelonapp, kan du udnytte funktionerne i apparbejdsområdet i Power BI. Du kan få flere oplysninger under [Hvordan skal jeg samarbejde og dele dashboards og rapporter?](/power-bi/collaborate-share/service-how-to-collaborate-distribute-dashboards-reports) 

### <a name="for-which-timeframe-is-data-available"></a>For hvilken tidsramme er der tilgængelige data?

Størstedelen af rapporterne viser data for de forrige 12 måneder. Nogle af diagrammerne kan dog vise mindre historik, da dataindsamlingen for forskellige produkter og rapporter blev startet på forskellige tidspunkter, og derfor er data for de hele 12 måneder muligvis ikke tilgængelige. Alle rapporter vil efterhånden bygge op til 12 måneders historie. Rapporter, der viser detaljer på brugerniveau, viser data for den forrige hele måned.

### <a name="what-data-is-included-in-the-template-app"></a>Hvilke data er inkluderet i skabelonappen?

Dataene i skabelonappen dækker i øjeblikket det samme sæt aktivitetsmålepunkter, der er tilgængelige i [aktivitetsrapporterne](../activity-reports/activity-reports.md). Når rapporter føjes til aktivitetsrapporterne, føjes de til skabelonappen i en fremtidig version.

### <a name="how-does-the-data-in-the-template-app-differ-from-the-data-in-the-usage-reports"></a>Hvordan adskiller dataene i skabelonappen sig fra dataene i forbrugsrapporterne?

De underliggende data, du kan se i skabelonappen, stemmer overens med de data, du får vist i aktivitetsrapporterne i Microsoft 365 Administration. De vigtigste forskelle er, at i administrationsdata er tilgængelige for de sidste 7/30/90/180 dage, mens skabelonappen præsenterer data på månedlig basis i op til 12 måneder.

Derudover er oplysninger på brugerniveau i skabelonappen kun tilgængelige for den seneste hele måned for brugere, der har fået tildelt en produktlicens og udført en aktivitet.

### <a name="when-should-i-use-the-template-app-and-when-the-usage-reports"></a>Hvornår skal jeg bruge skabelonappen, og hvornår forbrugsrapporterne?

[Aktivitetsrapporterne](../activity-reports/activity-reports.md) er et godt udgangspunkt for at forstå brugen og anvendelsen af Microsoft 365. Skabelonappen kombinerer de Microsoft 365 forbrugsdata og din organisations Active Directory-oplysninger og giver administratorer mulighed for at analysere datasættet ved hjælp af visualiseringsanalysefunktionerne i Power BI. Dette gør det muligt for administratorer ikke kun at visualisere og analysere Microsoft 365 forbrugsdata, men også opdele dem efter Active Directory-egenskaber, f.eks. afdelinger, placering osv. De kan også oprette brugerdefinerede rapporter og dele indsigten i deres organisation. 

### <a name="how-often-is-the-data-refreshed"></a>Hvor ofte opdateres dataene? 

Første gang, du opretter forbindelse til skabelonappen, udfyldes den automatisk med dine data for de forrige 12 måneder. Derefter opdateres dataene i skabelonappen ugentligt. Kunder kan vælge at ændre tidsplanen for opdatering, hvis deres brug af disse data kræver en anden opdateringsrytme.

Back end-tjenesten Microsoft 365 opdaterer data dagligt og leverer data, der er mellem 5-8 dage latent fra dags dato.

Kolonnen **Indholdsdato** i hvert datasæt repræsenterer opdateringsdatoen for dataene i skabelonappen.

### <a name="how-is-an-active-user-defined"></a>Hvordan er en aktiv bruger defineret?

Definitionen af aktiv bruger er den samme som definitionen af [aktiv bruger](../activity-reports/active-users.md) i aktivitetsrapporterne.

### <a name="what-sharepoint-site-collections-are-included-in-the-sharepoint-reports"></a>Hvilke SharePoint grupper af websteder er inkluderet i de SharePoint rapporter?

Den aktuelle version af skabelonappen indeholder filaktivitet fra SharePoint teamwebsteder og SharePoint gruppewebsteder.

### <a name="which-groups-are-included-in-the-microsoft-365-groups-usage-report"></a>Hvilke grupper er inkluderet i Microsoft 365-grupper forbrugsrapport?

Den aktuelle version af skabelonappen indeholder forbrug fra Outlook grupper, Yammer grupper og SharePoint grupper. Den indeholder ikke grupper, der er relateret til Microsoft Teams eller Planner.

### <a name="when-will-an-updated-version-of-the-template-app-become-available"></a>Hvornår bliver en opdateret version af skabelonappen tilgængelig?

Større ændringer af skabelonappen udgives to gange om året, hvilket kan omfatte nye rapporter eller nye data. Mindre ændringer af rapporterne kan udgives hyppigere.

### <a name="is-it-possible-to-integrate-the-data-from-the-template-app-into-existing-solutions"></a>Er det muligt at integrere dataene fra skabelonappen i eksisterende løsninger? 

Dataene i skabelonappen kan hentes via API'erne til Microsoft 365 (som prøveversion). Når de leveres til produktion, flettes de i [MICROSOFT Graph-rapporterings-API'er](https://go.microsoft.com/fwlink/p/?linkid=848843). 

### <a name="are-there-plans-to-expand-the-template-app-to-show-usage-data-from-other-microsoft-products"></a>Er der planer om at udvide skabelonappen for at vise forbrugsdata fra andre Microsoft-produkter?

Dette overvejes i forbindelse med fremtidige forbedringer. Se [køreplanen for Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) for at få opdateringer.

### <a name="how-can-i-pivot-by-company-information-in-active-directory"></a>Hvordan kan jeg pivotere efter firmaoplysninger i Active Directory?

Firmaoplysninger er inkluderet i et af Active Directory-felterne i skabelonappen, og du kan se dem som et færdigbygget filter i **aktivitetsrapporterne for produktbrugeren** . Den er tilgængelig som kolonne i tabellen **UserState** .

### <a name="is-it-possible-to-bring-in-additional-fields-from-active-directory"></a>Er det muligt at hente flere felter fra Active Directory?

Yderligere tilpasning af disse data er mulig ved at oprette forbindelse til [API'erne til Microsoft Graph rapportering](https://go.microsoft.com/fwlink/p/?linkid=848843) for at hente flere felter fra Azure Active Directory og oprette forbindelse til datasættet. 

### <a name="is-it-possible-to-aggregate-the-information-in-the-template-app-across-multiple-subscriptions"></a>Er det muligt at samle oplysningerne i skabelonappen på tværs af flere abonnementer?

På nuværende tidspunkt er skabelonappen til et enkelt abonnement, da den er knyttet til de legitimationsoplysninger, der blev brugt til at oprette forbindelse til det.

### <a name="is-it-possible-to-see-usage-by-plan-ie-e1-e3"></a>Er det muligt at se forbrug efter plan (dvs. E1, E3)?

I skabelonappen repræsenteres brugen på produktniveau. Data om de forskellige abonnementer, der er tildelt til brugere, leveres, men det er ikke muligt at korrelere brugeraktivitet med det abonnement, der er tildelt til brugeren.

### <a name="is-it-possible-to-integrate-other-data-sets-into-the-template-app"></a>Er det muligt at integrere andre datasæt i skabelonappen?

Du kan bruge Power BI Desktop til at oprette forbindelse til api'erne til Microsoft 365 (som prøveversion) for at få flere datakilder, der kan kombineres med data fra skabelonappen.

Du kan få flere oplysninger i [Tilpas dokument](customize-reports.md).

### <a name="is-it-possible-to-see-the-top-users-reports-for-a-specific-timeframe"></a>Er det muligt at se "Topbrugere"-rapporterne for en bestemt tidsramme?

Alle rapporter på brugerniveau præsenterer aggregerede data for den forrige måned.

### <a name="will-the-template-app-be-localized"></a>Lokaliseres skabelonappen? 

Det er i øjeblikket ikke på vej.

### <a name="i-have-a-specific-question-about-the-data-im-seeing-for-my-organization-who-can-i-reach-out-to"></a>Jeg har et specifikt spørgsmål om de data, jeg ser for min organisation. Who kan jeg kontakte?

Du kan bruge feedbackknappen på siden med oversigten over aktivitet i Administration, eller du kan åbne en supportsag ([Få support](../get-help-support.md) for at få hjælp til skabelonappen. 

### <a name="how-can-partners-access-the-data"></a>Hvordan kan partnere få adgang til dataene?

Hvis en partner har uddelegeret administratorrettigheder, kan vedkommende oprette forbindelse til skabelonappen på vegne af kunden.

### <a name="can-i-hide-identifiable-information-such-as-user-group-and-site-names-in-reports"></a>Kan jeg skjule identificerbare oplysninger som f.eks. bruger-, gruppe- og webstedsnavne i rapporter?

Ja, se [Gør de indsamlede data anonyme](enable-usage-analytics.md#make-the-collected-data-anonymous).

## <a name="related-content"></a>Relateret indhold

[Aktivér Microsoft 365 brugsanalyse](enable-usage-analytics.md) (artikel)\
[Naviger og anvend rapporterne i Microsoft 365 brugsanalyse](navigate-and-utilize-reports.md) (artikel)\
[Microsoft 365 rapporter i Administration](../activity-reports/activity-reports.md) (video)
