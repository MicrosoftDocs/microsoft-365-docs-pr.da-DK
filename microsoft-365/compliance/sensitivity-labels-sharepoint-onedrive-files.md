---
title: Aktivér følsomhedsmærkater for Office filer
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.date: ''
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Administratorer kan aktivere understøttelse af følsomhedsmærkater for Word-, Excel- og PowerPoint-filer i SharePoint og OneDrive.
ms.openlocfilehash: 4e3a3898f437325a28a4deda83ba8804324fe215
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285428"
---
# <a name="enable-sensitivity-labels-for-office-files-in-sharepoint-and-onedrive"></a>Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Aktivér indbygget mærkning for [understøttede Office filer](sensitivity-labels-office-apps.md#office-file-types-supported) i SharePoint og OneDrive, så brugerne kan anvende dine [følsomhedsmærkater](sensitivity-labels.md) i Office på internettet. Når denne funktion er aktiveret, kan brugerne se knappen **Følsomhed** på båndet, så de kan anvende mærkater og se eventuelle anvendte navne på statuslinjen.

Aktivering af denne funktion medfører også, at SharePoint og OneDrive kan behandle indholdet af Office filer, der er krypteret ved hjælp af en følsomhedsmærkat. Mærkaten kan anvendes i Office på internettet eller i Office desktopapps og uploades eller gemmes i SharePoint og OneDrive. Indtil du aktiverer denne funktion, kan disse tjenester ikke behandle krypterede filer, hvilket betyder, at samtidig redigering, eDiscovery, forebyggelse af datatab i Microsoft Purview, søgning og andre samarbejdsfunktioner ikke fungerer for disse filer.

Når du har aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive, for nye og ændrede filer, der har en følsomhedsmærkat, der anvender kryptering med en skybaseret nøgle (og ikke bruger [kryptering med dobbelt nøgle](double-key-encryption.md):

- I forbindelse med Word-, Excel- og PowerPoint-filer genkender SharePoint og OneDrive mærkaten og kan nu behandle indholdet af den krypterede fil.

- Når brugerne downloader eller får adgang til disse filer fra SharePoint eller OneDrive, gennemtvinges følsomhedsmærkaten og eventuelle krypteringsindstillinger fra mærkaten og forbliver i filen, uanset hvor den er gemt. Sørg for, at du giver brugervejledning til kun at bruge mærkater til at beskytte dokumenter. Du kan få flere oplysninger under [Indstillinger for IRM (Information Rights Management) og følsomhedsmærkater](sensitivity-labels-office-apps.md#information-rights-management-irm-options-and-sensitivity-labels).

- Når brugerne uploader navngivne og krypterede filer til SharePoint eller OneDrive, skal de som minimum have visningsrettigheder til disse filer. De kan f.eks. åbne filerne uden for SharePoint. Hvis de ikke har denne minimumanvendelsesrettighed, lykkes overførslen, men tjenesten genkender ikke mærkaten og kan ikke behandle filindholdet.

- Brug Office på internettet (Word, Excel, PowerPoint) til at åbne og redigere Office filer, der har følsomhedsmærkater, som anvender kryptering. De tilladelser, der blev tildelt med krypteringen, gennemtvinges. Du kan også bruge [automatisk mærkning](apply-sensitivity-label-automatically.md) til disse dokumenter.

- Eksterne brugere kan få adgang til dokumenter, der er mærket med kryptering, ved hjælp af gæstekonti. Du kan få flere oplysninger under [Understøttelse af eksterne brugere og markeret indhold](sensitivity-labels-office-apps.md#support-for-external-users-and-labeled-content).

- Office 365 eDiscovery understøtter fuldtekstsøgning efter disse filer og DLP-politikker (forebyggelse af datatab) understøtter indhold i disse filer.

> [!NOTE]
> Hvis kryptering er anvendt med en nøgle i det lokale miljø (en topologi til administration af nøgler, der ofte kaldes "hold din egen nøgle" eller HYOK) eller ved hjælp af [dobbeltnøglekryptering](double-key-encryption.md), ændres tjenestefunktionsmåden for behandling af filindholdet ikke. Så for disse filer fungerer samtidig redigering, eDiscovery, forebyggelse af datatab, søgning og andre samarbejdsfunktioner ikke.
>
> Funktionsmåden SharePoint og OneDrive ændres heller ikke for eksisterende filer på disse placeringer, der er mærket med kryptering ved hjælp af en enkelt Azure-baseret nøgle. Hvis disse filer skal kunne drage fordel af de nye funktioner, når du har aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive, skal filerne enten downloades og uploades igen eller redigeres.

Når du har aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive, er der tre nye [overvågningshændelser](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) tilgængelige til overvågning af følsomhedsmærkater, der anvendes på dokumenter i SharePoint og OneDrive:

- **Anvendte følsomhedsmærkat på fil**
- **Ændret følsomhedsmærkat anvendt på fil**
- **Følsomhedsmærkaten er fjernet fra filen**

Se følgende video (ingen lyd) for at se de nye funktioner i aktion:

> [!VIDEO https://www.microsoft.com/videoplayer/embed//RE4ornZ]

Du har altid mulighed for at deaktivere følsomhedsmærkater for Office filer i SharePoint og OneDrive ([framelde dig](#how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out)) når som helst.

Hvis du i øjeblikket beskytter dokumenter i SharePoint ved hjælp af SharePoint IRM (Information Rights Management), skal du kontrollere afsnittet [SharePoint IRM (Information Rights Management) og følsomhedsmærkater](#sharepoint-information-rights-management-irm-and-sensitivity-labels) på denne side.

## <a name="requirements"></a>Krav

Disse nye funktioner fungerer kun med [følsomhedsmærkater](sensitivity-labels.md) . Hvis du i øjeblikket har Azure Information Protection-mærkater, skal du først overføre dem til følsomhedsmærkater, så du kan aktivere disse funktioner for nye filer, som du uploader. Du kan finde instruktioner under [Sådan overfører du Azure Information Protection-mærkater til samlede følsomhedsmærkater](/azure/information-protection/configure-policy-migrate-labels).

Brug OneDrive-synkronisering appversion 19.002.0121.0008 eller nyere på Windows og version 19.002.0107.0008 eller nyere på Mac. Begge disse versioner blev udgivet 28. januar 2019, og er i øjeblikket frigivet til alle ringe. Du kan få flere oplysninger i [produktbemærkningerne til OneDrive](https://support.office.com/article/845dcf18-f921-435e-bf28-4e24b95e5fc0). Når du har aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive, bliver brugere, der kører en ældre version af synkroniseringsappen, bedt om at opdatere den.

## <a name="limitations"></a>Begrænsninger

- SharePoint og OneDrive kan ikke behandle nogle filer, der er mærket og krypteret fra Office desktopapps, når disse filer indeholder PowerQuery-data, data, der er gemt af brugerdefinerede tilføjelsesprogrammer, eller brugerdefinerede XML-dele, f.eks. egenskaber for forside, indholdstypeskemaer, brugerdefineret panel for dokumentoplysninger og brugerdefineret XSN. Denne begrænsning gælder også for filer, der indeholder en [bibliografi](https://support.microsoft.com/en-us/office/create-a-bibliography-citations-and-references-17686589-4824-4940-9c69-342c289fa2a5), og for filer, hvor der tilføjes et [dokument-id](https://support.microsoft.com/office/enable-and-configure-unique-document-ids-ea7fee86-bd6f-4cc8-9365-8086e794c984) , når de uploades.

    For disse filer skal du enten anvende en mærkat uden kryptering, så de senere kan åbnes i Office på internettet, eller instruere brugerne i at åbne filerne i deres skrivebordsapps. Filer, der kun er mærket og krypteret i Office på internettet, påvirkes ikke.

- SharePoint og OneDrive anvender ikke automatisk følsomhedsmærkater på eksisterende filer, som du allerede har krypteret ved hjælp af Azure Information Protection-mærkater. Hvis funktionerne skal fungere, når du har aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive, skal du i stedet udføre disse opgaver:

    1. Sørg for, at du har [overført Azure Information Protection-mærkater](/azure/information-protection/configure-policy-migrate-labels) til følsomhedsmærkater og [publiceret dem](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy) fra Microsoft Purview-overholdelsesportalen.
    2. Download de navngivne filer, og upload dem derefter til deres oprindelige placering i SharePoint eller OneDrive.

- SharePoint og OneDrive kan ikke behandle krypterede filer, når den mærkat, der anvendte krypteringen, har en af følgende [konfigurationer til kryptering](encryption-sensitivity-labels.md#configure-encryption-settings):
  - **Lad brugerne tildele tilladelser, når de anvender etiketten**, og afkrydsningsfeltet **I Word, PowerPoint og Excel skal du bede brugerne om at angive tilladelser** er markeret. Denne indstilling kaldes nogle gange "brugerdefinerede tilladelser".
  - **Brugeradgang til indhold, der udløber,** er angivet til en anden værdi end **Aldrig**.
  - **Kryptering af dobbelt nøgle** er valgt.

    For mærkater med nogen af disse krypteringskonfigurationer vises mærkaterne ikke for brugere i Office på internettet. Derudover kan de nye funktioner ikke bruges sammen med navngivne dokumenter, der allerede har disse krypteringsindstillinger. Disse dokumenter returneres f.eks. ikke i søgeresultater, selvom de opdateres.

- Når du uploader eller gemmer et dokument til SharePoint af hensyn til ydeevnen, og filens mærkat ikke anvender kryptering, kan kolonnen **Følsomhed** i dokumentbiblioteket tage et stykke tid at vise navnet. Medregn denne forsinkelse, hvis du bruger scripts eller automatisering, der afhænger af navnet på etiketten i denne kolonne.

- Hvis et dokument er markeret, mens det er [tjekket ud i SharePoint](https://support.microsoft.com/office/check-out-check-in-or-discard-changes-to-files-in-a-library-7e2c12a9-a874-4393-9511-1378a700f6de), viser kolonnen **Følsomhed** i dokumentbiblioteket ikke navnet, før dokumentet er tjekket ind og derefter åbnes i SharePoint.

- Hvis et navngivet og krypteret dokument downloades fra SharePoint eller OneDrive af en app eller tjeneste, der bruger et tjenesteprincipalnavn, og derefter uploades igen med en mærkat, der anvender andre krypteringsindstillinger, mislykkes overførslen. Et eksempelscenarie er Microsoft Defender for Cloud Apps ændrer en følsomhedsmærkat på en fil fra **Fortroligt** til **Meget fortroligt** eller fra **Fortroligt** til **Generelt**.
    
    Overførslen mislykkes ikke, hvis appen eller tjenesten først kører [Unlock-SPOSensitivityLabelEncryptedFile-cmdlet'en](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile) , som forklaret i afsnittet [Fjern kryptering for et navngivet dokument](#remove-encryption-for-a-labeled-document) . Eller før overførslen slettes den oprindelige fil, eller filnavnet ændres.

- Brugerne kan opleve forsinkelser i at åbne krypterede dokumenter i følgende Gem som-scenarie: Ved hjælp af en skrivebordsversion af Office vælger en bruger Gem som for et dokument, der har en følsomhedsmærkat, der anvender kryptering. Brugeren vælger SharePoint eller OneDrive for placeringen og forsøger derefter straks at åbne dokumentet i Office på internettet. Hvis tjenesten stadig behandler krypteringen, får brugeren vist en meddelelse om, at dokumentet skal åbnes i vedkommendes skrivebordsapp. Hvis de prøver igen om et par minutter, åbnes dokumentet i Office på internettet.

- I forbindelse med krypterede dokumenter understøttes udskrivning ikke i Office på internettet.

- I forbindelse med krypterede dokumenter i Office på internettet forhindres kopiering til Udklipsholder og hentning af skærmbilleder ikke. Du kan få flere oplysninger under [Kan Rights Management forhindre hentning af skærmbilleder?](/azure/information-protection/faqs-rms#can-rights-management-prevent-screen-captures)

- Som standard understøtter Office desktopapps og mobilapps ikke samtidig redigering af filer, der er mærket med kryptering. Disse apps fortsætter med at åbne navngivne og krypterede filer i eksklusiv redigeringstilstand.
    
    > [!NOTE]
    > Samtidig redigering understøttes nu for Windows og macOS. Du kan få flere oplysninger under [Aktivér samtidig redigering af filer, der er krypteret med følsomhedsmærkater](sensitivity-labels-coauthoring.md).

- Hvis en administrator ændrer indstillingerne for en publiceret etiket, der allerede er anvendt på filer, der er hentet til brugernes synkroniseringsklient, kan brugerne muligvis ikke gemme de ændringer, de foretager i filen, i deres OneDrive mappen Synkroniser. Dette scenarie gælder for filer, der er mærket med kryptering, og også når ændringen af mærkaten er fra en mærkat, der ikke anvendte kryptering på en mærkat, der anvender kryptering. Brugerne får vist en [rød cirkel med en fejl med et hvidt krydsikon](https://support.office.com/article/what-do-the-onedrive-icons-mean-11143026-8000-44f8-aaa9-67c985aa49b3), og de bliver bedt om at gemme nye ændringer som en separat kopi. De kan i stedet lukke og genåbne filen eller bruge Office på internettet.

- Brugerne kan opleve at gemme problemer, når de er gået offline eller i slumretilstand, når de i stedet for at bruge Office på internettet bruger skrivebords- og mobilapps til Word, Excel eller PowerPoint. Når brugerne genoptager deres Office-app session og forsøger at gemme ændringerne, får de vist en meddelelse om uploadfejl med mulighed for at gemme en kopi i stedet for at gemme den oprindelige fil.

- Dokumenter, der er krypteret på følgende måder, kan ikke åbnes i Office på internettet:
  - Kryptering, der bruger en lokal nøgle ("hold din egen nøgle" eller HYOK)
  - Kryptering, der blev anvendt ved hjælp af [kryptering med dobbelt nøgle](double-key-encryption.md)
  - Kryptering, der blev anvendt uafhængigt af en mærkat, f.eks. ved direkte anvendelse af en Rights Management-beskyttelsesskabelon.

- Navne, der er konfigureret til [andre sprog](create-sensitivity-labels.md#additional-label-settings-with-security--compliance-center-powershell) , understøttes ikke og viser kun det oprindelige sprog.

- Hvis du sletter en etiket, der er anvendt på et dokument i SharePoint eller OneDrive, i stedet for at fjerne mærkaten fra den relevante mærkatpolitik, vil dokumentet, når det downloades, ikke være forsynet med mærkater eller krypteret. Hvis det navngivne dokument til sammenligning gemmes uden for SharePoint eller OneDrive, forbliver dokumentet krypteret, hvis navnet slettes. Bemærk, at selvom du muligvis sletter mærkater i en testfase, er det meget sjældent at slette en mærkat i et produktionsmiljø.

## <a name="how-to-enable-sensitivity-labels-for-sharepoint-and-onedrive-opt-in"></a>Sådan aktiverer du følsomhedsmærkater for SharePoint og OneDrive (tilvalg)

Du kan aktivere de nye funktioner ved hjælp af Microsoft Purview-overholdelsesportalen eller ved hjælp af PowerShell. Som med alle konfigurationsændringer på lejerniveau for SharePoint og OneDrive tager det ca. 15 minutter, før ændringen træder i kraft.

### <a name="use-the-microsoft-purview-compliance-portal-to-enable-support-for-sensitivity-labels"></a>Brug Microsoft Purview-overholdelsesportalen til at aktivere understøttelse af følsomhedsmærkater

Denne indstilling er den nemmeste måde at aktivere følsomhedsmærkater for SharePoint og OneDrive på, men du skal logge på som global administrator for din lejer.

1. Log på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/) som global administrator, og naviger til **SolutionsInformation** >  **Protection**

    Hvis du ikke kan se denne indstilling med det samme, skal du først vælge **Vis alle**.

2. Hvis du får vist en meddelelse om at aktivere muligheden for at behandle indhold i Office onlinefiler, skal du vælge **Slå til nu**:

    ![Slå knappen Til nu for at aktivere følsomhedsmærkater for Office Online.](../media/sensitivity-labels-turn-on-banner.png)

    Kommandoen kører med det samme, og når siden opdateres næste gang, får du ikke længere vist meddelelsen eller knappen.

> [!NOTE]
> Hvis du har Microsoft 365 Multi-Geo, skal du bruge PowerShell til at aktivere disse funktioner for alle dine geografiske placeringer. Se næste afsnit for at få flere oplysninger.

### <a name="use-powershell-to-enable-support-for-sensitivity-labels"></a>Brug PowerShell til at aktivere understøttelse af følsomhedsmærkater

Som et alternativ til at bruge Microsoft Purview-overholdelsesportalen kan du aktivere understøttelse af følsomhedsmærkater ved hjælp af [Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/set-spotenant) fra SharePoint Online PowerShell.

Hvis du har Microsoft 365 Multi-Geo, skal du bruge PowerShell til at aktivere denne understøttelse for alle dine geografiske placeringer.

#### <a name="prepare-the-sharepoint-online-management-shell"></a>Forbered SharePoint Online Management Shell

Før du kører PowerShell-kommandoen for at aktivere følsomhedsmærkater for Office filer i SharePoint og OneDrive, skal du sørge for, at du kører SharePoint Online Management Shell version 16.0.19418.12000 eller nyere. Hvis du allerede har den nyeste version, kan du gå videre til [næste procedure](#run-the-powershell-command-to-enable-support-for-sensitivity-labels) for at køre PowerShell-kommandoen.

1. Hvis du har installeret en tidligere version af SharePoint Online Management Shell fra PowerShell-galleriet, kan du opdatere modulet ved at køre følgende cmdlet.

    ```PowerShell
    Update-Module -Name Microsoft.Online.SharePoint.PowerShell
    ```

2. Hvis du har installeret en tidligere version af SharePoint Online Management Shell fra Microsoft Download Center, kan du også gå til **Tilføj eller fjern programmer** og fjerne SharePoint Online Management Shell.

3. Gå til siden Download Center i en webbrowser, og [download den nyeste SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

4. Vælg dit sprog, og klik derefter på **Download**.

5. Vælg mellem filen x64 og x86 .msi. Download x64-filen, hvis du kører 64-bit versionen af Windows eller x86-filen, hvis du kører 32-bit versionen. Hvis du ikke ved det, kan du se [Hvilken version af Windows operativsystem kører jeg?](https://support.microsoft.com/help/13443/windows-which-operating-system)

6. Når du har downloadet filen, skal du køre filen og følge trinnene i installationsguiden.

#### <a name="run-the-powershell-command-to-enable-support-for-sensitivity-labels"></a>Kør PowerShell-kommandoen for at aktivere understøttelse af følsomhedsmærkater

Hvis du vil aktivere de nye funktioner, skal du bruge [Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/set-spotenant) med parameteren *EnableAIPIntegration* :

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administrator- eller SharePoint administratorrettigheder i Microsoft 365, skal du oprette forbindelse til SharePoint. Du kan få mere at vide om, hvordan [du kommer i gang med SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

    > [!NOTE]
    > Hvis du har Microsoft 365 Multi-Geo, skal du bruge parameteren -URL sammen med [Forbind-SPOService](/powershell/module/sharepoint-online/connect-sposervice) og angive URL-adressen for webstedet SharePoint Online Administrationscenter for en af dine geografiske placeringer.

2. Kør følgende kommando, og tryk på **Y** for at bekræfte:

    ```PowerShell
    Set-SPOTenant -EnableAIPIntegration $true
    ```
3. For Microsoft 365 Multi-Geo: Gentag trin 1 og 2 for hver af dine resterende geografiske placeringer.

## <a name="publishing-and-changing-sensitivity-labels"></a>Publicering og ændring af følsomhedsmærkater

Når du bruger følsomhedsmærkater med SharePoint og OneDrive, skal du huske på, at du skal tillade replikeringstid, når du publicerer nye følsomhedsmærkater eller opdaterer eksisterende følsomhedsmærkater. Dette er især vigtigt for nye mærkater, der anvender kryptering.

Eksempel: Du opretter og publicerer en ny følsomhedsmærkat, der anvender kryptering, og den vises meget hurtigt i en brugers skrivebordsapp. Brugeren anvender denne mærkat på et dokument og overfører den derefter til SharePoint eller OneDrive. Hvis etiketreplikeringen ikke er fuldført for tjenesten, anvendes de nye funktioner ikke på dette dokument ved upload. Derfor returneres dokumentet ikke i søgningen eller efter eDiscovery, og dokumentet kan ikke åbnes i Office på internettet.

Du kan få flere oplysninger om timingen af mærkater under [Hvornår du kan forvente, at nye mærkater og ændringer træder i kraft](create-sensitivity-labels.md#when-to-expect-new-labels-and-changes-to-take-effect).

Som en sikkerhedsforanstaltning anbefaler vi, at du kun udgiver nye mærkater til nogle få testbrugere først, venter mindst én time og derefter kontrollerer mærkatfunktionsmåden på SharePoint og OneDrive. Vent mindst en dag, før du gør mærkaten tilgængelig for flere brugere ved enten at føje flere brugere til den eksisterende mærkatpolitik eller føje mærkaten til en eksisterende mærkatpolitik for dine standardbrugere. Når standardbrugerne ser mærkaten, er den allerede synkroniseret til SharePoint og OneDrive.

## <a name="sharepoint-information-rights-management-irm-and-sensitivity-labels"></a>SharePoint IRM (Information Rights Management) og følsomhedsmærkater

[SharePoint IRM (Information Rights Management)](set-up-irm-in-sp-admin-center.md) er en ældre teknologi til beskyttelse af filer på liste- og biblioteksniveau ved at anvende kryptering og begrænsninger, når filer downloades. Denne ældre beskyttelsesteknologi er udviklet til at forhindre uautoriserede brugere i at åbne filen, mens den er uden for SharePoint.

Til sammenligning giver følsomhedsmærkater beskyttelsesindstillinger for visuelle markeringer (sidehoveder, sidefødder, vandmærker) ud over kryptering. Krypteringsindstillingerne understøtter det fulde udvalg af [brugsrettigheder](/azure/information-protection/configure-usage-rights) for at begrænse, hvad brugerne kan gøre med indholdet, og de samme følsomhedsmærkater understøttes i [mange scenarier](get-started-with-sensitivity-labels.md#common-scenarios-for-sensitivity-labels). Brug af den samme beskyttelsesmetode med ensartede indstillinger på tværs af arbejdsbelastninger og apps resulterer i en ensartet beskyttelsesstrategi.

Du kan dog bruge både beskyttelsesløsninger sammen, og funktionsmåden er som følger:

- Hvis du uploader en fil med en følsomhedsmærkat, der anvender kryptering, kan SharePoint ikke behandle indholdet af disse filer, så samtidig redigering, eDiscovery, DLP og søgning understøttes ikke for disse filer.

- Hvis du navngiver en fil ved hjælp af Office på internettet, gennemtvinges alle krypteringsindstillinger fra mærkaten. For disse filer understøttes samtidig redigering, eDiscovery, DLP og søgning.

- Hvis du downloader en fil, der er mærket ved hjælp af Office på internettet, bevares mærkaten, og krypteringsindstillinger fra mærkaten gennemtvinges i stedet for IRM-begrænsningsindstillingerne.

- Hvis du downloader en Office- eller PDF-fil, der ikke er krypteret med en følsomhedsmærkat, anvendes IRM-indstillinger.

- Hvis du har aktiveret nogle af de yderligere indstillinger for IRM-biblioteket, som omfatter forebyggelse af brugeres overførsel af dokumenter, der ikke understøtter IRM, gennemtvinges disse indstillinger.

Med denne funktionsmåde kan du være sikker på, at alle Office- og PDF-filer er beskyttet mod uautoriseret adgang, hvis de downloades, selvom de ikke er forsynet med mærkater. Navngivne filer, der uploades, drager dog ikke fordel af de nye funktioner.

## <a name="search-for-documents-by-sensitivity-label"></a>Søg efter dokumenter efter følsomhedsmærkat

Brug den administrerede egenskab **InformationProtectionLabelId** til at finde alle dokumenter i SharePoint eller OneDrive, der har en bestemt følsomhedsmærkat. Brug følgende syntaks: `InformationProtectionLabelId:<GUID>`

Hvis du f.eks. vil søge efter alle dokumenter, der er mærket som "Fortroligt", og denne mærkat har GUID'et "8faca7b8-8d20-48a3-8ea2-0f96310a848e", skal du skrive:

```
InformationProtectionLabelId:8faca7b8-8d20-48a3-8ea2-0f96310a848e
```

Søgningen kan ikke finde navngivne dokumenter i en komprimeret fil, f.eks. en .zip fil.

Hvis du vil hente GUID'erne for dine følsomhedsmærkater, skal du bruge cmdlet'en [Hent mærkat](/powershell/module/exchange/get-label) :

1. Først skal du [oprette forbindelse til Office 365 Security & Compliance Center PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

    I en PowerShell-session, som du kører som administrator, skal du f.eks. logge på med en global administratorkonto.

2. Kør derefter følgende kommando:

    ```powershell
    Get-Label |ft Name, Guid
    ```

Du kan finde flere oplysninger om brug af administrerede egenskaber [under Administrer søgeskemaet i SharePoint](/sharepoint/manage-search-schema).

## <a name="remove-encryption-for-a-labeled-document"></a>Fjern kryptering for et navngivet dokument

Der kan være sjældne tilfælde, hvor en SharePoint-administrator skal fjerne kryptering fra et dokument, der er gemt i SharePoint. Alle brugere, der har [rettigheden](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) Eksportér eller Fuld kontrol tildelt til Rights Management for det pågældende dokument, kan fjerne kryptering, der blev anvendt af Tjenesten Azure Rights Management, fra Azure Information Protection. Brugere med en af disse brugsrettigheder kan f.eks. erstatte en mærkat, der anvender kryptering med en mærkat uden kryptering. En [superbruger](/azure/information-protection/configure-super-users) kan også downloade filen og gemme en lokal kopi uden krypteringen.

Alternativt kan en global administrator eller [SharePoint administrator](/sharepoint/sharepoint-admin-role) køre [Unlock-SPOSensitivityLabelEncryptedFile-cmdlet'en](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile), hvilket fjerner både følsomhedsmærkaten og krypteringen. Denne cmdlet kører, selvom administratoren ikke har adgangstilladelser til webstedet eller filen, eller hvis Tjenesten Azure Rights Management ikke er tilgængelig.

Eksempel:

```powershell
Unlock-SPOSensitivityLabelEncryptedFile -FileUrl "https://contoso.com/sites/Marketing/Shared Documents/Doc1.docx" -JustificationText "Need to decrypt this file"
```

Krav:

- SharePoint Shell version 16.0.20616.12000 eller nyere.

- Krypteringen er blevet anvendt af en følsomhedsmærkat med administratordefinerede krypteringsindstillinger (mærkatindstillingerne [for Tildel tilladelser nu](encryption-sensitivity-labels.md#assign-permissions-now) ). [Kryptering af dobbeltnøgle](encryption-sensitivity-labels.md#double-key-encryption) understøttes ikke for denne cmdlet.

Justeringsteksten føjes til [overvågningshændelsen](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities) for **Fjernede følsomhedsmærkat fra filen**, og dekrypteringshandlingen registreres også i [logføring af beskyttelse for Azure Information Protection](/azure/information-protection/log-analyze-usage).

## <a name="how-to-disable-sensitivity-labels-for-sharepoint-and-onedrive-opt-out"></a>Sådan deaktiverer du følsomhedsmærkater for SharePoint og OneDrive (fravalg)

Hvis du deaktiverer disse nye funktioner, vil filer, du har uploadet, efter at du har aktiveret følsomhedsmærkater for SharePoint og OneDrive fortsat være beskyttet af mærkaten, fordi etiketindstillingerne fortsat gennemtvinges. Når du anvender følsomhedsmærkater på nye filer, efter du har deaktiveret disse nye funktioner, fungerer fuldtekstsøgning, eDiscovery og samtidig redigering ikke længere.

Hvis du vil deaktivere disse nye funktioner, skal du bruge PowerShell. Brug SharePoint Online Management Shell og [Set-SPOTenant-cmdlet'en](/powershell/module/sharepoint-online/set-spotenant) til at angive den samme *EnableAIPIntegration-parameter*, som beskrevet i afsnittet [Brug PowerShell til at aktivere understøttelse af følsomhedsmærkater](#use-powershell-to-enable-support-for-sensitivity-labels). Men denne gang skal du angive parameterværdien til falsk og trykke på **Y** for at bekræfte:

```PowerShell
Set-SPOTenant -EnableAIPIntegration $false
```

Hvis du har Microsoft 365 Multi-Geo, skal du køre denne kommando for hver af dine geografiske placeringer.

## <a name="next-steps"></a>Næste trin

Når du har aktiveret følsomhedsmærkater for Office filer i SharePoint og OneDrive, kan du overveje automatisk at navngive disse filer ved hjælp af politikker for automatisk mærkning. Du kan finde flere oplysninger under [Anvend en følsomhedsmærkat på indhold automatisk](apply-sensitivity-label-automatically.md).

Har du brug for at dele dine navngivne og krypterede dokumenter med personer uden for din organisation?  Se [Deling af krypterede dokumenter med eksterne brugere](sensitivity-labels-office-apps.md#sharing-encrypted-documents-with-external-users).
