---
title: Udvidelse af Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om udvidelse af Microsoft Purview-løsninger ved hjælp af dataconnectors fra tredjepart og Microsoft Graph-API'er.
ms.openlocfilehash: 8cda9ea3a5ef69af69ab802ca21aa8c4c0e716b9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66621177"
---
# <a name="microsoft-purview-and-microsoft-priva-extensibility"></a>Microsoft Purview og Microsoft Priva udvidelse

Microsoft Purview-løsninger hjælper organisationer med på intelligent vis at vurdere deres risici for overholdelse af angivne standarder, styre og beskytte følsomme data og reagere effektivt på lovmæssige krav. Microsoft Purview er rig på udvidelsesscenarier og giver organisationer mulighed for at tilpasse, udvide, integrere, sætte skub i og understøtte deres løsninger til overholdelse af angivne standarder.

Der er to vigtige komponenter til udvidelse af overholdelse af angivne standarder:

- **Dataconnectors**. Bruges til at importere og arkivere data, der ikke er fra Microsoft, så du kan anvende microsoft 365-funktioner til beskyttelse og styring på tredjepartsdata.

- **API'er**. Aktiverer programmatisk adgang til Microsoft Purview-funktioner.

## <a name="data-connectors"></a>Dataconnectors

Microsoft leverer dataconnectors fra tredjepart, der kan konfigureres i Microsoft Purview-compliance-portal. Du kan se en liste over dataconnectors, der leveres af Microsoft, i tabellen [Dataconnectors fra tredjepart](archiving-third-party-data.md#third-party-data-connectors) . Tabellen med dataconnectors fra tredjepart opsummerer også de løsninger til overholdelse af angivne standarder, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret data i Microsoft 365, og links til den trinvise vejledning for hver connector.

Hvis du vil vide mere om Microsoft 365-dataconnectors, skal du se [Arkivering af tredjepartsdata](archiving-third-party-data.md). Hvis en datatype fra tredjepart ikke understøttes af de dataconnectors, der er tilgængelige på overholdelsesportalen, kan du arbejde sammen med en partner, der kan give dig en brugerdefineret connector. Du kan se en liste over partnere, du kan arbejde med, og den trinvise proces for denne metode under [Arbejd med en partner for at arkivere tredjepartsdata](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Forudsætninger for dataconnectors

Mange af de dataconnectors, der er tilgængelige på overholdelsesportalen til import og arkivering af tredjepartsdata, kræver, at du forbereder og udfører konfigurationsopgaver i datakilden fra tredjepart. Disse forudsætninger er dokumenteret i detaljer for hver dataconnector fra tredjepart.

For dataconnectors på overholdelsesportalen, der leveres af en af Microsofts partnere, skal din organisation have en forretningsrelation med partneren, før du kan udrulle en connector.

Du kan finde vejledning og krav til dataconnectors fra tredjepart i afsnittet "Dataconnectors" i [Microsoft 365-vejledning til overholdelse af sikkerheds- & – tjenestebeskrivelser | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>Api'er

Microsoft Purview- og Microsoft Priva API'er er tilgængelige i api'en til Microsoft Information Protection SDK, Microsoft Graph API og API'en til Office 365 managementaktivitet. Nogle overholdelses-API'er er en del af et nyt sæt API'er til sikkerhed og overholdelse af angivne standarder, der gør det muligt for udviklere til Microsoft 365-kunder, uafhængige softwareleverandører, systemintegratorer og administrerede udbydere af sikkerhedstjenester at bygge sikkerheds- og overholdelsesløsninger af høj værdi.

Hvis du vil vide mere om, hvordan du får adgang til Graph-API'er, skal du se [Oversigt over Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Microsoft Graph-API'er til anmodninger om emnerettigheder

I overensstemmelse med visse bestemmelser om beskyttelse af personlige oplysninger over hele verden kan enkeltpersoner anmode om at gennemse eller administrere de personlige data om sig selv, som virksomhederne har indsamlet. Disse anmodninger kaldes *anmodninger om emnerettigheder* i Microsoft Priva Anmodninger om den registreredes rettigheder-løsningen. Anmodninger om fysiske rettigheder kaldes også DSR-anmodninger ( *Data Subject Requests* ) eller DSAR'er ( *Data Subject Access Requests* ). Microsoft Graph-API'er til anmodninger om emnerettigheder gør det muligt for udviklere at integrere Microsoft 365-relaterede anmodninger om emnerettigheder i det bredere økosystem for beskyttelse af personlige oplysninger. Denne API-baserede udvidelse gør det muligt for organisationer at svare på anmodninger om emnerettigheder på en samlet måde på tværs af hele deres dataområde, der dækker både Microsoft- og ikke-Microsoft-miljøer. Denne funktion hjælper også med automatisering i stor skala og hjælper organisationer med at overholde brancheregler mere effektivt uden at være afhængige af manuelle processer.

Du kan få mere at vide under [Microsoft Graph-API'er for anmodning om emnerettigheder](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Information Protection SDK (MIP)

MIP SDK fremviser mærkat- og beskyttelsestjenester fra Microsoft 365-sikkerheds- og overholdelsescentre til tredjepartsprogrammer og -tjenester. Udviklere kan bruge SDK'et til at bygge indbygget understøttelse af anvendelse af mærkater og beskyttelse af filer. Udviklere kan afgøre, hvilke handlinger der skal udføres, når bestemte mærkater registreres, og angive årsag til MIP-krypterede oplysninger.

MIP SDK-use cases på højt niveau omfatter:

- Et line of business-program, der anvender klassificeringsmærkater på filer ved eksport.

- Et CAD/CAM-designprogram, der giver indbygget understøttelse af følsomhedsmærkater.

- En cloudadgangssikkerhedsmægler eller løsning til forebyggelse af datatab, der kan kryptere data med Azure Information Protection.

Du kan få mere at vide om MIP SDK, forudsætninger, yderligere scenarier og eksempler under [Oversigt over MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft Graph API til Teams DLP

[DLP-funktioner (forebyggelse af datatab)](dlp-microsoft-teams.md) bruges i vid udstrækning i Microsoft Teams, især da organisationer har skiftet til fjernarbejde. For nylig [annoncerede vi den generelle tilgængelighed](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) af Microsoft Graph Change Notification-API'en for meddelelser i Teams. Denne API gør det muligt for udviklere at bygge apps, der kan lytte til Microsoft Teams-meddelelser i næsten realtid og derefter implementere DLP-scenarier for både kunder og partnere. Derudover giver Microsoft Graph Patch API dig mulighed for at anvende DLP-handlinger på Teams-meddelelser.

Disse to API'er udgør Microsoft Graph API til Teams DLP. Du kan komme i gang ved at prøve [eksempelappen](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Du kan få flere oplysninger om Microsoft Teams-meddelelseswebhooks i [dokumentationen](/graph/api/subscription-post-subscriptions).

Du kan finde licenskravene til Teams DLP i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft Graph API til eDiscovery (prøveversion)

Med [eDiscovery (Premium)](overview-ediscovery-20.md) kan organisationer finde data, hvor de findes, og administrere flere komplette eDiscovery-arbejdsprocesser med intelligent maskinel indlæring og analysefunktioner for at reducere data til det relevante sæt – alt sammen mens dataene forbliver inden for microsoft 365-sikkerheds- og overholdelsesgrænsen.

Graf-API'er til eDiscovery (Premium) kan bruges til at oprette og administrere sager, gennemse sæt og gennemse sætforespørgsler på en skalerbar og gentagelig måde. Dette gør det muligt for kunder og partnere at oprette apps og arbejdsprocesser for at automatisere almindelige og gentagne processer, f.eks. oprette sager og administrere tilsynsførende og juridiske ventepositioner.

Det første sæt Graph-API'er til eDiscovery er tilgængelige i en offentlig prøveversion. Vi planlægger at tilføje flere funktioner inden udgangen af kalenderåret. Hvis du vil vide mere om disse API'er og andre opdateringer til eDiscovery (Premium), skal du se denne [blog](https://aka.ms/Ignite2020AeDAA).

Du kan finde licenskravene til eDiscovery (Premium) og API'en i afsnittet "eDiscovery" i [microsoft 365-licensvejledningen om sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft Graph API til Teams-eksport

EIA (Enterprise Information Archiving) til Microsoft Teams er et nøglescenarie for vores kunder, da det giver dem mulighed for at løse lovmæssige krav. Ud over vores indbyggede funktioner til arkivering af indhold i Microsoft Teams kan kunder og partnere nu bruge Teams Eksport-API'er til at løse i forbindelse med brugerdefinerede program- og integrationsscenarier. Teams-eksport-API'erne understøtter masseeksport (op til 200 anmodninger pr. sekund/pr. app/pr. lejer) af Teams-meddelelser og vedhæftede filer i meddelelser. Slettede meddelelser er også tilgængelige for API'en i op til 30 dage, efter de er blevet slettet. Du kan finde flere oplysninger om disse Teams-eksport-API'er, og hvordan du bruger dem i dine programmer, under [Eksportér indhold med Microsoft Teams-eksport-API'erne](/microsoftteams/export-teams-content).

Du kan finde licenskravene til brugen af Teams Export API'er i [Licensvejledning til Microsoft 365 for at få sikkerheds & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>Microsoft Graph Connector-API'er (prøveversion)

Med [Microsoft Graph-connectors](/microsoftsearch/connectors-overview) kan organisationer indeksere tredjepartsdata, så de vises i Microsoft-søgeresultater. Denne funktion udvider de typer af indholdskilder, der kan søges i i dine Microsoft 365-produktivitetsapps og i det bredere Microsoft-økosystem. Tredjepartsdataene kan hostes i det lokale miljø eller i offentlige eller private cloudmiljøer. Fra og med eDiscovery (Premium) aktiverer vi udviklereksempel på indbygget overholdelsesværdi af Microsoft 365-forbundne apps. Dette muliggør overholdelse af angivne standarder for apps, der integreres i Microsoft 365-økosystemet, for at give brugerne mulighed for at opnå problemfrie overholdelsesoplevelser. Hvis du vil vide mere om, hvordan du inkorporerer Microsoft Graph Connector-API'er i din appvisning, skal du se [Opret, opdater og slet forbindelser i Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).

### <a name="microsoft-graph-api-for-records-management-preview"></a>Microsoft Graph API til datastyring (prøveversion)

Organisationer af alle typer kræver en løsning til datastyring for at administrere kritiske poster på tværs af deres data. [Microsoft Purview-datastyring](records-management.md) hjælper en organisation med at administrere deres juridiske forpligtelser, giver mulighed for at demonstrere overholdelse af regler og øger effektiviteten med regelmæssig fordeling af elementer, der ikke længere er påkrævet.

Datastyringsløsningen bruges af organisationer i store mængder til at bruge sine forskellige funktioner til at beskytte, navngive, bevare eller slette deres data. Microsoft Graph-API'erne til datastyring gør det muligt for organisationer at administrere opbevaringsmærkater og deres tilknyttede handlinger mere effektivt, automatisere gentagne opgaver og udstyre kunderne med fleksibilitet i mulighederne.

Nu udrulles den første version af Graph-API'er til datastyring, der understøtter administration af opbevaringsmærkater og hændelsesbaseret opbevaring. Eksempelscenarier:

- **Administration af opbevaringsmærkater**
    
    Administratorer af postadministration og udviklere skal vedligeholde deres systemer til administration af poster med mærkater, der jævnligt oprettes, opdateres og slettes.
    
    Udviklere og overholdelsesadministratorer bruger Graph API'er til datastyring til at udføre CRUD-handlinger på mærkatenheden for at vedligeholde deres systemer.

- **Udløsning af en hændelse for en eksisterende etiket**
    
    Når en medarbejder forlader en organisation, opdateres oplysningerne i HR-ledelsessystemet. Fra afrejsedatoen skal fortrolige dokumenter opbevares i syv år. Opbevaringsmærkaten "Employee_departure" er allerede anvendt på disse dokumenter.
    
    Udviklere og overholdelsesadministratorer bruger Graph-API'er til dataadministration til at læse mærkaten "Employee_departure" og slå den tilknyttede hændelsestype "Event-employee_departure" op.
    
    De bruger derefter Graph-API'erne til datastyring til at oprette en hændelse for den tilknyttede hændelsestype. Opbevaringsperioden for de fortrolige dokumenter starter, når denne hændelse er oprettet.

Du kan få flere oplysninger om Graph-API'er til datastyring under [Brug Microsoft Graph Records Management API](/graph/api/resources/security-recordsmanagement-overview?view=graph-rest-beta&preserve-view=true).

Hvis du vil have licenskrav til at bruge disse API'er, skal du se afsnittet om datastyring fra [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).
