---
title: Konfigurere indstillinger for uønsket mail Exchange Online postkasser
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
description: Administratorer kan lære, hvordan de konfigurerer indstillingerne for uønsket mail Exchange Online postkasser. Mange af disse indstillinger er tilgængelige for brugere i Outlook eller Outlook på internettet.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9e2db8fc6c88e3945081d3b2800aa5ea9cd57a11
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682455"
---
# <a name="configure-junk-email-settings-on-exchange-online-mailboxes"></a>Konfigurere indstillinger for uønsket mail Exchange Online postkasser

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online kontrolleres organisatoriske antispamindstillinger af Exchange Online Protection (EOP). Du kan finde flere oplysninger [under Beskyttelse mod uønsket post i EOP](anti-spam-protection.md).

Men der er også specifikke antispamindstillinger, som administratorer kan konfigurere for individuelle postkasser i Exchange Online:

> [!NOTE]
> EOP bruger nu sin egen agent til levering af mailflow til at distribuere meddelelser til mappen Uønsket mail i stedet for at bruge reglen om uønsket mail. _Parameteren_ Enabled på **cmdlet'en Set-MailboxJunkEmailConfiguration** har ikke længere nogen indflydelse på mailflowet. EOP sender meddelelser baseret på de handlinger, der er angivet i antispampolitikker. Brugerens liste over Pengeskab og listen over blokerede afsendere fungerer fortsat som normalt.

- Flyt meddelelser til mappen Uønsket mail baseret på **antispampolitikker**: Når en politik for uønsket post er konfigureret med handlingen Flyt meddelelsen til mappen Uønsket **mail for at** få en spamfiltreringskonstering, flyttes meddelelsen til mappen Uønsket mail, når meddelelsen leveres til postkassen. Du kan finde flere oplysninger om konfigurering af spamfiltrering i [antispam-politikker i Konfigurer politikker for uønsket post i EOP](configure-your-spam-filter-policies.md). Hvis automatisk tømning uden time (ZAP) afgør, at en leveret meddelelse er spam eller phish, flyttes meddelelsen til mappen Uønsket **mail for at** flytte meddelelsen til mappen Uønsket mail for at filtrere spam efter handlinger, hvor der modtages uønsket mail. Du kan finde flere oplysninger om ZAP [under Automatisk tømning uden for time (ZAP) Exchange Online](zero-hour-auto-purge.md).

- **Indstillinger for uønsket** mail, som brugerne konfigurerer for sig selv i Outlook eller Outlook på internettet: Listen  over sikre lister er listen Pengeskab Afsendere, listen Pengeskab-modtagere og listen over blokerede afsendere på hver postkasse. Posterne på disse lister afgør, om meddelelsen flyttes til indbakken eller mappen Uønsket mail. Brugerne kan konfigurere samlingen af sikre lister for deres egen postkasse i Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App). Administratorer kan konfigurere samlingen af sikre lister på en brugers postkasse.

EOP kan flytte meddelelser til mappen Uønsket mail baseret på handlingen med spamfiltrering Flyt meddelelsen til  mappen Uønsket mail eller listen over blokerede afsendere på postkassen, og forbyd, at meddelelser leveres til mappen Uønsket mail (baseret på listen Pengeskab Afsendere på postkassen).

Administratorer kan bruge Exchange Online PowerShell til at konfigurere poster i gruppen af postkasser, der er tillid til (listen Pengeskab-afsendere, listen Pengeskab-modtagere og listen over blokerede afsendere).

> [!NOTE]
> Meddelelser fra afsendere, som brugerne har føjet til deres egne lister over Pengeskab-afsendere, springer filtrering af indhold over som en del af EOP (SCL er -1). Hvis du vil forhindre brugere i at føje poster til deres liste over Pengeskab-afsendere i Outlook, skal du bruge Gruppepolitik som nævnt i afsnittet Om uønsket mail [Outlook](#about-junk-email-settings-in-outlook) senere i denne artikel. Politikfiltrering, indholdsfiltrering og Defender Office 365 kontrol anvendes stadig på meddelelserne.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du kan kun bruge Exchange Online PowerShell til at udføre procedurerne i denne artikel. Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Du skal have tildelt tilladelser i Exchange Online, før du kan udføre procedurerne i denne artikel. Du skal specifikt have rollen **Postmodtagere** (som er tildelt rollegrupperne  Organisationsadministration  **, Modtageradministration** og Brugerdefinerede postmodtagere som standard) eller rollen Brugerindstillinger (som er tildelt rollegrupperne Organisationsadministration  og **Helpdesk** som standard). Hvis du vil føje brugere til rollegrupper Exchange Online, skal du [se Rediger rollegrupper Exchange Online](/Exchange/permissions-exo/role-groups#modify-role-groups). Bemærk, at brugere med standardtilladelser kan udføre de samme procedurer på deres egen postkasse, så længe de har adgang til [Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell).

- I hybridmiljøer, hvor EOP beskytter lokale Exchange-postkasser, skal du konfigurere regler for mailflow (også kaldet transportregler) i lokale Exchange. Disse regler for mailflow oversætter reglen om spamfiltrering for EOP, så reglen om uønsket mail i postkassen kan flytte meddelelsen til mappen Uønsket mail. Du kan få mere at [vide under Konfigurer EOP til at levere spam til mappen Uønsket mail i hybridmiljøer](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- Pengeskab afsendere til delte postkasser synkroniseres ikke til Azure AD og EOP tilses af designet.

## <a name="use-exchange-online-powershell-to-configure-the-safelist-collection-on-a-mailbox"></a>Brug Exchange Online PowerShell til at konfigurere samlingen af sikre lister på en postkasse

Samlingen med sikre lister på en postkasse Pengeskab listen over afsendere, listen Pengeskab modtagere og listen over blokerede afsendere. Som standard kan brugerne konfigurere samlingen af sikre lister på deres egen postkasse i Outlook eller Outlook på internettet. Administratorer kan bruge de tilsvarende parametre på **Set-MailboxJunkEmailConfiguration-cmdlet'en** til at konfigurere samlingen af sikre lister i en brugers postkasse. Disse parametre er beskrevet i følgende tabel.

|Parameter på Set-MailboxJunkEmailConfiguration|Outlook på internettet indstilling|
|---|---|
|_BlockedSendersAndDomains_|**Flyt mail fra disse afsendere eller domæner til mappen Uønsket mail**|
|_ContactsTrusted_|**Hav tillid til mail fra mine kontakter**|
|_TrustedListsOnly_|**Hav kun tillid til mails fra adresser Pengeskab listen over afsendere og domæner og Pengeskab adresselister**|
|_TrustedSendersAndDomains_<sup>\*</sup>|**Flyt ikke mail fra disse afsendere til mappen Uønsket mail**|

<sup>\*</sup>**Bemærkninger**:

- I Exchange Online bliver domæneposterne  på listen Pengeskab-afsendere eller _Parameteren TrustedSendersAndDomains_ ikke genkendt, så brug kun mailadresser. I separat EOP med katalogsynkronisering synkroniseres domæneposter ikke som standard, men du kan aktivere synkronisering for domæner. Du kan finde flere oplysninger [i KB3019657](https://support.microsoft.com/help/3019657).
- Du kan ikke direkte ændre listen **Pengeskab-modtagere ved hjælp af cmdlet'en Set-MailboxJunkEmailConfiguration** (parameteren _TrustedRecipientsAndDomains_ fungerer ikke). Du redigerer Pengeskab afsendere, og disse ændringer synkroniseres med Pengeskab Modtagere.

Hvis du vil konfigurere samlingen af sikre lister i en postkasse, skal du bruge følgende syntaks:

```PowerShell
Set-MailboxJunkEmailConfiguration <MailboxIdentity> -BlockedSendersAndDomains <EmailAddressesOrDomains | $null> -ContactsTrusted <$true | $false> -TrustedListsOnly <$true | $false> -TrustedSendersAndDomains  <EmailAddresses | $null>
```

Hvis du vil angive flere værdier og overskrive eksisterende poster for parametrene _BlockedSendersAndDomains_ og _TrustedSendersAndDomains_ , skal du bruge følgende syntaks: `"<Value1>","<Value2>"...`. Hvis du vil tilføje eller fjerne en eller flere værdier uden at påvirke andre eksisterende poster, skal du bruge følgende syntaks: `@{Add="<Value1>","<Value2>"... ; Remove="<Value3>","<Value4>...}`

I dette eksempel konfigureres følgende indstillinger for sikker listesamling på Ori Epsteins postkasse:

- Føj værdien shopping@fabrikam.com til listen over blokerede afsendere.
- Fjern værdien chris@fourthcoffee.com listen Pengeskab Afsendere og listen Pengeskab Modtagere.
- Konfigurerer kontakter i mappen Kontakter, der skal behandles som afsendere, der er tillid til.

```PowerShell
Set-MailboxJunkEmailConfiguration "Ori Epstein" -BlockedSendersAndDomains @{Add="shopping@fabrikam.com"} -TrustedSendersAndDomains @{Remove="chris@fourthcoffee.com"} -ContactsTrusted $true
```

I dette eksempel fjernes domænepostkassen contoso.com listen over blokerede afsendere i alle brugerpostkasser i organisationen.

```PowerShell
$All = Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited; $All | foreach {Set-MailboxJunkEmailConfiguration $_.Name -BlockedSendersAndDomains @{Remove="contoso.com"}}
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-MailboxJunkEmailConfiguration](/powershell/module/exchange/set-mailboxjunkemailconfiguration).

> [!NOTE]
>
> - Hvis brugeren aldrig har åbnet sin postkasse, får du muligvis en fejl, når du kører de forrige kommandoer. Du kan undertrykke denne fejl ved massehandlinger ved `-ErrorAction SilentlyContinue` at føje den til **kommandoen Set-MailboxJunkEmailConfiguration** .
> - Filteret Outlook uønsket mail har yderligere indstillinger for sikker listesamling (f.eks. Tilføj automatisk personer, jeg sender mail til **Pengeskab Afsendere**). Få mere at vide under Brug [filtre mod uønsket mail til at styre, hvilke meddelelser du kan se](https://support.microsoft.com/office/274ae301-5db2-4aad-be21-25413cede077).

### <a name="how-do-you-know-this-worked"></a>Hvordan ved du, at det virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har konfigureret samlingen af sikre lister i en postkasse:

- Erstat _\<MailboxIdentity\>_ med postkassens navn, alias eller mailadresse, og kør følgende kommando for at bekræfte egenskabsværdierne:

  ```PowerShell
  Get-MailboxJunkEmailConfiguration -Identity "<MailboxIdentity>" | Format-List trusted*,contacts*,blocked*
  ```

  Hvis listen over værdier er for lang, skal du bruge denne syntaks:

  ```PowerShell
  (Get-MailboxJunkEmailConfiguration -Identity <MailboxIdentity>).BlockedSendersAndDomains
  ```

## <a name="about-junk-email-settings-in-outlook"></a>Om indstillinger for uønsket mail i Outlook

Hvis du vil aktivere, deaktivere og konfigurere indstillingerne for filteret mod uønsket mail på klientsiden, som findes i Outlook, skal du Gruppepolitik. Du kan finde flere oplysninger i Administrative skabelonfiler [(ADMX/ADML) og Office-tilpasningsværktøj til Microsoft 365 Apps for enterprise, Office 2019 og Office 2016](https://www.microsoft.com/download/details.aspx?id=49030) og Sådan installeres indstillinger for uønsket mail, f.eks. listen [over Pengeskab-afsendere, ved hjælp af Gruppepolitik](https://support.microsoft.com/help/2252421).

Når filteret Outlook  \>  \>  \> uønsket mail er indstillet til standardværdien Ingen automatisk  filtrering i Indstillinger for uønsket post i privat **mail forsøger Outlook** ikke at klassificere meddelelser som spam, men bruger stadig samlingen af sikre lister (listen Pengeskab-afsendere Pengeskab  Modtagerliste og Liste over blokerede afsendere) for at flytte meddelelser til mappen Uønsket mail efter levering. Du kan finde flere oplysninger om disse indstillinger under [Oversigt over filteret mod uønsket mail](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089).

Når filteret Outlook uønsket mail er indstillet til  Lav eller **Høj, bruger** Outlook-filteret mod uønsket mail sin egen SmartScreen-filterteknologi til at identificere og flytte spam til mappen Uønsket mail. Denne spamklassifikation er separat fra det SCL-niveau (spam confidence level), der bestemmes af EOP. Faktisk ignorerer Outlook SCL fra EOP (medmindre EOP har markeret meddelelsen for at springe spamfiltrering over) og bruger sine egne kriterier til at afgøre, om meddelelsen er spam. Selvfølgelig er det muligt, at spamfrafaldet fra EOP og Outlook kan være den samme. Du kan finde flere oplysninger om disse indstillinger [under Ændre beskyttelsesniveauet i filteret mod uønsket mail](https://support.microsoft.com/office/e89c12d8-9d61-4320-8c57-d982c8d52f6b).

> [!NOTE]
> I november 2016 stoppede Microsoft med at producere spamdefinitionsopdateringer til SmartScreen-filtre i Exchange og Outlook. De eksisterende SmartScreen-spamdefinitioner bevares, men deres effektivitet vil sandsynligvis forringes med tiden. Du kan finde flere oplysninger [i Fraråde understøttelse af SmartScreen i Outlook og Exchange](https://techcommunity.microsoft.com/t5/exchange-team-blog/deprecating-support-for-smartscreen-in-outlook-and-exchange/ba-p/605332).

Derfor kan filteret Outlook uønsket mail bruge postkassens liste over sikre lister og sin egen spamklassifikation til at flytte meddelelser til mappen Uønsket mail.

Outlook og Outlook på internettet understøtter begge samlingen af sikre lister. Samlingen af sikre lister gemmes i postkassen Exchange Online, så ændringer i samlingen med sikre lister i Outlook vises Outlook på internettet og omvendt.

## <a name="limits-for-junk-email-settings"></a>Begrænsninger for indstillinger for uønsket mail

Den liste over sikre lister (listen Pengeskab-afsendere, Pengeskab-modtagere og listen over blokerede afsendere), der er gemt i brugerens postkasse, synkroniseres også med EOP. Med katalogsynkronisering synkroniseres samlingen af sikre lister med Azure AD.

- Samlingen af sikre lister i brugerens postkasse har en grænse på 510 KB, som omfatter alle lister samt yderligere filterindstillinger for uønsket mail. Hvis en bruger overskrider denne grænse, modtager brugeren en fejlmeddelelse Outlook, der ser sådan ud:

  > Lister over uønsket mail kan ikke føjes til serveren. Du er over den tilladte størrelse på serveren. Filteret mod uønsket mail på serveren deaktiveres, indtil dine lister over uønskede mails er blevet reduceret til den størrelse, serveren tillader.

  Du kan finde flere oplysninger om denne grænse, og hvordan du kan ændre den, under [KB2669081](https://support.microsoft.com/help/2669081).

- Den synkroniserede sikre listesamling i EOP har følgende begrænsninger for synkronisering:
  - 1024 poster i alt på listen Pengeskab Afsendere, listen Pengeskab Modtagere og eksterne kontakter, hvis Hav tillid til mail fra mine **kontakter er** aktiveret.
  - 500 poster i alt på listen over blokerede afsendere og blokerede domæner.

  Når grænsen for 1024-indtastning er nået, sker følgende:

  - Listen stopper med at acceptere indtastninger i PowerShell og Outlook på internettet, men der vises ingen fejl.

    Outlook brugere kan fortsætte med at tilføje mere end 1024 poster, indtil de når grænsen Outlook 510 KB. Outlook kan bruge disse yderligere poster, så længe et EOP-filter ikke blokerer meddelelsen før levering til postkassen (regler for mailflow, uønsket spoofing osv.).

- Med katalogsynkronisering synkroniseres posterne med Azure AD i følgende rækkefølge:
  1. Mailkontakter, hvis **Hav tillid til mail fra mine kontakter** er aktiveret.
  2. Listen Pengeskab afsender og Pengeskab Liste over modtagere kombineres, duplikeres og sorteres alfabetisk, når der foretages en ændring for de første 1024 poster.

  De første 1024 poster bruges, og relevante oplysninger er stemplet i brevhovederne.

  Poster over 1024, som ikke er synkroniseret med Azure AD, behandles af Outlook (ikke Outlook på internettet), og ingen oplysninger er stemplet i brevhovederne.

Som du kan se, reduceres antallet af  afsendere og modtagere, der kan synkroniseres, ved at aktivere indstillingen Hav tillid til mail fra mine kontakter Pengeskab Pengeskab afsendere og modtagere, der kan synkroniseres. Hvis dette er et problem, anbefaler vi at bruge Gruppepolitik til at slå denne funktion fra:

- Filnavn: outlk16.opax
- Politikindstilling: **Hav tillid til mail fra kontakter**
