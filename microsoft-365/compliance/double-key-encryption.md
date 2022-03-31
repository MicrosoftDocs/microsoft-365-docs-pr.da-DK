---
title: Kryptering af dobbelt nøgle (DKE)
description: DKE giver dig mulighed for at beskytte meget følsomme data og samtidig bevare fuld kontrol over din nøgle.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: b16733a1d42ca245f096038f567be6fbd0c3fb2a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63601528"
---
# <a name="double-key-encryption-for-microsoft-365"></a>Kryptering med dobbelt nøgle til Microsoft 365

> *Gælder for: Kryptering med dobbelt nøgle til Microsoft 365, [Microsoft 365 overholdelse af regler og](https://www.microsoft.com/microsoft-365/business/compliance-management) standarder og [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Vejledning til: [Samlet Azure Information Protection-etiketklient til Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


> *Tjenestebeskrivelse for: [Microsoft 365 overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Dobbelt nøglekryptering (DKE) bruger to nøgler sammen for at få adgang til beskyttet indhold. Microsoft gemmer én nøgle i Microsoft Azure, og du holder den anden nøgle. Du har fuld kontrol over en af dine nøgler ved hjælp af krypteringstjenesten Dobbelt nøgle. Du anvender beskyttelse ved hjælp af Den samlede Azure Information Protection-etiketklient på dit meget følsomme indhold.

Double Key-kryptering understøtter både sky- og lokale installationer. Disse installationer hjælper med at sikre, at krypterede data forbliver uigennemsigtige, uanset hvor du gemmer de beskyttede data.

Du kan finde flere oplysninger om de skybaserede standardlejerrodsnøgler i [Planlægning og implementering af din Azure Information Protection-lejernøgle](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Når din organisation skal indføre DKE

Kryptering med dobbelt nøgle er beregnet til dine mest følsomme data, der er underlagt de strengeste beskyttelseskrav. DKE er ikke beregnet til alle data. Generelt skal du bruge dobbelt nøglekryptering til kun at beskytte en lille del af dine samlede data. Du skal være omhyggelig med at identificere de rigtige data, der skal dækkes med denne løsning, inden du installerer. I nogle tilfælde kan det være nødvendigt at indskrænke omfanget og bruge andre løsninger til de fleste af dine data, f.eks. Microsoft Information Protection med Microsoft-administrerede nøgler eller BYOK. Disse løsninger er tilstrækkelige til dokumenter, der ikke er underlagt udvidede beskyttelseskrav og lovmæssige krav. Disse løsninger giver dig også mulighed for at bruge de mest effektive Office 365 tjenester, som du ikke kan bruge med DKE-krypteret indhold. Eksempel:

- Transportregler, herunder antimalware og spam, der kræver synlighed i den vedhæftede fil
- Microsoft Delve
- eDiscovery
- Indholdssøgning og -indeksering
- Office webapps, herunder funktioner til samtidig redigering

Eventuelle eksterne programmer eller tjenester, der ikke er integreret med DKE via Microsoft Information Protection (MIP) SDK, kan ikke udføre handlinger på de krypterede data.

1.7+ Microsoft Information Protection SDK 1.7+ understøtter dobbelt nøglekryptering. Programmer, der integreres med vores SDK, kan have en grund til at bruge disse data med tilstrækkelige tilladelser og integrationer.

Brug Microsofts funktioner til beskyttelse af oplysninger (klassificering og mærkning) til at beskytte de fleste af dine følsomme data, og brug kun DKE til dine missionskritiske data. Dobbelt nøglekryptering er relevant for følsomme data i meget regulerede brancher som finansielle tjenester og sundhedssektoren.

Hvis din organisation har et af følgende krav, kan du bruge DKE til at sikre dit indhold:

- Du vil sikre, at *kun du nogensinde* kan dekryptere beskyttet indhold under alle omstændigheder.
- Du ønsker ikke, at Microsoft selv skal have adgang til beskyttede data.
- Du har lovmæssige krav til at opbevare nøgler inden for en geografisk grænse. Alle de nøgler, du opbevarer til kryptering og dekryptering af data, bevares i dit datacenter.

## <a name="system-and-licensing-requirements-for-dke"></a>System- og licenskrav til DKE

**Kryptering med dobbelt nøgle til Microsoft 365** leveres med Microsoft 365 E5. Hvis du ikke har en Microsoft 365 E5, kan du tilmelde dig en [prøveversion](https://aka.ms/M365E5ComplianceTrial). Du kan finde flere oplysninger om disse licenser [Microsoft 365 vejledning i licenser til & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection**. DKE fungerer sammen med følsomhedsmærkater og kræver Azure Information Protection.

DKE-følsomhedsmærkater gøres tilgængelige for slutbrugere via følsomhedsknappen i AIP Unified Labeling-klienten Office skrivebordsapps. Installér disse forudsætninger på hver klientcomputer, hvor du vil beskytte og bruge beskyttede dokumenter.

**Microsoft Office apps til** store virksomheder version 2009 eller nyere (desktopversioner af Word, PowerPoint og Excel) på Windows.

**Azure Information Protection Unified Labeling Client version** 2.7.93.0 eller nyere. Download og installer Unified Labeling-klienten fra [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Understøttede miljøer til lagring og visning af DKE-beskyttet indhold

**Understøttede programmer**. [Microsoft 365 Apps for enterprise](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) kunder på Windows, herunder Word, Excel og PowerPoint.

**Understøttelse af onlineindhold**. Du kan gemme dokumenter og filer, der er beskyttet med dobbelt nøglekryptering online, i både Microsoft SharePoint og OneDrive for Business. Du skal navnmærke og beskytte dokumenter og filer med DKE af understøttede programmer, før du uploader til disse placeringer. Du kan dele krypteret indhold via mail, men du kan ikke få vist krypterede dokumenter og filer online. I stedet skal du få vist beskyttet indhold ved hjælp af de understøttede skrivebordsprogrammer og klienter på din lokale computer.

## <a name="overview-of-deploying-dke"></a>Oversigt over implementering af DKE

Du skal følge disse generelle trin for at konfigurere DKE. Når du har udført disse trin, kan dine slutbrugere beskytte dine meget følsomme data med dobbelt nøglekryptering.

1. Installer DKE-tjenesten som beskrevet i denne artikel.

2. Opret et navn med kryptering af dobbelt nøgle. I Microsoft 365 Overholdelsescenter skal du gå til **Beskyttelse af oplysninger** og oprette en ny etiket med dobbelt nøglekryptering. Se [Begræns adgang til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](./encryption-sensitivity-labels.md).

3. Brug dobbelte nøglekrypteringsnavne. Beskyt data ved at vælge navnet Dobbelt-krypteret nøgle på båndet Følsomhed Microsoft Office.

Du kan udføre nogle af trinnene for at installere Dobbelt nøglekryptering på flere måder. Denne artikel indeholder detaljerede instruktioner, så mindre erfarne administratorer kan installere tjenesten. Hvis du er tryg ved at gøre dette, kan du vælge at bruge dine egne metoder.

## <a name="deploy-dke"></a>Udrul DKE

I denne artikel og installationsvideoen bruges Azure som installationsdestination for DKE-tjenesten. Hvis du installerer på en anden placering, skal du angive dine egne værdier.

Se [installationsvideoen med dobbeltnøglekryptering](https://youtu.be/vDWfHN_kygg) for at få vist en trinvis oversigt over begreberne i denne artikel. Det tager ca. 18 minutter at gennemføre videoen.

Du skal følge disse generelle trin for at konfigurere kryptering med dobbelt nøgle for organisationen.

1. [Installer softwareforud forudsætninger for DKE-tjenesten](#install-software-prerequisites-for-the-dke-service)
1. [Klon lageret med dobbeltnøglekryptering GitHub nøglelager](#clone-the-dke-github-repository)
1. [Rediger programindstillinger](#modify-application-settings)
1. [Generer testnøgler](#generate-test-keys)
1. [Byg projektet](#build-the-project)
1. [Installer DKE-tjenesten, og udgiv nøglelageret](#deploy-the-dke-service-and-publish-the-key-store)
1. [Valider din udrulning](#validate-your-deployment)
1. [Registrer dit nøglelager](#register-your-key-store)
1. [Opret følsomhedsmærkater ved hjælp af DKE](#create-sensitivity-labels-using-dke)
1. [Aktivér DKE i din klient](#enable-dke-in-your-client)
1. [Overfør beskyttede filer fra HYOK-etiketter til DKE-etiketter](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Når du er færdig, kan du kryptere dokumenter og filer ved hjælp af DKE. Du kan få mere at [vide under Anvend følsomhedsmærkater på dine filer og mails Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>Installer softwareforud forudsætninger for DKE-tjenesten

Installer disse forudsætninger på den computer, hvor du vil installere DKE-tjenesten.

**.NET Core 3.1 SDK**. Download og installér SDK fra [Download .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio kode**. Download Visual Studio kode fra [https://code.visualstudio.com/](https://code.visualstudio.com). Når du har installeret, skal du Visual Studio kode og vælge **Vis** \> **udvidelser**. Installér disse udvidelser.

- C# for Visual Studio kode

- NuGet Pakkestyring

**Git-ressourcer**. Download og installér et af følgende.

- [Git](https://git-scm.com/downloads)

- [GitHub skrivebord](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**OpenSSL** Du skal have [OpenSSL installeret](https://slproweb.com/products/Win32OpenSSL.html) for at [generere testnøgler,](#generate-test-keys) når du har installeret DKE. Sørg for, at du bruger den korrekt fra stien til dine miljøvariabler. Se f.eks. "Føj installationsmappen til PATH" for at [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) få flere oplysninger.

### <a name="clone-the-dke-github-repository"></a>Klon DKE-GitHub lager

Microsoft leverer DKE-kildefilerne i GitHub lager. Du kloner lageret for at bygge projektet lokalt til din organisations brug. DKE-GitHub lager er placeret på [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

Følgende instruktioner er beregnet til uerfarne git- eller Visual Studio Code-brugere:

1. I din browser skal du gå til: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. Vælg Kode i højre side af **skærmen**. Din version af brugergrænsefladen viser muligvis knappen **Klon eller** download. Derefter skal du i rullelisten, der vises, vælge kopieringsikonet for at kopiere URL-adressen til din udklipsholder.

    Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Klon dobbeltnøglekrypteringstjenestens lager fra GitHub.](../media/dke-clone.png)

3. I Visual Studio skal du vælge **Vis kommandopalet** \> **og** vælge **Git: Clone**. For at gå til indstillingen på listen skal du `git: clone` begynde at skrive for at filtrere posterne og derefter vælge dem på rullelisten. Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Visual Studio indstillingen Kode GIT:Clone.](../media/dke-vscode-clone.png)

4. I tekstfeltet skal du indsætte den URL-adresse, du kopierede fra Git, og **vælge Klon GitHub**.

5. I dialogboksen **Vælg mappe** , der vises, skal du gå til og vælge en placering, hvor lageret skal lagres. Når du bliver bedt om det, skal du **vælge Åbn**.

    Lageret åbnes i Visual Studio kode og viser den aktuelle Git-gren nederst til venstre. For eksempel bør grenen være **hoved.** Eksempel:

   ![Skærmbillede af DKE-repo i Visual Studio, der viser hovedgrenen.](../media/dke-vscode-main-branch.jpg)

6. Hvis du ikke er på hovedgrenen, skal du vælge den. I Visual Studio kode skal du vælge grenen og vælge hoved **på listen** over forgreninger, der vises.

   > [!IMPORTANT]
   > Når du vælger hovedgrenen, sikrer du, at du har de korrekte filer til at opbygge projektet. Hvis du ikke vælger den korrekte forgrening, vil din installation mislykkes.

Du har nu konfigureret dit DKE-kildelager lokalt. Dernæst skal [du ændre programindstillinger](#modify-application-settings) for din organisation.

### <a name="modify-application-settings"></a>Rediger programindstillinger

For at installere DKE-tjenesten skal du ændre følgende typer programindstillinger:

- [Indstillinger for nøgleadgang](#key-access-settings)
- [Lejer- og nøgleindstillinger](#tenant-and-key-settings)

Du redigerer programindstillingerne i filen appsettings.json. Denne fil er placeret i DoubleKeyEncryptionService repo, du klonede lokalt under DoubleKeyEncryptionService\src\customer-key-store. Eksempelvis kan du Visual Studio i kodefilen, som vist på følgende billede.

![Finde filen appsettings.json for DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Indstillinger for nøgleadgang

Vælg, om du vil bruge mail eller rollegodkendelse. DKE understøtter kun én af disse godkendelsesmetoder ad gangen.

- **Mailgodkendelse**. Tillader din organisation at godkende adgang til nøgler udelukkende baseret på mailadresser.

- **Rollegodkendelse**. Giver din organisation mulighed for at godkende adgang til nøgler baseret på Active Directory-grupper og kræver, at webtjenesten kan oprette en forespørgsel til LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>Sådan angives vigtige adgangsindstillinger for DKE ved hjælp af mailgodkendelse

1. Åbn filen **appsettings.json** , og find indstillingen `AuthorizedEmailAddress` .

2. Tilføj den eller de mailadresser, som du vil autorisere. Adskile flere mailadresser med dobbelte anførselstegn og kommaer. Eksempel:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Find indstillingen `LDAPPath` , og fjern teksten mellem `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` de dobbelte anførselstegn. Lad de dobbelte anførselstegn være på plads. Når du er færdig, bør indstillingen se sådan ud.

   ```json
   "LDAPPath": ""
   ```

4. Find indstillingen `AuthorizedRoles` , og slet hele linjen.

Dette billede viser filen **appsettings.json korrekt** formateret til mailgodkendelse.

   ![Filen appsettings.json, der viser mailgodkendelsesmetoden.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Sådan angives vigtige adgangsindstillinger for DKE ved hjælp af rollegodkendelse

1. Åbn filen **appsettings.json** , og find indstillingen `AuthorizedRoles` .

2. Tilføj de Active Directory-gruppenavne, du vil autorisere. Adskile flere gruppenavne med dobbelte anførselstegn og kommaer. Eksempel:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Find indstillingen `LDAPPath` , og tilføj Active Directory-domænet. Eksempel:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Find indstillingen `AuthorizedEmailAddress` , og slet hele linjen.

Dette billede viser filen **appsettings.json korrekt** formateret til rollegodkendelse.

   ![appsettings.json-fil, der viser rollegodkendelsesmetoden.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Lejer- og nøgleindstillinger

DKE lejer- og nøgleindstillinger findes i **filen appsettings.json** .

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>Sådan konfigureres lejer- og nøgleindstillinger for DKE

1. Åbn **filen appsettings.json** .

2. Find indstillingen `ValidIssuers` , og erstat med `<tenantid>` dit lejer-id. Du kan finde dit lejer-id ved at gå til Azure-portalen og få vist [lejeregenskaberne](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Eksempel:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Hvis du vil aktivere ekstern B2B-adgang til din nøglebutik, skal du også medtage disse eksterne lejere som en del af den gyldige udsteders liste.

Find .`JwtAudience` Erstat `<yourhostname>` med værtsnavnet på den computer, hvor DKE-tjenesten kører. Eksempel:

  > [!IMPORTANT]
  > Værdien for skal `JwtAudience` svare nøjagtigt til navnet på din *vært*. Du kan bruge **localhost:5001,** mens du foretager fejlfinding. Men når du er færdig med fejlfinding, skal du sørge for at opdatere denne værdi til serverens værtsnavn.

- `TestKeys:Name`. Angiv et navn til din nøgle. For eksempel: `TestKey1`
- `TestKeys:Id`. Opret et GUID, og angiv det som `TestKeys:ID` værdien. F.eks. `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Du kan bruge et websted som [f.eks. Online GUID Generator](https://guidgenerator.com/) til tilfældigt at generere et GUID.

Dette billede viser det korrekte format for indstillingerne for lejer og nøgler **i appsettings.json**. `LDAPPath` er konfigureret til rollegodkendelse.

![Viser korrekte indstillinger for lejer og nøgle for DKE i filen appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Generer testnøgler

Når du har defineret dine programindstillinger, er du klar til at generere offentlige og private testnøgler.

Sådan genererer du nøgler:

1. Fra Windows menuen Start du køre OpenSSL-kommandoprompten.

1. Skift til den mappe, hvor du vil gemme testtasterne. De filer, du opretter ved at udføre trinnene i denne opgave, gemmes i den samme mappe.

1. Generér den nye testnøgle.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. Generer den private nøgle.

   Hvis du har installeret OpenSSL version 3 eller nyere, skal du køre følgende kommando:
  
  ```console
  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM -traditional
  ```
  
>  Ellers skal du køre følgende kommando:
>  ```console
>  openssl rsa -in key.pem -out privkeynopass.pem -outform PEM
>  ```

1. Opret den offentlige nøgle.

   ```console
   openssl rsa -in key.pem -pubout > pubkeyonly.pem
   ```

1. I en teksteditor skal du **åbne pubkeyonly.pem**. Kopiér alt indholdet i **filen pubkeyonly.pem** , undtagen den første og sidste linje, `PublicPem` i den del af **filen appsettings.json** .

1. I en teksteditor skal du **åbne privkeynopass.pem**. Kopiér alt indholdet i **filen privkeynopass.pem** , undtagen den første og sidste linje, `PrivatePem` til den del af **filen appsettings.json** .

1. Fjern alle tomme mellemrum og nye streger i både `PublicPem` sektionerne `PrivatePem` og.

    > [!IMPORTANT]
    > Når du kopierer dette indhold, skal du ikke slette nogen af PEM-dataene.

1. I Visual Studio skal du gå til **filen Startup.cs**. Denne fil er placeret i DoubleKeyEncryptionService repo, du klonede lokalt under DoubleKeyEncryptionService\src\customer-key-store\.

1. Find følgende linjer:

    ```csharp
        #if USE_TEST_KEYS
        #error !!!!!!!!!!!!!!!!!!!!!! Use of test keys is only supported for testing,
        DO NOT USE FOR PRODUCTION !!!!!!!!!!!!!!!!!!!!!!!!!!!!!
        services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
        #endif
    ```

1. Erstat disse linjer med følgende tekst:

    ```csharp
    services.AddSingleton<ippw.IKeyStore, ippw.TestKeyStore>();
    ```

    Slutresultaterne bør ligne følgende.

    ![startup.cs-fil for offentlig forhåndsvisning.](../media/dke-startupcs-usetestkeys.png)

Nu er du klar til at [bygge dit DKE-projekt](#build-the-project).

### <a name="build-the-project"></a>Byg projektet

Brug følgende vejledning til at bygge DKE-projektet lokalt:

1. I Visual Studio i DKE-tjenestelageret skal du vælge **Vis** \> kommandopalet og derefter skrive **build** ved prompten.

2. Vælg Opgaver: Kør **buildopgave på listen**.

   Hvis der ikke findes nogen buildopgaver, skal du **vælge Konfigurer buildopgave** og oprette en til .NET core på følgende måde.

   ![Konfigurer manglende buildopgave for .NET.](../media/dke-configurebuildtask.png)

   1. Vælg **Opret tasks.json fra skabelon**.

      ![Opret tasks.json-fil fra skabelon til DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. Vælg **.NET Core på listen over skabelontyper**.

      ![Vælg den korrekte skabelon til DKE.](../media/dke-tasksjsontemplate.png)

   3. I buildsektionen skal du finde stien til **filen customerkeystore.csproj** . Hvis den ikke er der, skal du tilføje følgende linje:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Kør buildet igen.

3. Kontrollér, at der ikke er nogen røde fejl i outputvinduet.

   Hvis der er røde fejl, skal du kontrollere konsoloutputtet. Sørg for, at du har gennemført alle de forrige trin korrekt, og at de korrekte buildversioner er til stede.

4. Vælg **Kør** \> **Start fejlfinding for** at fejlfinde processen. Hvis du bliver bedt om at vælge et miljø, skal du vælge **.NET core**.

   Fejlfindingen af .NET Core starter typisk i `https://localhost:5001`. For at få vist din testnøgle skal `https://localhost:5001` du gå til og tilføje en skråstreg (/) og navnet på din nøgle. Eksempel:

   ```https
   https://localhost:5001/TestKey1
   ```

   Nøglen skal vises i JSON-format.

Konfigurationen er nu fuldført. Før du publicerer nøglestore, skal du i appsettings.json for JwtAudience-indstillingen sikre dig, at værdien for værtsnavn svarer nøjagtigt til navnet på din App-tjenestevært. Du har måske ændret det til den lokale vært for at foretage fejlfinding af buildet.

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>Installer DKE-tjenesten, og udgiv nøglelageret

I forbindelse med produktionsinstallationer skal du installere tjenesten enten i en tredjepartssky eller [publicere på et lokalt system](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

Du foretrækker måske andre metoder til at udrulle dine nøgler. Vælg den metode, der fungerer bedst for din organisation.

For pilotinstallationer kan du installere i Azure og komme i gang med det samme.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>Sådan opretter du en Azure Web App-forekomst, der skal hoste din DKE-installation

For at publicere nøglelageret skal du oprette en Azure App Service-forekomst som vært for din DKE-installation. Derefter skal du publicere dine genererede nøgler til Azure.

1. I din browser skal du logge på [Microsoft Azure portalen](https://ms.portal.azure.com) og gå til **App** **ServicesAdd** > .

2. Vælg dit abonnement og din ressourcegruppe, og definer dine oplysninger om forekomsten.

   - Angiv værtsnavnet på den computer, hvor du vil installere DKE-tjenesten. Sørg for, at det er det samme navn som det navn, der er defineret for indstillingen JwtAudience i [**filen appsettings.json**](#tenant-and-key-settings) . Den værdi, du angiver for navnet, er også WebAppInstanceName.

   - **Udgiv** skal du **vælge kode**, og for **Runtime-stak** skal du **vælge .NET Core 3.1**.

   Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Tilføj din apptjeneste.](../media/dke-azure-add-app-service.png)

3. Nederst på siden skal du vælge Gennemse **+ opret** og derefter vælge **Tilføj**.

4. Gør et af følgende for at publicere dine genererede nøgler:

   - [Publicer via ZipDeployUI](#publish-via-zipdeployui)
   - [Udgiv via FTP](#publish-via-ftp)
   - [Publicere via Visual Studio 2019 eller nyere](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>Publicer via ZipDeployUI

1. Gå til `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

   For eksempel: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

2. I codebase for nøglelageret skal du gå til mappen **customer-key-store\src\customer-key-store** og kontrollere, at denne mappe indeholder filen **customerkeystore.csproj** .

3. Kør: **dotnet publicer**

   I outputvinduet vises den mappe, hvor publicering blev installeret.

   For eksempel: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Send alle filer i mappen Udgiv til en .zip fil. Når du opretter .zip fil, skal du sørge for, at alle filer i mappen er på rodniveau i .zip fil.

5. Træk og slip den .zip, du opretter, til det ZipDeployUI-websted, du åbnede ovenfor. For eksempel: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

DKE installeres, og du kan søge efter de testnøgler, du har oprettet. Fortsæt med [Valider din installation](#validate-your-deployment) nedenfor.

#### <a name="publish-via-ftp"></a>Udgiv via FTP

1. Forbind til den apptjeneste, du oprettede [ovenfor](#deploy-the-dke-service-and-publish-the-key-store).

   I din browser skal du gå til: **Azure portalApp** >  **ServiceDeployment** >  **CenterManual** >  **DeploymentFTPDashboard** >  > .

2. Kopiér de forbindelsesstrenge, der vises, til en lokal fil. Du skal bruge disse strenge til at oprette forbindelse til webapptjenesten og uploade filer via FTP.

   Eksempel:

   ![Kopiér forbindelsesstrenge fra FTP-dashboardet.](../media/dke-ftp-dashboard.png)

3. I codebase for nøglelageret skal du gå til mappen **customer-key-store\src\customer-key-store**.

4. Kontrollér, at denne mappe indeholder **filen customerkeystore.csproj** .

5. Kør: **dotnet publicer**

   Outputtet indeholder den mappe, hvor publicering blev installeret.

   For eksempel: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Send alle filer i mappen Udgiv til en zip-fil. Når du opretter .zip fil, skal du sørge for, at alle filer i mappen er på rodniveau i .zip fil.

7. Fra din FTP-klient skal du bruge de forbindelsesoplysninger, du kopierede, til at oprette forbindelse til din apptjeneste. Upload den .zip fil, du oprettede i forrige trin, til rodmappen i din Web App.

DKE installeres, og du kan søge efter de testnøgler, du har oprettet. Dernæst skal du [validere din installation](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Valider din udrulning

Når du har implementeret DKE ved hjælp af en af de metoder, der er beskrevet ovenfor, skal du validere udrulningen og indstillingerne for nøglelager.

Kør:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Eksempel:

```powershell
key_store_tester.ps1 https://mydkeservice.com/mykey
```

Sørg for, at der ikke vises nogen fejl i outputtet. Når du er klar, skal [du registrere dit nøglelager](#register-your-key-store).

Der er store og små bogstaver i nøglenavnet. Angiv nøglenavnet, som det vises i filen appsettings.json.

## <a name="register-your-key-store"></a>Registrer dit nøglelager

Følgende trin gør det muligt at registrere din DKE-tjeneste. Registrering af din DKE-tjeneste er det sidste trin i udrulning af DKE, før du kan begynde at oprette etiketter.

Sådan registreres DKE-tjenesten:

1. Åbn portalen til [identitetsappen Microsoft Azure din](https://ms.portal.azure.com/) browser, og gå til **Registreringer** \> **for** \> **identitetsappen Alle tjenester**.

2. Vælg **Ny registrering**, og angiv et beskrivende navn.

3. Vælg en kontotype i de viste indstillinger.

   Hvis du bruger en Microsoft Azure med et ikke-brugerdefineret domæne, f.eks **. onmicrosoft.com**, skal du vælge Konti kun i denne organisationsmappe **(kun Microsoft – enkelt lejer).**

   Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Ny appregistrering.](../media/dke-app-registration.png)

4. Nederst på siden skal du vælge Registrer **for at** oprette den nye Appregistrering.

5. I din nye Appregistrering skal du i venstre rude under **Administrer** vælge **Godkendelse**.

6. Vælg **Tilføj en platform**.

7. I pop **op-vindue Konfigurer** platforme skal du vælge **Web**.

8. Under **Redirect URI'er** skal du angive URI'en for din krypteringstjeneste med dobbeltnøgler. Angiv apptjenestens URL-adresse, herunder både værtsnavn og domæne.

   For eksempel: `https://mydkeservicetest.com`

   - Den url-adresse, du angiver, skal svare til værtsnavnet, hvor din DKE-tjeneste installeres.
   - Domænet skal være et [bekræftet domæne](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
   - Hvis du tester lokalt med Visual Studio, skal du bruge `https://localhost:5001`.
   - I alle tilfælde skal skemaet være **https**.

   Sørg for, at værtsnavnet er nøjagtigt det samme som dit apptjenesteværtsnavn. Du har måske ændret det for at `localhost` foretage fejlfinding af buildet. I **appsettings.json er** denne værdi det værtsnavn, du angiver for `JwtAudience`.

9. Under **Implicit tildeling** skal du markere **afkrydsningsfeltet Id-tokens** .

10. Vælg **Gem** for at gemme ændringerne.

11. I venstre rude skal du vælge Vis **en API** ud for Program-id-URI, angive URL-adressen til din apptjeneste, herunder både værtsnavn og domæne, og derefter vælge **Angiv**.

12. På siden **Expose an API i** området, der er **defineret af dette API-område** , skal du vælge **Tilføj et omfang**. I det nye område:

    1. Definer navnet på området **som user_impersonation**.

    2. Vælg de administratorer og brugere, der kan give samtykke.

    3. Definer eventuelle resterende værdier, der er påkrævet.

    4. Vælg **Tilføj omfang**.

    5. Vælg **Gem** øverst for at gemme ændringerne.

13. På siden **Expose an API i** området **Authorized client applications skal** du vælge **Add a client application**.

    I det nye klientprogram:

    1. Definer klient-id'et som `d3590ed6-52b3-4102-aeff-aad2292ab01c`. Denne værdi er det Microsoft Office klient-id, og gør det Office at hente et adgangstoken til nøglelageret.

    2. Under **Tilladte områder skal** du vælge **user_impersonation** område.

    3. Vælg **Tilføj program**.

    4. Vælg **Gem** øverst for at gemme ændringerne.

    5. Gentag disse trin, men denne gang skal du definere klient-id'et som `c00e9d32-3c8d-4a7d-832b-029040e7db99`. Denne værdi er det samlede navn for Azure Information Protection-klient-id'et.

Din DKE-tjeneste er nu registreret. Fortsæt ved at [oprette navne ved hjælp af DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>Opret følsomhedsmærkater ved hjælp af DKE

I Microsoft 365 Overholdelsescenter du oprette en ny følsomhedsmærkat og anvende kryptering, som du ellers ville gøre. Vælg **Brug kryptering med dobbelt nøgle** , og angiv slutpunkts-URL-adressen til nøglen. Du skal medtage det nøglenavn, du har angivet i afsnittet "TestKeys" i filen appsettings.json i URL-adressen.

For eksempel: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![Vælg Brug kryptering med dobbelt nøgle i Microsoft 365 Overholdelsescenter.](../media/dke-use-dke.png)

Alle DKE-navne, du tilføjer, bliver vist for brugere i de seneste versioner af Microsoft 365 Apps for enterprise.

> [!NOTE]
> Det kan tage op til 24 timer, før klienterne opdateres med de nye etiketter.

### <a name="enable-dke-in-your-client"></a>Aktivér DKE i din klient

Hvis du er Insider Office er DKE aktiveret for dig. Ellers skal du aktivere DKE for din klient ved at tilføje følgende registreringsdatabasenøgler:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Overfør beskyttede filer fra HYOK-etiketter til DKE-etiketter

Hvis du vil, kan du, når du er færdig med at konfigurere DKE, overføre indhold, som du har beskyttet, ved hjælp af HYOK-etiketter til DKE-etiketter. Hvis du vil overføre, skal du bruge AIP-scanneren. For at komme i gang med at bruge scanneren skal [du se Hvad er Azure Information Protection Unified Labeling Scanner?](/azure/information-protection/deploy-aip-scanner).

Hvis du ikke overfører indhold, forbliver dit HYOK-beskyttede indhold upåvirket.

## <a name="other-deployment-options"></a>Andre installationsindstillinger

Vi er klar over, at for nogle kunder i meget regulerede brancher er denne standardreferenceimplementeringen ved hjælp af softwarebaserede nøgler muligvis ikke tilstrækkelig til at opfylde deres udvidede overholdelsesforpligtelser og -behov. Vi har indgået partnerskab med leverandører af tredjepartshardwaresikkerhedsmodul (HSM) for at understøtte udvidede nøgleadministrationsmuligheder i DKE-tjenesten, herunder:

- [Entrust](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Thales](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

Kontakt disse leverandører direkte for at få flere oplysninger og vejledning om deres markedsbaserede DKE HSM-løsninger.
