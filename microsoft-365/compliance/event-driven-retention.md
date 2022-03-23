---
title: Start opbevaring, når en hændelse forekommer
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
description: Typisk en del af en løsning til datastyring, kan du konfigurere en opbevaringsmærkat for at starte en opbevaringsperiode baseret på en hændelse, du identificerer.
ms.openlocfilehash: ad5fb2ef567525fa021acb0388ebc5cc98b1148c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589523"
---
# <a name="start-retention-when-an-event-occurs"></a>Start opbevaring, når en hændelse forekommer

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Når du bevarer indhold, er opbevaringsperioden ofte baseret på alderen på indholdet. Du kan f.eks. bevare dokumenter i syv år, efter de er oprettet, og derefter slette dem. Men når du [konfigurerer opbevaringsnavne](retention.md#retention-labels), kan du også basere en opbevaringsperiode på, hvornår en bestemt type hændelse forekommer. Hændelsen starter starten af opbevaringsperioden, og alt indhold med en opbevaringsetiket, der anvendes til den pågældende type hændelse, får etikettens opbevaringshandlinger gennemtvunget.
  
Eksempler på brug af hændelsesbaseret opbevaring:
  
- **Medarbejdere forlader organisationen** Antag, at medarbejderposter skal bevares i ti år fra det tidspunkt, hvor en medarbejder forlader organisationen. Når der er gået 10 år, skal alle dokumenter vedrørende ansættelse, ydeevne og opsigelse af den pågældende medarbejder bortkastes. Den hændelse, der udløser opbevaringsperioden på ti år, er medarbejderen, der forlader organisationen. 
    
- **Udløb af kontrakt** Antag, at alle poster vedrørende kontrakter skal bevares i fem år fra det tidspunkt, hvor kontrakten udløber. Den hændelse, der udløser opbevaringsperioden på fem år, er udløb af kontrakten. 
    
- **Produktlevetid** Din organisation har muligvis opbevaringskrav, der er relateret til den seneste produktionsdato for produkter til indhold som f.eks. tekniske specifikationer. I dette tilfælde er den sidste produktionsdato den hændelse, der udløser opbevaringsperioden. 
    
Hændelsesbaseret opbevaring bruges typisk som en del af en datastyringsproces. Det betyder, at:
  
- Opbevaringsnavne baseret på hændelser markerer normalt også elementer som en post som en del af en løsning til datastyring. Få mere at vide under [Få mere at vide om datastyring](records-management.md).

- Et dokument, der er erklæret en post, men hvis hændelsesudløser endnu ikke er sket, bevares på ubestemt tid (poster kan ikke slettes permanent), indtil en hændelse udløser det pågældende dokuments opbevaringsperiode.
    
- Opbevaringsnavne baseret på hændelser udløser normalt en gennemgang af dispositionen i slutningen af opbevaringsperioden, så en datastyring manuelt kan gennemse og bortkaste indholdet. Du kan finde flere oplysninger [under Disposition af indhold](disposition.md).
    

Et opbevaringsnavn, der er baseret på en begivenhed, har de samme egenskaber som enhver opbevaringsmærkat Microsoft 365. Få mere at vide under [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).

## <a name="understanding-the-relationship-between-event-types-labels-events-and-asset-ids"></a>Forstå relationen mellem hændelsestyper, etiketter, begivenheder og aktiv-id'er

For at kunne bruge begivenhedsbaseret opbevaring er det vigtigt at forstå relationen mellem hændelsestyper, opbevaringsmærkater, hændelser og aktiv-it'er, som vist i diagrammerne, og den forklaring, der følger: 
  
![Diagram 1 af 2: Begivenhedstype, etiketter, begivenheder og aktiv-id'er.](../media/a5141a6b-61ca-4a60-9ab0-24e6bb45bbdb.png)
  
![Diagram 2 af 2: Begivenhedstype, etiketter, begivenheder og aktiv-id'er.](../media/ce89a91f-49aa-4b5a-933c-ac3a13dccd5d.png)
  
1. Du kan oprette opbevaringsnavne for forskellige typer indhold og derefter knytte dem til en type hændelse. Opbevaringsnavne for forskellige typer produktfiler og -poster er f.eks. knyttet til en hændelsestype med navnet Produktlevetid, da disse poster skal bevares i 10 år fra det tidspunkt, hvor produktet når slutningen af sin levetid.
    
2. Brugere (typisk postadministratorer) anvender disse opbevaringsetiketter på indhold, og (for dokumenter i SharePoint og OneDrive) skal du angive et aktiv-id for hvert element. I dette eksempel er aktiv-id'et et produktnavn eller en kode, der bruges af organisationen. Derefter tildeles hvert produkts poster en opbevaringsmærkat, og hver post har en egenskab, der indeholder et aktiv-id. Diagrammet viser alt **indholdet for alle** produktposter i en organisation, og hvert element får aktiv-id'et for det produkt, hvis post er. 
    
3. Produktlevetid er begivenhedstypen; et bestemt produkt, der når slutningen af sin levetid, er en begivenhed. Når en hændelse af den pågældende hændelsestype forekommer – i dette tilfælde når et produkt når slutningen af sin levetid – opretter du en begivenhed, der angiver:
    
   - Et aktiv-id (for SharePoint og OneDrive dokumenter)
    
   - Nøgleord (for Exchange elementer). I dette eksempel bruger organisationen en produktkode i meddelelser, der indeholder produktposter, så nøgleordet for Exchange-elementer er funktionelt det samme som aktiv-id'et for SharePoint og OneDrive dokumenter.
    
   - Den dato, hvor hændelsen indtraf. Denne dato bruges som starten af en opbevaringsperiode. Denne dato kan være den aktuelle, en tidligere eller en fremtidig dato.

4. Når du har oprettet en begivenhed, synkroniseres den pågældende begivenhedsdato med alt det indhold, der har en opbevaringsetiket af den pågældende hændelsestype, og som indeholder det angivne aktiv-id eller nøgleord. Som enhver anden opbevaringsmærkat kan synkroniseringen tage op til syv dage. I det forrige diagram vises alle de elementer, der er omgivet af rød, med deres opbevaringsperiode udløst af denne hændelse. Med andre ord, når produktet når slutningen af sin levetid, udløser den pågældende hændelse opbevaringsperioden for det pågældende produkts poster.

Det er vigtigt at forstå, at hvis du ikke angiver et aktiv-id eller nøgleord for en **begivenhed, vil** alt indhold med en opbevaringsetiket for den pågældende hændelsestype have sin opbevaringsperiode udløst af begivenheden. Det betyder, at alt indhold i det forrige diagram begynder at blive bevaret. Dette er muligvis ikke det, du regner med.

Endelig skal du huske, at hver opbevaringsetiket har sine egne opbevaringsindstillinger. I dette eksempel angiver de alle 10 år, men en hændelse kan udløse opbevaringsetiketter, hvor hver etiket har en anden opbevaringsperiode.
  
## <a name="how-to-set-up-event-driven-retention"></a>Sådan konfigurerer du begivenhedsbaseret opbevaring

Arbejdsprocesser på højt niveau for hændelsesbaseret opbevaring:
  
![Diagram over arbejdsproces til konfiguration af begivenhedsbaseret opbevaring.](../media/event-based-retention-process.png)
  
> [!TIP]
> Se Brug opbevaringsnavne til at administrere livscyklussen for dokumenter, der er gemt i [SharePoint](auto-apply-retention-labels-scenario.md) for at få et detaljeret scenarie om brug af administrerede egenskaber i SharePoint til automatisk at anvende opbevaringsmærkater og implementere hændelsesbaseret opbevaring.

### <a name="step-1-create-a-label-whose-retention-period-is-based-on-an-event"></a>Trin 1: Opret et navn, hvis opbevaringsperiode er baseret på en begivenhed

Hvis du vil oprette og konfigurere din opbevaringsetiket, skal du se instruktionerne [til Oprette](file-plan-manager.md#create-retention-labels) opbevaringsnavne til datastyring eller Sådan oprettes opbevaringsnavne [til styring af oplysninger](create-retention-labels-information-governance.md). Men specifikt for begivenhedsbaseret opbevaring på siden **Definer** opbevaringsindstillinger, når du opretter opbevaringsmærkaten, skal du, når **du** har startet opbevaringsperioden baseret på, vælge en af standardhændelsestyperne på rullelisten eller oprette din egen ved at vælge **Opret ny begivenhedstype**:

![Opret en ny begivenhedstype for en opbevaringsetiket.](../media/SPRetention6.png)

En hændelsestype er blot en generel beskrivelse af en hændelse, du vil knytte til en opbevaringsetiket.

Standardhændelsestyperne har **(** hændelsestype) efter deres navn på rullelisten for at gøre det nemmere at identificere,  >  og du kan også se og oprette begivenhedstype fra fanen DatastyringHændelser > **Administrer** **hændelsestyper**.

Hændelsesbaseret opbevaring kræver opbevaringsindstillinger, som:
  
- Behold indholdet.
    
- Slet indholdet automatisk, eller udløs en gennemgang af dispositionen i slutningen af en opbevaringsperiode.
  
Hændelsesbaseret opbevaring bruges typisk til indhold, der erklæres som en post, så dette er et godt tidspunkt at kontrollere, om du også skal vælge den indstilling, der markerer indhold som en [post](records-management.md#records).

Hvis du bruger en eksisterende begivenhedstype i stedet for at oprette en ny begivenhedstype, skal du gå til trin 3.

> [!NOTE]
> Når du har valgt en hændelsestype og gemmer opbevaringsnavnet, kan hændelsestypen ikke ændres.

### <a name="step-2-create-a-new-event-type-for-your-label"></a>Trin 2: Opret en ny begivenhedstype for etiketten

Hvis du har valgt Opret ny hændelsestype for opbevaringsindstillingerne, **skal** du angive et navn og en beskrivelse af din hændelsestype. Vælg derefter **Næste**, **Send** og **Udført**.

Tilbage på siden **Definer opbevaringsindstillinger** skal du for **Start** opbevaringsperioden baseret på bruge rullelisten til at vælge den hændelsestype, du har oprettet.

  
### <a name="step-3-publish-or-auto-apply-the-event-based-retention-labels"></a>Trin 3: Udgive eller automatisk anvende de hændelsesbaserede opbevaringsnavne

Ligesom alle andre opbevaringsmærkater skal du publicere eller automatisk anvende et begivenhedsbaseret navn, så det anvendes manuelt eller automatisk på indhold:
- [Udgive opbevaringsmærkater og anvende dem i apps](create-apply-retention-labels.md)
- [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)

### <a name="step-4-enter-an-asset-id"></a>Trin 4: Angiv et aktiv-id

Når der anvendes en hændelsesbaseret etiket på indholdet, kan du angive et aktiv-id for hvert element. Din organisation kan f.eks. bruge:
  
- Produktkoder, du kan bruge til kun at bevare indhold for et bestemt produkt.
    
- Project koder, du kan bruge til kun at bevare indhold i et bestemt projekt.
    
- Medarbejder-id'er, som du kan bruge til kun at bevare indhold for en bestemt person.
    
Aktiv-id er blot en anden dokumentegenskab, der er tilgængelig SharePoint og OneDrive. Din organisation anvender måske allerede andre dokumentegenskaber og -oplysninger til at klassificere indhold. Hvis det er sådan, kan du også bruge disse egenskaber og værdier, når du opretter en begivenhed – se trin 6, der følger. Det vigtige punkt er, at du skal bruge en *kombination af egenskab:* værdi i dokumentegenskaberne for at knytte elementet til en hændelsestype.
  
![Tekstfelt til indtastning af et aktiv-id.](../media/6d31628e-7162-4370-a8d7-de704aafa350.png)
  
### <a name="step-5-create-an-event"></a>Trin 5: Opret en begivenhed

Når en bestemt forekomst af den pågældende hændelsestype forekommer, f.eks. når slutningen af **dets** levetid, skal du gå til siden **DatastyringHændelser** >  i Microsoft 365 Overholdelsescenter og vælge **+** Opret for at oprette en begivenhed. Her kan du udløse begivenheden ved at oprette den.

![Opret en begivenhed, der udløser starten af en opbevaring for hændelsesbaserede opbevaringsnavne.](../media/create-event-records-management.png)

Op til en million begivenheder understøttes pr. lejer.

### <a name="step-6-choose-the-same-event-type-used-by-the-label-in-step-2"></a>Trin 6: Vælg den samme hændelsestype, der bruges af etiketten i trin 2

Når du opretter begivenheden, skal du vælge den samme hændelsestype, der er angivet i indstillingerne for opbevaringsnavn i trin 2. Hvis du f.eks. har **valgt Produktlevetid** som din begivenhedstype til etiketindstillingerne, skal du vælge **Produktlevetid** , når du opretter begivenheden. Kun indhold med opbevaringsetiketter anvendt på den pågældende hændelsestype får sin opbevaringsperiode udløst.

![Indstilling i Begivenhedsindstillinger for at vælge en hændelsestype.](../media/choose-event-type-records-management.png)

Hvis du har brug for at oprette en begivenhed for flere opbevaringsnavne, der har forskellige hændelsestyper, kan du også vælge **indstillingen Vælg eksisterende** navne. Vælg derefter de etiketter, der er konfigureret for de hændelsestyper, du vil knytte til denne hændelse.

### <a name="step-7-enter-keywords-or-query-for-exchange-asset-id-for-sharepoint-and-onedrive"></a>Trin 7: Angiv nøgleord eller forespørgsel til Exchange, aktiv-id for SharePoint og OneDrive

Nu kan du begrænse omfanget af indholdet. For Exchange indhold skal du gøre dette ved at angive nøgleord eller en forespørgsel. For SharePoint og OneDrive du gøre dette ved at angive aktiv-id'er.

Brug nøgleord Exchange en forespørgsel, der bruger KQL (Sprog til forespørgsel af nøgleord) til emner. Du kan finde flere oplysninger om forespørgselssyntaksen under [Reference til syntaks for Sprog til nøgleordsforespørgsel (KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)). Du kan finde flere oplysninger om de søgbare egenskaber, du kan bruge til Exchange, under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

For aktiv-id'er gælder opbevaring kun for indhold med det angivne *par property:value* . Hvis du f.eks. bruger egenskaben Aktiv-id, skal du angive de id'er, der er vist på følgende billede, `ComplianceAssetID:<value>` i feltet for aktiv-id'er.

Hvis der ikke angives et aktiv-id, får alt indhold med etiketter af den pågældende hændelsestype samme opbevaringsdato anvendt på dem.

Din organisation har måske anvendt andre egenskaber og -oplysninger på de dokumenter, der er relateret til denne hændelsestype. Hvis du f.eks. har brug for at registrere et bestemt produkts poster, kan id'et være en kombination af din brugerdefinerede egenskab ProductID og værdien "XYZ". I dette tilfælde skal du skrive aktiv-jeg'er `ProductID:XYZ` som vist på følgende billede i feltet.

Til sidst skal du vælge den dato, hvor hændelsen indtraf. denne dato bruges som starten af en opbevaringsperiode. Når du har oprettet en begivenhed, synkroniseres den pågældende begivenhedsdato med alt indholdet med en opbevaringsetiket af den pågældende hændelsestype, aktiv-id og nøgleord eller forespørgsler. Som med alle andre opbevaringsmærkater kan synkroniseringen tage op til syv dage.
  
![Siden Begivenhedsindstillinger.](../media/40d3c9db-f624-49a5-b38a-d16bcce20231.png)

Når du har oprettet en begivenhed, træder opbevaringsindstillingerne i kraft for det indhold, der allerede er mærket og indekseret. Hvis opbevaringsnavnet føjes til nyt indhold, efter begivenheden er oprettet, skal du oprette en ny begivenhed med de samme oplysninger.

Sletning af en hændelse annullerer ikke de opbevaringsindstillinger, der nu er gældende for det indhold, der allerede er mærket. Du kan i øjeblikket ikke annullere begivenheder, efter de er blevet udløst.

## <a name="use-content-search-to-find-all-content-with-a-specific-label-or-asset-id"></a>Brug indholdssøgning til at finde alt indhold med en bestemt etiket eller et aktiv-id

Når der er tildelt opbevaringsnavne til indhold, kan du bruge indholdssøgning til at finde alt indhold, der er klassificeret med en bestemt opbevaringsetiket, eller som indeholder et bestemt aktiv-id:
  
- Hvis du vil finde alt indhold med en bestemt opbevaringsetiket, skal du vælge Betingelsen for Opbevaringsetiket og derefter angive det fulde etiketnavn eller en del af navnet og bruge et jokertegn. 
    
- Hvis du vil finde alt indhold med et bestemt aktiv-id, skal du angive **egenskaben ComplianceAssetID** og en værdi ved hjælp af formatet `ComplianceAssetID:<value>`. 
    
Du kan finde flere oplysninger [i Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

## <a name="automate-events-by-using-powershell"></a>Automatiser begivenheder ved hjælp af PowerShell

Du kan bruge et PowerShell-script til at automatisere begivenhedsbaseret opbevaring fra dine forretningsprogrammer. PowerShell-cmdlet'er, der er tilgængelige til begivenhedsbaseret opbevaring:
  
- [Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype)
    
- [New-ComplianceRetentionEventType](/powershell/module/exchange/new-complianceretentioneventtype)
    
- [Remove-ComplianceRetentionEventType](/powershell/module/exchange/remove-complianceretentioneventtype)
    
- [Set-ComplianceRetentionEventType](/powershell/module/exchange/set-complianceretentioneventtype)
    
- [Get-ComplianceRetentionEvent](/powershell/module/exchange/get-complianceretentionevent)
    
- [New-ComplianceRetentionEvent](/powershell/module/exchange/new-complianceretentionevent)
    

## <a name="automate-events-by-using-a-rest-api"></a>Automatiser begivenheder ved hjælp af en REST-API

Du kan bruge en REST-API til automatisk at oprette de hændelser, der udløser starten af opbevaringstiden.

En REST-API er et tjenesteslutpunkt, der understøtter sæt af HTTP-handlinger (metoder), som giver create/retrieve/update/delete adgang til tjenestens ressourcer. Du kan få mere at vide [under Komponenter i en REST API-anmodning/svar](/rest/api/gettingstarted/#components-of-a-rest-api-requestresponse). Ved hjælp af Microsoft 365 REST-API kan hændelser oprettes og hentes ved hjælp af POST- og GET-metoderne.

Der er to muligheder for at bruge REST-API'en:

- **Microsoft Power Automate et lignende program, der** udløser forekomsten af en hændelse automatisk. Microsoft Power Automate er din forhandler til at oprette forbindelse til andre systemer, så du behøver ikke at skrive en brugerdefineret løsning. Du kan finde flere oplysninger [Power Automate webstedet](https://flow.microsoft.com/en-us/).

- **PowerShell eller en HTTP-klient** , der kalder REST API'en for at oprette begivenheder ved hjælp af PowerShell (version 6 eller nyere), som er en del af en brugerdefineret løsning.

Før du bruger REST-API'en, skal du som global administrator bekræfte den URL-adresse, der skal bruges til opbevaringshændelsesopkaldet. Det gør du ved at køre et GET-opbevaringshændelsesopkald ved hjælp af REST API-URL-adressen:

```http
https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent
```

Kontrollér svarkoden. Hvis det er 302, skal du hente den omdirigerede URL fra egenskaben Placering for svaroverskriften og bruge den pågældende URL-adresse `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent` i stedet for i den vejledning, der følger.

De hændelser, der oprettes automatisk, kan bekræftes ved at få dem vist i Microsoft 365 Overholdelsescenter > **Records** **managementEvents** >  .

### <a name="use-microsoft-power-automate-to-create-the-event"></a>Brug Microsoft Power Automate til at oprette begivenheden

Opret et flow, der opretter en hændelse ved hjælp af Microsoft 365 REST-API:

![Brug Flow til at oprette en begivenhed.](../media/automate-event-driven-retention-flow-1.png)

![Brug af flow til at kalde REST-API'en.](../media/automate-event-driven-retention-flow-2.png)

#### <a name="create-an-event"></a>Opret en begivenhed

Eksempelkode til at kalde REST-API'en:

- **Metode**: POST
- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Overskrifter**: Nøgle = Content-Type, Value = application/atom+xml
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
|<d:Navn></d:Navn>|Angiv et entydigt navn til begivenheden,|Må ikke indeholde efterfølgende mellemrum eller følgende tegn: % * \ & < \> \| # ? , : ;|
|<d:EventType></d:EventType>|Angiv navn på hændelsestype (eller Guid),|Eksempel: "Medarbejders afslutning". Hændelsestype skal knyttes til en opbevaringsetiket.|
|<d:SharePointAssetIdQuery></d:SharePointAssetIdQuery>|Angiv "ComplianceAssetId:" + medarbejder-id|Eksempel: "ComplianceAssetId:12345"|
|<d:EventDateTime></d:EventDateTime>|Begivenhedsdato og -klokkeslæt|Format: yyyy-MM-ddTHH:mm:ssZ, eksempel: 2018-12-01T00:00:00Z
|

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse       |
| ----------------- | --------------------- |
| 302               | Omdiriger              |
| 201               | Oprettet               |
| 403               | Godkendelse mislykkedes  |
| 401               | Godkendelse mislykkedes |

##### <a name="get-events-based-on-a-time-range"></a>Få begivenheder baseret på et tidsinterval

- **Metode**: HENT

- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent?BeginDateTime=2019-01-11&EndDateTime=2019-01-16`

- **Overskrifter**: Nøgle = Content-Type, Value = application/atom+xml

- **Godkendelse**: Grundlæggende

- **Brugernavn**: "Complianceuser"

- **Adgangskode**: "Overholdelsesadgangskode"

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse                   |
| ----------------- | --------------------------------- |
| 200               | OK, En liste over hændelser i atom + xml |
| 404               | Blev ikke fundet                         |
| 302               | Omdiriger                          |
| 401               | Godkendelse mislykkedes              |
| 403               | Godkendelse mislykkedes             |

##### <a name="get-an-event-by-id"></a>Få en begivenhed efter id

- **Metode**: HENT

- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent('174e9a86-74ff-4450-8666-7c11f7730f66')`

- **Overskrifter**: Nøgle = Content-Type, Value = application/atom+xml

- **Godkendelse**: Grundlæggende

- **Brugernavn**: "Complianceuser"

- **Adgangskode**: "Overholdelsesadgangskode"

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, Svarteksten indeholder hændelsen i atom+ xml |
| 404               | Blev ikke fundet                                            |
| 302               | Omdiriger                                             |
| 401               | Godkendelse mislykkedes                                 |
| 403               | Godkendelse mislykkedes                                |

##### <a name="get-an-event-by-name"></a>Få en begivenhed efter navn

- **Metode**: HENT

- **URL-adresse**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`

- **Overskrifter**: Nøgle = Content-Type, Value = application/atom+xml

- **Godkendelse**: Grundlæggende

- **Brugernavn**: "Complianceuser"

- **Adgangskode**: "Overholdelsesadgangskode"

###### <a name="response-codes"></a>Svarkoder

| Svarkode | Beskrivelse                                      |
| ----------------- | ---------------------------------------------------- |
| 200               | OK, Svarteksten indeholder hændelsen i atom+ xml |
| 404               | Blev ikke fundet                                            |
| 302               | Omdiriger                                             |
| 401               | Godkendelse mislykkedes                                 |
| 403               | Godkendelse mislykkedes                                |

### <a name="use-powershell-or-any-http-client-to-create-the-event"></a>Brug PowerShell eller en HTTP-klient til at oprette begivenheden

PowerShell skal være version 6 eller nyere.

I en PowerShell-session skal du køre følgende script:

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
