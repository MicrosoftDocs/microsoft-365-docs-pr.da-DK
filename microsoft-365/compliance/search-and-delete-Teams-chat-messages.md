---
title: Søg efter og slet chatbeskeder i Teams
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 3526fd06-b45f-445b-aed4-5ebd37b3762a
description: Brug eDiscovery (Premium) og Microsoft Graph Explorer til at søge efter og fjerne chatbeskeder i Microsoft Teams og reagere på dataspildhændelser i Teams.
ms.openlocfilehash: 372293e11ee16498746da69c824a91abd108f2cf
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66858930"
---
# <a name="search-and-purge-chat-messages-in-teams-preview"></a>Søg efter og fjern chatbeskeder i Teams (prøveversion)

Du kan bruge eDiscovery (Premium) og Microsoft Graph Explorer til at søge efter og slette chatbeskeder i Microsoft Teams. Dette kan hjælpe dig med at finde og fjerne følsomme oplysninger eller upassende indhold. Denne arbejdsproces til søgning og fjernelse hjælper dig også med at reagere på en dataspildhændelse, når indhold, der indeholder fortrolige eller skadelige oplysninger, frigives via Teams-chatmeddelelser.

> [!NOTE]
> Denne artikel gælder for Microsoft 365 Enterprise organisationer. Understøttelse af US Government-cloudmiljøet (herunder GCC, GCC High og DoD) kommer snart.

## <a name="before-you-search-and-purge-chat-messages"></a>Før du søger efter og fjerner chatbeskeder

- Hvis du vil oprette en eDiscovery-sag (Premium) og bruge samlinger til at søge efter chatbeskeder, skal du være medlem af **rollegruppen eDiscovery Manager** i Microsoft Purview-compliance-portal. Hvis du vil slette chatbeskeder, skal du have tildelt rollen **Søg og fjern** . Denne rolle er som standard tildelt rollegrupperne Data investigator og Organisationsadministration. Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser](assign-ediscovery-permissions.md).
- Søgning og tømninger understøttes for samtaler i din lejer. Understøttelse af Teams Connect-chatsamtaler (ekstern adgang eller sammenslutning) er aktiveret i grænsefladen i nogle tilfælde, men fungerer ikke efter hensigten.
- Der kan maksimalt fjernes 10 elementer pr. postkasse på én gang. Da muligheden for at søge efter og fjerne chatbeskeder er beregnet til at være et værktøj til svar på hændelser, hjælper denne grænse med at sikre, at chatbeskeder fjernes hurtigt.

## <a name="search-and-purge-workflow"></a>Søg i og fjern arbejdsproces

Her er den proces, du skal bruge til at søge efter og fjerne Teams-chatmeddelelser:

![Arbejdsproces, der skal søge efter og fjerne Teams-chatmeddelelser.](../media/TeamsSearchAndPurgeWorkflow.png)

## <a name="step-1-create-a-case-in-ediscovery-premium"></a>Trin 1: Opret en sag i eDiscovery (Premium)

Det første trin er at oprette en sag i eDiscovery (Premium) for at administrere søge- og tømningen. Du kan få oplysninger om, hvordan du opretter en sag, [under Brug det nye sagsformat](advanced-ediscovery-new-case-format.md).

## <a name="step-2-create-a-draft-collection"></a>Trin 2: Opret en kladdesamling

Når du har oprettet en sag, er det næste trin at oprette en kladdesamling for at søge efter de Teams-chatmeddelelser, du vil fjerne. Den rensningsproces, du udfører, er trin 5, hvor alle elementer, der findes i kladdesamlingen, fjernes.

I eDiscovery (Premium) er en *samling* en eDiscovery-søgning på de Teams-indholdsplaceringer, der indeholder de chatbeskeder, du vil fjerne. Opret kladdesamlingen i det tilfælde, du oprettede i det forrige trin. Få mere at vide under [Opret et kladde-datasæt](create-draft-collection.md).

### <a name="data-sources-for-chat-messages"></a>Datakilder til chatbeskeder

Brug følgende tabel til at afgøre, hvilke datakilder der skal søges efter, afhængigt af hvilken type chatmeddelelse du skal fjerne.

| Til denne type chat...|Søg i denne datakilde...|
|:---------|:---------|
|Teams 1:1-chatsamtaler     |Chatdeltageres postkasse.|
|Teams: Gruppechats     |Chatdeltageres postkasser.|
|Teams-kanaler (standard og delte) |Den postkasse, der er knyttet til det overordnede team.|
|Private Teams-kanaler |Postkassen for medlemmer af den private kanal.|

> [!NOTE]
> I trin 4 skal du også identificere og fjerne alle ventepositioner og opbevaringspolitikker, der er tildelt postkassen, og som indeholder den type chatmeddelelser, du vil slette.

### <a name="tips-for-searching-for-chat-messages"></a>Tip til søgning efter chatbeskeder

For at sikre den mest omfattende samling af Teams-chatsamtaler (herunder 1:1 og gruppechats og chats fra standard-, delte og private chats) skal du bruge betingelsen **Type** og vælge indstillingen **Chatbeskeder** , når du opretter søgeforespørgslen til kladdesamlingen. Vi anbefaler også, at du inkluderer et datointerval eller flere nøgleord for at begrænse omfanget af samlingen til elementer, der er relevante for din søgning, som en undersøgelse af sletning.

Her er et skærmbillede af et eksempel på en forespørgsel, der bruger **Type** og **Dato**-indstillingerne:

   ![Forespørgsel til indsamling af Teams-indhold.](..\media\TeamsConditionsQueryType.png)

Du kan finde flere oplysninger under [Opret søgeforespørgsler for datasæt](building-search-queries.md).

## <a name="step-3-review-and-verify-chat-messages-to-purge"></a>Trin 3: Gennemse og bekræft chatmeddelelser for at fjerne

Som tidligere nævnt sletter tømningsprocessen i trin 5 de elementer, der returneres af samlingen. Det er derfor vigtigt, at du gennemser resultaterne af kladdesamlingen for at sikre, at samlingen kun returnerer de elementer, du vil fjerne. Hvis du vil gennemse et eksempel på elementer i en kladdesamling, skal du se afsnittet "Næste trin, når en kladdesamling er fuldført" i [Opret en kladdesamling](create-draft-collection.md#next-steps-after-a-draft-collection-is-complete).

Derudover kan du bruge indsamlingsstatistikken (især statistik for topplaceringer) til at generere en liste over de datakilder, der indeholder elementer, der returneres af samlingen. Brug denne liste i næste trin til at fjerne politikker for bevarelse og opbevaring fra de datakilder, der indeholder søgeresultater. Du kan få flere oplysninger under [Samlingsstatistik og -rapporter](collection-statistics-reports.md).

## <a name="step-4-remove-holds-and-retention-policies-from-data-sources"></a>Trin 4: Fjern politikker for bevarelse og opbevaring fra datakilder

Før du kan fjerne chatbeskeder fra en postkasse, skal du fjerne alle ventepositions- eller opbevaringspolitik, der er tildelt til en destinationspostkasse. Hvis ikke, bevares den chat, du forsøger at slette.

Brug listen over postkasser, der indeholder de chatmeddelelser, du vil slette, og find ud af, om der er tildelt en ventepositions- eller opbevaringspolitik til disse postkasser, og fjern derefter politikken for bevarelse eller bevarelse. Sørg for at identificere den ventepositions- eller opbevaringspolitik, du fjerner, så du kan tildele postkasserne igen i trin 7.

Du kan finde instruktioner om, hvordan du identificerer og fjerner ventepositioner og opbevaringspolitikker, under "Trin 3: Fjern alle ventepositioner fra postkassen" i [Slet elementer i mappen Genoprettelige elementer i skybaserede postkasser i venteposition](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox).

## <a name="step-5-purge-chat-messages-from-teams"></a>Trin 5: Fjern chatbeskeder fra Teams

Nu er du klar til rent faktisk at fjerne chatbeskeder fra Teams. Du skal bruge Microsoft Graph Explorer til at udføre følgende tre opgaver:

1. Hent id'et for den eDiscovery(Premium)-sag, du oprettede i trin 1. Dette er tilfældet, der indeholder den samling, der blev oprettet i trin 2.

2. Hent id'et for den samling, du oprettede i trin 2, og kontrollér søgeresultaterne i trin 3. Søgeforespørgslen i denne samling returnerer de chatbeskeder, der fjernes.

3. Fjern de chatmeddelelser, der returneres af samlingen.

Du kan få oplysninger om brug af Graph Explorer under [Brug Graph Explorer til at prøve Microsoft Graph API'er](/graph/graph-explorer/graph-explorer-overview).

> [!IMPORTANT]
> API'er under /beta-versionen i Microsoft Graph kan ændres. Brug af disse API'er i produktionsprogrammer understøttes ikke. Hvis du vil finde ud af, om en API er tilgængelig i v1.0, skal du bruge vælgeren Version.

> [!IMPORTANT]
> Hvis du vil udføre disse tre opgaver i Graph Explorer, skal du muligvis give samtykke til tilladelserne eDiscovery.Read.All og eDiscovery.ReadWrite.All. Du kan få flere oplysninger i afsnittet "Samtykke til tilladelser" i [Arbejde med Graph Explorer](/graph/graph-explorer/graph-explorer-features#consent-to-permissions).

### <a name="get-the-case-id"></a>Hent sags-id'et

1. Gå til <https://developer.microsoft.com/graph/graph-explorer> , og log på Graph Explorer med en konto, der har fået tildelt rollen **Søg og fjern** i Microsoft Purview-compliance-portal.

2. Kør følgende GET-anmodning for at hente id'et for eDiscovery-sagen (Premium). Brug værdien `https://graph.microsoft.com/beta/compliance/ediscovery/cases` i adresselinjen i anmodningsforespørgslen. Sørg for at vælge **v1.0** på rullelisten API-version.

   ![GET-anmodning om sag-id.](..\media\GraphGetRequestForCaseId.png)

   Denne anmodning returnerer oplysninger om alle sager i din organisation under fanen **Svareksempel** .

3. Rul gennem svaret for at finde eDiscovery-sagen (Premium). Brug egenskaben **displayName** til at identificere sagen.

   ![Svar med sag-id.](..\media\GraphResponseForCaseId.png)

4. Kopiér det tilsvarende id (eller kopiér og indsæt det i en tekstfil). Du skal bruge dette id i den næste opgave til at hente samlings-id'et.

> [!TIP]
> I stedet for at bruge den forrige procedure til at hente sags-id'et kan du åbne sagen i Microsoft Purview-compliance-portal og kopiere sags-id'et fra URL-adressen.

### <a name="get-the-collection-id"></a>Hent samlings-id'et

1. I Graph Explorer skal du køre følgende GET-anmodning for at hente id'et for den samling, du oprettede i trin 2, og den indeholder de elementer, du vil fjerne. Brug værdien `https://graph.microsoft.com/beta/compliance/ediscovery/cases('caseId')/sourceCollections` på adresselinjen i anmodningsforespørgslen, hvor CaseId er det id, du fik i den forrige procedure. Sørg for at omgive små og mellemstore bogstaver med parenteser og enkelte anførselstegn.

   ![GET-anmodning om samlings-id.](..\media\GraphGetRequestForCollectionId.png)

   Denne anmodning returnerer oplysninger om alle samlinger i sagen under fanen **Svareksempel** .

2. Rul gennem svaret for at finde den samling, der indeholder de elementer, du vil fjerne. Brug egenskaben **displayName** til at identificere den samling, du oprettede i trin 3.

   ![Svar med samlings-id.](..\media\GraphResponseForCollectionId.png)

   I svaret vises søgeforespørgslen fra samlingen i egenskaben **contentQuery** . Elementer, der returneres af denne forespørgsel, fjernes i den næste opgave.

3. Kopiér det tilsvarende id (eller kopiér og indsæt det i en tekstfil). Du skal bruge dette id i den næste opgave til at fjerne chatmeddelelserne.

### <a name="purge-the-chat-messages"></a>Fjern chatbeskederne

1. I Graph Explorer skal du køre følgende POST-anmodning for at fjerne de elementer, der returneres af den samling, du oprettede i trin 2. Brug værdien `https://graph.microsoft.com/beta/compliance/ediscovery/cases('caseId')/sourceCollections('collectionId')/purgeData` på adresselinjen i anmodningsforespørgslen, hvor caseId og collectionId er de id'er, du fik i de forrige procedurer. Sørg for at omgive id-værdierne med parenteser og enkelte anførselstegn.

      ![POST-anmodning om at slette elementer, der returneres af samlingen.](..\media\GraphPOSTRequestToPurgeItems.png)

   Hvis POST-anmodningen lykkes, vises der en HTTP-svarkode på et grønt banner, der angiver, at anmodningen blev accepteret.

   ![Svar på anmodningen om sletning.](..\media\GraphResponseForPurge.png)

  Du kan få flere oplysninger om purgeData under [sourceCollection: purgeData](/graph/api/ediscovery-sourcecollection-purgedata).

## <a name="step-6-verify-chat-messages-are-purged"></a>Trin 6: Kontrollér, at chatmeddelelser er fjernet

Når du har kørt POST-anmodningen om at fjerne chatmeddelelser, fjernes disse meddelelser fra Teams-klienten og erstattes af en automatisk oprettet meddelelse om, at en administrator har fjernet meddelelsen. Du kan se et eksempel på denne meddelelse i afsnittet [Slutbrugeroplevelse](#end-user-experience) i denne artikel.

Fjernede chatbeskeder flyttes til mappen SubstrateHolds, som er en skjult postkassemappe. Fjernede chatbeskeder gemmes der i mindst 1 dag og slettes derefter permanent, næste gang timerjobbet kører (typisk mellem 1-7 dage). Du kan finde flere oplysninger under [Få mere at vide om opbevaring til Microsoft Teams](retention-policies-teams.md).

## <a name="step-7-reapply-holds-and-retention-policies-to-data-sources"></a>Trin 7: Anvend politikker for bevarelse og opbevaring på datakilder igen

Når du har bekræftet, at chatmeddelelser er fjernet fra Teams-klienten, kan du anvende de bevarelses- og opbevaringspolitikker, du fjernede i trin 4, igen.

<!--
## Deleting chat messages in federated environments

Admins can use the procedures in this article to search and delete Teams chat messages in federated environments. However, you must adhere to the following guidelines. These guidelines are based on the organizational ownership of the conversation thread that contains the messages you want to delete. An organization is the owner of a conversation thread that is started by a user in that organization. In other words, when a user starts a chat, the user's organization becomes the owner of the conversation thread.

- Admins can delete the compliance copy in conversation threads owned by their organization. That means compliance copies are purged when the admin who purges the chat messages in Step 5 is in the same organization as the user who initiated the conversation thread that contains the purged messages. If a conversation thread has users in two organizations, compliance copies for the other organization will be retained.

- If a conversation thread has users in two organizations, purged chat messages are removed from the Teams client in both organizations.

- The only way to purge chat messages from user mailboxes in your organization for chat messages in conversation threads owned by another organization is to use retention policies for Teams. For more information, see [Learn about retention for Microsoft Teams](retention-policies-teams.md).
-->

## <a name="end-user-experience"></a>Slutbrugeroplevelse

I forbindelse med slettede chatbeskeder får brugerne vist en automatisk genereret meddelelse med teksten "Denne meddelelse blev slettet af en administrator".

![Visning af den slettede chatmeddelelse i Teams-klienten.](..\media\TeamsPurgeTombstone.png)

Meddelelsen på det forrige skærmbillede erstatter den chatmeddelelse, der blev slettet.

> [!NOTE]
> Hvis du er slutbruger, og en chatmeddelelse er blevet slettet, skal du kontakte din administrator for at få flere oplysninger.
