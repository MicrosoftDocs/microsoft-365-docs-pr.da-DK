---
title: Bedste fremgangsmåder for ikke-godkendt deling
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: I denne artikel får du mere at vide om de bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere.
ms.openlocfilehash: 4541f1b6021c5d58f27366bb508ccdaa216010d9
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63590034"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a>Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere

Ikke-godkendt deling (*Alle-links* ) kan være praktiske og nyttige i forskellige scenarier. *Alle* links er den nemmeste måde at dele det på: Folk kan åbne linket uden godkendelse og kan frit videregive det til andre.

Normalt er ikke alt indhold i en organisation egnet til ikke-godkendt deling. Denne artikel omhandler de muligheder, der kan hjælpe dig med at oprette et miljø, hvor dine brugere kan bruge ikke-godkendt deling af filer og mapper, men hvor der er indført sikkerhedsforanstaltninger for at beskytte din organisations indhold.

> [!NOTE]
> For at ikke-godkendt deling kan fungere, skal du aktivere det for din organisation og for det individuelle websted eller team, du bruger. Se [Samarbejde med personer uden for organisationen](collaborate-with-people-outside-your-organization.md) for det scenarie, du vil aktivere.

## <a name="set-an-expiration-date-for-anyone-links"></a>Angiv en udløbsdato for alle links

Filer gemmes ofte på websteder, grupper og teams i længere tid. Nogle gange er der dataopbevaringspolitikker, der kræver, at filer opbevares i flere år. Hvis sådanne filer deles med ikke-godkendte personer, kan det føre til uventet adgang og ændringer af filer i fremtiden. For at reducere denne mulighed kan du konfigurere et udløbstidspunkt for *alle-links* .

Når et *Alle-link* udløber, kan det ikke længere bruges til at få adgang til indhold.

Sådan angives en udløbsdato for alle links på tværs af organisationen

1. Åbn SharePoint Administration, udvid **Politikker**, og vælg derefter <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
1. Markér **afkrydsningsfeltet Disse links skal udløbe inden for dette** antal dage under Vælg udløbs- og tilladelsesindstillinger **for** alle links.</br>
   ![Skærmbillede af SharePoint på organisationsniveau. Udløbsindstillinger for Alle-links.](../media/sharepoint-organization-anyone-link-expiration.png)
1. Skriv et antal dage i feltet, og klik derefter på **Gem**.

Sådan angiver du en udløbsdato for alle links på et bestemt websted

1. Åbn SharePoint Administration, udvid **Websteder**, og vælg derefter <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
1. Vælg det websted, du vil ændre, og vælg derefter **Deling**.
1. Fjern **markeringen i afkrydsningsfeltet Samme** som **indstilling på organisationsniveau under** Avancerede indstillinger for alle links under Udløb af **alle** links.</br>
   ![Skærmbillede af SharePoint på webstedsniveau. Udløbsindstillinger for Alle-links.](../media/sharepoint-organization-anyone-link-expiration-site.png)
1. Vælg indstillingen **Disse links skal udløbe inden for dette antal** dage, og skriv et antal dage i feltet.
1. Vælg **Gem**.

Bemærk, at når *linket* Alle udløber, kan filen eller mappen deles igen med et nyt *Alle-link* .

Du kan angive *Udløb for Alle-link* for en bestemt OneDrive ved hjælp [af Set-SPOSite](/powershell/module/sharepoint-online/set-sposite).

## <a name="set-link-permissions"></a>Angiv linktilladelser

Som standard giver *Alle* links til en fil brugerne mulighed for at redigere filen, og *Alle-links* til en mappe giver brugerne mulighed for at redigere og få vist filer samt overføre nye filer til mappen. Du kan ændre disse tilladelser for filer og mapper uafhængigt af visning.

Hvis du vil tillade ikke-godkendt deling, men er bekymret over ikke-godkendte personer, der redigerer din organisations indhold, bør du overveje at indstille fil- og mappetilladelser til **Vis**.

Sådan angives tilladelser for alle links på tværs af organisationen

1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
1. Under **Avancerede indstillinger for links af "Alle"** skal du vælge de fil- og mappetilladelser, du vil bruge.</br>
   ![Skærmbillede af SharePoint af tilladelsesindstillingerne for Alle links på organisationsniveau.](../media/sharepoint-organization-anyone-link-permissions.png)

Med *alle* links angivet til **Vis** kan brugere stadig dele filer og mapper med gæster og give dem redigeringstilladelser ved hjælp af links *til Bestemte* personer. Disse links kræver, at personer uden for organisationen godkender som gæster, og du kan spore og overvåge gæsteaktivitet på filer og mapper, der deles med disse links.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Angiv standardlinktypen til kun at fungere for personer i organisationen

Når *Alle* deling er aktiveret for din organisation, er standardlinket til deling normalt indstillet til **Alle**. Selvom det kan være praktisk for brugerne, kan det øge risikoen for utilsigtet ikke-godkendt deling. Hvis en bruger glemmer at ændre linktypen, mens de deler et følsomt dokument, kan de ved en fejl oprette et delingslink, der ikke kræver godkendelse.

Du kan reducere risikoen ved at ændre standardindstillingen for linket til et link, der kun fungerer for personer inden for organisationen. Brugere, der vil dele med ikke-godkendte personer, skal derefter specifikt vælge den indstilling.

Sådan angives standardlinket til fil- og mappedeling for organisationen
1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
1. Under **Fil- og mappelinks** skal **du vælge Kun personer i organisationen**.

   ![Skærmbillede af SharePoint af standardindstillingen for linktyper.](../media/sharepoint-default-sharing-link-company-link.png)

1. Vælg **Gem**

Sådan angives standardlinket til fil- og mappedeling for et bestemt websted

1. Åbn SharePoint Administration, udvid **Websteder**, og vælg derefter <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
1. Vælg det websted, du vil ændre, og vælg derefter **Deling**.
1. Fjern **markeringen i afkrydsningsfeltet** Samme som indstilling **på organisationsniveau under Standardtype for delingslink** .

   ![Skærmbillede af SharePoint af standardindstillingerne for linktyper på webstedsniveau.](../media/sharepoint-organization-anyone-link-permissions-site.png)

1. Vælg indstillingen **Kun personer i din** organisation, og vælg derefter **Gem**.

## <a name="prevent-unauthenticated-sharing-of-sensitive-content"></a>Undgå ikke-godkendt deling af følsomt indhold

Du kan bruge [forebyggelse af datatab (DLP)](../compliance/dlp-learn-about-dlp.md) til at forhindre ikke-godkendt deling af følsomt indhold. Forebyggelse af datatab kan handle baseret på en fils følsomhedsmærkat, opbevaringsmærkat eller følsomme oplysninger i selve filen.

Sådan oprettes en DLP-regel
1. I Microsoft 365 administration af overholdelse skal du gå til siden [til forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention).
2. Klik **på Opret politik**.
3. Vælg **Brugerdefineret** , og klik **på Næste**.
4. Skriv et navn til politikken, og klik på **Næste**.
5. På siden **Placeringer for at anvende** politik deaktiveres alle indstillinger undtagen SharePoint **websteder** og **OneDrive konti**, og klik derefter på **Næste**.
6. Klik på **Næste på siden** Definer **politikindstillinger**.
7. På siden **Tilpas avancerede DLP-regler** skal du **klikke på Opret** regel og skrive et navn til reglen.
8. Under **Betingelser** skal du klikke **på Tilføj** betingelse og vælge **Indhold indeholder**.
9. Klik **på** Tilføj, og vælg den type oplysninger, du vil forhindre ikke-godkendt deling for.

   ![Skærmbillede af indstillinger for betingelser, følsomme oplysningstyper, følsomhedsmærkater og opbevaringsmærkater.](../media/limit-accidental-exposure-dlp-conditions.png)

10. Under **Handlinger** skal **du klikke på Tilføj** en **handling og vælge Begræns adgang eller kryptere indholdet Microsoft 365 placeringer**.
11. Markér **afkrydsningsfeltet Begræns** adgang eller kryptér indholdet på Microsoft 365-placeringer, og vælg derefter indstillingen Kun de personer, der har fået adgang til indholdet via indstillingen **"** Alle med linket".

      ![Skærmbillede af handlingsindstillinger for DLP-regel.](../media/limit-accidental-exposure-dlp-anyone-links.png)

12. Klik **på Gem** , og klik derefter **på Næste**.
13. Vælg dine testindstillinger, og klik på **Næste**.
14. Klik **på Send**, og klik derefter på **Udført**.

## <a name="protect-against-malicious-files"></a>Beskyt dig mod skadelige filer

Når du tillader anonyme brugere at uploade filer, er der en øget risiko for, at nogen uploader en skadelig fil. I Microsoft 365 kan du bruge funktionen *Pengeskab Vedhæftede* filer i Defender til Office 365 til automatisk at scanne uploadede filer og sætte filer i karantæne, der findes usikre.

Sådan aktiverer du sikrede vedhæftede filer
1. Åbn siden [ATP Pengeskab vedhæftede filer](https://protection.office.com/safeattachmentv2) i Security and Compliance Administration.
2. Klik **på Globale indstillinger**.
3. Slå ATP til for SharePoint, OneDrive og Microsoft Teams.

   ![Skærmbillede af indstillingen for sikrede vedhæftede filer i Security and Compliance Center.](../media/safe-attachments-setting.png)

4. Du kan også slå Pengeskab Dokumenter til og derefter klikke på **Gem**

Se [ATP for at SharePoint, OneDrive og Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md) at slå [ATP til for at få SharePoint, OneDrive og Microsoft Teams for at](../security/office-365-security/turn-on-mdo-for-spo-odb-and-teams.md) få yderligere vejledning.

## <a name="add-copyright-information-to-your-files"></a>Føj copyrightoplysninger til dine filer

Hvis du bruger følsomhedsmærkater i Microsoft 365 Compliance Administration, kan du konfigurere dine etiketter til automatisk at tilføje et vandmærke eller et sidehoved eller en sidefod i din organisations Office dokumenter. På denne måde kan du sikre dig, at delte filer indeholder oplysninger om ophavsret eller andre ejerskabsoplysninger.

Sådan føjer du en sidefod til en mærket fil

1. Åbn Microsoft 365 [Administration for overholdelse af regler og standarder](https://compliance.microsoft.com).
2. Klik på Beskyttelse af oplysninger under **Løsninger i** venstre **navigationsrude**.
3. Klik på den etiket, du vil have til at tilføje en sidefod, og klik derefter på **Rediger etiket**.
4. Klik **på Næste** for at gå **til fanen Indholdsmærkning** , og slå derefter **Aktivér indholdsmærkning** .
5. Markér afkrydsningsfeltet for den teksttype, du vil tilføje, og klik derefter på **Tilpas tekst**.
6. Skriv den tekst, du vil føje til dine dokumenter, vælg de ønskede tekstindstillinger, og klik derefter på **Gem**.</br>
   ![Skærmbillede af indstillingerne for indholdsmærkning for en følsomhedsmærkat.](../media/content-marking-for-anonymous-sharing.png)
7. Klik **på** Næste for at komme til slutningen af guiden, og klik derefter **på Gem etiket**.

Når indholdsmærkning er aktiveret for etiketten, føjes den angivne tekst til Office dokumenter, når en bruger anvender den pågældende etiket.

## <a name="see-also"></a>Se også

[Oversigt over følsomhedsmærkater](/Office365/SecurityCompliance/sensitivity-labels)

[Begræns utilsigtet eksponering af filer, når du deler med gæster](share-limit-accidental-exposure.md)

[Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)
