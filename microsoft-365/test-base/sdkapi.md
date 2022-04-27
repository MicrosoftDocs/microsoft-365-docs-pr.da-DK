---
title: Testbase-API & SDK
description: Testbase-API & SDK
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 6ae0fdf9cc49faaaff84eb3f96e076d1efba8a4c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65077431"
---
# <a name="manage-your-resource-with-sdk--apis"></a>Administrer din ressource med API'er til SDK-&

Automatisering er et vigtigt aspekt i DevOps og fleksibel udvikling. Ønsker du at administrere testbasen for Microsoft 365 ressourcer, få testresultater programmatisk og integrere dem med vores CI-værktøjer? Testbase-API'er/SDK'er kan hjælpe dig med at opnå alle disse og meget mere!

Disse API'er/SDK gør det muligt for it-teknikere og appudviklere at:

- Administrer testbasekonti, herunder oprettelse, opdatering og offboard.
- Administrer programpakker, herunder opret, opdater, slet og download pakke.
- Hent testoversigten, detaljerede testresultater og analyseresultater. Analyseresultatet omfatter analyse af CPU-regression, analyse af CPU-udnyttelse, analyse af hukommelsesregression og analyse af hukommelsesudnyttelse.
- Download testresultater og videooptagelse af udførelse af test.

Se den trinvise oversigt nedenfor for at finde ud af, hvordan du får adgang til denne nye funktion i testbasen for Microsoft 365 tjeneste.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Et trinvist eksempel på oprettelse af en Test Base-konto ved hjælp af Python SDK

1. Forudsætninger:

   - Installér under påkrævede komponenter:

     - [Azure-konto med et aktivt abonnement](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) , hvis du ikke har et abonnement
     - [Python 2,7+ eller 3,6+](https://www.python.org/downloads)
     - [Azure Command-Line Interface (CLI)](/cli/azure/install-azure-cli)

   - Installér bibliotekspakker ved hjælp af pip-installation fra konsollen

     ```console
     pip install azure-identity
     pip install azure-mgmt-testbase
     ```

   - Godkender i udviklingsmiljø

     Når du foretager fejlfinding og udfører kode lokalt, er det typisk for udviklere at bruge deres egne konti til godkendelse af opkald til Azure-tjenester. Azure-identitetspakken understøtter godkendelse via Kommandolinjegrænsefladen i Azure for at forenkle den lokale udvikling. Hvis du vil logge på kommandolinjegrænsefladen i Azure, skal du køre `az login`. I et system med en standardwebbrowser starter Kommandolinjegrænsefladen i Azure browseren for at godkende en bruger.

     Se [Sådan godkender du Python-programmer med Azure-tjenester| Microsoft Docs](/azure/developer/python/azure-sdk-authenticate) og <https://pypi.org/project/azure-identity/> for andre understøttede godkendelsesmetoder.

   - Opret en ressourcegruppe med det ønskede navn, som skal bruges i følgende trin.

2. Under kodestykket nedenfor beskrives flowet for oprettelse af en testbasiskonto, herunder

   - Anmod om legitimationsoplysninger via kommandolinjegrænsefladen i Azure for at få interaktion med Azure
   - Initialiser Test Base SDK-klienten med legitimationsoplysningerne og abonnements-id'et for senere handlinger
   - Aktivér begin_create fra test_base_accounts model for at oprette en testbasiskonto

   Kopiér koden til dit Python-udviklingsmiljø, og erstat "subscription-id" med dit Azure-abonnements-id og "resource-group-name" med din ressourcegruppe, du har oprettet ovenfor.

   ```python
   from azure.identity import AzureCliCredential
   from azure.mgmt.testbase import TestBase
   from azure.mgmt.testbase.models import TestBaseAccountResource
   from azure.mgmt.testbase.models import TestBaseAccountSKU

   # requesting token from Azure CLI for request
   # For other authentication approaches, please see: https://pypi.org/project/azure-identity/
   credential = AzureCliCredential()
   subscription_id = "<subscription-id>"
   resource_group = "<resource-group-name>"
   testBaseAccount_name = "contoso-testbaseAccount"
   testBaseAccount_location = "global"
   sku_name = "S0"
   sku_tier = "Standard"
   sku_locations = {"global"}
  
   # Create client
   testBase_client = TestBase(credential, subscription_id)
  
   # Create sku for test base account
   sku = TestBaseAccountSKU(name=sku_name, tier=sku_tier, locations=sku_locations)
  
   # Create test base account
   parameters = TestBaseAccountResource(location=testBaseAccount_location, sku=sku)
   testBaseAccount = testBase_client.test_base_accounts.begin_create(resource_group, testBaseAccount_name, parameters).result()
   print("Create test base account:\n{}".format(testBaseAccount))
   ```

## <a name="learn-more"></a>Lær mere

Se nedenfor links for at få flere oplysninger om API'en til SDK &.

**Azure-abonnement**:

- [Azure-konto med et aktivt abonnement](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK**:

- [Dokumentation til Test Base Python SDK](/python/api/overview/azure/mgmt-testbase-readme)
- [Test grundlæggende Python SDK-eksempel](https://aka.ms/testbase-sample-py)
- [Azure General Usage Pattern of Python SDK](/azure/developer/python/sdk/azure-sdk-library-usage-patterns)

**REST API**:

- [Dokumentation til REST API](https://aka.ms/testbase-api)
