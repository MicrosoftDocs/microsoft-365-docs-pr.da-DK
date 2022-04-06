---
title: Felter til dokumentmetadata Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: I denne artikel defineres metadatafelterne for dokumenter i et gennemsynssæt i en sag Advanced eDiscovery i Microsoft 365.
ms.openlocfilehash: e07afbcfff0c6cae748ac6104879ec25f046cbf5
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680725"
---
# <a name="document-metadata-fields-in-advanced-ediscovery"></a>Felter til dokumentmetadata Advanced eDiscovery

I følgende tabel vises metadatafelterne for dokumenter i et gennemsynssæt i en sag Advanced eDiscovery. Tabellen indeholder følgende oplysninger:

- **Feltnavn** og **Vist feltnavn:** Navnet på metadatafeltet og navnet på det felt, der vises, når du får vist filens metadata for et markeret dokument i et gennemsynssæt. Nogle metadatafelter medtages ikke, når du får vist et dokuments filmetadata. Disse felter er fremhævet med en stjerne (*).

- **Søgbart feltnavn:** Navnet på den egenskab, du kan søge efter, når du kører en forespørgsel [med et korrektursæt](review-set-search.md). En tom celle betyder, at du ikke kan søge efter feltet i en gennemsynssætforespørgsel.

- **Eksporteret feltnavn:** Navnet på metadatafeltet, der medtages, når dokumenter eksporteres.  En tom celle betyder, at feltet ikke er inkluderet i de eksporterede metadata.

- **Beskrivelse:** En beskrivelse af metadatafeltet.

> [!NOTE]
> Feltet **Nøgleord i** søgning [efter korrektursæt anvender](./review-set-search.md) KQL (Keyword Query Language). Felterne i kolonnen Søgbare  feltnavn kan bruges i feltet Nøgleord i en søgning  i et gennemsynssæt til at oprette komplekse forespørgsler, uden at du behøver at bruge forespørgselsgeneratoren. Du kan finde flere oplysninger om KQL i Reference [til syntaks for sprog til nøgleordsforespørgsel](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

<br>

****

|Feltnavn og vist feltnavn|Søgbart feltnavn|Eksporteret feltnavn|Beskrivelse|
|---|---|---|---|
|Indholds-id for vedhæftede filer|AttachmentContentId||Id for vedhæftet indhold Id for elementet.|
|Attorney client privilege score|AttorneyClientPrivilegeScore||Attorney-client privilege model content score.|
|Forfatter|Forfatter|Doc_authors|Forfatter fra dokumentets metadata.|
|BCC|Bcc|Email_bcc|Bcc-felt til meddelelsestyper. Formatet er **DisplayName \<SMTPAddress\>**.|
|CC|Cc|Email_cc|Cc-felt til meddelelsestyper. Formatet er **DisplayName \<SMTPAddress\>**.|
|Mærkater til overholdelse af regler og|ComplianceLabels|Compliance_labels|[Opbevaringsetiketter](retention.md) anvendt på indhold Office 365.|
|Sammensat sti|CompoundPath|Compound_path|Læsbar vej, der beskriver elementets kilde.|
|Indhold*|Indhold||Udtrukket tekst i elementet.|
|Brødtekst i samtale|ConversationKart||Elementets brødtekst.|
|Samtale-id|ConversationId|Conversation_ID|Samtale-id i meddelelsen. For Teams 1:1 og gruppechats deler alle afskriftsfiler og deres familieelementer i samme samtale det samme samtale-id. Du kan finde flere oplysninger [Advanced eDiscovery arbejdsprocessen for indhold Microsoft Teams](teams-workflow-in-advanced-ediscovery.md).|
|Id for samtalefamilie|ConversationFamilyID|ConversationFamilyID|Id'et, der identificerer individuelle elementer i en samtale samt de relaterede elementer i samtalen.|
|Samtaleindeks||Conversation_index|Samtaleindeks fra meddelelsen.|
|Samtalenavn||Samtalenavn|Dette felt afhænger af indholdstypen.<br>**Teams 1:1 Chat: de** første 40 tegn i første meddelelse.<br>**Teams 1:N-chat:** Navnet på gruppechat, hvis den ikke er tilgængelig, de første 40 tegn i den første meddelelse.<br>**Teams kanalindlæg: Underoverskrift** for indlægget eller meddelelsen, hvis dette ikke er tilgængeligt, de første 40 tegn i den første meddelelse.|
|Pdf-tidspunkt for samtale|ConversationPdfTime||Dato for oprettelse af PDF-versionen af samtalen.|
|Samtale redaction Burn Time|ConversationRedactionBurnTime||Dato for oprettelse af PDF-versionen af samtalen til Chat.|
|Samtaleemne|SamtaleTopisk||Elementets samtaleemne.|
|Samtaletype|ConversationType|ConversationType|Typen af chatsamtale. Værdierne er: <br>**Teams 1:1 og gruppechats og alle Yammer samtaler: Gruppe**<br>**Teams kanaler og private kanaler:** Kanal|
|Indeholder slettet meddelelse|ContainsDeletedMessage|ContainsDeletedMessage|Angiver, om chatudskriften indeholder en slettet meddelelse|
|Indeholder redigeret meddelelse|ContainsEditedMessage|ContainsEditedMessage|Angiver, om chatudskriften indeholder en redigeret meddelelse|
|Teams meddelelsestitel|TeamsAnnouncementTitle|TeamsAnnouncementTitle|Titel fra en [teammeddelelse](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992).|
|||Converted_file_path|Stien til den konverterede eksportfil. Kun til intern brug af Microsoft.|
|Øvøvrisk|Øvøvrisk|Øvøvrisk|Navnet på den, der blev tilknyttet elementet.|
|Dato|Dato|Dato|Dato er et beregnet felt, der afhænger af filtypen.<p>**Mail**: Dato for afsendt<br>**Vedhæftede filer** i mails: Dato for seneste ændring af dokumentet. hvis den ikke er tilgængelig, sendes den forælders dato for afsendt<br>**Integrerede dokumenter**: Dato for seneste ændring af dokumentet. Hvis den ikke er tilgængelig, kan du se den overordnedes dato for seneste ændring<br>**SPO-dokumenter (indeholder moderne vedhæftede filer)**: Dato for seneste ændring af dokumentet; Hvis den ikke er tilgængelig, SharePoint dato for seneste ændring<br>**Ikke-Office 365 dokumenter**: Dato for seneste ændring<br>**Møder**: Mødets startdato<br>**Telefonsvarer**: Dato for afsendt post<br>**Chat**: Dato for afsendt<br>**Teams**: Dato for sendt|
|Dokumentkommentarer|DocComments|Doc_comments|Kommentarer fra dokumentets metadata.|
|Dokumentvirksomhed||Doc_company|Firma fra dokumentets metadata.|
|Dokumentdato oprettet|CreatedTime|Doc_date_created|Oprette dato ud fra dokumentmetadata.|
|DocIndex*|||Indekset i familien. **-1** eller **0 betyder** , at det er roden.|
|Nøgleord i dokumenter||Doc_keywords|Nøgleord fra dokumentets metadata.|
|Dokument ændret af||Doc_modified_by|Den bruger, der senest har ændret dokumentet fra dokumentmetadata.|
|Dokumentrevision|Doc_Version|Doc_Version|Revision fra dokumentets metadata.|
|Dokumentt emne||Doc_subject|Emne fra dokumentets metadata.|
|Dokumentskabelon||Doc_template|Skabelon fra dokumentets metadata.|
|DocLastSavedBy||Doc_last_saved_by|Navnet på den bruger, der sidst har gemt dokumentet.|
|Det dominerende tema|Det dominerendetheme|Dominant_theme|Det dominerende tema som beregnet for analyser.|
|Dupliker undersæt||Duplicate_subset|Gruppe-id for nøjagtige dubletter.|
|EmailAction*||Email_action|Værdier er **Ingen****, Svar** eller **Videressendelse**. baseret på emnelinjen i en meddelelse.|
|Anmodning om kvittering for levering af mail||Email_delivery_receipt|Mailadresse, der er angivet i Internetheadere som kvittering for modtagelse.|
|Prioritet|EmailImportance|Email_importance|Meddelelsens prioritet: **0** - Lav; **1** - Normal; **2** - Høj|
|Ignorerede behandlingsfejl|ErrorIgnored|Error_Ignored|Fejlen blev ignoreret og ikke løst.|
|EmailInternetHeaders|EmailInternetHeaders|Email_internet_headers|Det komplette sæt mailoverskrifter fra mailen|
|EmailLevel*||Email_level|Angiver en meddelelses niveau i den mailtråd, den tilhører; Vedhæftede filer arver dens overordnede meddelelses værdi.|
|Mail-id||Email_message_ID|Internetmeddelelses-id fra meddelelsen.|
|EmailReadReceiptRequested||Email_read_receipt|Mailadresse, der er angivet i internetoverskrifter for kvittering for læsning.|
|Mailsikkerhed|EmailSecurity|Email_security|Sikkerhedsindstilling for meddelelsen: **0** - Ingen; **1** - signeret; **2** - Krypteret; **3** – Krypteret og signeret.|
|Mailfølsomhed|EmailSensitivity|email_sensitivity|Følsomhedsindstilling for meddelelsen: **0** - Ingen; **1** Personlig; **2** - Privat; **3** – Firmakonfidentiel.|
|Mailsæt|EmailSet|Email_set|Gruppe-id for alle meddelelser i samme mailsæt.|
|EmailThread*||Email_thread|Placering af meddelelsen i mailsættet. består af node-l'er fra roden til den aktuelle meddelelse og er adskilt af punktummer (.).|
|||Export_native_path|Stien til den eksporterede fil.|
|Udtrukket indholdstype||Native_type|Udtrukket indholdstype i form af mimetype; f.eks **. image/jpeg**|
|||Extracted_text_path|Stien til den udpakkede tekstfil i eksporten.|
|ExtractedTextLength*||Extracted_text_length|Antal tegn i den udtrukne tekst.|
|FamilyDuplicateSet*||Family_duplicate_set|Numerisk id for familier, der er nøjagtige dubletter af hinanden (samme indhold og alle de samme vedhæftede filer).|
|Familie-id|FamilyId|Family_ID|Grupperer vedhæftede filer sammen og udtrækker elementer fra mails og chatsamtaler med det overordnede element. Dette omfatter chatten eller mailen og alle vedhæftede filer og udtrukne elementer.|
|Familiestørrelse||Family_size|Antal dokumenter i familien.|
|Filklasse|FileClass|File_class|For indhold fra SharePoint og OneDrive: **Dokument**. <br>For indhold fra Exchange: **Mail eller** Vedhæftet **fil**. <br>Indhold fra Teams eller Yammer: **Samtaler**.|
|Fil-id|FileId|File_ID|Dokumentidentifikator er entydig i sagen.|
|Filsystemdato oprettet||File_system_date_created|Oprettelsesdato fra filsystemet (gælder kun for ikke-Office 365 data).|
|Ændring af filsystemdato||File_system_date_modified|Ændringsdato fra filsystemet (gælder kun for ikke-Office 365 data).|
|Filtype|FileType||Elementets filtype baseret på filtypenavn.|
|Gruppe-id|GroupId|Group_ID|Grupperer alle elementer til mail og dokumenter sammen. Dette inkluderer meddelelsen og alle vedhæftede filer og udtrukne elementer i mails. For dokumenter omfatter dette dokumentet og eventuelle integrerede elementer.|
|Har vedhæftet fil|EmailHasAttachment|Email_has_attachment|Angiver, om meddelelsen har vedhæftede filer.|
|Har advokat|HasAttorney||**True** when least one of the participants is found in the attorney list; Ellers er værdien **Falsk**.|
|HasText*||Has_text|Angiver, om elementet har tekst eller ej. mulige værdier er **Sand** og **Falsk**.|
|Uforanderligt id||Immutable_ID|Dette id bruges til entydigt at identificere et dokument i et korrektursæt. Dette felt kan ikke bruges i en søgning i et korrektursæt, og id'et kan ikke bruges til at få adgang til et dokument på dets oprindelige placering.|
|Inkluderende type|InclusiveType|Inclusive_type|Inkluderende type beregnet til analyse: **0** – ikke inklusive; **1** – inklusive; **2** – inklusive minus; **3** – inkluderende kopi.|
|I Svar på id||In_reply_to_ID|Som svar på id fra meddelelsen.|
|InputFileExtension||Original_file_extension|Det oprindelige filtypenavn for filen.|
|InputFileID||Input_file_ID|Fil-id'et for elementet på øverste niveau i korrektursættet. Ved vedhæftede filer er dette id det overordnede id. Dette kan bruges til at gruppere familier sammen.|
|Er moderne vedhæftet fil|IsModernAttachment||Denne fil er en moderne vedhæftet eller sammenkædet fil.|
|Er fra dokumentversion|IsFromDocumentVersion||Det aktuelle dokument er fra en anden version af et andet dokument.|
|Er vedhæftet fil i en mail|IsEmailAttachment||Dette element er fra en vedhæftet fil i en mail, der vises som et vedhæftet element i meddelelsen.|
|Er indbygget vedhæftet fil|IsInlineAttachment||Den blev vedhæftet indbygget og vises i brødteksten i meddelelsen.|
|Er repræsentant|IsRepresentative|Is_representative|Et dokument i hvert sæt af nøjagtige dubletter markeres som repræsentant.|
|Elementklasse|ItemClass|Item_class|Elementklasse leveret af Exchange-server. F.eks **. IPM. Bemærk!**|
|Dato for seneste ændring|LastModifiedDate|Doc_date_modified|Dato for seneste ændring fra dokumentmetadata.|
|Indlæs id|LoadId|Load_ID|Id'et for det indlæsningssæt, hvor elementet blev føjet til et korrektursæt.|
|Placering|Placering|Placering|Streng, der angiver typen af placering, som dokumenter blev kildet fra.<p>**Importerede data** – ikke-Office 365 data<br>**Teams** - Microsoft Teams<br>**Exchange** – Exchange postkasser<br>**SharePoint** – SharePoint websteder<br>**OneDrive** – OneDrive konti|
|Placeringsnavn|LocationName|Location_name|Streng, der identificerer elementets kilde. Til ombytning er dette postkassens SMTP-adresse. URL-SharePoint for OneDrive gruppe af websteder.|
|||Marked_as_pivot|Denne fil er pivot i et næsten duplikeret sæt.|
|Markeret som repræsentant|MarkAsRepresentative||Ét dokument fra hvert sæt af nøjagtige dubletter markeres som repræsentanter.|
|Mødets slutdato|MeetingEndDate|Meeting_end_date|Mødets slutdato for møder.|
|Mødets startdato|MeetingStartDate|Meeting_start_date|Mødets startdato for møder.|
|Meddelelses type|MessageKind|Message_kind|Typen af meddelelse, der skal søges efter. Mulige værdier: **<p><br><br><br>Kontakters dokumenter sender eksterne datafaxer <br>i journaler <br><br><br><br>til møder microsoftteams** (returnerer elementer fra chatsamtaler, møder og opkald i Microsoft Teams) **<br><br><br>læser indlæg med rssfeeds-opgaver <br><br>på voicemail**|
|Moderne vedhæftet forælder-id||ModernAttachment_ParentId|Det uforanderlige id for dokumentets overordnede.|
|Lokal udvidelse|NativeExtension|Native_extension|Oprindelig udvidelse af elementet.|
|Lokalt filnavn|NativeFileName|Native_file_name|Elementets oprindelige filnavn.|
|NativeMD5||Native_MD5|MD5-hash (128-bit hash-værdi) for filstrømmen.|
|NativeSHA256||Native_SHA_256|SHA256-hash (256-bit hash-værdi) for filstrømmen.|
|Sortering af ND/ET: Undtagen vedhæftede filer|NdEtSortExclAttach|ND_ET_sort_excl_attach|Sammenkæd mailtrådsættet (ET) og det næsten duplikerede sæt (ND). Dette felt bruges til effektiv sortering på korrekturtid. Et **D** har præfiks på ND-sæt, og et **E** har præfiks på ET-sæt.|
|Sortering efter ND/ET: Herunder vedhæftede filer|NdEtSortInclAttach|ND_ET_sort_incl_attach|Sammenkæd et mailtrådsæt (ET) og næsten en dubletsæt (ND). Dette felt bruges til effektiv sortering på korrekturtid. Et **D** har præfiks på ND-sæt, og et **E** har præfiks på ET-sæt. Hvert mailelement i et ET-sæt efterfølges af de relevante vedhæftede filer.|
|Nær dubletsæt||ND_set|Elementer, der ligner pivotdokumentet, deler den samme ND_set.|
|O365-forfattere||O365_authors|Forfatter fra SharePoint.|
|O365 oprettet af||O365_created_by|Oprettet af SharePoint.|
|O365-dato oprettet||O365_date_created|Oprettelsesdato fra SharePoint.|
|O365ModifiedDate||O365_date_modified|Den dato, et dokument (eller en dokumentversion), der er indsamlet fra SharePoint eller OneDrive for Business blev ændret. Dette er den samme ændringsdato som den, der vises i versionshistorikken i SharePoint og OneDrive brugeroplevelse.|
|O365 ændret af||O365_modified_by|Ændret af fra SharePoint eller OneDrive.|
|Andre øverere|Dedupedcustodians|Deduped_custodians|Liste over kontrolere af dokumenter, der er nøjagtige dubletter (for mails, baseret på indhold, for dokumenter baseret på hash).|
|Andre fil-id'er|DedupedFileIds|Deduped_file_IDs|Liste over fil-id'er af dokumenter, der er nøjagtige dubletter (for mails, baseret på indhold, for dokumenter baseret på hash).|
|Andre stier|Dedupedcompoundpath|Deduped_compound_path|Liste over sammensatte stier til dokumenter, der er nøjagtige dubletter (mail: baseret på indhold, dokumenter: baseret på hash).|
|Overordnet id|ParentId|Parent_ID|Id for elementets overordnede.|
|ParentNode||Parent_node|Den nærmeste foregående mail i mailtråden.|
|Deltagerdomæner|ParticipantDomains|Email_participant_domains|Liste over alle domæner for deltagere i en meddelelse.|
|Deltagere|Deltagere|Email_participants|Liste over alle deltagere i en meddelelse; Afsender, Til, Cc, Bcc.|
|Pivot-id|PivotId|Pivot_ID|Id'et for en pivot.|
|Potentielt privilegeret|PotentieltPrivilegeret|Potentially_privileged|Sand, hvis registreringsmodellen for attorney-client-rettigheder opfatter dokumentet som potentielt privilegeret|
|Status for behandling|ProcessingStatus|Error_code|Behandler status, efter elementet blev føjet til et korrektursæt.|
|Læs fraktil|ReadPercentile||Læs fraktil for dokumentet baseret på relevans.|
|Modtaget|Modtaget|Email_date_received|Dato og klokkeslæt for modtagelse af mailen i UTC.|
|Antal modtagere||Recipient_count|Antal modtagere i meddelelsen.|
|Modtagerdomæner|RecipientDomains|Email_recipient_domains|Liste over alle domæner for modtagere af en meddelelse.|
|Modtagere|Modtagere|Email_recipients|Liste over alle modtagere af en meddelelse (Til, Cc, Bcc).|
|||Redacted_file_path|Stien til den redigerede erstatningsfil i eksporten.|
|||Redacted_text_path|Stien til den generede tekstfilerstatning i eksporten. Kun til intern brug af Microsoft.|
|Relevansmærke Sagsproblem 1||Relevance_tag_case_issue_1|Relevansmærke Sagsproblem 1 fra Relevans.|
|Relevansscore|Relevansstegn||Relevansscore for et dokument baseret på relevans.|
|Relevansmærke|Relevanstag||Relevansscore for et dokument baseret på relevans.|
|Repræsentativt id|RepresentativeId||Numerisk id for hvert sæt af nøjagtige dubletter.|
|||Row_number|Rækkenummeret på elementet i indlæsningsfilen.|
|Afsender|Afsender|Email_sender|Feltet Afsender (Fra) for meddelelsestyper. Formatet er **DisplayName \<SmtpAddress>**.|
|Afsender/forfatter|AfsenderAuthor||Beregnet felt bestående af afsenderen eller forfatteren af elementet.|
|Afsenderdomæne|SenderDomain|Email_sender_domain|Afsenderens domæne.|
|Sendt|Sendt|Email_date_sent|Meddelelsens sendt dato.<br>Chatsamtaler: Startdato fra udskriften|
|Indstil ordre: Inkluderende først|SetOrderInclusivesFirst|Set_order_inclusives_first|Sorteringsfelt – mails og vedhæftede filer: modkronologisk; dokumenter: pivotér først derefter ved at faldende lighedsscore.|
|Angiv id||Set_ID|Dokumenter med lignende indhold (ND_set) eller mail i den samme mailtråd (Email_set) deler den samme Set_ID.|
|Lighedspercent||Similarity_percent|Angiver, hvor lig et dokument er med pivoten for det næsten duplikerede sæt.|
|Oprindelige filstørrelse|Størrelse|Native_size|Antallet af byte for det oprindelige element.|
|Emne|Emne|Email_subject|Meddelelsens emne.|
|Emne/titel|Emne||Beregnet felt bestående af elementets emne eller titel.|
|Mærker|Mærker|Mærker|Mærker anvendt i et korrektursæt.|
|Kanalnavn|Kanal|ChannelName|Dette er Teams kanalnavn. Gælder kun for Microsoft Teams indhold.|
|Teamnavn|Teamnavn|Teamnavn|**Teams:** Navn på team<br>**Yammer: Communitynavn**|
|Listen Temaer|ThemesList|Themes_list|Listen Temaer beregnes for analyser.|
|Titel|Titel|Doc_title|Titel fra dokumentets metadata. Titel fra dokumentets metadata. For Teams og Yammer indhold er dette værdien fra egenskaben Samtalenavn.|
|Hvis du vil|Hvis du vil|Email_to|Felt til meddelelsestyper. Formatet er **DisplayName\<SmtpAddress>**|
|Entydigt i mailsæt|UniqueInEmailSet||**Falsk** , hvis der er en kopi af den vedhæftede fil i mailsættet.|
|Versions-gruppe-id||Version_Group_Id|Grupperer de forskellige versioner af det samme dokument.|
|VersionNumber||Version_Number|Versionsnummeret på et dokument, der er indsamlet SharePoint eller OneDrive for Business. Dette er det samme versionsnummer som det, der vises i versionshistorikken i SharePoint og OneDrive brugeroplevelse.|
|Blev løst|WasRemediated|Was_Remediated|**Sand** , hvis elementet blev løst, ellers **falsk**.|
|Ordoptælling|WordCount|Word_count|Antallet af ord i elementet.|
|||||

> [!NOTE]
> Du kan finde flere oplysninger om søgbare egenskaber, når du søger på Office 365-indholdsplaceringer, når du indsamler data for en Advanced eDiscovery-sag, under Nøgleordsforespørgsler og søgebetingelser [for indholdssøgning](keyword-queries-and-search-conditions.md).
