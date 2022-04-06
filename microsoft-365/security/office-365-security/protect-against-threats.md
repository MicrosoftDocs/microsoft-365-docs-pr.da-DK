---
title: Beskyt dig mod trusler i Microsoft Defender for Office 365, antimalware, antiphishing, uønsket post, Pengeskab-links, Pengeskab-vedhæftede filer, T ZAP (Zero-hour Auto Tømning), MDO-sikkerhedskonfiguration
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
description: Administratorer kan få mere at vide om trusselsbeskyttelse Microsoft 365 at vide og konfigurere, hvordan de skal bruge det i din organisation.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e5a0be5171a2de07792cd259dc6547046d7c1630
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507166"
---
# <a name="protect-against-threats"></a>Beskyt dig mod trusler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Her er en startvejledning, der bryder konfigurationen af Defender for Office 365 i dele. Hvis du er ny bruger af funktioner til trusselsbeskyttelse i Office 365, er i tvivl om, hvor du skal begynde, eller hvis du lærer bedst ved at *gøre det,* kan du bruge denne vejledning som en tjekliste og et udgangspunkt.

> [!IMPORTANT]
> **Oprindeligt anbefalede indstillinger er inkluderet for** hver type politik, men der er mange tilgængelige indstillinger, og du kan justere dine indstillinger, så de opfylder din specifikke organisations behov. Det kan tage ca. 30 minutter, før dine politikker eller ændringer arbejder sig gennem dit datacenter.
>
> Hvis du vil springe manuel konfiguration af de fleste politikker over Defender for Office 365, kan du bruge forudindstillede sikkerhedspolitikker på niveauet Standard eller Begrænset. Få mere at vide under [Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md).

## <a name="requirements"></a>Krav

### <a name="subscriptions"></a>Abonnementer

Funktioner til trusselsbeskyttelse er *inkluderet* i alle Microsoft- Office 365-abonnementer, men nogle abonnementer har avancerede funktioner. Tabellen nedenfor viser de beskyttelsesfunktioner, der er inkluderet i denne artikel sammen med minimumskravene til abonnement.

> [!TIP]
> Bemærk, at foruden vejledningen i at aktivere overvågning starter trinene antimalware, antiphishing og uønsket post, som er markeret som en del af Office 365 Exchange Online Protection (**EOP**).  Dette kan virke underligt i Defender for Office 365 artikel, indtil du husker (**Defender for Office 365**) indeholder og bygger på, EOP.

|Beskyttelsestype|Abonnementskrav|
|---|---|
|Overvågningslogføring (til rapporteringsformål)|[Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)|
|Beskyttelse mod malware|[Exchange Online Protection](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description) (**EOP**)|
|Beskyttelse mod phishing|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Beskyttelse mod uønsket post|[EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description)|
|Beskyttelse mod skadelige URL-adresser og filer i mails og Office (Pengeskab Links og Pengeskab vedhæftede filer)|[Microsoft Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description)|

### <a name="roles-and-permissions"></a>Roller og tilladelser

Hvis du Defender for Office 365 politikker, skal du have tildelt en passende rolle. Se tabellen herunder for roller, der kan udføre disse handlinger.

|Rolle eller rollegruppe|Her kan du få mere at vide|
|---|---|
|global administrator|[Om Microsoft 365 administratorroller](../../admin/add-users/about-admin-roles.md)|
|Sikkerhedsadministrator|[Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference#security-administrator)
|Exchange Online organisationsadministration|[Tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo)|

Du kan få mere at [vide under Tilladelser i Microsoft 365 Defender portal](permissions-microsoft-365-security-center.md).

### <a name="turn-on-audit-logging-for-reporting-and-investigation"></a>Slå overvågningslogføring til for rapportering og undersøgelse

- Start overvågningslogføringen tidligt. Du skal have overvågning til for **at kunne** bruge nogle af de følgende trin. Overvågningslogføring er tilgængelig i abonnementer, der [Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). For at få vist data i rapporter om trusselsbeskyttelse, [mailsikkerhedsrapporter](view-email-security-reports.md) og [Stifinder](threat-explorer.md) skal overvågningslogføring være *til*. Du kan få mere at vide [under Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="part-1---anti-malware-protection-in-eop"></a>Del 1 – Beskyttelse mod malware i EOP

Du kan finde flere oplysninger om de anbefalede indstillinger for antimalware i [Politikindstillinger for EOP-antimalware](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings).

1. Åbn **siden for antimalware** i Microsoft 365 Defender på <https://security.microsoft.com/antimalwarev2>.

2. På siden **Antimalware** skal du vælge politikken Standard **(standard)** ved at klikke på navnet.

3. I pop op-vindue med politikoplysninger, der åbnes, **skal du klikke på Rediger** beskyttelsesindstillinger og derefter konfigurere følgende indstillinger:
   - **Sektionen Beskyttelsesindstillinger** :
     - **Aktivér filteret for almindelige vedhæftede** filer: Vælg (slå til). Klik **på Tilpas filtyper** for at tilføje flere filtyper.
     - **Aktivér automatisk tømning uden time for malware**: Bekræft, at denne indstilling er valgt. Du kan finde flere oplysninger om ZAP for malware i [Nul-timers automatisk tømning (ZAP) for malware](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-malware).
   - **Karantænepolitik**: Lad standardværdien AdminOnlyAccessPolicy være markeret. Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne, og om brugerne modtager beskeder om karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).
   - **Meddelelsessektion** : Kontrollér, at ingen af indstillingerne for meddelelser er markeret.

   Klik på **Gem**, når du er færdig.

4. Tilbage i pop op-menuen med politikoplysninger skal du klikke **på Luk**.

Du kan finde detaljerede instruktioner til konfiguration af antimalwarepolitikker [under Konfigurer antimalwarepolitikker i EOP](configure-anti-malware-policies.md).

## <a name="part-2---anti-phishing-protection-in-eop-and-defender-for-office-365"></a>Del 2 – Beskyttelse mod phishing i EOP og Defender for Office 365

[Beskyttelse mod phishing er](anti-phishing-protection.md) tilgængelig i abonnementer, der omfatter [EOP](/office365/servicedescriptions/exchange-online-protection-service-description/exchange-online-protection-service-description). Avanceret beskyttelse mod phishing findes i [Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

Du kan finde flere oplysninger om de anbefalede indstillinger for antiphishing-politikker i [Politikindstillinger for EOP-antiphishing](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings) og politikindstillinger for [phishing Microsoft Defender for Office 365](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365).

Følgende procedure beskriver, hvordan du konfigurerer standardpolitikken for phishing. Indstillinger, der kun er tilgængelige i Defender for Office 365, er tydeligt markeret.

1. Åbn **siden antiphishing** i Microsoft 365 Defender på <https://security.microsoft.com/antiphishing>.

2. På siden **Antiphishing** skal du vælge politikken **Office365 AntiPhish Default (standard)** ved at klikke på navnet.

3. I pop op-vindue med politikoplysninger, der vises, skal du konfigurere følgende indstillinger:
   - **Grænseværdi for & for phishing** : Klik **på Rediger beskyttelsesindstillinger** , og konfigurer følgende indstillinger i pop op-menuen, der åbnes:
     - **Grænseværdi for phishing-mail**<sup>\*</sup>**: Vælg 2 - Aggressive** (standard) **eller 3 - Mere aggressive** (streng).
     - **Repræsentationssektion**<sup>\*</sup>: Konfigurer følgende værdier:
       - **Vælg Gør** det muligt for brugere at beskytte, klik på linket Administrer **afsendere (nn),** der vises, og tilføj derefter interne og eksterne afsendere for at beskytte mod efterligning, f.eks. organisationens tavlemedlemmer, den administrerende direktør, CFO og andre ledende ledere.
       - Vælg **Aktivér domæner, der skal beskyttes**, og konfigurer derefter følgende indstillinger, der vises:
         - Vælg **Medtag domæner, jeg ejer** for at beskytte interne afsendere på dine accepterede domæner (kan ses ved at klikke på Vis mine **domæner) mod** efterligning.
         - Hvis du vil beskytte afsendere på andre domæner, skal du vælge Medtag brugerdefinerede **domæner, klikke** på linket Administrer **(nn) brugerdefinerede domæne(r),** der vises, og derefter tilføje andre domæner for at beskytte mod efterligning.
     - **Tilføj sektionen**<sup>\*</sup> Afsendere og domæner, der er tillid til: Klik på Administrer **(nn)** afsendere, der er tillid til, og domæner for at konfigurere undtagelser fra afsender- og afsenderdomæner til repræsentationsbeskyttelse, hvis det er nødvendigt.
     - Indstillinger for postkasseintelligens <sup>\*</sup>: Kontrollér, **at Aktivér** postkasseintelligens og **Aktivér intelligens til repræsentationsbeskyttelse** er markeret.
     - **Spoof-sektion** : **Bekræft, at Aktivér efterlignet intelligens** er markeret.

     Klik på **Gem**, når du er færdig.

   - **Sektionen** Handlinger: Klik **på Rediger handlinger** , og konfigurer følgende indstillinger i pop op-menuen, der åbnes:
     - **Sektionen Meddelelseshandlinger** : Konfigurer følgende indstillinger:
       - **Hvis meddelelsen registreres som en efterligning af en bruger**<sup>\*</sup>: Vælg **Sæt meddelelsen i karantæne**. Der **vises et anvend karantænepolitikfelt**, hvor du [](quarantine-policies.md) vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af bruger efterligningsbeskyttelse.
       - **Hvis meddelelsen registreres som et efterligning af domæne**<sup>\*</sup>: Vælg **Sæt meddelelsen i karantæne**. Der **vises et anvend karantænepolitikfelt**, hvor du [](quarantine-policies.md) vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af domænebeskyttelse.
       - **Hvis postkassens intelligens registrerer**<sup>\*</sup> en efterligning af en bruger: Vælg Flyt meddelelsen til **modtagernes** mapper med Uønsket mail (Standard) eller **Sæt** meddelelsen i karantæne (Streng). Hvis du vælger **Karantæne i** meddelelsen, vises  der et anvend karantænepolitikfelt, hvor du [](quarantine-policies.md) vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af postkassens intelligencebeskyttelse.
       - **Hvis meddelelsen registreres som efterlignet**: Vælg Flyt meddelelsen til **modtagernes** mapper med Uønsket mail (Standard) eller Sæt meddelelsen i **karantæne (Streng** ).  Hvis du vælger **Karantæne for** meddelelsen, vises  der et anvend karantænepolitikfelt, hvor du [](quarantine-policies.md) vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af efterlignet intelligencebeskyttelse.
     - **Sektionen Sikkerhedstip &** Indikatorer: Konfigurer følgende indstillinger:
       - **Vis den første sikkerhedstip**: Vælg (slå til).
       - **Vis bruger efterligning sikkerhedstip**<sup>\*</sup>: Vælg (slå til).
       - **Vis domænepersonation sikkerhedstip**<sup>\*</sup>: Vælg (slå til).
       - **Vis bruger efterligning af usædvanlige tegn sikkerhedstip**<sup>\*</sup>: Vælg (slå til).
       - **Vis (?) for ikke-godkendte afsendere for spoof**: Vælg (slå til).
       - **Vis "via"-mærke**: Vælg (slå til).

     Klik på **Gem**, når du er færdig.

   <sup>\*</sup>Denne indstilling er kun tilgængelig i Defender for Office 365.

4. Klik **på Gem** , og klik derefter på **Luk**

Hvis du vil have en detaljeret vejledning til konfiguration af antiphishing-politikker, skal du se Konfigurer antiphishing-politikker i [EOP](configure-anti-phishing-policies-eop.md) og Konfigurer [antiphishing-politikker Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="part-3---anti-spam-protection-in-eop"></a>Del 3 – Beskyttelse mod spam i EOP

Du kan finde flere oplysninger om de anbefalede indstillinger for antispam i [Politikindstillinger for EOP-antispam](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings).

1. Åbn siden **Antispampolitikker** i Microsoft 365 Defender på <https://security.microsoft.com/antispam>.

2. På siden **Politikker for uønsket** post skal du vælge politikken for **indgående uønsket post på** listen ved at klikke på navnet.

3. I pop op-vindue med politikoplysninger, der vises, skal du konfigurere følgende indstillinger:
   - **Grænseværdi for massemail & sektionen Egenskaber for** spam: Klik på **Rediger grænseværdi for spam og egenskaber**. I pop op-menuen, der vises, skal du konfigurere følgende indstillinger:
     - **Grænseværdi for massemail**: Angiv denne værdi til 5 (streng) eller 6 (standard).
     - Lad andre indstillinger være ved standardværdierne (**Fra** eller **Ingen**).

     Klik på **Gem**, når du er færdig.

   - **Sektionen** Handlinger: Klik på **Rediger handlinger**. I pop op-menuen, der vises, skal du konfigurere følgende indstillinger:
     - **Sektionen Meddelelseshandlinger** :
       - **Spam**: Bekræft **, at Flyt meddelelsen til mappen Uønsket** mail er valgt (Standard), eller vælg **Karantænemeddelelse** (Streng).
       - **Spam med høj tillid**: Vælg **en meddelelse i karantæne**.
       - **Phishing**: Vælg **en meddelelse i karantæne**.
       - **Phishing med høj tillid**: **Bekræft, at meddelelser i karantæne** er markeret.
       - **Masse**: Bekræft **, at Flyt meddelelsen til mappen Uønsket** mail er valgt (Standard), eller vælg **Karantænemeddelelse** (Streng).

       For hver handling, hvor du vælger  karantænemeddelelse **, vises** der et politikfelt afkrydsningsfeltet Vælg karantæne [](quarantine-policies.md), hvor du vælger den karantænepolitik, der gælder for meddelelser, der er sat i karantæne af beskyttelse mod spam.

     - **Bekræft spam i karantæne i dette antal dage**: Bekræft værdien **30** dage.
     - **Aktivér sikkerhedstip til spam**: Kontrollér, at denne indstilling er valgt (aktiveret).
     - **Aktivér automatisk tømning uden time (ZAP): Kontrollér**, at denne indstilling er valgt (aktiveret).
       - **Aktivér for phishingmeddelelser**: Kontrollér, at denne indstilling er valgt (aktiveret). Du kan finde flere oplysninger [i TØM (Zero-hour Auto Tømning) for phishing](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-phishing).
       - **Aktivér for spammeddelelser**: Kontrollér, at denne indstilling er valgt (aktiveret). Du kan finde flere oplysninger [i TØM (Zero-hour Auto Tømning) for spam](zero-hour-auto-purge.md#zero-hour-auto-purge-zap-for-spam).

     Klik på **Gem**, når du er færdig.

   - **Afsnittet Tilladte** og blokerede afsendere og domæner: Gennemse eller rediger dine tilladte afsendere og tilladte domæner som beskrevet i Opret lister over blokerede afsendere i [EOP](create-block-sender-lists-in-office-365.md) eller Opret lister over afsendere, der er tillid til i [EOP](create-safe-sender-lists-in-office-365.md).

     Klik på **Gem**, når du er færdig.

4. Klik på Luk, når du er **færdig**.

Hvis du vil have detaljerede oplysninger om konfiguration af antispampolitikker, skal [du se Konfigurer antispampolitikker i EOP](configure-your-spam-filter-policies.md).

## <a name="part-4---protection-from-malicious-urls-and-files-safe-links-and-safe-attachments-in-defender-for-office-365"></a>Del 4 – Beskyttelse mod skadelige URL-adresser og filer (Pengeskab links og vedhæftede Pengeskab i Defender for Office 365)

Time of click-beskyttelse mod skadelige URL-adresser og filer er tilgængelig i abonnementer, der [omfatter Microsoft Defender for Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Det er konfigureret via Pengeskab [vedhæftede filer](safe-attachments.md) [og Pengeskab Links-politikker](safe-links.md).

### <a name="safe-attachments-policies-in-microsoft-defender-for-office-365"></a>Pengeskab politikker for vedhæftede filer i Microsoft Defender for Office 365

Du kan finde flere oplysninger om de anbefalede indstillinger for Pengeskab vedhæftede filer i .[ Pengeskab indstillinger for vedhæftede filer](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

1. Åbn Pengeskab **vedhæftede** filer i Microsoft 365 Defender på <https://security.microsoft.com/safeattachmentv2>.

2. På siden **Pengeskab vedhæftede filer** skal du klikke **på Globale** indstillinger og derefter konfigurere følgende indstillinger i pop op-menuen, der vises:
   - **Slå indstillingen Defender for Office 365 for SharePoint, OneDrive og Microsoft Teams**: Slå denne indstilling til (![Til/fra).](../../media/scc-toggle-on.png)

     > [!IMPORTANT]
     > Før du slår Pengeskab Vedhæftede filer **til for SharePoint, OneDrive og Microsoft Teams,** skal du kontrollere, at overvågningslogføring er aktiveret i organisationen. Denne handling udføres typisk af en person, der har fået tildelt overvågningslogrollen Exchange Online. Få mere at vide under [Slå søgning i overvågningslog til eller fra](../../compliance/turn-audit-log-search-on-or-off.md)!

   - **Slå indstillingen Pengeskab Dokumenter til for Office** klienter: Aktiver denne indstilling (![Slå til.](../../media/scc-toggle-on.png)) Bemærk, at denne funktion kun er tilgængelig og giver mening med de nødvendige typer licenser. Du kan finde flere oplysninger [Pengeskab Dokumenter i Microsoft 365 E5](safe-docs.md).
   - **Tillad brugere at klikke gennem Beskyttet visning, selvom de Pengeskab filer**, der identificeres som skadelige: Bekræft, at denne indstilling er slået fra (![slå indstillingen fra](../../media/scc-toggle-off.png)).

   Når du er færdig, skal du klikke på **Gem**

3. Klik på **Pengeskab** på siden ![Vedhæftede filer](../../media/m365-cc-sc-create-icon.png).

4. I guiden **Opret Pengeskab politik for vedhæftede filer**, der åbnes, skal du konfigurere følgende indstillinger:
   - **Navngive din politikside** :
     - **Navn**: Angiv noget entydigt og beskrivende.
     - **Beskrivelse**: Angiv en valgfri beskrivelse.
   - **Siden Brugere og domæner**: Da dette er din første politik, og du sandsynligvis vil maksimere dækningen, skal du overveje [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) at angive dine accepterede domæner **i feltet** Domæner. Ellers kan du bruge felterne **Brugere og** **Grupper** for at få mere detaljeret kontrol. Du kan angive undtagelser ved at **vælge Udelad disse brugere, grupper og domæner** og angive værdier.
   - **Indstillinger** side:
     - **Pengeskab ukendt malwaresvar ved vedhæftede filer**: Vælg **Bloker**.
     - **Karantænepolitik**: Standardværdien er tom, hvilket betyder, at politikken AdminOnlyAccessPolicy bruges. Karantænepolitikker definerer, hvad brugerne kan gøre for meddelelser, der er sat i karantæne, og om brugerne modtager beskeder om karantæne. Du kan få mere at vide under [Karantænepolitikker](quarantine-policies.md).
     - **Omdiriger vedhæftede filer** med registrerede vedhæftede **filer:** Aktivér omdirigering: Slå denne indstilling til (vælg), og angiv en mailadresse for at modtage registrerede meddelelser.
     - **Anvend Pengeskab svar til registrering af vedhæftede filer, hvis scanningen ikke kan fuldføres (timeout** eller fejl): Kontrollér, at denne indstilling er valgt.

5. Når du er færdig, skal du klikke **på Send** og derefter klikke på **Udført**.

6. (Anbefalet) Som global administrator eller SharePoint **[Online-administrator skal du køre Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/Set-SPOTenant)** med parameteren _DisallowInfectedFileDownload_ `$true` angivet til i SharePoint Online PowerShell.
   - `$true` blokerer alle handlinger (undtagen Slet) for registrerede filer. Personer kan ikke åbne, flytte, kopiere eller dele registrerede filer.
   - `$false` blokerer alle handlinger undtagen Slet og Download. Folk kan vælge at acceptere risikoen og downloade en registreret fil.

7. Det kan tage op til 30 minutter, før dine ændringer er spredt ud Microsoft 365 alle datacentre.

Hvis du vil have detaljeret vejledning til konfiguration Pengeskab politikker for vedhæftede filer og globale indstillinger for Pengeskab vedhæftede filer, skal du se følgende emner:

- [Konfigurer Pengeskab Politikker for vedhæftede filer i Microsoft Defender for Office 365](set-up-safe-attachments-policies.md)
- [Slå vedhæftede Pengeskab til for SharePoint, OneDrive og Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md)
- [Sikre dokumenter i Microsoft 365 E5](safe-docs.md)

### <a name="safe-links-policies-in-microsoft-defender-for-office-365"></a>Pengeskab sammenkædede politikker i Microsoft Defender for Office 365

Du kan finde flere oplysninger om de anbefalede Pengeskab links under [Indstillinger Pengeskab Links](recommended-settings-for-eop-and-office365.md#safe-links-settings).

1. Åbn **Pengeskab Links** i Microsoft 365 Defender på <https://security.microsoft.com/safelinksv2>.

2. På siden **Pengeskab Links** skal du klikke **på Globale indstillinger** og derefter konfigurere følgende indstillinger i pop op-menuen, der vises:
   - **Indstillinger, der gælder for indhold i sektionen Office 365 understøttede apps**:
     - **Brug Pengeskab Links i Office 365 apps: Kontrollér**, at denne indstilling er slået til (![Slå til](../../media/scc-toggle-on.png)).
     - **Registrer ikke, hvornår brugere klikker på beskyttede links Office 365 følgende apps**: Slå denne indstilling fra (![Slå den fra).](../../media/scc-toggle-off.png)
     - **Lad ikke brugere klikke igennem til den oprindelige URL-adresse i Office 365-apps**: Bekræft, at denne indstilling er slået til (![til/fra).](../../media/scc-toggle-on.png)

   Når du er færdig, skal du klikke på **Gem**

3. Tilbage på siden **Pengeskab,** skal du klikke på ![Opret ikon.](../../media/m365-cc-sc-create-icon.png)

4. I guiden **Opret Pengeskab kæder,** der åbnes, skal du konfigurere følgende indstillinger:
   - **Navngive din politikside** :
     - **Navn**: Angiv noget entydigt og beskrivende.
     - **Beskrivelse**: Angiv en valgfri beskrivelse.
   - **Siden Brugere og domæner**: Da dette er din første politik, og du sandsynligvis vil maksimere dækningen, skal du overveje [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) at angive dine accepterede domæner **i feltet** Domæner. Ellers kan du bruge felterne **Brugere og** **Grupper** for at få mere detaljeret kontrol. Du kan angive undtagelser ved at **vælge Udelad disse brugere, grupper og domæner** og angive værdier.
   - **Url-& på siden med beskyttelsesindstillinger** :
     - **Handling på potentielt skadelige URL-adresser i sektionen** Mails:
       - **Til: Pengeskab kontrollerer en liste over kendte, skadelige links,** når brugere klikker på links i en mail: Vælg hans indstilling (slå til).
       - **Anvend Pengeskab links til mails, der sendes inden for organisationen**: Vælg denne indstilling (slå til).
       - **Anvend URL-adressescanning i realtid for mistænkelige links og links, der peger på filer**: Vælg denne indstilling (slå til).
       - **Vent på, at URL-adressen scannes, før meddelelsen** leveres: Markér denne indstilling (slå til).
       - **Undlad at omskrive URL-adresser, kontrollér kun via Pengeskab Links API**: Bekræft, at denne indstilling ikke er valgt (slå fra).
     - **Undlad at omskrive følgende URL-adresser i en mail**: Vi har ingen specifik anbefaling for denne indstilling. Få mere at vide under ["Omse ikke følgende URL-adresser"-lister i Pengeskab Links-politikker](safe-links.md#do-not-rewrite-the-following-urls-lists-in-safe-links-policies).
     - **Handling for potentielt skadelige URL-adresser i Microsoft Teams** sektion:
       - ***Til: Pengeskab kontrollerer en liste over kendte, skadelige links,** når brugere klikker på links i Microsoft Teams: Markér denne indstilling (slå til).
     - **Klik på sektionen Beskyttelsesindstillinger** :
       - **Registrere brugerklik**: Kontrollér, at denne indstilling er valgt (aktiveret).
       - **Lad brugere klikke igennem til den oprindelige URL-adresse**: Slå denne indstilling fra (ikke valgt).
       - **Vise organisationsbranding** på meddelelses- og advarselssider: Det er kun relevant at vælge denne indstilling (slå den til), når du har fulgt vejledningen i Tilpas [Microsoft 365-temaet for](../../admin/setup/customize-your-organization-theme.md) din organisation for at overføre dit firmalogo.
   - **Meddelelsesside** :
     - **Hvordan vil du give brugerne besked?** sektion: Du kan også vælge Brug brugerdefineret **meddelelsestekst for at** angive brugerdefineret meddelelsestekst, der skal bruges. Du kan også vælge **Brug Microsoft Oversætter til automatisk lokalisering for** at oversætte den brugerdefinerede meddelelsestekst til brugerens sprog. Ellers skal du **lade Brug standardmeddelelsesteksten være** markeret.

5. Når du er færdig, skal du klikke **på Send** og derefter klikke på **Udført**.

Hvis du vil have detaljeret vejledning til konfiguration Pengeskab links-politikker og globale indstillinger for Pengeskab Links, skal du se følgende emner:

- [Konfigurer Pengeskab links-politikker i Microsoft Defender for Office 365](set-up-safe-links-policies.md)
- [Konfigurere globale indstillinger for Pengeskab links i Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md)

### <a name="now-set-up-alerts-for-detected-files-in-sharepoint-online-or-onedrive-for-business"></a>Konfigurer nu beskeder for registrerede filer i SharePoint Online eller OneDrive for Business

Hvis du vil modtage en meddelelse, når en fil i SharePoint Online eller OneDrive for Business er blevet identificeret som skadelig, kan du konfigurere en besked som beskrevet i dette afsnit.

1. I portalen Microsoft 365 Defender på skal du <https://security.microsoft.com>gå til Politik for **& mailsamarbejde** \> **& politikker for besked** \> **om regler**.

2. Klik på **Ny beskedpolitik** på **siden Beskedpolitik**.

3. Guiden **Ny beskedpolitik** åbnes. På siden **Navn** skal du konfigurere følgende indstillinger:
   - **Navn**: Angiv et entydigt og beskrivende navn. Du kan f.eks. skrive Skadelige filer i biblioteker.
   - **Beskrivelse**: Angiv en valgfri beskrivelse.
   - **Alvorsgrad**: Vælg **Lav**, **Mellem** eller **Høj**.
   - **Kategori**: Vælg **Trusselsadministration**.

   Når du er færdig, skal du klikke på **Næste**

4. Konfigurer **følgende indstillinger på** siden Opret beskedindstillinger:
   - **Hvad vil du have besked om?** sektionen: **Aktivitet registreres** \> **malware i filen**.
   - **Hvordan skal beskeden udløses? Bekræft** , hver gang **en aktivitet stemmer overens med reglen** er markeret.

   Når du er færdig, skal du klikke på **Næste**

5. På siden **Angiv modtagere skal** du konfigurere følgende indstillinger:
   - **Send mailmeddelelser**: Kontrollér, at denne indstilling er valgt.
   - **Mailmodtagere**: Vælg en eller flere globale administratorer, sikkerhedsadministratorer eller sikkerhedslæsere, som skal modtage besked, når der registreres en skadelig fil.
   - **Daglig meddelelsesgrænse**: **Bekræft, at Ingen** grænse er markeret.

   Når du er færdig, skal du klikke på **Næste**

6. På siden **Gennemse dine indstillinger** skal du gennemse dine indstillinger, bekræfte, at Ja, slå det til med **det** samme er valgt, og derefter skal du klikke på **Udfør**

Du kan få mere at vide om beskedpolitikker [under Påmindelsespolitikker i Microsoft 365 Overholdelsescenter](../../compliance/alert-policies.md).

> [!NOTE]
> Når du er færdig med at konfigurere, kan du bruge disse links til at starte undersøgelser af arbejdsbelastningen:
>
> - [Statusrapport over trusselsbeskyttelse](view-email-security-reports.md#threat-protection-status-report)
> - [Brug portalen Microsoft 365 Defender til at administrere filer, der er sat i karantæne, i Defender for Office 365](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365)
> - [Hvad du skal gøre, når der findes en skadelig fil SharePoint Online, OneDrive eller Microsoft Teams](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2)
> - [Administrer meddelelser og filer i karantæne som administrator i Microsoft 365](manage-quarantined-messages-and-files.md)

## <a name="post-setup-tasks-and-next-steps"></a>Opgaver efter konfiguration og næste trin

Når du har konfigureret funktionerne til trusselsbeskyttelse, skal du sørge for at overvåge, hvordan disse funktioner fungerer! Gennemse og revidere dine politikker, så de gør det, du har brug for. Se også efter nye funktioner og tjenesteopdateringer, der kan tilføje værdi.

|Hvad kan du gøre?|Ressourcer til at få mere at vide|
|---|---|
|Se, hvordan funktioner til trusselsbeskyttelse fungerer for din organisation, ved at få vist rapporter|[Mailsikkerhedsrapporter](view-email-security-reports.md) <p> [Rapporter for Microsoft Defender for Office 365](view-reports-for-mdo.md) <p> [Threat Explorer](threat-explorer.md)|
|Med jævne mellemrum gennemse og revidere dine politikker for trusselsbeskyttelse efter behov|[Secure Score](../defender/microsoft-secure-score.md) <p> [Microsoft 365 funktioner til trusselsundersøgelse og svar](./office-365-ti.md)|
|Se efter nye funktioner og tjenesteopdateringer|[Standard og Målrettede udgivelsesindstillinger](../../admin/manage/release-options-in-office-365.md) <p> [Meddelelsescenter](../../admin/manage/message-center.md) <p> [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=advanced%2Cthreat%2Cprotection) <p> [Tjenestebeskrivelser](/office365/servicedescriptions/office-365-service-descriptions-technet-library)|
