---
title: inkluder fil
description: inkluder fil
author: mjcaparas
ms.service: microsoft-365-enterprise
ms.author: macapara
ms.openlocfilehash: 31008df3e43c99f3a97dad3dce037b96e3b0c4b5
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66116221"
---
## <a name="prerequisites"></a>Forudsætninger

Gennemse følgende afsnit for at se kravene til Sikkerhedsadministration for Microsoft Defender for Endpoint scenarie:

### <a name="environment"></a>Miljø

Når en enhed onboarder til Microsoft Defender for Endpoint:


- Enheden undersøges for eksisterende Endpoint Manager tilstedeværelse, som er en MDM-tilmelding (Mobile Device Management) til Intune
- Enheder uden en Endpoint Manager tilstedeværelse aktiverer funktionen Sikkerhedsadministration
- Der oprettes et tillidsforhold med Azure Active Directory, hvis der ikke allerede findes et
- Azure Active Directory tillid bruges til at kommunikere med Endpoint Manager (Intune) og hente politikker
- Politik, der hentes fra Endpoint Manager gennemtvinges på enheden af Microsoft Defender for Endpoint

### <a name="active-directory-requirements"></a>Active Directory-krav

Når en enhed, der er domænetilsluttet, opretter et tillidsforhold til Azure Active Directory, kaldes dette scenarie et *Hybrid-Azure Active Directory Join-scenarie*. Sikkerhedsadministrationen for Microsoft Defender for Endpoint understøtter fuldt ud dette scenarie med følgende krav:

- Azure Active Directory Forbind (AAD-Forbind) skal synkroniseres med den lejer, der bruges fra Microsoft Defender for Endpoint
- Hybrid Azure Active Directory joinforbindelse skal konfigureres i dit miljø (enten via samling eller AAD-Forbind synkronisering)
- AAD-Forbind synkronisering skal inkludere enhedsobjekterne *i området* for synkronisering med Azure Active Directory (når det er nødvendigt til joinforbindelse)
- AAD-Forbind regler for synkronisering [skal ændres for Server 2012 R2](/microsoft-365/security/defender-endpoint/troubleshoot-security-config-mgt?view=o365-worldwide#instructions-for-applying-computer-join-rule-in-aad-connect) (når der kræves understøttelse af Server 2012 R2)
- Alle enheder skal registreres i Azure Active Directory for den lejer, der er vært for Microsoft Defender for Endpoint. Scenarier på tværs af lejere understøttes ikke. 

### <a name="connectivity-requirements"></a>Forbindelseskrav

Enheder skal have adgang til følgende slutpunkter:

- `enterpriseregistration.windows.net`- For Azure AD registrering.
- `login.microsoftonline.com`- For Azure AD registrering.
- `*.dm.microsoft.com` – Brugen af jokertegn understøtter cloudtjenestens slutpunkter, der bruges til tilmelding, indtjekning og rapportering, og som kan ændres, efterhånden som tjenesten skaleres.

> [!Note]
> Hvis organisationens brugere kontrollerer SSL (Secure Socket Layer), skal slutpunkterne udelukkes fra inspektionen.

### <a name="supported-platforms"></a>Understøttede platforme

Politikker for Microsoft Defender for Endpoint sikkerhedsadministration understøttes for følgende enhedsplatforme:

- Windows 10 Professional/Enterprise (med [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541))
- Windows 11 Professional/Enterprise
- Windows Server 2012 R2 med [Microsoft Defender for Down-Level-enheder](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2016 med [Microsoft Defender for Down-Level-enheder](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview)
- Windows Server 2019 (med [KB5006744](https://support.microsoft.com/topic/october-19-2021-kb5006744-os-build-17763-2268-preview-e043a8a3-901b-4190-bb6b-f5a4137411c0))
- Windows Server 2022 (med [KB5006745](https://support.microsoft.com/topic/october-26-2021-kb5006745-os-build-20348-320-preview-8ff9319a-19e7-40c7-bbd1-cd70fcca066c))

### <a name="licensing-and-subscriptions"></a>Licenser og abonnementer

Hvis du vil bruge sikkerhedsadministration til Microsoft Defender for Endpoint, skal du bruge:

- Et abonnement, der giver licenser til Microsoft Defender for Endpoint, f.eks. Microsoft 365, eller en separat licens til kun Microsoft Defender for Endpoint. Et abonnement, der giver Microsoft Defender for Endpoint licenser, giver også din lejer adgang til slutpunktets sikkerhedsnode i Microsoft Endpoint Manager Administration.

  > [!NOTE]  
  > **Undtagelse**: Hvis du har adgang til Microsoft Defender for Endpoint som en del af en Licens kun til Microsoft Defender for Cloud (tidligere Azure Security Center), er Sikkerhedsadministration for Microsoft Defender for Endpoint funktionalitet ikke tilgængelig.

I slutpunktets sikkerhedsnode skal du konfigurere og installere politikker for at administrere Microsoft Defender for Endpoint for dine enheder og overvåge enhedsstatus.

Du kan få aktuelle oplysninger om indstillinger under [Minimumkrav til Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/minimum-requirements?view=o365-worldwide&preserve-view=true).



## <a name="architecture"></a>Architecture

Følgende diagram er en konceptuel repræsentation af Microsoft Defender for Endpoint løsning til administration af sikkerhedskonfiguration.

:::image type="content" alt-text="Konceptuel repræsentation af løsningen til administration af Microsoft Defender for Endpoint sikkerhedskonfiguration" source="../security/defender-endpoint/images/mde-architecture.png":::

1. Enheder ombord til Microsoft Defender for Endpoint.

2. Der etableres et tillidsforhold mellem hver enhed og Azure AD. Når en enhed har et eksisterende tillidsforhold, bruges det. Når enheder ikke er registreret, oprettes der et nyt tillidsforhold.

3. Enheder bruger deres Azure AD identitet til at kommunikere med Endpoint Manager. Denne identitet gør det muligt for Microsoft Endpoint Manager at distribuere politikker, der er målrettet til enhederne, når de tjekker ind.

4. Defender for Endpoint rapporterer status for politikken tilbage til Endpoint Manager.

## <a name="which-solution-should-i-use"></a>Hvilken løsning skal jeg bruge?

Microsoft Endpoint Manager indeholder flere metoder og politiktyper til administration af konfigurationen af Defender for Endpoint på enheder.

Når dine behov for enhedsbeskyttelse rækker ud over administration af Defender for Endpoint, skal du se [Oversigt over enhedsbeskyttelse](/mem/intune/protect/device-protect) for at få mere at vide om yderligere funktioner, der leveres af Microsoft Endpoint Manager for at hjælpe med at beskytte enheder, herunder *enhedsoverholdelse*, *administrerede apps*, *politikker til beskyttelse af apps* og integration med tredjepartsoverholdelse og partnere til *forsvar af mobiltrusler*.

Følgende tabel kan hjælpe dig med at forstå, hvilke politikker der kan konfigurere MDE-indstillinger, der understøttes af enheder, der administreres af de forskellige scenarier. Når du installerer en politik, der understøttes for både *MDE-sikkerhedskonfiguration* og *Microsoft Endpoint Manager*, kan en enkelt forekomst af denne politik behandles af enheder, der kun kører Microsoft Defender for Endpoint, og enheder, der administreres af enten Intune eller Configuration Manager.

| Microsoft Endpoint Manager  | Arbejdsbyrde |Politik| Konfiguration af MDE-sikkerhed  |  Microsoft Endpoint Manager |
|----------------|----------------|-------------------|------------|
| Slutpunktssikkerhed    | Antivirus   |     Antivirus           | ![Understøttes](../media/green-check.png)  | ![Understøttes](../media/green-check.png)  |
|                      | Antivirus   |   Antivirusudeladelser   | ![Understøttes](../media/green-check.png)  | ![Understøttes](../media/green-check.png)  |
|                      | Antivirus   | Windows Sikkerhed oplevelse |                        | ![Understøttes](../media/green-check.png)  |
|                      | Diskkryptering   |     Alle |      | ![Understøttes](../media/green-check.png)  |
|                      | Firewall   | Firewall              | ![Understøttes](../media/green-check.png) | ![Understøttes](../media/green-check.png)  |
|                      | Firewall | Firewallregler                | ![Understøttes](../media/green-check.png) | ![Understøttes](../media/green-check.png)  |
|                      | Slutpunktsregistrering og -svar   | Slutpunktsregistrering og -svar | ![Understøttes](../media/green-check.png) | ![Understøttes](../media/green-check.png)  |
|                      | Reduktion af angrebsoverfladen    |   Alle |          | ![Understøttes](../media/green-check.png)  |
|                      | Kontobeskyttelse       |    Alle |     | ![Understøttes](../media/green-check.png)  |
|                      | Enhedsoverholdelse     |   Alle |  | ![Understøttes](../media/green-check.png)  |
|                      | Betinget adgang    |   Alle |  | ![Understøttes](../media/green-check.png)  |
|                      | Sikkerhedsbaselines      |  Alle |   | ![Understøttes](../media/green-check.png)  |

**Sikkerhedspolitikker for slutpunkter** er dedikerede grupper af indstillinger, der er beregnet til brug af sikkerhedsadministratorer, som fokuserer på at beskytte enheder i din organisation.

- **Antiviruspolitikker** administrerer de sikkerhedskonfigurationer, der findes i Microsoft Defender for Endpoint. Se  [antiviruspolitikken](/mem/intune/protect/endpoint-security-antivirus-policy) for at få mere at vide om sikkerhed for slutpunkter.
- Politikker til **reduktion af angrebsoverfladen** fokuserer på at minimere de steder, hvor din organisation er sårbar over for cybertrusler og angreb. Du kan finde flere oplysninger i [Oversigt over reduktion af angrebsoverfladen](/windows/security/threat-protection/microsoft-defender-atp/overview-attack-surface-reduction) i dokumentationen til Windows Threat Protection og politikken til [reduktion af angrebsoverfladen](/mem/intune/protect/endpoint-security-asr-policy) for slutpunktssikkerhed.
- **Politikker for registrering af slutpunkter og svar** (Slutpunktsregistrering og -svar) administrerer Defender for Endpoint-funktioner, der leverer avancerede angrebsregistreringer, der er næsten i realtid og kan handles på. Baseret på Slutpunktsregistrering og -svar konfigurationer kan sikkerhedsanalytikere prioritere beskeder effektivt, få indblik i det fulde omfang af et brud og reagere på trusler. Se [slutpunktsregistrering og -svar](/mem/intune/protect/endpoint-security-edr-policy) politik for slutpunktssikkerhed.
- **Firewallpolitikker** fokuserer på Defender-firewallen på dine enheder. Se [firewallpolitik](/mem/intune/protect/endpoint-security-firewall-policy) for at få oplysninger om sikkerhed for slutpunkter.
- **Firewallregler** konfigurerer detaljerede regler for firewalls, herunder specifikke porte, protokoller, programmer og netværk. Se [firewallpolitik](/mem/intune/protect/endpoint-security-firewall-policy) for at få oplysninger om sikkerhed for slutpunkter.
- **Grundlæggende sikkerhedsindstillinger** omfatter forudkonfigurerede sikkerhedsindstillinger, der definerer Microsofts anbefalede sikkerhedsholdning for forskellige produkter, f.eks. Defender, Edge eller Windows. Standardanbefalinger kommer fra de relevante produktteams og giver dig mulighed for hurtigt at udrulle den anbefalede sikre konfiguration på enheder. Selvom indstillingerne forudkonfigureres i hver baseline, kan du oprette brugerdefinerede forekomster af dem for at fastslå din organisations sikkerhedsforventninger. Se [grundlæggende sikkerhedslinjer](/mem/intune/protect/security-baselines) for at få Intune.

## <a name="configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management"></a>Konfigurer din lejer til at understøtte Microsoft Defender for Endpoint administration af sikkerhedskonfiguration

Hvis du vil understøtte Microsoft Defender for Endpoint administration af sikkerhedskonfiguration via Microsoft Endpoint Manager Administration, skal du aktivere kommunikation mellem dem inde fra hver konsol.

1. Log på [Microsoft 365 Defender portal,](https://security.microsoft.com/) og gå til **Indstillinger** >  **Endpoints** > **Configuration Management** > **Enforcement Scope**, og aktivér platformene til administration af sikkerhedsindstillinger:

   :::image type="content" source="../media/security-settings-mgt.png" alt-text="Aktivér administration af Microsoft Defender for Endpoint indstillinger i Defender-konsollen.":::
    
1. Konfigurer indstillinger for pilottilstand og Configuration Manager autoritet, så de passer til organisationens behov:

   :::image type="content" source="../media/pilot-CMAuthority-mde-settings-management-defender.png" alt-text="Konfigurer pilottilstand for administration af slutpunktsindstillinger på portalen Microsoft 365 Defender.":::
   
  > [!TIP]
  > Brug pilottilstand og de korrekte enhedskoder til at teste og validere udrulningen på et lille antal enheder. Uden at bruge pilottilstand tilmeldes alle enheder, der er omfattet af det konfigurerede område, automatisk.

1. Sørg for, at de relevante brugere har tilladelse til at administrere sikkerhedsindstillinger for slutpunkter i Microsoft Endpoint Manager eller tildele disse tilladelser ved at konfigurere en rolle på Defender-portalen. Gå til **Indstillinger** >  **Rolles** > **Tilføj element**:

   :::image type="content" source="../media/add-role-in-mde.png" alt-text="Opret en ny rolle på Defender-portalen.":::

   > [!TIP]
   > Du kan ændre eksisterende roller og tilføje de nødvendige tilladelser i forhold til at oprette yderligere roller i Microsoft Defender for Endpoint

1. Når du konfigurerer rollen, skal du tilføje brugere og sørge for at vælge **Administrer sikkerhedsindstillinger for slutpunkter i Microsoft Endpoint Manager**:

   :::image type="content" source="../media/add-role.png" alt-text="Tildel brugere tilladelser til at administrere indstillinger.":::

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

1. Vælg **Slutpunktssikkerhed** >  **Microsoft Defender for Endpoint**, og angiv **Tillad, at Microsoft Defender for Endpoint gennemtvinger Endpoint Security Configurations (prøveversion)** til **Til**.

   :::image type="content" source="../media/enable-mde-settings-management-mem.png" alt-text="Aktivér administration af Microsoft Defender for Endpoint-indstillinger i Microsoft Endpoint Manager Administration.":::

   Når du angiver denne indstilling til *Til*, kvalificeres alle enheder i platformområdet i Microsoft Defender for Endpoint, der ikke administreres af Microsoft Endpoint Manager, til at onboarde til Microsoft Defender for Endpoint.

## <a name="onboard-devices-to-microsoft-defender-for-endpoint"></a>Om bord på enheder til Microsoft Defender for Endpoint

Microsoft Defender for Endpoint understøtter flere muligheder for at onboarde enheder. Du kan finde den aktuelle vejledning under [Onboarding-værktøjer og -metoder til Windows enheder](/microsoft-365/security/defender-endpoint/security-config-management) i dokumentationen til Defender for Endpoint.



## <a name="co-existence-with-microsoft-endpoint-configuration-manager"></a>Samk Microsoft Endpoint Configuration Manager
I nogle miljøer kan det være en idé at bruge Sikkerhedsadministration til Microsoft Defender for Endpoint med [Configuration Manager lejertilknyt.](/mem/configmgr/tenant-attach/endpoint-security-get-started) Hvis du bruger begge dele, skal du styre politikken via en enkelt kanal, da brug af mere end én kanal opretter muligheden for konflikter og uønskede resultater.

Hvis du vil understøtte dette, skal du konfigurere *indstillingerne for Administrer sikkerhed ved hjælp af Configuration Manager* til *Fra*.  Log på [Microsoft 365 Defender-portalen](https://security.microsoft.com/), og gå til **Indstillinger** >  **Endpoints** > **Configuration Management** > **Enforcement Scope**:

:::image type="content" source="../media/manage-security-settings-cfg-mgr.png" alt-text="Administrer sikkerhedsindstillinger ved hjælp af Configuration Manager indstilling.":::

>[!NOTE]
>Når du bruger Sikkerhedsadministration til Microsoft Defender for Endpoint med Configuration Manager, skal slutpunktssikkerhedspolitikken isoleres til et enkelt kontrolfly. Styring af politik via begge kanaler kan medføre konflikter og uønskede resultater.


## <a name="create-azure-ad-groups"></a>Opret Azure AD grupper

Når enheder er onboardet til Defender for Endpoint, skal du oprette enhedsgrupper for at understøtte installation af politik for Microsoft Defender for Endpoint.

Sådan identificerer du de enheder, der er tilmeldt Microsoft Defender for Endpoint, men som ikke administreres af Intune eller Configuration Manager:

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Gå til **Enheder** > **Alle enheder**, og vælg derefter kolonnen **Administreret af** for at sortere visningen af enheder.

   Enheder, der onboarder til Microsoft Defender for Endpoint og har registreret, men som ikke administreres af Intune, vises **Microsoft Defender for Endpoint** i kolonnen *Administreret af*. Dette er de enheder, der kan modtage en politik for sikkerhedsadministration for Microsoft Defender for Endpoint.

   Du kan også finde to mærkater for enheder, der bruger sikkerhedsadministration til Microsoft Defender for Endpoint:

   - **MDEJoined – Føjet** til enheder, der er forbundet til mappen som en del af dette scenarie.
   - **MDEManaged – Føjet** til enheder, der aktivt bruger sikkerhedsadministrationsscenariet. Denne kode fjernes fra enheden, hvis Defender for Endpoint stopper administrationen af sikkerhedskonfigurationen.

Du kan oprette grupper for disse enheder [i Azure AD](/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) eller [fra Microsoft Endpoint Manager Administration](/mem/intune/fundamentals/groups-add).

## <a name="deploy-policy"></a>Installér politik

Når du har oprettet en eller flere Azure AD grupper, der indeholder enheder, der administreres af Microsoft Defender for Endpoint, kan du oprette og installere følgende politikker for Sikkerhedsadministration for Microsoft Defender for Endpoint til disse grupper:

- Antivirus
- Firewall
- Firewallregler
- Registrering af slutpunkt og svar

> [!TIP]
> Undgå at installere flere politikker, der administrerer den samme indstilling på en enhed.
>
> Microsoft Endpoint Manager understøtter installation af flere forekomster af hver slutpunktssikkerhedspolitiktype på den samme enhed, hvor hver enkelt politikforekomst modtages separat af enheden. En enhed kan derfor modtage separate konfigurationer for den samme indstilling fra forskellige politikker, hvilket resulterer i en konflikt. Nogle indstillinger (f.eks. antivirusudeladelser) flettes på klienten og anvendes korrekt.

1. Log på [Microsoft Endpoint Manager Administration](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Gå til **Slutpunktsikkerhed** , vælg derefter den type politik, du vil konfigurere, enten Antivirus eller Firewall, og vælg derefter **Opret politik**.

3. Angiv følgende egenskaber eller den valgte politiktype:

   - Som Antivirus-politik skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (prøveversion)**
     - Profil: **Microsoft Defender Antivirus (prøveversion)**

   - Som firewallpolitik skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (prøveversion)**
     - Profil: **Microsoft Defender Firewall (prøveversion)**

   - Som politik for firewallregler skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (prøveversion)**
     - Profil: **Microsoft Defender Firewall regler (prøveversion)**

   - For Politikken Registrering af slutpunkt og Svar skal du vælge:
     - Platform: **Windows 10, Windows 11 og Windows Server (prøveversion)**
     - Profil: **Registrering af slutpunkt og svar (prøveversion)**

   >[!Note]
   > Disse profiler gælder for begge enheder, der kommunikerer via MDM (Mobile Enhedshåndtering) med Microsoft Intune samt enheder, der kommunikerer ved hjælp af Microsoft Defender for Endpoint-klienten.
   >
   > Sørg for, at du gennemser din målretning og dine grupper efter behov.

4. Vælg **Opret**.

5. Angiv et navn og en beskrivelse til profilen på siden **Grundlæggende** , og vælg derefter **Næste**.

6. På siden **Konfigurationsindstillinger** skal du vælge de indstillinger, du vil administrere med denne profil. Hvis du vil vide mere om en indstilling, skal du udvide dialogboksen med oplysninger og vælge linket *Få mere at vide* for at få vist oplysninger om CSP'en for indstillingen i onlinedokumentationen.

   Når du er færdig med at konfigurere indstillinger, skal du vælge **Næste**.

7. På siden **Tildelinger** skal du vælge de Azure AD grupper, der skal modtage denne profil. Du kan få flere oplysninger om tildeling af profiler under [Tildel bruger- og enhedsprofiler](/mem/intune/configuration/device-profile-assign).

   Vælg **Næste** for at fortsætte.

   > [!TIP]
   >
   > - Tildelingsfiltre understøttes ikke for profiler til administration af sikkerhedskonfiguration.
   > - Det er kun *enhedsobjekter,* der gælder for Microsoft Defender for Endpoint administration. Målretningsbrugere understøttes ikke.
   > - De konfigurerede politikker gælder for både Microsoft Intune og Microsoft Defender for Endpoint klienter

8. Fuldfør processen til oprettelse af politikken, og vælg derefter **Opret** på siden **Gennemse + opret**. Den nye profil vises på listen, når du vælger politiktypen for den profil, du har oprettet.

9. Vent på, at politikken tildeles, og få vist en indikation af, at politikken er blevet anvendt.

10. Du kan validere, at indstillingerne er anvendt lokalt på klienten, ved hjælp af kommandoværktøjet [Get-MpPreference](/powershell/module/defender/get-mppreference#examples) .
