---
title: Find og afhjælp de Outlook regler og angreb på brugerdefinerede formularer.
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
description: Få mere at vide om, hvordan du genkender og afhjælper Outlook regler og brugerdefinerede formularinjektioner i Office 365
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 370fa7cf6e8003954044290b7c19c3d839b0a145
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016026"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Registrer og afhjælp Outlook regler og angreb på brugerdefinerede formularer

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Resumé** Få mere at vide om, hvordan du genkender og afhjælper de Outlook regler og brugerdefinerede formularinjektionsangreb i Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Hvad er indsprøjtningsangrebet Outlook regler og brugerdefinerede formularer?

Når en person med ondsindede hensigter får adgang til din organisation, forsøger de at etablere et fodfæste for at blive i eller komme tilbage, når de er blevet opdaget. Denne aktivitet kaldes *oprettelse af en fastholdelsesmekanisme*. En hacker kan bruge Outlook til at etablere en fastholdelsesmekanisme på to måder:

- Ved at udnytte Outlook regler.
- Ved at indsætte brugerdefinerede formularer i Outlook.

Det hjælper ikke at geninstallere Outlook eller endda give den pågældende person en ny computer. Når den nye installation af Outlook opretter forbindelse til postkassen, synkroniseres alle regler og formularer fra cloudmiljøet. Reglerne eller formularerne er typisk designet til at køre fjernkode og installere malware på den lokale computer. Malwaren stjæler legitimationsoplysninger eller udfører andre ulovlige aktiviteter.

Den gode nyhed er: Hvis du holder dine Outlook klienter lappet til den nyeste version, er du ikke sårbar over for truslen, da aktuelle Outlook klientstandarder blokerer begge mekanismer.

Angrebene følger typisk disse mønstre:

**Udnyt reglerne**:

1. Hackeren stjæler en brugers legitimationsoplysninger.

2. Hackeren logger på den pågældende brugers Exchange postkasse (Exchange Online eller Exchange i det lokale miljø).

3. Hackeren opretter en regel for videresendelse af Indbakke i postkassen. Videresendelsesreglen udløses, når postkassen modtager en bestemt meddelelse fra hackeren, der svarer til betingelserne i reglen. Regelbetingelserne og meddelelsesformatet skræddersys til hinanden.

4. Hackeren sender den udløsende mail til den kompromitterede postkasse, som stadig bruges som normalt af den intetanende bruger.

5. Når postkassen modtager en meddelelse, der opfylder betingelserne i reglen, anvendes reglens handling. Regelhandlingen er typisk at starte et program på en ekstern (WebDAV)-server.

6. Programmet installerer typisk malware på brugerens computer (f.eks [. PowerShell Empire](https://www.powershellempire.com/)).

7. Malwaren gør det muligt for hackeren at stjæle (eller stjæle igen) brugerens brugernavn og adgangskode eller andre legitimationsoplysninger fra lokal computer og udføre andre skadelige aktiviteter.

**Udnyttelse af formularer**:

1. Hackeren stjæler en brugers legitimationsoplysninger.

2. Hackeren logger på den pågældende brugers Exchange postkasse (Exchange Online eller Exchange i det lokale miljø).

3. Hackeren indsætter en brugerdefineret mailformularskabelon i brugerens postkasse. Den brugerdefinerede formular udløses, når postkassen modtager en bestemt meddelelse fra hackeren om, at postkassen skal indlæse den brugerdefinerede formular. Den brugerdefinerede formular og meddelelsesformatet er skræddersyet til hinanden.

4. Hackeren sender den udløsende mail til den kompromitterede postkasse, som stadig bruges som normalt af den intetanende bruger.

5. Når postkassen modtager meddelelsen, indlæser postkassen den påkrævede formular. Formularen starter et program på en ekstern server (WebDAV).

6. Programmet installerer typisk malware på brugerens computer (f.eks [. PowerShell Empire](https://www.powershellempire.com/)).

7. Malwaren gør det muligt for hackeren at stjæle (eller stjæle igen) brugerens brugernavn og adgangskode eller andre legitimationsoplysninger fra lokal computer og udføre andre skadelige aktiviteter.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Hvordan kan et angreb med en regel- og brugerdefineret formularinjektion se ud Office 365?

Det er usandsynligt, at brugerne lægger mærke til disse fastholdelsesmekanismer, og de kan i nogle tilfælde endda være usynlige for dem. I denne artikel kan du se, hvordan du søger efter et af de syv tegn (indikatorer for kompromis), der er angivet nedenfor. Hvis du finder nogen af disse, skal du udføre afhjælpningsforanstaltninger.

- **Indikatorer for forretningsordenen kompromitterer**:
  - Regelhandling er at starte et program.
  - Regel henviser til en EXE-, ZIP- eller URL-adresse.
  - På den lokale maskine skal du søge efter nye processer, der stammer fra Outlook PID.

- **Indikatorer for brugerdefinerede formularer kompromitteres**:
  - Brugerdefinerede formularer, der vises som deres egen meddelelsesklasse.
  - Meddelelsesklassen indeholder eksekverbar kode.
  - Ondsindede formularer gemmes typisk i biblioteket med personlige formularer eller i indbakkemapper.
  - Formularen hedder IPM. Bemærk. [brugerdefineret navn].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Trin til at finde tegn på dette angreb og bekræfte det

Du kan bruge en af følgende metoder til at bekræfte angrebet:

- Undersøg reglerne og formularerne for hver postkasse manuelt ved hjælp af Outlook-klienten. Denne metode er grundig, men du kan kun kontrollere én postkasse ad gangen. Denne metode kan være meget tidskrævende, hvis du har mange brugere at kontrollere, og den kan også inficere den computer, du bruger.

- Brug [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell-scriptet til automatisk at dumpe alle regler for videresendelse af mail og brugerdefinerede formularer for alle brugerne i din lejer. Dette er den hurtigste og sikreste metode med den mindste mængde overhead.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Bekræft regelangrebet ved hjælp af Outlook-klienten

1. Åbn brugerne Outlook klient som brugeren. Brugeren har muligvis brug for din hjælp til at undersøge reglerne i sin postkasse.

2. Se artiklen [Administrer mails ved hjælp af regler](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) for at få oplysninger om, hvordan du åbner regelgrænsefladen i Outlook.

3. Søg efter regler, som brugeren ikke har oprettet, eller eventuelle uventede regler eller regler med mistænkelige navne.

4. Se regelbeskrivelsen for regelhandlinger, der starter og programmer, eller som refererer til en .EXE, .ZIP fil eller til at starte en URL-adresse.

5. Søg efter nye processer, der begynder at bruge proces-id'et Outlook. Se [Find proces-id'et](/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Trin til bekræftelse af formularangrebet ved hjælp af Outlook-klienten

1. Åbn brugeren Outlook klient som bruger.

2. Følg trinnene i [Vis fanen Udvikler](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) for brugerens version af Outlook.

3. Åbn den nu synlige udviklerfane i Outlook, og klik på **Design en formular**.

4. Vælg **Indbakke** på listen **Søg i** . Søg efter brugerdefinerede formularer. Brugerdefinerede formularer er sjældne nok til, at hvis du overhovedet har brugerdefinerede formularer, er det værd at se nærmere på dem.

5. Undersøg alle brugerdefinerede formularer, især dem, der er markeret som skjulte.

6. Åbn brugerdefinerede formularer, og klik på **Vis kode** i gruppen **Formular** for at se, hvad der kører, når formularen indlæses.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>Trin til bekræftelse af angrebet med regler og formularer ved hjælp af PowerShell

Den nemmeste måde at bekræfte et angreb på regler eller brugerdefinerede formularer på er ved at køre [Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell-scriptet. Dette script opretter forbindelse til alle postkasser i din lejer og gemmer alle regler og formularer i to .csv filer.

#### <a name="pre-requisites"></a>Forudsætninger

Du skal have globale administratorrettigheder for at køre scriptet, fordi scriptet opretter forbindelse til alle postkasser i lejeren for at læse reglerne og formularerne.

1. Log på den computer, du vil køre scriptet fra, med lokale administratorrettigheder.

2. Download eller kopiér Get-AllTenantRulesAndForms.ps1 scriptet fra GitHub til en mappe, du vil køre det fra. Scriptet opretter to datostemplede filer til denne mappe, MailboxFormsExport-yyyy-mm-dd.csv og MailboxRulesExport-yyyy-mm-dd.csv.

3. Åbn en PowerShell-forekomst som administrator, og åbn den mappe, du gemte scriptet i.

4. Kør denne PowerShell-kommandolinje på følgende måde `.\Get-AllTenantRulesAndForms.ps1`:\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Fortolkning af outputtet

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: Undersøg reglerne (én pr. række) for handlingsbetingelser, der omfatter programmer eller eksekverbare filer:

  - **ActionType (kolonne A)**: Hvis du ser værdien "ID_ACTION_CUSTOM", er reglen sandsynligvis skadelig.

  - **IsPotentiallyMalicious (kolonne D):** Hvis denne værdi er "TRUE", er reglen sandsynligvis skadelig.

  - **ActionCommand (kolonne G)**: Hvis denne kolonne viser et program eller en fil med .exe eller .zip filtypenavne eller en ukendt post, der refererer til en URL-adresse, er reglen sandsynligvis skadelig.

- ***MailboxFormsExport-yyyy-mm-dd*.csv**: Generelt er brugen af brugerdefinerede formularer sjældent. Hvis du finder nogen i denne projektmappe, skal du åbne den pågældende brugers postkasse og undersøge selve formularen. Hvis din organisation ikke har angivet den med vilje, er det sandsynligvis skadeligt.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Sådan stopper og afhjælper du angreb på Outlook regler og formularer

Hvis du finder beviser for et af disse angreb, er afhjælpning enkel, du skal blot slette reglen eller formularen fra postkassen. Du kan gøre dette med Outlook-klienten eller bruge Exchange PowerShell til at fjerne regler.

### <a name="using-outlook"></a>Brug af Outlook

1. Identificer alle de enheder, som brugeren har brugt sammen med Outlook. De vil alle nødt til at blive renset for potentiel malware. Tillad ikke, at brugeren logger på og bruger mail, før alle enhederne er renset.

2. Følg trinnene i [Slet en regel](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) for hver enhed.

3. Hvis du er usikker på tilstedeværelsen af anden malware, kan du formatere og geninstallere al softwaren på enheden. For mobilenheder kan du følge producentens trin for at nulstille enheden til fabriksbilledet.

4. Installér de nyeste versioner af Outlook. Husk, at den aktuelle version af Outlook blokerer begge typer af dette angreb som standard.

5. Når alle offlinekopier af postkassen er blevet fjernet, skal du nulstille brugerens adgangskode (bruge en høj kvalitet) og følge trinnene i [Konfigurer multifaktorgodkendelse for brugere](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) , hvis MFA ikke allerede er aktiveret. Dette sikrer, at brugerens legitimationsoplysninger ikke eksponeres via andre metoder (f.eks. phishing eller genbrug af adgangskode).

### <a name="using-powershell"></a>Brug af PowerShell

Der er to Exchange PowerShell-cmdlet'er, du kan bruge til at fjerne eller deaktivere farlige regler. Du skal blot følge trinnene.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Trin til postkasser på en Exchange server

1. Forbind til Exchange-serveren ved hjælp af PowerShell eller Exchange Management Shell. Følg trinnene i [Forbind for at Exchange servere ved hjælp af Ekstern PowerShell](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell) eller [Åbn Exchange Management Shell](/powershell/exchange/open-the-exchange-management-shell).

2. Hvis du vil fjerne en enkelt regel helt, flere regler eller alle regler fra en postkasse, skal du bruge cmdlet'en [Fjern IndbakkeRegel](/powershell/module/exchange/Remove-InboxRule) .

3. Hvis du vil bevare reglen og dens indhold til yderligere undersøgelse, skal du bruge cmdlet'en [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Trin til postkasser i Exchange Online

1. Følg trinnene i [Forbind for at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Hvis du vil fjerne en enkelt regel helt, flere regler eller alle regler fra en postkasse, skal du bruge cmdlet'en [Fjern indbakkeregel](/powershell/module/exchange/Remove-InboxRule) .

3. Hvis du vil bevare reglen og dens indhold til yderligere undersøgelse, skal du bruge cmdlet'en [Disable-InboxRule](/powershell/module/exchange/disable-inboxrule) .

## <a name="how-to-minimize-future-attacks"></a>Sådan minimerer du fremtidige angreb

### <a name="first-protect-your-accounts"></a>Først: Beskyt dine konti

Udnyttelser af regler og formularer bruges kun af en hacker, efter at de har stjålet eller brudt en af din brugers konti. Så dit første skridt til at forhindre brugen af disse udnyttelser mod din organisation er at beskytte dine brugerkonti aggressivt. Nogle af de mest almindelige måder, konti brydes på, er gennem phishing- eller [adgangskodesprøjteangreb](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

Den bedste måde at beskytte dine brugerkonti og især dine administratorkonti på er ved at [konfigurere multifaktorgodkendelse for brugere](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Du skal også:

- Overvåg, hvordan dine brugerkonti [tilgås og bruges](/azure/active-directory/active-directory-view-access-usage-reports). Du kan ikke forhindre det indledende brud, men du vil forkorte varigheden og virkningen af sikkerhedsbrud ved at opdage det hurtigere. Du kan bruge disse [Office 365 Cloud App Security politikker](/cloud-app-security/what-is-cloud-app-security) til at overvåge konti og beskeder om usædvanlig aktivitet:

  - **Flere mislykkede logonforsøg**: Denne politik profilerer dit miljø og udløser beskeder, når brugerne udfører flere mislykkede logonaktiviteter i en enkelt session med hensyn til den lærte baseline, hvilket kan indikere et forsøg på brud.

  - **Umulig rejse**: Denne politik profilerer dit miljø og udløser beskeder, når aktiviteter registreres fra den samme bruger på forskellige placeringer inden for en tidsperiode, der er kortere end den forventede rejsetid mellem de to placeringer. Dette kan indikere, at en anden bruger bruger de samme legitimationsoplysninger. Registrering af denne unormale adfærd nødvendiggør en indledende læringsperiode på syv dage, hvor den lærer en ny brugers aktivitetsmønster.

  - **Usædvanlig repræsenteret aktivitet (efter bruger)**: Denne politik profilerer dit miljø og udløser beskeder, når brugerne udfører flere repræsenterede aktiviteter i en enkelt session med hensyn til den lærte baseline, hvilket kan indikere et forsøg på brud.

- Brug et værktøj som [Office 365 Secure Score](/microsoft-365/security/defender/microsoft-secure-score) til at administrere sikkerhedskonfigurationer og -funktionsmåder for konti.

### <a name="second-keep-your-outlook-clients-current"></a>For det andet: Hold dine Outlook klienter opdaterede

Fuldt opdaterede og reparerede versioner af Outlook 2013 og 2016 deaktiverer som standard handlingen "Start program". Dette sikrer, at reglen og formularhandlingerne blokeres, selvom en hacker overtræder kontoen. Du kan installere de nyeste opdateringer og sikkerhedsrettelser ved at følge trinnene i [Installér Office opdateringer](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5).

Her er programrettelsesversionerne til dine Outlook 2013- og 2016-klienter:

- **Outlook 2016**: 16.0.4534.1001 eller nyere.

- **Outlook 2013**: 15.0.4937.1000 eller nyere.

Du kan få flere oplysninger om de enkelte sikkerhedsrettelser under:

- [sikkerhedsrettelse til Outlook 2016](https://support.microsoft.com/help/3191883)

- [sikkerhedsrettelse Outlook 2013](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Tredje: Overvåg dine Outlook klienter

Bemærk, at selvom programrettelser og opdateringer er installeret, er det muligt for en hacker at ændre konfigurationen af den lokale computer for at aktivere funktionsmåden "Start program" igen. Du kan bruge [Administration af avancerede Gruppepolitik](/microsoft-desktop-optimization-pack/agpm/) til at overvåge og gennemtvinge lokale computerpolitikker på dine klienter.

Du kan se, om "Start program" er blevet genaktiveret via en tilsidesættelse i registreringsdatabasen ved hjælp af oplysningerne i [Sådan får du vist systemregistreringsdatabasen ved hjælp af 64-bit versioner af Windows](https://support.microsoft.com/help/305097). Kontrollér disse undernøgler:

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

Se efter nøglen EnableUnsafeClientMailRules. Hvis den er der og er indstillet til 1, er sikkerhedsrettelsen Outlook blevet tilsidesat, og computeren er sårbar over for formular-/regelangrebet. Hvis værdien er 0, er handlingen "Start program" deaktiveret. Hvis den opdaterede og reparerede version af Outlook er installeret, og denne registreringsdatabasenøgle ikke findes, er et system ikke sårbart over for disse angreb.

Kunder med Exchange installationer i det lokale miljø bør overveje at blokere ældre versioner af Outlook, der ikke har programrettelser tilgængelige. Du kan finde oplysninger om denne proces i artiklen [Konfigurer Outlook klientblokering](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Sikker Microsoft 365 som en cybersikkerhedspro

Dit Microsoft 365-abonnement leveres med et sæt effektive sikkerhedsfunktioner, som du kan bruge til at beskytte dine data og dine brugere. Brug [køreplanen for Microsoft 365 sikkerhed – topprioriteter for de første 30 dage, 90 dage og mere til](security-roadmap.md) at implementere Microsofts anbefalede bedste praksis for sikring af din Microsoft 365 lejer.

- Opgaver, der skal udføres i de første 30 dage. Disse har øjeblikkelig virkning og har lav indvirkning på dine brugere.

- Opgaver, der skal udføres på 90 dage. Disse tager lidt mere tid at planlægge og implementere, men i høj grad forbedre din sikkerhedsholdning.

- Mere end 90 dage. Disse forbedringer bygges i dit første 90 dages arbejde.

## <a name="see-also"></a>Se også:

- [Ondsindede Outlook regler](https://silentbreaksecurity.com/malicious-outlook-rules/) fra SilentBreak Security Post om Regelvektor giver en detaljeret gennemgang af, hvordan Outlook regler.

- [MAPI over HTTP og Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/) på Sensepost-bloggen om Mailrule Pwnage diskuterer et værktøj kaldet Lineal, der giver dig mulighed for at udnytte postkasser via Outlook regler.

- [Outlook formularer og shells](https://sensepost.com/blog/2017/outlook-forms-and-shells/) på Sensepost-bloggen om Forms Threat Vector.

- [Kodebase for lineal](https://github.com/sensepost/ruler)

- [Linealindikatorer for kompromitteret](https://github.com/sensepost/notruler/blob/master/iocs.md)
