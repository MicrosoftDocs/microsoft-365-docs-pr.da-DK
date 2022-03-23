---
title: Almindelige politikker for nultillids identitet og enhedsadgang – Microsoft 365 til | Microsoft Docs
description: Beskriver de anbefalede almindelige nultillidsidentitets- og enhedsadgangspolitikker og -konfigurationer.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 08d15cacdd6b391759aeb1a22abd91c98376cd17
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591693"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Fælles politikker for nultillids identitet og enhedsadgang

I denne artikel beskrives de almindelige anbefalede politikker for nultillidsidentitet og enhedsadgang til sikring af adgang til Microsoft 365-skytjenester, herunder programmer i det lokale miljø, der er publiceret med Azure Active Directory-programproxy (Azure AD).

Denne vejledning beskriver, hvordan du installerer de anbefalede politikker i et nyligt klargjort miljø. Konfiguration af disse politikker i et separat laboratoriemiljø giver dig mulighed for at forstå og evaluere de anbefalede politikker, før du sætter kørslen i gang med dine præprodukt- og produktionsmiljøer. Dit nye klargjorte miljø kan være kun skybaseret eller hybridt for at afspejle dine evalueringsbehov.

## <a name="policy-set"></a>Politiksæt

Følgende diagram illustrerer det anbefalede sæt politikker. Den viser, hvilket niveau af beskyttelse hver politik gælder for, og om politikkerne gælder for pc'er eller telefoner og tablets eller begge kategorier af enheder. Den angiver også, hvor du konfigurerer disse politikker.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="Almindelige politikker til konfiguration af nultillidsidentitet og enhedsadgang." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::


<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)


--> 

I resten af denne artikel beskrives det, hvordan disse politikker konfigureres.

> [!NOTE]
> Det anbefales, at du kræver brug af multifaktorgodkendelse (MFA), før du tilmelder enheder i Intune for at sikre, at enheden er i den tilsigtede brugers adgang. Du skal tilmelde enheder i Intune, før du kan gennemtvinge politikker for enhedsoverholdelse.

For at give dig tid til at udføre disse opgaver anbefaler vi, at du implementerer startpolitikkerne i den rækkefølge, der er angivet i denne tabel. Men MFA-politikkerne for virksomhedssikkerhed og specialiserede sikkerhedsniveauer kan gennemføres når som helst.

|Beskyttelsesniveau|Politikker|Flere oplysninger|Licensering|
|---|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisici er *mellem* eller *høj*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Sikkerhed|
||[Blokere klienter, der ikke understøtter moderne godkendelse](#block-clients-that-dont-support-multi-factor)|Klienter, der ikke bruger moderne godkendelse, kan tilsidesætte Betingede adgangspolitikker, så det er vigtigt at blokere disse.|Microsoft 365 E3 eller E5|
||[Brugere med høj risiko skal ændre adgangskode](#high-risk-users-must-change-password)|Tvinger brugerne til at ændre deres adgangskode, når de logger på, hvis der registreres aktivitet med høj risiko for deres konto.|Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Sikkerhed|
||[Anvend politikker for programbeskyttelse (APP) databeskyttelse](#apply-app-data-protection-policies)|One Intune-politik for appbeskyttelse pr. platform (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 eller E5|
||[Kræv godkendte apps og appbeskyttelse](#require-approved-apps-and-app-protection)|Gennemtvinger beskyttelse af mobilapps til telefoner og tablets ved hjælp af iOS, iPadOS eller Android.|Microsoft 365 E3 eller E5|
|**Enterprise**|[Kræv MFA, når risikoen for *at logge på er* *lav, mellem* eller *høj*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Sikkerhed|
||[Definer politikker for enhedsoverholdelse](#define-device-compliance-policies)|Én politik for hver platform.|Microsoft 365 E3 eller E5|
||[Kræv kompatible pc'er og mobilenheder](#require-compliant-pcs-and-mobile-devices)|Gennemtvinger Intune-administration for både pc'er (Windows eller macOS) og telefoner eller tablets (iOS, iPadOS eller Android).|Microsoft 365 E3 eller E5|
|**Speciel sikkerhed**|[*Kræv* altid MFA](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 eller E5|
|

## <a name="assigning-policies-to-groups-and-users"></a>Tildele politikker til grupper og brugere

Inden du konfigurerer politikker, skal du identificere de Azure AD-grupper, du bruger til hvert niveau af beskyttelse. Beskyttelse på udgangspunktet gælder typisk for alle i organisationen. En bruger, der er inkluderet i både start- og virksomhedsbeskyttelsespolitikkerne, vil få anvendt alle startpolitikker samt virksomhedspolitikkerne. Beskyttelse er kumulativ, og den mest restriktive politik håndhæves.

Det anbefales, at du opretter en Azure AD-gruppe til udelukkelse af betinget adgang. Føj denne gruppe til alle dine Betingede adgangspolitikker i **indstillingen** Udelad værdien **for Brugere og** grupper i **sektionen** Tildelinger. Dette giver dig en metode til at give adgang til en bruger, mens du foretager fejlfinding af adgangsproblemer. Dette anbefales kun som en midlertidig løsning. Overvåg denne gruppe for ændringer, og sørg for, at udeladelsesgruppen kun bruges efter hensigten.

Her er et eksempel på gruppetildeling og udeladelse af krav til MFA.

![Eksempel på gruppetildeling og udeladelse af MFA-politikker.](../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png)

Her er resultaterne:

- Alle brugere skal bruge MFA, når risikoen for at logge på er mellem eller høj.

- Medlemmer af ledergruppen skal bruge MFA, når risikoen for at logge på er lav, mellem eller høj.

  I dette tilfælde matcher medlemmer af gruppen Ledelsesmedarbejdere både udgangspunktet og virksomhedens betingede adgangspolitikker. Adgangskontrolelementerne for begge politikker kombineres, hvilket i dette tilfælde svarer til virksomhedens betingede adgangspolitik.

- Medlemmer af gruppen Top Secret Project X skal altid bruge MFA

  I dette tilfælde svarer medlemmer af gruppen Top Secret Project X både udgangspunktet og specialiserede politikker for betinget adgang til sikkerhed. Adgangskontrolelementerne for begge politikker kombineres. Da adgangskontrol for den specialiserede politik for betinget adgang er mere restriktiv, bruges den.

Vær forsigtig, når du anvender højere beskyttelsesniveauer for grupper og brugere. Medlemmer af gruppen Top Secret Project X skal f.eks. bruge MFA, hver gang de logger på, også selvom de ikke arbejder på det specialiserede sikkerhedsindhold til Project X.

Alle Azure AD-grupper, der er oprettet som en del af disse anbefalinger, skal oprettes Microsoft 365 grupper. Dette er vigtigt for udrulningen af følsomhedsmærkater, når du sikrer dokumenter i Microsoft Teams og SharePoint.

![Eksempel på oprettelse af Microsoft 365 gruppe.](../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png)

## <a name="require-mfa-based-on-sign-in-risk"></a>Kræv MFA baseret på logonrisici

Du skal lade dine brugere registrere MFA, før du kræver, at de bruges. Hvis du har Microsoft 365 E5, Microsoft 365 E3 med E5 Security-tilføjelsesprogrammet, Office 365 med EMS E5 eller individuelle Azure AD Premium P2-licenser, kan du bruge MFA-registreringspolitikken med Azure AD Identity Protection til at kræve, at brugerne tilmelder sig MFA. Det [nødvendige arbejde](identity-access-prerequisites.md) omfatter registrering af alle brugere med MFA.

Når brugerne er registreret, kan du kræve MFA for at logge på med en ny politik for betinget adgang.

1. Gå til [Azure-portalen](https://portal.azure.com), og log på med dine legitimationsoplysninger.
2. På listen over Azure-tjenester skal du vælge **Azure Active Directory**.
3. På listen **Administrer** skal du vælge **Sikkerhed** og derefter vælge **Betinget adgang**.
4. Vælg **Ny politik** , og skriv navnet på den nye politik.

I følgende tabeller beskrives de betingede indstillinger for Access-politik, der kræver MFA baseret på logonrisici.

I **sektionen** Opgaver:

|Indstilling|Egenskaber|Værdier|Bemærkninger|
|---|---|---|---|
|Brugere og grupper|Medtag|**Vælg brugere og grupper > brugere og grupper**: Vælg bestemte grupper, der indeholder målrettede brugerkonti.|Start med den gruppe, der omfatter pilotbrugerkonti.|
||Udelad|**Brugere og grupper**: Vælg undtagelsesgruppen Betinget adgang. tjenestekonti (appidentiteter).|Medlemskab bør ændres midlertidigt efter behov.|
|Skyapps eller -handlinger|**Skyapps med > Inkluder**|**Vælg apps**: Vælg de apps, denne politik skal gælde for. Vælg f.eks Exchange Online.||
|Betingelser|||Konfigurer betingelser, der er specifikke for dit miljø og dine behov.|
||Risiko ved logon||Se vejledningen i følgende tabel.|
|

### <a name="sign-in-risk-condition-settings"></a>Indstillinger for risiko ved logon

Anvend indstillingerne for risikoniveau baseret på det beskyttelsesniveau, du målretter.

|Beskyttelsesniveau|Værdier på risikoniveau skal bruges|Handling|
|---|---|---|
|Udgangspunkt|Høj, mellem|Kontrollér begge dele.|
|Enterprise|Høj, mellem, lav|Markér alle tre.|
|Speciel sikkerhed||Lad alle indstillinger være umarkeret for altid at gennemtvinge MFA.|
|

I sektionen **Access-kontrolelementer** :

|Indstilling|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Giv|**Giv adgang**||Vælg|
|||**Kræv multifaktorgodkendelse**|Tjek|
||**Kræve alle de markerede kontrolelementer**||Vælg|
|

Vælg **Vælg** for at gemme **indstillingerne for Tildeling** .

Til sidst skal **du vælge** **Til for aktivér-politik** og derefter vælge **Opret**.

Overvej også at bruge [værktøjet Hvad hvis](/azure/active-directory/active-directory-conditional-access-whatif) til at teste politikken.

## <a name="block-clients-that-dont-support-multi-factor"></a>Bloker klienter, der ikke understøtter multifaktor

Brug indstillingerne i disse tabeller til en politik for Betinget adgang til at blokere klienter, der ikke understøtter multifaktorgodkendelse.

Se [denne artikel](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) for at få en liste over klienter Microsoft 365 der understøtter multifaktorgodkendelse.

I **sektionen** Opgaver:

|Indstilling|Egenskaber|Værdier|Bemærkninger|
|---|---|---|---|
|Brugere og grupper|Medtag|**Vælg brugere og grupper > brugere og grupper**: Vælg bestemte grupper, der indeholder målrettede brugerkonti.|Start med den gruppe, der omfatter pilotbrugerkonti.|
||Udelad|**Brugere og grupper**: Vælg undtagelsesgruppen Betinget adgang. tjenestekonti (appidentiteter).|Medlemskab bør ændres midlertidigt efter behov.|
|Skyapps eller -handlinger|**Skyapps med > Inkluder**|**Vælg apps**: Vælg de apps, der svarer til de klienter, der ikke understøtter moderne godkendelse.||
|Betingelser|**Klientapps**|Vælg **Ja** for **Konfigurer** <p> Fjern markeringen for Browser- **og** **Mobilapps og skrivebordsklienter**||
|

I sektionen **Access-kontrolelementer** :

|Indstilling|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Giv|**Bloker adgang**||Vælg|
||**Kræve alle de markerede kontrolelementer**||Vælg|
|

Vælg **Vælg** for at gemme **indstillingerne for Tildeling** .

Til sidst skal **du vælge** **Til for aktivér-politik** og derefter vælge **Opret**.

Overvej at bruge [værktøjet Hvad hvis](/azure/active-directory/active-directory-conditional-access-whatif) til at teste politikken.

For Exchange Online kan du bruge godkendelsespolitikker til at [deaktivere](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) Grundlæggende godkendelse, hvilket tvinger alle klientadgangsanmodninger til at bruge moderne godkendelse.

## <a name="high-risk-users-must-change-password"></a>Brugere med høj risiko skal ændre adgangskode

For at sikre, at alle brugere med høj risiko får kompromitterede konti gennemtvunget at udføre en ændring af adgangskoden, når du logger på, skal du anvende følgende politik.

Log på portalen [Microsoft Azure (https://portal.azure.com)](https://portal.azure.com/)med dine administratorlegitimationsoplysninger, og gå derefter til **Azure AD Identity Protection > politikken for brugerrisici**.

I **sektionen** Opgaver:

|Type|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Brugere|Medtag|**Alle brugere**|Vælg|
|Bruger risiko|**Høj**||Vælg|
|

I den **anden Opgavesektion** :

|Type|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Access|**Tillad adgang**||Vælg|
|||**Kræv ændring af adgangskode**|Tjek|
|

Vælg **Udført** for at gemme **Access-indstillingerne** .

Til sidst skal **du vælge Til** for **Gennemtving** politik og derefter vælge **Gem**.

Overvej at bruge [værktøjet Hvad hvis](/azure/active-directory/active-directory-conditional-access-whatif) til at teste politikken.

Brug denne politik sammen med Konfigurer [azure AD-adgangskodebeskyttelse](/azure/active-directory/authentication/concept-password-ban-bad), som registrerer og blokerer kendte svage adgangskoder og deres varianter og yderligere svage ord, der er specifikke for din organisation. Brug af Azure AD-adgangskodebeskyttelse sikrer, at ændrede adgangskoder er stærke.

## <a name="apply-app-data-protection-policies"></a>Anvend politikker for beskyttelse af app-data

API'er definerer, hvilke apps der er tilladte, og de handlinger, de kan udføre med din organisations data. Valgmulighederne i APP giver organisationer mulighed for at skræddersy beskyttelsen til deres specifikke behov. For nogle er det muligvis ikke indlysende, hvilke politikindstillinger der kræves for at implementere et fuldstændigt scenarie. For at hjælpe organisationer med at prioritere harde på mobilklientens slutpunkter har Microsoft indført taksonomi for sin ramme for app-databeskyttelse til administration af mobilapps i iOS og Android.

Rammen for app-databeskyttelse er organiseret i tre forskellige konfigurationsniveauer, hvor hvert niveau bygger ud over det forrige niveau:

- **Niveau 1: Grundlæggende beskyttelse af virksomhedsdata** sikrer, at apps er beskyttet med en pinkode og krypteret og udfører selektiv sletning. For Android-enheder validerer dette niveau Android-enheds bekræftelse. Dette er en konfiguration på indtastningsniveau, der giver tilsvarende databeskyttelseskontrol i Exchange Online-postkassepolitikker og introducerer IT og brugerens befolkning til APP.
- **Niveau 2: Enterprise Enhanced Data Protection introducerer** mekanismer til forebyggelse af lækage af appdata og minimumskrav til operativsystemet. Dette er den konfiguration, der gælder for de fleste mobilbrugere, der har adgang til arbejds- eller skoledata.
- **Niveau 3: Virksomhedens høje databeskyttelse introducerer** avancerede databeskyttelsesmekanismer, forbedret pinkodekonfiguration og APP Mobile Threat Defense. Denne konfiguration er ønskede for brugere, der tilgår data med høj risiko.

Hvis du vil have vist specifikke anbefalinger for hvert konfigurationsniveau og minimumskravene til apps, der skal beskyttes, skal du gennemgå [Rammen for databeskyttelse ved hjælp af politikker for beskyttelse af apps](/mem/intune/apps/app-protection-framework).

Med udgangspunkt i de principper, der er beskrevet i [Konfigurationer af Zero Trust-identitet](microsoft-365-policies-configurations.md) og enhedsadgang, knyttes udgangspunktet og Enterprise Protection-niveauerne tæt sammen med niveau 2-niveauerne for virksomhedens forbedrede indstillinger for databeskyttelse. Det specialiserede sikkerhedsbeskyttelsesniveau er tæt forbundet med niveau 3-indstillingerne for virksomhedssikkerhed.

|Beskyttelsesniveau|Politik for appbeskyttelse|Flere oplysninger|
|---|---|---|
|Udgangspunkt|[Niveau 2 forbedret databeskyttelse](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Politikindstillingerne, der håndhæves på niveau 2, omfatter alle de politikindstillinger, der anbefales til niveau 1, og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.|
|Enterprise|[Niveau 2 forbedret databeskyttelse](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Politikindstillingerne, der håndhæves på niveau 2, omfatter alle de politikindstillinger, der anbefales til niveau 1, og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.|
|Speciel sikkerhed|[Niveau 3 til virksomheder høj databeskyttelse](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Politikindstillingerne, der håndhæves på niveau 3, omfatter alle de politikindstillinger, der anbefales til niveau 1 og 2 og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 2.|
|

Hvis du vil oprette en ny politik for beskyttelse af apps til hver platform (iOS og Android) inden for Microsoft Endpoint Manager brug af indstillingerne for databeskyttelse, kan du:

1. Opret politikkerne manuelt ved at følge trinnene i [Sådan oprettes og installeres politikker for appbeskyttelse Microsoft Intune](/mem/intune/apps/app-protection-policies).
2. Importér eksempler på [JSON-skabeloner for Intune App Protection Policy Configuration Framework](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) [med Intunes PowerShell-scripts](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Kræv godkendte apps og APP-beskyttelse

Hvis du vil gennemtvinge de politikker for appbeskyttelse, du har anvendt i Intune, skal du oprette en politik for Betinget adgang, så der kræves godkendte klientapps og de betingelser, der er angivet i appbeskyttelsespolitikkerne.

Gennemtvingelse af politikker for appbeskyttelse kræver et sæt af politikker, der er beskrevet i [Kræv appbeskyttelsespolitik for appadgang i skyen med Betinget adgang](/azure/active-directory/conditional-access/app-protection-based-conditional-access). Disse politikker er hver især inkluderet i dette anbefalede sæt identitets- og adgangskonfigurationspolitikker.

Hvis du vil oprette politikken Betinget adgang, der kræver godkendt apps og appbeskyttelse, skal du følge trinnene i Kræv godkendte klientapps eller appbeskyttelsespolitik med mobilenheder[, som](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices) kun tillader konti i mobilapps beskyttet af politikker for appbeskyttelse at få adgang til Microsoft 365-slutpunkter.

   > [!NOTE]
   > Denne politik sikrer, at mobilbrugere kan få adgang til Microsoft 365 slutpunkter ved hjælp af de relevante apps.

Denne politik blokerer Exchange ActiveSync klienter på mobilenheder fra at oprette forbindelse til Exchange Online. Du kan dog oprette en separat politik for håndtering af Exchange ActiveSync på tværs af alle enheder. Få mere at vide under [Bloker ActiveSync-klienter](secure-email-recommended-policies.md#block-activesync-clients), som forhindrer Exchange ActiveSync klienter, der udnytter grundlæggende godkendelse, i at oprette forbindelse til Exchange Online. Denne politik vises ikke i illustrationen øverst i denne artikel. Det beskrives og vises i [Politikanbefalinger til sikring af mail](secure-email-recommended-policies.md).

 Denne politik udnytter kontrolelementerne Kræv [godkendt klientapp og](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) [Kræv beskyttelsespolitik for apps](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Endelig sikrer blokering af ældre godkendelse for andre klientapps på iOS- og Android-enheder, at disse klienter ikke kan tilsidesætte betingede Access-politikker. Hvis du følger vejledningen i denne artikel, har du allerede konfigureret Bloker klienter [, der ikke understøtter moderne godkendelse](#block-clients-that-dont-support-multi-factor).

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>Definer politikker for enhedsoverholdelse

Politikker for enhedsoverholdelse definerer de krav, som enhederne skal opfylde for at kunne overholde kravene. Du kan oprette Politikker for overholdelse af enhed i Intune i Microsoft Endpoint Manager Administration.

Du skal oprette en politik for hver pc, telefon eller tabletplatform:

- Android-enhedsadministrator
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 og nyere
- Windows 10 og nyere

Hvis du vil oprette politikker for enhedsoverholdelse, [skal du logge på Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com) med dine administratorlegitimationsoplysninger og  \> derefter gå til Politikker for overholdelse **af politikker for enhedsoverholdelse**\>. Vælg **Opret politik**.

For at politikker for enhedsoverholdelse skal installeres, skal de tildeles til brugergrupper. Du tildeler en politik, efter du har oprettet og gemt den. Vælg politikken i Administration, og vælg derefter **Opgaver**. Når du har valgt de grupper, du vil modtage politikken for, skal du vælge **Gem** for at gemme gruppetildelingen og implementere politikken.

Du kan finde en trinvis vejledning til oprettelse af overholdelsespolitikker i Intune under Opret en politik for overholdelse [af regler og standarder Microsoft Intune](/mem/intune/protect/create-compliance-policy) i Intune-dokumentationen.

### <a name="recommended-settings-for-ios"></a>Anbefalede indstillinger for iOS

iOS/iPadOS understøtter flere registreringsscenarier, hvoraf to er dækket som en del af denne struktur:

- [Tilmelding af enheder til personligt ejet enheder](/mem/intune/enrollment/ios-enroll) – disse enheder ejes personligt og bruges både til arbejdsbrug og personlig brug.
- [Overvågede automatiserede enhedsregistrering](/mem/intune/enrollment/device-enrollment-program-enroll-ios) til virksomhedsejede enheder – disse enheder ejes i virksomheden, er knyttet til en enkelt bruger og bruges kun til arbejde og ikke personlig brug.

Sikkerhedskonfigurationsrammen for iOS/iPadOS er organiseret i flere forskellige konfigurationsscenarier, hvilket giver vejledning til personligt ejet og overvågede enheder.

Til personligt ejet enheder:

- Grundlæggende sikkerhed (niveau 1) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfigurationen for personlige enheder, hvor brugere får adgang til arbejds- eller skoledata. Dette gøres ved at gennemtvinge adgangskodepolitikker, enhedslåsning og deaktivere visse enhedsfunktioner (f.eks. certifikater, der ikke er tillid til).
- Øget sikkerhed (niveau 2) – Microsoft anbefaler denne konfiguration til enheder, hvor brugere får adgang til følsomme eller fortrolige oplysninger. Denne konfiguration kontrollerer datadeling. Denne konfiguration gælder for de fleste mobilbrugere, der har adgang til arbejds- eller skoledata på en enhed.
- Høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration til enheder, der bruges af bestemte brugere eller grupper, som hver især har en høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret videregivelse medfører betydelige materialetab for organisationen). Denne konfiguration håndhæver stærkere adgangskodepolitikker, deaktiverer visse enhedsfunktioner og gennemtvinger yderligere begrænsninger for dataoverførsel.

Til overvågede enheder:

- Grundlæggende sikkerhed (niveau 1) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfigurationen for overvågede enheder, hvor brugere får adgang til arbejds- eller skoledata. Dette gøres ved at gennemtvinge adgangskodepolitikker, enhedslåsning og deaktivere visse enhedsfunktioner (f.eks. certifikater, der ikke er tillid til).
- Øget sikkerhed (niveau 2) – Microsoft anbefaler denne konfiguration til enheder, hvor brugere får adgang til følsomme eller fortrolige oplysninger. Denne konfiguration kontrollerer datadeling og blokerer adgang til USB-enheder. Denne konfiguration gælder for de fleste mobilbrugere, der har adgang til arbejds- eller skoledata på en enhed.
- Høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration til enheder, der bruges af bestemte brugere eller grupper, som hver især har en høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret videregivelse medfører betydelige materialetab for organisationen). Denne konfiguration har stærkere adgangskodepolitikker, deaktiverer visse enhedsfunktioner, håndhæver yderligere begrænsninger for dataoverførsel og kræver, at apps installeres via Apples volumenkøbsprogram.

Med udgangspunkt i de principper, der er beskrevet i [Konfigurationer af Zero Trust-identitet](microsoft-365-policies-configurations.md) og enhedsadgang, knyttes udgangspunktet og Enterprise Protection-niveauerne tæt sammen med niveau 2-forbedrede sikkerhedsindstillinger. Det specialiserede sikkerhedsbeskyttelsesniveau er tæt forbundet med niveau 3-sikkerhedsindstillingerne.

|Beskyttelsesniveau  |Enhedspolitik |Flere oplysninger  |
|---------|---------|---------|
|Udgangspunkt     |Udvidet sikkerhed (niveau 2)         |Politikindstillingerne, der håndhæves på niveau 2, omfatter alle de politikindstillinger, der anbefales til niveau 1, og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Enterprise     |Udvidet sikkerhed (niveau 2)         |Politikindstillingerne, der håndhæves på niveau 2, omfatter alle de politikindstillinger, der anbefales til niveau 1, og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Speciel sikkerhed     |Høj sikkerhed (niveau 3)         |Politikindstillingerne, der håndhæves på niveau 3, omfatter alle de politikindstillinger, der anbefales til niveau 1 og 2 og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 2.         |

Hvis du vil have vist specifikke anbefalinger om enhedsoverholdelse og enhedsbegrænsning for hvert konfigurationsniveau, skal du se [iOS/iPadOS Security Configuration Framework](/mem/intune/enrollment/ios-ipados-configuration-framework).

### <a name="recommended-settings-for-android"></a>Anbefalede indstillinger for Android

Android Enterprise understøtter flere registreringsscenarier, hvoraf to er dækket som en del af denne struktur:

- [Android Enterprise-arbejdsprofil](/intune/android-work-profile-enroll) – denne registreringsmodel bruges typisk til personligtejede enheder, hvor it-virksomheden ønsker at give en klar adskillelsesgrænse mellem arbejds- og personlige data. Politikker, der styres af IT, sikrer, at arbejdsdata ikke kan overføres til den personlige profil.
- [Android Enterprise fuldt administrerede](/intune/android-fully-managed-enroll) enheder – disse enheder ejes af virksomheden, er knyttet til en enkelt bruger og bruges udelukkende til arbejde og ikke personlig brug.

Sikkerhedskonfigurationsrammen for Android Enterprise er organiseret i flere forskellige konfigurationsscenarier, hvilket giver vejledning til arbejdsprofil og fuldt administrerede scenarier.

Til Android Enterprise-arbejdsprofilenheder:

- Øget sikkerhed på arbejdsprofil (niveau 2) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfigurationen for personlige enheder, hvor brugere får adgang til arbejds- eller skoledata. Denne konfiguration introducerer krav til adgangskoder, adskiller arbejds- og personlige data og validerer Android-enhedens udtale.
- Arbejdsprofil høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration til enheder, der bruges af bestemte brugere eller grupper, som hver især har en høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret videregivelse medfører betydelige materialetab for organisationen). Denne konfiguration introducerer beskyttelse mod mobilenheder eller Microsoft Defender til slutpunkt, indstiller minimumversionen af Android, indfører stærkere adgangskodepolitikker og begrænser yderligere arbejdsadskillelse og personlig adskillelse.

Til Android Enterprise-enheder, der er fuldt administreret:

- Fuldstændig administreret grundlæggende sikkerhed (niveau 1) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfigurationen for en virksomhedsenhed. Denne konfiguration gælder for de fleste mobilbrugere, der har adgang til arbejds- eller skoledata. Denne konfiguration introducerer krav til adgangskode, angiver minimumversionen af Android og indfører visse enhedsbegrænsninger.
- Fuldt administreret udvidet sikkerhed (niveau 2) – Microsoft anbefaler denne konfiguration til enheder, hvor brugere får adgang til følsomme eller fortrolige oplysninger. Denne konfiguration aktiverer stærkere adgangskodepolitikker og deaktiverer egenskaber for bruger/konto.
- Fuldt administreret høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration for enheder, der bruges af bestemte brugere eller grupper, som hver især har en høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret videregivelse medfører betydelige materialetab for organisationen). Denne konfiguration øger minimumversionen af Android, introducerer mobiltrusler eller Microsoft Defender til slutpunkt og håndhæver yderligere enhedsbegrænsninger.

Ved hjælp af de principper, der er beskrevet i [Konfigurationer af Zero Trust-identitet](microsoft-365-policies-configurations.md) og enhedsadgang, knyttes startniveau og Enterprise Protection-niveau tæt sammen med niveau 1-grundlæggende sikkerhed for personligt ejet enheder og niveau 2-udvidede sikkerhedsindstillinger for fuldt administrerede enheder. Det specialiserede sikkerhedsbeskyttelsesniveau er tæt forbundet med niveau 3-sikkerhedsindstillingerne.

Til Android Enterprise-arbejdsprofilenheder:

|Beskyttelsesniveau  |Enhedspolitik |Flere oplysninger  |
|---------|---------|---------|
|Udgangspunkt     |Arbejdsprofil: Grundlæggende sikkerhed (niveau 1)      |I/T         |
|Enterprise     |Arbejdsprofil: Grundlæggende sikkerhed (niveau 1)         |I/T         |
|Udgangspunkt     |Fuldt administreret: Udvidet sikkerhed (niveau 2)       |Politikindstillingerne, der håndhæves på niveau 2, omfatter alle de politikindstillinger, der anbefales til niveau 1, og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Enterprise     |Fuldt administreret: Udvidet sikkerhed (niveau 2)         |Politikindstillingerne, der håndhæves på niveau 2, omfatter alle de politikindstillinger, der anbefales til niveau 1, og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Speciel sikkerhed     |Høj sikkerhed (niveau 3)         |Politikindstillingerne, der håndhæves på niveau 3, omfatter alle de politikindstillinger, der anbefales til niveau 1 og 2 og tilføjer eller opdaterer kun nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 2.         |

Hvis du vil se specifikke anbefalinger om enhedsoverholdelse og enhedsbegrænsning for hvert konfigurationsniveau, skal du se [Android Enterprise Security Configuration Framework](/mem/intune/enrollment/android-configuration-framework).

### <a name="recommended-settings-for-windows-10-and-later"></a>Anbefalede indstillinger for Windows 10 og nyere

Følgende indstillinger anbefales til pc'er, der kører Windows 10 og nyere, som konfigureret i Trin **2:** Overholdelsesindstillinger for processen til oprettelse af politikker.

Du **kan finde flere > Windows om evalueringsregler for enhedstilstand i** denne tabel.

|Egenskaber|Værdi|Handling|
|---|---|---|
|Kræv BitLocker|Kræv|Vælg|
|Kræv, at Secure Boot er aktiveret på enheden|Kræv|Vælg|
|Kræve kodeintegritet|Kræv|Vælg|
|

For **Enhedsegenskaber skal** du angive relevante værdier for operativsystemversioner baseret på it og sikkerhedspolitikker.

Vælg **Kræv Konfigurationsstyring** for at sikre **overholdelse af regler og standarder**.

Du **kan se Systemsikkerhed** i denne tabel.

|Type|Egenskaber|Værdi|Handling|
|---|---|---|---|
|Adgangskode|Kræv en adgangskode for at låse mobilenheder op|Kræv|Vælg|
||Simple adgangskoder|Bloker|Vælg|
||Adgangskodetype|Standardenhed|Vælg|
||Minimum adgangskodelængde|6|Type|
||Maksimalt antal minutters inaktivitet, før adgangskoden er påkrævet|15|Type <p> Denne indstilling understøttes for Android-versionerne 4.0 og nyere eller KNOX 4.0 og nyere. For iOS-enheder understøttes det iOS 8.0 og derover.|
||Udløb af adgangskode (dage)|41|Type|
||Antal tidligere adgangskoder for at forhindre genbrug|5|Type|
||Kræv adgangskode, når enheden returnerer fra inaktiv tilstand (mobil og holografisk)|Kræv|Tilgængelig til Windows 10 og nyere|
|Kryptering|Kryptering af datalager på enhed|Kræv|Vælg|
|Enhedssikkerhed|Firewall|Kræv|Vælg|
||Antivirus|Kræv|Vælg|
||Antispyware|Kræv|Vælg <p> Denne indstilling kræver en antis spyware-løsning, der er registreret i Windows Sikkerhed appen.|
|Defender til skyen|Microsoft Defender Antimalware|Kræv|Vælg|
||Minimumversion af Microsoft Defender Antimalware||Type <p> Understøttes kun til Windows 10 skrivebord. Microsoft anbefaler versioner, der højst er fem bagud i forhold til den nyeste version.|
||Microsoft Defender Antimalware-signatur opdateret|Kræv|Vælg|
||Beskyttelse i realtid|Kræv|Vælg <p> Understøttes kun til Windows 10 og nyere computere|
|

#### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender til Slutpunkt

|Type|Egenskaber|Værdi|Handling|
|---|---|---|---|
|Microsoft Defender for Endpoint-regler Microsoft Endpoint Manager Administration|[Kræv, at enheden er på eller under scoren for maskinrisici](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Mellem|Vælg|
|

<!--
## Require compliant PCs (but not compliant phones and tablets)

Before adding a policy to require compliant PCs, be sure to enroll your devices for management in Intune. Using multi-factor authentication is recommended before enrolling devices into Intune for assurance that the device is in the possession of the intended user.

To require compliant PCs:

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials.
2. In the list of Azure services, choose **Azure Active Directory**.
3. In the **Manage** list, choose **Security**, and then choose **Conditional Access**.
4. Choose **New policy** and type the new policy's name.

5. Under **Assignments**, choose **Users and groups** and include who you want the policy to apply to. Also exclude your Conditional Access exclusion group.

6. Under **Assignments**, choose **Cloud apps or actions**.

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the **Cloud apps** list. For example, select Office 365. Choose **Select** when done.

8. To require compliant PCs (but not compliant phones and tablets), under **Assignments**, choose **Conditions > Device platforms**. Select **Yes** for **Configure**. Choose  **Select device platforms**, select **Yes** and select **Any device** and under Exclude select **iOS** and **Android**, and then choose **Done**.

9. Under **Access controls**, choose **Grant** .

10. Choose **Grant access** and then check **Require device to be marked as compliant**. For multiple controls, select **Require all the selected controls**. When complete, choose **Select**.

11. Select **On** for **Enable policy**, and then choose **Create**.

> [!NOTE]
> Make sure that your device is compliant before enabling this policy. Otherwise, you could get locked out and will be unable to change this policy until your user account has been added to the Conditional Access exclusion group.

--> 

## <a name="require-compliant-pcs-and-mobile-devices"></a>Kræv kompatible pc'er og mobilenheder

Sådan kræver du overholdelse for alle enheder:

1. Gå til [Azure-portalen](https://portal.azure.com), og log på med dine legitimationsoplysninger.
2. På listen over Azure-tjenester skal du vælge **Azure Active Directory**.
3. På listen **Administrer** skal du vælge **Sikkerhed** og derefter vælge **Betinget adgang**.
4. Vælg **Ny politik** , og skriv navnet på den nye politik.

5. Under **Tildelinger skal** du **vælge Brugere og grupper** og medtage, hvem politikken skal gælde for. Du kan også udelade udeladelsesgruppen Betinget adgang.

6. Under **Opgaver skal du** vælge **Skyapps eller -handlinger**.

7. Under **Medtag** skal **du vælge Vælg > Vælg** og derefter vælge de ønskede apps på listen **Skyapps** . Vælg f.eks Office 365. Vælg **Vælg,** når du er færdig.

8. Under **Access-kontrolelementer** skal du **vælge Tildr** .

9. Vælg **Giv adgang,** og markér derefter **Kræv, at en enhed er markeret som kompatibel**. For flere kontrolelementer skal du **vælge Kræv alle de markerede kontrolelementer**. Vælg Vælg, når du er **færdig**.

10. Vælg **Til** for **aktivér politik**, og vælg derefter **Opret**.

> [!NOTE]
> Sørg for, at din enhed er kompatibel, før du aktiverer denne politik. Ellers kan du blive låst ude og kan ikke ændre denne politik, før din brugerkonto er blevet føjet til udelukkelsesgruppen Betinget adgang.

## <a name="next-step"></a>Næste trin

[![Trin 3: Politikker for gæster og eksterne brugere.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png)](identity-access-policies-guest-access.md)

[Få mere at vide om politikanbefalinger for gæster og eksterne brugere](identity-access-policies-guest-access.md)
