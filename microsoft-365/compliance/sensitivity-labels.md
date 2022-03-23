---
title: Få mere at vide om følsomhedsmærkater
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Brug følsomhedsmærkater fra Microsoft Information Protection (MIP) til at klassificere og beskytte følsomt indhold.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: 1c7ec0f9411d767e588e391eb7eb94ec95a219fb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587526"
---
# <a name="learn-about-sensitivity-labels"></a>Få mere at vide om følsomhedsmærkater

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Hvis du leder efter oplysninger om følsomhedsmærkater, som du kan se i dine Office-apps, skal du se Anvend [følsomhedsmærkater](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) på dine filer og mail Office.
>
> Oplysningerne på denne side er til it-administratorer, der kan oprette og konfigurere disse etiketter.

Personer i organisationen samarbejder med andre både i og uden for organisationen for at få arbejdet udført. Det betyder, at indhold ikke længere bliver bag en firewall – det kan rejse overalt, på tværs af enheder, apps og tjenester. Og når den er på vej, skal den gøre det på en sikker og beskyttet måde, der opfylder din organisations forretnings- og overholdelsespolitikker.

Følsomhedsmærkater fra Microsoft Information Protection-løsningen lader dig klassificere og beskytte din organisations data, samtidig med at det sikrer, at brugernes produktivitet og deres evne til at samarbejde ikke bliver forhindret.

Eksempel, der viser tilgængelige følsomhedsmærkater Excel på **fanen** Hjem på båndet. I dette eksempel vises den anvendte etiket på statuslinjen:

![Følsomhedsmærkat på Excel båndet og statuslinjen.](../media/Sensitivity-label-in-Excel.png)

For at anvende følsomhedsmærkater skal brugerne være logget på med deres Microsoft 365 arbejds- eller skolekonto.

> [!NOTE]
> For lejere i den amerikanske stat understøttes følsomhedsmærkater for alle platforme.
>
> Hvis du bruger en samlet Azure Information Protection-klient til mærkning og scanner, skal du se Beskrivelsen [af Azure Information Protection Premium Government-tjenesten](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).

Du kan bruge følsomhedsmærkater til at:
  
- **Angiv beskyttelsesindstillinger, der omfatter kryptering og indholdsmærkning.** Du kan f.eks. anvende en "Fortroligt" etiket i et dokument eller en mail, og den pågældende etiket krypterer indholdet og anvender et "Fortroligt" vandmærke. Indholdsmærkning omfatter sidehoveder og sidefødder samt vandmærker, og kryptering kan også begrænse, hvilke handlinger autoriserede personer kan udføre på indholdet.

- **Beskyt indhold i Office-apps på tværs af forskellige platforme og enheder.** Understøttes af Word, Excel, PowerPoint og Outlook på Office-skrivebordsapps og Office på internettet. Understøttes på Windows, macOS, iOS og Android.

- **Beskyt indhold i tredjepartsapps og -tjenester ved hjælp** af Microsoft Defender til skyapps. Med Defender til skyapps kan du registrere, klassificere, mærke og beskytte indhold i tredjepartsapps og -tjenester, f.eks. SalesForce, Box eller DropBox, selvom tredjepartsappen eller -tjenesten ikke læser eller understøtter følsomhedsmærkater.

- **Beskyt beholdere**, der Teams, Microsoft 365 gruppe- og SharePoint websteder. Du kan f.eks. angive indstillinger for beskyttelse af personlige oplysninger, ekstern brugeradgang og ekstern deling og adgang fra enheder, der ikke er administrerede.

- **Udvid følsomhedsmærkater til Power BI**: Når du aktiverer denne funktion, kan du anvende og få vist navne i Power BI og beskytte data, når de gemmes uden for tjenesten.

- **Udvid følsomhedsmærkaterne** til aktiver i Azure-visningen: Når du aktiverer denne funktion, som i øjeblikket er i forhåndsvisning, kan du anvende dine følsomhedsmærkater på filer og skemalagte dataaktiver i Azure-visningen. De skemalagte dataaktiver omfatter SQL, Azure SQL, Azure Synapse, Azure Cosoms og AWS RDS.

- **Udvid følsomhedsmærkater til tredjepartsapps og -tjenester.** Ved hjælp Microsoft Information Protection SDK kan tredjepartsapps læse følsomhedsmærkater og anvende beskyttelsesindstillinger.

- **Klassificer indhold uden at bruge nogen beskyttelsesindstillinger.** Du kan også blot tildele en etiket som et resultat af klassificeringen af indholdet. Dette giver brugerne en visuel tilknytning af klassificering til organisationens navnenavne og kan bruge etiketterne til at generere forbrugsrapporter og se aktivitetsdata for dit følsomme indhold. Baseret på disse oplysninger kan du altid vælge at anvende beskyttelsesindstillinger senere.

I alle disse tilfælde kan følsomhedsmærkater i Microsoft 365 hjælpe dig med at tage de rigtige handlinger på det rigtige indhold. Med følsomhedsmærkater kan du klassificere data på tværs af din organisation og håndhæve beskyttelsesindstillinger baseret på denne klassificering.

Du kan finde flere oplysninger om disse og andre scenarier, der understøttes af følsomhedsmærkater, [under Almindelige scenarier for følsomhedsmærkater](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Der udvikles hele tiden nye funktioner, der understøtter følsomhedsmærkater, så du kan også finde det nyttigt at [referere til Microsoft 365 oversigten](https://aka.ms/MIPC/Roadmap).

## <a name="what-a-sensitivity-label-is"></a>Hvad en følsomhedsmærkat er

Når du tildeler et følsomhedsmærkat til indhold, er det ligesom et stempel, der anvendes og er:

- **Kan tilpasses.** Specifikt for din organisation og virksomhedens behov kan du oprette kategorier til forskellige niveauer af følsomt indhold i organisationen. Eksempelvis Personlig, Offentlig, Generel, Fortrolig og Meget fortrolig.

- **Ryd tekst.** Da et navn er gemt i klar tekst i metadataene for filer og mails, kan apps og tjenester fra tredjeparter læse den og derefter anvende deres egne beskyttende handlinger, hvis det er nødvendigt.

- **Fast.** Da navnet er gemt i metadata for filer og mails, vil navnet følge med indholdet, uanset hvor det gemmes eller gemmes. Den entydige etiketidentifikation danner basis for at anvende og gennemtvinge de politikker, du konfigurerer.

Når et følsomhedsmærkat vises af brugerne, vises det som et mærke på apps, de bruger, og den kan nemt integreres i deres eksisterende arbejdsprocesser.

Hvert element, der understøtter følsomhedsetiketter, kan have et enkelt følsomhedsmærkat anvendt på det. Dokumenter og mails kan have både et følsomhedsmærkat og et [opbevaringsmærkat](retention.md#retention-labels) anvendt på dem.

> [!div class="mx-imgBorder"]
> ![Følsomhedsmærkat anvendt på en mail.](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Dette kan følsomhedsmærkater gøre

Når et følsomhedsmærkat er anvendt på en mail eller et dokument, håndhæves alle konfigurerede beskyttelsesindstillinger for den pågældende etiket på indholdet. Du kan konfigurere et følsomhedsmærkat til at:

- **Kryptér** mails og dokumenter for at forhindre uautoriserede personer i at få adgang til disse data. Du kan desuden vælge, hvilke brugere eller grupper der har tilladelse til at udføre hvilke handlinger og i hvor lang tid. Du kan f.eks. vælge at give alle brugere i organisationen tilladelse til at redigere et dokument, mens en bestemt gruppe i en anden organisation kun kan se det. Alternativt kan du i stedet for administratordefinerede tilladelser give brugerne tilladelse til at tildele tilladelser til indholdet, når de anvender etiketten. 
    
    Du kan finde flere oplysninger **om krypteringsindstillingerne** , når du opretter eller redigerer en følsomhedsmærkat i Begræns adgang til [indhold ved hjælp af kryptering i følsomhedsmærkater](encryption-sensitivity-labels.md).

- **Markér indholdet, når** du bruger Office apps, ved at tilføje vandmærker, sidehoveder eller sidefødder i mails eller dokumenter, hvor etiketten er anvendt. Vandmærker kan anvendes på dokumenter, men ikke i mails. Eksempel på sidehoved og vandmærke:
    
    ![Vandmærke og sidehoved anvendt på dokument.](../media/Sensitivity-label-watermark-header.png)
    
    Dynamiske markeringer understøttes også ved hjælp af variabler. Indsæt f.eks. etiketnavnet eller dokumentnavnet i sidehovedet, sidefoden eller vandmærket. Du kan finde flere oplysninger [under Dynamiske markeringer med variabler](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    Har du brug for at kontrollere, hvornår der anvendes indholdsmærkning? Se [Når Office anvende indholdsmærkning og kryptering](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    Hvis du har skabeloner eller arbejdsprocesser, der er baseret på bestemte dokumenter, skal du teste disse dokumenter med det valgte indhold, før du gør etiketten tilgængelig for brugerne. Nogle begrænsninger for strenglængde, du skal være opmærksom på:
    
    Vandmærker er begrænset til 255 tegn. Sidehoveder og sidefødder er begrænset til 1024 tegn, undtagen Excel. Excel har en samlet grænse på 255 tegn for sidehoveder og sidefødder, men denne grænse omfatter tegn, der ikke er synlige, f.eks. formateringskoder. Hvis denne grænse er nået, vises den streng, du angiver, ikke i Excel.

- **Beskyt indhold i beholdere**, f.eks. websteder og grupper, når du aktiverer muligheden for at bruge følsomhedsmærkater sammen Microsoft Teams [, Microsoft 365 grupper og SharePoint websteder](sensitivity-labels-teams-groups-sites.md).
    
    Du kan ikke konfigurere beskyttelsesindstillinger for grupper og websteder, før du har aktiveret denne funktion. Denne etiketkonfiguration medfører ikke, at dokumenter eller mails automatisk mærkes, men i stedet beskytter etiketindstillingerne indhold ved at kontrollere adgangen til beholderen, hvor indhold kan gemmes. Disse indstillinger omfatter indstillinger for beskyttelse af personlige oplysninger, ekstern brugeradgang og ekstern deling og adgang fra enheder, der ikke er administrerede.

- **Anvend etiketten automatisk på filer og mails, eller anbefal en etiket.** Vælg, hvordan du vil identificere følsomme oplysninger, du vil have mærket, og etiketten kan anvendes automatisk, eller du kan bede brugerne om at anvende den etiket, du anbefaler. Hvis du anbefaler en etiket, vises den tekst, du vælger, i prompten. Eksempel:
    
    ![Spørg, om der skal tildeles en påkrævet etiket.](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Du kan finde flere oplysninger  om automatisk mærkning af filer og mailindstillinger, når du opretter eller redigerer en følsomhedsmærkat[](apply-sensitivity-label-automatically.md), under Anvend automatisk en følsomhedsmærkat på indhold til Office-apps og Mærkning i [Azure-visning](/azure/purview/create-sensitivity-label).

- **Angiv standardtypen for delingslink** til SharePoint websteder og individuelle dokumenter. For at forhindre overdeling af brugere skal du angive standardomfanget og [standardtilladelserne for](sensitivity-labels-default-sharing-link.md), hvornår brugere deler dokumenter SharePoint og OneDrive.

### <a name="label-scopes"></a>Navneomfang

Når du opretter en følsomhedsmærkat, bliver du bedt om at konfigurere etikettens omfang, som bestemmer to ting:
- Hvilke etiketindstillinger du kan konfigurere for den pågældende etiket
- Hvor etiketten vil være synlig for brugerne

Denne omfangskonfiguration giver dig mulighed for at få følsomhedsmærkater, der kun er til dokumenter og mails og ikke kan vælges til beholdere. Og på samme måde er følsomhedsetiketter, der kun er til beholdere og ikke kan vælges til dokumenter og mails. Du kan også vælge området for Azure Purview-aktiver:

![Indstillinger for omfang for følsomhedsmærkater.](../media/sensitivity-labels-scopes.png)

Som standard er **området filer & mails** altid markeret. De andre områder vælges som standard, når funktionerne er aktiveret for din lejer:

- **Grupper & websteder**: [Aktivér følsomhedsmærkater for beholdere og synkroniser etiketter](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Skemalagte dataaktiver**: [Navn giv dit indhold en automatisk mærkat i Azure-visning](/azure/purview/create-sensitivity-label)

Hvis du ændrer standardindstillingerne, så ikke alle områder markeres, får du vist den første side i konfigurationsindstillingerne for områder, du ikke har valgt, men du kan ikke konfigurere indstillingerne. Hvis f.eks. området for filer og mails ikke er markeret, kan du ikke vælge indstillingerne på den næste side:

![Utilgængelige indstillinger for følsomhedsmærkater.](../media/sensitivity-labels-unavailable-settings.png)

For disse sider, hvor indstillingerne ikke er tilgængelige, skal du vælge **Næste for** at fortsætte. Eller vælg **Tilbage for** at ændre navnets omfang.

### <a name="label-priority-order-matters"></a>Mærkatprioritet (rækkefølgen har betydning)

Når du opretter dine følsomhedsmærkater i Administration, vises de på **en liste på** fanen Følsomhed på **siden** Etiketter. På denne liste er rækkefølgen af etiketterne vigtig, fordi den afspejler deres prioritet. Du ønsker, at din mest restriktive følsomhedsmærkat, f.eks. Meget  fortrolig, vises nederst på listen, og at din mindst restriktive følsomhedsmærkat, f.eks. Offentlig, vises **øverst**.

Du kan kun anvende ét følsomhedsmærkat på et element, f.eks. et dokument, en mail eller en beholder. Hvis du angiver en indstilling, der kræver, at brugerne skal angive en begrundelse for at ændre en mærkat til en lavere klassificering, identificerer rækkefølgen af denne liste de lavere klassificeringer. Denne indstilling gælder dog ikke for undergrupper, der deler prioriteten af deres overordnede etiket.

Rækkefølgen af undermapper bruges dog [med automatisk](apply-sensitivity-label-automatically.md) mærkat. Når du konfigurerer mærkater til at blive anvendt automatisk eller som en anbefaling, kan flere matches resultere for mere end én mærkat. For at finde den etiket, der skal anvendes eller anbefales, bruges rækkefølgen af etiketter: Den sidste følsomme etiket markeres og derefter det sidste undernavn, hvis det er relevant.

![Mulighed for at oprette et undermærke.](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Undermærkater (grupperingsmærkater)

Med undermærkater kan du gruppere en eller flere mærkater under en overordnet mærkat, som en bruger ser i en Office-app. Under Fortroligekan din organisation f.eks. bruge flere forskellige mærkater til bestemte typer af den pågældende klassificering. I dette eksempel er det overordnede navn Fortroligt blot en tekstetiket uden beskyttelsesindstillinger, og fordi den har undergrupper, kan den ikke anvendes på indhold. I stedet skal brugerne vælge Fortroligt for at få vist undergrupperne, og derefter kan de vælge et underordnet navn, der skal gælde for indholdet.

Undermærkater er blot en måde at præsentere mærkater for brugere i logiske grupper på. Undermærkater arver ikke nogen indstillinger fra deres overordnede mærkat. Når du publicerer en undermærkat for en bruger, kan den pågældende bruger derefter anvende den pågældende undermærkat på indhold, men kan ikke kun anvende den overordnede mærkat.

Vælg ikke en overordnet etiket som standardetiket, eller konfigurer en overordnet etiket til at blive anvendt automatisk (eller anbefalet). Hvis du gør det, anvendes den overordnede etiket ikke på indholdet.

Eksempel på, hvordan undermapper vises for brugere:

![Grupperede undergrupper på båndet.](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Redigere eller slette et følsomhedsmærkat

Hvis du sletter et følsomhedsmærkat fra din Administration, fjernes mærkaten ikke automatisk fra indholdet, og eventuelle beskyttelsesindstillinger vil fortsat blive håndhævet på indhold, der havde den pågældende etiket anvendt.

Hvis du redigerer et følsomhedsmærkat, er versionen af den etiket, der blev anvendt på indholdet, hvad der håndhæves på indholdet.

## <a name="what-label-policies-can-do"></a>Hvilke etiketpolitikker kan gøre

Når du har oprettet dine følsomhedsmærkater, skal du publicere dem for at gøre dem tilgængelige for personer og tjenester i din organisation. Følsomhedsmærkaterne kan derefter anvendes på Office dokumenter og mails og andre elementer, der understøtter følsomhedsmærkater. 

I modsætning til opbevaringsmærkater, der publiceres på placeringer som f.eks Exchange alle postkasser, publiceres følsomhedsmærkater til brugere eller grupper. Apps, der understøtter følsomhedsmærkater, kan derefter vise dem til disse brugere og grupper som etiketter eller som etiketter, de kan anvende.

Når du konfigurerer en etiketpolitik, kan du:

- **Vælg, hvilke brugere og grupper der skal kunne se etiketterne.** Etiketter kan publiceres til en bestemt bruger eller mailaktiveret sikkerhedsgruppe, distributionsgruppe eller Microsoft 365 gruppe (som kan have [dynamisk medlemskab](/azure/active-directory/users-groups-roles/groups-create-rule)) i Azure AD.

- **Angiv et standardnavn** til ikke-navnerede dokumenter og mails, nye beholdere (når du har aktiveret følsomhedsetiketter [for Microsoft Teams-, Microsoft 365-grupper og SharePoint-websteder](sensitivity-labels-teams-groups-sites.md), og nu en standardmærkat til [Power BI indhold](/power-bi/admin/service-security-sensitivity-label-default-label-policy). Du kan angive den samme etiket for alle fire typer elementer eller forskellige navne. Brugere kan ændre den anvendte standard-følsomhedsmærkat, så den passer bedre til følsomheden af deres indhold eller beholder.
    
    > [!NOTE]
    > I forhåndsvisning Office apps, der bruger indbyggede etiketter: Denne indstilling understøtter nu eksisterende dokumenter, når de åbnes af brugere samt nye dokumenter. Denne ændring giver paritet med den samlede Azure Information Protection-etiketklient. Du kan finde flere oplysninger om udrulning pr. app og minimumsversioner i tabellen med [egenskaber for Word](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint), Excel og PowerPoint.
    
    Overvej at bruge en standardetiket til at angive et grundlæggende niveau af beskyttelse, der skal anvendes på alt dit indhold. Men uden brugerkurser og andre kontrolelementer kan denne indstilling også medføre unøjagtige etiketter. Det er normalt ikke en god ide at vælge en etiket, der anvender kryptering som standardetiket til dokumenter. Mange organisationer har f.eks. brug for at sende og dele dokumenter med eksterne brugere, som muligvis ikke har apps, der understøtter krypteringen, eller de bruger muligvis ikke en konto, der kan godkendes. Du kan finde flere oplysninger om dette scenarie [under Dele krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
    
    > [!IMPORTANT]
    > Når du har [undergrupper, skal](#sublabels-grouping-labels) du være forsigtig med at konfigurere den overordnede etiket som en standardetiket.

- **Kræve en begrundelse for at ændre en etiket.** Hvis en bruger forsøger at fjerne en etiket eller erstatte den med en etiket, der har et lavere ordrenummer, kan du kræve, at brugeren angiver en begrundelse for at udføre denne handling. En bruger åbner f.eks. et dokument med navnet Fortroligt (ordre nr. 3) og erstatter denne etiket med en navngivet Offentlig (ordrenummer 1). For Office apps udløses denne begrundelsesprompt én gang pr. appsession, når du bruger indbygget mærkning og pr. fil, når du bruger den samlede Azure Information Protection-etiketklient. Administratorer kan læse begrundelsesårsagen sammen med navneændringen i [Aktivitetsstifinder](data-classification-activity-explorer.md).

    ![Spørg, hvor brugerne skal angive en begrundelse.](../media/Sensitivity-label-justification-required.png)

- **Kræv, at brugerne skal anvende** en etiket til dokumenter og mails, kun dokumenter, til beholdere og Power BI indhold. Disse indstillinger er også kendt som obligatorisk mærkning og sikrer, at der skal anvendes en etiket, før brugerne kan gemme dokumenter og sende mails, oprette nye grupper eller websteder, og når de bruger indhold uden navn til Power BI.
    
    For dokumenter og mails kan en etiket tildeles manuelt af brugeren, automatisk på grund af en betingelse, du konfigurerer, eller tildeles som standard (standardetiketindstillingen tidligere beskrevet). En eksempelprompt, når en bruger skal tildele en etiket:

    ![Spørg i Outlook, om brugeren skal anvende den påkrævede etiket.](../media/sensitivity-labels-mandatory-prompt-outlook.png)
    
    Du kan finde flere oplysninger om obligatorisk mærkning af dokumenter og mails i [Kræv, at brugerne anvender en etiket i deres mail og dokumenter](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    For beholdere skal der tildeles en etiket på det tidspunkt, hvor gruppen eller webstedet oprettes.
    
    Du kan finde flere oplysninger om obligatorisk mærkning til Power BI i [Obligatorisk etiketpolitik for Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).
    
    Overvej at bruge denne indstilling til at øge din dækning af mærkningen. Men uden brugerkurser kan disse indstillinger medføre unøjagtige etiketter. Medmindre du også angiver en tilsvarende standardmærkat, kan obligatorisk mærkning frustrere dine brugere med de hyppige prompter.

- **Give hjælp-link til en brugerdefineret side i Hjælp.** Hvis brugerne ikke er sikre på, hvad dine følsomhedsmærkater betyder, eller hvordan de skal bruges, kan du angive en Få mere at vide URL-adresse,  der vises nederst i menuen følsomhedsetiketter i Office apps:

    ![Få mere at vide om linket på knappen Følsomhed på båndet.](../media/Sensitivity-label-learn-more.png)

Når du har oprettet en etiketpolitik, der tildeler nye følsomhedsmærkater til brugere og grupper, begynder brugerne at se disse etiketter i deres Office apps. Det kan tage op til 24 timer, før de seneste ændringer replikeres i hele organisationen.

Der er ingen begrænsninger for antallet af følsomhedsmærkater, som du kan oprette og publicere med én undtagelse: Hvis etiketten anvender kryptering, der angiver brugere og tilladelser, understøttes der maksimalt 500 etiketter med denne konfiguration. Men som en bedste fremgangsmåde til at sænke administrationsomkostninger og reducere kompleksiteten for dine brugere skal du prøve at holde antallet af navne på et minimum. Virkelige implementeringer har givet effektiviteten betydeligt reduceret, når brugere har mere end fem hovednavne eller mere end fem undernavne pr. hovednavn.

### <a name="label-policy-priority-order-matters"></a>Prioritet af navnepolitik (ordrespørgsmål)

Du gør dine følsomhedsmærkater tilgængelige for brugere ved at publicere dem i en følsomhedsmærkatpolitik, der  vises på en liste på fanen Følsomhedspolitikker på **siden Etiketpolitikker**. Ligesom følsomhedsetiketter (se Etiketprioritet (rækkefølge vigtig [))](#label-priority-order-matters) er rækkefølgen af politikkerne for følsomhedsetiketter vigtig, fordi den afspejler deres prioritet. Etiketpolitikken med laveste prioritet **vises øverst,** og etiketpolitikken med højeste prioritet vises **nederst**.

En etiketpolitik består af:

- Et sæt etiketter.
- De brugere og grupper, der får tildelt politikken, med etiketter.
- Omfanget af politikken og politikindstillingerne for det pågældende område (f.eks. standardnavn for filer og mails).

Du kan medtage en bruger i flere etiketpolitikker, og brugeren får alle følsomhedsmærkater og indstillinger fra disse politikker. Hvis der er en konflikt mellem indstillinger fra flere politikker, anvendes indstillingerne fra politikken med højeste prioritet (laveste placering). Med andre ord vinder højeste prioritet for hver indstilling.

Hvis du ikke kan se funktionsmåden for politikindstillingen for etiketter eller etiketter, som du forventer for en bruger eller gruppe, skal du kontrollere rækkefølgen af politikkerne for følsomhedsmærkater. Du skal muligvis flytte politikken ned. Hvis du vil ændre rækkefølgen af etiketpolitikker, skal du vælge en følsomhedsmærkatpolitik > vælge ellipsen i højre side > **Flyt ned** **eller Flyt op**.

![Indstillingen Flyt på siden for politikker for følsomhedsmærkater.](../media/sensitivity-label-policy-priority.png)

> [!NOTE]
> Husk: Når der opstår en konflikt mellem indstillingerne for en bruger, der har fået tildelt flere politikker, anvendes indstillingen fra politikken med højeste prioritet (laveste placering).

## <a name="sensitivity-labels-and-azure-information-protection"></a>Følsomhedsmærkater og Azure Information Protection

Følsomhedsmærkaterne, der er indbygget i Microsoft 365 Apps på Windows, macOS, iOS og Android, ser ud og fungerer på samme måde på tværs af disse enheder for at give brugerne en ensartet etiketoplevelse. Men på Windows computere kan du også bruge [Azure Information Protection-klienten (AIP](/azure/information-protection/rms-client/aip-clientv2)). Denne klient er nu i [vedligeholdelsestilstand](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613).

Hvis du bruger AIP-klienten, skal du se Hvorfor vælge Indbygget [MIP-mærkning over AIP-tilføjelsesprogrammet til Office-apps for](sensitivity-labels-aip.md) at forstå og administrere dine valg af mærkning for Windows computere.

### <a name="azure-information-protection-labels"></a>Azure Information Protection-etiketter

> [!NOTE]
> Navneadministration for Azure Information Protection-etiketter i Azure-portalen blev frarådet **den 31. marts 2021**. Få mere at vide fra [den officielle meddelelse om udrådning](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179).

Hvis din lejer endnu ikke er på den samlede [etiketplatform, skal](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform) du først aktivere samlet mærkning, før du kan bruge følsomhedsmærkater. Du kan finde en vejledning [i Sådan overfører du Azure Information Protection-etiketter til samlede følsomhedsmærkater](/azure/information-protection/configure-policy-migrate-labels).

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Følsomhedsmærkater og Microsoft Information Protection SDK

Da et følsomhedsmærkat er gemt i metadataene i et dokument, kan tredjepartsapps og -tjenester læse fra og skrive til denne mærkning af metadata som et supplement til din installation af etiketter. Desuden kan softwareudviklere bruge SDK til [Microsoft Information Protection fuldt](/information-protection/develop/overview#microsoft-information-protection-sdk) ud understøtte mærknings- og krypteringsfunktioner på tværs af flere platforme. Du kan få mere at vide i [meddelelsen Generelt tilgængelighed på Tech Community-bloggen](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

Du kan også få mere at [vide om partnerløsninger, der er integreret med Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657).

## <a name="deployment-guidance"></a>Installationsvejledning

Se Introduktion til følsomhedsmærkater for installationsplanlægning og vejledning, som omfatter licensoplysninger, tilladelser, implementeringsstrategi, en liste over understøttede scenarier og [slutbrugerdokumentation](get-started-with-sensitivity-labels.md).

Du kan få mere at vide om, hvordan du bruger følsomhedsmærkater til at overholde bestemmelser om beskyttelse af data ved at se Udrul beskyttelse af data for bestemmelser om beskyttelse af personlige oplysninger [Microsoft 365](../solutions/information-protection-deploy.md) (aka.ms/m365dataprivacy).
