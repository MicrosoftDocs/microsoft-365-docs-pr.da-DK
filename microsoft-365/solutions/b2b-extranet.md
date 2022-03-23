---
title: Opret et B2B-ekstranet med administrerede gæster
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
ms.custom: ''
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du opretter et B2B-ekstranetwebsted eller -team med administrerede gæster fra en partnerorganisation.
ms.openlocfilehash: ab8bba31538b9e79ed198f65349f14d8211f81f7
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588397"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a>Opret et B2B-ekstranet med administrerede gæster

Du kan bruge [Azure Active Directory rettighedsstyring](/azure/active-directory/governance/entitlement-management-overview) til at oprette et B2B-ekstranet til at samarbejde med en partnerorganisation, der bruger Azure Active Directory. Dette giver brugerne mulighed for selv at tilmelde sig ekstranetwebstedet eller -teamet og få adgang via en arbejdsproces til godkendelse.

Med denne metode til deling af ressourcer til samarbejde kan partnerorganisationen hjælpe med at vedligeholde og godkende gæster på deres afslutning, hvilket reducerer belastningen på din it-afdeling og gør det muligt for dem, der er mest fortrolige med samarbejdsaftalen, at administrere brugeradgang.

I denne artikel gennemgås trinnene til oprettelse af en pakke med ressourcer (i dette tilfælde et websted eller team), som du kan dele med en partnerorganisation via en selvbetjeningsregistreringsmodel for adgang. 

Før du begynder, skal du oprette det websted eller team, du vil dele med partnerorganisationen, og aktivere gæstedeling. Se [Samarbejd med gæster på et websted eller Samarbejd](collaborate-in-site.md) [med gæster i et team for at](collaborate-as-team.md) få flere oplysninger. Vi anbefaler også, at du gennemgår [Opret](create-secure-guest-sharing-environment.md) et sikkert miljø for gæstedeling for at få oplysninger om funktioner til sikkerhed og overholdelse af regler og standarder, som du kan bruge til at opretholde dine styringspolitikker, når du samarbejder med gæster.

## <a name="license-requirements"></a>Licenskrav

Brug af denne funktion kræver en Azure AD Premium P2-licens. 

Specialiserede skyer, f.eks. Azure Germany og Azure China 21Vianet, er i øjeblikket ikke tilgængelige til brug.

## <a name="video-demonstration"></a>Videodemonstration

Denne video viser de procedurer, der er dækket af denne artikel.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4wKUj?autoplay=false]

## <a name="connect-the-partner-organization"></a>Forbind partnerorganisationen

Hvis du vil invitere gæster fra en partnerorganisation, skal du tilføje partnerens domæne som en forbundet organisation i Azure Active Directory.

Sådan tilføjer du en forbundet organisation
1. Klik [Azure Active Directory](https://aad.portal.azure.com) styring af identitet **under fanen Indstillinger**.
2. Klik **på Forbundne organisationer**.
4. Klik **på Tilføj tilknyttet organisation**.
5. Skriv et navn og en beskrivelse af organisationen, og klik derefter **på Næste: Mappe + domæne**.
6. Klik **på Tilføj mappe + domæne**.
7. Skriv domænet for den organisation, du vil oprette forbindelse til, og klik derefter på **Tilføj**.
8. Klik **Forbind**, og klik derefter **på Næste: Sponsorer**.
9. Tilføj personer fra din organisation eller den organisation, du opretter forbindelse til, til hvem du vil godkende adgang for gæster.
10. Klik **på Næste: Gennemse + Opret**.
11. Gennemgå de indstillinger, du har valgt, og klik derefter på **Opret**.

    ![Skærmbillede af siden forbundne organisationer i Azure Active Directory.](../media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a>Vælg de ressourcer, du vil dele

Det første trin i at vælge ressourcer at dele med en partnerorganisation er at oprette et katalog, der indeholder dem.

Sådan opretter du et katalog
1. Klik [Azure Active Directory](https://aad.portal.azure.com) styring af identitet **under fanen Indstillinger**.
2. Klik **på Kataloger**.
3. Klik **på Nyt katalog**.
4. Skriv et navn og en beskrivelse af kataloget, og sørg for, at **Aktiveret** **og Aktiveret for eksterne** brugere begge er indstillet til **Ja**.
5. Klik **på Opret**.

   ![Skærmbillede af katalogsiden i Azure Active Directory styring af identitet.](../media/identity-governance-catalogs.png)

Når kataloget er blevet oprettet, skal du tilføje det SharePoint websted eller team, du vil dele med partnerorganisationen.

Sådan føjer du ressourcer til et katalog
1. I Azure AD Identity Governance skal du klikke **på Kataloger** og derefter klikke på det katalog, hvor du vil tilføje ressourcer.
2. Klik **på Ressourcer** , og klik derefter **på Tilføj ressourcer**.
3. Vælg de teams eller SharePoint, du vil medtage i dit ekstranet, og klik derefter på **Tilføj**.

   ![Skærmbillede af siden katalogressourcer i Azure Active Directory styring af identitet.](../media/identity-governance-catalog-resource.png)

Når du har defineret de ressourcer, du vil dele, er næste trin at oprette en adgangspakke, som definerer den type adgang, som partnerbrugere tildeles, og godkendelsesprocessen for nye partnerbrugere, der anmoder om adgang.

Sådan opretter du en adgangspakke
1. I Azure AD Identity Governance skal du klikke på Kataloger og derefter klikke på det katalog, hvor du vil oprette en **adgangspakke**.
2. Klik **på Access-pakker**, og klik derefter **på Ny adgangspakke**.
3. Skriv et navn og en beskrivelse af adgangspakken, og klik derefter på **Næste: Ressourceroller**.
4. Vælg ressourcerne fra det katalog, du vil bruge til dit ekstranet.
5. For hver ressource skal du i **kolonnen** Rolle vælge den brugerrolle, du vil tildele til de gæster, der bruger ekstranet.
6. Klik **på Næste: Anmodninger**.
7. Under **Brugere, der kan anmode om adgang** skal du **vælge For brugere, der ikke er i dit katalog**.
8. Sørg for, **at indstillingen Bestemte forbundne** organisationer er markeret, og klik derefter **på Tilføj mapper**.
9. Vælg den forbundne organisation, du tilføjer tidligere, og klik derefter på **Vælg**
10. Under **Godkendelse skal** du **vælge Ja** til **Kræv godkendelse**.
11. Under **First approver skal** du vælge en af de sponsorer, du tilføjede tidligere, eller vælge en bestemt bruger.
12. Klik **på Tilføj reserve,** og vælg en godkender af reserve.
13. Vælg **Ja** under **Aktivér**.
14. Klik **på Næste: Livscyklus**.
15. Vælg de indstillinger for udløb og adgang til gennemsyn, du vil bruge, og klik derefter **på Næste: Gennemse + Opret**.
16. Gennemse dine indstillinger, og klik derefter på **Opret**.

    ![Skærmbillede af skærmen adgangspakker i Azure Active Directory styring af identitet.](../media/identity-governance-access-packages.png)

Hvis du samarbejder med en stor organisation, kan det være en god ide at skjule adgangspakken. Hvis pakken er skjult, vil brugerne i partnerorganisationen ikke kunne se pakken på deres *Min Access-portal* . I stedet skal de sendes et direkte link for at tilmelde sig pakken. Hvis du skjuler adgangspakken, kan det reducere antallet af upassende anmodninger om adgang og kan også hjælpe med at holde tilgængelige adgangspakker organiseret på partnerorganisationens portal.

Sådan angives en adgangspakke til skjult
1. I Azure AD Identity Governance skal du klikke **på Access-pakker** og derefter klikke på din adgangspakke.
2. Klik på **Rediger** på siden **Oversigt**.
3. Under **Egenskaber** skal du **vælge Ja** for **Skjult** og derefter klikke på **Gem**.

   ![Skærmbillede af skærmbilledet rediger egenskaber for adgangspakke.](../media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a>Inviter partnerbrugere

Hvis du indstiller adgangspakken til skjult, skal du sende et direkte link til partnerorganisationen, så de kan anmode om adgang til dit websted eller team.

Sådan finder du adgangsportallinket
1. I Azure AD Identity Governance skal du klikke **på Access-pakker** og derefter klikke på din adgangspakke.
2. Klik på **Kopiér** til **udklipsholderlink** til linket **Min Access-portal på siden Oversigt**.

   ![Skærmbillede af egenskaber for adgang til pakke med adgangsportallink.](../media/identity-governance-access-portal-link.png)

Når du har kopieret linket, kan du dele det med din kontakt i partnerorganisationen, og de kan sende det til brugerne på deres samarbejdsteam.

## <a name="see-also"></a>Se også

[Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)