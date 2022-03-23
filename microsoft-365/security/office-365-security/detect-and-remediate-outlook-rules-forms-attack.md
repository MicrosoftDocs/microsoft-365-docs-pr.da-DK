---
title: Registrer og afhjulpet de Outlook og brugerdefinerede formularerindskudsangreb.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: 04/23/2018
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Få mere at vide om, hvordan du genkender og afhjælper Outlook og brugerdefinerede formularindskudsangreb i Office 365
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c715552fedeefeb87206d889aa448609e8d7f60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587901"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Registrer og afhjulpet Outlook og brugerdefinerede formularindskudsangreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**Oversigt** Få mere at vide om, hvordan du genkender og afhjælper Outlook og brugerdefinerede formularindskudsangreb i Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Hvad er den Outlook- og brugerdefinerede formularindførselsangreb?

Når en hacker får adgang til din organisation, vil de forsøge at etablere et fodhold for at forblive i eller komme ind igen, når de er blevet fundet. Denne aktivitet kaldes *at etablere en vedholdende mekanisme*. Der er to måder, som en hacker kan bruge Outlook til at etablere en vedholdende mekanisme:

- Ved at udnytte Outlook regler.
- Ved at indsætte brugerdefinerede formularer i Outlook.

Det hjælper Outlook at geninstallere computeren eller endda give den pågældende person en ny computer. Når den nye installation Outlook til postkassen, synkroniseres alle regler og formularer fra skyen. Reglerne eller formularerne er typisk designet til at køre fjernkode og installere malware på den lokale computer. Malwaren stjæler legitimationsoplysninger eller udfører anden aktivitet, der er aktivitet på aktivitetsniveau.

Den gode nyhed er: Hvis du beholder dine Outlook-klienter med fejlrettelser til den nyeste version, er du ikke sårbar over for truslerne, da de aktuelle Outlook-klientstandard blokerer begge mekanismer.

Angrebene følger typisk disse mønstre:

**The Rules Exploit**:

1. Hackeren stjæler en brugers legitimationsoplysninger.

2. Hackeren logger på den pågældende brugers Exchange (Exchange Online eller en lokal Exchange).

3. Hackeren opretter en regel for videresendelse af indbakken i postkassen. Reglen for videresendelse udløses, når postkassen modtager en bestemt besked fra hackeren, der opfylder reglens betingelser. Regelbetingelserne og meddelelsesformatet skræddersys til hinanden.

4. Hackeren sender udløsermailen til den kompromitterede postkasse, som stadig bruges som normalt af intetanende bruger.

5. Når postkassen modtager en meddelelse, der opfylder reglens betingelser, anvendes reglens handling. Regelhandlingen er typisk at starte et program på en fjernserver (WebDAV).

6. Programmet installerer typisk malware på brugerens maskine (f.eks. [PowerShell Empire](https://www.powershellempire.com/)).

7. Malwaren gør det muligt for hackeren at stjæle (eller stjæle igen) brugerens brugernavn og adgangskode eller andre legitimationsoplysninger fra en lokal computer og udføre andre ondsindede aktiviteter.

**Forms Exploit**:

1. Hackeren stjæler en brugers legitimationsoplysninger.

2. Hackeren logger på den pågældende brugers Exchange (Exchange Online eller en lokal Exchange).

3. Hackeren indsætter en brugerdefineret formularskabelon i brugerens postkasse. Den brugerdefinerede formular udløses, når postkassen modtager en bestemt besked fra hackeren, der kræver, at postkassen indlæser den brugerdefinerede formular. Den brugerdefinerede formular og meddelelsesformatet er tilpasset til hinanden.

4. Hackeren sender udløsermailen til den kompromitterede postkasse, som stadig bruges som normalt af intetanende bruger.

5. Når postkassen modtager meddelelsen, indlæser postkassen den påkrævede formular. Formularen starter et program på en fjernserver (WebDAV).

6. Programmet installerer typisk malware på brugerens maskine (f.eks. [PowerShell Empire](https://www.powershellempire.com/)).

7. Malwaren gør det muligt for hackeren at stjæle (eller stjæle igen) brugerens brugernavn og adgangskode eller andre legitimationsoplysninger fra en lokal computer og udføre andre ondsindede aktiviteter.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Hvordan kan et angreb på indførsel af regler og brugerdefinerede formularer se ud Office 365?

Disse vedholdenhedsmekanismer vil sandsynligvis ikke blive bemærket af brugerne og kan i nogle tilfælde endda være usynlige. Denne artikel fortæller dig, hvordan du søger efter et af de syv tegn (Indikatorer for kompromis), der er angivet nedenfor. Hvis du finder nogen af disse, skal du gøre noget ved det.

- **Indikatorer for forlig med regler**:
  - Regelhandling er at starte et program.
  - Regel Refererer til en EXE, ZIP- eller URL-adresse.
  - På den lokale computer skal du se efter nye processtarter, der stammer fra Outlook PID.

- **Symboler for tilpassede formularer forlig:**
  - Brugerdefinerede formularer, der er gemt som deres egen meddelelsesklasse.
  - Meddelelsesklasse indeholder eksekverbar kode.
  - Ondsindede formularer gemmes typisk i private formularbiblioteker eller indbakkemapper.
  - Formular hedder IPM. Bemærk! [brugerdefineret navn].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Trin til at finde tegn på dette angreb og bekræfte det

Du kan bruge en af følgende metoder til at bekræfte angrebene:

- Undersøg regler og formularer for hver postkasse manuelt ved hjælp Outlook klient. Denne metode er grundig, men du kan kun kontrollere én postkasse ad gangen. Denne metode kan være meget tidskrævende, hvis du har mange brugere, der skal tjekke, og kan også inficere den computer, du bruger.

- Brug [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell til automatisk at gemme alle regler for videresendelse af mail og brugerdefinerede formularer for alle brugerne i dit leje. Dette er den hurtigste og sikreste metode med mindst mulige spild.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Bekræft regelangrebet ved hjælp Outlook klient

1. Åbn de brugere Outlook klient som brugeren. Brugeren har muligvis brug for din hjælp til at undersøge reglerne på sin postkasse.

2. Se Administrer [mails ved hjælp af regelartikel](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) for procedurerne til at åbne brugergrænsefladen for regler i Outlook.

3. Se efter regler, som brugeren ikke har oprettet, eller uventede regler eller regler med mistænkelige navne.

4. Se beskrivelsen af reglen for regelhandlinger, der starter og anvendes, eller se en .EXE, .ZIP eller til at starte en URL-adresse.

5. Se efter nye processer, der begynder at bruge Outlook proces-id'et. Se Find [proces-id'et](/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Trin til at bekræfte Forms-angreb med Outlook klient

1. Åbn brugeren Outlook klienten som brugeren.

2. Følg trinnene i [Vis fanen Udvikler](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) for brugerens version af Outlook.

3. Åbn den nu synlige udviklerfane i Outlook klik på **Design en formular**.

4. Vælg **Indbakke** på **listen Søg i** . Se efter eventuelle brugerdefinerede formularer. Brugerdefinerede formularer er sjældne nok til, at hvis du overhovedet har brugerdefinerede formularer, er det værd at kigge dybere.

5. Undersøg eventuelle brugerdefinerede formularer, især dem, der er markeret som skjulte.

6. Åbn eventuelle brugerdefinerede formularer, og klik **på** Vis kode i **gruppen Formular** for at se, hvad der kører, når formularen indlæses.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Trin til at bekræfte Rules and Forms-angreb ved hjælp af PowerShell

Den nemmeste måde at bekræfte et regel- eller brugerdefineret formularangreb på er at [ køreGet-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell-script. Dette script opretter forbindelse til hver postkasse i din lejer og gemmer alle regler og formularer i to .csv filer.

#### <a name="pre-requisites"></a>Forudsætninger

Du skal have globale administratorrettigheder for at køre scriptet, fordi scriptet opretter forbindelse til hver postkasse i lejen for at læse regler og formularer.

1. Log på den computer, som du vil køre scriptet fra med lokale administratorrettigheder.

2. Download eller kopiér Get-AllTenantRulesAndForms.ps1 fra GitHub til en mappe, hvorfra du kører det. Scriptet opretter to datostemplede filer til denne mappe, MailboxFormsExport-yyyy-mm-dd.csv og MailboxRulesExport-yyyy-mm-dd.csv.

3. Åbn en PowerShell-forekomst som administrator, og åbn den mappe, du gemte scriptet i.

4. Kør denne PowerShell-kommandolinje på følgende `.\Get-AllTenantRulesAndForms.ps1`måde :\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Forstå outputtet

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: Undersøg reglerne (én pr. række) for handlingsbetingelser, der omfatter programmer eller eksekverbare programmer:

  - **ActionType (kolonne A)**: Hvis du ser værdien "ID_ACTION_CUSTOM", er reglen sandsynligvis skadelig.

  - **IsPotentiallyMalicious (kolonne D)**: Hvis denne værdi er "SAND", er reglen sandsynligvis skadelig.

  - **ActionCommand (kolonne G)**: Hvis denne kolonne viser et program eller en fil med .exe- eller .zip-filtypenavne eller et ukendt element, der refererer til en URL-adresse, er reglen sandsynligvis skadelig.

- ***MailboxFormsExport-yyyy-mm-dd*.csv**: Generelt er det sjældent, at der anvendes brugerdefinerede formularer. Hvis du finder nogen i denne projektmappe, åbner du den pågældende brugers postkasse og undersøger selve formularen. Hvis din organisation ikke placerede det bevidst, er det sandsynligvis skadeligt.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Sådan stoppes og afhjælpes de Outlook Rules and Forms-angreb

Hvis du finder noget bevis for et af disse angreb, er afhjælpning enkelt, men du skal blot slette reglen eller formularen fra postkassen. Du kan gøre dette med Outlook-klienten eller ved at bruge Remote PowerShell til at fjerne regler.

### <a name="using-outlook"></a>Brug af Outlook

1. Identificer alle de enheder, som brugeren har brugt Outlook. De skal alle renses for potentielt malware. Tillad ikke, at brugeren logger på og bruger mail, før alle enhederne er ryddet.

2. Følg trinnene i Slet [en regel](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) for hver enhed.

3. Hvis du ikke er sikker på tilstedeværelsen af anden malware, kan du formatere og geninstallere al software på enheden. For mobilenheder kan du følge trinnene for producenter for at nulstille enheden til fabriksbilledet.

4. Installér de mest opdaterede versioner af Outlook. Husk, at den aktuelle version Outlook blokerer begge typer af dette angreb som standard.

5. Når alle offlinekopier af postkassen er blevet fjernet, skal du nulstille brugerens adgangskode (bruge en af høj kvalitet) og følge trinnene i Konfigurer [multifaktorgodkendelse for](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) brugere, hvis MFA ikke allerede er aktiveret. Dette sikrer, at brugerens legitimationsoplysninger ikke er synlige på andre måder (f.eks. at phishing eller adgangskode bruges igen).

### <a name="using-powershell"></a>Brug af PowerShell

Der er to Eksterne PowerShell-cmdlet'er, du kan bruge til at fjerne eller deaktivere skadelige regler. Følg blot trinnene.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Trin til postkasser, der er på Exchange server

1. Forbind til Exchange ved hjælp af Remote PowerShell. Følg trinnene i [PowerShell Forbind til Exchange servere, der bruger Remote PowerShell](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell).

2. Hvis du helt vil fjerne en enkelt regel, flere regler eller alle regler fra en postkasse, skal du bruge [cmdlet'en Remove-InboxRule](/powershell/module/exchange/Remove-InboxRule) .

3. Hvis du vil bevare reglen og dens indhold til yderligere undersøgelse, skal du bruge [cmdlet'en Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Trin til postkasser i Exchange Online

1. Følg trinnene i Trin Forbind [at Exchange Online ved hjælp af PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Hvis du helt vil fjerne en enkelt regel, flere regler eller alle regler fra en postkasse, skal du bruge [cmdlet'en Remove-Inbox Rule](/powershell/module/exchange/Remove-InboxRule) .

3. Hvis du vil bevare reglen og dens indhold til yderligere undersøgelse, skal du bruge [cmdlet'en Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

## <a name="how-to-minimize-future-attacks"></a>Sådan minimerer du fremtidige angreb

### <a name="first-protect-your-accounts"></a>Først skal du beskytte dine konti

De udnyttede regler og formularer bruges kun af en hacker, når han eller hun har stjålet eller brudt en af dine brugeres konti. Så dit første trin til at forhindre brugen af disse udnyttelseer mod din organisation er at beskytte dine brugerkonti aggressive. Nogle af de mest almindelige måder, konti misligholdes på, er via phishing [- eller adgangskodeangreb](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

Den bedste måde at beskytte dine brugerkonti, og især dine administratorkonti, er at [konfigurere multifaktorgodkendelse for brugere](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Du skal også:

- Overvåg, hvordan dine brugerkonti [tilgås og bruges](/azure/active-directory/active-directory-view-access-usage-reports). Du kan ikke forhindre den indledende misligholdelse, men du vil forkorte varigheden og effekten af den ved at registrere den tidligere. Du kan bruge disse [Office 365 Cloud App Security til](/cloud-app-security/what-is-cloud-app-security) at overvåge dine konti og give besked om usædvanlig aktivitet:

  - **Flere mislykkede logonforsøg**: Dette brugerprofil i dit miljø og udløser beskeder, når brugere udfører flere mislykkede logonaktiviteter i en enkelt session i forhold til den lærde grundlinje, hvilket kunne indikere et forsøg på misligholdelse.

  - **Umulig rejse**: Denne politikprofiler dit miljø og udløser beskeder, når aktiviteter registreres fra den samme bruger på forskellige steder inden for en tidsperiode, der er kortere end den forventede rejsetid mellem de to placeringer. Dette kan betyde, at en anden bruger bruger de samme legitimationsoplysninger. Det at registrere denne unormale adfærd medfører en startlæringsperiode på syv dage, hvor den lærer en ny brugers aktivitetsmønster at vide.

  - **Usædvanlig impersonated activity (by user)**: This policy profiles your environment and triggers alerts when users perform multiple impersonated activities in a single session with the baseline learned, which could indicate an attempted breach.

- Brug et værktøj som [f.Office 365 Secure Score](https://securescore.office.com/) til at administrere kontosikkerhedskonfigurationer og -funktionsmåder.

### <a name="second-keep-your-outlook-clients-current"></a>Andet: Hold dine Outlook klienter opdateret

Fuldt opdaterede og patcherede versioner af Outlook 2013 og 2016 deaktiverer som standard reglen/formularhandlingen "Start program". Dette sikrer, at selv hvis en hacker overtræder kontoen, blokeres regel- og formularhandlingerne. Du kan installere de seneste opdateringer og sikkerhedsrettelser ved at følge trinnene i [Installér Office opdateringer](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5).

Her er patchversionerne til dine Outlook 2013- og 2016-klienter:

- **Outlook 2016**: 16.0.4534.1001 eller højere.

- **Outlook 2013**: 15.0.4937.1000 eller større.

Du kan finde flere oplysninger om de enkelte sikkerhedsrettelser i:

- [Outlook 2016 sikkerhedsrettelse](https://support.microsoft.com/help/3191883)

- [Outlook 2013-sikkerhedsrettelse](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Tredje: Overvåg dine Outlook klienter

Bemærk, at selv med rettelserne og opdateringerne installeret, er det muligt for en hacker at ændre konfigurationen af den lokale maskine for at genaktivere "Start application"-funktionsmåden. Du kan bruge [Advanced Gruppepolitik Management til](/microsoft-desktop-optimization-pack/agpm/) at overvåge og håndhæve lokale computerpolitikker på dine kunder.

Du kan se, om "Start program" er blevet aktiveret igen via en tilsidesættelse i registreringsdatabasen ved hjælp af oplysningerne i Sådan får du vist systemregistreringsdatabasen ved hjælp af [64-bit versioner af Windows](https://support.microsoft.com/help/305097). Kontrollér disse undernøgler:

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

Se efter nøglen EnableUnsafeClientMailRules. Hvis den er der og er indstillet til 1, er Outlook blevet tilsidesat, og computeren er sårbar over for Formular/Regel-angreb. Hvis værdien er 0, deaktiveres handlingen "Start program". Hvis den opdaterede og patcherede version af Outlook er installeret, og denne registreringsdatabasenøgle ikke findes, er et system ikke sårbar over for disse angreb.

Kunder med lokale installationer Exchange overveje at blokere ældre versioner af Outlook, der ikke har tilgængelige programrettelser. Du kan finde oplysninger om denne proces i artiklen Konfigurer [blokering Outlook klient](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Beskyt Microsoft 365 som en cybersecurity-pro

Dit Microsoft 365-abonnement leveres med et effektivt sæt sikkerhedsfunktioner, som du kan bruge til at beskytte dine data og dine brugere. Brug [Microsoft 365-sikkerhedsoversigten – Topprioriteter for de første 30 dage, 90](security-roadmap.md) dage og derefter for at implementere anbefalede microsoft-fremgangsmåder til sikring af din Microsoft 365 lejer.

- Opgaver, der skal udføres inden for de første 30 dage. Disse har øjeblikkelig virkning og har lav effekt for dine brugere.

- Opgaver, der skal udføres på 90 dage. Disse tager lidt mere tid at planlægge og implementere, men i høj grad forbedre din sikkerhed.

- Mere end 90 dage. Disse forbedringer er en del af dit første arbejde på 90 dage.

## <a name="see-also"></a>Se også:

- [Ondsindede Outlook af](https://silentbreaksecurity.com/malicious-outlook-rules/) SilentBreak Security Post om regelvektor giver en detaljeret gennemgang af, hvordan reglerne Outlook regler.

- [MAPI over HTTP og Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) på Sensepost-bloggen om Mailrule Pwnage diskuterer et værktøj kaldet Lineal, der gør det muligt at udnytte postkasser via Outlook regler.

- [Outlook formularer og shells på](https://sensepost.com/blog/2017/outlook-forms-and-shells/) Sensepost-bloggen om Forms Threat Vector.

- [Linealkodebase](https://github.com/sensepost/ruler)

- [Linealindikatorer for kompromis](https://github.com/sensepost/notruler/blob/master/iocs.md)