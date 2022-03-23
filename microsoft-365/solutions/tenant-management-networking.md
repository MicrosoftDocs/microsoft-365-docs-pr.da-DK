---
title: Trin 2. Optimalt netværk for dine Microsoft 365 for virksomhedslejere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Optimer netværksadgangen til dine Microsoft 365 lejere.
ms.openlocfilehash: 2ee0f5cd784112909cbba465b94031ac2429963f
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63590492"
---
# <a name="step-2-optimal-networking-for-your-microsoft-365-for-enterprise-tenants"></a>Trin 2. Optimalt netværk for dine Microsoft 365 for virksomhedslejere

Microsoft 365 til virksomheder omfatter produktivitetsapps i skyen som Teams og Exchange Online og Microsoft Intune samt mange identitets- og sikkerhedstjenester Microsoft Azure. Alle disse skybaserede tjenester er afhængige af sikkerhed, ydeevne og pålidelighed af forbindelser fra klientenheder på dit lokale netværk eller en hvilken som helst placering på internettet. 

Hvis du vil optimere netværksadgang for din lejer, skal du:

- Optimer stien mellem dine lokale brugere og den nærmeste placering til Microsoft Global Network.
- Optimer adgangen til Microsoft Global Network for dine eksterne brugere, der bruger en VPN-løsning med fjernadgang.
- Brug netværksservere Insights at designe netværksperimeteren for dine kontorplaceringer.
- Optimer adgangen til bestemte aktiver, der hostes SharePoint websteder med Office 365 CDN.
- Konfigurer proxy- og netværkskantenheder til at tilsidesætte behandling for Microsoft 365, der er tillid til, med listen over slutpunkter, og automatiser opdateringen af listen, når der foretages ændringer.

## <a name="enterprise-on-premises-workers"></a>Medarbejdere i det lokale miljø

For virksomhedsnetværk skal du optimere slutbrugeroplevelsen ved at give den højest effektive netværksadgang mellem klienter og de nærmeste Microsoft 365 slutpunkter. Kvaliteten af slutbrugeroplevelsen er direkte relateret til ydeevnen og svarigheden i det program, brugeren bruger. Eksempelvis er Microsoft Teams af lav ventetid, så brugernes telefonopkald, telefonmøder og delte skærmsamarbejder er ustabile.

Det primære mål i netværksdesignet bør være at minimere ventetiden ved at reducere tiden for returkørslen (RTT) fra klientenheder til Microsoft Global Network, Microsofts offentlige netværkssten, der indbyrdes forbinder alle Microsofts datacentre med lav latenstid, indgangspunkter til skybaserede programmer med høj tilgængelighed, kaldet front døre, spredt over hele verden.

Her er et eksempel på et traditionelt virksomhedsnetværk.

![Et traditionelt virksomhedsnetværk med central adgang til internettet.](../media/tenant-management-overview/tenant-management-networking-traditional.png)

I denne illustration opretter afdelingskontorer forbindelse til et centralt kontor via wide area network-enheder (WAN) og en WAN-basis. Internetadgang er via en sikkerheds- eller proxyenhed i netværkskanten på det centrale kontor og en internetudbyder(serviceudbyder). På internettet har Microsoft Global Network en række forside døre i områder over hele verden. Organisationer kan også bruge mellemliggende placeringer til yderligere pakkebehandling og sikkerhed for trafik. En organisations lejer Microsoft 365 placeret i Microsoft Global Network.

Problemerne med denne konfiguration for Microsoft 365 i skyen er:

- For brugere i afdelingskontorer sendes trafik til ikke-lokale for døre, hvilket øger ventetiden.
- Når du sender trafik til mellemliggende placeringer, oprettes der netværks hairpins, der udfører duplikerede pakkebehandlinger på pålidelig trafik, hvilket øger ventetiden.
- Network edge-enheder udfører unødig og duplikeret pakkebehandling på pålidelig trafik, hvilket øger ventetiden.

Optimering Microsoft 365 netværkets ydeevne behøver ikke at være kompliceret. Du kan opnå den bedst mulige ydeevne ved at følge nogle få vigtige principper:

- Identificer Microsoft 365 netværkstrafik, som er pålidelig trafik, der er beregnet til Microsofts skytjenester.
- Tillad lokal afdelings udgangspunkt for Microsoft 365 til internettet fra hver placering, hvor brugerne opretter forbindelse til Microsoft 365.
- Undgå netværks hairpins.
- Tillad Microsoft 365 trafik til at tilsidesætte proxyer og pakkeinspektionsenheder.

Hvis du implementerer disse principper, får du et virksomhedsnetværk, der er optimeret til Microsoft 365.

![Et virksomhedsnetværk, der er optimeret til Microsoft 365.](../media/tenant-management-overview/tenant-management-networking-optimized.png)

I denne illustration har afdelingskontorer deres egen internetforbindelse via en software defineret WAN-enhed (SDWAN), som sender pålidelig Microsoft 365-trafik til den regionale nærmeste frontport. På det centrale kontor bruges pålidelig Microsoft 365 trafik ikke længere sikkerhed eller proxyenhed, og mellemliggende enheder bruges ikke længere.

Her kan du se, hvordan den optimerede konfiguration løser problemerne med ventetid for et traditionelt virksomhedsnetværk:

- Pålidelig Microsoft 365-trafik springer WAN-basisn over og sendes til lokale forside døre til alle kontorer, hvilket reducerer ventetiden.
- Netværks hairpins, der udfører duplikerede pakkebehandlinger, ignoreres for Microsoft 365 pålidelig trafik, hvilket reducerer ventetiden.
- Netværkkantenheder, der udfører unødig og duplikeret pakkebehandling, ignoreres for at Microsoft 365 pålidelig trafik, hvilket reducerer ventetiden.

Du kan finde flere oplysninger [Microsoft 365 oversigt over netværksforbindelsen](../enterprise/microsoft-365-networking-overview.md).

## <a name="remote-workers"></a>Fjernarbejdere

Hvis dine eksterne medarbejdere bruger en traditionel VPN-klient til at få fjernadgang til dit organisationsnetværk, skal du bekræfte, at VPN-klienten har opdelt understøttelse af netværksforbindelse. Uden opdelte netværksforbindelser bliver al din fjerntrafik sendt på tværs af VPN-forbindelsen, hvor den skal videresendes til din organisations edgeenheder, behandles og derefter sendes på internettet. Her er et eksempel.

![Netværkstrafik fra VPN-klienter uden netværksforbindelse.](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-before-tunneling.png)

I denne illustration skal Microsoft 365-trafik tage en indirekte rute gennem din organisation, som kan videresendes til en Microsoft Global Network-frontport langt væk fra VPN-klientens fysiske placering. Denne indirekte sti føjer ventetid til netværkstrafikken og reducerer den overordnede ydeevne. 

Med opdelte netværksnetværk kan du konfigurere din VPN-klient til at udelukke bestemte typer trafik fra at blive sendt via VPN-forbindelsen til organisationens netværk.

Hvis du vil optimere adgangen Microsoft 365 skyressourcer, skal du konfigurere dine opdelte VPN-klienter til at udelukke trafik til  kategorien Optimer Microsoft 365 slutpunkter via VPN-forbindelsen. Du kan finde flere oplysninger [Office 365 kategorier for slutpunkter](../enterprise/microsoft-365-network-connectivity-principles.md#new-office-365-endpoint-categories) [og listerne](../enterprise/microsoft-365-vpn-implement-split-tunnel.md#implement-vpn-split-tunneling) over slutpunkter i kategorien Optimer til opdelte hierarkier.

Her er det resulterende trafikflow til opdelt inddelning, hvor det meste af trafik til Microsoft 365 apps tilsidesætter VPN-forbindelsen.

![Netværkstrafik fra VPN-klienter med indføring.](../media/empower-people-to-work-remotely-remote-access/empower-people-to-work-remotely-remote-access-after-tunneling.png)

I denne illustration sender og modtager VPN-klienten Microsoft 365 skytjenestetrafik direkte via internettet og til den nærmeste frontport til Microsoft Global Network.

Du kan finde flere oplysninger og vejledning i [Optimer Office 365 forbindelse for eksterne brugere, der bruger VPN-opdeling af netværksforbindelse](../enterprise/microsoft-365-vpn-split-tunnel.md).

## <a name="using-network-insights-preview"></a>Brug af Insights (forhåndsvisning)

Netværksindsigt er målepunkter for ydeevnen, der indsamles fra din Microsoft 365 lejer, som hjælper dig med at designe netværksperimetere for dine kontorplaceringer. Hvert indsigt giver liveoplysninger om ydeevneegenskaber for et bestemt problem for hver geografisk placering, hvor lokale brugere har adgang til din lejer.

Der er to netværksindsigt på lejerniveau, der kan vises for lejeren:

- [Exchange forbindelser, der er påvirket af forbindelsesproblemer](../enterprise/office-365-network-mac-perf-insights.md#exchange-sampled-connections-affected-by-connectivity-issues)
- [SharePoint forbindelser, der er påvirket af forbindelsesproblemer](../enterprise/office-365-network-mac-perf-insights.md#sharepoint-sampled-connections-affected-by-connectivity-issues)

Disse er de specifikke netværksindsigter for hver placering på kontoret:

- [Backhauled network udgangspunktress](../enterprise/office-365-network-mac-perf-insights.md#backhauled-network-egress)
- [Bedre ydeevne registreret for kunder i nærheden af dig](../enterprise/office-365-network-mac-perf-insights.md#better-performance-detected-for-customers-near-you)
- [Brug af en ikke-optimal Exchange Online en serviceforsideport](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-exchange-online-service-front-door)
- [Brug af en ikke-optimal SharePoint en online service front dør](../enterprise/office-365-network-mac-perf-insights.md#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [Lav downloadhastighed SharePoint en forsideport](../enterprise/office-365-network-mac-perf-insights.md#low-download-speed-from-sharepoint-front-door)
- [Brugerens optimale netværks udgangspunkt i Kina](../enterprise/office-365-network-mac-perf-insights.md#china-user-optimal-network-egress)

> [!IMPORTANT]
> Netværksindsigt, anbefalinger om ydeevne og evalueringer i Microsoft 365 Administration Center er i øjeblikket en forhåndsvisningsstatus. Det er kun tilgængeligt for Microsoft 365 lejere, der er tilmeldt preview-programmet til funktioner.

Du kan finde flere oplysninger [Microsoft 365 Network Insights](../enterprise/office-365-network-mac-perf-insights.md).

## <a name="sharepoint-performance-with-the-office-365-cdn"></a>SharePoint ydeevne med Office 365 CDN

Med en skybaseret Content Delivery Network (CDN) kan du reducere indlæsningstiderne, spare båndbredde og hastighedens svartid. En CDN forbedrer ydeevnen ved at cache statiske aktiver, f.eks grafik- eller videofiler, tættere på browserne, der anmoder om dem, hvilket hjælper dig med at sætte fart på overførsler og reducere ventetiden. Du kan bruge den indbyggede Office 365 Content Delivery Network (CDN), der følger med SharePoint i Microsoft 365 E3 og E5, til at hoste statiske aktiver for at give bedre ydeevne for dine SharePoint sider.

The Office 365 CDN består af flere CDN'er, der giver dig mulighed for at hoste statiske aktiver på flere placeringer eller _oprindelser og betjene_ dem fra globale højhastighedsnetværk. Afhængigt af den type indhold, du vil hoste i Office 365 CDN, kan du tilføje offentlige oprindelser, **private** oprindelser eller begge dele.

Når den installeres og konfigureres, overfører Office 365 CDN aktiver fra offentlige og private oprindelser og gør dem tilgængelige for hurtig adgang for brugere, der er placeret på internettet.

![Office 365 CDN installeret for brugere.](../media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN installeret for brugere")

Få mere at vide under [Brug Office 365 CDN med SharePoint Online](../enterprise/use-microsoft-365-cdn-with-spo.md).

## <a name="automated-endpoint-listing"></a>Automatiseret slutpunktspost

Hvis du vil have, at dine lokale klienter, edge-enheder og skybaserede pakkeanalysetjenester springer behandlingen af pålidelig Microsoft 365-trafik over, skal du konfigurere dem med det sæt slutpunkter (IP-adresseintervaller og DNS-navne), der svarer til Microsoft 365-tjenester. Disse slutpunkter kan konfigureres manuelt i firewalls og andre grænsesikkerhedsenheder, PAC-filer til klientcomputere til at tilsidesætte proxyer eller SD-WAN-enheder på afdelingskontorer. Slutpunkterne ændres imidlertid over tid, hvilket kræver løbende manuel vedligeholdelse af slutpunktslisterne på disse placeringer.

For at automatisere angivelsen og styringen af ændringer for Microsoft 365 slutpunkter i PAC-klientens filer og netværksenheder skal du bruge [Office 365 IP-adresse og URL REST-baseret webtjeneste](../enterprise/microsoft-365-ip-web-service.md). Denne tjeneste hjælper dig med bedre at identificere og Microsoft 365 og netværkstrafik, hvilket gør det nemmere for dig at evaluere, konfigurere og holde dig opdateret med de seneste ændringer.

Du kan bruge PowerShell, Python eller andre sprog til at bestemme ændringerne i slutpunkter over tid og konfigurere PAC-filer og grænsenetværksenheder.

Den grundlæggende proces er:

1. Brug Office 365 IP-adresse og URL-webtjeneste og konfigurationsmekanismen efter eget valg til at konfigurere PAC-filer og netværksenheder med det aktuelle sæt Microsoft 365 slutpunkter.
2. Kør en daglig tilbagevendende begivenhed for at se, om der er ændringer i slutpunkterne, eller brug en meddelelsesmetode.
3. Når ændringerne registreres, skal du genoprette og videredistribuere PAC-filen for klientcomputere og foretage ændringerne på dine netværksenheder.

Du kan finde flere oplysninger [Office 365 IP-adresse og URL-webtjeneste](../enterprise/microsoft-365-ip-web-service.md).

## <a name="results-of-step-2"></a>Resultater af trin 2

For din Microsoft 365 med optimale netværk har du besluttet dig for:

- Sådan optimerer du netværkets ydeevne for lokale brugere ved at føje internetforbindelser til alle afdelingskontorer og fjerne hairpins på netværket.
- Sådan implementerer du automatiseret liste over slutpunkter, der er tillid til, til dine klientbaserede PAC-filer og dine netværksenheder og -tjenester, herunder løbende opdateringer (bedst egnet til virksomhedsnetværk).
- Sådan understøttes fjernmedarbejdernes adgang til lokale ressourcer.
- Sådan bruges Insights
- Sådan installeres Office 365 CDN.

Her er et eksempel på en virksomhedsorganisation og dens lejer med optimale netværk.

![Eksempel på en lejer med optimalt netværk.](../media/tenant-management-overview/tenant-management-tenant-build-step2.png)

[Se en større version af dette billede](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/tenant-management-overview/tenant-management-tenant-build-step2.png)

I denne illustration har lejeren for denne virksomhedsorganisation:

- Lokal internetadgang for hvert afdelingskontor med en SDWAN-enhed, der videresender pålidelig Microsoft 365 til en lokal frontport.
- Ingen hairpins på netværket.
- Central office security and proxy edge devices that forward Microsoft 365 trusted traffic to a local front door.

## <a name="ongoing-maintenance-for-optimal-networking"></a>Løbende vedligeholdelse for optimal netværking

Du kan løbende få brug for at:

- Opdater dine Edge-enheder og installerede PAC-filer for ændringer i slutpunkter, eller bekræft, at din automatiserede proces fungerer korrekt.
- Administrer aktiverne i Office 365 CDN.
- Opdater konfigurationen for opdeling af netværksforbindelse i dine VPN-klienter for ændringer i slutpunkter.

## <a name="next-step"></a>Næste trin

[![Trin 3. Synkroniser dine identiteter, og gennemtving sikre logons.](../media/tenant-management-overview/tenant-management-step-grid-identity.png)](tenant-management-identity.md)

Fortsæt med [identitet](tenant-management-identity.md) for at synkronisere dine lokale konti og grupper, og gennemtving sikre bruger logins.
