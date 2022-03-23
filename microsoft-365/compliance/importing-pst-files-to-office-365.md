---
title: Få mere at vide om at importere din organisations PST-filer
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.IngestionHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: ba688e0a-0fcb-4bd7-8e57-2b669564ea84
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Lær at bruge importtjenesten i Microsoft 365 Overholdelsescenter til masseimport af maildata (PST-filer) til brugerpostkasser.
ms.openlocfilehash: b88cd9f6b12f382f8fdeb696af32c1fd95ad805d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63587292"
---
# <a name="learn-about-importing-your-organizations-pst-files"></a>Få mere at vide om at importere din organisations PST-filer

> [!NOTE]
> Denne artikel gælder for administratorer. Forsøger du at importere PST-filer til din egen postkasse? Se [Importér mail, kontakter og kalender fra en Outlook .pst-fil](https://go.microsoft.com/fwlink/p/?LinkID=785075).

Du kan bruge importtjenesten i Microsoft 365 Overholdelsescenter til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank"></a> hurtigt at importere PST-filer til Exchange Online postkasser i organisationen. Der er to måder, hvorpå du kan importere PST-filer Microsoft 365:

- **Netværksupload** ![ Upload fra skyen.](../media/54ab16ee-3822-4551-abef-3d926f4e1c01.png) - Upload PST-filerne via netværket til en midlertidig Azure Storage placering i Microsoft-skyen. Derefter skal du bruge Microsoft 365 Import til at importere PST-data til postkasser i organisationen.

- **Drevforsendelse** ![ Harddisk.](../media/e72b76f3-1f73-4296-b749-c325d95d9ef6.png) - Kopiér PST-filerne til en BitLocker-krypteret harddisk, og send derefter drevet fysisk til Microsoft. Når Microsoft modtager harddisken, uploader datacentermedarbejderen dataene til en midlertidig Azure Storage placering i Microsoft-skyen. Derefter skal du bruge Microsoft 365 Importér til at importere dataene til postkasser i organisationen.

## <a name="step-by-step-instructions"></a>Trinvis vejledning

Se et af følgende emner for at få en detaljeret, trinvis vejledning til masseimport af din organisations PST-filer for at Microsoft 365.

- [Brug netværksupload til at importere PST-filer til Microsoft 365](use-network-upload-to-import-pst-files.md)

- [Brug drevforsendelse til at importere PST-filer](use-drive-shipping-to-import-pst-files-to-office-365.md)

## <a name="how-importing-pst-files-works"></a>Sådan fungerer import af PST-filer

Her er en illustration og beskrivelse af den komplette PST-importproces. Illustrationen viser den primære arbejdsproces og fremhæver forskellene mellem overførsels- og drevforsendelsesmetoderne på netværket.

![Arbejdsproces for PST-importproces.](../media/76997b69-67d7-433a-a0ca-9389f85a36a1.png)

1. **Download PST-importværktøjerne** og -nøglen til privat Azure Storage placering – Det første trin er at downloade værktøjet og adgangsnøglen, der bruges til at uploade PST-filerne eller kopiere dem til en harddisk. Du får disse fra **siden Import** i Microsoft 365 Overholdelsescenter. Nøglen giver dig (eller en microsoft-datacentermedarbejder i forbindelse med drevforsendelse) de nødvendige tilladelser til at uploade PST-filer til en privat og sikker placering, Azure Storage placering. Denne adgangsnøgle er unik for din organisation og hjælper med at forhindre uautoriseret adgang til dine PST-filer, når de er uploadet til Microsoft Cloud. Hvis du importerer PST-Microsoft 365 til en konto, kræver det ikke, at din organisation har et separat Azure-abonnement.

2. **Upload eller kopiere PST-filerne** – Næste trin afhænger af, om du bruger netværksupload eller drevforsendelse til at importere PST-filer. I begge tilfælde skal du bruge værktøjet og den sikre lagernøgle, du fik i forrige trin.

    - **Netværksoverførsel:** Værktøjet AzCopy.exe (downloadet i trin 1) bruges til at uploade og gemme dine PST-filer på en placering Azure Storage i Microsoft-skyen. Den Azure Storage, du overfører dine PST-filer til, er placeret i det samme regionale Microsoft-datacenter som din organisation.

      Hvis du vil overføre dem, skal de PST-filer, du vil importere, være placeret i et filshare eller en filserver i organisationen.

    - **Drevforsendelse:** Værktøjet WAImportExport.exe (downloadet i trin 1) bruges til at kopiere dine PST-filer til harddisken. Dette værktøj krypterer harddisken med BitLocker og kopierer derefter PST'erne til harddisken. Ligesom netværksupload skal de PST-filer, du vil kopiere til harddisken, være placeret i et filshare eller en filserver i organisationen.

3.  Opret en PST-importtilknytningsfil – Når PST-filerne er blevet uploadet til placeringen i Azure Storage eller kopieret til en harddisk, er næste trin at oprette en kommasepareret fil (CSV), der angiver, hvilke brugerpostkasser PST-filerne importeres til (og en PST-fil kan importeres til en brugers primære postkasse eller brugerens arkivpostkasse). [Download en kopi af PST-importtilknytningsfilen](https://go.microsoft.com/fwlink/p/?LinkId=544717). Tjenesten Microsoft 365 import bruger oplysningerne til at importere PST-filerne.

4. **Opret et PST-importjob** – Næste trin er at oprette et PST-importjob på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter og sende den PST-importtilknytningsfil, der blev oprettet i det forrige trin. Til netværksupload (fordi PST-filer er blevet uploadet til Azure) analyserer Microsoft 365 dataene i PST-filerne og giver dig derefter mulighed for at angive filtre, der styrer, hvilke data der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen.

    For drevforsendelse sker der et par andre ting på nuværende tidspunkt i processen.

    - Du sender fysisk harddisken til et Microsoft-datacenter (leveringsadressen for Microsoft-datacenteret vises, når importjobbet oprettes).

    - Når Microsoft modtager harddisken, vil datacentermedarbejderen overføre PST-filerne på harddisken til den Azure Storage placering for organisationen. Som beskrevet tidligere uploades dine PST-filer til Azure Storage placering, der er placeret i det samme regionale Microsoft-datacenter, hvor din organisation er placeret.

      > [!NOTE]
      > PST-filerne på harddisken uploades til Azure inden for 7 til 10 arbejdsdage, efter Microsoft modtager harddisken.

      Ligesom netværksuploadprocessen analyserer Microsoft 365 derefter dataene i PST-filerne og giver dig mulighed for at indstille filtre, der styrer, hvilke data der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen.

    - Microsoft sender harddisken tilbage til dig.

5. Filtrer **de PST-data**, der skal importeres til postkasser – Når importjobbet er oprettet (og efter PST-filer fra et drevforsendelsesjob er uploadet til Azure Storage-placeringen) analyserer Microsoft 365 dataene i PST-filerne (sikkert og sikkert) ved at identificere alderen på elementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er færdig, og dataene er klar til at blive importeret, har du mulighed for at importere alle de data, der er indeholdt i PST-filerne, eller du kan trimme de importerede data ved at angive filtre, der styrer, hvilke data der importeres.

6. **Start PST-importjobbet** – Når importjobbet er startet, bruger Microsoft 365 oplysningerne i PST-importtilknytningsfilen til at importere PST-filerne fra Azure Storage-placeringen til brugerpostkasserne. Statusoplysninger om importjobbet (herunder oplysninger om hver PST-fil, der importeres) vises på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter. Når importjobbet er afsluttet, angives jobstatus til **Fuldført**.

## <a name="why-import-email-data-to-microsoft-365"></a>Hvorfor importere maildata til Microsoft 365?

- Det er en god metode til at importere organisationens arkiveringsdata for at Microsoft 365.

- Du kan bruge funktionen [Intelligent import til](filter-data-when-importing-pst-files.md) at filtrere elementer i PST-filer, der faktisk importeres til målpostkasserne. Dette gør det muligt at trimme de importerede data ved at angive filtre, der styrer, hvilke data der importeres.

- Import af maildata til en Microsoft 365 hjælper med at imødekomme organisationens behov for overholdelse ved at lade dig:

  - [Aktivér arkivpostkasser](enable-archive-mailboxes.md) [og automatisk udvidende arkivering for](autoexpanding-archiving.md) at give brugerne yderligere lagerplads til postkassen.

  - Placer postkasser i [retslig tilbageholdelse for](./create-a-litigation-hold.md) at bevare indhold.

  - Brug værktøjet [Indholdssøgning til](content-search.md) at søge efter postkasseindhold.

  - Brug [eDiscovery-sager](./get-started-core-ediscovery.md) til at administrere din organisations juridiske undersøgelser

  - Brug [opbevaringspolitikker](retention.md) i Microsoft 365 Overholdelsescenter til at styre, hvor lang tid postkasseindhold opbevares, og slet derefter indhold, når en opbevaringsperiode udløber.

  - Brug [Politikker for overholdelse af regler og standarder i](communication-compliance.md) kommunikation til at undersøge meddelelser for at sikre, at de overholder meddelelsesstandarder, og tilføj en klassificeringstype.

- Import af data til Microsoft 365 hjælper med at beskytte dig mod tab af data. Maildata, der importeres til Microsoft 365 nedarver funktionerne til høj tilgængelighed i Exchange Online.

- Maildata er tilgængelige for brugere fra alle enheder, fordi de er gemt i skyen.

## <a name="importing-sharepoint-data-to-microsoft-365"></a>Importere SharePoint data til Microsoft 365

Du kan også importere filer og dokumenter SharePoint websteder og OneDrive konti i organisationen. Du kan finde flere oplysninger i følgende artikler:

- [Overfør til SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)

- [Introduktion til SharePoint overflytningsværktøj](/sharepointmigration/introducing-the-sharepoint-migration-tool)

- [Overfør til SharePoint Online ved hjælp af PowerShell](/sharepointmigration/overview-spmt-ps-cmdlets)

- [Overfør fildelingsindhold til SharePoint Online ved hjælp af Azure-datafeltet](/sharepointmigration/how-to-migrate-file-share-content-to-spo-using-azuredatabox)

## <a name="frequently-asked-questions-about-importing-pst-files"></a>Ofte stillede spørgsmål om import af PST-filer

Her er nogle ofte stillede spørgsmål om brugen Microsoft 365 importtjenesten til masseimport af PST-filer Microsoft 365 postkasser.

- [Brug af netværksupload til at importere PST-filer](#using-network-upload-to-import-pst-files)

- [Brug af drevforsendelse til at importere PST-filer](#using-drive-shipping-to-import-pst-files)

### <a name="using-network-upload-to-import-pst-files"></a>Brug af netværksupload til at importere PST-filer

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-network-upload"></a>Hvilke tilladelser kræves der for at oprette importjob i den Microsoft 365 importtjeneste ved hjælp af netværksoverførsel?

Du skal have tildelt rollen Postkasse Import Eksport i Exchange Online for at importere PST-filer til Microsoft 365 postkasser. Som standard er denne rolle ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Postkasse Import Eksport til rollegruppen Organisationsadministration. Eller du kan oprette en ny rollegruppe, tildele rollen Postkasse Import Eksport og derefter tilføje dig selv eller andre brugere som medlem. Du kan finde flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i Administrer [rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

Og hvis du vil oprette importjob i Microsoft 365 Overholdelsescenter, skal et af følgende være sandt:

- Du skal have tildelt rollen Postmodtagere i Exchange Online. Som standard er denne rolle tildelt rollegrupperne Organisationsadministration og Modtageradministration.

    Eller

- Du skal være global administrator i organisationen.

> [!TIP]
> Overvej at oprette en ny rollegruppe Exchange Online, der specifikt er beregnet til import af PST-filer til Microsoft 365. For det mindste niveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Postkasse Import Eksport og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.

#### <a name="where-is-network-upload-available"></a>Hvor er netværksupload tilgængelig?

Netværksoverførsel er i øjeblikket tilgængelig i disse områder: USA, Canada, Brasilien, Storbritannien, Frankrig, Schweiz, Norge, Europa, Indien, Østasien, Sydøstasien, Japan, Republikken Korea, Australien og De Forenede Arabiske Emirater (UAE). Netværksoverførsel vil være tilgængelig i flere områder i fremtiden.

#### <a name="what-is-the-pricing-for-importing-pst-files-by-using-network-upload"></a>Hvad er prisen for at importere PST-filer ved hjælp af netværksoverførsel?

Det er gratis at bruge netværksupload til at importere PST-filer.

Det betyder også, at når PST-filer er blevet slettet fra Azure Storage-området, vises de ikke længere på listen over filer i et færdiggjort importjob [i Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339). Selvom et importjob muligvis stadig er anført på listen på siden **Importér data Microsoft 365**, kan listen over PST-filer være tom, når du får vist detaljerne for ældre importjobs.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Hvilken version af PST-filformatet understøttes til import til Microsoft 365?

Der findes to versioner af PST-filformatet: ANSI og Unicode. Vi anbefaler, at du importerer filer, der bruger Unicode PST-filformatet. Men filer, der bruger ANSI PST-filformatet, f.eks. filer til sprog, der bruger dobbelt-byte tegnsæt (DBCS), kan også importeres Microsoft 365. Du kan finde flere oplysninger om import af ANSI PST-filer i trin 4 i Brug netværksupload til at importere [PST-filer Microsoft 365](./use-network-upload-to-import-pst-files.md).

Desuden kan PST-filer fra Outlook 2007 og nyere versioner importeres til Microsoft 365.

#### <a name="after-i-upload-my-pst-files-to-the-azure-storage-area-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Når jeg har uploadet mine PST-filer til Azure Storage, hvor længe opbevares de så i Azure, før de slettes?

Når du bruger netværksuploadmetoden til at importere PST-filer, uploader du dem til en Azure Blob-beholder med navnet `ingestiondata`. Hvis der ikke er nogen importjob i gang på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter), slettes alle PST-filer `ingestiondata` i beholderen i Azure 30 dage efter, det seneste importjob blev oprettet i Microsoft 365 Overholdelsescenter. Det betyder også, at du skal oprette et nyt importjob i Microsoft 365 Overholdelsescenter (beskrevet i trin 5 i vejledningen til netværksupload) inden for 30 dage efter PST-filer er uploadet til Azure.

Det betyder også, at når PST-filer er blevet slettet fra Azure Storage-området, vises de ikke længere på listen over filer i et færdiggjort importjob i Microsoft 365 Overholdelsescenter. Selvom et importjob muligvis stadig er anført på listen på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter, kan listen over PST-filer være tom, når du får vist detaljerne for ældre importjobs.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-network-upload"></a>Hvor lang tid tager det at importere en PST-fil til en postkasse ved hjælp af netværksupload?

Det afhænger af dit netværks kapacitet, men det tager typisk adskillige timer for hver terabyte (TB) af data, der skal uploades til Azure Storage-området for organisationen. Når PST-filerne er blevet kopieret til Azure Storage-området, importeres en PST-fil til en Microsoft 365-postkasse i en hastighed på ca. 24 GB pr. dag<sup>\*</sup>. Hvis denne hastighed ikke opfylder dine behov, kan du overveje at bruge andre metoder til at hente maildata Microsoft 365. Du kan få mere at vide [under Sådan kan du overføre flere mailkonti Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Hvis forskellige PST-filer importeres til forskellige målpostkasser, foregår importen parallelt; Med andre ord importeres hvert PST-/postkassepar samtidigt. Hvis flere PST-filer importeres til den samme postkasse, importeres de sekventielt (én ad gangen), ikke samtidigt.

> [!NOTE]
> <sup>\*</sup> Denne sats er ikke garanteret. Serverens arbejdsbelastning og midlertidige problemer med ydeevnen kan reducere denne hastighed.

#### <a name="how-does-the-pst-import-process-handle-duplicate-email-items"></a>Hvordan håndterer PST-importprocessen duplikerede mailelementer?

PST-importprocessen søger efter dublerede elementer og kopierer ikke elementerne fra en PST-fil til postkassen eller arkivet, hvis der findes et tilsvarende element i destinationsmappen i målpostkassen eller destinationsarkivet. Hvis du importerer den samme PST-fil igen og angiver en anden destinationsmappe (ved hjælp af egenskaben TargetRootFolder i PST-importtilknytningsfilen) end den, du angav i et tidligere importjob, importeres alle elementer i PST-filen igen.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-network-upload"></a>Er der en størrelsesgrænse for meddelelser, når du importerer PST-filer ved hjælp af netværksoverførsel?

Ja. Hvis en PST-fil indeholder et postkasseelement, der er større end 150 MB, ignoreres elementet og importeres ikke under importen. Elementer, der er større end 150 MB importeres ikke, fordi 150 MB er meddelelsens størrelsesgrænse i Exchange Online. Du kan finde flere oplysninger [i Meddelelsesgrænser i Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-network-upload"></a>Bevares meddelelsesegenskaber som f.eks., hvornår meddelelsen blev sendt eller modtaget, listen over modtagere og andre egenskaber, når PST-filer importeres til en Microsoft 365-postkasse ved hjælp af netværksupload?

Ja. De oprindelige meddelelsesmetadata ændres ikke under importen.

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-network-upload"></a>Er der en grænse for antallet af niveauer i et mappehierarki for en PST-fil, som jeg vil importere til en postkasse ved hjælp af netværksupload?

Ja. Du kan ikke importere en PST-fil med 300 eller flere niveauer af indlejrede mapper.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Kan jeg bruge netværksupload til at importere PST-filer til en inaktiv postkasse i Microsoft 365?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Kan jeg bruge netværksupload til at importere PST-filer til et onlinearkivs postkasse i Exchange en hybridinstallation?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-public-folders-in-exchange-online"></a>Kan jeg bruge netværksupload til at importere PST-filer til offentlige mapper i Exchange Online?

Nej, du kan ikke importere PST-filer til offentlige mapper.

### <a name="using-drive-shipping-to-import-pst-files"></a>Brug af drevforsendelse til at importere PST-filer

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-drive-shipping"></a>Hvilke tilladelser kræves der for at oprette importjob i Microsoft 365 importtjenesten ved hjælp af drevforsendelse?

Du skal have tildelt rollen Postkasse Import Eksport for at importere PST-filer til Microsoft 365 postkasser. Som standard er denne rolle ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Postkasse Import Eksport til rollegruppen Organisationsadministration. Eller du kan oprette en ny rollegruppe, tildele rollen Postkasse Import Eksport og derefter tilføje dig selv eller andre brugere som medlem. Du kan finde flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i Administrer [rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

Og hvis du vil oprette importjob i Microsoft 365 Overholdelsescenter, skal et af følgende være sandt:

- Du skal have tildelt rollen Postmodtagere i Exchange Online. Som standard er denne rolle tildelt rollegrupperne Organisationsadministration og Modtageradministration.

    Eller

- Du skal være global administrator i organisationen.

> [!TIP]
> Overvej at oprette en ny rollegruppe Exchange Online, der specifikt er beregnet til import af PST-filer til Microsoft 365. For det mindste niveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Postkasse Import Eksport og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.

#### <a name="where-is-drive-shipping-available"></a>Hvor er drevforsendelse tilgængelig?

Drevforsendelse er i øjeblikket tilgængelig i USA, Canada, Brasilien, Storbritannien, Europa, Indien, Østasien, Sydøstasien, Japan, Republikken Korea og Australien. Drevforsendelse vil være tilgængelig i flere områder i fremtiden.

> [!NOTE]
> På nuværende tidspunkt er drevforsendelse til import af PST-filer ikke tilgængelig i Tyskland og Schweiz. Disse ofte stillede spørgsmål opdateres, når drevforsendelse er tilgængelig i disse lande/områder.

#### <a name="what-commercial-licensing-agreements-support-drive-shipping"></a>Hvilke kommercielle licensaftaler understøtter drevforsendelse?

Drevforsendelse til import af PST-filer til Microsoft 365 fås via en Microsoft Enterprise Agreement (EA). Drevforsendelse fås ikke gennem en Aftale om Microsoft-produkter og -tjenester (MPSA).

#### <a name="what-is-the-pricing-for-using-drive-shipping-to-import-pst-files-to-microsoft-365"></a>Hvad er prisen for at bruge drevforsendelse til at importere PST-filer til Microsoft 365?

Omkostningerne til at bruge drevforsendelse til at importere PST-filer Microsoft 365 postkasser er USD 2 USD pr. GB data. Hvis du f.eks. sender en harddisk, der indeholder 1.000 GB (1 TB) PST-filer, koster det 2.000 USD. Du kan arbejde sammen med en partner om at betale importgebyret. Hvis du vil have mere at vide om at finde en partner, [skal du se Find din Microsoft-partner eller -forhandler](../admin/manage/find-your-partner-or-reseller.md).

#### <a name="what-kind-of-hard-drives-are-supported-for-drive-shipping"></a>Hvilke typer harddiske understøttes til drevforsendelse?

Kun 2,5 tommer Solid State Drives (SSDs) eller 2,5 tommer eller 3,5 tommer SATA II/III-interne harddiske er understøttet til brug sammen med Microsoft 365-importtjenesten. Du kan bruge harddiske op til 10 TB. I forbindelse med importjob vil kun den første datamængde på harddisken blive behandlet. Datamængden skal være formateret med NTFS. Når du kopierer data til en harddisk, kan du tilslutte den direkte ved hjælp af en 2,5 tommer SSD- eller 2,5 tommer eller 3,5 tommer SATA II/III-forbindelse, eller du kan tilslutte den eksternt ved hjælp af en ekstern 2,5 tommer SSD eller 2,5 tommer eller 3,5 tommer SATA II/III USB-adapter.

> [!IMPORTANT]
> Eksterne harddiske, der indeholder en indbygget USB-adapter, understøttes ikke af Microsoft 365 Import. Derudover kan disken i kassen på en ekstern harddisk ikke bruges. Send ikke eksterne harddiske.

#### <a name="how-many-hard-drives-can-i-ship-for-a-single-import-job"></a>Hvor mange harddiske kan jeg sende til et enkelt importjob?

Du kan sende maksimalt 10 harddiske til et enkelt importjob.

#### <a name="after-i-ship-my-hard-drive-how-long-does-it-take-to-get-to-the-microsoft-datacenter"></a>Når jeg sender min harddisk, hvor lang tid tager det så at få adgang til Microsoft-datacenteret?

Det afhænger af et par ting, f.eks. hvor tæt du er på datacenteret i Microsoft, og hvilken type forsendelse du har valgt at benytte til at sende harddisken (f.eks. levering næste dag, to dages-levering eller grundlæggende levering). Hos de fleste spedder kan du bruge sporingsnummeret til at spore din forsendelses status.

#### <a name="after-my-hard-drive-arrives-at-the-microsoft-datacenter-how-long-does-it-take-to-upload-my-pst-files-to-azure"></a>Når min harddisk er ankommet til Microsoft-datacenteret, hvor lang tid tager det så at uploade mine PST-filer til Azure?

Når Microsoft-datacenteret modtager din harddisk, tager det mellem 7 til 10 arbejdsdage at overføre PST-filerne til Azure Storage placering for din organisation. PST-filerne uploades til en Azure Blob-beholder med navnet `ingestiondata`.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-drive-shipping"></a>Hvor lang tid tager det at importere en PST-fil til en postkasse ved hjælp af drevforsendelse?

Når PST-filerne er uploadet til Azure Storage-området, analyserer Microsoft 365 dataene i PST-filerne (på en sikker måde) for at identificere alderen på elementerne og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når denne analyse er fuldført, har du mulighed for at importere alle dataene i PST-filerne eller indstille filtre til at styre, hvilke data der importeres. Når du starter importjobbet, importeres en PST-fil til en Microsoft 365 til en hastighed på ca. 24 GB pr. dag.<sup>\*</sup> Hvis denne hastighed ikke opfylder dine behov, kan du overveje at bruge andre metoder til at hente maildata Microsoft 365. Du kan få mere at vide [under Sådan kan du overføre flere mailkonti Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Hvis forskellige PST-filer importeres til forskellige målpostkasser, foregår importen parallelt; Med andre ord importeres hvert PST-/postkassepar samtidigt. Hvis flere PST-filer importeres til den samme postkasse, importeres de sekventielt (én ad gangen), ikke samtidigt.

> [!NOTE]
> <sup>\*</sup> Denne sats er ikke garanteret. Serverens arbejdsbelastning og midlertidige problemer med ydeevnen kan reducere denne hastighed.

#### <a name="after-microsoft-uploads-my-pst-files-to-azure-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Når Microsoft har uploadet mine PST-filer til Azure, hvor længe opbevares de så i Azure, før de slettes?

Alle PST-filer på organisationens Azure Storage-placering (i blobcontaineren `ingestiondata`kaldet ) slettes 30 dage efter, det seneste importjob blev oprettet på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter.

Det betyder også, at når PST-filer er blevet slettet fra Azure Storage-området, vises de ikke længere på listen over filer i et færdiggjort importjob i Microsoft 365 Overholdelsescenter. Selvom et importjob muligvis stadig er anført på listen på siden **Importér PST-filer** i Microsoft 365 Overholdelsescenter, kan listen over PST-filer være tom, når du får vist detaljerne for ældre importjobs.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Hvilken version af PST-filformatet understøttes til import til Microsoft 365?

Der findes to versioner af PST-filformatet: ANSI og Unicode. Vi anbefaler, at du importerer filer, der bruger Unicode PST-filformatet. Men filer, der bruger ANSI PST-filformatet, f.eks. filer til sprog, der bruger dobbelt-byte tegnsæt (DBCS), kan også importeres Microsoft 365. Du kan finde flere oplysninger om import af ANSI PST-filer i trin 3 i Brug drevforsendelse til at importere din organisations [PST-filer til Microsoft 365](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file).

Desuden kan PST-filer fra Outlook 2007 og nyere versioner importeres til Microsoft 365.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-drive-shipping"></a>Er der en størrelsesbegrænsning for meddelelser ved import af PST-filer ved hjælp af drevforsendelse?

Ja. Hvis en PST-fil indeholder et postkasseelement, der er større end 150 MB, ignoreres elementet og importeres ikke under importen. Elementer, der er større end 150 MB importeres ikke, fordi 150 MB er meddelelsens størrelsesgrænse i Exchange Online. Du kan finde flere oplysninger [i Meddelelsesgrænser i Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

  **Hvordan håndterer PST-importprocessen duplikerede mailelementer?

PST-importprocessen søger efter dublerede elementer og kopierer ikke elementerne fra en PST-fil til postkassen eller arkivet, hvis der findes et tilsvarende element i destinationsmappen i målpostkassen eller destinationsarkivet. Hvis du importerer den samme PST-fil igen og angiver en anden destinationsmappe (ved hjælp af egenskaben TargetRootFolder i PST-importtilknytningsfilen) end den, du angav i et tidligere importjob, importeres alle elementer i PST-filen igen.

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-drive-shipping"></a>Bevares meddelelsesegenskaber som f.eks., hvornår meddelelsen blev sendt eller modtaget, listen over modtagere og andre egenskaber, når PST-filer importeres til en Microsoft 365 postkasse ved hjælp af drevforsendelse?

Ja. De oprindelige metadata for meddelelser ændres ikke under importprocessen

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-drive-shipping"></a>Er der en grænse for antallet af niveauer i et mappehierarki for en PST-fil, som jeg vil importere til en postkasse ved hjælp af drevforsendelse?

Ja. Du kan ikke importere en PST-fil med 300 eller flere niveauer af indlejrede mapper.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Kan jeg bruge drevforsendelse til at importere PST-filer til en inaktiv postkasse i Microsoft 365?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Kan jeg bruge drevforsendelse til at importere PST-filer til et onlinearkivs postkasse i en Exchange hybridinstallation?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-public-folders-in-exchange-online"></a>Kan jeg bruge drevforsendelse til at importere PST-filer til offentlige mapper i Exchange Online?

Nej, du kan ikke importere PST-filer til offentlige mapper.

#### <a name="can-microsoft-wipe-my-hard-drive-before-they-ship-it-back-to-me"></a>Kan Microsoft slette min harddisk fuldstændigt, før de sender den tilbage til mig?

Nej, Microsoft kan ikke slette harddiske fuldstændigt, før de sender dem tilbage til kunderne. Harddiske returneres til dig i samme stand, de var i, da de blev modtaget af Microsoft.

#### <a name="can-microsoft-shred-my-hard-drive-instead-of-shipping-it-back-to-me"></a>Kan Microsoft installere min harddisk i stedet for at sende den tilbage til mig?

Nej, Microsoft kan ikke destruere harddisken. Harddiske returneres til dig i samme stand, de var i, da de blev modtaget af Microsoft.

#### <a name="what-courier-services-are-supported-for-return-shipping"></a>Hvilke courier services understøttes til returnering?

Hvis du er kunde i USA eller Europa, bruger Microsoft FedEx til at returnere din harddisk. Microsoft bruger DHL i alle andre områder.

#### <a name="what-are-the-return-shipping-costs"></a>Hvad er returneringens omkostninger?

Returneringens omkostninger varierer afhængigt af, hvor tæt du er på Microsoft-datacenteret, du har sendt din harddisk til. Microsoft vil fakturere din FedEx- eller DHL-konto for returneringen af harddisken. Du har ansvaret for returneringens omkostninger.

#### <a name="can-i-use-a-custom-courier-shipping-service-such-as-fedex-custom-shipping-to-ship-my-hard-drive-to-microsoft"></a>Kan jeg bruge en tilpasset speditørtjeneste, f.eks. FedEx Custom Shipping, til at sende min harddisk til Microsoft?

Ja.

#### <a name="if-i-have-to-ship-my-hard-drive-to-another-country-is-there-anything-i-need-to-do"></a>Hvis jeg skal sende min harddisk til et andet land, er der så noget, jeg skal gøre?

Harddisken, som du sender til Microsoft, skal muligvis krydse internationale grænser. I så fald er du ansvarlig for at sikre, at harddisken og de data, den indeholder, importeres og/eller eksporteres i overensstemmelse med gældende lovgivning. Før du sender en harddisk, skal du kontakte dine rådgivere for at bekræfte, at dit drev og data kan sendes til det pågældende Microsoft-datacenter på lovlig vis. Dette hjælper med til at sikre, at den når rettidigt frem til Microsoft.
