---
title: Microsoft 365 informeret netværksrouting
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 informeret netværksrouting
ms.openlocfilehash: fc946b3a1de057605b89bcadeb4e5b7269aebcb0
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622485"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 informeret netværksrouting

Informeret netværksrouting er en funktion, der integrerer forskellige Microsoft 365 programmer med SD-WAN-løsninger (softwaredefinerede netværk) fra tredjepart for at optimere og forbedre din netværksforbindelse til Microsoft-tjenesteslutpunkter. Optimeret SD-WAN-forbindelse kan resultere i forbedrede brugeroplevelser og ydeevne.

## <a name="overview"></a>Oversigt

Informeret netværksrouting giver en tovejs-datadelingskanal mellem Microsoft og din SD-WAN-løsning. For hver kontorplacering og hvert internetkredsløb, som du konfigurerer, deler Microsoft jævnligt feedback med SD-WAN-løsningen om kvaliteten af udvalgte Microsoft 365 programoplevelser for netværkstrafik, der er knyttet til hvert specifikke internetkredsløb. Ved hjælp af denne feedback kan SD-WAN-løsningen derefter foretage intelligente genoprettelseshandlinger ved at dirigere Microsoft 365 programtrafik via alternative tilgængelige links. 

Kvaliteten af tjenesteforringelser i forbindelse med et bestemt internetkredsløb, f.eks. øget ventetid eller højt pakketab, er svære at detektere på kontinuerlig basis. Disse forringelser kan være skadelige for brugeroplevelser for programmer som Exchange Online, SharePoint, OneDrive og Microsoft Teams. Almindelige symptomer omfatter langsom søgning efter Exchange indhold, høje overførselstider, når der interageres med SharePoint eller OneDrive dokumentbiblioteker, eller dårlig opkalds- eller mødekvalitet i Microsoft Teams.

Feedback- og genoprettelsesmekanismen inden for informeret netværksrouting søger dynamisk at registrere sådanne problemer i næsten realtid og informerer den udrullede SD-WAN-løsning om at foretage automatiske genoprettelseshandlinger.

Datadelingskanalen bruges også til jævnligt at modtage optikdata på netværksniveau fra SD-WAN-løsningen, herunder konfigurationsoplysninger og brugsstatistikker, der er knyttet til enheden og tilknyttede kredsløb. Der indsamles eller gemmes ingen personlige oplysninger. Alle indsamlede oplysninger samles på kontorplaceringer og forbundne internetkredsløb. Disse oplysninger kan hjælpe Microsoft med mere effektivt at løse rapporterede problemer med din brug af Microsoft 365 tjenester og programmer.

>[!NOTE]
>Microsoft 365 informerede netværksrouting understøtter lejere i WW Commercial-cloudmiljøet, men ikke cloudmiljøerne GCC Moderate, GCC High, DoD, Germany eller China.

## <a name="requirements"></a>Krav

### <a name="integrated-sd-wan-solutions"></a>Integrerede SD-WAN-løsninger

Microsoft arbejder sammen med forskellige partnere for at muliggøre integration med Microsoft 365 informeret netværksrouting. Løsninger, der er aktiveret i øjeblikket, omfatter følgende:

| Enhedsopretter | Løsningsnavn | Minimumversion |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Netværkstopologi

Informeret netværksrouting identificerer i øjeblikket trafik, der er knyttet til en bestemt kontorplacering og internetkredsløb, baseret på den offentlige IP-adresse, der bruges til at sende netværkstrafik til Microsoft. 

Hvis der ikke er mindst ét netværkskredsløb, der giver direkte internetadgang på en forgreningsplacering, giver informeret netværksrouting muligvis ikke nogen betydelig værdi.

### <a name="application-usage"></a>Programanvendelse

Programoplevelsesdata (afspejlet via målepunkter for netværkskvalitet) indsamles via brug af specifikke Microsoft-klientprogrammer. Exchange målepunkter afspejler brugen af Outlook-klienten og noget Outlook Web App forbrug. SharePoint og OneDrive målepunkter afspejler brugen af de lejerspecifikke SharePoint slutpunkter, uanset klientprogram. Teams målepunkter afspejler brugen af Teams desktopklienten. Anden programtrafik tages ikke i betragtning, når du evaluerer tilstanden af et netværkskredsløb.

## <a name="enabling-informed-network-routing"></a>Aktivering af informeret netværksrouting

Aktivering af informeret netværksrouting kræver flere trin, hvoraf nogle skal udføres i konfigurationsgrænsefladen i SD-WAN-løsningen. Kontakt din SD-WAN-løsningsleverandør for at få vejledning i, hvordan du starter processen med at aktivere informeret netværksrouting i SD-WAN-løsningen, før du fortsætter med konfigurationen i Microsoft 365 Administration.

Når du er klar til at aktivere informeret netværksrouting i Microsoft 365 Administration, skal du sikre dig, at du har de nødvendige **brugeradministrator**- eller **globale administratortilladelser**.

>[!IMPORTANT]
>Hvis du vil give det nødvendige tilladelsessamtykke for programmer på lejerniveau til den valgte SD-WAN-løsning for at få adgang til den informerede netværksroutingdatadelingskanal, skal du udføre følgende trin som global administrator.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Trin 1: Åbn konfigurationsindstillinger for SD-WAN-løsninger

I [Microsoft 365 Administration](https://admin.microsoft.com/) skal du vælge **Tilstand > Netværksforbindelse** i navigationsruden til venstre.

Dette afsnit af Administration indeholder samlede målepunkter for netværksforbindelsen for din organisation og vejledning til, hvordan du kan forbedre din forbindelse. Se [Netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md) for at få flere oplysninger om disse funktioner, der er tilgængelige i Administration.

Vælg **Indstillinger > SD-WAN-løsning** for at åbne konfigurationsruden for informeret netværksrouting. De andre indstillinger, der vises under **Indstillinger**, gælder for den generelle vejledning til netværksforbindelser i Administration og er ikke påkrævet for at aktivere informeret netværksrouting.

I konfigurationsruden skal du vælge **Tilføj din SD-WAN-løsning**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Trin 2: Vælg din SD-WAN-løsning og datalagerplacering

I rullelisterne skal du vælge den SD-WAN-løsning, du har installeret, og den placering, hvor du vil have de data, der er knyttet til informeret netværksrouting, gemt. Se afsnittet [om datalager](#data-storage) for at få flere oplysninger.

Vælg **Næste**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Trin 3: Acceptér vilkår for deling af data

Læs omhyggeligt og bekræft de angivne vilkår, der er knyttet til deling af data mellem Microsoft og din valgte SD-WAN-løsning, og markér derefter det angivne afkrydsningsfelt.

Vælg **Næste**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Trin 4: Giv tilladelser til SD-WAN-løsningen

Dette trin starter en anmodning om tildeling af tilladelser med Azure Active Directory (Azure AD). Du bliver bedt om at give tilladelser på lejerniveau, der giver din valgte SD-WAN-løsning adgang til det informerede datalager for netværksrouting og de tjenestetilstandsoplysninger, der er knyttet til din lejer. Denne handling kræver **Azure AD dc-administrator** eller **rolletilladelser som global administrator**.

Vælg linket **Giv tilladelse til dette program**, og følg anmodningerne om Azure AD.

Når du har fuldført tilladelserne, skal du vælge **Næste**.

### <a name="step-5-confirm-your-configuration-settings"></a>Trin 5: Bekræft dine konfigurationsindstillinger

Det sidste trin i aktivering af informeret netværksrouting for din lejer er en bekræftelsesside, der viser de indstillinger, du har angivet. 

Informeret netværksrouting er nu aktiveret for din lejer.

Vælg **Udført** , og luk derefter konfigurationsruden for SD-WAN-løsningen.

## <a name="configuring-informed-network-routing"></a>Konfiguration af informeret netværksrouting

Du skal udføre en stor del af konfigurationen for informeret netværksrouting i din SD-WAN-løsning, f.eks. konfiguration af, hvordan din trafik skal distribueres under normale omstændigheder, og de alternative stier, der skal bruges, hvis der registreres problemer. Kontakt SD-WAN-løsningsudbyderen for at få oplysninger om disse konfigurationstrin.

Hver office-placering skal konfigureres i Microsoft 365 Administration, så informeret netværksrouting på korrekt vis kan identificere trafik, der er knyttet til de netværkskredsløb, der giver forbindelse til disse placeringer.

Office placeringer kan registreres automatisk som en del af Microsofts løbende samling af netværkstelemetri. Derfor kan nogle placeringer være udfyldt på forhånd i Administration for din lejer. 

Hvis disse placeringer er nøjagtige, skal du blot aktivere funktionen til informeret netværksrouting for hver ønsket placering og konfigurere internetkredsløbene og deres offentlige IP-adresser. 

Hvis de automatisk registrerede placeringer ikke er nøjagtige, eller hvis der ikke er udfyldt nogen placeringer på forhånd i din lejer, skal du tilføje eller redigere placeringer manuelt for at afspejle en nøjagtig topologi for din organisation.

### <a name="updating-locations"></a>Opdaterer placeringer

Du kan finde placeringer for din lejer under fanen **Placeringer** . Placeringer kan redigeres direkte på listen eller opdateres ved hjælp af en CSV-fil.

Sørg for, at hver office-placering, hvor du vil aktivere informeret netværksrouting, findes på denne liste.

>[!NOTE]
>Kolonnerne på listen **Placeringer** for eksempler, der indsamles, og andre vurderingsrelaterede oplysninger er ikke relateret til funktionen til informeret netværksrouting.

### <a name="enabling-a-location-for-informed-network-routing"></a>Aktivering af en placering til informeret netværksrouting

1. På listen **Placeringer** skal du vælge **Rediger** i menuen med hurtige handlinger for at åbne konfigurationsruden for placering.

2. Vælg **Brug Microsoft 365 informeret netværksrouting på denne placering**.

3. Tilføj alle netværkskredsløb, der giver internetforbindelse til denne **office-placering, i afsnittet Egress IP-adresseområder på denne office-placering**. Sørg for, at hvert kredsløb er knyttet til de entydige offentlige IP-adresseundernet, der repræsenterer netværkstrafikken.

4. Vælg **Gem** for at gemme dine ændringer.

## <a name="disabling-informed-network-routing"></a>Deaktivering af informeret netværksrouting

Funktionen til informeret netværksrouting kan være deaktiveret for hele lejeren ved at nulstille indstillingerne for SD-WAN-løsningen. Selvom dette stopper al behandling af data i Microsoft 365, bør du også deaktivere informeret netværksrouting i Administration.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Trin 1: Åbn konfigurationsindstillinger for SD-WAN-løsninger

I [Microsoft 365 Administration](https://admin.microsoft.com/) skal du vælge **Tilstand > Netværksforbindelse** i navigationsruden til venstre.

Vælg **Indstillinger > SD-WAN-løsning** for at åbne konfigurationsruden for informeret netværksrouting.

I konfigurationsruden vises en oversigt over din aktuelt konfigurerede SD-WAN-løsning.

### <a name="step-2-reset-your-configuration"></a>Trin 2: Nulstil konfigurationen

I konfigurationsruden skal du vælge **Nulstil indstillingerne for din SD-WAN-løsning**.

Dine indstillinger er nu blevet nulstillet, og den informerede netværksrouting er deaktiveret. Du kan genaktivere den når som helst ved at følge trinnene under [Aktivering af informeret netværksrouting](#enabling-informed-network-routing).

## <a name="data-storage"></a>Datalager

Data, der udveksles mellem Microsoft og SD-WAN-løsningsudbyderen, gemmes på den placering af datalageret, der blev valgt under den indledende aktivering af informeret netværksrouting. Indstillingerne for lagring af data repræsenterer geografiske områder, der indeholder Microsoft Azure områder, hvor dataene er gemt.

Data opbevares på denne placering i op til 30 dage. Når de er deaktiveret, fjernes alle resterende data i dette 30-dages opbevaringsvindue.

Data på denne placering udveksles med den valgte SD-WAN-løsning, og placeringen af den konfigurerede SD-WAN-løsning er muligvis ikke inden for det samme område. Kunder skal samarbejde med deres SD-WAN-løsningsudbyder om at evaluere krav til placering af datalager før udrulningen af produktionen.

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse i Microsoft 365 Administration](office-365-network-mac-perf-overview.md)

[Microsoft 365 placeringstjenester for netværksforbindelsen](office-365-network-mac-location-services.md)
