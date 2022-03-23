---
title: Microsoft 365 testværktøj til netværksforbindelse
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 1/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 testværktøj til netværksforbindelse
ms.openlocfilehash: e464b4e651276f8b36f54e91ea0bfc7b7b52d69b
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63590569"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>Microsoft 365 testværktøj til netværksforbindelse

Testværktøjet Microsoft 365 netværksforbindelsen er placeret på <https://connectivity.office.com>. Det er et tillægsværktøj til netværksvurdering og netværksindsigt, der er tilgængelige i Microsoft 365 Administration under **| Forbindelsesmenu**.

> [!IMPORTANT]
> Det er vigtigt at logge på din Microsoft 365-lejer, da alle testrapporter deles med din administrator og uploades til lejeren, mens du er logget på.

> [!div class="mx-imgBorder"]
> ![Forbindelsestestværktøj.](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>Værktøjet til test af netværksforbindelsen understøtter lejere i WW Commercial, men ikke GCC Moderat, GCC High, DoD eller Kina.

Netværksindsigt i Microsoft 365 Administration-center er baseret på almindelige produktmål for din Microsoft 365 lejer, aggregeret hver dag. Til sammenligning køres netværksindsigt Microsoft 365 test af netværksforbindelsen lokalt i værktøjet.

Test i produkter er begrænset, og lokale kørselstests til brugeren indsamler flere data, hvilket giver større indsigt. Netværksindsigt i Microsoft 365 Administration center viser, at der er et netværksproblem på en bestemt kontorplacering. Forbindelsestesten Microsoft 365 hjælp til at identificere den egentlige årsag til problemet og levere en målrettet handling til forbedring af ydeevnen.

Vi anbefaler, at denne indsigt bruges sammen, hvor status for netværkskvalitet kan vurderes for hver enkelt kontorplacering i Microsoft 365 Administration Center, og du kan finde flere oplysninger efter udrulningen af test baseret på Microsoft 365-forbindelsestesten.

## <a name="what-happens-at-each-test-step"></a>Hvad sker der ved hvert testtrin?

### <a name="office-location-identification"></a>Office placeringsidentifikation

Når du klikker på *knappen Kør test* , viser vi den kørende testside og identificerer kontorplaceringen. Du kan skrive din placering efter by, stat og land eller vælge at få det registreret for dig. Hvis du registrerer kontorplaceringen, anmoder værktøjet om bredde- og længdegrader fra webbrowseren og begrænser nøjagtigheden til 300 meter gange 300 meter før brug. Det er ikke nødvendigt at identificere placeringen mere præcist end bygningen for at måle netværkets ydeevne.

### <a name="javascript-tests"></a>JavaScript-test

Efter identifikation af kontorplacering kører vi en TCP-latenstidstest i JavaScript, og vi anmoder om data fra tjenesten om brug og anbefalede Microsoft 365-front door-servere. Når disse test er fuldført, viser vi dem på kortet og under fanen detaljer, hvor de kan ses før næste trin.

### <a name="download-the-advanced-tests-client-application"></a>Download klientprogrammet Advanced Tests

Derefter starter vi download af klientprogrammet Avancerede test. Vi er afhængige af, at brugeren starter klientprogrammet, og de skal også have .NET 6.0 Runtime installeret.

Der er to dele i Microsoft 365 test af netværksforbindelsen: <https://connectivity.office.com> webstedet og et klientprogram, der kan downloades Windows, som kører avancerede test af netværksforbindelsen. De fleste test kræver, at programmet køres. Det udfylder resultaterne på websiden igen, mens det køres.

Når webbrowsertestene er fuldført, bliver du bedt om at hente det avancerede klienttestprogram fra webstedet. Åbn og kør filen, når du bliver bedt om det.

> [!div class="mx-imgBorder"]
> ![Avanceret test-klientprogram.](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Starte klientprogrammet Avancerede test

Når klientprogrammet starter, opdateres websiden for at vise dette resultat. Testdata begynder at blive modtaget på websiden. Siden opdateres, hver gang der modtages nye data, og du kan gennemse dataene, når de modtages.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Avancerede test fuldført og overførsel af testrapport

Når testene er fuldført, viser websiden og klienten til avancerede test begge dette. Hvis brugeren er logget på, uploades testrapporten til kundens lejer.

## <a name="sharing-your-test-report"></a>Dele din testrapport

Testrapporten kræver godkendelse for din Microsoft 365 konto. Din administrator vælger, hvordan du kan dele din testrapport.

### <a name="sharing-your-report-with-your-administrator"></a>Dele rapporten med din administrator

Hvis du er logget på, når der opstår en testrapport, deles rapporten med din administrator.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Deling med dit Microsoft-kontoteam, support eller anden medarbejder

Testrapporter (undtagen personlig identifikation) deles med Microsoft-medarbejdere. Denne deling er som standard aktiveret og kan deaktiveres af administratoren i **| Siden Netværksforbindelse** i Microsoft 365 Administration Center.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-microsoft-365-tenant"></a>Deling med andre brugere, der logger på den samme Microsoft 365 lejer

Du kan vælge brugere at dele din rapport med. At være i stand til at vælge er aktiveret som standard, men det kan deaktiveres af din administrator.

> [!div class="mx-imgBorder"]
> ![Dele et link til dine testresultater med en bruger.](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>Dele med alle ved hjælp af et ReportID-link

Du kan dele din testrapport med alle ved at give adgang til et ReportID-link. Dette link genererer en URL-adresse, som du kan sende til en person, så de kan få testrapporten frem uden at logge på. Denne deling er som standard deaktiveret og skal aktiveres af din administrator.

> [!div class="mx-imgBorder"]
> ![Del et link til dine testresultater.](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Resultater af test af netværksforbindelse

Resultaterne vises i fanerne **Oversigt** **og** Detaljer. Fanen Oversigt viser et kort over den registrerede netværksperimeter og en sammenligning af netværksvurderingen med andre Microsoft 365 kunder i nærheden. Det giver også mulighed for deling af testrapporten. Sådan ser oversigtsresultatvisningen ud:

> [!div class="mx-imgBorder"]
> ![Resultater af testværktøj til netværksforbindelse.](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Her er et eksempel på faneoutput for detaljer. Under fanen detaljer viser vi en grøn cirkelkontrol, hvis resultatet blev sammenlignet. Vi viser et udråbstegn med en rød trekant, hvis resultatet har overskredet en grænseværdi, der angiver et netværksindsigt. I de følgende afsnit beskrives hver af rækkerne med detaljerede resultater under fanen med resultater, og der forklares de grænseværdier, der bruges til netværksindsigt.

> [!div class="mx-imgBorder"]
> ![Eksempel på testresultater for værktøjet Netværksforbindelse.](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Dine placeringsoplysninger

Dette afsnit viser testresultater, der er relateret til din placering.

#### <a name="your-location"></a>Din placering

Brugerens placering registreres i brugerens webbrowser. Den kan også indtastes efter brugerens valg. Det bruges til at identificere netværksafstande til bestemte dele af virksomhedens netværksperimeter. Kun byen fra denne registrering af placering og afstanden til andre netværkspunkter gemmes i rapporten.

Brugerens kontorplacering vises i kortvisningen.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Netværksud udgangspunkt (den placering, hvor dit netværk opretter forbindelse til din internetudbyder)

Vi identificerer netværkets udgangs-IP-adresse på serversiden. Placeringsdatabaser bruges til at søge efter den omtrentlige placering for netværks udgangspunktet. Disse databaser har typisk en nøjagtighed på ca. 90 % af IP-adresserne. Hvis placeringen, der blev søgt efter fra netværkets udgangs-IP-adresse, ikke er nøjagtig, vil dette føre til et falsk resultat. Hvis du vil validere, om denne fejl opstår for en bestemt IP-adresse, kan du bruge websteder med offentlig tilgængelig netværks-IP-adresseplacering til at sammenligne med din faktiske placering.

#### <a name="your-distance-from-the-network-egress-location"></a>Din afstand til netværkets udgangspunkt

Vi bestemmer afstanden fra den pågældende placering til kontorplaceringen. Dette vises som et netværksindsigt, hvis afstanden er større end **500 km** (800 kilometer), da det sandsynligvis vil øge TCP-ventetiden med mere end 25 ms og kan påvirke brugeroplevelsen.

Kortet viser netværkets udgangspunkt i forhold til brugerens kontorplacering, der angiver netværkets backhaul i virksomhedens WAN.

Implementer et lokalt og direkte netværks udgangspunkt fra brugerkontorplaceringer til internettet for at opnå optimal Microsoft 365 netværksforbindelsen. Forbedringer af det lokale og direkte udgangspunkt er den bedste måde at løse dette netværksindsigt på.

#### <a name="proxy-server-information"></a>Oplysninger om proxyserver

Vi identificerer, om proxyserver(e) er konfigureret på den lokale computer til at Microsoft 365 netværkstrafik i **kategorien Optimer**. Vi identificerer afstanden fra brugerens kontorplacering til proxyserverne.

Afstanden testes først af ICMP ping. Hvis det ikke lykkes, tester vi med TCP ping, og til sidst slår vi IP-adressen på proxyserveren op i en IP-adresseplaceringsdatabase. Vi viser et netværksindsigt, hvis proxyserveren er længere end **500 km** (800 kilometer) væk fra brugerens kontorplacering.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>Virtuelt privat netværk (VPN), som du bruger til at oprette forbindelse til din organisation

Denne test registrerer, hvis du bruger et VPN til at oprette forbindelse til Microsoft 365. Et videregivende resultat vises, hvis du ikke har et VPN, eller hvis du har et VPN med anbefalet konfiguration af opdelte konfigurationer for Microsoft 365.

#### <a name="vpn-split-tunnel"></a>Opdeling af VPN Tunnel

Hver **Optimer** kategorirute for Exchange Online, SharePoint Online og Microsoft Teams er testet for at se, om det er videreopret på VPN. En opdelt arbejdsbyrde undgår VPN helt. Der sendes en arbejdsbelastning via VPN. En selektiv opgavearbejdsbelastning har nogle ruter sendt via VPN og nogle opdelte. Et videregivende resultat viser, hvis alle arbejdsbelastninger opdeles eller selektivt opdeles.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Kunder i dit hovedstadsområde med bedre ydeevne

Netværksventetid mellem brugerens kontorplacering og tjenesten Exchange Online sammenlignet med andre Microsoft 365 kunder i samme metroområde. Der vises et netværksindsigt, hvis 10 % eller flere kunder i samme metroområde har bedre ydeevne. Det betyder, at deres brugere får en bedre ydeevne Microsoft 365 brugergrænsefladen.

Denne netværksindsigt genereres på grundlag af, at alle brugere i en by har adgang til den samme telekommunikationsinfrastruktur og den samme afstand til internetkredsløb og Microsofts netværk.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Tid til at oprette en DNS-anmodning på dit netværk

Dette viser den DNS-server, der er konfigureret på den klientmaskine, der kørte testene. Det kan være en DNS Rekursiv Resolver-server, men det er ualmindeligt. Det er mere sandsynligt, at det er en DNS-videresendelsesserver, som cachelagrer DNS-resultater og videresender eventuelle ikke-cachelagrede DNS-anmodninger til en anden DNS-server.

Dette er kun til information og bidrager ikke til netværksindsigt.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>Din afstand fra og/eller tid til at oprette forbindelse til en DNS-rekursiv løsning

Den brugsbaserede DNS Recursive Resolver identificeres ved at oprette en bestemt DNS-anmodning og derefter bede DNS Name Server om den IP-adresse, den modtog den samme anmodning fra. Denne IP-adresse er DNS Recursive Resolver, og den bliver søgt op i IP Address-placeringsdatabaser for at finde placeringen. Afstanden fra brugerens kontorplacering til placeringen for DNS Rekursive Resolver-serveren beregnes derefter. Dette vises som et netværksindsigt, hvis afstanden er større end **500 km** (800 kilometer).

Placeringen, der blev søgt efter fra netværkets udgangs-IP-adresse, er muligvis ikke nøjagtig, og det ville føre til et falsk resultat fra denne test. Hvis du vil validere, om denne fejl opstår for en bestemt IP-adresse, kan du bruge websteder med offentlig tilgængelig netværks-IP-adresseplacering.

Dette netværksindsigt påvirker specifikt valget af Exchange Online service front door. For at kunne håndtere dette indsigts lokale og direkte netværks udgangspunkt skal være en forudsætning, og derefter skal DNS Rekursiv Resolver være placeret tæt på det pågældende netværks udgangspunkt.

### <a name="exchange-online"></a>Exchange Online

Dette afsnit viser testresultater, der er relateret Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Exchange af service- og frontportplacering

Den in-use Exchange-tjenestes frontport identificeres på samme måde, som Outlook gør dette, og vi måler netværks-TCP-ventetiden fra brugerplaceringen til den. TCP-ventetiden vises, og den in-use Exchange service front door sammenlignes med listen over bedste forside døre til den aktuelle placering. Dette vises som et netværksindsigt, hvis en af de bedste Exchange servicefrontporte ikke er i brug.

Hvis du ikke bruger en af de bedste Exchange-tjenesteporte, kan det skyldes backhaul for netværket før virksomhedens udgangspunkt. Vi anbefaler i så fald lokale og direkte netværksud udgangspunkter. Det kan også skyldes brug af en ekstern DNS rekursiv resolver-server, hvor vi anbefaler, at dns-rekursiv resolver-serveren justeres med netværkets udgangspunkt.

Vi beregner en potentiel forbedring af TCP-ventetiden (ms) på Exchange service front door. Dette gøres ved at kigge på den testede brugers office location-netværksventetid og trække netværksventetid fra den aktuelle placering til Exchange service front door. Forskellen repræsenterer den potentielle mulighed for forbedring.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Bedste Exchange service-front dør(e) for din placering

Her vises de bedste Exchange af placeringerne for servicen efter by for din placering.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Service front door recorded in the client DNS

Dette viser DNS-navnet og IP-adressen på den Exchange front door-server, du er blevet omdirigeret til. Den er kun til information, og der er ingen tilknyttet netværksindsigt.

### <a name="sharepoint-online"></a>SharePoint Online

Dette afsnit viser testresultater, der er relateret SharePoint Online og OneDrive.

#### <a name="the-service-front-door-location"></a>Placering af servicefronten

Den in-use SharePoint service front door identificeres på samme måde som OneDrive-klienten gør, og vi måler netværks-TCP-ventetiden fra brugerens kontorplacering til den.

#### <a name="download-speed"></a>Downloadhastighed

Vi måler downloadhastigheden for en fil på 15 Mb fra SharePoint service-frontporten. Resultatet vises i megabyte pr. sekund for at angive, hvilken størrelse filen i megabyte kan downloades fra SharePoint eller OneDrive på **ét sekund**. Antallet skal være lig med en tiendedel af den mindste kredsløbsbåndbredde i megabit pr. sekund. Hvis du f.eks. har en 100 MBps internetforbindelse, kan du forvente 10 megabyte pr. sekund (10 MBps).

#### <a name="buffer-bloat"></a>Buffer bliver større

Under overførslen af 15 MB måler vi TCP-ventetiden til SharePoint service front door. Dette er ventetiden under belastning, og den sammenlignes med ventetiden, når den ikke er under belastning. Øg ventetiden, når belastningen er under belastning, kan ofte tilskrives enheders buffere på forbrugernetværket, som indlæses (eller er overbelastning). Et netværksindsigt vises for en hvilken som helst over 1.000 eller mere.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Service front door recorded in the client DNS

Dette viser DNS-navnet og IP-adressen på den SharePoint front door-server, du er blevet omdirigeret til. Den er kun til information, og der er ingen tilknyttet netværksindsigt.

### <a name="microsoft-teams"></a>Microsoft Teams

Dette afsnit viser testresultater, der er relateret Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Medieforbindelse (lyd, video og programdeling)

Dette tester, om UDP-forbindelsen er Microsoft Teams af frontsideporten for tjenester. Hvis det er blokeret, Microsoft Teams muligvis stadig arbejde med TCP, men lyd og video vil være forringet. Læs mere om disse UDP-netværksmål, som også gælder for Microsoft Teams at [mediekvalitet og ydeevne for netværksforbindelse i Skype for Business Online](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

#### <a name="packet-loss"></a>Pakketab

Viser UDP-pakketab målt i et 10-andet testlydopkald fra klienten til Microsoft Teams service front door. Dette bør være lavere end **1,00 %** for et pas.

#### <a name="latency"></a>Ventetid

Viser den målte UDP-ventetid, som skal være mindre end **100 ms**.

#### <a name="jitter"></a>Jitter

Viser den målte UDP-jitter, som skal være mindre **end 30 ms**.

#### <a name="connectivity"></a>Forbindelse

Vi tester HTTP-forbindelsen fra brugerens kontorplacering til alle de nødvendige Microsoft 365 netværksslutpunkter. Disse publiceres på [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Der vises netværksindsigt for alle nødvendige netværksslutpunkter, som ikke kan oprettes forbindelse til.

Forbindelsen kan være blokeret af en proxyserver, en firewall eller en anden netværkssikkerhedsenhed på virksomhedens netværksperimeter. Forbindelse til TCP-port 80 er testet med en HTTP-anmodning, og forbindelse til TCP-port 443 er testet med en HTTPS-anmodning. Hvis der ikke er noget svar, markeres FQDN som en fejl. Hvis der er en HTTP-svarkode 407, markeres FQDN som en fejl. Hvis der er en HTTP-svarkode 403, kontrollerer vi serverattributten for svaret, og hvis det ser ud til at være en proxyserver, markerer vi dette som en fejl. Du kan simulere de test, vi udfører med Windows kommandolinjeværktøjslinjen curl.exe.

Vi tester SSL-certifikatet på hver påkrævede Microsoft 365 netværksslutpunkt, der er i kategorien Optimer eller Tillad som defineret på [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Hvis der er test, som ikke kan findes et Microsoft SSL-certifikat, skal det krypterede netværk, der er tilsluttet, være opfanget af en mellemliggende netværksenhed. Der vises et netværksindsigt på alle krypterede netværksslutpunkter.

Hvis der findes et SSL-certifikat, der ikke leveres af Microsoft, viser vi FQDN'et til testen og ejeren af det in use SSL-certifikat. Dette SSL-certifikatejer kan være en proxyserverleverandør, eller det kan være et selv signeret virksomhedscertifikat.

#### <a name="network-path"></a>Netværkssti

Dette afsnit viser resultaterne af en ICMP-traceroute til Exchange Online service front door, SharePoint Online service front door, og Microsoft Teams service front door. Den er kun til information, og der er ingen tilknyttet netværksindsigt. Der findes tre sporinger. En traceroute _til outlook.office365.com_, en traceroute til kunderne SharePoint front end eller til _microsoft.sharepoint.com_ hvis der ikke blev angivet en, og en traceroute til _world.tr.teams.microsoft.com_.

## <a name="connectivity-reports"></a>Forbindelsesrapporter

Når du er logget på, kan du gennemse tidligere rapporter, du har kørt. Du kan også dele dem eller slette dem på listen.

> [!div class="mx-imgBorder"]
> ![Rapporter.](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>Status for netværkstilstand

Dette viser væsentlige sundhedsproblemer med Microsofts globale netværk, som kan påvirke Microsoft 365 kunder.

> [!div class="mx-imgBorder"]
> ![Status for netværkstilstand.](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="testing-from-the-command-line"></a>Test fra kommandolinjen

Vi leverer en eksekverbar kommandolinje, der kan bruges af dine fjernudrulnings- og eksekveringsværktøjer, og kører de samme test, som er tilgængelige på webstedet for Microsoft 365-værktøjet til test af netværksforbindelse.

Kommandolinjetestværktøjet kan downloades her: [Kommandolinjeværktøj](https://connectivity.office.com/api/AnonymousConnectivityTest/DownloadStandAloneRichClient)

Du kan køre den ved at dobbeltklikke på den eksekverbare fil i Windows Stifinder, eller du kan starte den fra en kommandoprompt, eller du kan planlægge den med opgavestyring.

Første gang du starter den eksekverbare brugerlicensaftale, bliver du bedt om at acceptere slutbrugerlicensaftalen (EULA), før der udføres test. Hvis du allerede har læst og accepteret eula'en, kan du oprette en tom fil, der kaldes Microsoft-365-Network-Connectivity-Test-EULA-accepted.txt i den aktuelle arbejdsmappe til den eksekverbare proces, når den startes. Hvis du vil acceptere landeaftalen, kan du skrive "y" og trykke på Enter i kommandolinjevinduet, når du bliver bedt om det.

Den eksekverbare bruger accepterer et kommandolinjeparameter på /h for at vise et link til denne Hjælp-dokumentation.

### <a name="results"></a>Resultater
Resultatoutput skrives til en JSON-fil i en mappe med navnet TestResultater, der er oprettet i den aktuelle arbejdsmappe i processen, medmindre den allerede findes. Filformatet for outputtet er connectivity_test_result_YYYY-MM-DD-HH-MM-SS.json. Resultaterne er i JSON-noder, der svarer til outputtet, der vises på websiden for webstedet Microsoft 365 testværktøjet til netværksforbindelse. Der oprettes en ny resultatfil, hver gang du kører den, og den enkeltstående eksekverbare eksekverbare fil overfører ikke resultater til din Microsoft-lejer til visning på siderne Netværksforbindelse i Administration.

### <a name="launching-from-windows-file-explorer"></a>Starte fra Windows Stifinder
Du kan blot dobbeltklikke på den eksekverbare kommando for at starte testen, så vises der et kommandopromptvindue.

### <a name="launching-from-the-command-prompt"></a>Starte fra kommandoprompten
På et CMD.EXE kommandopromptvindue kan du skrive stien og navnet på den eksekverbare kommandoprompt for at køre den. Filnavnet er Microsoft.Connectivity.Test.exe

### <a name="launching-from-windows-task-scheduler"></a>Starte fra Windows Opgavestyring
I Windows Opgavestyring kan du tilføje en opgave for at starte den enkeltstående test eksekverbar. Du skal angive den aktuelle arbejdsmappe for opgaven til at være der, hvor du har oprettet den accepterede EULA-fil, da den eksekverbare fil blokerer, indtil den er blevet accepteret. Du kan ikke acceptere eula'en interaktivt, hvis processen startes i baggrunden uden en konsol.

### <a name="more-details-on-the-standalone-executable"></a>Flere oplysninger om den enkeltstående eksekverbare eksekverbar
Kommandolinjeværktøjet bruger Placeringstjenester Windows at finde brugerne oplysninger om Byland til at fastslå visse afstande. Hvis Windows placeringstjenester er deaktiveret i kontrolpanelet, vil brugerplaceringsbaserede vurderinger være tomme. I Windows Indstillinger skal "Placeringstjenester" være tændt, og "Lad skrivebordsapps få adgang til din placering" også være tændt.

Kommandolinjeværktøjet forsøger at installere værktøjet, hvis .NET Framework ikke allerede er installeret. Programmet downloader også den primære eksekverbare test fra Microsoft 365 netværksforbindelsesværktøjet og starter det.

## <a name="faq"></a>Ofte stillede spørgsmål

Her finder du svar på nogle af vores ofte stillede spørgsmål.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Hvad kræves der for at køre den avancerede testklient?

Den avancerede testklient kræver .NET 6.0 Runtime. Hvis du kører den avancerede testklient uden den installerede, bliver du ført til [installationssiden .NET 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0/runtime?utm_source=getdotnetcore). Sørg for at installere fra kolonnen Kør skrivebordsapps for at Windows. Administratortilladelser på computeren skal være nødvendige for at installere .NET 6.0 Runtime.

Den avancerede testklient bruger SignalR til at kommunikere til websiden. For at gøre dette skal du sikre dig, at TCP-port **443-forbindelse til connectivity.service.signalr.net** er åben. Denne URL-adresse publiceres ikke i, <https://aka.ms/o365ip> fordi forbindelsen ikke er påkrævet for en bruger Microsoft 365 klientprogram.

### <a name="what-is-microsoft-365-service-front-door"></a>Hvad er Microsoft 365 service front dør?

Frontporten Microsoft 365 er et indgangspunkt på Microsofts globale netværk, hvor Office klienter og tjenester afslutter deres netværksforbindelse. For en optimal netværksforbindelse til Microsoft 365 anbefales det, at din netværksforbindelse afsluttes til den nærmeste Microsoft 365 frontport i din by eller metro.

> [!NOTE]
> Microsoft 365 servicefronten har ingen direkte relation til det **Azure Front Door Service-produkt, der** er tilgængeligt på Azure Marketplace.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Hvad er den bedste Microsoft 365 service front door?

En bedste Microsoft 365 service front door (tidligere kendt som en optimal service front door) er en, der er tættest på dit netværk udgangspunkt, generelt i din by eller metro-området. Brug Microsoft 365 til at bestemme placeringen af din in-use Microsoft 365 service front door(s) og den bedste service frontsideport(e). Hvis værktøjet afgør, at din in-use front door er en af de bedste, så kan du forvente gode forbindelser til Microsofts globale netværk.

### <a name="what-is-an-internet-egress-location"></a>Hvad er en internet udgangspunkt placering?

Internetudgangsplaceringen er den placering, hvor netværkstrafikken afslutter virksomhedsnetværket og opretter forbindelse til internettet. Dette identificeres også som den placering, hvor du har en enhed til oversættelse af netværksadresse (NAT), og som regel der, hvor du opretter forbindelse til en internetudbyder. Hvis du ser en lang afstand mellem din placering og din internetud udgangspunkt, kan dette identificere en betydelig WAN-backhaul.

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md)

[Microsoft 365 indsigt i netværksydeevne](office-365-network-mac-perf-insights.md)

[Microsoft 365 netværksvurdering](office-365-network-mac-perf-score.md)

[Microsoft 365 til placeringstjenester for netværksforbindelse](office-365-network-mac-location-services.md)
