---
title: Dokumentmetadatafelter i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Denne artikel definerer metadatafelterne for dokumenter i et gennemsynssæt i en sag i Microsoft Purview eDiscovery (Premium) i Microsoft 365.
ms.openlocfilehash: a6fc8479d3ecd2b89c0331220fb7f88f46bda1e4
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629745"
---
# <a name="document-metadata-fields-in-ediscovery-premium"></a>Dokumentmetadatafelter i eDiscovery (Premium)

I følgende tabel vises metadatafelterne for dokumenter i et gennemsynssæt i en sag i Microsoft Purview eDiscovery (Premium). Tabellen indeholder følgende oplysninger:

- **Feltnavn** og **Vist feltnavn:** Navnet på metadatafeltet og navnet på det felt, der vises, når du får vist filmetadata for et valgt dokument i et gennemsynssæt. Nogle metadatafelter medtages ikke, når du får vist filmetadata for et dokument. Disse felter er fremhævet med en stjerne (*).

- **Feltnavn, der kan søges i:** Navnet på den egenskab, du kan søge efter, når du kører en [forespørgsel, der er angivet til gennemsyn](review-set-search.md). En tom celle betyder, at du ikke kan søge efter feltet i en forespørgsel i et gennemsynssæt.

- **Navn på eksporteret felt:** Navnet på det metadatafelt, der inkluderes, når dokumenter eksporteres.  En tom celle betyder, at feltet ikke er inkluderet i de eksporterede metadata.

- **Beskrivelse:** En beskrivelse af metadatafeltet.

> [!NOTE]
> I feltet **Nøgleord** i [korrektursæt-søgning](./review-set-search.md) bruges KQL (Keyword Query Language). De felter, der er angivet i kolonnen **Søgbart feltnavn** , kan bruges i feltet **Nøgleord** i en gennemsynssætsøgning til at danne komplekse forespørgsler, uden at du behøver at bruge forespørgselsgeneratoren. Du kan få flere oplysninger om KQL under [syntaksreference til nøgleordsforespørgselssprog](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

<br>

****

|Feltnavn og Vist feltnavn|Feltnavn, der kan søges i|Navn på eksporteret felt|Beskrivelse|
|---|---|---|---|
|Indholds-id for vedhæftet fil|AttachmentContentId||Indholds-id for vedhæftet fil for elementet.|
|Score for advokatklientrettigheder|AttorneyClientPrivilegeScore||Score for modelindhold for advokat-klient-rettigheder.|
|Forfatter|Forfatter|Doc_authors|Forfatter fra dokumentets metadata.|
|BCC|Bcc|Email_bcc|Bcc-felt til meddelelsestyper. Formatet er **DisplayName \<SMTPAddress\>**.|
|CC|Cc|Email_cc|Cc-felt til meddelelsestyper. Formatet er **DisplayName \<SMTPAddress\>**.|
|Overholdelsesmærkater|ComplianceLabels|Compliance_labels|[Opbevaringsmærkater](retention.md), der anvendes på indhold i Office 365.|
|Sammensat sti|Sammensat sti|Compound_path|Sti, der kan læses af mennesker, og som beskriver elementets kilde.|
|Indhold*|Indhold||Udtrukket tekst til elementet.|
|Brødtekst i samtale|Samtalebod||Elementets samtalebrødtekst.|
|Samtale-id|ConversationId|Conversation_ID|Samtale-id fra meddelelsen. I forbindelse med Teams 1:1- og gruppechats deler alle transskriptionsfiler og deres familieelementer i den samme samtale det samme samtale-id. Du kan finde flere oplysninger i [arbejdsprocessen for eDiscovery (Premium) for indhold i Microsoft Teams](teams-workflow-in-advanced-ediscovery.md).|
|Samtalefamilie-id|ConversationFamilyID|ConversationFamilyID|Det id, der identificerer individuelle elementer i en samtale samt de relaterede elementer i samtalen.|
|Samtaleindeks||Conversation_index|Samtaleindeks fra meddelelsen.|
|Samtalenavn||Samtalenavn|Dette felt afhænger af indholdstypen.<br>**Teams 1:1-chat:** første 40 tegn i den første meddelelse.<br>**Teams 1:N-chat:** Navn på gruppechat; hvis den ikke er tilgængelig, de første 40 tegn i den første meddelelse.<br>**Indlæg til Teams-kanal:** Underoverskrift for opslag eller meddelelse; hvis den ikke er tilgængelig, de første 40 tegn i den første meddelelse.|
|Samtale-PDF-tid|ConversationPdfTime||Dato for oprettelse af PDF-versionen af samtalen.|
|Brændtid for samtale-redigering|ConversationRedactionBurnTime||Den dato, hvor PDF-versionen af samtalen blev oprettet til Chat.|
|Samtaleemne|SamtaleTopic||Samtaleemne for elementet.|
|Samtaletype|Samtaletype|Samtaletype|Typen af chatsamtale. Værdierne er: <br>**Teams 1:1 og gruppechats og alle Yammer-samtaler:** Gruppe<br>**Teams-kanaler og private kanaler:** Kanal|
|Indeholder slettet meddelelse|ContainsDeletedMessage|ContainsDeletedMessage|Angiver, om chatudskriften indeholder en slettet meddelelse|
|Indeholder redigeret meddelelse|ContainsEditedMessage|ContainsEditedMessage|Angiver, om chatudskriften indeholder en redigeret meddelelse|
|Teams-meddelelsestitel|TeamsAnnouncementTitle|TeamsAnnouncementTitle|Titel fra en [teams-meddelelse](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992).|
|||Converted_file_path|Stien til den konverterede eksportfil. Kun til intern Brug af Microsoft.|
|Vogter|Vogter|Vogter|Navnet på den tilsynsførende, som elementet var knyttet til.|
|Dato|Dato|Dato|Dato er et beregnet felt, der afhænger af filtypen.<p>**Mail**: Afsendelsesdato<br>**Vedhæftede filer i mails**: Dato for seneste ændring af dokumentet; Hvis den ikke er tilgængelig, sendes den overordnedes dato<br>**Integrerede dokumenter**: Dato for seneste ændring af dokumentet; Hvis den ikke er tilgængelig, den overordnedes seneste ændringsdato<br>**SPO-dokumenter (indeholder moderne vedhæftede filer)**: Dato for seneste ændring af dokumentet; Hvis den ikke er tilgængelig, senest ændret i SharePoint<br>**Ikke-Office 365 dokumenter**: Dato for seneste ændring<br>**Møder**: Mødets startdato<br>**Talebesked**: Sendt dato<br>**Chat**: Afsendelsesdato<br>**Teams**: Afsendelsesdato|
|Dokumentkommentarer|Dokumentkommentarer|Doc_comments|Kommentarer fra dokumentets metadata.|
|Dokumentfirma||Doc_company|Firma fra dokumentets metadata.|
|Oprettelsesdato for dokument|CreatedTime|Doc_date_created|Opret dato ud fra dokumentmetadata.|
|DocIndex*|||Indekset i familien. **-1** eller **0** betyder, at det er roden.|
|Dokumentnøgleord||Doc_keywords|Nøgleord fra dokumentets metadata.|
|Dokumentet er ændret af||Doc_modified_by|Den bruger, der senest har ændret dokumentet fra dokumentmetadata.|
|Dokumentrevision|Doc_Version|Doc_Version|Revision fra dokumentets metadata.|
|Dokumentemne||Doc_subject|Emne fra dokumentets metadata.|
|Dokumentskabelon||Doc_template|Skabelon fra dokumentets metadata.|
|DocLastSavedBy||Doc_last_saved_by|Navnet på den bruger, der senest gemte dokumentet.|
|Dominerende tema|DominantTheme|Dominant_theme|Dominerende tema som beregnet til analyse.|
|Dupliker undersæt||Duplicate_subset|Gruppe-id for præcise dubletter.|
|Mailhandling*||Email_action|Værdierne er **None (Ingen**), **Reply (Svar**) eller **Forward (Videresend**). baseret på emnelinjen i en meddelelse.|
|Kvittering for levering via mail||Email_delivery_receipt|Mailadresse, der er angivet i InternetHeadere til kvittering for levering.|
|Betydning|Importance for mail|Email_importance|Vigtigheden af meddelelsen: **0** - Lav; **1** - Normal; **2** - høj|
|Ignorerede behandlingsfejl|Fejlretning|Error_Ignored|Fejlen blev ignoreret og blev ikke rettet.|
|MailInternetHeaders|MailInternetHeaders|Email_internet_headers|Det fulde sæt mailheadere fra mailmeddelelsen|
|Mailniveau*||Email_level|Angiver en meddelelses niveau i den mailtråd, den tilhører. vedhæftede filer nedarver den overordnede meddelelses værdi.|
|Mailmeddelelses-id||Email_message_ID|Internetmeddelelses-id fra meddelelsen.|
|EmailReadReceiptRequested||Email_read_receipt|Mailadresse, der er angivet i internetheadere til kvittering for læsning.|
|Mailsikkerhed|Mailsikkerhed|Email_security|Sikkerhedsindstilling for meddelelsen: **0** - Ingen; **1** - Signeret; **2** – Krypteret; **3** – Krypteret og signeret.|
|Mailfølsomhed|Følsomhed over for mail|email_sensitivity|Følsomhedsindstilling for meddelelsen: **0** - Ingen; **1** Personlig; **2** - Privat; **3** – CompanyConfidential.|
|Mailsæt|Mailsæt|Email_set|Gruppe-id for alle meddelelser i det samme mailsæt.|
|MailTråd*||Email_thread|Meddelelsens placering i mailsættet. består af node-id'er fra roden til den aktuelle meddelelse og er adskilt af punktummer (.).|
|||Export_native_path|Stien til den eksporterede fil.|
|Udpakket indholdstype||Native_type|Udpakket indholdstype i form af MIME-type; f.eks. **billede/jpeg**|
|||Extracted_text_path|Stien til den udtrukne tekstfil i eksporten.|
|Uddraget tekstlængde*||Extracted_text_length|Antal tegn i den udtrukne tekst.|
|FamilyDuplicateSet*||Family_duplicate_set|Numerisk id for familier, der er nøjagtige dubletter af hinanden (samme indhold og alle de samme vedhæftede filer).|
|Familie-id|FamilyId|Family_ID|Grupperer vedhæftede filer og udtrukne elementer fra mail og chats med dets overordnede element. Dette omfatter chat eller mail og alle vedhæftede filer og udtrukne elementer.|
|Familiestørrelse||Family_size|Antallet af dokumenter i familien.|
|Filklasse|FileClass|File_class|For indhold fra SharePoint og OneDrive: **Dokument**. <br>For indhold fra Exchange: **Mail** eller **Vedhæftet fil**. <br>For indhold fra Teams eller Yammer: **Samtaler**.|
|Fil-id|Fil-id|File_ID|Dokument-id'et er entydigt i sagen.|
|Oprettelsesdato for filsystem||File_system_date_created|Oprettelsesdato fra filsystem (gælder kun for data, der ikke er Office 365).|
|Ændringsdato for filsystem||File_system_date_modified|Dato for ændring fra filsystem (gælder kun for data, der ikke er Office 365).|
|Filtype|Filtype||Elementets filtype baseret på filtypenavnet.|
|Gruppe-id|Gruppe-id|Group_ID|Grupperer alle elementer til mail og dokumenter. I forbindelse med mail omfatter dette meddelelsen og alle vedhæftede filer og udtrukne elementer. For dokumenter omfatter dette dokumentet og alle integrerede elementer.|
|Har vedhæftet fil|EmailHasAttachment|Email_has_attachment|Angiver, om meddelelsen indeholder vedhæftede filer.|
|Har advokat|HasAttorney||**Sand** , når mindst én af deltagerne findes på advokatlisten; Ellers er værdien **False**.|
|Har tekst*||Has_text|Angiver, om elementet indeholder tekst. mulige værdier er **True** og **False**.|
|Uforanderligt id||Immutable_ID|Dette id bruges til entydigt at identificere et dokument i et korrektursæt. Dette felt kan ikke bruges i en gennemsynssætsøgning, og id'et kan ikke bruges til at få adgang til et dokument på dets oprindelige placering.|
|Inkluderende type|InclusiveType|Inclusive_type|Inkluderende type beregnet for analyse: **0** – ikke inkluderende; **1** - inklusive; **2** - inklusive minus; **3** – inklusive kopi.|
|Svar til id||In_reply_to_ID|Som svar på id'et fra meddelelsen.|
|InputFileExtension||Original_file_extension|Filens oprindelige filtypenavn.|
|InputFileID||Input_file_ID|Fil-id'et for elementet på øverste niveau i korrektursættet. For en vedhæftet fil er dette id id'et for det overordnede element. Dette kan bruges til at gruppere familier sammen.|
|Er moderne vedhæftet fil|IsModernAttachment||Denne fil er en moderne vedhæftet fil eller sammenkædet fil.|
|Er fra dokumentversion|IsFromDocumentVersion||Det aktuelle dokument er fra en anden version af et andet dokument.|
|Er vedhæftet fil|IsEmailAttachment||Dette element er fra en vedhæftet fil, der vises som et vedhæftet element i meddelelsen.|
|Er indbygget vedhæftet fil|IsInlineAttachment||Dette blev vedhæftet indbygget og vises i meddelelsens brødtekst.|
|Er repræsentant|IsRepresentative|Is_representative|Ét dokument i hvert sæt nøjagtige dubletter markeres som repræsentativt.|
|Elementklasse|ItemClass|Item_class|Elementklasse leveret af exchange-server; F.eks **. IPM. Bemærk**|
|Dato for seneste ændring|Senest ændret dato|Doc_date_modified|Dato for seneste ændring fra dokumentmetadata.|
|Indlæs id|LoadId|Load_ID|Id'et for det indlæsningssæt, som elementet blev føjet til et korrektursæt i.|
|Placering|Placering|Placering|Streng, der angiver den type placering, som dokumenter blev hentet fra.<p>**Importerede data** – data, der ikke er Office 365<br>**Teams** – Microsoft Teams<br>**Exchange** – Exchange-postkasser<br>**SharePoint** - SharePoint-websteder<br>**OneDrive** – OneDrive-konti|
|Navn på placering|Placeringsnavn|Location_name|Streng, der identificerer elementets kilde. Til exchange vil dette være SMTP-adressen på postkassen. for SharePoint og OneDrive, URL-adressen til gruppen af websteder.|
|||Marked_as_pivot|Denne fil er pivotet i et næsten duplikeret sæt.|
|Markeret som repræsentant|MarkAsRepresentative||Ét dokument fra hvert sæt nøjagtige dubletter markeres som repræsentanter.|
|Mødets slutdato|Mødedato|Meeting_end_date|Mødets slutdato for møder.|
|Mødets startdato|Mødestartdato|Meeting_start_date|Mødets startdato for møder.|
|Meddelelsestype|MessageKind|Message_kind|Den type meddelelse, der skal søges efter. Mulige værdier: **<p>kontakter <br>docs <br>email <br>externaldata <br>faxes <br>im <br>journals <br>møder <br>Microsoftteams** (returnerer elementer fra chats, møder og opkald i Microsoft Teams) **<br>noter indlæg <br><br>rssfeeds <br>opgaver <br>voicemail**|
|Moderne overordnet id for vedhæftet fil||ModernAttachment_ParentId|Det uforanderlige id for dokumentets overordnede.|
|Oprindelig udvidelse|NativeExtension|Native_extension|Oprindelig udvidelse af elementet.|
|Oprindeligt filnavn|NativeFileName|Native_file_name|Elementets oprindelige filnavn.|
|NativeMD5||Native_MD5|MD5-hash (128-bit hashværdi) for filstreamen.|
|NativeSHA256||Native_SHA_256|SHA256-hash (256-bit hashværdi) for filstreamen.|
|ND/ET Sortér: Udelader vedhæftede filer|NdEtSortExclAttach|ND_ET_sort_excl_attach|Sammenkædning af mailtrådsættet (ET) og ND-sættet (Near-duplicate). Dette felt bruges til effektiv sortering på gennemsynstidspunktet. Et **D** har præfikset ND-sæt, og et **E** har et præfiks til ET-sæt.|
|ND/ET-sortering: Herunder vedhæftede filer|NdEtSortInclAttach|ND_ET_sort_incl_attach|Sammenkædning af et mailtrådsæt (ET) og næsten dubletsæt (ND). Dette felt bruges til effektiv sortering på gennemsynstidspunktet. Et **D** har præfikset ND-sæt, og et **E** har et præfiks til ET-sæt. Hvert mailelement i et et-sæt efterfølges af de relevante vedhæftede filer.|
|Nær dubletsæt||ND_set|Elementer, der ligner pivottabellen, deler samme ND_set.|
|O365-forfattere||O365_authors|Forfatter fra SharePoint.|
|O365 oprettet af||O365_created_by|Oprettet af fra SharePoint.|
|O365-dato for oprettelse||O365_date_created|Oprettelsesdato fra SharePoint.|
|O365ModifiedDate||O365_date_modified|Den dato, hvor et dokument (eller en dokumentversion), der er indsamlet fra SharePoint eller OneDrive for Business, blev ændret. Dette er den samme ændringsdato som den, der vises i versionshistorikken i SharePoint- og OneDrive-brugeroplevelsen.|
|O365 ændret af||O365_modified_by|Ændret af fra SharePoint eller OneDrive.|
|Andre tilsynsførende|DedupedCustodians|Deduped_custodians|Liste over vogtere af dokumenter, der er nøjagtige dubletter (for mail, baseret på indhold, for dokumenter, baseret på hash).|
|Andre fil-id'er|DedupedFileIds|Deduped_file_IDs|Liste over fil-id'er for dokumenter, der er nøjagtige dubletter (for mail, baseret på indhold, for dokumenter, baseret på hash).|
|Andre stier|Dedupedcompoundpath|Deduped_compound_path|Liste over sammensatte stier til dokumenter, der er nøjagtige dubletter (mail: baseret på indhold, dokumenter: baseret på hash).|
|Overordnet id|Overordnet id|Parent_ID|Id'et for elementets overordnede.|
|ParentNode||Parent_node|Den nærmeste foregående mail i mailtråden.|
|Deltagerdomæner|DeltagerDomæner|Email_participant_domains|Liste over alle domæner for deltagere i en meddelelse.|
|Deltagere|Deltagere|Email_participants|Liste over alle deltagere i en meddelelse. f.eks. Afsender, Til, Cc, Bcc.|
|Pivot-id|PivotId|Pivot_ID|Id'et for en pivot.|
|Potentielt privilegeret|Potentieltprivilegeret|Potentially_privileged|Sand, hvis modellen til registrering af rettigheder for advokatklienter tager dokumentet i betragtning, der potentielt er privilegeret|
|Behandlingsstatus|Status for behandling|Error_code|Behandlingsstatus, efter at elementet blev føjet til et gennemsynssæt.|
|Læs fraktil|Læsepercentile||Læs fraktilen for dokumentet baseret på relevans.|
|Modtaget|Modtaget|Email_date_received|Den dato og det klokkeslæt, hvor mailen blev modtaget i UTC.|
|Antal modtagere||Recipient_count|Antallet af modtagere i meddelelsen.|
|Modtagerdomæner|Modtagerdomæner|Email_recipient_domains|Liste over alle domæner for modtagere af en meddelelse.|
|Modtagere|Modtagere|Email_recipients|Liste over alle modtagere af en meddelelse (Til, Cc, Bcc).|
|||Redacted_file_path|Stien til den redigerede erstatningsfil i eksporten.|
|||Redacted_text_path|Stien til erstatningen af den redigerede tekstfil i eksporten. Kun til intern Brug af Microsoft.|
|Relevanskode Sagsproblem 1||Relevance_tag_case_issue_1|Relevanskode Sag nr. 1 fra Relevans.|
|Relevansscore|Relevansscore||Relevansscore for et dokument baseret på relevans.|
|Relevanskode|Relevansmærke||Relevansscore for et dokument baseret på relevans.|
|Repræsentativt id|Repræsentant-id||Numerisk id for hvert sæt nøjagtige dubletter.|
|||Row_number|Rækkenummeret for elementet i indlæsningsfilen.|
|Afsender|Afsender|Email_sender|Afsenderfelt (fra) for meddelelsestyper. Formatet er **DisplayName \<SmtpAddress>**.|
|Afsender/forfatter|Afsenderauthor||Beregnet felt, der består af elementets afsender eller forfatter.|
|Afsenderdomæne|SenderDomain|Email_sender_domain|Afsenderens domæne.|
|Sendt|Sendt|Email_date_sent|Afsendelsesdatoen for meddelelsen.<br>Chats: Startdato fra transskriptionen|
|Angiv rækkefølge: Inklusive først|SetOrderInclusivesFirst|Set_order_inclusives_first|Sorteringsfelt - mail og vedhæftede filer: kontra kronologisk; dokumenter: pivoter først og derefter med faldende lighedsscore.|
|Angiv id||Set_ID|Dokumenter med lignende indhold (ND_set) eller mail i den samme mailtråd (Email_set) deler den samme Set_ID.|
|Lighedspercent||Similarity_percent|Angiver, hvor lignende et dokument er i forhold til pivot for det næsten duplikerede sæt.|
|Oprindelig filstørrelse|Størrelse|Native_size|Antallet af byte i det oprindelige element.|
|Emne|Emne|Email_subject|Meddelelsens emne.|
|Emne/titel|Emnenavn||Beregnet felt, der består af elementets emne eller titel.|
|Tags|Tags|Tags|Mærker anvendt i et korrektursæt.|
|Kanalnavn|Kanal|ChannelName|Dette er Navnet på Teams-kanalen. Gælder kun for Microsoft Teams-indhold.|
|Teamnavn|Teamnavn|Teamnavn|**Hold:** Navn på team<br>**Yammer:** Communitynavn|
|Liste over temaer|Liste over temaer|Themes_list|Listen Temaer beregnet til analyse.|
|Titel|Titel|Doc_title|Titel fra dokumentets metadata. Titel fra dokumentets metadata. For Teams- og Yammer-indhold er dette værdien fra egenskaben ConversationName.|
|Til|Til|Email_to|Til felt for meddelelsestyper. Formatet er **DisplayName\<SmtpAddress>**|
|Entydig i mailsæt|UniqueInEmailSet||**Falsk** , hvis der er en dublet af den vedhæftede fil i mailsættet.|
|Versionsgruppe-id||Version_Group_Id|Grupperer de forskellige versioner af det samme dokument.|
|VersionNumber||Version_Number|Versionsnummeret på et dokument, der er indsamlet fra SharePoint eller OneDrive for Business. Dette er det samme versionsnummer som det, der vises i versionshistorikken i SharePoint- og OneDrive-brugeroplevelsen.|
|Blev afhjulpet|WasRemediated|Was_Remediated|**Sand** , hvis elementet blev afhjælpet, ellers **false**.|
|Ordoptælling|WordCount|Word_count|Antal ord i elementet.|
|||||

> [!NOTE]
> Du kan finde flere oplysninger om egenskaber, der kan søges i, når du søger efter Office 365 indholdsplaceringer, når du indsamler data for en eDiscovery (Premium)-sag, under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).
