---
title: Administrer partnerrelationer
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
description: Få mere at vide om, hvordan du arbejder sammen med Microsoft-certificerede løsningsudbydere (partnere) om at købe og administrere produkter og tjenester for din organisation eller skole.
ms.date: 02/04/2022
ms.openlocfilehash: 313cea4bef92da66bb5c95f3cf9ccd0f9a1d6f32
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490713"
---
# <a name="manage-microsoft-certified-solution-provider-partner-relationships"></a>Administrer partnerrelationer for Microsoft-certificerede løsningsudbydere

Du kan samarbejde med Microsoft-certificerede løsningsudbydere (partnere) om at købe og administrere produkter og tjenester til din organisation eller skole. Der er nogle få trin involveret i at få tingene konfigureret.

1. Administratorer finder og kontakter en partner ved hjælp af formularen på <a href="https://www.microsoft.com/solution-providers/home" target="_blank">https://www.microsoft.com/solution-providers/home</a>.
2. Partnere sender en mailanmodning til kunder om at etablere en partnerrelation.
3. Kunderne accepterer invitationen i Microsoft 365 Administration og begynder at arbejde sammen med partneren.

## <a name="before-you-begin"></a>Før du begynder

Du skal være enten global administrator eller faktureringsadministrator for at kunne udføre disse trin. Du kan få mere at vide under [Om administratorroller](../admin/add-users/about-admin-roles.md).

## <a name="what-can-a-partner-do-for-my-organization-or-school"></a>Hvad kan en partner gøre for min organisation eller skole?

En partner kan arbejde sammen med dig på flere måder. Baseret på dine forretningsmæssige behov vælger de en af disse typer, når de sender deres anmodning om at arbejde sammen med dig.

| Partnertype | Beskrivelse |
| ------ | ------------------- |
| Detaljeret uddelegeret administrator | Partnere, der administrerer produkter og tjenester for din organisation eller skole, men som har begrænset adgang til det, de kan gøre i Microsoft 365 Administration. Detaljeret delegerede administratorrettigheder (GDAP) gør det muligt for partnere at udføre opgaver i Administration uden at have global administratortilladelse. Når du giver GDAP til partnere, sikrer du, at de har de mindst tilladte roller og begrænser risikoen for din organisation. |
| Forhandler | Partnere, der sælger Microsoft-produkter til din organisation eller skole. |
| Delegeret administrator | Partnere, der administrerer produkter og tjenester for din organisation eller skole. I Azure Active Directory (AD) er partneren global administrator for din lejer. Denne rolle giver dem mulighed for at administrere tjenester som oprettelse af brugerkonti, tildeling og administration af licenser og nulstilling af adgangskode. |
| Forhandler & uddelegeret administrator | Partnere, der sælger og administrerer Microsoft-produkter og -tjenester til din organisation eller skole. |
| Partner | Du giver din partner en brugerkonto i din lejer, og de arbejder sammen med andre Microsoft-tjenester på dine vegne. |
| Rådgiver | Partnere kan nulstille adgangskoder og håndtere supporthændelser for dig. |
| Mpsa-partner (Microsoft Products & Services Agreement) | Hvis du har arbejdet sammen med flere partnere via MPSA-programmet, kan du give dem mulighed for at se køb, der er foretaget af hinanden. |
| Line of business-partner (LOB) | Partnere kan udvikle, indsende og administrere LOB-apps, der er specifikke for din organisation eller skole. |

## <a name="find-a-partner"></a>Find en partner

1. Gå til <a href="https://www.microsoft.com/en-us/solution-providers/home" target="_blank">https://www.microsoft.com/en-us/solution-providers/home</a>.
2. Angiv din placering, vælg din organisationsstørrelse, tilføj nøgleord for den type tjenester, du har brug for, og vælg derefter **Gå**.
3. Vælg en eller flere partnere, og vælg derefter **Kontakt de valgte udbydere**.
4. Udfyld formularen for at beskrive dine forretningsbehov, og vælg derefter **Send**.

Partneren kontakter dig og giver dig mulighed for at lære mere om dem. Hvis du beslutter dig for at arbejde med dem, sender de dig en invitation via mail for at oprette en partnerrelation.

## <a name="review-and-accept-a-partner-relationship-and-microsoft-customer-agreement"></a>Gennemse og acceptér en partnerrelation og Microsoft-kundeaftale

Når du har fundet en partner og beslutter dig for at arbejde med dem, sender de dig en invitation via mail.

1. I mailen skal du vælge linket for at gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>.
2. På siden **Acceptér aftale & godkend partner** skal du vælge linket til **Microsoft-kundeaftale** og læse dokumentet.
3. Markér afkrydsningsfeltet for at bekræfte, at du har læst aftalen.
4. Vælg **Acceptér & Godkend**.
5. Listen over partnere, du arbejder med, vises. Vælg en partner for at få vist detaljer.

## <a name="review-and-accept-a-microsoft-customer-agreement"></a>Gennemse og acceptér en Microsoft-kundeaftale

Hvis du allerede har en partner, men endnu ikke har underskrevet en Microsoft-kundeaftale, skal du acceptere aftalen, før de kan foretage køb eller administrere dine abonnementer på dine vegne.

1. Hvis du modtager en mail fra din partner, skal du vælge linket for at gå til Microsoft 365 Administration eller gå til siden <a href="https://go.microsoft.com/fwlink/?linkid=2116573" target="_blank">Acceptér aftale</a>.
2. Vælg linket til **Microsoft-kundeaftale**, og læs dokumentet.
3. Markér afkrydsningsfeltet for at bekræfte, at du har læst aftalen.
4. Vælg **Acceptér**.
5. Listen over partnere, du arbejder med, vises. Vælg en partner for at få vist detaljer.

## <a name="remove-partner-admin-roles"></a>Fjern partneradministratorroller

Afhængigt af den anmodning, som partneren har fremsat, når du accepterer invitationen, accepterer du at give dem administratorrollerne Global og Helpdesk. Når du giver disse administratorroller til en partner, tildeler du dem automatisk delegerede administratorrettigheder i Azure AD. Du kan få mere at vide under [Delegerede administratorrettigheder i Azure AD](/partner-center/customers_revoke_admin_privileges#delegated-admin-privileges-in-azure-ad).

Den nye GDAP-funktion (Detaljeret delegerede administrative rettigheder) giver partnere mere detaljeret og tidsbunden adgang til deres kunders arbejdsbelastninger. Det betyder, at partnere er bedre i stand til at håndtere deres kunders sikkerhedsproblemer. Partnere kan også levere flere tjenester til kunder, der ikke har det godt med de nuværende niveauer af partneradgang, og som har lovmæssige krav om kun at give partnere mindst privilegeret adgang. Med GDAP accepterer du at give partnere roller, der er angivet i deres anmodning. Disse roller kan tilpasses, så du kan diskutere med din partner, om visse tilladelser ikke er godkendt af dig.

Hvis du ikke vil give partneren administratorroller, skal du annullere invitationen i stedet for at acceptere den.

Du kan når som helst fjerne administratorroller fra en partner. Hvis du fjerner administratorrollerne, fjernes partnerrelationen ikke. De kan stadig arbejde sammen med dig i en anden kapacitet, f.eks. en forhandler. Hvis du beslutter, at du ikke længere vil arbejde med en partner, skal du kontakte din partner for at afslutte relationen.

1. I Administration skal du gå til siden **Indstillinger** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partnerrelationer</a> .
2. På siden **Partnerrelationer** skal du vælge den række, der indeholder navnet på den partner, du vil fjerne.
3. Vælg den række, der indeholder navnet på partneren.
4. Vælg **Fjern roller** på partnersiden.
5. I dialogboksen **Fjern roller?** skal du vælge **Ja**.

Hvis du ikke kan se indstillingen **Fjern roller** , skal du kontakte [Partnercenter](https://partner.microsoft.com/support).
