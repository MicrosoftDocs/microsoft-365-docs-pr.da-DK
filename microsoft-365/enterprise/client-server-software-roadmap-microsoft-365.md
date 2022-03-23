---
title: Roadmap til klient- og serversoftware til Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 08/10/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-subscription-management
ms.custom: it-pro
description: Brug denne oversigt til at konfigurere klient- og serversoftware til Microsoft 365.
ms.openlocfilehash: 1522cf706be06656427412f76d6fa3b5455ac7d9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589725"
---
# <a name="client-and-server-software-roadmap-for-microsoft-365"></a>Roadmap til klient- og serversoftware til Microsoft 365

De fleste virksomhedsorganisationer har et hetergene miljø, der indeholder flere versioner af operativsystemer, klientsoftware og serversoftware. Microsoft 365 til Enterprise indeholder de mest sikre versioner af de vigtigste komponenter i din it-infrastruktur. Den indeholder også produktivitetsfunktioner, der er udviklet til at drage fordel af skyteknologier.

Hvis du vil maksimere forretningsværdien af Microsoft 365 for Enterprise-integreret produktpakke, skal du begynde at planlægge og implementere en strategi til at overføre udgivelser af:

- Klienten Office installeret på dine computere for at Microsoft 365 Apps for enterprise.
- Serverne Office installeret på dine servere til deres tilsvarende tjenester i Microsoft 365.
- Windows 7 og Windows 8.1 på dine enheder for at Windows 10 Enterprise.

>[!Note]
>Support til Windows 7 sluttede *den 14. januar 2020*. Hvis du vil have mere at vide, [skal du se oplysninger om ophør af support](https://support.microsoft.com/help/4057281/windows-7-support-will-end-on-january-14-2020).
>

Efterhånden som du udfører disse overflytninger, kommer din organisation tættere på visionen om den [moderne arbejdsplads](https://www.microsoft.com/microsoft-365/blog/2018/04/27/making-it-simpler-with-a-modern-workplace/). Dette sikre og integrerede miljø kan hjælpe dig med at få adgang til teamwork og kreativitet i organisationen. Microsoft 365 til Enterprise aktiverer og giver dig alle på vej.

## <a name="migration-for-office-client-products"></a>Overførsel til Office klientprodukter

Organisationer, både store og små, bruger ofte en kombination af ældre versioner af Office-klientprodukter som Word, Excel og PowerPoint. Disse ældre versioner:

- Kan [opdateres med](https://support.office.com/article/install-office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5) de nyeste sikkerhedsopdateringer og supportrettelser. Men processen er nogle gange manuel og skaleres muligvis ikke på tværs af organisationen.
- Er ikke optimeret til at bruge Microsofts skyteknologier, der hjælper dig med at transformere din virksomhed digitalt.
- Yd ikke de nyeste funktioner.

Microsoft 365 til store virksomheder omfatter Microsoft 365 Apps for enterprise. Denne version af Office-klientprodukter er tilgængelig med en Microsoft 365 for Enterprise-licens. Det installeres og opdateres fra Microsoft Cloud. Microsoft 365 Apps for enterprise indeholder sikkerhedsopdateringer og de nyeste funktioner. Du kan finde flere oplysninger [under Om Microsoft 365 Apps for enterprise](/deployoffice/about-microsoft-365-apps).

### <a name="office-2007"></a>Office 2007

For versioner af Office i Office 2007-versionen er slutdatoen for support allerede gået. Du kan finde flere [oplysninger Office oversigt over slutdato for support i 2007](/deployoffice/office-2007-end-support-roadmap).

I stedet for at opgradere dine computere, der kører Office 2007 til Office 2010, Office 2013 eller Office 2016, skal du overveje at gøre følgende:

1. Hent og tildel Microsoft 365 licens til dine brugere.
2. Fjern Office 2007 på computeren.
3. Installér Microsoft 365 Apps for enterprise, enten individuelt eller under en it-udrulning. Du kan finde flere oplysninger [i Installationsvejledning til Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Microsoft 365 Apps for enterprise installerer automatisk opdateringer. Den kan drage fordel af skybaserede tjenester for at øge sikkerheden og produktiviteten.

### <a name="office-2010"></a>Office 2010

For versioner af Office i Office 2010 ophørte supporten *d. 13. oktober 2020*. Du kan finde flere [oplysninger Office oversigt over slutdato for support for 2010](/deployoffice/office-2010-end-support-roadmap).

Du kan overveje at opgradere dine computere, der kører Office 2010, Office 2013 eller Office 2016. Begge disse versioner skal dog opdateres manuelt. Så overvej i stedet at følge disse trin:

1. Hent og tildel Microsoft 365 licens til dine brugere.
2. Fjern Office 2010 på computeren.
3. Installér Microsoft 365 Apps for enterprise, enten individuelt eller under en it-udrulning. Du kan finde flere oplysninger [i Installationsvejledning til Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Microsoft 365 Apps for enterprise installerer automatisk både sikkerhedsopdateringer og nye funktionsopdateringer. Den kan drage fordel af skybaserede tjenester i Microsoft 365 for øget sikkerhed og produktivitet.

### <a name="office-2013-and-office-2016"></a>Office 2013 og Office 2016

Se roadmap [for ophør af support for at få Office 2013](/lifecycle/products/microsoft-office-2013). Ophør af support til Office 2016 er endnu ikke fastlagt. I disse versioner, f.Office 2010, skal du stadig [installere sikkerhedsopdateringer](https://support.office.com/article/install-office-updates-2ab296f3-7f03-43a2-8e50-46de917611c5). Denne opgave skaleres muligvis ikke godt afhængigt af organisationens størrelse.

I stedet for at holde dine computere opdateret med de nyeste sikkerhedsopdateringer til Office 2013 eller Office 2016 eller opdatere dine computere fra Office 2013 til Office 2016 bør du overveje at gøre følgende:

1. Hent og tildel Microsoft 365 licens til dine brugere.
2. Fjern Office 2013 eller Office 2016 på computeren.
3. Installér Microsoft 365 Apps for enterprise, enten individuelt eller under en it-udrulning. Du kan finde flere oplysninger [i Installationsvejledning til Microsoft 365 Apps](/deployoffice/deployment-guide-microsoft-365-apps).

Microsoft 365 Apps for enterprise installerer automatisk både sikkerhedsopdateringer og nye funktionsopdateringer. Den kan drage fordel af skybaserede tjenester i Microsoft 365 for øget sikkerhed og produktivitet.

## <a name="migration-for-office-server-products"></a>Overførsel til Office serverprodukter

Både store og små organisationer bruger ofte en kombination af ældre versioner af Office-serverprodukter, f.eks. Exchange Server og SharePoint Server. Disse ældre versioner:

- Bør opdateres med de nyeste sikkerhedsopdateringer og supportrettelser. I nogle tilfælde frigives disse opdateringer hver måned.
- Er ikke optimeret til at bruge Microsofts skyteknologier, der hjælper dig med at transformere din virksomhed digitalt.
- Medtag ikke nye produktivitetsprogrammer, f.eks. Microsoft Teams.
- Du skal ikke inkludere de nyeste sikkerhedsfunktioner, f.eks. Exchange og Defender Office 365.

Microsoft 365 til enterprise omfatter skybaserede versioner af Office-servertjenester, der bruger nogle af de samme værktøjer som lokale versioner af Office-serversoftware, f.eks. webbrowsere og Outlook-klienten. Disse tjenester opdateres automatisk af sikkerhedsmæssige hensyn. Så din it-medarbejder sparer tid, det tager at vedligeholde og opdatere lokale servere. Disse tjenester tilbyder også nye forbedringer af funktioner, der ikke findes i Office-serversoftware.

Brug følgende ressourcer til oplysninger om overførsel af brugere og data for bestemte Microsoft 365 arbejdsbelastninger:

- [Flyt postkasser fra lokale Exchange Server til Exchange Online](/exchange/hybrid-deployment/move-mailboxes)
- [Overfør SharePoint data fra SharePoint Server til SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)
- [Overfør Skype for Business Online til Microsoft Teams](/microsoftteams/migration-interop-guidance-for-teams-with-skype)

### <a name="office-2007-server-products"></a>Office 2007-serverprodukter

For serverprodukter i Office 2007-versionen er ophør af support allerede gået. Se disse artikler for at få mere at vide:

- [Exchange oversigt over afslutning af support for 2007](exchange-2007-end-of-support.md)
- [SharePoint oversigt over ophør af support til Server 2007](sharepoint-2007-end-of-support.md)
- [Project oversigt over ophør af support til Server 2007](project-server-2007-end-of-support.md)
- [Office end of support til Communications Server](/skypeforbusiness/plan-your-deployment/upgrade)
- [PerformancePoint Server oversigt over afslutning af support for 2007](pps-2007-end-of-support.md)

I stedet for at opgradere dine serverprodukter i Office 2007-versionen med serverprodukter i versionerne til Office 2010, Office 2013 eller Office 2016 bør du overveje at gøre følgende:

1. Overfør dataene på dine Office 2007-servere til Microsoft 365. Du kan få mere at vide eller hjælp ved at hyre en Microsoft-partner.
2. Udrul de nye funktioner og arbejdsprocesser til brugerne.
3. Når du ikke længere har brug for de lokale servere, der Office 2007-serverprodukterne, skal du afvikle dem.

### <a name="office-2010-server-products"></a>Office 2010-serverprodukter

Support til [Exchange Server 2010](exchange-2010-end-of-support.md) sluttede *d. 13. oktober 2020*.

Ophør af support til [SharePoint Server 2010](upgrade-from-sharepoint-2010.md) er *13. april 2021*.

I stedet for at opgradere disse serverprodukter i Office 2010-versionen med serverprodukter i versionerne til Office 2013 eller Office 2016 bør du overveje at gøre følgende:

1. Overfør dataene på dine Office 2010-servere til Microsoft 365. Få mere at vide under [FastTrack til Microsoft 365](https://fasttrack.microsoft.com/microsoft365) eller ansætte en Microsoft-partner.
2. Udrul de nye funktioner og arbejdsprocesser til brugerne.
3. Når du ikke længere har brug for de lokale servere, der Office 2010-serverprodukterne, kan du afvikle dem.

### <a name="office-2013-server-products"></a>Office 2013-serverprodukter

For serverprodukter i Office 2013 er ophør af support endnu ikke fastlagt. I stedet for at opgradere dine serverprodukter i Office 2013-versionen med serverprodukter i Office 2016-versionen, skal du overveje at gøre følgende:

1. Overfør dataene på dine Office 2013-servere til Microsoft 365. Få mere at vide under [FastTrack til Microsoft 365](https://fasttrack.microsoft.com/microsoft365) eller ansætte en Microsoft-partner.
2. Udrul de nye funktioner og arbejdsprocesser til brugerne.
3. Når du ikke længere har brug for de lokale servere, der Office 2013-serverprodukterne, skal du afvikle dem.

### <a name="office-2016-server-products"></a>Office 2016-serverprodukter

For serverprodukter i Office 2016-versionen er ophør af support endnu ikke fastlagt. Hvis du vil drage fordel af skybaseret tjeneste og forbedringer til digitalt at transformere din virksomhed, kan du overveje at gøre følgende:

1. Overfør dataene på dine Office 2016-servere til Microsoft 365. Få mere at vide under [FastTrack til Microsoft 365](https://fasttrack.microsoft.com/microsoft365) eller ansætte en Microsoft-partner.
2. Udrul de nye funktioner og arbejdsprocesser til brugerne.
3. Når du ikke længere har brug for de lokale servere, der Office 2016-serverprodukterne, kan du afvikle dem.

## <a name="migration-for-windows-7-and-81"></a>Overførsel til Windows 7 og 8.1

Support sluttede for Windows 7 *den 14. januar 2020*. Hvis du vil overføre dine enheder, Windows 7 eller Windows 8.1, kan du udføre en direkte opgradering.

Du kan finde flere [metoder Windows 10 ved hjælp af installationsscenarier](/windows/deployment/windows-10-deployment-scenarios). Du kan også [planlægge Windows 10 din](/windows/deployment/planning/) egen installation.

## <a name="office-2010-clients-and-servers-and-windows-7"></a>Office 2010-klienter og -servere Windows 7

Her er en visuel oversigt over indstillingerne for opgradering, overførsel og flytning til skyen for Office 2010-klienter og -servere Windows 7:

[![Billede, der viser indstillingerne for ophør af supporten for Office 2010-klienter og -servere Windows 7.](../media/microsoft-365-overview/office2010-windows7-end-of-support.png)](../downloads/Office2010Windows7EndOfSupport.pdf)

Denne plakat på én side er en hurtig måde at forstå de stier, du kan følge for at administrere slutdatoen for support til Office 2010-klient- og serverprodukter og Windows 7. De foretrukne stier understøttes i Microsoft 365 for Enterprise.

Du kan [downloade denne plakat](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/Office2010Windows7EndOfSupport.pdf) og udskrive den i Letter-størrelse, juridisk størrelse eller tabloid (11 x 17) størrelse.

## <a name="transition-your-entire-organization"></a>Overgå hele organisationen

Hent denne overgangsplakat for at få et bedre billede af, hvordan du flytter hele organisationen til produkterne og tjenesterne i Microsoft 365 for Enterprise:

[![Billede, der viser overgang til Microsoft 365 plakat.](../media/microsoft-365-overview/transition-org-to-m365.png)](https://download.microsoft.com/download/2/c/7/2c7bcc04-aae3-4604-9707-1ffff66b9851/transition-org-to-m365.pdf)

Denne tosidede plakat er en hurtig måde til at lagerfortegne din eksisterende infrastruktur. Brug den til at få vejledning i at flytte til et produkt eller en tjeneste Microsoft 365 for Enterprise. Den viser Windows og Office og andre infrastruktur- og sikkerhedselementer som administration af enheder, identitet og trusselsbeskyttelse samt oplysninger og overholdelsesbeskyttelse.

## <a name="how-microsoft-migrated-to-microsoft-365-for-enterprise"></a>Sådan overflyttes Microsoft til Microsoft 365 til Enterprise

Se, hvordan it-eksperter hos Microsoft har overflyttet virksomheden Microsoft 365 for Enterprise:

- [Installation og opdatering af Microsoft 365 Apps for enterprise](https://www.microsoft.com/itshowcase/Article/Content/757/Deploying-and-updating-Microsoft-Office-365-ProPlus)
- [Microsoft overfører 150.000 postkasser til Exchange Online](https://www.microsoft.com/itshowcase/Article/Content/577/Microsoft-migrates-150000-mailboxes-to-Exchange-Online)
- [SharePoint til skyen: Få mere at vide om, hvordan Microsoft kørte sin egen overførsel](https://www.microsoft.com/itshowcase/Article/Content/691/SharePoint-to-the-cloud-Learn-how-Microsoft-ran-its-own-migration)
- [Installation Windows 10 Microsoft som en direkte opgradering](https://www.microsoft.com/itshowcase/Article/Content/668/Deploying-Windows-10-at-Microsoft-as-an-inplace-upgrade)
- [Windows 10 installation: Tips og tricks fra Microsoft IT](https://www.microsoft.com/itshowcase/Article/Content/951/Windows-10-deployment-tips-and-tricks-from-Microsoft-IT) (video)