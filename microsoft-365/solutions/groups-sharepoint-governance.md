---
title: Indstillinger interaktioner mellem Microsoft 365 og SharePoint
ms.reviewer: mmclean
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
description: Få mere at vide om interaktion mellem Microsoft 365 og SharePoint
ms.openlocfilehash: 76f3772685dbf67e61d68a47373f514ab2dabfbc
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63590529"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Indstillinger interaktioner mellem Microsoft 365 og SharePoint

Nogle indstillinger for Microsoft 365 grupper og SharePoint i Microsoft 365, specielt relateret til deling og oprettelse af grupper og teamwebsteder, overlapper med hinanden. Denne artikel indeholder beskrivelser af disse interaktioner og bedste praksis for, hvordan du arbejder med disse indstillinger.

![Venn-diagram over SharePoint, Yammer og gruppefunktioner.](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Effekterne af SharePoint i Microsoft 365 grupper

|SharePoint indstilling|Beskrivelse|Effekt på Microsoft 365 grupper|Anbefaling|
|:-----------------|:----------|:-----------------------------|:-------------|
|Ekstern deling for organisation og websted|Bestemmer, om websteder, filer og mapper kan deles med personer uden for organisationen.|Hvis SharePoint og gruppeindstillinger ikke stemmer overens, kan gæster i gruppen være blokeret fra at få adgang til webstedet, eller ekstern adgang kan være tilgængelig på webstedet, men ikke gruppen.|Når du ændrer indstillingerne for deling, skal du kontrollere både gruppeindstillinger SharePoint indstillingerne for websted for gruppeforbundne teamwebsteder.<br><br>Se [Samarbejd med gæster på et websted](./collaborate-in-site.md).|
|Tillad/bloker for domæne|Tillader eller forhindrer indhold, der deles med angivne domæner.|Grupper genkender ikke SharePoint tilladelseslister eller blokeringslister. Brugere fra domæner, der ikke er SharePoint, kan få adgang til SharePoint via en gruppe.|Administrer domæne tilladelister eller blokeringslister for Azure AD og SharePoint sammen. Opret en styringsproces for hele organisationen for at tillade og blokere domæner.<br><br>Se [SharePoint domæneindstillinger og](/sharepoint/restricted-domains-sharing) [Azure AD-domæneindstillinger](/azure/active-directory/b2b/allow-deny-list)|
|Tillad kun brugere i bestemte sikkerhedsgrupper at dele eksternt|Angiver sikkerhedsgrupper, der kan dele websteder, mapper og filer eksternt.|Denne indstilling påvirker ikke gruppeejere, der deler grupper eksternt. Gruppe guests have access to the associated SharePoint site.||
|SharePoint indstillinger for deling af websteder|Bestemmer, hvem der kan dele webstedet direkte uden for gruppemedlemskabet. Dette konfigureres af gruppen eller ejeren af webstedet.|Denne indstilling påvirker ikke direkte gruppen, men den kan tillade brugere at blive føjet til et websted og ikke have adgang til andre grupperessourcer|Overvej at bruge denne indstilling til at begrænse deling af webstedet direkte og administrere webstedsadgang via gruppen.|
|Lad brugere oprette websteder fra SharePoint startsiden og OneDrive|Angiver, om brugerne kan oprette nye SharePoint websteder.|Hvis denne indstilling er slået fra, kan brugerne stadig oprette teamwebsteder med forbindelse til grupper ved at oprette en gruppe.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Effekterne af Microsoft 365 gruppeindstillinger på SharePoint

|Microsoft 365 gruppeindstillinger|Beskrivelse|Effekt på SharePoint|Anbefaling|
|:---------------------------|:----------|:-------------------|:-------------|
|Navngivningspolitikker|Angiver præfikser og suffikser for gruppenavn og blokerede ord ved oprettelse af grupper|Politikker håndhæves for brugere, der opretter gruppeforbundne teamwebsteder, men ikke kommunikationswebsteder eller websteder med andre skabeloner.|Opret separate navngivningsvejledninger til kommunikationswebsteder, hvis det er nødvendigt.|
|Gruppegæstadgang|Angiver, om personer uden for organisationen kan føjes til grupper.|Hvis SharePoint og gruppeindstillinger ikke stemmer overens, kan gæster i gruppen være blokeret fra at få adgang til webstedet, eller ekstern adgang kan være tilgængelig på webstedet, men ikke gruppen.|Når du ændrer indstillingerne for deling, skal du kontrollere både gruppeindstillinger SharePoint indstillingerne for websted for gruppeforbundne teamwebsteder.<br><br>Se [Samarbejd med gæster på et websted](./collaborate-in-site.md)|
|Oprettelse af grupper efter sikkerhedsgruppe|Grupper kan kun oprettes af medlemmer af en bestemt sikkerhedsgruppe.|Brugere, der ikke er medlemmer af sikkerhedsgruppen, vil ikke kunne oprette et teamwebsted med forbindelse til grupper.|Sørg for, at processen for at anmode om en gruppe indeholder instruktioner til at anmode om et websted.|
|Udløbspolitik for gruppe|Angiver en tidsperiode, hvorefter grupper, der ikke bruges aktivt, slettes automatisk.|Når gruppen er blevet slettet, slettes SharePoint websted. Indhold, der er beskyttet af opbevaringspolitikker bevares.|Brug udløbspolitikker til at undgå at udvnde ubrugte grupper og websteder.|

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Samarbejde med personer uden for organisationen](./collaborate-with-people-outside-your-organization.md)

[Administrer oprettelse af websteder i SharePoint](/sharepoint/manage-site-creation)