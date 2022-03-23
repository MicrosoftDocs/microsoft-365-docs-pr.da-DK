---
title: Bedste fremgangsmåder for brug Office 365 på et langsomt netværk
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: I denne artikel gennemgås de bedste fremgangsmåder, du kan bruge til at Office 365 på et langsomt netværk.
ms.openlocfilehash: 0b3b46bcc28b8c25f363268adfa720f4d1df47b8
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589748"
---
# <a name="best-practices-for-using-office-365-on-a-slow-network"></a>Bedste fremgangsmåder for brug Office 365 på et langsomt netværk

Ville det ikke være rart, hvis din internetforbindelse altid var hurtig og aldrig gik ned? Måske kommer dagen. Men i mellemtiden er der praktiske ting, du kan gøre for at løse et usikkert netværk og stadig få udført dit daglige arbejde. Selvom Office 365 er en skybaseret tjeneste, indeholder den også mange måder at arbejde med dit indhold offline og problemfrit holde dine ændringer synkroniserede. Desuden er det nogle gange mere effektivt at arbejde med indhold offline, blot fordi programmer kører hurtigere, og brugergrænsefladen er mere effektiv. Pointen er følgende: Office 365 giver dig det bedste fra begge verdener. Sådan kan du drage fordel af det.

> [!TIP]
> Vil du se, hvor langsom (eller hurtig) din netværksforbindelse er? Prøv [OOKLA Speed test eller](https://www.speedtest.net/) [Network Speed Test App](https://www.windowsphone.com/store/app/network-speed-test/9b9ae06b-2961-41ef-987d-b09567cffe70).

## <a name="why-is-my-network-so-slow"></a>Hvorfor er mit netværk så langsomt?

Selvom du ikke har kontrol over selve netværkydeevnen, hjælper det at forstå, hvad der foregår i baggrunden. Internettet er enormt komplekst, men der er et par begreber, som kan hjælpe dig med at forstå situationen meget bedre. Hvis du følger de bedste fremgangsmåder i denne artikel, kan det hjælpe dig med at løse problemer med ydeevnen og dermed mindske risikoen for frustration.

### <a name="major-factors-that-affect-network-performance"></a>Overordnede faktorer, der påvirker netværkets ydeevne

![Faktorer for netværkydeevne.](../media/62a94322-3f1a-4d2d-bbdc-2aa0722d2d96.png)

 **Båndbredde og ventetid**: De to vigtigste mål for netværkydeevnen er båndbredde og ventetid:

- Båndbredden er overførselshastighed målt i bit pr. sekund. Jo større, jo bedre. Båndbredden er ligesom et vandrør. Jo større rør, jo mere vand kan det "lægge igennem".

- Ventetid er den tid, det tager for indhold at komme fra en server eller tjeneste til din enhed, og den måles i millisekunder. Jo hurtigere, jo bedre. Ventetid kan skyldes en række faktorer, herunder lav båndbredde, en sparsom forbindelse eller transmissionstid.

 **Almindelige problemer**: Ud over båndbredde og ventetid har andre problemer også indflydelse på netværkets ydeevne og er ofte uforudsigelige. Netværkydeevnen kan variere afhængigt af tidspunktet på dagen eller din fysiske placering. Netværket kan blive til fed, når visse hændelser forekommer, at brugen af internettet sammenftoppes, f.eks. en naturlig katastrofe eller en større offentlig begivenhed. Størrelsen og kompleksiteten af den side, der indlæses, og antallet og størrelsen af filer, der overføres, har direkte indflydelse på ydeevnen. En WiFi-forbindelse kan midlertidigt forringes: Du skal f.eks. oprette en afstemning om et stort møde med tusindvis ved at bede alle om at tweete på samme tid.

 **Overvejelser i forbindelse med et** satellitnetværk: Et satellitnetværk er nyttigt, når et netværks, der er under land, ikke er muligt, f.eks. back country, etnavigationstog eller et eksternt videnskabelig område. Disse netværk er afhængige af satellittter, der er placeret i en geosynkron kredsløb 22.000 km over ækvator. Men en transmission rejser faktisk omkring 30.000 kilometer, så et satellitnetværk har en langsommere ventetid (500 ms eller mere) end et netværk, som lander (20 til 50 ms). Under de bedste omstændigheder vil du muligvis ikke bemærke denne ventetid, men hvis du downloader store filer, streamer videoer og spiller spil, vil du sandsynligvis gøre det. Et andet problem er "regntoning", hvor kraftigt vejr, f.eks. tordenstorme og skybrud, midlertidigt kan afbryde satellitoverførsler.

## <a name="are-you-sure-its-the-network"></a>Er du sikker på, at det er netværket?

Når du oplever problemer med ydeevnen, skal du først sørge for, at enheden ikke er den egentlige årsag til problemet. Der er to ting, du kan gøre, som kan gøre en stor forskel:

- Sørg for, at enheden kører godt, og der ikke er nogen malware på computeren.

- Køb mere hukommelse, hvis det er muligt. Den mest enkle og ofte mest effektive måde at forbedre ydeevnen på din enhed er at tilføje mere hukommelse. Det er især nyttigt, når du arbejder med store filer og videoer.

Du kan finde flere oplysninger [Windows ydeevne og vedligeholdelse og](https://windows.microsoft.com/windows/performance-maintenance-help#performance-maintenance-help) [Tips for at forbedre pc'ens Windows 10](https://support.microsoft.com/help/4002019/windows-10-improve-pc-performance).

## <a name="best-practices-for-using-your-browser"></a>Bedste fremgangsmåder for brug af din browser

Din browser er din gateway til Office 365, så den kan påvirke ydeevnen, især med den tid, det tager at indlæse en side, og hvor ofte du går til Office 365-tjenesten.

### <a name="browsers-in-general"></a>Browsere generelt

Her er nogle generelle forslag til browsere:

- Deaktiver tilføjelser i browseren, der kan påvirke ydeevnen, eller som du ikke rigtigt har brug for.

- Øg cachestørrelsen for dine midlertidige internetfiler.

- Når du har logget på din arbejds- eller skolekonto, skal du holde browservinduet åbent hele dagen. Du kan åbne andre faner og vinduer uden at logge på igen. Hvis du skal logge på en anden konto, skal du bruge Privat browsing.

- Når hver side er hentet og åbnet, skal du holde dem åbne ved hjælp af faner. Det er nemt at navigere mellem fanerne og bruge siden senere på dagen. Opdater kun en side, hvis du har brug for de seneste data på den pågældende side.

- Hvis det tager for lang tid at åbne en side, skal du stoppe overførslen af siden (tryk på ESC) og derefter opdatere siden (tryk på F5).

- Når det er muligt, kan du reducere turene til Office 365. I stedet for at sideindde igennem lister eller biblioteker kan du bruge søg til at finde filer i et stort bibliotek og filtrere en liste for at komme direkte til de ønskede resultater. Du kan også oprette visninger, der minimerer sideindlæsningstiden. Få mere at vide under [Administrer store lister og biblioteker i Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784#BKMK_PAGES).

- Hvis ydeevnen for videoer er dårlig, kan du muligvis hente videoen og se den på din enhed. Der kan muligvis være et downloadlink, eller du kan muligvis højreklikke på videolinket og vælge **Gem destination som**.

### <a name="browser-specific"></a>Browserspecifik

Her er nogle forslag til din specifikke browser:

- **Internet Explorer**: Opgrader til Internet Explorer version 11 eller nyere for betydelige forbedringer af ydeevnen i forhold til tidligere versioner. Du kan finde flere oplysninger [i Fejlfindingsvejledning til Internet Explorer](https://support.microsoft.com/help/2437121/troubleshooting-guide-for-internet-explorer-when-you-access-office-365).
- **FireFox**: Få mere at vide under [Firefox er langsom eller holder op med at fungere](https://support.mozilla.org/products/firefox/fix-problems/slowness-or-hanging).
- **Safari**: Du kan finde flere oplysninger i [Apple – Safari](https://www.apple.com/safari/).
- **Chrome**: Du kan finde flere oplysninger i [Chrome Hjælp](https://support.google.com/chrome/?hl=en).

## <a name="best-practices-for-using-outlook-and-outlook-web-app"></a>Bedste fremgangsmåder for brug af Outlook og Outlook Web App

At læse, skrive og organisere mail er en stor del af alles hverdag. Både Outlook og Outlook Web App (OWA) tilbyder offlinesupport. Et andet nyttigt alternativ er at bruge en mailapp på din smartphone. Brug følgende indstillinger, der passer bedst til dine behov:

- Opgrader til den nyeste version af Outlook for betydelige forbedringer af ydeevnen i forhold til tidligere versioner.

- Outlook Web App kan du oprette offlinemeddelelser, -kontakter og -begivenheder i kalenderen, som overføres, næste gang OWA kan oprette forbindelse til Office 365. Du kan finde flere oplysninger om at konfigurere og bruge OWA i offlinetilstand under [Brug Outlook Web App offline](https://support.office.com/article/3214839c-0604-4162-8a97-6856b4c27b36).

- Outlook kan du arbejde i cachelagret tilstand, hvor der automatisk oprettes forbindelse, når det er muligt. Du kan få Outlook at downloade hele postkassen eller kun en del af den. Du kan finde flere oplysninger [i Slå Cachelagret Exchange-tilstand](https://support.office.com/article/7885af08-9a60-4ec3-850a-e221c1ed0c1c) til [og Arbejd offline Outlook](https://support.office.com/article/f3a1251c-6dd5-4208-aef9-7c8c9522d633).

- Outlook også en offlinetilstand. Hvis du vil bruge denne, skal du først konfigurere cachelagret tilstand, så oplysninger fra din konto kopieres ned til computeren. I offlinetilstand forsøger Outlook oprette forbindelse ved hjælp af send og modtag-indstillingerne, eller når du manuelt indstiller den til at arbejde online. Du kan finde flere oplysninger i [Arbejde offline](https://support.office.com/article/827fe51f-5609-4062-82b4-3578057f9282) for at undgå dataforbindelsesgebyrer, Ændre indstillinger for send og modtag, når du arbejder [offline](https://support.office.com/article/f681ec10-cb14-40cb-8709-1909a13c304a) og Skift fra [at arbejde offline til online](https://support.office.com/article/2460e4a8-16c7-47fc-b204-b1549275aac9).

- Hvis du har en smartphone, kan du bruge den til at triage din mail og kalender via din telefonudbyders netværk.

> [!NOTE]
> Her er nogle retningslinjer for, hvornår du skal bruge Outlook eller OWA. Hvis der ikke er problemer med diskpladsen på din enhed, Outlook har et komplet sæt funktioner og fungerer muligvis bedst for dig. Hvis der er problemer med diskpladsen på din enhed, kan du overveje at bruge OWA, som har en del af funktionerne, men også fungerer bedst i en onlinesituation. Du kan selvfølgelig bruge begge, fordi de fungerer godt sammen.

## <a name="best-practices-for-using-onedrive-for-business"></a>Bedste fremgangsmåder for brug af OneDrive for Business

OneDrive for Business er udviklet fra bunden til at arbejde med dine filer online og offline. Når du konfigurerer den, sker synkronisering af ændringer automatisk og pålideligt, uanset hvor og hvornår du foretager dem. Hvis netværket er langsomt, kan du arbejde med offlineversionen af filerne.

Synkroniseringsappen OneDrive for Business leveres med et SharePoint Online- og Office 365 Business-abonnement, eller du kan downloade OneDrive for Business-synkroniseringsappen gratis.[](https://support.microsoft.com/kb/2903984) Denne app er også hurtigere end at bruge **kommandoerne Åbn** **i Upload** Stifinder. Få mere at vide under [Konfigurer computeren til at synkronisere dine OneDrive for Business filer Office 365](https://support.office.com/article/23e1f12b-d896-4cb1-a238-f91d19827a16).

Her er nogle yderligere vejledninger til brug af OneDrive for Business-synkroniseringsappen:

- Hvis du synkroniserer et stort bibliotek for første gang, skal du starte synkroniseringen uden for arbejdstiden, f.eks. om natten.
- Du kan bruge funktionen [Stop synkroniseringen af et bibliotek OneDrive for Business-appen](https://support.office.com/article/a7e41f1f-3a98-4ca7-9443-f10250688330) til midlertidigt at stoppe synkroniseringen af opdateringer. Du kan dog bruge denne funktion i korte perioder, f.eks. et par timer ad gangen, for at undgå at skulle stå i kø med et stort antal opdateringer og for at minimere risikoen for flettekonflikter, hvis flere personer arbejder på det samme dokument.

## <a name="best-practices-for-using-onenote"></a>Bedste fremgangsmåder for brug af OneNote

Alle SharePoint-teamwebsteder har en indbygget OneNote, og du kan nemt oprette din egen. OneNote er en god metode til at indsamle rettidige oplysninger, som du skal bruge hver dag for at få opgaverne udført. Eksempelvis bruger mange teams OneNote samlingspunkt for ugentlige møder, projektnoter, ideer, planer og statusrapporter. Du kan nemt organisere disse uensartede oplysninger ved hjælp af sider, sektioner og faner.

Det smarte ved OneNote er, at du kan få adgang til indholdet fra næsten enhver enhed, uanset om det er en stationær computer, en bærbar computer, en tablet eller en smartphone. Og du behøver ikke at bekymre dig om at gemme eller synkronisere, da det OneNote det for dig.

Du kan finde flere oplysninger [under Microsoft OneNote](https://office.microsoft.com/onenote).

## <a name="best-practices-for-using-skype-for-business-and-lync-online"></a>Bedste fremgangsmåder for brug Skype for Business og Lync Online

Følgende er generelle retningslinjer for brug af Skype for Business Lync Online, når netværket er langsomt:

- Brug chat, når du kan, da det fungerer godt på et langsomt netværk.

- Undgå at foretage telefonopkald via et virtuelt privat netværk (VPN) eller fjernadgangstjeneste (RAS).

- Kontrollér, at din lydenhed er godkendt. Du kan finde flere oplysninger i [Telefoner og enheder, der kan bruge Microsoft Lync](/skypeforbusiness/lync-cert/ip-phones).

- Når du PowerPoint i en onlinepræsentation, kan du reducere størrelsen og kompleksiteten af slides. Du kan finde flere [oplysninger Tips om forbedring af ydeevnen for din præsentation](https://support.office.com/article/34c82835-5f23-4bf0-98cc-72235bbd2949).

- Ydeevnen for video er meget afhængig af netværkets ydeevne. Undgå at bruge video, hvis netværket er langsomt.

Du kan finde flere oplysninger [i Dårlig lyd- eller videokvalitet i Lync Online](https://support.microsoft.com/kb/2386655), eller hvordan du foretager fejlfinding [af forbindelsesproblemer Skype for Business](https://support.office.com/article/troubleshoot-connection-issues-in-skype-for-business-ca302828-783f-425c-bbe2-356348583771).

## <a name="best-practices-for-using-sharepoint-lists"></a>Bedste fremgangsmåder for brug af SharePoint lister

Arbejde med listedata offline for at "rense", analysere eller rapportere data er en god måde at minimere effekten af et langsomt netværk. Du kan læse og skrive de fleste lister fra Microsoft Access 2019 og Microsoft Access 2016 ved at sammenkæde dem. Du kan også eksportere en liste til Excel Tabel, som opretter en envejsdataforbindelse mellem Excel og listen. Få mere at vide [om at arbejde offline med tabeller, der er kædet SharePoint lister](https://support.office.com/article/work-offline-with-tables-that-are-linked-to-sharepoint-lists-5d66594a-6176-4a25-a198-320f13ccf41e).

Du kan finde flere oplysninger i afsnittet "Mere om administration af store lister" i Administrer store [lister og biblioteker Office 365](https://support.office.com/article/b4038448-ec0e-49b7-b853-679d3d8fb784).

## <a name="best-practices-for-customizing-web-pages"></a>Bedste fremgangsmåder for tilpasning af websider

Når du tilpasser en webside, kan det utilsigtet medføre dårlig ydeevne for siden. En række faktorer kan påvirke siders kompleksitet og størrelse, hvor mange webdele, der tilføjes, hvor mange liste- eller bibliotekselementer, der i første omgang vises, og den måde, du koder siden på.

Du kan finde flere oplysninger [i Finjuster SharePoint onlineydeevne](tune-sharepoint-online-performance.md).

## <a name="best-practices-for-using-project-online"></a>Bedste fremgangsmåder for brug af Project Online

Følgende retningslinjer kan hjælpe med at forbedre netværkets ydeevne.

- Project Online og SharePoint Online kræver synkronisering, som kan være tidskrævende. Hvis der ikke sker den store udskiftning i dine projektgrupper, kan du Project synkronisering af websteder for at forbedre ydeevnen Project Publicer Project Detaljersider. Begræns Active Directory-synkronisering til grupper af ressourcer, der faktisk har brug for at bruge systemet, og hold øje med potentielle problemer med tilladelser efter synkroniseringen af store grupper.

- Hvis din organisation bruger projektwebsteder, kan du oprette dem efter behov i stedet for automatisk. Dette får den første udgivelse til at gå hurtigere og undgår oprettelse af unødvendige websteder og indhold.

- Project detaljesider (PDP) kan udløse en genberegning af hele projektet og starte arbejdsproceshandlinger, som kan være krævende for ydeevnen. Undgå at opdatere kalenderfelterne (Startdato, Slutdato, Statusdato og Dags dato) og ikke-planlagte felter (projektnavn, beskrivelse og ejer) for at undgå at udløse to opdateringsprocesser på samme tid på den samme projektdedp.

- Reducer antallet af webdele og brugerdefinerede felter, der vises på hver PDP. Opret en dedikeret PDP med de eneste felter, der kræver opdatering, for at forbedre indlæsningen og spare tid.

- Når du bruger OData til rapportering, kan du begrænse mængden af data, du forespørger om, på kørselstidspunktet ved hjælp af filtrering på serversiden.

Du kan finde flere oplysninger [i finjustere ydeevnen Project Online ydeevnen](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c).

## <a name="whats-the-best-way-to-report-problems"></a>Hvad er den bedste måde at rapportere problemer på?

Microsoft forbedrer kontinuerligt den overordnede ydeevne for Office 365 ved at overvåge netværket, måle båndbredde og ventetid, forbedre sideindlæsningstiden, reducere disk-I/O, ændre siders design til brug af Minimal downloadstrategi, føje hardware til datacentre og tilføje flere datacentre. Du kan finde flere oplysninger om, hvordan du kontrollerer din aktuelle status og rapporterer problemer, [under Sådan Office 365 kontrollere tjenestetilstanden](view-service-health.md).

## <a name="see-also"></a>Se også

[Netværksplanlægning og justering af ydeevnen for Office 365](network-planning-and-performance.md)

[Office 365 principper for netværksforbindelse](microsoft-365-network-connectivity-principles.md)

[Administrere Office 365 slutpunkter](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)

[Office 365 ofte stillede spørgsmål om slutpunkter](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
