---
title: Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser
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
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Administratorer kan lære, hvordan de bruger den avancerede leveringspolitik i Exchange Online Protection (EOP) til at identificere meddelelser, der ikke skal filtreres i bestemte understøttede scenarier (phishingsimulering fra tredjeparter og meddelelser leveret til sikkerhedshandlinger ) postkasser (SecOps).
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bf564765b9bb896fcfcdac01961d414139199603
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63597899"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

For at sikre din organisation som standard tillader Exchange Online Protection (EOP) ikke sikre lister eller filtreringstillidslister for [meddelelser, der](secure-by-default.md) er identificeret som malware eller phishing med høj sikkerhed. Men der er bestemte scenarier, der kræver levering af ufiltrerede meddelelser. Eksempel:

- **Tredjeparts phishing-simulering**: Simulerede angreb kan hjælpe dig med at identificere følsomme brugere, før et rigtigt angreb påvirker din organisation.
- **Sikkerhedshandlinger (SecOps) postkasser**: Dedikerede postkasser, der bruges af sikkerhedsteams til at indsamle og analysere ufiltrerede meddelelser (både gode og dårlige).

Du bruger politikken _for avanceret_ levering Microsoft 365 at forhindre indgående _meddelelser i disse specifikke_ scenarier i at blive filtreret.<sup>\*</sup> Den avancerede leveringspolitik sikrer, at meddelelser i disse scenarier opnår følgende resultater:

- Filtre i EOP og Microsoft Defender for Office 365 ikke nogen handling på disse meddelelser.<sup>\*</sup>
- [TØM (Zero-hour TØM)](zero-hour-auto-purge.md) for spam og phishing gør ikke noget ved disse meddelelser.<sup>\*</sup>
- [Der udløses ikke](/microsoft-365/compliance/alert-policies#default-alert-policies) standardsystemadvarsler for disse scenarier.
- [AIR og klyngedannelse i Defender for Office 365](office-365-air.md) ignorerer disse meddelelser.
- Specifikt for phishing-simulering fra tredjepart:
  - [Administratorindsendelser](admin-submission.md) genererer et automatisk svar, der fortæller, at meddelelsen er en del af en phishing-simuleringskampagne og ikke er en reel trussel. Beskeder og AIR udløses ikke. Oplevelsen af administratorindsendelser viser disse meddelelser som en simuleret trussel.
  - Når en bruger rapporterer en phishing-simuleringsmeddelelse ved hjælp af rapportmeddelelsen eller tilføjelsesprogrammet [Report Phishing](enable-the-report-message-add-in.md), genererer systemet ikke en besked, undersøgelse eller hændelse. Links eller filer bliver ikke detoneret, men meddelelsen vises også på fanen **Bruger rapporterede** meddelelser på **siden Indsendelser** .
  - [Pengeskab Links i Defender til Office 365](safe-links.md) ikke blokere eller deonere de specifikt identificerede URL-adresser i disse meddelelser, når der klikkes. URL-adresser ombrudt stadig, men de blokeres ikke.
  - [Pengeskab Vedhæftede filer i Defender Office 365](safe-attachments.md) ikke vedhæftede filer i disse meddelelser.

<sup>\*</sup> Du kan ikke tilsidesætte malwarefiltrering eller ZAP for malware.

Meddelelser, der identificeres af den avancerede leveringspolitik, er ikke sikkerhedstrusler, så meddelelserne er markeret med systemtilsidesættelser. Administratoroplevelser viser disse meddelelser som enten på grund af en tilsidesættelse af **et phishing-simuleringssystem** eller en **tilsidesættelse af et SecOps-postkassesystem** . Administratorer kan filtrere og analysere på disse systemtilsidesættelser i følgende oplevelser:

- [Trusselsstifinder/registreringer i realtid i Defender til Office 365 plan 2](threat-explorer.md): Administratoren kan filtrere på **systemets** tilsidesættelseskilde og vælge enten **Phishing-simulering** eller **SecOps-postkasse**.
- Siden [Mailenhed i trusselsstifinder/](mdo-email-entity-page.md)registreringer i realtid: Administratoren kan få vist en meddelelse, der er blevet tilladt af organisationens politik af enten **SecOps-postkasse** eller **phishing-simulering** **under** Lejers tilsidesættelse i sektionen Tilsidesættelse( **er** ).
- [Statusrapporten for trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report): Administratoren kan filtrere efter at få vist **data efter Systemtilsidesættelse** i rullemenuen og vælge at få vist meddelelser, der er tilladt på grund af en tilsidesættelse af et phishing-simuleringssystem. Hvis du vil have vist meddelelser, der er tilladt af SecOps-postkassens tilsidesættelse, kan du vælge diagramopdeling efter leveringssted i rullemenuen **Diagramoversigt efter** årsag.
- [Avanceret jagt i Microsoft Defender til slutpunkt](../defender-endpoint/advanced-hunting-overview.md): Phishing-simulering og tilsidesættelse af SecOps-postkassesystem vises som indstillinger i OrgLevelPolicy i EmailEvents.
- [Kampagnevisninger](campaigns.md): Administratoren kan filtrere på **systemets tilsidesættelseskilde og** vælge enten **Phishing-simulering** **eller SecOps-postkasse**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til siden **Avanceret levering** skal du åbne <https://security.microsoft.com/advanceddelivery>.

- Hvis du vil oprette forbindelse & Security & Compliance Center PowerShell, [skal du Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

- Du skal have tildelt tilladelser, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere eller fjerne konfigurerede indstillinger i politikken for avanceret levering, skal du være medlem af sikkerhedsadministratorrollegruppen i **Microsoft 365 Defender-portalen** og være medlem af rollegruppen Organisationsadministration **i Exchange Online**. 
  - For skrivebeskyttet adgang til politikken for avanceret levering skal du være medlem af **rollegrupperne Global læser** eller **Sikkerhedslæser** .

  Du kan finde flere [oplysninger under Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md) [og tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > Når brugere føjes til den Azure Active Directory rolle, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Brug portalen Microsoft 365 Defender til at konfigurere SecOps-postkasser i politikken for avanceret levering

1. I  portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & samarbejdspolitikker** \> **& Politikker** \> \> for trussel om regler **Avanceret** levering i **sektionen** Regler. For at gå direkte til siden **Avanceret levering skal** du bruge <https://security.microsoft.com/advanceddelivery>.

2. På siden **Avanceret** levering skal du bekræfte, **at fanen SecOps-postkasse** er markeret og derefter gøre et af følgende:
   - Klik ![på ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.
   - Hvis der ikke er nogen konfigurerede phishing-simulering, skal du klikke **på Tilføj**.

3. I pop op-pop op-menuen Rediger **SecOps-postkasser**, der åbnes, skal du angive en eksisterende Exchange Online-postkasse, du vil angive som SecOps-postkasse, ved at gøre et af følgende:
   - Klik i feltet, lad listen over postkasser blive løst, og vælg derefter postkassen.
   - Klik i feltet og begynd at skrive en identifikator for postkassen (navn, visningsnavn, alias, mailadresse, kontonavn osv.), og vælg postkassen (visningsnavn) fra resultaterne.

     Gentag dette trin så mange gange, det er nødvendigt. Distributionsgrupper er ikke tilladt.

     Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

4. Klik på **Gem**, når du er færdig.

De SecOps-postkasseposter, du konfigurerede, vises under **fanen SecOps-postkasse** . Hvis du vil foretage ændringer, skal du klikke ![på ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger** under fanen.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Brug portalen Microsoft 365 Defender til at konfigurere phishing-simuleringer fra tredjeparter i politikken for avanceret levering

1. I  portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til **Mail & samarbejdspolitikker** \> **& Politikker** \> \> for trussel om regler **Avanceret** levering i **sektionen** Regler. For at gå direkte til siden **Avanceret levering skal** du bruge <https://security.microsoft.com/advanceddelivery>.

2. Vælg fanen **Phishing-simulering** på **siden Avanceret** levering, og gør derefter et af følgende:
   - Klik ![på ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.
   - Hvis der ikke er nogen konfigurerede phishing-simulering, skal du klikke **på Tilføj**.

3. I pop **op-menuen Rediger phishing-simulering** fra tredjepart, der åbnes, skal du konfigurere følgende indstillinger:

   - **Domæne**: Udvid denne indstilling, og angiv mindst ét mailadressedomæne (f.eks. contoso.com) ved at klikke i feltet, angive en værdi og derefter trykke på Enter eller vælge den værdi, der vises under feltet. Gentag dette trin så mange gange, det er nødvendigt. Du kan tilføje op til 20 poster.

     > [!NOTE]
     > Brug domænet `5321.MailFrom` fra adressen (også kaldet **MAIL FROM-adresse**, P1-afsender eller konvolutafsender), der bruges i SMTP-afsendelsen af meddelelsen eller et DomainKeys Identified Mail-domæne (DKIM), som angivet af din phishing-simuleringsleverandør. 

   - **Afsendelse af IP**: Udvid denne indstilling, og angiv mindst én gyldig IPv4-adresse ved at klikke i feltet, angive en værdi og derefter trykke på Enter eller vælge den værdi, der vises under feltet. Gentag dette trin så mange gange, det er nødvendigt. Du kan tilføje op til 10 poster. Gyldige værdier er:
     - Enkelt IP: F.eks. 192.168.1.1.
     - IP-område: Eksempel: 192.168.0.1-192.168.0.254.
     - CIDR IP: F.eks. 192.168.0.1/25.
   - Simuleringswebadresser til at tillade: Udvid denne indstilling, og angiv eventuelt bestemte URL-adresser, som er en del af din phishing-simuleringskampagne, som ikke bør blokeres eller detoneres ved at klikke i feltet, angive en værdi og derefter trykke på Enter eller vælge den værdi, der vises under feltet. Du kan tilføje op til 10 poster. Du kan finde syntaksen for URL-adressen i [URL-syntaksen for lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Disse URL-adresser ombrudt på tidspunktet for klik, men de blokeres ikke.

   Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   > [!NOTE]
   > Hvis du vil konfigurere en phishing-simulering fra en tredjepart i Avanceret levering, skal du finde følgende oplysninger:
   > 
   > - Mindst ét **domæne** fra en af følgende kilder:
   >   - Adressen `5321.MailFrom` (også kaldet MAIL FROM-adressen, P1-afsenderen eller konvolutafsenderen).
   >   - DKIM-domænet.
   > - Mindst én **afsendelses-IP-adresse**.
   > 
   > Du kan også vælge at medtage **Simuleringswebadresser for at sikre** , at URL-adresser i simuleringsmeddelelser ikke blokeres.
   > Du kan angive op til 10 poster for hvert felt.
   > Der skal være et match på mindst ét domæne **og** én **afsendelses-IP**, men der bevares ingen tilknytning mellem værdier.

4. Når du er færdig, skal du gøre et af følgende:
   - **Første gang**: Klik **på Tilføj**, og klik derefter på **Luk**.
   - **Rediger eksisterende**: Klik på **Gem,** og klik derefter på **Luk**.

De phishing-simuleringsposter, som du har konfigureret fra tredjepart, vises på fanen **Phishing-simulering** . Hvis du vil foretage ændringer, skal du klikke ![på ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger** under fanen.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Yderligere scenarier, der kræver bypass af filtrering

Ud over de to scenarier, som den avancerede leveringspolitik kan hjælpe dig med, er der andre scenarier, der kan kræve, at du tilsidesætter filtrering:

- Tredjepartsfiltre: Hvis  domænets **MX-post** ikke peger på Office 365 (meddelelser sendes et andet sted hen [først), er](secure-by-default.md) sikker som standard *ikke tilgængelig*. Hvis du gerne vil tilføje beskyttelse, skal du aktivere Udvidet filtrering for forbindelser (også kaldet spring *over*). Få mere at vide under [Administrer mailflow ved hjælp af en tredjeparts skytjeneste med Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). Hvis du ikke vil have udvidet filtrering for forbindelser, skal du bruge regler for mailflow (også kaldet transportregler) til at tilsidesætte Microsoft-filtrering for meddelelser, der allerede er blevet evalueret af tredjepartsfiltrering. Få mere at vide under [Brug regler for mailflow til at indstille SCL i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **Falske positive under** gennemgang: Det kan være en god idé midlertidigt at tillade, at visse meddelelser, der stadig analyseres af Microsoft, via administratorindsendelser, rapporterer kendte gode meddelelser, der fejlagtigt [markeres](admin-submission.md) som dårlige for Microsoft (falske positive). Som med alle tilsidesættelser anbefaler **_vi kraftigt_** , at disse lommepenge er midlertidige.

## <a name="security--compliance-center-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Security & Compliance Center PowerShell-procedurer for SecOps-postkasser i den avancerede leveringspolitik

I Security & Compliance Center PowerShell er de grundlæggende elementer i SecOps-postkasser i politikken for avanceret levering:

- **Politikken SecOps tilsidesætter**: Styret af **\*cmdlet'erne -SecOpsOverridePolicy** .
- **Reglen SecOps tilsidesætter**: Styres af **\*cmdlet'erne -SecOpsOverrideRule** .

Denne funktionsmåde har følgende resultater:

- Du opretter først politikken, og derefter opretter du den regel, der identificerer den politik, som reglen gælder for.
- Når du fjerner en politik fra PowerShell, fjernes den tilsvarende regel også.
- Når du fjerner en regel fra PowerShell, fjernes den tilsvarende politik ikke. Du skal fjerne den tilsvarende politik manuelt.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>Brug PowerShell til at konfigurere SecOps-postkasser

Konfiguration af en SecOps-postkasse i den avancerede leveringspolitik i PowerShell er en proces i to trin:

1. Opret politikken Tilsidesæt SecOps.
2. Opret SecOps-tilsidesættelsesreglen, der angiver den politik, som reglen gælder for.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>Trin 1: Brug PowerShell til at oprette politikken til tilsidesættelse af SecOps

Hvis du vil oprette politikken Tilsidesæt SecOps, skal du bruge følgende syntaks:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Uanset hvilken værdi du angiver, er politiknavnet _SecOpsOverridePolicy_, så du kan lige så godt bruge denne værdi.

I dette eksempel oprettes postkassepolitikken SecOps.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>Trin 2: Brug PowerShell til at oprette reglen Om tilsidesættelse af SecOps

I dette eksempel oprettes postkassereglen SecOps med de angivne indstillinger.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Uanset hvilken værdi du angiver, er regelnavnet _SecOpsOverrideRule_\<GUID\>\<GUID\>, hvor er en entydig GUID-værdi (f.eks. 6fed4b63-3563-495d-a481-b24a311f8329).

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>Brug PowerShell til at få vist politikken til tilsidesættelse af SecOps

I dette eksempel returneres detaljerede oplysninger om den ene og kun SecOps-postkassepolitik.

```powershell
Get-SecOpsOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>Brug PowerShell til at få vist SecOps-tilsidesættelsesregler

I dette eksempel returneres detaljerede oplysninger om, at SecOps tilsidesætter regler.

```powershell
Get-SecOpsOverrideRule
```

Selvom den forrige kommando kun bør returnere én regel, medtages alle regler, der afventer sletning, muligvis også i resultaterne.

I dette eksempel identificeres den gyldige regel (én) og alle ugyldige regler.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Når du har identificeret de ugyldige regler, kan du fjerne dem ved hjælp af **cmdlet'en Remove-SecOpsOverrideRule** som [beskrevet senere i denne artikel](#use-powershell-to-remove-secops-override-rules).

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>Brug PowerShell til at ændre politikken til tilsidesættelse af SecOps

Hvis du vil ændre politikken Tilsidesæt SecOps, skal du bruge følgende syntaks:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

I dette eksempel føjes `secops2@contoso.com` politikken Tilsidesæt SecOps til politikken.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> Hvis der findes en tilknyttet, gyldig SecOps-tilsidesættelsesregel, opdateres mailadresserne i reglen også.

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>Brug PowerShell til at ændre en SecOps-tilsidesættelsesregel

**Cmdlet'en Set-SecOpsOverrideRule** ændrer ikke mailadresserne i reglen SecOps override. Hvis du vil ændre mailadresserne i reglen SecOps override, skal du bruge **Set-SecOpsOverridePolicy-cmdlet'en** .

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>Brug PowerShell til at fjerne politikken til tilsidesættelse af SecOps

I dette eksempel fjernes politikken for postkassen SecOps og den tilsvarende regel.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>Brug PowerShell til at fjerne SecOps-tilsidesættelsesregler

Hvis du vil fjerne en SecOps-tilsidesættelsesregel, skal du bruge følgende syntaks:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

I dette eksempel fjernes reglen SecOps, der tilsidesætter.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-center-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Security & Compliance Center PowerShell-procedurer for phishing-simulering fra tredjeparter i politikken for avanceret levering

I Security & Compliance Center PowerShell er de grundlæggende elementer i phishing-simuleringer fra tredjeparter i politikken for avanceret levering:

- **Politikken til tilsidesættelse af phishing-simulering**: Kontrolleres **\*af PhishSimOverridePolicy-cmdletterne** .
- **Reglen til tilsidesættelse af phishing-simulering**: Styres af **\*cmdlet'erne -PhishSimOverrideRule** .
- **URL-adresserne for tilladt (ikke-blokeret) phishing-simulering**: **\*Styret af cmdlet'erne -TenantAllowBlockListItems** .

Denne funktionsmåde har følgende resultater:

- Du opretter først politikken, og derefter opretter du den regel, der identificerer den politik, som reglen gælder for.
- Du redigerer indstillingerne i politikken og reglen separat.
- Når du fjerner en politik fra PowerShell, fjernes den tilsvarende regel også.
- Når du fjerner en regel fra PowerShell, fjernes den tilsvarende politik ikke. Du skal fjerne den tilsvarende politik manuelt.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Brug PowerShell til at konfigurere phishing-simulering fra tredjeparter

Konfiguration af en phishing-simulering fra tredjepart i PowerShell er en proces, der tager flere trin:

1. Opret politikken til tilsidesættelse af phishing-simulering.
2. Opret reglen til tilsidesættelse af phishing-simulering, der angiver:
   - Den politik, som reglen gælder for.
   - IP-kildeadressen til phishing-simuleringsmeddelelser.
3. Du kan også identificere de URL-adresser til phishing-simulering, der skal være tilladt (det vil sige, ikke blokeret eller scannet).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>Trin 1: Brug PowerShell til at oprette politikken til tilsidesættelse af phishing-simulering

I dette eksempel oprettes politikken til tilsidesættelse af phishing-simulering.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Bemærk**! Uanset værdien Navn, du angiver, vil navnet på politikken være _PhishSimOverridePolicy_, så du kan lige så godt bruge denne værdi.

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>Trin 2: Brug PowerShell til at oprette reglen om tilsidesættelse af phishing-simulering

Brug følgende syntaks:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Uanset hvilken værdi du angiver, er regelnavnet _PhishSimOverrideRule_\<GUID\>\<GUID\>, hvor er en entydig GUID-værdi (f.eks. a0eae53e-d755-4a42-9320-b9c6b55c5011).

En gyldig IP-adressepost er en af følgende værdier:

- Enkelt IP: F.eks. 192.168.1.1.
- IP-område: Eksempel: 192.168.0.1-192.168.0.254.
- CIDR IP: F.eks. 192.168.0.1/25.

I dette eksempel oprettes reglen til tilsidesættelse af phishing-simulering med de angivne indstillinger.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>Trin 3: (Valgfrit) Brug PowerShell til at identificere PHISHING-simulerings-URL-adresser for at tillade

Brug følgende syntaks:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

Hvis du vil have mere at vide om URL-syntaksen, [skal du se URL-syntaksen for lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

I dette eksempel tilføjes en URL-adresse, der tillader indtastning for den angivne URL-adresse til phishing-phishing fra tredjepart uden udløb.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Brug PowerShell til at få vist politikken til tilsidesættelse af phishing-simulering

I dette eksempel returneres detaljerede oplysninger om politikken for tilsidesættelse af phishing og kun phishing-simulering.

```powershell
Get-PhishSimOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Brug PowerShell til at få vist regler for tilsidesættelse af phishingseulering

I dette eksempel returneres detaljerede oplysninger om regler for tilsidesættelse af phishing-simulering.

```powershell
Get-PhishSimOverrideRule
```

Selvom den forrige kommando kun bør returnere én regel, medtages alle regler, der afventer sletning, muligvis også i resultaterne.

I dette eksempel identificeres den gyldige regel (én) og alle ugyldige regler.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Når du har identificeret de ugyldige regler, kan du fjerne dem ved hjælp af **cmdlet'en Remove-PhishSimOverrideRule** som [beskrevet senere i denne artikel](#use-powershell-to-remove-phishing-simulation-override-rules).

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>Brug PowerShell til at få vist de tilladte URL-poster for phishing-simulering

Hvis du vil have vist URL-adresserne til tilladt phishing-simulering, skal du køre følgende kommando:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Brug PowerShell til at ændre politikken for tilsidesættelse af phishing-simulering

Hvis du vil ændre politikken til tilsidesættelse af phishing-simulering, skal du bruge følgende syntaks:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

I dette eksempel deaktiveres politikken til tilsidesættelse af phishing-simulering.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Brug PowerShell til at ændre regler for tilsidesættelse af phishingseulering

Hvis du vil ændre reglen til tilsidesættelse af phishing-simulering, skal du bruge følgende syntaks:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

I dette eksempel ændres reglen for tilsidesættelse af den angivne phishing-simulering med følgende indstillinger:

- Tilføj domæneposten blueyonderairlines.com.
- Fjern IP-adresseposten 192.168.1.55.

Bemærk, at disse ændringer ikke påvirker de eksisterende poster.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>Brug PowerShell til at ændre de tilladte URL-poster for phishing-simulering

Du kan ikke ændre URL-værdierne direkte. Du kan [fjerne eksisterende URL-poster og](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) [tilføje nye URL-poster som](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) beskrevet i denne artikel.

Hvis du vil ændre andre egenskaber for en tilladt url-adresse til phishing-simulering (f.eks. udløbsdato eller kommentarer), skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Du identificerer posten, der skal ændres ud fra dens URL-værdier _(parameteren_ Poster) eller identitetsværdien fra outputtet fra cmdlet'en **Get-TenantAllowBlockListItems** ( _id-parameteren_ ).

I dette eksempel er udløbsdatoen for den angivne post blevet ændret.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery –Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Brug PowerShell til at fjerne en politik for tilsidesættelse af phishing-simulering

I dette eksempel fjernes politikken for tilsidesættelse af phishing-simulering og den tilsvarende regel.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Brug PowerShell til at fjerne regler for tilsidesættelse af phishingseulering

Hvis du vil fjerne en regel for tilsidesættelse af phishing-simulering, skal du bruge følgende syntaks:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

I dette eksempel fjernes reglen for tilsidesættelse af den angivne phishing-simulering.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>Brug PowerShell til at fjerne de tilladte URL-poster for phishing-simulering

Hvis du vil fjerne en eksisterende URL-adresse til phishing-simulering, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Du identificerer posten, der skal ændres ud fra dens URL-værdier _(parameteren_ Poster) eller identitetsværdien fra outputtet fra cmdlet'en **Get-TenantAllowBlockListItems** ( _id-parameteren_ ).

I dette eksempel er udløbsdatoen for den angivne post blevet ændret.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery –Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
