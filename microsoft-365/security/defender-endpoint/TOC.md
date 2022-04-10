# [Microsoft Defender for Endpoint](index.yml)

## [Oversigt]()
### [Hvad er Microsoft Defender for Endpoint?](microsoft-defender-endpoint.md)
### [Sammenlign Defender for Endpoint Plan 1 med Plan 2](defender-endpoint-plan-1-2.md)
### [Minimumskrav](minimum-requirements.md)
### [Nyheder i Microsoft Defender for Endpoint](whats-new-in-microsoft-defender-endpoint.md)
### [Visningsfunktioner](preview.md)
### [Datalagring og beskyttelse af personlige oplysninger](data-storage-privacy.md)
### [Oversigt over Microsoft Defender Security Center](use.md)
### [Defender for Endpoint Plan 1]()
#### [Oversigt](defender-endpoint-plan-1.md)
#### [Installation og konfiguration](mde-p1-setup-configuration.md)
#### [Introduktion](mde-plan1-getting-started.md)
#### [Vedligeholdelse og handlinger](mde-p1-maintenance-operations.md)
### [Microsoft Defender for Endpoint for US Government-kunder](gov.md)
### [Microsoft Defender for Endpoint på ikke-Windows-platforme](non-windows.md)


## [Evaluer funktioner](evaluation-lab.md)

## [Plan for udrulning](deployment-strategy.md)

## [Udrulningsvejledning]()
### [Udrulningsfaser](deployment-phases.md)
### [Fase 1: Forbered](prepare-deployment.md)
### [Fase 2: Konfigurer](production-deployment.md)
### [Fase 3: Onboard]()
#### [Oversigt over onboarding](onboarding.md)
#### [Udrulningsringe](deployment-rings.md)
#### [Onboarding ved hjælp af Microsoft Endpoint Konfigurationsstyring](onboarding-endpoint-configuration-manager.md)
#### [Onboarding ved hjælp af Microsoft Endpoint Manager](onboarding-endpoint-manager.md)

## [Overførselsvejledninger](migration-guides.md)
### [Flyt til Defender for Endpoint](switch-to-mde-overview.md)
#### [Fase 1: Forbered](switch-to-mde-phase-1.md)
#### [Fase 2: Installation](switch-to-mde-phase-2.md)
#### [Fase 3: Onboard](switch-to-mde-phase-3.md)
#### [Fejlfinding](switch-to-mde-troubleshooting.md)
### [Administrer Defender for Endpoint efter overførsel](manage-mde-post-migration.md)
#### [Brug Intune (anbefales)](manage-mde-post-migration-intune.md)
#### [Brug Konfigurationsstyring](manage-mde-post-migration-configuration-manager.md)
#### [Brug Gruppepolitik](manage-mde-post-migration-group-policy-objects.md)
#### [Brug PowerShell, WMI eller MPCmdRun.exe](manage-mde-post-migration-other-tools.md)
#### [Server-migreringsscenarier](server-migration.md)

## [Konfigurer og onboard enheder]()
### [Onboard enheder, og konfigurer Microsoft Defender for Endpoint-funktioner](onboard-configure.md)


### [Microsoft Defender for Endpoint på Windows og Windows Server]()
#### [Onboardingværktøjer og -metoder til Windows-slutpunkter](configure-endpoints.md)
#### [Onboard Windows-enheder og Windows Servers]()

##### [Onboard tidligere versioner af Windows](onboard-downlevel.md)


##### [Onboard Windows-enheder og Windows Servers]()
###### [Onboard Windows Server 2012 R2, 2016, Halvårlig kanal, 2019 og 2022](configure-server-endpoints.md)
###### [Onboard Windows-enheder ved hjælp af et lokalt script](configure-endpoints-script.md)
###### [Onboard Windows-enheder ved hjælp af Gruppepolitik](configure-endpoints-gp.md)
###### [Onboard Windows-enheder ved hjælp af Microsoft Endpoint Konfigurationsstyring](configure-endpoints-sccm.md)
###### [Onboard Windows-enheder ved hjælp af værktøjer til administration af mobilenheder](configure-endpoints-mdm.md)
###### [Indbyggede VDI-enheder (Virtual Desktop Infrastructure)](configure-endpoints-vdi.md)
###### [Onboard Windows 10 enheder med flere sessioner i Windows Virtual Desktop](onboard-windows-multi-session-device.md)




#### [Integration med Microsoft Defender for Cloud](azure-server-integration.md)

#### [Onboard enheder uden internetadgang](onboard-offline-machines.md)
#### [Kør en registreringstest på en ny onboardet enhed](run-detection-test.md)
#### [Kør simulerede angreb på enheder](attack-simulations.md)
#### [Konfigurer indstillinger for proxy- og internetforbindelse](configure-proxy-internet.md)
#### [Opret en beskedregel for onboarding eller offboarding](onboarding-notification.md)



### [Microsoft Defender for Endpoint på andre operativsystemer]()
#### [Onboard ikke-Windows-enheder](configure-endpoints-non-windows.md)

#### [Microsoft Defender for Endpoint på macOS]()
##### [Oversigt over Microsoft Defender for Endpoint på macOS](microsoft-defender-endpoint-mac.md)
##### [Nyheder](mac-whatsnew.md)

##### [Udrul]()
###### [Microsoft Intune-baseret udrulning](mac-install-with-intune.md).
###### [JAMF Pro-baseret udrulning]()
####### [Udrulning af Microsoft Defender for Endpoint på macOS ved hjælp af Jamf Pro](mac-install-with-jamf.md)
####### [Log på Jamf Pro](mac-install-jamfpro-login.md)
####### [Konfigurer enhedsgrupper](mac-jamfpro-device-groups.md)
####### [Konfigurer politikker](mac-jamfpro-policies.md)
####### [Tilmeld enheder](mac-jamfpro-enroll-devices.md)

###### [Installation med et andet MDM-system (Mobile Device Management)](mac-install-with-other-mdm.md)
###### [Manuel udrulning](mac-install-manually.md)
##### [Opdater](mac-updates.md)

##### [Konfigurer]()
###### [Konfigurer og valider udeladelser](mac-exclusions.md)
###### [Angiv indstillinger](mac-preferences.md)
###### [Find og bloker potentielt uønskede programmer](mac-pua.md)
###### [Enhedsstyring]()
####### [Oversigt over enhedsstyring](mac-device-control-overview.md)
####### [SYLTEF-eksempler](mac-device-control-jamf.md)
####### [Intune eksempler](mac-device-control-intune.md)
###### [Planlæg scanninger](mac-schedule-scan.md)

##### [Fejlfinding]()
###### [Fejlfinding af installationsproblemer](mac-support-install.md)
###### [Fejlfinding af problemer med ydeevnen](mac-support-perf.md)
###### [Fejlfinding af forbindelse til skyen](troubleshoot-cloud-connect-mdemac.md)
###### [Fejlfinding af problemer med kerneudvidelse](mac-support-kext.md)
###### [Fejlfinding af licensproblemer](mac-support-license.md)

##### [Beskyttelse af personlige oplysninger](mac-privacy.md)
##### [Ressourcer](mac-resources.md)


#### [Microsoft Defender for Endpoint på Linux]()
##### [Oversigt over Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
##### [Nyheder](linux-whatsnew.md)
##### [Udrul]()
###### [Manuel udrulning](linux-install-manually.md)
###### [Puppet-baseret udrulning](linux-install-with-puppet.md)
###### [Ansible-baseret udrulning](linux-install-with-ansible.md)
###### [Udrul Defender for Endpoint på Linux med Chef](linux-deploy-defender-for-endpoint-with-chef.md)

##### [Opdater](linux-updates.md)

##### [Konfigurer]()
###### [Konfigurer og valider udeladelser](linux-exclusions.md)
###### [Statisk proxykonfiguration](linux-static-proxy-configuration.md)
###### [Angiv indstillinger](linux-preferences.md)
###### [Find og bloker potentielt uønskede programmer](linux-pua.md)
###### [Planlæg scanninger med Microsoft Defender for Endpoint på Linux](linux-schedule-scan-mde.md)
###### [Planlæg en opdatering af Microsoft Defender for Endpoint (Linux)](linux-update-MDE-Linux.md)


##### [Fejlfinding]()
###### [Fejlfinding af installationsproblemer](linux-support-install.md)
###### [Undersøg agentens tilstandsproblemer](health-status.md)
###### [Fejlfinding af problemer med forbindelse til skyen](linux-support-connectivity.md)
###### [Fejlfinding af problemer med RHEL 6-installation](linux-support-rhel.md)
###### [Fejlfinding af problemer med ydeevnen](linux-support-perf.md)
###### [Fejlfinding af problemer med manglende hændelser](linux-support-events.md)

##### [Beskyttelse af personlige oplysninger](linux-privacy.md)
##### [Ressourcer](linux-resources.md)

#### [Mobile Threat Defense]()
##### [Oversigt over Mobile Threat Defense](mtd.md)

##### [Microsoft Defender for Endpoint på Android]()
###### [Oversigt over Microsoft Defender for Endpoint på Android](microsoft-defender-endpoint-android.md)
###### [Nyheder](android-whatsnew.md)

###### [Udrul]()
####### [Installér Microsoft Defender for Endpoint på Android med Microsoft Intune](android-intune.md)

###### [Konfigurer]()
####### [Konfigurer Microsoft Defender for Endpoint på Android-funktioner](android-configure.md)
####### [Konfigurer Microsoft Defender for Endpoint-risikosignaler ved hjælp af politikker om beskyttelse af apps](android-configure-mam.md)

###### [Beskyttelse af personlige oplysninger]()
####### [Microsoft Defender for Endpoint på Android – oplysninger om beskyttelse af personlige oplysninger](android-privacy.md)

###### [Fejlfinding]()
####### [Fejlfinding af problemer](android-support-signin.md)

##### [Microsoft Defender for Endpoint på iOS]()
###### [Oversigt over Microsoft Defender for Endpoint på iOS](microsoft-defender-endpoint-ios.md)
###### [Nyheder](ios-whatsnew.md)

###### [Udrul]()
####### [Udrul Microsoft Defender for Endpoint på iOS via Intune-](ios-install.md)
####### [Udrul Microsoft Defender for Endpoint på iOS til enheder, der ikke er tilmeldt,](ios-install-unmanaged.md)

###### [Konfigurer iOS-funktioner](ios-configure-features.md)

###### [Ofte stillede spørgsmål og fejlfinding](ios-troubleshoot.md)

###### [Beskyttelse af personlige oplysninger](ios-privacy.md)


### [Administrer konfigurationsindstillinger for Microsoft Defender for Endpoint på enheder med Microsoft Endpoint Manager](security-config-management.md)

### [Fejlfinding af problemer med onboarding]()
#### [Fejlfinding af problemer under onboarding](troubleshoot-onboarding.md)
#### [Fejlfinding af problemer med abonnements- og portaladgang](troubleshoot-onboarding-error-messages.md)
#### [Fejlfinding af problemer med onboarding af styring af sikkerhedskonfigurations](troubleshoot-security-config-mgt.md)





### [Konfigurer portalindstillinger]()
#### [Konfigurer generelle indstillinger for Defender for Endpoint](preferences-setup.md)
#### [Generel]()
##### [Bekræft placeringen af datalageret, og opdater indstillingerne for dataopbevaring](data-retention-settings.md)
##### [Konfigurer beskedmeddelelser](configure-email-notifications.md)
##### [Konfigurer meddelelser om sikkerhedsrisiko](configure-vulnerability-email-notifications.md)
##### [Konfigurer avancerede funktioner](advanced-features.md)

#### [Tilladelser]()
##### [Brug grundlæggende tilladelser til at få adgang til portalen](basic-permissions.md)
##### [Administrer portaladgang ved hjælp af RBAC-](rbac.md)
###### [Opret og administrer roller](user-roles.md)
###### [Opret og administrer enhedsgrupper](machine-groups.md)
###### [Opret og administrer enhedsmærker](machine-tags.md)

#### [Regler]()
##### [Administrer undertrykkelsesregler](manage-suppression-rules.md)
##### [Opret indikatorer](manage-indicators.md)
###### [Opret indikatorer for filer](indicator-file.md)
###### [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)
###### [Opret indikatorer for certifikater](indicator-certificates.md)
###### [Administrer indikatorer](indicator-manage.md)
##### [Administrer automatiske filuploads](manage-automation-file-uploads.md)
##### [Administrer udeladelse af automatiseringsmapper](manage-automation-folder-exclusions.md)

#### [Enhedshåndtering]()
##### [Onboardingenheder](onboard-configure.md)
##### [offboardingenheder](offboard-machines.md)
##### [Sørg for, at dine enheder er konfigureret korrekt](configure-machines.md)
##### [Overvåg og øg onboarding af enheder](configure-machines-onboarding.md) 

#### [Konfigurer Microsoft Defender Security Center tidszoneindstillinger](time-settings.md)

## [Find trusler, og beskyt slutpunkter]()
### [Håndtering af trusler og sikkerhedsrisici]()
#### [Oversigt](next-gen-threat-and-vuln-mgt.md)
#### [Introduktion]()
##### [Tilladelser & forudsætninger](tvm-prerequisites.md)
##### [Platforme og funktioner til understøttede operativsystemer](tvm-supported-os.md)
##### [Tildel enhedsværdi](tvm-assign-device-value.md)
#### [Vurder dit sikkerhedsniveau]()
##### [Dashboardindsigt](tvm-dashboard-insights.md)
##### [Eksponeringsscore](tvm-exposure-score.md)
##### [Microsoft Secure Score til enheder](tvm-microsoft-secure-score-devices.md)
#### [Forbedr din sikkerhed, & reducer risikoen]()
##### [Adresser sikkerhedsanbefalinger](tvm-security-recommendation.md)
##### [Afhjælpning af sikkerhedsrisici](tvm-remediation.md)
##### [Undtagelser for sikkerhedsanbefalinger](tvm-exception.md)
##### [Plan for ophør af supportsoftware](tvm-end-of-support-software.md)
##### [Afhjælpning af zero-day-sårbarheder](tvm-zero-day-vulnerabilities.md)
#### [Forstå sikkerhedsrisici på dine enheder]()
##### [Softwarelager](tvm-software-inventory.md)
##### [Sårbarheder i min organisation](tvm-weaknesses.md)
##### [Tidslinje for begivenhed](threat-and-vuln-mgt-event-timeline.md)
##### [Rapport over følsomme enheder](tvm-vulnerable-devices-report.md)
##### [Gå på jagt efter eksponerede enheder](tvm-hunt-exposed-devices.md)

### [Enhedssøgning]()
#### [Oversigt over enhedssøgning](device-discovery.md)
#### [Konfigurer enhedssøgning](configure-device-discovery.md)
#### [Integration af Microsoft Defender til IoT](enable-microsoft-defender-for-iot-integration.md)
#### [Aktiver Integration af Corelight-data](corelight-integration.md)
#### [Ofte stillede spørgsmål om enhedssøgning](device-discovery-faq.md)

### [Enhedslager]()
#### [Enhedslager](machines-view-overview.md)
#### [Udelad enheder](exclude-devices.md)
#### [Begivenhedsflag på enhedens tidslinje](device-timeline-event-flag.md)
#### [Administrer enhedsgruppe og -mærker](machine-tags.md)

### [Netværksenheder](network-devices.md)

### [Rapportering af værtsfirewall i Microsoft Defender for Endpoint](host-firewall-reporting.md)

### [Reduktion af angrebsoverfladen]()
#### [Oversigt over reduktion af angrebsoverflade](overview-attack-surface-reduction.md)
#### [Regler for reduktion af angrebsoverflade]()
##### [Få mere at vide om ASR-regler](attack-surface-reduction.md)
##### [Udrulningsvejledning til reduktion af angrebsoverflade (ASR)]()
###### [Udrulningsoversigt til reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment.md)
###### [Planlæg udrulning af reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment-plan.md)
###### [Regler for testreduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-test.md)
###### [Aktiver regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-implement.md)
###### [Operationaliser regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-operationalize.md)
##### [Henvisning til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md)
##### [Aktivér ASR-regler for alternative konfigurationsmetoder](enable-attack-surface-reduction.md)
##### [Ofte stillede spørgsmål om reduktion af angrebsoverflade](attack-surface-reduction-faq.yml)
#### [Styret mappeadgang]()
##### [Beskyt mapper](controlled-folders.md)
##### [Evaluer styret mappeadgang](evaluate-controlled-folder-access.md)
##### [Aktivér styret mappeadgang](enable-controlled-folders.md)
##### [Tilpas styret mappeadgang](customize-controlled-folders.md)
#### [Exploit Protection]()
##### [Beskyt enheder mod misbrug](exploit-protection.md)
##### [Evaluering af Exploit Protection](evaluate-exploit-protection.md)
##### [Aktivér Exploit Protection](enable-exploit-protection.md)
##### [Tilpas Exploit Protection](customize-exploit-protection.md)
##### [Importer, eksporter og implementer konfigurationer af exploit protection](import-export-exploit-protection-emet-xml.md)
##### [Exploit protection-reference](exploit-protection-reference.md)
#### [Netværksbeskyttelse]()
##### [Beskyt dit netværk](network-protection.md)
##### [Evaluer netværksbeskyttelse](evaluate-network-protection.md)
##### [Slå netværksbeskyttelse til](enable-network-protection.md)

### Næste generations beskyttelse
#### [Oversigt over næste generations beskyttelse](next-generation-protection.md)
##### [Oversigt over Microsoft Defender Antivirus](microsoft-defender-antivirus-windows.md)
##### [Bedre sammen: Microsoft Defender Antivirus og Microsoft Defender for Endpoint](why-use-microsoft-defender-antivirus.md)
##### [Bedre sammen: Microsoft Defender Antivirus og Office 365](office-365-microsoft-defender-antivirus.md)
#### [Evaluer Microsoft Defender Antivirus](evaluate-microsoft-defender-antivirus.md)
#### [Konfigurere Microsoft Defender Antivirus-funktioner](configure-microsoft-defender-antivirus-features.md)
#### [Skybeskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md)
##### [Derfor skal skybeskyttelse være tændt](why-cloud-protection-should-be-on-mdav.md)
##### [Slå skybeskyttelse til](enable-cloud-protection-microsoft-defender-antivirus.md)
##### [Angive skybeskyttelsesniveauet](specify-cloud-protection-level-microsoft-defender-antivirus.md)
##### [Skybeskyttelse og indsendelse af eksempler](cloud-protection-microsoft-antivirus-sample-submission.md)
#### [Konfigurer og valider Microsoft Defender Antivirus netværksforbindelser](configure-network-connections-microsoft-defender-antivirus.md)
#### [Beskyt sikkerhedsindstillinger med manipulationsbeskyttelse](prevent-changes-to-security-settings-with-tamper-protection.md)
#### [Slå Bloker når den ses første gang til](configure-block-at-first-sight-microsoft-defender-antivirus.md)
#### [Konfigurer timeoutperioden for skyblokering](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)
#### [Konfigurer funktionsmåde-, heuristisk- og realtidsbeskyttelse](configure-protection-features-microsoft-defender-antivirus.md)
#### [Find og bloker potentielt uønskede programmer](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
#### [Aktivér og konfigurer Microsoft Defender Antivirus altid-aktive beskyttelse i Gruppepolitik](configure-real-time-protection-microsoft-defender-antivirus.md)
#### [Konfigurer afhjælpning af Microsoft Defender Antivirus registreringer](configure-remediation-microsoft-defender-antivirus.md)
#### [Konfigurer Microsoft Defender Antivirus-scanninger](schedule-antivirus-scans.md)
##### [Planlæg scanninger ved hjælp af Gruppepolitik](schedule-antivirus-scans-group-policy.md)
##### [Planlæg scanninger ved hjælp af PowerShell](schedule-antivirus-scans-powershell.md)
##### [Planlæg scanninger ved hjælp af WMI](schedule-antivirus-scans-wmi.md)
#### [Brug begrænset periodisk scanning i Microsoft Defender Antivirus](limited-periodic-scanning-microsoft-defender-antivirus.md)
#### [Kompatibilitet med andre sikkerhedsprodukter](microsoft-defender-antivirus-compatibility.md)
#### [Find navne på malwareregistrering til Microsoft Defender for Endpoint](find-defender-malware-name.md)

#### [Få dine antivirus- og antimalwareopdateringer](manage-updates-baselines-microsoft-defender-antivirus.md)
##### [Administrer kilderne til Microsoft Defender Antivirus beskyttelsesopdateringer](manage-protection-updates-microsoft-defender-antivirus.md)
##### [Administrer tidsplanen for, hvornår beskyttelsesopdateringer skal downloades og anvendes](manage-protection-update-schedule-microsoft-defender-antivirus.md)
##### [Administrer processen for gradvis udrulning af Microsoft Defender-opdateringer](manage-gradual-rollout.md)
##### [Konfigurer processen for gradvis udrulning af Microsoft Defender-opdateringer](configure-updates.md)
##### [Administrer Microsoft Defender Antivirus opdateringer og scanninger for slutpunkter, der er forældede](manage-outdated-endpoints-microsoft-defender-antivirus.md)
##### [Administrer begivenhedsbaserede gennemtvungne opdateringer](manage-event-based-updates-microsoft-defender-antivirus.md)
##### [Administrer opdateringer til mobilenheder og virtuelle maskiner (VMs)](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)

#### [Administrer Microsoft Defender Antivirus for din organisation](configuration-management-reference-microsoft-defender-antivirus.md)
##### [Brug Microsoft Endpoint Manager til at administrere Microsoft Defender Antivirus](use-intune-config-manager-microsoft-defender-antivirus.md)
##### [Brug indstillinger for Gruppepolitik til at administrere Microsoft Defender Antivirus](use-group-policy-microsoft-defender-antivirus.md)
##### [Brug PowerShell-cmdlet'er til at administrere Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)
##### [Brug Windows Management Instrumentation (WMI) til at administrere Microsoft Defender Antivirus](use-wmi-microsoft-defender-antivirus.md)
##### [Brug værktøjet mpcmdrun.exe til at administrere Microsoft Defender Antivirus](command-line-arguments-microsoft-defender-antivirus.md)
##### [Konfigurer de meddelelser, der vises på slutpunkter,](configure-notifications-microsoft-defender-antivirus.md)
##### [Angiv, om bruger kan ændre Microsoft Defender Antivirus-politikindstillinger lokalt](configure-local-policy-overrides-microsoft-defender-antivirus.md)
##### [Angiv, om bruger kan se eller interagere med Microsoft Defender Antivirus](prevent-end-user-interaction-microsoft-defender-antivirus.md)

#### [Udrul og rapportér om Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
##### [Udrul og aktivér Microsoft Defender Antivirus](deploy-microsoft-defender-antivirus.md)
##### [Udrulningsvejledning til Microsoft Defender Antivirus i et VDI-miljø (Virtual Desktop Infrastructure)](deployment-vdi-microsoft-defender-antivirus.md)
##### [Rapport om Microsoft Defender Antivirus](report-monitor-microsoft-defender-antivirus.md)

#### [Scanninger og afhjælpning](review-scan-results-microsoft-defender-antivirus.md)
##### [Konfigurer og kør scanninger efter behov Microsoft Defender Antivirus](run-scan-microsoft-defender-antivirus.md)
##### [Kør og gennemse resultaterne af en Microsoft Defender Offline scanning](microsoft-defender-offline.md)
##### [Konfigurer scanningsindstillinger for Microsoft Defender Antivirus](configure-advanced-scan-types-microsoft-defender-antivirus.md)
##### [Gendan filer i karantæne i Microsoft Defender Antivirus](restore-quarantined-files-microsoft-defender-antivirus.md)

#### [Microsoft Defender Antivirus udeladelser](configure-exclusions-microsoft-defender-antivirus.md)
##### [Udeladelser baseret på filtypenavn og mappeplacering](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
##### [Udeladelser for filer, der åbnes af processer](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md)
##### [Udeladelser for Windows Server-](configure-server-exclusions-microsoft-defender-antivirus.md)
##### [Almindelige fejl at undgå](common-exclusion-mistakes-microsoft-defender-antivirus.md)

#### Diagnosticering og ydeevne for Microsoft Defender Antivirus
##### [Rapporter om enhedens tilstand og overholdelse af angivne standarder](machine-reports.md)
##### [Fejlfinding af problemer med ydeevnen i forbindelse med beskyttelse i realtid](troubleshoot-performance-issues.md) 
##### [Fejlfinding af Microsoft Defender Antivirus-rapportering i Update Compliance](troubleshoot-reporting.md)
##### [Finjuster ydeevnen for Microsoft Defender Antivirus](tune-performance-defender-antivirus.md)

#### Fejlfinding af Microsoft Defender Antivirus
##### [Gennemse hændelseslogge og fejlkoder for at foretage fejlfinding af problemer med Microsoft Defender Antivirus](troubleshoot-microsoft-defender-antivirus.md)
##### [Fejlfinding af Microsoft Defender Antivirus under overførsel fra en tredjepartsløsning](troubleshoot-microsoft-defender-antivirus-when-migrating.md)

#### [Webbeskyttelse]()
##### [Oversigt over webbeskyttelse](web-protection-overview.md)
##### [Beskyttelse mod webtrusler]()
###### [Oversigt over beskyttelse mod webtrusler](web-threat-protection.md)
###### [Overvåge websikkerhed](web-protection-monitoring.md)
###### [Svar på webtrusler](web-protection-response.md)
##### [Filtrering af webindhold](web-content-filtering.md)

#### [Enhedsstyring]()
##### [Flytbar lagringsbeskyttelse](device-control-removable-storage-protection.md)
##### [Styring af adgang til flytbar lagring](device-control-removable-storage-access-control.md)
##### [Installation af enhed](mde-device-control-device-installation.md)
##### [Printerbeskyttelse til enhedsstyring](printer-protection.md)
##### [Rapporter om enhedsstyring](device-control-report.md)

#### [Blokering og opbevaring af funktionsmåder]()
##### [Blokering og opbevaring af funktionsmåder](behavioral-blocking-containment.md)
##### [blokering af klientfunktionsmåder](client-behavioral-blocking.md)
##### [Blokering af feedbackløkker](feedback-loop-blocking.md)


### [Adresser falske positive/negativer i Microsoft Defender for Endpoint](defender-endpoint-false-positives-negatives.md)


### [Administrer enhedskonfiguration]()

#### [Øg overholdelsen af sikkerhedsbaseline](configure-machines-security-baseline.md)
#### [Optimer udrulning af regler for reduktion af angrebsoverfladen og registreringer](configure-machines-asr.md)

## [Undersøg og reager på trusler]()
### [Slutpunktsregistrering og -svar]()
#### [Oversigt over slutpunktsregistrering og svar](overview-endpoint-detection-response.md)
#### [Dashboard til sikkerhedshandlinger](security-operations-dashboard.md)
#### [Indsend filer](admin-submissions-mde.md)
#### [Kø over hændelser]()
##### [Få vist og organiser hændelseskøer](view-incidents-queue.md)
##### [Administrer hændelser](manage-incidents.md)
##### [Undersøg hændelser](investigate-incidents.md)

#### [Beskedkøer]()
##### [Beskedkøer i Microsoft 365 Defender](alerts-queue-endpoint-detection-response.md)
##### [Få vist og organiser beskedkøer](alerts-queue.md)
##### [Gennemse beskeder](review-alerts.md)
##### [Administrer beskeder](manage-alerts.md)
##### [Undersøg beskeder](investigate-alerts.md)
##### [Undersøg filer](investigate-files.md)
##### [Undersøg enheder](investigate-machines.md)
##### [Undersøg en IP-adresse](investigate-ip.md)
##### [Undersøg et domæne](investigate-domain.md)
###### [Undersøg forbindelseshændelser, der opstår bag fremadrettet proxyer](investigate-behind-proxy.md)
##### [Undersøg en brugerkonto](investigate-user.md)

#### [Udføre svarhandlinger]()
##### [Udfør svarhandlinger på en enhed]()
###### [Svarhandlinger på enheder](respond-machine-alerts.md)
###### [Administrer mærker](respond-machine-alerts.md#manage-tags)
###### [Start en automatiseret undersøgelse](respond-machine-alerts.md#initiate-automated-investigation)
###### [Start en live-svarsession](respond-machine-alerts.md#initiate-live-response-session)
###### [Hent undersøgelsespakke](respond-machine-alerts.md#collect-investigation-package-from-devices)
###### [Kør antivirusscanning](respond-machine-alerts.md#run-microsoft-defender-antivirus-scan-on-devices)
###### [Begræns appudførelse](respond-machine-alerts.md#restrict-app-execution)
###### [Isoler enheder fra netværket](respond-machine-alerts.md#isolate-devices-from-the-network)
###### [Kontakt en trusselsekspert](respond-machine-alerts.md#consult-a-threat-expert)
###### [Kontrollér aktivitetsdetaljer i Handlingscenter](respond-machine-alerts.md#check-activity-details-in-action-center)

##### [Udfør svarhandlinger på en fil]()
###### [Svarhandlinger på filer](respond-file-alerts.md)
###### [Stop og sæt filer i karantæne i dit netværk](respond-file-alerts.md#stop-and-quarantine-files-in-your-network)
###### [Gendan fil fra karantæne](respond-file-alerts.md#restore-file-from-quarantine)
###### [Tilføje indikatorer for at blokere eller tillade en fil](respond-file-alerts.md#add-indicator-to-block-or-allow-a-file)
###### [Kontakt en trusselsekspert](respond-file-alerts.md#consult-a-threat-expert)
###### [Kontrollér aktivitetsdetaljer i Handlingscenter](respond-file-alerts.md#check-activity-details-in-action-center)
###### [Download eller indsaml fil](respond-file-alerts.md#download-or-collect-file)
###### [Dybdegående analyse](respond-file-alerts.md#deep-analysis)

#### [Få vist og godkend afhjælpningshandlinger](manage-auto-investigation.md)
##### [Få vist detaljer om og resultater af automatiserede undersøgelser](auto-investigation-action-center.md)

#### [Undersøg enheder ved hjælp af Direkte svar]()
##### [Undersøg enheder på enheder](live-response.md)
##### [Eksempler på kommandoen Direkte svar](live-response-command-examples.md)

#### [Brug følsomhedsmærkater til at prioritere hændelsesrespons](information-protection-investigation.md)

#### [Rapportering]()
##### [Power BI – Sådan bruger du API – eksempler](api-power-bi.md)
##### [Rapporter om trusselsbeskyttelse](threat-protection-reports.md)

### [Avanceret jagt]()
#### [Oversigt over avanceret jagt](advanced-hunting-overview.md)
#### [Forstå skemaet](advanced-hunting-schema-reference.md)
#### [DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)

### [Oversigt over Trusselsanalyse](threat-analytics.md)
#### [Læs analyserapporten](threat-analytics-analyst-reports.md)

### [EDR i bloktilstand](edr-in-block-mode.md)

### [Automatisk undersøgelse og svar (AIR)]()
#### [Oversigt over AIR](automated-investigations.md)
#### [Automatiseringsniveauer i AIR](automation-levels.md)
#### [Konfigurer AIR-funktioner](configure-automated-investigations-remediation.md)

### [Microsoft Threat Experts]()
#### [Oversigt over Microsoft Threat Experts](microsoft-threat-experts.md)
#### [Konfigurer og administrer Microsoft Threat Experts-funktioner](configure-microsoft-threat-experts.md)



## Reference
### [Forstå begreber om trusselsintelligens](threat-indicator-concepts.md)
### [Konfigurer integration med andre Microsoft-løsninger]()
#### [Konfigurer betinget adgang](configure-conditional-access.md)
#### [Konfigurer integration af Microsoft Defender for Cloud Apps](microsoft-cloud-app-security-config.md)
### [Administration og API'er]()
#### [Oversigt over administration og API'er](management-apis.md)
#### [Produktbemærkninger til API](api-release-notes.md)
#### [Microsoft Defender for Endpoint API]()
##### [Introduktion]()
###### [Microsoft Defender for Endpoint API-licens og -vilkår](api-terms-of-use.md)
###### [Få adgang til Microsoft Defender for Endpoint API'er](apis-intro.md)
###### [Hello World](api-hello-world.md)
###### [Få adgang med programkontekst](exposed-apis-create-app-webapp.md)
###### [Få adgang med brugerkontekst](exposed-apis-create-app-nativeapp.md)



##### [Microsoft Defender for Endpoint API-skema]()
###### [Understøttede Microsoft Defender for Endpoint API'er](exposed-apis-list.md)
###### [Almindelige REST API-fejlkoder](common-errors.md)
###### [Avanceret jagt](run-advanced-query-api.md)

###### [Besked]()
####### [Metoder og egenskaber for beskeder](alerts.md) 
####### [Angiv beskeder](get-alerts.md)
####### [Opret besked](create-alert-by-reference.md)
####### [Beskeder om batchopdatering](batch-update-alerts.md)
####### [Opdateringsbesked](update-alert.md)
####### [Få beskedoplysning efter id](get-alert-info-by-id.md)
####### [Få beskedrelaterede domæneoplysninger](get-alert-related-domain-info.md)
####### [Få beskedrelaterede filoplysninger](get-alert-related-files-info.md)
####### [Få beskedrelaterede IP-adresser](get-alert-related-ip-info.md)
####### [Få beskedrelaterede enhedsoplysninger](get-alert-related-machine-info.md)
####### [Få beskedrelaterede brugeroplysninger](get-alert-related-user-info.md)


###### [Vurdering af sårbarheder og sikre konfigurationer]()
####### [Eksporter bedømmelsesmetoder og egenskaber](get-assessment-methods-properties.md)
####### [Eksportér sikker konfigurationsvurdering](get-assessment-secure-config.md)
####### [Eksportér vurdering af softwarelager](get-assessment-software-inventory.md)
####### [Eksportér vurdering af softwaresikkerhedsrisici](get-assessment-software-vulnerabilities.md)

###### [Automatiseret undersøgelse]()
####### [Undersøgelsesmetoder og egenskaber](investigation.md)
####### [Angiv undersøgelse](get-investigation-collection.md)
####### [Hent undersøgelse](get-investigation-object.md)
####### [Start undersøgelse](initiate-autoir-investigation.md)

###### [Domæne]()
####### [Få domænerelaterede beskeder](get-domain-related-alerts.md)
####### [Hent domænerelaterede maskiner](get-domain-related-machines.md)
####### [Hent domænestatistik](get-domain-statistics.md)

###### [Filer]()
####### [Filmetoder og -egenskaber](files.md)
####### [Hent filoplysninger](get-file-information.md)
####### [Få filrelaterede beskeder](get-file-related-alerts.md)
####### [Hent filrelaterede maskiner](get-file-related-machines.md)
####### [Hent filstatistik](get-file-statistics.md)

###### [Indikatorer]()
####### [Metoder og egenskaber for indikatorer](ti-indicator.md)
####### [Angiv indikatorer](get-ti-indicators-collection.md)
####### [Indsend indikator](post-ti-indicator.md)
####### [Importér indikator](import-ti-indicators.md)
####### [Slet Indikator](delete-ti-indicator-by-id.md)

###### [IP]()
####### [Få IP-relaterede beskeder](get-ip-related-alerts.md)
####### [Hent IP-statistik](get-ip-statistics.md)

###### [Direkte svar-bibliotek]()
####### [Metoder og egenskaber for Direkte var-bibliotek](live-response-library-methods.md)
####### [Angiv biblioteksfiler](list-library-files.md)
####### [Upload til Direkte svar-bibliotek](upload-library.md)
####### [Slet fra bibliotek](delete-library.md)


###### [Maskine]()
####### [Metoder og egenskaber for maskiner](machine.md)
####### [Angiv maskiner](get-machines.md)
####### [Hent maskine efter id](get-machine-by-id.md)
####### [Hent brugere til logon](get-machine-log-on-users.md)
####### [Få maskinrelaterede beskeder](get-machine-related-alerts.md)
####### [Hent installeret software](get-installed-software.md)
####### [Få fundne sikkerhedsrisici](get-discovered-vulnerabilities.md)
####### [Få sikkerhedsanbefalinger](get-security-recommendations.md)
####### [Tilføj eller fjern maskintags](add-or-remove-machine-tags.md)
####### [Find maskiner efter IP](find-machines-by-ip.md)
####### [Find maskiner efter mærke](find-machines-by-tag.md)
####### [Få manglende KB'er](get-missing-kbs-machine.md)
####### [Angiv enhedsværdi](set-device-value.md)
####### [Opdater maskine](update-machine-method.md)



###### [Maskinhandling]()
####### [Metoder og egenskaber for maskinhandling](machineaction.md)
####### [Angiv maskinhandlinger](get-machineactions-collection.md)
####### [Hent maskinhandling](get-machineaction-object.md)
####### [Hent undersøgelsespakke](collect-investigation-package.md)
####### [Hent undersøgelsespakken SAS URI](get-package-sas-uri.md)
####### [Få Direkte svar-resultat](get-live-response-result.md)
####### [Isoler maskine](isolate-machine.md)
####### [Frigiv maskine fra isolation](unisolate-machine.md)
####### [Begræns appudførelse](restrict-code-execution.md)
####### [Fjern appbegrænsning](unrestrict-code-execution.md)
####### [Kør antivirusscanning](run-av-scan.md)
####### [Kør Direkte svar](run-live-response.md)
####### [offboard-maskine](offboard-machine-api.md)
####### [Stop og sæt fil i karantæne](stop-and-quarantine-file.md)
####### [Annuller maskinhandling](cancel-machine-action.md)

###### [Anbefaling]()
####### [Metoder og egenskaber for anbefaling](recommendation.md)
####### [Angiv alle anbefalinger](get-all-recommendations.md)
####### [Få anbefaling efter id](get-recommendation-by-id.md)
####### [Få anbefaling efter software](list-recommendation-software.md)
####### [Angiv maskiner efter anbefaling](get-recommendation-machines.md)
####### [Angiv sikkerhedsrisici efter anbefaling](get-recommendation-vulnerabilities.md)

###### [Afhjælpningsaktivitet]()
####### [Metoder og -egenskaber for afhjælpningsaktivitet](get-remediation-methods-properties.md)
####### [Få én afhjælpningsaktivitet efter id](get-remediation-one-activity.md)
####### [Angiv alle afhjælpningsaktiviteter](get-remediation-all-activities.md)
####### [Angiv eksponerede enheder for én afhjælpningsaktivitet](get-remediation-exposed-devices-activities.md)

###### [Score]()
####### [Scoremetoder og -egenskaber](score.md)
####### [Angiv over eksponeringsscore efter maskingruppe](get-machine-group-exposure-score.md)
####### [Få eksponeringsscore](get-exposure-score.md)
####### [Få sikker score på enhed](get-device-secure-score.md)

###### [Software]()
####### [Softwaremetoder og -egenskaber](software.md)
####### [Angiv software](get-software.md)
####### [Hent software efter id](get-software-by-id.md)
####### [Angiv softwareversionsdistribution](get-software-ver-distribution.md)
####### [Angiv maskiner efter software](get-machines-by-software.md)
####### [Angiv sikkerhedsrisici efter software](get-vuln-by-software.md)
####### [Få manglende KB'er](get-missing-kbs-software.md)

###### [Bruger]()
####### [Brugermetoder](user.md)
####### [Få brugerrelaterede beskeder](get-user-related-alerts.md)
####### [Hent brugerrelaterede maskiner](get-user-related-machines.md)

###### [Sikkerhedsrisici]()
####### [Metoder og egenskaber for sikkerhedsrisici](vulnerability.md)
####### [Angiv over sikkerhedsrisici](get-all-vulnerabilities.md)
####### [Angiv sikkerhedsrisici efter maskine og software](get-all-vulnerabilities-by-machines.md)
####### [Få sikkerhedsrisici efter id](get-vulnerability-by-id.md)
####### [Angiv over maskiner efter sikkerhedsrisiko](get-machines-by-vulnerability.md)

##### [Sådan bruges API'er – Eksempler]()
###### [Power Automate](api-microsoft-flow.md)
###### [Power BI](api-power-bi.md)
###### [Avanceret jagt ved hjælp af Python](run-advanced-query-sample-python.md)
###### [Avanceret jagt ved hjælp af PowerShell](run-advanced-query-sample-powershell.md)
###### [Brug af OData-forespørgsler](exposed-apis-odata-samples.md)


#### [Rå datastreaming-API]()
##### [Rå datastreaming](raw-data-export.md)
##### [Stream avancerede jagthændelser til Azure Events Hub](raw-data-export-event-hub.md)
##### [Stream avancerede jagthændelser til din lagerkonto](raw-data-export-storage.md)

#### [SIEM-integration]()
##### [Integrer SIEM-værktøjer med Microsoft Defender for Endpoint-](configure-siem.md)
##### [Fejlfinding af problemer med integration af SIEM-værktøjer](troubleshoot-siem.md)

#### [Partnere & API'er]()
##### [Partnerprogrammer](partner-applications.md)
##### [Forbundne programmer](connected-applications.md)
##### [API-stifinder](api-explorer.md)

#### [Rollebaseret adgangskontrol]()
##### [Administrer portaladgang ved hjælp af RBAC-](rbac.md)
##### [Opret og administrer roller](user-roles.md)
##### [Opret og administrer enhedsgrupper]()
###### [Brug af enhedsgrupper](machine-groups.md)
###### [Opret og administrer enhedsmærker](machine-tags.md)







### [MSSP-integration (Managed Security Service Provider)]()
#### [Konfigurer integration af administrerede sikkerhedsudbydere](configure-mssp-support.md)
#### [Understøttede udbydere af administrerede sikkerhedstjenester](mssp-list.md)
#### [Giv MSSP adgang til portalen](grant-mssp-access.md)
#### [Få adgang til MSSP-kundeportalen](access-mssp-portal.md)
#### [Konfigurer beskedmeddelelser](configure-mssp-notifications.md)
#### [Få adgang til partnerprogram](exposed-apis-create-app-partners.md)
#### [Hent beskeder fra kundelejeren](fetch-alerts-mssp.md)
#### [Mulighed for udbyder af administrerede sikkerhedstjenester](mssp-support.md)
### [Scenarier for partnerintegration]()
#### [Tekniske partnermuligheder](partner-integration.md)
#### [Bliv Microsoft Defender for Endpoint-partner](get-started-partner-integration.md)
### [Integrationer]()
#### [integrationer af Microsoft Defender for Endpoint](threat-protection-integration.md)
#### [Beskyt brugere, data og enheder med betinget adgang](conditional-access.md)
#### [Oversigt over integration af Microsoft Defender for Cloud Apps](microsoft-cloud-app-security-integration.md)

### [Oversigt over Informationsbeskyttelse i Windows]()
#### [Windows-integration](information-protection-in-windows-overview.md)

### [Få adgang til i Microsoft Defender for Endpoint Community Center](community.md)

### [Nyttige ressourcer](helpful-resources.md)

## [Fejlfinding]()
### [Fejlfinding af sensortilstand]()
#### [Kontrollér sensortilstand](check-sensor-status.md)
#### [Løs usunde sensorer](fix-unhealthy-sensors.md)
#### [Inaktive enheder](fix-unhealthy-sensors.md#inactive-devices)
#### [Forkert konfigurerede enheder](fix-unhealthy-sensors.md#misconfigured-devices)
#### [Gennemse sensorhændelser og -fejl på maskiner med Logbog](event-error-codes.md)

### [Fejlfinding af problemer med sensorens tilstand ved hjælp af Client Analyzer]()
#### [Oversigt over klientanalyse](overview-client-analyzer.md)
#### [Download og kør klientanalysen](download-client-analyzer.md)
#### [Kør klientanalysen på Windows](run-analyzer-windows.md)
#### [Kør klientanalysen på macOS eller Linux](run-analyzer-macos-linux.md)
#### [Dataindsamling til avanceret fejlfinding på Windows](data-collection-analyzer.md)
#### [Forstå HTML-analyserapporten](analyzer-report.md)
#### [Giv feedback om værktøjet til klientanalyse](analyzer-feedback.md)

 

### [Fejlfinding af problemer med tjenesten Microsoft Defender for Endpoint]()
#### [Fejlfinding af tjenesteproblemer](troubleshoot-mdatp.md)
#### [Kontakt support til Microsoft Defender for Endpoint](contact-support.md)

### [Fejlfinding af problemer med Direkte svar](troubleshoot-live-response.md)

### [Indsaml supportlogfiler ved hjælp af LiveAnalyzer](troubleshoot-collect-support-log.md)

### [Fejlfinding af problemer med reduktion af angrebsoverfladen]()
#### [Netværksbeskyttelse](troubleshoot-np.md)
#### [Regler for reduktion af angrebsoverflade](troubleshoot-asr.md)
#### [Regler for reduktion af angrebsoverfladen](migrating-asr-rules.md)

# [Microsoft 365 Defender-dokumenter]()
## [Microsoft 365 Defender](../defender/index.yml)
## [Defender for Office 365](../office-365-security/index.yml)
## [Defender for Identity](/defender-for-identity/)
## [Defender for Cloud Apps](/cloud-app-security/)
## [Defender for Business](../defender-business/index.yml)

