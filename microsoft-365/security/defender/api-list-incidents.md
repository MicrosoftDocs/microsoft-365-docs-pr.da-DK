---
title: Vis hændelses-API i Microsoft 365 Defender
description: Få mere at vide om, hvordan du får vist hændelses-API Microsoft 365 Defender
keywords: liste, hændelse, hændelser, api
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.custom: api
ms.openlocfilehash: 03fbcb70588158919b54c9153b5d8d32d416cc75
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/24/2022
ms.locfileid: "63603037"
---
# <a name="list-incidents-api-in-microsoft-365-defender"></a>Vis hændelses-API i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!IMPORTANT]
> Nogle oplysninger relaterer til foreløbige produkter, som kan ændres væsentligt, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

## <a name="api-description"></a>API-beskrivelse

Listens API'er med hændelser giver dig mulighed for at sortere hændelser for at skabe et informeret svar om cybersikkerhed. Den viser en samling af hændelser, der er markeret med flag i dit netværk, inden for det tidsinterval, du har angivet i din miljøopbevaringspolitik. De seneste hændelser vises øverst på listen. Hver hændelse indeholder en række relaterede beskeder og deres relaterede enheder.

API'en understøtter følgende **OData-operatorer** :

- `$filter``lastUpdateTime`på , , `createdTime`og `status`egenskaber `assignedTo`
- `$top`med en maksimumværdi på **100**
- `$skip`

## <a name="limitations"></a>Begrænsninger

1. Den maksimale sidestørrelse **er 100 hændelser**.
2. Den maksimale hastighed for anmodninger er **50 opkald i minuttet** og **1500 opkald pr. time**.

## <a name="permissions"></a>Tilladelser

En af følgende tilladelser er påkrævet for at kalde denne API. Du kan få mere at vide, herunder hvordan du vælger tilladelser, [under Access Microsoft 365 Defender API'er](api-access.md)

Tilladelsestype|Tilladelse|Visningsnavn for tilladelse
---|---|---
Program|Incident.Read.All|Læs alle hændelser
Program|Incident.ReadWrite.All|Læs og skriv alle hændelser
Delegeret (arbejds- eller skolekonto)|Incident.Read|Læs hændelser
Delegeret (arbejds- eller skolekonto)|Incident.ReadWrite|Læs og skriv hændelser

> [!NOTE]
> Når du får et token med brugerlegitimationsoplysninger:
>
> - Brugeren skal have visningstilladelse til hændelser i portalen.
> - Svaret indeholder kun hændelser, brugeren er eksponeret for.

## <a name="http-request"></a>HTTP-anmodning

```HTTP
GET /api/incidents
```

## <a name="request-headers"></a>Anmod om brevhoveder

Navn|Type|Beskrivelse
---|---|---
Godkendelse|String|Bearer {token}. **Påkrævet**

## <a name="request-body"></a>Anmodningstekst

Ingen.

## <a name="response"></a>Svar

Hvis det lykkes, returnerer denne metode `200 OK`, og der vises [en liste over hændelser](api-incident.md) i svarteksten.

## <a name="schema-mapping"></a>Skematilknytning

### <a name="incident-metadata"></a>Hændelsesmetadata

Feltnavn|Beskrivelse|Eksempelværdi
---|---|---
incidentId|Entydigt id, der repræsenterer hændelsen|924565
redirectIncidentId|Kun udfyldt, hvis en hændelse grupperes sammen med en anden hændelse som en del af logikken til behandling af hændelser.|924569
incidentName|Strengværdi, der er tilgængelig for hver hændelse.|Ransomware-aktivitet
createdTime|Tidspunktet, hvor hændelsen blev oprettet.|2020-09-06T14:46:57.0733333Z
lastUpdateTime|Tidspunktet, hvor hændelsen sidst blev opdateret på back-enden. <p> Dette felt kan bruges, når du angiver anmodningsparameteren for det tidsrum, som hændelserne skal hentes fra.|2020-09-06T14:46:57.29Z
assignedTo|Ejeren af hændelsen eller null, *hvis* der ikke er tildelt nogen ejer.|secop2@contoso.com
klassificering|Specifikationen for hændelsen. Egenskabsværdierne er: *Unknown*, *FalsePositive*, *TruePositive*|Unknown
determination|Angiver bestemmelse af hændelsen. Egenskabsværdierne er: *NotAvailable*, *Apt*, *Malware*, *SecurityPersonnel*, *SecurityTesting*, *UnwantedSoftware*, *Other*|NotAvailable
detectionSource|Angiver registreringskilden.|Defender til skyapps
status|Kategoriser hændelser ( *som Aktiv* eller *Løst*). Den kan hjælpe dig med at organisere og administrere din svar på hændelser.|Aktiv
alvorsgrad|Angiver den mulige påvirkning af aktiver. Jo højere alvorsgrad, desto større er effekten. Elementer med højere alvorsgrad kræver som regel den mest øjeblikkelige opmærksomhed. <p> En af følgende værdier: *Informational*, *Lav*, *Mellem og *Høj*.|Mellem
mærker|Matrix med brugerdefinerede mærker, der er knyttet til en hændelse, f.eks. til at markere en gruppe af hændelser med en fælles egenskab.|\[\]
kommentarer|Matrix med kommentarer, der er oprettet ved secops, når du administrerer hændelsen, f.eks. yderligere oplysninger om markeringen af klassificeringen.|\[\]
beskeder|Matrix, der indeholder alle de beskeder, der er relateret til hændelsen, samt andre oplysninger, f.eks. alvorsgrad, enheder, der var involveret i beskeden, og kilden til beskederne.|\[\] (se oplysninger om beskedfelter nedenfor)

### <a name="alerts-metadata"></a>Beskeder om metadata

Feltnavn|Beskrivelse|Eksempelværdi
---|---|---
alertId|Entydigt id, der repræsenterer beskeden|cad70CFEE2-1F54-32DB-9988-3A868A1EBFAC
incidentId|Entydigt id, der repræsenterer den hændelse, denne besked er knyttet til|924565
serviceSource|Tjeneste, som beskeden kommer fra, f.eks. Microsoft Defender for Endpoint, Microsoft Defender til skyapps, Microsoft Defender for Identity eller Microsoft Defender Office 365.|MicrosoftCloudAppSecurity
creationTime|Tidspunktet, hvor beskeden blev oprettet.|2020-09-06T14:46:55.7182276Z
lastUpdatedTime|Tidspunkt, hvor påmindelsen sidst blev opdateret i back-enden.|2020-09-06T14:46:57.2433333Z
resolvedTime|Tidspunkt, hvor beskeden blev løst.|2020-09-10T05:22:59Z
firstActivity|Tidspunkt, hvor påmindelsen første gang rapporterede, at aktiviteten blev opdateret i backend.|2020-09-04T05:22:59Z
titel|Kort identificerende strengværdi for hver besked.|Ransomware-aktivitet
beskrivelse|Strengværdi, der beskriver hver besked.|Brugeren Test User2 (testUser2@contoso.com) manipulerede 99 filer med flere udvidelser, der slutter med den *ualmindelige udvidelse herunterladen*. Dette er et usædvanligt antal filmanipulationer og er angreb med mulig ransomware.
kategori|Visuel og numerisk visning af, hvor langt angrebene er løbet langs kill-kæden. Justeret til [MITRE ATT&CK-rammen™](https://attack.mitre.org/).|Virkning
status|Kategorisere beskeder (som *Ny*, *Aktiv* eller *Løst*). Det kan hjælpe dig med at organisere og administrere dit svar på beskeder.|Ny
alvorsgrad|Angiver den mulige påvirkning af aktiver. Jo højere alvorsgrad, desto større er effekten. Elementer med højere alvorsgrad kræver som regel den mest øjeblikkelige opmærksomhed.<br>En af følgende værdier: *Informational*, *Lav*, *Mellem* og *Høj*.|Mellem
investigationId|Det automatiserede undersøgelses-id, som denne besked udløser.|1234
undersøgelseTilstande|Oplysninger om undersøgelsens aktuelle status. En af følgende *værdier: Unknown*, *Terminated*, *SuccessfullyRemedated*, *Benign*, *Failed*, *PartiallyRemediated*, *Running*, *PendingApproval*, *PendingResource*, *PartiallyInvestigated*, *TerminatedByUser*, *TerminatedBySystem*, *Queued*, *InnerFailure*, *PreexistingAlert*, *UnsupportedOs*, *UnsupportedAlertType*, *UndertryktAlert*.|UnsupportedAlertType
klassificering|Specifikationen for hændelsen. Egenskabsværdierne er: *Unknown*, *FalsePositive*, *TruePositive* eller *Null*|Unknown
determination|Angiver bestemmelse af hændelsen. Egenskabsværdierne er: *NotAvailable*, *Apt*, *Malware*, *SecurityPersonnel*, *SecurityTesting*, *UnwantedSoftware*, *Other* eller  *null*|Nr.
assignedTo|Ejeren af hændelsen eller null, *hvis* der ikke er tildelt nogen ejer.|secop2@contoso.com
agentnavn|Aktivitetsgruppen, hvis der er nogen, den, der er knyttet til denne besked.|BORON
threatFamilyName|Trusselsfamilie, der er knyttet til denne besked.|null
mitreTechniques|De angrebsteknikker, der er justeret med [MITRE ATT&CK-frameworket](https://attack.mitre.org/)™.|\[\]
enheder|Alle enheder, hvor der blev sendt beskeder om hændelsen.|\[\] (se oplysninger om enhedsfelter nedenfor)

### <a name="device-format"></a>Enhedsformat

Feltnavn|Beskrivelse|Eksempelværdi
---|---|---
DeviceId|Enheds-id'et, der er angivet i Microsoft Defender til slutpunkt.|24c222b0b60fe148eeece49ac83910cc6a7ef491
aadDeviceId|Enheds-id'et, der er [angivet i Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis). Kun tilgængelig for enheder, der er forbundet med domæner.|null
deviceDnsName|Enhedens fulde domænenavn.|user5cx.middleeast.corp.contoso.com
osPlatform|Den operativsystemplatform, enheden kører.|WindowsServer2016
osBuild|Buildversionen for det operativsystem, enheden kører.|14393
rbacGroupName|Den [rollebaserede adgangskontrolgruppe](/azure/role-based-access-control/overview) (RBAC), der er knyttet til enheden.|WDATP-Ring0
firstSeen|Tidspunkt, hvor enheden blev set første gang.|2020-02-06T14:16:01.9330135Z
healthStatus|Enhedens tilstand.|Aktiv
riskScore|Risikoscore for enheden.|Høj
enheder|Alle enheder, der er identificeret som en del af eller relateret til en bestemt besked.|\[\] (se oplysninger om enhedsfelter nedenfor)

### <a name="entity-format"></a>Enhedsformat

Feltnavn|Beskrivelse|Eksempelværdi
---|---|---
entityType|Enheder, der er identificeret som en del af eller relateret til en bestemt besked.<br>Egenskabsværdierne er: *Bruger*, *Ip*, *URL-adresse*, *File*, *Process*, *MailBox*, *MailMessage*, *MailCluster*, *Registry*|Bruger
sha1|Tilgængelig, hvis entityType er *Fil*.<br>Filhash for beskeder, der er knyttet til en fil eller proces.|5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd
sha256|Tilgængelig, hvis entityType er *Fil*.<br>Filhash for beskeder, der er knyttet til en fil eller proces.|28cb017dfc99073aa1b47c1b30f413e3ce774c4991eb4158de50f9dbb36d8043
filnavn|Tilgængelig, hvis entityType er *Fil*.<br>Filnavnet for beskeder, der er knyttet til en fil eller proces|Detector.UnitTests.dll
filePath|Tilgængelig, hvis entityType er *Fil*.<br>Filstien til beskeder, der er knyttet til en fil eller proces|C:\\\agent_work_temp\Deploy\SYSTEM\2020-09-06 12_14_54\Out
processId|Tilgængelig, hvis entityType er *Process*.|24348
processCommandLine|Tilgængelig, hvis entityType er *Process*.|"Filen er klar til at blive downloadet\_1911150169.exe"
processCreationTime|Tilgængelig, hvis entityType er *Process*.|2020-07-18T03:25:38.5269993Z
parentProcessId|Tilgængelig, hvis entityType er *Process*.|16840
parentProcessCreationTime|Tilgængelig, hvis entityType er *Process*.|2020-07-18T02:12:32.8616797Z
ipAddress|Tilgængelig, hvis entityType er *Ip*. <br>IP-adresse for beskeder, der er knyttet til netværkshændelser, f.eks *Kommunikation til en ondsindet netværksdestination*.|62.216.203.204
url|Tilgængelig, hvis entityType er *URL-adresse*. <br>URL-adresse for beskeder, der er knyttet til netværkshændelser, f.eks *. Kommunikation til en ondsindet netværksdestination*.|down.esales360.cn
accountName|Tilgængelig, hvis entityType er *bruger*.|testUser2
domainName|Tilgængelig, hvis entityType er *bruger*.|europe.corp.contoso
userSid|Tilgængelig, hvis entityType er *bruger*.|S-1-5-21-1721254763-462695806-1538882281-4156657
aadUserId|Tilgængelig, hvis entityType er *bruger*.|fc8f7484-f813-4db2-afab-bc1507913fb6
userPrincipalName|Tilgængelig, hvis entityType *er* *UserMailBoxMailMessage*//.|testUser2@contoso.com
mailboxDisplayName|Tilgængelig, hvis entityType er *MailBox*.|test bruger2
mailboxAddress|Tilgængelig, hvis entityType *er* *UserMailBoxMailMessage*//.|testUser2@contoso.com
clusterBy|Tilgængelig, hvis entityType er  *MailCluster*.|Emne; P2SenderDomain; ContentType
afsender|Tilgængelig, hvis entityType *er* *UserMailBoxMailMessage*//.|user.abc@mail.contoso.co.in
modtager|Tilgængelig, hvis entityType er *MailMessage*.|testUser2@contoso.com
emne|Tilgængelig, hvis entityType er *MailMessage*.|\[EKSTERN\] opmærksomhed
deliveryAction|Tilgængelig, hvis entityType er *MailMessage*.|Leveret
securityGroupId|Tilgængelig, hvis entityType er  *SecurityGroup*.|301c47c8-e15f-4059-ab09-e2ba9ffd372b
securityGroupName|Tilgængelig, hvis entityType er  *SecurityGroup*.|Netværkskonfigurationsoperatorer
registryHive|Tilgængelig, hvis entityType er  *Registreringsdatabase*.|HKEYLOCALMACHINE\_\_|
registryKey|Tilgængelig, hvis entityType er  *Registreringsdatabase*.|SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon
registryValueType|Tilgængelig, hvis entityType er  *Registreringsdatabase*.|String
registryValue|Tilgængelig, hvis entityType er  *Registreringsdatabase*.|31-00-00-00
deviceId|Id'et for den enhed, der er relateret til enheden, hvis dette er nogen.|986e5df8b73dacd43c8917d17e523e76b13c75cd

## <a name="example"></a>Eksempel

### <a name="request-example"></a>Eksempel på anmodning

```HTTP
GET https://api.security.microsoft.com/api/incidents
```

### <a name="response-example"></a>Eksempel på svar

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Incidents",
    "value": [
            {
            "incidentId": 924565,
            "redirectIncidentId": null,
            "incidentName": "Ransomware activity",
            "createdTime": "2020-09-06T14:46:57.0733333Z",
            "lastUpdateTime": "2020-09-06T14:46:57.29Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Medium",
            "tags": [],
            "comments": [
                {
                    "comment": "test comment for docs",
                    "createdBy": "secop123@contoso.com",
                    "createdTime": "2021-01-26T01:00:37.8404534Z"
                }
            ],
            "alerts": [
                {
                    "alertId": "caD70CFEE2-1F54-32DB-9988-3A868A1EBFAC",
                    "incidentId": 924565,
                    "serviceSource": "MicrosoftCloudAppSecurity",
                    "creationTime": "2020-09-06T14:46:55.7182276Z",
                    "lastUpdatedTime": "2020-09-06T14:46:57.2433333Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-04T05:22:59Z",
                    "lastActivity": "2020-09-04T05:22:59Z",
                    "title": "Ransomware activity",
                    "description": "The user Test User2 (testUser2@contoso.com) manipulated 99 files with multiple extensions ending with the uncommon extension herunterladen. This is an unusual number of file manipulations and is indicative of a potential ransomware attack.",
                    "category": "Impact",
                    "status": "New",
                    "severity": "Medium",
                    "investigationId": null,
                    "investigationState": "UnsupportedAlertType",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "MCAS",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "User",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": "testUser2",
                            "domainName": "europe.corp.contoso",
                            "userSid": "S-1-5-21-1721254763-462695806-1538882281-4156657",
                            "aadUserId": "fc8f7484-f813-4db2-afab-bc1507913fb6",
                            "userPrincipalName": "testUser2@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "62.216.203.204",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924521,
            "redirectIncidentId": null,
            "incidentName": "'Mimikatz' hacktool was detected on one endpoint",
            "createdTime": "2020-09-06T12:18:03.6266667Z",
            "lastUpdateTime": "2020-09-06T12:18:03.81Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Low",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "da637349914833441527_393341063",
                    "incidentId": 924521,
                    "serviceSource": "MicrosoftDefenderATP",
                    "creationTime": "2020-09-06T12:18:03.3285366Z",
                    "lastUpdatedTime": "2020-09-06T12:18:04.2566667Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:15:07.7272048Z",
                    "lastActivity": "2020-09-06T12:15:07.7272048Z",
                    "title": "'Mimikatz' hacktool was detected",
                    "description": "Readily available tools, such as hacking programs, can be used by unauthorized individuals to spy on users. When used by attackers, these tools are often installed without authorization and used to compromise targeted machines.\n\nThese tools are often used to collect personal information from browser records, record key presses, access email and instant messages, record voice and video conversations, and take screenshots.\n\nThis detection might indicate that Windows Defender Antivirus has stopped the tool from being installed and used effectively. However, it is prudent to check the machine for the files and processes associated with the detected tool.",
                    "category": "Malware",
                    "status": "New",
                    "severity": "Low",
                    "investigationId": null,
                    "investigationState": "UnsupportedOs",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "WindowsDefenderAv",
                    "assignedTo": null,
                    "actorName": null,
                    "threatFamilyName": "Mimikatz",
                    "mitreTechniques": [],
                    "devices": [
                        {
                            "mdatpDeviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491",
                            "aadDeviceId": null,
                            "deviceDnsName": "user5cx.middleeast.corp.contoso.com",
                            "osPlatform": "WindowsServer2016",
                            "version": "1607",
                            "osProcessor": "x64",
                            "osBuild": 14393,
                            "healthStatus": "Active",
                            "riskScore": "High",
                            "rbacGroupName": "WDATP-Ring0",
                            "rbacGroupId": 9,
                            "firstSeen": "2020-02-06T14:16:01.9330135Z"
                        }
                    ],
                    "entities": [
                        {
                            "entityType": "File",
                            "sha1": "5de839186691aa96ee2ca6d74f0a38fb8d1bd6dd",
                            "sha256": null,
                            "fileName": "Detector.UnitTests.dll",
                            "filePath": "C:\\Agent\\_work\\_temp\\Deploy_SYSTEM 2020-09-06 12_14_54\\Out",
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": "24c222b0b60fe148eeece49ac83910cc6a7ef491"
                        }
                    ]
                }
            ]
        },
        {
            "incidentId": 924518,
            "redirectIncidentId": null,
            "incidentName": "Email reported by user as malware or phish",
            "createdTime": "2020-09-06T12:07:55.1366667Z",
            "lastUpdateTime": "2020-09-06T12:07:55.32Z",
            "assignedTo": null,
            "classification": "Unknown",
            "determination": "NotAvailable",
            "status": "Active",
            "severity": "Informational",
            "tags": [],
            "comments": [],
            "alerts": [
                {
                    "alertId": "faf8edc936-85f8-a603-b800-08d8525cf099",
                    "incidentId": 924518,
                    "serviceSource": "OfficeATP",
                    "creationTime": "2020-09-06T12:07:54.3716642Z",
                    "lastUpdatedTime": "2020-09-06T12:37:40.88Z",
                    "resolvedTime": null,
                    "firstActivity": "2020-09-06T12:04:00Z",
                    "lastActivity": "2020-09-06T12:04:00Z",
                    "title": "Email reported by user as malware or phish",
                    "description": "This alert is triggered when any email message is reported as malware or phish by users -V1.0.0.2",
                    "category": "InitialAccess",
                    "status": "InProgress",
                    "severity": "Informational",
                    "investigationId": null,
                    "investigationState": "Queued",
                    "classification": null,
                    "determination": null,
                    "detectionSource": "OfficeATP",
                    "assignedTo": "Automation",
                    "actorName": null,
                    "threatFamilyName": null,
                    "mitreTechniques": [],
                    "devices": [],
                    "entities": [
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser3@contoso.com",
                            "mailboxDisplayName": "test User3",
                            "mailboxAddress": "testUser3@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailBox",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "testUser4@contoso.com",
                            "mailboxDisplayName": "test User4",
                            "mailboxAddress": "test.User4@contoso.com",
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailMessage",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": "test.User4@contoso.com",
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": "user.abc@mail.contoso.co.in",
                            "recipient": "test.User4@contoso.com",
                            "subject": "[EXTERNAL] Attention",
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "Subject;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;P2SenderDomain;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "MailCluster",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": null,
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": "BodyFingerprintBin1;SenderIp;ContentType",
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        },
                        {
                            "entityType": "Ip",
                            "sha1": null,
                            "sha256": null,
                            "fileName": null,
                            "filePath": null,
                            "processId": null,
                            "processCommandLine": null,
                            "processCreationTime": null,
                            "parentProcessId": null,
                            "parentProcessCreationTime": null,
                            "ipAddress": "49.50.81.121",
                            "url": null,
                            "accountName": null,
                            "domainName": null,
                            "userSid": null,
                            "aadUserId": null,
                            "userPrincipalName": null,
                            "mailboxDisplayName": null,
                            "mailboxAddress": null,
                            "clusterBy": null,
                            "sender": null,
                            "recipient": null,
                            "subject": null,
                            "deliveryAction": null,
                            "securityGroupId": null,
                            "securityGroupName": null,
                            "registryHive": null,
                            "registryKey": null,
                            "registryValueType": null,
                            "registryValue": null,
                            "deviceId": null
                        }
                    ]
                }
            ]
        },
        ...
    ]
}
```

## <a name="related-articles"></a>Relaterede artikler

- [Få adgang til Microsoft 365 Defender API'er](api-access.md)
- [Få mere at vide om API-begrænsninger og licenser](api-terms.md)
- [Forstå fejlkoder](api-error-codes.md)
- [Oversigt over hændelser](incidents-overview.md)
- [Hændelses-API'er](api-incident.md)
- [Opdater hændelses-API](api-update-incidents.md)
