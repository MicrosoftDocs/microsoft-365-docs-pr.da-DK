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
description: Brug følsomhedsmærkater fra Microsoft Purview Information Protection til at klassificere og beskytte følsomt indhold.
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.openlocfilehash: f06b4a2f40987481c3870ee512e60497f57d851a
ms.sourcegitcommit: ebaa70d0da4a600efe52b5008eaddb511d36df8c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66687800"
---
# <a name="learn-about-sensitivity-labels"></a>Få mere at vide om følsomhedsmærkater

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Hvis du leder efter oplysninger om følsomhedsmærkater, som du kan se i dine Office-apps, skal du se [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).
>
> Oplysningerne på denne side er til it-administratorer, der kan oprette og konfigurere disse mærkater.

Personer i din organisation samarbejder med andre både i og uden for organisationen for at få deres arbejde fra hånden. Det betyder, at indhold ikke længere forbliver bag en firewall – det kan roame overalt på tværs af enheder, apps og tjenester. Og når den roamer, vil du gerne have, at den gør det på en sikker og beskyttet måde, der opfylder organisationens politikker for virksomhed og overholdelse af angivne standarder.

Følsomhedsmærkater fra Microsoft Purview Information Protection giver dig mulighed for at klassificere og beskytte din organisations data, samtidig med at du sikrer, at brugernes produktivitet og deres evne til at samarbejde ikke hindres.

Eksempel på visning af tilgængelige følsomhedsmærkater i Excel fra fanen **Hjem** på båndet. I dette eksempel vises den anvendte mærkat på statuslinjen:

![Følsomhedsmærkat på Excel-båndet og statuslinjen.](../media/Sensitivity-label-in-Excel.png)

Hvis brugerne skal anvende følsomhedsmærkater, skal de være logget på med deres Arbejds- eller skolekonto i Microsoft 365.

> [!NOTE]
> Følsomhedsmærkater understøttes for alle platforme for US Government-lejere.
>
> Hvis du bruger Azure Information Protection Unified-mærkatklient og -scanner, skal du se [beskrivelsen af Azure Information Protection Premium Government-tjenesten](/enterprise-mobility-security/solutions/ems-aip-premium-govt-service-description).

Du kan bruge følsomhedsmærkater til at:
  
- **Angiv beskyttelsesindstillinger, der omfatter kryptering og indholdsmarkeringer.** Du kan f.eks. anvende mærkaten "Fortroligt" på et dokument eller en mail, og mærkaten krypterer indholdet og anvender et vandmærke af typen "Fortroligt". Indholdsmarkeringer omfatter sidehoveder og sidefødder samt vandmærker, og kryptering kan også begrænse, hvilke handlinger godkendte personer kan udføre på indholdet.

- **Beskyt indhold i Office-apps på tværs af forskellige platforme og enheder.** Understøttes af Word, Excel, PowerPoint og Outlook i Office-skrivebordsapps og -Office på internettet. Understøttes på Windows, macOS, iOS og Android.

- **Beskyt indhold i tredjepartsapps og -tjenester** ved hjælp af Microsoft Defender for Cloud Apps. Med Defender for Cloud Apps kan du registrere, klassificere, navngive og beskytte indhold i tredjepartsapps og -tjenester, f.eks. SalesForce, Box eller DropBox, også selvom tredjepartsappen eller -tjenesten ikke læser eller understøtter følsomhedsmærkater.

- **Beskyt objektbeholdere**, der indeholder Teams-, Microsoft 365-grupper- og SharePoint-websteder. Du kan f.eks. angive indstillinger for beskyttelse af personlige oplysninger, ekstern brugeradgang og ekstern deling samt adgang fra ikke-administrerede enheder.

- **Udvid følsomhedsmærkater til Power BI**: Når du aktiverer denne funktion, kan du anvende og få vist mærkater i Power BI og beskytte data, når de gemmes uden for tjenesten.

- **Udvid følsomhedsmærkater til aktiver i Microsoft Purview-dataoversigt**: Når du aktiverer denne funktion, der i øjeblikket er en prøveversion, kan du anvende dine følsomhedsmærkater på filer og skematiserede dataaktiver i Microsoft Purview-dataoversigt. De skematiserede dataaktiver omfatter SQL, Azure SQL, Azure Synapse, Azure Cosmos og AWS RDS.

- **Udvid følsomhedsmærkater til tredjepartsapps og -tjenester.** Ved hjælp af Microsoft Information Protection SDK kan tredjepartsapps læse følsomhedsmærkater og anvende beskyttelsesindstillinger.

- **Klassificer indhold uden at bruge nogen beskyttelsesindstillinger.** Du kan også blot tildele en mærkat som følge af klassificeringen af indholdet. Dette giver brugerne en visuel tilknytning af klassificering til organisationens navne og kan bruge mærkaterne til at generere forbrugsrapporter og se aktivitetsdata for dit følsomme indhold. På baggrund af disse oplysninger kan du altid vælge at anvende beskyttelsesindstillinger senere.

I alle disse tilfælde kan følsomhedsmærkater fra Microsoft Purview hjælpe dig med at træffe de rigtige handlinger på det rigtige indhold. Med følsomhedsmærkater kan du klassificere data på tværs af din organisation og gennemtvinge beskyttelsesindstillinger baseret på denne klassificering. Denne beskyttelse forbliver derefter sammen med indholdet.

Du kan få flere oplysninger om disse og andre scenarier, der understøttes af følsomhedsmærkater, under [Almindelige scenarier for følsomhedsmærkater](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Der udvikles hele tiden nye funktioner, der understøtter følsomhedsmærkater, så det kan også være nyttigt at henvise til [Microsoft 365-køreplanen](https://aka.ms/MIPC/Roadmap).

## <a name="what-a-sensitivity-label-is"></a>Hvad en følsomhedsmærkat er

Når du tildeler et følsomhedsmærkat til indhold, er det som et stempel, der anvendes, og som er:

- **Tilpasselig.** Du kan oprette kategorier for forskellige niveauer af følsomt indhold i organisationen, der er specifikke for organisationens og virksomhedens behov. Det kan f.eks. være Personlig, Offentlig, Generelt, Fortroligt og Meget fortroligt.

- **Ryd tekst.** Da en mærkat er gemt i klartekst i metadataene for filer og mails, kan tredjepartsapps og -tjenester læse den og derefter anvende deres egne beskyttende handlinger, hvis det er nødvendigt.

- **Vedvarende.** Da mærkaten er gemt i metadata for filer og mails, forbliver etiketten sammen med indholdet, uanset hvor den gemmes eller gemmes. Det entydige mærkat-id bliver grundlaget for anvendelse og håndhævelse af politikker, som du konfigurerer.

Når brugerne i din organisation får vist en følsomhedsmærkat, vises den som et mærke for de apps, de bruger, og den kan nemt integreres i deres eksisterende arbejdsprocesser.

Hvert element, der understøtter følsomhedsmærkater, kan have en enkelt følsomhedsmærkat anvendt på det. Dokumenter og mails kan både have en følsomhedsmærkat og en [opbevaringsmærkat](retention.md#retention-labels) anvendt på dem.

> [!div class="mx-imgBorder"]
> ![Følsomhedsmærkat anvendt på en mail.](../media/Sensitivity-label-on-email.png)

## <a name="what-sensitivity-labels-can-do"></a>Hvad følsomhedsmærkater kan gøre

Når der er anvendt en følsomhedsmærkat på en mail eller et dokument, gennemtvinges eventuelle konfigurerede beskyttelsesindstillinger for den pågældende mærkat på indholdet. Du kan konfigurere en følsomhedsmærkat til:

- **Kryptér** mails og dokumenter for at forhindre uautoriserede personer i at få adgang til disse data. Du kan desuden vælge, hvilke brugere eller grupper der har tilladelse til at udføre hvilke handlinger og hvor længe. Du kan f.eks. vælge at tillade, at alle brugere i organisationen redigerer et dokument, mens en bestemt gruppe i en anden organisation kun kan se det. I stedet for administratordefinerede tilladelser kan du også give dine brugere tilladelse til at tildele tilladelser til indholdet, når de anvender mærkaten. 
    
    Du kan få flere oplysninger om **krypteringsindstillingerne** , når du opretter eller redigerer en følsomhedsmærkat, under [Begræns adgang til indhold ved hjælp af kryptering i følsomhedsmærkater](encryption-sensitivity-labels.md).

- **Markér indholdet** , når du bruger Office-apps, ved at føje vandmærker, sidehoveder eller sidefødder til mails eller dokumenter, hvor mærkaten er anvendt. Vandmærker kan anvendes på dokumenter, men ikke på mail. Eksempelheader og vandmærke:
    
    ![Vandmærke og sidehoved anvendt på dokumentet.](../media/Sensitivity-label-watermark-header.png)
    
    Dynamiske markeringer understøttes også ved hjælp af variabler. Indsæt f.eks. navnet eller dokumentnavnet i sidehovedet, sidefoden eller vandmærket. Du kan få flere oplysninger under [Dynamiske markeringer med variabler](sensitivity-labels-office-apps.md#dynamic-markings-with-variables).
    
    Skal det kontrolleres, hvornår der anvendes indholdsmarkeringer? Se [Når Office-apps anvender indholdsmarkering og kryptering](sensitivity-labels-office-apps.md#when-office-apps-apply-content-marking-and-encryption).
    
    Hvis du har skabeloner eller arbejdsprocesser, der er baseret på bestemte dokumenter, skal du teste disse dokumenter med dine valgte indholdsmarkeringer, før du gør mærkaten tilgængelig for brugerne. Nogle begrænsninger for strenglængde for at være opmærksom på:
    
    Vandmærker er begrænset til 255 tegn. Sidehoveder og sidefødder er begrænset til 1024 tegn, undtagen i Excel. Excel har en samlet grænse på 255 tegn for sidehoveder og sidefødder, men denne grænse omfatter tegn, der ikke er synlige, f.eks. formateringskoder. Hvis grænsen nås, vises den streng, du angiver, ikke i Excel.

- **Beskyt indhold i objektbeholdere, f.eks. websteder og grupper** , når du aktiverer funktionen til at [bruge følsomhedsmærkater med Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder](sensitivity-labels-teams-groups-sites.md).
    
    Du kan ikke konfigurere beskyttelsesindstillinger for grupper og websteder, før du aktiverer denne funktion. Denne etiketkonfiguration medfører ikke, at dokumenter eller mails automatisk navngives, men i stedet beskytter mærkatindstillingerne indhold ved at styre adgangen til objektbeholderen, hvor indhold kan gemmes. Disse indstillinger omfatter indstillinger for beskyttelse af personlige oplysninger, ekstern brugeradgang og ekstern deling og adgang fra ikke-administrerede enheder.

- **Anvend mærkaten automatisk på filer og mails, eller anbefal en etiket.** Vælg, hvordan følsomme oplysninger skal identificeres, og mærkaten kan anvendes automatisk, eller du kan bede brugerne om at anvende den mærkat, du anbefaler. Hvis du anbefaler en etiket, vises den tekst, du vælger, i prompten. Eksempel:
    
    ![Spørg, om der skal tildeles en påkrævet etiket.](../media/Sensitivity-label-Prompt-for-required-label.png)
    
    Du kan finde flere oplysninger om **automatisk mærkning af filer og mailindstillinger** , når du opretter eller redigerer en følsomhedsmærkat, under [Anvend en følsomhedsmærkat på indhold automatisk](apply-sensitivity-label-automatically.md) til Office-apps og [mærkning i Microsoft Purview-dataoversigt](/azure/purview/create-sensitivity-label).

- **Angiv standardlinktypen for deling** for SharePoint-websteder og individuelle dokumenter. Du kan forhindre brugere i at dele dem ved at angive [standardområdet og -tilladelserne](sensitivity-labels-default-sharing-link.md) for, når brugerne deler dokumenter fra SharePoint og OneDrive.

### <a name="label-scopes"></a>Navneområder

Når du opretter en følsomhedsmærkat, bliver du bedt om at konfigurere mærkatens omfang, som bestemmer to ting:
- Hvilke navneindstillinger du kan konfigurere for det pågældende navn
- Hvor mærkaten er synlig for brugerne

Med denne områdekonfiguration kan du have følsomhedsmærkater, der kun er til dokumenter og mails og ikke kan vælges for objektbeholdere. Og på samme måde er følsomhedsmærkater, der kun er beregnet til objektbeholdere og ikke kan vælges til dokumenter og mails. Du kan også vælge området for Microsoft Purview Data Map-aktiver:

![Områdeindstillinger for følsomhedsmærkater.](../media/sensitivity-labels-scopes.png)

Som standard er området **Elementer** (tidligere kaldet **Filer & mails**) altid valgt. De andre områder vælges som standard, når funktionerne er aktiveret for din lejer:

- **Grupper & websteder**: Se [Aktivér følsomhedsmærkater for objektbeholdere, og synkroniser mærkater](sensitivity-labels-teams-groups-sites.md#how-to-enable-sensitivity-labels-for-containers-and-synchronize-labels)

- **Skematiserede dataaktiver**: Se [Mærk automatisk dit indhold i Microsoft Purview-dataoversigt](/azure/purview/create-sensitivity-label)

Hvis du ændrer standardindstillingerne, så ikke alle områder er valgt, kan du se den første side i konfigurationsindstillingerne for områder, du ikke har valgt, men du kan ikke konfigurere indstillingerne. Hvis området for elementer f.eks. ikke er markeret, kan du ikke vælge indstillingerne på næste side:

![Indstillinger for følsomhedsmærkater er ikke tilgængelige.](../media/sensitivity-labels-unavailable-settings.png)

For de sider, der ikke har tilgængelige indstillinger, skal du vælge **Næste** for at fortsætte. Eller vælg **Tilbage** for at ændre navnets omfang.

### <a name="label-priority-order-matters"></a>Mærkatprioritet (rækkefølgen har betydning)

Når du opretter dine følsomhedsmærkater i Microsoft Purview Compliance Center, vises de på en liste under fanen **Følsomhed** på siden **Etiketter** . På denne liste er rækkefølgen af mærkater vigtig, fordi den afspejler deres prioritet. Din mest restriktive følsomhedsmærkat, f.eks. Meget fortroligt, skal vises **nederst** på listen, og din mindst restriktive følsomhedsmærkat, f.eks. Offentlig, skal vises **øverst**.

Du kan kun anvende én følsomhedsmærkat på et element, f.eks. et dokument, en mail eller en objektbeholder. Hvis du angiver en indstilling, der kræver, at brugerne skal angive en begrundelse for at ændre en mærkat til en lavere klassificering, identificerer rækkefølgen af denne liste de lavere klassificeringer. Denne indstilling gælder dog ikke for undermærkater, der deler prioriteten for deres overordnede mærkat.

Rækkefølgen af undermærkater bruges dog med [automatisk mærkning](apply-sensitivity-label-automatically.md). Når du konfigurerer mærkater til at blive anvendt automatisk eller som en anbefaling, kan flere matches resultere for mere end én mærkat. For at bestemme den etiket, der skal anvendes eller anbefales, bruges navnerækkefølgen: Den sidste følsomme mærkat vælges, og den sidste undermærkat, hvis det er relevant.

![Mulighed for at oprette en underabel.](../media/Sensitivity-label-sublabel-options.png)

### <a name="sublabels-grouping-labels"></a>Undermærkater (grupperingsmærkater)

Med undermærkater kan du gruppere en eller flere mærkater under en overordnet mærkat, som en bruger ser i en Office-app. Under Fortroligekan din organisation f.eks. bruge flere forskellige mærkater til bestemte typer af den pågældende klassificering. I dette eksempel er den overordnede mærkat Fortroligt blot en tekstmærkat uden beskyttelsesindstillinger, og fordi den har undermærkater, kan den ikke anvendes på indhold. Brugerne skal i stedet vælge Fortroligt for at få vist underlabels, og de kan derefter vælge et undermærke, der skal anvendes på indhold.

Undermærkater er blot en måde at præsentere mærkater for brugere i logiske grupper på. Undermærkater arver ikke nogen indstillinger fra deres overordnede mærkat. Når du publicerer en undermærkat for en bruger, kan den pågældende bruger derefter anvende den pågældende undermærkat på indhold, men kan ikke kun anvende den overordnede mærkat.

Vælg ikke en overordnet etiket som standardetiket, eller konfigurer en overordnet etiket, så den anvendes automatisk (eller anbefales). Hvis du gør det, anvendes den overordnede mærkat ikke på indhold.

Eksempel på, hvordan underlabels vises for brugere:

![Grupperede underlabels på båndet.](../media/Sensitivity-label-grouped-labels2.png)

### <a name="editing-or-deleting-a-sensitivity-label"></a>Redigering eller sletning af en følsomhedsmærkat

Hvis du sletter en følsomhedsmærkat fra administrationen, fjernes mærkaten ikke automatisk fra indholdet, og eventuelle beskyttelsesindstillinger gennemtvinges fortsat for indhold, hvor mærkaten er anvendt.

Hvis du redigerer en følsomhedsmærkat, er den version af mærkaten, der blev anvendt på indhold, det, der gennemtvinges for det pågældende indhold.

## <a name="what-label-policies-can-do"></a>Hvad kan mærkatpolitikker gøre?

Når du har oprettet dine følsomhedsmærkater, skal du publicere dem for at gøre dem tilgængelige for personer og tjenester i din organisation. Følsomhedsmærkater kan derefter anvendes på Office-dokumenter og -mails og andre elementer, der understøtter følsomhedsmærkater. 

I modsætning til opbevaringsmærkater, der publiceres på placeringer, f.eks. alle Exchange-postkasser, publiceres følsomhedsmærkater til brugere eller grupper. Apps, der understøtter følsomhedsmærkater, kan derefter vise dem til disse brugere og grupper som anvendte mærkater eller som mærkater, som de kan anvende.

Når du konfigurerer en mærkatpolitik, kan du:

- **Vælg, hvilke brugere og grupper der skal se mærkaterne.** Mærkater kan publiceres til en bestemt bruger eller mailaktiveret sikkerhedsgruppe, distributionsgruppe eller Microsoft 365-gruppe (som kan have [dynamisk medlemskab](/azure/active-directory/users-groups-roles/groups-create-rule)) i Azure AD.

- **Angiv en standardmærkat** for ikke-navngivne dokumenter og mails, nye objektbeholdere (når du har [aktiveret følsomhedsmærkater for Microsoft Teams, Microsoft 365-grupper og SharePoint-websteder](sensitivity-labels-teams-groups-sites.md)) og også et standardnavn til [Power BI-indhold](/power-bi/admin/service-security-sensitivity-label-default-label-policy). Du kan angive den samme etiket for alle fire elementtyper eller forskellige navne. Brugerne kan ændre den anvendte standardfølsomhedsmærkat, så den bedre matcher følsomheden af deres indhold eller objektbeholder.
    
    > [!NOTE]
    > Som prøveversion til Office-apps, der bruger indbyggede mærkater: Denne indstilling understøtter nu eksisterende dokumenter, når de åbnes af brugere, samt nye dokumenter. Denne ændring i funktionsmåden giver paritet med Azure Information Protection Unified-mærkatklienten. Du kan finde flere oplysninger om udrulningen pr. app og minimumversioner i [tabellen med funktioner](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) til Word, Excel og PowerPoint.
    
    Overvej at bruge et standardnavn til at angive et grundlæggende niveau af beskyttelsesindstillinger, som du vil anvende på alt dit indhold. Men uden brugertræning og andre kontrolelementer kan denne indstilling også resultere i unøjagtig mærkning. Det er normalt ikke en god idé at vælge en mærkat, der anvender kryptering som standardmærkat på dokumenter. Mange organisationer skal f.eks. sende og dele dokumenter med eksterne brugere, der muligvis ikke har apps, der understøtter krypteringen, eller de bruger muligvis ikke en konto, der kan godkendes. Du kan få flere oplysninger om dette scenarie under [Deling af krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
    
    > [!IMPORTANT]
    > Når du har [undermærkater](#sublabels-grouping-labels), skal du være forsigtig med ikke at konfigurere den overordnede etiket som en standardetiket.

- **Kræv en begrundelse for ændring af en etiket.** Hvis en bruger forsøger at fjerne en etiket eller erstatte den med en etiket, der har et lavere nummer, kan du kræve, at brugeren angiver en begrundelse for at udføre denne handling. En bruger åbner f.eks. et dokument med navnet Fortroligt (ordrenummer 3) og erstatter denne etiket med et med navnet Offentlig (ordrenummer 1). I forbindelse med Office-apps udløses denne begrundelsesprompt én gang pr. appsession, når du bruger indbygget mærkat og pr. fil, når du bruger Azure Information Protection Unified Labeling-klienten. Administratorer kan læse begrundelsesårsagen sammen med navneændringen i [aktivitetsoversigten](data-classification-activity-explorer.md).

    ![Spørg, hvor brugerne skal angive en begrundelse.](../media/Sensitivity-label-justification-required.png)

- **Kræv, at brugerne anvender en mærkat** for dokumenter og mails, kun dokumenter, for objektbeholdere og Power BI-indhold. Disse indstillinger, der også kaldes obligatorisk mærkning, sikrer, at der skal anvendes en mærkat, før brugerne kan gemme dokumenter og sende mails, oprette nye grupper eller websteder, og når de bruger ikke-navngivet indhold til Power BI.
    
    I forbindelse med dokumenter og mails kan en mærkat tildeles manuelt af brugeren automatisk som følge af en betingelse, som du konfigurerer, eller tildeles som standard (standardindstillingen for mærkat, der tidligere er beskrevet). En eksempelprompt, når en bruger skal tildele en mærkat:

    ![Spørg i Outlook, hvor brugeren bliver bedt om at anvende det påkrævede navn.](../media/sensitivity-labels-mandatory-prompt-outlook.png)
    
    Du kan finde flere oplysninger om obligatorisk mærkning af dokumenter og mails under [Kræv, at brugerne anvender en mærkat på deres mail og dokumenter](sensitivity-labels-office-apps.md#require-users-to-apply-a-label-to-their-email-and-documents).
    
    I forbindelse med objektbeholdere skal der tildeles en mærkat på det tidspunkt, hvor gruppen eller webstedet oprettes.
    
    Du kan finde flere oplysninger om obligatorisk mærkning til Power BI under [Obligatorisk mærkatpolitik for Power BI](/power-bi/admin/service-security-sensitivity-label-mandatory-label-policy).
    
    Overvej at bruge denne indstilling som en hjælp til at øge din mærkatdækning. Men uden brugertræning kan disse indstillinger resultere i unøjagtig mærkning. Medmindre du også angiver en tilsvarende standardmærkat, kan obligatorisk mærkning desuden frustrere dine brugere med de hyppige prompts.

- **Angiv et link til hjælp til en brugerdefineret hjælpside.** Hvis dine brugere ikke er sikre på, hvad dine følsomhedsmærkater betyder, eller hvordan de skal bruges, kan du angive en URL-adresse til Få mere at vide, der vises nederst i menuen **Følsomhedsmærkat** i Office-apps:

    ![Linket Få mere at vide om knappen Følsomhed på båndet.](../media/Sensitivity-label-learn-more.png)

Når du har oprettet en mærkatpolitik, der tildeler nye følsomhedsmærkater til brugere og grupper, begynder brugerne at se disse mærkater i deres Office-apps. Der kan gå op til 24 timer, før de seneste ændringer replikeres i hele organisationen.

Der er ingen grænse for, hvor mange følsomhedsmærkater du kan oprette og publicere, med én undtagelse: Hvis mærkaten anvender kryptering, der angiver brugerne og tilladelserne, understøttes der maksimalt 500 mærkater med denne konfiguration. Som bedste praksis for at reducere administrationsomkostningerne og reducere kompleksiteten for dine brugere kan du dog prøve at begrænse antallet af mærkater til et minimum. Udrulninger i den virkelige verden har vist sig at være mærkbart reducerede, når brugerne har mere end fem hovedmærkater eller mere end fem undermærkater pr. hovedmærkat.

### <a name="label-policy-priority-order-matters"></a>Prioritet for mærkatpolitik (order matters)

Du gør dine følsomhedsmærkater tilgængelige for brugere ved at publicere dem i en politik for følsomhedsmærkater, der vises på en liste under fanen **Følsomhedspolitikker** på siden **Mærkatpolitikker** . På samme måde som følsomhedsmærkater (se [Mærkatprioritet (order matters))](#label-priority-order-matters) er rækkefølgen af politikker for følsomhedsmærkater vigtig, fordi den afspejler deres prioritet. Etiketpolitikken med den laveste prioritet vises **øverst**, og mærkatpolitikken med den højeste prioritet vises **nederst**.

En mærkatpolitik består af:

- Et sæt mærkater.
- De brugere og grupper, der får tildelt politikken med mærkater.
- Omfanget af politik- og politikindstillingerne for det pågældende område (f.eks. standardmærkat for filer og mails).

Du kan inkludere en bruger i flere mærkatpolitikker, så får brugeren alle følsomhedsmærkater og -indstillinger fra disse politikker. Hvis der er en konflikt i indstillinger fra flere politikker, anvendes indstillingerne fra politikken med den højeste prioritet (laveste placering). Med andre ord vinder den højeste prioritet for hver indstilling.

Hvis du ikke kan se funktionsmåden for politikindstillingen for mærkater eller mærkater, som du forventer for en bruger eller gruppe, skal du kontrollere rækkefølgen af politikkerne for følsomhedsmærkater. Du skal muligvis flytte politikken ned. Hvis du vil ændre rækkefølgen af mærkatpolitikkerne, skal du vælge en politik for følsomhedsmærkater > vælge ellipsen til højre > **Flyt ned** eller **Flyt op**.

![Flyt indstillingen på siden for politikker for følsomhedsmærkater.](../media/sensitivity-label-policy-priority.png)

> [!NOTE]
> Husk: Når der er en konflikt mellem indstillinger for en bruger, der har flere politikker tildelt, anvendes indstillingen fra politikken med den højeste prioritet (laveste placering).

## <a name="sensitivity-labels-and-azure-information-protection"></a>Følsomhedsmærkater og Azure Information Protection

De følsomhedsmærkater, der er indbygget i Microsoft 365 Apps på Windows, macOS, iOS og Android, ser og fungerer på samme måde på tværs af disse enheder for at give brugerne en ensartet mærkatoplevelse. På Windows-computere kan du dog også bruge [Azure Information Protection-klienten (AIP).](/azure/information-protection/rms-client/aip-clientv2) Denne klient er nu i [vedligeholdelsestilstand](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/announcing-aip-unified-labeling-client-maintenance-mode-and/ba-p/3043613).

Hvis du bruger AIP-klienten, skal du se [Hvorfor vælge indbygget mærkat over AIP-tilføjelsesprogrammet til Office-apps for](sensitivity-labels-aip.md) at forstå og administrere dine valg af mærkater til Windows-computere.

### <a name="azure-information-protection-labels"></a>Azure Information Protection-mærkater

Label management for Azure Information Protection mærkater i Azure Portal frarådes **31. marts 2021**. Få mere at vide fra den officielle [meddelelse om udfasning](https://techcommunity.microsoft.com/t5/azure-information-protection/announcing-timelines-for-sunsetting-label-management-in-the/ba-p/1226179).

Hvis din lejer endnu ikke er på [unified labeling-platformen](/azure/information-protection/faqs#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform), skal du først aktivere unified labeling, før du kan bruge følsomhedsmærkater. Du kan finde instruktioner under [Sådan overfører du Azure Information Protection-mærkater til samlede følsomhedsmærkater](/azure/information-protection/configure-policy-migrate-labels).

## <a name="sensitivity-labels-and-the-microsoft-information-protection-sdk"></a>Følsomhedsmærkater og SDK'et for Microsoft Information Protection

Da en følsomhedsmærkat gemmes i metadataene for et dokument, kan tredjepartsapps og -tjenester læse fra og skrive til disse mærkatmetadata som supplement til installationen af mærkater. Derudover kan softwareudviklere bruge [Microsoft Information Protection SDK](/information-protection/develop/overview#microsoft-information-protection-sdk) til fuldt ud at understøtte mærkat- og krypteringsfunktioner på tværs af flere platforme. Du kan få mere at vide i [meddelelsen om generel tilgængelighed på tech community-bloggen](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Microsoft-Information-Protection-SDK-Now-Generally-Available/ba-p/263144). 

Du kan også få mere at vide om [partnerløsninger, der er integreret med Microsoft Purview Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Microsoft-Information-Protection-showcases-integrated-partner/ba-p/262657).

## <a name="deployment-guidance"></a>Installationsvejledning

Hvis du vil have planlægning af udrulning og vejledning, der indeholder licensoplysninger, tilladelser, udrulningsstrategi, en liste over understøttede scenarier og dokumentation til slutbrugere, skal [du se Kom i gang med følsomhedsmærkater](get-started-with-sensitivity-labels.md).

Hvis du vil vide mere om, hvordan du bruger følsomhedsmærkater til at overholde reglerne for beskyttelse af personlige oplysninger, skal du se [Installér bestemmelser om beskyttelse af personlige oplysninger med Microsoft 365](../solutions/information-protection-deploy.md).
