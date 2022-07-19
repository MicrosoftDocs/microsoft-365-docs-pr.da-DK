---
title: Reaktion på ransomware-angreb
description: Denne artikel indeholder en generel playbook til at reagere på ransomware-angreb.
search.appverid: MET150
author: nic-name
ms.author: noriordan
manager: dolmont
audience: ITPro
ms.topic: article
ms.date: 05/30/2022
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection: M365-security-compliance
f1.keywords: NOCSH
ms.openlocfilehash: a7c03947cc159ed9933854c9fd1041af63c3f55c
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/01/2022
ms.locfileid: "66858606"
---
# <a name="responding-to-ransomware-attacks"></a>Reaktion på ransomware-angreb

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Når du har mistanke om, at du var eller i øjeblikket er under et ransomware-angreb, skal du straks etablere sikker kommunikation med dit hændelsessvarteam. De kan udføre følgende svarfaser for at afbryde angrebet og afhjælpe skaden:

* Undersøgelse og indeslutning
* Udryddelse og genopretning

Denne artikel indeholder en generel playbook til at reagere på ransomware-angreb. Overvej at tilpasse de beskrevne trin og opgaver i denne artikel til din egen strategibog for sikkerhedshandlinger.
BEMÆRK! Du kan få oplysninger om forebyggelse af ransomware-angreb under [Beskyt hurtigt mod ransomware og afpresning](/security/compass/protect-against-ransomware).

## <a name="containment"></a>Indeslutning

Indeslutning og undersøgelse bør finde sted så samtidigt som muligt; Du skal dog fokusere på hurtigt at opnå indeslutning, så du har mere tid til at undersøge det. Disse trin hjælper dig med at bestemme omfanget af angrebet og isolere det til kun berørte enheder, f.eks. brugerkonti og enheder.

### <a name="step-1-assess-the-scope-of-the-incident"></a>Trin 1: Vurder omfanget af hændelsen

Gennemgå denne liste over spørgsmål og opgaver for at finde omfanget af angrebet. Microsoft 365 Defender kan give et samlet overblik over alle påvirkede aktiver eller risikobetonede aktiver, der kan hjælpe dig med vurderingen af svar på hændelser. Se [Svar på hændelse med Microsoft 365 Defender | Microsoft Docs](/incidents-overview.md). Du kan bruge beskederne og bevislisten i hændelsen til at bestemme:

* Hvilke brugerkonti kan være kompromitteret?
  * Hvilke konti blev brugt til at levere nyttedataene?
* Hvilke [onboardede](../defender-endpoint/investigate-machines.md) og [registrerede](../defender-endpoint/device-discovery.md) enheder påvirkes og hvordan?
  * Oprindelige enheder
  * Påvirkede enheder
  * Mistænkelige enheder
* Identificer enhver netværkskommunikation, der er knyttet til hændelsen.
* Hvilke programmer påvirkes?
* Hvilke nyttedata blev spredt?
* Hvordan kommunikerer angriberen med de kompromitterede enheder? (Netværksbeskyttelse skal [være aktiveret](../defender-endpoint/enable-network-protection.md)):
  * Gå til [siden indikatorer](../defender-endpoint/indicator-ip-domain.md#create-indicators-for-ips-and-urlsdomains) for at tilføje en blok for IP-adressen og URL-adressen (hvis du har disse oplysninger).
* Hvad var nyttelastleveringsmediet?

### <a name="step-2-preserve-existing-systems"></a>Trin 2: Bevar eksisterende systemer

Gennemgå denne liste over opgaver og spørgsmål for at beskytte eksisterende systemer mod angreb:

* Hvis du har online backups, overveje at afbryde backup-systemet fra netværket, indtil du er sikker på, at angrebet er indeholdt, se [Backup og gendannelse plan om at beskytte mod ransomware | Microsoft Docs](/security/compass/backup-plan-to-protect-against-ransomware).
* Hvis du oplever eller forventer en forestående og aktiv ransomware installation:
  * [Suspender privilegerede og lokale konti](/investigate-users.md) , som du har mistanke om er en del af angrebet. Det kan du gøre fra fanen **Brugere** i egenskaberne for hændelsen på Microsoft 365 Defender-portalen.
  * Stop alle [fjernlogonsessioner](/defender-for-identity/playbook-domain-dominance).
  * Nulstil adgangskoderne for den kompromitterede brugerkonto, og kræv, at brugere af kompromitterede brugerkonti logger på igen.
  * Gør det samme for brugerkonti, der kan være kompromitteret.
  * Hvis delte lokale konti kompromitteres, kan du få it-administratoren til at hjælpe dig med at gennemtvinge en adgangskodeændring på tværs af alle viste enheder. Eksempel på Kusto-forespørgsel:

```kusto
DeviceLogonEvents | where DeviceName  contains (AccountDomain) | take 10 
```

* For de enheder, der endnu ikke er isoleret og ikke er en del af den kritiske infrastruktur:
  * Isoler kompromitterede enheder fra netværket, men luk dem ikke.
  * Hvis du identificerer de oprindelige enheder eller sprederenheder, skal du isolere dem først.
* Bevar kompromitterede systemer til analyse.

### <a name="step-3-prevent-the-spread"></a>Trin 3: Undgå spredningen

Brug denne liste til at forhindre, at angrebet spredes til flere enheder.

* Hvis der bruges delte lokale konti i angrebet, bør du overveje [at blokere fjernanvendelse af lokale konti](https://techcommunity.microsoft.com/t5/microsoft-security-baselines/blocking-remote-use-of-local-accounts/ba-p/701042).
  * Kusto-forespørgsel om alle netværkslogon, der er lokale administratorer:

```kusto
DeviceLogonEvents
| where IsLocalAdmin == true and AccountDomain == DeviceName
| extend IsLocalLogon = tobool(todynamic(AdditionalFields).IsLocalLogon)
| where IsLocalLogon==false
```

* Kusto-forespørgsel om ikke-RDP-logon (mere realistisk for de fleste netværk):

```kusto
DeviceLogonEvents
| where IsLocalAdmin == true and AccountDomain == DeviceName and LogonType != 'RemoteInteractive'
| extend IsLocalLogon = tobool(todynamic(AdditionalFields).IsLocalLogon)
| where IsLocalLogon==false
```

* Sæt indikatorer i karantæne for filer, der er inficeret.
* Sørg for, at din antivirusløsning kan konfigureres i sin optimale beskyttelsestilstand. For Microsoft Defender Antivirus omfatter dette:
  * [Beskyttelse i realtid](../defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus.md) er aktiveret.
  * [Manipulationsbeskyttelse](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md) er aktiveret. På Microsoft 365 Defender-portalen skal du vælge **Indstillinger > Slutpunkter > Avancerede funktioner > Tamper-beskyttelse**.
  * [ASR-regler (Attack surface reduction)](../defender-endpoint/enable-attack-surface-reduction.md) er aktiveret.
  * [Cloudbeskyttelse](../defender-endpoint/enable-attack-surface-reduction.md) er aktiveret.
* Deaktiver Exchange ActiveSync og OneDrive-synkronisering.
  * Hvis du vil deaktivere Exchange ActiveSync for en postkasse, skal du se [Sådan deaktiverer du Exchange ActiveSync for brugere i Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-exchange-activesync).
  * Hvis du vil deaktivere andre typer adgang til en postkasse, skal du se:
    * [Aktivér eller deaktiver MAPI for en postkasse](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).
    * [Aktivér eller deaktiver pop3- eller IMAP4-adgang for en bruger](/exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access).
  * Hvis du standser OneDrive-synkronisering midlertidigt, hjælper det med at beskytte dine clouddata mod at blive opdateret af potentielt inficerede enheder. Du kan få flere oplysninger under [Sådan standser og genoptager du synkronisering i OneDrive](https://support.microsoft.com/office/how-to-pause-and-resume-sync-in-onedrive-2152bfa4-a2a5-4d3a-ace8-92912fb4421e).
* Anvend relevante programrettelser og konfigurationsændringer på berørte systemer.
* Bloker ransomware-kommunikation ved hjælp af interne og eksterne kontroller.
* Fjern cachelagret indhold

## <a name="investigation"></a>Undersøgelse

Brug dette afsnit til at undersøge angrebet og planlægge dit svar.

### <a name="assess-your-current-situation"></a>Vurder din nuværende situation

* Hvad oprindeligt gjorde dig opmærksom på ransomware-angrebet?
  * Hvis it-medarbejderne identificerede den indledende trussel – f.eks. at bemærke sikkerhedskopier, der slettes, antivirusbeskeder, EDR-beskeder (endpoint detection and response) eller mistænkelige systemændringer – er det ofte muligt at træffe hurtige afgørende foranstaltninger for at forhindre angrebet, typisk af de indeslutningshandlinger, der er beskrevet i denne artikel.
* Hvilken dato og hvilket klokkeslæt lærte du første gang om hændelsen?
  * Hvilke system- og sikkerhedsopdateringer blev ikke installeret på enheder på den pågældende dato? Dette er vigtigt for at forstå, hvilke sikkerhedsrisici der kan være blevet udnyttet, så de kan håndteres på andre enheder.
  * Hvilke brugerkonti blev brugt på denne dato?
  * Hvilke nye brugerkonti er oprettet siden denne dato?
  * Hvilke programmer blev tilføjet for automatisk at starte omkring det tidspunkt, hvor hændelsen fandt sted?
* Er der nogen indikation af, at angriberen i øjeblikket tilgår systemer?
  * Er der nogen formodede kompromitterede systemer, der oplever usædvanlig aktivitet?
  * Er der nogen formodede kompromitterede konti, der synes at være aktivt brugt af modstanderen?
  * Er der nogen beviser for aktive C2-servere (command-and-control) i EDR, firewall, VPN, webproxy og andre logge?

### <a name="identify-the-ransomware-process"></a>Identificer ransomware-processen

* Ved hjælp af [avanceret jagt](/microsoft-365/security/defender/advanced-hunting-overview.md) kan du søge efter den identificerede proces i processens oprettelseshændelser på andre enheder.

### <a name="look-for-exposed-credentials-in-the-infected-devices"></a>Søg efter viste legitimationsoplysninger på de inficerede enheder

* For brugerkonti, hvis legitimationsoplysninger muligvis blev kompromitteret, skal du nulstille kontoens adgangskoder og kræve, at brugerne logger på igen.
* Følgende IOA'er kan indikere tværgående bevægelse:

<details>
  <summary>Klik for at udvide</summary>

* Mistænkelige ekseloratorykommandoer
* MLFileBasedAlert
* IfeoDebuggerPersistence
* MistænkeligRemoteFileDropAndExecution
* ExploratoryWindowsCommands
* IoaStickyKeys
* Mimikatz Defender Forstærker
* Netværksscanningsværktøj, der bruges af PARINACOTA
* DefenderServerAlertMSSQLServer
* SuspiciousLowReputationFileDrop
* SuspiciousServiceExecution
* AdminUserAddition
* MimikatzArtifactsDetector
* Scuba-WdigestEnabledToAccessCredentials
* DefenderMalware
* MLSuspCmdBehavior
* MLSuspiciousRemoteInvocation
* MistænkeligRemoteComponentInvocation
* MistænkeligWmiProcessCreation
* MLCmdBasedWithRemoting
* Behandl accesses Lsass
* Mistænkelig udførelse af rundll32-proces
* BitsAdmin
* DefenderCobaltStrikeDetection
* DefenderHacktool
* IoaSuspPSCommandline
* Metasploit
* MLSuspToolBehavior
* RegistryQueryForPasswords
* SuspiciousWdavExclusion
* ASEPRegKey
* CobaltStrikeExecutionDetection
* DefenderBackdoor
* DefenderBehaviorSuspiciousActivity
* DefenderMalwareExecuted
* DefenderServerAlertDomainController
* DupTokenPrivilegeEscalationDetector
* FakeWindowsBinary
* IoaMaliciousCmdlets
* LivingOffTheLandBinary
* MicrosoftSignedBinaryAbuse
* MicrosoftSignedBinaryScriptletAbuse
* MLFileBasedWithRemoting
* MLSuspSvchostBehavior
* Læsfølsommemory
* RemoteCodeInjection-IREnabled
* Scuba-EchoSeenOverPipeOnLocalhost
* Scuba-SuspiciousWebScriptFileDrop
* Mistænkelig DLL-registrering af odbcconf
* Mistænkelig DPAPI-aktivitet
* Kørsel af mistænkelig exchange-proces
* Mistænkelig planlagt opgavestart
* SuspiciousLdapQueryDetector
* SuspiciousScheduledTaskRegistration
* Et program, der ikke er tillid til, åbner en RDP-forbindelse

</details>

### <a name="identify-the-line-of-business-lob-apps-that-are-unavailable-due-to-the-incident"></a>Identificer de LOB-apps (line of business), der ikke er tilgængelige på grund af hændelsen

* Kræver appen en identitet?
  * Hvordan udføres godkendelsen?
  * Hvordan gemmes og administreres legitimationsoplysninger som f.eks. certifikater eller hemmeligheder?
* Er evaluerede sikkerhedskopier af programmet, dets konfiguration og dets data tilgængelige?
* Find ud af, hvilken gendannelsesproces der kompromitteres.

## <a name="eradication-and-recovery"></a>Udryddelse og genopretning

Brug disse trin til at udrydde truslen og genoprette beskadigede ressourcer.

### <a name="step-1-verify-your-backups"></a>Trin 1: Kontrollér dine sikkerhedskopier

Hvis du har offline-sikkerhedskopier, kan du sandsynligvis gendanne de data, der er krypteret, efter at du har fjernet ransomware-nyttelasten (malware) fra dit miljø, og efter at du har bekræftet, at der ikke er uautoriseret adgang i din Microsoft 365-lejer.

### <a name="step-2-add-indicators"></a>Trin 2: Tilføj indikatorer

Tilføj kendte kommunikationskanaler for hackere som indikatorer, der er blokeret i firewalls, i dine proxyservere og på slutpunkter.

### <a name="step-3-reset-compromised-users"></a>Trin 3: Nulstil kompromitterede brugere

Nulstil adgangskoderne for alle kendte kompromitterede brugerkonti, og kræv et nyt logon.

* Overvej at nulstille adgangskoderne for alle privilegerede konti med en bred administrativ myndighed, f.eks. medlemmerne af gruppen Domæneadministratorer.
* Hvis en brugerkonto kan være oprettet af en hacker, skal du deaktivere kontoen. Slet ikke kontoen, medmindre der ikke er planer om at udføre sikkerhedstekniske oplysninger for hændelsen.

### <a name="step-4-isolate-attacker-control-points"></a>Trin 4: Isoler kontrolpunkter for hacker

Isoler alle kendte kontrolpunkter for personer med ondsindede hensigter i virksomheden fra internettet.

### <a name="step-5-remove-malware"></a>Trin 5: Fjern malware

Fjern malwaren fra de berørte enheder.

* Kør en fuld, aktuel antivirusscanning på alle mistænkte computere og enheder for at registrere og fjerne nyttedataene, der er knyttet til ransomware.
* Glem ikke at scanne enheder, der synkroniserer data eller mål for tilknyttede netværksdrev.

### <a name="step-6-recover-files-on-a-cleaned-device"></a>Trin 6: Gendan filer på en renset enhed

Gendan filer på en renset enhed.

* Du kan bruge [Filhistorik](https://support.microsoft.com/help/17128) i Windows 11, Windows 10, Windows 8.1 og Systembeskyttelse i Windows 7 til at forsøge at gendanne lokale filer og mapper.

### <a name="step-7-recover-files-in-onedrive-for-business"></a>Trin 7: Gendan filer i OneDrive for Business

Gendan filer i OneDrive for Business.

* Gendannelse af filer i OneDrive for Business giver dig mulighed for at gendanne et helt OneDrive til et tidligere tidspunkt inden for de sidste 30 dage. Du kan finde flere oplysninger under [Gendan dit OneDrive](https://support.microsoft.com/office/restore-your-onedrive-fa231298-759d-41cf-bcd0-25ac53eb8a15).

### <a name="step-8-recover-deleted-email"></a>Trin 8: Gendan slettet mail

Gendan slettet mail.

* I det sjældne tilfælde, at ransomware slettede al e-mail i en postkasse, kan du gendanne de slettede elementer. Se [Gendan slettede meddelelser i en brugers postkasse i Exchange Online](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages).

### <a name="step-9-re-enable-exchange-activesync-and-onedrive-sync"></a>Trin 9: Genaktiver Exchange ActiveSync og OneDrive-synkronisering

* Når du har renset dine computere og enheder og gendannet dataene, kan du genaktivere Exchange ActiveSync og OneDrive-synkronisering, som du tidligere har deaktiveret i trin 3 af opbevaringen.
