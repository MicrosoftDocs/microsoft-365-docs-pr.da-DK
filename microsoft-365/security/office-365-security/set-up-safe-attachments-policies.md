---
title: Konfigurer Pengeskab politikker for vedhæftede filer i Microsoft Defender Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 078eb946-819a-4e13-8673-fe0c0ad3a775
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan Pengeskab politikker for vedhæftede filer for at beskytte din organisation mod skadelige filer i mails.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cc0f2e3e87c288383880ba5b69f3b6b5d303c40
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63591317"
---
# <a name="set-up-safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Konfigurer Pengeskab politikker for vedhæftede filer i Microsoft Defender Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til virksomhedskunder, der [har Microsoft Defender Office 365](whats-new-in-defender-for-office-365.md). Hvis du er hjemmebruger og leder efter oplysninger om scanning af vedhæftede filer i Outlook, skal du se [Avanceret Outlook.com-sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Pengeskab Vedhæftede filer er en funktion i [Microsoft Defender til Office 365](whats-new-in-defender-for-office-365.md), der bruger et virtuelt miljø til at kontrollere vedhæftede filer i indgående mails, når de er blevet scannet af beskyttelse mod [malware i Exchange Online Protection (EOP),](anti-malware-protection.md) men før levering til modtagerne. Du kan finde flere oplysninger [Pengeskab Vedhæftede filer i Microsoft Defender Office 365](safe-attachments.md).

Selvom der ikke er nogen standardpolitik Pengeskab Vedhæftede filer, giver den **indbyggede** beskyttelse foruddefinerede sikkerhedspolitik Pengeskab Beskyttelse af vedhæftede filer til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab Politikker for vedhæftede filer). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md). Du kan også bruge procedurerne i denne artikel til at oprette Pengeskab politikker for vedhæftede filer, der gælder for bestemte brugere, grupper eller domæner.

Du kan konfigurere Pengeskab Politikker for vedhæftede filer på Microsoft 365 Defender-portalen eller i PowerShell (Exchange Online PowerShell for berettigede Microsoft 365-organisationer med postkasser i Exchange Online; enkeltstående EOP PowerShell til organisationer uden Exchange Online postkasser, men med Defender Office 365-tilføjelsesabonnementer).

De grundlæggende elementer i Pengeskab politik for vedhæftede filer er:

- Politikken for sikre vedhæftede **filer: Angiver** handlingerne for registreringer af ukendt malware, om der skal sendes meddelelser med vedhæftede malwares til en bestemt mailadresse, og om du skal levere meddelelser, hvis Pengeskab Scanning af vedhæftede filer ikke kan fuldføres.
- **Regel for sikre vedhæftede** filer: Angiver prioriteten og modtagerens filtre (hvem politikken gælder for).

Forskellen mellem disse to elementer er ikke indlysende, når du administrerer Pengeskab politikker for vedhæftede filer i Microsoft 365 Defender portal:

- Når du opretter en Pengeskab Politik for vedhæftede filer, opretter du faktisk en regel for sikre vedhæftede filer og den tilknyttede politik for sikre vedhæftede filer på samme tid med samme navn for begge.
- Når du ændrer en Pengeskab politik for vedhæftede filer, ændrer indstillinger, der er relateret til navn, prioritet, aktiveret eller deaktiveret, og modtagerfiltrene ændrer reglen for sikre vedhæftede filer. Alle andre indstillinger ændrer den tilknyttede politik for sikre vedhæftede filer.
- Når du fjerner en Pengeskab politik for vedhæftede filer, fjernes reglen for sikre vedhæftede filer og den tilknyttede politik for sikre vedhæftede filer.

I Exchange Online PowerShell eller enkeltstående EOP PowerShell administrerer du politikken og reglen separat. Du kan finde flere oplysninger i [afsnittet Brug Exchange Online PowerShell eller enkeltstående EOP PowerShell](#use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies) til at konfigurere Pengeskab politikker for vedhæftede filer senere i denne artikel.

> [!NOTE]
> I området globale indstillinger i Pengeskab indstillinger for Vedhæftede filer skal du konfigurere funktioner, der ikke er afhængige Pengeskab politikker for vedhæftede filer. Du kan finde [en vejledning i aktivere Pengeskab Vedhæftede filer for SharePoint, OneDrive, og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) og [Pengeskab Dokumenter i Microsoft 365 E5](safe-docs.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Hvad har du brug for at vide, før du begynder?

- Du åbner Microsoft 365 Defender på <https://security.microsoft.com>. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

- Hvis du vil oprette Exchange Online forbindelse til PowerShell, [skal du Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Hvis du vil oprette forbindelse til enkeltstående EOP PowerShell, [skal du Forbind Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Du skal have tilladelser, før du kan udføre procedurerne i denne artikel:
  - Hvis du vil oprette, redigere og slette Pengeskab Politikker for vedhæftede filer skal du være medlem af rollegrupperne  Organisationsadministration eller  Sikkerhedsadministrator i Microsoft 365 Defender-portalen **og** være medlem af rollegruppen Organisationsadministration i Exchange Online.
  - For skrivebeskyttet adgang til Pengeskab Politikker for vedhæftede filer skal du være medlem af rollegrupperne **Global** læser eller Sikkerhedslæser  Microsoft 365 Defender portalen.

  Du kan finde flere [oplysninger under Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md) [og tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Bemærkninger**:

  - Når du føjer brugere til den tilsvarende Azure Active Directory-rolle i Microsoft 365 Administration, får brugerne de nødvendige tilladelser i _Microsoft 365 Defender-portalen og_ tilladelser til andre funktioner i Microsoft 365. Du kan få mere at vide [under Om administratorroller](../../admin/add-users/about-admin-roles.md).
  - **Rollegruppen Skrivebeskyttet** organisationsadministration i [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) også skrivebeskyttet adgang til funktionen.

- For vores anbefalede indstillinger for Pengeskab Politikker for vedhæftede filer skal du [Pengeskab indstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- Der kan gå op til 30 minutter, før en ny eller opdateret politik anvendes.

## <a name="use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies"></a>Brug portalen Microsoft 365 Defender til at oprette Pengeskab politikker for vedhæftede filer

Når du opretter en brugerdefineret Pengeskab Politik for vedhæftede filer i Microsoft 365 Defender-portalen, oprettes reglen for sikre vedhæftede filer og den tilknyttede politik for sikre vedhæftede filer på samme tid med det samme navn for begge.

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til & politikker  \> for samarbejde **&** **regler** \> \> **for trussel Pengeskab** Vedhæftede filer i **sektionen** Politikker. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. Klik Pengeskab **ikonet Opret** på siden Vedhæftede ![filer.](../../media/m365-cc-sc-create-icon.png) **Opret**.

3. Guiden politik åbnes. På siden **Navngive din** politik skal du konfigurere følgende indstillinger:
   - **Navn**: Angiv et entydigt, beskrivende navn til politikken.
   - **Beskrivelse**: Angiv en valgfri beskrivelse af politikken.

   Klik på Næste, når du er **færdig**.

4. På siden **Brugere og domæner, der** vises, skal du identificere de interne modtagere, som politikken gælder for (modtagerbetingelser):
   - **Brugere**: De angivne postkasser, mailbrugere eller mailkontakter i organisationen.
   - **Grupper**: De angivne distributionsgrupper, mailaktiverede sikkerhedsgrupper eller Microsoft 365 grupper i organisationen.
   - **Domæner:** Alle modtagere på de angivne [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i organisationen.

   Klik i det relevante felt, begynd at skrive en værdi, og vælg den ønskede værdi i resultaterne. Gentag denne proces så mange gange, som det er nødvendigt. Hvis du vil fjerne en eksisterende værdi, skal du klikke på Fjern ![Ikonet Fjern.](../../media/m365-cc-sc-remove-selection-icon.png) ud for værdien.

   For brugere eller grupper kan du bruge de fleste identifikatorer (navn, visningsnavn, alias, mailadresse, kontonavn osv.), men det tilsvarende viste navn vises i resultaterne. For brugere skal du angive en stjerne (\*) alene for at få vist alle tilgængelige værdier.

   Flere værdier i samme betingelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

   - **Udelad disse brugere,** grupper og domæner: Hvis du vil tilføje undtagelser for de interne modtagere, som politikken gælder for (recpient-undtagelser), skal du vælge denne indstilling og konfigurere undtagelserne. Indstillingerne og funktionsmåden er præcis som betingelserne.

   Klik på Næste, når du er **færdig**.

5. På siden **Indstillinger** skal du konfigurere følgende indstillinger:

   - **Pengeskab Ukendt malwaresvar ved vedhæftede** filer: Vælg en af følgende værdier:
     - **Fra**: Typisk anbefaler vi ikke denne værdi.
     - **Skærm**
     - **Bloker**: Dette er standardværdien og den anbefalede værdi i Standard og Faste [forudindstillede sikkerhedspolitikker](preset-security-policies.md).
     - **Erstat**
     - **Dynamisk levering (funktionen Eksempel)**

     Disse værdier er forklaret i Pengeskab [indstillinger for politik for vedhæftede filer](safe-attachments.md#safe-attachments-policy-settings).

   - **Karantænepolitik**: Vælg den karantænepolitik **, der** gælder for meddelelser, der er i karantæne af **Pengeskab Vedhæftede** filer (Bloker, Erstat eller **Dynamisk levering**). Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne, og om brugerne modtager beskeder om karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).

     En tom værdi betyder, at standardkarantænepolitikken bruges (AdminOnlyAccessPolicy til mailregistreringer af Pengeskab vedhæftede filer). Når du senere redigerer Pengeskab vedhæftede filer eller får vist indstillingerne, vises standardnavnet for karantænepolitikken.

   - Omdiriger meddelelser med registrerede vedhæftede **filer: Hvis** du vælger Aktivér **omdirigering, kan** du angive en mailadresse i feltet Send meddelelser, der indeholder blokerede, overvågede eller erstattede vedhæftede filer til den angivne mailadresse for at sende meddelelser, der indeholder vedhæftede malwares **,** til analyse og undersøgelse.

     Det anbefales, at du bruger standardindstillinger og faste politikindstillinger til at aktivere omdirigering. Du kan finde flere oplysninger [under Pengeskab Indstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

   - Anvend registreringssvaret Pengeskab vedhæftede filer, hvis **scanningen ikke kan fuldføres (timeout** eller fejl): Den handling, der er angivet af **Pengeskab Ukendt malwaresvar** ved vedhæftede filer modtages på meddelelser, selvom Pengeskab Scanning af vedhæftede filer ikke kan fuldføres. Hvis du har valgt denne indstilling, skal du altid vælge **Aktivér omdirigering** og angive en mailadresse til at sende meddelelser, der indeholder vedhæftede malwaremeddelelser. Ellers kan meddelelser gå tabt.

   Klik på Næste, når du er **færdig**.

6. Gennemgå dine **indstillinger** på siden Gennemse, der vises. Du kan vælge **Rediger** i hver sektion for at ændre indstillingerne i sektionen. Eller du kan klikke **på** Tilbage eller vælge den bestemte side i guiden.

   Klik på Send, når du er **færdig**.

7. Klik på Udført på bekræftelsessiden, der **vises**.

## <a name="use-the-microsoft-365-defender-portal-to-view-safe-attachments-policies"></a>Brug portalen Microsoft 365 Defender til at få vist Pengeskab politikker for vedhæftede filer

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til & politikker  \> for samarbejde **&** **regler** \> \> **for trussel Pengeskab** Vedhæftede filer i **sektionen** Politikker. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab vedhæftede** filer vises følgende egenskaber på listen over politikker:
   - **Navn**
   - **Status**
   - **Prioritet**

3. Når du vælger en politik ved at klikke på navnet, vises politikindstillingerne i en pop op-meddelelse.

## <a name="use-the-microsoft-365-defender-portal-to-modify-safe-attachments-policies"></a>Brug portalen Microsoft 365 Defender til at ændre Pengeskab politikker for vedhæftede filer

1. IIn the Microsoft 365 Defender portal at <https://security.microsoft.com>, go to **Email & Collaboration Policies** \> **& Rules Threat** \> **policies** \> **Pengeskab Attachments** in **the Policies** section. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab vedhæftede** filer skal du vælge en politik på listen ved at klikke på navnet.

3. I pop op-vindue med politikoplysninger skal du **vælge Rediger** i hver sektion for at ændre indstillingerne i sektionen. Du kan finde flere oplysninger om indstillingerne i afsnittet [Brug Microsoft 365 Defender til at oprette Pengeskab Politikker for vedhæftede filer](#use-the-microsoft-365-defender-portal-to-create-safe-attachments-policies) tidligere i denne artikel.

Hvis du vil aktivere eller deaktivere en politik eller angive prioritetsrækkefølgen for politikker, skal du se følgende afsnit.

### <a name="enable-or-disable-safe-attachments-policies"></a>Aktivere eller deaktivere Pengeskab politikker for vedhæftede filer

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til & politikker  \> for samarbejde **&** **regler** \> \> **for trussel Pengeskab** Vedhæftede filer i **sektionen** Politikker. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab vedhæftede** filer skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist en af følgende værdier:
   - **Politik deaktiveret**: Hvis du vil aktivere politikken, skal du klikke ![på ikonet Slå til.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå til** .
   - **Politik slået til**: Hvis du vil deaktivere politikken, skal du klikke ![på Ikonet Slå fra.](../../media/m365-cc-sc-turn-on-off-icon.png) **Slå fra**.

4. I bekræftelsesdialogboksen, der vises, skal **du klikke på Aktivér** **eller Slå fra**.

5. Klik **på Luk** i pop op-menuen med politikoplysninger.

Tilbage på hovedpolitiksiden vil **politikkens statusværdi** **være Til eller** **Fra**.

### <a name="set-the-priority-of-safe-attachments-policies"></a>Angiv prioriteten for politikkerne Pengeskab vedhæftede filer

Som standard får politikkerne Pengeskab vedhæftede filer en prioritet, der er baseret på den rækkefølge, de blev oprettet i (nyere politikker har lavere prioritet end ældre politikker). Et tal for lavere prioritet angiver en højere prioritet for politikken (0 er den højeste), og politikkerne behandles i prioritetsrækkefølgen (politikker med højere prioritet behandles før politikker med lavere prioritet). Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

Du kan finde flere oplysninger om rangordenen, og hvordan flere politikker evalueres og anvendes, i Rækkefølge [og prioriteret mailbeskyttelse](how-policies-and-protections-are-combined.md).

Pengeskab Politikker for vedhæftede filer vises i den rækkefølge, de behandles (den første politik har **værdien Prioritet** 0).

**Bemærk**! I Microsoft 365 Defender-portalen kan du kun ændre prioriteten af politikken Pengeskab vedhæftede filer, når du har oprettet den. I PowerShell kan du tilsidesætte standardprioriteten, når du opretter reglen om sikre vedhæftede filer (som kan påvirke prioriteten af eksisterende regler).

Hvis du vil ændre prioriteten af en politik, skal du klikke  på Forøg prioritet eller Formindsk prioritet i egenskaberne for politikken (du kan ikke direkte ændre tallet prioritet i Microsoft 365 Defender portal). Det giver kun mening at ændre prioriteten af en politik, hvis du har flere politikker.

1. I  portalen Microsoft 365 Defender skal du gå til **& politikker** \> for samarbejde **& Regler** \> \> Pengeskab Trussel **om** vedhæftede filer i **sektionen** Politikker.

2. På siden **Pengeskab vedhæftede** filer skal du vælge en politik på listen ved at klikke på navnet.

3. Øverst i pop op-vindue med politikoplysninger, der vises, får du vist  Forøg  prioritet eller Formindsk prioritet baseret på den aktuelle prioritetsværdi og antallet af politikker:
   - Politikken med værdien **Prioritet** **0 har** kun indstillingen **Formindsk** prioritet tilgængelig.
   - Politikken med den laveste **prioritetsværdi** (f.eks. **3**) har kun indstillingen **Forøg** prioritet tilgængelig.
   - Hvis du har tre eller flere politikker, har politikkerne mellem de højeste og laveste prioritetsværdier både indstillingerne Forøg **prioritet** **og Formindsk** prioritet.

   Klik på ![ikonet Forøg prioritet.](../../media/m365-cc-sc-increase-icon.png) **Forøg** prioritet ![eller ikonet Formindsk prioritet](../../media/m365-cc-sc-decrease-icon.png) **Formindsk prioritet** for at **ændre værdien** Prioritet.

4. Når du er færdig, skal du **klikke på** Luk i pop op-menuen med politikoplysninger.

## <a name="use-the-microsoft-365-defender-portal-to-remove-safe-attachments-policies"></a>Brug portalen Microsoft 365 Defender til at fjerne Pengeskab politikker for vedhæftede filer

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til & politikker  \> for samarbejde **&** **regler** \> \> **for trussel Pengeskab** Vedhæftede filer i **sektionen** Politikker. For at gå direkte til **Pengeskab vedhæftede filer skal** du bruge <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab Vedhæftede** filer skal du vælge en brugerdefineret politik på listen ved at klikke på navnet på politikken.

3. Øverst i pop op-vindue med politikoplysninger, der vises, skal du klikke på ![ikonet Flere handlinger.](../../media/m365-cc-sc-more-actions-icon.png) **Flere handlinger** \> ![Ikonet Slet politik **Slet**](../../media/m365-cc-sc-delete-icon.png) politik.

4. Klik på Ja i bekræftelsesdialogboksen, der **vises**.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-attachments-policies"></a>Brug Exchange Online PowerShell eller den enkeltstående EOP PowerShell til at konfigurere Pengeskab politikker for vedhæftede filer

Som beskrevet tidligere består en politik Pengeskab Vedhæftede filer af en sikker politik for vedhæftede filer og en regel for sikre vedhæftede filer.

I PowerShell fremgår forskellen mellem politikker for sikre vedhæftede filer og regler for sikre vedhæftede filer. Du administrerer politikker for sikre vedhæftede filer ved hjælp af cmdlet'erne **-SafeAttachmentPolicy, og du administrerer regler for sikre vedhæftede filer ved hjælp af cmdlet'erne -SafeAttachmentRule.\*** **\***

- I PowerShell opretter du først politikken for sikre vedhæftede filer, og derefter opretter du reglen for sikker vedhæftet fil, der identificerer den politik, som reglen gælder for.
- I PowerShell ændrer du indstillingerne i politikken for sikre vedhæftede filer og reglen for sikre vedhæftede filer separat.
- Når du fjerner en politik for sikre vedhæftede filer fra PowerShell, fjernes den tilsvarende regel for sikre vedhæftede filer ikke automatisk og omvendt.

### <a name="use-powershell-to-create-safe-attachments-policies"></a>Brug PowerShell til at oprette Pengeskab politikker for vedhæftede filer

Oprettelse af Pengeskab politik for vedhæftede filer i PowerShell er en proces i to trin:

1. Opret politikken for sikre vedhæftede filer.
2. Opret reglen for sikre vedhæftede filer, der angiver politikken for sikre vedhæftede filer, som reglen gælder for.

 **Bemærkninger**:

- Du kan oprette en ny regel for sikre vedhæftede filer og tildele en eksisterende, ikke-tilknyttet politik for sikre vedhæftede filer til den. En regel for sikre vedhæftede filer kan ikke knyttes til mere end én politik for sikre vedhæftede filer.

- Du kan konfigurere følgende indstillinger for nye politikker for sikre vedhæftede filer i PowerShell, der ikke er tilgængelige i Microsoft 365 Defender-portalen, før du har oprettet politikken:
  - Opret den nye politik som _deaktiveret (_ `$false` Aktiveret på cmdlet'en **New-SafeAttachmentRule** ).
  - Angiv prioriteten af politikken under oprettelsen (_Prioritet_ _\<Number\>_) på den **nye SikreAttachmentRule-cmdlet** ).

- En ny politik for sikre vedhæftede filer, som du opretter i PowerShell, er ikke synlig i Microsoft 365 Defender-portalen, før du tildeler politikken til en regel for sikker vedhæftet fil.

#### <a name="step-1-use-powershell-to-create-a-safe-attachment-policy"></a>Trin 1: Brug PowerShell til at oprette en politik for sikre vedhæftede filer

Hvis du vil oprette en politik for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
New-SafeAttachmentPolicy -Name "<PolicyName>" -Enable $true [-AdminDisplayName "<Comments>"] [-Action <Allow | Block | Replace | DynamicDelivery>] [-Redirect <$true | $false>] [-RedirectAddress <SMTPEmailAddress>] [-ActionOnError <$true | $false>] [-QuarantineTag <QuarantinePolicyName>]
```

I dette eksempel oprettes en politik for sikre vedhæftede filer med navnet Contoso Alle med følgende værdier:

- Bloker meddelelser, der findes at indeholde malware, Pengeskab scanning af dokumenter (vi bruger ikke handlingsparameteren, og standardværdien er ). `Block`
- [Standardkarantænepolitikken](quarantine-policies.md) bruges (AdminOnlyAccessPolicy), fordi vi ikke bruger _parameteren QuarantineTag_.
- Omdirigering er aktiveret, og meddelelser, der findes at indeholde malware, sendes til sec-ops@contoso.com til analyse og undersøgelse.
- Hvis Pengeskab scanning af vedhæftede filer ikke er tilgængelig eller støder på fejl, skal du ikke levere meddelelsen (vi bruger ikke _parameteren ActionOnError_, og standardværdien er `$true`).

```PowerShell
New-SafeAttachmentPolicy -Name "Contoso All" -Enable $true -Redirect $true -RedirectAddress sec-ops@contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-SafeAttachmentPolicy](/powershell/module/exchange/new-safeattachmentpolicy).

> [!NOTE]
> Hvis du vil have en detaljeret [](quarantine-policies.md) vejledning til at angive karantænepolitikken, der skal bruges i en sikker vedhæftet fil-politik, skal du se Brug PowerShell til at angive karantænepolitikken [Pengeskab politikker for vedhæftede filer](quarantine-policies.md#safe-attachments-policies-in-powershell).

#### <a name="step-2-use-powershell-to-create-a-safe-attachment-rule"></a>Trin 2: Brug PowerShell til at oprette en regel for sikre vedhæftede filer

Hvis du vil oprette en regel for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
New-SafeAttachmentRule -Name "<RuleName>" -SafeAttachmentPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"] [-Enabled <$true | $false>]
```

I dette eksempel oprettes en regel for sikre vedhæftede filer med navnet Contoso Alle med følgende betingelser:

- Reglen er knyttet til politikken for sikre vedhæftede filer kaldet Contoso All.
- Reglen gælder for alle modtagere i contoso.com domæne.
- Da vi ikke bruger parameteren _Prioritet_ , bruges standardprioriteten.
- Reglen er aktiveret (vi bruger ikke parameteren _Aktiveret_ , og standardværdien er `$true`).

```powershell
New-SafeAttachmentRule -Name "Contoso All" -SafeAttachmentPolicy "Contoso All" -RecipientDomainIs contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-SafeAttachmentRule](/powershell/module/exchange/new-safeattachmentrule).

### <a name="use-powershell-to-view-safe-attachment-policies"></a>Brug PowerShell til at få vist politikker for sikre vedhæftede filer

Hvis du vil have vist eksisterende politikker for sikre vedhæftede filer, skal du bruge følgende syntaks:

```PowerShell
Get-SafeAttachmentPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigt over alle politikker for sikre vedhæftede filer.

```PowerShell
Get-SafeAttachmentPolicy
```

I dette eksempel returneres detaljerede oplysninger om politikken for sikre vedhæftede filer med navnet Contoso-ledere.

```PowerShell
Get-SafeAttachmentPolicy -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-SafeAttachmentPolicy](/powershell/module/exchange/get-safeattachmentpolicy).

### <a name="use-powershell-to-view-safe-attachment-rules"></a>Brug PowerShell til at få vist regler for sikre vedhæftede filer

Hvis du vil have vist eksisterende regler for sikre vedhæftede filer, skal du bruge følgende syntaks:

```PowerShell
Get-SafeAttachmentRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled>] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

I dette eksempel returneres en oversigt over alle regler for sikre vedhæftede filer.

```PowerShell
Get-SafeAttachmentRule
```

Hvis du vil filtrere listen efter aktiverede eller deaktiverede regler, skal du køre følgende kommandoer:

```PowerShell
Get-SafeAttachmentRule -State Disabled
```

```PowerShell
Get-SafeAttachmentRule -State Enabled
```

I dette eksempel returneres detaljerede oplysninger om reglen om sikre vedhæftede filer med navnet Contoso-ledere.

```PowerShell
Get-SafeAttachmentRule -Identity "Contoso Executives" | Format-List
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Get-SafeAttachmentRule](/powershell/module/exchange/get-safeattachmentrule).

### <a name="use-powershell-to-modify-safe-attachment-policies"></a>Brug PowerShell til at ændre politikker for sikre vedhæftede filer

Du kan ikke omdøbe en politik for sikre vedhæftede filer i PowerShell ( **cmdlet'en Set-SafeAttachmentPolicy** har ingen _Navneparameter_ ). Når du omdøber Pengeskab politik for vedhæftede filer i Microsoft 365 Defender-portalen, omdøber du kun reglen om sikre vedhæftede _filer_.

Ellers er de samme indstillinger tilgængelige, når du opretter en politik for sikre vedhæftede filer, som beskrevet i Trin [1: Brug PowerShell](#step-1-use-powershell-to-create-a-safe-attachment-policy) til at oprette en politik for sikre vedhæftede filer tidligere i denne artikel.

Hvis du vil ændre en politik for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
Set-SafeAttachmentPolicy -Identity "<PolicyName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SafeAttachmentPolicy](/powershell/module/exchange/set-safeattachmentpolicy).

> [!NOTE]
> Hvis du vil have en detaljeret [](quarantine-policies.md) vejledning til at angive karantænepolitikken, der skal bruges i en sikker vedhæftet fil-politik, skal du se Brug PowerShell til at angive karantænepolitikken [Pengeskab politikker for vedhæftede filer](quarantine-policies.md#safe-attachments-policies-in-powershell).

### <a name="use-powershell-to-modify-safe-attachment-rules"></a>Brug PowerShell til at ændre regler for sikre vedhæftede filer

Den eneste indstilling, der ikke er tilgængelig, når du ændrer en sikker regel for vedhæftede filer i  PowerShell, er parameteren Enabled, der giver dig mulighed for at oprette en deaktiveret regel. Hvis du vil aktivere eller deaktivere eksisterende regler for sikre vedhæftede filer, skal du se næste afsnit.

Ellers er de samme indstillinger tilgængelige, når du opretter en regel som beskrevet i trin [2: Brug PowerShell](#step-2-use-powershell-to-create-a-safe-attachment-rule) til at oprette en sikker regel for vedhæftede filer tidligere i denne artikel.

Hvis du vil ændre en regel for sikre vedhæftede filer, skal du bruge denne syntaks:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" <Settings>
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-enable-or-disable-safe-attachment-rules"></a>Brug PowerShell til at aktivere eller deaktivere regler for sikre vedhæftede filer

Aktivering eller deaktivering af en regel for sikre vedhæftede filer i PowerShell aktiverer eller deaktiverer hele politikken for vedhæftede filer i Pengeskab (reglen om sikker vedhæftet fil og politikken for sikre vedhæftede filer).

Hvis du vil aktivere eller deaktivere en regel for sikre vedhæftede filer i PowerShell, skal du bruge denne syntaks:

```PowerShell
<Enable-SafeAttachmentRule | Disable-SafeAttachmentRule> -Identity "<RuleName>"
```

I dette eksempel deaktiveres reglen om sikre vedhæftede filer med navnet Marketingafdeling.

```PowerShell
Disable-SafeAttachmentRule -Identity "Marketing Department"
```

I dette eksempel kan du bruge den samme regel.

```PowerShell
Enable-SafeAttachmentRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter i [Enable-SafeAttachmentRule](/powershell/module/exchange/enable-safeattachmentrule) og [Disable-SafeAttachmentRule](/powershell/module/exchange/disable-safeattachmentrule).

### <a name="use-powershell-to-set-the-priority-of-safe-attachment-rules"></a>Brug PowerShell til at angive prioriteten af regler for sikre vedhæftede filer

Den højeste prioritetsværdi, du kan angive for en regel, er 0. Den laveste værdi, du kan angive, afhænger af antallet af regler. Hvis du f.eks. har fem regler, kan du bruge prioritetsværdierne 0 til 4. Hvis du ændrer prioriteten af en eksisterende regel, kan det have en overlappende effekt på andre regler. Hvis du f.eks. har fem brugerdefinerede regler (prioriteter 0 til 4), og du ændrer prioriteten af en regel til 2, ændres den eksisterende regel med prioritet 2 til prioritet 3, og reglen med prioritet 3 ændres til prioritet 4.

Hvis du vil angive prioriteten af en regel for sikre vedhæftede filer i PowerShell, skal du bruge følgende syntaks:

```PowerShell
Set-SafeAttachmentRule -Identity "<RuleName>" -Priority <Number>
```

I dette eksempel angives prioriteten af reglen Marketingafdeling til 2. Alle eksisterende regler, der har en prioritet, der er mindre end eller lig med 2, formindskes med 1 (deres prioritetstal øges med 1).

```PowerShell
Set-SafeAttachmentRule -Identity "Marketing Department" -Priority 2
```

**Bemærk**! For at angive prioriteten af en ny regel, når du opretter den, skal du bruge parameteren _Priority_ på **New-SafeAttachmentRule-cmdlet'en** i stedet.

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-SafeAttachmentRule](/powershell/module/exchange/set-safeattachmentrule).

### <a name="use-powershell-to-remove-safe-attachment-policies"></a>Brug PowerShell til at fjerne politikker for sikre vedhæftede filer

Når du bruger PowerShell til at fjerne en politik for sikker vedhæftet fil, fjernes den tilsvarende regel for sikker vedhæftet fil ikke.

Hvis du vil fjerne en politik for sikre vedhæftede filer i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeAttachmentPolicy -Identity "<PolicyName>"
```

I dette eksempel fjernes politikken for sikre vedhæftede filer med navnet Marketingafdeling.

```PowerShell
Remove-SafeAttachmentPolicy -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-SafeAttachmentPolicy](/powershell/module/exchange/remove-safeattachmentpolicy).

### <a name="use-powershell-to-remove-safe-attachment-rules"></a>Brug PowerShell til at fjerne regler for sikre vedhæftede filer

Når du bruger PowerShell til at fjerne en regel for sikker vedhæftet fil, fjernes den tilsvarende politik for sikre vedhæftede filer ikke.

Hvis du vil fjerne en regel for sikre vedhæftede filer i PowerShell, skal du bruge denne syntaks:

```PowerShell
Remove-SafeAttachmentRule -Identity "<PolicyName>"
```

I dette eksempel fjernes reglen for sikre vedhæftede filer med navnet Marketingafdeling.

```PowerShell
Remove-SafeAttachmentRule -Identity "Marketing Department"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-SafeAttachmentRule](/powershell/module/exchange/remove-safeattachmentrule).

## <a name="how-do-you-know-these-procedures-worked"></a>Hvordan ved du, at disse procedurer fungerede?

For at bekræfte, at du har oprettet, ændret eller fjernet Pengeskab politikker for vedhæftede filer, skal du gøre et af følgende:

- På siden **Pengeskab Vedhæftede** filer på Microsoft 365 Defender på <https://security.microsoft.com/safeattachmentv2>skal du bekræfte listen over politikker, deres **Statusværdier** og deres **Prioritetsværdier**. Hvis du vil have vist flere detaljer, skal du vælge politikken på listen ved at klikke på navnet og få vist detaljerne i pop op-menuen.

- I Exchange Online PowerShell eller Exchange Online Protection PowerShell \<Name\> skal du erstatte med navnet på politikken eller reglen, køre følgende kommando og kontrollere indstillingerne:

  ```PowerShell
  Get-SafeAttachmentPolicy -Identity "<Name>" | Format-List
  ```

  ```PowerShell
  Get-SafeAttachmentRule -Identity "<Name>" | Format-List
  ```

Kontrollér, at Pengeskab vedhæftede filer scanner meddelelser, ved at kontrollere den tilgængelige Defender til Office 365 rapporter. Få mere at vide under [Få vist rapporter for Defender Office 365](view-reports-for-mdo.md) [og Brug Stifinder Microsoft 365 Defender-portalen](threat-explorer.md).
