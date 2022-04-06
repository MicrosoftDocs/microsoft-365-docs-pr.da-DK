---
title: Sådan beskytter du mod phishing-angreb
ms.reviewer: ''
description: Få mere at vide om, hvordan phishing fungerer, leverer malware på dine enheder, og hvad du kan gøre for at beskytte dig selv
keywords: sikkerhed, malware, phishing, oplysninger, fidus, social engineering, agn, lokke, beskyttelse, tendenser, målrettet angreb
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 1f414c80d3c0b5478112cd402f8e3839908787d4
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666762"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Sådan beskytter du mod phishing-angreb

Phishingangreb forsøger at stjæle følsomme oplysninger via mails, websteder, sms'er eller andre former for elektronisk kommunikation. De forsøger at ligne officiel kommunikation fra legitime virksomheder eller enkeltpersoner.

Cyberkriminelle forsøger ofte at stjæle brugernavne, adgangskoder, kreditkortoplysninger, bankkontooplysninger eller andre legitimationsoplysninger. De bruger stjålne oplysninger til skadelige formål, såsom hacking, identitetstyveri eller stjæler penge direkte fra bankkonti og kreditkort. Oplysningerne kan også sælges på cyberkriminelle underjordiske markeder.

Social engineering angreb er designet til at drage fordel af en brugers mulige bortfald i beslutningsprocessen. Vær opmærksom på og giv aldrig følsomme eller personlige oplysninger via e-mail eller ukendte websteder eller over telefonen. Husk, at phishing-mails er designet til at virke legitime.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Få mere at vide om tegn på phishing

Den bedste beskyttelse er opmærksomhed og uddannelse. Åbn ikke vedhæftede filer eller links i uopfordrede mails, selvom e-mails kom fra en kendt kilde. Hvis mailen er uventet, skal du være forsigtig med at åbne den vedhæftede fil og bekræfte URL-adressen.

Virksomheder bør uddanne og uddanne deres medarbejdere til at være på vagt over for enhver kommunikation, der anmoder om personlige eller finansielle oplysninger. De bør også instruere medarbejderne i straks at rapportere truslen mod virksomhedens sikkerhedsdriftsteam.

Her er flere afslørende tegn på et phishing-svindelnummer:

* De links eller URL-adresser, der leveres i e-mails **, peger ikke på den korrekte placering** eller peger på et tredjepartswebsted, der ikke er tilknyttet afsenderen af e-mailen. På billedet nedenfor svarer den angivne URL-adresse f.eks. ikke til den URL-adresse, du bliver ført til.

    ![eksempel på, hvordan du holder markøren over en URL-adresse.](../../media/security-intelligence-images/url-hover.png)

* Der er en **anmodning om personlige oplysninger** , f.eks. CPR-numre eller bank- eller finansielle oplysninger. Officiel kommunikation vil generelt ikke anmode om personlige oplysninger fra dig i form af en e-mail.

* **Elementer i mailadressen ændres** , så de svarer til en legitim mailadresse, men har tilføjet tal eller ændrede bogstaver.

* Meddelelsen er **uventet og uopfordret**. Hvis du pludselig modtager en mail fra en enhed eller en person, du sjældent beskæftiger dig med, skal du overveje denne mailmistænkte.

* Meddelelsen eller den vedhæftede fil beder dig om at **aktivere makroer, justere sikkerhedsindstillingerne eller installere programmer**. Normale mails beder dig ikke om at gøre dette.

* Meddelelsen indeholder **fejl**. Legitime virksomhedsmeddelelser har mindre sandsynlighed for at have typografiske eller grammatiske fejl eller indeholde forkerte oplysninger.

* **Afsenderadressen stemmer ikke overens med signaturen** i selve meddelelsen. En mail foregives f.eks. at være fra Mary fra Contoso Corp, men afsenderadressen er john<span></span>@example.com.

* Der er **flere modtagere** i feltet "Til", og de ser ud til at være tilfældige adresser. Firmameddelelser sendes normalt direkte til individuelle modtagere.

* Hilsenen på selve meddelelsen **henvender dig ikke personligt**. Bortset fra meddelelser, der fejlagtigt adresse en anden person, hilsener, der misbruger dit navn eller trække dit navn direkte fra din e-mail-adresse tendens til at være ondsindet.

* Webstedet ser velkendt ud, men der er **uoverensstemmelser eller ting, der ikke er helt rigtige**. Advarselsskilte omfatter forældede logoer, stavefejl eller beder brugerne om at give yderligere oplysninger, der ikke bliver spurgt af legitime logonwebsteder.

* Den side, der åbnes, er **ikke en dynamisk side**, men snarere et billede, der er designet til at ligne det websted, du kender. Der vises muligvis et pop op-vindue, der anmoder om legitimationsoplysninger.

Hvis du er i tvivl, skal du kontakte virksomheden af kendte kanaler for at kontrollere, om nogen mistænkelige e-mails faktisk er legitime.

## <a name="software-solutions-for-organizations"></a>Softwareløsninger til organisationer

* [Microsoft Edge](/microsoft-edge/deploy/index) og [Windows Defender Application Guard](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md) tilbyder beskyttelse mod den stigende trussel om målrettede angreb ved hjælp af Microsofts brancheførende Hyper-V-virtualiseringsteknologi. Hvis et gennemset websted anses for upålideligt, isolerer Hyper-V-objektbeholderen enheden fra resten af netværket, hvilket forhindrer adgang til dine virksomhedsdata.

* [EOP (Microsoft Exchange Online Protection)](https://products.office.com/exchange/exchange-email-security-spam-protection) tilbyder pålidelighed og beskyttelse i virksomhedsklassen mod spam og malware, samtidig med at du bevarer adgang til mail under og efter nødsituationer.  Ved hjælp af forskellige lag af filtrering kan EOP levere forskellige kontrolelementer til spamfiltrering, f.eks. massepostkontrol og international spam, der yderligere vil forbedre dine beskyttelsestjenester.

* Brug [Microsoft Defender for Office 365](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc) til at beskytte dine mails, filer og onlinelager mod malware. Den tilbyder holistisk beskyttelse i Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online og OneDrive for Business. Ved at beskytte mod usikre vedhæftede filer og udvide beskyttelsen mod skadelige links supplerer den sikkerhedsfunktionerne i Exchange Online Protection for at give bedre nuldagsbeskyttelse.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Hvad skal du gøre, hvis du har været offer for et phishing-svindelnummer?

Hvis du føler, at du har været offer for et phishing-angreb:

1. Kontakt it-administratoren, hvis du arbejder på en arbejdscomputer
2. Skift straks alle adgangskoder, der er knyttet til kontiene
3. Rapportér enhver svigagtig aktivitet til din bank- og kreditkortvirksomhed

### <a name="reporting-spam"></a>Rapportering af spam

- **Outlook.com**: Hvis du modtager en mistænkelig mail, der beder om personlige oplysninger, skal du markere afkrydsningsfeltet ud for meddelelsen i din Outlook indbakke. Vælg pilen ud for **Uønsket**, og vælg derefter **Phishing**.

- **Microsoft Office Outlook**: I den mistænkelige meddelelse skal du vælge **Rapportér meddelelse** på båndet og derefter vælge **Phishing**.

- **Microsoft 365**: Brug [indsendelsesportalen i Microsoft 365 Defender](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft) til at sende eksemplet på uønsket eller phishing til Microsoft til analyse. Du kan få flere oplysninger under [Rapportér meddelelser og filer til Microsoft](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Arbejdsgruppe til bekæmpelse af phishing**: phishing-report@us-cert.gov. Gruppen bruger rapporter, der er genereret fra e-mails, til at bekæmpe phishing-svindel og hackere. Internetudbydere, sikkerhedsleverandører, finansielle institutioner og retshåndhævelsesinstanser er involveret.

### <a name="if-youre-on-a-suspicious-website"></a>Hvis du er på et mistænkeligt websted

- **Microsoft Edge**: Mens du er på et mistænkeligt websted, skal du vælge **ikonet** >  Mere (...)**Hjælp og feedbackRapportér** >  **usikkert websted**. Følg vejledningen på den viste webside for at rapportere webstedet.

- **Internet Explorer**: Mens du er på et mistænkeligt websted, skal du vælge tandhjulsikonet, pege på **Sikkerhed** og derefter vælge **Rapportér usikkert websted**. Følg vejledningen på den viste webside for at rapportere webstedet.

## <a name="more-information-about-phishing-attacks"></a>Flere oplysninger om phishing-angreb

- [Beskyt dig selv mod phishing](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Phishing-tendenser](phishing-trends.md)
