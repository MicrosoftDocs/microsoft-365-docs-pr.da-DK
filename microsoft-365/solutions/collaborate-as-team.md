---
title: Samarbejd med gæster i et team
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
- admindeeplinkMAC
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide Microsoft 365 konfigurationstrin, der er nødvendige for at konfigurere et team til samarbejde om opgaver, samtaler og dokumentation med gæster Teams.
ms.openlocfilehash: bb6ccf4f3e17192d86675d99072eca8b836973e2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588184"
---
# <a name="collaborate-with-guests-in-a-team"></a>Samarbejd med gæster i et team

Hvis du har brug for at samarbejde med gæster på tværs af dokumenter, opgaver og samtaler, anbefaler vi, at du bruger Microsoft Teams. Teams indeholder alle de samarbejdsfunktioner, der er tilgængelige i Office og SharePoint med fast chat samt en brugerdefinerbar og udvidet sæt samarbejdsværktøjer i en samlet brugeroplevelse.

I denne artikel gennemgår vi de mest Microsoft 365 konfigurationstrin for at konfigurere et team til samarbejde med gæster. Når du har konfigureret gæsteadgang, kan du invitere gæster til teams ved at følge trinnene i Føj gæster til [et team Teams](https://support.microsoft.com/office/fccb4fa6-f864-4508-bdde-256e7384a14f).

## <a name="video-demonstration"></a>Videodemonstration

Denne video viser de konfigurationstrin, der er beskrevet i dette dokument.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

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

## <a name="teams-guest-access-settings"></a>Teams indstillinger for gæsteadgang

Teams har en master til/fra-knap til gæsteadgang og en række indstillinger, der er tilgængelige til at styre, hvad gæster kan gøre i et team. Masterskiftet Tillad **gæsteadgang i Teams** **være til**, for at gæsteadgang kan fungere i Teams.

Kontrollér, at gæsteadgang er aktiveret i Teams og foretag eventuelle ændringer af gæsteindstillingerne baseret på virksomhedens behov. Husk, at disse indstillinger påvirker alle teams.

![Skærmbillede af Teams til/fra-knap for gæsteadgang.](../media/teams-guest-access-toggle-on.png)

Sådan angives Teams indstillingerne for gæsteadgang

1. Log på Microsoft 365 Administration på [https://admin.microsoft.com](https://admin.microsoft.com).
2. Klik på Vis alle i venstre **navigationsrude**.
3. Under **Administration skal** du klikke **på Teams**.
4. I Teams Administration skal du i venstre navigationsrude **vælge Adgang for** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**UsersGuest**</a> > .
5. Sørg for **, at Tillad gæsteadgang Teams** er indstillet til **Til**.
6. Foretag de ønskede ændringer af de ekstra gæsteindstillinger, og klik derefter på **Gem**.

Når Teams er slået til, kan du vælge at styre gæsteadgang til individuelle teams og deres tilknyttede SharePoint ved hjælp af følsomhedsmærkater. Få mere at vide under [Brug følsomhedsmærkater til at beskytte indhold Microsoft Teams, Microsoft 365, grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!NOTE]
> Det kan tage op til 24 timer, Teams indstillingerne for gæster bliver aktive, efter du har aktiveret dem.

## <a name="microsoft-365-groups-guest-settings"></a>Microsoft 365 gruppegæstindstillinger

Teams bruger Microsoft 365 grupper til teammedlemskab. Gæsteindstillingerne Microsoft 365 Grupper skal være slået til, for at gæsteadgang i Teams at fungere.

![Skærmbillede af Microsoft 365 i Grupper i Microsoft 365 Administration.](../media/office-365-groups-guest-settings.png)

Sådan angives Microsoft 365 gruppegæstindstillinger

1. I Microsoft 365 Administration i venstre navigationsrude skal du udvide **Indstillinger**.
2. Klik **på Org-indstillinger**.
3. Klik på Grupper på **Microsoft 365 listen**.
4. Sørg for, at afkrydsningsfelterne Lad gruppeejere føje personer **uden for organisationen til Microsoft 365 Grupper** som gæster og Lad **gæstegruppemedlemmer** få adgang til gruppeindhold begge er markeret.
5. Hvis du har foretaget ændringer, skal du klikke **på Gem ændringer**.


## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint indstillinger for deling på organisationsniveau

Teams indhold som filer, mapper og lister gemmes alle i SharePoint. For at gæster kan få adgang til disse elementer i Teams, skal SharePoint indstillinger for deling på organisationsniveau tillade deling med gæster.

Indstillingerne på organisationsniveau afgør, hvilke indstillinger der er tilgængelige for individuelle websteder, herunder websteder, der er knyttet til teams. Webstedsindstillinger kan ikke være mere tilladelige end indstillingerne på organisationsniveau.

Hvis du vil tillade fil- og mappedeling med ikke-godkendte personer, skal du vælge **Alle**. Hvis du vil sikre dig, at alle gæster skal godkendes, skal du **vælge Ny og eksisterende gæster**. Vælg den mest diskrete indstilling, der vil være nødvendig for et websted i organisationen.

![Skærmbillede af SharePoint af indstillinger for deling på organisationsniveau.](../media/sharepoint-organization-external-sharing-controls.png)


Sådan angives SharePoint indstillinger for deling på organisationsniveau

1. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> i venstre navigationsrude under **Administration for** at **SharePoint**.
2. I SharePoint Administration i venstre navigationsrude skal du udvide **Politikker** og derefter vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Deling**</a>.
3. Sørg for, at ekstern deling for SharePoint er indstillet **til Alle** **eller Ny og eksisterende gæster**.
4. Hvis du har foretaget ændringer, skal du vælge **Gem**.


## <a name="sharepoint-organization-level-default-link-settings"></a>SharePoint standardlinkindstillinger på organisationsniveau

Standardindstillingerne for fil- og mappelink bestemmer den linkindstilling, der vises til brugerne som standard, når de deler en fil eller mappe. Brugere kan ændre linktypen til en af de andre indstillinger før deling, hvis det ønskes.

Husk, at denne indstilling påvirker alle teams og SharePoint i organisationen.

Vælg en af følgende linktyper, der som standard vælges, når brugere deler filer og mapper:

- **Alle med linket** – Vælg denne indstilling, hvis du forventer at udføre en masse ikke-godkendt deling af filer og mapper. Hvis du vil tillade *Alle* links, men er bekymrede for utilsigtet deling, skal du overveje en af de andre muligheder som standard. Denne linktype er kun tilgængelig, hvis du har aktiveret **Alle, der deler** .
- **Kun personer i din organisation –** Vælg denne indstilling, hvis du forventer, at det meste af fil- og mappedeling er med personer inden for organisationen.
- **Bestemte personer** – Overvej denne indstilling, hvis du forventer at gøre en masse fil- og mappedeling med gæster. Denne type link fungerer sammen med gæster og kræver, at de godkender.
 
![Skærmbillede af SharePoint af filer og mapper på organisationsniveau.](../media/sharepoint-organization-files-folders-sharing-settings.png)


Sådan angives SharePoint standardlinkindstillingerne på organisationsniveau

1. Gå <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**til**</a> Deling SharePoint Administration.
2. Under **Fil- og mappelinks** skal du vælge det standardlink til deling, du vil bruge.
3. Hvis du har foretaget ændringer, skal du vælge **Gem**.

## <a name="create-a-team"></a>Opret et team

Næste trin er at oprette det team, som du planlægger at bruge til at samarbejde med gæster.

Sådan opretter du et team
1. I Teams skal du **Teams** på Deltag i eller opret et **team** nederst i venstre rude.
2. Klik **på Opret et team**.
3. Klik **på Opret et team fra bunden**.
4. Vælg **Privat** eller **Offentlig**.
5. Skriv et navn og en beskrivelse af teamet, og klik derefter på **Opret**.
6. Klik **på Spring over**.

Vi inviterer brugere senere. Dernæst er det vigtigt at kontrollere indstillingerne for deling på webstedsniveau for det SharePoint, der er knyttet til teamet.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint indstillinger for deling på webstedsniveau

Kontrollér indstillingerne for deling på webstedsniveau for at sikre, at de tillader den type adgang, du ønsker for dette team. Hvis du f.eks. angiver indstillingerne på organisationsniveau til **Alle, men** du vil have alle gæster til at godkende for dette team, skal du sørge for, at indstillingerne for deling på webstedsniveau er angivet til Nye og **eksisterende gæster**.

![Skærmbillede af SharePoint indstillingerne for ekstern deling på webstedet.](../media/sharepoint-site-external-sharing-settings.png)

Sådan angives indstillinger for deling på webstedsniveau
1. På siden SharePoint Administration i venstre navigationsrude skal du **udvide Websteder** og vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a>.
2. Vælg webstedet for det team, du lige har oprettet.
3. Vælg ... og vælg **Deling**.
4. Sørg for, at deling er **indstillet til** Alle **eller Ny og eksisterende gæster**.
5. Hvis du har foretaget ændringer, skal du vælge **Gem**.

## <a name="invite-users"></a>Inviter brugere

Indstillingerne for gæstedeling er nu konfigureret, så du kan begynde at tilføje interne brugere og gæster til dit team. 

Sådan inviteres interne brugere til et team
1. I teamet skal du klikke **på Flere indstillinger** (**\*\*\***) og derefter klikke på **Tilføj medlem**.
2. Skriv navnet på den person, du vil invitere.
3. Klik **på Tilføj**, og klik derefter på **Luk**.

Sådan inviterer du gæster til et team
1. I teamet skal du klikke **på Flere indstillinger** (**\*\*\***) og derefter klikke på **Tilføj medlem**.
2. Skriv mailadressen på den gæst, du vil invitere.
3. Klik **på Rediger gæsteoplysninger**.
4. Skriv gæstens fulde navn, og klik på markeringen.
5. Klik **på Tilføj**, og klik derefter på **Luk**.

> [!NOTE]
> Gæster med en arbejds- eller skolekonto kan kun inviteres ved hjælp af brugerens hovednavn (UPN) (f.eks adele@contoso.com). Invitation af gæster ved hjælp af EAS-id eller andre mailformater understøttes ikke.

## <a name="see-also"></a>Se også

[Bedste fremgangsmåder for deling af filer og mapper med ikke-godkendte brugere](best-practices-anonymous-sharing.md)

[Begræns utilsigtet eksponering af filer, når du deler med gæster](share-limit-accidental-exposure.md)

[Opret et sikkert miljø for gæstedeling](create-secure-guest-sharing-environment.md)

[Opret et B2B-ekstranet med administrerede gæster](b2b-extranet.md)

[SharePoint- og OneDrive-integration med Azure Active Directory B2B](/sharepoint/sharepoint-azureb2b-integration-preview)

[Delingsindstillinger nedtones, når du deler fra SharePoint eller OneDrive](/sharepoint/troubleshoot/administration/sharing-options-grayed-out-when-sharing-from-sharepoint-online-or-onedrive)
