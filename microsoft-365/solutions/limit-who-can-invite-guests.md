---
title: Begræns, hvem der kan invitere gæster
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan du begrænser, hvem der kan invitere gæster til din organisation.
ms.openlocfilehash: d8eb9452abb76916940d10fa042dae479358568a
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63717300"
---
# <a name="limit-who-can-invite-guests"></a>Begræns, hvem der kan invitere gæster

Du kan begrænse, hvem i organisationen der kan invitere gæster. Gæstekonti kan bruges til at dele teams, SharePoint, filer og mapper med personer uden for organisationen.

Hvis dine forretningsprocesser kræver, at du begrænser, hvem der kan dele med gæster, eller hvis du ønsker, at brugerne skal gennemføre træningen, før de kan dele med gæster, kan du begrænse, hvem der kan dele ved hjælp af rollen Gæste inviterer i Azure Active Directory.

## <a name="create-a-security-group-for-people-allowed-to-invite-guests"></a>Opret en sikkerhedsgruppe for personer, der har tilladelse til at invitere gæster

Det første trin er at oprette en sikkerhedsgruppe for de brugere, der skal have tilladelse til at invitere gæster. Sørg for at konfigurere denne gruppe til at tillade en Azure AD-rolle, og tildel den derefter rollen Gæste inviterer.

Sådan opretter du en sikkerhedsgruppe for gæsteinvitatorer
1. Log på Azure Active Directory [en](https://aad.portal.azure.com) Global administrator- eller sikkerhedsadministratorkonto.
1. På siden **Active Directory** skal du vælge **Grupper** og derefter vælge **Ny gruppe**.
1. Vælg **Sikkerhed** for **typen Gruppe**.
1. Skriv et **Gruppenavn.** 
1. Du kan også tilføje en beskrivelse af gruppen.
1. For **Azure AD-roller kan tildeles til gruppen skal** du vælge **Ja**.
1. Tilføj gruppeejere og -medlemmer.
1. Under **Roller skal** du vælge **Ingen roller markeret**.
1. Søg efter og vælg rollen **Gæste inviterer** , og vælg derefter **Vælg**.
1. Vælg **Opret**, og bekræft, at du vil have en gruppe, hvilke roller der kan tildeles. Din gruppe er oprettet og klar til, at du kan tilføje medlemmer.

## <a name="configure-external-collaboration-settings"></a>Konfigurere indstillinger for eksternt samarbejde

Når du har oprettet sikkerhedsgruppen og tilføjet de brugere, der skal kunne invitere gæster, er næste trin at konfigurere indstillingerne for eksternt samarbejde i Azure AD til kun at tillade brugere med rollen Gæsteinvitator at invitere gæster.

Bemærk, at globale administratorer altid kan invitere gæster uanset denne indstilling.

> [!NOTE]
> Ændringer af adgangsindstillinger for flere lejere kan tage to timer, før de træder i kraft.

Sådan konfigureres Azure AD til at begrænse gæsteinvitationer til rollen Gæsteinvitator
1. I [Azure Active Directory](https://aad.portal.azure.com/) skal du **vælge Eksterne identiteter**.
1. Vælg **Indstillinger for eksternt samarbejde**.
1. Under **Indstillinger for gæste inviteres** skal du **vælge Kun brugere, der er tildelt bestemte administratorroller kan invitere gæster**.
1. Vælg **Gem**.

## <a name="related-topics"></a>Relaterede emner

[Tillad kun brugere i bestemte sikkerhedsgrupper at dele eksternt i SharePoint og OneDrive](/sharepoint/manage-security-groups)

[Aktivér eksternt B2B-samarbejde, og administrer, hvem der kan invitere gæster](/azure/active-directory/external-identities/delegate-invitations)