---
title: Brug netværksbeskyttelse til at forhindre forbindelser til forkerte websteder
description: Beskyt dit netværk ved at forhindre brugerne i at få adgang til kendte skadelige og mistænkelige netværksadresser
keywords: Netværksbeskyttelse, udnyttelser, skadeligt websted, ip, domæne, domæner, kommando og kontrol, SmartScreen, toastbesked
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 20de4c18c46977108c1570ba89bb6daefcf8cfdd
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923396"
---
# <a name="protect-your-network"></a>Beskyt dit netværk

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Vil du gerne opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Oversigt over netværksbeskyttelse

Netværksbeskyttelse hjælper med at beskytte enheder mod internetbaserede hændelser. Netværksbeskyttelse er en funktionalitet til reduktion af angrebsoverfladen. Det hjælper med at forhindre medarbejdere i at få adgang til farlige domæner via programmer. Domæner, der hoster phishing-svindel, udnyttelser og andet skadeligt indhold på internettet, betragtes som farlige. Netværksbeskyttelse udvider omfanget af [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) for at blokere al udgående HTTP(er) trafik, der forsøger at oprette forbindelse til kilder med lavt omdømme (baseret på domænet eller værtsnavnet).

Netværksbeskyttelse udvider beskyttelsen i [webbeskyttelse](web-protection-overview.md) til operativsystemets niveau. Den leverer den webbeskyttelsesfunktionalitet, der findes i Microsoft Edge, til andre understøttede browsere og programmer, der ikke er browsere. Netværksbeskyttelse giver også synlighed og blokering af indikatorer for kompromitteret (IOCs), når de bruges sammen med [registrering og svar af slutpunkter](overview-endpoint-detection-response.md). Netværksbeskyttelse fungerer f.eks. med dine [brugerdefinerede indikatorer](manage-indicators.md) , som du kan bruge til at blokere bestemte domæner eller værtsnavne.

> [!TIP]
> Se Microsoft Defender for Endpoint-testground-webstedet på [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at se, hvordan netværksbeskyttelse fungerer.

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

Se denne video for at få mere at vide om, hvordan Netværksbeskyttelse hjælper med at reducere angrebsoverfladen på dine enheder fra phishing-svindel, udnyttelser og andet skadeligt indhold.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4r4yZ]

## <a name="requirements-for-network-protection"></a>Krav til netværksbeskyttelse

Netværksbeskyttelse kræver Windows 10 Pro eller Enterprise og Microsoft Defender Antivirus i realtid.

| Windows-version | Microsoft Defender Antivirus |
|:---|:---|
| Windows 10 version 1709 eller nyere <br> Windows 11 <br> Windows Server 1803 eller nyere | [Microsoft Defender Antivirus beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md) <br> og [skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) skal aktiveres (aktiv)|

## <a name="why-network-protection-is-important"></a>Hvorfor netværksbeskyttelse er vigtig

> [!IMPORTANT]
> Nogle oplysninger er relateret til et forhåndsudgivet produkt, som kan blive ændret væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.
> Oplysninger om de funktioner, der er kommercielt tilgængelige, følger oplysningerne om den offentlige prøveversion.

Netværksbeskyttelse er en del af gruppen af løsninger til reduktion af angrebsoverfladen i Microsoft Defender for Endpoint. Netværksbeskyttelse gør det muligt for netværkslag at blokere URL-adresser og IP-adresser. Netværksbeskyttelse kan forhindre ADGANG til URL-adresser ved hjælp af visse browsere og standardnetværksforbindelser.

Som standard beskytter netværksbeskyttelse dine computere mod kendte skadelige URL-adresser ved hjælp af SmartScreen-feedet, som blokerer skadelige URL-adresser på samme måde som SmartScreen i Microsoft Edge-browseren. Funktionaliteten til netværksbeskyttelse kan udvides til:

- Bloker IP/URL-adresse fra din egen Threat Intel (indikatorer)
- Bloker ikke-registrerede tjenester fra Microsoft Defender for Cloud Apps (tidligere Microsoft Cloud App Security)
- Bloker websteder baseret på kategori (filtrering af webindhold)

Network Protection er en vigtig del af Microsofts beskyttelses- og svarstak.

Du kan finde flere oplysninger om Netværksbeskyttelse til Windows Server, Linux, MacOS og MTD under [Proaktiv jagt efter trusler med avanceret jagt](advanced-hunting-overview.md).

### <a name="block-command-and-control-c2-attacks"></a>C2-angreb (Block Command and Control)

C2-servercomputere bruges af ondsindede brugere til at sende kommandoer til systemer, der er kompromitteret af malware, og derefter udøve en form for kontrol over kompromitterede systemer. C2-angreb skjules typisk i cloudbaserede tjenester som fildeling og webmailtjenester, hvilket gør det muligt for C2-serverne at undgå registrering ved at blande sig med typisk trafik.

C2-servere kan bruges til at starte kommandoer, der kan:

- stjæle data (f.eks. ved hjælp af phishing)
- styre kompromitterede computere i et botnet
- afbryde legitime programmer
- sprede malware, f.eks. ransomware

Netværksbeskyttelseskomponenten i Microsoft Defender for Endpoint identificerer og blokerer forbindelser til C2-infrastrukturer, der bruges i menneskedrevne ransomware-angreb, ved hjælp af teknikker som maskinel indlæring og intelligent identifikation af kompromitteret (IoC).

#### <a name="network-protection-new-toast-notifications"></a>Netværksbeskyttelse: Nye toastbeskeder

| Ny tilknytning  | Svarkategori  | Kilder |
| :--- | :--- | :--- |
| Phishing | Phishing | Smartscreen |
| Skadelig | Skadelig | Smartscreen |
| kommando og kontrolelement | C2 | Smartscreen |
| kommando og kontrolelement | COCO | Smartscreen |
| Skadelig | Untrusted | Smartscreen |
| af it-administratoren | CustomBlockList |   |
| af it-administratoren | Brugerdefineret politik |   |

> [!NOTE]
> **customAllowList** genererer ikke meddelelser på slutpunkter.

### <a name="new-notifications-for-network-protection-determination"></a>Nye meddelelser til bestemmelse af netværksbeskyttelse

En ny offentligt tilgængelig funktion i netværksbeskyttelse bruger funktioner i SmartScreen til at blokere phishing-aktiviteter fra skadelige kommando- og kontrolwebsteder.

Når en slutbruger forsøger at besøge et websted i et miljø, hvor netværksbeskyttelse er aktiveret, er der tre mulige scenarier:

- URL-adressen har et **kendt godt omdømme** – I dette tilfælde har brugeren tilladelse til at få adgang uden hindring, og der vises ingen toastbesked på slutpunktet. Domænet eller URL-adressen er reelt angivet til _Tilladt_.
- URL-adressen har et **ukendt eller usikkert omdømme** – Brugerens adgang er blokeret, men med muligheden for at omgå (fjerne blokeringen) blokken. Domænet eller URL-adressen er reelt angivet til _Overvågning_.
- URL-adressen har et **kendt dårligt (skadeligt) omdømme** – Brugeren forhindres i at få adgang. Domænet eller URL-adressen er reelt angivet til _Bloker_.

#### <a name="warn-experience"></a>Advar-oplevelse

En bruger besøger et websted:

- Hvis URL-adressen har et ukendt eller usikkert omdømme, vil en toastbesked give brugeren følgende muligheder:

  - **Ok** – Toastmeddelelsen frigives (fjernes), og forsøget på at få adgang til webstedet er afsluttet.
  - **Fjern blokering** – Brugeren behøver ikke at få adgang til Windows Defender Security Intelligence-portalen (WDSI) for at få adgang til webstedet. Brugeren har adgang til webstedet i 24 timer. på hvilket tidspunkt blokken kan genbruges i yderligere 24 timer. Brugeren kan fortsætte med at bruge **Fjern blokering** til at få adgang til webstedet, indtil administratoren forbyder (blokerer) webstedet og dermed fjerner muligheden for at **fjerne blokeringen**.
  - **Feedback** – Toastmeddelelsen giver brugeren et link til at indsende en billet, som brugeren kan bruge til at sende feedback til administratoren i et forsøg på at retfærdiggøre adgangen til webstedet.

  > [!div class="mx-imgBorder"]
  > ![Viser en advarsel om advarsel om phishing-indhold til netværksbeskyttelse](images/network-protection-phishing-warn-2.png)

  > [BEMÆRK!] De billeder, der vises her for at advare og blokere (nedenfor), indeholder begge en liste over **"blokeret URL-adresse"** som eksempelpladsholdertekst. i et fungerende miljø vises den faktiske URL-adresse eller det faktiske domæne.  

#### <a name="block-experience"></a>Blokoplevelse

En bruger besøger et websted:

- Hvis URL-adressen har et dårligt omdømme, vil en toastbesked give brugeren følgende muligheder:
  - **Ok** Toastbeskeden frigives (fjernes), og forsøget på at få adgang til webstedet afsluttes.
  - **Feedback** Toastbeskeden giver brugeren et link til at indsende en billet, som brugeren kan bruge til at sende feedback til administratoren i et forsøg på at retfærdiggøre adgangen til webstedet.
  
  > [!div class="mx-imgBorder"]
  > ![ Viser en kendt meddelelse om blokeret phishing-indhold i netværksbeskyttelse](images/network-protection-phishing-blocked.png)

### <a name="network-protection-c2-detection-and-remediation"></a>Netværksbeskyttelse: C2-registrering og -afhjælpning

I sin oprindelige form er ransomware en råvaretrussel, forudprogrammeret og fokuseret på begrænsede, specifikke resultater (for eksempel kryptering af en computer). Dog, ransomware har udviklet sig til en sofistikeret trussel, der er menneskeligt drevne, adaptive, og fokuserede på større skala og mere udbredte resultater; som at opbevare en hel organisations aktiver eller data som løsesum.

Understøttelse af kommando og kontrol (C2) er en vigtig del af denne ransomware-udvikling og er det, der gør det muligt for disse angreb at tilpasse sig det miljø, de er målrettet mod. At bryde linket til kommando- og kontrolinfrastrukturen betyder at stoppe et angrebs forløb til næste fase.

#### <a name="detecting-and-remediating-cobaltstrike-public-preview"></a>Registrering og afhjælpning af CobaltStrike (offentlig prøveversion)

En af de mest almindelige rammer efter udnyttelse, der bruges i menneskeligt drevne ransomware-angreb, er CobaltStrike. Threat Intelligence-teams på tværs af Microsoft spor _taktik, teknikker og procedurer_ (TTP'er) på flere aktivitetsgrupper, der installerer ransomware for at identificere adfærdsmønstre, der kan bruges til at forsvare sig mod specifikke strategier og trusselsvektorer, der bruges af ondsindede aktører. Disse ransomware aktivitetsgrupper alle, på et tidspunkt i angrebet livscyklus, involverer installation af en CobaltStrike Beacon til et offer computer for at aktivere praktisk tastaturaktivitet.

CobaltStrike muliggør tilpasning af flere aspekter af angrebet, fra evnen til at hoste flere lyttere, der reagerer på forskellige protokoller, til hvordan hovedkomponenten på klientsiden (Beacon) skal udføre kodeinjektion og køre job efter udnyttelse. Når Microsoft Defender registrerer CobaltStrike, kan den på intelligent vis finde og indsamle nøgleindikatorer for kompromis (IoC). Når disse indikatorer er registreret, deles de i Microsofts produktstak med henblik på registrering og beskyttelse.

Microsoft Defenders kommando- og kontrolregistrering er ikke begrænset til CobaltStrike. Microsoft Defender kan registrere vigtige IOCs for flere malwarefamilier. Indikatorerne deles på tværs af Microsofts beskyttelsesstak for at beskytte kunder og advare dem, hvis der er et kompromis.

Blokering af kommando- og kontrolkommunikation kan hæmme et målrettet angreb alvorligt, hvilket giver forsvarerne tid til at finde de første indgangsvektorer og lukke dem ned før et andet forsøg på angreb.

<!-- Hide {this intro with no subsequent list items}
[For additional details about Microsoft Defender's command and control detection, see **ADD LINK TO BLOG**.]
-->

## <a name="smart-screen-unblock"></a>Fjern blokering af smart skærm

En ny funktion i Microsoft Defender for Endpoint-indikatorer giver administratorer mulighed for at give slutbrugere mulighed for at omgå "advarsler", der er genereret for nogle URL-adresser og IP-adresser. Afhængigt af hvorfor URL-adressen blev blokeret, kan det give administratorer mulighed for at fjerne blokeringen af webstedet i op til 24 timer, når der opstår en smartskærmblokering. I sådanne tilfælde vises en Windows Security-toastbesked, der giver slutbrugeren mulighed for at **fjerne blokeringen** af URL-adressen eller IP-adressen i den definerede tidsperiode.  

 > [!div class="mx-imgBorder"]
 > ![ Windows Sikkerhedsmeddelelse til netværksbeskyttelse](images/network-protection-smart-screen-block-notification.png)

Microsoft Defender for Endpoint Administratorer kan konfigurere funktionen Til fjernelse af blokering af smart skærm i [Microsoft 365 Defender](https://security.microsoft.com/) ved hjælp af følgende konfigurationsværktøj. Gå til stien til ConfigToolName fra Microsoft 365 Defender-portalen.

<!-- Hide {this intro with no subsequent list items}
[Line 171: Delete the colon and the right angle-brackets. The resulting sentence will be "From the [MS365 Defender] portal, navigate to path to ConfigToolName." Delete "to" and add "the" before path unless a specific description is available. Would a screenshot help? Normally angle brackets or arrows are used in place of certain text rather than in addition.]
-->

 > [!div class="mx-imgBorder"]
 > ![Konfiguration af ULR og IP-formular til smartskærmsblokering i netværksbeskyttelse](images/network-protection-smart-screen-block-configuration.png)

## <a name="using-network-protection"></a>Brug af netværksbeskyttelse

Netværksbeskyttelse er aktiveret pr. enhed, hvilket typisk gøres ved hjælp af din administrationsinfrastruktur. Du kan se understøttede metoder under [Slå netværksbeskyttelse til](enable-network-protection.md).

> [!NOTE]
> Microsoft Defender Antivirus skal være aktiv for at aktivere netværksbeskyttelse.

Du kan aktivere Netværksbeskyttelse i **overvågningstilstand** eller **bloktilstand** . Hvis du vil evaluere effekten af at aktivere Network Protection, før du blokerer IP-adresser eller URL-adresser, kan du aktivere den i overvågningstilstand i en periode for at indsamle data om, hvad der ville blive blokeret. Overvågningstilstand logfører, når slutbrugerne har oprettet forbindelse til en adresse eller et websted, der ellers ville være blevet blokeret af netværksbeskyttelse.

## <a name="advanced-hunting"></a>Avanceret jagt

Hvis du bruger Avanceret jagt til at identificere overvågningshændelser, har du op til 30 dages historik tilgængelig fra konsollen. Se [Avanceret jagt](advanced-hunting-overview.md).

Du kan finde overvågningsdataene i **Avanceret jagt** på Microsoft Defender for Endpoint-portalen.  

Hændelserne er i DeviceEvents med en ActionType af ExploitGuardNetworkProtectionAudited. Blokke vises af ExploitGuardNetworkProtectionBlocked.  

Følgende eksempel indeholder de blokerede handlinger:

DeviceEvents

- Where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked')

 > [!div class="mx-imgBorder"]
 > ![Avanceret søgning efter overvågning og identificering af hændelser](images/network-protection-advanced-hunting.png)

> [!TIP]
> Disse poster indeholder data i kolonnen AdditionalFields, som giver dig gode oplysninger om handlingen. Hvis du udvider AdditionalFields, kan du også hente felterne: **IsAudit**, **ResponseCategory** og **DisplayName**.

DeviceEvents:

- hvor ActionType indeholder "ExploitGuardNetworkProtection"
- udvid ParsedFields=parse_json(AdditionalFields)
- project DeviceName, ActionType, Timestamp, RemoteUrl, InitiatingProcessFileName, IsAudit=tostring(ParsedFields.IsAudit), ResponseCategory=tostring(ParsedFields.ResponseCategory), DisplayName=tostring(ParsedFields.DisplayName)
- sortér efter tidsstempelafskr.

Svarkategorien fortæller dig, hvad der forårsagede hændelsen, f.eks.:

| Svarkategori | Funktion, der er ansvarlig for hændelsen |
|:---|:---|
| Brugerdefineret politik |  WCF  |
| CustomBlockList  |   Brugerdefinerede indikatorer   |
| CasbPolicy   |   Defender for Cloud Apps   |
| Skadelig   |   Webtrusler  |
| Phishing  |   Webtrusler  |

Du kan finde flere oplysninger under [Fejlfinding af slutpunktblokke](web-protection-overview.md#troubleshoot-endpoint-blocks).

Du kan bruge den resulterende liste over URL-adresser og IP-adresser til at bestemme, hvad der ville være blevet blokeret, hvis enheden var i blokeringstilstand, samt hvilken funktion der blokerede dem. Gennemse hvert element på listen for at identificere URL-adresser eller IP-adresser, uanset om der er nødvendige i dit miljø. Hvis du finder poster, der er blevet overvåget, og som er kritiske for dit miljø, skal du oprette en indikator, der tillader dem på dit netværk. Tillad, at URL-adresser/IP-indikatorer tilsidesætter en hvilken som helst blok.

Når du har oprettet en indikator, kan du se på, hvordan du løser det underliggende problem:

- Smartskærm – anmod om gennemsyn
- Indikator – rediger eksisterende indikator
- MCA – gennemse ikke-sanktioneret APP
- WCF – omkategorisering af anmodning

Ved hjælp af disse data kan du træffe en informeret beslutning om at aktivere Netværksbeskyttelse i bloktilstand. Se [Rangorden for netværksbeskyttelsesblokke](web-protection-overview.md#order-of-precedence).

> [!NOTE]
> Da dette er en indstilling pr. enhed, hvis der er enheder, der ikke kan flytte til bloktilstand, kan du blot lade dem være på overvågning, indtil du kan rette op på udfordringen, og du vil stadig modtage overvågningshændelserne.

Du kan få oplysninger om, hvordan du rapporterer falske positiver, under [Rapportér falske positiver](web-protection-overview.md#report-false-positives).

Du kan finde oplysninger om, hvordan du opretter dine egne Power BI-rapporter, under [Opret brugerdefinerede rapporter ved hjælp af Power BI](api-power-bi.md).

## <a name="configuring-network-protection"></a>Konfiguration af netværksbeskyttelse

Du kan få mere at vide om, hvordan du aktiverer netværksbeskyttelse, under **[Aktivér netværksbeskyttelse](enable-network-protection.md)**. Brug Gruppepolitik, PowerShell eller MDM-CSP'er til at aktivere og administrere netværksbeskyttelse på dit netværk.

Når du har aktiveret tjenesterne, skal du muligvis konfigurere netværket eller firewallen for at tillade forbindelser mellem tjenesterne og dine enheder (også kaldet slutpunkter).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="viewing-network-protection-events"></a>Visning af netværksbeskyttelseshændelser

Netværksbeskyttelse fungerer bedst sammen med [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md), som giver dig detaljeret rapportering om hændelser og blokke for udnyttelse af beskyttelse som en del af [scenarier med undersøgelse af beskeder](investigate-alerts.md).

Når netværksbeskyttelse blokerer en forbindelse, vises der en meddelelse fra Løsningscenter. Dit team af sikkerhedshandlinger kan [tilpasse meddelelsen](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) med din organisations oplysninger og kontaktoplysninger. Derudover kan individuelle regler for reduktion af angrebsoverfladen aktiveres og tilpasses, så de passer til visse teknikker, der skal overvåges.

Du kan også bruge [overvågningstilstand](audit-windows-defender.md) til at evaluere, hvordan netværksbeskyttelse vil påvirke din organisation, hvis den er aktiveret.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Gennemse netværksbeskyttelseshændelser på Microsoft 365 Defender-portalen

Microsoft Defender for Endpoint giver detaljeret rapportering om hændelser og blokke som en del af [scenarierne til undersøgelse af vigtige beskeder](investigate-alerts.md). Du kan få vist disse oplysninger på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i [beskedkøen](review-alerts.md) eller ved hjælp af [avanceret jagt](advanced-hunting-overview.md). Hvis du bruger [overvågningstilstand](audit-windows-defender.md), kan du bruge avanceret jagt til at se, hvordan indstillinger for netværksbeskyttelse vil påvirke dit miljø, hvis de er aktiveret.

Her er et eksempel på en forespørgsel om avanceret jagt:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Gennemse netværksbeskyttelseshændelser i Windows Logbog

Du kan gennemse Windows-hændelsesloggen for at se hændelser, der oprettes, når netværksbeskyttelse blokerer (eller overvåger) adgang til en skadelig IP-adresse eller et skadeligt domæne:

1. [Kopiér XML-koden direkte](event-views.md).

2. Vælg **OK**.

Denne procedure opretter en brugerdefineret visning, der filtrerer for kun at vise følgende hændelser, der er relateret til netværksbeskyttelse:

****

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1125|Hændelse, når netværksbeskyttelse udløses i overvågningstilstand|
|1126|Hændelse, når netværksbeskyttelse udløses i bloktilstand|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Netværksbeskyttelse og TCP-trevejs-håndtryk

Med netværksbeskyttelse afgøres det, om der skal tillades eller blokeres adgang til et websted, efter at [det trevejshåndtryk er fuldført via TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Når et websted er blokeret af netværksbeskyttelse, kan du derfor se en handlingstype `ConnectionSuccess` under `NetworkConnectionEvents` i Microsoft 365 Defender-portalen, selvom webstedet faktisk blev blokeret. `NetworkConnectionEvents` rapporteres fra TCP-laget og ikke fra netværksbeskyttelse. Når det trevejs-håndtryk er fuldført, er adgang til webstedet tilladt eller blokeret af netværksbeskyttelse.

Her er et eksempel på, hvordan det fungerer:

1. Lad os antage, at en bruger forsøger at få adgang til et websted på sin enhed. Webstedet hostes tilfældigvis på et farligt domæne, og det bør blokeres af netværksbeskyttelse.  

2. Det trevejs-håndtryk via TCP/IP begynder. Før den fuldføres, logføres en `NetworkConnectionEvents` handling, og den `ActionType` er angivet som `ConnectionSuccess`. Men så snart den trevejshandtryksproces er fuldført, blokerer netværksbeskyttelse adgangen til webstedet. Alt dette sker meget hurtigt. En lignende proces forekommer med [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview). Det er, når det trevejshåndtryk fuldfører, at der foretages en bestemmelse, og adgang til et websted enten er blokeret eller tilladt.

3. I Microsoft 365 Defender-portalen vises der en besked i [beskedkøen](alerts-queue.md). Oplysningerne om denne besked omfatter både `NetworkConnectionEvents` og `AlertEvents`. Du kan se, at webstedet er blokeret, selvom du også har et `NetworkConnectionEvents` element med ActionType for `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Overvejelser i forbindelse med virtuelt Windows-skrivebord, der kører Windows 10 Enterprise Multi-Session

På grund af windows 10 Enterprise's karakter af flere brugere skal du være opmærksom på følgende:

1. Netværksbeskyttelse er en funktion i hele enheden og kan ikke målrettes til bestemte brugersessioner.

2. Politikker til filtrering af webindhold er også enhedsdækkende.

3. Hvis du har brug for at skelne mellem brugergrupper, kan du overveje at oprette separate Windows Virtual Desktop-værtsgrupper og -tildelinger.

4. Test netværksbeskyttelse i overvågningstilstand for at vurdere dens funktionsmåde, før den udrulles.

5. Overvej at ændre størrelsen på udrulningen, hvis du har et stort antal brugere eller et stort antal sessioner med flere brugere.

### <a name="alternative-option-for-network-protection"></a>Alternativ mulighed for netværksbeskyttelse

For Windows 10 Enterprise Multi-Session 1909 og nyere, der bruges i Windows Virtual Desktop på Azure, kan netværksbeskyttelse til Microsoft Edge aktiveres ved hjælp af følgende metode:

1. Brug [Slå netværksbeskyttelse](enable-network-protection.md) til, og følg vejledningen for at anvende din politik.

2. Udfør følgende PowerShell-kommandoer:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Fejlfinding af netværksbeskyttelse

På grund af det miljø, hvor netværksbeskyttelse kører, kan Microsoft muligvis ikke registrere operativsystemets proxyindstillinger. I nogle tilfælde kan klienter til netværksbeskyttelse ikke oprette forbindelse til Cloud Service. For at løse forbindelsesproblemet skal kunder med E5-licenser konfigurere en af følgende registreringsdatabasenøgler:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="optimizing-network-protection-performance"></a>Optimering af ydeevnen for netværksbeskyttelse

Netværksbeskyttelse har nu en optimering af ydeevnen, der gør det muligt for Bloker-tilstand at starte asynkront undersøgelse af lange forbindelser, når de er valideret og tilladt af SmartScreen, hvilket kan give en potentiel reduktion i omkostningerne for, at inspektionen har på båndbredden, og kan også hjælpe med problemer med appkompatibilitet. Denne optimeringsfunktion er som standard slået til. Du kan slå denne funktion fra ved hjælp af følgende PowerShell-cmdlet:

`Set-MpPreference -AllowSwitchToAsyncInspection $false`

## <a name="see-also"></a>Se også

- [Evaluer | netværksbeskyttelse](evaluate-network-protection.md) Tag et hurtigt scenarie, der viser, hvordan funktionen fungerer, og hvilke hændelser der typisk oprettes.
- [Aktivér netværksbeskyttelse](enable-network-protection.md) | Brug Gruppepolitik, PowerShell eller MDM-CSP'er til at aktivere og administrere netværksbeskyttelse på dit netværk.
- [Konfiguration af funktioner til reduktion af angrebsoverfladen i Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
