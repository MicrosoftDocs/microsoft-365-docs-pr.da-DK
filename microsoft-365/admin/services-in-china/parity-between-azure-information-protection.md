---
title: Azure Information Protection-support til Office 365 drevet af 21Vianet
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
description: Få mere at vide om Azure Information Protection (AIP) til Office 365 drevet af 21Vianet, og hvordan du konfigurerer den for kunder i Kina.
monikerRange: o365-21vianet
ms.openlocfilehash: 44681286bce5e16a08f7400a2dbb083288a6f3b7
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63588505"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>Azure Information Protection-support til Office 365 drevet af 21Vianet

I denne artikel beskrives forskellene mellem understøttelsen af Azure Information Protection (AIP) for Office 365, der drives af 21Vianet og kommercielle tilbud, samt specifikke instruktioner til konfiguration af AIP for&mdash; kunder i Kinaom, hvordan du installerer den lokale AIP-scanner og administrerer indholdsscanningsjob.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>Forskelle mellem AIP for Office 365 drevet af 21Vianet og kommercielle tilbud

Vores mål er at levere alle kommercielle funktioner og funktionalitet til kunder i Kina med vores AIP til Office 365, der drives af 21Vianet-tilbuddet, men vi mangler nogle funktioner, som vi gerne vil fremhæve.

Følgende liste indeholder de eksisterende huller mellem AIP for Office 365 drevet af 21Vianet og vores kommercielle tilbud pr. januar 2021:

- Active Directory Rights Management-tjenester (AD RMS) understøttes kun i Microsoft 365 Apps for enterprise (build 11731.10000 eller nyere). Office Professional Plus understøtter ikke AD RMS.

- Overførsel fra AD RMS til AIP er ikke tilgængelig i øjeblikket.
  
- Deling af beskyttede mails med brugere i den kommercielle sky understøttes.
  
- Deling af dokumenter og vedhæftede filer i mails med brugere i den kommercielle sky er ikke tilgængelig i øjeblikket. Dette omfatter Office 365 drevet af 21Vianet-brugere i den kommercielle sky, ikke-Office 365, der drives af 21Vianet-brugere i den kommercielle sky, og brugere med en RMS for enkeltpersoner-licens.
  
- IRM med SharePoint (IRM-beskyttede websteder og biblioteker) er ikke tilgængelig i øjeblikket.
  
- Mobilenhedsudvidelsen til AD RMS er ikke tilgængelig i øjeblikket.

- [Mobile-fremviseren](/azure/information-protection/rms-client/mobile-app-faq) understøttes ikke af Azure China 21Vianet.

- AIP-området på Azure-portalen er ikke tilgængeligt for kunder i Kina. Brug [PowerShell-kommandoer i](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) stedet for at udføre handlinger i portalen, f.eks. administration og kørsel af dine indholdsscanningsjob.

- AIP-slutpunkter i Office 365 drevet af 21Vianet er forskellige fra de slutpunkter, der kræves til andre skytjenester. Netværksforbindelse fra klienter til følgende slutpunkter er påkrævet:
    - Download etiket- og etiketpolitikker: `*.protection.partner.outlook.cn`
    - Azure Rights Management-tjeneste: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Konfigurer AIP for kunder i Kina

Sådan konfigurerer du AIP for kunder i Kina:
1. [Aktivér Rettighedsstyring for lejeren](#step-1-enable-rights-management-for-the-tenant).

1. [Tilføj Microsoft Information Protection-synkroniseringstjenestes hovedstol](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [Konfigurer DNS-kryptering](#step-3-configure-dns-encryption).

1. [Installér og konfigurer den samlede AIP-etiketklient](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Konfigurer AIP-apps på Windows](#step-5-configure-aip-apps-on-windows).

1. [Installér den lokale AIP-scanner, og administrer indholdsscanningsjob.](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>Trin 1: Aktivér Rights Management for lejeren

Hvis krypteringen skal fungere korrekt, skal RMS være aktiveret for lejeren.

1. Kontrollér, om RMS er aktiveret:

    1. Start PowerShell som administrator.
    2. Hvis AIPService-modulet ikke er installeret, skal du køre `Install-Module AipService`.
    3. Importér modulet ved hjælp af `Import-Module AipService`.
    4. Forbind til tjenesten ved hjælp af `Connect-AipService -environmentname azurechinacloud`.
    5. Kør `(Get-AipServiceConfiguration).FunctionalState` og kontrollér, om tilstanden er `Enabled`.

2. Hvis funktionstilstanden er `Disabled`, skal du køre `Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>Trin 2: Tilføj Microsoft Information Protection synkroniseringstjenestes hovedstol

**Hovedstolen Microsoft Information Protection synkroniseringstjenesten** er ikke tilgængelig i Azure China-lejere som standard og er påkrævet til Azure Information Protection. Opret denne tjeneste hovedstol manuelt via Azure Az PowerShell-modulet.

1. Hvis du ikke har Azure Az-modulet installeret, skal du installere det eller bruge en ressource, hvor Azure Az-modulet er forudinstalleret, f.eks [. Azure Cloud Shell](/azure/cloud-shell/overview). Du kan finde flere oplysninger [under Installere Azure Az PowerShell-modulet](/powershell/azure/install-az-ps).

1. Forbind til tjenesten ved hjælp af [Forbind-AzAccount](/powershell/module/az.accounts/Connect-AzAccount) cmdlet og `azurechinacloud` miljønavnet:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. Opret **hovedstolen Microsoft Information Protection-synkroniseringstjenesten** manuelt ved hjælp af cmdlet'en `870c4f2e-85b6-4d43-bdda-6ed9a579b725` [New-AzADServicePrincipal og program-id](/powershell/module/az.resources/new-azadserviceprincipal) Microsoft Information Protection synkroniseringstjenesten:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Når du har tilføjet tjenesteinspektøren, skal du tilføje de relevante tilladelser, der er påkrævet for tjenesten.

### <a name="step-3-configure-dns-encryption"></a>Trin 3: Konfigurer DNS-kryptering

For at kryptering kan fungere korrekt, Office klientprogrammer oprette forbindelse til forekomsten af Kina af tjenesten og starte derfra. For at omdirigere klientprogrammer til den rigtige tjenesteforekomst skal lejeradministratoren konfigurere en DNS SRV-post med oplysninger om Azure RMS-URL-adressen. Uden DNS SRV-posten vil klientprogrammet som standard forsøge at oprette forbindelse til den offentlige skyforekomst og vil mislykkes.

Det antages desuden, `joe@contoso.cn`at brugerne logger på med et brugernavn, der er baseret på det lejerejede domæne (f.eks. ) `onmschina` og ikke brugernavnet (f.eks. `joe@contoso.onmschina.cn`). Domænenavnet fra brugernavnet bruges til DNS-omdirigering til den korrekte tjenesteforekomst.

#### <a name="configure-dns-encryption---windows"></a>Konfigurere DNS-kryptering – Windows

1. Hent RMS-id'et:

    1. Start PowerShell som administrator.
    2. Hvis AIPService-modulet ikke er installeret, skal du køre `Install-Module AipService`.
    3. Forbind til tjenesten ved hjælp af `Connect-AipService -environmentname azurechinacloud`.
    4. Kør `(Get-AipServiceConfiguration).RightsManagementServiceId` for at få RMS-id'et.

2. Log på din DNS-udbyder, gå til DNS-indstillingerne for domænet, og tilføj derefter en ny SRV-post.

    - Tjeneste = `_rmsredir`
    - Protocol = `_http`
    - Navn = `_tcp`
    - Target = `[GUID].rms.aadrm.cn` (hvor GUID er RMS-id'et)
    - Prioritet, Vægt, Sekunder, TTL = standardværdier

3. Knyt det brugerdefinerede domæne til lejeren i [Azure-portalen](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains). Dette tilføjer en post i DNS, hvilket kan tage flere minutter at blive bekræftet, efter at du har føjet værdien til DNS-indstillingerne.

4. Log på domænet Microsoft 365 Administration de tilsvarende globale legitimationsoplysninger, og tilføj domænet (f.eks. `contoso.cn`) til oprettelse af brugere. I bekræftelsesprocessen kan yderligere DNS-ændringer være nødvendige. Når bekræftelsen er udført, kan brugerne oprettes.

#### <a name="configure-dns-encryption---mac-ios-android"></a>Konfigurere DNS-kryptering - Mac, iOS, Android

Log på din DNS-udbyder, gå til DNS-indstillingerne for domænet, og tilføj derefter en ny SRV-post.

- Tjeneste = `_rmsdisco`
- Protocol = `_http`
- Navn = `_tcp`
- Target = `api.aadrm.cn`
- Port = `80`
- Prioritet, Vægt, Sekunder, TTL = standardværdier


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>Trin 4: Installér og konfigurer den samlede AIP-etiketklient

Download og installér den samlede AIP-etiketklient fra [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018).

Du kan finde flere oplysninger under:

- [AIP-dokumentation](/azure/information-protection/)
- [AIP-versionshistorik og supportpolitik](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [Systemkrav for AIP](/azure/information-protection/requirements)
- [Hurtig start til AIP: Installere AIP-klienten](/azure/information-protection/quickstart-deploy-client)
- [AIP-administratorvejledning](/azure/information-protection/rms-client/clientv2-admin-guide)
- [AIP-brugervejledning](/azure/information-protection/rms-client/clientv2-user-guide)
- [Få mere at vide Microsoft 365 følsomhedsmærkater](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>Trin 5: Konfigurer AIP-apps på Windows

AIP-apps på Windows skal bruge følgende registreringsdatabasenøgle for at kunne pege dem på den korrekte suveræne sky til Azure Kina:

- Node i registreringsdatabasen = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Navn = `CloudEnvType`
- Værdi = `6` (standard = 0)
- Skriv = `REG_DWORD`

> [!IMPORTANT]
> Sørg for, at du ikke sletter registreringsdatabasenøglen efter fjernelsen. Hvis nøglen er tom, forkert eller ikke-eksisterende, fungerer funktionaliteten som standardværdien (standardværdi = 0 for den kommercielle sky). Hvis nøglen er tom eller forkert, tilføjes der også en udskriftsfejl i logfilen.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>Trin 6: Installér den lokale AIP-scanner, og administrer indholdsscanningsjob

Installér den lokale AIP-scanner for at scanne dit netværk og indholdsshares for følsomme data, og anvend klassificerings- og beskyttelsesetiketter som konfigureret i organisationens politik.

Når du konfigurerer og administrerer dine indholdsscanningsjob, skal du bruge følgende fremgangsmåde i stedet for [grænsefladen for Azure-portalen](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) , der bruges af de kommercielle tilbud.

Du kan få mere at vide [under Hvad er Azure Information Protection unified labeling scanner?](/azure/information-protection/deploy-aip-scanner) og [Administrer dine indholdsscanningsjob kun ved hjælp af PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**Sådan installerer og konfigurerer du din scanner**:

1. Log på den Windows Server-computer, der kører scanneren. Brug en konto, der har lokale administratorrettigheder, og som har tilladelse til at skrive til SQL Server hoveddatabasen.

1. Start med PowerShell lukket. Hvis du tidligere har installeret AIP-klienten og -scanneren, skal du sørge for, at **AIPScanner-tjenesten** stoppes.

1. Åbn en Windows PowerShell med **indstillingen Kør som** administrator.

1. Kør [Install-AIPScanner-cmdlet'en](/powershell/module/azureinformationprotection/Install-AIPScanner), og angiv din SQL Server-forekomst, hvor der skal oprettes en database til Azure Information Protection-scanneren, og et beskrivende navn til din scannerklynge.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Du kan bruge det samme klyngenavn i [kommandoen Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) til at knytte flere scannernoder til den samme klynge. Hvis du bruger den samme klynge til flere scannernoder, kan flere scannere arbejde sammen om at udføre dine scanninger.
    > 

1. Kontrollér, at tjenesten nu er installeret, ved hjælp **af Administrative** **ToolsServices** > .

    Den installerede tjeneste hedder **Azure Information Protection Scanner og** er konfigureret til at køre ved hjælp af den scannertjenestekonto, du har oprettet.

1. Få et Azure-token til brug med din scanner. Med et Azure AD-token kan scanneren godkende til tjenesten Azure Information Protection, så scanneren kan køres ikke-interaktivt. 

    1. Åbn Azure-portalen, og opret et Azure AD-program for at angive et adgangstoken til godkendelse. Du kan få mere at vide [under Sådan mærker du filer, der ikke er interaktive, for Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > Når du opretter og konfigurerer Azure [AD-programmer for kommandoen Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), viser ruden Anmod om **API-tilladelser** fanen API'er, som min organisation bruger i stedet for fanen **Microsoft API'er**. Vælg de **API'er, som min organisation** bruger til at vælge **Azure Rights Management Services**. 
        >

    1. Hvis din scannertjenestekonto på Windows Server-computer har fået tildelt Log på lokalt til installationen, skal du logge på med denne konto og starte en PowerShell-session. 
    
        Hvis din scannertjenestekonto ikke kan tildeles  Log på lokalt til installationen, skal du bruge *parameteren OnBehalfOf* med [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication), som beskrevet i Sådan etikette filer, der ikke [er interaktive for Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).

    1. Kør [Set-AIPAuthentication, der](/powershell/module/azureinformationprotection/set-aipauthentication) angiver værdier, der er kopieret fra dit Azure AD-program:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Eksempel:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Scanneren har nu en token til godkendelse til Azure AD. Dette token er gyldigt i et år, to år eller aldrig, i henhold til din konfiguration af **webappen/** API-klienthemmelighed i Azure AD. Når tokenet udløber, skal du gentage denne procedure.

1. Kør [Set-AIPScannerConfiguration-cmdlet'en](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) for at indstille scanneren til at fungere i offlinetilstand. Kør:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Kør [Set-AIPScannerContentScanJob-cmdlet'en](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) for at oprette et standard scanningsjob for indhold.

    Den eneste påkrævede parameter i **Set-AIPScannerContentScanJob-cmdlet'en** er **Enforce**. Det kan dog være en ide at definere andre indstillinger for dit indholdsscanningsjob på nuværende tidspunkt. Eksempel:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    Syntaksen ovenfor konfigurerer følgende indstillinger, mens du fortsætter konfigurationen:

    - Holder planlægningen af scannerkørslen *manuel*
    - Angiver de oplysningstyper, der skal opdages, baseret på følsomhedsmærkatpolitikken
    - *Gennemtvinger ikke* en følsomhedsmærkatpolitik
    - Mærkater automatisk filer baseret på indhold ved hjælp af den standardetiket, der er defineret for følsomhedsetiketpolitikken
    - Tillader *ikke* , at filer navnmærkes igen
    - Bevarer fildetaljer under scanning og automatisk mærkat, herunder *dato for ændring*, *senest* ændret *og ændret* af værdier
    - Indstiller scanneren til at udelade .msg- og .tmp-filer, når den kører
    - Angiver standardejeren til den konto, du vil bruge, når du kører scanneren

1. Brug [Add-AIPScannerRepository-cmdlet'en](/powershell/module/azureinformationprotection/add-aipscannerrepository) til at definere de lagre, du vil scanne i dit indholdsscannerjob. Kør f.eks.:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Brug en af følgende syntakser, afhængigt af hvilken type lager du tilføjer:

    - Hvis du vil have et netværksshare, skal du bruge `\\Server\Folder`.
    - Hvis du vil SharePoint et bibliotek, skal du bruge `http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - For en lokal sti: `C:\Folder`
    - For en UNC-sti: `\\Server\Folder`

    > [!NOTE]
    > Jokertegn understøttes ikke, og WebDav-placeringer understøttes ikke.
    >
    > Hvis du vil ændre lageret senere, skal du bruge [den Set-AIPScannerRepository-cmdlet](/powershell/module/azureinformationprotection/set-aipscannerrepository) i stedet. 


Fortsæt med følgende trin efter behov:

- [Kør en registreringscyklus, og få vist rapporter for scanneren](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Brug PowerShell til at konfigurere scanneren til at anvende klassificering og beskyttelse](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Brug PowerShell til at konfigurere en DLP-politik med scanneren](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

I følgende tabel vises PowerShell-cmdlet'er, der er relevante for installation af scanneren og administration af dine indholdsscanningsjob:

| Cmdlet | Beskrivelse |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | Føjer et nyt lager til dit indholdsscanningsjob. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Returnerer oplysninger om din klynge. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | Henter oplysninger om dit indholdsscanningsjob. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | Henter oplysninger om lagre, der er defineret for dit indholdsscanningsjob. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | Sletter dit indholdsscanningsjob. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | Fjerner et lager fra dit indholdsscanningsjob. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | Definerer indstillinger for dit indholdsscanningsjob. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | Definerer indstillinger for et eksisterende lager i dit indholdsscanningsjob. |
| | |

Du kan finde flere oplysninger under:

- [Hvad er den samlede Azure Information Protection-etiketscanner?](/azure/information-protection/deploy-aip-scanner)
- [Konfiguration og installation af den samlede Azure Information Protection -scanner (AIP)](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [Administrer dine indholdsscanningsjob kun ved hjælp af PowerShell](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
