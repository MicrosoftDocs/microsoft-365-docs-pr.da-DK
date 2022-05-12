---
title: Konfigurer kundenøgle
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Få mere at vide om, hvordan du konfigurerer kundenøgle.
ms.openlocfilehash: 42c89c23f823f5f4297f31308516888633a1c06c
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363164"
---
# <a name="set-up-customer-key"></a>Konfigurer kundenøgle

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Med Kundenøgle kan du styre din organisations krypteringsnøgler og derefter konfigurere Microsoft 365 til at bruge dem til at kryptere inaktive data i Microsofts datacentre. Med andre ord giver Kundenøgle kunderne mulighed for at tilføje et krypteringslag, der tilhører dem, med deres nøgler.

Konfigurer Azure, før du kan bruge Kundenøgle. I denne artikel beskrives de trin, du skal følge for at oprette og konfigurere de påkrævede Azure-ressourcer, og den indeholder derefter trinnene til konfiguration af kundenøgle. Når du har konfigureret Azure, bestemmer du, hvilken politik og derfor hvilke nøgler der skal tildeles for at kryptere data på tværs af forskellige Microsoft 365 arbejdsbelastninger i din organisation. Du kan få flere oplysninger om kundenøgle eller få en generel oversigt under [Tjenestekryptering med Microsoft Purview kundenøgle](customer-key-overview.md).
  
> [!IMPORTANT]
> Vi anbefaler på det kraftigste, at du følger de bedste fremgangsmåder i denne artikel. Disse kaldes **tip** og **VIGTIGT**. Kundenøgle giver dig kontrol over rodkrypteringsnøgler, hvis omfang kan være så stort som hele organisationen. Det betyder, at fejl, der er foretaget med disse nøgler, kan have en bred indvirkning og kan medføre afbrydelser i tjenesten eller uigenkaldeligt tab af dine data.
  
## <a name="before-you-set-up-customer-key"></a>Før du konfigurerer kundenøgle

Før du kommer i gang, skal du sikre dig, at du har de relevante Azure-abonnementer og M365/O365-licenser til din organisation. Du skal bruge betalte Azure-abonnementer. Abonnementer, du fik via gratis, prøveversion, sponsorater, MSDN-abonnementer og dem under ældre support, er ikke berettigede.

> [!IMPORTANT]
> Gyldige M365/O365-licenser, der tilbyder M365-kundenøgle, er:
>
> - Office 365 E5
> - Microsoft 365 E5
> - Microsoft 365 E5 Overholdelse
> - SKU'er for Microsoft 365 E5 Information Protection & styring
> - Microsoft 365 sikkerhed og overholdelse af angivne standarder for FLW

Eksisterende Avanceret overholdelse i Office 365 licenser understøttes fortsat.

Hvis du vil vide mere om begreberne og procedurerne i denne artikel, [skal du gennemse dokumentationen til Azure Key Vault](/azure/key-vault/). Bliv også fortrolig med de begreber, der bruges i Azure, f.eks. [Azure AD lejer](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
Hvis du har brug for mere support ud over dokumentationen, kan du kontakte Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) eller en Microsoft-partner for at få hjælp. Hvis du vil give feedback om Kundenøgle, herunder dokumentationen, skal du sende dine ideer, forslag og perspektiver for at customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Oversigt over trin til konfiguration af kundenøgle

Hvis du vil konfigurere kundenøgle, skal du udføre disse opgaver i den angivne rækkefølge. Resten af denne artikel indeholder detaljerede instruktioner til hver opgave eller links til flere oplysninger for hvert trin i processen.
  
**I Azure og Microsoft FastTrack:**
  
Du udfører de fleste af disse opgaver ved at oprette fjernforbindelse til Azure PowerShell. Du opnår det bedste resultat ved at bruge version 4.4.0 eller nyere af Azure PowerShell.
  
- [Opret to nye Azure-abonnementer](#create-two-new-azure-subscriptions)

- [Send en anmodning om at aktivere kundenøglen for Office 365](#submit-a-request-to-activate-customer-key-for-office-365)

- [Registrer Azure-abonnementer for at bruge en obligatorisk opbevaringsperiode](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Det tager fem arbejdsdage at fuldføre registreringsprocessen.
- [Kontakt det tilsvarende Microsoft-alias for at fortsætte med processen](#contact-the-corresponding-microsoft-alias-to-proceed-with-the-process)

- [Opret en Premium Azure-Key Vault i hvert abonnement](#create-a-premium-azure-key-vault-in-each-subscription)

- [Tildel tilladelser til hver key vault](#assign-permissions-to-each-key-vault)

- [Sørg for, at blød sletning er aktiveret i dine key vaults](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Føj en nøgle til hver key vault ved enten at oprette eller importere en nøgle](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Kontrollér udløbsdatoen for dine nøgler](#verify-expiration-date-of-your-keys)

- [Kontrollér genoprettelsesniveauet for dine nøgler](#check-the-recovery-level-of-your-keys)

- [Sikkerhedskopiér Azure Key Vault](#back-up-azure-key-vault)

- [Hent URI'en for hver Azure Key Vault-nøgle](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Udfør opgaver i Azure Key Vault og Microsoft FastTrack for Customer Key

Udfør disse opgaver i Azure Key Vault. Du skal fuldføre disse trin for alle de DEP'er, du bruger med Kundenøgle.
  
### <a name="create-two-new-azure-subscriptions"></a>Opret to nye Azure-abonnementer

Kundenøgle kræver to Azure-abonnementer. Som bedste praksis anbefaler Microsoft, at du opretter nye Azure-abonnementer til brug sammen med Customer Key. Azure Key Vault-nøgler kan kun godkendes for programmer i den samme lejer af typen Azure Active Directory (Microsoft Azure Active Directory), du skal oprette de nye abonnementer ved hjælp af den samme Azure AD lejer, der bruges sammen med din organisation, hvor DEP'erne tildeles. Det kan f.eks. være at bruge din arbejds- eller skolekonto, der har globale administratorrettigheder i din organisation. Du kan finde detaljerede trin under [Tilmeld dig Azure som en organisation](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> Kundenøglen kræver to nøgler til hver datakrypteringspolitik. Hvis du vil opnå dette, skal du oprette to Azure-abonnementer. Som bedste praksis anbefaler Microsoft, at du har separate medlemmer af din organisation, der konfigurerer én nøgle i hvert abonnement. Du bør kun bruge disse Azure-abonnementer til at administrere krypteringsnøgler til Office 365. Dette beskytter din organisation, hvis en af dine operatorer utilsigtet, bevidst eller ondsindet sletter eller på anden måde mismanagerer de nøgler, de er ansvarlige for.

Der er ingen praktisk grænse for antallet af Azure-abonnementer, som du kan oprette for din organisation. Hvis du følger disse bedste fremgangsmåder, minimeres indvirkningen af menneskelige fejl, samtidig med at du hjælper med at administrere de ressourcer, der bruges af kundenøglen.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Send en anmodning om at aktivere kundenøglen for Office 365

Når du har oprettet de to nye Azure-abonnementer, skal du sende den relevante anmodning om kundenøgletilbud på [Microsoft FastTrack portalen](https://fasttrack.microsoft.com/). De valg, du foretager i tilbudsformularen om de godkendte betegnelser i din organisation, er vigtige og nødvendige for at fuldføre registreringen af kundenøglen. Officererne i disse valgte roller i din organisation sikrer ægtheden af enhver anmodning om at tilbagekalde og ødelægge alle nøgler, der bruges sammen med en politik for kryptering af kundenøgledata. Du skal udføre dette trin én gang for hver kundenøgledetalstype, du vil bruge til din organisation.

**Det FastTrack team yder ikke hjælp til Kundenøgle. Office 365 bruger blot FastTrack-portalen til at sende formularen og til at hjælpe os med at spore de relevante tilbud på Kundenøgle. Når du har indsendt anmodningen om FastTrack, skal du kontakte det tilsvarende onboardingteam for kundenøglen for at starte onboardingprocessen.**
  
Hvis du vil indsende et tilbud om at aktivere Kundenøgle, skal du udføre disse trin:
  
1. Log på [Microsoft FastTrack-portalen](https://fasttrack.microsoft.com/) ved hjælp af en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation.

2. Når du er logget på, skal du vælge det relevante domæne.

3. For det valgte domæne skal du vælge **Anmod om tjenester** på den øverste navigationslinje og gennemse listen over tilgængelige tilbud.

4. Vælg oplysningskortet for det tilbud, der gælder for dig:

   - **Flere Microsoft 365 arbejdsbelastninger:** Vælg **hjælpen til anmodningskrypteringsnøglen til Microsoft 365** tilbud.

   - **Exchange Online og Skype for Business:** Vælg **hjælp til hjælp til anmodning om krypteringsnøgle til Exchange** tilbud.

   - **SharePoint Online-, OneDrive- og Teams-filer:** Vælg **hjælpen til anmodning om krypteringsnøgle for at få SharePoint og OneDrive for Business** tilbud.

5. Når du har gennemset oplysningerne om tilbuddet, skal du vælge **Fortsæt til trin 2**.

6. Udfyld alle relevante oplysninger og de ønskede oplysninger på tilbudsformularen. Vær især opmærksom på dine valg, hvilke medarbejdere i din organisation du vil give tilladelse til at godkende permanent og uigenkaldelig destruktion af krypteringsnøgler og data. Når du har udfyldt formularen, skal du vælge **Send**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Registrer Azure-abonnementer for at bruge en obligatorisk opbevaringsperiode

Det midlertidige eller permanente tab af rodkrypteringsnøgler kan være forstyrrende eller endda katastrofalt for servicehandlingen og kan medføre tab af data. Derfor kræver de ressourcer, der bruges sammen med Customer Key, stærk beskyttelse. Alle de Azure-ressourcer, der bruges sammen med Customer Key, tilbyder beskyttelsesmekanismer ud over standardkonfigurationen. Du kan tagge eller registrere Azure-abonnementer i en *obligatorisk opbevaringsperiode*. En obligatorisk opbevaringsperiode forhindrer øjeblikkelig og uigenkaldelig annullering af dit Azure-abonnement. De trin, der kræves for at registrere Azure-abonnementer i en obligatorisk opbevaringsperiode, kræver samarbejde med det Microsoft 365 team. Det tager fem arbejdsdage at fuldføre denne proces. Tidligere blev obligatorisk opbevaringsperiode nogle gange kaldt "Annuller ikke".
  
> [!IMPORTANT]
> Før du kontakter det Microsoft 365 team, skal du gøre følgende for **hvert** Azure-abonnement, du bruger med Customer Key. Sørg for, at [du har Azure PowerShell Az-modulet](/powershell/azure/new-azureps-module-az) installeret, før du starter.

1. Log på med Azure PowerShell. Du kan finde en vejledning under [Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Kør Register-AzProviderFeature-cmdlet'en for at registrere dine abonnementer for at bruge en obligatorisk opbevaringsperiode. Fuldfør denne handling for hvert abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

### <a name="contact-the-corresponding-microsoft-alias-to-proceed-with-the-process"></a>Kontakt det tilsvarende Microsoft-alias for at fortsætte med processen

>[!NOTE]
> Før du kontakter det tilsvarende Microsoft-alias, skal du kontrollere, at du har fuldført dine FastTrack anmodninger om M365-kundenøgle.

- Kontakt [exock@microsoft.com](mailto:exock@microsoft.com), hvis du vil aktivere kundenøgle for tildeling af deaktivering af forhindring af datasupport til individuelle Exchange Online postkasser.

- Kontakt [spock@microsoft.com](mailto:spock@microsoft.com) for at aktivere kundenøglen for tildeling af DEP'er for at kryptere SharePoint Online- og OneDrive for Business-indhold (herunder Teams filer) for alle lejerbrugere.

- Kontakt [m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com) for at aktivere kundenøglen for tildeling af dep'er for at kryptere indhold på tværs af flere Microsoft 365 arbejdsbelastninger (Exchange Online, Teams, Microsoft Purview Information Protection).

- Medtag følgende oplysninger i din mail:

     **Emne**: Kundenøgle til \<*Your tenant's fully qualified domain name*\>

     **Brødtekst**: Medtag FastTrack anmodnings-id'er og abonnements-id'er for **hver** af de kundenøgletjenester, du vil onboardes til. Disse abonnements-id'er er dem, du vil fuldføre den obligatoriske opbevaringsperiode og outputtet af Get-AzProviderFeature for hvert abonnement.

Serviceniveauaftalen (SLA) til fuldførelse af denne proces er fem arbejdsdage, når Microsoft har fået besked (og bekræftet), at du har registreret dine abonnementer til at bruge en obligatorisk opbevaringsperiode.

### <a name="verify-the-status-of-each-your-azure-subscriptions"></a>Bekræft status for hvert af dine Azure-abonnementer

Når du har modtaget en meddelelse fra Microsoft om, at registreringen er fuldført, skal du kontrollere status for registreringen ved at køre kommandoen Get-AzProviderFeature på følgende måde. Hvis den Get-AzProviderFeature kommando bekræftes, returnerer den en værdi af typen **Registreret** for egenskaben **Registreringstilstand** . Fuldfør dette trin for **hvert** abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

Kør kommandoen Register-AzResourceProvider for at fuldføre processen. Fuldfør dette trin for **hvert** abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   ```

   ```powershell
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

> [!TIP]
> Før du går videre, skal du sørge for, at 'RegistrationState' er angivet til 'Registreret' som på billedet nedenfor.
>
> ![Obligatorisk opbevaringsperiode](../media/MandatoryRetentionPeriod.png)

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Opret en Premium Azure-Key Vault i hvert abonnement

Trinnene til oprettelse af en key vault er dokumenteret i [Introduktion med Azure Key Vault](/azure/key-vault/general/overview), som hjælper dig med at installere og starte Azure PowerShell, oprette forbindelse til dit Azure-abonnement, oprette en ressourcegruppe og oprette en key vault i den pågældende ressourcegruppe.
  
Når du opretter en key vault, skal du vælge en SKU: enten Standard eller Premium. Standard-SKU'en gør det muligt at beskytte Azure Key Vault-nøgler med software – der er ingen HSM-nøglebeskyttelse (Hardware Security Module), og den Premium SKU gør det muligt at bruge HSM'er til beskyttelse af Key Vault nøgler. Customer Key accepterer key vaults, der bruger en af SKU'erne, selvom Microsoft på det kraftigste anbefaler, at du kun bruger den Premium SKU. Omkostningerne til handlinger med nøgler af begge typer er de samme, så den eneste forskel i omkostningerne er omkostningerne pr. måned for hver HSM-beskyttet nøgle. Se [Key Vault priser for at](https://azure.microsoft.com/pricing/details/key-vault/) få flere oplysninger.
  
> [!IMPORTANT]
> Brug de Premium SKU-nøglebokse og HSM-beskyttede nøgler til produktionsdata, og brug kun Standard SKU-nøglebokse og nøgler til test- og valideringsformål.
  
For hver Microsoft 365 tjeneste, som du skal bruge Customer Key til, skal du oprette en key vault i hvert af de to Azure-abonnementer, du har oprettet. Hvis du f.eks. vil gøre det muligt for Kundenøgle at bruge DEP'er til Exchange Online, SharePoint Online og scenarier med flere arbejdsbelastninger, skal du oprette tre par key vaults.
  
Brug en navngivningskonvention for key vaults, der afspejler den tilsigtede brug af programmet til forhindring af dataforbindelse, som du vil knytte vaults til. Se afsnittet Bedste fremgangsmåder nedenfor for at få anbefalinger til navngivningskonventioner.
  
Opret et separat parvis sæt vaults for hver datakrypteringspolitik. For Exchange Online vælges omfanget af en datakrypteringspolitik af dig, når du tildeler politikken til postkassen. En postkasse kan kun have én politik tildelt, og du kan oprette op til 50 politikker. Omfanget af en SharePoint Online-politik omfatter alle dataene i en organisation på en geografisk placering eller *geografisk* placering. Omfanget for en politik med flere arbejdsbelastninger omfatter alle data på tværs af de understøttede arbejdsbelastninger for alle brugere.

Oprettelsen af key vaults kræver også oprettelse af Azure-ressourcegrupper, da key vaults har brug for lagerkapacitet (selvom de er små) og Key Vault logføring, hvis den er aktiveret, genererer også gemte data. Som bedste praksis anbefaler Microsoft at bruge separate administratorer til at administrere hver ressourcegruppe med den administration, der er justeret i forhold til det sæt administratorer, der administrerer alle relaterede kundenøgleressourcer.
  
### <a name="assign-permissions-to-each-key-vault"></a>Tildel tilladelser til hver key vault

Du skal definere tre separate sæt tilladelser for hver key vault, afhængigt af implementeringen. Du skal f.eks. definere ét sæt tilladelser for hver af følgende:
  
- **Key Vault-administratorer** , der udfører den daglige administration af din key vault for din organisation. Disse opgaver omfatter sikkerhedskopiering, oprettelse, hentning, import, liste og gendannelse.

  > [!IMPORTANT]
  > Det sæt tilladelser, der er tildelt key vault-administratorer, indeholder ikke tilladelse til at slette nøgler. Dette er bevidst og en vigtig praksis. Sletning af krypteringsnøgler udføres normalt ikke, da det permanent ødelægger data. Som bedste praksis skal du ikke give denne tilladelse til key vault-administratorer som standard. Du kan i stedet reservere dette til key vault-bidragydere og kun tildele det til en administrator på kort sigt, når en klar forståelse af konsekvenserne er forstået.
  
  Hvis du vil tildele disse tilladelser til en bruger i din organisation, skal du logge på dit Azure-abonnement med Azure PowerShell. Du kan finde en vejledning under [Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

  - Kør Set-AzKeyVaultAccessPolicy-cmdlet'en for at tildele de nødvendige tilladelser.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Eksempel:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Key Vault-bidragydere**, der kan ændre tilladelser til selve Azure-Key Vault. Du skal ændre disse tilladelser, når medarbejdere forlader eller deltager i dit team. I den sjældne situation, hvor key vault-administratorer lovligt har brug for tilladelse til at slette eller gendanne en nøgle, skal du også ændre tilladelserne. Dette sæt af bidragydere til key vault skal tildeles rollen **Bidragyder** i din key vault. Du kan tildele denne rolle ved hjælp af Azure Resource Manager. Du kan finde detaljerede trin under [Brug Role-Based Access Control til at administrere adgang til dine Azure-abonnementsressourcer](/azure/active-directory/role-based-access-control-configure). Den administrator, der opretter et abonnement, har implicit denne adgang og muligheden for at tildele andre administratorer rollen Bidragyder.

- **Tilladelser til at Microsoft 365 programmer** for hver key vault, du bruger til Kundenøgle, skal du give wrapKey, unwrapKey og få tilladelser til den tilsvarende Microsoft 365 tjenesteprincipal.

  Hvis du vil give tilladelse til Microsoft 365 tjenesteprincipal, skal du køre Cmdlet'en **Set-AzKeyVaultAccessPolicy** ved hjælp af følgende syntaks:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Hvor:
   - *vault name* er navnet på den key vault, du har oprettet.
   - Erstat *Office 365 appID med for Exchange Online og Skype for Business*`00000002-0000-0ff1-ce00-000000000000`
   - I forbindelse med SharePoint Online-, OneDrive for Business- og Teams-filer skal *du erstatte Office 365 appID* med`00000003-0000-0ff1-ce00-000000000000`
   - I forbindelse med en politik med flere arbejdsbelastninger (Exchange, Teams, Microsoft Purview Information Protection), der gælder for alle lejerbrugere, skal du erstatte *Office 365 appID* med`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Eksempel: Angivelse af tilladelser for Exchange Online og Skype for Business:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Eksempel: Angivelse af tilladelser for SharePoint Online-, OneDrive for Business- og Teams-filer:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

  Bekræft *, at Get, wrapKey og unwrapKey* tildeles til **hver** key vault ved at køre *Get-AzKeyVault-cmdlet'en* .

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```  

> [!Tip]
> Før du går videre, skal du sørge for, at tilladelserne er konfigureret korrekt til key vault, og *at Tilladelser til nøgler* returnerer **wrapKey, unwrapKey, hent**.
> Sørg for at rette tilladelserne til den korrekte tjeneste, du onboarder til. Vist *navn* for hver tjeneste er angivet nedenfor:  
  >
  > - Exchange Online og Skype for Business: *Office 365 Exchange Online*
  > - SharePoint Online-, OneDrive- og Teams-filer: *Office 365 SharePoint Online*
  > - Flere Microsoft 365 arbejdsbelastninger: *M365DataAtRestEncryption*
  >  
  > Nedenstående kodestykke er f.eks. et eksempel på at sikre, at tilladelserne er konfigureret til M365DataAtRestEncryption. I nedenstående cmdlet med en samling med navnet *mmcexchangevault* vises følgende felter.
  >
  > ```powershell
  >   Get-AzKeyVault -VaultName mmcexchangevault | fl
  >   ```  
  >
  >
  > ![Krypteringsciffer til Exchange Online kundenøgle.](../media/KeyVaultPermissions.png)

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Sørg for, at blød sletning er aktiveret i dine key vaults

Når du hurtigt kan gendanne dine nøgler, er der mindre sandsynlighed for, at du oplever en længere tjenesteafbrydelse på grund af utilsigtet eller skadeligt slettede nøgler. Aktivér denne konfiguration, der kaldes Blød sletning, før du kan bruge dine nøgler med Kundenøgle. Aktivering af Blød sletning giver dig mulighed for at gendanne nøgler eller vaults inden for 90 dage efter sletning uden at skulle gendanne dem fra sikkerhedskopien.
  
Hvis du vil aktivere Blød sletning i dine key vaults, skal du udføre disse trin:
  
1. Log på dit Azure-abonnement med Windows PowerShell. Du kan finde en vejledning under [Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Kør Cmdlet'en [Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) . I dette eksempel er *vault-navnet* navnet på den key vault, som du aktiverer blød sletning for:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Bekræft blød sletning er konfigureret for key vault ved at køre **Get-AzKeyVault-cmdlet'en** . Hvis blød sletning er konfigureret korrekt for key vault, returnerer egenskaben *Blød sletning aktiveret* værdien **True**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

> [!TIP]
> Før du går videre, skal du sørge for, at 'Blød sletning er aktiveret?' er indstillet til 'Sand' som på billedet nedenfor.
>
> <img src="../media/SoftDeleteEnabled.png" alt="SoftDelete" width="400"/>

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Føj en nøgle til hver key vault ved enten at oprette eller importere en nøgle

Der er to måder at føje nøgler til et Azure-Key Vault på. Du kan oprette en nøgle direkte i Key Vault, eller du kan importere en nøgle. Oprettelse af en nøgle direkte i Key Vault er mindre kompliceret, men import af en nøgle giver total kontrol over, hvordan nøglen genereres. Brug RSA-nøglerne. Azure Key Vault understøtter ikke ombrydning og udpakning med elliptiske kurvetaster.

Du kan finde oplysninger om, hvordan du føjer en nøgle til hver vault, under [Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey).

 Du kan finde detaljerede trin til at oprette en nøgle i det lokale miljø og importere den i din key vault under [Sådan genererer og overfører du HSM-beskyttede nøgler til Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). Brug Azure-vejledningen til at oprette en nøgle i hver key vault.

### <a name="verify-expiration-date-of-your-keys"></a>Kontrollér udløbsdatoen for dine nøgler

Hvis du vil kontrollere, at der ikke er angivet en udløbsdato for dine nøgler, skal du køre Cmdlet'en [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) på følgende måde:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Kundenøglen kan ikke bruge en udløbet nøgle. Handlinger, der forsøges med en udløbet nøgle, mislykkes og medfører muligvis en tjenesteafbrydelse. Vi anbefaler på det kraftigste, at nøgler, der bruges sammen med kundenøglen, ikke har en udløbsdato. En udløbsdato, når den er angivet, kan ikke fjernes, men kan ændres til en anden dato. Hvis der skal bruges en nøgle, hvor en udløbsdato er angivet, skal du ændre udløbsværdien til 31-12-9999. Nøgler med en udløbsdato, der er angivet til en anden dato end 31-12-9999, vil ikke bestå Microsoft 365 validering.
  
Hvis du vil ændre en udløbsdato, der er angivet til en anden værdi end 31-12-9999, skal du køre [Update-AzKeyVaultKey-cmdlet'en](/powershell/module/az.keyvault/update-azkeyvaultkey) på følgende måde:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Angiv ikke udløbsdatoer for de krypteringsnøgler, du bruger sammen med kundenøglen.  

### <a name="check-the-recovery-level-of-your-keys"></a>Kontrollér genoprettelsesniveauet for dine nøgler

Microsoft 365 kræver, at Azure Key Vault-abonnementet er angivet til Annuller ikke, og at de nøgler, der bruges af kundenøglen, er aktiveret til blød sletning. Du kan bekræfte indstillingerne for dine abonnementer ved at se på genoprettelsesniveauet på dine nøgler.
  
Hvis du vil kontrollere genoprettelsesniveauet for en nøgle, skal du køre Get-AzKeyVaultKey-cmdlet'en på følgende måde i Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

> [!Tip]
> Før du går videre, skal du sørge for, at du har registreret funktionen *MandatoryRetentionPeriodEnabled* på abonnementet, hvis egenskaben *Recovery Level* returnerer andet end værdien **Recoverable+ProtectedSubscription**, og at du har aktiveret blød sletning for hver af dine key vaults.
>
>    <img src="../media/RecoveryLevel.png" alt="drawing" width="500"/>

### <a name="back-up-azure-key-vault"></a>Sikkerhedskopiér Azure Key Vault

Umiddelbart efter oprettelsen eller eventuelle ændringer af en nøgle skal du udføre en sikkerhedskopiering og gemme kopier af sikkerhedskopien, både online og offline.
Hvis du vil oprette en sikkerhedskopi af en Azure Key Vault-nøgle, skal du køre cmdlet'en [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey).

### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Hent URI'en for hver Azure Key Vault-nøgle

Når du har konfigureret dine key vaults og tilføjet dine nøgler, skal du køre følgende kommando for at hente URI'en for nøglen i hver key vault. Du skal bruge disse URI'er, når du opretter og tildeler hver enkelt dep senere, så gem disse oplysninger et sikkert sted. Kør denne kommando én gang for hver key vault.
  
I Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Næste trin

Når du har fuldført trinnene i denne artikel, er du klar til at oprette og tildele DEP'er. Du kan finde instruktioner under [Administrer kundenøgle](customer-key-manage.md).

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)

- [Tjenestekryptering](office-365-service-encryption.md)
