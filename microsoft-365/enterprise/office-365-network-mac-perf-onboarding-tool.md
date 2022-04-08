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
ms.openlocfilehash: 047a1ad10efa20f2c47491a20855a92bf141eb15
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705575"
---
# <a name="microsoft-365-network-connectivity-test-tool"></a>Microsoft 365 testværktøj til netværksforbindelse

Testværktøjet Microsoft 365 netværksforbindelse er placeret på <https://connectivity.office.com>. Det er et supplement til den netværksvurdering og netværksindsigt, der er tilgængelig i Microsoft 365 Administration under **| Menuen Forbindelse**.

> [!IMPORTANT]
> Det er vigtigt at logge på din Microsoft 365 lejer, da alle testrapporter deles med administratoren og uploades til lejeren, mens du er logget på.

> [!div class="mx-imgBorder"]
> ![Forbindelsestestværktøj.](../media/m365-mac-perf/m365-mac-perf-test-tool-page.png)

>[!NOTE]
>Testværktøjet til netværksforbindelse understøtter lejere i WW Commercial, men ikke GCC Moderate, GCC High, DoD eller China.

Netværksindsigt i Microsoft 365 Administration Center er baseret på almindelige målinger i produktet for din Microsoft 365 lejer, der samles hver dag. Til sammenligning køres netværksindsigt fra Microsoft 365 test af netværksforbindelsen lokalt i værktøjet.

Test i produktet er begrænset, og kørsel af test lokalt for brugeren indsamler flere data, hvilket resulterer i dybere indsigt. Netværksindsigt i Microsoft 365 Administration Center viser, at der er et netværksproblem på en bestemt office-placering. Microsoft 365 forbindelsestesten kan hjælpe med at identificere hovedårsagen til problemet og levere en målrettet handling til forbedring af ydeevnen.

Vi anbefaler, at disse indsigter bruges sammen, hvor netværksstatus kan vurderes for hver office-placering i Microsoft 365 Administration Center, og der kan findes flere specifikke oplysninger efter udrulningen af test baseret på Microsoft 365 forbindelsestest.

## <a name="what-happens-at-each-test-step"></a>Hvad sker der på hvert testtrin?

### <a name="office-location-identification"></a>Office placerings-id

Når du klikker på knappen *Kør test* , viser vi den kørende testside og identificerer office-placeringen. Du kan skrive din placering efter by, stat og land eller vælge at få den registreret for dig. Hvis du registrerer kontorplaceringen, anmoder værktøjet om breddegrad og længdegrad fra webbrowseren og begrænser nøjagtigheden til 300 meter med 300 meter før brug. Det er ikke nødvendigt at identificere placeringen mere præcist end bygningen for at måle netværkets ydeevne.

### <a name="javascript-tests"></a>JavaScript-test

Efter identifikation af office-placering kører vi en TCP-ventetidstest i JavaScript, og vi anmoder om data fra tjenesten om i brug og anbefalede Microsoft 365 front door-servere til tjenesten. Når disse test er fuldført, viser vi dem på kortet og under fanen Detaljer, hvor de kan ses før næste trin.

### <a name="download-the-advanced-tests-client-application"></a>Download klientprogrammet til avancerede test

Derefter starter vi downloaden af klientprogrammet til avancerede test. Vi er afhængige af brugeren for at starte klientprogrammet, og de skal også have .NET 6.0 Runtime installeret.

Der er to dele til Microsoft 365 test af netværksforbindelsen: webstedet <https://connectivity.office.com> og et Windows klientprogram, der kan downloades, og som kører avancerede test af netværksforbindelsen. De fleste af testene kræver, at programmet køres. Resultaterne udfyldes på websiden igen, når den køres.

Du bliver bedt om at hente det avancerede klienttestprogram fra webstedet, når webbrowsertestene er fuldført. Åbn og kør filen, når du bliver bedt om det.

> [!div class="mx-imgBorder"]
> ![Klientprogram til avancerede test.](../media/m365-mac-perf/m365-mac-perf-open-run-file.png)

### <a name="start-the-advanced-tests-client-application"></a>Start klientprogrammet til avancerede test

Når klientprogrammet starter, opdateres websiden for at vise dette resultat. Testdata vil begynde at blive modtaget på websiden. Siden opdateres, hver gang der modtages nye data, og du kan gennemse dataene, når de modtages.

### <a name="advanced-tests-completed-and-test-report-upload"></a>Avancerede test er fuldført og upload af testrapport

Når testene er fuldført, viser websiden og klienten til avancerede test begge dette. Hvis brugeren er logget på, uploades testrapporten til kundens lejer.

## <a name="sharing-your-test-report"></a>Deling af din testrapport

Testrapporten kræver godkendelse til din Microsoft 365 konto. Din administrator vælger, hvordan du kan dele din testrapport. Standardindstillingerne gør det muligt at dele dine rapporter med andre brugere i organisationen, og linket ReportID er ikke tilgængeligt. Rapporter udløber som standard efter 90 dage.

### <a name="sharing-your-report-with-your-administrator"></a>Deling af din rapport med administratoren

Hvis du er logget på, når der opstår en testrapport, deles rapporten med administratoren.

### <a name="sharing-with-your-microsoft-account-team-support-or-other-personnel"></a>Deling med dit Microsoft-kontoteam, support eller andet personale

Testrapporter (undtagen enhver personlig identifikation) deles med Microsoft-medarbejdere. Denne deling er aktiveret som standard og kan deaktiveres af administratoren i **| Siden Network Connectivity** i Microsoft 365 Administration Center.

### <a name="sharing-with-other-users-who-sign-in-to-the-same-microsoft-365-tenant"></a>Deling med andre brugere, der logger på den samme Microsoft 365 lejer

Du kan vælge brugere, som din rapport skal deles med. Det er som standard aktiveret at kunne vælge, men det kan deaktiveres af administratoren.

> [!div class="mx-imgBorder"]
> ![Deling af et link til dine testresultater med en bruger.](../media/m365-mac-perf/m365-mac-perf-share-to-user.png)

### <a name="sharing-with-anyone-using-a-reportid-link"></a>Deling med alle, der bruger et ReportID-link

Du kan dele din testrapport med alle ved at give adgang til et ReportID-link. Dette link genererer en URL-adresse, som du kan sende til en person, så de kan få vist testrapporten uden at logge på. Denne deling er deaktiveret som standard og skal aktiveres af administratoren.

> [!div class="mx-imgBorder"]
> ![Deling af et link til dine testresultater.](../media/m365-mac-perf/m365-mac-perf-share-link.png)

## <a name="network-connectivity-test-results"></a>Testresultater for netværksforbindelse

Resultaterne vises under fanerne **Oversigt** og **Detaljer** . Fanen Oversigt viser et kort over den registrerede netværksperimeter og en sammenligning af netværksvurderingen med andre Microsoft 365 kunder i nærheden. Det giver også mulighed for deling af testrapporten. Sådan ser visningen med oversigtsresultater ud:

> [!div class="mx-imgBorder"]
> ![Oversigtsresultater for testværktøjet til netværksforbindelsen.](../media/m365-mac-perf/m365-mac-perf-summary-page.png)

Her er et eksempel på outputtet under fanen Detaljer. Under fanen Detaljer vises en markering af grøn cirkel, hvis resultatet blev sammenlignet positivt. Vi viser et rødt trekantudråbstegn, hvis resultatet overskred en grænse, der angiver en netværksindsigt. I de følgende afsnit beskrives hver af rækkerne under fanen Detaljer, og de tærskler, der bruges til netværksindsigt, forklares.

> [!div class="mx-imgBorder"]
> ![Eksempel på testresultater af test af netværksforbindelsen.](../media/m365-mac-perf/m365-mac-perf-all-details.png)

### <a name="your-location-information"></a>Oplysninger om din placering

I dette afsnit vises testresultater, der er relateret til din placering.

#### <a name="your-location"></a>Din placering

Brugerens placering registreres fra brugernes webbrowser. Det kan også skrives efter brugerens eget valg. Den bruges til at identificere netværksafstande til bestemte dele af virksomhedens netværksperimeter. Det er kun byen fra denne placeringsregistrering og afstanden til andre netværkspunkter, der gemmes i rapporten.

Brugerens kontorplacering vises i kortvisningen.

#### <a name="network-egress-location-the-location-where-your-network-connects-to-your-isp"></a>Netværks udgangsplacering (den placering, hvor dit netværk opretter forbindelse til internetudbyderen)

Vi identificerer netværkets udgående IP-adresse på serversiden. Placeringsdatabaser bruges til at slå den omtrentlige placering af netværksudgående op. Disse databaser har typisk en nøjagtighed på ca. 90 % af IP-adresserne. Hvis placeringen, der blev slået op fra netværkets udgående IP-adresse, ikke er nøjagtig, vil dette føre til et falsk resultat. Hvis du vil validere, om denne fejl opstår for en bestemt IP-adresse, kan du bruge offentligt tilgængelige netværks-IP-adresseplaceringswebsteder til at sammenligne med din faktiske placering.

#### <a name="your-distance-from-the-network-egress-location"></a>Din afstand fra netværkets udgående placering

Vi bestemmer afstanden fra denne placering til kontorplaceringen. Dette vises som en netværksindsigt, hvis afstanden er større end **800 kilometer** , da det sandsynligvis vil øge TCP-ventetiden med mere end 25 ms og kan påvirke brugeroplevelsen.

Kortet viser netværkets udgående placering i forhold til brugerens kontorplacering, hvilket angiver netværkets backhaul i virksomhedens WAN.

Implementer udgående lokale og direkte netværk fra brugerens kontorplaceringer til internettet for at få optimal Microsoft 365 netværksforbindelse. Forbedringer af lokal og direkte udgående data er den bedste måde at håndtere denne netværksindsigt på.

#### <a name="proxy-server-information"></a>Oplysninger om proxyserver

Vi identificerer, om proxyserver(r) er konfigureret på den lokale computer til at overføre Microsoft 365 netværkstrafik i kategorien **Optimer**. Vi identificerer afstanden fra brugerens office-placering til proxyserverne.

Afstanden testes først af ICMP-ping. Hvis det mislykkes, tester vi med TCP-ping, og til sidst slår vi proxyserverens IP-adresse op i en placeringsdatabase for IP-adressen. Vi viser en netværksindsigt, hvis proxyserveren er længere end **800** kilometer væk fra brugerens kontorplacering.

#### <a name="virtual-private-network-vpn-you-use-to-connect-to-your-organization"></a>VPN (Virtuelt privat netværk), du bruger til at oprette forbindelse til din organisation

Denne test registrerer, om du bruger en VPN til at oprette forbindelse til Microsoft 365. Et overførselsresultat vises, hvis du ikke har nogen VPN, eller hvis du har en VPN med anbefalet konfiguration af opdelt tunnel til Microsoft 365.

#### <a name="vpn-split-tunnel"></a>VPN-opdeling Tunnel

Hver  optimeringskategorirute for Exchange Online, SharePoint Online og Microsoft Teams testes for at se, om den er tunneleret på VPN'en. En opdelt arbejdsbelastning forhindrer VPN-forbindelsen helt. Der sendes en tunnelarbejdsbelastning via VPN'en. En selektiv tunnelarbejdsbelastning har nogle ruter sendt via VPN'en, og nogle er opdelt. Et overførselsresultat vises, hvis alle arbejdsbelastninger er opdelt eller selektivt tunneleret.

#### <a name="customers-in-your-metropolitan-area-with-better-performance"></a>Kunder i dit storbyområde med bedre ydeevne

Netværksventetid mellem brugerens kontorplacering og Exchange Online-tjenesten sammenlignes med andre Microsoft 365 kunder i samme metroområde. Der vises en netværksindsigt, hvis 10 % eller flere af kunderne i samme metroområde har en bedre ydeevne. Det betyder, at brugerne får en bedre ydeevne i den Microsoft 365 brugergrænseflade.

Denne netværksindsigt genereres på baggrund af, at alle brugere i en by har adgang til den samme telekommunikationsinfrastruktur og den samme nærhed til internetkredsløb og Microsofts netværk.

#### <a name="time-to-make-a-dns-request-on-your-network"></a>Tid til at foretage en DNS-anmodning på dit netværk

Dette viser den DNS-server, der er konfigureret på den klientcomputer, der kørte testene. Det kan være en DNS-rekursiv resolverserver, men dette er ualmindeligt. Det er mere sandsynligt, at det er en DNS-videresendelsesserver, der cachelagrer DNS-resultater og videresender alle ikke-cachelagrede DNS-anmodninger til en anden DNS-server.

Dette er kun til orientering og bidrager ikke til nogen netværksindsigt.

#### <a name="your-distance-from-andor-time-to-connect-to-a-dns-recursive-resolver"></a>Din afstand fra og/eller tid til at oprette forbindelse til en REKURSIV DNS-fortolker

Den anvendte DNS-rekursive resolver identificeres ved at foretage en bestemt DNS-anmodning og derefter bede DNS-navneserveren om den IP-adresse, den modtog den samme anmodning fra. Denne IP-adresse er den rekursive DNS-fortolker, og den vil blive slået op i databaser med IP-adresseplaceringer for at finde placeringen. Afstanden fra brugerens office-placering til serverplaceringen for DNS-rekursiv fortolker beregnes derefter. Dette vises som en netværksindsigt, hvis afstanden er større end **800 kilometer** .

Den placering, der blev slået op fra netværkets udgående IP-adresse, er muligvis ikke nøjagtig, og dette ville føre til et falsk resultat fra denne test. Hvis du vil validere, om denne fejl opstår for en bestemt IP-adresse, kan du bruge offentligt tilgængelige netværks-IP-adresseplaceringswebsteder.

Denne netværksindsigt vil specifikt påvirke valget af Exchange Online service front door. For at løse denne indsigt skal lokal og direkte netværksudgående være en forudsætning, og derefter skal DNS Rekursive Resolver være placeret tæt på denne netværksudgående.

### <a name="exchange-online"></a>Exchange Online

I dette afsnit vises testresultater, der er relateret til Exchange Online.

#### <a name="exchange-service-front-door-location"></a>Exchange placering af hoveddøren til tjenesten

Hoveddøren i brug Exchange tjenesten identificeres på samme måde, som Outlook gør, og vi måler netværkets TCP-ventetid fra brugerens placering til den. TCP-ventetiden vises, og den brugsbaserede Exchange fordøren til tjenesten sammenlignes med listen over de bedste servicefrontdøre for den aktuelle placering. Dette vises som en netværksindsigt, hvis en af de bedste Exchange hoveddøren(e) til tjenesten ikke er i brug.

Hvis du ikke bruger en af de bedste Exchange hoveddøren(e) til tjenesten, kan det skyldes, at netværkets backhaul er udgående, før virksomhedens netværk udgående, i hvilket tilfælde vi anbefaler lokal og direkte netværksafgang. Det kan også skyldes brugen af en ekstern DNS-rekursiv resolverserver, i hvilket tilfælde vi anbefaler, at den REkursive DNS-fortolkerserver justeres med netværksudgående.

Vi beregner en potentiel forbedring af TCP-ventetiden (ms) i Exchange servicens hoveddør. Dette gøres ved at se på den testede netværksventetid på brugerens kontorplacering og trække netværksventetiden fra den aktuelle placering til skabet Exchange fordøren til tjenesten. Forskellen repræsenterer den potentielle mulighed for forbedringer.

#### <a name="best-exchange-service-front-doors-for-your-location"></a>Bedste Exchange service front door(s) til din placering

Dette viser de bedste Exchange service front door placeringer efter by for din placering.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Hoveddøren til tjenesten registreres i klientens DNS

Dette viser DNS-navnet og IP-adressen på den Exchange tjenestes front door-server, som du blev dirigeret til. Den er kun beregnet til oplysninger, og der er ingen tilknyttet netværksindsigt.

### <a name="sharepoint-online"></a>SharePoint Online

I dette afsnit vises testresultater, der er relateret til SharePoint Online og OneDrive.

#### <a name="the-service-front-door-location"></a>Placeringen af hoveddøren til tjenesten

Hoveddøren i brug SharePoint tjenesten identificeres på samme måde, som den OneDrive klient gør, og vi måler netværkets TCP-ventetid fra brugerens kontorplacering til den.

#### <a name="download-speed"></a>Downloadhastighed

Vi måler downloadhastigheden for en fil på 15 Mb fra SharePoint-tjenestens hoveddør. Resultatet vises i megabyte pr. sekund for at angive, hvilken størrelse fil i megabyte der kan downloades fra SharePoint eller OneDrive på **ét sekund**. Tallet skal svare til en tiendedel af den minimale kredsløbsbåndbredde i megabit pr. sekund. Hvis du f.eks. har en internetforbindelse på 100 mbps, kan du forvente 10 megabyte pr. sekund (10 MBps).

#### <a name="buffer-bloat"></a>Bufferbloat

Under downloaden på 15 MB måler vi TCP-ventetiden for SharePoint-tjenestens hoveddør. Dette er ventetiden under indlæsning, og den sammenlignes med ventetiden, når den ikke er under indlæsning. Stigningen i ventetiden, når der er under belastning, skyldes ofte, at forbrugernetværksenhedsbuffere indlæses (eller oppustet). Der vises en netværksindsigt for en bloat på 1.000 eller mere.

#### <a name="service-front-door-recorded-in-the-client-dns"></a>Hoveddøren til tjenesten registreres i klientens DNS

Dette viser DNS-navnet og IP-adressen på den SharePoint tjenestes front door-server, som du blev dirigeret til. Den er kun beregnet til oplysninger, og der er ingen tilknyttet netværksindsigt.

### <a name="microsoft-teams"></a>Microsoft Teams

I dette afsnit vises testresultater, der er relateret til Microsoft Teams.

#### <a name="media-connectivity-audio-video-and-application-sharing"></a>Medieforbindelse (lyd-, video- og programdeling)

Dette tester udP-forbindelsen til Microsoft Teams-tjenestens hoveddør. Hvis dette er blokeret, fungerer Microsoft Teams muligvis stadig ved hjælp af TCP, men lyd og video forringes. Læs mere om disse UDP-netværksmålinger, som også gælder for Microsoft Teams i [Media Quality og Network Connectivity Performance i Skype for Business Online](/skypeforbusiness/optimizing-your-network/media-quality-and-network-connectivity-performance).

#### <a name="packet-loss"></a>Pakketab

Viser UDP-pakketabet målt i et 10-sekunders testlydopkald fra klienten til Microsoft Teams-tjenestens hoveddør. Dette skal være lavere end **1,00 %** for et gennemløb.

#### <a name="latency"></a>Latency

Viser den målte UDP-ventetid, som skal være mindre end **100 ms**.

#### <a name="jitter"></a>Jitter

Viser den målte UDP-jitter, som skal være mindre end **30 ms**.

#### <a name="connectivity"></a>Forbindelse

Vi tester for HTTP-forbindelse fra brugerens Office-placering til alle de påkrævede Microsoft 365 netværksslutpunkter. Disse udgives på [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Der vises en netværksindsigt for alle påkrævede netværksslutpunkter, som der ikke kan oprettes forbindelse til.

Forbindelsen kan være blokeret af en proxyserver, en firewall eller en anden netværkssikkerhedsenhed på virksomhedens netværksperimeter. Forbindelsen til TCP-port 80 testes med en HTTP-anmodning, og forbindelsen til TCP-port 443 testes med en HTTPS-anmodning. Hvis der ikke er noget svar, er FQDN markeret som en fejl. Hvis der er en HTTP-svarkode 407, er FQDN markeret som en fejl. Hvis der er en HTTP-svarkode 403, kontrollerer vi svarets serverattribut, og hvis det ser ud til at være en proxyserver, markerer vi dette som en fejl. Du kan simulere de test, vi udfører med kommandolinjeværktøjet Windows curl.exe.

Vi tester SSL-certifikatet på hvert påkrævede Microsoft 365 netværksslutpunkt, der findes i kategorien Optimer eller tillad som defineret på [https://aka.ms/o365ip](./urls-and-ip-address-ranges.md). Hvis nogen test ikke finder et Microsoft SSL-certifikat, skal det krypterede netværk, der er tilsluttet, være blevet opfanget af en mellemliggende netværksenhed. Der vises en netværksindsigt på alle opfangede krypterede netværksslutpunkter.

Hvor der findes et SSL-certifikat, der ikke leveres af Microsoft, viser vi FQDN for testen og ejeren af det i brug brugte SSL-certifikat. Denne ssl-certifikatejer kan være en proxyserverleverandør, eller det kan være et selvstændigt virksomhedssigneret certifikat.

#### <a name="network-path"></a>Netværkssti

I dette afsnit vises resultaterne af en ICMP-sporingsroute til Exchange Online servicefront door, SharePoint Online-tjenestens fordør og Microsoft Teams servicefront door. Den er kun beregnet til oplysninger, og der er ingen tilknyttet netværksindsigt. Der er angivet tre traceroutes. En traceroute til _outlook.office365.com_, en traceroute til kunderne SharePoint frontend eller til at _microsoft.sharepoint.com_, hvis der ikke blev angivet en, og en traceroute til _world.tr.teams.microsoft.com_.

## <a name="connectivity-reports"></a>Forbindelsesrapporter

Når du er logget på, kan du gennemse tidligere rapporter, som du har kørt. Du kan også dele dem eller slette dem på listen.

> [!div class="mx-imgBorder"]
> ![Rapporter.](../media/m365-mac-perf/m365-mac-perf-reports-list.png)

## <a name="network-health-status"></a>Status for netværkstilstand

Dette viser eventuelle betydelige tilstandsproblemer med Microsofts globale netværk, som kan påvirke Microsoft 365 kunder.

> [!div class="mx-imgBorder"]
> ![Status for netværkets tilstand.](../media/m365-mac-perf/m365-mac-perf-status-page.png)

## <a name="testing-from-the-command-line"></a>Test fra kommandolinjen

Vi leverer en eksekverbar kommandolinje, der kan bruges af fjerninstallations- og udførelsesværktøjerne og køre de samme test, som er tilgængelige på webstedet for Microsoft 365 testværktøj til netværksforbindelsen.

Kommandolinjetestværktøjet kan downloades her: [Kommandolinjeværktøj](https://connectivity.office.com/api/AnonymousConnectivityTest/DownloadStandAloneRichClient)

Du kan køre den ved at dobbeltklikke på den eksekverbare fil i Windows Stifinder, eller du kan starte den fra en kommandoprompt, eller du kan planlægge den med Opgavestyring.

Første gang du starter den eksekverbare fil, bliver du bedt om at acceptere slutbrugerlicensaftalen, før der udføres test. Hvis du allerede har læst og accepteret slutbrugerlicensaftalen, kan du oprette en tom fil med navnet Microsoft-365-Network-Connectivity-Test-EULA-accepted.txt i den aktuelle arbejdsmappe for den eksekverbare proces, når den startes. Hvis du vil acceptere slutbrugerlicensaftalen, kan du skrive 'y' og trykke på Enter i kommandolinjevinduet, når du bliver bedt om det.

Den eksekverbare fil accepterer kommandolinjeparameteren /h for at få vist et link til denne Hjælp-dokumentation.

### <a name="results"></a>Resultater
Output af resultater skrives til en JSON-fil i en mappe med navnet TestResults, som oprettes i den aktuelle arbejdsmappe for processen, medmindre den allerede findes. Filformatet for outputtet er connectivity_test_result_YYYY-MM-DD-HH-MM-SS.json. Resultaterne er i JSON-noder, der svarer til det output, der vises på websiden for Microsoft 365 testværktøjet til netværksforbindelse. Der oprettes en ny resultatfil, hver gang du kører den, og den separate eksekverbare fil overfører ikke resultater til din Microsoft-lejer til visning på siderne til Netværksforbindelse i Administration.

### <a name="launching-from-windows-file-explorer"></a>Starter fra Windows Stifinder
Du kan blot dobbeltklikke på den eksekverbare fil for at starte testen, hvorefter der vises et kommandopromptvindue.

### <a name="launching-from-the-command-prompt"></a>Starter fra kommandoprompten
I et CMD.EXE kommandopromptvindue kan du skrive stien til og navnet på den eksekverbare fil for at køre den. Filnavnet er Microsoft.Connectivity.Test.exe

### <a name="launching-from-windows-task-scheduler"></a>Starter fra Windows Opgavestyring
I Windows Opgavestyring kan du tilføje en opgave for at starte den eksekverbare test. Du skal angive den aktuelle arbejdsmappe for opgaven, så den er der, hvor du har oprettet den godkendte fil med slutbrugerlicensaftalen, da den eksekverbare fil blokeres, indtil slutbrugerlicensaftalen accepteres. Du kan ikke acceptere slutbrugerlicensaftalen interaktivt, hvis processen startes i baggrunden uden en konsol.

### <a name="more-details-on-the-standalone-executable"></a>Flere oplysninger om den separate eksekverbare fil
Kommandolinjeværktøjet bruger Windows Location Services til at finde oplysningerne om brugerne City State Country til at bestemme nogle afstande. Hvis Windows Placeringstjenester er deaktiveret i Kontrolpanel, er brugerplaceringsbaserede vurderinger tomme. I Windows Indstillinger skal "Placeringstjenester" være slået til, og "Lad skrivebordsapps få adgang til din placering" skal også være slået til.

Kommandolinjeværktøjet forsøger at installere .NET Framework, hvis det ikke allerede er installeret. Den downloader også den primære eksekverbare test fra testværktøjet til Microsoft 365 netværksforbindelse og starter den.

## <a name="faq"></a>Ofte stillede spørgsmål

Her er svar på nogle af vores ofte stillede spørgsmål.

### <a name="what-is-required-to-run-the-advanced-test-client"></a>Hvad kræves der for at køre den avancerede testklient?

Den avancerede testklient kræver .NET 6.0 Runtime. Hvis du kører den avancerede testklient, uden at det er installeret, sendes du videre til [installationssiden til .NET 6.0](https://dotnet.microsoft.com/en-us/download/dotnet/6.0/runtime?utm_source=getdotnetcore). Sørg for at installere fra kolonnen Kør skrivebordsapps for Windows. Der kræves administratortilladelser på computeren for at installere .NET 6.0 Runtime.

Den avancerede testklient bruger SignalR til at kommunikere til websiden. Til dette skal du sikre, at TCP-port 443-forbindelsen til **connectivity.service.signalr.net** er åben. Denne URL-adresse er ikke publiceret i , <https://aka.ms/o365ip> fordi denne forbindelse ikke er påkrævet for en Microsoft 365 bruger af klientprogrammet.

### <a name="what-is-microsoft-365-service-front-door"></a>Hvad er Microsoft 365 hoveddør til service?

Hoveddøren til Microsoft 365-tjenesten er et indgangspunkt på Microsofts globale netværk, hvor Office klienter og tjenester afslutter deres netværksforbindelse. Hvis du vil have en optimal netværksforbindelse til Microsoft 365, anbefales det, at din netværksforbindelse afsluttes til den nærmeste Microsoft 365 hoveddør i din by eller metro.

> [!NOTE]
> Microsoft 365 front door-tjeneste har ingen direkte relation til det **Azure Front Door Service-produkt**, der er tilgængeligt på Azure Marketplace.

### <a name="what-is-the-best-microsoft-365-service-front-door"></a>Hvad er den bedste Microsoft 365 hoveddøren til service?

En bedste Microsoft 365 service front door (tidligere kendt som en optimal service front door) er en, der er tættest på dit netværk udgang, generelt i din by eller metro område. Brug værktøjet til Microsoft 365 netværksydeevne til at bestemme placeringen af din i brug Microsoft 365 fordøren til tjenesten og den eller de bedste servicefrontdøre. Hvis værktøjet bestemmer, at din brugsdør er en af de bedste, bør du forvente god forbindelse til Microsofts globale netværk.

### <a name="what-is-an-internet-egress-location"></a>Hvad er en internet udgående placering?

Internet udgående placering er den placering, hvor netværkstrafikken forlader virksomhedsnetværket og opretter forbindelse til internettet. Dette identificeres også som den placering, hvor du har en NAT-enhed (Network Address Translation), og som regel hvor du opretter forbindelse til en internetudbyder. Hvis du ser en lang afstand mellem din placering og din internet udgående placering, kan dette identificere en betydelig WAN-backhaul.

## <a name="related-topics"></a>Relaterede emner

[Netværksforbindelse i Microsoft 365 Administration Center](office-365-network-mac-perf-overview.md)

[Microsoft 365 indsigt i netværksydeevne](office-365-network-mac-perf-insights.md)

[Microsoft 365 netværksvurdering](office-365-network-mac-perf-score.md)

[Microsoft 365 placeringstjenester for netværksforbindelsen](office-365-network-mac-location-services.md)
