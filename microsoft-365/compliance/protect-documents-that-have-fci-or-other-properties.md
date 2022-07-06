---
title: Opret en DLP-politik for at beskytte dokumenter
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
description: Få mere at vide om, hvordan du bruger en DLP-politik (forebyggelse af datatab) til at beskytte dokumenter, der har egenskaber fra et tredjepartssystem.
ms.openlocfilehash: c57a7b60377cf401a0e29e33ce524c4180b9f725
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66626353"
---
# <a name="create-a-dlp-policy-to-protect-documents-with-fci-or-other-properties"></a>Opret en DLP-politik for at beskytte dokumenter med FCI eller andre egenskaber

Microsoft Purview Forebyggelse af datatab politikker (DLP) kan bruge klassificeringsegenskaber eller elementegenskaber til at identificere følsomme elementer. Du kan f.eks. bruge:

- Egenskaber for Windows Server File Classification Infrastructure (FCI)
- Egenskaber for SharePoint-dokument
- egenskaber for systemdokument fra tredjepart

![Diagram, der viser Office 365 og eksternt klassificeringssystem.](../media/59ad0ac1-4146-4919-abd1-c74d8508d25e.png)

Din organisation kan f.eks. bruge Windows Server FCI til at identificere elementer med personlige data, f.eks. cpr-numre, og derefter klassificere dokumentet ved at angive egenskaben **Personligt identificerbare oplysninger** til **Høj**, **Moderat**, **Lav**, **Offentlig** eller **Ikke-PII** baseret på typen og antallet af forekomster af personlige oplysninger, der findes i dokumentet.

I Microsoft 365 kan du oprette en DLP-politik, der identificerer dokumenter, hvor egenskaben er angivet til bestemte værdier, f.eks **. Høj** og **Mellem**, og derefter udfører en handling, f.eks. blokering af adgang til disse filer. Den samme politik kan have en anden regel, der udfører en anden handling, hvis egenskaben er angivet til **Lav**, f.eks. afsendelse af en mailmeddelelse. På denne måde integreres DLP med Windows Server FCI og kan hjælpe med at beskytte Office-dokumenter, der uploades eller deles til Microsoft 365, fra Windows Server-baserede filservere.

En DLP-politik søger ganske enkelt efter et bestemt egenskabsnavn/værdipar. En hvilken som helst dokumentegenskab kan bruges, så længe egenskaben har en tilsvarende administreret egenskab for SharePoint-søgning. En gruppe af SharePoint-websteder kan f.eks. bruge en indholdstype med navnet **Rejserapport** med et obligatorisk felt med navnet **Kunde**. Når en person opretter en rejserapport, skal vedkommende angive kundenavnet. Dette egenskabsnavn/værdipar kan også bruges i en DLP-politik – f.eks. hvis du vil have en regel, der blokerer adgang til dokumentet for gæster, når feltet **Kunde** indeholder **Contoso**.

Hvis du vil anvende din DLP-politik på indhold med bestemte Microsoft 365-mærkater, skal du ikke følge trinnene her. I stedet kan du få mere at vide om, hvordan [du bruger en opbevaringsmærkat som en betingelse i en DLP-politik](data-loss-prevention-policies.md#using-a-retention-label-as-a-condition-in-a-dlp-policy).

## <a name="before-you-create-the-dlp-policy"></a>Før du opretter DLP-politikken

Før du kan bruge en Windows Server FCI-egenskab eller en anden egenskab i en DLP-politik, skal du oprette en administreret egenskab i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>. Her er hvorfor.

I SharePoint Online og OneDrive for Business bygges søgeindekset op ved at gennemsøge indholdet på dine websteder. Crawleren henter indhold og metadata fra dokumenterne i form af gennemsøgte egenskaber. Søgeskemaet hjælper crawleren med at beslutte, hvilket indhold og hvilke metadata der skal hentes. Eksempler på metadata er forfatteren og titlen på et dokument. Hvis du vil hente indhold og metadata fra dokumenterne til søgeindekset, skal de gennemsøgte egenskaber dog knyttes til administrerede egenskaber. Det er kun administrerede egenskaber, der bevares i indekset. En gennemsøgt egenskab, der er relateret til forfatteren, knyttes f.eks. til en administreret egenskab, der er relateret til forfatteren.

> [!NOTE]
> Sørg for at bruge et navn på en administreret egenskab og ikke et gennemsøgt egenskabsnavn, når du opretter DLP-regler ved hjælp af betingelsen `ContentPropertyContainsWords` .

Dette er vigtigt, fordi DLP bruger søgecrawleren til at identificere og klassificere følsomme oplysninger på dine websteder og derefter gemme disse følsomme oplysninger i en sikker del af søgeindekset. Når du uploader et dokument til Office 365, opretter SharePoint automatisk gennemsøgte egenskaber baseret på dokumentegenskaberne. Men hvis du vil bruge en FCI eller en anden egenskab i en DLP-politik, skal den gennemsøgte egenskab knyttes til en administreret egenskab, så indholdet med den pågældende egenskab bevares i indekset.

Du kan finde flere oplysninger om søgeegenskaber og administrerede egenskaber [under Administrer søgeskemaet i SharePoint Online](/sharepoint/manage-search-schema).

### <a name="step-1-upload-a-document-with-the-needed-property-to-office-365"></a>Trin 1: Overfør et dokument med den nødvendige egenskab for at Office 365

Du skal først uploade et dokument med den egenskab, du vil referere til i din DLP-politik. Microsoft 365 registrerer egenskaben og opretter automatisk en gennemsøgt egenskab ud fra den. I næste trin skal du oprette en administreret egenskab og derefter knytte den administrerede egenskab til denne gennemsøgte egenskab.

### <a name="step-2-create-a-managed-property"></a>Trin 2: Opret en administreret egenskab

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.

2. I venstre navigationsrude skal du vælge **Administration centre** \> **i SharePoint**. Du er nu i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>.

3. I venstre navigationsrude skal du vælge **Søg** \> på siden \> **til administration af søgning** **Administrer søgeskema**.

   ![siden til administration af søgning i SharePoint Administration.](../media/6bcd3aec-d11a-4f8c-9987-8f35da14d80b.png)

4. På siden \> **Administrerede egenskaber** **Ny administreret egenskab**.

   ![Siden Administrerede egenskaber med knappen Ny administreret egenskab fremhævet.](../media/b161c764-414c-4037-83ed-503a49fb4410.png)

5. Angiv et navn og en beskrivelse af egenskaben. Dette navn vises i dine DLP-politikker.

6. Vælg **Tekst** i **Type**.

7. Under **Hovedegenskaber** skal du vælge **Forespørgselsbar** og **Kan hentes**.

8. Tilføj **en tilknytning** under **Tilknytninger til gennemsøgte egenskaber**\>.

9. I dialogboksen \> **til valg af gennemsøgt egenskab** skal du søge efter og vælge den gennemsøgte egenskab, der svarer til egenskaben Windows Server FCI eller en anden egenskab, som du vil bruge i DLP-politikken \> **OK**.

   ![dialogboksen til valg af gennemsøgt egenskab.](../media/aeda1dce-1342-48bf-9594-a8e4f230e8aa.png)

10. Nederst på siden \> **OK**.

## <a name="create-a-dlp-policy-that-uses-an-fci-property-or-other-property"></a>Opret en DLP-politik, der bruger en FCI-egenskab eller en anden egenskab

I dette eksempel bruger en organisation FCI på sine Windows Server-baserede filservere. De bruger specifikt FCI-klassificeringsegenskaben med navnet **Personligt identificerbare oplysninger** med mulige værdier som **High**, **Moderate**, **Low**, **Public** og **Not PII**. Nu vil de bruge deres eksisterende FCI-klassificering i deres DLP-politikker i Office 365.

Først skal de følge trinnene ovenfor for at oprette en administreret egenskab i SharePoint Online, som knyttes til den gennemsøgte egenskab, der oprettes automatisk ud fra FCI-egenskaben.

Derefter opretter de en DLP-politik med to regler, der begge bruger betingelsen **Dokumentegenskaber indeholder en af disse værdier**:

- **FCI PII-indhold – høj, moderat** Den første regel begrænser adgangen til dokumentet, hvis FCI-klassificeringsegenskaben **Personligt identificerbare oplysninger** er lig med **Høj** eller **Moderat,** og dokumentet deles med personer uden for organisationen.

- **FCI PII-indhold – lav** Den anden regel sender en meddelelse til ejeren af dokumentet, hvis FCI-klassificeringsegenskaben **Personligt identificerbare oplysninger** er lig med **Lav** , og dokumentet deles med personer uden for organisationen.

### <a name="create-the-dlp-policy-by-using-security--compliance-powershell"></a>Opret DLP-politikken ved hjælp af PowerShell til sikkerhed & overholdelse af angivne standarder

Betingelsen **Dokumentegenskaber indeholder nogen af disse værdier** er midlertidigt ikke tilgængelige i Microsoft Purview-compliance-portal, men du kan stadig bruge denne betingelse i Security & Compliance PowerShell. Du kan bruge `New\Set\Get-DlpCompliancePolicy` cmdlet'erne til at arbejde med en DLP-politik og bruge `New\Set\Get-DlpComplianceRule` cmdlet'erne med `ContentPropertyContainsWords` parameteren til at tilføje betingelsen **Dokumentegenskaber indeholder en af disse værdier**.

1. [Opret forbindelse til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell)

2. Opret politikken ved hjælp `New-DlpCompliancePolicy`af .

   Denne PowerShell opretter en DLP-politik, der gælder for alle placeringer.

   ```powershell
   New-DlpCompliancePolicy -Name FCI_PII_policy -ExchangeLocation All -SharePointLocation All -OneDriveLocation All -Mode Enable
   ```

3. Opret de to regler, der er beskrevet ovenfor, ved hjælp `New-DlpComplianceRule`af , hvor én regel er for værdien **Lav** , og en anden regel er for værdierne **Høj** og **Moderat** .

   Her er et PowerShell-eksempel, der opretter disse to regler. Egenskabsnavne/værdipar er omsluttet af anførselstegn, og et egenskabsnavn kan angive flere værdier adskilt af kommaer uden mellemrum, f.eks. `"<Property1>:<Value1>,<Value2>","<Property2>:<Value3>,<Value4>"....`

   ```powershell
   New-DlpComplianceRule -Name FCI_PII_content-High,Moderate -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $true -ContentPropertyContainsWords "Personally Identifiable Information:High,Moderate" -Disabled $falseNew-DlpComplianceRule -Name FCI_PII_content-Low -Policy FCI_PII_policy -AccessScope NotInOrganization -BlockAccess $false -ContentPropertyContainsWords "Personally Identifiable Information:Low" -Disabled $false -NotifyUser Owner
   ```

   Windows Server FCI indeholder mange indbyggede egenskaber, herunder **personlige oplysninger** , der bruges i dette eksempel. De mulige værdier for hver egenskab kan være forskellige for hver organisation. Værdierne **High**, **Moderate** og **Low** , der bruges her, er kun et eksempel. For din organisation kan du få vist egenskaberne for Windows Server FCI-klassificering med deres mulige værdier i filen Server Resource Manager på den Windows Server-baserede filserver. Du kan få flere oplysninger under [Opret en klassificeringsegenskab](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759215(v=ws.11)).

Når du er færdig, skal politikken have to nye regler, der begge bruger **dokumentegenskaberne, som indeholder en af disse værdibetingelse** . Denne betingelse vises ikke i brugergrænsefladen, selvom de andre betingelser, handlinger og indstillinger vises.

En regel blokerer adgang til indhold, hvor egenskaben **Personlige oplysninger** er lig med **Høj** eller **Moderat**. En anden regel sender en meddelelse om indhold, hvor egenskaben **Personlige oplysninger** er lig med **Lav**.

![Dialogboksen Ny DLP-politik, der viser to regler, der netop er oprettet.](../media/5c56c13b-62a5-4f25-8eb7-ce83a844bb12.png)

## <a name="after-you-create-the-dlp-policy"></a>Når du har oprettet DLP-politikken

Hvis du udfører trinnene i de forrige afsnit, oprettes der en DLP-politik, der hurtigt registrerer indhold med denne egenskab, men kun hvis indholdet netop er uploadet (så indholdet indekseres), eller hvis indholdet er gammelt, men blot redigeret (så indholdet indekseres igen).

Hvis du vil registrere indhold med denne egenskab overalt, kan du manuelt anmode om, at biblioteket, webstedet eller gruppen af websteder indekseres igen, så DLP-politikken er opmærksom på alt indholdet med den pågældende egenskab. I SharePoint Online gennemsøges indhold automatisk baseret på en defineret tidsplan for gennemsøgning. Crawleren henter indhold, der er ændret siden sidste gennemsøgning, og opdaterer indekset. Hvis du har brug for din DLP-politik for at beskytte indhold før den næste planlagte gennemsøgning, kan du udføre disse trin.

> [!CAUTION]
> Genindeksering af et websted kan medføre en massiv belastning på søgesystemet. Indeksér ikke dit websted igen, medmindre dit scenarie absolut kræver det.

Du kan få flere oplysninger under [Anmod manuelt om gennemsøgning og genindeksering af et websted, et bibliotek eller en liste](/sharepoint/crawl-site-content).

### <a name="reindex-a-site-optional"></a>Omsæt et websted (valgfrit)

1. På webstedet skal du vælge **Indstillinger** (tandhjulsikon øverst til højre) \> **Indstillinger for websted**.

2. Under **Søg** skal du vælge **Søg og offlinetilgængelighed** \> **Omstil websted**.

## <a name="more-information"></a>Flere oplysninger

- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)

- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)

- [Send meddelelser, og vis politiktip til DLP-politikker](use-notifications-and-policy-tips.md)

- [Hvad inkluderes i DLP-politikskabelonerne](what-the-dlp-policy-templates-include.md)

- [Enhedsdefinitioner for type af følsomme oplysninger](sensitive-information-type-entity-definitions.md)
