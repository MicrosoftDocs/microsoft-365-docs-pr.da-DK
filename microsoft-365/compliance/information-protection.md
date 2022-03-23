---
title: Microsoft Information Protection i Microsoft 365
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
description: Implementer Microsoft Information Protection (MIP)-funktioner for at hjælpe dig med at beskytte følsomme oplysninger, uanset hvor de befinder sig eller rejser.
ms.openlocfilehash: 2fccdafa662bfdf8390a53ac535c571f52f673de
ms.sourcegitcommit: 39838c1a77d4e23df56af74059fb95970223f718
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63591728"
---
# <a name="microsoft-information-protection-in-microsoft-365"></a>Microsoft Information Protection i Microsoft 365

>*[Licensering til Microsoft 365 til & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Implementer funktioner fra Microsoft Information Protection (MIP) for at hjælpe dig med at opdage, klassificere og beskytte følsomme oplysninger, uanset hvor de befinder sig eller rejser.

MIP-funktioner er inkluderet Microsoft 365 overholdelse af regler og standarder og giver dig værktøjerne til at kende dine [data](#know-your-data), beskytte [dine data](#protect-your-data) [og forhindre tab af data](#prevent-data-loss).

![Billede af, hvordan MIP hjælper dig med at opdage, klassificere og beskytte følsomme data.](../media/powered-by-intelligent-platform.png)

Hvis du vil have en beskrivelse af, hvordan du installerer en MIP-løsning til din organisation, skal [du se installere Microsoft Information Protection løsning](information-protection-solution.md).

Du kan finde oplysninger om, hvordan du styrer dine data, [under Microsoft Information Governance Microsoft 365](manage-Information-governance.md).

## <a name="know-your-data"></a>Kende dine data

For at forstå dit datamiljø og identificere følsomme data på tværs af dit hybridmiljø skal du bruge følgende funktioner:

|Funktion|Hvilke problemer løser den?|Kom i gang|
|:------|:------------|:--------------------|
|[Typer af følsomme oplysninger](sensitive-information-type-learn-about.md)| Identificerer følsomme data ved hjælp af indbyggede eller brugerdefinerede regulære udtryk eller en funktion. Bekræftende beviser omfatter nøgleord, tillidsniveauer og afstand.| [Tilpasse en indbygget følsom oplysningstype](customize-a-built-in-sensitive-information-type.md)|
|[Trænbare klassificeringer](classifier-learn-about.md)| Identificerer følsomme data ved hjælp af eksempler på de data, du er interesseret i, i stedet for at identificere elementer i elementet (mønstersammenholdelse). Du kan bruge indbyggede klassificeringer eller træne en klassificering med dit eget indhold.| [Kom i gang med klassekammerater, der kan trænes](classifier-get-started-with.md) |
|[Dataklassificering](data-classification-overview.md) | En grafisk identifikation af elementer i din organisation, som har en følsomhedsmærkat, et opbevaringsmærkat, eller som er blevet klassificeret. Du kan også bruge disse oplysninger til at få indsigt i de handlinger, dine brugere benytter på disse elementer. | [Introduktion til indholdsstifinder](data-classification-content-explorer.md) <p> [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md) |

## <a name="protect-your-data"></a>Beskyt dine data

Hvis du vil anvende fleksible beskyttelseshandlinger, som omfatter kryptering, adgangsbegrænsninger og visuelle markeringer, skal du bruge følgende funktioner:

|Funktion|Hvilke problemer løser den?|Kom i gang|
|:------|:------------|---------------------|
|[Følsomhedsmærkater](sensitivity-labels.md)| En enkelt løsning på tværs af apps, tjenester og enheder til at mærke og beskytte dine data, mens de ligger inden for og uden for organisationen. <br /><br /> Eksempelscenarier: <br />- [Administrer følsomhedsmærkater for Office apps](sensitivity-labels-office-apps.md) <br />- [Kryptér dokumenter og mails](encryption-sensitivity-labels.md) <br />-  [Anvend og få vist navne i Power BI](/power-bi/admin/service-security-apply-data-sensitivity-labels) <br /><br /> Du kan finde en omfattende liste over scenarier for følsomhedsmærkater i Dokumentationen Introduktion.|[Introduktion til følsomhedsmærkater](get-started-with-sensitivity-labels.md) |
|[Samlet Etiketklient til Azure Information Protection](/azure/information-protection/rms-client/aip-clientv2)| For Windows computere kan du udvide mærkningen til Stifinder og PowerShell med yderligere funktioner til Office apps, hvis det er nødvendigt| [Samlet vejledning til Azure Information Protection-klientadministrator](/azure/information-protection/rms-client/clientv2-admin-guide)|
|[Kryptering med dobbelt nøgle](double-key-encryption.md)| Under alle omstændigheder er det kun din organisation, der nogensinde kan dekryptere beskyttet indhold eller for lovmæssige krav, der skal opbevares krypteringsnøgler inden for en geografisk grænse. | [Installér kryptering med dobbelt nøgle](double-key-encryption.md#deploy-dke)|
|[Office 365-meddelelseskryptering (OME)](ome.md)| Krypterer mails og vedhæftede dokumenter, der sendes til alle brugere på en hvilken som helst enhed, så kun autoriserede modtagere kan læse mailoplysninger. <br /><br />  Eksempelscenarie: Tilbagekalde [mail krypteret med avanceret meddelelseskryptering](revoke-ome-encrypted-mail.md) | [Konfigurer nye egenskaber for meddelelseskryptering](set-up-new-message-encryption-capabilities.md)|
|[Tjenestekryptering med kundenøgle](customer-key-overview.md) | Beskytter mod visning af data fra uautoriserede systemer eller medarbejdere og supplerer BitLocker-diskkryptering i Microsoft-datacentre. | [Konfigurer kundenøgle til Office 365](customer-key-set-up.md)|
|[SharePoint IRM (Information Rights Management)](set-up-irm-in-sp-admin-center.md#irm-enable-sharepoint-document-libraries-and-lists)|Beskytter SharePoint og biblioteker, så når en bruger tjekker et dokument ud, er den downloadede fil beskyttet, så kun autoriserede personer kan få vist og bruge filen i overensstemmelse med de politikker, du angiver. | [Konfigurere IRM (Information Rights Management) SharePoint Administration](set-up-irm-in-sp-admin-center.md)|
[Rights Management-forbindelse](/azure/information-protection/deploy-rms-connector) |Protection-only for eksisterende lokale installationer, der bruger Exchange eller SharePoint Server eller filservere, der kører Windows Server and File Classification Infrastructure (FCI). | [Trin til installation af RMS-forbindelsen](/azure/information-protection/deploy-rms-connector#steps-to-deploy-the-rms-connector)
|[Azure Information Protection samlet scanner til mærkning](/azure/information-protection/deploy-aip-scanner)| Finder, etiketter og beskytter følsomme oplysninger, der findes i lokale datalagre. | [Konfiguration og installation af den samlede Azure Information Protection-etiketscanner](/azure/information-protection/deploy-aip-scanner-configure-install)|
|[Microsoft Defender til skyapps](/cloud-app-security/what-is-cloud-app-security)| Finder, navne og beskytter følsomme oplysninger, der findes i datalagre, der findes i skyen. | [Opdag, klassificer, mærkater og beskyt regulerede og følsomme data, der er gemt i skyen](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|[Azure-visning](/azure/purview/overview) |Identificerer følsomme data og anvender automatisk mærkning på indhold i Azure Purview-aktiver. Disse omfatter filer i lagerplads som Azure Data Lake og Azure Files og skemalagte data som f.eks. kolonner i Azure SQL DB og Db. |[Mærkning i Azure-visning](/azure/purview/create-sensitivity-label) |
|[Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|Udvider følsomhedsmærkater til tredjepartsapps og -tjenester. <br /><br />  Eksempelscenarie: [Angiv og få en følsomhedsmærkat (C++)](/information-protection/develop/quick-file-set-get-label-cpp) |[Microsoft Information Protection og konfiguration af SDK (MIP)](/information-protection/develop/setup-configure-mip)|


## <a name="prevent-data-loss"></a>Undgå tab af data

For at forhindre utilsigtet overdeling af følsomme oplysninger kan du bruge følgende funktioner:


|Funktion|Hvilke problemer løser den?|Kom i gang|
|:------|:------------|:---------------------|
|[Forebyggelse af datatab](dlp-learn-about-dlp.md)| Hjælper med at forhindre utilsigtet deling af følsomme elementer. | [Introduktion til DLP-standardpolitikken](get-started-with-the-default-dlp-policy.md)|
|[Forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)| Udvider DLP-funktioner til elementer, der bruges og deles på Windows 10 computere. | [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md)|
|[Microsoft-udvidelse til overholdelse af regler og standarder](dlp-chrome-learn-about.md) | Udvider DLP-funktioner til Chrome-browseren | [Kom i gang med Microsoft-udvidelse til overholdelse af regler og standarder](dlp-chrome-get-started.md)|
|[Microsoft 365 lokal scanner til forebyggelse af datatab (forhåndsvisning)](dlp-on-premises-scanner-learn.md)|Udvider DLP-overvågning af filaktiviteter og beskyttende handlinger for disse filer til lokale filshares og SharePoint-mapper og dokumentbiblioteker.|[Introduktion til Microsoft 365 lokal scanner til forebyggelse af datatab (forhåndsvisning)](dlp-on-premises-scanner-get-started.md)|
|[Beskyt følsomme oplysninger i Microsoft Teams og kanalmeddelelser](dlp-microsoft-teams.md) | Udvider nogle DLP-funktioner til at Teams chat og kanalmeddelelser | [Få mere at vide om standardpolitikken til forebyggelse af datatab i Microsoft Teams (forhåndsvisning)](dlp-teams-default-policy.md)|

## <a name="licensing-requirements"></a>Licenskrav

Licenskrav til MIP afhænger af de scenarier og funktioner, du bruger, i stedet for at angive licenskrav for hver funktionalitet, der er angivet på denne side. For at forstå dine licenskrav og -indstillinger for MIP skal du se afsnittene til **informationsbeskyttelse** fra [Microsoft 365 &-vejledning](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance) for sikkerhed og overholdelse af regler og standarder og den relaterede [PDF-fil](https://go.microsoft.com/fwlink/?linkid=2139145) for licenskrav på funktionsniveau.