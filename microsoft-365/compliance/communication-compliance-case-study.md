---
title: Casestudie – Contoso konfigurerer hurtigt en upassende tekstpolitik for Microsoft Teams, Exchange og Yammer meddelelser
description: Et casestudie af Contoso, og hvordan de hurtigt konfigurerer en politik for overholdelse af kommunikation for at overvåge upassende tekst i Microsoft Teams, Exchange Online og Yammer kommunikation.
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
ms.openlocfilehash: 7532051d649be4d0e9320a372c53686879c31972
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/13/2022
ms.locfileid: "63588193"
---
# <a name="case-study---contoso-quickly-configures-an-inappropriate-text-policy-for-microsoft-teams-exchange-and-yammer-communications"></a>Casestudie – Contoso konfigurerer hurtigt en upassende tekstpolitik for Microsoft Teams, Exchange og Yammer meddelelser

Overholdelse af regler og Microsoft 365 hjælper dig med at minimere kommunikationsrisici ved at hjælpe dig med at registrere, registrere og handle på meddelelser med upassende tekst i organisationen. Upassende tekst kan indeholde bandeord, trusler, chikane og upassende billeder. Foruddefinerede og brugerdefinerede politikker giver dig mulighed for at scanne intern og ekstern kommunikation for at finde politik match, så de kan blive gennemgået af bestemte korrekturlæsere. Korrekturlæsere kan undersøge scannede mails, Microsoft Teams, Yammer eller tredjepartskommunikation i din organisation og tage relevante afhjælpningshandlinger for at sikre, at de overholder din organisations meddelelsesstandarder.

Contoso Corporation er en fiktiv organisation, der hurtigt skal konfigurere en politik til at overvåge upassende tekst. De har primært brugt Microsoft 365 til mail, Microsoft Teams og Yammer-support til deres brugere, men har nye krav til at håndhæve virksomhedspolitik vedrørende chikane på arbejdspladsen. Contoso-it-administratorer og overholdelsesspecialister har en grundlæggende forståelse af det grundlæggende ved at arbejde med Microsoft 365 og leder efter en ende-til-ende-vejledning til, hvordan du hurtigt kommer i gang med kommunikationsoverholdelse.

Casestudiet dækker de grundlæggende funktioner til hurtigt at konfigurere en politik for overholdelse af kommunikation for at overvåge kommunikation for upassende tekst. Denne vejledning omfatter:

- Trin 1: Planlægning af overholdelse af kommunikationsreglerne
- Trin 2: Adgang til kommunikationsoverholdelse i Microsoft 365
- Trin 3– Konfiguration af forudsætninger og oprettelse af en politik for overholdelse af regler og standarder i kommunikation
- Trin 4 – Undersøgelse og afhjælpning af beskeder

## <a name="step-1-planning-for-communication-compliance"></a>Trin 1: Planlægning af overholdelse af regler og standarder i kommunikation

Contoso-it-administratorer og overholdelsesspecialister deltog i onlinewebinar om løsninger til overholdelse af regler og standarder i Microsoft 365 og har besluttet, at politikker for overholdelse af kommunikation kan hjælpe dem med at opfylde de opdaterede krav i virksomhedens politik for reduktion af chikane på arbejdspladsen. Når de arbejder sammen, har de udviklet en plan for at oprette og aktivere en politik for overholdelse af kommunikation, der overvåger upassende tekst for chats, der sendes i Microsoft Teams, private meddelelser og community-samtaler i Yammer og i mails, der sendes i Exchange Online. Deres plan omfatter at identificere:

- It-administratorer, der skal have adgang til funktioner til overholdelse af kommunikation.
- Specialister i overholdelse af regler og standarder, der skal oprette og administrere kommunikationspolitikker.
- Specialister i overholdelse af regler og standarder og andre kollegaer i andre afdelinger (Human Resources, Legal osv.), der har brug for at undersøge og afhjælpe beskeder om kommunikationsoverholdelse.
- De brugere, der er omfattet af politikken for upassende tekst i forbindelse med kommunikation.

### <a name="licensing"></a>Licensering

Det første trin er at bekræfte, at Contosos licens Microsoft 365 omfatter understøttelse af løsningen til overholdelse af kommunikation. For at få adgang til og bruge kommunikationsoverholdelse skal Contoso-it-administratorer kontrollere, at Contoso har et af følgende:

- Microsoft 365 E5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3-abonnement + Microsoft 365 E5 Overholdelse-tilføjelsesprogrammet
- Microsoft 365 E3 -abonnement + Microsoft 365 E5 Insider Risk Management-tilføjelsesprogrammet
- Microsoft 365 A5-abonnement (betalt version eller prøveversion)
- Microsoft 365 A3+tilføjelsesprogrammet Microsoft 365 A5 overholdelse af regler og standarder
- Microsoft 365 A3 +Microsoft 365 A5 Insider Risk Management-tilføjelsesprogrammet
- Microsoft 365 G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 G5-abonnement + Microsoft 365 tilføjelsesprogrammet G5 Compliance
- Microsoft 365 G5-abonnement + Microsoft 365 G5 Insider Risk Management-tilføjelsesprogrammet
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (der er ikke længere tilgængeligt for nye abonnementer, se bemærk)

De skal også bekræfte, at brugere, der er inkluderet i politikker for overholdelse af kommunikation, skal tildeles en af licenserne ovenfor.

> [!IMPORTANT]
> Avanceret overholdelse i Office 365 sælges ikke længere som enkeltstående abonnement. Når aktuelle abonnementer udløber, skal kunder overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af regler og standarder.

Contoso-it-administratorer gør følgende for at bekræfte licenseringssupport til Contoso:

1. It-administratorer logger på Microsoft 365 Administration <https://admin.microsoft.com> og går til Microsoft 365 Administration > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">**BillingLicenses**</a> > .

2. Her bekræfter de, at de har en af de licensmuligheder [, der](communication-compliance-configure.md#subscriptions-and-licensing) omfatter understøttelse af overholdelse af regler og standarder.

![Licenser til overholdelse af kommunikation.](../media/communication-compliance-case-licenses.png)

### <a name="permissions-for-communication-compliance"></a>Tilladelser til overholdelse af regler og standarder i kommunikation

Der bruges fem rollegrupper til at konfigurere tilladelser til at administrere funktioner til overholdelse af kommunikation. For at **gøre overholdelse** af kommunikation tilgængelig som en menuindstilling i Microsoft 365 Overholdelsescenter og fortsætte med disse konfigurationstrin, tildeles Contoso-administratorer rollen *Kommunikationsoverholdelsesadministrator*.

Contoso beslutter at bruge rollegruppen Kommunikationsoverholdelse til at tildele alle administratorer af kommunikationsoverholdelse, analytikere, analytikere og seere til gruppen. Det gør det nemmere for Contoso at komme hurtigt i gang og passer bedst til deres krav til overholdelsesstyring.

|**Rolle**|**Rolletilladelser**|
|:-----|:-----|
| **Kommunikationsoverholdelse** | Brug denne rollegruppe til at administrere overholdelse af kommunikationsreglerne for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udvalgte administratorer, analytikere, seere og seere kan du konfigurere tilladelser til overholdelse af kommunikation i en enkelt gruppe. Denne rollegruppe indeholder alle kommunikationsoverholdelsestilladelsesroller. Denne konfiguration er den nemmeste måde til hurtigt at komme i gang med overholdelse af regler og standarder i kommunikation, og den passer godt til organisationer, der ikke har brug for separate tilladelser defineret til separate grupper af brugere. |
| **Administrator for overholdelse af kommunikation** | Brug denne rollegruppe til i første omgang at konfigurere kommunikationsoverholdelse og senere for at adskille administratorer af kommunikationsoverholdelse i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for overholdelse af kommunikation, globale indstillinger og rollegruppetildelinger. Brugere, der er tildelt denne rollegruppe, kan ikke få vist beskeder om meddelelser. |
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere for kommunikationsoverholdelse. Brugere, der er tildelt denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist metadata for meddelelser (ikke meddelelsesindhold), eskalere til flere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse ventende beskeder. |
| **Communication Compliance Investigator** | Brug denne gruppe til at tildele tilladelser til brugere, der skal fungere som kompatibilitetsgrupper for kommunikation. Brugere, der er tildelt denne rollegruppe, kan få vist metadata og indhold for meddelelser, eskalere til flere korrekturlæsere, eskalere til Advanced eDiscovery-sag, sende meddelelser til brugere og løse beskeden. |
| **Fremviser til overholdelse af kommunikation** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden til overholdelse af kommunikation og kan få vist alle rapporter om overholdelse af kommunikation. |

1. Contoso-it-administratorer logger på [siden Microsoft 365 Overholdelsescenter-tilladelser](https://compliance.microsoft.com/permissions) ved hjælp af legitimationsoplysninger til en global administratorkonto og vælger linket for at få vist og administrere roller i Microsoft 365.
2. I Microsoft 365 Overholdelsescenter skal de gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser og**</a> vælge linket for at få vist og administrere roller i Office 365.
3. Administratorerne vælger *rollegruppen Kommunikationsoverholdelse* , og vælg derefter **Rediger rollegruppe**.
4. Administratorerne vælger **Vælg medlemmer i** venstre navigationsrude og vælger derefter **Rediger**.
5. De vælger **Tilføj og** markerer derefter afkrydsningsfeltet for alle Contoso-brugere, der skal administrere overholdelse af kommunikationsreglerne, undersøge og gennemse beskeder.
6. Administratorerne vælger **Tilføj** og derefter **Udført**.
7. De vælger **Gem for** at føje Contoso-brugere til rollegruppen. De vælger **Luk** for at fuldføre trinnene.

## <a name="step-2-accessing-communication-compliance-in-microsoft-365"></a>Trin 2: Adgang til kommunikationsoverholdelse Microsoft 365

Efter konfiguration af tilladelser til overholdelse af kommunikation kan Contoso-it-administratorer og overholdelsesspecialister, der er tildelt rollegruppen Kommunikationsoverholdelse, få adgang til løsningen til kommunikationsoverholdelse Microsoft 365. Contoso-it-administratorer og overholdelsesspecialister har flere måder at få adgang til overholdelse af kommunikation på og komme i gang med at oprette en ny politik:

- Start direkte fra kommunikationsoverholdelsesløsningen
- Startende fra Microsoft 365 Overholdelsescenter
- Startende fra Microsoft 365 fra løsningskataloget
- Fra og med Microsoft 365 Administration

### <a name="starting-directly-from-the-communication-compliance-solution"></a>Start direkte fra kommunikationsoverholdelsesløsningen

Den hurtigste måde at få adgang til løsningen på er at logge på direkte til løsningen **Kommunikationsoverholdelse** (<https://compliance.microsoft.com/supervisoryreview>). Med dette link dirigeres it-administratorer og overholdelsesspecialister fra Contoso til dashboardet Oversigt over overholdelse af kommunikation, hvor du hurtigt kan gennemgå status for vigtige beskeder og oprette nye politikker ud fra de foruddefinerede skabeloner.

![Oversigt over kommunikationsoverholdelse.](../media/communication-compliance-case-overview.png)

### <a name="starting-from-the-microsoft-365-compliance-center"></a>Startende fra Microsoft 365 Overholdelsescenter

En anden nem måde for contoso-it-administratorer og overholdelsesspecialister at få adgang til løsningen til overholdelse af kommunikation er at logge på [direkte Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com). Når brugerne har logget på, skal de blot  vælge kontrolelementet Vis alle for at få vist alle overholdelsesløsninger  og derefter vælge kommunikationsoverholdelsesløsningen for at komme i gang.

![Overholdelsescenter.](../media/communication-compliance-case-center.png)

### <a name="starting-from-the-microsoft-365-solution-catalog"></a>Startende fra Microsoft 365 fra løsningskataloget

Contoso-it-administratorer og overholdelsesspecialister kan også vælge at få adgang til løsningen til overholdelse af kommunikation ved at vælge Microsoft 365 løsningskatalog. Ved at vælge **sektionen Katalog** i løsninger i venstre navigationsrude, mens du er **i Microsoft 365 Overholdelsescenter**, kan de åbne løsningskataloget med en liste over Microsoft 365 løsninger til overholdelse af regler og standarder. Når du ruller ned til **sektionen Insider-risikostyring** kan Contoso-it-administratorer vælge Kommunikationsoverholdelse for at komme i gang. Contoso-it-administratorer beslutter også at bruge kontrolelementet Vis i navigation til at fastgøre løsningen til overholdelse af kommunikation til venstre navigationsrude for hurtigere adgang, når de logger på fremover.

![Løsningskatalog.](../media/communication-compliance-case-solution.png)

### <a name="starting-from-the-microsoft-365-admin-center"></a>Fra og med Microsoft 365 Administration

For at få adgang til overholdelse af kommunikationsreglerne, når du starter fra Microsoft 365 Administration, skal Contoso-it-administratorer og overholdelsesspecialister logge på Microsoft 365 Administration [(https://admin.microsoft.com)](https://admin.microsoft.com) og [gå til Microsoft 365 Overholdelsescenter ](https://compliance.microsoft.com)

![Link til overholdelse af kommunikation.](../media/communication-compliance-case-compliance-link.png)

Denne handling åbner **Office 365 Security and Compliance Center**, og de skal vælge linket til **Microsoft 365 Overholdelsescenter, der** findes i banneret øverst på siden.

![Office 365 security and compliance center.](../media/communication-compliance-case-scc.png)

Når du er i **Microsoft 365 Overholdelsescenter**, vælger Contoso-it-administratorer **Vis alle for** at få vist den komplette liste over løsninger til overholdelse af regler og standarder.

![Menu for overholdelse af kommunikation.](../media/communication-compliance-case-show-all.png)

Når du har **valgt Vis alle**, kan Contoso-it-administratorer få adgang til løsningen til overholdelse af kommunikation.

![Oversigt over kommunikationsoverholdelse.](../media/communication-compliance-case-overview.png)

## <a name="step-3-configuring-prerequisites-and-creating-a-communication-compliance-policy"></a>Trin 3: Konfiguration af forudsætninger og oprettelse af en politik for overholdelse af regler og standarder i kommunikation

For at komme i gang med en politik for overholdelse af kommunikation er der flere forudsætninger for, at Contoso-it-administratorer skal konfigurere, før de konfigurerer den nye politik til overvågning af upassende tekst. Når disse forudsætninger er afsluttet, kan Contoso-it-administratorer og overholdelsesspecialister konfigurere de nye specialister i politikker og overholdelse af regler og standarder, og de kan begynde at undersøge og afhjælpe eventuelle genererede beskeder.

### <a name="enabling-auditing-in-microsoft-365"></a>Aktivering af overvågning i Microsoft 365

Kommunikationsoverholdelse kræver overvågningslogs for at vise beskeder og registrere afhjælpningshandlinger, som er foretaget af korrekturlæsere. Overvågningsloggen er en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når der sker en ændring i en politik for overholdelse af kommunikation.

Contoso-it-administratorer gennemser [og gennemfører den trinvise vejledning](turn-audit-log-search-on-or-off.md) for at aktivere overvågning. Når overvågning er aktiveret, vises der en meddelelse om, at overvågningsloggen forberedes, og at de kan køre en søgning om et par timer, efter at klargøringen er fuldført. It-administratorer af Contoso skal kun udføre denne handling én gang.

### <a name="configuring-yammer-tenant-for-native-mode"></a>Konfiguration Yammer lejer for oprindelig tilstand

Kommunikationsoverholdelse kræver, at Yammer lejer for en organisation er i indbygget tilstand for at overvåge upassende tekst i private meddelelser og offentlige communitysamtaler.

Contoso-it-administratorer sørger for, at de gennemser oplysningerne i artiklen Oversigt [over Yammer Native Mode i Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode) og følger trinnene for at køre overflytningsværktøjet i artiklen Konfigurere dit [Yammer-netværk til oprindelig tilstand til Microsoft 365](/yammer/configure-your-yammer-network/native-mode).

### <a name="setting-up-a-group-for-in-scope-users"></a>Konfiguration af en gruppe for in-scope-brugere

Contoso-overholdelsesspecialister ønsker at føje alle brugere til kommunikationspolitikken, der overvåger upassende tekst. De kan beslutte at føje hver brugerkonto til politikken separat, men de har besluttet, at det er meget nemmere og sparer tid at bruge **en distributionsgruppe** for alle brugere for brugerne til denne politik.

De skal oprette en ny gruppe for at inkludere alle Contoso-brugere, så de gør følgende:

1. Contoso-it-administratorer It-administratorer logger på Microsoft 365 Administration [(https://admin.microsoft.com)](https://admin.microsoft.com) og går til Microsoft 365 Administration > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**GroupsGroups**</a> > .
2. De vælger **Tilføj en gruppe og** fuldfører guiden for at oprette Microsoft 365 *gruppe eller* *distributionsgruppe*.

    ![Grupper.](../media/communication-compliance-case-all-employees.png)

3. Når den nye gruppe er oprettet, skal de føje alle Contoso-brugere til den nye gruppe. De åbner **Exchange Administration** [(https://outlook.office365.com/ecp)](https://outlook.office365.com/ecp) og navigerer **Exchange** **AdministrationrecipientsGroups** >  > .<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a> Contoso-it-administratorer vælger området Medlemskab og den nye  gruppe Alle medarbejdere, de oprettede, og  vælger kontrolelementet Rediger for at føje alle Contoso-brugere til den nye gruppe i guiden.

    ![Exchange Administration.](../media/communication-compliance-case-eac.png)

### <a name="creating-the-policy-to-monitor-for-inappropriate-text"></a>Opret politikken til overvågning af upassende tekst

Når alle forudsætningerne er opfyldt, er it-administratorer og overholdelsesspecialister for Contoso klar til at konfigurere politikken til overholdelse af kommunikation for at overvåge upassende tekst. Det er nemt og hurtigt at konfigurere denne politik ved hjælp af den nye skabelon til upassende tekst.

1. Contoso-it-administratorer og overholdelsesspecialister logger **på Microsoft 365 Overholdelsescenter** og vælger **Kommunikationsoverholdelse** i venstre navigationsrude. Denne handling åbner **oversigtsdashboardet** med hurtige links til skabeloner til politikker for overholdelse af kommunikation. De vælger **skabelonen Skærm for upassende** tekst ved at **vælge Introduktion** til skabelonen.

    ![Skabelon til upassende tekst i kommunikationsoverholdelse.](../media/communication-compliance-case-template.png)

2. I guiden til politikskabeloner arbejder it-administratorer og overholdelsesspecialister fra Contoso sammen for at udfylde de tre påkrævede **felter: Navn** på politik **, Brugere** eller grupper, der skal overvåges, og korrekturlæsere.
3. Da guiden politik allerede har foreslået et navn til politikken, beslutter it-administratorer og overholdelsesspecialister sig at beholde det foreslåede navn og fokusere på de resterende felter. De vælger gruppen *Alle* brugere for feltet Brugere  eller grupper for at overvåge feltet og vælge de kompatibilitetsspecialister, der skal undersøge og afhjælpe politikadvarsler for **feltet Korrekturlæsere**. Det sidste trin til at konfigurere politikken og begynde at indsamle beskedoplysninger er at vælge **Opret politik**.

    ![Guiden til upassende tekst i kommunikationsoverholdelse.](../media/communication-compliance-case-wizard.png)

## <a name="step-4-investigate-and-remediate-alerts"></a>Trin 4: Undersøg og afhjulpet beskeder

Nu hvor politikken til overholdelse af regler og standarder for kommunikation til overvågning af upassende tekst er konfigureret, er det næste trin for Contoso-overholdelsesspecialister at undersøge og afhjælpe eventuelle beskeder, der genereres af politikken. Det tager op til 24 timer, før politikken behandler kommunikation fuldt ud i alle kommunikationskildekanaler, og før beskeder vises i **dashboardet Besked**.

Når der er oprettet beskeder, vil Contoso-overholdelsesspecialister følge arbejdsprocesinstruktionerne for at undersøge og afhjælpe upassende tekstproblemer.[](communication-compliance-investigate-remediate.md)