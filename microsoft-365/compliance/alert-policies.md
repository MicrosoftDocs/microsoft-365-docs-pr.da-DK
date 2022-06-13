---
title: Microsoft 365 politikker for beskeder
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
- admindeeplinkDEFENDER
description: Opret politikker for beskeder på Microsoft Purview-overholdelsesportalen eller på Microsoft 365 Defender-portalen for at overvåge potentielle trusler, problemer med datatab og tilladelser.
ms.openlocfilehash: 46be5c46c49b50286983517b7b1625f3309ca949
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015054"
---
# <a name="alert-policies-in-microsoft-365"></a>Beskedpolitikker i Microsoft 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Du kan bruge politikker for beskeder og dashboardet for beskeder på Microsoft Purview-overholdelsesportalen eller på Microsoft 365 Defender-portalen til at oprette politikker for beskeder og derefter få vist de beskeder, der genereres, når brugerne udfører aktiviteter, der opfylder betingelserne i en beskedpolitik. Der er flere standardpolitikker for beskeder, der hjælper dig med at overvåge aktiviteter, f.eks. tildeling af administratorrettigheder i Exchange Online, malwareangreb, phishingkampagner og usædvanlige niveauer af filsletninger og ekstern deling.

> [!TIP]
> Gå til afsnittet [Standardpolitikker for beskeder](#default-alert-policies) i denne artikel for at få en liste over og en beskrivelse af de tilgængelige politikker for beskeder.

Med politikker for beskeder kan du kategorisere de beskeder, der udløses af en politik, anvende politikken på alle brugere i din organisation, angive et tærskelniveau for, hvornår en besked udløses, og beslutte, om du vil modtage mailmeddelelser, når beskeder udløses. Der er også siden **Beskeder** , hvor du kan få vist og filtrere beskeder, angive en beskedstatus, der kan hjælpe dig med at administrere beskeder og derefter afvise beskeder, når du har løst eller løst den underliggende hændelse.

> [!NOTE]
> Beskedpolitikker er tilgængelige for organisationer med et Microsoft 365 Enterprise, Office 365 Enterprise eller Office 365 US Government E1/F1/G1, E3/F3/G3 eller E5/G5-abonnement. Avanceret funktionalitet er kun tilgængelig for organisationer med et E5/G5-abonnement eller for organisationer, der har et E1/F1/G1- eller E3/F3/G3-abonnement og et Microsoft Defender for Office 365 P2- eller et Microsoft 365 E5 Overholdelse- eller et E5 eDiscovery- og Audit-tilføjelsesprogram. Den funktionalitet, der kræver et E5/G5- eller tilføjelsesabonnement, er fremhævet i dette emne. Bemærk også, at beskedpolitikker er tilgængelige i miljøer med Office 365 GCC, GCC High og DoD US Government.

## <a name="how-alert-policies-work"></a>Sådan fungerer beskedpolitikker

Her er et hurtigt overblik over, hvordan politikker for beskeder fungerer, og de beskeder, der udløses, når bruger- eller administratoraktivitet stemmer overens med betingelserne for en beskedpolitik.

![Oversigt over, hvordan politikker for beskeder fungerer.](../media/M365ComplianceDefender-AlertPolicies-Overview.png)

1. En administrator i din organisation opretter, konfigurerer og aktiverer en beskedpolitik ved hjælp af siden **Beskedpolitikker** på portalen til overholdelse af regler og standarder eller på Microsoft 365 Defender-portalen. Du kan også oprette politikker for beskeder ved hjælp af Cmdlet'en [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) i Security & Compliance PowerShell.

   Hvis du vil oprette politikker for beskeder, skal du have tildelt rollen Administrer beskeder eller rollen Organisationskonfiguration på overholdelsesportalen eller Defender-portalen.

   > [!NOTE]
   > Det tager op til 24 timer, efter at du har oprettet eller opdateret en beskedpolitik, før beskeder kan udløses af politikken. Det skyldes, at politikken skal synkroniseres med programmet til registrering af beskeder.

2. En bruger udfører en aktivitet, der svarer til betingelserne i en beskedpolitik. I tilfælde af malwareangreb udløser inficerede mails, der sendes til brugere i din organisation, en besked.

3. Microsoft 365 genererer en besked, der vises på siden **Beskeder** i overholdelsesportalen eller På Defender-portalen. Hvis mailmeddelelser er aktiveret for beskedpolitikken, sender Microsoft også en meddelelse til en liste over modtagere. De beskeder, som en administrator eller andre brugere kan se på siden Beskeder, bestemmes af de roller, der er tildelt brugeren. Du kan få flere oplysninger under [RBAC-tilladelser, der kræves for at få vist beskeder](#rbac-permissions-required-to-view-alerts).

4. En administrator administrerer beskeder på Microsoft Purview-overholdelsesportalen. Administration af beskeder består i at tildele en beskedstatus som en hjælp til at spore og administrere enhver undersøgelse.

## <a name="alert-policy-settings"></a>Indstillinger for beskedpolitik

En beskedpolitik består af et sæt regler og betingelser, der definerer den bruger- eller administratoraktivitet, der genererer en besked, en liste over brugere, der udløser beskeden, hvis de udfører aktiviteten, og en tærskel, der definerer, hvor mange gange aktiviteten skal forekomme, før en besked udløses. Du kan også kategorisere politikken og tildele den et alvorsgradsniveau. Disse to indstillinger hjælper dig med at administrere politikker for beskeder (og de beskeder, der udløses, når politikbetingelserne matches), fordi du kan filtrere på disse indstillinger, når du administrerer politikker og får vist beskeder på Microsoft Purview-overholdelsesportalen. Du kan f.eks. få vist beskeder, der stemmer overens med betingelserne fra den samme kategori, eller få vist beskeder med samme alvorsgradsniveau.

Sådan får du vist og opretter politikker for beskeder:

### <a name="microsoft-purview-compliance-portal"></a>Microsoft Purview-overholdelsesportal

Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a>, og vælg derefter **Politikker** > **Beskedbeskedpolitikker** > .

![På Microsoft Purview-overholdelsesportalen skal du vælge Politikker og under Besked vælge Beskedpolitikker for at få vist og oprette politikker for beskeder.](../media/LaunchAlertPoliciesMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portal

Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og vælg **Politikker & regler** > **Beskedpolitik** under **Mail & samarbejde**. Du kan også gå direkte til <https://security.microsoft.com/alertpolicies>.

![På Defender-portalen skal du vælge Politikker & regler under Mail & samarbejde og derefter vælge Beskedpolitik for at få vist og oprette politikker for beskeder.](../media/LaunchAlertPoliciesDefenderPortal.png)

> [!NOTE]
> Du skal have tildelt rollen View-Only Administrer beskeder for at få vist beskedpolitikker på Microsoft Purview-overholdelsesportalen eller på Microsoft 365 Defender-portalen. Du skal have tildelt rollen Administrer beskeder for at oprette og redigere politikker for beskeder. Du kan få flere oplysninger under [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md).

En beskedpolitik består af følgende indstillinger og betingelser.

- **Aktivitet, som beskeden sporer**. Du opretter en politik for at spore en aktivitet eller i nogle tilfælde nogle relaterede aktiviteter, f.eks. deling af en fil med en ekstern bruger ved at dele den, tildele adgangstilladelser eller oprette et anonymt link. Når en bruger udfører den aktivitet, der er defineret af politikken, udløses en besked baseret på indstillingerne for beskedtærskel.

    > [!NOTE]
    > De aktiviteter, du kan spore, afhænger af organisationens Office 365 Enterprise eller Office 365 US Government-plan. Aktiviteter, der er relateret til malwarekampagner og phishingangreb, kræver generelt et E5/G5-abonnement eller et E1/F1/G1- eller E3/F3/G3-abonnement med et abonnement på et [Defender for Office 365](../security/office-365-security/defender-for-office-365.md) Plan 2-tilføjelsesprogram.

- **Aktivitetsbetingelser**. For de fleste aktiviteter kan du definere yderligere betingelser, der skal være opfyldt for at udløse en besked. Almindelige betingelser omfatter IP-adresser (så en besked udløses, når brugeren udfører aktiviteten på en computer med en bestemt IP-adresse eller inden for et IP-adresseområde), om en besked udløses, hvis en bestemt bruger eller brugere udfører denne aktivitet, og om aktiviteten udføres på et bestemt filnavn eller en BESTEMT URL-adresse. Du kan også konfigurere en betingelse, der udløser en besked, når aktiviteten udføres af en hvilken som helst bruger i din organisation. De tilgængelige betingelser afhænger af den valgte aktivitet.

Du kan også definere brugerkoder som en betingelse for en beskedpolitik. Dette resulterer i de beskeder, der udløses af politikken, for at inkludere konteksten for den påvirkede bruger. Du kan bruge systembrugerkoder eller brugerdefinerede brugerkoder. Du kan få flere oplysninger [under Brugerkoder i Microsoft Defender for Office 365](/microsoft-365/security/office-365-security/user-tags).

- **Når beskeden udløses**. Du kan konfigurere en indstilling, der definerer, hvor ofte en aktivitet kan forekomme, før en besked udløses. Dette giver dig mulighed for at konfigurere en politik til at generere en besked, hver gang en aktivitet stemmer overens med politikbetingelserne, når en bestemt grænse overskrides, eller når forekomsten af den aktivitet, som beskeden sporer, bliver usædvanlig for din organisation.

    ![Konfigurer, hvordan beskeder udløses, afhængigt af hvornår aktiviteten forekommer, en tærskel eller usædvanlig aktivitet for din organisation.](../media/howalertsaretriggered.png)

    Hvis du vælger indstillingen baseret på usædvanlig aktivitet, opretter Microsoft en oprindelig værdi, der definerer den normale frekvens for den valgte aktivitet. Det tager op til syv dage at oprette denne baseline, hvor der ikke genereres beskeder. Når den oprindelige plan er oprettet, udløses en besked, når hyppigheden af den aktivitet, der spores af beskedpolitikken, langt overstiger den oprindelige værdi. I forbindelse med overvågningsaktiviteter (f.eks. fil- og mappeaktiviteter) kan du oprette en oprindelig plan baseret på en enkelt bruger eller baseret på alle brugere i organisationen. I forbindelse med malwarerelaterede aktiviteter kan du oprette en baseline baseret på en enkelt malwarefamilie, en enkelt modtager eller alle meddelelser i din organisation.

    > [!NOTE]
    > Muligheden for at konfigurere beskedpolitikker baseret på en tærskel eller baseret på usædvanlig aktivitet kræver et E5/G5-abonnement eller et E1/F1/G1- eller E3/F3/G3-abonnement med et Microsoft Defender for Office 365 P2-, Microsoft 365 E5 Overholdelse- eller Microsoft 365 tilføjelsesprogram til eDiscovery og overvågning Abonnement. Organisationer med et E1/F1/G1- og E3/F3/G3-abonnement kan kun oprette beskedpolitikker, hvor en besked udløses, hver gang en aktivitet forekommer.

- **Beskedkategori**. Hvis du vil hjælpe med at spore og administrere de beskeder, der genereres af en politik, kan du tildele en af følgende kategorier til en politik.

  - Forebyggelse af datatab

  - Administration af datalivscyklus

  - Mailflow

  - Tilladelser

  - Trusselsstyring

  - Andre

  Når der forekommer en aktivitet, der svarer til betingelserne i beskedpolitikken, mærkes den genererede besked med den kategori, der er defineret i denne indstilling. Det giver dig mulighed for at spore og administrere beskeder, der har samme kategoriindstilling på siden **Beskeder** på Microsoft Purview-portalen, fordi du kan sortere og filtrere beskeder baseret på kategori.

- **Alvorsgrad af vigtig besked**. På samme måde som med kategorien for beskeder tildeler du en alvorsgradattribut (**Low**, **Medium**, **High** eller **Informational**) til beskedpolitikker. Når der forekommer en aktivitet, der svarer til betingelserne i beskedpolitikken, mærkes den genererede besked på samme alvorsgradsniveau, som er angivet for beskedpolitikken, på samme måde som kategorien for beskeder. Igen giver dette dig mulighed for at spore og administrere beskeder, der har samme alvorsgrad på siden **Beskeder** . Du kan f.eks. filtrere listen over beskeder, så der kun vises beskeder med **høj** alvorsgrad.

    > [!TIP]
    > Når du konfigurerer en beskedpolitik, kan du overveje at tildele aktiviteter, der kan medføre alvorligt negative konsekvenser, f.eks. registrering af malware efter levering til brugere, visning af følsomme eller klassificerede data, deling af data med eksterne brugere eller andre aktiviteter, der kan medføre tab af data eller sikkerhedstrusler. Dette kan hjælpe dig med at prioritere beskeder og de handlinger, du foretager for at undersøge og løse de underliggende årsager.

- **Automatiserede undersøgelser**. Nogle beskeder udløser automatiserede undersøgelser for at identificere potentielle trusler og risici, der kræver afhjælpning eller afhjælpning.  I de fleste tilfælde udløses disse beskeder ved registrering af skadelige mails eller aktiviteter, men i nogle tilfælde udløses beskederne af administratorhandlinger på sikkerhedsportalen.  Du kan få flere oplysninger om automatiserede undersøgelser [under Automatiseret undersøgelse og svar (AIR) i Microsoft Defender for Office 365](../security/office-365-security/office-365-air.md).

- **Mailmeddelelser**. Du kan konfigurere politikken, så mailmeddelelser sendes (eller ikke sendes) til en liste over brugere, når en besked udløses. Du kan også angive en daglig meddelelsesgrænse, så når det maksimale antal meddelelser er nået, sendes der ikke flere meddelelser for beskeden i løbet af den pågældende dag. Ud over mailmeddelelser kan du eller andre administratorer få vist de beskeder, der udløses af en politik på siden **Beskeder** . Overvej at aktivere mailmeddelelser for beskedpolitikker for en bestemt kategori, eller som har en indstilling med højere alvorsgrad.

## <a name="default-alert-policies"></a>Standardpolitikker for beskeder

Microsoft leverer indbyggede beskedpolitikker, der hjælper med at identificere Exchange misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler samt risici for administration af datalivscyklusser. På siden **Beskedpolitikker** er navnene på disse indbyggede politikker med fed skrift, og politiktypen er defineret som **System**. Disse politikker er som standard slået til. Du kan slå disse politikker (eller slå dem til igen), konfigurere en liste over modtagere, der skal sendes mailmeddelelser til, og angive en daglig grænse for meddelelser. De andre indstillinger for disse politikker kan ikke redigeres.

I følgende tabel vises og beskrives de tilgængelige standardbeskedpolitikker og den kategori, som hver politik tildeles til. Kategorien bruges til at bestemme, hvilke beskeder en bruger kan få vist på siden Beskeder. Du kan få flere oplysninger under [RBAC-tilladelser, der kræves for at få vist beskeder](#rbac-permissions-required-to-view-alerts).

Tabellen angiver også den Office 365 Enterprise og Office 365 US Government-plan, der kræves for hver enkelt. Nogle standardpolitikker for beskeder er tilgængelige, hvis din organisation har det relevante tilføjelsesprogramabonnement ud over et E1/F1/G1- eller E3/F3/G3-abonnement.
 
| Standardbeskedpolitik | Beskrivelse | Kategori | Automatiseret undersøgelse | Enterprise-abonnement |
|:-----|:-----|:-----|:-----|:-----|
|**Der blev registreret et potentielt skadeligt klik på URL-adressen**|Genererer en besked, når en bruger, der er beskyttet af [Pengeskab Links](../security/office-365-security/safe-links.md) i din organisation, klikker på et skadeligt link. Denne hændelse udløses, når ændringer i URL-adressens dom identificeres af Microsoft Defender for Office 365, eller når brugerne tilsidesætter siderne med Pengeskab links (baseret på organisationens politik for Microsoft 365 for virksomheder Pengeskab links). Denne beskedpolitik har en indstilling **med høj** alvorsgrad. For Defender for Office 365 P2-, E5- og G5-kunder udløser denne besked automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md). Du kan få flere oplysninger om hændelser, der udløser denne besked, under [Konfigurer politikker for Pengeskab links](../security/office-365-security/set-up-safe-links-policies.md).|Trusselsstyring|Ja|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Resultat af administratorindsendelse er fuldført**|Genererer en besked, når en [administratorindsendelse](../security/office-365-security/admin-submission.md) fuldfører genscannelsen af den sendte enhed. Der udløses en besked, hver gang et genscannet resultat gengives fra en administratorindsendelse. Disse beskeder er beregnet til at minde dig om at [gennemse resultaterne af tidligere indsendelser](https://compliance.microsoft.com/reportsubmission), sende brugerrapporterede meddelelser for at få den seneste politikkontrol og scanne domme igen og hjælpe dig med at afgøre, om filtreringspolitikkerne i din organisation har den tilsigtede virkning. Denne politik har en indstilling **for oplysningers** alvorsgrad.|Trusselsstyring|Nej|E1/F1, E3/F3 eller E5|
|**Administratoren udløste manuel undersøgelse af mail**|Genererer en besked, når en administrator udløser den manuelle undersøgelse af en mail fra Threat Explorer. Du kan få flere oplysninger under [Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). Denne besked giver din organisation besked om, at undersøgelsen blev startet. Beskeden indeholder oplysninger om, hvem der har udløst den, og indeholder et link til undersøgelsen. Denne politik har en indstilling **for oplysningers** alvorsgrad.|Trusselsstyring|Ja|E5/G5- eller Microsoft Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Administratoren udløste en undersøgelse af bruger kompromitteret**|Genererer en besked, når en administrator udløser den manuelle bruger kompromitterende undersøgelse af enten en mail afsender eller modtager fra Threat Explorer. Du kan få flere oplysninger under [Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer), som viser den relaterede manuelle udløsning af en undersøgelse i en mail. Denne besked giver din organisation besked om, at undersøgelsen af bruger kompromitteret blev startet. Beskeden indeholder oplysninger om, hvem der har udløst den, og indeholder et link til undersøgelsen. Denne politik har en indstilling for **mellem** alvorsgrad.|Trusselsstyring|Ja|E5/G5- eller Microsoft Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Oprettelse af regel for videresendelse/omdirigering**|Genererer en besked, når en person i din organisation opretter en indbakkeregel for deres postkasse, der videresender eller omdirigerer meddelelser til en anden mailkonto. Denne politik sporer kun indbakkeregler, der er oprettet ved hjælp af Outlook på internettet (tidligere kaldet Outlook Web App) eller Exchange Online PowerShell. Denne politik har en indstilling **for oplysningers** alvorsgrad. Du kan få flere oplysninger om, hvordan du bruger indbakkeregler til at videresende og omdirigere mails i Outlook på internettet, [under Brug regler i Outlook på internettet til automatisk at videresende meddelelser til en anden konto](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**eDiscovery-søgning er startet eller eksporteret**|Genererer en besked, når nogen bruger indholdssøgeværktøjet på Microsoft Purview-portalen. En besked udløses, når følgende aktiviteter for indholdssøgning udføres: <br><br> <li> En indholdssøgning startes <li> Resultaterne af en indholdssøgning eksporteres <li> Der eksporteres en rapport til indholdssøgning <br><br> Beskeder udløses også, når de tidligere aktiviteter til indholdssøgning udføres i tilknytning til en eDiscovery-sag. Denne politik har en indstilling **for oplysningers** alvorsgrad. Du kan finde flere oplysninger om aktiviteter for indholdssøgning under [Søg efter eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Udvidede rettigheder som Exchange administrator**|Genererer en besked, når en person er tildelt administrative tilladelser i din Exchange Online organisation. Når en bruger f.eks. føjes til rollegruppen Organisationsadministration i Exchange Online. Denne politik har en indstilling **for lav** alvorsgrad.|Tilladelser|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Mails, der indeholder skadelig fil, er fjernet efter levering**|Genererer en besked, når meddelelser, der indeholder en skadelig fil, leveres til postkasser i din organisation. Hvis denne hændelse opstår, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [automatisk tømning på nul timer](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en indstilling for **oplysningers** alvorsgrad og udløser automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md). Du kan få flere oplysninger om denne nye politik [under Nye politikker for beskeder i Microsoft Defender for Office 365](new-defender-alert-policies.md).|Trusselsstyring|Ja|E5/G5- eller Microsoft Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Mails, der indeholder skadelig URL-adresse, er fjernet efter levering**|Genererer en besked, når meddelelser, der indeholder en skadelig URL-adresse, leveres til postkasser i din organisation. Hvis denne hændelse opstår, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [automatisk tømning på nul timer](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en indstilling for **oplysningers** alvorsgrad og udløser automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md). Du kan få flere oplysninger om denne nye politik [under Nye politikker for beskeder i Microsoft Defender for Office 365](new-defender-alert-policies.md).|Trusselsstyring|Ja|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Mails fra en kampagne, der er fjernet efter levering**|Genererer en besked, når meddelelser, der er knyttet til en [kampagne](../security/office-365-security/campaigns.md) , leveres til postkasser i din organisation. Hvis denne hændelse opstår, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [automatisk tømning på nul timer](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en indstilling for **oplysningers** alvorsgrad og udløser automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md). Du kan få flere oplysninger om denne nye politik [under Nye politikker for beskeder i Microsoft Defender for Office 365](new-defender-alert-policies.md).|Trusselsstyring|Ja|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Mails, der er fjernet efter levering**|Genererer en besked, når skadelige meddelelser, der ikke indeholder en skadelig enhed (URL-adresse eller fil) eller er knyttet til en kampagne, leveres til postkasser i din organisation. Hvis denne hændelse opstår, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [automatisk tømning på nul timer](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en indstilling for **oplysningers** alvorsgrad og udløser automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md). Du kan få flere oplysninger om denne nye politik [under Nye politikker for beskeder i Microsoft Defender for Office 365](new-defender-alert-policies.md).|Trusselsstyring|Ja|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Meddelelser, der indeholder skadelig enhed, fjernes ikke efter levering**|Genererer en besked, når en meddelelse, der indeholder skadeligt indhold (fil, URL-adresse, kampagne, ingen enhed), leveres til postkasser i din organisation. Hvis denne hændelse indtræffer, forsøgte Microsoft at fjerne de inficerede meddelelser fra Exchange Online postkasser ved hjælp af [automatisk fjernelse på nul timer](../security/office-365-security/zero-hour-auto-purge.md), men meddelelsen blev ikke fjernet på grund af en fejl. Yderligere undersøgelse anbefales. Denne politik har en indstilling for **mellem** alvorsgrad og udløser automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md).|Trusselsstyring|Ja|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Mail, der er rapporteret af brugeren som malware eller phish**|Genererer en besked, når brugere i organisationen rapporterer meddelelser som phishingmail ved hjælp af tilføjelsesprogrammet Rapportmeddelelse. Denne politik har en indstilling **med lav** alvorsgrad. Du kan få flere oplysninger om dette tilføjelsesprogram under [Brug tilføjelsesprogrammet Rapportmeddelelse](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). For Defender for Office 365 P2-, E5- og G5-kunder udløser denne besked automatisk [automatiseret undersøgelse og svar i Office 365](../security/office-365-security/office-365-air.md).|Trusselsstyring|Ja|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Grænsen for afsendelse af mail er overskredet**|Genererer en besked, når en person i din organisation har sendt flere mails, end det er tilladt af politikken for udgående spam. Dette er normalt en indikation af, at brugeren sender for meget mail, eller at kontoen kan blive kompromitteret. Denne politik har en indstilling for **mellem** alvorsgrad. Hvis du får en besked, der genereres af denne beskedpolitik, er det en god idé at [kontrollere, om brugerkontoen er kompromitteret](../security/office-365-security/responding-to-a-compromised-email-account.md).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Formularen er blokeret på grund af et muligt forsøg på phishing**|Genererer en besked, når en person i din organisation er blevet begrænset fra at dele formularer og indsamle svar ved hjælp af Microsoft Forms på grund af registreret gentaget phishing-forsøg. Denne politik har en indstilling **med høj alvorsgrad** .|Trusselsstyring|Nej|E1, E3/F3 eller E5|
|**Formular, der er markeret og bekræftet som phishing**|Genererer en besked, når en formular, der er oprettet i Microsoft Forms fra din organisation, er blevet identificeret som potentiel phishing via Rapportér misbrug og bekræftet som phishing af Microsoft. Denne politik har en indstilling **med høj** alvorsgrad.|Trusselsstyring|Nej|E1, E3/F3 eller E5|
|**Meddelelser er blevet forsinket**|Genererer en besked, når Microsoft ikke kan levere mails til din organisation i det lokale miljø eller en partnerserver ved hjælp af en connector. Når det sker, sættes meddelelsen i kø i Office 365. Denne besked udløses, når der er 2.000 meddelelser eller mere, der er sat i kø i mere end en time. Denne politik har en indstilling **med høj** alvorsgrad.|Mailflow|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Malwarekampagne registreret efter levering**|Genererer en besked, når et usædvanligt stort antal meddelelser, der indeholder malware, leveres til postkasser i din organisation. Hvis denne hændelse opstår, fjerner Microsoft de inficerede meddelelser fra Exchange Online postkasser. Denne politik har en indstilling **med høj** alvorsgrad.|Trusselsstyring|Nej|E5/G5- eller Microsoft Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Malwarekampagne registreret og blokeret**|Genererer en besked, når en person har forsøgt at sende et usædvanligt stort antal mails, der indeholder en bestemt type malware, til brugere i din organisation. Hvis denne hændelse opstår, blokeres de inficerede meddelelser af Microsoft og leveres ikke til postkasser. Denne politik har en indstilling **for lav** alvorsgrad.|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Malwarekampagne, der er registreret i SharePoint og OneDrive**|Genererer en besked, når der registreres en usædvanlig stor mængde malware eller virus i filer, der er placeret på SharePoint websteder eller OneDrive konti i din organisation. Denne politik har en indstilling **med høj** alvorsgrad.|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Malware blev ikke zapped, fordi ZAP er deaktiveret**| Genererer en besked, når Microsoft registrerer levering af en malwaremeddelelse til en postkasse, fordi Zero-Hour Automatisk udrensning for Phish-meddelelser er deaktiveret. Denne politik har en indstilling **for oplysningers** alvorsgrad. |Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Phish leveres, fordi en brugers mappe med uønsket mail er deaktiveret**|Genererer en besked, når Microsoft registrerer, at en brugers mappe med uønsket mail er deaktiveret, så der kan leveres en phishingmeddelelse med høj sikkerhed til en postkasse. Denne politik har en indstilling **for oplysningers** alvorsgrad.|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Phish leveret på grund af en TILSIDESÆTTELSE AF ETR**|Genererer en besked, når Microsoft registrerer en etr (Exchange Transport Rule), der tillader levering af en phishingmeddelelse med høj sikkerhed til en postkasse. Denne politik har en indstilling **for oplysningers** alvorsgrad. Du kan få flere oplysninger om Exchange transportregler (regler for mailflow[) under Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Phish leveret på grund af en ip-tilladelsespolitik**|Genererer en besked, når Microsoft registrerer en IP-tilladelsespolitik, der tillader levering af en phishingmeddelelse med høj sikkerhed til en postkasse. Denne politik har en indstilling **for oplysningers** alvorsgrad. Du kan få flere oplysninger om ip-tilladelsespolitikken (forbindelsesfiltrering) under [Konfigurer standardfilterpolitikken for forbindelse – Office 365](../security/office-365-security/configure-the-connection-filter-policy.md).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Phish ikke zapped, fordi ZAP er deaktiveret**| Genererer en besked, når Microsoft registrerer levering af en phishingmeddelelse med høj genkendelsessikkerhed til en postkasse, fordi Zero-Hour Automatisk udrensning for Phish-meddelelser er deaktiveret. Denne politik har en indstilling **for oplysningers** alvorsgrad.|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Phish leveret på grund af tilsidesættelse af lejer eller bruger**<sup>1</sup>|Genererer en besked, når Microsoft registrerer, at en tilsidesættelse af en administrator eller bruger har tilladt levering af en phishing-meddelelse til en postkasse. Eksempler på tilsidesættelser omfatter en indbakke- eller mailflowregel, der tillader meddelelser fra en bestemt afsender eller et bestemt domæne eller en politik mod spam, der tillader meddelelser fra bestemte afsendere eller domæner. Denne politik har en indstilling **med høj** alvorsgrad.|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Mistænkelig aktivitet for videresendelse af mail**|Genererer en besked, når en person i din organisation automatisk har videresendt en mail til en mistænkelig ekstern konto. Dette er en tidlig advarsel om funktionsmåde, der kan indikere, at kontoen er kompromitteret, men ikke alvorlig nok til at begrænse brugeren. Denne politik har en indstilling **med høj** alvorsgrad. Selvom det er sjældent, kan en besked, der genereres af denne politik, være en uregelmæssighed. Det er en god idé at [kontrollere, om brugerkontoen er kompromitteret](../security/office-365-security/responding-to-a-compromised-email-account.md).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Registrerede mønstre for afsendelse af mistænkelige mails**|Genererer en besked, når en person i din organisation har sendt mistænkelig mail og er i fare for at blive begrænset fra at sende mail. Dette er en tidlig advarsel om funktionsmåde, der kan indikere, at kontoen er kompromitteret, men ikke alvorlig nok til at begrænse brugeren. Denne politik har en indstilling for **mellem** alvorsgrad. Selvom det er sjældent, kan en besked, der genereres af denne politik, være en uregelmæssighed. Det er dog en god idé at [kontrollere, om brugerkontoen er kompromitteret](../security/office-365-security/responding-to-a-compromised-email-account.md).|Trusselsstyring|Ja|E1/F1/G1, E3/F3/G3 eller E5/G5  |
|**Lejerens tilladelses-/bloklistepost er ved at udløbe**|Genererer en besked, når en post på listen over tilladte/blokerede lejere er ved at blive fjernet. Denne hændelse udløses tre dage før udløbsdatoen, hvilket er baseret på, hvornår posten blev oprettet eller sidst opdateret. Denne beskedpolitik har en indstilling **for oplysningers** alvorsgrad. Dette er for at informere administratorer om kommende ændringer i filtrene, da tillad eller blok kan forsvinder. For blokke kan du forlænge udløbsdatoen for at bevare blokken på plads. For tillader det skal du sende elementet igen, så vores analytikere kan se nærmere på det igen. Men hvis tilladelsen allerede er klassificeret som falsk positiv, udløber posten kun, når systemfiltrene er blevet opdateret, så posten naturligvis tillades. Du kan få flere oplysninger om hændelser, der udløser denne besked, [under Administrer listen over tilladte/blokerede lejere](../security/office-365-security/tenant-allow-block-list.md).|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Lejeren er begrænset til at sende mail**|Genererer en besked, når det meste af mailtrafikken fra din organisation er blevet registreret som mistænkelig, og Microsoft har begrænset din organisation til at sende mail. Undersøg eventuelle kompromitterede bruger- og administratorkonti, nye connectors eller åbne relæer, og kontakt derefter Microsoft Support for at fjerne blokeringen af din organisation. Denne politik har en indstilling **med høj** alvorsgrad. Du kan finde flere oplysninger om, hvorfor organisationer er blokeret, under [Løs problemer med levering af mail for fejlkode 5.7.7xx i Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Lejeren er begrænset til at sende ikke-klargjort mail**|Genererer en besked, når der sendes for mange mails fra ikke-registrerede domæner (også kendt som *ikke-klargjorte* domæner). Office 365 tillader en rimelig mængde mail fra ikke-registrerede domæner, men du skal konfigurere alle domæner, du bruger til at sende mail som et accepteret domæne. Denne besked angiver, at alle brugere i organisationen ikke længere kan sende mails. Denne politik har en indstilling **med høj** alvorsgrad. Du kan finde flere oplysninger om, hvorfor organisationer er blokeret, under [Løs problemer med levering af mail for fejlkode 5.7.7xx i Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Usædvanlig aktivitet i eksterne brugerfiler**|Genererer en besked, når et usædvanligt stort antal aktiviteter udføres på filer i SharePoint eller OneDrive af brugere uden for organisationen. Dette omfatter aktiviteter som f.eks. adgang til filer, hentning af filer og sletning af filer. Denne politik har en indstilling **med høj** alvorsgrad.|Administration af datalivscyklus|Nej|E5/G5, Microsoft Defender for Office 365 P2 eller Microsoft 365 E5 tilføjelsesprogramabonnement|
|**Usædvanlig mængde ekstern fildeling**|Genererer en besked, når et usædvanligt stort antal filer i SharePoint eller OneDrive deles med brugere uden for organisationen. Denne politik har en indstilling for **mellem** alvorsgrad.|Administration af datalivscyklus|Nej|E5/G5, Defender for Office 365 P2 eller Microsoft 365 E5 tilføjelsesprogramabonnement|
|**Usædvanlig mængde af filsletning**|Genererer en besked, når et usædvanligt stort antal filer slettes i SharePoint eller OneDrive inden for en kort tidsramme. Denne politik har en indstilling for **mellem** alvorsgrad.|Administration af datalivscyklus|Nej|E5/G5, Defender for Office 365 P2 eller Microsoft 365 E5 tilføjelsesprogramabonnement|
|**Usædvanlig stigning i e-mail rapporteret som phish**|Genererer en besked, når der er en betydelig stigning i antallet af personer i din organisation ved hjælp af tilføjelsesprogrammet Rapportmeddelelse Outlook til at rapportere meddelelser som phishing-mails. Denne politik har en indstilling for **mellem** alvorsgrad. Du kan få flere oplysninger om dette tilføjelsesprogram under [Brug tilføjelsesprogrammet Rapportmeddelelse](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Brugeridentificeret udtryk leveret til indbakke/mappe**<sup>1,2</sup><sup></sup>|Genererer en besked, når Microsoft registrerer, at en tilsidesættelse af en administrator eller bruger har tilladt levering af en phishing-meddelelse om brugerrepræsentation til indbakken (eller en anden mappe, der er tilgængelig for brugeren) i en postkasse. Eksempler på tilsidesættelser omfatter en indbakke- eller mailflowregel, der tillader meddelelser fra en bestemt afsender eller et bestemt domæne eller en politik mod spam, der tillader meddelelser fra bestemte afsendere eller domæner. Denne politik har en indstilling for **mellem** alvorsgrad.|Trusselsstyring|Nej|E5/G5- eller Defender for Office 365 P2-tilføjelsesprogramabonnement|
|**Brugeren har anmodet om at frigive en karantænemeddelelse**|Genererer en besked, når en bruger anmoder om frigivelse af en karantænemeddelelse. Hvis du vil anmode om frigivelse af karantænemeddelelser, skal du i karantænepolitikken (f.eks. fra gruppen Forudindstillede tilladelser med **begrænset adgang**) **tillade, at modtagerne anmoder om, at en meddelelse frigives fra karantæne** (_PermissionToRequestRelease_). Du kan få flere oplysninger under [Tillad, at modtagerne anmoder om, at en meddelelse frigives fra karantænetilladelsen](../security/office-365-security/quarantine-policies.md#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission). Denne politik har en indstilling **for oplysningers** alvorsgrad.|Trusselsstyring|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Brugeren er begrænset til at sende mail**|Genererer en besked, når en person i din organisation er begrænset fra at sende udgående mails. Dette resulterer typisk, når en konto kompromitteres, og brugeren er angivet på siden **Brugere med begrænset adgang** på overholdelsesportalen. (Hvis du vil have adgang til denne side, skal du gå til **Threat Management > Gennemse > Brugere med begrænset adgang**). Denne politik har en indstilling **med høj** alvorsgrad. Du kan finde flere oplysninger om brugere med begrænset adgang under [Fjernelse af en bruger, et domæne eller en IP-adresse fra en blokliste efter afsendelse af spammail](/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Trusselsstyring|Ja|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Brugeren er begrænset fra at dele formularer og indsamle svar**|Genererer en besked, når en person i din organisation er blevet begrænset fra at dele formularer og indsamle svar ved hjælp af Microsoft Forms på grund af registreret gentaget phishing-forsøg. Denne politik har en indstilling **med høj** alvorsgrad.|Trusselsstyring|Nej|E1, E3/F3 eller E5|

> [!NOTE]
> <sup>1</sup> Vi har midlertidigt fjernet denne standardbeskedpolitik baseret på kundefeedback. Vi arbejder på at forbedre den og erstatter den med en ny version i den nærmeste fremtid. Indtil da kan du oprette en brugerdefineret beskedpolitik for at erstatte denne funktionalitet ved hjælp af følgende indstillinger: <ul><li>Aktivitet er phishmail, der registreres på leveringstidspunktet</li> <li>Mail er ikke ZAP'd</li> <li>Postretning er indgående</li> <li>Status for levering af post er Leveret</li> <li>Registreringsteknologi er opbevaring af skadelige URL-adresser, detonation af URL-adresser, avanceret phishfilter, generelt phishfilter, domænerepræsentation, brugerrepræsentation og brandrepræsentation</li></ul> Du kan få flere oplysninger om anti-phishing i Office 365 under [Konfigurer politikker til anti-phishing og anti-phishing](../security/office-365-security/set-up-anti-phishing-policies.md).<br/><br/><sup>2</sup> Hvis du vil genoprette denne beskedpolitik, skal du følge vejledningen i den forrige fodnote, men vælge Brugerrepræsentation som den eneste registreringsteknologi.

Den usædvanlige aktivitet, der overvåges af nogle af de indbyggede politikker, er baseret på den samme proces som den indstilling for beskedtærskel, der tidligere blev beskrevet. Microsoft opretter en oprindelig værdi, der definerer den normale frekvens for "sædvanlig" aktivitet. Beskeder udløses derefter, når hyppigheden af aktiviteter, der spores af den indbyggede beskedpolitik, langt overstiger den oprindelige værdi.

<a name="viewing-alerts"></a>

## <a name="view-alerts"></a>Vis beskeder

Når en aktivitet, der udføres af brugere i din organisation, stemmer overens med indstillingerne for en beskedpolitik, oprettes der en besked, som vises på siden **Beskeder** på Microsoft Purview-portalen eller På Defender-portalen. Afhængigt af indstillingerne for en beskedpolitik sendes der også en mailmeddelelse til en liste over angivne brugere, når en besked udløses. For hver besked viser dashboardet på siden **Beskeder** navnet på den tilsvarende beskedpolitik, alvorsgraden og kategorien for beskeden (defineret i beskedpolitikken) og det antal gange, en aktivitet har fundet sted, hvilket har medført, at beskeden genereres. Denne værdi er baseret på tærsklen for beskedpolitikken. Dashboardet viser også status for hver besked. Du kan få flere oplysninger om, hvordan du bruger statusegenskaben til at administrere beskeder, under [Administration af beskeder](#manage-alerts).

Sådan får du vist beskeder:

### <a name="microsoft-purview-compliance-portal"></a>Microsoft Purview-overholdelsesportal

 Gå til , <https://compliance.microsoft.com> og vælg derefter **Beskeder**. Du kan også gå direkte til <https://compliance.microsoft.com/compliancealerts>.

![Vælg Beskeder på overholdelsesportalen.](../media/ViewAlertsMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender portal

Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal,</a> og vælg derefter **Hændelser & beskeder** > **Beskeder**. Du kan også gå direkte til <https://security.microsoft.com/alerts>.

![På Microsoft 365 Defender-portalen skal du vælge Hændelser & beskeder og derefter vælge Beskeder.](../media/ViewAlertsDefenderPortal.png)

Du kan bruge følgende filtre til at få vist et undersæt af alle beskeder på siden **Beskeder** .

- **Status.** Brug dette filter til at få vist beskeder, der er tildelt en bestemt status. Standardstatussen er **Aktiv**. Du eller andre administratorer kan ændre statusværdien.

- **Politik.** Brug dette filter til at få vist beskeder, der stemmer overens med indstillingen af en eller flere politikker for beskeder. Eller du kan få vist alle beskeder for alle beskedpolitikker.

- **Tidsinterval.** Brug dette filter til at få vist beskeder, der er genereret inden for et bestemt dato- og tidsinterval.

- **Sværhedsgraden.** Brug dette filter til at få vist beskeder, der er tildelt en bestemt alvorsgrad.

- **Kategori.** Brug dette filter til at få vist beskeder fra en eller flere beskedkategorier.

- **Tags.** Brug dette filter til at få vist beskeder fra en eller flere brugerkoder. Mærker afspejles baseret på mærkede postkasser eller brugere, der vises i beskederne. Se [Brugerkoder i Office 356 ATP](../security/office-365-security/user-tags.md) for at få mere at vide.

- **Kilde.** Brug dette filter til at få vist beskeder, der udløses af beskedpolitikker på Microsoft Purview-portalen, eller beskeder, der udløses af Microsoft Defender for Cloud Apps politikker eller begge dele. Du kan få flere oplysninger om beskeder om Cloud App Security under [Visning af beskeder i Defender for Cloud Apps](#viewing-cloud-app-security-alerts).

> [!IMPORTANT]
> Filtrering og sortering efter brugerkoder er i øjeblikket en offentlig prøveversion.
> Den kan blive ændret væsentligt, før den udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der gives om det.

## <a name="alert-aggregation"></a>Beskedsammenlægning

Når flere hændelser, der matcher betingelserne for en beskedpolitik, forekommer med en kort periode, føjes de til en eksisterende besked af en proces, der kaldes *beskedsammenlægning*. Når en hændelse udløser en besked, genereres beskeden og vises på siden **Beskeder** , og der sendes en meddelelse. Hvis den samme hændelse forekommer inden for sammenlægningsintervallet, føjer Microsoft 365 oplysninger om den nye hændelse til den eksisterende besked i stedet for at udløse en ny besked. Målet med sammenlægning af beskeder er at hjælpe med at reducere advarslen "træthed" og lade dig fokusere og handle på færre beskeder for den samme hændelse.

Længden af sammenlægningsintervallet afhænger af dit Office 365 eller Microsoft 365 abonnement.

|Abonnement|Sammenlægningsinterval|
|:---------|:---------:|
|Office 365 eller Microsoft 365 E5/G5|1 minut|
|Defender for Office 365 Plan 2 |1 minut|
|Tilføjelsesprogrammet E5 Compliance eller tilføjelsesprogrammet E5 Discovery and Audit|1 minut|
|Office 365 eller Microsoft 365 E1/F1/G1 eller E3/F3/G3|15 minutter|
|Defender for Office 365 plan 1 eller Exchange Online Protection|15 minutter|

Når hændelser, der stemmer overens med den samme beskedpolitik, forekommer inden for sammenlægningsintervallet, føjes der oplysninger om den efterfølgende hændelse til den oprindelige besked. For alle hændelser vises oplysninger om aggregerede hændelser i detaljefeltet, og det antal gange, en hændelse indtraf med sammenlægningsintervallet, vises i feltet aktivitet/antal forekomster. Du kan få vist flere oplysninger om alle forekomster af samlede hændelser ved at få vist aktivitetslisten.

På følgende skærmbillede vises en besked med fire samlede hændelser. Aktivitetslisten indeholder oplysninger om de fire mails, der er relevante for beskeden.

![Eksempel på sammenlægning af beskeder.](../media/AggregatedAlertExample.png)

Vær opmærksom på følgende ting i forbindelse med sammenlægning af beskeder:

- Beskeder, der udløses af **klik på en potentielt skadelig URL-adresse, blev registreret** [som standardbeskedpolitik](#default-alert-policies) , som ikke er samlet. Det skyldes, at beskeder, der udløses af denne politik, er entydige for hver bruger og mail.

- På nuværende tidspunkt angiver beskedegenskaben **Antal forekomster** ikke antallet af samlede hændelser for alle beskedpolitikker. For beskeder, der udløses af disse beskedpolitikker, kan du få vist de samlede hændelser ved at klikke på **Vis meddelelsesliste** eller **Vis aktivitet** for beskeden. Vi arbejder på at gøre antallet af samlede hændelser, der er angivet i beskedegenskaben **Besøgsantal** , tilgængeligt for alle politikker for beskeder.

## <a name="rbac-permissions-required-to-view-alerts"></a>RBAC-tilladelser, der kræves for at få vist beskeder

De rollebaserede Access Control-tilladelser (RBAC), der er tildelt brugerne i din organisation, bestemmer, hvilke beskeder en bruger kan se på siden **Beskeder**. Hvordan opnås dette? De administrationsroller, der er tildelt brugerne (baseret på deres medlemskab i rollegrupper på overholdelsesportalen eller på Microsoft 365 Defender-portalen), bestemmer, hvilke beskedkategorier en bruger kan se på siden **Beskeder**. Her er nogle eksempler:

- Medlemmer af rollegruppen Datastyring kan kun få vist de beskeder, der genereres af beskedpolitikker, der er tildelt kategorien **Administration af datalivscyklus** .

- Medlemmer af rollegruppen Overholdelsesadministrator kan ikke få vist beskeder, der genereres af vigtige politikker, der er tildelt kategorien **Trusselsadministration** .

- Medlemmer af rollegruppen eDiscovery Manager kan ikke få vist nogen beskeder, fordi ingen af de tildelte roller giver tilladelse til at få vist beskeder fra en hvilken som helst beskedkategori.

Dette design (baseret på RBAC-tilladelser) giver dig mulighed for at bestemme, hvilke beskeder der kan vises (og administreres) af brugere i bestemte jobroller i din organisation.

I følgende tabel vises de roller, der kræves for at få vist beskeder fra de seks forskellige beskedkategorier. Den første kolonne i tabellerne viser alle roller på overholdelsesportalen eller i Microsoft 365 Defender-portalen.  Et flueben angiver, at en bruger, der er tildelt den pågældende rolle, kan få vist beskeder fra den tilsvarende beskedkategori, der er angivet i den øverste række.

Hvis du vil se, hvilken kategori en standardbeskedpolitik er tildelt, skal du se tabellen i [Standardpolitikker for beskeder](#default-alert-policies).

|Rolle|Administration af datalivscyklus|Forebyggelse af datatab|Mailflow|Tilladelser|Trusselsstyring|Andre|
|:---------|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Overvågningslogge|||||||
|Sagsstyring|||||||
|Administrator for overholdelse af angivne standarder|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)||![Markeret.](../media/checkmark.png)||![Markeret.](../media/checkmark.png)|
|Søgning efter overholdelse|||||||
|Enhedshåndtering|||||||
|Dispositionsstyring|||||||
|Administration af DLP-overholdelse||![Markeret.](../media/checkmark.png)|||||
|eksportér|||||||
|Holde|||||||
|Information Protection analytiker||![Markeret.](../media/checkmark.png)|||||
|Information Protection investigator||![Markeret.](../media/checkmark.png)|||||
|Administrer beskeder||||||![Markeret.](../media/checkmark.png)|
|Organisationskonfiguration||||||![Markeret.](../media/checkmark.png)|
|Preview|||||||
|Postadministration|![Markeret.](../media/checkmark.png)||||||
|Opbevaringsstyring|![Markeret.](../media/checkmark.png)||||||
|Vurder|||||||
|RMS-dekryptering|||||||
|Rolleadministration||||![Markeret.](../media/checkmark.png)|||
|Søg og fjern|||||||
|Sikkerhedsadministrator||![Markeret.](../media/checkmark.png)||![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|
|Sikkerhedslæser||![Markeret.](../media/checkmark.png)||![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)
|Service Assurance-visning|||||||
|Administrator af tilsynsgennemsyn|||||||
|View-Only overvågningslogge|||||||
|View-Only Enhedshåndtering|||||||
|administration af DLP-overholdelse af View-Only||![Markeret.](../media/checkmark.png)|||||
|View-Only Administrer beskeder||||||![Markeret](../media/checkmark.png)|
|View-Only modtagere|||![Markeret](../media/checkmark.png)||||
|View-Only postadministration|![Markeret](../media/checkmark.png)||||||
|View-Only opbevaringsstyring|![Markeret](../media/checkmark.png)||||||

> [!TIP]
> Hvis du vil have vist de roller, der er tildelt til hver af standardrollegrupperne, skal du køre følgende kommandoer i Security & Compliance PowerShell:
>
> ```powershell
> $RoleGroups = Get-RoleGroup
> ```
>
> ```powershell
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,"-----------------------"; Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
>
> Du kan også få vist de roller, der er tildelt en rollegruppe, på overholdelsesportalen eller på Microsoft 365 Defender-portalen. Gå til siden **Tilladelser** , og vælg en rollegruppe. De tildelte roller vises på pop op-siden.

<a name="manage-alerts"></a>

## <a name="manage-alerts"></a>Administrer beskeder

Når beskeder er blevet genereret og vist på siden **Beskeder** på Microsoft Purview-portalen, kan du opsøge, undersøge og løse dem. De samme [RBAC-tilladelser](#rbac-permissions-required-to-view-alerts) , der giver brugerne adgang til beskeder, giver dem også mulighed for at administrere beskeder.

Her er nogle opgaver, du kan udføre for at administrere beskeder.

- **Tildel en status til beskeder.** Du kan tildele en af følgende statusser til beskeder: **Aktiv** (standardværdien), **Undersøgelse**, **Løst** eller **Afvist**. Derefter kan du filtrere denne indstilling for at få vist beskeder med den samme statusindstilling. Denne statusindstilling kan hjælpe med at spore processen til administration af beskeder.

- **Vis oplysninger om beskeder.** Du kan vælge en besked for at få vist en pop op-side med oplysninger om beskeden. De detaljerede oplysninger afhænger af den tilsvarende advarselspolitik, men de omfatter typisk følgende:

  - Navnet på den faktiske handling, der udløste beskeden, f.eks. en cmdlet- eller en overvågningsloghandling.

  - En beskrivelse af den aktivitet, der udløste beskeden.

  - Den bruger (eller liste over brugere), der udløste beskeden. Dette er kun inkluderet for beskedpolitikker, der er konfigureret til at spore en enkelt bruger eller en enkelt aktivitet.

  - Det antal gange, den aktivitet, der spores af beskeden, blev udført. Dette tal stemmer muligvis ikke overens med det faktiske antal relaterede beskeder, der er angivet på siden Beskeder, fordi der kan være udløst flere beskeder.

  - Et link til en aktivitetsliste, der indeholder et element for hver aktivitet, der blev udført, som udløste beskeden. Hver post på denne liste identificerer, hvornår aktiviteten fandt sted, navnet på den faktiske handling (f.eks. "FileDeleted"), den bruger, der udførte aktiviteten, objektet (f.eks. en fil, en eDiscovery-sag eller en postkasse), som aktiviteten blev udført på, og IP-adressen på brugerens computer. For malwarerelaterede beskeder linker dette til en meddelelsesliste.

  - Navnet (og linket) på den tilsvarende beskedpolitik.

- **Skjul mailmeddelelser.** Du kan deaktivere (eller undertrykke) mailmeddelelser fra pop op-siden for en besked. Når du undertrykker mailmeddelelser, sender Microsoft ikke meddelelser, når der forekommer aktiviteter eller hændelser, der opfylder betingelserne i beskedpolitikken. Men beskeder udløses, når aktiviteter, der udføres af brugere, stemmer overens med betingelserne i beskedpolitikken. Du kan også slå mailmeddelelser fra ved at redigere beskedpolitikken.

- **Løs beskeder.** Du kan markere en besked som løst på pop op-siden for en besked (som angiver status for beskeden til **Løst**). Medmindre du ændrer filteret, vises de løste beskeder ikke på siden **Beskeder** .

<a name="viewing-cloud-app-security-alerts"></a>

## <a name="view-defender-for-cloud-apps-alerts"></a>Vis beskeder om Defender for Cloud Apps

Beskeder, der udløses af Defender for Cloud Apps Security-politikker, vises nu på siden **Beskeder** på Microsoft Purview-portalen. Dette omfatter beskeder, der udløses af aktivitetspolitikker og beskeder, der udløses af politikker for registrering af uregelmæssigheder i Defender for Cloud Apps Security. Det betyder, at du kan få vist alle beskeder på Microsoft Purview-portalen. Defender for Cloud App Security er kun tilgængelig for organisationer med et Office 365 Enterprise E5- eller Office 365 US Government G5-abonnement. Du kan få flere oplysninger under [Oversigt over Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security).

Organisationer, der har Microsoft Defender for Cloud Apps som en del af et Enterprise Mobility + Security E5-abonnement eller som en separat tjeneste, kan også få vist Defender for Cloud Apps-beskeder, der er relateret til Microsoft 365 apps og tjenester på overholdelsesportalen eller i Microsoft 365 Defender portal.

Hvis du kun vil have vist beskeder fra Defender for Cloud Apps på Microsoft Purview-portalen eller På Defender-portalen, skal du bruge **kildefilteret** og vælge **Defender for Cloud Apps**.

![Brug kildefilteret til kun at vise beskeder om Defender for Cloud Apps.](../media/FilterCASAlerts.png)

På samme måde som med en besked, der udløses af en beskedpolitik på Microsoft Purview-portalen, kan du vælge en Defender for Cloud Apps-besked for at få vist en pop op-side med oplysninger om beskeden. Beskeden indeholder et link til at få vist detaljerne og administrere beskeden på Defender for Cloud Apps-portalen og et link til den tilsvarende Defender for Cloud Apps-politik, der udløste beskeden. Se [Overvåg beskeder i Defender for Cloud Apps](/cloud-app-security/monitor-alerts).

![Beskedoplysninger indeholder links til Defender for Cloud Apps-portalen.](../media/CASAlertDetail.png)

> [!IMPORTANT]
> Hvis du ændrer status for en besked fra Defender for Cloud Apps på Microsoft Purview-portalen, opdateres løsningsstatussen ikke for den samme besked på Defender for Cloud Apps-portalen. Hvis du f.eks. markerer status for beskeden som **Løst** på Microsoft Purview-portalen, er status for beskeden i Defender for Cloud Apps-portalen uændret. Hvis du vil løse eller afvise en besked fra Defender for Cloud Apps, skal du administrere beskeden på Defender for Cloud Apps-portalen.
