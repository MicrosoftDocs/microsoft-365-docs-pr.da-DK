---
title: Overfør Exchange Online DLP-politikker til Overholdelsescenter
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
description: Få mere at vide om, hvordan du planlægger og overfører dine politikker til forebyggelse af datatab i Exchange til DLP.
ms.openlocfilehash: 371dfafbbf6acf31587b0786a5b5594fb83571d9
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638273"
---
# <a name="migrate-exchange-online-data-loss-prevention-policies-to-microsoft-purview-compliance-portal"></a>Overfør Exchange Online politikker til forebyggelse af datatab til Microsoft Purview-compliance-portal

[Exchange Online politikker til forebyggelse af datatab](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) frarådes. [Der tilbydes meget bedre DLP-funktionalitet](dlp-learn-about-dlp.md), herunder Exchange Online DLP, i [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/datalossprevention?viewid=policies). Du kan bruge guiden til overflytning af DLP-politik til at hjælpe dig med at overføre dine Exchange Online DLP-politikker til Overholdelsescenter, hvor du administrerer dem.

Guiden til overførsel fungerer ved at læse konfigurationen af dine DLP-politikker i Exchange og derefter oprette duplikerede politikker i Overholdelsescenter. Guiden opretter som standard de nye versioner af politikkerne i **testtilstand** , så du kan se, hvilken indvirkning de ville have i dit miljø, uden at gennemtvinge nogen af handlingerne. Når du er klar til fuldt ud at skifte til versionerne i Overholdelsescenter, **_skal du_**:

1. Deaktiver eller slet kildepolitikken i Exchange Administration Center (EAC).
1. Rediger versionen af politikkens Overholdelsescenter, og skift dens status fra **Test** til **Gennemtving**.

> [!WARNING]
> Hvis du ikke sletter eller deaktiverer kildepolitikken i EAC, før du angiver versionen for Overholdelsescenter til **Gennemtving** , vil begge sæt politikker forsøge at gennemtvinge handlinger, og du vil modtage dublethændelser. **_Dette er en konfiguration, der ikke understøttes._**

Guiden til overførsel overfører kun EXO-politikker og tilknyttede regler for mailflow. Separate regler for Exchange-mailflow overføres ikke.

## <a name="migration-workflow"></a>Overførselsarbejdsproces

Der er fire faser til overførsel af DLP-politikker fra Exchange til Unified DLP-administrationskonsollen i Overholdelsescenter.

1. Forbered migrering
    1. Evaluer og sammenlign dine exo-politikker (Exchange Online) og dine DLP-politikker for overholdelsescenter for dubletter.
    1. Beslut, hvilke EXO DLP-politikker du vil overføre, præcis som de er, du kan bruge guiden til at overføre disse.
    1. Beslut, hvilke EXO DLP-politikker du vil konsolidere og konsolidere dem i Exchange Administration, og brug derefter guiden til overførsel til at overføre dem til Overholdelsescenter.
1. Udfør migreringen – brug guiden
1. Test og validering – undersøg resultaterne
1. Aktivér de migrerede politikker

## <a name="before-you-begin"></a>Før du begynder

### <a name="licensing-and-versions"></a>Licenser og versioner

Før du begynder at overføre DLP-politikker, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) og eventuelle tilføjelsesprogrammer.

Hvis du vil have adgang til og bruge guiden til overførsel af politik, skal du have et af disse abonnementer eller tilføjelsesprogrammer

- Microsoft 365 E3
- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 overholdelse af angivne standarder
- Microsoft 365 A5 overholdelse af angivne standarder
- Microsoft 365 E5 beskyttelse og styring af oplysninger
- Microsoft 365 A5 beskyttelse og styring af oplysninger

Du kan finde en detaljeret liste over DLP-licenskrav i [Microsoft 365 Licensvejledning til overholdelse af & sikkerhed, forebyggelse af datatab](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

### <a name="permissions"></a>Tilladelser

Den konto, du bruger til at køre guiden til overførsel, skal have adgang til både Exchange Administration Console DLP-siden og til Unified DLP-konsollen i Overholdelsescenter.

## <a name="prepare-for-migration"></a>Forbered migrering

1. Hvis du ikke er fortrolig med DLP, DLP-konsollen i Compliance Center eller Exchange Administration Center DLP-konsollen, bør du blive fortrolig med dig selv, før du forsøger at migrere en politik.
    1. [Exchange Online politikker til forebyggelse af datatab](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    1. [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
    1. [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md)
1. Evaluer politikkerne for Exchange DLP og Overholdelsescenter ved at stille disse spørgsmål:

|Spørgsmål|Handling|Overførselsprocedure|
|---|---|---|
|Er politikken stadig nødvendig?|Hvis ikke, skal du slette eller deaktivere den|migrer ikke|
|Overlapper den med andre DLP-politikker for Exchange eller Overholdelsescenter?|Hvis ja, kan du så konsolidere de overlappende politikker?|– Hvis den overlapper en anden Exchange-politik, skal du manuelt oprette den konsoliderede DLP-politik i Exchange Administration center og derefter bruge guiden til overflytning. </br> - Hvis den overlapper en eksisterende politik for Overholdelsescenter, kan du ændre den eksisterende politik for Overholdelsescenter, så den stemmer overens, og ikke overføre Exchange-versionen|
|Er Exchange DLP-politikken begrænset og har den veldefinerede betingelser, handlinger, medtagelser og udeladelser?|Hvis ja, er det en god kandidat at overføre med guiden. Notér dig politikken, så du husker at vende tilbage for at slette den senere|migrer med guiden|

## <a name="migration"></a>Overførsel

Når du har evalueret alle DLP-politikkerne for Exchange og Overholdelsescenter for behov og kompatibilitet, kan du bruge guiden til overførsel.

1. Åbn [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP-konsollen.
2. Hvis der er Exchange DLP-politikker, der kan overføres, vises der et banner øverst på siden, hvor du får besked.
3. Vælg **Overfør politikker** på banneret for at åbne overførselsguiden. Alle DLP-politikker for Exchange vises. Tidligere overflyttede politikker kan ikke vælges.
4. Vælg de politikker, du vil overføre. Du kan overføre dem individuelt eller i grupper ved hjælp af en faseinddelt tilgang eller på én gang. Vælg **Næste**.
5. Gennemse pop op-ruden for eventuelle advarsler eller meddelelser. Løs eventuelle problemer, før du fortsætter.
6. Vælg den tilstand, som den nye politik for Overholdelsescenter skal oprettes i, **Aktiv**, **Test** eller **Deaktiveret**.  Standarden er **Test**. Vælg **Næste**.
7. Hvis du vil, kan du oprette flere politikker, der er baseret på Exchange DLP-politikker for andre samlede DLP-placeringer. Dette resulterer i én ny samlet DLP-politik for den migrerede Exchange-politik og en ny samlet DLP-politik for alle andre placeringer, som du vælger her.

> [!IMPORTANT]
> Alle Exchange DLP-politikbetingelser og -handlinger, der ikke understøttes af andre DLP-placeringer, f.eks. enheder, SharePoint, OneDrive, lokalt miljø, MCAS eller Teams-chat og -kanalmeddelelser, fjernes fra den ekstra politik. Der er også præ-arbejde, der skal udføres for de andre placeringer. Se:
>- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
>- [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)
>- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)
>- [Få mere at vide om forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-learn.md)
>- [Kom i gang med forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-get-started.md)
>- [Brug Microsoft Purview-scanneren til forebyggelse af datatab i det lokale miljø](dlp-on-premises-scanner-use.md)
>- [Brug politikker til forebyggelse af datatab til cloudapps, der ikke er fra Microsoft](dlp-use-policies-non-microsoft-cloud-apps.md)
 
8. Gennemse indstillingerne for overførselsguidens session. Vælg **Næste**.
9. Gennemse overførselsrapporten. Vær opmærksom på eventuelle fejl, der involverer regler for Exchange-mailflow. Du kan løse dem og genmigrere de tilknyttede politikker.

De migrerede politikker vises nu på listen over DLP-politikker i DLP-konsollen i Compliance Center.

## <a name="common-errors-and-mitigation"></a>Almindelige fejl og afhjælpning

|Fejlmeddelelse|Grund|Afhjælpning/anbefalede trin|
|---|---|---|
|Der findes allerede en politik for overholdelse af regler og standarder med navnet `<Name of the policy>` i scenarier `Dlp`.|Det er sandsynligt, at denne politikoverførsel blev udført tidligere og derefter overvejet igen i den samme session|Opdater sessionen for at opdatere listen over politikker, der er tilgængelige for overførsel. Alle tidligere migrerede politikker skal være i `Already migrated` tilstanden .|
|Der findes allerede en politik for overholdelse af regler og standarder med navnet `<Name of the policy>` i scenarier `Hold`.|Der findes en opbevaringspolitik med det samme navn i den samme lejer.|– Omdøb DLP-politikken i EAC til et andet navn. </br> – Prøv at udføre overflytningen for den påvirkede politik igen.|
|`DLP-group@contoso.com` kan ikke bruges som en værdi for betingelsen Delt med, fordi det er en distributionsgruppe eller en mailaktiveret sikkerhedsgruppe. Brug Delt af prædikatets medlem til at registrere aktiviteter for medlemmer af visse grupper.|Transportregler tillader, at grupper bruges i betingelsen, `sender is` men unified DLP tillader det ikke.|Opdater transportreglen for at fjerne alle gruppemailadresser fra betingelsen `sender is` , og føj gruppen til betingelsen, hvis det `sender is a member of` er nødvendigt. Prøv at migrering for den påvirkede politik igen|
|Modtageren `DLP-group@contoso.com`blev ikke fundet. Hvis du lige har oprettet den, skal du prøve at udføre handlingen igen efter et tidspunkt. Hvis du har slettet eller udløbet, skal du nulstille med gyldige værdier og prøve igen.|Det er sandsynligt, at den gruppeadresse, der bruges i `sender is a member of` eller `recipient is a member of` betingelsen, er udløbet eller ugyldig.|– Fjern/erstat alle de ugyldige gruppemailadresser i transportreglen i Exchange Administration. </br> – Prøv at udføre overflytningen for den påvirkede politik igen.|
|Den værdi, der er angivet i `FromMemberOf` prædikat, skal være en mailaktiveret sikkerhedsgruppe.|Transportregler gør det muligt for individuelle brugere at blive brugt i betingelsen, `sender is a member of` men unified DLP tillader det ikke.|– Opdater transportreglen for at fjerne alle individuelle brugermailadresser fra betingelsen `sender is a member of` , og føj brugerne til betingelsen, hvis det `sender is` er nødvendigt. </br> – Prøv at udføre overflytningen for den påvirkede politik igen.|
|Den værdi, der er angivet i `SentToMemberOf` prædikat, skal være en mailaktiveret sikkerhedsgruppe.|Transportregler gør det muligt for individuelle brugere at blive brugt under betingelsen, `recipient is a member of` men unified DLP tillader det ikke.|– Opdater transportreglen for at fjerne alle individuelle brugermailadresser fra betingelsen `recipient is a member of` , og føj brugerne til betingelsen, hvis det `recipient is` er nødvendigt. </br> – Prøv at udføre overflytningen for den påvirkede politik igen.|
|`<Name of condition>` Brug af parameteren understøttes kun for Exchange. Fjern enten denne parameter, eller slå kun Exchange-placering til.|Det er sandsynligt, at der findes en anden politik med samme navn i Overholdelsescenter med andre placeringer, f.eks. SPO/ODB/Teams, hvor den nævnte betingelse ikke understøttes.|Omdøb DLP-politikken i Exchange Administration, og prøv at migrering igen.|

## <a name="testing-and-validation---prateek-and-aakash-to-provide-a-list-of-supported-predicates-and-known-issues-before-publishing--"></a>Test og validering <!--PRATEEK AND AAKASH TO PROVIDE A LIST OF SUPPORTED PREDICATES AND KNOWN ISSUES BEFORE PUBLISHING-->

Test og gennemse dine politikker.

1. Følg [procedurerne for test af en DLP-politik](create-test-tune-dlp-policy.md#test-a-dlp-policy) .
2. Gennemse de hændelser, der er oprettet af politikken i [Aktivitetsoversigt](data-classification-activity-explorer.md).

## <a name="review-the-policy-matches-between-exchange-admin-center-dlp-and-microsoft-purview-unified-dlp"></a>Gennemse politikforekomsterne mellem Exchange Administration Center DLP og Microsoft Purview Unified DLP

Hvis du vil sikre, at de migrerede politikker fungerer som forventet, kan du eksportere rapporterne fra begge administrationscentre og foretage en sammenligning af politikforekomsterne.

1. Opret forbindelse til [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).
2. Eksportér [EAC DLP-rapporten](/powershell/module/exchange/get-maildetaildlppolicyreport). Du kan kopiere denne cmdlet og indsætte de relevante værdier:

   ```powershell
   Get-MailDetailDlpPolicyReport -StartDate <dd/mm/yyyy -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, MessageId, DlpPolicy, TransportRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

3. Eksportér [Unified DLP-rapporten](/powershell/module/exchange/get-dlpdetailreport). Du kan kopiere denne cmdlet og indsætte de relevante værdier:

   ```powershell
   Get-DlpDetailReport -StartDate <dd/mm/yyyy> -EndDate <dd/mm/yyyy> -PageSize 5000 | select Date, Location, DlpCompliancePolicy, DlpComplianceRule -Unique | Export-CSV <"C:\path\filename.csv">
   ```

## <a name="activate-your-migrated-policies"></a>Aktivér dine migrerede politikker

Når du er tilfreds med, hvordan dine migrerede politikker fungerer, kan du angive dem til **Gennemtving**.

1. Åbn Exchange Administration Center DLP-konsollen.
2. Deaktiver eller slet kildepolitikken.
3. Åbn [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/datalossprevention?viewid=policies) DLP-konsollen, og vælg den politik, du vil gøre aktiv for at redigere den.
4. Skift status til **Slå** til.

## <a name="related-articles"></a>Relaterede artikler

- [Exchange Online politikker til forebyggelse af datatab](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
- [Exchange Online politikker til forebyggelse af datatab](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
