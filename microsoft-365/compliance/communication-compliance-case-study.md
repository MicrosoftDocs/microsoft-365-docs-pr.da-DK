---
title: Casestudie – Contoso konfigurerer en upassende tekstpolitik
description: En casestudie for Contoso, og hvordan de hurtigt konfigurerer en politik for overholdelse af kommunikation for at registrere upassende tekst i Microsoft Teams, Exchange Online og Yammer-kommunikation.
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
ms.openlocfilehash: 17b80d00cfb8c5855dda7d21371097dd413fb707
ms.sourcegitcommit: 1734c95ce72d9c8af695cb4b49b1e40d921a1fee
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66685651"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-text-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Casestudie – Contoso konfigurerer hurtigt en upassende tekstpolitik for Microsoft Teams-, Exchange- og Yammer-kommunikation

[Microsoft Purview Kommunikationsoverholdelse](/microsoft-365/compliance/communication-compliance) hjælper med at minimere kommunikationsrisici ved at hjælpe dig med at registrere, registrere og reagere på meddelelser med upassende tekst i din organisation. upassende tekst kan omfatte bandeord, trusler, chikane og upassende billeder. Foruddefinerede og brugerdefinerede [politikker](/microsoft-365/compliance/communication-compliance-policies) giver dig mulighed for at scanne intern og ekstern kommunikation for politikkampe, så de kan undersøges af udpegede korrekturlæsere. Korrekturlæsere kan [undersøge beskeder](/microsoft-365/compliance/communication-compliance-investigate-remediate#investigate-alerts) for mail, Microsoft Teams, Yammer eller tredjepartskommunikation i din organisation og udføre de nødvendige [afhjælpningshandlinger](/microsoft-365/compliance/communication-compliance-investigate-remediate#remediate-alerts) for at sikre, at de overholder organisationens meddelelsesstandarder.

Contoso Corporation er en fiktiv organisation, der hurtigt skal konfigurere en politik for at registrere upassende tekst. De har primært brugt Microsoft 365 til mail, Microsoft Teams og Yammer-support til deres brugere, men har nye krav til at håndhæve virksomhedens politik vedrørende chikane på arbejdspladsen. Contoso-it-administratorer og overholdelsesspecialister har en grundlæggende forståelse af de grundlæggende funktioner i at arbejde med Microsoft 365 og er på udkig efter komplette vejledninger til, hvordan du hurtigt kommer i gang med overholdelse af angivne standarder for kommunikation.

I denne casestudie beskrives de grundlæggende funktioner til hurtigt at konfigurere en politik for overholdelse af angivne standarder for kommunikation for at registrere upassende tekst. Denne vejledning omfatter:

- [Trin 1: Planlægning af overholdelse af kommunikation](#step-1-planning-for-communication-compliance)
- [Trin 2: Adgang til overholdelse af kommunikation](#step-2-accessing-communication-compliance)
- [Trin 3: Konfiguration af forudsætninger og oprettelse af en politik for kommunikation med overholdelse af angivne standarder](#step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy)
- [Trin 4: Undersøg og afhjælp beskeder](#step-4-investigate-and-remediate-alerts)

## <a name="step-1-planning-for-communication-compliance"></a>Trin 1: Planlægning af overholdelse af kommunikation

Contoso-it-administratorer og overholdelsesspecialister deltog i onlinewebinarer om løsninger til overholdelse af angivne standarder i Microsoft 365 og besluttede, at politikker for kommunikation med overholdelse af angivne standarder vil hjælpe dem med at opfylde de opdaterede krav til virksomhedens politik for reduktion af chikane på arbejdspladsen. Når de arbejder sammen, har de udviklet en plan for at oprette og aktivere en politik for overholdelse af angivne standarder for kommunikation, der registrerer upassende meddelelser. Denne konfiguration omfatter registrering af tekst til chats, der sendes i Microsoft Teams, private meddelelser og communitysamtaler i Yammer og i mails, der sendes i Exchange Online. Deres plan omfatter identificering af:

- It-administratorer, der skal have adgang til funktioner til kommunikation med overholdelse af angivne standarder.
- De overholdelsesspecialister, der skal oprette og administrere kommunikationspolitikker.
- Overholdelsesspecialister og andre kollegaer i andre afdelinger (Hr, Juridisk osv.), der skal undersøge og afhjælpe beskeder om kommunikation med overholdelse af angivne standarder.
- De brugere, der vil være omfattet af politikken for kommunikation med overholdelse af angivne standarder.

### <a name="licensing"></a>Licensering

Det første trin er at bekræfte, at Contosos Microsoft 365-licenser omfatter understøttelse af løsningen til kommunikationsoverholdelse. For at få adgang til og bruge kommunikationsoverholdelse skal Contoso-it-administratorer bekræfte, at Contoso har en af følgende:

- Microsoft 365 E5/A5/F5/G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3/A3/F3/G5-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Compliance
- Microsoft 365 E3/A3/F3/G5-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 A5 abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (ikke længere tilgængeligt for nye abonnementer, se note)

Brugere, der er inkluderet i politikker for kommunikation med overholdelse af angivne standarder, skal tildeles en af licenserne ovenfor. Du kan finde flere oplysninger om abonnementer og licenser under [Vejledning til sikkerhed & overholdelse af angivne standarder i Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Avanceret overholdelse i Office 365 sælges ikke længere som et separat abonnement. Når de aktuelle abonnementer udløber, skal kunderne overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af angivne standarder.

Contoso-it-administratorer gør følgende for at bekræfte licensunderstøttelse for Contoso:

1. It-administratorer logger på [Microsoft 365 Administration](https://admin.microsoft.com) og går til Microsoft 365 Administration > **faktureringslicenser** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

2. Her bekræfter de, at de har en af de [licensmuligheder](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) , der omfatter understøttelse af kommunikation med overholdelse af angivne standarder.

![Licenser til kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Tilladelser til kommunikation med overholdelse af angivne standarder

Der er fem rollegrupper, der bruges til at konfigurere tilladelser til at administrere funktioner til kommunikation med overholdelse af angivne standarder. Contoso-administratorer tildeles rollen *Communication Compliance Administration* for at gøre **overholdelse af kommunikation** tilgængelig som en menuindstilling i Microsoft Purview-compliance-portal og fortsætte med disse konfigurationstrin.

Contoso beslutter at bruge rollegruppen *Kommunikationsoverholdelse* til at tildele alle administratorer, analytikere, efterforskere og seere til gruppen for kommunikationsoverholdelse. Denne rollegruppekonfiguration gør det nemmere for Contoso at komme hurtigt i gang og passer bedst til deres krav til administration af overholdelse.

|**Rolle**|**Rolletilladelser**|
|:-----|:-----|
| **Kommunikation med overholdelse af angivne standarder** | Brug denne rollegruppe til at administrere overholdelse af kommunikation for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere kan du konfigurere tilladelser til kommunikation med overholdelse af angivne standarder i en enkelt gruppe. Denne rollegruppe indeholder alle tilladelser til kommunikation med overholdelse af angivne standarder. Denne konfiguration af rollegrupper er den nemmeste måde hurtigt at komme i gang med overholdelse af kommunikation på, og den er velegnet til organisationer, der ikke har brug for separate tilladelser, der er defineret for separate grupper af brugere. |
| **Administration for overholdelse af angivne standarder for kommunikation** | Brug denne rollegruppe til først at konfigurere overholdelse af kommunikation og senere til at adskille administratorer af kommunikation med overholdelse af angivne standarder i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for kommunikation med overholdelse af angivne standarder, globale indstillinger og tildelinger af rollegrupper. Brugere, der er tildelt denne rollegruppe, kan ikke få vist meddelelsesbeskeder. |
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt til denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist meddelelsesmetadata (ikke meddelelsesindhold), eskalere til yderligere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse ventende beskeder. |
| **Efterforsker af kommunikation med overholdelse af angivne standarder** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som undersøgere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt denne rollegruppe, kan få vist meddelelsesmetadata og indhold, eskalere til yderligere korrekturlæsere, eskalere til en eDiscovery (Premium)-sag, sende meddelelser til brugere og løse beskeden. |
| **Meddelelsesoverholdelsesfremviser** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden for kommunikation med overholdelse af angivne standarder og kan få vist alle rapporter om kommunikation med overholdelse af angivne standarder. |

1. Contoso-it-administratorer logger på siden [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/permissions) tilladelser ved hjælp af legitimationsoplysninger for en global administratorkonto og vælger linket for at få vist og administrere roller i Microsoft 365.
2. I Microsoft Purview-compliance-portal går de til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a> og vælger linket for at få vist og administrere roller i Office 365.
3. Administratorerne vælger rollegruppen *Kommunikationsoverholdelse* og vælger derefter **Rediger rollegruppe**.
4. Administratorer vælger **Vælg medlemmer** i venstre navigationsrude og vælger derefter **Rediger**.
5. De vælger **Tilføj** og markerer derefter afkrydsningsfeltet for alle Contoso-brugere, der skal administrere kommunikation med overholdelse af angivne standarder, undersøge og gennemse beskeder.
6. Administratorer vælger **Tilføj** og vælger derefter **Udført**.
7. De vælger **Gem** for at føje Contoso-brugere til rollegruppen. De vælger **Luk** for at fuldføre trinnene.

## <a name="step-2-accessing-communication-compliance"></a>Trin 2: Adgang til overholdelse af kommunikation

Når du har konfigureret tilladelserne til overholdelse af kommunikationsoverholdelse, kan Contoso-it-administratorer og overholdelsesspecialister, der er tildelt rollegruppen Kommunikationsoverholdelse, få adgang til løsningen til kommunikationsoverholdelse i Microsoft Purview. Contoso-it-administratorer og overholdelsesspecialister har flere måder at få adgang til overholdelse af kommunikation på og komme i gang med at oprette en ny politik:

- Starter direkte fra løsningen til overholdelse af kommunikationsoverholdelse
- Fra og med Microsoft Purview-compliance-portal
- Starter fra Microsoft Purview-løsningskataloget
- Fra og med Microsoft 365 Administration

### <a name="starting-directly-from-the-communication-compliance-solution"></a>Starter direkte fra løsningen til overholdelse af kommunikationsoverholdelse

Den hurtigste måde at få adgang til løsningen på er ved at logge direkte på [løsningen til kommunikation med overholdelse af angivne standarder](https://compliance.microsoft.com/supervisoryreview). Ved hjælp af dette link bliver Contoso-it-administratorer og overholdelsesspecialister dirigeret til startsiden for kommunikation med overholdelse af angivne standarder, hvor du hurtigt kan gennemse status for beskeder og oprette nye politikker ud fra de foruddefinerede skabeloner.

![Startside for overholdelse af angivne standarder for kommunikation.](../media/communication-compliance-home.png)

### <a name="starting-from-the-microsoft-purview-compliance-portal"></a>Fra og med Microsoft Purview-compliance-portal

En anden nem måde for Contoso-it-administratorer og overholdelsesspecialister at få adgang til løsningen til kommunikation med overholdelse af angivne standarder på er ved at logge på [Microsoft Purview-compliance-portal](https://compliance.microsoft.com). Når brugerne er logget på, skal de blot vælge kontrolelementet **Vis alle** for at få vist alle løsninger til overholdelse af angivne standarder og derefter vælge løsningen **Kommunikation for** at komme i gang.

![Overholdelsescenter.](../media/communication-compliance-compliance-portal.png)

### <a name="starting-from-the-microsoft-purview-solution-catalog"></a>Starter fra Microsoft Purview-løsningskataloget

Contoso-it-administratorer og overholdelsesspecialister kan også vælge at få adgang til løsningen til kommunikationsoverholdelse ved at vælge kataloget til Microsoft Purview-løsning. Ved at vælge **Katalog** i afsnittet **Løsninger** i venstre navigationsrude, mens de **er i Microsoft Purview-compliance-portal**, kan de åbne løsningskataloget med en liste over alle Microsoft Purview-løsninger. Når du ruller ned til afsnittet **Styring af insiderrisiko** , kan Contoso-it-administratorer vælge Kommunikation med overholdelse af angivne standarder for at komme i gang. Contoso-it-administratorer beslutter også at bruge kontrolelementet Vis i navigation til at fastgøre løsningen til kommunikation med overholdelse af angivne standarder i venstre navigationsrude for at få hurtigere adgang, når de logger på fremover.

![Løsningskatalog.](../media/m365-solution-catalog-home.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>Fra og med Microsoft 365 Administration

Contoso-it-administratorer og overholdelsesspecialister logger på [Microsoft 365 Administration](https://admin.microsoft.com) for at få adgang til overholdelse af angivne standarder, når de starter fra Microsoft 365 Administration, og gå til [Microsoft Purview-compliance-portal ](https://compliance.microsoft.com)

![Link til kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-compliance-link.png)

Denne handling åbner **Office 365 Security and Compliance Center**, og de skal vælge linket til de **Microsoft Purview-compliance-portal**, der er angivet på banneret øverst på siden.

![Office 365 Security and Compliance Center.](../media/communication-compliance-case-scc.png)

Når contoso-it-administratorer er **i Microsoft Purview-compliance-portal**, vælger de **Vis alle** for at få vist den komplette liste over løsninger til overholdelse af angivne standarder.

![Menuen kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-show-all.png)

Når du har valgt **Vis alle**, kan Contoso-it-administratorer få adgang til løsningen til kommunikation med overholdelse af angivne standarder.

![Oversigt over kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Trin 3: Konfiguration af forudsætninger og oprettelse af en politik for kommunikation med overholdelse af angivne standarder

For at komme i gang med en politik for overholdelse af angivne standarder for kommunikation er der flere forudsætninger, som Contoso-it-administratorer skal konfigurere, før de konfigurerer den nye politik for at registrere upassende tekst. Når disse forudsætninger er fuldført, kan Contoso-it-administratorer og overholdelsesspecialister konfigurere den nye politik, og overholdelsesspecialister kan begynde at undersøge og afhjælpe genererede beskeder.

### <a name="enabling-auditing-in-microsoft-365"></a>Aktivering af overvågning i Microsoft 365

Kommunikationsoverholdelse kræver overvågningslogge for at vise beskeder og spore afhjælpningshandlinger, der udføres af korrekturlæsere. Overvågningsloggene er en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når der sker en ændring af en politik for kommunikation med overholdelse af angivne standarder.

Contoso-it-administratorer gennemser og [fuldfører den trinvise vejledning](/microsoft-365/compliance/turn-audit-log-search-on-or-off) for at aktivere overvågning. Når de har slået overvågning til, vises der en meddelelse om, at overvågningsloggen er ved at blive forberedt, og at de kan udføre en søgning om et par timer, efter at forberedelsen er fuldført. Contoso-it-administratorer behøver kun at udføre denne handling én gang.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Konfiguration af Yammer-lejer til oprindelig tilstand

Overholdelse af kommunikation kræver, at Yammer-lejeren for en organisation er i oprindelig tilstand for at registrere upassende tekst i private meddelelser og offentlige communitysamtaler.

Contoso-it-administratorer skal sørge for, at de gennemser oplysningerne i [artiklen Oversigt over Oprindelig tilstand i Yammer i Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) og følger trinnene til kørsel af overførselsværktøjet i artiklen [Konfigurer dit Yammer-netværk til oprindelig tilstand for Microsoft 365](/yammer/configure-your-yammer-network/native-mode) .

### <a name="setting-up-a-group-for-in-scope-users"></a>Konfiguration af en gruppe for brugere i området

Specialister i Contoso-overholdelse vil gerne føje alle brugere til kommunikationspolitikken, der registrerer upassende tekst. De kan beslutte at føje hver brugerkonto til politikken separat, men de har besluttet, at det er meget nemmere, og det sparer tid at bruge en distributionsgruppe af **typen Alle brugere** for brugerne til denne politik.

De skal oprette en ny gruppe for at inkludere alle Contoso-brugere, så de gør følgende:

1. Contoso It-administratorer logger på [Microsoft 365 Administration](https://admin.microsoft.com) og går til Microsoft 365 Administration > **grupper** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**.**</a>
2. De vælger **Tilføj en gruppe** og fuldfører guiden for at oprette en ny *Microsoft 365-gruppe* eller *distributionsgruppe*.

    ![Grupper.](../media/communication-compliance-case-all-employees.png)

3. Når den nye gruppe er oprettet, skal de føje alle Contoso-brugere til den nye gruppe. De åbner [Exchange Administration](https://outlook.office365.com/ecp) og navigerer til **Exchange Administration-modtagere** >  > <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">**Grupper**</a>. Contoso-it-administratorer vælger området Medlemskab og den nye gruppe *Alle medarbejdere* , de har oprettet, og vælger kontrolelementet **Rediger** for at føje alle Contoso-brugere til den nye gruppe i guiden.

    ![Exchange Administration.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-detect-inappropriate-text"></a>Oprettelse af politikken til registrering af upassende tekst

Når alle forudsætninger er fuldført, er it-administratorer og overholdelsesspecialister for Contoso klar til at konfigurere politikken for kommunikation med overholdelse af angivne standarder for at registrere upassende tekst. Det er nemt og hurtigt at konfigurere denne politik ved hjælp af den nye upassende skabelon til tekstpolitik.

1. Contoso-it-administratorer og overholdelsesspecialister logger på **Microsoft Purview-compliance-portal** og vælger **Kommunikation med overholdelse** i navigationsruden til venstre. Denne handling åbner dashboardet **Oversigt** , der indeholder hurtige links til skabeloner til politik for kommunikation med overholdelse af angivne standarder. De vælger skabelonen **Overvåg for upassende tekst** ved at vælge **Kom i gang** for skabelonen.

    ![Uegnet tekstskabelon til kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-case-template.png)

2. I guiden med politikskabeloner arbejder Contoso-it-administratorer og overholdelsesspecialister sammen om at fuldføre de tre påkrævede felter: **Politiknavn**, **brugere eller grupper, der skal overvåges**, og **Korrekturlæsere**.
3. Da guiden Politik allerede har foreslået et navn til politikken, beslutter it-administratorer og overholdelsesspecialister at beholde det foreslåede navn og fokusere på de resterende felter. De vælger gruppen *Alle brugere* for de **brugere eller grupper, der skal overvåge** feltet, og vælger de overholdelsesspecialister, der skal undersøge og afhjælpe politikbeskeder for feltet **Korrekturlæsere** . Det sidste trin til at konfigurere politikken og begynde at indsamle beskedoplysninger er at vælge **Opret politik**.

    ![Guiden Til kommunikation med overholdelse af angivne standarder er upassende.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Trin 4: Undersøg og afhjælp beskeder

Nu, hvor politikken for overholdelse af angivne standarder for kommunikation til registrering af upassende tekst er konfigureret, vil det næste trin for Contosos overholdelsesspecialister være at undersøge og afhjælpe eventuelle beskeder, der genereres af politikken. Det tager op til en time, før politikken fuldt ud behandler kommunikation i alle kommunikationskanalerne, og at beskeder vises på **dashboardet Besked**.

Når der er genereret beskeder, følger specialister i Overholdelse af Contoso [arbejdsprocesvejledningen](/microsoft-365/compliance/communication-compliance-investigate-remediate) for at undersøge og afhjælpe upassende tekstproblemer.
