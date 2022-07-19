---
title: Microsoft 365 Defender-portal
description: Portalen Microsoft 365 Defender kombinerer beskyttelse, registrering, undersøgelse og svar på mail, samarbejde, identitet, enhed og apptrusler på et centralt sted.
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
ms.openlocfilehash: c2915adc7b9b49015cdb436886563c4eba74d989
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/05/2022
ms.locfileid: "66858919"
---
# <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender-portal

[Portalen Microsoft 365 Defender](https://sip.security.microsoft.com/homepage?tid=72f988bf-86f1-41af-91ab-2d7cd011db47) kombinerer beskyttelse, registrering, undersøgelse og svar på mail, samarbejde, identitet, enhed og trusler mod cloudapps på et centralt sted. I Microsoft 365 Defender-portalen lægges der vægt på hurtig adgang til oplysninger, enklere layout og samle relaterede oplysninger, så de bliver nemmere at bruge. Den indeholder:

- **[Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/defender-for-office-365)** Microsoft Defender for Office 365 hjælper organisationer med at beskytte deres virksomhed med et sæt funktioner til forebyggelse, registrering, undersøgelse og jagt for at beskytte mail og Office 365 ressourcer.
- **[Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-advanced-threat-protection)** leverer forebyggende beskyttelse, registrering efter sikkerhedsbrud, automatisk undersøgelse og svar til enheder i din organisation.
- **[Microsoft Defender for Identity](/defender-for-identity/what-is)** er en cloudbaseret sikkerhedsløsning, der udnytter dine Active Directory i det lokale miljø signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation.
- **[Microsoft Defender for Cloud Apps](/cloud-app-security/)** er en omfattende saaS- og PaaS-løsning, der giver dig dyb synlighed, stærke datakontroller og forbedret trusselsbeskyttelse af dine cloudapps.

Se denne korte video for at få mere at vide om portalen Microsoft 365 Defender.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBKau]

## <a name="what-to-expect"></a>Hvad kan du forvente?

Portalen Microsoft 365 Defender hjælper sikkerhedsteams med at undersøge og reagere på angreb ved at hente signaler fra forskellige arbejdsbelastninger ind i en række samlede oplevelser for:

- Hændelser & beskeder
- Jagt
- Handlinger & indsendelser
- Trusselsanalyse
- Secure Score
- Læringshub
- Forsøg

Microsoft 365 Defender lægger vægt på *enhed, klarhed og fælles mål*. 

> [!NOTE]
> Microsoft 365 Defender-portalen er tilgængelig, uden at kunderne behøver at udføre migreringstrin eller købe en ny licens. Denne nye portal er f.eks. tilgængelig for administratorer med et E3-abonnement, ligesom den er tilgængelig for dem med Microsoft Defender for Office 365 Plan 1 og Plan 2, men Exchange Online Protection eller Defender for Office 365  Plan 1-kunder kan kun se de sikkerhedsfunktioner, deres abonnementslicens understøtter. Målet med portalen er at centralisere sikkerheden.

## <a name="incident-and-alert-investigations"></a>Efterforskning af hændelser og advarsler

Centralisering af sikkerhedsoplysninger opretter et enkelt sted til undersøgelse af sikkerhedshændelser på tværs af Microsoft 365. Et primært eksempel er **Hændelser** under **Hændelser & beskeder**.

:::image type="content" source="../../media/converged-incidents-2.png" alt-text="Siden Hændelser på Microsoft 365 Defender-portalen" lightbox="../../media/converged-incidents-2.png":::

Når du vælger et hændelsesnavn, vises en side, der viser værdien af at centralisere sikkerhedsoplysninger, da du får bedre indsigt i den fulde udvidelse af en trussel fra mail til identitet til slutpunkter.

:::image type="content" source="../../media/converged-incident-info-3.png" alt-text="Oversigtssiden for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/converged-incident-info-3.png":::

Tag dig tid til at gennemse hændelserne i dit miljø, foretage detailudledning i hver besked og øve dig i at opbygge en forståelse af, hvordan du får adgang til oplysningerne og fastlægge de næste trin i din analyse.

Du kan få flere oplysninger [under hændelser i Microsoft 365 Defender](incidents-overview.md).

## <a name="hunting"></a>Jagt
Du kan oprette brugerdefinerede regler for registrering og jagte bestemte trusler i dit miljø. **Jagt** bruger et forespørgselsbaseret værktøj til trusselsjagt, der giver dig mulighed for proaktivt at inspicere hændelser i din organisation for at finde trusselsindikatorer og enheder. Disse regler kører automatisk for at kontrollere, om der er mistanke om brudaktivitet, forkert konfigurerede maskiner og andre resultater.

Du kan finde flere oplysninger under [Proaktiv jagt efter trusler med avanceret jagt i Microsoft 365 Defender](advanced-hunting-overview.md).

## <a name="improved-processes"></a>Forbedrede processer

Almindelige kontrolelementer og indhold vises enten på samme sted eller komprimeres til ét datafeed, hvilket gør det nemmere at finde det. Det kan f.eks. være samlede indstillinger.

### <a name="unified-settings"></a>Samlede indstillinger

:::image type="content" source="../../media/converged-add-role-9.png" alt-text="Siden Indstillinger på Microsoft 365 Defender-portalen" lightbox="../../media/converged-add-role-9.png":::

### <a name="permissions--roles"></a>Tilladelser & roller

:::image type="content" source="../../media/converged-roles-5.png" alt-text="Slutpunktsrollerne & grupper, der vises på siden Tilladelser & roller" lightbox="../../media/converged-roles-5.png":::

Adgang til Microsoft 365 Defender er konfigureret med Azure AD globale roller eller ved hjælp af brugerdefinerede roller.

- Få mere at vide om, hvordan [du administrerer adgang til Microsoft 365 Defender](m365d-permissions.md)
- Få mere at vide om, hvordan [du opretter brugerdefinerede roller](custom-roles.md) i Microsoft 365 Defender


### <a name="integrated-reports"></a>Integrerede rapporter

Rapporter er også samlet i Microsoft 365 Defender. Administratorer kan starte med en generel sikkerhedsrapport og forgrene sig til specifikke rapporter om slutpunkter, mail & samarbejde. Linkene her genereres dynamisk baseret på konfigurationen af arbejdsbelastningen.

### <a name="quickly-view-your-microsoft-365-environment"></a>Få hurtigt vist dit Microsoft 365-miljø

**På** startsiden kan du se mange af de almindelige kort, som sikkerhedsteams har brug for. Sammensætningen af kort og data afhænger af brugerrollen. Da Microsoft 365 Defender portal bruger rollebaseret adgangskontrol, kan forskellige roller se kort, der giver mere mening for deres daglige job.

Disse hurtigt overbliksoplysninger hjælper dig med at holde dig opdateret om de nyeste aktiviteter i din organisation. Microsoft 365 Defender samler signaler fra forskellige kilder for at præsentere en holistisk visning af dit Microsoft 365-miljø.

Du kan tilføje og fjerne forskellige kort, afhængigt af dine behov.

### <a name="search-across-entities-preview"></a>Søg på tværs af enheder (prøveversion)

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

## <a name="threat-analytics"></a>Trusselsanalyse

Spor og reager på nye trusler med følgende Microsoft 365 Defender trusselsanalyse: Threat Analytics er den Microsoft 365 Defender løsning til trusselsintelligens fra ekspertforskere i Microsoft-sikkerhed. Den er designet til at hjælpe sikkerhedsteams med at være så effektive som muligt, mens de står over for nye trusler, f.eks.:

- Aktive trusselsaktører og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sikkerhedsrisici
- Almindelige angrebsoverflader
- Udbredt malware

## <a name="learning-hub"></a>Læringshub

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a> indeholder en læringshub, der indeholder vejledning fra ressourcer som Microsofts sikkerhedsblog, Microsofts sikkerhedsfællesskab på YouTube og den officielle dokumentation.

> [!NOTE]
> Der er nyttige **filtre** langs toppen af Microsoft 365 Defender læringshub, der giver dig mulighed for at vælge mellem produkter (i øjeblikket Microsoft 365 Defender, Microsoft Defender for Endpoint og Microsoft Defender for Office 365). Bemærk, at antallet af læringsressourcer for hvert afsnit er angivet, hvilket kan hjælpe eleverne med at holde styr på, hvor mange ressourcer de har til rådighed til uddannelse og læring.
>
> Sammen med produktfilteret vises aktuelle emner, typer af ressourcer (fra videoer til webinarer), kendskab til eller erfaring med sikkerhedsområder, sikkerhedsroller og produktfunktioner.

> [!TIP]
> Der er mange andre læringsmuligheder i [Microsoft Learn](/learn/). Du finder certificeringskurser som f.eks [. kursus MS-500T02-A: Implementering af Microsoft 365 Threat Protection](/learn/certifications/courses/ms-500t02).

## <a name="send-us-your-feedback"></a>Send os din feedback

Vi har brug for din feedback. Vi vil altid forbedre os, så hvis der er noget, du gerne vil se, kan du [se denne video for at finde ud af, hvordan du kan stole på, at vi læser din feedback](https://www.microsoft.com/videoplayer/embed/RE4K5Ci).

## <a name="explore-what-the-microsoft-365-defender-portal-has-to-offer"></a>Udforsk, hvad Microsoft 365 Defender-portalen tilbyder

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
