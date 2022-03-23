---
title: Kryptering i Azure
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Få mere at vide om tilgængelig kryptering i Azure, f.eks. Azure-diskkryptering
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f3672800b6f90277195a63b640911ea1ed24cac9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589552"
---
# <a name="encryption-in-azure"></a>Kryptering i Azure

Teknologiske sikkerhedsforanstaltninger i Azure, f.eks. krypteret kommunikation og driftsprocesser, hjælper med at holde dine data sikre. Du har også fleksibilitet til at implementere yderligere krypteringsfunktioner og administrere dine egne krypterede nøgler. Uanset kundekonfiguration anvender Microsoft kryptering til at beskytte kundedata i Azure. Microsoft giver dig også mulighed for at styre dine data, der hostes i Azure, via en række avancerede teknologier til at kryptere, kontrollere og administrere krypterede nøgler samt styre og overvåge adgang til data. Derudover indeholder Azure Storage et omfattende sæt sikkerhedsfunktioner, som sammen giver udviklere mulighed for at opbygge sikre programmer.

Azure indeholder mange mekanismer til at beskytte data, når de flyttes fra én placering til en anden. Microsoft bruger TLS til at beskytte data, når de rejser mellem skytjenesterne og kunderne. Microsofts datacentre forhandler en TLS-forbindelse med klientsystemer, der opretter forbindelse til Azure-tjenester. Perfect Forward Pfs (PFS) beskytter forbindelser mellem kundernes klientsystemer og Microsofts skytjenester ved hjælp af unikke nøgler. Forbindelser bruger også RSA-baserede 2.048-bit krypteringsnøglelængder. Denne kombination gør det svært for nogen at opfange og få adgang til data, der er under overførsel.

Data kan beskyttes under overførsel mellem et program og Azure ved hjælp af kryptering på klientsiden [, HTTPS](/azure/storage/storage-client-side-encryption) eller SMB 3.0. Du kan aktivere kryptering af trafik mellem dine egne virtuelle maskiner (VMs) og dine brugere. Med [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/) kan du bruge branchestandarden IPsec-protokol til at kryptere trafik mellem din virksomheds VPN-gateway og Azure samt mellem de VM'er, der er placeret på dit virtuelle netværk.

Når det kommer til data i hvile, tilbyder Azure mange krypteringsmuligheder, f.eks. understøttelse af AES-256, der giver dig fleksibilitet til at vælge det datalagerscenarie, der bedst opfylder dine behov. Data kan krypteres automatisk, når de skrives til Azure Storage ved hjælp [af Storage-tjenestekryptering](/azure/storage/storage-service-encryption), og operativsystem- og datadisks, der bruges af VM'er, kan krypteres. Få mere at vide under [Sikkerhedsanbefalinger for Windows virtuelle maskiner i Azure](/azure/security/azure-security-disk-encryption). Desuden kan delegeret adgang til dataobjekter i Azure Storage gives ved hjælp [af Delte access-signaturer](/azure/storage/storage-dotnet-shared-access-signature-part-1). Azure leverer også kryptering til inaktivitetsdata ved hjælp [af gennemsigtig datakryptering til Azure SQL Database og Data Warehouse](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Du kan finde flere oplysninger om kryptering i Azure i [Oversigt over Azure-kryptering](/azure/security/security-azure-encryption-overview) [og Azure-datakryptering -at-Rest](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Azure-diskkryptering

Azure-diskkryptering gør det muligt at kryptere Windows og Linux-infrastruktur som en service -VM-diske (IaaS). Azure-diskkryptering anvender BitLocker-funktionen i Windows og DM-Crypt-funktionen til Linux til at levere kryptering på volumenniveau til operativsystemet og datadiskerne. Det sikrer også, at alle data på VM-diskene er krypteret indisken i din Azure-lagerplads. Azure Disk Encryption er integreret med Azure Key Vault for at hjælpe dig med at styre, administrere og overvåge brugen af krypteringsnøgler og hemmeligheder.

Få mere at vide under [Sikkerhedsanbefalinger for Windows virtuelle maskiner i Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Azure Storage af tjeneste

Med [Azure Storage tjenestekryptering](/azure/storage/storage-service-encryption) krypterer Azure Storage automatisk data, før de gemmes, til lagring og dekrypterer data, før der hentes. Krypteringen, dekrypteringsprocessen og nøgleadministrationsprocesserne er helt gennemsigtige for brugerne. Azure Storage tjenestekryptering kan bruges til [Azure Blob-Storage og](https://azure.microsoft.com/services/storage/blobs/) [Azure-filer](https://azure.microsoft.com/services/storage/files/). Du kan også bruge Microsoft-administrerede krypteringsnøgler med Azure Storage af tjenestekryptering, eller du kan bruge dine egne krypteringsnøgler. (Du kan finde oplysninger om brug af dine egne nøgler [i Storage tjenestekryptering ved hjælp af kunde-administrerede nøgler i Azure Key Vault](/azure/storage/common/storage-service-encryption-customer-managed-keys). Du kan finde oplysninger om brug af Microsoft-administrerede nøgler [Storage kryptering af tjeneste til data på rest-tasten](/azure/storage/storage-service-encryption). Desuden kan du automatisere brugen af kryptering. Du kan f.eks. aktivere eller deaktivere Storage-tjenestekryptering på en lagerkonto ved hjælp af [Azure Storage Resource Provider REST API](/rest/api/storagerp/), [Storage Resource Provider Client Library til .NET](/dotnet/api/overview/azure/storage), [Azure PowerShell](/powershell/azureps-cmdlets-docs) eller [Azure CLI](/azure/storage/storage-azure-cli).

Nogle Microsoft 365 bruger Azure til at lagre data. Eksempel: SharePoint Online og OneDrive for Business gemmer data i Azure Blob-lagerplads, og Microsoft Teams gemmer data for dens chattjeneste i tabeller, blobs og køer. Desuden gemmer overholdelsesstyringsfunktionen i Microsoft 365 Overholdelsescenter data, som er indtastet af kunden, og som gemmes i krypteret form i [Azure Azure Azure Azure DB](/azure/cosmos-db/database-encryption-at-rest), en Platform as a Service (PaaS), global distribueret database med flere modeller. Azure Storage-tjenestekryptering krypterer data, der er gemt i Azure Blob-lagerplads og i tabeller, og Azure-diskkryptering krypterer data i køer samt virtuelle Windows- og IaaS-diske for at levere volumenkryptering til operativsystemet og datadisken. Løsningen sikrer, at alle data på de virtuelle diske er krypteret in dit Azure-lager. [Kryptering i Azure Azure Azures DB implementeres](/azure/cosmos-db/database-encryption-at-rest) ved hjælp af flere sikkerhedsteknologier, herunder sikre nøglelagersystemer, krypterede netværk og krypterede API'er.

## <a name="azure-key-vault"></a>Azure Key Vault

Sikker nøgleadministration er ikke blot kernen i bedste praksis for kryptering; er det også vigtigt for at beskytte data i skyen. [Azure Key Vault gør](/azure/key-vault/key-vault-whatis) det muligt at kryptere nøgler og små hemmeligheder som adgangskoder, der bruger nøgler, der er gemt i hardwaresikkerhedsmoduler (HSMs). Azure Key Vault er Microsofts anbefalede løsning til administration og kontrol af adgang til krypteringsnøgler, der bruges af skytjenester. Tilladelser til at få adgang til nøgler kan tildeles til tjenester eller til brugere med Azure Active Directory konti. Azure Key Vault letter organisationers behov for at konfigurere, installere og vedligeholde HSMs og nøgleadministrationssoftware. Med Azure Key Vault ser Microsoft aldrig dine nøgler og programmer har ikke direkte adgang til dem. du bevarer kontrollen. Du kan også importere eller generere nøgler i HSMs. Organisationer, der har et abonnement, der omfatter Azure Information Protection, kan konfigurere deres Azure Information Protection-lejer til at bruge en kunde-administreret nøgle [Bring Your Own Key](/information-protection/plan-design/byok-price-restrictions) (BYOK)) og [logføre brugen af den](/information-protection/deploy-use/log-analyze-usage).