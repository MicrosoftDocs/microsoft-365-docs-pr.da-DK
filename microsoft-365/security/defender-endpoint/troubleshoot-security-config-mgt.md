---
title: Fejlfinding af onboardingproblemer i forbindelse med Sikkerhedsadministration for Microsoft Defender til Slutpunkt
description: Fejlfinding af problemer, der kan opstå under onboarding af enheder ved hjælp af Sikkerhedsadministration til Microsoft Defender til slutpunkt.
keywords: fejlfinding af onboarding, onboardingproblemer, logføring, dataindsamling og eksempel builds, sensordata og diagnosticering
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
ms.openlocfilehash: d6c3beb5a33a6d2323159917944e0f069b02035e
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/19/2022
ms.locfileid: "63601015"
---
# <a name="troubleshoot-onboarding-issues-related-to-security-management-for-microsoft-defender-for-endpoint"></a>Fejlfinding af onboardingproblemer i forbindelse med Sikkerhedsadministration for Microsoft Defender til Slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**

- [Administrer Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
- [Microsoft Defender til Slutpunkt](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Sikkerhedsadministration for Microsoft Defender til slutpunkt er en funktion til enheder, der ikke administreres af en Microsoft Endpoint Manager, hverken Microsoft Intune eller Microsoft Endpoint Configuration Manager for at modtage sikkerhedskonfigurationer til Microsoft Defender til slutpunkt direkte fra Endpoint Manager.
Du kan finde flere oplysninger om Sikkerhedsadministration for Microsoft Defender til slutpunkt under [Administrer Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration).

Du kan finde en sikkerhedsadministration for onboardinginstruktioner til [Microsoft Defender for Endpoint Security Configurationing](security-config-management.md)

Denne indbyggede onboarding er designet til at være problemfri og kræver ikke brugerinput. Men hvis du støder på problemer under onboarding, kan du få vist og foretage fejlfinding af fejl på platformen for Microsoft Defender til Slutpunkt.

> [!NOTE]
> Hvis du har problemer med onboardingflowet til nye enheder, skal du gennemse [forudsætningerne for Microsoft Defender til](/mem/intune/protect/mde-security-integration#prerequisites) slutpunktet og sørge for, at onboardinginstruktionerne følges.

Du kan finde flere oplysninger om klientanalysen under [Fejlfinding af sensorens tilstand ved hjælp af Microsoft Defender til Endpoint Client Analyzer](/microsoft-365/security/defender-endpoint/overview-client-analyzer).

## <a name="registering-domain-joined-computers-with-azure-active-directory"></a>Registrering af domænets computere med Azure Active Directory

Hvis du vil registrere Azure Active Directory, skal du sikre dig følgende:

- Computere kan godkende med domænecontrolleren
- Computere har adgang til følgende Microsoft-ressourcer fra din organisations netværk:
  - https://enterpriseregistration.windows.net
  - https://login.microsoftonline.com
  - https://device.login.microsoftonline.com
- Azure AD-forbindelsen er konfigureret til at synkronisere computerobjekterne. Computer-OUs er som standard inden for Azure AD-forbindelsesomfanget. Hvis computerobjekterne tilhører bestemte organisationsenheder (OUs), skal du konfigurere OUs til at synkronisere i Azure AD Forbind. Du kan få mere at vide om, hvordan du synkroniserer computerobjekter ved hjælp Forbind Azure AD-objekter, [under Organisationsenhedsbaseret filtrering](/azure/active-directory/hybrid/how-to-connect-sync-configure-filtering#organizational-unitbased-filtering).

> [!IMPORTANT]
> Azure AD Connect synkroniserer ikke Windows Server 2012 R2-computerobjekter. Hvis du vil registrere dem i Azure AD for Security Management til Microsoft Defender til slutpunkt, skal du tilpasse synkroniseringsreglen for Azure AD-forbindelse for at medtage disse computerobjekter i synkroniseringsomfanget. Se [Vejledning til anvendelse af reglen Computerforbindelse i Azure Active Directory Forbind]().

> [!NOTE]
> For at fuldføre onboardingflowet og uafhængigt af en enheds operativsystem kan enhedens Azure Active Directory ændres afhængigt af enhederens oprindelige tilstand:
>
> <br>
>
>|Startenhedstilstand|Ny enhedstilstand|
>|---|---|
>|Allerede AADJ eller HAADJ|Forbliver, som den er|
>|Not AADJ or Hybrid Azure Active Directory Join (HAADJ) + Domain joined|Enheden er HAADJ'd|
>|Not AADJ or HAADJ + Not domain joined|Enheden er AADJ'd|
>
> Hvor AADJ repræsenterer Azure Active Directory, og HAADJ repræsenterer Hybrid Azure Active Directory sammenføjet.

## <a name="troubleshoot-errors-from-the-microsoft-defender-for-endpoint-portal"></a>Fejlfinding af fejl fra Microsoft Defender for Endpoint-portalen

Sikkerhedsadministratorer kan nu via Microsoft Defender til Endpoint-portalen foretage fejlfinding af sikkerhedsadministration for Microsoft Defender til endpoint-onboarding.

I **lager for slutpunkter** \> **for** enheder er **kolonnen Administreret** af blevet tilføjet til at filtrere efter administrationskanal (f.eks. MEM).

:::image type="content" alt-text="Billede af lagerside for enheder" source="./images/device-inventory-mde-error.png":::

Hvis du vil se en liste over alle enheder, der har mislykket Security Management for Microsoft Defender for Endpoint onboarding-processen, skal du filtrere tabellen efter **MDE-Error**.

På listen skal du vælge en bestemt enhed for at få vist fejlfindingsoplysninger i sidepanelet, som peger på den egentlige årsag til fejlen og tilsvarende dokumentation.

:::image type="content" alt-text="Billede af lagerside for enheder filtreret" source="./images/secconfig-mde-error.png":::

## <a name="run-microsoft-defender-for-endpoint-client-analyzer-on-windows"></a>Kør Microsoft Defender for Endpoint Client Analyzer på Windows

Overvej at køre Klientanalyse på slutpunkter, der ikke fuldfører sikkerhedsadministrationen for onboardingflowet for Microsoft Defender til slutpunkter. Du kan finde flere oplysninger om klientanalysen under [Fejlfinding af sensorens tilstand ved hjælp af Microsoft Defender til Endpoint Client Analyzer](overview-client-analyzer.md).

MDE Client Analyzer-outputfilen (MDE Client Analyzer Results.htm) kan indeholde vigtige fejlfindingsoplysninger:

- Kontrollér, at enhedens operativsystem er i området for Sikkerhedsadministration for Microsoft Defender for endpoint-onboardingflow i **sektionen Generelle enhedsoplysninger**
- Kontrollér, at enheden er registreret som en Azure Active Directory oplysninger i **Detaljer om administration af enhedskonfiguration**

    ![Billede af resultater fra klientanalyse](images/client-analyzer-results.png)

I sektionen **Detaljerede** resultater i rapporten giver Klientanalyse også vejledning, der kan handle på.

> [!TIP]
> Sørg for, at sektionen Detaljerede resultater i rapporten ikke indeholder nogen "Fejl", og sørg for at gennemse alle "Advarsels"-meddelelser.

Som en del af onboardingflowet til sikkerhedsadministration kræves det f.eks., at Azure Active Directory-lejer-id'et i din Microsoft Defender for Endpoint-lejer matcher SCP-lejer-id'et,  der vises i rapporternes detaljer om enhedskonfigurationsadministration. Hvis det er relevant, anbefaler rapportoutputtet at udføre denne bekræftelse.

![Billede af detaljerede resultater](images/detailed-results.png)

## <a name="general-troubleshooting"></a>Generel fejlfinding

Hvis du ikke kunne identificere onboardingenheden i AAD eller MEM, og du ikke modtog en fejl under tilmeldingen, `Computer\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\SenseCM\\EnrollmentStatus` kan kontrol af registreringsdatabasenøglen give yderligere fejlfindingsoplysninger.

:::image type="content" alt-text="Billede af status for tilmelding." source="images/enrollment-status.png":::

I følgende tabel vises fejl og anvisninger for, hvad du skal prøve/kontrollere for at løse fejlen. Bemærk, at listen over fejl ikke er fuldstændig og er baseret på typiske/almindelige fejl, der er opstået af kunder tidligere:

<br>

****

|Fejlkode|Status for tilmelding|Administratorhandlinger|
|---|---|---|
|`5-9`,`11-12`, `26-33`|Generel fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til sikkerhedskonfigurationsstyring. Dette kan skyldes, at enheden ikke er [mødefor forudsætninger for Microsoft Defender for endpoint-administrationskanalen](security-config-management.md). Kørsel af [Klientanalyse på](https://aka.ms/BetaMDEAnalyzer) enheden kan hjælpe med at identificere den egentlige årsag til problemet. Hvis det ikke hjælper, skal du kontakte support.|
|`13-14`,`20`,`24`,`25`|Forbindelsesproblem|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i administrationsflowet til sikkerhedskonfigurationen, som kan skyldes et forbindelsesproblem. Kontrollér, [Azure Active Directory og Microsoft Endpoint Manager slutpunkter](security-config-management.md#connectivity-requirements) åbnes i din firewall.|
|`10`,`42`|Generel fejl i hybrid joinforbindelse|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i administrationsflowet til sikkerhedskonfiguration, og operativsystemet kunne ikke udføre hybrid joinforbindelse. Brug [Fejlfinding Azure Active Directory-enheder, der er forbundet til](/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current) fejlfinding af hybrid joinfejl i OS-niveau.|
|`15`|Lejerens uoverensstemmelse|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i administrationsflowet til sikkerhedskonfiguration, fordi dit Microsoft Defender til slutpunkt-lejer-id ikke stemmer overens med dit Azure Active Directory-lejer-id. Sørg for, at Azure Active Directory dit lejer-id fra din Defender for Endpoint-lejer svarer til lejer-id'et i dit domænes SCP-post. Hvis du vil have mere at [vide, skal du foretage fejlfinding af onboardingproblemer i forbindelse med Sikkerhedsadministration for Microsoft Defender til slutpunkt](troubleshoot-security-config-mgt.md).|
|`16`,`17`|Hybridfejl – Forbindelsespunkt for tjeneste|Enheden blev onboardet til Microsoft Defender for Endpoint. Men service Connection Point-posten (SCP) er ikke konfigureret korrekt, og enheden kunne ikke blive forbundet til Azure AD. Dette kan skyldes, at SCP konfigureres til at deltage i Enterprise DRS. Sørg for, at SCP-posten peger på AAD og SCP er konfigureret til at følge bedste praksis. Du kan finde flere oplysninger [under Konfigurere et tjenesteforbindelsespunkt](/azure/active-directory/devices/hybrid-azuread-join-manual#configure-a-service-connection-point).|
|`18`|Certifikatfejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i administrationsflowet til sikkerhedskonfigurationen på grund af en fejl i enhedscertifikatet. Enhedscertifikatet tilhører en anden lejer. Kontrollér, at der følges bedste fremgangsmåder, når du opretter [certifikatprofiler, der er tillid til](/mem/intune/protect/certificates-trusted-root#create-trusted-certificate-profiles).|
|`36`|LDAP API-fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til sikkerhedskonfigurationsstyring. Bekræft netværktopologien, og sørg for, at LDAP-API'en er tilgængelig for at udføre hybrid joinanmodninger.|
|`37`|Problem med lokal synkronisering|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til sikkerhedskonfigurationsstyring. Prøv igen senere. Hvis det ikke hjælper, skal du se Fejlfinding [af objektsynkronisering med Azure AD Forbind synkronisering](/azure/active-directory/hybrid/tshoot-connect-objectsync).|
|`38`,`41`|DNS-fejl|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til sikkerhedskonfigurationen på grund af en DNS-fejl. Kontrollér internetforbindelsen og/eller DNS-indstillingerne på enheden. De ugyldige DNS-indstillinger kan være på arbejdsstationens side. Active Directory kræver, at du bruger domæne-DNS for at fungere korrekt (og ikke routerens adresse). Få mere at vide under [Fejlfinding af onboardingproblemer i forbindelse med Sikkerhedsadministration for Microsoft Defender til slutpunkt](troubleshoot-security-config-mgt.md).|
|`40`|Problem med synkronisering af ur|Enheden blev onboardet til Microsoft Defender for Endpoint. Der opstod dog en fejl i flowet til sikkerhedskonfigurationsstyring. Kontrollér, at uret er indstillet korrekt og er synkroniseret på den enhed, hvor fejlen opstår.|

## <a name="azure-active-directory-runtime-troubleshooting"></a>Azure Active Directory Runtime-fejlfinding

### <a name="azure-active-directory-runtime"></a>Azure Active Directory Runtime

Den vigtigste mekanisme til fejlfinding Azure Active Directory Runtime (AADRT) er at indsamle fejlfindingssporinger. Azure Active Directory Runtime på Windows bruger **ETW-udbyder med id bd67e65c-9cc2-51d8-7399-0bb9899e75c1**. ETW-sporinger skal registreres sammen med reproduktionen af fejlen (f.eks. hvis joinfejlen opstår, skal sporingerne være aktiveret i hele tiden, som omfatter opkald til AADRT-API'er for at udføre joinforbindelse).

Nedenfor kan du se en typisk fejl i AADRT-log, og hvordan du kan læse den:

![Billede af hændelsesegenskaber](images/event-properties.png)

I henhold til oplysningerne i meddelelsen er det i de fleste tilfælde muligt at forstå, hvilken fejl der opstod, hvad Win32 API har returneret fejlen (hvis relevant), hvilken URL-adresse (hvis det er relevant), og hvilken AAD Runtime API-fejl der opstod.

## <a name="instructions-for-applying-computer-join-rule-in-aad-connect"></a>Vejledning til at anvende reglen Computer join i AAD Forbind

Hvis du vil have sikkerhedsadministration til Microsoft Defender til slutpunkt på Windows Server 2012 R2-domænets computere, kræves der en opdatering til Azure AD Forbind-synkroniseringsreglen "In from AD-Computer Join". Dette kan opnås ved at klone og ændre reglen, hvilket deaktiverer den oprindelige regel "In from AD – Computer Join". Azure AD Forbind giver som standard denne oplevelse, når du vil ændre de indbyggede regler.

> [!NOTE]
>Disse ændringer skal anvendes på den server, AAD Forbind kører. Hvis du har flere forekomster af AAD Forbind installeret, skal disse ændringer anvendes på alle forekomster.

1. Åbn programmet Redigeringsprogram til synkroniseringsregler fra menuen Start. Find reglen med navnet Ind fra **AD – Computer join på listen over regler**. **Vær opmærksom på værdien i kolonnen "Prioriteret" for denne regel.**

    ![Billede af editor til synkroniseringsregler](images/57ea94e2913562abaf93749d306dd6cf.png)

2. Med reglen **Ind fra AD – Computerforbindelse fremhævet** skal du vælge **Rediger**. I dialogboksen **Bekræftelse af reserveret regel** skal du vælge **Ja**.

   ![Billede af bekræftelse af reserveret regel](images/8854440d6180a5580efda24110551c68.png)

3. Vinduet **Rediger regel for indgående** synkronisering vises. Opdater beskrivelsen af reglen for at bemærke, Windows Server 2012R2 synkroniseres ved hjælp af denne regel. Lad alle andre indstillinger forblive uændrede med undtagelse af værdien Rangfølge. Angiv en værdi for Rangfølge, der er højere end værdien fra den oprindelige regel (som det fremgår af regellisten).

   ![Billede af bekræftelse](images/ee0f29162bc3f2fbe666c22f14614c45.png)

4. Vælg **Næste** tre gange. Dette navigerer til afsnittet "Transformationer" i reglen. Du må ikke foretage nogen ændringer i sektionerne "Filtrer område" og "Joinregler" i reglen. Sektionen "Transformationer" bør nu vises.

    ![Billede af indgående synkroniseringsregel](images/296f2c2a705e41233631c3784373bc23.png)

5. Rul til bunden af listen over transformationer. Find transformationen for **attributten cloudFiltered** . Markér al tekst ( **Ctrl-A** ) i tekstfeltet i kolonnen Kilde, og slet den. Tekstfeltet skulle nu være tomt.

6. Indsæt indholdet for den nye regel i tekstfeltet.

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
> Når denne regelændring er udført, kræves der en fuld synkronisering af dit Active Directory. Ved store miljøer anbefales det at planlægge denne regelændring og fuld synkronisering under lokale Active Directory stille perioder.

## <a name="related-topic"></a>Relateret emne

- [Administrer Microsoft Defender til slutpunkt på enheder med Microsoft Endpoint Manager](/mem/intune/protect/mde-security-integration)
