---
title: Microsoft 365 Defender
description: Microsoft 365 Defender er en koordineret trusselsbeskyttelsesløsning, som er udviklet til at beskytte enheder, identitet, data og programmer
keywords: Introduktion til MMicrosoft 365 Defender, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatisk undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- m365solution-m365-defender
- m365solution-scenario
- m365solution-overview
ms.custom:
- admindeeplinkDEFENDER
- intro-overview
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 691db83111ba14e9fed7eed36a819479bda15ff5
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63591841"
---
# <a name="microsoft-365-defender"></a>Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

Microsoft 365 Defender er en samlet forsvarspakke før og efter brud på enterprise defense, som indbygget koordinerer registrering, forebyggelse, undersøgelse og svar på tværs af slutpunkter, identiteter, mail og programmer for at yde integreret beskyttelse mod avancerede angreb.

Med den integrerede Microsoft 365 Defender-løsning kan sikkerhedsmedarbejdere arbejde sammen om trusselssignalerne om, at hvert af disse produkter modtager og fastslår det fulde omfang og indvirkningen af truslen, hvordan den er kommet ind i miljøet, hvad det påvirkes af, og hvordan det i øjeblikket påvirker organisationen. Microsoft 365 Defender automatisk handling for at forhindre eller stoppe angreb og selvkørende postkasser, slutpunkter og brugeridentiteter.

<center><h2>Microsoft 365 Defender tjenester</center></h2>
<table><tr><td><center><b><a href="/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint"><b>Microsoft Defender til Slutpunkt</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/office-365-security/overview"><b>Microsoft Defender til Office 365</b></center></a></td>
<td><center><b><a href="/defender-for-identity/"><b>Microsoft Defender for Identity</b></a></center></td>
<td><center><b><a href="/cloud-app-security/"><b>Microsoft Defender til skyapps</b></a></center></td>
</tr>
</table>
<br>

## <a name="microsoft-365-defender-interactive-guide"></a>Microsoft 365 Defender interaktiv vejledning

I denne interaktive vejledning lærer du, hvordan du beskytter din organisation med Microsoft 365 Defender. Du kan se, hvordan Microsoft 365 Defender kan hjælpe dig med at registrere sikkerhedsrisici, undersøge angreb på din organisation og automatisk forhindre skadelige aktiviteter.

[Se den interaktive vejledning](https://aka.ms/M365Defender-InteractiveGuide)

## <a name="microsoft-365-defender-protection"></a>Microsoft 365 Defender beskyttelse

Microsoft 365 Defender-tjenester beskytte:

- **Slutpunkter med Defender til slutpunkt** – Defender til slutpunkt er en samlet slutpunktsplatform til forebyggelse af beskyttelse efter brud, automatisk undersøgelse og svar.
- **Mail og samarbejde med Defender for Office 365** – Defender til Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL'er) og samarbejdsværktøjer.
- Identiteter med **Defender for Identity og Azure Active Directory (Azure AD) Identity Protection** – Defender for Identity bruger din lokale Active Directory-domæneservices (AD DS) signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og ondsindede Insider-handlinger rettet mod din organisation. Azure AD Identity Protection automatiserer registrering og afhjælpning af identitetsbaserede risici i din skybaserede Azure AD.
- **Programmer med Microsoft Defender til skyapps** – Microsoft Defender til skyapps er en omfattende kryds SaaS-løsning, der giver stor synlighed, stærke datakontrolelementer og forbedret trusselsbeskyttelse til dine skyapps.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww]

Microsoft 365 Defender unikke laget på tværs af produkter udvide de enkelte tjenestekomponenter til:

- Beskyt dig mod angreb, og koordiner svar på tværs af tjenesterne via signaldeling og automatiserede handlinger.
- Narrate the full story of the attack across product alerts, behaviors, and context for security teams by joining data on alerts, suspicious events and impacted assets to 'incidents'.
- Automatiser svar på kompromis ved at udløse selvbetjening for på påvirkede aktiver gennem automatiseret afhjælpning.
- Giv sikkerhedsteams mulighed for at udføre en detaljeret og effektiv trusselssøgning på tværs af slutpunkter Office data.

Her er et eksempel på, hvordan Microsoft 365 Defender-portalen korrelerer alle relaterede beskeder på tværs af produkter til en enkelt hændelse.

:::image type="content" source="../../media/overview-incident.png" alt-text="Eksempel på en side med oversigt over hændelser" lightbox="../../media/overview-incident.png":::

Her er et eksempel på listen over relaterede beskeder om en hændelse.

:::image type="content" source="../../media/incident-list.png" alt-text="Eksempel på listen over beskeder om en hændelse" lightbox="../../media/incident-list.png":::

Her er et eksempel på forespørgselsbaseret jagt oven på rådata på mail og slutpunkt.

:::image type="content" source="../../media/advanced-hunting.png" alt-text="Eksempel på avanceret jagt og en forespørgsel" lightbox="../../media/advanced-hunting.png":::

Microsoft 365 Defender funktioner på tværs af produkter omfatter:

- **Enkelt rude af glas** på tværs af produkter i Microsoft 365 Defender-portalen – en central visning til alle oplysninger om registreringer, påknyttede aktiver, automatiserede handlinger, der er foretaget, og relaterede beviser i en enkelt kø og en enkelt <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">rude i Microsoft 365 Defender-portalen</a>. 
- Samlet kø af hændelser – For at hjælpe sikkerhedsmedarbejdere med at fokusere på det, der er vigtigt, kan du sikre, at det fulde angrebsomfang, de påsatte aktiver og automatiserede **afhjælpningshandlinger** grupperes sammen og vises i tide. 
- **Automatisk svar på trusler** – Oplysninger om kritiske trusler deles i realtid mellem Microsoft 365 Defender-produkter for at stoppe forløbet af et angreb. 

   Hvis der f.eks. registreres en skadelig fil på et slutpunkt, der er beskyttet af Defender til Slutpunkt, får det Defender til Office 365 at scanne og fjerne filen fra alle mails. Filen vil være blokeret ved syne af hele Microsoft 365 sikkerhedspakke.

- **Selvaktiveret for** kompromitterede enheder, brugeridentiteter og postkasser – Microsoft 365 Defender bruger automatiske AI-baserede handlinger og afspilningsbøger til at afhjælpe påvirkningsaktiver, så de igen får en sikker tilstand. Microsoft 365 Defender udnytter automatiske afhjælpningsfunktioner i pakkeprodukterne for at sikre, at alle påknyttede aktiver, der er relateret til en hændelse, automatisk afhjælpes, hvor det er muligt.
- **Trusselssøgning** på tværs af produkter – Sikkerhedsteams kan udnytte deres unikke organisatoriske viden til at lede efter tegn på kompromis ved at oprette deres egne brugerdefinerede forespørgsler over de rå data, der indsamles af de forskellige beskyttelsesprodukter. Microsoft 365 Defender giver forespørgselsbaseret adgang til 30 dages historiske rå signaler og besked om data på tværs af slutpunktet og Defender Office 365 data.

## <a name="get-started"></a>Kom i gang

Microsoft 365 Defender licenskrav skal være opfyldt, før du kan aktivere tjenesten i Microsoft 365 Defender-portalen på Få mere at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> vide under:

- [Licenskrav](prerequisites.md#licensing-requirements)
- [Slå Microsoft 365 Defender](m365d-enable.md)

## <a name="the-microsoft-365-defender-portal"></a>Den Microsoft 365 Defender portal

Portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender kombinerer</a> beskyttelse, registrering, undersøgelse og svar på *mails, samarbejde**, identitet**, enhed* og *apptrusler* på et centralt sted. 

Denne enkelt rude af glas samler funktionalitet fra eksisterende Microsoft-sikkerhedsportaler, f.eks. Microsoft 365 Defender-portalen og Office 365 Security & Compliance Center. Portalen Microsoft 365 Defender fremhæver hurtig adgang til oplysninger, enklere layout og samler relaterede oplysninger, så de er nemmere at bruge. Den indeholder:

- **[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender for Office 365 hjælper organisationer med at beskytte deres virksomhed med et sæt funktioner til forebyggelse, registrering, undersøgelse og jagt for at beskytte mail og Office 365 ressourcer.
- **[Microsoft Defender til Slutpunkt leverer](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** forebyggelsesbeskyttelse, registrering efter brud, automatisk undersøgelse og svar til enheder i organisationen.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** er en del af Microsofts XDR-løsning (*Extended Detection and Response*), der udnytter Microsoft 365-sikkerhedsporteføljen til automatisk at analysere trusselsdata på tværs af domæner og opbygge et billede af et angreb på et enkelt dashboard.
- **[Microsoft Defender til skyapps](/cloud-app-security/)** er en omfattende cross-SaaS- og PaaS-løsning, der giver stor synlighed, stærke datakontrolelementer og forbedret trusselsbeskyttelse til dine skyapps.

Hvis du har brug for oplysninger om, hvad der er ændret Office 365 Security & Compliance Center eller Microsoft 365 Defender-portalen, skal du se:

- [Defender til Office 365 i Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Defender til slutpunkt i Microsoft 365 Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Portalen Microsoft 365 Defender bruger og gennemtvinger eksisterende rollebaseret adgang og flytter hver enkelt sikkerhedsmodel til den samlede portal. Hver konvergeret arbejdsbyrde har sin egen rollebaserede adgang. De roller, der allerede er i produkterne, konvergeres automatisk i Microsoft 365 Defender portalen. Microsoft Defender til skyapps vil dog stadig håndtere sine egne roller og tilladelser.

### <a name="what-to-expect"></a>Hvad du kan forvente

Alt det sikkerhedsindhold, du bruger <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">i Office 365 Security & Compliance Center</a> og Microsoft 365 Security Center, kan nu findes på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

Portalen Microsoft 365 Defender hjælper sikkerhedsteams med at undersøge og reagere på angreb ved at samle signaler fra forskellige arbejdsbelastninger i et sæt samlede oplevelser til:

- Hændelser & beskeder
- På jagt
- Handlingscenter
- Trusselsanalyse

Microsoft 365 Defender fremhæver forening *, tydelighed* og fælles mål, når det fletter Microsoft Defender Office 365 og Microsoft Defender til slutpunkt. Fletningen er baseret på nedenstående prioriteter og er skabt uden at yde de egenskaber, som hver enkelt sikkerhedspakke har medført for kombinationen af:

- Almindelige dokumentkomponenter
- Almindelig terminologi
- Fælles enheder
- Paritet mellem funktioner og andre arbejdsbelastninger

> [!NOTE]
> Portalen Microsoft 365 Defender er tilgængelig uden behov for, at kunderne kan foretage overførselstrin eller købe en ny licens. Denne nye portal er f.eks. tilgængelig for administratorer med et E3-abonnement, ligesom den er for administratorer med Microsoft Defender til Office 365 Plan 1 og Plan 2, men Exchange Online Protection- eller Defender til Office 365 Plan 1-kunder kan kun se de sikkerhedsfunktioner, som deres abonnementslicens understøtter. Formålet med portalen er at centralisere sikkerhed.

### <a name="unified-investigations"></a>Samlede undersøgelser

Centralisering af sikkerhedsoplysninger udgør et samlet sted til undersøgelse af sikkerhedshændelser på tværs Microsoft 365. Et primært eksempel **er Hændelser** under **hændelser & beskeder** om hurtig start af Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Siden Hændelser i Microsoft 365 Defender" lightbox="../../media/converged-incidents-2.png.png":::

Når du vælger et hændelsesnavn, vises en side, der demonstrerer værdien af at centralisere sikkerhedsoplysninger.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Eksempel på oversigtssiden for en hændelse i Microsoft 365 Defender" lightbox="../../media/converged-incident-info-3.png":::

Langs toppen af en **hændelsesside** vises oversigten **,** **beskeder****, enheder****, brugere**, **postkasser**, **undersøgelser, beviser** og svar **og Graph** faner. Vælg disse faner for at få mere detaljerede oplysninger. Fanen Brugere viser f.eks. oplysninger for brugere fra konvergerede arbejdsbelastninger (Microsoft Defender til slutpunkt, Microsoft Defender for Identity og Microsoft Defender til skyapps) og en række kilder som f.eks. lokale Active Directory-domæneservices (AD DS), Azure AD og tredjepartsudbydere af identitet. Du kan få mere at vide under [Undersøg brugere](investigate-users.md).

Tag dig tid til at gennemgå hændelserne i dit miljø, dykke ned i disse faner og øve dig på at opbygge en forståelse af, hvordan du får adgang til oplysningerne om hændelser for forskellige slags trusler.

Få mere at vide [under Hændelser i Microsoft 365 Defender](incidents-overview.md).

### <a name="improved-processes"></a>Forbedrede processer

Almindelige kontrolelementer og indhold vises enten på samme sted, eller de er sammen komprimeret til ét feed med data, som gør det nemmere at finde. For eksempel samlede indstillinger.

#### <a name="unified-settings"></a>Samlede indstillinger

:::image type="content" source="../../media/converged-add-role-9.png" alt-text="Siden Indstilling for Microsoft 365 Defender portal" lightbox="../../media/converged-add-role-9.png":::

#### <a name="permissions--roles"></a>Tilladelser & roller

:::image type="content" source="../../media/converged-roles-5.png" alt-text="Siden & Roller, der viser slutpunktsroller & grupper, roller og enhedsgrupper" lightbox="../../media/converged-roles-5.png":::

Adgang til Microsoft 365 Defender der er konfigureret med globale Azure AD-roller eller ved hjælp af brugerdefinerede roller. For Defender til Slutpunkt skal du se [Tildel brugeradgang til Microsoft 365 Defender-portalen](/microsoft-365/security/defender-endpoint/assign-portal-access). Hvis du har brug for Defender Office 365, [skal du se Tilladelser i Microsoft 365 Overholdelsescenter og Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- Få mere at vide om[, hvordan du administrerer adgang til Microsoft 365 Defender](m365d-permissions.md)
- Få mere at vide om, [hvordan du opretter brugerdefinerede](custom-roles.md) roller i Microsoft 365 Defender

> [!NOTE]
> Microsoft Defender til slutpunkt i Microsoft 365 Defender understøtter tildeling af adgang [](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) til administrerede sikkerhedstjenesteudbydere på samme måde, som adgang gives [på Microsoft 365 Defender-portalen](./mssp-access.md).

#### <a name="integrated-reports"></a>Integrerede rapporter

Rapporter er også samlet i Microsoft 365 Defender. Administratorer kan starte med en generel sikkerhedsrapport og forgrene sig til bestemte rapporter om slutpunkter, & samarbejde. Linkene her genereres dynamisk baseret på arbejdsbelastningskonfiguration.

#### <a name="quickly-view-your-microsoft-365-environment"></a>Få hurtigt vist dit Microsoft 365 miljø

**Startsiden** viser mange af de fælles kort, sikkerhedsteams skal bruge. Kompositionen af kort og data afhænger af brugerrollen. Da Microsoft 365 Defender portal bruger rollebaseret adgangskontrol, får forskellige roller vist kort, der giver mere mening for deres daglige job.

Disse oversigtsoplysninger hjælper dig med at holde dig trit med de seneste aktiviteter i organisationen. Microsoft 365 Defender samler signaler fra forskellige kilder for at præsentere en fantastisk visning af dit Microsoft 365 miljø.

Kortene kan ind under disse kategorier:

- **Identities**- Monitor the identities in your organization and keep track of suspicious or risky behaviors. [Få mere at vide om identitetsbeskyttelse](/azure/active-directory/identity-protection/overview-identity-protection).
- **Data** – Hjælp med at spore brugeraktivitet, der kan føre til uautoriseret videregivelse af data.
- **Enheder** – Få opdaterede oplysninger om beskeder, brudaktivitet og andre trusler på dine enheder.
- **Apps** – Få indsigt i, hvordan skyapps bruges i din organisation. [Få mere at vide om opdagede apps i Defender til skyapps](/cloud-app-security/discovered-apps).


#### <a name="search-across-entities-preview"></a>Søg på tværs af enheder (eksempel)

>[!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.
Søgelinjen er placeret øverst på siden. Mens du skriver, får du forslag, så det er nemmere at finde enheder. Den forbedrede side med søgeresultater centraliserer resultaterne fra alle enheder.

Du kan søge på tværs af følgende enheder i Defender for Endpoint og Defender for Identity: 

- **Enheder** – understøttes både for Defender til slutpunkt og Defender til identitet. Understøtter brug af søgeoperatorer. 
- **Brugere** – understøttes til Defender for Endpoint, Defender for Identity og Defender til skyapps. 
- **Filer, IP'er og URL-adresser** – samme funktioner som i Defender til slutpunkt.

    >[!NOTE]
    >IP- og URL-søgninger svarer nøjagtigt til hinanden og vises ikke på siden med søgeresultater – de fører direkte til enhedssiden. 

- **TVM** – samme funktioner som i Defender til slutpunkt (sårbarheder, software og anbefalinger). 

 





### <a name="threat-analytics-with-better-data-coverage"></a>Trusselsanalyse med bedre datadækning

Spor og svar på nye trusler med følgende Microsoft 365 Defender integreret oplevelse af trusselsanalyse:

- Bedre datadækning mellem Microsoft Defender til Slutpunkt og Microsoft Defender til Office 365, hvilket gør kombineret hændelsesstyring, automatisk undersøgelse, afhjælpning og proaktiv eller reaktiv trusselssøgning på tværs af domæner mulig.
- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365 samt de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender til slutpunkt.
- En oversigt over trusselsrelaterede hændelser, som samler beskeder til ende-til-ende-angrebshistorier på tværs af Microsoft Defender for Endpoint og Microsoft Defender til Office 365 for at reducere arbejdskøen, samt forenkle og sætte fart på din undersøgelse.
- Angrebsforsøg registreret og blokeret af Microsoft 365 Defender løsninger. Der findes også data, som du kan bruge til at køre sikkerhedsforanstaltninger, der reducerer risikoen for yderligere eksponering og øger fleksibiliteten.
- Forbedret design, der placerer brugbare oplysninger i spotlyset for at hjælpe dig med hurtigt at identificere data, der haster med at fokusere på, undersøge og udnytte fra rapporterne.

### <a name="a-centralized-learning-hub"></a>En centraliseret Learning Hub

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender indeholder</a> en læringshub, der bobler op med officiel vejledning fra ressourcer som f.eks. Microsoft-sikkerhedsbloggen, Microsofts sikkerhedsfællesskab på YouTube og den officielle dokumentation på docs.microsoft.com.

I læringshubben er vejledningen Mail & Collaboration (Microsoft Defender for Office 365) side om side med Slutpunkt (Microsoft Defender til slutpunkt) og Microsoft 365 Defender læringsressourcer.

Læringshubben åbnes med Learning, der er organiseret omkring emner som f.eks. "Sådan undersøger du Microsoft 365 Defender?" og "Microsoft Defender for Office 365 bedste fremgangsmåder". Dette afsnit er aktuelt af sikkerhedsproduktgruppen i Microsoft. Hver Learning sti afspejler en projiceret tid, det tager at gennemgå koncepterne. Det kan f.eks. være "Trin, der skal tages, når en Microsoft Defender for Office 365-brugerkonto er kompromitteret" projiceret til at tage 8 minutter, og det er værdifuld læring på farten.

Når du har klikket igennem til indholdet, kan det være nyttigt at bogmærke dette websted og organisere bogmærker i en mappe med navnet "Sikkerhed" eller "Kritisk". Hvis du vil Learning alle stierne, skal du klikke på linket Vis alle i hovedpanelet.

> [!NOTE]
> Der er nyttige **filtre** langs toppen af Microsoft 365 Defender Learning Hub, hvor du kan vælge mellem produkter (aktuelt Microsoft 365 Defender, Microsoft Defender til slutpunkt og Microsoft Defender til Office 365). Bemærk, at antallet af undervisningsressourcer for hver sektion er angivet, hvilket kan hjælpe elever med at holde styr på, hvor mange ressourcer de har til uddannelse og læring.
>
> Sammen med Produktfilter, aktuelle emner, typer af ressourcer (fra videoer til webinarer), niveauer af kendskab til eller erfaring med sikkerhedsområder, sikkerhedsroller og produktfunktioner vises.

> [!TIP]
> Der er mange andre læringsmuligheder i [Microsoft Learn](/learn/). Du kan finde certificeringskurser som [MS-500T02-A, som f.eks. kursus MS-500T02-A: implementering Microsoft 365 Threat Protection](/learn/certifications/courses/ms-500t02).

### <a name="send-us-your-feedback"></a>Send os din feedback

Vi har brug for din feedback. Vi søger altid at forbedre os, så hvis der er noget, du kunne tænke dig, kan du se denne video for at finde ud af, hvordan du kan stole på, at vi kan [læse din feedback](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Du kan også give feedback fra denne artikel. I afsnittet "Feedback" til sidst under "Send og vis feedback til" er indstillingerne *Dette produkt* eller *Denne side*.

Brug knappen **Dette produkt** til feedback *om* produktet:

1. Vælg *Dette* produkt nederst i artiklen.
    1. Højreklik på knappen og "Åbn i en ny fane", hvis du vil fortsætte med at læse disse anvisninger.
2. Dette navigerer til **UserVoice-forummet**.
3. Du har to muligheder:
    1. Rul ned til tekstfeltet Hvordan kan vi forbedre overholdelse eller beskytte dine brugere bedre *i Office 365?* og indsætte *Microsoft 365 Defender*. Du kan søge i resultaterne efter en idé som din og stemme op på den, eller du kan bruge knappen til at **slå en ny idé op**.
    1. Hvis du mener, at dette problem allerede er rapporteret, og du vil hæve profilen med en stemme (eller stemmer), skal du bruge feltet *Giv feedback* i højre side af UserVoice. Søg efter *Microsoft 365 Defender*, **find problemet, og brug stemmeknappen til** at hæve status.

Brug *Denne side* til feedback på selve artiklen. Tak for din feedback. Din stemme hjælper os med at forbedre produkter.

### <a name="explore-what-the-microsoft-365-defender-portal-has-to-offer"></a>Udforsk, hvad Microsoft 365 Defender har at tilbyde

Fortsæt med at udforske funktionerne og egenskaberne i Microsoft 365 Defender:

- [Administrer hændelser og beskeder](manage-incidents.md)
- [Spore og reagere på nye trusler med trusselsanalyse](threat-analytics.md)
- [Handlingscenter](m365d-action-center.md)
- [Lede efter trusler på tværs af enheder, mails, apps og identiteter](./advanced-hunting-query-emails-devices.md)
- [Brugerdefinerede registreringsregler](./custom-detection-rules.md)
- [Beskeder & mailsamarbejde](../../compliance/alert-policies.md#default-alert-policies)
- [Opret en simulering af phishingangreb](../office-365-security/attack-simulation-training.md)[, og opret en nyttelast til oplæring af dine teams](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)

## <a name="training-for-security-analysts"></a>Kurser til sikkerhedsanalytikere

Med denne læringssti fra Microsoft Learn kan du forstå Microsoft 365 Defender og hvordan det kan hjælpe med at identificere, kontrollere og løse sikkerhedstrusler.

|Kursus:|Find og svar på cyberangreb med Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender kursusikon.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Microsoft 365 Defender samlede trusselssignaler på tværs af slutpunkter, identiteter, mail og programmer for at yde integreret beskyttelse mod avancerede cyberangreb. Microsoft 365 Defender er den centrale oplevelse til at undersøge og reagere på hændelser og proaktivt søge efter igangværende ondsindede cybersikkerhedsaktiviteter.<p> 1 time 38 min - Learning Sti - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/paths/defender-detect-respond/)


## <a name="see-also"></a>Se også

- [Nyheder i Microsoft 365 Defender](whats-new.md)
- [Microsoft Defender til Office 365 i Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Microsoft Defender til slutpunkt i Microsoft 365 Defender](microsoft-365-security-center-mde.md)
