---
title: Konfigurer teams med beskyttelse af meget følsomme data
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkSPO
recommendations: false
description: Få mere at vide om, hvordan du udruller teams med beskyttelse af meget følsomme data.
ms.openlocfilehash: b104828f5437b9389e83379984a40edf33340f33
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947555"
---
# <a name="configure-teams-with-protection-for-highly-sensitive-data"></a>Konfigurer teams med beskyttelse af meget følsomme data

I denne artikel ser vi på, hvordan du opretter et team til et meget følsomt beskyttelsesniveau. Sørg for, at du har fuldført trinnene i [Installér teams med grundlæggende beskyttelse,](configure-teams-baseline-protection.md) før du følger trinnene i denne artikel.

Til dette beskyttelsesniveau opretter vi en følsomhedsmærkat, der kan bruges på tværs af organisationen til meget følsomme teams og filer. Det er kun medlemmer af din organisation og gæster, som du har angivet, der kan dekryptere filer, der bruger dette navn. Hvis du har brug for yderligere isolering af tilladelser, så det kun er medlemmer af et bestemt team, der kan dekryptere filer, skal du se  [Udrul et team med sikkerhedsisolering](secure-teams-security-isolation.md).

Det yderst følsomme niveau giver følgende yderligere beskyttelse over det oprindelige niveau:

- En følsomhedsmærkat for teamet, der giver dig mulighed for at slå gæstedeling til eller fra og blokerer adgang til SharePoint indhold for ikke-administrerede enheder. Denne mærkat kan også bruges til at klassificere og kryptere filer.
- En mere restriktiv standardlinktype for deling
- Det er kun teamejere, der kan oprette private kanaler.
- Adgangsanmodninger for det tilknyttede SharePoint websted er deaktiveret.

## <a name="video-demonstration"></a>Videodemonstration

Se denne video for at få en gennemgang af de procedurer, der er beskrevet i denne artikel.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzI7]

## <a name="guest-sharing"></a>Gæstedeling

Afhængigt af din virksomheds karakter vil du måske aktivere gæstedeling for teams, der indeholder meget følsomme data. Hvis du planlægger at samarbejde med personer uden for din organisation i teamet, anbefaler vi, at du aktiverer gæstedeling. Microsoft 365 indeholder en række funktioner til sikkerhed og overholdelse af angivne standarder, der kan hjælpe dig med at dele følsomt indhold på en sikker måde. Dette er generelt en mere sikker mulighed end at sende indhold direkte til personer uden for din organisation.

Du kan finde oplysninger om sikker deling med gæster i følgende ressourcer:

- [Begræns utilsigtet eksponering af filer, når der deles med personer uden for din organisation](./share-limit-accidental-exposure.md)
- [Opret et sikkert gæstedelingsmiljø](./create-secure-guest-sharing-environment.md)

Hvis du vil tillade eller blokere gæstedeling, bruger vi en kombination af en følsomhedsmærkat for teamet og kontrolelementerne til deling på webstedsniveau for det tilknyttede SharePoint websted, som begge drøftes senere.

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

Til det yderst følsomme beskyttelsesniveau bruger vi en følsomhedsmærkat til at klassificere teamet. Denne mærkat kan også bruges til at klassificere og kryptere individuelle filer i dette eller andre teams eller på andre filplaceringer, f.eks. SharePoint eller OneDrive. 

Som det første trin skal du aktivere følsomhedsmærkater for Teams. Du kan finde flere oplysninger [under Brug følsomhedsmærkater til at beskytte indhold på Microsoft Teams, Office 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

Hvis du allerede har udrullet følsomhedsmærkater i din organisation, skal du overveje, hvordan denne mærkat passer til din overordnede mærkatstrategi. Du kan ændre navnet eller indstillingerne, hvis det er nødvendigt for at opfylde organisationens behov.

Når du har aktiveret følsomhedsmærkater for Teams, er næste trin at oprette mærkaten.

Sådan opretter du en følsomhedsmærkat
1. Åbn [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com).
2. Klik på **Information Protection** under **Løsninger**.
3. Klik på **Opret en etiket**.
4. Giv etiketten et navn. Vi foreslår **Meget følsom**, men du kan vælge et andet navn, hvis det ene allerede er i brug.
5. Tilføj et vist navn og en beskrivelse, og klik derefter på **Næste**.
6. På **siden Definer omfanget for denne etiket** skal du vælge **Filer & mails** og **grupper & websteder** og klikke på **Næste**.
7. På siden **Vælg beskyttelsesindstillinger for filer og mails** skal du vælge **Kryptér filer og mails**, og klik derefter på **Næste**.
8. På siden **Kryptering** skal du vælge **Konfigurer krypteringsindstillinger**.
9. Klik på **Tildel tilladelser** under **Tildel tilladelser til bestemte brugere og grupper**.
10. Klik på **Tilføj alle brugere og grupper i din organisation**.
11. Hvis der er gæster, der skal have tilladelse til at dekryptere filer, skal du klikke på **Tilføj brugere eller grupper** og tilføje dem.
12.  Klik på **Gem**, og klik derefter på **Næste**.
13. Klik på **Næste** på siden *Automatisk mærkning af filer og mails**.
14. På siden **Definer beskyttelsesindstillinger for grupper og websteder** skal du vælge **Beskyttelse af personlige oplysninger og indstillinger for ekstern brugeradgang** og **Indstillinger for enhedsadgang og ekstern deling** og klikke på **Næste**.
15. På siden **Definer indstillinger for beskyttelse af personlige oplysninger og ekstern brugeradgang** under **Beskyttelse af personlige oplysninger** skal du vælge indstillingen **Privat** .
16. Hvis du vil tillade gæsteadgang, skal du under **Adgang til eksterne brugere** vælge **Lad Microsoft 365 gruppeejere føje personer uden for organisationen til gruppen som gæster**.
17. Klik på **Næste**.
18. På siden **Definer indstillinger for ekstern deling og enhedsadgang** skal du vælge **Kontrollér ekstern deling fra navngivne SharePoint websteder**.
19. Under **Indhold kan deles med** skal du vælge **Nye og eksisterende gæster** , hvis du tillader gæsteadgang eller **Kun personer i din organisation** , hvis ikke.
20. Under **Adgang fra ikke-administrerede enheder** skal du vælge **Bloker adgang**. (Hvis du tillader gæster, og de ikke har administrerede enheder, kan du vælge **Tillad begrænset, kun webadgang**).
21. Klik på **Næste**.
22. Klik på **Næste** på siden **Automatisk mærkning af databasekolonner**.
23. Klik på **Opret navn**, og klik derefter på **Udført**.

Når du har oprettet mærkaten, skal du publicere den til de brugere, der skal bruge den. Af hensyn til følsom beskyttelse gør vi mærkaten tilgængelig for alle brugere. Du publicerer etiketten på Microsoft Purview-overholdelsesportalen på fanen **Mærkatpolitikker** på siden **Information Protection** . Hvis du har en eksisterende politik, der gælder for alle brugere, skal du føje dette navn til politikken. Hvis du har brug for at oprette en ny politik, skal du se [Publicer følsomhedsmærkater ved at oprette en mærkatpolitik](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Opret et team

Yderligere konfiguration af det yderst følsomme scenarie udføres på det SharePoint websted, der er knyttet til teamet, så næste trin er at oprette et team.

Sådan opretter du et team til meget følsomme oplysninger
1. I Teams skal du klikke på **Teams** i venstre side af appen og derefter klikke på **Deltag eller opret et team** nederst på listen over teams.
2. Klik på **Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. På listen **Følsomhed** skal du vælge mærkaten **Meget følsom** , som du lige har oprettet.
5. Klik på **Privat** under **Beskyttelse af personlige oplysninger**.
6. Skriv et navn til teamet, og klik derefter på **Opret**.
7. Føj brugere til teamet, og klik derefter på **Luk**.

## <a name="private-channel-settings"></a>Indstillinger for privat kanal

På dette niveau begrænser vi oprettelse af private kanaler til teamejere.

Sådan begrænser du oprettelse af private kanaler
1. Klik på **Flere indstillinger** i teamet, og klik derefter på **Administrer team**.
2. Udvid **Medlemstilladelser** under fanen **Indstillinger**.
3. Fjern markeringen i afkrydsningsfeltet **Tillad, at medlemmer opretter private kanaler** .

Du kan også bruge [teams-politikker](/MicrosoftTeams/teams-policies) til at styre, hvem der kan oprette private kanaler.

## <a name="shared-channel-settings"></a>Indstillinger for delt kanal

[Delte kanaler](/MicrosoftTeams/shared-channels) har ikke indstillinger på teamniveau. De delte kanalindstillinger, du konfigurerer i Teams Administration og Azure AD, vil være tilgængelige for alle teams, uanset følsomhed.

## <a name="sharepoint-settings"></a>indstillinger for SharePoint

Hver gang du opretter et nyt team med den meget følsomme mærkat, er der to trin at udføre i SharePoint:

- Opdater indstillingerne for gæstedeling for webstedet i SharePoint Administration for at opdatere standardlinket til deling *med personer med eksisterende adgang*.
- Opdater indstillingerne for webstedsdeling på selve webstedet for at forhindre medlemmer i at dele filer, mapper eller webstedet og deaktivere adgangsanmodninger.

### <a name="site-default-sharing-link-settings"></a>Indstillinger for links til deling, der er standard for webstedet

Sådan opdaterer du linktypen for standarddeling for webstedet

1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> under **Websteder**.
1. Vælg det websted, der er knyttet til teamet.
1. Under fanen **Politikker** under **Ekstern deling** skal du vælge **Rediger**.
1. Under Standardlinktype for deling skal du fjerne markeringen i afkrydsningsfeltet **Samme som indstilling på organisationsniveau** og vælge **Personer med eksisterende adgang**.
1. Vælg **Gem**.

Bemærk, at hvis du føjer private eller delte kanaler til teamet, oprettes der hver især et nyt SharePoint websted med standardindstillingerne for deling. Du kan opdatere dem i SharePoint Administration ved at vælge de websteder, der er knyttet til teamet.

### <a name="site-sharing-settings"></a>Indstillinger for webstedsdeling

For at hjælpe med at sikre, at det SharePoint websted ikke deles med personer, der ikke er medlemmer af teamet, begrænser vi delingen til ejere. Vi begrænser også deling af filer og mapper til teamejere. Dette hjælper med at sikre, at ejerne er opmærksomme på, når en fil deles med en person uden for teamet.

Sådan konfigurerer du webstedsdeling, der kun er for ejere
1. I Teams skal du gå til fanen **Generelt** for det team, du vil opdatere.
2. Klik på **Filer** på værktøjslinjen for teamet.
3. Klik på ellipsen, og klik derefter på **Åbn i SharePoint**.
4. Klik på ikonet Indstillinger på værktøjslinjen på det underliggende SharePoint websted, og klik derefter på **Webstedstilladelser**.
5. Klik på **Rediger, hvordan medlemmer kan dele** under **Webstedsdeling** i ruden **Webstedstilladelser**.
6. Under **Delingstilladelser** skal du vælge **Kun webstedsejere kan dele filer, mapper og webstedet**.
7. Angiv **Tillad adgangsanmodninger** til **Fra**, og klik derefter på **Gem**.

## <a name="see-also"></a>Se også

[Opret og konfigurer følsomhedsmærkater og deres politikker](../compliance/create-sensitivity-labels.md)
