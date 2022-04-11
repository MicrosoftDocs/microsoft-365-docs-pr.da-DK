---
title: DLP-politikbetingelser, -undtagelser og -handlinger
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
description: få mere at vide om dlp-politikbetingelser og -undtagelser
ms.openlocfilehash: f4a3521d0e5aab73cc16d97e0aea9c5830d9ddec
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/11/2022
ms.locfileid: "64762051"
---
# <a name="dlp-policy-conditions-exceptions-and-actions"></a>DLP-politikbetingelser, -undtagelser og -handlinger

Betingelser og undtagelser i DLP-politikker identificerer følsomme elementer, som politikken anvendes på. Handlinger definerer, hvad der sker som følge af en undtagelsesbetingelse, der er opfyldt.

- Betingelser definerer, hvad der skal inkluderes
- Undtagelser definerer, hvad der skal udelades.
- Handlinger definerer, hvad der sker som følge af en betingelse eller undtagelse, der opfyldes

De fleste betingelser og undtagelser har én egenskab, der understøtter en eller flere værdier. Hvis DLP-politikken f.eks. anvendes på Exchange mails, kræver betingelsen **Afsenderen** er afsenderen af meddelelsen. Nogle betingelser har to egenskaber. **En meddelelsesoverskrift indeholder** f.eks. en af disse ordbetingelse, som kræver én egenskab for at angive meddelelsesoverskriftsfeltet og en anden egenskab for at angive den tekst, der skal søges efter i overskriftsfeltet. Nogle betingelser eller undtagelser har ingen egenskaber. Betingelsen **Vedhæftet fil er** f.eks. beskyttet med adgangskode og søger blot efter vedhæftede filer i meddelelser, der er beskyttet med adgangskode.

Handlinger kræver typisk yderligere egenskaber. Når DLP-politikreglen f.eks. omdirigerer en meddelelse, skal du angive, hvor meddelelsen omdirigeres til.
<!-- Some actions have multiple properties that are available or required. For example, when the rule adds a header field to the message header, you need to specify both the name and value of the header. When the rule adds a disclaimer to messages, you need to specify the disclaimer text, but you can also specify where to insert the text, or what to do if the disclaimer can't be added to the message. Typically, you can configure multiple actions in a rule, but some actions are exclusive. For example, one rule can't reject and redirect the same message.-->

## <a name="conditions-and-exceptions-for-dlp-policies"></a>Betingelser og undtagelser for DLP-politikker

Tabellerne i følgende afsnit beskriver de betingelser og undtagelser, der er tilgængelige i DLP.

- [Afsendere](#senders)
- [Modtagere](#recipients)
- [Meddelelsesemne eller meddelelsestekst](#message-subject-or-body)
- [Vedhæftede filer](#attachments)
- [Brevhoveder](#message-headers)
- [Meddelelsesegenskaber](#message-properties)

### <a name="senders"></a>Afsendere

Hvis du bruger afsenderadressen som en betingelse eller undtagelse, varierer det faktiske felt, hvor værdien søges efter, afhængigt af den konfigurerede afsenderadresseplacering. DLP-regler bruger som standard afsenderadressen som afsenderadresse.

![Billede af en mailheader, der viser forskellen mellem konvolutadressen (P1) og headeradressen (P2)](../media/dlp-conditions-exceptions-meetinginvite-callouts.png)

På lejerniveau kan du konfigurere en afsenderadresseplacering, der skal bruges på tværs af alle regler, medmindre den tilsidesættes af en enkelt regel. Hvis du vil angive konfigurationen af lejerens DLP-politik for at evaluere afsenderadressen fra konvolutten på tværs af alle regler, kan du køre følgende kommando:

```PowerShell
Set-PolicyConfig -SenderAddressLocation Envelope
```

Hvis du vil konfigurere afsenderens adresseplacering på et DLP-regelniveau, er parameteren *SenderAddressLocation*. De tilgængelige værdier er:

- **Header**: Undersøg kun afsendere i brevhovederne (f.eks. felterne **Fra**, **Afsender** eller **Svar til** ). Dette er standardværdien.

- **Konvolut**: Undersøg kun afsendere fra meddelelseskonvolutten (værdien **MAIL FROM** , der blev brugt i SMTP-overførslen, som typisk gemmes i feltet **Return-Path** ).

- **Brevhoved eller konvolut** (`HeaderOrEnvelope`) Undersøg afsendere i brevhovedet og brevkonvolutten.

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Afsenderen er|betingelse: *Fra* <br/><br/> undtagelse: *ExceptIfFrom*|Adresser|Meddelelser, der sendes af de angivne postkasser, mailbrugere, mailkontakter eller Microsoft 365 grupper i organisationen.|
|Afsenderen er medlem af |*Framedlem af* <br/><br/> *Undtagen hvis framedlem af*|Adresser|Meddelelser, der sendes af et medlem af den angivne distributionsgruppe, mailaktiverede sikkerhedsgruppe eller Microsoft 365 gruppe.|
|Afsenderens IP-adresse er|betingelse: *SenderIPRanges*<br/><br/> undtagelse: *ExceptIfSenderIPRanges*|IPAddressRanges|Meddelelser, hvor afsenderens IP-adresse svarer til den angivne IP-adresse eller falder inden for det angivne IP-adresseinterval.|
|Afsenderadressen indeholder ord|betingelse: *FromAddressContainsWords* <br/><br/> undtagelse: *ExceptIfFromAddressContainsWords*|Ord|Meddelelser, der indeholder de angivne ord i afsenderens mailadresse.|
|Afsenderadresse matcher mønstre|condition: *FromAddressMatchesPatterns* <br/><br/> undtagelse: *ExceptFromAddressMatchesPatterns*|Mønstre|Meddelelser, hvor afsenderens mailadresse indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Afsenderdomænet er|betingelse: *SenderDomainIs* <br/><br/> undtagelse: *ExceptIfSenderDomainIs*|Domainname|Meddelelser, hvor domænet for afsenderens mailadresse stemmer overens med den angivne værdi. Hvis du har brug for at finde afsenderdomæner, der *indeholder* det angivne domæne (f.eks. et underdomæne for et domæne), skal du bruge betingelsen **AfsenderadressematchesPatterns** og angive domænet ved hjælp af syntaksen: '\.domaincom\.$'.|
|Afsenderområde|betingelse: *FromScope* <br/><br/> undtagelse: *ExceptIfFromScope*|UserScopeFrom|Meddelelser, der sendes af enten interne eller eksterne afsendere.|
|Afsenderens angivne egenskaber omfatter et af disse ord|betingelse: *SenderADAttributeContainsWords* <br/><br/> undtagelse: *ExceptIfSenderADAttributeContainsWords*|Første egenskab: `ADAttribute` <br/><br/> Anden egenskab: `Words`|Meddelelser, hvor afsenderens angivne Active Directory-attribut indeholder et af de angivne ord.|
|Afsenderens angivne egenskaber stemmer overens med disse tekstmønstre|condition: *SenderADAttributeMatchesPatterns* <br/><br/> undtagelse: *ExceptIfSenderADAttributeMatchesPatterns*|Første egenskab: `ADAttribute` <br/><br/> Anden egenskab: `Patterns`|Meddelelser, hvor afsenderens angivne Active Directory-attribut indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|

### <a name="recipients"></a>Modtagere

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Modtageren er|betingelse: *SentTo* <br/><br/> exception: *ExceptIfSentTo*|Adresser|Meddelelser, hvor en af modtagerne er den angivne postkasse, mailbruger eller mailkontakt i organisationen. Modtagerne kan være i felterne **Til**, **Cc** eller **Bcc** i meddelelsen.|
|Modtagerdomænet er|condition: *RecipientDomainIs* <br/><br/> undtagelse: *ExceptIfRecipientDomainIs*|Domainname|Meddelelser, hvor domænet for modtagerens mailadresse stemmer overens med den angivne værdi.|
|Modtageradressen indeholder ord|condition: *AnyOfRecipientAddressContainsWords* <br/><br/> undtagelse: *ExceptIfAnyOfRecipientAddressContainsWords*|Ord|Meddelelser, der indeholder de angivne ord i modtagerens mailadresse. <br/><br/>**Bemærk**! Denne betingelse tager ikke højde for meddelelser, der sendes til modtagerproxyadresser. Den svarer kun til meddelelser, der sendes til modtagerens primære mailadresse.|
|Modtageradressen stemmer overens med mønstre|condition: *AnyOfRecipientAddressMatchesPatterns* <br/><br/> undtagelse: *ExceptIfAnyOfRecipientAddressMatchesPatterns*|Mønstre|Meddelelser, hvor en modtagers mailadresse indeholder tekstmønstre, der svarer til de angivne regulære udtryk. <br/><br/> **Bemærk**! Denne betingelse tager ikke højde for meddelelser, der sendes til modtagerproxyadresser. Den svarer kun til meddelelser, der sendes til modtagerens primære mailadresse.|
|Sendt til medlem af|betingelse: *SentToMemberOf* <br/><br/> undtagelse: *ExceptIfSentToMemberOf*|Adresser|Meddelelser, der indeholder modtagere, der er medlemmer af den angivne distributionsgruppe, mailaktiverede sikkerhedsgruppe eller Microsoft 365 gruppe. Gruppen kan være i felterne **Til**, **Cc** eller **Bcc** i meddelelsen.|
|Modtagerens angivne egenskaber omfatter et af disse ord |*RecipientADAttributeContainsWords* <br/><br/> *ExceptIfRecipientADAttributeContainsWords*|Første egenskab: `ADAttribute` <br/><br/> Anden egenskab: `Words`|Meddelelser, hvor den angivne Active Directory-attribut for en modtager indeholder et af de angivne ord. <br/><br/> Bemærk, at attributten **Land** kræver landekodeværdien på to bogstaver (f.eks. DE for Tyskland).|
|Modtagerens angivne egenskaber stemmer overens med disse tekstmønstre |*RecipientADAttributeMatchesPatterns* <br/><br/> *ExceptIfRecipientADAttributeMatchesPatterns*|Første egenskab: `ADAttribute` <br/><br/> Anden egenskab: `Patterns`|Meddelelser, hvor den angivne Active Directory-attribut for en modtager indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|

### <a name="message-subject-or-body"></a>Meddelelsesemne eller meddelelsestekst

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Emne indeholder ord eller udtryk|betingelse: *SubjectContainsWords* <br/><br/> undtagelse: *ExceptIf SubjectContainsWords*|Ord|Meddelelser med de angivne ord i emnefeltet.|
|Emne matcher mønstre|condition: *SubjectMatchesPatterns* <br/><br/> undtagelse: *ExceptIf SubjectMatchesPatterns*|Mønstre|Meddelelser, hvor emnefeltet indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Indholdet indeholder|betingelse: *ContentContainsSensitiveInformation* <br/><br/> exception *ExceptIfContentContainsSensitiveInformation*|SensitiveInformationTypes|Meddelelser eller dokumenter, der indeholder følsomme oplysninger, som defineret af DLP-politikker (forebyggelse af datatab).|
|Mønster for match af emne eller brødtekst|condition: *SubjectOrBodyMatchesPatterns* <br/><br/> undtagelse: *ExceptIfSubjectOrBodyMatchesPatterns*|Mønstre|Meddelelser, hvor emnefeltet eller meddelelsesteksten indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Emne eller brødtekst indeholder ord|betingelse: *SubjectOrBodyContainsWords* <br/><br/> undtagelse: *ExceptIfSubjectOrBodyContainsWords*|Ord|Meddelelser med de angivne ord i emnefeltet eller meddelelsesteksten|

### <a name="attachments"></a>Vedhæftede filer

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Den vedhæftede fil er beskyttet med adgangskode|condition: *DocumentIsPasswordProtected* <br/><br/> undtagelse: *ExceptIfDocumentIsPasswordProtected*|Ingen|Meddelelser, hvor en vedhæftet fil er beskyttet med adgangskode (og derfor ikke kan scannes). Registrering af adgangskoder fungerer kun for Office dokumenter, .zip filer og .7z-filer.|
|Filtypenavnet for den vedhæftede fil er|condition: *ContentExtensionMatchesWords* <br/><br/> undtagelse: *ExceptIfContentExtensionMatchesWords*|Ord|Meddelelser, hvor filtypenavnet for en vedhæftet fil svarer til et af de angivne ord.|
|Indhold fra en vedhæftet fil kunne ikke scannes|betingelse: *DocumentIsUnsupported* <br/><br/>undtagelse: *ExceptIf DocumentIsUnsupported*|Nielsen|Meddelelser, hvor en vedhæftet fil ikke genkendes oprindeligt af Exchange Online.|
|Indholdet af en vedhæftet fil i en hvilken som helst mail blev ikke scannet|condition: *ProcessingLimitExceeded* <br/><br/> undtagelse: *ExceptIfProcessingLimitExceeded*|Nielsen|Meddelelser, hvor regelprogrammet ikke kunne fuldføre scanningen af de vedhæftede filer. Du kan bruge denne betingelse til at oprette regler, der arbejder sammen for at identificere og behandle meddelelser, hvor indholdet ikke kunne scannes fuldt ud.|
|Dokumentnavnet indeholder ord|condition: *DocumentNameMatchesWords* <br/><br/> undtagelse: *ExceptIfDocumentNameMatchesWords*|Ord|Meddelelser, hvor navnet på en vedhæftet fil svarer til et af de angivne ord.|
|Dokumentnavnet stemmer overens med mønstre|condition: *DocumentNameMatchesPatterns* <br/><br/> undtagelse: *ExceptIfDocumentNameMatchesPatterns*|Mønstre|Meddelelser, hvor en vedhæftet fils filnavn indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|
|Dokumentegenskaben er|condition: *ContentPropertyContainsWords* <br/><br/> undtagelse: *ExceptIfContentPropertyContainsWords*|Ord|Meddelelser eller dokumenter, hvor filtypenavnet for en vedhæftet fil svarer til et af de angivne ord.|
|Dokumentstørrelsen er lig med eller større end|betingelse: *DocumentSizeOver* <br/><br/> undtagelse: *ExceptIfDocumentSizeOver*|Størrelse|Meddelelser, hvor en vedhæftet fil er større end eller lig med den angivne værdi.|
|Alle vedhæftede filers indhold indeholder et af disse ord|betingelse: *DocumentContainsWords* <br/><br/> undtagelse: *ExceptIfDocumentContainsWords*|`Words`|Meddelelser, hvor en vedhæftet fil indeholder de angivne ord.|
|Alt indhold i vedhæftede filer svarer til disse tekstmønstre|condition: *DocumentMatchesPatterns* <br/><br/> undtagelse: *ExceptIfDocumentMatchesPatterns*|`Patterns`|Meddelelser, hvor en vedhæftet fil indeholder tekstmønstre, der svarer til de angivne regulære udtryk.|

### <a name="message-headers"></a>Brevhoveder

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Sidehovedet indeholder ord eller udtryk|betingelse: *HeaderContainsWords* <br/><br/> undtagelse: *ExceptIfHeaderContainsWords*|Hashtabel|Meddelelser, der indeholder det angivne overskriftsfelt, og værdien af det pågældende overskriftsfelt indeholder de angivne ord.|
|Header matcher mønstre|betingelse: *HeaderMatchesPatterns* <br/><br/> undtagelse: *ExceptIfHeaderMatchesPatterns*|Hashtabel|Meddelelser, der indeholder det angivne headerfelt, og værdien af det pågældende overskriftsfelt indeholder de angivne regulære udtryk.|

### <a name="message-properties"></a>Meddelelsesegenskaber

|betingelse eller undtagelse i DLP|parametre for betingelse/undtagelse i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Med prioritet|betingelse: *WithImportance* <br/><br/> undtagelse: *ExceptIfWithImportance*|Betydning|Meddelelser, der er markeret med det angivne vigtighedsniveau.|
|Indholdstegnsæt indeholder ord|betingelse: *ContentCharacterSetContainsWords* <br/><br/> *ExceptIfContentCharacterSetContainsWords*|Tegnsæt|Meddelelser, der har et af de angivne tegnsætnavne.|
|Har afsendertilsidesættelse|betingelse: *HasSenderOverride* <br/><br/> undtagelse: *ExceptIfHasSenderOverride*|Nielsen|Meddelelser, hvor afsenderen har valgt at tilsidesætte en DLP-politik (forebyggelse af datatab). Du kan finde flere oplysninger om DLP-politikker under [Få mere at vide om forebyggelse af datatab](./dlp-learn-about-dlp.md)|
|Forekomster af meddelelsestype|betingelse: *MessageTypeMatches* <br/><br/> undtagelse: *ExceptIfMessageTypeMatches*|Meddelelsestype|Meddelelser af den angivne type. **Bemærk**! De tilgængelige meddelelsestyper er Auto reply, Auto-forward, Encrypted (S/MIME), Calendaring, Permission controlled (rights management), Voicemail, Signed, Read receipt og Approval request. |
|Meddelelsesstørrelsen er større end eller lig med|betingelse: *MessageSizeOver* <br/><br/> undtagelse: *ExceptIfMessageSizeOver*|`Size`|Meddelelser, hvor den samlede størrelse (meddelelse plus vedhæftede filer) er større end eller lig med den angivne værdi. **Bemærk**! Grænser for meddelelsesstørrelse for postkasser evalueres før regler for mailflow. En meddelelse, der er for stor til en postkasse, afvises, før en regel med denne betingelse kan reagere på meddelelsen.|

## <a name="actions-for-dlp-policies"></a>Handlinger for DLP-politikker

I denne tabel beskrives de handlinger, der er tilgængelige i DLP.

|handling i DLP|handlingsparametre i Microsoft 365 PowerShell|egenskabstype|Beskrivelse|
|---|---|---|---|
|Angiv sidehoved|SetHeader|Første egenskab: *Overskriftsnavn* <br/><br/> Anden egenskab: *Overskriftsværdi*|Parameteren SetHeader angiver en handling for DLP-reglen, der tilføjer eller ændrer et headerfelt og en værdi i meddelelsesoverskriften. Denne parameter bruger syntaksen "HeaderName:HeaderValue". Du kan angive flere overskriftsnavne og værdipar adskilt af kommaer|
|Fjern sidehoved|Fjernoverskrift|Første egenskab: *MessageHeaderField*<br/><br/> Anden egenskab: *Streng*|Parameteren RemoveHeader angiver en handling for DLP-reglen, der fjerner et headerfelt fra meddelelsesoverskriften. Denne parameter bruger syntaksen "HeaderName" eller "HeaderName:HeaderValue". Du kan angive flere overskriftsnavne eller overskriftsnavne og værdipar adskilt af kommaer|
|Omdiriger meddelelsen til bestemte brugere|*RedirectMessageTo*|Adresser|Omdirigerer meddelelsen til de angivne modtagere. Meddelelsen leveres ikke til de oprindelige modtagere, og der sendes ingen meddelelse til afsenderen eller de oprindelige modtagere.|
|Videresend meddelelsen til godkendelse til afsenderens chef|Moderat|Første egenskab: *ModerateMessageByManager*<br/><br/> Anden egenskab: *Boolesk*|Parameteren Moderat angiver en handling for DLP-reglen, der sender mailen til en redaktør. Denne parameter bruger syntaksen: @{ModerateMessageByManager = <$true \|$false>;|
|Videresend meddelelsen til godkendelse til bestemte godkendere|Moderat|Første egenskab: *ModerateMessageByUser*<br/><br/>Anden egenskab: *Adresser*|Parameteren Moderat angiver en handling for DLP-reglen, der sender mailen til en redaktør. Denne parameter bruger syntaksen: @{ ModerateMessageByUser = @("emailaddress1","emailaddress2",..."emailaddressN")}|
|Tilføj modtager|Tilføj modtagere|Første egenskab: *Field*<br/><br/>Anden egenskab: *Adresser*|Føjer en eller flere modtagere til feltet Til/Cc/Bcc i meddelelsen. Denne parameter bruger syntaksen: @{<AddToRecipients \<CopyTo \| BlindCopyTo\> = "emailaddress"}|
|Tilføj afsenderens chef som modtager|Tilføj modtagere|Første egenskab: *AddedManagerAction*<br/><br/>Anden egenskab: *Field*|Føjer afsenderens chef til meddelelsen som den angivne modtagertype (Til, Cc, Bcc) eller omdirigerer meddelelsen til afsenderens leder uden at give afsenderen eller modtageren besked. Denne handling fungerer kun, hvis afsenderens lederattribut er defineret i Active Directory. Denne parameter bruger syntaksen: @{AddManagerAsRecipientType = "\<To \| Cc \| Bcc\>"}|
Forudindstillet emne|PrependSubject|String|Tilføjer den angivne tekst i starten af emnefeltet i meddelelsen. Overvej at bruge et mellemrum eller et kolon (:) som det sidste tegn i den angivne tekst for at adskille den fra den oprindelige emnetekst.<br/><br/>Hvis du vil forhindre, at den samme streng føjes til meddelelser, der allerede indeholder teksten i emnet (f.eks. svar), skal du føje undtagelsen "Emnet indeholder ord" (ExceptIfSubjectContainsWords) til reglen.|
|Anvend HTML-ansvarsfraskrivelse|AnvendHtmlDisclaimer|Første egenskab: *Tekst*<br/><br/>Anden egenskab: *Placering*<br/><br/>Tredje egenskab: *Fallback-handling*|Anvender den angivne HTML-ansvarsfraskrivelse på den påkrævede placering af meddelelsen.<br/><br/>Denne parameter bruger syntaksen: @{ Text = " " ; Placering = \<Append \| Prepend\>; FallbackAction = \<Wrap \| Ignore \| Reject\> }|
|Fjern Office 365 meddelelsekryptering og rettighedsbeskyttelse|RemoveRMSTemplate|Nielsen|Fjerner Office 365 kryptering, der er anvendt på en mail|
|Levér meddelelsen til den hostede karantæne |*Karantæne*|Nielsen| Denne handling er i øjeblikket en **offentlig prøveversion**. I denne fase viser mails, der er sat i karantæne af DLP-politikker, politiktypen som ExchangeTransportRule.<br/><br/> Leverer meddelelsen til karantænen i EOP. Du kan få flere oplysninger under [Karantænelagrede mails i EOP](/microsoft-365/security/office-365-security/quarantine-email-messages).|

<!--|Modify Subject|ModifySubject|PswsHashTable | Remove text from the subject line that matches a specific pattern and replace it with different text. See the example below. You can: <br/><br/>- **Replace** all matches in the subject with the replacement text <br/><br/>- **Append** to remove all matches in the subject and inserts the replacement text at the end of the subject. <br/><br/>- **Prepend** to remove all matches and inserts the replacement text at the beginning of the subject. See ModifySubject parameter in, /powershell/module/exchange/new-dlpcompliancerule|-->
