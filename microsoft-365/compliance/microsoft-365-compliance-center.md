---
title: Microsoft Purview-overholdelsesportal
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Få mere at vide om Microsoft Purview-compliance-portal, herunder hvad den indeholder, hvordan du henter den, og dine næste trin.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- intro-overview
ms.openlocfilehash: 45bca9fa0cfe3867d97065be3cb84440dc6bc014
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642476"
---
# <a name="microsoft-purview-compliance-portal"></a>Microsoft Purview-overholdelsesportal

Hvis du er interesseret i din organisations overholdelse af angivne standarder, vil du elske <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>. Microsoft Purview-compliance-portal giver nem adgang til de data og værktøjer, du skal bruge til at administrere organisationens overholdelse af angivne standarder.

Læs denne artikel for at få kendskab til overholdelsesportalen, [hvordan du får adgang til den](#how-do-i-access-the-compliance-portal) og dine [næste trin](#next-steps).

[![Microsoft Purview-compliance-portal startside.](../media/m365-compliance-center-home.png)](https://compliance.microsoft.com)

## <a name="welcome-to-microsoft-purview"></a>Velkommen til Microsoft Purview

Første gang du går til overholdelsesportalen, får du vist følgende velkomstmeddelelse:

![Microsoft Purview-compliance-portal intro.](../media/m365-compliance-center-welcome-steps.png)

Velkomstbanneret giver dig nogle tip til, hvordan du kommer i gang, med de næste trin og en invitation til dig om at give os feedback.

## <a name="card-section"></a>Kortsektion

Når du besøger overholdelsesportalen første gang, kan du i kortafsnittet på startsiden hurtigt se, hvordan din organisation klarer sig med dataoverholdelse, hvilke løsninger der er tilgængelige for din organisation, og en oversigt over eventuelle aktive beskeder.

Herfra kan du:

- Gennemse kortet **Microsoft Purview Compliance Manager** , som fører dig til løsningen [Overholdelsesstyring](compliance-manager.md) . Overholdelsesstyring hjælper med at forenkle den måde, du administrerer overholdelse på. Den beregner en risikobaseret score, der måler din status i forhold til fuldførelse af anbefalede handlinger, som hjælper med at reducere risici i forbindelse med databeskyttelse og lovgivningsmæssige standarder. Den indeholder også arbejdsprocesfunktioner og indbygget kontroltilknytning, der kan hjælpe dig med effektivt at udføre forbedringshandlinger.

    ![Kortet Overholdelsesstyring Microsoft Purview-compliance-portal.](../media/m365-compliance-center-compliance-manager-card.png)

- Gennemse det nye **katalogkort Løsning** , som linker til samlinger af [integrerede løsninger](microsoft-365-solution-catalog.md) , som du kan bruge til at administrere komplette scenarier med overholdelse af angivne standarder. En løsnings funktioner og værktøjer kan omfatte en kombination af politikker, beskeder, rapporter og meget mere.

    ![Kortet med løsningskataloget Microsoft Purview-compliance-portal.](../media/m365-compliance-center-solution-catalog-card.png)

- Gennemse kortet **Aktive beskeder** , som indeholder en oversigt over de mest [aktive beskeder](alert-policies.md) og indeholder et link, hvor du kan få vist mere detaljerede oplysninger, f.eks. alvorsgrad, status, kategori med mere.

    ![Kortet Aktive beskeder Microsoft Purview-compliance-portal.](../media/m365-compliance-center-active-alerts-card.png)

Du kan også bruge funktionen **Tilføj kort** til at tilføje ekstra kort, f.eks. ét, der viser organisationens overholdelse af cloudapps, og et andet, der viser data om brugere med delte filer, med links til [Defender for Cloud Apps](/cloud-app-security/) eller andre værktøjer, hvor du kan udforske data.

![Yderligere oplysninger om overholdelsescenterkort.](../media/m365-compliance-center-additional-cards.png)

## <a name="easy-navigation-to-more-compliance-features-and-capabilities"></a>Nem navigation til flere funktioner og funktioner til overholdelse af angivne standarder

Ud over links på kort på startsiden kan du se en navigationsrude i venstre side af skærmen, der giver dig nem adgang til dine [beskeder](../security/office-365-security/alerts.md), [rapporter](reports-in-security-and-compliance.md), [politikker](alert-policies.md), løsninger til overholdelse af angivne standarder med mere. Hvis du vil tilføje eller fjerne indstillinger for en brugerdefineret navigationsrude, skal du bruge kontrolelementet **Tilpas navigation** i navigationsruden. Dette åbner indstillingerne for **navigationsruden** , så du kan konfigurere, hvilke elementer der skal vises i navigationsruden.

<br>

****

|Navigation|Kommentarer|
|---|---|
|![Navigation i Microsoft Purview-compliance-portal.](../media/m365-compliance-center-leftnav.png)|Vælg **Startside** for at vende tilbage til hovedsiden for overholdelsesportalen. <p> Besøg **Overholdelsesstyring** for at kontrollere din overholdelsesscore og begynde at [administrere overholdelse af angivne standarder](compliance-manager.md) for din organisation. <p> Vælg afsnittet **Dataklassificering** for at få adgang til [klassificeringer, der kan oplæres](classifier-learn-about.md), [enhedsdefinitioner af følsomme oplysninger](sensitive-information-type-entity-definitions.md), indhold og [aktivitetsoversigter](data-classification-activity-explorer.md) . <p> Vælg **Dataconnectors** for at [konfigurere connectors](archiving-third-party-data.md) til at importere og arkivere data i dit Microsoft 365-abonnement. <p> Gå til **Beskeder** for at få vist og løse [beskeder](alert-policies.md) <p>Besøg **Rapporter** for at få vist data om [mærkatforbrug og -opbevaring](sensitivity-labels.md), [DLP-politikforekomster og -tilsidesættelser](view-the-dlp-reports.md), [delte filer](/cloud-app-security/file-filters), [tredjepartsapps, der er i brug](/cloud-app-security/discovered-apps) med mere. <p> Gå til **Politikker** for at konfigurere politikker til at styre data, administrere enheder og modtage [beskeder](../security/office-365-security/alerts.md). Du kan også få adgang til dine [DLP-](dlp-learn-about-dlp.md) og [opbevaringspolitikker](retention.md) . <p> Vælg **Tilladelser** for at administrere, hvem i organisationen der har adgang til overholdelsesportalen for at få vist indhold og udføre opgaver. <p> Brug linkene i afsnittet **Løsninger** til at få adgang til organisationens løsninger til overholdelse af angivne standarder. Disse omfatter: <p> [Katalog](microsoft-365-solution-catalog.md) <br> Opdag, få mere at vide om, og begynd at bruge de intelligente løsninger til overholdelse af angivne standarder og risikostyring, der er tilgængelige for din organisation. <p> [Revision](search-the-audit-log-in-security-and-compliance.md) <br> Brug overvågningsloggen til at undersøge almindelige problemer med support og overholdelse af angivne standarder. <p> [Indholdssøgning](search-for-content.md) <br> Brug Indholdssøgning til hurtigt at finde mail i Exchange-postkasser, dokumenter på SharePoint-websteder og OneDrive-placeringer samt chatsamtaler i Microsoft Teams og Skype for Business. <p> [Kommunikationsoverholdelse](communication-compliance.md) <br> Minimer kommunikationsrisici ved automatisk at registrere upassende meddelelser, undersøge mulige politikovertrædelser og tage skridt til at afhjælpe. <p> [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md) <br> Registrer følsomt indhold, efterhånden som det bruges og deles i hele organisationen, i cloudmiljøet og på enheder, og hjælper med at forhindre utilsigtet tab af data. <p> [Anmodninger fra den registrerede](/compliance/regulatory/gdpr-manage-gdpr-data-subject-requests-with-the-dsr-case-tool) <br> Find og eksportér en brugers personlige data for at hjælpe dig med at besvare anmodninger fra fysiske personer i henhold til den generelle forordning om databeskyttelse (GDPR). <p> [eDiscovery](overview-ediscovery-20.md) <br> Udvid dette afsnit for at bruge kernen og eDiscovery (Premium) til at bevare, indsamle, gennemgå, analysere og eksportere indhold, der reagerer på din organisations interne og eksterne undersøgelser. <p> [Administration af datalivscyklus](manage-data-governance.md) <br> Administrer livscyklussen for følsomme data ved hjælp af funktioner til at importere, gemme og klassificere forretningskritiske data, så du kan bevare det, du har brug for, og slette det, du ikke har brug for. <p> [Beskyttelse af oplysninger](information-protection.md) <br> Opdag, klassificer og beskyt følsomme og forretningskritiske data i hele organisationens livscyklus. <p> [Styring af insider-risiko](insider-risk-management.md) <br> Registrer risikable aktiviteter på tværs af organisationen, så du hurtigt kan identificere, undersøge og reagere på insiderrisici og trusler. <p> [Datastyring](records-management.md) <br> Administrer opbevaring og sletning af elementer af høj værdi for forretningsrelaterede, juridiske eller lovmæssige krav til registrering.|
|

## <a name="how-do-i-access-the-compliance-portal"></a>Hvordan gør jeg du få adgang til overholdelsesportalen?

Hvis du vil have adgang til overholdelsesportalen, skal du gå til [https://compliance.microsoft.com](https://compliance.microsoft.com) og logge på som global administrator, overholdelsesadministrator eller administrator af overholdelsesdata.

## <a name="next-steps"></a>Næste trin

- **Besøg Microsoft Purview Compliance Manager** for at se din overholdelsesscore og begynde at administrere overholdelse af angivne standarder for din organisation. Du kan få mere at vide under [Overholdelsesstyring](compliance-manager.md).

- **Konfigurer politikker for styring af insiderrisiko** for at minimere interne risici og give dig mulighed for at registrere, undersøge og udføre handlinger for risikable aktiviteter i din organisation. Se [Få mere at vide om styring af insiderrisiko](insider-risk-management.md).

- **Gennemse organisationens politikker til forebyggelse af datatab** , og foretag de nødvendige ændringer efter behov. Du kan få mere at vide om under [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md).

- **Bliv bekendt med og konfigurer Microsoft Defender for Cloud Apps**. Se [Hurtig start: Kom i gang med Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security).

- **Få mere at vide om og opret politikker for overholdelse af kommunikation for** hurtigt at identificere og afhjælpe overtrædelser af virksomhedens ordensregler. Se [Få mere at vide om overholdelse af angivne standarder for kommunikation](communication-compliance.md).

- **Besøg ofte din overholdelsesportal**, og sørg for at gennemse eventuelle beskeder eller potentielle risici, der opstår. Gå til , [https://compliance.microsoft.com](https://compliance.microsoft.com) og log på.
