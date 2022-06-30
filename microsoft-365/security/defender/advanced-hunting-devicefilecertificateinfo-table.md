---
title: Tabellen DeviceFileCertificateInfo i det avancerede jagtskema
description: Få mere at vide om oplysninger om filsignering i tabellen DeviceFileCertificateInfo i det avancerede jagtskema
keywords: avanceret jagt, trusselsjagt, cybertrusselsjagt, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, skemareference, kusto, tabel, kolonne, datatype, digital signatur, certifikat, filsignering, DeviceFileCertificateInfo
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
ms.openlocfilehash: 019ca8eced735b8a9e24c2b0f3e3baae37757875
ms.sourcegitcommit: bc35c7826e3403f259725ac72cca5bafd36aa56a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/30/2022
ms.locfileid: "66554549"
---
# <a name="devicefilecertificateinfo"></a>DeviceFileCertificateInfo

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender for Endpoint

Tabellen `DeviceFileCertificateInfo` i det [avancerede jagtskema](advanced-hunting-overview.md) indeholder oplysninger om certifikater til filsignering. Denne tabel bruger data, der er hentet fra aktiviteter til bekræftelse af certifikater, som jævnligt udføres på filer på slutpunkter.

Du kan finde oplysninger om andre tabeller i det avancerede jagtskema [i referencen til avanceret jagt](advanced-hunting-schema-tables.md).

| Kolonnenavn | Datatype | Beskrivelse |
|-------------|-----------|-------------|
| `Timestamp` | `datetime` | Dato og klokkeslæt for registrering af hændelsen |
| `DeviceId` | `string` | Entydigt id for computeren i tjenesten |
| `DeviceName` | `string` | Fuldt kvalificeret domænenavn (FQDN) på computeren |
| `SHA1` | `string` | SHA-1 for den fil, som den registrerede handling blev anvendt på |
| `IsSigned` | `boolean` | Angiver, om filen er signeret |
| `SignatureType` | `string` | Angiver, om signaturoplysningerne blev læst som integreret indhold i selve filen eller læst fra en ekstern katalogfil |
| `Signer` | `string` | Oplysninger om underskriveren af filen |
| `SignerHash` | `string` | Entydig hashværdi, der identificerer underskriveren |
| `Issuer` | `string` | Oplysninger om det udstedende nøglecenter |
| `IssuerHash` | `string` | Entydig hashværdi, der identificerer udstedende nøglecenter (CA) |
| `CertificateSerialNumber` | `string` | Id for det certifikat, der er entydigt for det udstedende nøglecenter (CA) |
| `CrlDistributionPointUrls` | `string` |  JSON-matrix, der viser URL-adresserne til netværksshares, der indeholder certifikater og lister over tilbagekaldte certifikater |
| `CertificateCreationTime` | `datetime` | Dato og klokkeslæt for oprettelse af certifikatet |
| `CertificateExpirationTime` | `datetime` | Dato og klokkeslæt, hvor certifikatet er angivet til at udløbe |
| `CertificateCountersignatureTime` | `datetime` | Dato og klokkeslæt, hvor certifikatet blev kontrasigneret |
| `IsTrusted` | `boolean` | Angiver, om der er tillid til filen på baggrund af resultaterne af funktionen WinVerifyTrust, som kontrollerer, om der er ukendte rodcertifikatoplysninger, ugyldige signaturer, tilbagekaldte certifikater og andre tvivlsomme attributter |
| `IsRootSignerMicrosoft` | `boolean` | Angiver, om underskriveren af rodcertifikatet er Microsoft, og om filen er inkluderet i Windows-operativsystemet |
| `ReportId` | `long` | Hændelses-id baseret på en gentaget tæller. Hvis du vil identificere entydige hændelser, skal denne kolonne bruges sammen med kolonnerne DeviceName og Timestamp. | 

## <a name="related-topics"></a>Relaterede emner
- [Oversigt over avanceret jagt](advanced-hunting-overview.md)
- [Få mere at vide om forespørgselssproget](advanced-hunting-query-language.md)
- [Brug delte forespørgsler](advanced-hunting-shared-queries.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste praksis for forespørgsler](advanced-hunting-best-practices.md)
