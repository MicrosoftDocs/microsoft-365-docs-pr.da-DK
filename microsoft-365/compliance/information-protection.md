---
title: Microsoft Purview Information Protection
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-mip
- m365initiative-compliance
recommendations: false
description: Implementer Microsoft Purview Information Protection funktioner for at hjælpe dig med at beskytte følsomme oplysninger, uanset hvor de befinder sig eller rejser.
ms.openlocfilehash: 97f5172479d889ec1914cfc46102a58a83165269
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285472"
---
# <a name="protect-your-sensitive-data-with-microsoft-purview"></a>Beskyt dine følsomme data med Microsoft Purview

>*[Licenser til overholdelse af & for Microsoft 365 sikkerhed](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!TIP]
> *Vidste du, at du kan prøve premiumversionerne af alle ni Microsoft Purview-løsninger gratis?* Brug den 90-dages prøveversion af Purview-løsninger til at udforske, hvordan robuste Purview-funktioner kan hjælpe din organisation med at opfylde sine behov for overholdelse af angivne standarder. Microsoft 365 E3 og Office 365 E3 kunder kan starte nu ved [prøveversionshubben til Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Få mere at vide om [, hvem der kan tilmelde sig og prøvevilkår](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Implementer funktioner fra **Microsoft Purview Information Protection** (tidligere Microsoft Information Protection) for at hjælpe dig med at finde, klassificere og beskytte følsomme oplysninger, uanset hvor de befinder sig eller rejser.

Disse funktioner til beskyttelse af oplysninger giver dig værktøjer til at [kende dine data](#know-your-data), [beskytte dine data](#protect-your-data) og [forhindre tab af data](#prevent-data-loss).

![Billede af, hvordan Microsoft Purview Information Protection hjælper dig med at finde, klassificere og beskytte følsomme data.](../media/powered-by-intelligent-platform.png)

Hvis du vil have en præskriptiv vejledning til installation af en Microsoft Purview-Information Protection-løsning til din organisation, skal du se [Installér en løsning til beskyttelse af oplysninger med Microsoft Purview](information-protection-solution.md).

Du kan få oplysninger om, hvordan du styrer dine data, under [Styr dine data med Microsoft Purview](manage-Information-governance.md).

## <a name="know-your-data"></a>Kend dine data

Hvis du vil forstå dit datalandskab og identificere følsomme data på tværs af dit hybridmiljø, skal du bruge følgende funktioner:

|Kapacitet|Hvilke problemer løser det?|Kom i gang|
|:------|:------------|:--------------------|
|[Typer af følsomme oplysninger](sensitive-information-type-learn-about.md)| Identificerer følsomme data ved hjælp af indbyggede eller brugerdefinerede regulære udtryk eller en funktion. Bekræftende beviser omfatter nøgleord, tillidsniveauer og nærhed.| [Tilpas en indbygget type af følsomme oplysninger](customize-a-built-in-sensitive-information-type.md)|
|[Trænbare klassificeringer](classifier-learn-about.md)| Identificerer følsomme data ved hjælp af eksempler på de data, du er interesseret i, i stedet for at identificere elementer i elementet (mønstermatch). Du kan bruge indbyggede klassificeringer eller oplære en klassificering med dit eget indhold.| [Kom i gang med trænbare klassificeringer](classifier-get-started-with.md) |
|[Klassificering af data](data-classification-overview.md) | En grafisk identifikation af elementer i din organisation, der har en følsomhedsmærkat, en opbevaringsmærkat eller er blevet klassificeret. Du kan også bruge disse oplysninger til at få indsigt i de handlinger, som dine brugere foretager på disse elementer. | [Kom i gang med Indholdsviser](data-classification-content-explorer.md) <p> [Kom i gang med aktivitetsviser](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Beskyt dine data

Hvis du vil anvende fleksible beskyttelseshandlinger, der omfatter kryptering, adgangsbegrænsninger og visuelle markeringer, skal du bruge følgende funktioner:

|Kapacitet|Hvilke problemer løser det?|Kom i gang|
|:------|:------------|---------------------|
|[Følsomhedsmærkater](sensitivity-labels.md)| En enkelt løsning på tværs af apps, tjenester og enheder til mærkning og beskyttelse af dine data, efterhånden som de bevæger sig i og uden for din organisation. <br /><br /> Eksempelscenarier: <br />- [Administrer følsomhedsmærkater for Office apps](sensitivity-labels-office-apps.md) <br />- [Kryptér dokumenter og mails](encryption-sensitivity-labels.md) <br />-  [Anvend og få vist navne i Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Du kan se en omfattende liste over scenarier for følsomhedsmærkater i dokumentationen Introduktion.|[Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md) |
|[Azure Information Protection Unified Labeling Client](/azure/information-protection/rms-client/aip-clientv2)| For Windows computere udvides mærkaten til Stifinder og PowerShell med yderligere funktioner til Office apps, hvis det er nødvendigt| [Vejledning til Azure Information Protection unified labeling-klientadministrator](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Kryptering med dobbelt nøgle](double-key-encryption.md)| Under alle omstændigheder er det kun din organisation, der nogensinde kan dekryptere beskyttet indhold eller til lovmæssige krav, du skal have krypteringsnøgler inden for en geografisk grænse. | [Installer kryptering med dobbelt nøgle](double-key-encryption.md#deploy-dke)|
|[Kryptering af Office 365-meddelelser](ome.md)| Krypterer mails og vedhæftede dokumenter, der sendes til alle brugere på en hvilken som helst enhed, så det kun er godkendte modtagere, der kan læse mailoplysninger. <br /><br />  Eksempelscenarie: [Tilbagekald mail, der er krypteret af avanceret meddelelseskryptering](revoke-ome-encrypted-mail.md) | [Konfigurer nye funktioner til meddelelsekryptering](set-up-new-message-encryption-capabilities.md)|
|[Tjenestekryptering med kundenøgle](customer-key-overview.md) | Beskytter mod visning af data af uautoriserede systemer eller medarbejdere og supplerer BitLocker-diskkryptering i Microsoft-datacentre. | [Konfigurer kundenøgle til Office 365](customer-key-set-up.md)|
|[SharePoint IRM (Information Rights Management)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Beskytter SharePoint lister og biblioteker, så når en bruger tjekker et dokument ud, er den downloadede fil beskyttet, så det kun er godkendte personer, der kan få vist og bruge filen i henhold til de politikker, du angiver. | [Konfigurer IRM (Information Rights Management) i SharePoint Administration](set-up-irm-in-sp-admin-center.md)|
[Rights Management-connector](/azure/information-protection/deploy-rms-connector) |Kun beskyttelse for eksisterende installationer i det lokale miljø, der bruger Exchange eller SharePoint Server eller filservere, der kører Windows FCI (Server and File Classification Infrastructure). | [Trin til installation af RMS-connectoren](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Azure Information Protection unified labeling scanner](/azure/information-protection/deploy-aip-scanner)| Registrerer, mærkater og beskytter følsomme oplysninger, der er placeret i datalagre i det lokale miljø. | [Konfiguration og installation af Azure Information Protection Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)| Registrerer, mærkater og beskytter følsomme oplysninger, der er placeret i datalagre i cloudmiljøet. | [Opdag, klassificer, mærk og beskyt regulerede og følsomme data, der er gemt i cloudmiljøet](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Microsoft Purview-dataoversigt](/azure/purview/overview) |Identificerer følsomme data og anvender automatisk mærkning på indhold i Microsoft Purview Data Map-aktiver. Disse omfatter filer i lageret, f.eks. Azure Data Lake og Azure Files, og skematiserede data, f.eks. kolonner i Azure SQL DB og Cosmos DB. |[Mærkat i Microsoft Purview-datatilknytning](/azure/purview/create-sensitivity-label) |
|[Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|Udvider følsomhedsmærkater til tredjepartsapps og -tjenester. <br /><br />  Eksempelscenarie: [Angiv og hent en følsomhedsmærkat (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[konfiguration og konfiguration af MICROSOFT INFORMATION PROTECTION (MIP)](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Undgå datatab

Brug følgende funktioner for at forhindre utilsigtet overdeling af følsomme oplysninger:


|Kapacitet|Hvilke problemer løser det?|Kom i gang|
|:------|:------------|:---------------------|
|[Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)| Hjælper med at forhindre utilsigtet deling af følsomme elementer. | [Kom i gang med DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)|
|[Forebyggelse af datatab for slutpunkt](endpoint-dlp-learn-about.md)| Udvider DLP-funktioner til elementer, der bruges og deles på Windows 10 computere. | [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)|
|[Microsoft Compliance-udvidelse](dlp-chrome-learn-about.md) | Udvider DLP-funktioner til Chrome-browseren | [Kom i gang med Microsoft Overholdelsesudvidelse](dlp-chrome-get-started.md)|
|[Microsoft Purview-scanner til forebyggelse af datatab i det lokale miljø (prøveversion)](dlp-on-premises-scanner-learn.md)|Udvider DLP-overvågning af filaktiviteter og beskyttende handlinger for disse filer til filshares i det lokale miljø og SharePoint mapper og dokumentbiblioteker.|[Kom i gang med Microsoft Purview-scanner til forebyggelse af datatab i det lokale miljø (prøveversion)](dlp-on-premises-scanner-get-started.md)|
|[Beskyt følsomme oplysninger i Microsoft Teams chat- og kanalmeddelelser](dlp-microsoft-teams.md) | Udvider nogle DLP-funktioner til Teams chat- og kanalmeddelelser | [Få mere at vide om standardpolitikken for forebyggelse af datatab i Microsoft Teams (prøveversion)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>Licenskrav

Licenskrav til Microsoft Purview Information Protection afhænger af de scenarier og funktioner, du bruger, i stedet for at angive licenskrav for hver egenskab, der er angivet på denne side. Hvis du vil vide mere om dine licenskrav og muligheder for Microsoft Purview Information Protection, skal du se afsnittene **om Information Protection** i [Microsoft 365 vejledning til overholdelse af & sikkerhed](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) og den relaterede [PDF-download](https://go.microsoft.com/fwlink/?linkid=2139145) for at få oplysninger om licenskrav på funktionsniveau.
