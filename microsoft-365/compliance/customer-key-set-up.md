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
description: Få mere at vide om, hvordan du konfigurerer en kundenøgle Microsoft 365.
ms.openlocfilehash: f3d7da27e0c9a5e27f0c3e7bcc3adb48dad5d42c
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634509"
---
# <a name="set-up-customer-key"></a>Konfigurer kundenøgle

Med Kundenøgle kan du kontrollere organisationens krypteringsnøgler og derefter konfigurere Microsoft 365 til at bruge dem til at kryptere dine in resterede data i Microsofts datacentre. Med andre ord giver Kundenøgle kunderne mulighed for at tilføje et lag af kryptering, der tilhører dem, med deres nøgler.

Konfigurer Azure, før du kan bruge kundenøgle til Office 365. I denne artikel beskrives de trin, du skal følge for at oprette og konfigurere de nødvendige Azure-ressourcer, og derefter angives trinnene til konfiguration af kundenøgle i Office 365. Når du har konfigureret Azure, bestemmer du, hvilken politik og derfor, hvilke nøgler, der skal tildeles for at kryptere data på tværs af Microsoft 365 arbejdsbelastninger i organisationen. Du kan finde flere oplysninger om kundenøgle eller en generel oversigt under [Tjenestekryptering med kundenøgle i Office 365](customer-key-overview.md).
  
> [!IMPORTANT]
> Vi anbefaler på det kraftigste, at du følger de bedste fremgangsmåder i denne artikel. Disse kaldes for **TIP** og **VIGTIGT**. Kundenøgle giver dig kontrol over rodkrypteringsnøgler, hvis omfang kan være så stort som hele organisationen. Det betyder, at fejl, der er begået med disse nøgler, kan have en bred effekt og kan medføre afbrydelser af tjenesten eller uigenkaldelige tab af dine data.
  
## <a name="before-you-set-up-customer-key"></a>Før du konfigurerer en kundenøgle

Før du går i gang, skal du sikre dig, at du har de relevante Azure-abonnementer og -licenser til din organisation. Brug betalte Azure-abonnementer med enten en Enterprise Agreement eller en udbyder af skytjenester. Kreditkortbaserede betalinger accepteres ikke. Godkend og konfigurer kontobehovet til fakturering. Abonnementer, du har fået via gratis prøveversion, sponsorater, MSDN-abonnementer og dem under ældre support, er ikke berettigede.

Office 365 E5 tilbyder Microsoft 365 E5, Microsoft 365 E5 Overholdelse og Microsoft 365 E5 Information Protection & SKU'er til styring af kundenøgler. Avanceret overholdelse i Office 365 SKU er ikke længere tilgængelig til fremskaffelse af nye licenser. Eksisterende Avanceret overholdelse i Office 365-licenser understøttes fortsat.

Gennemgå Azure Key Vault dokumentationen for at forstå [begreber og procedurer i denne](/azure/key-vault/) artikel. Bliv også fortrolig med de udtryk, der bruges i Azure, f.eks [. Azure AD-lejer](/previous-versions/azure/azure-services/jj573650(v=azure.100)#what-is-an-azure-ad-tenant).
  
Hvis du har brug for mere support ud over dokumentationen, kan du kontakte Microsoft Consulting Services (MCS), Premier Field Engineering (PFE) eller en Microsoft-partner for at få hjælp. Hvis du vil give feedback på kundenøgler, herunder dokumentationen, kan du sende dine idéer, forslag og perspektiver til customerkeyfeedback@microsoft.com.
  
## <a name="overview-of-steps-to-set-up-customer-key"></a>Oversigt over trin til at konfigurere kundenøgle

Du kan konfigurere en kundenøgle ved at udføre disse opgaver i den angivne rækkefølge. Resten af denne artikel indeholder detaljerede instruktioner til hver opgave eller links til flere oplysninger om hvert trin i processen.
  
**I Azure og Microsoft FastTrack:**
  
Du kommer til at udføre de fleste af disse opgaver ved at oprette fjernforbindelse til Azure PowerShell. Du opnår de bedste resultater ved at bruge version 4.4.0 eller nyere Azure PowerShell.
  
- [Opret to nye Azure-abonnementer](#create-two-new-azure-subscriptions)

- [Indsend en anmodning om at aktivere kundenøgle til Office 365](#submit-a-request-to-activate-customer-key-for-office-365)
 
- [Registrer Azure-abonnementer for at bruge en obligatorisk opbevaringsperiode](#register-azure-subscriptions-to-use-a-mandatory-retention-period)

  Denne registreringsproces tager fem arbejdsdage at fuldføre.

- [Opret en Premium Azure-Key Vault hvert abonnement](#create-a-premium-azure-key-vault-in-each-subscription)

- [Tildele tilladelser til hver nøgleboks](#assign-permissions-to-each-key-vault)

- [Sørg for, at blød sletning er aktiveret på dine nøglebokse](#make-sure-soft-delete-is-enabled-on-your-key-vaults)

- [Føj en nøgle til hver nøgleboks ved enten at oprette eller importere en nøgle](#add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key)

- [Kontrollér dine nøglers genoprettelsesniveau](#check-the-recovery-level-of-your-keys)

- [Sikkerhedskopier Azure Key Vault](#back-up-azure-key-vault)

- [Valider Azure Key Vault konfigurationsindstillinger](#validate-azure-key-vault-configuration-settings)

- [Hent URI'en for hver Azure Key Vault nøgle](#obtain-the-uri-for-each-azure-key-vault-key)
  
## <a name="complete-tasks-in-azure-key-vault-and-microsoft-fasttrack-for-customer-key"></a>Udfør opgaver i Azure Key Vault og Microsoft FastTrack til kundenøgle

Fuldfør disse opgaver i Azure Key Vault. Du skal udføre disse trin for alle de løsningsprogrammer, du bruger med kundenøgle.
  
### <a name="create-two-new-azure-subscriptions"></a>Opret to nye Azure-abonnementer

Kundenøgle kræver to Azure-abonnementer. Som bedste fremgangsmåde anbefaler Microsoft, at du opretter nye Azure-abonnementer til brug med kundenøgle. Azure Key Vault-nøgler kan kun godkendes til programmer i den samme Azure Active Directory-lejer (Microsoft Azure Active Directory), skal du oprette de nye abonnementer ved hjælp af den samme Azure AD-lejer, der bruges sammen med din organisation, hvor ip'erne tildeles. For eksempel ved hjælp af din arbejds- eller skolekonto, der har globale administratorrettigheder i organisationen. Hvis du vil have en detaljeret vejledning [, skal du se Tilmelde dig Azure som en organisation](/azure/active-directory/fundamentals/sign-up-organization).
  
> [!IMPORTANT]
> Kundenøgle kræver to nøgler for hver datakrypteringspolitik (DEP). For at gøre dette skal du oprette to Azure-abonnementer. Som bedste fremgangsmåde anbefaler Microsoft, at du har separate medlemmer af organisationen konfigureret én nøgle i hvert abonnement. Du bør kun bruge disse Azure-abonnementer til at administrere krypteringsnøgler for Office 365. Dette beskytter din organisation i tilfælde af, at en af dine operatorer utilsigtet, bevidst eller ondsindet sletter eller på anden måde forkert administrerer de taster, som de har ansvaret for.

Der er ingen praktisk begrænsning på antallet af Azure-abonnementer, du kan oprette for organisationen. Hvis du følger disse bedste fremgangsmåder, minimeres effekten af menneskerfejl, mens det hjælper med at administrere de ressourcer, der bruges af Kundenøgle.
  
### <a name="submit-a-request-to-activate-customer-key-for-office-365"></a>Indsend en anmodning om at aktivere kundenøgle til Office 365

Når du har oprettet de to nye Azure-abonnementer, skal du indsende den relevante anmodning om kundenøgletilbud [Microsoft FastTrack portalen](https://fasttrack.microsoft.com/). De valg, du foretager i tilbudsformularen om de autoriserede angivelser i organisationen, er vigtige og nødvendige for fuldførelsen af registrering af kundenøgler. De officerer, der er i de valgte roller i din organisation, sikrer autenticiteten af enhver anmodning om at tilbagekalde og destruere alle nøgler, der bruges med en krypteringspolitik for kundenøgledata. Du skal udføre dette trin én gang for hver datanøgletype, som du vil bruge til din organisation.

**Teamet FastTrack ikke hjælpe med kundenøglen. Office 365 bruger blot portalen FastTrack til at give dig mulighed for at sende formularen og til at hjælpe os med at spore de relevante tilbud på kundenøgle. Når du har indsendt anmodningen FastTrack, skal du kontakte det tilsvarende kundenøgleteam for at starte onboardingprocessen.**
  
Hvis du vil sende et tilbud om at aktivere kundenøgle, skal du udføre disse trin:
  
1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at logge på [Microsoft FastTrack-portalen](https://fasttrack.microsoft.com/).

2. Når du er logget på, skal du vælge det relevante domæne.

3. For det valgte domæne skal du **vælge Anmod** om tjenester fra den øverste navigationslinje og gennemse listen over tilgængelige tilbud.

4. Vælg oplysningskortet for det tilbud, der gælder for dig:

   - **Flere Microsoft 365 arbejdsbelastninger: Vælg** **Hjælp til anmod om krypteringsnøgle til Microsoft 365** tilbud.

   - **Exchange Online og Skype for Business: Vælg** Hjælp til **krypteringsnøgle til Anmod om Exchange** tilbud.

   - **SharePoint Online-, OneDrive- Teams filer:** Vælg Hjælp til anmod om krypteringsnøgle **til SharePoint og OneDrive for Business** tilbud.

5. Når du har gennemset tilbudsoplysningerne, skal du **vælge Fortsæt til trin 2**.

6. Udfyld alle relevante oplysninger og ønskede oplysninger i tilbudsformularen. Vær særlig opmærksom på dine valg, som medarbejdere i din organisation, som du vil godkende, om at godkende den permanente og uigenkaldelige sletning af krypteringsnøgler og -data. Når du har udfyldt formularen, skal du vælge **Send**.

### <a name="register-azure-subscriptions-to-use-a-mandatory-retention-period"></a>Registrer Azure-abonnementer for at bruge en obligatorisk opbevaringsperiode

Det midlertidige eller permanente tab af rodkrypteringsnøgler kan være forstyrrende eller endda ødelagt i forbindelse med tjenestehandlingen og kan medføre tab af data. Derfor kræver de ressourcer, der bruges med kundenøgle, stærk beskyttelse. Alle Azure-ressourcer, der bruges sammen med mekanismerne til kundenøgletilbudsbeskyttelse ud over standardkonfigurationen. Du kan mærke eller registrere Azure-abonnementer i en *obligatorisk opbevaringsperiode*. En obligatorisk opbevaringsperiode forhindrer øjeblikkelig og uigenkaldelig annullering af dit Azure-abonnement. De trin, der kræves for at registrere Azure-abonnementer i en obligatorisk opbevaringsperiode, kræver samarbejde Microsoft 365 team. Denne proces tager fem arbejdsdage at gennemføre. Tidligere blev obligatorisk opbevaringsperiode nogle gange kaldt for "Annuller ikke".
  
Før du kontakter Microsoft 365-teamet, skal du udføre følgende trin for hvert Azure-abonnement, du bruger med kundenøgle. Sørg for, at du har [installeret Azure PowerShell Az-modulet](/powershell/azure/new-azureps-module-az), før du starter.
  
1. Log på med Azure PowerShell. Du kan finde en vejledning [under Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Kør cmdletten Register-AzProviderFeature registrere dine abonnementer for at bruge en obligatorisk opbevaringsperiode. Fuldfør denne handling for hvert abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzProviderFeature -FeatureName mandatoryRetentionPeriodEnabled -ProviderNamespace Microsoft.Resources
   ```

3. Kontakt Microsoft for at fuldføre processen.

   - For at aktivere kundenøgle til tildeling af DEP til individuelle Exchange Online postkasser skal du [kontakte exock@microsoft.com](mailto:exock@microsoft.com).

   - For at aktivere kundenøgle til tildeling af IP-adresser til at kryptere SharePoint Online- og OneDrive for Business-indhold (herunder Teams-filer) for alle lejerbrugere skal du [kontakte spock@microsoft.com](mailto:spock@microsoft.com).

   - For at aktivere kundenøgle til tildeling af IP-adresser til kryptering af indhold på tværs af flere Microsoft 365-arbejdsbelastninger (Exchange Online, Teams, Microsoft Information Protection) for alle lejerbrugere skal du [kontakte m365-ck@service.microsoft.com](mailto:m365-ck@service.microsoft.com).

   - Medtag følgende oplysninger i din mail:

     **Emne**: Kundenøgle til \<*Your tenant's fully qualified domain name*\>

     **Brødtekst**: Medtag de abonnements-Get-AzProviderFeature for hvert abonnement, du vil fuldføre den obligatoriske opbevaringsperiode for.

     Serviceaftale (SLA) for fuldførelse af denne proces er fem arbejdsdage, når Microsoft er blevet underrettet (og bekræftet), at du har registreret dine abonnementer til at bruge en obligatorisk opbevaringsperiode.

4. Når du modtager en meddelelse fra Microsoft om, at registreringen er fuldført, skal du bekræfte status for din registrering ved at køre kommandoen Get-AzProviderFeature som følger: Hvis det bekræftes, returnerer Get-AzProviderFeature en værdi af **Registreret** for **egenskaben Registreringstilstand** . Fuldfør dette trin for hvert abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Get-AzProviderFeature -ProviderNamespace Microsoft.Resources -FeatureName mandatoryRetentionPeriodEnabled
   ```

5. For at fuldføre processen skal du køre Register-AzResourceProvider kommando. Fuldfør dette trin for hvert abonnement.

   ```powershell
   Set-AzContext -SubscriptionId <SubscriptionId>
   Register-AzResourceProvider -ProviderNamespace Microsoft.KeyVault
   ```

### <a name="create-a-premium-azure-key-vault-in-each-subscription"></a>Opret en Premium Azure-Key Vault hvert abonnement

Trinnene til at oprette en nøgleboks er dokumenteret i [Introduktion med Azure Key Vault](/azure/key-vault/general/overview), som vejleder dig gennem installation og lancering af Azure PowerShell, oprettelse af forbindelse til dit Azure-abonnement, oprettelse af en ressourcegruppe og oprettelse af en nøgleboks i den pågældende ressourcegruppe.
  
Når du opretter en nøgleboks, skal du vælge en SKU: enten Standard eller Premium. Standard-SKU'en gør det muligt at beskytte Azure Key Vault-nøgler med software – der er ingen HSM-nøglebeskyttelse (Hardware Security Module), og Premium-SKU'en tillader brugen af HSMs til beskyttelse af Key Vault nøgler. Kundenøgle accepterer nøgle bokse, der bruger enten SKU, selvom Microsoft anbefaler på det kraftigste, at du kun bruger Premium SKU. Driftsomkostninger med nøgler af hver type er den samme, så den eneste forskel i omkostninger er omkostningerne pr. måned for hver HSM-beskyttet nøgle. Se [Key Vault for at](https://azure.microsoft.com/pricing/details/key-vault/) få mere at vide.
  
> [!IMPORTANT]
> Brug Premium-nøglebokse og HSM-beskyttede nøgler til produktionsdata, og brug kun standardnøgle bokse og nøgler til test og validering.
  
For hver Microsoft 365, som du vil bruge som kundenøgle, skal du oprette en nøgleboks i hvert af de to Azure-abonnementer, du har oprettet. Hvis du f.eks. vil gøre det muligt for kundenøgler at bruge DEP'er til Exchange Online-, SharePoint Online- og scenarier med flere arbejdsbelastninger, skal du oprette tre par nøglebokse.
  
Brug en navngivningskonvention til nøgle bokse, der afspejler den tilsigtede brug af de DATAP, som du skal knytte boksene til. Se afsnittet Bedste fremgangsmåder nedenfor for at få anbefalinger om navngivningskonventioner.
  
Opret et separat, parret sæt bokse for hver datakrypteringspolitik. For Exchange Online vælges omfanget af en datakrypteringspolitik af dig, når du tildeler politikken til postkassen. En postkasse kan kun have én politik tildelt, og du kan oprette op til 50 politikker. Omfanget af en SharePoint Online-politik omfatter alle data i en organisation på en geografisk placering eller _geo_. Omfanget af en politik med flere arbejdsbelastninger omfatter alle data på tværs af de understøttede arbejdsbelastninger for alle brugere.

Oprettelse af vigtige bokse kræver også oprettelse af Azure-ressourcegrupper, da nøglebokse har brug for lagerkapacitet (selvom mindre), og Key Vault-logføring også genererer gemte data, hvis de er aktiveret. Som bedste fremgangsmåde anbefaler Microsoft at bruge separate administratorer til at administrere hver ressourcegruppe med den administration, der er justeret med det sæt af administratorer, der administrerer alle relaterede kundenøgleressourcer.
  
> [!IMPORTANT]
> Du kan maksimere tilgængeligheden ved at placere dine nøglebokse i områder tæt på din Microsoft 365-tjeneste. Hvis f.eks. din Exchange Online-organisation er i Nordamerika, skal du placere dine nøglebokse i Nordamerika. Hvis din Exchange Online er i Europa, skal du placere dine nøglebokse i Europa.
>
> Brug et almindeligt præfiks til nøglebokse, og medtag en forkortelse for brugen af og omfanget af nøglenøglerne (f.eks. for Contoso SharePoint-tjenesten, hvor boksene er placeret i Nordamerika, er et muligt sæt navne Contoso-CK-SP-NA-VaultA1 og Contoso-CK-SP-NA-VaultA1 og Contoso-CK-SP-NA-VaultA2. Navne på bokse er globalt entydige strenge i Azure, så det kan være nødvendigt at prøve variationer af dine ønskede navne i tilfælde af, at de ønskede navne allerede er påstået af andre Azure-kunder. Fra og med juli 2017 kan navne på bokse ikke ændres, så den bedste fremgangsmåde er at have en skriftlig plan for konfigurationen og bruge en anden person til at bekræfte, at planen udføres korrekt.
>
> Hvis det er muligt, skal du oprette dine bokse i ikke-parrede områder. Parrede Azure-områder giver høj tilgængelighed på tværs af tjenestefejldomæner. Derfor kan regionale par tænkes som hinandens sikkerhedskopiområde. Det betyder, at en Azure-ressource, der er placeret i ét område, automatisk opnår fejltolerance gennem det parrede område. Valg af områder til to bokse, der bruges i en datakrypteringspolitik, hvor områder parres, betyder, at kun to områder af tilgængelighed er i brug i alt. De fleste områder har kun to områder, så det er endnu ikke muligt at vælge ikke-parrede områder. Hvis det er muligt, skal du vælge to ikke-parrede områder til de to bokse, der bruges med en politik for datakryptering. Denne fordel er på sammenlagt fire områder med tilgængelighed. Få mere at vide under [Forretningskontinuitet og genoprettelse efter nedbrud (BCDR): Azure Paired Regions](/azure/best-practices-availability-paired-regions) for en aktuel liste over regionale par.
  
### <a name="assign-permissions-to-each-key-vault"></a>Tildele tilladelser til hver nøgleboks

Du skal definere tre separate sæt af tilladelser for hver nøgleboks, afhængigt af din implementering. Du skal f.eks. definere ét sæt tilladelser for hver af følgende:
  
- **Vigtige administratorer af bokse** , der administrerer din organisations vigtige boks i det daglige. Disse opgaver omfatter sikkerhedskopiering, oprettelse, hent, import, liste og gendannelse.

  > [!IMPORTANT]
  > Det sæt tilladelser, der er tildelt administratorer af nøglebokse, omfatter ikke tilladelse til at slette nøgler. Dette er bevidst og en vigtig øvelse. Det er normalt ikke at slette krypteringsnøgler, da det vil ødelægge data permanent. Som bedste fremgangsmåde skal du ikke give denne tilladelse til nøgleadministratorer i bokse som standard. Du skal i stedet reservere dette til bidragydere til nøglevælgerne og kun tildele den til en administrator på kort tid, når man har forstået en klar forståelse af konsekvenserne.
  
  Hvis du vil tildele disse tilladelser til en bruger i organisationen, skal du logge på dit Azure-abonnement med Azure PowerShell. Du kan finde en vejledning [under Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

- Kør Set-AzKeyVaultAccessPolicy cmdlet'en for at tildele de nødvendige tilladelser.

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user> -PermissionsToKeys create,import,list,get,backup,restore
   ```

   Eksempel:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -UserPrincipalName alice@contoso.com -PermissionsToKeys create,import,list,get,backup,restore
   ```

- **Nøglebidragsydere** til boks, der kan ændre tilladelser på azure-Key Vault sig selv. Du skal ændre disse tilladelser, efterhånden som medarbejdere forlader eller tilmelder sig dit team. I en sjælden situation, hvor administratorerne af nøglevælgerne har brug for tilladelse til at slette eller gendanne en nøgle, skal du også ændre tilladelserne. Dette sæt af nøgleringsbidragere skal tildeles **rollen Bidragyder** i din nøgleboks. Du kan tildele denne rolle ved hjælp af Azure Resource Manager. Hvis du vil have en detaljeret vejledning[, skal du Role-Based Access Control til at administrere adgangen til dine Azure-abonnementsressourcer](/azure/active-directory/role-based-access-control-configure). Den administrator, der opretter et abonnement, har denne adgang implicit, og muligheden for at tildele andre administratorer rollen som bidragyder.

- **Tilladelser til Microsoft 365-programmer** til hver nøgleboks, du bruger til kundenøgle, skal du give wrapKey, unwrapKey og få tilladelser til den tilsvarende Microsoft 365-tjenesteinspektør. 

  Hvis du vil give tilladelse Microsoft 365 Service Principal, skal du køre **Set-AzKeyVaultAccessPolicy-cmdlet'en** ved hjælp af følgende syntaks:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
   ```

   Hvor:

   - *navnet på boksen* er navnet på den nøgleboks, du har oprettet.
   - Ud for Exchange Online og Skype for Business du *erstatte Office 365 app-id* med`00000002-0000-0ff1-ce00-000000000000`
   - For SharePoint Online-, OneDrive for Business og Teams skal du *Office 365 appID* med`00000003-0000-0ff1-ce00-000000000000`
   - For politikker for flere arbejdsbelastninger (Exchange, Teams, Microsoft Information Protection), der gælder for alle *lejerbrugere, skal du erstatte Office 365 appID* med`c066d759-24ae-40e7-a56f-027002b5d3e4`

  Eksempel: Indstilling af tilladelser for Exchange Online og Skype for Business:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
   ```

  Eksempel: Indstilling af tilladelser for SharePoint Online-, OneDrive for Business- og Teams filer:

   ```powershell
   Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1 -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
   ```

### <a name="make-sure-soft-delete-is-enabled-on-your-key-vaults"></a>Sørg for, at blød sletning er aktiveret på dine nøglebokse

Når du hurtigt kan gendanne dine nøgler, vil du være mindre tilbøjelig til at opleve et længere tjenestesvigt på grund af utilsigtede eller skadelige nøgler. Aktivér denne konfiguration, der kaldes blød sletning, før du kan bruge dine nøgler med kundenøgle. Hvis du aktiverer Blød sletning, kan du gendanne nøgler eller bokse inden for 90 dage efter sletningen uden at skulle gendanne dem fra sikkerhedskopien.
  
Hvis du vil aktivere Blød sletning i nøgle bokse, skal du udføre disse trin:
  
1. Log på dit Azure-abonnement med Windows PowerShell. Du kan finde en vejledning [under Log på med Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Kør [Cmdlet'en Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) . I dette eksempel *er boksnavnet* navnet på den nøgleboks, du aktiverer blød sletning for:

   ```powershell
   $v = Get-AzKeyVault -VaultName <vault name>
   $r = Get-AzResource -ResourceId $v.ResourceId
   $r.Properties | Add-Member -MemberType NoteProperty -Name enableSoftDelete -Value 'True'
   Set-AzResource -ResourceId $r.ResourceId -Properties $r.Properties
   ```

3. Bekræft, at blød sletning er konfigureret til nøgleboksen ved at køre **Cmdlet'en Get-AzKeyVault** . Hvis blød sletning er konfigureret korrekt til nøgleboksen, returnerer _egenskaben_ Ikke-permanent sletning værdien **Sand**:

   ```powershell
   Get-AzKeyVault -VaultName <vault name> | fl
   ```

### <a name="add-a-key-to-each-key-vault-either-by-creating-or-importing-a-key"></a>Føj en nøgle til hver nøgleboks ved enten at oprette eller importere en nøgle

Der er to måder at føje nøgler til en Azure Key Vault: du kan oprette en nøgle direkte i Key Vault, eller du kan importere en nøgle. Det er mindre kompliceret at oprette Key Vault direkte i en nøgle, men hvis du importerer en nøgle, får du samlet kontrol over, hvordan nøglen genereres. Brug RSA-tasterne. Azure Key Vault ikke ombrydning og opbrud med ellipseformede kurvetaster.
  
For at oprette en nøgle direkte i din nøgleboks skal du køre [Cmdlet'en Add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) på følgende måde:
  
```powershell
Add-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Destination <HSM|Software> -KeyOps wrapKey,unwrapKey
```

Hvor:

- *boksnavn* er navnet på den nøgleboks, hvor du vil oprette nøglen.

- *nøglenavn* er det navn, du vil give den nye nøgle.

  > [!TIP]
  > Navnenøgler med en lignende navngivningskonvention som beskrevet ovenfor for nøglebokse. På denne måde beskriver strengen sig selv i værktøjer, der kun viser nøglenavnet.
  
Hvis du vil beskytte nøglen med en HSM, skal du angive **HSM** som værdien af Destinationsparameteren,  ellers skal du angive **Software**.

Eksempel:
  
```powershell
Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps wrapKey,unwrapKey
```

Hvis du vil importere en nøgle direkte i din nøgleboks, skal du have et nCipher nShield Hardware Security Module.
  
Nogle organisationer foretrækker denne fremgangsmåde for at fastlægge oprindelsen af deres nøgler, og derefter giver denne metode også følgende citater:
  
- Værktøjerne, der bruges til import, omfatteration fra nCipher, at Nøgle Exchange Key (KEK), der bruges til at kryptere den nøgle, du genererer, ikke kan eksporteres og genereres i et ægte HSM, der er fremstillet af nCipher.

- Værktøjssættet omfatter bekræftelse fra nCipher af, at Azure Key Vault-sikkerhedsverden også blev genereret på en ægte HSM fremstillet af nCipher. Denne bekræftelse beviser, at Microsoft også bruger ægte nCipher-hardware.

Kontakt din sikkerhedsgruppe for at finde ud af, om ovenstående overvisninger er påkrævede. Hvis du vil have en detaljeret vejledning til at oprette en nøgle i det lokale miljø og importere den til din nøgleboks, skal du se Sådan genererer og overfører [du HSM-beskyttede nøgler til Azure Key Vault](/azure/key-vault/keys/hsm-protected-keys). Brug Azure-vejledningen til at oprette en nøgle i hver nøgleboks.
  
### <a name="check-the-recovery-level-of-your-keys"></a>Kontrollér dine nøglers genoprettelsesniveau

Microsoft 365 kræver, at Azure Key Vault-abonnementet er indstillet til Annuller ikke, og at de nøgler, der bruges af kundenøgle, er aktiveret til blød sletning. Du kan bekræfte dine abonnementsindstillinger ved at se på gendannelsesniveauet på dine nøgler.
  
Hvis du vil kontrollere genoprettelsesniveauet for en nøgle i Azure PowerShell, skal du køre Get-AzKeyVaultKey cmdlet'en på følgende måde:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name> -Name <key name>).Attributes
```

Hvis egenskaben _Genoprettelsesniveau_ returnerer noget andet end en værdi af **Genoprettelig+Beskyttetabonnement**, skal du sikre dig, at du har lagt abonnementet på listen Annuller ikke, og at du har blød sletning aktiveret på hver af dine nøglebokse.
  
### <a name="back-up-azure-key-vault"></a>Sikkerhedskopier Azure Key Vault

Udfør en sikkerhedskopiering og gem kopier af sikkerhedskopieringen, både online og offline, umiddelbart efter oprettelse eller ændring af en nøgle. Forbind ikke offlinekopier til noget netværk. Gem dem i stedet på et offline sted, f.eks. i en fysisk sikker eller kommerciel lagringsfacilitet. Mindst én kopi af sikkerhedskopien skal gemmes på en placering, der er tilgængelig, hvis der opstår nedbrud. Sikkerhedskopierings-blobs er den eneste måde at gendanne nøglemateriale på, Key Vault en nøgle ødelægges permanent eller på anden måde gengives ubrugelig. Nøgler, der er eksterne i forhold til Azure Key Vault og som importeres til Azure Key Vault, kvalificeres ikke som en sikkerhedskopi, da de metadata, der er nødvendige for, at kundenøglen kan bruge nøglen, ikke findes med den eksterne nøgle. Kun en sikkerhedskopi, der er taget fra Azure Key Vault, kan bruges til gendannelseshandlinger med Kundenøgle. Derfor skal du oprette en sikkerhedskopi af Azure Key Vault efter du har uploadet eller oprettet en nøgle.
  
Hvis du vil oprette en sikkerhedskopi af en Azure Key Vault-nøgle, skal du køre cmdlet'en [Backup-AzKeyVaultKey](/powershell/module/az.keyvault/backup-azkeyvaultkey) på følgende måde:

```powershell
Backup-AzKeyVaultKey -VaultName <vault name> -Name <key name>
-OutputFile <filename.backup>
```

Sørg for, at outputfilen bruger suffikset `.backup`.
  
Outputfilen, der kommer fra denne cmdlet, krypteres og kan ikke bruges uden for Azure Key Vault. Sikkerhedskopieringen kan kun gendannes til det Azure-abonnement, hvorfra sikkerhedskopieringen blev taget.
  
> [!TIP]
> For outputfilen skal du vælge en kombination af navn og nøgle for boksen. Dette gør filnavnet til en selvbeskrivelse. Det sikrer også, at navne på sikkerhedskopifiler ikke kolliderer.
  
Eksempel:
  
```powershell
Backup-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -OutputFile Contoso-CK-EX-NA-VaultA1-Key001-Backup-20170802.backup
```

### <a name="validate-azure-key-vault-configuration-settings"></a>Valider Azure Key Vault konfigurationsindstillinger

Validering før brug af nøgler i en dep er valgfrit, men anbefales kraftigt. Hvis du bruger trinene til at konfigurere andre nøgler og bokse end dem, der er beskrevet i denne artikel, skal du validere tilstand for dine Azure Key Vault-ressourcer, før du konfigurerer kundenøgle.
  
Sådan kontrollerer du, at dine nøgler har `get`, `wrapKey`og at `unwrapKey` handlinger er aktiveret:
  
Kør [Cmdlet'en Get-AzKeyVault](/powershell/module/az.keyvault/get-azkeyvault) på følgende måde:
  
```powershell
Get-AzKeyVault -VaultName <vault name>
```

I outputtet skal du se efter Access-politikken og efter Exchange Online identitet (GUID) eller SharePoint Online Identity (GUID) efter behov. Alle tre af ovenstående tilladelser skal vises under Tilladelser til nøgler.
  
Hvis konfigurationen af adgangspolitikken er forkert, skal du køre Set-AzKeyVaultAccessPolicy cmdlet'en på følgende måde:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName <vault name> -PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName <Office 365 appID>
```

For eksempel til Exchange Online og Skype for Business:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-EX-NA-VaultA1 
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000002-0000-0ff1-ce00-000000000000
```

Eksempelvis SharePoint Online og OneDrive for Business:
  
```powershell
Set-AzKeyVaultAccessPolicy -VaultName Contoso-CK-SP-NA-VaultA1
-PermissionsToKeys wrapKey,unwrapKey,get -ServicePrincipalName 00000003-0000-0ff1-ce00-000000000000
```

Hvis du vil bekræfte, at en udløbsdato ikke er angivet for dine nøgler, skal du køre cmdlet'en [Get-AzKeyVaultKey](/powershell/module/az.keyvault/get-azkeyvault) på følgende måde:
  
```powershell
Get-AzKeyVaultKey -VaultName <vault name>
```

Kundenøgle kan ikke bruge en udløbet nøgle. Handlinger, der forsøges med en udløbet nøgle, mislykkes og kan muligvis medføre nede på tjenesten. Vi anbefaler på det kraftigste, at de nøgler, der bruges sammen med kundenøgle, ikke har en udløbsdato. En udløbsdato, når den er angivet, kan ikke fjernes, men kan ændres til en anden dato. Hvis der skal bruges en nøgle, der har en udløbsdato angivet, skal du ændre udløbsværdien til 31-12-9999. Nøgler med en udløbsdato, der er angivet til en anden dato end 31-12-9999, passerer ikke Microsoft 365 validering.
  
Hvis du vil ændre en udløbsdato, der er blevet indstillet til en anden værdi end 31-12-9999, skal du køre cmdlet'en [Update-AzKeyVaultKey](/powershell/module/az.keyvault/update-azkeyvaultkey) på følgende måde:
  
```powershell
Update-AzKeyVaultKey -VaultName <vault name> -Name <key name> -Expires (Get-Date -Date "12/31/9999")
```

> [!CAUTION]
> Angiv ikke udløbsdatoer for de krypteringsnøgler, du bruger med kundenøgle.
  
### <a name="obtain-the-uri-for-each-azure-key-vault-key"></a>Hent URI'en for hver Azure Key Vault nøgle

Når du har konfigureret dine nøglebokse og tilføjet dine nøgler, skal du køre følgende kommando for at hente URI'en for nøglen i hver nøgleboks. Du skal bruge disse URI'er, når du opretter og tildeler hver deP senere, så gem disse oplysninger et sikkert sted. Kør denne kommando én gang for hver nøgleboks.
  
I Azure PowerShell:
  
```powershell
(Get-AzKeyVaultKey -VaultName <vault name>).Id
```

## <a name="next-steps"></a>Næste trin

Når du har gennemført trinnene i denne artikel, er du klar til at oprette og tildele DEP'er. Du kan finde en vejledning [under Administrer kundenøgle](customer-key-manage.md).

## <a name="related-articles"></a>Relaterede artikler

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Få mere at vide om tilgængelighedsnøglen](customer-key-availability-key-understand.md)

- [Tjenestekryptering](office-365-service-encryption.md)