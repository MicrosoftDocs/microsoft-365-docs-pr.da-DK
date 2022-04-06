---
title: Filløse trusler
ms.reviewer: ''
description: Få mere at vide om kategorierne af filløse trusler og malware, der lever af jorden
keywords: fileless, fileless malware, living off the land, lolbins, amsi, behavior monitoring, memory scanning, boot sector protection, security, malware, Windows Defender ATP, antivirus, AV, Microsoft Defender ATP, next-generation protection
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 4db82cfc20bb1e27b2ef9a75793170c451c3868a
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665332"
---
# <a name="fileless-threats"></a>Filløse trusler

Hvad er filløse trusler? Udtrykket "fileless" antyder, at en trussel ikke findes i en fil, f.eks. en bagdør, der kun findes i en maskines hukommelse. Der er dog ingen definition for filuafhængig malware. Udtrykket bruges bredt, og nogle gange til at beskrive malware familier, der er afhængige af filer til at fungere.

Angreb omfatter [flere faser](https://attack.mitre.org/wiki/ATT&CK_Matrix) for funktioner som eksekvering, vedholdenhed eller informationstyveri. Nogle dele af angrebskæden kan være filløse, mens andre kan involvere filsystemet i en eller anden form.

For klarhedens skyld grupperes filløse trusler i forskellige kategorier.

![Omfattende diagram over filuafhængig malware.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Figur 1. Omfattende diagram over filuafhængig malware*

Filløse trusler kan klassificeres ved deres indgangspunkt, hvilket angiver, hvordan filuafhængig malware kan modtage på en maskine. De kan nå frem via en udnyttelse, gennem kompromitteret hardware eller via regelmæssig udførelse af applikationer og scripts.

Derefter skal du angive formularen til indgangspunkt. Udnyttelser kan f.eks. være baseret på filer eller netværksdata, PCI-eksterne enheder er en type hardwarevektor, og scripts og eksekverbare filer er underkategorier af udførelsesvektoren.

Endelig klassificere værten for infektionen. Et Flash-program kan f.eks. indeholde en række trusler, f.eks. en udnyttelse, en simpel eksekverbar og skadelig firmware fra en hardwareenhed.

Klassificering hjælper dig med at opdele og kategorisere de forskellige former for filløse trusler. Nogle er mere farlige, men også vanskeligere at implementere, mens andre er mere almindeligt anvendte, selv om (eller netop på grund af) ikke er meget avancerede.

Fra denne kategorisering kan du indsamle tre hovedtyper af filløse trusler baseret på, hvor meget fingeraftryk de kan efterlade på inficerede maskiner.

## <a name="type-i-no-file-activity-performed"></a>Type I: Der blev ikke udført nogen filaktivitet

En fuldt filløs malware kan betragtes som en, der aldrig kræver at skrive en fil på disken. Hvordan ville sådan malware inficere en maskine i første omgang? Et eksempel er, hvor en destinationscomputer modtager skadelige netværkspakker, der udnytter sårbarheden i EternalBlue. Sårbarheden gør det muligt at installere DoublePulsar-bagdøren, som ender med kun at være i kernehukommelsen. I dette tilfælde er der ingen fil eller nogen data, der er skrevet på en fil.

En kompromitteret enhed kan også have skadelig kode, der skjules i enhedens firmware (f.eks. en BIOS), en ekstern USB-enhed (f.eks. BadUSB-angrebet) eller i firmwaren på et netværkskort. Alle disse eksempler kræver ikke, at en fil på disken køres, og de kan teoretisk set kun leve i hukommelsen. Den skadelige kode ville overleve genstart, omformatering af disken og geninstallation af operativsystemet.

Infektioner af denne type kan være særligt svære at opdage, fordi de fleste antivirusprodukter ikke har mulighed for at inspicere firmware. I tilfælde, hvor et produkt har mulighed for at inspicere og opdage skadelig firmware, er der stadig betydelige udfordringer forbundet med afhjælpning af trusler på dette niveau. Denne type filløs malware kræver et højt niveau af sofistikeret og afhænger ofte af bestemt hardware- eller softwarekonfiguration. Det er ikke en angrebsvektor, der let og pålideligt kan udnyttes. Mens farlige, trusler af denne type er ualmindelige og ikke praktisk for de fleste angreb.

## <a name="type-ii-indirect-file-activity"></a>Type II: Indirekte filaktivitet

Der er andre måder at malware kan opnå filløs tilstedeværelse på en maskine uden at kræve en betydelig teknisk indsats. Filløs malware af denne type skriver ikke direkte filer på filsystemet, men de kan ende med at bruge filer indirekte. Med [Poshspy-bagdør-angribere](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) installerede f.eks. en skadelig PowerShell-kommando i WMI-lageret og konfigurerede et WMI-filter til at køre kommandoen med jævne mellemrum.

Det er muligt at udføre en sådan installation via kommandolinjen uden at kræve, at der allerede findes en bagdør i filen. Malwaren kan installeres og teoretisk køre uden nogensinde at røre filsystemet. WMI-lageret gemmes dog på en fysisk fil i et centralt lagerområde, der administreres af CIM Object Manager, og indeholder normalt legitime data. Selvom infektionskæden teknisk set bruger en fysisk fil, betragtes den som et filløst angreb, fordi WMI-lageret er en multifunktionel databeholder, der ikke kan registreres og fjernes.

## <a name="type-iii-files-required-to-operate"></a>Type III: Filer, der kræves for at fungere

Nogle malware kan have en slags filløs vedholdenhed, men ikke uden at bruge filer til at fungere. Et eksempel på dette scenarie er Kovter, som opretter en shell open verb-handler i registreringsdatabasen for et tilfældigt filtypenavn. Åbning af en fil med et sådant filtypenavn vil føre til udførelse af et script via det legitime værktøj mshta.exe.

![Billede af Kovters registreringsdatabasenøgle.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Figur 2. Kovters registreringsdatabasenøgle*

Når det åbne verbum aktiveres, startes den tilknyttede kommando fra registreringsdatabasen, hvilket resulterer i udførelse af et lille script. Dette script læser data fra en anden registreringsdatabasenøgle og udfører dem, hvilket igen fører til indlæsning af den endelige nyttedata. Men for at udløse det åbne verbum i første omgang skal Kovter slippe en fil med samme filtypenavn, der er målrettet af verbet (i eksemplet ovenfor er filtypenavnet .bbf5590fd). Den skal også angive en automatisk kørselsnøgle, der er konfigureret til at åbne en sådan fil, når computeren starter.

Kovter betragtes som en filløs trussel, fordi filsystemet ikke er til praktisk brug. Filerne med tilfældige udvidelser indeholder tilfældige data, der ikke kan bruges til at bekræfte tilstedeværelsen af truslen. De filer, der lagrer registreringsdatabasen, er objektbeholdere, der ikke kan registreres og slettes, hvis der findes skadeligt indhold.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Kategorisering af filløse trusler af infektionsvært

Efter at have beskrevet de brede kategorier kan vi nu grave ned i detaljerne og give en opdeling af infektionsværterne. Denne omfattende klassificering dækker panoramaet over det, der normalt kaldes filløs malware. Det driver vores bestræbelser på at forske i og udvikle nye beskyttelsesfunktioner, der neutraliserer klasser af angreb og sikrer, at malware ikke får overtaget i våbenkapløbet.

### <a name="exploits"></a>Udnytter

**Filbaseret** (Type III: eksekverbar, Flash, Java, dokumenter): En indledende fil kan udnytte operativsystemet, browseren, Java-programmet, Flash-programmet osv. til at udføre en shellcode og levere en nyttedata i hukommelsen. Mens nyttedataene er filløse, er den indledende postvektor en fil.

**Netværksbaseret** (Type I): En netværkskommunikation, der udnytter en sårbarhed i destinationsmaskinen, kan opnå kodeudførelse i forbindelse med et program eller kernen. Et eksempel er WannaCry, som udnytter en tidligere fast sårbarhed i SMB-protokollen til at levere en bagdør i kernehukommelsen.

### <a name="hardware"></a>Hardware

**Enhedsbaseret** (type I: netværkskort, harddisk): Enheder som harddiske og netværkskort kræver chipsæt og dedikeret software til at fungere. Software, der findes og kører i chipsættet på en enhed, kaldes firmware. Selvom en kompleks opgave, firmwaren kan være inficeret med malware, som [Equation spionage gruppe er blevet fanget gør](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**CPU-baseret** (type I): Moderne CPU'er er komplekse og kan omfatte undersystemer, der kører firmware med henblik på administration. En sådan firmware kan være sårbar over for kapring og tillade udførelse af skadelig kode, der ville fungere fra CPU'en. I december 2017 rapporterede to forskere en sårbarhed, der kan gøre det muligt for hackere at udføre kode inde i [management engine (ME),](https://en.wikipedia.org/wiki/Intel_Management_Engine) der findes i enhver moderne CPU fra Intel. I mellemtiden er hackergruppen PLATINUM blevet observeret for at have mulighed for at bruge Intels [AMT (Active Management Technology)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) til at udføre [usynlig netværkskommunikation](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/) og omgå det installerede operativsystem. ME og AMT er grundlæggende autonome mikrocomputere, der lever inde i CPU'en, og som fungerer på et meget lavt niveau. Da disse teknologier har til formål at sikre fjernstyring, har de direkte adgang til hardware, er uafhængige af operativsystemet og kan køre, selvom computeren er slukket.

Ud over at være sårbar på firmwareniveau kan CPU'er fremstilles med bagdøre indsat direkte i hardwarekredsløbet. Dette angreb er blevet [undersøgt og vist sig muligt](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) i fortiden. Det er blevet rapporteret, at visse modeller af x86-processorer indeholder en sekundær integreret RISC-lignende CPU-kerne, der [effektivt kan give en bagdør](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) , hvorigennem regelmæssige programmer kan få privilegeret udførelse.

**USB-baseret** (Type I): USB-enheder af alle slags kan omprogrammeres med skadelig firmware, der er i stand til at interagere med operativsystemet på nefarious måder. [BadUSB-teknikken](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) gør det f.eks. muligt for en omprogrammeret USB-pind at fungere som et tastatur, der sender kommandoer til maskiner via tastetryk eller som et netværkskort, der kan omdirigere trafik efter forgodtbehold.

**BIOS-baseret** (type I): En BIOS er en firmware, der kører i et chipsæt. Den udføres, når en computer er tændt, initialiserer hardwaren og overfører derefter styringen til startsektoren. BIOS er en vigtig komponent, der kører på et lavt niveau og kører før startsektoren. Det er muligt at omprogrammere BIOS-firmwaren med skadelig kode, som det tidligere er sket med [Mebromi rootkit](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Hypervisorbaseret** (Type I): Moderne CPU'er understøtter hypervisorhardware, så operativsystemet kan oprette robuste virtuelle maskiner. En virtuel maskine kører i et lukket, simuleret miljø og er teoretisk set uvidende om emulering. En malware, der overtager en maskine, kan implementere en lille hypervisor for at skjule sig uden for det kørende operativsystems rige. Malware af denne type er blevet theorized i fortiden, og i sidste ende reelle hypervisor rootkits [er blevet observeret](http://seclists.org/fulldisclosure/2017/Jun/29), selv om få er kendt for at dato.

### <a name="execution-and-injection"></a>Udførelse og injektion

**Filbaseret** (Type III: eksekverbare filer, DLL'er, LNK-filer, planlagte opgaver): Dette er standardkørselsvektoren. En simpel eksekverbar kan startes som en første fase malware til at køre en ekstra nyttedata i hukommelsen, eller indsprøjtes i andre legitime kørende processer.

**Makrobaseret** (type III: Office dokumenter): [VBA-sproget](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) er et fleksibelt og effektivt værktøj, der er udviklet til at automatisere redigeringsopgaver og føje dynamiske funktioner til dokumenter. Som sådan kan det misbruges af hackere til at udføre ondsindede handlinger som afkodning, kørsel eller indsprøjtning af en eksekverbar nyttedata eller endda implementere en hel ransomware, som i [tilfælde af qkG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/). Makroer udføres i forbindelse med en Office proces (f.eks. Winword.exe) og implementeres på et scriptsprog. Der er ingen binær eksekverbar fil, som et antivirusprogram kan undersøge. Selvom Office apps kræver eksplicit samtykke fra brugeren til at udføre makroer fra et dokument, bruger hackere socialtekniske teknikker til at narre brugere til at tillade makroer at køre.

**Scriptbaseret** (Type II: fil, tjeneste, registreringsdatabase, WMI-lager, shell): JavaScript-, VBScript- og PowerShell-scriptsprogene er som standard tilgængelige på Windows platforme. Scripts har de samme fordele som makroer, de er tekstfiler (ikke binære eksekverbare filer) og kører inden for konteksten af fortolkeren (f.eks. wscript.exe, powershell.exe), som er en ren og legitim komponent. Scripts er alsidige og kan køres fra en fil (ved at dobbeltklikke på dem) eller udføres direkte på kommandolinjen i en fortolker. Hvis du kører på kommandolinjen, kan malware kode skadelige scripts som autostart-tjenester i [registreringsdatabasenøgler til automatisk kørsel](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) som [WMI-hændelsesabonnementer](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) fra WMI-lageret. En hacker, der har fået adgang til en inficeret maskine, kan desuden angive scriptet i kommandoprompten.

**Diskbaseret** (Type II: Startpost): Startposten er den første sektor på en disk eller diskenhed og indeholder den eksekverbare kode, der kræves for at starte startprocessen for operativsystemet. Trusler som [Petya](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) er i stand til at inficere Boot Record ved at overskrive det med skadelig kode. Når maskinen startes op, får malwaren straks kontrol. Startposten findes uden for filsystemet, men den er tilgængelig for operativsystemet. Moderne antivirusprodukter har mulighed for at scanne og gendanne dem.

## <a name="defeating-fileless-malware"></a>Besejre filuafhængig malware

Hos Microsoft overvåger vi aktivt sikkerhedslandskabet for at identificere nye trusselstendenser og udvikle løsninger til at afhjælpe klasser af trusler. Vi instrument holdbar beskyttelse, der er effektive mod en bred vifte af trusler. Via AMSI (AntiMalware Scan Interface), overvågning af funktionsmåde, hukommelsesscanning og startsektorbeskyttelse kan [Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) inspicere filløse trusler selv med kraftig forsnæring. Teknologier til maskinel indlæring i cloudmiljøet giver os mulighed for at skalere disse beskyttelser mod nye og nye trusler.

Hvis du vil vide mere, kan du læse: [Ude af syne, men ikke usynlig: Besejre filløs malware med adfærdsovervågning, AMSI og next-gen AV](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Yderligere ressourcer og oplysninger

Få mere at vide om, hvordan [du udruller trusselsbeskyttelsesfunktioner på tværs af Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
