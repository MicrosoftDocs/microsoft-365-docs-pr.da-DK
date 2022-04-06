---
title: Kom i gang med Microsoft-udvidelse til overholdelse af regler og standarder
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Forbered og installer Microsoft Overholdelsesudvidelsen.
ms.openlocfilehash: 1c4c0a79f65f8a58ed30a9170256ef93b2bb4cef
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681804"
---
# <a name="get-started-with-microsoft-compliance-extension"></a>Kom i gang med Microsoft-udvidelse til overholdelse af regler og standarder

Brug disse procedurer til at udrulle Microsoft Compliance Extension.

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil bruge Microsoft Overholdelsesudvidelse, skal enheden være onboardet til slutpunktet DLP. Gennemse disse artikler, hvis du er ny bruger af DLP eller slutpunkt DLP

- [Få mere at vide om Microsoft-udvidelse til overholdelse af regler og standarder](dlp-chrome-learn-about.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md)
- [Onboardingværktøjer og metoder til Windows 10 enheder](device-onboarding-overview.md)
- [Konfigurere indstillinger for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>SKU/abonnementslicenser

Før du går i gang, skal du [bekræfte Microsoft 365 dit](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) abonnement og eventuelle tilføjelser. For at få adgang til og bruge slutpunkts-DLP-funktionalitet skal du have et af disse abonnementer eller tilføjelser.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 overholdelse af regler og standarder
- Microsoft 365 A5 overholdelse af regler og standarder
- Microsoft 365 E5 beskyttelse og styring af oplysninger
- Microsoft 365 A5 beskyttelse og styring af oplysninger

Du kan finde detaljerede [licenseringsvejledning Microsoft 365 vejledning i licensering for & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- Din organisation skal have licens til Endpoint DLP
- Dine enheder skal køre i Windows 10 x64 build 1809 eller nyere.
- Enheden skal have antimalwareklientversion 4.18.2101.9 eller nyere. Kontrollér din aktuelle version ved at **Windows Sikkerhed** appen, vælge **ikonet Indstillinger** og derefter vælge **Om**.


### <a name="permissions"></a>Tilladelser

Data fra Slutpunkt DLP kan vises i [Aktivitetsoversigt](data-classification-activity-explorer.md). Der er syv roller, der giver tilladelse til Aktivitetsstifinder. Den konto, du bruger til at få adgang til dataene, skal være medlem af en af dem.

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Dataadministrator for overholdelse af regler og standarder
- Global læser
- Sikkerhedslæser
- Rapportlæser

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper i forhåndsvisning

Eksempelvisningen har roller og rollegrupper, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over de Microsoft Information Protection (MIP)-roller, der er i forhåndsvisning. Du kan få mere at vide om [dem under Roller i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administratoren for informationsbeskyttelse
- Information Protection-analytiker
- Information Protection Investigator
- Information Protection Reader

Her er en liste over MIP-rollegrupper, der er i forhåndsvisning. Du kan få mere at vide om [dette under Rollegrupper i & Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Beskyttelse af oplysninger
- Administratorer for informationsbeskyttelse
- Information Protection-analytikere
- Beskyttelse af oplysninger
- Læsere til informationsbeskyttelse

### <a name="overall-installation-workflow"></a>Overordnet installationsarbejdsproces

Implementering af Microsoft Overholdelsesudvidelse er en proces i flere faser. Du kan vælge at installere på én computer ad gangen eller bruge Microsoft Endpoint Manager eller Gruppepolitik til installationer i hele organisationen.

1. [Gør dine enheder klar](#prepare-your-devices).
2. [Grundlæggende konfiguration af egenvært på en enkelt computer](#basic-setup-single-machine-selfhost)
3. [Installér ved hjælp Microsoft Endpoint Manager](#deploy-using-microsoft-endpoint-manager)
4. [Installér ved hjælp Gruppepolitik](#deploy-using-group-policy)
5. [Test udvidelse](#test-the-extension)
6. [Brug administrationsdashboardet til vigtige beskeder til at få vist Chrome DLP-beskeder](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [Visning af Chrome DLP-data i Aktivitetsoversigt](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>Forbered infrastruktur

Hvis du udruller Microsoft-overholdelsesudvidelsen på alle de overvågede Windows 10-enheder, skal du fjerne Google Chrome fra de ikke-tilladte apps og lister over ikke-tilladte browsere. Du kan få mere at vide [under Ikke-tilladte browsere](dlp-configure-endpoint-settings.md#unallowed-browsers). Hvis du kun ruller den ud til nogle få enheder, kan du lade Chrome blive på listerne over apps, der ikke er tilladt, eller om du ikke må bruge den. Microsoft Overholdelsesudvidelsen tilsidesætter begrænsningerne for begge lister for de computere, hvor den er installeret.

### <a name="prepare-your-devices"></a>Forbered dine enheder

1. Brug fremgangsmåderne i disse emner til at onboarde dine enheder:
    1. [Kom i gang med forebyggelse af datatab på slutpunkt](endpoint-dlp-getting-started.md)
    1. [Onboarding Windows 10 og Windows 11 enheder](device-onboarding-overview.md)
    1. [Konfigurere indstillinger for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>Grundlæggende konfiguration af egenvært på en enkelt computer

Dette er den anbefalede metode.

1. Log på den Windows 10 computer, hvor du vil installere Microsoft Overholdelsesudvidelse på, og kør dette PowerShell-script som administrator.

   ```powershell
   Get-Item -path "HKLM:\SOFTWARE\Microsoft\Windows Defender\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
   ```

2. Gå til [Microsoft Overholdelsesudvidelse - Chrome Webshop (google.com)](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).

3. Installér udvidelsen ved at følge vejledningen på Chrome Webshop side.

### <a name="deploy-using-microsoft-endpoint-manager"></a>Installér ved hjælp Microsoft Endpoint Manager

Brug denne konfigurationsmetode til installationer i hele organisationen.

##### <a name="enabling-required-registry-value-via-microsoft-endpoint-manager"></a>Aktivering af påkrævet registreringsdatabaseværdi via Microsoft Endpoint Manager

1. Opret et PowerShell-script med følgende indhold:

    ```powershell
    Get-Item -path "HKLM:\SOFTWARE\Microsoft\Windows Defender\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

2. Log på [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com).

3. Gå til **EnhederScripts** > , og vælg **Tilføj**.

4. Gå til placeringen for det script, der blev oprettet, når du bliver bedt om det.

5. Vælg følgende indstillinger:
    1. Kør dette script ved hjælp af legitimationsoplysningerne, der er logget på: NEJ
    1. Gennemtving kontrol af scriptsignatur: NEJ
    1. Kør script i 64-bit PowerShell-vært: JA

6. Vælg de rette enhedsgrupper, og anvend politikken.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>Microsoft Endpoint Manager gennemtving installationstrin

Før du føjer Microsoft-udvidelse til listen over force-installerede udvidelser, er det vigtigt at ingest the Chrome ADMX. Trin til denne proces i Microsoft Endpoint Manager er dokumenteret af Google: [Administrer Chrome Browser med Microsoft Intune – Hjælp til Google Chrome Enterprise](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 Når DU har indlastet ADMX, kan nedenstående trin følges for at oprette en konfigurationsprofil for denne udvidelse.

1. Log på Microsoft Endpoint Manager Administration (https://endpoint.microsoft.com).

2. Gå til Konfigurationsprofiler.

3. Vælg **Opret profil**.

4. Vælg **Windows 10** som platform.

5. Vælg **Brugerdefineret** som profiltype.

6. Vælg **Indstillinger** fane.

7. Vælg **Tilføj**.

8. Angiv følgende politikoplysninger.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    Datatype: `String`<br/>
    Værdi: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. Klik på Opret.

### <a name="deploy-using-group-policy"></a>Installér ved hjælp Gruppepolitik

Hvis du ikke vil bruge en microsoft-Microsoft Endpoint Manager, kan du bruge gruppepolitikker til at installere Microsoft Overholdelsesudvidelse i hele organisationen

1. Dine enheder skal kunne administreres via Gruppepolitik, og du skal importere alle Chrome ADMX'er i Gruppepolitik Central Store. Få mere at vide under [Sådan opretter og administrerer du den centrale Store til Gruppepolitik administrative skabeloner i Windows](/troubleshoot/windows-client/group-policy/create-and-manage-central-store).

2. Opret et PowerShell-script ved hjælp af denne PowerShell-kommando:

    ```powershell
    Get-Item -path "HKLM:\SOFTWARE\Microsoft\Windows Defender\Miscellaneous Configuration" | New-ItemProperty -Name DlpDisableBrowserCache -Value 0 -Force
    ```

3. Åbn Gruppepolitik **administrationskonsollen,** og gå til din organisationsenhed ( OU).

4. Højreklik, og vælg Opret **et gruppepolitikobjekt for dette domæne, og sammenkæd det her**. Når du bliver bedt om det, skal du tildele dette gruppepolitikobjekt et beskrivende navn og afslutte oprettelsen af det.

5. Højreklik på gruppepolitikobjektet, og vælg **Rediger**.

6. Gå til **ComputerKonfigurationPræferencerKontrolpanel** >  >  **Indstillinger** >  **Planlagte opgaver**.

7. Opret en ny øjeblikkelig opgave ved at vælge Højreklik og vælge **NewImmediate** >  **Task (mindst Windows 7)**.

8. Navngive opgaven & beskrivelse.

9. Vælg den tilsvarende konto for at køre den øjeblikkelige opgave, f.eks. NT Authority

10. Vælg **Kør med højeste rettigheder**.

11. Konfigurer politikken for Windows 10.

12. På fanen **Handlinger** skal du vælge handlingen **Start et program**.

13. Angiv stien til det program/script, der blev oprettet i trin 1.

14. Vælg **Anvend**.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>Tilføjelse af Chrome-udvidelsen til ForceInstall-listen

1. I administrationseditoren Gruppepolitik du gå til din OU.

2. Udvid følgende sti **Computer/** BrugerkonfigurationPoliciesAdministrative  > **skabelonerKlassiske** >  >  **administrative** >  **skabelonerGoogleGoogle** >  **ChromeExtensions** > . Denne sti kan variere afhængigt af din konfiguration.

3. Vælg **Konfigurer listen over tving-installerede udvidelser**.

4. Højreklik, og vælg **Rediger**.

5. Vælg **Aktiveret**.

6. Vælg **Vis**.

7. Tilføj **følgende** post under Værdi: `echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. Vælg **OK og** derefter **Anvend**.

### <a name="test-the-extension"></a>Test udvidelse

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>Upload til skytjeneste eller adgang fra ikke-tilladte browsere Sky Egress

1. Opret eller få fat i et følsomt element, og prøv at overføre en fil til et af organisationens begrænsede tjenestedomæner. De følsomme data skal matche en af [vores indbyggede](sensitive-information-type-entity-definitions.md) typer af følsomme oplysninger eller en af organisationens typer af følsomme oplysninger. Du bør få en DLP toast-meddelelse på den enhed, du tester fra, der viser, at denne handling ikke er tilladt, når filen er åben.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>Test af andre DLP-scenarier i Chrome

Nu hvor du har fjernet Chrome fra listen over ikke-tilladte browsere/apps, kan du teste nedenstående scenarier for at bekræfte, at funktionaliteten opfylder din organisations krav:

- Kopiere data fra et følsomt element til et andet dokument ved hjælp af Udklipsholder
  - Hvis du vil teste, skal du åbne en fil, der er beskyttet mod kopiér, til udklipsholderhandlinger i Chrome-browseren og forsøge at kopiere data fra filen.
  - Forventet resultat: En DLP-toastmeddelelse, der viser, at denne handling ikke er tilladt, når filen er åben.
- Udskrive et dokument
  - Hvis du vil teste, skal du åbne en fil, der er beskyttet mod udskriftshandlinger i Chrome-browseren, og forsøge at udskrive filen.
  - Forventet resultat: En DLP-toastmeddelelse, der viser, at denne handling ikke er tilladt, når filen er åben.
- Kopiér til medier, der kan fjernes via USB
  - Hvis du vil teste, skal du prøve at gemme filen på et medielager, der kan fjernes.
  - Forventet resultat: En DLP-toastmeddelelse, der viser, at denne handling ikke er tilladt, når filen er åben.
- Kopiér til netværksshare
  - Hvis du vil teste, skal du prøve at gemme filen på et netværksshare.
  - Forventet resultat: En DLP-toastmeddelelse, der viser, at denne handling ikke er tilladt, når filen er åben.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>Brug administrationsdashboardet til vigtige beskeder til at få vist Chrome DLP-beskeder

1. Åbn siden **forebyggelse af** datatab i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> vælg **Beskeder**.

2. Se procedurerne i Sådan konfigurerer og får du vist beskeder [for dine DLP-politikker for](dlp-configure-view-alerts-policies.md) at få vist beskeder for dine Slutpunkt DLP-politikker.

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>Visning af Chrome DLP-data i Aktivitetsoversigt

1. Åbn siden [Dataklassificering](https://compliance.microsoft.com/dataclassification?viewid=overview) for dit <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">domæne i Microsoft 365 Overholdelsescenter</a> vælg **Aktivitetsstifinder**.

2. Se procedurerne i Introduktion til [Aktivitetsstifinder for at](data-classification-activity-explorer.md) få adgang til og filtrere alle data til dine slutpunktsenheder.

   > [!div class="mx-imgBorder"]
   > ![Filter til aktivitetsstifinder til slutpunktsenheder.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

1. Incognito-tilstand understøttes ikke og skal deaktiveres.

## <a name="next-steps"></a>Næste trin

Nu hvor du har onboardede enheder og kan få vist aktivitetsdata i Aktivitetsoversigt, er du klar til at gå videre til næste trin, hvor du opretter DLP-politikker, der beskytter dine følsomme elementer.

- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md)

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab på slutpunkt](endpoint-dlp-learn-about.md)
- [Brug af forebyggelse af datatab på slutpunkt](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Introduktion til Aktivitetsstifinder](data-classification-activity-explorer.md)
- [Microsoft Defender til Slutpunkt](/windows/security/threat-protection/)
- [Onboardingværktøjer og metoder til Windows 10 computere](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Enheder, der er forbundet til Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
