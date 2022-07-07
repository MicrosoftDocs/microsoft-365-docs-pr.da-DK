---
title: Anvend kryptering ved hjælp af følsomhedsmærkater
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
ms.openlocfilehash: ef00ca10ca932322e51d71449e42f45842ce4c97
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663786"
---
# <a name="restrict-access-to-content-by-using-sensitivity-labels-to-apply-encryption"></a>Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Når du opretter en følsomhedsmærkat, kan du begrænse adgangen til indhold, som mærkaten anvendes på. Med krypteringsindstillingerne for en følsomhedsmærkat kan du f.eks. beskytte indhold, så:

- Det er kun brugere i organisationen, der kan åbne et fortroligt dokument eller en fortrolig mail.
- Det er kun brugere i marketingafdelingen, der kan redigere og udskrive annoncedokumentet eller mailen, mens alle andre brugere i organisationen kun kan læse det.
- Brugerne kan ikke videresende en mail eller kopiere oplysninger fra den, der indeholder nyheder om en intern omorganisering.
- Den aktuelle prisliste, der sendes til forretningspartnere, kan ikke åbnes efter en angivet dato.

Når et dokument eller en mail er krypteret, er adgangen til indholdet begrænset, så det:

- Kan kun dekrypteres af brugere, der er godkendt af mærkatens krypteringsindstillinger.
- Forbliver krypteret, uanset hvor den er placeret, i eller uden for din organisation, selvom filen omdøbes.
- Krypteres både inaktivt (f.eks. på en OneDrive-konto) og under overførsel (f.eks. mail, når den gennemgår internettet).

Når du som administrator konfigurerer en følsomhedsmærkat til at anvende kryptering, kan du til sidst vælge en af følgende:

- **Tildel tilladelser nu**, så du kan bestemme præcis, hvilke brugere der får hvilke tilladelser til indhold med den pågældende mærkat.
- **Lad brugerne tildele tilladelser** , når de anvender mærkaten på indhold. På denne måde kan du give personer i din organisation en vis fleksibilitet, som de muligvis har brug for til at samarbejde og få udført deres arbejde.

Krypteringsindstillingerne er tilgængelige, når du [opretter en følsomhedsmærkat](create-sensitivity-labels.md) i Microsoft Purview-compliance-portal.

> [!NOTE]
> Nu udrulles en følsomhedsmærkat i Outlook som prøveversion og kan anvende S/MIME-beskyttelse i stedet for kryptering og tilladelser fra Azure Rights Management-tjenesten. Du kan finde flere oplysninger under [Konfigurer en mærkat til at anvende S/MIME-beskyttelse i Outlook](sensitivity-labels-office-apps.md#configure-a-label-to-apply-smime-protection-in-outlook).

## <a name="understand-how-the-encryption-works"></a>Forstå, hvordan krypteringen fungerer

Kryptering bruger Azure Rights Management-tjenesten (Azure RMS) fra Azure Information Protection. Denne beskyttelsesløsning bruger politikker for kryptering, identitet og godkendelse. Du kan få mere at vide under [Hvad er Azure Rights Management?](/azure/information-protection/what-is-azure-rms) i dokumentationen til Azure Information Protection. 

Når du bruger denne krypteringsløsning, sikrer **funktionen superbruger** , at godkendte personer og tjenester altid kan læse og inspicere de data, der er krypteret for din organisation. Hvis det er nødvendigt, kan krypteringen derefter fjernes eller ændres. Du kan finde flere oplysninger under [Konfiguration af superbrugere til Azure Information Protection- og registreringstjenester eller datagendannelse](/azure/information-protection/configure-super-users).

## <a name="important-prerequisites"></a>Vigtige forudsætninger

Før du kan bruge kryptering, skal du muligvis udføre nogle konfigurationsopgaver. Når du konfigurerer krypteringsindstillinger, er der ingen kontrol til at validere, at disse forudsætninger er opfyldt.

- Aktivér beskyttelse fra Azure Information Protection
    
    Hvis følsomhedsmærkater skal anvende kryptering, skal beskyttelsestjeneste (Azure Rights Management) fra Azure Information Protection være aktiveret for din lejer. I nyere lejere er dette standardindstillingen, men du skal muligvis aktivere tjenesten manuelt. Du kan få flere oplysninger under [Aktivering af beskyttelsestjeneste fra Azure Information Protection](/azure/information-protection/activate-service).

- Kontrollér, om der er netværkskrav
    
    Du skal muligvis foretage nogle ændringer på dine netværksenheder, f.eks. firewalls. Du kan finde flere oplysninger i [Firewalls og netværksinfrastruktur](/azure/information-protection/requirements#firewalls-and-network-infrastructure) fra dokumentationen til Azure Information Protection.

- Konfigurer Exchange til Azure Information Protection
    
    Exchange behøver ikke at være konfigureret til Azure Information Protection, før brugerne kan anvende mærkater i Outlook til at kryptere deres mails. Men indtil Exchange er konfigureret til Azure Information Protection, får du ikke den fulde funktionalitet ved at bruge Azure Rights Management-beskyttelse med Exchange.
    
    Brugerne kan f.eks. ikke få vist krypterede mails på mobiltelefoner eller med Outlook på internettet, krypterede mails kan ikke indekseres til søgning, og du kan ikke konfigurere Exchange Online DLP for Rights Management-beskyttelse. 
    
    Sådan sikrer du, at Exchange kan understøtte disse yderligere scenarier:
    
    - Du kan finde Exchange Online i vejledningen til [Exchange Online: IRM-konfiguration](/azure/information-protection/configure-office365#exchangeonline-irm-configuration).
    - I forbindelse med Exchange i det lokale miljø skal du installere [RMS-connectoren og konfigurere dine Exchange-servere](/azure/information-protection/deploy-rms-connector).

## <a name="how-to-configure-a-label-for-encryption"></a>Sådan konfigurerer du en mærkat til kryptering

1. Følg den generelle vejledning for at [oprette eller redigere en følsomhedsmærkat](create-sensitivity-labels.md#create-and-configure-sensitivity-labels) , og sørg for **, at Elementer** er valgt til etikettens område: 
    
    ![Indstillinger for følsomhedsmærkatområde for filer og mails.](../media/filesandemails-scope-options-sensitivity-label.png)

2. På siden **Vælg beskyttelsesindstillinger for navngivne elementer** skal du derefter sørge for at vælge **Kryptér elementer**
    
    :::image type="content" source="../media/protection-options-sensitivity-label.png" alt-text="Indstillinger for beskyttelse af følsomhedsmærkater for elementer." Lightbox="../media/protection-options-sensitivity-label.png":::

4.  Vælg en af følgende indstillinger på siden **Kryptering** :
    
    - **Fjern kryptering, hvis filen er krypteret**: Denne indstilling understøttes kun af Azure Information Protection Unified-navngivningsklienten. Når du vælger denne indstilling og bruger indbygget mærkat, vises etiketten muligvis ikke i apps eller vises og foretager ikke nogen krypteringsændringer.
        
        Du kan finde flere oplysninger om dette scenarie i afsnittet [Hvad sker der med eksisterende kryptering, når en mærkat anvendes](#what-happens-to-existing-encryption-when-a-labels-applied) ? Det er vigtigt at forstå, at denne indstilling kan resultere i en følsomhedsmærkat, som brugerne muligvis ikke kan anvende, når de ikke har tilstrækkelige tilladelser.
    
    - **Konfigurer krypteringsindstillinger**: Slår kryptering til og gør krypteringsindstillingerne synlige:
        
        :::image type="content" source="../media/encrytion-options-sensitivity-label.png" alt-text="Indstillinger for følsomhedsmærkat til kryptering. "lightbox="../media/encrytion-options-sensitivity-label.png":::
        
        Instruktioner til disse indstillinger findes i følgende afsnit [Konfigurer krypteringsindstillinger](#configure-encryption-settings) .

### <a name="what-happens-to-existing-encryption-when-a-labels-applied"></a>Hvad sker der med eksisterende kryptering, når der anvendes en mærkat?

Hvis der anvendes en følsomhedsmærkat på ukrypteret indhold, er resultatet af de krypteringsindstillinger, du kan vælge, selvforklarende. Hvis du f.eks. ikke har valgt **Kryptér filer og mails**, forbliver indholdet ukrypteret.

Indholdet er dog muligvis allerede krypteret. En anden bruger kan f.eks. have anvendt:

- Deres egne tilladelser, som omfatter brugerdefinerede tilladelser, når de bliver bedt om det af en mærkat, brugerdefinerede tilladelser fra Azure Information Protection-klienten og dokumentbeskyttelse med **begrænset adgang** inde fra en Office-app.
- En Azure Rights Management-beskyttelsesskabelon, der krypterer indholdet uafhængigt af en mærkat. Denne kategori indeholder regler for mailflow, der anvender kryptering ved hjælp af rettighedsbeskyttelse.
- En mærkat, der anvender kryptering med tilladelser, der er tildelt af administratoren.

I følgende tabel identificeres det, hvad der sker med eksisterende kryptering, når der anvendes en følsomhedsmærkat på det pågældende indhold:

| | Kryptering: Ikke valgt | Kryptering: Konfigureret | Kryptering: Fjern <sup>\*</sup> |
|:-----|:-----|:-----|:-----|
|**Tilladelser, der er angivet af en bruger**|Den oprindelige kryptering bevares|Der anvendes ny mærkatkryptering|Den oprindelige kryptering er fjernet|
|**Beskyttelsesskabelon**|Den oprindelige kryptering bevares|Der anvendes ny mærkatkryptering|Den oprindelige kryptering er fjernet|
|**Navn med administratordefinerede tilladelser**|Den oprindelige kryptering er fjernet|Der anvendes ny mærkatkryptering|Den oprindelige kryptering er fjernet|

**Fodnote:**

<sup>\*</sup>Understøttes kun af Azure Information Protection unified labeling-klienten

I de tilfælde, hvor den nye mærkatkryptering anvendes, eller den oprindelige kryptering fjernes, sker dette kun, hvis den bruger, der anvender mærkaten, har en brugsrettighed eller -rolle, der understøtter denne handling:

- [Brugsrettigheden](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Eksportér eller Fuld kontrol.
- Rollen som [Rettighedsadministration-udsteder eller Rights Management-ejer](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) eller [superbruger](/azure/information-protection/configure-super-users).

Hvis brugeren ikke har en af disse rettigheder eller roller, kan mærkaten ikke anvendes, og den oprindelige kryptering bevares. Brugeren får vist følgende meddelelse: **Du har ikke tilladelse til at foretage denne ændring af følsomhedsmærkaten. Kontakt ejeren af indholdet.**

Den person, der anvender Videresend ikke på en mail, kan f.eks. genmærke tråden for at erstatte krypteringen eller fjerne den, fordi vedkommende er ejeren af Rights Management for mailen. Men med undtagelse af superbrugere kan modtagere af denne mail ikke genmærke den, fordi de ikke har de påkrævede brugsrettigheder.

#### <a name="email-attachments-for-encrypted-email-messages"></a>Vedhæftede filer i mails for krypterede mails

Når en mail krypteres af en hvilken som helst metode, arver alle ukrypterede Office-dokumenter, der er knyttet til mailen, automatisk de samme krypteringsindstillinger.

Dokumenter, der allerede er krypteret og derefter tilføjes som vedhæftede filer, bevarer altid deres oprindelige kryptering.

## <a name="configure-encryption-settings"></a>Konfigurer krypteringsindstillinger

Når du vælger **Konfigurer krypteringsindstillinger** på siden **Kryptering** for at oprette eller redigere en følsomhedsmærkat, skal du vælge en af følgende indstillinger:

- **Tildel tilladelser nu**, så du kan bestemme præcis, hvilke brugere der får hvilke tilladelser til indhold, hvor mærkaten er anvendt. Du kan finde flere oplysninger i næste afsnit [Tildel tilladelser nu](#assign-permissions-now).
- **Lad brugerne tildele tilladelser** , når brugerne anvender mærkaten på indhold. Med denne indstilling kan du give personer i din organisation en vis fleksibilitet, så de kan få brug for at samarbejde og få arbejdet fra hånden. Du kan få flere oplysninger i afsnittet [Lad brugere tildele tilladelser](#let-users-assign-permissions) på denne side.

Hvis du f.eks. har en følsomhedsmærkat med navnet **Meget fortroligt** , der anvendes på dit mest følsomme indhold, kan det være en god idé at beslutte, hvem der får hvilken type tilladelser til det pågældende indhold.

Hvis du har en følsomhedsmærkat med navnet **Forretningskontrakter**, og din organisations arbejdsproces kræver, at dine personer samarbejder om dette indhold med andre personer på en ikke-planlagt basis, kan det være en god idé at give dine brugere tilladelse til at beslutte, hvem der får tilladelser, når de tildeler mærkaten. Denne fleksibilitet hjælper både brugernes produktivitet og reducerer anmodningerne til dine administratorer om at opdatere eller oprette nye følsomhedsmærkater for at håndtere bestemte scenarier.

Vælg, om du vil tildele tilladelser nu, eller lade brugerne tildele tilladelser:

![Mulighed for at tilføje bruger- eller administratordefinerede tilladelser.](../media/sensitivity-label-user-or-admin-defined-permissions.png)

## <a name="assign-permissions-now"></a>Tildel tilladelser nu

Brug følgende indstillinger til at styre, hvem der har adgang til mail eller dokumenter, som denne mærkat anvendes på. Du kan:

- **Tillad, at adgangen til markeret indhold udløber** enten på en bestemt dato eller efter et bestemt antal dage, efter at mærkaten er anvendt. Efter dette tidspunkt kan brugerne ikke åbne det mærkede element. Hvis du angiver en dato, træder den i kraft midnat på den pågældende dato i din aktuelle tidszone. Nogle mailklienter gennemtvinger muligvis ikke udløb og viser mails efter deres udløbsdato på grund af deres cachelagringsmekanismer.

- **Tillad offlineadgang** aldrig, altid eller i et bestemt antal dage, efter at etiketten er anvendt. Brug denne indstilling til at afbalancere de sikkerhedskrav, du har, så brugerne kan åbne krypteret indhold, når de ikke har en internetforbindelse. Hvis du begrænser offlineadgang til aldrig eller et antal dage, når denne grænse nås, skal brugerne godkendes igen, og deres adgang logføres. Du kan få flere oplysninger om, hvordan denne proces fungerer, i følgende afsnit om [rights management-brugslicensen](#rights-management-use-license-for-offline-access).

Indstillinger for adgangskontrol for krypteret indhold:

![Indstillinger for administratordefinerede tilladelser.](../media/sensitivity-encryption-settings-for-admin-defined-permissions.png)

Anbefalinger til indstillingerne for udløbs- og offlineadgang:

|Indstilling|Anbefalet indstilling|
|-------|----------------|-------------------|
|**Brugeradgang til indhold udløber**|**Aldrig** medmindre indholdet har et bestemt tidsbundet krav.|
|**Tillad offlineadgang**|Afhænger af indholdets følsomhed:<br /><br />- **Kun i et antal dage** =  **7** for følsomme forretningsdata, der kan forårsage skade på virksomheden, hvis de deles med uautoriserede personer. Denne henstilling udgør et afbalanceret kompromis mellem fleksibilitet og sikkerhed. Eksempler omfatter kontrakter, sikkerhedsrapporter, prognoseoversigter og salgskontodata.<br /><br />- **Aldrig** for meget følsomme forretningsdata, der ville forårsage skade på virksomheden, hvis de blev delt med uautoriserede personer. Denne anbefaling prioriterer sikkerhed frem for fleksibilitet og sikrer, at hvis du fjerner en eller flere brugeres adgang til dokumentet, kan de ikke åbne det. Eksempler omfatter medarbejder- og kundeoplysninger, adgangskoder, kildekode og forhånds annoncerede regnskaber. <br /><br />- **Altid** for mindre følsomt indhold, hvor det ikke betyder noget, om brugerne kan fortsætte med at åbne krypteret indhold i op til 30 dage (eller lejerens konfigurerede licensperiode), efter deres adgang er fjernet, og de tidligere har åbnet det krypterede indhold.|

Det er kun etiketter, der er konfigureret til at tildele tilladelser, der nu understøtter forskellige værdier for offlineadgang. Mærkater, der giver brugerne mulighed for automatisk at bruge lejerens Rights Management-licensperiode. Det kan f.eks. være mærkater, der er konfigureret for Videresend ikke, Kryptér kun og bede brugerne om at angive deres egne tilladelser. Standardværdien for denne indstilling er 30 dage.

### <a name="rights-management-use-license-for-offline-access"></a>Rights Management bruger licens til offlineadgang

> [!NOTE]
> Selvom du kan konfigurere krypteringsindstillingen for at tillade offlineadgang, understøtter nogle apps muligvis ikke offlineadgang til krypteret indhold. Navngivne og krypterede filer i [Power BI Desktop](/power-bi/admin/service-security-sensitivity-label-overview) åbnes f.eks. ikke, hvis du er offline.

Når en bruger åbner et dokument eller en mail, der er beskyttet af kryptering fra Azure Rights Management-tjenesten, tildeles brugeren en Azure Rights Management-brugerlicens til det pågældende indhold. Denne brugslicens er et certifikat, der indeholder brugerens brugsrettigheder til dokumentet eller mailen og den krypteringsnøgle, der blev brugt til at kryptere indholdet. Brugslicensen indeholder også en udløbsdato, hvis den er angivet, og hvor lang tid brugslicensen er gyldig.

Hvis der ikke er angivet en udløbsdato, er standardlicensens gyldighedsperiode for brug 30 dage for en lejer. I varigheden af brugslicensen godkendes eller autoriseres brugeren ikke for indholdet igen. Denne proces gør det muligt for brugeren at fortsætte med at åbne det beskyttede dokument eller den beskyttede mail uden en internetforbindelse. Når gyldighedsperioden for brugslicensen udløber, skal brugeren godkendes og godkendes igen, næste gang brugeren tilgår det beskyttede dokument eller den beskyttede mail.

Ud over at godkende igen evalueres krypteringsindstillingerne og brugergruppemedlemskabet igen. Det betyder, at brugerne kan opleve forskellige adgangsresultater for det samme dokument eller den samme mail, hvis der er ændringer i krypteringsindstillingerne eller gruppemedlemskabet, fra da de sidst fik adgang til indholdet.

Hvis du vil vide mere om, hvordan du ændrer standardindstillingen for 30 dage, skal du se [Rights Management-brugslicens](/azure/information-protection/configure-usage-rights#rights-management-use-license).

### <a name="assign-permissions-to-specific-users-or-groups"></a>Tildel tilladelser til bestemte brugere eller grupper

Du kan tildele tilladelser til bestemte personer, så det kun er dem, der kan interagere med det navngivne indhold:

1. Tilføj først brugere eller grupper, der skal tildeles tilladelser til det navngivne indhold.

2. Vælg derefter, hvilke tilladelser disse brugere skal have til det navngivne indhold.

Tildeling af tilladelser:

![Indstillinger for tildeling af tilladelser til brugere.](../media/Sensitivity-Assign-permissions-settings.png)

#### <a name="add-users-or-groups"></a>Tilføj brugere eller grupper

Når du tildeler tilladelser, kan du vælge:

- Alle i organisationen (alle lejermedlemmer). Denne indstilling udelukker gæstekonti.

- Alle godkendte brugere. Sørg for at forstå [kravene og begrænsningerne](#requirements-and-limitations-for-add-any-authenticated-users) for denne indstilling, før du vælger den.

- En bestemt bruger- eller mailaktiveret sikkerhedsgruppe, distributionsgruppe eller Microsoft 365-gruppe i Azure AD. Microsoft 365-gruppen kan have statisk eller [dynamisk medlemskab](/azure/active-directory/users-groups-roles/groups-create-rule). Du kan ikke bruge en [dynamisk distributionsgruppe fra Exchange](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups), fordi denne gruppetype ikke er synkroniseret til Azure AD. Du kan heller ikke bruge en sikkerhedsgruppe, der ikke er mailaktiveret.
    
    Selvom du kan angive grupper, der indeholder mailkontakter, som en praktisk metode til at give adgang til flere personer uden for din organisation, er der i øjeblikket et kendt problem med denne konfiguration. Du kan få flere oplysninger under [Mailkontakter i grupper har periodisk adgang til krypteret indhold](/office365/troubleshoot/sensitivity-labels/mail-contacts-lose-access-encrypted-content).

- En hvilken som helst mailadresse eller et domæne. Brug denne indstilling til at angive alle brugere i en anden organisation, der bruger Azure AD, ved at angive et domænenavn fra den pågældende organisation. Du kan også bruge denne indstilling til sociale udbydere ved at angive deres domænenavn, f.eks. **gmail.com**, **hotmail.com** eller **outlook.com**.

    > [!NOTE]
    > Hvis du angiver et domæne fra en organisation, der bruger Azure AD, kan du ikke begrænse adgangen til det pågældende domæne. I stedet medtages alle bekræftede domæner i Azure AD automatisk for den lejer, der ejer det domænenavn, du angiver.

Når du vælger alle brugere og grupper i din organisation eller gennemser mappen, skal brugerne eller grupperne have en mailadresse.

Som bedste praksis kan du bruge grupper i stedet for brugere. Denne strategi gør konfigurationen enklere.

##### <a name="requirements-and-limitations-for-add-any-authenticated-users"></a>Krav og begrænsninger for "Tilføj godkendte brugere"

Denne indstilling begrænser ikke, hvem der kan få adgang til det indhold, som mærkaten krypterer, mens den stadig krypterer indholdet og giver dig mulighed for at begrænse, hvordan indholdet kan bruges (tilladelser), og hvordan det kan tilgås (udløbs- og offlineadgang). Programmet, der åbner det krypterede indhold, skal dog kunne understøtte den godkendelse, der bruges. Derfor fungerer sociale udbydere i organisationsnetværket, f.eks. Google, og engangsgodkendelse af adgangskode kun for mail, og kun når du bruger Exchange Online. Microsoft-konti kan bruges sammen med Office 365 apps og [Azure Information Protection-fremviseren](https://portal.azurerms.com/#/download).

> [!NOTE]
> Overvej at bruge denne indstilling med [SharePoint- og OneDrive-integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview), når følsomhedsmærkater er [aktiveret for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Nogle typiske scenarier for enhver indstilling for godkendte brugere:

- Du har ikke noget imod, hvem der får vist indholdet, men du vil begrænse, hvordan det bruges. Du ønsker f.eks. ikke, at indholdet skal redigeres, kopieres eller udskrives.
- Du behøver ikke at begrænse, hvem der har adgang til indholdet, men du vil gerne kunne bekræfte, hvem der åbner det.
- Du har et krav om, at indholdet skal krypteres som inaktive og under overførsel, men det kræver ikke adgangskontrol.

#### <a name="choose-permissions"></a>Vælg tilladelser

Når du vælger, hvilke tilladelser der skal tillades for disse brugere eller grupper, kan du vælge en af følgende:

- Et [foruddefineret tilladelsesniveau](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels) med en forudindstillet gruppe af rettigheder, f.eks. Co-Author eller Korrekturlæser.
- Brugerdefinerede tilladelser, hvor du vælger en eller flere brugsrettigheder.

Du kan finde flere oplysninger, der kan hjælpe dig med at vælge de relevante tilladelser, under [Brugsrettigheder og beskrivelser](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions).  

![Indstillinger for at vælge forudindstillede eller brugerdefinerede tilladelser.](../media/Sensitivity-Choose-permissions-settings.png)

Bemærk, at den samme mærkat kan give forskellige tilladelser til forskellige brugere. En enkelt mærkat kan f.eks. tildele nogle brugere som Reviewer og en anden bruger som medforfatter, som vist på følgende skærmbillede.

Det gør du ved at tilføje brugere eller grupper, tildele dem tilladelser og gemme disse indstillinger. Gentag derefter disse trin, tilføj brugere, og tildel dem tilladelser, og gem indstillingerne hver gang. Du kan gentage denne konfiguration så ofte, det er nødvendigt, for at definere forskellige tilladelser for forskellige brugere.

![Forskellige brugere med forskellige tilladelser.](../media/Sensitivity-Multiple-users-permissions.png)

#### <a name="rights-management-issuer-user-applying-the-sensitivity-label-always-has-full-control"></a>Rights Management-udsteder (bruger, der anvender følsomhedsmærkaten) har altid Fuld kontrol

Kryptering af en følsomhedsmærkat bruger Azure Rights Management-tjenesten fra Azure Information Protection. Når en bruger anvender en følsomhedsmærkat for at beskytte et dokument eller en mail ved hjælp af kryptering, bliver brugeren Rights Management-udstederen for det pågældende indhold.

Rights Management-udstederen tildeles altid fuld kontrol-tilladelser til dokumentet eller mailen og derudover:

- Hvis krypteringsindstillingerne indeholder en udløbsdato, kan Rights Management-udstederen stadig åbne og redigere dokumentet eller mailen efter denne dato.
- Rights Management-udstederen kan altid få adgang til dokumentet eller mailen offline.
- Rights Management-udstederen kan stadig åbne et dokument, når det er tilbagekaldt.

Du kan få flere oplysninger under [Udsteder af Rights Management og Rights Management-ejer](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner).

### <a name="double-key-encryption"></a>Kryptering med dobbelt nøgle

> [!NOTE]
> Denne funktion understøttes i øjeblikket kun af Azure Information Protection Unified Labeling-klienten.

Vælg kun denne indstilling, når du har konfigureret tjenesten Dobbeltnøglekryptering, og du skal bruge denne dobbelte nøglekryptering til filer, hvor denne mærkat anvendes. Når etiketten er konfigureret og gemt, kan du ikke redigere den.

Du kan finde flere oplysninger, forudsætninger og konfigurationsinstruktioner under [Dobbeltnøglekryptering (DKE).](double-key-encryption.md)

## <a name="let-users-assign-permissions"></a>Lad brugerne tildele tilladelser

> [!IMPORTANT]
> Ikke alle navngivne klienter understøtter alle de indstillinger, der giver brugerne mulighed for at tildele deres egne tilladelser. Brug dette afsnit til at få mere at vide.

Du kan bruge følgende indstillinger til at lade brugerne tildele tilladelser, når de manuelt anvender en følsomhedsmærkat på indhold:

- I Outlook kan en bruger vælge begrænsninger, der svarer til indstillingen [Videresend ikke](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails) eller [Kun kryptér](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails) for de valgte modtagere.
    
    Indstillingen Videresend ikke understøttes af alle mailklienter, der understøtter følsomhedsmærkater. Men anvendelse af indstillingen **Encrypt-Only** med en følsomhedsmærkat er en nyere version, der kun understøttes af indbygget mærkning og ikke Azure Information Protection Unified Labeling-klienten. For mailklienter, der ikke understøtter denne funktion, er mærkaten ikke synlig.
    
    Hvis du vil kontrollere minimumversionerne af Outlook-apps, der bruger indbygget mærkning til at understøtte anvendelse af indstillingen Encrypt-Only med en følsomhedsmærkat, skal du bruge [tabellen capabilities til Outlook](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-outlook) og rækken **Lad brugerne tildele tilladelser: - Encrypt-Only**.

- I Word, PowerPoint og Excel bliver en bruger bedt om at vælge sine egne tilladelser til bestemte brugere, grupper eller organisationer.

    Denne indstilling understøttes af Azure Information Protection Unified Labeling-klienten og af nogle apps, der bruger indbygget mærkning. For apps, der ikke understøtter denne funktion, vil mærkaten enten ikke være synlig for brugere, eller etiketten er synlig af hensyn til konsistens, men den kan ikke anvendes med en forklaringsmeddelelse til brugerne.
    
    Hvis du vil kontrollere, hvilke apps der bruger indbygget mærkning, der understøtter denne indstilling, skal du bruge [tabel over funktioner til Word, Excel og PowerPoint](sensitivity-labels-office-apps.md#sensitivity-label-capabilities-in-word-excel-and-powerpoint) og rækken **Lad brugere tildele tilladelser: – Spørg brugere**.

Når indstillingerne understøttes, kan du bruge følgende tabel til at identificere, hvornår brugerne får vist følsomhedsmærkaten:

|Indstilling |Navnet er synligt i Outlook|Mærkat, der er synlig i Word, Excel, PowerPoint|
|:-----|:-----|:-----|:-----|
|**I Outlook skal du gennemtvinge begrænsninger med indstillingen Videresend ikke eller Encrypt-Only**|Ja |Nej |
|**I Word, PowerPoint og Excel skal du bede brugerne om at angive tilladelser**|Nej |Ja|

Når begge indstillinger er valgt, er mærkaten derfor synlig både i Outlook og i Word, Excel og PowerPoint.

En følsomhedsmærkat, der giver brugerne mulighed for at tildele tilladelser, skal anvendes på indhold manuelt af brugerne. den kan ikke anvendes automatisk eller bruges som en anbefalet mærkat.

Konfiguration af de brugertildelt tilladelser:

![Krypteringsindstillinger for brugerdefinerede tilladelser.](../media/sensitivity-encryption-settings-for-user-defined-permissions.png)

### <a name="outlook-restrictions"></a>Outlook-begrænsninger

Når en bruger anvender en følsomhedsmærkat i Outlook, der giver vedkommende mulighed for at tildele tilladelser til en meddelelse, kan du vælge **indstillingen Videresend ikke** eller **Kryptér kun**. Brugeren får vist navnet og beskrivelsen øverst i meddelelsen, som angiver, at indholdet er beskyttet. I modsætning til Word, PowerPoint og Excel (se [næste afsnit](#word-powerpoint-and-excel-permissions)) bliver brugerne ikke bedt om at vælge bestemte tilladelser.

![Følsomhedsmærkat anvendt på meddelelsen i Outlook.](../media/sensitivity-label-outlook-protection-applied.png)

Når en af disse indstillinger anvendes på en mail, krypteres mailen, og modtagerne skal godkendes. Modtagerne har derefter automatisk begrænsede brugsrettigheder:

- **Videresend ikke**: Modtagerne kan ikke videresende mailen, udskrive den eller kopiere den fra den. I Outlook-klienten er knappen Videresend f.eks. ikke tilgængelig, menuindstillingerne Gem som og Udskriv er ikke tilgængelige, og du kan ikke tilføje eller ændre modtagere i boksene Til, Cc eller Bcc.
    
    Du kan få flere oplysninger om, hvordan denne indstilling fungerer, under [Indstillingen Videresend ikke for mails](/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails).

- **Kun krypt**: Modtagere har alle brugsrettigheder undtagen Gem som, Eksportér og Fuld kontrol. Denne kombination af brugsrettigheder betyder, at modtagerne ikke har nogen begrænsninger, bortset fra at de ikke kan fjerne beskyttelsen. En modtager kan f.eks. kopiere fra mailen, udskrive den og videresende den.
    
    Du kan få flere oplysninger om, hvordan denne indstilling fungerer, under [Indstillingen Kun kryptering for mails](/azure/information-protection/configure-usage-rights#encrypt-only-option-for-emails).

Ukrypterede Office-dokumenter, der er knyttet til mailen, nedarver automatisk de samme begrænsninger. For Videresend ikke er de anvendelsesrettigheder, der er anvendt på disse dokumenter, Rediger indhold, Rediger. Gem; Vis, Åbn, Læs; og Tillad makroer. Hvis brugeren ønsker forskellige brugsrettigheder til en vedhæftet fil, eller hvis den vedhæftede fil ikke er et Office-dokument, der understøtter denne nedarvede beskyttelse, skal brugeren kryptere filen, før den vedhæftes i mailen.

### <a name="word-powerpoint-and-excel-permissions"></a>Word-, PowerPoint- og Excel-tilladelser

Når en bruger anvender en følsomhedsmærkat i Word, PowerPoint og Excel, der giver vedkommende mulighed for at tildele tilladelser til et dokument, bliver brugeren bedt om at angive sit valg af brugere og tilladelser til krypteringen.

Med Azure Information Protection Unified-mærkatklienten kan brugerne f.eks.:[](sensitivity-labels-coauthoring.md)

- Vælg et tilladelsesniveau, f.eks. Fremviser (som tildeler tilladelsen Vis kun) eller Co-Author (som tildeler tilladelserne Vis, Rediger, Kopiér og Udskriv).
- Vælg brugere, grupper eller organisationer. Dette kan omfatte personer både i og uden for din organisation.
- Angiv en udløbsdato, hvorefter de valgte brugere ikke kan få adgang til indholdet. Du kan få flere oplysninger i afsnittet [Rights Management bruger licens til offlineadgang](#rights-management-use-license-for-offline-access).

![Indstillinger, som brugeren kan beskytte med brugerdefinerede tilladelser.](../media/sensitivity-aip-custom-permissions-dialog.png)

I forbindelse med indbygget mærkning og For Azure Information Protection Unified [Labeling-klienten, når samtidig redigering er aktiveret](sensitivity-labels-coauthoring.md), får brugerne vist den samme dialogboks, som hvis de valgte følgende indstillinger:

- Windows: Fanen **Filer** > **Info** > **Beskyt dokument** > **Begræns adgang til** > **begrænset adgang**

- macOS: **Gennemse** fane >**beskyttelsesrettigheder** >  >  **begrænset adgang**

> [!TIP]
> Hvis brugerne havde kendskab til at konfigurere brugerdefinerede tilladelser med Azure Information Protection Unified-navngivningsklienten, før [samtidig redigering blev aktiveret](sensitivity-labels-coauthoring.md), kan det være nyttigt at gennemse tilknytningen af tilladelsesniveauer til individuelle brugsrettigheder: [Rettigheder, der er inkluderet i tilladelsesniveauer](/azure/information-protection/configure-usage-rights#rights-included-in-permissions-levels).

## <a name="example-configurations-for-the-encryption-settings"></a>Eksempelkonfigurationer for krypteringsindstillingerne

For hvert af de følgende eksempler skal du udføre konfigurationen fra siden **Kryptering** , når **Konfigurer krypteringsindstillinger** er valgt:

![Indstillingen Anvend kryptering i guiden med følsomhedsmærkater.](../media/apply-encryption-option.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-an-encrypted-email-to-a-gmail-account"></a>Eksempel 1: Mærkat, der anvender Videresend ikke for at sende en krypteret mail til en Gmail-konto

Denne etiket vises kun i Outlook og Outlook på internettet, og du skal bruge Exchange Online. Instruer brugerne i at vælge denne mærkat, når de har brug for at sende en krypteret mail til personer, der bruger en Gmail-konto (eller en anden mailkonto uden for din organisation).

Dine brugere skriver Gmail-mailadressen i feltet **Til** .  Derefter vælger de etiketten, og indstillingen Videresend ikke føjes automatisk til mailen. Resultatet er, at modtagerne ikke kan videresende mailen eller udskrive den, kopiere fra den eller gemme mailen uden for deres postkasse ved hjælp af indstillingen **Gem som** .

1. På siden **Kryptering** : For **Tildel tilladelser nu eller lad brugerne bestemme?** vælg **Lad brugere tildele tilladelser, når de anvender mærkaten**.

2. Markér afkrydsningsfeltet: **I Outlook skal du gennemtvinge begrænsninger, der svarer til indstillingen Videresend ikke**.

3. Hvis indstillingen er markeret, skal du fjerne markeringen i afkrydsningsfeltet: **I Word, PowerPoint og Excel skal du bede brugerne om at angive tilladelser**.

4. Vælg **Næste** , og fuldfør konfigurationen.

### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization"></a>Eksempel 2: Mærkat, der begrænser skrivebeskyttet tilladelse til alle brugere i en anden organisation

Denne mærkat er velegnet til deling af meget følsomme dokumenter som skrivebeskyttet, og dokumenterne kræver altid en internetforbindelse for at få dem vist.

Denne mærkat er ikke egnet til mails.

1. På siden **Kryptering** : Hvis **du vil tildele tilladelser nu, eller lade brugerne bestemme,** skal du vælge **Tildel tilladelser nu**.

2. Vælg **Aldrig** **for Tillad offlineadgang**.

3. Vælg **Tildel tilladelser**.

4. I ruden **Tildel tilladelser** skal du vælge **Tilføj bestemte mailadresser eller domæner**.

5. I tekstfeltet skal du angive navnet på et domæne fra den anden organisation, f.eks. **fabrikam.com**. Vælg derefter **Tilføj**.

6. Vælg **Vælg tilladelser**.

7. I ruden **Vælg tilladelser** skal du vælge rullelisten, vælge **Seer** og derefter vælge **Gem**.

8. Tilbage i ruden **Tildel tilladelser** skal du vælge **Gem**.

9. På siden **Kryptering** skal du vælge **Næste** og fuldføre konfigurationen.

### <a name="example-3-add-external-users-to-an-existing-label-that-encrypts-content"></a>Eksempel 3: Føj eksterne brugere til en eksisterende mærkat, der krypterer indhold

De nye brugere, du tilføjer, kan åbne dokumenter og mails, der allerede er beskyttet med denne mærkat. De tilladelser, du tildeler disse brugere, kan være forskellige fra de tilladelser, som de eksisterende brugere har.

1. På siden **Kryptering** : Hvis du vil **tildele tilladelser nu, eller lade brugerne bestemme,** skal du sørge for **, at Tildel tilladelser nu** er valgt.

2. Vælg **Tildel tilladelser**.

3. I ruden **Tildel tilladelser** skal du vælge **Tilføj bestemte mailadresser eller domæner**.

4. Angiv mailadressen på den første bruger (eller gruppe), der skal tilføjes, i tekstfeltet, og vælg derefter **Tilføj**.

5. Vælg **Vælg tilladelser**.

6. I ruden **Vælg tilladelser** skal du vælge tilladelserne for denne bruger (eller gruppe) og derefter vælge **Gem**.

7. Tilbage i ruden **Tildel tilladelser** skal du gentage trin 3 til 6 for hver bruger (eller gruppe), du vil føje til dette navn. Klik derefter på **Gem**.

8. På siden **Kryptering** skal du vælge **Næste** og fuldføre konfigurationen.

### <a name="example-4-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Eksempel 4: Mærkat, der krypterer indhold, men som ikke begrænser, hvem der har adgang til det

Denne konfiguration har den fordel, at du ikke behøver at angive brugere, grupper eller domæner for at kryptere en mail eller et dokument. Indholdet krypteres stadig, og du kan stadig angive brugsrettigheder, en udløbsdato og offlineadgang.

Brug kun denne konfiguration, når du ikke behøver at begrænse, hvem der kan åbne det beskyttede dokument eller den beskyttede mail. Se [flere oplysninger om denne indstilling](#requirements-and-limitations-for-add-any-authenticated-users).

1. På siden **Kryptering** : Hvis du vil **tildele tilladelser nu, eller lade brugerne bestemme,** skal du sørge for **, at Tildel tilladelser nu** er valgt.

2. Konfigurer indstillingerne for **brugeradgang til indhold udløber** , og **Tillad offlineadgang** efter behov.

3. Vælg **Tildel tilladelser**.

4. I ruden **Tildel tilladelser** skal du vælge **Tilføj alle godkendte brugere**.

    For **brugere og grupper** kan du se **Godkendte brugere** , der tilføjes automatisk. Du kan ikke ændre denne værdi, men kun slette den, hvilket annullerer valget **Tilføj alle godkendte brugere** .

5. Vælg **Vælg tilladelser**.

6. I ruden **Vælg tilladelser** skal du vælge rullelisten, vælge de ønskede tilladelser og derefter vælge **Gem**.

7. Tilbage i ruden **Tildel tilladelser** skal du vælge **Gem**.

8. På siden **Kryptering** skal du vælge **Næste** og fuldføre konfigurationen.

## <a name="considerations-for-encrypted-content"></a>Overvejelser i forbindelse med krypteret indhold

Kryptering af dine mest følsomme dokumenter og mails hjælper med at sikre, at det kun er godkendte personer, der kan få adgang til disse data. Der er dog nogle overvejelser, der skal tages højde for:

- Hvis din organisation ikke har [aktiveret følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md):

  - Søgning, eDiscovery og Delve fungerer ikke for krypterede filer.
  - DLP-politikker fungerer for metadataene for disse krypterede filer (herunder oplysninger om opbevaringsmærkat), men ikke indholdet af disse filer (f.eks. kreditkortnumre i filer).
  - Brugerne kan ikke åbne krypterede filer ved hjælp af Office på internettet. Når følsomhedsmærkater for Office-filer i SharePoint og OneDrive er aktiveret, kan brugerne bruge Office på internettet til at åbne krypterede filer med nogle [begrænsninger](sensitivity-labels-sharepoint-onedrive-files.md#limitations), der omfatter kryptering, der er anvendt med en lokal nøgle (kaldet "hold din egen nøgle" eller HYOK), kryptering med [dobbelt nøgle](#double-key-encryption) og kryptering, der er anvendt uafhængigt af en følsomhedsmærkat.

- Hvis du deler krypterede dokumenter med personer uden for din organisation, skal du muligvis oprette gæstekonti og redigere politikker for betinget adgang. Du kan få flere oplysninger under [Deling af krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Når godkendte brugere åbner krypterede dokumenter i deres Office-apps, får de vist mærkatnavnet og beskrivelsen på en gul meddelelseslinje øverst i deres app. Når krypteringstilladelserne udvides til personer uden for din organisation, skal du omhyggeligt gennemse de navne og beskrivelser, der er synlige på denne meddelelseslinje, når dokumentet åbnes.

- Hvis flere brugere skal kunne redigere en krypteret fil på samme tid, skal de alle bruge Office på internettet, eller du har [aktiveret samtidig redigering af filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md), og alle brugere har [Office-apps, der understøtter denne funktion](sensitivity-labels-coauthoring.md#prerequisites). Hvis det ikke er tilfældet, og filen allerede er åben:
    
  - I Office-apps (Windows, Mac, Android og iOS) får brugerne vist meddelelsen **Filer i brug** med navnet på den person, der har tjekket filen ud. De kan derefter få vist en skrivebeskyttet kopi eller gemme og redigere en kopi af filen og modtage en meddelelse, når filen er tilgængelig.
  - I Office på internettet får brugerne vist en fejlmeddelelse om, at de ikke kan redigere dokumentet med andre personer. De kan derefter vælge **Åbn i Læsevisning**.

- [Funktionen AutoSave](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) i Office-apps er deaktiveret for krypterede filer, hvis du ikke har [aktiveret samtidig redigering af filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md). Brugerne får vist en meddelelse om, at filen har begrænsede tilladelser, der skal fjernes, før Automatisk lagring kan aktiveres.

- Office til Windows understøtter mærkater, der anvender kryptering, når brugerne ikke har forbindelse til internettet. Men for de andre platforme (macOS, iOS, Android) skal brugerne være online for at anvende disse mærkater i Office-apps. Azure Information Protection Unified Labeling-klienten skal også være online for at kunne anvende disse mærkater i Stifinder og PowerShell. Brugerne behøver ikke at være online for at åbne krypteret indhold. Du kan få flere oplysninger om offlineadgang i afsnittet [Rights Management-brugslicens til offlineadgang ](#rights-management-use-license-for-offline-access) .

- Det kan tage længere tid at åbne krypterede filer i Office-apps (Windows, Mac, Android og iOS).

- Hvis en mærkat, der anvender kryptering, tilføjes ved hjælp af en Office-app, når dokumentet tjekkes [ud i SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de), og brugeren derefter sletter udtjekningen, forbliver dokumentet mærket og krypteret.

- Medmindre du har [aktiveret samtidig redigering af filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md), understøttes følgende handlinger for krypterede filer ikke fra Office-apps (Windows, Mac, Android og iOS), og brugerne får vist en fejlmeddelelse om, at noget gik galt. SharePoint-funktionalitet kan dog bruges som et alternativ:

  - Få vist, gendan og gem kopier af tidligere versioner. Alternativt kan brugerne udføre disse handlinger ved hjælp af Office på internettet, når du [aktiverer og konfigurerer versionering for en liste eller et bibliotek](https://support.office.com/article/enable-and-configure-versioning-for-a-list-or-library-1555d642-23ee-446a-990a-bcab618c7a37).
  - Rediger navnet på eller placeringen af filer. Alternativt kan brugerne [omdøbe en fil, en mappe eller et link i et dokumentbibliotek](https://support.microsoft.com/office/rename-a-file-folder-or-link-in-a-document-library-bc493c1a-921f-4bc1-a7f6-985ce11bb185) i SharePoint.

Vi anbefaler, at du bruger [følsomhedsmærkater til Office-filer i SharePoint og OneDrive og Office på internettet for](sensitivity-labels-sharepoint-onedrive-files.md) at få den bedste samarbejdsoplevelse for filer, der er krypteret af en følsomhedsmærkat.



## <a name="next-steps"></a>Næste trin

Har du brug for at dele dine navngivne og krypterede dokumenter med personer uden for din organisation?  Se [Deling af krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
