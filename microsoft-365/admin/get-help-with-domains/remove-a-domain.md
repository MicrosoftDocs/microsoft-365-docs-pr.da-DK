---
title: Fjerne et domæne
f1.keywords:
- NOCSH
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
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Få mere at vide om, hvordan du fjerner et gammelt domæne Microsoft 365 flytter brugere og grupper til et andet domæne eller annullerer dit abonnement.
ms.openlocfilehash: 3da47275e090296c9b192b4bd60ad19dd8cf4149
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588319"
---
# <a name="remove-a-domain"></a>Fjerne et domæne

 **[Tjek ofte stillede spørgsmål om](../setup/domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter.

Fjerner du dit domæne, fordi du vil føje det til en anden Microsoft 365 abonnementsplan? Eller vil du blot opsige dit abonnement? Du kan [ændre din plan eller dit abonnement](../../commerce/subscriptions/switch-to-a-different-plan.md) eller [opsige dit abonnement](../../commerce/subscriptions/cancel-your-subscription.md).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

### <a name="step-1-move-users-to-another-domain"></a>Trin 1: Flyt brugere til et andet domæne

#### <a name="move-users"></a>Flyt brugere

::: moniker range="o365-worldwide"

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Administration</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration</a>.

::: moniker-end

2. Vælg **BrugereAktivér** >  brugere.

3. Markér felterne ud for navnene på alle de brugere, du vil flytte.

4. Øverst på siden skal du vælge **Skift domæner**.

5. Vælg **et andet domæne** i ruden Skift domæner.

Du skal også gøre dette for dig selv, hvis du er på det domæne, du vil fjerne. Når du redigerer domænet for din konto, skal du logge af og logge på igen ved hjælp af det nye domæne, du valgte for at fortsætte.

#### <a name="move-yourself"></a>Flyt dig selv

::: moniker range="o365-worldwide"

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Administration</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration</a>.

::: moniker-end

2. Gå til **Aktive** \> **brugere,** og vælg din konto på listen.

3. På fanen **Konto** skal du vælge **Administrer brugernavn** og derefter vælge et andet domæne.

4. Øverst skal du vælge dit kontonavn og derefter vælge **Log af**.

5. Log på med det nye domæne og den samme adgangskode.

Du kan også bruge PowerShell til at flytte brugere til et andet domæne. Se [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname) for at få flere oplysninger. Brug [Set-MsolDomain til at angive standarddomænet](/powershell/module/msonline/set-msoldomain).

### <a name="step-2-move-groups-to-another-domain"></a>Trin 2: Flyt grupper til et andet domæne

::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Grupper**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Administration skal</a> du gå til **siden Grupper**>.

::: moniker-end

2. Vælg gruppenavnet, og vælg **derefter Rediger** på **fanen Generelt under Mailadresse,** **Primær**.

3. Brug rullelisten til at vælge et andet domæne.

4. Vælg **Gem** og derefter **Luk**. Gentag denne proces for alle de grupper eller distributionslister, der er knyttet til det domæne, du vil fjerne.

### <a name="step-3-remove-the-old-domain"></a>Trin 3: Fjern det gamle domæne

::: moniker range="o365-worldwide"

> [!NOTE]
> Hvis du vil fjerne et brugerdefineret domæne, skal du se [Fjern et brugerdefineret domæne, før](#remove-a-custom-domain) du fortsætter.

1. I Administration skal du gå til **Indstillinger** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domæner</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til **siden Konfiguration** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">af</a> domæner.

::: moniker-end

2. På siden **Domæner skal** du vælge det domæne, du vil fjerne.

3. Vælg Fjern i højre **rude**.

4. Følg eventuelle yderligere anvisninger, og vælg derefter **Luk**.




### <a name="remove-a-custom-domain"></a>Fjerne et brugerdefineret domæne

Hvis du annullerer dit abonnement, og du bruger et brugerdefineret domæne, er der et par ekstra trin, du skal udføre, før du kan annullere dit abonnement. 

#### <a name="change-your-domain-nameserver-records-if-needed"></a>Ændre dine navneserverposter (hvis det er nødvendigt)

Hvis du har konfigureret et brugerdefineret domæne, har du tilføjet DNS-poster, så domænet fungerer med Microsoft 365-tjenester. Før du fjerner dit domæne, skal du sørge for at opdatere DNS-posterne, f.eks dit domæne MX-post, på din DNS-vært.

Du kan f.eks. ændre MX-posten hos din DNS-vært. Mails, der sendes til dit domæne, stopper med at komme til din Microsoft-adresse og går i stedet til din nye mailudbyder. En MX-post bestemmer, hvor mail til dit domæne sendes til.

- Hvis dine navneserverposter (NS) peger på [Microsoft 365-navneservere](../../admin/setup/add-domain.md), træder ændringer af din MX-post ikke i kraft, før du ændrer dine NS-poster, så de peger på din nye DNS-vært (se trin 2).

- Før du opdaterer MX-posten, skal du give brugerne besked om den dato, hvor du planlægger at skifte deres mail, og den nye mailudbyder, du vil bruge. Hvis brugerne vil flytte deres eksisterende Microsoft-mail til den nye udbyder, skal de også gøre noget ekstra.

- På dagen, hvor du ændrer MX-posten, skal du sørge for at gemme [dine data](/microsoft-365/commerce/subscriptions/cancel-your-subscription#save-your-data) og fjerne Office [hvis det er nødvendigt](/microsoft-365/commerce/subscriptions/cancel-your-subscription#uninstall-office-optional).

#### <a name="update-your-domain-mx-and-other-dns-records-if-youre-using-a-custom-domain"></a>Opdater dit domæneSX-poster og andre DNS-poster (hvis du bruger et brugerdefineret domæne)

Hvis du ændrede dine navneserverposter (NS) til Microsoft 365, da du konfigurerede dit domæne, skal du konfigurere eller opdatere din MX-post og andre DNS-poster på den DNS-vært, du planlægger at bruge, og derefter ændre din NS-post til den pågældende DNS-vært.

Hvis du ikke ændrede NS-poster, da du konfigurerede dit domæne, da du ændrede MX-posten, begynder din mail at gå til den nye adresse med det samme.

Hvis du vil ændre dine NS-poster, [skal du se Skift navneservere for at Microsoft 365 med en domæneregistrator](../../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md).



## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Hvor lang tid tager det for et domæne at blive fjernet?

Det kan tage så lidt som 5 minutter for Microsoft 365 at fjerne et domæne, hvis der ikke refereres til det på mange steder, f.eks. sikkerhedsgrupper, distributionslister, brugere og Microsoft 365 grupper. Hvis der er mange referencer, der bruger domænet, kan det tage flere timer (en dag), før domænet fjernes.

Hvis du har hundredvis eller tusindvis af brugere, kan du bruge PowerShell til at forespørge for alle brugere og derefter flytte dem til et andet domæne. Ellers er det muligt for en håndfuld brugere at blive overset i brugergrænsefladen, og når du derefter går til at fjerne domænet, kan du ikke det, og du ved ikke hvorfor. Se [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname) for at få flere oplysninger. Brug [Set-MsolDomain til at angive standarddomænet](/powershell/module/msonline/set-msoldomain).

## <a name="still-need-help"></a>Har du stadig brug for hjælp?

::: moniker range="o365-worldwide"

> [!NOTE]
> Du kan ikke fjerne [domænet ".onmicrosoft.com"](../setup/domains-faq.yml) fra din konto. Når du fjerner et domæne, vender brugerkonti tilbage til adressen ".onmicrosoft.com" som primær SMTP/UserPrincipalName.

Fungerer det stadig ikke? Dit domæne skal muligvis fjernes manuelt. [Ring til os,](../../business-video/get-help-support.md) og vi hjælper dig med at tage os af det!

::: moniker-end

::: moniker range="o365-21vianet"

> [!NOTE]
> Du kan ikke fjerne [domænet ".partner.onmschina.cn"](../setup/domains-faq.yml) fra din konto. Når du fjerner et domæne, vender brugerkonti tilbage til adressen ".partner.onmschina.cn" som primær SMTP/UserPrincipalName.

Fungerer det stadig ikke? Dit domæne skal muligvis fjernes manuelt. [Ring til os,](../../business-video/get-help-support.md?view=o365-21vianet&preserve-view=true) og vi hjælper dig med at tage os af det!

::: moniker-end

## <a name="related-content"></a>Relateret indhold

[Ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) (artikel)

[Skift til en anden Microsoft 365 for business-plan](../../commerce/subscriptions/switch-to-a-different-plan.md) (artikel)

[Annuller dit abonnement](../../commerce/subscriptions/cancel-your-subscription.md) (artikel)
