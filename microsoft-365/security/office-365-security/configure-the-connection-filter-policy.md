---
title: Konfigurere standardfilterpolitikken for forbindelse
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan lære, hvordan du konfigurerer filtrering af forbindelse i Exchange Online Protection (EOP) for at tillade eller blokere mails fra mailservere.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2fbc481468fca8562c11e89b2e6c9dfa6361126a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589139"
---
# <a name="configure-connection-filtering"></a>Konfigurere filtrering af forbindelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


Hvis du er Microsoft 365 kunde med postkasser i Exchange Online eller en enkeltstående Exchange Online Protection (EOP) uden Exchange Online  postkasser, skal du bruge forbindelsesfiltrering i EOP (specifikt standardfilterpolitikken for forbindelse) til at identificere gode eller dårlige kildemailservere efter deres IP-adresser. De vigtigste komponenter i standardfilterpolitikken for forbindelse er:

- **Liste over tilladte** IP-adresser: Spring spamfiltrering over for alle indgående meddelelser fra de kildemailservere, du angiver efter IP-adresse eller IP-adresseområde. Hvis du vil se scenarier, hvor der muligvis stadig kan forekomme spamfiltrering på meddelelser fra disse kilder, skal du se afsnittet Scenarier, hvor meddelelser fra kilder på listen over tilladte IP-adresser stadig [filtreres](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) senere i denne artikel. Du kan finde flere oplysninger om, hvordan listen over tilladte IP-adresser skal passe ind i din overordnede strategi for afsendere, der er tillid til, i Opret lister over afsendere, der er tillid til [i EOP](create-safe-sender-lists-in-office-365.md).

- **IP-blokliste**: Bloker alle indgående meddelelser fra de kildemailservere, du angiver efter IP-adresse eller IP-adresseområde. De indgående meddelelser afvises, markeres ikke som spam, og der sker ingen yderligere filtrering. Du kan finde flere oplysninger om, hvordan IP-blokeringslisten skal passe ind i din overordnede strategi for blokerede afsendere, under Opret lister over [blokerede afsendere i EOP](create-block-sender-lists-in-office-365.md).

- **Pengeskab liste**: Listen *over sikre er* en dynamisk tilladelsesliste i Microsofts datacenter, der ikke kræver nogen kundekonfiguration. Microsoft identificerer disse pålidelige mailkilder fra abonnementer til forskellige tredjepartslister. Du aktiverer eller deaktiverer brugen af listen over sikre; du kan ikke konfigurere kildemailserverne på listen over sikre mailservere. Spamfiltrering ignoreres på indgående meddelelser fra mailserverne på listen over sikre afsendere.

I denne artikel beskrives det, hvordan du konfigurerer standardfilterpolitikken for forbindelser i Microsoft 365 Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell Microsoft 365 organisationer med postkasser i Exchange Online ; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser). Du kan finde flere oplysninger om, hvordan EOP bruger forbindelsesfiltrering, i din organisations overordnede antispamindstillinger under [Beskyttelse mod spam](anti-spam-protection.md).

> [!NOTE]
> Listen over tilladte IP-adresser, sikre lister og IP-bloklisten er en del af din overordnede strategi for at tillade eller blokere mail i organisationen. Få mere at vide under Opret [lister over afsendere, der er tillid til](create-safe-sender-lists-in-office-365.md) [og Opret lister over blokerede afsendere](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser **i Exchange Online,** før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre standardfilterpolitikken for forbindelser, skal du være medlem af **rollegrupperne Organisationsadministration** **eller Sikkerhedsadministrator** .
  - For skrivebeskyttet adgang til standardfilterpolitikken for forbindelse skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger i Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Hvis du føjer brugere til den Azure Active Directory rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser og tilladelser til andre  funktioner Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- Hvis du vil finde kilde-IP-adresserne på de mailservere (afsendere), du vil tillade eller blokere, kan du markere feltet med den tilsluttende IP-adresse (**CIP**) i brevhovedet. Hvis du vil have vist et brevhoved i forskellige mailklienter, [skal du se Få vist internetmeddelelsesoverskrifter Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- Listen over tilladte IP-adresser tilsidesætter LISTEN over blokerede IP-adresser (en adresse på begge lister blokeres ikke).

- Listen over tilladte IP-adresser og listen over blokerede IP-adresser understøtter maksimalt 1273 poster, hvor et element er en enkelt IP-adresse, et IP-adresseområde eller en CIDR-IP (Classless InterDomain Routing).

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Brug portalen Microsoft 365 Defender til at ændre standardfilterpolitikken for forbindelse

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Antispam-politikker** skal du vælge Forbindelsesfilterpolitik **(Standard)** på listen ved at klikke på navnet på politikken.

3. I pop op-vindue med politikoplysninger, der vises, skal du konfigurere en af følgende indstillinger:

   - **Beskrivelsessektion** : Klik **på Rediger navn og beskrivelse**. I pop **op-menuen Rediger navn og** beskrivelse, der vises, skal du angive valgfri **beskrivende tekst i feltet** Beskrivelse.

     Klik på **Gem**, når du er færdig.

   - **Sektionen Filtrering af forbindelse**: Klik på **Rediger filterpolitik for forbindelse**. I pop op-menuen, der vises, skal du konfigurere følgende indstillinger:

     - **Tillad altid meddelelser fra følgende IP-adresser eller adresseområde**: Dette er listen over tilladte IP-adresser. Klik i feltet, angiv en værdi, og tryk derefter på Enter, eller vælg den fulde værdi, der vises under feltet. Gyldige værdier er
       - Enkelt IP: F.eks. 192.168.1.1.
       - IP-område: Eksempel: 192.168.0.1-192.168.0.254.
       - CIDR IP: F.eks. 192.168.0.1/25. Gyldige værdier for undernetmasker er /24 til /32. Hvis du vil springe spamfiltrering for /1 til /23 over, skal du se afsnittet [Spring spamfiltrering over for en CIDR-IP uden for](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) det tilgængelige område senere i denne artikel.

       Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

     Hvis du vil tilføje IP-adressen eller adresseområdet, skal du klikke i feltet **og skrive tilføj** ![tilføj ikon](../../media/ITPro-EAC-AddIcon.png). Hvis du vil fjerne en post, skal du markere posten **i Tilladt IP-adresse og** derefter klikke **på Fjern** ![Fjern](../../media/scc-remove-icon.png). Klik på **Gem**, når du er færdig.

   - **Bloker altid meddelelser fra følgende IP-adresser eller adresseområde**: Dette er IP-blokeringslisten. Angiv en enkelt IP-, IP-område eller CIDR-IP i feltet som tidligere beskrevet i indstillingen Tillad altid meddelelser fra følgende **IP-adresser eller adresseområde** .

   - **Aktivér listen over afsendere**, der er tillid til: Aktivér eller deaktiver brugen af listen, der er tillid til, for at identificere kendte, gode afsendere, der springer spamfiltrering over. Hvis du vil bruge listen over sikre personer, skal du markere afkrydsningsfeltet.

   Klik på **Gem**, når du er færdig.

4. Tilbage i pop op-menuen med politikoplysninger skal du klikke **på Luk**.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Brug portalen Microsoft 365 Defender til at få vist standardfilterpolitikken for forbindelse

1.  I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **&-samarbejdspolitikker** \> **& Politikker** \> \> for trussel mod **trusler** i **afsnittet Politikker.** For at gå direkte til **siden Politikker for uønsket post** skal du bruge <https://security.microsoft.com/antispam>.

2. På **siden Politikker for uønsket** post vises følgende egenskaber på listen over politikker:

   - **Navn**: Denne værdi er **Filterpolitik for forbindelse (Standard)** for standardfilterpolitikken for forbindelse.
   - **Status**: Denne værdi er **altid til** for standardfilterpolitikken for forbindelse.
   - **Prioritet**: Denne værdi er **Laveste** for standardfilterpolitikken for forbindelse.
   - **Type**: Denne værdi er tom for standardfilterpolitikken for forbindelse.

3. Når du vælger standardfilterpolitikken for forbindelse, vises politikindstillingerne i en pop op-meddelelse.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at ændre standardfilterpolitikken for forbindelse

Brug følgende syntaks:

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Bemærkninger**:

- Gyldige værdier for IP-adresse eller adresseområde er:
  - Enkelt IP: F.eks. 192.168.1.1.
  - IP-område: Eksempel: 192.168.0.1-192.168.0.254.
  - CIDR IP: F.eks. 192.168.0.1/25. Gyldige værdier for netværksmasker er /24 til /32.
- Hvis *du vil overskrive eksisterende* poster med de værdier, du angiver, skal du bruge følgende syntaks: `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Hvis *du vil tilføje eller fjerne* IP-adresser eller adresseintervaller, uden at det påvirker andre eksisterende poster, skal du bruge følgende syntaks: `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- Hvis du vil tømme listen over tilladte IP-adresser eller listen over blokerede IP-adresser, skal du bruge værdien `$null`.

I dette eksempel konfigureres listen over tilladte IP-adresser og IP-blokeringen med de angivne IP-adresser og adresseintervaller.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

I dette eksempel tilføjes og fjernes de angivne IP-adresser og adresseintervaller fra listen over tilladte IP-adresser.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Hvordan ved du, at det virkede?

For at bekræfte, at du har ændret standardfilterpolitikken for forbindelse, skal du gøre et af følgende:

- På siden **Antispam i Microsoft 365 Defender-portalen** på skal du vælge Filterpolitik for forbindelse **(standard)** på listen ved at <https://security.microsoft.com/antispam>klikke på navnet på politikken og kontrollere indstillingerne.

- I Exchange Online PowerShell eller enkeltstående EOP PowerShell skal du køre følgende kommando og bekræfte indstillingerne:

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Send en testmeddelelse fra en post på listen over tilladte IP-adresser.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Yderligere overvejelser i forbindelse med listen over tilladte IP-adresser

De følgende afsnit identificerer yderligere elementer, du skal kende til, når du konfigurerer listen over tilladte IP-adresser.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Spring spamfiltrering over for en CIDR-IP uden for det tilgængelige område

Som beskrevet tidligere i denne artikel kan du kun bruge en CIDR-IP med netværksmasken /24 til /32 på listen over tilladte IP-adresser. Hvis du vil springe spamfiltrering over meddelelser fra kildemailservere i området /1 til /23, skal du bruge Exchange-regler for mailflow (også kaldet transportregler). Men vi anbefaler, at du ikke gør dette, hvis det overhovedet er muligt, da meddelelserne blokeres, hvis en IP-adresse i IP-området /1 til /23 CIDR vises på en af Microsofts beskyttede lister eller blokeringslister fra tredjeparter.

Nu, hvor du er fuldt ud klar over de potentielle problemer, kan du oprette en regel for mailflow med følgende indstillinger (som minimum) for at sikre, at meddelelser fra disse IP-adresser springer spamfiltrering over:

- Regelbetingelse **:** \>  \> Anvend denne regel, hvis **afsenderens IP-adresse** er i et af disse områder eller er helt ens \> (angiv din CIDR-IP med en /1 til /23-netværksmaske).
- Regelhandling: **Rediger meddelelsesegenskaberne Angiv** \> **SCL-niveauet** \> for **spamfiltrering**.

Du kan overvåge reglen, teste reglen, aktivere reglen i en bestemt tidsperiode og andre valg. Vi anbefaler, at du tester reglen for en periode, før du gennemtvinger den. Få mere at vide under [Administrer regler for mailflow i Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Spring spamfiltrering over selektive maildomæner fra den samme kilde

Typisk betyder tilføjelse af en IP-adresse eller et adresseområde til listen over tilladte IP-adresser, at du har tillid til alle indgående meddelelser fra den pågældende mailkilde. Men hvad nu, hvis kilden sender mails fra flere domæner, og du vil springe spamfiltrering over for nogle af disse domæner, men ikke andre? Du kan ikke bruge listen over tilladte IP-adresser alene til dette, men du kan bruge listen over tilladte IP-adresser sammen med en regel for mailflow.

For eksempel sender kildemailserveren 192.168.1.25 mails fra domænerne contoso.com, fabrikam.com og tailspintoys.com, men du vil kun springe spamfiltrering over for meddelelser fra afsendere i fabrikam.com. Det gør du ved at følge disse trin:

1. Føj 192.168.1.25 til listen over tilladte IP-adresser.

2. Konfigurer en regel for mailflow med følgende indstillinger (som minimum):
   - Regelbetingelse **:** \>  \> Anvend denne regel, hvis **afsenderens** \> IP-adresse er i et af disse områder eller svarer nøjagtigt til 192.168.1.25 (den samme IP-adresse eller det samme adresseområde, som du føjede til listen over tilladte IP-adresser i forrige trin).
   - Regelhandling: **Rediger meddelelsesegenskaberne Angiv** \> **SCL(spam confidence level)** \> **0**.
   - Undtagelse for regel: **Afsenderdomænet** \> **er fabrikam.com** \> (kun det eller de domæner, du vil springe spamfiltrering over).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scenarier, hvor meddelelser fra kilder på listen over tilladte IP-adresser stadig filtreres

Meddelelser fra en mailserver på din liste over tilladte IP-adresser er stadig underlagt spamfiltrering i følgende scenarier:

- En IP-adresse i din liste over tilladte IP-adresser er også konfigureret i en lokal, IP-baseret indgående  forbindelse i enhver lejer i Microsoft 365 (lad os kalde denne lejer **A) og** Lejer A og EOP-serveren, der begge støder på meddelelsen, ligger begge i den *samme Active* Directory-skov i Microsoft-datacentrene. I dette scenarie føjes **IPV:CAL**  til [meddelelsens antispam-brevhoveder](anti-spam-message-headers.md) (hvilket angiver, at meddelelsen har ignoreret spamfiltrering), men meddelelsen er stadig underlagt spamfiltrering.

- Din lejer, der indeholder listen over tilladte IP-adresser og EOP-serveren, der først støder på meddelelsen, ligger begge i *forskellige Active* Directory-områder i Microsoft-datacentrene. I dette scenarie **føjes IPV:CAL**  ikke til brevhovederne, så meddelelsen er stadig underlagt spamfiltrering.

Hvis du støder på et af disse scenarier, kan du oprette en regel for mailflow med følgende indstillinger (som minimum) for at sikre, at meddelelser fra de problematiske IP-adresser springer spamfiltrering over:

- Regelbetingelse: **Anvend denne regel**\>, hvis **afsenderens** \> IP-adresse er i et af disse områder eller er nøjagtigt den **samme** \> (din IP-adresse eller dine adresser).
- Regelhandling: **Rediger meddelelsesegenskaberne Angiv** \> **SCL-niveauet** \> for **spamfiltrering**.

## <a name="new-to-microsoft-365"></a>Er du ny Microsoft 365?

****

![Det korte ikon for LinkedIn Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Er du ny Microsoft 365?** Find gratis videokurser til **Microsoft 365 og it-fagfolk** gennem LinkedIn Learning.
