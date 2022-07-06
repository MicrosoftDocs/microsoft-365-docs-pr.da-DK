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
description: Få mere at vide om tilgængelig kryptering i Azure, f.eks. Azure Disk Encryption
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66fb4e54c0837534d6943372d84cf3a4864e4739
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632173"
---
# <a name="encryption-in-azure"></a>Kryptering i Azure

Teknologiske sikkerhedsforanstaltninger i Azure, f.eks. krypteret kommunikation og driftsprocesser, hjælper med at beskytte dine data. Du har også fleksibiliteten til at implementere yderligere krypteringsfunktioner og administrere dine egne kryptografiske nøgler. Uanset kundekonfiguration anvender Microsoft kryptering for at beskytte kundedata i Azure. Microsoft giver dig også mulighed for at styre dine data, der hostes i Azure, via en række avancerede teknologier til at kryptere, styre og administrere kryptografiske nøgler og styre og overvåge adgang til data. Desuden indeholder Azure Storage et omfattende sæt sikkerhedsfunktioner, der tilsammen gør det muligt for udviklere at bygge sikre programmer.

Azure tilbyder mange mekanismer til beskyttelse af data, når de flyttes fra ét sted til et andet. Microsoft bruger TLS til at beskytte data, når de kører mellem cloudtjenesterne og kunderne. Microsofts datacentre forhandler en TLS-forbindelse med klientsystemer, der opretter forbindelse til Azure-tjenester. PFS (Perfect Forward Secrecy) beskytter forbindelser mellem kundernes klientsystemer og Microsofts cloudtjenester ved hjælp af entydige nøgler. Forbindelser bruger også RSA-baserede 2.048-bit krypteringsnøglelængder. Denne kombination gør det svært for nogen at opfange og få adgang til data, der er under overførsel.

Data kan sikres under overførsel mellem et program og Azure ved hjælp af [kryptering på klientsiden](/azure/storage/storage-client-side-encryption), HTTPS eller SMB 3.0. Du kan aktivere kryptering for trafik mellem dine egne virtuelle maskiner (VM'er) og dine brugere. Med [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/) kan du bruge branchestandarden iPsec-protokollen til at kryptere trafik mellem virksomhedens VPN-gateway og Azure samt mellem de VM'er, der er placeret på din Virtual Network.

Azure tilbyder mange krypteringsmuligheder til inaktive data, f.eks. understøttelse af AES-256, hvilket giver dig fleksibiliteten til at vælge det datalagerscenarie, der bedst opfylder dine behov. Data kan krypteres automatisk, når de skrives til Azure Storage ved hjælp af [Storage Service Encryption](/azure/storage/storage-service-encryption), og operativsystemet og de datadiske, der bruges af VM'er, kan krypteres. Du kan få flere oplysninger under [Sikkerhedsanbefalinger til virtuelle Windows-maskiner i Azure](/azure/security/azure-security-disk-encryption). Derudover kan delegeret adgang til dataobjekter i Azure Storage tildeles ved hjælp af [delte adgangssignaturer](/azure/storage/storage-dotnet-shared-access-signature-part-1). Azure leverer også kryptering af inaktive data ved hjælp af [Transparent Data Encryption til Azure SQL Database og Data Warehouse](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Du kan få flere oplysninger om kryptering i Azure i [Oversigt over Azure-kryptering](/azure/security/security-azure-encryption-overview) og [Azure Data Encryption-at-Rest](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Azure-diskkryptering

Azure Disk Encryption gør det muligt for dig at kryptere dine VM-diske til Windows og Linux Infrastructure as a Service (IaaS). Azure Disk Encryption udnytter BitLocker-funktionen i Windows og funktionen DM-Crypt i Linux til at levere kryptering på diskenhedsniveau for operativsystemet og datadisketene. Det sikrer også, at alle data på VM-diskene krypteres som inaktive data i dit Azure-lager. Azure Disk Encryption er integreret i Azure Key Vault for at hjælpe dig med at styre, administrere og overvåge brugen af krypteringsnøgler og hemmeligheder.

Du kan få flere oplysninger under [Sikkerhedsanbefalinger til virtuelle Windows-maskiner i Azure](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Kryptering af Azure Storage-tjeneste

Med [Azure Storage Service Encryption](/azure/storage/storage-service-encryption) krypterer Azure Storage automatisk data, før de bevares på lageret, og dekrypterer data før hentning. Krypterings-, dekrypterings- og nøgleadministrationsprocesserne er helt gennemsigtige for brugerne. Azure Storage Service Encryption kan bruges til [Azure Blob Storage](https://azure.microsoft.com/services/storage/blobs/) og [Azure Files](https://azure.microsoft.com/services/storage/files/). Du kan også bruge Microsoft-administrerede krypteringsnøgler med Azure Storage Service Encryption, eller du kan bruge dine egne krypteringsnøgler. (Du kan få oplysninger om, hvordan du bruger dine egne nøgler, under [Kryptering af lagertjeneste ved hjælp af kundeadministrerede nøgler i Azure Key Vault](/azure/storage/common/storage-service-encryption-customer-managed-keys). Du kan få oplysninger om brug af Microsoft-administrerede nøgler under [Storage Service Encryption for Data inaktive data](/azure/storage/storage-service-encryption).) Derudover kan du automatisere brugen af kryptering. Du kan f.eks. aktivere eller deaktivere storagetjenestekryptering på en lagerkonto ved hjælp af [REST API'en til Azure Storage Resource Provider](/rest/api/storagerp/), [klientbiblioteket for lagerressourceudbyder for .NET](/dotnet/api/overview/azure/storage), [Azure PowerShell](/powershell/azureps-cmdlets-docs) eller [Azure CLI](/azure/storage/storage-azure-cli).

Nogle Microsoft 365-tjenester bruger Azure til lagring af data. SharePoint Online og OneDrive for Business f.eks. gemme data i Azure Blob Storage, og Microsoft Teams gemmer data til chattjenesten i tabeller, blobs og køer. Derudover gemmer funktionen Overholdelsesstyring i Microsoft Purview-compliance-portal kundeangivet data, som er gemt i krypteret form i [Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest), en PaaS (Platform as a Service), globalt distribueret database med flere modeller. Azure Storage Service Encryption krypterer data, der er gemt i Azure Blob Storage og i tabeller, og Azure Disk Encryption krypterer data i køer samt diske med virtuelle Windows- og IaaS-maskiner for at give diskenhedskryptering til operativsystemet og datadisken. Løsningen sikrer, at alle data på diskene på den virtuelle maskine krypteres som inaktive data i dit Azure-lager. [Inaktiv kryptering i Azure Cosmos DB](/azure/cosmos-db/database-encryption-at-rest) implementeres ved hjælp af flere sikkerhedsteknologier, herunder sikre nøglelagringssystemer, krypterede netværk og kryptografiske API'er.

## <a name="azure-key-vault"></a>Azure Key Vault

Sikker nøgleadministration er ikke kun kernen i bedste praksis for kryptering. Det er også vigtigt for at beskytte data i cloudmiljøet. [Med Azure Key Vault](/azure/key-vault/key-vault-whatis) kan du kryptere nøgler og små hemmeligheder, f.eks. adgangskoder, der bruger nøgler, der er gemt i HSM'er (Hardware Security Modules). Azure Key Vault er Microsofts anbefalede løsning til administration og styring af adgang til krypteringsnøgler, der bruges af cloudtjenester. Tilladelser til adgangsnøgler kan tildeles til tjenester eller til brugere med Azure Active Directory-konti. Azure Key Vault aflaster organisationer for behovet for at konfigurere, reparere og vedligeholde HSM'er og software til administration af nøgler. Med Azure Key Vault kan Microsoft aldrig se, at dine nøgler og programmer ikke har direkte adgang til dem. Du bevarer kontrollen. Du kan også importere eller generere nøgler i HSM'er. Organisationer, der har et abonnement, der indeholder Azure Information Protection, kan konfigurere deres Azure Information Protection-lejer til at bruge en kundeadministrerede nøgle [BYOK (Bring Your Own Key](/information-protection/plan-design/byok-price-restrictions))) og [logføre brugen af den](/information-protection/deploy-use/log-analyze-usage).
