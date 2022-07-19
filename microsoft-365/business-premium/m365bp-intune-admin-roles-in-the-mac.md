---
title: Om Intune administratorroller i Microsoft 365 Administration
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
description: Med Microsoft 365 Administration kan du administrere nogle Microsoft Intune roller, der knyttes til forretningsfunktioner og giver tilladelser til at udføre bestemte opgaver.
ms.openlocfilehash: ad630e7eac800e3c3c931f7ac6244c1e19e117a8
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66858935"
---
# <a name="intune-admin-roles-in-the-microsoft-365-admin-center"></a>Intune administratorroller i Microsoft 365 Administration

Dit Microsoft 365- eller Office 365-abonnement leveres med et sæt administratorroller, som du kan tildele til alle brugere i din organisation ved hjælp af <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. De enkelte administratorroller relaterer til almindelige forretningsfunktioner og giver personer tilladelse til at udføre bestemte opgaver i Administrationerne. Derfor er disse roller kun et undersæt af alle de roller, der er tilgængelige i Intune Administration, hvilket omfatter yderligere roller, der er specifikke for Intune sig selv.

Før du tilføjer bestemte Intune roller, skal rollerne tildeles i Azure AD. Hvis du vil se disse roller, skal du vælge **Endpoint Manager > lejeradministration > roller > Alle roller >**. Du kan administrere rollen på følgende sider:

- Egenskaber: Navn, beskrivelse, tilladelser og områdekoder for rollen.
- Tildelinger: En liste over rolletildelinger, der definerer, hvilke brugere der har adgang til hvilke brugere eller enheder. En rolle kan have flere tildelinger, og en bruger kan være i flere tildelinger.

## <a name="about-roles-based-access-control-in-intune"></a>Om rollebaseret adgangskontrol i Intune

Rollebaseret adgangskontrol hjælper dig med at administrere, hvem der har adgang til organisationens ressourcer, og hvad de kan gøre med disse ressourcer. Ved at tildele roller til dine Intune brugere kan du begrænse, hvad de kan se og ændre. Der er både indbyggede og brugerdefinerede roller, og hver rolle har et sæt tilladelser, der bestemmer, hvilke brugere med den pågældende rolle der kan få adgang til eller ændres i din organisation. Følgende oplysninger dækker begge typer roller i Intune.

Hvis du vil oprette, redigere eller tildele roller, skal din konto have en af følgende tilladelser i Azure AD:

- **Global administrator**
- **Intune-tjenesteadministrator** (også kendt som **Intune administrator**, men ikke at forveksle med rollen Intune **rolleadministrator**).

Find flere oplysninger om [Azure Active Directory-roller og RBAC](/azure/active-directory/roles/permissions-reference.md).

## <a name="microsoft-intune-built-in-roles"></a>Microsoft Intune indbyggede roller

Indbyggede roller bruger foruddefinerede regler, der er baseret på almindelige Intune scenarier. Brugerdefinerede roller er også baseret på regler, der er strengt defineret af dig. 

Her er de indbyggede roller, som du kan tildele:

|Administratorrolle     |Hvem skal have tildelt denne rolle?  |
|---------|---------|
|**Programstyring**     |   Tildel rollen Programadministrator til brugere, der administrerer programlivscyklussen for mobilapps, konfigurerer politikadministrerede apps og får vist enhedsoplysninger og konfigurationsprofiler.  |
|**Helpdesk-operatør**     |   Tildel rollen helpdeskoperator til brugere, der tildeler apps og politikker til brugere og enheder. |
|**Intune rolleadministrator**    |   Tildel Intune rolleadministrator til brugere, der kan tildele Intune tilladelser til andre administratorer og kan administrere brugerdefinerede og indbyggede Intune roller.   |
|**Politik- og profilstyring**     |   Tildel rollen politik- og profiladministrator til brugere, der administrerer politik for overholdelse af angivne standarder, konfigurationsprofiler og Apple-tilmelding.   |
|**Skrivebeskyttet operator**     |   Tildel rollen skrivebeskyttet operator til brugere, der kun kan få vist brugere, enheder, tilmeldingsoplysninger og konfigurationer.   |
|**Skoleadministrator**     |   Tildel skoleadministratorrollen til brugerne for at få fuld adgang til at administrere Windows 10-11- og iOS-enheder, -apps og -konfigurationer i Intune for Education.   |
|**Cloud-pc-administrator**     |   En Cloud PC-administrator har læse- og skriveadgang til alle cloud-pc-funktioner, der er placeret under bladet Cloud PC.   |
|**Cloud-pc-læser**     |   En Cloud PC Reader har læseadgang til alle Cloud PC-funktioner, der er placeret på bladet Cloud PC.   |

## <a name="microsoft-intune-custom-roles"></a>Microsoft Intune brugerdefinerede roller

Du kan oprette brugerdefinerede roller i Intune, der indeholder de tilladelser, der kræves til en bestemt jobfunktion. Hvis en it-afdelingsgruppe f.eks. administrerer programmer, politikker og konfigurationsprofiler, kan du tilføje alle disse tilladelser i én brugerdefineret rolle. Når du har oprettet en brugerdefineret rolle, kan du tildele den til alle brugere, der har brug for disse tilladelser.

På samme måde som med indbyggede roller skal din konto have en af følgende tilladelser i Azure AD for at oprette, redigere eller tildele roller:

- **Global administrator**
- **Intune-tjenesteadministrator** (også kendt som **Intune administrator**, men ikke at forveksle med rollen Intune **rolleadministrator**).

Sådan opretter du en brugerdefineret rolle:

1. I Microsoft Endpoint Manager Administration skal du vælge **Lejeradministration > Roller > Alle roller > Opret**.

1. Angiv et navn og en beskrivelse til den nye rolle på siden **Grundlæggende** , og vælg derefter **Næste**.

1. På siden **Tilladelser** skal du vælge de tilladelser, du vil bruge sammen med denne rolle.

1. På siden **Område (mærker)** skal du vælge mærkerne for denne rolle. Når denne rolle tildeles til en bruger, kan den pågældende bruger få adgang til ressourcer, der også har disse mærker. Vælg **Næste**.

1. På siden **Gennemse + opret** skal du vælge **Opret**, når du er færdig. Den nye rolle vises på listen på bladet **Intune roller – alle roller**.

Sådan kopierer du en rolle:

1. I Microsoft Endpoint Manager Administration skal du vælge **Lejeradministration > Roller > Alle roller >** markere afkrydsningsfeltet for en rolle på listen > **Dupliker**.

1. Angiv et navn på siden **Grundlæggende** . Sørg for at bruge et entydigt navn.

1. Alle tilladelser og områdekoder fra den oprindelige rolle er allerede valgt. Du kan efterfølgende ændre dubletrollens **navn, beskrivelse, tilladelser og omfang (mærker).**

1. Når du har foretaget alle de ønskede ændringer, skal du vælge Næste for at gå til siden Gennemse + opret. Vælg **Opret**.

> [!Note]
>Hvis du vil administrere Intune skal du have tildelt en Intune licens. Du kan også give brugere uden licens tilladelse til at administrere Intune ved **at angive Tillad adgang til administratorer uden licens** til **Ja**.

## <a name="how-to-assign-a-role"></a>Sådan tildeler du en rolle

Du kan tildele en indbygget eller brugerdefineret rolle til en Intune bruger. Hvis du vil oprette, redigere eller tildele roller, skal din konto have en af følgende tilladelser i Azure AD:

- **Global administrator**
- **Intune-tjenesteadministrator** (også kendt som **Intune administrator**, men ikke at forveksle med rollen Intune **rolleadministrator**).

1. I Microsoft Endpoint Manager Administration skal du vælge **Lejeradministration > Roller > Alle roller**.

1. På bladet **Endpoint Manager roller – Alle roller** skal du vælge den indbyggede rolle, du vil tildele > Tildelinger > + Tildel.

1. Angiv et **tildelingsnavn og en valgfri tildelingsbeskrivelse** på siden Grundlæggende, og vælg derefter **Næste**.

1. På siden **Administration grupper** skal du vælge den gruppe, der indeholder den bruger, du vil give tilladelserne til. Vælg **Næste**.

1. På siden **Område (grupper)** skal du vælge en gruppe, der indeholder de brugere og enheder, som ovenstående medlem har tilladelse til at administrere. Du har også mulighed for at vælge alle brugere eller alle enheder. Vælg **Næste**.

> [!Note]
> **Alle brugere** og **alle enheder** er **Intune virtuelle grupper** og ikke Azure Active Directory-sikkerhedsgrupper (Azure AD). Derfor kan du til tildelingsformål for **område (grupper)** ikke bruge dem som overordnede til Azure AD sikkerhedsgrupper. Hvis du har brug for både **Alle brugere** og **Alle enheder** og specifikke Azure AD sikkerhedsgrupper for **områdetildelinger (grupper),** skal du tilføje dem separat med separate tildelinger. Ellers har administratoren i denne rolle ikke adgang til bestemte Azure AD brugergrupper, selvom områdetildelingen (grupper) for en rolle er angivet til **Alle brugere**. Indlejring understøttes for Azure AD sikkerhedsgrupper.

6. På siden **Område (mærker)** skal du vælge mærker, hvor denne rolletildeling skal anvendes. Vælg **Næste**.

7. På siden **Gennemse + Opret** skal du vælge **Opret**, når du er færdig. Den nye tildeling vises på listen over tildelinger.

> [!Note]
> Når du opretter områdegrupper og tildeler et områdemærke, kan du kun bruge de målgrupper, der er angivet i Området (grupper) for din rolletildeling.

## <a name="delegated-administration-for-microsoft-partners"></a>Stedfortræderadministration til Microsoft-partnere

Hvis du arbejder med en Microsoft-partner, kan du tildele vedkommende administratorroller. De kan til gengæld tildele brugere i din virksomhed - eller deres firma - administratorroller. Det kan du eksempelvis gøre brug af, hvis de konfigurerer og administrerer din online-organisation for dig.
  
En partner kan tildele disse roller: 
  
- Fuld administration, som har rettigheder, der svarer til en global administrator, bortset fra administration af multifaktorgodkendelse via Partnercenter.

- Begrænset administration, som har rettigheder, der svarer til en helpdesk-administrator.

Før partneren kan tildele disse roller til brugere, skal du føje partneren til din konto, som delegeret administrator. Denne proces startes af en autoriseret partner. Partneren sender dig en mail for at spørge dig, om du vil give vedkommende tilladelse til at fungere som delegeret administrator. Du kan finde en vejledning under [Godkend eller fjern partnerrelationer](../admin/misc/add-partner.md).
  
## <a name="related-content"></a>Relateret indhold

[Om Microsoft 365-administratorroller](../admin/add-users/about-admin-roles.md) (artikel)\
[Tildel administratorroller](../admin/add-users/assign-admin-roles.md) (artikel)\
[Aktivitetsrapporter i Microsoft 365 Administration](../admin/activity-reports/activity-reports.md) (artikel)
