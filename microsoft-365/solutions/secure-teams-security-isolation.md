---
title: Konfigurere et team med sikkerhedsisolation
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
recommendations: false
description: Få mere at vide om, hvordan du opretter et team med en unik følsomhedsmærkat for sikkerhed.
ms.openlocfilehash: 2ca2e6320ddd119c4dcb20db2f816c9e9a4453ae
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588219"
---
# <a name="configure-a-team-with-security-isolation"></a>Konfigurere et team med sikkerhedsisolation

Denne artikel giver dig anbefalinger og trin til at konfigurere et privat team i Microsoft Teams og bruge en entydig følsomhedsmærkat til at kryptere filer, så kun teammedlemmer kan dekryptere dem.

Ud over den private adgang beskriver denne artikel, hvordan du konfigurerer det tilknyttede SharePoint-websted, som du kan få adgang til  fra sektionen Filer i en teamkanal, for den ekstra sikkerhed, der er nødvendig for at lagre stærkt regulerede data.

Elementerne i konfigurationen for et team med sikkerhedsisolation er:

- Et privat team
- Ekstra sikkerhed på det tilknyttede SharePoint for teamet, som:
  - Forhindrer medlemmer af webstedet i at dele webstedet med andre.
  - Forhindrer ikke-medlemmer af webstedet i at anmode om adgang til webstedet.
- Et følsomhedsmærkat, der specifikt er beregnet til dette team, som:
    - Forhindrer adgang til SharePoint fra enheder, der ikke er administrerede
    - Tillader eller afviser gæsteadgang til teamet afhængigt af dine krav
    - Krypterer dokumenter, som etiketten er anvendt på

> [!IMPORTANT]
> Sørg for, at du har aktiveret følsomhedsetiketter til at beskytte indhold [i Microsoft Teams, Office 365-grupper og SharePoint-websteder,](../compliance/sensitivity-labels-teams-groups-sites.md) før du fortsætter med trinnene i denne artikel.

Se denne video for at få et overblik over installationsprocessen.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a>Du kan finde en oversigt på én side over dette scenarie på Microsoft Teams [med sikkerhedsisolationsplakat](../downloads/team-security-isolation-poster.pdf).

[![Microsoft Teams med sikkerhedsisolationsplakat.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Du kan også downloade denne plakat i [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf)- [eller PowerPoint-format](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) og udskrive den på papir i Letter-, Legal- eller Tabloid-størrelse (11 x 17).

Prøv denne konfiguration i dit eget testlaboratoriemiljø med [disse instruktioner](team-security-isolation-dev-test.md).

Se, hvordan Contoso Corporation brugte et isoleret team til et tohemmeligt projekt [i dette casestudie](contoso-team-for-top-secret-project.md).

## <a name="initial-protections"></a>Indledende beskyttelse

Gennemgå følgende bedste fremgangsmåder for at beskytte adgangen SharePoint teamet og dets underliggende websted:
- [Politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md)
- [SharePoint politikker for onlineadgang](../security/office-365-security/sharepoint-file-access-policies.md)
- [Udrul teams med beskyttelse mod grundlinjer](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Gæstedeling

Afhængigt af din virksomheds art vil du måske eller måske ikke aktivere gæstedeling for dette team. Hvis du planlægger at samarbejde med personer uden for organisationen i teamet, skal du aktivere gæstedeling. 

Hvis du vil have mere at vide om sikker deling med gæster, skal du se følgende ressourcer:

- [Begræns utilsigtet eksponering af filer ved deling med personer uden for organisationen](./share-limit-accidental-exposure.md)
- [Opret et sikkert miljø for gæstedeling](./create-secure-guest-sharing-environment.md)

For at tillade eller blokere gæstedeling bruger vi en kombination af et følsomhedsmærkat til teamets og delingskontrolelementerne på webstedsniveau for det tilknyttede SharePoint-websted, begge diskuteret senere.

## <a name="create-a-private-team"></a>Opret et privat team

Da vi opretter et følsomhedsmærkat, der er specifikt for dette team, er næste trin at oprette teamet. Hvis du har et eksisterende team, kan du bruge det.

Sådan opretter du et team til følsomme oplysninger
1. I Teams skal **du Teams** team i venstre side af appen og derefter klikke på Deltag i eller opret et **team** nederst på teamlisten.
2. Klik **på Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. Bevar **standardindstillingen** på listen Følsomhed.
5. Klik **på Privat** under **Beskyttelse af personlige oplysninger**.
6. Skriv et navn til den gruppe, der er relateret til dit følsomme projekt. Du kan **f.eks Project Saturn**.
7. Klik **på Opret**.
8. Føj brugere til teamet, og klik derefter på **Luk**.

## <a name="private-channel-settings"></a>Indstillinger for privat kanal

Vi anbefaler, at du begrænser oprettelse af private kanaler til teamejere.

Sådan begrænser du oprettelse af private kanaler
1. I teamet skal du klikke **på Flere indstillinger** og derefter klikke på **Administrer team**.
2. På fanen **Indstillinger** skal du **udvide Medlemstilladelser**.
3. Fjern markeringen **i afkrydsningsfeltet Tillad medlemmer at oprette private** kanaler.

Du kan også bruge [teams-politikker til](/MicrosoftTeams/teams-policies) at styre, hvem der kan oprette private kanaler.

## <a name="create-a-sensitivity-label"></a>Opret et følsomhedsmærkat

For at konfigurere et team til sikkerhedsisolation bruger vi en følsomhedsmærkat, der er oprettet specifikt for dette team. Dette navn bruges på teamniveau til at styre gæstedeling og til at blokere adgang fra enheder, der ikke er administrerede. Den kan også bruges til at klassificere og kryptere individuelle filer i teamet, så kun teamejere og medlemmer kan åbne dem.

Hvis du har en intern partner eller interessentgruppe, der skal kunne få vist krypterede dokumenter, men ikke redigere dem, kan du føje dem til etiketten med skrivetilladelse. Du kan derefter føje disse personer til teamets SharePoint-websted med læsetilladelser, og de har skrivebeskyttet adgang til det websted, hvor dokumenterne opbevares, men ikke selve teamet.

Sådan opretter du en følsomhedsmærkat

1. Åbn Microsoft 365 Overholdelsescenter, og vælg **Beskyttelse** af <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**oplysninger under Løsninger**</a>.
1. Klik **på Opret en etiket**.
1. Giv etiketten et navn. Vi anbefaler, at du navngiver den efter det team, du skal bruge den sammen med.
1. Tilføj et vist navn og en beskrivelse, og klik derefter på **Næste**.
1. På siden **Definer omfanget for denne etiket skal** du vælge **Filer & mails og** **grupper på & og** klikke på **Næste**.
1. På siden **Vælg beskyttelsesindstillinger for filer og mails skal** du vælge **Kryptér filer og mails** og derefter klikke på **Næste**.
1. På siden **Kryptering** skal du vælge **Konfigurer krypteringsindstillinger**.
1. Klik **på Tilføj brugere eller grupper**, vælg det team, du har oprettet, og klik derefter på **Tilføj**
1. Klik **på Vælg tilladelser**.
1. Vælg **Samtidig redigering** på rullelisten, og klik derefter på **Gem**.
1. Hvis du vil medtage brugere eller grupper med skrivebeskyttet adgang til filer med etiketten:
    1. Klik **på Tildel tilladelser**.
    1. Klik **på Tilføj brugere eller grupper**, vælg de brugere eller grupper, du vil tilføje, og klik derefter på **Tilføj**.
    1. Klik **på Vælg tilladelser**.
    1. Vælg **Viewer** på rullelisten, og klik derefter på **Gem**.
13.  Klik **på Gem**, og klik derefter på **Næste**.
14. Klik *på Næste på siden Automatisk mærkatering for filer* og mails *****.
15. På siden **Definer beskyttelsesindstillinger for** grupper og websteder skal du  vælge Indstillinger for beskyttelse af personlige oplysninger og eksterne brugeres adgang og Enhedsadgang og indstillinger for ekstern **deling** og klikke på **Næste**.
16. Vælg indstillingen **Privat under Beskyttelse af personlige oplysninger** på siden **Definer** beskyttelse af personlige oplysninger og **indstillinger for ekstern** brugeradgang.
17. Hvis du vil tillade gæsteadgang **, skal** du under Ekstern brugeradgang vælge Lad Microsoft 365 gruppeejere føje personer uden for din organisation **til gruppen som gæster**.
18. Klik på **Næste**.
19. På siden **Definer indstillinger for ekstern deling og adgang til** enheder skal du **vælge Kontrolelement for ekstern deling SharePoint websteder**.
20. Under **Indhold kan deles med skal du** **vælge Ny** og eksisterende gæster, hvis du tillader gæsteadgang eller Kun **personer i din organisation, hvis** ikke.
21. Under **Adgang fra ikke-administrerede enheder skal** du vælge **Bloker adgang**.
22. Klik på **Næste**.
23. Klik på **Næste på siden Automatisk mærkat for** databasekolonner.
24. Klik **på Opret etiket**, og klik derefter på **Udført**.

Når du har oprettet etiketten, skal du publicere den til de brugere, der skal bruge den. I dette tilfælde gør vi kun etiketten tilgængelig for personer i teamet.

Sådan publicerer du en følsomhedsmærkat:

1. I Microsoft 365 Overholdelsescenter på siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Beskyttelse af oplysninger** skal</a> du vælge **fanen Etiketpolitikker**.
2. Klik **på Udgiv etiketter**.
3. På siden **Vælg følsomhedsmærkater til publicering** skal du klikke **på Vælg følsomhedsmærkater, der skal publicere**.
4. Vælg den etiket, du har oprettet, og klik derefter på **Tilføj**.
5. Klik på **Næste**.
6. Klik på Vælg brugere og grupper på siden **Publicer til brugere og grupper**.
7. Klik **på Tilføj**, og vælg derefter det team, du har oprettet.
8. Klik **på Tilføj**, og klik derefter på **Udført**.
9. Klik på **Næste**.
10. På siden Politikindstillinger skal du markere afkrydsningsfeltet Brugere skal angive begrundelse for at fjerne en etiket eller et lavere klassificeringsnavn og derefter klikke på **Næste**.
11. Skriv et navn til politikken, og klik derefter på **Næste**.
12. Klik **på Send** , og klik derefter på **Udført**.

## <a name="apply-the-label-to-the-team"></a>Anvend navnet på teamet

Når etiketten er blevet publiceret, skal du anvende den på teamet, før indstillingerne for gæstedeling og administrerede enheder træder i kraft. Dette gøres SharePoint Administration. Bemærk, at det kan tage lidt tid, før navnet er tilgængeligt, efter det er blevet publiceret.

For at anvende følsomhedsmærkatet

1. Åbn administration SharePoint, og vælg **Aktive websteder** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>.
1. Vælg det websted, der er knyttet til teamet.
1. På fanen **Politikker** under Følsomhed **skal** du vælge **Rediger**.
1. Vælg den etiket, du har oprettet, og vælg derefter **Gem**.

## <a name="sharepoint-settings"></a>SharePoint indstillinger

Der er tre trin at udføre i SharePoint:

- Opdater indstillingerne for gæstedeling for webstedet i SharePoint Administration, så de passer til det, du valgte, da du oprettede navnet, og opdater standardlinket til deling til Personer *med eksisterende adgang*.
- Opdater indstillingerne for webstedsdeling på selve webstedet for at forhindre medlemmer i at dele filer, mapper eller webstedet og deaktivere anmodninger om adgang.
- Hvis du har føjet personer eller grupper til navnet med Fremviser-tilladelser, kan du føje dem til webstedet SharePoint med læsetilladelser.

### <a name="sharepoint-guest-settings"></a>SharePoint gæsteindstillinger

Indstillingen for gæstedeling, som du valgte, da du oprettede etiketten (som kun påvirker teammedlemskab), skal svare til indstillingerne for gæstedeling for det tilknyttede SharePoint websted på følgende måde:

|Etiketindstilling|SharePoint webstedsindstilling|
|:------------|:----------------------|
|**Lad Office 365 gruppeejere føje personer uden for organisationen til den gruppe, der er** valgt|**Nye og eksisterende gæster** (standard for nye teams)|
|**Lad Office 365 gruppeejere føje personer uden for organisationen til den gruppe, der** ikke er markeret|**Kun personer i din organisation**|

Vi opdaterer også standardlinktypen for deling for at reducere risikoen for utilsigtet deling af filer og mapper med en bredere målgruppe end beregnet.

Sådan opdateres indstillinger for websted

1. Åbn administration SharePoint, og vælg **Aktive websteder** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>
1. Vælg det websted, der er knyttet til teamet.
1. På fanen **Politikker** under Ekstern **deling skal** du vælge **Rediger**.
1. Hvis du har tilladt gæstedeling, da du oprettede den følsomme etiket, skal du sikre **dig, at Nye og eksisterende gæster** er markeret. Hvis du ikke tillader deling, da du oprettede navnet, skal du vælge **Kun personer i organisationen**.
1. Fjern markeringen i afkrydsningsfeltet Samme som indstilling på **organisationsniveau under** Standardtype for delingslink, og vælg **Personer med eksisterende adgang**.
1. Vælg **Gem**.

#### <a name="private-channels"></a>Private kanaler

Hvis du føjer private kanaler til teamet, opretter hver privat kanal et nyt SharePoint-websted med standardindstillingerne for deling. Disse websteder er ikke synlige i SharePoint Administration, så du skal bruge [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) PowerShell-cmdlet'en med følgende parametre til at opdatere indstillingerne for gæstedeling:

- `-SharingCapability Disabled` for at slå gæstedeling fra (den er slået til som standard)
- `-DefaultSharingLinkType Internal` sådan ændres standarddelingslinket til *Bestemte personer*

Hvis du ikke planlægger at bruge private kanaler sammen med dit team, kan du overveje at deaktivere muligheden for, at teammedlemmer kan oprette **dem under** Medlemstilladelser i [teamindstillinger](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc).

### <a name="site-sharing-settings"></a>Indstillinger for webstedsdeling

For at sikre, at SharePoint-webstedet ikke deles med personer, der ikke er medlemmer af teamet, begrænser vi deling til ejere. Vi begrænser også deling af filer og mapper til teamejere. Dette er med til at sikre, at ejere ved, hvornår en fil deles med en person uden for teamet.

Sådan konfigureres webstedsdeling kun for ejere
1. I Teams du gå til **fanen Generelt** for det team, du vil opdatere.
2. Klik på Filer på teamets **værktøjslinje**.
3. Klik på ellipsen, og klik derefter **på Åbn i SharePoint**.
4. Klik på ikonet for indstillinger på SharePoint webstedsværktøjslinjen, og klik derefter på **Webstedstilladelser**.
5. I ruden Webstedstilladelser under **Delingsindstillinger Indstillinger** du klikke **på Skift indstillinger for deling**.
6. Under **Delingstilladelser** skal du **vælge Kun webstedsejere kan dele filer, mapper og webstedet** og derefter klikke på **Gem**.

### <a name="custom-site-permissions"></a>Brugerdefinerede webstedstilladelser

Hvis du har føjet personer med Fremviser-tilladelser til følsomhedsmærkatet, kan du føje dem til SharePoint-webstedet med Læseadgang, så de har nem adgang til filerne.

Sådan føjer du brugere til webstedet
1. Klik på ikonet Indstillinger på webstedet, og klik derefter på **Webstedstilladelser**.
2. Klik **på Inviter** personer, og klik derefter **på Del kun websted**.
3. Skriv navnene på de brugere og grupper, du vil invitere.
4. For hver person eller gruppe, du tilføjer, skal du ændre deres tilladelser fra **Rediger** til **Læs**.
5. Vælg, om du vil sende dem en mail med et link til webstedet.
6. Klik **på Tilføj**.

## <a name="additional-protections"></a>Yderligere beskyttelse

Microsoft 365 tilbyder yderligere metoder til sikring af dit indhold. Overvej, om følgende indstillinger kan være med til at forbedre sikkerheden for din organisation.

- Få dine gæster til at acceptere [vilkår for anvendelse](/azure/active-directory/conditional-access/terms-of-use).
- Konfigurer en [politik for timeout for en session](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) for gæster.
- Opret [typer af følsomme oplysninger,](../compliance/sensitive-information-type-learn-about.md) og brug [beskyttelse mod datatab til at](../compliance/dlp-learn-about-dlp.md) angive politikker vedrørende adgang til følsomme oplysninger.
- Brug [Azure Active Directory til at](/azure/active-directory/governance/access-reviews-overview) gennemgå teamadgang og -medlemskab regelmæssigt.

## <a name="drive-user-adoption-for-team-members"></a>Fremme brugerindføring for teammedlemmer

Når teamet er på plads, er det tid til at fremme indføringen af dette team og dets ekstra sikkerhed for teammedlemmer.

### <a name="train-your-users"></a>Oplære dine brugere

Medlemmer af teamet kan få adgang til teamet og alle dets ressourcer, herunder chats, møder og andre apps. Når du arbejder med filer fra **sektionen Filer** i en kanal, skal medlemmer af teamet tildele følsomhedsmærkatet til de filer, de opretter.

Når etiketten anvendes på filen, krypteres den. Medlemmer af teamet kan åbne den og samarbejde i realtid. Hvis filen forlader webstedet og videresendes til en ondsindet bruger, skal de angive legitimationsoplysninger for en brugerkonto, der er medlem af teamet, for at åbne filen og få vist indholdet. 

Oplære dine teammedlemmer:

- Om vigtigheden af at bruge det nye team til chatsamtaler, møder, filer og andre ressourcer på SharePoint-webstedet og konsekvenserne af en meget regulerede datalækage, f.eks juridiske konsekvenser, lovgivningsmæssige fines, ransomware eller tab af konkurrencemæssige fordele.
- Sådan får du adgang til teamet.
- Sådan opretter du nye filer på webstedet og overfører nye filer, der er gemt lokalt.
- Sådan mærker du filer med teamets korrekte følsomhedsmærkat.
- Sådan beskytter etiketten filer, selv når de er sivet væk fra webstedet.

Dette kursus bør omfatte praktiske øvelser, så dine teammedlemmer kan opleve disse egenskaber og deres resultater.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Udfør periodiske anmeldelser af brug og adressering af teammedlemmers feedback

I ugerne efter træning:

- Håndter hurtigt teammedlemmers feedback, og finjuster politik og konfigurationer.
- Analysér brugen for teamet, og sammenlign det med forbrugsforventninger.
- Kontrollér, at meget regulerede filer er blevet mærket korrekt med følsomhedsetiketten. Du kan se, hvilke filer der har fået tildelt en etiket, ved at få vist en mappe i SharePoint og  tilføje kolonnen Følsomhed via indstillingen Vis **/** skjul kolonner **i Tilføj kolonne**.

Omskod dine brugere efter behov.

## <a name="see-also"></a>Se også

[Azure AD-Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)