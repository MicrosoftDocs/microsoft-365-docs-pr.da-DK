---
title: Kunde-administrerede krypteringsfunktioner
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
ms.openlocfilehash: 80a0726e112324a673fc964a9fabdbc3ba0ac42e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587928"
---
# <a name="customer-managed-encryption-features"></a>Kunde-administrerede krypteringsfunktioner

Sammen med krypteringsteknologierne i Microsoft 365 administreres af Microsoft, fungerer Microsoft 365 også med yderligere krypteringsteknologier, som du kan administrere og konfigurere, f.eks.:

- [Azure Rights Management](/azure/information-protection/what-is-azure-rms)

- [Secure Multipurpose Internet Mail-udvidelse](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx)

- [Office 365-meddelelseskryptering](https://products.office.com/en-us/exchange/office-365-message-encryption)

- [Sikre mailflow med en partnerorganisation](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner)

Du kan finde flere oplysninger om disse teknologier [Microsoft 365 beskrivelserne af tjenesten](/office365/servicedescriptions/office-365-service-descriptions-technet-library).

## <a name="azure-rights-management"></a>Azure Rights Management

[Azure Rights Management](/azure/information-protection/what-is-azure-rms) (Azure RMS) er den teknologi til beskyttelse, der bruges [af Azure Information Protection](/information-protection/understand-explore/what-is-information-protection). Den bruger kryptering, identitet og godkendelsespolitikker til at sikre dine filer og mails på tværs af flere platforme og enheder – telefoner, tablets og pc'er. Oplysninger kan beskyttes både i og uden for organisationen, fordi beskyttelse forbliver med dataene. Azure RMS giver vedvarende beskyttelse af alle filtyper, beskytter filer hvor som helst, understøtter virksomhed-til-virksomhed-samarbejde og en lang række Windows- og ikke-Windows-enheder. Azure RMS-beskyttelse kan også udvide [politikker til forebyggelse af datatab (DLP](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)). Du kan finde flere oplysninger om, hvilke programmer og tjenester der kan bruge tjenesten Azure Rights Management fra Azure Information Protection under Sådan [understøtter programmer Azure Rights Management-tjenesten](/information-protection/understand-explore/applications-support).

Azure RMS er integreret med Microsoft 365 og er tilgængelig for alle kunder. Hvis du Microsoft 365 bruge Azure RMS, skal du se Konfigurer IRM til at bruge [Azure Rights Management og Konfigurere IRM (Information Rights Management) SharePoint Administration](../enterprise/activate-rms-in-microsoft-365.md). Hvis du bruger en lokal Active Directory (AD) RMS-server, kan du også konfigurere IRM til at bruge en lokal [AD RMS-server](/office365/SecurityCompliance/configure-irm-to-use-an-on-premises-ad-rms-server), men vi anbefaler på det kraftigste, at du overfører til [Azure RMS](/azure/information-protection/migrate-from-ad-rms-to-azure-rms) for at bruge nye funktioner som f.eks. sikkert samarbejde med andre organisationer.

Når du beskytter kundedata med Azure RMS, bruger Azure RMS en 2048-bit RSA-asymmetrisk nøgle med SHA-256-hashalgoritme for integritet til at kryptere dataene. Den symmetriske nøgle til Office dokumenter og mail er AES 128-bit. For hvert dokument eller hver mail, der er beskyttet af Azure RMS, opretter Azure RMS en enkelt AES-nøgle ("indholdsnøglen"), og denne nøgle integreres i dokumentet og bevares via udgaver af dokumentet. Indholdsnøglen er beskyttet med organisationens RSA-nøgle ("Azure Information Protection-lejernøgle") som en del af politikken i dokumentet, og politikken er også signeret af dokumentets forfatter. Denne lejernøgle er fælles for alle dokumenter og mails, der er beskyttet af Azure RMS for organisationen, og denne nøgle kan kun ændres af en Azure Information Protection-administrator, hvis organisationen bruger en lejernøgle, der er kundestyret. Du kan finde flere oplysninger om de krypterede kontrolelementer, der bruges af Azure RMS, [under Hvordan fungerer Azure RMS? Under toppen](/information-protection/understand-explore/how-does-it-work).

I en standard Azure RMS-implementering genererer og administrerer Microsoft den rodnøgle, der er entydig for hver lejer. Kunder kan administrere deres rodnøgles livscyklus i Azure RMS med Azure Key Vault Services ved hjælp af en nøgleadministrationsmetode kaldet [Bring Your Own Key (BYOK),](/azure/information-protection/plan-implement-tenant-key) der gør det muligt at generere din nøgle i lokale HSMs (hardwaresikkerhedsmoduler) og bevare kontrollen over denne nøgle efter overførslen til Microsofts FIPS 140-2 Niveau 2-validerede HSMs. Adgang til rodnøglen gives ikke til medarbejdere, da nøglerne ikke kan eksporteres eller udtrækkes fra HSMs, der beskytter dem. Desuden kan du til enhver tid få adgang til en næsten realtidslog, der viser al adgang til rodnøglen. Få mere at vide under [Logføring og analyse af brugen af Azure Rights Management](/azure/information-protection/log-analyze-usage).

Azure Rights Management hjælper med at reducere trusler som f.eks. wire-tapping, man-in-the-middle-angreb, datatyveri og utilsigtede overtrædelser af politikker for organisationsdeling. På samme tid forhindres uautoriseret adgang til kundedata under overførsel eller i hvile af uautoriserede brugere, der ikke har de rette tilladelser, via politikker, der følger disse data, hvilket mindsker risikoen for, at data falder i de forkerte hænder, enten bevidst eller ukendt og levere funktioner til forebyggelse af datatab. Hvis Azure RMS bruges som en del af Azure Information Protection, leverer den også egenskaberne Dataklassifikation og -mærkning, indholdsmærkning, sporing af dokumentadgang og tilbagekaldelse af adgang. Du kan få mere at vide om disse funktioner under Hvad [er Azure Information Protection](/information-protection/understand-explore/what-is-information-protection), [Roadmap til installation af Azure Information Protection](/information-protection/plan-design/deployment-roadmap) og [Quick Start-selvstudium til Azure Information Protection](/information-protection/get-started/infoprotect-quick-start-tutorial).

## <a name="secure-multipurpose-internet-mail-extension"></a>Secure Multipurpose Internet Mail-udvidelse

Secure/Multipurpose Internet Mail Extensions (S/MIME) er en standard for offentlig nøglekryptering og digital signering af MIME-data. S/MIME er defineret i RFCs 3369, 3370, 3850, 3851 og andre. Det gør det muligt for en bruger at kryptere en mail og signere en mail digitalt. En mail, der er krypteret ved hjælp af S/MIME, kan kun dekrypteres af modtageren af mailen ved hjælp af sin private nøgle, som kun er tilgængelig for den pågældende modtager. Derfor kan mails ikke dekrypteres af andre end modtageren af mailen.

[Microsoft understøtter S/MIME](https://blogs.technet.com/b/exchange/archive/2014/12/15/how-to-configure-s-mime-in-office-365.aspx). Offentlige certifikater distribueres til kundens lokale Active Directory og gemmes i attributter, der kan replikeres til en Microsoft 365 lejer. De private nøgler, der svarer til de offentlige nøgler, forbliver lokale og overføres aldrig Office 365. Brugere kan skrive, kryptere, dekryptere, læse og digitalt signere mails mellem to brugere i en organisation ved hjælp Outlook, Outlook på internettet og Exchange ActiveSync klienter. Få mere at vide under [S/MIME-kryptering nu i Office 365](https://blogs.office.com/2014/02/26/smime-encryption-now-in-office-365/).

## <a name="office-365-message-encryption"></a>Office 365-meddelelseskryptering

[Office 365-meddelelseskryptering](https://products.office.com/exchange/office-365-message-encryption) (OME), der er bygget oven på [Azure Information Protection](/information-protection/understand-explore/what-is-information-protection) (AIP), giver dig mulighed for at sende krypterede og rettighedsbeskyttede mails til alle. OME afhjælper trusler som f.eks. wire-tapping og man-in-the-middle-angreb og andre trusler, f.eks. uautoriseret adgang af data fra uautoriserede brugere, der ikke har de nødvendige tilladelser. Vi har foretaget investeringer, der giver dig en enklere, mere intuitiv, sikker mailoplevelse, der bygger på Azure Information Protection. Du kan beskytte meddelelser, der Microsoft 365 mails til personer i eller uden for organisationen. Disse meddelelser kan vises på tværs af en lang række mailklienter ved hjælp af en hvilken som helst identitet, Azure Active Directory, Microsoft-konto og Google-id'er. Du kan finde flere oplysninger om, hvordan din organisation kan bruge krypterede meddelelser, [under Office 365-meddelelseskryptering](./ome.md).

## <a name="transport-layer-security"></a>Transport Layer Security

Hvis du vil sikre sikker kommunikation med en partner, kan du bruge indgående og udgående forbindelser til at sikre sikkerhed og meddelelsesintegritet. Du kan konfigurere gennemtvungne indgående og udgående TLS på hver forbindelse ved hjælp af et certifikat. Brug af en krypteret SMTP-kanal kan forhindre data i at blive stjålet via et man-in-the-middle-angreb. Du kan få mere at [vide under Exchange Online bruger TLS til at sikre mailforbindelser](./exchange-online-uses-tls-to-secure-email-connections.md).

## <a name="domain-keys-identified-mail"></a>Domænenøgler, identificeret mail

Exchange Online Protection (EOP) og Exchange Online understøtter indgående validering af domænenøgler identificerede mails (DKIM). DKIM er en metode til at validere, at en meddelelse blev sendt fra domænet, hvor der står, at den stammer fra, og at den ikke blev efterlignet af en anden. Den binder en mail til den organisation, der er ansvarlig for at sende den, og er en del af en større kryptering af mail. Du kan finde flere oplysninger om de tre dele af dette fabriks, under:

- [Konfigurer SPF for at forhindre spoofing](/office365/SecurityCompliance/set-up-spf-in-office-365-to-help-prevent-spoofing)

- [Brug DKIM til at validere udgående mails, der sendes fra dit brugerdefinerede domæne](/office365/SecurityCompliance/use-dkim-to-validate-outbound-email)

- [Brug DMARC til at validere mail](/office365/SecurityCompliance/use-dmarc-to-validate-email)