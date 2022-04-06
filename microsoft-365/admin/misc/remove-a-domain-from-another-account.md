---
title: Fjern et domæne fra en anden konto
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: b9707ec8-2247-4e25-9bad-f11ddbc686e4
description: Få mere at vide om, hvordan du tilmelder dig en ikke-administreret konto, der er oprettet af en selvbetjeningsbruger til Microsoft 365.
ms.openlocfilehash: 0a7cf07a70e241c0b40f28159f31b0c86766bc1d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606825"
---
# <a name="perform-an-internal-admin-takeover"></a>Udføre en intern administratorovertagelse

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

Hvis du er administrator og vil overtage en ikke-administreret konto, der er oprettet ved tilmelding via selvbetjeningsbruger, kan du gøre dette ved at udføre en intern administratorovertagelse.

> [!NOTE]
> En tilmelding til en skytjeneste, der bruger Azure AD, føjer brugeren til en ikke-administreret mappe eller en "skygge"-mappe i Azure AD og opretter en ikke-administreret konto. En ikke-administreret konto er en mappe uden en global administrator. Hvis du vil afgøre, om en konto er administreret eller ikke-administreret, skal [du se Fastslå lejertype](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type). 
  
## <a name="before-you-begin"></a>Før du begynder

Nogle gange kan du ikke føje et domæne til din organisationskonto, fordi en anden allerede har tilmeldt sig Microsoft 365 via en mailadresse, der er knyttet til det pågældende domænenavn. Men du kan fjerne domænet fra den anden konto, der ikke er administreret, og føje det til din organisations administrerede konto.

Før du kan fjerne domænet fra den anden konto og føje det til din konto, skal du dog tilslutte dig den ikke-administrerede konto og blive administrator for den pågældende konto. Derefter skal du fjerne domænet fra den ikke-administrerede konto, logge på din konto igen og føje domænet til din administrerede konto.

Trinnene i denne artikel beskriver kun, hvordan du opretter forbindelse til den anden konto (trin 1 og 2) og følger trinnene i guiden til administratorovertagelse for at blive administrator på den ikke-administrerede konto (trin 3).

Når du er blevet administrator for den ikke-administrerede konto, kan du fjerne domænet fra den ikke-administrerede konto og føje det til din konto. 

## <a name="step-1-verify-your-email-address"></a>Trin 1: Bekræft din mailadresse

> [!NOTE]
> Hvis selvbetjening er aktiveret på din konto, kan brugerne abonnere på gratis tjenester som f.Power BI, selv. Disse tjenester er specifikt til brug i tilfælde, hvor et brugerabonnement til selvbetjening har oprettet den ikke-administrerede konto, du vil overtage som administrator. I trin 1 opretter du en brugerkonto til det domæne, du vil fjerne, ved hjælp af Power BI for at starte guiden til administratorovertagelse, så du kan blive administrator for den ikke-administrerede domænekonto.

1. For at tilmelde dig Power BI skal du gå til [Power BI-webstedet](https://powerbi.com) og vælge **Start gratisStart** >  gratis prøveversion (i feltet Del Power BI Pro prøveversion). 

2. Tilmeld dig en brugerkonto, der bruger organisationens domænenavn (f.eks `powerbiadmin@contoso.com`. ). Hvis din konto allerede er i brug, skal du logge på med din nuværende adgangskode.

3. Kontrollér din mail for **bekræftelseskoden,** og angiv koden for at validere din mailadresse.

## <a name="step-2-create-a-new-account-for-admin-access"></a>Trin 2: Opret en ny konto til administratoradgang

1. Når du angiver bekræftelseskoden, kommer du til en side, hvor du kan oprette en ny konto.

2. Udfyld felterne for brugernavn og adgangskode med den konto, du vil bruge, og vælg derefter **Start**.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Trin 3: Bekræft ejerskab af domænet, og bliv administrator

1. Når du har fuldført trin 2, skal du vælge ikonet Administration i venstre navigationsrude (du kan også gå til en browser og skrive i `https://admin.microsoft.com`).

    Du bliver omdirigeret til administratorovertagelsesguiden.

1. Vælg **Næste** , og bekræft, at du ejer det domæne, du vil overtage, ved at føje en TXT-post til din domæneregistrator. 

    Guiden giver dig den TXT-post, der skal tilføjes, samt et link til din registrators websted og et link til trinvise instruktioner.

1. På siden **Du er nu administrator skal** du **vælge Gå til Administration**.

    Du har nu de administratorrettigheder, der kræves for at fjerne domænet fra den anden konto. 
## <a name="related-content"></a>Relateret indhold

YouTube: [3 trin til at udføre en it-administratorovertagelse for Power BI og Microsoft 365](https://www.youtube.com/watch?v=xt5EsrQBZZk) (video)\
[Administratorovertagelse i Azure AD](/azure/active-directory/users-groups-roles/domains-admin-takeover) (artikel)\
[Ved hjælp af selvbetjenings-tilmelding i din organisation](self-service-sign-up.md) (artikel)\
[Om Power BI tjenesteadministratorrollen](/power-bi/service-admin-role) (artikel)
