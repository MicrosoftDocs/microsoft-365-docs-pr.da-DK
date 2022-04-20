---
title: Beskyt mod trusler i Microsoft Defender for Office 365, antimalware, anti-phishing, anti-spam, Pengeskab links, Pengeskab vedhæftede filer, zap (automatisk udrensning på nul timer), konfiguration af MDO-sikkerhed
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
ms.date: 06/22/2021
search.appverid:
- MOE150
- MET150
ms.assetid: b10023f6-f30f-45d3-b3ad-b71aa4aa0d58
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Administratorer kan få mere at vide om trusselsbeskyttelse i Microsoft 365 og konfigurere, hvordan de bruger det til din organisation.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d067035d5eaf3c7a4febac6feeab0c56cd707728
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941429"
---
# <a name="protect-against-threats"></a>Beskyt mod trusler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Her er en vejledning til hurtig start, der opdeler konfigurationen af Defender for Office 365 i segmenter. Hvis du ikke kender funktionerne til trusselsbeskyttelse i Office 365, er du ikke sikker på, hvor du skal begynde, eller hvis du lærer bedst ved *at gøre* det, skal du bruge denne vejledning som en tjekliste og et udgangspunkt.

> [!IMPORTANT]
> **De indledende anbefalede indstillinger er inkluderet for hver type politik. Der er dog mange tilgængelige indstillinger, og du kan justere dine indstillinger, så de passer til din organisations behov**. Det kan tage ca. 30 minutter, før dine politikker eller ændringer fungerer gennem dit datacenter.
>
> Hvis du vil springe den manuelle konfiguration af de fleste politikker i Defender for Office 365 over, kan du bruge forudindstillede sikkerhedspolitikker på standard- eller strict-niveau. Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

## <a name="requirements"></a>Krav

### <a name="subscriptions"></a>Abonnementer

Trusselsbeskyttelsesfunktioner er inkluderet i *alle* Microsoft- eller Office 365-abonnementer, men nogle abonnementer har avancerede funktioner. I nedenstående tabel vises de beskyttelsesfunktioner, der er inkluderet i denne artikel, sammen med minimumskravene til abonnementer.

> [!TIP]
> Bemærk, at ud over vejledningen til at aktivere overvågning starter *trin* antimalware, anti-phishing og anti-spam, som er markeret som en del af Office 365 Exchange Online Protection (**EOP**). Det kan virke mærkeligt i en Defender for Office 365 artikel, indtil du husker, at (**Defender for Office 365**) indeholder og bygger videre på EOP.

|Beskyttelsestype|Abonnementskrav|
|---|---|
|Overvågningslogføring (til rapporteringsformål)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Beskyttelse mod malware|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Beskyttelse mod phishing|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Beskyttelse mod spam|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Beskyttelse mod skadelige URL-adresser og filer i mails og Office dokumenter (Pengeskab links og Pengeskab vedhæftede filer)|[Microsoft Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Roller og tilladelser

Hvis du vil konfigurere Defender for Office 365 politikker, skal du have tildelt en relevant rolle. Se tabellen nedenfor for roller, der kan udføre disse handlinger.

|Rolle eller rollegruppe|Her kan du få mere at vide|
|---|---|
|global administrator|[Om Microsoft 365 administratorroller](../../admin/add-users/about-admin-roles.md)|
|Sikkerhedsadministrator|[Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference#security-administrator)
|Exchange Online organisationsstyring|[Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo)|

Du kan få mere at vide under [Tilladelser på portalen Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Slå overvågningslogføring til for rapportering og undersøgelse

- Start din overvågningslogføring tidligt. Du skal bruge overvågning for at være **AKTIVERET** for nogle af følgende trin. Overvågningslogføring er tilgængelig i abonnementer, der omfatter [Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Hvis du vil have vist data i rapporter om trusselsbeskyttelse, [mailsikkerhedsrapporter](view-email-security-reports.md) og [Stifinder](threat-explorer.md), skal logføring af overvågning være *slået til*. Du kan få mere at vide under [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Del 1 – Beskyttelse mod malware i EOP

Du kan få flere oplysninger om de anbefalede indstillinger for antimalware under [Politikindstillinger for EOP-antimalware](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Åbn siden **Antimalware** på portalen Microsoft 365 Defender på <https://security.microsoft.com/antimalwarev2>.

2. På siden **Antimalware** skal du vælge politikken **Standard (standard)** ved at klikke på navnet.

3. I pop op-vinduet med politikoplysninger, der åbnes, skal du klikke på **Rediger beskyttelsesindstillinger** og derefter konfigurere følgende indstillinger:
   - Sektionen **Beskyttelsesindstillinger**:
     - **Aktivér filteret for almindelige vedhæftede filer**: Vælg (slå til). Klik på **Tilpas filtyper** for at tilføje flere filtyper.
     - **Aktivér automatisk fjernelse på nul timer for malware**: Kontrollér, at denne indstilling er valgt. Du kan få flere oplysninger om ZAP til malware under [Automatisk udrensning (ZAP) på nul timer for malware](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware).
   - **Karantænepolitik**: Lad standardværdien AdminOnlyAccessPolicy være valgt. Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne, og om brugerne modtager karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).
   - **Meddelelsessektion** : Kontrollér, at ingen af meddelelsesindstillingerne er valgt.

   Klik på **Gem**, når du er færdig.

4. Klik på **Luk** på pop op-vinduet med politikoplysninger igen.

Du kan finde detaljerede instruktioner til konfiguration af politikker for antimalware under [Konfigurer politikker for antimalware i EOP](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Del 2 – Beskyttelse mod phishing i EOP og Defender for Office 365

[Anti-phishing-beskyttelse](anti-phishing-protection.md) er tilgængelig i abonnementer, der omfatter [EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Avanceret anti-phishing-beskyttelse er tilgængelig i [Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Du kan få flere oplysninger om de anbefalede indstillinger for politikker til bekæmpelse af phishing under [Indstillinger for EOP-politik for anti-phishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) og [Indstillinger for politik for anti-phishing i Microsoft Defender for Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

I følgende procedure beskrives det, hvordan du konfigurerer standardpolitikken for anti-phishing. Indstillinger, der kun er tilgængelige i Defender for Office 365, er markeret tydeligt.

1. Åbn siden **Anti-phishing** på Microsoft 365 Defender-portalen på <https://security.microsoft.com/antiphishing>.

2. På siden **Anti-phishing** skal du vælge politikken med navnet **Office365 Antiphish Default (Standard)** ved at klikke på navnet.

3. Konfigurer følgende indstillinger i det pop op-vindue med politikoplysninger, der vises:
   - **Tærskel for phishing & beskyttelse** : Klik på **Rediger beskyttelsesindstillinger** , og konfigurer følgende indstillinger i det pop op-vindue, der åbnes:
     - **Grænseværdi for**<sup>\*</sup> phishingmail: Vælg **2 – Aggressiv** (standard) eller **3 – Mere aggressiv** (streng).
     - **Repræsentationsafsnit**<sup>\*</sup>: Konfigurer følgende værdier:
       - Vælg **Aktivér brugere for at beskytte**, klik på linket **Administrer (nn) afsendere** , der vises, og tilføj derefter interne og eksterne afsendere for at beskytte mod repræsentation, f.eks. organisationens bestyrelsesmedlemmer, din administrerende direktør, økonomidirektøren og andre overordnede ledere.
       - Vælg **Aktivér domæner for at beskytte**, og konfigurer derefter følgende indstillinger, der vises:
         - Vælg **Medtag domæner, jeg ejer** , for at beskytte interne afsendere i dine accepterede domæner (synlig ved at klikke på **Vis mine domæner**) mod repræsentation.
         - Hvis du vil beskytte afsendere i andre domæner, skal du vælge **Medtag brugerdefinerede domæner**, klikke på linket **Administrer (nn) brugerdefinerede domæner** , der vises, og derefter tilføje andre domæner for at beskytte mod repræsentation.
     - Tilføj afsnittet <sup>\*</sup> **Afsendere og domæner,** der er tillid til: Klik på **Administrer (nn) afsendere, der er tillid til, og domæner, der er tillid** til, for at konfigurere undtagelser fra afsender- og afsenderdomæne til repræsentationsbeskyttelse, hvis det er nødvendigt.
     - Indstillinger for <sup>\*</sup> postkasseintelligens: Kontrollér, at **Aktivér postkasseintelligens** og **Aktivér intelligens for repræsentationsbeskyttelse** er valgt.
     - **Afsnittet Spoof** : Kontrollér, at **Aktivér spoof intelligence** er valgt.

     Klik på **Gem**, når du er færdig.

   - Afsnittet **Handlinger**: Klik på **Rediger handlinger**, og konfigurer følgende indstillinger i det pop op-vindue, der åbnes:
     - Afsnittet **Meddelelseshandlinger**: Konfigurer følgende indstillinger:
       - **Hvis meddelelsen registreres som en repræsenteret bruger**<sup>\*</sup>: Vælg **Sæt meddelelsen i karantæne**. Feltet **Anvend karantænepolitik** vises, hvor du vælger den [karantænepolitik](quarantine-policies.md) , der gælder for meddelelser, der er sat i karantæne af beskyttelse mod brugerpræsentation.
       - **Hvis meddelelsen registreres som et repræsenteret domæne**<sup>\*</sup>: Vælg **Sæt meddelelsen i karantæne**. Feltet **Anvend karantænepolitik** vises, hvor du vælger den [karantænepolitik](quarantine-policies.md) , der gælder for meddelelser, der er sat i karantæne af beskyttelse mod repræsentation af domæner.
       - **Hvis postkasseintelligens registrerer en repræsenteret bruger**<sup>\*</sup>: Vælg **Flyt meddelelse til modtagernes mapper med uønsket mail** (Standard) eller **Sæt meddelelsen i karantæne** (Strict). Hvis du vælger **Sæt meddelelsen i karantæne**, vises feltet **Anvend karantænepolitik** , hvor du vælger den [karantænepolitik](quarantine-policies.md) , der gælder for meddelelser, der er sat i karantæne af Mailbox Intelligence Protection.
       - **Hvis meddelelsen registreres som spoof**: Vælg **Flyt meddelelse til modtagernes mapper med uønsket mail** (Standard) eller **Sæt meddelelsen i karantæne** (Strict).  Hvis du vælger **Sæt meddelelsen i karantæne**, vises feltet **Anvend karantænepolitik** , hvor du vælger den [karantænepolitik](quarantine-policies.md) , der gælder for meddelelser, der er sat i karantæne af spoof intelligence-beskyttelse.
     - **Afsnittet Sikkerhedstip & indikatorer** : Konfigurer følgende indstillinger:
       - **Vis første kontakt sikkerhedstip**: Vælg (aktivér).
       - **Vis bruger repræsenter sikkerhedstip**<sup>\*</sup>: Vælg (aktivér).
       - **Vis repræsentation af domænet sikkerhedstip**<sup>\*</sup>: Vælg (slå til).
       - **Vis usædvanlige tegn for brugerpræsentation sikkerhedstip**<sup>\*</sup>: Vælg (aktivér).
       - **Vis (?) for ikke-godkendte afsendere for spoof**: Vælg (aktivér).
       - **Vis mærket "via"**: Vælg (aktivér).

     Klik på **Gem**, når du er færdig.

   <sup>\*</sup>Denne indstilling er kun tilgængelig i Defender for Office 365.

4. Klik på **Gem** , og klik derefter på **Luk**

Du kan finde detaljerede instruktioner til konfiguration af politikker til anti-phishing under [Konfigurer politikker til bekæmpelse af phishing i EOP](configure-anti-phishing-policies-eop.md) og [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Del 3 – Beskyttelse mod spam i EOP

Du kan få flere oplysninger om de anbefalede indstillinger for anti-spam under [Politikindstillinger for EOP for spam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

1. Åbn siden **Politikker til bekæmpelse af spam** på portalen Microsoft 365 Defender på <https://security.microsoft.com/antispam>.

2. På siden **Politikker for uønsket post** skal du vælge politikken med navnet **Indgående politik for uønsket post (standard)** på listen ved at klikke på navnet.

3. Konfigurer følgende indstillinger i det pop op-vindue med politikoplysninger, der vises:
   - **Grænseværdi for massemail & afsnittet med egenskaber for spam** : Klik på **Rediger grænseværdi for spam og egenskaber**. Konfigurer følgende indstillinger i det pop op-vindue, der vises:
     - **Grænseværdi for massemail**: Angiv denne værdi til 5 (Strict) eller 6 (Standard).
     - Lad andre indstillinger være til deres standardværdier (**Fra** eller **Ingen**).

     Klik på **Gem**, når du er færdig.

   - Afsnittet **Handlinger**: Klik på **Rediger handlinger**. Konfigurer følgende indstillinger i det pop op-vindue, der vises:
     - Afsnittet **Meddelelseshandlinger**:
       - **Spam**: Bekræft **, at Flyt meddelelse til mappen Uønsket mail** er valgt (Standard), eller vælg **Karantænemeddelelse** (Strict).
       - **Spam med høj genkendelsessikkerhed**: Vælg **Karantænemeddelelse**.
       - **Phishing**: Vælg **Karantænemeddelelse**.
       - **Phishing med høj genkendelsessikkerhed**: Kontrollér **, at karantænemeddelelser** er valgt.
       - **Masse**: Kontrollér, **at Flyt meddelelse til mappen Uønsket mail** er valgt (Standard), eller vælg **Karantænemeddelelse** (Streng).

       For hver handling, hvor du vælger **Karantænemeddelelse**, vises feltet **Vælg karantænepolitik** , hvor du vælger den [karantænepolitik](quarantine-policies.md) , der gælder for meddelelser, der er sat i karantæne af beskyttelse mod spam.

     - **Bevar spam i karantæne i dette antal dage**: Kontrollér værdien **30** dage.
     - **Aktivér tip til spamsikkerhed**: Kontrollér, at denne indstilling er valgt (slået til).
     - **Aktivér automatisk fjernelse på nul timer (ZAP):** Kontrollér, at denne indstilling er valgt (slået til).
       - **Aktivér for phishing-meddelelser**: Kontrollér, at denne indstilling er valgt (slået til). Du kan få flere oplysninger under [Automatisk rensning på nul timer (ZAP) for phishing](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing).
       - **Aktivér for spammeddelelser**: Kontrollér, at denne indstilling er valgt (slået til). Du kan få flere oplysninger under [Automatisk udrensning på nul timer (ZAP) for spam](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam).

     Klik på **Gem**, når du er færdig.

   - Afsnittet **Tilladte og blokerede afsendere og domæner**: Gennemse eller rediger dine tilladte afsendere og tilladte domæner som beskrevet i [Opret lister over blokerede afsendere på EOP](create-block-sender-lists-in-office-365.md)- eller [Opret sikre afsenderlister i EOP](create-safe-sender-lists-in-office-365.md).

     Klik på **Gem**, når du er færdig.

4. Klik på **Luk**, når du er færdig.

Du kan finde detaljerede instruktioner til, hvordan du konfigurerer politikker mod spam, under [Konfigurer politikker til bekæmpelse af spam i EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Del 4 – Beskyttelse mod skadelige URL-adresser og filer (Pengeskab links og Pengeskab vedhæftede filer i Defender for Office 365)

Beskyttelsestid for klik fra skadelige URL-adresser og filer er tilgængelig i abonnementer, der omfatter [Microsoft Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Den konfigureres via [politikker for vedhæftede filer Pengeskab](safe-attachments.md) og [Pengeskab links](safe-links.md).

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Pengeskab politikker for vedhæftede filer i Microsoft Defender for Office 365

Du kan få flere oplysninger om de anbefalede indstillinger for Pengeskab Vedhæftede filer under .[ Pengeskab indstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. Åbn siden **Pengeskab vedhæftede filer** på Microsoft 365 Defender-portalen på <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab Vedhæftede filer** skal du klikke på **Globale indstillinger** og derefter konfigurere følgende indstillinger på det pop op-vindue, der vises:
   - **Slå Defender for Office 365 til for SharePoint, OneDrive og Microsoft Teams**: Slå denne indstilling til (![Slå til).](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > **Før du aktiverer Pengeskab Vedhæftede filer for SharePoint, OneDrive og Microsoft Teams, skal du kontrollere, at logføring af overvågning er slået til i din organisation**. Denne handling udføres typisk af en person, der har rollen Overvågningslogger tildelt i Exchange Online. Du kan finde flere oplysninger under [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md)!

   - **Slå Pengeskab dokumenter til for Office klienter**: Slå denne indstilling til (![Slå til).](../../media/scc-toggle-on.png)). Bemærk, at denne funktion kun er tilgængelig og giver mening med de påkrævede licenstyper. Du kan få flere oplysninger [under Pengeskab dokumenter i Microsoft 365 E5](safe-docs.md).
   - **Tillad, at andre klikker gennem beskyttet visning, selvom Pengeskab dokumenter har identificeret filen som skadelig**: Kontrollér, at denne indstilling er slået fra (![Slå til/fra](../../media/scc-toggle-off.png)).

   Når du er færdig, skal du klikke på **Gem**

3. Klik på Opret ikon på siden **vedhæftede filer på siden** ![Pengeskab vedhæftede filer.](../../media/m365-cc-sc-create-icon.png)

4. Konfigurer følgende indstillinger i **guiden Opret Pengeskab vedhæftede filer**, der åbnes:
   - **Navngiv din politikside** :
     - **Navn**: Angiv noget entydigt og beskrivende.
     - **Beskrivelse**: Angiv en valgfri beskrivelse.
   - Siden **Brugere og domæner**: Da dette er din første politik, og du sandsynligvis vil maksimere dækningen, kan du overveje at angive dine [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i feltet **Domæner**. Ellers kan du bruge felterne **Brugere** og **Grupper** til mere detaljeret kontrol. Du kan angive undtagelser ved at vælge **Udelad disse brugere, grupper og domæner** og angive værdier.
   - **Indstillinger** side:
     - **Pengeskab Vedhæftede filer ukendt malware-svar**: Vælg **Bloker**.
     - **Karantænepolitik**: Standardværdien er tom, hvilket betyder, at politikken AdminOnlyAccessPolicy bruges. Karantænepolitikker definerer, hvad brugerne kan gøre for at sætte meddelelser i karantæne, og om brugerne modtager karantænemeddelelser. Du kan få flere oplysninger under [Karantænepolitikker](quarantine-policies.md).
     - **Omdiriger vedhæftet fil med registrerede vedhæftede filer** : **Aktivér omdirigering**: Slå denne indstilling til (vælg), og angiv en mailadresse for at modtage registrerede meddelelser.
     - **Anvend Pengeskab registreringssvar for vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout eller fejl)**: Kontrollér, at denne indstilling er valgt.

5. Når du er færdig, skal du klikke på **Send** og derefter klikke på **Udført**.

6. (Anbefalet) Som global administrator eller SharePoint **[Online-administrator skal du køre Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/Set-SPOTenant)** med parameteren _DisallowInfectedFileDownload_ angivet til `$true` i SharePoint Online PowerShell.
   - `$true` blokerer alle handlinger (undtagen Slet) for registrerede filer. Personer kan ikke åbne, flytte, kopiere eller dele registrerede filer.
   - `$false` blokerer alle handlinger undtagen Slet og Download. Folk kan vælge at acceptere risikoen og downloade en registreret fil.

7. Det kan tage op til 30 minutter, før dine ændringer kan spredes til alle Microsoft 365 datacentre.

Du kan finde detaljerede instruktioner til konfiguration af politikker for vedhæftede filer Pengeskab og globale indstillinger for Pengeskab Vedhæftede filer i følgende emner:

- [Konfigurer politikker for vedhæftede filer Pengeskab i Microsoft Defender for Office 365](set-up-safe-attachments-policies.md)
- [Aktiver Sikre vedhæftede filer i SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Sikre dokumenter i Microsoft 365 E5](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>politikker for Pengeskab links i Microsoft Defender for Office 365

Du kan få flere oplysninger om de anbefalede indstillinger for Pengeskab Links under [Pengeskab Indstillinger for links](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. Åbn siden **Pengeskab links** på portalen Microsoft 365 Defender på <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links** skal du klikke på **Globale indstillinger** og derefter konfigurere følgende indstillinger på det pop op-vindue, der vises:
   - **Indstillinger, der gælder for indhold i afsnittet understøttede Office 365 apps**:
     - **Brug Pengeskab links i Office 365 apps**: Kontrollér, at denne indstilling er slået til (![Til/](../../media/scc-toggle-on.png)fra).
     - **Spor ikke, når brugere klikker på beskyttede links i Office 365 apps**: Slå denne indstilling fra (![Slå til/fra](../../media/scc-toggle-off.png)).
     - **Lad ikke brugerne klikke sig igennem til den oprindelige URL-adresse i Office 365 apps**: Kontrollér, at denne indstilling er slået til (![Slå til](../../media/scc-toggle-on.png)).

   Når du er færdig, skal du klikke på **Gem**

3. Klik på Opret ikon på siden ![**links Pengeskab** igen.](../../media/m365-cc-sc-create-icon.png)

4. Konfigurer følgende indstillinger i **guiden Opret Pengeskab links-politik**, der åbnes:
   - **Navngiv din politikside** :
     - **Navn**: Angiv noget entydigt og beskrivende.
     - **Beskrivelse**: Angiv en valgfri beskrivelse.
   - Siden **Brugere og domæner**: Da dette er din første politik, og du sandsynligvis vil maksimere dækningen, kan du overveje at angive dine [accepterede domæner](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) i feltet **Domæner**. Ellers kan du bruge felterne **Brugere** og **Grupper** til mere detaljeret kontrol. Du kan angive undtagelser ved at vælge **Udelad disse brugere, grupper og domæner** og angive værdier.
   - **URL-adresse & klik på siden med beskyttelsesindstillinger** :
     - **Handling på potentielt skadelige URL-adresser i sektionen Mails** :
       - **On: Pengeskab Links kontrollerer en liste over kendte, ondsindede links, når brugerne klikker på links i mail**: Vælg hans indstilling (slå til).
       - **Anvend Pengeskab Links på mails, der er sendt i organisationen**: Vælg denne indstilling (aktivér).
       - **Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer**: Vælg denne indstilling (aktivér).
       - **Vent, indtil scanningen af URL-adressen er fuldført, før du leverer meddelelsen**: Vælg denne indstilling (aktivér).
       - **Undlad at omskrive URL-adresser. Kontrollér kun via API'en Pengeskab Links**: Kontrollér, at denne indstilling ikke er valgt (deaktiver).
     - **Omskriv ikke følgende URL-adresser i en mail**: Vi har ingen specifik anbefaling til denne indstilling. Du kan få flere oplysninger på [listerne "Omskriv ikke følgende URL-adresser" i politikker for Pengeskab links](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).
     - **Handling for potentielt skadelige URL-adresser i Microsoft Teams** afsnit:
       - ***Til: Pengeskab Links kontrollerer en liste over kendte, skadelige links, når brugere klikker på links i Microsoft Teams**: Vælg denne indstilling (aktivér).
     - **Klik på sektionen Beskyttelsesindstillinger** :
       - **Spor bruger clicks**: Kontrollér, at denne indstilling er valgt (slået til).
       - **Lad brugerne klikke sig igennem til den oprindelige URL-adresse**: Slå denne indstilling fra (ikke valgt).
       - **Vis organisationsbranding på meddelelses- og advarselssider**: Valg af denne indstilling (aktivering af den) giver kun mening, når du har fulgt vejledningen i [Tilpas det Microsoft 365 tema, som din organisation](../../admin/setup/customize-your-organization-theme.md) skal bruge til at uploade virksomhedens logo.
   - **Meddelelsesside** :
     - **Hvordan vil du give brugerne besked?** sektion: Du kan også vælge **Brug brugerdefineret meddelelsestekst** til at angive tilpasset meddelelsestekst, der skal bruges. Du kan også vælge **Brug Microsoft Oversætter til automatisk lokalisering for** at oversætte den brugerdefinerede meddelelsestekst til brugerens sprog. Ellers skal du lade **Brug standardmeddelelsesteksten** være markeret.

5. Når du er færdig, skal du klikke på **Send** og derefter klikke på **Udført**.

Du kan finde detaljerede instruktioner til konfiguration af politikker for Pengeskab links og globale indstillinger for Pengeskab Links i følgende emner:

- [Konfigurer politikker for Pengeskab links i Microsoft Defender for Office 365](set-up-safe-links-policies.md)
- [Konfigurer globale indstillinger for Pengeskab links i Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>Konfigurer nu beskeder for registrerede filer i SharePoint Online eller OneDrive for Business

Hvis du vil modtage en meddelelse, når en fil i SharePoint Online eller OneDrive for Business er blevet identificeret som skadelig, kan du konfigurere en besked, som beskrevet i dette afsnit.

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Beskedpolitik**.

2. Klik på **Ny beskedpolitik** på siden **Beskedpolitik**.

3. Guiden **Ny beskedpolitik** åbnes. Konfigurer følgende indstillinger på siden **Navn** :
   - **Navn**: Angiv et entydigt og beskrivende navn. Du kan f.eks. skrive Ondsindede filer i biblioteker.
   - **Beskrivelse**: Angiv en valgfri beskrivelse.
   - **Alvorsgrad**: Vælg **Lav**, **Mellem** eller **Høj**.
   - **Kategori**: Vælg **Trusselsadministration**.

   Klik på **Næste**, når du er færdig

4. Konfigurer følgende indstillinger på siden **Opret beskedindstillinger** :
   - **Hvad vil du advare om?** sektion: **Aktivitet er** \> **registreret malware i filen**.
   - **Hvordan skal beskeden udløses** : Kontrollér **, hver gang en aktivitet stemmer overens med reglen** .

   Klik på **Næste**, når du er færdig

5. Konfigurer følgende indstillinger på siden **Angiv dine modtagere** :
   - **Send mailmeddelelser**: Kontrollér, at denne indstilling er valgt.
   - **Mailmodtagere**: Vælg en eller flere globale administratorer, sikkerhedsadministratorer eller sikkerhedslæsere, der skal modtage en meddelelse, når der registreres en skadelig fil.
   - **Grænse for daglig meddelelse**: Kontrollér **, at der ikke er valgt nogen grænse** .

   Klik på **Næste**, når du er færdig

6. Gennemse indstillingerne på siden **Gennemse dine indstillinger** , kontrollér **Ja, slå det til med det samme** er markeret, og klik derefter på **Udfør**

Hvis du vil vide mere om politikker for beskeder, skal du se [Beskedpolitikker på Microsoft Purview-overholdelsesportalen](../../compliance/alert-policies.md).

> [!NOTE]
> Når du er færdig med at konfigurere, kan du bruge disse links til at starte arbejdsbelastningsundersøgelser:
>
> - [Statusrapport om trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
> - [Brug Microsoft 365 Defender-portalen til at administrere filer i karantæne i Defender for Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [Sådan gør du, når du finder en skadelig fil i SharePoint Online, OneDrive eller Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [Administrer karantænemeddelelser og filer som administrator i Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Opgaver efter konfiguration og næste trin

Når du har konfigureret funktionerne til trusselsbeskyttelse, skal du sørge for at overvåge, hvordan disse funktioner fungerer! Gennemse og rediger dine politikker, så de gør, hvad du har brug for dem til. Hold også øje med nye funktioner og tjenesteopdateringer, der kan tilføje værdi.

|Sådan gør du|Ressourcer til at få mere at vide|
|---|---|
|Se, hvordan trusselsbeskyttelsesfunktioner fungerer for din organisation, ved at få vist rapporter|[Mailsikkerhedsrapporter](view-email-security-reports.md) <p> [Rapporter til Microsoft Defender for Office 365](view-reports-for-mdo.md) <p> [Trusselsoversigt](threat-explorer.md)|
|Gennemse og revider jævnligt dine politikker for trusselsbeskyttelse efter behov|[Sikker score](../defender/microsoft-secure-score.md) <p> [funktioner til Microsoft 365 trusselsundersøgelse og svar](./office-365-ti.md)|
|Hold øje med nye funktioner og tjenesteopdateringer|[Standardindstillinger og målrettede udgivelsesmuligheder](../../admin/manage/release-options-in-office-365.md) <p> [Meddelelsescenter](../../admin/manage/message-center.md) <p> [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Tjenestebeskrivelser](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
