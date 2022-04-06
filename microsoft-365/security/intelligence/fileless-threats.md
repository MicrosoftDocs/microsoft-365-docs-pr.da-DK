---
title: Filløse trusler
ms.reviewer: ''
description: Få mere at vide om kategorierne for filløse trusler og malware, der lever uden for landet
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
ms.openlocfilehash: 97545714ff468c7be238585ab5d137a1ac93a5f9
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705915"
---
# <a name="fileless-threats"></a>Filløse trusler

Hvad er egentlige trusler uden filer? Udtrykket "filløs" antyder, at en trussel ikke kommer i en fil, f.eks. en backdoor, der kun findes i hukommelsen på en computer. Der er dog ingen definition for filløs malware. Ordet bruges bredt og nogle gange til at beskrive malwarefamilier, der er afhængige af filer for at fungere.

Angreb involverer [flere trin](https://attack.mitre.org/wiki/ATT&CK_Matrix) til funktioner som eksekvering, vedholdenhed eller oplysningstyveri. Nogle dele af angrebskæden kan være filløse, mens andre kan involvere filsystemet i en eller anden form.

For at gøre det mere overskueligt er filløse trusler grupperet i forskellige kategorier.

![Omfattende diagram over malware uden filer.](../../media/security-intelligence-images/fileless-malware.png)<br>
*Figur 1. Omfattende diagram over malware uden filer*

Filløse trusler kan klassificeres ud fra deres indgangspunkt, hvilket angiver, hvordan filløs malware kan modtages på en computer. De kan komme via en udnyttelse, via kompromitteret hardware eller via almindelig udførelse af programmer og scripts.

Dernæst skal du vise formularen for indgangspunkt. Udnyttelse kan f.eks. være baseret på filer eller netværksdata, AFRTABEL eksterne enheder er en type hardwarevektor, og scripts og eksekverbare filer er underkategorier i eksekveringsvektoren.

Til sidst skal du klassificere værten for denne virus. Eksempelvis kan et Flash-program indeholde en række forskellige trusler som f.eks. en udnyttelse, en simpel eksekverbar og skadelig firmware fra en hardwareenhed.

Klassificering hjælper dig med at inddele og kategorisere de forskellige slags trusler uden filer. Nogle er mere farlige, men også sværere at implementere, mens andre mere almindeligt anvendes på trods af (eller præcis på grund af) ikke er meget avanceret.

Fra denne kategorisering kan du indsamle tre primære typer af filløse trusler baseret på, hvor meget fingeraftryk de kan efterlade på inficeret computere.

## <a name="type-i-no-file-activity-performed"></a>Type I: Der blev ikke udført nogen filaktivitet

Malware uden filer kan betragtes som malware, der aldrig kræver, at du skriver en fil på disken. Hvordan kan sådanne malware inficere en maskine i første omgang? Et eksempel er, hvor en destinationscomputer modtager ondsindede netværkspakker, der udnytter sikkerhedsrisikoen AttlBlue. Sikkerhedsrisikoen tillader installation af DoublePulsar-backdooren, der kun bor i kernehukommelsen. I dette tilfælde er der ingen fil eller nogen data, der er skrevet på en fil.

En kompromitteret enhed kan også have en skadelig kode, der skjules i enhedens firmware (f.eks. en DVS.), en USB-ekstern enhed (f.eks. BadUSB-angreb) eller i et netværkskorts firmware. Alle disse eksempler kræver ikke, at der kører en fil på disken, og de kan teoretisk kun findes i hukommelsen. Den skadelige kode vil stadig kunne genstartes, diskformatering og geninstallationer af operativsystemet.

Inpatienser af denne type kan være særligt svære at registrere, fordi de fleste antivirusprodukter ikke har mulighed for at undersøge firmware. I tilfælde hvor et produkt har mulighed for at undersøge og registrere skadelig firmware, er der stadig betydelige udfordringer forbundet med afhjælpning af trusler på dette niveau. Denne type filløs malware kræver høj grad af sofistikerede og afhænger ofte af en bestemt hardware- eller softwarekonfiguration. Det er ikke en angrebsvektor, der kan udnyttes nemt og pålideligt. Selvom det er farligt, er trusler af denne type ualmindelige og ikke praktiske i forbindelse med de fleste angreb.

## <a name="type-ii-indirect-file-activity"></a>Type II: Indirekte filaktivitet

Malware kan på andre måder opnå filløs tilstedeværelse på en computer uden brug af en større teknisk indsats. Fileless malware of this type doesn't directly write files on the file system, but they can end up using files indirectly. Med [poshspy-backdoor-hackere](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) eksempelvis installeret en ondsindet PowerShell-kommando i WMI-lageret og konfigureret et WMI-filter til at køre kommandoen med jævne mellemrum.

Det er muligt at udføre en sådan installation via kommandolinjen, uden at der kræves en backdoor for allerede at være på filen. Malwaren kan installeres og teoretisk køres uden nogensinde at røre filsystemet. Men WMI-lageret gemmes på en fysisk fil i et centralt lagringsområde, der administreres af CIM-objektstyringen, og indeholder normalt legitime data. Selvom inficeret kæde rent teknisk bruger en fysisk fil, betragtes den som et filløst angreb, fordi WMI-lageret er en flerformåls-databeholder, der ikke kan registreres og fjernes.

## <a name="type-iii-files-required-to-operate"></a>Type III: Filer, der er nødvendige for at kunne fungere

Nogle malware kan have en slags filløs vedholdenhed, men ikke uden at bruge filer til at betjene. Et eksempel på dette scenarie er Kovter, som opretter en åben verbalbehandler til shell i registreringsdatabasen for et tilfældigt filtypenavn. Hvis du åbner en fil med et sådant filtypenavn, vil det føre til udførelse af et script via det legitime mshta.exe.

![Billede af Kovters registreringsdatabasenøgle.](../../media/security-intelligence-images/kovter-reg-key.png)<br>
*Figur 2. Kovters registreringsdatabasenøgle*

Når det åbne verbum aktiveres, startes den tilknyttede kommando fra registreringsdatabasen, hvilket resulterer i udførelse af et lille script. Dette script læser data fra en yderligere registreringsdatabasenøgle og udfører dem, hvilket igen fører til indlæsning af den endelige nyttedata. Men for at udløse det åbne verbum i første omgang, skal Kovter slippe en fil med samme filtypenavn målrettet af verbet (i eksemplet ovenfor er filtypenavnet .bbf5590fd). Den skal også indstille en tast til automatisk kør, som er konfigureret til at åbne en sådan fil, når computeren starter.

Kovter betragtes som en filløs trussel, fordi filsystemet ikke er til praktisk brug. Filer med tilfældige udvidelser indeholder uønskede data, der ikke kan bruges til at bekræfte tilstedeværelsen af truslerne. De filer, der gemmer registreringsdatabasen, er beholdere, der ikke kan registreres og slettes, hvis skadeligt indhold findes.

## <a name="categorizing-fileless-threats-by-infection-host"></a>Kategoriser filless threats by infection host

Når vi har beskrevet de generelle kategorier, kan vi nu gå ned i detaljerne og give en beskrivelse af værtsnværterne for på denne måde. Denne omfattende klassificering dækker panoramabilledet af det, der normalt kaldes filløs malware. Den driver vores bestræbelser på at undersøge og udvikle nye beskyttelsesfunktioner, der neutraliserer klasser af angreb og sikrer, at malware ikke får det store inden for armene.

### <a name="exploits"></a>Exploits

Filbaseret (Type III: eksekverbar fil, Flash, Java, dokumenter): En indledende fil kan udnytte operativsystemet, browseren, **Java-programmet, Flash-programmet** osv. til at udføre en shellcode og levere en nyttedata i hukommelsen. Mens nyttedata er filløse, er den indledende indgangsvektor en fil.

**Netværksbaseret** (Type I): En netværkskommunikation, der udnytter en sikkerhedsrisiko på destinationscomputeren, kan opnå udførelse af kode i forbindelse med et program eller kerne. Et eksempel er WannaCry, der udnytter en tidligere fast sikkerhedsrisiko i SMB-protokollen til at levere en backdoor i kernehukommelsen.

### <a name="hardware"></a>Hardware

**Enhedsbaseret** (Type I: netværkskort, harddisk): Enheder som harddiske og netværkskort kræver, at chipsæt og dedikeret software fungerer. Software, der bor og kører i chipset på en enhed, kaldes firmware. Selvom det er en kompleks opgave, kan firmware blive inficeret med malware, som [gruppen Equation e opgave har været i gang med](https://www.kaspersky.com/blog/equation-hdd-malware/7623/).

**CPU-baseret** (Type I): Moderne CPU'er er komplekse og kan omfatte undersystemer, der kører firmware til administrationsformål. En sådan firmware kan være sårbar over for kapring og tillade udførelse af skadelig kode, der fungerer inde fra CPU'en. I december 2017 rapporterede to hackere om en sikkerhedsrisiko, der kan tillade hackere at udføre kode i Management [Engine (ME),](https://en.wikipedia.org/wiki/Intel_Management_Engine) som findes i en hvilken som helst moderne CPU fra Intel. I mellemtiden er hackergruppen PLATINUM blevet observeret, så den kan bruge Intels [Active Management Technology (AMT)](https://en.wikipedia.org/wiki/Intel_Active_Management_Technology) til at udføre usynlig netværkskommunikation [og tilsidesætte](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/07/platinum-continues-to-evolve-find-ways-to-maintain-invisibility/) det installerede operativsystem. ME og AMT er i bund og grund mikrocomputere, der bor inde i CPU'en, og som arbejder på et meget lavt niveau. Da disse teknologiers formål er at levere fjernstyring, har de direkte adgang til hardware, er uafhængige af operativsystemet og kan køre, selvom computeren er slukket.

Ud over at være sårbar på firmwareniveau kan CPU'er være fremstillet med backdoors, der indsættes direkte i hardwarekredsløb. Dette angreb er blevet [undersøgt og har været muligt](https://www.emsec.rub.de/media/crypto/veroeffentlichungen/2015/03/19/beckerStealthyExtended.pdf) tidligere. Det er blevet rapporteret, at visse modeller af x86-processorer indeholder en sekundær integreret RISC-lignende CPU-kerne, der effektivt kan give en [backdoor](https://www.theregister.co.uk/2018/08/10/via_c3_x86_processor_backdoor/) , hvor almindelige programmer kan opnå den privilegerede udførelse.

**USB-baseret** (Type I): USB-enheder af alle typer kan omprogrammeres med ondsindet firmware, der kan interagere med operativsystemet på forældelige måder. [BadUSB-teknik](https://arstechnica.com/information-technology/2014/07/this-thumbdrive-hacks-computers-badusb-exploit-makes-devices-turn-evil/) gør det f.eks. muligt for en omprogrammeret USB-stick at fungere som et tastatur, der sender kommandoer til maskiner via tastetryk eller som et netværkskort, der kan omdirigere trafik efter ønsker.

**DENS-baserede** (Type I): En AFRÅR er en firmware, der kører inde i et chipsæt. Den udføres, når en computer er tændt, initialiserer hardwaren og overfører derefter kontrollen til startbranchen. 2016 er en vigtig komponent, der kører på et lavt niveau og udføres før opstartsbranchen. Det er muligt at omprogrammere DEN AMERIKANSKE FIRMWARE med skadelig kode, som det er sket i fortiden med [Mebromi rootkit](https://www.webroot.com/blog/2011/09/13/mebromi-the-first-bios-rootkit-in-the-wild/).

**Hypervisor-baseret** (type I): Moderne CPUs giver hardware hypervisor-support, så operativsystemet kan oprette robuste virtuelle maskiner. En virtuel maskine kører i et begrænset, simuleret miljø og er teoretisk ikke klar over emuleringen. Malware, der tager over en computer, kan implementere en lille hypervisor for at skjule sig selv uden for det kørende operativsystems domæne. Malware af denne type er blevet ændret i fortiden, og med tiden er der blevet observeret ægte hypervisor [rootkits,](http://seclists.org/fulldisclosure/2017/Jun/29) selvom kun få kender til dato.

### <a name="execution-and-injection"></a>Udførelse og indførelse

Filbaseret (Type III: eksekverbare filer, **URL-adresser, LNK-filer**, planlagte opgaver): Dette er standard eksekveringsvektoren. En simpel eksekverbar eksekverbar software kan startes som malware i første trin for at køre en ekstra nyttedata i hukommelsen eller tilføjes i andre legitime kørende processer.

**Makrobaseret** (Type III: Office-dokumenter): [VBA-sproget](/office/vba/Library-Reference/Concepts/getting-started-with-vba-in-office) er et fleksibelt og effektivt værktøj, der er designet til at automatisere redigeringsopgaver og føje dynamisk funktionalitet til dokumenter. Det kan misbruges af hackere til at udføre ondsindede handlinger som afkodning, kørsel eller indsatte en eksekverbar nyttedata eller endda implementere en hel ransomware, f.eks. med [qkG](https://blog.trendmicro.com/trendlabs-security-intelligence/qkg-filecoder-self-replicating-document-encrypting-ransomware/). Makroer udføres i forbindelse med en Office proces (f.eks. Winword.exe) og implementeres på et scriptsprog. Der er ingen binær eksekverbar fil, som et antivirusprogram kan undersøge. Selvom Office apps kræver udtrykkeligt samtykke fra brugeren til at udføre makroer fra et dokument, bruger hackere social engineering-teknikker til at narre brugere til at tillade makroer at udføre.

**Scriptbaseret** (Type II: fil, tjeneste, registreringsdatabase, WMI repo, shell): JavaScript-, VBScript- og PowerShell-scriptsprog er som standard tilgængelige på Windows platforme. Scripts har de samme fordele som makroer, de er tekstfiler (ikke binære eksekverbare filer) og kører inden for konteksten af tolken (f.eks. wscript.exe, powershell.exe), som er en ren og legitim komponent. Scripts er alsidige og kan køres fra en fil (ved at dobbeltklikke på dem) eller udføres direkte på kommandolinjen for en tolke. Hvis du kører på kommandolinjen, kan malware kode ondsindede scripts som automatiske starttjenester [](https://www.gdatasoftware.com/blog/2014/07/23947-poweliks-the-persistent-malware-without-a-file) i registreringsdatabasenøgler automatisk som [WMI-hændelsesabonnementer](https://www.fireeye.com/blog/threat-research/2017/03/dissecting_one_ofap.html) fra WMI-repo. Desuden kan en hacker, der har fået adgang til en inficeret maskine, indtaste manuskriptet i kommandoprompten.

**Diskbaseret** (Type II: Boot Record): Startposten er den første del af en disk eller mængde og indeholder den eksekverbare kode, der kræves for at starte startprocessen af operativsystemet. Trusler som [Petya kan](https://cloudblogs.microsoft.com/microsoftsecure/2017/06/27/new-ransomware-old-techniques-petya-adds-worm-capabilities/?source=mmpc) inficere startposten ved at overskrive den med skadelig kode. Når computeren er startet, får malwaren straks kontrollen. Startposten er placeret uden for filsystemet, men den er tilgængelig for operativsystemet. Moderne antivirusprodukter har mulighed for at scanne og gendanne dem.

## <a name="defeating-fileless-malware"></a>Overdrejende malware uden filer

Hos Microsoft overvåger vi aktivt sikkerhedslandskabet for at identificere nye trusselstendenser og udarbejde løsninger, der kan afhjælpe trusselsklasser. Vi instrumentholdige beskyttelser, der er effektive mod en lang række trusler. Via ANTIMalware Scan Interface (AMSI), overvågning af funktionsmåde, hukommelsesscanning og opstartsbeskyttelse af software kan [Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) undersøge filløse trusler selv med stor forvirring. Maskinlæringsteknologier i skyen giver os mulighed for at skalere disse beskyttelser mod nye og fremspirende trusler.

Du kan få mere at vide ved at læse: Ude af syne, men ikke usynlig: Forseende filfri malware med overvågning af adfærd [, AMSI og næste generation af AV](https://cloudblogs.microsoft.com/microsoftsecure/2018/09/27/out-of-sight-but-not-invisible-defeating-fileless-malware-with-behavior-monitoring-amsi-and-next-gen-av/)

## <a name="additional-resources-and-information"></a>Yderligere ressourcer og oplysninger

Få mere at vide [om, hvordan du udruller funktioner til trusselsbeskyttelse på Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection).
