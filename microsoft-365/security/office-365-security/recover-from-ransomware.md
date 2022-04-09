---
title: Gendan efter et ransomware-angreb
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- m365solution-ransomware
description: Microsoft 365 administratorer kan lære at komme sig efter et ransomware-angreb.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8e5e942bb39097fffa955d5bb9c3b8a72212d0cc
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "64730835"
---
# <a name="recover-from-a-ransomware-attack-in-microsoft-365"></a>Gendan efter et ransomware-angreb i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Selv hvis du tager alle forholdsregler for at beskytte din organisation, kan du stadig blive offer for en [ransomware](/windows/security/threat-protection/intelligence/ransomware-malware) angreb. Ransomware er en stor forretning, og i dagens trusselslandskab Microsoft 365 er et stadigt stigende [mål for sofistikerede angreb](https://i.blackhat.com/USA21/Wednesday-Handouts/us-21-Cloudy-With-A-Chance-Of-APT-Novel-Microsoft-365-Attacks-In-The-Wild.pdf).

Trinnene i denne artikel giver dig den bedste chance for at gendanne data og stoppe den interne spredning af infektion. Før du går i gang, skal du overveje følgende elementer:

- Der er ingen garanti for, at betaling af løsesummen vil vende tilbage til dine filer. Faktisk kan betaling af løsesum gøre dig et mål for mere ransomware.

  Hvis du allerede har betalt, men du har gendannet uden at bruge hackerens løsning, skal du kontakte din bank for at se, om de kan blokere transaktionen.

  Vi anbefaler også, at du rapporterer ransomware-angrebet til retshåndhævelse, websteder, der rapporterer svindel, og Microsoft som beskrevet senere i denne artikel.

- Det er vigtigt, at du reagerer hurtigt på angrebet og dets konsekvenser. Jo længere du venter, jo mindre sandsynligt er det, at du kan gendanne de berørte data.

## <a name="step-1-verify-your-backups"></a>Trin 1: Kontrollér dine sikkerhedskopier

Hvis du har offline-sikkerhedskopier, kan du sandsynligvis gendanne de krypterede data, **når** du har fjernet ransomware-nyttelasten (malware) fra dit miljø, og **efter** at du har bekræftet, at der ikke er uautoriseret adgang i dine Microsoft 365 miljøer.

Hvis du ikke har sikkerhedskopier, eller hvis dine sikkerhedskopier også blev påvirket af ransomware, kan du springe dette trin over.

## <a name="step-2-disable-exchange-activesync-and-onedrive-sync"></a>Trin 2: Deaktiver Exchange ActiveSync og OneDrive-synkronisering

Det vigtigste punkt her er at stoppe spredningen af datakryptering af ransomware.

Hvis du har mistanke om e-mail som et mål for ransomware kryptering, midlertidigt deaktivere brugeradgang til postkasser. Exchange ActiveSync synkroniserer data mellem enheder og Exchange Online postkasser.

Hvis du vil deaktivere Exchange ActiveSync for en postkasse, skal du se [Sådan deaktiverer du Exchange ActiveSync for brugere i Exchange Online](https://support.microsoft.com/help/2795303).

Hvis du vil deaktivere andre typer adgang til en postkasse, skal du se:

- [Aktivér eller deaktiver MAPI for en postkasse](/Exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-mapi).

- [Aktivér eller deaktiver pop3- eller IMAP4-adgang for en bruger](/Exchange/clients-and-mobile-in-exchange-online/pop3-and-imap4/enable-or-disable-pop3-or-imap4-access)

Hvis du standser OneDrive-synkronisering midlertidigt, hjælper det med at beskytte dine clouddata mod at blive opdateret af potentielt inficerede enheder. Du kan få flere oplysninger under [Sådan afbrydes og genoptages synkronisering i OneDrive](https://support.microsoft.com/office/2152bfa4-a2a5-4d3a-ace8-92912fb4421e).

## <a name="step-3-remove-the-malware-from-the-affected-devices"></a>Trin 3: Fjern malwaren fra de berørte enheder

Kør en fuld, aktuel antivirusscanning på alle mistænkte computere og enheder for at registrere og fjerne nyttedataene, der er forbundet med ransomware.

Glem ikke at scanne enheder, der synkroniserer data, eller målene for tilknyttede netværksdrev.

Du kan bruge [Windows Defender](https://www.microsoft.com/windows/comprehensive-security) eller (til ældre klienter) [Microsoft Security Essentials](https://www.microsoft.com/download/details.aspx?id=5201).

Et alternativ, der også vil hjælpe dig med at fjerne ransomware eller malware er [Værktøj til fjernelse af skadelig software (MSRT)](https://www.microsoft.com/download/details.aspx?id=9905).

Hvis disse indstillinger ikke fungerer, kan du prøve [Windows Defender Offline](https://support.microsoft.com/help/17466) eller [Foretage fejlfinding af problemer med registrering og fjernelse af malware](https://support.microsoft.com/help/4466982).

## <a name="step-4-recover-files-on-a-cleaned-computer-or-device"></a>Trin 4: Gendan filer på en renset computer eller enhed

Når du har fuldført det forrige trin til at fjerne ransomware nyttedata fra dit miljø (hvilket vil forhindre ransomware i at kryptere eller fjerne dine filer), kan du bruge [Filhistorik](https://support.microsoft.com/help/17128) i Windows 11, Windows 10, Windows 8.1, og ved at bruge Systembeskyttelse i Windows 7 til at forsøge at gendanne dine lokale filer og mapper.

**Noter**:

- Nogle ransomware vil også kryptere eller slette sikkerhedskopiversionerne, så du kan ikke bruge Filhistorik eller Systembeskyttelse til at gendanne filer. Hvis det sker, skal du bruge sikkerhedskopier på eksterne drev eller enheder, der ikke blev påvirket af ransomware eller OneDrive som beskrevet i næste afsnit.

- Hvis en mappe synkroniseres til OneDrive, og du ikke bruger den nyeste version af Windows, kan der være nogle begrænsninger ved hjælp af Filhistorik.

## <a name="step-5-recover-your-files-in-your-onedrive-for-business"></a>Trin 5: Gendan dine filer i din OneDrive for Business

Gendannelse af filer i OneDrive for Business giver dig mulighed for at gendanne hele OneDrive til et tidligere tidspunkt inden for de sidste 30 dage. Du kan finde flere oplysninger under [Gendan OneDrive](https://support.microsoft.com/office/fa231298-759d-41cf-bcd0-25ac53eb8a15).

## <a name="step-6-recover-deleted-email"></a>Trin 6: Gendan slettet mail

I det sjældne tilfælde, at ransomware slettede al din e-mail, kan du sandsynligvis gendanne de slettede elementer. Du kan finde flere oplysninger under:

- [Gendan slettede meddelelser i en brugers postkasse](/exchange/recipients-in-exchange-online/manage-user-mailboxes/recover-deleted-messages)

- [Gendan slettede elementer i Outlook for Windows](https://support.microsoft.com/office/49e81f3c-c8f4-4426-a0b9-c0fd751d48ce)

## <a name="step-7-re-enable-exchange-activesync-and-onedrive-sync"></a>Trin 7: Genaktiver Exchange ActiveSync og OneDrive-synkronisering

Når du har renset dine computere og enheder og gendannet dine data, kan du genaktivere Exchange ActiveSync og OneDrive-synkronisering, som du tidligere har deaktiveret i [trin 2](#step-2-disable-exchange-activesync-and-onedrive-sync).

## <a name="step-8-optional-block-onedrive-sync-for-specific-file-extensions"></a>Trin 8 (valgfrit): Bloker OneDrive-synkronisering for bestemte filtypenavne

Når du har gendannet, kan du forhindre OneDrive for Business klienter i at synkronisere de filtyper, der blev påvirket af denne ransomware. Du kan få flere oplysninger under [Set-SPOTenantSyncClientRestriction](/powershell/module/sharepoint-online/set-spotenantsyncclientrestriction)

## <a name="report-the-attack"></a>Rapportér angrebet

### <a name="contact-law-enforcement"></a>Kontakt de retshåndhævende myndigheder

Du bør kontakte din lokale eller føderale retshåndhævende myndigheder. Hvis du f.eks. befinder dig i USA kan du kontakte [FBI's lokale kontor](https://www.fbi.gov/contact-us/field), [IC3](http://www.ic3.gov/complaint/default.aspx) eller [Secret Service](http://www.secretservice.gov/).

### <a name="submit-a-report-to-your-countrys-scam-reporting-website"></a>Indsend en rapport på dit lands websted med rapportering om svindel

Websteder til rapportering af svindel indeholder oplysninger om, hvordan du kan forhindre og undgå svindel. De giver også mekanismer til at rapportere, hvis du var offer for fidus.

- Australien: [SCAMwatch](http://www.scamwatch.gov.au/)

- Canada: [Canadisk center for bekæmpelse af svig](http://www.antifraudcentre-centreantifraude.ca/)

- Frankrig: [Agence nationale de la sécurité des systèmes d'information](http://www.ssi.gouv.fr/)

- Tyskland: [Bundesamt für Sicherheit in der Informationstechnik](https://www.bsi.bund.de/DE/Home/home_node.html)

- Irland: [a Garda Síochána](http://www.garda.ie/)

- New Zealand: [Forbruger anliggender svindel](http://www.consumeraffairs.govt.nz/scams)

- Schweiz [Nationales Zentrum für Cybersicherheit NCSC](https://www.ncsc.admin.ch/ncsc/de/home.html)

- Det Forenede Kongerige: [Bedrageri i forbindelse med foranstaltninger](http://www.actionfraud.police.uk/)

- USA: [On Guard Online](http://www.onguardonline.gov/)

Hvis dit land ikke er angivet, skal du spørge din lokale eller føderale retshåndhævende myndigheder.

### <a name="submit-email-messages-to-microsoft"></a>Send mails til Microsoft

Du kan rapportere phishing-meddelelser, der indeholder ransomware, ved hjælp af en af flere metoder. Du kan få flere oplysninger under [Rapportér meddelelser og filer til Microsoft](report-junk-email-messages-to-microsoft.md).

## <a name="additional-ransomware-resources"></a>Yderligere ransomware-ressourcer

Nøgleoplysninger fra Microsoft:

- [Den voksende trussel om ransomware](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blogindlæg den 20. juli 2021
- [Menneskedrevet ransomware](/security/compass/human-operated-ransomware)
- [Beskyt hurtigt mod ransomware og pengeafpresning](/security/compass/protect-against-ransomware)
- [2021 Microsoft Digital Defense Report](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (se side 10-19)
- [Ransomware: En gennemtrængende og løbende rapport over trusselsanalyser](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) på Microsoft 365 Defender-portalen

Microsoft 365:

- [Udrul ransomware-beskyttelse til din Microsoft 365 lejer](/microsoft-365/solutions/ransomware-protection-microsoft-365)
- [Maksimer Ransomware Robusthed med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Beskyttelse mod malware og ransomware](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Beskyt din Windows pc mod ransomware](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [Håndtering af ransomware i SharePoint Online](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Trusselsanalyserapporter for ransomware](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) på Microsoft 365 Defender-portalen

Microsoft 365 Defender:

- [Find ransomware med avanceret jagt](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Azure Defenses for Ransomware Attack](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Maksimer Ransomware Robusthed med Azure og Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Sikkerhedskopierings- og gendannelsesplan for beskyttelse mod ransomware](/security/compass/backup-plan-to-protect-against-ransomware)
- [Hjælp med at beskytte mod ransomware med Microsoft Azure backup](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 minutters video)
- [Gendannelse efter kompromitteret systemisk identitet](/azure/security/fundamentals/recover-from-identity-compromise)
- [Avanceret registrering af angreb i fleretages i Microsoft Sentinel](/azure/sentinel/fusion#ransomware)
- [Fusion Detection for Ransomware i Microsoft Sentinel](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [Opret politikker for registrering af uregelmæssigheder i Defender for Cloud Apps](/cloud-app-security/anomaly-detection-policy)

Blogindlæg om Microsoft Security-teamet:

- [3 trin til at forhindre og komme sig efter ransomware (september 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [En guide til bekæmpelse af menneskeligt drevet ransomware: Del 1 (september 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Vigtige trin til, hvordan Microsofts detection and Response Team (DART) udfører ransomware-hændelsesundersøgelser.

- [En guide til bekæmpelse af menneskeligt drevet ransomware: Del 2 (september 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Anbefalinger og bedste praksis.

- [At blive modstandsdygtig ved at forstå cybersikkerhedsrisici: Del 4 – navigering i aktuelle trusler (maj 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Se afsnittet **Ransomware** .

- [Menneskedrevne ransomware-angreb: En forebyggelig katastrofe (marts 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Indeholder analyser af angrebskæder af faktiske angreb.

- [Ransomware-svar – at betale eller ikke at betale? (december 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro reagerer på ransomware-angreb med gennemsigtighed (december 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
