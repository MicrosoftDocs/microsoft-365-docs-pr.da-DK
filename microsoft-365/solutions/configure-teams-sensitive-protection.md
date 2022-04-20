---
title: Konfigurer teams med beskyttelse af følsomme data
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
description: Få mere at vide om, hvordan du udruller teams med beskyttelse af følsomme data.
ms.openlocfilehash: 2ea13fbf8a677ba4a04efbd0b2a6fdfed7d80644
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941275"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>Konfigurer teams med beskyttelse af følsomme data

I denne artikel ser vi på, hvordan du opretter et team til et følsomt beskyttelsesniveau. Sørg for, at du har fuldført trinnene i [Installér teams med grundlæggende beskyttelse,](configure-teams-baseline-protection.md) før du følger trinnene i denne artikel. Det følsomme niveau giver følgende yderligere beskyttelse over det oprindelige niveau:

- En følsomhedsmærkat for teamet, der giver dig mulighed for at slå gæstedeling til eller fra og begrænser adgangen til SharePoint indhold kun til internettet for ikke-administrerede enheder. Denne mærkat kan også bruges til at klassificere filer.
- En mere restriktiv standardlinktype for deling
- Det er kun teamejere, der kan oprette private kanaler.

## <a name="video-demonstration"></a>Videodemonstration

Se denne video for at få en gennemgang af de procedurer, der er beskrevet i denne artikel.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NMS6]

## <a name="guest-sharing"></a>Gæstedeling

Afhængigt af din virksomheds karakter vil du måske aktivere gæstedeling for teams, der indeholder følsomme data. Hvis du planlægger at samarbejde med personer uden for din organisation i teamet, anbefaler vi, at du aktiverer gæstedeling. Microsoft 365 indeholder en række funktioner til sikkerhed og overholdelse af angivne standarder, der kan hjælpe dig med at dele følsomt indhold på en sikker måde. Dette er generelt en mere sikker mulighed end at sende indhold direkte til personer uden for din organisation.

Du kan finde oplysninger om sikker deling med gæster i følgende ressourcer:

- [Begræns utilsigtet eksponering af filer, når der deles med personer uden for din organisation](./share-limit-accidental-exposure.md)
- [Opret et sikkert gæstedelingsmiljø](./create-secure-guest-sharing-environment.md)

Hvis du vil tillade eller blokere gæstedeling, bruger vi en kombination af en følsomhedsmærkat for teamet og kontrolelementerne til deling på webstedsniveau for det tilknyttede SharePoint websted, som begge drøftes senere.

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

Til det følsomme beskyttelsesniveau bruger vi en følsomhedsmærkat til at klassificere teamet. Denne mærkat kan også bruges til at klassificere individuelle filer i dette eller andre teams eller på andre filplaceringer, f.eks. SharePoint eller OneDrive. 

Som det første trin skal du aktivere følsomhedsmærkater for Teams. Du kan finde flere oplysninger [under Brug følsomhedsmærkater til at beskytte indhold på Microsoft Teams, Office 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

Hvis du allerede har udrullet følsomhedsmærkater i din organisation, skal du overveje, hvordan denne mærkat passer til din overordnede mærkatstrategi. Du kan ændre navnet eller indstillingerne, hvis det er nødvendigt for at opfylde organisationens behov.

Når du har aktiveret følsomhedsmærkater for Teams, er næste trin at oprette mærkaten.

Sådan opretter du en følsomhedsmærkat
1. Åbn [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com).
2. Klik på **Information Protection** under **Løsninger**.
3. Klik på **Opret en etiket**.
4. Giv etiketten et navn. Vi foreslår **Følsom**, men du kan vælge et andet navn, hvis det allerede er i brug.
5. Tilføj et vist navn og en beskrivelse, og klik derefter på **Næste**.
6. På **siden Definer omfanget for denne etiket** skal du vælge **Filer & mails** og **grupper & websteder** og klikke på **Næste**.
7. Klik på **Næste** på siden **Vælg beskyttelsesindstillinger for filer og mails**.
8. Klik på **Næste** på siden *Automatisk mærkning af filer og mails**.
9. På siden **Definer beskyttelsesindstillinger for grupper og websteder** skal du vælge **Beskyttelse af personlige oplysninger og indstillinger for ekstern brugeradgang** og **Indstillinger for enhedsadgang og ekstern deling** og klikke på **Næste**.
10. På siden **Definer indstillinger for beskyttelse af personlige oplysninger og ekstern brugeradgang** under **Beskyttelse af personlige oplysninger** skal du vælge indstillingen **Privat** .
11. Hvis du vil tillade gæsteadgang, skal du under **Adgang til eksterne brugere** vælge **Lad Microsoft 365 gruppeejere føje personer uden for organisationen til gruppen som gæster**.
12. Klik på **Næste**.
13. På siden **Definer indstillinger for ekstern deling og enhedsadgang** skal du vælge **Kontrollér ekstern deling fra navngivne SharePoint websteder**.
14. Under **Indhold kan deles med** skal du vælge **Nye og eksisterende gæster** , hvis du tillader gæsteadgang eller **Kun personer i din organisation** , hvis ikke.
15. Under **Adgang fra ikke-administrerede enheder** skal du vælge **Tillad begrænset, webbaseret adgang**.
16. Klik på **Næste**.
17. Klik på **Næste** på siden **Automatisk mærkning af databasekolonner**.
18. Klik på **Opret navn**, og klik derefter på **Udført**.

Når du har oprettet mærkaten, skal du publicere den til de brugere, der skal bruge den. Af hensyn til følsom beskyttelse gør vi mærkaten tilgængelig for alle brugere. Du publicerer etiketten på Microsoft Purview-overholdelsesportalen på fanen **Mærkatpolitikker** på siden **Information Protection** . Hvis du har en eksisterende politik, der gælder for alle brugere, skal du føje dette navn til politikken. Hvis du har brug for at oprette en ny politik, skal du se [Publicer følsomhedsmærkater ved at oprette en mærkatpolitik](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Opret et team

Yderligere konfiguration af det følsomme scenarie udføres på det SharePoint websted, der er knyttet til teamet, så næste trin er at oprette et team.

Sådan opretter du et team til følsomme oplysninger
1. I Teams skal du klikke på **Teams** i venstre side af appen og derefter klikke på **Deltag eller opret et team** nederst på listen over teams.
2. Klik på **Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. Vælg den **følsomme** mærkat, du lige har oprettet, på listen **Følsomhed**.
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

[Delte kanaler](/MicrosoftTeams/shared-channels) har ikke indstillinger på teamniveau. De delte kanalindstillinger, du konfigurerer i Teams Administration og Azure AD, gælder for alle teams, uanset følsomhed.

## <a name="sharepoint-settings"></a>indstillinger for SharePoint

Hver gang du opretter et nyt team med det følsomme mærkat, skal du udføre to trin i SharePoint:

- Opdater indstillingerne for gæstedeling for webstedet i SharePoint Administration for at opdatere standardlinket til deling for *bestemte personer*.
- Opdater indstillingerne for webstedsdeling på selve webstedet for at forhindre medlemmer i at dele webstedet.

### <a name="site-default-sharing-link-settings"></a>Indstillinger for links til deling, der er standard for webstedet

Sådan opdaterer du linktypen for standarddeling for webstedet

1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> under **Websteder**.
1. Vælg det websted, der er knyttet til teamet.
1. Klik på **Rediger** under **Ekstern deling** under fanen **Politikker**.
1. Under Standardlinktype for deling skal du fjerne markeringen i afkrydsningsfeltet **Samme som indstilling på organisationsniveau** og vælge **Specifikke personer (kun de personer, som brugeren angiver).**
1. Vælg **Gem**.

Hvis du vil scripte dette som en del af teamoprettelsesprocessen, kan du bruge [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) med `-DefaultSharingLinkType Direct` parameteren til at ændre standardlinket til deling til *Bestemte personer*.

Bemærk, at hvis du føjer private eller delte kanaler til teamet, oprettes der hver især et nyt SharePoint websted med standardindstillingerne for deling. Du kan opdatere dem i SharePoint Administration ved at vælge de websteder, der er knyttet til teamet.

### <a name="site-sharing-settings"></a>Indstillinger for webstedsdeling

For at hjælpe med at sikre, at det SharePoint websted ikke deles med personer, der ikke er medlemmer af teamet, begrænser vi delingen til ejere. Dette er kun nødvendigt for det SharePoint websted, der blev oprettet med teamet. Yderligere websteder, der er oprettet som en del af private eller delte kanaler, kan ikke deles uden for teamet eller kanalen.

Sådan konfigurerer du webstedsdeling, der kun er for ejere
1. I Teams skal du gå til fanen **Generelt** for det team, du vil opdatere.
2. Klik på **Filer** på værktøjslinjen for teamet.
3. Klik på ellipsen, og klik derefter på **Åbn i SharePoint**.
4. Klik på ikonet Indstillinger på værktøjslinjen på det underliggende SharePoint websted, og klik derefter på **Webstedstilladelser**.
5. Klik på **Rediger, hvordan medlemmer kan dele** under **Webstedsdeling** i ruden **Webstedstilladelser**.
6. Under **Delingstilladelser** skal du vælge **Webstedsejere og -medlemmer, og personer med redigeringstilladelser kan dele filer og mapper, men det er kun webstedsejere, der kan dele webstedet**, og klik derefter på **Gem**.


## <a name="related-topics"></a>Relaterede emner

[Opret og konfigurer følsomhedsmærkater og deres politikker](../compliance/create-sensitivity-labels.md)
