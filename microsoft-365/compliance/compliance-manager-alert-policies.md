---
title: Besked- og beskedpolitikker i Microsoft Purview Compliance Manager
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du opretter beskeder for aktiviteter i Microsoft Purview Compliance Manager, der kan påvirke din score for overholdelse af angivne standarder.
ms.openlocfilehash: 32ab22f47d35d64fa72dcc4898f5fff06d20c13c
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231731"
---
# <a name="microsoft-purview-compliance-manager-alerts-and-alert-policies"></a>Besked- og beskedpolitikker i Microsoft Purview Compliance Manager

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

**I denne artikel:** Få mere at vide om, hvordan **du angiver beskeder** for visse aktiviteter i Overholdelsesstyring, hvordan du administrerer beskeder, og hvordan **du opretter beskedpolitikker** for at definere betingelser for beskeder.

## <a name="overview"></a>Oversigt
Manger kan advare dig om ændringer, så snart de sker, så du kan holde styr på dine mål for overholdelse af angivne standarder. Du kan f.eks. konfigurere beskeder for at informere dig, når en forbedringshandlings scoreværdi er steget eller reduceret på grund af en konfigurationsændring i din lejer, eller når en forbedringshandling er tildelt en bruger til at udføre implementerings- eller testarbejde. Få vist de [typer hændelser](#create-an-alert-policy) , som du kan oprette beskeder for.

Hvis du vil oprette beskeder, skal du først konfigurere en beskedpolitik for at skitsere de betingelser, der udløser en besked, og hyppigheden af meddelelser. Når vi registrerer et match til dine politikbetingelser, modtager du en meddelelse via mail med oplysninger, så du kan afgøre, om du vil undersøge det eller foretage dig yderligere.

Alle beskeder vises under fanen **Beskeder** i Overholdelsesstyring, og alle beskedpolitikker vises **under fanen Politikker for beskeder**.  Alle organisationer har allerede konfigureret en [standardpolitik for ændring af score](#default-score-change-policy) for dem.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Om siderne Beskeder og Beskedpolitikker

> [!IMPORTANT]
> Brugerne skal have rollen **Sikkerhedslæser** i Azure Active Directory (AD) for at få adgang til siderne **med politikker for beskeder** og **beskeder** i Overholdelsesstyring. Der kræves yderligere roller som Sikkerheds- og Overholdelsesstyring for at arbejde med beskeder og beskedpolitikker. Få flere oplysninger nedenfor under [Tilladelser til beskedpolitik](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Siden Beskedpolitikker

Vælg fanen **Beskedpolitikker** i Overholdelsesstyring for at få vist og administrere dine politikker for beskeder. Siden **Beskedpolitikker** indeholder en tabel med alle de politikker, der er oprettet af din organisation. Fra denne side kan du oprette nye politikker, redigere eksisterende politikker og ændre aktiveringsstatus og slette politikker.

I **kolonnen Status** betyder **Aktiv** , at politikken er i kraft og udløser beskeder, når betingelser er opfyldt. **Inaktiv** betyder, at politikken findes, men genererer ikke beskeder. I politiktabellen kan du også se alvorsgraden af politikken og den dato, hvor politikken sidst blev ændret.

Hvis du vil have vist detaljer om en individuel politik, skal du vælge dens række i tabellen. Der vises en pop op-rude, der viser alle detaljer. Vælg knappen **Handling** nederst i ruden, og vælg mellem indstillinger for at redigere politikken, få vist dens beskeder eller slette den. Kommandoerne til at tilføje, redigere, slette, aktivere og deaktivere er også tilgængelige øverst i tabellen over filtrene.

Hvis du vil i gang med at oprette en beskedpolitik, skal du se [Opret en beskedpolitik](#create-an-alert-policy).

### <a name="alerts-page"></a>Siden Beskeder

Vælg fanen **Beskeder** i Overholdelsesstyring for at få vist og administrere dine beskeder. Siden **Beskeder** indeholder en tabel med en liste over hver besked, der genereres af en beskedpolitik, sammen med dens alvorsgrad og den udløsende hændelse (f.eks. en handlings resultatændring) og datoen for beskeden.

Hvis du vil have vist en individuel besked, skal du vælge rækken i tabellen. Der vises en pop op-rude, der viser alle detaljer under fanen **Oversigt** i ruden. Under fanen **Hændelseslog** vises de handlinger, der udføres af brugere, der udløste beskeden.

Knappen **Handling** nederst i ruden indeholder indstillinger til at tildele beskeden til en bruger til opfølgning, sende en mail til den bruger, hvis handlinger genererede beskeden, eller få vist detaljerne for den politik, der genererer beskeden. Du kan også udføre de samme handlinger ved at vælge den runde knap, der vises til venstre for beskednavnet, når du holder markøren over rækken og derefter vælger en af knapperne øverst i tabellen over filtrene.

Hvis du vil i gang med at arbejde med beskeder, skal [du se Visning og administration af beskeder](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Tilladelser til beskedpolitik

I nedenstående tabel beskrives, hvilke brugere der kan oprette og redigere beskeder og beskedpolitikker baseret på deres rolletype. Ud over at have rollen Overholdelsesadministrator skal brugerne også have en Azure AD rolle på følgende måde:

- Rollen **Sikkerhedslæser** i Azure AD til visning af beskeder og beskedpolitikker
- Rollen **Sikkerhedsadministrator** i Azure AD til oprettelse eller opdatering af beskedpolitikker
 
Få mere at vide om [Azure-roller på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-compliance-portal).


| Rolle | Kan oprette og redigere politikker | Beskeder kan redigeres | 
| :------------- | :-------------: | :------------: |
| **Administration af Overholdelsesstyring**| Ja  | Ja | 
| **Vurdering af overholdelsesstyring**| Ja | Ja | 
| **Bidrag til Overholdelsesstyring**| Ja | Ja | 
| **Global administrator**| Ja | Ja  | 
| **Læser til Overholdelsesstyring**| Nej | Nej | 

Få mere at vide om, hvordan [du angiver brugertilladelser og tildeler roller til Overholdelsesstyring](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Opret en beskedpolitik

Du kan oprette politikker, der giver dig besked, når visse ændringer eller hændelser, der er relateret til forbedringshandlinger, sker. Hændelsestyper er angivet nedenfor.

### <a name="alert-event-types"></a>Hændelsestyper for beskeder

- **Ændring af score**: en stigning eller et fald i point, der tildeles for en forbedringshandling på grund af konfigurationsændringer foretaget af en person i din organisation. Hvis din organisation f.eks. opretter en insiderrisikostyringspolitik, kan det øge dine point for en bestemt handling med et bestemt beløb.
- **Ændring af tildeling**: En forbedringshandling er tildelt til en bruger, er blevet tildelt en anden bruger igen eller ikke-tildelt fra en bruger.
- **Ændring af implementeringsstatus**: En bruger har ændret implementeringsstatus for en forbedringshandling.
- **Ændring af teststatus**: En bruger har ændret teststatussen for en forbedringshandling.
- **Ændring af bevismateriale**: En bruger har uploadet eller slettet et bevisdokument under fanen **Dokumenter** i forbedringshandlingen.

#### <a name="default-score-change-policy"></a>Politik for ændring af standardresultat

Overholdelsesstyring konfigurerer en standardbeskedpolitik, der skal overvåges for scoreændringer i forbedringshandlinger. Standardpolitikken genererer en besked, når en forbedringshandlings score ændres. De fleste indstillinger for standardpolitikken kan ikke redigeres, men du kan tilføje flere modtagere til meddelelser.

Her er indstillingerne for standardpolitikken:

- Alle match, der registreres inden for et tidsrum af 60 minutter, grupperes i én enkelt besked for at reducere overdrevne meddelelser. Hvis fem forbedringshandlinger f.eks. oplever en scoreændring inden for én time, genereres der én besked.

- Alvorsgraden for disse beskeder er **mellem**.

- Den globale administrator for din organisation er standardmodtageren af beskedmeddelelser.

- Du kan tilføje flere modtagere af beskeder ved at følge disse trin:
    - Find **standardbeskedpolitikken for Overholdelsesstyring** på siden **Politikker for beskeder**.
    - Markér afkrydsningsfeltet til venstre for navnet, og vælg knappen **Rediger** øverst over filtrene.
    - Vælg knappen **Næste** , indtil du kommer til siden **Beskedmodtagere** .
    - Vælg **+Vælg modtagere** , og markér afkrydsningsfelterne ud for hvert brugernavn i pop op-ruden, som du vil modtage mailmeddelelsen til. Når du er færdig, skal du vælge **Tilføj modtager** og derefter vælge **Næste**.
    - På siden **Gennemse og afslut** skal du vælge **Opdater** for at gemme dine ændringer.

- Standardpolitikken kan ikke slettes, men du kan deaktivere den ved [at følge de trin, der er beskrevet nedenfor](#activate-or-inactivate-a-policy).


### <a name="policy-creation-steps"></a>Trin til oprettelse af politik

Hvis du vil oprette en politik for at generere beskeder baseret på en eller flere hændelser, skal du følge nedenstående trin:

1. I **Overholdelsesstyring** skal du gå til siden **Beskedpolitikker** og vælge **+Tilføj** for at starte guiden til oprettelse af politikker.

2. På siden **Navn og beskrivelse** skal du angive et navn til politikken og en valgfri beskrivelse og derefter vælge **Næste**.

3. På siden **Betingelser** skal du vælge en eller flere hændelser, der udløser en besked. Under overskriften **Aktivitet i forbindelse med forbedring** skal du vælge **Tilføj underbetingelser** og markere afkrydsningsfeltet, der vises, når du holder markøren til venstre for hvert betingelsesnavn. Du kan vælge en eller flere betingelser for en politik: tildelingsændring, bevisændring, ændring af implementeringsstatus, ændring af score, ændring af teststatus. Når du er færdig, skal du vælge **Næste**.

4. På siden Resultater skal du vælge, hvad der sker, når der **registreres** et politikmatch:
      - Vælg et alvorsgradsniveau for beskeden, når der registreres et match: lav, mellem eller høj.
      - Vælg, hvor ofte du vil have besked via mail, når der registreres et match. Du kan vælge at få besked med hvert match eller vælge en tærskel på et bestemt antal match over tre.
      - Hvis du vælger at få besked efter tre eller flere matches, skal du angive det antal minutter, hvor grænsen skal nås (f.eks. 4 kampe inden for 90 minutter).
  
    Når du er færdig, skal du vælge **Næste**.

5. På siden **Beskedmodtager** skal du vælge flere brugere i din organisation for at modtage en mail, når politikbetingelserne er opfyldt. Den bruger, der opretter politikken, er standardmodtageren. Vælg **+Vælg modtagere** , og markér afkrydsningsfelterne ud for hvert brugernavn i pop op-ruden, som du vil modtage mailmeddelelsen til. Når du er færdig, skal du vælge **Tilføj modtagere** og derefter vælge **Næste**.

6. Gennemse alle markeringer, og foretag eventuelle ændringer i hver sektion ved at vælge og derefter vælge **Næste**. Når du er færdig med at gennemse, skal du vælge **Opret politik**.

7. Når din politik er oprettet, skal du vælge **Udført**. Du ankommer til siden **med politikker for beskeder** med pop op-ruden for den politik, du lige har oprettet, og som allerede er åben.

Din politik er aktiv, når du har oprettet den, hvilket betyder, at den begynder at registrere matches og generere beskeder. Se afsnittet **Administration af politikker** nedenfor for at få oplysninger om, hvordan du deaktiverer eller sletter politikker.

Det kan tage op til 24 timer, efter at du har oprettet eller opdateret en politik, før den pågældende politik genererer beskeder. Se [Få vist detaljer om beskeder](#view-alert-details) nedenfor for at få mere at vide om udløserhændelser og beskedsammenlægning.

## <a name="managing-policies"></a>Administration af politikker

Siden **Beskedpolitikker** indeholder en tabel over alle dine politikker. Se [siden Beskedpolitikker](#alert-policies-page) for at få en yderligere forståelse af denne side. Alle brugere i organisationen kan få vist politikker, men visse handlinger er begrænset til bestemte roller. se [Tilladelser til advarselspolitik](#alert-policy-permissions).

### <a name="view-policy-details"></a>Vis politikdetaljer

Vælg en politik på rækken på siden **Beskedpolitikker** for at få vist et pop op-panel, der viser detaljerne for politikken, herunder betingelserne for dens match, om og hvornår beskeder sendes til og til hvem samt niveau for alvorsgrad.

Knappen **Handlinger** nederst i panelet giver dig mulighed for at redigere politikken, slette politikken eller få vist beskeder.

### <a name="view-a-policys-alerts"></a>Få vist en politiks beskeder

Vælg **Handlinger** i politikkens pop op-panel, og vælg derefter **Vis beskeder**. Du føres direkte til siden Beskeder med en filtreret visning af alle de beskeder, der genereres af den pågældende politik. Få mere at vide om, hvordan du [arbejder med beskeder](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>Rediger en politik

Du kan redigere et hvilket som helst aspekt af en politik med undtagelse af dens navn. Hvis du vil ændre navnet på den, skal du oprette en ny politik med et nyt navn.

Hvis du vil redigere en politik, skal du vælge den runde knap, der vises til venstre for dens navn, når du peger på dens række på siden **Beskedpolitikker** og vælge knappen **Rediger** øverst over filtrene.

Du føres til guiden til oprettelse af politikker, hvor du kan foretage og gemme ændringer af politikken.  Du kan også vælge politikken for at få vist detaljepanelet, og på knappen **Handlinger** skal du vælge **Rediger politik**. Når du har gennemgået guiden igen, skal du gennemse dine valg og i det sidste trin vælge **Opdater** for at gemme ændringerne.

Det kan tage op til 24 timer, før beskeder genereres af den opdaterede politik.

### <a name="activate-or-inactivate-a-policy"></a>Aktivér eller deaktiver en politik

Politikker aktiveres som standard, så snart de er oprettet. Når en politik er aktiv, opretter den en besked (vises på siden **Beskeder** ), når betingelserne er opfyldt, og sender en mail med en meddelelse til de angivne modtagere.

Hvis du vil ændre en politik til en **inaktiv** tilstand, hvilket betyder, at den ikke genererer beskeder, skal du vælge den afrundede knap, der vises til venstre for politiknavnet, når du holder markøren over dens række. Vælg derefter kommandoen **Deaktiver** over tabellen. Status for din politik vil nu læse Inactive. Hvis du vil genaktivere politikken, skal du følge den samme proces og vælge knappen **Aktivér** over filtrene.

### <a name="delete-a-policy"></a>Slet en politik

Hvis du vil slette en politik, kan du vælge knappen ud for dens navn på siden **Beskedpolitikker** og vælge **Slet** øverst på siden. Du kan også vælge politikken for at få vist detaljepanelet, og på knappen **Handlinger** skal du vælge **Slet politik**.

Sletning er permanent. Når du sletter en politik, genererer den ikke længere beskeder eller mailmeddelelser. Få mere at vide om [beskeder, der er forbundet med slettede politikker](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Visning og administration af beskeder

På siden **Beskeder** vises en tabel med alle de beskeder, der genereres af alle dine politikker. Beskeder genereres næsten umiddelbart efter, at en hændelse opfylder politikkens betingelser. Beskednavnet er det samme navn som den politik, der genererede beskeden.

En besked kan kun genereres ud fra en aktiv politik. Når der genereres en besked, vises den stadig på siden **Beskeder** , uanset om politikken er aktiv eller inaktiv.

### <a name="filter-your-view-of-alerts"></a>Filtrer visningen af beskeder
Du kan filtrere visningen af beskeder ved at vælge kommandoen **Filtrer** over tabellen på siden **Beskeder** . I pop op-vinduet **Filter** skal du vælge mellem disse filterindstillinger:

- Hændelsestype
- Sværhedsgraden
- Status
- Bruger, der er tildelt
- Registreringsdato
- Politiknavn

Når du har valgt, skal du vælge **Anvend**. Pop op-ruden lukkes, **og den opdaterede** beskedside viser den filtrerede visning. Dine filtre vises øverst i tabellen, men det er ikke alle filterkolonner, der vises i tabellen.

### <a name="view-alert-details"></a>Vis oplysninger om vigtige beskeder

Hvis du vil have vist alle detaljer om beskeden, herunder de hændelser, der udløste den, skal du vælge rækken i tabellen. En pop op-rude viser detaljerne for beskeden under fanen **Oversigt** i panelet.

Fanen **Hændelseslog** i pop op-panelet viser de aktiviteter, der genererede beskeden, f.eks. en scoreændring eller en tildelingsændring sammen med navnet på den bruger, der er knyttet til hver handling, og den registrerede dato.

### <a name="alert-events"></a>Beskedhændelser

Kolonnen **Hændelser** på siden **Beskeder** angiver betingelserne for en politik, der blev registreret. med andre ord den aktivitet, der genererede beskeden. Fanen **Hændelseslog** på detaljepanelet for beskeden viser hver forekomst af en hændelse, den tilknyttede bruger og den registrerede dato. Hændelsesværdier er angivet nedenfor:

- **Ændring af score**: Viser antallet af forøgelser eller reduktioner i punkter
- **Ændring af tildeling**: En forbedringshandling er blevet tildelt en bruger, tildelt en anden bruger igen eller ikke-tildelt fra en bruger
- **Ændring af implementeringsstatus**: En bruger har ændret implementeringsstatus for en forbedringshandling
- **Ændring af teststatus**: En bruger har ændret teststatussen for en forbedringshandling.
- **Ændring af bevismateriale**: En bruger har uploadet eller slettet et bevisdokument under fanen Dokumenter i forbedringshandlingen
- **Multihændelse**: Der er registreret flere forekomster af den samme type hændelse. f.eks. en enkelt forbedringshandling, der er blevet omfordelt flere gange
- **Flere betingelser**: Der blev registreret flere betingelser i en enkelt politik

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Beskedsammenlægning for flere hændelser inden for ét minut

Når der forekommer flere hændelser, der opfylder betingelserne i en beskedpolitik, med ét minut, føjes de til en eksisterende besked af en proces, der kaldes beskedsammenlægning.

Når der f.eks. forekommer én hændelse, som svarer til en politik, genereres der en besked, som vises på siden **Beskeder** , og der sendes en meddelelse. Hvis en anden hændelse, der svarer til den samme politik, indtræffer inden for ét minut efter den første hændelse, tilføjer Overholdelsesstyring oplysninger om den ekstra hændelse under fanen **Hændelseslog** for den eksisterende besked i stedet for at udløse en ny besked. Målet med sammenlægning af beskeder er at hjælpe med at reducere advarslen "træthed" og lade dig fokusere og handle på færre beskeder.

### <a name="taking-action-on-alerts"></a>Handling på beskeder

Når en af dine politikker genererer en besked, kan du få vist de hændelser, der forårsagede beskeden, og afgøre, om du skal bekræfte eller undersøge hændelserne yderligere.

Hvis du vil udføre en handling på en besked, skal du vælge rækken på siden **Beskeder** for at få vist pop op-panelet med detaljer, vælge knappen **Handlinger** og vælge mellem de indstillinger, der er angivet nedenfor. Du kan også udføre handlinger ved at vælge den runde knap, der vises til venstre for beskednavnet, når du holder markøren over rækken, og vælge en af handlingsknapperne øverst på siden over filtrene.

**Tildel besked**: Det kan være en god idé at tildele beskeden til en bruger for at undersøge eller bekræfte de hændelser, der forårsagede beskeden. Når du vælger denne indstilling, åbnes der et panel, hvor du kan vælge en bruger i din organisation og tildele beskeden til vedkommende. Du kan filtrere visningen af dine beskeder ved at vælge **Filtre** på siden **Beskeder** og angive brugerens navn i feltet **Tildelt til** .

**Mailbesked**: Det kan være en god idé at sende en mail til den bruger, der er knyttet til beskedens aktivitet, for at bekræfte, at vedkommende har foretaget handlingen. Når du vælger denne indstilling, åbnes en mailskabelon med grundlæggende oplysninger om beskeden, som du kan tilpasse med yderligere instruktioner og sendes til brugeren.

**Vis oplysninger om politik**: Det kan være en god idé at gennemse indstillingerne for den politik, der udløste beskeden. Bemærk, at når du vælger denne indstilling, føres du direkte til siden Politikker for **beskeder** , hvor panelet med politikoplysninger allerede er åbent. Du vil ikke længere være på siden **Beskeder** , når du lukker panelet med politikoplysninger.

**Skift status**: Du kan opdatere status for din besked baseret på din gennemgang af dens virkning, og om den skal undersøges. Få mere at vide om status for beskeder i næste afsnit.

### <a name="alert-status"></a>Beskedstatus

Når der oprettes en besked, er dens status **Aktiv**. Når du gennemser detaljerne for hver besked, kan du opdatere dens status til en af de tilstande, der er angivet nedenfor:

- **Aktiv**: Standardtilstanden for beskeden, indtil dens status ændres
- **Undersøgelse**: Advarsel er under undersøgelse
- **Løst**: Beskeden kræver ikke yderligere undersøgelse eller opfølgning
- **Afvist**: Beskeden er ikke relevant eller skal ikke undersøges

Hvis du vil tildele eller ændre en beskeds status, skal du vælge en besked fra rækken i tabellen og vælge **Skift status** øverst på siden over filtrene. Vælg en status i rullemenuen i pop op-vinduet Opdater beskedstatus, og vælg derefter **Opdater besked**.

Når der genereres en besked, er dens status uafhængig af status for den politik, der genererede beskeden. Det er f.eks. muligt at have en **aktiv** besked knyttet til en **inaktiv** politik, og det er muligt at have en **undersøgelsesstatus** for en besked, der blev genereret af en politik, der efterfølgende blev deaktiveret eller slettet.

### <a name="when-policies-are-deleted"></a>Når politikker slettes

Når en politik slettes, forbliver alle beskeder, der er genereret af den pågældende politik, på siden **Beskeder** , men der genereres ingen nye beskeder.

## <a name="email-notifications-of-alerts"></a>Mailmeddelelser om beskeder

Når du opretter en politik, sendes der en mail til den bruger, der oprettede politikken, og som giver dem besked om, at der blev registreret et match. Du kan vælge at sende disse mailmeddelelser til flere brugere i organisationen. Beskeder forekommer næsten i realtid, og mailmeddelelserne sendes, så snart der genereres en besked. Mailen indeholder hændelsesnavn, alvorsgrad, registreret tid og et link til at få vist beskeden i Overholdelsesstyring.

### <a name="remove-users-from-receiving-alerts"></a>Fjern brugere fra at modtage beskeder

Hvis du angiver modtagere af beskeder og senere beslutter at fjerne dem, skal du følge nedenstående trin. Bemærk, at forfatteren af politikken stadig modtager mailmeddelelser, når der registreres politikforekomster.

1. Begynd trinnene til [at redigere din politik](#edit-a-policy).
2. Når du ankommer til skærmen **Beskedmodtagere** , skal du vælge **+Vælg modtagere**.
3. Find den bruger, du vil fjerne fra meddelelser, i pop op-panelet **Vælg modtagere** , og fjern markeringen i afkrydsningsfeltet til venstre for vedkommendes navn, og vælg derefter knappen **Tilføj modtagere** (hvilket medfører, at markeringen gemmes).
4. Fortsæt gennem guiden, og bekræft, at brugeren ikke vises under **Modtagere** på siden Gennemse og afslut. Vælg **Opdater** for at gemme dine indstillinger og afslutte.
