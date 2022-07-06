---
title: Kom i gang med Microsoft Purview-udvidelsen
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
description: Forbered og udrul Microsoft Purview-udvidelsen.
ms.openlocfilehash: 9593b75ea9bb858e9cd770ec4f40f4e6d7667a2e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622937"
---
# <a name="get-started-with-microsoft-purview-extension"></a>Kom i gang med Microsoft Purview-udvidelsen

Brug disse procedurer til at udrulle Microsoft Purview-udvidelsen.

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil bruge Microsoft Purview Extension, skal enheden være onboardet i slutpunktet DLP. Gennemse disse artikler, hvis du ikke kender DLP eller slutpunkt DLP

- [Få mere at vide om Microsoft Purview-udvidelsen](dlp-chrome-learn-about.md)
- [Få mere at vide om Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Opret en DLP-politik ud fra en skabelon](create-a-dlp-policy-from-a-template.md)
- [Få mere at vide om forebyggelse af datatab for slutpunkter](endpoint-dlp-learn-about.md)
- [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)
- [Onboardingværktøjer og -metoder til Windows 10 enheder](device-onboarding-overview.md)
- [Konfigurer indstillinger for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)
- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)

### <a name="skusubscriptions-licensing"></a>LICENSER TIL SKU/abonnementer

Før du kommer i gang, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1) og eventuelle tilføjelsesprogrammer. Hvis du vil have adgang til og bruge Endpoint DLP-funktionalitet, skal du have et af disse abonnementer eller tilføjelsesprogrammer.

- Microsoft 365 E5
- Microsoft 365 A5 (EDU)
- Microsoft 365 E5 overholdelse af angivne standarder
- Microsoft 365 A5 overholdelse af angivne standarder
- Microsoft 365 E5 beskyttelse og styring af oplysninger
- Microsoft 365 A5 beskyttelse og styring af oplysninger

Du kan finde en detaljeret licensvejledning i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

- Din organisation skal have licens til Endpoint DLP
- Dine enheder skal køre Windows 10 x64 build 1809 eller nyere.
- Enheden skal have En Antimalware-klientversion 4.18.2202.x eller nyere. Kontrollér din aktuelle version ved at åbne **Windows Sikkerhed** app, vælge ikonet **Indstillinger** og derefter vælge **Om**.


### <a name="permissions"></a>Tilladelser

Data fra Slutpunkt DLP kan ses i [Aktivitetsoversigt](data-classification-activity-explorer.md). Der er syv roller, der giver tilladelse til aktivitetsoversigten. Den konto, du bruger til at få adgang til dataene, skal være medlem af en hvilken som helst af dem.

- Global administrator
- Overholdelsesadministrator
- Sikkerhedsadministrator
- Administrator af overholdelsesdata
- Global læser
- Sikkerhedslæser
- Rapportlæser

#### <a name="roles-and-role-groups-in-preview"></a>Roller og rollegrupper som prøveversion

Der er roller og rollegrupper som prøveversion, som du kan teste for at finjustere dine adgangskontrolelementer.

Her er en liste over relevante roller, der findes som prøveversion. Hvis du vil vide mere om dem, skal du se [Roller i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Administration
- Information Protection analytiker
- Information Protection investigator
- Information Protection-læser

Her er en liste over relevante rollegrupper, der findes som prøveversion. Du kan få mere at vide om under [Rollegrupper i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection administratorer
- Information Protection analytikere
- Information Protection efterforskere
- Information Protection læsere

### <a name="overall-installation-workflow"></a>Overordnet installationsarbejdsproces

Udrulning af udvidelsen er en flerfaset proces. Du kan vælge at installere på én computer ad gangen eller bruge Microsoft Endpoint Manager eller Gruppepolitik til udrulninger i hele organisationen.

1. [Forbered dine enheder](#prepare-your-devices).
2. [Grundlæggende konfiguration af selfhost for enkelt maskine](#basic-setup-single-machine-selfhost)
3. [Udrul ved hjælp af Microsoft Endpoint Manager](#deploy-using-microsoft-endpoint-manager)
4. [Udrul ved hjælp af Gruppepolitik](#deploy-using-group-policy)
5. [Test udvidelsen](#test-the-extension)
6. [Brug Dashboard til administration af beskeder til at få vist Chrome DLP-beskeder](#use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts)
7. [Visning af Chrome DLP-data i Aktivitetsoversigt](#viewing-chrome-dlp-data-in-activity-explorer)

### <a name="prepare-infrastructure"></a>Forbered infrastruktur

Hvis du udruller udvidelsen til alle dine overvågede Windows 10 enheder, skal du fjerne Google Chrome fra de ikke-tilladte app- og ikke-tilladte browserlister. Du kan få flere oplysninger under [Ikke-tilladte browsere](dlp-configure-endpoint-settings.md#unallowed-browsers). Hvis du kun udruller den til nogle få enheder, kan du lade Chrome være på de ikke-tilladte browser- eller ikke-tilladte applister. Udvidelsen tilsidesætter begrænsningerne for begge lister for de computere, hvor den er installeret.

### <a name="prepare-your-devices"></a>Forbered dine enheder

1. Brug procedurerne i disse emner til at onboarde dine enheder:
    1. [Kom i gang med forebyggelse af datatab forebyggelse af datatab ved slutpunkt](endpoint-dlp-getting-started.md)
    1. [Onboarding af Windows 10 og Windows 11 enheder](device-onboarding-overview.md)
    1. [Konfigurer indstillinger for enhedsproxy og internetforbindelse for Information Protection](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection)

### <a name="basic-setup-single-machine-selfhost"></a>Grundlæggende konfiguration af selfhost for enkelt maskine

Dette er den anbefalede metode.

1. Gå til [Microsoft Purview Extension – Chrome Web Store (google.com)](https://chrome.google.com/webstore/detail/microsoft-compliance-exte/echcggldkblhodogklpincgchnpgcdco).

2. Installér udvidelsen ved hjælp af instruktionerne på siden Chrome Web Store.

### <a name="deploy-using-microsoft-endpoint-manager"></a>Udrul ved hjælp af Microsoft Endpoint Manager

Brug denne konfigurationsmetode til udrulninger i hele organisationen.

#### <a name="microsoft-endpoint-manager-force-install-steps"></a>Trin til gennemtving installation af Microsoft Endpoint Manager

Før du føjer udvidelsen til listen over tving installerede udvidelser, er det vigtigt at indtage Chrome ADMX. Trin til denne proces i Microsoft Endpoint Manager er dokumenteret af Google: [Administrer Chrome-browser med Microsoft Intune – Google Chrome Enterprise Hjælp](https://support.google.com/chrome/a/answer/9102677?hl=en#zippy=%2Cstep-ingest-the-chrome-admx-file-into-intune).

 Når ADMX er blevet indsat, kan du følge nedenstående trin for at oprette en konfigurationsprofil for denne udvidelse.

1. Log på Microsoft Endpoint Manager Administration Center (https://endpoint.microsoft.com).

2. Gå til Konfigurationsprofiler.

3. Vælg **Opret profil**.

4. Vælg **Windows 10** som platform.

5. Vælg **Brugerdefineret** som profiltype.

6. Vælg fanen **Indstillinger** .

7. Vælg **Tilføj**.

8. Angiv følgende politikoplysninger.

    OMA-URI: `./Device/Vendor/MSFT/Policy/Config/Chrome~Policy~googlechrome~Extensions/ExtensionInstallForcelist`<br/>
    Datatype: `String`<br/>
    Værdi: `<enabled/><data id="ExtensionInstallForcelistDesc" value="1&#xF000; echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx"/>`

9. Klik på Opret.

### <a name="deploy-using-group-policy"></a>Udrul ved hjælp af Gruppepolitik

Hvis du ikke vil bruge Microsoft Endpoint Manager, kan du bruge gruppepolitikker til at installere udvidelsen på tværs af organisationen.

#### <a name="adding-the-chrome-extension-to-the-forceinstall-list"></a>Tilføjelse af Chrome-udvidelsen til ForceInstall-listen

1. I Gruppepolitik Management Editor skal du navigere til din OU.

2. Udvid følgende sti **Konfigurationspolitikker** >  for  > **computer/bruger****Administrative skabeloner** > **Klassiske administrative skabeloner** > **Google** > **Chrome-udvidelser** > . Denne sti kan variere afhængigt af konfigurationen.

3. Vælg **Konfigurer listen over tving installerede udvidelser**.

4. Højreklik, og vælg **Rediger**.

5. Vælg **Aktiveret**.

6. Vælg **Vis**.

7. Tilføj følgende post under **Værdi**: `echcggldkblhodogklpincgchnpgcdco;https://clients2.google.com/service/update2/crx`

8. Vælg **OK** og derefter **Anvend**.

### <a name="test-the-extension"></a>Test udvidelsen

#### <a name="upload-to-cloud-service-or-access-by-unallowed-browsers-cloud-egress"></a>Upload til cloudtjenesten, eller få adgang af ikke-tilladte browsere Cloud Egress

1. Opret eller hent et følsomt element, og prøv at uploade en fil til et af organisationens tjenestedomæner med begrænset adgang. De følsomme data skal stemme overens med en af vores indbyggede [typer følsomme oplysninger](sensitive-information-type-entity-definitions.md) eller en af organisationens følsomme informationstyper. Du bør få en DLP-toastbesked på den enhed, du tester fra, der viser, at denne handling ikke er tilladt, når filen er åben.

#### <a name="testing-other-dlp-scenarios-in-chrome"></a>Test af andre DLP-scenarier i Chrome

Nu, hvor du har fjernet Chrome fra listen over ikke-tilladte browsere/apps, kan du teste scenarierne nedenfor for at bekræfte, at funktionsmåden opfylder organisationens krav:

- Kopiér data fra et følsomt element til et andet dokument ved hjælp af Udklipsholder
  - Hvis du vil teste den, skal du åbne en fil, der er beskyttet mod kopiering til udklipsholder, i Chrome-browseren og forsøge at kopiere data fra filen.
  - Forventet resultat: En DLP-toastbesked, der viser, at denne handling ikke er tilladt, når filen er åben.
- Udskriv et dokument
  - Hvis du vil teste, skal du åbne en fil, der er beskyttet mod udskrivningshandlinger i Chrome-browseren, og forsøge at udskrive filen.
  - Forventet resultat: En DLP-toastbesked, der viser, at denne handling ikke er tilladt, når filen er åben.
- Kopiér til fjernbart USB-medie
  - Prøv at gemme filen på et medielager, der kan fjernes, for at teste det.
  - Forventet resultat: En DLP-toastbesked, der viser, at denne handling ikke er tilladt, når filen er åben.
- Kopiér til netværksshare
  - Prøv at gemme filen på et netværksshare for at teste det.
  - Forventet resultat: En DLP-toastbesked, der viser, at denne handling ikke er tilladt, når filen er åben.

### <a name="use-the-alerts-management-dashboard-to-viewing-chrome-dlp-alerts"></a>Brug Dashboard til administration af beskeder til at få vist Chrome DLP-beskeder

1. Åbn siden **Forebyggelse af datatab** i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>, og vælg **Beskeder**.

2. Se procedurerne i [Sådan konfigurerer og får du vist beskeder for dine DLP-politikker for](dlp-configure-view-alerts-policies.md) at få vist beskeder for dine DLP-politikker for slutpunkter.

### <a name="viewing-chrome-dlp-data-in-activity-explorer"></a>Visning af Chrome DLP-data i Aktivitetsoversigt

1. Åbn [siden Dataklassificering](https://compliance.microsoft.com/dataclassification?viewid=overview) for dit domæne i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>, og vælg **Aktivitetsoversigt**.

2. Se procedurerne i [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md) for at få adgang til og filtrere alle dataene til dine slutpunktsenheder.

   > [!div class="mx-imgBorder"]
   > ![activity explorer-filter for slutpunktsenheder.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)

### <a name="known-issues-and-limitations"></a>Kendte problemer og begrænsninger

1. Inkognitotilstand understøttes ikke og skal deaktiveres.

## <a name="next-steps"></a>Næste trin

Nu, hvor du har onboardede enheder og kan få vist aktivitetsdataene i Aktivitetsoversigt, er du klar til at gå videre til dit næste trin, hvor du opretter DLP-politikker, der beskytter dine følsomme elementer.

- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)

## <a name="see-also"></a>Se også

- [Få mere at vide om forebyggelse af datatab ved slutpunkt](endpoint-dlp-learn-about.md)
- [Brug forebyggelse af datatab ved slutpunkt](endpoint-dlp-using.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md)
- [Kom i gang med Aktivitetsoversigt](data-classification-activity-explorer.md)
- [Microsoft Defender for Endpoint](/windows/security/threat-protection/)
- [Onboardingværktøjer og -metoder til Windows 10 maskiner](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD tilsluttede enheder](/azure/active-directory/devices/concept-azure-ad-join)
- [Download den nye Microsoft Edge baseret på Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
