---
title: Microsoft 365 global lejers ydeevneoptimering for Kina-brugere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 3/3/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- remotework
search.appverid: MET150
f1.keywords:
- NOCSH
description: Denne artikel indeholder vejledning til optimering af netværksydeevnen for Kinas brugere af Microsoft 365 lejere.
ms.openlocfilehash: 6c99245d523048d30124fc8f8b0c01d7c2004327
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601572"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 global lejers ydeevneoptimering for Kina-brugere

> [!IMPORTANT]
> Denne vejledning er specifik for brugsscenarier, hvor **virksomhedsbrugere Microsoft 365** i Kina opretter forbindelse til **en global Microsoft 365 lejer**. Denne vejledning gælder **ikke** for lejere i Office 365 drevet af 21Vianet.

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der adresserer Microsoft 365 optimering for eksterne brugere.

>- Du kan få et overblik over, hvordan du bruger VPN-opdelte forbindelser til at optimere Microsoft 365 forbindelse for eksterne brugere, under [Oversigt: VPN-opdelt Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Hvis du vil have detaljeret vejledning til implementering af VPN-opdeling, skal du [se Implementering af VPN-opdeling for at Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdeling af VPN i Almindelige [scenarier for vpnopdelning af Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde en vejledning til sikring Teams medietrafik i VPN-opdelte netværksmiljøer under Sikring [Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md).
>- Du kan finde oplysninger om, hvordan du konfigurerer Stream og livebegivenheder i VPN-miljøer, under Særlige overvejelser [i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).

For virksomheder med globale Microsoft 365-lejere og virksomhedens tilstedeværelse i Kina kan Microsoft 365-klientydeevnen for Kina-baserede brugere være kompliceret af faktorer, der er unikke for Kina Telcos internetarkitektur.

Kinas internetudbydere har regulerede netværksforbindelser til det globale offentlige internet, der går gennem perimeterenheder, der er udsat for høje niveauer af overbelastning af netværk på tværs af grænser. Denne overbelastning medfører pakketab og ventetid for al internettrafik, der går ind og ud af Kina.

![Microsoft 365 trafik – ikke-animeret.](../media/O365-networking/China-O365-unoptimized.png)

Pakketab og ventetid er negativ i forhold til ydeevnen i netværkstjenester, især tjenester, der kræver store dataudvekslinger (f.eks. store filoverførsler), eller som kræver næsten realtidsydeevne (lyd- og videoprogrammer).

Formålet med dette emne er at levere de bedste fremgangsmåder til at mindske påvirkningen af den overbelastning af netværk, som Kina på tværs af grænser har på Microsoft 365 tjenester. Dette emne adresserer ikke andre almindelige problemer med ydeevnen for de sidste kilometer, f.eks. problemer med høj pakkeventetid på grund af kompleks routing inden for Kina.

## <a name="corporate-network-best-practices"></a>Bedste fremgangsmåder for virksomhedsnetværk

Mange virksomheder med globale Microsoft 365-lejere og brugere i Kina har implementeret private netværk, der udfører virksomhedsnetværkstrafik mellem kontorplaceringer i Kina og placeringer over hele verden. Disse virksomheder kan udnytte denne netværksinfrastruktur for at undgå overbelastning af netværk på tværs af grænser og optimere deres Microsoft 365 tjenesteydeevne i Kina.

> [!IMPORTANT]
> Som med alle andre private WAN-implementeringer skal du altid rådføre dig med lovmæssige krav for dit land og/eller område for at sikre, at din netværkskonfiguration er i overensstemmelse med reglerne.

Som det første trin er det vigtigt, at du følger vores retningsgivende netværksvejledning under Netværksplanlægning og [justering af ydeevnen for Microsoft 365](./network-planning-and-performance.md). Det primære mål bør være at undgå at få adgang til globale Microsoft 365-tjenester fra internettet i Kina, hvis det er muligt.

- Udnyt dit eksisterende private netværk til at Microsoft 365 netværkstrafik mellem kinesiske office-netværk og placeringerne, der går ud på det offentlige internet uden for Kina. Næsten alle placeringer uden for Kina giver en klar fordel. Netværksadministratorer kan yderligere optimere ved hjælp af udgangspunkt i områder med lav ventetid, der er forbundet med [Microsofts globale netværk](/azure/networking/microsoft-global-network). Hongkong, Singapore, Japan og Sydkorea er eksempler.
- Konfigurer brugerenheder for at få adgang til virksomhedens netværk via en VPN-forbindelse for at tillade Microsoft 365 trafik for at undergå virksomhedens netværks private link. Sørg for, at VPN-klienter enten ikke er konfigureret til at bruge opdelt netværksforbindelse, eller at brugerenheder er konfigureret til at ignorere opdelt inddelning for Microsoft 365 trafik. Du kan finde flere oplysninger om optimering af VPN-Teams og medietrafik i [realtid i dette afsnit](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Konfigurer dit netværk til at dirigere al Microsoft 365 på tværs af dit private link. Hvis du skal minimere mængden af trafik på dit private link, kan du vælge kun at distribuere slutpunkter i kategorien Optimer  og tillade anmodninger om at tillade og  Standardslutpunkter at gennemsende internettet. Dette vil forbedre ydeevnen og minimere båndbreddeforbruget ved at begrænse optimeret trafik til kritiske tjenester, der er mest følsomme over for høj latenstid og pakketab.
- Hvis det er muligt, skal du bruge UDP i stedet for TCP til streaming af livemedietrafik, f.eks Teams. UDP tilbyder bedre streaming af livemedieydeevne end TCP.

Du kan finde oplysninger om, hvordan du Microsoft 365 distribuerer trafik selektivt[, under Office 365 slutpunkter](managing-office-365-endpoints.md). Du kan finde en liste over alle Office 365 globale WEBADRESSEr og IP-adresser [Office 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md).

![Microsoft 365 trafik – optimeret.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Bedste fremgangsmåder for brugere

Brugere i Kina, der opretter forbindelse til globale Microsoft 365-lejere fra eksterne placeringer som f.eks. huse, kaffecentre, restauranter og afdelingskontorer uden forbindelse til virksomhedsnetværk, kan opleve en dårlig netværksydeevne, fordi trafikken mellem deres enheder og Microsoft 365 skal transitre Kinas netværkskredsløb over grænsen.

Hvis private netværk på tværs af grænser og/eller VPN-adgang til virksomhedens netværk ikke er en mulighed, kan problemer med ydeevnen pr. bruger stadig afhjælpes ved at uddanne dine Kina-baserede brugere i at følge disse bedste fremgangsmåder.

- Brug omfattende Office-klienter, der understøtter cachelagring (f.eks. Outlook, Teams, OneDrive osv.), og undgå webbaserede klienter. Office klientcaching- og offlineadgangsfunktioner kan reducere effekten af netværksbelastning og -ventetid markant.
- Hvis din Microsoft 365-lejer er konfigureret med funktionen Lydmøder,  kan Teams-brugere deltage i møder via PSTN (Public Switched Telephone Network). Du kan finde flere oplysninger [under Lydmøder i Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Hvis brugerne oplever problemer med netværkets ydeevne, bør de rapportere til deres it-afdeling til fejlfinding og eskalere til Microsoft support, hvis der er mistanke om problemer med Microsoft 365-tjenester. Ikke alle problemer skyldes ydeevnen på tværs af grænser.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Optimere Microsoft Teams af møder for brugere i Kina

For organisationer med globale Microsoft 365-lejere og en tilstedeværelse i Kina kan Microsoft 365-klientydeevnen for Kina-baserede brugere være kompliceret af faktorer, der er unikke for Kinas internetarkitektur. Mange virksomheder og skoler har rapporteret gode resultater ved at følge denne vejledning. Omfanget er dog begrænset til brugeres netværksplaceringer, der er under kontrol af it-netværkskonfigurationen, f.eks. kontorplaceringer eller private/mobile slutpunkter med VPN-forbindelse. Microsoft Teams opkald og møder bruges ofte fra eksterne placeringer, f.eks. kontorer i hjemmet, mobile placeringer, på farten og caféer. Da opkald og møder er afhængige af medietrafik i realtid, er disse Teams særligt følsomme over for overbelastning af netværket.

Derfor har Microsoft indgået partnerskab med telekommunikationsudbydere for at kunne foretage Teams- og Skype for Business Online-medietrafik i realtid ved hjælp af en netværkssti af højere kvalitet, som er netværkssti mellem nationale og offentlige internetforbindelser i Kina og Teams- og Skype-tjenesterne i den globale Microsoft 365-sky. Denne funktion har resulteret i en mere end tidoblet forbedring i pakketab og andre vigtige målepunkter, der påvirker din brugers oplevelse.

>[!IMPORTANT]
>Disse forbedringer har i øjeblikket ikke noget at gøre med deltagelse i Microsoft Live Events-møder, f.eks. møder i stor udsendelses- eller "rådhus", som Teams eller Microsoft Stream. Brugere i Kina skal bruge et privat netværk eller en SDWAN/VPN-løsning for at få vist et møde med Live Events. Netværksforbedringerne vil dog være til fordel for brugere, der præsenterer eller producerer et møde under Live Events, fordi denne oplevelse fungerer som et almindeligt Teams-møde for produceren eller præsentationsværten.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Bedste fremgangsmåder for organisationsnetværk til Teams møder

Du er nødt til at overveje, hvordan du kan udnytte disse forbedringer af netværket, da den tidligere vejledning bør overveje en privat netværksudvidelse for at undgå overbelastning af netværk på tværs af grænser. Der er to generelle indstillinger for organisationens Office-netværk:

1. Gør intet nyt. Fortsæt med at følge den tidligere vejledning om privat netværksovergang for at undgå overbelastning på tværs af grænser. Teams medietrafik i realtid udnytter denne konfiguration som før.
2. Implementere et opdelt/hybridt mønster.
   - Brug den forrige vejledning til al trafik markeret med flag til optimering undtagen Teams og opkald til medietrafik i realtid.
   - Rute Teams møder og ringe til medietrafik i realtid via det offentlige internet. Se følgende oplysninger for at få oplysninger om, hvordan du identificerer medietrafik i realtid.

Afsendelse Teams medielyd- og videotrafik i realtid via det offentlige internet, som bruger en forbindelse af højere kvalitet, kan medføre betydelige omkostningsbesparelser, fordi det er gratis kontra betaling at sende denne trafik via et privat netværk. Der kan være lignende yderligere fordele, hvis brugerne også bruger SDWAN- eller VPN-klienter. Nogle organisationer foretrækker måske også at have flere af deres data gennem offentlige internetforbindelser som en generel praksis.

De samme indstillinger kunne gælde for SDWAN- eller VPN-konfigurationer. En bruger bruger f.eks. et SDWAN eller VPN til at dirigere Microsoft 365-trafik til virksomhedens netværk og derefter udnytte den private udvidelse af dette netværk for at undgå overbelastning på tværs af grænser. Brugerens SDWAN eller VPN kan nu konfigureres til at udelukke Teams møde og kalde realtidstrafik fra VPN-routingen. Denne VPN-konfiguration kaldes opdelt inddelning. Se [VPN-opdeling af vpn-Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) for at få flere oplysninger.

Du kan også fortsætte med at bruge dit SDWAN eller VPN til al Microsoft 365, herunder til Microsoft Teams trafik i realtid. Microsoft har ingen anbefalinger om brug af SDWAN- eller VPN-løsninger.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Bedste fremgangsmåder for hjemme-, mobil- og brugernetværk til Teams møder

Brugere i Kina kan drage fordel af disse forbedringer ved blot at oprette forbindelse til den offentlige internettjeneste i Kina med en fastnet- eller mobilforbindelse. Teams medielyd- og videotrafik i realtid på det offentlige internet direkte fordele fra forbedret forbindelse og kvalitet.

Men data fra andre Microsoft 365-tjenester – og anden trafik i Teams f.eks. chat eller filer – vil ikke drage direkte fordel af disse forbedringer. Brugere uden for organisationsnetværket kan stadig opleve dårlig netværksydeevne for denne trafik. Som nævnt i denne artikel kan du afhjælpe disse effekter ved hjælp af et VPN eller SDWAN. Du kan også få brugerne til at bruge omfattende skrivebordsklienter over webklienter, som understøtter cachelagring i appen for at reducere netværksproblemer.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Identificere Teams medienetværkstrafik i realtid

Når du konfigurerer en netværksenhed eller en VPN/SDWAN-konfiguration, skal du kun Teams medielyd- og videotrafik i realtid. Trafikoplysningerne kan findes til ID 11 på den officielle liste over [Office 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Alle andre netværkskonfigurationer skal forblive, som de er.

Microsoft arbejder kontinuerligt på at forbedre Microsoft 365 brugeroplevelsen og ydeevnen for klienter over det bredeste mulige udvalg af netværksarkitektur og egenskaber. Besøg vores [Office 365 Networking Tech Community for at](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking) starte eller deltage i en samtale, finde ressourcer og sende anmodninger om funktioner og forslag til funktioner

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdeling af Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementering af VPN-opdeling af Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Almindelige scenarier for opdeling af VPN-Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sikring Teams medietrafik til VPN-opdelte netværkstrafik](microsoft-365-vpn-securing-teams.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[Microsoft 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevnen](network-planning-and-performance.md)

[Alternative måder for sikkerhedsmedarbejdere og it-medarbejdere til at opnå moderne sikkerhedskontrolelementer i dagens unikke scenarier for fjernarbejde (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: brug Windows 10 VPN-profiler til at tillade automatiske til-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke forbundet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
