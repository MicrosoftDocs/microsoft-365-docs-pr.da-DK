---
title: Microsoft 365 global optimering af lejerydeevnen for kinesiske brugere
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
description: Denne artikel indeholder en vejledning i optimering af netværksydeevnen for Kina-brugere af globale Microsoft 365 lejere.
ms.openlocfilehash: f7e4e69277a252fd1af52559d3bc4360fd3cfd51
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65637863"
---
# <a name="microsoft-365-global-tenant-performance-optimization-for-china-users"></a>Microsoft 365 global optimering af lejerydeevnen for kinesiske brugere

> [!IMPORTANT]
> Denne vejledning er specifik for brugsscenarier, hvor **virksomheds-Microsoft 365-brugere, der er placeret i Kina**, opretter forbindelse til en **global Microsoft 365 lejer**. Denne vejledning gælder **ikke** for lejere i Office 365, der drives af 21Vianet.

>[!NOTE]
>Denne artikel er en del af et sæt artikler, der omhandler Microsoft 365 optimering for fjernbrugere.

>- Hvis du vil have en oversigt over, hvordan du bruger VPN-opdelt tunnelføring til at optimere Microsoft 365 forbindelse til fjernbrugere, skal du se [Oversigt: VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-split-tunnel.md).
>- Du kan finde en detaljeret vejledning i implementering af opdelt VPN-tunnelføring under [Implementering af VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md).
>- Du kan finde en detaljeret liste over scenarier med opdelt VPN-tunnelføring under [Almindelige scenarier med opdelt VPN-tunnelføring for Microsoft 365](microsoft-365-vpn-common-scenarios.md).
>- Du kan finde vejledning i, hvordan du sikrer Teams medietrafik i VPN-opdelte tunnelmiljøer, under [Sikring af Teams medietrafik til VPN-opdelt tunnelføring](microsoft-365-vpn-securing-teams.md).
>- Du kan få mere at vide om, hvordan du konfigurerer Stream- og livebegivenheder i VPN-miljøer, under [Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md).

For virksomheder med globale Microsoft 365 lejere og en virksomheds tilstedeværelse i Kina kan Microsoft 365 kundeydeevne for kinabaserede brugere være kompliceret af faktorer, der er unikke for Kina Telcos internetarkitektur.

Kina ISP'er har regulerede offshore forbindelser til det globale offentlige internet, der går gennem perimeterenheder, der er tilbøjelige til at høje niveauer af grænseoverskridende netværksoverbelastning. Denne overbelastning skaber pakketab og ventetid for al internettrafik, der kommer ind og ud af Kina.

![Microsoft 365 trafik – ikke optimeret.](../media/O365-networking/China-O365-unoptimized.png)

Pakketab og ventetid er skadelige for ydeevnen af netværkstjenester, især tjenester, der kræver store dataudvekslinger (f.eks. store filoverførsler) eller kræver ydeevne næsten i realtid (lyd- og videoprogrammer).

Målet med dette emne er at levere bedste praksis for at mindske den indvirkning, som den grænseoverskridende trafikpropper i Kina har på Microsoft 365 tjenester. Dette emne omhandler ikke andre almindelige problemer med ydeevnen for sidste kilometer, f.eks. problemer med høj pakkeventetid på grund af kompleks routing i kinesiske luftfartsselskaber.

## <a name="corporate-network-best-practices"></a>Bedste praksis for virksomhedsnetværk

Mange virksomheder med globale Microsoft 365 lejere og brugere i Kina har implementeret private netværk, der transporterer virksomhedsnetværkstrafik mellem kinesiske kontorplaceringer og offshore-placeringer over hele verden. Disse virksomheder kan udnytte denne netværksinfrastruktur for at undgå grænseoverskridende netværksoverbelastning og optimere deres Microsoft 365 servicepræstation i Kina.

> [!IMPORTANT]
> Som med alle private WAN-implementeringer bør du altid se lovmæssige krav til dit land og/eller område for at sikre, at din netværkskonfiguration overholder angivne standarder.

Som et første skridt er det afgørende, at du følger vores benchmarknetværksvejledning til [netværksplanlægning og justering af ydeevnen for Microsoft 365](./network-planning-and-performance.md). Det primære mål bør være at undgå at få adgang til globale Microsoft 365 tjenester fra internettet i Kina, hvis det er muligt.

- Udnyt dit eksisterende private netværk til at transportere Microsoft 365 netværkstrafik mellem kinas kontornetværk og offshore placeringer, der udgående på det offentlige internet uden for Kina. Næsten enhver placering uden for Kina vil give en klar fordel. Netværksadministratorer kan yderligere optimere ved at gå ud i områder med lav ventetid, der er forbundet med [Microsofts globale netværk](/azure/networking/microsoft-global-network). Hongkong, Singapore, Japan og Sydkorea er eksempler.
- Konfigurer brugerenheder for at få adgang til virksomhedens netværk via en VPN-forbindelse for at tillade, at Microsoft 365 trafik overfører virksomhedens private offshore-link. Sørg for, at VPN-klienter enten ikke er konfigureret til at bruge opdelt tunnelføring, eller at brugerenheder er konfigureret til at ignorere opdelt tunnelføring for Microsoft 365 trafik. Du kan finde flere oplysninger om optimering af VPN-forbindelsen til Teams og medietrafik i realtid i [dette afsnit](#optimizing-microsoft-teams-meetings-network-performance-for-users-in-china).
- Konfigurer dit netværk til at dirigere al Microsoft 365 trafik over dit private offshore-link. Hvis du skal minimere mængden af trafik på dit private link, kan du vælge kun at distribuere slutpunkter i kategorien **Optimer** og tillade anmodninger om at tillade, at slutpunkter af typen **Allow** og **Default** overføres til internettet. Dette vil forbedre ydeevnen og minimere båndbreddeforbruget ved at begrænse optimeret trafik til kritiske tjenester, der er mest følsomme over for høj ventetid og pakketab.
- Hvis det er muligt, skal du bruge UDP i stedet for TCP til direkte mediestreamingtrafik, f.eks. til Teams. UDP giver bedre ydeevne for streaming af livemedier end TCP.

Du kan finde oplysninger om, hvordan du selektivt distribuerer Microsoft 365 trafik, under [Administration af Office 365 slutpunkter](managing-office-365-endpoints.md). Du kan finde en liste over alle globale Office 365 URL-adresser og IP-adresser [under Office 365 URL-adresser og IP-adresseområder](urls-and-ip-address-ranges.md).

![Microsoft 365 trafik – optimeret.](../media/O365-networking/China-O365-optimized.png)

## <a name="user-best-practices"></a>Bedste praksis for brugere

Brugere i Kina, der opretter forbindelse til globale Microsoft 365 lejere fra fjernplaceringer, f.eks. hjem, kaffebarer, hoteller og forgreningskontorer uden forbindelse til virksomhedsnetværk, kan opleve dårlig netværksydeevne, fordi trafikken mellem deres enheder og Microsoft 365 skal overføre Kinas overbelastede grænseoverskridende netværkskredsløb.

Hvis grænseoverskridende private netværk og/eller VPN-adgang til virksomhedens netværk ikke er en mulighed, kan problemer med ydeevnen pr. bruger stadig afhjælpes ved at oplære dine Kina-baserede brugere til at følge disse bedste praksisser.

- Anvend omfattende Office klienter, der understøtter cachelagring (f.eks. Outlook, Teams, OneDrive osv.), og undgå webbaserede klienter. Office funktioner til cachelagring og offlineadgang kan reducere konsekvenserne af overbelastning og ventetid for netværk dramatisk.
- Hvis din Microsoft 365 lejer er konfigureret med funktionen _Lydmøde_, kan Teams brugere deltage i møder via det offentlige telefonnetværk (PSTN). Du kan få flere oplysninger [under Lydmøde i Office 365](/microsoftteams/audio-conferencing-in-office-365).
- Hvis brugerne oplever problemer med netværkets ydeevne, skal de rapportere til deres it-afdeling med henblik på fejlfinding og eskalere til Microsoft-support, hvis der er mistanke om problemer med Microsoft 365 tjenester. Det er ikke alle problemer, der skyldes netværksydeevnen på tværs af grænserne.

## <a name="optimizing-microsoft-teams-meetings-network-performance-for-users-in-china"></a>Optimering af netværksydeevnen for Microsoft Teams møder for brugere i Kina

For organisationer med globale Microsoft 365 lejere og tilstedeværelse i Kina kan Microsoft 365 kundeydeevne for kinabaserede brugere være kompliceret af faktorer, der er unikke for Internetarkitekturen i Kina. Mange virksomheder og skoler har rapporteret gode resultater ved at følge denne vejledning. Omfanget er dog begrænset til brugernetværksplaceringer, der er under kontrol af konfigurationen af it-netværk, f.eks. kontorplaceringer eller hjemme-/mobilslutpunkter med VPN-forbindelse. Microsoft Teams opkald og møder bruges ofte fra eksterne placeringer, f.eks. hjemmekontorer, mobile placeringer, på vejene og kaffebarer. Da opkald og møder er afhængige af medietrafik i realtid, er disse Teams-oplevelser særligt følsomme over for overbelastning af netværket.

Microsoft har derfor indgået partnerskab med udbydere af telekommunikation om at transportere Teams og Skype for Business Online-medietrafik i realtid ved hjælp af en netværkssti af højere kvalitet mellem indenlandske og offentlige internetforbindelser i Kina og Teams- og Skype-tjenester i Microsoft 365 globale cloud. Denne funktion har resulteret i mere end ti gange bedre pakketab og andre vigtige målepunkter, der påvirker din brugers oplevelse.

>[!IMPORTANT]
>I øjeblikket omhandler disse forbedringer ikke deltagelse i Microsoft Live Events-møder, f.eks. store udsendelses- eller "rådhusmøder" ved hjælp af Teams eller Microsoft Stream. Netværksforbedringerne vil være til gavn for brugere, der præsenterer eller producerer et Live Events-møde, fordi denne oplevelse fungerer som et regelmæssigt Teams møde for producenten eller præsentationsværten.

### <a name="organization-network-best-practices-for-teams-meetings"></a>Bedste praksis for organisationsnetværk i forbindelse med Teams møder

Du skal overveje, hvordan du kan udnytte disse netværksforbedringer, da den tidligere vejledning om at overveje en privat netværksudvidelse for at undgå grænseoverskridende netværksoverbelastning. Der er to generelle indstillinger for organisationskontornetværk:

1. Gør intet nyt. Fortsæt med at følge den tidligere vejledning om omfartsvejen til det private netværk for at undgå overbelastning på tværs af grænserne. Teams medietrafik i realtid vil udnytte denne konfiguration som før.
2. Implementer et opdelt/hybridt mønster.
   - Brug den tidligere vejledning til al trafik, der er markeret til optimering, undtagen Teams møder og opkald til medietrafik i realtid.
   - Distribuer Teams møde og opkald til medietrafik i realtid over det offentlige internet. Se følgende oplysninger for at få oplysninger om, hvordan du identificerer medienetværkstrafik i realtid.

Hvis du sender Teams medielyd- og videotrafik i realtid via det offentlige internet, som bruger forbindelsesmulighed af højere kvalitet, kan det medføre betydelige omkostningsbesparelser, fordi det er gratis i forhold til betaling at sende denne trafik via et privat netværk. Der kan være lignende yderligere fordele, hvis brugerne også bruger SDWAN- eller VPN-klienter. Nogle organisationer foretrækker måske også at få mere af deres data til at gennemgå offentlige internetforbindelser som en generel praksis.

De samme indstillinger kan gælde for SDWAN- eller VPN-konfigurationer. En bruger bruger f.eks. et SDWAN eller EN VPN til at dirigere Microsoft 365 trafik til virksomhedens netværk og derefter udnytte den private udvidelse af netværket for at undgå grænseoverskridende overbelastning. Brugerens SDWAN eller VPN kan nu konfigureres til at udelade Teams møde og kalde trafik i realtid fra VPN-routing. Denne VPN-konfiguration kaldes opdelt tunnelføring. Se [VPN-opdelt tunnelføring for at få Office 365](/microsoft-365/enterprise/microsoft-365-vpn-implement-split-tunnel) for at få flere oplysninger.

Du kan også fortsætte med at bruge dit SDWAN eller VPN til al Microsoft 365 trafik, herunder til Microsoft Teams trafik i realtid. Microsoft har ingen anbefalinger til brugen af SDWAN- eller VPN-løsninger.

### <a name="home-mobile-and-user-network-best-practices-for-teams-meetings"></a>Bedste fremgangsmåder for hjemmenetværk, mobilnetværk og brugernetværk i forbindelse med Teams møder

Brugere i Kina kan drage fordel af disse forbedringer blot ved at oprette forbindelse til den offentlige internettjeneste i Kina med en fastnet- eller mobilforbindelse. Teams medielyd- og videotrafik i realtid på det offentlige internet drager direkte fordel af forbedret forbindelse og kvalitet.

Data fra andre Microsoft 365 tjenester – og anden trafik i Teams, f.eks. chat eller filer – vil dog ikke drage direkte fordel af disse forbedringer. Brugere uden for organisationsnetværket kan stadig opleve dårlig netværksydeevne for denne trafik. Som beskrevet i denne artikel kan du afhjælpe disse effekter ved hjælp af en VPN eller SDWAN. Du kan også få dine brugere til at bruge omfattende skrivebordsklienter via webklienter, som understøtter cachelagring i appen for at afhjælpe netværksproblemer.

### <a name="identifying-teams-real-time-media-network-traffic"></a>Identificering Teams medienetværkstrafik i realtid

Hvis du vil konfigurere en netværksenhed eller en VPN/SDWAN-konfiguration, skal du kun udelukke den Teams medielyd- og videotrafik i realtid. Trafikoplysningerne kan findes for ID 11 på den officielle liste over [Office 365 URL-adresser og IP-adresseintervaller](urls-and-ip-address-ranges.md#skype-for-business-online-and-microsoft-teams). Alle andre netværkskonfigurationer skal forblive, som de er.

Microsoft arbejder hele tiden på at forbedre den Microsoft 365 brugeroplevelse og ydeevnen for klienter i det bredest mulige udvalg af netværksarkitekturer og -egenskaber. Besøg [Office 365 Netværk Tech Community](https://techcommunity.microsoft.com/t5/office-365-networking/bd-p/Office365Networking) for at starte eller deltage i en samtale, finde ressourcer og indsende funktionsanmodninger og -forslag

## <a name="related-articles"></a>Relaterede artikler

[Oversigt: VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-split-tunnel.md)

[Implementering af VPN-opdelt tunnelføring for Microsoft 365](microsoft-365-vpn-implement-split-tunnel.md)

[Almindelige scenarier med opdelt VPN-tunnelføring for Microsoft 365](microsoft-365-vpn-common-scenarios.md)

[Sikring af Teams-medietrafik til VPN-opdelt tunnelføring](microsoft-365-vpn-securing-teams.md)

[Særlige overvejelser i forbindelse med Stream og livebegivenheder i VPN-miljøer](microsoft-365-vpn-stream-and-live-events.md)

[principper for Microsoft 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md)

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)

[Microsoft 365 netværk og justering af ydeevne](network-planning-and-performance.md)

[Alternative måder for sikkerhedsteknikere og it-medarbejdere at opnå moderne sikkerhedskontroller i nutidens unikke fjernarbejdsscenarier (Microsoft Security Team-blog)](https://www.microsoft.com/security/blog/2020/03/26/alternative-security-professionals-it-achieve-modern-security-controls-todays-unique-remote-work-scenarios/)

[Forbedring af VPN-ydeevnen hos Microsoft: Brug af Windows 10 VPN-profiler til at tillade automatisk on-forbindelser](https://www.microsoft.com/itshowcase/enhancing-remote-access-in-windows-10-with-an-automatic-vpn-profile)

[Kører på VPN: Sådan holder Microsoft sin eksterne arbejdsstyrke tilsluttet](https://www.microsoft.com/itshowcase/blog/running-on-vpn-how-microsoft-is-keeping-its-remote-workforce-connected/?elevate-lv)

[Microsofts globale netværk](/azure/networking/microsoft-global-network)
