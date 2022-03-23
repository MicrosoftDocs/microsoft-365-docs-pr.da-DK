---
title: Tilladelser i Microsoft 365 Defender portalen
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Administratorer kan få mere at vide om, hvordan du administrerer tilladelser Microsoft 365 Defender portalen for alle opgaver, der er relateret til sikkerhed.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 74e9f6e0ae60b322ed4ec50c5b1a9db278dbb2e6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63593894"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Tilladelser i Microsoft 365 Defender portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du skal administrere sikkerhedsscenarier, der strækker sig over alle Microsoft 365 tjenester. Og du har brug for fleksibilitet til at give de rette administratortilladelser til de rette personer i organisationen.

Portalen Microsoft 365 Defender på understøtter <https://security.microsoft.com> direkte administration af tilladelser for brugere, der udfører sikkerhedsopgaver Microsoft 365. Ved hjælp Microsoft 365 Defender til at administrere tilladelser kan du administrere tilladelser centralt for alle opgaver relateret til sikkerhed.

Hvis du vil administrere tilladelser i Microsoft 365 Defender, skal du gå til **Tilladelser & roller** eller <https://security.microsoft.com/securitypermissions>. Du skal være **global administrator eller** medlem af rollegruppen **Organisationsadministration** i Microsoft 365 Defender portal. **Rollestyringsrollen** giver brugerne mulighed for at få vist, oprette og redigere rollegrupper i Microsoft 365 Defender-portalen, og som standard er denne rolle kun tildelt rollegruppen Organisationsadministration.

> [!NOTE]
> Du kan finde oplysninger om Microsoft 365 Overholdelsescenter under [Tilladelser i Microsoft 365 Overholdelsescenter](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation mellem medlemmer, roller og rollegrupper

Tilladelserne i Microsoft 365 Defender er baseret på den rollebaserede adgangskontrolmodel (RBAC). RBAC er den samme tilladelsesmodel, der bruges af de fleste Microsoft 365-tjenester, så hvis du kender tilladelsesstrukturen i disse tjenester, vil tildeling af tilladelser på Microsoft 365 Defender-portalen være meget velkendt.

En **rolle** giver tilladelser til at udføre en række opgaver.

En **rollegruppe** er et sæt roller, der gør det muligt for folk at udføre deres arbejde Microsoft 365 Defender-portalen.

Portalen Microsoft 365 Defender indeholder> standardrollegrupper til de mest almindelige opgaver og funktioner, du skal tildele. Generelt anbefaler vi, at du blot føjer individuelle brugere **som** medlemmer til standardrollegrupperne.

![Diagram, der viser relationen mellem rollegrupper og roller og medlemmer.](../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Roller og rollegrupper i Microsoft 365 Defender portalen

Følgende typer af roller og rollegrupper er tilgængelige på siden **& roller** <https://security.microsoft.com/securitypermissions> på Microsoft 365 Defender portal:

- **Azure AD-roller**: Du kan få vist rollerne og de tildelte brugere, men du kan ikke administrere dem direkte i Microsoft 365 Defender portal. Azure AD-roller er centrale roller, der tildeler **tilladelser til** alle Microsoft 365 tjenester.

- **Mail & samarbejdsroller**: Det er de samme rollegrupper, der er tilgængelige i Security & Compliance Center, men du kan administrere dem direkte i Microsoft 365 Defender-portalen. De tilladelser, du tildeler her, er specifikke for Microsoft 365 Defender-portalen, Microsoft 365 Overholdelsescenter og Security & Compliance Center og dækker ikke alle de tilladelser, der er nødvendige i andre Microsoft 365-arbejdsbelastninger.

![Tilladelser & rolleside i Microsoft 365 Defender portalen.](../../media/m365-sc-permissions-and-roles-page.png)

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Azure AD-roller i Microsoft 365 Defender portal

Når du åbner Microsoft 365 Defender-portalen <https://security.microsoft.com> på og går til Mail &-samarbejdsroller  \> Tilladelser **&** \> roller **i Azure AD-roller** \> **(**<https://security.microsoft.com/aadpermissions>eller direkte til), får du vist de Azure AD-roller, der er beskrevet i dette afsnit.

Når du vælger en rolle, vises der en pop op-vindue med oplysninger, der indeholder en beskrivelse af rollen og brugertildelingerne. Men hvis du vil administrere disse opgaver, skal du klikke på **Administrer medlemmer i Azure AD** i pop op-menuen med oplysninger.

![Link til at administrere tilladelser i Azure Active Directory.](../../media/permissions-manage-in-azure-ad-link.png)

Få mere at vide under [Få vist og tildel administratorroller Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

<br>

****

|Rolle|Beskrivelse|
|---|---|
|**Global administrator**|Adgang til alle administrative funktioner i Microsoft 365 tjenester. Kun globale administratorer kan tildele andre administratorroller. Du kan finde flere oplysninger [under Global administrator/virksomhedsadministrator](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Dataadministrator for overholdelse af regler og standarder**|Hold styr på din organisations data på tværs af Microsoft 365, sørg for, at de er beskyttet, og få indsigt i eventuelle problemer for at reducere risici. Du kan få mere at vide under [Dataadministrator for overholdelse af regler og standarder](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Overholdelsesadministrator**|Hjælp din organisation med at overholde eventuelle lovmæssige krav, administrer eDiscovery-sager og vedligehold politikker for datastyring på tværs Microsoft 365 placeringer, identiteter og apps. Du kan få mere at vide under [Overholdelsesadministrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Sikkerhedsoperatør**|Få vist, undersøg og svar på aktive trusler mod Microsoft 365 brugere, enheder og indhold. Du kan finde flere oplysninger under [Sikkerhedsoperator](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Sikkerhedslæser**|Få vist og undersøg aktive trusler mod dine Microsoft 365-brugere, enheder og indhold, men (i modsætning til sikkerhedsoperatøren) har de ikke tilladelse til at reagere ved at gøre noget. Du kan finde flere oplysninger under [Sikkerhedslæser](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Sikkerhedsadministrator**|Styr din organisations overordnede sikkerhed ved at administrere sikkerhedspolitikker, gennemse sikkerhedsanalyser og rapporter på tværs af Microsoft 365-produkter og holde dig i gang med at arbejde i trusselsbilledet. Du kan finde flere oplysninger under [Sikkerhedsadministrator](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Global læser**|Den skrivebeskyttede version af **rollen Global** administrator. Få vist alle indstillinger og administrative oplysninger på tværs Microsoft 365. Du kan finde flere oplysninger [under Global læser](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Angrebssimuleringsadministrator**|Opret og administrer alle aspekter af oprettelse [af angreb](attack-simulation-training.md) , start/planlægning af en simulering og gennemgang af simuleringsresultater. Du kan få mere at vide under [Administrator for angrebssimulering](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Forfatter til angrebsindlæsning**|Opret angrebsbelastninger, men start eller planlæg dem ikke rent faktisk. Få mere at vide under [Forfatter til angrebsindlæsning](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Mail & med samarbejdsroller i Microsoft 365 Defender-portalen

Når du åbner Microsoft 365 Defender-portalen <https://security.microsoft.com> på, og du går til **Mail &-samarbejdsroller** \> **Tilladelser & roller Mail** \> **&** \> samarbejdsroller **Roller (**<https://security.microsoft.com/emailandcollabpermissions>eller direkte til), får du vist de samme rollegrupper, der er tilgængelige i Security & Compliance Center.

Du kan finde komplette oplysninger om disse rollegrupper [under Tilladelser i & Security & Compliance Center](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Rediger mailkonto& som medlem af samarbejdsrollen i Microsoft 365 Defender portalen

1. I portalen Microsoft 365 Defender på skal du gå til **Mail & samarbejdsroller** \> Tilladelser **& roller** \> mail **& samarbejdsroller** <https://security.microsoft.com>**Roller**\>. For at gå direkte til **siden Tilladelser skal** du bruge <https://security.microsoft.com/emailandcollabpermissions>.

2. På siden **Tilladelser skal** du vælge den rollegruppe, du vil redigere, på listen. Du kan klikke på **kolonneoverskriften** Navn for at sortere listen efter navn, eller du kan klikke på **ikonet** ![Søg søg.](../../media/m365-cc-sc-search-icon.png) for at finde rollegruppen.

3. I pop op-vindue med oplysninger om rollegruppen, der vises, **skal du klikke** på Rediger **i sektionen** Medlemmer.

4. På siden **Redigering skal du vælge** medlemmer, der vises, gøre et af følgende:
   - Hvis der ikke er nogen rollegruppemedlemmer, skal du klikke **på Vælg medlemmer**.
   - Hvis der er eksisterende rollegruppemedlemmer, skal du klikke på **Rediger**

5. I pop **op-menuen** Vælg medlemmer, der vises, skal du gøre et af følgende:

   - Klik **på Tilføj**. Vælg en eller flere brugere på listen over brugere, der vises. Eller du kan klikke på **ikonet** ![Søg Søg.](../../media/m365-cc-sc-search-icon.png) for at finde og vælge brugere.

     Når du har valgt de brugere, du vil tilføje, skal du klikke på **Tilføj**.

   - Klik **på Fjern**. Vælg en eller flere af de eksisterende medlemmer. Eller du kan klikke på **ikonet** ![Søg Søg.](../../media/m365-cc-sc-search-icon.png) for at finde og vælge medlemmer.

     Når du har valgt de brugere, du vil fjerne, skal du klikke på **Fjern**.

6. Tilbage i pop **op-pop op-menuen** Vælg medlemmer skal du klikke **på Udført**.

7. Tilbage på siden **Redigering skal du vælge medlemmer** og klikke **på Gem**.

8. Tilbage på pop op-menuen med oplysninger om rollegruppen skal du klikke **på Udført**.
