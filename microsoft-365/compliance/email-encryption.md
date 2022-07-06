---
title: Mailkryptering i Microsoft 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 8/28/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.assetid: c0d87cbe-6d65-4c03-88ad-5216ea5564e8
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
description: Sammenlign Microsoft 365-krypteringsindstillinger, herunder Microsoft Purview-meddelelseskryptering, S/MIME, IRM (Information Rights Management), og få mere at vide om TLS (Transport Layer Security).
ms.openlocfilehash: a5541c9a1478d1eb1add40a5aecb7439d1442e1b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624239"
---
# <a name="email-encryption"></a>Mailkryptering

I denne artikel sammenlignes krypteringsindstillinger i Microsoft 365, herunder Microsoft Purview-meddelelseskryptering, S/MIME, IRM (Information Rights Management) og introducerer TLS (Transport Layer Security).
  
Microsoft 365 leverer flere krypteringsmuligheder, der kan hjælpe dig med at opfylde din virksomheds behov for mailsikkerhed. I denne artikel beskrives tre måder at kryptere mails på i Office 365. Hvis du vil vide mere om alle sikkerhedsfunktioner i Office 365, kan du besøge [Office 365 Center for sikkerhed og rettighedsadministration](https://go.microsoft.com/fwlink/p/?LinkID=282470). I denne artikel introduceres de tre krypteringstyper, der er tilgængelige for Microsoft 365-administratorer, for at hjælpe med at sikre mail i Office 365:
  
- Microsoft Purview-meddelelseskryptering.

- S/MIME (Secure/Multipurpose Internet Mail Extensions).

- IRM (Information Rights Management).

## <a name="how-microsoft-365-uses-email-encryption"></a>Sådan bruger Microsoft 365 mailkryptering

Kryptering er den proces, som oplysninger kodes af, så det kun er en godkendt modtager, der kan afkode og bruge oplysningerne. Microsoft 365 bruger kryptering på to måder: i tjenesten og som kundekontrol. I tjenesten bruges kryptering som standard i Microsoft 365. du ikke behøver at konfigurere noget. Microsoft 365 bruger f.eks. TLS (Transport Layer Security) til at kryptere forbindelsen eller sessionen mellem to servere. 
  
Sådan fungerer mailkryptering typisk:
  
- En meddelelse krypteres eller transformeres fra almindelig tekst til ulæselig kryptering, enten på afsenderens computer eller af en central server, mens meddelelsen er under overførsel.

- Meddelelsen forbliver i krypteringstekst, mens den er under overførsel for at beskytte den mod at blive læst, hvis meddelelsen opfanges.

- Når meddelelsen modtages af modtageren, transformeres meddelelsen tilbage til læsevenlig almindelig tekst på to måder:

  - Modtagerens computer bruger en nøgle til at dekryptere meddelelsen, eller

  - En central server dekrypterer meddelelsen på vegne af modtageren, når den har valideret modtagerens identitet.

Du kan få flere oplysninger om, hvordan Microsoft 365 sikrer kommunikation mellem servere, f.eks. mellem organisationer i Microsoft 365 eller mellem Microsoft 365 og en pålidelig forretningspartner uden for Microsoft 365, under [Sådan bruger Exchange Online TLS til at sikre mailforbindelser i Office 365](exchange-online-uses-tls-to-secure-email-connections.md).
    
## <a name="comparing-email-encryption-options-available-in-office-365"></a>Sammenligning af de krypteringsindstillinger for mails, der er tilgængelige i Office 365

|Teknologi til kryptering af mail|![Konceptuelt illustration, der beskriver OME.](../media/2bf27b5e-bbb3-46d1-95bf-884dc27a746c.png)|![Konceptuelt illustration, der beskriver IRM](../media/9c0cc444-9448-40c6-b244-8fcc593a64e0.png)|![Konceptuelt illustration, der beskriver SMIME](../media/ae4613a8-c17e-47e1-8e13-12e891e43744.png)|
|:-----|:-----|:-----|:-----|
|Hvad er det?|Meddelelseskryptering er en tjeneste, der er baseret på Azure RMS (Azure Rights Management), som gør det muligt for dig at sende krypterede mails til personer i eller uden for din organisation, uanset destinationsmailadressen (Gmail, Yahoo! Mail, Outlook.com osv.). <br/> Som administrator kan du konfigurere transportregler, der definerer betingelserne for kryptering. Når en bruger sender en meddelelse, der svarer til en regel, anvendes kryptering automatisk. <br/> For at få vist krypterede meddelelser kan modtagerne enten få en engangsadgangskode, logge på med en Microsoft-konto eller logge på med en arbejds- eller skolekonto, der er knyttet til Office 365. Modtagere kan også sende krypterede svar. De behøver ikke et Microsoft 365-abonnement for at få vist krypterede meddelelser eller sende krypterede svar.|IRM er en krypteringsløsning, der også anvender anvendelsesbegrænsninger på mailmeddelelser. Det hjælper med at forhindre, at følsomme oplysninger udskrives, videresendes eller kopieres af uautoriserede personer. <br/> IRM-funktioner i Microsoft 365 bruger Azure Rights Management (Azure RMS).|S/MIME er en certifikatbaseret krypteringsløsning, der giver dig mulighed for både at kryptere og signere en meddelelse digitalt. Meddelelseskrypteringen hjælper med at sikre, at det kun er den ønskede modtager, der kan åbne og læse meddelelsen. En digital signatur hjælper modtageren med at validere afsenderens identitet. <br/> Både digitale signaturer og meddelelseskryptering muliggøres ved hjælp af unikke digitale certifikater, der indeholder nøglerne til bekræftelse af digitale signaturer og kryptering eller dekryptering af meddelelser. <br/> Hvis du vil bruge S/MIME, skal du have offentlige nøgler på filen for hver modtager. Modtagerne skal vedligeholde deres egne private nøgler, som skal forblive sikre. Hvis en modtagers private nøgler kompromitteres, skal modtageren have en ny privat nøgle og videredistribuere offentlige nøgler til alle potentielle afsendere.|
|Hvad gør den?|OME: <br/> Krypterer meddelelser, der sendes til interne eller eksterne modtagere. <br/>  Giver brugerne mulighed for at sende krypterede meddelelser til en hvilken som helst mailadresse, herunder Outlook.com, Yahoo! Mail og Gmail. <br/>  Giver dig som administrator mulighed for at tilpasse mailvisningsportalen, så den afspejler organisationens brand. <br/> Microsoft administrerer og gemmer nøglerne på en sikker måde, så det behøver du ikke. <br/> Der kræves ingen særlig software på klientsiden, så længe den krypterede meddelelse (sendt som en vedhæftet HTML-fil) kan åbnes i en browser.|IRM: <br/> Bruger krypterings- og anvendelsesbegrænsninger til at sikre online- og offlinebeskyttelse af mails og vedhæftede filer. <br/> Giver dig som administrator mulighed for at konfigurere transportregler eller Outlook-beskyttelsesregler for automatisk at anvende IRM til at vælge meddelelser. <br/> Gør det muligt for brugerne manuelt at anvende skabeloner i Outlook eller Outlook på internettet (tidligere kaldet Outlook Web App).|S/MIME adresserer afsendergodkendelse med digitale signaturer og meddelelseshemmelighed med kryptering.|
|Hvad gør den ikke?|OME tillader ikke, at du anvender forbrugsbegrænsninger på meddelelser. Du kan f.eks. ikke bruge den til at forhindre en modtager i at videresende eller udskrive en krypteret meddelelse.|Nogle programmer understøtter muligvis ikke IRM-mails på alle enheder. Du kan få flere oplysninger om disse og andre produkter, der understøtter IRM-mail, under [Egenskaber for klientenhed](/azure/information-protection/requirements#BKMK_ClientCapabilities).|S/MIME tillader ikke, at krypterede meddelelser scannes for malware, spam eller politikker.|
|Anbefalinger og eksempelscenarier|Vi anbefaler, at du bruger OME, når du vil sende følsomme forretningsoplysninger til personer uden for din organisation, uanset om de er forbrugere eller andre virksomheder. Eksempel:  <br/>  En bankmedarbejder, der sender kreditkortopgørelser til kunder  <br/>  Et lægekontor, der sender journaler til en patient  <br/>  En advokat, der sender fortrolige juridiske oplysninger til en anden advokat|Vi anbefaler, at du bruger IRM, når du vil anvende anvendelsesbegrænsninger samt kryptering. Eksempel:  <br/>  En leder, der sender fortrolige oplysninger til sit team om et nyt produkt, anvender indstillingen "Videresend ikke".  <br/>  En direktør skal dele et tilbud med en anden virksomhed, som omfatter en vedhæftet fil fra en partner, der bruger Office 365, og kræve, at både mailen og den vedhæftede fil er beskyttet.|Vi anbefaler, at du bruger S/MIME, når enten din organisation eller modtagerens organisation kræver sand peer-to-peer-kryptering.  <br/>  S/MIME bruges oftest i følgende scenarier:  <br/>  Offentlige myndigheder kommunikerer med andre offentlige myndigheder  <br/>  En virksomhed kommunikerer med et offentligt organ|
||

## <a name="what-encryption-options-are-available-for-my-microsoft-365-subscription"></a>Hvilke krypteringsindstillinger er tilgængelige for mit Microsoft 365-abonnement?

Du kan få oplysninger om krypteringsindstillinger for mail for dit Microsoft 365-abonnement i [beskrivelsen af Exchange Online-tjenesten](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description). Her kan du finde oplysninger om følgende krypteringsfunktioner:
  
- Azure RMS, herunder både IRM-funktioner og Microsoft Purview-meddelelseskryptering

- S/MIME

- TLS

- Kryptering af inaktive data (via BitLocker)

Du kan også bruge krypteringsværktøjer fra tredjepart med Microsoft 365, f.eks. PGP (Pretty Good Privacy). Microsoft 365 understøtter ikke PGP/MIME, og du kan kun bruge PGP/Inline til at sende og modtage PGP-krypterede mails.

## <a name="what-about-encryption-for-data-at-rest"></a>Hvad med kryptering af inaktive data?

"Inaktive data" refererer til data, der ikke aktivt er under overførsel. I Microsoft 365 krypteres inaktive maildata ved hjælp af BitLocker-drevkryptering. BitLocker krypterer harddiske i Microsoft-datacentre for at give forbedret beskyttelse mod uautoriseret adgang. Du kan få mere at vide under [BitLocker-oversigt](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831713(v=ws.11)).
  
## <a name="more-information-about-email-encryption-options"></a>Flere oplysninger om indstillinger for mailkryptering

Du kan få flere oplysninger om indstillingerne for mailkryptering i denne artikel samt TLS i disse artikler:
  
**Microsoft Purview-meddelelseskryptering**
  
[Meddelelseskryptering](ome.md)
  
**IRM**
  
[Information Rights Management i Exchange Online](./information-rights-management-in-exchange-online.md)
  
[Hvad er Azure Rights Management?](/azure/information-protection/what-is-azure-rms)
  
**S/MIME**
  
[S/MIME til signering og kryptering af meddelelser](/Exchange/policy-and-compliance/smime/smime)
  
[Om S/MIME](/previous-versions/tn-archive/aa995740(v=exchg.65))
  
[Om kryptografi for offentlige nøgler](/previous-versions/tn-archive/aa998077(v=exchg.65))
  
**TLS**
  
[Konfigurer brugerdefineret mailflow ved hjælp af connectors](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
