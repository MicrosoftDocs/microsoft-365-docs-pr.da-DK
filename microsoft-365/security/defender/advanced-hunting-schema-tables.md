---
title: Datatabeller i Microsoft 365 Defender avanceret jagtskema
description: Få mere at vide om tabellerne i det avancerede jagtskema for at forstå de data, du kan køre trusselsforespørgsler på
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søg, forespørgsel, telemetri, skemareference, kusto, tabel, data
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: a496e0e293e72821016d6efa5fbd9622f669ab0b
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755544"
---
# <a name="understand-the-advanced-hunting-schema"></a>Forstå det avancerede jagtskema

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Det [avancerede jagtskema](advanced-hunting-overview.md) består af flere tabeller, der indeholder enten oplysninger om begivenheder eller oplysninger om enheder, beskeder, identiteter og andre enhedstyper. For effektivt at opbygge forespørgsler, der strækker sig over flere tabeller, skal du forstå tabellerne og kolonnerne i det avancerede jagtskema.

<a name="get-schema-information-in-the-security-center"></a>

## <a name="get-schema-information"></a>Hent skemaoplysninger

Under opbygning af forespørgsler kan du bruge den indbyggede skemareference til hurtigt at få følgende oplysninger om hver tabel i skemaet:

- **Beskrivelse af** tabeller – datatypen, der er indeholdt i tabellen, og kilden til dataene.
- **Kolonner** – alle kolonnerne i tabellen.
- **Handlingstyper** – mulige værdier i kolonnen, der `ActionType` repræsenterer de hændelsestyper, der understøttes af tabellen. Disse oplysninger leveres kun for tabeller, der indeholder hændelsesoplysninger.
- **Eksempelforespørgsel** – eksempelforespørgsler, der viser, hvordan tabellen kan bruges.

### <a name="access-the-schema-reference"></a>Få adgang til skemareferencen
Hvis du hurtigt vil have adgang til skemareferencen, skal **du vælge handlingen Vis reference** ud for tabelnavnet i skemarepræsentationen. Du kan også vælge **Skemareference for** at søge efter en tabel.

:::image type="content" source="../../media/understand-schema-1.png" alt-text="Siden Skemareference på siden Avanceret ræve Microsoft 365 Defender portalen" lightbox="../../media/understand-schema-1.png":::

## <a name="learn-the-schema-tables"></a>Lær skematabellerne at vide
Følgende reference viser alle tabellerne i skemaet. Hvert tabelnavn linker til en side, der beskriver kolonnenavnene for den pågældende tabel. Tabel- og kolonnenavne er også angivet i Defender for Cloud som en del af skemarepræsentationen på den avancerede jagtskærm.

| Tabelnavn | Beskrivelse |
|------------|-------------|
| **[AlertEvidence](advanced-hunting-alertevidence-table.md)** | Filer, IP-adresser, URL-adresser, brugere eller enheder, der er knyttet til beskeder |
| **[AlertInfo](advanced-hunting-alertinfo-table.md)** | Beskeder fra Microsoft Defender til slutpunkt, Microsoft Defender til Office 365, Microsoft Defender til skyapps og Microsoft Defender for Identity, herunder oplysninger om alvorlighed og trussels kategorisering  |
| **[CloudAppEvents](advanced-hunting-cloudappevents-table.md)** | Begivenheder, der involverer konti og objekter i Office 365 og andre skyapps og -tjenester |
| **[DeviceEvents](advanced-hunting-deviceevents-table.md)** | Flere hændelsestyper, herunder hændelser, der udløses af sikkerhedskontrolelementer, f.eks. Windows Defender Antivirus og udnyttelse af beskyttelse |
| **[DeviceFileCertificateInfo](advanced-hunting-DeviceFileCertificateInfo-table.md)** | Certifikatoplysninger for signerede filer, der er hentet fra certifikatbekræftelseshændelser på slutpunkter |
| **[DeviceFileEvents](advanced-hunting-devicefileevents-table.md)** | Filoprettelse, ændring og andre filsystemhændelser |
| **[DeviceImageLoadEvents](advanced-hunting-deviceimageloadevents-table.md)** | DLL-indlæsningshændelser |
| **[DeviceInfo](advanced-hunting-deviceinfo-table.md)** | Computeroplysninger, herunder os-oplysninger |
| **[DeviceLogonEvents](advanced-hunting-devicelogonevents-table.md)** | Logons og andre godkendelseshændelser på enheder |
| **[DeviceNetworkEvents](advanced-hunting-devicenetworkevents-table.md)** | Netværksforbindelse og relaterede begivenheder |
| **[DeviceNetworkInfo](advanced-hunting-devicenetworkinfo-table.md)** | Netværksegenskaber for enheder, herunder fysiske adaptere, IP- og MAC-adresser samt forbundne netværk og domæner |
| **[DeviceProcessEvents](advanced-hunting-deviceprocessevents-table.md)** | Procesoprettelse og relaterede begivenheder |
| **[DeviceRegistryEvents](advanced-hunting-deviceregistryevents-table.md)** | Oprettelse og ændring af poster i registreringsdatabasen |
| **[DeviceTvmSecureConfigurationAssessment](advanced-hunting-devicetvmsecureconfigurationassessment-table.md)** | Hændelser & vurdering af sikkerhedssikkerhedsrisiko, der angiver status for forskellige sikkerhedskonfigurationer på enheder |
| **[DeviceTvmSecureConfigurationAssessmentKB](advanced-hunting-devicetvmsecureconfigurationassessmentkb-table.md)** | Vidensbase for forskellige sikkerhedskonfigurationer, der bruges af Threat & Vulnerability Management til at vurdere enheder; omfatter tilknytning til forskellige standarder og benchmarks  |
| **[DeviceTvmSoftwareInventory](advanced-hunting-devicetvmsoftwareinventory-table.md)** | Lager af software, der er installeret på enheder, herunder versionsoplysninger og status for ophør af support |
| **[DeviceTvmSoftwareVulnerabilities](advanced-hunting-devicetvmsoftwarevulnerabilities-table.md)** | Softwarerisici, der findes på enheder, og listen over tilgængelige sikkerhedsopdateringer, der adresserer hver sikkerhedsrisiko |
| **[DeviceTvmSoftwareVulnerabilitiesKB](advanced-hunting-devicetvmsoftwarevulnerabilitieskb-table.md)** | Videnbase af offentligt offentliggjorte sårbarheder, herunder om udnyttelse af kode er offentligt tilgængelig |
| **[EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md)** | Oplysninger om filer, der er vedhæftet mails |
| **[EmailEvents](advanced-hunting-emailevents-table.md)** | Microsoft 365 mailbegivenheder, herunder levering af mail og blokering af begivenheder |
| **[EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md)** | Sikkerhedshændelser, der forekommer efter levering, når Microsoft 365 har leveret mails til modtagerens postkasse |
| **[EmailUrlInfo](advanced-hunting-emailurlinfo-table.md)** | Oplysninger om URL-adresser i mails |
| **[IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md)** | Hændelser, der involverer en lokal domænecontroller, der kører Active Directory (AD). Denne tabel dækker en række identitetsrelaterede hændelser og systemhændelser på domænecontrolleren. |
| **[IdentityInfo](advanced-hunting-identityinfo-table.md)** | Kontooplysninger fra forskellige kilder, herunder Azure Active Directory |
| **[IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md)** | Godkendelseshændelser på Active Directory og Microsoft-onlinetjenester |
| **[IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md)** | Forespørgsler til Active Directory-objekter, f.eks. brugere, grupper, enheder og domæner |

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
