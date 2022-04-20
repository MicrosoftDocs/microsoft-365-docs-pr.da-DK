---
title: Konfigurer standardfilterpolitikken for forbindelsen
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
description: Administratorer kan få mere at vide om, hvordan de konfigurerer forbindelsesfiltrering i Exchange Online Protection (EOP) for at tillade eller blokere mails fra mailservere.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0c09f445bf3d204f9e22d116dc9fda4c3fea9735
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974119"
---
# <a name="configure-connection-filtering"></a>Konfigurer filtrering af forbindelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Hvis du er Microsoft 365 kunde med postkasser i Exchange Online eller en separat EOP-kunde (Exchange Online Protection) uden Exchange Online  bruger du forbindelsesfiltrering i EOP (specifikt standardfilterpolitikken for forbindelse) til at identificere gode eller forkerte kildemailservere ved hjælp af deres IP-adresser. Nøglekomponenterne i standardfilterpolitikken for forbindelsen er:

- **Liste over ip-tilladte**: Spring spamfiltrering over for alle indgående meddelelser fra de kildemailservere, du angiver efter IP-adresse eller IP-adresseområde. I forbindelse med scenarier, hvor spamfiltrering stadig kan forekomme på meddelelser fra disse kilder, skal du se afsnittet [Scenarier, hvor meddelelser fra kilder på listen over tilladte IP-adresser stadig er filtreret](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) senere i denne artikel. Du kan få flere oplysninger om, hvordan listen over ip-adresser skal passe ind i din overordnede strategi for sikre afsendere, under [Opret lister over sikre afsendere i EOP](create-safe-sender-lists-in-office-365.md).

- **Ip-blokliste**: Bloker alle indgående meddelelser fra de kildemailservere, du angiver efter IP-adresse eller IP-adresseområde. De indgående meddelelser afvises, markeres ikke som spam, og der sker ingen yderligere filtrering. Du kan få flere oplysninger om, hvordan IP-blokeringslisten skal passe ind i din overordnede blokerede afsenderstrategi, under [Opret lister over afsendere af blokeringer i EOP](create-block-sender-lists-in-office-365.md).

- **Pengeskab liste**: Listen *over sikre* data er en dynamisk liste over tilladte i Microsoft-datacenteret, der ikke kræver kundekonfiguration. Microsoft identificerer disse mailkilder, der er tillid til, fra abonnementer til forskellige tredjepartslister. Du aktiverer eller deaktiverer brugen af listen over sikre filer. Du kan ikke konfigurere kildemailserverne på listen over sikre filer. Filtrering af spam springes over på indgående meddelelser fra mailserverne på den sikre liste.

I denne artikel beskrives det, hvordan du konfigurerer standardfilterpolitikken for forbindelser på Microsoft 365 Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell til Microsoft 365 organisationer med postkasser i Exchange Online ; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser). Du kan få flere oplysninger om, hvordan EOP bruger forbindelsesfiltrering, i organisationens overordnede indstillinger for anti-spam under [Beskyttelse mod spam](anti-spam-protection.md).

> [!NOTE]
> Ip-listen over tilladte, sikre lister og IP-blokeringslisten er en del af din overordnede strategi om at tillade eller blokere mail i din organisation. Du kan få flere oplysninger under [Opret lister over sikre afsendere](create-safe-sender-lists-in-office-365.md) og [Opret lister over blokerede afsendere](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

- Hvis du vil oprette forbindelse til Exchange Online PowerShell, [skal du se Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du se Forbind til Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tildelt tilladelser i **Exchange Online**, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil ændre standardfilterpolitikken for forbindelse, skal du være medlem af rollegrupperne **Organisationsadministration** eller **Sikkerhedsadministrator** .
  - Hvis du vil have skrivebeskyttet adgang til standardfilterpolitikken for forbindelse, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Noter**:

  - Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle i Microsoft 365 Administration giver brugerne de nødvendige tilladelser _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide under [Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - Rollegruppen **Vis kun organisationsadministration** i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) giver også skrivebeskyttet adgang til funktionen.

- Hvis du vil finde kilde-IP-adresserne for de mailservere (afsendere), du vil tillade eller blokere, kan du kontrollere headerfeltet for **ip-adressen (CIP**) i meddelelsesheaderen. Hvis du vil have vist en brevhoved i forskellige mailklienter, skal du se [Få vist brevhoveder på internettet i Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- Listen over tilladte IP-adresser tilsidesætter IP-blokeringslisten (en adresse på begge lister er ikke blokeret).

- Ip-tilladelseslisten og IP-bloklisten understøtter hver især maksimalt 1273 poster, hvor en post er en enkelt IP-adresse, et IP-adresseinterval eller en Klasseløs CIDR-IP (InterDomain Routing).

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Brug Microsoft 365 Defender-portalen til at ændre standardfilterpolitikken for forbindelsen

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** skal du vælge **Forbindelsesfilterpolitik (standard)** på listen ved at klikke på navnet på politikken.

3. Konfigurer en af følgende indstillinger i det viste pop op-vindue med politikoplysninger:

   - **Beskrivelsessektion** : Klik på **Rediger navn og beskrivelse**. I pop op-vinduet **Rediger navn og beskrivelse** , der vises, skal du angive valgfri beskrivende tekst i feltet **Beskrivelse** .

     Klik på **Gem**, når du er færdig.

   - **Sektionen Forbindelsesfiltrering**: Klik på **Rediger politik for forbindelsesfilter**. Konfigurer følgende indstillinger i det pop op-vindue, der vises:

     - **Tillad altid meddelelser fra følgende IP-adresser eller adresseinterval**: Dette er listen over tilladte IP-adresser. Klik i feltet, angiv en værdi, og tryk derefter på Enter, eller vælg den komplette værdi, der vises under feltet. Gyldige værdier er
       - Enkelt IP: f.eks. 192.168.1.1.
       - IP-interval: f.eks. 192.168.0.1-192.168.0.254.
       - CIDR IP: For eksempel 192.168.0.1/25. Gyldige værdier for undernetmaske er /24 til /32. Hvis du vil springe spamfiltrering for /1 til /23 over, skal du se afsnittet [Spring spamfiltrering over for en CIDR-IP uden for det tilgængelige intervalafsnit](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) senere i denne artikel.

       Gentag dette trin så mange gange, det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

     Hvis du vil tilføje IP-adressen eller adresseområdet, skal du klikke i feltet og skrive detklik på **Tilføj** ![ikon.](../../media/ITPro-EAC-AddIcon.png) Hvis du vil fjerne en post, skal du markere posten i **Tilladt IP-adresse** og derefter klikke på **Fjern** ![fjern](../../media/scc-remove-icon.png). Klik på **Gem**, når du er færdig.

   - **Bloker altid meddelelser fra følgende IP-adresser eller adresseinterval**: Dette er IP-blokeringslisten. Angiv en enkelt IP-, IP-interval- eller CIDR-IP-adresse i feltet som tidligere beskrevet i indstillingen **Tillad altid meddelelser fra følgende IP-adresser eller adresseområde** .

   - **Slå liste, der er tillid** til, til: Aktivér eller deaktiver brugen af listen, der er tillid til, for at identificere kendte, gode afsendere, der springer spamfiltrering over. Hvis du vil bruge listen, der er tillid til, skal du markere afkrydsningsfeltet.

   Klik på **Gem**, når du er færdig.

4. Klik på **Luk** på pop op-vinduet med politikoplysninger igen.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Brug Microsoft 365 Defender-portalen til at få vist standardfilterpolitikken for forbindelse

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Anti-spam** i afsnittet **Politikker**. Hvis du vil gå direkte til siden **Politikker mod spam** , skal du bruge <https://security.microsoft.com/antispam>.

2. På siden **Politikker mod spam** vises følgende egenskaber på listen over politikker:

   - **Navn**: Denne værdi er **Forbindelsesfilterpolitik (standard)** for standardpolitikken for forbindelsesfilter.
   - **Status**: Denne værdi er **altid aktiveret** for standardfilterpolitikken for forbindelsen.
   - **Prioritet**: Denne værdi er **Laveste** for standardfilterpolitikken for forbindelse.
   - **Type**: Denne værdi er tom for standardfilterpolitikken for forbindelsen.

3. Når du vælger standardfilterpolitikken for forbindelse, vises politikindstillingerne i et pop op-vindue.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell til at ændre standardfilterpolitikken for forbindelse

Brug følgende syntaks:

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Noter**:

- Gyldige værdier for IP-adresse eller adresseområde er:
  - Enkelt IP: f.eks. 192.168.1.1.
  - IP-interval: f.eks. 192.168.0.1-192.168.0.254.
  - CIDR IP: For eksempel 192.168.0.1/25. Gyldige værdier for netværksmasker er /24 til /32.
- Hvis du vil *overskrive* eksisterende poster med de værdier, du angiver, skal du bruge følgende syntaks: `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Hvis du vil *tilføje eller fjerne* IP-adresser eller adresseområder, uden at det påvirker andre eksisterende poster, skal du bruge følgende syntaks: `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- Hvis du vil tømme IP-listen over tilladte lister eller IP-blokeringslisten, skal du bruge værdien `$null`.

I dette eksempel konfigureres listen over tilladte IP-adresser og ip-bloklisten med de angivne IP-adresser og adresseintervaller.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

I dette eksempel tilføjes og fjernes de angivne IP-adresser og adresseområder fra listen over tilladte IP-adresser.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Hvordan ved du, det virkede?

Benyt en af følgende fremgangsmåder for at bekræfte, at du har ændret standardfilterpolitikken for forbindelsen:

- På siden **Anti-spam** på Microsoft 365 Defender-portalen på <https://security.microsoft.com/antispam>skal du vælge **Forbindelsesfilterpolitik (standard)** på listen ved at klikke på navnet på politikken og bekræfte indstillingerne.

- I Exchange Online PowerShell eller enkeltstående EOP PowerShell skal du køre følgende kommando og kontrollere indstillingerne:

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- Send en testmeddelelse fra en post på IP-listen over tilladte.

## <a name="additional-considerations-for-the-ip-allow-list"></a>Yderligere overvejelser i forbindelse med LISTEN over tilladte IP-adresser

I følgende afsnit identificeres yderligere elementer, som du har brug for at vide om, når du konfigurerer listen over tilladte IP-adresser.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Spring spamfiltrering over for en CIDR-IP uden for det tilgængelige interval

Som beskrevet tidligere i denne artikel kan du kun bruge en CIDR-IP med netværksmasken /24 til /32 på listen over tilladte IP-adresser. Hvis du vil springe spamfiltrering over på meddelelser fra kildemailservere i området /1 til /23, skal du bruge Exchange regler for mailflow (også kendt som transportregler). Men vi anbefaler, at du ikke gør dette, hvis det overhovedet er muligt, fordi meddelelserne blokeres, hvis en IP-adresse i CIDR-IP-intervallet /1 til /23 vises på nogen af Microsofts blokerede eller tredjepartsblokeringslister.

Nu, hvor du er helt opmærksom på de potentielle problemer, kan du oprette en regel for mailflow med følgende indstillinger (som minimum) for at sikre, at meddelelser fra disse IP-adresser springer spamfiltrering over:

- Regelbetingelse: **Anvend denne regel, hvis** \> **afsenderens IP-adresse er inden for et af disse intervaller eller stemmer nøjagtigt overens** \> (angiv din CIDR-IP med netværksmasken /1 til /23). \>
- Regelhandling: **Rediger meddelelsesegenskaberNe** \> **Angiv niveauet for spamsikkerhed (SCL)** \> **Tilsidesæt filtrering af spam**.

Du kan overvåge reglen, teste reglen, aktivere reglen i en bestemt tidsperiode og andre valg. Vi anbefaler, at du tester reglen i en periode, før du gennemtvinger den. Du kan få flere oplysninger under [Administrer regler for mailflow i Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Spring spamfiltrering over på udvalgte maildomæner fra den samme kilde

Hvis du føjer en IP-adresse eller et adresseområde til listen over tilladte IP-adresser, betyder det typisk, at du har tillid til alle indgående meddelelser fra den pågældende mailkilde. Men hvad nu, hvis denne kilde sender mail fra flere domæner, og du vil springe spamfiltrering over for nogle af disse domæner, men ikke andre? Du kan ikke bruge IP-tilladelseslisten alene til at gøre dette, men du kan bruge IP-listen over tilladte i kombination med en regel for mailflow.

Kildemailserveren 192.168.1.25 sender f.eks. mail fra domænerne contoso.com, fabrikam.com og tailspintoys.com, men du vil kun springe spamfiltrering over for meddelelser fra afsendere i fabrikam.com. Det gør du ved at følge disse trin:

1. Føj 192.168.1.25 til IP-listen over tilladte.

2. Konfigurer en regel for et mailflow med følgende indstillinger (som minimum):
   - Regelbetingelse: **Anvend denne regel, hvis** \> **afsenderens IP-adresse er i et af disse intervaller eller stemmer nøjagtigt overens med** \> 192.168.1.25 (den samme IP-adresse eller det samme adresseinterval, som du føjede til listen over tilladte IP-adresser i det forrige trin). \>
   - Regelhandling: **Rediger meddelelsesegenskaberne** \> **Angiv tillidsniveauet for spam (SCL)** \> **0**.
   - Regelundtagelse: **Afsenderdomænet** \> **er** \> fabrikam.com (kun det eller de domæner, du vil springe spamfiltrering over).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>Scenarier, hvor meddelelser fra kilder på listen over tilladte IP-adresser stadig filtreres

Meddelelser fra en mailserver på listen over tilladte IP-adresser kan stadig filtreres efter spam i følgende scenarier:

- En IP-adresse på listen over tilladte IP-adresser er også konfigureret i en IP-baseret indgående connector i en *hvilken som helst* lejer i Microsoft 365 (lad os kalde denne lejer A), **og** lejer A og den EOP-server, der første gang støder på meddelelsen, befinder sig i *det samme* Active Directory-område i Microsoft-datacentrene. I dette *scenarie føjes* **IPV:CAL** til meddelelsens [anti-spam-meddelelsesheadere](anti-spam-message-headers.md) (hvilket angiver, at meddelelsen er omgået spamfiltrering), men meddelelsen er stadig underlagt filtrering af spam.

- Din lejer, der indeholder ip-tilladelseslisten og den EOP-server, der første gang støder på meddelelsen, befinder sig i *forskellige* Active Directory-områder i Microsoft-datacentrene. I dette scenarie føjes **IPV:CAL** *ikke* til brevhovederne, så meddelelsen er stadig underlagt filtrering af spam.

Hvis du støder på et af disse scenarier, kan du oprette en regel for mailflow med følgende indstillinger (som minimum) for at sikre, at meddelelser fra de problematiske IP-adresser springer spamfiltrering over:

- Regelbetingelse: **Anvend denne regel, hvis** \> **afsenderens IP-adresse er inden for et af disse intervaller eller stemmer nøjagtigt overens** \> (din IP-adresse eller dine adresser). \>
- Regelhandling: **Rediger meddelelsesegenskaberNe** \> **Angiv niveauet for spamsikkerhed (SCL)** \> **Tilsidesæt filtrering af spam**.

## <a name="new-to-microsoft-365"></a>Er du ny Microsoft 365?

****

![Det korte ikon for LinkedIn-Learning.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Er du ny Microsoft 365?** Se gratis videokurser for **Microsoft 365 administratorer og it-teknikere**, som LinkedIn Learning har bragt til dig.
