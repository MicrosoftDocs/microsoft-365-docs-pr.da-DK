---
title: Kendte problemer med Microsoft 365 fyrtårn
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, skal du se en liste over kendte problemer for fyrtårnet efter funktionsområde.
ms.openlocfilehash: 3151937d4552da09c9cfd6808db2bad8bafbbc46
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594659"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Kendte problemer med Microsoft 365 fyrtårn

I denne artikel beskrives de kendte problemer for Microsoft 365 fyrtårn efter funktionsområde. Du kan finde flere oplysninger om Lighthouse [i Oversigt over Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Brugere

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Helpdesk-agent kan ikke nulstille en brugeradgangskode** | De teknikere, der er medlem af Helpdesk-agentgruppen, kan ikke nulstille adgangskoder for brugere i kundelejere. Når brugeren forsøger at nulstille adgangskoden, får brugeren vist følgende fejlmeddelelse: "Du har ikke tilladelse til at gøre dette. [Få mere at vide](m365-lighthouse-configure-portal-security.md)" | Helpdesk-agenter bør nulstille adgangskoder ved hjælp af tilladelser for at løse problemet med tilladelser ved Microsoft 365 Administration eller Azure Active Directory. |

## <a name="devices"></a>Enheder

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Slettet politik vises** | Når en politik for overholdelse af enhed er blevet slettet Intune, vil den midlertidigt fortsat være synlig i Fyrtårn. Hvis MSP-teknikere forsøger at foretage en sammenligning af politikker, der omfatter en politik, der er blevet slettet, får teknikeren følgende fejl: "Noget gik galt. Opdater siden, og prøv igen." | Du kan løse fejlen ved at fjerne den slettede politik fra en sammenligning af politikken og kun sammenligne eksisterende politikker. |

## <a name="threat-management"></a>Administration af trusler

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Trusselsnavn mangler** | Når MSP-teknikere får vist listen over trusler fra siden Trusselsadministration, kan der være nogle trusler, der mangler navnet på truslerne. Dette sker, når den enhed, som trussel blev registreret på, for nylig blev fjernet Intune. | Problemet vil blive løst inden for 48 timer. Der kræves ingen yderligere trin. |

## <a name="baselines"></a>Oprindelige planer

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Modstridende indstillinger ved sammenligning af ældre godkendelsestrin og MFA-installationstrin** | Hvis en kundelejer har installeret bloker for ældre godkendelse og et af installationstrinnene til MFA, vil en sammenligningstest fejlagtigt beskrive disse indstillinger som modstridende. | Der kræves ingen løsning. Indstillingerne er ikke i konflikt, og brugerne i kundelejeren påvirkes ikke. |

## <a name="windows-365"></a>Windows 365

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Prøv klargøringsfejl igen** | MSP-teknikere får fejlmeddelelsen "Du har ikke tilladelse til at gøre dette", når du forsøger at forsøge klargøring af en sky-pc igen. | Du kan løse dette problem ved at logge på kundelejeren og derefter installere sky-pc'er igen fra Microsoft Endpoint Manger Administration. Du kan finde en vejledning [under Genopdeling af en sky-pc](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="audit-logs"></a>Overvågningslogfiler


| Problem | Beskrivelse | Løsning |
|--|--|--|
| **Handlingerne Deaktiver og Genaktiver vises ikke i overvågningslogge** | Følgende aktiviteter rapporteres i øjeblikket ikke på siden Overvågningslogfiler i Fyrtårn: <ul><li>Navn: offboardTenant-handling \| : Deaktiver en kunde</li> <li>Navn: resetTenantOnboardingStatus \| Action: Reactive customer</li></ul> | Der findes ingen løsning, men vi arbejder på at finde en løsning. Disse aktiviteter vises i overvågningslogfilerne, når rettelsen er implementeret i tjenesten. |
| **Filter viser ikke alle brugere** | Når MSP-teknikere forsøger at filtrere ved hjælp af Startet **af, vises** listen over alle BRUGERENS hovednavne (UPN'er) – svarende til mail-id'er for de teknikere, der startede handlinger, der genererer overvågningslogfiler – ikke fuldt ud under filteret.<br><br>Bemærk, at selve overvågningsloggen vises fuldt ud. kun muligheden for at filtrere dem ved hjælp **af Startet af** påvirkes. | Der findes ingen løsning, men vi arbejder på at finde en løsning. Filteret vender tilbage til dets forventede funktionsmåde – viser den komplette liste over UPN'er, der skal filtreres efter – når rettelsen er implementeret i tjenesten. |

## <a name="delegated-admin-privilegesdap"></a>Delegerede administratorrettigheder (DAP)

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Forsinkelse af tilladelser, når du ændrer DAP-roller** | Hvis en MSP-tekniker føjes til eller fjernes fra administratoragenten eller helpdeskagentgruppen, kan der være en forsinkelse, som afspejler de relevante tilladelser i Lighthouse. | Problemet vil blive løst inden for 30 minutter. Der kræves ingen yderligere trin. |

## <a name="granular-delegated-admin-privilegesgdap"></a>Detaljeret delegeret administratorrettigheder (GDAP)

> [!NOTE]
> GDAP er i øjeblikket i [Technical Preview](/partner-center/announcements/2022-february#6) (offentlig prøveversion) for at give partnere mulighed for at tildele detaljerede tilladelser, før GDAP er alment tilgængelig.

I øjeblikket er DAP påkrævet for at onboarde kunder til Lighthouse. Vi anbefaler også at etablere GDAP med dine kunder for at give en mere sikker delegeret adgang. Mens DAP og GDAP coexist anvendes, har GDAP forrang for kunder, hvor begge modeller er på plads. Kunder med just GDAP (og ingen DAP) vil snart kunne onboarde til Lighthouse.<br><br>

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Forskellige problemer med GDAP-tilladelser på tværs af Lighthouse** | Visse GDAP-roller giver i sig selv ikke samme niveau af adgang til kundedata i Lighthouse, som de ville gøre i en enkelt lejeroplevelse. Hvis en af følgende roller tildeles individuelt (dette er, ikke i kombination med andre GDAP-roller) til MSP-teknikere, kan de støde på fejl, herunder:<ul><li>GDAP-sikkerhedsadministratorer kan ikke få vist risikabele brugere, afvise risici eller bekræfte kompromitterede brugere i Lighthouse.</li><li>GDAP-sikkerhedslæsere kan ikke få vist risikabele brugere i Lighthouse.</li><li>Globale GDAP-administratorer får vist en fejlmeddelelse, når de forsøger at få vist tjenestestilstanden i Lighthouse.</li><li>GLOBALE GDAP-administratorer oplever problemer med at udrulle installationsplantrin i Lighthouse.</li></ul> | Løsningen er at tildele en kombination af GDAP-roller til MSP-teknikere baseret på det adgangsniveau til kundedata, de har brug for. Hvis du vil have en liste over anbefalede GDAP-roller til at bruge Lighthouse, skal du [se Oversigt over tilladelser Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).<br><br>I forbindelse med problemer, hvor selv GDAP's globale administratortilladelser ikke tillader brug af en funktion i Lighthouse, kan du løse problemet ved at få adgang til det relevante Administration fra kundelejeren for at administrere kunden (f.eks. få adgang til Microsoft 365 Administration fra kundelejeren for at kontrollere tjenestens tilstand). Du kan finde en vejledning til, hvordan du redigerer en GDAP-relation, under Få detaljerede administratortilladelser til at administrere en [kundes tjeneste – Partnercenter](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). |

## <a name="localization"></a>Lokalisering

| Problem | Beskrivelse | Løsning |
| ---------------- | ---------------- | ---------------- |
| **Problemer med oversættelse** | Brugerne kan opleve problemer med sprogoversættelse, når sproget i deres browser, eller deres sprogvalg i Lighthouse, er noget andet end engelsk. | For at minimere oversættelsesproblemer i Lighthouse skal du sørge for, at browserens sprogvalg stemmer overens med sprogindstillingen i Fyrtårnsportalen. Hvis du vil ændre sprogvalget i Fyrtårn, skal du logge på Fyrtårn og vælge tandhjulsikonet øverst på siden for at åbne siden Portalindstillinger, vælge Sprog **+ område** og derefter vælge det rette sprog og de relevante internationale formater. |

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Fejlfinding og løsning af problemer og fejlmeddelelser i Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (artikel)\
[Få hjælp og support til Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (artikel)