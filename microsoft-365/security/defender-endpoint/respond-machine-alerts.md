---
title: Tag svarhandlinger på en enhed i Microsoft Defender for Endpoint
description: Tag svarhandlinger på en enhed, f.eks. isolere enheder, indsamling af en undersøgelsespakke, administration af mærker, kørsel af av-scanning og begrænsning af udførelse af apps.
keywords: svar, isoler, isoler enhed, indsaml undersøgelsespakke, handlingscenter, begræns, administrer mærker, av-scanning, begræns app
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
ms.openlocfilehash: f1fa77f33988893967e71b82cc81059429e41d55
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501283"
---
# <a name="take-response-actions-on-a-device"></a>Udføre svarhandlinger på en enhed

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender til virksomheder](/microsoft-365/security/defender-business/mdb-overview)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

Res responder hurtigt på registrerede angreb ved at isolere enheder eller ved at indsamle en undersøgelsespakke. Når du har taget skridtet videre på enheder, kan du kontrollere oplysninger om aktivitet i Handlingscenter.

Svarhandlinger kører langs toppen af en bestemt enhedsside og omfatter:

- Administrer mærker
- Initier automatiseret undersøgelse
- Start direkte svarsession
- Pakke til samlet undersøgelse
- Kør antivirusscanning
- Begræns appudførelse
- Isoler enhed
- Kontakt en trusselsekspert
- Handlingscenter

[![Billede af svarhandlinger.](images/response-actions.png)](images/response-actions.png#lightbox)


 Du kan finde enhedssider fra en af følgende visninger:

- **Dashboard for sikkerhedshandlinger** – Vælg et enhedsnavn fra kortet Enheder, der er i fare.
- **Kø til beskeder** – Vælg enhedsnavnet ud for enhedsikonet i køen med vigtige beskeder.
- **Listen Enheder** – Vælg overskriften på enhedsnavnet på listen over enheder.
- **Søgefelt** – Vælg Enhed i rullemenuen, og angiv enhedsnavnet.

> [!IMPORTANT]
>
> - Disse svarhandlinger er kun tilgængelige for enheder på Windows 10, version 1703 eller nyere, Windows 11, Windows Server 2019 og Windows Server 2022.
> - For ikke-Windows-platforme afhænger svaregenskaber (f.eks enhedsisolation) af tredjepartsfunktionerne.
> - Microsofts tredjepartsagenter kan se linket "flere oplysninger" under hver funktion for minimumskrav til operativsystemet.

## <a name="manage-tags"></a>Administrer mærker

Tilføj eller administrer mærker for at oprette en logisk gruppetilhørsforhold. Enhedsmærker understøtter korrekt tilknytning af netværket, så du kan vedhæfte forskellige mærker for at registrere kontekst og aktivere dynamisk oprettelse af lister som en del af en hændelse.

Du kan finde flere oplysninger om enhedsmærkning under [Opret og administrer enhedsmærker](machine-tags.md).

## <a name="initiate-automated-investigation"></a>Initier automatiseret undersøgelse

Du kan starte en ny generel automatiseret undersøgelse på enheden, hvis det er nødvendigt. Mens en undersøgelse kører, føjes alle andre beskeder, der genereres fra enheden, til en igangværende automatisk undersøgelse, indtil undersøgelsen er afsluttet. Hvis den samme trussel kan ses på andre enheder, føjes disse enheder til undersøgelsen.

Få mere at vide om automatiserede undersøgelser under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

## <a name="initiate-live-response-session"></a>Initier direkte svarsession

Direkte svar er en funktion, der giver dig øjeblikkelig adgang til en enhed ved hjælp af en forbindelse til en fjern shell. Dette giver dig mulighed for at udføre en dybdegående indsats og reagere omgående for at kunne inddæmme identificerede trusler i realtid.

Liverespons er designet til at forbedre undersøgelser ved at give dig mulighed for at indsamle analysere data, køre scripts, sende mistænkelige enheder til analyse, løse trusler og proaktivt lede efter nye trusler.

Du kan finde flere oplysninger om livesvar under [Undersøg enheder på enheder, der bruger live svar](live-response.md).

## <a name="collect-investigation-package-from-devices"></a>Indsamle undersøgelsespakke fra enheder

Som en del af undersøgelsen eller svarprocessen kan du indsamle en undersøgelsespakke fra en enhed. Ved at indsamle undersøgelsespakken kan du identificere enhedens aktuelle tilstand og yderligere forstå de værktøjer og teknikker, der bruges af hackeren.

> [!IMPORTANT]
>
>Disse handlinger understøttes i øjeblikket ikke til macOS og Linux. Brug live-svar til at køre handlingen. Du kan finde flere oplysninger om livesvar under [Undersøg enheder på enheder, der bruger live svar](live-response.md)

Sådan downloader du pakken (zip-filen) og undersøger de hændelser, der er opstået på en enhed

1. Vælg **Indsaml undersøgelsespakke** i rækken med svarhandlinger øverst på enhedssiden.
2. Angiv i tekstfeltet, hvorfor du vil udføre denne handling. Vælg **Bekræft**.
3. Zip-filen downloades

Alternativ måde:

1. Vælg **Handlingscenter** i sektionen Svarhandlinger på enhedens side.

   :::image type="content" source="images/action-center-package-collection.png" alt-text="Indstillingen Handlingscenter" lightbox="images/action-center-package-collection.png":::

2. I pop op-dialogboksen Handlingscenter skal du vælge **Pakkesamlingspakke, der kan** hentes zip-filen.

   :::image type="content" source="images/collect-package.png" alt-text="Indstillingen Download pakke" lightbox="images/collect-package.png":::

Pakken indeholder følgende mapper:

<br>

****

|Mappe|Beskrivelse|
|---|---|
|Autoruns|Indeholder et sæt filer, der hver især repræsenterer indholdet af registreringsdatabasen for et kendt automatisk start indgangspunkt (ASEP) for at hjælpe med at identificere hackerens vedvarendehed på enheden. <p> <div class="alert"><b>BEMÆRK!</b> Hvis registreringsdatabasenøglen ikke findes, indeholder filen følgende meddelelse: "FEJL: Systemet kunne ikke finde den angivne registreringsdatabasenøgle eller værdi".<div>|
|Installerede programmer|Denne .CSV indeholder listen over installerede programmer, som kan hjælpe med at identificere, hvad der aktuelt er installeret på enheden. Du kan finde flere oplysninger [Win32_Product klasse](https://go.microsoft.com/fwlink/?linkid=841509).|
|Netværksforbindelser|Denne mappe indeholder et sæt datapunkter, som er relateret til forbindelsesoplysninger, som kan hjælpe med at identificere forbindelsen til mistænkelige URL-adresser, hackeres kommando og kontrol (C&C)-infrastruktur, lateral bevægelse eller fjernforbindelser. <ul><li>ActiveNetConnections.txt: Viser protokolstatistik og aktuelle TCP/IP-netværksforbindelser. Giver mulighed for at søge efter mistænkelige forbindelser, der er foretaget af en proces.</li><li>Arp.txt: Viser de aktuelle ARP-cachetabeller for alle grænseflader. ARP-cachen kan vise andre værter på et netværk, der er blevet kompromitteret eller mistænkelige systemer på netværket, som måske er blevet brugt til at køre et internt angreb.</il><li>DnsCache.txt: Viser indholdet af cachen til DNS-klient resolver, som omfatter både poster, der er forudinstalleret fra den lokale Hosts-fil, og de nyligt opnås ressourceposter for navneforespørgsler, som løses af computeren. Dette kan hjælpe med at identificere mistænkelige forbindelser.</li><li>IpConfig.txt: Viser den fulde TCP/IP-konfiguration for alle adaptere. Adaptere kan repræsentere fysiske grænseflader, f.eks. installerede netværksadaptere eller logiske grænseflader, f.eks. opkaldsforbindelser.</li><li>FirewallExecutionLog.txt og pfirewall.log</li></ul><p><div class="alert"><b>BEMÆRK!</b> Filen pfirewall.log skal findes i %windir%\system32\logfiles\firewall\pfirewall.log, så den medtages i undersøgelsespakken. Du kan finde flere oplysninger om at oprette [firewall-logfilen under Konfigurere Windows Defender Firewall med Avanceret sikkerhedslog](/windows/security/threat-protection/windows-firewall/configure-the-windows-firewall-log)<div>|
|Forudindstillede filer|Windows Prefetch-filer er udviklet til at gøre startprocessen af programmet hurtigere. Det kan bruges til at spore alle de filer, der senest er brugt i systemet, og finde sporinger for programmer, der muligvis er blevet slettet, men stadig kan findes på listen over filer, der er forudindstillet. <ul><li>Prefetch folder: Contains a copy of the prefetch files from `%SystemRoot%\Prefetch`. BEMÆRK! Det anbefales at downloade en forudindstillet filvisning for at få vist de forudindstillede filer.</li><li>PrefetchFilesList.txt: Indeholder listen over alle de kopierede filer, der kan bruges til at spore, hvis der var nogen kopifejl til mappen prefetch.</li></ul>|
|Processer|Indeholder en .CSV fil, der viser de kørende processer og giver mulighed for at identificere aktuelle processer, der kører på enheden. Dette kan være nyttigt, når du identificerer en mistænkelig proces og dens tilstand.|
|Planlagte opgaver|Indeholder en .CSV fil, der viser de planlagte opgaver, som kan bruges til at identificere rutiner, der udføres automatisk på en valgt enhed, til at søge efter mistænkelig kode, der blev indstillet til at køre automatisk.|
|Sikkerhedshændelseslog|Indeholder sikkerhedshændelsesloggen, som indeholder poster for logon- eller logoutaktivitet eller andre sikkerhedsrelaterede hændelser, der er angivet af systemets overvågningspolitik. <p><div class="alert"><b>BEMÆRK!</b> Åbn hændelseslogfilen med Logbog.</div>|
|Tjenester|Indeholder en .CSV fil, der viser tjenester og deres tilstande.|
|Windows (SMB)-sessioner (Message Block) på server|Viser delt adgang til filer, printere og serielle porte og diverse kommunikation mellem noder på et netværk. Dette kan hjælpe med at identificere dataudfyldning eller lateral bevægelse. <p> Indeholder filer til SMBInboundSessions og SMBOutboundSession. <p> <div class="alert"><b>BEMÆRK!</b> Hvis der ikke er nogen sessioner (indgående eller udgående), får du en tekstfil, der fortæller dig, at der ikke blev fundet nogen SMB-sessioner.</div>|
|Systemoplysninger|Indeholder en SystemInformation.txt fil, der viser systemoplysninger som os-version og netværkskort.|
|Temp Directories|Indeholder et sæt tekstfiler, der viser de filer, der er placeret i %Temp% for hver bruger i systemet. <p> Dette kan hjælpe med at spore mistænkelige filer, som en hacker kan være gået tabt i systemet. <p> <div class="alert"><b>BEMÆRK!</b> Hvis filen indeholder følgende meddelelse: "Systemet kan ikke finde den angivne sti", betyder det, at der ikke er nogen midlertidig mappe for denne bruger, og det kan skyldes, at brugeren ikke loggede på systemet.</div>|
|Brugere og grupper|Indeholder en liste over filer, der hver især repræsenterer en gruppe og dens medlemmer.|
|WdSupportLogs|Indeholder MpCmdRunLog.txt og MPSupportFiles.cab  <p> <div class="alert"><b>BEMÆRK!</b> Denne mappe oprettes kun den Windows 10, version 1709 eller senere med opdateringsopdateringsopdateringen for februar 2020 eller nyere installeret: <ul><li>Win10 1709 (RS3) Build 16299.1717: [KB4537816](https://support.microsoft.com/help/4537816/windows-10-update-kb4537816)</li><li>Win10 1803 (RS4) Build 17134.1345: [KB4537795](https://support.microsoft.com/help/4537795/windows-10-update-kb4537795)</li><li>Win10 1809 (RS5) Build 17763.1075: [KB4537818](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818)</li><li>Win10 1903/1909 (19h1/19h2) Builds 18362.693 og 18363.693: [KB4535996](https://support.microsoft.com/help/4535996/windows-10-update-kb4535996)</li></ul> </div>|
|CollectionSummaryReport.xls|Denne fil er en oversigt over samlingen af undersøgelsespakker, den indeholder listen over datapunkter, den kommando, der bruges til at udtrække dataene, udførelsesstatus og fejlkoden, hvis der opstår fejl. Du kan bruge denne rapport til at spore, om pakken indeholder alle de forventede data og identificere, hvis der var nogen fejl.|
|

## <a name="run-microsoft-defender-antivirus-scan-on-devices"></a>Kør Microsoft Defender Antivirus scanning på enheder

Som en del af undersøgelsen eller svarprocessen kan du starte en antivirusscanning eksternt for at identificere og afhjælpe malware, der kan være på en kompromitteret enhed.

>[!IMPORTANT]
>- Denne handling understøttes i øjeblikket ikke til macOS og Linux. Brug live-svar til at køre handlingen. Du kan finde flere oplysninger om livesvar under [Undersøg enheder på enheder, der bruger live svar](live-response.md)
>- En Microsoft Defender Antivirus (Microsoft Defender AV) kan køre sammen med andre antivirusløsninger, uanset om Microsoft Defender AV er den aktive antivirusløsning eller ej. Microsoft Defender AV kan være i passiv tilstand. Du kan finde flere oplysninger [Microsoft Defender Antivirus kompatibilitet.](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-compatibility)

Når du har valgt **Kør antivirus-scanning**, skal du vælge den scanningstype, du vil køre (hurtig eller fuld) og tilføje en kommentar, før du bekræfter scanningen.

:::image type="content" source="images/run-antivirus.png" alt-text="Meddelelsen om at vælge hurtig scanning eller fuld scanning og tilføje kommentar" lightbox="images/run-antivirus.png":::

Handlingscenter viser scanningsoplysningerne, og tidslinjen for enheden indeholder en ny hændelse, hvilket afspejler, at en scanningshandling blev sendt på enheden. Microsoft Defender AV-beskeder afspejler eventuelle registreringer, der vises under scanningen.

> [!NOTE]
> Når du udløser en scanning ved hjælp af Defender for endpoint-svarhandling, gælder Microsoft Defender-antivirusværdien 'ScanAvgCPULoadFactor' stadig og begrænser CPU-effekten af scanningen.
>
> Hvis ScanAvgCPULoadFactor ikke er konfigureret, er standardværdien en grænse på 50 % maksimal CPU-belastning under en scanning.
>
> Få mere at vide under [configure-advanced-scan-types-microsoft-defender-antivirus](/windows/security/threat-protection/microsoft-defender-antivirus/configure-advanced-scan-types-microsoft-defender-antivirus).

## <a name="restrict-app-execution"></a>Begræns appudførelse

Ud over at indeholde et angreb ved at stoppe ondsindede processer kan du også låse en enhed og forhindre efterfølgende forsøg på potentielt skadelige programmer i at køre.

>[!IMPORTANT]
> - Denne handling er tilgængelig for enheder på Windows 10, version 1709 eller nyere, Windows 11 og Windows Server 2016. 
> - Denne funktion er tilgængelig, hvis din organisation bruger Microsoft Defender Antivirus.
> - Denne handling skal opfylde politikformaterne Windows Defender af kodeintegritet i programkontrolprogrammet og krav til signering. Du kan finde flere oplysninger under Formater [for politik for kodeintegritet og signering](/windows/security/threat-protection/windows-defender-application-control/use-code-signing-to-simplify-application-control-for-classic-windows-applications)).

Hvis du vil begrænse et program i at køre, anvendes en politik for kodeintegritet, der kun tillader, at filer kører, hvis de er signeret af et certifikat, der er udstedt af Microsoft. Denne metode til begrænsning kan hjælpe med at forhindre en hacker i at styre kompromitterede enheder og udføre yderligere ondsindede aktiviteter.

> [!NOTE]
> Du kan når som helst fortryde begrænsningen af programmer, så de ikke kører. Knappen på siden enhed ændres, så der siges **Fjern appbegrænsninger**, og derefter skal du udføre de samme trin som at begrænse udførelse af apps.

Når du har valgt **Begræns udførelse af apps** på enhedens side, skal du skrive en kommentar og vælge **Bekræft**. Handlingscenter viser scanningsoplysningerne, og enhedens tidslinje indeholder en ny begivenhed.

:::image type="content" source="images/restrict-app-execution.png" alt-text="Meddelelse om programbegrænsning" lightbox="images/restrict-app-execution.png":::

### <a name="notification-on-device-user"></a>Meddelelse på enhedsbruger

Når en app er begrænset, vises følgende meddelelse for at informere brugeren om, at en app begrænses i at køre:

:::image type="content" source="images/atp-app-restriction.png" alt-text="Meddelelsen om programbegrænsning" lightbox="images/atp-app-restriction.png":::

>[!NOTE]
>Meddelelsen er ikke tilgængelig på Windows Server 2016 og Windows Server 2012 R2.

## <a name="isolate-devices-from-the-network"></a>Isoler enheder fra netværket

Afhængigt af alvoren af angrebene og enhedens følsomhed kan det være en ide at isolere enheden fra netværket. Denne handling kan hjælpe med at forhindre hackeren i at styre den kompromitterede enhed og udføre yderligere aktiviteter som f.eks. dataudfyld og lateral bevægelse.

>[!IMPORTANT]
>- Denne handling understøttes i øjeblikket ikke til macOS og Linux. Brug live-svar til at køre handlingen. Du kan finde flere oplysninger om livesvar under [Undersøg enheder på enheder, der bruger live svar](live-response.md)
>- Fuld isolation er tilgængelig for enheder på Windows 10, version 1703, Windows 11, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 og Windows Server 2022.
>- Selektiv isolation er tilgængelig for enheder på Windows 10, version 1709 eller nyere, og Windows 11.
>- Når du isolerer en enhed, er det kun visse processer og destinationer, der er tilladt. Derfor kan enheder, der er bag en fuld VPN-vpn-android,, ikke oprette forbindelse til Microsoft Defender for Endpoint-skytjenesten, når enheden er isoleret. Vi anbefaler, at du bruger et opdelt VPN til Microsoft Defender for Endpoint og Microsoft Defender Antivirus skybaseret beskyttelsesrelateret trafik.

Denne enhedsisolationsfunktion afbryder forbindelsen til den kompromitterede enhed fra netværket, mens du bevarer forbindelsen til Defender for Endpoint-tjenesten, som fortsætter med at overvåge enheden.

På Windows 10 version 1709 eller nyere har du mere kontrol over netværkisolationsniveauet. Du kan også vælge at Outlook forbindelse Microsoft Teams netværksforbindelse (også Skype for Business selektiv isolation).

> [!NOTE]
> Du kan når som helst genoprette forbindelsen mellem enheden og netværket igen. Knappen på enhedssiden ændres, så der står **Frigiv fra isolation**, og derefter skal du gøre det samme som at isolere enheden.

Når du har valgt **Isoler enhed** på enhedssiden, skal du skrive en kommentar og vælge **Bekræft**. Handlingscenter viser scanningsoplysningerne, og enhedens tidslinje indeholder en ny begivenhed.

:::image type="content" source="images/isolate-device.png" alt-text="Detaljeside for en isoleret enhed" lightbox="images/isolate-device.png":::

> [!NOTE]
> Enheden forbliver tilsluttet Defender for Endpoint-tjenesten, også selvom den er isoleret fra netværket. Hvis du har valgt at Outlook adgang Skype for Business kommunikation, vil du kunne kommunikere til brugeren, mens enheden er isoleret.

### <a name="notification-on-device-user"></a>Meddelelse på enhedsbruger

Når en enhed isoleres, vises følgende meddelelse for at informere brugeren om, at enheden isoleres fra netværket:

:::image type="content" source="images/atp-notification-isolate.png" alt-text="Meddelelse om ingen netværksforbindelse" lightbox="images/atp-notification-isolate.png":::

## <a name="consult-a-threat-expert"></a>Kontakt en trusselsekspert

Du kan kontakte en Microsoft-trusselsekspert for at få mere at vide om en potentielt kompromitteret enhed eller allerede kompromitterede enheder. Microsoft-trusselseksperter kan engageres direkte fra den Microsoft 365 Defender for at få et rettidigt og nøjagtigt svar. Eksperter giver indsigt, ikke kun med hensyn til en potentielt kompromitteret enhed, men også med hensyn til bedre at forstå komplekse trusler, målrettede angrebsmeddelelser, du får, eller hvis du har brug for flere oplysninger om beskederne eller en kontekst med trusselsintelligens, som du kan se på dit portaldashboard.

Se [Kontakt en Microsoft Threat Expert for at](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) få flere oplysninger.

## <a name="check-activity-details-in-action-center"></a>Kontrollér detaljer om aktivitet i Handlingscenter

**Handlingscenter indeholder** oplysninger om handlinger, der er foretaget på en enhed eller fil. Du vil kunne se følgende detaljer:

- Undersøgelse af pakkesamling
- Antivirusscanning
- Appbegrænsning
- Enhedsisolation

Alle andre relaterede oplysninger vises også, f.eks. dato/klokkeslæt for indsendelse, afsendelse af bruger, og om handlingen lykkedes eller mislykkedes.

:::image type="content" source="images/action-center-details.png" alt-text="Handlingscenter med oplysninger" lightbox="images/action-center-details.png":::


## <a name="see-also"></a>Se også

- [Udføre svarhandlinger på en fil](respond-file-alerts.md)
- [Manuelle svarhandlinger i Microsoft Defender for Endpoint Plan 1](defender-endpoint-plan-1.md#manual-response-actions)
- [Rapportér unøjagtighed](/microsoft-365/security/defender-endpoint/tvm-security-recommendation#report-inaccuracy)
