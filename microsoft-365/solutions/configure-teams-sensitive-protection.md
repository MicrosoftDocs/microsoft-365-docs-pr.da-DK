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
description: Få mere at vide om, hvordan du installerer teams med beskyttelse af følsomme data.
ms.openlocfilehash: 51e4c3b13d1a54e4edcfd9926ae246dde7d7e3e4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712693"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>Konfigurer teams med beskyttelse af følsomme data

I denne artikel kigger vi på at konfigurere et team til et følsomt beskyttelsesniveau. Sørg for, at du har gennemført trinnene i [Installér teams med beskyttelse af grundlinje](configure-teams-baseline-protection.md) , før du følger trinnene i denne artikel. Det følsomme niveau giver følgende yderligere beskyttelse i forhold til grundlinjeniveauet:

- Et følsomhedsmærkat til teamet, som giver dig mulighed for at slå gæstedeling til eller fra og begrænse SharePoint adgang til indhold til web-only for enheder, der ikke er administrerede. Denne etiket kan også bruges til at klassificere filer.
- En mere restriktiv standarddelingslinktype
- Kun teamejere kan oprette private kanaler.

## <a name="video-demonstration"></a>Videodemonstration

Se denne video for at få en gennemgang af de procedurer, der er beskrevet i denne artikel.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NMS6]

## <a name="guest-sharing"></a>Gæstedeling

Afhængigt af din virksomheds art vil du måske eller måske ikke aktivere gæstedeling for teams, der indeholder følsomme data. Hvis du planlægger at samarbejde med personer uden for organisationen i teamet, anbefaler vi, at du aktiverer gæstedeling. Microsoft 365 indeholder en række funktioner til sikkerhed og overholdelse af regler og standarder, som hjælper dig med at dele følsomt indhold sikkert. Dette er generelt en mere sikker mulighed end at sende indhold direkte til personer uden for organisationen.

Hvis du vil have mere at vide om sikker deling med gæster, skal du se følgende ressourcer:

- [Begræns utilsigtet eksponering af filer ved deling med personer uden for organisationen](./share-limit-accidental-exposure.md)
- [Opret et sikkert miljø for gæstedeling](./create-secure-guest-sharing-environment.md)

For at tillade eller blokere gæstedeling bruger vi en kombination af et følsomhedsmærkat til teamets og delingskontrolelementerne på webstedsniveau for det tilknyttede SharePoint-websted, begge diskuteret senere.

## <a name="sensitivity-labels"></a>Følsomhedsmærkater

For det følsomme beskyttelsesniveau bruger vi et følsomhedsmærkat til at klassificere teamet. Denne etiket kan også bruges til at klassificere individuelle filer i dette eller andre teams eller på andre filplaceringer, f.eks SharePoint eller OneDrive. 

Som det første trin skal du aktivere følsomhedsmærkater for Teams. Se [Brug følsomhedsetiketter til at beskytte indhold i Microsoft Teams, Office 365 grupper og SharePoint, hvis](../compliance/sensitivity-labels-teams-groups-sites.md) du vil have mere at vide.

Hvis du allerede har implementeret følsomhedsmærkater i din organisation, kan du overveje, hvordan denne etiket passer til din overordnede etiketstrategi. Du kan ændre navnet eller indstillingerne, hvis det er nødvendigt, for at imødekomme organisationens behov.

Når du har aktiveret følsomhedsetiketter til Teams, er næste trin at oprette etiketten.

Sådan opretter du en følsomhedsmærkat
1. Åbn [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com).
2. Klik **på Beskyttelse** af oplysninger **under Løsninger**.
3. Klik **på Opret en etiket**.
4. Giv etiketten et navn. Vi anbefaler **Følsom**, men du kan vælge et andet navn, hvis det pågældende navn allerede er i brug.
5. Tilføj et vist navn og en beskrivelse, og klik derefter på **Næste**.
6. På siden **Definer omfanget for denne etiket skal** du vælge **Filer & mails og** **grupper på & og** klikke på **Næste**.
7. Klik på **Næste på siden Vælg beskyttelsesindstillinger for** filer og **mails**.
8. Klik *på Næste på siden Automatisk mærkatering for filer* og mails *****.
9. På siden **Definer beskyttelsesindstillinger for** grupper og websteder skal du  vælge Indstillinger for beskyttelse af personlige oplysninger og eksterne brugeres adgang og Enhedsadgang og indstillinger for ekstern **deling** og klikke på **Næste**.
10. Vælg indstillingen **Privat under Beskyttelse af personlige oplysninger** på siden **Definer** beskyttelse af personlige oplysninger og **indstillinger for ekstern** brugeradgang.
11. Hvis du vil tillade gæsteadgang **, skal** du under Ekstern brugeradgang vælge Lad Microsoft 365 gruppeejere føje personer uden for din organisation **til gruppen som gæster**.
12. Klik på **Næste**.
13. På siden **Definer indstillinger for ekstern deling og adgang til** enheder skal du **vælge Kontrolelement for ekstern deling SharePoint websteder**.
14. Under **Indhold kan deles med skal du** **vælge Ny** og eksisterende gæster, hvis du tillader gæsteadgang eller Kun **personer i din organisation, hvis** ikke.
15. Under **Adgang fra ikke-administrerede enheder skal** du **vælge Tillad begrænset adgang, der kun er tilgængelig via internettet**.
16. Klik på **Næste**.
17. Klik på **Næste på siden Automatisk mærkat for** databasekolonner.
18. Klik **på Opret etiket**, og klik derefter på **Udført**.

Når du har oprettet etiketten, skal du publicere den til de brugere, der skal bruge den. Af hensyn til følsom beskyttelse gør vi navnet tilgængeligt for alle brugere. Du publicerer navnet i Microsoft 365 Overholdelsescenter på fanen **Etiketpolitikker** på siden **Beskyttelse af** oplysninger. Hvis du har en eksisterende politik, der gælder for alle brugere, skal du føje denne etiket til den pågældende politik. Hvis du har brug for at oprette en ny politik, kan du se [Publicer følsomhedsmærkater ved at oprette en etiketpolitik](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Opret et team

Der foretages yderligere konfiguration af det følsomme scenarie på SharePoint, der er knyttet til teamet, så næste trin er at oprette et team.

Sådan opretter du et team til følsomme oplysninger
1. I Teams skal **du Teams** team i venstre side af appen og derefter klikke på Deltag i eller opret et **team** nederst på teamlisten.
2. Klik **på Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. På listen **Følsomhed** skal du vælge den følsomme **etiket** , du lige har oprettet.
5. Klik **på Privat** under **Beskyttelse af personlige oplysninger**.
6. Skriv et navn til teamet, og klik derefter på **Opret**.
7. Føj brugere til teamet, og klik derefter på **Luk**.

## <a name="private-channel-settings"></a>Indstillinger for privat kanal

På dette niveau begrænser vi oprettelse af private kanaler til teamejere.

Sådan begrænser du oprettelse af private kanaler
1. I teamet skal du klikke **på Flere indstillinger** og derefter klikke på **Administrer team**.
2. På fanen **Indstillinger** skal du **udvide Medlemstilladelser**.
3. Fjern markeringen **i afkrydsningsfeltet Tillad medlemmer at oprette private** kanaler.

Du kan også bruge [teams-politikker til](/MicrosoftTeams/teams-policies) at styre, hvem der kan oprette private kanaler.

## <a name="shared-channel-settings"></a>Indstillinger for delt kanal

[Delte kanaler](/MicrosoftTeams/shared-channels) har ikke teamniveauindstillinger. De indstillinger for delte kanaler, du konfigurerer i Teams Administration og Azure AD, gælder for alle teams uanset følsomhed.

## <a name="sharepoint-settings"></a>SharePoint indstillinger

Hver gang du opretter et nyt team med den følsomme etiket, er der to trin at udføre i SharePoint:

- Opdater indstillingerne for gæstedeling for webstedet i SharePoint Administration for at opdatere standardlinket til deling til *Bestemte personer*.
- Opdater indstillingerne for webstedsdeling på selve webstedet for at forhindre medlemmer i at dele webstedet.

### <a name="site-default-sharing-link-settings"></a>Indstillinger for standardlink til deling af websted

Sådan opdateres webstedets standardlinktype for deling

1. Åbn administration SharePoint, og vælg **Aktive websteder** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>.
1. Vælg det websted, der er knyttet til teamet.
1. Klik **på Rediger** under **Ekstern deling på** fanen **Politikker**.
1. Fjern markeringen i afkrydsningsfeltet Samme som indstilling  på organisationsniveau under Standardindstilling for delingslink, og vælg Bestemte personer **(kun de personer, som brugeren angiver)**.
1. Vælg **Gem**.

Hvis du vil scripte dette som en del af dit teams oprettelsesproces, kan du bruge [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) `-DefaultSharingLinkType Direct` med parameteren til at ændre standarddelingslinket til *Bestemte personer*.

Bemærk, at hvis du føjer private eller delte kanaler til teamet, opretter hver SharePoint websted med standardindstillingerne for deling. Du kan opdatere dem i SharePoint Administration ved at vælge de websteder, der er knyttet til teamet.

### <a name="site-sharing-settings"></a>Indstillinger for webstedsdeling

For at sikre, at SharePoint-webstedet ikke deles med personer, der ikke er medlemmer af teamet, begrænser vi deling til ejere. Dette er kun nødvendigt for det SharePoint, der blev oprettet sammen med teamet. Flere websteder, der er oprettet som en del af private eller delte kanaler, kan ikke deles uden for teamet eller kanalen.

Sådan konfigureres webstedsdeling kun for ejere
1. I Teams du gå til **fanen Generelt** for det team, du vil opdatere.
2. Klik på Filer på teamets **værktøjslinje**.
3. Klik på ellipsen, og klik derefter **på Åbn i SharePoint**.
4. Klik på ikonet for indstillinger på SharePoint webstedsværktøjslinjen, og klik derefter på **Webstedstilladelser**.
5. I **ruden Webstedstilladelser** under Deling **af websted skal du** klikke **på Rediger, hvordan medlemmer kan dele**.
6. Under **Tilladelser til deling** skal du vælge Webstedsejere og -medlemmer, og personer med redigeringstilladelser kan dele filer og mapper, men kun **webstedsejere** kan dele webstedet, og klik derefter på **Gem**.


## <a name="related-topics"></a>Relaterede emner

[Opret og konfigurer følsomhedsmærkater og deres politikker](../compliance/create-sensitivity-labels.md)
