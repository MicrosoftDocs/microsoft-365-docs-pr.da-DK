---
title: Kundeadministrerede krypteringsfunktioner
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
ms.custom:
- seo-marvel-mar2020
description: I denne artikel får du mere at vide om krypteringsteknologier, som du kan administrere og konfigurere i Microsoft 365.
ms.openlocfilehash: 55bc743f83b79ac83c764af24ef4100e5f72369d
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622545"
---
# <a name="customer-managed-encryption-features"></a>Kundeadministrerede krypteringsfunktioner

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [Microsoft Purview-meddelelseskryptering](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [Sikker mailflow med en partnerorganisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Du kan få flere oplysninger om disse teknologier i [tjenestebeskrivelserne for Microsoft 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) er den beskyttelsesteknologi, der bruges af [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection). Den bruger politikker for kryptering, identitet og godkendelse til at beskytte dine filer og mails på tværs af flere platforme og enheder – telefoner, tablets og pc'er. Oplysninger kan beskyttes både i og uden for din organisation, fordi beskyttelsen forbliver sammen med dataene. Azure RMS sikrer vedvarende beskyttelse af alle filtyper, beskytter filer overalt, understøtter samarbejde mellem virksomheder og en lang række Windows og ikke-Windows enheder. Azure RMS Protection kan også forbedre [politikker til forebyggelse af datatab (DLP).](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention) Du kan få flere oplysninger om, hvilke programmer og tjenester der kan bruge Azure Rights Management-tjenesten fra Azure Information Protection, under [Sådan understøtter programmer Azure Rights Management-tjenesten](/information-protection/understand-explore/applications-support).

Azure RMS er integreret med Microsoft 365 og tilgængelig for alle kunder. Hvis du vil konfigurere Microsoft 365 til at bruge Azure RMS, skal du se [Konfigurer IRM til at bruge Azure Rights Management og Konfigurer IRM (Information Rights Management) i SharePoint Administration](../enterprise/activate-rms-in-microsoft-365.md). Hvis du betjener Active Directory i det lokale miljø (AD) RMS-server, kan du også [konfigurere IRM til at bruge en AD RMS-server](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server) i det lokale miljø, men vi anbefaler på det kraftigste, at du [migrerer til Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) for at bruge nye funktioner, f.eks. sikkert samarbejde med andre organisationer.

Når du beskytter kundedata med Azure RMS, bruger Azure RMS en 2048-bit RSA-asymmetrisk nøgle med SHA-256-hashalgoritmen til integritet til at kryptere dataene. Den symmetriske nøgle til Office dokumenter og mail er AES 128-bit. For hvert dokument eller hver mail, der er beskyttet af Azure RMS, opretter Azure RMS en enkelt AES-nøgle ("indholdsnøglen"), og denne nøgle er integreret i dokumentet og fortsætter gennem udgaver af dokumentet. Indholdsnøglen er beskyttet med organisationens RSA-nøgle ("Azure Information Protection lejernøglen") som en del af politikken i dokumentet, og politikken er også signeret af dokumentets forfatter. Denne lejernøgle er fælles for alle dokumenter og mails, der er beskyttet af Azure RMS for organisationen, og denne nøgle kan kun ændres af en Azure Information Protection-administrator, hvis organisationen bruger en lejernøgle, der er kundeadministrerede. Du kan få flere oplysninger om de kryptografiske kontrolelementer, der bruges af Azure RMS, under [Hvordan fungerer Azure RMS? Under kølerhjelmen](/information-protection/understand-explore/how-does-it-work).

I en Azure RMS-standardimplementering genererer og administrerer Microsoft den rodnøgle, der er entydig for hver lejer. Kunder kan administrere livscyklussen for deres rodnøgle i Azure RMS med Azure Key Vault Services ved hjælp af en nøgleadministrationsmetode kaldet [BYOK (Bring Your Own Key),](/azure/information-protection/plan-implement-tenant-key) der giver dig mulighed for at generere din nøgle i lokale HSM'er (hardwaresikkerhedsmoduler) og bevare kontrollen over denne nøgle efter overførsel til Microsofts FIPS 140-2 Niveau 2-validerede HSM'er. Der gives ikke adgang til rodnøglen til nogen medarbejdere, da nøglerne ikke kan eksporteres eller udtrækkes fra HSM'erne for at beskytte dem. Derudover kan du til enhver tid få adgang til en log i nærheden af realtid, der viser al adgang til rodnøglen. Du kan finde flere oplysninger under [Logføring og analyse af Brug af Azure Rights Management](/azure/information-protection/log-analyze-usage).

Azure Rights Management hjælper med at afhjælpe trusler som f.eks. trådtapning, man-in-the-middle-angreb, datatyveri og utilsigtede overtrædelser af organisationens delingspolitikker. Samtidig forhindres enhver uretmæssig adgang til kundedata under overførsel eller inaktive data af en uautoriseret bruger, der ikke har de nødvendige tilladelser, via politikker, der følger efter disse data, hvilket afhjælper risikoen for, at disse data falder i de forkerte hænder enten bevidst eller ubevidst og giver forebyggelsesfunktioner til datatab. Hvis Azure RMS bruges som en del af Azure Information Protection, indeholder det også funktioner til dataklassificering og mærkning, indholdsmarkering, sporing af dokumentadgang og funktioner til tilbagekaldelse af adgang. Hvis du vil vide mere om disse funktioner, [skal du se Hvad er Azure Information Protection](/information-protection/understand-explore/what-is-information-protection), [Azure Information Protection udrulningsoversigt](/information-protection/plan-design/deployment-roadmap) og [Selvstudium til hurtig start til Azure Information Protection](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Sikker internetmailudvidelse til flere formål

Secure/Multipurpose Internet Mail Extensions (S/MIME) er en standard for kryptering af offentlige nøgler og digital signering af MIME-data. S/MIME er defineret i RIC 3369, 3370, 3850, 3851 og andre. Det gør det muligt for en bruger at kryptere en mail og signere en mail digitalt. En mail, der er krypteret ved hjælp af S/MIME, kan kun dekrypteres af modtageren af mailen ved hjælp af deres private nøgle, som kun er tilgængelig for den pågældende modtager. Derfor kan mails ikke dekrypteres af andre end modtageren af mailen.

[Microsoft understøtter S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Offentlige certifikater distribueres til kundens Active Directory i det lokale miljø og gemmes i attributter, der kan replikeres til en Microsoft 365 lejer. De private nøgler, der svarer til de offentlige nøgler, forbliver i det lokale miljø og sendes aldrig til Office 365. Brugerne kan oprette, kryptere, dekryptere, læse og signere mails digitalt mellem to brugere i en organisation ved hjælp af Outlook, Outlook på internettet og Exchange ActiveSync klienter. Du kan få flere oplysninger under [S/MIME-kryptering nu i Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>Office 365 meddelelsekryptering

[Office 365 OME (Message Encryption](https://products.office.com/exchange/office-365-message-encryption)), der er bygget oven på [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) (AIP), gør det muligt for dig at sende krypterede og rettighedsbeskyttede mails til alle. OME afhjælper trusler som f.eks. trådtapning og man-in-the-middle-angreb og andre trusler, f.eks. uberettigede adgang til data fra en uautoriseret bruger, der ikke har de nødvendige tilladelser. Vi har foretaget investeringer, der giver dig en enklere, mere intuitiv og sikker mailoplevelse, der er bygget oven på Azure Information Protection. Du kan beskytte meddelelser, der sendes fra Microsoft 365 til alle i eller uden for organisationen. Disse meddelelser kan ses på tværs af en lang række mailklienter ved hjælp af en hvilken som helst identitet, herunder Azure Active Directory, Microsoft-konto og Google-id'er. Du kan få flere oplysninger om, hvordan din organisation kan bruge krypterede meddelelser, [under Office 365 Meddelelsekryptering](./ome.md).

## <a name="transport-layer-security"></a>Sikkerhed på transportlag

Hvis du vil sikre sikker kommunikation med en partner, kan du bruge indgående og udgående connectors til at levere sikkerhed og meddelelsesintegritet. Du kan konfigurere tvungen indgående og udgående TLS på hver connector ved hjælp af et certifikat. Brug af en krypteret SMTP-kanal kan forhindre, at data bliver stjålet via et man-in-the-middle-angreb. Du kan få flere oplysninger under [Sådan bruger Exchange Online TLS til at sikre mailforbindelser](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>Identificerede mail med domænenavne

Exchange Online Protection (EOP) og Exchange Online understøtter indgående validering af DKIM-meddelelser (Domain Keys Identified Mail). DKIM er en metode til at validere, at en besked blev sendt fra domænet, den siger, at den stammer fra, og at den ikke blev spoofed af en anden. Det knytter en mail til den organisation, der er ansvarlig for at sende den, og er en del af et større paradigme af mailkryptering. Du kan få flere oplysninger om de tre dele af dette paradigme i:

- [Konfigurer SPF for at forhindre forfalskning](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [Brug DMARC til at validere mail](/office365/SecurityCompliance/use-dmarc-to-validate-email)
