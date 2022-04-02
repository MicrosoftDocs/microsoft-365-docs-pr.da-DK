---
title: DeviceFileCertificateInfo-tabel i det avancerede jagtskema
description: Få mere at vide om signeringsoplysninger om filer i tabellen DeviceFileCertificateInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselssøgning, cybertrusler på jagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, digital signatur, certifikat, filsignering, DeviceFileCertificateInfo
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
ms.openlocfilehash: 7b43b6ad8ed1422830f08358f460b20b16588996
ms.sourcegitcommit: 6dcc3b039e0f0b9bae17c386f14ed2b577b453a6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/15/2021
ms.locfileid: "63603070"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt

Tabellen `DeviceFileCertificateInfo` i det avancerede [skema indeholder](advanced-hunting-overview.md) oplysninger om signeringscertifikater. Denne tabel anvender data, der er hentet fra certifikatbekræftelsesaktiviteter, der regelmæssigt udføres på filer på slutpunkter.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema i [den avancerede jagtreference](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for, hvornår begivenheden blev optaget |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn på computeren |
| `SHA1` | `string` | SHA-1 i den fil, som den optagede handling blev anvendt på |
| `IsSigned` | `boolean` | Angiver, om filen er signeret |
| `SignatureType` | `string` | Angiver, om signaturoplysningerne blev læst som integreret indhold i selve filen eller læst fra en ekstern katalogfil |
| `Signer` | `string` | Oplysninger om underskriveren af filen |
| `SignerHash` | `string` | Entydig hash-værdi, der identificerer underskriveren |
| `Issuer` | `string` | Oplysninger om det udstedende nøglecenter |
| `IssuerHash` | `string` | Entydig hash-værdi, der identificerer udstedelsescertifikatcenter (CA) |
| `CertificateSerialNumber` | `string` | Id for det certifikat, der er entydigt for det udstedende nøglecenter |
| `CrlDistributionPointUrls` | `string` |  JSON-matrix, der viser URL-adresserne for netværkshares, der indeholder certifikater og lister over tilbagekaldte certifikater (CRLs) |
| `CertificateCreationTime` | `datetime` | Dato og klokkeslæt for oprettelse af certifikatet |
| `CertificateExpirationTime` | `datetime` | Dato og klokkeslæt, hvor certifikatet er indstillet til at udløbe |
| `CertificateCountersignatureTime` | `datetime` | Dato og klokkeslæt for, hvor certifikatet blev modsigneret |
| `IsTrusted` | `boolean` | Angiver, om der er tillid til filen baseret på resultaterne af funktionen WinVerifyTrust, som kontrollerer, om der er oplysninger om ukendt rodcertifikat, ugyldige signaturer, tilbagekaldte certifikater og andre tvivlsomme attributter |
| `IsRootSignerMicrosoft` | `boolean` | Angiver, om underskriveren af rodcertifikatet er Microsoft |
| `ReportId` | `long` | Hændelses-id baseret på en gentagende tæller. Denne kolonne skal bruges sammen med kolonnerne DeviceName og Timetamp til at identificere entydige hændelser. | 

## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)
