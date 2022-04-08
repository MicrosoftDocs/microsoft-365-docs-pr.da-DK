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
description: Administratorer kan få mere at vide om, hvordan de bruger den avancerede leveringspolitik i Exchange Online Protection (EOP) til at identificere meddelelser, der ikke skal filtreres i bestemte understøttede scenarier (phishing-simuleringer fra tredjepart og meddelelser, der leveres til sikkerhedshandlinger (SecOps)-postkasser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6ca3b62bba9a22d8c7c9f3f37dc191d1f458b523
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713905"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Konfigurer levering af phishing-simuleringer fra tredjepart til brugere og ufiltrerede meddelelser til SecOps-postkasser

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

For at holde din organisation [sikker som standard](secure-by-default.md) tillader Exchange Online Protection (EOP) ikke sikre lister eller filtreringssikkerhed for meddelelser, der er identificeret som malware eller phishing med høj sikkerhed. Men der er specifikke scenarier, der kræver levering af ufiltrerede meddelelser. Eksempel:

- **Phishingsimuleringer fra tredjepart**: Simulerede angreb kan hjælpe dig med at identificere sårbare brugere, før et reelt angreb påvirker din organisation.
- **Sikkerhedshandlinger (SecOps)-postkasser**: Dedikerede postkasser, der bruges af sikkerhedsteams til at indsamle og analysere ufiltrerede meddelelser (både gode og dårlige).

Du kan bruge den _avancerede leveringspolitik_ i Microsoft 365 til at forhindre filtrering af indgående meddelelser _i disse specifikke scenarier_.<sup>\*</sup> Den avancerede leveringspolitik sikrer, at meddelelser i disse scenarier opnår følgende resultater:

- Filtre i EOP og Microsoft Defender for Office 365 ikke udføre nogen handling på disse meddelelser.<sup>\*</sup>
- [Zap(nul-tøm)](zero-hour-auto-purge.md) for spam og phishing foretager ingen handling på disse meddelelser.<sup>\*\*</sup>
- [Standardsystembeskeder](/microsoft-365/compliance/alert-policies#default-alert-policies) udløses ikke for disse scenarier.
- [AIR og klyngedannelse i Defender for Office 365](office-365-air.md) ignorerer disse meddelelser.
- Specifikt til phishing-simuleringer fra tredjepart:
  - [Administratorindsendelser](admin-submission.md) genererer et automatisk svar, der siger, at meddelelsen er en del af en phishing-simuleringskampagne og ikke er en reel trussel. Beskeder og AIR udløses ikke. Oplevelsen med administratorindsendelser viser disse meddelelser som en simuleret trussel.
  - Når en bruger rapporterer en phishingsimuleringsmeddelelse ved hjælp af [rapportmeddelelsen eller tilføjelsesprogrammer til rapport phishing](enable-the-report-message-add-in.md), genererer systemet ikke en besked, undersøgelse eller hændelse. Links eller filer detoneres ikke, men meddelelsen vises også under fanen **Brugerrapporterede meddelelser** på siden **Indsendelser** .
  - [Pengeskab Links i Defender for Office 365](safe-links.md) blokerer eller detonerer ikke de specifikt identificerede URL-adresser i disse meddelelser, når der klikkes. URL-adresser er stadig ombrudt, men de er ikke blokeret.
  - [Pengeskab vedhæftede filer i Defender for Office 365](safe-attachments.md) detonerer ikke vedhæftede filer i disse meddelelser.

<sup>\*</sup> Du kan ikke omgå filtrering af malware.

<sup>\*\*</sup> Du kan omgå ZAP for malware ved at oprette en politik for antimalware for SecOps-postkassen, hvor ZAP til malware er slået fra. Du kan finde en vejledning [under Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md).

Meddelelser, der identificeres af den avancerede leveringspolitik, er ikke sikkerhedstrusler, så meddelelserne er markeret med systemtilsidesættelser. Administratoroplevelser viser disse meddelelser som enten på grund af tilsidesættelse af et **phishingsimuleringssystem** eller tilsidesættelse af **et SecOps-postkassesystem** . Administratorer kan filtrere og analysere på disse systemtilsidesættelser i følgende oplevelser:

- [Trusselsoversigt/registreringer i realtid i Defender for Office 365 plan 2](threat-explorer.md): Administratoren kan filtrere **efter systemets tilsidesættelseskilde** og vælge enten **phishingsimulering** eller **SecOps-postkasse**.
- [Mailobjektsiden i Threat Explorer/Realtidsregistreringer](mdo-email-entity-page.md): Administratoren kan få vist en meddelelse, der blev tilladt af organisationspolitikken af enten **SecOps-postkassen** eller **phishingsimulering** under **tilsidesættelse af lejer** i afsnittet **Tilsidesættelser**.
- [Statusrapporten trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report): Administratoren kan filtrere efter **visningsdata efter systemtilsidesættelse** i rullemenuen og vælge at få vist meddelelser, der er tilladt på grund af tilsidesættelse af et phishingsimuleringssystem. Hvis du vil se meddelelser, der er tilladt af tilsidesættelsen af SecOps-postkassen, kan du vælge **diagramopdeling efter leveringsplacering** i rullemenuen **med diagramopdeling efter årsag** .
- [Avanceret jagt i Microsoft Defender for Endpoint](../defender-endpoint/advanced-hunting-overview.md): Phishingsimulering og tilsidesættelser af SecOps-postkassesystemet vises som indstillinger i OrgLevelPolicy i EmailEvents.
- [Kampagnevisninger](campaigns.md): Administratoren kan filtrere **efter systemets tilsidesættelseskilde** og vælge enten **phishingsimulering** eller **SecOps-postkasse**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Hvis du vil gå direkte til siden **Avanceret levering** , skal du åbne <https://security.microsoft.com/advanceddelivery>.

- Hvis du vil oprette forbindelse til Security & Compliance Center PowerShell, [skal du se Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

- Du skal have tildelt tilladelser, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere eller fjerne konfigurerede indstillinger i politikken for avanceret levering, skal du være medlem af rollegruppen **Sikkerhedsadministrator** i **Microsoft 365 Defender portalen** og medlem af rollegruppen **Organisationsadministration** i **Exchange Online**.
  - Hvis du vil have skrivebeskyttet adgang til den avancerede leveringspolitik, skal du være medlem af rollegrupperne **Global læser** eller **Sikkerhedslæser** .

  Du kan få flere oplysninger [under Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md) og [Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > Tilføjelse af brugere til den tilsvarende Azure Active Directory rolle giver brugerne de nødvendige tilladelser på Microsoft 365 Defender-portalen _og_ tilladelser til andre funktioner i Microsoft 365. Du kan få flere oplysninger under [Om administratorroller](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Brug Microsoft 365 Defender-portalen til at konfigurere SecOps-postkasser i den avancerede leveringspolitik

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Avanceret levering** i afsnittet **Regler**. Hvis du vil gå direkte til siden **Avanceret levering** , skal du bruge <https://security.microsoft.com/advanceddelivery>.

2. På siden **Avanceret levering** skal du kontrollere, at fanen **SecOps-postkasse** er valgt, og derefter gøre et af følgende:
   - Klik på ![ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.
   - Hvis der ikke er konfigureret phishing-simuleringer, skal du klikke på **Tilføj**.

3. I pop op-vinduet **Rediger SecOps-postkasser**, der åbnes, skal du angive en eksisterende Exchange Online postkasse, som du vil angive som SecOps-postkasse, ved at gøre et af følgende:
   - Klik på feltet, lad listen over postkasser blive løst, og vælg derefter postkassen.
   - Klik i feltet, og begynd at skrive et id for postkassen (navn, vist navn, alias, mailadresse, kontonavn osv.), og vælg postkassen (vist navn) i resultaterne.

     Gentag dette trin så mange gange, det er nødvendigt. Distributionsgrupper er ikke tilladt.

     Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

4. Klik på **Gem**, når du er færdig.

Posterne i SecOps-postkassen, som du har konfigureret, vises på fanen **SecOps-postkasse** . Klik på ![Ikonet Rediger for at foretage ændringer.](../../media/m365-cc-sc-edit-icon.png) **Rediger** under fanen .

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Brug Microsoft 365 Defender-portalen til at konfigurere phishing-simuleringer fra tredjepart i den avancerede leveringspolitik

1. I Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & Samarbejdspolitikker** \> **& Regler** \> **Trusselspolitikker** \> **Avanceret levering** i afsnittet **Regler**. Hvis du vil gå direkte til siden **Avanceret levering** , skal du bruge <https://security.microsoft.com/advanceddelivery>.

2. På siden **Avanceret levering** skal du vælge fanen **Phishing-simulering** og derefter gøre et af følgende trin:
   - Klik på ![ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**.
   - Hvis der ikke er konfigureret phishing-simuleringer, skal du klikke på **Tilføj**.

3. Konfigurer følgende indstillinger i pop **op-vinduet Rediger phishingsimulering fra tredjepart** , der åbnes:

   - **Domæne**: Udvid denne indstilling, og angiv mindst ét mailadressedomæne (f.eks. contoso.com) ved at klikke i feltet, angive en værdi og derefter trykke på Enter eller vælge den værdi, der vises under feltet. Gentag dette trin så mange gange, det er nødvendigt. Du kan tilføje op til 20 poster.

     > [!NOTE]
     > Brug domænet fra adressen `5321.MailFrom` (også kendt som **MAIL FROM-adresse** , P1-afsender eller konvolutafsender), der bruges i SMTP-overførslen af meddelelsen **, eller** et DomæneNøgler-identificeret mail (DKIM) som angivet af din leverandør af phishingsimulering. 

   - **Sender IP**: Udvid denne indstilling, og angiv mindst én gyldig IPv4-adresse ved at klikke i feltet, angive en værdi og derefter trykke på Enter eller vælge den værdi, der vises under feltet. Gentag dette trin så mange gange, det er nødvendigt. Du kan tilføje op til 10 poster. Gyldige værdier er:
     - Enkelt IP: f.eks. 192.168.1.1.
     - IP-interval: f.eks. 192.168.0.1-192.168.0.254.
     - CIDR IP: For eksempel 192.168.0.1/25.
   - **Url-adresser til simulering, der skal tillades**: Udvid denne indstilling, og angiv eventuelt bestemte URL-adresser, der er en del af din phishing-simuleringskampagne, som ikke skal blokeres eller detoneres, ved at klikke i feltet, angive en værdi og derefter trykke på Enter eller vælge den værdi, der vises under feltet. Du kan tilføje op til 10 poster. Du kan se syntaksformatet for [URL-adressen i URL-syntaksen for listen over tilladte/blokerede lejere](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Disse URL-adresser ombrydes, når der klikkes, men de blokeres ikke.

   Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Fjern ikon.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   > [!NOTE]
   > Hvis du vil konfigurere en phishingsimulering fra tredjepart i Avanceret levering, skal du angive følgende oplysninger:
   > 
   > - Mindst ét **domæne** fra en af følgende kilder:
   >   - Adressen `5321.MailFrom` (også kendt som MAIL FROM-adresse, P1-afsender eller konvolut afsender).
   >   - DKIM-domænet.
   > - Mindst én **afsendelses-IP**.
   > 
   > Du kan eventuelt inkludere **URL-adresser til simulering for at** sikre, at URL-adresser i simuleringsmeddelelser ikke blokeres.
   > Du kan angive op til 10 poster for hvert felt.
   > Der skal være et match på mindst ét **domæne** og ét **afsendelses-IP**, men ingen tilknytning mellem værdier vedligeholdes.

4. Når du er færdig, skal du gøre et af følgende:
   - **Første gang**: Klik på **Tilføj**, og klik derefter på **Luk**.
   - **Rediger eksisterende**: Klik på **Gem** , og klik derefter på **Luk**.

De phishing-simuleringsposter fra tredjepart, som du har konfigureret, vises på fanen **Phishing-simulering** . Klik på ![Ikonet Rediger for at foretage ændringer.](../../media/m365-cc-sc-edit-icon.png) **Rediger** under fanen .

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Yderligere scenarier, der kræver tilsidesættelse af filtrering

Ud over de to scenarier, som den avancerede leveringspolitik kan hjælpe dig med, er der andre scenarier, der kan kræve, at du tilsidesætter filtrering:

- **Tredjepartsfiltre**: Hvis dit domænes MX-post *ikke* peger på Office 365 (meddelelser distribueres først et andet sted), er [sikker som standard](secure-by-default.md) *ikke tilgængelig*. Hvis du vil tilføje beskyttelse, skal du aktivere Udvidet filtrering for forbindelser (også kendt som *oversigt over spring over*). Du kan få flere oplysninger under [Administrer mailflow ved hjælp af en cloudtjeneste fra tredjepart med Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). Hvis du ikke vil have udvidet filtrering for forbindelser, skal du bruge regler for mailflow (også kaldet transportregler) til at omgå Microsoft-filtrering for meddelelser, der allerede er blevet evalueret af filtrering fra tredjepart. Du kan få flere oplysninger under [Brug regler for mailflow til at angive SCL'en i meddelelser](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **Falske positiver, der gennemses**: Det kan være en god idé midlertidigt at tillade, at visse meddelelser, der stadig analyseres af Microsoft, via [administratorindsendelser, rapporterer](admin-submission.md) kendte fungerende meddelelser, der fejlagtigt markeres som dårlige for Microsoft (falske positiver). Som med alle tilsidesættelser anbefaler vi **_på det kraftigste_** , at disse godtgørelser er midlertidige.

## <a name="security--compliance-center-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Security & Compliance Center PowerShell-procedurer for SecOps-postkasser i den avancerede leveringspolitik

I Security & Compliance Center i PowerShell er de grundlæggende elementer i SecOps-postkasser i den avancerede leveringspolitik:

- **SecOps-tilsidesættelsespolitikken**: Styres af **\*-SecOpsOverridePolicy-cmdlet'erne** .
- **SecOps-tilsidesættelsesreglen**: Styres af **\*-SecOpsOverrideRule-cmdlet'erne** .

Denne funktionsmåde har følgende resultater:

- Du opretter politikken først, og derefter opretter du den regel, der identificerer den politik, som reglen gælder for.
- Når du fjerner en politik fra PowerShell, fjernes den tilsvarende regel også.
- Når du fjerner en regel fra PowerShell, fjernes den tilsvarende politik ikke. Du skal fjerne den tilsvarende politik manuelt.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>Brug PowerShell til at konfigurere SecOps-postkasser

Konfiguration af en SecOps-postkasse i den avancerede leveringspolitik i PowerShell er en proces med to trin:

1. Opret politikken til tilsidesættelse af SecOps.
2. Opret den tilsidesættelsesregel for SecOps, der angiver den politik, som reglen gælder for.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>Trin 1: Brug PowerShell til at oprette tilsidesættelsespolitikken for SecOps

Hvis du vil oprette tilsidesættelsespolitikken for SecOps, skal du bruge følgende syntaks:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Uanset hvilken værdi for Navn du angiver, er politiknavnet _SecOpsOverridePolicy_, så du kan lige så godt bruge denne værdi.

I dette eksempel oprettes politikken for SecOps-postkassen.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>Trin 2: Brug PowerShell til at oprette tilsidesættelsesreglen for SecOps

I dette eksempel oprettes reglen for SecOps-postkassen med de angivne indstillinger.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Uanset hvilken værdi for Navn du angiver, er regelnavnet _SecOpsOverrideRule_\<GUID\> , hvor \<GUID\> er en entydig GUID-værdi (f.eks. 6fed4b63-3563-495d-a481-b24a311f8329).

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>Brug PowerShell til at få vist politikken for tilsidesættelse af SecOps

I dette eksempel returneres detaljerede oplysninger om den ene og den eneste SecOps-postkassepolitik.

```powershell
Get-SecOpsOverridePolicy
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>Brug PowerShell til at få vist regler for tilsidesættelse af SecOps

I dette eksempel returneres detaljerede oplysninger om tilsidesættelsesregler for SecOps.

```powershell
Get-SecOpsOverrideRule
```

Selvom den forrige kommando kun skal returnere én regel, medtages eventuelle regler, der afventer sletning, muligvis også i resultaterne.

I dette eksempel identificeres den gyldige regel (en) og eventuelle ugyldige regler.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Når du har identificeret de ugyldige regler, kan du fjerne dem ved hjælp af cmdlet'en **Remove-SecOpsOverrideRule** , som beskrevet [senere i denne artikel](#use-powershell-to-remove-secops-override-rules).

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>Brug PowerShell til at ændre politikken for tilsidesættelse af SecOps

Hvis du vil ændre politikken for tilsidesættelse af SecOps, skal du bruge følgende syntaks:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

Dette eksempel føjer `secops2@contoso.com` til politikken for tilsidesættelse af SecOps.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> Hvis der findes en tilknyttet, gyldig tilsidesættelsesregel for SecOps, opdateres mailadresserne i reglen også.

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>Brug PowerShell til at ændre en tilsidesættelsesregel for SecOps

**Set-SecOpsOverrideRule-cmdlet'en** ændrer ikke mailadresserne i secOps-tilsidesættelsesreglen. Hvis du vil ændre mailadresserne i tilsidesættelsesreglen for SecOps, skal du bruge cmdlet'en **Set-SecOpsOverridePolicy** .

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>Brug PowerShell til at fjerne politikken for tilsidesættelse af SecOps

I dette eksempel fjernes secOps-postkassepolitikken og den tilsvarende regel.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>Brug PowerShell til at fjerne regler for tilsidesættelse af SecOps

Hvis du vil fjerne en SecOps-tilsidesættelsesregel, skal du bruge følgende syntaks:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

I dette eksempel fjernes den angivne tilsidesættelsesregel for SecOps.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-center-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Security & Compliance Center PowerShell-procedurer for phishing-simuleringer fra tredjepart i den avancerede leveringspolitik

I Security & Compliance Center i PowerShell er de grundlæggende elementer i phishing-simuleringer fra tredjepart i den avancerede leveringspolitik:

- **Politikken for tilsidesættelse af phishing-simulering**: Styres af **\*-PhishSimOverridePolicy-cmdlet'erne** .
- **Reglen for phishingsimulering tilsidesætter reglen**: Styres af **\*-PhishSimOverrideRule-cmdlet'erne** .
- **De tilladte (ikke-blokerede) url-adresser til phishing-simulering**: Styres af cmdlet'erne **\*-TenantAllowBlockListItems** .

Denne funktionsmåde har følgende resultater:

- Du opretter politikken først, og derefter opretter du den regel, der identificerer den politik, som reglen gælder for.
- Du kan ændre indstillingerne i politikken og reglen separat.
- Når du fjerner en politik fra PowerShell, fjernes den tilsvarende regel også.
- Når du fjerner en regel fra PowerShell, fjernes den tilsvarende politik ikke. Du skal fjerne den tilsvarende politik manuelt.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Brug PowerShell til at konfigurere phishing-simuleringer fra tredjepart

Konfiguration af en phishing-simulering fra tredjepart i PowerShell er en proces med flere trin:

1. Opret politikken for tilsidesættelse af phishingsimulering.
2. Opret den tilsidesættelsesregel for phishingsimulering, der angiver:
   - Den politik, som reglen gælder for.
   - IP-kildeadressen for phishingsimuleringsmeddelelserne.
3. Du kan eventuelt identificere de URL-adresser til phishing-simulering, der skal tillades (dvs. ikke blokeret eller scannet).

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>Trin 1: Brug PowerShell til at oprette politikken for tilsidesættelse af phishing-simulering

I dette eksempel oprettes politikken for tilsidesættelse af phishingsimulering.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Bemærk**! Uanset hvilken værdi for Navn du angiver, er politiknavnet _PhishSimOverridePolicy_, så du kan lige så godt bruge denne værdi.

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>Trin 2: Brug PowerShell til at oprette tilsidesættelsesreglen for phishingsimulering

Brug følgende syntaks:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Uanset hvilken værdi for Navn du angiver, er regelnavnet _PhishSimOverrideRule_\<GUID\> , hvor \<GUID\> er en entydig GUID-værdi (f.eks. a0eae53e-d755-4a42-9320-b9c6b55c5011).

En gyldig IP-adressepost er en af følgende værdier:

- Enkelt IP: f.eks. 192.168.1.1.
- IP-interval: f.eks. 192.168.0.1-192.168.0.254.
- CIDR IP: For eksempel 192.168.0.1/25.

I dette eksempel oprettes reglen for tilsidesættelse af phishing-simulering med de angivne indstillinger.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>Trin 3: (Valgfrit) Brug PowerShell til at identificere URL-adresser til phishing-simulering, der skal tillades

Brug følgende syntaks:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

Du kan finde flere oplysninger om URL-syntaksen i [URL-syntaksen for listen over tilladte/blokerede lejere](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

I dette eksempel tilføjes en URL-adresse, der tillader angivelse af den angivne URL-adresse til phishing-simulering fra tredjepart uden udløb.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Brug PowerShell til at få vist politikken for tilsidesættelse af phishingsimulering

I dette eksempel returneres detaljerede oplysninger om den ene politik for tilsidesættelse af phishingsimulering.

```powershell
Get-PhishSimOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Brug PowerShell til at få vist tilsidesættelsesregler for phishingsimulering

I dette eksempel returneres detaljerede oplysninger om tilsidesættelsesregler for phishingsimulering.

```powershell
Get-PhishSimOverrideRule
```

Selvom den forrige kommando kun skal returnere én regel, medtages eventuelle regler, der afventer sletning, muligvis også i resultaterne.

I dette eksempel identificeres den gyldige regel (en) og eventuelle ugyldige regler.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Når du har identificeret de ugyldige regler, kan du fjerne dem ved hjælp af cmdlet'en **Remove-PhishSimOverrideRule** , som beskrevet [senere i denne artikel](#use-powershell-to-remove-phishing-simulation-override-rules).

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>Brug PowerShell til at få vist de tilladte URL-adresser til phishing-simulering

Kør følgende kommando for at få vist de tilladte URL-adresser til phishing-simulering:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Brug PowerShell til at ændre politikken for tilsidesættelse af phishingsimulering

Hvis du vil ændre politikken for tilsidesættelse af phishingsimulering, skal du bruge følgende syntaks:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

I dette eksempel deaktiveres politikken for tilsidesættelse af phishingsimulering.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Brug PowerShell til at ændre tilsidesættelsesregler for phishingsimulering

Hvis du vil ændre tilsidesættelsesreglen for phishingsimulering, skal du bruge følgende syntaks:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

I dette eksempel ændres den angivne tilsidesættelsesregel for phishing-simulering med følgende indstillinger:

- Tilføj domæneposten blueyonderairlines.com.
- Fjern IP-adresseposten 192.168.1.55.

Bemærk, at disse ændringer ikke påvirker eksisterende poster.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>Brug PowerShell til at ændre de tilladte URL-adresser til phishing-simulering

Du kan ikke ændre URL-værdierne direkte. Du kan [fjerne eksisterende URL-adresser](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) og [tilføje nye URL-adresser](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) som beskrevet i denne artikel.

Hvis du vil ændre andre egenskaber for en tilladt URL-adresse til phishing-simulering (f.eks. udløbsdatoen eller kommentarer), skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Du identificerer den post, der skal ændres ved hjælp af dens URL-værdier (parameteren _Entries_ ) eller identitetsværdien fra outputtet af cmdlet'en **Get-TenantAllowBlockListItems** (parameteren _Ids_ ).

I dette eksempel blev udløbsdatoen for den angivne post ændret.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Brug PowerShell til at fjerne en tilsidesættelsespolitik for phishingsimulering

I dette eksempel fjernes politikken for tilsidesættelse af phishingsimulering og den tilsvarende regel.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Brug PowerShell til at fjerne tilsidesættelsesregler for phishingsimulering

Hvis du vil fjerne en tilsidesættelsesregel for phishingsimulering, skal du bruge følgende syntaks:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

I dette eksempel fjernes den angivne tilsidesættelsesregel for phishingsimulering.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>Brug PowerShell til at fjerne de tilladte URL-adresser til phishing-simulering

Hvis du vil fjerne en eksisterende URL-adresse til phishing-simulering, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Du identificerer den post, der skal ændres ved hjælp af dens URL-værdier (parameteren _Entries_ ) eller identitetsværdien fra outputtet af cmdlet'en **Get-TenantAllowBlockListItems** (parameteren _Ids_ ).

I dette eksempel blev udløbsdatoen for den angivne post ændret.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery -Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
