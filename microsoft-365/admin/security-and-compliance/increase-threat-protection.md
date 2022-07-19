---
title: Øg trusselsbeskyttelsen for Microsoft 365 til virksomheder
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
description: Konfigurer Microsoft Defender for Office 365 og beskyt følsomme data mod phishing, malware og andre trusler.
ms.openlocfilehash: fe7a70b8418ef4658b173611b0c940a0932736d9
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66858915"
---
# <a name="increase-threat-protection-for-microsoft-365-for-business"></a>Øg trusselsbeskyttelsen for Microsoft 365 til virksomheder

Se [Microsoft 365 small business-hjælp](https://go.microsoft.com/fwlink/?linkid=2197659) på YouTube.

Denne artikel hjælper dig med at øge beskyttelsen i dit Microsoft 365-abonnement for at beskytte mod phishing, malware og andre trusler. Disse anbefalinger er passende for organisationer med et øget behov for sikkerhed, som advokatkontorer og sundhedsklinikker.

Før du begynder, skal du kontrollere din Office 365 Secure Score. Office 365 Secure Score analyserer din organisations sikkerhed baseret på dine almindelige aktiviteter og sikkerhedsindstillinger og tildeler en score. Begynd med at tage din aktuelle score til efterretning. Hvis du vil øge din score, skal du fuldføre de handlinger, der anbefales i denne artikel. Målet er ikke at opnå den maksimale score, men at være opmærksom på muligheder for at beskytte dit miljø, der ikke påvirker produktiviteten for dine brugere negativt.

Du kan få flere oplysninger under [Microsoft Secure Score](../../security/defender/microsoft-secure-score.md).

## <a name="watch-raise-the-level-of-protection-against-malware-in-mail"></a>Se: Hæv beskyttelsesniveauet mod malware i mails

Dit Office 365- eller Microsoft 365-miljø omfatter beskyttelse mod malware. Du kan øge denne beskyttelse ved at blokere vedhæftede filer med filtyper, der ofte bruges til malware. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4OA7Z?autoplay=false]

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> skal du vælge **Vis flere****, Administration centre** og derefter **Sikkerhed**.

1. Gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker**.

1. Vælg **Antimalware** blandt de tilgængelige politikker.

Sådan øger du beskyttelse mod skadelig software i mail:

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> skal du gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Antimalware** i afsnittet **Politikker**.

1. Dobbeltklik på **Standard (standard)** på siden **Antimalware**. Der vises et pop op-vindue. 

1. Vælg **Rediger beskyttelsesindstillinger** nederst i pop op-vinduet. 

1. under **Beskyttelsesindstillinger** skal du markere afkrydsningsfeltet ud for **Aktivér filteret for almindelige vedhæftede filer**. De blokerede filtyper vises direkte under dette kontrolelement. Sørg for at tilføje disse filtyper:

   `ade, adp, ani, bas, bat, chm, cmd, com, cpl, crt, hlp, ht, hta, inf, ins, isp, job, js, jse, lnk, mda, mdb, mde, mdz, msc, msi, msp, mst, pcd, reg, scr, sct, shs, url, vb, vbe, vbs, wsc, wsf, wsh, exe, pif`

   Hvis du vil tilføje eller slette filtyper, skal du vælge **Tilpas filtyper** i slutningen af listen.

1. Vælg **Gem.**

Du kan få flere oplysninger under [Beskyttelse mod skadelig software i EOP](../../security/office-365-security/anti-malware-protection.md).

## <a name="watch-protect-against-ransomware"></a>Se: Beskyt mod ransomware

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198018).

Ransomware begrænser adgangen til data ved at kryptere filer eller låse computerskærme. Det forsøger derefter at afpresse penge fra ofre ved at bede om "løsesum", som regel i form af kryptovalutaer som Bitcoin, i bytte for adgang til data.

For at beskytte mod ransomware skal du oprette en eller flere regler for mailflow for at blokere filtypenavne, der ofte bruges til ransomware. (Du har tilføjet disse regler i [Watch: Hæv niveauet af beskyttelse mod malware i mail-trinnet](#watch-raise-the-level-of-protection-against-malware-in-mail) .) Du kan også advare brugere, der modtager disse vedhæftede filer i en mail.

Ud over de filer, du blokerede i det forrige trin, er det en god idé at oprette en regel, der advarer brugerne, før du åbner vedhæftede filer i Office, der indeholder makroer. Ransomware kan skjules i makroer, så advar brugerne om ikke at åbne disse filer fra personer, de ikke kender.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWrWGt?autoplay=false]

1. Vælg **Exchange** under **Administration centre** i Administration på [https://admin.microsoft.com](https://admin.microsoft.com).

1. Vælg **Mailflow** i menuen til venstre.
 
1. Under fanen Regler skal du vælge pilen ud for plussymbolet (+) og derefter vælge **Opret en ny regel**.

1. Angiv et navn til reglen på den **nye regelside** , rul ned til bunden, og vælg derefter **Flere indstillinger**.

Sådan opretter du en regel for mailtransport:

1. Gå til Administration på <https://admin.microsoft.com>, og vælg **Administration centre** \> **Exchange**.

2. Vælg **regler** i kategorien **mailflow**.

3. Vælg **+**, og vælg derefter **Opret en ny regel**.

4. Vælg **Flere indstillinger** nederst i dialogboksen for at se det fulde sæt indstillinger.

5. Anvend indstillingerne i følgende tabel for reglen. Brug standardværdierne til resten af indstillingerne, medmindre du vil ændre dem.

6. Vælg **Gem**.

|Indstilling|Advar brugere, før de åbner vedhæftede filer i Office-filer|
|---|---|
|Navn|Anti-ransomware-regel: advar brugere|
|Anvend denne regel, hvis . . .|Alle vedhæftede filer . . . filtypenavnet svarer til . . .|
|Angiv ord eller udtryk|Tilføj disse filtyper:  <br/> dotm, docm, xlsm, sltm, xla, xlam, xll, pptm, potm, ppam, ppsm, sldm|
|Benyt følgende fremgangsmåde . . .|Giv modtageren besked med en meddelelse|
|Angiv meddelelsestekst|Undlad at åbne disse filtyper fra personer, du ikke kender, fordi de kan indeholde makroer med skadelig kode.|

Du kan finde flere oplysninger under:

- [Ransomware: Sådan reducerer du risikoen](https://www.microsoft.com/security/blog/2020/04/28/ransomware-groups-continue-to-target-healthcare-critical-services-heres-how-to-reduce-risk/)

- [Gendan dit OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15)

## <a name="stop-auto-forwarding-for-email"></a>Stop automatisk videresendelse af mail

Hackere, der får adgang til en brugers postkasse, kan stjæle mail ved at indstille postkassen til automatisk at videresende mail. Dette kan ske selv uden brugerens opmærksomhed. Du kan forhindre, at dette sker, ved at konfigurere en regel for et mailflow.

Følg disse trin for at oprette en regel for mailtransport:

1. I Microsoft 365 Administration skal du vælge **Administration centre** \> **Exchange**.

2. Vælg **regler** i kategorien **mailflow**.

3. Vælg **+**, og vælg derefter **Opret en ny regel**.

4. Hvis du vil se alle indstillingerne, skal du vælge **Flere indstillinger** nederst i dialogboksen.

5. Anvend indstillingerne i følgende tabel. Brug standardværdierne til resten af indstillingerne, medmindre du vil ændre dem.

6. Vælg **Gem**.

|Indstilling|Advar brugere, før de åbner vedhæftede filer i Office-filer|
|---|---|
|Navn|Undgå automatisk videresendelse af mail til eksterne domæner|
|Anvend denne regel, hvis ...|Afsenderen . . . er ekstern/intern . . . Inde i organisationen|
|Tilføj betingelse|Meddelelsesegenskaberne . . . medtag meddelelsestypen . . . Fremadrettet automatisk|
|Gør følgende...|Bloker meddelelsen . . . afvis meddelelsen, og medtag en forklaring.|
|Angiv meddelelsestekst|Automatisk videresendelse af mails uden for denne organisation forhindres af sikkerhedsmæssige årsager.|

## <a name="watch-protect-your-email-from-phishing-attacks"></a>Se: Beskyt din mail mod phishingangreb

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198014).

Hvis du har konfigureret et eller flere brugerdefinerede domæner til dit Office 365- eller Microsoft 365-miljø, kan du konfigurere målrettet beskyttelse mod phishing. Beskyttelse mod phishing, som er en del af Microsoft Defender for Office 365, kan hjælpe med at beskytte din organisation mod ondsindede efterligningsbaserede phishingangreb og andre phishingangreb. Hvis du ikke har konfigureret et brugerdefineret domæne, behøver du ikke at gøre dette.

Vi anbefaler, at du kommer i gang med denne beskyttelse ved at oprette en politik, der beskytter dine vigtigste brugere og dit brugerdefinerede domæne.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvt9r?autoplay=false]

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

2. Gå til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Anti-phishing** i afsnittet **Politikker** .

3. Vælg **+ Opret** på siden **Anti-phishing**. En guide starter en guide, der fører dig gennem definition af din anti-phishing-politik.

4. Angiv navnet, beskrivelsen og indstillingerne for politikken som anbefalet i følgende tabel. Du kan finde flere oplysninger under [Få mere at vide om anti-phishing-politik i Microsoft Defender for Office 365 indstillinger](../../security/office-365-security/set-up-anti-phishing-policies.md).

5. Når du har gennemset dine indstillinger, skal du vælge **Opret denne politik** eller **Gem** efter behov.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Domæne og de mest værdifulde kampagnemedarbejdere|
|Beskrivelse|Sørg for, at de vigtigste medarbejdere og vores domæne ikke repræsenteres.|
|Tilføj brugere for at beskytte|Vælg **+ Tilføj en betingelse. Modtageren er**. Skriv brugernavne, eller angiv mailadressen på kandidaten, kampagnelederen og andre vigtige medarbejdere. Du kan tilføje op til 20 interne og eksterne adresser, som du vil beskytte mod repræsentation.|
|Tilføj domæner for at beskytte|Vælg **+ Tilføj en betingelse. Modtagerdomænet er**. Angiv det brugerdefinerede domæne, der er knyttet til dit Microsoft 365-abonnement, hvis du har defineret et. Du kan angive mere end ét domæne.|
|Vælg handlinger|Hvis mail sendes af en repræsenteret bruger: Vælg **Omdiriger meddelelse til en anden mailadresse**, og skriv derefter sikkerhedsadministratorens mailadresse. Alice *<span><span>@contoso.com*. Hvis mail sendes af et repræsenterede domæne: Vælg **Karantænemeddelelse**.|
|Postkasseintelligens|Postkasseintelligens vælges som standard, når du opretter en ny politik mod phishing. Lad denne indstilling være **slået** til for at opnå de bedste resultater.|
|Tilføj afsendere og domæner, der er tillid til|Her kan du tilføje dit eget domæne eller andre domæner, der er tillid til.|
|Anvendt på|Vælg **Modtagerdomænet er**. Under **Et af disse** skal du vælge **Vælg**. Vælg **+ Tilføj**. Markér afkrydsningsfeltet ud for navnet på domænet, f.eks *. contoso.<span><span> på* listen, og vælg derefter **Tilføj**. Vælg **Udført**.|

## <a name="watch-protect-against-malicious-attachments-and-files-with-safe-attachments"></a>Se: Beskyt mod skadelige vedhæftede filer og filer med sikre vedhæftede filer

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198019).

Folk sender, modtager og deler jævnligt vedhæftede filer, f.eks. dokumenter, præsentationer, regneark og meget mere. Det er ikke altid nemt at se, om en vedhæftet fil er sikker eller ondsindet bare ved at se på en mail. Microsoft Defender for Office 365, der tidligere hed Microsoft 365 ATP eller Advanced Threat Protection, omfatter sikker beskyttelse af vedhæftede filer, men denne beskyttelse er ikke aktiveret som standard. Vi anbefaler, at du opretter en ny regel for at begynde at bruge denne beskyttelse. Denne beskyttelse omfatter også filer i SharePoint, OneDrive og Microsoft Teams.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWtn3I?autoplay=false]

1. Gå til [Administration](https://admin.microsoft.com), og vælg **Konfiguration**.
1. Rul ned for at **øge beskyttelsen mod avancerede trusler**. Vælg **Vis**, **Administrer** og derefter **ATP-sikre vedhæftede filer**.
1. Vælg reglen for sikre vedhæftede filer, og vælg derefter ikonet **Rediger** .
1. Vælg **indstillinger**, og bekræft derefter, at Bloker er valgt.
1. Rul ned. Vælg **Aktivér omdirigering**, og angiv din mailadresse eller adressen på den person, du vil gennemse de blokerede vedhæftede filer.
1. Vælg **Anvendt på**, og vælg derefter dit domænenavn.
1. Vælg eventuelle yderligere domæner, du ejer (f.eks. dit onmicrosoft.com domæne), som reglen skal anvendes på. Vælg **Tilføj** og derefter **OK**.
1. Vælg **Gem**.

Reglen for sikre vedhæftede filer i ATP er blevet opdateret. Nu, hvor beskyttelsen er på plads, kan du ikke åbne en skadelig fil fra Outlook, OneDrive, SharePoint eller Teams. De berørte filer vil have røde skjolde ved siden af dem. Hvis nogen forsøger at åbne en blokeret fil, modtager de en advarselsmeddelelse.

Når din politik har været på plads i et stykke tid, kan du gå til siden Rapporter for at se, hvad der er blevet scannet.

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
|Omdiriger vedhæftet fil ved registrering|Aktivér omdirigering (markér dette felt) Angiv administratorkontoen eller en postkassekonfiguration til karantæne.          Anvend ovenstående valg, hvis der opstår timeout for malwarescanning efter vedhæftede filer, eller der opstår fejl (markér dette felt).|
|Anvendt på|Modtagerdomænet er . . . vælg dit domæne.|

Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](../../security/office-365-security/set-up-anti-phishing-policies.md).

## <a name="watch-protect-against-phishing-attacks-with-safe-links"></a>Se: Beskyt mod phishingangreb med sikre links

Se denne og andre videoer på vores [YouTube-kanal](https://go.microsoft.com/fwlink/?linkid=2198201).

Hackere skjuler nogle gange ondsindede websteder i links i e-mail eller andre filer. Sikre links, der er en del af Microsoft Defender for Office 365, kan hjælpe med at beskytte din organisation ved at give bekræftelse af webadresser (URL-adresser) i mails og Office-dokumenter. Beskyttelse defineres via politikker for sikre links.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWvdwy?autoplay=false]

Microsoft Defender for Office 365, der tidligere hed Microsoft 365 ATP eller Advanced Threat Protection, hjælper med at beskytte din virksomhed mod skadelige websteder, når folk klikker på links i Office-apps.

1. Gå til [Administration](https://admin.microsoft.com), og vælg **Konfiguration**.

1. Rul ned for at **øge beskyttelsen mod avancerede trusler**. Vælg **Administrer** og derefter **Sikre links**.

1. Vælg **Globale indstillinger** , og angiv den URL-adresse, du vil blokere, i **Bloker følgende URL-adresser**.

Vi anbefaler, at du gør følgende:

- Rediger standardpolitikken for at øge beskyttelsen.

- Tilføj en ny politik, der er målrettet til alle modtagere i dit domæne.

Hvis du vil konfigurere Sikre links, skal du udføre følgende trin:

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>, og log på med din administratorkonto.

2. o til **Mail & samarbejdspolitikker** \> **& regler** \> **Trusselspolitikker** \> **Antimalware** i afsnittet **Politikker** .

3. Vælg **+ Opret** for at oprette en ny politik, eller rediger standardpolitikken.

Sådan redigerer du standardpolitikken:

1. Dobbeltklik på **standardpolitikken** . Der vises et pop op-vindue. 

2. Vælg **Rediger beskyttelsesindstillinger** nederst i pop op-vinduet.

3. Når du har ændret standardpolitikken, skal du vælge **Gem**.

|Indstilling eller indstilling|Anbefalet indstilling|
|---|---|
|Navn|Politik for sikre links for alle modtagere i domænet|
|Vælg handlingen for ukendte potentielt skadelige URL-adresser i meddelelser|Vælg **Til – URL-adresser omskrives og kontrolleres i forhold til en liste over kendte skadelige links, når brugeren klikker på linket**.|
|Brug Sikre vedhæftede filer til at scanne indhold, der kan downloades|Markér dette felt.|
|Anvendt på|Modtagerdomænet er . . . vælg dit domæne.|

Du kan få flere oplysninger under [Sikre links](../../security/office-365-security/safe-links.md).

## <a name="go-to-intune-admin-center"></a>Gå til Intune Administration

1. Log på [Azure Portal](https://portal.azure.com/).

2. Vælg **Alle tjenester**, og skriv *Intune* i **søgefeltet**.

3. Når resultaterne vises, skal du vælge start ud for **Microsoft Intune** for at gøre det til en favorit og nemt at finde senere.

Ud over Administration kan du bruge Intune til at tilmelde og administrere organisationens enheder. Du kan få flere oplysninger [under Egenskaber efter tilmeldingsmetode for Windows-enheder](/intune/enrollment/enrollment-method-capab) og [Tilmeldingsindstillinger for enheder, der administreres af Intune](/intune/enrollment-options).
