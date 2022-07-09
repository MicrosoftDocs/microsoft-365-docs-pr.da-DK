---
title: Foretag fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint
description: Foretag fejlfinding af problemer, der kan opstå under onboarding af enheder ved hjælp af Sikkerhedsadministration for Microsoft Defender for Endpoint.
keywords: fejlfinding af onboarding, onboardingproblemer, logbog, dataindsamling og eksempelbuilds, sensordata og diagnosticering
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: 0ceb24b5da0947dbb2b79ca7560ffbb46b701b38
ms.sourcegitcommit: 2aa5c026cc06ed39a9c1c2bcabd1f563bf5a1859
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/09/2022
ms.locfileid: "66696266"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Foretag fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Sikkerhedsadministration for Microsoft Defender for Endpoint er en funktion til enheder, der ikke administreres af en Microsoft-Endpoint Manager, enten Microsoft Intune eller Microsoft Endpoint Configuration Manager, til at modtage sikkerhed konfigurationer til Microsoft Defender for Endpoint direkte fra Endpoint Manager.
Du kan få flere oplysninger om Sikkerhedsadministration til Microsoft Defender for Endpoint under [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Du kan finde oplysninger om sikkerhedsadministration for Microsoft Defender for Endpoint onboardinginstruktioner under [Microsoft Defender for Endpoint Administration af sikkerhedskonfiguration](security-config-management.md)

Denne komplette onboarding er designet til at være friktionsfri og kræver ikke brugerinput. Men hvis du støder på problemer under onboarding, kan du få vist og foretage fejlfinding af fejl på Microsoft Defender for Endpoint platform.

> [!NOTE]
> Hvis du har problemer med onboardingflowet for nye enheder, skal du gennemse [forudsætningerne for Microsoft Defender for Endpoint](/mem/intune/protect/mde-security-integration#prerequisites) og sørge for, at onboardinginstruktionerne følges.

Du kan finde flere oplysninger om klientanalysen under [Fejlfinding af sensortilstand ved hjælp af Microsoft Defender for Endpoint Klientanalyse](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Registrerer domænetilsluttede computere med Azure Active Directory

Hvis du vil registrere enheder til Azure Active Directory, skal du sikre dig følgende:

- Computere kan godkende med domænecontrolleren
- Computere har adgang til følgende Microsoft-ressourcer fra organisationens netværk:
  - /windows/iot/iot-enterprise/commercialization/licensing
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD forbindelse er konfigureret til at synkronisere computerobjekterne. Computer-O'er er som standard i Azure AD oprette forbindelse til synkroniseringsomfang. Hvis computerobjekterne tilhører bestemte organisationsenheder, skal du konfigurere DE TIL at synkronisere i Azure AD Opret forbindelse. Hvis du vil vide mere om, hvordan du synkroniserer computerobjekter ved hjælp af Azure AD Opret forbindelse, skal du se [Organisationsenhedsbaseret filtrering](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD forbindelse synkroniserer ikke Windows Server 2012 R2-computerobjekter. Hvis du har brug for at registrere dem med Azure AD til sikkerhedsadministration for Microsoft Defender for Endpoint, skal du tilpasse Azure AD oprette forbindelse til synkroniseringsreglen, så disse computerobjekter medtages i synkroniseringsområdet. Se [Instruktioner til anvendelse af reglen Computer Join i Azure Active Directory Connect]().

> [!NOTE]
> Hvis du vil fuldføre onboardingflowet og uafhængigt af en enheds operativsystem, kan azure Active Directory-tilstanden for en enhed ændres baseret på enhedens oprindelige tilstand:
>
> <br>
>
>|Starter enhedens tilstand|Ny enhedstilstand|
>|---|---|
>|Allerede AADJ eller HAADJ|Forbliver som den er|
>|Ikke AADJ eller Hybrid Azure Active Directory Join (HAADJ) + domænetilsluttet|Enheden er HAADJ'd|
>|Ikke AADJ eller HAADJ + Ikke domænetilsluttet|Enheden er AADJ'd|
>
> Hvor AADJ repræsenterer Azure Active Directory Join, og HAADJ repræsenterer Hybrid Azure Active Directory Join.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Foretag fejlfinding af fejl fra Microsoft Defender for Endpoint-portalen

Via Microsoft Defender for Endpoint-portalen kan sikkerhedsadministratorer nu foretage fejlfinding af sikkerhedsadministration for Microsoft Defender for Endpoint onboarding.

I **Konfigurationsstyring** er **Onboarded via MDE-widgetten Til administration af sikkerhed** blevet tilføjet for at vise en oversigt over tilmeldingsstatus for Microsoft Defender for Endpoint-administrerede enheder.

Hvis du vil se en liste over alle enheder, der administreres af Microsoft Defender for Endpoint, skal du vælge **Få vist alle enheder, der administreres af MDE**.

Hvis en enheds tilmeldingsstatus ikke er "Udført" på listen, skal du vælge enheden for at få vist fejlfindingsdetaljer i sidepanelet, der peger på den egentlige årsag til fejlen og den tilsvarende dokumentation.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="De filterkriterier, der anvendes på enhedens lagerside" lightbox="./images/secconfig-mde-error.png":::

> [!NOTE] 
> Vi er opmærksomme på et problem, der påvirker den nøjagtige registrering af mdm'er fra tredjepart, når vi forsøger at bruge sikkerhedsadministrationsfunktionen, og arbejder på en rettelse. 

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Kør Microsoft Defender for Endpoint klientanalyse på Windows

Overvej at køre Klientanalyse på slutpunkter, der ikke kan fuldføre sikkerhedsadministrationen for Microsoft Defender for Endpoint onboardingflow. Du kan finde flere oplysninger om klientanalysen under [Fejlfinding af sensortilstand ved hjælp af Microsoft Defender for Endpoint Klientanalyse](overview-client-analyzer.md).

MDE-klientanalyse-outputfilen (MDE-Results.htm) kan levere vigtige fejlfindingsoplysninger:

- Bekræft, at enhedens operativsystem er inden for sikkerhedsadministration for Microsoft Defender for Endpoint onboardingflow i afsnittet **Generelle enhedsoplysninger**
- Kontrollér, at enheden er registreret til Azure Active Directory under **Oplysninger om administration af enhedskonfiguration**

  :::image type="content" source="images/client-analyzer-results.png" alt-text="Klientanalyseresultaterne" lightbox="images/client-analyzer-results.png":::

I afsnittet **Detaljerede resultater** i rapporten indeholder Klientanalyse også handlingsvejledning.

> [!TIP]
> Sørg for, at afsnittet Detaljerede resultater i rapporten ikke indeholder nogen "Fejl", og sørg for at gennemse alle "Advarselsmeddelelser".

Som en del af onboardingflowet til sikkerhedsadministration er det f.eks. påkrævet, at Azure Active Directory-lejer-id'et i din Microsoft Defender for Endpoint lejer stemmer overens med det SCP-lejer-id, der vises i afsnittet **Oplysninger om enhedskonfigurationsstyring** i rapporterne. Hvis det er relevant, anbefaler rapportoutputtet at udføre denne bekræftelse.

:::image type="content" source="images/detailed-results.png" alt-text="Den side, der viser de detaljerede resultater" lightbox="images/detailed-results.png"

## <a name="general-troubleshooting"></a>Generel fejlfinding

Hvis du ikke kunne identificere den onboardede enhed i AAD eller MEM og ikke modtog en fejl under tilmeldingen, kan du kontrollere, at registreringsdatabasenøglen `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` indeholder yderligere oplysninger om fejlfinding.

:::image type="content" source="images/enrollment-status.png" alt-text="Den side, der viser tilmeldingsstatussen" lightbox="images/enrollment-status.png":::

I følgende tabel vises en liste over fejl og retninger for, hvad du skal prøve/tjekke ind for at løse fejlen. Bemærk, at listen over fejl ikke er komplet og er baseret på typiske/almindelige fejl, som kunder har oplevet tidligere:

|Fejlkode|Status for tilmelding|Administratorhandlinger|
|---|---|---|
|`5-7`, `9`, `11-12`, `26-33`|Generel fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration. Dette kan skyldes, at enheden ikke opfylder [forudsætningerne for Microsoft Defender for Endpoint administrationskanal](security-config-management.md). Kørsel af [klientanalysen](https://aka.ms/BetaMDEAnalyzer) på enheden kan hjælpe med at identificere rodårsagen til problemet. Hvis dette ikke hjælper, skal du kontakte support.|
| `8`, `44` | Problem med Konfiguration af Microsoft Endpoint Manager | Enheden blev onboardet til Microsoft Defender for Endpoint. Microsoft Endpoint Manager er dog ikke konfigureret via Administration Center for at tillade Microsoft Defender for Endpoint sikkerhedskonfiguration. Sørg for, at [Microsoft Endpoint Manager-lejeren er konfigureret, og at funktionen er slået til](/mem/intune/protect/mde-security-integration#configure-your-tenant-to-support-microsoft-defender-for-endpoint-security-configuration-management).|
|`13-14`,`20`,`24`,`25`|Forbindelsesproblem|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration, som kan skyldes et forbindelsesproblem. Kontrollér, at [Azure Active Directory- og Microsoft Endpoint Manager-slutpunkter](security-config-management.md#connectivity-requirements) er åbnet i din firewall.|
|`10`,`42`|Generel hybridjoinforbindelsesfejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration, og operativsystemet kunne ikke udføre hybridjoinforbindelse. Brug [Foretag fejlfinding af hybride Azure Active Directory-tilsluttede enheder](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) til fejlfinding af fejl i hybridjoinforbindelse på OS-niveau.|
|`15`|Lejeruoverensstemmelse|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration, fordi dit Microsoft Defender for Endpoint lejer-id ikke stemmer overens med dit Azure Active Directory-lejer-id. Sørg for, at Azure Active Directory-lejer-id'et fra din Defender for Endpoint-lejer stemmer overens med lejer-id'et i SCP-posten for dit domæne. Du kan finde flere oplysninger [ved at foretage fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Hybridfejl – Tjenesteforbindelsespunkt|Enheden blev onboardet til Microsoft Defender for Endpoint. Posten tjenesteforbindelsespunkt (SCP) er dog ikke konfigureret korrekt, og enheden kunne ikke tilsluttes Azure AD. Dette kan skyldes, at SCP'et er konfigureret til at blive medlem af Enterprise DRS. Sørg for, at SCP-posten peger på AAD og SCP er konfigureret i nedenstående bedste praksis. Du kan få flere oplysninger under [Konfigurer et tjenesteforbindelsespunkt](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Certifikatfejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en fejl i enhedscertifikatet. Enhedscertifikatet tilhører en anden lejer. Kontrollér, at bedste praksis følges, når du opretter certifikatprofiler, der er [tillid til](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36` , `37`| Forkert konfiguration af AAD Connect |Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en forkert konfiguration i AAD Connect. Hvis du vil finde ud af, hvad der forhindrer enheden i at registrere sig i AAD, kan du overveje at køre [fejlfindingsværktøjet til enhedsregistrering](/samples/azure-samples/dsregtool/dsregtool). For Windows Server 2012 R2 skal du køre de  [dedikerede fejlfindingsinstruktioner](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy).  |
|`38`,`41`|DNS-fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en DNS-fejl. Kontrollér internetforbindelsen og/eller DNS-indstillingerne på enheden. De ugyldige DNS-indstillinger kan være på arbejdsstationens side. Active Directory kræver, at du bruger domæne-DNS for at fungere korrekt (og ikke routerens adresse). Du kan finde flere oplysninger under [Fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration, for Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).|
|`40`|Problem med synkronisering af ur|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration. Kontrollér, at uret er indstillet korrekt, og at det er synkroniseret på den enhed, hvor fejlen opstår.|
|`43`|MDE og ConfigMgr|Enheden administreres ved hjælp af Configuration Manager og Microsoft Defender for Endpoint. Styring af politikker via begge kanaler kan medføre konflikter og uønskede resultater. For at undgå dette skal sikkerhedspolitikker for slutpunkter isoleres til et enkelt kontrolplan. |

## <a name="azure-active-directory-runtime-troubleshooting"></a>Fejlfinding af Azure Active Directory Runtime

Den primære mekanisme til fejlfinding af Azure Active Directory Runtime (AADRT) er at indsamle fejlfindingssporinger. Azure Active Directory Runtime på Windows bruger **ETW-udbyder med id bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. ETW-sporinger skal registreres med gengivelsen af fejlen (hvis der f.eks. opstår joinforbindelsesfejl, skal sporingerne aktiveres i den periode, der dækker kald til AADRT-API'er for at udføre joinforbindelse).

Nedenfor kan du se en typisk fejl i AADRT-log, og hvordan du læser den:

:::image type="content" source="images/event-properties.png" alt-text="Siden med hændelsesegenskaber" lightbox="images/event-properties.png":::

Ud fra oplysningerne i meddelelsen er det i de fleste tilfælde muligt at forstå, hvilken fejl der opstod, hvilken Win32-API der returnerede fejlen (hvis relevant), hvilken URL-adresse (hvis relevant) der blev brugt, og hvilken AAD Runtime API-fejl der blev fundet.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>Instruktioner til anvendelse af en Computer Join-regel i AAD Connect

I forbindelse med sikkerhedsadministration for Microsoft Defender for Endpoint på computere, der er tilsluttet Windows Server 2012 R2-domænet, er der behov for en opdatering til Azure AD Connect-synkroniseringsreglen "In from AD-Computer Join". Dette kan opnås ved at klone og ændre reglen, hvilket deaktiverer den oprindelige regel "In from AD - Computer Join". Azure AD Opret forbindelse giver som standard denne oplevelse til at foretage ændringer af indbyggede regler.

> [!NOTE]
>Disse ændringer skal anvendes på den server, hvor AAD Connect kører. Hvis du har installeret flere forekomster af AAD Connect, skal disse ændringer anvendes på alle forekomster.

1. Åbn programmet Editor til synkroniseringsregler i menuen Start. Find reglen med navnet **In fra AD – Computer Join** på regellisten. **Notér værdien i kolonnen 'Rangplacering' for denne regel.**

   :::image type="content" source="images/57ea94e2913562abaf93749d306dd6cf.png" alt-text="Editor til synkroniseringsregler" lightbox="images/57ea94e2913562abaf93749d306dd6cf.png":::

2. Med reglen **In from AD – Computer Join** fremhævet skal du vælge **Rediger**. I dialogboksen **Rediger bekræftelse af reserveret regel** skal du vælge **Ja**.

   :::image type="content" source="images/8854440d6180a5580efda24110551c68.png" alt-text="Bekræftelsessiden rediger reserveret regel" lightbox="images/8854440d6180a5580efda24110551c68.png":::

3. Vinduet **Rediger regel for indgående synkronisering** vises. Opdater beskrivelsen af reglen for at bemærke, at Windows Server 2012R2 synkroniseres ved hjælp af denne regel. Lad alle andre indstillinger forblive uændrede med undtagelse af prioritetsværdien. Angiv en værdi for Rangplacering, der er højere end værdien fra den oprindelige regel (som vist på regellisten).

   :::image type="content" source="images/ee0f29162bc3f2fbe666c22f14614c45.png" alt-text="Siden Rediger regel for indgående synkronisering, hvor du angiver værdier" lightbox="images/ee0f29162bc3f2fbe666c22f14614c45.png":::

4. Vælg **Næste** tre gange. Dette navigerer til afsnittet 'Transformationer' i reglen. Foretag ikke ændringer af afsnittene "Filter for områder" og "Joinforbind regler" i reglen. Afsnittet 'Transformationer' bør nu vises.

   :::image type="content" source="images/296f2c2a705e41233631c3784373bc23.png" alt-text="Reglen for indgående synkronisering" lightbox="images/296f2c2a705e41233631c3784373bc23.png":::

5. Rul ned til bunden af listen over transformationer. Find transformationen for attributten **CloudFiltered** . I tekstfeltet i kolonnen **Kilde** skal du markere al teksten (Control-A) og slette den. Tekstfeltet bør nu være tomt.

6. Indsæt indholdet af den nye regel i tekstfeltet.

    ```command
    IIF(
      IsNullOrEmpty([userCertificate])
      ||
      (
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        (Left([operatingSystemVersion],2) = "6.")
        &&
        (Left([operatingSystemVersion],3) <> "6.3")
      )
      ||
      (
        (Left([operatingSystemVersion],3) = "6.3")
        &&
        (InStr(UCase([operatingSystem]),"WINDOWS") > 0)
        &&
        With(
          $validCerts,
          Where(
            $c,
            [userCertificate],
            IsCert($c) && CertNotAfter($c) > Now() && RegexIsMatch(CertSubject($c), "CN=[{]*" & StringFromGuid([objectGUID]) & "[}]*", "IgnoreCase")),
          Count($validCerts) = 0)
      ),
      True,
      NULL
    )
    ```

7. Vælg **Gem** for at gemme den nye regel.

> [!NOTE]
> Når denne regelændring er udført, kræves der en fuld synkronisering af Active Directory. I store miljøer anbefales det at planlægge denne regelændring og fuld synkronisering under stille perioder i Det lokale Active Directory.

## <a name="related-topic"></a>Relateret emne

- [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
