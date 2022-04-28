---
title: Bedste praksis for brug af Office 365 på et langsomt netværk
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/29/2016
audience: End User
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
search.appverid:
- MET150
- MET150
- MOP150
- MEW150
- BCS160
ms.assetid: fd16c8d2-4799-4c39-8fd7-045f06640166
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Denne artikel hjælper dig gennem de bedste fremgangsmåder, du kan anvende i forbindelse med brug af Office 365 på et langsomt netværk.
ms.openlocfilehash: 5ed3a9dfc665d5067fb3f310fc74aa4b100190f2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091627"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Bedste praksis for brug af Office 365 på et langsomt netværk

Ville det ikke være rart, hvis din internetforbindelse altid var hurtig og aldrig ned? Måske den dag vil komme. Men i mellemtiden er der praktiske ting, du kan gøre for at arbejde omkring et balky-netværk og stadig få dit daglige arbejde gjort. Selvom Office 365 er en cloudbaseret tjeneste, indeholder den også mange måder at arbejde offline med dit indhold på og holde dine ændringer synkroniseret på en problemfri måde. Desuden er det nogle gange mere effektivt at arbejde med indhold offline, bare fordi programmer kører hurtigere, og brugergrænsefladen er mere dynamisk. Pointen er dette: Office 365 giver dig det bedste fra begge verdener. Her kan du se, hvordan du kan drage fordel af det.

> [!TIP]
> Vil du gerne se, hvor langsom (eller hurtig) netværksforbindelsen er? Prøv [OOKLA Speed-testen](https://www.speedtest.net/) eller [appen Test af netværkshastighed](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).

## <a name="why-is-my-network-so-slow"></a>Hvorfor er mit netværk så langsomt?

Selvom du ikke selv har kontrol over netværkets ydeevne, hjælper det at forstå, hvad der foregår bag kulisserne. Internettet er enormt komplekst, men der er et par begreber, der kan hjælpe dig med at forstå situationen meget bedre. Hvis du følger de bedste fremgangsmåder i denne artikel, kan det hjælpe med at løse problemer med ydeevnen og reducere frustrationen.

### <a name="major-factors-that-affect-network-performance"></a>Overordnede faktorer, der påvirker netværkets ydeevne

![Faktorer for netværksydeevne.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Båndbredde og ventetid**: De to vigtigste målinger af netværkets ydeevne er båndbredde og ventetid:

- Båndbredde er dataoverførselshastigheden målt i bit pr. sekund. Større er bedre. Båndbredden er som et vandrør. Jo større rør, jo mere vand, som du kan "sætte igennem" det.

- Ventetid er den tid, det tager for indhold at komme fra en server eller tjeneste til din enhed, og den måles i millisekunder. Hurtigere er bedre. Ventetid kan skyldes en række faktorer, herunder lav båndbredde, en sparsom forbindelse eller overførselstid.

 **Almindelige problemer**: Ud over båndbredde og ventetid har andre problemer indflydelse på netværkets ydeevne og er ofte uforudsigelige. Netværksydeevnen kan svinge afhængigt af tidspunktet på dagen eller din fysiske placering. Netværket kan blive tilstoppet, når der forekommer visse hændelser, der stigninger i brugen af internettet, f.eks. en naturkatastrofe eller en større offentlig begivenhed. Størrelsen og kompleksiteten af den side, der indlæses, og antallet og størrelsen af de filer, der overføres, har direkte indflydelse på ydeevnen. En WiFi-forbindelse kan forringes midlertidigt: Du kan f.eks. forespørge på et stort møde med tusindvis ved at anmode alle om at tweete på samme tid.

 **Overvejelser i forbindelse med et satellitnetværk**: Et satellitnetværk er nyttigt, når et jordbaseret netværk ikke er praktisk, f.eks. baglandet, et krydstogtskib eller et eksternt videnskabeligt område. Disse netværk er afhængige af satellitter placeret i en geosynkron kredsløb 22.000 miles over ækvator. Men en transmission faktisk rejser omkring 90.000 miles, og så et satellitnetværk har en langsommere ventetid (500 ms eller mere) end et jordbaseret netværk (20 til 50 ms). Under de bedste betingelser bemærker du muligvis ikke denne ventetid, men for at downloade store filer, streame videoer og spille spil, vil du sandsynligvis. Et andet problem er "regnudtoning", hvor kraftigt vejr, såsom tordenvejr og snestorme, midlertidigt kan afbryde satellittransmission.

## <a name="are-you-sure-its-the-network"></a>Er du sikker på, at det er netværket?

Når du oplever problemer med ydeevnen, skal du først sørge for, at enheden ikke er den egentlige årsag til problemet. Der er to ting, du kan gøre, som kan gøre en stor forbedring:

- Sørg for, at enheden kører godt, og at der ikke er malware på computeren.

- Hvis det er muligt, skal du købe mere hukommelse. Tilføjelse af hukommelse er den enkleste og ofte mest effektive måde at forbedre ydeevnen på din enhed på. Det er især nyttigt, når du arbejder med store filer og videoer.

Du kan få flere oplysninger [under Windows Ydeevne og vedligeholdelse](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) og [Tips for at forbedre pc'ens ydeevne i Windows 10](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Bedste praksis for brug af din browser

Din browser er din gateway til Office 365, så den kan have indflydelse på ydeevnen, især med den tid, det tager at indlæse en side, og hvor ofte du rundtur til Office 365-tjenesten.

### <a name="browsers-in-general"></a>Browsere generelt

Her er nogle forslag til browsere generelt:

- Deaktiver browsertilføjelsesprogramper, der kan påvirke ydeevnen, eller som du ikke har brug for.

- Øg cachestørrelsen for dine midlertidige internetfiler.

- Når du er logget på din arbejds- eller skolekonto, skal du holde browservinduet åbent hele dagen. Du kan åbne andre faner og vinduer uden at logge på igen. Hvis du har brug for at logge på en anden konto, skal du bruge Privat browsing.

- Når hver side er downloadet og åbnet, skal du holde dem åbne ved hjælp af faner. Det er nemt at navigere mellem faner og bruge siden senere på dagen. Opdater kun en side, hvis du har brug for de nyeste data på den pågældende side.

- Hvis det tager for lang tid at åbne en side, skal du stoppe sidedownloaden (tryk på ESC) og derefter opdatere siden (tryk på F5).

- Reducer rundturene til Office 365, når det er muligt. I stedet for at sideopdeling via lister eller biblioteker kan du f.eks. bruge søgning til at finde filer i et stort bibliotek og filtrere på en liste for at få direkte adgang til de ønskede resultater. Du kan også oprette visninger, der minimerer indlæsningstiden for siden. Du kan få flere oplysninger under [Administrer store lister og biblioteker i Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Hvis videoens ydeevne er dårlig, kan du muligvis downloade videoen og se den på din enhed. Der kan være et downloadlink tilgængeligt, eller du kan højreklikke på videolinket og vælge **Gem mål som**.

### <a name="browser-specific"></a>Browserspecifik

Her er nogle forslag til din specifikke browser:

- **Internet Explorer**: Opgrader til Internet Explorer Version 11 eller nyere for at opnå betydelige forbedringer af ydeevnen i forhold til tidligere versioner. Du kan få flere oplysninger i [Fejlfindingsvejledning til Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox**: Du kan få flere oplysninger under [Firefox er langsom eller holder op med at fungere](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari**: Du kan få flere oplysninger under [Apple – Safari](https://www.apple.com/safari/).
- **Chrome**: Du kan finde flere oplysninger i [Chrome Hjælp](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Bedste praksis for brug af Outlook og Outlook Web App

Læsning, skrivning og organisering af mail er en stor del af alles dag. Både Outlook og Outlook Web App (OWA) tilbyder offlinesupport. Brug af en mailapp på din smartphone er et andet nyttigt alternativ. Brug følgende indstillinger, der passer bedst til dine behov:

- Opgrader til den nyeste version af Outlook for at opnå betydelige forbedringer af ydeevnen i forhold til tidligere versioner.

- Outlook Web App kan du oprette offlinemeddelelser, kontakter og kalenderhændelser, der uploades, når OWA næste gang kan oprette forbindelse til Office 365. Du kan få flere oplysninger om, hvordan du konfigurerer og bruger OWA i offlinetilstand, under [Brug Outlook Web App offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook gør det muligt at arbejde i cachelagret tilstand, hvor der automatisk oprettes forbindelse, når det er muligt. Du kan få Outlook downloade hele postkassen eller blot en del af den. Du kan få flere oplysninger under [Slå cachelagret Exchange tilstand](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) til, og [arbejd offline i Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook tilbyder også offlinetilstand. Hvis du vil bruge dette, skal du først konfigurere cachelagret tilstand, så oplysninger fra din konto kopieres ned til din computer. I offlinetilstand forsøger Outlook at oprette forbindelse ved hjælp af send og modtag-indstillingerne, eller når du manuelt indstiller den til at fungere online. Du kan finde flere oplysninger under [Arbejd offline for at undgå gebyrer for dataforbindelser](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282), [Skift indstillinger for afsendelse og modtagelse, når du arbejder offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a), og [Skift fra at arbejde offline til online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Hvis du har en smartphone, kan du bruge den til at triage din mail og kalender via din telefonudbyders netværk.

> [!NOTE]
> Her er nogle retningslinjer for, hvornår du skal bruge Outlook eller OWA. Hvis der ikke er diskplads på enheden, har Outlook et komplet sæt funktioner og fungerer muligvis bedst for dig. Hvis der er problemer med diskpladsen på din enhed, kan du overveje at bruge OWA, som har en delmængde af funktioner, men som også fungerer bedst i en onlinesituation. Du kan selvfølgelig bruge begge dele, fordi de fungerer godt sammen.

## <a name="best-practices-for-using-onedrive-for-business"></a>Bedste praksis for brug af OneDrive for Business

OneDrive for Business er designet fra bunden, så du kan arbejde med dine filer online og offline. Når du har konfigureret den, sker synkroniseringen af ændringer automatisk og pålideligt, uanset hvor og hvornår du foretager dem. Hvis netværket er langsomt, kan du arbejde med offlineversionen af filerne.

Den OneDrive for Business synkroniseringsapp leveres med et SharePoint Online- og Office 365-virksomhedsabonnement, eller du kan [downloade](https://support.microsoft.com/kb/2903984) OneDrive for Business synkroniseringsapp gratis. Denne app er også hurtigere end at bruge **kommandoerne Åbn i Stifinder** eller **Upload**. Du kan få flere oplysninger under [Konfigurer computeren til at synkronisere dine OneDrive for Business filer i Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

Her er nogle yderligere vejledninger i, hvordan du bruger OneDrive for Business-synkroniseringsappen:

- Hvis du synkroniserer et stort bibliotek for første gang, kan du starte synkroniseringen uden for arbejdstiden, f.eks. natten over.
- Du kan bruge funktionen [Stop synkronisering af et bibliotek med funktionen OneDrive for Business app](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) til midlertidigt at stoppe synkroniseringen af opdateringer. Brug dog denne funktion i korte perioder, f.eks. nogle få timer ad gangen, for at undgå at sætte et stort antal opdateringer i kø og for at minimere risikoen for flettekonflikter, hvis flere personer arbejder i det samme dokument.

## <a name="best-practices-for-using-onenote"></a>Bedste praksis for brug af OneNote

Hvert SharePoint teamwebsted har en indbygget OneNote notesbog, og du kan nemt oprette din egen. OneNote er en god måde at indsamle rettidige oplysninger, som du har brug for hver dag for at få udført opgaver. Mange teams bruger f.eks. OneNote som et samlingspunkt for ugentlige møder, projektnoter, ideer, planer og statusrapporter. Du kan organisere disse forskellige oplysninger pænt ved hjælp af sider, sektioner og faner.

Skønheden ved OneNote er, at du kan få adgang til indholdet fra stort set enhver enhed, uanset om det er en stationær computer, en bærbar computer, en tablet eller en smartphone. Og du behøver ikke at bekymre dig om at gemme eller synkronisere, fordi OneNote gør det for dig.

Du kan få flere oplysninger under [Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Bedste praksis for brug af Skype for Business og Lync Online

Følgende er generelle retningslinjer for brug af Skype for Business eller Lync Online, når netværket er langsomt:

- Brug chat, når du kan, fordi det fungerer godt på et langsomt netværk.

- Undgå at foretage telefonopkald via et VPN- eller RAS-forbindelser (Remote Access Service).

- Sørg for, at din lydenhed er godkendt. Du kan få flere oplysninger under [Telefoner og enheder, der er kvalificerede til Microsoft Lync](/skypeforbusiness/lync-cert/ip-phones).

- Når du bruger PowerPoint i en onlinepræsentation, skal du reducere slidenes størrelse og kompleksitet. Du kan få flere oplysninger [under Tips for at forbedre præsentationens ydeevne](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Videoydeevnen afhænger meget af netværkets ydeevne. Undgå at bruge video, hvis netværket er langsomt.

Du kan finde flere oplysninger under [Dårlig lyd- eller videokvalitet i Lync Online](https://support.microsoft.com/kb/2386655), eller hvordan [du foretager fejlfinding af forbindelsesproblemer i Skype for Business](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>Bedste praksis for brug af SharePoint lister

Når du arbejder med listedata offline for at "rense", analysere eller rapportere data, er det en god måde at minimere indvirkningen af et langsomt netværk på. Du kan læse og skrive de fleste lister fra Microsoft Access 2019 og Microsoft Access 2016 ved at linke til dem. Du kan også eksportere en liste til en Excel tabel, hvilket opretter en envejsdataforbindelse mellem den Excel tabel og listen. Få mere at vide om, hvordan du [arbejder offline med tabeller, der er sammenkædet med SharePoint lister](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).

Du kan få flere oplysninger i afsnittet "Mere om administration af store lister" under [Administrer store lister og biblioteker i Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).

## <a name="best-practices-for-customizing-web-pages"></a>Bedste praksis for tilpasning af websider

Når du tilpasser en webside, kan du utilsigtet forårsage dårlig ydeevne på siden. En række faktorer kan have indflydelse, f.eks. sidens kompleksitet og størrelse, hvor mange webdele der tilføjes, hvor mange liste- eller bibliotekselementer der vises i første omgang, og den måde, du koder siden på.

Du kan få flere oplysninger under [Tune SharePoint Online performance](tune-sharepoint-online-performance.md).

## <a name="best-practices-for-using-project-online"></a>Bedste praksis for brug af Project Online

Følgende retningslinjer kan hjælpe med at forbedre netværkets ydeevne.

- Project Online og SharePoint Online kræver synkronisering, hvilket kan være tidskrævende. Hvis dine projektteams har lav omsætning, kan du deaktivere Project synkroniser websted for at forbedre ydeevnen for Project Publicer og Project detaljesider. Begræns Active Directory-synkronisering til grupper af ressourcer, der rent faktisk skal bruge systemet, og overvåg eventuelle tilladelsesproblemer efter synkronisering af store grupper.

- Hvis din organisation bruger projektwebsteder, skal du oprette dem efter behov i stedet for automatisk. Dette fremskynder den første udgivelsesoplevelse og undgår at oprette unødvendige websteder og indhold.

- Project detaljesider (PDP) kan udløse en genberegning af hele projektet og starte arbejdsproceshandlinger, som begge kan være ydelsestunge handlinger. Hvis du vil undgå at udløse to opdateringsprocesser på samme tid på den samme PDP, skal du undgå at opdatere kalenderfelterne (Startdato, Slutdato, Statusdato og Dags dato) og de ikke-planlagte felter (projektnavn, beskrivelse og ejer).

- Reducer antallet af webdele og brugerdefinerede felter, der vises på hver PDP. Opret en dedikeret PDP med de eneste felter, der kræver opdatering for at forbedre belastningen og spare tid.

- Når du bruger OData til rapportering, skal du begrænse mængden af data, du forespørger på på kørselstidspunktet, ved hjælp af filtrering på serversiden.

Du kan få flere oplysninger under [Tune Project Online performance](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).

## <a name="whats-the-best-way-to-report-problems"></a>Hvad er den bedste måde at rapportere problemer på?

Microsoft forbedrer løbende den overordnede ydeevne for Office 365 ved at overvåge netværket, måle båndbredde og ventetid, forbedre indlæsningstiden for sider, reducere disk-I/O, omdesigne sider til at bruge Minimal Download-strategi, føje hardware til datacentre og tilføje flere datacentre. Du kan få flere oplysninger om kontrol af din aktuelle status og problemer med rapportering under [Sådan kontrollerer du Office 365 tjenestetilstand](view-service-health.md).

## <a name="see-also"></a>Se også

[Netværksplanlægning og justering af ydeevne for Office 365](network-planning-and-performance.md)

[principper for Office 365 netværksforbindelser](microsoft-365-network-connectivity-principles.md)

[Administrere Office 365-slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Ofte stillede spørgsmål om Office 365 slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
