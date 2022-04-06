---
title: Sådan beskyttes mod phishingangreb
ms.reviewer: ''
description: Få mere at vide om, hvordan phishing fungerer, leverer malware på dine enheder, og hvad du kan gøre for at beskytte dig selv
keywords: sikkerhed, malware, phishing, oplysninger, svindel, social engineering, bait, tilsnende, beskyttelse, tendenser, målrettede angreb
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
ms.openlocfilehash: 39b998b69b62a8c927ff26c1325d8a88812e0be6
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63706035"
---
# <a name="how-to-protect-against-phishing-attacks"></a>Sådan beskyttes mod phishingangreb

Phishingangreb forsøger at stjæle følsomme oplysninger via mails, websteder, sms'er eller andre former for elektronisk kommunikation. De forsøger at ligne officiel kommunikation fra legitime virksomheder eller enkeltpersoner.

Cyberkriminelle forsøger ofte at stjæle brugernavne, adgangskoder, kreditkortoplysninger, bankkontooplysninger eller andre legitimationsoplysninger. De bruger stjålne oplysninger til ondsindede formål, f.eks. hacking, identitetstyveri eller stjæler penge direkte fra bankkonti og kreditkort. Oplysningerne kan også sælges på cyberkriminelle markeder.

Sociale engineering-angreb er designet til at drage fordel af en brugers mulige udløb i beslutningstagningen. Vær opmærksom på, og giv aldrig følsomme eller personlige oplysninger via mail eller ukendte websteder eller via telefonen. Husk, at phishingmails er designet til at virke legitime.

## <a name="learn-the-signs-of-a-phishing-scam"></a>Få mere at vide om tegn på forsøg på phishing

Den bedste beskyttelse er opmærksomhed og uddannelse. Du må ikke åbne vedhæftede filer eller links i uopfordrede mails, heller ikke selvom mails stammer fra en genkendt kilde. Hvis mailen er uventet, skal du være forsigtig med at åbne den vedhæftede fil og bekræfte URL-adressen.

Virksomheder bør uddanne og oplære deres medarbejdere i at være på vagt over for enhver kommunikation, der anmoder om personlige eller økonomiske oplysninger. De skal også instruere medarbejderne i straks at rapportere truslen mod virksomhedens sikkerhedsteam.

Her er flere tegn på forsøg på phishing:

* De links eller URL-adresser, der er  angivet i mails, peger ikke på den korrekte placering eller peger på et websted fra en tredjepart, der ikke er knyttet til afsenderen af mailen. Eksempelvis stemmer billedet under den angivne URL-adresse ikke overens med den URL-adresse, du bliver ført til.

    ![eksempel på at pege på en URL-adresse.](../../media/security-intelligence-images/url-hover.png)

* Der er en anmodning **om personlige oplysninger som** f.eks. cpr-numre eller bankoplysninger eller økonomiske oplysninger. Officiel kommunikation vil generelt ikke anmode om personlige oplysninger fra dig i form af en mail.

* **Elementer i mailadressen ændres,** så det ligner nok en legitim mailadresse, men har tilføjet tal eller ændrede bogstaver.

* Meddelelsen er **uventet og uopfordret**. Hvis du pludselig modtager en mail fra en enhed eller en person, du sjældent håndterer, kan du have mistanke om denne mail.

* Meddelelsen eller den vedhæftede fil beder dig **om at aktivere makroer, justere sikkerhedsindstillinger eller installere programmer**. Normale mails beder dig ikke om at gøre dette.

* Meddelelsen **indeholder fejl**. Legitime virksomhedsmeddelelser har mindre sandsynlighed for at have typografiske eller grammatiske fejl eller indeholder forkerte oplysninger.

* **Afsenderadressen stemmer ikke overens med signaturen** i selve meddelelsen. Det kan f.eks. være, at en mail er fra Mary of Contoso Corp, men afsenderens adresse er john<span></span>@example.com.

* Der er **flere modtagere i** feltet "Til", og det ser ud til, at de er tilfældige adresser. Virksomhedsmeddelelser sendes normalt direkte til individuelle modtagere.

* Hilsenen på selve meddelelsen **adresserer dig ikke personligt**. Bortset fra meddelelser, der ved en fejltagelse adresserer en anden person, er der ofte en ondsindet hilsen, der misbruger dit navn eller trækker dit navn direkte fra din mailadresse.

* Webstedet ser bekendt ud, men **der er uoverensstemmelser eller ting, der ikke er helt rigtige**. Advarselstegn omfatter forældede logoer, slåfejl eller beder brugerne om at give yderligere oplysninger, som ikke stilles til deres legitime logonwebsteder.

* Den side, der åbnes, **er ikke en liveside**, men et billede, der er designet til at ligne det websted, du kender. Der vises muligvis et pop op-vindue, hvor der anmodes om legitimationsoplysninger.

Hvis du er i tvivl, kan du kontakte virksomheden via kendte kanaler for at bekræfte, om mistænkelige mails faktisk er legitime.

## <a name="software-solutions-for-organizations"></a>Softwareløsninger til organisationer

* [Microsoft Edge](/microsoft-edge/deploy/index) og [Windows Defender Application Guard beskytter](/windows/security/microsoft-defender-application-guard/md-app-guard-overview.md) mod den stigende trussel mod målrettede angreb ved hjælp af Microsofts brancheførende Hyper V-virtualiseringsteknologi. Hvis et gennemset websted betragtes som upålideligt, isolerer Hyper-V-beholderen den pågældende enhed fra resten af dit netværk og forhindrer dermed adgang til dine virksomhedsdata.

* [Microsoft Exchange Online Protection (EOP) tilbyder](https://products.office.com/exchange/exchange-email-security-spam-protection) pålidelighed i virksomhedsklassen og beskyttelse mod spam og malware, mens du bevarer adgangen til mail i nødstilfælde og efter.  Ved hjælp af forskellige lag af filtrering kan EOP give forskellige kontrolelementer til spamfiltrering, f.eks. kontrolelementer for massemails og international spam, som yderligere forbedrer dine beskyttelsestjenester.

* Brug [Microsoft Defender til Office 365](https://products.office.com/exchange/online-email-threat-protection?ocid=cx-blog-mmpc) at beskytte din mail, dine filer og din onlinelagerplads mod malware. Det tilbyder beskyttelse mod Microsoft Teams, Word, Excel, PowerPoint, Visio, SharePoint Online og OneDrive for Business. Ved at beskytte mod usikre vedhæftede filer og udvide beskyttelsen mod ondsindede links komplementerer den sikkerhedsfunktionerne i Exchange Online Protection for at give bedre beskyttelse på nul dage.

## <a name="what-to-do-if-youve-been-a-victim-of-a-phishing-scam"></a>Hvad du skal gøre, hvis du er blevet offer for et forsøg på phishing

Hvis du føler, at du er blevet offer for et phishingangreb:

1. Kontakt din it-administrator, hvis du er på en arbejdscomputer
2. Rediger straks alle adgangskoder, der er knyttet til kontiene
3. Rapportere svigagtig aktivitet til din bank og dit kreditkortfirma

### <a name="reporting-spam"></a>Rapportering af spam

- **Outlook.com**: Hvis du modtager en mistænkelig mail, hvor du bliver bedt om personlige oplysninger, skal du markere afkrydsningsfeltet ud for meddelelsen i din Outlook indbakke. Vælg pilen ud for **Uønsket** mail, og vælg derefter **Phishing**.

- **Microsoft Office Outlook**: Mens du er i den mistænkelige meddelelse, **skal du vælge** Rapportér meddelelse på båndet og derefter vælge **Phishing**.

- **Microsoft 365**: Brug portalen [til indsendelser Microsoft 365 Defender](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft) at sende eksemplet med uønsket mail eller phishing til Microsoft til analyse. Få mere at vide under [Rapportér meddelelser og filer til Microsoft](/microsoft-365/security/office-365-security/report-junk-email-messages-to-microsoft).

- **Antiphishing-arbejdsgruppe**: phishing-report@us-cert.gov. Gruppen bruger rapporter, der er genereret fra mails, der sendes til at bekæmpe forsøg på phishing og hackere. Internetudbydere, sikkerhedsleverandører, finansielle institutioner og håndhævende myndigheder er involveret.

### <a name="if-youre-on-a-suspicious-website"></a>Hvis du er på et mistænkeligt websted

- **Microsoft Edge**: Mens du er på et mistænkeligt websted, skal du vælge ikonet **Mere (...)** >  **Hjælp og feedbackRapport** >  **over usikkert websted**. Følg vejledningen på den webside, der vises for at rapportere webstedet.

- **Internet Explorer**: Mens du er på et mistænkeligt websted, skal du vælge tandhjulsikonet, pege på **Sikkerhed** og derefter vælge **Rapportér usikkert websted**. Følg vejledningen på den webside, der vises for at rapportere webstedet.

## <a name="more-information-about-phishing-attacks"></a>Flere oplysninger om phishing-angreb

- [Beskyt dig selv mod phishing](https://support.microsoft.com/help/4033787/windows-protect-yourself-from-phishing)
- [Phishingtendenser](phishing-trends.md)
