---
title: Forøg trusselsbeskyttelse til Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: Skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
- admindeeplinkMAC
- admindeeplinkEXCHANGE
- admindeeplinkSPO
search.appverid:
- BCS160
- MET150
description: Få hjælp til at øge beskyttelsesniveauet i Microsoft 365 Business Premium
ms.openlocfilehash: e8d1b010f18e595e0ea7c17caf94ca8d89eb0f47
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704995"
---
# <a name="increase-threat-protection-for-microsoft-365-business-premium"></a>Forøg trusselsbeskyttelse til Microsoft 365 Business Premium

Denne artikel hjælper dig med at øge beskyttelsen i dit Microsoft 365-abonnement for at beskytte dig mod phishing, malware og andre trusler. Disse anbefalinger er relevante for organisationer med et øget behov for sikkerhed, f.eks. politiske kampagner, advokatkontorer og sundhedsplejeafdelinger.

Før du begynder, skal du kontrollere din Microsoft Secure Score. Microsoft Secure Score analyserer din organisations sikkerhed baseret på dine almindelige aktiviteter og sikkerhedsindstillinger og tildeler en score. Start med at notere dit aktuelle resultat. Hvis du gør det, der anbefales i denne artikel, øges din score. Målet er ikke at opnå det højeste antal point, men at være opmærksom på muligheder for at beskytte dit miljø, der ikke påvirker produktiviteten for dine brugere negativt.

Du kan finde flere oplysninger [i Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Hæve beskyttelsesniveauet mod malware i mail

Dit Office 365 eller Microsoft 365-miljø omfatter beskyttelse mod malware, men du kan øge denne beskyttelse ved at blokere vedhæftede filer med filtyper, der ofte bruges til malware. Sådan får du en bedre beskyttelse mod malware i en mail:

1. Gå til Office 365 <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Security & Compliance Center</a>, og log på med legitimationsoplysningerne til din administratorkonto.

2. I venstre navigationsrude under **Trusselsstyring skal** du vælge **Antimalwarepolitik**\>.

3. Dobbeltklik på standardpolitikken for at redigere denne politik for hele virksomheden.

4. Klik **Indstillinger**.

5. Under **Filter for almindelige typer af vedhæftede** filer skal du **vælge Til**. De filtyper, der blokeres, vises i vinduet direkte under dette kontrolelement. Sørg for, at du tilføjer disse filtyper:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Du kan tilføje eller slette filtyper senere, hvis det er nødvendigt.

6. Klik **på Gem.**

Få mere at vide under [Beskyttelse mod malware i EOP](../security/office-365-security/anti-malware-protection.md).

## <a name="protect-against-ransomware"></a>Beskyt dig mod ransomware

Ransomware begrænser adgangen til data ved at kryptere filer eller låse computerskærme. Det forsøger derefter at afpresse penge fra det, der er brug for, ved at bede om "ekstra penge", som regel i form af f.eks. Bitcoin, til at få adgang til data.

Du kan beskytte mod ransomware ved at oprette en eller flere regler for mailflow for at blokere filtypenavne, der ofte bruges til ransomware (disse blev tilføjet i et højere niveau af beskyttelse mod [malware i mailtrin](#raise-the-level-of-protection-against-malware-in-mail) ), eller for at advare brugere, der modtager disse vedhæftede filer i en mail.

Ud over de filer, du blokerede i forrige trin, er det også god praksis at oprette en regel for at advare brugerne, før du åbner Office vedhæftede filer, der indeholder makroer. Ransomware kan være skjult i makroer, så advar brugerne, så de ikke bør åbne disse filer fra personer, de ikke kender.

Sådan oprettes en posttrafikregel:

1. Gå til Administration på , <https://admin.microsoft.com> og vælg **Exchange** \> **.**

2. Klik på **Regler i** kategorien **Mailflow**.

3. Klik **+** på , og klik derefter **på Opret en ny regel**.

4. Klik **på Flere** indstillinger nederst i dialogboksen for at få vist alle indstillinger.

5. Anvend indstillingerne i følgende tabel for reglen. Lad resten af indstillingerne være som standard, medmindre du vil ændre dem.

6. Klik på **Gem**.

|Indstilling|Advar brugerne, før du åbner vedhæftede filer Office filer|
|---|---|
|Navn|Regel for anti-ransomware: advar brugere|
|Anvend denne regel, hvis . . .|Enhver vedhæftet fil . . . filtypenavnet svarer til . . .|
|Angiv ord eller udtryk|Tilføj disse filtyper: <br/> `dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm`|
|Gør følgende. . .|Give modtageren besked med en meddelelse|
|Angiv meddelelsestekst|Du skal ikke åbne disse filtyper fra personer, du ikke kender, da de kan indeholde makroer med skadelig kode.|

Du kan finde flere oplysninger under:

- [Ransomware: Sådan reducerer du risikoen](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Gendan dine OneDrive](https://support.microsoft.com//office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>Stop automatisk videresendelse for mail

Hackere, der får adgang til en brugers postkasse, kan stjæle din mail ved at indstille postkassen til automatisk at videresende mails. Dette kan ske, selv uden brugerens opmærksomhed. Du kan forhindre dette ved at konfigurere en regel for mailflow.

Hvis du vil oprette en transportregel for mail, skal du [enten se denne korte video](https://support.office.com/article/f9d693ba-5c78-47c0-b156-8e461e062aa7) eller følge disse trin:

1. Klik <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> Administration **i Exchange**\>.

2. Klik på **Regler i** kategorien **Mailflow**.

3. Klik **+** på , og klik derefter **på Opret en ny regel**.

4. Klik **på Flere** indstillinger nederst i dialogboksen for at få vist alle indstillinger.

5. Anvend indstillingerne i følgende tabel. Lad resten af indstillingerne være som standard, medmindre du vil ændre dem.

6. Klik på **Gem**.

|Indstilling|Advar brugerne, før du åbner vedhæftede filer Office filer|
|---|---|
|Navn|Undgå automatisk videresendelse af mail til eksterne domæner|
|Anvend denne regel, hvis ...|Afsenderen . . . er ekstern/intern. . . Inden for organisationen|
|Tilføj betingelse|Meddelelsesegenskaberne. . . medtag meddelelsestypen . . . Automatisk videresendelse|
|Gør følgende...|Bloker meddelelsen. . . afvise meddelelsen og medtage en forklaring.|
|Angiv meddelelsestekst|Automatisk videresendelse af mail uden for denne organisation er forhindret af sikkerhedsmæssige årsager.|

## <a name="protect-your-email-from-phishing-attacks"></a>Beskyt dine mails mod phishingangreb

Hvis du har konfigureret et eller flere brugerdefinerede domæner til dit Office 365 eller Microsoft 365, kan du konfigurere målrettet beskyttelse mod phishing. Beskyttelse mod phishing, som er en del af Microsoft Defender Office 365, kan hjælpe med at beskytte din organisation mod ondsindede efterligningsbaserede phishingangreb og andre phishingangreb. Hvis du ikke har konfigureret et brugerdefineret domæne, behøver du ikke at gøre dette.

Vi anbefaler, at du går i gang med denne beskyttelse ved at oprette en politik for at beskytte dine vigtigste brugere og dit brugerdefinerede domæne.

Hvis du vil oprette en antiphishingpolitik i Defender for Office 365, skal du [se denne](https://support.office.com/article/86c425e1-1686-430a-9151-f7176cce4f2c) korte kursusvideo eller udføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a>.

2. I venstre navigationsrude under **Trusselsstyring skal** du vælge **Politik**.

3. Vælg **Antiphishing på siden Politik**.

4. På siden **Antiphishing** skal du vælge **+ Opret**. Der startes en guide, der fører dig gennem definitionen af din antiphishingpolitik.

5. Angiv navn, beskrivelse og indstillinger for din politik som anbefalet i nedenstående diagram. Du kan få mere at [vide under Få mere at vide om politik for phishing i Microsoft Defender for Office 365 indstillinger](../security/office-365-security/set-up-anti-phishing-policies.md).

6. Når du har gennemset dine indstillinger, skal du **vælge Opret denne politik** **eller Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Domæne og mest værdifulde medarbejdere|
|Beskrivelse|Sørg for, at de vigtigste medarbejdere og vores domæne ikke repræsenteres.|
|Tilføj brugere, der skal beskyttes|Vælg **+ Tilføj en betingelse, modtageren er**. Skriv brugernavne, eller angiv mailadressen på virksomhedsejere, partnere eller kandidater, ledere og andre vigtige medarbejdere. Du kan tilføje op til 20 interne og eksterne adresser, du vil beskytte mod efterligning.|
|Tilføj domæner, der skal beskyttes|Vælg **+ Tilføj en betingelse, Modtagerens domæne er**. Angiv det brugerdefinerede domæne, der er knyttet Microsoft 365 abonnementet, hvis du har defineret et. Du kan angive mere end ét domæne.|
|Vælg handlinger|Hvis mail sendes af en efterligning af en bruger: Vælg Omdiriger meddelelse til en anden **mailadresse, og** skriv derefter mailadressen på sikkerhedsadministratoren. for eksempel *2010<span><span>@contoso.com*. <br/> Hvis mail sendes af et efterligning af et domæne: Vælg **meddelelse i karantæne**.|
|Postkasseintelligens|Postkasseintelligens vælges som standard, når du opretter en ny antiphishingpolitik. Lad denne indstilling være **til for** at få de bedste resultater.|
|Tilføj afsendere og domæner, der er tillid til|Her kan du tilføje dit eget domæne eller andre domæner, der er tillid til.|
|Anvendt på|Vælg **Modtagerdomænet er**. Under **Alle disse skal** du vælge **Vælg**. Vælg **+ Tilføj**. Markér afkrydsningsfeltet ud for navnet på domænet, f.eks. *contoso.<span><span> på* listen, og vælg derefter **Tilføj**. Vælg **Udført**.|

Få mere at vide under [Konfigurer antiphishing-politikker i Defender Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-malicious-attachments-files-and-links-with-defender-for-office-365"></a>Beskyt dig mod skadelige vedhæftede filer, filer og links med Defender Office 365

![Banner, der peger på https://aka.ms/aboutM365preview.](../media/m365admincenterchanging.png)

Du skal først sørge for, at du i Administration har <https://admin.microsoft.com> aktiveret den nye forhåndsvisning af Administration. Slå til/fra-knappen til ud for **teksten Den nye Administration**.

   ![Den nye forhåndsvisning af Administration er blevet til.](../media/previewon.png)

Hvis du endnu ikke kan se konfigurationssiden med kort i din lejer, kan du se, hvordan du gennemfører disse trin i Security & Compliance Center. Se [Konfigurer Pengeskab i Security & Compliance Center](#set-up-safe-attachments-in-the-security--compliance-center) og Konfigurer [Pengeskab-links i Security & Compliance Center](#set-up-safe-links-in-the-security--compliance-center).

1. I venstre navigationslinje skal du vælge **Konfiguration**.
2. På siden **Konfiguration** skal du **vælge Vis** på kortet **Forøg beskyttelsen mod avancerede** trusler.

   ![Vælg Vis i forøg beskyttelsen mod avancerede trusler.](../media/startatp.png)

3. På siden **Forøg beskyttelsen mod avancerede trusler** skal du vælge **Introduktion**.
4. I den rude, der åbnes, skal du markere afkrydsningsfelterne ud for Links og vedhæftede filer i mails, Scan filer i **SharePoint, OneDrive og Teams** og **Scan links i Office-skrivebords- og Office Online-apps** under **Scan elementer for skadeligt** indhold.

   Under **Links og vedhæftede filer i mail** skal du skrive Alle brugere eller de bestemte brugere, hvis mail du vil scanne.

   ![Markér alle afkrydsningsfelter i Forøg beskyttelsen mod avancerede trusler.](../media/setatp.png)

5. Vælg **Opret politikker** for at aktivere Pengeskab vedhæftede filer og Pengeskab links.

### <a name="set-up-safe-attachments-in-the-security--compliance-center"></a>Konfigurer Pengeskab i Security & Compliance Center

Folk sender, modtager og deler jævnligt vedhæftede filer, f.eks. dokumenter, præsentationer, regneark og meget mere. Det er ikke altid nemt at afgøre, om en vedhæftet fil er sikker eller skadelig blot ved at se på en mail. Microsoft Defender til Office 365 indeholder Pengeskab Beskyttelse af vedhæftet fil, men denne beskyttelse er ikke slået til som standard. Vi anbefaler, at du opretter en ny regel for at begynde at bruge denne beskyttelse. Denne beskyttelse omfatter filer i SharePoint, OneDrive og Microsoft Teams.

Hvis du vil oprette Pengeskab vedhæftet fil, skal du [enten se denne korte video](https://support.office.com/article/e7e68934-23dc-4b9c-b714-e82e27a8f8a5) eller udføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a>, og log på med din administratorkonto.

2. I venstre navigationsrude under **Trusselsstyring skal** du vælge **Politik**.

3. På siden Politik skal du vælge Pengeskab **vedhæftede filer**.

4. På siden Pengeskab vedhæftede filer skal du anvende denne beskyttelse bredt ved at markere afkrydsningsfeltet **Slå ATP til for SharePoint, OneDrive og Microsoft Teams** filer.

5. Vælg **+** for at oprette en ny politik.

6. Anvend indstillingerne i følgende tabel.

7. Når du har gennemset dine indstillinger, **skal du vælge Opret denne** politik **eller Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Bloker nuværende og fremtidige mails med registreret malware.|
|Beskrivelse|Bloker nuværende og fremtidige mails og vedhæftede filer med registreret malware.|
|Gem vedhæftede filer ukendt malware svar|Vælg **Bloker – Bloker for nuværende og fremtidige mails og vedhæftede filer med registreret malware**.|
|Omdirigere vedhæftet fil ved registrering|Aktivér omdirigering (markér dette felt) <br/> Angiv administratorkontoen eller konfigurationen af en postkasse til karantæne. <br/> Anvend ovenstående markering, hvis malwarescanning for vedhæftede filer får time out, eller der opstår en fejl (markér dette felt).|
|Anvendt på|Modtagerdomænet er . . . skal du vælge dit domæne.|

Få mere at vide under [Konfigurer antiphishing-politikker i Defender Office 365](../security/office-365-security/set-up-anti-phishing-policies.md).

### <a name="set-up-safe-links-in-the-security--compliance-center"></a>Konfigurer Pengeskab links i Security & Compliance Center

Hackere skjuler sommetider ondsindede websteder i links i mails eller andre filer. Pengeskab Links, som er en del af Microsoft Defender til Office 365, kan hjælpe med at beskytte din organisation ved at angive tids-for-klik-bekræftelse af webadresser (URL-adresser) i mails og Office dokumenter. Beskyttelse defineres via Pengeskab Links-politikker.

Vi anbefaler, at du gør følgende:

- Rediger standardpolitikken for at øge beskyttelsen.

- Tilføj en ny politik, der er målrettet alle modtagere i dit domæne.

Hvis du vil konfigurere Pengeskab links, skal [du se denne korte kursusvideo](https://support.office.com/article/61492713-53c2-47da-a6e7-fa97479e97fa) eller udføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Office 365 Security & Compliance Center</a>, og log på med din administratorkonto.

2. I venstre navigationsrude under **Trusselsstyring skal** du vælge **Politik**.

3. På siden Politik skal du vælge **Pengeskab Links**.

Sådan ændres standardpolitikken:

1. På siden Pengeskab du vælge **Standardpolitik under Politikker, der gælder** for **hele** organisationen.

2. Under **Indstillinger, der gælder** for indhold undtagen mail, skal **du vælge Microsoft 365 Apps for enterprise, Office til iOS og Android**.

3. Klik på **Gem**.

Sådan opretter du en ny politik, der er målrettet alle modtagere i dit domæne:

1. På siden Pengeskab, der gælder **for hele** organisationen, skal du klikke for **+** at oprette en ny politik.

2. Anvend indstillingerne i følgende tabel.

3. Klik på **Gem**.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Pengeskab sammenkæder politik for alle modtagere i domænet|
|Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser|Vælg **Til – URL-adresser omskrives og kontrolleres mod en liste over kendte ondsindede links, når brugeren klikker på linket**.|
|Brug Pengeskab til at scanne indhold, der kan downloades|Markér dette felt.|
|Anvendt på|Modtagerdomænet er . . . skal du vælge dit domæne.|

Du kan finde flere oplysninger [Pengeskab Links i Defender for Office 365](../security/office-365-security/safe-links.md).

## <a name="turn-on-the-unified-audit-log"></a>Aktivere den samlede overvågningslog

Når du har aktiveret søgning i overvågningsloggen i Security & Compliance Center, kan du bevare administratoraktiviteten og anden brugeraktivitet i logfilen og søge i den.

Du skal være tildelt rollen Overvågningslogfiler Exchange Online at slå søgning i overvågningslog til eller fra i dit Microsoft 365 abonnement. Denne rolle er som standard tildelt rollegrupperne Styring af overholdelse og Organisationsadministration på siden Tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Globale administratorer i Microsoft 365 er som standard medlemmer af denne gruppe.

1. Hvis du vil aktivere søgning i overvågningsloggen <https://admin.microsoft.com> , skal du gå til Administration på og derefter vælge **Sikkerhed** under **Administrationer** i venstre navigationslinje.
2. På siden **Microsoft 365 Sikkerhed** skal du vælge Flere ressourcer og derefter åbn på kortet **Office 365 Security & Compliance Center**.

    ![Vælg Åbn i sikkerheds- & kompatibilitetsbiler.](../media/gotosecandcomp.png)
3. På siden sikkerhed og overholdelse af regler og standarder skal du **vælge Søg** og derefter **Søgning i overvågningslogfil**.
4. Øverst på siden Søgning **i overvågningslog** skal du **vælge Aktiver overvågning**.

Når funktionen er slået til, kan du søge efter filer, mapper og mange aktiviteter. Du kan få mere at vide [under Søg i overvågningsloggen](../compliance/search-the-audit-log-in-security-and-compliance.md).

## <a name="tune-up-anonymous-sharing-settings-for-sharepoint-and-onedrive-files-and-folders"></a>Finjustere anonyme indstillinger for deling SharePoint og OneDrive filer og mapper

(skift standard anonymt link udløb til 14 dage, skift standarddelingstype til "Bestemte personer") Sådan ændres indstillingerne for deling OneDrive og SharePoint:

1. Gå til Administration på, <https://admin.microsoft.com> og vælg derefter **SharePoint** under **Administration i** venstre navigationslinje.
2. I administration SharePoint skal du gå til **Deling af** \> <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**politikker**</a>.
3. På siden **Deling** **under** Fil- og mappelinks skal du vælge Bestemte **personer, og** under Avancerede indstillinger **for links til "Alle" skal** du vælge Disse **links** skal udløbe inden for dette antal dage og skrive 14 (eller et andet antal dage, du vil begrænse linkets levetid til).

   ![Vælg Bestemte personer, og angiv udløbslink til 14 dage.](../media/anyonelinks.png)

## <a name="activity-alerts"></a>Aktivitetsbeskeder

Du kan bruge aktivitetsbeskeder til at spore administrator- og brugeraktiviteter og registrere hændelser til forebyggelse af malware og datatab i organisationen. Dit abonnement omfatter et sæt standardpolitikker, men du kan også oprette brugerdefinerede politikker. Du kan finde flere oplysninger i [politikker for beskeder](../compliance/alert-policies.md). Hvis du f.eks. gemmer en vigtig fil i SharePoint som du ikke vil have nogen til at dele eksternt, kan du oprette en meddelelse, der giver dig besked, hvis nogen deler den.

I følgende figur vises de standardpolitikker, der er inkluderet Microsoft 365.

![Standardbeskedpolitikker, der er inkluderet Microsoft 365.](../media/alertpolicies.png)

## <a name="disable-or-manage-calendar-sharing"></a>Deaktiver eller administrer kalenderdeling

Du kan forhindre personer i din organisation i at dele deres kalendere, eller du kan også administrere, hvad de kan dele. Du kan f.eks. begrænse deling til kun at være ledig/optaget.

1. Gå til Administration på , og <https://admin.microsoft.com> vælg **Indstillinger** \> **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services**</a>.

1. Vælg **Kalender**, og vælg, om personer i organisationen kan dele deres kalendere med personer uden for organisationen Office 365 har Exchange kalendere eller med andre.

   Hvis du vælger indstillingen Del med alle, kan du vælge kun at dele oplysninger om ledig/optaget tid.

3. Vælg **Gem** ændringer nederst på siden.

   I følgende figur vises kalenderdeling, som ikke er tilladt.

   ![Skærmbillede af visning af ekstern kalenderdeling som ikke tilladt.](../media/nocalendarsharing.png)

   Følgende figur viser indstillingerne, når kalenderdeling er tilladt med et maillink kun med oplysninger om ledig/optaget tid.

   ![Skærmbillede af kalender, hvor ledig/optaget er delt med alle.](../media/sharefreebusy.png)

Hvis brugerne har tilladelse til at dele deres kalendere, skal du [se denne vejledning](https://support.office.com/article/7ecef8ae-139c-40d9-bae2-a23977ee58d5) til, hvordan du deler fra Outlook på internettet.
