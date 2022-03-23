---
title: Samarbejd med gæster om et dokument
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
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: I denne artikel lærer du, hvordan du kan samarbejde med gæster om et dokument i SharePoint og OneDrive.
ms.openlocfilehash: f27c47403e63c19bf341c69d8dffbe2ea450e1d4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590033"
---
# <a name="collaborate-with-guests-on-a-document"></a>Samarbejd med gæster om et dokument

Hvis du har brug for at samarbejde med personer uden for organisationen om dokumenter i SharePoint eller OneDrive, kan du sende dem et delingslink til dokumentet. I denne artikel gennemgår vi de Microsoft 365 konfigurationstrin, der er nødvendige for at konfigurere delingslinks til SharePoint og OneDrive til organisationens behov.

## <a name="video-demonstration"></a>Videodemonstration

Denne video viser de konfigurationstrin, der er beskrevet i dette dokument.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Indstillinger for eksternt Azure-samarbejde

Deling i Microsoft 365 er underlagt indstillingerne for eksternt [samarbejde i B2B](/azure/active-directory/external-identities/delegate-invitations) på højeste niveau Azure Active Directory. Hvis gæstedeling er deaktiveret eller begrænset i Azure AD, tilsidesætter denne indstilling eventuelle indstillinger for deling, som du konfigurerer i Microsoft 365.

Kontrollér indstillingerne for eksternt samarbejde i B2B for at sikre, at deling med gæster ikke er blokeret.

![Skærmbillede af Azure Active Directory siden Organisationsrelationer Indstillinger organisationsrelationer.](../media/azure-ad-organizational-relationships-settings.png)

Sådan angives indstillinger for eksternt samarbejde

1. Log på Azure Active Directory på [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. I venstre navigationsrude skal du klikke **på Azure Active Directory**.
3. Klik **på Eksterne identiteter**.
4. Klik på **Indstillinger for** eksternt samarbejde i venstre **navigationsrude på skærmbilledet Introduktion**.
5. Sørg for,  at medlemsbrugere og brugere, der er tildelt bestemte administratorroller, kan invitere gæstebrugere, herunder gæster med medlemstilladelser eller Alle i organisationen kan invitere gæstebrugere, herunder gæster og **ikke-administratorer**, er markeret.
6. Hvis du har foretaget ændringer, skal du klikke **på Gem**.

Bemærk indstillingerne i **sektionen Begrænsninger for** samarbejde. Sørg for, at domænerne for de gæster, du vil samarbejde med, ikke blokeres.

Hvis du arbejder med gæster fra flere organisationer, kan det være en ide at begrænse deres mulighed for at få adgang til katalogdata. Dette forhindrer dem i at se, hvem der ellers er gæst i kataloget. For at gøre **dette skal du** under Begrænsninger for gæstebrugeradgang vælge Gæstebrugere har begrænset adgang til egenskaber og medlemskab af indstillingerne for katalogobjekter eller Gæstebrugeradgang er begrænset til egenskaber og medlemskaber af deres egne **katalogobjekter**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint indstillinger for deling på organisationsniveau

Hvis personer uden for organisationen skal have adgang til et dokument i SharePoint eller OneDrive, skal indstillingerne for deling på SharePoint- og OneDrive-organisationsniveau tillade deling med personer uden for organisationen.

Indstillingerne på organisationsniveau for SharePoint de indstillinger, der vil være tilgængelige for individuelle SharePoint websteder. Webstedsindstillinger kan ikke være mere tilladelige end indstillingerne på organisationsniveau. Indstillingen på organisationsniveau for OneDrive af delingsniveauet, der vil være tilgængeligt i brugernes OneDrive biblioteker.

Hvis SharePoint og OneDrive tillader ikke-godkendt fil- og mappedeling, skal du vælge **Alle**. Hvis du vil sikre dig, at personer uden for organisationen skal godkendes, skal du **vælge Ny og eksisterende gæster**. *Alle* links er den nemmeste måde at dele det på: personer uden for organisationen kan åbne linket uden godkendelse og kan frit videregive det til andre.

Hvis SharePoint, skal du vælge den mest diskrete indstilling, der vil være nødvendig for et websted i din organisation.

![Skærmbillede af SharePoint af indstillinger for deling på organisationsniveau.](../media/sharepoint-organization-external-sharing-controls.png)


Sådan angives SharePoint indstillinger for deling på organisationsniveau

1. Klik Microsoft 365 Administration administration i venstre navigationsrude **under** **SharePoint**.
2. I SharePoint Administration i venstre navigationsrude under **Politikker skal** du vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
3. Sørg for, at ekstern deling for SharePoint eller OneDrive er **indstillet til Alle** **eller Ny og eksisterende gæster**. Bemærk, at OneDrive ikke kan være mere vedholdende end SharePoint indstilling.
4. Hvis du har foretaget ændringer, skal du vælge **Gem**.

## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint standardlinkindstillinger på organisationsniveau

Standardindstillingerne for fil- og mappelink bestemmer den linkindstilling, der vises til brugerne som standard, når de deler en fil eller mappe. Brugere kan ændre linktypen til en af de andre indstillinger før deling, hvis det ønskes.

Husk på, at denne indstilling SharePoint websteder i organisationen samt OneDrive.

Vælg et link fra en af følgende typer, som derefter vælges som standard, når brugere deler filer og mapper:

- **Alle med linket –** Vælg denne indstilling, hvis du forventer at udføre en masse ikke-godkendt fil- og mappedeling. Hvis du vil tillade *Alle* links, men er bekymrede for utilsigtet deling, skal du overveje en af de andre muligheder som standard. Denne linktype er kun tilgængelig, hvis du har aktiveret **Alle, der deler** .
- **Kun personer i din organisation –** Vælg denne indstilling, hvis du forventer, at det meste af fil- og mappedeling er med personer inden for organisationen.
- **Bestemte personer** – Overvej denne indstilling, hvis du forventer at gøre en masse fil- og mappedeling med gæster. Denne type link fungerer sammen med gæster og kræver, at de godkender.
 
![Skærmbillede af SharePoint af filer og mapper på organisationsniveau.](../media/sharepoint-organization-files-folders-sharing-settings.png)


Sådan angives linkindstillingerne SharePoint OneDrive på organisationsniveau

1. Gå <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**til**</a> Deling SharePoint Administration.
2. Under **Fil- og mappelinks** skal du vælge det standardlink til deling, du vil bruge.
3. Hvis du har foretaget ændringer, skal du klikke **på Gem**.

Hvis du vil angive tilladelsen for delingslinket, skal **du under Vælg den tilladelse, der er valgt som standard for deling af links.**

1. Vælg **Vis** , hvis ikke ikke-godkendte brugere skal foretage ændringer i filer og mapper.
2. Vælg **Rediger** , hvis du vil tillade, at ikke-godkendte brugere foretager ændringer i filer og mapper.

Bemærk, at de to ovenstående muligheder kan anvendes ikke kun for gæster/eksterne brugere, men også for interne brugere. Den valgte tilladelsesindstilling bestemmes efter eget skøn.

Sådan angives tilladelser for links, der tillader deling med alle

1. Under **disse links kan du få disse tilladelser:** underrude, 
    1. Fra **rullelisten** Filer skal du 
        - Vælg **Vis og rediger** , hvis du vil tillade, at ikke-godkendte brugere foretager ændringer i filerne.
        - Vælg **Vis** , hvis ikke ikke-godkendte brugere skal foretage ændringer i filerne.
    2. På **rullelisten** Mapper skal du
        - Vælg **Vis, rediger og upload** , hvis du vil tillade, at ikke-godkendte brugere foretager ændringer i mapperne.
        - Vælg **Vis** , hvis ikke ikke-godkendte brugere skal foretage ændringer i mapperne.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint indstillinger for deling på webstedsniveau

Hvis du deler filer og mapper, der er på et SharePoint-websted, skal du også kontrollere indstillingerne for deling på webstedsniveau for det pågældende websted.

![Skærmbillede af SharePoint indstillingerne for ekstern deling på webstedet.](../media/sharepoint-site-external-sharing-settings.png)

Sådan angives indstillinger for deling på webstedsniveau

1. På siden SharePoint Administration i venstre navigationsrude skal du **udvide Websteder** og vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
2. Vælg det websted, hvor du vil dele filer og mapper med gæster.
3. Rul til højre på rækken (hvor det valgte websted er til stede), og klik et vilkårligt sted i **kolonnen Ekstern** deling.
4. Klik på fanen Politikker på den side, **der vises** .
5. Klik på **Rediger under** ruden **Ekstern deling**.
6. Sørg for, at deling er **indstillet til** Alle **eller Ny og eksisterende gæster**.
7. Hvis du har foretaget ændringer, skal du klikke **på Gem**.

## <a name="invite-users"></a>Inviter brugere

Indstillingerne for gæstedeling er nu konfigureret. Så brugerne nu kan dele filer og mapper med personer uden for organisationen. Se [Del OneDrive og mapper og Del filer](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) [SharePoint mapper](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for at få flere oplysninger.

## <a name="see-also"></a>Se også

[Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)

[Begræns utilsigtet eksponering af filer, når du deler med gæster](share-limit-accidental-exposure.md)

[SharePoint- og OneDrive-integration med Azure Active Directory B2B](/sharepoint/sharepoint-azureb2b-integration-preview)
