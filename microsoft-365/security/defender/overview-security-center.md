---
title: Microsoft 365 Defender oversigt, der kombinerer MDO, MDE, MDI og MCAS
description: Fordelene ved Microsoft 365 Defender ved at kombinere Microsoft Defender for Office 365 (MDO) og Microsoft Defender for Endpoint (MDE) med Microsoft Defender for Identity (MDI) og Microsoft Cloud App Security (MCAS). I denne artikel beskrives Microsoft 365 Defender fremskridt for administratorer.
keywords: sikkerhed, malware, Microsoft 365, M365, sikkerhedscenter, overvåge, rapportere, identiteter, data, enheder, apps
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.date: 04/21/2021
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: a0dce3a61847924043a10df4c13c963f279ea011
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/03/2021
ms.locfileid: "63591885"
---
# <a name="microsoft-365-defender-overview"></a>Microsoft 365 Defender oversigt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender til Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).

**Microsoft 365 Defender** ([https://security.microsoft.com](https://security.microsoft.com)) kombinerer beskyttelse, registrering, undersøgelse og besvarelse af *mails**, samarbejde**, identitet* og enhedstrusler på  en central portal.

Microsoft 365 Defender samler funktionalitet fra eksisterende Microsoft-sikkerhedsportaler, f.eks. Microsoft Defender Security Center og Office 365 Security & Compliance Center. Sikkerhedscenteret fremhæver hurtig adgang til oplysninger, enklere layout og samler relaterede oplysninger, så de er nemmere at bruge. Dette center omfatter:

- **[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender for Office 365 hjælper organisationer med at beskytte deres virksomhed med et sæt funktioner til forebyggelse, registrering, undersøgelse og jagt for at beskytte mail og Office 365 ressourcer.
- **[Microsoft Defender til Slutpunkt leverer](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** forebyggelsesbeskyttelse, registrering efter brud, automatisk undersøgelse og svar til enheder i organisationen.
- **[Microsoft 365 Defender](microsoft-365-defender.md)** er en del af Microsofts XDR-løsning (*Extended Detection and Response*), der udnytter Microsoft 365-sikkerhedsporteføljen til automatisk at analysere trusselsdata på tværs af domæner og opbygge et billede af et angreb på et enkelt dashboard.

Hvis du har brug for oplysninger om, hvad der er ændret Office 365 Security & Compliance Center eller Microsoft Defender Security Center, skal du se:

- [Defender til Office 365 i Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Defender til slutpunkt i Microsoft 365 Defender](microsoft-365-security-center-mde.md)

> [!NOTE]
> Sikkerhedsportalen Microsoft 365 eksisterende rollebaseret adgang og flytter hver enkelt sikkerhedsmodel til den samlede portal. Hver konvergeret arbejdsbyrde har sin egen rollebaserede adgang. De roller, der allerede er i produkterne, konvergeres automatisk Microsoft 365 sikkerhedsportalen. Roller og tilladelser for MCAS håndteres dog stadig i MCAS.

## <a name="what-to-expect"></a>Hvad du kan forvente

Alt det sikkerhedsindhold, du bruger i Office 365 Security and Compliance Center (protection.office.com) og Microsoft Defender Security Center (securitycenter.microsoft.com), kan nu findes i *Microsoft 365 Defender*.

Microsoft 365 Defender hjælper sikkerhedsteams med at undersøge og reagere på angreb ved at samle signaler fra forskellige arbejdsbelastninger i et sæt samlede oplevelser til:

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
> Microsoft 365 Defender være tilgængeligt uden behov for, at kunderne kan foretage overførselstrin eller købe en ny licens. Denne nye portal vil f.eks. være tilgængelig for administratorer med et E3-abonnement, ligesom den er for administratorer med Microsoft Defender til Office 365 Plan 1 og Plan 2, men Exchange Online Protection- eller Defender til Office 365 Plan 1-kunder kan kun se de sikkerhedsfunktioner, som deres abonnementslicens understøtter. Formålet med det nye center er at centralisere sikkerheden.

## <a name="unified-investigations"></a>Samlede undersøgelser

Konvergerende sikkerhedscentre opretter et enkelt sted til undersøgelse af sikkerhedshændelser på tværs Microsoft 365. Et primært eksempel **er Hændelser** under **hændelser & beskeder** om hurtig start af Microsoft 365 Defender.

:::image type="content" source="../../media/converged-incidents-2.png.png" alt-text="Siden Hændelser i Microsoft 365 Defender.":::

Når du vælger et hændelsesnavn, vises en side, der viser værdien af konvergerende sikkerhedscentre.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Eksempel på oversigtssiden for en hændelse i Microsoft 365 Defender":::

<!--
![Example of the Summary page for an incident in Microsoft 365 Defender.](../../media/converged-incident-info-3.png)
--> 

Langs toppen af en **hændelsesside** får du vist fanerne **Oversigt,** **Beskeder****, Enheder**, **Brugere**, **Postkasser**, Undersøgelser og **Beviser**. Vælg disse faner for at få mere detaljerede oplysninger. Fanen Brugere viser f.eks. oplysninger for brugere fra konvergerede arbejdsbelastninger (Microsoft Defender til slutpunkt, Microsoft Defender til identitet og Microsoft Cloud App Security) og en række kilder som f.eks. lokale Active Directory-domæneservices (AD DS), Azure Active Directory (Azure AD) og tredjeparts-identitetsudbydere. Du kan få mere at vide under [Undersøg brugere](investigate-users.md).

Tag dig tid til at gennemgå hændelserne i dit miljø, dykke ned i disse faner og øve dig på at opbygge en forståelse af, hvordan du får adgang til oplysningerne om hændelser for forskellige slags trusler.

Få mere at vide [under Hændelser i Microsoft 365 Defender](incidents-overview.md).

## <a name="improved-processes"></a>Forbedrede processer

Almindelige kontrolelementer og indhold vises enten på samme sted, eller de er sammen komprimeret til ét feed med data, som gør det nemmere at finde. For eksempel samlede indstillinger.

### <a name="unified-settings"></a>Samlede indstillinger

![klikkede på "Roller" og åbnede siden Indstillinger, som omfatter Generelle indstillinger, Tilladelser, API'er og regler. Åbn Tilladelser og derefter Roller. Viser alle roller.](../../media/converged-add-role-9.png)

### <a name="permissions--roles"></a>Tilladelser & roller

![Tilladelser på & Roller, der viser slutpunktsroller & grupper, roller og enhedsgrupper.](../../media/converged-roles-5.png)

 Adgang til Microsoft 365 Defender er konfigureret med Azure Active Directory globale roller eller ved hjælp af brugerdefinerede roller. For Defender til slutpunkt skal du se [Tildel brugeradgang til Microsoft Defender Security Center](/microsoft-365/security/defender-endpoint/assign-portal-access). Hvis du har brug for Defender Office 365, [skal du se Tilladelser i Microsoft 365 Overholdelsescenter og Microsoft 365 Defender](../office-365-security/permissions-microsoft-365-compliance-security.md).

- Få mere at vide om[, hvordan du administrerer adgang til Microsoft 365 Defender](m365d-permissions.md)
- Få mere at vide om, [hvordan du opretter brugerdefinerede](custom-roles.md) roller i Microsoft 365 Defender

> [!NOTE]
> Microsoft Defender til slutpunkt i Microsoft 365 Defender understøtter tildeling af adgang [](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) til administrerede sikkerhedstjenesteudbydere på samme måde som adgang i [Microsoft Defender Security Center](./mssp-access.md).

### <a name="integrated-reports"></a>Integrerede rapporter

Rapporter er også samlet i Microsoft 365 Defender. Administratorer kan starte med en generel sikkerhedsrapport og forgrene sig til bestemte rapporter om slutpunkter, & samarbejde. Linkene her genereres dynamisk baseret på arbejdsbelastningskonfiguration.

### <a name="quickly-view-your-microsoft-365-environment"></a>Få hurtigt vist dit Microsoft 365 miljø

**Startsiden** viser mange af de fælles kort, sikkerhedsteams skal bruge. Kompositionen af kort og data afhænger af brugerrollen. Da Microsoft 365 Defender portal bruger rollebaseret adgangskontrol, får forskellige roller vist kort, der giver mere mening for deres daglige job.  

Disse oversigtsoplysninger hjælper dig med at holde dig trit med de seneste aktiviteter i organisationen. Microsoft 365 Defender samler signaler fra forskellige kilder for at præsentere en fantastisk visning af dit Microsoft 365 miljø.

Kortene kan ind under disse kategorier:

- **Identities**- Monitor the identities in your organization and keep track of suspicious or risky behaviors. [Få mere at vide om identitetsbeskyttelse](/azure/active-directory/identity-protection/overview-identity-protection).
- **Data** – Hjælp med at spore brugeraktivitet, der kan føre til uautoriseret videregivelse af data.
- **Enheder** – Få opdaterede oplysninger om beskeder, brudaktivitet og andre trusler på dine enheder.
- **Apps** – Få indsigt i, hvordan skyapps bruges i din organisation. [Få mere at vide Cloud App Security opdagede apps](/cloud-app-security/discovered-apps).

## <a name="threat-analytics-with-better-data-coverage"></a>Trusselsanalyse med bedre datadækning
Spor og svar på nye trusler med følgende Microsoft 365 Defender integreret oplevelse af trusselsanalyse:

- Bedre datadækning mellem Microsoft Defender til Slutpunkt og Microsoft Defender til Office 365, hvilket gør kombineret hændelsesstyring, automatisk undersøgelse, afhjælpning og proaktiv eller reaktiv trusselssøgning på tværs af domæner mulig. 
- Mailrelaterede registreringer og afhjælpninger fra Microsoft Defender for Office 365 samt de slutpunktsdata, der allerede er tilgængelige fra Microsoft Defender til slutpunkt.
- En oversigt over trusselsrelaterede hændelser, som samler beskeder til ende-til-ende-angrebshistorier på tværs af Microsoft Defender for Endpoint og Microsoft Defender til Office 365 for at reducere arbejdskøen, samt forenkle og sætte fart på din undersøgelse.
- Angrebsforsøg registreret og blokeret af Microsoft 365 Defender løsninger. Der findes også data, som du kan bruge til at køre sikkerhedsforanstaltninger, der reducerer risikoen for yderligere eksponering og øger fleksibiliteten. 
- Forbedret design, der placerer brugbare oplysninger i spotlyset for at hjælpe dig med hurtigt at identificere data, der haster med at fokusere på, undersøge og udnytte fra rapporterne.

## <a name="a-centralized-learning-hub"></a>En centraliseret Learning Hub

Microsoft 365 Defender indeholder en læringshub, der bobler op med officiel vejledning fra ressourcer som f.eks. Microsoft-sikkerhedsbloggen, Microsofts sikkerhedsfællesskab på YouTube og den officielle dokumentation på docs.microsoft.com.

I læringshubben er vejledningen Mail & Collaboration (Microsoft Defender for Office 365) side om side med Slutpunkt (Microsoft Defender til slutpunkt) og Microsoft 365 Defender læringsressourcer.

Læringshubben åbnes med Learning, der er organiseret omkring emner som f.eks. "Sådan undersøger du Microsoft 365 Defender?" og "Microsoft Defender for Office 365 bedste fremgangsmåder". Dette afsnit er aktuelt af sikkerhedsproduktgruppen i Microsoft. Hver Learning sti afspejler en projiceret tid, det tager at gennemgå koncepterne. Det kan f.eks. være "Trin, der skal tages, når en Microsoft Defender for Office 365-brugerkonto er kompromitteret" projiceret til at tage 8 minutter, og det er værdifuld læring på farten.

Når du har klikket igennem til indholdet, kan det være nyttigt at bogmærke dette websted og organisere bogmærker i en mappe med navnet "Sikkerhed" eller "Kritisk". Hvis du vil Learning alle stierne, skal du klikke på linket Vis alle i hovedpanelet.

> [!NOTE]
> Der er nyttige **filtre** langs toppen af Microsoft 365 Defender Learning Hub, hvor du kan vælge mellem produkter (aktuelt Microsoft 365 Defender, Microsoft Defender til slutpunkt og Microsoft Defender til Office 365). Bemærk, at antallet af undervisningsressourcer for hver sektion er angivet, hvilket kan hjælpe elever med at holde styr på, hvor mange ressourcer de har til uddannelse og læring.
>
> Sammen med Produktfilter, aktuelle emner, typer af ressourcer (fra videoer til webinarer), niveauer af kendskab til eller erfaring med sikkerhedsområder, sikkerhedsroller og produktfunktioner vises.

> [!TIP]
> Der er mange andre læringsmuligheder i [Microsoft Learn](/learn/). Du kan finde certificeringskurser som [MS-500T02-A, som f.eks. kursus MS-500T02-A: implementering Microsoft 365 Threat Protection](/learn/certifications/courses/ms-500t02).

## <a name="send-us-your-feedback"></a>Send os din feedback

Vi har brug for din feedback. Vi vil altid gerne forbedre os, så hvis der er noget, du kunne tænke dig, kan du sende [os din Microsoft 365 Defender feedback](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

Du kan også give feedback fra denne artikel. I afsnittet "Feedback" til sidst under "Send og vis feedback til" er indstillingerne *Dette produkt* eller *Denne side*.

Brug knappen **Dette produkt** til feedback *om* produktet:

1. Vælg *Dette* produkt nederst i artiklen.
    1. Højreklik på knappen og "Åbn i en ny fane", hvis du vil fortsætte med at læse disse anvisninger.
2. Dette navigerer til **UserVoice-forummet**.
3. Du har to muligheder:
    1. Rul ned til tekstfeltet Hvordan kan vi forbedre overholdelse eller beskytte dine brugere bedre *i Office 365?* og indsætte *Microsoft 365 Defender*. Du kan søge i resultaterne efter en idé som din og stemme op på den, eller du kan bruge knappen til at **slå en ny idé op**.
    1. Hvis du mener, at dette problem allerede er rapporteret, og du vil hæve profilen med en stemme (eller stemmer), skal du bruge feltet *Giv feedback* i højre side af UserVoice. Søg efter *Microsoft 365 Defender*, **find problemet, og brug stemmeknappen til** at hæve status.

Brug *Denne side* til feedback på selve artiklen. Tak for din feedback. Din stemme hjælper os med at forbedre produkter.

### <a name="explore-what-the-security-center-has-to-offer"></a>Udforsk, hvad sikkerhedscenteret kan tilbyde

Fortsæt med at udforske funktionerne og egenskaberne i Microsoft 365 Defender:

- [Administrer hændelser og beskeder](manage-incidents.md)
- [Spore og reagere på nye trusler med trusselsanalyse](threat-analytics.md)
- [Handlingscenter](m365d-action-center.md)
- [Lede efter trusler på tværs af enheder, mails, apps og identiteter](./advanced-hunting-query-emails-devices.md)
- [Brugerdefinerede registreringsregler](./custom-detection-rules.md)
- [Beskeder & mailsamarbejde](../../compliance/alert-policies.md#default-alert-policies)
- [Opret en simulering af phishingangreb](../office-365-security/attack-simulation-training.md)[, og opret en nyttelast til oplæring af dine teams](/microsoft-365/security/office-365-security/attack-simulation-training-payloads)
 
### <a name="related-information"></a>Relaterede oplysninger
- [Microsoft Defender til Office 365 i Microsoft 365 Defender](microsoft-365-security-center-mdo.md)
- [Microsoft Defender til slutpunkt i Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Omdirigere konti fra Microsoft Defender for Endpoint til Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)