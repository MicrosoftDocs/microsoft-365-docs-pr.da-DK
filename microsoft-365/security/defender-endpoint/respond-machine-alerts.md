---
title: Udfør svarhandlinger på en enhed i Microsoft Defender for Endpoint
description: Udfør svarhandlinger på en enhed, f.eks. isolering af enheder, indsamling af en undersøgelsespakke, administration af mærker, kørsel af av-scanning og begrænsning af udførelse af apps.
keywords: reagere, isolere, isolere enhed, indsamle undersøgelsespakke, handlingscenter, begrænse, administrere mærker, gennemsnitlig scanning, begrænse app
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c104b7fefae6ad02c9fb46b7d21522c21a2f6895
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014587"
---
# <a name="take-response-actions-on-a-device"></a>Udfør svarhandlinger på en enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1 og 2](defender-endpoint-plan-1-2.md)
- [Microsoft Defender for Business](/microsoft-365/security/defender-business/mdb-overview)

[!INCLUDE [Prerelease information](../../includes/prerelease.md)]

Reagere hurtigt på registrerede angreb ved at isolere enheder eller indsamle en undersøgelsespakke. Når du har foretaget en handling på enheder, kan du kontrollere aktivitetsoplysningerne i Løsningscenter.

Svarhandlinger kører langs toppen af en bestemt enhedsside og omfatter:

- Administrer mærker
- Initier automatiseret undersøgelse
- Start live-svarsession
- Hent undersøgelsespakke
- Kør antivirusscanning
- Begræns appudførelse
- Isoler enhed
- Indeholder enhed
- Kontakt en trusselsekspert
- Handlingscenter

[![Billede af svarhandlinger.](images/response-actions.png)](images/response-actions.png#lightbox)

> [!IMPORTANT]
> [Defender for Endpoint Plan 1](defender-endpoint-plan-1.md) og [Microsoft Defender til virksomheder](../defender-business/mdb-overview.md) kun indeholde følgende manuelle svarhandlinger:
> - Kør antivirusscanning
> - Isoler enhed
> - Stop og sæt en fil i karantæne
> - Tilføj en indikator for at blokere eller tillade en fil Dit abonnement skal omfatte Defender for Endpoint Plan 2 for at få alle de svarhandlinger, der er beskrevet i denne artikel.

 Du kan finde enhedssider fra en af følgende visninger:

- **Dashboard til sikkerhedshandlinger** – Vælg et enhedsnavn på kortet Enheder med risiko.
- **Beskedkø** – Vælg enhedsnavnet ud for enhedsikonet fra beskedkøen.
- **Liste over enheder** – Vælg overskriften for enhedsnavnet på listen over enheder.
- **Søgefelt** – Vælg Enhed i rullemenuen, og angiv enhedsnavnet.

> [!IMPORTANT]
> - Disse svarhandlinger er kun tilgængelige for enheder på Windows 10, version 1703 eller nyere, Windows 11, Windows Server 2019 og Windows Server 2022.
> - For platforme, der ikke er Windows, er svarfunktioner (f.eks. enhedsisolation) afhængige af tredjepartsfunktionerne.
> - For Microsofts førstepartsagenter skal du se linket "flere oplysninger" under hver funktion for at få vist minimumkrav til operativsystemet.

## <a name="manage-tags"></a>Administrer mærker

Tilføj eller administrer mærker for at oprette en logisk gruppetilhørsforhold. Enhedskoder understøtter korrekt tilknytning af netværket, så du kan vedhæfte forskellige mærker for at registrere kontekst og aktivere oprettelse af dynamiske lister som en del af en hændelse.

Du kan få flere oplysninger om enhedsmærkning under [Opret og administrer enhedskoder](machine-tags.md).

## <a name="initiate-automated-investigation"></a>Initier automatiseret undersøgelse

Du kan starte en ny automatiseret undersøgelse til generelle formål på enheden, hvis det er nødvendigt. Mens der kører en undersøgelse, føjes alle andre beskeder, der genereres fra enheden, til en igangværende automatiseret undersøgelse, indtil undersøgelsen er fuldført. Hvis den samme trussel ses på andre enheder, føjes disse enheder desuden til undersøgelsen.

Du kan få flere oplysninger om automatiserede undersøgelser under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

## <a name="initiate-live-response-session"></a>Start live-svarsession

Live response er en funktion, der giver dig øjeblikkelig adgang til en enhed ved hjælp af en ekstern shellforbindelse. Dette giver dig mulighed for at udføre dybdegående undersøgelsesarbejde og reagere øjeblikkeligt for straks at indeholde identificerede trusler i realtid.

Liverespons er designet til at forbedre undersøgelser ved at gøre det muligt for dig at indsamle retsmedicinske data, køre scripts, sende mistænkelige enheder til analyse, afhjælpe trusler og proaktivt jage efter nye trusler.

Du kan få flere oplysninger om live-svar under [Undersøg enheder på enheder, der bruger live-svar](live-response.md).

## <a name="collect-investigation-package-from-devices"></a>Indsaml undersøgelsespakke fra enheder

Som en del af undersøgelses- eller svarprocessen kan du indsamle en undersøgelsespakke fra en enhed. Ved at indsamle undersøgelsespakken kan du identificere enhedens aktuelle tilstand og yderligere forstå de værktøjer og teknikker, der bruges af hackeren.

> [!IMPORTANT]
> Disse handlinger understøttes ikke i øjeblikket for enheder, der kører macOS eller Linux. Brug direkte svar til at køre handlingen. Du kan få flere oplysninger om livesvar under [Undersøg enheder på enheder, der bruger liverespons](live-response.md)

Sådan downloader du pakken (zip-filen) og undersøger de hændelser, der opstod på en enhed

1. Vælg **Indsaml undersøgelsespakke** fra rækken af svarhandlinger øverst på enhedssiden.

2. Angiv i tekstfeltet, hvorfor du vil udføre denne handling. Vælg **Bekræft**.

3. Zip-filen downloades

Alternativ måde:

1. Vælg **Handlingscenter** i afsnittet svarhandlinger på enhedssiden.

   :::image type="content" source="images/action-center-package-collection.png" alt-text="Indstillingen Løsningscenter" lightbox="images/action-center-package-collection.png":::

2. Vælg **Pakkeindsamlingspakke, der er tilgængelig** for at downloade zip-filen, i Fly-out i Løsningscenter.

   :::image type="content" source="images/collect-package.png" alt-text="Indstillingen downloadpakke" lightbox="images/collect-package.png":::

Pakken indeholder følgende mapper:

|Mappe|Beskrivelse|
|---|---|
|Autoruns|Indeholder et sæt filer, der hver især repræsenterer indholdet af registreringsdatabasen for et kendt ASEP (Auto Start Entry Point) for at hjælpe med at identificere angriberens vedholdenhed på enheden. <p> <div class="alert"><b>BEMÆRK:</b> Hvis registreringsdatabasenøglen ikke findes, indeholder filen følgende meddelelse: "ERROR: Systemet kunne ikke finde den angivne registreringsdatabasenøgle eller -værdi".<div>|
|Installerede programmer|Denne .CSV fil indeholder en liste over installerede programmer, der kan hjælpe med at identificere, hvad der er installeret på enheden i øjeblikket. Du kan få flere oplysninger [under Win32_Product klasse](https://go.microsoft.com/fwlink/?linkid=841509).|
|Netværksforbindelser|Denne mappe indeholder et sæt datapunkter, der er relateret til forbindelsesoplysningerne, som kan hjælpe med at identificere forbindelsen til mistænkelige URL-adresser, infrastruktur for hackerkommandoer og -styringer (C&C), eventuelle tværgående bevægelser eller fjernforbindelser. <ul><li>ActiveNetConnections.txt: Viser protokolstatistik og aktuelle TCP/IP-netværksforbindelser. Giver mulighed for at søge efter mistænkelig forbindelse foretaget af en proces.</li><li>Arp.txt: Viser de aktuelle ARP-cachetabeller (Address Resolution Protocol) for alle grænseflader. ARP-cachen kan afsløre andre værter på et netværk, der er blevet kompromitteret eller mistænkelige systemer på netværket, som kan have været brugt til at køre et internt angreb.</il><li>DnsCache.txt: Viser indholdet af DNS-klientreklarercachen, som indeholder både poster, der er forudindlæset fra den lokale Hosts-fil, og eventuelle nyligt hentede ressourceposter for navneforespørgsler, der fortolkes af computeren. Dette kan hjælpe med at identificere mistænkelige forbindelser.</li><li>IpConfig.txt: Viser den fulde TCP/IP-konfiguration for alle adaptere. Adaptere kan repræsentere fysiske grænseflader, f.eks. installerede netværkskort eller logiske grænseflader, f.eks. opkaldsforbindelser.</li><li>FirewallExecutionLog.txt og pfirewall.log</li></ul><p><div class="alert"><b>BEMÆRK:</b> Filen pfirewall.log skal findes i %windir%\system32\logfiles\firewall\pfirewall.log, så den medtages i undersøgelsespakken. Du kan få flere oplysninger om, hvordan du opretter firewalllogfilen, under [Konfigurer Windows Defender Firewall med avanceret sikkerhedslogfil](/windows/security/threat-protection/windows-firewall/configure-the-windows-firewall-log)<div>|
|Forudindstillede filer|Windows Prefetch-filer er designet til at fremskynde programstartprocessen. Det kan bruges til at spore alle de filer, der for nylig er brugt i systemet, og finde sporinger for programmer, der kan være blevet slettet, men stadig kan findes på listen over filer, der allerede findes. <ul><li>Prefetch-mappe: Indeholder en kopi af filerne fra `%SystemRoot%\Prefetch`. BEMÆRK! Det anbefales at downloade en filfremviser for at få vist de forudindstillede filer.</li><li>PrefetchFilesList.txt: Indeholder listen over alle de kopierede filer, der kan bruges til at spore, om der opstod kopieringsfejl i mappen prefetch.</li></ul>|
|Processer|Indeholder en .CSV fil, der viser de kørende processer, og gør det muligt at identificere aktuelle processer, der kører på enheden. Dette kan være nyttigt, når du identificerer en mistænkelig proces og dens tilstand.|
|Planlagte opgaver|Indeholder en .CSV fil, der viser de planlagte opgaver, som kan bruges til at identificere rutiner, der udføres automatisk på en valgt enhed, for at søge efter mistænkelig kode, der er indstillet til at køre automatisk.|
|Log over sikkerhedshændelser|Indeholder sikkerhedshændelsesloggen, som indeholder poster for logon- eller logoutaktivitet eller andre sikkerhedsrelaterede hændelser, der er angivet af systemets overvågningspolitik. <p><div class="alert"><b>BEMÆRK:</b> Åbn hændelseslogfilen ved hjælp af Logbog.</div>|
|Tjenester|Indeholder en .CSV fil, der viser tjenester og deres tilstande.|
|Windows SMB-sessioner (Server Message Block)|Viser delt adgang til filer, printere og serielle porte og diverse kommunikation mellem noder på et netværk. Dette kan hjælpe med at identificere dataudfiltrering eller tværgående bevægelse. <p> Indeholder filer til SMBInboundSessions og SMBOutboundSession. <p> <div class="alert"><b>BEMÆRK:</b> Hvis der ikke er nogen sessioner (indgående eller udgående), får du vist en tekstfil, der fortæller dig, at der ikke blev fundet nogen SMB-sessioner.</div>|
|Systemoplysninger|Indeholder en SystemInformation.txt fil, der viser systemoplysninger, f.eks. operativsystemversion og netværkskort.|
|Midlertidige mapper|Indeholder et sæt tekstfiler, der viser de filer, der er placeret i %Temp% for hver bruger i systemet. <p> Dette kan hjælpe med at spore mistænkelige filer, som en hacker kan have mistet på systemet. <p> <div class="alert"><b>BEMÆRK:</b> Hvis filen indeholder følgende meddelelse: "Systemet kan ikke finde den angivne sti", betyder det, at der ikke er nogen temp-mappe til denne bruger, og det kan skyldes, at brugeren ikke loggede på systemet.</div>|
|Brugere og grupper|Indeholder en liste over filer, der hver især repræsenterer en gruppe og dens medlemmer.|
|WdSupportLogs|Leverer MpCmdRunLog.txt og MPSupportFiles.cab  <p> <div class="alert"><b>BEMÆRK:</b> Denne mappe oprettes kun på Windows 10 version 1709 eller nyere med opdateringspakken fra februar 2020 eller nyere installeret: <ul><li>Win10 1709 (RS3) Build 16299.1717: [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)</li><li>Win10 1803 (RS4) Build 17134.1345: [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)</li><li>Win10 1809 (RS5) Build 17763.1075: [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)</li><li>Win10 1903/1909 (19h1/19h2) Builds 18362.693 og 18363.693: [KB4535996](https://support.microsoft.com/help/4535996/windows-10-update-kb4535996)</li></ul> </div>|
|CollectionSummaryReport.xls|Denne fil er en oversigt over indsamlingen af undersøgelsespakken, den indeholder listen over datapunkter, den kommando, der bruges til at udtrække dataene, udførelsesstatussen og fejlkoden, hvis der er fejl. Du kan bruge denne rapport til at spore, om pakken indeholder alle de forventede data, og identificere, om der opstod fejl.|
|

## <a name="run-microsoft-defender-antivirus-scan-on-devices"></a>Kør Microsoft Defender Antivirus scanning på enheder

Som en del af undersøgelses- eller svarprocessen kan du fjernindsøge en antivirusscanning for at hjælpe med at identificere og afhjælpe malware, der kan være til stede på en kompromitteret enhed.

> [!IMPORTANT]
> - Denne handling understøttes ikke i øjeblikket for macOS og Linux. Brug direkte svar til at køre handlingen. Du kan få flere oplysninger om livesvar under [Undersøg enheder på enheder, der bruger liverespons](live-response.md)
> - En Microsoft Defender Antivirus (Microsoft Defender AV) scanning kan køre sammen med andre antivirusløsninger, uanset om Microsoft Defender AV er den aktive antivirusløsning eller ej. Microsoft Defender AV kan være i passiv tilstand. Du kan få flere oplysninger under [Microsoft Defender Antivirus kompatibilitet](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility).

Du har valgt **Kør antivirusscanning**, vælg den scanningstype, du vil køre (hurtig eller fuld), og tilføj en kommentar, før du bekræfter scanningen.

:::image type="content" source="images/run-antivirus.png" alt-text="Meddelelsen om at vælge hurtig scanning eller fuld scanning og tilføje kommentar" lightbox="images/run-antivirus.png":::

I Løsningscenter vises scanningsoplysningerne, og enhedens tidslinje indeholder en ny hændelse, hvilket afspejler, at der er sendt en scanningshandling på enheden. Microsoft Defender AV-beskeder afspejler alle registreringer, der vises under scanningen.

> [!NOTE]
> Når du udløser en scanning ved hjælp af En Defender for Endpoint-svarhandling, anvendes værdien 'ScanAvgCPULoadFactor' stadig for Microsoft Defender-antivirus, og den begrænser CPU-effekten af scanningen.
> Hvis ScanAvgCPULoadFactor ikke er konfigureret, er standardværdien en grænse på 50 % maksimal CPU-belastning under en scanning.
> Du kan få flere oplysninger under [configure-advanced-scan-types-microsoft-defender-antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-advanced-scan-types-microsoft-defender-antivirus).

## <a name="restrict-app-execution"></a>Begræns appudførelse

Ud over at indeholde et angreb ved at stoppe skadelige processer kan du også låse en enhed og forhindre efterfølgende forsøg på potentielt skadelige programmer i at køre.

> [!IMPORTANT]
> - Denne handling er tilgængelig for enheder på Windows 10, version 1709 eller nyere, Windows 11 og Windows Server 2019 eller nyere. 
> - Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus.
> - Denne handling skal opfylde Windows Defender politikformater og signeringskrav for programkontrolkodens integritet. Du kan få flere oplysninger under [Formater og signering af kodeintegritetspolitik](/windows/security/threat-protection/windows-defender-application-control/use-code-signing-to-simplify-application-control-for-classic-windows-applications)).

Hvis du vil begrænse et program fra at køre, anvendes der en kodeintegritetspolitik, der kun tillader, at filer køres, hvis de er signeret af et certifikat udstedt af Microsoft. Denne begrænsningsmetode kan hjælpe med at forhindre en hacker i at kontrollere kompromitterede enheder og udføre yderligere skadelige aktiviteter.

> [!NOTE]
> Du kan når som helst fortryde begrænsningen af programmer. Knappen på enhedssiden ændres til at sige **Fjern appbegrænsninger**, og derefter skal du udføre de samme trin som at begrænse udførelsen af appen.

Når du har valgt **Begræns udførelse af app** på enhedssiden, skal du skrive en kommentar og vælge **Bekræft**. I Løsningscenter vises scanningsoplysningerne, og enhedstidslinjen indeholder en ny hændelse.

:::image type="content" source="images/restrict-app-execution.png" alt-text="Meddelelsen om programbegrænsning" lightbox="images/restrict-app-execution.png":::

### <a name="notification-on-device-user"></a>Meddelelse på enhedsbruger

Når en app er begrænset, vises følgende meddelelse for at informere brugeren om, at en app er begrænset til at køre:

:::image type="content" source="images/atp-app-restriction.png" alt-text="Meddelelsen om programbegrænsning" lightbox="images/atp-app-restriction.png":::

> [!NOTE]
> Meddelelsen er ikke tilgængelig på Windows Server 2016 og Windows Server 2012 R2.

## <a name="isolate-devices-from-the-network"></a>Isoler enheder fra netværket

Afhængigt af alvorsgraden af angrebet og enhedens følsomhed kan det være en god idé at isolere enheden fra netværket. Denne handling kan hjælpe med at forhindre hackeren i at styre den kompromitterede enhed og udføre yderligere aktiviteter, f.eks. dataudfiltrering og tværgående bevægelse.

> [!IMPORTANT]
> - Isolering af enheder fra netværket understøttes ikke i øjeblikket for enheder, der kører macOS eller Linux. Brug direkte svar til at køre handlingen. Du kan få flere oplysninger om live-svar under [Undersøg enheder på enheder, der bruger live-svar](live-response.md).
> - Fuld isolation er tilgængelig for enheder, der kører Windows 11, Windows 10, version 1703 eller nyere, Windows Server 2022, Windows Server 2019 og Windows Server 2016.
> - Selektiv isolation er tilgængelig for enheder, der kører Windows 10, version 1709 eller nyere og Windows 11.
> - Når du isolerer en enhed, er det kun visse processer og destinationer, der er tilladt. Derfor kan enheder bag en fuld VPN-tunnel ikke nå den Microsoft Defender for Endpoint cloudtjeneste, når enheden er isoleret. Vi anbefaler, at du bruger en VPN til opdelt tunnelføring til Microsoft Defender for Endpoint og Microsoft Defender Antivirus skybaseret beskyttelsesrelateret trafik.

Denne enhedsisolationsfunktion afbryder forbindelsen mellem den kompromitterede enhed og netværket, samtidig med at forbindelsen til Defender for Endpoint-tjenesten bevares, og enheden overvåges fortsat.

På Windows 10 version 1709 eller nyere har du større kontrol over netværkets isolationsniveau. Du kan også vælge at aktivere Outlook, Microsoft Teams og Skype for Business forbindelse (også kaldet "Selektiv isolation").

> [!NOTE]
> Du kan til enhver tid genoprette forbindelsen til netværket. Knappen på enhedssiden ændres til **"Release from isolation"**, og derefter skal du udføre de samme trin som at isolere enheden.

Når du har valgt **Isoler enhed** på enhedssiden, skal du skrive en kommentar og vælge **Bekræft**. I Løsningscenter vises scanningsoplysningerne, og enhedstidslinjen indeholder en ny hændelse.

:::image type="content" source="images/isolate-device.png" alt-text="En side med oplysninger om en isoleret enhed" lightbox="images/isolate-device.png":::

> [!NOTE]
> Enheden forbliver tilsluttet Defender for Endpoint-tjenesten, selvom den er isoleret fra netværket. Hvis du har valgt at aktivere Outlook og Skype for Business kommunikation, kan du kommunikere med brugeren, mens enheden er isoleret.

### <a name="notification-on-device-user"></a>Meddelelse på enhedsbruger

Når en enhed isoleres, vises følgende meddelelse for at informere brugeren om, at enheden er isoleret fra netværket:

:::image type="content" source="images/atp-notification-isolate.png" alt-text="En meddelelse om ingen netværksforbindelse" lightbox="images/atp-notification-isolate.png":::

## <a name="contain-devices-from-the-network"></a>Indeholder enheder fra netværket

Når du har identificeret en ikke-administreret enhed, der er kompromitteret eller potentielt kompromitteret, kan det være en god idé at indeholde enheden fra netværket. Når du indeholder en enhed, blokerer enhver Microsoft Defender for Endpoint onboardede enhed indgående og udgående kommunikation med den pågældende enhed. Denne handling kan hjælpe med at forhindre, at tilstødende enheder kompromitteres, mens analytikeren af sikkerhedshandlinger finder, identificerer og afhjælper truslen på den kompromitterede enhed.

> [!NOTE]
> Blokering af indgående og udgående kommunikation med en "indeholdt" enhed understøttes på onboardede Microsoft Defender for Endpoint Windows 10 og Windows Server 2019+ enheder.

### <a name="how-to-contain-a-device"></a>Sådan indeholder du en enhed

1. Gå til siden **Enhedslager** , og vælg den enhed, der skal indeholdes.

2. Vælg **Medtag enhed** i menuen Handlinger i enhedens pop op-vindue.

:::image type="content" alt-text="Skærmbillede af pop op-meddelelsen med enhedens indhold." source="../../media/defender-endpoint/contain_device.png" lightbox="../../media/defender-endpoint/contain_device.png":::

3. Skriv en kommentar i pop op-vinduet med indeholder enheder, og vælg **Bekræft**.

:::image type="content" alt-text="Skærmbillede af menupunktet for enheden." source="../../media/defender-endpoint/contain_device_popup.png" lightbox="../../media/defender-endpoint/contain_device_popup.png":::

### <a name="contain-a-device-from-the-device-page"></a>Indeholder en enhed fra enhedssiden

En enhed kan også være indeholdt på enhedssiden ved at vælge **Medbring enhed** på handlingslinjen:

:::image type="content" alt-text="Skærmbillede af menupunktet med enhedens indhold på enhedssiden." source="../../media/defender-endpoint/contain_device_page.png" lightbox="../../media/defender-endpoint/contain_device_page.png":::

> [!NOTE]
> Det kan tage op til 5 minutter, før detaljerne om en nyligt indeholdt enhed når Microsoft Defender for Endpoint onboardede enheder.

> [!IMPORTANT]
> - Hvis en indeholdt enhed ændrer sin IP-adresse, genkender alle Microsoft Defender for Endpoint onboardede enheder dette og begynder at blokere kommunikation med den nye IP-adresse. Den oprindelige IP-adresse blokeres ikke længere (det kan tage op til fem minutter at se disse ændringer).  
> - I tilfælde, hvor den indeholdte enheds IP bruges af en anden enhed på netværket, vil der være en advarsel, mens den indeholder enheden, med et link til avanceret jagt (med en forudfyldt forespørgsel). Dette giver synlighed for de andre enheder, der bruger den samme IP-adresse, for at hjælpe dig med at træffe en bevidst beslutning, hvis du vil fortsætte med at indeholde enheden.
> - I de tilfælde, hvor den indeholdte enhed er en netværksenhed, vises der en advarsel med en meddelelse om, at dette kan medføre problemer med netværksforbindelsen (f.eks. indeholder en router, der fungerer som en standardgateway). På dette tidspunkt kan du vælge, om du vil indeholde enheden eller ej.

Hvis funktionsmåden ikke er som forventet, når du indeholder en enhed, skal du bekræfte, at tjenesten BFE (Base Filtering Engine) er aktiveret på de onboardede Defender for Endpoint-enheder.

### <a name="stop-containing-a-device"></a>Stop med at indeholde en enhed

Du kan når som helst stoppe med at indeholde en enhed.

1. Vælg enheden på **enhedslageret** , eller åbn enhedssiden.

2. Vælg **Frigiv fra opbevaring** i handlingsmenuen. Denne handling gendanner enhedens forbindelse til netværket.

## <a name="consult-a-threat-expert"></a>Kontakt en trusselsekspert

Du kan kontakte en Microsoft-trusselsekspert for at få mere indsigt i en potentielt kompromitteret enhed eller allerede kompromitterede enheder. Microsoft-trusselseksperter kan tilkobles direkte fra Microsoft 365 Defender for at få rettidig og præcis svar. Eksperter giver indsigt ikke kun vedrørende en potentielt kompromitteret enhed, men også for bedre at forstå komplekse trusler, målrettede angrebsmeddelelser, som du får, eller hvis du har brug for flere oplysninger om beskederne eller en trusselsintelligenskontekst, som du kan se på portaldashboardet.

Se [Kontakt en Microsoft Threat-ekspert](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) for at få flere oplysninger.

## <a name="check-activity-details-in-action-center"></a>Kontrollér aktivitetsdetaljer i Handlingscenter

**Løsningscenter** indeholder oplysninger om handlinger, der er udført på en enhed eller fil. Du kan få vist følgende oplysninger:

- Undersøgelsespakkesamling
- Antivirusscanning
- Appbegrænsning
- Enhedsisolation

Alle andre relaterede oplysninger vises også, f.eks. afsendelsesdato/-klokkeslæt, bruger, der indsender, og om handlingen lykkedes eller mislykkedes.

:::image type="content" source="images/action-center-details.png" alt-text="Handlingscenteret med oplysninger" lightbox="images/action-center-details.png":::


## <a name="see-also"></a>Se også

- [Udfør svarhandlinger på en fil](respond-file-alerts.md)
- [Manuelle svarhandlinger i Microsoft Defender for Endpoint Plan 1](defender-endpoint-plan-1.md#manual-response-actions)
- [Rapport unøjagtighed](/microsoft-365/security/defender-endpoint/tvm-security-recommendation#report-inaccuracy)
