---
title: Forøg trusselsbeskyttelse til Microsoft 365 for Business
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
description: Konfigurer Microsoft Defender til Office 365 beskytte følsomme data mod phishing, malware og andre trusler.
ms.openlocfilehash: 8bf954930edc94ccf750bb334a62a4c8a4581f80
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63596867"
---
# <a name="increase-threat-protection"></a>Forøg trusselsbeskyttelse

Denne artikel hjælper dig med at øge beskyttelsen i dit Microsoft 365-abonnement for at beskytte dig mod phishing, malware og andre trusler. Disse anbefalinger er relevante for organisationer med et øget behov for sikkerhed, f.eks. advokatkontorer og sundhedssektoren.

Før du begynder, skal du kontrollere Office 365 Secure Score. Office 365 Secure Score analyserer din organisations sikkerhed baseret på dine almindelige aktiviteter og sikkerhedsindstillinger og tildeler en score. Start med at notere dit aktuelle resultat. Hvis du vil øge din score, skal du udføre de handlinger, der anbefales i denne artikel. Målet er ikke at opnå det maksimale antal point, men at være opmærksom på muligheder for at beskytte dit miljø, der ikke påvirker produktiviteten for dine brugere negativt.

Du kan finde flere oplysninger [i Microsoft Secure Score](../../security/defender/microsoft-secure-score.md).

## <a name="raise-the-level-of-protection-against-malware-in-mail"></a>Hæve beskyttelsesniveauet mod malware i mail

Dit Office 365 eller Microsoft 365 omfatter beskyttelse mod malware. Du kan øge denne beskyttelse ved at blokere vedhæftede filer med filtyper, der ofte bruges til malware. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OA7Z?autoplay=false]

1. Fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration skal</a> du **vælge Vis flere**, **Administrationer** og derefter **Sikkerhed**.

1. Gå til **Mail & Politikker for** \> **samarbejde & regler for** \> **trusselspolitikker**.

1. Vælg Antimalware blandt **de tilgængelige politikker**.

Sådan øger du malwarebeskyttelse i mail:

1. I portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du gå til **& politikker** \> for **samarbejde & regler** \>  \> **for trussel mod malware** i **sektionen** Politikker.

2. På siden **antimalware** skal du dobbeltklikke på **Standard (standard).**. Der vises en pop op-meddelelse. 

3. Vælg **Rediger beskyttelsesindstillinger** nederst i pop op-vinduet. 

4. under **Beskyttelsesindstillinger skal** du markere afkrydsningsfeltet ud for **Aktivér filteret for almindelige vedhæftede filer**. De filtyper, der blokeres, vises direkte under dette kontrolelement. Sørg for, at du tilføjer disse filtyper:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Hvis du vil tilføje eller slette filtyper, **skal du vælge Tilpas** filtyper i slutningen af listen.

6. Vælg **Gem.**

Få mere at vide under [Beskyttelse mod malware i EOP](../../security/office-365-security/anti-malware-protection.md).

## <a name="protect-against-ransomware"></a>Beskyt dig mod ransomware

Ransomware begrænser adgangen til data ved at kryptere filer eller låse computerskærme. Det forsøger derefter at afpresse penge fra det, der er brug for, ved at bede om "ekstra penge", som regel i form af f.eks. Bitcoin, til at få adgang til data.

For at beskytte dig mod ransomware skal du oprette en eller flere regler for mailflow for at blokere filtypenavne, der ofte bruges til ransomware. (Du har tilføjet disse regler i [det højere niveau af beskyttelse mod malware i mailtrinnet](#raise-the-level-of-protection-against-malware-in-mail) .) Du kan også advare brugere, der modtager disse vedhæftede filer i en mail.

Ud over de filer, du blokerede i forrige trin, er det en god ide at oprette en regel for at advare brugerne, før du åbner Office vedhæftede filer, der indeholder makroer. Ransomware kan være skjult i makroer, så advar brugerne om ikke at åbne disse filer fra personer, de ikke kender.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

1. Fra Administration på skal du [https://admin.microsoft.com](https://admin.microsoft.com)**Exchange under** **Administration.**

1. Vælg **Mailflow** i menuen til venstre.
 
1. På fanen Regler skal du vælge pilen ud for plustegnet (+) og derefter vælge **Opret en ny regel**.

1. På siden **ny regel** skal du angive et navn til reglen, rulle ned til bunden og derefter vælge **Flere indstillinger**.

Sådan oprettes en posttrafikregel:

1. Gå til Administration på <https://admin.microsoft.com>, og vælg **Exchange** \> **.**

2. Vælg **regler i** kategorien **Mailflow**.

3. Vælg **+**, og vælg derefter **Opret en ny regel**.

4. Vælg **Flere indstillinger** nederst i dialogboksen for at få vist alle indstillinger.

5. Anvend indstillingerne i følgende tabel for reglen. Brug standardværdierne for resten af indstillingerne, medmindre du vil ændre dem.

6. Vælg **Gem**.

|Indstilling|Advar brugerne, før du åbner vedhæftede filer Office filer|
|---|---|
|Navn|Regel for anti-ransomware: advar brugere|
|Anvend denne regel, hvis . . .|Enhver vedhæftet fil . . . filtypenavnet svarer til . . .|
|Angiv ord eller udtryk|Tilføj disse filtyper:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm|
|Gør følgende. . .|Give modtageren besked med en meddelelse|
|Angiv meddelelsestekst|Du skal ikke åbne disse filtyper fra personer, du ikke kender, da de kan indeholde makroer med skadelig kode.|

Du kan finde flere oplysninger under:

- [Ransomware: Sådan reducerer du risikoen](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Gendan dine OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>Stop automatisk videresendelse for mail

Hackere, der får adgang til en brugers postkasse, kan stjæle mail ved at indstille postkassen til automatisk at videresende mails. Dette kan ske, selv uden brugerens opmærksomhed. Hvis du vil forhindre dette, skal du konfigurere en regel for mailflow.

Hvis du vil oprette en transportregel for mail, skal du følge disse trin:

1. Vælg Microsoft 365 Administration **Administrationer i** \> **Exchange**.

2. Vælg **regler i** kategorien **Mailflow**.

3. Vælg **+**, og vælg derefter **Opret en ny regel**.

4. Hvis du vil se alle indstillingerne, **skal du** vælge Flere indstillinger nederst i dialogboksen.

5. Anvend indstillingerne i følgende tabel. Brug standardværdierne for resten af indstillingerne, medmindre du vil ændre dem.

6. Vælg **Gem**.

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

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

2. Gå til **Mail & politikker** \> **for & regler for** \> **trussel mod** \> **phishing** i **sektionen** Politikker.

3. På siden **Antiphishing** skal du vælge **+ Opret**. Der startes en guide, der fører dig gennem definitionen af din antiphishingpolitik.

4. Angiv navn, beskrivelse og indstillinger for din politik som anbefalet i følgende tabel. Få mere at vide under [Få mere at vide om politikken for phishing i Microsoft Defender for Office 365 indstillinger](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Når du har gennemset dine indstillinger, skal du **vælge Opret denne politik** **eller Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Domæne og mest værdifulde kampagnemedarbejdere|
|Beskrivelse|Sørg for, at de vigtigste medarbejdere og vores domæne ikke repræsenteres.|
|Tilføj brugere, der skal beskyttes|Vælg **+ Tilføj en betingelse, modtageren er**. Skriv brugernavne, eller angiv mailadressen på kandidaterne, kampagnelederen og andre vigtige medarbejdere. Du kan tilføje op til 20 interne og eksterne adresser, du vil beskytte mod efterligning.|
|Tilføj domæner, der skal beskyttes|Vælg **+ Tilføj en betingelse, Modtagerens domæne er**. Angiv det brugerdefinerede domæne, der er knyttet Microsoft 365 abonnementet, hvis du har defineret et. Du kan angive mere end ét domæne.|
|Vælg handlinger|Hvis mail sendes af en efterligning af en bruger: Vælg Omdiriger meddelelse til en anden **mailadresse, og** skriv derefter mailadressen på sikkerhedsadministratoren. for eksempel *2010<span><span>@contoso.com*. Hvis mail sendes af et efterligning af et domæne: Vælg **meddelelse i karantæne**.|
|Postkasseintelligens|Postkasseintelligens vælges som standard, når du opretter en ny antiphishingpolitik. Lad denne indstilling være **til for** at få de bedste resultater.|
|Tilføj afsendere og domæner, der er tillid til|Her kan du tilføje dit eget domæne eller andre domæner, der er tillid til.|
|Anvendt på|Vælg **Modtagerdomænet er**. Under **Alle disse skal** du vælge **Vælg**. Vælg **+ Tilføj**. Markér afkrydsningsfeltet ud for navnet på domænet, f.eks. *contoso.<span><span> på* listen, og vælg derefter **Tilføj**. Vælg **Udført**.|

## <a name="watch-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>Se: Beskyt dig mod skadelige vedhæftede filer og filer med Pengeskab vedhæftede filer

Folk sender, modtager og deler jævnligt vedhæftede filer, f.eks. dokumenter, præsentationer, regneark og meget mere. Det er ikke altid nemt at afgøre, om en vedhæftet fil er sikker eller skadelig blot ved at se på en mail. Microsoft Defender til Office 365, tidligere kaldet Microsoft 365 ATP eller Advanced Threat Protection, omfatter Pengeskab Beskyttelse af vedhæftede filer, men denne beskyttelse er ikke slået til som standard. Vi anbefaler, at du opretter en ny regel for at begynde at bruge denne beskyttelse. Denne beskyttelse omfatter filer i SharePoint, OneDrive og Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWtn3I?autoplay=false]

1. Gå til [Administration,](https://admin.microsoft.com) og vælg **Konfiguration**.
1. Rul ned **til Forøg beskyttelsen mod avancerede trusler**. Vælg **Vis**, **Administrer og** derefter **ATP-sikrede vedhæftede filer**.
1. Vælg reglen for sikrede vedhæftede filer, og vælg derefter **ikonet** Rediger.
1. Vælg **Indstillinger**, og bekræft derefter, at Bloker er markeret.
1. Rul ned. Vælg **Aktivér omdirigering**, og angiv din mailadresse eller adressen på den person, du vil gennemse de blokerede vedhæftede filer for.
1. Vælg **anvendt på**, og vælg derefter dit domænenavn.
1. Vælg eventuelle andre domæner, du ejer (f.eks. onmicrosoft.com domæne), som reglen skal anvendes på. Vælg **Tilføj** og derefter **OK**.
1. Vælg **Gem**.

Reglen for ATP-sikrede vedhæftede filer er blevet opdateret. Nu hvor beskyttelsen er på plads, vil du ikke kunne åbne en skadelig fil fra Outlook, OneDrive, SharePoint eller Teams. Berørte filer har røde skjold ved siden af. Hvis nogen forsøger at åbne en blokeret fil, modtager de en advarselsmeddelelse.

Når din politik har været på plads i et stykke tid, kan du gå til siden Rapporter for at se, hvad der er scannet.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på med din administratorkonto.

2. Gå til **Mail & politikker** \> **for & regler for** \> **trussel** \> **mod malware** i **sektionen** Politikker.

3. Vælg **+ Opret** for at oprette en ny politik.

4. Anvend indstillingerne i følgende tabel.

5. Når du har gennemset dine indstillinger, skal **du vælge Opret denne politik** **eller Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Bloker nuværende og fremtidige mails med registreret malware.|
|Beskrivelse|Bloker nuværende og fremtidige mails og vedhæftede filer med registreret malware.|
|Gem vedhæftede filer ukendt malware svar|Vælg **Bloker – Bloker for nuværende og fremtidige mails og vedhæftede filer med registreret malware**.|
|Omdirigere vedhæftet fil ved registrering|Aktivér omdirigering (markér dette felt) Angiv administratorkontoen eller en postkassekonfiguration til karantæne.          Anvend ovenstående markering, hvis malwarescanning for vedhæftede filer får time out, eller der opstår en fejl (markér dette felt).|
|Anvendt på|Modtagerdomænet er . . . skal du vælge dit domæne.|

Du kan få mere at [vide under Konfigurer antiphishing-politikker i Microsoft Defender Office 365](../../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="protect-against-phishing-attacks-with-safe-links"></a>Beskyt dig mod phishingangreb med Pengeskab Links

Hackere skjuler sommetider ondsindede websteder i links i mails eller andre filer. Pengeskab Links, som er en del af Microsoft Defender til Office 365, kan hjælpe med at beskytte din organisation ved at angive tids-for-klik-bekræftelse af webadresser (URL-adresser) i mails og Office dokumenter. Beskyttelse defineres via Pengeskab Links-politikker.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Microsoft Defender for Office 365, tidligere kaldet Microsoft 365 ATP eller Advanced Threat Protection, hjælper med at beskytte din virksomhed mod skadelige websteder, når folk klikker på links i Office apps.

1. Gå til [Administration,](https://admin.microsoft.com) og vælg **Konfiguration**.

1. Rul ned **til Forøg beskyttelsen mod avancerede trusler**. Vælg **Administrer**, og vælg **Pengeskab Links**.

1. Vælg **Global Indstillinger,** og skriv **den URL-adresse, du vil** blokere, i Bloker følgende URL-adresser.

Vi anbefaler, at du gør følgende:

- Rediger standardpolitikken for at øge beskyttelsen.

- Tilføj en ny politik, der er målrettet alle modtagere i dit domæne.

Du kan konfigurere Pengeskab ved at udføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender,</a> og log på med din administratorkonto.

2. o to **Email & collaboration** \> **Policies & rules** \> **Threat policies** \> **Anti-malware** in **the Policies** section.

3. Vælg **+ Opret** for at oprette en ny politik eller ændre standardpolitikken.

Sådan ændres standardpolitikken:

1. Dobbeltklik **på Standardpolitikken** . Der vises en pop op-meddelelse. 

2. Vælg **Rediger beskyttelsesindstillinger** nederst i pop op-vinduet.

3. Når du har ændret standardpolitikken, skal du vælge **Gem**.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Pengeskab sammenkæder politik for alle modtagere i domænet|
|Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser|Vælg **Til – URL-adresser omskrives og kontrolleres mod en liste over kendte ondsindede links, når brugeren klikker på linket**.|
|Brug Pengeskab til at scanne indhold, der kan downloades|Markér dette felt.|
|Anvendt på|Modtagerdomænet er . . . skal du vælge dit domæne.|

Du kan finde flere oplysninger [Pengeskab Links](../../security/office-365-security/safe-links.md).

## <a name="go-to-intune-admin-center"></a>Gå til Intune Administration

1. Log på [Azure-portalen](https://portal.azure.com/).

2. Vælg **Alle tjenester** , og skriv *Intune* i **søgefeltet**.

3. Når resultaterne vises, skal du vælge startskærmen ud **for Microsoft Intune** for at gøre den til en favorit og nem at finde senere.

Ud over Administration kan du bruge Intune til at tilmelde og administrere organisationens enheder. Du kan få mere at [vide under Funktioner efter registreringsmetode til Windows og](/intune/enrollment/enrollment-method-capab) registreringsindstillinger for enheder, der [administreres af Intune](/intune/enrollment-options).
