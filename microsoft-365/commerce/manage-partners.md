---
title: Administrere partnerrelationer
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: tugu, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid: MET150
description: Få mere at vide om at arbejde med Microsoft-certificerede løsningsudbydere (partnere) for at købe og administrere produkter og tjenester for din organisation eller skole.
ms.date: 02/04/2022
ms.openlocfilehash: c07267989e8df7203cced6c3a21ffd9aa667347f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587474"
---
# <a name="manage-partner-relationships"></a>Administrere partnerrelationer

Du kan arbejde med Microsoft-certificerede løsningsudbydere (partnere) for at købe og administrere produkter og tjenester for din organisation eller skole. Der er nogle få trin involveret i at få tingene konfigureret.

1. Administratorer finder og kontakter en partner ved hjælp af formularen på <a href="https://www.microsoft.com/solution-providers/home" target="_blank">https://www.microsoft.com/solution-providers/home</a>.
2. Partnere sender en mailanmodning til kunder for at etablere en partnerrelation.
3. Kunder accepterer invitationen i Microsoft 365 Administration og begynder at arbejde sammen med partneren.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator eller faktureringsadministrator for at udføre disse trin. Du kan få mere at vide [under Om administratorroller](../admin/add-users/about-admin-roles.md).

## <a name="what-can-a-partner-do-for-my-organization-or-school"></a>Hvad kan en partner gøre for min organisation eller skole?

Der er flere måder, hvorpå en partner kan arbejde sammen med dig. Baseret på virksomhedens behov vælger de en af disse typer, når de sender deres anmodning om at arbejde sammen med dig.

| Partnertype | Beskrivelse |
| ------ | ------------------- |
| Detaljeret delegeret administrator | Partnere, der administrerer produkter og tjenester for din organisation eller skole, men som har begrænset adgang til, hvad de kan gøre i Microsoft 365 Administration. MED GDAP (Granular delegated administrator privileges) kan partnere udføre opgaver i Administration uden at have global administratortilladelse. Ved at give GDAP til partnere skal du sikre dig, at de har de mindst tilladte roller og begrænser risikoen til din organisation. |
| Forhandler | Partnere, der sælger Microsoft-produkter til din organisation eller skole. |
| Delegeret administrator | Partnere, der administrerer produkter og tjenester for din organisation eller skole. I Azure Active Directory (AD) er partneren en global administrator for din lejer. Med denne rolle kan de administrere tjenester som oprettelse af brugerkonti, tildeling og administration af licenser og nulstilling af adgangskoder. |
| Forhandleradministrator & delegeret administrator | Partnere, der sælger og administrerer Microsoft-produkter og -tjenester til din organisation eller skole. |
| Partner | Du giver din partner en brugerkonto i din lejer, og de arbejder sammen med Microsoft-tjenester på dine vegne. |
| Rådgiver | Partnere kan nulstille adgangskoder og håndtere supporthændelser for dig. |
| Microsofts &-serviceaftale (MPSA)-partner | Hvis du har arbejdet med flere partnere via MPSA-programmet, kan du give dem tilladelse til at se hinandens køb. |
| LOB-partner (Line of business) | Partnere kan udvikle, indsende og administrere LOB-apps, der er specifikke for din organisation eller skole. |

## <a name="find-a-partner"></a>Find en partner

1. Gå til <a href="https://www.microsoft.com/en-us/solution-providers/home" target="_blank">https://www.microsoft.com/en-us/solution-providers/home</a>.
2. Angiv din placering, vælg organisationens størrelse, tilføj nøgleord for den type tjenester, du har brug for, og vælg derefter **Gå**.
3. Vælg en eller flere partnere, og vælg derefter **Kontakt udvalgte udbydere**.
4. Udfyld formularen for at beskrive virksomhedens behov, og vælg derefter **Send**.

Partneren kontakter dig og giver dig mulighed for at få mere at vide om dem. Hvis du beslutter dig for at arbejde med dem, sender de dig en invitation via mail til at etablere en partnerrelation.

## <a name="review-and-accept-a-partner-relationship-and-microsoft-customer-agreement"></a>Gennemse og acceptér et partnerrelation og Microsoft-kundeaftale

Når du har fundet en partner og beslutter at arbejde sammen med vedkommende, sender vedkommende dig en invitation via mail.

1. I mailen skal du vælge linket for at gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.
2. På siden **Acceptér & godkende partner** skal du vælge linket til **Microsoft-kundeaftalen** og læse dokumentet.
3. Markér afkrydsningsfeltet for at bekræfte, at du læser aftalen.
4. Vælg **Acceptér& Godkend**.
5. Listen over partnere, du arbejder med, vises. Vælg en hvilken som helst partner for at få vist detaljer.

## <a name="review-and-accept-a-microsoft-customer-agreement"></a>Gennemse og acceptér en Microsoft-kundeaftale

Hvis du allerede har en partner, men endnu ikke har signeret en Microsoft-kundeaftale, skal du acceptere aftalen, før de kan foretage køb eller administrere dine abonnementer på dine vegne.

1. Hvis du modtager en mail fra din partner, skal du vælge linket for at gå til Microsoft 365 Administration eller gå til <a href="https://go.microsoft.com/fwlink/?linkid=2116573" target="_blank">siden Acceptér</a> aftale.
2. Vælg linket til **Microsoft-kundeaftalen,** og læs dokumentet.
3. Markér afkrydsningsfeltet for at bekræfte, at du læser aftalen.
4. Vælg **Acceptér**.
5. Listen over partnere, du arbejder med, vises. Vælg en hvilken som helst partner for at få vist detaljer.

## <a name="remove-partner-admin-roles"></a>Fjern partneradministratorroller

Afhængigt af anmodningen fra partneren, når du accepterer invitationen, accepterer du at give dem globale administratorroller og helpdesk-administratorroller. Når du giver disse administratorroller til en partner, giver du dem automatisk delegerede administratorrettigheder i Azure AD. Du kan få mere at vide [under Delegerede administratorrettigheder i Azure AD](/partner-center/customers_revoke_admin_privileges#delegated-admin-privileges-in-azure-ad).

Den nye detaljeret delegerede administrative rettighedsfunktion (GDAP) giver partnere mere detaljeret og tidsgrænset adgang til deres kunders arbejdsbelastning. Det betyder, at partnere bedre kan håndtere kundernes sikkerhedsproblemer. Partnere kan også tilbyde flere tjenester til kunder, der er utilpasse med de aktuelle niveauer af partneradgang, og som har lovmæssige krav, der kun giver mindst privilegeret adgang til partnere. Med GDAP accepterer du at give partnerroller specificeret i deres anmodning. Disse roller kan tilpasses, så du kan diskutere med din partner, hvis visse tilladelser ikke er godkendt af dig.

Hvis du ikke vil give administratorroller til partneren, skal du annullere invitationen i stedet for at acceptere den.

Du kan når som helst fjerne administratorroller fra en partner. Hvis du fjerner administratorrollerne, fjernes partnerrelationen ikke. De kan stadig arbejde sammen med dig i en anden kapacitet, f.eks. en forhandler. Hvis du beslutter, at du ikke længere vil arbejde sammen med en partner, skal du kontakte din partner for at afslutte relationen.

1. I Administration skal du gå til siden **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partner-relationer</a>.
2. På siden **Partnerrelationer skal** du vælge den række, der indeholder navnet på den partner, du vil fjerne.
3. Markér den række, der indeholder navnet på partneren.
4. Vælg Fjern roller på **partnersiden**.
5. I dialogboksen **Fjern roller?** skal du vælge **Ja**.

Hvis du ikke kan se indstillingen **Fjern roller** , skal du kontakte [Partnercenter](https://partner.microsoft.com/support).
