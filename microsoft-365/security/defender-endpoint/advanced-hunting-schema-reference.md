---
title: Avanceret reference til jagtskema
description: Få mere at vide om tabellerne i det avancerede jagtskema for at forstå de data, du kan køre trusselsforespørgsler på.
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, mdatp, microsoft defender atp, microsoft defender for slutpunkt, wdatp-søgning, forespørgsel, telemetri, skemareference, kusto, tabel, data
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 01/14/2020
ms.technology: mde
ms.openlocfilehash: 290d302f815de38c4cd84f417118205ed6504fe2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63592717"
---
# <a name="understand-the-advanced-hunting-schema-in-microsoft-defender-for-endpoint"></a>Forstå det avancerede jagtskema i Microsoft Defender til slutpunkt

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-advancedhuntingref-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Det [avancerede jagtskema](advanced-hunting-overview.md) består af flere tabeller, der enten indeholder oplysninger om begivenheder eller oplysninger om enheder og andre enheder. For effektivt at opbygge forespørgsler, der strækker sig over flere tabeller, skal du forstå tabellerne og kolonnerne i det avancerede jagtskema.

## <a name="get-schema-information-in-the-defender-for-cloud"></a>Få skemaoplysninger i Defender for Cloud

Under opbygning af forespørgsler kan du bruge den indbyggede skemareference til hurtigt at få følgende oplysninger om hver tabel i skemaet:

- **Beskrivelse af** tabeller: Typen af data, der er indeholdt i tabellen og kilden til de pågældende data.
- **Kolonner**: Alle kolonnerne i tabellen.
- **Handlingstyper**: Mulige værdier i kolonnen, der `ActionType` repræsenterer de hændelsestyper, der understøttes af tabellen. Dette gælder kun for tabeller, der indeholder hændelsesoplysninger.
- **Eksempelforespørgsel**: Eksempelforespørgsler, der viser, hvordan tabellen kan bruges.

### <a name="access-the-schema-reference"></a>Få adgang til skemareferencen

Hvis du hurtigt vil have adgang til skemareferencen, skal **du vælge handlingen Vis reference** ud for tabelnavnet i skemarepræsentationen. Du kan også vælge **Skemareference for** at søge efter en tabel.

![Billede, der viser, hvordan du får adgang til skemareference i portalen.](images/ah-reference.png)

## <a name="learn-the-schema-tables"></a>Lær skematabellerne at vide

Følgende reference viser alle tabellerne i det avancerede jagtskema. Hvert tabelnavn linker til en side, der beskriver kolonnenavnene for den pågældende tabel.

Tabel- og kolonnenavne er også angivet i Microsoft 365 Defender, i skemarepræsentationen på den avancerede jagtskærm.

<br>

****

|Tabelnavn|Beskrivelse|
|---|---|
|**[DeviceAlertEvents](advanced-hunting-devicealertevents-table.md)**|Beskeder om Microsoft 365 Defender |
|**[DeviceInfo](advanced-hunting-deviceinfo-table.md)**|Enhedsoplysninger, herunder os-oplysninger|
|**[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)**|Netværksegenskaber for enheder, herunder adaptere, IP- og MAC-adresser samt forbundne netværk og domæner|
|**[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)**|Procesoprettelse og relaterede begivenheder|
|**[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)**|Netværksforbindelse og relaterede begivenheder|
|**[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)**|Filoprettelse, ændring og andre filsystemhændelser|
|**[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)**|Oprettelse og ændring af poster i registreringsdatabasen|
|**[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)**|Logons og andre godkendelseshændelser|
|**[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)**|DLL-indlæsningshændelser|
|**[DeviceEvents](advanced-hunting-deviceevents-table.md)**|Flere hændelsestyper, herunder hændelser, der udløses af sikkerhedskontrolelementer, f.eks. Microsoft Defender Antivirus og udnyttelse af beskyttelse|
|**[DeviceFileCertificateInfo](advanced-hunting-devicefilecertificateinfo-table.md)**|Certifikatoplysninger for signerede filer, der er hentet fra certifikatbekræftelseshændelser på slutpunkter|
|**[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)**|Lager af software, der er installeret på enheder, herunder versionsoplysninger og status for ophør af support|
|**[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)**|Softwarerisici, der findes på enheder, og listen over tilgængelige sikkerhedsopdateringer, der adresserer hver sikkerhedsrisiko|
|**[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)**|Videnbase af offentligt offentliggjorte sårbarheder, herunder om udnyttelse af kode er offentligt tilgængelig|
|**[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)**|Hændelser & vurdering af sikkerhedssikkerhedsrisiko, der angiver status for forskellige sikkerhedskonfigurationer på enheder|
|**[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)**|Vidensbase for forskellige sikkerhedskonfigurationer, der bruges af Threat & Vulnerability Management til at vurdere enheder; omfatter tilknytning til forskellige standarder og benchmarks|
|

> [!TIP]
> Brug [avanceret jagt på Microsoft 365 Defender](/microsoft-365/security/defender/advanced-hunting-overview) til at lede efter trusler ved hjælp af data fra Defender til Slutpunkt, Microsoft Defender til Office 365, Microsoft Defender til skyapps og Microsoft Defender for Identity. [Slå Microsoft 365 Defender til](/microsoft-365/security/defender/m365d-enable).

Få mere at vide om, hvordan du flytter dine avancerede arbejdsprocesser på jagt fra Microsoft Defender til Microsoft 365 Defender i [Overfør avancerede forespørgselsforespørgsler fra Microsoft Defender til slutpunkt](/microsoft-365/security/defender/advanced-hunting-migrate-from-mde).

## <a name="related-topics"></a>Relaterede emner

- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
- [Oversigt over brugerdefinerede registreringer](overview-custom-detections.md)
- [Avancerede ændringer i dataskemaet](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/advanced-hunting-data-schema-changes/ba-p/1043914)
