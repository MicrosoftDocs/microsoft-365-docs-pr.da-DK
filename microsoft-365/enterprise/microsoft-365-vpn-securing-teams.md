---
title: Sikring Teams medietrafik til VPN-opdelte netværkstrafik
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
description: Sikring Teams medietrafik til VPN-opdelte netværkstrafik
ms.openlocfilehash: 0f16ed8f7f9721a79375f05f7b889bc8aab2d824
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704935"
---
# <a name="securing-teams-media-traffic-for-vpn-split-tunneling"></a>Sikring Teams medietrafik til VPN-opdelte netværkstrafik

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der adresserer Microsoft 365 optimering for eksterne brugere.

>- Du kan få et overblik over, hvordan du bruger VPN-opdelte forbindelser til at optimere Microsoft 365 forbindelse for eksterne brugere, under [Oversigt: VPN-opdelt Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Hvis du vil have detaljeret vejledning til implementering af VPN-opdeling, skal du [se Implementering af VPN-opdeling for at Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdeling af VPN i Almindelige [scenarier for vpnopdelning af Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde oplysninger om, hvordan du konfigurerer Stream og livebegivenheder i VPN-miljøer, under Særlige overvejelser [i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).
>- Du kan finde oplysninger om optimering Microsoft 365 globale lejerydeevne for brugere i Kina under [Microsoft 365 optimering af ydeevnen for Brugere i Kina](microsoft-365-networking-china.md).

Nogle Microsoft Teams administratorer kan kræve detaljerede oplysninger om, hvordan opkaldsflows fungerer i Teams ved hjælp af en opdelt strømningsmodel, og hvordan forbindelserne er sikret.

## <a name="configuration"></a>Konfiguration

For både opkald og møder gælder det, at så længe de nødvendige Optimer IP-undernet til Teams-medier er placeret korrekt i rutetabellen, når Teams kalder funktionen [GetBestRoute](/windows/win32/api/iphlpapi/nf-iphlpapi-getbestroute) for at afgøre, hvilken lokal grænseflade der svarer til den rute, den skal bruge til en bestemt destination, returneres den lokale grænseflade for Microsoft-destinationer i Microsofts IP-blokke ovenfor.

Nogle VPN-klientprogrammer tillader routingmanipulation baseret på URL-adresse. Medietrafik Teams dog ingen URL-adresse knyttet til den, så styring af routing for denne trafik skal udføres ved hjælp af IP-undernet.

I visse scenarier, der ofte ikke er relateret Teams klientkonfigurationen, krydser medietrafik stadig VPN-transport selv med de korrekte ruter på plads. Hvis du støder på dette scenarie, bør det være tilstrækkeligt at bruge en firewallregel til at blokere Teams IP-undernet eller porte fra at bruge VPN.

>[!IMPORTANT]
>For at Teams medietrafik dirigeres via den ønskede metode i alle VPN-scenarier, skal du sikre dig, at brugerne kører Microsoft Teams-klientversion **1.3.00.13565** eller højere. Denne version indeholder forbedringer af, hvordan klienten registrerer tilgængelige netværksstier.

Signalering af trafik udføres via HTTPS og er ikke så følsom som medietrafik og er markeret som Tillad i URL/IP-data og kan derfor sikkert dirigeres gennem VPN-klienten, hvis det ønskes.

>[!NOTE]
>Microsoft Edge **96 og derover** understøtter også VPN-opdeling af peer-to-peer-trafik. Det betyder, at kunderne kan drage fordel af VPN-opdeling af Teams for eksempel webklienter i Edge. Kunder, der vil konfigurere det til websteder, der kører på Microsoft Edge, kan opnå det ved at tage det ekstra trin for aktivering af Politikken Edge [WebRtcRespectOsRoutingTableEnabled](/deployedge/microsoft-edge-policies#webrtcrespectosroutingtableenabled) .

### <a name="security"></a>Sikkerhed

Et almindeligt argument til at undgå opdelte broer er, at det er mindre sikkert at gøre det, dvs. Al trafik, der ikke går gennem VPN-krypteringen, kan ikke drage fordel af den kryptering, der anvendes på VPN-vpn-krypteringen, og den er derfor mindre sikker.

Det vigtigste modargument til dette er, at medietrafik allerede er _krypteret via Secure Real-Time Transport Protocol (SRTP),_ en profil for Real-Time Transport Protocol (RTP), der giver beskyttelse mod fortrolighed, godkendelse og genafspilning af angreb mod RTP-trafik. Selve SRTP afhænger af en tilfældigt genereret sessionsnøgle, der udveksles via den TLS-sikrede signalkanal. Dette er beskrevet meget detaljeret i denne [sikkerhedsvejledning](/skypeforbusiness/optimizing-your-network/security-guide-for-skype-for-business-online), men den primære sektion af interesse er mediekryptering.

Medietrafik krypteres ved hjælp af SRTP, som bruger en sessionsnøgle, der genereres af en sikker, tilfældig talgenerator og udveksles ved hjælp af den signalerende TLS-kanal. Desuden krypteres medieflow i begge retninger mellem Mediation Server og dens interne næste hop også ved hjælp af SRTP.

Skype for Business Online genererer brugernavne/adgangskoder for sikker adgang til medie relays over _Traversal Using Relays around NAT (TURN)_. Medie relays udveksle brugernavn/adgangskode over en TLS-sikret SIP-kanal. Det er værd at bemærke, at selvom en VPN-vpn-forbindelse kan bruges til at forbinde klienten til virksomhedens netværk, så skal trafikken stadig flyde i sin SRTP-form, når den forlader virksomhedens netværk for at få forbindelse til tjenesten.

Oplysninger om, hvordan Teams afhjælper almindelige sikkerhedsproblemer som f.eks. tale eller _Session Traversal Utilities for NAT (STUN)_ amplification-angreb, kan findes i [5.1 Sikkerhedsovervejelser til implementeringere](/openspecs/office_protocols/ms-ice2/69525351-8c68-4864-b8a6-04bfbc87785c).

Du kan også læse om moderne sikkerhedskontrolelementer i scenarier med fjernarbejde på Alternative måder for sikkerhedsmedarbejdere og IT til at opnå moderne sikkerhedskontrolelementer i moderne unikke scenarier med fjernarbejde [(Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/).

### <a name="testing"></a>Test

Når politikken er på plads, skal du bekræfte, at den virker som forventet. Der er flere måder at teste stien på er korrekt indstillet til at bruge den lokale internetforbindelse:

- Kør den [Microsoft 365 forbindelsestest,](https://aka.ms/netonboard) der kører forbindelsestests for dig, herunder sporingsruter som ovenfor. Vi tilføjer også VPN-test til dette værktøj, som også bør give yderligere indsigt.

- En simpel **tracert til** et slutpunkt, som er inden for området for den opdelte revne, skal vise den vej, der er taget, f.eks.:

  ```powershell
  tracert worldaz.tr.teams.microsoft.com
  ```

  Du bør derefter se en sti via den lokale internetudbyder til dette slutpunkt, der skal løses til en IP-adresse i de Teams områder, vi har konfigureret til opdeling af netværksforbindelse.

- Tag en netværksregistrering ved hjælp af et værktøj som f.eks. Wireshark. Filtrer på UDP under et opkald, og du bør få vist trafik, der flyder til en IP i Teams **Optimer**. Hvis VPN-vpn-vpn bruges til denne trafik, vil medietrafikken ikke være synlig i sporingen.

## <a name="additional-support-logs"></a>Yderligere supportlogfiler

Hvis du har brug for yderligere data til fejlfinding, eller du anmoder om hjælp fra Microsoft-support, skal du få følgende oplysninger gøre det muligt at fremskynde find en løsning. Microsoft supportS **TSS-Windows CMD-baserede universelle problemfejlfinding af scriptværktøjeret** kan hjælpe dig med at indsamle de relevante logfiler på en enkel måde. Værktøjet og instruktionerne om brug kan findes på <https://aka.ms/TssTools>.

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdeling af Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementering af VPN-opdeling af Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Almindelige scenarier for opdeling af VPN-Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 optimering af ydeevnen for Kinas brugere](microsoft-365-networking-china.md)

[Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

[Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier for fjernarbejde (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: brug Windows 10 VPN-profiler til at tillade automatiske til-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
