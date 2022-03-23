---
title: Begræns utilsigtet eksponering
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
ms.custom: admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du begrænser utilsigtet eksponering af oplysninger, når du deler filer med personer uden for organisationen.
ms.openlocfilehash: c1bf6424e2be70118dd2d85671a857a8a33ef2f9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589409"
---
# <a name="limit-accidental-exposure-to-files-when-sharing-with-people-outside-your-organization"></a>Begræns utilsigtet eksponering af filer ved deling med personer uden for organisationen

Når du deler filer og mapper med personer uden for organisationen, er der forskellige muligheder for at reducere risikoen for utilsigtet deling af følsomme oplysninger. Du kan vælge mellem indstillingerne i denne artikel, så de bedst opfylder organisationens behov.

## <a name="use-best-practices-for-anyone-links"></a>Brug af bedste fremgangsmåder for alle-links

Hvis personer i din organisation har brug for ikke-godkendt deling, men du er bekymret over ikke-godkendte personer, der redigerer indhold, skal du læse Bedste fremgangsmåder [for](best-practices-anonymous-sharing.md) ikke-godkendt deling for at få vejledning i, hvordan du arbejder med ikke-godkendt deling i organisationen.

## <a name="turn-off-anyone-links"></a>Deaktivere alle links

Vi anbefaler, at *alle links er* aktiveret for det relevante indhold, da det er den nemmeste måde at dele og kan hjælpe med at reducere risikoen for, at brugerne søger efter andre løsninger, som ikke er under it-afdelingens kontrol. *Alle* links kan videresendes til andre, men adgang til filer er kun tilgængelig for dem, der har linket.

Hvis du altid vil have personer uden for organisationen til at godkende, når de tilgår indhold i SharePoint, grupper eller Teams, kan du deaktivere *Alle*, der deler. Dette vil forhindre brugere i ikke-godkendt deling af indhold.

Hvis du *deaktiverer alle* links, kan brugere stadig nemt dele med gæster ved hjælp af *links til Bestemte* personer. I dette tilfælde skal alle personer uden for organisationen godkendes, før de kan få adgang til det delte indhold.

Afhængigt af dine behov kan du deaktivere *Alle-links* for bestemte websteder eller for hele organisationen.

Sådan deaktiverer *du Alle-links* for organisationen

1. I SharePoint Administration skal du i venstre navigationsrude vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
2. Angiv indstillingerne SharePoint for ekstern deling til **Nye og eksisterende gæster**.

   ![Skærmbillede af niveauet på organisationsniveau SharePoint indstillingerne for ekstern deling på webstedet.](../media/sharepoint-organization-external-sharing-controls-new-users.png)

3. Klik på **Gem**.

Sådan deaktiverer du *alle* links for et websted

1. På siden SharePoint administration skal du i venstre navigationsrude **udvide Websteder** og vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
2. Vælg det websted, du vil konfigurere.
3. Vælg Deling på **båndet**.
4. Sørg for, at deling er **indstillet til Nye og eksisterende gæster**.

   ![Skærmbillede af indstillinger for ekstern deling SharePoint webstedsniveau.](../media/sharepoint-site-external-sharing-settings.png)

5. Hvis du har foretaget ændringer, skal du vælge **Gem**.

## <a name="domain-filtering"></a>Domænefiltrering

Du kan bruge lister over tilladte domæner eller afvisning til at angive, hvilke domæner brugerne kan bruge, når de deler med personer uden for organisationen.

Med en tilladelsesliste kan du angive en liste over domæner, hvor brugere i organisationen kan dele med personer uden for organisationen. Deling med andre domæner er blokeret. Hvis din organisation kun samarbejder med personer fra en liste over bestemte domæner, kan du bruge denne funktion til at forhindre deling med andre domæner.

Med en afvisningsliste kan du angive en liste over domæner, hvor brugerne i organisationen ikke kan dele med personer uden for organisationen. Deling med de angivne domæner er blokeret. Dette kan være nyttigt, hvis du har konkurrenter, f.eks. hvem du vil forhindre i at få adgang til indhold i organisationen.

Listerne Tillad og Afvisning påvirker kun deling med gæster. Brugere kan stadig dele med personer fra forbudte domæner ved hjælp *af alle* links, hvis du ikke har deaktiveret dem. Du opnår de bedste resultater med lister over tilladte domæner og afvisning ved at deaktivere *alle* links som beskrevet ovenfor.

Sådan konfigurerer du en liste til tillad eller afvisning af et domæne

1. I SharePoint Administration skal du i venstre navigationsrude vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>
2. Markér **afkrydsningsfeltet Begræns** ekstern deling efter domæne under **Avancerede** indstillinger for ekstern deling.
3. Klik **på Tilføj domæner**.
4. Vælg, om du vil blokere domæner, skriv domænerne, og klik på **OK**.

   ![Skærmbillede af SharePoint at begrænse ekstern deling efter domæneindstilling.](../media/sharepoint-sharing-block-domain.png)

5. Klik på **Gem**.

Hvis du vil begrænse deling efter domæne på et højere niveau end SharePoint og OneDrive, kan du tillade eller blokere [invitationer til B2B-brugere](/azure/active-directory/b2b/allow-deny-list) fra bestemte organisationer i Azure Active Directory. (Du skal konfigurere [SharePoint og OneDrive integration med Azure AD B2B Preview](/sharepoint/sharepoint-azureb2b-integration-preview), for at disse indstillinger påvirker SharePoint og OneDrive).

## <a name="limit-sharing-of-files-folders-and-sites-with-people-outside-your-organization-to-specified-security-groups"></a>Begræns deling af filer, mapper og websteder med personer uden for organisationen til angivne sikkerhedsgrupper

Du kan begrænse deling af filer, mapper og websteder med personer uden for organisationen til medlemmer af en bestemt sikkerhedsgruppe. Dette er nyttigt, hvis du vil aktivere ekstern deling, men med en arbejdsproces til godkendelse eller anmodningsproces. Alternativt kan du kræve, at brugerne skal gennemføre et kursus, før de føjes til sikkerhedsgruppen og har tilladelse til at dele eksternt.

Sådan begrænser du ekstern deling til medlemmer af en sikkerhedsgruppe

1. I SharePoint administration skal du i venstre navigationsrude **vælge** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling under Politikker**</a>.
2. **Udvid Flere** indstillinger for **ekstern deling under Ekstern deling**.

3. Vælg **Tillad kun brugere i bestemte sikkerhedsgrupper at dele eksternt**, og vælg derefter **Administrer sikkerhedsgrupper**.

    ![Skærmbillede af panelet Administrer sikkerhedsgrupper.](/sharepoint/sharepointonline/media/manage-security-groups.png)

4. I feltet **Tilføj en sikkerhedsgruppe** skal du skrive et navn til en sikkerhedsgruppe. Feltet sikkerhedsgruppe vises.

5. Ud for navnet på sikkerhedsgruppen skal du **på rullelisten Kan** dele med vælge enten:

    - **Kun godkendte gæster** (standard)
    - **Alle**

6. Vælg **Gem**.

Bemærk, at dette påvirker filer, mapper og websteder, men ikke Microsoft 365 grupper eller Teams. Når medlemmer inviterer gæster til en privat Microsoft 365 gruppe eller et privat team i Microsoft Teams, sendes invitationen til godkendelse i gruppen eller teamejeren.

## <a name="see-also"></a>Se også

[Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)

[Bedste fremgangsmåder for deling af filer og mapper med anonyme brugere](best-practices-anonymous-sharing.md)
