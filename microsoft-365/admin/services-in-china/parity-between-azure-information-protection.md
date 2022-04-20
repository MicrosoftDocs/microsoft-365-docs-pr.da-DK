---
title: Azure Information Protection support til Office 365, der drives af 21Vianet
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEU150
- GEA150
description: Få mere at vide om Azure Information Protection (AIP) til Office 365, der drives af 21Vianet, og hvordan du konfigurerer det for kunder i Kina.
monikerRange: o365-21vianet
ms.openlocfilehash: 0f495139a807d4a0eeb3181626717c6d5061fc38
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935209"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>Azure Information Protection support til Office 365, der drives af 21Vianet

I denne artikel beskrives forskellene mellem understøttelse af Azure Information Protection (AIP) for Office 365, der drives af 21Vianet og kommercielle tilbud, samt specifikke instruktioner til konfiguration af AIP til kunder i Kina&mdash;, herunder hvordan du installerer AIP-scannerjob i det lokale miljø og administrerer indholdsscanningsjob.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Forskelle mellem AIP for Office 365, der drives af 21Vianet, og kommercielle tilbud

Selvom vores mål er at levere alle kommercielle funktioner og funktionalitet til kunder i Kina med vores AIP for Office 365 drevet af 21Vianet-tilbud, er der nogle manglende funktioner, som vi gerne vil fremhæve.

Følgende liste indeholder de eksisterende huller mellem AIP for Office 365 drevet af 21Vianet og vores kommercielle tilbud fra og med januar 2021:

- AD RMS-kryptering (Active Directory Rights Management-tjenester) understøttes kun i Microsoft 365 Apps for enterprise (build 11731.10000 eller nyere). Office Professional Plus understøtter ikke AD RMS.

- Overførsel fra AD RMS til AIP er i øjeblikket ikke tilgængelig.
  
- Deling af beskyttede mails med brugere i det kommercielle cloudmiljø understøttes.
  
- Deling af dokumenter og vedhæftede filer med brugere i det kommercielle cloudmiljø er i øjeblikket ikke tilgængelig. Dette omfatter Office 365, der drives af 21Vianet-brugere i det kommercielle cloudmiljø, som ikke Office 365 drevet af 21Vianet-brugere i den kommercielle cloud, og brugere med en RMS for Individuals-licens.
  
- IRM med SharePoint (IRM-beskyttede websteder og biblioteker) er i øjeblikket ikke tilgængelig.
  
- Mobilenhedsudvidelsen til AD RMS er ikke tilgængelig i øjeblikket.

- [Mobilfremviseren](/azure/information-protection/rms-client/mobile-app-faq) understøttes ikke af Azure China 21Vianet.

- AIP-området i Azure Portal er ikke tilgængeligt for kunder i Kina. Brug [PowerShell-kommandoer](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) i stedet for at udføre handlinger på portalen, f.eks. administrere og køre dine indholdsscanningsjob.

- AIP-slutpunkter i Office 365, der drives af 21Vianet, er anderledes end de slutpunkter, der kræves til andre cloudtjenester. Netværksforbindelse fra klienter til følgende slutpunkter er påkrævet:
    - Download politikker for mærkater og mærkater: `*.protection.partner.outlook.cn`
    - Azure Rights Management-tjeneste: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Konfigurer AIP for kunder i Kina

Sådan konfigurerer du AIP for kunder i Kina:
1. [Aktivér Rights Management for lejeren](#step-1-enable-rights-management-for-the-tenant).

1. [Tilføj Tjenesteprincipalen Microsoft Purview Information Protection Synkroniser tjeneste](#step-2-add-the-microsoft-purview-information-protection-sync-service-service-principal).

1. [Konfigurer DNS-kryptering](#step-3-configure-dns-encryption).

1. [Installér og konfigurer AIP Unified-navngivningsklienten](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Konfigurer AIP-apps på Windows](#step-5-configure-aip-apps-on-windows).

1. [Installér AIP-scanneren i det lokale miljø, og administrer job til indholdsscanning](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>Trin 1: Aktivér Rights Management for lejeren

Hvis krypteringen skal fungere korrekt, skal RMS være aktiveret for lejeren.

1. Kontrollér, om RMS er aktiveret:

    1. Start PowerShell som administrator.
    2. Hvis AIPService-modulet ikke er installeret, skal du køre `Install-Module AipService`.
    3. Importér modulet ved hjælp af `Import-Module AipService`.
    4. Forbind til tjenesten ved hjælp af `Connect-AipService -environmentname azurechinacloud`.
    5. Kør `(Get-AipServiceConfiguration).FunctionalState` , og kontrollér, om tilstanden er `Enabled`.

2. Hvis funktionstilstanden er `Disabled`, skal du køre `Enable-AipService`.

### <a name="step-2-add-the-microsoft-purview-information-protection-sync-service-service-principal"></a>Trin 2: Tilføj Tjenesteprincipalen Microsoft Purview Information Protection synkroniser tjeneste

**Tjenesteprincipalen Microsoft Purview Information Protection Synkroniseringstjeneste** er som standard ikke tilgængelig i Azure China-lejere og kræves til Azure Information Protection. Opret denne tjenesteprincipal manuelt via Azure Az PowerShell-modulet.

1. Hvis du ikke har installeret Azure Az-modulet, skal du installere det eller bruge en ressource, hvor Azure Az-modulet er forudinstalleret, f.eks [. Azure Cloud Shell](/azure/cloud-shell/overview). Du kan få flere oplysninger under [Installér Azure Az PowerShell-modulet](/powershell/azure/install-az-ps).

1. Forbind til tjenesten ved hjælp af [cmdlet'en Forbind-AzAccount](/powershell/module/az.accounts/Connect-AzAccount) og `azurechinacloud` miljønavnet:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. Opret **tjenesteprincipalen Microsoft Purview Information Protection synkroniser tjeneste** manuelt ved hjælp af cmdlet'en [New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) og `870c4f2e-85b6-4d43-bdda-6ed9a579b725` program-id'et for Microsoft Purview Information Protection Synkroniseringstjeneste:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Når du har tilføjet tjenesteprincipalen, skal du føje de relevante tilladelser, der kræves til tjenesten.

### <a name="step-3-configure-dns-encryption"></a>Trin 3: Konfigurer DNS-kryptering

Hvis kryptering skal fungere korrekt, skal Office klientprogrammer oprette forbindelse til forekomsten af tjenesten i Kina og bootstrap derfra. Hvis du vil omdirigere klientprogrammer til den rette tjenesteforekomst, skal lejeradministratoren konfigurere en DNS SRV-post med oplysninger om URL-adressen til Azure RMS. Uden DNS SRV-posten forsøger klientprogrammet som standard at oprette forbindelse til den offentlige cloudforekomst og mislykkes.

Antagelsen er også, at brugerne logger på med et brugernavn, der er baseret på det lejerejede domæne (f.eks. `joe@contoso.cn`), og ikke brugernavnet `onmschina` (f.eks. `joe@contoso.onmschina.cn`). Domænenavnet fra brugernavnet bruges til DNS-omdirigering til den korrekte tjenesteforekomst.

#### <a name="configure-dns-encryption---windows"></a>Konfigurer DNS-kryptering – Windows

1. Hent RMS-id'et:

    1. Start PowerShell som administrator.
    2. Hvis AIPService-modulet ikke er installeret, skal du køre `Install-Module AipService`.
    3. Forbind til tjenesten ved hjælp af `Connect-AipService -environmentname azurechinacloud`.
    4. Kør `(Get-AipServiceConfiguration).RightsManagementServiceId` for at hente RMS-id'et.

2. Log på din DNS-udbyder, naviger til dns-indstillingerne for domænet, og tilføj derefter en ny SRV-post.

    - Tjeneste = `_rmsredir`
    - Protokol = `_http`
    - Navn = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (hvor GUID er RMS-id'et)
    - Prioritet, Vægt, Sekunder, TTL = standardværdier

3. Knyt det brugerdefinerede domæne til lejeren i [Azure Portal](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Dette tilføjer en post i DNS, som kan tage flere minutter at blive bekræftet, når du har føjet værdien til DNS-indstillingerne.

4. Log på Microsoft 365 Administration med de tilsvarende globale administratorlegitimationsoplysninger, `contoso.cn`og tilføj domænet (f.eks. ) til oprettelse af brugere. I bekræftelsesprocessen kan yderligere DNS-ændringer være påkrævet. Når bekræftelsen er fuldført, kan brugerne oprettes.

#### <a name="configure-dns-encryption---mac-ios-android"></a>Konfigurer DNS-kryptering – Mac, iOS, Android

Log på din DNS-udbyder, naviger til dns-indstillingerne for domænet, og tilføj derefter en ny SRV-post.

- Tjeneste = `_rmsdisco`
- Protokol = `_http`
- Navn = `_tcp`
- Mål = `api.aadrm.cn`
- Port = `80`
- Prioritet, Vægt, Sekunder, TTL = standardværdier


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>Trin 4: Installér og konfigurer AIP Unified-mærkatklienten

Download og installér AIP Unified Labeling-klienten fra [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018).

Du kan finde flere oplysninger under:

- [Dokumentation til AIP](/azure/information-protection/)
- [AIP-versionshistorik og supportpolitik](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [AIP-systemkrav](/azure/information-protection/requirements)
- [Hurtig start til AIP: Installér AIP-klienten](/azure/information-protection/quickstart-deploy-client)
- [AIP-administratorvejledning](/azure/information-protection/rms-client/clientv2-admin-guide)
- [AIP-brugervejledning](/azure/information-protection/rms-client/clientv2-user-guide)
- [Få mere at vide om Microsoft 365 følsomhedsmærkater](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>Trin 5: Konfigurer AIP-apps på Windows

AIP-apps på Windows skal bruge følgende registreringsdatabasenøgle for at pege dem på den korrekte nationale cloud til Azure China:

- Registreringsnode = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Navn = `CloudEnvType`
- Værdi = `6` (standard = 0)
- Type = `REG_DWORD`

> [!IMPORTANT]
> Sørg for, at du ikke sletter registreringsdatabasenøglen efter en fjernelse. Hvis nøglen er tom, forkert eller ikke-eksisterende, fungerer funktionaliteten som standardværdien (standardværdi = 0 for det kommercielle cloudmiljø). Hvis nøglen er tom eller forkert, føjes der også en udskriftsfejl til logfilen.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>Trin 6: Installér AIP-scanneren i det lokale miljø, og administrer job til indholdsscanning

Installér AIP-scanneren i det lokale miljø for at scanne dine netværks- og indholdsshares for følsomme data, og anvend klassificerings- og beskyttelsesmærkater som konfigureret i organisationens politik.

Når du konfigurerer og administrerer dine indholdsscanningsjob, skal du bruge følgende procedure i stedet for den [Azure Portal grænseflade](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only), der bruges af de kommercielle tilbud.

Du kan få flere oplysninger under [Hvad er Azure Information Protection unified labeling scanner?](/azure/information-protection/deploy-aip-scanner) og [Administrer kun dine indholdsscanningsjob ved hjælp af PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**Sådan installerer og konfigurerer du scanneren**:

1. Log på den Windows Server-computer, der skal køre scanneren. Brug en konto, der har lokale administratorrettigheder, og som har tilladelse til at skrive til SQL Server masterdatabase.

1. Start med PowerShell lukket. Hvis du tidligere har installeret AIP-klienten og -scanneren, skal du kontrollere, at tjenesten **AIPScanner** er stoppet.

1. Åbn en Windows PowerShell session med indstillingen **Kør som administrator**.

1. Kør [Install-AIPScanner-cmdlet'en](/powershell/module/azureinformationprotection/Install-AIPScanner), og angiv din SQL Server forekomst, hvor der skal oprettes en database til Azure Information Protection-scanneren, og et sigende navn til scannerklyngen.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Du kan bruge det samme klyngenavn i kommandoen [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) til at knytte flere scannernoder til den samme klynge. Brug af den samme klynge til flere scannernoder gør det muligt for flere scannere at arbejde sammen om at udføre dine scanninger.
    > 

1. Kontrollér, at tjenesten nu er installeret ved hjælp af **Administrative** **ToolsServices** > .

    Den installerede tjeneste hedder **Azure Information Protection Scanner** og er konfigureret til at køre ved hjælp af den scannertjenestekonto, du har oprettet.

1. Få et Azure-token, der skal bruges sammen med din scanner. Et Azure AD-token gør det muligt for scanneren at godkende til Azure Information Protection-tjenesten, hvilket gør det muligt for scanneren at køre ikke-interaktivt. 

    1. Åbn Azure Portal, og opret et Azure AD-program for at angive et adgangstoken til godkendelse. Du kan få flere oplysninger under [Sådan navngiver du filer, der ikke er interaktivt til Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > Når du opretter og konfigurerer Azure [AD-programmer til kommandoen Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) , viser ruden **Anmodnings-API-tilladelser** de **API'er, som min organisation bruger** , i stedet for fanen **Microsoft API'er** . Vælg de **API'er, som min organisation bruger** til, og vælg derefter **Azure Rights Management Services**. 
        >

    1. Log **på lokalt** for installationen fra computeren med Windows Server, hvis din scannertjenestekonto er tildelt den, skal du logge på med denne konto og starte en PowerShell-session. 
    
        Hvis din scannertjenestekonto ikke kan tildeles log **på lokalt** for installationen, skal du bruge parameteren *OnBehalfOf* med [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) som beskrevet i [Sådan navngiver du filer, der ikke er interaktivt for Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

    1. Kør [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), og angiv værdier, der er kopieret fra dit Azure AD-program:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Eksempel:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Scanneren har nu et token, der skal godkendes i Azure AD. Dette token er gyldigt i et år, to år eller aldrig i henhold til din konfiguration af **webapp/API-klienthemmeligheden** i Azure AD. Når tokenet udløber, skal du gentage denne procedure.

1. Kør [Set-AIPScannerConfiguration-cmdlet'en](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) for at indstille scanneren til at fungere i offlinetilstand. Køre:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Kør [Set-AIPScannerContentScanJob-cmdlet'en](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) for at oprette et standardjob til indholdsscanning.

    Den eneste påkrævede parameter i **Set-AIPScannerContentScanJob-cmdlet'en** er **Enforce**. Det kan dog være en god idé at definere andre indstillinger for dit indholdsscanningsjob på nuværende tidspunkt. Eksempel:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    Syntaksen ovenfor konfigurerer følgende indstillinger, mens du fortsætter konfigurationen:

    - Sørger for, at scanneren kører planlægning *manuelt*
    - Angiver de oplysningstyper, der skal registreres baseret på politikken for følsomhedsmærkater
    - Gennemtvinger *ikke* en politik for følsomhedsmærkater
    - Navngiver automatisk filer baseret på indhold ved hjælp af den standardmærkat, der er defineret for politikken for følsomhedsmærkater
    - Tillader *ikke* genmærkning af filer
    - Bevarer fildetaljer under scanning og automatisk mærkning, herunder *dato for ændring*, *seneste ændring* og *ændring af* værdier
    - Angiver scanneren til at udelade .msg- og .tmp-filer, når der køres
    - Angiver standardejeren til den konto, du vil bruge, når scanneren køres

1. Brug [cmdlet'en Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) til at definere de lagre, du vil scanne i dit indholdsscanningsjob. Kør f.eks.:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Brug en af følgende syntakser, afhængigt af den type lager, du tilføjer:

    - Til et netværksshare skal du bruge `\\Server\Folder`.
    - For et SharePoint bibliotek skal du bruge `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - For en lokal sti: `C:\Folder`
    - For en UNC-sti: `\\Server\Folder`

    > [!NOTE]
    > Jokertegn understøttes ikke, og WebDav-placeringer understøttes ikke.
    >
    > Hvis du vil ændre lageret senere, skal du bruge [Set-AIPScannerRepository-cmdlet'en](/powershell/module/azureinformationprotection/set-aipscannerrepository) i stedet for. 


Fortsæt med følgende trin efter behov:

- [Kør en registreringscyklus, og få vist rapporter for scanneren](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Brug PowerShell til at konfigurere scanneren til at anvende klassificering og beskyttelse](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Brug PowerShell til at konfigurere en DLP-politik med scanneren](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

I følgende tabel vises De PowerShell-cmdlet'er, der er relevante for installation af scanneren og administration af dine indholdsscanningsjob:

| Cmdlet | Beskrivelse |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Føjer et nyt lager til dit indholdsscanningsjob. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Returnerer oplysninger om din klynge. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Henter oplysninger om dit indholdsscanningsjob. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Henter oplysninger om lagre, der er defineret for dit indholdsscanningsjob. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Sletter dit indholdsscanningsjob. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Fjerner et lager fra dit indholdsscanningsjob. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Definerer indstillingerne for dit indholdsscanningsjob. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Definerer indstillinger for et eksisterende lager i dit indholdsscanningsjob. |
| | |

Du kan finde flere oplysninger under:

- [Hvad er Azure Information Protection Unified Labeling Scanner?](/azure/information-protection/deploy-aip-scanner)
- [Konfiguration og installation af Azure Information Protection (AIP) Unified Labeling Scanner](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [Administrer kun dine indholdsscanningsjob ved hjælp af PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
