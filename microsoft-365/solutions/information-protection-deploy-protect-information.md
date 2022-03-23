---
title: Beskytte oplysninger i henhold til persondataforordningen
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Installer Microsoft 365 funktioner til sikkerhed og overholdelse af regler og standarder, og beskyt dine personlige oplysninger.
ms.openlocfilehash: 2739da0b5e9c4896b65751c63d9b2e5f3b026a2e
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588233"
---
# <a name="protect-information-subject-to-data-privacy-regulation"></a>Beskytte oplysninger i henhold til persondataforordningen

Der kan anvendes en række kontrolforanstaltninger til beskyttelse af oplysninger i dit abonnement for at afhjælpe behov og bestemmelser vedrørende overholdelse af regler og standarder for beskyttelse af data. Disse omfatter General Data Protection Regulation (GDPR), HIPAA-HITECH (UNITED States Health Care Privacy Act), California Consumer Protection Act (CCPA) og LGPD (Brazil Data Protection Act).

Disse kontrolelementer er inden for følgende løsningsområder:

- Følsomhedsmærkater
- Forebyggelse af datatab (DLP)
- Office (OME)
- Teams- og webstedsadgangskontrolelementer

![Vigtige tjenester til beskyttelse af personlige oplysninger, der er underlagt lovgivningen om beskyttelse af personlige oplysninger.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-grid.png)

> [!NOTE]
> Denne løsning beskriver funktioner til sikkerhed og overholdelse af regler og standarder for at beskytte oplysninger, der er underlagt bestemmelser om beskyttelse af personlige oplysninger. Du kan finde en komplet liste over sikkerhedsfunktioner Microsoft 365 i Microsoft 365 [og sikkerhedsdokumentation](../security/index.yml). Du kan finde en komplet liste over overholdelsesfunktioner Microsoft 365 i [dokumentationen Microsoft 365 overholdelse af regler og standarder](../compliance/index.yml).

## <a name="data-privacy-regulations-that-impact-information-protection-controls"></a>Regler for beskyttelse af data, der påvirker kontrolelementer til beskyttelse af oplysninger

Her er en eksempelliste over bestemmelser om beskyttelse af data, der kan være relateret til kontrolelementer til beskyttelse af oplysninger:

- GDPR-artikel 5(1)(f))
- GDPR-artikel (32)(1)(a)
- LGPD artikel 46
- HIPAA-HITECH (45 CFR 164.312(e)(1))
- HIPAA-HITECH (45 C.F.R. 164.312(e)(2)(ii))

Se artiklen [vurder risici i forbindelse med beskyttelse af personlige oplysninger, og identificer](information-protection-deploy-assess.md) følsomme elementer for at få flere oplysninger om hvert af ovenstående.

Bestemmelser om beskyttelse af datas personlige oplysninger til beskyttelse af oplysninger anbefaler:

- Beskyttelse mod tab eller uautoriseret adgang, brug og/eller overførsel.
- Risikobaseret anvendelse af beskyttende mekanismer.
- Brug af kryptering, hvor det er relevant.

Det kan også være en ide for din organisation at beskytte Microsoft 365 indhold til andre formål, f.eks. andre overholdelsesbehov eller af forretningsmæssige årsager. Når du etablerer din plan for beskyttelse af oplysninger for beskyttelse af data, skal det gøres som en del af den overordnede planlægning, implementering og administration af beskyttelse af oplysninger.

For at hjælpe dig med at komme i gang med en informationsbeskyttelsesplan i Microsoft 365 indeholder det følgende afsnit en kort liste over relaterede funktioner og forbedringshandlinger til Microsoft 365. Listen indeholder funktioner og forbedringshandlinger, der gælder for regler om beskyttelse af personlige oplysninger for data. Men listen inkluderer ikke ældre teknologier, hvis der er en nyere funktion, der i høj grad erstatter den ældre. IRM (Information Rights Management) for SharePoint og OneDrive ikke på listen, men følsomhedsmærkaterne er medtaget.

## <a name="managing-information-protection-in-microsoft-365"></a>Administration af beskyttelse af oplysninger i Microsoft 365

[Microsofts løsninger til beskyttelse](../compliance/information-protection.md) af oplysninger omfatter en række integrerede funktioner på Microsoft 365, Microsoft Azure og Microsoft Windows. I Microsoft 365 omfatter løsninger til beskyttelse af oplysninger:

- [Typer af følsomme oplysninger](../compliance/sensitive-information-type-entity-definitions.md) (beskrevet i artiklen vurdere [risici i forbindelse med beskyttelse af data og identificere følsomme elementer)](information-protection-deploy-assess.md)
- [Følsomhedsmærkater](../compliance/sensitivity-labels.md)
  - Tjeneste/objektbeholderniveau
  - Klientside/indholdsniveau
  - Automatiseret til in-rest-data i SharePoint og OneDrive
- Forebyggelse af datatab (DLP)
- [Microsoft 365 forebyggelse af datatab på slutpunkt](../compliance/endpoint-dlp-learn-about.md)
- [Office 365-meddelelseskryptering funktioner (OME) og](../compliance/ome.md) AVANCERET [OME-meddelelseskryptering](../compliance/ome-advanced-message-encryption.md)

Desuden er beskyttelse af websteds- og biblioteksniveau vigtige mekanismer, som skal medtages i enhver beskyttelsesplan.

Du kan finde oplysninger om andre funktioner til beskyttelse af oplysninger Microsoft 365 i:

- [Microsoft Defender til skyapps](/cloud-app-security/)
- [Azure Information Protection](/azure/information-protection/what-is-information-protection)
- [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)
- [Windows beskyttelse af oplysninger](/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

Følsomhedsmærkater fra Microsoft Information Protection giver dig mulighed for at klassificere og beskytte din organisations data uden at påvirke produktiviteten for brugerne og deres mulighed for at samarbejde.

> [!div class="mx-imgBorder"]
> ![Følsomhedsmærkater i Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-labels.png)

### <a name="prerequisites-for-sensitivity-labels"></a>Forudsætninger for følsomhedsmærkater

Fuldfør disse aktiviteter, før du implementerer nogen af de følsomhedsmærkatbaserede funktioner, der er fremhævet nedenfor:

1. Forstå følgende:
   - **Virksomhedskrav.** Fastlægge de forretningsmæssige grunde til at anvende følsomhedsmærkater i din virksomhed. F.eks. dine krav til beskyttelse af personlige oplysninger.
   - **Følsomhedsmærkatfunktioner.** Følsomhedsmærkater kan blive meget komplekse, så sørg for at læse dokumentationen med [følsomhedsmærkaterne,](../compliance/sensitivity-labels.md) før du går i gang.
   - **Vigtige ting at huske** Følsomhedsmærkater administreres i Microsoft Compliance Administration, men indstillingerne for målretning og programmer varierer markant.
      - Der er følsomhedsmærkater for websteder, grupper og Teams på objektbeholderniveau (indstillingerne gælder ikke for indhold inde i beholderen). Disse publiceres til brugere og grupper, der anvender dem, når et websted, en gruppe eller et team er klargjort.
      - Der er følsomhedsmærkater for aktivt indhold. Disse publiceres også til brugere eller grupper, som enten anvender dem manuelt, eller de anvendes automatisk, når:
        - Filen åbnes/redigeres/gemmes enten på brugerens skrivebord eller et SharePoint websted.
        - En mail er kladdet og sendt.
      - Der er følsomhedsmærkater til automatisk anvendelse på filer, der ligger SharePoint og OneDrive ud over mails under overførsel gennem Exchange. Disse er rettet mod enten alle websteder eller bestemte websteder og gælder automatisk for de filer, der ligger i disse miljøer.

2. Rationaliser aktuelle følsomhedsmærkater med tidligere eller alternative metoder

   - Azure Information Protection

      Det aktuelle følsomhedsmærkatsystem kan være afstemt med en eksisterende [implementering af Azure Information Protection-mærkning](../compliance/sensitivity-labels.md#sensitivity-labels-and-azure-information-protection) .
   - OME

      Hvis du planlægger at bruge moderne følsomhed-mærkning for mailbeskyttelse og eksisterende mailkrypteringsmetoder som OME er på plads, kan de begge findes, men du skal forstå de scenarier, hvor begge skal anvendes. Se [Office 365-meddelelseskryptering nye funktioner (OME),](#office-365-message-encryption-ome-new-capabilities) som omfatter en tabel, der sammenligner moderne følsomhedsmærkat-typebeskyttelse med OME-baseret beskyttelse.

3. Planlæg integration med en bredere informationsbeskyttelsesplan. Oven i sameksistens med OME kan følsomhedsmærkater bruges på samme side som f.eks. Microsoft 365 forebyggelse af datatab (DLP) og Microsoft Defender til skyapps. Se [Microsoft Information Protection i Microsoft 365 at](../compliance/information-protection.md) opnå dine mål for beskyttelse af personlige oplysninger, som er relateret til beskyttelse af data.

4. Udvikle et følsomhedsmærkat klassificerings- og kontrolskema. Se [Dataklassificering og Følsomhedsmærkat taksonomi](https://aka.ms/dataclassificationwhitepaper).

### <a name="general-guidance"></a>Generel vejledning

1. **Skemadefinition.** Før du bruger tekniske funktioner til at anvende navne og beskyttelse, skal du arbejde på tværs af organisationen for at definere et klassificeringsskema. Du har måske allerede et klassificeringsskema, hvilket gør det nemmere at tilføje personlige data.
2. **Introduktion.** Start med at beslutte antallet og navnene på etiketterne, der skal implementeres. Gør denne aktivitet uden at bekymre dig om, hvilken teknologi der skal bruges, og hvordan etiketter anvendes. Anvend dette skema universelt i hele organisationen, herunder data, der findes lokalt og i andre skytjenester.
3. **Yderligere anbefalinger** Når du designer og implementerer politikker, etiketter og betingelser, bør du overveje at følge disse anbefalinger:

   - **Brug eksisterende klassificeringsskema (hvis dette er nogen).** Mange organisationer anvender allerede dataklassificering i en eller anden form. Evaluer omhyggeligt det eksisterende etiketskema, og brug det, som det er, hvis det er muligt. Brug af velkendte navne, der er genkendelige for dine slutbrugere, vil fremme indføringen.
   - **Start småt.** Der er stort set ingen begrænsninger for antallet af etiketter, du kan oprette. Et stort antal etiketter og underetiketter kan dog forsinke indføringen.
   - **Brug scenarier og use cases.** Identificer almindelige use cases inden for organisationen, og brug scenarier, der er afledt af de regler for beskyttelse af personlige oplysninger, som du er underlagt. Kontrollér, om konfigurationen af mærket og klassificeringen fungerer i praksis.
   - **Stille spørgsmål til alle anmodninger om en ny etiket.** Har alle scenarier eller use case virkelig brug for en ny etiket, eller kan du bruge det, du allerede har? Hvis du holder antallet af etiketter på et minimum, forbedres indføringen.
   - **Brug undernavne til nøgleafdelinger.** Nogle afdelinger har særlige behov, der kræver bestemte etiketter. Definer disse etiketter som undernavne til en eksisterende etiket, og overvej at bruge politikker, der er tildelt til brugergrupper i stedet for globalt.
   - **Overvej omfangspolitikker.** Politikker, der er målrettet mod undersæt af brugere, vil forhindre overbelastning af navne. En omfangsbaseret politik aktiverer tildeling af rolle- eller afdelingsspecifikke etiketter eller underetiketter til medarbejdere, der arbejder for den pågældende afdeling.
   - **Brug beskrivende navne.** Prøv ikke at bruge jargon, standarder eller akronymer som navne. Prøv at bruge navne, der giver slutbrugeren genlyd, for at forbedre indføringen. I stedet for at bruge navne som PII, AFSE, HIPAA, LBI, MBI og HBI kan du overveje navne som f.eks. non-business, offentlig, generelt, fortroligt og meget fortroligt.

### <a name="create-and-deploy-sensitivity-labels-for-sites-groups-and-teams"></a>Opret og implementer følsomhedsetiketter til websteder, grupper og teams

Når du opretter [følsomhedsmærkater](../compliance/sensitivity-labels-teams-groups-sites.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">i Microsoft 365 Overholdelsescenter</a>, kan du nu anvende dem på disse beholdere:

- Microsoft Teams websteder
- Microsoft 365 grupper (tidligere Office 365 grupper)
- SharePoint websteder

Brug følgende etiketindstillinger til at beskytte indholdet i disse beholdere:

- Beskyttelse af personlige oplysninger (offentlig eller privat) Microsoft 365 gruppeforbundne Teams websteder
- Adgang for eksterne brugere
- Adgang fra ikke-administrerede enheder

For beskyttelse af data skal du for at forhindre ekstern deling for objektbeholdere, der skal bruges til lagring af indhold med følsomme personlige data, markere de filer, der indeholder dataene, som private og kræve administrerede enheder.

### <a name="create-and-deploy-sensitivity-labels-for-content"></a>Opret og implementer følsomhedsmærkater for indhold

Følsomhedsmærkater, der anvendes på filer, giver dig mulighed for at kryptere deres indhold, vandmærke indholdet og definere andre kontrolelementer til Office-programindhold, herunder Outlook og Office på internettet.

Når du er klar til at begynde at beskytte din organisations data med følsomhedsmærkater:

1. **Opret etiketterne.** Opret og navngive dine følsomhedsmærkater efter organisationens klassificerings taksonomi for forskellige følsomhedsniveauer for indhold. For more information on developing a classification taxonomy, see the [Data Classification and Sensitivity Label Taxonomy white paper](https://aka.ms/dataclassificationwhitepaper).
2. **Definer, hvad hver etiket kan gøre.** Konfigurer de beskyttelsesindstillinger, der skal knyttes til hver etiket. Det kan f.eks. være, at du ønsker, at lavere følsomhedsindhold (f.eks. en "Generelt"-etiket) kun skal have et sidehoved eller en sidefod anvendt, mens højere følsomhedsindhold (f.eks. en "fortroligt" etiket) skal have et vandmærke og have kryptering aktiveret.
3. **Publicere etiketterne.** Når dine følsomhedsmærkater er konfigureret, kan du publicere dem ved hjælp af en etiketpolitik. Beslut, hvilke brugere og grupper der skal have etiketterne, og hvilke politikindstillinger der skal bruges. En enkelt etiket kan genbruges. Du definerer den én gang, og derefter kan du medtage den i flere etiketpolitikker, der er tildelt forskellige brugere.

Når du publicerer følsomhedsmærkater fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>, begynder de at blive vist i [Office-apps](../compliance/sensitivity-labels-office-apps.md), hvor brugerne kan klassificere og beskytte indhold, når det er oprettet eller redigeret.

![Installationsflow for følsomhedsmærkater i Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-label-flow.png)

Til beskyttelse af data skal du manuelt anvende en følsomhedsmærkat med kryptering og andre regler på mails eller indhold, der indeholder følsomme personlige oplysninger.

> [!NOTE]
> Følsomhedsmærkater med kryptering aktiveret på mail har nogle overlappende funktioner med OME. Se [Sammenligning af sikre mailscenarier med OME og følsomhedsmærkater](#secure-email-scenarios-comparison-with-ome-and-sensitivity-labels).

### <a name="client-side-auto-labeling-when-users-edit-documents-or-compose-emails"></a>Automatisk mærkning på klientsiden, når brugere redigerer dokumenter eller opretter mails

Når du opretter en følsomhedsmærkat, kan du automatisk tildele den [pågældende etiket](../compliance/apply-sensitivity-label-automatically.md) til indhold, herunder mail, når den opfylder de betingelser, du angiver.

Muligheden for automatisk at anvende følsomhedsmærkater på indhold er vigtig, fordi:

- Du behøver ikke at oplære dine brugere, hvornår de skal bruge hver af dine klassificeringer.
- Du behøver ikke at stole på, at brugerne klassificerer alt indhold korrekt.
- Brugere behøver ikke længere at kende til dine politikker – de kan i stedet fokusere på deres arbejde.

Automatisk mærkater understøtter anbefaling af et navn til brugere og til automatisk anvendelse af en etiket. Men i begge tilfælde beslutter brugeren, om han eller hun skal acceptere eller afvise etiketten for at sikre korrekt mærkat for indholdet.

Denne etiket på klientsiden har minimal forsinkelse for dokumenter, da etiketten kan anvendes, selv før dokumentet gemmes. Det er dog ikke alle klientapps, der understøtter automatisk mærkning. Denne funktion understøttes af den samlede Azure Information Protection-etiketklient, og [nogle versioner af Office apps](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Du kan finde [konfigurationsinstruktioner under Sådan konfigureres automatisk mærkater Office apps](../compliance/sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

Til beskyttelse af data skal du automatisk anvende følsomhedsmærkater på indhold, der indeholder følsomme personlige oplysninger.

### <a name="service-side-auto-labeling-when-content-is-already-saved"></a>Automatisk mærkning på tjenestesiden, når indhold allerede er gemt

Denne metode kaldes automatisk klassificering med følsomhedsmærkater. Du kan også høre det kaldet automatisk mærkat for in rest-data (for dokumenter i SharePoint og OneDrive) og data under overførsel (for mails, der sendes eller modtages af Exchange). For Exchange er mails i inkluder ikke i in hvilede postkasser.

Da denne mærkning anvendes af selve tjenesten i stedet for af brugerprogrammet, behøver du ikke at bekymre dig om, hvilke apps brugerne har og hvilken version. Derfor er denne funktion umiddelbart tilgængelig i hele organisationen og egnet til skalering. Politikker for automatisk mærkning understøtter ikke anbefalet mærkat, da brugeren ikke interagerer med mærkningsprocessen. I stedet kører administratoren politikkerne i simuleringstilstand for at sikre korrekt mærkat for indhold, før etiketten anvendes.

Du kan finde [konfigurationsinstruktioner i Sådan konfigureres politikker for SharePoint, OneDrive og Exchange](../compliance/apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

Tryk på følsomhedsmærkater for automatisk kryptering af indhold, der indeholder følsomme personlige oplysninger, for at beskytte data på websteder, der er problematiske.

## <a name="data-loss-prevention"></a>Forebyggelse af datatab

Du kan bruge [forebyggelse af datatab (DLP)](../compliance/dlp-learn-about-dlp.md) i Microsoft 365 til at registrere, advare og blokere risikabelt, utilsigtet eller upassende deling, f.eks. deling af data, der indeholder personlige oplysninger, både internt og eksternt.

DLP gør det muligt at:

- Identificer og overvåg risikabel delingsaktiviteter.
- Uddan brugere med kontekstafhængig vejledning i at træffe de rigtige beslutninger.
- Gennemtving politikker for databrug efter indhold uden at hindre produktivitet.
- Integrer med klassificering og mærkning for at registrere og beskytte data, når de deles.

### <a name="supported-workloads-for-dlp"></a>Understøttede arbejdsbelastninger for DLP

Med en DLP-politik i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> kan du identificere, overvåge og automatisk beskytte følsomme elementer på tværs af mange placeringer i Microsoft 365, f.eks. Exchange Online, SharePoint, OneDrive og Microsoft Teams.

Du kan f.eks. identificere et dokument, der indeholder et kreditkortnummer, der er gemt på et hvilket som helst OneDrive-websted, eller du kan overvåge netop de OneDrive af bestemte personer.

Du kan også overvåge og beskytte følsomme elementer i de lokalt installerede versioner af Excel, PowerPoint og Word, som omfatter muligheden for at identificere følsomme elementer og anvende DLP-politikker. DLP leverer løbende overvågning, når folk deler indhold fra disse Office apps.

> [!div class="mx-imgBorder"]
> ![Understøttede arbejdsbelastninger for DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-supported-workloads.png)

Figuren nedenfor viser et eksempel på beskyttelse af personlige data i DLP.

> [!div class="mx-imgBorder"]
> ![Eksempel på beskyttelse af personlige data ved hjælp af DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-use.png)

DLP bruges til at identificere et dokument eller en mail, der indeholder en tilstandspost, og blokerer derefter automatisk adgang til det pågældende dokument eller blokerer mailen fra at blive sendt. DLP giver derefter modtageren et politiktip og sender en besked til slutbrugeren og administratoren.

### <a name="planning-for-dlp"></a>Planlægning af DLP

Planlæg dine DLP-politikker for:

- Dine forretningsmæssige krav.

- En risikobaseret vurdering af organisationen som beskrevet i artiklen Vurder risici i forbindelse med [beskyttelse af personlige oplysninger og identificer følsomme elementer](information-protection-deploy-assess.md).

- Andre mekanismer til beskyttelse af oplysninger og styring på stedet eller i forbindelse med planlægning af beskyttelse af data.

- De typer af følsomme oplysninger, du har identificeret for personlige data baseret på dit vurderingsarbejde, som beskrevet i artiklen Vurder risici i forbindelse med beskyttelse af personlige oplysninger og [identificer følsomme elementer](information-protection-deploy-assess.md). DLP-politikbetingelser kan være baseret på både følsomme oplysningstyper og opbevaringsmærkater.

- De opbevaringsmærkater, du skal angive DLP-betingelser for. Du kan finde [flere oplysninger i artiklen om, hvilke oplysninger](information-protection-deploy-govern.md) der er underlagt lovgivningen om beskyttelse af personlige oplysninger for din organisation.

- Løbende administration af DLP-politikker, som kræver, at en person i organisationen kan styre og finjustere politikker for ændringer i typer af følsomme oplysninger, opbevaringsmærkater, bestemmelser og politikker for overholdelse af regler og standarder.

Selvom følsomhedsetiketter ikke kan bruges i DLP-politikbetingelser, kan visse beskyttelsesscenarier for at forhindre adgang være opnåelige blot med følsomhedsmærkater, der kan anvendes automatisk baseret på følsomme oplysningstyper. Hvis der er en robust følsomhedsmærkat, skal du overveje, om DLP skal bruges til at udvide beskyttelsen, fordi:

  - DLP kan forhindre deling af filer. Følsomhedsmærkater kan blot forhindre adgang.

  - DLP har mere detaljerede kontrolniveauer med hensyn til regler, betingelser og handlinger.

  - DLP-politikker kan anvendes på Teams chat og kanalmeddelelser. Følsomhedsmærkater kan kun anvendes på dokumenter og mails.


### <a name="dlp-policies"></a>DLP-politikker

DLP-politikker er konfigureret i Microsoft Compliance Administration og angiver beskyttelsesniveauet, typen af følsomme oplysninger, som politikken leder efter, og målarbejdsbelastningen. Deres grundlæggende komponenter består i at identificere beskyttelsen og datatyperne.

> [!div class="mx-imgBorder"]
> ![Konfiguration af DLP-politik i Microsoft 365.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-config.png)

Her er et eksempel på DLP-politik for opmærksomhed omkring GDPR.

![Eksempel på DLP-politik for opmærksomhed omkring GDPR.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-example-policy.png)

Se [denne artikel for at](../compliance/create-test-tune-dlp-policy.md) få flere oplysninger om at oprette og anvende DLP-politikker.

### <a name="protection-levels-for-data-privacy"></a>Beskyttelsesniveauer for beskyttelse af data

I følgende tabel vises tre konfigurationer af øget beskyttelse ved hjælp af DLP.

![Beskyttelsesniveauer for beskyttelse af data med DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-dlp-protection-levels.png)

Den første konfiguration, Awareness, kan bruges som et udgangspunkt og minimumsniveau for beskyttelse for at imødekomme overholdelsesbehov for regler om beskyttelse af personlige oplysninger.

> [!NOTE]
> Efterhånden som beskyttelsesniveauet øges, mindskes brugernes mulighed for at dele og få adgang til oplysninger i nogle tilfælde og kan potentielt påvirke deres produktivitet eller muligheden for at udføre daglige opgaver.

For at hjælpe dine medarbejdere med fortsat at være produktive i et mere sikkert miljø, når beskyttelsesniveauet øges, bør du bruge tid på at oplære og uddanne dem om nye sikkerhedspolitikker og -procedurer.

### <a name="example-of-using-sensitivity-labels-with-dlp"></a>Eksempel på brug af følsomhedsmærkater med DLP

Følsomhedsmærkater kan samarbejde med DLP om at levere beskyttelse af data i et meget regulerede miljø. Her er de vigtigste trin i den integrerede installation:

1. Lovgivningsmæssige og på anden måde forretningsmæssige krav til beskyttelse af personlige oplysninger er dokumenteret.
2. Målret datakilder, typer og ejerskab er forholdsmæssige i forhold til bekymringer vedrørende beskyttelse af personlige oplysninger.
3. Der opstilles en overordnet strategi for at tage hånd om krav og beskytte og styre hotspots for beskyttelse af data.
4. Der er udarbejdet en faseindfaset handlingsplan, som skal tage hånd om strategi for kontrol af datasikkerhed.

Når disse elementer er fastlagt, kan du bruge følsomme oplysningstyper, dine følsomhedsmærkater og DLP-politikker sammen. I figuren nedenfor vises et eksempel.

> [!div class="mx-imgBorder"]
> ![Eksempel på følsomhedsmærkater, der fungerer med DLP.](../media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

[Se en større version af dette billede](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/information-protection-deploy-protect-information/information-protection-deploy-protect-information-sensitivity-lables-dlp.png)

Her er nogle scenarier for databeskyttelse ved brug af DLP og følsomhedsetiketter sammen, som vist i figuren.

| Scenarie | Proces |
|:-------|:-----|
| A | <ol><li>Følsomhedsmærkater for indhold publiceres af en administrator til brugere og grupper for manuelt eller automatisk program til indhold og mail. </li><li>Bruger A anvender etiketterne manuelt eller automatisk, når der arbejdes med indhold, med kryptering eller andre indstillinger anvendt. </li><li>Bruger A sender en beskyttet mail eller fil til bruger B, en gæstebruger. </li></ol> |
| B | DLP-politik publiceret af en administrator til Bruger A blokerer bruger A fra at sende mailen og/eller filen til bruger B. |
| C |  Følsomhedsmærkat med indstillingen "ejeren kan ikke invitere gæster" er publiceret på Bruger A, som udgav et Teams team eller SharePoint websted. En anden bruger på webstedet forsøger selektivt at dele en fil med bruger B, men DLP blokerer den. |
| D | Følsomhedsmærkat for automatisk anvendelse på webstedsindhold publiceres på et eller flere websteder, hvilket giver et andet lag af beskyttelse, hvilket resulterer i et beskyttet websted. |
|||

## <a name="office-365-message-encryption-ome-new-capabilities"></a>Office 365-meddelelseskryptering (OME) nye funktioner

Folk bruger ofte mail til at udveksle følsomme elementer, f.eks. oplysninger om patient sundhed eller kunde- og medarbejderoplysninger. Kryptering af mail er med til at sikre, at det kun er de tilsigtede modtagere, der kan se meddelelsens indhold.

Med [OME](../compliance/ome.md) kan du sende og modtage krypterede meddelelser mellem personer i og uden for organisationen. OME fungerer sammen Outlook.com, Yahoo!, Gmail og andre mailtjenester. OME hjælper med at sikre, at kun de tilsigtede modtagere kan få vist meddelelsesindhold.

Til beskyttelse af data skal du bruge OME til at beskytte interne meddelelser, der indeholder følsomme elementer. Office 365-meddelelseskryptering er en onlinetjeneste, der er bygget på Microsoft Azure Rights Management (Azure RMS), som er en del af Azure Information Protection. Dette omfatter krypterings-, identitets- og godkendelsespolitikker, som er med til at sikre din mail. Du kan kryptere meddelelser ved hjælp af rettighedsstyringsskabeloner, indstillingen Videresende ikke og indstillingen kun krypteret.

Du kan også definere regler for mailflow for at anvende denne beskyttelse. Du kan f.eks. oprette en regel, der kræver kryptering af alle meddelelser, der er adresseret til en bestemt modtager, eller som indeholder bestemte nøgleord i emnelinjen, og du kan også angive, at modtagerne ikke kan kopiere eller udskrive indholdet af meddelelsen.

DESUDEN kan OME Advanced [Message Encryption](../compliance/ome-advanced-message-encryption.md) hjælpe dig med at opfylde overholdelsesforpligtelser, som kræver mere fleksible kontroller over eksterne modtagere og deres adgang til krypterede mails. Med OME Advanced Message Encryption i Microsoft 365 kan du styre følsomme mails, der deles uden for organisationen, med automatiske politikker, der registrerer følsomme oplysningstyper.

For beskyttelse af data kan du angive en udløbsdato og tilbagekalde meddelelser, hvis du har brug for at dele mail med en ekstern part. Du kan kun tilbagekalde og angive en udløbsdato for meddelelser, der sendes til eksterne modtagere.

### <a name="secure-email-scenarios-comparison-with-ome-and-sensitivity-labels"></a>Sikre mailscenarier til sammenligning med OME og følsomhedsetiketter

OME- og følsomhedsetiketter anvendt på mail med kryptering har et vist overlap, så det er vigtigt at forstå, hvilke scenarier der enten kan gælde for, som vist i denne tabel.

| Scenarie | Følsomhedsmærkater | OME |
|:-------|:-----|:-------|
| Interne + partnere <br> Kommuniker og samarbejd sikkert mellem interne brugere og partnere, der er tillid til | Anbefal – etiketter med fuldt tilpasset klassificering og beskyttelse | Ja – kun kryptér eller videresendelsesbeskyttelse uden nogen klassificering |
| Eksterne parter <br> Kommuniker og samarbejd sikkert med eksterne/forbrugerbrugere | Ja – foruddefinerede modtagere i etiket | Anbefal – just-in-time beskyttelse baseret på modtagere |
| Interne + partnere med udløb/tilbagekaldelse <br> Kontrollere adgang til mail og indhold med interne brugere og partnere, der er tillid til, med udløb og tilbagekaldelse | Anbefal – fuldt tilpasset beskyttelse med adgangsvarighed, og brugeren kan manuelt registrere og tilbagekalde filer | Nej – ingen tilbagekaldelse eller udløb af intern mail |
| Eksterne parter med udløb/tilbagekaldelse <br> Kontrollere adgang til mail og indhold med eksterne/forbrugerbrugere med udløb og tilbagekaldelse | Ja – brugeren kan manuelt registrere filer | Anbefal (E5) – administrator kan tilbagekalde mail fra Security & Compliance Center |
| Automatisk mærkning <br> Organisationen ønsker automatisk at beskytte mails/vedhæftede filer med specifikt følsomt indhold og/eller bestemte modtagere | Anbefal (E5) – Automatisk mærkatering i Exchange og Outlook klienter, øger regler for mailflow og DLP-politik | Ja – regler for mailflow og DLP-politik med kun kryptering eller videresendelsesbeskyttelse |
||||

Der vil også være forskelle i slutbruger- og administratoroplevelser mellem disse to metoder.

## <a name="teams-with-protection-for-highly-sensitive-data"></a>Teams beskyttelse af meget følsomme data

For organisationer, der planlægger at gemme personlige data, og som er underlagt bestemmelser om beskyttelse af data i Teams, skal du se Konfigurer et [team](secure-teams-security-isolation.md) med sikkerhedsisolation, som indeholder detaljeret vejledning og konfigurationstrin til:

- Identitets- og enhedsadgang
- Oprettelse af et privat team
- Låsning af underliggende teamwebstedstilladelser
- En gruppebaseret følsomhedsmærkat med kryptering
