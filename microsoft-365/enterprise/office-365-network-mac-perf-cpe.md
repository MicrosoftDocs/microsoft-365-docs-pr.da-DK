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
ms.openlocfilehash: f35257520385f8d4287c9a0839cd1e4e0e6b0aa3
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/07/2021
ms.locfileid: "63591019"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 informeret netværksrouting

Informeret netværksrouting er en funktion, der integrerer forskellige Microsoft 365-programmer med softwaredefinerede netværksløsninger (SD-WAN) fra tredjepart med henblik på at optimere og forbedre din netværksforbindelse til Microsoft-tjenesteslutpunkter. Optimeret SD-WAN-forbindelse kan give bedre brugeroplevelser og ydeevne.

## <a name="overview"></a>Oversigt

Informeret netværksrouting giver en tovejs-datadelingskanal mellem Microsoft og din SD-WAN-løsning. For alle office-placeringer og internetkredsløb, som du konfigurerer, deler Microsoft jævnligt feedback med SD-WAN-løsningen om kvaliteten af udvalgte Microsoft 365-programoplevelser til netværkstrafik, der er knyttet til hvert specifikke internetkredsløb. Med denne feedback kan SD-WAN-løsningen derefter udføre intelligente genoprettelseshandlinger ved at dirigere Microsoft 365 programtrafik via alternative tilgængelige links. 

Forringet tjenestekvalitet i stien til et bestemt internetkredsløb, f.eks. øget ventetid eller høj pakketab, er svære at registrere løbende. Disse forringelser kan være negativ i forhold til brugeroplevelser til programmer som Exchange Online, SharePoint, OneDrive og Microsoft Teams. Almindelige symptomer omfatter langsom søgning af Exchange-indhold, høje overførselstider, når du interagerer med SharePoint- eller OneDrive-dokumentbiblioteker, dårlig opkalds- eller mødekvalitet Microsoft Teams.

Feedback- og genoprettelsesmekanismen inden for informeret netværksrouting søger dynamisk at registrere sådanne problemer i nærheden af realtid og informerer den installerede SD-WAN-løsning om at udføre automatiske genoprettelseshandlinger.

Datadelingskanalen bruges også til jævnligt at modtage optikdata på netværksniveau fra SD-WAN-løsningen, herunder konfigurationsoplysninger og statistik for brug, der er knyttet til enheden og tilknyttede kredsløb. Der indsamles eller gemmes ingen personlige oplysninger. Alle indsamlede oplysninger samles på kontorplaceringer og tilknyttede internetkredsløb. Disse oplysninger kan hjælpe Microsoft med mere effektivt at løse rapporterede problemer med din brug af Microsoft 365 og -programmer.

>[!NOTE]
>Microsoft 365 informeret netværksrouting understøtter lejere i WW Commercial Cloud, men ikke GCC Moderate, GCC High, DoD, Germany eller Kinas skyer.

## <a name="requirements"></a>Krav

### <a name="integrated-sd-wan-solutions"></a>Integrerede SD-WAN-løsninger

Microsoft arbejder sammen med forskellige partnere for at muliggøre integration med Microsoft 365 informeret netværksrouting. Aktuelt aktiverede løsninger omfatter følgende:

| Device Maker | Løsningsnavn | Minimumsversion |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Netværk topologi

Informeret netværksrouting identificerer i øjeblikket trafik, der er knyttet til en bestemt office-placering og internetkredsløb, baseret på den offentlige IP-adresse, der bruges til at sende netværkstrafik til Microsoft. 

I tilfælde, hvor der ikke er mindst ét netværkskredsløb, der giver direkte internetadgang på en afdelingsplacering, giver informeret netværksrouting muligvis ikke en betydelig værdi.

### <a name="application-usage"></a>Anvendelse af program

Programoplevelsesdata (afspejles via målepunkter for netværkskvalitet) indsamles via brugen af bestemte Microsoft-klientprogrammer. Exchange målepunkter afspejler brugen af Outlook klient samt nogle Outlook Web App brug. SharePoint og OneDrive afspejler brugen af de lejerspecifikke SharePoint slutpunkter, uanset klientprogrammet. Teams målepunkter afspejler brugen af Teams desktopklienten. Andre programtrafik tages ikke i betragtning, når et netværkskredsløbs tilstand evalueres.

## <a name="enabling-informed-network-routing"></a>Aktivering af informeret netværksrouting

Aktivering af informeret netværksrouting kræver flere trin, hvoraf nogle skal udføres inden for konfigurationsgrænsefladen for din SD-WAN-løsning. Kontakt din SD-WAN-løsningsleverandør for at få en vejledning i, hvordan du starter processen med at aktivere informeret netværksrouting inden for SD-WAN-løsningen, før du fortsætter med konfigurationen i Microsoft 365 Administration.

Når du er klar til at aktivere informeret netværksrouting i Microsoft 365 Administration, skal du sikre **dig, at** du har de nødvendige brugeradministrator- eller **globale** administratortilladelser.

>[!IMPORTANT]
>For at give samtykke på lejerniveau til den valgte SD-WAN-løsning for at få adgang til den informerede kanal for routing af datadeling i netværket skal du udføre følgende trin som global administrator.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Trin 1: Åbne konfigurationsindstillinger for SD-WAN-løsninger

På siden [Microsoft 365 Administration](https://admin.microsoft.com/) du **vælge > Netværksforbindelse i** venstre navigationsrude.

Dette afsnit i Administration indeholder aggregerede målepunkter for netværksforbindelsen for organisationen og vejledning i, hvordan du forbedrer din forbindelse. Se [Netværksforbindelse i Microsoft 365 Administration for yderligere](office-365-network-mac-perf-overview.md) oplysninger om disse funktioner, der er tilgængelige i Administration.

Vælg **Indstillinger > SD-WAN-løsning for at** åbne den informerede rude til konfiguration af netværksrouting. De andre indstillinger, der vises under **Indstillinger**, er gældende for den generelle vejledning i netværksforbindelse i Administration og er ikke påkrævet for at aktivere informeret netværksrouting.

I konfigurationsruden skal du **vælge Tilføj din SD-WAN-løsning**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>Trin 2: Vælg din SD-WAN-løsning og datalagringsplacering

I rullelisten skal du vælge den SD-WAN-løsning, du har installeret, og den placering, hvor du vil have de data, der er knyttet til informeret netværksrouting, gemt. Du kan [finde flere oplysninger](#data-storage) i afsnittet om datalager.

Vælg **Næste**.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>Trin 3: Acceptér vilkår for deling af data

Læs og accepter omhyggeligt de angivne vilkår, der er knyttet til deling af data mellem Microsoft og din valgte SD-WAN-løsning, og markér derefter det angivne afkrydsningsfelt.

Vælg **Næste**.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>Trin 4: Giv tilladelser til SD-WAN-løsningen

Dette trin starter en anmodning om tilladelsestilladelser Azure Active Directory (Azure AD). Du bliver bedt om at give tilladelser på lejerniveau, der giver din valgte SD-WAN-løsning adgang til den informerede netværksroutingdatalager og de oplysninger om tjenestestilstand, der er knyttet til din lejer. Denne handling kræver **Azure AD DC-administrator** eller **globale administratorrolletilladelser** .

Vælg linket **Giv tilladelse til dette program,** og følg Azure AD-anmodningerne.

Når du har fuldført tildelingen af tilladelser, skal du vælge **Næste**.

### <a name="step-5-confirm-your-configuration-settings"></a>Trin 5: Bekræft konfigurationsindstillingerne

Det sidste trin til at aktivere informeret netværksrouting for din lejer er en bekræftelsesside, der viser de indstillinger, du har angivet. 

Informeret netværksrouting er nu aktiveret for din lejer.

Vælg **Udført** , og luk derefter konfigurationsruden for SD-WAN-løsninger.

## <a name="configuring-informed-network-routing"></a>Konfiguration af informeret netværksrouting

Du skal udføre meget af konfigurationen for informeret netværksrouting inden for din SD-WAN-løsning, f.eks. konfiguration af, hvordan din trafik skal dirigeres under normale omstændigheder, og de alternative stier, der skal bruges, hvis der registreres problemer. Kontakt din SD-WAN-løsningsudbyder for at få mere at vide om disse konfigurationstrin.

Hver kontorplacering skal konfigureres i Microsoft 365 Administration så informeret netværksrouting korrekt kan identificere trafik, der er knyttet til de netværkskredsløb, der giver forbindelse til disse placeringer.

Office placeringer kan blive registreret automatisk som en del af Microsofts løbende samling af netværkstelemetri. Derfor er nogle placeringer muligvis udfyldt på forhånd i Administration for din lejer. 

Hvis disse placeringer er nøjagtige, skal du blot aktivere den informerede funktion til netværksrouting for hver ønskede placering og konfigurere internetkredsløbene og deres offentlige IP-adresser. 

Hvis de automatisk registrerede placeringer ikke er nøjagtige, eller der ikke er udfyldt nogen placeringer i din lejer på forhånd, skal du tilføje eller redigere placeringer manuelt for at afspejle en nøjagtig topologi i organisationen.

### <a name="updating-locations"></a>Opdatering af placeringer

Placeringer for din lejer kan findes under **fanen** Placeringer. Placeringer kan redigeres direkte på listen eller opdateres ved hjælp af en CSV-fil.

Sørg for, at hver enkelt kontorplacering, hvor du vil aktivere informeret netværksrouting, findes på denne liste.

>[!NOTE]
>Kolonnerne på listen **Placeringer for stikprøver, der indsamles, og andre vurderingsrelaterede** oplysninger er ikke relateret til den informerede funktion til routing af netværk.

### <a name="enabling-a-location-for-informed-network-routing"></a>Aktivering af en placering til informeret netværksrouting

1. På listen **Placeringer skal du** vælge Rediger **i menuen** Hurtige handlinger for at åbne ruden til konfiguration af placering.

2. Vælg **Brug Microsoft 365 informeret netværksrouting på denne placering**.

3. Tilføj alle netværkskredsløb, der giver forbindelse til denne kontorplacering **, i Egress IP-adresseintervaller på denne placering.** Sørg for, at hvert kredsløb er knyttet til de entydige offentlige IP-adresseundernet, der repræsenterer din netværkstrafik.

4. Vælg **Gem** for at gemme ændringerne.

## <a name="disabling-informed-network-routing"></a>Deaktivere informeret netværksrouting

Den informerede netværksroutingsfunktion kan deaktiveres for hele lejeren ved at nulstille dine SD-WAN-løsningsindstillinger. Dette stopper al behandling af data inden for Microsoft 365, men du bør også deaktivere informeret netværksrouting i Administration.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>Trin 1: Åbne konfigurationsindstillinger for SD-WAN-løsninger

I [navigationsruden Microsoft 365 Administration](https://admin.microsoft.com/) **du > vælge Netværksforbindelse** i navigationsruden til venstre.

Vælg **Indstillinger > SD-WAN-løsning for at** åbne den informerede rude til konfiguration af netværksrouting.

Konfigurationsruden viser en oversigt over din aktuelt konfigurerede SD-WAN-løsning.

### <a name="step-2-reset-your-configuration"></a>Trin 2: Nulstil din konfiguration

I konfigurationsruden skal du vælge **Nulstil dine SD-WAN-løsningsindstillinger**.

Dine indstillinger er nu blevet nulstillet, og informeret netværksrouting er blevet deaktiveret. Du kan når som helst genaktivere den ved at følge trinnene i [Aktivere informeret netværksrouting](#enabling-informed-network-routing).

## <a name="data-storage"></a>Datalager

Data, der udveksles mellem Microsoft og SD-WAN-løsningsudbyderen, gemmes på den datalagerplacering, der blev valgt under den indledende aktivering af informeret netværksrouting. Indstillingerne for datalagerplacering repræsenterer geografiske områder, der Microsoft Azure områder, hvor dataene er gemt.

Data bevares på denne placering i op til 30 dage. Når den er deaktiveret, fjernes alle resterende data inden for dette 30-dages opbevaringsvindue.

Data på denne placering udveksles med den valgte SD-WAN-løsning, og placeringen af den konfigurerede SD-WAN-løsning er muligvis ikke inden for samme område. Kunder skal arbejde sammen med deres SD-WAN-løsningsudbyder for at evaluere eventuelle krav til datalagerplacering før produktionsinstallation.

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse på Microsoft 365 Administration](office-365-network-mac-perf-overview.md)

[Microsoft 365 til placeringstjenester for netværksforbindelse](office-365-network-mac-location-services.md)
