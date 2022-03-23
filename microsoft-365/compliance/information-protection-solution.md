---
title: Installér en Microsoft Information Protection løsning
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
description: Foruddefineret vejledning til installation Microsoft Information Protection (MIP) for organisationen.
ms.openlocfilehash: d70f7356909b0aa0ec663a641e1bc76926db72f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593056"
---
# <a name="deploy-a-microsoft-information-protection-solution"></a>Installér en Microsoft Information Protection løsning

>*[Licensering til Microsoft 365 til & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Din strategi til beskyttelse af oplysninger er drevet af virksomhedens behov. Mange organisationer skal overholde bestemmelser, love og forretningsmetoder. Desuden skal organisationer beskytte beskyttede oplysninger, f.eks data for bestemte projekter.

Microsoft Information Protection (MIP) udgør en ramme, proces og de funktioner, du kan bruge til at opfylde dine specifikke forretningsmål. 

## <a name="microsoft-information-protection-framework"></a>Microsoft Information Protection struktur

Brug Microsoft Information Protection til at hjælpe dig med at opdage, klassificere, beskytte og styre følsomme oplysninger, uanset hvor de befinder sig eller rejser.

![Oversigt over MIP-løsning](../media/mip-solution-overview-extended.png)

Se følgende Ignite-session for at se, hvordan disse funktioner understøtter og bygger videre på hinanden: Kende dine data, beskytte dine data og forhindre [tab af data med Microsoft Information Protection](https://myignite.microsoft.com/archives/IG20-OD273).

Du kan finde oplysninger om, hvordan du styrer dine data, [under Microsoft Information Governance Microsoft 365](manage-Information-governance.md).

## <a name="licensing"></a>Licensering

MIP-funktioner er inkluderet i Microsoft 365 overholdelse af regler og standarder. Licenskravene kan variere, selv inden for funktionaliteten, afhængigt af konfigurationsindstillingerne. For at identificere licenskrav og -indstillinger skal [du Microsoft 365 vejledning til sikkerhed og & overholdelse](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>Kende dine data

![Få overblik over dine data til MIP-løsning](../media/knowyourdata-mipsolution.png)

Det er ofte den største udfordring for mange organisationer at vide, hvor dine følsomme data befinder sig. MIP-dataklassificering hjælper dig med at opdage og præcist klassificere stadig større mængder data, som din organisation opretter. Grafiske repræsentationer hjælper dig med at få indsigt i disse data, så du kan konfigurere og overvåge politikker for at beskytte og styre dem.


|Trin|Beskrivelse|Flere oplysninger|
|:---|:----------|:---------------|
|1| Beskriv kategorierne for følsomme oplysninger, du vil beskytte. <br /><br /> Du har allerede en ide om, hvilke typer oplysninger der er mest værdifulde for din organisation, og hvilke typer der ikke er. Arbejd med interessenter for at beskrive disse kategorier, da disse er udgangspunktet for dig. | [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md) <p> [Få mere at vide om klassekammerater, der kan trænes](classifier-learn-about.md)|
|2| Find og klassificer følsomme data. <br /><br /> Følsomme data i elementer kan findes ved hjælp af mange forskellige metoder, der omfatter DLP-standardpolitikker, manuel mærkning af brugere og automatisk mønstergenkendelse ved hjælp af følsomme oplysningstyper eller maskinlæring. | [Få mere at vide om dataklassificering](data-classification-overview.md) <p> [Video: Dataklassificering i overholdelsescenter](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| Få vist dine følsomme elementer.  <br /><br /> Brug indholdsstifinder og aktivitetsstifinder til en dybere analyse af følsomme elementer og de handlinger, brugerne benytter på disse elementer.| [Introduktion til indholdsstifinder](data-classification-content-explorer.md) <p> [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>Beskyt dine data

![Oversigt over beskyttelse af dine data til MIP-løsning](../media/protect-mipsolution.png)

Brug oplysningerne fra at vide, hvor dine følsomme data findes, så du kan beskytte dem mere effektivt. Men der er ingen grund til at vente – du kan begynde at beskytte dine data med det samme med en kombination af manuel, standard og automatisk mærkning. Brug derefter [Indholdsstifinder](data-classification-content-explorer.md) [og Aktivitetsstifinder](data-classification-activity-explorer.md) fra det forrige afsnit til at bekræfte, hvilke elementer der er mærket, og hvordan dine etiketter bruges.

|Trin|Beskrivelse|Flere oplysninger|
|:---|-----------|:---------------|
| 1|Definer [dine følsomhedsmærkater](sensitivity-labels.md) og politikker, der beskytter din organisations data. <br /><br />Ud over at identificere følsomheden af indholdet, kan disse navne anvende beskyttelseshandlinger, f.eks sidehoveder, sidefødder, vandmærker og kryptering. | [Introduktion til følsomhedsmærkater](get-started-with-sensitivity-labels.md) <br /><br /> [Opret og konfigurer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md) <br /><br /> [Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](encryption-sensitivity-labels.md) |
| 2|Mærkater og beskyt elementer for Microsoft 365 apps og tjenester. <br /><br />Følsomhedsmærkater understøttes i Microsoft 365 Word, Excel, PowerPoint, Outlook og beholdere, der omfatter SharePoint- OneDrive-websteder og Microsoft 365 grupper. Brug en kombination af etiketmetoder, f.eks. manuel mærkning, automatisk mærkater, en standardmærkat og obligatorisk mærkning.| [Administrer følsomhedsmærkater i Office apps](sensitivity-labels-office-apps.md) <br /><br /> [Aktivér følsomhedsetiketter Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [Aktivere samtidig redigering for filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md) <br /><br /> [Anvend en følsomhedsmærkat på indhold automatisk](apply-sensitivity-label-automatically.md) <br /><br /> [Brug følsomhedsmærkater Microsoft Teams, Microsoft 365, grupper og SharePoint websteder](sensitivity-labels-teams-groups-sites.md) <br /><br /> [Brug følsomhedsmærkater til at angive standardlinket til deling for websteder og dokumenter SharePoint og OneDrive](sensitivity-labels-default-sharing-link.md) <br /><br /> [Anvend et følsomhedsmærkat på en model i Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [Følsomhedsmærkater i Power BI](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|Opdag, mærkater og beskyt følsomme elementer, der findes i datalagre i skyen, ved hjælp [af Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security) med dine følsomhedsmærkater.| [Opdag, klassificer, mærkater og beskyt regulerede og følsomme data, der er gemt i skyen](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|Find, etiket og beskyt følsomme elementer, der findes i datalagre i det lokale miljø, ved at installere [den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner) sammen med dine følsomhedsmærkater.| [Konfiguration og installation af den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|Udvid dine følsomhedsmærkater til Azure ved hjælp af [Azure-visning](/azure/purview/overview) for at finde og navngivet elementer til Azure Blob Storage, Azure-filer, Azure Data Lake Storage Gen1 og Azure Data Lake Storage Gen12. | [Mærkning i Azure-visning](/azure/purview/create-sensitivity-label)|

Hvis du er udvikler og ønsker at udvide følsomhedsetiketter til line of business-apps eller SaaS-apps fra tredjepart, skal du se [konfiguration og konfiguration Microsoft Information Protection SDK (MIP](/information-protection/develop/setup-configure-mip)). 

### <a name="additional-protection-capabilities"></a>Yderligere beskyttelsesfunktioner

Microsoft 365 indeholder yderligere funktioner til at beskytte data. Det er ikke alle kunder, der har brug for disse egenskaber, og nogle kan erstattes af nyere versioner.

Brug siden [Microsoft Information Protection-Microsoft 365](information-protection.md) for at få den komplette liste over beskyttelsesfunktioner.

## <a name="prevent-data-loss"></a>Undgå tab af data

![Undgå datatab for oversigt over MIP-løsning](../media/dlp-mipsolution.png)

Implementer politikker til forebyggelse af datatab (DLP) for at styre og forhindre upassende deling, overførsel eller brug af følsomme data på tværs af apps og tjenester. Disse politikker hjælper brugerne med at træffe de rigtige beslutninger og træffe de rigtige handlinger, når de bruger følsomme data.

|Trin|Beskrivelse|Flere oplysninger|
|:---|:----------|:---------------|
|1|Få mere at vide om DLP. <br /><br /> Organisationer har følsomme oplysninger under deres kontrol, f.eks. finansielle data, beskyttede data, kreditkortnumre, sundhedsjournaler eller personnumre. For at beskytte disse følsomme data og reducere risikoen har de brug for en metode til at forhindre deres brugere i upassende at dele dem med personer, der ikke bør have dem. Denne fremgangsmåde kaldes forebyggelse af datatab (DLP).| [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)|
|2|Planlæg din DLP-implementering. <br /><br /> Hver organisation planlægger og implementerer forebyggelse af datatab (DLP) forskelligt, fordi alle organisationers forretningsmæssige behov, mål, ressourcer og situation er unikke for dem. Der er dog elementer, der er fælles for alle vellykkede DLP-implementeringer. | [Plan for forebyggelse af datatab](dlp-overview-plan-for-dlp.md)|
|3|Design og opret en DLP-politik. <br /><br /> Det er hurtigt og nemt at oprette en politik til forebyggelse af datatab (DLP), men det kan være tidskrævende at få en politik, der giver de tilsigtede resultater, hvis du skal foretage en masse justering. Hvis du bruger tid på at designe en politik, før du implementerer den, får du hurtigere de ønskede resultater og færre utilsigtede problemer end justering efter prøveversion og fejl alene.| [Designe en DLP-politik](dlp-policy-design.md) <p> [Reference til DLP-politik](dlp-policy-reference.md) <p>[Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)|
|4|Finjuster dine DLP-politikker. <br /><br /> Når du har implementeret en DLP-politik, kan du se, hvor godt den opfylder det tilsigtede formål. Brug disse oplysninger til at justere politikindstillingerne for at forbedre ydeevnen. | [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>Uddannelsesressourcer

Learning moduler til konsulenter og administratorer:

- [Introduktion til beskyttelse og styring af oplysninger Microsoft 365](/learn/modules/m365-compliance-information-governance)
- [Klassificer data til beskyttelse og styring](/learn/modules/m365-compliance-information-classify-data)
- [Beskyt oplysninger i Microsoft 365](/learn/modules/m365-compliance-information-protect-information)
- [Undgå tab af data i Microsoft 365](/learn/modules/m365-compliance-information-prevent-data-loss)

Hvis du vil have hjælp til at oplære dine brugere til at anvende og bruge de følsomhedsmærkater, du konfigurerer for dem, skal du se [Slutbrugerdokumentationen for følsomhedsmærkater](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels).

Når du installerer politikker til forebyggelse af datatab for Teams, kan du finde nyttige følgende vejledning til slutbrugeren som en introduktion til denne teknologi med nogle potentielle meddelelser, som de kan se: Teams meddelelser om forebyggelse af datatab [(DLP) ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0)og politikker for overholdelse af kommunikation.
