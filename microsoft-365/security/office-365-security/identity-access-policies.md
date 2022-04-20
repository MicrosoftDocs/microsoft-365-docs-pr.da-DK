---
title: Almindelige politikker for identitets- og enhedsadgang for Nul tillid – Microsoft 365 for virksomheds-| Microsoft Docs
description: Beskriver de anbefalede almindelige Nul tillid politikker og konfigurationer for identitets- og enhedsadgang.
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
ms.openlocfilehash: 0c7facc2ac5a20b21a6862b115b62c576ebaeb1f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972183"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Almindelige politikker for identitet og enhedsadgang Nul tillid

I denne artikel beskrives de almindelige anbefalede Nul tillid politikker for identitets- og enhedsadgang til sikring af adgang til Microsoft 365 cloudtjenester, herunder programmer i det lokale miljø, der er publiceret med Azure Active Directory (Azure AD) Programproxy.

I denne vejledning beskrives det, hvordan du installerer de anbefalede politikker i et nyligt klargjort miljø. Når du konfigurerer disse politikker i et separat laboratoriemiljø, kan du forstå og evaluere de anbefalede politikker, før udrulningen gemmes i dine præproduktions- og produktionsmiljøer. Dit nyligt klargjorte miljø kan være skybaseret eller hybridt, så det afspejler dine evalueringsbehov.

## <a name="policy-set"></a>Politiksæt

I følgende diagram illustreres det anbefalede sæt politikker. Den viser, hvilket beskyttelsesniveau hver politik gælder for, og om politikkerne gælder for pc'er, telefoner og tablets eller begge kategorier af enheder. Det angiver også, hvor du konfigurerer disse politikker.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="De almindelige politikker til konfiguration af Nul tillid identitet og enhedsadgang." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::

<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)

-->

I resten af denne artikel beskrives det, hvordan du konfigurerer disse politikker.

> [!NOTE]
> Det anbefales, at du kræver multifaktorgodkendelse, før du tilmelder enheder i Intune for at sikre, at enheden er i den tilsigtede brugers besiddelse. Du skal tilmelde enheder i Intune, før du kan gennemtvinge politikker for enhedsoverholdelse.

For at give dig tid til at udføre disse opgaver anbefaler vi, at du implementerer startpunktpolitikkerne i den rækkefølge, der er angivet i denne tabel. MFA-politikkerne for virksomhedsrelaterede og specialiserede beskyttelsesniveauer kan dog til enhver tid implementeres.

|Beskyttelsesniveau|Politikker|Flere oplysninger|Licensering|
|---|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisikoen er *mellem* eller *høj*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Security|
||[Bloker klienter, der ikke understøtter moderne godkendelse](#block-clients-that-dont-support-multi-factor)|Klienter, der ikke bruger moderne godkendelse, kan tilsidesætte politikker for betinget adgang, så det er vigtigt at blokere disse.|Microsoft 365 E3 eller E5|
||[Brugere med høj risiko skal ændre adgangskode](#high-risk-users-must-change-password)|Tvinger brugerne til at ændre deres adgangskode, når de logger på, hvis der registreres højrisikoaktivitet for deres konto.|Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Security|
||[Anvend app-databeskyttelse (Application Protection Policies)](#apply-app-data-protection-policies)|En Intune appbeskyttelsespolitik pr. platform (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 eller E5|
||[Kræv godkendt app- og appbeskyttelse](#require-approved-apps-and-app-protection)|Gennemtvinger beskyttelse af mobilapps til telefoner og tablets ved hjælp af iOS, iPadOS eller Android.|Microsoft 365 E3 eller E5|
|**Enterprise**|[Kræv MFA, når logonrisikoen er *lav*, *mellem* eller *høj*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelsesprogrammet E5 Security|
||[Definer politikker for enhedsoverholdelse](#define-device-compliance-policies)|Én politik for hver platform.|Microsoft 365 E3 eller E5|
||[Kræv kompatible pc'er og mobilenheder](#require-compliant-pcs-and-mobile-devices)|Gennemtvinger Intune administration for både pc'er (Windows eller macOS) og telefoner eller tablets (iOS, iPadOS eller Android).|Microsoft 365 E3 eller E5|
|**Specialiseret sikkerhed**|[*Kræv altid* MFA](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 eller E5|

## <a name="assigning-policies-to-groups-and-users"></a>Tildeling af politikker til grupper og brugere

Før du konfigurerer politikker, skal du identificere de Azure AD-grupper, du bruger til hvert beskyttelsesniveau. Startpunktbeskyttelse gælder typisk for alle i organisationen. En bruger, der er inkluderet til både startpunkt og virksomhedsbeskyttelse, anvender alle startpunktspolitikker samt virksomhedspolitikkerne. Beskyttelse er kumulativ, og den mest restriktive politik gennemtvinges.

En anbefalet praksis er at oprette en Azure AD-gruppe til udeladelse af betinget adgang. Føj denne gruppe til alle dine politikker for betinget adgang i indstillingen **Udelad** for indstillingen **Brugere og grupper** i afsnittet **Tildelinger** . Dette giver dig en metode til at give adgang til en bruger, mens du foretager fejlfinding af adgangsproblemer. Dette anbefales kun som en midlertidig løsning. Overvåg denne gruppe for ændringer, og sørg for, at udeladelsesgruppen kun bruges efter hensigten.

Her er et eksempel på gruppetildelinger og udeladelser, der kræver MFA.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png" alt-text="Eksempel på gruppetildeling og -udeladelser for MFA-politikker" lightbox="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png":::

Her er resultaterne:

- Alle brugere skal bruge MFA, når logonrisikoen er mellem eller høj.

- Medlemmer af gruppen Af direktører skal bruge MFA, når logonrisikoen er lav, mellem eller høj.

  I dette tilfælde matcher medlemmer af gruppen Ledende medarbejdere både startpunktet og virksomhedens politikker for betinget adgang. Adgangskontrollerne for begge politikker kombineres, hvilket i dette tilfælde svarer til virksomhedens politik for betinget adgang.

- Medlemmer af gruppen Tophemmelighed Project X skal altid bruge MFA

  I dette tilfælde matcher medlemmer af gruppen Tophemmelighed Project X både startpunktet og de specialiserede politikker for betinget adgang til sikkerhed. Adgangskontrolelementerne for begge politikker kombineres. Da adgangskontrol for den specialiserede politik for betinget adgang til sikkerhed er mere restriktiv, bruges den.

Vær forsigtig, når du anvender højere beskyttelsesniveauer på grupper og brugere. Medlemmer af gruppen Tophemmelighed Project X skal f.eks. bruge MFA, hver gang de logger på, selvom de ikke arbejder med det specialiserede sikkerhedsindhold til Project X.

Alle Azure AD-grupper, der er oprettet som en del af disse anbefalinger, skal oprettes som Microsoft 365 grupper. Dette er vigtigt for udrulningen af følsomhedsmærkater, når dokumenter beskyttes i Microsoft Teams og SharePoint.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png" alt-text="Oprettelse af en Microsoft 365 gruppe" lightbox="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png":::

## <a name="require-mfa-based-on-sign-in-risk"></a>Kræv MFA baseret på logonrisiko

Du skal have dine brugere til at tilmelde sig MFA, før de skal bruge den. Hvis du har Microsoft 365 E5, Microsoft 365 E3 med tilføjelsesprogrammet E5 Security, Office 365 med EMS E5 eller individuelle Azure AD Premium P2-licenser, kan du bruge MFA-registreringspolitikken med Azure AD Identity Protection til at kræve, at brugerne tilmelder sig MFA. Det [nødvendige arbejde](identity-access-prerequisites.md) omfatter registrering af alle brugere med MFA.

Når dine brugere er registreret, kan du kræve MFA til logon med en ny politik for betinget adgang.

1. Gå til [Azure Portal](https://portal.azure.com), og log på med dine legitimationsoplysninger.
2. Vælg **Azure Active Directory** på listen over Azure-tjenester.
3. Vælg **Sikkerhed** på listen **Administrer**, og vælg derefter **Betinget adgang**.
4. Vælg **Ny politik** , og skriv navnet på den nye politik.

I følgende tabeller beskrives politikindstillingerne for betinget adgang for at kræve MFA baseret på logonrisiko.

I afsnittet **Tildelinger** :

|Indstilling|Egenskaber|Værdier|Bemærkninger|
|---|---|---|---|
|Brugere og grupper|Omfatter|**Vælg brugere og grupper > Brugere og grupper**: Vælg bestemte grupper, der indeholder målrettede brugerkonti.|Start med den gruppe, der indeholder pilotbrugerkonti.|
||Udelukke|**Brugere og grupper**: Vælg undtagelsesgruppen Betinget adgang. tjenestekonti (app-identiteter).|Medlemskabet bør ændres efter behov og midlertidigt.|
|Cloudapps eller -handlinger|**Cloudapps > inkludere**|**Vælg apps**: Vælg de apps, som politikken skal gælde for. Vælg f.eks. Exchange Online.||
|Betingelser|||Konfigurer betingelser, der er specifikke for dit miljø og dine behov.|
||Logonrisiko||Se vejledningen i følgende tabel.|

### <a name="sign-in-risk-condition-settings"></a>Indstillinger for logonrisikotilstand

Anvend indstillingerne for risikoniveau baseret på det beskyttelsesniveau, du er målrettet mod.

|Beskyttelsesniveau|Der kræves værdier på risikoniveau|Handling|
|---|---|---|
|Udgangspunkt|Høj, mellem|Tjek begge dele.|
|Enterprise|Høj, mellem, lav|Tjek alle tre.|
|Specialiseret sikkerhed||Lad alle indstillinger være umarkerede for altid at gennemtvinge MFA.|

I afsnittet **Adgangskontrolelementer** :

|Indstilling|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Give|**Giv adgang**||Vælg|
|||**Kræv multifaktorgodkendelse**|Kontrollere|
||**Kræv alle de markerede kontrolelementer**||Vælg|

Vælg **Vælg** for at gemme **grant-indstillingerne** .

Til sidst skal du vælge **Til** for **Aktivér politik** og derefter vælge **Opret**.

Overvej også at bruge [What if-værktøjet](/azure/active-directory/active-directory-conditional-access-whatif) til at teste politikken.

## <a name="block-clients-that-dont-support-multi-factor"></a>Bloker klienter, der ikke understøtter multifaktor

Brug indstillingerne i disse tabeller for en politik for betinget adgang til at blokere klienter, der ikke understøtter multifaktorgodkendelse.

I [denne artikel](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) kan du se en liste over klienter i Microsoft 365, der understøtter multifaktorgodkendelse.

I afsnittet **Tildelinger** :

|Indstilling|Egenskaber|Værdier|Bemærkninger|
|---|---|---|---|
|Brugere og grupper|Omfatter|**Vælg brugere og grupper > Brugere og grupper**: Vælg bestemte grupper, der indeholder målrettede brugerkonti.|Start med den gruppe, der indeholder pilotbrugerkonti.|
||Udelukke|**Brugere og grupper**: Vælg undtagelsesgruppen Betinget adgang. tjenestekonti (app-identiteter).|Medlemskabet bør ændres efter behov og midlertidigt.|
|Cloudapps eller -handlinger|**Cloudapps > inkludere**|**Vælg apps**: Vælg de apps, der svarer til de klienter, der ikke understøtter moderne godkendelse.||
|Betingelser|**Klientapps**|Vælg **Ja** for **Konfigurer** <p> Fjern markeringerne for **browser-** og **mobilapps og skrivebordsklienter**||

I afsnittet **Adgangskontrolelementer** :

|Indstilling|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Give|**Bloker adgang**||Vælg|
||**Kræv alle de markerede kontrolelementer**||Vælg|

Vælg **Vælg** for at gemme **grant-indstillingerne** .

Til sidst skal du vælge **Til** for **Aktivér politik** og derefter vælge **Opret**.

Overvej at bruge [What if-værktøjet](/azure/active-directory/active-directory-conditional-access-whatif) til at teste politikken.

I forbindelse med Exchange Online kan du bruge godkendelsespolitikker til at [deaktivere basisgodkendelse](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), hvilket tvinger alle anmodninger om klientadgang til at bruge moderne godkendelse.

## <a name="high-risk-users-must-change-password"></a>Brugere med høj risiko skal ændre adgangskode

Hvis du vil sikre, at alle kompromitterede konti for brugere med høj risiko tvinges til at udføre en adgangskodeændring, når du logger på, skal du anvende følgende politik.

Log på [Microsoft Azure-portalen (https://portal.azure.com)](https://portal.azure.com/) med dine administratorlegitimationsoplysninger, og naviger derefter til **Azure AD Identity Protection > User Risk Policy**.

I afsnittet **Tildelinger** :

|Type|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Brugere|Omfatter|**Alle brugere**|Vælg|
|Brugerrisiko|**Høj**||Vælg|

I det andet afsnit **Tildelinger** :

|Type|Egenskaber|Værdier|Handling|
|---|---|---|---|
|Access|**Tillad adgang**||Vælg|
|||**Kræv ændring af adgangskode**|Kontrollere|

Vælg **Udført** for at gemme **Access-indstillingerne** .

Til sidst skal du vælge **Til** for **Gennemtving politik** og derefter vælge **Gem**.

Overvej at bruge [What if-værktøjet](/azure/active-directory/active-directory-conditional-access-whatif) til at teste politikken.

Brug denne politik sammen med [Konfigurer Adgangskodebeskyttelse i Azure AD](/azure/active-directory/authentication/concept-password-ban-bad), som registrerer og blokerer kendte svage adgangskoder og deres varianter og yderligere svage ord, der er specifikke for din organisation. Brug af Adgangskodebeskyttelse i Azure AD sikrer, at ændrede adgangskoder er stærke adgangskoder.

## <a name="apply-app-data-protection-policies"></a>Anvend politikker for databeskyttelse i APP

APP'er definerer, hvilke apps der er tilladt, og de handlinger, de kan foretage med din organisations data. De valgmuligheder, der er tilgængelige i APP, gør det muligt for organisationer at skræddersy beskyttelsen til deres specifikke behov. For nogle er det muligvis ikke tydeligt, hvilke politikindstillinger der kræves for at implementere et komplet scenarie. For at hjælpe organisationer med at prioritere hærdning af mobilklientslutpunkt har Microsoft introduceret taksonomi til sin struktur til beskyttelse af appdata til administration af iOS- og Android-mobilapps.

Strukturen for databeskyttelse i APP er organiseret i tre forskellige konfigurationsniveauer, hvor hvert niveau bygges fra det forrige niveau:

- **Niveau 1: Grundlæggende databeskyttelse i virksomheden** sikrer, at apps er beskyttet med en pinkode og krypteres og udfører selektive sletningshandlinger. For Android-enheder validerer dette niveau attestation af Android-enheder. Dette er en konfiguration på indgangsniveau, der giver lignende kontrol over databeskyttelse i Exchange Online postkassepolitikker og introducerer it-programmet og brugerpopulationen til APP.
- **Niveau 2: Forbedret databeskyttelse i virksomheden** introducerer mekanismer til forebyggelse af datalækage i apps og minimumkrav til operativsystemet. Dette er den konfiguration, der gælder for de fleste mobilbrugere, der tilgår arbejds- eller skoledata.
- **Niveau 3: Høj databeskyttelse i virksomheden** introducerer avancerede databeskyttelsesmekanismer, forbedret konfiguration af pinkode og APP Mobile Threat Defense. Denne konfiguration er ønskelig for brugere, der tilgår højrisikodata.

Hvis du vil se de specifikke anbefalinger for hvert konfigurationsniveau og de minimumapps, der skal beskyttes, skal du gennemse [Databeskyttelsesstrukturen ved hjælp af politikker for appbeskyttelse](/mem/intune/apps/app-protection-framework).

Ved hjælp af de principper, der er beskrevet i [Nul tillid konfigurationer af identitet og enhedsadgang](microsoft-365-policies-configurations.md), knyttes startpunktet og beskyttelsesniveauer for virksomheder tæt sammen med indstillingerne for udvidet databeskyttelse på niveau 2 i virksomheden. Det specialiserede sikkerhedsbeskyttelsesniveau er tæt forbundet med indstillingerne for høj databeskyttelse på niveau 3 for virksomheder.

|Beskyttelsesniveau|Beskyttelsespolitik for apps|Flere oplysninger|
|---|---|---|
|Udgangspunkt|[Niveau 2 forbedret databeskyttelse](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|De politikindstillinger, der gennemtvinges på niveau 2, omfatter alle de politikindstillinger, der anbefales for niveau 1, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.|
|Enterprise|[Niveau 2 forbedret databeskyttelse](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|De politikindstillinger, der gennemtvinges på niveau 2, omfatter alle de politikindstillinger, der anbefales for niveau 1, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.|
|Specialiseret sikkerhed|[Høj databeskyttelse på niveau 3 i virksomheder](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|De politikindstillinger, der gennemtvinges på niveau 3, omfatter alle de politikindstillinger, der anbefales for niveau 1 og 2, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 2.|

Hvis du vil oprette en ny beskyttelsespolitik for apps for hver platform (iOS og Android) i Microsoft Endpoint Manager ved hjælp af indstillingerne for databeskyttelsesstrukturen, kan du:

1. Opret politikkerne manuelt ved at følge trinnene i [Sådan opretter og installerer du politikker for appbeskyttelse med Microsoft Intune](/mem/intune/apps/app-protection-policies).
2. Importér [JSON-skabelonerne Intune App Protection Policy Configuration Framework](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) med [Intune PowerShell-scripts](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Kræv godkendte apps og appbeskyttelse

Hvis du vil gennemtvinge de Appbeskyttelse politikker, du anvendte i Intune, skal du oprette en politik for betinget adgang for at kræve godkendte klientapps og de betingelser, der er angivet i politikkerne for appbeskyttelse.

Gennemtvingelse af Appbeskyttelse politikker kræver et sæt politikker, der er beskrevet i [Kræv beskyttelsespolitik for apps til cloudapps med betinget adgang](/azure/active-directory/conditional-access/app-protection-based-conditional-access). Disse politikker er hver især inkluderet i dette anbefalede sæt politikker for konfiguration af identitet og adgang.

Hvis du vil oprette politikken Betinget adgang, der kræver godkendte apps og appbeskyttelse, skal du følge trinnene i [Kræv godkendte klientapps eller politik for appbeskyttelse på mobilenheder](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices), som kun tillader konti i mobilapps, der er beskyttet af Appbeskyttelse politikker, at få adgang til Microsoft 365 slutpunkter.

   > [!NOTE]
   > Denne politik sikrer, at mobilbrugere kan få adgang til alle Microsoft 365 slutpunkter ved hjælp af de relevante apps.

Denne politik blokerer også Exchange ActiveSync klienter på mobilenheder fra at oprette forbindelse til Exchange Online. Du kan dog oprette en separat politik til håndtering af Exchange ActiveSync på tværs af alle enheder. Du kan få flere oplysninger under [Bloker ActiveSync-klienter](secure-email-recommended-policies.md#block-activesync-clients), hvilket forhindrer, at Exchange ActiveSync klienter, der benytter basisgodkendelse, opretter forbindelse til Exchange Online. Denne politik er ikke afbildet i illustrationen øverst i denne artikel. Den er beskrevet og afbilledet i [Politikanbefalinger til sikring af mail](secure-email-recommended-policies.md).

 Denne politik udnytter tildelingskontrolelementerne [Kræv godkendt klientapp](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) og [Kræv beskyttelsespolitik for apps](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Endelig sikrer blokering af ældre godkendelse for andre klientapps på iOS- og Android-enheder, at disse klienter ikke kan omgå politikker for betinget adgang. Hvis du følger vejledningen i denne artikel, har du allerede konfigureret [Bloker klienter, der ikke understøtter moderne godkendelse](#block-clients-that-dont-support-multi-factor).

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

Politikker for enhedsoverholdelse definerer de krav, som enhederne skal opfylde for at blive bestemt som kompatible. Du kan oprette Intune politikker for enhedsoverholdelse fra Microsoft Endpoint Manager Administration.

Du skal oprette en politik for hver pc, telefon eller tabletplatform:

- Android-enhedsadministrator
- Android Enterprise
- iOS/iPadOS
- Macos
- Windows 8.1 og nyere
- Windows 10 og nyere

Hvis du vil oprette politikker for enhedsoverholdelse, skal du logge på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com) med dine administratorlegitimationsoplysninger og derefter **navigere til** Politikker for \> **enheders overholdelse af regler** \> og **standarder**. Vælg **Opret politik**.

Hvis politikker for enhedsoverholdelse skal installeres, skal de tildeles til brugergrupper. Du tildeler en politik, når du har oprettet og gemt den. Vælg politikken i Administration, og vælg derefter **Tildelinger**. Når du har valgt de grupper, du vil modtage politikken for, skal du vælge **Gem** for at gemme gruppetildelingen og installere politikken.

Du kan finde en trinvis vejledning i, hvordan du opretter politikker for overholdelse af angivne standarder i Intune, [under Opret en politik for overholdelse af angivne standarder i Microsoft Intune](/mem/intune/protect/create-compliance-policy) i dokumentationen til Intune.

### <a name="recommended-settings-for-ios"></a>Anbefalede indstillinger for iOS

iOS/iPadOS understøtter flere tilmeldingsscenarier, hvoraf to er dækket som en del af denne struktur:

- [Tilmelding af enheder til personligt ejede enheder](/mem/intune/enrollment/ios-enroll) – disse enheder ejes personligt og bruges til både arbejde og personlig brug.
- [Overvåget automatiseret tilmelding af enheder til virksomhedsejede enheder](/mem/intune/enrollment/device-enrollment-program-enroll-ios) – disse enheder er virksomhedsejede, knyttet til en enkelt bruger og bruges udelukkende til arbejde og ikke personlig brug.

IOS-/iPadOS-sikkerhedskonfigurationsstrukturen er organiseret i flere forskellige konfigurationsscenarier, hvilket giver vejledning til personligt ejede og overvågede enheder.

For personligt ejede enheder:

- Grundlæggende sikkerhed (niveau 1) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfiguration for personlige enheder, hvor brugerne får adgang til arbejds- eller skoledata. Dette gøres ved at gennemtvinge adgangskodepolitikker, enhedslåseegenskaber og deaktivere visse enhedsfunktioner (f.eks. certifikater, der ikke er tillid til).
- Forbedret sikkerhed (niveau 2) – Microsoft anbefaler denne konfiguration for enheder, hvor brugerne får adgang til følsomme eller fortrolige oplysninger. Denne konfiguration omfatter kontrolelementer til datadeling. Denne konfiguration gælder for de fleste mobilbrugere, der tilgår arbejds- eller skoledata på en enhed.
- Høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration for enheder, der bruges af bestemte brugere eller grupper, der er unikt høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret offentliggørelse medfører betydelige væsentlige tab for organisationen). Denne konfiguration medfører stærkere adgangskodepolitikker, deaktiverer visse enhedsfunktioner og gennemtvinger yderligere begrænsninger for dataoverførsel.

For overvågede enheder:

- Grundlæggende sikkerhed (niveau 1) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfiguration for overvågede enheder, hvor brugerne får adgang til arbejds- eller skoledata. Dette gøres ved at gennemtvinge adgangskodepolitikker, enhedslåseegenskaber og deaktivere visse enhedsfunktioner (f.eks. certifikater, der ikke er tillid til).
- Forbedret sikkerhed (niveau 2) – Microsoft anbefaler denne konfiguration for enheder, hvor brugerne får adgang til følsomme eller fortrolige oplysninger. Denne konfiguration styrer datadeling og blokerer adgangen til USB-enheder. Denne konfiguration gælder for de fleste mobilbrugere, der tilgår arbejds- eller skoledata på en enhed.
- Høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration for enheder, der bruges af bestemte brugere eller grupper, der er unikt høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret offentliggørelse medfører betydelige væsentlige tab for organisationen). Denne konfiguration sender stærkere adgangskodepolitikker, deaktiverer visse enhedsfunktioner, gennemtvinger yderligere begrænsninger for dataoverførsel og kræver, at apps installeres via Apples volumenkøbsprogram.

Ved hjælp af de principper, der er beskrevet i [Nul tillid konfigurationer af identitet og enhedsadgang](microsoft-365-policies-configurations.md), knyttes niveauerne Startpunkt og Enterprise-beskyttelse tæt sammen med de udvidede sikkerhedsindstillinger på niveau 2. Det specialiserede sikkerhedsbeskyttelsesniveau er tæt knyttet til indstillingerne for høj sikkerhed på niveau 3.

|Beskyttelsesniveau  |Enhedspolitik |Flere oplysninger  |
|---------|---------|---------|
|Udgangspunkt     |Forbedret sikkerhed (niveau 2)         |De politikindstillinger, der gennemtvinges på niveau 2, omfatter alle de politikindstillinger, der anbefales for niveau 1, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Enterprise     |Forbedret sikkerhed (niveau 2)         |De politikindstillinger, der gennemtvinges på niveau 2, omfatter alle de politikindstillinger, der anbefales for niveau 1, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Specialiseret sikkerhed     |Høj sikkerhed (niveau 3)         |De politikindstillinger, der gennemtvinges på niveau 3, omfatter alle de politikindstillinger, der anbefales for niveau 1 og 2, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 2.         |

Hvis du vil se de specifikke anbefalinger til enhedsoverholdelse og enhedsbegrænsning for hvert konfigurationsniveau, skal du gennemse [iOS/iPadOS Security Configuration Framework](/mem/intune/enrollment/ios-ipados-configuration-framework).

### <a name="recommended-settings-for-android"></a>Anbefalede indstillinger for Android

Android Enterprise understøtter flere tilmeldingsscenarier, hvoraf to er dækket som en del af denne struktur:

- [Android Enterprise-arbejdsprofil](/intune/android-work-profile-enroll) – denne tilmeldingsmodel bruges typisk til personligt ejede enheder, hvor it-virksomheden ønsker at give en klar adskillelsesgrænse mellem arbejde og personlige data. Politikker, der styres af it-tjenesten, sikrer, at arbejdsdataene ikke kan overføres til den personlige profil.
- [Fuldt administrerede Android Enterprise-enheder](/intune/android-fully-managed-enroll) – disse enheder er virksomhedsejede, knyttet til en enkelt bruger og bruges udelukkende til arbejde og ikke personlig brug.

Android Enterprise Security Configuration Framework er organiseret i flere forskellige konfigurationsscenarier, der giver vejledning til arbejdsprofil og fuldt administrerede scenarier.

Til Android Enterprise-arbejdsprofilenheder:

- Udvidet sikkerhed for arbejdsprofil (niveau 2) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfiguration for personlige enheder, hvor brugerne får adgang til arbejds- eller skoledata. Denne konfiguration introducerer adgangskodekrav, adskiller arbejds- og personlige data og validerer attestation af Android-enheder.
- Høj sikkerhed for arbejdsprofil (niveau 3) – Microsoft anbefaler denne konfiguration for enheder, der bruges af bestemte brugere eller grupper, der er unikt høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret offentliggørelse medfører betydelige materielle tab for organisationen). Denne konfiguration introducerer forsvar af mobiltrussel eller Microsoft Defender for Endpoint, angiver den mindste Android-version, vedtager stærkere adgangskodepolitikker og begrænser arbejds- og personlig adskillelse yderligere.

Til fuldt administrerede Android Enterprise-enheder:

- Fuldt administreret grundlæggende sikkerhed (niveau 1) – Microsoft anbefaler denne konfiguration som minimumsikkerhedskonfiguration for en virksomhedsenhed. Denne konfiguration gælder for de fleste mobilbrugere, der tilgår arbejds- eller skoledata. Denne konfiguration introducerer adgangskodekrav, angiver den mindste Android-version og indfører visse enhedsbegrænsninger.
- Fuldt administreret udvidet sikkerhed (niveau 2) – Microsoft anbefaler denne konfiguration for enheder, hvor brugerne får adgang til følsomme eller fortrolige oplysninger. Denne konfiguration gennemtvinger stærkere adgangskodepolitikker og deaktiverer bruger-/kontofunktioner.
- Fuldt administreret høj sikkerhed (niveau 3) – Microsoft anbefaler denne konfiguration for enheder, der bruges af bestemte brugere eller grupper, der er unikt høj risiko (brugere, der håndterer meget følsomme data, hvor uautoriseret offentliggørelse medfører betydelige materielle tab for organisationen). Denne konfiguration øger minimumversionen af Android, introducerer forsvar af mobiltrusler eller Microsoft Defender for Endpoint og gennemtvinger yderligere enhedsbegrænsninger.

Ved hjælp af de principper, der er beskrevet i [Nul tillid konfigurationer af identitet og enhedsadgang](microsoft-365-policies-configurations.md), knyttes niveauerne Startpunkt og Enterprise-beskyttelsesniveau tæt sammen med den grundlæggende sikkerhed på niveau 1 for personligt ejede enheder og niveau 2 udvidede sikkerhedsindstillinger for fuldt administrerede enheder. Det specialiserede sikkerhedsbeskyttelsesniveau er tæt knyttet til indstillingerne for høj sikkerhed på niveau 3.

Til Android Enterprise-arbejdsprofilenheder:

|Beskyttelsesniveau  |Enhedspolitik |Flere oplysninger  |
|---------|---------|---------|
|Udgangspunkt     |Arbejdsprofil: Grundlæggende sikkerhed (niveau 1)      |NIELSEN         |
|Enterprise     |Arbejdsprofil: Grundlæggende sikkerhed (niveau 1)         |NIELSEN         |
|Udgangspunkt     |Fuldt administreret: Udvidet sikkerhed (niveau 2)       |De politikindstillinger, der gennemtvinges på niveau 2, omfatter alle de politikindstillinger, der anbefales for niveau 1, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Enterprise     |Fuldt administreret: Udvidet sikkerhed (niveau 2)         |De politikindstillinger, der gennemtvinges på niveau 2, omfatter alle de politikindstillinger, der anbefales for niveau 1, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 1.         |
|Specialiseret sikkerhed     |Høj sikkerhed (niveau 3)         |De politikindstillinger, der gennemtvinges på niveau 3, omfatter alle de politikindstillinger, der anbefales for niveau 1 og 2, og føjer kun til eller opdaterer nedenstående politikindstillinger for at implementere flere kontrolelementer og en mere avanceret konfiguration end niveau 2.         |

Hvis du vil se de specifikke anbefalinger til enhedsoverholdelse og enhedsbegrænsning for hvert konfigurationsniveau, skal du gennemse [Android Enterprise Security Configuration Framework](/mem/intune/enrollment/android-configuration-framework).

### <a name="recommended-settings-for-windows-10-and-later"></a>Anbefalede indstillinger for Windows 10 og nyere

Følgende indstillinger anbefales til pc'er, der kører Windows 10 og nyere, som konfigureret i **trin 2: Indstillinger for overholdelse af angivne standarder** for processen til oprettelse af politikker.

Du **kan se regler for evaluering af enhedstilstand > Windows tilstands attestationstjeneste** i denne tabel.

|Egenskaber|Værdi|Handling|
|---|---|---|
|Kræv BitLocker|Kræver|Vælg|
|Kræv, at Sikker start er aktiveret på enheden|Kræver|Vælg|
|Kræv kodeintegritet|Kræver|Vælg|

I forbindelse **med enhedsegenskaber** skal du angive de relevante værdier for operativsystemversioner baseret på it- og sikkerhedspolitikker.

Vælg **Kræv** **for Configuration Manager overholdelse**.

Se denne tabel for **systemsikkerhed**.

|Type|Egenskaber|Værdi|Handling|
|---|---|---|---|
|Adgangskode|Kræv en adgangskode for at låse mobilenheder op|Kræver|Vælg|
||Enkle adgangskoder|Bloker|Vælg|
||Adgangskodetype|Enhedsstandard|Vælg|
||Minimumlængde for adgangskode|6|Type|
||Maksimalt antal minutter med inaktivitet, før der kræves adgangskode|15|Type <p> Denne indstilling understøttes for Android version 4.0 og nyere eller KNOX 4.0 og nyere. For iOS-enheder understøttes den til iOS 8.0 og nyere.|
||Udløb af adgangskode (dage)|41|Type|
||Antal tidligere adgangskoder for at forhindre genbrug|5|Type|
||Kræv adgangskode, når enheden vender tilbage fra inaktiv tilstand (mobil og Holographic)|Kræver|Tilgængelig til Windows 10 og nyere|
|Kryptering|Kryptering af datalager på enhed|Kræver|Vælg|
|Enhedssikkerhed|Firewall|Kræver|Vælg|
||Antivirus|Kræver|Vælg|
||Antispyware|Kræver|Vælg <p> Denne indstilling kræver en antispywareløsning, der er registreret i Windows Sikkerhed-appen.|
|Defender for Cloud|Microsoft Defender Antimalware|Kræver|Vælg|
||Minimumversion af Microsoft Defender Antimalware||Type <p> Understøttes kun for Windows 10 desktopcomputer. Microsoft anbefaler versioner, der ikke er mere end fem bagud fra den nyeste version.|
||Microsoft Defender Antimalware-signatur opdateret|Kræver|Vælg|
||Beskyttelse i realtid|Kræver|Vælg <p> Understøttes kun for Windows 10 og nyere skrivebord|

#### <a name="microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint

|Type|Egenskaber|Værdi|Handling|
|---|---|---|---|
|Microsoft Defender for Endpoint regler i Microsoft Endpoint Manager Administration|[Kræv, at enheden er på eller under maskinens risikoscore](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Medium|Vælg|

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

Sådan kræver du overholdelse af angivne standarder for alle enheder:

1. Gå til [Azure Portal](https://portal.azure.com), og log på med dine legitimationsoplysninger.
2. Vælg **Azure Active Directory** på listen over Azure-tjenester.
3. Vælg **Sikkerhed** på listen **Administrer**, og vælg derefter **Betinget adgang**.
4. Vælg **Ny politik** , og skriv navnet på den nye politik.

5. Under **Tildelinger** skal du vælge **Brugere og grupper** og inkludere, hvem politikken skal gælde for. Udeluk også din gruppe af undtagelser for betinget adgang.

6. Under **Tildelinger** skal du vælge **Cloudapps eller -handlinger**.

7. Under **Medtag** skal du vælge **Vælg apps > Vælg** og derefter vælge de ønskede apps på listen **Cloudapps** . Vælg f.eks. Office 365. Vælg **Vælg** , når du er færdig.

8. Under **Adgangskontrolelementer** skal du vælge **Tildel** .

9. Vælg **Tildel adgang,** og **markér derefter Kræv, at enheden er markeret som kompatibel**. For flere kontrolelementer skal du vælge **Kræv alle de markerede kontrolelementer**. Når du er færdig, skal du vælge **Vælg**.

10. Vælg **Til** for **Aktivér politik**, og vælg derefter **Opret**.

> [!NOTE]
> Sørg for, at enheden er kompatibel, før du aktiverer denne politik. Ellers kan du blive låst ude og kan ikke ændre denne politik, før din brugerkonto er føjet til udeladelsesgruppen Betinget adgang.

## <a name="next-step"></a>Næste trin

[![Trin 3: Politikker for gæstebrugere og eksterne brugere.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](identity-access-policies-guest-access.md)

[Få mere at vide om politikanbefalinger for gæstebrugere og eksterne brugere](identity-access-policies-guest-access.md)
