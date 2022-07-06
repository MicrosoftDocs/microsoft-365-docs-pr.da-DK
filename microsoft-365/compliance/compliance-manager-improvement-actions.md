---
title: Arbejde med forbedringshandlinger i Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du implementerer og tester kontrolelementer ved at arbejde med forbedringshandlinger i Microsoft Purview Compliance Manager. Tildel arbejde, gem dokumentation og eksportér rapporter.
ms.openlocfilehash: ca6855c544451661f9a8bd3cc9f59a111eeed360
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625495"
---
# <a name="working-with-improvement-actions-in-compliance-manager"></a>Arbejde med forbedringshandlinger i Overholdelsesstyring

**I denne artikel:** I denne artikel forklares det, hvordan **du administrerer din arbejdsproces for overholdelse af angivne standarder** med forbedringshandlinger. Få mere at vide om, hvordan **du tildeler forbedringshandlinger** til implementering og test, **administrerer opdateringer** og **eksporterer rapporter**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Administrer arbejdsprocesser til overholdelse af angivne standarder med forbedringshandlinger

Forbedringshandlinger centraliserer dine aktiviteter for overholdelse af angivne standarder. Hver forbedringshandling giver detaljeret implementeringsvejledning, der hjælper dig med at tilpasse dig databeskyttelsesforskrifter og -standarder. Handlinger kan tildeles til brugere i din organisation for at udføre implementerings- og testarbejde. Du kan også gemme dokumentation, noter og poststatusopdateringer i handlingen.

Alle dine forbedringshandlinger er angivet på siden forbedringshandlinger. Få mere at vide om [visning af dine forbedringshandlinger](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Siden Med oplysninger om forbedring af handlinger

Hver forbedringshandling har en side med detaljer, der viser dens aktuelle status, de relaterede standarder og lovgivningsmæssige krav og anbefalede implementeringsvejledninger. [Tekniske handlinger](compliance-score-calculation.md#technical-and-non-technical-actions) omfatter linket **Start nu** , der fører dig til den rette løsning til implementering. Du kan vedhæfte dokumentation til implementering og test direkte på detaljesiden for en forbedringshandling.

Sådan får du vist detaljesiden for en forbedringshandling:

1. Gå til siden med forbedringshandlinger.
2. Vælg rækken for den ønskede forbedringshandling, som åbner siden med detaljer.

Du kan nemt få vist den næste eller forrige forbedringshandling på listen ved at vælge pil op eller pil ned i øverste højre hjørne af skærmen. Hvis du har filtreret din liste på siden forbedringshandlinger, kommer du til det næste element på den filtrerede liste, når du flytter op eller ned.

> [!TIP]
> Få mere at vide om de forskellige [typer forbedringshandlinger, og hvordan point tildeles](compliance-score-calculation.md#action-types-and-points) og indregnes i din score for overholdelse af angivne standarder.

## <a name="assign-improvement-actions"></a>Tildel forbedringshandlinger

Hvis du vil starte implementeringen af en forbedringshandling, kan du selv udføre arbejdet eller tildele det til en anden bruger. Den tildelte person kan være:

- En ejer af en forretningspolitik
- En it-implementer
- En anden medarbejder med ansvar for at udføre opgaven

Når du har identificeret den relevante modtageren, skal du sørge for, at vedkommende har en tilstrækkelig [rolle som Overholdelsesadministrator](compliance-manager-setup.md#set-user-permissions-and-assign-roles) til at udføre arbejdet. Følg derefter nedenstående trin for at tildele forbedringshandlingen:

1. På siden med oplysninger om forbedringshandlinger skal du vælge **Tildel handling** til venstre på skærmen.

2. I pop op-vinduet **Tildel til bruger** vises en liste over **foreslåede personer** over brugere. Du kan vælge brugeren på listen eller skrive mailadressen på den person, du vil tildele den til.

3. Vælg **Tildel**. Den tildelte bruger modtager en mail, der forklarer, at forbedringshandlingen er tildelt til vedkommende, med et direkte link til forbedringshandlingen.

> [!NOTE]
> Kunder med det amerikanske offentlige samfund (GCC) High and Department of Defense (DoD) modtager ikke en mail, når de tildeles forbedringshandlinger.

Den tildelte bruger kan derefter udføre de anbefalede handlinger.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Tildel en enkelt bruger flere forbedringshandlinger

Du kan tildele flere forbedringshandlinger til én bruger ved at følge disse trin:

1. Gå til siden Forbedringshandlinger.
2. Vælg området til venstre for navnet på forbedringshandlingen. Der vises et ikon for afrundet kontrol, der angiver, at du har valgt den pågældende handling. Kontrollér alle de handlinger, du vil tildele.
3. Vælg linket **Tildel til bruger** øverst i tabellen forbedringshandlinger.
4. Der vises et pop op-vindue. I feltet **Tildel til** skal du begynde at skrive navnet på den person, du vil tildele handlingerne til. Du kan også vælge på listen over foreslåede personer.
5. Når du har udfyldt feltet **Tildel til** med modtagerens navn, skal du vælge **Tildel**.
6. Derefter kan du se siden Forbedringshandlinger, hvor den nye modtager er angivet for de handlinger, du lige har tildelt.

## <a name="change-implementation-details"></a>Rediger implementeringsdetaljer

Du kan registrere implementeringsstatus og -dato for hver forbedringshandling og tilføje noter til intern reference. Disse felter kan redigeres af alle brugere med redigeringstilladelser og ikke kun af den tildelte person.

Hvis du vil redigere status for en forbedringshandling, skal du vælge **Rediger implementeringsoplysninger** på detaljesiden. Nedenfor er de tilgængelige felter og statusindstillinger:

- **Status for implementering**
  - **Ikke implementeret**: Handlingen er endnu ikke implementeret
  - **Delvist implementeret**: For automatisk testede handlinger er handlingen delvist implementeret (hverken består eller mislykkes) og modtager en delvis score
  - **Implementeret**: handling implementeret
  - **Alternativ implementering**: Vælg denne indstilling, hvis du har brugt andre tredjepartsværktøjer eller har udført andre handlinger, der ikke er inkluderet i Microsofts anbefalinger
  - **Planlagt**: Der er planlagt en handling til implementering
  - **Uden for omfanget**: Handling er ikke relevant for din organisation og bidrager ikke til din score
- **Implementeringsdato**: tilgængelig til at vælge, hvornår implementeringsstatus er "implementeret" eller "alternativ implementering"
- **Implementeringsnoter**: tekstfelt til noter om implementeringen.

Der er ingen tegngrænse i notefelterne. Vi anbefaler, at du holder noterne korte, så du nemt kan få vist og redigere dem fra siden med oplysninger om forbedringshandlinger.

Almindelige handlinger synkroniseres på tværs af grupper. Når to forskellige vurderinger i den samme gruppe deler forbedringshandlinger, der administreres af dig, synkroniseres alle opdateringer, du foretager af en handlings implementeringsoplysninger eller status, automatisk til den samme handling i en hvilken som helst anden vurdering i gruppen. Denne synkronisering giver dig mulighed for at implementere én forbedringshandling og opfylde flere krav på tværs af flere regler.

## <a name="change-test-status"></a>Skift teststatus

I afsnittet **Test** kan du få vist teststatussen for din forbedringshandling, testdatoen og eventuelle noter. En bruger med redigeringstilladelser kan vælge  **Rediger testoplysninger** for at redigere indhold under fanen **Test** .

#### <a name="testing-status-fields"></a>Test af statusfelter

**Teststatus**
 
Du kan redigere teststatussen, når en forbedringshandlings implementeringsstatus er "implementeret" eller "alternativ implementering".

Teststatusser for [manuelt testede handlinger](#manual-testing-source):
  - **Ingen**: Der er ikke startet noget arbejde på handlingen
  - **Ikke vurderet**: Handlingen er ikke blevet testet
  - **Bestået**: Gennemførelsen er blevet kontrolleret af en vurderingsperson
  - **Mislykket lav risiko**: Test mislykkedes, lav risiko
  - **Mislykket mellemstor risiko**: Test mislykkedes, mellem risiko
  - **Fejl med høj risiko**: Test mislykkedes, høj risiko
  - **Uden for omfanget**: Handlingen er ikke omfattet af vurderingen og bidrager ikke til din score
  - **Igangværende**: test er i gang
  - **Afhjælpet**: tbd

[Automatisk testede handlinger](#automatic-testing-source) kan også vise en af følgende tilstande i kolonnen **Teststatus** på siden **Forbedringshandlinger** :
   - **Skal registreres**: Afventer signaler, der angiver teststatus
  - **Der kunne ikke registreres**: Der kunne ikke registreres en teststatus. kontrolleres automatisk igen
  - **Delvist testet**: Handlingen er delvist testet;  hverken består eller mislykkes

> [!NOTE]
> Teststatus og testnoter for automatisk testede forbedringshandlinger kan ikke redigeres manuelt. Overholdelsesstyring opdaterer disse felter for dig.

**Testdato**

Skift mellem kalender pop op-vinduet for at vælge testdatoen.

**Test af noter** og **yderligere noter**

Angiv noter til din egen interne reference i disse fritekstfelter.

**Testhistorik**

Testhistorikken indeholder en downloadet rapport over alle ændringer af teststatus for forbedringshandlingen.

#### <a name="exporting-testing-history"></a>Eksport af testhistorik
Du kan eksportere en rapport, der viser dig en oversigt over alle ændringer i teststatus for en forbedringshandling. Disse rapporter er især nyttige til overvågning af status for [handlinger, der testes automatisk](#automatic-testing-source), da sådanne handlinger regelmæssigt eller ofte opdateres på baggrund af din lejers data.

På siden med oplysninger om en forbedringshandling skal du vælge fanen **Test** . Under **Testhistorik** skal du vælge knappen **Eksportér testhistorik** . Rapporten downloades som en Excel-fil.

## <a name="update-testing-source"></a>Opdater testkilde

Overholdelsesstyring giver dig mulighed for at teste forbedringshandlinger. I afsnittet **Oversigt** for hver forbedringshandling har området **Testkilde** en rullemenu, hvorfra du kan vælge, hvordan handlingen skal testes: **Manuel**, **Automatisk** og **Overordnet**. Få mere at vide om hver testmetode nedenfor.

#### <a name="manual-testing-source"></a>Manuel testkilde
Forbedringshandlinger, der er angivet for manuel test, er handlinger, som du manuelt tester og implementerer. Du angiver de nødvendige tilstande for implementering og teststatus og uploader eventuelle dokumentationsfiler under fanen **Dokumenter** . For nogle handlinger er dette den eneste tilgængelige metode til test af forbedringshandlinger.

#### <a name="automatic-testing-source"></a>Automatisk testkilde
Visse forbedringshandlinger kan testes automatisk af Overholdelsesstyring. [Få oplysninger](compliance-manager-improvement-actions.md#update-testing-source) om, hvilke forbedringshandlinger der kan og ikke kan testes automatisk.

For de forbedringshandlinger, der kan testes automatisk, kan du se indstillingen **Automatisk** til test af kilde. Overholdelsesstyring registrerer signaler fra andre løsninger til overholdelse af angivne standarder, som du har konfigureret i dit Microsoft 365-miljø, samt eventuelle komplementære handlinger, som Microsoft Secure Score også overvåger. Feltet **Testlogik** under fanen **Test** viser, hvilken type politik eller konfiguration der kræves i en anden løsning, for at handlingen kan overføre og optjene point i forhold til din overholdelsesscore.

Når signaler angiver, at en forbedringshandling er blevet implementeret korrekt, modtager du automatisk de point, der er berettiget til den pågældende handling, hvilket vil indregne scorer for alle relaterede kontrolelementer og vurderinger. Få mere at vide om, hvordan [kontinuerlig vurdering påvirker din score for overholdelse af angivne standarder](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

 Automatisk test er som standard slået til for alle berettigede forbedringshandlinger. Du kan justere disse indstillinger, så de kun tester visse forbedringshandlinger automatisk, eller du kan deaktivere automatisk test for alle handlinger. Få mere at vide om, hvordan automatiseret test fungerer, og hvordan du justerer dine indstillinger under [Konfigurer automatiseret test](compliance-manager-setup.md#manage-automated-testing-settings).

#### <a name="parent-testing-source"></a>Overordnet testkilde

Når du vælger **Overordnet** som testkilde for en forbedringshandling, vælger du en anden handling, som handlingen skal sammenkædes med. Din handling, der træder i kraft, bliver "underordnet" til den handling, du angiver som "overordnet". Når du angiver en overordnet til en forbedringshandling, vil denne handling være indbygget i implementerings- og testdetaljerne for den overordnede handling. Hver gang den overordnede handlings status ændres, nedarver barnets status disse ændringer. Den underordnede handling accepterer også alle beviser under fanen **Dokumenter** , der tilhører den overordnede handling, hvilket kan tilsidesætte alle data, der tidligere fandtes i den underordnede handlings **dokumenter**.

> [!NOTE]
> Hvis du har en testkilde for **Overordnet** , betyder det ikke nødvendigvis, at handlingen automatisk testes af Overholdelsesstyring. Hvis den overordnede handlings testkilde f.eks. er **manuel**, får den underordnede handling statussen overordnet handling, som er en manuel test og implementering af organisationen.

Hvis du vil konfigurere en overordnet testkilde, skal du følge nedenstående trin:

- Find afsnittet **Oversigt** på siden med oplysninger om en forbedringshandling.
- Under overskriften **Testkilde** skal du vælge **Overordnet** i rullemenuen.
- Vælg **Tildel overordnet**.
- I pop op-vinduet **Tildel overordnet forbedring** skal du finde den forbedringshandling, du vil tildele som overordnet på listen, eller angive handlingens navn på søgelinjen øverst. Når du identificerer den ønskede handling, skal du markere det afkrydsningsfelt, der vises til venstre for handlingsnavnet, når du holder markøren over den og derefter vælger **Gem**.

Du kommer tilbage til detaljesiden for din handling. Under **Testkilde** i afsnittet **Oversigt** vises den nye handling, du har angivet som overordnet, under **Overordnet handling**.

## <a name="review-standards-and-regulations"></a>Revision af standarder og forskrifter

Afsnittet **om standarder og forskrifter** indeholder en søgbar og filtreret liste over standarder og bestemmelser, der er knyttet til din forbedringshandling. Disse kan ses af det relevante **kontrolelement**, **kontrol-id'et**, **kontrolfamilien** og den pågældende **forordning** .

## <a name="perform-work-and-store-documentation"></a>Udfør arbejde og gem dokumentation

Du kan uploade filer og noter, der er relateret til implementering og test, direkte til afsnittet **Dokumenter** . Dette miljø er et sikkert, centraliseret lager, der hjælper dig med at demonstrere tilfredshed med kontrolelementer, der overholder angivne standarder og bestemmelser. Alle brugere med skrivebeskyttet adgang kan læse indhold i dette afsnit. Det er kun brugere med redigeringsrettigheder, der kan uploade og downloade filer.

#### <a name="uploaded-documents"></a>Overførte dokumenter

- Vælg **Administrer dokumenter** for at overføre relevante filer.
- Når pop op-vinduet Administrer dokumenter åbnes, skal du vælge **Tilføj dokument** og derefter vælge din fil fra dit system. Accepterede filtyper:
  - Dokumenter (.doc, .xls, .ppt, .txt, .pdf)
  - Billeder (.jpg, .png)
  - Video (.mkv)
  - Komprimerede filer (.zip, .rar)
- Når filen er løst i ruden, skal du vælge **Luk**, som automatisk gemmer den vedhæftede fil. Du kan derefter se den fil, der er angivet under **Overførte dokumenter**.
- Hvis du vil hente eller slette dokumentet, skal du vælge **Administrer dokumenter** under listen over dokumenter. Vælg dokumentrækken i pop op-ruden for at fremhæve den, og vælg derefter **Download** eller **Slet**.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Tildel en forbedringshandling til bedømmer til fuldførelse

Når du har fuldført arbejdet, udført test og uploadet dokumentation, er det næste trin at tildele forbedringshandlingen til en vurderingsperson til validering. Vurderingsmanden validerer arbejdet og undersøger dokumentationen og vælger den relevante teststatus.

**Hvis teststatussen er angivet til "Bestået"**: Handlingen er fuldført, og de opnåede punkter viser de maksimale opnåede point. Pointene tælles derefter med i din overordnede score for overholdelse af angivne standarder.

**Hvis teststatussen er angivet til "Mislykket"**: Handlingen opfylder ikke kravene, og evaluatoren kan tildele den tilbage til den relevante bruger til yderligere arbejde.

## <a name="accepting-updates-to-improvement-actions"></a>Accept af opdateringer til forbedringshandlinger

Når en opdatering er tilgængelig til en forbedringshandling, får du vist en meddelelse ud for dens navn. Du kan enten acceptere opdateringen eller udskyde den et senere tidspunkt.

#### <a name="what-causes-an-update"></a>Hvad er årsagen til en opdatering

Der forekommer en opdatering, når der er ændringer relateret til scoring, automatisering eller omfang. Ændringer kan omfatte ny vejledning i forbedringshandlinger baseret på lovgivningsmæssige ændringer, eller det kan skyldes produktændringer. Det er kun de forbedringshandlinger, der administreres af dine organisationer, der modtager opdateringsmeddelelser.

#### <a name="where-youll-see-assessment-update-notifications"></a>Her kan du se meddelelser om vurderingsopdatering

Når en forbedringshandling opdateres, får du vist mærkaten **Afventer opdatering** ud for navnet på siden forbedringshandlinger og på detaljesiden for dens relaterede vurderinger.

Gå til detaljesiden for forbedringshandlingen, og vælg knappen **Gennemse opdatering** på det øverste banner for at gennemse detaljer om ændringerne og acceptere eller udskyde opdateringen.

#### <a name="review-update-to-accept-or-defer"></a>Gennemse opdatering for at acceptere eller udskyde

Når du har valgt **Gennemse opdatering** på siden med oplysninger om forbedring, vises der en pop op-rude i højre side af skærmen. Pop op-ruden indeholder vigtige oplysninger om opdateringen, f.eks. de vurderinger, der påvirkes, og ændringer i score og omfang.

Vælg **Acceptér opdatering** for at acceptere alle ændringerne i forbedringshandlingen. **Accepterede ændringer er permanente**.

> [!NOTE]
> Når du accepterer en opdatering til en handling, accepterer du også opdateringer til andre versioner eller forekomster af denne handling. Opdateringer overføres for hele lejeren for tekniske handlinger og overføres gruppevis for ikke-tekniske handlinger.

Hvis du vælger **Annuller**, anvendes opdateringen ikke på forbedringshandlingen. Du vil dog fortsat se meddelelsen **Ventende opdatering** , indtil du accepterer opdateringen.

**Derfor anbefaler vi, at du accepterer opdateringer**

Accept af opdateringer hjælper med at sikre, at du har den mest opdaterede vejledning i at bruge løsninger og træffe passende forbedringshandlinger for at hjælpe dig med at opfylde kravene til den certificering, der er ved hånden.

**Derfor kan det være en god idé at udskyde en opdatering**

Hvis du er ved at fuldføre en vurdering, der indeholder forbedringshandlingen, kan du sikre dig, at du er færdig med at arbejde på den, før du accepterer opdateringen. Du kan udskyde opdateringen til et senere tidspunkt ved at vælge **Annuller** i pop op-vinduet til gennemsynsopdatering.

#### <a name="accept-all-updates-at-once"></a>Acceptér alle opdateringer på én gang

Hvis du har flere opdateringer og vil acceptere dem alle på én gang, skal du vælge linket **Acceptér alle opdateringer** øverst i tabellen forbedringshandlinger. Der vises en pop op-rude, som viser antallet af handlinger, der skal opdateres. Vælg knappen **Acceptér opdateringer** for at anvende alle opdateringer.

Bemærk, at når du vender tilbage til siden med forbedringshandlinger, får du muligvis vist en meddelelse øverst på siden, hvor du bliver bedt om at opdatere siden, så opdateringerne kan fuldføres.

## <a name="set-up-alerts-for-improvement-action-changes"></a>Konfigurer beskeder om ændringer af forbedringshandlinger

Du kan konfigurere beskeder, så du straks får besked, når der sker visse ændringer af forbedringshandlinger, f.eks. en ændring i implementerings- eller teststatus eller en stigning eller reduktion i scoren. Hvis du får hurtige meddelelser om sådanne ændringer, kan det hjælpe dig med at holde styr på mulige risici for overholdelse af angivne standarder. Besøg [Overholdelsesstyringsbeskeder og beskedpolitikker](compliance-manager-alert-policies.md) for at få mere at vide om, hvordan du konfigurerer beskeder.

## <a name="export-a-report"></a>Eksportér en rapport

Vælg **Eksportér** i øverste venstre hjørne af skærmen for at hente et Excel-regneark, der indeholder alle dine forbedringshandlinger og de filterkategorier, der vises på siden forbedringshandlinger.
