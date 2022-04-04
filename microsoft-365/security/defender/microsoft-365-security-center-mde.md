---
title: Microsoft Defender for Endpoint i Microsoft 365 Defender
description: Få mere at vide om ændringer Microsoft Defender Security Center til Microsoft 365 Defender
keywords: Introduktion til Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, MDO, MDE, sikkerhedsportal, sikkerhedsportal for defender
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: f50a6750c3f5cd39e68a39cf000ff60e4fec8ef2
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568688"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft Defender for Endpoint i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Oversigtsreference

Billedet og tabellen nedenfor viser ændringerne i navigationen mellem Microsoft Defender Security Center og Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="De nye placeringer i Microsoft 365 Defender portalen" lightbox="../../media/mde-m3d-security-center.png":::

| Microsoft Defender Security Center | Microsoft 365 Defender |
|---------|---------|
| Dashboards <ul><li>Sikkerhedshandlinger</li><li>Threat Analytics</li></ul>  |Home <ul><li>Trusselsanalyse</li></ul>   |
| Hændelser | Hændelser & beskeder |
| Lagerenhed | Lagerenhed |
| Kø til beskeder | Hændelser & beskeder |
| Automatiserede undersøgelser | Handlingscenter |
| Avanceret jagt | På jagt |
| Rapporter | Rapporter |
| Partner- & API'er | Partner- & API'er |
| Administration af & af sikkerhedssikkerhedsrisiko | Administration af sikkerhedsrisiko |
| Evaluering og selvstudier | Selvstudier & evaluering |
| Konfigurationsstyring | Konfigurationsstyring |
| Indstillinger | Indstillinger | 

Den forbedrede [Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> kombinerer sikkerhedsfunktioner, der beskytter, registrerer, undersøger og besvarer mails, samarbejde, identitet og enhedstrusler. Dette samler funktionalitet fra eksisterende Microsoft-sikkerhedsportaler, herunder Microsoft Defender Security Center og Office 365 Security & Compliance Center.

Hvis du kender til Microsoft Defender Security Center, kan denne artikel hjælpe med at beskrive nogle af de ændringer og forbedringer, der er Microsoft 365 Defender. Der er dog nogle nye og opdaterede elementer, du skal være opmærksom på.

Historisk har [Microsoft Defender Security Center](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) været hjemstedet for Microsoft Defender for Endpoint. Virksomhedssikkerhedsteams har brugt det til at overvåge og hjælpe med at svare på advarsler om potentielt avanceret vedvarende trusselsaktivitet eller databribris. For at reducere antallet af portaler vil Microsoft 365 Defender være hjemsted for overvågning og administration af sikkerhed på tværs af dine Microsoft-identiteter, data, enheder, apps og infrastruktur.

Microsoft Defender for Endpoint på Microsoft 365 Defender understøtter tildeling af adgang til administrerede sikkerhedstjenesteudbydere på samme måde som adgang i [Microsoft Defender Security Center](mssp-access.md).[](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access)

> [!IMPORTANT]
> Hvad du ser i Microsoft 365 Defender afhænger af dine aktuelle abonnementer. Hvis du f.eks. ikke har en licens til Microsoft Defender for Office 365, vises sektionen & Samarbejde med mail ikke.

> [!Note]
> Microsoft 365 Defender er ikke tilgængelig for:
>- Amerikansk Government Community Cloud (GCC)
>- Us Government Community Cloud High (GCC High)
>- Det amerikanske forsvarsministerium
>- Alle amerikanske myndigheder med kommercielle licenser

Se nærmere på Microsoft 365 Defender på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

Få mere at vide om fordelene: [Oversigt over Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>Hvad er der ændret

Denne tabel er en hurtig oversigt over ændringerne mellem Microsoft Defender Security Center og Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>Beskeder og handlinger

| Område | Beskrivelse af ændring |
|---------|---------|
| [Hændelser & beskeder](incidents-overview.md)  | I Microsoft 365 Defender kan du administrere hændelser og beskeder på tværs af alle dine slutpunkter, mails og identiteter. Vi har konvergeret i oplevelsen, så du nemmere kan finde relaterede begivenheder. Du kan få mere at vide [under Oversigt over hændelser](incidents-overview.md).   |
| [På jagt](advanced-hunting-overview.md)  |  Når du ændrer brugerdefinerede registreringsregler, der er oprettet Microsoft Defender for Endpoint til at medtage identitets- og mailtabeller, flyttes de automatisk Microsoft 365 Defender. Deres tilsvarende beskeder vises også i Microsoft 365 Defender. Du kan få mere at vide om disse ændringer ved at [læse Overfør brugerdefinerede registreringsregler](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>Tabellen `DeviceAlertEvents` til avanceret jagt er ikke tilgængelig i Microsoft 365 Defender. Hvis du vil forespørge efter enhedsspecifikke beskedoplysninger i Microsoft 365 Defender, `AlertInfo` `AlertEvidence` kan du bruge tabellerne og dem til at oprette endnu flere oplysninger fra forskellige kilder. Udret din næste enhedsrelaterede forespørgsel ved at [følge Skriveforespørgsler uden DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[Handlingscenter](m365d-action-center.md)    | Viser ventende og afsluttede handlinger, der er foretaget efter automatiserede undersøgelser og afhjælpningshandlinger. Tidligere blev handlingscenteret i Microsoft Defender Security Center angivet ventende og afsluttede handlinger til afhjælpning af handlinger, der kun blev udført på enheder, mens automatiserede undersøgelser viste vigtige beskeder og statusser. I det forbedrede Microsoft 365 Defender samler Handlingscenter afhjælpningshandlinger og undersøgelser på tværs af mail, enheder og brugere – alt sammen på ét sted.  |
| [Trusselsanalyse](threat-analytics.md) |  Flyttet til toppen af navigationslinjen, så den er nemmere at finde og bruge. Nu indeholder trusselsoplysninger til både slutpunkter og mail og samarbejde.    |

### <a name="endpoints"></a>Slutpunkter

| Område | Beskrivelse af ændring |
|---------|---------|
|Søg   |  Søgelinjen er placeret øverst på siden. Der gives forslag, mens du skriver. Du kan søge på tværs af følgende enheder i Defender for Endpoint og Defender for Identity: <br><br> - **Enheder** – understøttes både for Defender til slutpunkt og Defender til identitet. Du kan endda bruge søgeoperatorer, f.eks. kan du bruge "indeholder" til at søge efter en del af et værtsnavn. <br><br> - **Brugere** – understøttes både for Defender for Endpoint og Defender for Identity. <br><br> - **Filer, IP'er og URL-adresser** – samme funktioner som i Defender til slutpunkt. <br> BEMÆRK! *IP- og URL-søgninger svarer nøjagtigt til hinanden og vises ikke på siden med søgeresultater – de fører direkte til enhedssiden.  <br><br> - **TVM** – samme funktioner som i Defender til slutpunkt (sårbarheder, software og anbefalinger). <br><br>  Den forbedrede side med søgeresultater centraliserer resultaterne fra alle enheder.  |
|[Dashboard](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  Dette er dashboardet for sikkerhedshandlinger. Se en oversigt over, hvor mange aktive beskeder, der blev udløst, hvilke enheder der er i fare, hvilke brugere der er i fare, og alvorsniveau for beskeder, enheder og brugere. Du kan også se, om nogen enheder har sensorproblemer, din generelle tjenestestilstand, og hvordan eventuelle ikke-afklarede beskeder blev fundet. |
|Lagerenhed | Ingen ændringer. |
|[Administration af sikkerhedsrisiko](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Navnet blev forkortet til at passe ind i navigationsruden. Det er det samme som den Håndtering af trusler og sikkerhedsrisici sektion, hvor alle siderne nedenunder er.     |
| Partnere og API'er | Ingen ændringer. |
| Selvstudier til & evalueringer    |     Nye test- og læringsfunktioner.     |
| Konfigurationsstyring   |  Ingen ændringer.  |

> [!NOTE]
> **Automatisk undersøgelse og afhjælpning er** nu en del af hændelser. Du kan se Automatiseret undersøgelse og afhjælpning på fanen **> Undersøgelse** .

> [!TIP]
> Enhedssøgning udføres fra Slutpunkter > Søg.

### <a name="access-and-reporting"></a>Access og rapportering

| Område | Beskrivelse af ændring |
|---------|---------|
| Rapporter  | Se rapporter for slutpunkter og mailkonti &, herunder Trusselsbeskyttelse, Enhedstilstand og -overholdelse og Følsomme enheder. |
| Tilstand  |  Links i øjeblikket ud til siden "Tjenestetilstand" i [Microsoft 365 Administration](https://admin.microsoft.com/). |
| Indstillinger |  Administrer dine indstillinger for Microsoft 365 Defender, slutpunkter, & mailsamarbejde, identiteter og enhedsregistrering.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 og funktioner til sikkerhedsnavigation

Den venstre navigationslinje eller værktøjslinjen Hurtig start ser bekendt ud. Der er dog nogle nye og opdaterede elementer i Microsoft 365 Defender portal. 

### <a name="incidents-and-alerts"></a>Hændelser og beskeder

Samler hændelses- og beskedstyring på tværs af dine mails, enheder og identiteter. Beskedsiden giver fuld kontekst til beskeden ved at kombinere angrebslys for at opbygge en detaljeret historie. En ny, samlet oplevelse samler nu en ensartet visning af beskeder på tværs af arbejdsbelastninger. Du kan hurtigt undersøge, undersøge og reagere effektivt.

- [Få mere at vide om hændelser](incidents-overview.md)
- [Få mere at vide om administration af beskeder](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Værktøjslinjen Hurtig start for beskeder og handlinger i Microsoft 365 Defender portal" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>På jagt

Søg proaktivt efter trusler, malware og ondsindet aktivitet på tværs af dine slutpunkter, Office 365 postkasser og meget mere ved hjælp af avancerede [forespørgselsforespørgsler](advanced-hunting-overview.md). Disse effektive forespørgsler kan bruges til at finde og gennemse trusselsindikatorer og enheder for både kendte og potentielle trusler.

[Brugerdefinerede registreringsregler](custom-detection-rules.md) kan oprettes ud fra avancerede forespørgselsforespørgsler, der kan hjælpe dig med proaktivt at holde øje med begivenheder, der kan være til hjælp ved brudaktivitet og forkert konfigurerede enheder.


### <a name="action-center"></a>Handlingscenter

Handlingscenter viser dig de undersøgelser, der er oprettet af automatiseret undersøgelse og svarmuligheder. Denne automatiserede, selvkørende kalender Microsoft 365 Defender hjælpe sikkerhedsteams ved automatisk at svare på bestemte begivenheder.

[Få mere at vide om handlingscenter](m365d-action-center.md).

### <a name="threat-analytics"></a>Threat Analytics

Få trusselsintelligens fra ekspert Microsoft-sikkerhedseksperter. Threat Analytics hjælper sikkerhedsteams med at være mere effektive, når de oplever nye trusler. Threat Analytics omfatter:

- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365. Dette er i tillæg til de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender for Endpoint.
- Visning af hændelser relateret til truslerne.
- Forbedret oplevelse til hurtigt at identificere og bruge brugbare oplysninger i rapporterne.

Du kan få adgang til trusselsanalyse enten fra den øverste venstre navigationslinje i Microsoft 365 Defender eller fra et dedikeret dashboardkort, der viser de største trusler for organisationen.

Få mere at vide om, [hvordan du kan spore og reagere på nye trusler med trusselsanalyse](./threat-analytics.md).

### <a name="endpoints-section"></a>Sektionen Slutpunkter

Få vist og administrer sikkerheden for slutpunkter i organisationen. Hvis du har brugt Microsoft Defender Security Center, ser det bekendt ud.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="Værktøjslinjen Hurtig start for slutpunkter i Microsoft 365 Defender portal" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>Access og rapporter

Få vist rapporter, rediger dine indstillinger, og rediger brugerroller.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Hurtig startlinjen Access og Rapportering i Microsoft 365 Defender portal" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>SIEM API-forbindelser

Hvis du bruger [Defender for Endpoint SIEM API](../defender-endpoint/enable-siem-integration.md), kan du fortsætte med at gøre det. Vi har tilføjet nye links på API'ens nyttedata, der peger på påmindelsessiden eller hændelsessiden i Microsoft 365-sikkerhedsportalen. Nye API-felter omfatter LinkToMTP og IncidentLinkToMTP. Du kan finde flere oplysninger [i Omdirigere konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>Mailbeskeder

Du kan fortsætte med at bruge mailbeskeder for Defender til Slutpunkt. Vi har tilføjet nye links i de mails, der peger på påmindelsessiden eller hændelsessiden i Microsoft 365 Defender. Du kan finde flere oplysninger [i Omdirigere konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Administrerede sikkerhedstjenesteudbydere (MSSP)

At logge på flere lejere samtidigt i den samme browsersession understøttes i øjeblikket ikke i den samlede portal. Du kan fravælge den automatiske omdirigering ved at gå tilbage til den tidligere [Microsoft Defender for Endpoint-portal](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal) for at bevare denne funktionalitet, indtil problemet er løst.

## <a name="related-information"></a>Relaterede oplysninger

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint i Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Omdirigere konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
