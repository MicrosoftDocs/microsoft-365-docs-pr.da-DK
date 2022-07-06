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
description: I denne artikel kan du læse en oversigt over de forskellige former for kryptering, der bruges til at beskytte kundedata i Microsoft-cloudmiljøet.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3105da5d17b1656ffa0d29da4f4aa02c9a9f9064
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633911"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Kryptering i Microsoft Cloud

Kundedata i Microsofts cloudtjenester til virksomheder er beskyttet af flere teknologier og processer, herunder forskellige former for kryptering. (Kundedata i dette dokument omfatter Exchange Online postkasseindhold, mailbrødtekst, kalenderposter og indholdet af vedhæftede filer i mails, og hvis det er relevant, Skype for Business indhold), indhold på SharePoint Online-webstedet og de filer, der er gemt på websteder, og filer, der er uploadet til OneDrive for Business eller Skype for Business.) Microsoft bruger flere krypteringsmetoder, protokoller og ciffer på tværs af sine produkter og tjenester for at hjælpe med at levere en sikker sti til kundedata til at rejse gennem vores cloudtjenester og til at beskytte fortroligheden af kundedata, der er gemt i vores cloudtjenester. Microsoft bruger nogle af de stærkeste og mest sikre krypteringsprotokoller, der er tilgængelige, til at skabe barrierer mod uautoriseret adgang til kundedata. Korrekt administration af nøgler er også et vigtigt element i bedste praksis for kryptering, og Microsoft arbejder for at sikre, at alle Microsoft-administrerede krypteringsnøgler sikres korrekt.

Kundedata, der er gemt i Microsofts cloudtjenester til virksomheder, beskyttes ved hjælp af en eller flere former for kryptering. Validering af vores kryptografipolitik og dens håndhævelse bekræftes uafhængigt af flere tredjepartsrevisorer, og rapporter om disse revisioner er tilgængelige på [Service Trust Portal](https://aka.ms/stp).

Microsoft leverer teknologier på tjenestesiden, der krypterer inaktive og under overførsel af kundedata. For inaktive kundedata bruger Microsoft Azure [f.eks. BitLocker](/windows/device-security/bitlocker/bitlocker-overview) og [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt), og Microsoft 365 bruger BitLocker, [Azure Storage Service Encryption](/azure/), [Distributed Key Manager](./exchange-online-secures-email-secrets.md) (DKM) og Microsoft 365-tjenestekryptering. I forbindelse med kundedata under overførsel bruger Azure, Office 365, Microsoft Commercial Support, Microsoft Dynamics 365, Microsoft Power BI og Visual Studio Team Services branchestandardsikre transportprotokoller, f.eks. Internet Protocol Security (IPsec) og TLS (Transport Layer Security) mellem Microsoft-datacentre og mellem brugerenheder og Microsoft-datacentre.

Ud over det grundlæggende niveau for kryptografisk sikkerhed, der leveres af Microsoft, omfatter vores cloudtjenester også kryptografiske indstillinger, som du kan administrere. Du kan f.eks. aktivere kryptering for trafik mellem deres virtuelle Azure-maskiner (VM'er) og deres brugere. Med [Azure Virtual Networks](https://azure.microsoft.com/services/virtual-network/) kan du bruge branchestandarden iPsec-protokollen til at kryptere trafikken mellem din virksomheds VPN-gateway og Azure. Du kan også kryptere trafik mellem VM'er på dit virtuelle netværk. Derudover giver [nye Office 365 funktioner til meddelelseskryptering](set-up-new-message-encryption-capabilities.md) dig mulighed for at sende krypterede mails til alle.

Efter standarden for driftsmæssig sikkerhed for infrastruktur for offentlige nøgler, som er en komponent i [Microsofts sikkerhedspolitik](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers), bruger Microsoft de kryptografiske funktioner, der er inkluderet i Windows-operativsystemet, til certifikater og godkendelsesmekanismer. Disse mekanismer omfatter brug af kryptografiske moduler, der opfylder den amerikanske regerings FIPS 140-2-standard ( [Federal Information Processing Standards](https://csrc.nist.gov/publications/PubsFIPS.html) ). Du kan søge efter de relevante NIST-certifikatnumre for Microsoft ved hjælp af [CMVP'en til kryptografisk modulvalideringsprogram](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [NOTE] Hvis du vil have adgang til Microsofts sikkerhedspolitik som en ressource, skal du logge på med din arbejds- eller skolekonto. Hvis du endnu ikke har et abonnement, [kan du tilmelde dig en gratis prøveversion](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2 er en standard, der er udviklet specielt til validering af produktmoduler, der implementerer kryptografi i stedet for de produkter, der bruger dem. Kryptografiske moduler, der implementeres i en tjeneste, kan certificeres som opfylder kravene til hashstyrke, nøgleadministration og lignende. De kryptografiske moduler og ciffer, der bruges til at beskytte fortroligheden, integriteten eller tilgængeligheden af data i Microsofts cloudtjenester, opfylder FIPS 140-2-standarden.

Microsoft certificerer de underliggende kryptografiske moduler, der bruges i vores cloudtjenester, med hver ny version af Windows-operativsystemet:

- Azure og Azure U.S. Government
- Dynamics 365 og Dynamics 365 US Government
- Office 365, Office 365 amerikanske regering og Office 365 amerikanske regeringsforsvar

Kryptering af inaktive kundedata leveres af flere teknologier på tjenestesiden, herunder BitLocker, DKM, Azure Storage Service Encryption og tjenestekryptering i Exchange Online, Skype for Business, OneDrive for Business og SharePoint Online. Office 365 tjenestekryptering indeholder en mulighed for at bruge kundeadministrerede krypteringsnøgler, der er gemt i Azure Key Vault. Denne kundeadministrerede nøgleindstilling kaldet [Kundenøgle](./customer-key-overview.md) er tilgængelig for Exchange Online, SharePoint Online, Skype for Business og OneDrive for Business.

For kundedata under overførsel forhandler alle Office 365 servere som standard sikre sessioner ved hjælp af TLS med klientcomputere for at beskytte kundedata. Office 365 forhandler f.eks. sikre sessioner til Skype for Business, Outlook og Outlook på internettet, mobilklienter og webbrowsere.

(Alle kundeorienterede servere forhandler som standard til TLS 1.2).

## <a name="related-links"></a>Relaterede links

- [Kryptering i Azure](office-365-azure-encryption.md)
- [BitLocker og DKM (Distributed Key Manager) til kryptering](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365-tjenestekryptering](office-365-service-encryption.md)
- [Office 365 Kryptering af Skype for Business, OneDrive for Business, SharePoint Online og Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Kryptering af data under overførsel](/compliance/assurance/assurance-encryption-in-transit)
- [Kundeadministrerede krypteringsfunktioner](office-365-customer-managed-encryption-features.md)
- [Krypteringsrisici og -beskyttelser](office-365-encryption-risks-and-protections.md)
- [Kryptering i Microsoft Dynamics 365](office-365-encryption-in-microsoft-dynamics-365.md)
