---
title: Indstillinger interaktioner mellem Microsoft 365 grupper, Teams og SharePoint
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
description: Få mere at vide om interaktion mellem Microsoft 365 grupper, Teams og SharePoint
ms.openlocfilehash: 64f00fcb5ace9e2f2f4a6630def6beb0a51d40bf
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63590306"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Indstillinger interaktioner mellem Microsoft 365 grupper, Teams og SharePoint

Nogle indstillinger for Microsoft 365 grupper, Microsoft Teams og SharePoint i Microsoft 365, specielt relateret til deling og gruppe/team og SharePoint oprettelse af websteder, overlapper med hinanden. Denne artikel indeholder beskrivelser af disse interaktioner og bedste praksis for, hvordan du arbejder med disse indstillinger.

![Venn-diagram over SharePoint, Teams og grupperingsfunktioner.](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Effekterne af SharePoint for grupper og teams

|SharePoint indstilling|Beskrivelse|Effekt på Microsoft 365 og Teams|Anbefaling|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Ekstern deling for organisation og websted|Bestemmer, om websteder, filer og mapper kan deles med personer uden for organisationen.|Hvis SharePoint, grupper og Teams ikke stemmer overens, kan gæster i teamet være blokeret fra at få adgang til webstedet, eller der kan forekomme uventet ekstern adgang.|Når du ændrer indstillingerne for deling, skal du kontrollere gruppeindstillinger, Teams indstillinger og indstillinger for SharePoint for gruppeforbundne teamwebsteder.<br><br> Se [Samarbejd med gæster på et team](./collaborate-as-team.md)|
|Tillad/bloker for domæne|Tillader eller forhindrer indhold, der deles med angivne domæner.|Grupper og Teams kan ikke genkende SharePoint tilladelseslister eller blokeringslister. Brugere fra domæner, der ikke er tilladt i SharePoint, kan få adgang til SharePoint websteder eller indhold via et team.|Administrer domæne tilladelister eller blokeringslister for Azure AD og SharePoint sammen. Opret en styringsproces for hele organisationen for at tillade og blokere domæner.<br><br>Se [SharePoint domæneindstillinger og](/sharepoint/restricted-domains-sharing) [Azure AD-domæneindstillinger](/azure/active-directory/b2b/allow-deny-list)|
|Tillad kun brugere i bestemte sikkerhedsgrupper at dele eksternt|Angiver sikkerhedsgrupper, der kan SharePoint websteder, mapper og filer eksternt.|Denne indstilling forhindrer ikke teamejere i at dele teams eksternt. Team-gæster har adgang til det tilknyttede SharePoint websted.||
|SharePoint indstillinger for deling af websteder|Bestemmer, hvem der kan dele webstedet direkte uden for teammedlemskab. Dette konfigureres af team- eller webstedsejeren.|Denne indstilling påvirker ikke direkte teamet, men den kan tillade brugere at blive føjet til et websted og ikke har adgang til selve teamet eller andre Teams ressourcer|Overvej at bruge denne indstilling til at begrænse deling af webstedet direkte og administrere adgang til webstedet via teamet.|
|Lad brugere oprette websteder fra SharePoint startsiden og OneDrive|Angiver, om brugerne kan oprette nye SharePoint websteder.|Hvis denne indstilling er slået fra, kan brugerne stadig oprette teamwebsteder med forbindelse til grupper ved at oprette et team.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Effekten af gruppeindstillinger i teams

|Microsoft 365 gruppeindstillinger|Beskrivelse|Effekt på Teams|Anbefaling|
|:---------------------------|:----------|:--------------|:-------------|
|Navngivningspolitikker|Angiver præfikser og suffikser for gruppenavn og blokerede ord ved oprettelse af grupper|Politikker håndhæves for brugere, der opretter teams.||
|Gruppegæstadgang|Angiver, om personer uden for organisationen kan føjes til grupper.|Hvis enten grupperne eller Teams indstillingerne for gæstedeling er slået fra, kan teamet ikke deles med gæster.|Når du ændrer indstillingerne for gæstedeling, skal du kontrollere indstillingerne for Teams, Grupper og webstedet SharePoint, der er knyttet til teamet.<br><br> Se [Samarbejd med gæster på et team](./collaborate-as-team.md)|
|Oprettelse af grupper efter sikkerhedsgruppe|Grupper kan kun oprettes af medlemmer af en bestemt sikkerhedsgruppe.|Brugere, der ikke er medlemmer af sikkerhedsgruppen, vil ikke kunne oprette et team.|Sørg for, at processen for at anmode om en gruppe indeholder instruktioner til at anmode om et team eller SharePoint websted.|
|Udløbspolitik for gruppe|Angiver en tidsperiode, hvorefter grupper, der ikke bruges aktivt, slettes automatisk.|Når gruppen slettes, slettes teamet og det tilknyttede SharePoint også. Indhold, der er beskyttet af opbevaringspolitikker bevares.|Brug udløbspolitikker til at undgå at finde ubrugte teams, grupper og websteder.|

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Samarbejde med personer uden for organisationen](./collaborate-with-people-outside-your-organization.md)

[Administrer oprettelse af websteder i SharePoint](/sharepoint/manage-site-creation)