---
title: Insider-politikker for risikostyring
description: Få mere at vide om politikker for insider-risikostyring i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 86208efec649ad7fecc70ec1570a6e97ce28938c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587551"
---
# <a name="insider-risk-management-policies"></a>Insider-politikker for risikostyring

Insider-politikker for risikostyring afgør, hvilke brugere der er omfattet, og hvilke typer risikoindikatorer der konfigureres for beskeder. Du kan hurtigt oprette en politik, der gælder for alle brugere i organisationen, eller definere individuelle brugere eller grupper til administration i en politik. Politikker understøtter indholdsprioriteter for at fokusere på politikbetingelser for flere eller Microsoft Teams, SharePoint, datafølsomhedstyper og dataetiketter. Ved hjælp af skabeloner kan du vælge bestemte risikoindikatorer og tilpasse begivenhedstærskelværdier for politikindikatorer, tilpasse risikoresultater og niveau og hyppighed af beskeder. Desuden hjælper registreringer af risikoscore og unormalt brugeraktivitet med at identificere brugeraktivitet, der er af højere betydning eller mere usædvanlig. Politikvinduer giver dig mulighed for at definere den tidsramme, som politikken skal anvendes på for at advare aktiviteter, og de bruges til at bestemme varigheden af politikken, når den er aktiveret.

Se videoen Konfiguration [af politikker for insider-risikostyring](https://www.youtube.com/watch?v=kudK5ajZTUo) for at få et overblik over, hvordan politikker, der er oprettet med indbyggede politikskabeloner, kan hjælpe dig med hurtigt at reagere på potentielle risici.

## <a name="policy-dashboard"></a>Politikdashboard

Med **dashboardet** Politik kan du hurtigt se politikkerne i organisationen, politikkens tilstand, manuelt føje brugere til politikker og få vist status for beskeder, der er knyttet til hver politik.

- **Politiknavn**: Det navn, der er tildelt politikken i guiden Politik.
- **Status**: Tilstandsstatus for hver politik. Viser antallet af politikadvarsler og anbefalinger eller *statussen Sund* i forbindelse med politikker uden problemer.  Du kan vælge politikken for at få vist oplysninger om tilstandsstatus for eventuelle advarsler eller anbefalinger.
- **Aktive beskeder**: Antallet af aktive beskeder for hver politik.
- **Bekræftede beskeder**: Det samlede antal beskeder, der er resultatet af politikken i løbet af de seneste 365 dage.
- **Handlinger, der er foretaget på** påmindelser: Det samlede antal beskeder, der er blevet bekræftet eller afvist de seneste 365 dage.
- **Effektiviteten af politikbeskeder**: Den procentdel, der bestemmes af det samlede antal bekræftede beskeder, divideret med de samlede handlinger, der er foretaget på påmindelser (som er summen af vigtige beskeder, der er blevet bekræftet eller afvist i løbet af det seneste år).

![Insider dashboard for risikostyringspolitik.](../media/insider-risk-policy-dashboard.png)

## <a name="policy-recommendations-from-analytics"></a>Politikanbefalinger fra analyse

Insider-risikoanalyse gør det muligt at gennemføre en evaluering af potentielle insider-risici i organisationen uden at konfigurere insider-risikopolitikker. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisici og hjælpe med at bestemme typen og omfanget af de insider-risikostyringspolitikker, du kan overveje at konfigurere.

Du kan få mere at vide om Insider Risk Analytics og politikanbefalinger [under Indstillinger for Insider-risikostyring: Analyse](insider-risk-management-settings.md#analytics).

## <a name="policy-templates"></a>Politikskabeloner

Insider-skabeloner til risikostyring er foruddefinerede politikbetingelser, der definerer de typer risikoindikatorer og risikoscoremodel, der bruges af politikken. Der skal være tildelt en skabelon i guiden til oprettelse af politik, før politikken oprettes. Insider-risikostyring understøtter op til fem politikker for hver politikskabelon. Når du opretter en ny insider-risikopolitik med guiden Politik, kan du vælge mellem en af følgende politikskabeloner:

### <a name="data-theft-by-departing-users"></a>Datatyveri ved at brugere, der forlader brugere

Når brugere forlader organisationen, er der specifikke risikoindikatorer, der typisk er knyttet til datatyveri ved at brugere, der forlader organisationen. Denne politikskabelon bruger exfiltrationsindikatorer til risikoscore og fokuserer på registrering og beskeder i dette risikoområde. Datatyveri for brugere, der forlader tjenesten, kan omfatte at downloade filer fra SharePoint Online, udskrive filer og kopiere data til personlige beskeder i skyen og lagertjenester i nærheden af ansættelses- og slutdatoer. Ved at bruge enten Microsoft 365 HR-forbindelsen eller indstillingen til automatisk at overvåge sletning af brugerkonti i Azure Active Directory for din organisation starter denne skabelon point for risikoindikatorer, der er knyttet til disse aktiviteter, og hvordan de korrelerer med brugeraktivitetsstatus.

> [!IMPORTANT]
> Når du bruger denne skabelon, kan du konfigurere en Microsoft 365 HR-forbindelse til med jævne mellemrum at importere oplysninger om datoerne for dit arbejde og opsigelse for brugere i organisationen. Se artiklen [Importér data med HR-forbindelsen](import-hr-data.md) for at få en trinvis vejledning til konfiguration af Microsoft 365 HR-forbindelsen for organisationen. Hvis du vælger ikke at bruge HR-forbindelsen, skal du vælge den brugerkonto, der er slettet fra Azure AD, når du konfigurerer udløserhændelser i guiden politik.

### <a name="general-data-leaks"></a>Generelle datalækager

Beskyttelse af data og forhindring af datalækager er en konstant udfordring for de fleste organisationer, især med den hurtige vækst i de nye data, der skabes af brugere, enheder og tjenester. Brugerne har mulighed for at oprette, gemme og dele oplysninger på tværs af tjenester og enheder, som gør det sværere og mere komplekst at administrere datalækager. Datalækager kan omfatte utilsigtet overdeling af oplysninger uden for organisationen eller datatyveri med ondsindede hensigter. Med en tildelt DLP-politik (Forebyggelse af datatab), indbyggede eller brugerdefinerbare udløserhændelser starter denne skabelon registreringer i realtid af mistænkelige SharePoint Online-dataoverførsler, fil- og mappedeling, udskrivning af filer og kopiering af data til personlige beskeder i skyen samt lagertjenester.

Når du bruger *en skabelon til datalækager* , kan du tildele en DLP-politik til at udløse indikatorer i Insider-risikopolitikken for vigtige beskeder om høj alvorsgrad i organisationen. Når en alarm med høj alvorsgrad genereres af en regel for DLP-politik føjes til Office 365-overvågningsloggen, undersøger Insider-risikopolitikker, der oprettes med denne skabelon, automatisk DLP-beskeden med høj alvorsgrad. Hvis beskeden indeholder en omfangsbaseret bruger defineret i Insider Risk-politikken, behandles beskeden af Insider Risk-politikken som en ny besked og tildeles en insider-risikos alvorligheds- og risikoscore. Du kan også vælge at tildele valgte indikatorer som udløserhændelser for en politik. Denne fleksibilitet og tilpasning hjælper med at begrænse politikken til kun at omfatte de aktiviteter, der er omfattet af indikatorerne. Denne politik giver dig mulighed for at evaluere denne besked i kontekst med andre aktiviteter, der er inkluderet i sagen.

#### <a name="data-leaks-policy-guidelines"></a>Retningslinjer for politik om datalækager

Når du opretter eller ændrer DLP-politikker til brug med Insider-politikker for risikostyring, skal du overveje følgende retningslinjer:

- Prioriter dataudfyldningshændelser, og vær selektiv, når du  tildeler indstillinger for  hændelsesrapporter til Høj, når du konfigurerer regler i dine DLP-politikker. Eksempelvis bør mailing af følsomme dokumenter til en kendt konkurrent være en eksfiltreringshændelse på højt advarselsniveau. Hvis du overdeler  niveauet på højt niveau  i indstillingerne for hændelsesrapporter i andre DLP-politikregler, kan det øge støjen i arbejdsprocessen for insider-risikostyringsadvarsler og gøre det sværere for dine databehandlere og analytikere at evaluere disse beskeder korrekt. Tildeling af høje beskedniveauer  for at få adgang til denial-aktiviteter i DLP-politikker gør det f.eks. mere udfordrende at evaluere virkelig risikabel brugeradfærd og -aktiviteter.
- Når du bruger en DLP-politik som udløserhændelse, skal du sikre dig, at du forstår og korrekt konfigurerer de in-scope brugere i både DLP- og insider-risikostyringspolitikkerne. Kun brugere, der er defineret som omfattet af politikker for insider-risikostyring  ved hjælp af skabelonen datalækager, vil få behandlet vigtige DLP-politikbeskeder med høj alvorsgrad. Desuden er det kun brugere, der er defineret som omfattet af en regel for DLP-besked med høj alvorlighed, der vil blive behandlet af Insider-politikken for risikostyring til overvejelse. Det er vigtigt, at du ikke ukendt konfigurerer in-scope-brugere både i din DLP- og Insider-risikopolitik på en uoverens ment måde.

     Hvis dine DLP-politikregler f.eks. er fastsat til kun brugere på salgsteamet, og den insider-risikopolitik, der skabes af skabelonen datalækager, har defineret alle brugere som in-omfang, vil Insider-risikopolitikken kun behandle DLP-beskeder med høj alvorsgrad for brugerne på salgsteamet. Insider-risikopolitikken modtager ingen DLP-beskeder med høj prioritet, som brugerne skal behandle, som ikke er defineret i DLP-reglerne i dette eksempel. Omvendt, hvis din politik for insider-risikohåndtering,  der er oprettet ud fra datalækageskabeloner, er begrænset til kun brugere i salgsteamet, og den tildelte DLP-politik er begrænset til alle brugere, vil Insider-risikopolitikken kun behandle DLP-beskeder med høj alvorsgrad for medlemmer af salgsteamet. Insider-politikken for risikostyring ignorerer DLP-beskeder med høj alvorlighed for alle brugere, der ikke er på salgsteamet.

- Sørg *for,* **at indstillingen for hændelsesrapporter** i DLP-politikken, der bruges til denne insider-skabelon til risikostyring, er konfigureret til beskeder på højt alvorsniveau. Niveauet *Høj* alvorsgrad er de udløsende hændelser, og insider-risikostyringsbeskeder genereres ikke fra regler i DLP-politikker med feltet  Hændelsesrapporter indstillet til *Lav* eller *Mellem*.

    ![Indstilling for DLP-politikbesked.](../media/insider-risk-DLP-policy-high-severity.png)

     > [!NOTE]
     > Når du opretter en ny DLP-politik ved hjælp af de indbyggede skabeloner, skal du vælge indstillingen Opret eller tilpas avancerede **DLP-regler** for at konfigurere  indstillingen hændelsesrapporter for niveauet  Høj alvor.

Hver insider-politik for risikostyring, der oprettes ud fra skabelonen datalækager, kan kun have én DLP-politik tildelt, når du bruger denne udløsende **hændelsesindstilling** . Overvej at oprette en dedikeret DLP-politik, der kombinerer de forskellige aktiviteter, du vil registrere og fungere som udløsende hændelser for insider-risikopolitikker, der bruger skabelonen **Datalækager** .

Se artiklen [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md) for at få en trinvis vejledning til at konfigurere DLP-politikker for organisationen.

### <a name="data-leaks-by-priority-users-preview"></a>Datalækager efter prioritetsbrugere (forhåndsvisning)

Beskyttelse af data og forhindring af datalækager for brugere i organisationen kan afhænge af deres placering, adgangsniveau til følsomme oplysninger eller risikohistorik. Datalækager kan omfatte utilsigtet overdeling af meget følsomme oplysninger uden for organisationen eller datatyveri med ondsindede hensigter. Med en tildelt DLP-politik (Forebyggelse af datatab) som en udløsende hændelsesindstilling starter denne skabelon med at pointere registreringer af mistænkelig aktivitet i realtid og medfører en øget sandsynlighed for insider-risikobeskeder og -beskeder med højere alvorsgrad. Prioritetsbrugere defineres [i prioritetsbrugergrupper](insider-risk-management-settings.md#priority-user-groups-preview) , der er konfigureret på området for insider-risikostyring.

Som med **skabelonen Generelle datalækager** kan du vælge en DLP-politik til at udløse indikatorer i Insider-risikopolitikken for vigtige beskeder om høj alvorsgrad i organisationen. Følg politikretningslinjerne for datalækager for DLP-politikker, når du opretter en politik med DLP-indstillingen, når du bruger denne skabelon. Du kan også vælge at tildele valgte indikatorer som udløserhændelser for en politik. Denne fleksibilitet og tilpasning hjælper med at begrænse politikken til de aktiviteter, der er omfattet af indikatorerne. Desuden skal du tildele prioritetsbrugergrupper, der er oprettet i **Insider** >  **Indstillinger** >  **Prioritet-brugergrupper**, til politikken.

### <a name="data-leaks-by-disgruntled-users-preview"></a>Datalækager fra fordærv brugere (forhåndsvisning)

Når brugerne oplever stress ved ansættelse, kan de blive forskellige, hvilket kan øge risikoen for insider-risikoaktivitet. Denne skabelon starter pointbrugeraktivitet, når der identificeres en indikator, der er knyttet til forskellige forhold. Eksempler kan være meddelelser om forbedring af ydeevnen, dårlig evaluering af ydeevnen eller ændringer af jobniveau. Datalækager for ikke-belastede brugere kan omfatte at downloade filer fra SharePoint Online og kopiere data til personlige beskeder i skyen og lagertjenester nær ansættelses-stressor-hændelser.

Når du bruger denne skabelon, skal du også konfigurere en Microsoft 365 HR-forbindelse til jævnligt at importere meddelelser om forbedring af ydeevnen, status for dårlig ydeevne eller ændringsoplysninger på jobniveau for brugere i organisationen. Se artiklen [Importér data med HR-forbindelsen](import-hr-data.md) for at få en trinvis vejledning til konfiguration af Microsoft 365 HR-forbindelsen for organisationen.

### <a name="general-security-policy-violations-preview"></a>Generelle overtrædelser af sikkerhedspolitik (forhåndsvisning)

I mange organisationer har brugerne tilladelse til at installere software på deres enheder eller til at ændre enhedsindstillinger, så de kan udføre deres opgaver. Ved et tilfælde eller med ondsindede hensigter kan brugerne installere malware eller deaktivere vigtige sikkerhedsfunktioner, som hjælper med at beskytte oplysninger på deres enhed eller på dine netværksressourcer. Denne politikskabelon bruger sikkerhedsadvarsler fra Microsoft Defender for Endpoint til at begynde at pointere disse aktiviteter og fokusere på registrering og påmindelser om dette risikoområde. Brug denne skabelon til at give indsigt i brud på sikkerhedspolitiken i scenarier, hvor brugere kan have en historik over overtrædelser af sikkerhedspolitik, der kan være en indikator for insider-risici.

Du skal have Microsoft Defender til Slutpunkt konfigureret i din organisation og aktivere Defender for Endpoint for integration af Insider Risk Management i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde flere oplysninger om konfiguration af Defender til Endpoint for integration af insider-risikostyring i [Konfigurer avancerede funktioner i Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="general-patient-data-misuse-preview"></a>Generel forkert brug af patientdata (forhåndsvisning)

Beskyttelse af sundhedsjournaler og forhindring af misbrug af patientoplysninger er et vigtigt problem for organisationer i sundhedssektoren. Dette misbrug kan omfatte fortrolige datalækager til uautoriserede personer, svigagtig ændring af patientjournaler eller tyveri af patientjournaler. At forhindre misbrug af patientdata, enten ved manglende opmærksomhed, forsømmelighed eller svindel fra brugerne, er også et vigtigt led i at opfylde de lovmæssige krav i HIPAA (Health Insurance Portability and Accountability Act) og HEALTH Information Technology for Economic and Clinical Health (HITECH) Act. Begge disse handlinger fastlægger kravene til relevante patientbeskyttede sundhedsoplysninger (PHI).

Denne politikskabelon aktiverer risikoscore for interne brugere, der registrerer mistænkelige aktiviteter, der er knyttet til poster, der hostes på eksisterende elektroniske medicinske registreringssystemer (EMR). Registrering fokuserer på uautoriseret adgang, visning, ændring og eksport af patientdata. Du skal konfigurere en forbindelse (Forbindelseskomponent til [Microsoft Healthcare](import-healthcare-data.md) eller Episk forbindelse for at understøtte registrering af adgang, udfyldning eller sløringsaktiviteter i dit EMR-system.[](import-epic-data.md)

Når du bruger denne skabelon, skal du også konfigurere en Microsoft 365 HR-forbindelse til jævnligt at importere organisationsprofildata for brugere i organisationen. Se artiklen Importér data med HR-forbindelsen for at få en trinvis vejledning til at konfigurere Microsoft 365 HR-forbindelsen for din organisation.

### <a name="security-policy-violations-by-departing-users-preview"></a>Brud på sikkerhedspolitik ved brugere, der forlader brugere (forhåndsvisning)

Brugere, der forlader sig, uanset om de forlader positive eller negative termer, kan være større risiko for brud på sikkerhedspolitik. For at beskytte dig mod utilsigtede eller skadelige sikkerhedsbrud, når brugere forlader virksomheden, bruger denne politikskabelon Defender for Endpoint-beskeder til at give indsigt i sikkerhedsrelaterede aktiviteter. Disse aktiviteter omfatter installation af malware eller andre potentielt skadelige programmer og deaktivering af sikkerhedsfunktioner på brugerens enheder. Ved at bruge enten [Microsoft 365 HR-forbindelsen](import-hr-data.md) eller indstillingen til automatisk at overvåge sletning af brugerkonti i Azure Active Directory for din organisation starter denne skabelon point for risikoindikatorer, der vedrører disse sikkerhedsaktiviteter, og hvordan de korrelerer med brugertiltrædelsesstatus.

Du skal have Microsoft Defender til Slutpunkt konfigureret i din organisation og aktivere Defender for Endpoint for integration af Insider Risk Management i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde flere oplysninger om konfiguration af Defender til Endpoint for integration af insider-risikostyring i [Konfigurer avancerede funktioner i Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="security-policy-violations-by-priority-users-preview"></a>Overtrædelse af sikkerhedspolitik for prioritetsbrugere (forhåndsvisning)

Beskyttelse mod sikkerhedsbrud for brugere i organisationen kan afhænge af deres placering, adgangsniveau til følsomme oplysninger eller risikohistorik. Da sikkerhedsbrud efter prioritet-brugere kan have en betydelig indvirkning på organisationens kritiske områder, begynder denne politikskabelon at score på disse indikatorer og bruger Microsoft Defender til slutpunktsbeskeder til at give indsigt i sikkerhedsrelaterede aktiviteter for disse brugere. Disse aktiviteter kan omfatte prioritetsbrugere, der installerer malware eller andre potentielt skadelige programmer og deaktiverer sikkerhedsfunktioner på deres enheder. Prioritetsbrugere defineres i prioritetsbrugergrupper, der er konfigureret på området for insider-risikostyring.

Du skal have Microsoft Defender til Slutpunkt konfigureret i din organisation og aktivere Defender for Endpoint for integration af Insider Risk Management i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde flere oplysninger om konfiguration af Defender til Endpoint for integration af insider-risikostyring i [Konfigurer avancerede funktioner i Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center). Desuden skal du tildele prioritetsbrugergrupper, der er oprettet i **Insider** >  **Indstillinger** >  **Prioritet-brugergrupper**, til politikken.

### <a name="security-policy-violations-by-disgruntled-users-preview"></a>Brud på sikkerhedspolitik for brugere, der ikke er ens (forhåndsvisning)

Brugere, der oplever stressende ved ansættelse, kan have en højere risiko for utilsigtede eller skadelige sikkerhedspolitikbrud. Disse stressfaktorer kan omfatte, at brugeren bliver sat ind i en plan for forbedring af ydeevnen, at han eller hun bliver degraderet fra sin nuværende position. Denne politikskabelon starter risikoscore baseret på disse indikatorer og aktiviteter, der er knyttet til disse hændelser for disse brugere.

Når du bruger denne skabelon, skal du også konfigurere en Microsoft 365 HR-forbindelse til jævnligt at importere meddelelser om forbedring af ydeevnen, status for dårlig ydeevne eller ændringsoplysninger på jobniveau for brugere i organisationen. Se artiklen [Importér data med HR-forbindelsen](import-hr-data.md) for at få en trinvis vejledning til konfiguration af Microsoft 365 HR-forbindelsen for organisationen.

Du skal også have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af Insider Risk Management i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde flere oplysninger om konfiguration af Defender til Endpoint for integration af insider-risikostyring i [Konfigurer avancerede funktioner i Defender til Slutpunkt](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="policy-template-prerequisites-and-triggering-events"></a>Forudsætninger for politikskabeloner og udløser hændelser

Afhængigt af den skabelon, du vælger til en politik for insider-risikostyring, varierer de udløsende hændelser og politikforudsigt. Udløserhændelser er forudsætninger, der afgør, om en bruger er aktiv i forbindelse med en insider-politik for risikostyring. Hvis en bruger føjes til en insider-politik for risikostyring, men ikke har en udløsende hændelse, evalueres brugeraktiviteten ikke af politikken, medmindre de tilføjes manuelt i dashboardet Brugere. Politikforud forudsætninger er påkrævede elementer, så politikken modtager de signaler eller aktiviteter, der er nødvendige for at evaluere risikoen.

I følgende tabel vises de udløsende hændelser og forudsætninger for politikker, der er oprettet ud fra hver insider-skabelon til risikostyringspolitik:

| **Politikskabelon** | **Udløse begivenheder for politikker** | **Forudsætninger** |
| :------------------ | :--------------------------------- | :---------------- |
| **Datatyveri ved at brugere, der forlader brugere** | Indikator for opsigelse eller sletning fra HR-forbindelse eller Azure Active Directory kontosletning | (valgfrit) Microsoft 365 HR-forbindelse konfigureret til indikatorer for afslutning og udløbsdato |
| **Generelle datalækager** | Politikaktivitet for datalækage, der *opretter en* alarm med høj alvorlighed eller indbyggede udfyldningshændelsesudløsere | DLP-politik konfigureret til *beskeder om høj* alvorsgrad <br><br> ELLER <br><br> Tilpassede udløserindikatorer |
| **Datalækager efter prioritetsbrugere** | Politikaktivitet for datalækage, der *opretter en* alarm med høj alvorlighed eller indbyggede udfyldningshændelsesudløsere | DLP-politik konfigureret til *beskeder om høj* alvorsgrad <br><br> ELLER <br><br> Tilpassede udløserindikatorer <br><br> Prioritetsbrugergrupper konfigureret i indstillinger for insider-risiko |
| **Datalækager fra forskellige brugere** | Forbedring af ydeevnen, dårlig ydeevne eller indikatorer på jobniveau ændres fra HR-forbindelsen | Microsoft 365 HR-forbindelse konfigureret til forskellige indikatorer |
| **Generelle overtrædelser af sikkerhedspolitik** | Forsvar af sikkerhedskontroller eller uønsket software, der er registreret af Microsoft Defender for Endpoint | Aktivt abonnement på Microsoft Defender til Slutpunkt <br><br> Integration af Microsoft Defender til Slutpunkt med Microsoft 365 Overholdelsescenter konfigureret |
| **Generel forkert brug af patientdata** | Forsvar af sikkerhedskontroller fra EMR-systemer <br><br> Indikatorer, der matcher bruger- og patientadresser, fra HR-systemer | Indikatorer for adgang til sundhedssektoren valgt i politik eller indstillinger for insider-risiko <br><br> Microsoft 365 HR-forbindelse konfigureret til adressesammenholdelse <br><br> Microsoft Healthcare eller episk forbindelse konfigureret |
| **Brud på sikkerhedspolitik ved brugere, der forlader os** | Indikatorer for opsigelse eller opsigelsesdato fra HR-forbindelse eller Azure Active Directory kontosletning | (valgfrit) Microsoft 365 HR-forbindelse konfigureret til indikatorer for afslutning og udløbsdato <br><br> Aktivt abonnement på Microsoft Defender til Slutpunkt <br><br> Integration af Microsoft Defender til Slutpunkt med Microsoft 365 Overholdelsescenter konfigureret |
| **Prioritetsbrugeres brud på sikkerhedspolitik** | Forsvar af sikkerhedskontroller eller uønsket software, der er registreret af Microsoft Defender for Endpoint | Aktivt abonnement på Microsoft Defender til Slutpunkt <br><br> Integration af Microsoft Defender til Slutpunkt med Microsoft 365 Overholdelsescenter konfigureret <br><br> Prioritetsbrugergrupper konfigureret i indstillinger for insider-risiko |
| **Overtrædelse af sikkerhedspolitik for en bruger, der ikke er en gruppe af brugere** | Forbedring af ydeevnen, dårlig ydeevne eller indikatorer på jobniveau ændres fra HR-forbindelsen | Microsoft 365 HR-forbindelse konfigureret til forskellige indikatorer <br><br> Aktivt abonnement på Microsoft Defender til Slutpunkt <br><br> Integration af Microsoft Defender til Slutpunkt med Microsoft 365 Overholdelsescenter konfigureret |

## <a name="prioritize-content-in-policies"></a>Prioriter indhold i politikker

Insider-politikker for risikostyring understøtter angivelse af en højere prioritet for indhold, afhængigt af hvor det er gemt, eller hvordan det klassificeres. Hvis du angiver indhold som en prioritet, øges risikoresultatet for alle tilknyttede aktiviteter, hvilket igen øger risikoen for at generere en vigtig besked. Nogle aktiviteter genererer dog slet ikke en besked, medmindre det relaterede indhold indeholder indbyggede eller brugerdefinerede typer af følsomme oplysninger eller er angivet som en prioritet i politikken.

Din organisation har f.eks. en dedikeret SharePoint til et meget fortroligt projekt. Datalækager for oplysninger på dette SharePoint-websted kan bringe projektet i fare og vil have en betydelig indvirkning på projektets succes. Ved at prioritere dette SharePoint i en datalækagepolitik øges risikoresultater for kvalificerende aktiviteter automatisk. Denne prioritering øger sandsynligheden for, at disse aktiviteter genererer en insider-risikobesked og øger alvorsniveauet for beskeden.

Når du opretter en insider-politik for risikostyring i guiden politik, kan du vælge mellem følgende prioriteter:

- **SharePoint-websteder**: Alle aktiviteter, der er knyttet til alle filtyper i definerede SharePoint, tildeles en højere risiko. Brugere, der konfigurerer politikken og vælger prioritet af Share Point-websteder, kan SharePoint websteder, de har tilladelse til at få adgang til. Hvis SharePoint websteder ikke kan vælges i politikken af den aktuelle bruger, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de nødvendige websteder.
- **Typer af følsomme oplysninger**: Alle aktiviteter, der er knyttet til [indhold, der indeholder følsomme oplysningstyper](sensitive-information-type-entity-definitions.md) , tildeles en højere risikoscore.
- **Følsomhedsmærkater**: Alle aktiviteter, der er knyttet til indhold med [bestemte følsomhedsmærkater](sensitivity-labels.md) , tildeles en højere risikoscore.

## <a name="sequence-detection-preview"></a>Sekvensregistrering (eksempel)

Risikabele aktiviteter kan ikke forekomme som isolerede hændelser. Disse risici er ofte en del af en større række hændelser. En sekvens er en gruppe af to eller flere brugeraktiviteter, der udføres én efter en, og som kan foreslå en høj risiko. At identificere disse relaterede aktiviteter er en vigtig del af evalueringen af den overordnede risiko. Når sekvensregistrering er aktiveret for politikker for datatyveri eller datalækager, vises indsigt fra sekvensoplysninger på  fanen Brugeraktivitet i en Insider-risikostyringssag. Følgende politikskabeloner understøtter registrering af sekvenser:

- Datatyveri ved at brugere, der forlader brugere
- Generelle datalækager
- Datalækager efter prioritetsbrugere
- Datalækager fra forskellige brugere

Disse insider-politikker for risikostyring kan anvende specifikke indikatorer og den rækkefølge, de opstår i, til at registrere hvert trin i en sekvens af risici. Filnavne bruges til tilknytning af aktiviteter på tværs af en sekvens. Disse risici er inddelt i fire hovedkategorier for aktivitet:

- **Samling**: Denne kategori signalerer, at brugere af politikkens omfang fokuserer på downloadaktiviteter. Nogle eksempler på aktiviteter i denne kategori ville være at hente filer SharePoint websteder eller flytte filer til en komprimeret mappe.
- **Udfyldning: Denne kategori** signalerer fokus på delings- eller udtræksaktiviteter til interne og eksterne kilder af brugere af politikker i omfang. Et eksempel på en aktivitet i denne kategori ville være at sende mails med vedhæftede filer fra din organisation til eksterne modtagere.
- **Obskønhed**: Denne kategori signalerer, at der fokuseres på maskering af risikabelt aktivitet af brugere af politikkens omfang. Nogle eksempler på aktiviteter i denne kategori ville være omdøbning af filer på en enhed eller fjernelse eller nedgradering af følsomhedsetiketter på SharePoint filer.
- **Oprydning: Denne kategori** signalerer fokus på sletningsaktiviteter af brugere af politikker inden for området. Et eksempel på en aktivitet i denne kategori ville være at slette filer fra en enhed.

> [!NOTE]
> Sekvensregistrering anvender indikatorer, der er aktiveret i de globale indstillinger for insider-risikostyring og indikatorer, der er valgt i en politik. Hvis relevante indikatorer ikke er markeret, fungerer sekvensregistrering ikke.

Du kan tilpasse individuelle tærskelindstillinger for hver sekvensregistreringstype, når de er konfigureret i politikken. Disse tærskelindstillinger justerer beskeder baseret på mængden af filer, der er knyttet til sekvensen.

Du kan få mere at vide om administration af sekvensregistrering **i** visningen Brugeraktivitet under [Insider-sager til risikostyring: Brugeraktivitet](insider-risk-management-cases.md#user-activity).

## <a name="cumulative-exfiltration-detection-preview"></a>Registrering af kumulativ udfyldning (forhåndsvisning)

Insider-risikoindikatorer hjælper med at identificere usædvanlige niveauer af risikoaktiviteter, når de evalueres dagligt for brugere, der er omfattet af insider-risikopolitikker. Samlet registrering af udfyldning bruger maskinlæringsmodeller til at hjælpe dig med at identificere, hvornår udfyldningsaktiviteter, som en bruger udfører i løbet af en bestemt periode, overstiger den normale mængde, der er udført af brugerne i organisationen i de seneste 30 dage over flere eksfiltreringsaktivitetstyper. Hvis en bruger f.eks. har delt flere filer end de fleste brugere i løbet af den seneste måned, vil denne aktivitet blive registreret og klassificeret som en kumulativ udfyldningsaktivitet.

Insider-analytikere og risikoadministrationsanalytikere kan bruge indsigter i kumulativ udfyldningsregistrering til at identificere udfyldningsaktiviteter, der typisk ikke typisk genererer beskeder, men som er over det, der typisk gælder for deres organisation. Nogle eksempler kan være brugere, der forlader organisationen for langsomt at eksfiltrere data på tværs af en række dage, eller når brugere gentagne gange deler data på tværs af flere kanaler mere end normalt for datadeling for organisationen.  Højere risikoresultater tildeles akkumulerede udfyldningsaktiviteter for SharePoint-websteder, følsomme oplysningstyper og indhold med følsomhedsmærkater konfigureret som prioritetsindhold i en politik eller til aktivitet med etiketter konfigureret som høj prioritet i Microsoft Information Protection.[](/microsoft-365/compliance/sensitivity-labels#label-priority-order-matters)

Kumulativ registrering af udfyldning er aktiveret som standard, når du bruger følgende politikskabeloner:

- Datatyveri ved at brugere, der forlader brugere
- Generelle datalækager
- Datalækager efter prioritetsbrugere
- Datalækager fra forskellige brugere

> [!NOTE]
> Kumulativ registrering af udfyldning anvender udfyldningsindikatorer, der er aktiveret i de globale indstillinger for insider-risikostyring og udfyldningsindikatorer, der er valgt i en politik. Derfor evalueres den kumulative registrering af udfyldning kun for de relevante indikatorer for udfyldning. Akkumulerede udfyldningsaktiviteter for [følsomhedsmærkater](sensitivity-labels.md) konfigureret i prioriteret indhold genererer højere risikoresultater.

Når kumulativ registrering af udfyldning er aktiveret ved datatyveri eller datalækagespolitikker, vises indsigt fra kumulative udfyldningsaktiviteter på fanen Brugeraktivitet i en Insider-risikostyringssag.

Hvis du vil have mere at vide om administration af brugeraktivitet, skal [du se Insider-sager for risikostyring: Brugeraktiviteter](insider-risk-management-cases.md#user-activity).

## <a name="policy-health"></a>Politiks tilstand

Status for politikkens tilstand giver dig indsigt i potentielle problemer med dine Insider-politikker for risikostyring. Kolonnen Status under fanen Politikker kan give dig besked om politikker, der kan forhindre, at der rapporteres brugeraktivitet, eller hvorfor antallet af aktivitetsbeskeder er usædvanligt. Status for politikkens tilstand kan også bekræfte, at politikken er sund og kræver ikke opmærksomhed eller konfigurationsændringer.

Hvis der er problemer med en politik, viser politikkens tilstandsstatus advarsler om meddelelser og anbefalinger, så du kan gøre noget for at løse politikproblemer. Disse meddelelser kan hjælpe dig med at løse følgende problemer:

- Politikker med ufuldstændig konfiguration. Disse problemer kan omfatte manglende brugere eller grupper i konfigurationstrinnene til politikken eller andre ufuldstændige politikkonfigurationstrin.
- Politikker med problemer med konfiguration af indikator. Symboler er en vigtig del af hver politik. Hvis der ikke er konfigureret indikatorer, eller hvis der er valgt for få indikatorer, evaluerer politikken muligvis ikke risikabele aktiviteter som forventet.
- Politikudløser fungerer ikke, eller krav til politikudløser er ikke konfigureret korrekt. Politikfunktionaliteten kan afhænge af andre tjenester eller konfigurationskrav for effektivt at registrere udløsning af hændelser for at aktivere tildeling af risikoscore til brugere i politikken. Disse afhængigheder kan omfatte problemer med konfiguration af forbindelser, deling af Microsoft Defender for Endpoint-beskeder eller konfigurationsindstillinger for politik til forebyggelse af datatab.
- Volumengrænser nærmer sig eller grænser sig. Insider-politikker for risikostyring bruger mange Microsoft 365-tjenester og slutpunkter til at aggregere risikoaktivitetssignaler. Afhængigt af antallet af brugere i dine politikker kan mængdebegrænsninger forsinke identifikation og rapportering af risikoaktiviteter. Få mere at vide om disse begrænsninger i afsnittet Begrænsninger for politikskabeloner i denne artikel.

Hvis du hurtigt vil have vist en politiks tilstandsstatus, skal du gå til fanen Politik og kolonnen Status. Her får du vist følgende indstillinger for politiktilstand for hver politik:

- Sund: Der er ikke identificeret problemer med politikken.
- Anbefalinger: Der er nogle problemer med politikken, der kan forhindre politikken i at fungere som forventet.
- Advarsler: Der er problemer med politikken, der forhindrer den i at identificere risikabelt arbejde.

Hvis du vil have mere at vide om anbefalinger eller advarsler, skal du vælge en politik på **fanen Politik** for at åbne kortet med politikdetaljer. Du kan finde flere oplysninger om anbefalinger og advarsler, herunder vejledning til at løse disse problemer, i sektionen Meddelelser på detaljekortet.

![Insider-politik for risikostyring.](../media/insider-risk-policy-health.png)

### <a name="notification-messages"></a>Meddelelser

Brug tabellen nedenfor til at få mere at vide om anbefalinger og advarselsmeddelelser og handlinger, du kan udføre for at løse potentielle problemer.

|**Meddelelser**|**Politikskabeloner**|**Årsager / Prøv denne handling for at løse problemet**|
|:------------------------|:-------------------|:---------------------------|
| Politikken tildeler ikke risikoresultater til aktivitet | Alle politikskabeloner | Det kan være en ide at gennemgå politikkens omfang og udløse hændelseskonfiguration, så politikken kan tildele risikoresultater til aktivitet <br><br> 1. Gennemse de brugere, der er valgt til politikken. Hvis du kun har valgt få brugere, kan det være en ide at vælge flere brugere. <br> 2. Hvis du bruger en HR-forbindelse, skal du kontrollere, at din HR-forbindelse sender de korrekte data. <br> 3. Hvis du bruger en DLP-politik som din udløsende hændelse, skal du kontrollere din DLP-politikkonfiguration for at sikre, at den er konfigureret til at blive brugt i denne politik. <br> 4. For sikkerhedsfejlspolitikker skal du gennemse den triagestatus for beskeder om Microsoft Defender til Slutpunkt, der er valgt i insider-risikoindstillinger > intelligente registreringer. Bekræft, at beskedfilteret ikke er for smalt. |
| Politikken har ikke genereret beskeder | Alle politikskabeloner | Det kan være en ide at gennemgå politikkonfigurationen, så du analyserer pointprocenten for den aktivitet, der interesserer dig. <br><br> 1. Bekræft, at du har valgt de indikatorer, du vil score. Jo flere indikatorer der vælges, jo flere aktiviteter tildeles der risikoresultater. <br> 2. Gennemse tilpasning af grænseværdi for politik. Hvis de valgte grænseværdier ikke passer til organisationens risikotolerance, kan du justere valgene, så beskeder oprettes ud fra dine foretrukne grænseværdier. <br> 3. Gennemse de brugere og grupper, der er valgt til politikken. Bekræft, at du har valgt alle de relevante brugere og grupper. <br> 4. I forbindelse med sikkerhedsfejl skal du bekræfte, at du har valgt den beskedstatus, du vil have til at modtage Microsoft Defender for Endpoint-beskeder i intelligente registreringer i indstillinger.|
| Ingen brugere eller grupper er inkluderet i denne politik | Alle politikskabeloner | Brugere eller grupper tildeles ikke til politikken. <br><br> Rediger din politik, og vælg brugere eller grupper til politikken. |
| Der er ikke valgt nogen indikatorer for denne politik | Alle politikskabeloner | Symboler er ikke valgt for politikken <br><br> Rediger din politik, og vælg relevante politikindikatorer for politikken. |
| Denne politik indeholder ingen prioritetsbrugergrupper | - Datalækager efter prioritetsbrugere <br> - Prioritetsbrugeres brud på sikkerhedspolitik | Prioritetsbrugergrupper tildeles ikke til politikken. <br><br> Konfigurer prioritetsbrugergrupper i indstillingerne for Insider-risikostyring, og tildel prioritetsbrugergrupper til politikken. |
| Der er ikke valgt nogen udløserhændelse for denne politik | Alle politikskabeloner | Der er ikke konfigureret en udløserhændelse for politikken <br><br> Risikoresultater tildeles ikke til brugeraktiviteter, før du redigerer politikken og vælger en udløsende hændelse. |
| HR-forbindelse er ikke konfigureret eller fungerer som forventet | - Datatyveri ved at udgå af en bruger <br> - Sikkerhedspolitik bliver krænket af brugere, der forlader os <br> - Datalækager fra forskellige brugere <br> - Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens | Der er et problem med HR-forbindelsen. <br><br> 1. Hvis du bruger en HR-forbindelse, skal du kontrollere, at din HR-forbindelse sender korrekte data <br><br> ELLER <br><br> 2. Vælg den Azure AD-konto, der er blevet slettet og udløst en hændelse. |
| Ingen enheder er onboardet | - Datatyveri ved at udgå brugere <br> - Generelle datalækager <br> - Datalækager fra forskellige brugere <br> - Datalækager efter prioritetsbrugere | Enhedsindikatorer er markeret, men der er ikke nogen enheder onboardet til Microsoft 365 <br><br> Kontrollér, om enhederne er onboardet og opfylder kravene. |
| HR-forbindelse har ikke uploadet data for nylig | - Datatyveri ved at udgå af en bruger <br> - Sikkerhedspolitik bliver krænket af brugere, der forlader os <br> - Datalækager fra forskellige brugere <br> - Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens | HR-forbindelsen har ikke importeret data i mere end 7 dage. <br><br> Kontrollér, at din HR-forbindelse er konfigureret korrekt, og send data. |
| Vi kan ikke kontrollere status for din HR-forbindelse lige nu. Prøv igen senere | - Datatyveri ved at udgå af en bruger <br> - Sikkerhedspolitik bliver krænket af brugere, der forlader os <br> - Datalækager fra forskellige brugere <br> - Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens | Insider-løsningen til risikostyring kan ikke kontrollere status for din HR-forbindelse. <br><br> Kontrollér, at din HR-forbindelse er konfigureret korrekt, og afsende data, eller gå tilbage, og kontrollér politikstatus.  |
| DLP-politik vælges ikke som den udløsende hændelse | - Generelle datalækager <br> - Datalækager efter prioritetsbrugere | En DLP-politik er ikke blevet valgt som en udløserhændelse, eller den valgte DLP-politik er blevet slettet. <br><br> Rediger politikken, og vælg enten en aktiv DLP-politik eller 'Bruger udfører en udfyldningsaktivitet' som udløserhændelsen i politikkonfigurationen. |
| DLP-politik anvendt i denne politik er slået fra | - Generelle datalækager <br> - Datalækager efter prioritetsbrugere | DLP-politik, der bruges i denne politik, er slået fra. <br><br> 1. Slå den DLP-politik, der er tildelt denne politik, til. <br><br> ELLER <br><br> 2. Rediger denne politik, og vælg enten en ny DLP-politik eller "Brugeren udfører en udfyldningsaktivitet" som den udløsende hændelse i politikkonfigurationen. |
| DLP-politikken opfylder ikke kravene | - Generelle datalækager <br> - Datalækager efter prioritetsbrugere | DLP-politikker, der bruges som udløserhændelser, skal konfigureres til at generere beskeder med høj alvorsgrad. <br><br>  1. Rediger din DLP-politik for at tildele relevante beskeder *som Høj alvorsgrad*. <br><br> ELLER <br><br> 2. Rediger denne politik, *og vælg Bruger udfører en udfyldningsaktivitet* som udløserhændelsen. |
| Din organisation har ikke et abonnement på Microsoft Defender til slutpunkt | - Generel overtrædelse af sikkerhedspolitik <br> - Brud på sikkerhedspolitik ved brugere, der forlader os <br> - Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens <br> - Prioritetsbrugeres brud på sikkerhedspolitik | Der blev ikke fundet et aktivt Microsoft Defender for Endpoint-abonnement for din organisation. <br><br> Før et abonnement på Microsoft Defender til Slutpunkt er tilføjet, tildeler disse politikker ikke risikoresultater til brugeraktivitet. |
| Microsoft Defender for Endpoint-beskeder deles ikke med overholdelsescenteret | - Generel overtrædelse af sikkerhedspolitik <br> - Brud på sikkerhedspolitik ved brugere, der forlader os <br> - Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens <br> - Prioritetsbrugeres brud på sikkerhedspolitik | Microsoft Defender for Endpoint-beskeder deles ikke med Compliance Center. <br><br> Konfigurer deling af Microsoft Defender for Endpoint-beskeder. |
| Du nærmer dig den maksimale grænse for brugere, der scores aktivt for denne politikskabelon. | Alle politikskabeloner | Hver politikskabelon har et maksimalt antal in-scope-brugere. Se oplysninger om skabelongrænsesektionen. <br><br> Gennemse brugerne under fanen Brugere, og fjern alle brugere, der ikke længere skal have point. |
| Udløser hændelse gentagne gange for over 15 % af brugerne i denne politik. | Alle politikskabeloner | Juster den udløsende hændelse for at reducere, hvor ofte brugere kommer ind i politikkens omfang. |

## <a name="policy-template-limits"></a>Begrænsninger for politikskabeloner

Skabeloner til Insider-risikostyringspolitik bruger begrænsninger til at administrere mængden og hastigheden af behandling for in-omfang af brugerrisici, og hvordan denne proces er integreret med understøttelse af Microsoft 365-tjenester. Hver politikskabelon har et maksimalt antal brugere, der aktivt kan tildeles risikoresultater for politikken, som den kan understøtte og effektivt behandle og rapportere risikoaktiviteter. In-scope-brugere er brugere, der udløser hændelser for politikken.

Grænsen for hver politik beregnes på baggrund af det samlede antal unikke brugere, der modtager risikoresultater pr. politikskabelontype. Hvis antallet af brugere for en politikskabelontype er nær eller overstiger brugergrænsen, reduceres politikkens ydeevne. Hvis du vil have vist det aktuelle antal brugere for en politik, skal du gå til fanen Politik og kolonnen Brugere i omfang. Du kan have op til fem politikker for enhver politikskabelon. Disse maksimumgrænser gælder for brugere på tværs af alle politikker ved hjælp af en bestemt politikskabelon.

Brug følgende tabel til at bestemme det maksimale antal in-scope-brugere, der understøttes til hver politikskabelon:

|**Politikskabelon**|**Aktuel brugers maks. omfang**|
|:------------------|:--------------------------------|
| Generel datalækage | 15,000 |
| Datalækage af ikke-følsomme brugere | 7,500 |
| Datalækage efter prioritetsbrugere | 1,000 |
| Datatyveri ved at brugere, der forlader brugere | 20,000 |
| Generelle overtrædelser af sikkerhedspolitik | 1,000 |
| Generel forkert brug af patientdata | 5,000 |
| Overtrædelse af sikkerhedspolitik for prioritetsbrugere | 1,000 |
| Brud på sikkerhedspolitik ved brugere, der forlader os | 15,000 |
| Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens | 7,500 |

## <a name="create-a-new-policy"></a>Opret en ny politik

Hvis du vil oprette en ny insider-politik for risikostyring, skal du bruge guiden til politik i **Insider-løsningen** til risikostyring i Microsoft 365 Overholdelsescenter.

Udfør følgende trin for at oprette en ny politik:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring** og vælge **fanen** Politikker.
2. Vælg **Opret politik** for at åbne guiden politik.
3. På siden **Politikskabelon** skal du vælge en politikkategori og derefter vælge skabelonen til den nye politik. Disse skabeloner består af betingelser og indikatorer, der definerer de risikoaktiviteter, du vil registrere og undersøge. Gennemse skabelonens forudsætninger, udløsende hændelser og registrerede aktiviteter for at bekræfte, at denne politikskabelon passer til dine behov.

    > [!IMPORTANT]
    > Nogle politikskabeloner har forudsætninger, der skal konfigureres, for at politikken kan generere relevante beskeder. Hvis du ikke har konfigureret forudsætningerne for den gældende politik, skal du **se trin 4** ovenfor.

4. Vælg **Næste for** at fortsætte.
5. På siden **Navn og beskrivelse** skal du udfylde følgende felter:
    - **Navn (påkrævet)**: Angiv et brugervenligt navn til politikken. Dette navn kan ikke ændres, efter politikken er oprettet.
    - **Beskrivelse (valgfrit)**: Angiv en beskrivelse af politikken.

6. Vælg **Næste for** at fortsætte.
7. På siden **Brugere** og grupper skal du vælge  Inkluder alle brugere og  grupper eller Inkluder bestemte brugere og grupper for at definere, hvilke brugere eller grupper, der er inkluderet i politikken, eller hvis du har valgt en prioritetsbaseret skabelon for brugere. skal **du vælge Tilføj eller rediger prioritetsbrugergrupper**. Hvis du **vælger Medtag alle** brugere og grupper, leder du efter udløserhændelser for alle brugere og grupper i organisationen for at begynde at tildele risikopoint for politikken. Hvis du **vælger Medtag bestemte brugere og grupper,** kan du angive, hvilke brugere og grupper der skal tildeles politikken. Gæstebrugerkonti understøttes ikke.
8. Vælg **Næste for** at fortsætte.
9. På siden **Indhold, der** skal prioritere kan du tildele (hvis det er nødvendigt) de kilder, der skal prioriteres, hvilket øger risikoen for at generere en besked om høj alvorsgrad for disse kilder. Vælg en af følgende valgmuligheder:

    - **Jeg vil angive SharePoint, følsomhedsmærkater og/eller følsomme oplysningstyper som prioritetsindhold**. Hvis du vælger denne indstilling, aktiveres detaljesider i guiden til konfiguration af disse kanaler.
    - **Jeg vil ikke angive prioritetsindhold lige nu (det vil du kunne gøre, når politikken er oprettet)**. Hvis du vælger denne indstilling, springer du kanaldetaljesiderne over i guiden.

10. Vælg **Næste for** at fortsætte.

11. Hvis du har valgt Jeg vil angive **SharePoint-websteder,** følsomhedsmærkater og/eller følsomme oplysningstyper som prioritetsindhold i det forrige trin, får du vist detaljesiderne for *SharePoint-websteder**, typer* af følsomme oplysninger og følsomhedsmærkater. Brug disse detaljesider til at definere de SharePoint, typer af følsomme oplysninger og følsomhedsetiketter, der skal prioriteres i politikken.

    - **SharePoint websteder**: Vælg **Tilføj SharePoint websted,** og vælg SharePoint websteder, du har adgang til og vil prioritere. " *group1@contoso.sharepoint.com/sites/group1"*.
    - **Type af følsomme oplysninger**: **Vælg Tilføj følsom oplysningstype** , og vælg de følsomhedstyper, du vil prioritere. For eksempel *"USA Bankkontonummer"* og *"Kreditkortnummer"*.
    - **Følsomhedsmærkater**: **Vælg Tilføj følsomhedsmærkat** , og vælg de etiketter, du vil prioritere. For eksempel *"Fortroligt"* og *"Fortroligt"*.

    >[!NOTE]
    >Brugere, der konfigurerer politikken og vælger prioritet af Share Point-websteder, kan SharePoint websteder, de har tilladelse til at få adgang til. Hvis SharePoint websteder ikke kan vælges i politikken af den aktuelle bruger, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de nødvendige websteder.

12. Vælg **Næste for** at fortsætte.
13. Hvis du har valgt de generelle datalækager eller *datalækager* efter *prioritetsbrugerskabeloner* , kan du se valgmuligheder på siden Udløsere til denne politik for brugerdefinerede **udløsningshændelser** og politikindikatorer. Du har mulighed for at vælge en DLP-politik eller indikatorer til at udløse hændelser, der bringer brugere, som er tildelt politikkens omfang, til aktivitetsscore. Hvis du vælger brugeren svarer til en indstilling til forebyggelse af datatab **(DLP)** -politik, der udløser hændelse, skal du vælge en DLP-politik på rullelisten for DLP-politikken for at aktivere udløsere indikatorer for DLP-politikken for denne insider-politik for risikostyring. Hvis du vælger Brugeren **udfører en udfyldningsaktivitet** , der udløser hændelsesindstillingen, skal du vælge en eller flere af de angivne indikatorer for den politik, der udløser begivenheden.
    >[!IMPORTANT]
    >Hvis du ikke kan vælge en angivet indikator, skyldes det, at de ikke er aktiveret for din organisation. For at gøre dem tilgængelige til at vælge og tildele til politikken skal du aktivere indikatorerne i **Insider-Indstillinger** >  >  **Policy-indikatorer**.

    Hvis du har valgt andre politikskabeloner, understøttes brugerdefinerede udløserhændelser ikke. Den indbyggede politik, der udløser hændelser, anvendes, og du fortsætter til trin 23 uden at definere politikattributter.

14. Vælg **Næste for** at fortsætte.
15. Hvis du har valgt de generelle datalækager eller *datalækager* efter prioritetsbrugerskabeloner og har valgt, at Brugeren skal udføre en  **udfyldningsaktivitet** og tilknyttede indikatorer, kan du vælge brugerdefinerede eller standardtærskelværdier for de indikatorudløserhændelser, du har valgt. Vælg enten Brug **standardtærskelværdier (anbefales)** eller **Brug brugerdefinerede grænseværdier for udløsningshændelser**.
16. Vælg **Næste for** at fortsætte.
17. Hvis du har valgt Brug brugerdefinerede grænseværdier **for udløsningshændelser**, skal du for hver udløserbegivenhedsindikator, du valgte i trin 13, vælge det relevante niveau for at oprette det ønskede niveau af aktivitetsbeskeder.
18. Vælg **Næste for** at fortsætte.
19. På siden **Politikindikatorer** får du vist de indikatorer, du [](insider-risk-management-settings.md#indicators) har angivet som tilgængelige, på siden Insider-risikoindstillingerIndikatorer > . Vælg de indikatorer, du vil anvende på politikken.

    > [!IMPORTANT]
    > Hvis symboler på denne side ikke kan vælges, skal du vælge de indikatorer, du vil aktivere for alle politikker. Du kan bruge knappen **Aktivér indikatorer** i guiden eller vælge indikatorer på siden **Insider-Indstillinger** >  >  **Policy-indikatorer**.

    Hvis du har valgt mindst én indikator *Office* eller *Enhedsindikator*, skal du vælge **risikoscorecores efter** behov. Risikoscorepoint gælder kun for udvalgte indikatorer.
    Hvis du har valgt en politikskabelon til *datatyveri* eller  *Datalækager*, skal du vælge en eller flere metoder  til registrering af sekvenser og en kumulativ metode til registrering af udfyldning, som kan anvendes på politikken.

20. Vælg **Næste for** at fortsætte.
21. På siden **Beslut, om du vil bruge standard** - eller brugerdefinerede indikatortærskler skal du vælge brugerdefinerede eller standardtærskelværdier for de politikindikatorer, du har valgt. Vælg enten Brug **standardtærskelværdier for alle indikatorer eller** **Angiv brugerdefinerede grænseværdier** for de valgte politikindikatorer. Hvis du har valgt Angiv brugerdefinerede grænseværdier, skal du vælge det relevante niveau for at oprette det ønskede niveau af aktivitetsbeskeder for hver politikindikator.
22. Vælg **Næste for** at fortsætte.
23. På siden **Gennemse** skal du gennemgå de indstillinger, du har valgt for politikken, samt eventuelle forslag eller advarsler for dine valg. Vælg **Rediger** for at ændre nogen af politikværdierne, eller vælg **Send** for at oprette og aktivere politikken.

## <a name="update-a-policy"></a>Opdater en politik

Hvis du vil opdatere en eksisterende insider-politik for risikostyring, skal du bruge guiden til  politik i Insider-risikostyringsløsningen i Microsoft 365 Overholdelsescenter.

Udfør følgende trin for at administrere en eksisterende politik:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring** og vælge **fanen** Politikker.
2. Vælg den politik, du vil administrere, på politikdashboardet.
3. På siden med politikoplysninger skal du vælge **Rediger politik**
4. I guiden politik kan du ikke redigere følgende:
    - **Politikskabelon**: Den skabelon, der bruges til at definere de typer risikoindikatorer, der overvåges af politikken.
    - **Navn**: Det brugervenlige navn til politikken
5. På siden **Navn og** beskrivelse skal du opdatere beskrivelsen af politikken i **feltet** Beskrivelse.
6. Vælg **Næste for** at fortsætte.
7. På siden **Brugere** og grupper skal du vælge  Inkluder alle brugere og  grupper eller Inkluder bestemte brugere og grupper for at definere, hvilke brugere eller grupper, der er inkluderet i politikken, eller hvis du har valgt en prioritetsbaseret skabelon for brugere. skal **du vælge Tilføj eller rediger prioritetsbrugergrupper**. Hvis du **vælger Medtag alle** brugere og grupper, leder du efter udløserhændelser for alle brugere og grupper i organisationen for at begynde at tildele risikopoint for politikken. Hvis du **vælger Medtag bestemte brugere og grupper,** kan du angive, hvilke brugere og grupper der skal tildeles politikken. Gæstebrugerkonti understøttes ikke.
8. Vælg **Næste for** at fortsætte.
9. På siden **Indhold, der** skal prioritere kan du tildele (hvis det er nødvendigt) de kilder, der skal prioriteres, hvilket øger risikoen for at generere en besked om høj alvorsgrad for disse kilder. Vælg en af følgende valgmuligheder:

    - **Jeg vil angive SharePoint, følsomhedsmærkater og/eller følsomme oplysningstyper som prioritetsindhold**. Hvis du vælger denne indstilling, aktiveres detaljesider i guiden til konfiguration af disse kanaler.
    - **Jeg vil ikke angive prioritetsindhold lige nu (det vil du kunne gøre, når politikken er oprettet)**. Hvis du vælger denne indstilling, springer du kanaldetaljesiderne over i guiden.

10. Vælg **Næste for** at fortsætte.

11. Hvis du har valgt Jeg vil angive **SharePoint-websteder,** følsomhedsmærkater og/eller følsomme oplysningstyper som prioritetsindhold i det forrige trin, får du vist detaljesiderne for *SharePoint-websteder**, typer* af følsomme oplysninger og følsomhedsmærkater. Brug disse detaljesider til at definere de SharePoint, typer af følsomme oplysninger og følsomhedsetiketter, der skal prioriteres i politikken.

    - **SharePoint websteder**: Vælg **Tilføj SharePoint websted,** og vælg SharePoint websteder, du har adgang til og vil prioritere. " *group1@contoso.sharepoint.com/sites/group1"*.
    - **Type af følsomme oplysninger**: **Vælg Tilføj følsom oplysningstype** , og vælg de følsomhedstyper, du vil prioritere. For eksempel *"USA Bankkontonummer"* og *"Kreditkortnummer"*.
    - **Følsomhedsmærkater**: **Vælg Tilføj følsomhedsmærkat** , og vælg de etiketter, du vil prioritere. For eksempel *"Fortroligt"* og *"Fortroligt"*.

    >[!NOTE]
    >Brugere, der konfigurerer politikken og vælger prioritet af Share Point-websteder, kan SharePoint websteder, de har tilladelse til at få adgang til. Hvis SharePoint websteder ikke kan vælges i politikken af den aktuelle bruger, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de nødvendige websteder.

12. Vælg **Næste for** at fortsætte.
13. Hvis du har valgt de generelle datalækager eller *datalækager* efter *prioritetsbrugerskabeloner* , kan du se valgmuligheder på siden Udløsere til denne politik for brugerdefinerede **udløsningshændelser** og politikindikatorer. Du har mulighed for at vælge en DLP-politik eller indikatorer til at udløse hændelser, der bringer brugere, som er tildelt politikkens omfang, til aktivitetsscore. Hvis du vælger brugeren svarer til en indstilling til forebyggelse af datatab **(DLP)** -politik, der udløser hændelse, skal du vælge en DLP-politik på rullelisten for DLP-politikken for at aktivere udløsere indikatorer for DLP-politikken for denne insider-politik for risikostyring. Hvis du vælger Brugeren **udfører en udfyldningsaktivitet** , der udløser hændelsesindstillingen, skal du vælge en eller flere af de angivne indikatorer for den politik, der udløser begivenheden.
    >[!IMPORTANT]
    >Hvis du ikke kan vælge en angivet indikator, skyldes det, at de ikke er aktiveret for din organisation. For at gøre dem tilgængelige til at vælge og tildele til politikken skal du aktivere indikatorerne i **Insider-Indstillinger** >  >  **Policy-indikatorer**.

    Hvis du har valgt andre politikskabeloner, understøttes brugerdefinerede udløserhændelser ikke. Den indbyggede politik, der udløser hændelser, anvendes, og du fortsætter til trin 23 uden at definere politikattributter.

14. Vælg **Næste for** at fortsætte.
15. Hvis du har valgt de generelle datalækager eller *datalækager* efter prioritetsbrugerskabeloner og har valgt, at Brugeren skal udføre en  **udfyldningsaktivitet** og tilknyttede indikatorer, kan du vælge brugerdefinerede eller standardtærskelværdier for de indikatorudløserhændelser, du har valgt. Vælg enten Brug **standardtærskelværdier (anbefales)** eller **Brug brugerdefinerede grænseværdier for udløsningshændelser**.
16. Vælg **Næste for** at fortsætte.
17. Hvis du har valgt Brug brugerdefinerede grænseværdier **for udløsningshændelser**, skal du for hver udløserbegivenhedsindikator, du valgte i trin 13, vælge det relevante niveau for at oprette det ønskede niveau af aktivitetsbeskeder.
18. Vælg **Næste for** at fortsætte.
19. På siden **Politikindikatorer** får du vist de indikatorer, du [](insider-risk-management-settings.md#indicators) har angivet som tilgængelige, på siden Insider-risikoindstillingerIndikatorer > . Vælg de indikatorer, du vil anvende på politikken.

    > [!IMPORTANT]
    > Hvis symboler på denne side ikke kan vælges, skal du vælge de indikatorer, du vil aktivere for alle politikker. Du kan bruge knappen **Aktivér indikatorer** i guiden eller vælge indikatorer på siden **Insider-Indstillinger** >  >  **Policy-indikatorer**.

    Hvis du har valgt mindst én indikator *Office* eller *Enhedsindikator*, skal du vælge **risikoscorecores efter** behov. Risikoscorepoint gælder kun for udvalgte indikatorer.
    Hvis du har valgt en politikskabelon til *datatyveri* eller  *Datalækager*, skal du vælge en eller flere metoder  til registrering af sekvenser og en kumulativ metode til registrering af udfyldning, som kan anvendes på politikken.

20. Vælg **Næste for** at fortsætte.
21. På siden **Beslut, om du vil bruge standard** - eller brugerdefinerede indikatortærskler skal du vælge brugerdefinerede eller standardtærskelværdier for de politikindikatorer, du har valgt. Vælg enten Brug **standardtærskelværdier for alle indikatorer eller** **Angiv brugerdefinerede grænseværdier** for de valgte politikindikatorer. Hvis du har valgt Angiv brugerdefinerede grænseværdier, skal du vælge det relevante niveau for at oprette det ønskede niveau af aktivitetsbeskeder for hver politikindikator.
22. Vælg **Næste for** at fortsætte.
23. På siden **Gennemse** skal du gennemgå de indstillinger, du har valgt for politikken, samt eventuelle forslag eller advarsler for dine valg. Vælg **Rediger** for at ændre nogen af politikværdierne, eller vælg **Send** for at oprette og aktivere politikken.

## <a name="copy-a-policy"></a>Kopiér en politik

Du skal muligvis oprette en ny politik, der svarer til en eksisterende politik, men kun have nogle få konfigurationsændringer. I stedet for at oprette en ny politik fra bunden kan du kopiere en eksisterende politik og derefter ændre de områder, der skal opdateres i den nye politik.

Udfør følgende trin for at kopiere en eksisterende politik:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring** og vælge **fanen** Politikker.
2. Vælg den politik, du vil kopiere, på politikdashboardet.
3. På siden med politikoplysninger skal du vælge Kopiér.
4. I guiden politik skal du navngive den nye politik og opdatere politikkonfigurationen efter behov.

## <a name="immediately-start-scoring-user-activity"></a>Begynd straks at score brugeraktivitet

Der kan være scenarier, hvor du straks skal begynde at tildele risikoresultater til brugere med insider-risikopolitikker uden for insider-risikostyring, der udløser hændelsesarbejdsprocessen. Brug **Start** pointaktivitet for brugere på fanen  Politikker til manuelt at føje en bruger (eller brugere) til en eller flere Insider-risikopolitikker i en bestemt periode, til straks at tildele risikoresultater til deres aktivitet og til at tilsidesætte kravet om, at en bruger skal have en udløsende indikator (f.eks. et DLP-politik match). Du kan også føje en årsag til at føje brugeren til politikken, som vises på brugerens aktivitetstidslinje. Brugere, der er føjet manuelt til politikker, vises **i dashboardet** Brugere, og der oprettes beskeder, hvis aktiviteten opfylder politikadvarselstærskelværdierne.

Nogle scenarier, hvor du med det samme ønsker at starte pointdeling af brugeraktiviteter:

- Når brugerne identificeres med risici, og du vil begynde at tildele risikoresultater til deres aktivitet for en eller flere af dine politikker
- Når der er en hændelse, der kan kræve, at du straks begynder at tildele risikoresultater til involverede brugeres aktivitet for en eller flere af dine politikker
- Når du ikke har konfigureret din HR-forbindelse endnu, men du vil i gang med at tildele risikoresultater til brugeraktiviteter for HR-begivenheder ved at uploade en .csv-fil til brugerne

> [!NOTE]
> Det kan tage flere timer, før nye manuelt tilføjede brugere vises i **brugerdashboardet** . Det kan tage op til 24 timer at få vist aktiviteter for disse brugere i de foregående 90 dage. Hvis du vil have vist aktiviteter for manuelt tilføjede brugere,  skal du gå til fanen Brugere og vælge brugeren **på dashboardet** Brugere  og åbne fanen Brugeraktivitet i detaljeruden.

Hvis du manuelt vil starte pointaktivitet for brugere i en eller flere insider-risikostyringspolitikker, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring** og vælge **fanen** Politikker.
2. Vælg den eller de politikker, du vil føje brugere til, på politikdashboardet.
3. Vælg **Start pointaktivitet for brugere**.
4. I feltet **Årsag i** ruden **Føj brugere til flere politikker** skal du tilføje en årsag til at tilføje brugerne.
5. I feltet **Dette bør vare i (vælg mellem 5 og 30 dage)** skal du definere antallet af dage, brugerens aktivitet for den politik, brugeren føjes til
6. Hvis du vil søge efter brugere i dit Active Directory, skal du **bruge feltet Søg efter bruger til at føje til politikker** . Skriv navnet på den bruger, du vil føje til politikkerne. Vælg brugernavnet, og gentag proceduren for at tildele flere brugere til politikkerne. Listen over brugere, du har valgt, vises i afsnittet Brugere i ruden Føj brugere til flere politikker.
7. Hvis du vil importere en liste over brugere, der skal føjes til politikkerne, skal du vælge **Importér** for at .csv (kommaseparerede værdier). Filen skal være i følgende format, og du skal angive brugerens hovednavne i filen:

    ```csv
    user principal name
    user1@domain.com
    user2@domain.com
    ```

8. Vælg Føj brugere til politikker for at acceptere ændringerne og føje brugere til politikkerne, eller vælg Annuller for at annullere ændringerne og lukke dialogboksen.

## <a name="stop-scoring-users-in-a-policy"></a>Stoppe pointdeling af brugere i en politik

Hvis du vil stoppe med at score brugere i en politik, skal du se artiklen Insider-risikostyringsbrugere: Fjern brugere fra en [omfangsbaseret tildeling til en politikartikel](insider-risk-management-users.md#remove-users-from-in-scope-assignment-to-policies) .

## <a name="delete-a-policy"></a>Slet en politik

> [!NOTE]
> Når du sletter en politik, sletter det ikke aktive eller arkiverede beskeder, der genereres fra politikken.

Hvis du vil slette en eksisterende politik for insider-risikostyring, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring** og vælge **fanen** Politikker.
2. Vælg den politik, du vil slette, på politikdashboardet.
3. Vælg **Slet** på dashboardværktøjslinjen.
4. Vælg Ja **i** dialogboksen Slet **for at** slette politikken, eller vælg Annuller for at lukke dialogboksen.
