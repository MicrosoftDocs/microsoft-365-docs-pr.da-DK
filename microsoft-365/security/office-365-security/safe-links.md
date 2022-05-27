---
title: Oversigt over komplette Pengeskab links for Microsoft Defender for Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
f1_keywords:
- "197503"
ms.date: 09/08/2021
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- ZVO160
- ZXL160
- ZPP160
- ZWD160
ms.assetid: dd6a1fef-ec4a-4cf4-a25a-bb591c5811e3
description: Få mere at vide om Pengeskab Links-beskyttelse i Defender for Office 365 til at beskytte en organisation mod phishing og andre angreb, der bruger skadelige URL-adresser. Find Teams Pengeskab Links, og se grafik af meddelelser om Pengeskab links.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4b518095404f22631533cbf7eff744a62a9c7bd1
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739887"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Pengeskab Links i Microsoft Defender for Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til erhvervskunder, der har [Microsoft Defender for Office 365](defender-for-office-365.md). Hvis du bruger Outlook.com, Microsoft 365 Family eller Microsoft 365 Personal, og du leder efter oplysninger om Safelinks i Outlook, skal du se [Avanceret Outlook.com-sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Pengeskab Links er en funktion i [Defender for Office 365](defender-for-office-365.md), der leverer URL-scanning og -omskrivning af indgående mails i et mailflow og bekræftelse af URL-adresser og links i mails og andre placeringer. Pengeskab Scanning af links finder sted i tillæg til de almindelige [anti-spam](anti-spam-protection.md) og [anti-malware](anti-malware-protection.md) i indgående mails i Exchange Online Protection (EOP). Pengeskab Scanning af links kan hjælpe med at beskytte din organisation mod skadelige links, der bruges i phishing og andre angreb.

Se denne korte video om, hvordan du beskytter mod skadelige links med Pengeskab Links i Microsoft Defender for Office 365.  
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGzjb]

Pengeskab Links-beskyttelse er tilgængelig på følgende placeringer:

- **Mails**: Selvom der ikke er nogen standardpolitik for Pengeskab links, giver den forudindstillede sikkerhedspolitik for indbygget **beskyttelse** Pengeskab Links-beskyttelse til alle modtagere (brugere, der ikke er defineret i brugerdefinerede politikker for Pengeskab links). Du kan få flere oplysninger [under Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender for Office 365](preset-security-policies.md). Du kan også oprette politikker for Pengeskab links, der gælder for bestemte brugere, grupper eller domæner. Du kan finde instruktioner under [Konfigurer politikker for Pengeskab links i Microsoft Defender for Office 365](set-up-safe-links-policies.md).

  Du kan få flere oplysninger om Pengeskab linksbeskyttelse af mails i afsnittet [Pengeskab Links-indstillinger for mails](#safe-links-settings-for-email-messages) senere i denne artikel.
  
  > [!NOTE]
  > Pengeskab Links fungerer ikke på mailaktiverede offentlige mapper.
  >
  > Pengeskab Links understøtter kun FORMATerne HTTP(S) og FTP.

- **Microsoft Teams**: Pengeskab linksbeskyttelse for links i Teams samtaler, gruppechats eller fra kanaler styres også af Pengeskab Links-politikker.

  Du kan få flere oplysninger om Pengeskab Links-beskyttelse i Teams i afsnittet [Pengeskab links til Microsoft Teams](#safe-links-settings-for-microsoft-teams) senere i denne artikel.

  > [!NOTE]
  > Pengeskab Links-beskyttelse for Microsoft Teams er i øjeblikket ikke tilgængelig i Microsoft 365 GCC High eller Microsoft 365 DoD.

- **Office 365 apps**: Pengeskab Links-beskyttelse for Office 365 apps er tilgængelig i understøttede skrivebords-, mobil- og webapps. Du **kan konfigurere** Pengeskab Links-beskyttelse for Office 365 apps i den globale indstilling, der er **uden for** Pengeskab Links-politikker. Du kan finde en vejledning under [Konfigurer globale indstillinger for Pengeskab Links-indstillinger i Microsoft Defender for Office 365](configure-global-settings-for-safe-links.md).

  Pengeskab Links-beskyttelse for Office 365 apps anvendes på alle brugere i organisationen, der har licens til Defender for Office 365, uanset om brugerne er inkluderet i aktive Pengeskab Links-politikker eller ej.

  Du kan få flere oplysninger om Pengeskab Links-beskyttelse i Office 365 apps i afsnittet [Pengeskab Linksindstillinger for Office 365 apps](#safe-links-settings-for-office-365-apps) senere i denne artikel.

Denne artikel indeholder detaljerede beskrivelser af følgende typer indstillinger for Pengeskab links:

- **Indstillinger i politikker for Pengeskab links**: Disse indstillinger gælder kun for de brugere, der er inkluderet i de specifikke politikker, og indstillingerne kan være forskellige fra politik til politik. Disse indstillinger omfatter:

  - [indstillinger for Pengeskab links til mails](#safe-links-settings-for-email-messages)
  - [indstillinger for Pengeskab links for Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - ["Undlad at omskrive følgende URL-adresser" på Pengeskab links-politikker](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Indstillinger for globale Pengeskab links**: Disse indstillinger er konfigureret globalt, ikke i Pengeskab Links-politikker. Disse indstillinger omfatter:

  - [indstillinger for Pengeskab links til Office 365 apps](#safe-links-settings-for-office-365-apps)
  - [Listen "Bloker følgende URL-adresser" for Pengeskab links](#block-the-following-urls-list-for-safe-links)

I følgende tabel beskrives scenarier for Pengeskab Links i Microsoft 365 og Office 365 organisationer, der omfatter Defender for Office 365 (bemærk, at manglende licenser aldrig er et problem i eksemplerne).

|Scenario|Resultat|
|---|---|
|Jean er medlem af marketingafdelingen. Pengeskab Links-beskyttelse for Office 365 apps er slået til i de globale indstillinger for Pengeskab Links, og der findes en politik for Pengeskab links, der gælder for medlemmer af marketingafdelingen. Jean åbner en PowerPoint præsentation i en mail og klikker derefter på en URL-adresse i præsentationen.|Jean er beskyttet af Pengeskab Links. <p> Jean er inkluderet i en politik for Pengeskab links, og Pengeskab Links-beskyttelse for Office 365 apps er slået til. <p> Du kan få flere oplysninger om kravene til beskyttelse af Pengeskab links i Office 365 apps i afsnittet [Pengeskab Links-indstillinger for Office 365 apps](#safe-links-settings-for-office-365-apps) senere i denne artikel.|
|Chris' Microsoft 365 E5 organisation har ikke konfigureret nogen Pengeskab links-politikker. Chris modtager en mail fra en ekstern afsender, der indeholder en URL-adresse til et skadeligt websted, som han i sidste ende klikker på.|Chris er ikke beskyttet af Pengeskab Links. <p> En administrator skal oprette mindst én Pengeskab politik for links, for at alle kan få Pengeskab Links-beskyttelse i indgående mails. Chris skal være inkluderet i betingelserne for politikken for at få Pengeskab Links-beskyttelse.|
|I Pats organisation har ingen administratorer oprettet nogen Pengeskab links-politikker, men Pengeskab Links-beskyttelse for Office 365 apps er slået til. Pat åbner et Word-dokument og klikker på en URL-adresse i filen.|Pat er ikke beskyttet af Pengeskab Links. <p> Selvom Pengeskab Links-beskyttelse for Office 365 apps er slået til globalt, er Pat ikke inkluderet i nogen aktive Pengeskab Links-politikker, så beskyttelsen kan ikke anvendes.|
|I Lees organisation `https://tailspintoys.com` er konfigureret på listen **Bloker følgende URL-adresser** i de globale indstillinger for Pengeskab Links. Der findes allerede en politik for Pengeskab Links, der indeholder Lee. Lee modtager en mail, der indeholder URL-adressen `https://tailspintoys.com/aboutus/trythispage`. Lee klikker på URL-adressen.|URL-adressen kan være blokeret automatisk for Lee. Det afhænger af URL-adressen på listen og den anvendte mailklient Lee. Du kan få flere oplysninger på [listen "Bloker følgende URL-adresser" for Pengeskab links](#block-the-following-urls-list-for-safe-links) senere i denne artikel.|
|Jamie og Julia arbejder begge for contoso.com. For lang tid siden konfigurerede administratorer Pengeskab Links-politikker, der gælder for både Jamie og Julia. Jamie sender en mail til Julia uden at vide, at mailen indeholder en skadelig URL-adresse.|Julia er beskyttet af Pengeskab Links **, hvis** politikken Pengeskab links, der gælder for hende, er konfigureret til at gælde for meddelelser mellem interne modtagere. Du kan få flere oplysninger i afsnittet [Pengeskab Links-indstillinger for mails](#safe-links-settings-for-email-messages) senere i denne artikel.|

## <a name="safe-links-settings-for-email-messages"></a>indstillinger for Pengeskab links til mails

Pengeskab Links scanner indgående mail for kendte skadelige links. Scannede URL-adresser omskrives ved hjælp af Præfikset for URL-adresser i Microsoft standard: `https://nam01.safelinks.protection.outlook.com`. Når linket er blevet omskrevet, analyseres det for potentielt skadeligt indhold.

Når Pengeskab links omskriver en URL-adresse, omskrives URL-adressen, selvom meddelelsen videresendes eller besvares _manuelt_ (både til interne og eksterne modtagere). Yderligere links, der føjes til den videresendte eller besvarede meddelelse, omskrives ikke. I tilfælde af _automatisk_ videresendelse efter indbakkeregler eller viderestilling af SMTP omskrives URL-adressen dog ikke i den meddelelse, der er beregnet til den endelige modtager, _medmindre_ den pågældende modtager også er beskyttet af Pengeskab Links, eller URL-adressen allerede er blevet omskrevet i en tidligere meddelelse. Så længe Pengeskab Links er aktiveret, scannes URL-adresser stadig før levering, uanset om de er blevet omskrevet eller ej. Ikke-ombrudte URL-adresser kontrolleres også stadig af et API-kald på klientsiden for at Pengeskab Links, når der klikkes på Outlook til Desktop version 16.0.12513 eller nyere.

Indstillingerne i Pengeskab Links-politikker, der gælder for mails, er beskrevet på følgende liste:

- **På: Pengeskab Links kontrollerer en liste over kendte, skadelige links, når brugerne klikker på links i mail**: Aktiverer eller deaktiverer Pengeskab Links scanning i mails. Den anbefalede værdi er valgt (slået til) og resulterer i følgende handlinger:
  - scanning af Pengeskab links er aktiveret i Outlook (C2R) på Windows.
  - URL-adresser omskrives, og brugerne dirigeres via Pengeskab Links-beskyttelse, når de klikker på URL-adresser i meddelelser.
  - Når der klikkes på URL-adresserne, kontrolleres de i forhold til en liste over kendte skadelige URL-adresser og [listen "Bloker følgende URL-adresser"](#block-the-following-urls-list-for-safe-links).
  - URL-adresser, der ikke har et gyldigt omdømme, detoneres asynkront i baggrunden.

  Følgende indstillinger er kun tilgængelige, hvis scanning af Pengeskab links er slået til i mails:

  - **Anvend Pengeskab Links til mails, der er sendt i organisationen**: Aktiverer eller deaktiverer scanning af Pengeskab links i meddelelser, der sendes mellem interne afsendere og interne modtagere i den samme Exchange Online organisation. Den anbefalede værdi er valgt (slået til).

  - **Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer**: Aktiverer scanning i realtid af links, herunder links i mails, der peger på indhold, der kan downloades. Den anbefalede værdi er valgt (slået til).

  - **Vent på, at scanningen af URL-adressen fuldføres, før meddelelsen leveres**:
    - Valgt (slået til): Meddelelser, der indeholder URL-adresser, gemmes, indtil scanningen er fuldført. Meddelelser leveres først, når URL-adresserne er bekræftet til at være sikre. Dette er den anbefalede værdi.
    - Ikke valgt (slået fra): Hvis scanningen af URL-adressen ikke kan fuldføres, skal du levere meddelelsen alligevel.

  - **Undlad at omskrive URL-adresser. Kontroller kun via SafeLinks API**: Hvis denne indstilling er aktiveret, sker der ingen OMbrydning af URL-adresser. Pengeskab Links kaldes udelukkende via API'er på det tidspunkt, hvor URL-adressen klikkes af Outlook klienter, der understøtter den. Anbefalet værdi er deaktiveret.

- **Spor bruger clicks**: Aktiverer eller deaktiverer lagring af Pengeskab Links klikdata for URL-adresser, der klikkes på i mails. Anbefalet værdi er at lade denne indstilling være markeret (spor bruger klik).

  Sporing af URL-klik for links i mails, der sendes mellem interne afsendere og interne modtagere, understøttes ikke i øjeblikket.

- **Lad brugerne klikke sig videre til den oprindelige URL-adresse**: Tillader eller blokerer brugere fra at klikke gennem [advarselssiden](#warning-pages-from-safe-links) til den oprindelige URL-adresse. Anbefalet værdi er deaktiveret.

- **Vis organisationsbranding på meddelelses- og advarselssider**: Denne indstilling viser organisationens branding på advarselssider. Branding hjælper brugerne med at identificere legitime advarsler, fordi Microsofts standardadvarselssider ofte bruges af hackere. Du kan få flere oplysninger om brugerdefineret branding under [Tilpas temaet Microsoft 365 for din organisation](../../admin/setup/customize-your-organization-theme.md).

  Du kan få flere oplysninger om de anbefalede værdier for Standard- og Strict-politikindstillinger for politikker for Pengeskab Links under [Pengeskab Politikindstillinger for links](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- **Modtagerfiltre**: Du skal angive de betingelser og undtagelser for modtageren, der bestemmer, hvem politikken gælder for. Du kan bruge disse egenskaber til betingelser og undtagelser:
  - **Modtageren er**
  - **Modtagerdomænet er**
  - **Modtageren er medlem af**

  Du kan kun bruge en betingelse eller undtagelse én gang, men betingelsen eller undtagelsen kan indeholde flere værdier. Flere værdier med samme betingelse eller undtagelse bruger OR-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

- **Prioritet**: Hvis du opretter flere politikker, kan du angive den rækkefølge, de anvendes i. Der kan ikke være to politikker, der har samme prioritet, og behandlingen af politikker stopper, når den første politik er anvendt.

  Du kan finde flere oplysninger om prioritetsrækkefølgen, og hvordan flere politikker evalueres og anvendes, under [Beskyttelse af mailrækkefølge og prioritet](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Sådan fungerer Pengeskab links i mails

På et højt niveau kan du se, hvordan beskyttelse af Pengeskab links fungerer på URL-adresser i mails:

1. Alle mails går gennem EOP, hvor internetprotokol (IP) og konvolutfiltre, signaturbaseret malwarebeskyttelse, anti-spam- og antimalwarefiltre, før meddelelsen leveres til modtagerens postkasse.

2. Brugeren åbner meddelelsen i sin postkasse og klikker på en URL-adresse i meddelelsen.

3. Pengeskab Links kontrollerer straks URL-adressen, før webstedet åbnes:

   - Hvis URL-adressen er inkluderet på listen **Bloker følgende URL-adresser** , åbnes der en [advarsel om blokeret URL-adresse](#blocked-url-warning) .

   - Hvis URL-adressen peger på et websted, der er blevet fastslået som skadeligt, åbnes der en [advarselsside for et skadeligt websted](#malicious-website-warning) (eller en anden advarselsside).

   - Hvis URL-adressen peger på en fil, der kan downloades, og indstillingen **Anvend URL-adressescanning i realtid for mistænkelige links og links, der peger på filer** , er aktiveret i den politik, der gælder for brugeren, kontrolleres den fil, der kan downloades.

   - Hvis URL-adressen er bestemt til at være sikker, åbnes webstedet.

## <a name="safe-links-settings-for-microsoft-teams"></a>indstillinger for Pengeskab links for Microsoft Teams

Du aktiverer eller deaktiverer Pengeskab Links-beskyttelse for Microsoft Teams i politikker for Pengeskab links. Du bruger specifikt **indstillingen Vælg handlingen for ukendte eller potentielt skadelige URL-adresser i Microsoft Teams**. Den anbefalede værdi er **Slået til**.

> [!NOTE]
> Når du slår Pengeskab Links-beskyttelse til eller fra for Teams, kan det tage op til 24 timer, før ændringen træder i kraft.
>
> Pengeskab Links-beskyttelse for Microsoft Teams er i øjeblikket ikke tilgængelig i Microsoft 365 GCC High eller Microsoft 365 DoD.

Følgende indstillinger i Pengeskab linkspolitikker, der gælder for links i mails, gælder også for links i Teams:

- **Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer**
- **Spor ikke bruger klik**
- **Tillad ikke, at brugerne klikker sig igennem til den oprindelige URL-adresse**

Disse indstillinger er tidligere forklaret i [Pengeskab Indstillinger for links til mails](#safe-links-settings-for-email-messages).

Når du har slået beskyttelse af Pengeskab Links til for Microsoft Teams, kontrolleres URL-adresser i Teams mod en liste over kendte skadelige links, når den beskyttede bruger klikker på linket (beskyttelsestid for klik). URL-adresser omskrives ikke. Hvis det konstateres, at et link er skadeligt, får brugerne følgende oplevelser:

- Hvis der klikkes på linket i en Teams samtale, gruppechat eller fra kanaler, vises advarselssiden som vist på skærmbilledet nedenfor i standardwebbrowseren.
- Hvis der klikkes på linket fra en fastgjort fane, vises advarselssiden i grænsefladen Teams under den pågældende fane. Muligheden for at åbne linket i en webbrowser er deaktiveret af sikkerhedsmæssige årsager.
- Afhængigt af hvordan indstillingen **Tillad ikke brugere at klikke sig igennem til den oprindelige URL-adresse** i politikken er konfigureret, vil brugeren eller vil ikke få tilladelse til at klikke sig igennem til den oprindelige URL-adresse (**Fortsæt alligevel (anbefales ikke) på skærmbilledet** . Vi anbefaler, at du aktiverer indstillingen **Tillad ikke, at brugere klikker sig videre til den oprindelige URL-adresse,** så brugerne ikke kan klikke sig videre til den oprindelige URL-adresse.

Hvis den bruger, der har sendt linket, ikke er inkluderet i en politik for Pengeskab links, hvor Teams beskyttelse er aktiveret, kan brugeren frit klikke sig videre til den oprindelige URL-adresse på sin computer eller enhed.

:::image type="content" source="../../media/tp-safe-links-for-teams-malicious.png" alt-text="Et Pengeskab Links til Teams side, der rapporterer et skadeligt link" lightbox="../../media/tp-safe-links-for-teams-malicious.png":::

Hvis du klikker på knappen **Gå tilbage** på advarselssiden, vender brugeren tilbage til den oprindelige kontekst eller url-adresseplacering. Hvis du klikker på det oprindelige link igen, vil det dog medføre, at Pengeskab Links scanner URL-adressen igen, så advarselssiden vises igen.

### <a name="how-safe-links-works-in-teams"></a>Sådan fungerer Pengeskab links i Teams

På et højt niveau kan du se, hvordan beskyttelse af Pengeskab links fungerer for URL-adresser i Microsoft Teams:

1. En bruger starter appen Teams.

2. Microsoft 365 kontrollerer, at brugerens organisation inkluderer Microsoft Defender for Office 365, og at brugeren er inkluderet i en aktiv politik for Pengeskab Links, hvor beskyttelse af Microsoft Teams er aktiveret.

3. URL-adresser valideres, når brugeren klikker, i chats, gruppechats, kanaler og faner.

## <a name="safe-links-settings-for-office-365-apps"></a>indstillinger for Pengeskab links til Office 365 apps

Pengeskab Linkbeskyttelse for Office 365 apps kontrollerer links i Office dokumenter, ikke links i mails (men det kan kontrollere links i vedhæftede Office dokumenter i mails, når dokumentet er åbnet).

Pengeskab Links-beskyttelse for Office 365 apps har følgende klientkrav:

- Microsoft 365 Apps eller Microsoft 365 Business Premium.
  - Aktuelle versioner af Word, Excel og PowerPoint på Windows, Mac eller i en webbrowser.
  - Office apps på iOS- eller Android-enheder.
  - Visio på Windows.
  - OneNote i en webbrowser.
  - Outlook til Windows, når du åbner gemte EML- eller MSG-filer.

- Office 365 apps er konfigureret til at bruge moderne godkendelse. Du kan få flere oplysninger under [Sådan fungerer moderne godkendelse for Office 2013, Office 2016 og Office 2019-klientapps](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Brugerne er logget på med deres arbejds- eller skolekonti. Du kan få flere oplysninger under [Log på Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Du kan konfigurere Pengeskab Links-beskyttelse for Office 365 apps i de globale indstillinger for Pengeskab Links, ikke i politikker for Pengeskab links. Beskyttelsen anvendes på alle brugere i organisationen, der har licens til Defender for Office 365, uanset om brugerne er inkluderet i aktive Pengeskab Links-politikker eller ej.

Følgende indstillinger for Pengeskab Links er tilgængelige for Office 365 apps:

- **Office 365 programmer**: Aktiverer eller deaktiverer scanning af Pengeskab links i understøttede Office 365 apps. Standardværdien og den anbefalede værdi er **Slået til**.

- **Spor ikke, når brugere klikker på Pengeskab links**: Aktiverer eller deaktiverer lagring af Pengeskab Links klikker på data for URL-adresser, der klikkes på i desktopversionerne Word, Excel, PowerPoint og Visio. Den anbefalede værdi er **Fra**, hvilket betyder, at bruger klik spores.

- **Lad ikke brugere klikke gennem sikre links til den oprindelige URL-adresse**: Tillader eller blokerer brugere fra at klikke gennem [advarselssiden](#warning-pages-from-safe-links) til den oprindelige URL-adresse i desktopversionerne Word, Excel, PowerPoint og Visio. Standardværdien og den anbefalede værdi er **Slået til**.

Hvis du vil konfigurere indstillingerne for Pengeskab links for Office 365 apps, skal du se [Konfigurer Pengeskab Links-beskyttelse for Office 365 apps](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Du kan få flere oplysninger om de anbefalede værdier for Standard- og Strict-politikindstillinger under [Globale indstillinger for Pengeskab Links](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-365-apps"></a>Sådan fungerer Pengeskab links i Office 365 apps

På et højt niveau kan du se, hvordan beskyttelse af Pengeskab links fungerer for URL-adresser i Office 365 apps. De understøttede Office 365 apps er beskrevet i forrige afsnit.

1. En bruger logger på med at bruge sin arbejds- eller skolekonto i en organisation, der omfatter Microsoft 365 Apps eller Microsoft 365 Business Premium.

2. Brugeren åbner og klikker på et link til et Office dokument i et understøttet Office-app.

3. Pengeskab Links kontrollerer straks URL-adressen, før destinationswebstedet åbnes:

   - Hvis URL-adressen er inkluderet på den liste, der springer Pengeskab scanning af links (listen **Bloker følgende URL-adresser**), åbnes der en [advarselsside for blokeret URL-adresse](#blocked-url-warning).

   - Hvis URL-adressen peger på et websted, der er blevet fastslået som skadeligt, åbnes der en [advarselsside for et skadeligt websted](#malicious-website-warning) (eller en anden advarselsside).

   - Hvis URL-adressen peger på en fil, der kan downloades, og politikken for Pengeskab links, der gælder for brugeren, er konfigureret til at scanne links til indhold, der kan downloades (**Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer**), kontrolleres den fil, der kan downloades.

   - Hvis URL-adressen betragtes som sikker, føres brugeren til webstedet.

   - Hvis scanningen af Pengeskab links ikke kan fuldføres, udløses beskyttelsen Pengeskab Links ikke. I Office desktopklienter bliver brugeren advaret, før vedkommende fortsætter til destinationswebstedet.

> [!NOTE]
> Det kan tage flere sekunder i starten af hver session at bekræfte, at brugeren har Pengeskab Links for Office aktiveret.

## <a name="block-the-following-urls-list-for-safe-links"></a>Listen "Bloker følgende URL-adresser" for Pengeskab links

Listen **Bloker følgende URL-adresser** definerer de links, der altid blokeres af scanning af Pengeskab links på følgende placeringer:

- Mailmeddelelser.
- Dokumenter i Office 365 apps i Windows og Mac.
- Dokumenter i Office til iOS og Android.

Når en bruger i en aktiv Pengeskab politik for links klikker på et blokeret link i en understøttet app, føres vedkommende til [advarselssiden blokeret URL-adresse](#blocked-url-warning).

Du kan konfigurere listen over URL-adresser i de globale indstillinger for Pengeskab Links. Du kan finde instruktioner [på listen "Bloker følgende URL-adresser"](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal).

**Noter**:

- Du kan se en virkelig universel liste over URL-adresser, der er blokeret overalt, [under Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md).
- Grænser for listen **Bloker følgende URL-adresser** :
  - Det maksimale antal poster er 500.
  - Den maksimale længde på en post er 128 tegn.
  - Alle posterne må ikke overstige 10.000 tegn.
- Medtag ikke en skråstreg (`/`) i slutningen af URL-adressen. Brug f.eks. `https://www.contoso.com`, ikke `https://www.contoso.com/`.
- En URL-adresse, der kun er beregnet til domænet (f.eks `contoso.com` . eller `tailspintoys.com`), blokerer alle URL-adresser, der indeholder domænet.
- Du kan blokere et underdomæne uden at blokere hele domænet. Blokerer f.eks. enhver URL-adresse, `toys.contoso.com*` der indeholder underdomænet, men den blokerer ikke URL-adresser, der indeholder hele domænet `contoso.com`.
- Du kan inkludere op til tre jokertegn (`*`) pr. URL-adresse.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Postsyntaksen for listen "Bloker følgende URL-adresser"

Eksempler på de værdier, du kan angive, og deres resultater er beskrevet i følgende tabel:

|Værdi|Resultat|
|---|---|
|`contoso.com` <p> Eller <p> `*contoso.com*`|Blokerer domænet, underdomænerne og stierne. For eksempel `https://www.contoso.com`er , `https://sub.contoso.com`og `https://contoso.com/abc` blokeret.|
|`https://contoso.com/a`|Blokke `https://contoso.com/a` , men ikke yderligere understier som `https://contoso.com/a/b`.|
|`https://contoso.com/a*`|Blokke `https://contoso.com/a` og yderligere understier, f.eks `https://contoso.com/a/b`. .|
|`https://toys.contoso.com*`|Blokerer et underdomæne (`toys` i dette eksempel), men tillader klik til andre domæne-URL-adresser (f.eks `https://contoso.com` . eller `https://home.contoso.com`).|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>"Undlad at omskrive følgende URL-adresser" på Pengeskab links-politikker

> [!NOTE]
> Hvis din organisation bruger politikker for Pengeskab links, er **listerne Overskriv ikke følgende URL-adresser** den eneste understøttede metode til phishing-test fra tredjepart.

Hver Pengeskab links-politik indeholder en **Omskriv ikke følgende URL-adresseliste**, som du kan bruge til at angive URL-adresser, der ikke omskrives af Pengeskab Scanning af links. Listen gør det med andre ord muligt for brugere, der er inkluderet i politikken, at få adgang til de angivne URL-adresser, der ellers ville blive blokeret af Pengeskab Links. Du kan konfigurere forskellige lister i forskellige Pengeskab Links-politikker. Politikbehandlingen stopper, når den første politik (sandsynligvis den højeste prioritet) er anvendt på brugeren. Derfor anvendes kun én liste over **Undlad at omskrive følgende URL-adresser** for en bruger, der er inkluderet i flere aktive Pengeskab Links-politikker.

Hvis du vil føje poster til listen i nye eller eksisterende Pengeskab Links-politikker, skal du se [Opret politikker for Pengeskab links](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) eller [Rediger Pengeskab Links-politikker](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Noter**:

- Følgende klienter genkender ikke følgende **URL-adresser** i Pengeskab links-politikker. Brugere, der er inkluderet i politikkerne, kan blokeres, så de ikke kan få adgang til URL-adresserne baseret på resultaterne af scanningen af Pengeskab links i disse klienter:
  - Microsoft Teams
  - Office webapps

  Hvis du vil have en virkelig universel liste over URL-adresser, der er tilladt overalt, skal du se [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md). Bemærk dog, at URL-adresser, der tilføjes der, ikke udelukkes fra omskrivning af Pengeskab Links, da det skal gøres i en politik for Pengeskab Links.

- Overvej at føje almindeligt anvendte interne URL-adresser til listen for at forbedre brugeroplevelsen. Hvis du f.eks. har tjenester i det lokale miljø, f.eks. Skype for Business eller SharePoint, kan du tilføje disse URL-adresser for at udelukke dem fra scanning.
- Hvis du allerede har **Omskriv ikke følgende URL-adresser** i dine Pengeskab Links-politikker, skal du sørge for at gennemse listerne og tilføje jokertegn efter behov. Listen har f.eks. et element som `https://contoso.com/a` , og du beslutter senere at inkludere understier som `https://contoso.com/a/b`. I stedet for at tilføje en ny post skal du føje et jokertegn til den eksisterende post, så den bliver `https://contoso.com/a/*`til .
- Du kan inkludere op til tre jokertegn (`*`) pr. URL-adresse. Jokertegn indeholder eksplicit præfikser eller underdomæner. Posten `contoso.com` er f.eks. ikke den samme som `*.contoso.com/*`, fordi `*.contoso.com/*` giver brugerne mulighed for at besøge underdomæner og stier i det angivne domæne.
- Hvis en URL-adresse bruger automatisk omdirigering for HTTP til HTTPS (f.eks. 302-omdirigering for `http://www.contoso.com` til `https://www.contoso.com`), og du forsøger at angive både HTTP- og HTTPS-poster for den samme URL-adresse på listen, vil du måske bemærke, at den anden URL-adresse erstatter den første URL-adresse. Denne funktionsmåde opstår ikke, hvis HTTP- og HTTPS-versionerne af URL-adressen er helt separate.
- Angiv ikke http:// eller https:// (dvs. contoso.com) for at udelade både HTTP- og HTTPS-versioner.
- `*.contoso.com` dækker **ikke** contoso.com, så du skal udelukke både for at dække både det angivne domæne og eventuelle underordnede domæner.
- `contoso.com/*` dækker **kun** contoso.com, så der er ingen grund til at udelukke både `contoso.com` og `contoso.com/*`; bare `contoso.com/*` ville være tilstrækkeligt.
- Hvis du vil udelade alle gentagelser af et domæne, kræves der to udeladelsesposter. `contoso.com/*` og .`*.contoso.com/*` Disse kombineres for at udelade både HTTP og HTTPS, det primære domæne contoso.com og eventuelle underordnede domæner samt en del, der ikke slutter (f.eks. dækkes både contoso.com og contoso.com/vdir1).

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Postsyntaksen for listen "Omskriv ikke følgende URL-adresser"

Eksempler på de værdier, du kan angive, og deres resultater er beskrevet i følgende tabel:

|Værdi|Resultat|
|---|---|
|`contoso.com`|Giver adgang til `https://contoso.com` , men ikke underdomæner eller stier.|
|`*.contoso.com/*`|Giver adgang til et domæne, underdomæner og stier (f.eks. `https://www.contoso.com`, `https://www.contoso.com`, `https://maps.contoso.com`eller `https://www.contoso.com/a`). <p> Denne post er i sagens natur bedre end `*contoso.com*`, fordi den ikke tillader potentielt falske websteder, f.eks `https://www.falsecontoso.com` . eller `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Giver adgang til `https://contoso.com/a`, men ikke understier som `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Giver adgang til `https://contoso.com/a` og understier som `https://contoso.com/a/b`|

## <a name="warning-pages-from-safe-links"></a>Advarselssider fra Pengeskab links

Dette afsnit indeholder eksempler på de forskellige advarselssider, der udløses af Pengeskab Links-beskyttelse, når du klikker på en URL-adresse.

Bemærk, at flere advarselssider er blevet opdateret. Hvis du ikke allerede får vist de opdaterede sider, kommer du snart. De opdaterede sider indeholder et nyt farveskema, flere detaljer og muligheden for at gå videre til et websted på trods af den angivne advarsel og anbefalinger.

### <a name="scan-in-progress-notification"></a>Meddelelse om scanning i gang

Den URL-adresse, der klikkes på, scannes af Pengeskab Links. Du skal muligvis vente et øjeblik, før du prøver linket igen.

:::image type="content" source="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png" alt-text="Meddelelsen om, at linket scannes" lightbox="../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png":::

Den oprindelige meddelelsesside så sådan ud:

:::image type="content" source="../../media/04368763-763f-43d6-94a4-a48291d36893.png" alt-text="Linket bliver scannet meddelelse" lightbox="../../media/04368763-763f-43d6-94a4-a48291d36893.png":::

### <a name="suspicious-message-warning"></a>Advarsel om mistænkelig meddelelse

Den URL-adresse, der blev klikket på, var i en mail, der ligner andre mistænkelige meddelelser. Vi anbefaler, at du dobbelttjekke mailen, før du fortsætter til webstedet.

:::image type="content" source="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png" alt-text="Der blev klikket på et link fra en mistænkelig meddelelsesadvarsel" lightbox="../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png":::

### <a name="phishing-attempt-warning"></a>Advarsel om phishingforsøg

Den URL-adresse, der blev klikket på, var i en mail, der er blevet identificeret som et phishing-angreb. Derfor blokeres alle URL-adresser i mailen. Vi anbefaler, at du ikke fortsætter til webstedet.

:::image type="content" source="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png" alt-text="Advarslen om, at der blev klikket på et link fra en phishingmeddelelse" lightbox="../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png":::

### <a name="malicious-website-warning"></a>Advarsel om skadeligt websted

Den url-adresse, der klikkes på, peger på et websted, der er blevet identificeret som skadeligt. Vi anbefaler, at du ikke fortsætter til webstedet.

:::image type="content" source="../../media/058883c8-23f0-4672-9c1c-66b084796177.png" alt-text="Advarslen, der hedder, at hjemmesiden er klassificeret som ondsindet" lightbox="../../media/058883c8-23f0-4672-9c1c-66b084796177.png":::

Den oprindelige advarselsside så sådan ud:

:::image type="content" source="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png" alt-text="Den oprindelige advarsel, der hedder, at hjemmesiden er klassificeret som ondsindet" lightbox="../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png":::

### <a name="blocked-url-warning"></a>Advarsel om blokeret URL-adresse

Den url-adresse, der klikkes på, er blevet blokeret manuelt af en administrator i din organisation (listen **Bloker følgende URL-adresser** i de globale indstillinger for Pengeskab Links). Linket blev ikke scannet af Pengeskab Links, fordi det blev blokeret manuelt.

Der er flere grunde til, at en administrator manuelt blokerer bestemte URL-adresser. Hvis du mener, at webstedet ikke skal blokeres, skal du kontakte din administrator.

:::image type="content" source="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png" alt-text="Advarslen om, at webstedet blev blokeret af administratoren" lightbox="../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png":::

Den oprindelige advarselsside så sådan ud:

:::image type="content" source="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png" alt-text="Den oprindelige advarsel om, at webstedet er blevet blokeret i henhold til organisationens URL-politik" lightbox="../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png":::

### <a name="error-warning"></a>Fejladvarsel

Der opstod en form for fejl, og URL-adressen kan ikke åbnes.

:::image type="content" source="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png" alt-text="Advarslen om, at den side, du forsøger at få adgang til, ikke kan indlæses" lightbox="../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png":::

Den oprindelige advarselsside så sådan ud:

:::image type="content" source="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png" alt-text="Advarslen om, at websiden ikke kunne indlæses" lightbox="../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png":::
