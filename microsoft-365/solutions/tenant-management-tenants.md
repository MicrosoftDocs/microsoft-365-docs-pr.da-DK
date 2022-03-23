---
title: Trin 1. Dine Microsoft 365 for virksomhedslejere
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Installér og administrer enkelt- eller Microsoft 365 lejere med muligheder for multi-geo og flytningsplaceringer.
ms.openlocfilehash: 305d7683413d5682c0dddda418e87de0a0a682b7
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63593385"
---
# <a name="step-1-your-microsoft-365-for-enterprise-tenants"></a>Trin 1. Dine Microsoft 365 for virksomhedslejere

En af dine første lejerbeslutninger er, hvor mange der skal have. Hver Microsoft 365 lejer er særskilt, entydig og adskilt fra alle Microsoft 365 lejere. Dens tilsvarende Azure AD-lejer er også særskilt, entydig og adskilt fra alle Microsoft 365 lejere.

## <a name="single-tenant"></a>Enkelt lejer
Med en enkelt lejer forenkles mange aspekter af organisationens brug af Microsoft 365. En enkelt lejer betyder en enkelt Azure AD-lejer med et enkelt sæt konti, grupper og politikker. Tilladelser og deling af ressourcer på tværs af organisationen kan udføres via denne centrale identitetsudbyder.

En enkelt lejer giver dig det mest funktionsrige og forenklede samarbejde og din produktivitetsoplevelse for dine brugere.

Her er et eksempel, der viser standardplaceringen og Azure AD-lejeren for Microsoft 365 lejer.

![En enkelt Microsoft 365 lejer med sin Azure AD-lejer.](../media/tenant-management-overview/tenant-management-example-tenant.png)

## <a name="multiple-tenants"></a>Flere lejere

Der er mange grunde til, at din organisation kan have flere lejere:

- Administrativ isolation
- Decentraliseret it
- Historiske beslutninger
- Fusioner, overtagelser eller afhændelser
- Ryd adskillelse af branding for conglomerate organisationer
- Lejere inden produktion, test eller sandkasse

Her er et eksempel på en organisation, der har to lejere (Lejer A og Lejer B) i det samme standarddatacenter geo. Hver lejer som en separat Azure AD-lejer.

![Flere Microsoft 365 lejere med deres egne Azure AD-lejere.](../media/tenant-management-overview/tenant-management-example-multi-tenant.png)

Når du har flere lejere, er der begrænsninger og yderligere overvejelser, når du administrerer dem og leverer tjenester til brugerne.

### <a name="inter-tenant-collaboration"></a>Samarbejde mellem lejere

Hvis du ønsker, at dine brugere skal samarbejde mere effektivt på tværs af forskellige lejere i Microsoft 365 på en sikker måde, omfatter indstillinger for samarbejde mellem lejere at bruge en central placering til filer og samtaler, deling af kalendere, chat, lyd-/videoopkald til kommunikation og sikring af adgang til ressourcer og programmer.

Du kan finde flere oplysninger [Microsoft 365 samarbejde mellem lejere](../enterprise/microsoft-365-inter-tenant-collaboration.md).

### <a name="cross-tenant-mailbox-migration-preview"></a>Overførsel af postkasse på tværs af lejere (forhåndsvisning)

Før overførslen af postkasser på tværs af lejere (i forhåndsvisning) skal du, når du flytter Exchange Online-postkasser mellem lejere, helt fjerne en brugerpostkasse fra deres nuværende lejer (kildelejeren) til en lokal lejer og derefter onboarde dem til en ny lejer (mållejeren). Med den nye funktion til overførsel af postkasser på tværs af lejere kan lejeradministratorer i både kilde- og mållejeren flytte postkasser mellem lejere med minimal infrastrukturafhængigheder i deres lokale systemer. Dette fjerner behovet for postkasser uden for tavlen og i gang.

Her er to eksempler på lejere og deres postkasser før overførsel af postkasser på tværs af lejere.

![Flere Microsoft 365 lejere og deres postkasser.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-before.png)

I denne illustration har to separate lejere deres egne domæner og sæt af Exchange postkasser.

Her er mållejeren (Lejer A) efter overførsel af postkasse på tværs af lejere.

![Mållejeren efter overførsel af postkasse på tværs af lejere.](../media/tenant-management-overview/tenant-management-cross-tenant-mailbox-after.png)

I denne illustration har en enkelt lejer både domæner og begge sæt af Exchange postkasser.

Du kan få mere at vide under [Overførsel af postkasse på tværs af lejere](../enterprise/cross-tenant-mailbox-migration.md).

### <a name="tenant-to-tenant-migrations"></a>Lejer-til-lejer-migrering

Der er flere arkitektoniske metoder til fusioner, overtagelser, frasalg og andre scenarier, der kan føre dig til at overføre en eksisterende Microsoft 365 lejer til en ny lejer. 

Du kan finde en detaljeret [vejledning Microsoft 365 lejer-til-lejer-migrering.](../enterprise/microsoft-365-tenant-to-tenant-migrations.md)

## <a name="multi-geo-for-a-tenant"></a>Multi-Geo for en lejer

Med Microsoft 365 Multi-Geo kan du klargøre og gemme data på et andet datacenters geoplaceringer, som du har valgt at opfylde krav til dataopbevaring, og på samme tid låse op for din globale udrulning af moderne produktivitetsoplevelser til dine medarbejdere.

I et Multi-Geo-miljø består din Microsoft 365-lejer af en standard eller central placering, hvor dit Microsoft 365-abonnement oprindeligt blev oprettet, og en eller flere satellitplaceringer. I en lejer med flere geografiske placeringer masteres oplysningerne om geoplaceringer, grupper og brugeroplysninger i en global Azure AD-lejer. Da dine lejeroplysninger masteres centralt og synkroniseres til hver geoplacering, deles samarbejdsoplevelser med alle fra virksomheden på tværs af placeringerne.

Her er et eksempel på en organisation, der har sin standardplacering i Europa og en satellitplacering i Nordamerika. Begge placeringer deler den samme globale Azure AD-lejer for den enkelte Microsoft 365 lejer.

![Eksempel på en multi-geo Microsoft 365 lejer.](../media/tenant-management-overview/tenant-management-example-multi-geo.png)

Du kan finde flere oplysninger [Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

## <a name="moving-core-data-to-a-new-datacenter-geo"></a>Flytning af kernedata til et nyt datacenters geocenter

Microsoft fortsætter med at åbne nye datacenter-geos for Microsoft 365 tjenester. Disse nye datacentre tilføjer kapacitet og beregner ressourcer for at understøtte vores fortsatte kundebehov og forbrugsvækst. Desuden tilbyder det nye datacenter geos in-geo-dataopbevaring for kernekundedata.

Selvom åbning af et nyt datacenters geo ikke påvirker dig og dine kernedata, der er gemt i et allerede eksisterende datacenter geo, giver Microsoft dig mulighed for at anmode om en tidlig overførsel af din organisations kerne kundedata in rest-to-a new datacenter geo.

Her er et eksempel, hvor en Microsoft 365-lejer blev flyttet fra datacenteret for EU (EU) til det datacenter, der er placeret i Storbritannien.

![Eksempel på flytning af Microsoft 365 mellem datacenter-geos.](../media/tenant-management-overview/tenant-management-example-tenant-move.png)

Få mere at vide under [Flytning af kernedata til Microsoft 365 datacenter geos](../enterprise/moving-data-to-new-datacenter-geos.md).

## <a name="products-and-licenses-for-a-tenant"></a>Produkter og licenser til en lejer

Din Microsoft 365 lejer bliver oprettet, når du køber dit første produkt, f.eks. Microsoft 365 E3. Sammen med produktet er licenser, som opkræves et månedligt eller årligt gebyr. En administrator tildeler derefter en tilgængelig licens fra et af dine produkter til en brugerkonto, enten direkte eller via gruppemedlemskab. Afhængigt af din organisations forretningsmæssige behov kan du have et sæt produkter, hver med deres egen licenspulje. 

Fastlæggelse af produktsættet og antallet af licenser for hver kræver planlægning for at:

- Sørg for, at du har nok licenser til de brugerkonti, der har brug for avancerede funktioner.
- Undgå, at du løber tør for licenser eller har for mange ikke-tildelte licenser baseret på ændringer i medarbejderansatte i organisationen.


## <a name="results-of-step-1"></a>Resultater af trin 1

For dine Microsoft 365 for virksomhedslejere har du fastlagt:

- Hvor mange lejere du har eller har brug for.
- For hver lejer, hvilke produkter og licenser der skal købes.
- Om en lejer skal være Multi-Geo for at overholde krav til dataopbevaring.
- Uanset om du har brug for at konfigurere samarbejde mellem lejere.
- Uanset om du har brug for at overføre én lejer til en anden.
- Uanset om du har brug for at flytte kernedata fra ét datacenter geo til et nyt.

Her er et eksempel på en ny lejer.

![Eksempel på en ny lejer.](../media/tenant-management-overview/tenant-management-tenant-build-step1.png)

I denne illustration har lejeren:

- En standardplacering, der svarer til Microsoft 365 datacenter geo.
- Et sæt produkter og licenser.
- Sættet af produktivitetsapps i skyen, hvoraf nogle er specifikke for produkter.
- En Azure AD-lejer, der indeholder globale administratorkonti og et indledende DNS-domænenavn.

Efterhånden som vi bevæger os gennem de ekstra trin i denne løsning, bygger vi denne figur ud.

## <a name="ongoing-maintenance-for-tenants"></a>Løbende vedligeholdelse for lejere

Du kan løbende få brug for at:

- Tilføj en ny lejer.
- Føj nye produkter til en lejer med det første antal licenser.
- Rediger licenssættet for et produkt i en lejer for at justere for ændring af personalekrav.
- Flyt dine kernedata fra en lejer til et nyt datacenters geografiske placering.
- Tilføje krav til multi-geo for dataopbevaring.
- Konfigurer samarbejde mellem lejere.

## <a name="next-step"></a>Næste trin

[![Trin 2. Optimer din lejer til netværk for at få adgang.](../media/tenant-management-overview/tenant-management-step-grid-networking.png)](tenant-management-networking.md)

Fortsæt med [netværket](tenant-management-networking.md) for at levere optimale netværk fra dine medarbejdere Microsoft 365 skytjenester.
