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
description: Få mere at vide om, hvordan du bruger DkIM (DomainKeys Identified Mail) med Microsoft 365 til at sikre, at destinationsmailsystemerne har tillid til meddelelser, der sendes fra dit brugerdefinerede domæne.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 87f565d5058edff9ebde5af6e2cf84ca3e8262b4
ms.sourcegitcommit: 38a18b0195d99222c2c6da0c80838d24b5f66b97
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/28/2022
ms.locfileid: "65772144"
---
# <a name="use-dkim-to-validate-outbound-email-sent-from-your-custom-domain"></a>Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

 Denne artikel indeholder en liste over trinnene til at bruge DomainKeys Identified Mail (DKIM) med Microsoft 365 til at sikre, at destinationens mailsystemer har tillid til meddelelser, der sendes udgående fra dit brugerdefinerede domæne.

I denne artikel:

- [Sådan fungerer DKIM bedre end SPF alene for at forhindre skadelig spoofing](#how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing)
- [Trin til oprettelse, aktivering og deaktivering af DKIM fra Microsoft 365 Defender portal](#steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal)
- [Trin til manuelt at opgradere dine 1024-bit nøgler til 2048-bit DKIM-krypteringsnøgler](#steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys)
- [Trin til manuel konfiguration af DKIM](#steps-to-manually-set-up-dkim)
- [Trin til konfiguration af DKIM for mere end ét brugerdefineret domæne](#to-configure-dkim-for-more-than-one-custom-domain)
- [Deaktivering af DKIM-signeringspolitikken for et brugerdefineret domæne](#disabling-the-dkim-signing-policy-for-a-custom-domain)
- [Standardfunktionsmåde for DKIM og Microsoft 365](#default-behavior-for-dkim-and-microsoft-365)
- [Konfigurer DKIM, så en tredjepartstjeneste kan sende eller spoofe mail på vegne af dit brugerdefinerede domæne](#set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain)
- [Næste trin: Når du har konfigureret DKIM til Microsoft 365](#next-steps-after-you-set-up-dkim-for-microsoft-365)

> [!NOTE]
> Microsoft 365 konfigurerer automatisk DKIM til sine oprindelige domæner med "onmicrosoft.com". Det betyder, at du ikke behøver at gøre noget for at konfigurere DKIM for eventuelle indledende domænenavne (f.eks. litware.onmicrosoft.com). Du kan få flere oplysninger om domæner under [Ofte stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

DKIM er en af de tre godkendelsesmetoder (SPF, DKIM og DMARC), der hjælper med at forhindre hackere i at sende meddelelser, der ligner de kommer fra dit domæne.

I DKIM kan du føje en digital signatur til udgående mails i meddelelsesheaderen. Når du konfigurerer DKIM, giver du dit domæne tilladelse til at knytte eller signere dets navn til en mail ved hjælp af kryptografisk godkendelse. Mailsystemer, der modtager mail fra dit domæne, kan bruge denne digitale signatur til at kontrollere, om indgående mail er legitim.

Grundlæggende krypterer en privat nøgle headeren i et domænes udgående mail. Den offentlige nøgle publiceres i domænets DNS-poster, og modtagelsesservere kan bruge denne nøgle til at afkode signaturen. DKIM bekræftelse hjælper de modtagende servere bekræfte mailen virkelig kommer fra dit domæne og ikke nogen *spoofing* dit domæne.

> [!TIP]
>Du kan også vælge ikke at gøre noget ved DKIM for dit brugerdefinerede domæne. Hvis du ikke konfigurerer DKIM for dit brugerdefinerede domæne, opretter Microsoft 365 et privat og offentligt nøglepar, aktiverer DKIM-signering og konfigurerer derefter Microsoft 365 standardpolitik for dit brugerdefinerede domæne.

 Microsoft-365's indbyggede DKIM-konfiguration er tilstrækkelig dækning for de fleste kunder. Du skal dog konfigurere DKIM manuelt for dit brugerdefinerede domæne i følgende tilfælde:

- Du har mere end ét brugerdefineret domæne i Microsoft 365
- Du skal også konfigurere DMARC (**anbefales**)
- Du vil have kontrol over din private nøgle
- Du vil tilpasse dine CNAME-poster
- Du vil konfigurere DKIM-nøgler til mail, der stammer fra et tredjepartsdomæne, f.eks. hvis du bruger en massemailer fra tredjepart.

## <a name="how-dkim-works-better-than-spf-alone-to-prevent-malicious-spoofing"></a>Sådan fungerer DKIM bedre end SPF alene for at forhindre skadelig spoofing
<a name="HowDKIMWorks"> </a>

SPF føjer oplysninger til en meddelelseskonvolut, men DKIM *krypterer* en signatur i meddelelsesheaderen. Når du videresender en meddelelse, kan dele af meddelelsens konvolut fjernes af videresendelsesserveren. Da den digitale signatur forbliver i mailen, fordi den er en del af mailheaderen, fungerer DKIM også, når en meddelelse er videresendt som vist i følgende eksempel.

![Diagram, der viser en videresendt meddelelse, der sender DKIM-godkendelse, hvor SPF-kontrollen mislykkes.](../../media/28f93b4c-97e7-4309-acc4-fd0d2e0e3377.jpg)

Hvis du i dette eksempel kun havde publiceret en SPF TXT-post for dit domæne, kunne modtagerens mailserver have markeret din mail som spam og genereret et falsk positivt resultat. **Tilføjelsen af DKIM i dette scenarie reducerer *falsk positiv* spamrapportering.** Da DKIM er afhængig af kryptering af offentlige nøgler for at godkende og ikke kun IP-adresser, anses DKIM for at være en meget stærkere form for godkendelse end SPF. Vi anbefaler, at du bruger både SPF og DKIM samt DMARC i din udrulning.

> [!TIP]
> DKIM bruger en privat nøgle til at indsætte en krypteret signatur i brevhovederne. Signaturdomænet eller det udgående domæne indsættes som værdien af feltet **d=** i headeren. Bekræftelsesdomænet eller modtagerens domæne bruger derefter feltet **d=** til at slå den offentlige nøgle op fra DNS og godkende meddelelsen. Hvis meddelelsen bekræftes, overføres DKIM-kontrollen.

## <a name="steps-to-create-enable-and-disable-dkim-from-microsoft-365-defender-portal"></a>Trin til oprettelse, aktivering og deaktivering af DKIM fra Microsoft 365 Defender portal

Alle de accepterede domæner for din lejer vises på Microsoft 365 Defender portalen under DKIM-siden. Hvis du ikke kan se det, skal du tilføje dit accepterede domæne fra [siden domæner](/microsoft-365/admin/setup/add-domain#add-a-domain).
Når dit domæne er tilføjet, skal du følge trinnene som vist nedenfor for at konfigurere DKIM.

Trin 1: Klik på det domæne, du vil konfigurere DKIM på DKIM-siden (https://security.microsoft.com/dkimv2 eller https://protection.office.com/dkimv2).

:::image type="content" source="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png" alt-text="DKIM-siden på Microsoft 365 Defender portalen med et domæne valgt" lightbox="../../media/126996261-2d331ec1-fc83-4a9d-a014-bd7e1854eb07.png":::

Trin 2: Skub til/fra-knappen for at **aktivere**. Du får vist et pop op-vindue, der angiver, at du skal tilføje CNAME-poster.

:::image type="content" source="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png" alt-text="Pop op-vinduet Domæneoplysninger med knappen Opret DKIM-nøgler" lightbox="../../media/127001645-4ccf89e6-6310-4a91-85d6-aaedbfd501d3.png":::

Trin 3: Kopiér de CNAMES,der vises i pop op-vinduet

:::image type="content" source="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png" alt-text="Pop op-vinduet Publicer CNAMEs, der indeholder de to CNAME-poster, der skal kopieres" lightbox="../../media/127001787-3cce2c29-e0e4-4712-af53-c51dcba33c46.png":::

Trin 4: Publicer de kopierede CNAME-poster til din DNS-tjenesteudbyder.

På din DNS-udbyders websted kan du tilføje CNAME-poster for DKIM, som du vil aktivere. Sørg for, at felterne er indstillet til følgende værdier for hvert af dem:

```text
Record Type: CNAME (Alias)
> Host: Paste the values you copy from DKIM page.
Points to address: Copy the value from DKIM page.
TTL: 3600 (or your provider default)
```

Trin 5: Vend tilbage til DKIM-siden for at aktivere DKIM.

:::image type="content" source="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png" alt-text="Til/fra-knappen for at aktivere DKIM" lightbox="../../media/126995186-9b3fdefa-a3a9-4f5a-9304-1099a2ce7cef.png":::

Hvis du får vist fejlen CNAME-post ikke findes, kan det skyldes:

1. Synkronisering med DNS-serveren, som kan tage nogle få sekunder til timer, hvis problemet fortsætter, skal du gentage trinnene igen
2. Kontrollér, om der er fejl i kopieringsindsætning, f.eks. ekstra plads eller faner osv.

Hvis du vil deaktivere DKIM, skal du skifte tilbage til deaktiveringstilstand

## <a name="steps-to-manually-upgrade-your-1024-bit-keys-to-2048-bit-dkim-encryption-keys"></a>Trin til manuelt at opgradere dine 1024-bit nøgler til 2048-bit DKIM-krypteringsnøgler
<a name="1024to2048DKIM"> </a>

> [!NOTE]
> Microsoft 365 konfigurerer automatisk DKIM for *onmicrosoft.com* domæner. Der kræves ingen trin for at bruge DKIM til indledende domænenavne (f.eks. litware.*onmicrosoft.com*). Du kan få flere oplysninger om domæner under [Ofte stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

Da både 1024- og 2048-bittæthed understøttes for DKIM-nøgler, vil disse retninger fortælle dig, hvordan du opgraderer din 1024-bit nøgle til 2048 i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Nedenstående trin er til to use-cases. Vælg den, der passer bedst til din konfiguration.

- Når du **allerede har konfigureret DKIM**, roterer du bittætheden ved at køre følgende kommando:

  ```powershell
  Rotate-DkimSigningConfig -KeySize 2048 -Identity <DkimSigningConfigIdParameter>
  ```

  **Eller**

- Kør følgende kommando for at få en **ny implementering af DKIM**:

  ```powershell
  New-DkimSigningConfig -DomainName <Domain for which config is to be created> -KeySize 2048 -Enabled $true
  ```

Hold forbindelsen til Exchange Online PowerShell for at *bekræfte* konfigurationen ved at køre følgende kommando:

```powershell
Get-DkimSigningConfig -Identity <Domain for which the configuration was set> | Format-List
```

> [!TIP]
> Denne nye 2048-bit nøgle træder i kraft på RotateOnDate og sender mails med 1024-bit-nøglen i mellemtiden. Efter fire dage kan du teste igen med 2048-bit-nøglen (dvs. når rotationen træder i kraft til den anden selektor).

Hvis du vil rotere til den anden selektor efter fire dage og bekræfte, at 2048-bittæthed er i brug, skal du manuelt rotere den anden selektortast ved hjælp af den relevante cmdlet, der er angivet ovenfor.

Du kan finde detaljerede oplysninger om syntaks og parametre i følgende artikler: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig), [New-DkimSigningConfig](/powershell/module/exchange/new-dkimsigningconfig) og [Get-DkimSigningConfig](/powershell/module/exchange/get-dkimsigningconfig).

## <a name="steps-to-manually-set-up-dkim"></a>Trin til manuel konfiguration af DKIM
<a name="SetUpDKIMO365"> </a>

Hvis du vil konfigurere DKIM, skal du udføre disse trin:

- [Publicer to CNAME-poster for dit brugerdefinerede domæne i DNS](use-dkim-to-validate-outbound-email.md#Publish2CNAME)
- [Aktivér DKIM-signering for dit brugerdefinerede domæne](use-dkim-to-validate-outbound-email.md#EnableDKIMinO365)

### <a name="publish-two-cname-records-for-your-custom-domain-in-dns"></a>Publicer to CNAME-poster for dit brugerdefinerede domæne i DNS
<a name="Publish2CNAME"> </a>

For hvert domæne, som du vil tilføje en DKIM-signatur for i DNS, skal du publicere to CNAME-poster.

> [!NOTE]
> Hvis du ikke har læst hele artiklen, har du måske savnet disse tidsbesparende PowerShell-forbindelsesoplysninger: [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

Kør følgende kommandoer i Exchange Online PowerShell for at oprette selektorposterne:

```powershell
New-DkimSigningConfig -DomainName <domain> -Enabled $false
Get-DkimSigningConfig -Identity <domain> | Format-List Selector1CNAME, Selector2CNAME
```

Hvis du har klargjort brugerdefinerede domæner ud over det oprindelige domæne i Microsoft 365, skal du publicere to CNAME-poster for hvert ekstra domæne. Så hvis du har to domæner, skal du publicere to ekstra CNAME-poster osv.

Brug følgende format til CNAME-posterne.

> [!IMPORTANT]
> Hvis du er en af vores GCC High-kunder, beregner vi _customDomainIdentifier_ forskelligt! I stedet for at slå MX-posten op for dit _initialDomæne_ for at beregne _customDomainIdentifier_, beregner vi den i stedet direkte fra det brugerdefinerede domæne. Hvis dit tilpassede domæne f.eks. er "contoso.com" bliver dit _brugerdefineredeDomæneIdentifier_ til "contoso-com", erstattes alle perioder med en bindestreg. Så uanset hvilken MX-post dit _initialDomæne_ peger på, skal du altid bruge ovenstående metode til at beregne den _brugerdefineredeDomainIdentifier_ , der skal bruges i dine CNAME-poster.

```console
Host name:            selector1._domainkey
Points to address or value:    selector1-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600

Host name:            selector2._domainkey
Points to address or value:    selector2-<customDomainIdentifier>._domainkey.<initialDomain>
TTL:                3600
```

Hvor:

- For Microsoft 365 vil selektorerne altid være "selektor1" eller "selektor2".
- _customDomainIdentifier_ er den samme som _customDomainIdentifier_ i den brugerdefinerede MX-post for dit brugerdefinerede domæne, der vises før mail.protection.outlook.com. I følgende MX-post for domænet contoso.com er _customDomainIdentifier_ f.eks. contoso-com:

  > contoso.com.  3600 I MX 5 contoso-com.mail.protection.outlook.com

- _initialDomain_ er det domæne, du brugte, da du tilmeldte dig Microsoft 365. Indledende domæner slutter altid i onmicrosoft.com. Du kan finde oplysninger om, hvordan du bestemmer dit oprindelige domæne, under [Ofte stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

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
> Det er vigtigt at oprette den anden post, men kun én af selektorerne kan være tilgængelig på oprettelsestidspunktet. Den anden selektor kan i bund og grund pege på en adresse, der endnu ikke er oprettet. Vi anbefaler stadig, at du opretter den anden CNAME-post, fordi din nøglerotation fungerer problemfrit.

### <a name="steps-to-enable-dkim-signing-for-your-custom-domain"></a>Trin til aktivering af DKIM-signering for dit brugerdefinerede domæne
<a name="EnableDKIMinO365"> </a>

Når du har publiceret CNAME-posterne i DNS, er du klar til at aktivere DKIM-signering via Microsoft 365. Du kan gøre dette enten via Microsoft 365 Administration eller ved hjælp af PowerShell.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-in-the-microsoft-365-defender-portal"></a>Sådan aktiverer du DKIM-signering for dit brugerdefinerede domæne på Microsoft 365 Defender-portalen

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Rules** \> **Threat policies** \> **DKIM** i afsnittet **Regler**. Hvis du vil gå direkte til DKIM-siden, skal du bruge <https://security.microsoft.com/dkimv2>.

2. På siden **DKIM** skal du vælge domænet ved at klikke på navnet.

3. I pop op-vinduet med detaljer, der vises, skal du ændre **indstillingen Signeringsmeddelelser for dette domæne med INDSTILLINGEN DKIM-signaturer** til **Aktiveret** (![Slå til](../../media/scc-toggle-on.png)).

   Når du er færdig, skal du klikke på **Roter DKIM-taster**.

4. Gentag dette trin for hvert brugerdefineret domæne.

5. Hvis du konfigurerer DKIM for første gang og ser fejlen 'Ingen DKIM-nøgler gemt til dette domæne', skal du bruge Windows PowerShell til at aktivere DKIM-signering som forklaret i næste trin.

#### <a name="to-enable-dkim-signing-for-your-custom-domain-by-using-powershell"></a>Sådan aktiverer du DKIM-signering for dit brugerdefinerede domæne ved hjælp af PowerShell

> [!IMPORTANT]
> :::image type="content" source="../../media/dkim.png" alt-text="Ingen DKIM-nøgler, der er gemt for denne domænefejl" lightbox="../../media/dkim.png":::
> Hvis du konfigurerer DKIM første gang og får vist fejlen 'Ingen DKIM-nøgler, der er gemt for dette domæne', `Set-DkimSigningConfig -Identity contoso.com -Enabled $true`skal du fuldføre kommandoen i trin 2 nedenfor (f.eks. ) for at se nøglen.

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug følgende syntaks:

   ```powershell
   Set-DkimSigningConfig -Identity <Domain> -Enabled $true
   ```

   \<Domain\> er navnet på det brugerdefinerede domæne, du vil aktivere DKIM-signering for.

   I dette eksempel aktiveres DKIM-signering for domæne contoso.com:

   ```powershell
   Set-DkimSigningConfig -Identity contoso.com -Enabled $true
   ```

#### <a name="to-confirm-dkim-signing-is-configured-properly-for-microsoft-365"></a>Sådan bekræfter du, at DKIM-signering er konfigureret korrekt til Microsoft 365

Vent et par minutter, før du følger disse trin for at bekræfte, at du har konfigureret DKIM korrekt. Dette giver tid til, at DKIM-oplysninger om domænet kan spredes over hele netværket.

- Send en meddelelse fra en konto i dit Microsoft 365 DKIM-aktiverede domæne til en anden mailkonto, f.eks. outlook.com eller Hotmail.com.
- Brug ikke en aol.com konto til testformål. AOL kan springe DKIM-kontrollen over, hvis SPF-kontrollen passerer. Dette annullerer din test.
- Åbn meddelelsen, og se overskriften. Instruktioner til visning af brevhovedet for meddelelsen varierer afhængigt af din meddelelsesklient. Du kan finde oplysninger om visning af brevhoveder i Outlook under [Få vist brevhoveder på internettet i Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

  Den DKIM-signerede meddelelse indeholder det værtsnavn og domæne, du definerede, da du publicerede CNAME-posterne. Meddelelsen ser nogenlunde sådan ud i dette eksempel:

  ```console
    From: Example User <example@contoso.com>
    DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
        s=selector1; d=contoso.com; t=1429912795;
        h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
        bh=<body hash>;
        b=<signed field>;
  ```

- Søg efter overskriften Authentication-Results. Mens hver modtagelsestjeneste bruger et lidt forskelligt format til at stemple den indgående post, bør resultatet inkludere noget i stil med **DKIM=pass** eller **DKIM=OK**.

## <a name="to-configure-dkim-for-more-than-one-custom-domain"></a>Sådan konfigurerer du DKIM for mere end ét brugerdefineret domæne
<a name="DKIMMultiDomain"> </a>

Hvis du på et tidspunkt i fremtiden beslutter at tilføje et andet brugerdefineret domæne, og du vil aktivere DKIM for det nye domæne, skal du fuldføre trinnene i denne artikel for hvert domæne. Du skal specifikt fuldføre alle trin i [Hvad du skal gøre for at konfigurere DKIM manuelt](use-dkim-to-validate-outbound-email.md#SetUpDKIMO365).

## <a name="disabling-the-dkim-signing-policy-for-a-custom-domain"></a>Deaktivering af DKIM-signeringspolitikken for et brugerdefineret domæne
<a name="DisableDKIMSigningPolicy"> </a>

Deaktivering af signeringspolitikken deaktiverer ikke DKIM fuldstændigt. Efter et stykke tid anvender Microsoft 365 automatisk standardpolitikken for dit domæne, hvis standardpolitikken stadig er i aktiveret tilstand. Hvis du ønsker helt at deaktivere DKIM, skal du deaktivere DKIM på både brugerdefinerede og standarddomæner. Du kan få flere oplysninger under [Standardfunktionsmåde for DKIM og Microsoft 365](use-dkim-to-validate-outbound-email.md#DefaultDKIMbehavior).

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

   Hvor _tallet_ er indekset for politikken. Eksempel:

   ```powershell
   Set-DkimSigningConfig -Identity $p[0].Identity -Enabled $false
   ```

## <a name="default-behavior-for-dkim-and-microsoft-365"></a>Standardfunktionsmåde for DKIM og Microsoft 365
<a name="DefaultDKIMbehavior"> </a>

Hvis du ikke aktiverer DKIM, opretter Microsoft 365 automatisk en offentlig 2048-bit DKIM-nøgle til dit MOERA-domæne (Microsoft Online Email Routing Address) og den tilknyttede private nøgle, som vi gemmer internt i vores datacenter. Microsoft 365 bruger som standard en standardkonfiguration for signering for domæner, der ikke har en politik på plads. Det betyder, at hvis du ikke selv konfigurerer DKIM, vil Microsoft 365 bruge sin standardpolitik og nøgler, den opretter, til at aktivere DKIM for dit domæne.

Hvis du deaktiverer DKIM-signering på dit brugerdefinerede domæne, efter at du har aktiveret det, vil Microsoft 365 automatisk anvende MOERA/indledende domænepolitik for dit brugerdefinerede domæne.

Lad os i det følgende eksempel antage, at DKIM for fabrikam.com er aktiveret af Microsoft 365, ikke af domæneadministratoren. Det betyder, at de påkrævede CNAMEs ikke findes i DNS. DKIM-signaturer for mail fra dette domæne vil se nogenlunde sådan ud:

```console
From: Second Example <second.example@fabrikam.com>
DKIM-Signature: v=1; a=rsa-sha256; q=dns/txt; c=relaxed/relaxed;
    s=selector1-fabrikam-com; d=contoso.onmicrosoft.com; t=1429912795;
    h=From:To:Message-ID:Subject:MIME-Version:Content-Type;
    bh=<body hash>;
    b=<signed field>;
```

I dette eksempel indeholder værtsnavnet og domænet de værdier, som CNAME ville pege på, hvis DKIM-signering for fabrikam.com var blevet aktiveret af domæneadministratoren. Til sidst bliver hver enkelt meddelelse sendt fra Microsoft 365 DKIM-signeret. Hvis du selv aktiverer DKIM, vil domænet være det samme som domænet i Fra: adresse, i dette tilfælde fabrikam.com. Hvis du ikke gør det, justeres den ikke og bruger i stedet organisationens oprindelige domæne. Du kan finde oplysninger om, hvordan du bestemmer dit oprindelige domæne, under [Ofte stillede spørgsmål om domæner](../../admin/setup/domains-faq.yml#why-do-i-have-an--onmicrosoft-com--domain).

## <a name="set-up-dkim-so-that-a-third-party-service-can-send-or-spoof-email-on-behalf-of-your-custom-domain"></a>Konfigurer DKIM, så en tredjepartstjeneste kan sende eller spoofe mail på vegne af dit brugerdefinerede domæne
<a name="SetUp3rdPartyspoof"> </a>

Nogle udbydere af massemailtjenester eller software-as-a-tjenesteudbydere giver dig mulighed for at konfigurere DKIM-nøgler til mail, der stammer fra deres tjeneste. Dette kræver koordinering mellem dig selv og tredjeparten for at kunne oprette de nødvendige DNS-poster. Nogle tredjepartsservere kan have deres egne CNAME-poster med forskellige selektorer. Ikke to organisationer gør det på præcis samme måde. Processen afhænger i stedet udelukkende af organisationen.

En eksempelmeddelelse, der viser en korrekt konfigureret DKIM til contoso.com og bulkemailprovider.com kan se sådan ud:

```console
Return-Path: <communication@bulkemailprovider.com>
 From: <sender@contoso.com>
 DKIM-Signature: s=s1024; d=contoso.com
 Subject: Here is a message from Bulk Email Provider's infrastructure, but with a DKIM signature authorized by contoso.com
```

I dette eksempel skal du for at opnå dette resultat:

1. Massemailudbyder gav Contoso en offentlig DKIM-nøgle.

2. Contoso publicerede DKIM-nøglen til sin DNS-post.

3. Når du sender mail, signerer massemailudbyder nøglen med den tilsvarende private nøgle. Ved at gøre det vedhæftede Massemailudbyder DKIM-signaturen til meddelelsesheaderen.

4. Modtagelse af mailsystemer udfører en DKIM-kontrol ved at godkende den DKIM-Signature d=\<domain\> værdi i forhold til domænet i meddelelsens Fra-adresse (5322.From). I dette eksempel matcher værdierne:

   > sender@**contoso.com**

   > d=**contoso.com**

## <a name="identify-domains-that-do-not-send-email"></a>Identificer domæner, der ikke sender mail

Organisationer skal eksplicit angive, om et domæne ikke sender mail, ved at angive `v=DKIM1; p=` i DKIM-posten for disse domæner. Dette anbefaler, at du modtager mailservere, at der ikke er nogen gyldige offentlige nøgler for domænet, og alle mails, der hævder at være fra det pågældende domæne, bør afvises. Det skal du gøre for hvert domæne og underdomæne ved hjælp af jokertegnet DKIM.

DKIM-posten vil f.eks. se sådan ud:

```console
*._domainkey.SubDomainThatShouldntSendMail.contoso.com. TXT "v=DKIM1; p="
```

## <a name="next-steps-after-you-set-up-dkim-for-microsoft-365"></a>Næste trin: Når du har konfigureret DKIM til Microsoft 365
<a name="DKIMNextSteps"> </a>

**Selvom DKIM er designet til at forhindre spoofing, fungerer DKIM bedre med SPF og DMARC.**

Når du har oprettet DKIM, bør du gøre det, hvis du ikke allerede har oprettet SPF. Du kan få en hurtig introduktion til SPF og få den konfigureret hurtigt under [**Konfigurer SPF i Microsoft 365 for at forhindre spoofing**](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Hvis du vil have en mere detaljeret forståelse af, hvordan Microsoft 365 bruger SPF eller til fejlfinding eller ikke-standardinstallationer, f.eks. hybridinstallationer, skal du starte med [Sådan bruger Microsoft 365 SPF (Sender Policy Framework) til at forhindre spoofing](how-office-365-uses-spf-to-prevent-spoofing.md).

Derefter skal du se [**Brug DMARC til at validere mail**](use-dmarc-to-validate-email.md). [Brevhoveder mod spam](anti-spam-message-headers.md) indeholder syntaks- og headerfelter, der bruges af Microsoft 365 til DKIM-kontroller.

**Denne test validerer** , at konfigurationen af DKIM-signering er konfigureret korrekt, og at de korrekte DNS-poster er blevet publiceret.

> [!NOTE]
> Denne funktion kræver en Microsoft 365 administratorkonto. Denne funktion er ikke tilgængelig for Microsoft 365 offentlige myndigheder, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Tyskland.

<div class="nextstepaction">
<p><a href="https://admin.microsoft.com/AdminPortal/?searchSolutions=DKIM#/homepage" data-linktype="external">Kør test: DKIM</a></p>
</div>

## <a name="more-information"></a>Flere oplysninger

Nøglerotation via PowerShell: [Rotate-DkimSigningConfig](/powershell/module/exchange/rotate-dkimsigningconfig)

[Brug DMARC til at validere mail](/microsoft-365/security/office-365-security/use-dmarc-to-validate-email?view=o365-worldwide&preserve-view=true)

[Brug ARC-afsendere, der er tillid til, til legitime mailflow](/microsoft-365/security/office-365-security/use-arc-exceptions-to-mark-trusted-arc-senders?view=o365-21vianet&branch=tracyp_emailauth)