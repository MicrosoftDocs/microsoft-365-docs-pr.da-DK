---
title: Microsoft 365 Defender
description: Microsoft 365 Defender er en koordineret trusselsbeskyttelsesløsning, der er udviklet til at beskytte enheder, identitet, data og programmer
keywords: introduktion til MMicrosoft 365 Defender, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
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
ms.custom:
- admindeeplinkDEFENDER
- intro-overview
ms.topic: conceptual
ms.technology: m365d
adobe-target: true
ms.openlocfilehash: e52153542445e12ff983cc018a8186e62e6af2b0
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493503"
---
# <a name="microsoft-365-defender"></a>Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

Microsoft 365 Defender er en samlet virksomhedsforsvarspakke før og efter sikkerhedsbrud, der oprindeligt koordinerer registrering, forebyggelse, undersøgelse og svar på tværs af slutpunkter, identiteter, mail og programmer for at yde integreret beskyttelse mod avancerede angreb.

Med den integrerede Microsoft 365 Defender løsning kan sikkerhedseksperter samle de trusselssignaler, som hvert af disse produkter modtager, og bestemme det fulde omfang og den fulde indvirkning af truslen, hvordan den gik ind i miljøet, hvad det påvirkes, og hvordan det i øjeblikket påvirker organisationen. Microsoft 365 Defender udfører automatisk handlinger for at forhindre eller stoppe angreb og selvreparerende berørte postkasser, slutpunkter og brugeridentiteter.

<center><h2>Microsoft 365 Defender-tjenester</center></h2>
<table><tr><td><center><b><a href="/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint"><b>Microsoft Defender for Endpoint</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/defender-vulnerability-management/defender-vulnerability-management"><b>Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender</b></center></a></td>
<td><center><b><a href="/microsoft-365/security/office-365-security/overview"><b>Microsoft Defender for Office 365</b></center></a></td>
<td><center><b><a href="/defender-for-identity/"><b>Microsoft Defender for Identity</b></a></center></td>
<td><center><b><a href="/cloud-app-security/"><b>Microsoft Defender for Cloud Apps</b></a></center></td>
</tr>
</table>
<br>

## <a name="microsoft-365-defender-interactive-guide"></a>Microsoft 365 Defender interaktiv vejledning

I denne interaktive vejledning lærer du, hvordan du beskytter din organisation med Microsoft 365 Defender. Du kan se, hvordan Microsoft 365 Defender kan hjælpe dig med at registrere sikkerhedsrisici, undersøge angreb på din organisation og forhindre skadelige aktiviteter automatisk.

[Se den interaktive vejledning](https://aka.ms/M365Defender-InteractiveGuide)

## <a name="microsoft-365-defender-protection"></a>Microsoft 365 Defender beskyttelse

Microsoft 365 Defender tjenester beskytter:

- **Slutpunkter med Defender for Endpoint** – Defender for Endpoint er en samlet slutpunktsplatform til forebyggende beskyttelse, registrering efter brud, automatiseret undersøgelse og svar.
- **Assets with Defender Vulnerability Management** – Admininstration af håndtering af sikkerhedsrisici til Microsoft Defender leverer løbende synlighed af aktiver, intelligente risikobaserede vurderinger og indbyggede afhjælpningsværktøjer, der kan hjælpe dine sikkerheds- og it-teams med at prioritere og håndtere kritiske sikkerhedsrisici og fejlkonfigurationer på tværs af din Organisation.
- **Mail og samarbejde med Defender for Office 365** – Defender for Office 365 beskytter din organisation mod skadelige trusler fra mailmeddelelser, links (URL-adresser) og samarbejdsværktøjer.
- **Identiteter med Defender for Identity og Azure Active Directory (Azure AD) Identity Protection** – Defender for Identity bruger dine AD DS-signaler (Active Directory i det lokale miljø Domain Services) til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation. Azure AD Identity Protection automatiserer registrering og afhjælpning af identitetsbaserede risici i dine cloudbaserede Azure AD.
- **Programmer med Microsoft Defender for Cloud Apps** – Microsoft Defender for Cloud Apps er en omfattende saaS-løsning, der giver dig dyb synlighed, stærke datakontroller og forbedret trusselsbeskyttelse af dine cloudapps.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww]

Microsoft 365 Defender unikke lag på tværs af produkter øger de enkelte tjenestekomponenter til:

- Hjælp med at beskytte mod angreb og koordinere defensive svar på tværs af tjenesterne via signaldeling og automatiserede handlinger.
- Indtal hele historien om angrebet på tværs af produktbeskeder, funktionsmåder og kontekst for sikkerhedsteams ved at sammenføje data i beskeder, mistænkelige hændelser og påvirkede aktiver til 'hændelser'.
- Automatiser reaktion på kompromis ved at udløse selvreparation for påvirkede aktiver gennem automatiseret afhjælpning.
- Gør det muligt for sikkerhedsteams at udføre detaljeret og effektiv trusselsjagt på tværs af slutpunkts- og Office-data.

Her er et eksempel på, hvordan Microsoft 365 Defender-portalen korrelerer alle relaterede beskeder på tværs af produkter til en enkelt hændelse.

:::image type="content" source="../../media/overview-incident.png" alt-text="Siden oversigt over hændelser" lightbox="../../media/overview-incident.png":::

Her er et eksempel på listen over relaterede beskeder for en hændelse.

:::image type="content" source="../../media/incident-list.png" alt-text="Listen over beskeder om en hændelse" lightbox="../../media/incident-list.png":::

Her er et eksempel på forespørgselsbaseret jagt oven på rådata om mail og slutpunkter.

:::image type="content" source="../../media/advanced-hunting.png" alt-text=" Siden Avanceret jagt med forespørgselsoplysninger" lightbox="../../media/advanced-hunting.png":::

Microsoft 365 Defender funktioner på tværs af produkter omfatter:

- **Enkelt glasrude på tværs af produkter på Microsoft 365 Defender-portalen** – en central visning af alle oplysninger om registreringer, påvirkede aktiver, automatiserede handlinger og relaterede beviser i en enkelt kø og en enkelt rude i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal.</a> 
- **Kombineret hændelseskø** – For at hjælpe sikkerhedseksperter med at fokusere på det, der er vigtigt, ved at sikre, at det fulde angrebsomfang, påvirkede aktiver og automatiserede afhjælpningshandlinger grupperes og vises rettidigt. 
- **Automatisk reaktion på trusler** – Vigtige trusselsoplysninger deles i realtid mellem de Microsoft 365 Defender produkter for at hjælpe med at stoppe et angrebs forløb. 

   Hvis der f.eks. registreres en skadelig fil på et slutpunkt, der er beskyttet af Defender for Endpoint, instrueres Defender for Office 365 i at scanne og fjerne filen fra alle mails. Filen blokeres, når hele Microsoft 365-sikkerhedspakken vises.

- **Selvreparerende for kompromitterede enheder, brugeridentiteter og postkasser** – Microsoft 365 Defender bruger AI-drevne automatiske handlinger og playbooks til at afhjælpe påvirkede aktiver tilbage til en sikker tilstand. Microsoft 365 Defender udnytter automatisk afhjælpningsmuligheder for pakkeprodukterne for at sikre, at alle påvirkede aktiver, der er relateret til en hændelse, afhjælpes automatisk, hvor det er muligt.
- **Jagt på tværs af produkter** – Sikkerhedsteams kan udnytte deres unikke organisationsviden til at jage efter tegn på kompromis ved at oprette deres egne brugerdefinerede forespørgsler om de rå data, der indsamles af de forskellige beskyttelsesprodukter. Microsoft 365 Defender giver forespørgselsbaseret adgang til 30 dages historiske rådata og beskeddata på tværs af slutpunkts- og Defender for Office 365 data.

## <a name="get-started"></a>Kom i gang

Microsoft 365 Defender licenskrav skal være opfyldt, før du kan aktivere tjenesten på Microsoft 365 Defender-portalen på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a> Du kan få flere oplysninger under:

- [Licenskrav](prerequisites.md#licensing-requirements)
- [Slå Microsoft 365 Defender til](m365d-enable.md)

## <a name="the-microsoft-365-defender-portal"></a>Portalen Microsoft 365 Defender

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portalen Microsoft 365 Defender</a> kombinerer beskyttelse, registrering, undersøgelse og svar på *mail*, *samarbejde*, *identitet*, *enhed* og *apptrusler* på et centralt sted.

Denne enkelt glasrude samler funktioner fra eksisterende Microsoft-sikkerhedsportaler, f.eks. Microsoft 365 Defender-portalen og Office 365 Security & Compliance Center. I Microsoft 365 Defender-portalen lægges der vægt på hurtig adgang til oplysninger, enklere layout og samle relaterede oplysninger, så de bliver nemmere at bruge. Den indeholder:

- **[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender for Office 365 hjælper organisationer med at beskytte deres virksomhed med et sæt funktioner til forebyggelse, registrering, undersøgelse og jagt for at beskytte mail og Office 365 ressourcer.
- **[Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** leverer forebyggende beskyttelse, registrering efter sikkerhedsbrud, automatisk undersøgelse og svar til enheder i din organisation.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** er en del af Microsofts XDR-løsning (*Extended Detection and Response*), der udnytter Microsoft 365-sikkerhedsporteføljen til automatisk at analysere trusselsdata på tværs af domæner og oprette et billede af et angreb på et enkelt dashboard.
- **[Microsoft Defender for Cloud Apps](/cloud-app-security/)** er en omfattende saaS- og PaaS-løsning, der giver dig dyb synlighed, stærke datakontroller og forbedret trusselsbeskyttelse af dine cloudapps.

Hvis du har brug for oplysninger om, hvad der er ændret fra Office 365 Security & Compliance Center eller Microsoft 365 Defender-portalen, skal du se:

- [Defender for Office 365 i Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Defender for Endpoint i Microsoft 365 Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Den Microsoft 365 Defender portal bruger og gennemtvinger eksisterende rollebaseret adgang og flytter hver enkelt sikkerhedsmodel til den samlede portal. Hver konvergerede arbejdsbelastning har sin egen rollebaserede adgang. De roller, der allerede findes i produkterne, konvergeres automatisk til Microsoft 365 Defender-portalen. Microsoft Defender for Cloud Apps håndterer dog stadig sine egne roller og tilladelser.

Se denne korte video for at få mere at vide om den nye samlede portal i Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

### <a name="what-to-expect"></a>Hvad kan du forvente?

Alt det sikkerhedsindhold, du bruger i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a> og Microsoft 365 Sikkerhedscenter, kan nu findes på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>.

Portalen Microsoft 365 Defender hjælper sikkerhedsteams med at undersøge og reagere på angreb ved at hente signaler fra forskellige arbejdsbelastninger ind i en række samlede oplevelser for:

- Hændelser & beskeder
- Jagt
- Handlingscenter
- Trusselsanalyse

Microsoft 365 Defender lægger vægt på *enhed, klarhed og fælles mål,* når det fletter Microsoft Defender for Office 365 og Microsoft Defender for Endpoint. Fletningen var baseret på de prioriteter, der er angivet nedenfor, og blev foretaget uden at gå på kompromis med de funktioner, som hver sikkerhedspakke bragte til kombinationen af:

- Almindelige byggesten
- Almindelig terminologi
- Fælles enheder
- Funktionsparitet med andre arbejdsbelastninger

> [!NOTE]
> Microsoft 365 Defender-portalen er tilgængelig, uden at kunderne behøver at udføre migreringstrin eller købe en ny licens. Denne nye portal er f.eks. tilgængelig for administratorer med et E3-abonnement, ligesom den er tilgængelig for dem med Microsoft Defender for Office 365 Plan 1 og Plan 2, men Exchange Online Protection eller Defender for Office 365  Plan 1-kunder kan kun se de sikkerhedsfunktioner, deres abonnementslicens understøtter. Målet med portalen er at centralisere sikkerheden.

### <a name="unified-investigations"></a>Samlede undersøgelser

Centralisering af sikkerhedsoplysninger opretter et enkelt sted til undersøgelse af sikkerhedshændelser på tværs af Microsoft 365. Et primært eksempel er **Hændelser** under **Hændelser & beskeder** om hurtig start af Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Siden Hændelser på Microsoft 365 Defender-portalen" lightbox="../../media/converged-incidents-2.png.png":::

Når du vælger et hændelsesnavn, vises en side, der viser værdien af centralisering af sikkerhedsoplysninger.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Oversigtssiden for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/converged-incident-info-3.png":::

Øverst på en hændelsesside kan du se fanerne **Oversigt**, **Beskeder**, **Enheder**, **Brugere**, **Postkasser**, **Undersøgelser**, **Beviser og svar** og **Graf**  . Vælg disse faner for at få mere detaljerede oplysninger. Fanen **Brugere** viser f.eks. oplysninger om brugere fra konvergerede arbejdsbelastninger (Microsoft Defender for Endpoint, Microsoft Defender for Identity og Microsoft Defender for Cloud Apps) og en række kilder, f.eks. Active Directory i det lokale miljø domænetjenester (AD DS), Azure AD og tredjeparts-identitetsudbydere. Du kan få flere oplysninger under [Undersøg brugere](investigate-users.md).

Tag dig tid til at gennemse hændelserne i dit miljø, foretage detailudledning i disse faner og øve dig i at opbygge en forståelse af, hvordan du får adgang til de oplysninger, der er angivet for hændelser for forskellige typer trusler.

Du kan få flere oplysninger [under hændelser i Microsoft 365 Defender](incidents-overview.md).

### <a name="improved-processes"></a>Forbedrede processer

Almindelige kontrolelementer og indhold vises enten på samme sted eller komprimeres til ét datafeed, hvilket gør det nemmere at finde det. Det kan f.eks. være samlede indstillinger.

#### <a name="unified-settings"></a>Samlede indstillinger

:::image type="content" source="../../media/converged-add-role-9.png" alt-text="Siden Indstillinger på Microsoft 365 Defender-portalen" lightbox="../../media/converged-add-role-9.png":::

#### <a name="permissions--roles"></a>Tilladelser & roller

:::image type="content" source="../../media/converged-roles-5.png" alt-text="Slutpunktsrollerne & grupper, der vises på siden Tilladelser & roller" lightbox="../../media/converged-roles-5.png":::

Adgang til Microsoft 365 Defender er konfigureret med Azure AD globale roller eller ved hjælp af brugerdefinerede roller. Hvis du vil have mere at vide om Defender for Endpoint, skal du se [Tildel brugeradgang til portalen Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/assign-portal-access). Du kan få Defender for Office 365 [under Tilladelser i Microsoft Purview-compliance-portal og Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- Få mere at vide om, hvordan [du administrerer adgang til Microsoft 365 Defender](m365d-permissions.md)
- Få mere at vide om, hvordan [du opretter brugerdefinerede roller](custom-roles.md) i Microsoft 365 Defender

> [!NOTE]
> Microsoft Defender for Endpoint i Microsoft 365 Defender understøtter [tildeling af adgang til udbydere af administrerede sikkerhedstjenester](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) på samme måde, som der [gives adgang på Microsoft 365 Defender portalen](./mssp-access.md).

#### <a name="integrated-reports"></a>Integrerede rapporter

Rapporter er også samlet i Microsoft 365 Defender. Administratorer kan starte med en generel sikkerhedsrapport og forgrene sig til specifikke rapporter om slutpunkter, mail & samarbejde. Linkene her genereres dynamisk baseret på konfigurationen af arbejdsbelastningen.

#### <a name="quickly-view-your-microsoft-365-environment"></a>Få hurtigt vist dit Microsoft 365-miljø

**På** startsiden kan du se mange af de almindelige kort, som sikkerhedsteams har brug for. Sammensætningen af kort og data afhænger af brugerrollen. Da Microsoft 365 Defender portal bruger rollebaseret adgangskontrol, kan forskellige roller se kort, der giver mere mening for deres daglige job.

Disse hurtigt overbliksoplysninger hjælper dig med at holde dig opdateret om de nyeste aktiviteter i din organisation. Microsoft 365 Defender samler signaler fra forskellige kilder for at præsentere en holistisk visning af dit Microsoft 365-miljø.

Kortene falder i disse kategorier:

- **Identiteter** – Overvåg identiteterne i din organisation, og hold styr på mistænkelig eller risikabel adfærd. [Få mere at vide om identitetsbeskyttelse](/azure/active-directory/identity-protection/overview-identity-protection).
- **Data** – Hjælper med at spore brugeraktivitet, der kan føre til uautoriseret offentliggørelse af data.
- **Enheder** – Få opdaterede oplysninger om beskeder, sikkerhedsbrud og andre trusler på dine enheder.
- **Apps** – få indsigt i, hvordan cloudapps bruges i din organisation. [Få mere at vide om fundne apps i Defender for Cloud Apps](/cloud-app-security/discovered-apps).


#### <a name="search-across-entities-preview"></a>Søg på tværs af enheder (prøveversion)

>[!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.
Søgelinjen er placeret øverst på siden. Når du skriver, gives der forslag, så det er nemmere at finde objekter. Siden med forbedrede søgeresultater centraliserer resultaterne fra alle enheder.

Du kan søge på tværs af følgende enheder i Defender for Endpoint og Defender for Identity: 

- **Enheder** – understøttes for både Defender for Endpoint og Defender for Identity. Understøtter brug af søgeoperatorer. 
- **Brugere** – understøttes for Defender for Endpoint, Defender for Identity og Defender for Cloud Apps. 
- **Filer, IP-adresser og URL-adresser** – samme funktionalitet som i Defender for Endpoint.

    >[!NOTE]
    >IP- og URL-søgninger stemmer nøjagtigt overens og vises ikke på siden med søgeresultater – de fører direkte til enhedssiden. 

- **TVM** – samme funktionalitet som i Defender for Endpoint (sikkerhedsrisici, software og anbefalinger). 

 





### <a name="threat-analytics-with-better-data-coverage"></a>Trusselsanalyse med bedre datadækning

Spor og reager på nye trusler med følgende integrerede Microsoft 365 Defender trusselsanalyse:

- Bedre datadækning mellem Microsoft Defender for Endpoint og Microsoft Defender for Office 365, hvilket gør det muligt at foretage kombineret hændelsesstyring, automatisk undersøgelse, afhjælpning og proaktiv eller reaktiv trusselsjagt på tværs af domæner.
- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365 ud over de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender for Endpoint.
- En visning af trusselsrelaterede hændelser, der samler beskeder i end-to-end-angrebshistorier på tværs af Microsoft Defender for Endpoint og Microsoft Defender for Office 365 for at reducere arbejdskøen samt forenkle og fremskynde din undersøgelse.
- Angrebsforsøg, der er registreret og blokeret af Microsoft 365 Defender løsninger. Der er også data, som du kan bruge til at skabe forebyggende handlinger, der afhjælper risikoen for yderligere eksponering og øger robusthed.
- Forbedret design, der sætter handlingsvenlige oplysninger i søgelyset, så du hurtigt kan identificere data, så du hurtigt kan fokusere på, undersøge og udnytte fra rapporterne.

### <a name="a-centralized-learning-hub"></a>Et centraliseret Læringshub

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> indeholder en læringshub, der giver en bobler op officielle vejledning fra ressourcer som Microsofts sikkerhedsblog, Microsofts sikkerheds community på YouTube og den officielle dokumentation på docs.microsoft.com.

I læringshubben er vejledning til mail & samarbejde (Microsoft Defender for Office 365) side om side med Slutpunkt (Microsoft Defender for Endpoint) og Microsoft 365 Defender læringsressourcer.

Læringshubben åbnes med læringsforløb, der er organiseret omkring emner som f.eks. "Sådan undersøges brug af Microsoft 365 Defender?" og "Microsoft Defender for Office 365 bedste praksis". Dette afsnit er i øjeblikket kurateret af sikkerhedsproduktgruppen i Microsoft. Hvert læringsforløb afspejler en forventet tid, det tager at gennemgå koncepterne. 'Trin, der skal udføres, når en Microsoft Defender for Office 365 brugerkonto kompromitteres' forventes at tage 8 minutter, og det er værdifuld læring på farten.

Når du har klikket videre til indholdet, kan det være nyttigt at bogmærke dette websted og organisere bogmærker i en 'Sikkerhed' eller 'Kritisk' mappe. Hvis du vil se alle læringsforløb, skal du klikke på linket Vis alle i hovedpanelet.

> [!NOTE]
> Der er nyttige **filtre** langs toppen af Microsoft 365 Defender læringshub, der giver dig mulighed for at vælge mellem produkter (i øjeblikket Microsoft 365 Defender, Microsoft Defender for Endpoint og Microsoft Defender for Office 365). Bemærk, at antallet af læringsressourcer for hvert afsnit er angivet, hvilket kan hjælpe eleverne med at holde styr på, hvor mange ressourcer de har til rådighed til uddannelse og læring.
>
> Sammen med produktfilteret vises aktuelle emner, typer af ressourcer (fra videoer til webinarer), kendskab til eller erfaring med sikkerhedsområder, sikkerhedsroller og produktfunktioner.

> [!TIP]
> Der er mange andre læringsmuligheder i [Microsoft Learn](/learn/). Du finder certificeringskurser som f.eks [. kursus MS-500T02-A: Implementering af Microsoft 365 Threat Protection](/learn/certifications/courses/ms-500t02).

### <a name="send-us-your-feedback"></a>Send os din feedback

Vi har brug for din feedback. Vi vil altid forbedre os, så hvis der er noget, du gerne vil se, kan du [se denne video for at finde ud af, hvordan du kan stole på, at vi læser din feedback](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Du kan også give feedback fra denne artikel. I afsnittet "Feedback" i slutningen under "Send og få vist feedback til" er indstillingerne *Dette produkt* eller *Denne side*.

Brug knappen **Dette produkt** til *produktfeedback* :

1. Vælg *Dette produkt* nederst i artiklen.
    1. Højreklik på knappen og "Åbn i en ny fane", hvis du vil fortsætte med at læse disse retninger.
2. Dette navigerer til **UserVoice-forummet**.
3. Du har to muligheder:
    1. Rul ned til tekstfeltet *Hvordan kan vi forbedre overholdelse af angivne standarder eller beskytte dine brugere bedre i Office 365?* og indsætte *Microsoft 365 Defender*. Du kan søge i resultaterne efter en ide som din og stemme op, eller du kan bruge knappen til **at sende en ny ide**.
    1. Hvis du føler dig sikker på, at dette problem allerede er rapporteret, og du vil hæve profilen med en afstemning (eller stemmer), skal du bruge feltet *Giv feedback* i højre side af UserVoice. Søg efter *Microsoft 365 Defender*, **find problemet, og brug afstemningsknappen** til at hæve dens status.

Brug *denne side* til feedback om selve artiklen. Tak for din feedback. Din stemme hjælper os med at forbedre produkter.

### <a name="explore-what-the-microsoft-365-defender-portal-has-to-offer"></a>Udforsk, hvad Microsoft 365 Defender-portalen tilbyder

Fortsæt med at udforske funktionerne og egenskaberne i Microsoft 365 Defender:

- [Administrer hændelser og underretninger](manage-incidents.md)
- [Spor og reager på nye trusler med trusselsanalyse](threat-analytics.md)
- [Løsningscenter](m365d-action-center.md)
- [Jagt efter trusler på tværs af enheder, mails, apps og identiteter](./advanced-hunting-query-emails-devices.md)
- [Regler for brugerdefineret registrering](./custom-detection-rules.md)
- [Mailbeskeder & samarbejde](../../compliance/alert-policies.md#default-alert-policies)
- [Opret en simulering af phishingangreb](../office-365-security/attack-simulation-training.md) , og [opret en nyttedata til oplæring af dine teams](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)

## <a name="training-for-security-analysts"></a>Oplæring af sikkerhedsanalytikere

Med dette læringsforløb fra Microsoft Learn kan du forstå Microsoft 365 Defender, og hvordan det kan hjælpe med at identificere, styre og afhjælpe sikkerhedstrusler.

|Uddannelse:|Registrer og reager på cyberangreb med Microsoft 365 Defender|
|---|---|
|![Microsoft 365 Defender træningsikon.](../../media/microsoft-365-defender/m365-defender-secure-organization.svg)|Microsoft 365 Defender samler trusselssignaler på tværs af slutpunkter, identiteter, mail og programmer for at sikre integreret beskyttelse mod avancerede cyberangreb. Microsoft 365 Defender er den centrale oplevelse til at undersøge og reagere på hændelser og proaktivt søge efter igangværende ondsindede cybersikkerhedsaktiviteter.<p> 1 t. 38 min. - læringsforløb - 5 moduler|

> [!div class="nextstepaction"]
> [Start >](/learn/paths/defender-detect-respond/)


## <a name="see-also"></a>Se også

- [Nyheder i Microsoft 365 Defender](whats-new.md)
- [Microsoft Defender for Office 365 i Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Microsoft Defender for Endpoint i Microsoft 365 Defender](microsoft-365-security-center-mde.md)
