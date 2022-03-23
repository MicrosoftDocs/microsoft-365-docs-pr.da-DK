---
title: Kryptering i Microsoft Cloud
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
description: I denne artikel kan du læse en oversigt over de forskellige former for kryptering, der bruges til at holde kundedata sikre i Microsoft-skyen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c888c1958eb5265c31ae981e42a96eeeeb57f3ef
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587315"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Kryptering i Microsoft Cloud

Kundedata inden for Microsofts skybaserede virksomhedstjenester er beskyttet af flere teknologier og processer, herunder forskellige former for kryptering. (Kundedata i dette dokument omfatter Exchange Online-postkasseindhold, brødtekst i mails, kalenderposter og indholdet af vedhæftede filer i mails og om relevant Skype for Business-indhold), SharePoint onlinewebstedsindhold og de filer, der er gemt på websteder, og filer, der er overført til OneDrive for Business  eller Skype for Business). Microsoft bruger flere krypteringsmetoder, protokoller og kryptering på tværs af sine produkter og tjenester for at sikre, at kundedata kan passere gennem vores skytjenester, og for at beskytte fortroligheden af kundedata, der er gemt i vores skytjenester. Microsoft bruger nogle af de stærkeste, mest sikre krypteringsprotokoller, der er tilgængelige, til at skabe hindringer for uautoriseret adgang til kundedata. Ordentlig nøgleadministration er også et vigtigt element i bedste praksis for kryptering, og Microsoft arbejder på at sikre, at alle Microsoft-administrerede krypteringsnøgler er korrekt sikret.

Kundedata, der er gemt i Microsofts skybaserede virksomhedstjenester, er beskyttet ved hjælp af en eller flere former for kryptering. Validering af vores cryptopolitik og håndhævelsen bekræftes uafhængigt af flere tredjepartsrevisorer, og rapporter om disse revisioner er tilgængelige på [Service Trust Portal](https://aka.ms/stp).

Microsoft leverer serviceteknologier, der krypterer kundedata under transport og under overførsel. For eksempel bruger Microsoft Azure [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) og [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt) til kundens data i hvile, og Microsoft 365 bruger BitLocker, [Azure Storage-tjenestekryptering](/azure/), [DISTRIBUTED Key Manager](./exchange-online-secures-email-secrets.md) (DKM) og Microsoft 365-tjenestekryptering. For kundedata under overførsel bruger Azure, Office 365, Microsofts kommercielle support, Microsoft Dynamics 365, Microsoft Power BI og Visual Studio Team Services branchestandardsikkerheds transportprotokoller, f.eks Internet Protocol Security (IPsec) og Transport Layer Security (TLS), mellem Microsoft-datacentre og mellem brugerenheder og Microsoft-datacentre.

Ud over det oprindelige niveau for krypteret sikkerhed leveret af Microsoft, indeholder vores skytjenester også indstillinger for kryptering, som du kan administrere. Du kan f.eks. aktivere kryptering af trafik mellem deres virtuelle Azure-computere (VMs) og deres brugere. Med [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/) kan du bruge branchestandarden IPsec-protokol til at kryptere trafik mellem din virksomheds VPN-gateway og Azure. Du kan også kryptere trafik mellem VM'er på dit virtuelle netværk. Desuden giver [de nye Office 365-meddelelseskryptering dig mulighed](set-up-new-message-encryption-capabilities.md) for at sende krypterede mails til alle.

Efter Den offentlige infrastrukturs driftssikkerhedsstandard, som er en komponent i [Microsofts](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers) sikkerhedspolitik, bruger Microsoft de krypterede funktioner, der er inkluderet i Windows-operativsystemet til certifikater og godkendelsesmekanismer. Disse mekanismer omfatter brugen af krypterede moduler, der opfylder den amerikanske regerings føderale standarder for behandling af [oplysninger (](https://csrc.nist.gov/publications/PubsFIPS.html) FIPS) 140-2-standarden. Du kan søge efter de relevante NIST-certifikatnumre til Microsoft ved hjælp af [cmvp'et for det krypterede modulvalideringsprogram](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [BEMÆRK] For at få adgang til Microsofts sikkerhedspolitik som en ressource skal du logge på med din arbejds- eller skolekonto. Hvis du endnu ikke har et abonnement, [kan du tilmelde dig en gratis prøveversion](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 er en standard, der er udviklet specielt til validering af produktmoduler, der implementerer kryptering i stedet for de produkter, der bruger dem. Krypterede moduler, der implementeres i en tjeneste, kan certificeres til at opfylde kravene til hashstyrke, nøglestyring og lignende. De krypterede moduler og krypteringer, der bruges til at beskytte fortroligheden, integriteten eller tilgængeligheden af data i Microsofts skytjenester, opfylder FIPS 140-2-standarden.

Microsoft certificerer de underliggende krypterede moduler, der bruges i vores skytjenester, med hver ny version Windows operativsystemet:

- Azure og Azure U.S. Government
- Dynamics 365 og Dynamics 365 U.S. Government
- Office 365, Office 365 amerikanske myndigheder og det Office 365 amerikanske forsvar

Kryptering af kundens data in rest leveres af flere teknologier på tjenestesiden, herunder BitLocker, DKM, Azure Storage-tjenestekryptering og tjenestekryptering i Exchange Online, Skype for Business, OneDrive for Business og SharePoint Online. Office 365 indeholder en mulighed for at bruge kunde-administrerede krypteringsnøgler, der er gemt i Azure Key Vault. Denne indstilling for kunde-administreret nøgle, kaldet Kundenøgle[, er](./customer-key-overview.md) tilgængelig Exchange Online, SharePoint Online, Skype for Business og OneDrive for Business.

For kundedata under overførsel forhandler alle Office 365 sikre sessioner med TLS som standard med klientcomputere for at sikre kundedata. Eksempelvis vil Office 365 forhandle sikre sessioner med Skype for Business, Outlook og Outlook på internettet, mobilklienter og webbrowsere.

(Alle kunderettede servere forhandler med TLS 1.2 som standard).

## <a name="related-links"></a>Relaterede links

- [Kryptering i Azure](office-365-azure-encryption.md)
- [BitLocker og Distributed Key Manager (DKM) til kryptering](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365 af tjeneste](office-365-service-encryption.md)
- [Office 365 kryptering til Skype for Business, OneDrive for Business, SharePoint Online og Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Kryptering af data under overførsel](/compliance/assurance/assurance-encryption-in-transit)
- [Kunde-administrerede krypteringsfunktioner](office-365-customer-managed-encryption-features.md)
- [Krypteringsrisici og beskyttelse](office-365-encryption-risks-and-protections.md)
- [Kryptering i Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)