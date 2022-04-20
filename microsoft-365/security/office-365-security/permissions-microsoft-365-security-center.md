---
title: Tilladelser på Microsoft 365 Defender-portalen
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
description: Administratorer kan få mere at vide om, hvordan de administrerer tilladelser på Microsoft 365 Defender portalen for alle opgaver, der er relateret til sikkerhed.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3381d3eb823b818aec01a181f176cb56f6af310c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939185"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Tilladelser på Microsoft 365 Defender-portalen

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du skal administrere sikkerhedsscenarier, der strækker sig over alle Microsoft 365 tjenester. Og du har brug for fleksibiliteten til at give de rette administratortilladelser til de rette personer i din organisation.

Microsoft 365 Defender-portalen på <https://security.microsoft.com> understøtter direkte administration af tilladelser for brugere, der udfører sikkerhedsopgaver i Microsoft 365. Ved hjælp af Microsoft 365 Defender-portalen til at administrere tilladelser kan du administrere tilladelser centralt for alle opgaver, der er relateret til sikkerhed.

Hvis du vil administrere tilladelser på Microsoft 365 Defender-portalen, skal du gå til **Tilladelser & roller** eller <https://security.microsoft.com/securitypermissions>. Du skal være **global administrator** eller medlem af rollegruppen **Organisationsadministration** på Microsoft 365 Defender-portalen. Rolleadministrationsrollen giver især brugerne mulighed for at få vist, oprette og redigere rollegrupper på Microsoft 365 Defender portalen, og rollen tildeles som standard kun til rollegruppen **Organisationsadministration**.

> [!NOTE]
> Du kan få oplysninger om tilladelser på Microsoft Purview-overholdelsesportalen [under Tilladelser på Microsoft Purview-overholdelsesportalen](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation mellem medlemmer, roller og rollegrupper

Tilladelser i Microsoft 365 Defender portalen er baseret på den rollebaserede tilladelsesmodel RBAC (Access Control). RBAC er den samme tilladelsesmodel, der bruges af de fleste Microsoft 365 tjenester, så hvis du har kendskab til tilladelsesstrukturen i disse tjenester, vil tildeling af tilladelser på Microsoft 365 Defender-portalen være meget velkendt.

En **rolle** giver tilladelser til at udføre et sæt opgaver.

En **rollegruppe** er et sæt roller, der gør det muligt for personer at udføre deres job på Microsoft 365 Defender portalen.

Microsoft 365 Defender portal-> indeholder standardrollegrupper til de mest almindelige opgaver og funktioner, du skal tildele. Generelt anbefaler vi, at du blot føjer individuelle brugere som **medlemmer** til standardrollegrupperne.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Relationen mellem en rollegruppe og dens roller og medlemmer" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Roller og rollegrupper på Microsoft 365 Defender-portalen

Følgende typer roller og rollegrupper er tilgængelige på siden **Tilladelser & roller** på <https://security.microsoft.com/securitypermissions> Microsoft 365 Defender-portalen:

- **Azure AD-roller**: Du kan få vist rollerne og tildelte brugere, men du kan ikke administrere dem direkte på Microsoft 365 Defender-portalen. Azure AD-roller er centrale roller, der tildeler tilladelser til **alle** Microsoft 365 tjenester.

- **Mail & samarbejdsroller**: Dette er de samme rollegrupper, der er tilgængelige i Security & Compliance Center, men du kan administrere dem direkte på Microsoft 365 Defender portalen. De tilladelser, du tildeler her, er specifikke for Microsoft 365 Defender-portalen, Microsoft Purview-overholdelsesportalen og Security & Compliance Center og dækker ikke alle de tilladelser, der er nødvendige i andre Microsoft 365 arbejdsbelastninger.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="Siden Tilladelser & roller på Microsoft 365 Defender-portalen" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Azure AD-roller på Microsoft 365 Defender-portalen

Når du åbner Microsoft 365 Defender portalen på <https://security.microsoft.com> og går til **Mail & samarbejdsroller** \> **Tilladelser & roller** \> **Azure AD-roller** \> (eller direkte til  <https://security.microsoft.com/aadpermissions>), får du vist de Azure AD-roller, der er beskrevet i dette afsnit.

Når du vælger en rolle, vises der et detaljeret pop op-vindue, der indeholder beskrivelsen af rollen og brugertildelingerne. Men hvis du vil administrere disse tildelinger, skal du klikke på **Administrer medlemmer i Azure AD** i det detaljerede pop op-vindue.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="Linket til administration af tilladelser i Azure Active Directory" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

Du kan få flere oplysninger under [Få vist og tildel administratorroller i Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rolle|Beskrivelse|
|---|---|
|**Global administrator**|Adgang til alle administrative funktioner i alle Microsoft 365-tjenester. Det er kun globale administratorer, der kan tildele andre administratorroller. Du kan få flere oplysninger under [Global administrator/Firmaadministrator](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrator af overholdelsesdata**|Hold styr på din organisations data på tværs af Microsoft 365, sørg for, at de er beskyttet, og få indsigt i eventuelle problemer, der kan hjælpe med at afhjælpe risici. Du kan få flere oplysninger under [Administrator af overholdelsesdata](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Overholdelsesadministrator**|Hjælp din organisation med at overholde alle lovmæssige krav, administrere eDiscovery-sager og vedligeholde politikker for datastyring på tværs af Microsoft 365 placeringer, identiteter og apps. Du kan få flere oplysninger under [Overholdelsesadministrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Sikkerhedsoperator**|Få vist, undersøg og reager på aktive trusler mod dine Microsoft 365 brugere, enheder og indhold. Du kan få flere oplysninger under [Sikkerhedsoperator](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Sikkerhedslæser**|Få vist og undersøg aktive trusler mod dine Microsoft 365 brugere, enheder og indhold, men (i modsætning til sikkerhedsoperatoren) har de ikke tilladelse til at reagere ved at udføre handlinger. Du kan få flere oplysninger under [Sikkerhedslæser](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Sikkerhedsadministrator**|Styr din organisations overordnede sikkerhed ved at administrere sikkerhedspolitikker, gennemgå sikkerhedsanalyser og -rapporter på tværs af Microsoft 365 produkter og holde dig opdateret om trusselslandskabet. Du kan få flere oplysninger under [Sikkerhedsadministrator](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Global læser**|Den skrivebeskyttede version af **rollen Global administrator**. Få vist alle indstillinger og administrative oplysninger på tværs af Microsoft 365. Du kan få flere oplysninger under [Global læser](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrator af simulering af angreb**|Opret og administrer alle aspekter af oprettelse af [simulering af angreb](attack-simulation-training.md) , start/planlægning af en simulering og gennemgang af simuleringsresultater. Du kan få flere oplysninger under [Administrator af simulering af angreb](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Forfatter af nyttedata til angreb**|Opret nyttedata for angreb, men start eller planlæg dem faktisk ikke. Du kan få flere oplysninger under [Forfatter af nyttedata for angreb](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Mail & samarbejdsroller på Microsoft 365 Defender-portalen

Når du åbner Microsoft 365 Defender portalen på <https://security.microsoft.com> og går til **Mail & samarbejdsroller** \> **Tilladelser & roller** \> **Mail & samarbejdsroller** \> (eller direkte til  <https://security.microsoft.com/emailandcollabpermissions>) får du vist de samme rollegrupper, som er tilgængelige i Security & Compliance Center.

Du kan få komplette oplysninger om disse rollegrupper [under Tilladelser i Security & Compliance Center](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Rediger medlemskab af mail & samarbejdsrolle på Microsoft 365 Defender-portalen

1. På Microsoft 365 Defender-portalen på <https://security.microsoft.com>skal du gå til **Mail & samarbejdsroller** \> **Tilladelser & roller** \> **Mail & samarbejdsroller** \> **roller**. Hvis du vil gå direkte til siden **Tilladelser** , skal du bruge <https://security.microsoft.com/emailandcollabpermissions>.

2. På siden **Tilladelser** skal du vælge den rollegruppe, du vil ændre, på listen. Du kan klikke på kolonneoverskriften **Navn** for at sortere listen efter navn, eller du **kan klikke på** ![søgesøgeikonet.](../../media/m365-cc-sc-search-icon.png) for at finde rollegruppen.

3. I det viste pop op-vindue med oplysninger om rollegrupper skal du klikke på **Rediger** i afsnittet **Medlemmer** .

4. Gør et af følgende på siden **Redigering vælg medlemmer** , der vises:
   - Hvis der ikke er nogen medlemmer af rollegruppen, skal du klikke på **Vælg medlemmer**.
   - Hvis der er eksisterende medlemmer af rollegruppen, skal du klikke på **Rediger**

5. I pop op-vinduet **Vælg medlemmer** , der vises, skal du gøre et af følgende:

   - Klik på **Tilføj**. Vælg en eller flere brugere på listen over brugere, der vises. Du kan også klikke på søgeikonet **Søg**![.](../../media/m365-cc-sc-search-icon.png) for at finde og vælge brugere.

     Når du har valgt de brugere, du vil tilføje, skal du klikke på **Tilføj**.

   - Klik på **Fjern**. Vælg et eller flere af de eksisterende medlemmer. Du kan også klikke på søgeikonet **Søg**![.](../../media/m365-cc-sc-search-icon.png) for at finde og vælge medlemmer.

     Når du har valgt de brugere, du vil fjerne, skal du klikke på **Fjern**.

6. Klik på **Udført** i pop op-vinduet **Vælg medlemmer**.

7. Klik på **Gem** på siden **Rediger vælg medlemmer**.

8. Klik på **Udført** i pop op-vinduet med oplysninger om rollegruppen.
