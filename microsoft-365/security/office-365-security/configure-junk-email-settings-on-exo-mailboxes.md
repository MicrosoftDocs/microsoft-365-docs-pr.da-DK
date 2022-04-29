---
title: Konfigurer indstillinger for uønsket mail i Exchange Online-postkasser
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om, hvordan de konfigurerer indstillingerne for uønsket mail i Exchange Online postkasser. Mange af disse indstillinger er tilgængelige for brugere i Outlook eller Outlook på internettet.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ac7ac0f40c24c81cf916917b1b87626e032f8055
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130883"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Konfigurer indstillinger for uønsket mail i Exchange Online-postkasser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 organisationer med postkasser i Exchange Online styres organisationens indstillinger for spam af Exchange Online Protection (EOP). Du kan få flere oplysninger under [Beskyttelse mod spam i EOP](anti-spam-protection.md).

Men der er også specifikke indstillinger for spam, som administratorer kan konfigurere på individuelle postkasser i Exchange Online:

> [!NOTE]
> EOP bruger nu sin egen mailflowleveringsagent til at distribuere meddelelser til mappen Uønsket mail i stedet for at bruge reglen for uønsket mail. Parameteren _Enabled_ på Cmdlet'en **Set-MailboxJunkEmailConfiguration** har ikke længere nogen effekt på mailflowet. EOP distribuerer meddelelser baseret på de handlinger, der er angivet i politikker til bekæmpelse af spam. Brugerens liste over Pengeskab afsendere og listen over blokerede afsendere fungerer fortsat som normalt.

- **Flyt meddelelser til mappen Uønsket mail baseret på politikker til bekæmpelse af spam**: Når en politik til bekæmpelse af uønsket mail er konfigureret med handlingen **Flyt meddelelse til mappen Uønsket mail** for at få en dom til filtrering af uønsket mail, flyttes meddelelsen til mappen Uønsket mail, når meddelelsen er leveret til postkassen. Du kan få flere oplysninger om domsfiltrering af spam i politikker til bekæmpelse af [spam under Konfigurer politikker for spam i EOP](configure-your-spam-filter-policies.md). Hvis zap (automatisk tømning) på nul timer bestemmer, at en leveret meddelelse er spam eller phish, flyttes meddelelsen til mappen Uønsket mail for **at flytte meddelelse til mappen Uønsket mail** med spamfiltrering af domshandlinger. Du kan få flere oplysninger om ZAP [under Automatisk rensning på nul timer (ZAP) i Exchange Online](zero-hour-auto-purge.md).

- **Indstillinger for uønsket mail, som brugerne selv konfigurerer i Outlook eller Outlook på internettet**: _Gruppen af afsendere af uønsket_ mail er listen over afsendere Pengeskab, listen over de Pengeskab modtagere og listen Over blokerede afsendere i hver postkasse. Posterne på disse lister bestemmer, om meddelelsen flyttes til mappen Indbakke eller Uønsket mail. Brugerne kan konfigurere samlingen safelist for deres egen postkasse i Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App). Administratorer kan konfigurere samlingen safelist på en hvilken som helst brugers postkasse.

EOP kan flytte meddelelser til mappen Uønsket mail baseret på domshandlingen for filtrering af uønsket mail **Flyt meddelelsen til mappen Uønsket mail** eller listen Blokerede afsendere i postkassen, og forhindre, at meddelelser leveres til mappen Uønsket mail (baseret på listen Pengeskab afsendere i postkassen).

Administratorer kan bruge Exchange Online PowerShell til at konfigurere poster i gruppen af sikre lister på postkasser (listen over Pengeskab afsendere, listen over Pengeskab modtagere og listen Over blokerede afsendere).

> [!NOTE]
> Meddelelser fra afsendere, som brugerne har føjet til deres egne Pengeskab Afsendere lister springer indholdsfiltrering over som en del af EOP (SCL er -1). Hvis du vil forhindre brugere i at føje poster til deres liste over afsendere af Pengeskab i Outlook, skal du bruge Gruppepolitik som nævnt [i afsnittet Om uønsket mail i Outlook](#about-junk-email-settings-in-outlook) senere i denne artikel. Politikfiltrering, indholdsfiltrering og Defender for Office 365 kontroller anvendes stadig på meddelelserne.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du kan kun bruge Exchange Online PowerShell til at udføre procedurerne i denne artikel. Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser i Exchange Online, før du kan udføre procedurerne i denne artikel. Du skal især have rollen **Mailmodtagere** (som er tildelt rollegrupperne **Organisationsadministration**, **Modtagerstyring** og **Brugerdefinerede mailmodtagere** som standard) eller rollen **Brugerindstillinger** (som som standard er tildelt rollegrupperne **Organisationsadministration** og **HelpDesk** ). Hvis du vil føje brugere til rollegrupper i Exchange Online, skal du se [Rediger rollegrupper i Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Bemærk, at brugere med standardtilladelser kan udføre de samme procedurer i deres egen postkasse, så længe de har [adgang til Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

- I hybridmiljøer, hvor EOP beskytter Exchange postkasser i det lokale miljø, skal du konfigurere regler for mailflow (også kaldet transportregler) i Exchange i det lokale miljø. Disse regler for mailflow oversætter dommen til filtrering af uønsket mail, så reglen for uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan finde flere oplysninger under [Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- Pengeskab afsendere af delte postkasser synkroniseres ikke til Azure AD og EOP til design.

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Brug Exchange Online PowerShell til at konfigurere samlingen af sikre lister i en postkasse

Samlingen af sikre lister i en postkasse indeholder listen over Pengeskab afsendere, listen Pengeskab modtagere og listen Over blokerede afsendere. Brugerne kan som standard konfigurere samlingen af lister på deres egen postkasse i Outlook eller Outlook på internettet. Administratorer kan bruge de tilsvarende parametre på **Set-MailboxJunkEmailConfiguration-cmdlet'en** til at konfigurere samlingen safelist på en brugers postkasse. Disse parametre er beskrevet i følgende tabel.

|Parameter på Set-MailboxJunkEmailConfiguration|indstilling for Outlook på internettet|
|---|---|
|_BlockedSendersAndDomains_|**Flyt mail fra disse afsendere eller domæner til mappen Uønsket mail**|
|_Kontakter, der er tillid til_|**Hav tillid til mail fra mine kontakter**|
|_TrustedListsOnly_|**Hav kun tillid til mailadresser fra adresser på listen over Pengeskab afsendere og domæner og Pengeskab adresselister**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Flyt ikke mail fra disse afsendere til mappen Uønsket mail**|

<sup>\*</sup>**Noter**:

- I Exchange Online genkendes **domæneposter** på listen Pengeskab Afsendere eller _TrustedSendersAndDomains_ ikke, så brug kun mailadresser. I enkeltstående EOP med katalogsynkronisering synkroniseres domænenavne ikke som standard, men du kan aktivere synkronisering for domæner. Du kan få flere oplysninger under [KB3019657](https://support.microsoft.com/help/3019657).
- Du kan ikke redigere listen Pengeskab modtagere direkte ved hjælp af cmdlet'en **Set-MailboxJunkEmailConfiguration** (parameteren _TrustedRecipientsAndDomains_ fungerer ikke). Du ændrer listen Pengeskab afsendere, og disse ændringer synkroniseres med listen Pengeskab modtagere.

Hvis du vil konfigurere samlingen safelist på en postkasse, skal du bruge følgende syntaks:

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Hvis du vil angive flere værdier og overskrive eksisterende poster for parametrene _BlockedSendersAndDomains_ og _TrustedSendersAndDomains_ , skal du bruge følgende syntaks: `"<Value1>","<Value2>"...`. Hvis du vil tilføje eller fjerne en eller flere værdier, uden at det påvirker andre eksisterende poster, skal du bruge følgende syntaks: `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

I dette eksempel konfigureres følgende indstillinger for samlingen af lister på Ori Epsteins postkasse:

- Føj værdien shopping@fabrikam.com til listen Over blokerede afsendere.
- Fjern værdien chris@fourthcoffee.com fra listen Pengeskab afsendere og listen over Pengeskab modtagere.
- Konfigurerer kontakter i mappen Kontakter, så de behandles som afsendere, der er tillid til.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

I dette eksempel fjernes domæne-contoso.com fra listen Blokerede afsendere i alle brugerpostkasser i organisationen.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Hvis brugeren aldrig har åbnet sin postkasse, får du muligvis vist en fejl, når du kører de forrige kommandoer. Hvis du vil undertrykke denne fejl for massehandlinger, skal du føje `-ErrorAction SilentlyContinue` til kommandoen **Set-MailboxJunkEmailConfiguration** .
> - Filteret Outlook uønsket mail har yderligere indstillinger for indsamling af sikre lister (føj f.eks **. automatisk personer, jeg sender mails til, på listen Pengeskab afsendere**). Du kan få flere oplysninger under [Brug filtre for uønsket mail til at styre, hvilke meddelelser du får vist](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Hvordan ved du, det virkede?

Brug en af følgende procedurer for at bekræfte, at du har konfigureret samlingen safelist i en postkasse:

- Erstat _\<MailboxIdentity\>_ med navnet, aliaset eller mailadressen på postkassen, og kør følgende kommando for at bekræfte egenskabsværdierne:

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Hvis listen over værdier er for lang, skal du bruge denne syntaks:

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>Om indstillinger for uønsket mail i Outlook

Hvis du vil aktivere, deaktivere og konfigurere de indstillinger for filteret for uønsket mail på klientsiden, der er tilgængelige i Outlook, skal du bruge Gruppepolitik. Du kan få flere oplysninger under [Administrative skabelonfiler (ADMX/ADML) og Office tilpasningsværktøj til Microsoft 365 Apps for enterprise, Office 2019 og Office 2016](https://www.microsoft.com/download/details.aspx?id=49030) og [Sådan installerer du indstillinger for uønsket mail, f.eks. listen Pengeskab afsendere, ved hjælp af Gruppepolitik](https://support.microsoft.com/help/2252421).

Når Outlook filter for uønsket mail er angivet til standardværdien **Ingen automatisk filtrering** i **Indstillinger for**\> **uønsket** \> **mail** i **hjemmet**\>, forsøger Outlook ikke at klassificere meddelelser som spam, men stadig bruger gruppen af sikre lister (listen Pengeskab afsendere, Pengeskab  Liste over modtagere og liste over blokerede afsendere) for at flytte meddelelser til mappen Uønsket mail efter levering. Du kan få flere oplysninger om disse indstillinger under [Oversigt over filteret for uønsket mail](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

> [!NOTE]
> I Microsoft 365 organisationer anbefaler vi, at du lader filteret for uønsket mail i Outlook være angivet til **Ingen automatisk filtrering** for at forhindre unødvendige konflikter (både positive og negative) med EOP's spamfiltreringsbesigelser.

Når Outlook filter for uønsket mail er angivet til **Lav** eller **Høj**, bruger Outlook filter til uønsket mail sin egen SmartScreen-filterteknologi til at identificere og flytte spam til mappen Uønsket mail. Denne spamklassificering er adskilt fra det niveau for spamsikkerhed ( SCL), der bestemmes af EOP. Faktisk ignorerer Outlook SCL'en fra EOP (medmindre EOP har markeret meddelelsen for at springe spamfiltrering over) og bruger sine egne kriterier til at afgøre, om meddelelsen er spam. Det er selvfølgelig muligt, at spam-dommen fra EOP og Outlook kan være den samme. Du kan få flere oplysninger om disse indstillinger under [Skift beskyttelsesniveauet i filteret for uønsket mail](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> I november 2016 holdt Microsoft op med at producere opdateringer af spamdefinitioner til SmartScreen-filtrene i Exchange og Outlook. De eksisterende SmartScreen-spamdefinitioner blev tilbage på plads, men deres effektivitet vil sandsynligvis blive forringet over tid. Du kan få flere oplysninger under [Udfasning af understøttelse af SmartScreen i Outlook og Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Det Outlook filter for uønsket mail kan derfor bruge postkassens safelist-samling og sin egen spamklassificering til at flytte meddelelser til mappen Uønsket mail.

Outlook og Outlook på internettet understøtter begge samlingen af sikre lister. Samlingen af sikre lister gemmes i Exchange Online postkasse, så ændringer i samlingen af lister på listen i Outlook vises i Outlook på internettet og omvendt.

## <a name="limits-for-junk-email-settings"></a>Grænser for indstillinger for uønsket mail

Gruppen af sikre lister (listen over Pengeskab afsendere, Pengeskab modtagere og listen Over blokerede afsendere), der er gemt i brugerens postkasse, synkroniseres også med EOP. Med katalogsynkronisering synkroniseres samlingen af sikre lister til Azure AD.

- Gruppen af sikre lister i brugerens postkasse har en grænse på 510 KB, som omfatter alle lister samt yderligere filterindstillinger for uønsket mail. Hvis en bruger overskrider denne grænse, modtager vedkommende en Outlook fejl, der ser sådan ud:

  > Der kan ikke føjes til serverens lister over uønsket mail. Du har overskredet den tilladte størrelse på serveren. Filteret for uønsket mail på serveren deaktiveres, indtil listerne over uønsket mail er blevet reduceret til den størrelse, som serveren tillader.

  Du kan få flere oplysninger om denne grænse, og hvordan du ændrer den, under [KB2669081](https://support.microsoft.com/help/2669081).

- Den synkroniserede safelist-samling i EOP har følgende synkroniseringsgrænser:
  - 1024 poster i alt på listen over Pengeskab afsendere, listen over Pengeskab modtagere og eksterne kontakter, hvis **Hav tillid til mail fra mine kontakter** er aktiveret.
  - 500 poster i alt på listen Over blokerede afsendere og listen Blokerede domæner.

  Når 1024-indgangsgrænsen er nået, sker følgende ting:

  - Listen stopper med at acceptere poster i PowerShell og Outlook på internettet, men der vises ingen fejl.

    Outlook brugere kan fortsætte med at tilføje mere end 1.024 poster, indtil de når den Outlook grænse på 510 KB. Outlook kan bruge disse ekstra poster, så længe et EOP-filter ikke blokerer meddelelsen før levering til postkassen (regler for mailflow, anti-spoofing osv.).

- Med katalogsynkronisering synkroniseres posterne for at Azure AD i følgende rækkefølge:
  1. Mailkontakter, hvis **Hav tillid til mail fra mine kontakter** er aktiveret.
  2. Listen Pengeskab Afsender og Pengeskab modtagerliste kombineres, de duplikeres og sorteres alfabetisk, når der foretages en ændring for de første 1024 poster.

  De første 1024 poster bruges, og relevante oplysninger stemples i brevhovederne.

  Poster over 1024, der ikke blev synkroniseret til Azure AD, behandles af Outlook (ikke Outlook på internettet), og der stemples ingen oplysninger i brevhovederne.

Som du kan se, reducerer aktivering af indstillingen **Hav tillid til mail fra mine kontakter** antallet af Pengeskab afsendere og Pengeskab modtagere, der kan synkroniseres. Hvis dette er et problem, anbefaler vi, at du bruger Gruppepolitik til at slå denne funktion fra:

- Filnavn: outlk16.opax
- Politikindstilling: **Hav tillid til mail fra kontakter**
