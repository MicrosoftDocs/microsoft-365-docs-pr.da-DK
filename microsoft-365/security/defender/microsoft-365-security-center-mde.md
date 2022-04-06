---
title: Microsoft Defender for Endpoint i Microsoft 365 Defender
description: Få mere at vide om ændringer fra Microsoft Defender Security Center til Microsoft 365 Defender
keywords: Introduktion til Microsoft 365 Defender, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, MDO, MDE, sikkerhedsportal, sikkerhedsportalen Defender
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
ms.openlocfilehash: bac70dd864e1ab72fae5fbefa2a8da12cce4f6e7
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667224"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft Defender for Endpoint i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Hurtig reference

Billedet og tabellen nedenfor viser ændringerne i navigationen mellem Microsoft Defender Security Center og Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="De nye placeringer på Microsoft 365 Defender-portalen" lightbox="../../media/mde-m3d-security-center.png":::

| Microsoft Defender Security Center | Microsoft 365 Defender |
|---------|---------|
| Dashboards <ul><li>Sikkerhedshandlinger</li><li>Threat Analytics</li></ul>  |Home <ul><li>Trusselsanalyse</li></ul>   |
| Hændelser | Hændelser & beskeder |
| Enhedslager | Enhedslager |
| Beskedkøer | Hændelser & beskeder |
| Automatiserede undersøgelser | Handlingscenter |
| Avanceret jagt | Jagt |
| Rapporter | Rapporter |
| Partnere & API'er | Partnere & API'er |
| Administration af sårbarheder i forbindelse med trussel & | Administration af sårbarheder |
| Evaluering og selvstudier | Evaluering & selvstudier |
| Konfigurationsstyring | Konfigurationsstyring |
| Indstillinger | Indstillinger | 

Den forbedrede [Microsoft 365 Defender](microsoft-365-defender.md#the-microsoft-365-defender-portal) at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> kombinerer sikkerhedsfunktioner, der beskytter, registrerer, undersøger og besvarer mail-, samarbejds-, identitets- og enhedstrusler. Dette samler funktioner fra eksisterende Microsoft-sikkerhedsportaler, herunder Microsoft Defender Security Center og Office 365 Security & Compliance Center.

Hvis du kender Microsoft Defender Security Center, kan du i denne artikel beskrive nogle af ændringerne og forbedringerne i Microsoft 365 Defender. Der er dog nogle nye og opdaterede elementer, du skal være opmærksom på.

Historisk set har [Microsoft Defender Security Center](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) været hjemsted for Microsoft Defender for Endpoint. Virksomhedssikkerhedsteams har brugt den til at overvåge og hjælpe med at besvare beskeder om potentiel vedvarende trusselsaktivitet eller databrud. For at hjælpe med at reducere antallet af portaler er Microsoft 365 Defender hjemsted for overvågning og administration af sikkerhed på tværs af dine Microsoft-identiteter, data, enheder, apps og infrastruktur.

Microsoft Defender for Endpoint i Microsoft 365 Defender understøtter [tildeling af adgang til udbydere af administrerede sikkerhedstjenester](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) på samme måde[, som der gives adgang i Microsoft Defender Security Center](mssp-access.md).

> [!IMPORTANT]
> Det, du ser i Microsoft 365 Defender, afhænger af dine aktuelle abonnementer. Hvis du f.eks. ikke har en licens til Microsoft Defender for Office 365, vises sektionen Mail & Samarbejde ikke.

> [!Note]
> Microsoft 365 Defender er ikke tilgængelig for:
>- Amerikanske Government Community Cloud (GCC)
>- Amerikansk Government Community Cloud høj (GCC høj)
>- Det amerikanske forsvarsministerium
>- Alle amerikanske offentlige institutioner med kommercielle licenser

Se nærmere på Microsoft 365 Defender på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

Få mere at vide om fordelene: [Oversigt over Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>Hvad er ændret

Denne tabel er en hurtig reference til ændringerne mellem Microsoft Defender Security Center og Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>Beskeder og handlinger

| Område | Beskrivelse af ændring |
|---------|---------|
| [Hændelser & beskeder](incidents-overview.md)  | I Microsoft 365 Defender kan du administrere hændelser og beskeder på tværs af alle dine slutpunkter, mail og identiteter. Vi har konvergeret oplevelsen, så du nemmere kan finde relaterede hændelser. Du kan få flere oplysninger under [Oversigt over hændelser](incidents-overview.md).   |
| [Jagt](advanced-hunting-overview.md)  |  Hvis du ændrer regler for brugerdefineret registrering, der er oprettet i Microsoft Defender for Endpoint, så de indeholder identitets- og mailtabeller, flyttes de automatisk til Microsoft 365 Defender. Deres tilsvarende beskeder vises også i Microsoft 365 Defender. Du kan finde flere oplysninger om disse ændringer under [Overfør regler for brugerdefineret registrering](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>Tabellen `DeviceAlertEvents` til avanceret jagt er ikke tilgængelig i Microsoft 365 Defender. Hvis du vil forespørge om enhedsspecifikke beskedoplysninger i Microsoft 365 Defender, kan du bruge tabellerne `AlertInfo` og `AlertEvidence` til at imødekomme endnu flere oplysninger fra en række forskellige kilder. Udarbejde din næste enhedsrelaterede forespørgsel ved at følge [Skriv forespørgsler uden DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[Handlingscenter](m365d-action-center.md)    | Viser ventende og fuldførte handlinger, der blev udført efter automatiserede undersøgelser og afhjælpningshandlinger. Tidligere viste Løsningscenter i Microsoft Defender Security Center ventende og fuldførte handlinger for afhjælpningshandlinger, der kun blev udført på enheder, mens automatiserede undersøgelser viste beskeder og status. I den forbedrede Microsoft 365 Defender samler Løsningscenter afhjælpningshandlinger og -undersøgelser på tværs af mail, enheder og brugere – alt sammen på ét sted.  |
| [Trusselsanalyse](threat-analytics.md) |  Flyttet til toppen af navigationslinjen for at gøre det nemmere at finde og bruge den. Indeholder nu trusselsoplysninger for både slutpunkter og mail og samarbejde.    |

### <a name="endpoints"></a>Slutpunkter

| Område | Beskrivelse af ændring |
|---------|---------|
|Søg   |  Søgelinjen er placeret øverst på siden. Der gives forslag, mens du skriver. Du kan søge på tværs af følgende enheder i Defender for Endpoint og Defender for Identity: <br><br> - **Enheder** – understøttes for både Defender for Endpoint og Defender for Identity. Du kan endda bruge søgeoperatorer, f.eks. kan du bruge "indeholder" til at søge efter en del af et værtsnavn. <br><br> - **Brugere** – understøttes for både Defender for Endpoint og Defender for Identity. <br><br> - **Filer, IP-adresser og URL-adresser** – samme funktionalitet som i Defender for Endpoint. <br> BEMÆRK! *SØGNINGER I IP- og URL-adresser stemmer nøjagtigt overens og vises ikke på siden med søgeresultater – de fører direkte til enhedssiden.  <br><br> - **TVM** – samme funktionalitet som i Defender for Endpoint (sikkerhedsrisici, software og anbefalinger). <br><br>  Siden med forbedrede søgeresultater centraliserer resultaterne fra alle enheder.  |
|[Dashboard](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  Dette er dit dashboard til sikkerhedshandlinger. Se en oversigt over, hvor mange aktive beskeder der blev udløst, hvilke enheder der er i fare, hvilke brugere der er i fare, og alvorsgradsniveau for beskeder, enheder og brugere. Du kan også se, om nogen enheder har sensorproblemer, din overordnede tjenestetilstand, og hvordan der blev registreret uløste beskeder. |
|Enhedslager | Ingen ændringer. |
|[Administration af sårbarheder](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Navnet blev forkortet, så det passer til navigationsruden. Det er det samme som sektionen Håndtering af trusler og sikkerhedsrisici med alle siderne nedenunder.     |
| Partnere og API'er | Ingen ændringer. |
| Evalueringer & selvstudier    |     Nye test- og læringsfunktioner.     |
| Konfigurationsstyring   |  Ingen ændringer.  |

> [!NOTE]
> **Automatisk undersøgelse og afhjælpning** er nu en del af hændelser. Du kan se Automatiserede undersøgelses- og afhjælpningshændelser under fanen **Hændelse > undersøgelse** .

> [!TIP]
> Enhedssøgning udføres fra Slutpunkter > Søgning.

### <a name="access-and-reporting"></a>Adgang og rapportering

| Område | Beskrivelse af ændring |
|---------|---------|
| Rapporter  | Se rapporter for slutpunkter og mail & samarbejde, herunder Trusselsbeskyttelse, Enhedstilstand og overholdelse af angivne standarder og sårbare enheder. |
| Sundhed  |  Linker i øjeblikket til siden "Tjenestetilstand" i [Microsoft 365 Administration](https://admin.microsoft.com/). |
| Indstillinger |  Administrer dine indstillinger for Microsoft 365 Defender, Slutpunkter, Mail & samarbejde, Identiteter og Enhedsregistrering.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Microsoft 365 sikkerhedsnavigation og -funktioner

Den venstre navigationslinje eller værktøjslinjen Hurtig start vil se bekendt ud. Der er dog nogle nye og opdaterede elementer på Microsoft 365 Defender portal. 

### <a name="incidents-and-alerts"></a>Hændelser og beskeder

Samler administration af hændelser og beskeder på tværs af dine mails, enheder og identiteter. Beskedsiden giver fuld kontekst til beskeden ved at kombinere angrebssignaler for at oprette en detaljeret historie. En ny samlet oplevelse samler nu en ensartet visning af beskeder på tværs af arbejdsbelastninger. Du kan hurtigt triage, undersøge og udføre effektive handlinger.

- [Få mere at vide om hændelser](incidents-overview.md)
- [Få mere at vide om administration af beskeder](investigate-alerts.md)

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Værktøjslinjen Hurtig start af beskeder og handlinger på portalen Microsoft 365 Defender" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Jagt

Søg proaktivt efter trusler, malware og skadelig aktivitet på tværs af dine slutpunkter, Office 365 postkasser og meget mere ved hjælp af [avancerede jagtforespørgsler](advanced-hunting-overview.md). Disse effektive forespørgsler kan bruges til at finde og gennemse trusselsindikatorer og enheder for både kendte og potentielle trusler.

[Brugerdefinerede registreringsregler](custom-detection-rules.md) kan bygges fra avancerede jagtforespørgsler for at hjælpe dig med proaktivt at holde øje med hændelser, der kan være tegn på brudaktivitet og forkert konfigurerede enheder.


### <a name="action-center"></a>Handlingscenter

I Løsningscenter kan du se de undersøgelser, der er oprettet af automatiserede undersøgelses- og svarfunktioner. Denne automatiserede selvhelbredende Microsoft 365 Defender kan hjælpe sikkerhedsteams ved automatisk at reagere på bestemte hændelser.

[Få mere at vide om Løsningscenter](m365d-action-center.md).

### <a name="threat-analytics"></a>Threat Analytics

Få trusselsintelligens fra ekspertforskere i Microsoft-sikkerhed. Threat Analytics hjælper sikkerhedsteams med at være mere effektive, når de står over for nye trusler. Threat Analytics indeholder:

- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365. Dette er ud over de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender for Endpoint.
- Visning af hændelser relateret til truslerne.
- Forbedret oplevelse til hurtigt at identificere og bruge handlingsvenlige oplysninger i rapporterne.

Du kan få adgang til trusselsanalyser enten fra navigationslinjen øverst til venstre i Microsoft 365 Defender eller fra et dedikeret dashboardkort, der viser de største trusler for din organisation.

Få mere at vide om, hvordan [du sporer og reagerer på nye trusler med trusselsanalyser](./threat-analytics.md).

### <a name="endpoints-section"></a>Afsnittet Slutpunkter

Få vist og administrer sikkerheden for slutpunkter i din organisation. Hvis du har brugt Microsoft Defender Security Center, vil det se bekendt ud.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="Værktøjslinjen Hurtig start for slutpunkter på portalen Microsoft 365 Defender" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>Adgang og rapporter

Få vist rapporter, rediger dine indstillinger, og rediger brugerroller.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Værktøjslinjen Hurtig start for adgang og rapportering på Microsoft 365 Defender-portalen" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>SIEM API-forbindelser

Hvis du bruger [Defender for Endpoint SIEM-API'en](../defender-endpoint/enable-siem-integration.md), kan du fortsætte med at gøre det. Vi har tilføjet nye links i API-nyttedataene, der peger på beskedsiden eller hændelsessiden på Microsoft 365 sikkerhedsportalen. Nye API-felter omfatter LinkToMTP og IncidentLinkToMTP. Du kan få flere oplysninger under [Omdirigering af konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>Mailbeskeder

Du kan fortsætte med at bruge mailbeskeder til Defender for Endpoint. Vi har tilføjet nye links i de mails, der peger på beskedsiden eller hændelsessiden i Microsoft 365 Defender. Du kan få flere oplysninger under [Omdirigering af konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Udbydere af administrerede sikkerhedstjenester (MSSP)

Log på flere lejere samtidig i den samme browsersession understøttes i øjeblikket ikke i den samlede portal. Du kan fravælge den automatiske omdirigering ved [at vende tilbage til den tidligere Microsoft Defender for Endpoint portal](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal) for at bevare denne funktionalitet, indtil problemet er løst.

## <a name="related-information"></a>Relaterede oplysninger

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender for Endpoint i Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Omdirigering af konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
