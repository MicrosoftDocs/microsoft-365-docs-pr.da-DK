---
title: Sådan bruger du DKIM til mail i dit brugerdefinerede domæne
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Lær at bruge DomainKeys Identified Mail (DKIM) med Microsoft 365 til at sikre, at meddelelser, der sendes fra dit brugerdefinerede domæne, er pålidelige i destinationens mailsystemer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 25333a1616bb1f4e4e529c17813bdd58f4c768b4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587264"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 Denne artikel viser trinnene til at bruge DomainKeys Identified Mail (DKIM) med Microsoft 365 til at sikre, at destinationsmailsystemer har tillid til meddelelser, der sendes udgående fra dit brugerdefinerede domæne.

I denne artikel:

- [Sådan fungerer DKIM bedre end SPF alene for at forhindre skadelig spoofing](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Trin til at oprette, aktivere og deaktivere DKIM Microsoft 365 Defender-portalen](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [Trin til manuelt at opgradere dine 1024-bit nøgler til 2048-bit DKIM-krypteringsnøgler](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [Trin til manuel opsætning af DKIM](#steps-to-manually-set-up-dkim)
- [Trin til konfiguration af DKIM for mere end ét brugerdefineret domæne](#to-configure-dkim-for-more-than-one-custom-domain)
- [Deaktivering af DKIM-signeringspolitikken for et brugerdefineret domæne](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [Standardfunktionsmåden for DKIM og Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- [Konfigurer DKIM, så en tredjepartstjeneste kan sende, eller efterligne, mail på vegne af dit brugerdefinerede domæne](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [Næste trin: Når du har konfigureret DKIM til Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 automatisk DKIM til dens indledende "onmicrosoft.com"-domæner. Det betyder, at du ikke behøver at gøre noget for at konfigurere DKIM for nogen indledende domænenavne (f.eks. litware.onmicrosoft.com). Du kan finde flere oplysninger om domæner i Ofte [stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM er en af de mange godkendelsesmetoder (SPF, DKIM og DMARC), der er med til at forhindre hackere i at sende meddelelser, der ser ud som om, de kommer fra dit domæne.

DKIM gør det muligt at føje en digital signatur til udgående mails i brevhovedet. Når du konfigurerer DKIM, autoriserer du dit domæne til at knytte, eller signere, dets navn til en mail ved hjælp af krypteret godkendelse. Mailsystemer, der henter mail fra dit domæne, kan bruge denne digitale signatur til at bekræfte, om indgående mails er legitime.

Grundlæggende krypterer en privat nøgle sidehovedet i et domænes udgående mail. Den offentlige nøgle er publiceret i domænets DNS-poster, og modtagende servere kan bruge denne nøgle til at afkode signaturen. DKIM-bekræftelse hjælper de modtagende servere med at bekræfte, at mailen virkelig kommer fra dit domæne og ikke en *person, der spoofing dit* domæne.

> [!TIP]
>Du kan også vælge at gøre noget ved DKIM for dit brugerdefinerede domæne. Hvis du ikke konfigurerer DKIM for dit brugerdefinerede domæne, opretter Microsoft 365 et privat og offentligt nøglepar, aktiverer DKIM-signering og konfigurerer derefter Microsoft 365 standardpolitikken for dit brugerdefinerede domæne.

 Microsoft-365's indbyggede DKIM-konfiguration er tilstrækkelig dækning for de fleste kunder. Du skal dog konfigurere DKIM manuelt for dit brugerdefinerede domæne under følgende omstændigheder:

- Du har mere end ét brugerdefineret domæne i Microsoft 365
- Du kommer til at konfigurere DMARC også (**anbefales**)
- Du vil have kontrol over din private nøgle
- Du vil tilpasse dine CNAME-poster
- Du vil konfigurere DKIM-nøgler til mail, der stammer fra et tredjepartsdomæne, f.eks. hvis du bruger en tredjeparts masseforsendelse.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Sådan fungerer DKIM bedre end SPF alene for at forhindre skadelig spoofing
<a name="HowDKIMWorks"> </a>

SPF føjer oplysninger til en konvolut, men DKIM *krypterer en* signatur i brevhovedet. Når du videresender en meddelelse, kan dele af meddelelsens konvolut fjernes fra videresendelsesserveren. Da den digitale signatur forbliver sammen med mailen, fordi den er en del af mailens brevhoved, fungerer DKIM, også selvom en meddelelse er blevet videresendt som vist i følgende eksempel.

![Diagram, der viser en videresendt meddelelse med dkim-godkendelse, hvor SPF-kontrol mislykkes.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

Hvis du i dette eksempel kun har udgivet en SPF TXT-post for dit domæne, kan modtagerens mailserver have markeret din mail som spam og genereret et falsk positivt resultat. **Tilføjelsen af DKIM i dette scenarie reducerer *rapportering af falsk* positiv spam.** Da DKIM er afhængig af offentlig nøglekryptografi til godkendelse og ikke kun IP-adresser, betragtes DKIM som en meget stærkere form for godkendelse end SPF. Vi anbefaler, at du bruger både SPF og DKIM samt DMARC i din installation.

> [!TIP]
> DKIM bruger en privat nøgle til at indsætte en krypteret signatur i brevhovederne. Det signeringsdomæne eller det udgående domæne indsættes som værdien af **feltet d=** i sidehovedet. Det bekræftende domæne eller modtagerens domæne bruger derefter **feltet d=** til at søge efter den offentlige nøgle fra DNS og godkende meddelelsen. Hvis meddelelsen er bekræftet, passerer DKIM-tjek.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Trin til at oprette, aktivere og deaktivere DKIM Microsoft 365 Defender-portalen

Alle de accepterede domæner for din lejer vises på Microsoft 365 Defender under DKIM-siden. Hvis du ikke kan se det, skal du tilføje dit accepterede domæne [fra domænesiden](/microsoft-365/admin/setup/add-domain#add-a-domain).
Når dit domæne er tilføjet, skal du følge trinnene som vist nedenfor for at konfigurere DKIM.

Trin 1: Klik på det domæne, du ønsker at konfigurere DKIM på DKIM-siden (https://security.microsoft.com/dkimv2 eller https://protection.office.com/dkimv2).

![DKIM-siden i Microsoft 365 Defender med et domæne markeret.](../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png)

Trin 2: Skub til/fra-knappen for at **aktivere**. Du får vist et pop op-vindue med en besked om, at du skal tilføje CNAME-poster.

![Skub til/fra-knappen til Aktiveret for at aktivere DKIM.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

Trin 3: Kopiér de CNAMES, der vises i pop op-vinduet

Trin 4: Publicer de kopierede CNAME-poster til din DNS-serviceudbyder.

Tilføj CNAME-poster for DKIM, som du vil aktivere, på DNS-udbyderens websted. Sørg for, at felterne er indstillet til følgende værdier for hver:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

Trin 5: Vend tilbage til DKIM-siden for at aktivere DKIM.

![Skub til/fra-knappen til Aktiveret for at aktivere DKIM.](../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png)

Hvis du ser, at CNAME-posten ikke findes, kan det skyldes:

1. Synkronisering med DNS-server, hvilket kan tage få sekunder eller timer, hvis problemet fortsætter, skal du gentage trinnene igen
2. Kontrollér for eventuelle kopiér indsætningsfejl, f.eks. ekstra plads eller faner osv.

Hvis du vil deaktivere DKIM, skal du skifte tilbage for at deaktivere tilstand

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>Trin til manuelt at opgradere dine 1024-bit nøgler til 2048-bit DKIM-krypteringsnøgler
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 konfigurerer automatisk DKIM *til onmicrosoft.com* domæner. Der kræves ingen trin for at bruge DKIM for indledende domænenavne (f.eks. litware.*onmicrosoft.com*). Du kan finde flere oplysninger om domæner i Ofte [stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Da både 1024- og 2048-bittæthed understøttes for DKIM-nøgler, fortæller denne vejledning dig, hvordan du opgraderer din 1024-bit-nøgle til 2048 [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Nedenstående trin er til to use cases. Vælg den, der passer bedst til din konfiguration.

- Når du **allerede har DKIM konfigureret**, roterer du bittæthed ved at køre følgende kommando:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **eller**

- For en **ny implementering af DKIM** skal du køre følgende kommando:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Bevar forbindelsen til Exchange Online PowerShell *for at* bekræfte konfigurationen ved at køre følgende kommando:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Denne nye 2048-bit-nøgle træder i kraft på RotateOnDate og sender mails med nøglen 1024-bit i mellemtiden. Efter fire dage kan du teste igen med 2048-bit-tasten (det vil sige, at når rotationen træder i kraft i den anden vælger).

Hvis du vil rotere til den anden vælger efter fire dage og bekræfte, at 2048-bittæthed er i brug, skal du manuelt rotere den anden vælgernøgle ved hjælp af den relevante cmdlet, der er angivet ovenfor.

Du kan finde detaljerede oplysninger om syntaks og parameter i følgende artikler: [Roter-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) og [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>Trin til manuel opsætning af DKIM
<a name="SetUpDKIMO365"> </a>

Hvis du vil konfigurere DKIM, skal du udføre disse trin:

- [Publicere to CNAME-poster for dit brugerdefinerede domæne i DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Aktivér DKIM-signering for dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>Publicere to CNAME-poster for dit brugerdefinerede domæne i DNS
<a name="Publish2CNAME"> </a>

For hvert domæne, for hvilket du vil tilføje en DKIM-signatur i DNS, skal du publicere to CNAME-poster.

> [!NOTE]
> Hvis du ikke har læst hele artiklen, er du måske gået glip af disse tidsbesparende PowerShell-forbindelsesoplysninger: [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Kør følgende kommandoer i Exchange Online PowerShell for at oprette vælgerposterne:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

Hvis du har klargjorte brugerdefinerede domæner ud over det indledende domæne i Microsoft 365, skal du publicere to CNAME-poster for hvert ekstra domæne. Så hvis du har to domæner, skal du publicere to ekstra CNAME-poster osv.

Brug følgende format til CNAME-posterne.

> [!IMPORTANT]
> Hvis du er en af vores GCC High-kunder, beregner vi _customDomainIdentifier anderledes_! I stedet for at søge efter MX-posten for dit _initialdomæne_ til beregning af _customDomainIdentifier_, beregner vi den i stedet direkte fra det brugerdefinerede domæne. Hvis dit tilpassede domæne f.eks. er "contoso.com" bliver dit _customDomainIdentifier_ "contoso-com", så erstattes eventuelle perioder med en bindestreg. Så uanset hvilken MX-post dit _initialdomæne_ peger på, skal du altid bruge ovenstående metode til at beregne _den customDomainIdentifier_ , der skal bruges i dine CNAME-poster.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Hvor:

- For Microsoft 365 vælgerne altid være "vælger1" eller "vælger2".
- _customDomainIdentifier_ er den samme som _customDomainIdentifier_ i den brugerdefinerede MX-post for dit brugerdefinerede domæne, der vises før mail.protection.outlook.com. I følgende MX-post for domænets contoso.com er _customDomainIdentifier_ f.eks. contoso-com:

  > contoso.com.  3600 IN MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain er_ det domæne, du brugte, da du tilmeldte dig Microsoft 365. Startdomæner slutter altid onmicrosoft.com. Du kan finde oplysninger om, hvordan du fastlægger dit indledende domæne, under [Ofte stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Hvis du f.eks. har et indledende domæne med cohovineyardandwinery.onmicrosoft.com og to brugerdefinerede domæner cohovineyard.com og cohowinery.com, skal du konfigurere to CNAME-poster for hvert ekstra domæne i alt fire CNAME-poster.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohovineyard-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector1._domainkey
Points to address or value:    selector1-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-cohowinery-com._domainkey.cohovineyardandwinery.onmicrosoft.com
TTL:                3600
```

> [!NOTE]
> Det er vigtigt at oprette den anden post, men det er muligvis kun én af vælgerne, der er tilgængelige på oprettelses tidspunkt. Faktisk kan den anden vælger pege på en adresse, der endnu ikke er oprettet. Vi anbefaler stadig, at du opretter den anden CNAME-post, da din tasterotation vil være problemfri.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Trin til at aktivere DKIM-signering for dit brugerdefinerede domæne
<a name="EnableDKIMinO365"> </a>

Når du har publiceret CNAME-posterne i DNS, er du klar til at aktivere DKIM-signering via Microsoft 365. Du kan gøre dette enten via Microsoft 365 Administration ved hjælp af PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Sådan aktiverer du DKIM-signering for dit brugerdefinerede domæne Microsoft 365 Defender portalen

1. I  portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til Mail **& politikker** \> for **samarbejde & Politikker** \> \> for trussel om regler **DKIM** i **sektionen** Regler. For at gå direkte til DKIM-siden skal du bruge <https://security.microsoft.com/dkimv2>.

2. På **DKIM-siden** skal du vælge domænet ved at klikke på navnet.

3. I pop op-vindue med oplysninger, der vises, skal du ændre Indstillingen Signer meddelelser for dette domæne med **DKIM-signaturer** til Aktiveret **(**![til/fra.](../../media/scc-toggle-on.png))

   Når du er færdig, skal du klikke på **Roter DKIM-taster**.

4. Gentag disse trin for hvert brugerdefinerede domæne.

5. Hvis du konfigurerer DKIM for første gang og ser fejlen "Ingen DKIM-nøgler gemt for dette domæne", skal du bruge Windows PowerShell for at aktivere DKIM-signering som beskrevet i næste trin.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>Sådan aktiverer du DKIM-signering for dit brugerdefinerede domæne ved hjælp af PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="Fejlen &quot;Ingen DKIM-nøgler gemt for dette domæne&quot;.":::
> Hvis du konfigurerer DKIM for første gang og får vist fejlen "Ingen DKIM-nøgler gemt for dette domæne", `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`skal du fuldføre kommandoen i trin 2 nedenfor (f.eks. ) for at få vist nøglen.

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug følgende syntaks:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> er navnet på det brugerdefinerede domæne, du vil aktivere DKIM-signering for.

   I dette eksempel kan DKIM-signering for domænet contoso.com:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>For at bekræfte at DKIM-signering er konfigureret korrekt til Microsoft 365

Vent et par minutter, før du følger disse trin for at bekræfte, at du har konfigureret DKIM korrekt. Dette giver tid til, at DKIM-oplysningerne om domænet kan være spredt over hele netværket.

- Send en meddelelse fra en konto på dit Microsoft 365 DKIM-aktiverede domæne til en anden mailkonto, f.eks. outlook.com eller Hotmail.com.
- Brug ikke en aol.com-konto til testformål. AOL springer muligvis DKIM-kontrollerne over, hvis SPF-kontrollerne består. Dette vil nullificere din test.
- Åbn meddelelsen, og kig på sidehovedet. Instruktioner til visning af brevhovedet for meddelelsen varierer afhængigt af din meddelelsesklient. Hvis du vil have vejledning til at få vist brevhoveder i Outlook, skal du [se Få vist internetmeddelelsesoverskrifter Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  Den DKIM-signerede meddelelse indeholder det værtsnavn og domæne, du definerede, da du publicerede CNAME-posterne. Meddelelsen ser ud som i dette eksempel:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Se efter Authentication-Results sidehoved. Mens hver modtagende tjeneste bruger et lidt andet format til at stemple den indgående mail, bør resultatet indeholde noget i form af **DKIM=pass** eller **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>Sådan konfigurerer du DKIM for mere end ét brugerdefineret domæne
<a name="DKIMMultiDomain"> </a>

Hvis du på et tidspunkt i fremtiden beslutter at tilføje et andet brugerdefineret domæne, og du vil aktivere DKIM for det nye domæne, skal du gennemføre trinnene i denne artikel for hvert domæne. Du skal specifikt udføre alle [trin i Hvad du skal gøre for at konfigurere DKIM manuelt](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Deaktivering af DKIM-signeringspolitikken for et brugerdefineret domæne
<a name="DisableDKIMSigningPolicy"> </a>

Deaktivering af signeringspolitikken deaktiverer ikke DKIM helt. Efter et stykke tid anvender Microsoft 365 automatisk standardpolitikken for dit domæne, hvis standardpolitikken stadig er i den aktiverede tilstand. Hvis du helt vil deaktivere DKIM, skal du deaktivere DKIM på både brugerdefinerede domæner og standarddomæner. Du kan finde flere oplysninger [i Standardfunktionsmåden for DKIM og Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

### <a name="to-disable-the-dkim-signing-policy-by-using-windows-powershell"></a>Sådan deaktiverer du DKIM-signeringspolitikken ved hjælp af Windows PowerShell

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør en af følgende kommandoer for hvert domæne, som du vil deaktivere DKIM-signering for.

   ```powershell
   $p = Get-DkimSigningConfig -Identity <Domain>
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Eksempel:

   ```powershell
   $p = Get-DkimSigningConfig -Identity contoso.com
   $p[0] | Set-DkimSigningConfig -Enabled $false
   ```

   Eller

   ```powershell
   Set-DkimSigningConfig -Identity $p[<number>].Identity -Enabled $false
   ```

   Hvor _tal_ er indekset for politikken. Eksempel:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>Standardfunktionsmåden for DKIM og Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

Hvis du ikke aktiverer DKIM, opretter Microsoft 365 automatisk en offentlig 2048-bit DKIM-nøgle til dit Microsoft Online Email Routing Address (MOERA)/indledende domæne og den tilknyttede private nøgle, som vi gemmer internt i vores datacenter. Som standard bruger Microsoft 365 en standardsigneringskonfiguration til domæner, der ikke har en politik på plads. Det betyder, at hvis du ikke selv konfigurerer DKIM, bruger Microsoft 365 sin standardpolitik og nøgler, den opretter, for at aktivere DKIM for dit domæne.

Hvis du deaktiverer DKIM-signering på dit brugerdefinerede domæne efter aktivering efter et stykke tid, vil Microsoft 365 automatisk anvende MOERA/den indledende domænepolitik for dit brugerdefinerede domæne.

Antag i følgende eksempel, at DKIM for fabrikam.com blev aktiveret af Microsoft 365, ikke af administratoren af domænet. Det betyder, at de nødvendige CNAMEs ikke findes i DNS. DKIM-signaturer til mail fra dette domæne ser cirka sådan ud:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

I dette eksempel indeholder værtsnavnet og domænet de værdier, som CNAME ville pege på, hvis DKIM-signering for fabrikam.com var blevet aktiveret af domæneadministratoren. Hver enkelt meddelelse, der sendes fra Microsoft 365, bliver DKIM-signeret. Hvis du selv aktiverer DKIM, vil domænet være det samme som domænet i Fra:-adressen, i dette tilfælde fabrikam.com. Hvis du ikke gør det, justeres det ikke, og i stedet bruges din organisations indledende domæne. Du kan finde oplysninger om, hvordan du fastlægger dit indledende domæne, under [Ofte stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>Konfigurer DKIM, så en tredjepartstjeneste kan sende, eller efterligne, mail på vegne af dit brugerdefinerede domæne
<a name="SetUp3rdPartyspoof"> </a>

Nogle masseudbydere af mail eller software-som-en-tjenesteudbydere, gør det muligt at konfigurere DKIM-nøgler for mails, der stammer fra deres tjenester. Dette kræver koordinering mellem dig selv og tredjeparten for at konfigurere de nødvendige DNS-poster. Nogle tredjepartsservere kan have deres egne CNAME-poster med forskellige vælgere. Der er ikke to organisationer, der gør det på præcis samme måde. I stedet afhænger processen helt af organisationen.

Et eksempel på en meddelelse, der viser en korrekt konfigureret DKIM for contoso.com, bulkemailprovider.com kan se sådan ud:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

For at opnå dette resultat i dette eksempel:

1. Massemailudbyder gav Contoso en offentlig DKIM-nøgle.

2. Contoso har udgivet DKIM-nøglen til dens DNS-post.

3. Når du sender mail, signerer massemailudbyderen nøglen med den tilsvarende private nøgle. Ved at gøre dette vedhæftede massemailudbyderen DKIM-signaturen til brevhovedet.

4. Modtagende mailsystemer udfører en DKIM-kontrol ved at godkende værdien DKIM-Signature d=\<domain\> i domænet i meddelelsens Fra:(5322.Fra)-adresse. I dette eksempel svarer værdierne til hinanden:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>Identificer domæner, der ikke sender mails

Organisationer bør udtrykkeligt angive, om et domæne ikke sender mail ved at angive `v=DKIM1; p=` DKIM-posten for disse domæner. Det anbefales, at modtagende mailservere, at der ikke er nogen gyldige offentlige nøgler for domænet, og at mails, der hævder at være fra dette domæne, skal afvises. Du skal gøre dette for hvert domæne og underdomæne ved hjælp af et jokertegn DKIM.

DKIM-posten ville f.eks. se sådan ud:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Næste trin: Når du har konfigureret DKIM til Microsoft 365
<a name="DKIMNextSteps"> </a>

**SELVOM DKIM er designet til at forhindre spoofing, fungerer DKIM bedre med SPF og DMARC.**

Når du har konfigureret DKIM, skal du gøre det, hvis du ikke allerede har konfigureret SPF. Hvis du vil have en hurtig introduktion til SPF og få det konfigureret hurtigt, skal du se Konfigurer [**SPF i Microsoft 365 for at forhindre spoofing**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Hvis du vil have en mere dybdegående forståelse af, hvordan Microsoft 365 bruger SPF, eller til fejlfinding eller ikke-standardinstallationer, f.eks. hybride installationer, skal du starte med [Sådan bruger Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

Læs derefter Brug [**DMARC til at validere mail**](use-dmarc-to-validate-email.md). [Antispam-brevhoveder indeholder de syntaks](anti-spam-message-headers.md)- og brevhovedfelter, der bruges Microsoft 365 til DKIM-kontroller.

**Denne test validerer** , om DKIM-signeringskonfigurationen er konfigureret korrekt, og at de korrekte DNS-poster er blevet publiceret.

> [!NOTE]
> Denne funktion kræver en Microsoft 365 administratorkonto. Denne funktion er ikke tilgængelig for Microsoft 365 Government, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Germany.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Kør test: DKIM</a></p>
</div>

## <a name="more-information"></a>Flere oplysninger

Nøglerotation via PowerShell: [Roter-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[Brug DMARC til at validere mail](use-dmarc-to-validate-email.md)
