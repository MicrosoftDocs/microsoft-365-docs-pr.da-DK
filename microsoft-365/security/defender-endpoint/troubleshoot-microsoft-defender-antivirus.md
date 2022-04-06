---
title: Microsoft Defender Antivirus hændelses-id'er og fejlkoder
description: Slå årsager og løsninger op for Microsoft Defender Antivirus hændelses-id'er og fejl
keywords: hændelse, fejlkode, siem, logføring, fejlfinding, wef, videresendelse af Windows-hændelse
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
ms.openlocfilehash: c1fcf71aa91e944e36050dae85f0c31a316df344
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665442"
---
# <a name="review-event-logs-and-error-codes-to-troubleshoot-issues-with-microsoft-defender-antivirus"></a>Gennemse hændelseslogge og fejlkoder for at foretage fejlfinding af problemer med Microsoft Defender Antivirus

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Hvis du støder på et problem med Microsoft Defender Antivirus, kan du søge i tabellerne i dette emne for at finde et matchende problem og en potentiel løsning.

Listen over tabeller:

- [Microsoft Defender Antivirus hændelses-id'er](#windows-defender-av-ids) (disse gælder for Windows 10, Windows 11 og Windows Server 2016)
- [Microsoft Defender Antivirus klientfejlkoder](#error-codes)
- [Interne Microsoft Defender Antivirus klientfejlkoder (bruges af Microsoft under udvikling og test)](#internal-error-codes)

> [!TIP]
> Du kan også besøge webstedet for Microsoft Defender for Endpoint demo på [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at bekræfte, at følgende funktioner fungerer:
>
> - Skybaseret beskyttelse
> - Hurtig læring (herunder Blok ved første øjekast)
> - Potentielt uønsket programblokering

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

<a id="windows-defender-av-ids"></a>
## <a name="microsoft-defender-antivirus-event-ids"></a>id'er for Microsoft Defender Antivirus begivenhed

Microsoft Defender Antivirus registrerer hændelses-id'er i Windows hændelsesloggen.

Du kan få vist hændelsesloggen direkte, eller hvis du har et VÆRKTØJ til administration af hændelser fra tredjepart og et SIEM-værktøj (Event Management), kan du også bruge [Microsoft Defender Antivirus klienthændelses-id'er](troubleshoot-microsoft-defender-antivirus.md#windows-defender-av-ids) til at gennemse bestemte hændelser og fejl fra dine slutpunkter.

I tabellen i dette afsnit vises de primære Microsoft Defender Antivirus hændelses-id'er og, hvor det er muligt, forslag til løsninger til at rette eller løse fejlen.

## <a name="to-view-a-microsoft-defender-antivirus-event"></a>Sådan får du vist en Microsoft Defender Antivirus hændelse

1. Åbn **Logbog**.
2. Udvid **Logfiler for programmer og tjenester** i konsoltræet, derefter **Microsoft****, Windows** og derefter **Windows Defender**.
3. Dobbeltklik på **Handling**.
4. I detaljeruden kan du se listen over individuelle hændelser, der skal findes din begivenhed.
5. Klik på hændelsen for at se specifikke oplysninger om en hændelse i den nederste rude under fanerne **Generelt** og **Detaljer** .

<table>
<tr>
<th colspan="2" >Hændelses-id: 1000</th>
</tr>
<tr>
<td>
Symbolsk navn:
</td>
<td>
<b>MALWAREPROTECTION_SCAN_STARTED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>En antimalwarescanning startede. </b>
</td>
</tr>
<tr>
<td >
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummer for den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scan parametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Scan ressourcer: &lt; Ressourcer (f.eks. filer/mapper/BHO), der blev scannet.&gt;</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1001</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_COMPLETED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>En antimalwarescanning er fuldført.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummer for den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scan parametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt; Domænelt&gt;\&; UserScan&gt;</dt> 
<dt>Tid: &lt;Varigheden af en scanning.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1002</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_CANCELLED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>En antimalwarescanning blev stoppet, før den blev fuldført. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummer for den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scan parametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt; Domænelt&gt;&amp;; UserScan&gt;</dt> 
<dt>Tid: &lt;Varigheden af en scanning.&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1003</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_PAUSED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>En antimalwarescanning blev midlertidigt afbrudt. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummer for den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scan parametre&gt;, f.eks.:<ul>
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
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_RESUMED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>En antimalwarescanning blev genoptaget. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
<dl>
<dt>Scannings-id: &lt; Id-nummer for den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scan parametre&gt;, f.eks.:<ul>
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
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SCAN_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
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
<dt>Scannings-id: &lt; Id-nummer for den relevante scanning.&gt;</dt>
<dt> Scanningstype: &lt;Scanningstype&gt;, f.eks.:<ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
</ul>
</dt>
<dt>Scanningsparametre: &lt;Scan parametre&gt;, f.eks.:<ul>
<li>Fuld scanning</li>
<li>Hurtig scanning</li>
<li>Kundescanning</li>
</ul>
</dt>
<dt>Bruger: &lt; Domænelt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Antivirusklienten stødte på en fejl, og den aktuelle scanning er stoppet. Scanningen kan mislykkes på grund af et problem på klientsiden. Denne hændelsespost indeholder scannings-id, scanningstype (Microsoft Defender Antivirus, antispyware, antimalware), scanningsparametre, den bruger, der startede scanningen, fejlkoden og en beskrivelse af fejlen.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li>Kør scanningen igen.</li>
<li>Hvis det mislykkes på samme måde, skal du gå til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">webstedet Microsoft Support</a> og angive fejlnummeret <b>i søgefeltet</b> for at søge efter fejlkoden.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1006</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_DETECTED </b>
</td>
</tr>
<tr>
<td>
Besked:
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
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiDetection&gt;</dt>
<dt> Origin: &lt;Registreringsoprindelse&gt;, f.eks.:<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: &lt;Registreringstype&gt;, f.eks.:<ul>
<li>Heuristik</li>
<li>Generiske</li>
<li>Konkrete</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde&gt; f.eks.:<ul>
<li>Bruger: bruger initieret</li>
<li>System: systemet er startet</li>
<li>Realtid: Komponent i realtid er startet</li>
<li>IOAV: IE Downloads og Outlook Express Attachments initieret</li>
<li>NIS: Netværkskontrolsystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige websidekontrolelementer</li>
<li>Elam (Early Launch Antimalware). Dette omfatter malware, der registreres af startsekvensen</li>
<li>Fjern attestation</li>
</ul>AMSI (Antimalware Scan Interface). Bruges primært til at beskytte scripts (PowerShell, VBS), selvom det også kan aktiveres af tredjeparter.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Navn: &lt;Proces i PIDSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1007</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus har taget skridt til at beskytte denne maskine mod malware eller anden potentielt uønsket software. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Bruger: &lt; Domænelt&gt;\&; Brugernavn&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt>
<dt> Handling: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev renset</li>
<li>Karantæne: Ressourcen er sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at køre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er én fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Blok: Ressourcen blev blokeret fra at køre</li>
</ul>
</dt>
<dt>Status: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1008</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus er stødt på en fejl, når der udføres handlinger på malware eller anden potentielt uønsket software. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Bruger: &lt; Domænelt&gt;\&; Brugernavn&gt;</dt>
<dt>: &lt;Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiHandling&gt;</dt>
<dt>: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev renset</li>
<li>Karantæne: Ressourcen er sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at køre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er én fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Blok: Ressourcen blev blokeret fra at køre</li>
</ul>
</dt>
<dt>Fejlkode: &lt; Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Status: &lt; StatusSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1009</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareplatformen gendannede et element fra karantæne. </b>
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
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiBruger&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1010</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_RESTORE_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus har fundet en fejl under forsøg på at gendanne et element fra karantæne. Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiBruger&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1011</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareplatformen slettede et element fra karantæne. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har slettet et element fra karantænen.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiBruger&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserSignature&gt;</dt> 
<dt>Version: &lt;Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1012</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_QUARANTINE_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalware-platformen kunne ikke slette et element fra karantænen.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl under forsøg på at slette et element fra karantæne.
Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiBruger&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1013</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareplatformen slettede historikken for malware og anden potentielt uønsket software.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fjernet malwarehistorikken og anden potentielt uønsket software.
<dl>
<dt>Klokkeslæt: Det tidspunkt, hvor hændelsen indtraf, f.eks. når historikken fjernes. Denne parameter bruges ikke i trusselshændelser, så der ikke er nogen forvirring om, hvorvidt det er afhjælpningstid eller infektionstid. For dem kalder vi dem specifikt som Handlingstid eller Registreringstid.</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1014</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_MALWARE_HISTORY_DELETE_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
Antimalware-platformen kunne ikke slette historikken for malware og anden potentielt uønsket software.
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus er stødt på en fejl under forsøg på at fjerne historikken for malware og anden potentielt uønsket software.
<dl>
<dt>Klokkeslæt: Det tidspunkt, hvor hændelsen indtraf, f.eks. når historikken fjernes. Denne parameter bruges ikke i trusselshændelser, så der ikke er nogen forvirring om, hvorvidt det er afhjælpningstid eller infektionstid. For dem kalder vi dem specifikt som Handlingstid eller Registreringstid.</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier. </dt>
<dt>Fejlbeskrivelse: &lt;Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1015</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_BEHAVIOR_DETECTED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareplatformen registrerede mistænkelig funktionsmåde.</b>
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
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiDetection&gt;</dt>
<dt> Origin: &lt;Registreringsoprindelse&gt;, f.eks.:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: &lt;Registreringstype&gt;, f.eks.:<ul>
<li>Heuristik</li>
<li>Generiske</li>
<li>Konkrete</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde&gt; f.eks.:<ul>
<li>Bruger: bruger initieret</li>
<li>System: systemet er startet</li>
<li>Realtid: Komponent i realtid er startet</li>
<li>IOAV: IE Downloads og Outlook Express Attachments initieret</li>
<li>NIS: Netværkskontrolsystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige websidekontrolelementer</li>
<li>Elam (Early Launch Antimalware). Dette omfatter malware, der registreres af startsekvensen</li>
<li>Fjern attestation</li>
</ul>AMSI (Antimalware Scan Interface). Bruges primært til at beskytte scripts (PowerShell, VBS), selvom det også kan aktiveres af tredjeparter.
UACStatus</dt>
<dt>: &lt;StatusUser&gt;</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess-navn&gt;</dt>
<dt>: &lt;Behandl i PIDSignature-id'et&gt;</dt>
<dt>: Optælling med matchende alvorsgrad.</dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram versionFidelity&gt;</dt> 
<dt>Label:</dt>
<dt>Target File Name: &lt;Filnavn&gt; Navnet på filen.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1116</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_DETECTED</b>
</td>
</tr>
<tr>
<td>
Besked:
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
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiDetection&gt;</dt>
<dt> Origin: &lt;Registreringsoprindelse&gt;, f.eks.:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: &lt;Registreringstype&gt;, f.eks.:<ul>
<li>Heuristik</li>
<li>Generiske</li>
<li>Konkrete</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde&gt; f.eks.:<ul>
<li>Bruger: bruger initieret</li>
<li>System: systemet er startet</li>
<li>Realtid: Komponent i realtid er startet</li>
<li>IOAV: IE Downloads og Outlook Express Attachments initieret</li>
<li>NIS: Netværkskontrolsystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige websidekontrolelementer</li>
<li>Elam (Early Launch Antimalware). Dette omfatter malware, der registreres af startsekvensen</li>
<li>Fjern attestation</li>
</ul>AMSI (Antimalware Scan Interface). Bruges primært til at beskytte scripts (PowerShell, VBS), selvom det også kan aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; UserProcess&gt;</dt> 
<dt>Navn: &lt;Proces i PIDSignature&gt;</dt> 
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
Der kræves ingen handling. Microsoft Defender Antivirus kan suspendere og udføre rutinemæssige handlinger på denne trussel. Hvis du vil fjerne truslen manuelt, skal du klikke på <b>Ren computer</b> i grænsefladen Microsoft Defender Antivirus.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1117</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_TAKEN </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus har taget skridt til at beskytte denne maskine mod malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiDetection&gt;</dt>
<dt> Origin: &lt;Registreringsoprindelse&gt;, f.eks.:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: &lt;Registreringstype&gt;, f.eks.:<ul>
<li>Heuristik</li>
<li>Generiske</li>
<li>Konkrete</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde&gt; f.eks.:<ul>
<li>Bruger: bruger initieret</li>
<li>System: systemet er startet</li>
<li>Realtid: Komponent i realtid er startet</li>
<li>IOAV: IE Downloads og Outlook Express Attachments initieret</li>
<li>NIS: Netværkskontrolsystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige websidekontrolelementer</li>
<li>Elam (Early Launch Antimalware). Dette omfatter malware, der registreres af startsekvensen</li>
<li>Fjern attestation</li>
</ul>AMSI (Antimalware Scan Interface). Bruges primært til at beskytte scripts (PowerShell, VBS), selvom det også kan aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Navn på brugerproces&gt;</dt>
<dt>: &lt;Proces i PIDAction&gt;</dt>
<dt>: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev renset</li>
<li>Karantæne: Ressourcen er sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at køre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er én fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Blok: Ressourcen blev blokeret fra at køre</li>
</ul>
</dt>
<dt>Handlingsstatus: &lt; Beskrivelse af yderligere handlingerFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt> BEMÆRK! Når Microsoft Defender Antivirus, Microsoft Security Essentials, Værktøj til fjernelse af skadelig software eller System Center Endpoint Protection registrerer en malware, gendanner den følgende systemindstillinger og tjenester, som malwaren kan have ændret:<ul>
<li>Standardindstilling for Internet Explorer eller Microsoft Edge</li>
<li>Indstillinger for bruger Access Control</li>
<li>Chrome-indstillinger</li>
<li>Startkontroldata</li>
<li>Indstillinger for Regedit og Jobliste i registreringsdatabasen</li>
<li>Windows Update, Background Intelligent Transfer Service og Remote Procedure Call Service</li>
<li>filer Windows operativsystemet</li></ul>
Ovenstående kontekst gælder for følgende klient- og serverversioner:
<table>
<tr>
<th>Operativsystem</th>
<th>Operativsystemversion</th>
</tr>
<tr>
<td>
Klientoperativsystem
</td>
<td>
Windows Vista (Service Pack 1 eller Service Pack 2), Windows 7 og nyere
</td>
</tr>
<tr>
<td>
Serveroperativsystem
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
Det er ikke nødvendigt at gøre noget. Microsoft Defender Antivirus fjernet eller sat en trussel i karantæne.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1118</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_FAILED</b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus er stødt på en ikke-kritisk fejl, når der udføres handlinger på malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiDetection&gt;</dt>
<dt> Origin: &lt;Registreringsoprindelse&gt;, f.eks.:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: &lt;Registreringstype&gt;, f.eks.:<ul>
<li>Heuristik</li>
<li>Generiske</li>
<li>Konkrete</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde&gt; f.eks.:<ul>
<li>Bruger: bruger initieret</li>
<li>System: systemet er startet</li>
<li>Realtid: Komponent i realtid er startet</li>
<li>IOAV: IE Downloads og Outlook Express Attachments initieret</li>
<li>NIS: Netværkskontrolsystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige websidekontrolelementer</li>
<li>Elam (Early Launch Antimalware). Dette omfatter malware, der registreres af startsekvensen</li>
<li>Fjern attestation</li>
</ul>AMSI (Antimalware Scan Interface). Bruges primært til at beskytte scripts (PowerShell, VBS), selvom det også kan aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Navn på brugerproces&gt;</dt>
<dt>: &lt;Proces i PIDAction&gt;</dt>
<dt>: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev renset</li>
<li>Karantæne: Ressourcen er sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at køre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er én fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Blok: Ressourcen blev blokeret fra at køre</li>
</ul>
</dt>
<dt>Handlingsstatus: &lt; Beskrivelse af yderligere handlingerFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
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
Det er ikke nødvendigt at gøre noget. Microsoft Defender Antivirus kunne ikke fuldføre en opgave, der er relateret til afhjælpning af malware. Dette er ikke en alvorlig fejl.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1119</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_STATE_MALWARE_ACTION_CRITICALLY_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareplatformen stødte på en alvorlig fejl under forsøg på at udføre handlinger på malware eller anden potentielt uønsket software. Der er flere oplysninger i hændelsesmeddelelsen.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus er stødt på en alvorlig fejl, når der udføres handlinger på malware eller anden potentielt uønsket software.<br/>Brug nedenstående links til at få flere oplysninger:
<dl>
<dt>Navn: &lt; Threat nameID&gt;</dt>
<dt>: &lt;Threat IDSeverity&gt;</dt>
<dt>: &lt;Alvorsgrad&gt;, f.eks.:<ul>
<li>Lav</li>
<li>Moderat</li>
<li>Høj</li>
<li>Alvorlige</li>
</ul>
</dt>
<dt>Kategori: &lt; Kategoribeskrivelse&gt;, f.eks. enhver trussels- eller malwaretype.</dt> 
<dt>Sti: &lt; FilstiDetection&gt;</dt>
<dt> Origin: &lt;Registreringsoprindelse&gt;, f.eks.:
<ul>
<li>Unknown</li>
<li>Lokal computer</li>
<li>Netværksshare</li>
<li>Internet</li>
<li>Indgående trafik</li>
<li>Udgående trafik</li>
</ul>
</dt>
<dt>Registreringstype: &lt;Registreringstype&gt;, f.eks.:<ul>
<li>Heuristik</li>
<li>Generiske</li>
<li>Konkrete</li>
<li>Dynamisk signatur</li>
</ul>
</dt>
<dt>Registreringskilde: &lt;Registreringskilde&gt; f.eks.:<ul>
<li>Bruger: bruger initieret</li>
<li>System: systemet er startet</li>
<li>Realtid: Komponent i realtid er startet</li>
<li>IOAV: IE Downloads og Outlook Express Attachments initieret</li>
<li>NIS: Netværkskontrolsystem</li>
<li>IEPROTECT: IE - IExtensionValidation; dette beskytter mod skadelige websidekontrolelementer</li>
<li>Elam (Early Launch Antimalware). Dette omfatter malware, der registreres af startsekvensen</li>
<li>Fjern attestation</li>
</ul>AMSI (Antimalware Scan Interface). Bruges primært til at beskytte scripts (PowerShell, VBS), selvom det også kan aktiveres af tredjeparter.
UACUser</dt>
<dt>: &lt;Domainlt&gt;\&; Navn på brugerproces&gt;</dt>
<dt>: &lt;Proces i PIDAction&gt;</dt>
<dt>: &lt;Handling&gt;, f.eks.:<ul>
<li>Rens: Ressourcen blev renset</li>
<li>Karantæne: Ressourcen er sat i karantæne</li>
<li>Fjern: Ressourcen blev slettet</li>
<li>Tillad: Ressourcen fik tilladelse til at køre/eksistere</li>
<li>Brugerdefineret: Brugerdefineret handling, der normalt er én fra denne liste over handlinger, som brugeren har angivet</li>
<li>Ingen handling: Ingen handling</li>
<li>Blok: Ressourcen blev blokeret fra at køre</li>
</ul>
</dt>
<dt>Handlingsstatus: &lt; Beskrivelse af yderligere handlingerFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
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
Den Microsoft Defender Antivirus klient registrerede denne fejl på grund af alvorlige problemer. Slutpunktet er muligvis ikke beskyttet. Gennemse fejlbeskrivelsen, og følg derefter de relevante <b>trin til brugerhandlingen</b> nedenfor.
<table>
<tr>
<th>Handling</th>
<th>Brugerhandling</th>
</tr>
<tr>
<td>
<b>Fjerne</b>
</td>
<td>
Opdater definitionerne, og kontrollér derefter, at fjernelsen lykkedes.
</td>
</tr>
<tr>
<td>
<b>Ren</b>
</td>
<td>
Opdater definitionerne, og kontrollér derefter, at afhjælpningen lykkedes.
</td>
</tr>
<tr>
<td>
<b>Karantæne</b>
</td>
<td>
Opdater definitionerne, og kontrollér, at brugeren har tilladelse til at få adgang til de nødvendige ressourcer.
</td>
</tr>
<tr>
<td>
<b>Tillade</b>
</td>
<td>
Kontrollér, at brugeren har tilladelse til at få adgang til de nødvendige ressourcer.
</td>
</tr>
</table>

Hvis denne hændelse fortsætter:<ol>
<li>Kør scanningen igen.</li>
<li>Hvis det mislykkes på samme måde, skal du gå til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">webstedet Microsoft Support</a> og angive fejlnummeret <b>i søgefeltet</b> for at søge efter fejlkoden.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1120</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_THREAT_HASH</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Microsoft Defender Antivirus har udledt hashen for en trusselsressource.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus klient kører i en tilstand, der er i orden.
<dl>
<dt>Aktuel platformversion: &lt; Aktuel platformversionThreat&gt;</dt> 
<dt>Ressourcesti: &lt;PathHashes&gt;</dt>
<dt>: &lt;Hashes&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td></td>
<td >
<div class="alert"><b>Bemærk! Denne hændelse logføres kun, hvis følgende politik er angivet: <b>ThreatFileHashLogging usigneret</b>.</div>
<div> </div>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1127</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_FOLDER_GUARD_SECTOR_BLOCK</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>CFA (Controlled Folder Access) blokerede en proces, der ikke er tillid til, fra at foretage ændringer i hukommelsen. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Adgang til styrede mapper har blokeret en proces, der ikke er tillid til, fra potentielt at ændre disksektorer.
<br/> Du kan få flere oplysninger om hændelsesposten i følgende:
<dl>
<dt>EventID: &lt; EventID&gt;, f.eks.: 1127Version</dt>
<dt>: &lt;Version&gt;, for eksempel:</dt> 
<dt>0Level: &lt;Level&gt;, for eksempel: win:WarningTimeCreated</dt>
<dt>: &lt;SystemTime&gt;, tidspunkt hvor hændelsen blev oprettetEventRecordID</dt>
<dt>: &lt;EventRecordID&gt;, indeksnummer for hændelsen i hændelsesloggenExecution</dt> 
<dt>ProcessID: &lt;Execution ProcessID&gt;, proces, der genererede hændelsenChannel</dt>
<dt>: &lt;Hændelseskanal&gt;, f.eks.: Microsoft- Windows-Windows Defender/OperationalComputer</dt>
<dt>: &lt;ComputernavnSikkerhed&gt;</dt> 
<dt>Bruger-id: &lt;Sikkerhedsbruger-idProduktnavn&gt;</dt>
<dt>: &lt;Produktnavn&gt;, f.eks.: Microsoft Defender Antivirus</dt> 
<dt>Produktversion: &lt;ProduktversionRegistreringstid&gt;</dt>
<dt>: &lt;Registreringstid&gt;, hvor CFA blokerede en procesbruger, der ikke er tillid til</dt>
<dt>: &lt;Domainlt&gt;\&; UserPath&gt;</dt>
<dt>: &lt;Enhedsnavn&gt;, navn på den enhed eller disk, som en proces, der ikke er tillid til, blev åbnet for modifikationProcesnavn</dt>
<dt>: &lt;Processti&gt;, navnet på processtien, som CFA blokerede fra at få adgang til enheden eller disken til ændringSecurity</dt> 
<dt>Intelligence Version: &lt;Security Intelligence versionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram version&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Brugeren kan føje den blokerede proces til listen <i>Over tilladte processer</i> for CFA ved hjælp af Powershell eller Windows Sikkerhed Center.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 1150</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTHY</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Hvis din antimalwareplatform rapporterer status til en overvågningsplatform, angiver denne hændelse, at antimalwareplatformen kører og er i en sund tilstand. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus klient kører i en tilstand, der er i orden.
<dl>
<dt>Platformversion: &lt; Aktuel platformversionSignature&gt;</dt> 
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
Det er ikke nødvendigt at gøre noget. Den Microsoft Defender Antivirus klient er i en tilstand, der er i orden. Denne hændelse rapporteres på timebasis.
</td>
</tr>

<tr>
<th colspan="2">Hændelses-id: 1151</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SERVICE_HEALTH_REPORT</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Endpoint Protection klienttilstandsrapport (tid i UTC)</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Tilstandsrapport for antivirusklient.
<dl>
<dt>Platformversion: &lt; Aktuel platformversionEngine&gt;</dt> 
<dt>Version: &lt;antimalwareprogram versionNetwork&gt;</dt> 
<dt>Realtime Inspection engine version: &lt;Network Realtime Inspection engine versionAntivirus&gt;</dt> 
<dt>signaturversion: &lt;Antivirus signaturversionAntispyware&gt;</dt> 
<dt>signaturversion: &lt;Antispyware signaturversionNetwork&gt;</dt> 
<dt>Signaturversion for realtidskontrol: &lt; Netværk RealtidskontrolsignaturversionRTP-tilstand&gt;</dt>
<dt>: &lt;Realtidsbeskyttelsestilstand&gt; (aktiveret eller deaktiveret)</dt>
<dt>OA-tilstand: &lt;Ved Adgangstilstand&gt; (aktiveret eller deaktiveret)</dt>
<dt>IOAV-tilstand: &lt;IE-downloads og Outlook tilstanden&gt; Express Attachments (Enabled eller Disabled)</dt>
<dt>BM-tilstand: Tilstand for &lt;overvågning af&gt; funktionsmåde (aktiveret eller deaktiveret)</dt>
<dt>Antivirussignaturalder: &lt;Alder på antivirussignatur&gt;  (i dage)</dt> 
<dt>Alder for antispywaresignatur: &lt; Antispywaresignaturalder&gt; (i dage)</dt>
<dt>Sidste hurtigscanningsalder: &lt;Sidste hurtig scanningsalder&gt; (i dage)</dt>
<dt>Sidste fulde scanningsalder: &lt;Sidste fulde scanningsalder&gt; (i dage)</dt>
<dt>Oprettelsestid for antivirussignatur: ?&lt; Oprettelse af antivirussignatur timeAntispyware&gt;</dt> 
<dt>tidspunktet for oprettelse af signatur: ?&lt; Oprettelse af antispywaresignatursidste&gt;</dt> 
<dt>starttidspunkt for hurtig scanning: ?&lt; Starttidspunkt&gt; for seneste hurtig</dt> 
<dt>scanningSidste sluttidspunkt for hurtig scanning: ?&lt; Sidste sluttidspunkt&gt; for hurtig scanningSidste</dt> 
<dt>hurtigsøgningskilde: &lt;Seneste hurtigsøgningskilde&gt; (0 = scanningen blev ikke kørt, 1 = brugeren startede, 2 = systemet startede)</dt>
<dt>Sidste starttidspunkt for fuld scanning: ?&lt; Sidste fulde scanningsstarttidspunktSidste&gt;</dt> 
<dt>fulde scanningssluttidspunkt: ?&lt; Sidste fulde scanningssluttidSidste&gt;</dt> 
<dt>fulde scanningskilde: &lt;Seneste komplette scanningskilde&gt; (0 = scanningen blev ikke kørt, 1 = brugerinitieret, 2 = systeminitieret)</dt>
<dt>Produktstatus: Til intern fejlfinding
</dl>
</td>
</tr>

<tr>
<th colspan="2">Hændelses-id: 2000</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwaredefinitionerne blev opdateret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Antivirussignaturversionen er blevet opdateret.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionPrevious&gt;</dt> 
<dt>Signaturversion: &lt;Tidligere signaturversionSignature&gt;</dt>
<dt> Type: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Opdateringstype: &lt; Opdateringstype&gt;, enten Fuld eller Delta.</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Aktuel programversionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Tidligere programversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Det er ikke nødvendigt at gøre noget. Den Microsoft Defender Antivirus klient er i en tilstand, der er i orden. Denne hændelse rapporteres, når signaturer opdateres.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2001</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Opdateringen af security intelligence mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl under forsøg på at opdatere signaturer.
<dl>
<dt>Ny version af security intelligence: &lt; Nyt versionsnummerPrevious&gt;</dt> 
<dt>security intelligence-version: &lt;Forrige versionOpdateringskilde&gt;</dt>
<dt>: &lt;Opdateringskilde&gt;, f.eks.:
<ul>
<li>Mappe til opdatering af sikkerhedsintelligens</li>
<li>Intern sikkerhedsintelligensopdateringsserver</li>
<li>Microsoft Update Server</li>
<li>Filshare</li>
<li>Microsoft Malware Protection Center (MMPC)</li>
</ul>
</dt>
<dt>Opdateringsfase: &lt;Opdateringsfase&gt;, f.eks.:
<ul>
<li>Søg</li>
<li>Download</li>
<li>Installere</li>
</ul>
</dt>
<dt>Kildesti: Filnavn for UNC (Universal Naming Convention), servernavn for Windows Server Update Services (WSUS)/Microsoft Update/ADL.</dt>
<dt> Signaturtype: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Opdateringstype: &lt; Opdateringstype&gt;, enten Fuld eller Delta.</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; UserCurrent&gt;</dt> 
<dt>Engine Version: &lt;Aktuel programversionPrevious&gt;</dt> 
<dt>Programversion: &lt;Tidligere programversionFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
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
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Opdater definitioner</a> , og gennemtving en scanning direkte på slutpunktet.</li>
<li>Gennemse posterne i filen %Windir%\WindowsUpdate.log for at få flere oplysninger om denne fejl.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2002</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATED</b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus programversion er blevet opdateret.
<dl>
<dt>Aktuel programversion: &lt; Aktuel programversionPrevious&gt;</dt> 
<dt>Engine Version: &lt;Tidligere programversionEngine&gt;</dt> 
<dt>Type: &lt;Programtype&gt;, enten antimalwareprogram eller Network Inspection System-program.</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; Bruger&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Det er ikke nødvendigt at gøre noget. Den Microsoft Defender Antivirus klient er i en tilstand, der er i orden. Denne hændelse rapporteres, når antimalwareprogrammet opdateres.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2003</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_FAILED</b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus stødte på en fejl under forsøg på at opdatere programmet.
<dl>
<dt>Ny programversion:</dt>
<dt>Tidligere programversion: &lt;Tidligere programversionEnginetype&gt;</dt>
<dt>: &lt;Programtype&gt;, enten antimalwareprogram eller Network Inspection System-program.</dt> 
<dt>Bruger: &lt; Domænelt&gt;\&; UserError&gt;</dt> 
<dt>Code: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Den Microsoft Defender Antivirus klientopdatering mislykkedes. Denne hændelse opstår, når klienten ikke kan opdatere sig selv. Denne hændelse skyldes normalt en afbrydelse i netværksforbindelsen under en opdatering.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li><a href="manage-updates-baselines-microsoft-defender-antivirus.md" data-raw-source="[Update definitions](manage-updates-baselines-microsoft-defender-antivirus.md)">Opdater definitioner</a> , og gennemtving en scanning direkte på slutpunktet.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2004</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_REVERSION</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Der opstod et problem under indlæsning af antimalwaredefinitioner. Antimalwareprogrammet forsøger at indlæse det sidst kendte fungerende sæt definitioner.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har registreret en fejl under forsøg på at indlæse signaturer og vil forsøge at vende tilbage til et kendt fungerende sæt signaturer.
<dl>
<dt>Signaturer Forsøgt:</dt>
<dt>Fejlkode: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Signaturversion: &lt; Definition versionEngine&gt;</dt> 
<dt>Version: &lt;Antimalware-programversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Den Microsoft Defender Antivirus klient forsøgte at hente og installere den nyeste definitionsfil og mislykkedes. Denne fejl kan opstå, når klienten støder på en fejl under forsøg på at indlæse definitionerne, eller hvis filen er beskadiget. Microsoft Defender Antivirus vil forsøge at vende tilbage til et kendt og godt sæt definitioner.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li>Genstart computeren, og prøv igen.</li>
<li>Download de nyeste definitioner fra <a href="https://aka.ms/wdsi">Microsoft Sikkerhedsviden websted</a>.
Bemærk! Størrelsen på definitionsfilen, der downloades fra webstedet, kan overstige 60 MB og bør ikke bruges som en langsigtet løsning til opdatering af definitioner.
</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2005</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_UPDATE_PLATFORMOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareprogrammet kunne ikke indlæses, fordi antimalwareplatformen er forældet. Antimalware-platformen indlæser det sidst kendte fungerende antimalwareprogram og forsøger at opdatere.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus kunne ikke indlæse antimalwareprogrammet, fordi den aktuelle platformversion ikke understøttes. Microsoft Defender Antivirus vender tilbage til det sidst kendte fungerende program, og der forsøges at opdatere platformen.
<dl>
<dt>Aktuel platformversion: &lt;Aktuel platformversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2006</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Opdateringen af platformen mislykkedes. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus har fundet en fejl under forsøg på at opdatere platformen.
<dl>
<dt>Aktuel platformversion: &lt; Aktuel platformversionFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2007</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_PLATFORM_ALMOSTOUTOFDATE</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Platformen vil snart være forældet. Download den nyeste platform for at opretholde opdateret beskyttelse.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus kræver snart en nyere platformversion for at understøtte fremtidige versioner af antimalwareprogrammet. Download den nyeste Microsoft Defender Antivirus platform for at opretholde det bedste tilgængelige beskyttelsesniveau.
<dl>
<dt>Aktuel platformversion: &lt;Aktuel platformversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2010</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATED </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus brugte <i>Dynamic Signature Service</i> til at hente yderligere signaturer for at beskytte computeren.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionSignature&gt;</dt>
<dt> Type: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Aktuel programversion: &lt; Aktuel programversionDynamisk&gt;</dt>
<dt> signaturtype: &lt;Dynamisk signaturtype&gt;, f.eks.:
<ul>
<li>Version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
<li>Varighed</li>
</ul>
</dt>
<dt>Sti til fastholdelse: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;VersionsnummerDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistens limit type&gt;, for eksempel:
<ul>
<li>VDM-version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
</ul>
</dt>
<dt>Persistens Limit: Fastpath-signaturens grænse for fastholdelse.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2011</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Tjenesten Dynamic Signature slettede de forældede dynamiske definitioner. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus brugte <i>tjenesten Dynamic Signature</i> til at kassere forældede signaturer.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionSignature&gt;</dt>
<dt> Type: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Aktuel programversion: &lt; Aktuel programversionDynamisk&gt;</dt>
<dt> signaturtype: &lt;Dynamisk signaturtype&gt;, f.eks.:
<ul>
<li>Version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
<li>Varighed</li>
</ul>
</dt>
<dt>Sti til fastholdelse: &lt; PathDynamic&gt;</dt> 
<dt>Signaturversion: &lt;VersionsnummerTidsstempel&gt;</dt> for 
<dt>signaturkompilering: &lt;TidsstempelRemoval&gt;</dt> 
<dt>Reason:</dt>
<dt>Persistence Limit Type: &lt;Persistens limit type&gt;, f.eks.:
<ul>
<li>VDM-version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
</ul>
</dt>
<dt>Persistens Limit: Fastpath-signaturens grænse for fastholdelse.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Det er ikke nødvendigt at gøre noget. Den Microsoft Defender Antivirus klient er i en tilstand, der er i orden. Denne hændelse rapporteres, når Dynamic Signature Service sletter forældede dynamiske definitioner.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2012</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_UPDATE_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Der opstod en fejl i antimalwareprogrammet under forsøg på at bruge tjenesten Dynamic Signature. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus stødte på en fejl under forsøg på at bruge <i>tjenesten Dynamic Signature</i>.
<dl>
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionSignature&gt;</dt>
<dt> Type: &lt;Signaturtype&gt;, f.eks.: <ul>
<li>Antivirus</li>
<li>Antispyware</li>
<li>Antimalware</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Aktuel programversion: &lt; Aktuel programversionFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
<dt> Dynamisk signaturtype: &lt;Dynamisk signaturtype&gt;, f.eks.:
<ul>
<li>Version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
<li>Varighed</li>
</ul>
</dt>
<dt>Sti til fastholdelse: &lt; PathDynamic&gt;</dt> 
<dt>Signature Version: &lt;VersionsnummerDynamic&gt;</dt> 
<dt>Signature Compilation Timestamp: &lt;TimestampPersistence&gt;</dt>
<dt> Limit Type: &lt;Persistens limit type&gt;, for eksempel:
<ul>
<li>VDM-version</li>
<li>Tidsstempel</li>
<li>Ingen grænse</li>
</ul>
</dt>
<dt>Persistens Limit: Fastpath-signaturens grænse for fastholdelse.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Kontrollér indstillingerne for internetforbindelsen.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2013</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_SIGNATURE_FASTPATH_DELETED_ALL </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Tjenesten Dynamisk signatur slettede alle dynamiske definitioner. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus kasserede alle signaturer i <i>tjenesten dynamic signaturer</i>.
<dl>
<dt>Aktuel signaturversion: &lt;Aktuel signaturversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2020</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOADED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareprogrammet downloadede en ren fil. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus downloadet en ren fil.
<dl>
<dt>Filnavn: &lt; Filnavn&gt; Navnet på filen.</dt> 
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionAktuel&gt;</dt> 
<dt>programversion: &lt;Aktuel programversion&gt;</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2021</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_CLOUD_CLEAN_RESTORE_FILE_DOWNLOAD_FAILED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareprogrammet kunne ikke hente en ren fil. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus stødte på en fejl under forsøg på at hente en ren fil.
<dl>
<dt>Filnavn: &lt; Filnavn&gt; Navnet på filen.</dt> 
<dt>Aktuel signaturversion: &lt; Aktuel signaturversionAktuel&gt;</dt> 
<dt>programversion: &lt;Aktuel programversionFejlkode&gt;</dt>
<dt>: &lt;Fejlkode&gt; Resultatkode knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Kontrollér indstillingerne for internetforbindelsen.
Den Microsoft Defender Antivirus klient stødte på en fejl, da den dynamiske signaturtjeneste brugte den til at downloade de nyeste definitioner til en bestemt trussel. Denne fejl skyldes sandsynligvis et problem med netværksforbindelsen.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2030</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALLED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareprogrammet blev downloadet og er konfigureret til at køre offline ved næste genstart af systemet.</b>
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
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_OFFLINE_SCAN_INSTALL_FAILED </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus har fundet en fejl under forsøg på at downloade og konfigurere offline antivirus.
<dl>
<dt>Fejlkode: &lt; Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2040</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_OS_EXPIRING </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Understøttelse af antimalware til denne version af operativsystemet ophører snart. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Supporten til operativsystemet udløber om et øjeblik. Kørsel Microsoft Defender Antivirus på et operativsystem, der ikke understøttes, er ikke en tilstrækkelig løsning til at beskytte mod trusler.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2041</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_OS_EOL </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Understøttelse af antimalware til dette operativsystem er ophørt. Du skal opgradere operativsystemet for fortsat support. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Supporten til operativsystemet er udløbet. Kørsel Microsoft Defender Antivirus på et operativsystem, der ikke understøttes, er ikke en tilstrækkelig løsning til at beskytte mod trusler.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 2042</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_PROTECTION_EOL </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Supporten til operativsystemet er udløbet. Microsoft Defender Antivirus understøttes ikke længere på dit operativsystem, er holdt op med at fungere og beskytter ikke mod malwaretrusler.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 3002</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_FAILURE </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Beskyttelse i realtid registrerede en fejl og mislykkedes.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
funktionen Microsoft Defender Antivirus Real-Time Beskyttelse stødte på en fejl og mislykkedes.
<dl>
<dt>Funktion: &lt;Funktion&gt;, f.eks.:
<ul>
<li>VedAdgang</li>
<li>Internet Explorer-downloads og vedhæftede filer i Microsoft Outlook Express</li>
<li>Overvågning af funktionsmåde</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Fejlkode: &lt; Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt> 
<dt>Årsag: Årsagen Microsoft Defender Antivirus realtidsbeskyttelse har genstartet en funktion.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Du skal genstarte systemet og derefter køre en fuld scanning, fordi det er muligt, at systemet ikke var beskyttet i et stykke tid.
Der opstod en fejl i Microsoft Defender Antivirus-klientens funktion til beskyttelse i realtid, fordi en af tjenesterne ikke kunne starte.
Hvis den efterfølges af et 3007-hændelses-id, var fejlen midlertidig, og antimalwareklienten blev gendannet efter fejlen.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 3007</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_RECOVERED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Realtidsbeskyttelse genoprettet efter en fejl. Vi anbefaler, at du kører en fuld systemscanning, når du får vist denne fejl. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus Realtidsbeskyttelse har genstartet en funktion. Det anbefales, at du kører en komplet systemscanning for at registrere elementer, der kan være gået tabt, mens agenten var nede.
<dl>
<dt>Funktion: &lt;Funktion&gt;, f.eks.:
<ul>
<li>VedAdgang</li>
<li>Vedhæftede filer i IE og Outlook Express</li>
<li>Overvågning af funktionsmåde</li>
<li>Netværksinspektionssystem</li>
</ul>
</dt>
<dt>Årsag: Årsagen Microsoft Defender Antivirus realtidsbeskyttelse har genstartet en funktion.</dt>
</dl>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Funktionen til beskyttelse i realtid er genstartet. Hvis denne hændelse sker igen, skal du kontakte <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5000</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_RTP_ENABLED </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus scanning efter malware og anden potentielt uønsket software i realtid blev aktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5001</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_RTP_DISABLED</b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus beskyttelse i realtid scanning efter malware og anden potentielt uønsket software blev deaktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5004</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_RTP_FEATURE_CONFIGURED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Konfigurationen af beskyttelse i realtid blev ændret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus konfigurationen af funktionen til beskyttelse i realtid er ændret.
<dl>
<dt>Funktion: &lt;Funktion&gt;, f.eks.:
<ul>
<li>VedAdgang</li>
<li>Vedhæftede filer i IE og Outlook Express</li>
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
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_CONFIG_CHANGED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Konfigurationen af antimalwareplatformen blev ændret.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus konfiguration er ændret. Hvis dette er en uventet hændelse, skal du gennemse indstillingerne, da dette kan skyldes malware.
<dl>
<dt>Gammel værdi: &lt; Old value number&gt; Old antivirus configuration value.</dt> 
<dt>Ny værdi: &lt; Nyt værdinummer&gt; Ny værdi for antiviruskonfiguration.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5008</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ENGINE_FAILURE</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Antimalwareprogrammet registrerede en fejl og mislykkedes.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus program er blevet afbrudt pga. en uventet fejl.
<dl>
<dt>Fejltype: &lt; Fejltype&gt;, f.eks.: Nedbruds- eller</dt> 
<dt>HangException-kode: &lt;FejlkodeKilde&gt;</dt>
<dt>: &lt;Ressource&gt;</dt>
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
<li>I forbindelse med antimalware, antivirus og spyware skal du skrive <b>net stop msmpsvc</b> ved en kommandoprompt med administratorrettigheder og derefter skrive <b>net start msmpsvc</b> for at genstarte antimalwareprogrammet.</li>
<li>I <i>netværksinspektionssystemet</i> skal du skrive <b>net start nissrv</b> ved en kommandoprompt med administratorrettigheder og derefter skrive <b>net start nissrv</b> for at genstarte <i>programmet Network Inspection System</i> ved hjælp af filen NiSSRV.exe.
</li>
</ul>
</li>
<li>Hvis det mislykkes på samme måde, kan du slå fejlkoden op ved at få adgang til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">Microsoft Support-webstedet</a>  og angive fejlnummeret i <b>søgefeltet</b> og kontakte <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.</li>
</ol>
</td>
</tr>
<tr>
<td>
Brugerhandling:
</td>
<td >
Det Microsoft Defender Antivirus klientprogram stoppede på grund af en uventet fejl.
Sådan foretager du fejlfinding af denne hændelse:
<ol>
<li>Kør scanningen igen.</li>
<li>Hvis det mislykkes på samme måde, skal du gå til <a href="https://go.microsoft.com/fwlink/?LinkId=215163">webstedet Microsoft Support</a> og angive fejlnummeret <b>i søgefeltet</b> for at søge efter fejlkoden.</li>
<li>Kontakt <a href="https://go.microsoft.com/fwlink/?LinkId=215491">Microsoft Teknisk Support</a>.
</li>
</ol>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5009</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_ENABLED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Scanning efter malware og anden potentielt uønsket software er aktiveret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning efter malware og anden potentielt uønsket software er blevet aktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5010</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ANTISPYWARE_DISABLED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Scanning efter malware og anden potentielt uønsket software er deaktiveret.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning efter malware og anden potentielt uønsket software er deaktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5011</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_ENABLED</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Scanning efter virus er aktiveret.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning efter virus er aktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5012</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_ANTIVIRUS_DISABLED </b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Scanning efter virus er deaktiveret. </b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Microsoft Defender Antivirus scanning efter virus er deaktiveret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5013</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>
</b>
</td>
</tr>
<tr>
<td>
Besked:
</td>
<td >
<b>Ændringsbeskyttelse blokerede en ændring af Microsoft Defender Antivirus.</b>
</td>
</tr>
<tr>
<td>
Beskrivelse:
</td>
<td >
Hvis Tamper-beskyttelse er aktiveret, oprettes der et forsøg på at ændre indstillingerne for Defender, hvis de er blokeret, og Hændelses-id 5013, som angiver, at indstillingsændringen blev blokeret.
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5100</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_EXPIRATION_WARNING_STATE </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus har angivet en respitperiode og udløber snart. Efter udløb deaktiverer dette program beskyttelse mod virus, spyware og anden potentielt uønsket software.
<dl>
<dt>Udløbsårsag: Årsagen Microsoft Defender Antivirus udløber.</dt> 
<dt>Udløbsdato: Den dato Microsoft Defender Antivirus udløber.</dt>
</dl>
</td>
</tr>
<tr>
<th colspan="2">Hændelses-id: 5101</th>
</tr>
<tr><td>
Symbolsk navn:
</td>
<td >
<b>MALWAREPROTECTION_DISABLED_EXPIRED_STATE </b>
</td>
</tr>
<tr>
<td>
Besked:
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
Microsoft Defender Antivirus respitperiode er udløbet. Beskyttelse mod virus, spyware og anden potentielt uønsket software er deaktiveret.
<dl>
<dt>Udløbsårsag:</dt>
<dt>Udløbsdato: </dt>
<dt>Fejlkode: &lt;Fejlkode&gt; Resultatkode, der er knyttet til trusselsstatus. STANDARD HRESULT-værdier.</dt> 
<dt>Fejlbeskrivelse: &lt; Fejlbeskrivelse&gt; Beskrivelse af fejlen. </dt>
</dl>
</td>
</tr>
</table>

<a id="error-codes"></a>
##Microsoft Defender Antivirus klientfejlkoder Hvis Microsoft Defender Antivirus oplever problemer, får du normalt en fejlkode, der kan hjælpe dig med at foretage fejlfinding af problemet. Ofte betyder en fejl, at der opstod et problem under installationen af en opdatering.
Dette afsnit indeholder følgende oplysninger om Microsoft Defender Antivirus klientfejl.
- Fejlkoden - Den mulige årsag til fejlen - Råd om, hvad du skal gøre nu

Brug oplysningerne i disse tabeller til at foretage fejlfinding af Microsoft Defender Antivirus fejlkoder.


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
Denne fejl angiver, at du muligvis er løbet tør for hukommelse.
</td>
</tr>
<tr>
<td>Opløsning</td>
<td>
<ol>
<li>Kontrollér den tilgængelige hukommelse på enheden.</li>
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
Denne fejl angiver, at der kan være et problem med dit sikkerhedsprodukt.
</td>
</tr><tr><td>Opløsning</td><td>
<ol>
<li>Opdater definitionerne. Enten:<ol>
<li>Klik på knappen <b>Opdater definitioner</b> under fanen <b>Opdater</b> i Microsoft Defender Antivirus. <img src="images/defender-updatedefs2.png" alt="Update definitions in Microsoft Defender Antivirus"/>Eller
</li>
<li>Download de nyeste definitioner fra <a href="https://aka.ms/wdsi">Microsoft Sikkerhedsviden websted</a>.
Bemærk! Størrelsen på definitionsfilen, der downloades fra webstedet, kan overstige 60 MB og bør ikke bruges som en langsigtet løsning til opdatering af definitioner.
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
Denne fejl angiver, at der kan være en programkonfigurationsfejl. dette er ofte relateret til inputdata, der ikke tillader, at programmet fungerer korrekt.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x805080211
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_QUARANTINE_FAILED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at Microsoft Defender Antivirus ikke kunne sætte en trussel i karantæne.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508022
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_REBOOT_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at der kræves en genstart for at fjerne trusler.
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
Denne fejl angiver, at truslen muligvis ikke længere findes på medierne, eller at malware kan forhindre dig i at scanne din enhed.
</tr><tr><td>Opløsning
</td>
<td>
Kør <a href="https://www.microsoft.com/security/scanner/default.aspx">Microsoft Sikkerhedsscanner</a> opdater derefter sikkerhedssoftwaren, og prøv igen.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508024 </th></tr>
<tr>
<td>Meddelelse</td>
<td><b>ERR_MP_FULL_SCAN_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at en fuld systemscanning kan være påkrævet.
</td></tr>
<tr>
<td>Opløsning</td><td>
Kør en komplet systemscanning.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508025
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_MANUAL_STEPS_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at der kræves manuelle trin for at fjerne trusler.
</td></tr><tr><td>Opløsning</td><td>
Følg de manuelle afhjælpningstrin, der er beskrevet i <a href="https://www.microsoft.com/security/portal/threat/Threats.aspx">Microsoft Malware Protection Encyclopedia</a>. Du kan finde et trusselsspecifikt link i hændelseshistorikken.<br/></td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508026
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_REMOVE_NOT_SUPPORTED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at fjernelse i objektbeholdertypen muligvis ikke understøttes.
</td></tr><tr><td>Opløsning</td><td>
Microsoft Defender Antivirus kan ikke afhjælpe de trusler, der registreres i arkivet. Overvej at fjerne de registrerede ressourcer manuelt.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508027
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERR_MP_REMOVE_LOW_MEDIUM_DISABLED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at fjernelse af lave og mellemstore trusler kan være deaktiveret.
</td></tr><tr><td>Opløsning</td><td>
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
Denne fejl angiver, at en ny scanning af truslen er påkrævet.
</td></tr><tr><td>Opløsning</td><td>
Kør en komplet systemscanning.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508030
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERROR_MP_CALLISTO_REQUIRED </b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at der kræves en offlinescanning.
</td></tr><tr><td>Opløsning</td><td>
Kør offline Microsoft Defender Antivirus. Du kan læse om, hvordan du gør det, i <a href="https://windows.microsoft.com/windows/what-is-windows-defender-offline">artiklen offline Microsoft Defender Antivirus</a>.
</td>
</tr>
<tr>
<th colspan="2">Fejlkode: 0x80508031
</th>
</tr><tr><td>Meddelelse</td>
<td><b>ERROR_MP_PLATFORM_OUTDATED<br/></b>
</td></tr><tr><td>Mulig årsag</td>
<td>
Denne fejl angiver, at Microsoft Defender Antivirus ikke understøtter den aktuelle version af platformen og kræver en ny version af platformen.
</td></tr><tr><td>Opløsning</td><td>
Du kan kun bruge Microsoft Defender Antivirus i Windows 10 og Windows 11. Du kan bruge System Center Endpoint Protection til Windows 8, Windows 7 og <a href="https://www.microsoft.com/server-cloud/system-center/endpoint-protection-2012.aspx">Windows</a> Vista.<br/></td>
</tr>
</table>

<a id="internal-error-codes"></a>Følgende fejlkoder bruges under intern test af Microsoft Defender Antivirus.

Hvis du ser disse fejl, kan du forsøge at [opdatere definitioner](manage-updates-baselines-microsoft-defender-antivirus.md) og gennemtvinge en ny scanning direkte på slutpunktet.


<table>
<tr>
<th colspan="3">Interne fejlkoder</th>
</tr>
<tr>
<th><b>Fejlkode</b></th>
<th>Meddelelsen vises</th>
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
Kontrollér internetforbindelsen, og kør derefter scanningen igen.
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
Dette er en intern fejl. Det kan udløses, når fjernelse af malware ikke lykkes.
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
Dette er en intern fejl. Det kan være udløst, når en scanning ikke kan fuldføres.
</td>
</tr>
</table>

## <a name="related-topics"></a>Relaterede emner

- [Rapport om beskyttelse af Microsoft Defender Antivirus](report-monitor-microsoft-defender-antivirus.md)
- [Microsoft Defender Antivirus i Windows 10](microsoft-defender-antivirus-in-windows-10.md)
