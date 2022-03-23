---
title: Microsoft 365 til forbrugsanalyse
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
description: Få et overblik over, hvordan din organisation indfører Microsoft 365 til kommunikation og samarbejde.
ms.openlocfilehash: a3c77fe9a4e6d26e62525c6267ab32a81c78289b
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63588332"
---
# <a name="microsoft-365-usage-analytics"></a>Microsoft 365 til forbrugsanalyse

Brug Microsoft 365 inden for Power BI til at få indsigt i, hvordan din organisation anvender de forskellige tjenester inden for Microsoft 365. Du kan visualisere og analysere Microsoft 365 brugsdata, oprette brugerdefinerede rapporter og dele indsigter inden for organisationen. Du kan også få indsigt i, hvordan bestemte områder eller afdelinger bruger Microsoft 365.
  
Microsoft 365-forbrugsanalyse giver dig adgang til et indbygget dashboard, der indeholder en visning på tværs af produkter for de seneste 12 måneder og indeholder en række indbyggede rapporter. Hver rapport giver dig specifik forbrugsindsigt. Brugerspecifikke oplysninger er tilgængelige for den sidste hele kalendermåned.
  
Den [datamodel,](usage-analytics-data-model.md) der bruges til skabelonappen, omfatter brugerattributter fra Active Directory, som gør det muligt at pivote i bestemte rapporter. Følgende Active Directory-attributter er inkluderet: placering, afdeling og organisation. 
  
Se [Aktivér Microsoft 365 forbrugsanalyse for](enable-usage-analytics.md) at begynde at indsamle data. 
  
Microsoft 365 forbrugsanalyser indeholder en række rapporter, der er beskrevet i de følgende afsnit. 

Du kan få adgang til detaljerede rapporter for hvert område ved at markere datatabellerne. Du kan få vist alle færdigbyggede rapporter ved at vælge fanerne nederst på webstedet. Hvis du vil have mere detaljerede oplysninger, [skal du læse Navigering i og](navigate-and-utilize-reports.md) brug [af rapporter og Tilpasning af rapporter](customize-reports.md).

## <a name="executive-summary"></a>Ledelsesresume

Oversigten over ledelsen er en oversigtsvisning på højt niveau af Microsoft 365 til virksomheder indføring, brug, mobilitet, kommunikation, samarbejde og lagerrapporter, og den er beregnet til beslutningstagere. Den indeholder en oversigt over, hvordan nogle individuelle tjenester bruges, baseret på alle de brugere, der er blevet aktiveret, og dem, der er aktive. Alle værdier i den måned, der vises i rapporten, henviser til den seneste fuldførte måned. 

Med denne oversigt kan du hurtigt forstå brugsmønstre i Office og hvordan og hvor dine medarbejdere samarbejder.

![Billede af oversigten Microsoft 365 ledelsen.](../../media/office365usage-exec-summary.png)

## <a name="overview"></a>Oversigt

Rapporten Microsoft 365 oversigt indeholder følgende rapporter. Du kan få dem vist ved at vælge fanen øverst på rapportsiden. Alle værdier i måneden, der vises i den øverste del af rapporten, henviser til den seneste fuldførte måned.

- **Indføring** &ndash; Giver en samlet oversigt over implementeringstendenser. Brug rapporterne i dette afsnit for at få mere at vide om, hvordan dine brugere har indført Microsoft 365, samt hvordan overordnet brug af de enkelte tjenester har ændret sig måned for måned. Du kan se, hvordan brugere er aktiveret, hvor mange personer i organisationen der aktivt bruger Microsoft 365, hvor mange der er tilbagevendende brugere, og hvor mange der bruger produktet for første gang.

- **Anvendelse** &ndash; Giver mulighed for at analysere ned i mængden af aktive brugere og hovedaktiviteterne for hvert produkt for de seneste 12 måneder. Brug rapporterne i dette afsnit for at få mere at vide om, hvordan personer i din organisation bruger Microsoft 365.

- **Kommunikation** &ndash; Du kan få et hurtigt overblik over, om personer i din organisation foretrækker at holde kontakten ved hjælp Teams, Yammer, mail eller Skype opkald. Du kan se, om mønstret ændrer sig i brugen af kommunikationsværktøjer blandt medarbejderne. 

- **Samarbejde** &ndash; Se, hvordan personer i organisationen bruger OneDrive og SharePoint til at gemme dokumenter og samarbejde med hinanden, og hvordan disse tendenser udvikler sig måned efter måned. Du kan også se, hvor mange brugere der har delt dokumenter internt eller eksternt, og hvor mange brugere, der har brugt SharePoint websteder eller OneDrive-konti, opdelt efter ejere og andre samarbejdspartnere.

-  &ndash; Storage Brug denne rapport til at spore skylager til postkasser, OneDrive og SharePoint websteder.

- **Mobilitet** &ndash; Hold styr på, hvilke klienter og enheder personer bruger til at oprette forbindelse til mail, Teams, Skype eller Yammer.

## <a name="activation-and-licensing"></a>Aktivering og licensering

Siden Aktivering og licens tilbyder rapporter om Microsoft 365-aktivering, dvs. hvor mange brugere, der har downloadet og aktiveret Office-apps, og hvor mange licenser der er tildelt af din organisation. Månedsværdien mod toppen refererer til den aktuelle måned, og metrikværdierne afspejler værdier, der er aggregeret fra begyndelsen af måneden til den aktuelle dato.

- **Aktivering** &ndash; Spore serviceabonnementer (f.eks. Microsoft 365 Apps for enterprise, Project og Visio) i organisationen. Hver person med Office licens kan installere produkter på op til fem enheder. Du kan også bruge rapporter i dette afsnit for at se de enheder, som brugere har installeret Office apps. Bemærk, at for at aktivere en plan skal en bruger installere appen og logge på med sin konto.

- **Licensering** &ndash; Denne rapport indeholder en oversigt over licenstyper, antallet af brugere, der blev tildelt hver licenstype, og licenstildelingsdistributionen for hver måned. Månedsværdien mod toppen refererer til den aktuelle måned, og metrikværdierne afspejler værdier, der er aggregeret fra begyndelsen af måneden til den aktuelle dato.

## <a name="product-usage"></a>Produktforbrug

Denne rapport indeholder en separat rapport for hver Microsoft 365-tjeneste, herunder Exchange, Microsoft 365-grupper, OneDrive, SharePoint, Skype, Teams og Yammer. Hver rapport indeholder samlet aktiveret vs. samlet antal rapporter over aktive brugere, optællinger af enheder som postkasser, websteder, grupper og konti samt aktivitetstyperapporter, hvor det er relevant. Alle værdier i måneden, der vises i den øverste del af rapporten, henviser til den seneste fuldførte måned.

## <a name="user-activity"></a>Brugeraktivitet

Brugeraktivitetsrapporter er tilgængelige for visse individuelle tjenester. Disse rapporter giver detaljerede forbrugsdata på brugerniveau sammen med Active Directory-attributter. Desuden giver Department Adoption-rapporten dig mulighed for at opdele efter Active Directory-attributter, så du kan se aktive brugere på tværs af alle individuelle tjenester. Alle målepunkter aggregeres for den seneste fuldførte måned. For at få vist indholdsdatoen skal du gå til tabelsiden og vælge UserActivity-tabel, hvor værdien under Tidsramme indeholder rapporteringsperioden. 

> [!NOTE]
> Global læser og læser til oversigt over brugsrapporter har ikke tilladelse til at få vist rapporterne over brugeraktivitet. 

## <a name="faq"></a>Ofte stillede spørgsmål

### <a name="is-this-template-app-going-to-be-available-through-purchase-or-will-it-be-free"></a>Bliver denne skabelonapp tilgængelig via køb, eller er den gratis?

Det er ikke gratis, du skal bruge en Power BI Pro licens. Hvis du vil have [mere at vide](/power-bi/service-template-apps-install-distribute#prerequisites) , skal du se forudsætningerne for at installere, tilpasse og distribuere en skabelonapp.

Hvis du vil dele dashboards med andre, kan du se mere [under Del dashboards og rapporter](/power-bi/service-how-to-collaborate-distribute-dashboards-reports#share-dashboards-and-reports).

### <a name="who-can-connect-to-microsoft-365-usage-analytics"></a>Who kan oprette forbindelse til Microsoft 365 til forbrugsanalyse?

Du skal enten være **global** administrator, **Exchange-administrator**, **Skype for Business-administrator**, **SharePoint-administrator**, **global** **læser,** rapportlæser **, læser** til oversigt over brugsrapporter for at oprette forbindelse til skabelonappen. Se [Om administratorroller for](../add-users/about-admin-roles.md) at få flere oplysninger. **Bemærk!** **Global læser** og  rapportlæser til oversigt over brug tillader kun adgang til aggregater på lejerniveau i Microsoft 365-forbrugsanalyse, og de har ikke tilladelse til at få vist rapporterne over brugeraktivitet. 

### <a name="who-can-customize-the-usage-analytics-reports"></a>Who kan tilpasse forbrugsanalyserapporter?

Kun den bruger, der først oprette forbindelse til skabelonappen, kan tilpasse rapporterne eller oprette nye rapporter i Power BI webbrugergrænsefladen. Se [Tilpasning af rapporter i Microsoft 365 for vejledning](customize-reports.md).

### <a name="can-i-only-customize-the-reports-from-the-power-bi-web-interface"></a>Kan jeg kun tilpasse rapporterne fra Power BI webgrænseflade?

Ud over at tilpasse rapporterne fra Power BI-webbrugergrænsefladen kan brugerne også bruge Power BI Desktop til at oprette direkte forbindelse til Microsoft 365 rapporteringsservice for at opbygge deres egne rapporter.

### <a name="how-can-i-get-the-pbit-file-that-this-dashboard-is-associated-with"></a>Hvordan får jeg den pbit-fil, som dette dashboard er knyttet til?

Du kan få adgang til pbit-filen fra [Microsoft Download Center](https://download.microsoft.com/download/7/8/2/782ba8a7-8d89-4958-a315-dab04c3b620c/Microsoft%20365%20Usage%20Analytics.pbit). 

### <a name="who-can-view-the-dashboards-and-reports"></a>Who kan du få vist dashboards og rapporter?

Hvis du har oprettet forbindelse til skabelonappen, kan du dele den med andre ved hjælp af [delingsfunktionen](/power-bi/collaborate-share/service-share-dashboards). Power BI kræver, at både den bruger, der deler, og den bruger, som et dashboard deles med, har Power BI Pro eller Power BI Premium.

### <a name="can-anyone-share-the-dashboard-or-does-it-have-to-be-the-person-who-connected-to-the-dashboard"></a>Kan alle dele dashboardet, eller skal det være den person, der har oprettet forbindelse til dashboardet?

Når du deler dashboardet, kan du enten give brugere tilladelse til at dele dashboardet med andre eller ej. Du kan angive denne indstilling på tidspunktet for deling.

### <a name="is-it-possible-to-work-on-and-customize-the-same-template-app-with-a-group-of-people"></a>Er det muligt at arbejde på og tilpasse den samme skabelonapp sammen med en gruppe personer?

Ja. Hvis du vil gøre det muligt for en gruppe af administratorer at arbejde sammen på den samme skabelonapp, kan du udnytte appens arbejdsområdefunktionalitet i Power BI for at få mere at vide under Hvordan skal jeg samarbejde og dele [dashboards og rapporter?](/power-bi/collaborate-share/service-how-to-collaborate-distribute-dashboards-reports) 

### <a name="for-which-timeframe-is-data-available"></a>Hvilken tidsramme er data tilgængelige for?

Størstedelen af rapporterne viser data for de sidste 12 måneder. Nogle af diagrammerne kan dog vise mindre historik, da dataindsamlingen for forskellige produkter og rapporter blev startet på forskellige tidspunkter, og dermed er data for de fulde 12 måneder muligvis ikke tilgængelige. Alle rapporter opbygges med tiden til at have 12 måneders historik. Rapporter, der viser detaljer på brugerniveau, viser data for hele den forrige måned.

### <a name="what-data-is-included-in-the-template-app"></a>Hvilke data er inkluderet i skabelonappen?

Dataene i skabelonappen dækker i øjeblikket det samme sæt aktivitetsdata, der er tilgængelige i [Aktivitetsrapporter](../activity-reports/activity-reports.md). Efterhånden som rapporter føjes til aktivitetsrapporterne, føjes de til skabelonappen i en fremtidig version.

### <a name="how-does-the-data-in-the-template-app-differ-from-the-data-in-the-usage-reports"></a>Hvordan adskiller dataene i skabelonappen sig fra dataene i forbrugsrapporterne?

De underliggende data, der vises i skabelonappen, svarer til de data, der vises i aktivitetsrapporterne i Microsoft 365 Administration. De vigtigste forskelle er, at i Administration er data tilgængelige for de seneste 7/30/90/180 dage, mens skabelonappen præsenterer data på månedsbasis i op til 12 måneder.

Desuden er oplysninger på brugerniveau i skabelonappen kun tilgængelige for de brugere, der blev tildelt en produktlicens og udførte en aktivitet i sidste fuldførte måned.

### <a name="when-should-i-use-the-template-app-and-when-the-usage-reports"></a>Hvornår skal jeg bruge skabelonappen, og hvornår skal jeg bruge anvendelsesrapporterne?

[Aktivitetsrapporterne](../activity-reports/activity-reports.md) er et godt udgangspunkt for at forstå brugen og indføringen af Microsoft 365. Skabelonappen kombinerer Microsoft 365-forbrugsdata og organisationens Active Directory-oplysninger og gør det muligt for administratorer at analysere datasættet ved hjælp af de visuelle analysefunktioner Power BI. Dette giver administratorer mulighed for ikke blot at visualisere og analysere Microsoft 365 brugsdata, men også opdele dem ud fra Active Directory-egenskaber som f.eks. afdelinger, placering osv. De kan også oprette brugerdefinerede rapporter og dele indsigter inden for deres organisation. 

### <a name="how-often-is-the-data-refreshed"></a>Hvor ofte opdateres dataene? 

Når du opretter forbindelse til skabelonappen for første gang, bliver den automatisk udfyldet med dine data for de forrige 12 måneder. Derefter opdateres skabelonappdataene ugentligt. Kunder kan vælge at ændre tidsplanen for opdatering, hvis deres brug af disse data kræver en anden opdateringsrytme.

Back-end-Microsoft 365-tjenesten opdaterer dagligt data og leverer data, der er mellem 5-8 dage latente fra den aktuelle dato.

Kolonnen **Indholdsdato** i hvert datasæt repræsenterer datoen for dataene i skabelonappen.

### <a name="how-is-an-active-user-defined"></a>Hvordan defineres en aktiv bruger?

Definitionen af aktiv bruger er den samme som definitionen af [aktiv bruger i](../activity-reports/active-users.md) aktivitetsrapporterne.

### <a name="what-sharepoint-site-collections-are-included-in-the-sharepoint-reports"></a>Hvilke SharePoint grupper af websteder er inkluderet i SharePoint rapporter?

Den aktuelle version af skabelonappen omfatter filaktivitet fra SharePoint teamwebsteder og SharePoint gruppewebsteder.

### <a name="which-groups-are-included-in-the-microsoft-365-groups-usage-report"></a>Hvilke grupper er inkluderet i rapporten Microsoft 365 Brug af grupper?

Den aktuelle version af skabelonappen omfatter brug fra Outlook, Yammer grupper og SharePoint grupper. Den omfatter ikke grupper, der er relateret Microsoft Teams eller Planner.

### <a name="when-will-an-updated-version-of-the-template-app-become-available"></a>Hvornår bliver en opdateret version af skabelonappen tilgængelig?

Større ændringer af skabelonappen frigives to gange om året, hvilket kan omfatte nye rapporter eller nye data. Mindre ændringer i rapporterne kan frigives mere hyppigt.

### <a name="is-it-possible-to-integrate-the-data-from-the-template-app-into-existing-solutions"></a>Er det muligt at integrere dataene fra skabelonappen i eksisterende løsninger? 

Dataene i skabelonappen kan hentes via de Microsoft 365 API'er (i forhåndsvisning). Når de leveres til produktion, sammenflettes de i [Microsofts Graph API'er til rapportering](https://go.microsoft.com/fwlink/p/?linkid=848843). 

### <a name="are-there-plans-to-expand-the-template-app-to-show-usage-data-from-other-microsoft-products"></a>Er der planer om at udvide skabelonappen til at vise brugsdata fra andre Microsoft-produkter?

Dette overvejes ved kommende forbedringer. Se Oversigt [Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) for opdateringer.

### <a name="how-can-i-pivot-by-company-information-in-active-directory"></a>Hvordan kan jeg dreje efter firmaoplysninger i Active Directory?

Firmaoplysninger er medtaget i et af Active Directory-felterne i skabelonappen, og du kan se det som et indbygget filter i rapporterne **om produktbrugeraktivitet** . Den fås som kolonne i **UserState-tabellen** .

### <a name="is-it-possible-to-bring-in-additional-fields-from-active-directory"></a>Er det muligt at hente yderligere felter fra Active Directory?

Yderligere tilpasning af disse data er muligt ved at oprette forbindelse til [API'er til Microsoft Graph-rapportering](https://go.microsoft.com/fwlink/p/?linkid=848843) for at trække yderligere felter fra Azure Active Directory og joinforbinde til datasættet. 

### <a name="is-it-possible-to-aggregate-the-information-in-the-template-app-across-multiple-subscriptions"></a>Er det muligt at samle oplysningerne i skabelonappen på tværs af flere abonnementer?

På nuværende tidspunkt er skabelonappen til et enkelt abonnement, da den er knyttet til de legitimationsoplysninger, der blev brugt til først at oprette forbindelse til det.

### <a name="is-it-possible-to-see-usage-by-plan-ie-e1-e3"></a>Er det muligt at se brugen efter plan (dvs. E1, E3)?

I skabelonappen er brugen vist på niveau pr. produkt. Data om de forskellige abonnementer, der er tildelt til brugere, er angivet, men det er ikke muligt at korrelere brugeraktivitet til det abonnement, der er tildelt brugeren.

### <a name="is-it-possible-to-integrate-other-data-sets-into-the-template-app"></a>Er det muligt at integrere andre datasæt i skabelonappen?

Du kan bruge Power BI Desktop til at oprette forbindelse til Microsoft 365 API'er (i forhåndsvisning) for at få flere datakilder til at kombinere med skabelonappdataene.

Du kan finde flere oplysninger i [dokumentet Tilpas](customize-reports.md).

### <a name="is-it-possible-to-see-the-top-users-reports-for-a-specific-timeframe"></a>Er det muligt at få vist rapporter om "topbrugere" for en bestemt tidsramme?

Alle rapporter på brugerniveau viser aggregerede data for den forrige måned.

### <a name="will-the-template-app-be-localized"></a>Bliver skabelonappen lokaliseret? 

Dette er i øjeblikket ikke på vej.

### <a name="i-have-a-specific-question-about-the-data-im-seeing-for-my-organization-who-can-i-reach-out-to"></a>Jeg har et specifikt spørgsmål om de data, jeg får vist for min organisation. Who kan jeg tage kontakt til?

Du kan bruge feedbackknappen på siden Aktivitetsoversigt i Administration, eller du kan åbne en supportsag(Få [support](../get-help-support.md) for at få hjælp til skabelonappen. 

### <a name="how-can-partners-access-the-data"></a>Hvordan kan partnere få adgang til dataene?

Hvis en partner har uddelegeret administratorrettigheder, kan han eller hun oprette forbindelse til skabelonappen på vegne af sin kunde.

### <a name="can-i-hide-identifiable-information-such-as-user-group-and-site-names-in-reports"></a>Kan jeg skjule identificerbare oplysninger som f.eks. bruger-, gruppe- og webstedsnavne i rapporter?

Ja, se Gør [de indsamlede data anonyme](enable-usage-analytics.md#make-the-collected-data-anonymous).

## <a name="related-content"></a>Relateret indhold

[Aktivér Microsoft 365 forbrugsanalyse](enable-usage-analytics.md) (artikel)\
[Naviger i og brug rapporterne i Microsoft 365 (](navigate-and-utilize-reports.md)artikel)\
[Microsoft 365 Rapporter i Administration](../activity-reports/activity-reports.md) (video)
