---
title: Planlæg styring af organisering og livscyklus for Microsoft 365 grupper og Microsoft Teams
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om indstillinger for livscyklusstyring for samarbejdsværktøjer i Microsoft 365
ms.openlocfilehash: a0f4622afd1a22b8cd6574865012b7f636fc06c5
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63591338"
---
# <a name="plan-organization-and-lifecycle-governance-for-microsoft-365-groups-and-microsoft-teams"></a>Planlæg styring af organisering og livscyklus for Microsoft 365 grupper og Microsoft Teams

Microsoft 365-grupper har et omfattende sæt værktøjer til at implementere de styringsfunktioner, din organisation kræver. 

Det følgende afsnit beskriver egenskaberne, anbefaler de bedste fremgangsmåder og giver vejledning i at stille de rigtige spørgsmål for at afgøre, hvilke styringskrav der er, og hvordan de skal opfyldes.

## <a name="control-who-can-create-microsoft-365-groups"></a>Bekontrolelement, hvem der kan Microsoft 365 grupper

Grupper kan oprettes af slutbrugere fra flere slutpunkter, herunder Outlook, SharePoint, Teams og andre miljøer.

![image desc.](../media/04.png)

Vi anbefaler stærkt, at du bruger selvbetjening for at styrke gruppeejere og hjælpe brugerne med nemmere at få arbejdet udført. Begrænsning af oprettelse af grupper og teams kan sænke brugernes produktivitet, fordi mange Microsoft 365 tjenester kræver, at der oprettes grupper, for at tjenesten kan fungere.

Overvej følgende styringsmuligheder for oprettelse af grupper:

- Hvis du vil begrænse gruppeudvrængn, skal [du bruge udløbspolitikker](microsoft-365-groups-expiration-policy.md) for grupper til automatisk at slette grupper, der ikke bruges.
- Begræns oprettelse af grupper til medlemmer [af sikkerhedsgrupper med dynamisk](/azure/active-directory/users-groups-roles/groups-create-rule) medlemskab, der indeholder f.eks. alle fuldtidsansatte.
- Begræns oprettelse af grupper til en sikkerhedsgruppe og kræv, at brugerne afslutter kurserne i organisationens politikker for gruppeanvendelse for at blive medlemmer af sikkerhedsgruppen.

Hvis du vil begrænse, hvem der kan oprette grupper, skal du se Administrer, hvem der kan [Microsoft 365 grupper](manage-creation-of-groups.md) for at få oplysninger om, hvordan du konfigurerer dette.

## <a name="group-delete-restore-and-archiving"></a>Gruppere sletning, gendannelse og arkivering

Når en Microsoft 365 gruppe slettes, bevares den som standard i 30 dage. Denne periode på 30 dage kaldes "blød sletning", fordi du stadig kan gendanne gruppen. Efter 30 dage slettes gruppen og det tilknyttede indhold permanent og kan ikke gendannes.

Hvis du har opbevaringspolitikker på plads for at bevare chat, filer eller mail, bevares disse elementer, når gruppen er blevet slettet. Se [Få mere at vide om opbevaringspolitikker](../compliance/retention.md) , hvis du vil have mere at vide.

Hvis du vil slette en gruppe, men bevare indholdet fra en eller flere af de gruppeforbundne tjenester, skal du se Arkivér grupper[, teams og Yammer](end-life-cycle-groups-teams-sites-yammer.md) for at få flere oplysninger.

## <a name="group-naming-policy"></a>Politik for gruppenavngivning

En navngivningspolitik for grupper kan hjælpe dig med at styre grupper på to måder:

- En navngivningspolitik for præfiks/suffiks kan bruges til at gennemtvinge faste strenge eller Azure AD-attributter i begyndelsen eller slutningen af et gruppenavn og den tilknyttede mailadresse. Ved at gøre dette kan du sikre, at f.eks. afdelingsnavne eller områder medtages i gruppenavne.
- En politik for blokerede ord kan sikre, at bestemte ord, f.eks. navnene på ledere, ikke bruges i gruppenavne.

Navngivningspolitikker anvendes, når grupper oprettes ud fra en af de gruppeforbundne tjenester.

Hvis du beslutter dig for at bruge navngivningspolitikker for grupper, skal [Microsoft 365 politikker for gruppenavngivning](groups-naming-policy.md).

## <a name="group-expiration-policy"></a>Udløbspolitik for gruppe

Du kan angive en udløbsperiode, og enhver gruppe, der når slutningen af den pågældende periode, og som ikke fornys, slettes. Udløbsperioden starter, når gruppen oprettes, eller på den dato, hvor den sidst blev fornyet.

Når du har indstillet grupper til at udløbe:
- Ejere af gruppen får besked om at forny gruppen, når udløbsdatoen nærmer sig.
- Aktive grupper fornys automatisk.
- Alle grupper, der ikke fornys, slettes.
- Enhver gruppe, der slettes, kan gendannes inden for 30 dage af gruppeejerne eller administratoren.

Udløbspolitikker er en god metode til at begrænse gruppeudsvrængn ved at sikre, at grupper, der ikke længere er i brug, slettes. Hvis du vil oprette en udløbspolitik for en gruppe, skal du [Microsoft 365 udløbspolitik for grupper](microsoft-365-groups-expiration-policy.md).

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Fjern en tidligere medarbejder, og beskyt data](/microsoft-365/admin/add-users/remove-former-employee)
