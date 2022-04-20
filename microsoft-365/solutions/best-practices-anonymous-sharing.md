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
description: I denne artikel får du mere at vide om de bedste fremgangsmåder til deling af filer og mapper med ikke-godkendte brugere.
ms.openlocfilehash: ca6b75ba036aac826d657c8c907b512fe9d1f87a
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948369"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a>Bedste praksis for deling af filer og mapper med ikke-godkendte brugere

Ikke-godkendt deling (*alle* links) kan være praktisk og nyttig i forskellige scenarier. *Alle* links er den nemmeste måde at dele på: Folk kan åbne linket uden godkendelse og kan frit sende det til andre.

Normalt er ikke alt indhold i en organisation egnet til ikke-godkendt deling. I denne artikel beskrives de tilgængelige indstillinger, der kan hjælpe dig med at oprette et miljø, hvor dine brugere kan bruge ikke-godkendt deling af filer og mapper, men hvor der er sikkerhedsforanstaltninger på plads for at beskytte din organisations indhold.

> [!NOTE]
> Hvis ikke-godkendt deling skal fungere, skal du aktivere den for din organisation og for det individuelle websted eller team, du bruger. Se [Samarbejde med personer uden for din organisation](collaborate-with-people-outside-your-organization.md) for at se det scenarie, du vil aktivere.

## <a name="set-an-expiration-date-for-anyone-links"></a>Angiv en udløbsdato for links til alle

Filer gemmes ofte på websteder, i grupper og i teams i længere tid. Nogle gange er der politikker for dataopbevaring, der kræver, at filer bevares i årevis. Hvis sådanne filer deles med ikke-godkendte personer, kan det medføre uventet adgang og ændringer af filer i fremtiden. Hvis du vil afhjælpe denne mulighed, kan du konfigurere en udløbstid for *alle* links.

Når et link *af typen Alle* udløber, kan det ikke længere bruges til at få adgang til indhold.

Sådan angiver du en udløbsdato for alle links på tværs af organisationen

1. Åbn SharePoint Administration, udvid **Politikker**, og vælg derefter <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
1. Under **Vælg indstillinger for udløb og tilladelser for alle links** skal du markere afkrydsningsfeltet **Disse links skal udløbe inden for dette antal dage** .</br>
   ![Skærmbillede af SharePoint udløbsindstillinger for alle links på organisationsniveau.](../media/sharepoint-organization-anyone-link-expiration.png)
1. Skriv et antal dage i feltet, og klik derefter på **Gem**.

Sådan angiver du en udløbsdato for links til alle på et bestemt websted

1. Åbn SharePoint Administration, udvid **Websteder**, og vælg derefter <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
1. Vælg det websted, du vil ændre, og vælg derefter **Deling**.
1. Fjern markeringen i **afkrydsningsfeltet** **Samme som indstilling på organisationsniveau** under **Avancerede indstillinger for alle links**.</br>
   ![Skærmbillede af SharePoint indstillinger for udløb af links på webstedsniveau.](../media/sharepoint-organization-anyone-link-expiration-site.png)
1. Vælg indstillingen **Disse links skal udløbe inden for dette antal dage** , og skriv et antal dage i feltet.
1. Vælg **Gem**.

Bemærk, at når et link af typen *Alle* udløber, kan filen eller mappen deles igen med et nyt link *af typen Alle* .

Du kan angive udløb af *linket Alle* for en bestemt OneDrive ved hjælp af [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite).

## <a name="set-link-permissions"></a>Angiv linktilladelser

Som standard tillader *Alle* links til en fil, at andre kan redigere filen, og *alle* links til en mappe gør det muligt for andre at redigere og få vist filer og overføre nye filer til mappen. Du kan ændre disse tilladelser for filer og mapper uafhængigt af hinanden, så de kun vises.

Hvis du vil tillade ikke-godkendt deling, men er bekymret for ikke-godkendte personer, der ændrer organisationens indhold, kan du overveje at angive fil- og mappetilladelserne til **Vis**.

Sådan angiver du tilladelser for alle links på tværs af organisationen

1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
1. Under **Avancerede indstillinger for links til "Alle"** skal du vælge de fil- og mappetilladelser, du vil bruge.</br>
   ![Skærmbillede af SharePoint indstillinger for linktilladelser på organisationsniveau.](../media/sharepoint-organization-anyone-link-permissions.png)

Når *Alle links er* angivet til **Vis**, kan brugerne stadig dele filer og mapper med gæster og give dem redigeringstilladelser ved hjælp af *links til bestemte personer* . Disse links kræver, at personer uden for din organisation godkendes som gæster, og du kan spore og overvåge gæsteaktivitet for filer og mapper, der deles med disse links.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Angiv standardlinktypen til kun at arbejde for personer i din organisation

Når *Alle-deling* er aktiveret for din organisation, er standardlinket til deling normalt angivet til **Alle**. Selvom dette kan være praktisk for brugerne, kan det øge risikoen for utilsigtet ikke-godkendt deling. Hvis en bruger glemmer at ændre linktypen, mens vedkommende deler et følsomt dokument, kan vedkommende ved et uheld oprette et delingslink, der ikke kræver godkendelse.

Du kan afhjælpe denne risiko ved at ændre standardindstillingen for links til et link, der kun fungerer for personer i din organisation. Brugere, der vil dele med ikke-godkendte personer, skal derefter specifikt vælge denne indstilling.

Sådan angiver du standardlinket til fil- og mappedeling for organisationen
1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
1. Under **Fil- og mappelinks** skal du vælge **Kun personer i din organisation**.

   ![Skærmbillede af SharePoint indstilling for standardlinktype.](../media/sharepoint-default-sharing-link-company-link.png)

1. Vælg **Gem**

Sådan angiver du standardlinket til fil- og mappedeling for et bestemt websted

1. Åbn SharePoint Administration, udvid **Websteder**, og vælg derefter <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
1. Vælg det websted, du vil ændre, og vælg derefter **Deling**.
1. Fjern markeringen i afkrydsningsfeltet **Samme som indstilling på organisationsniveau** under **Standardlinktype for deling**.

   ![Skærmbillede af SharePoint indstillinger for standardlinktype på webstedsniveau.](../media/sharepoint-organization-anyone-link-permissions-site.png)

1. Vælg indstillingen **Kun personer i din organisation** , og vælg derefter **Gem**.

## <a name="prevent-unauthenticated-sharing-of-sensitive-content"></a>Undgå ikke-godkendt deling af følsomt indhold

Du kan bruge [Microsoft Purview DLP (forebyggelse af datatab)](../compliance/dlp-learn-about-dlp.md) til at forhindre ikke-godkendt deling af følsomt indhold. Forebyggelse af datatab kan udføre handlinger på baggrund af en fils følsomhedsmærkat, opbevaringsmærkat eller følsomme oplysninger i selve filen.

Sådan opretter du en DLP-regel
1. I Microsoft Purview Administration skal du gå til [siden til forebyggelse af datatab](https://compliance.microsoft.com/datalossprevention).
2. Klik på **Opret politik**.
3. Vælg **Brugerdefineret,** og klik på **Næste**.
4. Skriv et navn til politikken, og klik på **Næste**.
5. Slå alle indstillinger fra på **siden Placeringer for at anvende politikken**, undtagen **SharePoint websteder** og **OneDrive konti**, og klik derefter på **Næste**.
6. Klik på **Næste** på siden **Definer politikindstillinger**.
7. På siden **Tilpas avancerede DLP-regler** skal du klikke på **Opret regel** og skrive et navn til reglen.
8. Under **Betingelser** skal du klikke på **Tilføj betingelse** og vælge **Indhold indeholder**.
9. Klik på **Tilføj** , og vælg den type oplysninger, du vil forhindre ikke-godkendt deling for.

   ![Skærmbillede af indstillinger for betingelser, typer af følsomme oplysninger, følsomhedsmærkater og opbevaringsmærkater.](../media/limit-accidental-exposure-dlp-conditions.png)

10. Klik på **Tilføj en handling** under **Handlinger**, og vælg **Begræns adgang, eller kryptér indholdet på Microsoft 365 placeringer**.
11. Markér afkrydsningsfeltet **Begræns adgang til eller kryptér indholdet på Microsoft 365 placeringer**, og vælg derefter indstillingen **Kun personer, der har fået adgang til indholdet via indstillingen "Alle med linket"**.

      ![Skærmbillede af indstillinger for DLP-regelhandlinger.](../media/limit-accidental-exposure-dlp-anyone-links.png)

12. Klik på **Gem** , og klik derefter på **Næste**.
13. Vælg dine testindstillinger, og klik på **Næste**.
14. Klik på **Send**, og klik derefter på **Udført**.

## <a name="protect-against-malicious-files"></a>Beskyt mod skadelige filer

Når du tillader anonyme brugere at uploade filer, er der en øget risiko for, at nogen uploader en skadelig fil. I Microsoft 365 kan du bruge funktionen *Pengeskab vedhæftede filer* i Defender for Office 365 til automatisk at scanne uploadede filer og sætte filer i karantæne, der er usikre.

Sådan slår du sikre vedhæftede filer til
1. Åbn [siden Vedhæftede filer i ATP-Pengeskab](https://protection.office.com/safeattachmentv2) i Administration af sikkerhed og overholdelse.
2. Klik på **Globale indstillinger**.
3. Slå ATP til for SharePoint, OneDrive og Microsoft Teams.

   ![Skærmbillede af indstillingen for sikre vedhæftede filer i Security and Compliance Center.](../media/safe-attachments-setting.png)

4. Du kan også slå Pengeskab dokumenter til og derefter klikke på **Gem**

Se [ATP for at få SharePoint, OneDrive og Microsoft Teams](../security/office-365-security/mdo-for-spo-odb-and-teams.md) og [Slå ATP til for at få SharePoint, OneDrive og Microsoft Teams](../security/office-365-security/turn-on-mdo-for-spo-odb-and-teams.md) for at få yderligere vejledning.

## <a name="add-copyright-information-to-your-files"></a>Føj oplysninger om ophavsret til dine filer

Hvis du bruger følsomhedsmærkater i Microsoft Purview Administration, kan du konfigurere mærkaterne til automatisk at føje et vandmærke eller et sidehoved eller en sidefod til organisationens Office dokumenter. På denne måde kan du sikre dig, at delte filer indeholder oplysninger om ophavsret eller andre ejerskabsoplysninger.

Sådan føjer du en sidefod til en navngivet fil

1. Åbn [Microsoft Purview Administration](https://compliance.microsoft.com).
2. Klik på **Information Protection** under **Løsninger** i venstre navigationsrude.
3. Klik på den etiket, du vil have tilføjet en sidefod, og klik derefter på **Rediger etiket**.
4. Klik på **Næste** for at nå fanen **Indholdsmarkering** , **og slå derefter** indholdsmarkering til.
5. Markér afkrydsningsfeltet for den type tekst, du vil tilføje, og klik derefter på **Tilpas tekst**.
6. Skriv den tekst, du vil føje til dine dokumenter, markér de ønskede tekstindstillinger, og klik derefter på **Gem**.</br>
   ![Skærmbillede af indstillingerne for indholdsmarkering for en følsomhedsmærkat.](../media/content-marking-for-anonymous-sharing.png)
7. Klik på **Næste** for at nå slutningen af guiden, og klik derefter på **Gem navn**.

Når indholdsmarkering er aktiveret for etiketten, føjes den angivne tekst til Office dokumenter, når en bruger anvender denne etiket.

## <a name="see-also"></a>Se også

[Oversigt over følsomhedsmærkater](/Office365/SecurityCompliance/sensitivity-labels)

[Begræns utilsigtet eksponering for filer, når der deles med gæster](share-limit-accidental-exposure.md)

[Opret et sikkert gæstedelingsmiljø](create-secure-guest-sharing-environment.md)
