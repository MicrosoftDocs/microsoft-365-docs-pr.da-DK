---
title: Microsoft 365 mulighed for udvidelse af overholdelse
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Få mere at vide Microsoft 365 løsninger til overholdelse af regler og standarder ved hjælp af tredjepartsdataforbindelser og Microsoft Graph API'er.
ms.openlocfilehash: 0632de40141b86e6dfdebf3f5c3a97ca50219357
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590655"
---
# <a name="microsoft-365-compliance-and-microsoft-priva-extensibility"></a>Microsoft 365 overholdelse af regler og standarder og Microsoft Pr extensibility

Microsoft 365 løsninger til overholdelse af regler og standarder hjælper organisationer med intelligent at vurdere deres kompatibilitetsrisici, styre og beskytte følsomme data og på effektiv vis reagere på lovmæssige krav. Microsoft 365 er omfattende i forbindelse med udvidelsesmuligheder og gør det muligt for organisationer at tilpasse, udvide, integrere, fremskynde og understøtte deres løsninger til overholdelse af regler og standarder.

Der er to vigtige byggesten til udvidelse af overholdelsesmuligheder:

- **Dataforbindelser**. Bruges til at importere og arkivere ikke-Microsoft-data, så du Microsoft 365 funktioner til beskyttelse og styring på tredjepartsdata.

- **API'er**. Aktiverer programmeringsadgang til Microsoft 365 overholdelse af regler og standarder.

## <a name="data-connectors"></a>Dataforbindelser

Microsoft leverer dataforbindelser fra tredjepart, der kan konfigureres i Microsoft 365 Overholdelsescenter. Du kan finde en liste over dataforbindelser, der leveres af Microsoft, [i tabellen Dataforbindelser fra tredjepart](archiving-third-party-data.md#third-party-data-connectors) . Tabellen over tredjepartsdataforbindelser opsummerer også de løsninger til overholdelse, som du kan anvende på tredjepartsdata, når du har importeret og arkiveret data i Microsoft 365, og links til den trinvise vejledning for hver forbindelse.

Du kan få mere Microsoft 365 om dataforbindelser i [Arkivering af tredjepartsdata](archiving-third-party-data.md). Hvis en tredjepartsdatatype ikke understøttes af de dataforbindelser, der er tilgængelige i Microsoft 365 Overholdelsescenter, kan du arbejde med en partner, der kan give dig en brugerdefineret forbindelse. Hvis du vil have en liste over de partnere, du kan arbejde med, og den trinvise proces for denne metode, skal du se Arbejde sammen med en partner om at [arkivere tredjepartsdata](work-with-partner-to-archive-third-party-data.md).

### <a name="prerequisites-for-data-connectors"></a>Forudsætninger for dataforbindelser

Mange af de dataforbindelser, der er tilgængelige i Microsoft 365 Overholdelsescenter til at importere og arkivere tredjepartsdata, kræver, at du forbereder og udfører konfigurationsopgaver i tredjepartsdatakilden. Disse forudsætninger er beskrevet detaljeret for hver tredjeparts dataforbindelse.

For dataforbindelser i Microsoft 365 Overholdelsescenter, der leveres af en af Microsofts partnere, skal din organisation have en forretningsrelation med partneren, før du kan installere en forbindelse.

Du kan finde vejledning og krav til tredjepartsdataforbindelser i afsnittet "Dataforbindelser" i Microsoft 365 for sikkerhedsoplysninger & overholdelse af regler og [| Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="apis"></a>API'er

Microsoft 365 og Microsoft Pr dll-API'er er tilgængelige i Microsoft Information Protection SDK, Microsoft Graph API og Office 365 Management Activity API. Nogle API'er til overholdelse er del af et nyt sæt API'er til sikkerhed og overholdelse, som gør det muligt for udviklere af Microsoft 365-kunder, uafhængige softwareleverandører, systemintegratorer og administrerede sikkerhedstjenesteudbydere at opbygge sikkerheds- og overholdelsesløsninger af høj værdi.

Du kan få mere at vide om, hvordan du får Graph API'er, [under Oversigt over Microsoft Graph](/graph/overview).

### <a name="microsoft-graph-apis-for-subject-rights-requests"></a>Microsoft Graph API'er til anmodninger om emnerettigheder

I henhold til visse regler om beskyttelse af personlige oplysninger over hele verden kan enkeltpersoner anmode om at gennemse eller administrere de personlige data om sig selv, som virksomheder har indsamlet. Disse anmodninger kaldes for *emnerettighedersanmodninger* inden for løsningen Microsoft Priver-emnerettighedersanmodninger. Anmodninger om emnerettigheder kaldes også anmodninger *om* databehandlere (DSR'er) eller anmodninger om adgang for *den registrerede* . Microsoft Graph API'er til anmodninger om emnerettigheder gør det muligt for udviklere at integrere Microsoft 365 relaterede emnerettighedersanmodninger med det bredere økosystem til beskyttelse af personlige oplysninger. Denne API-baserede udvidelse gør det muligt for organisationer at besvare anmodninger om emnerettigheder på en ensartet måde på tværs af hele deres dataområde, som dækker både Microsoft- og ikke-Microsoft-miljøer. Denne funktion hjælper også med skalering med automatisering på skalaen og hjælper organisationer med at opfylde branchebestemmelser mere effektivt uden at være afhængig af manuelle processer.

Du kan få mere at vide under [Microsoft Graph API'er for anmodning om emnerettigheder](/graph/api/resources/subjectrightsrequest-subjectrightsrequestapioverview).

### <a name="microsoft-information-protection-mip-sdk"></a>Microsoft Information Protection (MIP) SDK

MIP SDK viser mærknings- og beskyttelsestjenester fra Microsoft 365-sikkerheds- og overholdelsescenter til tredjepartsprogrammer og -tjenester. Udviklere kan bruge SDK til at opbygge indbygget understøttelse til at anvende navne og beskyttelse på filer. Udviklere kan bestemme, hvilke handlinger der skal udføres, når bestemte navne registreres, og årsagen er over MIP-krypterede oplysninger.

Eksempler på brug af MIP-SDK på højt niveau omfatter:

- En line of business-applikation, der anvender klassificeringsetiketter på filer ved eksport.

- Et CAD-/CAM-designprogram, der leverer indbygget understøttelse af MIP-mærkning.

- En sikkerhedsmægler eller løsning til forebyggelse af datatab i skyen, der kan kryptere data med Azure Information Protection.

Du kan få mere at vide om MIP SDK, forudsætninger, yderligere scenarier og eksempler under [Oversigt over MIP SDK](/information-protection/develop/overview).

### <a name="microsoft-graph-api-for-teams-dlp"></a>Microsoft Graph API til Teams DLP

[Funktioner til forebyggelse af datatab (DLP)](dlp-microsoft-teams.md) anvendes i stor grad Microsoft Teams organisationer har skiftet til fjernarbejde. For nylig [annoncerede vi den generelle](https://devblogs.microsoft.com/microsoft365dev/change-notifications-for-microsoft-teams-messages-now-generally-available/) tilgængelighed af Microsoft Graph Change Notification API for meddelelser i Teams. Denne API gør det muligt for udviklere at opbygge apps, der kan lytte Microsoft Teams meddelelser i næsten realtid og derefter implementere DLP-scenarier for både kunder og partnere. Desuden giver Microsoft Graph Patch API dig mulighed for at anvende DLP-handlinger til at Teams meddelelser.

Disse to API'er udgør Microsoft Graph API til Teams DLP. Du kan komme i gang ved at afprøve [eksempelappen](https://github.com/microsoftgraph/aspnetcore-webhooks-sample). Du kan finde flere Microsoft Teams om mailwebhooks i [dokumentationen](/graph/api/subscription-post-subscriptions).

For licenseringskravene til Teams DLP skal du [Microsoft 365 vejledning til licensering for at & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-api-for-ediscovery-preview"></a>Microsoft Graph API til eDiscovery (forhåndsvisning)

Med [Advanced eDiscovery](overview-ediscovery-20.md) kan organisationer opdage data, hvor de findes, og administrere mere ende-til-ende eDiscovery-arbejdsprocesser med intelligent maskinlæring og analysefunktioner for at reducere data til det relevante sæt – alt sammen mens dataene forbliver inden for Microsoft 365-sikkerheds- og overholdelsesrammen.

Graph API'er til Advanced eDiscovery kan bruges til at oprette og administrere sager, gennemse sæt og gennemse sætforespørgsler på en skalerbar og gentagen måde. Dette giver kunder og partnere mulighed for at oprette apps og arbejdsprocesser for at automatisere almindelige og gentagne processer, f.eks oprettelse af sager og administration af ledende kunder og juridiske fast hold.

Det første sæt af Graph API'er til eDiscovery er tilgængelige i offentlig prøveversion. Vi planlægger at tilføje flere funktioner i slutningen af kalenderåret. Hvis du vil have mere at vide om disse API'er og andre Advanced eDiscovery, skal du se denne [blog](https://aka.ms/Ignite2020AeDAA).

For licenskrav til Advanced eDiscovery og API'en skal du se afsnittet "eDiscovery" i [Microsoft 365-licensvejledning for sikkerhed & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#ediscovery).

### <a name="microsoft-graph-api-for-teams-export"></a>Microsoft Graph API til Teams eksport

Enterprise Information Archiving (EIA) for Microsoft Teams er et vigtigt scenarie for vores kunder, da det giver dem mulighed for at løse i forbindelse med lovmæssige krav. Ud over vores indbyggede funktioner til arkivering af indhold i Microsoft Teams kan kunder og partnere nu bruge Teams-eksport-API'er til at løse problemer med brugerdefinerede program- og integrationsscenarier. Eksport-TEAMS understøtter masseeksport (op til 200 anmodninger pr. sekund/pr. app/pr. lejer) Teams meddelelser og vedhæftede filer. Slettede meddelelser er også tilgængelige for API'en i op til 30 dage, efter de er blevet slettet. Du kan finde flere oplysninger Teams eksportere API'er til eksport, og hvordan du bruger dem i dine programmer, under Eksportere indhold Microsoft Teams [eksportere API'er](/microsoftteams/export-teams-content).

For licenskrav til brug af TEAMS Export API'er skal du [Microsoft 365 vejledning til licensering for at få sikkerhedsoplysninger & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

### <a name="microsoft-graph-connector-apis-preview"></a>API'er Graph forbindelse (forhåndsvisning)

Med [Microsoft Graph forbindelser kan](/microsoftsearch/connectors-overview) organisationer indeksere tredjepartsdata, så de vises i Microsoft Søg resultater. Denne funktion udvider de typer indholdskilder, der kan søges i i dine Microsoft 365 og det bredere Microsoft-økosystem. Tredjepartsdata kan hostes lokalt eller i offentlige eller private skyer. Fra og Advanced eDiscovery viser udviklerens eksempel på indbygget overholdelsesværdi for de tilknyttede Microsoft 365 apps. Dette muliggør overholdelse af regler og standarder for apps, der integreres i Microsoft 365 at styrke brugere med problemfri overholdelsesoplevelser. Hvis du vil have mere at vide om, hvordan du inkorporerer Microsoft Graph Connector-API'er i din appvisning, skal du se Opret, opdater og slet forbindelser i [Microsoft Graph](/graph/connecting-external-content-connectors-api-overview).
