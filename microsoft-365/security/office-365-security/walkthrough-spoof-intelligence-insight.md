---
title: Administrer spoofed afsendere ved hjælp af spoof intelligence-politikken og efterlignet intelligensindsigt
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Administratorer kan lære, hvordan de bruger efterlignet intelligenspolitik og efterlignet intelligensindsigt til at tillade eller blokere registrerede spoof-afsendere.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 62be716a9663820f90d5c4f125f4634b3b399547
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63588731"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Administrer efterlignede afsendere ved hjælp af efterlignet intelligenspolitik og efterlignet intelligensindsigt i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> I denne artikel beskrives den ældre oplevelse med efterlignet afsenderadministration, der bliver erstattet (efterlignet intelligencepolitik  på siden **Antispam-politikker**). Du kan finde flere oplysninger om den nye oplevelse (fanen **Spoofing** i lejerens tilladelses-/blokliste) under [Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser er indgående mails automatisk beskyttet mod spoofing af EOP pr. oktober 2018. EOP bruger **efterlignet intelligens som** en del af organisationens overordnede forsvar mod phishing. Du kan finde flere oplysninger [under Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

Standarden (og **kun)** efterlignet intelligenspolitik hjælper med at sikre, at forfalskede mails, der sendes af legitime afsendere, ikke bliver holder sig over i EOP-spamfiltre, samtidig med at dine brugere beskyttes mod spam- eller phishingangreb. Du kan også bruge **Spoof** intelligence-indsigt til hurtigt at afgøre, hvilke eksterne afsendere der legitimt sender dig ikke-godkendte mails (meddelelser fra domæner, der ikke passerer SPF-, DKIM- eller DMARC-kontroller).

Du kan administrere efterlignet intelligens i Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online  postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre efterlignet intelligenspolitik eller aktivere eller deaktivere efterlignet intelligens, skal du være medlem af rollegrupperne Organisationsadministration eller **Sikkerhedsadministrator**.
  - For skrivebeskyttet adgang til efterlignet intelligencepolitik skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- Indstillingerne for efterlignet intelligens er beskrevet i [Spoof-indstillinger i antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

- Du kan aktivere, deaktivere og konfigurere indstillingerne for efterlignet intelligens i antiphishing-politikker. Du kan finde instruktioner, der er baseret på dit abonnement, under et af følgende emner:

  - [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md).
  - [Konfigurer antiphishing-politikker i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

- For vores anbefalede indstillinger for efterlignet intelligens skal du se [Politikindstillinger for EOP-antiphishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="manage-spoofed-senders"></a>Administrer spoofed afsendere

Der er to måder at tillade og blokere efterlignede afsendere:

- [Brug af efterlignet intelligenspolitik](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Brug efterlignet intelligensindsigt](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Administrer efterlignede afsendere i efterlignet intelligenspolitik

> [!IMPORTANT]
> I denne artikel beskrives den ældre oplevelse med efterlignet afsenderadministration, der bliver erstattet (efterlignet intelligencepolitik  på siden **Antispam-politikker**). Du kan finde flere oplysninger om den nye oplevelse (fanen **Spoofing** i lejerens tilladelses-/blokliste) under [Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Antispam-politikker** skal du **vælge Efterlignet intelligencepolitik** ved at klikke på navnet.

   ![Vælg efterlignet intelligencepolitik.](../../media/anti-spam-settings-spoof-intelligence-policy.png)

3. I pop **op-vindue med efterlignet** intelligenspolitik, der vises, skal du foretage et af følgende valg:
   - **Vis mig afsendere, jeg allerede har gennemgået**
   - **Gennemse nye afsendere**

4. I pop **op-dialogboksen Beslut** , om disse afsendere har tilladelse til at efterligne dine brugere, der vises, skal du vælge en af følgende faner:
   - **Dine domæner**: Afsendere efterligner brugere i dine interne domæner.
   - **Eksterne domæner**: Afsendere spoofing af brugere i eksterne domæner.

5. Klik på ![udvid ikon.](../../media/scc-expand-icon.png) i kolonnen **Tilladt at efterligne?** og foretage et af følgende valg:
   - **Ja**: Tillad spoof-afsenderen.
   - **Nej**: Markér meddelelsen som efterlignet. Handlingen styres af standardpolitikken for phishing eller brugerdefinerede antiphishing-politikker. Du kan finde flere oplysninger [under Indstillinger for spoof i antiphishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

   ![Skærmbillede, der viser pop op-billedet af spoof-afsendere, og om afsenderen har tilladelse til at spoof.](../../media/spoof-allow-block-flyout.png)

   De kolonner og værdier, du kan se, er forklaret på følgende liste:

   - **Spoof-bruger**: Brugerkontoen, der bliver efterlignet. Dette er meddelelsesafsenderen i Fra-adressen (også kaldet adressen `5322.From` ), der vises i mailklienter. Gyldigheden af denne adresse kontrolleres ikke af SPF.
     - På fanen **Dine domæner indeholder** værdien en enkelt mailadresse, eller hvis kildemailserveren efterligner flere brugerkonti, indeholder den **mere end én**.
     - På fanen **Eksterne domæner** indeholder værdien domænet for den spoofede bruger, ikke den fulde mailadresse.

   - **Sender infrastruktur**: Det domæne, der blev fundet i et omvendt DNS-opslag (PTR-post) for kildemailserverens IP-adresse. Hvis kilde-IP-adressen ikke har en PTR-post, \<source IP\>identificeres den afsendende infrastruktur som /24 (f.eks. 192.168.100.100/24).

     Du kan finde flere oplysninger om meddelelseskilder og meddelelsesafsendere [i En oversigt over mailstandarder](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **# af meddelelser**: Antallet af meddelelser fra den afsendende infrastruktur til din organisation, der indeholder den angivne spoofed afsender eller afsendere inden for de seneste 30 dage.

   - **# af brugerklager**: Klager fra dine brugere mod denne afsender inden for de seneste 30 dage. Klager er normalt i form af uønskede indsendelser til Microsoft.

   - **Godkendelsesresultat**: En af følgende værdier:
      - **Bestået**: Afsenderen har overført mailgodkendelseskontrol for afsender (SPF eller DKIM).
      - **Mislykket**: Afsenderen kunne ikke kontrollere EOP-afsenderens godkendelse.
      - **Ukendt**: Resultatet af disse kontroller kendes ikke.

   - **Sidst set**: Den sidste dato, hvor en meddelelse blev modtaget fra den afsendende infrastruktur, der indeholder den efterlignede bruger.

   - **Har du tilladelse til at efterligne?**: De værdier, du ser her, er:
     - **Ja**: Meddelelser fra kombinationen af efterlignet bruger og afsendelsesinfrastruktur er tilladt og behandles ikke som efterlignet mail.
     - **Nej**: Meddelelser fra kombinationen af efterlignet bruger- og afsendelsesinfrastruktur er markeret som spoofed. Handlingen styres af standardpolitikken for phishing eller brugerdefinerede antiphishing-politikker (standardværdien er **Flyt meddelelsen til mappen Uønsket mail**). Du kan finde flere oplysninger i næste afsnit.

     - **Nogle brugere** (**kun dine** domæner): En afsendende infrastruktur er poofing af flere brugere, hvor nogle efterlignede brugere er tilladt, og andre ikke er. Brug fanen **Detaljeret** til at få vist de specifikke adresser.

6. Klik på **Gem**, når du er færdig.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>Brug PowerShell til at administrere efterlignede afsendere

> [!IMPORTANT]
> I denne artikel beskrives den ældre oplevelse med efterlignet afsenderadministration, der bliver erstattet (efterlignet intelligencepolitik  på siden **Antispam-politikker**). Du kan finde flere oplysninger om den nye oplevelse (fanen **Spoofing** i lejerens tilladelses-/blokliste) under [Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

For at få vist tilladte og blokerede afsendere i efterlignet intelligens skal du bruge følgende syntaks:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

I dette eksempel returneres detaljerede oplysninger om alle afsendere, der har tilladelse til at efterligne brugere på dine domæner.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Hvis du vil konfigurere tilladte og blokerede afsendere i efterlignet intelligens, skal du følge disse trin:

1. Registrere den aktuelle liste over registrerede efterlignede afsendere ved at skrive outputtet fra **Get-PhishFilterPolicy-cmdlet'en til en CSV-fil** ved at køre følgende kommando:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Rediger CSV-filen for at tilføje eller ændre følgende værdier:
   - **Afsender** (domæne i kildeserverens PTR-post eller IP/24-adresse)
   - **SpoofedUser**: En af følgende værdier:
     - Den interne brugers mailadresse.
     - Den eksterne brugers maildomæne.
     - En tom værdi, der **angiver, at** du vil blokere eller tillade alle spoofede meddelelser fra den angivne afsender, uanset spoofed mailadressen.
   - **AllowedToSpoof** (Ja eller Nej)
   - **SpoofType** (intern eller ekstern)

   Gem filen, læs filen, og gem indholdet som en variabel, der er navngivet `$UpdateSpoofedSenders` ved at køre følgende kommando:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Brug variablen `$UpdateSpoofedSenders` til at konfigurere efterlignet intelligencepolitik ved at køre følgende kommando:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Administrer efterlignede afsendere i efterlignet intelligensindsigt

> [!IMPORTANT]
> I denne artikel beskrives den ældre oplevelse med efterlignet afsenderadministration, der bliver erstattet (efterlignet intelligencepolitik  på siden **Antispam-politikker**). Du kan finde flere oplysninger om den nye oplevelse (fanen **Spoofing** i lejerens tilladelses-/blokliste) under [Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

1. I Security & Compliance Center skal du gå til **Dashboard til trusselsadministration**\>.

2. I rækken **Insights** skal du se efter et af følgende elementer:

   - **Sandsynligvis efterlignede domæner i** løbet af de seneste syv dage: Dette indsigt indikerer, at efterlignet intelligens er aktiveret (den er aktiveret som standard).
   - **Aktivér Spoof Protection**: Dette indsigt indikerer, at efterlignet intelligens er deaktiveret, og når du klikker på indsigten, kan du aktivere efterlignet intelligens.

3. Indsigten på dashboardet viser dig oplysninger som dette:

   ![Skærmbillede af efterlignet intelligensindsigt.](../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png)

   Dette indsigt har to tilstande:

   - **Insight-tilstand**: Hvis efterlignet intelligens er aktiveret, viser indsigten, hvor mange meddelelser, der er blevet påvirket af vores efterlignede intelligensegenskaber i løbet af de seneste syv dage.
   - **Hvad hvis-tilstand**: Hvis efterlignet intelligens er deaktiveret, viser indsigten, hvor mange meddelelser der *vil være blevet* påvirket af vores efterlignede intelligensegenskaber i løbet af de seneste syv dage.

   Uanset hvad er de efterlignede domæner, der vises i indsigten, opdelt i to **kategorier:** Mistænkelige domæner og **ikke-mistænkelige domæner**.

   - **Mistænkelige domæner**:
     - **Høj tillidsspoof**: Baseret på de historiske afsendelsesmønstre og domæners omdømme er vi stærkt sikre på, at domænerne er efterlignede, og meddelelser fra disse domæner er mere skadelige.
     - **Moderat tillidsspoof**: Baseret på historiske afsendelsesmønstre og domæners omdømme er vi moderat sikre på, at domænerne er efterlignede, og at meddelelser, der sendes fra disse domæner, er legitime. Falske positive er mere sandsynlige i denne kategori end højfortroligt spoof.
   - **Ikke-mistænkelige domæner**: Domænet kunne ikke eksplicit mailgodkendelse kontrollerer [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md). Men domænet bestod vores implicitte mailgodkendelseskontroller ([sammensat godkendelse](email-validation-and-authentication.md#composite-authentication)). Derfor blev der ikke taget nogen antispoofinghandling på meddelelsen.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Få vist detaljerede oplysninger om mistænkelige og uovervejede domæner

1. På Spoof intelligence-indsigt skal du  klikke på Mistænkelige domæner eller **Ikke-mistænkelige** domæner for at gå til **siden Spoof intelligence insight**. Siden **Spoof Intelligence Insight** indeholder følgende oplysninger:

   - **Efterlignet domæne**: Domænet for den spoofede bruger, der vises i feltet **Fra i** mailklienter. Denne adresse kaldes også for `5322.From` adressen.
   - **Infrastruktur**: Også kendt som _afsendende infrastruktur_. Domænet, der findes i et omvendt DNS-opslag (PTR-post) på kildemailserverens IP-adresse. Hvis kilde-IP-adressen ikke har en PTR-post, \<source IP\>identificeres den afsendende infrastruktur som /24 (f.eks. 192.168.100.100/24).
   - **Meddelelsesantal**: Antallet af meddelelser fra den afsendende infrastruktur til din organisation, der indeholder det angivne efterlignede domæne inden for de seneste 7 dage.
   - **Sidst set**: Den sidste dato, hvor en meddelelse blev modtaget fra den afsendende infrastruktur, der indeholder det efterlignede domæne.
   - **Spoof-type**: Denne værdi er **Ekstern**.
   - **Har du tilladelse til at efterligne?**: De værdier, du ser her, er:
     - **Ja**: Meddelelser fra kombinationen af efterlignet brugers domæne og afsendelsesinfrastruktur er tilladt og behandles ikke som efterlignet mail.
     - **Nej**: Meddelelser fra kombinationen af efterlignet brugers domæne og afsendelsesinfrastruktur er markeret som efterlignet. Handlingen styres af standardpolitikken for phishing eller brugerdefinerede antiphishing-politikker (standardværdien er **Flyt meddelelsen til mappen Uønsket mail**).

2. Vælg et element på listen for at få vist detaljer om domænet/sender infrastrukturparet i en pop op-pop op-pop-op. Oplysningerne omfatter:
   - Derfor har vi opdaget dette.
   - Det skal du gøre.
   - En domæneoversigt.
   - WhoIs data about the sender.
   - Lignende meddelelser, vi har set i din lejer fra den samme afsender.

   Herfra kan du også vælge at tilføje eller fjerne infrastrukturparret for domæne/afsendelse fra listen Tilladt tilladt for **spoof-afsender** . Du skal blot indstille til/fra-knappen tilsvarende.

   ![Skærmbillede af et domæne i detaljeruden efterlignet intelligensindsigt.](../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png)

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

For at bekræfte, at du har konfigureret efterlignet efterlignet intelligens med afsendere, der er tilladt og ikke har tilladelse til at spoof, skal du bruge et af følgende trin:

- **Samarbejde & mail** \> **Politikker & regler** \> **Trusselspolitikker** \> **Antispam**  \>  \>  \> i afsnittet Politikker efterlignet intelligenspolitik vælg Vis mig afsendere, jeg allerede har gennemset,  vælg fanen Dine domæner  eller Eksterne domæner, og bekræft værdien Tilladt at **efterligne?** for afsenderen.

- I PowerShell skal du køre følgende kommandoer for at få vist afsendere, der har tilladelse til og ikke har tilladelse til at spoof:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- I PowerShell skal du køre følgende kommando for at eksportere listen over alle spoofede afsendere til en CSV-fil:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
