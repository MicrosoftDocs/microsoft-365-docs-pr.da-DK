---
title: Introduktion til følsomhedsmærkater
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
description: Er du klar til at implementere følsomhedsmærkater for at beskytte din organisations data, men er du i tvivl om, hvor du skal starte? Læs nogle praktiske vejledninger, der kan hjælpe dig med at komme på din mærkatrejse.
ms.openlocfilehash: adc939d44715bcfaeb97cdbfa530f55a5aeecd4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589626"
---
# <a name="get-started-with-sensitivity-labels"></a>Introduktion til følsomhedsmærkater

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Du kan finde oplysninger om, hvad følsomhedsmærkater er, og hvordan de kan hjælpe dig med at beskytte din organisations data, under [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md).

Hvis du har [Azure Information Protection](/azure/information-protection/what-is-information-protection) og stadig bruger Azure Information Protection-etiketter, der er administreret fra Azure-portalen, skal du overføre disse etiketter til den samlede [etiketplatform](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform). For Windows computere kan du derefter vælge, hvilken [etiketklient der skal bruges til](/azure/information-protection/rms-client/use-client#choose-which-labeling-client-to-use-for-windows-computers) dine publicerede følsomhedsmærkater.

Når du er klar til at begynde at beskytte din organisations data ved hjælp af følsomhedsmærkater:

1. **Opret etiketterne.** Opret og navngive dine følsomhedsmærkater efter organisationens klassificerings taksonomi for forskellige følsomhedsniveauer for indhold. Brug almindelige navne eller ord, der giver mening for dine brugere. Hvis du ikke allerede har en etableret taksonomi, kan du overveje at starte med etiketnavne som Personlig, Offentlig, Generelt, Fortrolig og Meget fortrolig. Du kan derefter bruge undernavne til at gruppere lignende navne efter kategori. Når du opretter en etiket, kan du bruge teksten i værktøjstip til at hjælpe brugerne med at vælge den korrekte etiket.
    
    For more extensive guidance for defining a classification taxonomy, download the white paper, "Data Classification & Sensitivity Label Taxonomy" from the [Service Trust Portal](https://aka.ms/DataClassificationWhitepaper).

2. **Definer, hvad hver etiket kan gøre.** Konfigurer de beskyttelsesindstillinger, der skal knyttes til hver etiket. Det kan f.eks. være, at du ønsker, at lavere følsomhedsindhold (f.eks. en "Generelt"-etiket) kun skal have et sidehoved eller en sidefod anvendt, mens højere følsomhedsindhold (f.eks. en "fortroligt" etiket) skal have et vandmærke og kryptering.

3. **Publicere etiketterne.** Når dine følsomhedsmærkater er konfigureret, kan du publicere dem ved hjælp af en etiketpolitik. Beslut, hvilke brugere og grupper der skal have etiketterne, og hvilke politikindstillinger der skal bruges. En enkelt etiket kan genbruges – du definerer den én gang, og derefter kan du medtage den i flere etiketpolitikker, der er tildelt forskellige brugere. Så du kan f.eks. prøve dine følsomhedsmærkater ved at tildele en etiketpolitik til blot nogle få brugere. Når du derefter er klar til at udrulle etiketterne på tværs af organisationen, kan du oprette en ny etiketpolitik for dine etiketter og denne gang angive alle brugere.


> Du kan være berettiget til automatisk oprettelse af standardnavne og en standardmærkatpolitik, der tager sig af trin 1-3 for dig. Du kan finde flere oplysninger [i Standardnavne og -politikker for Microsoft Information Protection](mip-easy-trials.md).

Det grundlæggende flow til implementering og anvendelse af følsomhedsmærkater:

![Diagram, der viser arbejdsgang for følsomhedsmærkater.](../media/Sensitivity-label-flow.png)

## <a name="subscription-and-licensing-requirements-for-sensitivity-labels"></a>Abonnements- og licenskrav til følsomhedsmærkater

Et antal forskellige abonnementer understøtter følsomhedsmærkater, og licenskravene for brugere afhænger af de funktioner, du bruger.

Hvis du vil se mulighederne for at licensere dine brugere til at drage fordel af Microsoft 365 overholdelsesfunktioner, skal du se [Microsoft 365 for sikkerheds- & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance). For følsomhedsmærkater skal du [se afsnittet Information Protection: Følsomhedsetiketter](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-sensitivity-labeling) og relateret [PDF-download](https://go.microsoft.com/fwlink/?linkid=2139145) for licenskrav på funktionsniveau.

## <a name="permissions-required-to-create-and-manage-sensitivity-labels"></a>Tilladelser, der kræves for at oprette og administrere følsomhedsmærkater

Medlemmer af dit overholdelsesteam, der opretter følsomhedsmærkater, skal have tilladelse til Microsoft 365 Overholdelsescenter.

Som standard har globale administratorer for din lejer adgang til denne Administration og kan give dem adgang til overholdelsesmedarbejdere og andre personer uden at give dem alle tilladelser som lejeradministrator. For denne delegerede begrænsede administratoradgang skal du føje brugere til rollegruppen **Overholdelsesdataadministrator****,** Overholdelsesadministrator **eller Sikkerhedsadministrator**. 

Alternativt kan du bruge standardrollerne, du kan oprette en ny rollegruppe og føje enten **følsomhedsmærkatadministrator**- eller organisationskonfigurationsroller til denne gruppe. Hvis du vil have en skrivebeskyttet rolle, skal du **bruge Følsomhedsmærkatlæser**. 

> [!NOTE]
> I forhåndsvisning kan du nu bruge følgende rollegrupper:
> - **Beskyttelse af oplysninger**
> - **Administratorer for informationsbeskyttelse**
> - **Information Protection-analytikere**
> - **Beskyttelse af oplysninger**
> - **Læsere til informationsbeskyttelse**
>
> Hvis du vil have en forklaring af hver enkelt rolle og de nye roller, de indeholder, skal du vælge en rollegruppe i ruden <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> >  **Permissioner &** >  >  RollerSammenligningscenterRoller og derefter gennemse beskrivelsen i pop op-ruden. Eller du kan [se Rollegrupper i sikkerheds- & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

Du kan finde en vejledning til at føje brugere til standardrollegruppen, -rollerne eller oprette dine egne [rollegrupper under Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md).

Disse tilladelser er kun nødvendige for at oprette og konfigurere følsomhedsmærkater og deres etiketpolitikker. De behøver ikke at anvende etiketterne i apps eller tjenester. Hvis der kræves yderligere tilladelser til bestemte konfigurationer, der er relateret til følsomhedsetiketter, vil disse tilladelser være angivet i deres respektive dokumentationsinstruktioner.

## <a name="deployment-strategy-for-sensitivity-labels"></a>Implementeringsstrategi for følsomhedsmærkater
En vellykket strategi til implementering af følsomhedsmærkater for en organisation er at oprette et virtuelt arbejdsteam, der identificerer og administrerer forretnings- og tekniske krav, koncepttests, interne kontrolpunkter og godkendelser og endelig installation af produktionsmiljøet.

Ved hjælp af tabellen i næste afsnit anbefaler vi, at du identificerer dine vigtigste et eller to scenarier, der er knyttes til dine mest virkningsfulde forretningsmæssige krav. Når disse scenarier er implementeret, skal du vende tilbage til listen for at identificere de næste en eller to prioriteter for anvendelsen.

Du kan finde yderligere generel installationsvejledning og bedste fremgangsmåder i Installationsacceleration-vejledning [til Microsoft Information Protection og forebyggelse af datatab](https://microsoft.github.io/ComplianceCxE/dag/mip-dlp/), en af ressourcerne fra webstedet [for Customer Acceleration Team (CAT](https://microsoft.github.io/ComplianceCxE/)).

## <a name="common-scenarios-for-sensitivity-labels"></a>Almindelige scenarier for følsomhedsmærkater

Alle scenarier kræver, at du [opretter og konfigurerer følsomhedsmærkater og deres politikker](create-sensitivity-labels.md).

|Jeg vil...|Dokumentation|
|----------------|---------------|
|Administrer følsomhedsetiketter for Office, så indholdet mærkes, som det er oprettet – omfatter understøttelse af manuel mærkning på alle platforme |[Administrer følsomhedsmærkater i Office apps](sensitivity-labels-office-apps.md)|
|Udvid mærkning til Stifinder og PowerShell med yderligere funktioner til Office apps på Windows (hvis det er nødvendigt)|[Azure Information Protection samlet etiketklient til Windows](/azure/information-protection/rms-client/aip-clientv2)|
|Kryptér dokumenter og mails med følsomhedsmærkater, og begræns, hvem der kan få adgang til indholdet, og hvordan det kan bruges |[Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](encryption-sensitivity-labels.md)|
|Aktivér følsomhedsmærkater til Office på internettet med understøttelse af samtidig redigering, eDiscovery, forebyggelse af datatab, søgning – selv når dokumenter er krypteret | [Aktivér følsomhedsetiketter Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)
|Brug samtidig redigering og automatisk lagring i Office, når dokumenter er krypteret | [Aktivere samtidig redigering for filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md)
|Anvend automatisk følsomhedsetiketter på dokumenter og mails | [Anvend en følsomhedsmærkat på indhold automatisk](apply-sensitivity-label-automatically.md)|
|Brug følsomhedsetiketter til at beskytte indhold Teams og SharePoint |[Brug følsomhedsmærkater Microsoft Teams, Microsoft 365, grupper og SharePoint websteder](sensitivity-labels-teams-groups-sites.md)|
|Brug følsomhedsmærkater til at konfigurere standardlinktypen for deling for websteder og individuelle dokumenter SharePoint og OneDrive |[Brug følsomhedsmærkater til at angive standardlinket til deling for websteder og dokumenter SharePoint og OneDrive](sensitivity-labels-default-sharing-link.md)|
|Anvend et følsomhedsmærkat på en dokumentforståelsesmodel, så identificerede dokumenter i et SharePoint automatisk klassificeres og beskyttes |[Anvend et følsomhedsmærkat på en model i Microsoft SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)|
|Undgå eller advar brugere om deling af filer eller mails med en bestemt følsomhedsmærkat |[Brug følsomhedsmærkater som betingelser i DLP-politikker](dlp-sensitivity-label-as-condition.md) |
|Anvend et opbevaringsmærkat for at bevare eller slette filer eller mails, der har en bestemt følsomhedsmærkat|[Anvend automatisk et opbevaringsnavn for at bevare eller slette indhold](apply-retention-labels-automatically.md) |
|Finde, navnmærke og beskytte filer, der er gemt i lokale datalagre |[Installation af Azure Information Protection-scanneren til automatisk at klassificere og beskytte filer](/azure/information-protection/deploy-aip-scanner)|
|Opdag, navn giv og beskyt filer, der er gemt i datalagre, som findes i skyen|[Opdag, klassificer, mærkater og beskyt regulerede og følsomme data, der er gemt i skyen](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|Anvend og vis etiketter i Power BI, og beskyt data, når de gemmes uden for tjenesten|[Følsomhedsmærkater i Power BI](/power-bi/admin/service-security-sensitivity-label-overview)|
|Overvåg og forstå, hvordan følsomhedsmærkater bruges i min organisation|[Få mere at vide om dataklassificering](data-classification-overview.md)|
|Udvid følsomhedsmærkater til tredjepartsapps og -tjenester|[Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk)|
|Udvid følsomhedsmærkater på tværs af indhold i mine Azure-visningsaktiver, f.eks. Azure Blob Storage, Azure Files, Azure Data Lake Storage og datakilder med flere skyer|[Mærkning i Azure-visning](/azure/purview/create-sensitivity-label) |


## <a name="end-user-documentation-for-sensitivity-labels"></a>Slutbrugerdokumentation for følsomhedsmærkater

Den mest effektive dokumentation til slutbrugeren bliver tilpasset vejledning og vejledning, som du angiver for de etiketnavne og konfigurationer, du vælger. Du kan bruge indstillingen etiketpolitik **Giv brugerne et link til en brugerdefineret hjælpeside til** at angive et internt link til denne dokumentation. Brugere kan derefter nemt få adgang til den via **knappen** Følsomhed:

- Til indbygget mærkning: **Menuindstillingen Få mere** at vide.
- Til Azure Information Protection-samlet etiketklient: **Menuindstillingen** Hjælp og feedback > **linket Fortæl** mig mere Microsoft Azure dialogboksen Beskyttelse af oplysninger.

For at hjælpe dig med at levere din tilpassede dokumentation kan du se følgende side og downloads, som du kan bruge til at hjælpe med at træne dine brugere: [Slutbrugerkurser i følsomhedsmærkater](https://microsoft.github.io/ComplianceCxE/enduser/sensitivity/). 

Du kan også bruge følgende ressourcer til grundlæggende instruktioner:

- [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/en-us/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)
    - [Kendte problemer med følsomhedsetiketter i Office](https://support.microsoft.com/en-us/office/known-issues-with-sensitivity-labels-in-office-b169d687-2bbd-4e21-a440-7da1b2743edc)

- [Anvend eller anbefal automatisk følsomhedsetiketter til dine filer og mails i Office](https://support.office.com/article/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1)
    - [Kendte problemer med automatisk anvendelse eller anbefaling af følsomhedsmærkater](https://support.office.com/article/known-issues-with-automatically-applying-or-recommending-sensitivity-labels-451698ae-311b-4d28-83aa-a839a66f6efc)

- [Samlet brugervejledning til Azure Information Protection](/azure/information-protection/rms-client/clientv2-user-guide)

Hvis dine følsomhedsmærkater anvender kryptering på PDF-dokumenter, kan disse dokumenter åbnes med Microsoft Edge på Windows eller Mac. Du kan finde flere oplysninger og alternative læsere under Hvilke [PDF-læsere understøttes for beskyttede PDF-filer?](/azure/information-protection/rms-client/protected-pdf-readers#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)
