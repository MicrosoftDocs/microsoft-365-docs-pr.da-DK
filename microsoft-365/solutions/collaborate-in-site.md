---
title: Samarbejd med gæster på et websted
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
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
description: Få mere at vide Microsoft 365 konfigurationstrin, der er nødvendige for at konfigurere SharePoint websted til samarbejde med gæster.
ms.openlocfilehash: 7187149324f88c64570549429f86291320431566
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588608"
---
# <a name="collaborate-with-guests-in-a-site"></a>Samarbejd med gæster på et websted

Hvis du har brug for at samarbejde med gæster på tværs af dokumenter, data og lister, kan du bruge SharePoint websted. Moderne SharePoint websteder har forbindelse til Microsoft 365-grupper og kan administrere medlemskabet af webstedet og give yderligere samarbejdsværktøjer, f.eks. en delt postkasse og en kalender.

I denne artikel gennemgår vi de Microsoft 365 trin til konfiguration for at konfigurere et SharePoint til samarbejde med gæster.

## <a name="video-demonstration"></a>Videodemonstration

Denne video viser de konfigurationstrin, der er beskrevet i dette dokument.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Indstillinger for eksternt Azure-samarbejde

Deling i Microsoft 365 er underlagt indstillingerne for eksternt [samarbejde i B2B](/azure/active-directory/external-identities/delegate-invitations) på højeste niveau Azure Active Directory. Hvis gæstedeling er deaktiveret eller begrænset i Azure AD, tilsidesætter denne indstilling eventuelle indstillinger for deling, som du konfigurerer i Microsoft 365.

Kontrollér indstillingerne for eksternt samarbejde i B2B for at sikre, at deling med gæster ikke er blokeret.

![Skærmbillede Azure Active Directory siden Eksternt Indstillinger samarbejde.](../media/azure-ad-organizational-relationships-settings.png)

Sådan angives indstillinger for eksternt samarbejde

1. Log på Azure Active Directory på [https://aad.portal.azure.com](https://aad.portal.azure.com).
2. I venstre navigationsrude skal du klikke **på Azure Active Directory**.
3. Klik **på Eksterne identiteter**.
4. Klik på **Indstillinger for** eksternt samarbejde i venstre **navigationsrude på skærmbilledet Introduktion**.
5. Sørg for,  at medlemsbrugere og brugere, der er tildelt bestemte administratorroller, kan invitere gæstebrugere, herunder gæster med medlemstilladelser eller Alle i organisationen kan invitere gæstebrugere, herunder gæster og **ikke-administratorer**, er markeret.
6. Hvis du har foretaget ændringer, skal du klikke **på Gem**.

Bemærk indstillingerne i **sektionen Begrænsninger for** samarbejde. Sørg for, at domænerne for de gæster, du vil samarbejde med, ikke blokeres.

Hvis du arbejder med gæster fra flere organisationer, kan det være en ide at begrænse deres mulighed for at få adgang til katalogdata. Dette forhindrer dem i at se, hvem der ellers er gæst i kataloget. For at gøre **dette skal du** under Begrænsninger for gæstebrugeradgang vælge Gæstebrugere har begrænset adgang til egenskaber og medlemskab af indstillingerne for katalogobjekter eller Gæstebrugeradgang er begrænset til egenskaber og medlemskaber af deres egne **katalogobjekter**.

## <a name="microsoft-365-groups-guest-settings"></a>Microsoft 365 gruppegæstindstillinger

Moderne SharePoint websteder bruger Microsoft 365 grupper til at kontrollere adgangen til webstedet. Gæsteindstillingerne Microsoft 365 Grupper skal være slået til, for at gæsteadgang på SharePoint kan fungere.

![Skærmbillede af Microsoft 365 i Grupper i Microsoft 365 Administration.](../media/office-365-groups-guest-settings.png)

Sådan angives Microsoft 365 gruppegæstindstillinger

1. I Microsoft 365 Administration i venstre navigationsrude skal du udvide **Indstillinger**.
2. Klik **på Org-indstillinger**.
3. Klik på Grupper på **Microsoft 365 listen**.
4. Sørg for, at afkrydsningsfelterne Lad gruppeejere føje personer **uden for organisationen til Microsoft 365 Grupper** som gæster og Lad **gæstegruppemedlemmer** få adgang til gruppeindhold begge er markeret.
5. Hvis du har foretaget ændringer, skal du klikke **på Gem ændringer**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint indstillinger for deling på organisationsniveau

For at gæster kan få adgang til SharePoint websteder, skal SharePoint indstillinger for deling på organisationsniveau tillade deling med gæster.

Indstillingerne på organisationsniveau bestemmer de indstillinger, der vil være tilgængelige for individuelle websteder. Webstedsindstillinger kan ikke være mere tilladelige end indstillingerne på organisationsniveau.

Hvis du vil tillade ikke-godkendt fil- og mappedeling, skal du vælge **Alle**. Hvis du vil sikre dig, at alle personer uden for organisationen skal godkendes, skal du **vælge Ny og eksisterende gæster**. Vælg den mest diskrete indstilling, der vil være nødvendig for et websted i organisationen.

![Skærmbillede af SharePoint af indstillinger for deling på organisationsniveau.](../media/sharepoint-organization-external-sharing-controls.png)


Sådan angives SharePoint indstillinger for deling på organisationsniveau

1. Vælg Microsoft 365 Administration i venstre navigationsrude under **Administration** for **at SharePoint**.
2. I SharePoint Administration i venstre navigationsrude under **Politikker skal** du vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
3. Sørg for, at ekstern deling for SharePoint er indstillet **til Alle** **eller Ny og eksisterende gæster**.
4. Hvis du har foretaget ændringer, skal du vælge **Gem**.

## <a name="create-a-site"></a>Opret et websted

Næste trin er at oprette det websted, du vil bruge til at samarbejde med gæster.

Sådan opretter du et websted
1. Vælg aktive SharePoint i **Administration** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>.
2. Vælg **Opret**.
3. Vælg **Teamwebsted**.
4. Skriv navnet på webstedet, og skriv et navn til gruppeejeren (ejeren af webstedet).
5. Under **Avancerede indstillinger** skal du vælge, om dette websted skal være offentligt eller privat.
6. Vælg **Næste**.
7. Vælg **Udfør**.

Vi inviterer brugere senere. Dernæst er det vigtigt at kontrollere indstillingerne for deling på webstedsniveau for dette websted.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint indstillinger for deling på webstedsniveau

Kontrollér indstillingerne for deling på webstedsniveau for at sikre, at de tillader den type adgang, du ønsker for dette websted. Hvis du f.eks. angiver indstillingerne på organisationsniveau til **Alle, men** du vil have alle gæster til at godkende for dette websted, skal du sørge for, at indstillingerne for deling på webstedsniveau er angivet til Ny og **eksisterende gæster**.

Bemærk, at webstedet ikke kan deles med ikke-godkendte personer (**indstillingen** Alle), men det kan individuelle filer og mapper.

Du kan også bruge [følsomhedsmærkater til at kontrollere indstillinger for ekstern deling for SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

![Skærmbillede af SharePoint indstillingerne for ekstern deling på webstedet.](../media/sharepoint-site-external-sharing-settings.png)

Sådan angives indstillinger for deling på webstedsniveau
1. På siden SharePoint administration skal du i venstre navigationsrude **udvide Websteder** og vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
2. Vælg det websted, du vil dele.
3. Vælg ..., og vælg **Deling**.
4. Sørg for, at deling er **indstillet til** Alle **eller Ny og eksisterende gæster**.
5. Hvis du har foretaget ændringer, skal du vælge **Gem**.

## <a name="invite-users"></a>Inviter brugere

Indstillingerne for gæstedeling er nu konfigureret, så du kan begynde at tilføje interne brugere og gæster til dit websted. Adgang til webstedet styres via den tilknyttede Microsoft 365 gruppe, så vi tilføjer brugere der.

Sådan inviteres interne brugere til en gruppe

1. Gå til det websted, hvor du vil tilføje brugere.
2. Vælg **linket** Medlemmer øverst til højre, som angiver antallet af medlemmer.
3. Vælg **Tilføj medlemmer**.
4. Skriv navnene eller mailadresserne på de brugere, du vil invitere til webstedet, og vælg derefter **Gem**.

Gæster kan ikke tilføjes fra webstedet. Du skal tilføje dem ved hjælp af Outlook på internettet. Som en forudsætning for at tilføje og invitere gæster til en gruppe skal du derfor klikke på URL-adressen for webstedet i **kolonnen URL-adresse**  for at gå til den webstedsspecifikke side. Klik på ikonet for **appstarteren på denne side**, og **vælg Outlook**. Dette er den skærm, hvorfra du kan invitere gæster til en gruppe, og proceduren er beskrevet nedenfor.

Sådan inviterer du gæster til en gruppe
1. Klik **på** den gruppe, du vil invitere gæster til, under Grupper.
2. Åbn gruppens visitkort, klik på **linket** Medlemmer øverst til højre (det link, der angiver antallet af medlemmer).
3. skal **du klikke på Tilføj medlemmer**.
4. Skriv mailadresserne på de gæster, du vil invitere, og klik derefter på **Tilføj**.
5. Klik **på Luk**.
Bemærk, at du kun skal  klikke på Luk, hvis du ikke er ejeren af gruppen, og du derfor ikke har tilladelse til at tilføje gæsten i gruppen. I sådanne tilfælde overføres anmodningen om at føje gæsten til gruppen til gruppeejeren til godkendelse.

## <a name="see-also"></a>Se også

[Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)

[Begræns utilsigtet eksponering af filer, når du deler med gæster](share-limit-accidental-exposure.md)

[Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)

[Opret et B2B-ekstranet med administrerede gæster](b2b-extranet.md)

[SharePoint- og OneDrive-integration med Azure Active Directory B2B](/sharepoint/sharepoint-azureb2b-integration-preview)
