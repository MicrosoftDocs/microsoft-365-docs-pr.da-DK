---
title: Kryptering med dobbelt nøgle (DKE)
description: DKE giver dig mulighed for at beskytte meget følsomme data, samtidig med at du bevarer fuld kontrol over din nøgle.
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
ms.openlocfilehash: 631df77a6f10c15dafcb78e58a715a029d32bb73
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66627541"
---
# <a name="double-key-encryption"></a>Kryptering med dobbelt nøgle

> *Gælder for: Microsoft Purview Double Key Encryption, [Microsoft Purview](https://www.microsoft.com/microsoft-365/business/compliance-management), [Azure Information Protection](https://azure.microsoft.com/pricing/)*
>
> *Instruktioner til: [Azure Information Protection Unified Labeling Client til Windows](/azure/information-protection/faqs#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> *Tjenestebeskrivelse af: [Microsoft Purview](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

DkE (Double Key Encryption) bruger to nøgler sammen til at få adgang til beskyttet indhold. Microsoft gemmer én nøgle i Microsoft Azure, og du holder den anden nøgle. Du bevarer fuld kontrol over en af dine nøgler ved hjælp af tjenesten Dobbeltnøglekryptering. Du kan anvende beskyttelse ved hjælp af Azure Information Protection Unified Labeling-klienten til dit meget følsomme indhold.

Dobbeltnøglekryptering understøtter både udrulninger i cloudmiljøet og det lokale miljø. Disse udrulninger hjælper med at sikre, at krypterede data forbliver uigennemsigtige, uanset hvor du gemmer de beskyttede data.

Du kan få flere oplysninger om standardnøglerne for cloudbaserede lejere under [Planlægning og implementering af din Azure Information Protection-lejernøgle](/azure/information-protection/plan-implement-tenant-key).

## <a name="when-your-organization-should-adopt-dke"></a>Når din organisation skal indføre DKE

Kryptering med dobbelt nøgle er beregnet til de mest følsomme data, der er underlagt de strengeste beskyttelseskrav. DKE er ikke beregnet til alle data. Generelt bruger du kryptering med dobbelt nøgle til kun at beskytte en lille del af dine overordnede data. Du skal være omhyggelig med at identificere de rigtige data, der skal dækkes med denne løsning, før du udruller. I nogle tilfælde skal du muligvis begrænse dit omfang og bruge andre løsninger til de fleste af dine data, f.eks. Microsoft Purview Information Protection med Microsoft-administrerede nøgler eller BYOK. Disse løsninger er tilstrækkelige til dokumenter, der ikke er underlagt forbedret beskyttelse og lovmæssige krav. Disse løsninger giver dig også mulighed for at bruge de mest effektive Office 365 tjenester, som du ikke kan bruge med DKE-krypteret indhold. Eksempel:

- Transportregler, herunder antimalware og spam, der kræver synlighed i den vedhæftede fil
- Microsoft Delve
- eDiscovery
- Indholdssøgning og -indeksering
- Office Web Apps herunder samtidig redigeringsfunktionalitet

Eksterne programmer eller tjenester, der ikke er integreret med DKE via Microsoft Information Protection (MIP) SDK, kan ikke udføre handlinger på de krypterede data.

Microsoft Information Protection SDK 1.7+ understøtter kryptering med dobbelt nøgle. Programmer, der integrerer med vores SDK, kan være årsag til disse data med tilstrækkelige tilladelser og integrationer på plads.

Brug Microsoft Purview Information Protection funktioner (klassificering og mærkning) til at beskytte de fleste af dine følsomme data og kun bruge DKE til dine missionskritiske data. Dobbeltnøglekryptering er relevant for følsomme data i stærkt regulerede brancher som finansielle tjenester og sundhedssektoren.

Hvis din organisation har et af følgende krav, kan du bruge DKE til at hjælpe med at sikre dit indhold:

- Du vil sikre, at det under alle omstændigheder *kun er dig* , der kan dekryptere beskyttet indhold.
- Du ønsker ikke, at Microsoft skal have adgang til beskyttede data alene.
- Du har lovmæssige krav om at indeholde nøgler inden for en geografisk grænse. Alle de nøgler, du holder for datakryptering og dekryptering, vedligeholdes i dit datacenter.

## <a name="system-and-licensing-requirements-for-dke"></a>System- og licenskrav til DKE

**Kryptering med dobbelt nøgle** leveres med Microsoft 365 E5. Hvis du ikke har en Microsoft 365 E5 licens, kan du tilmelde dig en [prøveversion](https://aka.ms/M365E5ComplianceTrial). Du kan finde flere oplysninger om disse licenser i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**Azure Information Protection**. DKE fungerer med følsomhedsmærkater og kræver Azure Information Protection.

DKE-følsomhedsmærkater gøres tilgængelige for slutbrugere via følsomhedsknappen i AIP Unified Labeling-klienten i Office Desktop Apps. Installér disse forudsætninger på hver klientcomputer, hvor du vil beskytte og bruge beskyttede dokumenter.

**Microsoft Office Apps for enterprise** version 2009 eller nyere (Desktop-versioner af Word, PowerPoint og Excel) på Windows.

**Azure Information Protection Unified Labeling Client** version 2.7.93.0 eller nyere. Download og installér Unified Labeling-klienten fra [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018).

## <a name="supported-environments-for-storing-and-viewing-dke-protected-content"></a>Understøttede miljøer til lagring og visning af DKE-beskyttet indhold

**Understøttede programmer**. [Microsoft 365 Apps for enterprise](https://www.microsoft.com/microsoft-365/business/microsoft-365-apps-for-enterprise-product) klienter på Windows, herunder Word, Excel og PowerPoint.

**Understøttelse af onlineindhold**. Du kan gemme dokumenter og filer, der er beskyttet med dobbeltnøglekryptering online, både i Microsoft SharePoint og OneDrive for Business. Du skal forsyne dokumenter og filer med DKE med understøttede applikationer med mærkater og beskytte dem, før du uploader dem. Du kan dele krypteret indhold via mail, men du kan ikke få vist krypterede dokumenter og filer online. Du skal i stedet få vist beskyttet indhold ved hjælp af de understøttede skrivebordsprogrammer og klienter på din lokale computer.

## <a name="overview-of-deploying-dke"></a>Oversigt over udrulning af DKE

Du skal følge disse generelle trin for at konfigurere DKE. Når du har fuldført disse trin, kan dine slutbrugere beskytte dine meget følsomme data med kryptering med dobbelt nøgle.

1. Installér DKE-tjenesten som beskrevet i denne artikel.

2. Opret en mærkat med dobbelt nøglekryptering. I Microsoft Purview-compliance-portal skal du navigere til **Information Protection** og oprette en ny mærkat med dobbelt nøglekryptering. Se [Begræns adgang til indhold ved hjælp af følsomhedsmærkater for at anvende kryptering](./encryption-sensitivity-labels.md).

3. Brug dobbelte nøglekrypteringsmærkater. Beskyt data ved at vælge mærkaten Krypteret med dobbelt nøgle på båndet Følsomhed i Microsoft Office.

Du kan udføre nogle af trinnene for at installere kryptering med dobbelt nøgle på flere måder. Denne artikel indeholder detaljerede instruktioner, så mindre erfarne administratorer kan udrulle tjenesten. Hvis du er fortrolig med at gøre det, kan du vælge at bruge dine egne metoder.

## <a name="deploy-dke"></a>Udrul DKE

I denne artikel og i installationsvideoen bruges Azure som udrulningsdestination for DKE-tjenesten. Hvis du udruller til en anden placering, skal du angive dine egne værdier.


Du skal følge disse generelle trin for at konfigurere kryptering med dobbelt nøgle for din organisation.

1. [Installér softwareforudsætningerne for DKE-tjenesten](#install-software-prerequisites-for-the-dke-service)
1. [Klon GitHub-lageret med dobbelt nøglekryptering](#clone-the-dke-github-repository)
1. [Rediger programindstillinger](#modify-application-settings)
1. [Generér testnøgler](#generate-test-keys)
1. [Byg projektet](#build-the-project)
1. [Udrul DKE-tjenesten, og publicer nøglelageret](#deploy-the-dke-service-and-publish-the-key-store)
1. [Valider din udrulning](#validate-your-deployment)
1. [Registrer din nøglebutik](#register-your-key-store)
1. [Opret følsomhedsmærkater ved hjælp af DKE](#create-sensitivity-labels-using-dke)
1. [Aktivér DKE i din klient](#enable-dke-in-your-client)
1. [Overfør beskyttede filer fra HYOK-mærkater til DKE-mærkater](#migrate-protected-files-from-hyok-labels-to-dke-labels)

Når du er færdig, kan du kryptere dokumenter og filer ved hjælp af DKE. Du kan finde flere oplysninger under [Anvend følsomhedsmærkater på dine filer og mails i Office](https://support.microsoft.com/office/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

### <a name="install-software-prerequisites-for-the-dke-service"></a>Installér softwareforudsætningerne for DKE-tjenesten

Installér disse forudsætninger på den computer, hvor du vil installere DKE-tjenesten.

**.NET Core 3.1 SDK**. Download og installér SDK'et fra [Download .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1).

**Visual Studio Code**. Download Visual Studio Code fra [https://code.visualstudio.com/](https://code.visualstudio.com). Når Visual Studio Code er installeret, skal du vælge **Vis** \> **udvidelser**. Installér disse udvidelser.

- C# til Visual Studio Code

- NuGet Package Manager

**Git-ressourcer**. Download og installér en af følgende.

- [Git](https://git-scm.com/downloads)

- [GitHub Desktop](https://desktop.github.com/)

- [GitHub Enterprise](https://github.com/enterprise)

**Openssl** Du skal have [OpenSSL](https://slproweb.com/products/Win32OpenSSL.html) installeret for at [kunne generere testnøgler](#generate-test-keys) , når du har installeret DKE. Sørg for, at du aktiverer den korrekt fra stien til dine miljøvariabler. Se f.eks. "Føj installationsmappen til PATH" på [https://www.osradar.com/install-openssl-windows/](https://www.osradar.com/install-openssl-windows/) for at få flere oplysninger.

### <a name="clone-the-dke-github-repository"></a>Klon DKE GitHub-lageret

Microsoft leverer DKE-kildefilerne i et GitHub-lager. Du kloner lageret for at bygge projektet lokalt til din organisations brug. DKE GitHub-lageret er placeret på [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

Følgende instruktioner er beregnet til uerfarne brugere af Git eller Visual Studio Code:

1. I din browser skal du gå til: [https://github.com/Azure-Samples/DoubleKeyEncryptionService](https://github.com/Azure-Samples/DoubleKeyEncryptionService).

2. Mod højre side af skærmen skal du vælge **Kode**. Din version af brugergrænsefladen viser muligvis knappen **Klon eller download** . Vælg derefter kopiikonet på den rulleliste, der vises, for at kopiere URL-adressen til udklipsholderen.

    Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Klon lageret med dobbeltnøglekrypteringstjenesten fra GitHub.](../media/dke-clone.png)

3. I Visual Studio Code skal du vælge **Vis** \> **kommandopalet** og vælge **Git: Klon**. Hvis du vil gå til indstillingen på listen, skal du begynde at skrive `git: clone` for at filtrere posterne og derefter vælge det på rullelisten. Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Indstillingen Visual Studio Code GIT:Clone.](../media/dke-vscode-clone.png)

4. I tekstfeltet skal du indsætte den URL-adresse, du kopierede fra Git, og vælge **Klon fra GitHub**.

5. I dialogboksen **Vælg mappe** , der vises, skal du gå til og vælge en placering, hvor lageret skal gemmes. Vælg **Åbn** ved prompten.

    Lageret åbnes i Visual Studio Code og viser den aktuelle Git-forgrening nederst til venstre. Forgreningen skal f.eks. være **den primære**. Eksempel:

   ![Skærmbillede af DKE-lageret i Visual Studio Code, der viser hovedgrenen.](../media/dke-vscode-main-branch.jpg)

6. Hvis du ikke er på hovedgrenen, skal du vælge den. I Visual Studio Code skal du vælge forgreningen og vælge **hoved** på listen over forgreninger, der vises.

   > [!IMPORTANT]
   > Hvis du vælger hovedgrenen, sikrer du, at du har de korrekte filer til at oprette projektet. Hvis du ikke vælger den korrekte forgrening, mislykkes installationen.

Du har nu konfigureret dit DKE-kildelager lokalt. Rediger derefter [programindstillingerne](#modify-application-settings) for din organisation.

### <a name="modify-application-settings"></a>Rediger programindstillinger

Hvis du vil installere DKE-tjenesten, skal du ændre følgende programindstillinger:

- [Indstillinger for nøgleadgang](#key-access-settings)
- [Lejer- og nøgleindstillinger](#tenant-and-key-settings)

Du ændrer programindstillingerne i filen appsettings.json. Denne fil er placeret i det DoubleKeyEncryptionService-lager, du klonede lokalt under DoubleKeyEncryptionService\src\customer-key-store. I Visual Studio Code kan du f.eks. gå til filen som vist på følgende billede.

![Søgning efter filen appsettings.json for DKE.](../media/dke-appsettingsjson.png)

#### <a name="key-access-settings"></a>Indstillinger for nøgleadgang

Vælg, om du vil bruge mail- eller rollegodkendelse. DKE understøtter kun én af disse godkendelsesmetoder ad gangen.

- **Godkendelse via mail**. Gør det muligt for din organisation at godkende adgang til nøgler, der kun er baseret på mailadresser.

- **Rolleautorisation**. Gør det muligt for din organisation at godkende adgang til nøgler, der er baseret på Active Directory-grupper, og kræver, at webtjenesten kan forespørge på LDAP.

##### <a name="to-set-key-access-settings-for-dke-using-email-authorization"></a>Sådan angiver du nøgleadgangsindstillinger for DKE ved hjælp af mailgodkendelse

1. Åbn filen **appsettings.json** , og find indstillingen `AuthorizedEmailAddress` .

2. Tilføj den eller de mailadresser, du vil godkende. Adskil flere mailadresser med dobbelte anførselstegn og kommaer. Eksempel:

   ```json
   "AuthorizedEmailAddress": ["email1@company.com", "email2@company.com ", "email3@company.com"]
   ```

3. Find indstillingen, `LDAPPath` og fjern teksten `If you use role authorization (AuthorizedRoles) then this is the LDAP path.` mellem dobbelte anførselstegn. Lad dobbelte anførselstegn være på plads. Når du er færdig, bør indstillingen se sådan ud.

   ```json
   "LDAPPath": ""
   ```

4. Find indstillingen, `AuthorizedRoles` og slet hele linjen.

På dette billede vises filen **appsettings.json** , der er korrekt formateret til mailgodkendelse.

   ![Filen appsettings.json, der viser godkendelsesmetoden for mail.](../media/dke-email-accesssetting.png)

##### <a name="to-set-key-access-settings-for-dke-using-role-authorization"></a>Sådan angiver du vigtige adgangsindstillinger for DKE ved hjælp af rolleautorisation

1. Åbn filen **appsettings.json** , og find indstillingen `AuthorizedRoles` .

2. Tilføj de Active Directory-gruppenavne, du vil godkende. Adskil flere gruppenavne med dobbelte anførselstegn og kommaer. Eksempel:

   ```json
   "AuthorizedRoles": ["group1", "group2", "group3"]
   ```

3. Find indstillingen, `LDAPPath` og tilføj Active Directory-domænet. Eksempel:

   ```json
   "LDAPPath": "contoso.com"
   ```

4. Find indstillingen, `AuthorizedEmailAddress` og slet hele linjen.

På dette billede vises filen **appsettings.json** , der er korrekt formateret til rollegodkendelse.

   ![appsettings.json-fil, der viser rollegodkendelsesmetoden.](../media/dke-role-accesssetting.png)

#### <a name="tenant-and-key-settings"></a>Lejer- og nøgleindstillinger

DKE-lejer- og nøgleindstillinger er placeret i **filen appsettings.json** .

##### <a name="to-configure-tenant-and-key-settings-for-dke"></a>Sådan konfigurerer du lejer- og nøgleindstillinger for DKE

1. Åbn filen **appsettings.json** .

2. Find indstillingen, `ValidIssuers` og erstat `<tenantid>` med dit lejer-id. Du kan finde dit lejer-id ved at gå til Azure Portal og få vist [lejeregenskaberne](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). Eksempel:

   ```json
   "ValidIssuers": [
     "https://sts.windows.net/9c99431e-b513-44be-a7d9-e7b500002d4b/"
   ]
   ```

> [!NOTE]
> Hvis du vil aktivere ekstern B2B-adgang til dit nøglelager, skal du også inkludere disse eksterne lejere som en del af listen over gyldige udstedere.

`JwtAudience`Find . Erstat `<yourhostname>` med værtsnavnet på den computer, hvor DKE-tjenesten skal køre. Eksempel: "https://dkeservice.contoso.com"

  > [!IMPORTANT]
  > Værdien for `JwtAudience` skal svare *nøjagtigt* til navnet på din vært.  

- `TestKeys:Name`. Angiv et navn til din nøgle. For eksempel: `TestKey1`
- `TestKeys:Id`. Opret et GUID, og angiv det som `TestKeys:ID` værdien. Det kunne f.eks. være `DCE1CC21-FF9B-4424-8FF4-9914BD19A1BE`. Du kan bruge et websted som [Online GUID Generator](https://guidgenerator.com/) til tilfældigt at generere et GUID.

På dette billede vises det korrekte format for lejer- og nøgleindstillinger i **appsettings.json**. `LDAPPath` er konfigureret til rolleautorisation.

![Viser korrekte lejer- og nøgleindstillinger for DKE i filen appsettings.json.](../media/dke-appsettingsjson-tenantkeysettings.png)

### <a name="generate-test-keys"></a>Generér testnøgler

Når du har defineret dine programindstillinger, er du klar til at generere offentlige og private testnøgler.

Sådan opretter du nøgler:

1. Kør OpenSSL-kommandoprompten i Menuen Start i Windows.

1. Skift til den mappe, hvor du vil gemme testnøglerne. De filer, du opretter ved at fuldføre trinnene i denne opgave, gemmes i den samme mappe.

1. Generér den nye testnøgle.

   ```console
   openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365
   ```

1. Opret den private nøgle.

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

1. Åbn **pubkeyonly.pem** i en teksteditor. Kopiér alt indholdet i filen **pubkeyonly.pem** , undtagen den første og sidste linje, til `PublicPem` afsnittet i filen **appsettings.json** .

1. Åbn **privkeynopass.pem** i en teksteditor. Kopiér alt indholdet i filen **privkeynopass.pem** , undtagen de første og sidste linjer, til `PrivatePem` afsnittet i filen **appsettings.json** .

1. Fjern alle tomme mellemrum og nye linjer i både sektionerne `PublicPem` og `PrivatePem` .

    > [!IMPORTANT]
    > Når du kopierer dette indhold, skal du ikke slette nogen af PEM-dataene.

1. Gå til filen **Startup.cs** i Visual Studio Code. Denne fil er placeret i det DoubleKeyEncryptionService-lager, du klonede lokalt under DoubleKeyEncryptionService\src\customer-key-store\.

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

    Slutresultaterne skal ligne følgende.

    ![startup.cs til offentlig prøveversion.](../media/dke-startupcs-usetestkeys.png)

Nu er du klar til at [bygge dit DKE projekt](#build-the-project).

### <a name="build-the-project"></a>Byg projektet

Brug følgende instruktioner til at bygge DKE-projektet lokalt:

1. I Visual Studio Code skal du i DKE-tjenestelageret vælge **Vis** \> **kommandopalet** og derefter skrive **build** ved prompten.

2. På listen skal du vælge **Opgaver: Kør buildopgave**.

   Hvis der ikke blev fundet nogen buildopgaver, skal du vælge **Konfigurer buildopgave** og oprette en til .NET Core på følgende måde.

   ![Konfigurer manglende buildopgave for .NET.](../media/dke-configurebuildtask.png)

   1. Vælg **Opret tasks.json fra skabelon**.

      ![Opret filen tasks.json fra skabelon for DKE.](../media/dke-createtasksjsonfromtemplate.png)

   2. Vælg **.NET Core** på listen over skabelontyper.

      ![Vælg den korrekte skabelon for DKE.](../media/dke-tasksjsontemplate.png)

   3. Find stien til filen **customerkeystore.csproj** i buildafsnittet. Hvis den ikke er der, skal du tilføje følgende linje:

      ```json
      "${workspaceFolder}/src/customer-key-store/customerkeystore.csproj",
      ```

   4. Kør buildet igen.

3. Kontrollér, at der ikke er nogen røde fejl i outputvinduet.

   Hvis der er røde fejl, skal du kontrollere konsoloutputtet. Sørg for, at du har fuldført alle tidligere trin korrekt, og at de korrekte buildversioner er til stede.


Konfigurationen er nu fuldført. Før du publicerer keystore i appsettings.json for indstillingen JwtAudience, skal du sikre, at værdien for værtsnavnet stemmer nøjagtigt overens med dit App Service værtsnavn. 

### <a name="deploy-the-dke-service-and-publish-the-key-store"></a>Udrul DKE-tjenesten, og publicer nøglelageret

I forbindelse med produktionsinstallationer skal du udrulle tjenesten enten i et tredjepartscloudmiljø eller [publicere til et lokalt system](/aspnet/core/tutorials/publish-to-iis?preserve-view=true&tabs=netcore-cli&view=aspnetcore-3.1).

Du foretrækker måske andre metoder til at installere dine nøgler. Vælg den metode, der fungerer bedst for din organisation.

I forbindelse med pilotudrulninger kan du udrulle i Azure og komme i gang med det samme.

#### <a name="to-create-an-azure-web-app-instance-to-host-your-dke-deployment"></a>Sådan opretter du en Forekomst af Azure Web App, der skal hoste din DKE-udrulning

Hvis du vil publicere nøglelageret, skal du oprette en Azure App Service instans, der skal hoste din DKE-udrulning. Derefter skal du publicere dine genererede nøgler på Azure.

1. Log på [Microsoft Azure Portal](https://ms.portal.azure.com) i din browser, og gå til **Tilføj** **apptjenester** > .

2. Vælg dit abonnement og din ressourcegruppe, og definer oplysninger om din forekomst.

   - Angiv værtsnavnet på den computer, hvor du vil installere DKE-tjenesten. Kontrollér, at navnet er det samme som det, der er defineret for indstillingen JwtAudience i filen [**appsettings.json**](#tenant-and-key-settings) . Den værdi, du angiver for navnet, er også WebAppInstanceName.

   - Vælg **kode** for **Publicer**, og vælg **.NET Core 3.1** som **Kørselsstak**.

   Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Tilføj din App Service.](../media/dke-azure-add-app-service.png)

3. Nederst på siden skal du vælge **Gennemse + opret** og derefter vælge **Tilføj**.

4. Benyt en af følgende fremgangsmåder for at publicere dine genererede nøgler:

   - [Publicer via ZipDeployUI](#publish-via-zipdeployui)
   - [Udgiv via FTP](#publish-via-ftp)
   - [Publicer via Visual Studio 2019 eller nyere](/aspnet/core/tutorials/)

#### <a name="publish-via-zipdeployui"></a>Publicer via ZipDeployUI

1. Gå til `https://<WebAppInstanceName>.scm.azurewebsites.net/ZipDeployUI`.

   For eksempel: `https://dkeservice.contoso.scm.azurewebsites.net/ZipDeployUI`

2. I kodebasen for nøglelageret skal du gå til mappen **customer-key-store\src\customer-key-store** og kontrollere, at denne mappe indeholder filen **customerkeystore.csproj** .

3. Kør: **dotnet publicer**

   Outputvinduet viser den mappe, hvor publiceringen blev installeret.

   For eksempel: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

4. Send alle filer i mappen Publicer til en .zip-fil. Når du opretter den .zip fil, skal du sørge for, at alle filer i mappen er på rodniveau for .zip-filen.

5. Træk og slip den .zip fil, du opretter, på det ZipDeployUI-websted, du åbnede ovenfor. For eksempel: `https://dkeservice.scm.azurewebsites.net/ZipDeployUI`

DKE er udrullet, og du kan gå til de testnøgler, du har oprettet. Fortsæt med at [validere installationen](#validate-your-deployment) nedenfor.

#### <a name="publish-via-ftp"></a>Udgiv via FTP

1. Opret forbindelse til de App Service, du oprettede [ovenfor](#deploy-the-dke-service-and-publish-the-key-store).

   Gå til: **Azure Portal** >  **App Service** >  **Deployment Center** > **Manual Deployment** > **FTP** > **Dashboard** i browseren.

2. Kopiér de forbindelsesstrenge, der vises, til en lokal fil. Du skal bruge disse strenge til at oprette forbindelse til App Service og overføre filer via FTP.

   Eksempel:

   ![Kopiér forbindelsesstrenge fra FTP-dashboardet.](../media/dke-ftp-dashboard.png)

3. I kodebasen for nøglelageret skal du gå til **mappen customer-key-store\src\customer-key-store**.

4. Kontrollér, at denne mappe indeholder filen **customerkeystore.csproj** .

5. Kør: **dotnet publicer**

   Outputtet indeholder den mappe, hvor publiceringen blev installeret.

   For eksempel: `customer-key-store\src\customer-key-store\bin\Debug\netcoreapp3.1\publish\`

6. Send alle filer i mappen Publicer til en zip-fil. Når du opretter den .zip fil, skal du sørge for, at alle filer i mappen er på rodniveau for .zip-filen.

7. Brug de forbindelsesoplysninger, du kopierede, fra FTP-klienten til at oprette forbindelse til App Service. Upload den .zip fil, du oprettede i det forrige trin, til rodmappen på din Web App.

DKE er udrullet, og du kan gå til de testnøgler, du har oprettet. Derefter [skal du validere udrulningen](#validate-your-deployment).

### <a name="validate-your-deployment"></a>Valider din udrulning

Når du har udrullet DKE ved hjælp af en af de metoder, der er beskrevet ovenfor, skal du validere indstillingerne for udrulningen og nøglelageret.

Køre:

```powershell
src\customer-key-store\scripts\key_store_tester.ps1 dkeserviceurl/mykey
```

Eksempel:

```powershell
key_store_tester.ps1 https://dkeservice.contoso.com/TestKey1
```

Sørg for, at der ikke vises nogen fejl i outputtet. Når du er klar, [skal du registrere din nøglebutik](#register-your-key-store).

Der skelnes mellem store og små bogstaver i nøglenavnet. Angiv nøglenavnet, som det vises i filen appsettings.json.

## <a name="register-your-key-store"></a>Registrer din nøglebutik

Følgende trin giver dig mulighed for at registrere din DKE-tjeneste. Registrering af din DKE-tjeneste er det sidste trin i udrulningen af DKE, før du kan begynde at oprette mærkater.

Sådan registrerer du DKE-tjenesten:

1. Åbn [Microsoft Azure Portal](https://ms.portal.azure.com/) i din browser, og gå til **Alle** **tjenesteidentitetsappregistreringer** \> \>.

2. Vælg **Ny registrering**, og angiv et sigende navn.

3. Vælg en kontotype i de viste indstillinger.

    Eksempel:

   > [!div class="mx-imgBorder"]
   > ![Ny appregistrering.](../media/dke-app-registration.png)

4. Nederst på siden skal du vælge **Registrer** for at oprette den nye appregistrering.

5. Vælg **Godkendelse** under **Administrer** i den nye appregistrering i ruden til venstre.

6. Vælg **Tilføj en platform**.

7. I pop op-vinduet **Konfigurer platforme** skal du vælge **Web**.

8. Angiv URI'en for krypteringstjenesten med dobbelt nøgle under **Omdirigerings-URI'er**. Angiv App Service URL-adresse, herunder både værtsnavn og domæne.

   For eksempel: `https://mydkeservicetest.com`

   - Den URL-adresse, du angiver, skal svare til det værtsnavn, hvor din DKE-tjeneste er installeret.
   - Domænet skal være et [bekræftet domæne](/azure/active-directory/develop/reference-breaking-changes#appid-uri-in-single-tenant-applications-will-require-use-of-default-scheme-or-verified-domains).
    - I alle tilfælde skal skemaet være **https**.

   Sørg for, at værtsnavnet stemmer nøjagtigt overens med App Service værtsnavn.

9. Under **Implicit tildeling** skal du markere afkrydsningsfeltet **Id-tokens** .

10. Vælg **Gem** for at gemme dine ændringer.

11. I ruden til venstre skal du vælge **Vis en API** ud for URI'en for program-id, angive din App Service URL-adresse, herunder både værtsnavn og domæne, og derefter vælge **Angiv**.

12. På siden **Vis en API** skal du i de **områder, der er defineret af dette API-område** , vælge **Tilføj et område**. I det nye område:

    1. Definer områdenavnet som **user_impersonation**.

    2. Vælg de administratorer og brugere, der kan give samtykke.

    3. Definer eventuelle resterende værdier, der skal angives.

    4. Vælg **Tilføj område**.

    5. Vælg **Gem** øverst for at gemme dine ændringer.

13. På siden **Vis en API** i området **Godkendte klientprogrammer** skal du stadig vælge **Tilføj et klientprogram**.

    I det nye klientprogram:

    1. Definer klient-id'et som `d3590ed6-52b3-4102-aeff-aad2292ab01c`. Denne værdi er Microsoft Office-klient-id'et og gør det muligt for Office at hente et adgangstoken til dit nøglelager.

    2. Vælg området **user_impersonation** under **Godkendte områder**.

    3. Vælg **Tilføj program**.

    4. Vælg **Gem** øverst for at gemme dine ændringer.

    5. Gentag disse trin, men denne gang skal du definere klient-id'et som `c00e9d32-3c8d-4a7d-832b-029040e7db99`. Denne værdi er Azure Information Protection unified labeling-klient-id.

Din DKE service er nu registreret. Fortsæt ved [at oprette mærkater ved hjælp af DKE](#create-sensitivity-labels-using-dke).

## <a name="create-sensitivity-labels-using-dke"></a>Opret følsomhedsmærkater ved hjælp af DKE

I Microsoft Purview-compliance-portal skal du oprette en ny følsomhedsmærkat og anvende kryptering, som du ellers ville gøre. Vælg **Brug kryptering med dobbelt nøgle** , og angiv URL-adressen til slutpunktet for din nøgle. Du skal inkludere det nøglenavn, du har angivet, i afsnittet "TestKeys" i filen appsettings.json i URL-adressen.

For eksempel: `https://testingdke1.azurewebsites.net/KEYNAME`

> [!div class="mx-imgBorder"]
> ![Vælg Brug kryptering med dobbelt nøgle i Microsoft Purview-compliance-portal.](../media/dke-use-dke.png)

Alle DKE-mærkater, du tilføjer, vises for brugere i de nyeste versioner af Microsoft 365 Apps for enterprise.

> [!NOTE]
> Det kan tage op til 24 timer, før klienterne opdateres med de nye mærkater.

### <a name="enable-dke-in-your-client"></a>Aktivér DKE i din klient

Hvis du er Office Insider, er DKE aktiveret for dig. Ellers skal du aktivere DKE for din klient ved at tilføje følgende registreringsdatabasenøgler:

```console
   [HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001

   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\flighting]
   "DoubleKeyProtection"=dword:00000001
```

## <a name="migrate-protected-files-from-hyok-labels-to-dke-labels"></a>Overfør beskyttede filer fra HYOK-mærkater til DKE-mærkater

Når du er færdig med at konfigurere DKE, kan du overføre indhold, du har beskyttet, ved hjælp af HYOK-mærkater til DKE-mærkater. Hvis du vil overføre, skal du bruge AIP-scanneren. Hvis du vil i gang med at bruge scanneren, skal [du se Hvad er Azure Information Protection Unified Labeling Scanner?](/azure/information-protection/deploy-aip-scanner).

Hvis du ikke overfører indhold, påvirkes dit HYOK-beskyttede indhold ikke.

## <a name="other-deployment-options"></a>Andre installationsindstillinger

Vi er klar over, at for nogle kunder i stærkt regulerede brancher er denne standardreferenceimplementering ved hjælp af softwarebaserede nøgler muligvis ikke tilstrækkelig til at opfylde deres forbedrede overholdelsesforpligtelser og behov. Vi har indgået partnerskab med tredjepartsleverandører af hardwaresikkerhedsmoduler (HSM) for at understøtte forbedrede muligheder for nøgleadministration i DKE-tjenesten, herunder:

- [Overlade](https://www.entrust.com/digital-security/hsm/services/packaged-services/double-key-encryption-integration#:~:text=Entrust%20Double%20Key%20Encryption%20for%20Microsoft%20AIP%2C%20offered,trust%20for%20the%20protection%20of%20sensitive%20cryptographic%20keys.)

- [Thales](https://cpl.thalesgroup.com/cloud-security/encryption/double-key-encryption)

Kontakt disse forhandlere for at få mere information og vejledning om deres DKE HSM-løsninger på markedet.
