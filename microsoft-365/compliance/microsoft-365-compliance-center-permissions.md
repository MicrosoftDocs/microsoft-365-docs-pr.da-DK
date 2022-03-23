---
title: Tilladelser i Microsoft 365 Overholdelsescenter
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
ms.service: O365-seccomp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
description: Få mere at vide om administration af tilladelser Microsoft 365 Overholdelsescenter.
ms.collection: M365-security-compliance
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkEXCHANGE
ms.openlocfilehash: 45540713452b91da171f6fc52eef8210fa256c4e
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63592438"
---
# <a name="permissions-in-the-microsoft-365-compliance-center"></a>Tilladelser i Microsoft 365 Overholdelsescenter

The Microsoft 365 Overholdelsescenter er blevet opdateret for nylig og understøtter nu direkte administration af tilladelser for brugere, der udfører overholdelsesopgaver Microsoft 365. Denne opdatering betyder, at du ikke længere behøver at bruge Office 365 Security & Compliance Center til at administrere tilladelser til overholdelse af regler og standarder. Ved hjælp af  den nye side Tilladelser i Microsoft 365 Overholdelsescenter kan du administrere tilladelser til brugere med henblik på overholdelse af regler og standarder i funktioner som administration af enheder, forebyggelse af datatab, eDiscovery, insider-risikostyring, opbevaring og mange andre. Brugere kan kun udføre de overholdelsesopgaver, som du udtrykkeligt giver dem adgang til.

For at få  vist fanen Tilladelser i Microsoft 365 Overholdelsescenter skal brugerne være globale administratorer eller være tildelt rollen rollestyring (en rolle er kun tildelt rollegruppen Organisationsadministration).  *Rollestyringsrollen* giver brugerne mulighed for at få vist, oprette og redigere rollegrupper.

![Siden Tilladelser i Microsoft 365 Overholdelsescenter.](../media/m365-compliance-center-permissions.png)

Tilladelserne i Microsoft 365 Overholdelsescenter er baseret på den rollebaserede adgangskontrolmodel (RBAC). RBAC er den samme tilladelsesmodel, der bruges af de fleste Microsoft 365-tjenester, så hvis du kender til tilladelsesstrukturen i disse tjenester, vil tildeling af tilladelser i Microsoft 365 Overholdelsescenter være velkendt. Det er vigtigt at huske, at tilladelserne, der administreres i Microsoft 365 Overholdelsescenter, ikke dækker administrationen af alle de tilladelser, der er nødvendige for hver enkelt tjeneste. Du skal stadig administrere bestemte tjenestespecifikke tilladelser i Administration for den specifikke tjeneste. Hvis du f.eks. skal tildele tilladelser til arkiverings-, overvågnings- og MRM-opbevaringspolitikker, skal du administrere disse tilladelser <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>.

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation mellem medlemmer, roller og rollegrupper

En rolle giver tilladelse til at udføre en række opgaver. Eksempelvis giver sagsadministrationsrollen brugerne mulighed for at arbejde med eDiscovery-sager.

En rollegruppe er et sæt roller, der giver brugerne mulighed for at udføre deres opgaver på tværs af overholdelsesløsninger, Microsoft 365 Overholdelsescenter. Ved f.eks. at føje brugere til rollegruppen *Insider Risk Management* konfigureres udpegede administratorer, analytikere, administratorer og revisorer til de nødvendige insider-risikostyringstilladelser i en enkelt gruppe. Opgavegruppen Microsoft 365 Overholdelsescenter standardrollegrupper for opgaver og funktioner for hver overholdelsesløsning, som du skal tildele personer til. Generelt anbefaler vi, at du blot føjer individuelle brugere som medlemmer til standardgrupper for overholdelse af regler og standarder efter behov.

![Diagram, der viser relationen mellem rollegrupper og roller og medlemmer.](../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png)

## <a name="permissions-needed-to-use-features-in-the-microsoft-365-compliance-center"></a>Tilladelser, der er nødvendige for at bruge funktionerne i Microsoft 365 Overholdelsescenter

Hvis du vil have vist alle standardrollegrupperne, der er tilgængelige i Microsoft 365 Overholdelsescenter og de roller, der er tildelt rollegrupperne som standard, skal du se Tilladelser i [Sikkerheds- & Overholdelsescenter](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

Administration af tilladelser i Microsoft 365 Overholdelsescenter giver kun brugerne adgang til de overholdelsesfunktioner, der er tilgængelige i Microsoft 365 Overholdelsescenter. Hvis du vil give tilladelser til andre funktioner, der ikke findes i Microsoft 365 Overholdelsescenter, f.eks. Exchange regler for mailflow (også kaldet transportregler), skal du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>.

## <a name="azure-roles-in-the-microsoft-365-compliance-center"></a>Azure-roller i Microsoft 365 Overholdelsescenter

De roller, der vises i **sektionen Azure** **ADRoles** >  på siden Microsoft 365 Overholdelsescenter **Tilladelser**, er Azure Active Directory roller. Disse roller er designet til at justere efter jobfunktioner i organisationens it-gruppe, hvilket gør det nemt at give en person alle de nødvendige tilladelser for at få arbejdet gjort. Du kan få vist de brugere, der aktuelt er tildelt til hver rolle, ved at vælge en administratorrolle og få vist oplysninger om rollepanelet. Hvis du vil administrere medlemmer af en Azure AD-rolle, skal du vælge Administrer medlemmer i Azure AD. Denne valgmulighed omdirigerer dig til Azure-administrationsportalen.

|Rolle|Beskrivelse|
|:---|:----------|
|**Global administrator**|Adgang til alle administrative funktioner i Microsoft 365 tjenester. Kun globale administratorer kan tildele andre administratorroller. Du kan finde flere oplysninger [under Global administrator/virksomhedsadministrator](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Dataadministrator for overholdelse af regler og standarder**|Hold styr på din organisations data på tværs af Microsoft 365, sørg for, at de er beskyttet, og få indsigt i eventuelle problemer for at reducere risici. Du kan få mere at vide under [Dataadministrator for overholdelse af regler og standarder](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Overholdelsesadministrator**|Hjælp din organisation med at overholde eventuelle lovmæssige krav, administrer eDiscovery-sager og vedligehold politikker for datastyring på tværs Microsoft 365 placeringer, identiteter og apps. Du kan få mere at vide under [Overholdelsesadministrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Sikkerhedsoperatør**|Få vist, undersøg og svar på aktive trusler mod Microsoft 365 brugere, enheder og indhold. Du kan finde flere oplysninger under [Sikkerhedsoperator](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Sikkerhedslæser**|Få vist og undersøg aktive trusler mod dine Microsoft 365-brugere, enheder og indhold, men (i modsætning til sikkerhedsoperatøren) har de ikke tilladelse til at reagere ved at gøre noget. Du kan finde flere oplysninger under [Sikkerhedslæser](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Sikkerhedsadministrator**|Styr din organisations overordnede sikkerhed ved at administrere sikkerhedspolitikker, gennemse sikkerhedsanalyser og rapporter på tværs af Microsoft 365-produkter og holde dig i gang med at arbejde i trusselsbilledet. Du kan finde flere oplysninger under [Sikkerhedsadministrator](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Global læser**|Den skrivebeskyttede version af **rollen Global** administrator. Få vist alle indstillinger og administrative oplysninger på tværs Microsoft 365. Du kan finde flere oplysninger [under Global læser](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Angrebssimuleringsadministrator**|Opret og administrer alle aspekter af oprettelse af angreb, start/planlægning af en simulering og gennemgang af simuleringsresultater. Du kan få mere at vide under [Administrator for angrebssimulering](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Forfatter til angrebsindlæsning**|Opret angrebsbelastninger, men start eller planlæg dem ikke rent faktisk. Få mere at vide under [Forfatter til angrebsindlæsning](/azure/active-directory/roles/permissions-reference#attack-payload-author).|
|

## <a name="add-users-to-a-compliance-role-group"></a>Føje brugere til en overholdelsesrollegruppe

Udfør følgende trin for at føje brugere til en overholdelsesrollegruppe:

1. Log på tilladelsesområdet i Microsoft 365 Overholdelsescenter ved hjælp af legitimationsoplysninger for en administratorkonto i Microsoft 365-organisationen, og gå til Tilladelser for at vælge linket for at få vist og administrere <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**overholdelsesroller**</a> i Microsoft 365.
1. Udvid afsnittet **Overholdelsescenter** , og vælg **Roller**.
1. På siden **Roller for Overholdelsescenter** skal du vælge en overholdelsesrollegruppe, du vil føje brugere til, og derefter vælge Rediger **rollegruppe** i detaljeruden.
1. Vælg **Vælg medlemmer** i venstre navigationsrude, og vælg derefter **Rediger**.
1. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle brugere, du vil føje til rollegruppen.
1. Vælg **Tilføj**, og vælg derefter **Udført**.
1. Vælg **Gem** for at føje brugerne til rollegruppen. Vælg **Luk** for at fuldføre trinnene.

## <a name="remove-users-from-a-compliance-role-group"></a>Fjern brugere fra en overholdelsesrollegruppe

Udfør følgende trin for at fjerne brugere fra en overholdelsesrollegruppe:

1. Log på tilladelsesområdet i Microsoft 365 Overholdelsescenter ved hjælp af legitimationsoplysninger for en administratorkonto i Microsoft 365-organisationen, og gå til Tilladelser for at vælge linket for at få vist og administrere <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**overholdelsesroller**</a> i Microsoft 365.
1. Udvid afsnittet Overholdelsescenter, og vælg **Roller**.
1. På siden **Roller for Overholdelsescenter** skal du vælge en overholdelsesrollegruppe, du vil fjerne brugere fra, og derefter vælge Rediger **rollegruppe** i detaljeruden.
1. Vælg **Vælg medlemmer** i venstre navigationsrude, og vælg derefter **Rediger**.
1. Vælg **Fjern** , og markér derefter afkrydsningsfeltet for alle brugere, du vil fjerne fra rollegruppen.
1. Vælg **Fjern**, og vælg derefter **Udført**.
1. Vælg **Gem** for at fjerne brugerne fra rollegruppen. Vælg **Luk** for at fuldføre trinnene.

## <a name="create-a-custom-role-group"></a>Opret en brugerdefineret rollegruppe

Udfør følgende trin for at oprette en brugerdefineret rollegruppe:

1. Log på området for tilladelser i Microsoft 365 Overholdelsescenter ved hjælp af legitimationsoplysninger for en administratorkonto i Microsoft 365, og gå <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**til Tilladelser**</a>.
1. På siden **Tilladelser & skal du** vælge **Overholdelsescenter > Roller**.
1. På siden **Roller for Overholdelsescenter** skal du vælge **Opret**.
1. På siden **Navngive din rollegruppe** skal du angive et navn til den brugerdefinerede rollegruppe i **feltet** Navn. Navnet på rollegruppen kan ikke ændres efter oprettelse af rollegruppen. Hvis det er nødvendigt, kan du angive en beskrivelse af den brugerdefinerede rollegruppe **i feltet** Beskrivelse. Vælg **Næste for** at fortsætte.
1. På siden **Vælg roller** skal du vælge **Vælg roller**.
1. Vælg **Tilføj**, og vælg derefter de roller, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje rollegruppen, og vælg derefter **Udført**.
1. Vælg **Næste for** at fortsætte.
1. På siden **Vælg medlemmer** skal du vælge **Vælg medlemmer**.
1. Vælg **Tilføj**, og vælg derefter de medlemmer, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje medlemmer, og vælg derefter **Udført**.
1. Vælg **Næste for** at fortsætte.
1. Gennemgå oplysningerne **om den brugerdefinerede** rollegruppe på siden Gennemse dine indstillinger. Hvis du vil redigere oplysningerne, skal du vælge **Rediger** i den relevante sektion. Når alle indstillingerne er korrekte, skal du  vælge Opret rollegruppe for at oprette den brugerdefinerede rollegruppe eller vælge Annuller for at annullere ændringerne og ikke oprette den brugerdefinerede rollegruppe.

## <a name="update-a-custom-role-group"></a>Opdatere en brugerdefineret rollegruppe

Udfør følgende trin for at opdatere en brugerdefineret rollegruppe:

1. Log på området for tilladelser i Microsoft 365 Overholdelsescenter ved hjælp af legitimationsoplysninger for en administratorkonto i Microsoft 365, og gå <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**til Tilladelser**</a>.
1. På siden **Tilladelser & skal du** vælge **Overholdelsescenter > Roller**.
1. På siden Roller **for Overholdelsescenter skal** du vælge den rollegruppe, der skal opdateres.
1. Vælg Rediger rollegruppe i detaljeruden for den **valgte rollegruppe**.
1. På siden **Redigeringsrollegruppenavn** skal du opdatere beskrivelsen af den brugerdefinerede rollegruppe i **feltet** Beskrivelse. Navnet på den brugerdefinerede rollegruppe kan ikke ændres.
1. På siden **Vælg roller skal** du vælge Rediger **for at** opdatere de roller, der er tildelt rollegrupperne.
1. Vælg **Tilføj**, og vælg derefter de roller, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje rollegruppen, og vælg derefter **Udført**.
1. På siden **Vælg medlemmer** skal du vælge **Rediger**.
1. Vælg **Tilføj**, og vælg derefter de medlemmer, der skal føjes til den brugerdefinerede rollegruppe. Vælg **Tilføj** for at tilføje medlemmer, og vælg derefter **Udført**.
1. Vælg **Gem** for at gemme *opdaterede* værdier *for Beskrivelse*, *Rollegrupper og* Medlemmer.
1. Vælg Luk i detaljeruden for den valgte **rollegruppe**.

## <a name="delete-a-custom-role-group"></a>Slette en brugerdefineret rollegruppe

Udfør følgende trin for at opdatere en brugerdefineret rollegruppe:

1. Log på området for tilladelser i Microsoft 365 Overholdelsescenter ved hjælp af legitimationsoplysninger for en administratorkonto i Microsoft 365, og gå <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**til Tilladelser**</a>.
1. På siden **Tilladelser & skal du** vælge **Overholdelsescenter > Roller**.
1. På siden Roller **for Overholdelsescenter skal** du vælge den rollegruppe, der skal opdateres.
1. Vælg Slet rollegruppe i detaljeruden for den valgte **rollegruppe**.
1. I dialogboksen **Advarsel** skal du vælge **Ja for** at slette rollegruppen eller vælge **Nej for** at annullere sletningsprocessen.
