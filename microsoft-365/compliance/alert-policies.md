---
title: Microsoft 365 politikker for påmindelser
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Opret beskedpolitikker i Microsoft 365 Overholdelsescenter-portalen Microsoft 365 Defender for at overvåge potentielle trusler, datatab og problemer med tilladelser.
ms.openlocfilehash: 9137c74cd2c32539a339a9cabc2d9f66f6923636
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63587701"
---
# <a name="alert-policies-in-microsoft-365"></a>Beskedpolitikker i Microsoft 365

Du kan bruge beskedpolitikker og dashboardet til påmindelsesbeskeder i Microsoft 365 Overholdelsescenter- eller Microsoft 365 Defender-portalen til at oprette beskedpolitikker og derefter få vist de beskeder, der genereres, når brugere udfører aktiviteter, der opfylder betingelserne for en beskedpolitik. Der findes flere standardpolitikker for påmindelser, der hjælper dig med at overvåge aktiviteter som f.eks. at tildele administratorrettigheder i Exchange Online, malwareangreb, phishingkampagner og usædvanlige niveauer af filsletning og ekstern deling.

> [!TIP]
> Gå til sektionen [Standardbeskedpolitikker](#default-alert-policies) i denne artikel for at få en liste over og en beskrivelse af de tilgængelige beskedpolitikker.

Beskedpolitikker gør det muligt at kategorisere de beskeder, der udløses af en politik, anvende politikken på alle brugere i organisationen, angive en grænseværdi for, hvornår en besked udløses, og beslutte, om du vil modtage mailbeskeder, når der udløses beskeder. Der er også en beskedside, hvor du kan få vist og filtrere vigtige beskeder, angive en beskedstatus for at hjælpe dig med at administrere vigtige beskeder og derefter afvise vigtige beskeder, når du har løst eller løst den underliggende hændelse.

> [!NOTE]
> Beskedpolitikker er tilgængelige for organisationer med et Microsoft 365 Enterprise-, Office 365 Enterprise- eller Office 365 us Government E1/F1/G1-, E3/F3/G3- eller E5/G5-abonnement. Avanceret funktionalitet er kun tilgængelig for organisationer med et E5/G5-abonnement, eller for organisationer, der har et E1/F1/G1- eller E3/F3/G3-abonnement og et Microsoft Defender til Office 365 P2 eller et Microsoft 365 E5 Overholdelse- eller et E5 eDiscovery- og Overvågnings-tilføjelsesabonnement. Den funktionalitet, der kræver et E5/G5- eller tilføjelsesabonnement, er fremhævet i dette emne. Bemærk også, at påmindelsespolitikker er tilgængelige i Office 365 GCC, GCC High og DoD government-miljøer i USA.

## <a name="how-alert-policies-work"></a>Sådan fungerer påmindelsespolitikker

Her er en hurtig oversigt over, hvordan påmindelsespolitikker fungerer, og de beskeder, der udløses, når bruger- eller administratoraktivitet opfylder betingelserne i en beskedpolitik.

![Oversigt over, hvordan beskedpolitikker fungerer.](../media/M365ComplianceDefender-AlertPolicies-Overview.png)

1. En administrator i organisationen opretter, konfigurerer og aktiverer en beskedpolitik ved hjælp af siden Beskedpolitikker  i Microsoft 365 Overholdelsescenter eller Microsoft 365 Defender portalen. Du kan også oprette beskedpolitikker ved hjælp af [New-ProtectionAlert-cmdlet'en](/powershell/module/exchange/new-protectionalert) i Security & Compliance Center PowerShell.

   Hvis du vil oprette beskedpolitikker, skal du have tildelt rollen Administrer vigtige beskeder eller rollen Organisationskonfiguration på Microsoft 365 Overholdelsescenter eller Defender-portalen.

   > [!NOTE]
   > Det tager op til 24 timer efter oprettelse eller opdatering af en beskedpolitik, før beskeder kan udløses af politikken. Dette skyldes, at politikken skal synkroniseres til registreringsprogrammet til påmindelsesbeskeder.

2. En bruger udfører en aktivitet, der opfylder betingelserne i en beskedpolitik. I tilfælde af malwareangreb udløser inficeret mailbeskeder, der sendes til brugere i organisationen, en alarm.

3. Microsoft 365 genererer en besked, der vises på **siden Vigtige** beskeder på Microsoft 365 Overholdelsescenter Defender-portalen. Hvis mailmeddelelser er aktiveret for påmindelsespolitikken, sender Microsoft en meddelelse til en liste over modtagere. Beskederne om, at en administrator eller andre brugere kan se, at på siden Vigtige beskeder bestemmes af de roller, der er tildelt brugeren. Få mere at vide under [RBAC-tilladelser, der kræves for at få vist beskeder](#rbac-permissions-required-to-view-alerts).

4. En administrator administrerer beskeder i overholdelsescenteret. Administration af beskeder består i at tildele en beskedstatus for at hjælpe med at spore og administrere enhver undersøgelse.

## <a name="alert-policy-settings"></a>Politikindstillinger for besked

En beskedpolitik består af et sæt regler og betingelser, der definerer den bruger- eller administratoraktivitet, der genererer en besked, en liste over brugere, der udløser beskeden, hvis de udfører aktiviteten, og en grænseværdi, der definerer, hvor mange gange aktiviteten skal udføres, før der udløses en besked. Du kan også kategorisere politikken og tildele den et alvorsniveau. Disse to indstillinger hjælper dig med at administrere beskedpolitikker (og de beskeder, der udløses, når politikbetingelserne matches), fordi du kan filtrere disse indstillinger, når du administrerer politikker og får vist beskeder i overholdelsescenteret. Du kan f.eks. få vist beskeder, der opfylder betingelserne fra den samme kategori, eller få vist beskeder med det samme alvorsniveau.

Sådan får du vist og opretter beskedpolitikker:

### <a name="microsoft-365-compliance-center"></a>Microsoft 365 Overholdelsescenter

Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>, og vælg **derefter** **PolitikkerAlertAlert-politikker** >  > .

![I overholdelsescenteret skal du vælge Politikker, og under Besked skal du vælge Beskedpolitikker for at få vist og oprette beskedpolitikker.](../media/LaunchAlertPoliciesMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender-portal

Gå til Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">,</a> og vælg **& regler for** **&** >  **Regler under Mailsamarbejde**. Alternativt kan du gå direkte til <https://security.microsoft.com/alertpolicies>.

![I Defender-portalen skal du vælge Politikker & regler under & mailsamarbejde og derefter vælge Beskedpolitik for at få vist og oprette beskedpolitikker.](../media/LaunchAlertPoliciesDefenderPortal.png)

> [!NOTE]
> Du skal være tildelt rollen View-Only Administrer vigtige beskeder for at få vist beskedpolitikker i overholdelsescenter eller Defender-portalen. Du skal have tildelt rollen Administrer vigtige beskeder for at kunne oprette og redigere beskedpolitikker. Du kan få mere at [vide under Tilladelser i Sikkerheds- og overholdelsescenter](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

En beskedpolitik består af følgende indstillinger og betingelser.

- **Aktivitet, som beskeden registrerer**. Du opretter en politik til sporing af en aktivitet eller i nogle tilfælde et par relaterede aktiviteter, f.eks. deling af en fil med en ekstern bruger ved at dele den, tildele adgangstilladelser eller oprette et anonymt link. Når en bruger udfører den aktivitet, der er defineret af politikken, udløses en besked baseret på indstillingerne for beskedtærskelværdi.

    > [!NOTE]
    > De aktiviteter, du kan spore, afhænger af din organisations Office 365 Enterprise eller Office 365 plan for den amerikanske forvaltning. Generelt kræver aktiviteter i forbindelse med malwarekampagner og phishing-angreb et E5/G5-abonnement eller et E1/F1/G1- eller E3/F3/G3-abonnement med et [Defender til Office 365](../security/office-365-security/defender-for-office-365.md) Plan 2-tilføjelsesabonnement.

- **Aktivitetsbetingelser**. For de fleste aktiviteter kan du definere yderligere betingelser, der skal være opfyldt for at udløse en besked. Almindelige betingelser omfatter IP-adresser (så der udløses en besked, når brugeren udfører aktiviteten på en computer med en bestemt IP-adresse eller inden for et IP-adresseområde), om der udløses en besked, hvis en eller flere brugere udfører denne aktivitet, og om aktiviteten udføres på et bestemt filnavn eller url-adresse. Du kan også konfigurere en betingelse, der udløser en besked, når aktiviteten udføres af en hvilken som helst bruger i organisationen. De tilgængelige betingelser afhænger af den valgte aktivitet.

Du kan også definere brugermærker som en betingelse for en beskedpolitik. Dette resulterer i beskeder, der udløses af politikken, for at medtage konteksten for den på påvirkede bruger. Du kan bruge systembrugermærker eller brugerdefinerede brugermærker. Du kan få mere at [vide under Brugermærker i Microsoft Defender Office 365](/microsoft-365/security/office-365-security/user-tags).

- **Når beskeden udløses**. Du kan konfigurere en indstilling, der definerer, hvor ofte en aktivitet kan forekomme, før der udløses en besked. Dette giver dig mulighed for at konfigurere en politik til at generere en besked, hver gang en aktivitet opfylder politikbetingelserne, når en bestemt grænseværdi overskrides, eller når forekomsten af den aktivitet, som beskeden registrerer, bliver usædvanlig for organisationen.

    ![Konfigurer, hvordan beskeder udløses, baseret på, hvornår aktiviteten forekommer, en grænseværdi eller usædvanlig aktivitet for organisationen.](../media/howalertsaretriggered.png)

    Hvis du vælger indstillingen baseret på usædvanlig aktivitet, opretter Microsoft en oprindelig planværdi, der definerer den normale hyppighed for den valgte aktivitet. Det tager op til syv dage at oprette denne oprindelige plan, hvor der ikke genereres beskeder. Når den oprindelige plan er oprettet, udløses en besked, når hyppigheden af den aktivitet, der registreres af påmindelsespolitikken, væsentligt overstiger den oprindelige værdi. For overvågningsrelaterede aktiviteter (f.eks. fil- og mappeaktiviteter) kan du oprette en grundlinje baseret på en enkelt bruger eller baseret på alle brugere i organisationen. for malwarerelaterede aktiviteter kan du oprette en grundlinje baseret på en enkelt malwarefamilie, en enkelt modtager eller alle meddelelser i organisationen.

    > [!NOTE]
    > Muligheden for at konfigurere påmindelsespolitikker baseret på en grænseværdi eller baseret på usædvanlig aktivitet kræver et E5/G5-abonnement eller et E1/F1/G1- eller E3/F3/G3-abonnement med et Microsoft Defender til Office 365 P2-, Microsoft 365 E5 Overholdelse- eller Microsoft 365-tilføjelsesabonnement på eDiscovery og overvågning. Organisationer med et E1/F1/G1- og E3/F3/G3-abonnement kan kun oprette beskedpolitikker, hvor der udløses en besked, hver gang der sker en aktivitet.

- **Beskedkategori**. Som en hjælp til at spore og administrere de beskeder, der genereres af en politik, kan du tildele en af følgende kategorier til en politik.

  - Forebyggelse af datatab

  - Styring af oplysninger

  - Mailflow

  - Tilladelser

  - Administration af trusler

  - Andre

  Når der sker en aktivitet, der opfylder betingelserne i påmindelsespolitikken, mærkes den besked, der genereres, med den kategori, der er defineret i denne indstilling. Dette giver dig mulighed for at registrere og administrere beskeder, der har samme kategoriindstilling på siden Beskeder i **Overholdelsescenter** , fordi du kan sortere og filtrere beskeder baseret på kategori.

- **Besked alvorsgrad**. På samme måde som beskedkategorien tildeler du en alvorsattribut **(Lav****,** **Mellem**, Høj eller **Informational**) til beskedpolitikker. På samme måde som advarselskategorien mærkes den oprettede besked med det samme alvorsniveau, som er angivet for beskedpolitikken, når der sker en aktivitet, der opfylder betingelserne i beskedpolitikken. Dette giver dig også mulighed for at spore og administrere beskeder med samme alvorsgrad på **siden Beskeder** . Du kan f.eks. filtrere listen over beskeder, så kun vigtige beskeder med høj alvorsgrad vises.

    > [!TIP]
    > Når du konfigurerer en beskedpolitik, bør du overveje at tildele aktiviteter, der kan have alvorlige negative konsekvenser, f.eks. registrering af malware efter levering til brugere, visning af følsomme eller klassificerede data, deling af data med eksterne brugere eller andre aktiviteter, der kan medføre tab af data eller sikkerhedstrusler. Dette kan hjælpe dig med at prioritere beskeder og de handlinger, du tager for at undersøge og løse de underliggende årsager.

- **Automatiserede undersøgelser**. Nogle beskeder vil udløse automatiserede undersøgelser for at identificere potentielle trusler og risici, der skal afhjælpes eller afhjælpes.  I de fleste tilfælde udløses disse beskeder ved registrering af skadelige mails eller aktiviteter, men i nogle tilfælde udløses beskederne af administratorhandlinger på sikkerhedsportalen.  Du kan finde flere oplysninger om automatiserede undersøgelser [i Automatiseret undersøgelse og svar (AIR) i Microsoft Defender Office 365](../security/office-365-security/office-365-air.md).

- **Mailbeskeder**. Du kan konfigurere politikken, så mailbeskeder sendes (eller ikke sendes) til en liste over brugere, når der udløses en besked. Du kan også angive en daglig grænse for meddelelser, så der ikke sendes flere meddelelser for den pågældende dag, når det maksimale antal meddelelser er nået. Ud over mailbeskeder kan du eller andre administratorer se de beskeder, der udløses af en politik på **siden Vigtige** beskeder. Overvej at aktivere mailbeskeder for beskedpolitikker for en bestemt kategori, eller som har en højere alvorsgrad.

## <a name="default-alert-policies"></a>Standardbeskedpolitikker

Microsoft leverer indbyggede politikker for påmindelser, der hjælper med at identificere Exchange misbrug af administratortilladelser, malwareaktivitet, potentielle eksterne og interne trusler og risici i forbindelse med informationsstyring. På siden **Påmindelsespolitikker** står navnene på disse indbyggede politikker med fed skrift, og politiktypen er defineret som **System**. Disse politikker er som standard slået til. Du kan deaktivere disse politikker (eller slå dem til igen), konfigurere en liste over modtagere, der skal sendes mailbeskeder til, og angive en daglig beskedgrænse. De andre indstillinger for disse politikker kan ikke redigeres.

Følgende tabel viser og beskriver de tilgængelige standardbeskedpolitikker og den kategori, som hver politik er tildelt til. Kategorien bruges til at bestemme, hvilke beskeder en bruger kan få vist på siden Vigtige beskeder. Få mere at vide under [RBAC-tilladelser, der kræves for at få vist beskeder](#rbac-permissions-required-to-view-alerts).

Tabellen angiver også den Office 365 Enterprise og Office 365 amerikanske regerings plan, der kræves for hver enkelt. Nogle standardbeskedpolitikker er tilgængelige, hvis din organisation har det relevante tilføjelsesabonnement ud over et E1/F1/G1- eller E3/F3/G3-abonnement.
 
| Standardbeskedpolitik | Beskrivelse | Kategori | Automatiseret undersøgelse | Enterprise-abonnement |
|:-----|:-----|:-----|:-----|:-----|
|**Der blev fundet et potentielt ondsindet klik på webadressen**|Genererer en besked, når en bruger er [beskyttet af Pengeskab links](../security/office-365-security/safe-links.md) i organisationen klikker på et skadeligt link. Hændelsen udløses, når ændringer i webadressens konklusion identificeres af Microsoft Defender for Office 365, eller når brugere tilsidesætter siderne Pengeskab Links (baseret på organisationens politik for Microsoft 365 for business Pengeskab Links). Denne beskedpolitik har en **indstilling med** høj alvorsgrad. For Defender til Office 365 P2, E5 og G5-kunder udløser denne besked automatisk automatiseret undersøgelse og [reaktion Office 365](../security/office-365-security/office-365-air.md). Du kan finde flere oplysninger om hændelser, der udløser denne besked, [under Konfigurer Pengeskab links-politikker](../security/office-365-security/set-up-safe-links-policies.md).|Administration af trusler|Ja|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Administratorafsendelsesresultat fuldført**|Genererer en besked, når [en administratorafsendelse](../security/office-365-security/admin-submission.md) fuldfører kanden for den indsendte enhed. Der udløses en besked, hver gang et genscanne resultat gengives fra en administratorindsendelse. Disse beskeder er beregnet til at minde dig om at gennemgå resultaterne af tidligere indsendelser [, sende](https://compliance.microsoft.com/reportsubmission) brugerrapporterede meddelelser for at få den seneste politikkontrol og genangivelsesresultater og hjælpe dig med at afgøre, om filtreringspolitikkerne i din organisation har den tilsigtede virkning. Denne politik har en **indstilling for alvorlighed** for oplysninger.|Administration af trusler|Nej|E1/F1, E3/F3 eller E5|
|**Administratoren har udløst en manuel undersøgelse af mails**|Genererer en besked, når en administrator udløser den manuelle undersøgelse af en mail fra Threat Explorer. Få mere at vide under [Eksempel: En sikkerhedsadministrator udløser en undersøgelse fra Threat Explorer](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer). Denne advarsel giver din organisation besked om, at undersøgelsen blev startet. Beskeden indeholder oplysninger om, hvem der har udløst den, og indeholder et link til undersøgelsen. Denne politik har en **indstilling for alvorlighed** for oplysninger.|Administration af trusler|Ja|E5/G5 eller Microsoft Defender til Office 365 P2-tilføjelsesabonnement|
|**Administrator udløst undersøgelse af brugerforlig**|Genererer en besked, når en administrator udløser den manuelle undersøgelse af brugeres kompromis med enten en mailafsender eller en modtager fra Threat Explorer. Få mere at vide under [Eksempel: En sikkerhedsadministrator](../security/office-365-security/automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer) udløser en undersøgelse fra Threat Explorer, som viser den relaterede manuelle igangsættelse af en undersøgelse af en mail. Denne advarsel giver din organisation besked om, at undersøgelsen af brugerforlig blev startet. Beskeden indeholder oplysninger om, hvem der har udløst den, og indeholder et link til undersøgelsen. Denne politik har en **indstilling af** typen Mellem alvorlighed.|Administration af trusler|Ja|E5/G5 eller Microsoft Defender til Office 365 P2-tilføjelsesabonnement|
|**Oprettelse af regel for videresendelse/omdirigering**|Genererer en besked, når en person i organisationen opretter en indbakkeregel for sin postkasse, som videresender eller omdirigerer meddelelser til en anden mailkonto. Denne politik registrerer kun indbakkeregler, der er oprettet ved hjælp Outlook på internettet (tidligere kaldet Outlook Web App) eller Exchange Online PowerShell. Denne politik har en **indstilling for alvorlighed** for oplysninger. Du kan finde flere oplysninger om brug af indbakkeregler til at videresende og omdirigere mail i Outlook på internettet i Brug regler i [Outlook på internettet til automatisk at videresende meddelelser til en anden konto](https://support.office.com/article/1433e3a0-7fb0-4999-b536-50e05cb67fed).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**eDiscovery-søgning startet eller eksporteret**|Genererer en besked, når nogen bruger værktøjet indholdssøgning i Security and compliance Center. Der udløses en besked, når følgende aktiviteter for indholdssøgning udføres: <br><br> <li> En indholdssøgning startes <li> Resultaterne af en indholdssøgning eksporteres <li> En rapport for indholdssøgning eksporteres <br><br> Beskeder udløses også, når de tidligere aktiviteter til indholdssøgning udføres i forbindelse med en eDiscovery-sag. Denne politik har en **indstilling for alvorlighed** for oplysninger. Du kan finde flere oplysninger om indholdssøgningsaktiviteter [under Søge efter eDiscovery-aktiviteter i overvågningsloggen](search-for-ediscovery-activities-in-the-audit-log.md#ediscovery-activities).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Udvidelse af Exchange administratorrettigheder**|Genererer en besked, når en person tildeles administrative tilladelser i Exchange Online organisation. Når en bruger f.eks. føjes til rollegruppen Organisationsadministration i Exchange Online. Denne politik har en **indstilling** med lav alvorsgrad.|Tilladelser|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Mails, der indeholder skadelig fil fjernet efter levering**|Genererer en besked, når meddelelser, der indeholder en skadelig fil, leveres til postkasser i organisationen. Hvis denne hændelse sker, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser ved hjælp [af automatisk Tømning i nul-time](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en **informations alvorsgrad** og udløser automatisk [undersøgelse og svar Office 365](../security/office-365-security/office-365-air.md). Du kan finde flere oplysninger om denne nye politik [i Nye beskedpolitikker i Microsoft Defender Office 365](new-defender-alert-policies.md).|Administration af trusler|Ja|E5/G5 eller Microsoft Defender til Office 365 P2-tilføjelsesabonnement|
|**Mails, der indeholder skadelig URL-adresse fjernet efter levering**|Genererer en besked, når meddelelser, der indeholder en skadelig URL-adresse, leveres til postkasser i organisationen. Hvis denne hændelse sker, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser ved hjælp [af automatisk Tømning i nul-time](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en **informations alvorsgrad** og udløser automatisk [undersøgelse og svar Office 365](../security/office-365-security/office-365-air.md). Du kan finde flere oplysninger om denne nye politik [i Nye beskedpolitikker i Microsoft Defender Office 365](new-defender-alert-policies.md).|Administration af trusler|Ja|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Mails fra en kampagne, der er fjernet efter levering**|Genererer en besked, når alle meddelelser, der er [knyttet til](../security/office-365-security/campaigns.md) en kampagne, leveres til postkasser i organisationen. Hvis denne hændelse sker, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser ved hjælp [af automatisk Tømning i nul-time](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en **informations alvorsgrad** og udløser automatisk [undersøgelse og svar Office 365](../security/office-365-security/office-365-air.md). Du kan finde flere oplysninger om denne nye politik [i Nye beskedpolitikker i Microsoft Defender Office 365](new-defender-alert-policies.md).|Administration af trusler|Ja|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Mails fjernet efter levering**|Genererer en besked, når skadelige meddelelser, der ikke indeholder en ondsindet enhed (URL eller fil), eller som er knyttet til en kampagne, leveres til postkasser i organisationen. Hvis denne hændelse sker, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser ved hjælp [af automatisk Tømning i nul-time](../security/office-365-security/zero-hour-auto-purge.md). Denne politik har en **informations alvorsgrad** og udløser automatisk [undersøgelse og svar Office 365](../security/office-365-security/office-365-air.md). Du kan finde flere oplysninger om denne nye politik [i Nye beskedpolitikker i Microsoft Defender Office 365](new-defender-alert-policies.md).|Administration af trusler|Ja|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Mail rapporteret af bruger som malware eller phish**|Genererer en besked, når brugere i organisationen rapporterer meddelelser som phishingmail ved hjælp af tilføjelsesprogrammet Rapportmeddelelse. Denne politik har en **indstilling** med lav alvorsgrad. Du kan finde flere oplysninger om dette tilføjelsesprogrammet [under Brug af tilføjelsesprogrammet Rapportmeddelelse](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2). For Defender til Office 365 P2, E5 og G5-kunder udløser denne besked automatisk automatiseret undersøgelse og [reaktion Office 365](../security/office-365-security/office-365-air.md).|Administration af trusler|Ja|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Grænse for afsendelse af mail er overskredet**|Genererer en besked, når en person i organisationen har sendt mere mail, end det tillades af politikken for udgående spam. Dette indikerer som regel, at brugeren sender for mange mails, eller at kontoen kan blive kompromitteret. Denne politik har en **indstilling af** typen Mellem alvorlighed. Hvis du får en besked genereret af denne beskedpolitik, er det en god ide at [kontrollere, om brugerkontoen er kompromitteret](../security/office-365-security/responding-to-a-compromised-email-account.md).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Formular blokeret på grund af potentielt forsøg på phishing**|Genererer en besked, når en person i organisationen er blevet begrænset fra delingsformularer og indsamling af svar ved hjælp af Microsoft Forms på grund af registreret gentagen adfærd i forbindelse med forsøg på phishing. Denne politik har en **indstilling med høj alvorsgrad** .|Administration af trusler|Nej|E1, E3/F3 eller E5|
|**Formular markeret med flag og bekræftet som phishing**|Genererer en besked, når en formular, der er oprettet i Microsoft Forms fra din organisation, er blevet identificeret som potentielt phishing via Rapportér misbrug og bekræftet som phishing af Microsoft. Denne politik har en **indstilling med** høj alvorsgrad.|Administration af trusler|Nej|E1, E3/F3 eller E5|
|**Meddelelser er forsinkede**|Genererer en besked, når Microsoft ikke kan levere mails til din lokale organisation eller en partnerserver ved hjælp af en forbindelse. Når dette sker, er meddelelsen i kø i Office 365. Denne besked udløses, når der er 2.000 meddelelser eller flere, der er sat i kø i mere end en time. Denne politik har en **indstilling med** høj alvorsgrad.|Mailflow|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Malwarekampagne registreret efter levering**|Genererer en besked, når et usædvanligt stort antal meddelelser, der indeholder malware, leveres til postkasser i organisationen. Hvis denne hændelse sker, fjerner Microsoft de inficeret meddelelser fra Exchange Online postkasser. Denne politik har en **indstilling med** høj alvorsgrad.|Administration af trusler|Nej|E5/G5 eller Microsoft Defender til Office 365 P2-tilføjelsesabonnement|
|**Malwarekampagner, der registreres og blokeres**|Genererer en besked, når nogen har forsøgt at sende et usædvanligt stort antal mails, der indeholder en bestemt type malware, til brugere i organisationen. Hvis denne hændelse indtræffer, blokeres de inficeret meddelelser af Microsoft og leveres ikke til postkasser. Denne politik har en **indstilling** med lav alvorsgrad.|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Malwarekampagner registreret i SharePoint og OneDrive**|Genererer en besked, når der registreres en usædvanlig stor mængde malware eller virus i filer, der er placeret på SharePoint-websteder eller OneDrive-konti i organisationen. Denne politik har en **indstilling med** høj alvorsgrad.|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Malware er ikke zappet, fordi ZAP er deaktiveret**| Genererer en besked, når Microsoft registrerer levering af en malwaremeddelelse til en postkasse, fordi Zero-Hour automatisk tømning af phish-meddelelser er deaktiveret. Denne politik har en **indstilling for alvorlighed** for oplysninger. |Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Phish leveret, fordi en brugers mappe uønsket mail er deaktiveret**|Genererer en besked, når Microsoft registrerer, at en brugers mappe med Uønsket mail er deaktiveret, hvilket tillader levering af en phishing-meddelelse med høj genkendelse til en postkasse. Denne politik har en **indstilling for alvorlighed** for oplysninger.|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Phish leveret på grund af en etr-tilsidesættelse**|Genererer en besked, når Microsoft registrerer en Exchange-transportregel (ETR), der tillod levering af en phishing-meddelelse med høj tillid til en postkasse. Denne politik har en **indstilling for alvorlighed** for oplysninger. Du kan finde flere Exchange om transportregler (regler for mailflow) i [Regler for mailflow (transportregler) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Phish leveret på grund af en IP-tilladelsespolitik**|Genererer en besked, når Microsoft registrerer en politik for tilladt IP-adresser, der tillader levering af en phishing-meddelelse med høj tillid til en postkasse. Denne politik har en **indstilling for alvorlighed** for oplysninger. Du kan finde flere oplysninger om politikken for tilladte IP-adresser (forbindelsesfiltrering) under Konfigurer standardfilterpolitikken [for forbindelse – Office 365](../security/office-365-security/configure-the-connection-filter-policy.md).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Phish er ikke zappet, fordi ZAP er deaktiveret**| Genererer en besked, når Microsoft registrerer levering af en phishing-meddelelse med høj tillid til en postkasse, fordi Zero-Hour Automatisk tømning af phish-meddelelser er deaktiveret. Denne politik har en **indstilling for alvorlighed** for oplysninger.|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Phish leveret på grund af lejer- eller brugertilsidesættelse1**<sup></sup>|Genererer en besked, når Microsoft registrerer en administrator eller bruger tilsidesætter tilladt levering af en phishing-meddelelse til en postkasse. Eksempler på tilsidesættelser omfatter en indbakke eller regel for mailflow, der tillader meddelelser fra en bestemt afsender eller et bestemt domæne, eller en antispampolitik, der tillader meddelelser fra bestemte afsendere eller domæner. Denne politik har en **indstilling med** høj alvorsgrad.|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Mistænkelig videresendelse af mail**|Genererer en besked, når en person i organisationen automatisk har sendt mail til en mistænkelig ekstern konto. Dette er en tidlig advarsel for funktionsmåde, der kan betyde, at kontoen er kompromitteret, men ikke alvorlig nok til at begrænse brugeren. Denne politik har en **indstilling med** høj alvorsgrad. Selvom det er sjældent, kan en besked, der genereres af denne politik, være en anomali. Det er en god ide at [kontrollere, om brugerkontoen er kompromitteret](../security/office-365-security/responding-to-a-compromised-email-account.md).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Mistænkelige e-mail-afsendelsesmønstre registreret**|Genererer en besked, når en person i organisationen har sendt mistænkelige mails og er i risiko for at blive begrænset fra at sende mails. Dette er en tidlig advarsel for adfærd, der kan betyde, at kontoen er kompromitteret, men ikke alvorlig nok til at begrænse brugeren. Denne politik har en **indstilling af** typen Mellem alvorlighed. Selvom det er sjældent, kan en besked, der genereres af denne politik, være en anomali. Det er dog en god ide at [kontrollere, om brugerkontoen er kompromitteret](../security/office-365-security/responding-to-a-compromised-email-account.md).|Administration af trusler|Ja|E1/F1/G1, E3/F3/G3 eller E5/G5  |
|**Lejers tilladelses-/blokeringslistepost er ved at udløbe**|Genererer en besked, når en lejers tilladelses-/blokeringslistepost er ved at blive fjernet. Denne hændelse udløses tre dage før udløbsdatoen, som er baseret på, hvornår posten blev oprettet eller senest opdateret. Denne beskedpolitik har en **indstilling for alvorlighed** for oplysninger. Dette er for at informere administratorer om kommende ændringer i filtrene, da tilladelses- eller blokeringen muligvis forsvinder. For blokke kan du forlænge udløbsdatoen for at holde blokken på plads. For allows skal du sende elementet igen, så vores analytikere kan se nærmere på det. Men hvis tillad allerede er blevet givet som en falsk positiv, så udløber posten kun, når systemfiltrene er blevet opdateret til naturligt at tillade indtastningen. Du kan finde flere oplysninger om hændelser, der udløser denne besked, [under Administrere listen lejer tillade/blokere](../security/office-365-security/tenant-allow-block-list.md).|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Lejer er begrænset i at kunne sende mails**|Genererer en besked, når det meste af mailtrafik fra din organisation er blevet registreret som mistænkelig, og Microsoft har begrænset din organisation i at sende mails. Undersøg potentielt kompromitterede bruger- og administratorkonti, nye forbindelser eller åbne relæer, og kontakt derefter Microsoft Support for at fjerne blokeringen af organisationen. Denne politik har en **indstilling med** høj alvorsgrad. Du kan finde flere oplysninger om, hvorfor organisationer blokeres, under Løs problemer med levering af mail [for fejlkode 5.7.7xx Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Lejer er begrænset i at sende ikke-klassificerede mails**|Genererer en besked, når der sendes for mange mails fra ikke-registrerede domæner (også kaldet *ikke-registrerede* domæner). Office 365 tillader en rimelig mængde mail fra ikke-registrerede domæner, men du skal konfigurere hvert domæne, som du bruger til at sende mail som et accepteret domæne. Denne besked angiver, at alle brugere i organisationen ikke længere kan sende mails. Denne politik har en **indstilling med** høj alvorsgrad. Du kan finde flere oplysninger om, hvorfor organisationer blokeres, under Løs problemer med levering af mail [for fejlkode 5.7.7xx Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-7-700-through-5-7-750).|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Usædvanlig filaktivitet for eksterne brugere**|Genererer en besked, når et usædvanligt stort antal aktiviteter udføres på filer i SharePoint eller OneDrive af brugere uden for organisationen. Dette omfatter aktiviteter som adgang til filer, overførsel af filer og sletning af filer. Denne politik har en **indstilling med** høj alvorsgrad.|Styring af oplysninger|Nej|E5/G5, Microsoft Defender Office 365 P2 eller Microsoft 365 E5-tilføjelsesabonnement|
|**Usædvanlig volumen af ekstern fildeling**|Genererer en besked, når et usædvanligt stort antal filer i SharePoint eller OneDrive deles med brugere uden for organisationen. Denne politik har en **indstilling af** typen Mellem alvorlighed.|Styring af oplysninger|Nej|E5/G5, Defender til Office 365 P2 eller Microsoft 365 E5-tilføjelsesabonnement|
|**Usædvanlig volumensletning af filer**|Genererer en besked, når et usædvanligt stort antal filer slettes i SharePoint eller OneDrive inden for en kort tidsramme. Denne politik har en **indstilling af** typen Mellem alvorlighed.|Styring af oplysninger|Nej|E5/G5, Defender til Office 365 P2 eller Microsoft 365 E5-tilføjelsesabonnement|
|**Usædvanlig stigning i mail rapporteret som phish**|Genererer en besked, når der er en betydelig stigning i antallet af personer i organisationen, der bruger tilføjelsesprogrammet Rapportmeddelelse i Outlook til at rapportere meddelelser som phishingmail. Denne politik har en **indstilling af** typen Mellem alvorlighed. Du kan finde flere oplysninger om dette tilføjelsesprogrammet [under Brug af tilføjelsesprogrammet Rapportmeddelelse](https://support.office.com/article/b5caa9f1-cdf3-4443-af8c-ff724ea719d2).|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Bruger efterligning phish leveret til indbakke/**<sup>mappe1,2</sup><sup></sup>|Genererer en besked, når Microsoft registrerer, at en administrator eller brugertilsidesættelse har tilladt levering af en bruger efter phishing-meddelelse til indbakken (eller en anden brugervenlig mappe) i en postkasse. Eksempler på tilsidesættelser omfatter en indbakke eller regel for mailflow, der tillader meddelelser fra en bestemt afsender eller et bestemt domæne, eller en antispampolitik, der tillader meddelelser fra bestemte afsendere eller domæner. Denne politik har en **indstilling af** typen Mellem alvorlighed.|Administration af trusler|Nej|E5/G5 eller Defender Office 365 P2-tilføjelsesabonnement|
|**Brugeren har anmodet om at frigive en meddelelse i karantæne**|Genererer en besked, når en bruger anmoder om frigivelse af en meddelelse i karantæne. Hvis du vil anmode om frigivelse af meddelelser, der er sat i karantæne, skal tilladelsen Tillad, at modtagerne anmoder om at få en meddelelse frigivet fra **karantæne (**_PermissionToRequestRelease_) være påkrævet i karantænepolitikken (f.eks. fra gruppen Begrænsede adgangsindstillinger for forudindstillede tilladelser). Få mere at vide under [Tillad, at modtagere anmoder om, at en meddelelse frigives fra karantænetilladelse.](../security/office-365-security/quarantine-policies.md#allow-recipients-to-request-a-message-to-be-released-from-quarantine-permission) Denne politik har en **indstilling for alvorlighed** for oplysninger.|Administration af trusler|Nej|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Brugeren er begrænset i at sende mail**|Genererer en besked, når en person i organisationen er begrænset i at kunne sende udgående mail. Dette resulterer typisk, når en konto er kompromitteret, og brugeren er angivet på siden **Begrænsede** brugere i Microsoft 365 Overholdelsescenter. (For at få adgang til denne side skal du **gå til > Gennemse > Begrænsede brugere**). Denne politik har en **indstilling med** høj alvorsgrad. Du kan finde flere oplysninger om begrænsede brugere i [Fjerne en bruger, et domæne eller en IP-adresse fra en liste over blokerede afsendere efter afsendelse af spammail](/office365/securitycompliance/removing-user-from-restricted-users-portal-after-spam).|Administration af trusler|Ja|E1/F1/G1, E3/F3/G3 eller E5/G5|
|**Bruger begrænset fra delingsformularer og indsamling af svar**|Genererer en besked, når en person i organisationen er blevet begrænset fra delingsformularer og indsamling af svar ved hjælp af Microsoft Forms på grund af registreret gentagen adfærd i forbindelse med forsøg på phishing. Denne politik har en **indstilling med** høj alvorsgrad.|Administration af trusler|Nej|E1, E3/F3 eller E5|

> [!NOTE]
> <sup>1</sup> Vi har midlertidigt fjernet denne standardbeskedpolitik baseret på kundefeedback. Vi arbejder på at forbedre det og vil erstatte det med en ny version i den nærmeste fremtid. Indtil da kan du oprette en brugerdefineret politik til at erstatte denne funktion ved hjælp af følgende indstillinger: <ul><li>Aktivitet er Phish-mail registreret på leveringstidspunktet</li> <li>Mail er ikke ZAP'd</li> <li>Mailretning er indgående</li> <li>Status for levering af mail er Leveret</li> <li>Registreringsteknologien er Opbevaring af skadelig URL-adresse, URL-detonation, avanceret phish-filter, generel phish-filter, domænepersonation, bruger efterligning og brand-efterligning</li></ul> Du kan finde flere oplysninger om antiphishing i Office 365 i [Konfigurer politikker for antiphishing og antiphishing](../security/office-365-security/set-up-anti-phishing-policies.md).<br/><br/><sup>2 Hvis</sup> du vil genskabe denne beskedpolitik, skal du følge vejledningen i den forrige fodnote, men vælge Bruger efterligning som den eneste registreringsteknologi.

Den usædvanlige aktivitet, der overvåges af nogle af de indbyggede politikker, er baseret på den samme proces som den indstilling for beskedtærskelværdi, der er blevet beskrevet tidligere. Microsoft opretter en oprindelig værdi, der definerer den normale hyppighed for "normal" aktivitet. Beskeder udløses derefter, når hyppigheden af aktiviteter, der registreres af den indbyggede beskedpolitik, væsentligt overstiger den oprindelige værdi.

<a name="viewing-alerts"></a>

## <a name="view-alerts"></a>Få vist beskeder

Når en aktivitet, der udføres af brugerne i organisationen, svarer til indstillingerne i en beskedpolitik, genereres der en besked, som vises på siden Vigtige beskeder i **overholdelsescenteret** eller på Defender-portalen. Afhængigt af indstillingerne for en beskedpolitik sendes der også en mailbesked til en liste over bestemte brugere, når der udløses en besked. For hver besked viser dashboardet på siden Beskeder navnet på den tilsvarende beskedpolitik, alvorsgrad og kategori for beskeden (defineret i politikken for **påmindelsesbeskeder** ), og det antal gange en aktivitet har resulteret i, at beskeden blev genereret. Denne værdi er baseret på tærskelindstillingen for beskedpolitikken. Dashboardet viser også status for hver besked. Du kan finde flere oplysninger om, hvordan du bruger statusegenskaben til at administrere beskeder [, under Administrere beskeder](#manage-alerts).

Sådan får du vist beskeder:

### <a name="microsoft-365-compliance-center"></a>Microsoft 365 Overholdelsescenter

 Gå til <https://compliance.microsoft.com> , og vælg **derefter Beskeder**. Alternativt kan du gå direkte til <https://compliance.microsoft.com/compliancealerts>.

![Vælg Microsoft 365 Overholdelsescenter i dialogboksen Beskeder.](../media/ViewAlertsMCC.png)

### <a name="microsoft-365-defender-portal"></a>Microsoft 365 Defender-portal

Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, **og vælg & hændelser og** **beskederAlerts** > . Alternativt kan du gå direkte til <https://security.microsoft.com/alerts>.

![I Microsoft 365 Defender skal du vælge Hændelser & beskeder og derefter vælge Beskeder.](../media/ViewAlertsDefenderPortal.png)

Du kan bruge følgende filtre til at få vist et undersæt af alle beskederne **på siden Vigtige** beskeder.

- **Status.** Brug dette filter til at få vist beskeder, der er tildelt en bestemt status. Standardstatus er **Aktiv**. Du eller andre administratorer kan ændre statusværdien.

- **Politik.** Brug dette filter til at få vist beskeder, der svarer til indstillingen af en eller flere beskedpolitikker. Eller du kan få vist alle beskeder for alle beskedpolitikker.

- **Tidsinterval.** Brug dette filter til at få vist beskeder, der er oprettet inden for et bestemt dato- og tidsinterval.

- **Alvorsgrad.** Brug dette filter til at få vist beskeder, der er tildelt en bestemt alvorsgrad.

- **Kategori.** Brug dette filter til at vise beskeder fra én eller flere beskedkategorier.

- **Mærker.** Brug dette filter til at vise beskeder fra en eller flere brugermærker. Mærker afspejles baseret på mærkede postkasser eller brugere, der vises i beskederne. Se [Brugermærker i Office 356 ATP for at](../security/office-365-security/user-tags.md) få mere at vide.

- **Kilde.** Brug dette filter til at vise beskeder, der udløses af påmindelsespolitikker i overholdelsescenteret, eller til beskeder, der Office 365 Cloud App Security eller begge dele. Du kan finde flere oplysninger Office 365 Cloud App Security om vigtige beskeder i [Visning af Defender for skyapps-beskeder](#viewing-cloud-app-security-alerts).

> [!IMPORTANT]
> Filtrering og sortering efter brugermærker er i øjeblikket offentlig prøveversion.
> Den kan være væsentligt ændret, før den frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har om det.

## <a name="alert-aggregation"></a>Akkumulering af beskeder

Når flere hændelser, der opfylder betingelserne i en beskedpolitik, sker med en kort tidsperiode, føjes de til en eksisterende besked via en proces kaldet sammenlægning *af beskeder*. Når en hændelse udløser en besked, genereres beskeden og vises på **siden Vigtige beskeder** , og der sendes en meddelelse. Hvis den samme hændelse forekommer inden for aggregeringsintervallet, føjer Microsoft 365 oplysninger om den nye hændelse til den eksisterende besked i stedet for at udløse en ny besked. Formålet med sammenlægning af beskeder er at reducere advarsel "træthed" og lade dig fokusere og handle på færre beskeder for den samme begivenhed.

Længden på sammenlægningsintervallet afhænger af dit Office 365 eller Microsoft 365 abonnement.

|Abonnement|Akkumuleringsinterval|
|:---------|:---------:|
|Office 365 eller Microsoft 365 E5/G5|1 minut|
|Defender til Office 365 Plan 2 |1 minut|
|Tilføjelsesprogrammet Overholdelse af E5 eller tilføjelsesprogrammet E5 Discovery and Audit|1 minut|
|Office 365 eller Microsoft 365 E1/F1/G1 eller E3/F3/G3|15 minutter|
|Defender til Office 365 Plan 1 eller Exchange Online Protection|15 minutter|

Når hændelser, der stemmer overens med den samme beskedpolitik, sker inden for akkumuleringsintervallet, føjes oplysninger om den efterfølgende hændelse til den oprindelige besked. For alle hændelser vises oplysninger om aggregerede hændelser i detaljefeltet, og antallet af gange, en hændelse med sammenlægningsintervallet vises i feltet aktivitet/hitantal. Du kan få vist flere oplysninger om alle aggregerede hændelsesforekomster ved at få vist aktivitetslisten.

Følgende skærmbillede viser en besked med fire samlede hændelser. Aktivitetslisten indeholder oplysninger om de fire mails, der er relevante for beskeden.

![Eksempel på sammenlægning af beskeder.](../media/AggregatedAlertExample.png)

Vær opmærksom på følgende i forbindelse med aggregering af beskeder:

- Beskeder udløst af et potentielt ondsindet **klik på en URL-adresse blev registreret**[, at standardbeskedpolitikken](#default-alert-policies) ikke aggregeres. Dette skyldes, at beskeder, der udløses af denne politik, er unikke for hver bruger og mail.

- På nuværende tidspunkt angiver **egenskaben Hit Count** ikke antallet af samlede hændelser for alle beskedpolitikker. For beskeder, der er udløst af disse politikker, kan du få vist de aggregerede hændelser  ved at klikke på Vis meddelelsesliste eller **Vis aktivitet** for beskeden. Vi arbejder på at gøre antallet af aggregerede hændelser, der vises i egenskaben **Hit count** alert, tilgængelig for alle beskedpolitikker.

## <a name="rbac-permissions-required-to-view-alerts"></a>RBAC-tilladelser, der kræves for at få vist beskeder

RBAC-tilladelser (Role Based Access Control), der er tildelt til brugere i organisationen, afgør, hvilke beskeder en bruger kan se **på siden Vigtige** beskeder. Hvordan opnår man dette? De administrationsroller, der er tildelt til brugere (baseret på deres medlemskab af rollegrupper i Microsoft 365 Overholdelsescenter- eller Microsoft 365 Defender-portalen) bestemmer, hvilke beskedkategorier en bruger kan se på siden **Vigtige beskeder.** Her er nogle eksempler:

- Medlemmer af rollegruppen Datastyring kan kun få vist de beskeder, der genereres af beskedpolitikker, der er tildelt kategorien **Til styring af** oplysninger.

- Medlemmer af rollegruppen Overholdelsesadministrator kan ikke få vist beskeder, der genereres af beskedpolitikker, der er tildelt **kategorien Trusselsadministration** .

- Medlemmer af rollegruppen eDiscovery Manager kan ikke få vist vigtige beskeder, fordi ingen af de tildelte roller giver tilladelse til at få vist vigtige beskeder fra en hvilken som helst beskedkategori.

Med dette design (baseret på RBAC-tilladelser) kan du bestemme, hvilke beskeder der kan vises (og administreres) af brugere i bestemte jobroller i organisationen.

I følgende tabel vises de roller, der kræves for at få vist beskeder fra de seks forskellige beskedkategorier. I den første kolonne i tabellerne vises alle roller i Microsoft 365 Overholdelsescenter eller Microsoft 365 Defender portalen.  En markering angiver, at en bruger, der er tildelt den rolle, kan få vist beskeder fra den tilsvarende beskedkategori, der er angivet i den øverste række.

Hvis du vil se, hvilken kategori der er tildelt en standardbeskedpolitik, skal du se tabellen i [Standardbeskedpolitikker](#default-alert-policies).

|Rolle|Styring af oplysninger|Forebyggelse af datatab|Mailflow|Tilladelser|Administration af trusler|Andre|
|:---------|:---------:|:---------:|:---------:|:---------:|:---------:|:---------:|
|Overvågningslogfiler|||||||
|Sagsadministration|||||||
|Overholdelsesadministrator|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)||![Markering.](../media/checkmark.png)||![Markering.](../media/checkmark.png)|
|Søgning i overholdelse af regler og standarder|||||||
|Enhedshåndtering|||||||
|Dispositionsstyring|||||||
|Administration af DLP-overholdelse||![Markering.](../media/checkmark.png)|||||
|eksportér|||||||
|Venteposition|||||||
|Information Protection-analytiker||![Markering.](../media/checkmark.png)|||||
|Information Protection Investigator||![Markering.](../media/checkmark.png)|||||
|Administrer beskeder||||||![Markering.](../media/checkmark.png)|
|Organisationskonfiguration||||||![Markering.](../media/checkmark.png)|
|Eksempel|||||||
|Datastyring|![Markering.](../media/checkmark.png)||||||
|Opbevaringsstyring|![Markering.](../media/checkmark.png)||||||
|Gennemse|||||||
|RMS Dekrypter|||||||
|Rollestyring||||![Markering.](../media/checkmark.png)|||
|Søg og tøm|||||||
|Sikkerhedsadministrator||![Markering.](../media/checkmark.png)||![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|
|Sikkerhedslæser||![Markering.](../media/checkmark.png)||![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)
|Tjenestesikringsvisning|||||||
|Administrator for kontrolvurdering|||||||
|View-Only overvågningslogfiler|||||||
|View-Only af enheder|||||||
|View-Only DLP-overholdelsesstyring||![Markering.](../media/checkmark.png)|||||
|View-Only Administrer beskeder||||||![Markering](../media/checkmark.png)|
|View-Only modtagere|||![Markering](../media/checkmark.png)||||
|View-Only datastyring|![Markering](../media/checkmark.png)||||||
|View-Only opbevaringsstyring|![Markering](../media/checkmark.png)||||||

> [!TIP]
> Hvis du vil have vist de roller, der er tildelt hver af standardrollegrupperne, skal du køre følgende kommandoer i Security & Compliance Center PowerShell:
>
> ```powershell
> $RoleGroups = Get-RoleGroup
> ```
>
> ```powershell
> $RoleGroups | foreach {Write-Output -InputObject `r`n,$_.Name,"-----------------------"; Get-RoleGroup $_.Identity | Select-Object -ExpandProperty Roles}
> ```
>
> Du kan også se de roller, der er tildelt en rollegruppe i Microsoft 365 Overholdelsescenter eller Microsoft 365 Defender portalen. Gå til siden **Tilladelser** , og vælg en rollegruppe. De tildelte roller vises på pop op-siden.

<a name="manage-alerts"></a>

## <a name="manage-alerts"></a>Administrer beskeder

Når beskeder er blevet oprettet og vist på siden Beskeder i **overholdelsescenteret** , kan du undersøge og løse dem. De samme [RBAC-tilladelser,](#rbac-permissions-required-to-view-alerts) der giver brugerne adgang til beskeder, giver dem også mulighed for at administrere beskeder.

Her er nogle opgaver, du kan udføre for at administrere beskeder.

- **Tildel en status til beskeder.** Du kan tildele en af følgende statusser til beskeder: **Aktiv** (standardværdien), **Undersøger****, Løst** **eller Afvist**. Derefter kan du filtrere efter denne indstilling for at få vist beskeder med samme statusindstilling. Denne statusindstilling kan hjælpe dig med at holde styr på processen med at administrere beskeder.

- **Vis oplysninger om besked.** Du kan vælge en besked for at få vist en pop op-side med oplysninger om beskeden. De detaljerede oplysninger afhænger af den tilsvarende beskedpolitik, men den indeholder typisk følgende:

  - Navnet på den faktiske handling, der udløste beskeden, f.eks. en cmdlet eller en overvågningsloghandling.

  - En beskrivelse af den aktivitet, der udløste beskeden.

  - Den bruger (eller liste over brugere), der udløste beskeden. Dette er kun inkluderet i beskedpolitikker, der er konfigureret til at spore en enkelt bruger eller en enkelt aktivitet.

  - Antallet af gange, den aktivitet, der registreres af beskeden, blev udført. Dette tal stemmer muligvis ikke overens med det faktiske antal relaterede beskeder, der er angivet på siden Vigtige beskeder, da der muligvis er blevet udløst flere beskeder.

  - Et link til en aktivitetsliste, der indeholder et element for hver aktivitet, der blev udført, som udløste beskeden. Hver post på denne liste identificerer, hvornår aktiviteten forekom, navnet på den faktiske handling (f.eks. "FileDeleted"), den bruger, der udførte aktiviteten, objektet (f.eks. en fil, en eDiscovery-sag eller en postkasse), som aktiviteten blev udført på, og IP-adressen på brugerens computer. Dette linker til en meddelelsesliste for malwarerelaterede beskeder.

  - Navnet (og linket) på den tilsvarende beskedpolitik.

- **Skjule mailbeskeder.** Du kan deaktivere (eller skjule) mailbeskeder fra pop op-siden for en besked. Når du undertrykker mailbeskeder, sender Microsoft ikke meddelelser, når der sker aktiviteter eller hændelser, der opfylder betingelserne i beskedpolitikken. Men der udløses beskeder, når aktiviteter udført af brugere opfylder betingelserne i beskedpolitikken. Du kan også deaktivere mailbeskeder ved at redigere påmindelsespolitikken.

- **Løs beskeder.** Du kan markere en besked som løst på pop op-siden for en besked (hvilket angiver status for beskeden til **Løst**). Medmindre du ændrer filteret, vises løste beskeder ikke på **siden Vigtige** beskeder.

<a name="viewing-cloud-app-security-alerts"></a>

## <a name="view-defender-for-cloud-apps-alerts"></a>Få vist beskeder om Defender til skyapps

Beskeder, der **udløses** af Office 365 Cloud App Security politikker, vises nu på siden Beskeder i Overholdelsescenter. Dette omfatter beskeder, der udløses af aktivitetspolitikker og påmindelser, der er udløst af politikker til registrering af unormalt Office 365 Cloud App Security. Det betyder, at du kan få vist alle beskeder i overholdelsescenteret. Office 365 Cloud App Security er kun tilgængeligt for organisationer med et Office 365 Enterprise E5- Office 365 Government G5-abonnement. Få mere at vide under [Oversigt over Defender til skyapps](/cloud-app-security/what-is-cloud-app-security).

Organisationer, der har Microsoft Defender til skyapps som en del af et Enterprise Mobility + Security E5-abonnement eller som en separat tjeneste, kan også få vist Defender for Cloud Apps-beskeder, der er relateret til Microsoft 365-apps og -tjenester på Microsoft 365 Overholdelsescenter eller den Microsoft 365 Defender portal.

Hvis du kun vil have vist Defender for Cloud Apps-beskeder i overholdelsescenteret eller På Defender-portalen, skal du bruge kildefilteret og **vælge Defender til skyapps**.

![Brug kildefilteret til kun at vise Defender for skyapps-beskeder.](../media/FilterCASAlerts.png)

På samme måde som en besked, der udløses af en beskedpolitik i overholdelsescenteret, kan du vælge en Defender for Cloud Apps-besked for at få vist en pop op-side med oplysninger om beskeden. Beskeden indeholder et link til at få vist detaljerne og administrere beskeden i Defender for Cloud Apps-portalen og et link til den tilsvarende politik for Defender for Cloud Apps, der udløste beskeden. Se [Overvåg beskeder i Defender til skyapps](/cloud-app-security/monitor-alerts).

![Oplysninger om påmindelse indeholder links til Defender for Cloud Apps-portalen.](../media/CASAlertDetail.png)

> [!IMPORTANT]
> Hvis du ændrer status for en Defender for Cloud Apps-besked i overholdelsescenteret, opdateres opløsningsstatus ikke for den samme besked i portalen Defender for Cloud Apps. Hvis du f.eks. markerer status for beskeden som  Løst i overholdelsescenteret, er status for beskeden i portalen Defender for Cloud Apps uændret. For at løse eller afvise en Defender for Cloud Apps-besked, skal du administrere beskeden i Defender for Cloud Apps-portalen.
