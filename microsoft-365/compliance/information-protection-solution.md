---
title: Udrul en løsning til beskyttelse af oplysninger med Microsoft Purview
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-overview
- m365solution-mip
- m365initiative-compliance
description: Præskriptive vejledning til installation af Microsoft Purview Information Protection til din organisation.
ms.openlocfilehash: fa826e7b9761ebcff34dd9ae6f7c2ee1b268bade
ms.sourcegitcommit: d9842a9fcaead280bb704e92d44c1f4c201f9eb4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65759825"
---
# <a name="deploy-an-information-protection-solution-with-microsoft-purview"></a>Udrul en løsning til beskyttelse af oplysninger med Microsoft Purview

>*[Licenser til overholdelse af & for Microsoft 365 sikkerhed](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Din strategi til beskyttelse af oplysninger er baseret på dine forretningsmæssige behov. Mange organisationer skal overholde regler, love og forretningspraksisser. Organisationer skal desuden beskytte beskyttede oplysninger, f.eks. data til bestemte projekter.

Microsoft Purview Information Protection (tidligere Microsoft Information Protection) indeholder en struktur, proces og funktionalitet, som du kan bruge til at nå dine specifikke forretningsmål. 

## <a name="microsoft-purview-information-protection-framework"></a>Microsoft Purview Information Protection struktur

Brug Microsoft Purview Information Protection til at hjælpe dig med at finde, klassificere, beskytte og styre følsomme oplysninger, uanset hvor de befinder sig eller rejser.

![oversigt over Microsoft Purview Information Protection løsning](../media/mip-solution-overview-extended.png)

Se følgende Ignite-session for at se, hvordan disse funktioner understøtter og bygger videre på hinanden: [Kend dine data, beskyt dine data, og undgå tab af data med Microsoft Information Protection](https://myignite.microsoft.com/archives/IG20-OD273).

Hvis du vil have datastyring, skal du se [Installér en løsning til datastyring med Microsoft Purview](data-governance-solution.md).

## <a name="licensing"></a>Licensering

Microsoft Purview Information Protection funktioner er inkluderet i Microsoft Purview. Licenskravene kan variere, selv inden for funktionaliteten, afhængigt af konfigurationsmulighederne. Hvis du vil identificere licenskrav og -muligheder, skal du se [Microsoft 365 vejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>Kend dine data

![Få en oversigt over dine data til Microsoft Purview Information Protection løsning](../media/knowyourdata-mipsolution.png)

Det er ofte den største udfordring for mange organisationer at vide, hvor dine følsomme data er placeret. Microsoft Purview Information Protection dataklassificering hjælper dig med at finde og præcist klassificere stadigt stigende mængder data, som din organisation opretter. Grafiske repræsentationer hjælper dig med at få indsigt i disse data, så du kan konfigurere og overvåge politikker for at beskytte og styre dem.


|Trin|Beskrivelse|Flere oplysninger|
|:---|:----------|:---------------|
|1| Beskriv kategorierne af følsomme oplysninger, du vil beskytte. <br /><br /> Du har allerede en idé om, hvilke typer oplysninger der er mest værdifulde for din organisation, og hvilke typer der ikke er. Arbejd sammen med interessenter for at beskrive de kategorier, der er dit udgangspunkt. | [Få mere at vide om typer af følsomme oplysninger.](sensitive-information-type-learn-about.md) <p> [Få mere at vide om trænbare klassificeringer](classifier-learn-about.md)|
|2| Find og klassificer følsomme data. <br /><br /> Følsomme data i elementer kan findes ved hjælp af mange forskellige metoder, der omfatter DLP-standardpolitikker, manuel mærkning af brugere og automatiseret mønstergenkendelse ved hjælp af følsomme oplysningstyper eller maskinel indlæring. | [Om klassificering af data](data-classification-overview.md) <p> [Video: Dataklassificering i Overholdelsescenter](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| Få vist dine følsomme elementer.  <br /><br /> Brug Indholdsoversigt og aktivitetsoversigt til en dybere analyse af følsomme elementer og de handlinger, som brugerne foretager på disse elementer.| [Kom i gang med Indholdsviser](data-classification-content-explorer.md) <p> [Kom i gang med aktivitetsviser](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>Beskyt dine data

![Beskyt dine data for Microsoft Purview Information Protection løsningsoversigt](../media/protect-mipsolution.png)

Brug oplysningerne fra at vide, hvor dine følsomme data er placeret, for at hjælpe dig med at beskytte dem mere effektivt. Men der er ingen grund til at vente – du kan begynde at beskytte dine data med det samme med en kombination af manuel, standard og automatisk mærkning. Brug derefter [Indholdsoversigt](data-classification-content-explorer.md) og [Aktivitetsoversigt](data-classification-activity-explorer.md) fra det forrige afsnit til at bekræfte, hvilke elementer der er mærket, og hvordan dine mærkater bruges.

|Trin|Beskrivelse|Flere oplysninger|
|:---|-----------|:---------------|
| 1|Definer dine [følsomhedsmærkater](sensitivity-labels.md) og politikker, der beskytter organisationens data. <br /><br />Ud over at identificere indholdets følsomhed kan disse mærkater anvende beskyttelseshandlinger, f.eks. sidehoveder, sidefødder, vandmærker og kryptering. | [Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md) <br /><br /> [Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md) <br /><br /> [Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](encryption-sensitivity-labels.md) |
| 2|Mærk og beskyt elementer til Microsoft 365 apps og tjenester. <br /><br />Følsomhedsmærkater understøttes for Microsoft 365 Word-, Excel-, PowerPoint-, Outlook- og objektbeholdere, der omfatter SharePoint og OneDrive websteder og Microsoft 365 grupper. Brug en kombination af metoder til mærkning, f.eks. manuel mærkning, automatisk mærkning, en standardmærkat og obligatorisk mærkning.| [Administrer følsomhedsmærkater i Office apps](sensitivity-labels-office-apps.md) <br /><br /> [Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [Aktivér samtidig redigering af filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md) <br /><br /> [Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md) <br /><br /> [Brug følsomhedsmærkater med Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](sensitivity-labels-teams-groups-sites.md) <br /><br /> [Brug følsomhedsmærkater til at angive standardlinket til deling for websteder og dokumenter i SharePoint og OneDrive](sensitivity-labels-default-sharing-link.md) <br /><br /> [Anvend en følsomhedsmærkat på en model i Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [Følsomhedsmærkater i Power BI](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|Opdag, mærkat og beskyt følsomme elementer, der er placeret i datalagre i cloudmiljøet, ved hjælp af [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) med dine følsomhedsmærkater.| [Opdag, klassificer, mærk og beskyt regulerede og følsomme data, der er gemt i cloudmiljøet](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|Find, mærkat og beskyt følsomme elementer, der er placeret i datalagre i det lokale miljø, ved at udrulle [Azure Information Protection unified labeling scanner](/azure/information-protection/deploy-aip-scanner) med dine følsomhedsmærkater.| [Konfiguration og installation af Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|Udvid dine følsomhedsmærkater til Azure ved hjælp af [Microsoft Purview Datakort](/azure/purview/overview) for at finde og mærke elementer til Azure Blob Storage, Azure-filer, Azure Data Lake Storage Gen1 og Azure Data Lake Storage Gen12. | [Navne i Microsoft Purview datatilknytning](/azure/purview/create-sensitivity-label)|

Hvis du er udvikler og ønsker at udvide følsomhedsmærkater til line of business-apps eller SaaS-apps fra tredjepart, [skal du se konfiguration og konfiguration af Microsoft Information Protection (MIP) SDK](/information-protection/develop/setup-configure-mip). 

### <a name="additional-protection-capabilities"></a>Yderligere beskyttelsesfunktioner

Microsoft Purview indeholder yderligere funktioner, der kan hjælpe med at beskytte data. Det er ikke alle kunder, der har brug for disse funktioner, og nogle af dem tilsidesættes muligvis af nyere versioner.

Brug siden [Beskyt dine data med Microsoft Purview](information-protection.md) for at få vist en komplet liste over beskyttelsesfunktioner.

## <a name="prevent-data-loss"></a>Undgå datatab

![Undgå tab af data for Microsoft Purview Information Protection løsningsoversigt](../media/dlp-mipsolution.png)

Udrul DLP-politikker (Microsoft Purview Forebyggelse af datatab) for at styre og forhindre upassende deling, overførsel eller brug af følsomme data på tværs af apps og tjenester. Disse politikker hjælper brugerne med at træffe de rigtige beslutninger og træffe de rigtige handlinger, når de bruger følsomme data.

|Trin|Beskrivelse|Flere oplysninger|
|:---|:----------|:---------------|
|1|Få mere at vide om DLP. <br /><br /> Organisationer har følsomme oplysninger under deres kontrol, f.eks. finansielle data, beskyttede data, kreditkortnumre, sundhedsjournaler eller cpr-numre. For at beskytte disse følsomme data og reducere risikoen har de brug for en metode til at forhindre deres brugere i at dele dem upassende med personer, der ikke skulle have dem. Denne praksis kaldes forebyggelse af datatab (DLP).| [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)|
|2|Planlæg din DLP-implementering. <br /><br /> Hver organisation planlægger og implementerer DLP (forebyggelse af datatab) forskelligt, fordi hver organisations forretningsmæssige behov, mål, ressourcer og situation er unikke for dem. Der er dog elementer, der er fælles for alle vellykkede DLP-implementeringer. | [Plan for forebyggelse af datatab](dlp-overview-plan-for-dlp.md)|
|3|Design og opret en DLP-politik. <br /><br /> Det er hurtigt og nemt at oprette en DLP-politik (forebyggelse af datatab), men det kan være tidskrævende at få en politik, der giver de tilsigtede resultater, hvis du skal foretage en masse justering. Hvis du tager dig tid til at designe en politik, før du implementerer den, får du hurtigere de ønskede resultater og med færre utilsigtede problemer end at justere efter prøveversion og fejl alene.| [Design en DLP-politik](dlp-policy-design.md) <p> [Reference til DLP-politik](dlp-policy-reference.md) <p>[Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)|
|4|Juster dine DLP-politikker. <br /><br /> Når du har udrullet en DLP-politik, kan du se, hvor godt den opfylder det tilsigtede formål. Brug disse oplysninger til at justere dine politikindstillinger for at opnå en bedre ydeevne. | [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>Oplæringsressourcer

Learning moduler til konsulenter og administratorer:

- [Introduktion til information beskyttelse og administration af datalivscyklus i Microsoft Purview](/learn/modules/m365-compliance-information-governance)
- [Klassificer data til beskyttelse og styring](/learn/modules/m365-compliance-information-classify-data)
- [Beskyt oplysninger i Microsoft Purview](/learn/modules/m365-compliance-information-protect-information)
- [Undgå tab af data i Microsoft Purview](/learn/modules/m365-compliance-information-prevent-data-loss)

Hvis du vil have hjælp til at oplære dine brugere til at anvende og bruge de følsomhedsmærkater, du konfigurerer for dem, skal du se [Slutbrugerdokumentation for følsomhedsmærkater](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels).

Når du installerer politikker til forebyggelse af datatab for Teams, kan du finde nyttige i følgende slutbrugervejledning som en introduktion til denne teknologi med nogle potentielle meddelelser, som de kan se: [Teams meddelelser om DLP (forebyggelse af datatab) og politikker for overholdelse af kommunikation ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0).
