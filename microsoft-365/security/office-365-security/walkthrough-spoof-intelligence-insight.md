---
title: Administrer spoofed afsendere ved hjælp af spoof intelligence-politikken og indsigt i spoof intelligence
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
description: Administratorer kan få mere at vide om, hvordan de bruger spoof intelligence-politikken og indsigt i spoof intelligence til at tillade eller blokere registrerede spoofed-afsendere.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 59f52e7fe10030283601aad86a1aa49ed91255ab
ms.sourcegitcommit: 363bdc517bd2564c6420cf21f352e97079f950e0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/22/2022
ms.locfileid: "65031791"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Administrer spoofed afsendere ved hjælp af spoof intelligence-politikken og indsigt i spoof intelligence i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> I denne artikel beskrives den ældre spoofed afsenderadministrationsoplevelse, der erstattes ( **spoof intelligence-politikken** på siden **Politikker til bekæmpelse af spam** ). Du kan få flere oplysninger om den nye oplevelse (fanen **Spoofing** på listen Over tilladte/blokerede lejere) [under Indsigt i Spoof intelligence i EOP](learn-about-spoof-intelligence.md).

I Microsoft 365 organisationer med postkasser i Exchange Online eller enkeltstående EOP-organisationer (Exchange Online Protection) uden Exchange Online postkasser beskyttes indgående mails automatisk mod spoofing af EOP fra oktober 2018. EOP bruger **spoof intelligence** som en del af din organisations overordnede forsvar mod phishing. Du kan få flere oplysninger under [Beskyttelse mod spoofing i EOP](anti-spoofing-protection.md).

**Standard-spoof intelligence-politikken** (og kun) hjælper med at sikre, at den forfalskede mail, der sendes af legitime afsendere, ikke bliver fanget i EOP-spamfiltre, samtidig med at dine brugere beskyttes mod spam- eller phishingangreb. Du kan også bruge **Spoof Intelligence-indsigten** til hurtigt at bestemme, hvilke eksterne afsendere der lovligt sender dig ikke-godkendte mails (meddelelser fra domæner, der ikke sender SPF-, DKIM- eller DMARC-kontroller).

Du kan administrere spoof intelligence på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online  postkasser).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre spoof intelligence-politikken eller aktivere eller deaktivere spoof intelligence, skal du være medlem af 
    -   **Organisationsadministration**
    -   **Konfiguration af sikkerhedsadministrator** <u>og</u> kun **visning** eller **kun visning af organisationsadministration**.
  - Hvis du vil have skrivebeskyttet adgang til spoof intelligence-politikken, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Indstillingerne for spoof intelligence er beskrevet i [Spoof-indstillinger i anti-phishing-politikker](set-up-anti-phishing-policies.md#spoof-settings).

- Du kan aktivere, deaktivere og konfigurere spoof intelligence-indstillingerne i politikker til bekæmpelse af phishing. Du kan finde instruktioner baseret på dit abonnement i et af følgende emner:

  - [Konfigurer politikker til bekæmpelse af phishing i EOP](configure-anti-phishing-policies-eop.md).
  - [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

- Du kan se vores anbefalede indstillinger for spoof intelligence under [EOP-politikindstillinger for anti-phishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="manage-spoofed-senders"></a>Administrer misvisende afsendere

Der er to måder at tillade og blokere spoofede afsendere på:

- [Brug spoof intelligence-politikken](#manage-spoofed-senders-in-the-spoof-intelligence-policy)
- [Brug spoof intelligence-indsigten](#manage-spoofed-senders-in-the-spoof-intelligence-insight)

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-policy"></a>Administrer spoofed afsendere i spoof intelligence-politikken

> [!IMPORTANT]
> I denne artikel beskrives den ældre spoofed afsenderadministrationsoplevelse, der erstattes ( **spoof intelligence-politikken** på siden **Politikker til bekæmpelse af spam** ). Du kan få flere oplysninger om den nye oplevelse (fanen **Spoofing** på listen Over tilladte/blokerede lejere) [under Indsigt i Spoof intelligence i EOP](learn-about-spoof-intelligence.md).

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du vælge **Spoof intelligence-politik** ved at klikke på navnet.

   :::image type="content" source="../../media/anti-spam-settings-spoof-intelligence-policy.png" alt-text="Muligheden for at vælge spoof intelligence-politikken" lightbox="../../media/anti-spam-settings-spoof-intelligence-policy.png":::

3. På pop **op-vinduet Spoof intelligence-politik** , der vises, skal du foretage et af følgende valg:
   - **Vis afsendere, jeg allerede har gennemset**
   - **Gennemse nye afsendere**

4. I pop op-vinduet **Beslut, om disse afsendere må spoof dine brugere** , der vises, skal du vælge en af følgende faner:
   - **Dine domæner**: Afsendere spoofing-brugere i dine interne domæner.
   - **Eksterne domæner**: Afsendere spoofing-brugere i eksterne domæner.

5. Klik på ![ikonet Udvid.](../../media/scc-expand-icon.png) i kolonnen **Tilladt at spoof?** og foretage en af følgende valg:
   - **Ja**: Tillad den spoofede afsender.
   - **Nej**: Markér meddelelsen som spoofed. Handlingen styres af standardpolitikken for anti-phishing eller brugerdefinerede politikker til bekæmpelse af phishing. Du kan få flere oplysninger under [Spoof-indstillinger i politikker til bekæmpelse af phishing](set-up-anti-phishing-policies.md#spoof-settings).

   :::image type="content" source="../../media/spoof-allow-block-flyout.png" alt-text="Pop op-vinduet spoofed afsendere, og om afsenderen har tilladelse til at spoof" lightbox="../../media/spoof-allow-block-flyout.png":::

   De kolonner og værdier, du får vist, er forklaret på følgende liste:

   - **Spoofed bruger**: Den brugerkonto, der bliver spoofed. Dette er meddelelsens afsender i fra-adressen (også kaldet adressen `5322.From` ), der vises i mailklienter. Gyldigheden af denne adresse kontrolleres ikke af SPF.
     - Under fanen **Dine domæner** indeholder værdien en enkelt mailadresse, eller hvis kildemailserveren spooferer flere brugerkonti, indeholder den **mere end én**.
     - Under fanen **Eksterne domæner** indeholder værdien domænet for den spoofede bruger og ikke den fulde mailadresse.

   - **Sender infrastruktur**: Domænet, der blev fundet i et omvendt DNS-opslag (PTR-post) i kildemailserverens IP-adresse. Hvis kildens IP-adresse ikke har nogen PTR-post, identificeres den afsendende infrastruktur som \<source IP\>/24 (f.eks. 192.168.100.100/24).

     Du kan få flere oplysninger om meddelelseskilder og meddelelsessendere under [En oversigt over standarder for mails](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards).

   - **Antal meddelelser**: Antallet af meddelelser fra afsendelsesinfrastrukturen til din organisation, der indeholder den eller de angivne spoofede afsendere eller afsendere inden for de sidste 30 dage.

   - **Antal brugerklager**: Klager indgivet af dine brugere mod denne afsender inden for de sidste 30 dage. Klager er normalt i form af indsendelser af uønsket post til Microsoft.

   - **Godkendelsesresultat**: En af følgende værdier:
      - **Bestået**: Afsenderen har sendt kontrol af godkendelse via mail (SPF eller DKIM).
      - **Mislykket**: Der opstod fejl i godkendelseskontrollen for EOP-afsenderen.
      - **Ukendt**: Resultatet af disse kontroller er ikke kendt.

   - **Sidst set**: Den sidste dato, hvor en meddelelse blev modtaget fra den afsendende infrastruktur, der indeholder den efterligningsbruger.

   - **Tilladt at spoof?**: De værdier, du kan se her, er:
     - **Ja**: Meddelelser fra kombinationen af spoofed bruger og afsendelsesinfrastruktur er tilladt og behandles ikke som spoofed mail.
     - **Nej**: Meddelelser fra kombinationen af spoofed bruger og afsendelsesinfrastruktur er markeret som spoofed. Handlingen styres af standardpolitikken til anti-phishing eller brugerdefinerede politikker til bekæmpelse af phishing (standardværdien er **Mappen Flyt meddelelse til mappen Uønsket mail**). Se næste afsnit for at få flere oplysninger.

     - **Nogle brugere** (kun fanen **Domæner** ): En afsendende infrastruktur er spoofing af flere brugere, hvor nogle spoofed-brugere er tilladt, og andre ikke er. Brug fanen **Detaljeret** til at se de specifikke adresser.

6. Klik på **Gem**, når du er færdig.

#### <a name="use-powershell-to-manage-spoofed-senders"></a>Brug PowerShell til at administrere forfalskede afsendere

> [!IMPORTANT]
> I denne artikel beskrives den ældre spoofed afsenderadministrationsoplevelse, der erstattes ( **spoof intelligence-politikken** på siden **Politikker til bekæmpelse af spam** ). Du kan få flere oplysninger om den nye oplevelse (fanen **Spoofing** på listen Over tilladte/blokerede lejere) [under Indsigt i Spoof intelligence i EOP](learn-about-spoof-intelligence.md).

Hvis du vil have vist tilladte og blokerede afsendere i spoof intelligence, skal du bruge følgende syntaks:

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

I dette eksempel returneres detaljerede oplysninger om alle afsendere, der har tilladelse til at spoof-brugere i dine domæner.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Hvis du vil konfigurere tilladte og blokerede afsendere i spoof intelligence, skal du følge disse trin:

1. Hent den aktuelle liste over registrerede spoofede afsendere ved at skrive outputtet fra **Get-PhishFilterPolicy-cmdlet'en** til en CSV-fil ved at køre følgende kommando:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Rediger CSV-filen for at tilføje eller ændre følgende værdier:
   - **Afsender** (domæne i kildeserverens PTR-post eller IP/24-adresse)
   - **SpoofedUser**: En af følgende værdier:
     - Den interne brugers mailadresse.
     - Den eksterne brugers maildomæne.
     - En tom værdi, der angiver, at du vil blokere eller tillade alle spoofede meddelelser fra den angivne **afsender**, uanset den spoofede mailadresse.
   - **AllowedToSpoof** (Ja eller Nej)
   - **SpoofType** (intern eller ekstern)

   Gem filen, læs filen, og gem indholdet som en variabel med navnet `$UpdateSpoofedSenders` ved at køre følgende kommando:

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Brug variablen `$UpdateSpoofedSenders` til at konfigurere spoof intelligence-politikken ved at køre følgende kommando:

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

### <a name="manage-spoofed-senders-in-the-spoof-intelligence-insight"></a>Administrer spoofed afsendere i indsigt i spoof intelligence

> [!IMPORTANT]
> I denne artikel beskrives den ældre spoofed afsenderadministrationsoplevelse, der erstattes ( **spoof intelligence-politikken** på siden **Politikker til bekæmpelse af spam** ). Du kan få flere oplysninger om den nye oplevelse (fanen **Spoofing** på listen Over tilladte/blokerede lejere) [under Indsigt i Spoof intelligence i EOP](learn-about-spoof-intelligence.md).

1. I Security & Compliance Center skal du gå til **Dashboard** til **trusselsstyring**\>.

2. I den **Insights** række skal du søge efter et af følgende elementer:

   - **Sandsynligvis forfalskede domæner i løbet af de seneste syv dage**: Denne indsigt angiver, at spoof intelligence er aktiveret (den er aktiveret som standard).
   - **Aktivér Spoof Protection**: Denne indsigt angiver, at spoof intelligence er deaktiveret, og når du klikker på indsigten, kan du aktivere spoof intelligence.

3. Indsigten på dashboardet viser oplysninger som disse:

   :::image type="content" source="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png" alt-text="Indsigten spoof intelligence" lightbox="../../media/28aeabac-c1a1-4d16-9fbe-14996f742a9a.png":::

   Denne indsigt har to tilstande:

   - **Indsigtstilstand**: Hvis spoof intelligence er aktiveret, viser indsigten, hvor mange meddelelser der blev påvirket af vores spoof intelligence-funktioner i løbet af de seneste syv dage.
   - **What if-tilstand**: Hvis spoof intelligence er deaktiveret, viser indsigten, hvor mange meddelelser *der ville* være blevet påvirket af vores spoof intelligence-funktioner i løbet af de seneste syv dage.

   I begge tilfælde er de spoofede domæner, der vises i indsigten, opdelt i to kategorier: **Mistænkelige domæner** og **ikke-mistænkelige domæner**.

   - **Mistænkelige domæner**:
     - **Spoof med høj konfidens**: Baseret på de historiske afsendelsesmønstre og domænernes omdømmescore er vi meget sikre på, at domænerne er spoofing, og meddelelser fra disse domæner er mere tilbøjelige til at være skadelige.
     - **Moderat tillidsspoof**: Baseret på historiske afsendelsesmønstre og domænernes omdømmescore er vi moderat sikre på, at domænerne er spoofing, og at meddelelser, der sendes fra disse domæner, er legitime. Falske positiver er mere sandsynlige i denne kategori end spoof med høj konfidens.
   - **Ikke-mistænkelige domæner**: Domænet mislykkedes eksplicitte mailgodkendelseskontroller [SPF](how-office-365-uses-spf-to-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md). Domænet overførte dog vores implicitte kontrol af mailgodkendelse ([sammensat godkendelse](email-validation-and-authentication.md#composite-authentication)). Derfor blev der ikke foretaget nogen anti-spoofing-handling på meddelelsen.

#### <a name="view-detailed-information-about-suspicious-and-nonsuspicious-domains"></a>Få vist detaljerede oplysninger om mistænkelige og ikke-skadelige domæner

1. På Spoof Intelligence-indsigten skal du klikke på **Mistænkelige domæner** eller **Ikke-mistænkelige domæner** for at gå til siden **Spoof intelligence-indsigt** . Siden **Spoof Intelligence-indsigt** indeholder følgende oplysninger:

   - **Spoofed domæne**: Domænet for den spoofede bruger, der vises i feltet **Fra** i mailklienter. Denne adresse kaldes også adressen `5322.From` .
   - **Infrastruktur**: Også kendt som _den afsendende infrastruktur_. Domænet, der blev fundet i et omvendt DNS-opslag (PTR-post) for kildemailserverens IP-adresse. Hvis kildens IP-adresse ikke har nogen PTR-post, identificeres den afsendende infrastruktur som \<source IP\>/24 (f.eks. 192.168.100.100/24).
   - **Antal meddelelser**: Antallet af meddelelser fra den sendende infrastruktur til din organisation, der indeholder det angivne spoofed domæne inden for de sidste 7 dage.
   - **Sidst set**: Den sidste dato, hvor der blev modtaget en meddelelse fra den afsendelsesinfrastruktur, der indeholder det spoofede domæne.
   - **Spoof-type**: Denne værdi er **ekstern**.
   - **Tilladt at spoof?**: De værdier, du kan se her, er:
     - **Ja**: Meddelelser fra kombinationen af den spoofede brugers domæne og afsendelsesinfrastruktur er tilladt og behandles ikke som spoofed mail.
     - **Nej**: Meddelelser fra kombinationen af den spoofede brugers domæne og afsendelsesinfrastruktur er markeret som spoofed. Handlingen styres af standardpolitikken til anti-phishing eller brugerdefinerede politikker til bekæmpelse af phishing (standardværdien er **Mappen Flyt meddelelse til mappen Uønsket mail**).

2. Vælg et element på listen for at få vist oplysninger om domænet/det afsendende infrastrukturpar i et pop op-vindue. Oplysningerne omfatter:
   - Hvorfor vi fangede det her.
   - Hvad du skal gøre.
   - En domæneoversigt.
   - WhoIs-data om afsenderen.
   - Lignende meddelelser, vi har set i din lejer fra den samme afsender.

   Herfra kan du også vælge at tilføje eller fjerne domænet/afsendelsesinfrastrukturparret fra listen **Tilladte til spoof-afsendere** . Du skal blot angive til/fra-knappen i overensstemmelse hermed.

   :::image type="content" source="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png" alt-text="Et domæne i detaljeruden for Spoof Intelligence-indsigt" lightbox="../../media/03ad3e6e-2010-4e8e-b92e-accc8bbebb79.png":::

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer virkede?

Hvis du vil bekræfte, at du har konfigureret spoof intelligence med afsendere, der har tilladelse og ikke har tilladelse til at spoof, skal du følge en af følgende trin:

- **Mail & samarbejde** \> **Politikker & regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet \> **Politikker** **Spoof intelligence-politik** \> vælg **Vis afsendere, jeg allerede har gennemgået**\>, vælg fanen **Dine domæner** eller **eksterne domæner**, og bekræft værdien **Tilladt at spoof?** for afsenderen.

- I PowerShell skal du køre følgende kommandoer for at få vist de afsendere, der har tilladelse til at spoof:

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- I PowerShell skal du køre følgende kommando for at eksportere listen over alle misvisende afsendere til en CSV-fil:

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
