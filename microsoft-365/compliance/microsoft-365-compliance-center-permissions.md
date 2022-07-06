---
title: Tilladelser på Microsoft Purview-overholdelsesportalen
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Få mere at vide om administration af tilladelser i Microsoft Purview-compliance-portal.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
ms.openlocfilehash: b8e7f17ef22163e091307fda7cd0beb6659022dc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623845"
---
# <a name="permissions-in-the-microsoft-purview-compliance-portal"></a>Tilladelser på Microsoft Purview-overholdelsesportalen

Microsoft Purview-compliance-portal understøtter direkte administration af tilladelser for brugere, der udfører overholdelsesopgaver i Microsoft 365. Denne opdatering betyder, at du ikke længere behøver at bruge Office 365 Security & Compliance Center til at administrere tilladelser til løsninger til overholdelse af angivne standarder. Ved hjælp af den nye side **Tilladelser på overholdelsesportalen** kan du administrere tilladelser til brugere for overholdelsesopgaver i funktioner som enhedshåndtering, Microsoft Purview Forebyggelse af datatab, eDiscovery, styring af insiderrisiko, opbevaring og mange andre. Brugerne kan kun udføre de overholdelsesopgaver, som du eksplicit giver dem adgang til.

Hvis brugerne vil have vist fanen **Tilladelser på overholdelsesportalen** , skal de være globale administratorer eller have tildelt rollen *Rolleadministration* (en rolle tildeles kun rollegruppen *Organisationsadministration* ). *Rolleadministrationsrollen* giver brugerne mulighed for at få vist, oprette og redigere rollegrupper.

![Siden Tilladelser i Microsoft Purview-compliance-portal.](../media/m365-compliance-center-permissions.png)

Tilladelser i overholdelsesportalen er baseret på den rollebaserede adgangskontrolmodel (RBAC). RBAC er den samme tilladelsesmodel, der bruges af de fleste Microsoft 365-tjenester, så hvis du har kendskab til tilladelsesstrukturen i disse tjenester, kender du til at tildele tilladelser på overholdelsesportalen. Det er vigtigt at huske, at de tilladelser, der administreres på overholdelsesportalen, ikke dækker administrationen af alle de tilladelser, der er nødvendige i hver enkelt tjeneste. Du skal stadig administrere visse tjenestespecifikke tilladelser i Administration for den specifikke tjeneste. Hvis du f.eks. har brug for at tildele tilladelser til arkivering, overvågning og MRM-opbevaringspolitikker, skal du administrere disse tilladelser i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation mellem medlemmer, roller og rollegrupper

En rolle giver tilladelser til at udføre et sæt opgaver. Rollen Sagsstyring giver f.eks. brugerne mulighed for at arbejde med eDiscovery-sager.

En rollegruppe er et sæt roller, der gør det muligt for brugerne at udføre deres job på tværs af overholdelsesløsninger på overholdelsesportalen. Ved f.eks. at føje brugere til rollegruppen *Styring af insiderrisiko* er udpegede administratorer, analytikere, efterforskere og auditører konfigureret for de nødvendige tilladelser til styring af insiderrisiko i en enkelt gruppe. Overholdelsesportalen indeholder standardrollegrupper for opgaver og funktioner for hver overholdelsesløsning, som du skal tildele personer til. Generelt anbefaler vi, at du blot føjer individuelle brugere som medlemmer til standardrollegrupperne for overholdelse efter behov.

![Diagram, der viser relationen mellem rollegrupper og roller og medlemmer.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-compliance-portal"></a>Tilladelser, der er nødvendige for at bruge funktioner på overholdelsesportalen

Hvis du vil have vist alle de standardrollegrupper, der er tilgængelige på overholdelsesportalen, og de roller, der som standard er tildelt rollegrupperne, skal du se [Tilladelser i Security & Compliance Center](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

Administration af tilladelser på overholdelsesportalen giver kun brugere adgang til de funktioner til overholdelse af angivne standarder, der er tilgængelige på overholdelsesportalen. Hvis du vil give tilladelser til andre funktioner, der ikke findes på overholdelsesportalen, f.eks. exchange-regler for mailflow (også kaldet transportregler), skal du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

## <a name="azure-roles-in-the-compliance-portal"></a>Azure-roller på overholdelsesportalen

De roller, der vises i afsnittet **Azure AD** >  **Roles** på siden **med tilladelser til overholdelsesportalen**, er Azure Active Directory-roller. Disse roller er designet til at passe til jobfunktionerne i din organisations it-gruppe, hvilket gør det nemt at give en person alle de tilladelser, der er nødvendige for at få arbejdet udført. Du kan få vist de brugere, der i øjeblikket er tildelt hver rolle, ved at vælge en Administration rolle og få vist detaljerne for rollepanelet. Hvis du vil administrere medlemmer af en Azure AD rolle, skal du vælge Administrer medlemmer i Azure AD. Dette valg omdirigerer dig til Azure-administrationsportalen.

|Rolle|Beskrivelse|
|:---|:----------|
|**Global administrator**|Adgang til alle administrative funktioner i alle Microsoft 365-tjenester. Det er kun globale administratorer, der kan tildele andre administratorroller. Du kan få flere oplysninger under [Global administrator/Firmaadministrator](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrator af overholdelsesdata**|Hold styr på din organisations data på tværs af Microsoft 365, sørg for, at de er beskyttet, og få indsigt i eventuelle problemer, der kan hjælpe med at afhjælpe risici. Du kan få flere oplysninger under [Administrator af overholdelsesdata](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Overholdelsesadministrator**|Hjælp din organisation med at overholde alle lovmæssige krav, administrere eDiscovery-sager og vedligeholde politikker for datastyring på tværs af Microsoft 365-placeringer, -identiteter og -apps. Du kan få flere oplysninger under [Overholdelsesadministrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Sikkerhedsoperator**|Få vist, undersøg og reager på aktive trusler mod dine Microsoft 365-brugere, -enheder og -indhold. Du kan få flere oplysninger under [Sikkerhedsoperator](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Sikkerhedslæser**|Få vist og undersøg aktive trusler mod dine Microsoft 365-brugere, -enheder og -indhold, men (i modsætning til sikkerhedsoperatoren) har de ikke tilladelse til at svare ved at udføre handlinger. Du kan få flere oplysninger under [Sikkerhedslæser](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Sikkerhedsadministrator**|Styr din organisations overordnede sikkerhed ved at administrere sikkerhedspolitikker, gennemgå sikkerhedsanalyser og -rapporter på tværs af Microsoft 365-produkter og holde dig opdateret om trusselslandskabet. Du kan få flere oplysninger under [Sikkerhedsadministrator](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Global læser**|Den skrivebeskyttede version af **rollen Global administrator**. Få vist alle indstillinger og administrative oplysninger på tværs af Microsoft 365. Du kan få flere oplysninger under [Global læser](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrator af simulering af angreb**|Opret og administrer alle aspekter af oprettelse af simulering af angreb, start/planlægning af en simulering og gennemgang af simuleringsresultater. Du kan få flere oplysninger under [Administrator af simulering af angreb](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Forfatter af nyttedata til angreb**|Opret nyttedata for angreb, men start eller planlæg dem faktisk ikke. Du kan få flere oplysninger under [Forfatter af nyttedata for angreb](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Føj brugere til en rollegruppe for overholdelse af angivne standarder

Udfør følgende trin for at føje brugere til en rollegruppe for overholdelse af angivne standarder:

1. Log på tilladelsesområdet på overholdelsesportalen ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, og gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a> for at vælge linket for at få vist og administrere overholdelsesroller i Microsoft 365.
1. Udvid afsnittet **Overholdelsescenter,** og vælg **Roller**.
1. På siden **Overholdelsescenter-roller** skal du vælge en rollegruppe for overholdelse, som du vil føje brugere til, og derefter vælge **Rediger rollegruppe** i detaljeruden.
1. Vælg **Vælg medlemmer** i navigationsruden til venstre, og vælg derefter **Rediger**.
1. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil føje til rollegruppen.
1. Vælg **Tilføj**, og vælg derefter **Udført**.
1. Vælg **Gem** for at føje brugerne til rollegruppen. Vælg **Luk** for at fuldføre trinnene.

## <a name="remove-users-from-a-compliance-role-group"></a>Fjern brugere fra en rollegruppe for overholdelse af regler og standarder

Udfør følgende trin for at fjerne brugere fra en rollegruppe for overholdelse af angivne standarder:

1. Log på tilladelsesområdet på overholdelsesportalen ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, og gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a> for at vælge linket for at få vist og administrere overholdelsesroller i Microsoft 365.
1. Udvid afsnittet Overholdelsescenter, og vælg **Roller**.
1. Vælg en rollegruppe for overholdelse, som du vil fjerne brugere fra, på siden **Overholdelsescenter-roller** , og vælg derefter **Rediger rollegruppe** i detaljeruden.
1. Vælg **Vælg medlemmer** i navigationsruden til venstre, og vælg derefter **Rediger**.
1. Vælg **Fjern** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil fjerne fra rollegruppen.
1. Vælg **Fjern**, og vælg derefter **Udført**.
1. Vælg **Gem** for at fjerne brugerne fra rollegruppen. Vælg **Luk** for at fuldføre trinnene.

## <a name="create-a-custom-role-group"></a>Opret en brugerdefineret rollegruppe

Udfør følgende trin for at oprette en brugerdefineret rollegruppe:

1. Log på tilladelsesområdet på overholdelsesportalen ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, og gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a>.
1. På siden **Tilladelser & roller** skal du vælge **Overholdelsescenter > Roller**.
1. På siden **Overholdelsescenter-roller** skal du vælge **Opret**.
1. Angiv et navn til den brugerdefinerede rollegruppe i feltet **Navn** på siden **Navngiv din rollegruppe**. Navnet på rollegruppen kan ikke ændres efter oprettelsen af rollegruppen. Angiv evt. en beskrivelse af den brugerdefinerede rollegruppe i feltet **Beskrivelse** . Vælg **Næste** for at fortsætte.
1. Vælg **Vælg roller** på siden **Vælg roller**.
1. Vælg **Tilføj**, og vælg derefter de roller, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje rollegruppen, og vælg derefter **Udført**.
1. Vælg **Næste** for at fortsætte.
1. Vælg **Vælg medlemmer** på siden **Vælg medlemmer**.
1. Vælg **Tilføj**, og vælg derefter de medlemmer, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje medlemmerne, og vælg derefter **Udført**.
1. Vælg **Næste** for at fortsætte.
1. Gennemse detaljerne for den brugerdefinerede rollegruppe på siden **Gennemse dine indstillinger** . Hvis du har brug for at redigere oplysningerne, skal du vælge **Rediger** i det relevante afsnit. Når alle indstillingerne er korrekte, skal du vælge **Opret rollegruppe** for at oprette den brugerdefinerede rollegruppe eller vælge **Annuller** for at kassere ændringerne og ikke oprette den brugerdefinerede rollegruppe.

## <a name="update-a-custom-role-group"></a>Opdater en brugerdefineret rollegruppe

Fuldfør følgende trin for at opdatere en brugerdefineret rollegruppe:

1. Log på tilladelsesområdet på overholdelsesportalen ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, og gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a>.
1. På siden **Tilladelser & roller** skal du vælge **Overholdelsescenter > Roller**.
1. På siden **Med overholdelsescenters roller** skal du vælge den rollegruppe, der skal opdateres.
1. Vælg **Rediger rollegruppe** i detaljeruden for den valgte rollegruppe.
1. Opdater beskrivelsen af den brugerdefinerede rollegruppe i feltet **Beskrivelse** på siden **Redigering af rollegruppenavn**. Navnet på den brugerdefinerede rollegruppe kan ikke ændres.
1. På siden **Vælg roller** skal du vælge **Rediger** for at opdatere de roller, der er tildelt rollegrupperne.
1. Vælg **Tilføj**, og vælg derefter de roller, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje rollegruppen, og vælg derefter **Udført**.
1. På siden **Vælg medlemmer** skal du vælge **Rediger**.
1. Vælg **Tilføj**, og vælg derefter de medlemmer, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje medlemmerne, og vælg derefter **Udført**.
1. Vælg **Gem** for at gemme opdaterede værdier *for Beskrivelse*, *Rollegrupper* og *Medlemmer* .
1. Vælg **Luk** i detaljeruden for den valgte rollegruppe.

## <a name="delete-a-custom-role-group"></a>Slet en brugerdefineret rollegruppe

Fuldfør følgende trin for at opdatere en brugerdefineret rollegruppe:

1. Log på tilladelsesområdet på overholdelsesportalen ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, og gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**Tilladelser**</a>.
1. På siden **Tilladelser & roller** skal du vælge **Overholdelsescenter > Roller**.
1. På siden **Med overholdelsescenters roller** skal du vælge den rollegruppe, der skal opdateres.
1. Vælg **Slet rollegruppe** i detaljeruden for den valgte rollegruppe.
1. I dialogboksen **Advarsel** skal du vælge **Ja** for at slette rollegruppen eller vælge **Nej** for at annullere sletningen.
