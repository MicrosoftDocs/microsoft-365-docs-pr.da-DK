---
title: Microsoft-administreret skrivebordshandlinger og -overvågning
description: Who gør hvad for forskellige ændringsprocesser
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6b1771660cb25ccd9d23c97d1e3fcf6edd27feaa
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63587658"
---
# <a name="microsoft-managed-desktop-operations-and-monitoring"></a>Microsoft-administreret skrivebordshandlinger og -overvågning

<!-- Operations and monitoring: -->

## <a name="change-management"></a>Administration af ændringer

I servicetilbuddene skifter ansvarsbalancen for vedligeholdelse af hardware og sikkerhedsopdateringer til serviceudbyder (Microsoft) i stedet for kunden (dig). Du skal dog stadig sikre, at ikke-Microsoft og brugerdefineret software fortsat fungerer som forventet, når opdateringerne rulles ud.

For produkter i det lokale miljø påtager din organisation sig alt ansvar for administration af ændringer.

### <a name="balance-of-responsibility"></a>Ansvarsbalance

| Ansvar | Microsoft-administreret skrivebordstjeneste | Microsoft 365 klientsoftware | Klienter og servere i det lokale miljø | Ikke-Microsoft og brugerdefineret software
| ----- | ----- | ----- | ----- | ----- |
| Udnyt nye funktioner | Microsoft | Microsoft | Begge | Kunde
| Test nye funktioner til kvalitetssikring |  Microsoft | Microsoft | Begge | Kunde
| Kommuniker om nye funktioner | Begge | Begge | Begge | Kunde
| Integrer brugerdefineret software | Begge | Begge | Kunde | Kunde
| Anvend sikkerhedsopdateringer | Microsoft | Microsoft | Kunde | Kunde
| Vedligehold systemsoftware | Microsoft | Microsoft | Kunde | Kunde
| Pakke til installation | Microsoft | Microsoft | Kunde | Kunde

### <a name="change-process-overview"></a>Oversigt over ændringsproces

Nedenfor er en oversigt over, hvordan ændringsprocessen deles mellem Microsoft og kunder:

| Scenarie | Microsofts rolle | Kundens rolle |
| ----- | ----- | ----- |
| Før en ændring | <ul><li>Sæt forventninger til tjenesteændringer.</li><li>Giv kunder besked 5 dage forud for ændringer, der kræver handling fra en administrator.</li><li>Ved akutte ændringer skal du foretage en afhjælpning, før du giver besked.</li></ul> | <ul><li>Forstå, hvad du kan forvente for ændringer og kommunikation.</li><li>Læs Microsoft Managed Desktop Message Center regelmæssigt.</li><li>Gennemgå og opdater interne processer for administration af ændringer.</li><li>Forstå og kontrollér overholdelse af krav til Microsoft Managed Desktop. </li><li>Anerkend og godkend, når det er nødvendigt.</li></ul>
| Under en ændring | <ul><li>Udgive og installere månedlige sikkerheds- og ikke-sikkerhedsopdateringer til Windows 10 og Office 365 klienter.</li><li>Overvåg datasignaler og supportkøer for påvirkning.</li></ul> | <ul><li>Se Meddelelsescenter for Microsoft-administreret skrivebord, og gennemse eventuelle yderligere oplysninger.</li><li>Foranstaltninger, der er påkrævet, hvis det er relevant, og testprogrammer.</li><li>Hvis der findes et scenarie med pause/rettelse, kan du oprette en supportanmodning.</li></ul> |
| Efter en ændring | <ul><li>Indsaml kundefeedback for at forbedre rullen af fremtidige ændringer.</li><li>Overvåg datasignaler og supportkøer for påvirkning.</li></ul> | <ul><li>Arbejd sammen med personer i din organisation om at indføre ændringen.</li><li>Gennemgå processer for styring af ændringer og implementering for at se muligheder for at opnå større effektivitet.</li><li>Giv generel feedback og specifik feedback i værktøjet til administratorfeedback.</li><li>Oplær brugerne til at give appspecifik feedback ved Windows Feedback Hub knappen Smil i Office apps.</li></ul> |

### <a name="change-types"></a>Skift typer

Der er flere typer af ændringer, vi regelmæssigt foretager i tjenesten. Kommunikationskanalen for disse ændringer og de handlinger, du er ansvarlig for, varierer.

Ikke alle ændringer har den samme effekt på dine brugere eller kræver handling. Nogle er planlagt, og andre er ikke planlagt. Eksempelvis er ikke-sikkerhedsopdateringer og sikkerhedsopdateringer normalt ikke planlagt.

Afhængigt af typen af ændring kan kommunikationskanalen variere. I følgende tabel vises de typer ændringer, du kan forvente for Microsoft Managed Desktop-tjenesten.

|  | Funktionalitet | Ikke-sikkerhedsrelaterede opdateringer | Sikkerhed |
| ----- | ----- | ----- | ----- |
| **Ændringstype** | <ul><li>Funktionsopdateringer</li><li>Nye funktioner eller programmer</li><li>Forældet funktioner</li></ul> | Klient-hotfixes til problemer | Sikkerhedsopdateringer |
**Varsel på forhånd** | Fem dages varsel for ændringer, der kræver handling | Disse ændringer er ikke inkluderet i den månedlige version | Ingen ændringer er inkluderet i den månedlige version |
**Kommunikationskanal** | <ul><li>Meddelelsescenter</li><li>Mailbesked</li></ul> | <ul><li>Meddelelsescenter</li><li>Mailbesked</li></ul> | <ul><li>Meddelelsescenter</li><li>Mailbesked</li></ul> |
**Kræver handling fra global administrator** | Nogle gange | Sjældent | Sjældent |
**Type af handling** | Skift indstillinger | Kommunikere ændringer til brugerne | Skift administratorindstillinger |
**Kræver test** | Kontrollere forretningsprogrammer, herunder fjernadgangstjenester | Nogle gange: test af rettelsen i forhold til processer eller tilpasninger | Sjældent |
**Eksempler på ændringer** | <ul><li>Funktionsopdateringer: It-administrationsportalen har forenklet indsendelse og gennemgang af supportanmodninger</li><li>Nye funktioner eller programmer: Semi-Annual udgivelse af en Windows 10 funktionsopdatering</li></ul> | Hotfixes baseret på fejl rapporteret af kunden |

## <a name="standard-operating-procedures"></a>Standardoperativsystemer

Microsofts administrerede skrivebordstjeneste implementeres og drives af Microsoft i din Microsoft-skyforekomst, hvor du kan udføre andre administrative aktiviteter. Microsoft er eneansvarlig for microsoft-administreret skrivebordsspecifik konfiguration, konfiguration og handling.

For produkter i det lokale miljø tager din organisation det fulde ansvar for administration af konfiguration og drift.

| Kategorier | Microsoft vil | Kunden vil |
| ----- | ----- | ----- |
| Netværk (proxy, pakkeinspektion, VPN) | Råd og planlæg med kunder for at minimere risikoen for virksomhedsbrugere. | <ul><li>Opret en supportanmodning om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li></ul> |
Tjenestekonti | <ul><li>Implementer, gem og administrer legitimationsoplysningerne på sikker måde.</li><li>Kommuniker uautoriseret adgang eller brug af disse legitimationsoplysninger til dit Sikkerhedsteam.</li></ul> | <ul><li>Opret en supportanmodning om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li><li>Tildel ikke politik, multifaktorgodkendelse, betinget adgang eller programinstallation til Microsoft Managed Desktop Service-konti.</li><li>Nulstil ikke adgangskoden, eller brug legitimationsoplysningerne.</li><li>Åbn en supportanmodning for Sev C til Microsoft Managed Desktop Operations, hvis der observeres mistænkelig aktivitet i Intune- eller Azure-overvågningslogfiler, der er relateret til disse tjenestekonti.</li></ul>
| Enhedsgrupper | <li> Implementer og tildel medlemskabet af enheder i microsoft-administrerede skrivebordsgrupper.</li><li>Brug grupperne for Microsoft-administreret skrivebord til at administrere tildeling og frigivelse af konfiguration og opdateringer til enheder.</li></ul> | <ul><li>Opret en supportanmodning om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li><li>Tildel kun enheder til en Gruppe med Microsoft-administreret skrivebord ved at følge trinnene i [Tildel enheder til en installationsgruppe](../working-with-managed-desktop/assign-deployment-group.md).</li><li>Brug kun grupperne til at tildele virksomhedscertifikater til tjenester som VPN, Windows Hello til virksomheder eller mailkryptering eller konfiguration af virksomhedens Wifi-profil.</li><li>Hvis der findes samtidig administration, skal du eksplicit udelade alle Microsoft Managed Desktop-grupper, når du Konfigurationsstyring klienten.</li></ul>
| Politikker | <ul><li>Implementer og administrer de Microsoft Managed Desktop-politikker, der styrer konfigurationstilstanden for enheder i tjenesten.</li><li> Installér opdateringer, til politik eller Windows trinvist ved hjælp af enhedsgrupper.</li><li>Eksplicit udelade målretning af ikke-Microsoft-administrerede skrivebordsgrupper.</li></ul> | <ul><li>Opret en supportanmodning om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li><li>Ikke redigere eller tildele Microsoft-administrerede politikker for skrivebord til enheder eller brugere, der ikke administreres af Microsoft Managed Desktop-tjenesten.
Microsoft 365 Defender til slutpunkt.</li></ul> | Overvåg og undersøg enheder, som er omfattet af tjenesten Microsoft Managed Desktop. | <ul><li>Opret en supportanmodning om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li></ul>
| Microsoft Store til Virksomheder | Konfigurer og vedligehold autopilotprofilen Windows Microsoft Managed Desktop-tjenesten. | <ul><li>Opret en supportanmodning om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li><li>Rediger ikke konfigurationen af Microsoft Managed Desktop Windows Autopilot-profilen eller tilføj/fjern tildelte enheder.</li></ul>
| Certifikater | | <ul><li>Opret en supportanmodning 60 dage før, at et certifikat udløber, og anmod om oplysninger om en planlagt konfigurationsændring. Inkluder konfigurationsoplysninger, omfang, tidslinje og andre relevante oplysninger, som Microsoft kan gennemgå.</li><li>Anvend kun en ændring, når Microsoft Managed Desktop-handlinger har evalueret og anbefalet.</li><li>Opdater alle certifikater, der kræves for at konfigurere certifikatprofiler, VPN-profiler og Wi-Fi profiler.</li></ul>|

## <a name="device-wipe-with-factory-reset"></a>Sletning af enhed ved nulstilling til fabriksindstillingerne

Microsoft Managed Desktop Operations-teamet kan udføre nulstilling til fabriksindstillingerne for enheder, der er tilmeldt tjenesten, når det er nødvendigt. Nulstilling er nyttigt, hvis du vil give en enhed til en anden medarbejder, eller hvis en medarbejder forlader virksomheden.

Der er nogle få krav:

- Din globale administrator skal sende en supportanmodning.
- Medtag enhedens computernavn i anmodningen.
- Brugerkontoen skal være i Azure AD, før vi nulstiller enheden.

Administrerede skrivebordshandlinger vil:

- Slå enhedsnavnet op i Intune.
- Send kommandoen nulstilling til fabriksindstillingerne på enheden.

> [!NOTE]
> Fjern ikke brugerkontoen fra Azure AD, før enheden nulstilles. Hvis brugeren ikke er i Azure AD, kan Intune ikke sende kommandoen til nulstilling til fabriksindstillingerne til enheden.

Enheden starter i "out of box-oplevelsen", og alle forudinstallerede programmer og indstillinger anvendes igen. Brugeren af enheden skal angive oplysninger om den indledende konfiguration igen.

Når enheden er blevet nulstillet, kan du give den til en anden person i organisationen. Ingen af den forrige brugers data eller virksomhedsdata bliver på enheden. Den næste bruger gennemgår den samme proces, som den forrige person gjorde med en ny Microsoft Managed Desktop-enhed.

BitLocker er en vigtig komponent i datasikkerhed i denne proces. Med BitLocker-kryptering på Microsoft Managed Desktop-enheder forbliver dataene på drevet sikre, selv efter enheden er blevet nulstillet til fabriksindstillingerne. Alle data, der var på drevet, vil ikke være tilgængelige for den næste bruger af enheden. Få mere at vide under [BitLocker-oversigt](/windows/security/information-protection/bitlocker/bitlocker-overview).

Du kan få mere at vide under [Nulstil en enhed fra fabriksindstillingerne](/intune/remote-actions/devices-wipe#factory-reset-a-device).
