---
title: Flyt et domæne, der er bekræftet i en ikke-administreret konto
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
description: Få mere at vide om, hvordan du slutter dig til en ikke-administreret konto for at fjerne domænet fra kontoen og føje domænet til din konto.
ms.openlocfilehash: 7b7befdae4279b4b08ff076b88ed552b2bc411c3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63596993"
---
# <a name="move-a-domain-verified-in-an-unmanaged-account"></a>Flyt et domæne, der er bekræftet i en ikke-administreret konto

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

Hvis du er administrator, og du har forsøgt at føje et domæne til din Microsoft 365-konto, men du er blokeret, fordi domænet er bekræftet for en ikke-administreret konto, kan du blive administrator på den ikke-administrerede konto for at fjerne domænet og føje det til din konto.

> [!NOTE]
> En tilmelding til en skytjeneste, der bruger Azure AD, føjer brugeren til en ikke-administreret mappe eller en "skygge"-mappe i Azure AD og opretter en ikke-administreret konto. En ikke-administreret konto er en mappe uden en global administrator. Hvis du vil afgøre, om en konto er administreret eller ikke-administreret, skal [du se Fastslå lejertype](/power-platform/admin/powerapps-gdpr-dsr-guide-systemlogs#determining-tenant-type).
  
## <a name="before-you-begin"></a>Før du begynder

Nogle gange kan du ikke føje et domæne til din organisationskonto, fordi en anden allerede har tilmeldt sig Microsoft 365 via en mailadresse, der er knyttet til det pågældende domænenavn. Men du kan fjerne domænet fra den anden konto, der ikke er administreret, og føje det til din organisationskonto.

Først skal du tilmelde dig den ikke-administrerede konto og blive administrator for den pågældende konto (trin 1 - 3). Du kan derefter fjerne domænet fra kontoen (trin 4), logge på din organisationskonto igen og føje domænet til din konto (trin 5).

## <a name="step-1-get-an-invitation-to-join-the-unmanaged-account"></a>Trin 1: Få en invitation til at deltage i den ikke-administrerede konto

Når du forsøger at føje et domæne til din konto, får du muligvis en meddelelse om, at nogen allerede har tilmeldt sig Microsoft 365 via mailadressen. Trin 1 er at anmode om en invitation til at deltage i den anden konto og starte processen med at udføre en administratorovertagelse.

1. Gå til Microsoft 365 Administration > **Indstillinger** >  **Domæner** > **+ Tilføj domæne**, og tilføj domænenavnet.

1. Hvis du får vist en meddelelse om, at du ikke kan tilføje domænet, fordi andre allerede har tilmeldt sig ved hjælp af en mailadresse for domænet, skal du angive dit kontobrugernavn og derefter vælge **Send mig invitationen**.

1. Log af din nuværende konto, så du kan logge på den ikke-administrerede konto.

    Kontrollér din mail for at få en invitation til at hjælpe dig med at tilmelde dig den ikke-administrerede konto, og vælg linket i mailen.

    Indtast **bekræftelseskoden** fra mailen for at validere din mailadresse.

## <a name="step-2-complete-signup-with-email-instructions"></a>Trin 2: Fuldfør tilmelding med mailinstruktioner

1. Når du angiver bekræftelseskoden, kommer du til en side, hvor du kan oprette en ny konto.

2. Udfyld felterne brugernavn og adgangskode med den konto, du vil bruge, og udfør derefter trinnene for at oprette kontoen.

## <a name="step-3-verify-domain-ownership-and-become-the-admin"></a>Trin 3: Bekræft ejerskab af domænet, og bliv administrator

1. Når du har fuldført trin 2, skal du vælge ikonet Administration i venstre navigationsrude (du kan også gå til en browser og skrive i `https://admin.microsoft.com`).

    Du bliver omdirigeret til administratorovertagelsesguiden.

1. Vælg **Næste** , og bekræft, at du ejer det domæne, du vil overtage, ved at føje en TXT-post til din domæneregistrator.

    Guiden giver dig den TXT-post, der skal tilføjes, samt et link til din registrators websted og et link til trinvise instruktioner.

1. På siden **Du er nu administrator skal** du **vælge Gå til Administration**.

    Du har nu de administratorrettigheder, der kræves for at fjerne domænet fra den tidligere ikke-administrerede konto.

## <a name="step-4-remove-a-domain-from-the-unmanaged-account"></a>Trin 4: Fjern et domæne fra den konto, der ikke er administreret

1. Gå til **BrugereAktivér** >  brugere for den konto, du **tilmeldte** dig i trin 2, og vælg derefter Vist navn for det brugernavn, du er logget på med.

1. Under **Brugernavn** skal du **vælge** Administrer brugernavn og flytte brugeren til onmicrosoft-domænet ved at onmicrosoft.com domæne på rullelisten.

1. Log af kontoen, og log på igen ved hjælp af den nye `username@account.onmicrosoft.com`.

1. Vælg **Indstillinger** >  **Domæner**, find det domæne, du vil føje til den anden konto, og vælg **Fjern domæne**.

    Hvis du bliver bedt om at vælge et andet domæne som standard, skal du onmicrosoft.com domænet.

    Hvis andre brugere bruger domænet, skal du fjerne dem. Vælg mellem indstillingerne for **Fjern automatisk**, flyt manuelt brugerne til dit domæne, eller fjern brugerne helt.

   > [!NOTE]
   > Tjek igen, da det kan tage lidt tid, før domænet fjernes fra kontoen. Fjernelsen er fuldført, når domænet forsvinder fra kontoen.

1. Log af kontoen.

## <a name="step-5-add-the-domain-to-your-account"></a>Trin 5: Føj domænet til din konto

1. Log på den konto, hvor du vil tilføje domænet.

1. Vælg **Indstillinger** >  **Domæner** >  **+** Tilføj domæne, og angiv derefter domænenavnet for at fortsætte med guidens trin til at bekræfte ejerskabet af domænet i denne konto og fuldføre tilføjelsen af domænet til din konto.
  
## <a name="related-content"></a>Relateret indhold

[Udføre en intern administratorovertagelse](become-the-admin.md) (artikel)
