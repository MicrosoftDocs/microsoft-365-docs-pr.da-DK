---
title: Bedste praksis for sikring af Microsoft 365 til virksomheder
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- admindeeplinkDEFENDER
- adminvideo
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: de2da300-dbb6-4725-bb12-b85a9d296e75
description: Beskyt din virksomheds mail og dine data mod cybertrusler, herunder ransomware, phishing og skadelige vedhæftede filer.
ms.openlocfilehash: 347d88a95d8ed55116655980560eb3d9cf925213
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602928"
---
# <a name="best-practices-for-securing-microsoft-365-for-business"></a>Bedste praksis for sikring af Microsoft 365 til virksomheder

Se [Hjælp til små virksomheder i Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

Hvis du er en lille eller mellemstor organisation, der bruger en af Microsofts forretningsplaner, hjælper vejledningen i denne artikel dig med at skærpe sikkerheden i din organisation. Blandt dine valg er Microsoft 365 Business Premium vejen, da det nu omfatter Microsoft Defender til virksomheder og anden [sikkerhedsbeskyttelse](../../business-premium/get-microsoft-365-business-premium.md). De anbefalede handlinger, der er inkluderet her, vil hjælpe dig med at nå de mål, der er beskrevet i Harvard Kennedy School [Cybersecurity Campaign Handbook](https://go.microsoft.com/fwlink/p/?linkid=2015598).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i denne artikel, kan du overveje at [arbejde sammen med en Microsoft-specialist i mindre virksomheder](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="watch-a-quick-overview-of-security"></a>Se: Et hurtigt overblik over sikkerhed

Se denne video og andre på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198012).

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mzxI?autoplay=false]

Alle Microsoft 365-planer tilbyder grundlæggende beskyttelse og sikkerhed med Defender Antivirus, men med Microsoft 365 Business Premium har du også trusselsbeskyttelse, databeskyttelse og enhedshåndteringsfunktioner på grund af medtagelse af Microsoft Defender til virksomheder.  Disse yderligere funktioner beskytter din organisation mod onlinetrusler og uautoriseret adgang samt giver dig mulighed for at administrere virksomhedsdata på dine telefoner, tablets og computere.

## <a name="security-features-comparison"></a>Sammenligning af sikkerhedsfunktioner

Hvis du vil vide mere om en af funktionerne i serviceplanen, skal du klikke på overskriften i følgende tabel. 

|Opgave|Microsoft 365 Business Standard|Microsoft 365 Business Premium|
|---|---|---|
[Beskyt mod mistede eller stjålne adgangskoder](#set-up-multi-factor-authentication) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Oplær dine brugere](#train-your-users) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Brug dedikerede administratorkonti](#use-dedicated-admin-accounts)|![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | 
[Beskyt mod malware](#protect-against-malware) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(beskyttelse af mail) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(øget beskyttelse af mail og enheder) |
[Beskyt mod ransomware](#protect-against-ransomware) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(beskyttelse af mail og cloudlager) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(øget beskyttelse af enheder, mail og cloudlager) |
[Kryptér følsomme mails](#send-encrypted-email) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) |
[Beskyt din mail mod phishingangreb](#protect-sensitive-emails) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(beskyttelse mod phishing) | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(avanceret beskyttelse mod phishing) |
[Beskyt mod skadelige vedhæftede filer, filer og URL-adresser i mails og Office-filer](#protect-against-malicious-attachments-files-and-urls) | | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(Sikre links og vedhæftede filer, der er tillid til) |
[Øg beskyttelsen af organisationens enheder](#increase-protection-for-your-organizations-devices) | | ![Inkluderet.](../../media/d238e041-6854-4a78-9141-049224df0795.png) <br/>(enhedsbeskyttelse i virksomhedsklasse) |

Du kan hurtigt konfigurere sikkerhed og begynde at samarbejde sikkert med den vejledning, vi giver i [Microsoft 365 Business Premium](../../business-premium/index.md) bibliotek. Business Premium-oplysningerne blev udviklet i samarbejde med Microsoft Defending Democracy-teamet for at beskytte alle mindre virksomhedskunder mod cybertrusler, der blev lanceret af avancerede cyberangreb og hackere.

### <a name="about-the-microsoft-365-secure-score"></a>Om Microsoft 365 Secure Score

Det er vigtigt, at du kontrollerer din [Microsoft 365 Secure Score](../../security/defender/microsoft-secure-score.md) på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>, før du begynder. Fra et centraliseret dashboard kan du overvåge og forbedre sikkerheden for dine Microsoft 365-identiteter, data, apps, enheder og infrastruktur. Du får point for konfiguration af anbefalede sikkerhedsfunktioner, udførelse af sikkerhedsrelaterede opgaver (f.eks. visning af rapporter) eller løsning af anbefalinger med et tredjepartsprogram eller -software. Med tilføjet indsigt og mere synlighed i et bredere sæt Microsoft-produkter og -tjenester kan du føle dig tryg ved at rapportere om din organisations sikkerhedstilstand.

![Skærmbillede af Microsoft Secure Score.](../../media/secure-score.png)

## <a name="set-up-multi-factor-authentication"></a>Konfigurer multifaktorgodkendelse

Beskyt mod mistede eller stjålne adgangskoder ved hjælp af multifaktorgodkendelse (MFA). Når multifaktorgodkendelse er konfigureret, kræver det, at brugerne bruger en kode på deres telefon for at logge på Microsoft 365. Dette ekstra skridt kan forhindre hackere i at overtage, hvis de kender din adgangskode. 

Multifaktorgodkendelse kaldes også totrinsbekræftelse. Enkeltpersoner kan nemt føje totrinsbekræftelse til de fleste konti, f.eks. til deres Google- eller Microsoft-konti. Sådan [føjer du totrinsbekræftelse til din personlige Microsoft-konto](https://go.microsoft.com/fwlink/p/?linkid=2016403).

For virksomheder, der bruger Microsoft 365, skal du tilføje en indstilling, der kræver, at brugerne logger på med multifaktorgodkendelse. Når du foretager denne ændring, bliver brugerne bedt om at konfigurere deres telefon til tofaktorgodkendelse, næste gang de logger på.
Hvis du vil se en træningsvideo om, hvordan du konfigurerer MFA, og hvordan brugerne fuldfører konfigurationen, skal du se [Konfigurer MFA](set-up-multi-factor-authentication.md) og [brugerkonfiguration](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

### <a name="turn-on-security-defaults"></a>Slå sikkerhedsstandarder til

For de fleste organisationer tilbyder sikkerhedsstandarder et godt niveau af ekstra logonsikkerhed. Du kan få flere oplysninger under [Hvad er sikkerhedsstandarder?](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults). Hvis dit abonnement er nyt, er sikkerhedsstandarder muligvis allerede slået til automatisk for dig.

Aktivér eller deaktiver sikkerhedsstandarder i ruden **Egenskaber** for Azure Active Directory (Azure AD) i Azure Portal.

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med globale administratorlegitimationsoplysninger.

2. Vælg **Vis alle** i venstre navigationsrude, og vælg **Azure Active Directory** under **Administration centre**.

3. Vælg **Azure Active Directory-egenskaber** >  i **Azure Active Directory Administration**.

4. Nederst på siden skal du vælge **Administrer sikkerhedsstandarder**.

5. Vælg **Ja** for at aktivere sikkerhedsstandarder eller **Nej** for at deaktivere sikkerhedsstandarder, og vælg derefter **Gem**.

Når du har konfigureret multifaktorgodkendelse for din organisation, skal brugerne konfigurere totrinsbekræftelse på deres enheder. Du kan få flere oplysninger under [Konfigurer totrinsbekræftelse til Microsoft 365](https://support.microsoft.com/office/ace1d096-61e5-449b-a875-58eb3d74de14).

> [!Tip]
> Hvis du har brug for mere detaljeret kontrol af multifaktorgodkendelse, kan du aktivere Betinget adgang med Microsoft 365 Business Premium. Hvis du gør dette, anbefaler vi, at du implementerer de tilsvarende politikker som sikkerhedsstandarder. Gå til denne side for at få flere oplysninger om [sikkerhedsstandarder](/microsoft-365/business-premium/m365bp-conditional-access).

Du kan finde flere oplysninger og anbefalinger under [Konfigurer multifaktorgodkendelse for brugere](set-up-multi-factor-authentication.md).

## <a name="train-your-users"></a>Oplær dine brugere

Harvard Kennedy School [Cybersecurity Campaign Handbook](https://go.microsoft.com/fwlink/p/?linkid=2015598) giver fremragende vejledning i at etablere en stærk kultur af sikkerhedsbevidsthed i din organisation, herunder uddannelse af brugere til at identificere phishing-angreb.

Derudover anbefaler Microsoft, at dine brugere foretager de handlinger, der er beskrevet i denne artikel: [Beskyt din konto og dine enheder mod hackere og malware](https://support.microsoft.com/office/066d6216-a56b-4f90-9af3-b3a1e9a327d6). Disse handlinger omfatter:

- Brug af stærke adgangskoder
- Beskyttelse af enheder
- Aktivering af sikkerhedsfunktioner på Windows 10- og Mac-pc'er

Microsoft anbefaler også, at brugerne beskytter deres personlige mailkonti ved at gøre de handlinger, der anbefales i følgende artikler:

- [Hjælp med at beskytte din Outlook.com mailkonto](https://support.microsoft.com/office/a4f20fc5-4307-4ece-8231-6d4d4bd8a9ba)

- [Beskyt din Gmail-konto med totrinsbekræftelse](https://go.microsoft.com/fwlink/p/?linkid=2015688&)

## <a name="use-dedicated-admin-accounts"></a>Brug dedikerede administratorkonti

De administrative konti, du bruger til at administrere dit Microsoft 365-miljø, omfatter administratorrettigheder. Dette er værdifulde mål for hackere og cyberangreb. Brug kun administratorkonti til administration. Administratorer skal have en separat brugerkonto til regelmæssig, ikke-administrativ brug og kun bruge deres administrative konto, når det er nødvendigt, for at fuldføre en opgave, der er knyttet til deres jobfunktion. Yderligere anbefalinger:

- Sørg for, at konti føjes til [Azure Active Directory](../../admin/add-users/add-users.md).
- Sørg for, at der også er konfigureret administratorkonti til multifaktorgodkendelse.
- Før du bruger administratorkonti, skal du lukke alle ikke-relaterede browsersessioner og -apps, herunder personlige mailkonti.
- Når du har fuldført administratoropgaver, skal du sørge for at logge af browsersessionen.

## <a name="protect-against-malware"></a>Beskyt mod malware

Dit Microsoft 365-miljø omfatter beskyttelse mod malware. Du kan øge beskyttelsen af skadelig software ved at:

- Brug [af forudindstillede politikker for Microsoft Office 365](../../../microsoft-365/security/office-365-security/preset-security-policies.md).
- Blokerer vedhæftede filer med visse filtyper.
- Brug antivirus-/antimalwarebeskyttelse på dine enheder, især Microsoft Defender til virksomheder. Det indeholder funktioner som [automatiseret undersøgelsesrapportering](../../security/office-365-security/air-view-investigation-results.md) (AIR) og dashboardet Threat and Vulnerability Management (TVM). Når Microsoft Defender til virksomheder ikke er din primære antivirussoftware, kan du stadig køre den i passiv tilstand og bruge [EDR (endpoint Protection and Response),](../../security/defender-endpoint/overview-endpoint-detection-response.md) især i [bloktilstand](../../security/defender-endpoint/edr-in-block-mode.md), hvor det fungerer bag kulisserne for at afhjælpe skadelige artefakter, der blev opdaget af EDR's egenskaber, og som er savnet af den primære virusregistreringssoftware.

### <a name="block-attachments-with-certain-file-types"></a>Bloker vedhæftede filer med bestemte filtyper

Du kan øge beskyttelsen mod skadelig software ved at blokere vedhæftede filer med filtyper, der ofte bruges til malware. Hvis du vil opsne malwarebeskyttelse i mail, skal du se [Se: Hæv niveauet af beskyttelse mod malware i mails](increase-threat-protection.md#watch-raise-the-level-of-protection-against-malware-in-mail), eller udfør følgende trin:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Antimalware** i afsnittet **Politikker**.
2. Dobbeltklik på **Standard** på siden **Antimalware**. Der vises et pop op-vindue.
3. Vælg **Rediger beskyttelsesindstillinger** nederst i pop op-vinduet.
4. På næste side under **Beskyttelsesindstillinger** skal du markere afkrydsningsfeltet ud for **Aktivér filteret for almindelige vedhæftede filer**. De filtyper, der er blokeret, vises direkte under denne indstilling. Hvis du vil tilføje eller slette filtyper, skal du vælge **Tilpas filtyper** i slutningen af listen.
5. Vælg **Gem**.

Du kan få flere oplysninger under [Beskyttelse mod antimalware i EOP](../../security/office-365-security/anti-malware-protection.md).

### <a name="use-antivirus-and-anti-malware-protection"></a>Brug antivirus- og antimalwarebeskyttelse

Microsoft Defender Antivirus giver stærk antivirus- og antimalwarebeskyttelse og er indbygget i Windows-operativsystemet.

Hvis din organisation bruger Microsoft 365 Business Premium, får du yderligere enhedsbeskyttelse, der omfatter:

- Næste generations beskyttelse
- Firewallbeskyttelse
- Filtrering af webindhold

Disse funktioner er inkluderet i Microsoft Defender til virksomheder, et tilbud, der begynder at blive udrullet for Microsoft 365 Business Premium kunder fra og med den 1. marts 2022.

[Få mere at vide om Microsoft Defender til virksomheder](../../security/defender-business/mdb-overview.md).

## <a name="protect-against-ransomware"></a>Beskyt mod ransomware

Ransomware begrænser adgangen til data ved at kryptere filer eller låse computerskærme. Det forsøger derefter at afpresse penge fra ofre ved at bede om "løsesum", som regel i form af kryptovalutaer som Bitcoin, i bytte for adgang til data.

Du får ransomware-beskyttelse for mail, der hostes i Microsoft 365, og for filer, der er gemt i OneDrive. Hvis du har Microsoft 365 Business Premium, får du yderligere ransomware-beskyttelse til din organisations enheder.

Du kan beskytte dig mod ransomware ved at oprette en eller flere regler for mailflow for at blokere filtypenavne, der ofte bruges til ransomware, eller for at advare brugere, der modtager disse vedhæftede filer i en mail. Et godt udgangspunkt er at oprette to regler:

- Brug OneDrive til at flytte filer, så de altid er adgangskontrollerede og beskyttede.

- Advar brugerne, før de åbner vedhæftede filer i Office, der indeholder makroer. Ransomware kan skjules i makroer, så vi advarer brugerne om ikke at åbne disse filer fra personer, de ikke kender.

- Bloker filtyper, der kan indeholde ransomware eller anden skadelig kode. Vi starter med en fælles liste over eksekverbare filer (angivet i nedenstående tabel). Hvis din organisation bruger en af disse eksekverbare typer, og du forventer, at de sendes i en mail, skal du føje dem til den forrige regel (advar brugere).

Hvis du vil oprette en regel for mailtransport, skal du se [Se: Beskyt mod ransomware](increase-threat-protection.md#watch-protect-against-ransomware), eller udfør følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

2. Vælg **regler** i kategorien **mailflow**.

3. Vælg **+**, og **opret derefter en ny regel**.

4. Vælg **** nederst i dialogboksen for at se det fulde sæt indstillinger.

5. Anvend indstillingerne i følgende tabel for hver regel. Lad resten af indstillingerne være standard, medmindre du vil ændre dem.

6. Vælg **Gem**.

| Indstilling | Advar brugere, før de åbner vedhæftede filer i Office-filer | Bloker filtyper, der kan indeholde ransomware eller anden skadelig kode |
|:-----|:-----|:-----|
|Navn  <br/> |Anti-ransomware-regel: advar brugere  <br/> |Anti-ransomware-regel: bloker filtyper  <br/> |
|Anvend denne regel, hvis . . .  <br/> |Alle vedhæftede filer . . . filtypenavnet svarer til . . .  <br/> |Alle vedhæftede filer . . . filtypenavnet svarer til . . .  <br/> |
|Angiv ord eller udtryk  <br/> |Tilføj disse filtyper:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm  <br/> |Tilføj disse filtyper:  <br/> ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif  <br/> |
|Benyt følgende fremgangsmåde . . .  <br/> |Forbestil en ansvarsfraskrivelse  <br/> |Bloker meddelelsen . . . afvis meddelelsen, og medtag en forklaring  <br/> |
|Angiv meddelelsestekst  <br/> |Du må ikke åbne disse filtyper – medmindre du forventede dem – da filerne kan indeholde skadelig kode, og hvis du kender afsenderen, er det ikke en garanti for sikkerhed.  <br/> ||

> [!TIP]
> Du kan også føje de filer, du vil blokere, til listen over antimalwarefiler i [Beskyt mod malware](#protect-against-malware).

Du kan finde flere oplysninger under:

- [Ransomware: Sådan reducerer du risikoen](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Bedre sammen: Microsoft Defender Antivirus og Office 365](../../security/defender-endpoint/office-365-microsoft-defender-antivirus.md)

- [Gendan dit OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)


## <a name="protect-sensitive-emails"></a>Beskyt følsomme mails

Microsoft 365 indeholder Office-meddelelseskryptering, som giver dig mulighed for at sende og modtage krypterede mails mellem personer i og uden for din organisation, og kun de ønskede modtagere kan få dem vist. Krypteringen fungerer sammen med Outlook.com, Yahoo!, Gmail og andre mailtjenester.

> [!Tip]
> Hvis der er behov for et strengere sikkerhedsniveau, skal din organisation også konfigurere og bruge følsomhedsmærkatering til mails eller filer. [Følsomhedsmærkater](../../compliance/sensitivity-labels.md) tillader kontrol over indhold, uanset hvor det går hen.

### <a name="send-encrypted-email"></a>Send krypteret mail

Sådan krypterer du din mail:

1. Når en ny mail er åben, skal du vælge menuen **Indstillinger** .
1. Vælg det relevante tilladelsesniveau på rullelisten **Kryptér** .

:::image type="content" source="../../media/08e90a7e-a2d2-41a4-bae9-0a46b4ce639b.png" alt-text="Kryptering af mailmeddelelser i Outlook":::

### <a name="receive-encrypted-email"></a>Modtag krypteret mail

Hvis modtageren har Outlook 2013 eller Outlook 2016 og en Microsoft-mailkonto, får vedkommende vist en besked om elementets begrænsede tilladelser i læseruden. Når du har åbnet meddelelsen, kan modtageren få vist meddelelsen på samme måde som enhver anden.

Hvis modtageren bruger en anden mailklient eller mailkonto, f.eks. Gmail eller Yahoo, får vedkommende vist et link, hvor de enten kan logge på for at læse mailen eller anmode om en engangsadgangskode for at få vist meddelelsen i en webbrowser. Hvis brugerne ikke modtager mailen, skal de kontrollere deres mappe med spam eller uønsket mail.

> [!TIP]
> Du kan få flere oplysninger under [Send, få vist og besvar krypterede meddelelser i Outlook til pc](https://support.microsoft.com/office/eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="protect-the-organization"></a>Beskyt organisationen

Hvis du har konfigureret et eller flere brugerdefinerede domæner til dit Microsoft 365-miljø, kan du konfigurere målrettet beskyttelse mod phishing. Beskyttelse mod phishing er inkluderet i Microsoft Defender for Office 365 og kan hjælpe med at beskytte din organisation mod skadelig efterligningsbaseret phishing og andre angreb.

> [!Note]
> Hvis du ikke har konfigureret et brugerdefineret domæne, behøver du ikke at gøre dette.

Vi anbefaler, at du kommer i gang med denne beskyttelse ved at oprette en politik for dine vigtigste brugere og dit brugerdefinerede domæne. Et godt sted at gøre dette er i Microsoft 365 Defender, der er inkluderet i Microsoft Business Premium. Hvis du vil oprette en politik til bekæmpelse af phishing i Defender for Office 365, skal du fuldføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

2. Gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker** .

3. Vælg **+ Opret** på siden Anti-phishing. En guide starter en guide, der fører dig gennem definition af din anti-phishing-politik.

4. Angiv navnet, beskrivelsen og indstillingerne for politikken som anbefalet i nedenstående diagram. Du kan finde flere oplysninger [under Få mere at vide om anti-phishing-politik i Microsoft Defender for Office 365 indstillinger](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Når du har gennemset dine indstillinger, skal du vælge **Opret denne politik** eller **Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Domæne og de mest værdifulde kampagnemedarbejdere|
|Beskrivelse|Sørg for, at de vigtigste medarbejdere og vores domæne ikke repræsenteres.|
|Tilføj brugere for at beskytte|Vælg **+ Tilføj en betingelse. Modtageren er**. Skriv brugernavne, eller angiv mailadressen på kandidaten, kampagnelederen og andre vigtige medarbejdere. Du kan tilføje op til 20 interne og eksterne adresser, som du vil beskytte mod repræsentation.|
|Tilføj domæner for at beskytte|Vælg **+ Tilføj en betingelse. Modtagerdomænet er**. Angiv det brugerdefinerede domæne, der er knyttet til dit Microsoft 365-abonnement, hvis du har defineret et. Du kan angive mere end ét domæne.|
|Vælg handlinger|Hvis mail sendes af en repræsenteret bruger: Vælg **Omdiriger meddelelse til en anden mailadresse**, og skriv derefter sikkerhedsadministratorens mailadresse. f.eks. securityadmin@contoso.com. <br/> Hvis mail sendes af et repræsenterede domæne: Vælg **Karantænemeddelelse**.|
|Postkasseintelligens|Postkasseintelligens vælges som standard, når du opretter en ny politik mod phishing. Lad denne indstilling være **slået** til for at opnå de bedste resultater.|
|Tilføj afsendere og domæner, der er tillid til|I dette eksempel skal du ikke definere nogen tilsidesættelser.|
|Anvendt på|Vælg **Modtagerdomænet er**. Under **Et af disse** skal du vælge **Vælg**. Vælg **+ Tilføj**. Markér afkrydsningsfeltet ud for navnet på domænet, f.eks. contoso.com, på listen, og vælg derefter **Tilføj**. Vælg **Udført**.|

> [!TIP]
> Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

## <a name="protect-against-malicious-attachments-files-and-urls"></a>Beskyt mod skadelige vedhæftede filer, filer og URL-adresser

Folk sender, modtager og deler jævnligt vedhæftede filer, f.eks. dokumenter, præsentationer, regneark og meget mere. Det er ikke altid nemt at se, om en vedhæftet fil er sikker eller ondsindet bare ved at se på en mail. Microsoft Defender for Office 365 omfatter sikker beskyttelse af vedhæftede filer, men denne beskyttelse er ikke aktiveret som standard. Vi anbefaler, at du opretter en ny regel for at begynde at bruge denne beskyttelse. Denne beskyttelse omfatter også filer i SharePoint, OneDrive og Microsoft Teams.

### <a name="set-up-safe-attachments"></a>Konfigurer sikre vedhæftede filer

Du kan bruge forudindstillede politikker for vedhæftede filer eller oprette dine egne. Hvis du vil oprette en politik for sikre vedhæftede filer, skal du se en [kort træningsvideo](increase-threat-protection.md) eller fuldføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>, og log på med din administratorkonto.

2. Gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Antimalware** i afsnittet **Politikker** .

3. Vælg **+ Opret** for at oprette en ny politik.

4. Anvend indstillingerne i følgende tabel.

5. Når du har gennemset dine indstillinger, skal du vælge **Opret denne politik** eller **Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Bloker aktuelle og fremtidige mails med registreret malware.|
|Beskrivelse|Bloker aktuelle og fremtidige mails og vedhæftede filer med registreret malware.|
|Gem vedhæftede filer ukendt malware-svar|Vælg **Bloker – Bloker de aktuelle og fremtidige mails og vedhæftede filer med registreret malware**.|
|Omdiriger vedhæftet fil ved registrering|Aktivér omdirigering (markér dette felt) <br/> Angiv administratorkontoen eller konfigurationen af en postkasse til karantæne. <br/> Anvend ovenstående valg, hvis der opstår timeout for malwarescanning efter vedhæftede filer, eller der opstår fejl (markér dette felt).|
|Anvendt på|Modtagerdomænet er . . . vælg dit domæne.|

> [!TIP]
> Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i Defender for Office 365](../../security/office-365-security/configure-atp-anti-phishing-policies.md).

### <a name="set-up-safe-links"></a>Konfigurer sikre links

Hackere skjuler nogle gange ondsindede websteder i links i e-mail eller andre filer. Sikre links, der er en del af Microsoft Defender for Office 365, kan hjælpe med at beskytte din organisation ved at give bekræftelse af webadresser (URL-adresser) i mails og Office-dokumenter. Beskyttelse defineres via politikker for sikre links.

Gør følgende for at beskytte mod angreb:

- Rediger standardpolitikken for at øge beskyttelsen.

- Tilføj en ny politik, der er målrettet til alle modtagere i dit domæne.

Hvis du vil have vist Sikre links, skal du se [Se: Beskyt din mail mod phishing-angreb](increase-threat-protection.md#watch-protect-your-email-from-phishing-attacks), eller udfør følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>, og log på med din administratorkonto.

2. Gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Antimalware** i afsnittet **Politikker** .

3. Vælg **+ Opret** for at oprette en ny politik, eller rediger standardpolitikken.

Sådan redigerer du standardpolitikken:

1. Dobbeltklik på **standardpolitikken** . Der vises et pop op-vindue. 

2. Vælg **Rediger beskyttelsesindstillinger** nederst i pop op-vinduet.

3. Når du har ændret standardpolitikken, skal du vælge **Gem**.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Politik for sikre links for alle modtagere i domænet|
|Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser|Vælg **Til – URL-adresser omskrives og kontrolleres i forhold til en liste over kendte skadelige links, når brugeren klikker på linket**.|
|Anvend scanning af URL-adresser i realtid for mistænkelige links og links, der peger på filer|Markér dette felt.|
|Anvendt på|Modtagerdomænet er . . . vælg dit domæne.|

> [!TIP]
> Du kan få flere oplysninger [under Sikre links i Microsoft Defender for Office 365](../../security/office-365-security/atp-safe-links.md).

## <a name="increase-protection-for-your-organizations-devices"></a>Øg beskyttelsen af organisationens enheder

Microsoft Defender Antivirus er indbygget i Windows-operativsystemet og giver god beskyttelse mod virus og malware. Du kan dog øge beskyttelsen af din organisations enheder ved at onboarde dem til Microsoft Defender til virksomheder hvilket er et nyt tilbud til små og mellemstore virksomheder som dine og er inkluderet [i Microsoft 365 Business Premium](../../business-premium/index.md). Med Defender for Business er din organisations enheder bedre beskyttet mod ransomware, malware, phishing og andre trusler.

Med Microsoft 365 Business Premium får du øgede sikkerhedsfunktioner, f.eks. enhedshåndtering og avanceret trusselsbeskyttelse. Når du tilmelder enheder til Microsoft 365 Business for Defender, overvåges og beskyttes enhederne af InTune.


Du kan få mere at vide i følgende ressourcer:

- [Oversigt over Microsoft Defender til virksomheder](../../security/defender-business/mdb-overview.md)

- [Konfigurer og konfigurer Microsoft Defender til virksomheder](../../security/defender-business/mdb-setup-configuration.md)

- [Kom i gang med at bruge Microsoft 365 Defender-portalen](../../security/defender-business/mdb-get-started.md)

## <a name="related-content"></a>Relateret indhold

[Multifaktorgodkendelse til Microsoft 365](multi-factor-authentication-microsoft-365.md) (artikel)\
[Administrer og overvåg prioritetskonti](../setup/priority-accounts.md) (artikel)\
[Microsoft 365-rapporter i Administration](../activity-reports/activity-reports.md) (video)\
[Microsoft 365 Business Premium — cybersikkerhed for små virksomheder](/microsoft-365/business-premium/) (artikel)\

