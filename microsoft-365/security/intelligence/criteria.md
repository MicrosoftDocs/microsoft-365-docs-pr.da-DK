---
title: Sådan identificerer Microsoft malware og potentielt uønskede programmer
ms.reviewer: ''
description: Få mere at vide om, hvordan Microsoft gennemser software for overtrædelser af personlige oplysninger og anden negativ adfærd for at afgøre, om det er malware eller et potentielt uønsket program.
keywords: sikkerhed, malware, virusundersøgelsestrusler, researchmalware, enhedsbeskyttelse, computerinstruktion, virusinstruktion, beskrivelser, afhjælpning, nyeste trusler, MMdevice, Microsoft Malware Protection Center, PUA, potentielt uønskede programmer
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
ms.openlocfilehash: 3eb7eefb5309383b46189f784f811224dcfb2b28
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705885"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Sådan identificerer Microsoft malware og potentielt uønskede programmer

Microsoft arbejder på at skabe en herlig og produktiv Windows ved at arbejde for at sikre, at du er sikker og i kontrol over dine enheder. Microsoft hjælper med at beskytte dig mod potentielle trusler ved at identificere og analysere software og onlineindhold. Når du downloader, installerer og kører software, kontrollerer vi omdømmet af downloadede programmer og sikrer, at du er beskyttet mod kendte trusler. Du bliver også advaret om software, vi ikke kender.  

Du kan hjælpe Microsoft ved [at indsende ukendt eller mistænkelig software til analyse](https://www.microsoft.com/wdsi/filesubmission/). Dette er med til at sikre, at ukendt eller mistænkelig software scannes af vores system for at starte på at etablere et ry. [Få mere at vide om at sende filer til analyse](submission-guide.md)

De næste afsnit indeholder en oversigt over de klassificeringer, vi bruger til programmer, og de typer funktionsmåder, der fører til den pågældende klassificering.

>[!NOTE]
> Nye former for malware og potentielt uønskede programmer udvikles og distribueres hurtigt. Følgende liste er muligvis ikke fyldestgørende, og Microsoft forbeholder sig ret til at justere, udvide og opdatere disse uden forudgående varsel eller meddelelse.

## <a name="unknown--unrecognized-software"></a>Ukendt – Ukendt software  

Ingen antivirus- eller beskyttelsesteknologi er perfekt. Det tager tid at identificere og blokere skadelige websteder og programmer eller have tillid til nyligt udgivne programmer og certifikater.Med næsten 2 mia. websteder på internettet og softwaren opdateres og udgives løbende, er det umuligt at have oplysninger om hvert enkelt websted og program.

Tænk på Ukendt/Ualmindeligt downloadede advarsler som et tidligt advarselssystem for potentielt ikke-opdaget malware. Der er generelt en forsinkelse fra det tidspunkt, hvor der frigives ny malware, indtil den identificeres. Ikke alle ualmindelige programmer er skadelige, men risikoen i den ukendte kategori er meget højere for den typiske bruger. Advarsler om ukendt software er ikke blokke. Brugere kan vælge at downloade og køre programmet normalt, hvis de ønsker det.

Når der er indsamlet nok data, kan Microsofts sikkerhedsløsninger træffe en beslutning. Der er enten ikke fundet nogen trusler, eller også kategoriseres et program eller software som malware eller potentielt uønsket software.

## <a name="malware"></a>Malware

Malware er det overordnede navn for programmer og anden kode, f.eks. software, som Microsoft klassificerer mere detaljeret som skadelig *software* eller *uønsket software*.

### <a name="malicious-software"></a>Skadelig software

Ondsindet software er et program eller en kode, der kompromitterer brugersikkerheden. Ondsindet software kan stjæle dine personlige oplysninger, låse din enhed, indtil du betaler for noget, bruge din enhed til at sende spam eller downloade anden ondsindet software. Generelt vil skadelig software gerne narre, snyde eller bedrage brugere og placere dem i følsomme tilstande.

Microsoft klassificerer mest skadelig software i en af følgende kategorier:

* **Backdoor:** En type malware, der giver ondsindede hackere fjernadgang til og kontrol over din enhed.

* **Kommando og styring:** En type malware, der inficerer din enhed og etablerer kommunikation med hackeres kommando- og kontrolserver for at modtage instruktioner. Når kommunikationen er etableret, kan hackere sende kommandoer, der kan stjæle data, lukke og genstarte enheden og afbryde webtjenester.

* **Downloader:** En type malware, der downloader anden malware til din enhed. Den skal oprette forbindelse til internettet for at downloade filer.

* **Pipette:** En type malware, der installerer andre malwarefiler på din enhed.I modsætning til en downloader behøver en fjernelse af filer ikke at oprette forbindelse til internettet for at slippe skadelige filer. De indfaldne filer er typisk integreret i selve nedfalden.

* **Exploit:** Et stykke kode, der bruger softwaresårbarheder til at få adgang til din enhed og udføre andre opgaver, f.eks. installation af malware. [Se flere oplysninger om udnyttelse](exploits-malware.md).

* **Hackværktøj:** En type værktøj, der kan bruges til at få uautoriseret adgang til din enhed.

* **Makrovirus:** En type malware, der spredes gennem inficeret dokumenter, f.eks. Microsoft Word eller Excel dokumenter. Virusset køres, når du åbner et inficeret dokument.

* **Obfuscator:** En type malware, der skjuler dens kode og formål, hvilket gør det sværere for sikkerhedssoftware at registrere eller fjerne.

* **Password stealer:** En type malware, der indsamler dine personlige oplysninger, f.eks. brugernavne og adgangskoder. Den fungerer ofte sammen med en jod, som indsamler og sender oplysninger om de taster, du trykker på, og de websteder, du besøger.

* **Ransomware:** En type malware, der krypterer dine filer eller foretager andre ændringer, der kan forhindre dig i at bruge din enhed. Herefter vises en notat, som angiver, at du skal betale penge eller udføre andre handlinger, før du kan bruge enheden igen. [Se flere oplysninger om ransomware](/security/compass/human-operated-ransomware).

* **Software med sikkerhed:** Malware, der forestiller sig at være sikkerhedssoftware, men ikke giver nogen beskyttelse. Denne type malware viser normalt beskeder om ikke-eksisterende trusler på din enhed. Den forsøger også at overbevise dig om at betale for sine tjenester.

* **trojansk:** En type malware, der forsøger at blive vist uskadeligt. I modsætning til en virus eller en orm spredes en trojansk ikke sig selv. Den forsøger i stedet at se legitim ud for at narre brugere til at downloade og installere den. Når trojanske er installeret, udfører de forskellige ondsindede aktiviteter, som f.eks. at stjæle personlige oplysninger, hente anden malware eller give hackere adgang til din enhed.

* **trojansk klikker:** En type trojansk, der automatisk klikker på knapper eller lignende kontrolelementer på websteder eller programmer. Hackere kan bruge denne trojanske til at klikke på onlineannoncer. Disse klik kan give en skævhed i online afstemninger eller andre sporingssystemer, og de kan endda installere programmer på din enhed.

* **Orm:** En type malware, der spredes til andre enheder. Orme kan spredes via mail, chat, fildelingsplatforme, sociale netværk, netværksshares og flytbare drev. Avancerede orme udnytter softwaresårbarheder til at overføres.

### <a name="unwanted-software"></a>Uønsket software

Microsoft mener, at du bør have kontrol over din Windows oplevelse. Software, der kører Windows, skal holde dig i kontrol over din enhed gennem informerede valg og tilgængelige kontrolelementer. Microsoft identificerer softwarefunktionsmåder, der sikrer, at du holder styr på det. Vi klassificerer software, der ikke fuldt ud demonstrerer disse funktionsmåder som "uønsket software".

#### <a name="lack-of-choice"></a>Manglende valgmulighed

Du skal have besked om, hvad der sker på din enhed, herunder hvilken software der gør, og om den er aktiv.

Software, der ikke har noget valg, kan:

* Undlade at give fremtrædende meddelelse om softwarens funktionsmåde og formål og formål.

* Du kan ikke tydeligt angive, hvornår softwaren er aktiv. Den kan også forsøge at skjule eller skjule dens tilstedeværelse.

* Installér, geninstaller eller fjern software uden din tilladelse, interaktion eller dit samtykke.

* Installér anden software uden tydeligt at angive dens relation til den primære software.

* Omgå dialogbokse for brugersamtykke fra browseren eller operativsystemet.

* Falsk hævder at være software fra Microsoft.

Softwaren må ikke få dig til at få en ide om eller tvinge dig til at træffe beslutninger om din enhed. Det betragtes som funktionsmåde, der begrænser dine valg. Ud over den forrige liste kan software, der udviser manglende valgmulighed,:

* Vise overdrivede krav om enhedens tilstand.

* Foretag vildledende eller unøjagtige krav om filer, poster i registreringsdatabasen eller andre elementer på din enhed.

* Vis krav på alarmerende vis om din enheds tilstand og kræv betaling eller visse handlinger i bytte for at løse de påståede problemer.

Software, der lagrer eller overfører dine aktiviteter eller data, skal:

* Giv dig besked, og få samtykke til at gøre dette. Software bør ikke indeholde en indstilling, der konfigurerer den til at skjule aktiviteter, der er knyttet til lagring eller overførsel af dine data.

#### <a name="lack-of-control"></a>Manglende kontrol

Du skal kunne styre softwaren på din enhed. Du skal kunne starte, stoppe eller på anden måde tilbagekalde autorisationen til software.

Software, der udviser manglende kontrol, kan:

* Undgå eller begræns, at du får vist eller redigerer browserfunktioner eller -indstillinger.

* Åbn browservinduer uden godkendelse.

* Omdiriger webtrafik uden at give meddelelse og få samtykke.

* Rediger eller rediger websideindhold uden dit samtykke.

Software, der ændrer din browseroplevelse, må kun bruge browserens understøttede udvidelsesmodel til installation, udførelse, deaktivering eller fjernelse. Browsere, der ikke leverer understøttede udvidelsesmuligheder, betragtes som ikke-udvidelige og bør ikke ændres.

#### <a name="installation-and-removal"></a>Installation og fjernelse

Du skal kunne starte, stoppe eller på anden måde tilbagekalde den godkendelse, der er givet til software. Softwaren skal have dit samtykke, før den installeres, og den skal være en klar og ukompliceret måde, hvorpå du kan installere, fjerne eller deaktivere den.

Software, der leverer dårlig *installationsoplevelse, kan* bundte eller downloade anden "uønsket software", som er klassificeret af Microsoft.

Software, der leverer *dårlig fjernelsesoplevelse,* kan:

* Præsenter forvirrende eller misvisende prompter eller pop op-vinduesmeddelelser, når du forsøger at fjerne den.

* Du kan ikke bruge standardfunktionerne til installation/fjernelse, f.eks. Tilføj/fjern programmer.

#### <a name="advertising-and-advertisements"></a>Reklamer og annoncer

Software, der promoverer et produkt eller en tjeneste uden for selve softwaren, kan forstyrre din computeroplevelse. Du skal have et tydeligt valg og kontrol, når du installerer software, der præsenterer reklamer.

De reklamer, der præsenteres af software, skal:

* Inkluder en indlysende måde, hvorpå brugerne kan lukke annonceringen. En handling, der lukker annonceringen, må ikke åbne en anden annoncering.

* Medtag navnet på den software, der har præsenteret annonceringen.

Den software, der præsenterer disse reklamer, skal:

* Angiv en standardinstallationsmetode til softwaren med det samme navn som vist i den præsenterer reklame.

Reklamer, der vises for dig, skal:

* Skelnes fra webstedsindhold.

* Du må ikke få en kant, snyde eller forplumme.

* Ikke indeholder skadelig kode.

* Ikke fremkalde en filoverførsel.

#### <a name="consumer-opinion"></a>Forbrugeres mening

Microsoft vedligeholder et verdensomspændende netværk af analytikere og intelligencesystemer, hvor du [kan indsende software til analyse](https://www.microsoft.com/wdsi/filesubmission). Din deltagelse hjælper Microsoft med hurtigt at identificere ny malware. Efter analyse opretter Microsoft sikkerhedsintelligens til software, der opfylder de beskrevne kriterier. Denne sikkerhedsintelligens identificerer softwaren som malware og er tilgængelig for alle brugere via Microsoft Defender Antivirus og andre Microsoft-antimalwareløsninger.

## <a name="potentially-unwanted-application-pua"></a>Potentielt uønsket program (PUA)

Vores PUA-beskyttelse beskytter brugernes produktivitet og sikrer god Windows oplevelser. Denne beskyttelse hjælper med at levere mere produktiv, performant og herlig Windows oplevelser. Du kan finde vejledning til at aktivere PUA-beskyttelse i Chromium-baseret Microsoft Edge og Microsoft Defender Antivirus i Finde og [blokere potentielt uønskede programmer](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*PPA'er betragtes ikke som malware.*

Microsoft bruger bestemte kategorier og kategoridefinitionerne til at klassificere software som en PUA.

* **Reklamesoftware:** Software, der viser reklamer eller kampagner, eller som beder dig om at gennemføre undersøgelser af andre produkter eller tjenester i anden software end sig selv. Dette omfatter software, der indsætter reklamer på websider.

* **Torrent-software (kun for virksomheder):** Software, der bruges til at oprette eller downloade strømsider eller andre filer, der specifikt bruges med peer-to-peer-fildelingsteknologier.

* **Cryptomining-software (kun til virksomheder):** Software, der bruger dine enhedsressourcer til at udminde.

* **Bundtningssoftware:** Software, der tilbyder installation af anden software, der ikke er udviklet af den samme enhed, eller som ikke er nødvendig for, at softwaren kan køre. Desuden er software, der tilbyder installation af anden software, der kvalificerer som PUA baseret på de kriterier, der er beskrevet i dette dokument.

* **Marketingsoftware:** Software, der overvåger og overfører brugernes aktiviteter til programmer eller tjenester, som ikke er dem selv, til marketingundersøgelse.

* **Software, der er tilstrund:** Software, der aktivt forsøger at undgå registrering af sikkerhedsprodukter, herunder software, der opfører sig anderledes i tilstedeværelse af sikkerhedsprodukter.

* **Dårligt branche ry:** Software, som sikkerhedsudbydere, der er tillid til, registrerer med deres sikkerhedsprodukter. Sikkerhedsbranchen har fokus på at beskytte kunder og forbedre deres oplevelser. Microsoft og andre organisationer inden for sikkerhedsbranchen udveksler løbende viden om filer, vi har analyseret, for at give brugerne den bedst mulige beskyttelse.

