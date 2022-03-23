---
title: Test Base API & SDK
description: Test Base API & SDK
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
ms.openlocfilehash: f7e5edeeac79b417bcb41f8607c46fc8894ea4fc
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63593617"
---
# <a name="manage-your-resource-with-sdk--apis"></a>Administrere din ressource med SDK-& API'er
Automatisering er et vigtigt aspekt af DevOps og Agile-udvikling. Ønsker du at administrere Test Base for Microsoft 365 ressourcer, få testresultater programmeringelt og integrere dem med vores CI-værktøjer? Test base-API'er/SDK kan hjælpe dig med at opnå alt dette og meget mere! 

Disse API'er/SDK gør it-fagfolk og appudviklere i stand til at: 
- Administrer Test Base-konti, herunder opret, opdater og offboard. 
- Administrer programpakker, herunder opret, opdater, slet og download pakke. 
- Få testoversigten, detaljerede testresultater og analyseresultater. Analyseresultatet omfatter CPU-regressionsanalyse, ANALYSE af CPU-udnyttelse, regressionsanalyse af hukommelse og analyse af hukommelsesudnyttelse. 
- Download testresultater og videooptagelse af testkørsel.  

Se den trinvise disposition nedenfor for at finde ud af, hvordan du får adgang til denne nye funktion i Test Base for Microsoft 365 tjeneste.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Et trinvist eksempel på oprettelse af Test Base-konto ved hjælp af Python SDK

1. Forudsætninger: 

- Installér under påkrævede komponenter: 

    [Azure-konto med et aktivt](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) abonnement, hvis du ikke har et abonnement<br>
    [Python 2.7+ eller 3.6+](https://www.python.org/downloads)<br>
    [Azure Command-Line Interface (CLI)](/cli/azure/install-azure-cli) <br>

- Installér bibliotekspakker ved hjælp af rørinstallation fra konsol 

```
pip install azure-identity 
pip install azure-mgmt-testbase
```

- Godkendelse i udviklingsmiljø 

Ved fejlfinding og udførelse af kode lokalt er det typisk for udviklere at bruge deres egne konti til godkendelse af opkald til Azure-tjenester. Azure-identitetspakken understøtter godkendelse via Azure CLI for at forenkle den lokale udvikling. Hvis du vil logge på Azure CLI, skal du køre ```az login ```. På et system med en standardwebbrowser starter Azure CLI browseren for at godkende en bruger. 

Kontrollér [, hvordan du godkender Python-programmer med Azure-tjenester| Microsoft Docs](/azure/developer/python/azure-sdk-authenticate)  og [https://pypi.org/project/azure-identity/](https://pypi.org/project/azure-identity/) andre understøttede godkendelsesmetoder. 

 - Opret en ressourcegruppe med dit ønskede navn, som skal bruges i følgende trin. 

2. Nedenstående kodestykke dækker flow til oprettelse af en Test Base-konto, herunder 

- Anmod om legitimationsoplysninger via Azure CLI for at interagere med Azure 
- Initialisere Test Base SDK-klient med legitimationsoplysninger og abonnements-id for senere handlinger 
- Invoke begin_create from test_base_accounts model for at oprette Test Base Account 

Kopiér koden til dit Python-udviklingsmiljø, og erstat "subscription-id" med dit Azure-abonnements-id og "resource-group-name" med din ressourcegruppe, du oprettede ovenfor. 

 
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

Se nedenstående links for at få mere at vide om SDK & API. 

**Azure-abonnement** 

- [Azure-konto med et aktivt abonnement](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK** 

- [Dokumentation til Test Base Python SDK](/python/api/overview/azure/mgmt-testbase-readme)
- [TEST Base Python SDK-eksempel](https://aka.ms/testbase-sample-py)
- [Azure Generelt brugsmønster for Python SDK](/azure/developer/python/azure-sdk-overview#provision-and-manage-azure-resources-with-management-libraries)

**REST-API**  

- [REST API-dokumentation](https://aka.ms/testbase-api)  
