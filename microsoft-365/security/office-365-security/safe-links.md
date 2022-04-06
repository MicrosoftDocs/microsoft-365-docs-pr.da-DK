---
title: Fuldfør Pengeskab Links-oversigt for Microsoft Defender Office 365
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
description: Få mere at Pengeskab om beskyttelse af links i Defender for Office 365 at beskytte en organisation mod phishing og andre angreb, der bruger skadelige URL-adresser. Find Teams Pengeskab Links, og se grafik af Pengeskab Links-meddelelser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8bd4773d3f712adf13ac2a006f5d8450c58fc89a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682080"
---
# <a name="safe-links-in-microsoft-defender-for-office-365"></a>Pengeskab Links i Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Denne artikel er beregnet til virksomhedskunder, der [har Microsoft Defender Office 365](defender-for-office-365.md). Hvis du bruger Outlook.com, Microsoft 365 Family eller Microsoft 365 Personal, og du leder efter oplysninger om Safelinks i Outlook, skal du se [Avanceret Outlook.com-sikkerhed](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Pengeskab Links er en funktion i [Defender til Office 365](defender-for-office-365.md), der giver URL-scanning og omskrivning af indgående mails i mailflow, og tids-for-klik-bekræftelse af URL-adresser og links i mails og andre placeringer. Pengeskab sker der scanning af links ud over den almindelige [antispam- og antimalwarebeskyttelse](anti-spam-and-anti-malware-protection.md) i indgående mails Exchange Online Protection (EOP). Pengeskab Links scanning kan hjælpe med at beskytte din organisation mod skadelige links, der bruges i phishing og andre angreb.

Pengeskab Links-beskyttelse er tilgængelig på følgende placeringer:

- **Mails**: Selvom der ikke er nogen standardpolitik for Pengeskab Links, giver den indbyggede beskyttelse foruddefinerede sikkerhedspolitik Pengeskab beskyttelse af links til alle modtagere (brugere, der ikke er defineret i brugerdefinerede Pengeskab **Kæder-politikker**). Du kan finde flere oplysninger [i Forudindstillede sikkerhedspolitikker i EOP og Microsoft Defender Office 365](preset-security-policies.md). Du kan også oprette Pengeskab kæder, der gælder for bestemte brugere, grupper eller domæner. Du kan finde en [vejledning under Konfigurere Pengeskab Links-politikker i Microsoft Defender Office 365](set-up-safe-links-policies.md).

  Du kan finde flere Pengeskab om beskyttelse af links til [mails i Pengeskab Indstillinger for links til](#safe-links-settings-for-email-messages) mails senere i denne artikel.
  
  > [!NOTE]
  > Pengeskab Links virker ikke i mailaktiverede offentlige mapper.
  >
  > Pengeskab Links understøtter kun HTTP(S) og FTP-formater.

- **Microsoft Teams**: Pengeskab links til links i Teams samtaler, gruppechatsamtaler eller fra kanaler styres også af Pengeskab Links-politikker.

  Du kan finde flere Pengeskab om beskyttelse Teams links i [Pengeskab Links for](#safe-links-settings-for-microsoft-teams) Microsoft Teams senere i denne artikel.

- **Office 365-apps**: Pengeskab links til Office 365-apps er tilgængelig i understøttede skrivebords-, mobil- og webapps. Du **skal** Pengeskab beskyttelse af links til Office 365 apps i den globale indstilling, der er **uden** for Pengeskab politikker for links. Du kan finde en [vejledning i Konfigurere globale indstillinger for Pengeskab Links i Microsoft Defender Office 365](configure-global-settings-for-safe-links.md).

  Pengeskab Beskyttelse af links til Office 365-apps anvendes for alle brugere i organisationen, der har licens til Defender til Office 365, uanset om brugerne er inkluderet i aktive Pengeskab Links-politikker eller ej.

  Du kan finde flere oplysninger Pengeskab beskyttelse af Office 365 links i Pengeskab [Links-indstillinger for Office 365-apps](#safe-links-settings-for-office-365-apps) senere i denne artikel.

Denne artikel indeholder detaljerede beskrivelser af følgende typer af Pengeskab links:

- **Indstillinger politikker i Pengeskab Links**: Disse indstillinger gælder kun for de brugere, der er inkluderet i de specifikke politikker, og indstillingerne kan være forskellige fra politik til politik. Disse indstillinger omfatter:

  - [Pengeskab links til mails](#safe-links-settings-for-email-messages)
  - [Pengeskab links til Microsoft Teams](#safe-links-settings-for-microsoft-teams)
  - ["Undlad at omskrive følgende URL-adresser"-lister i Pengeskab Links-politikker](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies)

- **Globale Pengeskab for links**: Disse indstillinger er konfigureret globalt, ikke i Pengeskab Links. Disse indstillinger omfatter:

  - [Pengeskab links til Office 365 apps](#safe-links-settings-for-office-365-apps)
  - [Listen "Bloker følgende URL-adresser" for Pengeskab links](#block-the-following-urls-list-for-safe-links)

I følgende tabel beskrives scenarier for Pengeskab Links i Microsoft 365- og Office 365-organisationer, der omfatter Defender for Office 365 (Bemærk, at manglende licenser aldrig er et problem i eksemplerne).

|Scenarie|Resultat|
|---|---|
|Jane er medlem af marketingafdelingen. Pengeskab Links-beskyttelse for Office 365-apps er slået til i de globale indstillinger for Pengeskab Links, og der findes en Pengeskab Links-politik, der gælder for medlemmer af marketingafdelingen. Jean åbner PowerPoint i en mail og klikker derefter på en URL-adresse i præsentationen.|Jean er beskyttet af Pengeskab Links. <p> Jean er inkluderet i en Pengeskab Links-politik, og Pengeskab Links-beskyttelse til Office 365-apps er slået til. <p> Du kan finde flere oplysninger om kravene til beskyttelse af Pengeskab Links i Office 365-apps i [afsnittet indstillinger for Pengeskab Links til Office 365-apps](#safe-links-settings-for-office-365-apps) senere i denne artikel.|
|Chris' Microsoft 365 E5 har ikke konfigureret Pengeskab Links. Chris modtager en mail fra en ekstern afsender, der indeholder en URL-adresse til et skadeligt websted, som han i sidste ende klikker på.|Chris er ikke beskyttet af Pengeskab Links. <p> En administrator skal oprette mindst én politik for Pengeskab links, for at alle kan få Pengeskab beskyttelse af links i indgående mails. Chris skal være inkluderet i betingelserne for politikken for at få Pengeskab Links-beskyttelse.|
|I Pats organisation har ingen administratorer oprettet nogen Pengeskab Links-politikker, men Pengeskab Links-beskyttelse for Office 365-apps er slået til. Pat åbner et Word-dokument og klikker på en URL-adresse i filen.|Pat er ikke beskyttet af Pengeskab Links. <p> Selvom Pengeskab Links-beskyttelse for Office 365-apps er slået til globalt, er Pat ikke inkluderet i nogen aktiv Pengeskab Links-politikker, så beskyttelsen kan ikke anvendes.|
|I Lees organisation er konfigureret `https://tailspintoys.com` på listen **Bloker følgende URL-adresser** i de globale indstillinger for Pengeskab Links. En Pengeskab links-politik, der omfatter Lee, findes allerede. Lee modtager en mail, der indeholder URL-adressen `https://tailspintoys.com/aboutus/trythispage`. Lee klikker på URL-adressen.|URL-adressen kan blive blokeret automatisk for Lee; det afhænger af URL-posten på listen, og den mailklient Lee har brugt. Du kan finde flere oplysninger i [listen "Bloker følgende URL-adresser" for Pengeskab Links](#block-the-following-urls-list-for-safe-links) senere i denne artikel.|
|Jamie og Ane arbejder begge for contoso.com. For lang tid siden konfigurerede administratorer Pengeskab Links, der gælder for både Jamie og Bai. Jamie sender en mail til Bell uden at vide, at mailen indeholder en skadelig URL-adresse.|Indhold er beskyttet af **Pengeskab Links,** hvis politikken Pengeskab Links, der gælder for hende, er konfigureret til at gælde for meddelelser mellem interne modtagere. Du kan finde flere oplysninger [Pengeskab indstillinger for links til mails](#safe-links-settings-for-email-messages) senere i denne artikel.|

## <a name="safe-links-settings-for-email-messages"></a>Pengeskab links til mails

Pengeskab Links scanner indgående mail for kendte ondsindede links. Scannede URL-adresser omskrives ved hjælp af Microsofts standard-URL-præfiks: `https://nam01.safelinks.protection.outlook.com`. Når linket er omskrevet, analyseres det for potentielt skadeligt indhold.

Når Pengeskab Links en URL-adresse igen, forbliver URL-adressen omskrevet, selvom meddelelsen videresendes manuelt  eller besvares (både interne og eksterne modtagere). Yderligere links, der føjes til den videresendte eller besvarede meddelelse, bliver ikke omskrevet. Men i tilfælde af automatisk videresendelse ved hjælp af indbakkeregler eller SMTP-videresendelse bliver URL-adressen ikke omskrevet i den meddelelse, der er beregnet til den endelige  modtager, medmindre modtageren også er beskyttet med Pengeskab links, eller URL-adressen allerede er blevet omskrevet i en tidligere kommunikation. Så længe linkene Pengeskab aktiveret, scannes URL-adresser stadig før levering, uanset om de er blevet omskrevet eller ej. Url-adresser, der ikke er blevet installeret, kontrolleres også stadig af et KLIENT-API-opkald til Pengeskab Links på tidspunktet for klik i Outlook til desktopversion 16.0.12513 eller nyere.

Indstillingerne i Pengeskab Links, der gælder for mails, er beskrevet på følgende liste:

- **Vælg handlingen for ukendte potentielt skadelige URL-adresser i** meddelelser: Aktiverer eller deaktiverer søgning Pengeskab links i mails. Den anbefalede værdi er **Til**. Hvis du slår denne indstilling til, medfører det følgende handlinger.

  - Pengeskab Links-scanning er aktiveret i Outlook (C2R) på Windows.
  - URL-adresser omskrives, og brugerne distribueres via Pengeskab Links-beskyttelse, når de klikker på URL-adresser i meddelelser.
  - Når der klikkes på dem, kontrolleres URL-adresser i forhold til en liste over kendte skadelige URL-adresser og [listen "Bloker følgende URL-adresser"](#block-the-following-urls-list-for-safe-links).
  - URL-adresser, der ikke har et gyldigt ry, detoneres asynkront i baggrunden.

- **Anvend URL-adressescanning** i realtid for mistænkelige links og links, der peger på filer: Gør det muligt at scanne links i realtid, herunder links i mails, der peger på indhold, der kan downloades. Den anbefalede værdi er aktiveret.
  - **Vent på, at URL-adressen scannes, før meddelelsen leveres**:
    - Aktiveret: Meddelelser, der indeholder URL-adresser, opbevares, indtil scanningen er færdig. Meddelelser leveres først, når URL-adresserne er bekræftet som sikre. Dette er den anbefalede værdi.
    - Deaktiveret: Hvis scanning af URL-adresser ikke kan fuldføres, skal du levere meddelelsen alligevel.

- **Anvend Pengeskab Links** til mails, der sendes i organisationen: Aktiverer eller deaktiverer Pengeskab Links, der scanner for meddelelser, der sendes mellem interne afsendere og interne modtagere i den samme Exchange Online organisation. Den anbefalede værdi er aktiveret.

- **Registrer ikke brugerklik**: Aktiverer eller deaktiverer lagring af indhold Pengeskab klikker på data for URL-adresser, der er klikket på i mails. Den anbefalede værdi er at lade denne indstilling være fravalgt (for at spore brugerklik).

  Url-kliksporing for links i mails, der sendes mellem interne afsendere og interne modtagere, understøttes ikke i øjeblikket.

- **Tillad ikke, at brugerne klikker igennem til den oprindelige URL-adresse**: Gør det muligt eller blokerer brugere fra at klikke gennem [advarselssiden](#warning-pages-from-safe-links) til den oprindelige URL-adresse. Anbefal-værdien er aktiveret.

- **Vise organisationens branding på sider med meddelelser** og advarsler: Denne indstilling viser organisationens branding på advarselssider. Branding hjælper brugerne med at identificere legitime advarsler, fordi Microsofts standardadvarselssider ofte bruges af hackere. Du kan finde flere oplysninger om tilpasset branding [under Tilpas Microsoft 365 tema til organisationen](../../admin/setup/customize-your-organization-theme.md).

- **Undlad at omskrive følgende URL-adresser: Forlader URL-adresserne**, som de er. Opbevarer en brugerdefineret liste over sikre URL-adresser, der ikke behøver at blive scannet. Listen er entydig for hver Pengeskab links-politik. Du kan finde flere oplysninger  om listen over URL-adresser, der ikke skal omskrives, på listerne "Omstøt ikke følgende URL-adresser[" Pengeskab](#do-not-rewrite-the-following-urls-lists-in-safe-links-policies) politikker for links senere i denne artikel.

  Du kan finde flere oplysninger om de anbefalede værdier for Standard- og Restriktive politikindstillinger for politikker for Pengeskab Links [under Pengeskab politikindstillinger for links](recommended-settings-for-eop-and-office365.md#safe-links-policy-settings).

- **Undlad at omskrive URL-adresser, kontroller kun via SafeLinks API: Hvis** denne indstilling er aktiveret, sker der ingen URL-ombrydning. Pengeskab Links kaldes udelukkende via API'er på tidspunktet for URL-adressen, når der klikkes på Outlook klienter, der understøtter det. Anbefal-værdien er deaktiveret.
  
- **Modtagerfiltre**: Du skal angive modtagerbetingelser og undtagelser, der bestemmer, hvem politikken gælder for. Du kan bruge disse egenskaber til betingelser og undtagelser:
  - **Modtageren er**
  - **Modtagerdomænet er**
  - **Modtageren er medlem af**

  Du kan kun bruge en betingelse eller undtagelse én gang, men betingelsen eller undtagelsen kan indeholde flere værdier. Flere værdier af samme betingelse eller undtagelse bruger ELLER-logik (f.eks. _\<recipient1\>_ eller _\<recipient2\>_). Forskellige betingelser eller undtagelser bruger AND-logik (f.eks. _\<recipient1\>_ og _\<member of group 1\>_).

- **Prioritet**: Hvis du opretter flere politikker, kan du angive den rækkefølge, de anvendes i. Der er ikke to politikker, der kan have samme prioritet, og behandling af politikker stopper, når den første politik er anvendt.

  Du kan finde flere oplysninger om rangordenen, og hvordan flere politikker evalueres og anvendes, i Rækkefølge [og prioriteret mailbeskyttelse](how-policies-and-protections-are-combined.md).
  
### <a name="how-safe-links-works-in-email-messages"></a>Sådan Pengeskab Links fungerer i mails

På et højt niveau kan du se, hvordan beskyttelse Pengeskab Links fungerer på URL-adresser i mails:

1. Alle mails går gennem EOP, hvor IP (Internet Protocol) og konvolutfiltre, signaturbaseret malwarebeskyttelse, antispam- og antimalwarefiltre før meddelelsen leveres til modtagerens postkasse.

2. Brugeren åbner meddelelsen i sin postkasse og klikker på en URL-adresse i meddelelsen.

3. Pengeskab Kontrollerer straks URL-adressen, før webstedet åbnes:

   - Hvis URL-adressen findes på listen **Bloker følgende URL-adresser** , åbnes en advarsel [om blokeret URL-adresse](#blocked-url-warning) .

   - Hvis webadressen peger på et websted, der er fundet skadeligt, åbnes en skadelig [](#malicious-website-warning) advarselsside (eller en anden advarselsside).

   - Hvis URL-adressen peger på en fil, der kan downloades, og indstillingen Anvend **URL-adresse** i realtid for mistænkelige links og links, der peger på filer er aktiveret i den politik, der gælder for brugeren, er indstillingen for den fil, der kan downloades, markeret.

   - Hvis URL-adressen vurderes som sikker, åbnes webstedet.

## <a name="safe-links-settings-for-microsoft-teams"></a>Pengeskab links til Microsoft Teams

Du aktiverer eller deaktiverer Pengeskab links-beskyttelse for Microsoft Teams i Pengeskab links-politikker. Specifikt bruger du indstillingen **Vælg handlingen for ukendte eller potentielt skadelige URL-adresser Microsoft Teams** handling. Den anbefalede værdi er **Til**.

> [!NOTE]
> Når du slår beskyttelse af Pengeskab Links til eller Teams, kan det tage op til 24 timer, før ændringen træder i kraft.

Følgende indstillinger i Pengeskab Links, der gælder for links i mails, gælder også for links i Teams:

- **Anvend URL-scanning i realtid for mistænkelige links og links, der peger på filer**
- **Registrer ikke brugerklik**
- **Tillad ikke, at brugerne klikker sig til den oprindelige URL-adresse**

Disse indstillinger er tidligere forklaret [Pengeskab indstillinger for links til mails](#safe-links-settings-for-email-messages).

Når du har aktiveret beskyttelse af Pengeskab-links for Microsoft Teams, kontrolleres URL-adresserne i Teams mod en liste over kendte skadelige links, når den beskyttede bruger klikker på linket (beskyttelse med tid til at klikke). URL-adresser omskrives ikke. Hvis der findes et link, der er skadeligt, vil brugerne få følgende oplevelser:

- Hvis der blev klikket på linket i en Teams-samtale, gruppechat eller fra kanaler, vises advarselssiden som vist på skærmbilledet nedenfor i standardwebbrowseren.
- Hvis der klikkes på linket fra en fastgjort fane, vises advarselssiden i grænsefladen Teams under den pågældende fane. Indstillingen til at åbne linket i en webbrowser er deaktiveret af sikkerhedsmæssige årsager.
- Afhængigt af hvordan indstillingen Tillad ikke brugere at klikke igennem til den oprindelige **URL-adresse** i politikken er konfigureret, vil eller vil brugeren ikke have tilladelse til at klikke igennem til den oprindelige URL-adresse (Fortsæt alligevel (anbefales ikke **)** i skærmbilledet). Vi anbefaler, at du aktiverer indstillingen Tillad ikke brugere at klikke igennem til den oprindelige **URL-adresse** , så brugerne ikke kan klikke igennem til den oprindelige URL-adresse.

Hvis den bruger, der sendte linket, ikke er inkluderet i en politik for Pengeskab-links, hvor Teams-beskyttelse er aktiveret, kan brugeren klikke igennem til den oprindelige URL-adresse på sin computer eller enhed.

![En Pengeskab Links til Teams, der rapporterer et skadeligt link.](../../media/tp-safe-links-for-teams-malicious.png)

Hvis du klikker **på knappen Gå** tilbage på advarselssiden, returneres brugeren til den oprindelige kontekst eller URL-placering. Men hvis du klikker på det oprindelige link igen, medfører det, Pengeskab Links kan scanne URL-adressen igen, så advarselssiden vises igen.

### <a name="how-safe-links-works-in-teams"></a>Sådan Pengeskab Links i Teams

På et højt niveau kan du se her, hvordan Pengeskab Links-beskyttelse fungerer for URL-adresser Microsoft Teams:

1. En bruger starter Teams appen.

2. Microsoft 365 bekræfter, at brugerens organisation omfatter Microsoft Defender til Office 365, og at brugeren er inkluderet i en aktiv Pengeskab Links-politik, hvor beskyttelse af Microsoft Teams er aktiveret.

3. URL-adresser valideres på tidspunktet for klik for brugeren i chatsamtaler, gruppechats, kanaler og faner.

## <a name="safe-links-settings-for-office-365-apps"></a>Pengeskab links til Office 365 apps

Pengeskab Links-beskyttelse til Office 365-apps kontrollerer links i Office-dokumenter og ikke links i mails (men den kan kontrollere links i vedhæftede Office-dokumenter i mails, når dokumentet er åbnet).

Pengeskab Links-beskyttelse til Office 365-apps har følgende klientkrav:

- Microsoft 365 Apps eller Microsoft 365 Business Premium.
  - Aktuelle versioner af Word, Excel og PowerPoint på Windows, Mac eller i en webbrowser.
  - Office apps på iOS- eller Android-enheder.
  - Visio på Windows.
  - OneNote i en webbrowser.
  - Outlook til Windows, når du åbner gemte EML- eller MSG-filer.

- Office 365 apps konfigureres til at bruge moderne godkendelse. Få mere at vide under Sådan fungerer moderne godkendelse [til Office 2013, Office 2016 og Office 2019-klientprogrammer](../../enterprise/modern-auth-for-office-2013-and-2016.md).

- Brugerne er logget på med deres arbejds- eller skolekonti. Du kan få mere at [vide under Log på Office](https://support.microsoft.com/office/b9582171-fd1f-4284-9846-bdd72bb28426).

Du skal Pengeskab beskyttelse af links Office 365 apps i de globale indstillinger for Pengeskab Links og ikke i Pengeskab links. Beskyttelsen gælder for alle brugere i organisationen, der har licens til Defender til Office 365, uanset om brugerne er inkluderet i aktive Pengeskab Links-politikker eller ej.

Følgende indstillinger Pengeskab Links er tilgængelige for Office 365 apps:

- **Office 365 programmer**: Aktiverer eller deaktiverer scanning af Pengeskab links i understøttede Office 365 apps. Standardværdien og den anbefalede værdi er **Til**.

- **Registrer ikke**, hvornår brugere klikker på Pengeskab-links: Aktiverer eller deaktiverer lagring af Pengeskab Links klikker på data for URL-adresser, der er klikket på i computerversionerne Word, Excel, PowerPoint og Visio. Den anbefalede værdi er **Fra**, hvilket betyder, at brugerklik registreres.

- **Lad ikke** brugere klikke gennem sikre links til den oprindelige URL-adresse: Gør det muligt eller blokerer brugere fra [](#warning-pages-from-safe-links) at klikke gennem advarselssiden til den oprindelige URL-adresse i computerversionerne Word, Excel, PowerPoint og Visio. Standardværdien og den anbefalede værdi er **Til**.

Hvis du vil konfigurere Pengeskab links til Office 365 apps, skal [du se konfigurer Pengeskab links til Office 365 apps](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Du kan finde flere oplysninger om de anbefalede værdier for standard- og restriktive politikindstillinger [under Globale indstillinger for Pengeskab links](recommended-settings-for-eop-and-office365.md#global-settings-for-safe-links).

### <a name="how-safe-links-works-in-office-365-apps"></a>Sådan Pengeskab Links i Office 365 apps

På et højt niveau kan du se her, hvordan Pengeskab Links-beskyttelse fungerer for URL-adresser Office 365 apps. De understøttede Office 365 apps er beskrevet i forrige afsnit.

1. En bruger logger på med sin arbejds- eller skolekonto i en organisation, der Microsoft 365 Apps eller Microsoft 365 Business Premium.

2. Brugeren åbner og klikker på et link for at oprette Office dokument i en understøttet Office-app.

3. Pengeskab Kontrollerer straks URL-adressen, før destinationswebstedet åbnes:

   - Hvis URL-adressen er medtaget på listen, og Pengeskab scanning af links (listen Bloker  følgende URL-adresser), åbnes en advarselsside med [blokeret URL-adresse](#blocked-url-warning).

   - Hvis webadressen peger på et websted, der er fundet skadeligt, åbnes en skadelig [](#malicious-website-warning) advarselsside (eller en anden advarselsside).

   - Hvis URL-adressen peger på en fil, der kan downloades, og politikken Pengeskab Links, der gælder for brugeren, er konfigureret til at scanne links til indhold, der kan downloades (Anvend **URL-scanning** i realtid for mistænkelige links og links, der peger på filer), er den fil, der kan downloades, markeret.

   - Hvis URL-adressen betragtes som sikker, bliver brugeren ført til webstedet.

   - Hvis Pengeskab Links-scanning ikke kan fuldføres, Pengeskab Beskyttelse af links ikke udløses. I Office-skrivebordsklienter bliver brugeren advaret, før brugeren går videre til destinationswebstedet.

> [!NOTE]
> Det kan tage flere sekunder i starten af hver session at bekræfte, at brugeren har Pengeskab Links for Office aktiveret.

## <a name="block-the-following-urls-list-for-safe-links"></a>Listen "Bloker følgende URL-adresser" for Pengeskab links

Listen **Bloker følgende URL-adresser** definerer de links, der altid blokeres af Pengeskab links, der scanner på følgende placeringer:

- Mails.
- Dokumenter i Office 365 apps i Windows og Mac.
- Dokumenter i Office til iOS og Android.

Når en bruger i en aktiv Pengeskab-politik klikker på et blokeret link i en understøttet app, kommer brugeren til advarselssiden for [blokeret URL-adresse](#blocked-url-warning).

Du skal konfigurere listen over URL-adresser i de globale indstillinger for Pengeskab links. Du kan finde en vejledning [under Konfigurer listen "Bloker følgende URL-adresser"](configure-global-settings-for-safe-links.md#configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal).

**Bemærkninger**:

- Du kan finde en virkelig universal liste over URL-adresser, der blokeres overalt, [under Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md).
- Begrænsninger for listen **Bloker følgende URL-adresser** :
  - Det maksimale antal poster er 500.
  - Den maksimale længde for en indtastning er 128 tegn.
  - Alle indtastninger må ikke overstige 10.000 tegn.
- Medtag ikke en skråstreg (`/`) i slutningen af URL-adressen. Brug f.eks. `https://www.contoso.com`, ikke `https://www.contoso.com/`.
- En URL-adresse, der kun gælder for domæne (f.eks `contoso.com` `tailspintoys.com`. eller ), blokerer alle URL-adresser, der indeholder domænet.
- Du kan blokere et underdomæne uden at blokere det fulde domæne. Blokerer f.eks `toys.contoso.com*` . URL-adresser, der indeholder underdomænet, men ikke blokerer ikke URL-adresser, der indeholder det fulde domæne `contoso.com`.
- Du kan medtage op til tre jokertegn () pr`*`. URL-adresse.

### <a name="entry-syntax-for-the-block-the-following-urls-list"></a>Postsyntaksen for listen "Bloker følgende URL-adresser"

Eksempler på de værdier, du kan angive, og deres resultater er beskrevet i følgende tabel:

|Værdi|Resultat|
|---|---|
|`contoso.com` <p> eller <p> `*contoso.com*`|Blokerer domænet, underdomæner og stier. f.eks. `https://www.contoso.com`, `https://sub.contoso.com`og blokeres `https://contoso.com/abc` .|
|`https://contoso.com/a`|Blokke `https://contoso.com/a` , men ikke yderligere underpather som `https://contoso.com/a/b`.|
|`https://contoso.com/a*`|Blokke `https://contoso.com/a` og yderligere underpather som `https://contoso.com/a/b`.|
|`https://toys.contoso.com*`|Blokerer et underdomæne (i dette`toys` eksempel), men tillader klik til andre domæne-URL-adresser (f.eks. `https://contoso.com` eller `https://home.contoso.com`).|

## <a name="do-not-rewrite-the-following-urls-lists-in-safe-links-policies"></a>"Undlad at omskrive følgende URL-adresser"-lister i Pengeskab Links-politikker

> [!NOTE]
> Hvis din organisation bruger Pengeskab Links-politikker, er listerne  Omsend ikke følgende URL-adresser den eneste understøttede metode til phishingtests fra tredjepart.

Hver Pengeskab links-politik indeholder en Liste over  url-adresser, du ikke må skrive igen, og som du kan bruge til at angive URL-adresser, der ikke omskrives ved Pengeskab scanning af links. Listen giver med andre ord brugere, der er inkluderet i politikken, mulighed for at få adgang til de angivne URL-adresser, som ellers ville være blokeret af Pengeskab links. Du kan konfigurere forskellige lister i Pengeskab politikker for links. Behandling af politikker stopper efter den første (sandsynligvis den højeste prioritet) politik anvendt på brugeren. Så der anvendes kun **én af følgende URL-adresser på** en bruger, der er inkluderet i flere aktive politikker for Pengeskab URL-adresser.

Hvis du vil føje poster til listen i nye eller eksisterende Pengeskab links-politikker, skal du se Opret [Pengeskab-links-politikker](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-create-safe-links-policies) eller [Rediger Pengeskab Links-politikker](set-up-safe-links-policies.md#use-the-microsoft-365-defender-portal-to-modify-safe-links-policies).

**Bemærkninger**:

- Følgende klienter genkender ikke listerne over **URL-adresser** i de Pengeskab kæder. Brugere, der er inkluderet i politikkerne, kan blokeres fra at få adgang til URL-adresserne baseret på resultaterne af Pengeskab Links scanning i disse klienter:
  - Microsoft Teams
  - Office webapps

  Du kan finde en virkelig universal liste over URL-adresser, der er tilladt overalt, under [Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md). Bemærk dog, at URL-adresser, der er tilføjet der, ikke vil blive udelukket Pengeskab Links omskrivning, da det skal gøres i en Pengeskab Links-politik.

- Overvej at føje ofte anvendte interne URL-adresser til listen for at forbedre brugeroplevelsen. Hvis du f.eks. har lokale tjenester, f.eks. Skype for Business eller SharePoint, kan du tilføje disse URL-adresser for at udelukke dem fra scanning.
- Hvis du allerede har  omskrivning af følgende URL-adresser i politikkerne for Pengeskab-links, skal du sørge for at gennemse listerne og tilføje jokertegn efter behov. Listen indeholder f.eks. en post som f.eks `https://contoso.com/a` ., og du senere beslutter dig for at medtage understier som f.eks `https://contoso.com/a/b`. . I stedet for at tilføje en ny post skal du føje et jokertegn til den eksisterende post, så den bliver til `https://contoso.com/a/*`.
- Du kan medtage op til tre jokertegn () pr`*`. URL-adresse. Jokertegn indeholder eksplicit præfikser eller underdomæner. Posten er f.eks. `contoso.com` ikke den samme `*.contoso.com/*`som , `*.contoso.com/*` fordi den tillader brugere at besøge underdomæner og stier i det angivne domæne.
- Hvis en URL-adresse anvender automatisk omdirigering for HTTP til HTTPS (f.eks. 302 omdirigering for `http://www.contoso.com` til `https://www.contoso.com`), og du forsøger at angive både HTTP- og HTTPS-poster for den samme URL-adresse til listen, bemærker du muligvis, at den anden URL-adresse erstatter den første URL-adressepost. Denne funktionsmåde forekommer ikke, hvis HTTP- og HTTPS-versionerne af URL-adressen er fuldstændig adskilte.
- Undlad at angive http:// eller https:// (dvs. contoso.com) for at udelukke både HTTP- og HTTPS-versioner.
- `*.contoso.com` dækker **ikke** contoso.com, så du er nødt til at udelukke både det angivne domæne og underordnede domæner.
- `contoso.com/*` dækker **kun** contoso.com, så der er ingen grund til at udelukke både og `contoso.com` `contoso.com/*`– kun tilstrækkelig `contoso.com/*` .
- Hvis du vil udelade alle gentagelser af et domæne, skal der udelades to udeladelsesposter: `contoso.com/*` og `*.contoso.com/*`. Disse kombineres for at udelukke både HTTP og HTTPS, hoveddomænet contoso.com og underordnede domæner samt en eller ikke-slutdel (f.eks. dækkes både contoso.com og contoso.com/vdir1).

### <a name="entry-syntax-for-the-do-not-rewrite-the-following-urls-list"></a>Postsyntaksen for listen "Omstøt ikke følgende URL-adresser"

Eksempler på de værdier, du kan angive, og deres resultater er beskrevet i følgende tabel:

|Værdi|Resultat|
|---|---|
|`contoso.com`|Tillader adgang til `https://contoso.com` , men ikke underdomæner eller stier.|
|`*.contoso.com/*`|Giver adgang til et domæne, underdomæner og stier (f.eks. `https://www.contoso.com`, `https://www.contoso.com`, `https://maps.contoso.com`eller `https://www.contoso.com/a`). <p> Denne post er forbundet med bedre end `*contoso.com*`, fordi den ikke tillader potentielt svigagtige websteder, `https://www.falsecontoso.com` såsom eller `https://www.false.contoso.completelyfalse.com`|
|`https://contoso.com/a`|Tillader adgang til `https://contoso.com/a`, men ikke understier som `https://contoso.com/a/b`|
|`https://contoso.com/a/*`|Giver adgang til `https://contoso.com/a` og underpather som f.1. `https://contoso.com/a/b`|

## <a name="warning-pages-from-safe-links"></a>Advarselssider fra Pengeskab Links

Dette afsnit indeholder eksempler på de forskellige advarselssider, der udløses af beskyttelse af Pengeskab, når du klikker på en URL-adresse.

Bemærk, at flere advarselssider er blevet opdateret. Hvis du ikke allerede kan se de opdaterede sider, vil du snart kunne se dem. De opdaterede sider indeholder et nyt farveskema, flere detaljer og muligheden for at gå videre til et websted på trods af den angivne advarsel og anbefalinger.

### <a name="scan-in-progress-notification"></a>Meddelelse om scanning i gang

Den klikkede URL-adresse scannes af Pengeskab Links. Du skal muligvis vente et øjeblik, før du prøver linket igen.

![Meddelelsen "Linket scannes"](../../media/ee8dd5ed-6b91-4248-b054-12b719e8d0ed.png)

Den oprindelige meddelelsesside så sådan ud:

![Den oprindelige meddelelse "Linket scannes"](../../media/04368763-763f-43d6-94a4-a48291d36893.png)

### <a name="suspicious-message-warning"></a>Advarsel om mistænkelig meddelelse

Den klikkede URL-adresse var i en mail, der ligner andre mistænkelige meddelelser. Vi anbefaler, at du dobbelttjekker mailen, før du fortsætter til webstedet.

![Advarslen "Der blev klikket på et link fra en mistænkelig meddelelse"](../../media/33f57923-23e3-4b0f-838b-6ad589ba897b.png)

### <a name="phishing-attempt-warning"></a>Advarsel om forsøg på phishing

Den klikkede URL-adresse var i en mail, der er identificeret som et phishingangreb. Derfor blokeres alle URL-adresser i mailen. Vi anbefaler, at du ikke fortsætter til webstedet.

![Advarslen "Linket blev klikket på fra en phishing-meddelelse"](../../media/6e544a28-0604-4821-aba6-d5a57bb917e5.png)

### <a name="malicious-website-warning"></a>Advarsel om ondsindet websted

Den klikkede URL-adresse peger på et websted, der er identificeret som skadeligt. Vi anbefaler, at du ikke fortsætter til webstedet.

![Advarslen "Dette websted er klassificeret som skadelig"](../../media/058883c8-23f0-4672-9c1c-66b084796177.png)

Den oprindelige advarselsside så sådan ud:

![Oprindelig "Dette websted er blevet klassificeret som skadelig" advarsel](../../media/b9efda09-6dd8-46ef-82cb-56e4d538b8f5.png)

### <a name="blocked-url-warning"></a>Advarsel om blokeret URL-adresse

Den klikkede URL-adresse er blevet blokeret manuelt af en administrator i organisationen  (listen Bloker følgende URL-adresser i de globale indstillinger for Pengeskab Links). Linket blev ikke scannet af Pengeskab, fordi det blev blokeret manuelt.

Der er flere årsager til, at en administrator manuelt blokerer bestemte URL-adresser. Hvis du mener, at webstedet ikke skal blokeres, skal du kontakte din administrator.

![Advarslen "Dette websted blev blokeret af din administrator"](../../media/6b4bda2d-a1e6-419e-8b10-588e83c3af3f.png)

Den oprindelige advarselsside så sådan ud:

![Den oprindelige advarsel "Dette websted er blevet blokeret ifølge organisationens URL-politik"](../../media/3d6ba028-30bf-45fc-958e-d3aad3defc83.png)

### <a name="error-warning"></a>Fejladvarsel

Der opstod en eller anden form for fejl, og URL-adressen kan ikke åbnes.

![Advarslen "Den side, du forsøger at få adgang til"](../../media/2f7465a4-1cf4-4c1c-b7d4-3c07e4b795b4.png)

Den oprindelige advarselsside så sådan ud:

![Den oprindelige advarsel om, at "Denne webside kunne ikke indlæses"](../../media/9aaa4383-2f23-48be-bdaa-8efbcb2acc70.png)
