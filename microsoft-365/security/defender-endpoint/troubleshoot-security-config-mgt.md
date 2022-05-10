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
ms.openlocfilehash: e7b9e757f15663338f2e12c645cc3cb0b63ef34b
ms.sourcegitcommit: 4cd8be7c22d29100478dce225dce3bcdce52644d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/10/2022
ms.locfileid: "65302239"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Foretag fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Administrer Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender for Endpoint](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Sikkerhedsadministration for Microsoft Defender for Endpoint er en funktion for enheder, der ikke administreres af en Microsoft Endpoint Manager, enten Microsoft Intune eller Microsoft Endpoint Configuration Manager, hvis du vil modtage sikkerhedskonfigurationer for Microsoft Defender for Endpoint direkte fra Endpoint Manager.
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
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD forbindelse er konfigureret til at synkronisere computerobjekterne. Computer-O'er er som standard i Azure AD oprette forbindelse til synkroniseringsomfang. Hvis computerobjekterne tilhører bestemte organisationsenheder, skal du konfigurere DE, der skal synkroniseres i Azure AD Forbind. Hvis du vil vide mere om, hvordan du synkroniserer computerobjekter ved hjælp af Azure AD Forbind, skal du se [Filtrering baseret på organisationsenhed](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD forbindelse synkroniseres ikke Windows Server 2012 R2-computerobjekter. Hvis du har brug for at registrere dem med Azure AD til sikkerhedsadministration for Microsoft Defender for Endpoint, skal du tilpasse Azure AD oprette forbindelse til synkroniseringsreglen, så disse computerobjekter medtages i synkroniseringsområdet. Se [Instruktioner til anvendelse af Computer Join-regel i Azure Active Directory Forbind]().

> [!NOTE]
> Hvis du vil fuldføre onboardingflowet og uafhængigt af en enheds operativsystem, kan en enheds Azure Active Directory tilstand ændres baseret på enhedens oprindelige tilstand:
>
> <br>
>
>|Starter enhedens tilstand|Ny enhedstilstand|
>|---|---|
>|Allerede AADJ eller HAADJ|Forbliver som den er|
>|Ikke AADJ eller Hybrid Azure Active Directory Join (HAADJ) + domænetilsluttet|Enheden er HAADJ'd|
>|Ikke AADJ eller HAADJ + Ikke domænetilsluttet|Enheden er AADJ'd|
>
> Hvor AADJ repræsenterer Azure Active Directory joinforbundet, og HAADJ repræsenterer hybride Azure Active Directory joinforbundne.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Foretag fejlfinding af fejl fra Microsoft Defender for Endpoint-portalen

Via Microsoft Defender for Endpoint-portalen kan sikkerhedsadministratorer nu foretage fejlfinding af sikkerhedsadministration for Microsoft Defender for Endpoint onboarding.

I **Enhedslager for slutpunkter** \> er kolonnen **Administreret af** føjet til filter efter administrationskanal (f.eks. MEM).

:::image type="content" source="./images/device-inventory-mde-error.png" alt-text="Enhedens lagerside" lightbox="./images/device-inventory-mde-error.png":::

Hvis du vil se en liste over alle de enheder, der ikke har udført sikkerhedsadministrationen for Microsoft Defender for Endpoint onboardingproces, skal du filtrere tabellen efter **MDE-Error**.

Vælg en bestemt enhed på listen for at få vist fejlfindingsdetaljer i sidepanelet, der peger på den underliggende årsag til fejlen og den tilsvarende dokumentation.


:::image type="content" source="./images/secconfig-mde-error.png" alt-text="De filterkriterier, der anvendes på enhedens lagerside" lightbox="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Kør Microsoft Defender for Endpoint klientanalyse på Windows

Overvej at køre Klientanalyse på slutpunkter, der ikke kan fuldføre sikkerhedsadministrationen for Microsoft Defender for Endpoint onboardingflow. Du kan finde flere oplysninger om klientanalysen under [Fejlfinding af sensortilstand ved hjælp af Microsoft Defender for Endpoint Klientanalyse](overview-client-analyzer.md).

MDE-klientanalyse-outputfilen (MDE-Results.htm) kan levere vigtige fejlfindingsoplysninger:

- Bekræft, at enhedens operativsystem er inden for sikkerhedsadministration for Microsoft Defender for Endpoint onboardingflow i afsnittet **Generelle enhedsoplysninger**
- Kontrollér, at enheden er registreret til Azure Active Directory i **Oplysninger om administration af enhedskonfiguration**

  :::image type="content" source="images/client-analyzer-results.png" alt-text="Klientanalyseresultaterne" lightbox="images/client-analyzer-results.png":::

I afsnittet **Detaljerede resultater** i rapporten indeholder Klientanalyse også handlingsvejledning.

> [!TIP]
> Sørg for, at afsnittet Detaljerede resultater i rapporten ikke indeholder nogen "Fejl", og sørg for at gennemse alle "Advarselsmeddelelser".

Som en del af onboardingflowet til sikkerhedsadministration er det f.eks. påkrævet, at det Azure Active Directory lejer-id i din Microsoft Defender for Endpoint lejer stemmer overens med det SCP-lejer-id, der vises i sektionen **Oplysninger om enhedskonfigurationsstyring** i rapporterne. Hvis det er relevant, anbefaler rapportoutputtet at udføre denne bekræftelse.

:::image type="content" source="images/detailed-results.png" alt-text="Den side, der viser de detaljerede resultater" lightbox="images/detailed-results.png"

## <a name="general-troubleshooting"></a>Generel fejlfinding

Hvis du ikke kunne identificere den onboardede enhed i AAD eller MEM og ikke modtog en fejl under tilmeldingen, kan du kontrollere, at registreringsdatabasenøglen `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` indeholder yderligere oplysninger om fejlfinding.

:::image type="content" source="images/enrollment-status.png" alt-text="Den side, der viser tilmeldingsstatussen" lightbox="images/enrollment-status.png":::

I følgende tabel vises en liste over fejl og retninger for, hvad du skal prøve/tjekke ind for at løse fejlen. Bemærk, at listen over fejl ikke er komplet og er baseret på typiske/almindelige fejl, som kunder har oplevet tidligere:

<br>

****

|Fejlkode|Status for tilmelding|Administratorhandlinger|
|---|---|---|
|`5-9`,`11-12`, `26-33`|Generel fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration. Dette kan skyldes, at enheden ikke opfylder [forudsætningerne for Microsoft Defender for Endpoint administrationskanal](security-config-management.md). Kørsel af [klientanalysen](https://aka.ms/BetaMDEAnalyzer) på enheden kan hjælpe med at identificere rodårsagen til problemet. Hvis dette ikke hjælper, skal du kontakte support.|
|`13-14`,`20`,`24`,`25`|Forbindelsesproblem|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration, som kan skyldes et forbindelsesproblem. Kontrollér, at [slutpunkterne Azure Active Directory og Microsoft Endpoint Manager](security-config-management.md#connectivity-requirements) er åbnet i firewallen.|
|`10`,`42`|Generel hybridjoinforbindelsesfejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration, og operativsystemet kunne ikke udføre hybridjoinforbindelse. Brug [Foretag fejlfinding af hybride Azure Active Directory-joinforbundne enheder](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) til fejlfinding af fejl i hybridjoinforbindelse på OS-niveau.|
|`15`|Lejeruoverensstemmelse|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration, fordi dit Microsoft Defender for Endpoint lejer-id ikke stemmer overens med dit Azure Active Directory lejer-id. Sørg for, at det Azure Active Directory lejer-id fra din Defender for Endpoint-lejer stemmer overens med lejer-id'et i SCP-posten for dit domæne. Du kan finde flere oplysninger [ved at foretage fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration for Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Hybridfejl – Tjenesteforbindelsespunkt|Enheden blev onboardet til Microsoft Defender for Endpoint. Posten tjenesteforbindelsespunkt (SCP) er dog ikke konfigureret korrekt, og enheden kunne ikke tilsluttes Azure AD. Dette kan skyldes, at SCP'et er konfigureret til at blive medlem af Enterprise DRS. Sørg for, at SCP-posten peger på AAD og SCP er konfigureret i nedenstående bedste praksis. Du kan få flere oplysninger under [Konfigurer et tjenesteforbindelsespunkt](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Certifikatfejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en fejl i enhedscertifikatet. Enhedscertifikatet tilhører en anden lejer. Kontrollér, at bedste praksis følges, når du opretter certifikatprofiler, der er [tillid til](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36`|Fejl i LDAP-API|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en forkert konfiguration i AAD Forbind. Hvis du vil identificere, hvad der forhindrer enheden i at registrere sig i AAD, kan du overveje at køre [fejlfindingsværktøjet til enhedsregistrering](/samples/azure-samples/dsregtool/dsregtool). For Windows Server 2012 R2 skal du køre de [dedikerede fejlfindingsinstruktioner](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy).  |
|`37`|Problem med synkronisering i det lokale område|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en forkert konfiguration i AAD Forbind. Hvis du vil identificere, hvad der forhindrer enheden i at registrere sig i AAD, kan du overveje at køre [fejlfindingsværktøjet til enhedsregistrering](/samples/azure-samples/dsregtool/dsregtool). For Windows Server 2012 R2 skal du køre de [dedikerede fejlfindingsinstruktioner](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-legacy). |
|`38`,`41`|DNS-fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration på grund af en DNS-fejl. Kontrollér internetforbindelsen og/eller DNS-indstillingerne på enheden. De ugyldige DNS-indstillinger kan være på arbejdsstationens side. Active Directory kræver, at du bruger domæne-DNS for at fungere korrekt (og ikke routerens adresse). Du kan finde flere oplysninger under [Fejlfinding af onboardingproblemer, der er relateret til sikkerhedsadministration, for Microsoft Defender for Endpoint](troubleshoot-security-config-mgt.md).|
|`40`|Problem med synkronisering af ur|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til administration af sikkerhedskonfiguration. Kontrollér, at uret er indstillet korrekt, og at det er synkroniseret på den enhed, hvor fejlen opstår.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>fejlfinding af Azure Active Directory kørsel

### <a name="azure-active-directory-runtime"></a>Azure Active Directory runtime

Den primære mekanisme til fejlfinding af Azure Active Directory Runtime (AADRT) er at indsamle fejlfindingssporinger. Azure Active Directory Runtime på Windows bruger **ETW-provideren med ID bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. ETW-sporinger skal registreres med gengivelsen af fejlen (hvis der f.eks. opstår joinforbindelsesfejl, skal sporingerne aktiveres i den periode, der dækker kald til AADRT-API'er for at udføre joinforbindelse).

Nedenfor kan du se en typisk fejl i AADRT-log, og hvordan du læser den:

:::image type="content" source="images/event-properties.png" alt-text="Siden med hændelsesegenskaber" lightbox="images/event-properties.png":::

Ud fra oplysningerne i meddelelsen er det i de fleste tilfælde muligt at forstå, hvilken fejl der opstod, hvilken Win32-API der returnerede fejlen (hvis relevant), hvilken URL-adresse (hvis relevant) der blev brugt, og hvilken AAD Kørsels-API-fejl der blev fundet.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>Instruktioner til anvendelse af Computer Join-regel i AAD Forbind

I forbindelse med Sikkerhedsadministration for Microsoft Defender for Endpoint på Windows Server 2012 R2-domænetilsluttede computere er der behov for en opdatering til Azure AD Forbind synkroniseringsregel "In from AD-Computer Join". Dette kan opnås ved at klone og ændre reglen, hvilket deaktiverer den oprindelige regel "In from AD - Computer Join". Azure AD Forbind giver som standard denne oplevelse til at foretage ændringer af indbyggede regler.

> [!NOTE]
>Disse ændringer skal anvendes på den server, hvor AAD Forbind kører. Hvis du har installeret flere forekomster af AAD Forbind, skal disse ændringer anvendes på alle forekomster.

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
