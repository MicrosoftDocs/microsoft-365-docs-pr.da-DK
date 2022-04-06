---
title: Microsoft Compliance Manager-beskeder og -beskedpolitikker
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
description: Få mere at vide om, hvordan du opretter beskeder for aktiviteter i Microsoft Overholdelsesstyring, som kan påvirke dit resultat af overholdelse.
ms.openlocfilehash: bb81588be31b2c13113953c585112ee2f5a56875
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704685"
---
# <a name="microsoft-compliance-manager-alerts-and-alert-policies"></a>Microsoft Compliance Manager-beskeder og -beskedpolitikker

**I denne artikel:** Få mere at vide om, hvordan du angiver beskeder for visse aktiviteter i **Overholdelsesstyring** , hvordan du administrerer beskeder, og hvordan du opretter beskedpolitikker **til definition** af beskedbetingelser.

## <a name="overview"></a>Oversigt
Compliance Manger kan give dig besked om ændringer, så snart de foretages, så du kan holde styr på dine overholdelsesmål. Du kan f.eks. konfigurere påmindelser, der informerer dig, når en forbedringshandlings scoreværdi er steget eller formindsket på grund af en konfigurationsændring i din lejer, eller når en forbedringshandling er blevet tildelt en bruger til at udføre implementerings- eller testarbejde. Få vist [de typer hændelser](#create-an-alert-policy) , som du kan oprette beskeder for.

Hvis du vil oprette beskeder, skal du først konfigurere en beskedpolitik for at skitsere de betingelser, der udløser en besked, samt hyppigheden af meddelelser. Når vi registrerer et match til dine politikbetingelser, modtager du en mail med oplysninger, så du kan afgøre, om du skal undersøge eller gøre yderligere.


Alle beskeder vises på fanen Beskeder i **Overholdelsesadvarsel** , og alle beskedpolitikker er angivet på **fanen Beskedpolitikker**.

## <a name="understanding-the-alerts-and-alert-policies-pages"></a>Forstå politiksiderne Beskeder og Beskeder

> [!IMPORTANT]
> Brugere skal have **sikkerhedslæserrollen** i Azure Active Directory (AD) for at få adgang til siderne politikker for vigtige beskeder og  beskeder i **Overholdelsesstyring**. Der kræves yderligere roller for Sikkerhed og Overholdelsesstyring for at kunne arbejde med beskeder og beskedpolitikker. Få mere at vide nedenfor [under Besked om politiktilladelser](#alert-policy-permissions).

### <a name="alert-policies-page"></a>Siden Beskedpolitikker

Vælg fanen **Beskedpolitikker** i Compliance Manger for at få vist og administrere dine beskedpolitikker. Siden **Beskedpolitikker indeholder** en tabel, der viser alle de politikker, der er oprettet af organisationen. Fra denne side kan du oprette nye politikker, redigere eksisterende politikker og ændre aktiveringsstatus og slette politikker.

I kolonnen **Status betyder** **Aktiv, at** politikken er i kraft, og udløser beskeder, når betingelserne er opfyldt. **Inaktiv** betyder, at politikken findes, men ikke genererer beskeder. I tabellen over politikker kan du også se politikkens alvorsgrad og den dato, hvor politikken sidst blev ændret.

Hvis du vil have vist detaljerne for en enkelt politik, skal du markere dens række i tabellen. Der vises en pop op-rude med alle detaljer. Vælg **handlingsknappen** nederst i ruden, og vælg mellem indstillinger for at redigere politikken, få vist dens beskeder eller slette den. Kommandoerne til at tilføje, redigere, slette, aktivere og deaktivere findes også øverst i tabellen over filtrene.

Se Opret en beskedpolitik for at komme i [gang med at oprette en beskedpolitik](#create-an-alert-policy).

### <a name="alerts-page"></a>Siden Beskeder

Vælg fanen **Beskeder i Overholdelsesstyring** for at få vist og administrere dine vigtige beskeder. Siden **Vigtige beskeder** indeholder en tabel, der viser hver besked, der genereres af en beskedpolitik, samt alvorsgrad og udløsende hændelse (f.eks. en handlings scoreændring) og datoen for beskeden.

Hvis du vil have vist en enkelt besked, skal du markere dens række i tabellen. Der vises en pop op-rude med alle detaljer **på fanen** Oversigt i ruden. Fanen **Hændelseslog** viser handlinger, der er foretaget af brugere, der udløste beskeden.

Knappen **Handling** nederst i ruden indeholder indstillinger til at tildele beskeden til en bruger til opfølgning, sende en mail til den bruger, hvis handlinger oprettede beskeden, eller få vist detaljerne for den politik, der genererer beskeden. Du kan også udføre de samme handlinger ved at vælge den runde knap, der vises til venstre for beskedens navn, når du peger på dens række og derefter vælge en af knapperne øverst i tabellen over filtrene.

Se Få vist og administrer beskeder for at [komme i gang med at arbejde med beskeder](#viewing-and-managing-alerts).

## <a name="alert-policy-permissions"></a>Besked om politiktilladelser

Tabellen nedenfor viser, hvilke brugere der kan oprette og redigere beskeder og beskedpolitikker baseret på deres rolletype. Ud over at have en Overholdelsesstyring-rolle skal brugerne også have en Azure AD-rolle som følger:

- **Sikkerhedslæserrollen** i Azure AD til visning af beskeder og beskedpolitikker
- **Sikkerhedsadministratorrollen** i Azure AD til oprettelse eller opdatering af beskedpolitikker
 
Få mere at vide [om Azure-roller i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#azure-roles-in-the-microsoft-365-compliance-center).


| Rolle | Kan oprette og redigere politikker | Kan redigere beskeder | 
| :------------- | :-------------: | :------------: |
| **Administration af overholdelsesstyring**| Ja  | Ja | 
| **Compliance Manager Assessor**| Ja | Ja | 
| **Bidrag til Overholdelsesstyring**| Ja | Ja | 
| **Global Administrator**| Nej | Nej  | 
| **Overholdelsesstyringslæser**| Nej | Nej | 

Få mere at vide [om, hvordan du angiver brugertilladelser og tildeler roller for Overholdelsesstyring](compliance-manager-setup.md#set-user-permissions-and-assign-roles).

## <a name="create-an-alert-policy"></a>Opret en beskedpolitik

Du kan oprette politikker, der giver dig besked, når visse ændringer eller hændelser relateret til forbedringshandlinger sker. Hændelsestyper er angivet nedenfor.

### <a name="alert-event-types"></a>Beskedhændelsestyper

- **Scoreændring**: En stigning eller et fald i tildelte point for en forbedringshandling på grund af konfigurationsændringer foretaget af en person i din organisation. Hvis din organisation f.eks. opretter en politik for insider-risikostyring, kan det øge dine point for en bestemt handling med et bestemt beløb.
- **Tildelingsændring**: En forbedringshandling er blevet tildelt en bruger, er tildelt en anden bruger igen eller er ikke tildelt en bruger.
- **Statusændring for implementering**: En bruger har ændret implementeringens status for en forbedringshandling.
- **Teststatusændring**: En bruger har ændret teststatus for en forbedringshandling.
- **Bevisændring**: En bruger har uploadet eller slettet et dokument med bevis på **fanen Dokumenter** for forbedringshandlingen.

### <a name="policy-creation-steps"></a>Trin til oprettelse af politik

Hvis du vil oprette en politik for at generere beskeder baseret på en eller flere hændelser, skal du følge trinnene nedenfor:

1. I **Overholdelsesstyring** skal du gå til siden **Beskedpolitikker** og vælge **+Tilføj for** at starte guiden til oprettelse af politik.

2. Angiv et **navn til politikken** og en valgfri beskrivelse på siden Navn og beskrivelse, og vælg derefter **Næste**.

3. På siden **Betingelser** skal du vælge en eller flere hændelser, der udløser en besked. Under overskriften **Forbedringshandling skal** du vælge **Tilføj** underbetingelser og markere afkrydsningsfeltet, der vises, når markøren holdes til venstre for hvert betingelsesnavn. Du kan vælge en eller flere betingelser for en politik: ændring af tildeling, ændring af bevisførelse, statusændring for implementering, ændring af score, ændring af teststatus. Når du er færdig, skal du vælge **Næste**.

4. På siden **Resultater skal** du vælge, hvad der skal ske, når der registreres et politik match:
      - Vælg et alvorsniveau for beskeden, når der registreres et match: lav, mellem eller høj.
      - Vælg, hvor ofte du vil have besked via mail, når der registreres et match. Du kan vælge at få besked om hvert match, eller du kan vælge en grænseværdi for et bestemt antal matches over tre.
      - Hvis du vælger at få besked efter tre eller flere matches, angiver du det antal minutter, som denne grænse skal være nået i (f.eks. 4 matches inden for 90 minutter).
  
    Vælg Næste, når du er **færdig**.

5. På siden **Beskedmodtager skal** du vælge flere brugere i organisationen, der skal modtage en mail, når politikbetingelserne er opfyldt. Den bruger, der opretter politikken, er standardmodtageren. Vælg **+Vælg modtagere,** og markér felterne ud for hvert brugernavn i pop op-ruden, som du vil modtage mailbeskeden om. Når du er færdig, **skal du vælge Tilføj** modtagere og derefter vælge **Næste**.

6. Gennemse alle valg, og foretag eventuelle ændringer i hver sektion ved at vælge , og vælg derefter **Næste**. Vælg Opret politik, når du er **færdig med at gennemgå den**.

7. Når din politik er oprettet, skal du vælge **Udført**. Du kommer til siden Med **påmindelsespolitikker med pop** op-ruden for den politik, du lige har oprettet, der allerede er åben.

Din politik er aktiv, når du har oprettet den, hvilket betyder, at den begynder at registrere matches og generere beskeder. Se afsnittet **Administrer politikker** nedenfor for at finde ud af, hvordan du deaktiverer eller sletter politikker.

Der kan gå op til 24 timer, efter du har oprettet eller opdateret en politik, før denne politik genererer beskeder. Se [Få vist oplysninger om påmindelse](#view-alert-details) nedenfor for at få mere at vide om, hvordan du udløser hændelser og sammenlægning af beskeder.

## <a name="managing-policies"></a>Administrere politikker

Siden **Beskedpolitikker** indeholder en tabel med en oversigt over alle dine politikker. Se [siden Beskedpolitikker for](#alert-policies-page) yderligere at forstå denne side. Alle brugere i organisationen kan få vist politikker, men visse handlinger er begrænset til bestemte roller. se [Besked om politiktilladelser](#alert-policy-permissions).

### <a name="view-policy-details"></a>Vis oplysninger om politik

Vælg en politik fra dens række på  siden Beskedpolitikker for at få vist et pop op-panel, der viser politikkens detaljer, herunder dens matchbetingelser, hvorvidt og hvornår beskeder sendes, til hvem og alvorsniveau.

Knappen **Handlinger** nederst i panelet giver dig mulighed for at redigere politikken, slette politikken eller få vist beskeder.

### <a name="view-a-policys-alerts"></a>Få vist beskeder om en politik

I pop op-panelet for politikken skal du **vælge Handlinger** og derefter **Vis beskeder**. Du kommer direkte til siden Vigtige beskeder med en filtreret visning af alle de beskeder, der genereres af den pågældende politik. Få mere at vide [om at arbejde med beskeder](#viewing-and-managing-alerts).

### <a name="edit-a-policy"></a>Rediger en politik

Du kan redigere alle aspekter af en politik med undtagelse af dens navn. Hvis du vil ændre navnet, skal du oprette en ny politik med et nyt navn.

Hvis du vil redigere en politik, skal du vælge den runde knap, der vises til venstre for dens navn, når du  peger på rækken på siden Påmindelsespolitikker og vælge knappen Rediger øverst over filtrene.

Du bliver ført til guiden til oprettelse af politikker, hvor du kan foretage og gemme ændringer i din politik.  Du kan også vælge politikken for at få vist detaljepanelet, og fra **knappen Handlinger** skal du vælge **Rediger politik**. Når du har arbejdet dig gennem guiden igen, skal du gennemse dine valg og i det sidste **trin vælge Opdater** for at gemme ændringerne.

Det kan tage op til 24 timer, før beskeder genereres af den opdaterede politik.

### <a name="activate-or-inactivate-a-policy"></a>Aktivere eller deaktivere en politik

Politikker aktiveres som standard, så snart de oprettes. Når en politik er aktiv, **oprettes** der en besked (vist på siden Vigtige beskeder), når betingelserne er opfyldt, og der sendes en mail med besked til de angivne modtagere.

Hvis du vil ændre en politik  til en inaktiv tilstand, hvilket betyder, at den ikke genererer beskeder, skal du vælge den runde knap, der vises til venstre for navnet på politikken, når du peger på rækken. Vælg derefter **kommandoen Deaktiver** over tabellen. Status for din politik vil nu læse Inaktiv. Hvis du vil genaktivere politikken, skal du følge den samme proces og **vælge knappen** Aktivér over filtrene.

### <a name="delete-a-policy"></a>Slet en politik

Hvis du vil slette en politik, kan du vælge knappen ud for dens navn  på siden Beskedpolitikker og  vælge Slet øverst på siden. Du kan også vælge politikken for at få vist detaljepanelet, og fra knappen **Handlinger** skal du vælge **Slet politik**.

Når du sletter, er det en permanent sletning. Når du sletter en politik, vil den ikke længere generere beskeder eller mailbeskeder. Få mere at vide [om beskeder med forbindelse til slettede politikker](#when-policies-are-deleted).

## <a name="viewing-and-managing-alerts"></a>Få vist og administrere beskeder

Siden **Vigtige beskeder** viser en tabel med alle de beskeder, der genereres af alle dine politikker. Beskeder genereres næsten straks efter en hændelse, der opfylder politikkens betingelser. Beskedens navn er det samme navn som den politik, der genererede beskeden.

Der kan kun genereres en besked fra en aktiv politik. Når der genereres en besked, forbliver den anført på **siden Vigtige beskeder** , uanset om politikken er aktiv eller inaktiv.

### <a name="filter-your-view-of-alerts"></a>Filtrer din visning af beskeder
Du kan filtrere din visning af beskeder ved at vælge **kommandoen Filtrer** over tabellen på **siden Vigtige** beskeder. Vælg **mellem disse** filterindstillinger i pop op-ruden Filtrer:

- Hændelsestype
- Alvorsgrad
- Status
- Bruger tildelt til
- Registreringsdato
- Politiknavn

Når du har valgt en indstilling, skal du **vælge Anvend**. Pop op-ruden lukkes, og din opdaterede **side** med vigtige beskeder viser din filtrerede visning. Filtrene vises øverst i tabellen, men ikke alle filterkolonner vises i tabellen.

### <a name="view-alert-details"></a>Vis oplysninger om besked

Hvis du vil have vist alle oplysningerne om beskeden, herunder de hændelser, der udløste den, skal du markere dens række i tabellen. I pop op-ruden vises detaljerne for beskeden **på fanen** Oversigt i panelet.

Fanen **Hændelseslog** i pop op-panelet viser de aktiviteter, der genererede beskeden, f.eks. en scoreændring eller en opgaveændring sammen med navnet på den bruger, der er knyttet til hver handling, og den registrerede dato.

### <a name="alert-events"></a>Beskedhændelser

Kolonnen **Hændelser** på siden **Beskeder angiver** betingelserne for en registreret politik; med andre ord den aktivitet, der genererede beskeden. Fanen **Hændelseslog** i detaljepanelet for beskeden viser hver forekomst af en hændelse, den tilknyttede bruger og den registrerede dato. Hændelsesværdier er angivet nedenfor:

- **Scoreændring**: Viser antallet af point forøg eller formindsk
- **Tildelingsændring**: En forbedringshandling er blevet tildelt en bruger, er tildelt en anden bruger igen eller er ikke tildelt fra en bruger
- **Statusændring for implementering**: En bruger har ændret implementeringsstatus for en forbedringshandling
- **Teststatusændring**: En bruger har ændret teststatus for en forbedringshandling.
- **Bevisændring**: En bruger har uploadet eller slettet et dokument med bevis på fanen Dokumenter i forbedringshandlingen
- **Multi-event**: flere forekomster af samme type hændelse er blevet fundet; F.eks. en enkelt forbedringshandling, der er blevet tildelt flere gange
- **Flere betingelser**: der blev fundet flere betingelser i en enkelt politik

#### <a name="alert-aggregation-for-multiple-events-within-one-minute"></a>Akkumulering af beskeder for flere hændelser inden for et minut

Når flere hændelser, der opfylder betingelserne i en beskedpolitik, sker med et minut, føjes de til en eksisterende besked via en proces kaldet sammenlægning af beskeder.

Når der f.eks. sker en hændelse, der svarer til en politik, **genereres** der en besked, som vises på siden Vigtige beskeder, og der sendes en meddelelse. Hvis en anden hændelse, der matcher den samme politik, forekommer inden for et minut fra den første hændelse, tilføjer Overholdelsesstyring oplysninger om  den ekstra hændelse under fanen Hændelseslog i den eksisterende besked i stedet for at udløse en ny besked. Formålet med sammenlægning af beskeder er at reducere advarsel "træthed" og lade dig fokusere og handle på færre vigtige beskeder.

### <a name="taking-action-on-alerts"></a>Handling på vigtige beskeder

Når en af dine politikker genererer en besked, kan du se de hændelser, der forårsagede beskeden, og afgøre, om du skal bekræfte eller undersøge hændelserne yderligere.

Hvis du vil udføre en handling på en besked, skal du vælge  rækken på siden Vigtige beskeder for at få vist pop op-panelet med oplysninger,  vælge knappen Handlinger og vælge mellem indstillinger, der er angivet nedenfor. Du kan også udføre handlinger ved at vælge den runde knap, der vises til venstre for beskedens navn, når du peger på dens række og vælge en af handlingsknapperne øverst på siden over filtrene.

**Tildel besked**: Det kan være en god ide at tildele beskeden til en bruger for at undersøge eller bekræfte de hændelser, der forårsagede beskeden. Når du vælger denne indstilling, åbnes et panel, hvor du kan vælge en bruger i organisationen og tildele beskeden til vedkommende. Du kan filtrere visningen af vigtige beskeder ved at vælge  Filtre på siden  Vigtige beskeder og skrive brugerens navn i **feltet Tildelt** til.

**Mailbesked**: Det kan være en ide at sende en mail til den bruger, der er knyttet til beskedens aktivitet, for at bekræfte, at brugeren har taget handlingen. Når du vælger denne indstilling, åbnes en mailskabelon med grundlæggende oplysninger om beskeden, som du kan tilpasse med yderligere instruktioner og sendes til brugeren.

**Vis oplysninger om** politik: Det kan være en ide at gennemgå indstillingerne for den politik, der udløste beskeden. Bemærk, at når du vælger denne indstilling, kommer du direkte til siden Beskedpolitikker, hvor detaljepanelet for politikken allerede er åbent. Du vil ikke længere være på siden **Vigtige beskeder** , når du lukker panelet med politikdetaljer.

**Ændre status**: Du kan opdatere status for din besked baseret på din gennemgang af dens virkning, og om der er behov for at undersøge den. Få mere at vide om beskedstatusser i næste afsnit.

### <a name="alert-status"></a>Beskedstatus

Når der oprettes en besked, er dens status **Aktiv**. Når du gennemgår oplysningerne for hver besked, kan du opdatere dens status til en af de tilstande, der er angivet nedenfor:

- **Aktiv**: Standardtilstanden for beskeden, indtil dens status ændres
- **Undersøgelse**: Undersøgelse af besked undersøges i øjeblikket
- **Løst**: Beskeden kræver ikke yderligere undersøgelse eller opfølgning
- **Afvist**: Beskeden er ikke relevant eller kræver ikke undersøgelse

Hvis du vil tildele eller ændre en beskeds status, skal du vælge en besked fra rækken i tabellen og vælge Skift **status** øverst på siden over filtrene. Vælg en status i rullemenuen i pop op-vinduet Opdater beskedstatus, og vælg derefter **Opdater besked**.

Når der genereres en besked, er dens status uafhængig af status for den politik, der genererede beskeden. Det er f.eks. muligt at have en aktiv besked, der er  knyttet til en inaktiv politik, og det er muligt  at have en undersøgelsesstatus på en besked, der blev genereret af en politik, der efterfølgende blev deaktiveret eller slettet.

### <a name="when-policies-are-deleted"></a>Når politikker slettes

Når en politik slettes, forbliver alle beskeder, der blev genereret af denne politik, på siden Vigtige  beskeder, men der genereres ingen nye beskeder.

## <a name="email-notifications-of-alerts"></a>Mailbeskeder om beskeder

Når du opretter en politik, sendes der en mail til den bruger, der oprettede politikken, der advarer vedkommende om, at der blev registreret et match. Du kan vælge at sende disse mailbeskeder til flere brugere i organisationen. Beskeder sker næsten i realtid, og mailmeddelelser sendes, så snart der genereres en besked. Mailen indeholder hændelsesnavnet, alvorsgrad, registreret tid og et link til at få vist beskeden i Overholdelsesstyring.

### <a name="remove-users-from-receiving-alerts"></a>Fjern brugere fra at modtage beskeder

Hvis du angiver beskedmodtagere og senere beslutter at fjerne dem, skal du følge trinnene nedenfor. Bemærk, at opretteren af politikken stadig vil modtage mailbeskeder, når der registreres politik match.

1. Begynd trinnene for at [redigere din politik](#edit-a-policy).
2. Når du når til **skærmbilledet Besked modtagere** , skal du **vælge + Vælg modtagere**.
3. I pop  op-panelet Vælg modtagere skal du finde den bruger, du vil fjerne fra meddelelser, og fjerne markeringen i afkrydsningsfeltet til venstre for deres navn og derefter vælge  knappen Tilføj modtagere (hvilket har den effekt, at du gemmer dit valg).
4. Fortsæt gennem guiden, og bekræft, at brugeren ikke vises under **Modtagere** på siden Gennemse og udfør. Vælg **Opdater** for at gemme dine indstillinger og afslutte.
