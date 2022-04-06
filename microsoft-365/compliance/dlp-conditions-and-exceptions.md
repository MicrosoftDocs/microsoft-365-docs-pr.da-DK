---
title: DLP-politikbetingelser, undtagelser og handlinger
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
recommendations: false
description: få mere at vide om DLP-politikbetingelser og -undtagelser
ms.openlocfilehash: 9b735d139950399fb80e9063e7d9fdd1176c2d2b
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500051"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>DLP-politikbetingelser, undtagelser og handlinger

Betingelser og undtagelser i DLP-politikker identificerer følsomme elementer, som politikken anvendes på. Handlinger definerer, hvad der sker som en følge af en betingelse om, at undtagelser opfyldes.

- Betingelser definerer, hvad der skal medtages
- Undtagelser definerer, hvad der skal udelades.
- Handlinger definerer, hvad der sker som følge af, at en betingelse eller undtagelse opfyldes

De fleste betingelser og undtagelser har én egenskab, der understøtter en eller flere værdier. Hvis DLP-politikken f.eks. anvendes på Exchange mails, kræver afsenderens betingelse afsenderen  af meddelelsen. Nogle betingelser har to egenskaber. F.eks.  omfatter brevhovedet En meddelelse et af disse ord kræver én egenskab til at angive brevhovedfeltet og en anden egenskab til at angive den tekst, der skal søges efter i sidehovedfeltet. Visse betingelser eller undtagelser har ingen egenskaber. Tilstanden Vedhæftet fil **er adgangskodebeskyttet og** søger blot efter vedhæftede filer i meddelelser, der er beskyttet med adgangskode.

Handlinger kræver typisk yderligere egenskaber. Når F.eks. DLP-politikreglen omdirigerer en meddelelse, skal du angive, hvor meddelelsen omdirigeres til.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Betingelser og undtagelser for DLP-politikker

Tabellerne i følgende afsnit beskriver de betingelser og undtagelser, der er tilgængelige i DLP.

- [Afsendere](#senders)
- [Modtagere](#recipients)
- [Meddelelses emne eller brødtekst](#message-subject-or-body)
- [Vedhæftede filer](#attachments)
- [Brevhoveder for meddelelser](#message-headers)
- [Meddelelsesegenskaber](#message-properties)

### <a name="senders"></a>Afsendere

Hvis du bruger afsenderadressen som en betingelse eller undtagelse, varierer det faktiske felt, hvor der søgt efter værdien, afhængigt af den konfigurerede afsenderadresseplacering. Som standard bruger DLP-reglerne brevhovedadressen som afsenderadresse.

![Billede af en mailoverskrift, der viser forskellen mellem konvolutadressen (P1) og sidehovedet (P2) adresse](../media/dlp-conditions-exceptions-meetinginvite-callouts.png)

På lejerniveau kan du konfigurere en afsenderadresseplacering, der skal bruges på tværs af alle regler, medmindre en enkelt regel tilsidesætter den. Hvis du vil indstille konfiguration af DLP-politik for lejer for at evaluere afsenderadressen fra konvolutten på tværs af alle regler, kan du køre følgende kommando:

```PowerShell
Set-PolicyConfig –SenderAddressLocation Envelope
```

For at konfigurere afsenderens adresseplacering på et DLP-regelniveau er parameteren _SenderAddressLocation_. De tilgængelige værdier er:

- **Brevhoved**: Undersøg kun afsendere i brevhovederne (f.eks. felterne **Fra, Afsender** **eller Svar til**). Dette er standardværdien.

- **Konvolut**: Undersøg kun afsendere fra meddelelseskonvoluten (mail fra-værdien, der blev brugt i SMTP-overførslen, som normalt er gemt i feltet **Retursti**).

- **Brevhoved eller konvolut** (`HeaderOrEnvelope`) Undersøg afsendere i brevhovedet og konvolutten.
<br>

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Afsenderen er|betingelse: *Fra* <br/> undtagelse: *ExceptIfFrom*|Adresser|Meddelelser, der sendes af de angivne postkasser, mailbrugere, mailkontakter eller Microsoft 365 grupper i organisationen.|
|Afsenderen er medlem af |_FromMemberOf_ <br/> _ExceptIfFromMemberOf_|Adresser|Meddelelser, der sendes af et medlem af den angivne distributionsgruppe, mailaktiverede sikkerhedsgruppe eller Microsoft 365 distributionsgruppe.|
|Afsenders IP-adresse er|betingelse: *SenderIPRanges*<br/> undtagelse: *ExceptIfSenderIPRanges*|IPAddressRanges|Meddelelser, hvor afsenderens IP-adresse svarer til den angivne IP-adresse, eller falder inden for det angivne IP-adresseområde.|
|Afsenderadresse indeholder ord|betingelse: *FromAddressContainsWords* <br/> undtagelse: *ExceptIfFromAddressContainsWords*|Ord|Meddelelser, der indeholder de angivne ord i afsenderens mailadresse.|
|Afsenderadresse matcher mønstre|betingelse: *FromAddressMatchesPatterns* <br/> undtagelse: *ExceptFromAddressMatchesPatterns*|Mønstre|Meddelelser, hvor afsenderens mailadresse indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Afsenderdomæne er|betingelse: *SenderDomainIs* <br/> undtagelse: *ExceptIfSenderDomainIs*|DomainName|Meddelelser, hvor domænet for afsenderens mailadresse svarer til den angivne værdi. Hvis du skal finde afsenderdomæner, der  indeholder det angivne domæne (f.eks. et underdomæne til et domæne), skal du bruge betingelsen Afsenderadresse **svarer(***FromAddressMatchesPatterns*) og angive domænet ved hjælp af syntaksen: '\.domaincom\.$'.|
|Afsenderområde|betingelse: *FromScope* <br/> undtagelse: *ExceptIfFromScope*|UserScopeFrom|Meddelelser, der sendes af enten interne eller eksterne afsendere.|
|Afsenderens angivne egenskaber omfatter et af disse ord|betingelse: *SenderADAttributeContainsWords* <br/> undtagelse: *ExceptIfSenderADAttributeContainsWords*|Første egenskab: `ADAttribute` <p> Anden egenskab: `Words`|Meddelelser, hvor den angivne Active Directory-attribut for afsenderen indeholder et af de angivne ord.|
|Afsenderens angivne egenskaber svarer til disse tekstmønstre|betingelse: *SenderADAttributeMatchesPatterns* <br/> undtagelse: *ExceptIfSenderADAttributeMatchesPatterns*|Første egenskab: `ADAttribute` <p> Anden egenskab: `Patterns`|Meddelelser, hvor den angivne Active Directory-attribut for afsenderen indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|

### <a name="recipients"></a>Modtagere

<br>

****

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Modtageren er|betingelse: *SentTo* <br/> undtagelse: *ExceptIfSentTo*|Adresser|Meddelelser, hvor en af modtagerne er den angivne postkasse, mailbruger eller mailkontakt i organisationen. Modtagerne kan være i felterne **Til**, **Cc** eller **Bcc** i meddelelsen.|
|Modtagerdomæne er|betingelse: *RecipientDomainIs* <br/> undtagelse: *ExceptIfRecipientDomainIs*|DomainName|Meddelelser, hvor domænet for modtagerens mailadresse svarer til den angivne værdi.|
|Modtageradresse indeholder ord|betingelse: *AnyOfRecipientAddressContainsWords* <br/> undtagelse: *ExceptIfAnyOfRecipientAddressContainsWords*|Ord|Meddelelser, der indeholder de angivne ord i modtagerens mailadresse. <br/>**Bemærk**! Denne betingelse omfatter ikke meddelelser, der sendes til modtagerens proxyadresser. Det svarer kun til meddelelser, der sendes til modtagerens primære mailadresse.|
|Modtageradresse matcher mønstre|betingelse: *AnyOfRecipientAddressMatchesPatterns* <br/> undtagelse: *ExceptIfAnyOfRecipientAddressMatchesPatterns*|Mønstre|Meddelelser, hvor en modtagers mailadresse indeholder tekstmønstre, der svarer til de angivne regulære udtryk. <br/> **Bemærk**! Denne betingelse omfatter ikke meddelelser, der sendes til modtagerens proxyadresser. Det svarer kun til meddelelser, der sendes til modtagerens primære mailadresse.|
|Sendt til medlem af|betingelse: *SentToMemberOf* <br/> undtagelse: *ExceptIfSentToMemberOf*|Adresser|Meddelelser, der indeholder modtagere, som er medlemmer af den angivne distributionsgruppe, mailaktiverede sikkerhedsgruppe eller Microsoft 365 distributionsgruppe. Gruppen kan være i **felterne Til**, **Cc** eller **Bcc** i meddelelsen.|
|Modtagerens angivne egenskaber omfatter et af disse ord |_RecipientADAttributeContainsWords_ <br/> _ExceptIfRecipientADAttributeContainsWords_|Første egenskab: `ADAttribute` <p> Anden egenskab: `Words`|Meddelelser, hvor den angivne Active Directory-attribut for en modtager indeholder et af de angivne ord. <p> Bemærk, at **attributten** Land kræver en landekode på to bogstaver (f.eks. DE for Germany).|
|Modtagerens angivne egenskaber svarer til disse tekstmønstre |_RecipientADAttributeMatchesPatterns_ <br/> _ExceptIfRecipientADAttributeMatchesPatterns_|Første egenskab: `ADAttribute` <p> Anden egenskab: `Patterns`|Meddelelser, hvor den angivne Active Directory-attribut for en modtager indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|

### <a name="message-subject-or-body"></a>Meddelelses emne eller brødtekst

<br>

****

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Emnet indeholder ord eller udtryk|betingelse: *SubjectContainsWords* <br/> undtagelse: *ExceptIf SubjectContainsWords*|Ord|Meddelelser med de angivne ord i feltet Emne.|
|Emnet matcher mønstre|betingelse: *SubjectMatchesPatterns* <br/> undtagelse: *ExceptIf SubjectMatchesPatterns*|Mønstre|Meddelelser, hvor feltet Emne indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Indhold indeholder|betingelse: *ContentContainsSensitiveInformation* <br/> undtagelse *ExceptIfContentContainsSensitiveInformation*|SensitiveInformationTypes|Meddelelser eller dokumenter, der indeholder følsomme oplysninger som defineret af politikker til forebyggelse af datatab (DLP).|
|Emne eller Brødtekst matcher mønster|betingelse: *SubjectOrMatchyMatchesPatterns* <br/> undtagelse: *ExceptIfSubjectOrKartyMatchesPatterns*|Mønstre|Meddelelser, hvor emnefeltet eller brødteksten indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Emne eller Brødtekst indeholder ord|betingelse: *SubjectOrWordsyContainsWords* <br/> undtagelse: *ExceptIfSubjectOrWordsyContainsWords*|Ord|Meddelelser med de angivne ord i emnefeltet eller meddelelsesteksten|
|

### <a name="attachments"></a>Vedhæftede filer

<br>

****

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Vedhæftet fil er beskyttet med adgangskode|betingelse: *DocumentIsPasswordProtected* <br/> undtagelse: *ExceptIfDocumentIsPasswordProtected*|ingen|Meddelelser, hvor en vedhæftet fil er beskyttet med adgangskode (og derfor ikke kan scannes). Registrering af adgangskoder virker kun for Office- .zip- og .7z-filer.|
|Filtypenavnet for den vedhæftede fil er|betingelse: *ContentExtensionMatchesWords* <br/> undtagelse: *ExceptIfContentExtensionMatchesWords*|Ord|Meddelelser, hvor filtypenavnet for en vedhæftet fil svarer til et af de angivne ord.|
|Indholdet af vedhæftede filer i mails kan ikke scannes|betingelse: *DocumentIsUnsupported* <br/>undtagelse: *ExceptIf DocumentIsUnsupported*|i/t|Meddelelser, hvor en vedhæftet fil ikke oprindeligt blev genkendt af Exchange Online.|
|Scanningen af eventuelle vedhæftede filers indhold blev ikke fuldført|betingelse: *ProcessingLimitExceeded* <br/> undtagelse: *ExceptIfProcessingLimitExceeded*|i/t|Meddelelser, hvor regelprogrammet ikke kunne udføre scanningen af de vedhæftede filer. Du kan bruge denne betingelse til at oprette regler, der arbejder sammen for at identificere og behandle meddelelser, hvor indholdet ikke kunne scannes fuldstændigt.|
|Dokumentnavn indeholder ord|betingelse: *DocumentNameMatchesWords* <br/> undtagelse: *ExceptIfDocumentNameMatchesWords*|Ord|Meddelelser, hvor navnet på en vedhæftet fil svarer til et af de angivne ord.|
|Dokumentnavn matcher mønstre|betingelse: *DocumentNameMatchesPatterns* <br/> undtagelse: *ExceptIfDocumentNameMatchesPatterns*|Mønstre|Meddelelser, hvor filnavnet på en vedhæftet fil indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Dokumentegenskab er|betingelse: *ContentPropertyContainsWords* <br/> undtagelse: *ExceptIfContentPropertyContainsWords*|Ord|Meddelelser eller dokumenter, hvor en vedhæftet fils filtypenavn svarer til et af de angivne ord.|
|Dokumentstørrelse er lig med eller større end|betingelse: *DocumentSizeOver* <br/> undtagelse: *ExceptIfDocumentSizeOver*|Størrelse|Meddelelser, hvor vedhæftede filer er større end eller lig med den angivne værdi.|
|Enhver vedhæftet fils indhold omfatter ethvert af disse ord|betingelse: *DocumentContainsWords* <br/> undtagelse: *ExceptIfDocumentContainsWords*|`Words`|Meddelelser, hvor en vedhæftet fil indeholder de angivne ord.|
|Indholdet af vedhæftede filer svarer til disse tekstmønstre|betingelse: *DocumentMatchesPatterns* <br/> undtagelse: *ExceptIfDocumentMatchesPatterns*|`Patterns`|Meddelelser, hvor en vedhæftet fil indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|

### <a name="message-headers"></a>Brevhoveder

<br>

****

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Sidehovedet indeholder ord eller udtryk|betingelse: *HeaderContainsWords* <br/> undtagelse: *ExceptIfHeaderContainsWords*|Hash-tabel|Meddelelser, der indeholder det angivne overskriftsfelt, og værdien af overskriftsfeltet indeholder de angivne ord.|
|Sidehoved matcher mønstre|betingelse: *HeaderMatchesPatterns* <br/> undtagelse: *ExceptIfHeaderMatchesPatterns*|Hash-tabel|Meddelelser, der indeholder det angivne overskriftsfelt, og værdien af overskriftsfeltet indeholder de angivne regulære udtryk.|

### <a name="message-properties"></a>Meddelelsesegenskaber

<br>

****

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Med prioritet|betingelse: *WithImportance* <br/> undtagelse: *ExceptIfWithImportance*|Prioritet|Meddelelser, der er markeret med det angivne prioritetsniveau.|
|Indholdstegnsæt indeholder ord|betingelse: *ContentCharacterSetContainsWords* <br/> *ExceptIfContentCharacterSetContainsWords*|Tegnsæt|Meddelelser, der har et eller flere af de angivne tegnsætnavne.|
|Har afsender tilsidesættelse|betingelse: *HasSenderOverride* <br/> undtagelse: *ExceptIfHasSenderOverride*|i/t|Meddelelser, hvor afsenderen har valgt at tilsidesætte en politik til forebyggelse af datatab (DLP). Du kan finde flere oplysninger om DLP-politikker [under Få mere at vide om forebyggelse af datatab](./dlp-learn-about-dlp.md)|
|Meddelelsestype svarer til|betingelse: *MessageTypeMatches* <br/> undtagelse: *ExceptIfMessageTypeMatches*|MessageType|Meddelelser af den angivne type. **Bemærk**! De tilgængelige meddelelsestyper er Autosvar, Automatisk videresendelse, Krypteret (S/MIME), Kalender, Tilladelsesstyret (rettighedsstyring), Telefonsvarer, Signeret, Kvittering for læsning og Godkendelsesanmodning. |
|Meddelelsens størrelse er større end eller lig med|betingelse: *MessageSizeOver* <br/> undtagelse: *ExceptIfMessageSizeOver*|`Size`|Meddelelser, hvor den samlede størrelse (meddelelse plus vedhæftede filer) er større end eller lig med den angivne værdi. **Bemærk**! Begrænsninger på meddelelsesstørrelser for postkasser evalueres før regler for mailflow. En meddelelse, der er for stor til en postkasse, afvises, før en regel med denne betingelse kan handle på meddelelsen.|
|

## <a name="actions-for-dlp-policies"></a>Handlinger for DLP-politikker

I denne tabel beskrives de handlinger, der er tilgængelige i DLP.

<br>

****

|handling i DLP|handlingsparametre i Microsoft 365 PowerShell|egenskabstype|beskrivelse|
|---|---|---|---|
|Angiv sidehoved|Sætoverskrift|Første egenskab: *Sidehovednavn* </br> Anden egenskab: *Overskriftsværdi*|Parameteren SetHeader angiver en handling for DLP-reglen, der tilføjer eller ændrer et hovedfelt og en værdi i brevhovedet. Denne parameter bruger syntaksen "HeaderName:HeaderValue". Du kan angive flere sidehovednavn og værdipar adskilt af kommaer|
|Fjern sidehoved|RemoveHeader|Første egenskab: *MessageHeaderField*</br> Anden egenskab: *Streng*|Parameteren RemoveHeader angiver en handling for DLP-reglen, der fjerner et sidehovedfelt fra brevhovedet. Denne parameter bruger syntaksen "Overskriftsnavn" eller "Overskriftsnavn:Overskriftsværdi". Du kan angive flere overskriftsnavne eller hovednavn og værdipar adskilt af kommaer|
|Omdiriger meddelelsen til bestemte brugere|*RedirectMessageTo*|Adresser|Omdirigerer meddelelsen til de angivne modtagere. Meddelelsen leveres ikke til de oprindelige modtagere, og der sendes ingen meddelelse til afsenderen eller de oprindelige modtagere.|
|Videresende meddelelsen til godkendelse til afsenderens leder|Moderat|Første egenskab: *ModerateMessageByManager*</br> Anden egenskab: *Boolesk*|Parameteren Moderat angiver en handling for DLP-reglen, der sender mailen til en redaktør. Dette parameter bruger syntaksen: @{ModerateMessageByManager = <$true \|$false>;|
|Videresende meddelelsen til godkendelse til bestemte godkendere|Moderat|Første egenskab: *ModerateMessageByUser*</br>Anden egenskab: *Adresser*|Parameteren Moderat angiver en handling for DLP-reglen, der sender mailen til en redaktør. Dette parameter bruger syntaksen: @{ ModerateMessageByUser = @("emailaddress1","emailaddress2",..."emailaddressN")}|
|Tilføj modtager|AddRecipients|Første egenskab: *Felt*</br>Anden egenskab: *Adresser*|Føjer en eller flere modtagere til feltet Til/Cc/Bcc i meddelelsen. Denne parameter bruger syntaksen: @{<AddToRecipients \|CopyTo \|BlindCopyTo> = "emailaddress"}|
|Tilføj afsenderens overordnede som modtager|AddRecipients|Første egenskab: *AddedManagerAction*</br>Anden egenskab: *Felt*|Føjer afsenderens overordnede til meddelelsen som den angivne modtagertype (Til, Cc, Bcc) eller omdirigerer meddelelsen til afsenderens chef uden at underrette afsenderen eller modtageren. Denne handling virker kun, hvis afsenderens Manager-attribut er defineret i Active Directory. Denne parameter bruger syntaksen: @{AddManagerAsRecipientType = "<To \|Cc \|Bcc>"}|
Forudindstillet emne|PrependSubject|String|Føjer den angivne tekst til starten af feltet Emne i meddelelsen. Overvej at bruge et mellemrum eller et kolon (:) som det sidste tegn i den angivne tekst for at adskille den fra den oprindelige emnetekst.</br>Hvis du vil forhindre, at den samme streng føjes til meddelelser, der allerede indeholder teksten i emnet (f.eks. svar), skal du tilføje undtagelsen "Emnet indeholder ord" (ExceptIfSubjectContainsWords) til reglen.|
|Anvend HTML-ansvarsfraskrivelse|ApplyHtmlDisclaimer|Første egenskab: *Tekst*</br>Anden egenskab: *Placering*</br>Tredje egenskab: *Fallback-handling*|Anvender den angivne HTML-ansvarsfraskrivelse på den nødvendige placering af meddelelsen.</br>Denne parameter bruger syntaksen: @{ Text = " " ; Placering = <Tilføjelse \|>; FallbackAction = <Ombryd \|Ignorer \|afvis> }|
|Fjern Office 365 kryptering af meddelelser og rettighedsbeskyttelse|RemoveRMSTemplate|i/t|Fjerner Office 365, der anvendes på en mail|
|Levere meddelelsen til den tilknyttede karantæne |_Karantæne_|i/t| Denne handling findes i øjeblikket **i offentlig prøveversion**. I denne fase vil mails, der er sat i karantæne af DLP-politikker, vise politiktype som ExchangeLager.</br> Leverer meddelelsen til karantæne i EOP. Du kan få mere at vide [under Meddelelser, der er sat i karantæne i EOP](/microsoft-365/security/office-365-security/quarantine-email-messages).|
|

<!--|Modify Subject|ModifySubject|PswsHashTable | Remove text from the subject line that matches a specific pattern and replace it with different text. See the example below. You can: </br>- **Replace** all matches in the subject with the replacement text </br>- **Append** to remove all matches in the subject and inserts the replacement text at the end of the subject. </br>- **Prepend** to remove all matches and inserts the replacement text at the beginning of the subject. See ModifySubject parameter in, /powershell/module/exchange/new-dlpcompliancerule|-->

