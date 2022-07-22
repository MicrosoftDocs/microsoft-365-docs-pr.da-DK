---
title: Kom i gang med følsomhedsmærkater
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Præskriptive trin til administratorer, licenskrav og almindelige scenarier, der bruger følsomhedsmærkater til at beskytte din organisations data.
ms.openlocfilehash: 84e111bbcc6b0d12f1f209993b9c9a0404fa7a77
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949321"
---
# <a name="get-started-with-sensitivity-labels"></a>Kom i gang med følsomhedsmærkater

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Du kan finde oplysninger om, hvad følsomhedsmærkater er, og hvordan de kan hjælpe dig med at beskytte din organisations data, under [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md).

Hvis du har [Azure Information Protection](/azure/information-protection/what-is-information-protection) og stadig bruger Azure Information Protection-mærkater, der blev administreret fra Azure Portal, skal du overføre disse mærkater til platformen for [samlet mærkat](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). På Windows-computere kan du derefter [vælge, hvilken navngivningsklient der skal bruges til](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) dine publicerede følsomhedsmærkater.

Når du er klar til at begynde at beskytte din organisations data ved hjælp af følsomhedsmærkater:

1. **Opret etiketterne.** Opret og navngiv dine følsomhedsmærkater i henhold til din organisations klassificeringstosonomi for forskellige følsomhedsniveauer for indhold. Brug almindelige navne eller ord, der giver mening for dine brugere. Hvis du ikke allerede har en etableret taksonomi, kan du overveje at starte med navne som Personlig, Offentlig, Generelt, Fortroligt og Meget fortroligt. Du kan derefter bruge undermærkater til at gruppere lignende mærkater efter kategori. Når du opretter en etiket, skal du bruge teksten i værktøjstippet til at hjælpe brugerne med at vælge den relevante mærkat.
    
    Du kan finde en mere omfattende vejledning i, hvordan du definerer en klassificeringstosonomi, ved at downloade hvidbogen "Data Classification & Sensitivity Label Taxonomy" fra [Service Trust Portal](https://aka.ms/DataClassificationWhitepaper).

2. **Definer, hvad hver etiket kan gøre.** Konfigurer de beskyttelsesindstillinger, du vil knytte til hver etiket. Det kan f.eks. være, at du ønsker, at der kun anvendes et sidehoved eller en sidefod med et lavere følsomhedsindhold (f.eks. mærkaten "Generelt"), mens et højere følsomhedsindhold (f.eks. mærkaten "Fortroligt" ) skal have et vandmærke og en kryptering.

3. **Publicer etiketterne.** Når dine følsomhedsmærkater er konfigureret, kan du publicere dem ved hjælp af en mærkatpolitik. Beslut, hvilke brugere og grupper der skal have mærkaterne, og hvilke politikindstillinger der skal bruges. En enkelt etiket kan genbruges – du definerer den én gang, og derefter kan du inkludere den i flere mærkatpolitikker, der er tildelt forskellige brugere. Så du kan f.eks. styre dine følsomhedsmærkater ved at tildele en mærkatpolitik til nogle få brugere. Når du derefter er klar til at udrulle mærkaterne på tværs af din organisation, kan du oprette en ny mærkatpolitik for dine mærkater, og denne gang skal du angive alle brugere.

> [!TIP]
> Du er muligvis berettiget til automatisk oprettelse af standardnavne og en standardetiketpolitik, der tager sig af trin 1-3 for dig. Du kan få flere oplysninger under [Standardmærkater og -politikker for Microsoft Purview Information Protection](mip-easy-trials.md).

Det grundlæggende flow til installation og anvendelse af følsomhedsmærkater:

![Diagram, der viser arbejdsprocessen for følsomhedsmærkater.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Abonnements- og licenskrav til følsomhedsmærkater

En række forskellige abonnementer understøtter følsomhedsmærkater, og licenskravene for brugere afhænger af de funktioner, du bruger.

Hvis du vil se mulighederne for at licensere dine brugere, så de kan drage fordel af Microsoft Purview-funktioner, skal du se [Microsoft 365-licensvejledningen for at få hjælp til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). Du kan se følsomhedsmærkater i afsnittet [Microsoft Purview Information Protection: Følsomhedsmærkater](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-information-protection-sensitivity-labeling) og relateret [PDF-download](https://go.microsoft.com/fwlink/?linkid=2139145) for at få licenskrav på funktionsniveau.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Tilladelser, der kræves for at oprette og administrere følsomhedsmærkater

Medlemmer af overholdelsesteamet, der skal oprette følsomhedsmærkater, skal have tilladelser til Microsoft Purview-compliance-portal.

Globale administratorer for din lejer har som standard adgang til dette administrationscenter og kan give overholdelsesansvarlige og andre personer adgang uden at give dem alle tilladelserne for en lejeradministrator. For denne delegerede begrænsede administratoradgang skal du føje brugere til rollegruppen **Overholdelsesdataadministrator**, **Overholdelsesadministrator** eller **Sikkerhedsadministrator** . 

Hvis du vil bruge standardrollerne, kan du oprette en ny rollegruppe og føje rollerne **Administrator af følsomhedsmærkat** eller **Organisationskonfiguration** til denne gruppe. Hvis du vil have en skrivebeskyttet rolle, skal du bruge **Læser af følsomhedsmærkat**. 

> [!NOTE]
> Nu som prøveversion kan du bruge følgende rollegrupper:
> - **Information Protection**
> - **Information Protection administratorer**
> - **Information Protection analytikere**
> - **Information Protection efterforskere**
> - **Information Protection læsere**
>
> Hvis du vil have en forklaring på hver enkelt og de nye roller, de indeholder, skal du vælge en rollegruppe i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> >  **Tilladelser & roller** > **Overholdelsescenterroller** >  og derefter gennemse beskrivelsen i pop op-ruden. Du kan også se [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Du kan finde oplysninger om, hvordan du føjer brugere til standardrollegruppen, roller eller opretter dine egne rollegrupper, [under Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md).

Disse tilladelser kræves kun for at oprette og konfigurere følsomhedsmærkater og deres mærkatpolitikker. De behøver ikke at anvende mærkaterne i apps eller tjenester. Hvis der er behov for yderligere tilladelser til bestemte konfigurationer, der er relateret til følsomhedsmærkater, vises disse tilladelser i deres respektive dokumentationsinstruktioner.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Udrulningsstrategi for følsomhedsmærkater
En vellykket strategi for udrulning af følsomhedsmærkater for en organisation er at oprette et fungerende virtuelt team, der identificerer og administrerer de forretningsmæssige og tekniske krav, blåstempling af koncepttest, interne kontrolpunkter og godkendelser og endelig udrulning til produktionsmiljøet.

Ved hjælp af tabellen i det næste afsnit anbefaler vi, at du identificerer dine vigtigste et eller to scenarier, der er knyttet til dine mest virkningsfulde forretningskrav. Når disse scenarier er udrullet, skal du gå tilbage til listen for at identificere den næste eller to prioriteter for udrulning.

## <a name="common-scenarios-for-sensitivity-labels"></a>Almindelige scenarier for følsomhedsmærkater

Alle scenarier kræver, at du [opretter og konfigurerer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md).

|Jeg vil...|Dokumentation|
|----------------|---------------|
|Administrer følsomhedsmærkater for Office-apps, så indhold mærkes, som det oprettes – omfatter understøttelse af manuel mærkning på alle platforme |[Administrer følsomhedsmærkater i Office apps](sensitivity-labels-office-apps.md)|
|Udvid mærkning til Stifinder og PowerShell med yderligere funktioner til Office-apps på Windows (hvis det er nødvendigt)|[Azure Information Protection Unified Labeling Client til Windows](/azure/information-protection/rms-client/aip-clientv2)|
|Kryptér dokumenter og mails med følsomhedsmærkater, og begræns, hvem der har adgang til indholdet, og hvordan det kan bruges |[Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](encryption-sensitivity-labels.md)|
|Aktivér følsomhedsmærkater for Office på internettet med understøttelse af samtidig redigering, eDiscovery, forebyggelse af datatab, søgning – også selvom dokumenter krypteres | [Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Brug samtidig redigering og automatisk lagring i Office-skrivebordsapps, når dokumenter krypteres | [Aktivér samtidig redigering af filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md)
|Anvend automatisk følsomhedsmærkater på dokumenter og mails | [Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md)|
|Brug følsomhedsmærkater til at beskytte indhold i Teams og SharePoint |[Brug følsomhedsmærkater med Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder](sensitivity-labels-teams-groups-sites.md)|
|Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og individuelle dokumenter i SharePoint og OneDrive |[Brug følsomhedsmærkater til at angive standardlinket til deling for websteder og dokumenter i SharePoint og OneDrive](sensitivity-labels-default-sharing-link.md)|
|Anvend en følsomhedsmærkat på en model til dokumentforståelse, så identificerede dokumenter i et SharePoint-bibliotek automatisk klassificeres og beskyttes |[Anvend en følsomhedsmærkat på en model i Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Undgå eller advar brugere om deling af filer eller mails med en bestemt følsomhedsmærkat |[Brug følsomhedsmærkater som betingelser i DLP-politikker](dlp-sensitivity-label-as-condition.md) |
|Anvend en følsomhedsmærkat på en fil, når jeg modtager en besked om, at indhold, der indeholder personlige data, deles og skal beskyttes| [Undersøg og afhjælp beskeder i Administration af risiko for beskyttelse af personlige oplysninger](/privacy/priva/risk-management-alerts)|
|Anvend en opbevaringsmærkat for at bevare eller slette filer eller mails, der har en bestemt følsomhedsmærkat|[Anvend automatisk en opbevaringsmærkat for at bevare eller slette indhold](apply-retention-labels-automatically.md) |
|Find, mærk og beskyt filer, der er gemt i datalagre i det lokale miljø |[Udrulning af Azure Information Protection-scanneren for automatisk at klassificere og beskytte filer](/azure/information-protection/deploy-aip-scanner)|
|Find, mærk og beskyt filer, der er gemt i datalagre i cloudmiljøet|[Opdag, klassificer, mærk og beskyt regulerede og følsomme data, der er gemt i cloudmiljøet](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Mærkér SQL-databasekolonner ved hjælp af de samme følsomhedsmærkater som dem, der bruges til filer og mails, så organisationen har en samlet mærkatløsning, der fortsat kan beskytte disse strukturerede data, når de eksporteres |[Klassificering af & dataregistrering for Azure SQL Database, Azure SQL Managed Instance og Azure Synapse Analytics](/azure/azure-sql/database/data-discovery-and-classification-overview) <br /><br /> [SQL-dataregistrering og -klassificering for SQL Server i det lokale miljø](/sql/relational-databases/security/sql-data-discovery-and-classification)|
|Anvend og få vist mærkater i Power BI, og beskyt data, når de gemmes uden for tjenesten|[Følsomhedsmærkater i Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|Overvåg og forstå, hvordan følsomhedsmærkater bruges i min organisation|[Om klassificering af data](data-classification-overview.md)|
|Udvid følsomhedsmærkater til tredjepartsapps og -tjenester|[Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Udvid følsomhedsmærkater på tværs af indhold i mine Microsoft Purview-datakortaktiver, f.eks. Azure Blob Storage, Azure Files, Azure Data Lake Storage og datakilder med flere cloudmiljøer|[Mærkat i Microsoft Purview-datatilknytning](/azure/purview/create-sensitivity-label) |

## <a name="end-user-documentation-for-sensitivity-labels"></a>Slutbrugerdokumentation til følsomhedsmærkater

Den mest effektive dokumentation til slutbrugere er tilpasset vejledning og instruktioner, du angiver for de navne og konfigurationer, du vælger. Du kan bruge politikindstillingen Mærkat **Giv brugere et link til en brugerdefineret Hjælp-side** til at angive et internt link til denne dokumentation. Brugerne kan derefter nemt få adgang til den fra knappen **Følsomhed** :

- Til indbygget mærkning: Menuindstillingen **Få mere at vide** .
- Til Azure Information Protection unified labeling-klient: Menupunkt for **Hjælp og feedback** > linket **Fortæl mig mere** i dialogboksen Microsoft Azure Information Protection.

For at hjælpe dig med at angive din tilpassede dokumentation kan du se følgende side og downloads, som du kan bruge til at hjælpe med at oplære dine brugere: [Slutbrugeruddannelse af følsomhedsmærkater](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Du kan også bruge følgende ressourcer til grundlæggende instruktioner:

- [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Kendte problemer med følsomhedsmærkater i Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Anvend eller anbefal automatisk følsomhedsmærkater på dine filer og mails i Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Kendte problemer med automatisk anvendelse eller anbefaling af følsomhedsmærkater](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Azure Information Protection samlet brugervejledning til mærkning](/azure/information-protection/rms-client/clientv2-user-guide)

Hvis dine følsomhedsmærkater anvender kryptering til PDF-dokumenter, kan disse dokumenter åbnes med Microsoft Edge på Windows eller Mac. Du kan finde flere oplysninger og alternative læsere under [Hvilke PDF-læsere understøttes for beskyttede PDF-filer?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
