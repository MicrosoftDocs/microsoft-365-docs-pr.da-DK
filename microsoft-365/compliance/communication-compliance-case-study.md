---
title: Casestudie – Contoso konfigurerer en upassende tekstpolitik
description: En casestudie for Contoso, og hvordan de hurtigt konfigurerer en politik for overholdelse af angivne standarder for kommunikation for at overvåge upassende tekst i Microsoft Teams, Exchange Online og Yammer kommunikation.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.custom:
- admindeeplinkMAC
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- remotework
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 756c6dfdafb6329fa2df6a4231e9630647d9d11e
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971919"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-text-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Casestudie – Contoso konfigurerer hurtigt en upassende tekstpolitik for Microsoft Teams, Exchange og Yammer kommunikation

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Communication Compliance hjælper med at minimere kommunikationsrisici ved at hjælpe dig med at registrere, registrere og reagere på meddelelser med upassende tekst i din organisation. upassende tekst kan omfatte bandeord, trusler, chikane og upassende billeder. Foruddefinerede og brugerdefinerede politikker giver dig mulighed for at scanne intern og ekstern kommunikation for politikkampe, så de kan undersøges af udpegede korrekturlæsere. Korrekturlæsere kan undersøge scannede mails, Microsoft Teams, Yammer eller tredjepartskommunikation i din organisation og udføre de nødvendige afhjælpningshandlinger for at sikre, at de overholder organisationens meddelelsesstandarder.

Contoso Corporation er en fiktiv organisation, der hurtigt skal konfigurere en politik for at overvåge upassende tekst. De har brugt Microsoft 365 primært til mail, Microsoft Teams og Yammer støtte til deres brugere, men har nye krav til at håndhæve virksomhedens politik omkring chikane på arbejdspladsen. Contoso-it-administratorer og overholdelsesspecialister har en grundlæggende forståelse af de grundlæggende funktioner i at arbejde med Microsoft 365 og er på udkig efter komplette retningslinjer for, hvordan du hurtigt kommer i gang med overholdelse af angivne standarder for kommunikation.

I denne casestudie beskrives det grundlæggende om hurtigt at konfigurere en politik for overholdelse af angivne standarder for kommunikation for at overvåge kommunikation for upassende tekst. Denne vejledning omfatter:

- Trin 1 – Planlægning af overholdelse af kommunikation
- Trin 2 – Adgang til overholdelse af kommunikation
- Trin 3 – Konfiguration af forudsætninger og oprettelse af en politik for kommunikation med overholdelse af angivne standarder
- Trin 4 – Undersøgelse og afhjælpning af beskeder

## <a name="step-1-planning-for-communication-compliance"></a>Trin 1: Planlægning af overholdelse af kommunikation

Contoso-it-administratorer og overholdelsesspecialister deltog i onlinewebinarer om løsninger til overholdelse af angivne standarder i Microsoft 365 og besluttede, at politikker for overholdelse af angivne standarder for kommunikation vil hjælpe dem med at opfylde de opdaterede krav til virksomhedens politik for reduktion af chikane på arbejdspladsen. Når de arbejder sammen, har de udviklet en plan om at oprette og aktivere en politik for overholdelse af kommunikation, der overvåger upassende tekst til chats, der sendes i Microsoft Teams, private meddelelser og communitysamtaler i Yammer og i mails, der sendes i Exchange Online. Deres plan omfatter identificering af:

- It-administratorer, der skal have adgang til funktioner til kommunikation med overholdelse af angivne standarder.
- De overholdelsesspecialister, der skal oprette og administrere kommunikationspolitikker.
- Overholdelsesspecialister og andre kollegaer i andre afdelinger (Hr, Juridisk osv.), der skal undersøge og afhjælpe beskeder om kommunikation med overholdelse af angivne standarder.
- De brugere, der vil være omfattet af politikken for kommunikation med overholdelse af angivne standarder.

### <a name="licensing"></a>Licensering

Det første trin er at bekræfte, at Contosos Microsoft 365-licenser omfatter understøttelse af løsningen til kommunikationsoverholdelse. For at få adgang til og bruge overholdelse af kommunikation skal Contoso-it-administratorer bekræfte, at Contoso har en af følgende:

- Microsoft 365 E5/A5/F5/G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3/A3/F3/G5-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Compliance
- Microsoft 365 E3/A3/F3/G5-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 A5 abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (ikke længere tilgængeligt for nye abonnementer, se note)

Brugere, der er inkluderet i politikker for kommunikation med overholdelse af angivne standarder, skal tildeles en af licenserne ovenfor. Du kan finde flere oplysninger om abonnementer og licenser i [Microsoft 365 vejledning til overholdelse af & sikkerhed](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Avanceret overholdelse i Office 365 sælges ikke længere som et separat abonnement. Når de aktuelle abonnementer udløber, skal kunderne overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af angivne standarder.

Contoso-it-administratorer gør følgende for at bekræfte licensunderstøttelse for Contoso:

1. It-administratorer logger på Microsoft 365 Administration <https://admin.microsoft.com> og går til Microsoft 365 Administration > **FaktureringLicenser** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

2. Her bekræfter de, at de har en af de [licensmuligheder](communication-compliance-configure.md#subscriptions-and-licensing) , der omfatter understøttelse af kommunikation med overholdelse af angivne standarder.

![Licenser til kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Tilladelser til kommunikation med overholdelse af angivne standarder

Der er fem rollegrupper, der bruges til at konfigurere tilladelser til at administrere funktioner til kommunikation med overholdelse af angivne standarder. Contoso-administratorer tildeles rollen *Administrator af kommunikationsoverholdelse* for at gøre **Kommunikationsoverholdelse** tilgængelig som en menuindstilling på Microsoft Purview-overholdelsesportalen og for at fortsætte med disse konfigurationstrin.

Contoso beslutter at bruge rollegruppen *Kommunikationsoverholdelse* til at tildele alle administratorer, analytikere, efterforskere og seere til gruppen for kommunikationsoverholdelse. Det gør det nemmere for Contoso at komme hurtigt i gang og passer bedst til deres krav til overholdelse af angivne standarder.

|**Rolle**|**Rolletilladelser**|
|:-----|:-----|
| **Kommunikation med overholdelse af angivne standarder** | Brug denne rollegruppe til at administrere overholdelse af kommunikation for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere kan du konfigurere tilladelser til kommunikation med overholdelse af angivne standarder i en enkelt gruppe. Denne rollegruppe indeholder alle tilladelser til kommunikation med overholdelse af angivne standarder. Denne konfiguration er den nemmeste måde hurtigt at komme i gang med overholdelse af angivne standarder for kommunikation på, og den er velegnet til organisationer, der ikke har brug for separate tilladelser, der er defineret for separate grupper af brugere. |
| **Administrator af kommunikation med overholdelse af angivne standarder** | Brug denne rollegruppe til først at konfigurere overholdelse af kommunikation og senere til at adskille administratorer af kommunikation med overholdelse af angivne standarder i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for kommunikation med overholdelse af angivne standarder, globale indstillinger og tildelinger af rollegrupper. Brugere, der er tildelt denne rollegruppe, kan ikke få vist meddelelsesbeskeder. |
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt til denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist meddelelsesmetadata (ikke meddelelsesindhold), eskalere til yderligere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse ventende beskeder. |
| **Efterforsker af kommunikation med overholdelse af angivne standarder** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som undersøgere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt denne rollegruppe, kan få vist metadata og indhold, eskalere til yderligere korrekturlæsere, eskalere til en eDiscovery-sag (Premium), sende meddelelser til brugere og løse beskeden. |
| **Meddelelsesoverholdelsesfremviser** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden for kommunikation med overholdelse af angivne standarder og kan få vist alle rapporter om kommunikation med overholdelse af angivne standarder. |

1. Contoso-it-administratorer logger på siden med tilladelser til [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/permissions) ved hjælp af legitimationsoplysninger for en global administratorkonto og vælger linket for at få vist og administrere roller i Microsoft 365.
2. På Microsoft Purview-overholdelsesportalen går de til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a> og vælger linket for at få vist og administrere roller i Office 365.
3. Administratorerne vælger rollegruppen *Kommunikationsoverholdelse* og vælger derefter **Rediger rollegruppe**.
4. Administratorer vælger **Vælg medlemmer** i venstre navigationsrude og vælger derefter **Rediger**.
5. De vælger **Tilføj** og markerer derefter afkrydsningsfeltet for alle Contoso-brugere, der skal administrere kommunikation med overholdelse af angivne standarder, undersøge og gennemse beskeder.
6. Administratorer vælger **Tilføj** og vælger derefter **Udført**.
7. De vælger **Gem** for at føje Contoso-brugere til rollegruppen. De vælger **Luk** for at fuldføre trinnene.

## <a name="step-2-accessing-communication-compliance"></a>Trin 2: Adgang til overholdelse af kommunikation

Når du har konfigureret tilladelserne til overholdelse af kommunikationsoverholdelse, kan Contoso-it-administratorer og overholdelsesspecialister, der er tildelt rollegruppen Kommunikationsoverholdelse, få adgang til løsningen til kommunikationsoverholdelse i Microsoft Purview. Contoso-it-administratorer og overholdelsesspecialister har flere måder at få adgang til overholdelse af kommunikation på og komme i gang med at oprette en ny politik:

- Starter direkte fra løsningen til overholdelse af kommunikationsoverholdelse
- Starter fra Microsoft Purview-overholdelsesportalen
- Starter fra Microsoft Purview-løsningskataloget
- Fra og med Microsoft 365 Administration

### <a name="starting-directly-from-the-communication-compliance-solution"></a>Starter direkte fra løsningen til overholdelse af kommunikationsoverholdelse

Den hurtigste måde at få adgang til løsningen på er ved at logge direkte på løsningen **til overholdelse af kommunikation** (<https://compliance.microsoft.com/supervisoryreview>). Ved hjælp af dette link dirigeres Contoso-it-administratorer og overholdelsesspecialister til dashboardet Oversigt over kommunikation, hvor du hurtigt kan gennemse status for beskeder og oprette nye politikker ud fra de foruddefinerede skabeloner.

![Oversigt over kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-purview-compliance-portal"></a>Starter fra Microsoft Purview-overholdelsesportalen

En anden nem måde for Contoso-it-administratorer og overholdelsesspecialister at få adgang til løsningen til kommunikation med overholdelse af angivne standarder på er ved at logge på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com) direkte. Når brugerne er logget på, skal de blot vælge kontrolelementet **Vis alle** for at få vist alle løsninger til overholdelse af angivne standarder og derefter vælge løsningen **Kommunikation for** at komme i gang.

![Overholdelsescenter.](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-purview-solution-catalog"></a>Starter fra Microsoft Purview-løsningskataloget

Contoso-it-administratorer og overholdelsesspecialister kan også vælge at få adgang til løsningen til kommunikationsoverholdelse ved at vælge kataloget til Microsoft Purview-løsning. Ved at vælge **Katalog** i afsnittet **Løsninger** i venstre navigationsrude, mens de er på **Microsoft Purview-overholdelsesportalen**, kan de åbne løsningskataloget med en liste over alle Microsoft Purview-løsninger. Når du ruller ned til afsnittet **Styring af insiderrisiko** , kan Contoso-it-administratorer vælge Kommunikation med overholdelse af angivne standarder for at komme i gang. Contoso-it-administratorer beslutter også at bruge kontrolelementet Vis i navigation til at fastgøre løsningen til kommunikation med overholdelse af angivne standarder i venstre navigationsrude for at få hurtigere adgang, når de logger på fremover.

![Løsningskatalog.](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>Fra og med Microsoft 365 Administration

Contoso-it-administratorer og overholdelsesspecialister logger på Microsoft 365 Administration [(https://admin.microsoft.com)](https://admin.microsoft.com) for at få adgang til overholdelse af angivne standarder, når de starter fra Microsoft 365 Administration, og gå til [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com)

![Link til kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-compliance-link.png)

Denne handling åbner **Office 365 Security and Compliance Center**, og de skal vælge linket til **Microsoft Purview-overholdelsesportalen**, der er angivet på banneret øverst på siden.

![Office 365 Security and Compliance Center.](../media/communication-compliance-case-scc.png)

Når du er på **Microsoft Purview-overholdelsesportalen**, vælger Contoso-it-administratorer **Vis alle** for at få vist den komplette liste over løsninger til overholdelse af angivne standarder.

![Menuen kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-show-all.png)

Når du har valgt **Vis alle**, kan Contoso-it-administratorer få adgang til løsningen til kommunikation med overholdelse af angivne standarder.

![Oversigt over kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Trin 3: Konfiguration af forudsætninger og oprettelse af en politik for kommunikation med overholdelse af angivne standarder

For at komme i gang med en politik for overholdelse af angivne standarder for kommunikation er der flere forudsætninger, som Contoso-it-administratorer skal konfigurere, før den nye politik konfigureres til at overvåge upassende tekst. Når disse forudsætninger er fuldført, kan Contoso-it-administratorer og overholdelsesspecialister konfigurere den nye politik, og overholdelsesspecialister kan begynde at undersøge og afhjælpe genererede beskeder.

### <a name="enabling-auditing-in-microsoft-365"></a>Aktivering af overvågning i Microsoft 365

Kommunikationsoverholdelse kræver overvågningslogge for at vise beskeder og spore afhjælpningshandlinger, der udføres af korrekturlæsere. Overvågningsloggene er en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når der er en ændring af en politik for kommunikation med overholdelse af angivne standarder.

Contoso-it-administratorer gennemser og [fuldfører den trinvise vejledning](turn-audit-log-search-on-or-off.md) for at aktivere overvågning. Når de har slået overvågning til, vises der en meddelelse om, at overvågningsloggen er ved at blive forberedt, og at de kan udføre en søgning om et par timer, efter at forberedelsen er fuldført. Contoso-it-administratorer behøver kun at udføre denne handling én gang.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Konfiguration af Yammer lejer til oprindelig tilstand

Overholdelse af angivne standarder for kommunikation kræver, at den Yammer lejer for en organisation er i oprindelig tilstand for at overvåge upassende tekst i private meddelelser og offentlige communitysamtaler.

Contoso-it-administratorer skal sørge for at gennemse oplysningerne i [artiklen Oversigt over Yammer oprindelig tilstand i Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) og følge trinnene til kørsel af overførselsværktøjet i artiklen [Konfigurer dit Yammer netværk til oprindelig tilstand for Microsoft 365](/yammer/configure-your-yammer-network/native-mode).

### <a name="setting-up-a-group-for-in-scope-users"></a>Konfiguration af en gruppe for brugere i området

Specialister i Contoso-overholdelse vil gerne føje alle brugere til kommunikationspolitikken, der overvåger upassende tekst. De kan beslutte at føje hver brugerkonto til politikken separat, men de har besluttet, at det er meget nemmere, og det sparer tid at bruge en distributionsgruppe af **typen Alle brugere** for brugerne til denne politik.

De skal oprette en ny gruppe for at inkludere alle Contoso-brugere, så de gør følgende:

1. Contoso-it-administratorer logger på Microsoft 365 Administration [(https://admin.microsoft.com)](https://admin.microsoft.com) og går til Microsoft 365 Administration > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**GroupsGroups**</a> > .
2. De vælger **Tilføj en gruppe** og fuldfører guiden for at oprette en ny *Microsoft 365 gruppe* eller *distributionsgruppe*.

    ![Grupper.](../media/communication-compliance-case-all-employees.png)

3. Når den nye gruppe er oprettet, skal de føje alle Contoso-brugere til den nye gruppe. De åbner **Exchange Administration** [(https://outlook.office365.com/ecp)](https://outlook.office365.com/ecp) og navigerer til **Exchange AdministrationrecipientsGroups** >  > .<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a> Contoso-it-administratorer vælger området Medlemskab og den nye gruppe *Alle medarbejdere* , de har oprettet, og vælger kontrolelementet **Rediger** for at føje alle Contoso-brugere til den nye gruppe i guiden.

    ![Exchange Administration.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-inappropriate-text"></a>Oprettelse af den politik, der skal overvåges for upassende tekst

Når alle forudsætninger er fuldført, er it-administratorer og overholdelsesspecialister for Contoso klar til at konfigurere politikken for kommunikation med overholdelse af angivne standarder for at overvåge upassende tekst. Det er nemt og hurtigt at konfigurere denne politik ved hjælp af den nye upassende skabelon til tekstpolitik.

1. Contoso-it-administratorer og overholdelsesspecialister logger på **Microsoft Purview-overholdelsesportalen** og vælger **Kommunikation med overholdelse** i venstre navigationsrude. Denne handling åbner dashboardet **Oversigt** , der indeholder hurtige links til skabeloner til politik for kommunikation med overholdelse af angivne standarder. De vælger skabelonen **Overvåg for upassende tekst** ved at vælge **Kom i gang** for skabelonen.

    ![Uegnet tekstskabelon til kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-template.png)

2. I guiden med politikskabeloner arbejder Contoso-it-administratorer og overholdelsesspecialister sammen om at fuldføre de tre påkrævede felter: **Politiknavn**, **brugere eller grupper, der skal overvåges**, og **Korrekturlæsere**.
3. Da guiden Politik allerede har foreslået et navn til politikken, beslutter it-administratorer og overholdelsesspecialister at beholde det foreslåede navn og fokusere på de resterende felter. De vælger gruppen *Alle brugere* for de **brugere eller grupper, der skal overvåge** feltet, og vælger de overholdelsesspecialister, der skal undersøge og afhjælpe politikbeskeder for feltet **Korrekturlæsere** . Det sidste trin til at konfigurere politikken og begynde at indsamle beskedoplysninger er at vælge **Opret politik**.

    ![Guiden Til kommunikation med overholdelse af angivne standarder er upassende.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Trin 4: Undersøg og afhjælp beskeder

Nu, hvor politikken for overholdelse af angivne standarder for kommunikation, der skal overvåges for upassende tekst, er det næste trin for Contoso-overholdelsesspecialisterne at undersøge og afhjælpe eventuelle beskeder, der genereres af politikken. Det tager op til 24 timer, før politikken fuldt ud behandler kommunikation i alle kommunikationskanalerne, og at beskeder vises på **dashboardet Besked**.

Når der er genereret beskeder, følger specialister i Overholdelse af Contoso [arbejdsprocesvejledningen](communication-compliance-investigate-remediate.md) for at undersøge og afhjælpe upassende tekstproblemer.
