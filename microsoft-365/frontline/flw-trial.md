---
title: Administrer frontline-prøveversionen i Teams
author: daisyfell
ms.author: daisyfeller
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du konfigurerer en 90-dages Prøveversion af Teams til frontlinjemedarbejdere i din organisation.
ms.localizationpriority: high
ms.collection:
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 311d0a5b1204f022a993bbef24ea4bc1edda324c
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823997"
---
# <a name="manage-the-frontline-trial-in-teams"></a>Administrer frontline-prøveversionen i Teams

> [!NOTE]
> Denne prøveversion kommer snart. Du kan kontrollere, hvornår dette er tilgængeligt for din organisation, ved at søge efter en meddelelse i [Meddelelsescenter](https://go.microsoft.com/fwlink/p/?linkid=2070717) i dit Microsoft 365 Administration center.

Prøveversionen af Frontline i Microsoft Teams giver brugere i din organisation, der er i Teams, mulighed for at starte en Teams-oplevelse for hele deres frontlinjeteam, så længe de andre medlemmer befinder sig i Azure Active Directory (Azure AD). Du kan deaktivere denne funktion for brugere i din organisation ved hjælp af [PowerShell-modulet AllowSelfServicePurchase](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

## <a name="what-services-are-included"></a>Hvilke tjenester er inkluderet

Prøveversionen omfatter alt i [Microsoft 365 F3-licensen](https://www.microsoft.com/microsoft-365/enterprise/f3) med følgende undtagelser:

- Frontline-prøveversionen omfatter Exchange Foundation i stedet for Exchange Kiosk. Brugerne mangler muligvis andre Teams-funktioner på grund af denne ændring.

## <a name="eligibility"></a>Støtteberettigelse

> [!NOTE]
> Du kan kontrollere, om din organisation er en del af prøvepiloten, ved at søge efter en meddelelse i [Meddelelsescenter](https://go.microsoft.com/fwlink/p/?linkid=2070717) i dit Microsoft 365 Administration center. Din organisation skal være en del af prøvepiloten, for at brugerne kan starte eller deltage i en prøveversion. Dette tilbud er ikke tilgængeligt for GCC-, GCC High-, DoD- eller EDU-kunder.

Frontline-prøveversionen kan maksimalt rumme 300 brugere pr. prøveversion.

Brugerne kan starte en frontline-prøveversion for deres team, hvis de:

- Have en aktiv licens, der giver dem adgang til Teams.
- Har ikke tidligere startet en prøveversion af frontlinemedarbejdere.

> [!IMPORTANT]
> Hvis den bruger, der startede prøveversionen, forlader din organisation, før prøveversionen slutter, skal du som administrator overvåge prøveversionen, kontakte teamet for at se, hvem der drager fordel af disse funktioner, og beslutte, hvilke brugere du skal opgradere til en betalt licens.

Brugerne kan deltage i en prøveversion af frontlinemedarbejdere, hvis de har en administreret mailadresse på et Azure Active Directory-domæne.

Brugerne kan deltage, hvis de tidligere har startet en prøveversion, men ikke kan starte en anden prøveversion.

> [!NOTE]
> Brugere uden eksisterende adgang til Teams kan kun føjes til prøveteamet på tidspunktet for teamoprettelsen. Eksisterende Teams-brugere kan stadig føjes til prøveversionen, når teamet er blevet oprettet.

## <a name="set-up-the-trial"></a>Konfigurer prøveversionen

Berettigede brugere kan starte en frontline-prøveversion ved at logge på appen Opgaver i Teams fra skrivebordet eller [webappen](https://teams.microsoft.com/_#/apps/com.microsoft.teamspace.tab.planner/sections/mytasks). På nuværende tidspunkt understøttes start af en frontline-prøveversion via mobil ikke. Når en prøveversion startes, tildeles hele teamet automatisk frontline-prøvelicensen. Brugere med eksisterende betalte licenser, der giver dem adgang til Teams, tildeles også prøvelicenser, men bevarer funktionaliteten af deres eksisterende licenser i hele prøveversionen og beholder deres eksisterende betalte licenser, når prøveversionen slutter. Den bruger, der startede prøveversionen, modtager mailmeddelelser i løbet af prøveversionen.

## <a name="manage-the-frontline-trials-experience"></a>Administrer oplevelsen med frontline-prøveversioner

Administratorer kan forhindre slutbrugere i at starte frontlinjeversionen i deres organisation ved hjælp af **PowerShell-modulet AllowSelfServicePurchase** . Dette gælder kun for prøvelicenser. [Få mere at vide om, hvordan du bruger PowerShell-modulet AllowSelfServicePurchase](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

### <a name="manage-teams-for-users-who-have-the-frontline-trial-license"></a>Administrer Teams for brugere, der har en frontline-prøveversionslicens

Du kan administrere brugere, der har frontline-prøvelicensen, på samme måde som du administrerer brugere, der har en almindelig betalt licens. Du kan få flere oplysninger under [Administrer Teams-indstillinger for din organisation](/microsoftteams/manage-teams-overview).

### <a name="remove-a-trial-license"></a>Fjern en prøvelicens

Du kan fjerne Frontline Trial-licensen via PowerShell eller din Microsoft 365 Administration.

[Få mere at vide om, hvordan du fjerner med PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell).

[Få mere at vide om, hvordan du fjerner i Administration](/microsoft-365/admin/add-users/delete-a-user).

## <a name="upgrade-users-from-frontline-trial"></a>Opgrader brugere fra Frontline-prøveversion

Brugerne kan kontakte dig for at bede om licenser, når prøveversionen slutter. Du skal have administratorrettigheder for at opgradere dine brugere.

### <a name="when-to-upgrade"></a>Hvornår skal du opgradere?

I slutningen af den 90-dages prøveversion skal du kontakte dine brugere for at se, hvem der skal fortsætte med en betalt licens. Sørg for at gøre dette, før prøveversionsabonnementet på Frontline udløber for at undgå enhver afbrydelse af brugernes oplevelser.

> [!IMPORTANT]
> Hvis Frontline-prøvelicensen slutter, og en bruger ikke straks tildeles en licens, der omfatter Teams, mister vedkommende adgang til Teams. Efter 30 dage slettes deres data (filer, meddelelser og meget mere). Brugeren findes stadig i Azure Active Directory. Hvis der tildeles en ny licens til brugeren for at aktivere Teams-funktionalitet inden for 30-dages perioden, vil alt deres indhold i Teams stadig eksistere.

### <a name="choose-an-upgrade-path"></a>Vælg en opgraderingssti

> [!TIP]
> Frontline-prøveversionen er baseret på [licensen til Microsoft 365 F3](https://www.microsoft.com/microsoft-365/enterprise/f3).

Afhængigt af de abonnementer din organisation i øjeblikket har, er der tre måder at opgradere fra en Frontline Trial til en betalt licens:

- **Opgrader et eksisterende Microsoft 365-abonnement.** Brug denne indstilling, hvis din organisation har abonnementer på andre Office-produkter, der ikke indeholder Teams. Du kan få flere oplysninger under [Opgrader til en anden plan](/microsoft-365/commerce/subscriptions/upgrade-to-different-plan). Hvis du vil se aktive brugere for et eksisterende abonnement, skal du gå til **Brugere >** [Aktive brugere](https://go.microsoft.com/fwlink/p/?linkid=834822) i Microsoft 365 Administration.

- **Føj brugere til et eksisterende Microsoft 365-abonnement.** Brug denne indstilling, hvis din organisation ikke har nok betalte Teams-licenser til at dække dit frontlinjeteam. Du kan få flere oplysninger under [Køb eller fjern licenser](/microsoft-365/commerce/licenses/buy-licenses). Hvis du vil føje brugere til et eksisterende abonnement, der allerede har nok tilgængelige licenser, skal du se [Flyt brugere til et andet abonnement](/microsoft-365/commerce/subscriptions/move-users-different-subscription). Hvis du vil se aktive brugere for et eksisterende abonnement, skal du gå til **Brugere >** [Aktive brugere](https://go.microsoft.com/fwlink/p/?linkid=834822) i Microsoft 365 Administration.

- **Køb et nyt Microsoft 365-abonnement.** Brug denne indstilling, hvis din organisation ikke har nogen eksisterende abonnementer på Office-produkter, eller hvis din organisation ønsker at købe et abonnement, der er forskelligt fra deres eksisterende abonnement, til at dække frontlinebrugere. Du kan få flere oplysninger i [Microsoft 365 til frontlinjemedarbejdere](https://www.microsoft.com/microsoft-365/enterprise/frontline).

Hvis du ikke er sikker på, hvilket Microsoft 365-abonnement du skal opgradere til, skal du se [Microsoft 365 til frontlinjearbejdere](https://www.microsoft.com/microsoft-365/enterprise/frontline). Hvis du har brug for yderligere hjælp til at vælge et abonnement, eller hvis din organisation har brug for mere end 300 licenser, skal du kontakte din [Microsoft-partner](https://www.microsoft.com/solution-providers/home) eller Microsoft-kontorepræsentant.

### <a name="assign-paid-licenses"></a>Tildel betalte licenser

Hvis du vil tildele dine nyligt erhvervede licenser, skal du se [Tildel licenser til brugere](/microsoft-365/admin/manage/assign-licenses-to-users).  

Når du har tildelt de nye licenser, skal du fjerne tildelingen af Teams Exploratory-licenser. Se [Fjern tildeling af licenser fra brugere](/microsoft-365/admin/manage/remove-licenses-from-users) for at få flere oplysninger.

## <a name="faq"></a>Ofte stillede spørgsmål

**Hvor lang tid varer prøveversionen?** <br>
Frontline-prøveversionen varer 90 dage.

**Hvad skal administratorer gøre i slutningen af den 90-dages frontlinjeprøveoplevelse?** <br>
I slutningen af den 90-dages prøveversion skal du kontakte dine brugere for at se, hvem der skal fortsætte med en betalt licens. Derefter skal du [opgradere dine brugere](#upgrade-users-from-frontline-trial).

**Hvad sker der, hvis den bruger, der startede prøveversionen, forlader organisationen?** <br>
Du som administrator skal overvåge prøveversionen i resten af den 90-dages periode og opgradere til betalte licenser for brugere, der har brug for dem, når prøveversionen slutter.

**Hvad er politikken for dataopbevaring?** <br>
Du kan få mere at vide om dataopbevaring fra [oplysningerne om Microsoft 365-abonnementet](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?).

**Hvad sker der, hvis en bruger støder på en fejl, når frontline-prøveversionen startes?** <br>
Sørg for, at din organisation, den bruger, der starter prøveversionen, og de brugere, der føjes til prøveversionen, opfylder [berettigelseskriterierne](#eligibility).