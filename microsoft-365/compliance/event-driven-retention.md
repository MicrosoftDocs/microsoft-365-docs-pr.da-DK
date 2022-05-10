---
title: Start opbevaring, når der opstår en hændelse
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-may2020
- seo-marvel-jun2020
description: Som regel en del af en løsning til datastyring, kan du konfigurere en opbevaringsmærkat for at starte opbevaringsperioden baseret på en hændelse, som du identificerer.
ms.openlocfilehash: 65a3c2088974398abb6ddbeb205cfb66541629e2
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285100"
---
# <a name="start-retention-when-an-event-occurs"></a>Start opbevaring, når der opstår en hændelse

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du bevarer indhold, er opbevaringsperioden ofte baseret på indholdets alder. Du kan f.eks. bevare dokumenter i syv år, efter at de er oprettet, og derefter slette dem. Men når du konfigurerer [opbevaringsmærkater](retention.md#retention-labels), kan du også basere en opbevaringsperiode på, hvornår der opstår en bestemt type hændelse. Hændelsen udløser starten af opbevaringsperioden, og alt indhold med en opbevaringsmærkat, der er anvendt for den pågældende type hændelse, gennemtvinger mærkatens opbevaringshandlinger på dem.
  
Eksempler på brug af hændelsesbaseret opbevaring:
  
- **Medarbejdere, der forlader organisationen** Lad os antage, at medarbejderposter skal opbevares i 10 år fra det tidspunkt, hvor en medarbejder forlader organisationen. Efter 10 år skal alle dokumenter vedrørende ansættelse, præstation og opsigelse af den pågældende medarbejder bortskaffes. Hændelsen, der udløser opbevaringsperioden på 10 år, er den medarbejder, der forlader organisationen. 
    
- **Kontraktudløb** Lad os antage, at alle poster, der er relateret til kontrakter, skal opbevares i fem år fra det tidspunkt, hvor kontrakten udløber. Den hændelse, der udløser opbevaringsperioden på fem år, er kontraktens udløb. 
    
- **Produktlevetid** Din organisation kan have opbevaringskrav, der er relateret til den sidste produktionsdato for produkter for indhold, f.eks. tekniske specifikationer. I dette tilfælde er den sidste produktionsdato den hændelse, der udløser opbevaringsperioden. 
    
Hændelsesbaseret opbevaring bruges typisk som en del af en proces til datastyring. Det betyder, at:
  
- Opbevaringsmærkater, der er baseret på hændelser, markerer også normalt elementer som en post som en del af en løsning til datastyring. Du kan finde flere oplysninger under [Få mere at vide om datastyring](records-management.md).

- Et dokument, der er blevet erklæret som en post, men hvis hændelsesudløser endnu ikke er sket, bevares på ubestemt tid (poster kan ikke slettes permanent), før en hændelse udløser dokumentets opbevaringsperiode.
    
- Opbevaringsmærkater, der er baseret på hændelser, udløser normalt en dispositionsgennemgang i slutningen af opbevaringsperioden, så en dataadministrator manuelt kan gennemse og fjerne indholdet. Du kan få flere oplysninger under [Fordeling af indhold](disposition.md).
    

En opbevaringsmærkat, der er baseret på en hændelse, har de samme egenskaber som enhver opbevaringsmærkat i Microsoft 365. Du kan finde flere oplysninger under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Om relationen mellem hændelsestyper, mærkater, hændelser og aktiv-id'er

Hvis du vil bruge hændelsesbaseret opbevaring, er det vigtigt at forstå relationen mellem hændelsestyper, opbevaringsmærkater, hændelser og aktiv-id'er som vist i diagrammerne og følgende forklaring: 
  
![Diagram 1 af 2: Hændelsestype, mærkater, hændelser og aktiv-id'er.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![Diagram 2 af 2: Hændelsestype, mærkater, hændelser og aktiv-id'er.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. Du opretter opbevaringsmærkater for forskellige typer indhold og knytter dem derefter til en type hændelse. Opbevaringsmærkater for forskellige typer produktfiler og -poster er f.eks. knyttet til en hændelsestype med navnet Produktlevetid, fordi disse poster skal opbevares i 10 år, fra det tidspunkt, hvor produktet udløber.
    
2. Brugere (typisk dataadministratorer) anvender disse opbevaringsmærkater på indhold og (for dokumenter i SharePoint og OneDrive) angive et aktiv-id for hvert element. I dette eksempel er aktiv-id'et et produktnavn eller en produktkode, der bruges af organisationen. Derefter tildeles hvert produkts poster en opbevaringsmærkat, og hver post har en egenskab, der indeholder et aktiv-id. Diagrammet repræsenterer **alt indhold** for alle produktposter i en organisation, og hvert element indeholder aktiv-id'et for det produkt, hvis post det er. 
    
3. Produktlevetid er hændelsestypen. et bestemt produkt, der når ud af livet, er en begivenhed. Når der opstår en hændelse af den pågældende hændelsestype – i dette tilfælde, når et produkt når sin slutdato – opretter du en hændelse, der angiver:
    
   - Et aktiv-id (for SharePoint og OneDrive dokumenter)
    
   - Nøgleord (til Exchange elementer). I dette eksempel bruger organisationen en produktkode i meddelelser, der indeholder produktposter, så nøgleordet for Exchange elementer er funktionelt det samme som aktiv-id'et for SharePoint og OneDrive dokumenter.
    
   - Den dato, hvor hændelsen fandt sted. Denne dato bruges som starten på opbevaringsperioden. Denne dato kan være den aktuelle, en fortid eller en fremtidig dato.

4. Når du har oprettet en hændelse, synkroniseres denne hændelsesdato med alt det indhold, der har en opbevaringsmærkat af den pågældende hændelsestype, og som indeholder det angivne aktiv-id eller nøgleord. Som enhver opbevaringsmærkat kan denne synkronisering tage op til syv dage. I det forrige diagram udløses opbevaringsperioden for alle elementer med rødt af denne hændelse. Med andre ord, når dette produkt når sin levetid, udløser hændelsen opbevaringsperioden for det pågældende produkts poster.

Det er vigtigt at forstå, at hvis du ikke angiver et aktiv-id eller nøgleord for en hændelse, vil **alt indhold** med en opbevaringsmærkat for den pågældende hændelsestype få sin opbevaringsperiode udløst af hændelsen. Det betyder, at alt indhold bevares i det forrige diagram. Det er muligvis ikke, hvad du har tænkt dig.

Til sidst skal du huske, at hver opbevaringsmærkat har sine egne opbevaringsindstillinger. I dette eksempel angiver de alle 10 år, men det er muligt for en hændelse at udløse opbevaringsmærkater, hvor hver etiket har en anden opbevaringsperiode.
  
## <a name="how-to-set-up-event-driven-retention"></a>Sådan konfigurerer du hændelsesbaseret opbevaring

Arbejdsproces på højt niveau for hændelsesbaseret opbevaring:
  
![Diagram over arbejdsproces til konfiguration af hændelsesbaseret opbevaring.](../media/event-based-retention-process.png)
  
> [!TIP]
> Se [Brug opbevaringsmærkater til at administrere livscyklussen for dokumenter, der er gemt i SharePoint](auto-apply-retention-labels-scenario.md) for at få et detaljeret scenarie om brug af administrerede egenskaber i SharePoint til automatisk at anvende opbevaringsmærkater og implementere hændelsesbaseret opbevaring.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>Trin 1: Opret en mærkat, hvis opbevaringsperiode er baseret på en hændelse

Hvis du vil oprette og konfigurere din opbevaringsmærkat, skal du se instruktionerne for [Opret opbevaringsmærkater](file-plan-manager.md#create-retention-labels) til dataadministration eller [Sådan opretter du opbevaringsmærkater til administration af datalevetid](create-retention-labels-data-lifecycle-management.md). Men specifikt for hændelsesbaseret opbevaring skal du på siden **Definer opbevaringsindstillinger** , når du opretter opbevaringsmærkaten, efter **Start opbevaringsperioden baseret på** vælge en af standardhændelsestyperne på rullelisten eller oprette din egen ved at vælge **Opret ny hændelsestype**:

![Opret en ny hændelsestype for en opbevaringsmærkat.](../media/SPRetention6.png)

En hændelsestype er blot en generel beskrivelse af en hændelse, som du vil knytte til en opbevaringsmærkat.

Standardhændelsestyperne har **(hændelsestype)** efter deres navn på rullelisten for at gøre det nemmere at identificere dem, og du kan også se og oprette hændelsestype fra fanen **DatastyringHændelser** >  > **Administrer hændelsestyper**.

Hændelsesbaseret opbevaring kræver opbevaringsindstillinger, der:
  
- Bevar indholdet.
    
- Slet indholdet automatisk, eller udløs en dispositionsgennemgang i slutningen af opbevaringsperioden.
  
Hændelsesbaseret opbevaring bruges typisk til indhold, der er defineret som en post, så dette er et godt tidspunkt til at kontrollere, om du også skal vælge den indstilling, der markerer indhold som en [post](records-management.md#records).

Hvis du bruger en eksisterende hændelsestype i stedet for at oprette en ny hændelsestype, skal du gå til trin 3.

> [!NOTE]
> Når du har valgt en hændelsestype og gemt opbevaringsmærkaten, kan hændelsestypen ikke ændres.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>Trin 2: Opret en ny hændelsestype for dit navn

Hvis du har valgt **Opret ny hændelsestype** for opbevaringsindstillingerne, skal du angive et navn og en beskrivelse til hændelsestypen. Vælg derefter **Næste**, **Indsend** og **Udført**.

Tilbage på siden **Definer opbevaringsindstillinger** for **Start den opbevaringsperiode**, der er baseret på, skal du bruge rullelisten til at vælge den hændelsestype, du har oprettet.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>Trin 3: Publicer eller anvend automatisk de hændelsesbaserede opbevaringsmærkater

På samme måde som med enhver opbevaringsmærkat skal du publicere eller anvende en hændelsesbaseret mærkat automatisk, for at den kan anvendes manuelt eller automatisk på indhold:
- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>Trin 4: Angiv et aktiv-id

Når der anvendes en hændelsesbaseret mærkat på indhold, kan du angive et aktiv-id for hvert element. Din organisation kan f.eks. bruge:
  
- Produktkoder, som du kan bruge til kun at bevare indhold for et bestemt produkt.
    
- Project koder, som du kan bruge til kun at bevare indhold for et bestemt projekt.
    
- Medarbejder-id'er, som du kan bruge til kun at bevare indhold for en bestemt person.
    
Aktiv-id er blot en anden dokumentegenskab, der er tilgængelig i SharePoint og OneDrive. Din organisation bruger muligvis allerede andre dokumentegenskaber og id'er til at klassificere indhold. Hvis det er tilfældet, kan du også bruge disse egenskaber og værdier, når du opretter en hændelse – se trin 6, der følger efter. Det vigtige er, at du skal bruge en kombination af *egenskab:værdi* i dokumentegenskaberne for at knytte elementet til en hændelsestype.
  
![Tekstfelt til at angive et aktiv-id.](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>Trin 5: Opret en hændelse

Når der opstår en bestemt forekomst af den pågældende hændelsestype, f.eks. når et produkt udløber, skal du gå til siden **DatastyringHændelser** >  på Microsoft Purview-overholdelsesportalen og vælge **+ Opret** for at oprette en hændelse. Du udløser hændelsen ved at oprette den her.

![Opret en hændelse for at udløse start af opbevaring for hændelsesbaserede opbevaringsmærkater.](../media/create-event-records-management.png)

Der understøttes op til en million hændelser pr. lejer.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>Trin 6: Vælg den samme hændelsestype, der bruges af etiketten i trin 2

Når du opretter hændelsen, skal du vælge den samme hændelsestype, der er angivet i indstillingerne for opbevaringsmærkaten i trin 2. Hvis du f.eks. har valgt **Produktlevetid** som din hændelsestype for mærkatindstillingerne, skal du vælge **Produktlevetid** , når du opretter hændelsen. Det er kun indhold med opbevaringsmærkater, der er anvendt på den pågældende hændelsestype, der udløses.

![Mulighed i Hændelsesindstillinger for at vælge en hændelsestype.](../media/choose-event-type-records-management.png)

Hvis du har brug for at oprette en hændelse for flere opbevaringsmærkater, der har forskellige hændelsestyper, skal du vælge indstillingen **Vælg eksisterende navne** . Vælg derefter de mærkater, der er konfigureret for de hændelsestyper, du vil knytte til denne hændelse.

### <a name="step-7-enter-keywords-or-query-for-exchange-asset-id-for-sharepoint-and-onedrive"></a>Trin 7: Angiv nøgleord eller forespørgsler for Exchange, aktiv-id for SharePoint og OneDrive

Nu begrænser du omfanget af indholdet. For Exchange indhold gør du dette ved at angive nøgleord eller en forespørgsel. For SharePoint og OneDrive indhold gør du dette ved at angive aktiv-id'er.

Til Exchange elementer skal du bruge nøgleord eller en forespørgsel, der bruger KQL (Keyword Query Language). Du kan få flere oplysninger om forespørgselssyntaksen i [Reference til nøgleordsforespørgselssprog (KQL).](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference) Du kan finde flere oplysninger om de egenskaber, der kan søges efter, som du kan bruge til Exchange, under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

For aktiv-id'er gennemtvinges opbevaring kun for indhold med det angivne *egenskab:værdipar* . Hvis du f.eks. bruger egenskaben Aktiv-id, skal du angive `ComplianceAssetID:<value>` i feltet for aktiv-id'er, der vises på følgende billede.

Hvis der ikke angives et aktiv-id, anvendes den samme opbevaringsdato for alt indhold med mærkater af den pågældende hændelsestype.

Din organisation kan have anvendt andre egenskaber og id'er på de dokumenter, der er relateret til denne hændelsestype. Hvis du f.eks. har brug for at registrere et bestemt produkts poster, kan id'et være en kombination af din brugerdefinerede egenskab ProductID og værdien "XYZ". I dette tilfælde skal du angive `ProductID:XYZ` i feltet for aktiv-id'er, der vises på følgende billede.

Til sidst skal du vælge den dato, hvor hændelsen indtraf. denne dato bruges som begyndelsen af opbevaringsperioden. Når du har oprettet en hændelse, synkroniseres denne hændelsesdato med alt indholdet med en opbevaringsmærkat for den pågældende hændelsestype, aktiv-id og nøgleord eller forespørgsler. Som med enhver opbevaringsmærkat kan denne synkronisering tage op til syv dage.
  
![Siden Med hændelsesindstillinger.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

Når du har oprettet en hændelse, træder opbevaringsindstillingerne i kraft for det indhold, der allerede er mærket og indekseret. Hvis opbevaringsmærkaten føjes til nyt indhold, når hændelsen er oprettet, skal du oprette en ny hændelse med de samme oplysninger.

Sletning af en hændelse annullerer ikke de opbevaringsindstillinger, der nu er i kraft for det indhold, der allerede er mærket. I øjeblikket kan du ikke annullere hændelser, når de udløses.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Brug indholdssøgning til at finde alt indhold med et bestemt navn eller aktiv-id

Når opbevaringsmærkater er tildelt indhold, kan du bruge indholdssøgning til at finde alt indhold, der er klassificeret med en bestemt opbevaringsmærkat, eller som indeholder et bestemt aktiv-id:
  
- Hvis du vil finde alt indhold med en bestemt opbevaringsmærkat, skal du vælge betingelsen **Opbevaringsmærkat** og derefter angive det fulde navn eller en del af navnet og bruge et jokertegn. 
    
- Hvis du vil finde alt indhold med et bestemt aktiv-id, skal du angive egenskaben **ComplianceAssetID** og en værdi i formatet `ComplianceAssetID:<value>`. 
    
Du kan finde flere oplysninger under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>Automatiser hændelser ved hjælp af PowerShell

Du kan bruge et PowerShell-script til at automatisere hændelsesbaseret opbevaring fra dine virksomhedsprogrammer. De PowerShell-cmdlet'er, der er tilgængelige til hændelsesbaseret opbevaring:
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

## <a name="automate-events-by-using-a-rest-api"></a>Automatiser hændelser ved hjælp af en REST API

Du kan bruge en REST API til automatisk at oprette de hændelser, der udløser starten af opbevaringstiden.

En REST API er et tjenesteslutpunkt, der understøtter sæt HTTP-handlinger (metoder), som giver adgang til oprettelse/hentning/opdatering/sletning af tjenestens ressourcer. Du kan få flere oplysninger under [Komponenter i en REST API-anmodning/-svar](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). Ved hjælp af Microsoft 365 REST API kan hændelser oprettes og hentes ved hjælp af metoderne POST og GET.

Der er to muligheder for at bruge REST-API'en:

- **Microsoft Power Automate eller et lignende program** til automatisk at udløse forekomsten af en hændelse. Microsoft Power Automate er en orchestrator til oprettelse af forbindelse til andre systemer, så du behøver ikke at skrive en brugerdefineret løsning. Du kan få flere oplysninger på [Power Automate websted](https://flow.microsoft.com/en-us/).

- **PowerShell eller en HTTP-klient til at kalde REST-API'en** for at oprette hændelser ved hjælp af PowerShell (version 6 eller nyere), som er en del af en brugerdefineret løsning.

Før du bruger REST-API'en som global administrator, skal du bekræfte den URL-adresse, der skal bruges til opkaldet til opbevaringshændelsen. Det gør du ved at køre et get-opbevaringshændelseskald ved hjælp af URL-adressen til REST-API'en:

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

Kontrollér svarkoden. Hvis det er 302, skal du hente den omdirigerede URL-adresse fra egenskaben Location for svarheaderen og bruge denne URL-adresse i stedet for `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` i de efterfølgende instruktioner.

De hændelser, der oprettes automatisk, kan bekræftes ved at få dem vist på Microsoft Purview-overholdelsesportalen > **DataadministrationHændelser** >  .

### <a name="use-microsoft-power-automate-to-create-the-event"></a>Brug Microsoft Power Automate til at oprette hændelsen

Opret et flow, der opretter en hændelse ved hjælp af REST API'en Microsoft 365:

![Brug Flow til at oprette en hændelse.](../media/automate-event-driven-retention-flow-1.png)

![Brug af flow til at kalde REST-API'en.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>Opret en hændelse

Eksempelkode, der kalder REST-API'en:

- **Metode**: POST
- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Headere**: Key = Content-Type, Value = application/atom+xml
- **Brødtekst**:

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'?>
    
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'
    
    xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'
    
    xmlns='http://www.w3.org/2005/Atom'>
    
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />
    
    <updated>9/9/2017 10:50:00 PM</updated>
    
    <content type='application/xml'>
    
    <m:properties>
    
    <d:Name>Employee Termination </d:Name>
    
    <d:EventType>99e0ae64-a4b8-40bb-82ed-645895610f56</d:EventType>
    
    <d:SharePointAssetIdQuery>1234</d:SharePointAssetIdQuery>
    
    <d:EventDateTime>2018-12-01T00:00:00Z </d:EventDateTime>
    
    </m:properties>
    
    </content>
    
    </entry>
    ```

- **Godkendelse**: Grundlæggende
- **Brugernavn**: "Complianceuser"
- **Adgangskode**: "Overholdelsesadgangskode"


##### <a name="available-parameters"></a>Tilgængelige parametre


|Parametre|Beskrivelse|Bemærkninger|
|--- |--- |--- |
|<d:Name></d:Name>|Angiv et entydigt navn til hændelsen,|Må ikke indeholde efterstillede mellemrum eller følgende tegn: % * \ & < \> \| # ? , : ;|
|<d:EventType></d:EventType>|Angiv navnet på hændelsestypen (eller GUID)|Eksempel: "Medarbejders opsigelse". Hændelsestypen skal knyttes til en opbevaringsmærkat.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|Angiv "ComplianceAssetId:" + medarbejder-id|Eksempel: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|Dato og klokkeslæt for begivenhed|Format: yyyyy-MM-ddTHH:mm:ssZ, eksempel: 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse       |
| ----------------- | --------------------- |
| 302               | Omdirigere              |
| 201               | Lavet               |
| 403               | Autorisationen mislykkedes  |
| 401               | Godkendelse mislykkedes |

##### <a name="get-events-based-on-a-time-range"></a>Hent hændelser baseret på et tidsinterval

- **Metode**: GET

- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **Headere**: Key = Content-Type, Value = application/atom+xml

- **Godkendelse**: Grundlæggende

- **Brugernavn**: "Complianceuser"

- **Adgangskode**: "Overholdelsesadgangskode"

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse                   |
| ----------------- | --------------------------------- |
| 200               | OK, En liste over hændelser i atom+ xml |
| 404               | Ikke fundet                         |
| 302               | Omdirigere                          |
| 401               | Autorisationen mislykkedes              |
| 403               | Godkendelse mislykkedes             |

##### <a name="get-an-event-by-id"></a>Hent en hændelse efter id

- **Metode**: GET

- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **Headere**: Key = Content-Type, Value = application/atom+xml

- **Godkendelse**: Grundlæggende

- **Brugernavn**: "Complianceuser"

- **Adgangskode**: "Overholdelsesadgangskode"

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, svarteksten indeholder hændelsen i atom+xml |
| 404               | Ikke fundet                                            |
| 302               | Omdirigere                                             |
| 401               | Autorisationen mislykkedes                                 |
| 403               | Godkendelse mislykkedes                                |

##### <a name="get-an-event-by-name"></a>Hent en hændelse efter navn

- **Metode**: GET

- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **Headere**: Key = Content-Type, Value = application/atom+xml

- **Godkendelse**: Grundlæggende

- **Brugernavn**: "Complianceuser"

- **Adgangskode**: "Overholdelsesadgangskode"

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, svarteksten indeholder hændelsen i atom+xml |
| 404               | Ikke fundet                                            |
| 302               | Omdirigere                                             |
| 401               | Autorisationen mislykkedes                                 |
| 403               | Godkendelse mislykkedes                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>Brug PowerShell eller en HTTP-klient til at oprette hændelsen

PowerShell skal være version 6 eller nyere.

Kør følgende script i en PowerShell-session:

```powershell
param([string]$baseUri)

$userName = "UserName"

$password = "Password"

$securePassword = ConvertTo-SecureString $password -AsPlainText -Force

$credentials = New-Object System.Management.Automation.PSCredential($userName, $securePassword)

$EventName="EventByRESTPost-$(([Guid]::NewGuid()).ToString('N'))"

Write-Host "Start to create an event with name: $EventName"

$body = "<?xml version='1.0' encoding='utf-8' standalone='yes'?>

<entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices'

xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata'

xmlns='http://www.w3.org/2005/Atom'>

<category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent' />

<updated>7/14/2017 2:03:36 PM</updated>

<content type='application/xml'>

<m:properties>

<d:Name>$EventName</d:Name>

<d:EventType>e823b782-9a07-4e30-8091-034fc01f9347</d:EventType>

<d:SharePointAssetIdQuery>'ComplianceAssetId:123'</d:SharePointAssetIdQuery>

</m:properties>

</content>

</entry>"

$event = $null

try

{

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri "$baseUri/ComplianceRetentionEvent" -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

catch

{

$response = $_.Exception.Response

if($response.StatusCode -eq "Redirect")

{

$url = $response.Headers.Location

Write-Host "redirected to $url"

$event = Invoke-RestMethod -Body $body -Method 'POST' -Uri $url -ContentType "application/atom+xml" -Authentication Basic -Credential $credentials -MaximumRedirection 0

}

}

$event | fl *
```
