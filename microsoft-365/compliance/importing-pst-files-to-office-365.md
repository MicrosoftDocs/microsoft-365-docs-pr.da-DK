---
title: Få mere at vide om import af PST-filer til organisationer
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Få mere at vide om, hvordan du bruger importtjenesten i Microsoft Purview-compliance-portal til masseimport af maildata (PST-filer) til brugerpostkasser.
ms.openlocfilehash: 254d9cc31e4d8be88671ca59de176a308ae008a8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636111"
---
# <a name="learn-about-importing-your-organizations-pst-files"></a>Få mere at vide om import af din organisations PST-filer

> [!NOTE]
> Denne artikel er til administratorer. Forsøger du at importere PST-filer til din egen postkasse? Se [Importér mail, kontakter og kalender fra en Outlook.pst-fil](https://go.microsoft.com/fwlink/p/?LinkID=785075).

Du kan bruge importtjenesten i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> til hurtigt at masseimportere PST-filer til Exchange Online postkasser i din organisation. Du kan importere PST-filer til Microsoft 365 på to måder:

- **Overførsel af netværk** ![ Cloudupload.](../media/54ab16ee-3822-4551-abef-3d926f4e1c01.png) – Overfør PST-filerne via netværket til en midlertidig Azure Storage-placering i Microsoft-cloudmiljøet. Derefter skal du bruge tjenesten Microsoft 365 Import til at importere PST-dataene til postkasser i din organisation.

- **Kør forsendelse** ![ Harddisk.](../media/e72b76f3-1f73-4296-b749-c325d95d9ef6.png) - Kopiér PST-filerne til en BitLocker-krypteret harddisk, og send derefter drevet fysisk til Microsoft. Når Microsoft modtager harddisken, uploader datacenterafdelingen dataene til en midlertidig Azure Storage-placering i Microsoft-cloudmiljøet. Derefter skal du bruge tjenesten Microsoft 365 Import til at importere dataene til postkasser i din organisation.

## <a name="step-by-step-instructions"></a>Trinvis vejledning

Se et af følgende emner for at få en detaljeret trinvis vejledning i masseimport af din organisations PST-filer til Microsoft 365.

- [Brug netværksoverførsel til at importere PST-filer til Microsoft 365](use-network-upload-to-import-pst-files.md)

- [Brug drevforsendelse til at importere PST-filer](use-drive-shipping-to-import-pst-files-to-office-365.md)

## <a name="how-importing-pst-files-works"></a>Sådan fungerer import af PST-filer

Her er en illustration og beskrivelse af den komplette PST-importproces. Illustrationen viser den primære arbejdsproces og fremhæver forskellene mellem overførsel af netværk og kørsel af forsendelsesmetoder.

![Arbejdsproces for PST-importproces.](../media/76997b69-67d7-433a-a0ca-9389f85a36a1.png)

1. **Download PST-importværktøjerne og nøglen til en privat Azure Storage-placering** – Det første trin er at downloade værktøjet og adgangsnøglen, der bruges til at uploade PST-filerne eller kopiere dem til en harddisk. Du henter disse fra siden **Importér** på overholdelsesportalen. Nøglen giver dig (eller Microsofts datacenterpersonale i tilfælde af drevforsendelse) de nødvendige tilladelser til at uploade PST-filer til en privat og sikker Azure Storage-placering. Denne adgangsnøgle er unik for din organisation og hjælper med at forhindre uautoriseret adgang til dine PST-filer, når de er uploadet til Microsoft-cloudmiljøet. Import af PST-filer til Microsoft 365 kræver ikke, at din organisation har et separat Azure-abonnement.

2. **Upload eller kopiér PST-filerne** – Næste trin afhænger af, om du bruger netværksupload eller driver forsendelse til at importere PST-filer. I begge tilfælde skal du bruge værktøjet og den sikre lagernøgle, du fik i det forrige trin.

    - **Netværksoverførsel:** Værktøjet AzCopy.exe (downloadet i trin 1) bruges til at uploade og gemme dine PST-filer på en Azure Storage-placering i Microsoft-cloudmiljøet. Den Azure Storage-placering, du uploader dine PST-filer til, er placeret i det samme regionale Microsoft-datacenter som din organisation.

      Hvis du vil overføre dem, skal de PST-filer, du vil importere, være placeret i et filshare eller en filserver i din organisation.

    - **Kør forsendelse:** Værktøjet WAImportExport.exe (downloadet i trin 1) bruges til at kopiere dine PST-filer til harddisken. Dette værktøj krypterer harddisken med BitLocker og kopierer derefter PST'erne til harddisken. På samme måde som netværksupload skal de PST-filer, du vil kopiere til harddisken, være placeret i et filshare eller en filserver i din organisation.

3. **Opret en PST-importtilknytningsfil** – Når PST-filerne er blevet uploadet til Azure Storage-placeringen eller kopieret til en harddisk, er det næste trin at oprette en kommasepareret værdifil (CSV), der angiver, hvilke brugerpostkasser PST-filerne importeres til (og en PST-fil kan importeres til en brugers primære postkasse eller deres arkivpostkasse). [Download en kopi af PST-importtilknytningsfilen](https://go.microsoft.com/fwlink/p/?LinkId=544717). Tjenesten Microsoft 365 Import bruger oplysningerne til at importere PST-filerne.

4. **Opret et PST-importjob** – Næste trin er at oprette et PST-importjob på siden **Importér PST-filer** på overholdelsesportalen og sende den PST-importtilknytningsfil, der blev oprettet i det forrige trin. I forbindelse med netværksupload (fordi PST-filerne er blevet uploadet til Azure) analyserer Microsoft 365 dataene i PST-filerne og giver dig derefter mulighed for at angive filtre, der styrer, hvilke data der rent faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen.

    For drevforsendelse sker der et par andre ting på dette tidspunkt i processen.

    - Du sender fysisk harddisken til et Microsoft-datacenter (leveringsadressen til Microsoft-datacenteret vises, når importjobbet oprettes).

    - Når Microsoft modtager harddisken, uploader datacenterafdelingen PST-filerne på harddisken til Azure Storage-placeringen for din organisation. Som tidligere forklaret, uploades dine PST-filer til en Azure Storage-placering, der er placeret i det samme regionale Microsoft-datacenter, hvor din organisation er placeret.

      > [!NOTE]
      > PST-filerne på harddisken uploades til Azure inden for 7 til 10 arbejdsdage, efter At Microsoft har modtaget harddisken.

      På samme måde som netværksuploadprocessen analyserer Microsoft 365 derefter dataene i PST-filerne og giver dig mulighed for at angive filtre, der styrer, hvilke data der faktisk importeres til de postkasser, der er angivet i PST-importtilknytningsfilen.

    - Microsoft sender harddisken tilbage til dig.

5. **Filtrer de PST-data, der importeres til postkasser** – Når importjobbet er oprettet (og når PST-filerne fra et drevforsendelsesjob uploades til Azure Storage-placeringen) analyserer Microsoft 365 dataene i PST-filerne (sikkert og sikkert) ved at identificere elementernes alder og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når analysen er fuldført, og dataene er klar til import, har du mulighed for at importere alle dataene i PST-filerne, eller du kan trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres.

6. **Start PST-importjobbet** – Når importjobbet er startet, bruger Microsoft 365 oplysningerne i PST-importtilknytningsfilen til at importere PST-filerne fra Azure Storage-placeringen til brugerpostkasser. Statusoplysninger om importjobbet (herunder oplysninger om hver PST-fil, der importeres) vises på siden **Importér PST-filer** på overholdelsesportalen. Når importjobbet er afsluttet, angives status for jobbet til **Fuldført**.

## <a name="why-import-email-data-to-microsoft-365"></a>Hvorfor importere maildata til Microsoft 365?

- Det er en god måde at importere din organisations arkiveringsmeddelelsesdata til Microsoft 365 på.

- Du kan bruge funktionen [Intelligent import](filter-data-when-importing-pst-files.md) til at filtrere elementerne i PST-filer, der faktisk importeres til destinationspostkasserne. Det giver dig mulighed for at trimme de data, der importeres, ved at angive filtre, der styrer, hvilke data der importeres.

- Import af maildata til Microsoft 365 hjælper med at imødekomme organisationens behov for overholdelse af angivne standarder ved at lade dig:

  - Aktivér [arkivpostkasser](enable-archive-mailboxes.md) og [automatisk udvidelse af arkivering](autoexpanding-archiving.md) for at give brugerne ekstra lagerplads på postkassen.

  - Placer postkasser i [procesventeposition](./create-a-litigation-hold.md) for at bevare indhold.

  - Brug [værktøjet Indholdssøgning](content-search.md) til at søge efter indhold i postkassen.

  - Brug [eDiscovery-sager](./get-started-core-ediscovery.md) til at administrere organisationens juridiske undersøgelser

  - Brug [opbevaringspolitikker](retention.md) i overholdelsesportalen til at styre, hvor længe postkasseindholdet bevares, og slet derefter indhold, når opbevaringsperioden udløber.

  - Brug [politikker for overholdelse af kommunikation](communication-compliance.md) til at undersøge meddelelser for at sikre, at de overholder meddelelsesstandarderne, og tilføj en klassificeringstype.

- Import af data til Microsoft 365 hjælper med at beskytte mod tab af data. Maildata, der er importeret til Microsoft 365, arver funktionerne med høj tilgængelighed i Exchange Online.

- Maildata er tilgængelige for brugere fra alle enheder, fordi de er gemt i cloudmiljøet.

## <a name="importing-sharepoint-data-to-microsoft-365"></a>Importerer SharePoint-data til Microsoft 365

Du kan også importere filer og dokumenter til SharePoint-websteder og OneDrive-konti i din organisation. Du kan finde flere oplysninger i følgende artikler:

- [Overfør til SharePoint Online](/sharepointmigration/migrate-to-sharepoint-online)

- [Introduktion til SharePoint-overførselsværktøjet](/sharepointmigration/introducing-the-sharepoint-migration-tool)

- [Overfør til SharePoint Online ved hjælp af PowerShell](/sharepointmigration/overview-spmt-ps-cmdlets)

- [Overfør dit filshareindhold til SharePoint Online ved hjælp af Azure Data Box](/sharepointmigration/how-to-migrate-file-share-content-to-spo-using-azuredatabox)

## <a name="frequently-asked-questions-about-importing-pst-files"></a>Ofte stillede spørgsmål om import af PST-filer

Her er nogle ofte stillede spørgsmål om brug af tjenesten Microsoft 365 Import til masseimport af PST-filer til Microsoft 365-postkasser.

- [Brug af netværksoverførsel til at importere PST-filer](#using-network-upload-to-import-pst-files)

- [Brug af drevforsendelse til at importere PST-filer](#using-drive-shipping-to-import-pst-files)

### <a name="using-network-upload-to-import-pst-files"></a>Brug af netværksoverførsel til at importere PST-filer

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-network-upload"></a>Hvilke tilladelser kræves der for at oprette importjob i Microsoft 365-importtjenesten ved hjælp af netværksoverførsel?

Du skal have tildelt rollen Importér eksport af postkasse i Exchange Online for at importere PST-filer til Microsoft 365-postkasser. Denne rolle er som standard ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Importér eksport af postkasse til rollegruppen Organisationsadministration. Du kan også oprette en ny rollegruppe, tildele rollen Importér eksport af postkasse og derefter tilføje dig selv eller andre brugere som medlem. Du kan få flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i [Administrer rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

Hvis du vil oprette importjob på overholdelsesportalen, skal et af følgende være sandt:

- Du skal tildeles rollen Postmodtagere i Exchange Online. Denne rolle er som standard tildelt rollegrupperne Organisationsadministration og Modtageradministration.

    Eller

- Du skal være global administrator i din organisation.

> [!TIP]
> Overvej at oprette en ny rollegruppe i Exchange Online, der er specifikt beregnet til import af PST-filer til Microsoft 365. Hvis du vil have det minimumsniveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Importér eksport af postkasse og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.

#### <a name="where-is-network-upload-available"></a>Hvor er netværksupload tilgængelig?

Netværksupload er i øjeblikket tilgængelig i disse områder: USA, Canada, Brasilien, Storbritannien, Frankrig, Tyskland, Schweiz, Norge, Europa, Indien, Det østlige Asien, Det sydøstlige Asien, Japan, Republikken Korea, Australien og De Forenede Arabiske Emirater. Netværksoverførslen vil være tilgængelig i flere områder i fremtiden.

#### <a name="what-is-the-pricing-for-importing-pst-files-by-using-network-upload"></a>Hvad er priserne for import af PST-filer ved hjælp af netværksupload?

Det er gratis at bruge netværksupload til at importere PST-filer.

Det betyder også, at når PST-filer er slettet fra Azure Storage-området, vises de ikke længere på listen over filer for et fuldført importjob i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339). Selvom et importjob stadig vises på siden **Importér data til Microsoft 365** , kan listen over PST-filer være tom, når du får vist detaljer om ældre importjob.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Hvilken version af PST-filformatet understøttes for import til Microsoft 365?

Der er to versioner af PST-filformatet: ANSI og Unicode. Vi anbefaler, at du importerer filer, der bruger Unicode PST-filformatet. Filer, der bruger ANSI PST-filformatet, f.eks. til sprog, der bruger et dobbeltbytetegnsæt (DBCS), kan dog også importeres til Microsoft 365. Du kan få flere oplysninger om import af ANSI PST-filer under Trin 4 i [Brug netværksupload til at importere PST-filer til Microsoft 365](./use-network-upload-to-import-pst-files.md).

Derudover kan PST-filer fra Outlook 2007 og nyere versioner importeres til Microsoft 365.

#### <a name="after-i-upload-my-pst-files-to-the-azure-storage-area-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Når jeg har uploadet mine PST-filer til Azure Storage-området, hvor længe opbevares de i Azure, før de slettes?

Når du bruger metoden til netværksupload til at importere PST-filer, uploader du dem til en Azure-blobobjektbeholder med navnet `ingestiondata`. Hvis der ikke er nogen igangværende importjob på siden **Importér PST-filer** i overholdelsesportalen, slettes alle PST-filer i objektbeholderen `ingestiondata` i Azure 30 dage efter, at det seneste importjob blev oprettet i overholdelsesportalen. Det betyder også, at du skal oprette et nyt importjob på overholdelsesportalen (beskrevet i trin 5 i vejledningen til netværksupload) inden for 30 dage efter upload af PST-filer til Azure.

Det betyder også, at når PST-filer er slettet fra Azure Storage-området, vises de ikke længere på listen over filer for et fuldført importjob på overholdelsesportalen. Selvom et importjob stadig er angivet på siden **Importér PST-filer** på overholdelsesportalen, kan listen over PST-filer være tom, når du får vist detaljer om ældre importjob.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-network-upload"></a>Hvor lang tid tager det at importere en PST-fil til en postkasse ved hjælp af netværksoverførsel?

Det afhænger af netværkets kapacitet, men det tager typisk flere timer for hver terabyte (TB) data, der skal uploades til Azure Storage-området for din organisation. Når PST-filerne er kopieret til Azure Storage-området, importeres en PST-fil til en Microsoft 365-postkasse med en hastighed på ca. 24 GB pr. dag<sup>\*</sup>. Hvis denne sats ikke opfylder dine behov, kan du overveje andre metoder til at hente maildata til Microsoft 365. Du kan finde flere oplysninger under [Måder at overføre flere mailkonti til Microsoft 365](/Exchange/mailbox-migration/mailbox-migration) på.

Hvis forskellige PST-filer importeres til forskellige destinationspostkasser, sker importprocessen parallelt. Med andre ord importeres hvert PST/postkassepar samtidigt. Hvis der importeres flere PST-filer til den samme postkasse, importeres de sekventielt (én ad gangen) ikke samtidigt.

> [!NOTE]
> <sup>\*</sup> Denne sats garanteres ikke. Problemer med serverarbejdsbelastningen og midlertidige ydeevne kan reducere denne hastighed.

#### <a name="how-does-the-pst-import-process-handle-duplicate-email-items"></a>Hvordan håndterer PST-importprocessen dublerede mailelementer?

PST-importprocessen søger efter dublerede elementer og kopierer ikke elementerne fra en PST-fil til postkassen eller arkivet, hvis der findes et tilsvarende element i destinationsmappen i målpostkassen eller målarkivet. Hvis du importerer den samme PST-fil igen og angiver en anden destinationsmappe (ved hjælp af egenskaben TargetRootFolder i PST-importtilknytningsfilen) end den, du angav i et tidligere importjob, importeres alle elementerne i PST-filen igen.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-network-upload"></a>Er der en grænse for meddelelsens størrelse, når du importerer PST-filer ved hjælp af netværksoverførsel?

Ja. Hvis en PST-fil indeholder et postkasseelement, der er større end 150 MB, springes elementet over og importeres ikke under importprocessen. Elementer, der er større end 150 MB, importeres ikke, fordi 150 MB er grænsen for meddelelsesstørrelsen i Exchange Online. Du kan få flere oplysninger [under Meddelelsesgrænser i Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-network-upload"></a>Bevares meddelelsesegenskaber, f.eks. hvornår meddelelsen blev sendt eller modtaget, listen over modtagere og andre egenskaber, når PST-filer importeres til en Microsoft 365-postkasse ved hjælp af netværksoverførsel?

Ja. De oprindelige meddelelsesmetadata ændres ikke under importprocessen.

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-network-upload"></a>Er der en grænse for antallet af niveauer i et mappehierarki for en PST-fil, som jeg vil importere til en postkasse ved hjælp af netværksoverførsel?

Ja. Du kan ikke importere en PST-fil, der har 300 eller flere niveauer af indlejrede mapper.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Kan jeg bruge netværksupload til at importere PST-filer til en inaktiv postkasse i Microsoft 365?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Kan jeg bruge netværksupload til at importere PST-filer til en onlinearkivpostkasse i en Exchange-hybridinstallation?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-public-folders-in-exchange-online"></a>Kan jeg bruge netværksupload til at importere PST-filer til offentlige mapper i Exchange Online?

Nej, du kan ikke importere PST-filer til offentlige mapper.

### <a name="using-drive-shipping-to-import-pst-files"></a>Brug af drevforsendelse til at importere PST-filer

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-drive-shipping"></a>Hvilke tilladelser kræves der for at oprette importjob i Microsoft 365 Import Service ved hjælp af drevforsendelse?

Du skal have tildelt rollen Importér eksport af postkasse for at importere PST-filer til Microsoft 365-postkasser. Denne rolle er som standard ikke tildelt nogen rollegruppe i Exchange Online. Du kan føje rollen Importér eksport af postkasse til rollegruppen Organisationsadministration. Du kan også oprette en ny rollegruppe, tildele rollen Importér eksport af postkasse og derefter tilføje dig selv eller andre brugere som medlem. Du kan få flere oplysninger i afsnittene "Føj en rolle til en rollegruppe" eller "Opret en rollegruppe" i [Administrer rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups).

Hvis du vil oprette importjob på overholdelsesportalen, skal et af følgende være sandt:

- Du skal tildeles rollen Postmodtagere i Exchange Online. Denne rolle er som standard tildelt rollegrupperne Organisationsadministration og Modtageradministration.

    Eller

- Du skal være global administrator i din organisation.

> [!TIP]
> Overvej at oprette en ny rollegruppe i Exchange Online, der er specifikt beregnet til import af PST-filer til Microsoft 365. Hvis du vil have det minimumsniveau af rettigheder, der kræves for at importere PST-filer, skal du tildele rollerne Importér eksport af postkasse og Postmodtagere til den nye rollegruppe og derefter tilføje medlemmer.

#### <a name="where-is-drive-shipping-available"></a>Hvor er drevforsendelse tilgængelig?

Drive shipping er i øjeblikket tilgængelig i USA, Canada, Brasilien, Storbritannien, Europa, Indien, Østasien, Sydøstasien, Japan, Republikken Korea og Australien. Drive shipping vil være tilgængelig i flere områder i fremtiden.

> [!NOTE]
> På nuværende tidspunkt er det ikke muligt at køre transport til import af PST-filer i Tyskland og Schweiz. Disse ofte stillede spørgsmål vil blive opdateret, når drevforsendelse er tilgængelig i disse lande.

#### <a name="what-commercial-licensing-agreements-support-drive-shipping"></a>Hvilke kommercielle licensaftaler understøtter forsendelse?

Du kan køre forsendelse for at importere PST-filer til Microsoft 365 via en Microsoft Enterprise Agreement (EA). Drevforsendelse er ikke tilgængelig via en Aftale om Microsoft-produkter og Services (MPSA).

#### <a name="what-is-the-pricing-for-using-drive-shipping-to-import-pst-files-to-microsoft-365"></a>Hvad er priserne for at bruge drevforsendelse til at importere PST-filer til Microsoft 365?

Omkostningerne ved at bruge drevforsendelse til import af PST-filer til Microsoft 365-postkasser er $2 USD pr. GB data. Hvis du f.eks. leverer en harddisk, der indeholder 1.000 GB (1 TB) PST-filer, er prisen USD 2.000 USD. Du kan samarbejde med en partner om at betale importgebyret. Du kan finde oplysninger om, hvordan du finder en partner, under [Find din Microsoft-partner eller -forhandler](../admin/manage/find-your-partner-or-reseller.md).

#### <a name="what-kind-of-hard-drives-are-supported-for-drive-shipping"></a>Hvilken type harddisk understøttes til levering af drev?

Kun 2,5 tommer SSD-harddiske eller 2,5 tommer eller 3,5" SATA II/III-interne harddiske understøttes til brug sammen med Microsoft 365-importtjenesten. Du kan bruge harddiske op til 10 TB. I forbindelse med importjob behandles kun den første datamængde på harddisken. Dataenheden skal være formateret med NTFS. Når du kopierer data til en harddisk, kan du vedhæfte dem direkte ved hjælp af en 2,5 tommer SSD- eller 2,5- eller 3,5 tommer SATA II/III-connector, eller du kan vedhæfte dem eksternt ved hjælp af en ekstern 2,5 tommer SSD eller 2,5 tommer eller 3,5 tommer SATA II/III USB-adapter.

> [!IMPORTANT]
> Eksterne harddiske, der følger med en indbygget USB-adapter, understøttes ikke af Microsoft 365-importtjenesten. Disken i kabinettet på en ekstern harddisk kan ikke bruges. Undlad at sende eksterne harddiske.

#### <a name="how-many-hard-drives-can-i-ship-for-a-single-import-job"></a>Hvor mange harddiske kan jeg sende til et enkelt importjob?

Du kan maksimalt sende 10 harddiske til et enkelt importjob.

#### <a name="after-i-ship-my-hard-drive-how-long-does-it-take-to-get-to-the-microsoft-datacenter"></a>Når jeg har sendt min harddisk, hvor lang tid tager det så at komme til Microsoft-datacenteret?

Det afhænger af et par ting, f.eks. din nærhed til Microsoft-datacenteret, og hvilken type leveringsmulighed du brugte til at sende din harddisk (f.eks. levering næste dag, levering på to dage eller levering på jorden). Med de fleste afsendere kan du bruge sporingsnummeret til at spore statussen for din levering.

#### <a name="after-my-hard-drive-arrives-at-the-microsoft-datacenter-how-long-does-it-take-to-upload-my-pst-files-to-azure"></a>Når min harddisk ankommer til Microsoft-datacenteret, hvor lang tid tager det så at uploade mine PST-filer til Azure?

Når din harddisk er modtaget i Microsoft-datacenteret, tager det mellem 7 og 10 arbejdsdage at uploade PST-filerne til Azure Storage-placeringen for din organisation. PST-filerne uploades til en Azure-blobobjektbeholder med navnet `ingestiondata`.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-drive-shipping"></a>Hvor lang tid tager det at importere en PST-fil til en postkasse ved hjælp af drevforsendelse?

Når PST-filerne er uploadet til Azure Storage-området, analyserer Microsoft 365 dataene i PST-filerne (på en sikker og sikker måde) for at identificere elementernes alder og de forskellige meddelelsestyper, der er inkluderet i PST-filerne. Når denne analyse er fuldført, har du mulighed for at importere alle dataene i PST-filerne eller angive filtre til at styre, hvilke data der importeres. Når du har startet importjobbet, importeres der en PST-fil til en Microsoft 365-postkasse med en hastighed på ca. 24 GB pr. dag.<sup>\*</sup> Hvis denne sats ikke opfylder dine behov, kan du overveje andre metoder til at hente maildata til Microsoft 365. Du kan finde flere oplysninger under [Måder at overføre flere mailkonti til Microsoft 365](/Exchange/mailbox-migration/mailbox-migration) på.

Hvis forskellige PST-filer importeres til forskellige destinationspostkasser, sker importprocessen parallelt. Med andre ord importeres hvert PST/postkassepar samtidigt. Hvis der importeres flere PST-filer til den samme postkasse, importeres de sekventielt (én ad gangen) ikke samtidigt.

> [!NOTE]
> <sup>\*</sup> Denne sats garanteres ikke. Problemer med serverarbejdsbelastningen og midlertidige ydeevne kan reducere denne hastighed.

#### <a name="after-microsoft-uploads-my-pst-files-to-azure-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Når Microsoft har uploadet mine PST-filer til Azure, hvor længe opbevares de i Azure, før de slettes?

Alle PST-filer på Azure Storage-placeringen for din organisation (i blobobjektbeholder med navnet `ingestiondata`) slettes 30 dage efter, at det seneste importjob blev oprettet på siden **Importér PST-filer** på overholdelsesportalen.

Det betyder også, at når PST-filer er slettet fra Azure Storage-området, vises de ikke længere på listen over filer for et fuldført importjob på overholdelsesportalen. Selvom et importjob stadig er angivet på siden **Importér PST-filer** på overholdelsesportalen, kan listen over PST-filer være tom, når du får vist detaljer om ældre importjob.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>Hvilken version af PST-filformatet understøttes for import til Microsoft 365?

Der er to versioner af PST-filformatet: ANSI og Unicode. Vi anbefaler, at du importerer filer, der bruger Unicode PST-filformatet. Filer, der bruger ANSI PST-filformatet, f.eks. til sprog, der bruger et dobbeltbytetegnsæt (DBCS), kan dog også importeres til Microsoft 365. Du kan få flere oplysninger om import af ANSI PST-filer under Trin 3 i [Brug drevforsendelse til at importere dine pst-filer til din organisation til Microsoft 365](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file).

Derudover kan PST-filer fra Outlook 2007 og nyere versioner importeres til Microsoft 365.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-drive-shipping"></a>Er der en grænse for meddelelsens størrelse, når du importerer PST-filer ved hjælp af drevforsendelse?

Ja. Hvis en PST-fil indeholder et postkasseelement, der er større end 150 MB, springes elementet over og importeres ikke under importprocessen. Elementer, der er større end 150 MB, importeres ikke, fordi 150 MB er grænsen for meddelelsesstørrelsen i Exchange Online. Du kan få flere oplysninger [under Meddelelsesgrænser i Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

  **Hvordan håndterer PST-importprocessen dublerede mailelementer?

PST-importprocessen søger efter dublerede elementer og kopierer ikke elementerne fra en PST-fil til postkassen eller arkivet, hvis der findes et tilsvarende element i destinationsmappen i målpostkassen eller målarkivet. Hvis du importerer den samme PST-fil igen og angiver en anden destinationsmappe (ved hjælp af egenskaben TargetRootFolder i PST-importtilknytningsfilen) end den, du angav i et tidligere importjob, importeres alle elementerne i PST-filen igen.

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-drive-shipping"></a>Bevares meddelelsesegenskaber, f.eks. hvornår meddelelsen blev sendt eller modtaget, listen over modtagere og andre egenskaber, når PST-filer importeres til en Microsoft 365-postkasse ved hjælp af drevforsendelse?

Ja. De oprindelige meddelelsesmetadata ændres ikke under importprocessen

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-drive-shipping"></a>Er der en grænse for antallet af niveauer i et mappehierarki for en PST-fil, som jeg vil importere til en postkasse ved hjælp af drevforsendelse?

Ja. Du kan ikke importere en PST-fil, der har 300 eller flere niveauer af indlejrede mapper.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>Kan jeg bruge drevforsendelse til at importere PST-filer til en inaktiv postkasse i Microsoft 365?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>Kan jeg bruge drevforsendelse til at importere PST-filer til en onlinearkivpostkasse i en Exchange-hybridinstallation?

Ja, denne funktion er nu tilgængelig.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-public-folders-in-exchange-online"></a>Kan jeg bruge drevforsendelse til at importere PST-filer til offentlige mapper i Exchange Online?

Nej, du kan ikke importere PST-filer til offentlige mapper.

#### <a name="can-microsoft-wipe-my-hard-drive-before-they-ship-it-back-to-me"></a>Kan Microsoft slette min harddisk, før de sender den tilbage til mig?

Nej, Microsoft kan ikke slette harddiske, før de sendes tilbage til kunder. Harddiske returneres til dig i den samme tilstand, som de var i, da de blev modtaget af Microsoft.

#### <a name="can-microsoft-shred-my-hard-drive-instead-of-shipping-it-back-to-me"></a>Kan Microsoft makulere min harddisk i stedet for at sende den tilbage til mig?

Nej, Microsoft kan ikke ødelægge din harddisk. Harddiske returneres til dig i den samme tilstand, som de var i, da de blev modtaget af Microsoft.

#### <a name="what-courier-services-are-supported-for-return-shipping"></a>Hvilke kurertjenester understøttes for returforsendelse?

Hvis du er kunde i USA eller Europa, bruger Microsoft FedEx til at returnere din harddisk. For alle andre områder bruger Microsoft DHL.

#### <a name="what-are-the-return-shipping-costs"></a>Hvad er returforsendelsesomkostningerne?

Forsendelsesomkostninger for returnering varierer, afhængigt af hvor tæt du er på det Microsoft-datacenter, du har leveret din harddisk til. Microsoft fakturerer din FedEx- eller DHL-konto for at returnere din harddisk. Prisen for returforsendelse er dit ansvar.

#### <a name="can-i-use-a-custom-courier-shipping-service-such-as-fedex-custom-shipping-to-ship-my-hard-drive-to-microsoft"></a>Kan jeg bruge en brugerdefineret kurerforsendelsestjeneste, f.eks. FedEx Custom Shipping, til at sende min harddisk til Microsoft?

Ja.

#### <a name="if-i-have-to-ship-my-hard-drive-to-another-country-is-there-anything-i-need-to-do"></a>Hvis jeg skal sende min harddisk til et andet land, er der så noget, jeg skal gøre?

Den harddisk, du sender til Microsoft, kan være nødt til at krydse internationale grænser. Hvis det er tilfældet, er du ansvarlig for at sikre, at harddisken og de data, den indeholder, importeres og/eller eksporteres i overensstemmelse med gældende lovgivning. Før du sender en harddisk, skal du kontakte dine rådgivere for at bekræfte, at dit drev og dine data lovligt kan sendes til det angivne Microsoft-datacenter. Dette vil hjælpe med at sikre, at det når Microsoft i tide.
