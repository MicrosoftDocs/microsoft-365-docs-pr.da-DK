---
title: Kendte problemer med Microsoft 365 Fyrtårn
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthous
search.appverid: MET150
description: For MSP'er (Managed Service Providers), der bruger Microsoft 365 Lighthouse, skal du se en liste over kendte problemer for Lighthouse efter funktionsområde.
ms.openlocfilehash: 61073729b9589033ab361973c1c87bac2b28959a
ms.sourcegitcommit: 04a93269fbbbdb5513335422cabdc1b269ead5ac
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/18/2022
ms.locfileid: "66160814"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Kendte problemer med Microsoft 365 Fyrtårn

I denne artikel beskrives de kendte problemer for Microsoft 365 Fyrtårn efter funktionsområde. Du kan få flere oplysninger om Lighthouse i [Oversigt over Microsoft 365 Fyrtårn](m365-lighthouse-overview.md).

## <a name="users"></a>Brugere

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Helpdesk Agent kan ikke nulstille en brugeradgangskode** | MSP-teknikere (Managed Service Provider), der er medlemmer af gruppen Helpdesk Agent, kan ikke nulstille adgangskoder for brugere i kundelejere. Når brugeren forsøger at nulstille adgangskoden for en bruger, får vedkommende vist følgende fejlmeddelelse: "Du har ikke tilladelse til at gøre dette. [Få mere at vide](m365-lighthouse-configure-portal-security.md)" | Helpdesk Agents skal nulstille adgangskoder ved hjælp af Microsoft 365 Administration eller Azure Active Directory for at løse problemet med tilladelser. |

## <a name="devices"></a>Enheder

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Slettet politik vises** | Når en politik for enhedsoverholdelse er blevet slettet fra Intune, vil den midlertidigt fortsat være synlig i Lighthouse. Hvis MSP-teknikere forsøger at foretage en politiksammenligning, der indeholder en politik, der er blevet slettet, får teknikerne vist følgende fejl: "Noget gik galt. Opdater siden, og prøv igen." | Du kan løse fejlen ved at rydde den slettede politik fra politiksammenligningen og kun sammenligne eksisterende politikker. |

## <a name="threat-management"></a>Trusselsstyring

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Trusselsnavnet mangler** | Når MSP-teknikere får vist listen over trusler fra siden Threat Management, kan nogle trusler mangle navnet på truslen. Dette sker, når den enhed, som truslen blev registreret på, for nylig blev fjernet fra Intune. | Problemet løses inden for 48 timer. Der kræves ingen yderligere trin. |

## <a name="baselines"></a>Grundlinjer

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Modstridende indstillinger ved sammenligning af bloker ældre godkendelse og MFA-udrulningstrin** | Hvis en kundelejer har installeret bloker ældre godkendelse og et af MFA-udrulningstrinnene, vil en sammenligningstest fejlagtigt beskrive disse indstillinger som modstridende. | Der kræves ingen løsning. Indstillingerne er faktisk ikke i konflikt, og brugerne i kundelejer påvirkes ikke. |

## <a name="windows-365"></a>Windows 365

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Der opstod en fejl under forsøg på at klargøre igen** | MSP-teknikere får fejlmeddelelsen "Du har ikke tilladelse til at gøre dette", når de forsøger at klargøre en Cloud-pc igen. | Du kan løse dette problem ved at logge på kundelejeren og derefter klargør cloud-pc'er fra Microsoft Endpoint Manger Administration. Du kan finde instruktioner under [Klargør en cloud-pc](/windows-365/enterprise/reprovision-cloud-pc) igen. |

## <a name="audit-logs"></a>Overvågningslogge


| Problem | Beskrivelse | Løsning |
|--|--|--|
| **Deaktiverings- og genaktiveringshandlinger er ikke angivet i overvågningslogge** | Følgende aktiviteter rapporteres i øjeblikket ikke på siden Overvågningslogge i Lighthouse: <ul><li>Navn: offboardTenant \| Action: Inaktiver en kunde</li> <li>Navn: resetTenantOnboardingStatus \| Action: Reactive customer</li></ul> | Der er ingen løsning, men vi arbejder på at løse problemet. Disse aktiviteter vises i overvågningslogge, når rettelsen er installeret i tjenesten. |
| **Filteret viser ikke alle brugere** | Når MSP-teknikere forsøger at filtrere ved hjælp af **Initieret** af, vises listen over alle UPN'er (User Principal Names) – svarende til mail-id'er for de teknikere, der startede handlinger, der genererer overvågningslogge – ikke fuldt ud under filteret.<br><br>Bemærk, at selve overvågningsloggene vises fuldt ud. Det er kun muligheden for at filtrere dem ved hjælp af **Initieret af** , der påvirkes. | Der er ingen løsning, men vi arbejder på at løse problemet. Filteret vender tilbage til den forventede funktionsmåde – der viser den komplette liste over UPN'er, der skal filtreres efter – når rettelsen er installeret i tjenesten. |

## <a name="delegated-admin-privileges-dap"></a>Delegerede Administration rettigheder (DAP)

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Tilladelsesforskydning ved ændring af DAP-roller** | Hvis en MSP-tekniker føjes til eller fjernes fra gruppen Administration Agent eller Helpdesk Agent, kan der opstå en forsinkelse, der afspejler de relevante tilladelser i Lighthouse. | Problemet løses inden for 30 minutter. Der kræves ingen yderligere trin. |

## <a name="granular-delegated-admin-privileges-gdap"></a>Detaljeret delegerede Administration rettigheder (GDAP)

Enten GDAP (Granular Delegated Administration Privileges) plus en indirekte forhandlerrelation eller en DAP-relation (Delegated Administration Privileges) er påkrævet for at onboarde kunder til Lighthouse. Hvis DAP og GDAP eksisterer i en kundelejer, har GDAP-tilladelserne forrang for MSP-teknikere i GDAP-aktiverede sikkerhedsgrupper. Kunder med kun GDAP-relationer (uden indirekte forhandlerrelationer) kan i øjeblikket ikke onboarde til Lighthouse, men vil kunne onboarde i en fremtidig version.<br><br>

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Forskellige problemer med GDAP-tilladelser på tværs af Lighthouse** | Visse GDAP-roller tildeler ikke i sig selv det samme adgangsniveau til kundedata i Lighthouse, som de ville gøre i en oplevelse med en enkelt lejer. Hvis en af følgende roller tildeles individuelt (dette er ikke i kombination med andre GDAP-roller) til MSP-teknikere, kan der opstå fejl, herunder:<ul><li>GDAP-sikkerhedsadministratorer kan ikke få vist risikable brugere, afvise risici eller bekræfte kompromitterede brugere i Lighthouse.</li><li>GDAP-sikkerhedslæsere kan ikke se risikable brugere i Lighthouse.</li><li>Globale GDAP-administratorer får vist en fejlmeddelelse, når de forsøger at få vist tjenestetilstanden i Lighthouse.</li><li>Globale GDAP-administratorer oplever problemer med installationsplanen i Lighthouse.</li></ul> | Løsningen er at tildele en kombination af GDAP-roller til MSP-teknikere baseret på det adgangsniveau for kundedata, de har brug for. Du kan se en liste over anbefalede GDAP-roller til at bruge Lighthouse [under Oversigt over tilladelser i Microsoft 365 Fyrtårn](m365-lighthouse-overview-of-permissions.md).<br><br>I forbindelse med problemer, hvor selv globale GDAP-administratortilladelser ikke tillader brug af en funktion i Lighthouse, er løsningen at få adgang til det relevante administrationscenter fra kundelejer for at administrere kunden (f.eks. få adgang til Microsoft 365 Administration fra kundens lejer for at kontrollere tjenestetilstanden). Du kan finde instruktioner til, hvordan du ændrer en GDAP-relation, under [Få detaljerede administratortilladelser til at administrere en kundes tjeneste – Partnercenter](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). |

## <a name="localization"></a>Lokalisering

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Oversættelsesproblemer** | Brugerne kan opleve problemer med oversættelse af sprog, når sproget i deres browser eller deres valg af sprog i Lighthouse er andet end engelsk. | Hvis du vil minimere oversættelsesproblemer i Lighthouse, skal du sørge for, at browserens valg af sprog stemmer overens med sprogindstillingen på Lighthouse-portalen. Hvis du vil ændre sprogvalget i Lighthouse, skal du logge på Lighthouse og vælge tandhjulsikonet øverst på siden for at åbne siden Med portalindstillinger, vælge **Sprog + område** og derefter vælge de relevante sprog- og internationale formater. |

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 Ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Foretag fejlfinding af fejlmeddelelser og problemer i Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (artikel)\
[Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artikel)
