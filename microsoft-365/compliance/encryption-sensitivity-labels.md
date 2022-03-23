---
title: Begræns adgang til indhold ved hjælp af følsomhedsmærkater for at anvende kryptering
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Konfigurer følsomhedsmærkater til kryptering, der beskytter dine data ved at begrænse adgang og brug.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ac50568f9ce995f658e6b06c3a2b13b666211810
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63587495"
---
# <a name="restrict-access-to-content-by-using-sensitivity-labels-to-apply-encryption"></a>Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Når du opretter en følsomhedsmærkat, kan du begrænse adgangen til indhold, som etiketten vil blive anvendt på. Med krypteringsindstillingerne for en følsomhedsmærkat kan du f.eks. beskytte indhold, så:

- Kun brugere i din organisation kan åbne et fortroligt dokument eller en mail.
- Kun brugere i marketingafdelingen kan redigere og udskrive kampagnemeddelelsesdokumentet eller -mailen, mens alle andre brugere i organisationen kun kan læse den.
- Brugerne kan ikke videresende en mail eller kopiere oplysninger fra den, der indeholder nyheder om en intern omorganisering.
- Den aktuelle prisliste, der sendes til forretningspartnere, kan ikke åbnes efter en angivet dato.

Når et dokument eller en mail er krypteret, begrænses adgangen til indholdet, så det:

- Kan kun dekrypteres af brugere, der er godkendt af etikettens krypteringsindstillinger.
- Forbliver krypteret, uanset hvor den er placeret, i eller uden for din organisation, også selvom filen er omdøbt.
- Er krypteret både ved in rest (f.eks. i en OneDrive-konto) og under overførsel (f.eks. mail, når den krydser internettet).

Som administrator kan du, når du konfigurerer en følsomhedsmærkat til at anvende kryptering, vælge enten at:

- **Tildel tilladelser nu**, så du nøjagtigt bestemmer, hvilke brugere, der får hvilke tilladelser til indhold med den pågældende etiket.
- **Giv brugere tilladelse til at tildele** tilladelser, når de anvender etiketten på indhold. På den måde kan du give personer i organisationen fleksibilitet, som de kan få brug for til at samarbejde og få deres arbejde udført.

Krypteringsindstillingerne er tilgængelige, når [du opretter en følsomhedsmærkat](create-sensitivity-labels.md) i Microsoft 365 Overholdelsescenter. Du kan også bruge den ældre portal, Security & Compliance Center.

## <a name="understand-how-the-encryption-works"></a>Forstå, hvordan krypteringen fungerer

Kryptering anvender Azure Rights Management-tjenesten (Azure RMS) fra Azure Information Protection. Denne beskyttelsesløsning bruger krypterings-, identitets- og godkendelsespolitikker. Du kan få mere at vide [under Hvad er Azure Rights Management?](/azure/information-protection/what-is-azure-rms) fra Dokumentationen til Azure Information Protection. 

Når du bruger denne krypteringsløsning,  sikrer superbrugerfunktionen, at autoriserede personer og tjenester altid kan læse og undersøge de data, der er blevet krypteret for organisationen. Krypteringen kan om nødvendigt fjernes eller ændres. Få mere at vide under [Konfiguration af superbrugere til Azure Information Protection og Discovery-tjenester eller datagendannelse](/azure/information-protection/configure-super-users).

## <a name="important-prerequisites"></a>Vigtige forudsætninger

Før du kan bruge kryptering, skal du muligvis udføre nogle konfigurationsopgaver. Når du konfigurerer krypteringsindstillinger, er der ingen kontrol for at bekræfte, at disse forudsætninger er opfyldt.

- Aktivér beskyttelse fra Azure Information Protection
    
    For at følsomhedsmærkater kan anvende kryptering, skal beskyttelsestjenesten (Azure Rights Management) fra Azure Information Protection være aktiveret for din lejer. I nyere lejere er dette standardindstillingen, men det kan være nødvendigt at aktivere tjenesten manuelt. Du kan finde flere oplysninger [under Aktivering af beskyttelsestjeneste fra Azure Information Protection](/azure/information-protection/activate-service).

- Kontrollér for netværkskrav
    
    Du skal muligvis foretage nogle ændringer på dine netværksenheder, f.eks firewalls. Du kan finde flere [oplysninger i Firewalls og netværksinfrastruktur](/azure/information-protection/requirements#firewalls-and-network-infrastructure) fra Azure Information Protection-dokumentationen.

- Konfigurere Exchange Azure Information Protection
    
    Exchange behøver ikke at være konfigureret til Azure Information Protection, før brugerne kan anvende navne i Outlook at kryptere deres mails. Indtil du Exchange Azure Information Protection, får du dog ikke den fulde funktionalitet ved at bruge Azure Rights Management Protection med Exchange.
    
    Brugere kan f.eks. ikke se krypterede mails på mobiltelefoner eller med Outlook på internettet, krypterede mails kan ikke indekseres til søgning, og du kan ikke konfigurere Exchange Online DLP til Rights Management-beskyttelse. 
    
    Hvis du vil sikre Exchange du kan understøtte disse yderligere scenarier, skal du se følgende:
    
    - Du Exchange Online anvisninger for at Exchange Online[: IRM-konfiguration](/azure/information-protection/configure-office365#exchangeonline-irm-configuration).
    - For Exchange forbindelse i det lokale miljø skal du installere [RMS-forbindelsen og konfigurere Exchange serverne](/azure/information-protection/deploy-rms-connector). 

## <a name="how-to-configure-a-label-for-encryption"></a>Sådan konfigurerer du en etiket til kryptering

1. Følg de generelle instruktioner for [at oprette eller](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) redigere en følsomhedsmærkat, og sørg for, **at filer & mails** er markeret for etikettens omfang: 
    
    ![Indstillinger for følsomhedsmærkatens omfang for filer og mails.](../media/filesandemails-scope-options-sensitivity-label.png)

2. Derefter skal du på **siden Vælg beskyttelsesindstillinger for filer og mails sørge for** , at du vælger **Krypter filer og mails**
    
    ![Indstillinger for følsomhedsmærkatbeskyttelse til filer og mails.](../media/protection-options-sensitivity-label.png)

4.  På siden **Kryptering** skal du vælge en af følgende indstillinger:
    
    - **Fjern kryptering, hvis filen er krypteret**: Denne indstilling understøttes kun af den samlede Azure Information Protection-etiketklient. Når du vælger denne indstilling og bruger indbygget mærkning, vises navnet muligvis ikke i apps eller vises, og der foretages ikke nogen krypteringsændringer.
        
        Du kan finde flere oplysninger om dette scenarie [i afsnittet Hvad sker](#what-happens-to-existing-encryption-when-a-labels-applied) der med eksisterende kryptering, når en etiket anvendes. Det er vigtigt at forstå, at denne indstilling kan resultere i en følsomhedsmærkat, som brugerne muligvis ikke kan anvende, når de ikke har de nødvendige tilladelser.
    
    - **Konfigurer krypteringsindstillinger**: Aktiverer kryptering og gør krypteringsindstillingerne synlige:
        
        ![Indstillinger for følsomhedsmærkat for kryptering.](../media/encrytion-options-sensitivity-label.png)
        
        Vejledning til disse indstillinger findes i afsnittet [Konfigurer krypteringsindstillinger](#configure-encryption-settings) .

### <a name="what-happens-to-existing-encryption-when-a-labels-applied"></a>Hvad sker der med eksisterende kryptering, når en etiket anvendes

Hvis der anvendes en følsomhedsmærkat på ikke-krypteret indhold, er resultatet af de krypteringsindstillinger, du kan vælge, selvforklarende. Hvis du f.eks. ikke har valgt **Kryptér filer og** mails, forbliver indholdet ukrypteret.

Indholdet kan dog allerede være krypteret. En anden bruger kunne f.eks. have anvendt:

- Deres egne tilladelser, som omfatter brugerdefinerede tilladelser, når du bliver bedt om det af en etiket, brugerdefinerede tilladelser af Azure Information Protection-klienten og  begrænset adgang-dokumentbeskyttelse fra en Office-app.
- En Azure Rights Management-beskyttelsesskabelon, der krypterer indholdet uafhængigt af en etiket. Denne kategori omfatter regler for mailflow, der anvender kryptering ved hjælp af rettighedsbeskyttelse.
- En etiket, der anvender kryptering, med tilladelser, der er tildelt af administratoren.

I følgende tabel kan du se, hvad der sker med eksisterende kryptering, når der anvendes en følsomhedsmærkat på indholdet:

| | Kryptering: Ikke markeret | Kryptering: Konfigureret | Kryptering: Fjern <sup>\*</sup> |
|:-----|:-----|:-----|:-----|
|**Tilladelser, der er angivet af en bruger**|Oprindelig kryptering bevares|Ny etiketkryptering anvendes|Oprindelig kryptering fjernes|
|**Skabelon til beskyttelse**|Oprindelig kryptering bevares|Ny etiketkryptering anvendes|Oprindelig kryptering fjernes|
|**Navn med administratordefinerede tilladelser**|Oprindelig kryptering fjernes|Ny etiketkryptering anvendes|Oprindelig kryptering fjernes|

**Fodnote:**

<sup>\*</sup> Understøttes kun af den samlede Azure Information Protection-etiketklient

I de tilfælde, hvor den nye etiketkryptering anvendes, eller den oprindelige kryptering fjernes, sker dette kun, hvis den bruger, der anvender etiketten, har en brugs- eller rolle, der understøtter denne handling:

- [Brugs højre](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Eksportér eller Fuld kontrol.
- Rollen som [rettighedsstyringsudsteder eller ejer af Rights Management](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) eller [superbruger](/azure/information-protection/configure-super-users).

Hvis brugeren ikke har en af disse rettigheder eller roller, kan navnet ikke anvendes, så den oprindelige kryptering bevares. Brugeren får vist følgende meddelelse: Du **har ikke tilladelse til at foretage denne ændring i følsomhedsmærkatet. Kontakt ejeren af indholdet.**

Den person, der anvender Videressendelse til en mail, kan f.eks. genmærke tråden for at erstatte krypteringen eller fjerne den, fordi vedkommende er Rights Management-ejeren af mailen. Men med undtagelse af superbrugere kan modtagerne af denne mail ikke give den et navn, fordi de ikke har de nødvendige brugsrettigheder.

#### <a name="email-attachments-for-encrypted-email-messages"></a>Vedhæftede filer i mails til krypterede mails

Når en mail krypteres på enhver måde, arver alle ikke-krypterede Office dokumenter, der er vedhæftet mailen, automatisk de samme krypteringsindstillinger.

Dokumenter, der allerede er krypteret og derefter tilføjet som vedhæftede filer, bevarer altid deres oprindelige kryptering.

## <a name="configure-encryption-settings"></a>Konfigurere krypteringsindstillinger

Når du vælger **Konfigurer krypteringsindstillinger** på siden **Kryptering** for at oprette eller redigere en følsomhedsmærkat, skal du vælge en af følgende indstillinger:

- **Tildel tilladelser nu**, så du kan bestemme, præcist hvilke brugere, der får hvilke tilladelser til indhold, der får etiketten anvendt. Du kan finde flere oplysninger i næste afsnit [Tildel tilladelser nu](#assign-permissions-now).
- **Giv brugere tilladelse til at tildele** tilladelser, når brugerne anvender etiketten på indhold. Med denne indstilling kan du give personer i organisationen fleksibilitet, som de kan få brug for til at samarbejde og få deres arbejde udført. Du kan finde flere oplysninger i [afsnittet Lad brugere tildele tilladelser](#let-users-assign-permissions) på denne side.

Hvis du f.eks. har en følsomhedsmærkat med navnet Meget fortroligt, der vil blive anvendt på dit mest følsomme indhold, vil du måske beslutte, hvem der nu får hvilke typer tilladelser til indholdet.

Alternativt kan du, hvis du har en følsomhedsmærkat med navnet **Forretningskontrakter**, og din organisations arbejdsproces kræver, at dine personer samarbejder om dette indhold med forskellige personer på ad hoc-basis, give dine brugere mulighed for at beslutte, hvem der får tilladelser, når de tildeler etiketten. Denne fleksibilitet hjælper både dine brugeres produktivitet og reducerer anmodningerne om, at dine administratorer opdaterer eller opretter nye følsomhedsmærkater for at håndtere bestemte scenarier.

Vælg, om du vil tildele tilladelser nu eller lade brugere tildele tilladelser:

![Mulighed for at tilføje bruger- eller administrator definerede tilladelser.](../media/sensitivity-label-user-or-admin-defined-permissions.png)

## <a name="assign-permissions-now"></a>Tildel tilladelser nu

Brug følgende indstillinger til at styre, hvem der kan få adgang til mails eller dokumenter, som denne etiket anvendes på. Du kan:

- **Tillad adgang til mærket indhold for at** udløbe, enten på en bestemt dato eller efter et bestemt antal dage, efter etiketten er anvendt. Efter dette tidspunkt kan brugerne ikke åbne det mærkede element. Hvis du angiver en dato, anvendes midnat på den pågældende dato i den aktuelle tidszone. Bemærk, at nogle mailklienter muligvis ikke gennemtvinger udløb og viser mails, der er over udløbsdatoen på grund af deres cachelagringsmekanismer.

- **Tillad offlineadgang** aldrig, altid eller i et bestemt antal dage, efter at etiketten er anvendt. Hvis du begrænser offlineadgang til aldrig eller et antal dage, når denne grænse nås, skal brugerne genauthenticeres, og deres adgang logføres. Du kan finde flere oplysninger i næste afsnit om Rights Management Use License.

Indstillinger adgangskontrol for krypteret indhold:

![Indstillinger for administrator definerede tilladelser.](../media/sensitivity-encryption-settings-for-admin-defined-permissions.png)

### <a name="rights-management-use-license-for-offline-access"></a>Brugslicens til Rettighedsstyring til offlineadgang

Når en bruger åbner et dokument eller en mail, der er blevet beskyttet med kryptering fra Azure Rights Management-tjenesten, tildeles brugeren en licens til brug af Azure Rights Management for det pågældende indhold. Denne brugslicens er et certifikat, der indeholder brugerens brugsrettigheder til dokumentet eller mailen, og den krypteringsnøgle, der blev brugt til at kryptere indholdet. Brugslicensen indeholder også en udløbsdato, hvis den er blevet angivet, og hvor lang tid brugslicensen er gyldig.

Hvis der ikke er angivet en udløbsdato, er standardbrugslicensens gyldighedsperiode for en lejer 30 dage. Under hele brugslicensens varighed bliver brugeren ikke genauthetated eller uautoriseret for indholdet. Denne proces gør det muligt for brugeren fortsat at åbne det beskyttede dokument eller den beskyttede mail uden en internetforbindelse. Når anvendelseslicensens gyldighedsperiode udløber, næste gang brugeren får adgang til det beskyttede dokument eller den beskyttede mail, skal brugeren genautateres og uautoriseret.

Ud over genautentiation genautificeres krypteringsindstillingerne og brugergruppemedlemskabet igen. Det betyder, at brugerne kan opleve forskellige adgangsresultater for det samme dokument eller den samme mail, hvis der er ændringer i krypteringsindstillingerne eller gruppemedlemskabet, fra da de sidst fik adgang til indholdet.

Hvis du vil have mere at vide om, hvordan du ændrer standardindstillingen for 30 dage, skal du [se Licens til brug af Rights Management](/azure/information-protection/configure-usage-rights#rights-management-use-license).

### <a name="assign-permissions-to-specific-users-or-groups"></a>Tildele tilladelser til bestemte brugere eller grupper

Du kan give tilladelser til bestemte personer, så kun de kan interagere med det mærkede indhold:

1. Først skal du tilføje brugere eller grupper, der får tildelt tilladelser til det mærkede indhold.

2. Vælg derefter, hvilke tilladelser disse brugere skal have for det mærkede indhold.

Tildeling af tilladelser:

![Indstillinger for tildeling af tilladelser til brugere.](../media/Sensitivity-Assign-permissions-settings.png)

#### <a name="add-users-or-groups"></a>Tilføj brugere eller grupper

Når du tildeler tilladelser, kan du vælge:

- Alle i din organisation (alle lejermedlemmer). Denne indstilling udelader gæstekonti.

- Alle godkendte brugere. Sørg for, at du [forstår kravene og begrænsningerne](#requirements-and-limitations-for-add-any-authenticated-users) ved denne indstilling, før du vælger den.

- En bestemt bruger- eller mailaktiveret sikkerhedsgruppe, distributionsgruppe eller Microsoft 365 gruppe ([tidligere Office 365 gruppe](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) i Azure AD. Den Microsoft 365 gruppe kan have statisk eller [dynamisk medlemskab](/azure/active-directory/users-groups-roles/groups-create-rule). Bemærk, at du ikke kan bruge en dynamisk [distributionsgruppe fra Exchange](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups), fordi denne gruppetype ikke er synkroniseret med Azure AD, og du kan ikke bruge en sikkerhedsgruppe, der ikke er mailaktiveret.
    
    Inden for en bestemt gruppe, der understøttes af denne indstilling, [](/azure/information-protection/prepare#azure-information-protection-requirements-for-user-accounts) godkendes hver enkelt bruger enkeltvis af Azure Information Protection-tjenesten, før de kan åbne det krypterede indhold.

- En mailadresse eller et domæne. Brug denne indstilling til at angive alle brugere i en anden organisation, der bruger Azure AD, ved at indtaste et domænenavn fra den pågældende organisation. Du kan også bruge denne indstilling til sociale udbydere ved at indtaste deres domænenavn, f.eks **. gmail.com**, **hotmail.com** eller **outlook.com**.

    > [!NOTE]
    > Hvis du angiver et domæne fra en organisation, der bruger Azure AD, kan du ikke begrænse adgangen til det pågældende domæne. I stedet medtages alle bekræftede domæner i Azure AD automatisk for den lejer, der ejer det domænenavn, du angiver.

Når du vælger alle brugere og grupper i organisationen eller gennemser kataloget, skal brugerne eller grupperne have en mailadresse.

Som bedste fremgangsmåde skal du bruge grupper i stedet for brugere. Denne strategi holder din konfiguration enklere.

##### <a name="requirements-and-limitations-for-add-any-authenticated-users"></a>Krav og begrænsninger for "Tilføj eventuelle godkendte brugere"

Denne indstilling begrænser ikke, hvem der kan få adgang til indholdet, som etiketten krypterer, mens indholdet stadig krypteres, og giver dig mulighed for at begrænse, hvordan indholdet kan bruges (tilladelser) og åbnes (udløbsdato og offlineadgang). Men det program, der åbner det krypterede indhold, skal kunne understøtte den godkendelse, der bruges. Derfor fungerer de sociale udbydere i organisationsnetværket, f.eks. Google, og godkendelse af engangskoder kun for mails, og kun når du bruger Exchange Online. Microsoft-konti kan bruges sammen Office 365 apps og [Azure Information Protection-fremviseren](https://portal.azurerms.com/#/download).

> [!NOTE]
> Overvej at bruge denne [indstilling med SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview), når følsomhedsetiketter er [aktiveret til Office-filer SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Nogle typiske scenarier for alle godkendte brugeres indstillinger:

- Du har ikke noget imod, hvem der får visning af indholdet, men du vil begrænse den måde, det bruges på. Du ønsker f.eks. ikke, at indholdet skal redigeres, kopieres eller udskrives.
- Du behøver ikke at begrænse, hvem der har adgang til indholdet, men du vil kunne bekræfte, hvem der åbner indholdet.
- Du har et krav om, at indholdet skal krypteres ved in rest- og overførsel, men det kræver ikke adgangskontrolelementer.

#### <a name="choose-permissions"></a>Vælg tilladelser

Når du vælger, hvilke tilladelser der skal tillades for disse brugere eller grupper, kan du vælge enten:

- Et [foruddefineret tilladelsesniveau med en foruddefineret](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels) gruppe af rettigheder, f.eks. Co-Author eller Korrekturlæser.
- Brugerdefinerede tilladelser, hvor du vælger en eller flere brugsrettigheder.

Du kan finde flere oplysninger, der kan hjælpe dig med at vælge de relevante tilladelser, [under Brugsrettigheder og beskrivelser](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions).  

![Indstillinger til at vælge forudindstillede eller brugerdefinerede tilladelser.](../media/Sensitivity-Choose-permissions-settings.png)

Bemærk, at den samme etiket kan give forskellige tilladelser til forskellige brugere. Eksempelvis kan et enkelt navn tildele nogle brugere som Korrekturlæser og en anden bruger som Medforfatter, som vist på følgende skærmbillede.

Det gør du ved at tilføje brugere eller grupper, tildele dem tilladelser og gemme disse indstillinger. Gentag derefter disse trin, og tilføj brugere og tildel dem tilladelser, og spar indstillingerne hver gang. Du kan gentage denne konfiguration så ofte, som det er nødvendigt, for at definere forskellige tilladelser for forskellige brugere.

![Forskellige brugere med forskellige tilladelser.](../media/Sensitivity-Multiple-users-permissions.png)

#### <a name="rights-management-issuer-user-applying-the-sensitivity-label-always-has-full-control"></a>Rettighedsstyringsudsteder (bruger, der anvender følsomhedsmærkaten) har altid fuld kontrol

Kryptering til et følsomhedsmærkat anvender Azure Rights Management-tjenesten fra Azure Information Protection. Når en bruger anvender et følsomhedsmærkat for at beskytte et dokument eller en mail ved hjælp af kryptering, bliver den pågældende bruger Rettighedsadministrationsudsteder for det pågældende indhold.

Rettighedsstyringsudstederen tildeles altid tilladelsen Fuld kontrol for dokumentet eller mailen samt:

- Hvis krypteringsindstillingerne omfatter en udløbsdato, kan udstederen af Rights Management stadig åbne og redigere dokumentet eller mailen efter denne dato.
- Rettighedsstyringsudstederen kan altid få adgang til dokumentet eller mailen offline.
- Rettighedsstyringsudstederen kan stadig åbne et dokument, efter det er blevet tilbagekaldt.

Du kan finde flere oplysninger [i Rights Management-udsteder og ejer af Rights Management](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

### <a name="double-key-encryption"></a>Kryptering med dobbelt nøgle

> [!NOTE]
> Denne funktion understøttes i øjeblikket kun af Azure Information Protection Unified Labeling Client.

Vælg kun denne indstilling, når du har konfigureret tjenesten Dobbelt nøglekryptering, og du skal bruge denne kryptering med dobbelt nøgle til filer, hvor denne etiket vil blive anvendt. Når etiketten er konfigureret og gemt, kan du ikke redigere den.

Du kan finde flere oplysninger, forudsætninger og konfigurationsinstruktioner [under Dobbelt nøglekryptering (DKE)](double-key-encryption.md).

## <a name="let-users-assign-permissions"></a>Lad brugere tildele tilladelser

> [!IMPORTANT]
> Ikke alle etiketklienter understøtter alle de indstillinger, der giver brugerne mulighed for at tildele deres egne tilladelser. Brug dette afsnit for at få mere at vide.

Du kan bruge følgende indstillinger til at give brugere tilladelse til at tildele tilladelser, når de manuelt anvender en følsomhedsmærkat på indhold:

- I Outlook kan en bruger vælge begrænsninger, der svarer til indstillingen [Videresende ikke](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails) eller [Kryptér kun](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails) for de valgte modtagere.
    
    Indstillingen Videresvarer ikke understøttes af alle mailklienter, der understøtter følsomhedsmærkater. Men anvendelsen af indstillingen  Krypteringsbeskyttelse med en følsomhedsmærkat er en nyere version, der kun understøttes af indbygget mærkning og ikke den samlede Azure Information Protection-etiketklient. For mailklienter, der ikke understøtter denne funktion, er navnet ikke synligt.
    
    For at kontrollere minimumversionerne af Outlook-apps, der bruger indbygget mærkning til at understøtte brugen af Encrypt-Only-indstillingen med en **følsomhedsmærkat**, skal du bruge tabellen med egenskaber [for Outlook](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-outlook) og rækken Lad brugere tildele tilladelser: - Kun krypteret.

- I Word, PowerPoint og Excel bliver en bruger bedt om at vælge sine egne tilladelser til bestemte brugere, grupper eller organisationer.

    Denne indstilling understøttes af den samlede Azure Information Protection-etiketklient og nogle apps, der bruger indbygget mærkning. For apps, der ikke understøtter denne funktion, vil etiketten enten ikke være synlig for brugere, eller etiketten er synlig for ensartethed, men den kan ikke anvendes med en forklaringsmeddelelse til brugerne.
    
    Hvis du vil kontrollere, hvilke apps der bruger indbygget mærkning, der understøtter denne indstilling, skal du bruge tabellen med egenskaber [for Word, Excel og PowerPoint](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) og rækken Lad brugere tildele tilladelser **: - Spørg** brugerne.

Når indstillingerne understøttes, skal du bruge følgende tabel til at identificere, hvornår brugere kan se følsomhedsmærkaten:

|Indstilling |Navn synligt i Outlook|Etiket synlig i Word, Excel, PowerPoint|
|:-----|:-----|:-----|:-----|
|**Du Outlook begrænsninger med indstillingen Videresig ikke eller Encrypt-Only.**|Ja |Nej |
|**I Word, PowerPoint og Excel skal du bede brugerne om at angive tilladelser**|Nej |Ja|

Når begge indstillinger er markeret, er navnet derfor synligt både i Outlook og i Word, Excel og PowerPoint.

Et følsomhedsmærkat, der giver brugere mulighed for at tildele tilladelser, skal anvendes på indhold manuelt af brugerne; den kan ikke anvendes automatisk eller bruges som en anbefalet etiket.

Konfiguration af bruger tildelte tilladelser:

![Krypteringsindstillinger for brugerdefinerede tilladelser.](../media/sensitivity-encryption-settings-for-user-defined-permissions.png)

### <a name="outlook-restrictions"></a>Outlook begrænsninger

Når Outlook en bruger anvender en følsomhedsmærkat, der giver brugeren mulighed for at tildele tilladelser til en meddelelse, kan du vælge indstillingen  Videresende ikke eller **Kryptér kun**. Brugeren får vist etikettens navn og beskrivelse øverst i meddelelsen, som angiver, at indholdet er beskyttet. I modsætning PowerPoint Word, Excel brugere (se næste [afsnit), bliver](#word-powerpoint-and-excel-permissions) brugerne ikke bedt om at vælge bestemte tilladelser.

![Følsomhedsmærkat anvendt på meddelelse i Outlook.](../media/sensitivity-label-outlook-protection-applied.png)

Når en af disse indstillinger anvendes på en mail, krypteres mailen, og modtagerne skal godkendes. Derefter har modtagerne automatisk begrænsede brugsrettigheder:

- **Undlad at videresende**: Modtagerne kan ikke videresende mailen, udskrive den eller kopiere fra den. I Outlook-klienten er knappen Videressendelse f.eks. ikke tilgængelig, menuindstillingerne Gem som og Udskriv er ikke tilgængelige, og du kan ikke tilføje eller ændre modtagere i felterne Til, Cc eller Bcc.
    
    Du kan finde flere oplysninger om, hvordan denne indstilling fungerer, [under Indstillingen Videressendelse ikke for mails](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails).

- **Kun krypteret**: Modtagerne har alle brugsrettigheder undtagen Gem som, Eksportér og Fuld kontrol. Denne kombination af brugsrettigheder betyder, at modtagerne ikke har nogen begrænsninger, bortset fra at de ikke kan fjerne beskyttelsen. Eksempelvis kan en modtager kopiere fra mailen, udskrive den og videresende den.
    
    Du kan finde flere oplysninger om, hvordan denne indstilling fungerer, [under Krypteringsindstilling for mails](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails).

Ikke-krypterede dokumenter Office der er vedhæftet mailen, arver automatisk de samme begrænsninger. For Videres end ikke er de brugsrettigheder, der gælder for disse dokumenter, Rediger indhold, Rediger; Gem; Vis, Åbn, Læs; og Tillad makroer. Hvis brugeren ønsker forskellige brugerrettigheder til en vedhæftet fil, eller hvis den vedhæftede fil ikke er et Office-dokument, der understøtter denne nedarvede beskyttelse, skal brugeren kryptere filen, før den vedhæftes mailen.

### <a name="word-powerpoint-and-excel-permissions"></a>Word-, PowerPoint- Excel-tilladelser

Når en bruger i Word, PowerPoint og Excel anvender en følsomhedsmærkat, der giver brugeren mulighed for at tildele tilladelser til et dokument, bliver brugeren bedt om at angive sit valg af brugere og tilladelser, når krypteringen anvendes.

Med Azure Information Protection samlet etiketklient, medmindre samtidig redigering er [aktiveret](sensitivity-labels-coauthoring.md), kan brugerne f.eks.:

- Vælg et tilladelsesniveau, f.eks. Viewer (der tildeler tilladelsen Kun visning) eller Co-Author (som tildeler tilladelserne Vis, Rediger, Kopiér og Udskriv).
- Vælg brugere, grupper eller organisationer. Dette kan omfatte personer både i og uden for din organisation.
- Angiv en udløbsdato, hvorefter de valgte brugere ikke kan få adgang til indholdet. Du kan finde flere oplysninger i ovenstående afsnit [Rights Management-brugslicens til offlineadgang](#rights-management-use-license-for-offline-access).

![Indstillinger, som brugerne kan beskytte med brugerdefinerede tilladelser.](../media/sensitivity-aip-custom-permissions-dialog.png)

For indbygget mærkning og for den samlede Azure Information [Protection-etiketklient](sensitivity-labels-coauthoring.md), når samtidig redigering er aktiveret, får brugerne vist den samme dialogboks, som hvis de valgte følgende:

- Windows: **Fanen** Filer > **InfoProtect** >  **DocumentRestrict** >  **AccessRestricted** >  Access

- macOS: **Fanen** Gennemse > **ProtectionPermissionsRestricted** >  >  **Access**

> [!TIP]
> Hvis brugerne var bekendte med konfiguration af brugerdefinerede tilladelser med Azure Information Protection-klienten til samlet [mærkning, før](sensitivity-labels-coauthoring.md) samtidig redigering blev aktiveret, kan det være nyttigt at gennemgå tilknytningen af tilladelsesniveauer til individuelle brugerrettigheder: Rettigheder inkluderet i [tilladelsesniveauer](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels).

## <a name="example-configurations-for-the-encryption-settings"></a>Eksempelkonfigurationer af krypteringsindstillingerne

For hvert eksempel, der følger, skal du udføre konfigurationen fra **siden Kryptering** , når **Konfigurer krypteringsindstillinger** er valgt:

![Anvend krypteringsindstillingen i guiden til følsomhedsmærkater.](../media/apply-encryption-option.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-an-encrypted-email-to-a-gmail-account"></a>Eksempel 1: Etiket, der gælder Videressendelse for at sende en krypteret mail til en Gmail-konto

Denne etiket vises kun i Outlook og Outlook på internettet, og du skal bruge Exchange Online. Bed brugerne om at vælge denne etiket, når de skal sende en krypteret mail til personer, der bruger en Gmail-konto (eller en anden mailkonto uden for organisationen).

Dine brugere skriver Gmail-mailadressen i **feltet** Til.  Derefter vælger de etiketten, og indstillingen Videressendelse føjes automatisk til mailen. Resultatet er, at modtagerne ikke kan videresende eller udskrive mailen, kopiere fra den eller gemme mailen uden for deres postkasse ved hjælp af **indstillingen Gem** som.

1. På siden **Kryptering** : **Tildel tilladelser nu, eller** lad brugerne beslutte det? Vælg Lad brugere tildele **tilladelser, når de anvender etiketten**.

2. Markér afkrydsningsfeltet: Du **kan Outlook begrænsninger, der svarer til indstillingen Videresig ikke**.

3. Hvis dette er markeret, skal du fjerne markeringen i **afkrydsningsfeltet: PowerPoint brugere Excel at angive tilladelser i Word**.

4. Vælg **Næste** , og fuldfør konfigurationen.

### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization"></a>Eksempel 2: Etiket, der begrænser skrivebeskyttet tilladelse til alle brugere i en anden organisation

Denne etiket er egnet til at dele meget følsomme dokumenter som skrivebeskyttede, og dokumenterne kræver altid en internetforbindelse for at få dem vist.

Denne etiket er ikke egnet til mails.

1. På siden **Kryptering** : **Tildel tilladelser nu, eller lad brugere beslutte? vælg** **Tildel tilladelser nu**.

2. For **Tillad offlineadgang skal** du vælge **Aldrig**.

3. Vælg **Tildel tilladelser**.

4. I **ruden Tildel** tilladelser skal du **vælge Tilføj bestemte mailadresser eller domæner**.

5. Skriv navnet på et domæne fra den anden organisation i tekstfeltet, f.eks **. fabrikam.com**. Vælg derefter **Tilføj**.

6. Vælg **Vælg tilladelser**.

7. I **ruden Vælg tilladelser** skal du vælge rullelisten, vælge **Seer** og derefter vælge **Gem**.

8. Tilbage i **ruden Tildel tilladelser** skal du vælge **Gem**.

9. På siden **Kryptering** skal du vælge **Næste** og fuldføre konfigurationen.

### <a name="example-3-add-external-users-to-an-existing-label-that-encrypts-content"></a>Eksempel 3: Føj eksterne brugere til en eksisterende etiket, der krypterer indhold

De nye brugere, du tilføjer, vil kunne åbne dokumenter og mails, der allerede er beskyttet med denne etiket. De tilladelser, du giver disse brugere, kan være forskellige fra de tilladelser, som de eksisterende brugere har.

1. På siden **Kryptering** : Tildel **tilladelser nu, eller lad brugerne beslutte?** Sørg for **, at Tildel tilladelser nu** er markeret.

2. Vælg **Tildel tilladelser**.

3. I **ruden Tildel** tilladelser skal du **vælge Tilføj bestemte mailadresser eller domæner**.

4. Skriv mailadressen på den første bruger (eller gruppe), der skal tilføjes, i tekstfeltet, og vælg derefter **Tilføj**.

5. Vælg **Vælg tilladelser**.

6. I **ruden Vælg tilladelser** skal du vælge tilladelserne for denne bruger (eller gruppe) og derefter vælge **Gem**.

7. Tilbage i **ruden Tildel** tilladelser skal du gentage trin 3 til 6 for hver bruger (eller gruppe), du vil føje til denne etiket. Klik derefter på **Gem**.

8. På siden **Kryptering** skal du vælge **Næste** og fuldføre konfigurationen.

### <a name="example-4-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Eksempel 4: Etiket, der krypterer indhold, men ikke begrænser, hvem der kan få adgang til det

Denne konfiguration har den fordel, at du ikke behøver at angive brugere, grupper eller domæner for at kryptere en mail eller et dokument. Indholdet vil stadig være krypteret, og du kan stadig angive brugsrettigheder, en udløbsdato og offlineadgang.

Brug kun denne konfiguration, når du ikke har brug for at begrænse, hvem der kan åbne det beskyttede dokument eller den beskyttede mail. [Flere oplysninger om denne indstilling](#requirements-and-limitations-for-add-any-authenticated-users)

1. På siden **Kryptering** : Tildel **tilladelser nu, eller lad brugerne beslutte?** Sørg for **, at Tildel tilladelser nu** er markeret.

2. Konfigurer indstillingerne for **Brugeradgang til indhold udløber og Tillad** **offlineadgang efter** behov.

3. Vælg **Tildel tilladelser**.

4. I **ruden Tildel** tilladelser skal du **vælge Tilføj alle godkendte brugere**.

    For **Brugere og grupper** kan du se **Godkendte brugere, der er** tilføjet automatisk. Du kan ikke ændre denne værdi, kun slette den, hvilket annullerer **markeringen Tilføj eventuelle godkendte** brugere.

5. Vælg **Vælg tilladelser**.

6. I **ruden Vælg** tilladelser skal du vælge rullelisten, vælge de ønskede tilladelser og derefter vælge **Gem**.

7. Tilbage i **ruden Tildel tilladelser** skal du vælge **Gem**.

8. På siden **Kryptering** skal du vælge **Næste** og fuldføre konfigurationen.

## <a name="considerations-for-encrypted-content"></a>Overvejelser i forbindelse med krypteret indhold

Kryptering af dine mest følsomme dokumenter og mails hjælper med at sikre, at kun autoriserede personer kan få adgang til disse data. Der er dog nogle overvejelser at tage højde for:

- Hvis din organisation ikke har [aktiveret følsomhedsmærkater for Office i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

  - Søgning, eDiscovery og Delve fungerer ikke for krypterede filer.
  - DLP-politikker fungerer for metadataene fra disse krypterede filer (herunder oplysninger om opbevaringsetiket), men ikke indholdet af disse filer (f.eks. kreditkortnumre i filer).
  - Brugere kan ikke åbne krypterede filer ved hjælp af Office på internettet. Når følsomhedsetiketter til Office-filer i SharePoint og OneDrive er aktiveret, kan brugerne bruge Office på internettet til at åbne krypterede filer med visse begrænsninger, der omfatter kryptering, der [](sensitivity-labels-sharepoint-onedrive-files.md#limitations) er blevet anvendt med en lokal nøgle (kaldet "hold din egen nøgle" eller HYOK), dobbelt [nøglekryptering](#double-key-encryption) og kryptering, der er anvendt uafhængigt af en følsomhedsmærkat.

- Hvis du deler krypterede dokumenter med personer uden for organisationen, kan det være nødvendigt at oprette gæstekonti og redigere politikker for betinget adgang. Du kan få mere at vide [under Dele krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Når autoriserede brugere åbner krypterede dokumenter i deres Office-apps, kan de se etiketnavnet og beskrivelsen i en gul meddelelseslinje øverst i deres app. Når krypteringstilladelserne gælder for personer uden for organisationen, skal du nøje gennemse navne og beskrivelser, der vil være synlige på denne meddelelseslinje, når dokumentet åbnes.

- Hvis flere brugere skal kunne redigere en krypteret fil på samme tid, skal de alle bruge Office på internettet, eller du har aktiveret samtidig redigering for filer, der er krypteret med følsomhedsmærkater, og alle brugere har [Office-apps](sensitivity-labels-coauthoring.md), der understøtter denne funktion.[](sensitivity-labels-coauthoring.md#prerequisites) Hvis dette ikke er tilfældet, og filen allerede er åben:

  - I Office apps (Windows, Mac, Android og iOS) får brugerne vist meddelelsen Filer i brug med navnet på  den person, der har tjekket filen ud. De kan derefter få vist en skrivebeskyttet kopi eller gemme og redigere en kopi af filen og modtage en meddelelse, når filen er tilgængelig.
  - I Office på internettet får brugerne vist en fejlmeddelelse om, at de ikke kan redigere dokumentet med andre personer. De kan derefter vælge **Åbn i læsevisning**.

- Funktionen [Automatisk lagring i](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) apps Office iOS og Android er deaktiveret for krypterede filer. Denne funktion er også deaktiveret for krypterede filer på Windows og Mac, hvis du ikke har aktiveret samtidig redigering for filer, der er krypteret [med følsomhedsmærkater](sensitivity-labels-coauthoring.md). Brugere får vist en meddelelse om, at filen har begrænsede tilladelser, der skal fjernes, før automatisk lagring kan slås til.

- Det kan tage længere tid at åbne krypterede filer i Office (Windows, Mac, Android og iOS).

- Hvis der tilføjes en etiket, der anvender kryptering, ved hjælp af en Office-app når dokumentet tjekkes ud i [SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de), og brugeren derefter kasserer udtjekningen, forbliver dokumentet mærket og krypteret.

- Medmindre du har aktiveret samtidig redigering for filer, der er krypteret med følsomhedsmærkater, understøttes følgende handlinger for krypterede filer ikke fra [Office-apps](sensitivity-labels-coauthoring.md) (Windows, Mac, Android og iOS), og brugerne får vist en fejlmeddelelse om, at noget er gået galt. Funktioner i SharePoint kan dog bruges som et alternativ:

  - Få vist, gendan og gem kopier af tidligere versioner. Som alternativ kan brugerne udføre disse handlinger ved hjælp af Office på internettet når du [aktiverer og konfigurerer versionsversioner for en liste eller et bibliotek](https://support.office.com/article/enable-and-configure-versioning-for-a-list-or-library-1555d642-23ee-446a-990a-bcab618c7a37).
  - Rediger navnet på eller placeringen af filer. Som alternativ kan brugerne omdøbe [en fil, mappe eller et link i et dokumentbibliotek i](https://support.microsoft.com/office/rename-a-file-folder-or-link-in-a-document-library-bc493c1a-921f-4bc1-a7f6-985ce11bb185) SharePoint.

For at få den bedste samarbejdsoplevelse til filer, der er krypteret med en følsomhedsmærkat, anbefaler vi, at du bruger følsomhedsmærkater til [Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) og Office på internettet.



## <a name="next-steps"></a>Næste trin

Har du brug for at dele dine mærkede og krypterede dokumenter med personer uden for organisationen?  Se [Dele krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
