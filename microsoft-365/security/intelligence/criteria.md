---
title: Sådan identificerer Microsoft malware og potentielt uønskede programmer
ms.reviewer: ''
description: Få mere at vide om, hvordan Microsoft gennemser software for overtrædelser af personlige oplysninger og andre negative funktionsmåder for at afgøre, om det er malware eller et potentielt uønsket program.
keywords: sikkerhed, malware, virusforskningstrusler, researchmalware, enhedsbeskyttelse, computer infektion, virus infektion, beskrivelser, afhjælpning, seneste trusler, MMdevice, Microsoft Malware Protection Center, PUA, potentielt uønskede programmer
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
ms.date: 12/13/2021
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 1f210ee98c8fc51cfa6900b19bb3cb5d5465dbb3
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663528"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Sådan identificerer Microsoft malware og potentielt uønskede programmer

Microsoft tilstræber at give en dejlig og produktiv Windows oplevelse ved at arbejde for at sikre, at du er sikker og har kontrol over dine enheder. Microsoft hjælper dig med at beskytte dig mod potentielle trusler ved at identificere og analysere software og onlineindhold. Når du downloader, installerer og kører software, kontrollerer vi omdømmet for downloadede programmer og sikrer, at du er beskyttet mod kendte trusler. Du bliver også advaret om software, der er ukendt for os.  

Du kan hjælpe Microsoft ved [at indsende ukendt eller mistænkelig software til analyse](https://www.microsoft.com/wdsi/filesubmission/). Dette vil hjælpe med at sikre, at ukendt eller mistænkelig software scannes af vores system for at begynde at etablere omdømme. [Få mere at vide om indsendelse af filer til analyse](submission-guide.md)

De næste afsnit indeholder en oversigt over de klassificeringer, vi bruger til programmer, og de typer funktionsmåder, der fører til klassificeringen.

>[!NOTE]
> Nye former for malware og potentielt uønskede programmer udvikles og distribueres hurtigt. Følgende liste er muligvis ikke omfattende, og Microsoft forbeholder sig ret til at justere, udvide og opdatere disse uden forudgående varsel eller meddelelse.

## <a name="unknown--unrecognized-software"></a>Ukendt – ukendt software  

Ingen antivirus- eller beskyttelsesteknologi er perfekt. Det tager tid at identificere og blokere skadelige websteder og programmer eller have tillid til nyligt udgivne programmer og certifikater. Med næsten 2 milliarder websteder på internettet og software løbende opdateret og udgivet, er det umuligt at have oplysninger om hvert enkelt websted og program.

Tænk på Ukendte/ualmindeligt downloadede advarsler som et tidligt advarselssystem for potentielt uopdaget malware. Der er generelt en forsinkelse fra det tidspunkt, hvor ny malware frigives, indtil den er identificeret. Ikke alle ualmindelige programmer er ondsindede, men risikoen i den ukendte kategori er meget højere for den typiske bruger. Advarsler for ukendt software er ikke blokke. Brugerne kan vælge at downloade og køre programmet på normal vis, hvis de ønsker det.

Når der er indsamlet nok data, kan Microsofts sikkerhedsløsninger træffe en afgørelse. Enten findes der ingen trusler, eller et program eller software er kategoriseret som malware eller potentielt uønsket software.

## <a name="malware"></a>Malware

Malware er det overordnede navn for programmer og anden kode, f.eks. software, som Microsoft klassificerer mere detaljeret som *skadelig software* eller *uønsket software*.

### <a name="malicious-software"></a>Skadelig software

Skadelig software er et program eller en kode, der kompromitterer brugersikkerheden. Skadelig software kan stjæle dine personlige oplysninger, låse din enhed, indtil du betaler en løsesum, bruge din enhed til at sende spam eller downloade anden skadelig software. Generelt ønsker skadelig software at narre, snyde eller bedrage brugere, placere dem i sårbare stater.

Microsoft klassificerer mest skadelig software i en af følgende kategorier:

* **Bagdør:** En type malware, der giver ondsindede hackere fjernadgang til og kontrol over din enhed.

* **Kommando og kontrolelement:** En type malware, der inficerer din enhed og etablerer kommunikation med hackernes kommando- og kontrolserver for at modtage instruktioner. Når kommunikation er etableret, hackere kan sende kommandoer, der kan stjæle data, lukke ned og genstarte enheden, og forstyrre webtjenester.

* **Downloader:** En type malware, der downloader anden malware på din enhed. Den skal oprette forbindelse til internettet for at downloade filer.

* **Dropper:** En type malware, der installerer andre malwarefiler på din enhed. I modsætning til en downloader behøver en dropper ikke at oprette forbindelse til internettet for at slippe skadelige filer. De udeladte filer er typisk integreret i selve dropperen.

* **Udnytte:** Et stykke kode, der bruger softwaresårbarheder til at få adgang til din enhed og udføre andre opgaver, f.eks. installation af malware. [Se flere oplysninger om udnyttelser](exploits-malware.md).

* **Hacktool:** En type værktøj, der kan bruges til at få uautoriseret adgang til din enhed.

* **Makrovirus:** En type malware, der spredes via inficerede dokumenter, f.eks. Microsoft Word eller Excel dokumenter. Virusen køres, når du åbner et inficeret dokument.

* **Obfuscator:** En type malware, der skjuler sin kode og sit formål, hvilket gør det vanskeligere for sikkerhedssoftware at registrere eller fjerne.

* **Adgangskodesjæl:** En type malware, der indsamler dine personlige oplysninger, f.eks. brugernavne og adgangskoder. Det fungerer ofte sammen med en keylogger, der indsamler og sender oplysninger om de taster, du trykker på, og websteder, du besøger.

* **Ransomware:** En type malware, der krypterer dine filer eller foretager andre ændringer, der kan forhindre dig i at bruge din enhed. Det viser derefter en løsesum note, der hedder du skal betale penge eller udføre andre handlinger, før du kan bruge din enhed igen. [Se flere oplysninger om ransomware](/security/compass/human-operated-ransomware).

* **Rogue-sikkerhedssoftware:** Malware, der foregiver at være sikkerhedssoftware, men som ikke yder nogen beskyttelse. Denne type malware viser normalt beskeder om ikke-eksisterende trusler på din enhed. Det forsøger også at overbevise dig om at betale for sine tjenester.

* **Trojan:** En type malware, der forsøger at virke harmløs. I modsætning til en virus eller en orm spredes en trojan ikke af sig selv. I stedet forsøger den at se legitim ud for tricks, som brugerne kan bruge til at downloade og installere den. Når de er installeret, udfører trojanske heste forskellige ondsindede aktiviteter, f.eks. at stjæle personlige oplysninger, downloade anden malware eller give hackere adgang til din enhed.

* **Trojansk klikmaskine:** En type trojansk, der automatisk klikker på knapper eller lignende kontrolelementer på websteder eller applikationer. Angribere kan bruge denne trojanske til at klikke på online reklamer. Disse klik kan forvrænge online afstemninger eller andre sporingssystemer og kan endda installere programmer på din enhed.

* **Orm:** En type malware, der spredes til andre enheder. Orme kan spredes via mail, chat, fildelingsplatforme, sociale netværk, netværksshares og flytbare drev. Sofistikerede orme drage fordel af software sårbarheder til at overføre.

### <a name="unwanted-software"></a>Uønsket software

Microsoft mener, at du skal have kontrol over din Windows oplevelse. Software, der kører på Windows, bør holde dig i kontrol over din enhed via informerede valg og tilgængelige kontrolelementer. Microsoft identificerer softwarefunktioner, der sikrer, at du forbliver i kontrol. Vi klassificerer software, der ikke fuldt ud demonstrerer disse funktionsmåder som "uønsket software".

#### <a name="lack-of-choice"></a>Manglende valg

Du skal have besked om, hvad der sker på din enhed, herunder hvilken software der bruges, og om den er aktiv.

Software, der udviser manglende valg, kan:

* Det lykkedes ikke at give en fremtrædende meddelelse om softwarens funktionsmåde og dens formål og hensigt.

* Det lykkedes ikke tydeligt at angive, hvornår softwaren er aktiv. Det kan også forsøge at skjule eller skjule sin tilstedeværelse.

* Installér, geninstaller eller fjern software uden din tilladelse, interaktion eller dit samtykke.

* Installér anden software uden en klar indikation af dens relation til den primære software.

* Omgå brugersamtykkedialogboksene fra browseren eller operativsystemet.

* Falsk hævder at være software fra Microsoft.

Software må ikke vildlede eller tvinge dig til at træffe beslutninger om din enhed. Det betragtes som funktionsmåde, der begrænser dine valg. Ud over den forrige liste, software, der udviser manglende valg kan:

* Vis overdrevne krav om enhedens tilstand.

* Fremsætte vildledende eller unøjagtige påstande om filer, poster i registreringsdatabasen eller andre elementer på din enhed.

* Vis krav på en alarmerende måde om enhedens tilstand og kræver betaling eller visse handlinger til gengæld for at løse de påståede problemer.

Software, der gemmer eller overfører dine aktiviteter eller data, skal:

* Giv dig besked og få samtykke til at gøre det. Softwaren bør ikke indeholde en indstilling, der konfigurerer den til at skjule aktiviteter, der er knyttet til lagring eller overførsel af dine data.

#### <a name="lack-of-control"></a>Manglende kontrol

Du skal kunne styre software på din enhed. Du skal kunne starte, stoppe eller på anden måde tilbagekalde autorisation til software.

Software, der udviser manglende kontrol, kan:

* Forhindre eller begrænse dig i at få vist eller ændre browserfunktioner eller -indstillinger.

* Åbn browservinduer uden godkendelse.

* Omdiriger webtrafik uden at give besked og få samtykke.

* Rediger eller rediger websideindhold uden dit samtykke.

Software, der ændrer din browseroplevelse, må kun bruge browserens understøttede udvidelsesmodel til installation, udførelse, deaktivering eller fjernelse. Browsere, der ikke indeholder understøttede udvidelsesmodeller, betragtes som ikke-udvidelsesbare og bør ikke ændres.

#### <a name="installation-and-removal"></a>Installation og fjernelse

Du skal kunne starte, stoppe eller på anden måde tilbagekalde den autorisation, der er givet til softwaren. Software skal indhente dit samtykke, før du installerer, og det skal give dig en klar og enkel måde at installere, fjerne eller deaktivere den på.

Software, der leverer *dårlig installationsoplevelse* , kan bundte eller downloade anden "uønsket software", som er klassificeret af Microsoft.

Software, der leverer *en dårlig fjernelsesoplevelse* , kan:

* Præsenter forvirrende eller vildledende prompter eller pop op-meddelelser, når du forsøger at fjerne det.

* Det lykkedes ikke at bruge standardinstallations-/fjernelsesfunktioner, f.eks. Tilføj/fjern programmer.

#### <a name="advertising-and-advertisements"></a>Annoncering og reklamer

Software, der markedsfører et produkt eller en tjeneste uden for selve softwaren, kan forstyrre din computeroplevelse. Du skal have klart valg og kontrol, når du installerer software, der præsenterer reklamer.

De reklamer, der præsenteres af software skal:

* Medtag en tydelig måde for brugerne at lukke annonceringen på. Når annonceringen lukkes, må der ikke åbnes en anden annonce.

* Medtag navnet på den software, der præsenterede reklamen.

Den software, der præsenterer disse reklamer skal:

* Angiv en standardafinstallationsmetode for softwaren med det samme navn som vist i den reklame, den viser.

Reklamer, der vises for dig, skal:

* Skelnes fra webstedsindhold.

* Ikke vildlede, bedrage eller forvirre.

* Indeholder ikke skadelig kode.

* Aktivér ikke en fildownload.

#### <a name="consumer-opinion"></a>Forbrugerudtalelse

Microsoft vedligeholder et verdensomspændende netværk af analytikere og intelligence-systemer, hvor du kan [indsende software til analyse](https://www.microsoft.com/wdsi/filesubmission). Din deltagelse hjælper Microsoft med hurtigt at identificere ny malware. Efter analysen opretter Microsoft Sikkerhedsintelligens for software, der opfylder de beskrevne kriterier. Denne sikkerhedsintelligens identificerer softwaren som malware og er tilgængelig for alle brugere via Microsoft Defender Antivirus og andre Microsoft antimalware-løsninger.

## <a name="potentially-unwanted-application-pua"></a>Potentielt uønsket applikation (PUA)

Vores PUA-beskyttelse har til formål at sikre brugernes produktivitet og sikre behagelige Windows oplevelser. Denne beskyttelse hjælper med at levere mere produktive, effektive og dejlige Windows oplevelser. Hvis du vil have en vejledning i, hvordan du aktiverer PUA-beskyttelse i Chromium-baserede Microsoft Edge og Microsoft Defender Antivirus, skal du se [Registrer og bloker potentielt uønskede programmer](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*PUA'er betragtes ikke som malware.*

Microsoft bruger specifikke kategorier og kategoridefinitioner til at klassificere software som en PUA.

* **Annonceringssoftware:** Software, der viser reklamer eller kampagner, eller beder dig om at gennemføre undersøgelser for andre produkter eller tjenester i anden software end sig selv. Dette omfatter software, der indsætter reklamer på websider.

* **Torrent software (kun Enterprise):** Software, der bruges til at oprette eller downloade torrents eller andre filer, der specifikt bruges med peer-to-peer-fildelingsteknologier.

* **Kryptografisoftware (kun virksomhed):** Software, der bruger dine enhedsressourcer til at mine kryptovalutaer.

* **Bundling-software:** Software, der tilbyder at installere anden software, der ikke er udviklet af den samme enhed eller ikke kræves, for at softwaren kan køre. Også software, der tilbyder at installere anden software, der er kvalificeret som PUA baseret på de kriterier, der er beskrevet i dette dokument.

* **Marketingsoftware:** Software, der overvåger og sender brugernes aktiviteter til andre programmer eller tjenester end sig selv med henblik på markedsføringsforskning.

* **Undvigelsessoftware:** Software, der aktivt forsøger at undgå registrering af sikkerhedsprodukter, herunder software, der fungerer anderledes i tilstedeværelse af sikkerhedsprodukter.

* **Dårlig brancheomdømme:** Software, som sikkerhedsudbydere, der er tillid til, registrerer med deres sikkerhedsprodukter. Sikkerhedsbranchen er dedikeret til at beskytte kunder og forbedre deres oplevelser. Microsoft og andre organisationer i sikkerhedsbranchen udveksler løbende viden om filer, vi har analyseret, for at give brugerne den bedst mulige beskyttelse.

