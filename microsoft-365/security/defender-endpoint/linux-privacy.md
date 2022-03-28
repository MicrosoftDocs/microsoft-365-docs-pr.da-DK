---
title: Beskyttelse af personlige oplysninger for Microsoft Defender til slutpunkt på Linux
description: Kontrolelementer til beskyttelse af personlige oplysninger, hvordan du konfigurerer politikindstillinger, der påvirker beskyttelse af personlige oplysninger og oplysninger om de diagnostiske data, der indsamles i Microsoft Defender til Slutpunkt på Linux.
keywords: microsoft, defender, Microsoft Defender til Endpoint, linux, privacy, diagnostic
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: d2da0f15b392da9a461c8a2e50e7110610fcc5a2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63597589"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-on-linux"></a>Beskyttelse af personlige oplysninger for Microsoft Defender til slutpunkt på Linux

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft er forpligtet til at give dig de oplysninger og kontrolelementer, du skal bruge for at foretage valg om, hvordan dine data indsamles og bruges, når du bruger Defender til slutpunkt på Linux.

I denne artikel beskrives de kontrolelementer til beskyttelse af personlige oplysninger, der er tilgængelige i produktet, hvordan du administrerer disse kontrolelementer med politikindstillinger, og flere oplysninger om de datahændelser, der indsamles.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-on-linux"></a>Oversigt over kontrolelementer til beskyttelse af personlige oplysninger i Microsoft Defender til slutpunkt på Linux

I dette afsnit beskrives kontrolelementerne til beskyttelse af personlige oplysninger for de forskellige typer data, der indsamles af Defender til Slutpunkt på Linux.

### <a name="diagnostic-data"></a>Diagnosticeringsdata

Diagnostiske data bruges til at holde Defender til Slutpunkt sikker og opdateret, registrere, diagnosticere og løse problemer samt foretage produktforbedringer.

Visse diagnosticeringsdata er påkrævede, mens andre er valgfri. Vi giver dig mulighed for at vælge, om du vil sende obligatoriske eller valgfrie diagnostiske data ved hjælp af kontrolelementer til beskyttelse af personlige oplysninger, f.eks. politikindstillinger for organisationer.

Der er to niveauer af diagnostiske data til Defender til Endpoint-klientsoftware, du kan vælge mellem:

- **Påkrævet**: De minimumsdata, der er nødvendige for at Defender for Endpoint er sikkert, opdateret og fungerer som forventet på den enhed, det er installeret på.
- **Valgfrit**: Andre data, der hjælper Microsoft med at foretage produktforbedringer og indeholder forbedrede oplysninger, der kan hjælpe med at registrere, diagnosticere og afhjælpe problemer.

Som standard sendes kun nødvendige diagnostiske data til Microsoft.

### <a name="cloud-delivered-protection-data"></a>Cloud-leveret beskyttelsesdata

Cloud-leveret beskyttelse bruges til at give øget og hurtigere beskyttelse med adgang til de nyeste beskyttelsesdata i skyen.

Aktivering af den skybaserede beskyttelsestjeneste er valgfri, men det anbefales kraftigt, da den giver vigtig beskyttelse mod malware på dine slutpunkter og på tværs af netværket.

### <a name="sample-data"></a>Eksempeldata

Eksempeldata bruges til at forbedre produktets beskyttelsesfunktioner ved at sende mistænkelige Microsoft-eksempler, så de kan analyseres. Det er valgfrit, om du vil aktivere automatisk indsendelse af eksempler.

Der er tre niveauer til kontrol af prøveindsendelse:

- **Ingen**: Der sendes ingen mistænkelige eksempler til Microsoft.
- **Pengeskab**: Der sendes kun automatisk mistænkelige eksempler, der ikke indeholder personidentificerbare oplysninger (PII). Dette er standardværdien.
- **Alle**: alle mistænkelige eksempler sendes til Microsoft.

## <a name="manage-privacy-controls-with-policy-settings"></a>Administrere kontrolelementer til indstillinger for politik

Hvis du er it-administrator, kan det være en ide at konfigurere disse kontrolelementer på virksomhedsniveau.

Kontrolelementerne til beskyttelse af personlige oplysninger for de forskellige datatyper, der er beskrevet i det foregående afsnit, er beskrevet detaljeret under Angiv indstillinger [for Defender til Slutpunkt på Linux](linux-preferences.md).

Som med alle nye politikindstillinger skal du nøje teste dem i et begrænset, kontrolleret miljø for at sikre, at de indstillinger, du konfigurerer, har den ønskede effekt, før du implementerer politikindstillingerne mere i organisationen.

## <a name="diagnostic-data-events"></a>Diagnostiske datahændelser

I dette afsnit beskrives, hvad der betragtes som nødvendige diagnostiske data, og hvad der betragtes som valgfri diagnostiske data, samt en beskrivelse af de hændelser og felter, der indsamles.

### <a name="data-fields-that-are-common-for-all-events"></a>Datafelter, der er fælles for alle hændelser

Der er nogle oplysninger om hændelser, der er fælles for alle hændelser, uanset kategori eller dataundertype.

Følgende felter betragtes som almindelige for alle begivenheder:

|Felt|Beskrivelse|
|---|---|
|platform|Den generelle klassificering af den platform, hvor appen kører. Dette giver Microsoft mulighed for at identificere, hvilke platforme et problem kan forekomme, så det kan prioriteres korrekt.|
|machine_guid|Entydigt id, der er knyttet til enheden. Gør det muligt for Microsoft at identificere, om problemer påvirker et udvalgt sæt installationer, og hvor mange brugere, der påvirkes.|
|sense_guid|Entydigt id, der er knyttet til enheden. Gør det muligt for Microsoft at identificere, om problemer påvirker et udvalgt sæt installationer, og hvor mange brugere, der påvirkes.|
|org_id|Entydigt id, der er knyttet til den virksomhed, enheden tilhører. Gør det muligt for Microsoft at identificere, om problemer påvirker et udvalgt sæt virksomheder, og hvor mange virksomheder der påvirkes.|
|værtsnavn|Navn på lokal enhed (uden DNS-suffiks). Gør det muligt for Microsoft at identificere, om problemer påvirker et udvalgt sæt installationer, og hvor mange brugere, der påvirkes.|
|product_guid|Entydigt id for produktet. Gør det muligt for Microsoft at skelne mellem problemer, der påvirker forskellige varianter af produktet.|
|app_version|Version af Defender for Endpoint på Linux-programmet. Dette giver Microsoft mulighed for at identificere, hvilke versioner af produktet der viser et problem, så det kan prioriteres korrekt.|
|sig_version|Version af sikkerhedsintelligensdatabase. Gør det muligt for Microsoft at identificere, hvilke versioner af sikkerhedsintelligens der viser et problem, så den kan prioriteres korrekt.|
|supported_compressions|Liste over komprimeringsalgoritmer, der understøttes af programmet, f.eks `['gzip']`. . Gør det muligt for Microsoft at forstå, hvilke typer komprimering der kan bruges, når det kommunikerer med programmet.|
|release_ring|Ring, som enheden er knyttet til (f.eks. Insider Fast, Insider Slow, Production). Dette giver Microsoft mulighed for at identificere, hvilken udgivelsesring der kan opstå et problem, så den kan prioriteres korrekt.|

### <a name="required-diagnostic-data"></a>Obligatoriske diagnosticeringsdata

**Obligatoriske diagnostiske data** er de minimumsdata, der er nødvendige for at defender til Slutpunkt er sikkert, opdateret og fungerer som forventet på den enhed, det er installeret på.

Obligatoriske diagnostiske data hjælper dig med at identificere problemer med Microsoft Defender til slutpunkt, der kan være relateret til en enheds- eller softwarekonfiguration. Den kan f.eks. hjælpe med at afgøre, om en Defender for Endpoint-funktion går ned oftere på en bestemt version af operativsystemet, med nyligt introducerede funktioner, eller når visse Defender for Endpoint-funktioner er deaktiveret. Obligatoriske diagnostiske data hjælper Microsoft med at registrere, diagnosticere og løse disse problemer hurtigere, så påvirkningen af brugere eller organisationer reduceres.

#### <a name="software-setup-and-inventory-data-events"></a>Hændelser tilknyttet data for softwarekonfiguration og lager

**Installation/fjernelse af Microsoft Defender til slutpunkt**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|correlation_id|Entydigt id, der er knyttet til installationen.|
|version|Version af pakken.|
|alvorsgrad|Meddelelsens alvorsgrad (f.eks. Information).|
|kode|Kode, der beskriver handlingen.|
|tekst|Yderligere oplysninger, der er knyttet til produktinstallationen.|

**Konfiguration af Microsoft Defender til slutpunkt**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|antivirus_engine.enable_real_time_protection|Om beskyttelse i realtid er aktiveret på enheden eller ej.|
|antivirus_engine.passive_mode|Om passiv tilstand er aktiveret på enheden eller ej.|
|cloud_service.enabled|Om cloud-leveret beskyttelse er aktiveret på enheden eller ej.|
|cloud_service.timeout|Time out, når programmet kommunikerer med Defender for Endpoint-skyen.|
|cloud_service.heartbeat_interval|Interval mellem fortløbende impulser, der sendes af produktet til skyen.|
|cloud_service.service_uri|URI'en, der bruges til at kommunikere med skyen.|
|cloud_service.diagnostic_level|Enhedens diagnosticeringsniveau (obligatorisk, valgfrit).|
|cloud_service.automatic_sample_submission|Automatisk prøveindsendelsesniveau for enheden (ingen, sikker, alle).|
|cloud_service.automatic_definition_update_enabled|Om automatisk opdatering af definition er slået til eller ej.|
|edr.early_preview|Om enheden skal køre Slutpunktsregistrering og -svar tidlige visningsfunktioner.|
|edr.group_id|Gruppeidentifikator, der bruges af registrerings- og svarkomponenten.|
|edr.tags|Brugerdefinerede mærker.|
|funktioner.\[ valgfri funktionsnavn\]|Liste over visningsfunktioner, samt om de er aktiveret eller ej.|

#### <a name="product-and-service-usage-data-events"></a>Datahændelser i forbindelse med brug af produkter og tjenester

**Sikkerhedsintelligens-opdateringsrapport**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|from_version|Den oprindelige sikkerhedsintelligens-version.|
|to_version|Ny sikkerhedsintelligens-version.|
|status|Status for den opdatering, der angiver succes eller fejl.|
|using_proxy|Om opdateringen blev udført over en proxy.|
|fejl|Fejlkode, hvis opdateringen mislykkedes.|
|Årsag|Fejlmeddelelse, hvis opdateringen mislykkedes.|

#### <a name="product-and-service-performance-data-events-for-required-diagnostic-data"></a>Datahændelser for produkt- og tjenesteydeevne for nødvendige diagnostiske data

**Statistik for kerneludvidelse**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|version|Version af Defender til slutpunkt på Linux.|
|instance_id|Entydigt id, der genereres ved start af kerneudvidelse.|
|trace_level|Sporingsniveau for kerneudvidelsen.|
|undersystem|Det underliggende undersystem, der bruges til beskyttelse i realtid.|
|ipc.connects|Antal forbindelsesanmodninger, der er modtaget af kerneudvidelsen.|
|ipc.rejects|Antal forbindelsesanmodninger, der er afvist af kerneudvidelsen.|
|ipc.connected|Om der er en aktiv forbindelse til kerneudvidelsen.|

#### <a name="support-data"></a>Supportdata

**Diagnostiske logfiler**:

Diagnostiske logfiler indsamles kun med samtykke fra brugeren som en del af funktionen til indsendelse af feedback. Følgende filer indsamles som en del af supportlogfilerne:

- Alle filer under */var/log/microsoft/mdatp*
- Undersæt af filer under */etc/opt/microsoft/mdatp* , der er oprettet og bruges af Defender til Slutpunkt på Linux
- Produktinstallation og fjernelse af installationslogfiler under */var/log/microsoft_mdatp_\*.log*

### <a name="optional-diagnostic-data"></a>Valgfrie diagnostiske data

**Valgfrie diagnostiske data** er yderligere data, der hjælper Microsoft med at foretage produktforbedringer og indeholder forbedrede oplysninger, der kan hjælpe med at registrere, diagnosticere og løse problemer.

Hvis du vælger at sende os valgfri diagnosticeringdata, er de påkrævede diagnosticeringsdata også inkluderet.

Eksempler på valgfri diagnostiske data omfatter data, som Microsoft indsamler om produktkonfiguration (f.eks. antal udeladelsesindstillinger på enheden) og produktydeevne (aggregerede målinger for ydeevnen for komponenterne i produktet).

#### <a name="software-setup-and-inventory-data-events-for-optional-diagnostic-data"></a>Hændelser i forbindelse med softwarekonfiguration og lagerdata til valgfrie diagnostiske data

**Konfiguration af Microsoft Defender til slutpunkt**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|connection_retry_timeout|Forbindelsen får time out igen, når du kommunikerer med skyen.|
|file_hash_cache_maximum|Størrelse på produktcachen.|
|crash_upload_daily_limit|Begrænsning af nedbrudslogfiler, der er uploadet dagligt.|
|antivirus_engine.exclusions[].is_directory|Uanset om udelukkelsen fra scanning er en mappe eller ej.|
|antivirus_engine.exclusions[].sti|Sti, der blev udelukket fra scanning.|
|antivirus_engine.exclusions[].udvidelse|Udvidelse er udeladt fra scanning.|
|antivirus_engine.exclusions[].name|Navnet på den fil, der ikke blev scannet.|
|antivirus_engine.scan_cache_maximum|Størrelse på produktcachen.|
|antivirus_engine.maximum_scan_threads|Maksimale antal tråde, der bruges til scanning.|
|antivirus_engine.threat_restoration_exclusion_time|Time out, før en fil, der er gendannet fra karantæne, kan findes igen.|
|antivirus_engine.threat_type_settings|Konfiguration af, hvordan forskellige trusselstyper håndteres af produktet.|
|filesystem_scanner.full_scan_directory|Komplet scanningsmappe.|
|filesystem_scanner.quick_scan_directories|Liste over mapper, der bruges i Hurtig scanning.|
|edr.latency_mode|Ventetidstilstand, der bruges af registrerings- og svarkomponenten.|
|edr.proxy_address|Proxyadresse, der bruges af registrerings- og svarkomponenten.|

**Microsoft Automatisk opdateringskonfiguration**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|how_to_check|Bestemmer, hvordan produktopdateringer kontrolleres (f.eks. automatisk eller manuel).|
|channel_name|Opdater kanal, der er knyttet til enheden.|
|manifest_server|Server, der bruges til at hente opdateringer.|
|update_cache|Placeringen af cachen, der bruges til at gemme opdateringer.|

### <a name="product-and-service-usage"></a>Brug af produkter og tjenester

#### <a name="diagnostic-log-upload-started-report"></a>Rapport over overførsel af diagnosticeringslogfil startet

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|sha256|SHA256-id for supportloggen.|
|størrelse|Supportloggens størrelse.|
|original_path|Stien til supportloggen (altid under */var/opt/microsoft/mdatp/wdavdiag/*).|
|format|Supportloggens format.|

#### <a name="diagnostic-log-upload-completed-report"></a>Rapport over overførsel af diagnosticeringslogfil fuldført

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|request_id|Korrelations-id for anmodning om overførsel af supportlogfil.|
|sha256|SHA256-id for supportloggen.|
|blob_sas_uri|URI'en, der bruges af programmet til at overføre supportloggen.|

#### <a name="product-and-service-performance-data-events-for-product-service-and-usage"></a>Datahændelser for produkt- og tjenesteydeevne for produkttjeneste og -brug

**Uventet programafslutning (nedbrud)**:

Uventede programafslutninger samt programmets tilstand, når det sker.

**Statistik for kerneludvidelse**:

Følgende felter indsamles:

|Felt|Beskrivelse|
|---|---|
|pkt_ack_timeout|Følgende egenskaber er sammenlagte numeriske værdier, der repræsenterer antallet af hændelser, der er sket siden start af kerneudvidelse.|
|pkt_ack_conn_timeout||
|ipc.ack_pkts||
|ipc.nack_pkts||
|ipc.send.ack_no_conn||
|ipc.send.nack_no_conn||
|ipc.send.ack_no_qsq||
|ipc.send.nack_no_qsq||
|ipc.ack.no_space||
|ipc.ack.timeout||
|ipc.ack.ackd_fast||
|ipc.ack.ackd||
|ipc.recv.bad_pkt_len||
|ipc.recv.bad_reply_len||
|ipc.recv.no_waiter||
|ipc.recv.copy_failed||
|ipc.th.vnode.mask||
|ipc.virtuelth.vnode.read||
|ipc.virtuelth.vnode.write||
|ipc.exeth.vnode.exec||
|ipc.syndth.vnode.del||
|ipc.kauth.vnode.read_attr||
|ipc.kauth.vnode.write_attr||
|ipc.kauth.vnode.read_ex_attr||
|ipc.kauth.vnode.write_ex_attr||
|ipc.kauth.vnode.read_sec||
|ipc.kauth.vnode.write_sec||
|ipc.kauth.vnode.take_own||
|ipc.kauth.vnode.link||
|ipc.denth.vnode.create||
|ipc.vuth.vnode.move||
|ipc.virtuelth.vnode.mount||
|ipc.virtuelth.vnode.denied||
|ipc.kauth.vnode.ackd_before_deadline||
|ipc.kauth.vnode.missed_deadline||
|ipc.kauth.file_op.mask||
|ipc.kauth_file_op.open||
|ipc.kauth.file_op.close||
|ipc.kauth.file_op.close_modified||
|ipc.kauth.file_op.move||
|ipc.kauth.file_op.link||
|ipc.kauth.file_op.exec||
|ipc.kauth.file_op.remove||
|ipc.kauth.file_op.unmount||
|ipc.kauth.file_op.fork||
|ipc.kauth.file_op.create||

## <a name="resources"></a>Ressourcer

- [Beskyttelse af personlige oplysninger hos Microsoft](https://privacy.microsoft.com/)
