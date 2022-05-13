---
title: Konfigurer et team med sikkerhedsisolation ved hjælp af en entydig følsomhedsmærkat
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
description: Få mere at vide om, hvordan du opretter et team med en unik følsomhedsmærkat af hensyn til sikkerheden.
ms.openlocfilehash: 15f155255518df38921288f68dcc9365703e4f2a
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393104"
---
# <a name="configure-a-team-with-security-isolation-by-using-a-unique-sensitivity-label"></a>Konfigurer et team med sikkerhedsisolation ved hjælp af en entydig følsomhedsmærkat

I denne artikel får du anbefalinger og trin til at konfigurere et privat team i Microsoft Teams og bruge en entydig følsomhedsmærkat til at kryptere filer, så det kun er teammedlemmer, der kan dekryptere dem.

Ud over den private adgang beskriver denne artikel, hvordan du konfigurerer det tilknyttede SharePoint websted, som du kan få adgang til fra afsnittet **Filer** på en teamkanal, for den ekstra sikkerhed, der kræves for at gemme stærkt regulerede data.

Elementerne i konfigurationen for et team med sikkerhedsisolation er:

- Et privat team
- Yderligere sikkerhed på det tilknyttede SharePoint websted for det team, der:
  - Forhindrer medlemmer af webstedet i at dele webstedet med andre.
  - Forhindrer, at ikke-medlemmer af webstedet anmoder om adgang til webstedet.
- En følsomhedsmærkat specifikt for dette team, der:
    - Forhindrer adgang til SharePoint indhold fra ikke-administrerede enheder
    - Tillader eller afviser gæsteadgang til teamet, afhængigt af dine krav
    - Krypterer dokumenter, som mærkaten anvendes på

> [!IMPORTANT]
> Sørg for, at du har aktiveret [følsomhedsmærkater for at beskytte indhold i Microsoft Teams, Office 365 grupper og SharePoint websteder,](../compliance/sensitivity-labels-teams-groups-sites.md) før du fortsætter med trinnene i denne artikel.

Se denne video for at få en oversigt over udrulningsprocessen.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a>Du kan se en 1-siders oversigt over dette scenarie i [plakaten Microsoft Teams med sikkerhedsisolering](../downloads/team-security-isolation-poster.pdf).

[![Microsoft Teams med plakat med sikkerhedsisolation.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Du kan også downloade denne plakat i [PDF-](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf) eller [PowerPoint](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) formater og udskrive den på brev-, juridisk eller tabloid-papirstørrelse (11 x 17).

Prøv denne konfiguration i dit eget testlaboratorium med [disse instruktioner](team-security-isolation-dev-test.md).

Se, hvordan Contoso Corporation brugte et isoleret team til et tophemmeligt projekt i [denne casestudie](contoso-team-for-top-secret-project.md).

## <a name="initial-protections"></a>Indledende beskyttelse

Gennemse følgende bedste fremgangsmåder for at hjælpe med at beskytte adgangen til teamet og dets underliggende SharePoint websted:
- [Politikker for identitets- og enhedsadgang](../security/office-365-security/identity-access-policies.md)
- [SharePoint politikker for onlineadgang](../security/office-365-security/sharepoint-file-access-policies.md)
- [Udrul teams med grundlæggende beskyttelse](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Gæstedeling

Afhængigt af din virksomheds karakter vil du måske aktivere gæstedeling for dette team. Hvis du planlægger at samarbejde med personer uden for din organisation i teamet, skal du aktivere gæstedeling. 

Du kan finde oplysninger om sikker deling med gæster i følgende ressourcer:

- [Begræns utilsigtet eksponering af filer, når der deles med personer uden for din organisation](./share-limit-accidental-exposure.md)
- [Opret et sikkert gæstedelingsmiljø](./create-secure-guest-sharing-environment.md)

Hvis du vil tillade eller blokere gæstedeling, bruger vi en kombination af en følsomhedsmærkat for teamet og kontrolelementerne til deling på webstedsniveau for det tilknyttede SharePoint websted, som begge drøftes senere.

## <a name="create-a-private-team"></a>Opret et privat team

Da vi opretter en følsomhedsmærkat specifikt for dette team, er næste trin at oprette teamet. Hvis du har et eksisterende team, kan du bruge det.

Sådan opretter du et team til følsomme oplysninger
1. I Teams skal du klikke på **Teams** i venstre side af appen og derefter klikke på **Deltag eller opret et team** nederst på listen over teams.
2. Klik på **Opret team** (første kort, øverste venstre hjørne).
3. Vælg **Opret et team fra bunden**.
4. Bevar standarden på listen **Følsomhed** .
5. Klik på **Privat** under **Beskyttelse af personlige oplysninger**.
6. Skriv et navn til den gruppe, der er relateret til det følsomme projekt. F.eks. **Project Saturn**.
7. Klik på **Opret**.
8. Føj brugere til teamet, og klik derefter på **Luk**.

## <a name="private-channel-settings"></a>Indstillinger for privat kanal

Vi anbefaler, at du begrænser oprettelse af private kanaler til teamejere.

Sådan begrænser du oprettelse af private kanaler
1. Klik på **Flere indstillinger** i teamet, og klik derefter på **Administrer team**.
2. Udvid **Medlemstilladelser** under fanen **Indstillinger**.
3. Fjern markeringen i afkrydsningsfeltet **Tillad, at medlemmer opretter private kanaler** .

Du kan også bruge [teams-politikker](/MicrosoftTeams/teams-policies) til at styre, hvem der kan oprette private kanaler.

## <a name="create-a-sensitivity-label"></a>Opret en følsomhedsmærkat

Hvis du vil konfigurere et team til sikkerhedsisolation, bruger vi en følsomhedsmærkat, der er oprettet specielt til dette team. Denne mærkat bruges på teamniveau til at styre gæstedeling og til at blokere adgang fra ikke-administrerede enheder. Den kan også bruges til at klassificere og kryptere individuelle filer i teamet, så det kun er teamejere og -medlemmer, der kan åbne dem.

Hvis du har en intern partner eller interessentgruppe, der skal kunne få vist krypterede dokumenter, men ikke redigere dem, kan du føje dem til etiketten med visningstilladelser. Du kan derefter føje disse personer til teamets SharePoint websted med læserettigheder, og de har skrivebeskyttet adgang til det websted, hvor dokumenterne opbevares, men ikke selve teamet.

Sådan opretter du en følsomhedsmærkat

1. Åbn Microsoft Purview-compliance-portal, og vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Information Protection**</a> under **Løsninger**.
1. Klik på **Opret en etiket**.
1. Giv etiketten et navn. Vi foreslår, at du navngiver det efter det team, du bruger det sammen med.
1. Tilføj et vist navn og en beskrivelse, og klik derefter på **Næste**.
1. På **siden Definer omfanget for denne etiket** skal du vælge **Filer & mails** og **grupper & websteder** og klikke på **Næste**.
1. På siden **Vælg beskyttelsesindstillinger for filer og mails** skal du vælge **Kryptér filer og mails**, og klik derefter på **Næste**.
1. På siden **Kryptering** skal du vælge **Konfigurer krypteringsindstillinger**.
1. Klik på **Tilføj brugere eller grupper**, vælg det team, du har oprettet, og klik derefter på **Tilføj**
1. Klik på **Vælg tilladelser**.
1. Vælg **Medforfatter** på rullelisten, og klik derefter på **Gem**.
1. Hvis du vil medtage brugere eller grupper med skrivebeskyttet adgang til filer med mærkaten:
    1. Klik på **Tildel tilladelser**.
    1. Klik på **Tilføj brugere eller grupper**, vælg de brugere eller grupper, du vil tilføje, og klik derefter på **Tilføj**.
    1. Klik på **Vælg tilladelser**.
    1. Vælg **Fremviser** på rullelisten, og klik derefter på **Gem**.
13.  Klik på **Gem**, og klik derefter på **Næste**.
14. Klik på **Næste** på siden *Automatisk mærkning af filer og mails**.
15. På siden **Definer beskyttelsesindstillinger for grupper og websteder** skal du vælge **Beskyttelse af personlige oplysninger og indstillinger for ekstern brugeradgang** og **Indstillinger for enhedsadgang og ekstern deling** og klikke på **Næste**.
16. På siden **Definer indstillinger for beskyttelse af personlige oplysninger og ekstern brugeradgang** under **Beskyttelse af personlige oplysninger** skal du vælge indstillingen **Privat** .
17. Hvis du vil tillade gæsteadgang, skal du under **Adgang til eksterne brugere** vælge **Lad Microsoft 365 gruppeejere føje personer uden for organisationen til gruppen som gæster**.
18. Klik på **Næste**.
19. På siden **Definer indstillinger for ekstern deling og enhedsadgang** skal du vælge **Kontrollér ekstern deling fra navngivne SharePoint websteder**.
20. Under **Indhold kan deles med** skal du vælge **Nye og eksisterende gæster** , hvis du tillader gæsteadgang eller **Kun personer i din organisation** , hvis ikke.
21. Under **Adgang fra ikke-administrerede enheder** skal du vælge **Bloker adgang**.
22. Klik på **Næste**.
23. Klik på **Næste** på siden **Automatisk mærkning af databasekolonner**.
24. Klik på **Opret navn**, og klik derefter på **Udført**.

Når du har oprettet mærkaten, skal du publicere den til de brugere, der skal bruge den. I dette tilfælde gør vi etiketten kun tilgængelig for personer i teamet.

Sådan udgiver du en følsomhedsmærkat:

1. Vælg fanen **Mærkatpolitikker** på <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">siden **Information Protection**</a> i Microsoft Purview-compliance-portal.
2. Klik på **Publicer navne**.
3. På siden **Vælg følsomhedsmærkater, der skal udgives** skal du klikke på **Vælg følsomhedsmærkater, der skal publiceres**.
4. Vælg den etiket, du har oprettet, og klik derefter på **Tilføj**.
5. Klik på **Næste**.
6. På siden Publicer til brugere og grupper skal du klikke på **Vælg brugere og grupper**.
7. Klik på **Tilføj**, og vælg derefter det team, du har oprettet.
8. Klik på **Tilføj**, og klik derefter på **Udført**.
9. Klik på **Næste**.
10. På siden Politikindstillinger skal du markere afkrydsningsfeltet **Brugere skal angive begrundelse for at fjerne en etiket eller en lavere klassificeringsmærkat** og derefter klikke på **Næste**.
11. Skriv et navn til politikken, og klik derefter på **Næste**.
12. Klik på **Send,** og klik derefter på **Udført**.

## <a name="apply-the-label-to-the-team"></a>Anvend etiketten på teamet

Når etiketten er publiceret, skal du anvende den på teamet, for at indstillingerne for gæstedeling og administrerede enheder kan træde i kraft. Dette gøres i SharePoint Administration. Bemærk, at det kan tage noget tid, før etiketten bliver tilgængelig, når den er publiceret.

Sådan anvender du følsomhedsmærkaten

1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> under **Websteder**.
1. Vælg det websted, der er knyttet til teamet.
1. Under fanen **Politikker** under **Følsomhed** skal du vælge **Rediger**.
1. Vælg det navn, du har oprettet, og vælg derefter **Gem**.

## <a name="sharepoint-settings"></a>indstillinger for SharePoint

Der er tre trin at udføre i SharePoint:

- Opdater indstillingerne for gæstedeling for webstedet i SharePoint Administration, så de stemmer overens med det, du valgte, da du oprettede mærkaten, og opdater standardlinket til deling til *Personer med eksisterende adgang*.
- Opdater indstillingerne for webstedsdeling på selve webstedet for at forhindre medlemmer i at dele filer, mapper eller webstedet og deaktivere adgangsanmodninger.
- Hvis du har føjet personer eller grupper til etiketten med læserettigheder, kan du føje dem til det SharePoint websted med læsetilladelser.

### <a name="sharepoint-guest-settings"></a>SharePoint gæsteindstillinger

Den indstilling for gæstedeling, du valgte, da du oprettede mærkaten (som kun påvirker teammedlemskab), skal stemme overens med indstillingerne for gæstedeling for det tilknyttede SharePoint websted på følgende måde:

|Navneindstilling|SharePoint webstedsindstilling|
|:------------|:----------------------|
|**Lad Office 365 gruppeejere føje personer uden for organisationen til den valgte gruppe**|**Nye og eksisterende gæster** (standard for nye teams)|
|**Lad Office 365 gruppeejere føje personer uden for organisationen til den gruppe, der** ikke er valgt|**Kun personer i din organisation**|

Vi opdaterer også standardtypen for delingslink for at reducere risikoen for utilsigtet deling af filer og mapper til en større målgruppe end forventet.

Sådan opdaterer du webstedsindstillinger

1. Åbn SharePoint Administration, og vælg <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Aktive websteder**</a> under **Websteder**
1. Vælg det websted, der er knyttet til teamet.
1. Under fanen **Politikker** under **Ekstern deling** skal du vælge **Rediger**.
1. Hvis du har tilladt gæstedeling, da du oprettede den følsomme mærkat, skal du sørge for, at **Nye og eksisterende gæster** er valgt. Hvis du ikke tillader deling, da du oprettede mærkaten, skal du vælge **Kun personer i din organisation**.
1. Under Standardlinktype for deling skal du fjerne markeringen i afkrydsningsfeltet **Samme som indstilling på organisationsniveau** og vælge **Personer med eksisterende adgang**.
1. Vælg **Gem**.

#### <a name="private-channels"></a>Private kanaler

Hvis du føjer private kanaler til teamet, opretter hver privat kanal et nyt SharePoint websted med standardindstillingerne for deling. Disse websteder er ikke synlige i SharePoint Administration, så du skal bruge PowerShell-cmdlet'en [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) med følgende parametre til at opdatere indstillingerne for gæstedeling:

- `-SharingCapability Disabled` for at slå gæstedeling fra (den er som standard slået til)
- `-DefaultSharingLinkType Internal` for at ændre standardlinket til deling til *bestemte personer*

Hvis du ikke har planer om at bruge private kanaler sammen med dit team, kan du overveje at deaktivere teammedlemmernes mulighed for at oprette dem under **Medlemstilladelser** i [teamindstillinger](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc).

### <a name="site-sharing-settings"></a>Indstillinger for webstedsdeling

For at hjælpe med at sikre, at det SharePoint websted ikke deles med personer, der ikke er medlemmer af teamet, begrænser vi delingen til ejere. Vi begrænser også deling af filer og mapper til teamejere. Dette hjælper med at sikre, at ejerne er opmærksomme på, når en fil deles med en person uden for teamet.

Sådan konfigurerer du webstedsdeling, der kun er for ejere
1. I Teams skal du gå til fanen **Generelt** for det team, du vil opdatere.
2. Klik på **Filer** på værktøjslinjen for teamet.
3. Klik på ellipsen, og klik derefter på **Åbn i SharePoint**.
4. Klik på ikonet Indstillinger på værktøjslinjen på det underliggende SharePoint websted, og klik derefter på **Webstedstilladelser**.
5. Klik på **Rediger indstillinger for deling** under **Deling Indstillinger** i ruden Webstedstilladelser.
6. Under **Delingstilladelser** skal du vælge **Kun webstedsejere kan dele filer, mapper og webstedet** og derefter klikke på **Gem**.

### <a name="custom-site-permissions"></a>Brugerdefinerede webstedstilladelser

Hvis du har føjet personer med læserettigheder til følsomhedsmærkaten, kan du føje dem til det SharePoint websted med læseadgang, så de har nem adgang til filerne.

Sådan føjer du brugere til webstedet
1. Klik på ikonet indstillinger på webstedet, og klik derefter på **Webstedstilladelser**.
2. Klik på **Inviter personer**, og klik derefter på **Del kun websted**.
3. Skriv navnene på de brugere og grupper, du vil invitere.
4. For hver person eller gruppe, du tilføjer, skal du ændre deres tilladelser fra **Rediger** til **Læs**.
5. Vælg, om du vil sende dem en mail med et link til webstedet.
6. Klik på **Tilføj**.

## <a name="additional-protections"></a>Yderligere beskyttelse

Microsoft 365 tilbyder yderligere metoder til beskyttelse af dit indhold. Overvej, om følgende indstillinger kan hjælpe med at forbedre sikkerheden for din organisation.

- Få dine gæster til at acceptere vilkår [for anvendelse](/azure/active-directory/conditional-access/terms-of-use).
- Konfigurer en [timeoutpolitik for session](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) for gæster.
- Opret [følsomme oplysningstyper](../compliance/sensitive-information-type-learn-about.md) , og brug [beskyttelse mod datatab](../compliance/dlp-learn-about-dlp.md) til at angive politikker for adgang til følsomme oplysninger.
- Brug [Azure Active Directory adgangsgennemgange](/azure/active-directory/governance/access-reviews-overview) til jævnligt at gennemse teamadgang og -medlemskab.

## <a name="drive-user-adoption-for-team-members"></a>Kør brugertiltrædelse for teammedlemmer

Når teamet er på plads, er det tid til at fremme vedtagelsen af dette team og dets ekstra sikkerhed for teammedlemmerne.

### <a name="train-your-users"></a>Oplær dine brugere

Medlemmer af teamet kan få adgang til teamet og alle dets ressourcer, herunder chats, møder og andre apps. Når du arbejder med filer fra afsnittet **Filer** på en kanal, skal teamets medlemmer tildele følsomhedsmærkaten til de filer, de opretter.

Når mærkaten anvendes på filen, krypteres den. Medlemmer af teamet kan åbne den og samarbejde i realtid. Hvis filen forlader webstedet og videresendes til en ondsindet bruger, skal vedkommende angive legitimationsoplysninger for en brugerkonto, der er medlem af teamet, for at åbne filen og få vist dens indhold. 

Oplær dine teammedlemmer:

- Om vigtigheden af at bruge det nye team til chats, møder, filer og de andre ressourcer på SharePoint site og konsekvenserne af en højt reguleret datalækage, såsom juridiske konsekvenser, lovmæssige bøder, ransomware, eller tab af konkurrencemæssig fordel.
- Sådan får du adgang til teamet.
- Sådan opretter du nye filer på webstedet og overfører nye filer, der er gemt lokalt.
- Sådan navngiver du filer med den korrekte følsomhedsmærkat for teamet.
- Hvordan mærkaten beskytter filer, selvom de lækkes fra webstedet.

Denne træning bør omfatte praktiske øvelser, så dine teammedlemmer kan opleve disse funktioner og deres resultater.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Udfør periodiske gennemgange af brugen, og løs feedback fra teammedlemmer

I ugerne efter træningen:

- Løs hurtigt feedback fra teammedlemmer, og finjuster politikker og konfigurationer.
- Analysér forbruget for teamet, og sammenlign det med forbrugsforventninger.
- Kontrollér, at stærkt regulerede filer er forsynet med en korrekt mærkat med følsomhedsmærkaten. Du kan se, hvilke filer der har fået tildelt en mærkat, ved at få vist en mappe i SharePoint og tilføje kolonnen **Følsomhed** via indstillingen **Vis/skjul kolonner** i **Tilføj kolonne**.

Oplær dine brugere efter behov.

## <a name="see-also"></a>Se også

[Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)
