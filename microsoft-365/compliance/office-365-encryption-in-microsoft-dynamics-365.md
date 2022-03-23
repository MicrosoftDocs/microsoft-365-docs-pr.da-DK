---
title: Kryptering i Microsoft Dynamics 365
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
ms.collection: Strat_O365_Enterprise
description: Få mere at vide om, hvordan Microsoft bruger krypteringsteknologi til at beskytte kundedata i Microsoft Dynamics 365, mens de ligger i en Microsoft-database og under overførsel.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ba3dbef73b7674364f19e83befdbb8cdfe417ad6
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63589167"
---
# <a name="encryption-in-microsoft-dynamics-365"></a>Kryptering i Microsoft Dynamics 365

Microsoft bruger krypteringsteknologi til at beskytte kundedata i Dynamics 365, mens de er i hvile i et Microsoft-datacenter, og mens det er i transit mellem brugerenheder og vores datacentre. Forbindelser, der er oprettet mellem kunder og Microsoft-datacentre, krypteres, og alle offentlige slutpunkter er sikret ved hjælp af branchestandard-TLS. TLS etablerer på effektiv vis en sikkerhedsregeret browser-til-server-forbindelse for at sikre datafortrolighed og integritet mellem skriveborde og datacentre. Når datakryptering er aktiveret, kan den ikke deaktiveres. Du kan finde flere oplysninger [under Kryptering af data på feltniveau](/previous-versions/dynamicscrm-2016/developers-guide/dn481562(v=crm.8)).

Dynamics 365 bruger standardkryptering på Microsoft SQL Server celleniveau til et sæt standardenhedsattributter, der indeholder følsomme oplysninger, f.eks. brugernavne og mailadgangskoder. Denne funktion kan hjælpe organisationer med at opfylde de krav, der er knyttet til FIPS 140-2. Datakryptering på feltniveau er især vigtigt i scenarier, der udnytter [](/previous-versions/dynamicscrm-2016/administering-dynamics-365/hh699800(v=crm.8))Microsoft Dynamics CRM-mailouteren, som skal gemme brugernavne og adgangskoder for at aktivere integration mellem en Dynamics 365-forekomst og en mailtjeneste.

Alle forekomster af Dynamics 365 bruger [Microsoft SQL Server gennemsigtig datakryptering](/sql/relational-databases/security/encryption/transparent-data-encryption) (TDE) til at udføre kryptering af data i realtid, når de skrives til disken (i hvile). TDE krypterer SQL Server, Azure SQL Database og Azure SQL datafiler fra Data Warehouse. Som standard gemmer og administrerer Microsoft databasekrypteringsnøglerne for dine forekomster af Dynamics 365. (De nøgler, der bruges af Dynamics 365 til finansielle midler, genereres af .NET Framework databeskyttelses-API.)

Funktionen Administrer nøgler i Dynamics 365 Administration giver administratorer mulighed for selv at administrere de databasekrypteringsnøgler, der er knyttet til forekomster af Dynamics 365. (Selv-administrerede databasekrypteringsnøgler er kun tilgængelige i opdateringen for januar 2017 til Microsoft Dynamics 365 og bliver muligvis ikke tilgængelig for senere versioner. Få mere at vide under [Administrer krypteringsnøgler for din Dynamics 365-forekomst (online](/dynamics365/customer-engagement/admin/manage-encryption-keys-instance)). Nøgleadministrationsfunktionen understøtter både PFX- og BYOK-krypteringsnøglefiler, f.eks. filer, der er gemt i en HSM. (Du kan finde flere oplysninger om at generere og overføre en HSM-beskyttet nøgle via internettet under Sådan genererer og overfører [du HSM-beskyttede nøgler til Azure Key Vault](/azure/key-vault/key-vault-hsm-protected-keys)).

Hvis du vil bruge indstillingen uploadkrypteringsnøgle, skal du bruge både den offentlige og den private krypteringsnøgle.

Funktionen Nøgleadministration fjerner kompleksiteten fra krypteringsnøgleadministrationen ved at bruge Azure Key Vault til sikkert at gemme krypteringsnøgler. Azure Key Vault hjælper med at beskytte krypterede nøgler og hemmeligheder, der bruges af programmer og tjenester i skyen. Nøgleadministrationsfunktionen kræver ikke, at du har et abonnement på Azure Key Vault, og i de fleste situationer er der ingen grund til at få adgang til de krypteringsnøgler, der bruges til Dynamics 365 i boksen.
