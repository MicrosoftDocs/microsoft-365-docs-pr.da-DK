---
title: Overfør Exchange Online politikker til forebyggelse af datatab til Overholdelsescenter
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Få mere at vide om, hvordan du planlægger og overfører Exchange politikker til forebyggelse af datatab online til Microsoft 365 DLP.
ms.openlocfilehash: 07d0eb19155a7f91b30feb8d7938ea574b0e75f9
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63600968"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-compliance-center"></a>Overfør Exchange Online politikker til forebyggelse af datatab til Overholdelsescenter

[Exchange Online forebyggelse af datatab (DLP)-](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)politikker frarådes. [Meget mere omfattende DLP-funktionalitet](dlp-learn-about-dlp.md), herunder Exchange Online DLP, tilbydes i [Microsoft 365 Compliance Center](https://compliance.microsoft.com/datalossprevention?viewid=policies). Du kan bruge guiden til overførsel af DLP-politik til at hjælpe dig med at få dine Exchange Online DLP-politikker over til Overholdelsescenter, hvor du kan administrere dem.

Guiden Overførsel fungerer ved at læse konfigurationen af dine DLP-politikker i Exchange og derefter oprette dublerede politikker i Overholdelsescenter. Som standard opretter guiden de nye versioner af politikkerne i **testtilstand** , så du kan se, hvilke konsekvenser de har for dit miljø, uden at udføre nogen af handlingerne. Når du er klar til fuld overgang til versioner af Overholdelsescenter, **_skal du_**:

1. Deaktiver eller slet kildepolitikken i Exchange Administration (EAC).
1. Rediger versionen af Overholdelsescenter for politikken, og skift dens status fra **Test til** **Gennemtving**. 

> [!WARNING]
> Hvis du ikke sletter eller deaktiverer kildepolitikken i EAC, før du indstiller versionen af Overholdelsescenter  til Gennemtving begge sæt af politikker, forsøger du at gennemtvinge handlinger, og du vil modtage dublerede hændelser. **_Dette er en ikke-understøttet konfiguration._**


Overførselsguiden overfører kun EXO-politikker og tilknyttede regler for mailflow. Enkeltstående Exchange regler for mailflow overføres ikke.

## <a name="migration-workflow"></a>Arbejdsproces for overførsel

Der er fire faser til at overføre DLP-politikker fra Exchange til den samlede DLP-administrationskonsol i Overholdelsescenter.  

1. Klargør til overførsel
    1. Evaluer og sammenlign dine Exchange Online (EXO) DLP-politikker og dit Overholdelsescenter DLP-politikker for dubletfunktionalitet.
    1. Beslut, hvilke EXO DLP-politikker du vil overføre nøjagtigt, som de er, du kan bruge guiden til at overføre disse.
    1. Beslut, hvilke EXO DLP-politikker du vil konsolidere og konsolidere dem i Exchange Administration, og brug derefter overførselsguiden til at samle dem i Overholdelsescenter.
1. Udfør overførslen – brug guiden
1. Test og validering – undersøg resultaterne
1. Aktivere de overførte politikker

## <a name="before-you-begin"></a>Før du begynder

### <a name="licensing-and-versions"></a>Licenser og versioner

Før du går i gang med at overføre DLP-politikker, skal du bekræfte [Microsoft 365 dit abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) og eventuelle tilføjelser. 

For at få adgang til og bruge guiden til overførsel af politikker skal du have et af disse abonnementer eller tilføjelsesprogrammet

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 overholdelse af regler og standarder
- Microsoft 365 A5 overholdelse af regler og standarder
- Microsoft 365 E5 beskyttelse og styring af oplysninger
- Microsoft 365 A5 beskyttelse og styring af oplysninger

Du kan finde en detaljeret liste over DLP-licenskrav [under Microsoft 365 licensvejledning til sikkerhed og & overholdelse af regler og standarder og forebyggelse af datatab](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)


### <a name="permissions"></a>Tilladelser

Den konto, du bruger til at køre guiden Overførsel, skal have adgang til både siden Exchange Admin Console DLP og den samlede DLP-konsol i Overholdelsescenter.

## <a name="prepare-for-migration"></a>Klargør til overførsel

1. Hvis du ikke er bekendt med DLP, DLP-konsollen i Overholdelsescenter eller Exchange Administration DLP-konsol, skal du gøre dig bekendt med det, før du forsøger at bruge en politikoverførsel.
    1. [Exchange Online politikker til forebyggelse af datatab (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
    1. [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
1. Evaluer dine Exchange politikker for DLP og Overholdelsescenter ved at stille disse spørgsmål:


|Spørgsmål  |Handling  | Overførselsprocedure|
|---------|---------|---------|
|Er politikken stadig nødvendig?    |Hvis den ikke er det, skal du slette eller deaktivere den |overfør ikke|
|Overlapper det med andre Exchange eller Overholdelsescenter DLP-politikker?     |Hvis Ja, kan du konsolidere de overlappende politikker?         |- Hvis det overlapper en Exchange anden Exchange-politik, skal du manuelt oprette den konsoliderede DLP-politik i Exchange Administration og derefter bruge overførselsguiden. </br> - Hvis det overlapper en eksisterende Politik for overholdelsescenter, kan du ændre den eksisterende politik for overholdelsescenter, så den matcher, og overfør ikke Exchange version|
|Er den Exchange DLP-politik tæt fastsat, og har den veldefinerede betingelser, handlinger, inklusioner og udeladelse?     |Hvis ja, er det en god kandidat til at overføre med guiden, skal du notere dig politikken, så du husker at vende tilbage for at slette den senere         | overfør med guiden|

## <a name="migration"></a>Overførsel

Når du har evalueret alle Exchange og Compliance Center DLP-politikker for behov og kompatibilitet, kan du bruge overførselsguiden.

1. Åbn Microsoft 365 [Compliance Center](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP-konsol.
2. Hvis der er Exchange DLP-politikker, der kan overføres, vises der et banner øverst på siden, der giver dig besked.
3. Vælg **Overfør** politikker i banneret for at åbne overførselsguiden. Alle Exchange DLP-politikker vises. Tidligere overførte politikker kan ikke vælges.
4. Vælg de politikker, du vil overføre. Du kan overføre dem enkeltvis eller i grupper ved hjælp af en trinvis tilgang eller alle på én gang. Vælg **Næste**.
5. Gennemse pop op-ruden for eventuelle advarsler eller meddelelser. Løs eventuelle problemer, før du fortsætter.
6. Vælg den tilstand, du vil have den nye politik for Overholdelsescenter oprettet i, **Aktiv**, **Test** eller **Deaktiveret**.  Standarden er **Test**. Vælg **Næste**.
7. Hvis du ønsker det, kan du oprette flere politikker, der er baseret på Exchange DLP-politikker for andre samlede DLP-placeringer. Dette resulterer i én ny samlet DLP-politik for den overførte Exchange-politik og én ny samlet DLP-politik for alle andre placeringer, du vælger her.

> [!IMPORTANT]
> Alle Exchange DLP-politikbetingelser og -handlinger, der ikke understøttes af andre DLP-placeringer, f.eks. enheder, SharePoint, OneDrive, lokalt, MCAS eller Teams-chat og kanalmeddelelser, fjernes fra den yderligere politik. Der er også et forudgående arbejde, der skal udføres for de andre placeringer. Se:
>- [Få mere at Microsoft 365 om forebyggelse af datatab på slutpunkter](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
>- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)
>- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
>- [Få mere at vide Microsoft 365 lokal scanner til forebyggelse af datatab](dlp-on-premises-scanner-learn.md#learn-about-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Kom i gang med den lokale scanner til forebyggelse af datatab](dlp-on-premises-scanner-get-started.md#get-started-with-the-data-loss-prevention-on-premises-scanner)
>- [Brug Microsoft 365 lokal scanner til forebyggelse af datatab](dlp-on-premises-scanner-use.md#use-the-microsoft-365-data-loss-prevention-on-premises-scanner)
>- [Brug politikker til forebyggelse af datatab til ikke-Microsoft-skyapps](dlp-use-policies-non-microsoft-cloud-apps.md#use-data-loss-prevention-policies-for-non-microsoft-cloud-apps)
 
8. Gennemse indstillingerne for overførselsguiden. Vælg **Næste**.
9. Gennemse overførselsrapporten. Vær opmærksom på eventuelle fejl, der Exchange regler for mailflow. Du kan løse dem og overflytte de tilknyttede politikker.

De overførte politikker vises nu på listen over DLP-politikker i Overholdelsescenter DLP-konsollen. 

## <a name="common-errors-and-mitigation"></a>Almindelige fejl og afhjælpning
|Fejlmeddelelse  |Årsag  | Afhjælpning/anbefalede trin|
|---------|---------|---------|
|Der findes allerede en politik for `<Name of the policy>` overholdelse af regler og standarder med navn i scenarier `Dlp`.    |Det er sandsynligt, at denne politikoverførsel blev udført tidligere og derefter blev udført igen i den samme session |Opdater sessionen for at opdatere listen over de politikker, der er tilgængelige for overførslen. Alle tidligere overførte politikker skal være i `Already migrated` tilstanden.|
|Der findes allerede en politik for `<Name of the policy>` overholdelse af regler og standarder med navn i scenarier `Hold`.     |Der findes en opbevaringspolitik med det samme navn i den samme lejer.       |- Omdøb DLP-politikken i EAC til et andet navn. </br> - Prøv overførslen igen for den på påvirkede politik. |
|`DLP-group@contoso.com` kan ikke bruges som en værdi for betingelsen Delt af, fordi det er en distributionsgruppe eller mailaktiveret sikkerhedsgruppe. Brug prædikatet Delt af medlem af til at registrere aktiviteter fra medlemmer af bestemte grupper.     |Transportregler tillader grupper at blive brugt i betingelsen `sender is` , men samlet DLP tillader det ikke.         | Opdater transportreglen for at fjerne alle gruppemailadresser fra betingelsen `sender is` , og føj gruppen til betingelsen `sender is a member of` , hvis det er nødvendigt. Prøv overførslen igen for den på påvirkede politik|
|Modtageren blev ikke fundet `DLP-group@contoso.com`. Hvis den er oprettet for nylig, kan du prøve at forsøge handlingen igen efter et stykke tid. Hvis slettet eller udløbet, skal du nulstille med gyldige værdier og prøve igen.     |Det er sandsynligt, at den gruppeadresse, der bruges i `sender is a member of` tilstanden `recipient is a member of` , er udløbet eller ugyldig.         | - Fjern/erstat alle de ugyldige gruppemailadresser i transportreglen Exchange Administration. </br> - Prøv overførslen igen for den på påvirkede politik.|
|Den værdi, der er angivet `FromMemberOf` i prædikatet, skal være mailaktiveret sikkerhedsgruppe.     |Transportregler tillader, at individuelle brugere kan bruges i betingelsen `sender is a member of` , men samlet DLP tillader det ikke.         | - Opdater transportreglen for at fjerne alle individuelle brugermailadresser fra betingelsen `sender is a member of` og føje brugerne til betingelsen, hvis `sender is` det er nødvendigt. </br> - Prøv overførslen igen for den på påvirkede politik.|
|Den værdi, der er angivet `SentToMemberOf` i prædikatet, skal være mailaktiveret sikkerhedsgruppe.    |Transportregler tillader individuelle brugere at blive brugt under betingelsen `recipient is a member of` , men samlet DLP tillader det ikke.         | - Opdater transportreglen for at fjerne alle individuelle brugermailadresser fra betingelsen `recipient is a member of` og føje brugerne til betingelsen, hvis `recipient is` det er nødvendigt. </br> - Prøv overførslen igen for den på påvirkede politik.|
|Brug af `<Name of condition>` parameteren understøttes kun for Exchange. Fjern enten denne parameter, eller aktiver kun Exchange placering.         | Det er sandsynligt, at der findes en anden politik med det samme navn i Overholdelsescenter med andre placeringer, f.eks. SPO/ODB/Teams, hvor den nævnte betingelse ikke understøttes. | Omdøb DLP-politikken Exchange Administration, og prøv overførslen igen.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Test og validering <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Test og gennemse dine politikker.

1. Følg fremgangsmåden [til test af en DLP-politik](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. Gennemse de hændelser, der er oprettet af politikken i [Aktivitetsoversigt](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-365-unified-dlp"></a>Gennemse politik match mellem Exchange Administration DLP og Microsoft 365 Unified DLP

Hvis du vil sikre, at de overførte politikker fungerer som forventet, kan du eksportere rapporterne fra begge administrationer og foretage en sammenligning af politikoverensstemmelsen.

1. Forbind til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Eksportér [EAC DLP-rapporten](/powershell/module/exchange/get-maildetaildlppolicyreport). Du kan kopiere denne cmdlet og indsætte de relevante værdier:

```powershell
Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv"> 
```

3. Eksportér [den samlede DLP-rapport](/powershell/module/exchange/get-dlpdetailreport). Du kan kopiere denne cmdlet og indsætte de relevante værdier:

```powershell
Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">  
```

## <a name="activate-your-migrated-policies"></a>Aktivere dine overførte politikker

Når du er tilfreds med, hvordan dine overførte politikker fungerer, kan du angive dem **til Gennemtving**.

1. Åbn Exchange Administration DLP-konsol.
2. Deaktiver eller slet kildepolitikken.
3. Åbn Microsoft 365 [Compliance Center](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP-konsol, og vælg den politik, du vil gøre aktiv for at redigere den.
4. Skift status til **Aktiver**.

## <a name="related-articles"></a>Relaterede artikler

- [Exchange Online politikker til forebyggelse af datatab (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
- [Exchange Online politikker til forebyggelse af datatab (DLP)](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
