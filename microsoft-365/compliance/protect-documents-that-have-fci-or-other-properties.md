---
title: Opret en DLP-politik for at beskytte dokumenter med FCI eller andre egenskaber
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleContentPropertyContainsWords
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkSPO
description: Lær at bruge en politik til forebyggelse af datatab (DLP) til at beskytte dokumenter, der har egenskaber fra et tredjepartssystem.
ms.openlocfilehash: 0bfb520119717d952a803e0f37fef0a1499ff0da
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589546"
---
# <a name="create-a-dlp-policy-to-protect-documents-with-fci-or-other-properties"></a>Opret en DLP-politik for at beskytte dokumenter med FCI eller andre egenskaber

Microsoft 365 politikker til forebyggelse af datatab (DLP) kan bruge klassificeringsegenskaber eller elementegenskaber til at identificere følsomme elementer. Du kan f.eks. bruge:

- Windows egenskaber for Server File Classification-infrastruktur (FCI)
- SharePoint dokumentegenskaber
- dokumentegenskaber fra tredjepart

![Diagram, der Office 365 et eksternt klassificeringssystem.](../media/59ad0ac1-4146-4919-abd1-c74d8508d25e.png)

Din organisation kan f.eks. bruge Windows Server FCI til at identificere elementer med personlige data som f.eks. cpr-numre og derefter klassificere dokumentet ved at indstille egenskaben Personligt **identificerbare** oplysninger til **Høj, Moderat****, Lav****, Offentlig** eller Ikke **PII** baseret på typen og antallet af forekomster af personlige data, der findes i dokumentet.

I Microsoft 365 kan du oprette en DLP-politik, der identificerer dokumenter, der har denne egenskab indstillet til bestemte værdier, f.eks.  Høj og **Mellem, og** derefter tager en handling som f.eks. at blokere adgang til disse filer. Den samme politik kan have en anden regel, der tager en anden **handling, hvis** egenskaben er indstillet til Lav, f.eks. afsendelse af en mailmeddelelse. På denne måde integreres DLP med Windows Server FCI og kan hjælpe med at beskytte Office dokumenter, der uploades eller deles Microsoft 365 fra Windows Serverbaserede filservere.

En DLP-politik søger blot efter et bestemt egenskabsnavn/værdipar. Alle dokumentegenskaber kan bruges, så længe egenskaben har en tilsvarende administreret egenskab til SharePoint søgning. Eksempelvis kan en gruppe SharePoint bruge en indholdstype med navnet **Rejserapport med** et obligatorisk felt med navnet **Kunde**. Når en person opretter en rejserapport, skal vedkommende angive kundenavnet. Dette egenskabsnavn/værdipar kan også bruges i en DLP-politik – f.eks. hvis du vil have en regel, der blokerer adgangen til dokumentet for  gæster, når feltet Kunde indeholder **Contoso**.

Hvis du vil anvende din DLP-politik på indhold med bestemte Microsoft 365 navne, skal du ikke følge trinnene her. I stedet kan du få mere at [vide om, hvordan du bruger en opbevaringsetiket som en betingelse i en DLP-politik](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

## <a name="before-you-create-the-dlp-policy"></a>Før du opretter DLP-politikken

Før du kan bruge en Windows Server FCI-egenskab eller en anden egenskab i en DLP-politik, skal du oprette en administreret egenskab <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">i SharePoint Administration</a>. Her er årsagen.

I SharePoint Online og OneDrive for Business oprettes søgeindekset ved at gennemsøge indholdet på dine websteder. Crawleren henter indhold og metadata fra dokumenterne i form af gennemsøgte egenskaber. Søgeskemaet hjælper crawleren med at beslutte, hvilket indhold og metadata, der skal afhentes. Eksempler på metadata er forfatteren og titlen på et dokument. Men for at hente indhold og metadata fra dokumenterne ind i søgeindekset skal de gennemsøgte egenskaber knyttes til administrerede egenskaber. Det er kun administrerede egenskaber, der opbevares i indekset. Eksempelvis er en gennemsøgt egenskab, der er relateret til forfatteren, knyttet til en administreret egenskab, der er relateret til forfatteren.

> [!NOTE]
> Sørg for at bruge et administreret egenskabsnavn og ikke et gennemsøgt egenskabsnavn, når du opretter DLP-regler ved hjælp af betingelsen `ContentPropertyContainsWords` .

Dette er vigtigt, fordi DLP bruger søge crawleren til at identificere og klassificere følsomme oplysninger på dine websteder og derefter gemme disse følsomme oplysninger i en sikker del af søgeindekset. Når du overfører et dokument til en Office 365, SharePoint automatisk gennemsøgte egenskaber ud fra dokumentegenskaberne. Men hvis du vil bruge en FCI-egenskab eller en anden egenskab i en DLP-politik, skal den gennemsøgte egenskab knyttes til en administreret egenskab, så indhold med denne egenskab opbevares i indekset.

Du kan finde flere oplysninger om søgning og administrerede [egenskaber under Administrer søgeskemaet i SharePoint Online](/sharepoint/manage-search-schema).

### <a name="step-1-upload-a-document-with-the-needed-property-to-office-365"></a>Trin 1: Upload et dokument med den nødvendige egenskab til at Office 365

Du skal først overføre et dokument med den egenskab, du vil referere til i din DLP-politik. Microsoft 365 registrerer egenskaben og opretter automatisk en gennemsøgt egenskab ud fra den. I næste trin skal du oprette en administreret egenskab og derefter knytte den administrerede egenskab til denne gennemsøgte egenskab.

### <a name="step-2-create-a-managed-property"></a>Trin 2: Oprette en administreret egenskab

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

2. I venstre navigationsrude skal du **vælge SharePoint** \> **.** Du er nu i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>.

3. I venstre navigationsrude skal du **vælge søgning** \> på **administrationssiden for søgning** Administrer \> **søgeskema**.

   ![siden administration af søgning SharePoint Administration.](../media/6bcd3aec-d11a-4f8c-9987-8f35da14d80b.png)

4. På siden **Administrerede egenskaber** ny \> **administreret egenskab**.

   ![Siden Administrerede egenskaber med knappen Ny administreret egenskab fremhævet.](../media/b161c764-414c-4037-83ed-503a49fb4410.png)

5. Angiv et navn og en beskrivelse af egenskaben. Dette navn er, hvad der vises i dine DLP-politikker.

6. Under **Type** skal du vælge **Tekst**.

7. Under **Hovedegenskaber skal du** vælge **Forespørgsels- og** **Hentbare**.

8. Under **Tilknytninger til gennemsøgte egenskaber Tilføj** \> **en tilknytning**.

9. I dialogboksen **for valg** \> af gennemsøgte egenskaber skal du finde og vælge den gennemsøgte egenskab, der svarer til egenskaben Windows Server FCI eller en anden egenskab, som du skal bruge i din DLP-politik \> **OK**.

   ![Dialogboks til valg af gennemsøgt egenskab.](../media/aeda1dce-1342-48bf-9594-a8e4f230e8aa.png)

10. Nederst på siden **OK**\>.

## <a name="create-a-dlp-policy-that-uses-an-fci-property-or-other-property"></a>Opret en DLP-politik, der bruger en FCI-egenskab eller en anden egenskab

I dette eksempel bruger en organisation FCI på sine Windows Serverbaserede filservere. Specifikt bruger de FCI-klassificeringsegenskaben Personidentificerbare  oplysninger med mulige værdier **høj,** **moderat****,** **lav**, offentlig og **ikke pii**. Nu vil de bruge deres eksisterende FCI-klassificering i deres DLP-politikker Office 365.

Først skal de følge trinnene ovenfor for at oprette en administreret egenskab i SharePoint Online, som er kort til den gennemsøgte egenskab, der oprettes automatisk fra FCI-egenskaben.

Derefter opretter de en DLP-politik med to regler, der begge bruger betingelsen **Dokumentegenskaber indeholder nogen af disse værdier**:

- **FCI PII-indhold – høj, moderat** Den første regel begrænser adgangen til dokumentet, hvis FCI-klassificeringsegenskaben Personligt **identificerbare** oplysninger er  lig med Høj eller Moderat, og dokumentet deles med personer uden for organisationen.

- **FCI PII-indhold – Lav** Den anden regel sender en meddelelse til **dokumentets ejer**, hvis FCI-klassificeringsegenskaben Personligt **identificerbare** oplysninger er lig med Lav, og dokumentet deles med personer uden for organisationen.

### <a name="create-the-dlp-policy-by-using-powershell"></a>Opret DLP-politikken ved hjælp af PowerShell

Betingelsen **Dokumentegenskaber indeholder** nogen af disse værdier er midlertidigt ikke tilgængelig i brugergrænsefladen i Security &amp; Compliance Center, men du kan stadig bruge denne betingelse ved hjælp af PowerShell. Du kan bruge  `New\Set\Get-DlpCompliancePolicy` cmdlet'er til at arbejde med en DLP-politik og  `New\Set\Get-DlpComplianceRule` bruge cmdlet'er  `ContentPropertyContainsWords` med parameteren til at tilføje betingelsen Dokumentegenskaber indeholder en af **disse værdier**.

Du kan finde flere oplysninger om disse cmdlet'er i [Security &amp; Compliance Center-cmdlet'er](/powershell/exchange/exchange-online-powershell).

1. [Forbind til sikkerhed &amp; Overholdelsescenter ved hjælp af Remote PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. Opret politikken ved hjælp af  `New-DlpCompliancePolicy`.

Denne PowerShell opretter en DLP-politik, der gælder for alle placeringer.

   ```powershell
   New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable
   ```

3. Opret de to regler, der er `New-DlpComplianceRule`beskrevet ovenfor, ved hjælp af , hvor  én regel gælder for lav værdi, og en anden regel bruges til **værdierne Høj og** **Moderat.**

   Her er et PowerShell-eksempel, der opretter disse to regler. Egenskabsnavn/værdipar er omsluttet af anførselstegn, og et egenskabsnavn kan angive flere værdier adskilt af kommaer uden mellemrum, f.eks.  `"<Property1>:<Value1>,<Value2>","<Property2>:<Value3>,<Value4>"....`

   ```powershell
   New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $falseNew-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner
   ```

   Windows Server FCI indeholder mange indbyggede egenskaber, herunder personligt **identificerbare** oplysninger, der bruges i dette eksempel. De mulige værdier for hver egenskab kan være forskellige for hver organisation. Værdierne **Høj**, **Moderat** og **Lav, der** bruges her, er kun et eksempel. For din organisation kan du få vist Windows Server FCI-klassificeringsegenskaberne med deres mulige værdier i filen Server Resource Manager på Windows Server-baseret filserver. Få mere at vide under [Opret en klassificeringsegenskab](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759215(v=ws.11)).

Når du er færdig, skal din politik have to nye regler, der begge bruger **dokumentegenskaberne, indeholder en af disse værdibetingelse** . Denne betingelse vises ikke i brugergrænsefladen, men de andre betingelser, handlinger og indstillinger vises.

En regel blokerer adgangen til indhold, hvor **egenskaben Personligt identificerbare** oplysninger er lig **med Høj** eller **Moderat**. En anden regel sender en meddelelse om indhold, hvor egenskaben **Personligt identificerbare oplysninger** er lig med **Lav**.

![Dialogboksen Ny DLP-politik viser to regler, der lige er oprettet.](../media/5c56c13b-62a5-4f25-8eb7-ce83a844bb12.png)

## <a name="after-you-create-the-dlp-policy"></a>Når du har oprettet DLP-politikken

Hvis du udfører trinnene i de forrige afsnit, oprettes der en DLP-politik, der hurtigt registrerer indhold med den pågældende egenskab, men kun hvis indholdet uploades for nyligt (så indholdet indekseres), eller hvis indholdet er gammelt, men kun redigeret (så indholdet bliver indekseret igen).

Hvis du vil registrere indhold med den pågældende egenskab overalt, kan du manuelt anmode om, at dit bibliotek, dit websted eller din gruppe af websteder indekseres igen, så DLP-politikken er opmærksom på alt indhold med den pågældende egenskab. I SharePoint Online gennemsøges indhold automatisk ud fra en defineret gennemsøgningsplan. Crawleren henter indhold, der er blevet ændret siden den seneste gennemsøgning, og opdaterer indekset. Hvis du har brug for din DLP-politik til at beskytte indhold før den næste planlagte gennemsøgning, kan du følge disse trin.

> [!CAUTION]
> Genindeksering af et websted kan medføre en stor belastning af søgesystemet. Indekser ikke dit websted igen, medmindre scenariet kræver det.

Få mere at vide under [Anmod manuelt om gennemsøgning og genindeksering af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

### <a name="reindex-a-site-optional"></a>Sæt et websted ind igen (valgfrit)

1. På webstedet skal du vælge **Indstillinger** (tandhjulsikonet øverst til højre) **Indstillinger**\>.

2. Under **Søgning** skal du **vælge Søg og offline tilgængelighed** \> **Gensøge websted**.

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)

- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)

- [Send meddelelser, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md)

- [Hvad DLP-politikskabelonerne indeholder](what-the-dlp-policy-templates-include.md)

- [Enhedsdefinitioner for følsomme oplysningstyper](sensitive-information-type-entity-definitions.md)