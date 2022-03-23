---
title: Arbejde med forbedringshandlinger i Microsoft Overholdelsesstyring
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
description: Få mere at vide om, hvordan du implementerer og tester kontrolelementer ved at arbejde med forbedringshandlinger i Microsoft Compliance Manager. Tildel arbejde, gem dokumentation, og eksportér rapporter.
ms.openlocfilehash: 33b1de7dfc116cc1403d0e3619dfbec2f0853be3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591458"
---
# <a name="working-with-improvement-actions-in-compliance-manager"></a>Arbejde med forbedringshandlinger i Overholdelsesstyring

**I denne artikel:** I denne artikel forklares det, hvordan **du administrerer arbejdsprocessen i forbindelse med** overholdelse med forbedringshandlinger. Få mere at vide **om, hvordan du tildeler** forbedringshandlinger til implementering og **test, administrerer** opdateringer og **eksporterer rapporter**.

## <a name="manage-compliance-workflows-with-improvement-actions"></a>Administrere arbejdsprocesser for overholdelse af regler og standarder med forbedringshandlinger

Forbedringshandlinger centraliserer dine overholdelsesaktiviteter. Hver forbedring giver detaljerede retningslinjer for implementering, som kan hjælpe dig med at rette ind efter regler og standarder inden for databeskyttelse. Handlinger kan tildeles til brugere i organisationen til at udføre implementerings- og testarbejde. Du kan også gemme dokumentation, noter og statusopdateringer for poster i handlingen.

Alle dine forbedringshandlinger er angivet på siden for forbedringshandlinger. Få mere at vide [om at få vist dine forbedringshandlinger](compliance-manager-setup.md#improvement-actions-page).

## <a name="improvement-actions-details-page"></a>Detaljeside med oplysninger om forbedringshandlinger

Hver forbedringshandling har en detaljeside, der viser dens aktuelle status, de relaterede standarder og lovmæssige krav samt anbefalede retningslinjer for implementering. [Tekniske handlinger omfatter](compliance-score-calculation.md#technical-and-non-technical-actions) et **Start nu-link** , der fører dig til den relevante løsning til implementering. Du kan vedhæfte implementerings- og testdokumentation direkte til detaljesiden for en forbedringshandling.

Sådan får du vist detaljesiden for en forbedringshandling:

1. Gå til siden med dine forbedringshandlinger.
2. Vælg rækken for den tilsigtede forbedringshandling, som åbner detaljesiden.

Du kan nemt få vist den næste eller forrige forbedringshandling på listen ved at vælge pil op eller pil ned i øverste højre hjørne af skærmen. Hvis du har filtreret listen på siden for forbedringshandlinger, kommer du til det næste element på den filtrerede liste ved at flytte op eller ned.

> [!TIP]
> Få mere at vide om de [forskellige typer af forbedringshandlinger, og hvordan der gives point](compliance-score-calculation.md#action-types-and-points) og tages i betragtning i dit overholdelsesresultat.

## <a name="assign-improvement-actions"></a>Tildel forbedringshandlinger

Du kan påbegynde implementeringen af en forbedringshandling ved at udføre arbejdet selv eller tildele det til en anden bruger. Den tildelte person kan være:

- Ejer af en forretningspolitik
- En it-implementerer
- En anden medarbejder med ansvar for at udføre opgaven

Når du har identificeret den relevante tildelt, skal du sikre dig, at denne har en tilstrækkelig [Overholdelsesstyring-rolle](compliance-manager-setup.md#set-user-permissions-and-assign-roles) til at udføre arbejdet. Følg derefter trinnene nedenfor for at tildele forbedringshandlingen:

1. På siden med oplysninger om forbedringshandlinger **skal du vælge Tildel** handling til venstre på skærmen.

2. Pop **op-ruden** Tildel til bruger viser **en liste over Foreslåede** personer over brugere. Du kan vælge brugeren på listen eller skrive mailadressen på den person, du vil tildele den til.

3. Vælg **Tildel**. Den tildelte bruger modtager en mail, der forklarer, at forbedringshandlingen er blevet tildelt brugeren med et direkte link til forbedringshandlingen.

> [!NOTE]
> Us Government Community-kunder (GCC) High og Department of Defense (DoD) modtager ikke en mail, når der tildeles forbedringshandlinger til dem.

Den tildelte bruger kan derefter udføre de anbefalede handlinger.

#### <a name="assign-multiple-improvement-actions-to-a-single-user"></a>Tildele flere forbedringshandlinger til en enkelt bruger

Du kan tildele flere forbedringshandlinger til én bruger ved at følge disse trin:

1. Gå til siden Forbedringshandlinger.
2. Vælg området til venstre for navnet på forbedringshandlingen. Der vises et rundt kontrolikon, der angiver, at du har valgt den pågældende handling. Markér alle de handlinger, du vil tildele.
3. Vælg linket **Tildel til** bruger øverst i tabellen forbedringshandlinger.
4. Der vises et pop op-vindue. Begynd at **skrive navnet** på den person, du vil tildele handlingerne til, i feltet Tildel til. Du kan også vælge forslag på listen over foreslåede personer.
5. Når du har **befolket feltet Tildel** til med navnet på den tildelende, skal du vælge **Tildel**.
6. Derefter får du vist siden forbedringshandlinger med den nye tildelte angivet for de handlinger, du lige har tildelt.

## <a name="change-implementation-details"></a>Oplysninger om ændring af implementering

Du kan registrere implementeringens status og dato for hver forbedringshandling og tilføje noter til intern reference. Disse felter kan redigeres af alle brugere med redigeringstilladelser, ikke kun af den tildelte person.

Hvis du vil redigere status for en forbedringshandling, skal **du vælge Rediger implementeringsoplysninger** på detaljesiden. Nedenfor finder du de tilgængelige felter og statusindstillinger:

- **Implementeringsstatus**
  - **Ikke implementeret**: Handling endnu ikke implementeret
  - **Implementeret**: handling implementeret
  - **Alternativ implementering**: Vælg denne indstilling, hvis du har brugt andre tredjepartsværktøjer eller har taget andre handlinger, der ikke er inkluderet i Microsoft-anbefalinger
  - **Planlagt**: Der er planlagt en handling til implementering
  - **Uden for omfanget**: Handling er ikke relevant for din organisation og bidrager ikke til din score
- **Implementeringsdato**: tilgængelig til at vælge, hvornår status for implementering er "implementeret" eller "alternativ implementering"
- **Implementeringsnoter**: tekstfelt til noter om din implementering.

Der er ingen tegnbegrænsning i notefelterne. Vi anbefaler, at du holder noter korte, så du nemt kan se og redigere dem fra siden med oplysninger om forbedringshandlinger.

Almindelige handlinger synkroniseres på tværs af grupper. Når to forskellige evalueringer i samme gruppe deler forbedringshandlinger, der administreres af dig, synkroniseres eventuelle opdateringer, du foretager i en handlings implementeringsoplysninger eller status automatisk med den samme handling i en anden vurdering i gruppen. Denne synkronisering giver dig mulighed for at implementere én forbedringshandling og opfylde flere krav på tværs af flere bestemmelser.

## <a name="change-test-status"></a>Skift teststatus

I sektionen **Test** kan du få vist teststatus for din forbedringshandling, testdatoen og eventuelle noter. Indholdet af disse felter kan ændres under Rediger **testdetaljer af** enhver bruger med redigeringstilladelser.

De tilgængelige felter er som følger:

- **Teststatus**: Kan vælges, når implementeringsstatus er "implementeret" eller "alternativ implementering". Indstillingerne omfatter:
  - **Ikke vurderet**: Handlingen er ikke blevet testet
  - **Godkendt**: implementeringen er blevet bekræftet af en vurder
  - **Ikke udført lav risiko**: test mislykkedes, lav risiko
  - **Mellemstor risiko mislykkedes**: test mislykkedes, mellemstor risiko
  - **Ikke udført høj risiko**: test mislykkedes, høj risiko
  - **Uden for omfanget**: Handlingen er uden for omfanget af vurderingen og bidrager ikke til din score
- **Testdato**: Skift mellem pop op-kalenderen for at vælge datoen
- **Test af** noter **og yderligere noter**: tekstfelter til noter til intern reference

### <a name="update-testing-source"></a>Opdater testkilde

Overholdelsesstyring giver dig mulighed for at teste forbedringshandlinger. I sektionen **Oversigt** for hver forbedringshandling har området  Testkilde en rullemenu, hvorfra du kan **vælge, hvordan** handlingen skal testes **: Manuel**, Automatisk og **Overordnet**. Få mere at vide om hver testmetode nedenfor.

#### <a name="manual-testing-source"></a>Manuel testkilde
Forbedringshandlinger, der er indstillet til manuel test, er handlinger, som du manuelt tester og implementerer. Du angiver den nødvendige implementering og teststatus og overfører alle beviser på **fanen** Dokumenter. For nogle handlinger er dette den eneste tilgængelige metode til test af forbedringshandlinger.

#### <a name="automatic-testing-source"></a>Automatisk testkilde
Hvis en implementeringshandling er berettiget til at blive testet automatisk af Overholdelsesstyring, får du vist **indstillingen Automatisk** til testkilde. Overholdelsesstyring registrerer signaler fra andre overholdelsesløsninger, du har konfigureret i dit Microsoft 365-miljø, samt andre supplerende handlinger, som Microsoft Secure Score også overvåger. Feltet **Testlogik** på fanen  Test viser, hvilken type politik eller konfiguration der kræves i en anden løsning, for at handlingen passerer og optjene point i din overholdelsesscore.

Når det signalerer, at en forbedringshandling er blevet implementeret, modtager du automatisk de point, der er berettiget til den pågældende handling, som tager højde for pointtal i alle relaterede kontrolelementer og bedømmelser. Få mere at vide om [, hvordan løbende vurdering påvirker din vurdering af overholdelse](compliance-score-calculation.md#how-compliance-manager-continuously-assesses-controls).

 Automatisk test er som standard aktiveret for alle berettigede forbedringshandlinger. Du kan justere disse indstillinger til automatisk at teste kun visse forbedringshandlinger, eller du kan deaktivere automatisk test for alle handlinger. Få mere at vide om, hvordan automatiserede test fungerer, og hvordan du kan justere dine indstillinger [under Konfigurer automatiserede test](compliance-manager-setup.md#manage-automated-testing-settings).

#### <a name="parent-testing-source"></a>Overordnet tester kilde

Når du vælger **Overordnet** som testkilde for en forbedringshandling, skal du vælge en anden handling, som din handling sammenkædes med. Din handling bliver i kraft til "underordnet" for den handling, du angiver som "overordnet". Når du angiver en overordnet for en forbedringshandling, er denne handling forbundet med implementeringen og testdetaljerne for den overordnede handling. Når status for den overordnede handling ændres, arver barnets status disse ændringer. Den underordnede handling accepterer også alle beviser på fanen Dokumenter, der tilhører den overordnede handling, hvilket kan tilsidesætte alle data, der tidligere fandtes i den underordnede handlings **Dokumenter**.

> [!NOTE]
> At have en testkilde **til overordnet** betyder ikke nødvendigvis, at handlingen testes automatisk af Overholdelsesstyring. Hvis den overordnede handlings testkilde f.eks. er **manuel, så** udføres den underordnede handling under statussen for overordnet handling, som er en manuel test og implementering af organisationen.

Hvis du vil konfigurere en overordnet testkilde, skal du følge trinnene nedenfor:

- Find sektionen Oversigt på siden med oplysninger om **forbedringshandling** .
- Under overskriften **Test** af kilde skal **du vælge** Overordnet i rullemenuen.
- Vælg **Tildel overordnet**.
- I pop **op-ruden** Tildel overordnet forbedringshandling skal du finde den forbedringshandling, du vil tildele som overordnet på listen, eller indtaste handlingens navn i søgelinjen øverst. Når du identificerer den tilsigtede handling, skal du markere afkrydsningsfeltet til venstre for handlingsnavnet, når du peger på det, og derefter vælge **Gem**.

Du vender tilbage til siden med oplysninger om din handling. Under **Testkilde** i sektionen **Oversigt er** den nye handling, du har angivet som overordnet, angivet under **Overordnet handling**.

## <a name="review-standards-and-regulations"></a>Gennemse standarder og bestemmelser

Sektionen **standarder og bestemmelser indeholder** en søgbar og filtreret liste over standarder og bestemmelser, der er knyttet til din forbedringshandling. Disse kan ses af det relevante **kontrolelement**, **kontrol-id'et**, **kontrolfamilien** og den **pågældende** regel.

## <a name="perform-work-and-store-documentation"></a>Udføre arbejds- og lagerdokumentation

Du kan uploade filer og noter, der er relateret til implementering, og teste arbejdet direkte i **sektionen** Dokumenter. Dette miljø er et sikkert, centraliseret lager, der kan hjælpe dig med at demonstrere tilfredshed med kontrolelementer for at overholde overholdelsesstandarder og -bestemmelser. Alle brugere med skrivebeskyttet adgang kan læse indhold i dette afsnit. Kun brugere med redigeringsrettigheder kan uploade og downloade filer.

#### <a name="uploaded-documents"></a>Overførte dokumenter

- Vælg **Administrer dokumenter for** at overføre alle relevante filer.
- Når pop op-ruden administrer dokumenter åbnes, **skal du vælge Tilføj** dokument og derefter vælge filen fra systemet. Accepterede filtyper:
  - Dokumenter (.doc, .xls, .ppt, .txt, .pdf)
  - Billeder (.jpg, .png)
  - Video (.mkv)
  - Komprimerede filer (.zip, .rar)
- Når filen er løst i ruden, skal du **vælge Luk**, som automatisk gemmer den vedhæftede fil. Derefter vises filen under Overførte **dokumenter**.
- Hvis du vil downloade eller slette dokumentet, **skal du vælge** Administrer dokumenter under listen over dokumenter. I pop op-ruden skal du vælge dokumentrækken for at fremhæve den og derefter **vælge Download** eller **Slet**.

## <a name="assign-improvement-action-to-assessor-for-completion"></a>Tildel forbedringshandling til vurder ved afslutning

Når du har fuldført arbejdet, udført test og uploadet beviser, er næste trin at tildele forbedringshandlingen til en taksator for validering. Bedømmeren validerer arbejdet og undersøger dokumentationen og vælger den relevante teststatus.

**Hvis teststatus er angivet til "Bestået"**: handlingen er fuldført, og de punkter, der er opnået, viser de maksimale punkter, der er opnået. Pointene tælles derefter med i dit overordnede overholdelsesresultat.

**Hvis teststatus er angivet til "** Mislykket": Handlingen opfylder ikke kravene, og bedømmeren kan tildele den tilbage til den relevante bruger for yderligere arbejde.

## <a name="accepting-updates-to-improvement-actions"></a>Accept af opdateringer til forbedringshandlinger

Når der findes en opdatering til en forbedringshandling, får du vist en meddelelse ud for dens navn. Du kan enten acceptere opdateringen eller udskyde den til et senere tidspunkt.

#### <a name="what-causes-an-update"></a>Årsagen til en opdatering

Der sker en opdatering, når der er ændringer i relation til pointdeling, automatisering eller omfang. Ændringer kan omfatte ny vejledning til forbedringshandlinger baseret på lovmæssige ændringer, eller de kan skyldes produktændringer. Kun de forbedringshandlinger, der administreres af din organisation, modtager opdateringsmeddelelser.

#### <a name="where-youll-see-assessment-update-notifications"></a>Hvor du får vist meddelelser om opdatering af bedømmelsesvurdering

Når en forbedringshandling opdateres, får du vist etiketten  Afventer opdatering ud for navnet på siden med forbedringshandlinger og på detaljesiden for dens relaterede vurderinger.

Gå til detaljesiden for forbedringshandlingen, og vælg knappen  Gennemse opdatering i det øverste banner for at gennemse detaljer om ændringerne og acceptere eller udskyde opdateringen.

#### <a name="review-update-to-accept-or-defer"></a>Gennemse opdateringen for at acceptere eller udsætte

Når du har **valgt Gennemse opdatering** på siden med oplysninger om forbedringshandling, vises en pop op-rude i højre side af skærmen. Pop op-ruden indeholder vigtige oplysninger om opdateringen, f.eks. de påvirkningte bedømmelser og ændringer af score og omfang.

Vælg **Acceptér opdatering** for at acceptere alle ændringerne i forbedringshandlingen. **Accepterede ændringer er permanente**.

> [!NOTE]
> Når du accepterer en opdatering af en handling, accepterer du også opdateringer til andre versioner eller forekomster af denne handling. Opdateringer bliver overført for alle lejere for at udføre tekniske handlinger og vil blive overført for hele gruppen for ikke-tekniske handlinger.

Hvis du vælger **Annuller**, anvendes opdateringen ikke på forbedringshandlingen. Du vil dog fortsat få vist meddelelsen **Afventer opdatering** , indtil du accepterer opdateringen.

**Derfor anbefaler vi, at du accepterer opdateringer**

Accept af opdateringer er med til at sikre, at du har den mest opdaterede vejledning til brug af løsninger og tager de relevante forbedringshandlinger, der kan hjælpe dig med at opfylde kravene i den certificering, du er i gang med.

**Derfor kan det være en ide at udskyde en opdatering**

Hvis du er midt i en vurdering, der omfatter forbedringshandlingen, kan det være en god ide at sikre, at du er færdig med at arbejde på den, før du accepterer opdateringen. Du kan udskyde opdateringen til et senere tidspunkt ved at vælge **Annuller** i pop op-ruden med gennemsynsopdateringen.

#### <a name="accept-all-updates-at-once"></a>Acceptér alle opdateringer på én gang

Hvis du har flere opdateringer og vil acceptere dem alle på én gang, skal du vælge linket **Acceptér** alle opdateringer øverst i tabellen med forbedringshandlinger. Der vises en pop op-rude med antallet af handlinger, der skal opdateres. Vælg knappen **Acceptér opdateringer** for at anvende alle opdateringer.

Bemærk, at når du vender tilbage til siden med forbedringshandlinger, vises der muligvis en meddelelse øverst på siden, hvor du bliver bedt om at opdatere siden, så opdateringerne kan fuldføres.

## <a name="set-up-alerts-for-improvement-action-changes"></a>Konfigurere påmindelser om ændringer i forbedringshandlingen

Du kan konfigurere påmindelser til at give dig besked straks, når visse ændringer i forbedringshandlinger sker, f.eks. en ændring i implementerings- eller teststatus eller en stigning eller et fald i score. Hvis du får hurtige beskeder om sådanne ændringer, kan det hjælpe dig med at holde dig på for sikre overholdelse af regler og standarder. Besøg [Overholdelsesstyringsbeskeder og beskedpolitikker](compliance-manager-alert-policies.md) for at få mere at vide om, hvordan du konfigurerer beskeder.

## <a name="export-a-report"></a>Eksportere en rapport

Vælg **Eksportér** i øverste venstre hjørne af skærmen for at downloade et Excel regneark, der indeholder alle dine forbedringshandlinger og filterkategorierne, der vises på siden med forbedringshandlinger.