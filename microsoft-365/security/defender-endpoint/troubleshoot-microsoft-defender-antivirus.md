---
title: Microsoft Defender Antivirus hændelses-og fejlkoder
description: Slå årsager og løsninger til Microsoft Defender Antivirus-hændelses-og -fejl op
keywords: hændelse, fejlkode, siem, logføring, fejlfinding, wef, windows event forwarding
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/27/2022
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: db4401e1215ab50e47425dee15a1337466e1e98a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63597893"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Gennemse hændelseslogfiler og fejlkoder for at foretage fejlfinding af problemer med Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis du støder på et problem med Microsoft Defender Antivirus, kan du søge i tabellerne i dette emne for at finde et matchende problem og en potentiel løsning.

Tabellisten:

- [Microsoft Defender Antivirus hændelses-Windows 10](#windows-defender-av-ids) for Windows 11 og Windows Server 2016)
- [Microsoft Defender Antivirus klientfejlkoder](#error-codes)
- [Interne Microsoft Defender Antivirus klientfejlkoder (bruges af Microsoft under udvikling og test)](#internal-error-codes)

> [!TIP]
> Du kan også besøge webstedet for demoen Microsoft Defender for Endpoint [demo.wd.microsoft.com for](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) at bekræfte, at følgende funktioner virker:
>
> - Cloud-leveret beskyttelse
> - Hurtig læring (herunder Blok ved første synsviden)
> - Potentielt uønsket programblokering

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>Microsoft Defender Antivirus begivenheds-i-erne

Microsoft Defender Antivirus hændelses-Windows i Windows.

Du kan få vist hændelsesloggen direkte, eller hvis du har et sikkerhedsinformationsværktøj fra tredjepart og et værktøj til begivenhedsstyring (SIEM), kan du også bruge [Microsoft Defender Antivirus-klienthændelses-it'er](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) til at gennemse bestemte hændelser og fejl fra dine slutpunkter.

Tabellen i dette afsnit viser hovedhændelses-Microsoft Defender Antivirus og giver, hvor det er muligt, forslag til løsninger til løsning eller løsning af fejlen.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Sådan får du vist Microsoft Defender Antivirus begivenhed

1. Åbn **Log over begivenheder**.
2. I konsoltræet skal du **udvide Program- og tjenestelogfiler**, derefter **Microsoft** **og Windows** og **derefter Windows Defender**.
3. Dobbeltklik på **Drift**.
4. I detaljeruden kan du se listen over individuelle begivenheder for at finde din begivenhed.
5. Klik på begivenheden for at få vist specifikke detaljer om en begivenhed i den nederste rude under **fanerne Generelt** **og** Detaljer.

<table>
<tr>
<th colspan="2" >Hændelses-id: 1000</th>
</tr>
<tr>
<td>
Symbolic name:
</td>
<td>
<b>MALWAREPROTECTION_SCAN_STARTED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>En antimalwarescanning er startet. </b>
</td>
</tr>
<tr>
<td >
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummeret på den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scanningsparametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Scanningsressourcer: &lt; Ressourcer (f.eks. filer/kataloger/BHO), der er scannet.&gt;</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1001</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_COMPLETED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>En antimalwarescanning er afsluttet.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummeret på den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scanningsparametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt; Domainlt&gt;\&; UserScan&gt;</dt> 
<dt>Time: &lt;Varigheden af en scanning.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1002</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_CANCELLED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>En antimalwarescanning blev stoppet, før den blev færdig. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummeret på den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scanningsparametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt; Domainlt&gt;&amp;; UserScan&gt;</dt> 
<dt>Time: &lt;Varigheden af en scanning.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1003</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_PAUSED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>En antimalwarescanning blev afbrudt midlertidigt. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummeret på den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scanningsparametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt;Domainlt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1004</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_RESUMED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>En antimalware-scanning blev genoptaget. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummeret på den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scanningsparametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt;Domainlt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1005</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>En antimalwarescanning mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummeret på den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scanningsparametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt; Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Antivirusklienten stødte på en fejl, og den aktuelle scanning er stoppet. Scanningen kan mislykkes på grund af et problem på klientsiden. Denne hændelsespost indeholder scannings-id'et, scanningstypen (Microsoft Defender Antivirus, antispyware, antimalware), scanningsparametre, den bruger, der startede scanningen, fejlkoden og en beskrivelse af fejlen.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li>Kør scanningen igen.</li>
<li>Hvis det mislykkes på samme måde, skal du gå til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft Support-webstedet</a> og skrive fejlnummeret i <b></b> feltet Søg for at søge efter fejlkoden.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsofts tekniske support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1006</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_DETECTED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet fandt malware eller anden potentielt uønsket software. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Detection origin&gt;, for example:<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: Registreringstype&lt;&gt;, f.eks.:<ul>
<li>Heuristics</li>
<li>Standard</li>
<li>Cement</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde f.eks&gt; .:<ul>
<li>Bruger: Brugeren er startet</li>
<li>System: Startet system</li>
<li>Realtid: Komponent i realtid startet</li>
<li>IOAV: IE-downloads og Outlook vedhæftede filer startet</li>
<li>NIS: Netværksinspektionssystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige kontrolelementer på websider</li>
<li>Antimalware (ELAM) i tidlig start. Dette omfatter malware, der registreres ved startsekvensen</li>
<li>Fjernafslutning</li>
</ul>Antimalware Scan Interface (AMSI). Primært brugt til at beskytte scripts (PowerShell, VBS), men det kan også aktiveres af tredjeparter.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1007</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen udførte en handling for at beskytte dit system mod malware eller anden potentielt uønsket software. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har taget skridt til at beskytte denne computer mod malware eller anden potentielt uønsket software. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Bruger: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt>
<dt> Handling: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev ryddet</li>
<li>Karantæne: Ressourcen blev sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at udføre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er en fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Bloker: Ressourcen blev blokeret fra at udføre</li>
</ul>
</dt>
<dt>Status: &lt; StatusSignature-version&gt;</dt>
<dt>: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1008</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen forsøgte at udføre en handling for at beskytte dit system mod malware eller anden potentielt uønsket software, men handlingen mislykkedes.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus opstår en fejl, når du oplever malware eller anden potentielt uønsket software. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Bruger: &lt; Domainlt&gt;\&; UserName&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiHandling&gt;</dt>
<dt>: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev ryddet</li>
<li>Karantæne: Ressourcen blev sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at udføre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er en fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Bloker: Ressourcen blev blokeret fra at udføre</li>
</ul>
</dt>
<dt>Fejlkode: &lt; Fejlkode Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Beskrivelse&gt; af fejlen. </dt> 
<dt>Status: &lt; StatusSignature-version&gt;</dt>
<dt>: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1009</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen har gendannet et element fra karantæne. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har gendannet et element fra karantæne. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature-version&gt;</dt>
<dt>: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1010</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen kunne ikke gendanne et element fra karantæne. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus er opstået en fejl, der forsøger at gendanne et element fra karantæne. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Beskrivelse&gt; af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1011</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen har slettet et element fra karantæne. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har slettet et element fra karantæne.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature-version&gt;</dt>
<dt>: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1012</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen kan ikke slette et element fra karantæne.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus er opstået en fejl ved sletning af et element fra karantæne.
Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Beskrivelse&gt; af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1013</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen har slettet malwarehistorikken og anden potentielt uønsket software.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fjernet historikken for malware og anden potentielt uønsket software.
<dl>
<dt>Klokkeslæt: Det tidspunkt, hvor hændelsen indtraf, f.eks. når historikken bliver fjernet. Denne parameter bruges ikke i trusselshændelser, så der ikke er nogen forvirring om, hvorvidt det er afhjælpningstid eller instrueringstid. For dem kalder vi dem specifikt for Handlings- eller Registreringstid.</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1014</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
Antimalwareplatformen kan ikke slette historikken for malware og anden potentielt uønsket software.
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus opstår en fejl ved fjernelse af historikken for malware og anden potentielt uønsket software.
<dl>
<dt>Klokkeslæt: Det tidspunkt, hvor hændelsen indtraf, f.eks. når historikken bliver fjernet. Denne parameter bruges ikke i trusselshændelser, så der ikke er nogen forvirring om, hvorvidt det er afhjælpningstid eller instrueringstid. For dem kalder vi dem specifikt for Handlings- eller Registreringstid.</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Beskrivelse&gt; af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1015</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_BEHAVIOR_DETECTED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen registrerede mistænkelig adfærd.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har registreret en mistænkelig funktionsmåde.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Detection origin&gt;, for example:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: Registreringstype&lt;&gt;, f.eks.:<ul>
<li>Heuristics</li>
<li>Standard</li>
<li>Cement</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde f.eks&gt; .:<ul>
<li>Bruger: Brugeren er startet</li>
<li>System: Startet system</li>
<li>Realtid: Komponent i realtid startet</li>
<li>IOAV: IE-downloads og Outlook vedhæftede filer startet</li>
<li>NIS: Netværksinspektionssystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige kontrolelementer på websider</li>
<li>Antimalware (ELAM) i tidlig start. Dette omfatter malware, der registreres ved startsekvensen</li>
<li>Fjernafslutning</li>
</ul>Antimalware Scan Interface (AMSI). Primært brugt til at beskytte scripts (PowerShell, VBS), men det kan også aktiveres af tredjeparter.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process i PIDSignature&gt;</dt> 
<dt>ID: Enumeration matching severity.</dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>version: &lt;antimalwareprogram versionFidelity&gt;</dt> 
<dt>Label:</dt>
<dt>Target File Name: &lt;Filnavnet&gt; på filen.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1116</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_DETECTED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen registrerede malware eller anden potentielt uønsket software. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har registreret malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Detection origin&gt;, for example:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: Registreringstype&lt;&gt;, f.eks.:<ul>
<li>Heuristics</li>
<li>Standard</li>
<li>Cement</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde f.eks&gt; .:<ul>
<li>Bruger: Brugeren er startet</li>
<li>System: Startet system</li>
<li>Realtid: Komponent i realtid startet</li>
<li>IOAV: IE-downloads og Outlook vedhæftede filer startet</li>
<li>NIS: Netværksinspektionssystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige kontrolelementer på websider</li>
<li>Antimalware (ELAM) i tidlig start. Dette omfatter malware, der registreres ved startsekvensen</li>
<li>Fjernafslutning</li>
</ul>Antimalware Scan Interface (AMSI). Primært brugt til at beskytte scripts (PowerShell, VBS), men det kan også aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Der kræves ingen handling. Microsoft Defender Antivirus kan suspendere og handle rutinemæssigt på denne trussel. Hvis du vil fjerne truslen manuelt, skal du klikke på Microsoft Defender Antivirus på <b>Ryd computer i grænsefladen</b>.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1117</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen udførte en handling for at beskytte dit system mod malware eller anden potentielt uønsket software. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har taget skridt til at beskytte denne computer mod malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Detection origin&gt;, for example:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: Registreringstype&lt;&gt;, f.eks.:<ul>
<li>Heuristics</li>
<li>Standard</li>
<li>Cement</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde f.eks&gt; .:<ul>
<li>Bruger: Brugeren er startet</li>
<li>System: Startet system</li>
<li>Realtid: Komponent i realtid startet</li>
<li>IOAV: IE-downloads og Outlook vedhæftede filer startet</li>
<li>NIS: Netværksinspektionssystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige kontrolelementer på websider</li>
<li>Antimalware (ELAM) i tidlig start. Dette omfatter malware, der registreres ved startsekvensen</li>
<li>Fjernafslutning</li>
</ul>Antimalware Scan Interface (AMSI). Primært brugt til at beskytte scripts (PowerShell, VBS), men det kan også aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, for example:<ul>
<li>Rens: Ressourcen blev ryddet</li>
<li>Karantæne: Ressourcen blev sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at udføre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er en fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Bloker: Ressourcen blev blokeret fra at udføre</li>
</ul>
</dt>
<dt>Handlingsstatus: &lt; Beskrivelse af yderligere handlingerFejlkode&gt;</dt>
<dt>: Fejlkode &lt;Resultatkode&gt; knyttet til trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>version: &lt;antimalwareprogram version&gt;</dt> BEMÆRK: Hver gang Microsoft Defender Antivirus, Microsoft Security Essentials, Værktøj til fjernelse af skadelig software eller System Center Endpoint Protection registrerer malware, gendanner programmet følgende systemindstillinger og tjenester, som malwaren muligvis har ændret sig:<ul>
<li>Standardindstilling for Internet Explorer Microsoft Edge Internet Explorer</li>
<li>Indstillinger for Kontrol af brugeradgang</li>
<li>Indstillinger for Chrome</li>
<li>Startkontroldata</li>
<li>Registreringsdatabaseindstillinger for Regedit og Jobliste</li>
<li>Windows, Background Intelligent Transfer Service og Remote Procedure Call Service</li>
<li>Windows-operativsystemfiler</li></ul>
Ovenstående kontekst gælder for følgende klient- og serverversioner:
<table>
<tr>
<th>Operativsystem</th>
<th>Version af operativsystem</th>
</tr>
<tr>
<td>
Klientoperativsystemer
</td>
<td>
Windows Vista (Service Pack 1 eller Service Pack 2), Windows 7 og nyere
</td>
</tr>
<tr>
<td>
Serveroperativsystemer
</td>
<td>
Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 og Windows Server 2016
</td>
</tr>
</table>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Ingen handling er nødvendig. Microsoft Defender Antivirus fjernet en trussel eller sat i karantæne.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1118</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen forsøgte at udføre en handling for at beskytte dit system mod malware eller anden potentielt uønsket software, men handlingen mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus er opstået en ikke-kritisk fejl, når du oplever malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Detection origin&gt;, for example:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: Registreringstype&lt;&gt;, f.eks.:<ul>
<li>Heuristics</li>
<li>Standard</li>
<li>Cement</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde f.eks&gt; .:<ul>
<li>Bruger: Brugeren er startet</li>
<li>System: Startet system</li>
<li>Realtid: Komponent i realtid startet</li>
<li>IOAV: IE-downloads og Outlook vedhæftede filer startet</li>
<li>NIS: Netværksinspektionssystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige kontrolelementer på websider</li>
<li>Antimalware (ELAM) i tidlig start. Dette omfatter malware, der registreres ved startsekvensen</li>
<li>Fjernafslutning</li>
</ul>Antimalware Scan Interface (AMSI). Primært brugt til at beskytte scripts (PowerShell, VBS), men det kan også aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, for example:<ul>
<li>Rens: Ressourcen blev ryddet</li>
<li>Karantæne: Ressourcen blev sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at udføre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er en fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Bloker: Ressourcen blev blokeret fra at udføre</li>
</ul>
</dt>
<dt>Handlingsstatus: &lt; Beskrivelse af yderligere handlingerFejlkode&gt;</dt>
<dt>: Fejlkode &lt;Resultatkode&gt; knyttet til trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Ingen handling er nødvendig. Microsoft Defender Antivirus ikke fuldføre en opgave relateret til afhjælpning af malware. Dette er ikke en kritisk fejl.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1119</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_CRITICALLY_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen stødte på en kritisk fejl, når du forsøgte at handle på malware eller anden potentielt uønsket software. Der er flere oplysninger i begivenhedsmeddelelsen.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus opstået en kritisk fejl, når du oplever malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Severity&gt;, for example:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlig</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; File pathDetection&gt;</dt>
<dt> Origin: &lt;Detection origin&gt;, for example:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: Registreringstype&lt;&gt;, f.eks.:<ul>
<li>Heuristics</li>
<li>Standard</li>
<li>Cement</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde f.eks&gt; .:<ul>
<li>Bruger: Brugeren er startet</li>
<li>System: Startet system</li>
<li>Realtid: Komponent i realtid startet</li>
<li>IOAV: IE-downloads og Outlook vedhæftede filer startet</li>
<li>NIS: Netværksinspektionssystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige kontrolelementer på websider</li>
<li>Antimalware (ELAM) i tidlig start. Dette omfatter malware, der registreres ved startsekvensen</li>
<li>Fjernafslutning</li>
</ul>Antimalware Scan Interface (AMSI). Primært brugt til at beskytte scripts (PowerShell, VBS), men det kan også aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Name: &lt;Process in the PIDAction&gt;</dt>
<dt>: &lt;Action&gt;, for example:<ul>
<li>Rens: Ressourcen blev ryddet</li>
<li>Karantæne: Ressourcen blev sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at udføre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er en fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Bloker: Ressourcen blev blokeret fra at udføre</li>
</ul>
</dt>
<dt>Handlingsstatus: &lt; Beskrivelse af yderligere handlingerFejlkode&gt;</dt>
<dt>: Fejlkode &lt;Resultatkode&gt; knyttet til trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Klienten Microsoft Defender Antivirus denne fejl på grund af vigtige problemer. Slutpunktet er muligvis ikke beskyttet. Gennemse fejlbeskrivelsen, og følg derefter de relevante <b>brugerhandlingstrin</b> nedenfor.
<table>
<tr>
<th>Handling</th>
<th>Brugerhandling</th>
</tr>
<tr>
<td>
<b>Fjern</b>
</td>
<td>
Opdater definitionerne, og bekræft derefter, at fjernelsen blev gennemført.
</td>
</tr>
<tr>
<td>
<b>Rens</b>
</td>
<td>
Opdater definitionerne, og bekræft derefter, at afhjælpningen blev gennemført.
</td>
</tr>
<tr>
<td>
<b>Karantæne</b>
</td>
<td>
Opdater definitionerne, og bekræft, at brugeren har tilladelse til at få adgang til de nødvendige ressourcer.
</td>
</tr>
<tr>
<td>
<b>Tillad</b>
</td>
<td>
Kontrollér, at brugeren har tilladelse til at få adgang til de nødvendige ressourcer.
</td>
</tr>
</table>

Hvis hændelsen fortsætter:<ol>
<li>Kør scanningen igen.</li>
<li>Hvis det mislykkes på samme måde, skal du gå til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft Support-webstedet</a> og skrive fejlnummeret i <b></b> feltet Søg for at søge efter fejlkoden.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsofts tekniske support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1120</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_THREAT_HASH</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Microsoft Defender Antivirus har fortrudt hash'erne for en trusselsressource.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus klient er i gang i en sund tilstand.
<dl>
<dt>Aktuel platformversion: &lt; Aktuel platformversionThreat-ressourcesti&gt;</dt>
<dt>: &lt;PathHashes&gt;</dt>
<dt>: &lt;Hashes&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Bemærk! Denne hændelse logføres kun, hvis følgende politik er angivet: <b>ThreatFileHashLogging unsigned</b>.</div>
<div> </div>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1127</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_FOLDER_GUARD_SECTOR_BLOCK</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Kontrolleret mappeadgang (CFA) har blokeret for, at der ikke kunne foretages ændringer i hukommelsen i en proces, der ikke er tillid til. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Kontrolleret mappeadgang har blokeret for en upålidelig proces fra potentielt at ændre diskhåndtering.
<br/> Du kan finde flere oplysninger om hændelsesposten i følgende:
<dl>
<dt>Hændelses-id: &lt; EventID&gt;, for eksempel: 1127Version</dt>
<dt>: &lt;Version&gt;,</dt> f.eks.: 
<dt>0Niveau: &lt;&gt;Niveau, for eksempel: Win:WarningTimeCreated</dt>
<dt>: &lt;SystemTime&gt;,</dt> tidspunktet, hvor hændelsen blev 
<dt>oprettetEventRecordID: EventRecordID&gt;, indeksnummer for hændelsen i hændelsesloggenExecution ProcessID: EksekveringsprocesID, proces, der genererede begivenhedenChannel: &lt;</dt>
<dt>Hændelseskanal, f.eks.: Microsoft-&gt;&lt;</dt>
<dt>&lt;&gt; Windows-Windows Defender/</dt>
<dt>OperationalComputer: &lt;Computer nameSecurity&gt;</dt> 
<dt>UserID: &lt;Security UserIDProduct&gt;</dt> 
<dt>Name: &lt;Product Name&gt;, for example: Microsoft Defender Antivirus</dt> 
<dt>Product Version: &lt;Product VersionDetection&gt;</dt> 
<dt>Time: &lt;Registreringstid&gt;, tidspunkt, hvor CFA blokerede en upålidelig</dt> 
<dt>procesBruger: &lt;Domainlt&gt;\&; UserPath&gt;</dt>
<dt>: &lt;&gt;</dt> Enhedsnavn, navnet på den enhed eller disk, som en proces, der ikke er tillid til, blev åbnet for 
<dt>ændringProcesnavn: &lt;&gt;</dt> Processti, navnet på processtien, som CFA blokerede fra at få adgang til enheden eller disken til 
<dt>ændringsikkerheds intelligenceversion: &lt;Security intelligence-versionEngine-version&gt;</dt>
<dt>: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Brugeren kan føje den blokerede proces til listen <i>over tilladte</i> proces for CFA ved hjælp af Powershell eller Windows Sikkerhed Center.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1150</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTHY</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Hvis din antimalwareplatform rapporterer status til en overvågningsplatform, indikerer denne hændelse, at antimalwareplatformen kører og er i en sund tilstand. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus klient er i gang i en sund tilstand.
<dl>
<dt>Platformsversion: &lt; Aktuel platformversionSignatur&gt;</dt> 
<dt>version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Ingen handling er nødvendig. Klienten Microsoft Defender Antivirus i en sund tilstand. Denne hændelse rapporteres på timebasis.
</td>
</tr>

<tr>
<th colspan="2">Hændelses-id: 1151</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTH_REPORT</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Endpoint Protection klient sundhedsrapport (tid i UTC)</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Tilstandsrapport for antivirusklient.
<dl>
<dt>Platformsversion: &lt; Aktuel platform&gt;</dt> 
<dt>versionEngine Version: &lt;antimalwareprogram versionNetwork&gt;</dt> 
<dt>Realtime Inspection engine version: &lt;Network Realtime Inspection engine versionAntivirus&gt;</dt> 
<dt>signature version: &lt;Antivirus signatur versionAntispyware&gt;</dt> 
<dt>signatur version: &lt;Antispyware signature versionNetwork&gt;</dt> 
<dt>Realtime Inspection signature version: &lt; Network Realtime Inspection signature versionRTP&gt;</dt> state
<dt>: &lt;Realtime protection state&gt; (Enabled or Disabled)</dt>
<dt>OA state: &lt;On Access state&gt; (Enabled or Disabled)</dt>
<dt>IOAV state: &lt;IE Downloads and Outlook Express Attachments state&gt; (Enabled or Disabled)</dt>
<dt>BM state: &lt;Behavior Monitoring state&gt; (Enabled or Disabled)</dt>
<dt>Antivirus signature age: &lt;Antivirus signature age&gt;  (i dage)</dt> 
<dt>Antispyware-signaturalder: &lt; Antispyware-signaturalder&gt; (i dage)Seneste hurtig scanningsalder</dt>
<dt>: &lt;&gt;</dt> Seneste hurtig scanningsalder (i dage)Seneste fulde scanningsalder
<dt>: &lt;&gt;</dt> Seneste fulde scanningsalder (i dage)Klokkeslæt for oprettelse af 
<dt>antivirussignatur: ?&lt; Antivirussignatur oprettelsestid&gt;</dt> 
<dt>for oprettelse afantispyware-signatur: ?&lt; Antispyware signature creation timeLast&gt;</dt> 
<dt>quick scan start time: ?&lt; Sidste starttid for hurtig scanningSenseendetid&gt;</dt> 
<dt>for hurtig scanning: ?&lt; Sidste sluttid&gt;</dt> for hurtig scanningSens sidste hurtig scanningskilde
<dt>: &lt;&gt; Sidste hurtig scanningskilde (0 = scanning blev ikke kørt, 1 = startet af brugeren, 2 = system startet)</dt>Sidste fulde 
<dt>scanningsstarttid: ?&lt; Sidste fulde starttid for scanningSens&gt;</dt> 
<dt>fulde scanningssluttid: ?&lt; Sidste fulde scanningssluttidSeende&gt;</dt> fuld scanningskilde
<dt>: &lt;&gt; Seneste fuld scanningskilde (0 = scanning blev ikke kørt, 1 = bruger startet, 2 = system startet)</dt>
<dt>Produktstatus: Til intern fejlfinding
</dl>
</td>
</tr>

<tr>
<th colspan="2">Hændelses-id: 2000</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwaredefinitionerne blev opdateret korrekt. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Antivirussignaturversionen er blevet opdateret.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionForrige&gt;</dt> 
<dt>signaturversion: &lt;Tidligere signaturversionSignaturtype&gt;</dt>
<dt>: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Opdateringstype: &lt; Opdateringstype&gt;, enten Fuld eller Delta.</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Ingen handling er nødvendig. Klienten Microsoft Defender Antivirus i en sund tilstand. Denne hændelse rapporteres, når signaturer opdateres.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2001</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Sikkerheds intelligence-opdateringen mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl ved opdatering af signaturer.
<dl>
<dt>Ny sikkerhedsintelligens-version: &lt; Nyt versionsnummerForrige&gt;</dt> 
<dt>sikkerhedsintelligens-version: &lt;Forrige versionOpdateringskilde&gt;</dt>
<dt>: &lt;Opdateringskilde&gt;, for eksempel:
<ul>
<li>Sikkerhedsintelligens-opdateringsmappe</li>
<li>Intern sikkerhedsintelligens-opdateringsserver</li>
<li>Microsoft Update Server</li>
<li>Filshare</li>
<li>Microsoft Malware Protection Center (MMPC)</li>
</ul>
</dt>
<dt>Opdateringsfase: Opdateringsfase&lt;&gt;, f.eks.:
<ul>
<li>Søg</li>
<li>Download</li>
<li>Installér</li>
</ul>
</dt>
<dt>Kildesti: Filnavn på UNC (Universal Naming Convention), servernavn for Windows Server Update Services (WSUS)/Microsoft Update/ADL.</dt>
<dt> Signaturtype: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Opdateringstype: &lt; Opdateringstype&gt;, enten Fuld eller Delta.</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Current engine versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine versionError&gt;</dt> 
<dt>Code: &lt;Error code&gt; Result code associated with threat status. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Denne fejl opstår, når der er problemer med at opdatere definitioner.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Opdater definitioner</a> , og gennemtving en kant direkte på slutpunktet.</li>
<li>Gennemse posterne i filen %Windir%\WindowsUpdate.log for at få flere oplysninger om denne fejl.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsofts tekniske support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2002</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet blev opdateret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus programversionen er blevet opdateret.
<dl>
<dt>Aktuel engine-version: &lt; Aktuel engine-versionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Previous engine versionEngine&gt;</dt> 
<dt>Type: &lt;Engine type&gt;, enten antimalwareprogram eller Network Inspection System Engine.</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Ingen handling er nødvendig. Klienten Microsoft Defender Antivirus i en sund tilstand. Denne hændelse rapporteres, når antimalwareprogrammet opdateres.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2003</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Opdateringen af antimalwareprogrammet mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus opstår en fejl under forsøg på at opdatere programmet.
<dl>
<dt>New Engine Version:</dt>
<dt>Previous Engine Version: &lt;Previous engine versionEngine&gt;</dt> 
<dt>Type: &lt;Engine type&gt;, enten antimalwareprogram eller Network Inspection System Engine.</dt> 
<dt>Bruger: &lt; Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Klientopdateringen Microsoft Defender Antivirus mislykkedes. Denne hændelse sker, når klienten ikke kan opdatere sig selv. Denne hændelse skyldes normalt en afbrydelse af netværksforbindelsen under en opdatering.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Opdater definitioner</a> , og gennemtving en kant direkte på slutpunktet.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsofts tekniske support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2004</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_REVERSION</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Der opstod et problem under indlæsning af antimalwaredefinitioner. Antimalwareprogrammet vil forsøge at indlæse det senest kendte gode sæt definitioner.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl ved indlæsning af signaturer og vil forsøge at vende tilbage til et kendt godt sæt signaturer.
<dl>
<dt>Signaturer forsøgt:Fejlkode</dt>
<dt>: Resultatkode for &lt;fejlkode&gt;, der er knyttet til trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware engine version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Klienten Microsoft Defender Antivirus at downloade og installere filen med de nyeste definitioner og mislykkedes. Denne fejl kan opstå, når klienten støder på en fejl under forsøg på at indlæse definitionerne, eller hvis filen er beskadiget. Microsoft Defender Antivirus vil forsøge at vende tilbage til et kendt godt sæt definitioner.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li>Genstart computeren, og prøv igen.</li>
<li>Download de seneste definitioner fra <a href="https://aka.ms/wdsi">Microsoft Sikkerhedsviden websted</a>.
Bemærk! Størrelsen på den definitionsfil, der downloades fra webstedet, kan overskride 60 MB og bør ikke bruges som en langsigtet løsning til opdatering af definitioner.
</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsofts tekniske support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2005</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_PLATFORMOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet kunne ikke indlæses, fordi antimalwareplatformen er forældet. Antimalwareplatformen indlæser det senest kendte gode antimalwareprogram og forsøger at opdatere.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus ikke kan indlæse antimalwareprogrammet, fordi den aktuelle platformversion ikke understøttes. Microsoft Defender Antivirus vende tilbage til det senest kendte gode program, og du vil forsøge at opdatere platformen.
<dl>
<dt>Aktuel platformversion: Aktuel &lt;platformversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2006</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Platformsopdateringen mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus er stødt på en fejl ved forsøg på at opdatere platformen.
<dl>
<dt>Aktuel platformversion: &lt; Aktuel platformversionFejlkode&gt;</dt>
<dt>: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2007</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_ALMOSTOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Platformen vil snart være forældet. Download den nyeste platform for at bevare opdateret beskyttelse.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus snart en nyere platformsversion for at understøtte fremtidige versioner af antimalwareprogrammet. Download de nyeste Microsoft Defender Antivirus-platformen for at bevare det bedst mulige beskyttelsesniveau.
<dl>
<dt>Aktuel platformversion: Aktuel &lt;platformversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2010</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet brugte Dynamic Signature Service til at hente yderligere definitioner. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus Dynamisk <i>signaturtjeneste til at</i> hente flere signaturer for at beskytte din computer.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionSignaturtype&gt;</dt>
<dt>: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Aktuel engine-version: &lt; Aktuel engine-versionDynamic&gt;</dt>
<dt> Signature Type: &lt;Dynamisk signaturtype&gt;, f.eks.:
<ul>
<li>Version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
<li>Varighed</li>
</ul>
</dt>
<dt>Fastholdelsessti: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;VersionsnummerAnamisk&gt;</dt> signaturkompileringstidsstempel
<dt>: &lt;Tidsstempelbegrænsningstype&gt;</dt>
<dt>:&gt;&lt; Type af begrænsning for vedholdenhed, f.eks.:
<ul>
<li>VDM-version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
</ul>
</dt>
<dt>Fastholdelsesgrænse: Begrænsninger for vedholdende brug af fastpath-signaturen.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2011</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Den dynamiske signaturtjeneste slettede de forældede dynamiske definitioner. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus Dynamisk <i>signaturtjeneste til at</i> kassere forældede signaturer.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionSignaturtype&gt;</dt>
<dt>: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Aktuel engine-version: &lt; Aktuel engine-versionDynamic&gt;</dt>
<dt> Signature Type: &lt;Dynamisk signaturtype&gt;, f.eks.:
<ul>
<li>Version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
<li>Varighed</li>
</ul>
</dt>
<dt>Fastholdelsessti: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;VersionsnummerDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimetampRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Per persistens Limit Type: &lt;Per persistens limit type&gt;, for eksempel:
<ul>
<li>VDM-version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
</ul>
</dt>
<dt>Fastholdelsesgrænse: Begrænsninger for vedholdende brug af fastpath-signaturen.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Ingen handling er nødvendig. Klienten Microsoft Defender Antivirus i en sund tilstand. Denne hændelse rapporteres, når dynamisk signaturtjeneste sletter forældede dynamiske definitioner.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2012</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet stødte på en fejl, når man forsøgte at bruge Dynamic Signature Service. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl under forsøg på at bruge <i>tjenesten Dynamisk signatur</i>.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionSignaturtype&gt;</dt>
<dt>: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Aktuel engine-version: &lt; Aktuel programversionFejlkode&gt;</dt>
<dt>: Fejlkode &lt;Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
<dt> Dynamisk signaturtype: &lt;Dynamisk signaturtype&gt;, f.eks.:
<ul>
<li>Version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
<li>Varighed</li>
</ul>
</dt>
<dt>Fastholdelsessti: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;VersionsnummerAnamisk&gt;</dt> signaturkompileringstidsstempel
<dt>: &lt;Tidsstempelbegrænsningstype&gt;</dt>
<dt>:&gt;&lt; Type af begrænsning for vedholdenhed, f.eks.:
<ul>
<li>VDM-version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
</ul>
</dt>
<dt>Fastholdelsesgrænse: Begrænsninger for vedholdende brug af fastpath-signaturen.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Kontrollér indstillingerne for din internetforbindelse.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2013</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED_ALL </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Tjenesten Dynamisk signatur har slettet alle dynamiske definitioner. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus kasseret alle <i>Dynamic Signature Service-signaturer</i>.
<dl>
<dt>Aktuel signaturversion: Aktuel &lt;signaturversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2020</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOADED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet hentede en ren fil. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus hentet en ren fil.
<dl>
<dt>Filnavn: &lt; Filnavn Filnavn&gt; på filen.</dt> 
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionCurrent&gt;</dt> 
<dt>Engine-version: &lt;Aktuel programversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2021</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOAD_FAILED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet kunne ikke downloade en ren fil. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl ved download af en ren fil.
<dl>
<dt>Filnavn: &lt; Filnavn Filnavn&gt; på filen.</dt> 
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionCurrent&gt;</dt> 
<dt>Engine-version: &lt;Aktuel programversionFejlkode&gt;</dt>
<dt>: &lt;Fejlkode Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Kontrollér indstillingerne for din internetforbindelse.
Klienten Microsoft Defender Antivirus en fejl, når du bruger tjenesten Dynamisk signatur til at hente de seneste definitioner til en bestemt trussel. Denne fejl er sandsynligvis forårsaget af et problem med netværksforbindelsen.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2030</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALLED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet er downloadet og konfigureret til at køre offline ved næste genstart af systemet.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus downloadet og konfigureret offline antivirus til at køre ved næste genstart.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2031</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALL_FAILED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet kunne ikke downloade og konfigurere en offlinescanning.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl ved forsøg på at downloade og konfigurere offline antivirus.
<dl>
<dt>Fejlkode: &lt; Fejlkode Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2040</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_OS_EXPIRING </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwaresupport til denne version af operativsystemet slutter snart. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Supporten til dit operativsystem udløber om kort tid. Kørsel Microsoft Defender Antivirus et operativsystem, der ikke længere understøttes, er ikke en tilstrækkelig løsning til at beskytte dig mod trusler.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2041</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_OS_EOL </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwaresupport til dette operativsystem er ophørt. Du skal opgradere operativsystemet for fortsat at kunne understøttes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Understøttelsen af dit operativsystem er udløbet. Kørsel Microsoft Defender Antivirus et operativsystem, der ikke længere understøttes, er ikke en tilstrækkelig løsning til at beskytte dig mod trusler.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2042</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_PROTECTION_EOL </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet understøtter ikke længere dette operativsystem og beskytter ikke længere dit system mod malware. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Understøttelsen af dit operativsystem er udløbet. Microsoft Defender Antivirus understøttes ikke længere i dit operativsystem, fungerer ikke længere og beskytter ikke mod malwaretrusler.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 3002</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_FAILURE </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Beskyttelse i realtid stødte på en fejl og mislykkedes.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus Real-Time-beskyttelse har fundet en fejl og mislykkedes.
<dl>
<dt>Funktion: &lt;Funktion&gt;, f.eks.:
<ul>
<li>I Access</li>
<li>Internet Explorer-downloads og vedhæftede Microsoft Outlook Express</li>
<li>Overvågning af funktionsmåde</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Fejlkode: &lt; Fejlkode Resultatkode&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Årsag: Årsagen Microsoft Defender Antivirus beskyttelse i realtid er genstartet en funktion.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Du skal genstarte systemet og derefter køre en fuld scanning, da det er muligt, at systemet ikke var beskyttet i et stykke tid.
Den Microsoft Defender Antivirus klientens beskyttelse i realtid, stødte på en fejl, fordi en af tjenesterne ikke kunne starte.
Hvis det efterfølges af et 3007-hændelses-id, var fejlen midlertidig, og den antimalwareklient, der blev gendannet efter fejlen.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 3007</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_RECOVERED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Beskyttelse i realtid gendannes efter en fejl. Vi anbefaler, at du kører en fuld systemscanning, når du får vist denne fejl. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus Beskyttelse i realtid har genstartet en funktion. Det anbefales, at du kører en komplet systemscanning for at registrere elementer, der kan være gået glip af, mens denne agent var nede.
<dl>
<dt>Funktion: &lt;Funktion&gt;, f.eks.:
<ul>
<li>I Access</li>
<li>IE-downloads og Outlook Express-vedhæftede filer</li>
<li>Overvågning af funktionsmåde</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Årsag: Årsagen Microsoft Defender Antivirus beskyttelse i realtid er genstartet en funktion.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Beskyttelsesfunktionen i realtid er genstartet. Hvis denne hændelse sker igen, skal du <a href="https://go.microsoft.com/fwlink/?LinkId=215491">kontakte Microsofts tekniske support</a>.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5000</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_RTP_ENABLED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Beskyttelse i realtid er aktiveret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning for beskyttelse i realtid for malware, og anden potentielt uønsket software blev aktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5001</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_RTP_DISABLED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Beskyttelse i realtid er deaktiveret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning for beskyttelse i realtid for malware, og anden potentielt uønsket software blev deaktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5004</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_CONFIGURED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Konfigurationen af beskyttelse i realtid er blevet ændret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus funktionskonfigurationen i realtid er blevet ændret.
<dl>
<dt>Funktion: &lt;Funktion&gt;, f.eks.:
<ul>
<li>I Access</li>
<li>IE-downloads og Outlook Express-vedhæftede filer</li>
<li>Overvågning af funktionsmåde</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Konfiguration: </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5007</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_CONFIG_CHANGED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Konfigurationen af antimalwareplatformen er blevet ændret.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus konfigurationen er ændret. Hvis dette er en uventet hændelse, skal du gennemgå indstillingerne, da dette kan være resultatet af malware.
<dl>
<dt>Gammel værdi: &lt; Gammel værdinummer Gammel&gt; antivirus-konfigurationsværdi.</dt> 
<dt>Ny værdi: &lt; Nyt værdinummer Ny&gt; antiviruskonfigurationsværdi.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5008</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_FAILURE</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareprogrammet stødte på en fejl og mislykkedes.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus program er afsluttet på grund af en uventet fejl.
<dl>
<dt>Fejltype: &lt; Fejltype&gt;, f.eks.: Crash eller</dt> 
<dt>HangException Code: &lt;Error codeResource&gt;</dt>
<dt>: &lt;Resource&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Sådan foretager du fejlfinding af denne hændelse:<ol>
<li>Prøv at genstarte tjenesten.<ul>
<li>For antimalware, antivirus og spyware skal du ved en kommandoprompt med administrator administrator indtaste <b>net stop msmpsvc</b> og derefter skrive <b>net start msmpsvc</b> for at genstarte antimalwareprogrammet.</li>
<li>For <i>Netværksinspektionssystem</i> skal du ved en kommandoprompt med administratortype skrive <b>net start nissrv</b> og derefter skrive <b>net start nissrv</b> for at genstarte <i>netværksinspektionssystemprogrammet</i> ved hjælp af NiSSRV.exe-filen.
</li>
</ul>
</li>
<li>Hvis det mislykkes på samme måde, skal du søge efter fejlkoden ved at åbne <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft Support-webstedet</a> og skrive fejlnummeret i <b></b> feltet Søg og kontakte <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft teknisk support</a>.</li>
</ol>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Klientprogrammet Microsoft Defender Antivirus stoppet på grund af en uventet fejl.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li>Kør scanningen igen.</li>
<li>Hvis det mislykkes på samme måde, skal du gå til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft Support-webstedet</a> og skrive fejlnummeret i <b></b> feltet Søg for at søge efter fejlkoden.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsofts tekniske support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5009</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_ENABLED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Scanning for malware og anden potentielt uønsket software er aktiveret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning for malware, og anden potentielt uønsket software er blevet aktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5010</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_DISABLED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Scanning for malware og potentielt uønsket software er deaktiveret.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning for malware, og anden potentielt uønsket software deaktiveres.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5011</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_ENABLED</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Scanning for virus er aktiveret.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning for virus er blevet aktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5012</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_DISABLED </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Scanning for virus er deaktiveret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning for virus er deaktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5013</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>
</b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Beskyttelse mod manipulation har blokeret en ændring i Microsoft Defender Antivirus.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Hvis Beskyttelse af Tamper er aktiveret, vil ethvert forsøg på at ændre nogen af Defenders indstillinger, hvis det blokeres, og hændelses-id 5013 genereres, der angiver, hvilken indstillingsændring der blev blokeret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5100</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_EXPIRATION_WARNING_STATE </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen udløber snart. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har angivet en udvidet periode og udløber snart. Efter udløb deaktiverer dette program beskyttelse mod virus, spyware og anden potentielt uønsket software.
<dl>
<dt>Udløbsårsagen: Årsagen Microsoft Defender Antivirus udløber.</dt> 
<dt>Udløbsdato: Den dato Microsoft Defender Antivirus udløber.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5101</th>
</tr>
<tr><td>
Symbolic name:
</td>
<td >
<b>MALWAREPROTECTION_DISABLED_EXPIRED_STATE </b>
</td>
</tr>
<tr>
<td>
Meddelelse:
</td>
<td >
<b>Antimalwareplatformen er udløbet. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus prøveperioden er udløbet. Beskyttelse mod virus, spyware og anden potentielt uønsket software deaktiveres.
<dl>
<dt>Udløbsårsagen:</dt>
<dt>Udløbsdato: Fejlkode</dt>
<dt>: Fejlkode Resultatkode &lt;&gt; tilknyttet trusselsstatus. Standard HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Microsoft Defender Antivirus klientfejlkoder Hvis Microsoft Defender Antivirus oplever problemer, vil det normalt give dig en fejlkode, der kan hjælpe dig med at foretage fejlfinding af problemet. Oftest betyder en fejl, at der opstod et problem med at installere en opdatering.
Dette afsnit indeholder følgende oplysninger om Microsoft Defender Antivirus klientfejl.
- Fejlkoden Den - mulige årsag til fejlen Råd om - , hvad du skal gøre nu

Brug oplysningerne i disse tabeller til at foretage fejlfinding Microsoft Defender Antivirus fejlkoder.


<table>
<tr>
<th colspan="2">Fejlkode: 0x80508007</th>
</tr>
<tr>
<td>Meddelelse</td>
<td>
<b>ERR_MP_NO_MEMORY </b>
</td>
</tr>
<tr>
<td>
Mulig årsag
</td>
<td>
Denne fejl indikerer, at du måske er løbet tør for hukommelse.
</td>
</tr>
<tr>
<td>Løsning</td>
<td>
<ol>
<li>Kontrollér den tilgængelige hukommelse på din enhed.</li>
<li>Luk ubrugte programmer, der kører, for at frigøre hukommelse på enheden.</li>
<li>Genstart enheden, og kør scanningen igen.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x8050800C</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_BAD_INPUT_DATA</b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at der kan være et problem med dit sikkerhedsprodukt.
</td>
</tr><tr><td>Løsning</td><td>
<ol>
<li>Opdater definitionerne. Enten:<ol>
<li>Klik på <b>knappen Opdater</b> definitioner på <b>fanen Opdater</b> i Microsoft Defender Antivirus. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Eller
</li>
<li>Download de seneste definitioner fra <a href="https://aka.ms/wdsi">Microsoft Sikkerhedsviden websted</a>.
Bemærk! Størrelsen på den definitionsfil, der downloades fra webstedet, kan overskride 60 MB og bør ikke bruges som en langsigtet løsning til opdatering af definitioner.
</li>
</ol>
</li>
<li>Kør en fuld scanning.
</li>
<li>Genstart enheden, og prøv igen.</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508020</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_BAD_CONFIGURATION </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at der kan være en programkonfigurationsfejl; Dette er ofte relateret til inputdata, der ikke tillader, at programmet fungerer korrekt.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x805080211
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at Microsoft Defender Antivirus ikke kunne sætte en trussel i karantæne.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508022
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at der kræves en genstart for at udføre fjernelse af trusler.
</td>
</tr>
<tr>
<th colspan="2">
0x80508023
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_THREAT_NOT_FOUND </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at truslerne muligvis ikke længere findes i mediet, eller at malware forhindrer dig i at scanne din enhed.
</tr><tr><td>Løsning
</td>
<td>
Kør <a href="https://www.microsoft.com/security/scanner/default.aspx">sikkerhedssoftwaren Microsoft Sikkerhedsscanner</a> opdater derefter din sikkerhedssoftware, og prøv igen.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508024 </th></tr>
<tr>
<td>Meddelelse</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at en komplet systemscanning kan være påkrævet.
</td></tr>
<tr>
<td>Løsning</td><td>
Kør en fuld systemscanning.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508025
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_MANUAL_STEPS_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at manuelle trin er nødvendige for at udføre fjernelse af trusler.
</td></tr><tr><td>Løsning</td><td>
Følg de manuelle afhjælpningstrin, der er beskrevet <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">i Microsoft Malware Protection Encyclopedia</a>. Du kan finde et trusselsspecifikt link i hændelsesoversigten.<br/></td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508026
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at fjernelse inden i beholdertypen muligvis ikke understøttes.
</td></tr><tr><td>Løsning</td><td>
Microsoft Defender Antivirus kan ikke løse trusler, der er registreret i arkivet. Overvej manuelt at fjerne de registrerede ressourcer.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508027
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_REMOVE_LOW_MEDIUM_DISABLED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at fjernelse af lave og mellemstor trusler kan være deaktiveret.
</td></tr><tr><td>Løsning</td><td>
Kontrollér de registrerede trusler, og løs dem efter behov.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508029
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERROR_MP_RESCAN_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at en kant af truslerne er påkrævet.
</td></tr><tr><td>Løsning</td><td>
Kør en fuld systemscanning.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508030
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERROR_MP_CALLISTO_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, at en offlinescanning er påkrævet.
</td></tr><tr><td>Løsning</td><td>
Kør offline Microsoft Defender Antivirus. Du kan læse om, hvordan du gør dette i <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">artiklen Microsoft Defender Antivirus offline.</a>
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508031
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl indikerer, Microsoft Defender Antivirus ikke understøtter den aktuelle version af platformen og kræver en ny version af platformen.
</td></tr><tr><td>Løsning</td><td>
Du kan kun bruge Microsoft Defender Antivirus i Windows 10 og Windows 11. Hvis Windows 8, Windows 7 og Windows Vista, kan du <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">bruge System Center Endpoint Protection</a>.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Følgende fejlkoder bruges ved intern test af Microsoft Defender Antivirus.

Hvis du får vist disse fejl, kan du prøve at [opdatere definitioner](manage-updates-baselines-microsoft-defender-antivirus.md) og gennemtvinge en kant direkte på slutpunktet.


<table>
<tr>
<th colspan="3">Interne fejlkoder</th>
</tr>
<tr>
<th><b>Fejlkode</b></th>
<th>Meddelelse vist</th>
<th>Mulig årsag til fejl og løsning</th>
</tr>
<tr>
<td>
0x80501004
</td>
<td>
<b>ERROR_MP_NO_INTERNET_CONN </b>
</td>
<td>
Kontrollér din internetforbindelse, og kør scanningen igen.
</td>
</tr>
<tr>
<td>
0x80501000
</td>
<td>
<b>ERROR_MP_UI_CONSOLIDATION_BAS</b> E
</td>
<td rowspan="34">
Dette er en intern fejl. Årsagen er ikke klart defineret.
</td>
<td rowspan="36">

</td>
</tr>
<tr>
<td>
0x80501001
</td>
<td>
<b>ERROR_MP_ACTIONS_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80501002
</td>
<td>
<b>ERROR_MP_NOENGINE</b>
</td>
</tr>
<tr>
<td>
0x80501003
</td>
<td>
<b>ERROR_MP_ACTIVE_THREATS</b>
</td>
</tr>
<tr>
<td>
0x805011011
</td>
<td>
<b>MP_ERROR_CODE_LUA_CANCELLED </b>
</td>
</tr>
<tr>
<td>
0x80501101
</td>
<td>
<b>ERROR_LUA_CANCELLATION </b>
</td>
</tr>
<tr>
<td>
0x80501102
</td>
<td>
<b>MP_ERROR_CODE_ALREADY_SHUTDOWN</b>
</td>
</tr>
<tr>
<td>
0x80501103
</td>
<td>
<b>MP_ERROR_CODE_RDEVICE_S_ASYNC_CALL_PENDING </b>
</td>
</tr>
<tr>
<td>
0x80501104
</td>
<td>
<b>MP_ERROR_CODE_CANCELLED</b>
</td>
</tr>
<tr>
<td>
0x80501105
</td>
<td>
<b>MP_ERROR_CODE_NO_TARGETOS</b>
</td>
</tr>
<tr>
<td>
0x80501106
</td>
<td>
<b>MP_ERROR_CODE_BAD_REGEXP</b>
</td>
</tr>
<tr>
<td>
0x80501107
</td>
<td>
<b>MP_ERROR_TEST_INDUCED_ERROR</b>
</td>
</tr>
<tr>
<td>
0x80501108
</td>
<td>
<b>MP_ERROR_SIG_BACKUP_DISABLED</b>
</td>
</tr>
<tr>
<td>
0x80508001
</td>
<td>
<b>ERR_MP_BAD_INIT_MODULES</b>
</td>
</tr>
<tr>
<td>
0x80508002
</td>
<td>
<b>ERR_MP_BAD_DATABASE</b>
</td>
</tr>
<tr>
<td>
0x80508004
</td>
<td>
<b>ERR_MP_BAD_UFS </b>
</td>
</tr>
<tr>
<td>
0x8050800C
</td>
<td>
<b>ERR_MP_BAD_INPUT_DATA</b>
</td>
</tr>
<tr>
<td>
0x8050800D
</td>
<td>
<b>ERR_MP_BAD_GLOBAL_STORAGE</b>
</td>
</tr>
<tr>
<td>
0x8050800E
</td>
<td>
<b>ERR_MP_OBSOLETE</b>
</td>
</tr>
<tr>
<td>
0x8050800F
</td>
<td>
<b>ERR_MP_NOT_SUPPORTED</b>
</td>
</tr>
<tr>
<td>
0x8050800F 0x80508010
</td>
<td>
<b>ERR_MP_NO_MORE_ITEMS </b>
</td>
</tr>
<tr>
<td>
0x80508011
</td>
<td>
<b>ERR_MP_DUPLICATE_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508012
</td>
<td>
<b>ERR_MP_BAD_SCANID</b>
</td>
</tr>
<tr>
<td>
0x80508013
</td>
<td>
<b>ERR_MP_BAD_USERDB_VERSION</b>
</td>
</tr>
<tr>
<td>
0x80508014
</td>
<td>
<b>ERR_MP_RESTORE_FAILED</b>
</td>
</tr>
<tr>
<td>
0x80508016
</td>
<td>
<b>ERR_MP_BAD_ACTION</b>
</td>
</tr>
<tr>
<td>
0x80508019
</td>
<td>
<b>ERR_MP_NOT_FOUND</b>
</td>
</tr>
<tr>
<td>
0x80509001
</td>
<td>
<b>ERR_RELO_BAD_EHANDLE</b>
</td>
</tr>
<tr>
<td>
0x80509003
</td>
<td>
<b>ERR_RELO_KERNEL_NOT_LOADED</b>
</td>
</tr>
<tr>
<td>
0x8050A001
</td>
<td>
<b>ERR_MP_BADDB_OPEN</b>
</td>
</tr>
<tr>
<td>
0x8050A002
</td>
<td>
<b>ERR_MP_BADDB_HEADER</b>
</td>
</tr>
<tr>
<td>
0x8050A003
</td>
<td>
<b>ERR_MP_BADDB_OLDENGINE</b>
</td>
</tr>
<tr>
<td>
0x8050A004
</td>
<td>
<b>ERR_MP_BADDB_CONTENT </b>
</td>
</tr>
<tr>
<td>
0x8050A005
</td>
<td>
<b>ERR_MP_BADDB_NOTSIGNED</b>
</td>
</tr>
<tr>
<td>
0x8050801
</td>
<td>
<b>ERR_MP_REMOVE_FAILED</b>
</td>
<td>
Dette er en intern fejl. Det kan blive udløst, når fjernelse af malware ikke lykkes.
</td>
</tr>
<tr>
<td>
0x80508018
</td>
<td>
<b>ERR_MP_SCAN_ABORTED </b>
</td>
<td>
Dette er en intern fejl. Det kan have udløst en scanning, der ikke kan fuldføres.
</td>
</tr>
</table>

## <a name="related-topics"></a>Relaterede emner

- [Rapport om Microsoft Defender Antivirus beskyttelse](report-monitor-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
