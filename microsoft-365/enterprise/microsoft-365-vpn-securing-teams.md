---
title: Sikring af Teams-medietrafik til VPN-opdelt tunnelføring
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
f1.keywords:
- NOCSH
description: Sikring af Teams-medietrafik til VPN-opdelt tunnelføring
ms.openlocfilehash: 715d5e02ef01db9ef1c75a063ef5a2771d425f5c
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64715379"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>Sikring af Teams-medietrafik til VPN-opdelt tunnelføring

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der omhandler Microsoft 365 optimering for fjernbrugere.

>- Hvis du vil have en oversigt over, hvordan du bruger VPN-opdelt tunnelføring til at optimere Microsoft 365 forbindelse til fjernbrugere, skal du se [Oversigt: VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Du kan finde en detaljeret vejledning i implementering af opdelt VPN-tunnelføring under [Implementering af VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdelt VPN-tunnelføring under [Almindelige scenarier med opdelt VPN-tunnelføring for Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan få mere at vide om, hvordan du konfigurerer Stream- og livebegivenheder i VPN-miljøer, under [Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).
>- Du kan få oplysninger om optimering af Microsoft 365 verdensomspændende lejerydeevne for brugere i Kina under [Microsoft 365 optimering af ydeevnen for brugere i Kina](microsoft-365-networking-china.md).

Nogle Microsoft Teams administratorer kan kræve detaljerede oplysninger om, hvordan opkaldsflow fungerer i Teams ved hjælp af en opdelt tunnelføringsmodel, og hvordan forbindelser sikres.

## <a name="configuration"></a>Konfiguration

For både kald og møder, så længe de påkrævede Optimer IP-undernet for Teams medier er korrekt på plads i rutetabellen, returneres den lokale grænseflade for Microsoft-destinationer i de Microsoft IP-blokke, der er angivet ovenfor, når Teams kalder funktionen [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) for at bestemme, hvilken lokal grænseflade der svarer til den rute, den skal bruge til en bestemt destination.

Nogle VPN-klientsoftware tillader manipulation af routing baseret på URL-adresse. Men Teams medietrafik har ingen URL-adresse tilknyttet, så styringen af routing for denne trafik skal udføres ved hjælp af IP-undernet.

I visse scenarier, der ofte ikke er relateret til Teams klientkonfiguration, gennemgår medietrafik stadig VPN-tunnellen, selv med de korrekte ruter på plads. Hvis du støder på dette scenarie, bør det være tilstrækkeligt at bruge en firewallregel til at blokere Teams IP-undernet eller porte fra at bruge VPN.

>[!IMPORTANT]
>Hvis du vil sikre dig, at Teams medietrafik dirigeres via den ønskede metode i alle VPN-scenarier, skal du sørge for, at brugerne kører Microsoft Teams klientversion **1.3.00.13565** eller nyere. Denne version indeholder forbedringer af, hvordan klienten registrerer tilgængelige netværksstier.

Signaltrafik udføres via HTTPS og er ikke så ventetidsfølsom som medietrafikken og er markeret som **Tillad** i URL-adressen/IP-dataene og kan derfor sikkert dirigeres gennem VPN-klienten, hvis det er nødvendigt.

>[!NOTE]
>Microsoft Edge **96 og nyere** understøtter også OPDELT VPN-tunnelføring for peer-to-peer-trafik. Det betyder, at kunder f.eks. kan få fordel af VPN-opdelt tunnelføring for Teams webklienter på Edge. Kunder, der ønsker at konfigurere det til websteder, der kører på Edge, kan opnå det ved at tage det ekstra trin med at deaktivere Edge [WebRtcRespectOsRoutingTableEnabled-politikken](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Sikkerhed

Et almindeligt argument for at undgå opdelte tunneler er, at det er mindre sikkert at gøre det, dvs. al trafik, der ikke går gennem VPN-tunnellen, vil ikke drage fordel af det krypteringsskema, der anvendes på VPN-tunnellen, og er derfor mindre sikker.

Det primære modargument til dette er, at medietrafik allerede er krypteret via _SRTP (Secure Real-Time Transport Protocol),_ en profil for Real-Time Transport Protocol (RTP), der sikrer fortrolighed, godkendelse og genafspilning af angrebsbeskyttelse til RTP-trafik. SRTP selv er afhængig af en tilfældigt genereret sessionsnøgle, som udveksles via den sikrede TLS-signalkanal. Dette behandles udførligt i [denne sikkerhedsvejledning](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), men det primære afsnit af interesse er mediekryptering.

Medietrafik krypteres ved hjælp af SRTP, som bruger en sessionsnøgle, der genereres af en sikker generator af tilfældige tal og udveksles ved hjælp af den signalerende TLS-kanal. Derudover krypteres medier, der flyder i begge retninger mellem mediationsserveren og dens interne næste hop, også ved hjælp af SRTP.

Skype for Business Online genererer brugernavn/adgangskoder for at sikre adgang til medierelæer via _Traversal Using Relays omkring NAT (TURN)_. Medierelæer udveksler brugernavnet/adgangskoden via en TLS-sikret SIP-kanal. Det er værd at bemærke, at selvom en VPN-tunnel kan bruges til at forbinde klienten til virksomhedens netværk, skal trafikken stadig flyde i sin SRTP-formular, når den forlader virksomhedens netværk for at nå tjenesten.

Du kan finde oplysninger om, hvordan Teams afhjælper almindelige sikkerhedsbekymringer, f.eks. stemme- eller _Session Traversal Utilities for NAT-forstærkerangreb (STUN),_ i [5.1 Sikkerhedsovervejelser for implementere](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

Du kan også læse om moderne sikkerhedskontroller i fjernarbejdsscenarier på [Alternative måder for sikkerhedsteknikere og it-medarbejdere at opnå moderne sikkerhedskontroller i nutidens unikke fjernarbejdsscenarier (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Test

Når politikken er på plads, skal du bekræfte, at den fungerer som forventet. Der er flere måder at teste stien på, som er indstillet korrekt til at bruge den lokale internetforbindelse:

- Kør [Microsoft 365 forbindelsestest](https://aka.ms/netonboard), der kører forbindelsestest for dig, herunder sporingsruter som ovenfor. Vi føjer også VPN-test til dette værktøj, som også bør give yderligere indsigt.

- En enkel **tracert** til et slutpunkt inden for området for den opdelte tunnel skal vise den sti, der er taget, f.eks.:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Du bør derefter se en sti via den lokale internetudbyder til dette slutpunkt, der skal oversættes til en IP-adresse i de Teams områder, vi har konfigureret til opdelt tunnelføring.

- Tag en netværksregistrering ved hjælp af et værktøj som Wireshark. Filtrer på UDP under et kald, og du bør se, at trafikken flyder til en IP-adresse i området Teams **Optimer**. Hvis VPN-tunnelen bruges til denne trafik, vil medietrafikken ikke være synlig i sporingen.

## <a name="additional-support-logs"></a>Yderligere supportlogge

Hvis du har brug for yderligere data til fejlfinding eller anmoder om hjælp fra Microsoft Support, bør du kunne fremskynde søgning efter en løsning ved at indhente følgende oplysninger. Microsoft support **tss Windows CMD-baserede universelle TroubleShooting Script toolset** kan hjælpe dig med at indsamle de relevante logge på en enkel måde. Du kan finde værktøjet og brugsvejledningen på <https://aka.ms/TssTools>.

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementering af VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Almindelige scenarier med opdelt VPN-tunnelføring for Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimering af ydeevnen for kinabrugere](microsoft-365-networking-china.md)

[principper for Microsoft 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md)

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevne](network-planning-and-performance.md)

[Alternative måder for sikkerhedsteknikere og it-medarbejdere at opnå moderne sikkerhedskontroller i nutidens unikke fjernarbejdsscenarier (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: Brug af Windows 10 VPN-profiler til at tillade automatisk on-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke tilsluttet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
