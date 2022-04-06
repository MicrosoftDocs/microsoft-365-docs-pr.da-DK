---
title: Anvend automatisk en følsomhedsmærkat på indhold i Microsoft 365
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
description: Når du opretter et følsomhedsmærkat, kan du automatisk tildele en etiket til filer og mails, eller du kan bede brugerne om at vælge den etiket, du anbefaler.
ms.openlocfilehash: 80f3b5c69e482301dd8c4e926959087c7149a529
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499655"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>Anvend en følsomhedsmærkat på indhold automatisk

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Du kan finde oplysninger om automatisk anvendelse af et følsomhedsmærkat i Azure-visning under [Mærkning i Azure-visning](/azure/purview/create-sensitivity-label).

Når du opretter en følsomhedsmærkat, kan du automatisk tildele den pågældende etiket til filer og mails, når den opfylder de betingelser, du angiver.

Denne mulighed for automatisk at anvende følsomhedsmærkater på indhold er vigtig, fordi:

- Du behøver ikke at oplære dine brugere, hvornår de skal bruge hver af dine klassificeringer.

- Du behøver ikke at stole på, at brugerne klassificerer alt indhold korrekt.

- Brugere behøver ikke længere at kende til dine politikker – de kan i stedet fokusere på deres arbejde.

Der er to forskellige metoder til automatisk at anvende en følsomhedsmærkat på indhold i Microsoft 365:

- **Mærkning på klientsiden**, når brugere redigerer dokumenter eller skriver (også svar eller videresender) mails: Brug en etiket, der er konfigureret til automatisk mærkning af filer og mails (omfatter Word, Excel, PowerPoint og Outlook).

    Denne metode understøtter anbefaling af et navn til brugerne og til automatisk anvendelse af en etiket. Men i begge tilfælde beslutter brugeren, om han eller hun skal acceptere eller afvise etiketten for at sikre korrekt mærkat for indholdet. Denne etiket på klientsiden har minimal forsinkelse for dokumenter, da etiketten kan anvendes, selv før dokumentet gemmes. Det er dog ikke alle klientapps, der understøtter automatisk mærkning. Denne funktion understøttes af indbygget mærkning med nogle versioner [af Office](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) og også Azure Information Protection samlet etiketklient.

    Du kan finde [konfigurationsinstruktioner under Sådan konfigureres automatisk mærkater Office-apps](#how-to-configure-auto-labeling-for-office-apps) på denne side.

- Mærkning på tjenestesiden, når indhold allerede er gemt **(i SharePoint eller OneDrive) eller sendt via mail (behandlet af Exchange Online)**: Brug en politik for automatisk mærkatning.
    
    Du hører muligvis også denne metode kaldet automatisk mærkning af indeværende data (dokumenter i SharePoint og OneDrive) og data under overførsel (mails, der sendes eller modtages af Exchange). For Exchange indeholder den ikke in restmails (postkasser).
    
    Da denne mærkning anvendes af tjenester i stedet for af programmer, behøver du ikke at bekymre dig om, hvilke apps brugerne har og hvilken version. Derfor er denne funktion umiddelbart tilgængelig i hele organisationen og egnet til skalering. Politikker for automatisk mærkning understøtter ikke anbefalet mærkat, da brugeren ikke interagerer med mærkningsprocessen. I stedet kører administratoren politikkerne i simulering for at sikre den korrekte mærkat for indhold, før den faktisk anvender etiketten.

    Du kan finde konfigurationsinstruktioner i Sådan konfigureres politikker [for SharePoint, OneDrive navne og Exchange](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) på denne side.
    
    Specifikt for automatisk mærkatering til SharePoint og OneDrive:
    
    - Office filer til Word (.docx), PowerPoint (.pptx) og Excel (.xlsx) understøttes.
        - Disse filer kan automatisk navnmærkes under mærkater, før eller efter politikkerne for automatisk mærkatering oprettes. Filer kan ikke navnmærkes automatisk, hvis de er en del af en åben session (filen er åben).
        - I øjeblikket understøttes vedhæftede filer i listeelementer ikke, og de bliver ikke navnmærket automatisk.
    - Maksimalt 25.000 automatisk navnerede filer i din lejer pr. dag.
    - Maksimalt 100 politikker for automatisk mærkning pr. lejer, hver målretning på op til 100 websteder (SharePoint eller OneDrive), når de angives individuelt. Du kan også angive alle websteder, og denne konfiguration er undtaget fra maksimum 100 websteder.
    - Eksisterende værdier for ændret, ændret af, og datoen ændres ikke som et resultat af politikker for automatisk mærkning – for både simuleringstilstand og når der anvendes etiketter.
    - Når etiketten anvender kryptering, er [udstederen af Rights Management og Rights Management ejeren](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) den konto, der senest har ændret filen. Hvis denne konto ikke længere er Azure Active Directory, anvendes navnet ikke, fordi disse værdier ikke kan angives.

    Specifik for automatisk mærkat for Exchange:
    
    - I modsætning til manuel mærkat eller automatisk mærkater med Office-apps scannes vedhæftede PDF-filer samt vedhæftede Office også for de betingelser, du angiver i din politik for automatisk mærkatmærkning. Når der er et match, mærkes mailen, men ikke den vedhæftede fil.
        - For PDF-filer, hvis etiketten anvender kryptering, krypteres disse filer ved hjælp [af ome Office 365 (Message Encryption),](ome.md) når din lejer er aktiveret til [vedhæftede PDF-filer](ome-faq.yml#are-pdf-file-attachments-supported-).
        - Disse Office filer, Word, PowerPoint og Excel understøttes. Hvis etiketten anvender kryptering, krypteres de ved hjælp Office 365 [ome (Message Encryption](ome.md)).
    - Hvis du har Exchange regler for mailflow eller forebyggelse af datatab (DLP), der anvender IRM-kryptering: Når indhold identificeres af disse regler eller politikker og en politik for automatisk mærkning, anvendes etiketten. Hvis den etiket anvender kryptering, ignoreres IRM-indstillingerne Exchange regler for mailflow eller DLP-politikker. Men hvis den pågældende etiket ikke anvender kryptering, anvendes IRM-indstillingerne fra regler for mailflow eller DLP-politikker ud over navnet.
    - Mail, der har IRM-kryptering uden etiket, erstattes af en etiket med nogen krypteringsindstillinger, når der findes et match, ved hjælp af automatisk mærkat.
    - Indgående mail mærkes, når der er et match med dine betingelser for automatisk mærkat. Hvis denne etiket er konfigureret [til kryptering](encryption-sensitivity-labels.md), anvendes denne kryptering altid, når afsenderen er fra din organisation. Som standard anvendes denne kryptering ikke, når afsenderen er uden for organisationen, men kan anvendes ved at konfigurere Flere indstillinger **for** mail og angive en ejer af Rights Management.
    - Når etiketten anvender kryptering, er [udstederen af Rights Management og Rights Management-ejeren](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) den person, der sender mailen, når afsenderen er fra din egen organisation. Når afsenderen er uden for organisationen, kan du angive en Rights Management-ejer for indgående mails, der er mærket og krypteret af din politik.
    - Hvis etiketten er konfigureret til at anvende dynamiske markeringer [, skal](sensitivity-labels-office-apps.md#dynamic-markings-with-variables) du være opmærksom på, at for indgående mails kan denne konfiguration medføre visning af navnene på personer uden for organisationen.

## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a>Sammenlign automatisk mærkning af Office apps med politikker for automatisk mærkning

Brug følgende tabel som en hjælp til at identificere forskelle i funktionsmåden for de to komplementære automatiske mærkningsmetoder:

|Funktion eller funktionsmåde|Etiketindstilling: Automatisk mærkning af filer og mails  |Politik: Automatisk mærkning|
|:-----|:-----|:-----|
|Appafhængighed|Ja ([minimumversioner](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)) |Nej \* |
|Begræns efter placering|Nej |Ja |
|Betingelser: Klassekammerater, der kan trænes|Ja |Nej |
|Betingelser: Indstillinger for deling og yderligere indstillinger for mail|Nej |Ja |
|Betingelser: Undtagelser|Nej |Ja (kun mail) |
|Anbefalinger, værktøjstip til politikker og brugertilsidesættelser|Ja |Nej |
|Simuleringstilstand|Nej |Ja |
|Exchange, der er kontrolleret for betingelser|Nej | Ja|
|Anvend visuelle markeringer |Ja |Ja (kun mail) |
|Tilsidesæt IRM-kryptering, der anvendes uden et navn|Ja, hvis brugeren har den mindste brugs rettighed til at eksportere |Ja (kun mail) |
|Navnmærke indgående mail|Nej |Ja|
|Tildele en Rights Management-ejer for mails, der sendes fra en anden organisation |Nej |Ja|
|Erstat eksisterende etiket med samme eller lavere prioritet for mails |Nej |Ja (kan konfigureres)|

\* Automatisk mærkning er i øjeblikket ikke tilgængelig i alle områder på grund af en backend Azure-afhængighed. Hvis din lejer ikke understøtter denne funktionalitet **, er fanen** Automatisk mærkning ikke synlig i overholdelsescenteret. Få mere at vide under [Tilgængelighed af Azure-afhængighed efter land](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Sådan evalueres flere betingelser, når de gælder for mere end én etiket

Etiketterne er sorteret efter deres placering i henhold til deres placering i politikken: Den første etiket har den laveste placering (mindst følsom), og den sidst placerede etiket har den højeste placering (mest følsom). Du kan finde flere oplysninger om prioritet under [Etiketprioritet (rækkefølge vigtig)](sensitivity-labels.md#label-priority-order-matters).

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Konfigurer ikke en overordnet etiket til at blive anvendt automatisk eller anbefalet

Husk, at du ikke kan anvende en overordnet etiket (en etiket med underlabels) til indhold. Sørg for, at du ikke konfigurerer en overordnet etiket, så den automatisk anvendes eller anbefales i Office-apps, og vælg ikke et overordnet navn til en politik for automatisk mærkatmærkning. Hvis du gør det, anvendes den overordnede etiket ikke på indholdet.

Hvis du vil bruge automatisk mærkater med undergrupper, skal du sørge for at publicere både det overordnede navn og undernavnet.

Du kan finde flere oplysninger om overordnede navne og undernavne [i Undernavne (grupperingsetiketter)](sensitivity-labels.md#sublabels-grouping-labels).

## <a name="will-an-existing-label-be-overridden"></a>Tilsidesættes en eksisterende etiket?

> [!NOTE]
> Med en nyligt tilføjet indstilling for automatisk mærkning af mail-politik kan du angive, at en matchende følsomhedsmærkat altid tilsidesætter en eksisterende etiket.

Standardfunktionsmåde for, om automatisk mærkat tilsidesætter en eksisterende etiket:

- Når indhold er blevet navngivet manuelt, bliver den pågældende etiket ikke erstattet af automatisk mærkat.

- Automatisk mærkning erstatter en [følsomhedsmærkat med lavere](sensitivity-labels.md#label-priority-order-matters) prioritet, som automatisk blev anvendt, men ikke en etiket med højere prioritet.
    
    > [!TIP]
    > Følsomhedsmærkatet øverst på listen i Overholdelsescenter kaldes f.eks. Offentlig med et  ordrenummer (prioritet) på 0, og følsomhedsmærkatet nederst på listen kaldes Meget fortroligt med et ordrenummer  (prioritet 4). Etiketten **Meget fortroligt** kan tilsidesætte den **offentlige** etiket, men ikke omvendt.

Ved politikker for automatisk mærkning af mail kan du vælge en indstilling, der altid tilsidesætter en eksisterende følsomhedsmærkat, uanset hvordan den er anvendt.

|Eksisterende etiket |Tilsidesæt med etiketindstilling: Automatisk mærkat for filer og mails  |Tilsidesæt med politik: Automatisk mærkning|
|:-----|:-----|:-----|
|Manuelt anvendt, enhver prioritet|Word, Excel, PowerPoint: Nej <br /><br> Outlook: Nej  |SharePoint og OneDrive: Nej <br /><br> Exchange: Nej som standard, men kan konfigureres |
|Automatisk anvendt etiket eller standardetiket fra politik, lavere prioritet |Word, Excel, PowerPoint: Ja <br /><br> Outlook: Ja | SharePoint og OneDrive: Ja <br /><br> Exchange: Ja |
|Automatisk anvendt etiket eller standardetiket fra politik, højere prioritet |Word, Excel, PowerPoint: Nej <br /><br> Outlook: Nej |SharePoint og OneDrive: Nej <br /><br> Exchange: Nej som standard, men kan konfigureres |

Den konfigurerbare indstilling for politikker for automatisk mærkatering af mail findes **på siden Yderligere indstillinger for** mail. Denne side vises, når du har valgt en følsomhedsmærkat for en automatisk mærkatpolitik, der omfatter Exchange placering.

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Sådan konfigurerer du automatisk mærkater til Office apps

For indbygget mærkning i Office skal du kontrollere [minimumversionerne](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps), der kræves for automatisk mærkning i Office apps.

Azure Information Protection samlet mærkatklient understøtter kun automatisk mærkning for indbyggede og brugerdefinerede følsomme oplysningstyper og understøtter ikke klassificeringer, der kan trænes, eller følsomme oplysningstyper, der bruger Nøjagtig dataoverensstemmelse (EDM) eller navngivne enheder.

Indstillingerne for automatisk mærkatering for Office apps er tilgængelige, når du [opretter eller redigerer en følsomhedsmærkat](create-sensitivity-labels.md). Sørg for **, & filer og** mails er markeret ud for etikettens omfang:

![Indstillinger for følsomhedsmærkatens omfang for filer og mails.](../media/filesandemails-scope-options-sensitivity-label.png)

Mens du bevæger dig gennem konfigurationen, kan du se siden Automatisk mærkning **af** filer og mails, hvor du kan vælge på en liste over følsomme oplysningstyper eller oplærende klassificeringer:

![Etiketbetingelser for automatisk mærkatering i Office apps.](../media/sensitivity-labels-conditions.png)

Når denne følsomhedsmærkat anvendes automatisk, ser brugeren en meddelelse i deres Office-app. Eksempel:

![Meddelelse om, at der automatisk blev anvendt en etiket i et dokument.](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Konfiguration af følsomme oplysningstyper for en etiket

Når du vælger indstillingen **Typer af** følsomme oplysninger, får du vist den samme liste over typer af følsomme oplysninger, som når du opretter en politik til forebyggelse af datatab (DLP). Så du kan f.eks. automatisk anvende en meget fortrolig etiket på alt indhold, der indeholder kundernes personlige oplysninger, f.eks. kreditkortnumre, personnumre eller pasnumre:

![Følsomme oplysningstyper til automatisk mærkatering i Office apps.](../media/sensitivity-labels-sensitive-info-types.png)

På samme måde som når du konfigurerer DLP-politikker, kan du derefter indskrænke din betingelse ved at ændre antallet af forekomster og matchnøjagtigheden. Eksempel:

![Indstillinger for matchnøjagtighed og antal forekomster.](../media/sit-confidence-level.png)

Du kan få mere at vide om disse konfigurationsindstillinger i DLP-dokumentationen: [Justeringsregler for at gøre dem nemmere eller sværere at matche](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Typerne af følsomme oplysninger har to forskellige måder at definere parametrene for det maksimale antal entydige forekomster på. Du kan få mere at vide under [Forekomstantal understøttede værdier for SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

På samme måde som konfiguration af DLP-politik kan du også vælge, om en betingelse skal registrere alle følsomme oplysningstyper eller kun én af dem. Og hvis du vil gøre dine betingelser mere fleksible eller komplekse, kan du [tilføje grupper og bruge logiske operatorer mellem grupperne](data-loss-prevention-policies.md).

> [!NOTE]
> Automatisk mærkning baseret på brugerdefinerede typer af følsomme oplysninger gælder kun for nyligt oprettet eller ændret indhold i OneDrive og SharePoint, ikke for eksisterende indhold. Denne begrænsning gælder også for automatisk mærkning af politik.

#### <a name="custom-sensitive-information-types-with-exact-data-match"></a>Brugerdefinerede typer af følsomme oplysninger med nøjagtig dataoverensstemmelse

Du kan konfigurere et følsomhedsmærkat til at bruge [nøjagtigt data, der matcher baserede typer](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) af følsomme oplysninger til brugerdefinerede typer af følsomme oplysninger. Men i øjeblikket skal du også angive mindst én type af følsomme oplysninger, der ikke bruger EDM. Eksempelvis en af de indbyggede følsomme oplysningstyper, f.eks **Kreditkortnummer**.

Hvis du konfigurerer et følsomhedsmærkat kun med EDM for din type af følsomme oplysninger, deaktiveres indstillingen for automatisk mærkater automatisk for etiketten.

### <a name="configuring-trainable-classifiers-for-a-label"></a>Konfiguration af klassificeringer, der kan trænes, for en etiket

Hvis du bruger denne indstilling med Microsoft 365 Apps til Windows version 2106 eller lavere eller Microsoft 365 Apps til Mac version 16.50 eller lavere, skal du kontrollere, at du har publiceret i din lejer mindst én anden følsomhedsmærkat, der er konfigureret til automatisk mærkning og indstillingen for følsomme [oplysningstyper](#configuring-sensitive-info-types-for-a-label). Dette krav er ikke nødvendigt, når du bruger nyere versioner på disse platforme.

Når du vælger indstillingen **Trænbare** klassificeringer, skal du vælge en eller flere af de præ-uddannede eller brugerdefinerede klassificeringer, der kan trænes:

![Indstillinger for klassificeringer og følsomhedsmærkater, der kan trænes.](../media/sensitivity-labels-classifers.png)

> [!CAUTION]
> Vi fraråder den **præ-uddannede classifier** for stødende sprog, fordi den har produceret et stort antal falske positive. Brug ikke denne klassificering, og hvis du bruger den i øjeblikket, anbefaler vi, at du flytter dine forretningsprocesser væk fra den og i stedet bruger de målrettede **,** **profanity**- og trusselsbaserede klassificeringer.

Du kan finde flere oplysninger om disse klassificeringer i [Få mere at vide om trænbare klassificeringer](classifier-learn-about.md).

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a>Anbefal, at brugeren anvender en følsomhedsmærkat

Hvis du foretrækker det, kan du anbefale brugerne, at de anvender etiketten. Med denne indstilling kan brugerne acceptere klassificeringen og den tilknyttede beskyttelse, eller de kan afvise anbefalingen, hvis etiketten ikke er egnet til deres indhold.

![Indstilling til at anbefale et følsomhedsmærkat til brugere.](../media/Sensitivity-labels-Recommended-label-option.png)

Her er et eksempel på en prompt fra Azure Information Protection samlet etiketklient, når du konfigurerer en betingelse for at anvende en etiket som en anbefalet handling med et brugerdefineret politiktip. Du kan vælge, hvilken tekst der skal vises i politiktip.

![Spørg, om der skal anvendes en anbefalet etiket.](../media/Sensitivity-label-prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a>Når der anvendes automatiske eller anbefalede etiketter

Implementeringen af automatisk og anbefalet mærkning i Office-apps afhænger af, om du bruger mærkning, der er indbygget i Office, eller Azure Information Protection unified labeling client. Men i begge tilfælde:

- Du kan ikke bruge automatisk mærkning til dokumenter og mails, der tidligere var manuelt mærket, eller tidligere automatisk mærket med en højere følsomhed. Husk, at du kun kan anvende en enkelt følsomhedsmærkat i et dokument eller en mail (ud over en enkelt opbevaringsmærkat).

- Du kan ikke bruge anbefalet mærkning til dokumenter eller mails, der tidligere er blevet mærket med en højere følsomhed. Når indholdet allerede er mærket med en højere følsomhed, kan brugeren ikke se prompten med anbefalingen og politiktip.

Specifikt for indbygget mærkning:

- Ikke alle Office-apps understøtter automatisk (og anbefalet) mærkning. Du kan finde flere oplysninger [i Understøttelse af følsomhedsmærkatfunktioner i apps](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- For anbefalede navne i skrivebordsversionerne af Word markeres det følsomme indhold, der udløste anbefalingen, så brugerne kan gennemse og fjerne det følsomme indhold i stedet for at anvende den anbefalede følsomhedsmærkat.

- Hvis du vil have mere at vide om, hvordan disse etiketter anvendes i Office-apps, eksempelskærme, og hvordan følsomme oplysninger registreres, skal du se Anvend eller anbefal automatisk følsomhedsmærkater på dine filer og mails [i Office](https://support.microsoft.com/office/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).

Specifikt for azure-Information Protection samlet etiketklient:

- Automatisk og anbefalet mærkning gælder for Word, Excel og PowerPoint, når du gemmer et dokument, og for at Outlook, når du sender en mail.

- Hvis Outlook du vil understøtte anbefalet mærkat, skal du først konfigurere en [avanceret politikindstilling](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).

- Følsomme oplysninger kan findes i brødteksten i dokumenter og mails og i sidehoveder og sidefødder, men ikke i emnelinjen eller vedhæftede filer i en mail.

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a>Sådan konfigureres politikker for automatisk mærkatering for SharePoint, OneDrive og Exchange

Sørg for, at du er opmærksom på forudsætningerne, før du konfigurerer politikker for automatisk mærkning.

### <a name="prerequisites-for-auto-labeling-policies"></a>Forudsætninger for politikker for automatisk mærkatering

- Simuleringstilstand:
  - Overvågning for Microsoft 365 skal være slået til. Hvis du har brug for at aktivere overvågning, eller hvis du ikke er sikker på, om overvågning allerede er aktiveret, skal du se Slå søgning i [overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).
  - Hvis du vil have vist fil- eller mailindhold i kildevisningen, skal du have rollen **Indholdsvisning** af dataklassificering, som er medtaget i rollegruppen **indholdsvisning i Indholdsoversigt** eller **i Information Protection**- og Information Protection-rollegrupper (i øjeblikket i forhåndsvisning). Uden den påkrævede rolle kan du ikke se indholdsruden, når du vælger et element på **fanen Matchede** elementer. Globale administratorer har ikke denne rolle som standard.

- Sådan navnmærkes filer automatisk SharePoint og OneDrive:
  - Du har [aktiveret følsomhedsetiketter til Office filer SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).
  - På det tidspunkt, hvor politikken for automatisk mærkater køres, skal filen ikke være åben af en anden proces eller bruger. En fil, der er tjekket ud til redigering, falder ind under denne kategori.

- Hvis du planlægger at bruge [brugerdefinerede typer af følsomme oplysninger](sensitive-information-type-learn-about.md) i stedet for de indbyggede følsomhedstyper:
  - Brugerdefinerede følsomhedsoplysninger gælder kun for indhold, der tilføjes eller ændres i SharePoint eller OneDrive efter de brugerdefinerede oplysningstyper for følsomhed er oprettet.
  - Hvis du vil teste nye brugerdefinerede typer af følsomme oplysninger, skal du oprette dem, før du opretter din politik for automatisk mærkning, og derefter oprette nye dokumenter med eksempeldata til test.

- Et eller flere [følsomhedsmærkater](create-sensitivity-labels.md) , der er oprettet og publiceret (til mindst én bruger), som du kan vælge til dine politikker for automatisk mærkning. For disse etiketter:
  - Det betyder ikke noget, om indstillingen for automatisk mærkater i Office apps er slået til eller fra, fordi denne etiketindstilling supplerer politikkerne for automatisk mærkatmærkning som beskrevet i introduktionen.
  - Hvis de etiketter, du vil bruge til automatisk mærkning, er konfigureret til at bruge visuelle markeringer (sidehoveder, sidefødder, vandmærker), skal du bemærke, at disse ikke anvendes på dokumenter.
  - Hvis etiketterne anvender [kryptering](encryption-sensitivity-labels.md):
    - Når politikken for automatisk mærkat omfatter placeringer til SharePoint eller OneDrive, skal etiketten **konfigureres til indstillingen Tildel** tilladelser nu.
    - Når politikken for automatisk mærkatering kun er til Exchange, kan etiketten **konfigureres** til enten Tildel tilladelser nu eller Lad brugere tildele tilladelser (til indstillingerne **Videresende** ikke eller Encrypt-Only).

### <a name="learn-about-simulation-mode"></a>Få mere at vide om simuleringstilstand

Simuleringstilstand er unik for politikker for automatisk mærkater og flettet ind i arbejdsprocessen. Du kan ikke automatisk navnmærke dokumenter og mails, før din politik har kørt mindst én simulering.

Simuleringstilstand understøtter op til 1.000.000 matchede filer. Hvis mere end dette antal filer er matchet fra en politik for automatisk mærkning, kan du ikke aktivere politikken for at anvende etiketterne. I dette tilfælde skal du omkonfigurere politikken for automatisk mærkning, så færre filer matches, og køre simulering igen. Dette maksimum på 1.000.000 matchede filer gælder kun for simuleringstilstand og ikke for en allerede aktiveret automatisk mærkningspolitik for at anvende følsomhedsmærkater.

Arbejdsproces for en politik for automatisk mærkat:

1. Opret og konfigurer en politik for automatisk mærkater.

2. Kør politikken i simuleringstilstand, hvilket kan tage 12 timer at gennemføre. Den fuldførte simulering udløser en mailmeddelelse, der sendes til brugeren, som er konfigureret til at modtage [aktivitetsbeskeder](alert-policies.md).

3. Gennemse resultaterne, og tilpas din politik, hvis det er nødvendigt. Det kan f.eks. være nødvendigt at redigere politikreglerne for at reducere falske positive eller fjerne nogle websteder, så antallet af matchede filer ikke overstiger 1.000.000. Kør simuleringstilstand igen, og vent på, at det fuldføres igen.

4. Gentag trin 3 efter behov.

5. Installér i produktion.

Den simulerede installation kører som WhatIf-parameteren for PowerShell. Du får vist resultater rapporteret, som om politikken for automatisk mærkning havde anvendt den valgte etiket ved hjælp af de regler, du har defineret. Du kan derefter justere dine regler for nøjagtighed, hvis det er nødvendigt, og køre simulering igen. Men da automatisk mærkater for Exchange gælder for mails, der sendes og modtages, i stedet for mails, der er gemt i postkasser, forvent ikke resultater for mails i en simulering for at være ensartede, medmindre du kan sende og modtage præcis de samme mails.

Simuleringstilstand gør det også muligt gradvist at øge omfanget af din politik for automatisk mærkatning før installationen. Du kan f.eks. starte med en enkelt placering, f.eks. et SharePoint websted, med et enkelt dokumentbibliotek. Med de iterative ændringer skal du derefter øge omfanget til flere websteder og derefter til en anden placering, f.eks. OneDrive.

Endelig kan du bruge simuleringstilstand til at give en tilnærmelse af den tid, det tager at køre din politik for automatisk mærkatering, for at hjælpe dig med at planlægge og planlægge, hvornår du skal køre den uden simuleringstilstand.

#### <a name="deleted-onedrive-accounts-and-simulation-results"></a>Slettede OneDrive og simuleringsresultater

Forvent mulige uoverensstemmelser i simuleringsresultaterne, når OneDrive konti stadig er i [opbevaringsfasen af sletningsprocessen](/onedrive/retention-and-deletion#the-onedrive-deletion-process). En medarbejder har f.eks. forladt organisationen, og dennes leder har midlertidig adgang til brugerens OneDrive filer.

I dette scenarie medtages matchede filer fra den slettede OneDrive-konto i simuleringsresultaterne, hvis OneDrive-kontoen blev angivet af URL'en i politikken for automatisk mærkning.

Men hvis den OneDrive konto ikke er angivet af URL, men var inkluderet i **standardindstillingen** Alle:
- Når placeringen SharePoint i politikken, vises matchede filer fra den slettede OneDrive-konto SharePoint elementer i simuleringsresultaterne.
- Når placeringen SharePoint ikke er medtaget i politikken, medtages matchede filer fra den slettede OneDrive-konto ikke i simuleringsresultaterne.

I alle tilfælde navnmærkes matchede filer, indtil OneDrive-kontoen slettes permanent. De viste uoverensstemmelser gælder kun for simuleringsresultaterne.

### <a name="creating-an-auto-labeling-policy"></a>Opret en politik for automatisk mærkater

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter du</a> gå til følsomhedsmærkaterne:

    - **Løsninger** >  **Beskyttelse af oplysninger**

    Hvis du ikke umiddelbart kan se denne indstilling, skal du først vælge **Vis alle**.

2. Vælg **fanen Automatisk mærkat** :

    ![Fanen Automatisk mærkat.](../media/auto-labeling-tab.png)

    > [!NOTE]
    > Hvis du ikke kan se fanen Automatisk mærkatering, er denne funktion i øjeblikket ikke tilgængelig i dit område på grund af en Backend **Azure-afhængighed** . Få mere at vide under [Tilgængelighed af Azure-afhængighed efter land](/troubleshoot/azure/general/dependency-availability-by-country).

3. Vælg **+ Opret automatisk etiketpolitik**. Dette starter konfigurationen Ny politik:

    ![Ny politikkonfiguration til automatisk mærkatering.](../media/auto-labeling-wizard.png)

4. Til siden Vælg **oplysninger, som denne etiket skal anvendes på**: Vælg en af skabelonerne, f.eks. **Finansiel** eller Beskyttelse af personlige **oplysninger**. Du kan afgrænse søgningen ved hjælp **af rullelisten** Vis indstillinger for. Eller vælg **Brugerdefineret politik** , hvis skabelonerne ikke opfylder dine krav. Vælg **Næste**.

5. Til siden Navngive din politik for automatisk **mærkater:** Angiv et entydigt navn og eventuelt en beskrivelse for at identificere den automatisk anvendte etiket, placeringer og betingelser, der identificerer indholdet, der skal navngives.

6. På siden Vælg **placeringer**, hvor du vil anvende etiketten: Vælg og angiv placeringer for Exchange, SharePoint og OneDrive. Hvis du ikke vil beholde standardindstillingen for Alle inkluderet for dine valgte placeringer, skal du vælge linket for at vælge bestemte forekomster, der skal medtages, eller vælge linket for at vælge bestemte forekomster at udelade. Vælg derefter **Næste**.

    ![Vælg placeringsside til automatisk konfiguration af mærkater.](../media/locations-auto-labeling-wizard.png)
    
    Hvis du ændrer standardindstillingerne ved hjælp af **Inkluderet eller** **Udeladt**:
    
    - For den **Exchange** placering, anvendes politikken i henhold til afsenderadressen på de angivne modtagere. Det meste af tiden skal du beholde standarden for Alle **inkluderet** med **Ingen** udeladt. Denne konfiguration er egnet, selvom du tester for et undersæt af brugere. I stedet for at angive dit undersæt af brugere her kan du bruge de avancerede regler i næste trin til at konfigurere betingelser, der omfatter eller udelader modtagere i organisationen. Ellers når du ændrer standardindstillingerne her:
        -  Hvis du ændrer standardindstillingen  for Alle inkluderet og i stedet vælger bestemte brugere eller grupper, vil mails, der sendes fra uden for din organisation, være undtaget fra politikken. 
        -  Hvis du beholder standardindstillingen  for Alle inkluderet, men angiver brugere eller grupper, der skal udelades, vil mails, som disse ekskluderede brugere sender, være undtaget fra politikken, men ikke mails, de modtager.
    
    - Du OneDrive få vist en liste over alle [BRUGER-OneDrive URL-adresser](/onedrive/list-onedrive-urls) i organisationen for at hjælpe dig med at angive individuelle OneDrive-konti, der skal medtages eller udelades.

7. På siden **Konfigurer almindelige eller** avancerede regler: Bevar standarden for almindelige  regler for at definere regler, der identificerer indhold, der skal navnmærkes, på tværs af alle dine valgte placeringer. Hvis du har brug for forskellige regler pr. placering, herunder flere indstillinger for Exchange, skal du vælge **Avancerede regler**. Vælg derefter **Næste**.

    Reglerne anvender betingelser, der omfatter følsomme oplysningstyper og indstillinger for deling:
    - Til typer af følsomme oplysninger kan du vælge både indbyggede og brugerdefinerede typer af følsomme oplysninger.
    - For de delte indstillinger kan du kun **vælge med personer inden for organisationen** eller **med personer uden for organisationen**.

    Hvis din placering er **Exchange og** du har **valgt Avancerede** regler, er der andre betingelser, du kan vælge:
    - Afsenders IP-adresse er
    - Modtagerdomæne er
    - Modtageren er
    - Filtypenavnet for den vedhæftede fil er
    - Vedhæftet fil er beskyttet med adgangskode
    - Indholdet af vedhæftede filer i mails kan ikke scannes
    - Scanningen af eventuelle vedhæftede filers indhold blev ikke fuldført
    - Sidehoved matcher mønstre
    - Emnet matcher mønstre
    - Modtageradresse indeholder ord
    - Modtageradresse matcher mønstre
    - Afsenderadresse matcher mønstre
    - Afsenderdomæne er
    - Modtageren er medlem af
    - Afsenderen er

    For hver af disse betingelser kan du derefter angive undtagelser.

8. Afhængigt af dine tidligere valg har du nu mulighed for at oprette nye regler ved hjælp af betingelser og undtagelser.

    Konfigurationsindstillingerne for typer af følsomme oplysninger er de samme som dem, du vælger til automatisk mærkatering til Office apps. Hvis du har brug for flere oplysninger, kan [du se Konfigurering af følsomme oplysningstyper for en etiket](#configuring-sensitive-info-types-for-a-label).

    Når du har defineret alle de regler, du skal bruge, og bekræftet, at deres status  er angivet, skal du vælge Næste for at gå videre til at vælge en etiket, der skal anvendes automatisk.

9. For siden **Vælg et navn til automatisk** anvendelse: Vælg **+** Vælg en etiket, vælg en etiket i ruden **Vælg** et følsomhedsmærkat, og vælg derefter **Næste**.

10. Hvis din politik omfatter placeringen Exchange: Angiv valgfrie konfigurationer på **siden Yderligere indstillinger for** mail:
    
    - **Erstat automatisk eksisterende** etiketter med samme eller lavere prioritet: Gældende for både indgående og udgående mails, når du vælger denne indstilling, sikrer det, at der altid anvendes en matchende følsomhedsmærkat. Hvis du ikke vælger denne indstilling, anvendes der ikke en matchende følsomhedsmærkat på mails, der har en eksisterende følsomhedsmærkat med en højere [](sensitivity-labels.md#label-priority-order-matters) prioritet, eller som er blevet navnmærket manuelt.
    
    - Anvend kryptering på mails, der modtages fra personer [uden for](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) **organisationen: Når** du vælger denne indstilling, skal du tildele en [rettighedsadministrationsejer](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) for at sikre, at en autoriseret person i organisationen har fuld kontrol over brugsrettigheder til mails, der sendes fra dig uden for organisationen, og dine politiknavne med kryptering. Denne rolle kan være nødvendig for senere at fjerne krypteringen eller tildele andre brugerrettigheder til brugerne i organisationen.
        
        **Tildel en Rights Management-ejer** skal du angive en enkelt bruger med en mailadresse, der ejes af organisationen. Angiv ikke en mailkontakt, en delt postkasse eller gruppetype, da disse ikke understøttes for denne rolle.

10. Til siden **Beslut** , om du vil teste politikken nu eller senere: Vælg Kør politik i **simuleringstilstand** , hvis du er klar til at køre politikken for automatisk mærkning nu i simuleringstilstand. Ellers skal du **vælge Forlad politik deaktiveret**. Vælg **Næste**:

    ![Test den konfigurerede politik for automatisk mærkning.](../media/simulation-mode-auto-labeling-wizard.png)

11. Til siden **Oversigt** : Gennemgå konfigurationen af din politik for automatisk mærkning, og foretag de nødvendige ændringer, og fuldfør konfigurationen.

Nu kan du  på siden Information **protectionAuto-labeling**  >  se din automatiske etiketpolitik i afsnittet Simulering eller Fra, afhængigt af om du har valgt at køre den i simuleringstilstand eller ej. Vælg din politik for at få vist oplysninger om konfiguration og status (f.eks. kører **politiksimulering stadig**). For politikker i simuleringstilstand skal du vælge **fanen Matchede** elementer for at se, hvilke mails eller dokumenter der matcher de regler, du har angivet.

Du kan ændre politikken direkte fra denne grænseflade:

- Hvis du vil have en politik **i sektionen** Fra, skal du **vælge knappen Rediger** politik.

- For politikker i **afsnittet Simulering** skal du **vælge** indstillingen Rediger politik øverst på siden fra en af fanerne:

    ![Rediger politikindstillingen for automatisk mærkat.](../media/auto-labeling-edit.png)

    Når du er klar til at køre politikken uden simulering, skal du **vælge indstillingen Aktiver** politik.

Politikker for automatisk mærkning kører løbende, indtil de slettes. Nye og ændrede filer inkluderes f.eks. i de aktuelle politikindstillinger.

### <a name="monitoring-your-auto-labeling-policy"></a>Overvåge din politik for automatisk mærkning

Når din politik for automatisk mærkater er slået til, kan du se status for mærkater for filer i den valgte placering SharePoint og OneDrive placeringer. Mails inkluderes ikke i mærkatens status, fordi de automatisk mærkes, når de sendes.

Status for mærkning omfatter de filer, der skal mærkes af politikken, de filer, der er mærket i de seneste syv dage, og de samlede filer, der er navngivet. Da der maksimalt kan mærkes 25.000 filer om dagen, giver disse oplysninger dig overblik over den aktuelle status for mærkater for din politik, og hvor mange filer der stadig skal mærkes.

Når du først aktiverer politikken, ser du i første omgang en værdi på 0 for filer, der skal mærkes, indtil de nyeste data er hentet. Disse statusoplysninger opdateres hver 48. time, så du kan forvente at se de nyeste data om hver anden dag. Når du vælger en politik for automatisk mærkatering, kan du se flere oplysninger om politikken i en pop op-rude, som omfatter status for mærkning af de øverste 10 websteder. Oplysningerne i denne pop op-rude kan være mere aktuelle end de aggregerede politikoplysninger, der vises på **hovedsiden til automatisk mærkatning** .

Du kan også se resultaterne af din politik for automatisk mærkatering ved hjælp af [indholdsstifinder](data-classification-content-explorer.md) , når du har [de relevante tilladelser](data-classification-content-explorer.md#permissions):

- **Med rollegruppen Listevisning** i Indholdsoversigt kan du se en fils navn, men ikke filens indhold.
- **Indholdsoversigtens** rollegruppe Indholdsvisning og **Information Protection** og **Information Protection Grupper af indholdsgrupper** (i øjeblikket i forhåndsvisning) giver dig mulighed for at se filens indhold.

> [!TIP]
> Du kan også bruge indholdsstifinder til at identificere placeringer, der indeholder dokumenter med følsomme oplysninger, men som ikke er navnmærket. Med disse oplysninger bør du overveje at føje disse placeringer til din politik for automatisk mærkning og medtage de identificerede typer af følsomme oplysninger som regler.

### <a name="use-powershell-for-auto-labeling-policies"></a>Brug PowerShell til politikker for automatisk mærkning

Du kan bruge [Security & Compliance Center PowerShell til](/powershell/exchange/scc-powershell) at oprette og konfigurere politikker for automatisk mærkning. Det betyder, at du fuldt ud kan scripte oprettelse og vedligeholdelse af dine politikker for automatisk mærkning, hvilket også giver en mere effektiv metode til at angive flere URL-adresser OneDrive og SharePoint placeringer.

Før du kører kommandoerne i PowerShell, skal du først [oprette forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

Sådan oprettes en ny politik for automatisk mærkater:

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Denne kommando opretter en automatisk etiketpolitik for et SharePoint, du angiver. Hvis du OneDrive placering, skal du bruge *parameteren OneDriveLocation* i stedet.

Sådan føjer du flere websteder til en eksisterende politik for automatisk mærkning:

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Denne kommando angiver den nye SharePoint URL-adresser i en variabel, som derefter føjes til en eksisterende politik for automatisk mærkning. Hvis du OneDrive placeringerne i stedet, skal du bruge *parameteren AddOneDriveLocation* med en anden variabel, f.eks *. $OneDriveLocations*.

Sådan oprettes en ny politikregel for automatisk mærkater:

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

For en eksisterende politik for automatisk mærkater opretter denne kommando en ny politikregel til at registrere typen af følsomme oplysninger for amerikanske CPR-nummer **(SSN**), som har et enheds-id for en44669fe-0d48-453d-a9b1-2cc83f2cba77. Hvis du vil finde enheds-i-erne til andre typer af følsomme oplysninger, skal du se [enhedsdefinitioner af typen Følsomme oplysninger](sensitive-information-type-entity-definitions.md).

Du kan finde flere oplysninger om de PowerShell-cmdlet'er, der understøtter politikker for automatisk mærkning, deres tilgængelige parametre og nogle eksempler i følgende hjælp til cmdlet'er:

- [Get-AutoSensitivityLabelPolicy](/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelPolicy](/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelRule](/powershell/module/exchange/new-autosensitivitylabelrule)
- [Remove-AutoSensitivityLabelPolicy](/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [Remove-AutoSensitivityLabelRule](/powershell/module/exchange/remove-autosensitivitylabelrule)
- [Set-AutoSensitivityLabelPolicy](/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [Set-AutoSensitivityLabelRule](/powershell/module/exchange/set-autosensitivitylabelrule)

## <a name="tips-to-increase-labeling-reach"></a>Tips for at øge mærkatens nå

Selvom automatisk mærkning er en af de mest effektive måder at klassificere, navnlægge og beskytte Office-filer, som din organisation ejer, kan du kontrollere, om du kan supplere den med en af følgende metoder til at øge mærkatens rækkevidde:

- Med SharePoint Syntex kan du anvende en følsomhedsmærkat på en dokumentforståelsesmodel, så identificerede dokumenter i et SharePoint-bibliotek automatisk mærkes.[](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model)

- Når du bruger [Azure Information Protection samlet etiketklient](/azure/information-protection/rms-client/aip-clientv2):

  - For filer i lokale datalagre, f.eks. netværksshares og SharePoint Server-biblioteker: Brug [scanneren](/azure/information-protection/deploy-aip-scanner) til at finde følsomme oplysninger i disse filer, og mærkater dem korrekt. Hvis du planlægger at overføre eller uploade disse filer til en SharePoint i Microsoft 365, skal du bruge scanneren til at navnmærke filerne, før du flytter dem til skyen.

  - Hvis du har brugt en anden mærkningsløsning, før du bruger følsomhedsmærkater: Brug PowerShell og en avanceret indstilling [til at genbruge etiketter](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#migrate-labels-from-secure-islands-and-other-labeling-solutions) fra disse løsninger.

- [Tilskyd manuel mærkning efter](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) at have forsynet brugerne med træning, hvilke følsomhedsmærkater der skal anvendes. Når du er sikker på, at brugerne forstår, hvilken etiket der skal anvendes, kan du overveje at konfigurere en standardetiket og obligatorisk mærkning som [politikindstillinger](sensitivity-labels.md#what-label-policies-can-do).

Desuden bør [du overveje at](/sharepoint/sensitive-by-default) markere nye filer som følsomme som standard i SharePoint for at forhindre gæster i at få adgang til nyligt tilføjede filer, indtil mindst én DLP-politik scanner indholdet af filen.
