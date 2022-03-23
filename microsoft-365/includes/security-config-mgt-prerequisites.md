---
title: inkluder fil
description: inkluder fil
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 2d48c4066cc1cde102fc395d7c532d26ea2a4db0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594058"
---
## <a name="prerequisites"></a>Forudsætninger

Gennemgå følgende afsnit for at finde krav til Sikkerhedsadministration for Microsoft Defender til slutpunktsscenariet:

### <a name="environment"></a>Miljø

Når en enhed er onboardet til Microsoft Defender for Endpoint:


- Enheden er undersøge for en eksisterende Endpoint Manager, som er en MDM-registrering (mobile device management) til Intune
- Enheder uden Endpoint Manager-tilstedeværelse aktiverer funktionen Sikkerhedsadministration
- Der oprettes en tillid til Azure Active Directory, hvis der ikke allerede findes en
- Azure Active Directory tillid bruges til at kommunikere med Endpoint Manager (Intune) og hente politikker
- Politik, der Endpoint Manager automatisk på enheden af Microsoft Defender til Slutpunkt

### <a name="active-directory-requirements"></a>Active Directory-krav

Når en enhed, der er domænetilføjet, opretter en tillid Azure Active Directory, kaldes dette scenarie en *hybrid Azure Active Directory joinscenarie*. Sikkerhedsadministrationen for Microsoft Defender til Slutpunkt understøtter fuldt ud dette scenarie med følgende krav:

- Azure Active Directory Forbind (AAD Forbind) skal synkroniseres med den lejer, der bruges fra Microsoft Defender til slutpunkt
- Hybrid Azure Active Directory joinforbindelse skal konfigureres i dit miljø (enten via sammenslutning eller AAD Forbind synkronisering)
- AAD Forbind synkronisering skal medtage de enhedsobjekter, *der er omfattet* af synkronisering med Azure Active Directory (når det er nødvendigt til joinforbindelse)
- AAD Forbind for synkronisering skal ændres for Server 2012 R2 (når der kræves understøttelse af Server 2012 R2)
- Alle enheder skal registreres på Azure Active Directory lejer, der hoster Microsoft Defender til slutpunkt. Scenarier på tværs af lejere understøttes ikke. 

### <a name="connectivity-requirements"></a>Forbindelseskrav

Enheder skal have adgang til følgende slutpunkter:

- `enterpriseregistration.windows.net` - Til Azure AD-registrering.
- `login.microsoftonline.com` - Til Azure AD-registrering.
- `*.dm.microsoft.com` - Brugen af et jokertegn understøtter slutpunkter i skytjenesten, der bruges til registrering, indtjekning og rapportering, og som kan ændres i forbindelse med tjenesteskalaer.

### <a name="supported-platforms"></a>Understøttede platforme

Politikker for Microsoft Defender til sikkerhedsadministration af Slutpunkt understøttes for følgende enhedsplatforme:

- Windows 10 Pro/Enterprise (med [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Pro/Enterprise
- Windows Server 2012 R2 med [Microsoft Defender til Down-Level enheder](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 med [Microsoft Defender til Down-Level enheder](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (med [KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 (med [KB5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>Licenser og abonnementer

Hvis du vil bruge sikkerhedsadministration til Microsoft Defender til Slutpunkt, skal du bruge:

- Et abonnement, der giver licenser til Microsoft Defender til Slutpunkt, f.eks. Microsoft 365, eller en separat licens til kun Microsoft Defender til slutpunkt. Et abonnement, der giver Microsoft Defender for Endpoint-licenser, giver også din lejer adgang til slutpunktssikkerhedsnoden i Microsoft Endpoint Manager Administration.

  > [!NOTE]  
  > **Undtagelse**: Hvis du har adgang til Microsoft Defender for Endpoint som en del af en licens, der kun gælder For Microsoft Defender for Cloud (tidligere Azure Security Center), er Sikkerhedsstyring til Microsoft Defender til slutpunktsfunktionaliteten ikke tilgængelig.

Sikkerhedsnoden Slutpunkt er det sted, hvor du kan konfigurere og udrulle politikker for at administrere Microsoft Defender til Slutpunkt for dine enheder og overvåge enhedens status.

Du kan finde de seneste oplysninger om indstillinger [under Minimumskrav til Microsoft Defender til slutpunkt](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Architecture

Følgende diagram er en konceptuel gengivelse af sikkerhedsadministrationsløsningen Microsoft Defender til sikkerhedskonfiguration på Slutpunkt.

:::image type="content" alt-text="Konceptuel gengivelse af sikkerhedsadministrationsløsningen Microsoft Defender til slutpunktskonfiguration" source="../security/defender-endpoint/images/mde-architecture.png":::

1. Enheder indbygget i Microsoft Defender til Slutpunkt.

2. Der oprettes en tillid mellem hver enhed og Azure AD. Når en enhed har en eksisterende tillid, bruges den. Når enhederne ikke er registreret, oprettes der en ny tillid.

3. Enheder bruger deres Azure AD-identitet til at kommunikere med Endpoint Manager. Denne identitet gør det Microsoft Endpoint Manager at distribuere politikker, der er målrettet enhederne, når de tjekker ind.

4. Defender for Endpoint rapporterer politikkens status tilbage Endpoint Manager.

## <a name="which-solution-should-i-use"></a>Hvilken løsning skal jeg bruge?

Microsoft Endpoint Manager indeholder adskillige metoder og politiktyper til at administrere konfigurationen af Defender til slutpunkt på enheder.

Når dine behov for enhedsbeskyttelse strækker sig ud over administration af Defender til [](/mem/intune/protect/device-protect) Slutpunkt, kan du se Oversigt over enhedsbeskyttelse for at få mere at vide om yderligere funktioner, der leveres af Microsoft Endpoint Manager for at beskytte enheder, herunder enhedsoverholdelse *,* administrerede *apps*, *politikker for appbeskyttelse* og integration med overholdelse fra tredjeparter og partnere til *mobiltrusler*.

Den følgende tabel kan hjælpe dig med at forstå, hvilke politikker der kan konfigurere MDE-indstillinger, der understøttes af enheder, der administreres af de forskellige scenarier. Når du installerer en politik, der understøttes til både *MDE-sikkerhedskonfiguration* og *Microsoft Endpoint Manager*, kan en enkelt forekomst af denne politik behandles af enheder, der kun kører MDE, og enheder, der administreres af enten Intune eller Konfigurationsstyring.

| Microsoft Endpoint Manager  | Arbejdsbelastning | MDE-sikkerhedskonfiguration  |  Microsoft Endpoint Manager |
|----------------|----------------|-------------------|------------|
| Slutpunktssikkerhed    | Antivirus                   | ![Understøttet](../media/green-check.png)  | ![Understøttet](../media/green-check.png)  |
|                      | Diskkryptering   |           | ![Understøttet](../media/green-check.png)  |
|                      | Firewall (profil og regler)                | ![Understøttet](../media/green-check.png) | ![Understøttet](../media/green-check.png)  |
|                      | Registrering af slutpunkt og svar        | ![Understøttet](../media/green-check.png) | ![Understøttet](../media/green-check.png)  |
|                      | Reduktion af angrebsoverfladen    |           | ![Understøttet](../media/green-check.png)  |
|                      | Kontobeskyttelse       |       | ![Understøttet](../media/green-check.png)  |
|                      | Enhedsoverholdelse     |   | ![Understøttet](../media/green-check.png)  |
|                      | Betinget adgang    |   | ![Understøttet](../media/green-check.png)  |
|                      | Grundlinjer for sikkerhed      |   | ![Understøttet](../media/green-check.png)  |

**Sikkerhedspolitikker for slutpunkter** er diskrete grupper af indstillinger, der er beregnet til brug af sikkerhedsadministratorer, som fokuserer på at beskytte enheder i organisationen.

- **Antiviruspolitikker** administrerer de sikkerhedskonfigurationer, der findes i Microsoft Defender til slutpunkt. Se  [antiviruspolitik](/mem/intune/protect/endpoint-security-antivirus-policy) for slutpunktssikkerhed.
- **Politikker for reduktion af** angrebsoverfladen fokuserer på minimering af de steder, hvor din organisation er sårbar over for cybertrusler og angreb. Få mere at vide under [Oversigt](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) over reduktion af angrebsoverfladen i Windows dokumentation til trusselsbeskyttelse og politik for reduktion [af](/mem/intune/protect/endpoint-security-asr-policy) angrebsoverfladen for slutpunktssikkerhed.
- **Endpoint-registrering og** -svar (Slutpunktsregistrering og -svar) administrerer Defender for Endpoint-egenskaberne, der giver avancerede registreringer af angreb, der er næsten i realtid og kan handles på. Baseret på Slutpunktsregistrering og -svar sikkerhedsanalytikere kan prioritere vigtige beskeder effektivt, få overblik over det fulde omfang af en overtrædelse og reagere på dem for at afhjælpe trusler. Se [slutpunktsregistrering og -svar](/mem/intune/protect/endpoint-security-edr-policy) politik for slutpunktssikkerhed.
- **Firewallpolitikker** fokuserer på Defender-firewallen på dine enheder. Se [firewallpolitikken](/mem/intune/protect/endpoint-security-firewall-policy) for slutpunktssikkerhed.
- **Firewallregler** konfigurerer detaljerede regler for firewalls, herunder bestemte porte, protokoller, programmer og netværk. Se [firewallpolitikken](/mem/intune/protect/endpoint-security-firewall-policy) for slutpunktssikkerhed.
- **Sikkerheds oprindelige planer** omfatter forudkonfigurerede sikkerhedsindstillinger, der definerer Microsofts anbefalede sikkerhedsoverholdelse for forskellige produkter som Defender, Edge eller Windows. Standardanbefalinger er fra de relevante produktteams og gør det muligt hurtigt at installere den anbefalede sikre konfiguration på enheder. Selvom indstillingerne er forudkonfigureret i hver oprindelig plan, kan du oprette brugerdefinerede forekomster af dem for at opfylde organisationens sikkerhedsmæssige forventninger. Se [grundlinjer for sikkerhed](/mem/intune/protect/security-baselines) for Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Konfigurer din lejer til at understøtte Microsoft Defender for Endpoint Security Configuration Management

Hvis du vil understøtte Sikkerhedskonfiguration af Microsoft Defender til slutpunkt via Microsoft Endpoint Manager Administration, skal du aktivere kommunikation mellem dem fra hver konsol.

1. Log på [Microsoft 365 Defender portalen](https://security.microsoft.com/), og gå **til Indstillinger** >  **EndpointsConfiguration** >  **ManagementEnforcement-omfang** > , og aktivér platforme til styring af sikkerhedsindstillinger:

   :::image type="content" source="../media/enable-mde-settings-management-defender.png" alt-text="Aktivér Microsoft Defender for endpoint-indstillingsstyring i Defender-konsollen.":::

2. Sørg for, at de relevante brugere har tilladelse til at administrere slutpunktssikkerhedsindstillinger i Microsoft Endpoint Manager eller tildele disse tilladelser ved at konfigurere en rolle i Defender-portalen. Gå til **Indstillinger** >  **RolesAdd-element** > :

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Opret en ny rolle i Defender-portalen.":::

   > [!TIP]
   > Du kan ændre eksisterende roller og tilføje de nødvendige tilladelser kontra at oprette flere roller i Microsoft Defender til Slutpunkt

3. Når du konfigurerer rollen, skal du tilføje brugere og sørge for at **vælge Administrer sikkerhedsindstillinger for slutpunkt i Microsoft Endpoint Manager**:

   :::image type="content" source="../media/add-role.png" alt-text="Giv brugere tilladelse til at administrere indstillinger.":::

4. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Vælg **Endpoint securityMicrosoft** >  **Defender for Endpoint**, og indstil Tillad **Microsoft Defender for Endpoint at gennemtvinge Sikkerhedskonfigurationer for Slutpunkt (preview)** **til Til**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Aktivér Microsoft Defender til administration af slutpunktsindstillinger Microsoft Endpoint Manager Administration.":::

   Når du indstiller denne indstilling til *Til,* kvalificeres alle enheder i platformens omfang i Microsoft Defender til slutpunkt, der ikke administreres af Microsoft Endpoint Manager, til onboarding til Microsoft Defender til slutpunkt.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Onboard-enheder til Microsoft Defender til Slutpunkt

Microsoft Defender til Slutpunkt understøtter flere forskellige muligheder for onboard-enheder. Du kan finde den aktuelle [vejledning i Onboarding-værktøjer og -metoder Windows enheder i](/microsoft-365/security/defender-endpoint/security-config-management) dokumentationen til Defender til Slutpunkt.


> [!IMPORTANT]
> Når en enhed er blevet installeret med Microsoft Defender til Slutpunkt, skal den mærkes med **MDE-administration** , før den kan tilmeldes Sikkerhedsadministration til Microsoft Defender til Slutpunkt. Du kan finde flere oplysninger om enhedsmærkning i MDE under [*Opret og administrer enhedsmærker*](/microsoft-365/security/defender-endpoint/machine-tags).


## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Sameksistens med Microsoft Endpoint Configuration Manager
Når du Konfigurationsstyring, er den bedste vej til administration af sikkerhedspolitik at bruge den [Konfigurationsstyring lejeren vedhæfter](/mem/configmgr/tenant-attach/endpoint-security-get-started). I nogle miljøer kan det være en ide at bruge Sikkerhedsadministration for Microsoft Defender. Når du bruger sikkerhedsadministration til Microsoft Defender Konfigurationsstyring, skal slutpunktssikkerhedspolitik isoleres til et enkelt kontrolplan. Kontrol af politik via begge kanaler giver mulighed for konflikter og uønskede resultater.


## <a name="create-azure-ad-groups"></a>Opret Azure AD-grupper

Når enheder er blevet integreret i Defender til Slutpunkt, skal du oprette enhedsgrupper for at understøtte udrulning af politik for Microsoft Defender til Slutpunkt.

Sådan identificerer du enheder, der har tilmeldt sig Microsoft Defender til Slutpunkt, men ikke administreres af Intune eller Konfigurationsstyring:

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Gå til **EnhederAlle** >  enheder, og vælg derefter kolonnen **Administreret af** for at sortere visningen af enheder.

   Enheder, der onboarder Microsoft Defender til Slutpunkt og har registreret, men som ikke administreres af Intune, viser **Microsoft Defender til slutpunkt** i kolonnen *Administreret af* . Dette er de enheder, der kan modtage politik for sikkerhedsadministration for Microsoft Defender til slutpunkt.

   Du kan også finde to mærkater for enheder, der bruger sikkerhedsadministration til Microsoft Defender til slutpunkt:

   - **MDEJoined** – Føjet til enheder, der er forbundet til mappen som en del af dette scenarie.
   - **MDEManaged – Føjet** til enheder, der aktivt bruger sikkerhedsadministrationsscenariet. Dette mærke fjernes fra enheden, hvis Defender til Slutpunkt stopper med at administrere sikkerhedskonfigurationen.

Du kan oprette grupper til disse [enheder i Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) [eller fra Microsoft Endpoint Manager Administration](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>Implementer politik

Når du har oprettet en eller flere Azure AD-grupper, der indeholder enheder, der administreres af Microsoft Defender til Slutpunkt, kan du oprette og udrulle følgende politikker for Sikkerhedsadministration for Microsoft Defender til Slutpunkt for disse grupper:

- Antivirus
- Firewall
- Firewallregler
- Registrering af slutpunkt og svar

> [!TIP]
> Undgå at implementere flere politikker, der administrerer den samme indstilling på en enhed.
>
> Microsoft Endpoint Manager understøtter installation af flere forekomster af hver slutpunktssikkerhedspolitik på den samme enhed, hvor hver politikforekomst modtages separat på enheden. Derfor kan en enhed modtage separate konfigurationer for den samme indstilling fra forskellige politikker, hvilket resulterer i en konflikt. Nogle indstillinger (f.eks. antivirus udeladelse) flettes på klienten og anvendes korrekt.

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Gå til **Slutpunktssikkerhed** , og vælg derefter den type politik, du vil konfigurere, enten Antivirus eller Firewall, og vælg **derefter Opret politik**.

3. Angiv følgende egenskaber eller den valgte politiktype:

   - For Antiviruspolitik skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (preview)**
     - Profil: **Microsoft Defender Antivirus (forhåndsvisning)**

   - For Firewall-politik skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (preview)**
     - Profil: **Microsoft Defender Firewall (prøveversion)**

   - For politik for firewallregler skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (preview)**
     - Profil: **Regler for Microsoft Defender Firewall (prøveversion)**

   - For politikken Til registrering af slutpunkt og svar skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (preview)**
     - Profil: **Slutpunktsregistrering og -svar (forhåndsvisning)**

   >[!Note]
   > Disse profiler gælder for begge enheder, der kommunikerer via administration af mobilenheder (MDM – Mobile Device Management) med Microsoft Intune samt enheder, der kommunikerer ved hjælp af Microsoft Defender til slutpunktsklienten.
   >
   > Kontrollér, at du gennemser din målretning og dine grupper efter behov.

4. Vælg **Opret**.

5. Angiv et **navn og** en beskrivelse af profilen på siden Grundlæggende, og vælg derefter **Næste**.

6. På siden **Konfigurationsindstillinger** skal du vælge de indstillinger, du vil administrere med denne profil. Du kan få mere at vide om en indstilling ved at udvide dialogboksen med  oplysninger og vælge linket Få mere at vide for at få vist CSP-oplysningerne for indstillingen i den onlinedokumentation.

   Vælg Næste, når du er færdig med at konfigurere **indstillinger**.

7. På siden **Opgaver skal du** vælge de Azure AD-grupper, der modtager denne profil. Du kan finde flere oplysninger om tildeling af profiler under [Tildel bruger- og enhedsprofiler](/mem/intune/configuration/device-profile-assign).

   Vælg **Næste for** at fortsætte.

   > [!TIP]
   >
   > - Tildelingsfiltre understøttes ikke for sikkerhedskonfigurationsstyringsprofiler.
   > - Kun *enhedsobjekter* er gældende for Microsoft Defender til administration af slutpunkter. Målretning af brugere understøttes ikke.
   > - Politikker, der er konfigureret, gælder for både Microsoft Intune og Microsoft Defender for slutpunkt-klienter

8. Fuldfør processen for oprettelse af politikken, og **vælg derefter Opret på** siden **Gennemse + opret**. Den nye profil vises på listen, når du vælger politiktypen for den profil, du har oprettet.

9. Vent på, at politikken tildeles, og få vist et vellykket resultat, der indikerer, at politikken er blevet anvendt.

10. Du kan validere, om indstillingerne er anvendt lokalt på klienten ved hjælp af [kommandoværktøjet Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
