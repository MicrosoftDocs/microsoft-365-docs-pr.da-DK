---
title: Anvend automatisk en følsomhedsmærkat i Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Når du opretter en følsomhedsmærkat, kan du automatisk tildele en mærkat til filer og mails, eller du kan bede brugerne om at vælge den mærkat, du anbefaler.
ms.openlocfilehash: 69a36789e4143e3e8852976eb5e41c12ab6872f8
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287216"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>Anvend automatisk en følsomhedsmærkat på indhold

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!TIP]
> Du kan få oplysninger om automatisk anvendelse af en følsomhedsmærkat i datatilknytningen [under Mærkat i Microsoft Purview-datatilknytning](/azure/purview/create-sensitivity-label).

Når du opretter en følsomhedsmærkat, kan du automatisk tildele denne mærkat til filer og mails, når den opfylder betingelser, som du angiver.

Denne mulighed for automatisk at anvende følsomhedsmærkater på indhold er vigtig, fordi:

- Du behøver ikke at oplære dine brugere, hvornår de skal bruge hver af dine klassificeringer.

- Du behøver ikke at stole på, at brugerne klassificerer alt indhold korrekt.

- Brugerne behøver ikke længere at kende til dine politikker – de kan i stedet fokusere på deres arbejde.

Der er to forskellige metoder til automatisk anvendelse af en følsomhedsmærkat på indhold i Microsoft 365:

- **Navngivning på klientsiden, når brugerne redigerer dokumenter eller skriver (også besvarer eller videresender) mails**: Brug en mærkat, der er konfigureret til automatisk mærkning af filer og mails (herunder Word, Excel, PowerPoint og Outlook).

    Denne metode understøtter anbefaling af en mærkat til brugere samt automatisk anvendelse af en mærkat. Men i begge tilfælde beslutter brugeren, om brugeren vil acceptere eller afvise mærkaten, for at sikre korrekt mærkning af indhold. Denne navngivning på klientsiden har minimal forsinkelse for dokumenter, fordi mærkaten kan anvendes, selv før dokumentet gemmes. Det er dog ikke alle klientapps, der understøtter automatisk mærkning. Denne funktion understøttes af indbygget mærkning med [nogle versioner af Office](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) samt Azure Information Protection Unified Labeling-klienten.

    Du kan finde konfigurationsanvisninger under [Sådan konfigurerer du automatisk mærkning for Office apps](#how-to-configure-auto-labeling-for-office-apps) på denne side.

- **Mærkning på tjenestesiden, når indhold allerede er gemt (i SharePoint eller OneDrive) eller sendt via mail (behandlet af Exchange Online)**: Brug en politik for automatisk mærkning.
    
    Du kan også høre denne metode, der kaldes automatisk mærkning af inaktive data (dokumenter i SharePoint og OneDrive) og data under overførsel (mail, der sendes eller modtages af Exchange). For Exchange omfatter den ikke inaktive mails (postkasser).
    
    Da denne mærkning anvendes af tjenester i stedet for af programmer, behøver du ikke at bekymre dig om, hvilke apps brugerne har, og hvilken version. Denne funktion er derfor tilgængelig i hele organisationen med det samme og egner sig til mærkning i stor skala. Politikker for automatisk mærkning understøtter ikke anbefalet mærkning, fordi brugeren ikke interagerer med mærkatprocessen. Administratoren kører i stedet politikkerne i simulering for at sikre korrekt mærkning af indhold, før mærkaten anvendes.

    Du kan finde konfigurationsanvisninger under [Sådan konfigurerer du politikker for automatisk mærkning for SharePoint, OneDrive og Exchange](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) på denne side.
    
    Specifik til automatisk mærkning af SharePoint og OneDrive:
    
    - Office filer til Word (.docx), PowerPoint (.pptx) og Excel (.xlsx) understøttes.
        - Disse filer kan automatisk mærkes som hvile, før eller efter politikkerne for automatisk mærkning oprettes. Filer kan ikke navngives automatisk, hvis de er en del af en åben session (filen er åben).
        - I øjeblikket understøttes vedhæftede filer i listeelementer ikke og navngives ikke automatisk.
    - Maksimalt 25.000 automatisk navngivne filer i din lejer pr. dag.
    - Der kan maksimalt angives 100 politikker for automatisk mærkning pr. lejer, som hver især er målrettet til op til 100 websteder (SharePoint eller OneDrive), når de er angivet individuelt. Du kan også angive alle websteder, og denne konfiguration er undtaget fra maksimum 100 websteder.
    - Eksisterende værdier for ændret, ændret af og datoen ændres ikke som følge af politikker for automatisk mærkning – både for simuleringstilstand, og når der anvendes mærkater.
    - Når mærkaten anvender kryptering, er [udstederen af Rights Management og Rights Management-ejeren](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) den konto, der senest ændrede filen. Hvis denne konto ikke længere er i Azure Active Directory, anvendes mærkaten ikke, fordi disse værdier ikke kan angives.

    Specifik til automatisk mærkning af Exchange:
    
    - I modsætning til manuel mærkning eller automatisk mærkning med Office apps scannes vedhæftede PDF-filer samt Office vedhæftede filer også for de betingelser, du angiver i politikken for automatisk mærkning. Når der er et match, er mailen mærket, men ikke den vedhæftede fil.
        - Hvis mærkaten anvender kryptering for PDF-filer, krypteres disse filer ved hjælp af [meddelelsekryptering](ome.md) , når din lejer er [aktiveret for vedhæftede PDF-filer](ome-faq.yml#are-pdf-file-attachments-supported-).
        - For disse Office-filer understøttes Word, PowerPoint og Excel. Hvis mærkaten anvender kryptering, krypteres de ved hjælp af [Meddelelsekryptering](ome.md).
    - Hvis du har Exchange regler for mailflow eller DLP-politikker (Microsoft Purview Data Loss Prevention), der anvender IRM-kryptering: Når indhold identificeres af disse regler eller politikker og en politik for automatisk mærkning, anvendes mærkaten. Hvis dette navn anvender kryptering, ignoreres IRM-indstillingerne fra reglerne for Exchange mailflow eller DLP-politikker. Men hvis denne mærkat ikke anvender kryptering, anvendes IRM-indstillingerne fra reglerne for mailflowet eller DLP-politikkerne ud over mærkaten.
    - Mail, der har IRM-kryptering uden mærkat, erstattes af en mærkat med eventuelle krypteringsindstillinger, når der er et match ved hjælp af automatisk mærkning.
    - Indgående mail markeres, når der er et match med betingelserne for automatisk mærkning. Hvis denne mærkat er konfigureret til [kryptering](encryption-sensitivity-labels.md), anvendes denne kryptering altid, når afsenderen er fra din organisation. Denne kryptering anvendes som standard ikke, når afsenderen er uden for din organisation, men kan anvendes ved at konfigurere **Yderligere indstillinger for mail** og angive en Rights Management-ejer.
    - Når mærkaten anvender kryptering, er Udstederen [af Rights Management og Rights Management-ejeren](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) den person, der sender mailen, når afsenderen er fra din egen organisation. Når afsenderen er uden for din organisation, kan du angive en Rights Management-ejer for indgående mail, der er mærket og krypteret af din politik.
    - Hvis mærkaten er konfigureret til at anvende [dynamiske markeringer](sensitivity-labels-office-apps.md#dynamic-markings-with-variables), skal du være opmærksom på, at for indgående mail kan denne konfiguration resultere i, at navnene på personer uden for din organisation vises.

## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a>Sammenlign automatisk mærkning for Office apps med politikker for automatisk mærkning

Brug følgende tabel som en hjælp til at identificere forskellene i funktionsmåden for de to komplementære automatiske mærkningsmetoder:

|Funktion eller funktionsmåde|Navneindstilling: Automatisk mærkning af filer og mails  |Politik: Automatisk mærkning|
|:-----|:-----|:-----|
|Appafhængighed|Ja ([minimumversioner](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)) |Nej \* |
|Begræns efter placering|Nej |Ja |
|Betingelser: Klassificeringer, der kan oplæres|Ja |Nej |
|Betingelser: Delingsindstillinger og yderligere indstillinger for mail|Nej |Ja |
|Betingelser: Undtagelser|Nej |Ja (kun mail) |
|Anbefalinger, politikværktøjstip og brugertilsidesættelser|Ja |Nej |
|Simuleringstilstand|Nej |Ja |
|Exchange vedhæftede filer kontrolleres for betingelser|Nej | Ja|
|Anvend visuelle markeringer |Ja |Ja (kun mail) |
|Tilsidesæt IRM-kryptering, der er anvendt uden et navn|Ja, hvis brugeren har minimumsretten til eksport |Ja (kun mail) |
|Navn på indgående mail|Nej |Ja|
|Tildel en Rights Management-ejer til mails, der er sendt fra en anden organisation |Nej |Ja|
|Erstat eksisterende mærkat med samme eller lavere prioritet for mails |Nej |Ja (kan konfigureres)|

\* Automatisk mærkning er i øjeblikket ikke tilgængelig i alle områder på grund af en backend-Azure-afhængighed. Hvis din lejer ikke kan understøtte denne funktionalitet, er fanen **Automatisk mærkning** ikke synlig på Microsoft Purview-overholdelsesportalen. Du kan få flere oplysninger under [Tilgængelighed af Azure-afhængighed efter land](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Hvordan flere betingelser evalueres, når de gælder for mere end én etiket

Etiketterne sorteres til evaluering i henhold til deres position, som du angiver i politikken: Den etiket, der placeres først, har den laveste placering (mindst følsom), og den sidst placerede etiket har den højeste placering (mest følsomme). Du kan få flere oplysninger om prioritet under [Mærkatprioritet (order matters)](sensitivity-labels.md#label-priority-order-matters).

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Konfigurer ikke en overordnet etiket, der skal anvendes automatisk eller anbefales

Husk, at du ikke kan anvende en overordnet etiket (en etiket med undermærkater) på indhold. Sørg for, at du ikke konfigurerer et overordnet navn, så det anvendes automatisk eller anbefales i Office apps, og vælg ikke et overordnet navn til en politik for automatisk mærkning. Hvis du gør det, anvendes den overordnede mærkat ikke på indhold.

Hvis du vil bruge automatisk mærkning med undermærkater, skal du sørge for at publicere både den overordnede etiket og undermærkaten.

Du kan få flere oplysninger om overordnede navne og undermærkater [under Undermærkater (grupperingsnavne).](sensitivity-labels.md#sublabels-grouping-labels)

## <a name="will-an-existing-label-be-overridden"></a>Bliver en eksisterende etiket tilsidesat?

> [!NOTE]
> Med en indstilling, der er tilføjet for nylig for politik for automatisk mærkning af mails, kan du angive, at en matchende følsomhedsmærkat altid tilsidesætter en eksisterende mærkat.

Standardfunktionsmåde for, om automatisk mærkning tilsidesætter et eksisterende navn:

- Når indholdet er blevet navngivet manuelt, erstattes denne etiket ikke af automatisk mærkning.

- Automatisk mærkning erstatter en [følsomhedsmærkat med lavere prioritet](sensitivity-labels.md#label-priority-order-matters) , der blev anvendt automatisk, men ikke en mærkat med højere prioritet.
    
    > [!TIP]
    > Følsomhedsmærkaten øverst på listen på Microsoft Purview-overholdelsesportalen hedder f.eks. **Offentlig** med et ordrenummer (prioritet) på 0, og følsomhedsmærkaten nederst på listen har navnet **Meget fortroligt** med et ordrenummer (prioritet 4). Mærkaten **Meget fortroligt** kan tilsidesætte mærkaten **Offentlig** , men ikke omvendt.

Kun for politikker for automatisk mærkning af mails kan du vælge en indstilling, der altid skal tilsidesætte en eksisterende følsomhedsmærkat, uanset hvordan den blev anvendt.

|Eksisterende navn |Tilsidesæt med etiketindstilling: Automatisk mærkning af filer og mails  |Tilsidesæt med politik: Automatisk mærkning|
|:-----|:-----|:-----|
|Manuelt anvendt, en hvilken som helst prioritet|Word, Excel, PowerPoint: Nej <br /><br> Outlook: Nej  |SharePoint og OneDrive: Nej <br /><br> Exchange: Nej som standard, men kan konfigureres |
|Automatisk anvendt eller standardmærkat fra politik, lavere prioritet |Word, Excel, PowerPoint: Ja <br /><br> Outlook: Ja | SharePoint og OneDrive: Ja <br /><br> Exchange: Ja |
|Automatisk anvendt eller standardmærkat fra politik, højere prioritet |Word, Excel, PowerPoint: Nej <br /><br> Outlook: Nej |SharePoint og OneDrive: Nej <br /><br> Exchange: Nej som standard, men kan konfigureres |

Den konfigurerbare indstilling for politikker for automatisk mærkning af mails findes på siden **Yderligere indstillinger for mail** . Denne side vises, når du har valgt en følsomhedsmærkat for en politik for automatisk mærkning, der indeholder Exchange placering.

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Sådan konfigurerer du automatisk mærkning for Office apps

Hvis du vil have indbygget mærkning i Office apps, skal du kontrollere de [minimumversioner, der kræves](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) til automatisk mærkning i Office apps.

Azure Information Protection unified labeling-klienten understøtter kun automatisk mærkning for indbyggede og brugerdefinerede følsomme infotyper og understøtter ikke klassificeringstyper, der kan oplæres, eller følsomme infotyper, der bruger EDM (Exact Data Match) eller navngivne enheder.

Indstillingerne for automatisk mærkning af Office apps er tilgængelige, når du [opretter eller redigerer en følsomhedsmærkat](create-sensitivity-labels.md). Sørg for **, at Filer & mails** er valgt for etikettens område:

![Indstillinger for følsomhedsmærkatområde for filer og mails.](../media/filesandemails-scope-options-sensitivity-label.png)

Når du bevæger dig gennem konfigurationen, kan du se siden **Automatisk mærkning af filer og mails** , hvor du kan vælge på en liste over følsomme infotyper eller klassificeringer, der kan oplæres:

![Etiketbetingelser for automatisk mærkning i Office apps.](../media/sensitivity-labels-conditions.png)

Når denne følsomhedsmærkat anvendes automatisk, får brugeren vist en meddelelse i deres Office-app. Eksempel:

![Meddelelse om, at der automatisk er anvendt en mærkat i et dokument.](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Konfiguration af følsomme oplysningstyper for en etiket

Når du vælger indstillingen **Følsomme oplysningstyper** , får du vist den samme liste over typer af følsomme oplysninger, som når du opretter en DLP-politik (forebyggelse af datatab). Så du kan f.eks. automatisk anvende mærkaten Meget fortroligt på indhold, der indeholder kundernes personlige oplysninger, f.eks. kreditkortnumre, cpr-numre eller pasnumre:

![Følsomme oplysningstyper til automatisk mærkning i Office apps.](../media/sensitivity-labels-sensitive-info-types.png)

På samme måde som når du konfigurerer DLP-politikker, kan du tilpasse din betingelse ved at ændre antallet af forekomster og matche nøjagtigheden. Eksempel:

![Indstillinger for matchnøjagtighed og antal forekomster.](../media/sit-confidence-level.png)

Du kan få mere at vide om disse konfigurationsindstillinger i dokumentationen til DLP: [Justering af regler for at gøre dem nemmere eller sværere at matche](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Følsomme informationstyper har to forskellige måder at definere de maksimale antal parametre for entydige forekomster på. Hvis du vil vide mere, skal du se [Antal understøttede værdier for SIT.](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit)

På samme måde som med konfiguration af DLP-politik kan du vælge, om en betingelse skal registrere alle følsomme oplysningstyper eller blot én af dem. Hvis du vil gøre dine betingelser mere fleksible eller komplekse, kan du tilføje [grupper og bruge logiske operatorer mellem grupperne](data-loss-prevention-policies.md).

> [!NOTE]
> Automatisk mærkning baseret på brugerdefinerede følsomme oplysningstyper gælder kun for nyligt oprettet eller ændret indhold i OneDrive og SharePoint og ikke for eksisterende indhold. Denne begrænsning gælder også for politi til automatisk mærkning.

#### <a name="custom-sensitive-information-types-with-exact-data-match"></a>Brugerdefinerede typer følsomme oplysninger med nøjagtigt datamatch

Du kan konfigurere en følsomhedsmærkat til at bruge [nøjagtige datamatchbaserede typer følsomme oplysninger](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) for brugerdefinerede typer følsomme oplysninger. I øjeblikket skal du dog også angive mindst én type følsomme oplysninger, der ikke bruger EDM. Det kan f.eks. være en af de indbyggede typer følsomme oplysninger, f.eks **. kreditkortnummer**.

Hvis du konfigurerer en følsomhedsmærkat med kun EDM for betingelser for følsomme oplysninger, deaktiveres indstillingen for automatisk mærkning automatisk for mærkaten.

### <a name="configuring-trainable-classifiers-for-a-label"></a>Konfiguration af klassificeringer, der kan oplæres, for en etiket

Hvis du bruger denne indstilling med Microsoft 365 Apps til Windows version 2106 eller nyere eller Microsoft 365 Apps til Mac version 16.50 eller nyere, skal du sørge for, at du har publiceret i din lejer mindst én anden følsomhedsmærkat, der er konfigureret til automatisk mærkning og [indstillingen følsomme infotyper](#configuring-sensitive-info-types-for-a-label). Dette krav er ikke nødvendigt, når du bruger nyere versioner på disse platforme.

Når du vælger indstillingen **Klassificeringer, der kan oplæres** , skal du vælge en eller flere af de forudoplærte eller brugerdefinerede klassificeringer, der kan oplæres:

![Indstillinger for klassificeringer og følsomhedsmærkater, der kan oplæres.](../media/sensitivity-labels-classifers.png)

> [!CAUTION]
> Vi udfaser den prækvalificerede klassificering af **stødende sprog** , fordi den har produceret et højt antal falske positiver. Brug ikke denne klassificering, og hvis du i øjeblikket bruger den, anbefaler vi, at du fjerner dine forretningsprocesser fra den og i stedet bruger de forududlærte klassificeringer **målrettet chikane**, **bandeord** og **trussel** .

Du kan finde flere oplysninger om disse klassificeringer under [Få mere at vide om klassificeringer, der kan oplæres](classifier-learn-about.md).

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a>Anbefal, at brugeren anvender en følsomhedsmærkat

Hvis du foretrækker det, kan du anbefale dine brugere, at de anvender mærkaten. Med denne indstilling kan brugerne acceptere klassificeringen og eventuel tilknyttet beskyttelse eller afvise anbefalingen, hvis mærkaten ikke er egnet til deres indhold.

![Mulighed for at anbefale en følsomhedsmærkat til brugere.](../media/Sensitivity-labels-Recommended-label-option.png)

Her er et eksempel på en prompt fra Azure Information Protection Unified Labeling-klienten, når du konfigurerer en betingelse for at anvende en mærkat som en anbefalet handling med et brugerdefineret politiktip. Du kan vælge, hvilken tekst der skal vises i politiktip.

![Spørg, om der skal anvendes et anbefalet navn.](../media/Sensitivity-label-prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a>Når der anvendes automatiske eller anbefalede mærkater

Implementeringen af automatisk og anbefalet mærkning i Office apps afhænger af, om du bruger mærkning, der er indbygget i Office, eller Azure Information Protection Unified-mærkatklienten. I begge tilfælde:

- Du kan ikke bruge automatisk mærkning til dokumenter og mails, der tidligere blev manuelt mærket eller tidligere automatisk mærket med en højere følsomhed. Husk, at du kun kan anvende en enkelt følsomhedsmærkat på et dokument eller en mail (ud over en enkelt opbevaringsmærkat).

- Du kan ikke bruge anbefalet mærkning til dokumenter eller mails, der tidligere er mærket med en højere følsomhed. Når indholdet allerede er mærket med en højere følsomhed, kan brugeren ikke se prompten med anbefalingen og politiktip.

Specifik til indbygget mærkning:

- Det er ikke alle Office apps, der understøtter automatisk (og anbefalet) mærkning. Du kan få flere oplysninger under [Understøttelse af egenskaber for følsomhedsmærkat i apps](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- For anbefalede mærkater i skrivebordsversionerne af Word markeres det følsomme indhold, der udløste anbefalingen, så brugerne kan gennemse og fjerne det følsomme indhold i stedet for at anvende den anbefalede følsomhedsmærkat.

- Du kan finde oplysninger om, hvordan disse mærkater anvendes i Office apps, f.eks. skærmbilleder, og hvor følsomme oplysninger registreres, under [Anvend eller anbefal automatisk følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/office/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).

Specifik til Azure Information Protection Unified Labeling-klienten:

- Automatisk og anbefalet mærkning gælder for Word, Excel og PowerPoint, når du gemmer et dokument, og for at Outlook, når du sender en mail.

- Hvis Outlook skal understøtte anbefalet mærkning, skal du først konfigurere en [avanceret politikindstilling](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).

- Følsomme oplysninger kan registreres i brødtekst i dokumenter og mails og i sidehoveder og sidefødder – men ikke i emnelinjen eller vedhæftede filer i mails.

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a>Sådan konfigurerer du politikker for automatisk mærkning for SharePoint, OneDrive og Exchange

Sørg for, at du er opmærksom på forudsætningerne, før du konfigurerer politikker for automatisk mærkning.

### <a name="prerequisites-for-auto-labeling-policies"></a>Forudsætninger for politikker for automatisk mærkning

- Simuleringstilstand:
  - Overvågning af Microsoft 365 skal være aktiveret. Hvis du har brug for at aktivere overvågning, eller hvis du ikke er sikker på, om overvågning allerede er aktiveret, skal du se [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).
  - Hvis du vil have vist fil- eller mailindhold i kildevisningen, skal du have rollen **Indholdsfremviser til dataklassificering**, som er inkluderet i rollegruppen **Indholdsfremviser i Indholdsoversigt** eller **Information Protection** og **Information Protection Rollegrupper for efterforskere** (i øjeblikket i prøveversion). Uden den påkrævede rolle kan du ikke se indholdsruden, når du vælger et element under fanen **Matchende elementer** . Globale administratorer har ikke denne rolle som standard.

- Sådan navngiver du filer automatisk i SharePoint og OneDrive:
  - Du har [aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).
  - På det tidspunkt, hvor politikken for automatisk mærkning kører, må filen ikke være åben af en anden proces eller bruger. En fil, der er tjekket ud til redigering, er omfattet af denne kategori.

- Hvis du planlægger at bruge [brugerdefinerede typer følsomme oplysninger](sensitive-information-type-learn-about.md) i stedet for de indbyggede følsomhedstyper:
  - Brugerdefinerede typer af oplysninger om følsomhed gælder kun for indhold, der tilføjes eller ændres i SharePoint eller OneDrive, når de brugerdefinerede typer af følsomhedsoplysninger er oprettet.
  - Hvis du vil teste nye brugerdefinerede følsomme oplysningstyper, skal du oprette dem, før du opretter politikken for automatisk mærkning og derefter oprette nye dokumenter med eksempeldata til test.

- En eller flere følsomhedsmærkater [, der er oprettet og publiceret](create-sensitivity-labels.md) (til mindst én bruger), som du kan vælge til politikker for automatisk mærkning. For disse mærkater:
  - Det er ligegyldigt, om mærkatindstillingen for automatisk mærkning i Office apps er slået til eller fra, fordi denne etiketindstilling supplerer politikker for automatisk mærkning, som forklaret i indledningen.
  - Hvis de navne, du vil bruge til automatisk mærkning, er konfigureret til at bruge visuelle markeringer (sidehoveder, sidefødder, vandmærker), skal du være opmærksom på, at disse ikke anvendes på dokumenter.
  - Hvis mærkaterne anvender [kryptering](encryption-sensitivity-labels.md):
    - Når politikken for automatisk mærkning indeholder placeringer for SharePoint eller OneDrive, skal mærkaten konfigureres for indstillingen **Tildel tilladelser nu**.
    - Når politikken for automatisk mærkning kun er til Exchange, kan mærkaten konfigureres for enten **Tildel tilladelser nu** eller **Lad brugere tildele tilladelser** (for indstillingerne Videresend ikke eller Encrypt-Only).

### <a name="learn-about-simulation-mode"></a>Få mere at vide om simuleringstilstand

Simuleringstilstand er unik for politikker til automatisk mærkning og vævet ind i arbejdsprocessen. Du kan ikke automatisk navngive dokumenter og mails, før din politik har kørt mindst én simulering.

Simuleringstilstand understøtter op til 1.000.000 matchende filer. Hvis der matches mere end dette antal filer fra en politik for automatisk mærkning, kan du ikke aktivere politikken for at anvende mærkaterne. I dette tilfælde skal du omkonfigurere politikken for automatisk mærkning, så der matches færre filer, og køre simulering igen. Dette maksimum på 1.000.000 matchede filer gælder kun for simuleringstilstand og ikke for en politik for automatisk mærkning, der allerede er slået til for at anvende følsomhedsmærkater.

Arbejdsproces for en politik for automatisk mærkning:

1. Opret og konfigurer en politik for automatisk mærkning.

2. Kør politikken i simuleringstilstand, hvilket kan tage 12 timer at fuldføre. Den fuldførte simulering udløser en mailmeddelelse, der sendes til den bruger, der er konfigureret til at modtage [aktivitetsbeskeder](alert-policies.md).

3. Gennemse resultaterne, og om nødvendigt afgræns din politik. Du skal muligvis redigere politikreglerne for at reducere falske positiver eller fjerne nogle websteder, så antallet af matchede filer ikke overstiger 1.000.000. Kør simuleringstilstanden igen, og vent på, at den fuldføres igen.

4. Gentag trin 3 efter behov.

5. Udrul i produktion.

Den simulerede installation kører som WhatIf-parameteren for PowerShell. Du får vist resultater, der er rapporteret, som om politikken for automatisk mærkning har anvendt den valgte etiket ved hjælp af de regler, du har defineret. Du kan derefter tilpasse dine regler for nøjagtighed, hvis det er nødvendigt, og køre simuleringen igen. Men da automatisk mærkning af Exchange gælder for mails, der sendes og modtages i stedet for mails, der er gemt i postkasser, skal du ikke forvente, at resultaterne for mail i en simulering er konsistente, medmindre du kan sende og modtage præcis de samme mails.

I simuleringstilstand kan du også gradvist øge omfanget af politikken for automatisk mærkning før udrulningen. Du kan f.eks. starte med en enkelt placering, f.eks. et SharePoint websted, med et enkelt dokumentbibliotek. Derefter skal du med iterative ændringer øge omfanget til flere websteder og derefter til en anden placering, f.eks. OneDrive.

Endelig kan du bruge simuleringstilstand til at angive en tilnærmelse af den tid, det tager at køre politikken for automatisk mærkning, for at hjælpe dig med at planlægge og planlægge, hvornår du skal køre den uden simuleringstilstand.

### <a name="creating-an-auto-labeling-policy"></a>Oprettelse af en politik for automatisk mærkning

1. Gå til følsomhedsmærkater på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>:

    - **Løsninger** >  **Information Protection**

    Hvis du ikke kan se denne indstilling med det samme, skal du først vælge **Vis alle**.

2. Vælg fanen **Med automatisk mærkat** :

    ![Fanen Med automatisk etiket.](../media/auto-labeling-tab.png)

    > [!NOTE]
    > Hvis du ikke kan se fanen Automatisk mærkning, er denne funktionalitet i øjeblikket ikke tilgængelig i dit område på grund af en Backend **Azure-afhængighed** . Du kan få flere oplysninger under [Tilgængelighed af Azure-afhængighed efter land](/troubleshoot/azure/general/dependency-availability-by-country).

3. Vælg **+ Opret politik for automatisk mærkning**. Dette starter konfigurationen Ny politik:

    ![Ny politikkonfiguration til automatisk mærkning.](../media/auto-labeling-wizard.png)

4. For siden **Vælg de oplysninger, som mærkaten skal anvendes på**: Vælg en af skabelonerne, f.eks **. Økonomisk** eller **Beskyttelse af personlige oplysninger**. Du kan afgrænse din søgning ved hjælp af rullelisten **Vis indstillinger** . Du kan også vælge **Brugerdefineret politik** , hvis skabelonerne ikke opfylder dine krav. Vælg **Næste**.

5. For siden **Navngiv din politik for automatisk mærkning**: Angiv et entydigt navn og eventuelt en beskrivelse for at hjælpe med at identificere det automatisk anvendte navn, de placeringer og betingelser, der identificerer det indhold, der skal navngives.

6. På siden **Vælg de placeringer, hvor du vil anvende etiketten**: Vælg, og angiv placeringer for Exchange, SharePoint og OneDrive. Hvis du ikke vil beholde standarden for **Alle** , der er inkluderet for dine valgte placeringer, skal du vælge linket for at vælge bestemte instanser, der skal medtages, eller vælge linket for at vælge bestemte forekomster, der skal udelades. Vælg derefter **Næste**.

    ![Vælg siden Placeringer til konfiguration af automatisk mærkning.](../media/locations-auto-labeling-wizard.png)
    
    Hvis du ændrer standardindstillingerne ved hjælp af **Inkluderet** eller **Udeladt**:
    
    - For den **Exchange** placering anvendes politikken i henhold til afsenderadressen for de angivne modtagere. For det meste vil du beholde standardindstillingen **Alle** , der er inkluderet **i Ingen** udeladt. Denne konfiguration er velegnet, selvom du tester for et undersæt af brugere. I stedet for at angive dit undersæt af brugere her, kan du bruge de avancerede regler i næste trin til at konfigurere betingelser til at inkludere eller udelade modtagere i din organisation. Ellers kan du ændre standardindstillingerne her:
        -  Hvis du ændrer standarden for **Alle** inkluderet og i stedet vælger bestemte brugere eller grupper, vil mails, der sendes uden for din organisation, være undtaget fra politikken. 
        -  Hvis du bevarer standardindstillingen **Alle** inkluderet, men angiver brugere eller grupper, der skal udelades, vil mails, som disse udeladte brugere sender, være undtaget fra politikken, men ikke mail, som de modtager.
    
    - Hvis du vil have OneDrive konti, skal du se [Hent en liste over alle url-adresser til OneDrive i din organisation](/onedrive/list-onedrive-urls) for at hjælpe dig med at angive individuelle OneDrive konti, der skal medtages eller udelades.

7. På siden **Konfigurer almindelige eller avancerede regler** : Bevar standarden for **Fælles regler** for at definere regler, der identificerer indhold, der skal navngives på tværs af alle de valgte placeringer. Hvis du har brug for forskellige regler pr. placering, herunder flere indstillinger for Exchange, skal du vælge **Avancerede regler**. Vælg derefter **Næste**.

    I reglerne bruges betingelser, der omfatter følsomme oplysningstyper og delingsindstillinger:
    - I forbindelse med følsomme oplysningstyper kan du vælge både indbyggede og brugerdefinerede typer følsomme oplysninger.
    - For de delte indstillinger kan du kun vælge **med personer i min organisation** eller **med personer uden for min organisation**.

    Hvis din placering er **Exchange**, og du har valgt **Avancerede regler**, er der andre betingelser, som du kan vælge:
    - Afsenderens IP-adresse er
    - Modtagerdomænet er
    - Modtageren er
    - Filtypenavnet for den vedhæftede fil er
    - Den vedhæftede fil er beskyttet med adgangskode
    - Indhold fra en vedhæftet fil kunne ikke scannes
    - Indholdet af en vedhæftet fil i en hvilken som helst mail blev ikke scannet
    - Header matcher mønstre
    - Emne matcher mønstre
    - Modtageradressen indeholder ord
    - Modtageradressen stemmer overens med mønstre
    - Afsenderadresse matcher mønstre
    - Afsenderdomænet er
    - Modtageren er medlem af
    - Afsenderen er

    For hver af disse betingelser kan du derefter angive undtagelser.

8. Afhængigt af dine tidligere valg har du nu mulighed for at oprette nye regler ved hjælp af betingelser og undtagelser.

    Konfigurationsindstillingerne for følsomme oplysningstyper er de samme som dem, du vælger til automatisk mærkning af Office apps. Hvis du har brug for flere oplysninger, skal du se [Konfiguration af følsomme oplysningstyper for en mærkat](#configuring-sensitive-info-types-for-a-label).

    Når du har defineret alle de regler, du har brug for, og bekræftet, at deres status er slået til, skal du vælge **Næste** for at gå videre til at vælge en etiket, der skal anvendes automatisk.

9. På siden **Vælg en mærkat, der skal anvendes automatisk** : Vælg **+ Vælg en etiket**, vælg en etiket i ruden **Vælg en følsomhedsmærkat** , og vælg derefter **Næste**.

10. Hvis din politik indeholder Exchange placering: Angiv valgfri konfigurationer på siden **Yderligere indstillinger for mail**:
    
    - **Erstat automatisk eksisterende mærkater med samme eller lavere prioritet**: Gælder for både indgående og udgående mails, når du vælger denne indstilling, sikrer det, at der altid anvendes en matchende følsomhedsmærkat. Hvis du ikke vælger denne indstilling, anvendes der ikke en matchende følsomhedsmærkat på mails, der har en eksisterende følsomhedsmærkat med [en højere prioritet](sensitivity-labels.md#label-priority-order-matters) , eller som er manuelt mærket.
    
    - **Anvend kryptering på mails, der modtages uden for din organisation**: Når du vælger denne indstilling, skal du tildele en [Rights Management-ejer](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) for at sikre, at en autoriseret person i organisationen har [brugsrettigheder](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) til fuld kontrol for mails, der er sendt fra din uden for organisationen, og dine politikmærkater med kryptering. Denne rolle kan være nødvendig for senere at fjerne krypteringen eller tildele forskellige brugsrettigheder til brugere i din organisation.
        
        For **Tildel en Rights Management-ejer** skal du angive en enkelt bruger efter en mailadresse, der ejes af din organisation. Angiv ikke en mailkontakt, en delt postkasse eller en gruppetype, da disse ikke understøttes for denne rolle.

10. På siden **Beslut, om du vil teste politikken nu eller senere** : Vælg **Kør politik i simuleringstilstand** , hvis du er klar til at køre politikken for automatisk mærkning nu i simuleringstilstand. Ellers skal du vælge **Forlad politik slået fra**. Vælg **Næste**:

    ![Test politikken for automatisk mærkning, der er konfigureret.](../media/simulation-mode-auto-labeling-wizard.png)

11. På **oversigtssiden** : Gennemse konfigurationen af politikken for automatisk mærkning, foretag de nødvendige ændringer, og fuldfør konfigurationen.

Nu kan du på siden **Information** **ProtectionAuto-labeling** >  se din politik for automatisk mærkning i afsnittet **Simulering** eller **Fra**, afhængigt af om du har valgt at køre den i simuleringstilstand eller ej. Vælg din politik for at få vist detaljer om konfigurationen og status (f.eks. **kører politiksimulering stadig**). For politikker i simuleringstilstand skal du vælge fanen **Matchende elementer** for at se, hvilke mails eller dokumenter der opfylder de angivne regler.

Du kan ændre din politik direkte fra denne grænseflade:

- For en politik i afsnittet **Fra** skal du vælge knappen **Rediger politik** .

- For politik i afsnittet **Simulering** skal du vælge indstillingen **Rediger politik** øverst på siden fra en af fanerne:

    ![Rediger politikindstillingen for automatisk mærkning.](../media/auto-labeling-edit.png)

    Når du er klar til at køre politikken uden simulering, skal du vælge indstillingen **Slå politik** til.

Politikker for automatisk mærkning kører løbende, indtil de slettes. Nye og ændrede filer medtages f.eks. i de aktuelle politikindstillinger.

### <a name="monitoring-your-auto-labeling-policy"></a>Overvågning af politikken for automatisk mærkning

Når politikken for automatisk mærkning er slået til, kan du få vist status for mærkater for filer på de valgte SharePoint og OneDrive placeringer. Mails er ikke inkluderet i status for mærkat, fordi de automatisk er mærket, som de sendes.

Status for mærkning omfatter de filer, der skal mærkes af politikken, de filer, der er mærket inden for de seneste syv dage, og det samlede antal filer, der er mærket. På grund af den maksimale mærkat på 25.000 filer om dagen giver disse oplysninger dig indblik i den aktuelle status for mærkaten for din politik, og hvor mange filer der stadig skal mærkes.

Når du aktiverer din politik første gang, får du indledningsvist vist en værdi på 0 for filer, der skal forsynes med mærkater, indtil de nyeste data hentes. Disse statusoplysninger opdateres hver 48. time, så du kan forvente at se de mest aktuelle data om hver anden dag. Når du vælger en politik for automatisk mærkning, kan du se flere oplysninger om politikken i en pop op-rude, som omfatter status for mærkat på de ti øverste websteder. Oplysningerne i denne pop op-rude kan være mere aktuelle end de aggregerede politikoplysninger, der vises på hovedsiden **med automatisk mærkning** .

Du kan også se resultaterne af politikken for automatisk mærkning ved hjælp af [Indholdsoversigt](data-classification-content-explorer.md) , når du har de nødvendige [tilladelser](data-classification-content-explorer.md#permissions):

- **Med indholdsoversigtens listefremviser-rollegruppe** kan du se en fils navn, men ikke filens indhold.
- **Rollegruppen Indholdsoversigt i Indholdsoversigt** og **Information Protection** og **Information Protection Undersøgere-rollegrupper** (i øjeblikket i prøveversion) giver dig mulighed for at se filens indhold.

> [!TIP]
> Du kan også bruge Indholdsoversigt til at identificere placeringer, der har dokumenter med følsomme oplysninger, men som ikke har mærkat. Ved hjælp af disse oplysninger kan du overveje at føje disse placeringer til politikken for automatisk mærkning og inkludere de identificerede følsomme oplysningstyper som regler.

### <a name="use-powershell-for-auto-labeling-policies"></a>Brug PowerShell til politikker for automatisk mærkning

Du kan bruge [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell) til at oprette og konfigurere politikker for automatisk mærkning. Det betyder, at du fuldt ud kan scripte oprettelsen og vedligeholdelsen af politikkerne for automatisk mærkning, hvilket også giver en mere effektiv metode til angivelse af flere URL-adresser til OneDrive og SharePoint placeringer.

Før du kører kommandoerne i PowerShell, skal du først [oprette forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

Sådan opretter du en ny politik for automatisk mærkning:

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Denne kommando opretter en politik for automatisk mærkning for et SharePoint websted, du angiver. Hvis du vil have en OneDrive placering, skal du i stedet bruge parameteren *OneDriveLocation*.

Sådan føjer du flere websteder til en eksisterende politik for automatisk mærkning:

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Denne kommando angiver de nye SharePoint URL-adresser i en variabel, der derefter føjes til en eksisterende politik for automatisk mærkning. Hvis du vil tilføje OneDrive placeringer i stedet, skal du bruge parameteren *AddOneDriveLocation* med en anden variabel, f.eks. *$OneDriveLocations*.

Sådan opretter du en ny politikregel for automatisk mærkning:

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

I forbindelse med en eksisterende politik for automatisk mærkning opretter denne kommando en ny politikregel for at registrere den følsomme informationstype for **SSN (Us Social Security Number),** som har enheds-id'et a44669fe-0d48-453d-a9b1-2cc83f2cba77. Hvis du vil finde enheds-id'erne for andre følsomme oplysningstyper, skal du se [Objektdefinitioner for følsomme oplysninger](sensitive-information-type-entity-definitions.md).

Du kan finde flere oplysninger om de PowerShell-cmdlet'er, der understøtter politikker for automatisk mærkning, deres tilgængelige parametre og nogle eksempler, i følgende cmdlet hjælp:

- [Get-AutoSensitivityLabelPolicy](/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelPolicy](/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelRule](/powershell/module/exchange/new-autosensitivitylabelrule)
- [Remove-AutoSensitivityLabelPolicy](/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [Remove-AutoSensitivityLabelRule](/powershell/module/exchange/remove-autosensitivitylabelrule)
- [Set-AutoSensitivityLabelPolicy](/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [Set-AutoSensitivityLabelRule](/powershell/module/exchange/set-autosensitivitylabelrule)

## <a name="tips-to-increase-labeling-reach"></a>Tips for at øge rækkevidden af mærkater

Selvom automatisk mærkning er en af de mest effektive måder at klassificere, navngive og beskytte Office filer, som din organisation ejer, skal du kontrollere, om du kan supplere den med en af følgende metoder for at øge rækkevidden af mærkater:

- Med SharePoint Syntex kan du [anvende en følsomhedsmærkat på en model til dokumentforståelse](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model), så identificerede dokumenter i et SharePoint bibliotek automatisk mærkes.

- Når du bruger [Azure Information Protection Unified-mærkatklienten](/azure/information-protection/rms-client/aip-clientv2):

  - For filer i datalagre i det lokale miljø, f.eks. netværksshares og SharePoint serverbiblioteker: Brug [scanneren](/azure/information-protection/deploy-aip-scanner) til at finde følsomme oplysninger i disse filer, og mærk dem korrekt. Hvis du planlægger at overføre eller overføre disse filer til SharePoint i Microsoft 365, kan du bruge scanneren til at navngive filerne, før du flytter dem til cloudmiljøet.

  - Hvis du har brugt en anden etiketløsning, før du bruger følsomhedsmærkater: Brug PowerShell og [en avanceret indstilling til at genbruge mærkater](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#migrate-labels-from-secure-islands-and-other-labeling-solutions) fra disse løsninger.

- Tilskynd [manuel mærkning,](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) når brugerne har fået oplæring af, hvilke følsomhedsmærkater der skal anvendes. Når du er sikker på, at brugerne forstår, hvilken mærkat der skal anvendes, kan du overveje at konfigurere en standardmærkat og obligatorisk mærkning som [politikindstillinger](sensitivity-labels.md#what-label-policies-can-do).

Overvej desuden at [markere nye filer som følsomme som standard](/sharepoint/sensitive-by-default) i SharePoint for at forhindre gæster i at få adgang til nyligt tilføjede filer, indtil mindst én DLP-politik scanner indholdet af filen.
